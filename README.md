// SPDX-License-Identifier: MIT
pragma solidity 0.8.9;

contract MyToken {

    // Public variables to store the details about the token
    string public tokenName = "MyToken";
    string public tokenSymbol = "MTK";
    uint256 public totalSupply;

    // Mapping from addresses to balances
    mapping(address => uint256) public balances;

    // Mint function to create new tokens
    function mint(address account, uint256 amount) public {
        totalSupply += amount;         // Increase the total supply by the minted amount
        balances[account] += amount;   // Increase the balance of the recipient
    }

    // Burn function to destroy tokens
    function burn(address account, uint256 amount) public {
        require(balances[account] >= amount, "Insufficient balance to burn"); // Ensure the account has enough balance
        totalSupply -= amount;         // Decrease the total supply by the burned amount
        balances[account] -= amount;   // Decrease the balance of the account
    }
}
