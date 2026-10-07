---
layout: post
title: "Notes on Building an Eval Harness You Can Trust"
date: 2026-09-17 09:00:00 -0700
categories: ai evaluation
---

Placeholder. Draft outline:

- The failure mode: a test suite that measures the model's baseline competence
  rather than the change under test. Control arms fix this.
- Ground truth from disk state — SHA-256 diffs, behavioral code markers — instead
  of asking the model whether it complied.
- Small n read for direction, not effect size. Say so out loud.
- What's still missing: sampling real failure traces, and wiring the harness to
  block a merge instead of advising one.
