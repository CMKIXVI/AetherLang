# Target Registry

The target registry is the machine-readable catalogue used by the compiler and runtime to select valid execution targets.

## Target identity

A target entry should identify:

- vendor and device family
- exact device/model when known
- architecture and ISA
- firmware/runtime versions
- supported operating environment
- compiler/SDK versions
- board or platform variant

## Resource graph

Represent the machine as a graph rather than a flat device list:

`compute -> memory -> interconnect -> compute`

Edges describe transfer paths, bandwidth/latency characteristics, synchronization mechanisms and access restrictions.

## Versioning

Target profiles are immutable by version. A workload execution receipt records the profile version, backend version and toolchain versions so a result can be reproduced.

## Registry rules

- Never silently substitute a different device.
- Reject incompatible SDK/runtime versions.
- Keep vendor-specific details behind stable AetherLang capability interfaces.
- Permit local/private target profiles without changing the language core.
