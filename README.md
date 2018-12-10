# ethereum-intro
Introduction to Ethereum
=========================

Intro - What's Ethereum?
App #1 - Interacting with Ethereum
App #2 - Tooling, Deployment, and Testing of Ethereum applications
App #3 - Multi-page Dapp on Ethereum

Intro
=====

History 
-------

Oct 31st, 2008 Bitcoin Whitepaper
"Bitcoin: A Peer-to-Peer Electronic Cash System"

Dec, 2013 Ethereum Whitepaper
"Ethereum: The Ultimate Smart Contract and Decentralized Application Platform"

What's Ethereum

- N/W of nodes
- It's used to transfer money and store data
- Anyone can download an Ethereum client and run a node
- Each node has a complete copy of the blockchain

Interfacing with Ethereum

- For Developers: web3.js
- For Consumers: Metamask or Mist Browser

MetaMask Setup

- Go to Chrome Webstore and install the Metmask plugin
- Create a username and password
- Copy your 12-word mnemonic 

Metamask N/Ws

- Main
- Ropsten
- Kovan
- Rinkeby
- localhost
- Custom RPC

Ethereum Accounts

- Your account consists of your account address, your public key, and your private key
- Account address is like your email address
- Public and Private keys together form your password
- These are hex numbers, once converted to base10 => x 10^79 (incomprehensibly large, cannot be guessed)

Getting 'free' ether on Rinkeby

- Go to faucet.rinkeby.io and follow the steps
- Ether has real value only on the main network
- Receiving ether takes a certain amount of time (around 15 to 20 seconds)

Transaction Object

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
  
Reason for the 15 sec delay for transaction to complete

- The transaction object is sent to one node on the Ethereum N/W
- The node combines all transaction received at the same time into a list
- The node then runs some 'validation logic' (mining) which causes the delay

Block

- Data is represented by a Hash
- Hash in a digital fingerprint of the data
- It's calculated by the proof-of-work alogorithm
- Block consists of:
  - Block Number
  - Nonce
  - Data
  - Prev
  - Hash
  - MINE (readjusts the nonce to calculate a specfic hash)
  
Blockchain
  
- Series of blocks connected in series
- Previous hash is the hash of the previous block
- If you need to change the data in one block, you would have to mine all subsequent blocks
- That's how a blockchain resists change

Distributed Blockchain

- Peer A: Block 1 -> Block 2 ...
- Peer B: Block 1 -> Block 2 ...
- For a change to be propagated it needs to be accepted by majority of the peers









