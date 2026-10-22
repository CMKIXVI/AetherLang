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

## Rules
1. Reject targets missing required capabilities.
2. Reject incompatible toolchain/runtime versions.
3. Score remaining targets against declared workload objectives.
4. Record the selected target and rationale in the execution plan.
5. Fail explicitly if no valid target remains.
