# Axiom Mesh Quorum Forge Walkthrough

This note is the quickest way to read the extra review model in `axiom-mesh-quorum-forge`.

| Case | Focus | Score | Lane |
| --- | --- | ---: | --- |
| baseline | quorum health | 206 | ship |
| stress | lease drift | 197 | ship |
| edge | replica lag | 262 | ship |
| recovery | membership churn | 234 | ship |
| stale | quorum health | 205 | ship |

Start with `edge` and `stress`. They create the widest contrast in this repository's fixture set, which makes them better review anchors than the middle cases.

The next useful expansion would be a malformed fixture around lease drift and membership churn.
