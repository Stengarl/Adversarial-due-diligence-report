# USD.AI (Permian Labs) — Adversarial Due Diligence Report

**Investigator:** DeFi Adversarial Research Agent
**Date:** 2026-02-24
**Confidence Level:** Medium (constrained by opaque tokenomics and unverified on-chain data)

---

## LEAD FINDING — Read This First

> **The team's flagship "prior success" story (MetaStreet) collapsed to sub-1% NFT lending market share.**

MetaStreet — the protocol USD.AI openly evolved from — was effectively killed by the NFT crash, losing 97% of its market volume. The team pivoted the *entire product thesis* away from NFT-backed loans into GPU/AI-backed loans. This is not the same as building on success. This is a full pivot from a failed vertical. **This fact is buried in marketing materials that characterize MetaStreet as validating proof of concept.**

---

## 1. Executive Summary

**Verdict:** USD.AI is a legitimate-but-high-risk DeFi experiment, NOT an obvious rug pull. It has real institutional backers, real audits, and a real product. However, it carries **structural risks that are fundamentally different from what the marketing implies**, and the CHIP token ICO presents a separate, significant value-extraction risk for retail participants.

### Top 3 Risks

1. 🔴 **CRITICAL — Untested Legal Framework at Scale:** The CALIBER/UCC Article 7 system that underpins the *entire collateral model* has never been stress-tested in an actual default + liquidation event. Physical GPU repossession costs ~30% in ITAD fees alone, before legal costs.
2. 🔴 **CRITICAL — CHIP Token Opacity:** Full tokenomics allocation (team %, VC %, vesting schedules) has **not been publicly disclosed**. Retail buyers at $0.03 / $300M FDV are flying blind on insider supply overhang.
3. 🟠 **HIGH — GPU Collateral Depreciation:** AI hardware depreciates 20–50% annually. Multi-year loans against depreciating collateral with LTVs not publicly disclosed creates structural underwater-loan risk, especially if a new GPU architecture releases mid-loan-term.

### Top 3 Positive Signals

1. ✅ **Institutional Backers Independently Verified:** Framework Ventures, Dragonfly, YZi Labs (Binance), Coinbase Ventures, DCG — confirmed via multiple independent sources including The Block, CoinDesk, and PANews. These are not logo-farms.
2. ✅ **Multiple Cantina Audits, No Critical/High Findings:** 5 Cantina audits from 2023–2025 exist. The most recent (May 2025) found 0 critical, 0 high issues. Active bug bounties on Immunefi and Cantina.
3. ✅ **PayPal PYUSD Integration Confirmed:** The PYUSD partnership was independently confirmed by The Defiant, Crypto Economy, and PYUSD's own on-chain data (>43% of Arbitrum PYUSD deposits are in USDai). This is real.

---

## 2. Team Assessment

### Identified Team Members

> ⚠️ **UNVERIFIED via primary sources — sourced from aggregators only**

| Name | Role | Verified? |
|------|------|-----------|
| David Choi | CEO, Permian Labs | Unverified — not independently confirmed |
| Conor Moore | COO, Permian Labs | Unverified — not independently confirmed |

> ⚠️ **UNVERIFIED CLAIM:** The Stablecoin Insider review mentions "former Deutsche Bank investment banker" as a founder credential. This was NOT independently corroborated by LinkedIn, news articles, or other sources found in this investigation. **Treat as unverified marketing claim.**

### GitHub / Developer Activity

**STATUS: UNVERIFIED — Direct GitHub access was not obtained in this investigation.**

What is known:
- USD.AI explicitly traces its technical lineage to MetaStreet Protocol
- MetaStreet introduced: Automatic Tranche Maker (ATM), Liquid Credit Token (LCT), Yield Pass primitives
- Cantina's auditors examined real, substantive code: ERC-7540 async vaults, Chainlink oracle integrations, redemption queue mechanics — this level of audit complexity implies real engineering work

**What could NOT be verified:**
- GitHub repo URL, commit count, contributor count
- Whether any developers have prior contributions to failed/scam projects
- Code quality, test coverage, CI/CD presence
- Whether Solidity code is original or a fork

### Social Media Forensics

- **Twitter/X account @USDai_Official** exists (confirmed via direct tweet references in CoinDesk, The Defiant)
- **ZERO Reddit discussion found** across r/DeFi, r/CryptoCurrency, r/ethfinance — this is anomalous for a protocol claiming $658M TVL. Legitimate protocols of this size typically generate organic community discussion.
- No evidence of deleted tweets or social media impersonation found, but no deep forensic archive search was possible

### What Could NOT Be Verified

- Team members' actual employment histories
- "Deutsche Bank" credential claim
- LinkedIn profiles not independently accessed
- No prior projects the team worked on (beyond MetaStreet) were identified
- No legal records search was completed

---

## 3. Third-Party Consensus

### Independent Analyst Coverage

| Source | Coverage Type | Sentiment | Affiliation Risk |
|--------|--------------|-----------|-----------------|
| CoinDesk | News article (Oct 2025) | Neutral/informative | Low — tier 1 publication |
| The Block | News article (Jan 2026) | Neutral/informative | Low |
| The Defiant | News coverage | Neutral/informative | Low |
| Bankless | Feature article | Positive | **Medium — Bankless has sponsored content history** |
| Arbitrum Blog | Protocol feature | Positive | **High — Arbitrum is an investor** |
| Stablecoin Insider | Deep dive review | Mixed/cautionary | Low-Medium |
| Tom's Hardware | Tech news | Informative | Low |
| Stablewatch | Deep dive | Descriptive | Medium — unknown affiliation |

> ⚠️ **CRITICAL OBSERVATION:** No coverage from **Rekt News**, no negative investigative journalism, no DeFi Safety assessment, no independent security researcher commentary was found. For a $658M TVL protocol, this absence of adversarial coverage is notable — but may reflect recency (rapid growth in H2 2025) rather than suppression.

### Security Posture — Audits

> **PARTIALLY VERIFIED**

| Audit | Date | Firm | Critical/High Found | Status |
|-------|------|------|---------------------|--------|
| Cantina Audit | 06-22-2023 | Cantina | Unknown | Listed on docs |
| Cantina Audit | 10-03-2023 | Cantina | Unknown | Listed on docs |
| Cantina Audit | 11-25-2023 | Cantina | Unknown | Listed on docs |
| Cantina Audit | 04-30-2024 | Cantina | Unknown | Listed on docs |
| Cantina Audit (USDai Stablecoin) | 05-12-2025 | Cantina | **0 Critical, 0 High** | ✅ Verified via Cantina portal |

**Notable findings from May 2025 audit:**
- Medium: "Inflation Attack" on StakedUSDai — **FIXED**
- Low (unresolved): DoS vulnerability on redemption requests for specific controllers — **ACKNOWLEDGED, NOT FIXED**
- Bug Bounties: Active on Immunefi and Cantina

> ⚠️ **AUDIT CAVEAT:** Only Cantina has audited. No Trail of Bits, OpenZeppelin, Spearbit, or competitive audit (Code4rena/Sherlock) found. A $658M TVL protocol relying on a single audit firm — even a reputable one — is a concentration risk. The audited code matching deployed bytecode was **NOT independently verified.**

### Community Sentiment

- **Reddit:** 0 posts found. Anomalous for claimed scale.
- **Critical CT discussion:** Community criticism noted around $300M FDV, VC extraction risk, and "mercenary capital" post-airdrop
- **No DeFi community governance discussions** (Ethresear.ch, Snapshot) found

---

## 4. On-Chain Findings

> ⚠️ **DISCLAIMER:** Direct contract verification was NOT completed in this investigation. No Etherscan/Arbiscan query was executed. The following is based on secondary sources only.

### What Is Known (Secondary Sources)

| Data Point | Value | Verified? |
|-----------|-------|-----------|
| Primary chain | Arbitrum | ✅ Multiple sources |
| Secondary chain | Base (Nov 2025 expansion) | ✅ Multiple sources |
| USDai token address | `0x0a1a1a107e45b7ced86833863f482bc5f4ed82ef` | ⚠️ From Coinbase price page only — unconfirmed |
| TVL (reported) | $658M (peaked ~$701M Nov 2025) | ⚠️ DefiLlama listed, not verified on-chain |
| PYUSD share of deposits | >43% of Arbitrum PYUSD | ✅ The Defiant, on-chain data |

### Structural On-Chain Risks

| Risk | Source | Severity |
|------|--------|----------|
| Chainlink oracle dependency | Confirmed by Cantina audit | 🟠 HIGH |
| ERC-7540 async vault / redemption queue delays | Cantina audit | 🟡 MEDIUM |
| Blacklisting functionality (who controls it?) | Cantina audit confirmed present | 🟠 HIGH |
| CALIBER ERC-721 auction mechanism for defaults | Protocol docs | 🟠 HIGH |
| DoS on redemption queue (known, unpatched) | Cantina audit (May 2025) | 🟡 MEDIUM |

### Token Distribution

| Allocation | Amount | % of Supply | Verified? |
|-----------|--------|-------------|-----------|
| Total supply | 10,000,000,000 CHIP | 100% | ✅ |
| Public ICO (CoinList) | 700,000,000 | 7% | ✅ |
| Airdrop | 300,000,000 | 3% | ✅ |
| Team allocation | Unknown | **UNDISCLOSED** | 🔴 |
| VC/Investor allocation | Unknown | **UNDISCLOSED** | 🔴 |
| Ecosystem/Treasury | Unknown | **UNDISCLOSED** | 🔴 |
| Remaining 90% | Unknown | **UNDISCLOSED** | 🔴 |

> 🔴 **CRITICAL:** $300M FDV at public launch, with 90% of supply allocation undisclosed, means retail ICO participants cannot calculate their actual dilution exposure or insider dump risk. Seed/private round pricing vs. $0.03 public price is also not disclosed.

---

## 5. Yield Mechanism Assessment

**Claimed yield:** 13–17% APY on sUSDai; 4.5% on PYUSD deposits (PayPal incentive program)

| Yield Component | Source | Sustainable? | Risk Level |
|----------------|--------|-------------|-----------|
| 15% APR GPU loans | Borrower loan repayments | Yes, if no defaults | 🟠 HIGH — credit risk |
| T-Bill floor (unused capital) | US Treasuries | Yes | 🟢 LOW |
| $M (WrappedM) base asset emissions | M0 protocol mechanics | Partially | 🟡 MEDIUM |
| Pendle boost multipliers | Token incentives (inflationary) | **No** — time-limited | 🟠 HIGH |
| Base chain 15x launch bonuses | Token incentives | **No** — sunset | 🟠 HIGH |
| PayPal 4.5% on PYUSD | PayPal incentive program (1 year) | **No** — expires | 🟡 MEDIUM |

**Verdict on yield:** The *base yield* (15% APR on loans + T-Bill floor) is economically legitimate if loans perform. This is NOT an Anchor Protocol situation — the yield source is identifiable and real. However, boosted yields (Pendle 25x, Base 15x, PayPal 4.5%) are temporary incentives that inflate reported APY significantly. Post-incentive yield normalization is a known risk that could trigger TVL flight.

**This is NOT a Ponzi. But it is a credit protocol with real-world credit risk, dressed in DeFi clothing.**

---

## 6. Red Flags Register

| # | Flag | Severity | Evidence | Why It Matters |
|---|------|----------|----------|----------------|
| 1 | MetaStreet predecessor collapsed (<1% market share) | 🟠 HIGH | NFT lending market data; DeFiLlama market share | Team pivoted from failed product. Marketing frames this as "proof of concept." It is not. |
| 2 | 90% of CHIP token allocation undisclosed | 🔴 CRITICAL | ICOAnalytics, CryptoRank, ICODrops all note missing data | Retail cannot assess insider supply overhang. Classic information asymmetry exploitation. |
| 3 | No seed/private round pricing disclosed | 🔴 CRITICAL | ICOAnalytics explicitly flags absence | Standard VC deals imply seed at ~$0.003–0.01. If VC cost basis is 3–10x below retail, dump pressure is structurally embedded. |
| 4 | 100% TGE unlock for public sale | 🟠 HIGH | CoinList ICO terms | Unusual. Creates immediate sell pressure at listing. Devastating if insiders dump simultaneously. |
| 5 | CALIBER legal framework unproven in court | 🔴 CRITICAL | Protocol docs; Stablecoin Insider; Stablewatch | Entire collateral model rests on UCC Article 7 digital title transfers never tested in a real default. |
| 6 | GPU depreciation 20–50% annually | 🟠 HIGH | Stablecoin Insider risk analysis; multiple analyst sources | Multi-year loans with 3–5yr amortization = collateral could be worth 50–90% less at maturity. |
| 7 | Physical liquidation costs ~30% of asset value | 🟠 HIGH | Stablewatch deep dive | ITAD firms charge ~30% gross sale price. Net recovery in a default could be 40–50 cents on the dollar. |
| 8 | Zero Reddit community discussion for $658M TVL protocol | 🟡 MEDIUM | Search confirmed: 0 posts found | Anomalous. May indicate TVL concentrated among institutional/insider depositors, not organic retail. |
| 9 | Single audit firm (Cantina) for all audits | 🟡 MEDIUM | docs.usd.ai/technical-overview/audits | No competitive audit contest, no second-opinion firm. Audit firm diversity is best practice at this scale. |
| 10 | DoS on redemption queue left unresolved | 🟡 MEDIUM | Cantina audit May 2025, Low severity, Acknowledged not Fixed | Known attack vector for blocking specific users from redemptions remains live in production. |
| 11 | Bankless and Arbitrum coverage have financial conflicts | 🟡 MEDIUM | Arbitrum is listed investor; Bankless sponsored content history | Positive coverage from financially interested parties cannot be weighted equally to independent journalism. |
| 12 | Sharon AI $500M facility: counterparty concentration risk | 🟡 MEDIUM | The Block (Jan 2026); BusinessWire | OTC-listed Australian neocloud with limited disclosure. Single-counterparty concentration at massive scale. |
| 13 | "Former Deutsche Bank banker" credential unverified | 🟡 MEDIUM | Stablecoin Insider review; no independent corroboration | Could be accurate. Could be marketing inflation. Cannot verify without primary source confirmation. |
| 14 | PYUSD concentration risk | 🟡 MEDIUM | The Defiant; on-chain data | >43% of USDai deposits are PYUSD. If PayPal changes terms or faces regulatory action, USDai loses its largest deposit base. |
| 15 | No Rekt News coverage despite $658M TVL | 🟢 LOW (ambiguous) | Search confirmed absence | Either no exploits (positive) or insufficient scrutiny from security researchers yet (neutral-negative). |

---

## 7. Comparative Analysis

| Pattern | Anchor/Terra | Olympus DAO | Celsius | USD.AI |
|---------|-------------|-------------|---------|--------|
| Identified yield source | ❌ No | ❌ No | ⚠️ Partially | ✅ Yes |
| Sustainable base mechanism | ❌ No | ❌ No | ⚠️ Partially | ⚠️ Partially |
| Collateral backing | ❌ LUNA (circular) | ❌ OHM (circular) | ⚠️ User deposits | ✅ GPUs (real) |
| Legal enforcement untested | N/A | N/A | ❌ Revealed in bankruptcy | 🔴 Yes |
| Tokenomics opacity | 🟢 Low | 🟢 Low | N/A | 🔴 High |
| Institutional backing | ⚠️ Partially | ❌ No | ✅ Yes (misleading) | ✅ Yes |
| Concentration risk | 🔴 High | 🟡 Medium | 🔴 High | 🟠 High |

**Closest failed comparator:** Maple Finance's undercollateralized lending period (2022), when institutional borrower defaults (Orthogonal Trading) caused lender losses. USD.AI's FiLo (First Loss Curator) model is designed to prevent this, but it has not been stress-tested in a real default event.

---

## 8. Unresolved Questions

The following could NOT be determined and require additional investigation:

1. **Full tokenomics table:** What % goes to team, VC, ecosystem, treasury? What are vesting cliff/linear periods? *This is the most critical unresolved question for ICO participants.*
2. **Seed/Series A token pricing:** At what price did Framework, Dragonfly, YZi Labs receive CHIP tokens? The implied markup over retail is unknown.
3. **LTV ratios on GPU loans:** What % of GPU value can be borrowed? What triggers a margin call? Not found in any public source.
4. **Sharon AI creditworthiness:** An OTC-listed Australian neocloud is taking a $500M facility. Revenue, profitability, and existing debt are not publicly assessable.
5. **GitHub codebase verification:** No direct code inspection performed. Fork status, commit authenticity, contributor identity unverified.
6. **Contract admin key structure:** Who controls the blacklist function? Is there a timelock? How many multisig signers? Not confirmed from available sources.
7. **CALIBER legal stress test:** Has any borrower defaulted yet? If yes, what happened? If no, the enforcement mechanism is entirely theoretical at scale.
8. **Audited vs. deployed bytecode match:** Not verified. Contract address found needs direct Etherscan/Arbiscan confirmation.
9. **Team's actual GitHub profiles:** Contributor identities and prior project history not verified.
10. **MetaStreet → USD.AI continuity:** Was the pivot a full team continuation, or did key engineers leave when MetaStreet failed?

---

## Final Verdict

**USD.AI is not a rug pull.** It is a genuinely novel credit protocol with real institutional backing, real audits, and a real product thesis. The core innovation — tokenizing GPU hardware under UCC law to enable on-chain lending — is legitimately interesting and addresses a real market gap.

**However, the CHIP token ICO is a separate matter.** Retail participants at $0.03 / $300M FDV are investing in a governance token with:
- Unknown insider supply overhang (90% allocation undisclosed)
- Unknown seed-round markup (VC cost basis likely far below $0.03)
- 100% TGE unlock for public purchasers
- Governance utility entirely dependent on protocol growth

**The protocol itself:** Treat as high-risk institutional credit infrastructure. The risks are real-world credit risks — GPU market collapse, borrower default cascade, legal framework failure — not crypto-native scam risks. It can fail via market forces, not by a team disappearing overnight.

**The CHIP token:** Approach with extreme caution until full tokenomics disclosure. Do not allocate based on current public information. Demand the complete supply breakdown before committing capital.

---

## Sources

| Source | URL |
|--------|-----|
| RootData — USD.AI Profile | https://www.rootdata.com/Projects/detail/usd.ai?k=MTY1MDA%3D |
| Cantina Audit Portfolio (USDai Stablecoin) | https://cantina.xyz/portfolio/23dbab18-bbea-4184-8eb5-584faaf80903 |
| Cantina Bug Bounty | https://cantina.xyz/bounties/32e64f2e-5f01-4a0b-bbe3-76f32c17b99f |
| docs.usd.ai — Audits | https://docs.usd.ai/technical-overview/audits |
| Immunefi Bug Bounty | https://immunefi.com/bug-bounty/metastreet/information/ |
| The Block — Sharon AI $500M Facility | https://www.theblock.co/post/386759/onchain-lending-protocol-usdai-approves-500-million-loan-australian-ai-startup |
| CoinDesk — GPU Loan Bridges DeFi and AI | https://www.coindesk.com/markets/2025/10/24/usdai-bridges-defi-and-ai-by-turning-stablecoins-into-loans-for-nvidia-gpus |
| Stablewatch — GPU-Backed Credit Deep Dive | https://www.stablewatch.io/blog/usd-ai-deep-dive |
| ICO Analytics — USD.AI Token Sale | https://icoanalytics.org/projects/usd-ai-permian-labs/ |
| CryptoRank — CHIP ICO | https://cryptorank.io/ico/usd-ai |
| ICO Drops — USD.AI | https://icodrops.com/usd-ai/ |
| The Defiant — PYUSD Supply Crosses $4B | https://thedefiant.io/news/tradfi-and-fintech/paypal-pyusd-supply-crosses-usd4-billion |
| The Defiant — USDAI Token Launch | https://thedefiant.io/news/defi/usdai-gears-up-for-token-launch-and-airdrop |
| NFT Lending Market Crashes 97% | https://cryptonews.com/news/nft-lending-market-crashes-97-as-users-and-loan-sizes-plummet/ |
| DefiLlama — USD AI Protocol | https://defillama.com/protocol/usd-ai |
| Arbitrum Blog — USD.AI InfraFi | https://blog.arbitrum.io/usd-ai-accessible-ai-infra-financing/ |
| BusinessWire — Sharon AI $500M | https://www.businesswire.com/news/home/20260122439371/en/Sharon-AI-Secures-up-to-US$500M-Debt-Facility-from-USD.AI-to-Support-GPU-Backed-AI-Infrastructure-Expansion-in-Australia-and-Asia-Pacific |
| PANews — Coinbase Ventures Investment | https://www.panewslab.com/en/articles/a2c4d54c-ddce-4978-b464-723ba839816f |
| CoinList — USD.AI Token Sale Announcement | https://blog.coinlist.co/announcing-the-usd-ai-token-sale-on-coinlist/ |
| Bankless — Earning from GPUs with USDai | https://www.bankless.com/read/earning-from-gpus-with-usdai |
| RWA.xyz — USDai | https://app.rwa.xyz/assets/USDai |
