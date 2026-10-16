# Current capabilities and limits

Selected evidence available by October 15, 2026. **DEMONSTRATED** refers to retained internal development evidence. **SUPPORTED BUT LIMITED** identifies narrower qualification than a general capability claim. Neither means independent public replication.

| Claim | Status | Limit |
|---|---|---|
| Replaceable cognition returns proposals rather than directly admitting canonical updates. | **DEMONSTRATED** | Interface and FD053 candidate non-admission checks; Python contracts do not isolate hostile code. |
| Selected canonical state survives restart and checkpoint recovery. | **SUPPORTED BUT LIMITED** | Selected records and continuity checks; not exhaustive crash recovery, disaster restoration or semantic correctness. |
| Scoped delegated authority supports revocation, expiry, ancestry and budget checks. | **SUPPORTED BUT LIMITED** | Implementation and selected test controls; not universal revocation or physical resource isolation. |
| FD076 preserves invalidated parent authority constraints through a nested read. | **DEMONSTRATED** | Passing injected Stop/Resume regression; no retained failing pre-correction run or production incident claim. |
| Selected persistent workflows and resident-interface continuation exist. | **SUPPORTED BUT LIMITED** | Finite, operator-authored workflows with explicit continuation and offline/scripted qualification; not unattended goal completion. |
| Selected provider interchange preserves Body-owned state. | **SUPPORTED BUT LIMITED** | FD053 uses actual adapters and two profiles with scripted transport in one protocol family; broad live interchange is not demonstrated. |
| General persistent autonomy. | **UNDER CONSTRUCTION** | General/final acceptance remains open; reliable long-horizon planning and autonomous project completion are not established. |
| Memory quality over extended operation. | **RESEARCH QUESTION** | Storage, provenance and revision foundations do not establish retrieval quality, consolidation or contradiction handling. |
| Broader live cross-model operation. | **RESEARCH QUESTION** | Cross-family quality, outages, latency and ongoing provider compatibility remain unqualified in the selected evidence. |
| Hardware-backed governing authority. | **UNDER CONSTRUCTION** | Software validation is distinct from completed hardware-backed verification; protected activation remains gated. |

See [Architecture](ARCHITECTURE.md#provider-abstraction-and-evidence-basis) for the retained evidence basis and [FD076](FD076_CASE_STUDY.md) for the principal case.

## Limits that affect interpretation

- **Software authority is not hostile-code containment:** cooperating service checks do not establish operating-system isolation, hardware security or resistance to a compromised host.
- **Persistence is not semantic truth:** an admitted record need not be correct or prove an operation completed.
- **Architectural model agnosticism exceeds the live demonstration:** scripted interchange establishes neither universal compatibility nor equivalent capability.
- **Recovery has a usability cost:** uncertainty can require manual inspection. Metadata cannot restore unretained content or prove delivery; arbitrary external effects have no exactly-once guarantee.
- **Protected work remains gated:** ordinary confirmation does not establish hardware-backed governing authority.
- **External replication is limited:** separate AI development agents are not independent human replication. Source and original logs are not public here.

No AGI, consciousness, solved alignment, production security or general long-horizon autonomy is established by this material. Comparative benefit over a simpler agent harness remains unmeasured in the selected evidence.
