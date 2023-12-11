---
description: Collection
---

# Collection Open Rule

The collection open rule was designed to protect against sybil attacks in the early stages, and  collections are gradually unlocked and available for placement on the MOPN map as specific Map Point milestones are reached.

On December 4, 2023, at 00:00:00 UTC, a [snapshot](https://dune.com/mopn/collection-open-rule) was taken of an ERC721 collection on Ethereum. This snapshot considered the past 30 days' transaction volume, owner count, and total supply to calculate a ranking score.

$$
Score = (\text{Past 30 days volume})^2 \cdot \frac{\text{total owner}}{\max(\text{supply}, 10000)}
$$
