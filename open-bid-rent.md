# Open Bid Rent

## Introduction

The open bid rent is a new type of protocol without a fixed term, which is natively supported by the MOPN ERC-6551 account. At any moment, a renter with a higher bid will automatically replace the previous renter and become the new owner of ERC-6551 account. The nft holder can cancel the rental and reset the account owner at any time.

## Rental Floor Price

Each collection has a dynamic rental floor price, serving as the minimum rent for all MOPN accounts within that collection. The initial value of the rental floor price is 0.01 ETH, with a minimum value of 10^-5 ETH,

For this collection, whenever there are 5 continuous blocks without a bid rent transaction, the rental floor price decreases by 1%. However, when the collection generates a bid rent transaction, the rental floor price increases by 2%.

$$C' =  \begin{cases}  C \times (99\%)^t &\text{no bid rent for 5 continuous blocks } \\ C \times 102\% &\text{every bid rent} \end{cases}$$

## Dynamic Rental Price

Every nft's ERC-6551 account has a dynamic rental price, when the number of blocks since the last open bid rent transaction for that NFT is ≤ 200,000, the dynamic rental price is always at 110% of the last completed rent price. However, once it exceeds 200,000, it starts to decrease from 110% of the last completed rent price, decreasing by 0.0005% per block.

$$R' =  \begin{cases}   R\times 110\% & \text{if } n \leq 200,000 \\ R\times 110\%  \times \left(99.9995\% \right)^{(n-200,000)} & \text{if } n > 200,000 \end{cases}$$

## Bid Rent

When a player pays a price higher than both the dynamic rental price and the rental floor price, they will become the owner of the ERC-6551 account. The nft holder can cancel the open bid rent at any time.

Rent is settled in blocks and paid to the NFT holder. The NFT holder has the option to withdraw settled rent at any time or choose automatic settlement once the current rent ends.

When a new bid rent transaction occurs or when the NFT holder cancels the current bid rent, any $MT in the current ERC-6551 account will be transferred to the current owner's wallet address, along with any remaining rent refund.
