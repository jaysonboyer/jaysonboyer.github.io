---
layout: post
title: "Migrating to a Federated Graph Without a Freeze"
date: 2026-09-03 09:00:00 -0700
categories: architecture graphql
---

Placeholder. Draft outline:

- Keeping REST a first-class interface for the whole migration, versioned, with
  stable error envelopes.
- Onion architecture per service: REST and GraphQL as siblings over one service
  layer, so there's one set of rules and one cache.
- Backward-compatibility checks on every schema change, so the UI can move page
  type by page type.
- What the tracing showed once every subgraph leg was instrumented.
