# DAO - Twitter + Blockchain protocol

![Solidity](https://img.shields.io/badge/Solidity-0.7.5-363636?logo=solidity&logoColor=white)
![Blockchain](https://img.shields.io/badge/Blockchain-Ethereum-3C3C3D?logo=ethereum)
![Token](https://img.shields.io/badge/Token-DAI-F5AC37)
![Status](https://img.shields.io/badge/Status-Experimental-blueviolet)

Functional **on-chain social coordination protocol** where users stake tokens to publish content and vote on what gets surfaced next.

<p align="center">
  <a href="https://bscscan.com/address/0x18f7B5aB35B2f23Ccb18FA3833E73eAAfA57b400">
    <img src="https://img.shields.io/badge/View-Contract%20on%20BscScan-yellow?logo=binance&logoColor=white" />
  </a>
</p>
<p align="center">
  <a href="https://bscscan.com/address/0x18f7B5aB35B2f23Ccb18FA3833E73eAAfA57b400" target="_blank">
    <img src="https://raw.githubusercontent.com/0xAccount/community-contracts/0ca3acf835368f4294cb3dae0e44431ef6507648/Contract%20BSC.png" width="70%" />
  </a>
</p>


## Core Idea

Users **stake DAI to publish content (tweets)** and the community **votes to decide visibility/priority**.

- Publishing 
- Voting = decentralized  
- Reserves = protocol-level value accumulation  

## 🔄 How It Works

### 1. Publish Content

Users submit a "tweet" by staking DAI:

```solidity
publishTweet(uint amount, string memory content)
```

- Requires sufficient DAI balance
- Transfers tokens into the contract
- Adds to total reserves
- Stores content on-chain

---

### 2. Vote

```solidity
vote(uint tweetId)
```

- One vote per address
- Increments vote count
- Tracks voters to prevent duplicates

---

### 3. Protocol Lifecycle

```solidity
toggleActive()
```

- Enables / disables the system

```solidity
setNextTweet(uint timestamp)
```

- Resets:
  - Votes
  - Voters
  - Tweets
- Starts a new cycle


## Design Insights

Publishing requires capital → reduces spam and aligns incentives.
One vote per address (not perfect, but simple baseline).
All published content increases protocol reserves.
Keeps the system fresh and prevents stale dominance.

## Potential Improvements

- Add reward distribution mechanism
- Integrate quadratic voting
- Add identity layer (ENS / Proof of Humanity)
- Optimize storage with indexing/mappings
- Frontend (React + Web3)
- Off-chain indexing (The Graph)

## License

MIT


## Philosophy

> "Attention is valuable — this protocol makes it stakeable."
> 
If you build on top of this, feel free to fork, extend, and experiment.
