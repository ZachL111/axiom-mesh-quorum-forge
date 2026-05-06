# axiom-mesh-quorum-forge

`axiom-mesh-quorum-forge` is a compact SQL repository for distributed systems, centered on this goal: Implement an SQL distributed systems project for quorum security rule linting, using safe and unsafe fixtures and remediation hints.

## Purpose

I want this repository to be useful as a quick reading exercise: fixtures first, implementation second, verifier last.

## Axiom Mesh Quorum Forge Review Notes

Start with `replica lag` and `lease drift`. Those cases create the widest score spread in this repo, so they are the best quick check when the model changes.

## What Is Covered

- `fixtures/domain_review.csv` adds cases for quorum health and lease drift.
- `metadata/domain-review.json` records the same cases in structured form.
- `config/review-profile.json` captures the read order and the two review questions.
- `examples/axiom-mesh-quorum-walkthrough.md` walks through the case spread.
- The SQL code includes a review path for `replica lag` and `lease drift`.
- `docs/field-notes.md` explains the strongest and weakest cases.

## Implementation Notes

The repository has two validation layers: the original compact policy fixture and the domain review fixture. They are separate so one can change without hiding failures in the other.

The SQL checks add a separate view over the domain review fixture.

## Command

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File scripts/verify.ps1
```

## Audit Path

That command is also the regression path. It verifies the domain cases and catches mismatches between the CSV, metadata, and code.

## Limits

This remains a local project with deterministic fixtures. It does not depend on credentials, hosted services, or live data. Future work should add richer malformed inputs before widening the public API.
