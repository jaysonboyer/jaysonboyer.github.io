---
layout: post
title: "How Werkmeister started"
date: 2026-10-26 00:00:44 -0700
categories: werkmeister
permalink: /blog/werkmeister-origin/
description: "A Pune office, a ten-container dev setup, and the one-environment sandbox that grew into Werkmeister."
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

What I wanted was one command that brought everything up, so nobody needed me
awake for it.

The hard part was deciding what to leave out. Nobody needs the whole platform on
their laptop, just the services they're about to change. Everything else can
come from the shared environment that's already running. That became the rule:
run locally only what you change, and use remote for the rest.

Setup went from days to about thirty minutes, and from ten containers to one to
three. Everyone started from the same baseline, and the drift stopped.

The team called the tool the developer sandbox. It ran one environment at a
time, for the feature you were working on right then. Switching to a bug fix
meant tearing that down, bringing up another, and finding your place again when
you came back.

So it grew, from one environment for the feature in progress to many features at
once, each with an agent doing the work. That's Werkmeister.

Werkmeister is open source: [werkmeister.io](https://werkmeister.io) · [GitHub](https://github.com/jbbz-sandbox/werkmeister).
