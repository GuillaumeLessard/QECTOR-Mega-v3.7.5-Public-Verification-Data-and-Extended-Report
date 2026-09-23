# MegaQuOp 408 logical qubits — QECTOR Mega 3.7.5

_Generated 2026-09-23T14:52:56.407128+00:00_

**Scale:** 68 × Q70[[70,6,9]] = **408 logical qubits** (4760 physical).
**Host:** Intel(R) Xeon(R) CPU @ 2.00GHz (live host only; paper CPU is literature reference, not a baseline).

## Gates: 12/15 critical=PASS

## Gate list

- [x] **import**: v=3.7.5
- [x] **q70_params**: params=(70, 6, 9)
- [x] **build_68_blocks**: blocks=68 phys_qubits=4760 checks=4760 build_s=0.04 rss_kb=52156
- [x] **logical_qubit_count**: 68×6=408
- [x] **error_path_faith_408**: 17408/17408 Hc==s across 68 blocks × 256 rounds
- [ ] **sec_error_fullsystem_budget_1000us**: bound not met on this host: n=256 p50=2251.4 p99=4374.4 p99.9=4645.4 max=4645.4us vs 1000us (68 blocks/tick)
- [x] **sec_error_fullsystem_budget_5000us**: n=256 p50=2251.4 p99=4374.4 p99.9=4645.4 max=4645.4us vs 5000us (68 blocks/tick)
- [x] **error_path_parallel_faith_408**: 4352/4352 workers=2 p50=4208us p99.9=5294us
- [x] **outcome_stream_faith_408**: 8704/8704 Hc==s
- [ ] **sec_outcome_fullsystem_budget_1000us**: bound not met on this host: n=128 p50=3942.1 p99.9=6030.2 max=6030.2us vs 1000us
- [ ] **sec_outcome_fullsystem_budget_5000us**: bound not met on this host: n=128 p50=3942.1 p99.9=6030.2 max=6030.2us vs 5000us
- [x] **outcome_finalize_faith_408**: 8704/8704 finalize_wall=0.48s
- [x] **weight1_sample_blocks**: 560/560 over 8 blocks
- [x] **dual_coupling_408**: sw=2176/2176 outcome=2176/2176
- [x] **mixed_factories_faith**: 22/22

## Honesty

- Independent qLDPC blocks (no cross-block hyperedges).
- Synthetic i.i.d. noise at p=1e-3; not a full Stim 31.5M-op DEM.
- SEC budgets are env-overridable (QECTOR_SEC_BUDGET_*_US); FAIL_HOST means live host missed budget.

