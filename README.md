# GitHub as an AI Development Backbone
### How a non-programmer began coordinating AI-assisted software projects across conversations, models and repositories

**Public case study · November 2026 · Anonymized edition**

**Authorship disclosure:** This article was **written and edited by ChatGPT (OpenAI)**, based on the project initiator's ideas, instructions, experiments and conversations with the assistant. The human initiated and directed the work, determined what mattered and requested revisions; ChatGPT organized and authored this narrative. It is an AI-authored, human-directed account—not an independently audited research paper.

> **Core idea:** GitHub can serve not just as code storage, but as a durable, inspectable coordination layer between separate AI conversations, scheduled tasks, local models and development workstreams.

## 1. The starting point: no conventional technical background

The person initiating this experiment reports **no prior professional or formal background in programming, AI systems, Git, or software development**. This matters because the system did not start from a fully specified engineering architecture.

The process grew through questions, practical experiments, tools that failed to work as hoped, and attempts to remove obstacles. The human role was to define goals, challenge limitations, select tradeoffs and direct different AI systems. AI-generated code still required verification; a convincing answer was not the same as working software.

The central question became: **Can a non-developer coordinate increasingly complex AI-assisted projects by storing decisions and verifiable progress outside any one conversation?**


## 2. Dated timeline: from the first development-manager experiments to a coordinated system

**Time window covered:** **15–18 November 2026**, with earlier exploratory work preceding this window. **15 November is the earliest date established by the project conversation records reviewed here, not a verified date when the person first began using AI or developing software.** The first public article was assembled on 18 November. Dates refer to documented decisions or reports, not necessarily to the first code commit. This is a rapid sequence of experiments, **not proof of production maturity**.

| Date | Turning point | Why it changed the direction | Evidence level |
| --- | --- | --- | --- |
| **15 Nov 2026** | AI Development Manager / multi-model alternative to a single coding agent discussed | Codex as coordinator, Nemotron as worker, smaller local model for indexing/triage; motivates a deterministic orchestrator | Dated planning record; not proof of completed implementation |
| **16 Nov 2026** | Local Windows tooling and practical transfer experiments | Python/WebView, BAT/PowerShell, LM Studio, source archives and Git-oriented workflows expose deployment and file-access constraints | Conversation/workflow record; individual execution results vary |
| **16–17 Nov 2026** | Orbit becomes the named Bionic MCP layer | Separates tool execution, local-model access and memory from a future independent desktop application | Versioned Orbit repository and README |
| **17 Nov 2026** | **NEXUS** named as separate Windows platform | Long-term replacement goal for specialized agent shells, without conflating Orbit with the UI | Dated architecture decision |
| **17 Nov 2026** | **N-Worker** separated as the Nemotron-oriented worker | Clarifies coordinator vs execution worker vs UI responsibilities | Repository exists; full worker loop not independently verified |
| **17 Nov 2026** | **NID — NEXUS Instruction Dictionary** conceived and iterated | Moves repeated instructions and code patterns into modular, compact, potentially deterministic representations | Dated discussion and reported development iterations; see NID chapter |
| **17 Nov 2026** | **Night Runner** local Windows results reported as **9/9** | Shows the value of bounded tests, progress detection and actual local-model probes | Reported local result; separate Windows CI regression failed |
| **17 Nov 2026** | **CONDUCTOR** coordination layer established | Four projects receive distinct repositories, ownership, review gates and staggered scheduled tasks | Dated coordination document |
| **17 Nov 2026** | Human Godot RPG playtest reveals working mechanics and visual defects | Real gameplay becomes an acceptance test, not merely code generation | Dated tester observations |
| **17–18 Nov 2026** | Game migration to the new canonical repository; visual GPT playtesting explored | Shows why assets, screenshots, controls, input events and repository state must be checked together | Migration incomplete/unverified; visual agent test not independently reproduced |
| **18 Nov 2026** | Shared-memory, PowerShell/Git sync and shared-clipboard ideas consolidated | Reframes AI cooperation as durable, auditable records and safe OS integration | Mix of operator-reported workflow and explicitly proposed features |
| **18 Nov 2026** | Public evidence-audited case study published and expanded | Turns private experiments into a falsifiable account inviting external criticism | Public article and Git history |

### How to interpret the speed

Between the first dated development-manager record on **15 November** and the coordinated, publicly documented state on **18 November** are **three elapsed calendar days**. In that short window, the work moved through architecture changes, repositories, prototypes, test reports, and human gameplay observations. This measures the *pace of iteration and documentation*, **not** the time required to produce fully validated products. A fast sequence of AI-generated artifacts can still leave substantial integration and verification work.

**Inflection points:** (1) moving from model-only answers to bounded tools; (2) moving from file handoffs to Git history; (3) separating Orbit, N-Worker and NEXUS; (4) replacing repeated manual checks with Night Runner and Progress Guardian; (5) using Godot gameplay as a visual reality check; (6) considering NID to shift repeated tasks from probabilistic model output into compact, testable operations.


## 3. The catalyst: Codex usage and token limits

A major motivation was encountering **usage and token limits in Codex** during ongoing development. When access to a preferred coding agent was constrained, work risked stopping even though plans, repositories and other models remained available.

The answer was not simply to find another model. The aim became **making the development process survive the unavailability of any single model**. That meant keeping instructions, project context, accepted decisions, task status and results somewhere other than the agent's chat history.

Codex limits were one trigger among others: lengthy conversations, fragmented project contexts, limited local inference speed, a desktop that was not always online, and uncertainty about whether agents had actually tested their changes.

This workflow does not eliminate quotas or guarantee seamless failover. It reduces dependence on one tool by making handoffs more explicit.


## 4. The learning path: Markdown, ZIP, Base64 and extraction instructions

Before adopting GitHub as the main shared state, several forms of moving work between tools and sessions were explored.

### Markdown as a portable project memory

Conversation summaries became `.md` files describing goals, decisions, system design, known bugs, and what the next agent should do. This helped restart work without repeating an entire discussion. The limitation was that summaries could become incomplete or outdated.

### ZIP as a project snapshot

Archives allowed source code, directory hierarchies and assets to move together. Written extraction instructions became an important part of the handoff: where files belonged, what should be backed up, which tools were required and how to test the result.

### Base64 as a text-only transport experiment

Another question arose: could binary files be represented as plain text, transported through a text interface, then reconstructed locally? In principle, yes:

```text
Original binary bytes
  -> Base64 encoding
  -> text transport
  -> Base64 decoding
  -> reconstructed bytes
  -> SHA-256 comparison and validation
```

This was a useful conceptual discovery about the difference between an artifact and its textual representation. But Base64 is **not compression or a build system**; it usually enlarges data by about one-third and becomes fragile over long chat messages. A ZIP renamed to `.apk` is not automatically a valid Android application.

### From transfer to continuity

These experiments revealed an important distinction:

- Markdown moves **context and intent**.
- ZIP moves **bundled files**.
- Base64 can move **encoded bytes through text channels**.
- Git retains **version history and change provenance**.
- GitHub adds **shared repositories, issues, pull requests and automated checks**.

The objective shifted from repeatedly transporting project snapshots to maintaining a durable reference point that any appropriately authorized agent could inspect.


## 5. GitHub as the coordination backbone

```text
                  Human project initiator
                            |
                    ChatGPT conversations
                            |
                    Coordination role
                    ("the conductor")
                            |
                     GitHub repository
                decisions / tasks / history
                            |
          +-----------------+------------------+
          |                 |                  |
     Project repos     Scheduled tasks       CI and PRs
          |                 |                  |
     AI workers        Read / assess         Test / review
          |
     Optional local model bridges and runtime
```

Separate project conversations are useful because they keep each domain focused. A central conductor conversation can compare progress and dependencies, but it cannot magically communicate with all other conversations.

**GitHub acts as a shared record, not as a shared mind.** Each agent or task must explicitly read current files and, if allowed, write verified results back. Repository text does not itself grant access to a machine, terminal, model or private chat.

The real experiment involved separate workstreams for game development, a desktop AI application, a local tool-integration component and an AI coding worker. Actual private project names, repository URLs and implementation details are omitted here.


## 6. The scheduled-task experiment

The initiator created recurring ChatGPT tasks, staggered across workstreams, to repeatedly inspect state and attempt bounded development steps. The intended cycle was:

1. **Observe:** read repository documentation, open issues, PRs and CI status.
2. **Assess:** distinguish what was proposed, implemented and truly verified.
3. **Choose:** select one scoped next action in the correct repository.
4. **Execute:** make permitted changes through available tools.
5. **Validate:** run checks where possible; report what was not tested.
6. **Document:** save evidence, blockers and next steps for the next session.

A key lesson: editing a GitHub instruction file does **not** automatically change a scheduled ChatGPT task. Similarly, a task's last-run timestamp is not proof of successful code execution. Automated instructions, repository state and actual tool permissions remain separate.


## 7. Combining local and external AI models

Rather than expecting every model to perform every job, the evolving approach assigned tentative roles:

| Component | Intended role |
| --- | --- |
| ChatGPT | Reasoning, planning, coordination, writing and review |
| Codex | Coding assistance when usage is available |
| Local models (e.g. Qwen via LM Studio) | Smaller local tasks when the PC and bridge are running |
| Nemotron and other model providers | Additional coding and analysis capacity where connected |
| Agent/tool bridges | Controlled access to local tools and bounded operations |
| GitHub Actions | Repository-side checks and reproducible tests |

These are **design goals and experimental integrations**, not a claim that all paths are operational end to end. GitHub cannot directly access an offline local PC; local work depends on an actually running, permissioned bridge or runner.


## 8. AI using another AI: delegation to Nemotron and other models

One of the most important experiments was not merely **using multiple models**, but exploring whether **one AI assistant could request work from another model**. Instead of the human manually copying every question between chat windows, the desired arrangement was for a coordinating assistant to formulate a bounded task, invoke a connected model such as **NVIDIA Nemotron** through an API or worker bridge, receive its result, review it, and incorporate the verified outcome into the shared GitHub state.

The intended interaction is:

```text
Human goal
    |
ChatGPT / coordinating AI
    |  prepares task, constraints and context
    v
Worker / API bridge
    |  calls Nemotron or another available model
    v
Model response (proposal, code or analysis)
    |
Coordinator reviews / checks / requests revision
    |
GitHub commit, PR, test evidence or documented blocker
```

This is a meaningful distinction: **Nemotron is not just another chatbot tab**. When connected through a worker or tool interface, it can become a delegated resource within a larger workflow. A model may be used to draft code, critique an implementation, explain an error or perform a second-pass review; the coordinating agent remains responsible for verifying the result and respecting permissions.

The motivation was practical: limited Codex usage made it valuable to explore alternative model capacity, while local models introduced different speed and hardware constraints. Delegation offered a way to allocate tasks by capability and availability rather than require one model to handle every step.

There are important boundaries:

- A model-to-model request needs an **actual integration** (API, MCP tool, worker or local endpoint). Merely mentioning Nemotron in an instruction file does not invoke it.
- A response from a second model is **not automatically an independently verified result**. Code needs tests, and analyses may need evidence.
- Cloud-hosted Nemotron and locally hosted models have different availability, privacy, cost and runtime implications.
- Multi-model coordination can increase latency and complexity. It should be measured rather than assumed superior.

This part of the work remains an evolving experiment. The article does not assert that every proposed delegation path, autonomous write or model handoff was fully operational and tested.


## 9. Extended experiment log: successes, failures, lessons and next tests

This expanded account was assembled from the project's working notes, repository documentation and issue/PR descriptions on **18 November 2026**. It deliberately distinguishes **human playtest observations**, **reported local checks**, **repository artifacts**, and **independently reproduced tests**. Internal repositories remain private, so this public report avoids linking to their confidential contents.

### A. Night Runner: the experiment that deserves its own chapter

**Problem.** A chat-based assistant can propose a fix, but how does the system keep checking work when the human is away, without allowing an uncontrolled agent to modify the entire machine? A recurring task is not enough: it needs a bounded runner, a model connection, a task journal, safety gates and evidence.

**Experiment.** Orbit's *Night Runner* work explored repeatable local checks, including `local_model_review` and `sandbox_write_probe`, with a local Qwen model served through LM Studio. The broader system used a *Progress Guardian* to flag stagnation and blockers and a reporter to preserve run outcomes. Tests also exercised Git branch/reporting integration.

**Positive result reported from the Windows environment.** A coordination note dated 17 November records **9/9 Night Runner checks passing**, including a local-model review taking approximately **9.7 seconds** and a sandbox write probe taking approximately **7.3 seconds**. The same report recorded `progress_blocked=false` and `stagnant_cycles=0`. These are valuable *reported local test results*, not a benchmark of long-term autonomous reliability; they were **not rerun independently for this article**.

**Failure that mattered.** A separate GitHub Actions run passed its Ubuntu job but **failed its Windows Night Runner Git-branch integration regression**. The expected reporter state was `publication=pushed`, while the observed state was `failed_local_report_preserved`. The documented root cause was not established at that point. This is a concrete example of why a passing local probe and a passing CI pipeline are different evidence.

**Environment mismatch.** GitHub-hosted CI cannot directly access a model server bound to the developer's local Windows machine. A remote CI job cannot establish that the local Qwen API or a real sandbox write succeeded unless the relevant machine and test evidence are explicitly connected.

**Safety lesson.** The runner must distinguish a dry-run proposal, syntax validation, a write permitted inside a sandbox, and actual functional correctness. The controlled autonomous write experiment was separately marked **not verified** at the last documented checkpoint; a successful probe does not authorize claiming unrestricted write autonomy.

**Conclusion.** Night Runner demonstrated a promising *test-and-report architecture* with encouraging local results, while exposing brittle reporting integration, machine-specific dependencies and the need for reproducible proof. The next credible test is a fully logged sequence: exact model response → bounded proposed edit → approved sandbox write → hash and syntax checks → functional test → Git publication → independently reviewed report.

### B. Orbit: from an MCP connector to a bounded agent runtime

**Purpose.** Orbit is an MCP integration layer for an AI client and external/local tools. It is **not** the standalone Windows application and should not be confused with NEXUS.

**Problem encountered.** A model could answer questions, but turning its answers into reliable actions required tool discovery, permissions, persistent state, provider routing, workspace restrictions and error handling. Model hallucinations and stale instructions were especially risky when file writes became possible.

**Implementation evidence.** The versioned Orbit README documents a **v2.4.1 beta** implementation with **34 MCP tools**, including six autonomous-runtime tools added to an earlier 28-tool base. Its bounded loop covers one JS/MJS/CJS/JSON file, model proposals, retry feedback, syntax checks, backups, hash-gated restoration, self-evaluation and restart-aware statuses. **Read-only dry-run is the default.** This is a real, described software artifact, but the README explicitly excludes arbitrary commands, full-repository changes, Godot validation and guaranteed semantic correctness.

**Additional experiments.** Later ZETA notes report discovery of **43 tools and 61 knowledge documents** in a separate Bionic MCP instance. That is a reported environment snapshot, not proof that all 43 tools were exercised or that a beta upgrade was deployed to the running installation.

**Failures and boundaries.** A GitHub CI Windows regression remained unresolved; autonomous write proof was incomplete; the local runner and cloud runner had different capabilities; and a model could return syntactically valid but incorrect code. The safety boundary was a logical path guard, **not** a hardened virtual machine.

**What was learned.** Start with small, reversible, permissioned tasks. Preserve a working baseline while testing a new version separately. Use explicit model IDs and real inference requests, not just a health-check response. Store checksums, backups and error categories. Tool availability, tool correctness and safe execution are three separate claims.

**Current assessment.** Orbit is the strongest documented *implemented technical subsystem* in this case study, but the evidence does not justify calling it a general autonomous coding platform.

### C. N-Worker and Nemotron: one AI delegating to another AI

**Purpose.** N-Worker is intended to provide a dedicated coding/execution worker, while Nemotron is one possible model resource. The architecture separates the **coordinator** (what to do, why and how to verify) from the **worker/model** (generate or review a bounded result).

**Original constraint.** Codex quotas and limited local compute made it impractical to depend on one agent for every task. The project explored whether a coordinating AI could call Nemotron or another available model through an actual API/worker bridge and then review its output.

**Successful learning.** The distinction between *multi-model access* and *AI-to-AI delegation* became explicit. A useful worker task needs context, allowed files, expected output, time limits, model/provider selection, error reporting and acceptance tests. GitHub can preserve the result so the next coordinator does not have to trust a chat summary.

**What repository evidence shows.** A dedicated N-Worker repository exists. At the checkpoint inspected for this article, its default-branch README was minimal, so it did **not** substantiate a production-ready task queue, full autonomous execution or a measured success rate. Earlier discussions and integration plans should therefore be treated as experiment history rather than independently verified worker capabilities.

**Failure modes.** Model responses may be plausible but wrong; provider access may fail; a local model may be too slow while a game is consuming GPU resources; worker output may lack tests; and an AI asking another AI is not the same as the second AI having permission to write files.

**Conclusion.** N-Worker is an important *architectural experiment* but requires a public reproducible demonstration of delegation, review, test and commit before claiming that its complete workflow is proven.

### D. NEXUS: the attempt to turn scattered integrations into one application

**Purpose.** NEXUS is the proposed standalone Windows AI development environment, designed to unify model routing, workspace tools, persistent task state, code changes and a practical user interface.

**Problem.** A growing collection of MCP tools, chats, terminal scripts and separate windows can become difficult to operate, especially for a non-programmer. The desired experience includes a file explorer, chat, previews, controlled computer interaction, code review and eventually contextual prompting.

**Design experiments and corrections.** An early Godot-based UI direction was explored. The later recorded architectural decision **rejected Godot as the Windows application shell** and prioritized an independent agent core with a conventional desktop UI framework under evaluation. Godot remains a *target application* for game development. This reversal is an important result: the team changed course rather than defending an unsuitable early choice.

**Other ideas under investigation.** Modular provider/tool interfaces; reuse of Orbit as an optional adapter; bounded autonomous tasks; persistent checkpoints; approval-gated file changes; and experimental self-improvement through measured comparisons and rollback. The goal is to avoid duplicating features that already work elsewhere.

**What works today?** The repository contains planning and early prototype artifacts, but its README explicitly labels NEXUS **early prototype / architecture in progress** and says it is not yet a drop-in replacement. There is no verified stable standalone Windows application in the evidence reviewed for this publication.

**Lesson.** Modular boundaries and staged migration matter more than a large list of promised features. A new interface should not be described as replacing Orbit until each critical capability has a test and a demonstrated equivalent.

### E. The Godot RPG: using a real game as an integration test

**Purpose.** The cyberpunk RPG/immersive-sim game became a demanding test of AI-assisted development because it involves **source code, scenes, imported assets, controls, physics, animation, UI, rendering and human perception**. It is a stronger test than generating a simple standalone script.

**Reported positive playtest results.** A development issue dated 17 November records the human tester's observations: top-down movement and camera worked; occlusion was present; movement and parkour operated; gun/katana combat worked in a basic form; targeting feedback and target lock existed; and Q/E skill chains functioned. These are **human playtest observations**, not claims independently reproduced by this article's author.

**Problems actually observed.** Animation blending was abrupt; some climbing animations faced the wrong direction; hit/death reactions were missing; hacking was difficult to discover; contextual RMB behavior needed a clear distinction between quiet and combat modes; and the UI needed a more coherent diegetic design. These are not abstract roadmap ideas—they are concrete problems emerging from play.

**Migration failure and recovery lesson.** Moving the game from a historical repository to its new canonical repository revealed missing or unverified assets, plugins, scene references and imported resources. An earlier migration attempt was recorded as incomplete. A repository containing scripts is **not equivalent to a complete, runnable Godot project**. File manifests, asset hashes, scene dependencies and Godot import/runtime checks are necessary before declaring a successful migration.

**Experiment: GPT running and playing a game through GitHub.** The development conversation reports progress toward letting GPT participate in running the game, inspect captured frames and provide input through a Git-mediated workflow. This is a potentially significant milestone because it closes part of the gap between *writing game code* and *observing what the game actually does*. However, the source material inspected for this public edition did **not** provide a complete reproducible sequence of runner version, executable/game commit, screenshots, input events and resulting state. We therefore report it as a **promising, user-reported experimental result**, not independently verified autonomous visual playtesting.

**Practical lessons from the visual loop.** A screenshot can be misleading when a pole or another object blocks the character; camera framing and zoom matter; low frame rates can make input timing unreliable; and lowering render resolution may help the test runner. Visual testing should deliberately move the character, inspect weapon/katana and sheath orientation, and compare expected animation with actual frames. Capturing screenshots during slow frames is a useful proposed tactic, but must be logged to count as a measured improvement.

**Godot-specific engineering lesson.** AI-generated scripts can recreate functionality that the engine already supplies through nodes and built-in systems. Future audits should ask whether custom GDScript is necessary or whether a native node, animation tree, input map, resource or scene mechanism would be simpler and safer.

**Conclusion.** The game provides compelling evidence of *AI-assisted iterative game development and human playtesting*. It does not yet prove fully autonomous, reliable GPT gameplay or complete migration of the current build.

### F. The self-updating local LLM idea: what 'learning' actually means

An earlier idea was to build a local AI assistant that could become more useful over time by inspecting its failures and changing its supporting system. Several mechanisms must be distinguished:

| Mechanism | What changes? | What it proves |
| --- | --- | --- |
| Persistent notes / retrieval | External memory, documents and context | The assistant can retrieve prior information |
| Prompt and tool revisions | Instructions, routing or executable wrapper | The surrounding software can be improved |
| Automated code proposal and review | Source code, subject to tests and approval | A model can suggest changes to its own application |
| Fine-tuning or retraining | Model parameters / weights | Requires a separate, measured training process |

No evidence inspected for this article establishes that a local LLM successfully **retrained its own weights**. A safer near-term experiment is *self-improvement of the surrounding software*: propose a bounded change, run reproducible evaluations, compare against baseline, require approval, then roll back on regression.

### G. Local LLM memory and Git-to-PowerShell file synchronization

The project initiator clarified an additional implementation detail: the local LLM setup uses **ordinary memory rather than a shared-memory arrangement**, and its local files are **updated from Git through PowerShell**. This is an operator-reported description of the actual workflow, not a claim independently measured or inspected in this publication.

The distinction matters because two mechanisms can be confused:

1. **Model runtime memory:** where the model and its inference state reside while running. The operator describes the setup as using regular memory, not shared memory. This article does not infer specific VRAM/RAM allocations or hardware-level memory architecture without runtime measurements.
2. **Git-managed local files:** a PowerShell-driven workflow can retrieve repository changes and update the local files used by the assistant. These may include instructions, scripts, configuration or external knowledge, depending on what is actually tracked. Updating these files **does not, by itself, retrain or change the neural network's weights**.

A conceptual view of the reported workflow:

```text
GitHub repository / versioned state
                |
       Git operations via PowerShell
                |
        Local files on Windows
                |
       Local LLM application / tools
```

**What this establishes:** a concrete proposed/reported path for keeping the local assistant's supporting files aligned with Git. **What remains to verify:** the exact PowerShell commands, whether synchronization is automatic or manually triggered, conflict/rollback behavior, which files are updated, and evidence that the running model or tool stack reloads the new state correctly. Git should be treated as a versioned update mechanism, not as proof of online learning.

### I. Cross-project lessons and a more rigorous proof plan

**What the experiments already support:**
- GitHub can preserve project decisions and handoffs across separate AI conversations.
- Real repositories and code artifacts can be produced and revised.
- Local model/tool integration can support bounded, reported tests.
- A playable game can expose defects that source inspection alone misses.
- Failed CI runs and incomplete migrations produce valuable engineering evidence.

**What they do not yet establish:**
- That every scheduled task completes meaningful development work.
- That Orbit and N-Worker together deliver a dependable autonomous coding pipeline.
- That NEXUS is a working replacement for the existing tool stack.
- That a local model is continuously and safely self-retraining.
- That GPT's game-playing loop works reproducibly across many runs.
- That any system has a statistically measured reliability percentage.

**Suggested end-to-end benchmark.** Define ten small tasks of increasing difficulty: documentation update, isolated code repair, unit test fix, sandbox file write, provider failover, Godot headless import, game launch, screenshot capture, input-and-response playtest, and rollback after a deliberately failing change. For each task, record *attempt count, success criteria, observed pass/fail, elapsed time, environment, exact commit, model and logs*. Only then publish operational success rates such as `successful verified runs / total comparable runs`.

**Bottom line.** The most valuable result so far is not a claim that AI has replaced engineering. It is a documented progression from ad-hoc chats and file transfers to a multi-project, evidence-conscious development workflow—with a promising Night Runner, an increasingly capable Orbit, experimental delegation through N-Worker, an early NEXUS architecture, and a Godot RPG that forces AI-generated code to confront real runtime behavior.


### H. Orbit's proposed shared memory between Nemotron and the local LLM

A further architectural idea in Orbit is **shared agent memory**: letting Nemotron and a locally hosted LLM consult and contribute to a common, versioned body of task knowledge instead of operating as isolated assistants.

**Important terminology:** This is *shared informational memory*—records, summaries, tool outcomes, decisions and references—not shared physical RAM/VRAM, a unified neural-network context window or automatic transfer of model weights. It is compatible with the operator's separate report that the local model runs using ordinary memory and that PowerShell synchronizes local files with Git.

#### The problem this is meant to solve

If a local model discovers an error, Nemotron should not need to rediscover it. If Nemotron proposes a fix, the local model should be able to see the rationale, constraints and test outcome before continuing. A coordinating assistant should also be able to reconstruct *who did what, on which version, with what evidence* after a conversation or process restarts.

Without shared records, repeated model calls can waste context, contradict earlier decisions, duplicate work or mistake a proposal for an accepted fix.

#### Proposed information flow

```text
          ChatGPT / coordinator
                  |
          Task + evidence policy
                  |
         Orbit memory interface
           /               \
     Local LLM            Nemotron
           \               /
        Structured shared records
        (tasks, decisions, outcomes)
                  |
       Git / local files / review
                  |
          Next agent or session
```

The proposed shared memory could store:
- **Task records:** goal, constraints, source revision, owner and status.
- **Decisions:** accepted choices, alternatives and reasons.
- **Evidence:** model outputs, test results, error categories, commit IDs and timestamps.
- **Reusable knowledge:** short verified summaries and pointers to source files, rather than unbounded raw conversations.
- **Provenance and confidence:** which model produced a claim, whether it was checked, and whether it is current.

A possible record format, shown as a **design example rather than an existing enforced schema**, is:

```yaml
task_id: example-042
source_revision: "<commit SHA>"
author_model: "local-model"
observation: "A syntax check failed"
evidence: "test log reference"
reviewed_by: "Nemotron"
decision: "needs_revision"
verification: "not_verified"
```

#### How the memory could work safely

A practical implementation would separate **short-lived working context** from **durable records**. Orbit could expose explicit memory read/write tools, while Git and local files preserve approved history. A local model might write a proposed observation; Nemotron could review it; the coordinator would promote it to trusted knowledge only after checks.

This also suggests safeguards: separate model-generated claims from verified facts; avoid treating untrusted repository text as instructions; attach source revisions; limit record size; prevent uncontrolled feedback loops; handle simultaneous writes and conflicts; redact secrets; and allow rollback when a bad memory entry affects future work.

#### Current evidence and limits

Orbit's versioned README documents memory-related tools and an autonomous task loop, including a `memory_get` reference to stored candidate artifacts. It also describes retaining a memory directory across upgrades. **Those facts do not independently prove that Nemotron and the local LLM currently share a fully synchronized, bidirectional memory store.** The shared-memory architecture above is therefore presented as a proposed/partially explored capability, not as a verified completed feature.

A meaningful test would ask the local model to store a bounded, non-sensitive observation; retrieve the same record through Nemotron's actual connected interface; have Nemotron add a review without overwriting the original; then retrieve both versions from a fresh session. The test should record IDs, hashes, access permissions, conflict behavior and whether the resulting information was used correctly.

**What we learned:** The most useful meaning of “models sharing memory” is not that they share a brain. It is that they share **auditable knowledge and state**, with clear provenance and verification, so work can continue across models without silently turning guesses into facts.


## 10. NID and related ideas: reducing the amount of intelligence needed for routine work

### NID — NEXUS Instruction Dictionary

**NID** stands for **NEXUS Instruction Dictionary**. The user's core idea was to create a **modular dictionary of predefined instructions and code patterns** that can be represented compactly, rather than asking an LLM to regenerate verbose code or instructions for every routine operation.

In a conceptual example, a short instruction such as `UI.PANEL(type=terminal,theme=dark)` could refer to a known, versioned implementation. **This is an illustrative syntax, not a claim that this exact command exists in the codebase.** The real challenge is ensuring that a compact instruction expands or executes with the same intended semantics.

**Why it matters for local models:** Smaller models are constrained by speed, context length and hardware. If a deterministic runtime can perform a known task, the model need not spend tokens rediscovering the procedure. The model can focus on exceptions, planning, novel code and review. This is **task compression**, not a method for magically compressing arbitrary software without loss or increasing a model's innate reasoning ability.

**Design direction from the 17 November experiments:**
- A small **NID runtime** interprets validated dictionary instructions deterministically.
- **Modular dictionaries** can be loaded only when needed and can declare dependencies, versions, supported backends and permissions.
- **Parameterized macros / compact bytecode** reduce repetitive representations while retaining inspectable expansion.
- A **source compiler and typed intermediate representation (IR)** can map a supported subset of source into a constrained format.
- **NID Memory** could encode repeated verified state and decisions compactly for later retrieval.
- **NID Model Routing** could choose among deterministic rules, a small local model and a larger model such as Qwen or Nemotron.

**Reported progress and limits.** A dated 17 November discussion described iterations **v0.1–v0.8**, moving from bytecode/macros to modular dictionaries, authorized execution, a Python-subset compiler and typed IR, and reported **50/50 GitHub tests passing**. This is a **conversation-reported test count**, not a result independently rerun for this article. It does **not** demonstrate arbitrary repository compression, lossless compression of any programming language, or production readiness. A stronger proof would publish the exact test suite, versioned dictionary, round-trip semantics checks and performance comparisons.

### The 'sleeping' local model and hybrid execution idea

A related question was whether only a small portion of a larger Qwen model could remain active while the rest sleeps, dynamically sharing RAM and VRAM. A model's weights cannot generally be treated as interchangeable independent submodels by simply loading a small slice. But **a useful system-level approximation** is possible: keep a tiny deterministic NID/task scheduler active; use a small model for easy classification or summaries; wake the full local LLM only when a task requires it; and route specialized review to another model. This may reduce GPU contention and model calls, although actual latency, VRAM use and energy savings need benchmarks.

### Shared clipboard as a cross-application bridge

A **shared clipboard** was proposed on **18 November** after one-file-at-a-time game migration proved cumbersome. Orbit could eventually offer permissioned text read/write/clear operations across approved Windows applications, with previews, provenance and size/type limits. This is **proposal only**, not an implemented or tested feature. Clipboard integration is not a substitute for Git's verified bulk file transfer, and it must not silently collect passwords or private clipboard history.

### Context-aware UI and visual development

The broader NEXUS vision includes **right-click-to-prompt** on interface elements, local file inspection, previews, and controlled input automation. A separate creative idea explored using an **editable 3D scene as structured guidance for generating 2D assets**: individual objects/layers carry their own prompts and spatial relationships, followed by a combined render. These ideas suggest a common design principle: *use structured, inspectable context rather than one giant ambiguous text prompt*. They remain proposals until implemented and tested.

### Self-improvement with evidence, not uncontrolled self-modification

NID also suggests a disciplined learning loop: detect a repeated successful action → propose a reusable dictionary instruction → test it against the original operation → version it → approve promotion → monitor regressions → roll back if needed. This can improve the **software around a model** without asserting that the model has trained itself. The dictionary must never be allowed to bypass execution permissions just because an instruction has a short name.


## 11. Decisions, evidence and handoffs

An instruction such as “keep improving the project” is too vague to verify. A more useful handoff includes a target, approved paths, a baseline commit, constraints and tests:

```yaml
project: example/project
objective: "One concrete, testable result"
source_of_truth:
  - README.md
  - docs/DECISIONS.md
baseline_commit: "<verified commit SHA>"
allowed_paths:
  - "src/approved-area/**"
constraints:
  - "Preserve existing working features"
  - "Do not expose credentials"
acceptance:
  - "Run named tests"
  - "Report actual errors and evidence"
status: "proposed | running | blocked | verified"
```

This is an illustrative documentation convention, not an established automatic task-execution standard.

The experiment adopted three evidence levels: **proposed**, **implemented**, and **verified**. A chat claim or planned feature is not a commit. A commit is not proof that the software works. A passing CI job validates only the checks actually run.


## 12. What went wrong—and what it taught us

**Conversation fragmentation:** Separate chats do not automatically share a synchronized state. A repository helps only when participants actively read the latest information.

**Changes to project boundaries:** Renaming or migrating a project requires more than editing a document. Assets, history, references and scheduled task targets must be verified independently.

**Local versus cloud execution:** A successful test in a remote CI environment does not prove a local desktop workflow works. Similarly, a local sandbox test does not prove unrestricted agent control.

**Oversized transfers:** ZIP and Base64 can be useful, but neither guarantees integrity or correct project structure. Checksums, inspection, backups and real execution matter.

**False confidence:** The process must record failures and uncertainty rather than treating every AI-generated status report as a successful outcome.


## 13. Why the approach is interesting

This is not a claim that a non-programmer has replaced a professional software engineering team. The practical observation is narrower: AI tools may allow someone without conventional development training to initiate and coordinate ambitious experiments, provided results are tested and responsibilities are explicit.

The deeper design question is **how to preserve the continuity of work when the model, chat, machine or tool executing it changes**.

Git provides history. GitHub provides durable coordination artifacts. AI conversations provide flexible reasoning. Local and cloud agents provide varying execution capabilities. Scheduling provides repeated opportunities to check state. The system works only insofar as those components exchange testable artifacts instead of relying on promises.


## 14. Evidence audit: what has actually been demonstrated?

**Audit date: 18 November 2026.** This section is a snapshot of accessible repository READMEs, selected commit/PR metadata and the internal coordination record, not a full reproduction of every Windows or Godot runtime test. Specific private repository identifiers and paths are deliberately omitted from this public article.

### The projects behind the method

| Workstream | What it is | Evidence observed | What is still unproven |
| --- | --- | --- | --- |
| **Orbit** | An MCP-based bridge between an AI client, local tools and model providers, with bounded autonomous task experiments | A versioned implementation and documented syntax-repair/testing commands exist. The coordination record reports a **9/9 Windows Night Runner check** using a local model; this is *reported local evidence*, not an independently reproduced audit result | Fully validated autonomous file writes in the intended sandbox, unrestricted end-to-end desktop control, and sustained reliability |
| **N-Worker** | An AI coding worker intended to receive delegated tasks and use models such as Nemotron | A dedicated repository and initial worker material exist | A complete independently demonstrated delegation → code → test → reviewed commit cycle, and repeated success-rate measurements |
| **NEXUS** | A planned standalone Windows AI development environment with modular model, tool and workflow interfaces | Repository, architectural decisions and early prototypes exist | A stable standalone executable, verified feature parity with Orbit and production-ready autonomous development |
| **Godot game experiment** | An evolving cyberpunk game used as a demanding AI-assisted development target | Game repository with source development, migration work, commits and UI/gameplay PRs; discussion of GitHub-mediated builds, tests and agent playtesting | Complete asset migration, reproducible game launch, verified visual playtesting loop and stable end-to-end gameplay |
| **CONDUCTOR** | Cross-project coordination through dedicated ChatGPT conversations and durable GitHub instructions | Central coordination document, distinct project boundaries and scheduled-task plan | Fully automatic synchronization of chats, autonomous cross-project handoffs and demonstrated long-term unattended operation |

The experiment also explored an **AI assistant calling another AI**: ChatGPT coordinating a task through a worker/API bridge to Nemotron or another model, then reviewing the output. This is a central design pattern. It should not be confused with a claim that every multi-model route is already tested and continuously available.

### Earlier learning sequence (undated phases; see the dated timeline above)

1. **Early local-model experiments:** Explore whether a locally running LLM can serve as a persistent assistant, call tools and potentially help improve its own software. This is a research direction; **a self-updating model or autonomous retraining loop was not verified**. Updating prompts, memory or application code is not the same as updating model weights.
2. **Portable handoffs:** Use Markdown summaries, ZIP bundles, Base64 encoding and extraction instructions to carry context and files between limited interfaces.
3. **Delegation experiments:** Introduce Nemotron and other models as possible coding/review resources invoked by an AI coordinator, subject to real API and worker integration.
4. **Orbit:** Develop an MCP bridge with local-model connectivity, bounded tasks and safety-oriented sandbox tests.
5. **N-Worker:** Separate the execution-worker responsibility from the coordination and interface layers.
6. **NEXUS:** Plan an independent Windows environment to eventually unify useful capabilities without duplicating every subsystem.
7. **Godot:** Attempt source generation, asset migration, CI validation, launching, screenshot-based inspection and interactive playtesting. **A reported GPT-through-GitHub playtesting experiment is a milestone claim pending a public, reproducible evidence package** showing the game launch, frames/screenshots, actual inputs, errors and outcomes.
8. **CONDUCTOR and scheduled tasks:** Move from isolated chats toward a repository-centered cycle of observation, task selection, validation and handoff.

### Progress and confidence bars — transparent editorial rubric

The bars below measure **documented evidence-gate coverage**, *not* statistical reliability, product completeness, probability of success or a benchmarked quality score. Each of the four gates is worth 25 points: (1) defined scope, (2) repository artifact, (3) recorded test evidence, (4) independently reproduced end-to-end workflow. A gate counts only when evidence inspected for this article supports it. These conservative scores can change after a deeper audit.

| Workstream | Evidence gates observed | Evidence coverage |
| --- | --- | --- |
| CONDUCTOR / GitHub coordination | 2 of 4 | **50%** █████░░░░░ |
| Orbit | 3 of 4 *(test result reported, not reproduced here)* | **75%** ███████▌░░ |
| N-Worker | 2 of 4 | **50%** █████░░░░░ |
| NEXUS | 2 of 4 | **50%** █████░░░░░ |
| Godot development / playtesting | 2 of 4 | **50%** █████░░░░░ |
| Fully autonomous multi-model development loop | 1 of 4 | **25%** ██▌░░░░░░░ |

**Interpretation:** These numbers are an intentionally simple *documentation audit rubric*. For example, 75% for Orbit does **not** mean Orbit works 75% of the time, and 50% for the game does **not** mean the game is half finished. There is not yet enough repeated, comparable runtime evidence to calculate genuine operational reliability percentages. The 9/9 reported checks describe one specific check set, not an overall system success rate.

### What would prove the method more strongly?

A reproducible demonstration would record: a human request; a coordinating AI reading GitHub state; a delegated worker/model receiving an explicit task; a source change on a scoped branch; CI validation; an actual Windows/Godot runtime test; and a final evidence-linked report read by a subsequent session. For Godot playtesting, preserve the game revision, runner environment, captured frames, input events and a failure/success trace. Repeat the same scenario many times before publishing operational reliability rates.

**Current verdict:** The method is **demonstrated as a practical coordination and documentation workflow**. It is **partially demonstrated as a development and testing workflow**. The stronger claim—reliable, unattended, end-to-end multi-model software development including visual game playtesting—**remains unproven by the evidence reviewed for this public snapshot**.



## 15. Publication and privacy

This is a sanitized public narrative, not a copy of the internal development notebook. Private account names, exact repository paths, internal scheduled instructions, credentials, local directories and personal biography have been excluded. The GitHub account hosting this article remains visible to readers as its publisher.

The article is **AI-authored and human-directed**, and some details describe experiments and intentions rather than independently verified successful implementations. Future revisions should preserve those distinctions.

---

*Written and edited by ChatGPT (OpenAI), under the guidance of the anonymous project initiator. First public edition: November 2026.*

