# Target Adapter Specification

AetherLang target adapters isolate device-specific implementation from the language and core runtime.

## Required interface

A target adapter should expose:

```text
identify()
capabilities()
validate(plan)
lower(ir)
build(artifact)
submit(execution)
observe()
translate_error(error)
release(resources)
```

The exact programming interface can change, but the semantic contract should remain stable.

## Adapter responsibilities

- translate AetherLang capabilities into concrete SDK/runtime calls
- map memory and synchronization semantics
- select compatible kernels/instructions/runtime primitives
- expose device telemetry
- reject incompatible plans before submission
- preserve execution receipt metadata

## Adapter isolation

Vendor SDK headers, generated bindings, board-specific code and driver calls belong inside the adapter boundary. They should not leak into the language grammar or target-independent IR.

## Compatibility

Adapters must declare supported target-profile versions and toolchain ranges. A mismatch is a build/runtime error, not an automatic fallback.
