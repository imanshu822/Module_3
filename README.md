# MyToken Smart Contract

## Overview

This is a Solidity smart contract that implements an ERC20 token named "DogeCoin" with the symbol "Dog". The contract is built using the OpenZeppelin library for secure and reusable Solidity components. It includes minting and burning functionalities and is owned by a specific address.

## Features

- **ERC20 Standard**: Implements the standard ERC20 token interface.
- **Ownership**: Uses the `Ownable` contract from OpenZeppelin to restrict certain functions to the owner.
- **Minting**: The owner can mint new tokens.
- **Burning**: Any token holder can burn their own tokens.

## Prerequisites

- Solidity ^0.8.0
- OpenZeppelin Contracts

## Contract Details

- **Token Name**: DogeCoin
- **Token Symbol**: Dog
- **Owner Address**: 0x5B38Da6a701c568545dCfcB03FcB875f56beddC4

## Contract Structure

### Imports

```solidity
import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/access/Ownable.sol";
```

The contract imports the ERC20 and Ownable contracts from OpenZeppelin, which provide standard token functionality and ownership control respectively.

### Contract Declaration

```solidity
contract MyToken is ERC20, Ownable {
```

The `MyToken` contract inherits from `ERC20` and `Ownable`.

### Constructor

```solidity
constructor() ERC20("DogeCoin", "Dog") Ownable(address(uint160(0x5B38Da6a701c568545dCfcB03FcB875f56beddC4))) {
    _mint(msg.sender, 1000 * 10 ** decimals());
}
```

- **ERC20 Initialization**: Sets the token name to "DogeCoin" and the symbol to "Dog".
- **Ownable Initialization**: Sets the owner address to `0x5B38Da6a701c568545dCfcB03FcB875f56beddC4`.
- **Minting**: Mints 1000 tokens (considering the decimals) to the deployer of the contract.

### Mint Function

```solidity
function mint(address to, uint256 amount) external onlyOwner {
    _mint(to, amount);
}
```

Allows the owner to mint new tokens to a specified address.

### Burn Function

```solidity
function burn(uint256 amount) external {
    _burn(msg.sender, amount);
}
```

Allows any token holder to burn their own tokens.

## Deployment

To deploy the contract, use a tool like Remix, Truffle, or Hardhat. Ensure you have an Ethereum account with sufficient funds to deploy the contract.

## Usage

1. **Minting Tokens**: Only the owner can call the `mint` function to create new tokens.
2. **Burning Tokens**: Any token holder can call the `burn` function to destroy their tokens.

## License

This project is licensed under the MIT License.

