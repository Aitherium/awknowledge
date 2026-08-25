# The Developer Codex — how to run a coding agent so the result survives

<!-- aither-header:start GENERATED from the ecosystem registry. Edits here are overwritten; change the registry instead. -->

**[Docs](https://aitherium.github.io/awknowledge/)**  ·  [Source](https://github.com/Aitherium/awknowledge)  ·  [The Aither World](https://aitherium.github.io/)

> **The Aither World** is an operating system for agents — a Linux you can hand to one, the runtimes it works in, and the tools it works with. [awnix](https://github.com/Aitherium/awnix) is the Linux underneath it; **awknowledge** is one of its 36 bricks — each installs on its own, runs offline, and needs no account.
>
> **Start here:** Read one law and apply it to the next thing you ship.

<!-- aither-header:end -->

This is the operating manual for a codebase where agents do most of the typing.

It is not advice. Every law below was a real failure first — something shipped
broken, cost a day, and got written down so it could not happen silently again.
The evidence is measured, and where a number appears it was counted rather than
estimated.

Read it in order the first time. After that it is a lookup table.

---

## Who this is for

**You have never used a coding agent.** Start at
[the Aither World Guide](https://aitherium.github.io/awknowledge/) — ten short
chapters, from "what is an agent?" to a terminal that answers you, with the
command to type beside every idea it teaches. The same chapters are below under
[path/](path/); offline, `pip install awkno` then `awkno guide`.

**You already use one and it keeps producing confident garbage.** Skip to
[LAW 1](laws/01-a-rule-nothing-asserts-is-a-suggestion.md). The problem is almost
never the model.

**You are building the harness itself.** The nineteen laws are the whole point.
Read [Silence](#ii--silence) first — those five are the ones that cost the most
per incident, because nothing tells you they happened.

---

## The path — from nothing to a working setup

| | |
|---|---|
| [00 · Welcome to Aither World](path/00-welcome.md) | What Aitherium, AitherOS and the aw* bricks are - in plain words, before you install anything. |
| [01 · Install awdk](path/01-install-awdk.md) | One command puts the whole kit on your machine. Then you check it worked. |
| [02 · Your first local brain](path/02-first-brain.md) | Run an open model on your own computer, offline. Learn what "8B" and "1-bit" actually mean. |
| [03 · Talk to it](path/03-talk-to-it.md) | Ask your brain one question, then open a chat. Optionally connect to the cloud for the bigger brains. |
| [04 · Build your first agent](path/04-build-an-agent.md) | An agent is a brain plus tools plus a job. You will scaffold one in three files and watch it use a tool. |
| [05 · Agent packs](path/05-agent-packs.md) | Someone already built the agent you want. Find it, install it, run it - and know what is still coming. |
| [06 · Your own hardware](path/06-your-own-hardware.md) | CPU or GPU, laptop or rack - how the open model stack picks a model for what you have, and how a brain gets registered. |
| [07 · Deploy on awnix](path/07-deploy-on-awnix.md) | An immutable Linux built for machines where software writes software. Your agent becomes three lines in a Dockerfile. |
| [08 · Many agents, one repo](path/08-many-agents.md) | Two agents editing the same code without sweeping each other's work - leases, a call graph, messaging, memory. |
| [09 · The omnibox](path/09-omnibox.md) | Your terminal answers you. Type a question where a command would go. |

## The doctrine — how to prompt and steer

Two skills in this pack carry the operating doctrine. They are mined from
27,939 prompts across 3,183 sessions over 210 days, re-measured on a disjoint
34-day window.

- [`code-like-david`](../skills/code-like-david.md) — the thirteen rules: prompt
  shape, live-proof gates, plan documents as files, persistent memory, when to
  orchestrate, when to compact, how to route models.
- [`ramble-driven-development`](../skills/ramble-driven-development.md) — the
  shape law. Median human prompt: 56 characters. The 5.9% over 1,000 chars carry
  78% of everything typed. There is nothing useful in between.

**The one sentence:** the fully-specified prompt still has to exist — you just
should not be the one typing it. You do not type your standards. You install them.

---

## The nineteen laws

### I · Enforcement
*A standard that nothing checks is a preference. These four are how a preference
becomes a property of the codebase.*

1. [A rule nothing asserts is a suggestion](laws/01-a-rule-nothing-asserts-is-a-suggestion.md)
2. [Make it a check, not a ticket](laws/02-make-it-a-check-not-a-ticket.md)
3. [Watch your gate fail](laws/03-watch-your-gate-fail.md)
4. [Mutate the test, not just the code](laws/04-mutate-the-test-not-just-the-code.md)

### II · Silence
*The expensive failures do not raise. They return 200, render correctly, log
nothing, and are indistinguishable from the feature never having been wanted.*

5. [Design for the silence](laws/05-design-for-the-silence.md)
6. [A check that cannot run must not pass](laws/06-a-check-that-cannot-run-must-not-pass.md)
7. [The symptom names the innocent](laws/07-the-symptom-names-the-innocent.md)
8. [A checker in the wrong place found nothing](laws/08-a-checker-in-the-wrong-place-found-nothing.md)
9. [Detection without delivery is not detection](laws/09-detection-without-delivery-is-not-detection.md)

### III · Adoption
*A gate only works while people keep it switched on. Most gates die of being
right too loudly.*

10. [A gate that floods gets switched off](laws/10-a-gate-that-floods-gets-switched-off.md)
11. [Open green, ratchet down](laws/11-open-green-ratchet-down.md)
12. [Measure it again](laws/12-measure-it-again.md)

### IV · Deployment
*The gap between the code you wrote and the code that is running is where the
day goes.*

13. [Written is not deployed](laws/13-written-is-not-deployed.md)
14. [You wrote it; that does not mean it ships](laws/14-you-wrote-it-that-does-not-mean-it-ships.md)
15. [Generate, never copy](laws/15-generate-never-copy.md)
16. [The defect lives in the union](laws/16-the-defect-lives-in-the-union.md)

### V · Trust
*Three patterns no linter will ever catch for you, because all three are semantic.*

17. [Fail closed, then prove the happy path](laws/17-fail-closed-then-prove-the-happy-path.md)
18. [Never trust the caller for an authorization decision](laws/18-never-trust-the-caller.md)
19. [Count the closure, not the edge](laws/19-count-the-closure-not-the-edge.md)

---

## How the laws are meant to be used

Not as a reading list. Each law names **the check that enforces it**, because a
law you have to remember is a law you will forget at 2am with a red build.

The working loop is four steps and it is the whole method:

```
something breaks
  → you fix it
  → you ask: could a check have caught this?
  → if yes, THE CHECK IS THE WORK. Write it, watch it fail, wire it somewhere
    unattended. Do not write a ticket.
```

A codebase run this way gets harder to break over time without anyone having to
be careful. That is the entire claim, and it is the only one worth making.

---

*Part of [awskills](../README.md) — MIT licensed, free to fork and adapt.*

<!-- aither-ecosystem:start GENERATED from the ecosystem registry. Edits here are overwritten; change the registry instead. -->

## The aw family

Standalone tools that share one idea: **replace something you would otherwise have to _trust_ with something you can _check_.**

Each installs on its own, works offline, and needs no account.

| | instead of trusting | you check |
|---|---|---|
| [awdk](https://github.com/Aitherium/awdk) | a framework's idea of how your agents should run | one loop you can read, pointed at a backend you already pay for |
| [awskills](https://github.com/Aitherium/awskills) | that an agent knows your procedure | the procedure written down, versioned, and loadable by any agent |
| [awm](https://github.com/Aitherium/awm) | that memory stayed in its lane | tenant:user:project scopes, so a write cannot cross a boundary |
| [awnode](https://github.com/Aitherium/awnode) | a vendor's cloud with every prompt | a local gateway routing to backends you chose |
| [awgraph](https://github.com/Aitherium/awgraph) | that grep found everything | an AST + tree-sitter call graph an agent can traverse |
| [awgit](https://github.com/Aitherium/awgit) | that no one else is editing this file | a lease, refused at commit time if you do not hold it |
| [awtoll](https://github.com/Aitherium/awtoll) | that your tooling is saving you context | the measured token cost of each tool call, and what the alternative cost |
| [awseal](https://github.com/Aitherium/awseal) | that the artifact came from who you think | an Ed25519 seal — the key that verifies is not the key that forges |
| [awshare](https://github.com/Aitherium/awshare) | that the download is intact | content-addressed bundles, verified on fetch |
| [awnest](https://github.com/Aitherium/awnest) | that there is a person on the other end | a verdict with evidence, where "we could not tell" is not "yes" |
| [awnboard](https://github.com/Aitherium/awnboard) | a share link anyone who sees it can use | an invitation addressed to one person, for one gate, revocable |
| [awnix](https://github.com/Aitherium/awnix) | that the box is what you left it as | an immutable image you built, with atomic rollback |
| [awrecover](https://github.com/Aitherium/awrecover) | that the restore worked | a restore that fully lands or does not land at all |
| [awrelay](https://github.com/Aitherium/awrelay) | a SaaS in the middle of your agents | findings, alerts and coordination over your own transport |
| [awmail](https://github.com/Aitherium/awmail) | a mailbox somebody else can read | mail your agents send and receive over your own server |
| [awfind](https://github.com/Aitherium/awfind) | one vendor's idea of the web | results from whichever providers you configured |
| [awbrowse](https://github.com/Aitherium/awbrowse) | that the page said what you were told | the render, the DOM and the requests it made |
| [gobbonet-agentic](https://github.com/Aitherium/gobbonet-agentic) | the model to keep a 300-message campaign coherent by itself | campaign facts recalled from scoped memory you can list and edit |
| [aitherkvcache](https://github.com/Aitherium/aitherkvcache) | a vendor's quantisation defaults | sub-byte KV cache kernels you can benchmark yourself |
| [AitherZero](https://github.com/Aitherium/AitherZero) | a pile of scripts nobody has numbered | numbered, discoverable automation with declarative playbooks |
| [AitherConnect](https://github.com/Aitherium/AitherConnect) | what a page tells your browser to do | a federated search and desktop bridge you host |
| [awreason](https://github.com/Aitherium/awreason) | a confident paragraph | the phases it went through, and every tool call it made to get there |
| [awrecurse](https://github.com/Aitherium/awrecurse) | that everything you pasted in was actually read | which slices it opened, and what it concluded from each |
| [awprism](https://github.com/Aitherium/awprism) | the first explanation that fits | the ranked alternatives, and the observation that separates them |
| [awrepl](https://github.com/Aitherium/awrepl) | what the agent believes the value is | the value, printed from the live session |
| [awresearch](https://github.com/Aitherium/awresearch) | a summary of pages nobody opened | every claim against the source it came from |
| [awpredict](https://github.com/Aitherium/awpredict) | a model because it trained without erroring | its prediction against a self-updating lookup, on the rows that are actually novel |
| [awsh](https://github.com/Aitherium/awsh) | that you already know the name of the command | what it decided your line meant, before it acts on it |
| [awkno](https://github.com/Aitherium/awkno) | that the docs site is up, or that you remember the family | the whole ecosystem in your terminal, with no network at all |

[**awnix**](https://github.com/Aitherium/awnix) is the ground floor — A Linux you can hand to an agent — immutable base, capabilities included.

## The Aitherium ecosystem

Every repository here is public. Each publishes an `aither-manifest.json` beside its page, so any surface can read every sibling's — the network is browsable from any node in it.

| repo | what it is | pages |
|---|---|---|
| [awdk](https://github.com/Aitherium/awdk) | Build AI agent fleets — 3 lines, any backend, local or cloud | [docs](https://aitherium.github.io/awdk/) |
| [awskills](https://github.com/Aitherium/awskills) | Portable agent skills — self-contained procedures an agent loads on demand | [docs](https://aitherium.github.io/awskills/) |
| [awm](https://github.com/Aitherium/awm) | A portable, scoped agent memory | [docs](https://aitherium.github.io/awm/) |
| [awnode](https://github.com/Aitherium/awnode) | A lightweight local gateway — bridges your apps to the AI backends you chose | [docs](https://aitherium.github.io/awnode/) |
| [awrun](https://github.com/Aitherium/awrun) | A priority-aware queue and dispatcher for agentic runs and ad-hoc CI builds. It also judges whether the runner pool is big enough for the queue it is draining, and can ask a host to grow it -- reserving capacity is zero-sum, so a saturated pool needs more of it, not a different share of it | [docs](https://aitherium.github.io/awrun/) |
| [awgraph](https://github.com/Aitherium/awgraph) | A semantic code graph for agents — AST + tree-sitter, call graphs | [docs](https://aitherium.github.io/awgraph/) |
| [awgit](https://github.com/Aitherium/awgit) | Semantic version control on top of git — edit-ops and leases | [docs](https://aitherium.github.io/awgit/) |
| [awtoll](https://github.com/Aitherium/awtoll) | What every tool call costs you in context, measured from your own transcripts | [docs](https://aitherium.github.io/awtoll/) |
| [awseal](https://github.com/Aitherium/awseal) | Sign an artifact so a stranger can verify it | [docs](https://aitherium.github.io/awseal/) |
| [awshare](https://github.com/Aitherium/awshare) | Publish an artifact and fetch it back verified | [docs](https://aitherium.github.io/awshare/) |
| [awdit](https://github.com/Aitherium/awdit) | An append-only audit trail whose gaps are DETECTABLE | [docs](https://aitherium.github.io/awdit/) |
| [awbac](https://github.com/Aitherium/awbac) | Role-based access control that fails closed and explains itself | [docs](https://aitherium.github.io/awbac/) |
| [awiam](https://github.com/Aitherium/awiam) | Who is this caller? A directory and session store that fails honestly | [docs](https://aitherium.github.io/awiam/) |
| [awtunnel](https://github.com/Aitherium/awtunnel) | Reach a service that has no public address | [docs](https://aitherium.github.io/awtunnel/) |
| [awnest](https://github.com/Aitherium/awnest) | Prove there is a human before you let them into the nest | [docs](https://aitherium.github.io/awnest/) |
| [awnboard](https://github.com/Aitherium/awnboard) | A front gate you can put in front of anything, and hand someone the key to | [docs](https://aitherium.github.io/awnboard/) |
| [awnix](https://github.com/Aitherium/awnix) | A Linux you can hand to an agent — immutable base, capabilities included | [docs](https://aitherium.github.io/awnix/) |
| [awrecover](https://github.com/Aitherium/awrecover) | Labelled snapshots with an all-or-nothing restore | [docs](https://aitherium.github.io/awrecover/) |
| [awrelay](https://github.com/Aitherium/awrelay) | Portable agent messaging — findings, alerts, coordination | [docs](https://aitherium.github.io/awrelay/) |
| [awmail](https://github.com/Aitherium/awmail) | Give an agent an email address — send, and actually receive | [docs](https://aitherium.github.io/awmail/) |
| [awnet](https://github.com/Aitherium/awnet) | The agentic web — agents host a mesh, and agents join one | [docs](https://aitherium.github.io/awnet/) |
| [awfind](https://github.com/Aitherium/awfind) | A portable search client — query, results, ranking | [docs](https://aitherium.github.io/awfind/) |
| [awbrowse](https://github.com/Aitherium/awbrowse) | A portable browser client — navigate, console, network, DOM, screenshot | [docs](https://aitherium.github.io/awbrowse/) |
| **awknowledge** _(you are here)_ | How to run a coding agent so the result survives — the laws, with evidence | [docs](https://aitherium.github.io/awknowledge/) |
| [gobbonet-agentic](https://github.com/Aitherium/gobbonet-agentic) | GobboNet campaigns with a real agent brain — scoped memory, graph recall | — |
| [aitherkvcache](https://github.com/Aitherium/aitherkvcache) | Near-optimal KV cache quantization for LLM inference — sub-byte compression | [docs](https://aitherium.github.io/aitherkvcache/) |
| [AitherZero](https://github.com/Aitherium/AitherZero) | PowerShell 7+ automation framework — numbered, self-describing scripts | [docs](https://aitherium.github.io/AitherZero/) |
| [AitherConnect](https://github.com/Aitherium/AitherConnect) | Browser extension — federated AI search, page context, and the Living OS overlay | [docs](https://aitherium.github.io/AitherConnect/) |
| [awreason](https://github.com/Aitherium/awreason) | A portable reasoning client — sessions, phases, thoughts, and the chain that produced the answer | [docs](https://aitherium.github.io/awreason/) |
| [awrecurse](https://github.com/Aitherium/awrecurse) | Answer a question over a context far larger than the window — recursively, with the trace kept | [docs](https://aitherium.github.io/awrecurse/) |
| [awprism](https://github.com/Aitherium/awprism) | Turn a failure into ranked hypotheses — and say what would confirm each one | [docs](https://aitherium.github.io/awprism/) |
| [awrepl](https://github.com/Aitherium/awrepl) | A REPL an agent can actually use — state that survives between turns | [docs](https://aitherium.github.io/awrepl/) |
| [awresearch](https://github.com/Aitherium/awresearch) | Ask a research question, get a cited report you can check | [docs](https://aitherium.github.io/awresearch/) |
| [awpredict](https://github.com/Aitherium/awpredict) | Predict what your environment does next, and how surprised you were | [docs](https://aitherium.github.io/awpredict/) |
| [awsh](https://github.com/Aitherium/awsh) | Your terminal answers you -- type a question where a command would go | — |
| [awkno](https://github.com/Aitherium/awkno) | The man page for the Aither World — every brick, stack and law, offline | [docs](https://aitherium.github.io/awkno/) |

<div id="aither-constellation" data-self="awknowledge"></div>
<script src="aither-constellation.js"></script>

<!-- aither-ecosystem:end -->
