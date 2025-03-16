# Commons Stablecoin Format (CSF) v1.4.1

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)  
[![Version](https://img.shields.io/badge/version-1.4.1-orange.svg)](https://github.com/Brale-xyz/commons)  

## 📌 Overview
The **Commons Stablecoin Format (CSF)** is a standardized framework for **documenting and validating funds flows in stablecoin and blockchain-based payment systems**. It ensures the **correct handling of transaction types, compliance, error handling, exchange processing, and settlement finality** across **both on-chain and off-chain financial rails**.

This repository provides:
- **CSF Specification (JSON Format)**
- **ValueType & TransferType Definitions**
- **Supporting Files for Stablecoin Network Mappings**
- **Example Funds Flows Using CSF**

## 📁 Repository Structure
/CSF.json                      # CSF Parent Framework
/ValueTypes.json                # Stablecoins & Fiat Currencies (ValueTypes)
/TransferTypes.json             # Transfer Methods (On-Chain & Off-Chain)
/StablecoinDetails/             # Blockchain Contract Details for Stablecoins
├── USDC.json               # USDC Smart Contract Addresses
├── USDT.json               # USDT Smart Contract Addresses
├── EUROC.json              # EUROC Smart Contract Addresses
├── GBPT.json               # GBPT Smart Contract Addresses