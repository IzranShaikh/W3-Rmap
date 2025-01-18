# ROADMAP - BLOCKCHAIN 🧊🔗🧊🔗🧊🔗🧊🔗🧊

#### Stage I : Introduction
- WEB Evolution
- Decentralization Concept
    - Need
    - Implementation
    - Key Difference
- Blockchain Concept
- Single Block
- Mining Difficulty
    - Proof of Work
    - Proof of Stake
- Popular Blockchains [ETHEREUM, BITCOIN, BSC, SOLANA, etc]
    - Purpose
    - Differences
    - Consensus



<details>
  <summary>Play around with Script</summary>
  Blockchain Theory Example -
  
  ```javascript
const HASH_ALG = require('crypto-js/sha256');

class SingleBlock {
    constructor (time, data, prevHash = '\tGENESIS BLOCK') {
        this.time = time;
        this.data = data;
        this.prevHash = prevHash;
        //Dependencies
        this.hash = this.generateHash();this.nothing = 0;
    }
    generateHash() { return HASH_ALG(this.index + this.prevHash + JSON.stringify(this.data) + this.time + this.nothing).toString() }
    proofOfWork(intensity, prove){
        while (this.hash.substring(0, intensity) != Array(intensity + 1).join(prove)){ this.nothing++; this.hash = this.generateHash(); }
        console.log("Block Added/Mined: ");
        console.log(this) }
}

class Blockchain{
    constructor() { this.chain = [this.initGenesis()]; this.intensity = 5; this.prove = '0' }
    initGenesis() { return new SingleBlock('3:00:01-12/1/2017', "GENESIS"); }
    fetchLatest() { return this.chain[this.chain.length - 1]; }
    blockAdd(newBlock) {
        newBlock.prevHash = this.fetchLatest().hash;
        newBlock.proofOfWork(this.intensity, this.prove);
        this.chain.push(newBlock);
        console.log(this.chainCheck()) }
    chainCheck() {
        for(let i=1; i<this.chain.length; i++){
            const curBlock = this.chain[i];const prevBlock = this.chain[i - 1];
            if(curBlock.hash !== curBlock.generateHash()) { return false; }
            if(curBlock.prevHash != prevBlock.hash) { return false; }
            return true;} }
}

var Catcoin = new Blockchain();
console.log("\n[+] Mining New Block...");
Catcoin.blockAdd(new SingleBlock('7:47:01-12/1/2018',
{ amount: 1000000, sender: "Rohit", reciever: "Joel" }));
console.log("\n[+] Mining New Block...");
Catcoin.blockAdd(new SingleBlock('15:02:00-2/6/2018',
{ kickstart_amount: 5000, sender: ["Google", "META"], reciever: "Walter", project:'VR Game' }));
console.log("\n[+] Mining New Block...");
Catcoin.blockAdd(new SingleBlock('18:00:01-9/5/2019',
{ reward: 'Steam GiftCard : $10', quantity: 200, sender: "Fuzail", reciever: "Izran" }));

// Represent
let ch = Catcoin.chain;
console.log("\n\n\n[>] BLOCKCHAIN:\n\nBlock 0\tGENESIS BLOCK");
for(let i=1; i<ch.length; i++){
    console.log("  ||\t\t\t^^\n  VV\t\t\t|| - "+ch[i].prevHash);
    console.log("Block "+i+" - "+ch[i].hash+"\n"); }


  ```
</details>

<hr />

#### Stage II : Our Buissness
- Smart Contracts
    - Concept
    - Functioning
    - Types
    - Blockchains using them, primarily Ethereum's implementations
- Solidity<a href="https://docs.soliditylang.org/en/latest/introduction-to-smart-contracts.html#simple-smart-contract">🔗</a>
- Study Common Vulnerabilities In-Depth
    - Overflow/Underflow
    - Reentrancy
    - Broken Access Control
    - Uninitialized Variables and Improper Variable Scoping
    - DoS & Gas Exhaustion
    - Oracle Manipulation
    - Buissness Logic Flaws, etc


<details>
  <summary>Audit this sample Smart Contract</summary>

```javascript
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.X;

contract SimpleBank {
    mapping(address => uint256) public balances;

    // Deposit Ether into the contract
    function deposit() public payable {
        balances[msg.sender] += msg.value;
    }

    // Withdraw Ether from the contract
    function withdraw(uint256 _amount) public {
        require(balances[msg.sender] >= _amount, "Insufficient balance");
        (bool success, ) = msg.sender.call{value: _amount}("");
        require(success, "Transfer failed");
        balances[msg.sender] -= _amount;
    }
}
```
</details>

> [!CAUTION]
> Never send Smart Contracts or any Client provided Code to online LLMs

<hr />

#### Stage III : Genesis Testing
- <a href="https://metamask.io/">MetaMask</a> Setup
- Testing Environments
    - LocalNet
    - TestNet
    - MainNet
-  Foundry<a href="https://book.getfoundry.sh/">🔗</a>
-  HardHat Configuration<a href="https://github.com/NomicFoundation/hardhat">🔗</a>
-  Environment Setup
- The Ethernaut<a href="https://ethernaut.openzeppelin.com/">🔗</a>
- Video References
    - https://www.youtube.com/watch?v=fNMfMxGxeag
    - https://www.youtube.com/watch?v=UWy-CcnulCA&t=207s
    - https://youtube.com/playlist?list=PLS5SEs8ZftgUq-aMMYeKf8nPqHrNqa3Iu&si=d0SW8i_swZq16qHF


