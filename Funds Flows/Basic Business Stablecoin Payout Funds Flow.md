```mermaid
sequenceDiagram
    title Light: Business Payment Flow with On-Chain and Fiat Payout (CSF v1.4.2)

    participant Business as Business (Sender)
    participant FinTechPlatform as Fintech Platform
    participant FinancialSettlementPlatform as Brale (Exchange, Financial & Settlement Platform)
    participant BlockchainNetwork as Blockchain Network
    participant Receiver as Receiver
    participant ReceiverBank as Receiver's Bank Account

    %% Wallet Creation Process
    Business-->>FinTechPlatform: [DATA] Request Wallet for Payouts
    FinTechPlatform-->>FinancialSettlementPlatform: [DATA] Request Wallet Creation
    FinancialSettlementPlatform-->>FinTechPlatform: [DATA] Return Wallet Address
    FinTechPlatform-->>Business: [DATA] Deliver Wallet Address

    %% Transaction Submission to Blockchain
    Business-->>BlockchainNetwork: [DATA] Submit On-Chain Transaction for Processing
    BlockchainNetwork-->>Business: [DATA] Confirm Execution
    BlockchainNetwork-->>FinancialSettlementPlatform: [DATA] Transaction Finalized & Confirmed

    %% Funds Transfer to Brale (Executed On-Chain)
    Business->>FinancialSettlementPlatform: [ONCHAIN] Transfer USDC Ethereum 100.00

    %% Notification of Payment Receipt
    FinancialSettlementPlatform-->>FinTechPlatform: [DATA] Payment Received
    FinTechPlatform-->>Business: [DATA] Notify Payment Received
    FinTechPlatform-->>Receiver: [DATA] Notify Incoming Payment

    %% Exchange Process (On-Chain to Off-Chain)
    FinancialSettlementPlatform->>FinancialSettlementPlatform: [EXCHANGE] ExchangeInput USDC Ethereum → ExchangeOutput USD Wire

    %% Fiat Payout to Receiver
    FinancialSettlementPlatform->>ReceiverBank: [OFFCHAIN] Transfer USD Wire 100.00
    ReceiverBank-->>Receiver: [DATA] Confirm Deposit

    %% Final Confirmation
    FinancialSettlementPlatform-->>FinTechPlatform: [DATA] Confirm Payout Complete
    FinTechPlatform-->>Business: [DATA] Notify Payment Completed
