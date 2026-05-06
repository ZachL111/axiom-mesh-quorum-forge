# Review Journal

The repository goal stays the same: implement an SQL distributed systems project for quorum security rule linting, using safe and unsafe fixtures and remediation hints. This note explains the added review angle.

The local checks classify each case as `ship`, `watch`, or `hold`. That gives the project a small review vocabulary that matches its distributed systems focus without claiming live deployment or external usage.

## Cases

- `baseline`: `quorum health`, score 206, lane `ship`
- `stress`: `lease drift`, score 197, lane `ship`
- `edge`: `replica lag`, score 262, lane `ship`
- `recovery`: `membership churn`, score 234, lane `ship`
- `stale`: `quorum health`, score 205, lane `ship`

## Note

This file is intentionally plain so the fixture remains the source of truth.
