### Load the CSF Framework

The CSF.json file serves as the parent configuration, referencing ValueTypes and TransferTypes.

### Validate a Funds Flow

Use the CSF structure to ensure a transaction is valid.

Example: USD to USDC conversion  
- Allowed: USD (ACH) → USD (Wire) → USDC (Ethereum)  
- Not Allowed: USD (ACH) → USDC (ACH)  

### Extend the Framework

- To add a new stablecoin, update ValueTypes.json and include a new StablecoinDetails file.
- To define a new transfer type, update TransferTypes.json.

## CSF Specification

The CSF v1.4.1 specification defines:
- Diagram complexity levels
- Required participants in funds flows
- ValueType and TransferType mappings
- Validation rules for transactions
- Exchange processing rules

For details, refer to [CSF.json](CSF.json).

## Resources

### ValueTypes (Currencies)

- Fiat Currencies: USD, EUR, GBP, CAD, JPY, CHF, RUB
- Stablecoins: SBC, USDGLO, CFUSD, MXNE, USDC, USDT, EUROC, GBPT
- Mapped to allowed TransferTypes

### TransferTypes (Methods of Transfer)

- Off-Chain: ACH, Wire, SWIFT, SEPA, FasterPayments, Interac
- On-Chain: Ethereum, Solana, Avalanche, Polygon, Tron, Arbitrum, Base
- Mapped to allowed ValueTypes

### Stablecoin Smart Contracts

- Blockchain addresses stored in StablecoinDetails/

## Example Funds Flow

Example USD to USDC conversion using CSF syntax:

```mermaid
sequenceDiagram
    title USD to USDC Funds Flow (CSF v1.4.1)
    participant EndUser as End User
    participant PaymentPlatform as Payment Platform
    participant ExchangePlatform as Exchange Platform
    participant Blockchain as Ethereum Network
    participant UserWallet as User Crypto Wallet

    %% Step 1: USD Deposit
    EndUser->>PaymentPlatform: [OFFCHAIN] Transfer USD via ACH
    PaymentPlatform->>ExchangePlatform: [OFFCHAIN] Transfer USD via Wire

    %% Step 2: Exchange USD to USDC
    ExchangePlatform->>ExchangePlatform: [EXCHANGE] Convert USD to USDC
    ExchangePlatform->>Blockchain: [ONCHAIN] Transfer USDC on Ethereum
    Blockchain->>UserWallet: [ONCHAIN] Confirm USDC Transfer
