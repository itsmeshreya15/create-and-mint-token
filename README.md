Hello World
ShreyaToken This Solidity program is an ERC-20 token contract named "ShreyaToken". It demonstrates the basic functionality of the ERC-20 token standard, including minting, transferring, and burning 
tokens. This program is designed for those who are new to Solidity and ERC-20 token development on the Ethereum blockchain.

Description
The ShreyaToken contract is a smart contract written in Solidity for the Ethereum blockchain. It implements an ERC-20 token with the following features:

Minting Tokens: Upon deployment, 100 SHK tokens are minted to the contract's address. Token Transfer: The admin can transfer tokens from the contract's address to a recipient. 
Token Burning: Any user can burn their tokens, reducing the total supply. This contract demonstrates the use of OpenZeppelin's ERC-20 implementation, providing a secure and standard way to create
tokens. It can serve as a foundation for more complex projects.

Getting Started
Executing program
To run this program, you will need to use Remix, an online Solidity IDE. Follow these steps to get started:

Visit Remix: Go to https://remix.ethereum.org/. Create a New File: Click on the "+" icon in the left-hand sidebar to create a new file. Save the File: Save the file with a .sol extension 
(e.g., ShreyaToken.sol). Copy and Paste Code: Copy and paste the following code into the new file:
// SPDX-License-Identifier: MIT

//For this project, you will write a smart contract to create your own ERC20 token 
//and deploy it using HardHat or Remix. Once deployed, you should be able to interact 
//with it for your walk-through video. From your chosen tool, the contract owner should 
//be able to mint tokens to a provided address and any user should be able to burn
// and transfer tokens.

pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

contract MyToken is ERC20 {
 constructor() ERC20("Shreya Kandpal","SHK") {
     _mint(msg.sender, 1000 * 10**18);  // Mint 1000 tokens to the contract deployer
 }

 // Function to mint new tokens, callable only by the owner
     function mint(address to, uint256 amount) public  {
     _mint(to, amount);
 }

 // Override transfer function to include a balance check
 function transfer(address recipient, uint256 amount) public override returns (bool) {
     require(balanceOf(msg.sender) >= amount, "Insufficient funds to transfer");
     _transfer(msg.sender, recipient, amount);
     return true;
 }

 function sendFunds(address , uint _amount) public payable{
     require(balanceOf(msg.sender)> _amount, "unsufficient funds to transfer");
 }

 function burn(uint256 amount) public {
     _burn(msg.sender, amount);
 }
}
  


To run the program, follow these steps:

Compile the Code:

Click on the "Solidity Compiler" tab in the left-hand sidebar. Ensure the "Compiler" option is set to a compatible version, such as "0.8.0". Click on the "Compile ShreyaToken.sol" button.
Deploy the Contract:
Click on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "ShreyaToken" contract from the dropdown menu. Click on the "Deploy" button. Interact with the Contract:

Minting Tokens: Upon deployment, 100 SHK tokens are minted to the contract address. 
Creating Tokens: Call the createTokens function with the recipient address and quantity to transfer tokens from the contract address to the recipient. 
This can only be done by the admin. Destroying Tokens: Call the destroyTokens function with the amount to burn tokens from the caller's address.

Authors
Shreya 
shreyakandpal17@gmail.com

License
This project is licensed under the MIT License - see the LICENSE.md file for details
