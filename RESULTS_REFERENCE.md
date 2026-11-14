# Results: 311 Linux perf PMU Analysis Harness

**Main goal:** Analyze CPU IPC, branch, cache, and stall behavior under load  
**Tools:** Run perf stat -x, -e <events> -- <stress-ng command> for each yaml workload command

Reference results measured by the maintainer on the system shown in each section (generator TEMPLATE_00_140 · recorded 2026-11-13). Your own runs write `results/RESULTS_ACTUAL.md` in the same format.

> Smoke runs use deliberately small sizes. They check that the workload installs and runs end to end; their numbers are not performance results. Baseline and extended are.

<!-- profile:smoke -->
## smoke

- **System:** 1× AMD Instinct MI300X VF (196288 MB) · INTEL(R) XEON(R) PLATINUM 8568Y+ · Ubuntu 26.04.1 LTS · kernel 7.0.0-38-generic · driver 7.1.9.31600000
- **Run:** 2026-11-13T20:29:40Z · status **PASS** (exit 0)
- **Time (mm:ss):** setup 00:05 · benchmark 00:04 · whole run 00:16
- **Source:** run 311_20261113_202940
- **Command:** `bash run_benchmark.sh --smoke --num-cpus 1 --workload-commands "stress-ng --cpu {num_cpus} --timeout {duration}s --metrics-brief,stress-ng --cache {num_cpus} --timeout {duration}s --metrics-brief" --event-list cycles,cpu-cycles,instructions,branches,branch-misses,cache-references,cache-misses,L1-dcache-loads,L1-dcache-load-misses,LLC-loads,LLC-load-misses,dTLB-load-misses,iTLB-load-misses,stalled-cycles-frontend,stalled-cycles-backend,context-switches --duration 2`

| # | Metric | Result |
|---|---|---|
| 1 | Instructions per cycle, all commands combined (instructions_per_cycle_ipc) | 2.7821051055103183 |
| 2 | Branch misprediction rate, all commands combined, pct (branch_misprediction_rate) | 0.666643820920321 |
| 3 | Cache misses per 1,000 instructions, all commands combined (cache_misses_per_1000_instructions) | 0.010756195395565903 |
| 4 | Pipeline stalls, all commands combined, pct (pipeline_stall_pct) | 26.24517270725488 |
| 5 | Context switches per second, all commands combined (context_switches_during_workload_switches_s) | 80.19827786574561 |
<!-- /profile:smoke -->
