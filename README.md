# AetherLang

**Software-Defined Runtime for Heterogeneous Computing**

AetherLang is a software-defined language, compiler, runtime and orchestration layer for heterogeneous physical compute.

Its core goal is to let a workload move from a high-level requirement to a verified execution plan and then to concrete CPUs, GPUs, NPUs, accelerators and devices through explicit target knowledge.

## Core architecture

`Workload Intent -> Language -> Typed IR -> Hardware Knowledge -> Capability Analysis -> Target Selection -> Lowering -> Backend -> Runtime -> Device -> Observation -> Verification`

### 1. Language

AetherLang describes workloads, data, dependencies, resource requirements and execution constraints without hard-coding the program to one device.

### 2. Compiler and IR

The compiler converts source into a stable, inspectable intermediate representation. The IR retains the information needed for resource selection, memory placement, synchronization and target lowering.

### 3. Hardware Knowledge Layer

Every supported machine is described by a versioned target profile containing compute resources, memory, topology, supported operations, SDKs, runtimes, drivers, board interfaces, firmware compatibility and constraints.

Hardware facts carry provenance and confidence. Unsupported capabilities produce explicit diagnostics rather than guessed code.

See `docs/hardware-knowledge.md` and `docs/target-registry.md`.

### 4. Hardware-aware lowering

The compiler selects the best valid lowering path:

- native target operation
- verified runtime primitive
- composed supported operations
- explicit unsupported-target diagnostic

See `docs/code-generation.md`.

### 5. Runtime and orchestration

The runtime manages task graphs, events, resources, synchronization, placement and execution across heterogeneous devices. Adaptive decisions use target knowledge plus live telemetry.

See `docs/device-orchestration.md`.

### 6. Verification and receipts

Each execution can produce a reproducible receipt containing the workload hash, target profile, backend/toolchain versions, selected resources, telemetry and result hashes.

See `docs/verification-and-receipts.md`.

## Target integration model

A concrete device integration should provide:

- target profile
- capability discovery
- SDK/toolchain mapping
- driver/runtime mapping
- memory and synchronization mapping
- code generation/lowering
- build and link integration
- execution submission
- telemetry
- error translation
- compatibility validation

This keeps vendor-specific complexity inside backends while the language and runtime remain stable.

## Repository status

The repository currently contains the architecture and validation framework. The historical AetherLang source export has not yet been imported into this repository, so no production compiler/runtime implementation is claimed here.

When the export is available, it should be imported with provenance preserved and then validated through syntax checks, builds, unit tests, integration tests and target-specific execution tests.

## Engineering principles

1. Hardware facts must be explicit and versioned.
2. Generated code must be target-compatible before execution.
3. Unsupported operations must fail clearly rather than silently degrade.
4. Hardware-specific logic belongs in target adapters.
5. Adaptive scheduling must be observable and reproducible.
6. Performance claims require reproducible benchmarks.
7. Historical/recovered source must remain distinguishable from newly authored code.

## Documentation

- `docs/architecture.md` — system architecture
- `docs/hardware-knowledge.md` — target knowledge model
- `docs/target-registry.md` — target registry and topology
- `docs/code-generation.md` — hardware-aware lowering
- `docs/device-orchestration.md` — heterogeneous execution
- `docs/verification-and-receipts.md` — execution evidence
- `docs/roadmap.md` — implementation sequence
- `docs/source-recovery.md` — provenance and recovery rules
- `docs/validation-plan.md` — validation methodology

## License

No license has been selected yet. Until one is added, all rights are reserved by default.
