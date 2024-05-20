# MySchoolToken(Smart Contract)
This Solidity smart contract creates a custom ERC20 token called MyToken. The contract owner has the ability
to mint tokens to any provided address, while any user can burn and transfer tokens.

## Description
Good day, Im here again for another poroject assessment in Metacrafters. This is my code and we will explore now about ERC20 
Smart Contract and type of functions

## Getting Started
// SPDX-License-Identifier: MIT pragma solidity ^0.8.0;

/*REQUIREMENTS: For this project,Create and Mint Token. write a smart contract to create your own ERC20 token and deploy it using Remix.
From your chosen tool, the contract owner should be able to mint tokens to a provided address and any user should 
be able to burn and transfer tokens.

// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract MyToken is ERC20 {
    address private _owner;

    constructor(string memory name, string memory symbol, uint256 initialSupply) ERC20(name, symbol) {
        _mint(msg.sender, initialSupply);
        _owner = msg.sender;
    }
    modifier onlyOwner() {
        require(msg.sender == _owner, "Only owner can call this function");
        _;
    }

    function mint(address account, uint256 amount) public onlyOwner {
        _mint(account, amount);
    }

    function burn(uint256 amount) public {
        _burn(msg.sender, amount);
    }

    
    function transfer(address recipient, uint256 amount) public override returns (bool) {
        require(recipient != address(0), "ERC20: transfer to the zero address");
        _transfer(_msgSender(), recipient, amount);
        return true;
    }

   
    function transferFrom(address sender, address recipient, uint256 amount) public override returns (bool) {
        require(recipient != address(0), "ERC20: transfer to the zero address");
        _transfer(sender, recipient, amount);
        _approve(sender, _msgSender(), allowance(sender, _msgSender()) - amount);
        return true;
    }
}
    
        
## Executing Program
To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/. 
Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension 
(e.g., HelloWorld.sol). Then copy the code given in the assessment.

## Author
Marc Danniel Mariazeta 61902476@ntc.edu.ph


