# axiom-mesh-quorum-forge

`axiom-mesh-quorum-forge` is a SQL project for Distributed systems. It turns implement an SQL distributed systems project for quorum security rule linting, using safe and unsafe fixtures and remediation hints into a small local model with readable fixtures and a direct verification command.

## Reading Axiom Mesh Quorum Forge

Start with the README, then open `metadata/project.json` to check the constants behind the examples. After that, `fixtures/cases.csv` shows the compact path and `examples/extended_cases.csv` gives a wider look at the same rule.

## Design Sketch

The core is a scoring model over demand, capacity, latency, risk, and weight. That keeps node state, quorum behavior, and lease timing in one explicit decision path. The threshold is 161, with risk penalty 5, latency penalty 3, and weight bonus 3. The SQL project uses sqlite fixtures, views, and assertions to keep query behavior inspectable.

## Purpose

This is not a wrapper around a service. It is a self-contained project that shows how the model behaves when demand, capacity, latency, risk, and weight move in different directions.

## What It Does

- Uses fixture data to keep quorum behavior changes visible in code review.
- Includes extended examples for lease timing, including `surge` and `degraded`.
- Documents message ordering tradeoffs in `docs/operations.md`.
- Runs locally with a single verification command and no external credentials.
- Stores project constants and verification metadata in `metadata/project.json`.

## Fixture Notes

`examples/extended_cases.csv` adds six named cases. I kept the names plain so failures are easy to read in a terminal: baseline, pressure, surge, degraded, recovery, and boundary.

## Files Worth Reading

- `tests`: verification harness
- `fixtures`: compact golden scenarios
- `examples`: expanded scenario set
- `metadata`: project constants and verification metadata
- `docs`: operations and extension notes
- `scripts`: local verification and audit commands
- `schema.sql`: sqlite schema and view definitions

## Setup

Use a normal shell with SQL available on `PATH`. The verifier is written as a PowerShell script because the portfolio was assembled on Windows.

## Usage

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File scripts/verify.ps1
```

This runs the language-level build or test path against the compact fixture set.

## Verification

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File scripts/audit.ps1
```

The audit command checks repository structure and README constraints before it delegates to the verifier.

## Limits

The scoring model is simple by design. More domain-specific behavior should be added through explicit adapters or extra fixture classes rather than hidden constants.

## Next Directions

- Add malformed input fixtures so the failure path is as visible as the happy path.
- Split the scoring constants into a typed configuration object and validate it before use.
- Add a comparison mode that shows how decisions change when one signal is adjusted.
- Add one more distributed systems fixture that focuses on a malformed or borderline input.
