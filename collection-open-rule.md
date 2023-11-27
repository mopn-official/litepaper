---
description: Collection
---

# Collection Open Rule

The collection open rule was designed to protect against sybil attacks in the early stages, and  collections are gradually unlocked and available for placement on the MOPN map as specific Map Point milestones are reached.

On the day before the official release of MOPN, we took a [snapshot](https://dune.com/mopn/collection-open-rule) of an ERC721 collection on Ethereum. This snapshot considered the past 30 days transaction volume, owner count, and total supply to calculate a ranking score.

$$
\text{Score} = V \cdot e^{-k (S - S_0)^2} \cdot \frac{O}{S}
$$

$$V$$: The trading volume over the past 30 days

$$e$$: The base of the natural logarithm

$$k$$: A small positive constant `0.0000000001`

$$S$$: The total supply of collection

$$S_0​$$: A specified benchmark for the supply, set 10000

$$O$$: Refers to the number of collection owners
