**Architecture Meeting: Exchange API Integration**

**Date:** 2026-02-15

**Attendees:**
*   Lead Engineer (Crypto-Banking)
*   Backend Engineering Team
*   Security Architect

**Topic:** Strategy for integrating with external crypto exchanges (Kraken, Coinbase) to execute customer buy/sell orders.

---

**Objective:**

To design a secure, reliable, and scalable service to manage API connections, execute trades, and handle funds flow between our institution and third-party exchanges.

**Core Decision: OAuth 2.0 for Authentication**

*   **Why OAuth2?** Both Kraken and Coinbase support OAuth2 for third-party integrations. This is the industry standard and the most secure method.
*   **How it Works:**
    1.  **Our Application:** We will register our service as a client application with both Kraken and Coinbase.
    2.  **Institutional Account:** We will maintain a master institutional/corporate account with both exchanges. This account will hold the necessary float (both fiat and crypto) to facilitate trades.
    3.  **Permissions (Scopes):** We will use OAuth2 to grant our service specific, limited permissions. We will request only the scopes absolutely necessary:
        *   `trade`: To create and execute orders.
        *   `wallet:read`: To read balances and confirm funds have settled.
        *   `wallet:withdraw`: To move purchased crypto to our central custody wallet (e.g., Fireblocks).
        *   `wallet:deposit`: To move fiat currency into the exchange for pre-funding trades.
    4.  **Security:** Critically, we will **NOT** request permissions for `user:read` or any other scope that would give us access to sensitive user data on the exchange. The connection is purely for our institutional trading. The API keys and refresh tokens will be stored in a secure, encrypted vault (like HashiCorp Vault) with strict access controls.

**Proposed Architecture:**

1.  **Trade Execution Service (Microservice):**
    *   A dedicated, isolated microservice responsible for all interactions with exchange APIs.
    *   It will expose a simple internal API: `POST /v1/trade` with a payload like `{ "asset": "BTC", "amount": 0.1, "direction": "buy" }`.
    *   This service will encapsulate all the specific logic for each exchange (e.g., handling different endpoint URLs, rate limits, and order status conventions).

2.  **Order Matching & Routing:**
    *   For the MVP, we can simply route all trades to one primary exchange (e.g., Kraken).
    *   **Future Enhancement (v2):** The service can be enhanced to act as a **smart order router**. It would fetch quotes from both Kraken and Coinbase simultaneously and execute the trade with the one offering the better price, ensuring best execution for the customer.

3.  **Balance & Settlement Management:**
    *   The service will continuously monitor our fiat and crypto balances on the exchanges.
    *   It will have automated logic to trigger alerts if our hot-wallet/float balance drops below a certain threshold, prompting our treasury team to top it up.
    *   After a buy order is filled, it will automatically initiate a withdrawal of the crypto from the exchange to our main institutional custody wallet (managed by Fireblocks). This minimizes our exposure on the third-party exchange.

**Action Items:**

*   **Spike:** Create a proof-of-concept (PoC) to implement the OAuth2 client credentials flow with the Kraken and Coinbase sandboxes.
*   **Security:** Define the vault architecture and access policies for storing the API credentials.
*   **Treasury:** Work with the finance department to establish the operational process for pre-funding the exchange accounts with fiat currency.