# 3Jane (3jane.xyz) — Adversarial DeFi Due Diligence Report

**Date:** 2026-03-15
**Methodology:** Maximum adversity / guilty until proven innocent
**Trust Hierarchy:** On-chain > Independent third-party > Community > Historical footprints > Official comms

---

## Executive Summary

**Verdict: Legitimate protocol. Not a rug pull. Not a functional credit protocol — yet.**

3Jane is a credit-based money market protocol backed by Paradigm ($5.2M seed) targeting DeFi's unsecured lending problem. Its investor roster — Paradigm, Coinbase Ventures, Robot Ventures, Wintermute, Andre Cronje, Kain Warwick — is one of the most credible in the space and is the single strongest legitimacy signal available.

However, 4+ months after its November 2025 "mainnet launch," the protocol's core advertised product — unsecured USDC credit lines — has **not yet been deployed**. Current TVL (~$25M–$38M) earns Aave money market yield with JANE token incentives on top. Lenders are effectively depositing USDC in exchange for JANE token exposure, not credit yield. JANE token tokenomics are entirely undisclosed: no supply, no vesting, no team/investor allocation published.

The structural challenge 3Jane faces — the adverse selection problem in unsecured DeFi lending — is the same one that killed Goldfinch (3 defaults, $20M+ in losses), Maple Finance (~$36M in Orthogonal Trading defaults), and TrueFi (Blockwater default). 3Jane's design improvements (zkTLS credit scoring, EigenLayer verifiers, legal recourse via Credit Slasher) address the symptoms but not the structural problem. The advertised technical differentiators are mostly unproven in production.

The protocol is **not a rug**. The team is doxxed, the backing is genuine, and the architecture has been audited. But the live product does not yet match the advertised product, and the JANE token incentive program has all the structural characteristics of a yield-farming deposit drive ahead of a TGE — which may or may not deliver the underlying credit product as described.

---

## Team Assessment

### Identified Team Members

**Jacob Chudnovsky** (Founder, @_yakovsky)
- Role at Ribbon Finance/Aevo: **Strategy** (not smart contract engineering) for ~3 years
- Left Aevo April 2024 to found 3Jane
- Background: DeFi participant since 2017 (wrote ICO contracts), active during DeFi summer
- Stanford educated (matches LinkedIn profile)
- Has appeared in press (The Block interview, podcast), is fully doxxed
- **Ribbon Lend connection**: Worked at the company that built Ribbon Lend — an unsecured DeFi lending product wound down after FTX collapse in 2022. Borrowers (Folkvang, Wintermute) repaid out of pocket; no lender losses. But this means 3Jane is explicitly his second attempt at this product category.

**Jeremy Obadia** (Founding Member)
- MIT MSc Financial Engineering + UCL
- Previously at Aevo (strategy/growth)
- Strong TradFi quant credentials for a credit risk product

### Team Quality Assessment

**Positive signals:**
- Both founders fully doxxed with verifiable professional histories
- Ribbon Finance/Aevo is a legitimate, respected DeFi protocol
- Paradigm's diligence process effectively validates the team
- Jeremy Obadia's financial engineering background is relevant for credit modeling
- Julian Koh (Ribbon co-founder) investing personally is a credibility bridge

**Concerns:**
- Neither founder is primarily a smart contract engineer — both came from strategy/growth roles. The technical depth for a novel credit protocol is less clear than their domain credentials.
- No other team members publicly named despite a $5.2M raise and operating since mid-2025
- Chudnovsky's primary experience at Ribbon was strategy, not building Ribbon Lend (which he may have contributed to but did not build as a lead engineer)

**Risk Rating: LOW** — Team is doxxed, credentialed, legitimate. No rug probability based on team profile.

---

## Third-Party Consensus

### Audit Status

Three audits by **Veridise**, confirmed publicly at veridise.com/audits-archive/company/3jane/:

| Audit | Date | Product | Report |
|-------|------|---------|--------|
| 3JANE-EETH-X-C | April 2024 | V1 eETH covered calls vault | Listed, PDF access linked |
| Amplol | May 2024 | V1 Amplol vault | Listed, PDF access linked |
| Morpho Blue | August 2025 | Core money market contracts | Listed, PDF access linked |

**Critical gap**: Specific vulnerability counts (critical/high/medium/low) are not publicly disclosed in search-accessible form. The full audit PDFs require direct access to the Veridise report links. Absence of publicly confirmed "zero critical findings" from the primary audit (August 2025) is a yellow flag in a protocol holding $25M+.

**Veridise** is a legitimate security firm with a public audit portfolio. Not as prominent as Trail of Bits or Spearbit, but credible. Confirmed active since at least 2023.

Note also: The August 2025 "Morpho Blue" audit is specifically of 3jane's fork of Morpho Blue — not the original Morpho Blue (which has been audited separately by multiple Tier 1 firms). The 3jane-specific modifications and wrappers (USD3, sUSD3, credit underwriting module) are what Veridise reviewed.

### Independent Analysis Quality

- **Paradigm investment**: Highest-quality signal available. Paradigm is technically rigorous, has deep smart contract security expertise, and does not back scams.
- **Chaincatcher (adversarial)**: Geographic restriction, enforcement uncertainty, Goldfinch precedent, limited on-chain credit scoring deterrence
- **Alea Research (moderate)**: Concentration risk (UHNWI/institutional borrowers → similar to failed CeFi lending), privacy-enforcement trade-off, multisig details not addressed
- **PANews / MEXC / Gate educational articles**: Promotional, limited critical value

### Investor Signal

| Investor | Significance |
|----------|-------------|
| Paradigm | Tier 1 — among the most rigorous crypto investors; essentially eliminates rug probability |
| Coinbase Ventures | Strong — adds regulatory relationship value |
| Robot Ventures | DeFi-native, respected signal |
| Wintermute | Strategic: they also lend to the protocol ecosystem |
| Andre Cronje | DeFi OG validator; Yearn Finance founder |
| Kain Warwick | Synthetix founder; DeFi OG validator |
| Julian Koh | Ribbon Finance co-founder investing in his former employee's startup |

**Risk Rating: LOW** for rug/intentional fraud. Institutional backing this deep doesn't support rug mechanics.

---

## On-Chain Findings

### Contract Addresses (Ethereum Mainnet)

| Contract | Address | Type |
|----------|---------|------|
| USD3 Token | `0x056B269Eb1f75477a8666ae8C7fE01b64dD55eCc` | EIP-1967 Transparent Proxy |
| sUSD3 Token | `0xf689555121e529Ff0463e191F9Bd9d1E496164a7` | ERC-4626 |
| JANE Token | `0x1fF75fb5C20659f46a11Fd0734b464D5DD8004A7` | Base network |

**Chain confusion flag**: Sources describe 3Jane as running on "Base" but the USD3/sUSD3 tokens are deployed on Ethereum mainnet. The JANE token is on Base. This inconsistency across official and third-party sources reflects a documentation transparency gap. Not a red flag, but a yellow flag.

### Upgrade Risk — EIP-1967 Transparent Proxy

USD3 is deployed as an **EIP-1967 Transparent Proxy**. This means:
- There is a proxy admin who can upgrade the implementation contract
- A malicious or compromised upgrade could alter the logic controlling all lender funds
- The proxy admin's identity is not publicly disclosed in documentation

Per the docs/risk page: governance risk is mitigated by "multisig with time-lock" (not independently verified by on-chain inspection in this research). The docs acknowledge this is a roadmap item — a "veto window for USD3 governance token holders" — suggesting the current multisig is **team-controlled without governance veto**.

**Risk Rating: HIGH** — upgradeable contract with undisclosed proxy admin composition and unverified timelock.

### TVL and Deposit Structure

- **Phase 1 reality**: All deposited USDC goes into Aave V3 USDC pool, not into credit lines
- **First tranche** ($25M cap): Filled by November 18, 2025
- **Second tranche** ($12.5M cap): In progress at time of analysis
- **Effective TVL**: ~$25M–$38M as of this report
- **sUSD3** capped at 15% of total pool; earns all Aave yield during bootstrapping
- **sUSD3 APY**: ~27% during bootstrapping (Aave yield flows to sUSD3 holders)
- **USD3 yield**: Primarily JANE token incentives; no native credit yield currently

### JANE Token

- **7 million JANE emitted** as liquidity mining rewards
- **No secondary market** — pre-TGE
- **No publicly disclosed tokenomics**: total supply, team allocation, investor allocation, vesting schedule all undisclosed
- **Risk pattern**: Lenders may be farming JANE tokens at the expense of future token holders (same structure as many yield farming programs that precede dilutive TGEs)

### Protocol Activity Status

As of March 2026 (4+ months post-mainnet launch): **No credit lines have been extended to merchants.** The protocol is in Phase 1 (3CA data tuning) and Phase 2 (deposits open). Phase 3 (actual credit extension) has no publicly disclosed timeline.

**Risk Rating: MEDIUM** — The advertised product is not live. This is a deferral of the core product, not a complete absence. But it means lenders currently bear no credit risk while earning yield that depends on JANE token value at TGE.

---

## Comparative Analysis

### Predecessor Failures (Category Risk)

| Protocol | Default Event | Losses | Root Cause |
|----------|--------------|--------|-----------|
| Goldfinch | 3 defaults (Tugende, Lend East, others) | $20M+ | Adverse selection + emerging market enforcement gap |
| Maple Finance | Orthogonal Trading default | ~$36M | Institutional borrower insolvency; inadequate underwriting |
| TrueFi | Blockwater default | ~$4M | Underwriting failure + liquidation gap |
| Ribbon Lend | No defaults | $0 (borrowers repaid) | FTX contagion risk; voluntarily wound down |

3Jane's innovations vs. predecessors:
- **zkTLS credit scoring** (vs. reputation-only whitelisting in Maple/Goldfinch)
- **On-chain credit score anchoring** via Cred Protocol + Blockchain Bureau
- **Legal recourse** via Credit Slasher + US collections agencies
- **Junior/senior tranche** structure (sUSD3 absorbs first losses)

**Key structural problem not solved**: The adverse selection problem. Creditworthy crypto-native users who hold $600K in DeFi assets can already borrow $300K on Aave overcollateralized. They don't need 3jane's $68K unsecured credit line badly enough to accept the legal/privacy cost. Those who do need it badly enough are precisely the higher-risk borrowers. 3jane's design improvements reduce but cannot eliminate this selection effect.

### Tokenomics Sustainability

3Jane does not yet have a revenue model from credit operations (Phase 1: all funds in Aave, no credit spread). Revenue today = fraction of Aave's USDC APY.

Future revenue model: net interest spread on credit lines (borrower rate minus Aave base rate). At maturity, this could be substantial. But this model has not been demonstrated in any DeFi unsecured protocol at scale.

The JANE token emissions during bootstrapping are a deferred liability. When TGE occurs:
- Current lenders have earned JANE tokens at unknown dilution levels
- If the credit product underperforms, JANE token value depends entirely on speculative demand
- No disclosed mechanism linking JANE token to protocol revenue or governance rights

### Reclaim Protocol / zkTLS Trust Model

3jane uses Reclaim Protocol for zkTLS, which operates as a **transparent proxy model**. As established in the peer.xyz investigation, this model:
- Requires some trust in the proxy service
- Uses EigenLayer AVS with slashing for economic security (better than Peer.xyz's model)
- But introduces a bottleneck: if Reclaim Protocol is compromised or acts adversarially, 3jane's credit underwriting data could be fabricated

Unlike peer.xyz's fully centralized attestation service, 3jane's use of EigenLayer for cryptoeconomic security is a meaningful improvement. But it is not trustless — it is trust-minimized.

---

## Red Flags Register

| # | Flag | Severity | Evidence |
|---|------|----------|---------|
| 1 | Credit lines not yet deployed 4+ months post-mainnet | HIGH | Phase 1 bootstrapping still active; all TVL in Aave, not credit |
| 2 | JANE token with no disclosed tokenomics | HIGH | No supply, vesting, or allocation published; 7M tokens emitted |
| 3 | USD3 on upgradeable proxy, proxy admin undisclosed | HIGH | EIP-1967 Transparent Proxy confirmed on Etherscan; admin not named |
| 4 | Veridise audit findings not publicly disclosed | MEDIUM | Reports exist but vulnerability counts inaccessible |
| 5 | US-only borrower restriction with global lender base | MEDIUM | Plaid + Credit Karma coverage is US-centric; enforcement only via US collections |
| 6 | V1 product (covered calls) quietly wound down | MEDIUM | No post-mortem; V1 docs archived without announcement |
| 7 | Category precedent: unsecured DeFi lending has failed repeatedly | MEDIUM | Goldfinch 3 defaults, Maple ~$36M, TrueFi Blockwater |
| 8 | Chain deployment documented inconsistently | YELLOW | Some sources say Base, contracts found on Ethereum mainnet |
| 9 | Single founder + small undisclosed team | YELLOW | Only Chudnovsky and Obadia named despite $5.2M raise |
| 10 | Phase 3 transition timeline undisclosed | YELLOW | No date or TVL milestone published for actual credit launch |
| 11 | Reclaim Protocol proxy trust assumption | YELLOW | EigenLayer slashing mitigates but does not eliminate trust requirement |
| 12 | Adverse selection structural problem | STRUCTURAL | Creditworthy borrowers don't need 3jane; needy borrowers have higher default risk |

---

## Unresolved Questions

1. **Who holds the USD3 proxy admin key, and what is the multisig composition and timelock duration?** The risk docs say "multisig with time-lock" but this has not been independently confirmed via on-chain inspection.

2. **What are the specific JANE token tokenomics?** Total supply, team allocation percentage, investor allocation, vesting cliff/schedule, and community/lender allocation are entirely undisclosed as of this report.

3. **When does Phase 3 (actual credit line extension) begin?** The protocol has been in Phase 1 bootstrapping for 4+ months with no public timeline for moving to actual credit operations.

4. **What did the August 2025 Veridise audit find?** Severity and count of vulnerabilities discovered in the Morpho Blue core money market contracts are not publicly accessible.

5. **What is the total JANE token supply and how does it compare to the 7M already emitted?** This determines how much dilution current lenders face at TGE.

6. **How does the Credit Slasher actually work on-chain?** The mechanism for auctioning bad debt to US collection agencies has not been verified via contract code or independent audit.

7. **What is the protocol's actual default rate once credit lines are extended?** The 3CA underwriting model is untested in production; all historical comparables (Goldfinch, Maple) had poor default outcomes.

---

## Protocol History & Pivots

| Period | Product | Status |
|--------|---------|--------|
| Early 2024 | eETH Covered Calls Vault (V1) | Audited by Veridise, deployed, quietly wound down |
| April 2024 | Amplol Vault (V1 variant) | Audited by Veridise, appears archived |
| June 2025 | $5.2M seed raise; credit protocol revealed | Announced |
| August 2025 | Morpho Blue core contracts audited by Veridise | Completed |
| November 2025 | Mainnet launch; Phase 1 bootstrapping begins | Live (Aave-only deposits) |
| November 18, 2025 | First $25M tranche filled | Milestone |
| March 2026 | Protocol still in bootstrapping, no credit lines live | Ongoing |

The product pivot from covered calls to unsecured credit is substantial — it's a completely different product category, different risk model, and different user base. The V1 pivot was done without a public post-mortem. **This is the protocol's second major product bet in under two years.**

---

## Final Verdict

| Dimension | Assessment |
|-----------|-----------|
| Rug pull risk | **VERY LOW** — Paradigm backing, doxxed team, legitimate precedents |
| Smart contract exploit risk | **MEDIUM** — Veridise audited, Morpho Blue base is solid, but proxy admin and USD3 wrapper risks unverified |
| Credit default risk | **UNQUANTIFIABLE** — Product not live; category has poor DeFi track record |
| Governance centralization | **HIGH** — Multisig without confirmed timelock controls upgradeable contracts |
| Token risk | **HIGH** — JANE tokenomics entirely undisclosed; TGE could be dilutive |
| Product delivery risk | **MEDIUM-HIGH** — 4 months post-launch, core product not deployed; adverse selection unsolved |
| Team legitimacy | **LOW RISK** — Both founders doxxed, credentialed, Paradigm-validated |

**Bottom line**: 3Jane is a legitimate, well-funded experiment in solving DeFi's unsecured lending problem. It is not a rug. But it is a protocol where the advertised product has not yet launched, where the JANE token represents an undisclosed future dilution event, and where the category it is trying to dominate has failed repeatedly for structural reasons that 3jane's design improvements partially but not fully address.

**For depositors**: You are currently depositing USDC into Aave plus earning JANE tokens at unknown dilution. This is a yield-farming play with credit protocol upside — not a credit protocol investment. The risk profile is closer to a token presale with Aave as the base than to a lending protocol investment.

**For observers**: Watch for the Phase 3 launch date announcement and the JANE token TGE tokenomics disclosure. Both are the critical events that will determine whether the protocol delivers on its promises.
