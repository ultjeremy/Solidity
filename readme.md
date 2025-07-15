# Blockchain Use Case Research

In this GitHub project, I am exploring various well-known and real-world tokens and their use cases. This project focuses on their technical integration and includes some code snippet examples throughout.

## Binance (BNB):

Binance utilizes smart contracts with their BNB Smart Chain to facilitate the building of dApps to allow developers to create projects taking advantage of the benefits that the BNB token provides. The BNB Smart Chain utilizes the BEP-20 token standard, which is very similar to the ERC-20 standard. The standard acts like a guide and blueprint for how to utilize the BEP-20 standard.

BNB transactions largely operate with on-chain logic, where transactions are recorded on the BNB chain and executed by smart contracts directly on the chain. This follows from the fact that BNB is the native currency on the Binance Exchange, powering transactions and paying for fees.

BNB can be interacted with through smart contracts that allow many transactions to occur, providing many benefits to users. I coded a small example of a smart contract through Solidity of transfering tokens, which can be used for transfering BNB, Ether, and more across accounts. 

```
// SPDX-License-Identifier: GPL-3.0
pragma solidity >=0.7.0 <0.9.0;

contract tokenSend {

    // Create event that listens for the transferring of currency
    event CurrencySent(address sender, address receiver, uint amount);

    // Sender does not have enough currency to send amount
    error NotEnoughCurrency(uint amount);
    
    // Function that transferes payment from the caller to a receiver
    function sendToken(address payable receiver) external payable {
        
        // Ensure that the sender sends more than nothing
        require(msg.value > 0, "You have to send something.");

        // Make sure the transfer successfully went through
        (bool success, ) = receiver.call{value: msg.value}("");
        require(success, "Transfer failed.");

        // Log the transfer
        emit CurrencySent(msg.sender, receiver, msg.value);

        }
}
```
