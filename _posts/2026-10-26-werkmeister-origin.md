---
layout: post
title: "How Werkmeister started"
date: 2026-10-26 00:00:44 -0700
categories: werkmeister
permalink: /blog/werkmeister-origin/
---

It started with a time difference.

Our company opened an office in Pune, India, and we were hiring to fill it. Lots
of new developers, every one of them needing a working environment before they
could write a line of code.

Getting one took days. A new engineer spent two or three of them wiring up about
ten local containers, and no two environments came out the same. Their morning
was my evening, and their evening was my early morning, so every snag landed in
one or the other. I was walking people through setup one at a time and burning
the candle at both ends.

I didn't want a better onboarding doc. I wanted one command that brought
everything up, so nobody needed me awake for it.

The hard part was what *not* to run. Nobody needs the whole platform on their
laptop. You need the services you're about to change, and everything else should
come from the shared environment that's already running. So that became the
rule: run locally only what you change, and defer the rest to remote.

Setup went from days to about thirty minutes, and from ten containers to one to
three. Everyone started from the same baseline, and the drift stopped.

The team called the tool the developer sandbox. It ran one environment at a
time, for the feature you were working on right then. Switching to a bug fix
meant tearing that down, bringing up another, and finding your place again when
you came back. Context switching was hard because the tool made you pay for
every switch.

So it grew: from one environment for the feature in progress to many features at
once, each with an agent doing the work. That's Werkmeister.

Werkmeister is open: [werkmeister.io](https://werkmeister.io) · [GitHub](https://github.com/jbbz-sandbox/werkmeister).
