# Maple Finance — Adversarial Due Diligence Report

**Research Date:** February 24, 2026
**Investigator Stance:** Guilty until proven innocent
**Confidence Rating Key:**
- `High` = independently verifiable on-chain / multiple sources
- `Medium` = corroborated but incomplete
- `Low` = single source or unverifiable

---

## Table of Contents

1. [Executive Summary](#1-executive-summary)
2. [Team Assessment](#2-team-assessment)
3. [Third-Party Intelligence](#3-third-party-intelligence)
4. [On-Chain Findings](#4-on-chain-findings)
5. [Comparative Analysis](#5-comparative-analysis)
6. [Red Flags Register](#6-red-flags-register)
7. [Unresolved Questions](#7-unresolved-questions)
8. [Appendix: Subagent Accuracy Assessment](#8-appendix-subagent-accuracy-assessment)

---

## 1. Executive Summary

**Verdict (Medium-High Confidence):** Maple Finance is a real, operating DeFi protocol with a doxxed team and verifiable on-chain history — it is **not a rug pull or exit scam**. However, it carries several structural risks that are not adequately surfaced in its own marketing: an undercollateralized lending model that **catastrophically failed lenders in 2022** (80% loss in one pool), a **confirmed active lawsuit** involving allegations of trade secret theft and breach of exclusivity agreements, a **token migration that stranded retail investors** through alleged deadline manipulation, and **deep legacy entanglement** with failed entities (Alameda Research, Orthogonal Trading). The 2024–2025 recovery is real but its durability depends on market conditions and institutional trust that has been damaged before.

### Top 3 Risks

1. **Structural credit risk** — Undercollateralized/institutional lending is inherently opaque; lenders lost up to 80% in one pool in 2022 with no on-chain recourse.
2. **Active litigation** — Core Foundation obtained a court injunction against Maple Finance (October 2025) for alleged breach of exclusivity, misuse of confidential information, and potential impairment to Bitcoin Yield lenders.
3. **Governance centralization and token manipulation** — The MPL→SYRUP migration with a controversial shortened deadline effectively transferred unconverted holder value into a "Syrup Strategic Fund" controlled by the team.

### Top 3 Positive Signals

1. Doxxed, professionally verifiable team with genuine TradFi credentials (National Australia Bank, PwC, ASX-listed fintech).
2. Active GitHub with 81 repositories, multiple credible third-party audits (Trail of Bits, Spearbit, Sherlock, Code4rena), and a live Immunefi bug bounty.
3. Genuine TVL recovery: $85M → $1B+ (2024–2025), $8.5B in cumulative loans originated, $25M ARR — independently trackable on DeFiLlama.

---

## 2. Team Assessment

### 2.1 Sidney Powell — CEO & Co-Founder

**Claimed:** Traditional finance background at National Australia Bank (Securitisation & Corporate Finance), Treasurer/Portfolio Manager at Angle Finance (non-bank SME lending), contributed to $3B+ in corporate bond issuance. Holds CFA certificate.

**Independently verifiable:**
- LinkedIn profile exists and is consistent with corporate registry data for Australian fintech ecosystem. ([LinkedIn](https://www.linkedin.com/in/sidneypowell/))
- Career path confirmed across multiple independent sources: **NAB (2014–2017) → Angle Finance (to 2020) → Maple Finance (CEO/Co-founder, 2020–present)**
- Featured in Bloomberg, CoinDesk, Blockworks, speaking at Greenwich Economic Forum and Consensus — consistent with a legitimate public figure with years of public record. ([GEF profile](https://www.thegeforum.com/speakers/sidney-powell))
- Twitter: [@sidbpowell](https://twitter.com/sidbpowell) — active since at least 2021, consistent persona, no pattern of project-hopping found.
- No lawsuits, regulatory actions, or deleted social media patterns found.

**Unverifiable:** Exact role and compensation at NAB; precise contribution to bond issuance figures ($3B claim comes from Maple's own marketing material).

> **Note on training-data error:** One research subagent's training data listed Powell's prior employer as Commonwealth Bank of Australia (CBA). Live web research confirmed this was incorrect — the employer is **National Australia Bank (NAB)**. This is documented as a calibration point for AI-sourced team intelligence.

**Red Flags:** None critical. Medium-confidence profile — real person, plausible history, no hidden affiliations found.

---

### 2.2 Joe Flanagan — Co-Founder & Executive Chairman

**Claimed:** CFO at Axsesstoday (ASX-listed specialist fintech), CFO managing $400M+ in debt/equity transactions including IPO, Consultant at PwC Australia, Bachelor of Accounting from Saint Louis University.

**Independently verifiable:**
- Axsesstoday is a real ASX-listed company (ticker: AXL). ([LinkedIn](https://www.linkedin.com/in/joe-flanagan-3031b796/)) ([Crunchbase](https://www.crunchbase.com/person/joe-flanagan-5019))
- PwC Australia employment is plausible and consistent with the profile but not independently confirmed through PwC records.

**Yellow flag:** Axsesstoday entered **receivership in 2019** — the same year Maple was founded. Flanagan's prior employer failed. This does not implicate him in wrongdoing, but it should be noted as an unresolved context item.

**Unverified:** Saint Louis University degree (no independent verification). PwC employment dates.

---

### 2.3 GitHub Activity Assessment

- Organization: [github.com/maple-labs](https://github.com/maple-labs) — **81 repositories**
- Key repo `maple-core-v2`: 179 commits, built using Foundry. Active development pattern.
- Code is open-source and has been audited by independent firms.
- [Token Terminal code commit metrics](https://tokenterminal.com/explorer/projects/maple-finance/metrics/code-commits) shows ongoing activity.

**Assessment:** Legitimate development activity. This is not a fork-and-rebrand. The contracts are original work, audited, and open-source.

---

## 3. Third-Party Intelligence

### 3.1 Audit Coverage — Complete Picture

| Audit | Firm / Platform | Date | Key Findings | Status |
|---|---|---|---|---|
| Core contracts | [Code4rena](https://code4rena.com/reports/2021-04-maple) | Apr 2021 | 15 vulnerabilities, **0 high-severity** | Addressed |
| V2 contracts | [Code4rena](https://code4rena.com/reports/2022-03-maple) | Mar 2022 | 2 medium (delegatecall borrower exploit vector), 8 low | Addressed (team disputed severity of one) |
| V2 pre-launch | Trail of Bits | Aug–Sep 2022 | Real bugs found (uint32 overflow, origination fee logic) | Resolved pre-launch |
| Fix review | Trail of Bits | Dec 13–14, 2022 | Verified fixes effective | Confirmed |
| Jun 2023 release | 2 unnamed auditors | Jun 2023 | Addressed pre-release | Per project claim |
| Dec 2023 release | 2 unnamed auditors | Dec 2023 | Addressed pre-release | Per project claim |
| Aug 2024 release | 2 unnamed auditors | Aug 2024 | Maple & Syrup contracts | Per project claim |
| Withdrawal Manager | Spearbit + Sherlock | Nov 2025 | Upgrade-specific | Per project claim |

**Notable Code4rena finding (Mar 2022):** A borrower could exploit the `_acceptNewTerms` `delegatecall` path in `MapleLoanInternals.sol` to propose malicious loan terms. The Maple team disputed the medium severity rating, calling it "an extreme edge case." This is a documented instance of the project pushing back on an independent auditor's severity assessment.

**Audit firm transparency gap:** The June/December 2023 and August 2024 auditors are unnamed in Maple's own documentation. "2 audits" without naming the firms cannot be independently verified.

**DeFiSafety PQR:** [Maple V2.0 reviewed on DeFiSafety](https://www.defisafety.com/app/pqrs/533) — 3 audits confirmed reviewed, corrections implemented before deployment, architecture documented. Positive process quality rating.

**Bug Bounty:** Live on [Immunefi](https://immunefi.com) — a positive signal for legitimate protocols.

---

### 3.2 Independent Media Coverage

| Source | Coverage | Tone |
|---|---|---|
| [CoinDesk Dec 2022](https://www.coindesk.com/markets/2022/12/12/maple-finances-54m-of-sour-debt-shows-risks-of-crypto-lending-without-collateral) | "$54M of Sour Debt Shows Risks of Crypto Lending Without Collateral" | Critically negative |
| [CoinDesk Sep 2023](https://www.coindesk.com/markets/2023/09/11/maple-finance-nearly-imploded-but-sid-powell-wants-to-bring-back-its-billion-dollar-plus-glory) | "Nearly Imploded, but Sid Powell Wants to Bring Back Its Billion Dollar-Plus Glory" | Acknowledged near-failure |
| [The Block](https://www.theblock.co/post/192097/maple-finance-default-orthogonal-trading) | Defaults and protocol changes | Factual, no promotional tone |
| [Blockworks](https://blockworks.co/news/maple-finance-bad-loans-immediate-defaults) | Bad loans, immediate default protocol change | Neutral/analytical |
| [DL News 2025](https://www.dlnews.com/articles/defi/maple-finance-courting-institutions-key-to-revival-ceo-says/) | Institutional lending revival | Positive framing |
| Rekt News | **No entry found** | N/A |

> **No Rekt News entry** is a mildly positive signal — Rekt News covers exploits and rugs. Maple's losses were credit defaults, not smart contract exploits. This distinction matters architecturally.

---

### 3.3 The 2022 Default Ledger — Full Record

| Borrower | Amount | Pool | Lender Impact | Cause |
|---|---|---|---|---|
| Babel Finance | $10M | Orthogonal pool | $7.9M loss (~3.8% haircut to pool) | Jun 2022, crypto market collapse |
| Auros Global | $3M USDC + 2,400 wETH (~$2.9M) | M11 pools | Partial default | FTX exposure |
| Orthogonal Trading | $31M USDC | M11 USDC pool | **~80% loss to remaining investors** | Dec 2022, FTX exposure + alleged misrepresentation |
| Orthogonal Trading | $5M wETH | M11 WETH pool | 17% loss | Dec 2022 |
| **Total bad debt** | **~$54M** | — | 66% of total outstanding loans | — |

**CRITICAL FINDING:** Lenders in the M11 USDC pool suffered approximately **80% losses**. Pool cover (the "insurance") held less than **$2M** against $31M+ in defaults — the insurance mechanism failed catastrophically.

**Structural conflict surfaced:** Orthogonal Trading was simultaneously a **Pool Delegate** (earning fees for vetting borrowers) AND a **borrower** in those same pools. The fee incentive rewarded Orthogonal for growing pool volume, not protecting lender capital. Orthogonal concealed its insolvency from Maple for over **four weeks**.

**Maple's response:** Maple 2.0 eliminated grace periods and moved to immediate defaults on trigger conditions. This is a genuine protocol improvement but does not restore lost funds to 2022 lenders.

**Alameda conflict of interest:** Alameda Research was both a **seed investor** in Maple and a **borrower** on the platform. Maple halted Alameda loans in May 2022 after identifying "key weaknesses including declining asset quality" and "an increasingly byzantine corporate structure." This decision was correct, but the conflict — an equity stakeholder also being a credit customer — was never publicly disclosed as a risk factor.

**Framework Ventures conflict:** Framework Ventures was a **seed investor** AND Framework Labs (its affiliate) was an **inaugural borrower** in the first lending pool. Same structural conflict as Alameda, undisclosed.

---

### 3.4 Community Sentiment

**Negative themes (independent sources):**
- Lenders who lost money in 2022 posted extensively about yield APYs that did not reflect actual credit risk
- Criticism that "institutional borrowers" were crypto-native firms (3AC, Celsius, Orthogonal) that were themselves overleveraged, not traditional creditworthy institutions
- Pool Delegate model: delegates earn fees for curating borrowers but lenders bear the full loss on default
- [Trustpilot](https://www.trustpilot.com/review/maple.finance): Multiple reviews citing MPL→SYRUP migration deadline manipulation, Telegram censorship, and blocked support contacts

**MPL→SYRUP migration complaints (documented):**
- Project allegedly communicated a **3-year migration window** (to 2027), then shortened it with minimal notice — conversion ended **April 30, 2025**, with only a 48-hour final extension
- Unconverted MPL transferred to a "**Syrup Strategic Fund (SSF)**" controlled by the team — a wealth transfer from retail to insiders
- Maple accused of **blocking, muting, and censoring** complainants on Telegram
- Long-term holders with no social media activity missed the window entirely with no recourse offered

---

## 4. On-Chain Findings

### 4.1 Token Contracts

| Token | Address | Max Supply | Status |
|---|---|---|---|
| Original MPL | [`0x33349b282065b0284d756f0577fb39c158f935e6`](https://etherscan.io/token/0x33349b282065b0284d756f0577fb39c158f935e6) | 10,000,000 | Migration to SYRUP complete |
| New MPL / SYRUP | [`0x1915A8dE08A92b846dF7C845e140E4b0714820bd`](https://etherscan.io/token/0x1915A8dE08A92b846dF7C845e140E4b0714820bd) | 1,000,000,000 | Active governance + staking token |

- Original MPL: **8,673 holders** on Etherscan at time of research
- SYRUP token: 100:1 conversion ratio from MPL

### 4.2 Token Distribution

| Category | Estimated Allocation | Notes |
|---|---|---|
| Seed investors | ~26% | Alameda Research, Framework Ventures, Polychain, FBG, others |
| Team/founders | ~22% | Vesting 2–4 years from 2021 launch — largely expired by 2025 |
| Token sale (public LBP) | ~5% | Only public allocation at launch |
| Ecosystem/treasury | ~30% | DAO-controlled |
| Advisors + other | ~17% | — |
| **Insider total** | **~48%** | Team + seed investors combined |

> **Red flag:** Only 5% of supply was distributed publicly at launch. ~48% insider + seed allocation with vesting mostly expired by research date creates significant sell pressure risk with no ongoing lockup.

### 4.3 TVL History

| Period | TVL | Notes |
|---|---|---|
| Peak (mid-2022) | ~$900M | Undercollateralized institutional lending boom |
| Post-FTX (Dec 2022) | ~$25M | **97% drawdown from peak** |
| Start of 2023 | ~$85M | Pivoting to RWA/secured lending |
| End of 2024 | ~$600M+ | Syrup.fi driving growth |
| Early 2025 | **$1B+** | Surpassed $1B; institutional integrations |

Source: [DeFiLlama — Maple Finance](https://defillama.com/protocol/maple-finance)

### 4.4 Business Model Evolution — The RWA Pivot

| Product | Launch | Structure | Collateral | Risk Level |
|---|---|---|---|---|
| U.S. Treasury Bill Pool | Apr 2023 | RWA / Cash Management | T-bills (off-chain custodian) | Low |
| AQRU Receivables Pool | 2023 | Trade receivables | Off-chain receivables | Medium |
| Secured Lending Pool | 2023 | Overcollateralized | BTC/ETH/SOL (>150%) | Medium |
| High Yield Secured Pool | Mar 2024 | Overcollateralized | Alt digital assets | Medium-High |
| Syrup (syrup.fi) | May 2024 | DeFi-permissionless | Overcollateralized (~170%) | Medium |

**Assessment:** The 2023–2024 pivot represents a fundamentally different risk profile from the 2021–2022 undercollateralized model. Loans at 150–170% collateralization with BTC/ETH collateral are structurally closer to Aave's model than Celsius's. However, marketing language continues to use "institutional yield" framing that obscures the legacy bad debt history. The "Drips campaign" APY boosters are incentive-driven yields, not sustainable credit spread income.

### 4.5 Smart Contract Centralization Risk

| Control | Mechanism | Duration | Risk |
|---|---|---|---|
| Proxy upgrades | MapleGlobals governor | **3-day timelock** | Medium — functional window for community response |
| Governance actions | Snapshot + on-chain execution | **2-week timelock** (DeFiSafety reviewed) | Medium |
| Emergency pause | 2-of-3 multisig | Immediate | **Centralization risk — signer identities undisclosed** |
| Protocol fees | Governor address (team multisig) | N/A | Centralized |

**Critical transparency gap:** The 2-of-3 multisig signer identities are **not publicly named in any source found**. This makes independent verification of the multisig's integrity impossible. Who controls emergency pauses and protocol upgrades is unknown to the public.

**Positive:** Timelock of 3 days (upgrades) / 2 weeks (governance) is better than the 24-48 hour figure suggested by some training-data sources. Not industry-best, but not alarm-level short.

### 4.6 Governance

- Snapshot voting with **5% circulating supply quorum** and simple majority pass rate
- Academic research explicitly names Maple Finance in studies on **governance power concentration** among lending protocols
- ~48% insider + seed allocation means early investors can dominate governance votes if coordinating
- MIP-017 (SYRUP migration deadline that stranded retail holders) was passed through this governance structure

---

## 5. Comparative Analysis

### 5.1 Maple vs. Failed CeFi Lenders

| Dimension | Celsius | Maple Finance | Assessment |
|---|---|---|---|
| Custody | Custodial — user funds held by company | Non-custodial — on-chain pool shares | **Structurally different** |
| Transparency | Zero borrower disclosure, opaque books | On-chain loan terms, partial borrower disclosure | **Maple significantly better** |
| Withdrawal freeze | CEO unilateral | Smart-contract withdrawal queues | **Maple significantly better** |
| Fund comingling | User funds commingled with operating capital | Smart contracts prevent comingling | **Maple significantly better** |
| First-loss mechanism | None | Pool Delegate staking (proved insufficient in 2022) | **Maple better but inadequate** |
| Risk disclosure | Actively misled retail as "savings" | Explicit credit risk marketing | **Maple significantly better** |
| Survival of 2022 | No — bankruptcy | Yes — 97% TVL decline but protocol continued | **Maple survived** |

**Verdict:** "Better than Celsius" is a low bar. The structural mechanics are meaningfully different. The failure mode for Maple is credit cycle contraction, not executive fraud — but lenders still lost real capital in 2022.

### 5.2 Pattern Match — Known Failed/Struggling Protocols

| Protocol | Pattern Match | Rationale |
|---|---|---|
| **TrueFi** | **MEDIUM-HIGH** | Near-identical architecture; TrueFi declined into TVL irrelevance post-2022 without catastrophic collapse |
| Goldfinch Finance | MEDIUM | Architectural twin with different borrower base (EM SMEs vs. crypto institutions); both face underwriter moral hazard |
| Clearpool | MEDIUM | Similar model; "slow bleed" TVL atrophy risk |
| Celsius Network | LOW | Custodial, fractional reserve, retail fraud — structurally different failure mode |
| Genesis Capital | LOW | Intracompany DCG contagion — different corporate structure |
| BlockFi | LOW-MEDIUM | Custodial retail yield product vs. non-custodial DeFi protocol |

> **Most accurate failure pattern: TrueFi.** The risk for Maple is not sudden collapse but gradual TVL atrophy and token value destruction as the institutional crypto credit cycle tightens. The 2024–2025 recovery defers this risk to the next bear cycle — it does not eliminate it.

### 5.3 Business Model Sustainability

**Yield source:** Real credit spread income from borrower interest payments. Not token emissions. Not circular liquidity mining. **Categorically different from a Ponzi.**

**What makes it sustainable:**
- Genuine borrower demand for on-chain institutional credit
- Overcollateralized product suite (post-2023 pivot) dramatically reduces default risk
- $25M ARR supports SYRUP buyback mechanics at current scale

**What makes it fragile:**
- Yield is highly cyclical — crypto bear markets crush borrower demand
- Pool Delegate integrity is trust-based, not contractually enforced on-chain
- RWA pools rely on off-chain custodians (T-bill holdings) — introduces custodian counterparty risk invisible on-chain
- First-loss buffer proved inadequate in 2022; no evidence the buffer has been materially increased relative to pool exposure

**Sustainability rating: 6/10** — adequate in favorable conditions, fragile under stress.

### 5.4 Regulatory Risk Assessment

**SYRUP and the Howey Test:**

| Howey Element | Present in SYRUP? | Notes |
|---|---|---|
| Investment of money | Yes | Purchase of SYRUP |
| Common enterprise | Yes | Protocol revenue shared among stakers |
| Expectation of profits | Yes | Revenue-sharing explicitly marketed |
| From the efforts of others | Yes | Pool Delegates and team drive revenue |

Revenue-sharing tokens are among the SEC's primary enforcement targets. SYRUP's explicit profit-sharing mechanics make it a **higher Howey risk than a pure governance token**.

**Confirming evidence from live research:**
- [Wealthsimple](https://help.wealthsimple.com/hc/en-ca/articles/40411589447323-Maple-Finance-SYRUP) (a regulated Canadian platform) explicitly monitors "whether SYRUP is a security and/or a derivative" as an open question
- One independent analyst states Maple's success "may depend on **temporary regulatory forbearance** rather than genuine compliance advantage" — the most accurate framing of the risk
- No public legal opinion or regulatory safe harbor disclosure found for any jurisdiction

**Comparable enforcement history:**
- BlockFi: $100M SEC settlement (2022) over yield-bearing accounts — Maple's LP pools are functionally similar
- Nexo: Regulatory action across multiple jurisdictions for yield products
- Coinbase: SEC complaint included staking services as potential unregistered securities

**Regulatory risk rating: HIGH** — Not because of active enforcement, but because the product characteristics strongly match SEC enforcement patterns and no public safe harbor analysis exists.

---

## 6. Red Flags Register

| # | Flag | Severity | Evidence | Why It Matters |
|---|---|---|---|---|
| 1 | **80% lender losses in M11 USDC pool (2022)** | CRITICAL | [CoinDesk](https://www.coindesk.com/markets/2022/12/12/maple-finances-54m-of-sour-debt-shows-risks-of-crypto-lending-without-collateral), [The Block](https://www.theblock.co/post/192097/maple-finance-default-orthogonal-trading) | Retail lenders who trusted the protocol lost most of their capital with zero on-chain recourse. Demonstrates model failure under stress. |
| 2 | **Active court injunction (Oct 2025)** | CRITICAL | [CoinDesk](https://www.coindesk.com/policy/2025/11/20/core-foundation-wins-injunction-against-maple-finance-on-alleged-confidentiality-breach), [Cryptopotato](https://cryptopotato.com/core-foundation-claims-maple-misused-confidential-data-court-says-serious-issue-to-be-tried/) | Core Foundation won injunction for alleged breach of exclusivity, misuse of confidential IP. Court ruled "serious issue to be tried." Bitcoin Yield lenders told to seek independent legal advice. $107M TVL impact. |
| 3 | **Orthogonal Trading: Pool Delegate AND Borrower** | CRITICAL | [CoinDesk](https://www.coindesk.com/markets/2022/12/05/maple-finance-severs-ties-with-orthogonal-trading-alleging-it-misrepresented-financial-position), [Unchained Crypto](https://unchainedcrypto.com/large-defi-lender-maple-finance-cuts-ties-with-insolvent-client-that-was-exposed-to-ftx/) | Orthogonal simultaneously underwrote borrower creditworthiness (earning fees) while itself being the insolvent borrower. Classic principal-agent failure. Concealed insolvency for 4+ weeks. |
| 4 | **Alameda Research: seed investor AND borrower** | HIGH | [CoinDesk Nov 2021](https://www.coindesk.com/business/2021/11/18/maple-finance-launches-first-defi-syndicated-loan-for-alameda-research), DeFiLlama funding data | Structural conflict never publicly disclosed as a risk. Alameda's collapse inflicted contagion on the platform it had equity in. |
| 5 | **Framework Ventures: seed investor AND inaugural borrower** | HIGH | Maple seed announcement, inaugural pool borrower list | Same structural conflict as Alameda — governance stakeholders also became the first credit customers. |
| 6 | **MPL→SYRUP migration deadline manipulation** | HIGH | [Trustpilot reviews](https://www.trustpilot.com/review/maple.finance), [Maple Governance Forum](https://community.maple.finance/t/request-to-reopen-mpl-syrup-conversion-for-missed-long-term-holders/604/70) | Project allegedly communicated 3-year window then shortened to ~6 months. Unconverted MPL became team-controlled "Syrup Strategic Fund." Telegram censorship of complainants documented. |
| 7 | **SYRUP regulatory tripwire (Howey Test)** | HIGH | Wealthsimple regulatory disclosure, [Vaasblock analysis](https://www.vaasblock.com/research/maple-finance-syrup-token-risks-onchain-credit-2025/) | Revenue-sharing mechanics + profit expectation = high probability of securities classification. No public legal opinion found confirming safe harbor. |
| 8 | **Pool cover mechanism failed catastrophically** | MEDIUM | [Yahoo Finance](https://finance.yahoo.com/news/maple-finances-54m-sour-debt-035326041.html) | <$2M pool cover vs. $31M+ in defaults. Maple markets risk mitigation mechanisms that proved nearly worthless under actual stress. |
| 9 | **Multisig signer identities undisclosed** | MEDIUM | Trail of Bits audit (2-of-3 multisig confirmed), no public signer list found | Cannot independently verify who controls protocol upgrades and emergency pauses. |
| 10 | **Unnamed audit firms (2023–2024)** | MEDIUM | Maple security documentation | "2 audits" for multiple releases without naming the firms is unverifiable. |
| 11 | **Axsesstoday (Flanagan's prior employer) entered receivership 2019** | LOW | ASX records | Prior employer failed the year Maple was founded. Does not implicate Flanagan but is unresolved context. |
| 12 | **5% circulating supply governance quorum** | LOW | Maple governance documentation | Low quorum combined with ~48% insider token concentration enables whale-driven governance outcomes. |
| 13 | **No ASIC/SEC regulatory clarity disclosed** | HIGH | No public legal opinions or regulatory filings found | Undercollateralized lending + revenue-sharing token in multiple jurisdictions with no public legal position is a material undisclosed risk. |

---

## 7. Unresolved Questions

These items could not be determined from available sources. They are declared as gaps — **not filled with assumptions.**

1. **Who are the 2-of-3 multisig signers?** Not found in any public source. This is the single most important unanswered operational security question. Required: Gnosis Safe UI or governance forum disclosure.

2. **Has the Core Foundation lawsuit been resolved?** The October 2025 injunction was the last data point found. Current status unknown. Bitcoin Yield lenders remain in unresolved legal exposure.

3. **What is the current SYRUP whale concentration?** Full Etherscan top-holder breakdown not retrieved. Top-10 holder % of supply unknown from this research.

4. **Were 2022 lenders ever compensated?** No evidence found of recovery distributions to M11 USDC pool lenders who suffered 80% losses. Kroll was hired to pursue Orthogonal Trading — outcome unknown.

5. **Do deployed contracts match audited code?** Not independently verified. Requires bytecode comparison against the specific git commit hash referenced in each audit report.

6. **What is the current loan-level transparency?** Borrower identities in current pools are partially disclosed but the depth of on-chain verification for the 2024–2025 pool cohort is unclear.

7. **Has ASIC or any regulator taken a formal interest in Maple Finance's Australian operations?** No action found, but also no public legal opinions found. This gap is unresolved.

8. **Can the team choose not to execute passed governance votes?** Governance is executed by the multisig, not by automatic timelock. Whether the team has delayed or declined to execute any passed votes is not confirmed in this research.

---

## 8. Appendix: Subagent Accuracy Assessment

Four research subagents were deployed in parallel but were all blocked from live web access. Their training-data outputs were reconciled against live research:

| Subagent | Accuracy | Notable Contributions | Errors Caught |
|---|---|---|---|
| Team Deep Dive | MEDIUM | General background correct | Powell's bank listed as CBA — **wrong**. Live research confirmed NAB. |
| Third-Party Intel | HIGH | Correctly identified Code4rena audits, Howey risk, and Orthogonal's dual delegate/borrower role | Consensys Diligence audit unconfirmed by live research |
| On-Chain | MEDIUM-HIGH | Correctly flagged token concentration, governance centralization, custodian risk for RWA pools | Timelock duration overstated as risk (3-day upgrade / 2-week governance timelocks confirmed — better than subagent suggested) |
| Comparative Analysis | HIGH | Nuanced TrueFi comparison, Howey analysis, competitive moat assessment all confirmed by live data | Minor factual gaps on RWA pivot timing |

> **Key methodological finding:** AI training data on team backgrounds can contain factual errors (wrong employer bank). All team claims must be live-verified against primary sources. Training-data corroboration is not independent verification.

---

## Sources

| Source | URL |
|---|---|
| CoinDesk — Maple Finance coverage | https://www.coindesk.com/tag/maple-finance |
| The Block — Orthogonal default | https://www.theblock.co/post/192097/maple-finance-default-orthogonal-trading |
| DeFiLlama — Maple Finance TVL | https://defillama.com/protocol/maple-finance |
| Trail of Bits Audit (V2) | https://resources.cryptocompare.com/asset-management/17878/1749209866979.pdf |
| DeFiSafety PQR | https://www.defisafety.com/app/pqrs/533 |
| Code4rena Apr 2021 | https://code4rena.com/reports/2021-04-maple |
| Code4rena Mar 2022 | https://code4rena.com/reports/2022-03-maple |
| Maple Governance Forum | https://community.maple.finance |
| Trustpilot Reviews | https://www.trustpilot.com/review/maple.finance |
| Core Foundation Injunction — CoinDesk | https://www.coindesk.com/policy/2025/11/20/core-foundation-wins-injunction-against-maple-finance-on-alleged-confidentiality-breach |
| Yahoo Finance — $54M Bad Debt | https://finance.yahoo.com/news/maple-finances-54m-sour-debt-035326041.html |
| Etherscan MPL Token | https://etherscan.io/token/0x33349b282065b0284d756f0577fb39c158f935e6 |
| GitHub maple-labs | https://github.com/maple-labs |
| Sidney Powell — Greenwich Economic Forum | https://www.thegeforum.com/speakers/sidney-powell |
| Wealthsimple — SYRUP regulatory disclosure | https://help.wealthsimple.com/hc/en-ca/articles/40411589447323-Maple-Finance-SYRUP |
| Vaasblock — SYRUP Risk Analysis | https://www.vaasblock.com/research/maple-finance-syrup-token-risks-onchain-credit-2025/ |
| Unchained Crypto — Orthogonal default | https://unchainedcrypto.com/large-defi-lender-maple-finance-cuts-ties-with-insolvent-client-that-was-exposed-to-ftx/ |

---

*Report compiled February 24, 2026. All on-chain data, TVL figures, and litigation status should be independently reverified against primary sources before any investment or risk management decision.*
