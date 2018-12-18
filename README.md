# ethereum-intro

- Intro - What's Ethereum?
- App #1 - Interacting with Ethereum
- App #2 - Tooling, Deployment, and Testing of Ethereum applications
- App #3 - Multi-page Dapp on Ethereum

Introduction
=============

### [Custom containers](https://github.com/markdown-it/markdown-it-container)

::: warning
*here be dragons*
:::

#### History 
---
Oct 31st, 2008 Bitcoin Whitepaper
"Bitcoin: A Peer-to-Peer Electronic Cash System"

Dec, 2013 Ethereum Whitepaper
"Ethereum: The Ultimate Smart Contract and Decentralized Application Platform"

#### What's Ethereum?
---

- N/W of nodes
- It's used to transfer money and store data
- Anyone can download an Ethereum client and run a node
- Each node has a complete copy of the blockchain

#### Interfacing with Ethereum
---

- For Developers: web3.js
- For Consumers: Metamask or Mist Browser

#### Metamask Setup
---

- Go to Chrome Webstore and install the Metmask plugin
- Create a username and password
- Copy your 12-word mnemonic 

#### Metamask N/Ws
---

- Main
- Ropsten
- Kovan
- Rinkeby
- localhost
- Custom RPC

#### Ethereum Accounts
---

- Your account consists of your account address, your public key, and your private key
- Account address is like your email address
- Public and private keys together form your password
- These are hex numbers, once converted to base10 => 8 x 10^79 (incomprehensibly large, cannot be guessed)

#### Getting 'free' ether on Rinkeby
---

- Go to faucet.rinkeby.io and follow the steps
- Ether has real value only on the main network
- Receiving ether takes a certain amount of time (around 15 to 20 seconds)

#### Transaction Objects
---

- Your account address is sent to a backend node.js server
- The server uses web3.js to create a transaction object
- The transaction object consists of:
  - nonce
  - to 
  - value
  - gasprice
  - gasLimit (startGas)
  - v
  - r
  - s
  
#### Reason for the 15 sec delay for transaction to complete
---

- The transaction object is sent to one node on the Ethereum N/W
- The node combines all transactions received at the same time into a list
- The node then runs some 'validation logic' (mining) which causes the delay

#### Block
---

- Data is represented by a Hash
- Hash is a digital fingerprint of the data
- It's calculated by the proof-of-work algorithm
- Block consists of:
  - Block Number
  - Nonce
  - Data
  - Prev
  - Hash
  - MINE (readjusts the nonce to calculate a specfic hash)
  
#### Blockchain
---
  
- Series of blocks, each connected to the previous
- "Previous hash" is the hash of the previous block
- If you need to change the data in one block, you would have to mine all subsequent blocks
- This is how a blockchain resists change

#### Distributed Blockchain
---

- Peer A: Block 1 -> Block 2 ...
- Peer B: Block 1 -> Block 2 ...
- For a change to be propagated it needs to be accepted by majority of the peers

#### Blocktime
---

- You're looking for a hash less than some number, for example, 1000
- Data + Nonce = Hash -> Base10 is this < 1000, if no, decrease 1000 to maintain blocktime at 15s
- We need to vary 1000 because the number of nodes in the blockchain is always in flux

#### Smart Contract
---
 
 - Is an account controlled by code:
   - balance - Amount of ether this account holds
   - storage - Data store for this account
   - code - Raw machine byte code for this contract
  
#### Deploying a Smart Contract to Ethereum
---

- Contract source is written on your laptop
- This contract is deployed as a 'contract instance' to the Ethereum N/W

#### Solidity Programming Language
---

- Written as .sol files
- Strongly typed
- Similar to Javascript

#### Solidity Compiler
---

- A contract is compiled by the Solidity compiler into Bytecode and ABI (application binary interface)
- Bytecode is deployed into Ethereum 
- ABI is used for interfacing with a front-end application

#### Remix Code Editor
---

- Browser code editor used for testing smart contracts
- A sample contract is as follows:

      pragma solidity ^0.4.17
      
      //Version of the compiler
      //Contract will be valid for newer versions of Solidity
      
      contract Inbox {
      
      //Contract definition
      //Similar to class definition
      
          string public message;
          
      //string is the datatype
      //public means the variable can be called by anyone
      //message is the name of the storage variable
      //The value of message is stored on the blockchain
      
          function Inbox(string initialMessage) public {
          
      //Inbox is a constructor function
      //Contructor function is automatically called when the contract is deployed
      //public means that the function can be called by anyone
      //Function Types: public, private (only the contract can call this function), view (returns data but does not modify),
      //pure (does not return or modify data), payable (send some ether along)
      
              message = initialMessage;
          }
          function setMessage(string newMessage) public {
              message = newMessage;
          }
      }

#### Testing with Remix
---

- Remix hosts an Ethereum N/W to simulate running the contract
- Click "Create (string initialMessage)", after adding any initial message 
- Once created, click message to retrieve that initial message 
- Click "setMessage (string setMessage)", after adding a new message
- Once created, click message to retrieve the new message

#### Behind the scenes deployment
---

- The contract creates a transaction object with the following info:
 - nonce - Number of times a sender has sent a transction
 - to - Always blank for a contract
 - data - Bytecode
 - gasPrice - Amount of ether per transaction
 - startGas - Units of Gas
 - v, r, s - Cryptographic elements - Creates public and private keys from your Account address, the reverse is not possible
 
 #### More on Functions
 ---
 
 - Whenever we want to modify any data on the N/W, a trans object is sent, which needs to be approved (mining)
 - Calling a function - Get operation, free, instantaneous
 - Sending a transction to a function - Modify operation, costs ether, slow
 
#### Wei v/s Ether
---

  - Wei is the smallest unit of currency
  - 1 Eth = 1,000,000,000,000,000,000 Wei
  - No fractional unit of Wei

#### Gas and Transactions
---

 - Different operations have different gas costs
 - gasPrice - Amount of Wei per unit of gas
 - startGas - Total amount of Wei you are willing to spend (safety net)
 
#### Menomonic Phrase
---

 - 12-word phrase that allows you to generate the pub and priv key
 - 12-word menomonic -> BIP39 Algo -> Account address (Pub key and Priv key)








