# Canton SafeYield

Canton SafeYield is a secure, privacy-preserving yield vault designed to make on-chain income accessible to everyday users. Deposits remain protected inside a Canton escrow contract and are only deployed into yield-generating strategies once a private risk-oracle issues an attestation confirming that predefined safety conditions are met. If a violation occurs, funds automatically revert to the user.

SafeYield combines the simplicity of a deposit-based interface with institutional-grade risk management enabled by Canton's privacy model.

---

## Problem

Most on-chain yield products expose users to hidden leverage, weak risk controls, and the possibility of catastrophic loss. Yield vaults built on derivatives or automated strategies often show attractive APYs but lack transparency, safety guarantees, or privacy. As a result, everyday users avoid these products, limiting broader adoption.

---

## Solution: Risk-Gated Yield Vault

SafeYield introduces a protected yield vault built on Canton with the following properties:

1. Protected Escrow Deposits  
   User funds enter a Canton escrow and cannot be accessed by the strategy until required risk conditions are verified.

2. Private Risk Oracle Attestations  
   Delta exposure, drawdown limits, hedging requirements, and volatility thresholds are validated privately. Only the attestation result ("approved" or "violation") is revealed to the vault.

3. Automatic Capital Protection  
   Any violation immediately triggers an enforced return of user funds back to escrow.

4. Simple User Experience  
   Users interact with a minimal flow: deposit, escrow, yield accrual.

5. Mass-Market Accessibility  
   No derivatives knowledge is required. Users are not exposed to unmanaged directional or volatility risk.

---

## Yield Generation Logic

SafeYield’s yield engine is based on a structured options-selling framework similar to those used by professional options market-making systems. The core functional components are:

### 1. Premium Income Through Option Selling
The strategy generates yield by selling out-of-the-money call and put options.  
Premium income depends on implied volatility, strike selection, and time to expiry.  
Premiums create a predictable baseline return for depositors.

### 2. Dynamic Delta Hedging
Once an option position is created, the system continuously manages directional exposure.  
Delta neutrality is maintained by adjusting spot or synthetic positions as the market moves.  
This stabilizes the payoff profile and prevents directional losses.

### 3. Risk Budget and Exposure Controls
The strategy operates under strict invariants:
- maximum allowable drawdown  
- delta and gamma exposure limits  
- collateral sufficiency  
- volatility shock tolerance  

When volatility increases, hedging frequency and collateral requirements adjust to preserve capital.

### 4. Full Collateralization
All short option positions remain fully collateralized.  
Collateral levels adjust dynamically according to market risk, ensuring solvency in adverse conditions.

### 5. Premium Reinvestment and Compounding
Collected premiums are rolled forward into subsequent cycles, compounding returns while staying within predefined safety constraints.

### 6. Non-AMM Execution Model
The strategy does not rely on liquidity pools, bonding curves, or automated market makers.  
Option positions are individually priced and collateralized, eliminating risks such as impermanent loss or liquidity fragmentation.

---

## SafeYield Architecture Overview

### SafeYieldEscrow (Daml Template)
- Holds user deposits privately.  
- Enforces release conditions based on attestation.  
- Automatically returns funds upon violations.

### RiskOracleAttestation (Daml Template)
An off-ledger risk engine issues attestations indicating:
- Approved or Violation  
- Compliance with drawdown limits  
- Delta exposure conditions  
- Presence of hedging mechanisms  

Only the attestation status is made visible to Canton.

### SafeYieldStrategy (Daml Template)
- Activated only after an approved risk attestation.  
- Runs the yield-generation logic described above.  
- Returns aggregated outcomes to users without exposing strategy internals.

---

## Privacy Model

Canton's architecture enables:
- Private escrow per user  
- Private evaluation of risk conditions  
- Attestations without revealing individual balances or strategy-sensitive data  
- Enforced smart contract execution without leaking internal states  

This level of confidentiality and enforceable safety is not achievable on public blockchains without sacrificing transparency or user protection.

---

## Prototype Demo

Figma prototype:  
https://www.figma.com/proto/GAdcCOr6pp10yjMAX0jbw0/Untitled?node-id=0-1&t=ulAyU6izjnl3Vcxg-1

The demo illustrates the deposit and protection workflow for SafeYield.

---

## Why SafeYield Matters

SafeYield makes advanced yield strategies accessible to everyday users by combining verifiable risk controls, private attestations, and a simple interface. It enables a class of on-chain financial products that consumers can trust while meeting institutional expectations for safety and confidentiality.
