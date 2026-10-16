# FD076: parent/child authority across interruption

**DEMONSTRATED within a bounded software test.** FD076 identifies a durable, one-attempt file-read task with metadata recovery.

## Intended invariant

An old parent operation must not acquire fresh authority for a nested operation after Stop/Resume or invalidation of its original authority. Resume may permit new work; it must not revive an invalidated attempt.

Independent parent and child checks are insufficient if the child can obtain current permission while continuing an invalidated parent.

## Review-identified defect

Implementation review identified a gap between the parent's final validity check and entry into the child read service. If Stop and Resume occurred in that interval, the child could obtain fresh authority even though its parent belonged to the invalidated generation.

Checking before the child call did not establish the relationship throughout the nested operation.

This was identified through review. There is **no production-incident claim or retained failing pre-correction execution** of the later race regression.

## Bounded correction

The correction carries parent validity into the nested operation as an additional restriction. The child retains its authorization checks and rechecks parent validity at relevant boundaries. The inherited restriction is released at call exit to preserve unrelated fresh work.

In simplified terms, the required conjunction is:

```text
child may proceed only while:
    its own authorization remains valid
    AND the original parent remains valid
    AND the applicable budget permits progress
```

This explanatory pseudocode is not a complete algorithm. The change narrows authority without adding a model-controlled grant.

## Injected regression and acceptance

The regression named `test_stop_resume_between_parent_guard_and_child_read_cannot_renew_authority` injects Stop/Resume at the parent/child boundary. The corrected implementation's assertions establish that:

- the underlying source read is not called;
- the old attempt remains marked as requiring inspection and cannot be rerun;
- an unrelated, freshly authorized read can still proceed after Resume.

Related controls inject lost acknowledgement after a committed attempt claim and result-recording failure. They check that incomplete evidence remains an inspection-required attempt instead of permission to retry automatically.

The retained final FD076 acceptance record reports **47 distinct passing controls, zero skips**: 21 durable-task controls, 22 direct file-read controls and four adjacent task controls. These are not 47 separate tests of the race. Earlier evidence includes a fixture expectation error that was corrected; repeated passing runs are not counted as additional distinct controls.

The supported sequence is **review-identified defect → bounded correction → passing injected regression**.

## What this establishes, and what it does not

The case tests a concrete authority invariant at an affected service boundary: individually plausible checks can compose incorrectly across interruption.

This is evidence for a **specific cooperating software boundary**, not proof of hostile-code containment or universal revocation. It does not exhaust every scheduling interleaving, establish behavior across arbitrary process boundaries, or guarantee exactly-once external effects. The private source and original logs are not distributed here, so the reported result is not independently reproducible from this repository.
