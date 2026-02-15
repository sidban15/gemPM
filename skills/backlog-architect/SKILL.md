---
name: backlog-architect
description: Converts discovery notes into structured Markdown Jira tickets within the PRD folder.
---

# Instructions

1. **Context Synthesis**: 
   - Analyze `RawNotes/Intelligence_Update.md` and the generated PRD.
   - Map high-level features (e.g., "Wallet View," "Commission-based Buy/Sell") to the specific technical personas defined below.

2. **Persona Classification & Feature Mapping**:
   - **Customer Persona**: 
     - *Unified Dashboard*: Integrated view of Savings, Checking, LOC, and Crypto Wallet.
     - *Trading UI*: Buy/Sell interface with real-time price feeds and commission transparency.
     - *History*: Unified transaction ledger showing fiat-to-crypto flows.
   - **Core Banking Persona**: 
     - *Liquidity Bridge*: Integration with Kraken/Coinbase APIs for order execution.
     - *Ledger Sync*: Real-time updates between the bank’s core ledger and the crypto wallet balance.
     - *LOC Collateralization*: (Future-proof) Logic for using crypto as collateral for the Line of Credit.
   - **Admin/Ops Persona**: 
     - *Commission Engine*: Automation of the bank's published commission schedule.
     - *Compliance Dashboard*: KYC/AML flags and suspicious activity reporting (SAR) for crypto flows.
     - *Risk Management*: Liquidity checks and circuit breakers for high volatility.

3. **File Generation & Structure**:
   - **Pathing**: Create one file per Epic in `PRD/JiraTickets/[Persona]/`.
   - **Naming Convention**: `EPIC_ID_FeatureName.md` (e.g., `CUST_01_Unified_Wallet_View.md`).
   - **Template Requirements**:
     - **User Story**: "As a [Persona], I want [Feature] so that [Value]."
     - **Acceptance Criteria**: Minimum 4 bullet points covering functional and edge cases.
     - **Technical Notes**: Specific API endpoints or regulatory constraints identified in research.
     - **Story Points**: Use Fibonacci sequence (1, 2, 3, 5, 8).

4. **Diagram Integration**: 
   - For complex Core Banking tickets, include a Mermaid.js flowchart snippet within the ticket for developer clarity.
