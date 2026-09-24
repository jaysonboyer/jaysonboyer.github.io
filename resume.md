---
layout: page
title: Resume
permalink: /resume/
---

<div class="resume" markdown="1">

**Principal Software Architect**

Contact via [LinkedIn](https://linkedin.com/in/jaysonboyer/)

## Summary

Principal software architect with 20+ years building consumer-scale platforms and
15+ years designing large-scale distributed systems, 10+ of them cloud-native.
Recent work is production AI: agentic workflows, MCP servers, and the evaluation
and observability that keep them honest. Equally comfortable in federated GraphQL
schema design, Kubernetes capacity work, and a jobs-to-be-done interview.

## Technical Skills

**Languages:** Java, TypeScript/JavaScript, Python, Scala, C#, GraphQL, SQL

**AI & Agents:** Anthropic Claude API, Claude Agent SDK, OpenAI API, Google ADK,
LangChain/LangGraph, CrewAI, MCP server development, RAG & hybrid retrieval,
prompt and context engineering, adversarial eval harnesses, agent tracing and
cost instrumentation

**Backend & API:** NestJS, Node.js, Apollo Federation, REST, domain-driven design,
onion architecture, Spring MVC

**Frontend:** React, React Native, Web Components (LitElement/lit-html), MobX,
Next.js, micro-frontends, WCAG accessibility

**Data & Search:** Postgres, MongoDB, Redis, Typesense, BigQuery, Airflow, Kafka,
Spark, ArcadeDB (graph + vector)

**Infrastructure:** GKE/Kubernetes, Docker Compose, GitHub Actions, Cloudflare,
AWS, GCP, Terraform-adjacent Helm configuration, JMeter

**Observability:** OpenTelemetry, DataDog, New Relic, Splunk, Google Cloud Logging,
Opsgenie on-call

## Professional Experience

### HG Insights (formerly TrustRadius) — Principal Engineer

September 2023 – July 2026 · Remote

- Led the AI strategy: a customer-facing Python/Google ADK agent on the buyer site
  that summarized verified reviews in real time, backed by a TypeScript MCP server
  exposing platform data as its tool surface.
- Built an adversarial eval harness for agent behavior — pre-declared pass/fail
  markers, control arms, ground truth read from disk state rather than model
  self-report — and used it to isolate which half of a two-part fix carried the
  effect (0/3 → 3/3).
- Built a context management system for AI coding agents: ephemeral per-ticket
  workspaces generated from declarative config, phase-gated read-only research,
  and a durable notes ledger re-injected after compaction. Deterministic
  phase-entry gating beat model-side matching 15/15 against 0/16.
- Pioneered a federated GraphQL strategy, decomposing the monolith into subgraphs
  and migrating 4 of the 6 highest-traffic page types onto the unified graph.
- Led load testing and spike hardening — Helm autoscaling, MongoDB indexing,
  Redis caching, circuit breakers, edge caching — targeting a 4× traffic spike;
  the platform absorbed 17×.
- Drove web performance to eliminate all "Poor" mobile Core Web Vitals (50% → 0%),
  measured against CrUX field data rather than lab simulation.
- Built the AI-visibility pipeline for AEO/GEO: Cloudflare crawler logs plus
  Conductor prompt-tracking into BigQuery, surfaced in Looker.

### b.well Connected Health — Principal Architect

January 2021 – September 2023

- Co-architected an embeddable architecture — Web Components plus React Native —
  that let b.well ship its products into third-party web portals and into iOS and
  Android host apps from a single codebase.
- Secured those embedded surfaces with OAuth and encrypted JWTs under HIPAA and
  PHI handling constraints.
- Directed GraphQL/Apollo Federation strategy and domain-driven design for
  configuration services; authored the ADRs.
- Founded the UI component library and innersource program, and led accessibility
  (WCAG) across every client surface.

### Orion Advisor Tech — Software Architect

April 2020 – January 2021

- Worked on Eclipse's Express/Node.js business-rules layer — the eligibility and
  calculation logic behind portfolio rebalancing, trade execution, and tax-loss
  harvesting under financial services regulatory constraints.
- Established the quality and testing strategy for a C#/.NET trading application,
  including static analysis, unit, integration, and UI automation.
- Introduced documentation-as-code with Cucumber.

### Expedia — Software Engineer → Senior Software Engineer

March 2010 – April 2020

- Re-architected the Hotel Search frontend, cutting render time from 14.5s to 3s.
- On the lodging shopping team, ran segment-based A/B experiments measured on room
  nights booked and total spend; was on the pilot team that first put Expedia's
  "test-and-learn" program into practice.
- Built Media Solutions ad units as self-contained Web Components integrated with
  Google Ad Manager across high-traffic pages.
- Developed the ad-metrics pipeline in Spark, Scala, and Hadoop on AWS.
- Co-led an internal developer education program for interns and junior engineers.

### Earlier

Jay Bird LLC (founder, Drupal/LAMP consultancy, 2011–2017) · Amdocs ·
LRN (senior software engineer, ethics & compliance platforms) ·
REBT · Nordstrom.com (inventory and fulfillment) ·
The Cobalt Group (automotive digital marketing)

## Education

**University of Nebraska at Omaha** — B.S., Biology

**IDEO U**, All-Access Pass — *Bringing AI to the Design Thinking Process* (in progress)

</div>
