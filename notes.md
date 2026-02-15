Project: Crypto-Banking Integration (v2026.01)

1. Integration Specs:

    Dashboard Logic: Wallet must appear as a 4th "tile" alongside Savings, Checking, and Line of Credit (LOC).

    API Bridge: Use a "Read-Only" API key for balance fetching to minimize risk, but "Trade" access for Buy/Sell.

    Preferred Exchanges: Support Coinbase, Kraken, and Binance.US via OAuth2.

2. The "Commission Engine" (Based on 2026 Schedule):

    Retail Tier: 0.5% commission on trades under $10,000.

    Professional Tier: 0.3% commission on trades $10k - $50k.

    Whale Tier: 0.1% for $50k+.

    Note: Bank takes a flat $2.00 "Network Access Fee" on every transaction regardless of size.

3. Security & Compliance (Non-Negotiable):

    Crypto Travel Rule: System must automatically collect and transmit sender/recipient details for every transfer (EU/UK 2026 standard).

    Self-Custody Option: Customers can "Connect" a Ledger or Trezor, but the bank does not hold those keys.

    Institutional Custody: For "Managed" wallets, use Fireblocks as the underlying vault provider.

4. User Flows to Draft:

    Onboarding: How do we handle the "Risk Disclosure" pop-up before the wallet is activated?

    Buy Flow: User selects "Checking" as the source of funds → Bank checks liquidity → Trade executes on Exchange → Confirmation screen shows "Bank Commission" and "Exchange Fee" separately.

5. Technical Questions for Architect:

    How do we handle real-time price volatility during the 2-second "Bank Liquidity Check" window?

    Do we need a separate "Crypto Liability" ledger in the core banking system?
