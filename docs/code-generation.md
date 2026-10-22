# Hardware-Aware Code Generation

AetherLang code generation should move from intent to executable target code through explicit stages.

`Intent -> Typed IR -> Capability Analysis -> Target Selection -> Lowering -> Backend Code -> Build/Link -> Execution`

## Capability analysis

The compiler first determines the operations, memory classes, synchronization and I/O requirements of the workload. It then intersects those requirements with the selected target profile.

## Lowering strategy

Prefer this order:

1. direct native target operation
2. verified runtime primitive
3. composed sequence of supported primitives
4. explicit unsupported-target diagnostic

Do not generate speculative hardware instructions merely because they appear plausible.

## Build integration

A backend should produce a reproducible build description containing:

- target profile ID
- source/IR hash
- backend version
- compiler/toolchain versions
- SDK and driver versions
- build flags
- linked runtime components

## Verification

Generated artifacts should be checked before execution for target compatibility, required symbols, memory/address-space constraints and declared runtime dependencies.
