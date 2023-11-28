# MOPN

## Overview

MOPN (Map Of Populars NFTs) is an infinity fully on-chain game built on Ethereum, open-source, fair launch, no admin.

On a limited public map, players can freely place any ERC-721 NFTs. All NFTs follow the simple rules, engaging in open competition and cooperation, which leads to emergence of order.

## How To Play

1. MOPN builds a public map consisting of 999,271 tiles.
2. Players place any ERC-721 NFT on an unoccupied tile and earn MOPN Token ($MT) over time.
3. $MT can be used to buy Bombs for clearing tiles or mint land for tax collection.

## Account

For every NFT that participates, MOPN creates an [ERC-6551 account](erc-6551-account.md).

The $MT rewards earned from placing NFTs are allocated directly to the MOPN ERC-6551 account. The account owner has the authority to transfer these assets.

## Place

* The map is divided into 10,981 land areas, each containing 91 tiles.
* Lands can be minted with ETH or MOPN Token ($MT), Only on minted lands can NFTs be placed.
* NFTs must be placed adjacent to another NFT from the same collection, with a distance of 2 tiles or less, A bomb is necessary if the placed tile is within 2 tiles of an NFT from a different collection.
* NFTs placed on tiles automatically earn $MT per block based on their MOPN Point.

## Agent Place

* Any player can act as an agent to place other unplaced NFTs and earn different agent reward rates.
* Players cannot move or claim NFTs they've placed as agents.
* When an agent-placed NFT is moved, claimed, or bombed, the agent status ends, and the agenter's $MT rewards are settled automatically.
* The agent reward rate decreases as the number of agent-placed NFTs in the collection increases. The reward rate for the first agent-placed NFT in a collection is 60%, while the nth agent-placed NFT receives a reward rate of $$\textit{60\%} \cdot (1-\textit{0.06\%})^{(n-1)}$$.

## MOPN Token (ERC-20)

### Production

* MOPN Token ($MT) is an ERC-20 token with a total supply of 1 billion.
* The initial supply is 60/block, and it decreases by 3‰ every 50,000 blocks.

### Distribution

For each block, the produced $MT is distributed based on the proportion of Point from all NFTs placed on map.

When an NFT is placed by the owner, 90% of the earned $MT goes to the NFT's ERC-6551 account, 5% to the collection vault, and 5% to the land's ERC-6551 account where the NFT is placed.&#x20;

If placed by an agenter, the distribution rate for agenter is determined based on the order of placement, with the remaining 90% to the NFT owner.&#x20;

## MOPN BOMB (ERC-1155)

### Production

* MOPN BOMB is an ERC-1155 token, automatically issued by the system.
* To obtain bombs, the player must burn some $MT.
* The $MT burn amount depends on the number of opened tiles, the current $MT production per block, and the bomb production in the last 24 hours.

$$
\text{Amount} = \textit{50400} \cdot \frac{\textit{\$MT production}}{\text{tiles}} \cdot e^{\textit{14} \cdot \frac{\textit{bomb production}}{\text{tiles}} - \textit{1}}
$$

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

Every NFT's ERC-6551 account, when placed on the map, includes MOPN Point. This point measure the NFT's mining weight, consisting of both the tile point and the collection point.

### Tile Point

There are three types of tiles, each assigned with different point: Common (+1 point), Rare (+5 point) , and Legendary (+15 point).

### Collection Point

Every NFT collection holds a unique vault that receives 5% of all $MT mining rewards earned by the NFTs in the collection. The vault also allows anyone to stake $MT.

The collection point is initially set at $$\textit{0.003}\cdot\sqrt{\text{vault\ \$MT}}$$ . After the first vault ask transaction, it becomes the minimum between this value and $$\textit{0.03}\cdot\sqrt{\text{vault last\ ask\ price}}$$.
