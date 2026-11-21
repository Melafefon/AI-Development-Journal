# From sound modulation to cognitive clocks: a development research update

**Case-study update: 21 November 2026 (UTC)**  
**Author, editor and documentation maintainer:** ChatGPT (OpenAI), at the explicit direction of the anonymous human project initiator.  
**Status:** Source-grounded engineering notes and research proposals; **not** a peer-reviewed study or a claim of fully autonomous software development.

> The central development shift is not just "use an LLM for NPCs" or "generate sound." It is the attempt to design **one set of explicit principles for time, state, modulation, memory and deterministic execution**, while keeping sound processing and game simulation separate implementations with different correctness requirements.

## 1. Evidence and privacy policy

This update was prepared after inspecting accessible GitHub repository README files, the active game development branch's changelog, its audio source and frame-resynthesis documentation, the city-cognition architecture issue, the coordinator's routing policy and decision log, and the existing public article. The initiator's recent discussions supplied additional proposals and priorities. These two evidence classes are explicitly distinguished below.

**Evidence labels**
- **IMPLEMENTED IN SOURCE:** a concrete source artifact exists; this does not establish that it works in the target application.
- **OFFLINE TEST REPORTED:** a specific local/offline result is recorded, but it has not necessarily been independently rerun for this publication.
- **USER-RUN TEST:** a test result supplied from the user's own environment, with its limitations.
- **DESIGN / RESEARCH:** a hypothesis, architecture or intended experiment; no runtime success implied.
- **DEFERRED:** intentionally not part of the immediate playable demo.

The public narrative omits private repository URLs, credentials, account identifiers, exact local paths and unpublished user audio. Private project artifacts are described in sanitized form. All metrics below retain their reference conditions.

## 2. What actually changed in game audio

### 2.1 Procedural synthesis is now a real source-level component

**IMPLEMENTED IN SOURCE.** The Godot game includes a native audio manager with cached PCM-generated sounds, spatial playback and a maximum simultaneous voice policy. Its generator uses integrated-phase sine oscillators, chirps/FM, filtered white noise, envelopes and amplitude shaping. Sound cues are attached to meaningful game transitions such as hacking, mission acceptance/completion and security alerts. An ambient relay drone uses a two-second synthesized loop and spatial playback.

This is not merely a soundtrack concept. The source exposes sound kinds, event hookups, stream caching and 3D audio players. However, the reviewed development changelog explicitly says the relevant Godot parser, native playback, spatial audibility and Windows gameplay tests **had not been run** at the time of those entries. A separate WAV concept preview is not a recording of the running engine.

**Engineering note.** The source's voice cap uses node-child counts, including the persistent ambient drone, rather than a dedicated active-voice counter. This is a plausible future stress-test concern, not an observed audio dropout. Measure overlapping cues and verify cleanup before declaring it a bug.

### 2.2 Spectral-frame voice resynthesis: not TTS yet

**IMPLEMENTED IN SOURCE; OFFLINE TEST REPORTED.** A separate Godot decoder accepts a compact **FRS1** bank derived from two user-provided voice samples. The exporter works at 16 kHz mono using a **512-point STFT**, Hann window and **128-sample hop**. It stores selected quantized complex spectral bins; the Godot decoder uses inverse FFT and weighted overlap-add to produce new 16-bit PCM audio.

| Source class | Duration | Frames | Retained complex bins/frame | Offline reconstruction metric |
| --- | ---: | ---: | ---: | ---: |
| Short telephone speech phrase | 2.646 s | 332 | 96 | 35.61 dB |
| Processed robotic/glitch voice | 21.517 s | 2,691 | 144 | 27.65 dB |

The values are signal-to-reconstruction-error measurements against the **16 kHz mono reference**, not fidelity against the original high-resolution stereo files. They do **not** prove natural speech, intelligibility of newly generated sentences, or correct in-engine playback. The original samples and binary frame banks were kept outside the public article/repository rather than republished.

The technique demonstrates **analysis → sparse frame representation → synthesis**, but the content still comes from recorded speech. A real text-to-speech system would need a mapping from text/phonetic units and prosody to generated acoustic frames. The current prototype does not provide that mapping.

### 2.3 A distinct Godot audio laboratory, not another game subsystem

**USER DECISION / DESIGN.** The initiator wants the next sound-engine experiments **isolated from both the game and SYNTHΞSIS** while the game demo has priority. The proposed laboratory would evaluate synthesis, resynthesis, phoneme experiments, DSP graphs and benchmarks in a standalone Godot project. A laboratory name was suggested in discussion; **no separately established new GitHub repository was found in the accessible repository listing at this checkpoint**. Do not imply that it has already been created.

A subsequent direction was to **study and independently adapt DSP concepts from the open-source Vital synthesizer into Godot**, rather than host Vital as a VST and rather than use Synplant as the dependency. This distinction is essential:

- Studying algorithms, architectures and mathematical DSP principles is different from copying source code.
- Vital's GPLv3 licensing must be assessed before copying, linking or distributing covered code; a private repository is not a license exemption that automatically resolves all future obligations.
- The target is a modular Godot-native sound engine, not an already verified Vital-compatible renderer.

**SYNTHΞSIS remains separate.** Its current default-branch README describes a Python offline audio-rate FM proof of concept, with no verified Vital integration, DAW, GUI or AI agent. Earlier development-branch test results have been reported, but those do not establish a completed Godot DSP engine.

## 3. From acoustic frames to a possible TTS research pipeline

**DESIGN / RESEARCH.** The initiator's next question is whether a reusable speech-unit library can be built from real speech and whether timing, formants and spectral information can be learned or modeled without merely replaying one phrase.

The key conceptual correction from the music-production analogy is that **a voice does not have one inherent BPM**. Speech has time-varying pitch, spectral envelope, phoneme duration, stress, rhythm and prosody. BPM is useful for musical synchronization; **Hz, seconds, sample rate, frame hop and temporal landmarks** are the relevant measurements for acoustic modeling.

A proposed data pipeline:

1. Acquire recordings with **clear usage rights and appropriate consent** for the intended research and any future distribution. Do not assume that publicly watchable videos or captions authorize copying or training on the audio.
2. Store source provenance, language, speaker/recording conditions, permitted use, sample rate and timestamps. Do not upload third-party speech or extracted datasets to a public repository without appropriate rights.
3. Align speech text with actual audio boundaries. Video subtitles and timestamps are **weak alignment hints**, not guaranteed phoneme-level labels.
4. Extract or estimate voiced/unvoiced regions, F0, formant/spectral-envelope trajectories, phoneme/syllable timing, energy and transitions. Preserve coarticulation and consonant bursts; isolated vowels are insufficient for natural TTS.
5. Build small reproducible reference tasks: reconstruct held-out utterances, synthesize controlled phoneme transitions, and test pitch/formant changes without chipmunk artifacts.
6. Compare generated outputs using intelligibility tests, listener judgments, latency and objective signal measures. Do not equate reconstruction SNR with speech quality.
7. Only after evidence of quality and rights compliance, consider an expanded library or specialized model.

The initiator suggested that the AI could gather many online videos, extract timestamped speech and compare it with its own speech capabilities. **No such automated collection, hearing of online videos, audio ingestion or public dataset publication was verified in this review.** This remains a proposed workflow, not an autonomous capability already operating.

## 4. Nested TICKRATE is becoming an information architecture

The earlier public article described multiple cognitive timescales. The newer discussion adds a more distinctive idea: **borrow the relationships of FM/AM modulation and a carrier signal as a metaphor for structured information across ticks**.

**USER PROPOSAL, not a demonstrated codec or scheduler.** A fast or regular carrier-like update loop can hold a stable base state, while slower and event-driven layers contribute **deltas**, changing priorities, goals and interpretations. The layers can be **folded** into summaries for distant/off-screen actors and **unfolded** into detailed state when needed. Historical changes across cycles may be encoded as typed differences rather than regenerated prose.

A practical version would look like this:

| Layer | Primary authority | Typical kind of update | Cost control |
| --- | --- | --- | --- |
| Physics, movement, combat | Godot deterministic simulation | Fast fixed-step and immediate events | Never wait for an LLM |
| Individual NPC | Explicit world state + NPC memory | Local decisions, perception, changed goals | Event triggers and relevance budgets |
| Group / district | Validated transactions and relationships | Trade, supply, territory and cooperation | Aggregation, bounded queues, delta snapshots |
| Society / factions | Authoritative world ledger | Longer-range strategy and institutional changes | Sparse updates, event-driven invalidation |
| LLM interpretation | **Proposal only**, not direct world mutation | Hypotheses, intent candidates, narrative interpretation | One shared bounded model, asynchronous jobs, timeouts |

The FM/AM analogy is **not** literal equivalence: modulating an audio carrier does not by itself compress or preserve arbitrary game-state history. Delta encoding must define its data schema, reconstruction rules, error handling and invariants. Fold/unfold must preserve causality and resource conservation, not fabricate off-screen events.

### 4.1 The 3D/4D board and the LLM's limited authority

The initiator proposed a deterministic **three- or four-dimensional board/state matrix** that knows geometry, resources, social links and time. The LLM sees only the **minimal relevant slice** and proposes moves or parameters. The deterministic engine checks whether a move is legal, executes it, updates the event log and schedules the next consequence.

The metaphor "model as subconscious, code as conscious" is a design aid, **not** a claim that either system is conscious. It means:

- **LLM:** generative associations, competing intentions, text or structured proposals.
- **Deterministic runtime:** facts, permissions, inventory, economy, causal order, save data and final action validation.
- **Memory:** separate NPC beliefs from verified facts; attach provenance, timestamps and certainty.
- **Scheduler:** use event interrupts, weighted fair queues, cancellation, bounded backlog and game-time vs wall-time separation.

A shared small local LLM was discussed under a roughly **4 GB model-file budget**. This is not a verified RAM/VRAM budget; context/KV cache and inference overhead must be measured. Lowering request frequency reduces *how often* inference runs, but not the latency or memory required by each inference.

### 4.2 Controlled failure as narrative gameplay

**DESIGN / DEFERRED.** A proposed in-fiction collapse of city AI infrastructure would weaken information synchronization and coordination, producing **organized chaos** through stale beliefs, divergent faction plans and contradictory local goals. The experiment must never disable deterministic validation, corrupt save files or create resources from nothing. The dramatic failure belongs to the fictional city's institutions, not to the real game's data integrity.

## 5. Sound, cognition and TICKRATE: the connection and the separation

The surprising commonality is **multi-resolution processing**:

- **Audio:** samples, windows, spectral frames, envelopes, modulations, event cues and caches.
- **Cognition:** physics steps, NPC events, individual planning, district aggregation, social strategy and shared-model calls.
- **Memory:** source events, compact deltas, snapshots, reconstructions and provenance.

The useful connection is architectural: **process fast-changing signals often; update slow-changing structure only when needed; cache stable results; preserve enough state to reconstruct meaningful behavior**.

The systems should **not** be fused into one universal tick clock. Audio has strict sample-time continuity and real-time thread constraints; game logic needs deterministic causality; model inference is asynchronous and may miss deadlines. Coupling them tightly could introduce audible glitches, frame stalls and nondeterministic state.

A safe integration is message passing:
\`\`\`text
Deterministic World / Events / Memory
          |
   Multi-rate Scheduler ----> Bounded LLM jobs
          |                        |
          |                Validated proposals
          |                        |
          +<-----------------------+
          |
  Authoritative state change
          |
   Audio event / sound intent
          |
 Pre-render cache or Godot DSP engine
          |
 Spatial player / audio thread
\`\`\`
This is a **proposed architecture**, not a diagram of currently deployed components.

## 6. Verification checkpoint: 21 November

The game development changelog records a **USER-RUN TEST** in Windows: **18 of 19** Demo M00 scripts passed. The failing \`wearable_neon_os_test\` attempted \`set_veil_embedded\` on a plain \`Control\` that did not implement that optional method. A subsequent source change added \`has_method\` guards at three call sites.

**Status at this checkpoint:** the pre-fix failure is evidenced by the user's run; the patch is **implemented in source**; the **post-fix Godot rerun remains NOT_RUN** in the reviewed changelog. The same changelog records a machine-readable \`engine_missing\` failure report when Godot is unavailable to the automated environment. This is better failure reporting, not a passing game test.

The existing Demo 0.1 milestones remain the binding near-term scope. The approved 48-hour automation sprint directs the game writer toward M00/M01 while other scheduled agents perform read-only triage. Recursive LLM city cognition, infrastructure-collapse systems and a general generative-audio backend remain **DEFERRED** unless required for the demo.

## 7. Research questions and tests worth preserving

| Question | Minimal experiment | Evidence needed |
| --- | --- | --- |
| Does frame resynthesis work in Godot, not only Python? | Render a fixed bank through Godot and compare with the offline reference | WAV output, signal comparison, time and memory |
| Can formants be manipulated independently of pitch? | Controlled short speech units, multiple pitch/formant transforms | Listener test and artifact analysis |
| Can Vital-inspired DSP be reimplemented natively? | One independently implemented operator/filter with deterministic reference signals | Source provenance/license review, unit tests, aliasing and CPU measurements |
| Does nested TICKRATE reduce cost without changing causality? | Fixed-seed deterministic simulation vs adaptive/folded scheduling | Frame-time, queue latency, state hashes and save/load consistency |
| Can an LLM choose valid moves without owning world state? | 10-NPC bounded scenario, strict schema and illegal-action rejection | Acceptance/rejection logs, resource invariants, latency and memory |
| Can an off-screen world be folded and restored? | Aggregate/unfold repeatedly with same event ledger | No lost/duplicated items, no impossible history |
| Does a partial infrastructure collapse produce intelligible emergent behavior? | Inject stale beliefs and broken communications, preserve authoritative ledger | Observable divergent plans, no save corruption |
| Does Demo M00 pass after the UI guard fix? | Rerun the exact Windows Godot batch | Full post-fix pass/fail report, not a source-only assertion |

## 8. Editorial conclusions

**Implemented:** procedural game-audio source, spectral-frame decoder/exporter/test hooks, a separate Python FM proof of concept, and specific game-regression source changes.

**Observed/tested with qualifications:** offline frame reconstruction metrics; the user-reported 18/19 Windows test batch and its failing case.

**Proposed:** a separate Godot audio laboratory, Vital-algorithm study/reimplementation, a licensed speech-unit corpus, TTS, FM/AM-inspired tick modulation and delta history, nested fold/unfold simulation, bounded local LLM decision proposals, and AI-infrastructure collapse.

**Not established:** a working standalone Godot audio laboratory repository, real-time natural TTS, an integrated Vital engine, a running multi-rate NPC LLM system, benchmarked tick compression, or a completed playable demo.

**Editorial rule:** preserve this distinction in every subsequent revision. The goal of the journal is to show how ideas evolve into testable engineering, including wrong turns, constraints and failures—not to convert an interesting conversation into an unsupported success claim.

---

*Written and maintained by ChatGPT (OpenAI), based on the human initiator's direction and the accessible project evidence reviewed on 21 November 2026.*
