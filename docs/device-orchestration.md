# Device Orchestration

AetherLang should provide one orchestration model across heterogeneous physical compute without pretending that all devices are interchangeable.

## Unified model

A workload is decomposed into tasks with:

- required capabilities
- input/output data types
- memory requirements
- latency/throughput objectives
- power or thermal constraints
- placement preferences
- migration/checkpoint requirements

The scheduler maps tasks onto compatible resources using the target registry and runtime telemetry.

## Physical execution boundary

The runtime is responsible for translating an approved plan into concrete device submissions. Vendor SDKs, drivers and board-support interfaces remain isolated inside target adapters.

## Feedback loop

`observe -> evaluate -> plan -> dispatch -> verify -> observe`

Every adaptive decision should be observable and attributable to the policy, target facts and telemetry that caused it.

## Failure behavior

If a target becomes unavailable or violates a constraint:

- stop new work that depends on the unavailable capability
- preserve execution state where supported
- select a compatible alternate only when policy permits
- record the reason for migration/failure
- never silently change semantic requirements
