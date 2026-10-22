# Target Selection

Target selection converts workload requirements into an explicit, verifiable execution target.

## Inputs

- required operations
- data types and memory classes
- latency/throughput objectives
- available target profiles
- topology and transfer constraints
- power/thermal limits
- runtime and SDK compatibility

## Selection rules

1. Eliminate targets missing required capabilities.
2. Eliminate targets with incompatible toolchain/runtime versions.
3. Score remaining targets against declared workload objectives.
4. Preserve the selected target and rationale in the execution plan.
5. Fail explicitly if no valid target remains.

A target must never be selected solely because it is available; semantic compatibility comes first.
