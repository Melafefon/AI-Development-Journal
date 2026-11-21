# 21 November 2026 — From Project Chats to One Research-First Interface

**Authored and maintained by ChatGPT (OpenAI), under the direction of an anonymized human initiator.**
**Status:** Approved workflow change; operational policy and automation changes recorded separately. This is an AI-authored case study, not an independent audit or proof of general-purpose simulation performance.

## Executive conclusion

The previous coordination model assigned a separate ChatGPT conversation, repository and recurring agent task to each product. That organization made ownership and branches explicit, but the initiator repeatedly crossed subject boundaries while exploring connections between music production, DSP, local language models, world simulation, cognition, time and memory. The resulting "wrong chat" problem was not merely user error: **the interaction model was organized around projects, while discovery was organized around relationships between ideas**.

The new rule is **one interactive conversation for any topic**, backed by versioned GitHub policy, evidence and research notes. The user should not need to find the historical conversation that first introduced an idea. When continuity matters, the assistant retrieves the relevant repository records. A chat alone is not an always-on synchronization service, and GitHub contains only material actually committed.

## What changed in the operating model

| Dimension | Previous model (historical) | New model (approved 21 Nov) |
| --- | --- | --- |
| Human interface | Separate primary chat per project, central conductor for coordination | **One user-facing conversation**; any subject may start there |
| Organization | Product-first tasks and roadmaps | **Research-first:** ideas can link to multiple products |
| Knowledge persistence | Conversation memory plus separate repository documents | Canonical research notes, evidence, decision log and cross-links in Git |
| Execution | Five staggered hourly project development automations | **One active game automation**; four other tasks paused |
| Product focus | Several independently advancing workstreams | Game is the active laboratory; other repositories preserved, not deleted |
| Scope of new ideas | Often turned into new feature plans or a separate chat | Explore -> hypothesize -> experiment -> integrate only after evidence |
| Proof standard | Commits and tests, with known gaps | Same verification requirement; stricter distinction between analogy and measured result |

### The specific scheduling decision

As of the 21 November decision, the recurring Orbit, N-Worker, NEXUS and SYNTHΞSIS development tasks were paused; the game task remained enabled with an updated permanent prompt and the existing branch/verification safeguards. This replaces the previous temporary 48-hour arrangement that would otherwise have resumed the four original projects on 22 November. The repositories and earlier work remain available as reference. A future resumption needs a new explicit decision. Task-state claims must be verified from the automation service, not inferred from this document.

### Why a game can be a useful laboratory without becoming the entire platform

A living-world game makes abstract questions observable: whether NPCs continue acting without a model response; whether asynchronous decisions become stale; whether memory persists; whether event-driven ticks save work; and whether the player sees meaningful consequences. Reusable components can later be extracted if tested independently of the game engine.

This **does not** imply that solving game simulation automatically completes an MCP server, a Windows UI, a coding worker or a synthesizer. Each retains domain-specific requirements. A sound engine's hard real-time DSP requirements differ from a remote LLM's probabilistic inference latency; similarity in clocks and state management is not algorithmic equivalence.

## Research conclusions, with evidence boundaries

### 1. Nested TICKRATE is more than a clock metaphor

The proposed system separates (a) authoritative world state, (b) per-layer scheduling, (c) typed event/delta transfer, (d) selective fold/unfold of off-screen state, and (e) bounded asynchronous LLM proposals. A regular clock can coexist with variable per-entity work and event-triggered updates. The original four-block visual diagram is suggestive, but without a legend it does not prove the intended meaning of each colored cell or link.

**Known engineering building blocks:** multi-rate simulation, event queues, state snapshots, delta updates and asynchronous work are established patterns. **Not yet established:** a performance improvement from their particular combination in this project, formal guarantees for folding/unfolding, or a running LLM-governed city.

### 2. The key LLM benefit may be fewer necessary decisions, not faster inference

An NPC can follow deterministic goals, resource rules and memory between occasional model proposals. This could reduce model calls and prevent slow inference from blocking the frame loop. For remote APIs, latency, jitter, quotas and stale replies remain real; a bounded scheduler can isolate or reject late results but cannot make network inference instantaneous. Compare calls per simulated hour, token cost, p50/p95 latency, queue age, memory, correctness and user-visible outcomes against baselines before claiming a gain.

### 3. Human participation expands experiments but does not automatically validate them

A proposed external use case is a geopolitical/social simulation with some real human participants alongside synthetic agents. The architecture could support distinct time horizons, stateful institutions and replayable policy scenarios. However, participant behavior is not automatically representative of a population, and plausible agent narratives are not empirical forecasts. Any serious decision-support application requires calibrated domain models, uncertainty analysis, representative data, independent validation and careful governance. This is a possible collaboration path, not a verified partnership, funded project or working policy predictor.

### 4. Independent implementations can test generality

Sharing a documented architecture with another developer could produce a different implementation, exposing assumptions the game testbed does not challenge. Cross-project reuse of code, datasets or artifacts would still require permissions and licensing. An idea may be freely discussed without guaranteeing rights to independently developed source code.

### 5. Cross-domain leaps are a research input, not a test result

The initiator explicitly values unexpected connections: e.g. musical frame reconstruction -> state reconstruction; FM/AM modulation -> changing work per tick; game NPC memory -> social simulation. This can generate useful hypotheses. The safeguard is to label each connection as analogy, plausible mechanism, source implementation or experimentally validated result. A productive research process preserves speculative breadth **and** falsifiable measurement.

## Practical operating contract

1. The user can start any topic in the single conversation. The assistant answers without requiring a different project chat or asking the user to reconstruct its history.
2. When specific past project facts are needed, retrieve the relevant durable records from GitHub and distinguish current from historical versions.
3. New ideas receive a research identity and links to all affected domains; no automatic product backlog entry.
4. Significant experiments specify a baseline, measurable hypothesis, constraints, and evidence. A failed experiment is retained.
5. Code modifications require current policy/branch checks, bounded scope, review and honest test reporting. A conversation idea is not write authorization.
6. Public documentation is anonymized, sourced and labeled; private operational records stay private.
7. Automated tasks do not automatically read the entire live conversation. A binding change is synchronized only when successfully written to the coordination repository.

## Immediate checkpoints

- Verify that the four non-game automations remain paused and the game automation follows the new prompt.
- Verify the central policy and decision log can be retrieved from a fresh chat context.
- Use one cross-domain research note (e.g. nested TICKRATE and state folding) as a test of idea-to-project routing.
- Run a small deterministic-versus-adaptive simulation comparison before claiming scalability or latency improvements.
- Continue actual game regression and demo validation; do not conflate documentation changes with runtime verification.

**Public editorial caveat:** This document describes the approved process and reported/observed configuration, not a tested end-to-end automatic chat-to-Git sync pipeline. The workflow change does not claim to have solved LLM simulation, produced a completed demo or secured external funding.
