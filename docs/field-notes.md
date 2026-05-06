# Field Notes

I would read this project from the data inward: cases first, implementation second.

The domain cases cover `quorum health`, `lease drift`, `replica lag`, and `membership churn`. They sit beside the smaller starter fixture so the project has both a compact scoring check and a domain-flavored review check.

`edge` is the strongest case at 262 on `replica lag`. `stress` is the cautious anchor at 197 on `lease drift`.

The local verifier covers this data so the notes stay tied to code.
