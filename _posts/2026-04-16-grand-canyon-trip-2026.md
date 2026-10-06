---
layout: post
title: I Used OpenClaw to Co-Pilot Our Family Vacation. Here's What I Learned.
date: 2026-04-16
byline: By JJ · Powered by OpenClaw
footer_note: Written by JJ · April 2026 · Built with OpenClaw
---

TL;DR: I used an AI assistant running on Claude, Codex, and GitHub Copilot to plan a family road trip through Zion, Page, and the Grand Canyon. The surprising part was that switching models barely changed anything. The useful part was everything around the model: memory, context, tools, and autonomy.
{: .lede}

<div class="toc" markdown="1">
In this post

* TOC
{:toc}
</div>

## A moment on the Zion shuttle

It was Monday afternoon. We were on the Zion National Park shuttle — my wife, my 12-year-old daughter, my 16-year-old son, and me. We'd just had lunch at a tiny Mexican place called La Fonda Grill, chosen completely at random.

My daughter grabbed my phone and sent Zhu Li a message from the shuttle while signal came and went:

> We ended up having lunch at a random Mexican restaurant named La Fonda Grill, and all of us loved it. Mom said it's the best Mexican food she had ever tasted. Can you recommend more Mexican food in the next few days?

By the time we got off the shuttle and had reception again, Zhu Li had already recalibrated the rest of the trip’s food plan: more Mexican, more regional food, less Thai, Chinese moved way down the list.

It was exactly right. And it happened while we were riding a bus through a canyon with spotty signal.

That’s when it clicked for me: the interesting part wasn’t the model. It was the system.

## Wait — isn't this just ChatGPT?

Not really.

Zhu Li is running on the same families of models most people already have access to: Claude, GPT, GitHub Copilot. I started with Claude directly through Anthropic, then later switched to Codex and Claude through GitHub Copilot. For web search I used Gemini with DuckDuckGo. I swapped models a few times during the trip.

And almost nothing changed.

The itinerary didn’t get worse. The food recommendations didn’t get worse. Zhu Li didn’t suddenly forget the family, the bookings, or the trip context.

That’s because the memory, context, and tools live in the infrastructure, not in the model alone.

Most AI tools give you a brain in a tab. Open it, ask something, get an answer, close it. The model is impressive, but it’s isolated.

With OpenClaw, the AI is inside your world.

## The four real reasons it worked

### 1. Same brain, different nervous system

The model is the intelligence. But intelligence without agency is just a very smart conversation partner.

What OpenClaw adds is a nervous system: persistent memory on disk, access to the file system, shell commands, cron jobs, GitHub pushes, and messaging.

That meant Zhu Li didn’t just suggest things. It could actually do them:

- update the itinerary
- commit the changes
- push them to GitHub
- send me the link
- set up scheduled reminders
- build supporting pages and scripts

Same intelligence. Very different capability.

### 2. Context is the product

The reason Zhu Li felt smarter over time wasn’t that the model improved.
It was that I stopped re-explaining myself.

Preferences, bookings, family details, and trip constraints accumulated in memory files that Zhu Li reads at the start of each session. By mid-trip, I could text something like “help me plan tomorrow” and get a response that already knew the family, the route, the hotels, and the food preferences.

That kind of context is not a nice-to-have. It’s the product.

### 3. The interface changes the behavior

When AI lives in a browser tab, you use it like a search engine: ask a question, get an answer, close it.

When AI lives in messaging, you use it like a person. You send fragments. Half-formed thoughts. Ideas while driving. Questions from a shuttle bus with one bar of signal.

That changed how I used it.

The trip wasn’t planned in one polished session. It was assembled from dozens of tiny messages, corrections, and follow-ups. My daughter even said, “Dad, you’re so organized this time.”

I wasn’t.

Zhu Li was organized. I just kept sending raw thoughts.

### 4. The autonomy gap

Most AI tools are reactive. They wait for you to ask.

Zhu Li didn’t always wait.

It could push commits, build pages, wire up scripts, and report back without needing a fresh instruction every time. That’s the difference between a tool you consult and an assistant that works.

That autonomy gap mattered more than model quality.

## Why the usual tools didn’t get me here

<div class="callout" markdown="1">
**Google** is great at finding things that already exist. It doesn’t synthesize them into a plan that knows your family.
</div>

<div class="callout" markdown="1">
**ChatGPT and Claude** are excellent at one-shot sessions, but they’re still basically stateless across time in the way that matters for real life.
</div>

<div class="callout" markdown="1">
**Claude Code and Codex** are powerful, but they’re aimed at a developer working at a desk, not a parent texting from a shuttle bus.
</div>

<div class="callout" markdown="1">
**OpenClaw** sits in the middle of real life:

- persistent memory
- Telegram-native messaging
- filesystem access
- real-world actions
- ambient presence
</div>

The model underneath may be the same. The difference is everything around it.

## The honest bits

A few limitations are real:

- Sessions reset between conversations unless memory files are updated.
- The model can be confidently wrong.
- Infrastructure can be brittle; scheduled jobs can get lost.
- Human judgment still matters for the real calls.

I don’t think that weakens the story. It just keeps it honest.

## What this points to

We’re in a strange and interesting moment.

The models are already good enough to be useful. The bigger question is why they still feel incomplete in daily life.

My guess: the missing piece is infrastructure.

The trip is just one example, but it’s a good one. The same models that power ChatGPT and Claude, wrapped in the right system, turned a chaotic family vacation into something my daughter called “organized.”

<div class="thesis" markdown="1">
That’s not a model improvement.<br>It’s an infrastructure improvement.
</div>

And I think that’s where a lot of the real value in AI is going to come from next.

If you want to see the original artifact this came from, it started as a story page here:

<https://jjgao.github.io/Grand-Canyon-Trip-2026/story.html>

The Grand Canyon was spectacular. Zion was beautiful. And one of the best meals of the trip was a random Mexican place we found by accident — no algorithm, no Yelp, no AI recommendation.

Just a door we walked through.
