# Validation Plan

## Static checks
- Enumerate source and configuration files and identify languages/build systems.
- Run the native formatter, linter, and compiler where the toolchain is installed.
- Check dependency manifests for version consistency and known deprecated configuration.
- Validate JSON, YAML, TOML, and other machine-readable schemas.

## Functional checks
- Run existing unit and integration tests before changes.
- Add minimal deterministic fixtures around parser, IR, task graph, scheduler, and backend contracts.
- Include negative tests for invalid operations and unsupported targets.

## Runtime checks
- Test cancellation, timeout, dependency failure, event ordering, and resource unavailability.
- Ensure telemetry records carry timestamps, units, source, and environment metadata.
- Verify adaptive changes can be disabled and reproduced.

## Benchmark checks
- Publish inputs, command lines, environment versions, and raw outputs.
- Compare against a simple baseline and report variance.
- Never infer speedups from architecture diagrams or simulations alone.

## Reporting format
For each check record: command, environment, result (pass/fail/blocked/not run), concise evidence, and follow-up action. Do not mark unexecuted checks as passed.
