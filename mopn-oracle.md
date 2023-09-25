# MOPN Oracle

## Introduction

As a map of popular NFTs, the market price of collections is a key indicator. However, when we attempted to integrate collections into the MOPN economic system, we encountered a challenge: as a fully on-chain game, how can we obtain information about NFT prices solely from on-chain data, without relying on a centralized oracle system, and prevent price manipulation?

To address this, we've established Collection Vault Staking as an on-chain Oracle, furnishing MOPN with signals regarding Collection floor prices.

## Vault

* Each collection has its own vault.
* The vault balance contains only $MT, sourced from a 5% share of NFT earnings and from staking.
* The amount of $MT in the vault determines the collection point.
* By staking $MT to the collection vault, you can boost the collection point and also share in the vault's earnings.

## Staking

* By staking $MT to any collection vault, you will boost the collection point, and receive the earnings from collection vault.
* Each Collection Vault issues $vtoken as staking shares. You will receive $vtoken in proportion to the amount of $MT you stake in the vault.
* At any time, you can redeem them, including the earnings, for $MT from the vault based on your stake shares.

## Bid NFT

The vault automatically makes bids for the collection NFTs, with prices updated in real-time. NFT holders can accept these bids to complete transactions. The bid price is calculated by multiplying the current vault balance by the bid factor.

$$
\text{Bid factor} = \left(1-\frac{\$MT\ \text{Amount Of the Latest Successful Bid}}{\text{Total \$MT balance of all Vaults}}\right) \times \text{Previous bid factor}
$$

## Auction NFT

* After the NFT holder successfully accepts the bid from the vault, the vault automatically initiates the Dutch Auction for the NFT.
* The auction price starts at 1,000% of the bid price in $MT, and decreases by 1% per 5 blocks.
* Anyone can purchase the auctioned NFT at the current price.
* After the auction is completed, 95% of the final price goes directly into the vault, and the remaining 5% is burned.
* When a collection is auctioning an NFT, staking $MT is not allowed.