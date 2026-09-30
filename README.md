# BlockFind – Blockchain-Based Lost & Found System

A simple, unique, and fully functional college-level blockchain application designed to log, search, claim, and track lost and found items immutably using a Solidity smart contract.

---

## 🌟 Key Features

1. **Register Found Item:** Input Name, Description, and Found Location. The contract auto-assigns an **Item ID** (`itemCount`).
2. **Search by Item ID:** Look up any item using `getItem(uint256 _id)`.
3. **Item Details & Struct Inspection:** View complete details, finder address, status flags (`claimed`, `returned`), and raw Solidity struct layout.
4. **Mark as Claimed:** Claim an item (`claimItem(uint256 _id)`).
5. **Mark as Returned:** Confirm item handover (`returnItem(uint256 _id)`).
6. **Total Items Counter:** Displays real-time `itemCount` stored on the smart contract.
7. **Transaction States:** Visual indicators for loading/mining, transaction hash, block number, success, and error handling.
8. **College Viva & Architecture Guide:** Built-in interactive guide for project presentation and faculty evaluation.

---

## ⚡ Technical Architecture (NO METAMASK)

```
[ Frontend (React + Vite + Tailwind CSS) ]
                   │
                   ▼
       [ Ethers.js (v6) ]
                   │
                   ▼ (JsonRpcProvider)
[ Local Blockchain Node (127.0.0.1:8545) ]
                   │
                   ▼
  [ BlockFind Solidity Smart Contract ]
```

### Why No MetaMask?
- Eliminates dependency on browser extension plugins.
- Bypasses Remix VM external isolation issues.
- Connects directly to local JSON-RPC nodes (`http://127.0.0.1:8545`).
- Pre-loaded Hardhat test signers allow switching between **Finder**, **Claimer**, and **Inspector** accounts directly from the top navigation bar.

---

## 🚀 Quick Start Guide

### Prerequisites
- Node.js (v18 or higher)
- npm

### 1. Install Dependencies
```bash
npm install
```

### 2. Start Local Blockchain Node
Open Terminal 1:
```bash
npx hardhat node
```

### 3. Deploy Smart Contract
Open Terminal 2:
```bash
npm run deploy
```
*(This compiles `BlockFind.sol`, deploys it to `http://127.0.0.1:8545`, and saves the deployed address + ABI to `src/contractConfig.json`)*.

### 4. Launch Application
In Terminal 2 (or Terminal 3):
```bash
npm run dev
```
Open your browser at `http://localhost:3000`.

---

## 🧪 Running Unit Tests

Run full Hardhat smart contract test suite:
```bash
npx hardhat test
```

---

## 📜 Smart Contract Summary (`contracts/BlockFind.sol`)

- **`addItem(string _name, string _description, string _location)`** — Adds a new item record, assigns `itemCount`, logs `msg.sender` as finder.
- **`claimItem(uint256 _id)`** — Sets `claimed = true`.
- **`returnItem(uint256 _id)`** — Sets `returned = true`.
- **`getItem(uint256 _id)`** — Returns `(id, name, description, location, finder, claimed, returned)`.
