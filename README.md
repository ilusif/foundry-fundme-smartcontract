# FundMe – Foundry Practice Project

This repository contains **FundMe**, a learning-focused smart contract project built while following the **Foundry Fundamentals** course. The goal of this repo is to practice professional Solidity development workflows using **Foundry**, including testing, scripting, mocking, and deployment patterns that are directly applicable to real-world DeFi protocols.

> This project is intentionally educational. It prioritizes correctness, clarity, and tooling familiarity over production features.

---

## 📌 Project Overview

The **FundMe** contract allows users to:

* Send ETH to the contract (funding)
* Enforce a minimum USD value using a Chainlink price feed
* Track how much each address has funded
* Allow only the owner to withdraw all funds

It demonstrates:

* Price feed integration via `AggregatorV3Interface`
* Mocking Chainlink feeds for local testing
* Foundry-style unit tests
* Scripted deployments with environment-aware configuration

---

## 🧱 Tech Stack

* **Solidity** ^0.8.x
* **Foundry** (forge, cast, anvil)
* **Chainlink** Price Feeds (real + mock)
* **Polygon / Sepolia compatible**

---

## 📂 Repository Structure

```text

├── src/
│   ├── FundMe.sol
│   └── PriceConverter.sol
│
├── script/
│   ├── DeployFundMe.s.sol
│   ├── HelperConfig.s.sol
│   └── Interactions.s.sol
│
├── test/
│   ├── unit/
│   │   └── FundMeTest.t.sol
│   │
│   ├── FundMeTestIntegration.t.sol
│   │
│   └── mocks/
│       └── MockV3Aggregator.sol
│
├── lib/
├── foundry.toml
└── README.md
```

---

## 🔗 Price Feeds & Network Behavior

This project supports **multiple environments**:

### Local / Anvil

* Uses `MockV3Aggregator`
* No real ETH or MATIC required
* Fully deterministic testing

### Testnets (e.g. Sepolia)

* Uses real Chainlink price feeds
* Requires test ETH

### Forked Networks (Polygon Fork)

* Uses **Chainlink contracts**
* No real funds required
* Closest representation of mainnet behavior

> Forked testing is the recommended workflow for DeFi development.

---

## 🧪 Running Tests

```bash
forge test
```

Verbose output:

```bash
forge test -vvvv
```

Run tests against a fork (example: Polygon):

```bash
forge test --fork-url <YOUR_RPC_URL>
```

---

## 🚀 Deployment

### Local (Anvil)

```bash
anvil
forge script script/DeployFundMe.s.sol --rpc-url http://localhost:8545 --broadcast
```

### Testnet

```bash
forge script script/DeployFundMe.s.sol \
  --rpc-url <SEPOLIA_RPC_URL> \
  --private-key <PRIVATE_KEY> \
  --broadcast
```

---

## 🔐 Environment Variables

Create a `.env` file (not committed):

```env
PRIVATE_KEY=your_private_key
RPC_URL=your_rpc_url
```

> **Never commit private keys.**

---

## 🎯 Learning Objectives

By completing this project, you should be comfortable with:

* Writing Solidity contracts with external dependencies
* Using libraries and immutable variables
* Writing Foundry tests with mocks and cheats
* Debugging common EVM and Foundry errors
* Understanding environment-specific behavior (local vs testnet vs fork)

This project serves as **foundational preparation** for more advanced DeFi work such as:

* Aave V3 flash loans
* Liquidation bots
* Protocol integrations on Polygon

---

## ⚠️ Disclaimer

This code is for **educational purposes only**.
It has **not** been audited and should not be used in production.

---

## 📚 References

* Foundry Book
* Chainlink Documentation
* Aave V3 Documentation
* Cyfrin / Patrick Collins – Foundry Fundamentals

---

## 🧠 Author Notes

This repository reflects the reality of learning smart contract development:

* Course materials may evolve
* Patterns may change across lessons
* Understanding *why* things work matters more than copying code

If you understand the deployment flow, testing strategy, and error resolution — this repo has done its job.
