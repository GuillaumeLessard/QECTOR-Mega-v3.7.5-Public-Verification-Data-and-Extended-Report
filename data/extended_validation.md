# Extended Validation Suite - QECTOR Mega 3.7.5

_Generated 2026-09-23T14:54:18Z on Linux-6.6.122+-x86_64-with-glibc2.39; elapsed 19.4s. Every value measured in-process; PROJECTION rows are exact binomial computations, NOT samples._

## Gates: 15/15 (critical: PASS)

- [x] A_planar_construct_d3_d15: commutation certified d=3..15 (k=0 by generator construction)
- [x] A_hp_k1_d3_d7: HP surface k==1, commutes, d=3/5/7
- [x] A_toric_k2_l2_l6: toric k==2 for l=2..6
- [x] A_zero_unfaithful_scaling: unf=0
- [x] A_suppression_d3_to_d7: HP LER d=3:0.05054 -> d=7:0.01270 mono~True
- [x] B_rep100k_matches_exact: exact=5.336e-06 in 99% CI=[3.904e-06,1.024e-04] fails=2/100000
- [x] B_zero_unfaithful_highshot: unf=0
- [x] B_oracle_monotone: exact tails strictly decrease p=1e-2->1e-4 per distance
- [x] C_probes_recorded: 9 probe rows; cuda=True opencl=True simd=SimdLevel.Avx512
- [x] D_zero_unfaithful_all: 75612 vectors, unf=0
- [x] D_ionq_weight1_exhaustive: weight-1 exhaustive on q70/q102/gross
- [x] F1_depolarizing_faithful: X unf=0 Z unf=0 / 4096
- [x] F2_phenomenological_faithful: unf=0/4096 on noisy syndromes
- [x] F3_stim_circuit_faithful: unf=0/2048 circuit-level detectors
- [x] F4_dynamic_erasure: 512/512 masked-verified

## A. Distance scaling (planar-proper d=3..15 construct; HP d=3/5/7 + toric l=2..6 k>=1 decode)

| code | n | k | LER@0.05 | 95% CI | shots |
| --- | --- | --- | --- | --- | --- |
| HP surface d=3 | 13 | - | 0.05054 | [0.04424,0.05768] | 4096 |
| HP surface d=5 | 41 | - | 0.02661 | [0.02211,0.03200] | 4096 |
| HP surface d=7 | 85 | - | 0.01270 | [0.00743,0.02160] | 1024 |

## B. High-shot Monte Carlo + 1e7 oracle

- CSS repetition Z d=7: LER=0.000020 CI=[0.000005,0.000073] shots=100000
- HP surface d=3: LER=0.008300 CI=[0.007134,0.009655] shots=20000
- CSS toric l=3: LER=0.009200 CI=[0.007508,0.011269] shots=10000

Exact 1e7 oracle rows are in extended_validation.csv (B_oracle).

## C. Hardware probes

- cuda_is_available: measured True
- opencl_is_available: measured True
- simd: measured SimdLevel.Avx512
- probe_backends: measured [('cutlass_tensor_core', False, 'CUTLASS_PATH / cutlass/cutlass.h not found; using reference GEMM'), ('cuda_nvrtc', True
- opencl_devices: measured [('cutlass_tensor_core', False, 'CUTLASS_PATH / cutlass/cutlass.h not found; using reference GEMM'), ('cuda_nvrtc', True
- CUDABatchDecoder: measured constructs+decodes faithful=True
- CUDABpOsdDecoder: measured constructs+decodes faithful=True
- fpga: measured backend=FpgaBpOsd
- QECTOR_FPGA_PCI_ADDR: measured unset (expected)

## D. Exhaustive residual proofs

- rep_d7: tested=20029 (exhaustive 29) unf=0
- hp_d3: tested=20092 (exhaustive 92) unf=0
- toric_l3: tested=20172 (exhaustive 172) unf=0
- ionq_q70: tested=5071 (exhaustive 71) unf=0
- ionq_q102: tested=5103 (exhaustive 103) unf=0
- ionq_gross: tested=5145 (exhaustive 145) unf=0

## E. Formal verification (omitted here; user compiles in Colab)

## F. Advanced noise

- depolarizing: {"p_dep": 0.03, "px": 0.02, "pz": 0.02, "shots": 4096, "unfaithful_x": 0, "unfaithful_z": 0, "code": "HP surface d=3"}
- phenomenological: {"p_data": 0.02, "q_meas": 0.01, "shots": 4096, "unfaithful_noisy_syn": 0}
- stim_circuit: {"status": "measured", "shots": 2048, "n_detectors": 4, "unfaithful": 0, "backend": "qector_BPOSDDecoder"}
- erasure_dynamic: {"code": "gross", "shots": 512, "erasure_rate": 0.05, "masked_verified": 512, "total": 512}

## G. Graphs

- /content/Tests/qector_results/graphs/validation_ler_vs_distance.png
- /content/Tests/qector_results/graphs/validation_oracle_1e7.png
- /content/Tests/qector_results/graphs/validation_wilson_width.png
- /content/Tests/qector_results/graphs/validation_throughput.png
- /content/Tests/qector_results/graphs/validation_gates.png
