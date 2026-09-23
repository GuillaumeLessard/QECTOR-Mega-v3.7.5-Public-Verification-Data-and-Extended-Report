# MegaQuOp dual-decoder specification harness — QECTOR Mega 3.7.5

_Generated 2026-09-23T14:44:15.280111+00:00_

**Reference:** arXiv:2608.25027 — Real-time decoder for a MegaQuOp quantum computer using a single CPU
**Authors:** Min Ye, Andrii Maksymov, Nicolas Delfosse
**Paper demo CPU:** see arXiv:2608.25027 (literature only; not used as a timing baseline)
**This host:** Intel(R) Xeon(R) Platinum 8481C CPU @ 2.70GHz

## Gates: 61/61 (critical: PASS)

## Mapping paper → wheel

| Paper component | Wheel API exercised |
| --- | --- |
| Error Decoder (continuous) | `SlidingWindowDecoder(window_size=1).update` + Pauli frame XOR |
| Outcome Decoder (low-latency) | `IonQSuperionDecoder.update` + `flush` + `decode_batch_flat` |
| Second stage | `TwoStageDecoder.decode` |
| Beam-search software path | `prefer_beam` / `prefer_ultra_beam` |
| Walking Cat blocks | `IonQSuperionDecoder(code=q70|q102|gross)` |

## Code parameters

- **q70**: {'n': 70, 'n_checks': 70, 'd': 9, 'max_t': 4, 'params': (70, 6, 9), 'ok': True}
- **q102**: {'n': 102, 'n_checks': 102, 'd': 9, 'max_t': 4, 'params': (102, 22, 9), 'ok': True}
- **gross**: {'n': 144, 'n_checks': 144, 'd': 12, 'max_t': 5, 'params': (144, 12, 12), 'ok': True}

## Dual-path latency (measured)

- **q70** error p99.9=304.6µs [PASS/1ms] | outcome p99.9=158.2µs [PASS/1ms] finalize=9.4ms
- **q102** error p99.9=92.7µs [PASS/1ms] | outcome p99.9=76.0µs [PASS/1ms] finalize=19.2ms
- **gross** error p99.9=2152.4µs [PASS/1ms] | outcome p99.9=1458.2µs [PASS/1ms] finalize=31.7ms

## Gate detail

- [x] import_version: v=3.7.5
- [x] params_q70: n=70 checks=70 d=9 max_t=4 params=(70, 6, 9)
- [x] params_q102: n=102 checks=102 d=9 max_t=4 params=(102, 22, 9)
- [x] params_gross: n=144 checks=144 d=12 max_t=5 params=(144, 12, 12)
- [x] error_decoder_faith_q70: 2048/2048 Hc==s frame_wt=28
- [x] sec_q70_error_sw_w1_budget_1000us: n=1741 steady=True p50=13.3 p99=54.5 p99.9=304.6 max=1080.2us budget=1000us
- [x] sec_q70_error_sw_w1_budget_5000us: n=1741 steady=True p50=13.3 p99=54.5 p99.9=304.6 max=1080.2us budget=5000us
- [x] outcome_stream_faith_q70: 1024/1024 Hc==s via update()
- [x] sec_q70_outcome_update_budget_1000us: n=871 steady=True p50=12.8 p99=29.5 p99.9=158.2 max=158.2us budget=1000us
- [x] sec_q70_outcome_update_budget_5000us: n=871 steady=True p50=12.8 p99=29.5 p99.9=158.2 max=158.2us budget=5000us
- [x] outcome_flush_q70: flush()=None history_len=0
- [x] outcome_batch_flat_faith_q70: 1024/1024 finalize=9.4ms
- [x] twostage_faith_q70: 128/128 p50=81.6us
- [x] backend_q70_cpu_bposd: 128/128 thr=25915/s
- [x] backend_q70_cascade: 128/128 thr=26368/s
- [x] backend_q70_beam: 128/128 thr=42479/s
- [x] backend_q70_ultra_beam: 128/128 thr=20245/s
- [x] backend_q70_cuda: NOT_AVAILABLE: ValueError
- [x] backend_q70_opencl: NOT_AVAILABLE: ValueError
- [x] w1_q70_cpu_bposd: 70/70
- [x] w1_q70_beam: 70/70
- [x] w1_q70_ultra_beam: 70/70
- [x] dual_coupling_q70: sw=256/256 outcome=256/256
- [x] error_decoder_faith_q102: 2048/2048 Hc==s frame_wt=46
- [x] sec_q102_error_sw_w1_budget_1000us: n=1741 steady=True p50=17.4 p99=74.9 p99.9=92.7 max=93.2us budget=1000us
- [x] sec_q102_error_sw_w1_budget_5000us: n=1741 steady=True p50=17.4 p99=74.9 p99.9=92.7 max=93.2us budget=5000us
- [x] outcome_stream_faith_q102: 1024/1024 Hc==s via update()
- [x] sec_q102_outcome_update_budget_1000us: n=871 steady=True p50=17.2 p99=38.4 p99.9=76.0 max=76.0us budget=1000us
- [x] sec_q102_outcome_update_budget_5000us: n=871 steady=True p50=17.2 p99=38.4 p99.9=76.0 max=76.0us budget=5000us
- [x] outcome_flush_q102: flush()=None history_len=0
- [x] outcome_batch_flat_faith_q102: 1024/1024 finalize=19.2ms
- [x] twostage_faith_q102: 128/128 p50=98.2us
- [x] backend_q102_cpu_bposd: 128/128 thr=12557/s
- [x] backend_q102_cascade: 128/128 thr=12356/s
- [x] backend_q102_beam: 128/128 thr=34726/s
- [x] backend_q102_ultra_beam: 128/128 thr=10521/s
- [x] backend_q102_cuda: NOT_AVAILABLE: ValueError
- [x] backend_q102_opencl: NOT_AVAILABLE: ValueError
- [x] w1_q102_cpu_bposd: 102/102
- [x] w1_q102_beam: 102/102
- [x] w1_q102_ultra_beam: 102/102
- [x] dual_coupling_q102: sw=256/256 outcome=256/256
- [x] error_decoder_faith_gross: 2048/2048 Hc==s frame_wt=59
- [x] sec_gross_error_sw_w1_budget_1000us: n=1741 steady=True p50=25.2 p99=135.9 p99.9=2152.4 max=2180.5us budget=1000us
- [x] sec_gross_error_sw_w1_budget_5000us: n=1741 steady=True p50=25.2 p99=135.9 p99.9=2152.4 max=2180.5us budget=5000us
- [x] outcome_stream_faith_gross: 1024/1024 Hc==s via update()
- [x] sec_gross_outcome_update_budget_1000us: n=871 steady=True p50=24.6 p99=82.4 p99.9=1458.2 max=1458.2us budget=1000us
- [x] sec_gross_outcome_update_budget_5000us: n=871 steady=True p50=24.6 p99=82.4 p99.9=1458.2 max=1458.2us budget=5000us
- [x] outcome_flush_gross: flush()=None history_len=0
- [x] outcome_batch_flat_faith_gross: 1024/1024 finalize=31.7ms
- [x] twostage_faith_gross: 128/128 p50=133.9us
- [x] backend_gross_cpu_bposd: 128/128 thr=12381/s
- [x] backend_gross_cascade: 128/128 thr=12753/s
- [x] backend_gross_beam: 128/128 thr=19708/s
- [x] backend_gross_ultra_beam: 128/128 thr=6465/s
- [x] backend_gross_cuda: NOT_AVAILABLE: ValueError
- [x] backend_gross_opencl: NOT_AVAILABLE: ValueError
- [x] w1_gross_cpu_bposd: 144/144
- [x] w1_gross_beam: 144/144
- [x] w1_gross_ultra_beam: 144/144
- [x] dual_coupling_gross: sw=256/256 outcome=256/256

## Honesty limits

- Does **not** claim paper-host timings or a full 408-logical-qubit end-to-end DEM workload.
- Stretch % is wall vs (rounds × 1 ms) budget, **not** the paper’s noise-table stretch under matched DEM.
- CUDA/OpenCL/FPGA may be NOT_AVAILABLE on CPU-only hosts (fail-closed).

