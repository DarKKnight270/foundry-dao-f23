# 🗳️ DAO Governance with Timelock and Voting – Foundry + OpenZeppelin

This project implements a complete **on-chain governance system** using Solidity, OpenZeppelin's modular Governor contracts, and the Foundry framework for testing.

## ⚙️ Stack

- **Solidity** `^0.8.20`
- **Foundry** for testing and scripting
- **OpenZeppelin Contracts v5.x**
- **Governor**, **TimelockController**, **ERC20Votes**, and **AccessControl**
- Full DAO voting cycle: propose → vote → queue → execute

## 🧠 Features

- ERC20-based token with **voting checkpoints**
- **Gasless signature-based approvals** using `ERC20Permit`
- **Governor contract** with:
  - Configurable voting delay, period, and threshold
  - Quorum as a % of total supply
  - Voting with reason support
- **TimelockController** enforcing execution delay and role-based control
- Target contract (`Box`) whose ownership is transferred to the Timelock
- Full test that simulates the DAO lifecycle

---

## 🔬 Test Flow (`MyGovernorTest.t.sol`)

- Deploys the `GovToken`, `TimelockController`, and `MyGovernor`
- Transfers ownership of `Box` contract to the Timelock
- Simulates a DAO proposal:
  1. **Propose** `store(3)` in `Box`
  2. **Advance block/time to start voting**
  3. **Vote with reason**
  4. **Advance to end of voting**
  5. **Queue proposal in Timelock**
  6. **Advance past Timelock delay**
  7. **Execute** the proposal
- Asserts that `Box` now contains the correct stored value.

---

## 🚀 Running the Tests

Install Foundry and run:

```bash
forge install
forge test -vv

This repository is maintained by DarKKnight270.
Built as part of a learning project on DAO architecture and governance logic.