# Research questions

All five items below are **RESEARCH QUESTIONS**, not established findings. They concern the developing runtime and its contracts.

1. **Harness contribution:** How much reliability or portability comes from persistent, governed runtime services rather than the underlying model? Hold model and task selection fixed while varying the harness.

2. **Composed authority:** Can parent/child validity be specified and systematically tested across interruption, reentrancy and process boundaries? Extend fault-injection coverage beyond the single service boundary exercised by FD076.

3. **Recovery policy:** Which policies preserve useful progress without silently replaying uncertain external effects? Measure erroneous repeats, lost progress and manual inspection burden under controlled faults.

4. **State admission:** How should systems distinguish model-generated proposals from admitted knowledge or state? Test both inappropriate admissions and rejection of useful updates, including conflicting evidence.

5. **Comparative value:** Under equal model and compute budgets, what measurable benefit do MADOX's persistence and authority contracts provide over a minimal or stateless agent harness? Compare task completion, recovery correctness, invalid actions and operating cost.

The [current evidence](CURRENT_CAPABILITIES_AND_LIMITS.md) motivates these experiments. It does not answer them, establish a general safety guarantee or demonstrate superior task performance.
