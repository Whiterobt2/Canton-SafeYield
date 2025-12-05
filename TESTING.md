# Testing Instructions for Canton SafeYield

This repository provides a conceptual and structural prototype of the SafeYield protocol.  
The goal of testing is to validate the logical flow of deposits, risk attestations, and yield activation.

Testing consists of three components:

---

## 1. Prototype Testing (UI Flow)

1. Open the Figma prototype link provided in `prototype-link.txt`.
2. Click through the flow:
   - Deposit input screen
   - Escrow protection state
   - Risk check explanation
   - Strategy activation
3. Confirm that the user journey reflects the architecture described in the README.

This demonstrates how SafeYield would appear to an everyday user.

---

## 2. Daml Logic Examination

The `/daml` directory contains minimal working modules representing:
- Escrow logic  
- Risk attestations  
- Strategy activation  
- Vault parameters  
- Hedging state  
- Yield estimation  
- Shared type definitions  

Review the template structures to understand:
- Which parties are signatories and observers  
- How attestation results control contract transitions  
- How a strategy position is created or rejected  
- How hedging and yield components are modeled

These modules intentionally focus on clarity rather than full protocol completeness.
