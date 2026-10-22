# Hardware Knowledge Layer

AetherLang should understand the target machine before lowering and executing a workload.

## Target profile

Each supported target is represented by a versioned profile containing:

- CPU, GPU, NPU, DSP, FPGA, accelerator and memory resources
- instruction and operation capabilities
- memory hierarchy, address spaces and transfer costs
- interconnect topology and peer-access rules
- supported runtime, SDK and compiler toolchains
- board-support and device-driver interfaces
- peripheral and I/O capabilities
- power, thermal and performance constraints
- firmware/runtime version compatibility
- known limitations and unsupported operations

## Evidence levels

Every hardware fact must carry provenance:

1. vendor specification
2. official SDK/toolchain documentation
3. verified device probe
4. reproducible benchmark
5. inferred/estimated value

Inferred values must never silently become authoritative target facts.

## Capability resolution

Before lowering, AetherLang resolves each requested operation against the target profile. The result is one of:

- native operation
- supported through a runtime/SDK adapter
- transformable into supported operations
- unsupported with an explicit diagnostic

This prevents accidental generation of code that the target cannot execute.

## Backend contract

A backend should expose:

- capability discovery
- type and memory mapping
- operation lowering
- synchronization primitives
- device/queue submission
- event and error translation
- telemetry hooks
- resource cleanup
- version compatibility checks

The backend must report the exact target profile and toolchain used for a build.
