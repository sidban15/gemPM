**UX Audit: Integrating a Crypto Wallet into the Banking Dashboard**

**Date:** 2026-02-15

**Auditor:** UX Research Team

**Goal:** Propose a low-friction way to add a "Crypto" section to our existing mobile app UI, which currently features "Checking" and "Savings" accounts prominently.

---

**Current UI:**

The current home screen is a simple list:
*   Checking Account - $1,234.56
*   Savings Account - $50,000.00

---

**Core Principles for Integration:**

1.  **Familiarity:** The new crypto wallet should feel like just another account, not a completely separate, alien application bolted on.
2.  **Clarity:** The UI must clearly distinguish the crypto wallet from FDIC-insured cash accounts, both visually and with text, to manage customer expectations about risk.
3.  **Accessibility:** It should be visible and accessible from the main dashboard, not hidden three menus deep.

---

**Proposed UX Changes:**

**Option 1: The "New Account" Approach (Recommended)**

*   **How it works:** On the main dashboard, the crypto wallet appears as a third account type.

    *   Checking Account - $1,234.56
    *   Savings Account - $50,000.00
    *   **Crypto Wallet** - $8,500.00

*   **Visual Differentiators:**
    *   Use a distinct icon (e.g., a Bitcoin symbol, a stylized "C") next to "Crypto Wallet."
    *   Display the value in a slightly different color or font weight.
    *   Include a small, persistent disclaimer underneath: *"Not FDIC insured. Value may fluctuate."*

*   **Pros:**
    *   Highest visibility and integration.
    *   Leverages the existing mental model of "accounts."
    *   Simple, clean, and requires minimal user re-education.

*   **Cons:**
    *   May visually "demote" the importance of traditional accounts if the crypto balance is large.

**Option 2: The "Tab" Approach**

*   **How it works:** The top of the dashboard has tabs for "Cash" and "Crypto."

    *   `[ Cash ]` `[ Crypto ]`
    *   (The list of Checking/Savings accounts appears under the "Cash" tab)
    *   (The crypto assets would appear under the "Crypto" tab)

*   **Pros:**
    *   Clearly separates the regulated, insured world from the crypto world.
    *   Scalable if we add other investment types later (e.g., "Stocks").

*   **Cons:**
    *   Lower visibility for crypto. A significant portion of users never switch tabs.
    *   Creates a stronger sense of separation, which may work against the goal of making crypto feel "normal."

**Option 3: The "Widget" Approach**

*   **How it works:** A small, non-interactive widget is placed at the bottom of the current account list.

    *   Checking Account - $1,234.56
    *   Savings Account - $50,000.00
    *   ---
    *   [ **Your Crypto Portfolio** | Value: $8,500.00 | View > ]

*   **Pros:**
    *   Doesn't disrupt the primary banking UI at all.
    *   Safely "sandboxes" the crypto information.

*   **Cons:**
    *   The least integrated approach. Makes crypto feel like an afterthought or an advertisement.
    *   Poor discoverability for new users.

---

**Recommendation:**

Proceed with **Option 1: The "New Account" Approach**. It best aligns with our goal of making crypto a first-class citizen within the banking experience while providing clear visual cues about its unique nature. It is the most elegant and user-centric solution.

**Next Steps:**
*   Prototype Option 1 in Figma.
*   Conduct user testing sessions to validate the clarity of the "Not FDIC insured" disclaimer and the overall user perception.