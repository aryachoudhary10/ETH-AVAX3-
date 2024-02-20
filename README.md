# ERC20 Token

This Solidity program serves as a "fungible token" creator, showcasing how the ERC20 contract is extended and utilized to create customized fungible tokens in the Solidity programming language. The primary purpose is to demonstrate how fungible tokens are created on Ethereum Virtual Machines (EVMs).

## Description

This program is a simple Solidity contract, which is a programming language used for developing smart contracts on the Ethereum blockchain. The contract includes various functions for interacting with the Fungible token contract. Notably, the `mint` function allows token minting, which can only be called by the owner of the contract. Additional functions like `transfer` and `approve` are also present.

## Getting Started

### Execution

To run this program, you can use Remix, an online Solidity IDE. Follow these steps:

1. Go to the Remix website at [https://remix.ethereum.org/](https://remix.ethereum.org/).
2. Create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., `Token.sol`).
3. Copy and paste the provided code into the file.

```solidity
// SPDX-License-Identifier: UNLICENSED
pragma solidity ^0.8.9;
import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract Token is ERC20 {
    address public owner;

    constructor(string memory name, string memory symbol) ERC20(name, symbol) {
        owner = msg.sender;
    }

    modifier onlyOwner {
        require(msg.sender == owner, "Only owner can do this");
        _;
    }

    function mint(address _to, uint256 amount) public onlyOwner {
        _mint(_to, amount);
    }
}
