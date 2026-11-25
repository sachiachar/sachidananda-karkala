[← Back to portfolio](../README.md) · Reference Architectures

# AI-Native Software Delivery Factory

**AI SDLC · GitOps · Approval Gates**

Proof-of-concept design for a multi-agent "software factory" — program management, product specification, testing, and runtime engineering each as a specialised agent, communicating over a shared bus.

## The Enterprise Problem
AI coding assistants are individual-productivity tools. The harder problem — turning a business epic into a deployed, governed application — still requires several specialist roles (product owner, QA lead, platform engineer, program manager).

## Architectural Approach
Each role is its own agent, isolated to its own prompt and container, communicating over a shared message bus. A **dashboard** is the operator surface; the runtime-engineering agent serves as the orchestrator.

The agent runtime is shared and pluggable: any agent can use a cloud-hosted model or a self-hosted one per environment, with full request tracing for audit. New agent roles are configuration + prompt, not code.

## Design Outcomes
- **Role separation by design** — program, product, test, and platform concerns each owned by a specialised agent
- **Approval-gated releases** — nothing reaches the cluster without an explicit human decision
- **GitOps as the audit trail** — every deployment is a reviewable commit; rollback is a revert
- **Per-environment model choice** — cloud models in dev, fully self-hosted in regulated environments
- **Full request tracing** — every agent call is observable end-to-end for compliance and debugging
- **Configuration over code** — adding a new role agent is a prompt + an entry, not a new codebase

**Stack:** Multi-agent SDLC · GitOps / Argo CD · Approval gates · Distributed tracing · Kubernetes

<p align="center"><img src="../images/software-factory.png" alt="AI-Native Software Delivery Factory architecture" width="860"></p>

---

← [Shared Enterprise Inference Platform](shared-inference-platform.md) · [Home](../README.md) · [Enterprise Knowledge Layer with Measurable Quality](knowledge-layer.md) →
