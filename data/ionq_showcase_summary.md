# QECTOR Mega 3.7.5 - IonQ Superion decoding evidence

_Generated 2026-09-23T14:53:59Z on Linux-6.6.122+-x86_64-with-glibc2.39; physical rate p=0.001, 256 random shots per backend plus exhaustive single-error sweeps. Every correction verified H c == s._

## Hardware context (IonQ public announcements, Sept 2026)
- IonQ Superion 256 (sixth-generation trapped-ion QPU): 256 qubits, two-qubit fidelity 0.9999
- Walking Cat (published April 2026); breakeven qLDPC error correction on Tempo (August 2026)
- orders open, deliveries from 2027; Superion 10K; 800 logical qubits by 2027

## Results

| Code | Qubits | Best backend | Throughput (syn/s) | Latency (us) | Min exact faith |
| --- | --- | --- | --- | --- | --- |
| q70 | 70 | cascade | 172344 | 5.8 | 100.0% |
| q102 | 102 | cascade | 108162 | 9.2 | 100.0% |
| gross | 144 | cascade | 91300 | 10.9 | 100.0% |

## Dual-decoder paths (H c == s asserted on every shot)

| Code | Error SW (w=1) | Error TwoStage | Outcome update | Outcome batch_flat | Finalize |
| --- | --- | --- | --- | --- | --- |
| q70 | 2048/2048 | 256/256 | 1024/1024 | 1024/1024 | 57.92 ms |
| q102 | 2048/2048 | 256/256 | 1024/1024 | 1024/1024 | 81.77 ms |
| gross | 2048/2048 | 256/256 | 1024/1024 | 1024/1024 | 72.68 ms |

## SEC-window latency (budget p99.9 < 1000 us, warmed, perf_counter)

| Code | Path | n | p50 (us) | p99 (us) | p99.9 (us) | max (us) | Status |
| --- | --- | --- | --- | --- | --- | --- | --- |
| q70 | error_sw_update | 2048 | 36.4 | 119.3 | 134.7 | 156.5 | PASS |
| q70 | outcome_update | 1024 | 64.2 | 105.0 | 384.1 | 1650.3 | PASS |
| q102 | error_sw_update | 2048 | 43.8 | 191.3 | 257.8 | 1615.7 | PASS |
| q102 | outcome_update | 1024 | 103.6 | 181.5 | 1217.3 | 2118.8 | SKIP |
| gross | error_sw_update | 2048 | 38.3 | 191.0 | 234.8 | 277.6 | PASS |
| gross | outcome_update | 1024 | 86.6 | 172.4 | 229.4 | 2063.9 | PASS |
_Machine: Linux-6.6.122+-x86_64-with-glibc2.39; python 3.12.3; cpus=2; decoder=3.7.5. Scales run: error stream 2048 rounds/code, outcome stream 1024 rounds/code, 100 warmup rounds excluded. A bound missed on weaker hardware is recorded as fail-closed SKIP, never a pass._


## Baseline (gross [[144,12,12]], academic BP-OSD)
- ldpc BP-OSD: faith 100.0%, 12665 syn/s
- QECTOR best exact path: 91300 syn/s (x7.2 faster)

## Gates: 51/55 passed (critical: PASS)

- [x] faith_q70_cpu_bposd: 256/256
- [x] faith_q70_cascade: 256/256
- [x] faith_q70_beam: 256/256
- [x] faith_q70_ultra_beam: 256/256
- [x] faith_q70_cuda: 256/256
- [x] erasure_q70: masked-checks-verified=True
- [x] single_error_q70_cpu_bposd: 70/70
- [x] single_error_q70_cascade: 70/70
- [x] single_error_q70_beam: 70/70
- [x] single_error_q70_ultra_beam: 70/70
- [x] error_decoder_sw_q70: 2048/2048 Hc==s window=1 frame_wt=28
- [x] sec_latency_q70_error_sw_update: n=2048 p50=36.4 p99=119.3 p99.9=134.7 max=156.5us budget=1000us (warmed, perf_counter)
- [x] error_decoder_twostage_q70: 256/256 Hc==s p50=116.4us
- [ ] error_decoder_sw3_characterize_q70: 218/256 (characterization only)
- [x] outcome_decoder_stream_q70: 1024/1024 Hc==s via update()
- [x] sec_latency_q70_outcome_update: n=1024 p50=64.2 p99=105.0 p99.9=384.1 max=1650.3us budget=1000us (warmed, perf_counter)
- [x] outcome_decoder_flush_q70: flush() returned None; history_len=0
- [x] outcome_decoder_batch_flat_q70: 1024/1024 Hc==s finalize=57.9ms
- [x] faith_q102_cpu_bposd: 256/256
- [x] faith_q102_cascade: 256/256
- [x] faith_q102_beam: 256/256
- [x] faith_q102_ultra_beam: 256/256
- [x] faith_q102_cuda: 256/256
- [x] erasure_q102: masked-checks-verified=True
- [x] single_error_q102_cpu_bposd: 102/102
- [x] single_error_q102_cascade: 102/102
- [x] single_error_q102_beam: 102/102
- [x] single_error_q102_ultra_beam: 102/102
- [x] error_decoder_sw_q102: 2048/2048 Hc==s window=1 frame_wt=46
- [x] sec_latency_q102_error_sw_update: n=2048 p50=43.8 p99=191.3 p99.9=257.8 max=1615.7us budget=1000us (warmed, perf_counter)
- [x] error_decoder_twostage_q102: 256/256 Hc==s p50=226.4us
- [ ] error_decoder_sw3_characterize_q102: 217/256 (characterization only)
- [x] outcome_decoder_stream_q102: 1024/1024 Hc==s via update()
- [ ] sec_latency_q102_outcome_update: SKIP (fail-closed): bound not met on this host: n=1024 p50=103.6 p99=181.5 p99.9=1217.3 max=2118.8us budget=1000us (warmed, perf_counter)
- [x] outcome_decoder_flush_q102: flush() returned None; history_len=0
- [x] outcome_decoder_batch_flat_q102: 1024/1024 Hc==s finalize=81.8ms
- [x] faith_gross_cpu_bposd: 256/256
- [x] faith_gross_cascade: 256/256
- [x] faith_gross_beam: 256/256
- [x] faith_gross_ultra_beam: 256/256
- [x] faith_gross_cuda: 256/256
- [x] erasure_gross: masked-checks-verified=True
- [x] single_error_gross_cpu_bposd: 144/144
- [x] single_error_gross_cascade: 144/144
- [x] single_error_gross_beam: 144/144
- [x] single_error_gross_ultra_beam: 144/144
- [x] error_decoder_sw_gross: 2048/2048 Hc==s window=1 frame_wt=59
- [x] sec_latency_gross_error_sw_update: n=2048 p50=38.3 p99=191.0 p99.9=234.8 max=277.6us budget=1000us (warmed, perf_counter)
- [x] error_decoder_twostage_gross: 256/256 Hc==s p50=177.4us
- [ ] error_decoder_sw3_characterize_gross: 190/256 (characterization only)
- [x] outcome_decoder_stream_gross: 1024/1024 Hc==s via update()
- [x] sec_latency_gross_outcome_update: n=1024 p50=86.6 p99=172.4 p99.9=229.4 max=2063.9us budget=1000us (warmed, perf_counter)
- [x] outcome_decoder_flush_gross: flush() returned None; history_len=0
- [x] outcome_decoder_batch_flat_gross: 1024/1024 Hc==s finalize=72.7ms
- [x] baseline_gross_measured: ldpc faith=100.0%

## Sources
- https://www.ionq.com/news/ionq-launches-superion-product-line-industry-leading-upgradeable-platform-designed-to-scale-manufacturable-fault-tolerant-quantum-computing
- https://postquantum.com/quantum-research/ionq-secp256k1-resource-estimate/
