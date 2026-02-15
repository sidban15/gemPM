**Meeting: Crypto Custody Architecture Review**

**Date:** 2026-02-15

**Attendees:**
*   CTO, Head of Engineering, Lead Security Architect
*   Product Lead (Crypto-Banking)

**Agenda:** To make a preliminary decision on the custody model for our crypto-banking launch: Fireblocks (MPC) vs. Self-Custody (HSMs).

---

**Arguments for Fireblocks (MPC - Multi-Party Computation):**

*   **Speed to Market:** This is the primary advantage. Fireblocks provides a battle-tested, off-the-shelf solution for custody, transaction signing, and policy management. Integration would be months, not years.
*   **Reduced Operational Overhead:** We would not need to manage our own secure data centers, physical hardware (HSMs), or the complex key management ceremonies associated with self-custody. Fireblocks handles this.
*   **Asset Support:** Fireblocks supports hundreds of tokens and blockchains out-of-the-box. A self-custody solution would require significant engineering effort for each new asset we want to support.
*   **Security Model:** MPC eliminates the single point of failure of a private key. The key is split into shares and distributed, making it incredibly difficult for an attacker (or rogue insider) to compromise. Transactions are signed via a multi-party cryptographic process.
*   **Insurance:** Fireblocks comes with a significant insurance policy covering assets in their custody, which would be a major selling point for our customers and a requirement for our risk committee.

**Arguments for Self-Custody (HSMs - Hardware Security Modules):**

*   **Ultimate Control:** The keys are ours, stored in our own hardware, in our own data centers. We are not reliant on a third-party for security or access to our customers' funds. This aligns with our bank's traditional security posture.
*   **No Third-Party Risk:** We are not exposed to the risk of Fireblocks having a systemic security failure, a business continuity issue, or changing their terms of service.
*   **Potentially Lower Long-Term Cost:** While the initial investment in HSMs and secure infrastructure is very high, the ongoing costs could be lower than Fireblocks' annual licensing and transaction fees, especially at scale.
*   **Regulatory Perception:** Regulators may look more favorably on a model where we have direct physical and logical control over cryptographic keys, although MPC is rapidly gaining acceptance.

**Decision & Next Steps:**

*   **Preliminary Decision:** The consensus leans heavily towards **Fireblocks**. The speed-to-market advantage is too significant to ignore for our initial product launch. The operational complexity and cost of building a self-custody solution from scratch are prohibitive for our MVP.
*   **Risk Mitigation:** The security team will conduct a deep-dive due diligence on Fireblocks' security audits, certifications (like SOC 2 Type II), and insurance policies.
*   **Long-Term View:** We will re-evaluate this decision in 2-3 years. If our crypto business grows to a massive scale, the economic argument for bringing custody in-house may become compelling. We can build a roadmap for a potential migration in the future.

**Action Item:** Engineering to begin API exploration with the Fireblocks sandbox environment. Product to engage Fireblocks sales for detailed pricing and legal review.