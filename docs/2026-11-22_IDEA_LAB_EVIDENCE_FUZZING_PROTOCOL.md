# IDEA-LAB — Evidence-First Idea Evaluation and Fuzzing Protocol
**Established:** 22 November 2026 · **Status:** research workflow, not a validated scoring instrument

## Purpose
Explore freely; evaluate rigorously. No idea is rejected merely for being strange. No idea is promoted into architecture merely because it sounds plausible or passes a self-selected demonstration. Maintain separate research and delivery lanes.

## 100-point rubric
Each dimension receives 0..its weight, based on explicit evidence, not assistant enthusiasm:

| Dimension | Max | Evaluation question |
|---|---:|---|
| Relevance to the target problem | 15 | Which documented requirement or failure does it solve? |
| Advantage over a fair baseline | 15 | Is there a measured improvement relative to a simpler method? |
| Feasibility | 10 | Can the mechanism be implemented with current constraints? |
| Efficiency | 10 | CPU, memory, latency, token cost, bandwidth and energy |
| Originality / meaningful novelty | 15 | What genuinely differs from published research, GitHub projects or known implementations? |
| Research value | 15 | What useful knowledge, including negative results, can the test produce? |
| Falsifiability / testability | 10 | Are there explicit rejection conditions and measurable observables? |
| Complexity / maintainability / risk | 5 | Is the burden justified and safely bounded? Higher is better |
| Cross-project transferability | 5 | Is reuse demonstrable rather than assumed? |
| **Total** | **100** | |

**Unknown is not zero and not full credit.** Report a provisional score as an interval or mark `N/E` (not evaluated). Publish a numeric total only when all dimensions are supported, while showing uncertainty and the evidence date. Rubric weights are policy choices; a score is a prioritization aid, not an empirical probability of success or proof of novelty.

Add two **independent** judgments: **Research Score (0–100)** prioritizes learning potential, novelty, falsifiability and experiment cost; **Engineering Score (0–100)** prioritizes measured baseline benefit, reliability, operational complexity and delivery. Do not derive either automatically from the headline weighted sum; each needs a stated method and evidence.

### Decision tags
- **A — Verified candidate:** reproducible advantage on stated tests, suitable for bounded integration review; not automatically production-ready.
- **B — Promising:** credible mechanism and test path, comparative proof pending.
- **C — Exploratory concept:** worthwhile to test, but benefit/novelty not established.
- **D — Not suitable now:** misaligned or unjustified burden; archive with reason, not erase.

## Originality check
Search peer-reviewed papers, technical reports, relevant open-source repositories, implemented products and (when relevant) patents. Record search terms, date, links, found analogues and actual differences. Distinguish known technique, adaptation, new combination, and possible original mechanism. Absence of matches is **not** proof of uniqueness. Prior art can reduce novelty while increasing feasibility; it does not automatically make an idea worthless. Open-source licensing is separate from novelty and must be checked before reuse.

## Minimum experiment card
```yaml
id: EXP-000
date: YYYY-MM-DD
project: SYNAPSE
question: "What concrete decision will this test inform?"
hypothesis: "If X, then metric Y improves under condition Z"
null_hypothesis: "No material difference from baseline"
baseline: "named version/algorithm"
candidate: "named version/algorithm"
input_dataset: "public/reproducible or hashed private input"
code_revision: "commit SHA"
seed: 1234
hardware_and_runtime: "actual environment"
metrics: [accuracy, lossless_recovery, latency_ms, bytes, cpu, memory]
acceptance_thresholds: "set before running"
falsification_conditions: "set before running"
fuzz_strategy: "see below"
repetitions: 30
observations: "raw output location"
limitations: "known blind spots"
verdict: "supported | not_supported | inconclusive"
next_action: "integrate | repeat | revise | archive"
```

## Fuzzing as an adversarial scientific method
Fuzzing does not prove correctness. It searches for failures, bias, edge cases and fragile assumptions.
1. Freeze a **golden baseline** with deterministic seeds and exact input/output checksums.
2. Mutate inputs: valid boundary cases, invalid structure, random noise, missing events, reordering, clock drift, phase jitter, data truncation, high update frequency, resource exhaustion and adversarial player actions.
3. Compare candidate vs baseline on **identical** traces and hardware. Include a no-fuzz control and increasing stress levels.
4. Track: failures per test, first failing seed, minimized counterexample, mean/p95 latency, bytes and CPU/RAM, state divergence after N ticks, exact and tolerant reconstruction rates. Also record crashes and silent corruption.
5. Preserve **all** failures, including failed fixes and regressions; never convert a proposed patch to a pass without rerunning the failing case.
6. Reverse-engineer outputs **and failures**: infer recurring structures, frequencies, phases, loss patterns, hidden dependencies and possible leakage. Test inferred rules on previously unseen seeds/data.
7. Use ablation: remove one component at a time (NID, FOLD, wave modulation, scheduler) to identify which mechanism produces any benefit.
8. Distinguish source inspection, test scripts, local user reports and independent reproduction. A green status is scoped to the tests actually run.

## SYNAPSE control experiment
Run the same autonomous-player trace through:
- **A (baseline):** deterministic event log + snapshots + conventional delta/binary compression.
- **B (core):** NID + nested TICKRATE + FOLD, with equivalent fidelity requirements.
- **C (wave candidate):** B plus phase/frequency-based representation or reconstruction.

Hold inputs, fidelity tolerance, tick budget, CPU/time accounting and error handling constant. Report compression including **decoder dictionaries, model metadata, phase synchronization, checkpoints and recovery overhead**. Compare exact state replay, event loss, latency distributions and behavior under drift/noise. Add an independent player acting without wave feedback. If C does not outperform B under predefined constraints, keep waves a side research track rather than a core dependency. If B does not improve on A, re-evaluate B rather than rationalizing its complexity.

## Reporting and authorship safeguards
The AI assistant frequently proposes, implements and narrates these experiments: **author/evaluator conflict exists**. State what the assistant did not run or observe. Link supporting evidence; separate reported results from reproduced results. A successful demo is not validation of a general claim. Document uncertainty and a plausible alternative explanation. Allow independent counter-review and do not replace a negative result with a persuasive narrative.

## Decision record template
`IDEA-ID | date | target problem | prior-art links | baseline | result (+ negative cases) | novelty status | research score | engineering score | total/uncertainty | verdict | next test | evidence refs`.

This protocol is intended to make experimentation *more free and less self-deceptive*, not to prohibit unusual hypotheses.
