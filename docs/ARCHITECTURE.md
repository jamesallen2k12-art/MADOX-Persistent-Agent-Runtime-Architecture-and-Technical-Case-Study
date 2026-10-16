# Architecture

Model output, admitted state and execution authority have different owners and lifetimes. The **Body** is the runtime and its state, lifecycle and capability services. A **cognitive substrate** supplies replaceable model inference through an interface.

Persistence, recovery and governed workflows are intended to be independently useful with existing models. The [README diagram](../README.md#three-boundaries) summarizes the boundaries.

## Replaceable cognition

The `CognitiveSubstrate` interface defines a `think` operation over runtime-supplied views of identity, state, retrieved memory, current context, available tools and budget. It returns a `CognitiveResult`: a response plus possible memory, belief, goal, unknown or tool-request candidates.

Candidates are **uncommitted proposals**, not canonical writes, approvals or evidence of execution. Separate runtime paths admit changes or authorize operations. This software interface does not isolate arbitrary same-process code.

## Canonical state and evidence

Body-owned stores retain evidence, versioned state, references and history, separately from temporary model context. Replacing a model should not redefine persistent identity or rewrite existing state.

A mock-swap test checks unchanged canonical continuity and belief history after cognition returns candidates. Restart/checkpoint tests check selected record recovery. Neither establishes truth, retrieval quality or exhaustive recovery.

Admission is domain-specific: operator belief revision uses separate review and approval. There is no universal automatic proposal-admission pipeline.

## Capability and authority

A **capability** is a registered operation. **Authority** permits its use in a particular scope and lifecycle state. A delegated **lease** bounds permission by scope, time, ancestry and declared budget.

Tests check revocation, expiry, budget exhaustion and refusal of self-extension or child authority exceeding its parent. A cooperating invocation context rechecks authority before its effect. This depends on using the reviewed services; it is not hostile-code containment.

## History, recovery and uncertainty

History distinguishes requests, admitted attempts and recorded outcomes. Finite workflows retain a completed prefix and require explicit continuation. Selected uncertain attempts remain blocked for inspection instead of automatically replaying.

A completion record does not prove external delivery. Metadata recovery cannot reconstruct deliberately unretained content. FD076 connects these distinctions to interrupted authority.

## Provider abstraction and evidence basis

Model-specific adapters and provider profiles implement a common contract. FD053 used two profiles and actual adapters with scripted transport in one local protocol family. Selected state survived composition and restart; arbitrary live interoperability or comparable reasoning quality was not demonstrated.

The selected private baseline is `8598e494128e0e6bf25a7d16ab093603195e789b`, from October 15, 2026. This historical reference is not a public-repository commit or coverage of every later increment.

FD numbers identify internal development increments, not public benchmarks. The principal retained evidence is:

- **Interface and state:** `CognitiveSubstrate`, `CognitiveResult`; tests named `test_mock_swap_and_cognition_leave_canonical_state_unchanged` and `test_runtime_persists_body_owned_state_across_restart`.
- **Provider interchange:** FD053's acceptance record reports 23 focused and 81 adjacent passing controls with scripted transport, with no failures, errors or skips in those runs.
- **Workflow recovery:** FD061 qualifies an operator-authored finite workflow with checkpoints; FD067 qualifies selected resident-interface continuation with offline/scripted fixtures.
- **State admission:** FD063 qualifies candidate provenance through the existing operator belief-revision path.
- **Authority:** lease and capability controls, together with the [FD076 regression account](FD076_CASE_STUDY.md).

These private-artifact references are not public reproduction instructions. No new experiments were run for this overview. Independent implementation assessment requires separately approved source/evidence access.
