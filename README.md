# MOPN

## Overview

MOPN (Map Of Populars NFTs) is an infinity fully on-chain game built on Ethereum, open-source, fair launch, no admin.

On a limited public map, players can freely place any ERC-721 NFTs. All NFTs follow the simple rules, engaging in open competition and cooperation, which leads to emergence of order.

## How To Play

1. MOPN builds a public MAP consisting of 999,271 tiles.
2. Players place any ERC-721 NFT on an unoccupied tile and earn MOPN Token ($MT) over time.
3. $MT can be used to auction Bombs, which can take out tiles.

## Account

For every NFT that participates, MOPN creates an ERC-6551 account. For more information about MOPN's ERC-6551 account, please see the [detail](mopn-erc-6551-account.md).

The $MT rewards earned from placing NFTs are allocated directly to the MOPN ERC-6551 account. The account owner has the authority to transfer these assets.

The MOPN ERC-6551 Account has implemented a mechanism for ownership transfers. Building on this, MOPN has designed an innovative open bid rent protocol, addressing the issue of separating ownership and usage rights for NFTs, for more [detail](open-bid-rent.md).

## Map

* The map is divided into 10,981 land areas, each containing 91 tiles.
* Lands can be minted with ETH or MOPN Token ($MT), Only on minted lands can NFTs be placed.
* NFTs must be placed adjacent to another NFT from the same collection, with a distance of 2 tiles or less, A bomb is necessary if the placed tile is within 2 tiles of an NFT from a different collection.
* NFTs placed on tiles automatically earn $MT per block based on their MOPN Point.

## MOPN Token (ERC-20)

### Production

* MOPN Token ($MT) is an ERC-20 token with a total supply of 1 billion.
* The initial supply is 60/block, and it decreases by 3‰ every 50,000 blocks.

### Distribution

For each block, the produced $MT is distributed based on the proportion of Point from all NFTs placed on map.

$$
\text{NFT Earnings} = \frac{\text{NFT Point}}{\sum \text{NFT Point} \text{(on Map)}} \times \text{Supply(blocks)}
$$

When an NFT is placed, 90% of the earned $MT is allocated to the NFT's ERC-6551 account, 5% goes to the collection vault, and the remaining 5% is distributed to the ERC-6551 account of the land where the NFT is placed.

## MOPN BOMB (ERC-1155)

### Production

* MOPN BOMB is an ERC-1155 token, issued by [LPDA](./#lpda-later-price-dutch-auction) (Later Price Dutch Auction).
* In each auction round, the system auctions one bomb for every 10 open lands.

### LPDA (Later Price Dutch Auction)

* The price for bombs in every auction round begins at 10,000 $MT and decreases by 1% every 5 blocks.
* Once all the bombs are auctioned out, the next round will automatically start.
* Transactions that bid higher than the price of the fifth transaction after the current one in this round will automatically receive a refund for the difference.
* The used $MT for auctioning bombs will be burned.

### Use

* If the tile of the placed NFT is within 2 tiles of an NFT from a different collection, a bomb is required to be used.
* The bomb will remove NFTs from different collections in the area from the map. For every NFT removed, one bomb needs to be used.
* The used bomb tokens will be burned.

## MOPN Land (ERC-721)

* Land is an ERC-721 NFT with a fixed total supply of 10,981 and consisting of 91 tiles.
* After a land is minted, NFTs can be placed on its tiles.
* NFTs on the 91 tiles contribute 5% of their $MT earnings to the land NFT's ERC-6551 account.
* All land NFTs are issued through two methods: ETH curve minting and $MT auction minting.

### ETH Curve Minting

* Pricing starts at 0.02 ETH, with a price increase of 1‰ for each completed ETH curve mint.
* ETH curve minting was available starting from March 31, 2023.

### $MT Auction Minting

* The starting price is 1 million $MT, and one land will be auctioned per round, with the price decreasing by 1% per 5 blocks.
* When the current $MT auction minting is complete, the next round will automatically start.
* The used $MT for auctioning land will be burned.

## MOPN Point

Every NFT's ERC-6551 account, when placed on the map, includes MOPN Point — a non-transferable ERC-20 token. These tokens are used to measure the NFT's current mining weight, consisting of both the tile point and the collection point.

* **Tile Point**: There are three types of tiles, each assigned with different point: Common (+1 point), Rare (+5 point) , and Legendary (+15 point).
* **Collection Point**: Every NFT collection holds a unique vault, and the collection point is determined by the $MT balance within this vault, multiplied by 10^(-4).
