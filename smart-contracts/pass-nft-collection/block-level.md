# Block Level

Block Levels is randomly generated when NFT Collection has deployed because it's caculate by the collection's contract address and PassId.

```solidity
//this is a random str generated from "0112223333444445555556666666777777778888888889999999999aaaaaaaaaaabbbbbbbbbbbbccccccccccccc"
//represent the block level and amount distribution
bytes constant initBlockLevels =
    "678851ac687a239ab7ba923c49bcbb995c45accb6b508c4c6897a59cbcba98853ab3bca69c7c6878a967742b4a1";

bytes32 randomseed = keccak256(abi.encodePacked(address(this),PassId));

function blockLevels(bytes32 randomseed) public pure returns (uint8[] memory) {
        if (randomseed.length < 10) {
            revert RandomSeedInvalid();
        }
        unchecked {
            uint8[] memory blockLevels_ = new uint8[](91);
            uint256 startIndex = uint256(uint8(randomseed[0])) % 91;
            uint256 k = 0;
            uint256 index;
            for (uint256 i = 0; i < 9; i++) {
                uint256 groupIndex = uint256(uint8(randomseed[i + 1])) % 10;

                for (uint256 j = 0; j < 10; j++) {
                    index = (startIndex + (i * 10) + (groupIndex + j) % 10) % 91;
                    blockLevels_[k] = convertBytes1level(initBlockLevels[index]);
                    k++;
                }
            }
            if (startIndex == 0) {
                blockLevels_[k] = convertBytes1level(initBlockLevels[k]);
            } else {
                blockLevels_[k] = convertBytes1level(initBlockLevels[startIndex - 1]);
            }
            return blockLevels_;
        }
}

function blockLevel(bytes32 randomseed, uint256 blockIndex_) public pure returns (uint8) {
        if (randomseed.length < 10) {
            revert RandomSeedInvalid();
        }
        if (blockIndex_ > 90) {
            revert BlockIndexOverFlow();
        }
        unchecked {
            uint256 startIndex = uint256(uint8(randomseed[0])) % 91;
            if (blockIndex_ == 90) {
                if (startIndex == 0) {
                    return convertBytes1level(initBlockLevels[blockIndex_]);
                }
                return convertBytes1level(initBlockLevels[startIndex - 1]);
            }
            uint256 i = blockIndex_ / 10;
            uint256 groupIndex = uint256(uint8(randomseed[i])) % 10;
            uint256 index = (startIndex + i * 10 + (groupIndex + (blockIndex_ % 10)) % 10) % 91;
            return convertBytes1level(initBlockLevels[index]);
        }
}
```
