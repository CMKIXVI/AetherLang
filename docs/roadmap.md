# AetherLang Roadmap

This is a proposed, test-driven order of work. Dates and completion status are intentionally not asserted.

## Phase 0 — Source recovery and provenance
- Import the original historical export/archive.
- Inventory all files, hashes, duplicates, and archive paths.
- Label each artifact as recovered-original, reconstructed, or newly authored.
- Preserve originals in an immutable provenance area before refactoring.
- Record missing dependencies and unverified claims.

## Phase 1 — Minimal language-to-IR vertical slice
- Specify the smallest useful workload language.
- Implement parser, diagnostics, and schema validation.
- Define a versioned target-independent IR.
- Add positive/negative fixtures and deterministic output tests.

## Phase 2 — Simulator and runtime graph
- Implement a CPU-only simulation backend.
- Represent task dependencies, events, status, retries, and cancellation.
- Add deterministic replay and structured traces.

## Phase 3 — Scheduler and measurements
- Discover resources from an explicit simulated capability catalogue.
- Implement a baseline scheduler and one topology-aware policy.
- Publish benchmark inputs, metrics, environment metadata, and raw results.
- Compare policies against baselines; avoid unsubstantiated speedup claims.

## Phase 4 — Target adapters
- Define a versioned backend interface.
- Add one concrete target only after confirming SDK access, licenses, hardware and testability.
- Validate capability checks and error reporting before attempting optimization.

## Phase 5 — Adaptive behavior and migration
- Add policy-bounded adaptive scheduling.
- Define checkpoint/state-transfer contracts per backend.
- Test rollback, interruption, partial failure and observability.

## Release gates
- Reproducible build and test commands.
- Dependency/security review.
- Architecture and API documentation updated with implementation evidence.
- Benchmark reports include exact hardware/software configuration and raw data.
- Clearly state any untested hardware and unfinished capabilities.
