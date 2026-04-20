---
layout: notebook
title:  "Notes from building Clo-Author"
classes: wide
use_math: false
date:   2026-04-19 10:00:00 -0400
categories: notebook
excerpt: "Kicking off a series of notes on building <a href='https://github.com/hugosantanna/clo-author'>Clo-Author</a>."
---

I am an AI skeptic. Or I was. Or I still am, sort of — it's complicated, and that's actually the reason I started building [Clo-Author](https://github.com/hugosantanna/clo-author).

I've been at it for months. This post (and the ones that follow) is me writing down what I've found. Less a tutorial, more a notebook: what I tried, what broke, what surprised me, what I changed my mind about.

## What Clo-Author is

A [Claude Code](https://docs.anthropic.com/en/docs/claude-code) scaffold for empirical economics research. It started as a fork of [Pedro Sant'Anna's claude-code-my-workflow](https://github.com/pedrohcgs/claude-code-my-workflow) and I reoriented from lecture production to research papers. My idea was to become the principal investigator of a team of virtual research assistants.

The novelty in the architecture is actually pretty simple. It's around **worker-critic pairs**: every phase in the research pipeline has a worker-critic pair: the worker creates and cannot audit; the critic audits and cannot edit. One pair for literature review, another for data search, etc etc.

Picture Karl Popper's epistemology, raised by the Separatist Army.

![Battle droids from the Separatist Army](/assets/images/clo-author-separatists.jpg){: width="50%" style="display:block; margin:0 auto;"}

Every creator gets shadowed by a critic that exists only to attack it. The librarian writes a literature review; the librarian-critic hunts for missed papers and weak framings. The coder ships a script; the coder-critic stress-tests it. Nothing gets through without surviving a refutation attempt.

Looks absurd from outside — half the army exists to fight the other half. But I think it's the only setup that keeps a creator agent honest. Left alone, no matter how good the prompt, they all start believing their own drafts.

The scoring side has quality gates so a paper can't ship with one weak section masked by strong others. There's also a simulated peer review pipeline (`/review --peer [journal]`) that runs an editor desk review, assigns two referees with intellectual dispositions weighted by the journal's culture, and produces an editorial decision with FATAL / ADDRESSABLE / TASTE classifications.

Very cool. Does it work?

## Why I'm writing this series

Two reasons.

Before I get to those — a detour.

Most AI users, and most non-users, still think AI is just ChatGPT. Heck, even people using Claude Code are still debating whether "it p-hacks or not." Lols. Let me humbly attempt to convince you that those discussions are somewhat pointless — all the same critiques apply in a world without AI. Yeah, the AI will p-hack. So will your Ph.D. student. Yeah, the AI will hallucinate. Yes — just like an RA reads a paper and misinterprets it completely. At the end of the day, it's your judgment call, not the machine's. It's like blaming a Canon DSLR for taking bad photos.

Anyway. The reasons.

First, every time I extend the scaffold, I learn something about how Claude Code behaves under sustained, structured workflows that I didn't expect from one-shot prompting. Compaction discipline, demand-loading reference files, the difference between an agent that drafts and an agent that scores — these are real design choices with real tradeoffs, and I keep rediscovering the same lessons because I never wrote them down.

Second, I think more economists should be building infrastructure like this for themselves, and I'd rather show the rough edges than pretend it's polished. The README sells the architecture. These posts will document the messy parts: the agent that hallucinated a citation, the rubric that was too lenient, the refactor that broke three workflows, the moment I realized the writer was just paraphrasing the theorist instead of writing.

If you want to follow along, the repo is [here](https://github.com/hugosantanna/clo-author) and the live guide is at [hsantanna.org/clo-author](https://hsantanna.org/clo-author/). Feedback welcome — open an issue or email me. Especially if you're an economist tinkering with something similar.