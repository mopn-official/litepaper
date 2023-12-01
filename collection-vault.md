# Collection Vault

## Introduction

As a map of popular NFTs, the market price of collections is a key indicator. However, when we attempted to integrate collections into the MOPN economic system, we encountered a challenge: as a fully on-chain game, how can we obtain information about NFT prices solely from on-chain data, without relying on a centralized oracle system, and prevent price manipulation?

To address this, we've established collection vault, which capture signals related to floor prices and trading activity through the auto-bid/auto-ask mechanism. This provides an innovation automated market maker solution for the NFT market.&#x20;

## Vault

* Each collection has its own vault.
* The vault balance contains only $MT, sourced from a 5% share of NFT earnings and from staking.
* The amount of $MT in the vault determines the collection point.
* By staking $MT to the collection vault, you can boost the collection point and also share in the vault's earnings.

## Stake

* By staking $MT to any collection vault, you will boost the collection point, and receive the earnings from collection vault.
* Each Collection Vault issues $vtoken as staking shares. You will receive $vtoken in proportion to the amount of $MT you stake in the vault.
* At any time, you can redeem them, including the earnings, for $MT from the vault based on your stake shares.

## Auto-Bid

* The vault automatically makes bids for the collection NFTs, with prices updated in real-time.&#x20;
* NFT holders can accept the bid to sell their own NFTs to the vault and receive $MT in return.
* The bid price is initially calculated as 20% of the collection vault balance.
* After the first vault ask transaction, the initial bid price is set to 75% of the vault's last ask price, increasing by 0.05% per block, with a maximum limit of 20% of the collection vault balance.

## Auto-Ask

* After the NFT holder successfully accepts the bid from the vault, the vault automatically initiates the Dutch Auction for the NFT.
* The auction ask price starts at 125% of the bid price in $MT, and decreases by 0.05% per block, reaching a minimum of 1 $MT.
* Anyone can buy the NFT at the current price.
* After the auction is completed, 99.5% of the final price goes directly into the vault, and the remaining 0.5% is burned.
* When a collection is auctioning an NFT, staking $MT is not allowed.
