[portfolio.html](https://github.com/user-attachments/files/28580849/portfolio.html)
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Sachidananda Karkala — Enterprise AI Platform Architecture</title>
<script src="https://cdn.jsdelivr.net/npm/mermaid@10.9.1/dist/mermaid.min.js"></script>
<style>
  :root {
    --bg: #0b0d10;
    --bg-2: #11151a;
    --bg-3: #161b22;
    --border: #21262d;
    --border-2: #30363d;
    --fg: #e6edf3;
    --fg-dim: #9aa4b2;
    --fg-mute: #6e7681;
    --accent: #7ee787;
    --accent-2: #79c0ff;
    --accent-3: #d2a8ff;
    --warn: #f0883e;
    --code-bg: #161b22;
    --mono: ui-monospace, "SF Mono", "JetBrains Mono", "Fira Code", Menlo, Consolas, monospace;
    --sans: -apple-system, BlinkMacSystemFont, "Segoe UI", Inter, system-ui, sans-serif;
  }
  * { box-sizing: border-box; }
  html, body { margin: 0; padding: 0; background: var(--bg); color: var(--fg); font-family: var(--sans); line-height: 1.6; -webkit-font-smoothing: antialiased; }
  a { color: var(--accent-2); text-decoration: none; }
  a:hover { text-decoration: underline; }
  ::selection { background: rgba(126,231,135,0.25); }

  .wrap { max-width: 1080px; margin: 0 auto; padding: 64px 28px 96px; }

  /* Header */
  header { display: flex; flex-wrap: wrap; gap: 24px; align-items: flex-end; justify-content: space-between; padding-bottom: 36px; border-bottom: 1px solid var(--border); }
  .name-block .eyebrow { font-family: var(--mono); font-size: 12px; color: var(--accent); letter-spacing: 0.08em; text-transform: uppercase; margin-bottom: 8px; }
  .name-block h1 { font-size: 44px; font-weight: 700; margin: 0 0 10px; letter-spacing: -0.02em; }
  .name-block .tag { color: var(--fg-dim); font-size: 17px; max-width: 680px; }
  .links { display: flex; gap: 14px; font-family: var(--mono); font-size: 13px; }
  .links a { color: var(--fg-dim); display: inline-flex; align-items: center; gap: 6px; padding: 6px 10px; border: 1px solid var(--border); border-radius: 6px; }
  .links a:hover { color: var(--accent); border-color: var(--accent); text-decoration: none; }

  /* Intro */
  .intro { margin: 40px 0 48px; color: var(--fg-dim); font-size: 16px; }
  .intro p { margin: 0 0 14px; max-width: 780px; }
  .intro strong { color: var(--fg); font-weight: 600; }

  /* Competencies */
  .pillars { display: grid; grid-template-columns: repeat(4, 1fr); gap: 14px; margin: 32px 0 48px; }
  @media (max-width: 880px) { .pillars { grid-template-columns: repeat(2, 1fr); } }
  @media (max-width: 480px) { .pillars { grid-template-columns: 1fr; } }
  .pillar { background: var(--bg-2); border: 1px solid var(--border); border-radius: 10px; padding: 18px; }
  .pillar h4 { margin: 0 0 6px; font-size: 14px; color: var(--accent); font-family: var(--mono); letter-spacing: 0.02em; }
  .pillar p { margin: 0; font-size: 13.5px; color: var(--fg-dim); line-height: 1.5; }

  /* Section header */
  .section-h { display: flex; align-items: baseline; gap: 12px; margin: 56px 0 24px; }
  .section-h h2 { font-size: 22px; margin: 0; font-weight: 600; letter-spacing: -0.01em; }
  .section-h .hint { font-family: var(--mono); font-size: 12px; color: var(--fg-mute); }

  /* Ecosystem panel */
  .ecosystem { background: var(--bg-2); border: 1px solid var(--border); border-radius: 10px; padding: 24px; margin-bottom: 24px; }
  .ecosystem h3 { font-size: 15px; margin: 0 0 8px; color: var(--fg); }
  .ecosystem p { margin: 0 0 14px; color: var(--fg-dim); font-size: 14px; max-width: 820px; }
  .mermaid { background: transparent; font-family: var(--mono); }

  /* Project card */
  .project { background: var(--bg-2); border: 1px solid var(--border); border-radius: 10px; padding: 28px; margin-bottom: 22px; transition: border-color 0.15s ease; }
  .project:hover { border-color: var(--border-2); }
  .proj-head { display: flex; flex-wrap: wrap; gap: 12px; align-items: baseline; justify-content: space-between; margin-bottom: 4px; }
  .proj-title h3 { font-size: 20px; margin: 0; font-weight: 600; letter-spacing: -0.01em; }
  .proj-meta { font-family: var(--mono); font-size: 12px; color: var(--fg-mute); }
  .proj-meta .dot { color: var(--accent); }
  .pitch { color: var(--fg); font-size: 15.5px; margin: 6px 0 20px; max-width: 880px; font-weight: 500; }

  .row { display: grid; grid-template-columns: minmax(0, 1.05fr) minmax(0, 1fr); gap: 28px; margin-top: 6px; }
  @media (max-width: 760px) { .row { grid-template-columns: 1fr; } }

  .col-h { font-family: var(--mono); font-size: 11px; letter-spacing: 0.08em; text-transform: uppercase; color: var(--accent); margin: 0 0 10px; }
  .arch-text { color: var(--fg-dim); font-size: 14px; }
  .arch-text p { margin: 0 0 10px; }
  .arch-text strong { color: var(--fg); font-weight: 600; }
  .arch-text em { color: var(--fg); font-style: normal; font-weight: 500; }

  .feature-list { margin: 0; padding-left: 18px; color: var(--fg-dim); font-size: 14px; }
  .feature-list li { margin-bottom: 7px; }
  .feature-list strong { color: var(--fg); font-weight: 600; }

  .stack { display: flex; flex-wrap: wrap; gap: 6px; margin-top: 20px; padding-top: 16px; border-top: 1px dashed var(--border); }
  .chip { font-family: var(--mono); font-size: 11.5px; padding: 3px 9px; border-radius: 999px; background: var(--bg-3); color: var(--fg-dim); border: 1px solid var(--border-2); }
  .chip.k { color: var(--accent-2); border-color: rgba(121,192,255,0.25); }
  .chip.l { color: var(--accent); border-color: rgba(126,231,135,0.25); }
  .chip.i { color: var(--accent-3); border-color: rgba(210,168,255,0.25); }
  .chip.w { color: var(--warn); border-color: rgba(240,136,62,0.25); }

  .proj-arch { margin-top: 22px; background: var(--bg-3); border: 1px solid var(--border); border-radius: 8px; padding: 20px; overflow-x: auto; }

  footer { margin-top: 80px; padding-top: 28px; border-top: 1px solid var(--border); color: var(--fg-mute); font-family: var(--mono); font-size: 12px; display: flex; justify-content: space-between; flex-wrap: wrap; gap: 12px; }
</style>
</head>
<body>
<div class="wrap">

<header>
  <div class="name-block">
    <div class="eyebrow">Enterprise AI Platform Architecture</div>
    <h1>Sachidananda Karkala</h1>
    <p class="tag">Designing the platforms enterprises run AI on — shared inference, autonomous multi-agent systems, knowledge governance, and the identity and change-management glue that makes them safe to scale.</p>
  </div>
  <div class="links">
    <a href="mailto:sachi.achar@gmail.com">sachi.achar@gmail.com</a>
  </div>
</header>

<section class="intro">
  <p>I work on how enterprises move from <strong>ad-hoc AI pilots</strong> to <strong>governed, shared AI platforms</strong> — the kind that have one security perimeter, one cost centre, one knowledge surface, and a clear path from experiment to production. The portfolio below is a set of <strong>reference architectures and proof-of-concept designs</strong> — ideations worked through end-to-end, with system design, trade-offs, and component choices made explicit. Some are running as PoCs; all are architected to be production-deployable.</p>
  <p>The throughline is platform thinking: where to centralise (inference, identity, knowledge, change management) and where to keep things pluggable (model backends, workflow agents, downstream tools) so the platform can evolve without rewrites.</p>
</section>

<div class="pillars">
  <div class="pillar">
    <h4>// Shared AI Inference</h4>
    <p>One governed endpoint replacing per-team GPU sprawl. OIDC at the perimeter, swappable backend, cost attribution by user.</p>
  </div>
  <div class="pillar">
    <h4>// Autonomous Agents</h4>
    <p>Multi-agent pipelines with Plan / Execute / Evaluate / Replan loops, stakeholder-perspective review, and human-in-the-loop gates on quality.</p>
  </div>
  <div class="pillar">
    <h4>// AI Identity &amp; RBAC</h4>
    <p>Per-tool access control for AI agents, reusable across services. Auditable, role-inheriting, and built to integrate with any IdP.</p>
  </div>
  <div class="pillar">
    <h4>// Data &amp; Knowledge Platforms</h4>
    <p>Petabyte-scale log analytics, temporal knowledge graphs, and measurable knowledge quality with hallucination penalties.</p>
  </div>
</div>

<div class="section-h">
  <h2>How the platforms compose</h2>
  <span class="hint">// strategic view</span>
</div>

<div class="ecosystem">
  <h3>One substrate, three product lines</h3>
  <p>An <strong>autonomous research-agent platform</strong> designed to produce structured analysis end-to-end. A <strong>shared inference cluster</strong> designed to give every team and every agent one OIDC-secured, OpenAI-compatible LLM endpoint. A <strong>conversational gateway</strong> fronts both for end-users. Identity, knowledge, and observability are shared services — designed once, consumed everywhere.</p>
  <div class="mermaid">
flowchart LR
  user["Enterprise users<br/>analysts · operators · executives"]
  subgraph gw["Conversational Gateway"]
    chat["Chat + workflow registry"]
  end
  subgraph agents["Autonomous Agent Platforms"]
    ra["Research-agent pipeline"]
    sf["AI-native software factory"]
  end
  subgraph shared["Shared Enterprise Services"]
    inf["Shared inference platform"]
    kg["Knowledge graph + quality scoring"]
    iam["AI identity &amp; RBAC"]
    data["Petabyte log analytics"]
  end
  user --> chat
  chat --> agents
  agents --> inf
  agents --> kg
  agents -.governed by.-> iam
  inf -.governed by.-> iam
  kg -.governed by.-> iam
  classDef sub fill:#11151a,stroke:#30363d,color:#e6edf3
  class gw,agents,shared sub
  </div>
</div>

<div class="section-h">
  <h2>Reference architectures</h2>
  <span class="hint">// platform decisions &amp; design blueprints</span>
</div>

<!-- =========================== PROJECT 1 — Research Agent Platform =========================== -->
<article class="project">
  <div class="proj-head">
    <div class="proj-title">
      <h3>Autonomous Research-Agent Platform</h3>
    </div>
    <div class="proj-meta"><span><span class="dot">●</span> multi-agent · governance · GitOps</span></div>
  </div>
  <p class="pitch">Reference architecture for a governed multi-agent platform that takes a customer brief end-to-end — research, analysis, stakeholder-perspective review, and presentation-ready output — with human-in-the-loop gates on knowledge quality.</p>

  <div class="row">
    <div>
      <div class="col-h">The enterprise problem</div>
      <div class="arch-text">
        <p>Consulting and customer-success teams spend disproportionate effort preparing structured reviews — the analysis is repetitive but the stakes are high, the data is scattered, and quality varies by analyst. Generic LLM tools produce confident-sounding output that no one trusts in front of a customer executive.</p>
      </div>
      <div class="col-h" style="margin-top:18px">Architectural approach</div>
      <div class="arch-text">
        <p>A <strong>Plan → Execute → Evaluate → Replan</strong> loop driven by a durable workflow runtime. Agents are stateless and composable; all state lives in shared services (a temporal knowledge graph for long-term context, a scratch graph for per-job analysis, a calculation service for numerics so the LLM never invents figures). <strong>Specialists are synthesised at runtime</strong> from the knowledge graph — no hardcoded domain agents.</p>
        <p>Quality is treated as a first-class signal. Before deeper analysis runs, the planner reads a per-topic confidence score; topics that fall below threshold trigger a <strong>human-in-the-loop gap-filling step</strong>. Two reviewer agents simulate stakeholder scrutiny (security and operations perspectives) and generate the hard questions a customer would ask. The whole platform is GitOps-managed for change control.</p>
      </div>
    </div>
    <div>
      <div class="col-h">Design outcomes</div>
      <ul class="feature-list">
        <li><strong>End-to-end automation</strong> from raw inputs to executive-ready deliverable — analyst becomes editor, not author.</li>
        <li><strong>Stakeholder-perspective review</strong> built in — security and operations critique runs before content reaches a customer.</li>
        <li><strong>Knowledge-quality gating</strong> — the platform refuses to opine on topics it doesn&rsquo;t understand well enough; humans approve any gap-fill.</li>
        <li><strong>Cited findings</strong> — every conclusion traceable to a graph entity, eliminating &ldquo;the LLM said so&rdquo; risk.</li>
        <li><strong>GitOps change control</strong> — every platform change is a reviewable pull request; rollback is one commit away.</li>
        <li><strong>Pluggable models</strong> — analytical vs mechanical work routed to different tiers; private data never leaves the cluster.</li>
      </ul>
    </div>
  </div>

  <div class="proj-arch">
    <div class="mermaid">
flowchart LR
  inputs["Customer inputs<br/>+ prior engagement history"]
  plan["Planner<br/>(knowledge-quality gated)"]
  hitl{{"Human-in-the-loop<br/>gap-fill approval"}}
  exec["Specialist analysts<br/>(synthesised at runtime)"]
  review["Stakeholder-perspective<br/>reviewers"]
  brief["Briefing &amp; deliverable"]
  inputs --> plan
  plan -- gaps --> hitl --> plan
  plan --> exec --> review
  review -- replan --> plan
  review --> brief
    </div>
  </div>

  <div class="stack">
    <span class="chip i">Multi-agent orchestration</span><span class="chip i">Durable workflow runtime</span><span class="chip">Knowledge graph</span><span class="chip k">GitOps / Argo CD</span><span class="chip l">Identity &amp; RBAC</span><span class="chip">Self-hosted LLM inference</span><span class="chip">HITL gates</span>
  </div>
</article>

<!-- =========================== PROJECT 2 — Shared Inference Cluster =========================== -->
<article class="project">
  <div class="proj-head">
    <div class="proj-title">
      <h3>Shared Enterprise Inference Platform</h3>
    </div>
    <div class="proj-meta"><span><span class="dot">●</span> AI platform · cost governance · security</span></div>
  </div>
  <p class="pitch">Reference architecture for a centrally managed AI inference platform — replacing per-team GPU sprawl with one governed endpoint designed for global use across demos, proofs-of-concept, and customer engagements.</p>

  <div class="row">
    <div>
      <div class="col-h">The enterprise problem</div>
      <div class="arch-text">
        <p>Teams provision their own GPU instances. Most sit idle. Different teams run different model versions with different configurations — demos to customers stop being reproducible. Each ad-hoc endpoint is a separate security boundary to harden, monitor, and audit. There is no per-team or per-user cost visibility, so chargeback and capacity planning are impossible.</p>
      </div>
      <div class="col-h" style="margin-top:18px">Architectural approach</div>
      <div class="arch-text">
        <p>A single always-on inference endpoint, secured by an <strong>OIDC perimeter</strong> and protected by an <strong>AI-specific firewall</strong> (prompt injection, exfiltration, jailbreak detection) before any request reaches a GPU. The client-facing protocol is the de facto industry standard, so internal tools and SDKs work without changes. The model-serving backend underneath is <strong>swappable</strong> — the platform can evolve from LLMs to vision and classical ML without a client-side migration.</p>
        <p>Releases are guarded by automated capacity validation: a deployment is blocked before it lands if it would exceed safe GPU memory. Every request is attributed to a user at the perimeter, so cost and audit are by-construction, not bolted on.</p>
      </div>
    </div>
    <div>
      <div class="col-h">Design outcomes</div>
      <ul class="feature-list">
        <li><strong>One endpoint, one security boundary, one cost centre</strong> — replacing fragmented per-team setups.</li>
        <li><strong>Democratised access to large models</strong> — 30B+ parameter models reachable by any authorised user without per-team infrastructure overhead.</li>
        <li><strong>AI-perimeter security</strong> — prompt-injection and exfiltration filtering before requests consume GPU capacity.</li>
        <li><strong>Per-user cost attribution</strong> — usage tied to identity at the edge, enabling showback and chargeback.</li>
        <li><strong>Backend independence</strong> — model runtime can be swapped without client-side changes.</li>
        <li><strong>Safe by default</strong> — deployments blocked automatically if they would over-commit GPU memory.</li>
      </ul>
    </div>
  </div>

  <div class="proj-arch">
    <div class="mermaid">
flowchart LR
  callers["Enterprise tools<br/>agents · IDE plugins · UIs"]
  edge["AI perimeter<br/>OIDC · prompt-injection filtering"]
  endpoint["Single inference endpoint<br/>industry-standard protocol"]
  backend["Swappable model backend"]
  gov["Identity-linked usage<br/>cost &amp; audit"]
  callers --> edge --> endpoint --> backend
  edge -.attributes.-> gov
    </div>
  </div>

  <div class="stack">
    <span class="chip">Enterprise AI platform</span><span class="chip l">OIDC / SSO</span><span class="chip w">AI security perimeter</span><span class="chip">GPU capacity governance</span><span class="chip k">Kubernetes</span><span class="chip">Self-hosted LLM serving</span><span class="chip">Per-user cost attribution</span>
  </div>
</article>

<!-- =========================== PROJECT 3 — FactoryAgent =========================== -->
<article class="project">
  <div class="proj-head">
    <div class="proj-title">
      <h3>AI-Native Software Delivery Factory</h3>
    </div>
    <div class="proj-meta"><span><span class="dot">●</span> AI SDLC · GitOps · approval gates</span></div>
  </div>
  <p class="pitch">Proof-of-concept design for a multi-agent &ldquo;software factory&rdquo; — program management, product specification, testing, and runtime engineering each as a specialised agent — that takes a business epic toward a deployable application with approval gates on every release.</p>

  <div class="row">
    <div>
      <div class="col-h">The enterprise problem</div>
      <div class="arch-text">
        <p>AI coding assistants are individual-productivity tools. The harder problem — turning a business epic into a deployed, governed application — still requires several specialist roles (product, test, platform) and a release pipeline with approval gates. Most organisations have nothing connecting these.</p>
      </div>
      <div class="col-h" style="margin-top:18px">Architectural approach</div>
      <div class="arch-text">
        <p>Each role is its own agent, isolated to its own prompt and container, communicating over a shared message bus. A <strong>dashboard</strong> is the operator surface; the runtime-engineering agent produces a deployment plan that <em>only</em> reaches the cluster after a human clicks Approve. From there it is committed to a Git repository and reconciled by a GitOps controller — the same change-control model an enterprise platform team would insist on.</p>
        <p>The agent runtime is shared and pluggable: any agent can use a cloud-hosted model or a self-hosted one per environment, with full request tracing for audit. New agent roles are configuration, not code.</p>
      </div>
    </div>
    <div>
      <div class="col-h">Design outcomes</div>
      <ul class="feature-list">
        <li><strong>Role separation by design</strong> — program, product, test, and platform concerns each owned by a specialised agent.</li>
        <li><strong>Approval-gated releases</strong> — nothing reaches the cluster without an explicit human decision.</li>
        <li><strong>GitOps as the audit trail</strong> — every deployment is a reviewable commit; rollback is a revert.</li>
        <li><strong>Per-environment model choice</strong> — cloud models in dev, fully self-hosted in regulated environments.</li>
        <li><strong>Full request tracing</strong> — every agent call is observable end-to-end for compliance and debugging.</li>
        <li><strong>Configuration over code</strong> — adding a new role agent is a prompt + an entry, not a new codebase.</li>
      </ul>
    </div>
  </div>

  <div class="proj-arch">
    <div class="mermaid">
flowchart LR
  epic["Business epic"]
  subgraph factory["Specialised agents"]
    pm["Program mgmt"]
    pdm["Product spec"]
    qa["Testing"]
    re["Runtime engineering"]
  end
  plan["Deployment plan<br/>(markdown)"]
  hitl{{"Human approval"}}
  gitops["GitOps repo &amp; reconciler"]
  env["Governed environments"]
  epic --> pm --> pdm --> qa --> re --> plan --> hitl --> gitops --> env
    </div>
  </div>

  <div class="stack">
    <span class="chip i">Multi-agent SDLC</span><span class="chip k">GitOps / Argo CD</span><span class="chip">Approval gates</span><span class="chip">Distributed tracing</span><span class="chip k">Kubernetes</span><span class="chip">Per-env model routing</span><span class="chip l">Audit trail</span>
  </div>
</article>

<!-- =========================== PROJECT 4 — Knowledge Store =========================== -->
<article class="project">
  <div class="proj-head">
    <div class="proj-title">
      <h3>Enterprise Knowledge Layer with Measurable Quality</h3>
    </div>
    <div class="proj-meta"><span><span class="dot">●</span> knowledge graph · trust · RBAC</span></div>
  </div>
  <p class="pitch">Reference architecture for a temporal knowledge graph over enterprise content — product documentation, customer engagement history, analytical findings — that scores its own knowledge quality and refuses to opine on topics it doesn&rsquo;t understand well enough.</p>

  <div class="row">
    <div>
      <div class="col-h">The enterprise problem</div>
      <div class="arch-text">
        <p>RAG over an enterprise corpus produces fluent answers that no one can trust. There is no signal for &ldquo;is this graph good enough to use for this customer, this topic, this question?&rdquo; — and no fine-grained access control for who can read versus ingest versus modify.</p>
      </div>
      <div class="col-h" style="margin-top:18px">Architectural approach</div>
      <div class="arch-text">
        <p>A temporal knowledge graph stores entities and relationships extracted from source documents, namespaced per domain. After every ingest, the platform runs <strong>three probe passes</strong> against the live namespace — factual, relational, and a negative pass that detects hallucination — and produces a <em>ConfidenceReport</em> with a hallucination-penalised score per topic.</p>
        <p>That score is the input to other systems&rsquo; trust decisions: the autonomous agent platform reads it before deciding whether to plan analysis on a topic. Access is governed by per-tool RBAC with three role tiers; tokens are issued by a standard IdP and validated in-process, so the access layer is microseconds, not a network hop.</p>
      </div>
    </div>
    <div>
      <div class="col-h">Design outcomes</div>
      <ul class="feature-list">
        <li><strong>Measurable knowledge quality</strong> — every topic carries a score; downstream agents can refuse low-confidence work.</li>
        <li><strong>Hallucination-aware scoring</strong> — explicit penalty when the model invents facts under retrieval.</li>
        <li><strong>Per-tool RBAC</strong> — three role tiers control who can query, ingest, or evaluate.</li>
        <li><strong>Standard IdP integration</strong> — JWT-based, drops into any enterprise SSO setup.</li>
        <li><strong>Temporal model</strong> — facts are time-aware, so &ldquo;what did we know about this customer last quarter?&rdquo; is a first-class query.</li>
        <li><strong>Two surfaces, one core</strong> — programmatic and human UIs over the same governed store.</li>
      </ul>
    </div>
  </div>

  <div class="proj-arch">
    <div class="mermaid">
flowchart LR
  sources["Source docs<br/>customer history · findings"]
  ingest["Ingest"]
  kg[("Temporal knowledge graph")]
  probes["Quality probes<br/>factual · relational · negative"]
  score["ConfidenceReport"]
  rbac["Per-tool RBAC"]
  consumers["Agents / analysts / UIs"]
  sources --> ingest --> kg
  kg --> probes --> score
  consumers -.governed by.-> rbac
  rbac --> kg
  score -.gates.-> consumers
    </div>
  </div>

  <div class="stack">
    <span class="chip i">Knowledge graph</span><span class="chip">Hallucination scoring</span><span class="chip l">RBAC &amp; JWT</span><span class="chip">Temporal model</span><span class="chip k">Kubernetes</span><span class="chip">Standard IdP</span><span class="chip">Audit-ready</span>
  </div>
</article>

<!-- =========================== PROJECT 5 — mcp-identity =========================== -->
<article class="project">
  <div class="proj-head">
    <div class="proj-title">
      <h3>AI Identity &amp; Access for Tool-Using Agents</h3>
    </div>
    <div class="proj-meta"><span><span class="dot">●</span> identity · per-tool RBAC · drop-in</span></div>
  </div>
  <p class="pitch">Reference architecture for a reusable identity and per-tool access-control layer for AI agent platforms — designed to drop into any agent backend, governed by the same IdP an enterprise already uses for its workforce.</p>

  <div class="row">
    <div>
      <div class="col-h">The enterprise problem</div>
      <div class="arch-text">
        <p>AI agents expose tools. Analysts should only be able to read; ingestion pipelines should be able to write; only platform engineers should be able to evaluate or delete. A single shared key gives every caller full access — and most agent frameworks have nothing better. Enterprises cannot adopt agent platforms at scale until access control matches the rest of the workforce identity model.</p>
      </div>
      <div class="col-h" style="margin-top:18px">Architectural approach</div>
      <div class="arch-text">
        <p>Two artefacts. A <strong>self-hosted IdP</strong> deployment that issues tokens, manages users and roles, and provides an audit UI for ops. A <strong>pluggable access-control library</strong> any agent backend can drop in: tokens are validated against the IdP and per-tool authorisation runs in-process for microsecond latency, with <strong>role inheritance</strong> so policies stay small as the tool surface grows.</p>
      </div>
    </div>
    <div>
      <div class="col-h">Design outcomes</div>
      <ul class="feature-list">
        <li><strong>Per-tool, per-role authorisation</strong> — different callers see different surfaces of the same agent.</li>
        <li><strong>One identity layer across multiple agent platforms</strong> — same tokens, same roles, same audit trail.</li>
        <li><strong>Microsecond authorisation</strong> — no network hop on the hot path.</li>
        <li><strong>Role inheritance</strong> — policies grow linearly, not combinatorially.</li>
        <li><strong>IdP-agnostic</strong> — bring your own SSO or use the bundled one.</li>
        <li><strong>Auditable by design</strong> — every authorisation decision is loggable and explainable.</li>
      </ul>
    </div>
  </div>

  <div class="proj-arch">
    <div class="mermaid">
flowchart LR
  caller["Caller<br/>(user / agent / service)"]
  idp["Identity Provider"]
  enf["In-process authorisation<br/>per-tool RBAC"]
  agent["Agent backend tools"]
  audit[("Audit log")]
  caller --> idp
  caller --> enf
  enf -.validates.-> idp
  enf --> agent
  enf -.logs.-> audit
    </div>
  </div>

  <div class="stack">
    <span class="chip l">AI identity layer</span><span class="chip l">Per-tool RBAC</span><span class="chip">Role inheritance</span><span class="chip">SSO-agnostic</span><span class="chip k">Kubernetes</span><span class="chip">Drop-in library</span><span class="chip">Audit-by-design</span>
  </div>
</article>

<!-- =========================== PROJECT 6 — AskSachi =========================== -->
<article class="project">
  <div class="proj-head">
    <div class="proj-title">
      <h3>Conversational Gateway for Organisational Automation</h3>
    </div>
    <div class="proj-meta"><span><span class="dot">●</span> AI gateway · automation surface</span></div>
  </div>
  <p class="pitch">Architectural design for a single chat surface where employees talk things through with an assistant and run company-defined automations — every automation a pluggable workflow agent registered by the platform team.</p>

  <div class="row">
    <div>
      <div class="col-h">The enterprise problem</div>
      <div class="arch-text">
        <p>Public AI chat tools are great for conversation but can&rsquo;t kick off internal actions and don&rsquo;t know about private systems. Internal automation scripts exist but are scattered across CLIs, runbooks, and ticketing tools. Employees need <strong>one surface</strong> where they can both think out loud and trigger a sanctioned workflow.</p>
      </div>
      <div class="col-h" style="margin-top:18px">Architectural approach</div>
      <div class="arch-text">
        <p>A gateway with two modes. The <strong>default mode</strong> is a standard chat assistant pointed at an enterprise-approved upstream model. The <strong>workflow registry</strong> holds automations — each one a separately-deployed agent that registers a capability card with the gateway; the user selects a workflow and the next message routes to it. Automations can be added or removed without touching the gateway.</p>
        <p>External access to sensitive systems is locked to a read-only allowlist with identity-correct context resolution, so the gateway can never be tricked into acting on the wrong customer account.</p>
      </div>
    </div>
    <div>
      <div class="col-h">Design outcomes</div>
      <ul class="feature-list">
        <li><strong>One surface for chat + sanctioned automations</strong> — replacing tool sprawl with a governed gateway.</li>
        <li><strong>Pluggable workflows</strong> — platform teams add or retire automations without redeploying the gateway.</li>
        <li><strong>Industry-standard API</strong> — any client that speaks the standard LLM protocol drops in.</li>
        <li><strong>Identity-correct external access</strong> — read-only, with a resolver that refuses ambiguous customer context.</li>
        <li><strong>Deploy anywhere</strong> — runs on a laptop for dev, scales to a shared service for a department.</li>
        <li><strong>Observable by default</strong> — every run carries an audit trail.</li>
      </ul>
    </div>
  </div>

  <div class="proj-arch">
    <div class="mermaid">
flowchart LR
  emp["Employee"]
  gw["Gateway<br/>chat + workflow registry"]
  llm["Enterprise-approved LLM"]
  reg["Pluggable workflow agents"]
  sys["Internal systems<br/>(read-only, identity-correct)"]
  emp --> gw
  gw --> llm
  gw --> reg --> sys
    </div>
  </div>

  <div class="stack">
    <span class="chip">AI gateway</span><span class="chip">Pluggable workflows</span><span class="chip l">Read-only safe access</span><span class="chip">Standard LLM protocol</span><span class="chip">Audit trail</span><span class="chip k">Kubernetes or laptop</span>
  </div>
</article>

<!-- =========================== PROJECT 7 — ClickHouse Prod =========================== -->
<article class="project">
  <div class="proj-head">
    <div class="proj-title">
      <h3>Petabyte-Scale Observability — Reference Architecture</h3>
    </div>
    <div class="proj-meta"><span><span class="dot">●</span> data platform · tiered storage · DR</span></div>
  </div>
  <p class="pitch">Reference architecture for a log analytics platform designed to handle <strong>~800 billion events per month</strong> — columnar storage, tiered hot/cold/backup, and cross-region disaster recovery — the data backbone that AI platforms above can rely on.</p>

  <div class="row">
    <div>
      <div class="col-h">The enterprise problem</div>
      <div class="arch-text">
        <p>At edge-network scale, log volumes break general-purpose data stores and bankrupt naïve storage strategies. Customers need queryable history but the cost curve grows linearly with raw volume unless the architecture is right.</p>
      </div>
      <div class="col-h" style="margin-top:18px">Architectural approach</div>
      <div class="arch-text">
        <p>Columnar storage with <strong>10–12× compression</strong>, sharded for parallel ingest and query, with a <strong>tiered storage model</strong>: hot tier on local NVMe for recent data, cold tier on regional object storage for history, and a cross-region backup tier for disaster recovery. Ingestion is decoupled via a buffering layer so spikes don&rsquo;t propagate to the database. Read and write paths are isolated so customer queries never compete with ingest pressure.</p>
      </div>
    </div>
    <div>
      <div class="col-h">Design outcomes</div>
      <ul class="feature-list">
        <li><strong>~800B events / month</strong> as design target, with multi-x burst capacity headroom.</li>
        <li><strong>10–12× compression</strong> — economics that make full-history retention viable.</li>
        <li><strong>Tiered hot / cold / DR</strong> — recent data fast, history affordable, disaster recovery cross-region.</li>
        <li><strong>Ingest / query isolation</strong> — customer queries unaffected by ingestion spikes.</li>
        <li><strong>Improved RPO via cross-region snapshots</strong> — measured in hours, not days.</li>
        <li><strong>Documented operations</strong> — runbooks for DR, upgrades, credential rotation, troubleshooting.</li>
      </ul>
    </div>
  </div>

  <div class="proj-arch">
    <div class="mermaid">
flowchart LR
  edge["Edge network<br/>log streams"]
  buf["Buffering layer"]
  cluster[("Columnar analytics cluster<br/>sharded · replicated")]
  hot[("Hot · NVMe")]
  cold[("Cold · regional object store")]
  dr[("Cross-region DR snapshots")]
  q["Customer queries (read-only)"]
  edge --> buf --> cluster --> hot --> cold
  cluster -.snapshots.-> dr
  q --> cluster
    </div>
  </div>

  <div class="stack">
    <span class="chip">Columnar analytics</span><span class="chip">Tiered storage</span><span class="chip">Cross-region DR</span><span class="chip k">Kubernetes</span><span class="chip">Ingest / query isolation</span><span class="chip">Petabyte scale</span><span class="chip">Operational runbooks</span>
  </div>
</article>

<footer>
  <span>Sachidananda Karkala · enterprise AI platform architecture</span>
  <span>sachi.achar@gmail.com</span>
</footer>

</div>

<script>
  mermaid.initialize({
    startOnLoad: true,
    theme: 'base',
    themeVariables: {
      background: '#161b22',
      primaryColor: '#161b22',
      primaryTextColor: '#e6edf3',
      primaryBorderColor: '#30363d',
      lineColor: '#7ee787',
      secondaryColor: '#11151a',
      tertiaryColor: '#0b0d10',
      fontFamily: 'ui-monospace, "SF Mono", Menlo, monospace',
      fontSize: '13px'
    },
    flowchart: { curve: 'basis', padding: 16 },
    sequence: { actorMargin: 60, messageFontSize: 12 }
  });
</script>
</body>
</html>
