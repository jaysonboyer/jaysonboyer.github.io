---
layout: default
title: Resume
permalink: /
redirect_from: /resume/
---

<div class="resume" markdown="1">

**Principal Software Architect** · Seattle, WA · [LinkedIn](https://linkedin.com/in/jaysonboyer/) · [GitHub](https://github.com/jaysonboyer)

*This is the complete, general version. Tailored resumes sent to specific roles are selections from it.*

## Summary

Principal software architect with 20+ years building consumer-scale platforms and
marketplaces, and 15+ years designing and operating large-scale distributed
systems, 10+ of them cloud-native. Recent work is production AI: a customer-facing
agent and the MCP server behind it, a context management system for coding
agents, and the adversarial eval harness and cost instrumentation that tuned and
tracked them. Before that, frontend architecture and performance on large React
sites, federated GraphQL design, and Kubernetes capacity work. Combines backend
and scalability depth with a focus on user behavior, using experimentation and
analytics to drive product outcomes.

## Technical Skills

**Languages:** Java, TypeScript/JavaScript, Python, Scala, C#, PHP, Perl, GraphQL, SQL

**AI & Agents:** Anthropic Claude API, Claude Code and Claude Agent SDK, OpenAI
API, Google ADK, LangChain/LangGraph, CrewAI, MCP server development, RAG and
hybrid retrieval, prompt and context engineering, adversarial eval harnesses,
agent tracing and cost instrumentation, Cline, opencode, aider

**Backend & API:** Node.js, NestJS, Express, Apollo Federation, REST, domain-driven
design, onion architecture, Prisma, TypeORM, Spring MVC, Spring Boot, Spring Data JPA,
C#/.NET,
BullMQ/Kue

**Frontend:** React, Next.js (SSR), React Native, React Router loaders and actions,
Web Components (LitElement/lit-html), Apollo Client, Redux, MobX, Radix, GraphQL Codegen,
micro-frontends (Feature Hub), AngularJS, WCAG accessibility

**Build & Delivery:** Webpack (including custom plugins), Rollup/tsup (ESM and
CommonJS), code splitting (next/dynamic, React.lazy), Module Federation, bundle
analysis, React Profiler

**Data & Search:** Postgres, MongoDB, Redis, Typesense, MySQL, Oracle PL/SQL,
BigQuery, Looker, Airflow, Kafka, Spark, Hadoop, ArcadeDB (graph + vector)

**Infrastructure:** Kubernetes on GKE, Helm, Docker Compose, GitHub Actions,
Cloudflare, GCP, AWS (S3, EC2, IAM), Azure, Terraform (limited), JMeter

**Observability & Operations:** OpenTelemetry, DataDog, New Relic, Sentry, Splunk,
Google Cloud Logging, Opsgenie on-call, runbooks, postmortems

**Identity & Security:** Auth0/Okta, OAuth 2.0, JWT, OIDC, OWASP, SOC 2 remediation,
HIPAA/PHI handling

**Experimentation & Analytics:** GrowthBook (with Google Analytics and BigQuery), CloudBees Feature Management, Google
Analytics, Google Tag Manager, Google Ad Manager, Conductor, SEO split testing

**Testing:** Jest, Mocha, JUnit, Cypress, Playwright, Nightwatch, Selenium,
Cucumber

## Professional Experience

### HG Insights (formerly TrustRadius) — Principal Engineer

September 2023 – July 2026 · Remote · Reported to the CTO

#### AI strategy and agents

- Led the AI strategy and implementation: a customer-facing two-agent workflow on
  the TrustRadius B2B software review site, built in Python on Google ADK. One
  agent summarized the most relevant verified reviews and a second formatted and
  presented them in real time, with pricing benchmarks, feature analysis, and
  reviewer takeaways.
- Wrote the MCP server in NestJS/TypeScript that exposed platform data and tools
  to that agent as a versioned, independently deployable service.
- Built against the Claude and OpenAI model APIs directly, and with Google ADK,
  LangChain/LangGraph, and CrewAI for multi-step orchestration; used Claude Code
  and the Agent SDK for internal automation.
- Designed retrieval and grounding on Typesense over the review corpus, one index
  serving both the product search and the AI workflows.
- Wrote the prompts for and managed the automated code-review agents, reviewing
  every change for security, maintainability, and correctness.

#### Agent evaluation and production operations

- Built an adversarial eval harness for the coding-agent context system: hand-authored regression
  cases with pre-declared pass/fail markers, control arms that discard cases the
  model passes anyway, and ground truth read from disk state (SHA-256 diffs,
  behavioral code markers) instead of the model's own report. Used it to find
  which half of a two-part fix took three failing cases to passing, and dropped
  the other half.
- Instrumented agent workflows with tracing and structured logging on a logging
  library that enforced standards across services; built an operations dashboard
  for token consumption and inference cost per session, project, and model, with
  tool-error rates and failure timelines.
- Rolled agents out behind feature flags with staged exposure and kill switches;
  applied least-privilege credentials and tool scopes with audit logging of agent
  actions.

#### Context engineering for coding agents

- Built a context management system for development teams working with AI coding
  agents: acceptance criteria extracted from Jira tickets, an ephemeral isolated
  workspace per ticket generated from declarative config (git worktrees,
  generated instructions, projected skills and subagents, MCP wiring, compose
  services).
- Designed phase-gated workflows with human checkpoints: a read-only research
  phase that structurally cannot edit source, findings persisted as durable notes,
  and open questions resolved before implementation begins.
- Ran that tooling as a multi-agent workflow: a lead agent delegates to subagents
  per phase (research, implement, test, review), each with its own tool
  allowlist. Developers went from one feature at a time to about 3–4 in parallel.
- Designed a just-in-time context system gated on phase, domain, service presence,
  and per-subagent tool allowlists, which carries a compiled routing table instead
  of the standards themselves. Deterministic phase-entry gating loaded the right
  standard in 15 of 15 trials where letting the model decide loaded it in 0 of 16.
  With the right context loaded, Haiku 4.5 applied all nine standards under test;
  unloaded, it applied none.
- Built the durable notes ledger that serves as agent memory across sessions:
  typed notes with an open, superseded, graduated lifecycle, re-injected at
  session start including after compaction, with a graduation path into a
  versioned standards tree.

#### Platform resilience and scalability

- Led JMeter load testing against the highest-traffic page types to absorb
  thundering-herd bot spikes from email campaigns; after tuning Helm autoscaling,
  MongoDB indexes, Redis caching, edge caching, and circuit breakers, the platform
  absorbed 17× normal traffic. MongoDB request capacity rose 10×.
- The Next.js migration below, plus Postgres and MongoDB query tuning behind
  every GraphQL subgraph, cut the worst page type, Product Comparison, from about
  10s to under 4s average load.
- Introduced Typesense as the search layer, moving query pressure off MongoDB;
  ran Airflow for ETL including the Typesense index builds.

#### Architecture and GraphQL

- Owned the decomposition plan for the legacy monolith into services federated
  behind one graph: personally extracted the Interview, Awards, and Vendor
  services, built the federated interfaces for Product, Category, and User, and
  set the patterns other engineers followed. Migrated 4 of the 6
  highest-trafficked page types onto the federated graph.
- Refactored every extracted service into a strict onion architecture, REST and
  GraphQL as siblings over one service layer and one Redis cache; kept REST
  versioned and backward compatible throughout the migration.
- Instrumented the graph with OpenTelemetry so cross-subgraph latency could be
  attributed to the service that caused it.
- Owned the GraphQL layer beneath the Next.js buyer site, composed from
  colocated query fragments typed with GraphQL Codegen on a Radix-based
  component library; started the Product and Category APIs on Prisma over
  Postgres, later moved to TypeORM for hand-tuned SQL.
- Authored ADRs for Apollo Federation, JMeter load testing, Web Components for
  micro-frontends, and experimentation strategy.

#### Frontend architecture, web performance, and AI visibility

- Led the migration of the buyer site off a six-year-old stack of Pug templates
  on Node/Express, with a partial React migration left unfinished, onto Next.js
  with SSR. Owned the architecture, the migration plan, and the rollout across a
  team of 10 to 15 engineers.
- Led the web performance strategy that took mobile Core Web Vitals from 50%
  "Poor" to 0% and from 0% "Good" to 20%, measured in CrUX field data from real
  users. New features shipped dark and were checked in WebPageTest before flag-on.
- Got there by cutting what the browser had to load and run: wrote a custom
  Webpack plugin to find dead code, split bundles with next/dynamic and
  React.lazy after trying Module Federation and dropping it when Vercel ended
  support, and fixed SSR hydration mismatches and redundant renders found with
  React Profiler.
- Packaged shared library code with Rollup and tsup as ESM and CommonJS builds.
- Built the AI-visibility pipeline for AEO/GEO end to end: Cloudflare crawler logs
  plus Conductor prompt-tracking data into BigQuery, surfaced in Looker; collaborated
  on the warehouse schema and maintained the visit, AI-visibility, and review
  pipelines behind the company's BI.
- Built the custom metrics and Google Analytics and BigQuery integrations behind
  GrowthBook's experiment analytics.
- Expanded the experimentation program to SEO split testing with GrowthBook;
  participated in jobs-to-be-done interviews with software buyers and interviewed
  content, moderation, and UGC teams to map their workflows, producing improved
  moderation tooling, hybrid search, and AI content workflows.

#### Identity, reliability, and governance

- Contributed to the migration off home-grown auth onto Auth0 for OAuth 2.0/JWT across
  four applications and two subdomains with no disruption to signed-in users;
  integrated LinkedIn as an OIDC identity provider.
- Served in the Opsgenie on-call rotation; built outage runbooks; took turns
  running weekly postmortems with a root cause analysis required from the primary
  on-call; followed fixes with logging and an alert that fires if the issue recurs.
- Introduced merge-blocking CI gates (SonarQube, security scans, unit tests, lint
  and format checks, end-to-end suites), keeping a manual test step only where a
  test couldn't be automated; set up the same gates at b.well and Orion.
- Ramped new features, pages and data sources to production by percentage with
  GrowthBook wherever load was uncertain, and taught developers to use flags as
  kill switches and percentage ramps to shrink the blast radius of production
  issues; ramped the same way at b.well (CloudBees) and Expedia.
- Released to production multiple times a day as each feature completed.
- Shared remediation of SOC 2 and penetration-test findings; reviewed the Kue to
  BullMQ job-queue migration driven by a SOC 2 obligation.
- Facilitated monthly architecture forums, weekly domain-driven design sessions,
  weekly innersource check-ins on the shared UI library, and group code-review
  sessions.

#### Developer experience

- Engineered a multi-feature developer sandbox, first in Python and later a
  TypeScript CLI, on templated Docker Compose with a hybrid local/remote topology:
  environment setup fell from 2–3 days to about 30 minutes, local footprint from
  ~10 containers to 1–3, and time-to-first-contribution by 5×.
- Packaged the sandbox with skills connecting agents to Jira, GitHub, and Slack;
  partnered with Sales, Marketing, Support, and Research Ops to map workflows and
  trained non-engineering users on the AI tools delivered.

### b.well Connected Health — Principal Engineer / Principal Architect

January 2021 – September 2023 · Seattle, WA · Reported to the VP of Platform Engineering

- Co-architected an embeddable architecture, Web Components plus React Native,
  that let b.well ship its products into third-party web portals and into iOS and
  Android host apps from a single codebase, and composed them as micro-frontends
  with Feature Hub.
- UI lead architect for the b.well experience embedded in the Walgreens mobile
  app. Its first release shipped with bundle bloat that was only caught in
  production, so added build-system checks to stop it recurring.
- Packaged the shared UI and micro-frontend libraries with Rollup and tsup as ESM
  and CommonJS builds, composed at runtime through Feature Hub.
- Ran Apollo Client as the UI's normalized cache, with per-type freshness and
  eviction policies for the types the defaults handled badly.
- Secured embedded surfaces with OAuth 2.0 and encrypted JWTs under HIPAA and PHI
  handling constraints.
- Owned the foundational frontend and API decisions that became b.well's UI
  patterns: the component library, the micro-frontend libraries, feature flagging
  on CloudBees, and the GraphQL surface for the configuration API.
- Directed GraphQL/Apollo Federation strategy and domain-driven design for
  configuration services; authored the ADRs; routed micro-frontends with React
  Router loaders and actions and typed the UI with GraphQL Codegen.
- Integrated MedStar's b.well portal with Epic scheduling over Epic's Open
  Scheduling HL7 v2 API: ran the investigation, wrote the spec, and owned the
  mapping between Epic's scheduling data and b.well's model.
- Consumed FHIR (HL7 R4) resources for interoperability with health systems,
  EHRs, and partner platforms; contributed to b.well's open-source FHIR server
  (Node.js, MongoDB), making its GraphQL API an Apollo Federation subgraph on the
  supergraph, a change still in place on `main` three years on.
- Founded the UI component library and innersource program with weekly
  check-ins; led WCAG accessibility across every client surface.
- Spearheaded unit-test automation and GitHub Actions CI/CD, including custom
  reusable actions, enabling trunk-based development; built a structured logging
  library enforcing standards across services.
- Led the user engagement experimentation program measuring retention and feature
  effectiveness.
- Worked under weekly postmortems, HIPAA, SOC 2, and contractual SLAs to health
  systems, payers, and employers.

### Orion Advisor Tech — Software Architect

April 2020 – January 2021 · Seattle, WA

- Built and maintained Eclipse, Orion's portfolio rebalancing and trading platform
  for financial advisors: an AngularJS frontend over WebSockets, a C#/.NET backend
  on Azure, and an Express/Node.js business-rules application.
- Helped direct the offshore team building the rules layer behind rebalancing,
  trade execution, tax-loss harvesting, and model assignment, where calculation
  correctness is the product.
- Established the quality and testing strategy for the .NET application: static
  analysis, unit, integration, and UI automation.
- Advocated test-first development through pairing; introduced
  documentation-as-code with Cucumber.

### Expedia — Software Engineer → Senior Software Engineer

March 2010 – April 2020 · Bellevue, WA

- Re-architected the Hotel Search frontend, cutting render time from 14.5s to 3s.
- On the lodging shopping team, ran segment-based A/B experiments (leisure versus
  business travelers, prior-trip spend) measured on room nights booked and total
  spend; was on the pilot team that first put Expedia's "test-and-learn" program
  into practice, a program that went on to lift bookings 3% and revenue 20–30%.
- Contributed to and helped maintain the Hotel Shopping BFF APIs in Java on Spring MVC.
- Built Media Solutions ad units as self-contained Web Components (LitElement)
  integrated with Google Ad Manager across high-traffic pages, measuring their
  effect on above-the-fold render and guarding against malicious ad content.
- Developed the ad-metrics pipeline in Spark, Scala, and Hadoop on AWS over a
  Kafka ingestion stream landed in S3, including the EC2, IAM, and S3 setup it
  ran on.
- Contributed to the frontend redesign into a PWA on React, MobX, and TypeScript,
  including fixes for SSR hydration and serialization mismatches. Worked under
  automated bundle size budgets that made the developer split a bundle once it
  hit its threshold.
- Co-led an internal developer education program teaching structured web
  development to about 20 interns and junior engineers.
- Drove automated testing practices (unit, BDD, UI); advocated WCAG and OWASP
  practices into development and review; served in the Opsgenie on-call rotation
  using Splunk for triage.

### Jay Bird LLC — Founder & Principal Consultant

2011 – 2017 · Remote, alongside Expedia

- Built, hosted, and maintained Drupal/LAMP websites for local small businesses,
  including Drupal 6 to 7 migrations and MySQL administration.
- Built one client application on Spring Boot with Spring Data JPA.

### Amdocs — Software Engineer

February 2010 – March 2010 · Seattle, WA

- Developed account and permissions management UI with Google Web Toolkit on
  WebLogic, using Spring, Maven, JUnit, and Ext JS in a large Scrum team.

### LRN — Senior Software Engineer

August 2007 – January 2010 · Remote

- Built and enhanced enterprise ethics and compliance applications for Fortune
  500 customers, including security and reporting features driven by regulatory
  requirements.

### REBT (Real Estate Business Technologies) — Software Engineer

2005 – 2007 · Remote

- Developed full-stack web applications for real estate and financial services
  clients, placing business and query logic in Oracle PL/SQL to keep the UI thin.

### Nordstrom.com — Software Engineer

2003 – 2004 · Seattle, WA

- Engineer on the inventory and fulfillment team: inventory availability, order
  fulfillment routing, and allocation, reservation, and backorder handling for the
  online store.

### The Cobalt Group — Software Engineer

December 1998 – August 2003 · Seattle, WA

- Built dealer-facing web applications for automakers and dealerships across
  North America on high-traffic platforms for advertising, lead generation, and
  CRM.

## Personal Projects

### [Werkmeister](https://werkmeister.io/) — open source (2026–present)

- Built an orchestrator for developers stuck single-threaded, and for solo
  founders who want to ship with SDLC best practices like testing and CI gates:
  it runs many tickets at once, each in an isolated workspace with its own git
  worktree, generated Docker Compose services and routing. A ground-up rewrite of the
  developer sandbox HG Insights engineers use.
- Gave each work type its own staged workflow (bug: reproduce, fix, deploy,
  verify), with agents working autonomously and stopping only at
  human-judgment gates. A fresh subagent reviews each diff before the gate, and
  I run up to 8 features at once with it.
- Shipped a TypeScript monorepo of CLI, core library, dashboard, MCP server,
  VS Code extension and Claude Code plugin, published to npm with Changesets
  and OIDC trusted publishing. 985 commits since July 2026.

### Local agentic methodology coach (2026)

- Built a fully local RAG knowledge base over ArcadeDB on Apple Silicon: an
  11-vertex, 6-edge graph schema over methodology books, hybrid retrieval (HNSW
  vectors plus BM25 fused with Reciprocal Rank Fusion), and citation-grounded
  provenance back to page and section.
- Served it to a 4-agent LangGraph team over an MCP server with all inference
  local (Llama 3.3 70B, Qwen, bge-m3); instrumented with OpenTelemetry and a human
  review gate between extraction stages.

## Education

**University of Nebraska at Omaha** — Bachelor of Science

**IDEO U**, All-Access Pass — *Bringing AI to the Design Thinking Process* (in progress)

</div>
