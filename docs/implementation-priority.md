# Implementation Priority

## P0 — Hardware knowledge core

1. Target profile schema
2. Capability model
3. Versioned target registry
4. Provenance and confidence fields
5. Compatibility diagnostics

## P1 — Compiler vertical slice

1. Minimal workload syntax
2. Typed IR
3. Capability analysis
4. Target selection
5. One deterministic lowering backend
6. Reproducible build metadata

## P2 — Runtime vertical slice

1. Task graph
2. Event lifecycle
3. Resource allocation
4. Submission and completion
5. Structured execution receipt

## P3 — First physical target

Select one concrete, testable hardware platform and implement its adapter end-to-end. Prove:

`source -> IR -> target knowledge -> lowering -> build -> device submission -> observation -> verified receipt`

## P4 — Scale breadth

Only after the first target is stable: additional CPU/GPU targets, accelerators, embedded boards, heterogeneous multi-device execution, migration, adaptive scheduling and thermal/resource policies.
