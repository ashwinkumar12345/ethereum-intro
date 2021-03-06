# ethereum-intro

> ## Contents

**[History](#history)**<br>
**[What's Ethereum?](#whatsethereum)**<br>
**[Interfacing with Ethereum](#interfacing)**<br>
**[Metamask setup](#metamasksetup)**<br>
**[Ethereum networks](#ethereumnet)**<br>
**[Ethereum accounts](#ethereumacc)**<br>
**[Getting 'free' ether on rinkeby](#freeether)**<br>
**[Transaction objects](#trans-object)**<br>
**[Reason for the 15 sec delay for transaction to complete](#delay)**<br>
**[Block](#block)**<br>
**[Blockchain](#blockchain)**<br>
**[Distributed Blockchain](#distributedblockchain)**<br>
**[Blocktime](#blocktime)**<br>
**[Smart contract](#smartcontract)**<br>
**[Deploying a smart contract to Ethereum](#deployingasmartcontract)**<br>
**[Solidity (programming language)](#solidityprogramminglanguage)**<br>
**[Solidity compiler](#soliditycompiler)**<br>
**[Remix code editor](#remixcodeeditor)**<br>
**[Testing with remix](#remix)**<br>
**[Behind-the-Scenes deployment](#behind-the-scenes-deployment)**<br>
**[More on functions](#moreonfunctions)**<br>
**[Wei v/s Ether](#wei)**<br>
**[Gas and transactions](#gasandtransactions)**<br>
**[Mneomonic phrase](#mneomonic)**<br>

<a name="history"></a>
> ## History 
Oct 31st, 2008 Bitcoin Whitepaper
"Bitcoin: A Peer-to-Peer Electronic Cash System" 
(https://bitcoin.org/bitcoin.pdf)

Dec, 2013 Ethereum Whitepaper
"Ethereum: The Ultimate Smart Contract and Decentralized Application Platform" (http://web.archive.org/web/20131228111141/http://vbuterin.com/ethereum.html)

<a name="whatsethereum"></a>
> ## What's Ethereum?

- Network of nodes (computers):

![intro-1](https://user-images.githubusercontent.com/4720428/50610712-cf6ed880-0e88-11e9-9344-03a3f4aaa84f.png)

It's used to transfer money and store data. Anyone can download an Ethereum client and run a node. Each node has a complete copy of the blockchain.

<a name="interfacing"></a>
> ## Interfacing with Ethereum

- For Developers: web3.js
- For Consumers: Metamask (chrome extension) or Mist Browser

![intro-2](https://user-images.githubusercontent.com/4720428/50611167-4f497280-0e8a-11e9-8180-dac65c2a1bdf.png)

<a name="metamasksetup"></a>
> ## Metamask Setup

- Go to Chrome Webstore and install the Metmask plugin.
- Create a username and password.
- Copy your 12-word mnemonic.

<a name="ethereumnet"></a>
> ## Ethereum networks

Main (productions apps and where ether has value)
Ropsten
Kovan
Rinkeby
localhost
Custom RPC

<a name="ethereumacc"></a>
> ## Ethereum Accounts

Your account consists of your account address, your public key, and your private key. Account address is similar to your email address. 

Public and private keys together form your password. These are hex numbers, once converted to base10 => 8 x 10^79 (incomprehensibly large, cannot be guessed)

![intro-3](https://user-images.githubusercontent.com/4720428/50611521-9e43d780-0e8b-11e9-8280-74d39ab688d2.png)

<a name="freeether"></a>
> ## Getting 'Free' ether on rinkeby

Go to `faucet.rinkeby.io` and follow the steps. 
Ether has real value only on the main network. Receiving ether takes a certain amount of time (around 15 to 20 seconds).

<a name="trans-object"></a>
> ## Transaction Objects

Your account address is sent to a backend node.js server. The server uses web3.js to create a transaction object.
The transaction object consists of:

 - nonce
 - to 
 - value
 - gasprice
 - gasLimit (startGas)
 - v
 - r
 - s

<a name="delay"></a>
> ## Reason for the 15 sec delay for transaction to complete

The transaction object is sent to one node on the Ethereum network. The node combines all transactions received at the same time into a list. The node then runs some 'validation logic' (mining) which causes the delay as the result needs to be propagated across all the nodes.

<a name="block"></a>
> ## Block

Data is represented by a Hash. Hash is a digital fingerprint of the data. It's calculated by the proof-of-work algorithm.

Block consists of:

  - Block Number
  - Nonce
  - Data
  - Prev
  - Hash
  - MINE (readjusts the nonce to calculate a specfic hash)
 
<a name="blockchain"></a>
> ## Blockchain
  
Series of blocks, each connected to the previous. 'Previous hash' is the hash of the previous block. If you need to change the data in one block, you would have to mine all subsequent blocks. This is how a blockchain resists change.

<a name="distributedblockchain"></a>
> ## Distributed Blockchain

For a change to be propagated it needs to be accepted by the majority of the peers.

- Peer A: Block 1 -> Block 2 ...
- Peer B: Block 1 -> Block 2 ...

<a name="blocktime"></a>
> ## Blocktime

You're looking for a hash less than some number, for example, 1000.
Data + Nonce = Hash -> Base10 is this < 1000, if no, decrease 1000 to maintain blocktime at 15s.
We need to vary 1000 because the number of nodes in the blockchain is always in flux.

<a name="smartcontract"></a>
> ## Smart Contract
 
It's an account controlled by code:

 - balance - Amount of ether this account holds
 - storage - Actual data stored in this account
 - code - Raw machine byte code for this contract

<a name="deployingasmartcontract"></a>
> ## Deploying a smart contract to Ethereum

The contract source is written on your laptop. This contract is then deployed as a 'contract instance' to the Ethereum network.

<a name="solidityprogramminglanguage"></a>
> ## Solidity (programming language)

It's written as `.sol` files. It's a strongly typed language, similar to Javascript. 

<a name="soliditycompiler"></a>
> ## Solidity compiler

A contract is compiled by the Solidity compiler into bytecode and ABI (application binary interface).
The bytecode is deployed into Ethereum. 
ABI is used for interfacing with a front-end application.

<a name="remixcodeeditor"></a>
> ## Remix code editor

It's a browser code editor used for testing smart contracts.
A sample contract is as follows:

      pragma solidity ^0.4.17
     
      //Version of the compiler
      //Contract will be valid for newer versions of Solidity
      
      contract Inbox {
      
      //Contract definition
      //Similar to class definition
      
          string public message;
          
      //string is the datatype
      //public means that the variable can be called by anyone
      //message is the name of the storage variable
      //The value of message is stored on the blockchain
      
          function Inbox(string initialMessage) public {
          
      //Inbox is a constructor function
      //Contructor function is automatically called when the contract is deployed
      //public means that the function can be called by anyone
      //Function types: public, private (only the contract can call this function), view (returns data but does not modify),
      //pure (does not return or modify data), payable (sends some ether along)
      
              message = initialMessage;
          }
          function setMessage(string newMessage) public {
              message = newMessage;
          }
      }

<a name="remix"></a>
> ## Testing with remix

Remix hosts an Ethereum network to simulate running the contract.

- Click `Create (string initialMessage)`, after adding any initial message. 
- Once created, click `message` to retrieve that initial message. 
- Click `setMessage (string setMessage)`, after adding a new message.
- Once created, click `message` to retrieve the new message.

<a name="behind-the-scenes-deployment"></a>
> ## Behind-the-Scenes deployment

The contract creates a transaction object with the following info:

 - nonce - Number of times the sender has sent a transction
 - to - Always blank for a contract
 - data - Bytecode
 - gasPrice - Amount of ether per transaction
 - startGas - Units of Gas
 - v, r, s - Cryptographic elements - creates public and private keys from your account address, the reverse is not possible

<a name="moreonfunctions"></a>
> ## More on Functions
 
Whenever we want to modify any data on the network, a transaction object is sent, which needs to be approved (mining).

- Calling a function - Get operation, free, instantaneous
- Sending a transction to a function - Modify operation, costs ether, slow

<a name="wei"></a>
> ## Wei v/s Ether

Wei is the smallest unit of currency.
1 Eth = 1,000,000,000,000,000,000 Wei.
There is no fractional unit of Wei.

<a name="gasandtransactions"></a>
> ## Gas and Transactions

Different operations have different gas costs:

 - gasPrice - Amount of Wei per unit of gas.
 - startGas - Total amount of Wei you are willing to spend (safety net).

<a name="mneomonic"></a>
> ## Mneomonic Phrase

12-word phrase that allows you to generate the pub and priv key
12-word menomonic -> BIP39 Algo -> Account address (Pub key and Priv key)








