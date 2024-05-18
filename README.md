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

contract MyschoolToken {
    string public username;
    string public course;
    uint8 public decimals;
    uint256 public totalValue;

    mapping(address => uint256) public balanceOf;
    mapping(address => mapping(address => uint256)) public allowance;

    address private owner;

    event Transfer(address indexed from, address indexed to, uint256 value);
    event Approval(address indexed owner, address indexed spender, uint256 value);

    constructor(string memory _username, string memory _course, uint8 _decimals, uint256 _initialSupply) {
        username = _username;
        course = _course;
        decimals = _decimals;
        totalValue = _initialSupply * 10 ** uint256(decimals);
        balanceOf[msg.sender] = totalValue;
        owner = msg.sender;
        emit Transfer(address(0), msg.sender, totalValue);
    }

    modifier onlyOwner() {
        require(msg.sender == owner, "Only owner can call this function");
        _;
    }

    function transfer(address _to, uint256 _value) public returns (bool success) {
        require(_to != address(0), "ERC20: transfer to the zero address");
        require(balanceOf[msg.sender] >= _value, "ERC20: insufficient balance");
        
        balanceOf[msg.sender] -= _value;
        balanceOf[_to] += _value;
        emit Transfer(msg.sender, _to, _value);
        return true;
    }

    function approve(address _spender, uint256 _value) public returns (bool success) {
        allowance[msg.sender][_spender] = _value;
        emit Approval(msg.sender, _spender, _value);
        return true;
    }

    function transferFrom(address _from, address _to, uint256 _value) public returns (bool success) {
        require(_to != address(0), "ERC20: transfer to the zero address");
        require(balanceOf[_from] >= _value, "ERC20: insufficient balance");
        require(allowance[_from][msg.sender] >= _value, "ERC20: allowance exceeded");

        balanceOf[_from] -= _value;
        balanceOf[_to] += _value;
        allowance[_from][msg.sender] -= _value;
        emit Transfer(_from, _to, _value);
        return true;
    }

    function mint(address _to, uint256 _value) public onlyOwner returns (bool success) {
        totalValue += _value;
        balanceOf[_to] += _value;
        emit Transfer(address(0), _to, _value);
        return true;
    }

    function burn(uint256 _value) public returns (bool success) {
        require(balanceOf[msg.sender] >= _value, "ERC20: insufficient balance");

        balanceOf[msg.sender] -= _value;
        totalValue -= _value;
        emit Transfer(msg.sender, address(0), _value);
        return true;
    }
}

## Executing Program
To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/. 
Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension 
(e.g., HelloWorld.sol). Then copy the code given in the assessment.

## Author
Marc Danniel Mariazeta 61902476@ntc.edu.ph


