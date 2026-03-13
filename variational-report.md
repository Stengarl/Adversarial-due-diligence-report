# Variational Protocol — Adversarial Due Diligence Report

**Prepared:** 2026-03-10
**Methodology:** DeFi Adversarial Research Framework (Guilty Until Proven Innocent)
**Research Scope:** Team forensics, third-party intelligence, on-chain investigation, comparative analysis
**Sources ranked:** On-chain > Independent analysts > Community intelligence > Historical footprints > Official comms

---

## 1. Executive Summary

**Verdict:** Variational is a legitimate, institutionally-backed DeFi derivatives protocol with verifiable founders and a genuine product — but it carries several structural risks that the marketing obscures. It is NOT a rug pull candidate. It is, however, a protocol with a deeply centralized core mechanic (the OLP), undisclosed tokenomics, and a yield model that is mathematically unsustainable at scale. The 300%+ APY advertised for the OLP vault is the single largest red flag: this number reflects early-stage mechanics, not a durable business model.

**Confidence Level:** Medium-High. Research is limited by: (1) audit reports not publicly indexed, (2) VAR token not yet launched (vesting unknowable), (3) private mainnet limiting full on-chain transparency.

### Top 3 Risks

1. **OLP Centralization** — A single, team-controlled entity is the sole market maker for all Omni trades. Every user counterparty risk is concentrated here. If OLP mismanages hedging or faces operational failure, users have no alternative.
2. **Unsustainable Yield Incentives** — The 300%+ OLP APY reflects small vault size, rapid volume growth, and subsidized operations. At scale, hedging costs converge with spread income. Points program ends Q3 2026, creating a predictable activity cliff.
3. **Undisclosed Tokenomics** — Despite raising $11.8M from institutional investors, the team/investor vesting schedule for the VAR token has NOT been disclosed. The "50% community" allocation sounds good; the other 50% is a black box.

### Top 3 Positive Signals

1. Fully verifiable founders with pre-crypto digital footprints going back to 2014–2017: published research, real GitHub activity, legitimate academic and professional history. Strongest signal against rug risk.
2. Tier-1 institutional backers — Bain Capital Crypto, Coinbase Ventures, Dragonfly Capital, and Peak XV Partners are independently confirmable and represent serious reputational skin in the game.
3. Demonstrated protocol delivery — roadmap items show consistent execution across 2024–2025 with most quarterly milestones completed.

---

## 2. Team Assessment

### 2.1 Lucas Schuermann — Co-Founder and CEO

#### VERIFIED FACTS

- **Education:** BS Computer Science, Columbia University (2014–2019), Egleston Scholar (top <1% of class). Mathematics coursework at University of Oklahoma starting at age 12. Part-time graduate coursework at Stanford (2020–2021). Source: lucasschuermann.com/about
- **Qu Capital:** Co-founded 2017 with Edward Yu and Alex Price (all Columbia University). Statistical arbitrage hedge fund focused on crypto. Acquired by Digital Currency Group (Genesis parent) in September 2019. Source: theblock.co/post/40257
- **Genesis Global Trading:** VP of Engineering, 2019–2021. Genesis was an OTC desk handling over $250B in volume. Source: lucasschuermann.com
- **Left Genesis in 2021** — two years before the firm bankruptcy in January 2023. This is a meaningful mitigating fact.
- **GitHub:** github.com/lucas-schuermann — Active repository history including Rust and WASM physics simulations. Code quality is consistent with a genuine senior engineer. No fork-and-rebrand patterns detected.
- **Prior roles:** Software engineer intern at Google X (robotics), Quantitative Strategist intern at Goldman Sachs IB Division.
- **Awards:** Harvard Innovation Challenge Winner (2019), National Merit Scholar (2014), Presidential Scholar Nominee (2014). All predate crypto involvement and corroborate identity continuity.

#### UNVERIFIED CLAIMS

- No independent verification of exact VP Engineering scope at Genesis (LinkedIn shows it; company is defunct).
- "Stealth mode profitable market maker 2022–2024" — not independently verifiable since this predates any public on-chain footprint.

#### RED FLAGS — Lucas Schuermann

None identified. Unusually clean profile for DeFi.

#### WHAT COULD NOT BE DETERMINED

- Exact departure circumstances from Genesis.
- Whether any equity stake in DCG affects ongoing incentives.

---

### 2.2 Edward Yu — Co-Founder and CTO

#### VERIFIED FACTS

- **Education:** BS Applied Mathematics, Columbia University (2014–2017), graduated with honors. Source: quant.am
- **Qu Capital:** Co-founded 2017 alongside Lucas Schuermann and Alex Price. Same DCG acquisition September 2019. Source: prnewswire.com
- **Genesis Global Trading:** Head of Quantitative Research, 2019–2021. Market making on linear and options markets. Source: quant.am
- **Left Genesis in 2021** — predates the FTX contagion collapse by two years.
- **Published academic research:**
  - "Bayesian Neural Networks with Soft Evidence" (arxiv.org/abs/2010.09570) — 2021 ICML workshop
  - "A Bayesian Ensemble for Unsupervised Anomaly Detection" — 2016 Facebook research preprint
  - Open-source contributions to TPOT (Tree-based Pipeline Optimization Tool)
- **Angel investor in approximately 20 startups**, preferring seed or Series A stage. Source: quant.am
- **Personal website:** quant.am — active, consistent with career narrative.

#### UNVERIFIED CLAIMS

- "Head of Quantitative Research" scope at Genesis — LinkedIn attestable, but no public Genesis org chart exists to confirm seniority level.
- Exact nature of quant strategies employed at Genesis is unknown.

#### RED FLAGS — Edward Yu

None identified. Academic paper trail and open-source contributions confirm genuine quantitative background.

#### WHAT COULD NOT BE DETERMINED

- Whether quant strategies during Genesis tenure had any exposure to assets or counterparties that later imploded.
- No known pseudonyms detected.

---

### 2.3 Genesis Bankruptcy — Contextual Risk Assessment

Both founders worked at Genesis Global Trading, which filed Chapter 11 bankruptcy in January 2023. Critical context:

Genesis collapsed due to: (1) $175M locked in FTX trading account, (2) approximately $500M losses from Three Arrows Capital, (3) mismanaged crypto lending operations. The bankruptcy was a **credit and lending business failure, NOT a trading technology or quantitative research failure**.

Founders left in 2021 — not present during the 2022 crisis buildup. No regulatory actions identified against individual Genesis engineering or quantitative research personnel. The SEC charged Genesis and Gemini over the "Earn" product — a lending/yield product entirely unrelated to derivatives trading technology.

**Assessment:** Genesis association is a Medium reputational risk but does not constitute evidence of wrongdoing. Both founders demonstrably exited years before the crisis. Running a profitable proprietary MM desk for 2 years after leaving (2022–2024) before pivoting to infrastructure is consistent with founders who anticipated problems early.

---

## 3. Third-Party Consensus

### 3.1 Audit Status

| Auditor | Scope | Report Public | Firm Reputation |
|---|---|---|---|
| Zellic | Core smart contracts, settlement mechanics | NOT publicly indexed | Tier-1 |
| Spearbit | Front-end and API-level integrations | NOT publicly indexed | Tier-1 |

**Critical finding:** Zellic and Spearbit are both highly reputable firms. However, neither audit report appears in their public portfolios (reports.zellic.io, github.com/spearbit/portfolio) as of March 2026. An independent third-party review (CoinLaunch) explicitly noted: *"the project claims to have been audited by Zellic and Spearbit, yet no reports were provided."*

This does not mean the audits did not happen — the roadmap confirms "Contract audits" were completed in Q4 2024. But unverified findings severity is a yellow flag. Users cannot independently verify whether critical or high findings were identified, whether all findings were resolved before mainnet, or whether deployed contracts match the audited codebase.

No public exploits or security incidents have been reported since the January 2025 private beta launch — a positive signal given approximately $33M TVL and $2.5B cumulative volume.

### 3.2 Independent Analyst Coverage

**Alea Research (independent Substack):** Most substantive critical analysis found.
- Volume is incentive-driven capital rotation — traders farming points, not loyal users
- Only approximately 15K active addresses from 27K retroactive airdrop recipients (44% activation rate)
- Token distribution documentation vague: "50% community does not indicate entirely airdrop"
- Venture-backed positioning structurally disadvantaged vs. Hyperliquid "0 VC" narrative
- Points program ends Q3 2026 — predictable activity cliff

**PANews (independent Chinese-language crypto media):** Critical piece noting:
- OLP market-making mechanism "remains opaque and team-controlled"
- Current yield subsidies may represent unsustainable customer acquisition costs
- "Highly centralized nature" — users remain "powerless" relative to OLP as singular market maker

**Arbitrum Foundation Blog:** Promotional piece — aligned with project, not independent.

**Not covered by:** Rekt News, The Defiant, DL News. Absence of security-focused coverage is neutral (no exploits to report).

### 3.3 Investor Verification

| Investor | Status |
|---|---|
| Bain Capital Crypto | VERIFIED — The Block independent reporting |
| Peak XV Partners | VERIFIED — The Block independent reporting |
| Coinbase Ventures | VERIFIED — multiple independent sources |
| Dragonfly Capital | VERIFIED — multiple independent sources |
| North Island Ventures | VERIFIED — press confirmed |
| HackVC | VERIFIED — press confirmed |
| Brevan Howard | NOT independently verified |
| Mirana Ventures | VERIFIED — The Block press release June 2025 |

The institutional backer list is credible. Bain Capital Crypto and Coinbase Ventures are conservative, reputation-conscious investors. Their participation meaningfully lowers rug risk.

### 3.4 Community Sentiment

No scam or rug-pull allegations found in any community scan (Reddit, Twitter, forums). Critical commentary is entirely structural and technical — OLP centralization, yield sustainability — rather than fraud allegations. Competing protocol communities have raised no public warnings.

Positive Twitter sentiment skews toward airdrop farmers and speculative traders — not inherently meaningful as a signal of protocol quality.

---

## 4. On-Chain Findings

### 4.1 Contract Status

**Deployment:** Arbitrum One
**Core contract addresses:** Not definitively identified through public search. No canonical verified core contract is prominently disclosed in official documentation or indexed in secondary sources.

**Concern:** Competition participation NFT contracts (e.g., 0x33ec5ccf625fcd2e792bdc16d46d5c2c1cc484d7) appear unverified on Arbiscan. Lower-tier contract, but the non-disclosure pattern warrants monitoring.

**Audited code vs. deployed code match:** UNKNOWN — not verifiable without published audit reports containing contract hashes.

**Architecture elements from official docs:**
- Settlement Pools: isolated bilateral escrow contracts per trade
- Variational Oracle: custom price feed aggregating CEX and DEX data
- OLP: team-controlled market-making entity (on-chain position tracking, off-chain hedging on CEX)

**Centralization vectors identified:**
- OLP is the sole approved market maker on Omni — no decentralization mechanism announced
- Oracle is custom-built and internally controlled
- No disclosed timelocks or multisig configuration in public documentation

### 4.2 TVL and Volume Verification

| Metric | Source | Confidence |
|---|---|---|
| $33M TVL (Oct 2025) | Third-party aggregators | Medium — DeFiLlama page not confirmed |
| $2.5B cumulative volume (Oct 2025) | Arbitrum Foundation blog | Medium — promotional source |
| $195M open interest (Oct 2025) | Same source | Medium |
| 300%+ OLP annualized yield (Apr–Jul 2025) | Multiple independent analyses | High |
| Approximately 15K active addresses | Alea Research | Medium |

**Important caveat:** Variational operated invite-only until at least mid-2025. Volume and TVL figures may not be independently verifiable via DeFiLlama during this period. DeFiLlama page existence was not confirmed by direct access.

### 4.3 Token Distribution Analysis

**VAR Token status as of March 2026:** NOT YET LAUNCHED

**What is disclosed:**
- 50% community allocation (confirmed)
- 30% of protocol revenue to buyback and burn (confirmed)
- Points program ends Q3 2026

**What is NOT disclosed:**
- Team and founder vesting schedule
- Investor vesting schedule (despite $11.8M raised)
- Total supply
- Breakdown of remaining 50% (team, investors, treasury, ecosystem)
- Cliff periods and unlock percentages

**Assessment:** Absence of vesting schedule disclosure despite a completed $11.8M institutional raise is a significant red flag. Every legitimate protocol discloses this before token launch. The longer it remains undisclosed, the more dump risk accumulates at TGE.

### 4.4 Revenue Model — On-Chain vs. Off-Chain Risk

The OLP revenue model:
1. User requests quote; OLP provides bid-ask spread
2. Trade executes; OLP collects spread (estimated 4–6 bps)
3. OLP immediately hedges on Binance/Bybit/Hyperliquid (cost: 0–2 bps at institutional rates)
4. Net margin: approximately 2–6 bps per trade

**Off-chain dependency risk:** OLP hedging happens on centralized exchanges. If Binance/Bybit impose restrictions, CEX connectivity is lost during volatility, or regulatory action freezes API access, OLP is unhedged and directionally exposed. This risk is not disclosed prominently to retail users.

---

## 5. Red Flags Register

| # | Flag | Severity | Evidence | Why It Matters |
|---|---|---|---|---|
| 1 | Audit reports not publicly available | HIGH | Neither Zellic nor Spearbit portfolio lists Variational; third-party review confirms reports not provided | Cannot independently verify finding severity or remediation status |
| 2 | OLP is sole market maker, team-controlled | HIGH | Official docs, multiple independent analyses, PANews critical piece | Single point of failure for all Omni trades; pricing fairness unverifiable |
| 3 | 300%+ OLP APY unsustainable at scale | HIGH | Alea Research, Gate News, multiple independent analyses confirm early-stage inflation | Classic pattern attracting capital before inevitable yield compression |
| 4 | Team/investor vesting schedule undisclosed | HIGH | VAR token page, tokenomics docs — no breakdown of non-community 50% | $11.8M institutional capital with unknown unlock schedules is major dump risk at TGE |
| 5 | Genesis bankruptcy association | MEDIUM | Genesis filed Chapter 11 Jan 2023; both founders were employees | Reputational concern; MITIGATED by confirmed 2021 departure, 2 years before collapse |
| 6 | Core contract addresses not prominently disclosed | MEDIUM | Arbiscan search returned no canonical core contract; competition NFT unverified | Reduces ability to independently audit on-chain state |
| 7 | Only 44% activation of retroactive airdrop recipients | MEDIUM | Alea Research: ~15K active vs. 27K retroactive | Organic user interest substantially weaker than raw address counts suggest |
| 8 | Off-chain CEX dependency for hedging | MEDIUM | Arbitrum blog, multiple technical analyses | Centralized failure vector not disclosed to retail users |
| 9 | Points program cliff Q3 2026 | MEDIUM | Official points program documentation | Current activity partially artificial; post-cliff retention unproven |
| 10 | Zero-fee marketing obscures spread-based costs | LOW | OLP mechanics documentation | Users pay through spreads, not disclosed in headline marketing |
| 11 | US/Canada geographic restrictions | LOW | Platform terms of service | Indicates regulatory exposure awareness around token distribution |
| 12 | No bug bounty program identified | LOW | No Immunefi or equivalent program found | Best-in-class protocols run active bug bounties post-launch |

---

## 6. Comparative Analysis

### vs. Known Rug Pull Patterns

| Rug Pull Marker | Variational | Assessment |
|---|---|---|
| Anonymous team | Fully doxxed, verifiable identities | CLEAR |
| No pre-existing digital footprint | Both founders have 10+ year track records | CLEAR |
| Fake or unverifiable audits | Audits claimed but reports not public | YELLOW FLAG |
| Admin mint/pause mechanisms | Unknown — not independently verifiable | UNRESOLVED |
| Insider wallet patterns pre-launch | Unknown — private mainnet limits visibility | UNRESOLVED |
| Serial project hopper | Qu Capital to Genesis to Variational is coherent career trajectory | CLEAR |
| Sudden social media creation | Footprints predate crypto involvement | CLEAR |
| Exaggerated credentials | All claimed credentials independently verifiable | CLEAR |
| VCs as exit liquidity cover | Institutional rounds without disclosed vesting | YELLOW FLAG |

### vs. Known DeFi Failures

**Terra/Luna (Ponzi yield):** The 300%+ OLP yield rhymes superficially with UST Anchor yield, but the mechanism differs. OLP yield comes from real spread capture, not algorithmic minting. Risk is yield compression, not a death spiral.

**FTX (hidden leverage):** No evidence of hidden leverage or misuse of user funds. Settlement pools are isolated on-chain escrow. Meaningfully different from FTX structure.

**Celsius (broken yield promises):** When OLP vault opens publicly, depositors will be promised yield based on spread income. If volume declines after incentives end, depositors receive lower yields than anticipated. Not systemic collapse risk, but a broken-expectation risk.

### Tokenomics Sustainability Model

The revenue model (spread capture) is theoretically sustainable but currently subsidized:
- Institutional hedging rates (0–2 bps) vs. user spreads (4–6 bps) = approximately 2–4 bps margin
- At $1B monthly volume: $2–4M monthly revenue
- At $10B monthly volume: $20–40M monthly revenue
- OLP yield normalizes to 20–40% at scale — still competitive, but not 300%

The yield is not a Ponzi. It is inflated by early-stage mechanics. This distinction matters but does not eliminate user-expectation risk at scale.

---

## 7. Unresolved Questions

1. **Audit report contents:** What did Zellic and Spearbit find? Were any critical or high-severity issues identified? Were all findings resolved before mainnet? Cannot be determined without public reports.

2. **OLP contract architecture:** Are there admin keys, upgrade proxies, or emergency functions in the settlement pools? Cannot be verified without published contract addresses and source code.

3. **VAR token full allocation:** What is the team vesting cliff? What percentage goes to institutional investors? What are the unlock schedules? Not disclosed despite $11.8M raised.

4. **Post-incentive retention:** Will the approximately 15K active traders continue after the Q3 2026 points program ends? The 44% activation rate is a weak signal for organic loyalty.

5. **OLP actual P&L:** The hedging model is described but actual performance (slippage, failed hedges, edge cases) is opaque. Is the 300% yield net of all hedging losses?

6. **Regulatory posture:** Geographic restrictions on US/Canada suggest potential securities law concerns around VAR token airdrop. Legal structure governing the token is unknown.

7. **Alex Price (third Qu Capital co-founder):** His current role is unaccounted for. Was he included in Variational? Is he an undisclosed advisor or investor?

---

## 8. Final Risk Assessment

| Risk Category | Level | Reasoning |
|---|---|---|
| Rug Pull Risk | LOW | Verified team, institutional backers, real product with delivery track record |
| Protocol Failure Risk | MEDIUM | OLP centralization, undisclosed hedging operations, CEX dependency |
| Token Launch Risk | MEDIUM-HIGH | Undisclosed vesting for $11.8M institutional capital |
| Yield Sustainability Risk | MEDIUM | 300% APY will compress; broken-expectation risk at scale |
| Security Risk | MEDIUM | Audited by tier-1 firms but reports not publicly available |

**Overall verdict: SPECULATIVE.**

Recommended engagement limited to protocol usage (trading) until:
1. Full audit reports are published with finding severity and remediation status
2. Complete VAR tokenomics with vesting schedules are disclosed for all allocations
3. Post-incentive organic retention data is available after Q3 2026 points cliff

---

## Sources

- The Block — Variational $10.3M Seed Funding: https://www.theblock.co/post/322653/arbitrum-crypto-protocol-variational-funding
- The Block — Qu Capital acquisition by Genesis: https://www.theblock.co/post/40257/otc-crypto-trader-genesis-makes-its-first-acquisition-qu-capital-to-strengthen-trading-technology
- Lucas Schuermann Personal Site: https://lucasschuermann.com/about
- Edward Yu Personal Site: https://quant.am/
- PR Newswire — Qu Capital Acquisition: https://www.prnewswire.com/news-releases/genesis-acquires-quantitative-trading-and-research-firm-qu-capital-300921506.html
- Variational Official Docs: https://docs.variational.io
- Arbitrum Foundation Blog: https://blog.arbitrum.io/how-variational-is-reinventing-derivatives-onchain-with-arbitrum/
- Alea Research — Independent Analysis: https://alearesearch.substack.com/p/variational
- PANews — Critical Analysis: https://www.panewslab.com/en/articles/c9b8c9fe-9643-43b8-b405-a31e5b8c6141
- Followin.io — OLP Mechanics Analysis: https://followin.io/en/feed/19976153
- Gate News — Zero Fee Revenue Analysis: https://www.gate.com/news/detail/15062265
- Genesis Bankruptcy — Al Jazeera: https://www.aljazeera.com/economy/2023/1/20/crypto-giant-genesis-files-for-bankruptcy-after-ftx-collapse
- Variational Mirror Announcement: https://mirror.xyz/variational-io.eth/JfN5na3W-dxvPAPC3g2pmacoihWNMnQNBd55-ypybz8
- Zellic Audit Portal: https://reports.zellic.io/
- Spearbit Portfolio: https://github.com/spearbit/portfolio
- Xangle Research: https://xangle.io/en/research/detail/2287
- CoinLaunch Analysis: https://coinlaunch.space/projects/variational-protocol/

---

*Report generated using DeFi Adversarial Research Framework. Unverified claims are labeled as such. Absence of evidence of wrongdoing is not evidence of good behavior.*
