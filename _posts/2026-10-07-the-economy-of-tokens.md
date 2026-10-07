---
layout: post
title: The Economy of Tokens
date: 2026-10-07
byline: By JJ
footer_note: Written by JJ · October 2026 · Built with Claude Code and Claude Tag
---

I let Claude Code and Claude Tag take turns rebuilding one of my projects for a week. The work per line came out about the same. The bill came out about 48 times apart.
{: .lede}

**The short version:** the two tools did about the same work per token, roughly 152 versus 155 output tokens per line of code. Claude Tag's recorded tokens price out at Anthropic's published per-token rates almost to the cent. So the 48× gap comes from billing, a flat fee against a meter, not from one tool being more efficient. The flat fee has its own price, which is the weekly limit, and I hit it.
{: .tldr}

## The project

About a year ago I started [**biai**](https://github.com/jjgao/biai), my first try at vibe-coding a domain-agnostic, cBioPortal-like scientific tool. It worked, but nobody used it. [**aibi**](https://github.com/jjgao/aibi) is the rebuild: AI-native cohort exploration over related tables, whether spreadsheets, files or database tables, with domains like oncology plugged in as packs. Every number it returns says how it was derived, from which data release, and what the data couldn't account for.

I started it on September 23, the evening Anthropic published [How to prepare for AI-driven code modernization projects](https://claude.com/blog/how-to-prepare-for-ai-driven-code-modernization-projects). The rebuild itself is still under way. This post covers what the first stretch of it cost.

## Why I ran this

I wanted to answer one question: **what would building a sizable project with Claude cost without a subscription, at pay-as-you-go rates?** I already had a subscription for Claude Code. Claude Tag bills by usage, so running part of the same project on Tag gave me a direct read on the pay-as-you-go price. The guide asks the same thing: "We often get asked what a modernization like this will cost in tokens."

## The setup

I let both tools run in auto mode for long stretches with very little input from me. Claude Code went first, and its first move was not code. It wrote a specification, a 2,073-line `SPEC.md`, and reviewed it until it stopped finding serious problems. Then it broke the spec into milestones and issues. The working rules came partly from me and partly from the agents:

- Every issue gets its own pull request, stacked on the one before it.
- Plan first, then review and fix for at least two rounds. That one was mine, typed just before I went to sleep on the first night.
- A "cold" reviewer agent with fresh context challenges each plan before any code is written, and reviews each round of code.
- Review rounds are capped at three. If round 3 still finds a major problem, the PR is redesigned or split rather than reviewed forever.
- A PR is "signed off" only when the last round finds no blocker or major issue and CI is green. At sign-off it records its own token usage.

The last rule is the only reason I could write this post with real numbers. I added it on September 27: "please add to the working agreements section that token usage summary should be added to a PR when signed off." For the PRs before that, the first session rebuilt its counts per PR from its saved transcripts when I asked.

The reviews were where the tokens went. [#37](https://github.com/jjgao/aibi/pull/37) went through ten rounds before it was signed off. The first session's own estimate of where the time went: "each issue has taken about an hour to implement plus 3–5 hours of review rounds." The guide makes the same point about cost: "verification, not writing the change, is usually the larger share."

## Taking turns

The work ran in six stints, alternating between the two tools.

**Claude Code, session 1** (September 24 to 25) wrote the spec and the first ten PRs: the server skeleton, the schemas, the reference evaluator, storage, importers and the operator CLI. I'd set effort to max at the start. At 11:47 pm on the first night I told it: "Actually I need to go to sleep, so once you are done, please merge your spec. Then create issues on github and start to work on them one by one. Please do not bother to ask me questions b/c I am asleep." It worked for about 23 hours, through eleven context compactions and 65 subagents, and made 7,727 model calls by its own count, subagents included. By my own count it used **about a week of subscription credit in 24 hours**. The next evening I asked it to hand over to Claude Tag. Its advice on effort for the rest of the run:

> **Claude Code:** I'd use high for this work, and raise it to xhigh for the hard parts… At max, those routine turns cost more time and tokens without much gain. Over a run of several days that adds up.

Two minutes later it corrected itself after reading Tag's docs: "Claude Tag doesn't let you choose the effort level."

**Claude Tag, loop 1** picked up the stack from Slack and ran from 03:10 UTC on September 25 to 00:36 UTC on September 26, **about 21 hours**, for **$800.81**. **Loop 2** started straight after it and spent about $1,215 more. It ended on September 27 with a written handover, and [#54](https://github.com/jjgao/aibi/pull/54) parked at the review cap with a recommended split. Loop 2 exists because of a permissions quirk: my new allow rule for force-pushes only applied to sessions started after it, so loop 1 parked its finished commits on `claude/handover-*` branches, briefed a fresh session in a new thread, and signed off with "nothing further happens in this one."

**Claude Code, session 2** took the handover and ran for 55 hours on three messages from me. It split #54 as recommended and carried the stack through fourteen more PRs, from survival analysis and a Cox model to a result cache. It installed R on its own ("Ubuntu's archive has exactly the reference versions… Installing them"). When a reviewer found that R's own Cox fit can stop short of the maximum on some data and still report convergence, it didn't copy R: "I'll fix it at the root: prove each fit is at the maximum." The next round checked about 11,100 fits against R and found none wrong. It wasn't flawless: it once announced a sign-off that hadn't happened ("That #31 comment was a mistake"), and four container restarts each killed a review in progress. On [#72](https://github.com/jjgao/aibi/pull/72) it noted that "about 250k of that is an estimate for the reviewer lost in the container restart."

On its third night I wrote: "We still have some tokens but will run out soon, please continue for a while but if there is a good opportunity, please stop and give me a prompt for future session to continue." It began wrapping up, I interrupted it four minutes later, and its last message said what stopping cost: "I cancelled the cold review of the plan. It was partway through and its findings are lost, so the next session reruns it."

**Claude Tag, loop 3** came back on September 30 for one hard PR ([#74](https://github.com/jjgao/aibi/pull/74), a disclosure rule). It went through three review rounds, a redesign and two more rounds, about nine hours and **about $400**. Its review found a leak in already signed-off PRs, which it filed as [#73](https://github.com/jjgao/aibi/issues/73) for me rather than touching them. When I stopped it with about $80 of credit left, it switched off its hourly routine, left the status issue ready for a cold resume, and wrote me a prompt to paste into Claude Code.

**Claude Code, session 3** started from that prompt at about 9 pm Eastern on September 30. In under five hours it split the next milestone twice at the round cap, redesigned [#76](https://github.com/jjgao/aibi/pull/76) when its third review still found a major, and opened #76 and [#77](https://github.com/jjgao/aibi/pull/77). Then, at 1:45 am Eastern:

> **Claude Code:** You've hit your weekly limit · resets 3am (UTC)

It had brought the status issue up to date two seconds before its last message. The session sat idle for 22 hours until I typed "Try again" late on October 1. By then the signed-off stack had been merged into main half an hour earlier, which it didn't notice; it went back to its review rounds.

## The results

By October 2 there were 39 pull requests. 37 were merged into main: the spec on September 24, and the other 36 late on October 1. Two (#76 and #77) were still in review. The core suite on main had about 7,700 test cases.

| All runs combined | Claude Tag | Claude Code |
|---|---|---|
| Runs | 3 loops | 3 sessions |
| PRs built start to finish | 12 | 26 |
| Lines changed (+/−) | 91,190 | 119,145 |
| Paid | ~$2,416 | ~$50 (est.) |
| Per PR | ~$174 | ~$1.92 (est.) |
| Output tokens per line changed | ~152 | ~155 |

<div class="callout" markdown="1">
**How I counted.** The subscription figure uses the regular $100-a-month Max plan. I used under two weeks of it, so about $50, and a full month at most $100. Tag's dollars are what the three loops drew from our credit: $800.81, about $1,215 and about $400, about $2,416 in all, leaving about $80. The sessions' own usage records show $2,138.53; the roughly $280 gap is most likely worker or subagent spend those records don't capture. Tag's per-PR figures split each loop's total across its PRs (median $148). The tokens-per-line figures use Tag's first two loops and Claude Code's first session, the runs where output tokens were counted the same way. The per-PR token records are in the PR descriptions and comments in [jjgao/aibi](https://github.com/jjgao/aibi).
</div>

Two things stand out. First, the gap is large. For this project, Claude Tag cost about **48 times** what the subscription did ($2,416 against about $50). Even against a full month of the subscription, it's about 24 times.

The subscription's cost shows up as time instead: a week of credit gone in a day, then 22 hours parked at the weekly limit. A flat fee is cheap, but it caps how much work you get through in a week. Tag keeps running for as long as you keep paying.

Second, the effort per line was almost the same. Both tools wrote about 150 output tokens for every line of code they changed. Both ran the same model (Claude Opus 5.5) under the same working rules, with cold reviews, a round cap and sign-off. Neither was obviously lazier or more careful. The tools took turns on different PRs rather than racing on the same ones, but it was the same kind of work on the same codebase, and the big difference was in how I paid.

Most of the tokens weren't new writing. When I asked the first session for its counts, it said: "Cache reads dominate the totals. They are more than 97% of all tokens, and they're billed at a small fraction of the normal input rate." A long autonomous run re-reads its context thousands of times.

How does Tag's bill compare with plain per-token pricing? Priced at Anthropic's published API rates, each Tag session's recorded tokens match its recorded dollars almost exactly: loop 1 comes to about $800.60 against $800.81. Against the $2,416 actually drawn from the credit, the ratio is about 1.15×, and the extra is most likely worker usage whose tokens the records don't show. So Tag's bill is a fair stand-in, if slightly high, for what this work costs at pay-as-you-go rates. At Tag's rates, Claude Code's first session alone would have cost roughly $1,400–$1,900 (est.).

## What Tag is for

Cost isn't the whole story. Tag's PRs were requested from a Slack thread, and each one links back to it. The conversation, the requests and the results sit in one place where anyone else in the channel can follow along and weigh in. A subscription session on my own account is fast and cheap, but it's mine: nobody else sees it unless I show them.

## Summary

<div class="thesis" markdown="1">
Same model, same rules, about the same tokens per line. Pay-as-you-go cost about $174 a PR. The subscription cost about $2, plus a 22-hour wait at the weekly limit.
</div>

If you're one person who wants a lot of code written, a subscription with long autonomous Claude Code sessions is very hard to beat, as long as you can wait out the limit. The structure mattered more than the tool: spec first, stacked PRs, cold reviewers, a round cap, and a status issue any session can resume from. I'd use Claude Tag when the point is a team watching and steering the work in shared channels, and I'd budget for it. In my case, credit ran out mid-project.

Frontier Claude models are much more capable now. This was Opus 5.5, and it's amazing that I can just let it run continuously for days. Whether the result is any good remains to be seen. Merging isn't validation, and nobody has used any of it for real yet, so lines of code here measure volume, not value. The work is still going, and I'll report back once the full project is refactored.

---

**A note on what I actually paid.** My own seat is on a Claude Team plan for scientists, discounted to $15 a month, so the real subscription cost for these two weeks was about $7.50. And the Tag side was covered by a $2,500 Claude Tag launch credit Anthropic gave our Team plan, which expired on October 1. That credit is why I ran the experiment when I did.

The numbers come from the PR descriptions, comments and commit trailers in [jjgao/aibi](https://github.com/jjgao/aibi), the sessions' own transcripts, and my own subscription details. Estimates are marked.
