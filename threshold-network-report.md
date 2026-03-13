# Threshold Network (T / tBTC) — Adversarial Due Diligence Report
**Research Date:** 2026-03-13
**Analyst:** DeFi Adversarial Research Agent
**Framework:** Maximum Adversity, Guilty Until Proven Otherwise

---

## ⚠️ PRE-REPORT ALERT

> **One item demands immediate framing before the full report:** The August 2024 #saveWBTC proposal would have minted 1.655 billion new T tokens (a 15% supply dilution) and transferred them to BitGo — giving a single corporate entity more T tokens than typically participate in DAO governance votes. BitGo's own CEO publicly stated Threshold's motives were self-interested price speculation. This proposal did **not** appear to pass, but its existence is architecturally revealing: Threshold leadership was willing to consider a dilutive corporate deal that could have handed network governance to a custodian. This pattern warrants emphasis throughout this report.

---

## 1. Executive Summary

**Verdict:** Threshold Network is a **legitimate, long-running protocol with a verifiable team and genuine technical depth**, but it carries **significant structural risks** that distinguish it sharply from marketing materials. The project is not a rug pull. It is instead a cautionary case of a decentralized ideal compromised by governance centralization, a bridge product with meaningful (if not catastrophic) attack surfaces, persistent token price collapse (-97% from ATH), and a deliberate pivot away from multiple products that appear to have failed. Confidence in this verdict: **High**.

**Top 3 Risks:**
1. **Governance centralization:** A 5/6-of-9 multisig committee (Threshold Council) retains unilateral, delay-free control over Bridge, Bank, and tBTC Vault contract upgrades. The top 6 voters control over 50% of governance power. On-chain DAO governance has not yet replaced this multisig structure despite years of promises.
2. **Bridge custody architecture under stress:** The 51-of-100 GG18 threshold ECDSA model cannot attribute misbehaving signers, is vulnerable to signing abort attacks by a single malicious party, and relies on a single Curve pool EMA for price discovery — a manipulable oracle. The top 18 node operators control 51.1% of stake.
3. **Product abandonment pattern / financial fragility:** thUSD is in "maintenance mode." TACo is being spun out. The protocol is now a one-product company (tBTC) with $1.4M annualized revenue, a ~$72M market cap, a team of ~10 people, and a T token trading -97% from its all-time high near an all-time low. A 40% probability of financial distress is flagged by independent quantitative models.

**Top 3 Positive Signals:**
1. **Zero security exploits in ~5 years of operation** across $4.6B in cumulative bridge volume — the strongest empirical signal available for a bridge protocol.
2. **Verified, credible team** with decade-long public track record. Thesis portfolio includes a Nasdaq-listed company (Fold), VC backing from a16z, Polychain, Pantera, and Multicoin.
3. **Responsible fiscal governance:** Inflation (500M T/year, ~$12.5M annual cost) was eliminated via community vote (TIP-092/TIP-100, Feb 2025), followed by a DAO-approved buyback program — evidence of genuine community-driven cost discipline.

---

## 2. Team Assessment

### 2.1 Matt Luongo — Keep Network / Thesis Co-Founder, CEO
**Role:** Co-founder of Thesis (the venture studio behind tBTC, Keep, Mezo, Fold, Acre, Taho)

**Verified Claims:**
- BS Computer Science, Georgia Institute of Technology, 2009 (verifiable via LinkedIn, press profiles)
- Founded Fold (Bitcoin rewards app) in 2014 — Fold went public on Nasdaq in February 2025. This is a hard, verifiable, publicly-reported milestone that anchors legitimacy.
- GitHub: [github.com/mhluongo](https://github.com/mhluongo) — 55 public repos, affiliated with @thesis, @keep-network, @threshold-network. Pinned repos include threshold-network/keep-core (Go, 138 stars), the archived keep-network/tbtc (210 stars), and tahowallet/extension (TypeScript, 3.2k stars). Activity reflects genuine engineering commitment across multiple years.
- Thesis raised a $21M Series A in 2021; Mezo (Thesis product) raised $30M led by Pantera Capital + Multicoin in 2024.
- Active on X as [@mhluongo](https://x.com/mhluongo). No patterns of project-hopping, shilling, or abandoned projects.

**Unverified / Unconfirmed:**
- No evidence of prior work on failed or fraudulent crypto projects.
- Prior roles (Agency Spotter tech lead, Insightpool advisor) are soft-verifiable but not critical risk vectors.

**Red Flags:** None material. Luongo is one of the more credible founder profiles in DeFi.

---

### 2.2 MacLane Wilkison — NuCypher Co-Founder
**Role:** Co-founder of NuCypher; proposer of #saveWBTC; currently listed as CEO of Threshold Network

**Verified Claims:**
- UNC Kenan-Flagler Business School (verifiable)
- Former investment banker at Morgan Stanley (TMT M&A) — verifiable via LinkedIn, press profiles, independent coverage
- Certified Information Systems Security Professional (CISSP), Chartered Financial Analyst (CFA), Financial Risk Manager (FRM) — three professional credentials that are hard to fake and independently verifiable
- NuCypher founded 2015, backed by Y Combinator (S16) and Polychain Capital ($4.4M venture round, 2017) — independently documented in YC's public company list and The Block/Crunchbase records
- Co-designed the "KEANU" on-chain merger with Keep Network — covered independently by Messari, Decrypt, The Block

**Contextual Concern (not a red flag, but relevant):**
- The #saveWBTC proposal (August 2024) originated from Wilkison. It called for minting 1.655B new T tokens (~15% dilution) to acquire BitGo's WBTC product and give BitGo a controlling governance stake in Threshold. BitGo's CEO Mike Belshe publicly accused Wilkison's team of purely self-interested motives: *"They've even said publicly that if they had all of Wrapped Bitcoin's market share, their token's value would be 35 times higher."* The proposal did not appear to be implemented. This is rated **MEDIUM** risk — it reflects potential willingness to trade decentralization for market position, but it was a governance proposal, not unilateral action.

**Unverified:**
- Current day-to-day operational role vs. Threshold Labs leadership (Callan Sarre listed as CPO of Threshold Labs)

---

### 2.3 Supporting Team
**Callan "Sap" Sarre** — Co-Founder and CPO of Threshold Labs. Limited independent verification available. No red flags identified in available sources.

**Corbin Pon** — Keep Network co-founder alongside Luongo. Also a Fold co-founder. Less visible post-merger. No red flags.

**Ethan Hassall** — Head of Business Development. No independent verification conducted; limited public footprint.

**New hires (Nov 2025):** Lev A. (12 years experience, crypto since 2018), Miquel C. (PhD in blockchain protocols, Rust/Solidity specialist), José Orlicki (integration development). These appear to be genuine technical hires.

**Team Size Alert:** A 10-person team managing a Bitcoin bridge with $785M peak TVL, operating across 8+ chains, with an active bug bounty program, is **dangerously understaffed**. This is a systemic risk, not a team competence criticism.

---

## 3. Third-Party Consensus

### 3.1 Independent Analyst Coverage

**LlamaRisk (Collateral Risk Assessment — most adversarial independent analysis found):**
This is the most rigorous independent analysis identified. Key findings:
- Governance is effectively controlled by a 6-of-9 multisig (now restructured to 5-of-9 under TIP-103), with NO on-chain governance delay on the Bridge upgrade function. The `onlyOwner` modifier on bridge upgrades allows changes without community time-lock input.
- Top 6 voters control >50% of voting power; "a small set of addresses actively voting" with "little no votes" against proposals
- Oracle dependency: single Curve pool EMA for tBTC price — high manipulation risk if liquidity migrates
- No Terms of Service or OFAC compliance documentation
- 30% of tBTC supply concentrated as crvUSD collateral = systemic risk
- GG18 signing scheme cannot identify misbehaving signers
- Treasury burn risk if revenues don't scale faster than operating costs
- Rating source: [LlamaRisk Collateral Assessment](https://llamarisk.com/research/collateral-risk-tbtc)

**Messari:** Covered the merger in depth as a historical case study. No adverse findings on team integrity. Coverage positions tBTC as a genuine decentralization alternative to WBTC.

**The Defiant:** Published a feature-length piece on tBTC's institutional ambitions (Feb 2025 era). Tone was largely positive/supportive. Note that The Defiant's coverage often includes sponsored or partnership content — this specific piece should be weighted as **partially promotional**.

**Rekt News:** No dedicated coverage found. Absence of Rekt coverage is actually modestly positive — it suggests no major exploits or scam behavior that would attract their investigative journalism.

**DL News:** No specific coverage found.

**Gate.com / Independent Collateral Risk Reports:** Echoed LlamaRisk concerns around oracle dependency, governance centralization, and GG18 signing limitations.

### 3.2 Audit and Security Assessment

| Audit | Date | Auditor | Verdict |
|---|---|---|---|
| Staking contracts, T token, vending machine | Nov 2021 | ChainSecurity | Issues addressed |
| Vending machine | Nov 2021 | CertiK | Issues addressed |
| tBTC Bridge v2 core contracts | Sep 2022 | Least Authority | Issues found; most addressed |
| Solana tBTC Bridge | Aug 2023 | Least Authority | Issues found; most addressed |
| Base tBTC integration | Apr 2024 | (unspecified in sources) | Completed |
| StarkNet tBTC integration | Apr 2025 | (unspecified in sources) | Completed |

**Key Unresolved Finding:** Least Authority's audit flagged that the epoch timestamp will overflow `uint32` on February 7, 2106. Threshold chose **not** to fix this to save gas. While this is a theoretical risk 80 years away, it reflects a pattern of accepting risk for efficiency gains.

**Bug Bounty:** Immunefi program active since April 2023, last updated November 2025. Maximum payout: $500,000. A $50,000 bounty was paid to whitehat researcher "Kayaba" in August 2023 for a Bitcoin transaction malleability issue — the bug was ultimately non-exploitable but the responsible disclosure and payment are positive signals.

**Critical Gap:** The 2024 Base integration and 2025 StarkNet audit auditor names are not specified in public documentation. This should be independently verified before any significant capital commitment to tBTC on these chains.

**Assessment:** The audited scope is meaningful and the auditor roster (Least Authority, ChainSecurity) is credible. However, the absence of published auditor names for cross-chain extensions is a transparency gap.

### 3.3 Community Sentiment

- **No rug pull or scam allegations found** in any independent source. This is meaningful after searching across multiple adversarial query formulations.
- Reddit-specific criticism threads were not indexable via web search — this limits confidence in community sentiment assessment.
- Governance forum shows active participation but concentration: proposals receive "little no votes," and major proposals like TIP-103 (restructuring $millions in treasury authority) appear to pass with minimal opposition. This is either a sign of genuine community consensus or dangerous governance apathy — the data does not distinguish clearly.
- The #saveWBTC proposal sparked substantive community debate, with a notable concern raised by a community member that the BitGo token grant "would end up transferring more tokens to BitGo than generally participate in Threshold Network DAO votes." This concern was independently echoed — rating it as a legitimate structural governance red flag.

---

## 4. On-Chain Findings

### 4.1 T Token Contract
- **Contract Address (Ethereum):** `0xCdF7028ceAB81fA0C6971208e83fa7872994beE5`
- **Source verified:** Yes, on Etherscan
- **Standard:** ERC-20 with EIP-712 permit/delegation (`delegateBySig`)
- **License:** GPL-3.0-or-later
- **Solidity version:** 0.8.9
- **Extensions:** `ERC20WithPermit`, `MisfundRecovery`, `Checkpoints`
- **Total Supply:** ~11.155 billion T (includes inflation emissions pre-TIP-092)
- **Holders:** ~9,164 unique addresses (relatively thin distribution for a $72M market cap asset)
- **Price:** ~$0.0065 (near all-time low of $0.006101; ATH was $0.2269)
- **Market cap:** ~$72M

**Distribution:**
- 4.5B T: Legacy NU holders (via vending machine)
- 4.5B T: Legacy KEEP holders (via vending machine)
- 1.0B T: Threshold DAO Treasury
- ~+155M T: Inflation emissions (pre-TIP-092, ~500M/year × partial years)

**Token Staking Contract:** `0x01B67b1194C75264d06F808A921228a95C765dd7`

**Governance Concern:** ~28% of T supply locked in staking contracts; "significant share on centralized exchanges." Top 6 voters control >50% of total voting power — confirmed by LlamaRisk analysis. Specific wallet addresses were not obtainable due to Etherscan 403 blocking the holders page; this gap is declared.

### 4.2 tBTC v2 Contract
- **Contract Address:** `0x18084fba666a33d37592fa2633fd49a74dd93a88` (Ethereum)
- **Architecture:** Three core contracts — Bank (non-upgradeable), Bridge (upgradeable proxy), tBTC Vault (upgradeable proxy)
- **Critical finding:** The Bridge contract uses a Transparent Upgradeable Proxy. The `onlyOwner` modifier allows bridge address upgrades **with no governance delay** — the Council can modify core bridge logic instantly without community time-lock protection. The Bank (which holds deposited BTC) is non-upgradeable, which mitigates the worst-case scenario.

### 4.3 TVL and Supply
- **Peak TVL:** ~$806M (October 2025, ~6,500 BTC)
- **Current supply (Q4 2025 end):** ~5,900 tBTC
- **Cumulative bridge volume:** 32,000 BTC (~$2.7B at current prices); $4.6B cumulative when adjusted for price at time of transaction
- **DeFi deployment:** ~4,900 BTC actively deployed in DeFi (up 65% YoY) — suggests genuine utility, not just idle bridging
- **WBTC comparison:** tBTC ~$566M TVL vs. WBTC ~$7.8B — tBTC holds roughly 7% of the tokenized BTC market

### 4.4 Revenue and Treasury
- **Annualized protocol revenue:** $1.4M run rate (0.2% redemption fee; minting fees currently waived)
- **Treasury (post-TIP-103):** ~$420M T tokens (~$7M market value) + $8-9M in reserve assets (tBTC, ETH, stablecoins)
- **Operational runway:** ~23 months of stablecoin obligations funded
- **Annual costs (post-restructuring):** ~$2.8M protocol and incentives
- **Buyback completed:** ~30M T tokens purchased for 5.8 tBTC (modest but symbolic)
- **Key risk:** Revenue is driven entirely by redemption flow, not mint fees (waived). If BTC bridging velocity slows, revenue collapses faster than TVL metrics suggest.

### 4.5 Transaction Pattern Concerns
- **30% of tBTC supply concentrated in crvUSD collateral** — significant systemic risk. A Curve or crvUSD exploit would create cascading liquidation pressure on tBTC.
- **Wormhole TokenBridge dependency:** A significant portion of tBTC supply is bridged via Wormhole — adding another third-party bridge risk layer.
- **Oracle:** Single Curve pool EMA for tBTC price. If tBTC/WBTC liquidity migrates off this pool, the price feed becomes unreliable and exploitable.

---

## 5. Red Flags Register

| # | Flag | Severity | Evidence | Why It Matters |
|---|---|---|---|---|
| 1 | **Bridge upgrades executable with no time-lock** | CRITICAL | LlamaRisk: `onlyOwner` modifier on Bridge upgrade, no governance delay | Council could modify bridge logic instantly with no community recourse |
| 2 | **5/6-of-9 multisig controls protocol operations** | HIGH | TIP-103 restructuring, LlamaRisk governance review | Effective centralization despite DAO framing; ~9 humans hold operational keys |
| 3 | **Top 6 voters control >50% governance power** | HIGH | LlamaRisk: empirical on-chain voting analysis | Effectively plutocratic governance; small set can pass any proposal |
| 4 | **GG18 threshold ECDSA cannot attribute misbehaving signers** | HIGH | Least Authority audit; tBTC security model docs | A single malicious signer can abort signing indefinitely with no accountability |
| 5 | **Oracle: Single Curve pool EMA dependency** | HIGH | LlamaRisk; gate.com collateral review | If liquidity migrates, price feed becomes manipulable; no Chainlink price feed |
| 6 | **30% of tBTC supply as crvUSD collateral** | HIGH | LlamaRisk | Concentration + systemic risk; Curve exploit = tBTC forced selling |
| 7 | **#saveWBTC proposal: 15% token dilution for corporate deal** | HIGH | Community forum, CryptoSlate, Protos, The Block coverage | Willingness to dilute 1.655B T and hand governance control to BitGo; self-interest framing by BitGo CEO |
| 8 | **Top 18 node operators control 51.1% of stake** | MEDIUM | LlamaRisk node concentration analysis | Mitigated by Beta Staker restrictions now, but concentration risk as network scales |
| 9 | **T token trading -97% from ATH, near all-time low** | MEDIUM | CoinGecko price data | Severe token value destruction; holder confidence erosion; governance participation may decline further |
| 10 | **~10-person team managing $800M peak TVL bridge** | MEDIUM | Threshold blog (Nov 2025 team updates) | Operational risk: insufficient staffing for critical Bitcoin bridge infrastructure |
| 11 | **thUSD put in "maintenance mode" / TACo being spun out** | MEDIUM | TIP-102, TIP-103 governance decisions | Pattern of product abandonment; protocol is now entirely dependent on tBTC single-product bet |
| 12 | **No Terms of Service or OFAC compliance documentation** | MEDIUM | LlamaRisk legal/compliance review | Regulatory exposure; liability gap for institutional users |
| 13 | **Uint32 timestamp overflow in 2106 — accepted unfixed** | LOW | Least Authority audit finding | Reflects acceptance of known technical risk for gas efficiency; precedent-setting attitude |
| 14 | **Audit details missing for Base (2024) and StarkNet (2025)** | LOW | Review of public audit documentation | Auditor names not specified for two chain extensions; limits independent verification |
| 15 | **KEEP community only 78% approval for merger (vs. 100% NU)** | LOW | Messari merger analysis, Decrypt coverage | Historical record of meaningful internal dissent; merger was contentious, not unanimous |
| 16 | **40% financial distress probability (quantitative model)** | LOW | Macroaxis quantitative model | Model-derived, not fundamental analysis; but reinforces thin revenue vs. operational cost picture |

---

## 6. Unresolved Questions

1. **Who specifically are the 5-of-9 Threshold Committee multisig signers, and what are their wallet addresses?** Public documentation does not clearly list individual signer identities or confirm separation of key custody. Critical for assessing real decentralization.

2. **What is the actual token holder concentration?** Etherscan's holder page returned 403 during research. Top holders (beyond known contract addresses) and their percentage shares are **unverified** in this report.

3. **Was the #saveWBTC proposal formally voted down, or did it simply die in forum discussion?** Evidence suggests it did not proceed to a Snapshot vote, but the formal disposition is unclear.

4. **What are the names of auditors for the Base (April 2024) and StarkNet (April 2025) chain integrations?** Not specified in publicly available documentation.

5. **What is the Beta Staker permissioning status?** tBTC's "controlled rollout" currently restricts who can run minter/guardian roles. The timeline and criteria for full permissionlessness are not clearly documented publicly.

6. **What is TACo's actual revenue and adoption?** TACo is being transitioned to an independent network. Its commercial traction (paying developers, ~120 nodes, ~$80M economic security) is stated but not independently verified via on-chain data.

7. **Wormhole TokenBridge exposure:** What percentage of tBTC supply is currently bridged via Wormhole and exposed to Wormhole's smart contract risks?

8. **FROST/ROAST migration timeline:** The GG18 → FROST/ROAST upgrade is described as "in development" but no concrete deployment timeline has been found. Until deployed, the signing attributability gap remains open.

---

## 7. Comparative Analysis

### 7.1 Bridge Protocol Risk Patterns
tBTC is notably different from the classic bridge rug pull template (Ronin, Wormhole, Nomad exploits). Those failures involved: (a) small/anonymous multisigs with concentrated key control, (b) no audits or insufficient audits, (c) no bug bounty programs, (d) rapid TVL accumulation without proportional security investment. tBTC exhibits **none** of these patterns.

However, tBTC shares structural risk with Multichain's collapse pattern: **operational single-points-of-failure masked by decentralization marketing**. Multichain was not a rug pull — it collapsed because a small number of people held operational keys and one of them was arrested. Threshold's 5-of-9 multisig with unclear signer identities represents a non-trivial Multichain-adjacency risk.

### 7.2 Tokenomics Sustainability
**Pre-TIP-092 (legacy):** Ponzi-adjacent. 15% staker yield funded by 500M T/year emission (~$12.5M/year at peak) while generating ~$223K/year in fees (October 2023 figures). Classic "yield from inflation" structural insolvency.

**Post-TIP-092 (current):** Materially improved. Inflation stopped. Revenue ($1.4M annualized) vs. operating costs (~$2.8M/year). Still not self-sustaining on revenue alone — requires treasury drawdown. The buyback program is symbolic at current scale (30M T for 5.8 tBTC ≈ trivial relative to 11B supply).

**Verdict:** Tokenomics went from unsustainable to transitional. The bet is that tBTC supply growth drives fee revenue toward profitability. At current trajectory (27% YoY supply growth, $1.4M revenue run rate growing 30% QoQ), the model could reach break-even within 12-24 months — but it requires continued TVL growth in a volatile market.

### 7.3 Yield Source Verification
tBTC's value proposition is straightforward and verifiable: 0.2% redemption fee on BTC bridge outflows. **This is a real, on-chain, fee-based revenue model** — not circular, not Ponzi-dependent. It is simply too small at current scale to fund operations without treasury support.

---

## 8. Final Risk Matrix

| Category | Rating | Notes |
|---|---|---|
| Team Integrity | ✅ LOW RISK | Decade-long verifiable track record, Nasdaq-listed portfolio company |
| Smart Contract Security | 🟡 MEDIUM RISK | Zero exploits in 5 years, but GG18 gaps and bridge upgrade without time-lock remain |
| Governance Centralization | 🔴 HIGH RISK | 5/6-of-9 multisig, top 6 voters control majority, no on-chain governance yet |
| Token Economics | 🟡 MEDIUM RISK | Inflation stopped, buyback launched, but T at -97% ATH and revenue below costs |
| Bridge Architecture | 🟡 MEDIUM RISK | Better than single-custodian alternatives; real risks in oracle, concentration, GG18 |
| Custody Risk (Bitcoin) | 🟡 MEDIUM RISK | 51/100 threshold ECDSA is theoretically sound; no historical breach |
| Regulatory/Legal | 🟡 MEDIUM RISK | No ToS, no OFAC documentation, unclear legal jurisdiction |
| Operational Risk | 🟡 MEDIUM RISK | 10-person team for multi-chain Bitcoin bridge is understaffed |
| Exit Scam Probability | ✅ VERY LOW | Open-source, audited, long track record, reputable investors, Nasdaq exposure |

---

## 9. Conclusions

Threshold Network is **not a scam**. The team is real, experienced, and has more accountable public footprint than 95% of DeFi projects. tBTC's five-year clean security record is empirically impressive.

However, **"not a scam" and "safe to use or invest in" are different claims.** The structural risks here are genuine:

- The governance architecture is a **6/9 multisig with bridge upgrade powers and no time-lock** — this is a centralized control system operating under decentralized branding.
- The T token has **destroyed -97% of value** from its ATH and trades near its all-time low. This is not primarily a market condition — it reflects fundamental tokenomics design flaws (inflation) that took until 2025 to fix.
- The protocol is executing a **high-stakes single-product bet** (tBTC) after quietly sunsetting thUSD and TACo. If tBTC stalls, there is no fallback.
- The #saveWBTC episode revealed leadership's **willingness to dilute token holders and cede governance for market position** when opportunistically motivated.

For users **bridging BTC:** The risk is meaningfully lower than centralized alternatives like WBTC (pre-BitGo/Sun restructuring). The 51-of-100 random signer model with zero historical exploits is legitimately more trust-minimized. Accept the oracle risk, the GG18 gap, and the Council's upgrade powers as real — but bounded — risks.

For T token **investors:** You are buying a governance token in a protocol that generated $1.4M in annualized revenue with an $11B token supply and a market cap of ~$72M. The buyback program is real but trivially small. The bet requires sustained BTC price appreciation + tBTC market share growth. High-risk, speculative, not suitable for size positions.

---

*Sources consulted: Etherscan, GitHub (mhluongo), LlamaRisk Collateral Assessment, Messari, The Block, Decrypt, CryptoSlate, Protos, The Defiant, Gate.com Collateral Risk Report, Threshold Network governance forum (TIP-092, TIP-103), tBTC security model documentation, Least Authority audit summaries, Immunefi bug bounty page, CoinGecko, DeFiLlama, IQ.wiki, Macroaxis, ChainSecurity audit announcement.*
