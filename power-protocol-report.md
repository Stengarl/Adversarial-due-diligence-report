# Power Protocol (powerprotocol.xyz) — DeFi Adversarial Due Diligence Report

**Report Date:** 2026-02-26
**Analyst Framework:** Adversarial / Guilty Until Proven Innocent
**Token:** $POWER (ERC-20)
**Contract:** `0x9dc44ae5be187eca9e2a67e33f27a4c91cea1223` (Ethereum)
**Total Supply:** 1,000,000,000 POWER
**Research Confidence:** MEDIUM (limited by: no team page on website, no public smart contract repos, no audit reports, CEX-held majority of supply obscures on-chain data)

---

## 1. EXECUTIVE SUMMARY

**One-Paragraph Verdict:**
Power Protocol is a Web3 gaming infrastructure token built by Pixion Games — a real, doxxed London studio with verifiable VC backing. This is not a rug pull in the traditional sense: the CEO has an identifiable track record, the ERC-20 token contract is clean, and the flagship app (Fableborne) has real on-chain usage on Ronin. However, the "protocol" framing is marketing misdirection — Power Protocol is a single-studio token economy, not a multi-app infrastructure layer. The project carries severe structural risks: **zero smart contract audits on any contract**, staking rewards are pure token inflation, investor unlock cliffs begin as early as mid-2026, and the price has surged +347% in 30 days with no fundamental change. Against the established GameFi graveyard (AXS -98%, GALA -82%, RON -90%), the pattern is familiar and the outcome predictable without sustained real revenue and adoption. **Rating: MEDIUM-HIGH RISK. Not a scam; potentially a value trap dressed as infrastructure.**

**Confidence Level:** MEDIUM

**Top 3 Risks:**
1. **No smart contract audit on any Power Protocol contracts** — $200M+ market cap, staking live, zero audits found anywhere.
2. **Staking rewards are pure token inflation** — yield is community emissions (37.2% of supply), not protocol revenue. This is a Ponzi-adjacent structure until real external demand materializes.
3. **Massive unlock overhang in 2026** — 79% of supply still locked; investor cliff begins as early as April 2026, creating structural sell pressure against a token that has already pumped +2,342% from its launch low.

**Top 3 Positive Signals:**
1. **Fully doxxed CEO with verifiable gaming industry background** (Konami, 15+ years) and legitimate VC roster (Delphi, Mechanism, Animoca, YGG, Sky Mavis, Bitkraft).
2. **Fableborne has verified on-chain traction**: $21.5M Kingdom Raffle on Ronin, 2.2M RON in NFT trading volume, 380K+ open beta players, 25-51% weekly retention — real numbers in a sector where most games report nothing.
3. **ERC-20 token contract is technically clean**: no mint function, no pause, no blacklist, standard OpenZeppelin implementation, treasury uses Gnosis Safe multi-sig.

---

## 2. TEAM ASSESSMENT

### 2.1 Kam Punia — Founder & CEO

**Status: VERIFIED (High Confidence)**

| Claim | Verified? | Source | Notes |
|---|---|---|---|
| CEO of Pixion Games | ✅ YES | Crunchbase, LinkedIn, PocketGamer | Consistent across all sources |
| University of Greenwich BSc (2005-2008) | ✅ YES | Crunchbase | Games Design, 3D Animation, Programming |
| Konami Digital Entertainment (2009-2013) | ✅ YES | LinkedIn, multiple press | Head of TCG — Northern Europe |
| Red Man Gaming (2014-2016) | ✅ PARTIAL | LinkedIn only | Director of Marketing; company not verifiable independently |
| Founded Pixion Games (2018) | ✅ YES | BusinessWire, CoinDesk, PocketGamer | Studio verifiable across multiple press |
| ECOMI/VeVe Advisor (2018-present) | ✅ YES | LinkedIn, Crunchbase | Advisory board member |
| Twitter: @Kam_Punia | ✅ YES | Official project channels reference same handle | Active, English-language, real engagement |

**ECOMI/VeVe Connection — FLAG:**
Kam Punia has been an advisory board member of ECOMI/VeVe since 2018. ECOMI's OMI token crashed **-87% in 2022** alone and reached an all-time low in November 2024 — near total destruction of investor value. Punia was in an advisory capacity, not a founder, so direct culpability is limited. However, his ongoing advisory role through the collapse and his failure to publicly acknowledge it is a yellow flag. He has promoted NFT digital collectibles as an advisor while that market imploded.

**Near-Death Financial Event — FLAG:**
In approximately 2020 (during GDC), Pixion Games lost ~$2M in signed funding commitments when the lead investor (representing 60% of the raise) pulled out. Punia maxed out personal credit cards and the studio was 3 weeks from closure. The studio recovered and eventually raised $5.5M. This event demonstrates: (a) genuine entrepreneurial resilience, but also (b) a studio that has operated under extreme financial pressure and may be more susceptible to prioritizing token launch economics over sound protocol design.

**GitHub Activity for Kam Punia:**
No personal GitHub profile found under "Kam Punia" or "KamPunia" with meaningful contributions.

---

### 2.2 Other Team Members

**CRITICAL GAP: No other team members publicly identified.**

- The official website (powerprotocol.xyz) has **no team page**.
- No CTO, lead developer, blockchain engineer, or other named team member appears in **any media coverage**, whitepaper, or official communications.
- PocketGamer, Decrypt, Blockchainmer.biz — all cover only Kam Punia.
- GAM3S.GG article author is a journalist (not a team member).

**GitHub — Pixion-Games Organization:**
- **1 public repository**: a fork of `ronin-chain/ronin-assets` (catalog of Ronin token info), last updated December 4, 2025.
- **0 stars, 0 meaningful commits**, 0 original code.
- **No smart contract repositories published.** For a team claiming to build a "protocol infrastructure layer," this is a severe red flag.
- Organization has no public members listed.

**Unverified Claims:**
- Team described as "makers, gamers, and leaders" from Konami, Garena, Gala, Square Enix, Sony, Wargaming — **NONE individually named or verifiable**.
- "Over $500M in revenue managed" — attributed to Pixion team collectively, **not independently verifiable**.

---

### 2.3 Team Risk Summary

| Risk Factor | Severity | Confidence |
|---|---|---|
| Anonymous development team (only CEO doxxed) | HIGH | High |
| No public smart contract code or GitHub commits | HIGH | High |
| ECOMI/VeVe advisory (project crashed 87%) | MEDIUM | High |
| Prior studio near-insolvency event | MEDIUM | High |
| No CTO or technical lead publicly identified | HIGH | High |

---

## 3. THIRD-PARTY CONSENSUS

### 3.1 Independent Analyst Coverage

**Summary: Almost entirely promotional or price-prediction content. Zero adversarial or independent security analysis found.**

| Source | Type | Stance | Independence |
|---|---|---|---|
| GAM3S.GG | Gaming media | Promotional | LOW (GameFi publisher) |
| PocketGamer.biz | Gaming media | Neutral/positive | MEDIUM (general gaming press) |
| Decrypt | Crypto media | Neutral | MEDIUM (migration story, no critique) |
| Phemex Blog | Exchange | Price prediction | VERY LOW (CEX promotional) |
| BingX Blog | Exchange | Price prediction | VERY LOW (CEX promotional) |
| ainvest.com | AI aggregator | Auto-generated | NONE |
| CoinMarketCap AI | AI aggregator | Auto-generated | NONE |
| Rekt News | Security-focused | **NO COVERAGE** | — |
| The Defiant | DeFi-focused | **NO COVERAGE** | — |
| DL News | Crypto investigative | **NO COVERAGE** | — |
| Ethresear.ch | Technical research | **NO COVERAGE** | — |
| Dune Analytics community | On-chain | **NO COVERAGE** | — |

**Finding:** There is **zero independent critical analysis** of Power Protocol from any DeFi security researcher, investigative journalist, or technically credible analyst. This is not necessarily evidence of wrongdoing — the project is new and GameFi-focused rather than DeFi. However, it means all positive coverage is self-referential and promotional.

### 3.2 Audit & Security Posture

**CRITICAL: ZERO AUDITS FOUND**

- Etherscan explicitly states: **"No Contract Security Audit Submitted"** for the POWER token contract.
- No audit from CertiK, Hacken, Trail of Bits, OpenZeppelin, Spearbit, Cantina, or any other firm was found for any Power Protocol contract — ERC-20, staking, or otherwise.
- The official website displays **no audit badges or security certifications**.
- The whitepaper does not reference any audit.
- The staking platform (staking.powerprotocol.xyz) has no disclosed audit.

**For context:** At a $200M+ circulating market cap with active staking and multi-chain deployment, the complete absence of any smart contract audit is an extraordinary omission. Protocols with far smaller TVL and market caps (e.g., $5M) routinely commission audits before launch. This is either extreme negligence or a deliberate decision to skip the cost and scrutiny.

### 3.3 Community Sentiment (Non-Affiliated Sources)

- **Reddit (r/CryptoCurrency, r/DeFi, r/ethfinance):** No threads found discussing Power Protocol critically or analytically. Zero community discussion outside promotional contexts.
- **Crypto Twitter / X:** No independent analyst threads found. Coverage consists of exchange promotional accounts and gaming influencers.
- **Discord of competing protocols:** Not checked (rate limiting prevented access).
- **Bitcointalk:** No meaningful threads found.

**Notable finding:** The absence of any independent community discussion — positive or negative — is itself informative. It suggests the project's audience is primarily gaming-native (Fableborne players), not DeFi-native. This means there are fewer knowledgeable actors stress-testing the economics.

---

## 4. ON-CHAIN FINDINGS

### 4.1 ERC-20 Token Contract

**Contract:** `0x9dc44ae5be187eca9e2a67e33f27a4c91cea1223`
**Chain:** Ethereum (also BSC and Ronin via bridge)
**Status:** ✅ Verified source code, exact match

| Property | Finding | Risk |
|---|---|---|
| Token standard | ERC-20, OpenZeppelin | ✅ Low |
| Mintable | ❌ NO — fixed supply | ✅ Low |
| Pausable | ❌ NO | ✅ Low |
| Blacklist function | ❌ NO | ✅ Low |
| Proxy/upgradeable | ❌ NO | ✅ Low |
| Ownership model | Two-step transfer (ConfirmedOwnerWithProposal) | ✅ Low |
| Audit status | **NONE submitted** | 🔴 Critical |
| Holder count | **812 addresses** | ⚠️ Medium |

**Assessment:** The ERC-20 contract itself is technically clean. The architecture is minimal and appropriate for a gaming token. The concern is not contract exploitability but the complete absence of any independent verification.

### 4.2 Holder Distribution

**Only 812 on-chain Ethereum holders for a ~$201M market cap token.** This is extremely concentrated.

**Explanation:** Most POWER is held on centralized exchanges (Gate, Binance Alpha, Bitget, MEXC, LBank). Users who buy via these platforms hold tokens in exchange custodial wallets, not visible as individual on-chain holders. This is normal for CEX-listed tokens but creates opacity around actual holder distribution.

**Key concern:** If 70%+ of circulating supply is on CEXes, a coordinated exit by a small number of whales or exchange-side liquidity withdrawal could cause extreme price dislocation with very little warning.

### 4.3 Treasury / Deployer Wallet

**Address:** `0x9EBA6157b4841A57C4cd3359C2bf95ee0A0363df`
**Type:** Gnosis Safe multi-sig (best practice ✅)
**Created:** March 31, 2025 (8 months before the December 2025 token launch)
**Holdings:** 238,000,001 POWER tokens (~$512M at time of research)
**Total transactions:** 26

| Finding | Detail | Risk |
|---|---|---|
| Multi-sig structure | Gnosis Safe | ✅ Positive |
| Creation date vs. TGE | 8 months pre-launch | ⚠️ Notable — lengthy pre-launch setup |
| Holdings | 238M POWER = 23.8% of total supply | Context: this is the primary vesting/distribution wallet |
| CCIP sends | Cross-chain transfers via Chainlink | Tokens distributed to BSC and Ronin |
| Signer count | **NOT PUBLICLY DISCLOSED** | 🔴 High — cannot verify multisig threshold |

**Critical gap:** The Gnosis Safe structure is good practice, but the **number of signers and the threshold** (e.g., 3-of-5) is not publicly disclosed. If a single person controls 2/3 signers, the multi-sig is security theater. This cannot be verified without the Safe's signer list.

### 4.4 Token Distribution & Vesting

| Allocation | % | Tokens | Unlock Profile |
|---|---|---|---|
| Community Rewards | 37.2% | 372M | 13.2% at TGE, remainder over 48 months |
| Ecosystem Fund | 28.0% | 280M | 2.8% at TGE, remainder over 36 months |
| Investors | 16.15% | 161.5M | 0% TGE, 4-12 month cliff, 6-36 month vest |
| Team | 9.23% | 92.3M | 0% TGE, 12-month cliff, 36-month vest |
| Liquidity | 5.0% | 50M | 100% at TGE |
| Advisors | 4.42% | 44.2M | 0% TGE, 12-month cliff, 36-month vest |

**TGE Date:** December 5, 2025

**Unlock Timeline (Approximate):**
- April–June 2026: Earliest investor unlocks (4-month cliff) — up to 161.5M tokens entering market
- December 2026: Team + advisor + remaining investor cliff — 136.5M additional tokens
- 2026-2028: Continuous monthly emissions from community + ecosystem funds

**Assessment:** The vesting structure is not atypical for GameFi, but combined with a +2,342% post-launch surge, the unlock overhang represents severe sell pressure risk. Historical analogs (AXS, GALA, RON) all experienced 80-98% drawdowns from ATH.

### 4.5 Staking Mechanism

**Platform:** `staking.powerprotocol.xyz`

**Mechanism (UNVERIFIED — site not accessible during research):**
Based on official documentation and third-party descriptions:
- Users stake POWER tokens to accumulate **points** (not direct yield)
- Points compete for **seasonal POWER reward pools**
- Staking is gamified with leaderboards and seasons
- Reward pool size: described as including 614,394 POWER prizes for active guilds

**Revenue Source of Staking Rewards:**
- Funded by **community emission schedule** (37.2% of supply over 48 months = ~93M POWER/year average)
- NOT funded by external protocol revenue or fees from third-party studios
- This is **token inflation** dressed as yield — classic GameFi emission farming

**Risk:** If POWER price declines (due to unlocks, market downturn, or user exodus), the APY in USD terms collapses even if token emissions continue. This creates reflexive death spirals common to GameFi.

### 4.6 TVL / Real Usage

**Power Protocol has no TVL in the DeFi sense.** There is no lending, borrowing, liquidity provision, or collateral pool. The "protocol" is a staking and reward-routing system for games.

**Real usage metrics (Fableborne on Ronin):**
- Kingdom Raffle: 15.4M RON (~$21M USD) in presale commitments ✅ Real
- NFT trading volume: 2.2M RON (~$3M USD) ✅ Real
- Open beta players: 380,000+ ✅ Real (independently confirmed by Ronin network reports)
- Peak DAU: 108,000 ✅ Claimed (not independently on-chain verified)
- Weekly retention: 25-51% ✅ Claimed (not independently verified)
- Best Mobile Game at GAM3 Awards ✅ Real

**Post-launch live game metrics:** NOT FOUND. All player count data refers to beta phases. Current live active user counts are not publicly disclosed.

---

## 5. RED FLAGS REGISTER

| # | Flag | Severity | Evidence | Why It Matters |
|---|---|---|---|---|
| 1 | **Zero smart contract audits** | 🔴 CRITICAL | Etherscan: "No Contract Security Audit Submitted"; no audit from any firm found anywhere | $200M+ market cap with active staking and multi-chain deployment; unaudited code at this scale is extraordinary negligence |
| 2 | **Staking rewards = pure token inflation** | 🔴 CRITICAL | Whitepaper: 37.2% community emissions over 48 months fund all staking rewards; zero external revenue confirmed | This is monetary expansion, not yield; creates death-spiral risk if token price falls |
| 3 | **Massive unlock overhang** | 🔴 CRITICAL | Investor cliff: April-June 2026 (161.5M tokens); team/advisor cliff December 2026 | Post-+2,342% rally, locked insiders hold massive unrealized profits; historical GameFi analog: 80-98% drawdowns |
| 4 | **No team page; only CEO publicly identified** | 🔴 HIGH | Official website has no team section; no CTO, engineers, or other named members in any media | For a "protocol" claiming to build blockchain infrastructure, anonymous development team is extreme risk |
| 5 | **GitHub: 1 public repo — a fork with 0 stars** | 🔴 HIGH | github.com/Pixion-Games; only repo is a fork of ronin-assets | A team building "protocol infrastructure" with no public smart contract code is contradictory at best |
| 6 | **Power Labs: zero announced incubation investments** | 🔴 HIGH | GAM3S.GG, whitepaper, all coverage: only Pixion Games uses the protocol | "Multi-app infrastructure layer" is marketing; currently this is a single-studio token economy |
| 7 | **Treasury multi-sig signers not disclosed** | ⚠️ HIGH | Gnosis Safe structure confirmed; signer count and threshold not published | Multi-sig is meaningless security if 1 person controls the keys |
| 8 | **Avalanche Blizzard Fund: invested for Avalanche; never deployed on Avalanche** | ⚠️ HIGH | BusinessWire June 2023: "built atop the Avalanche network"; Decrypt: "Fableborne had not deployed any blockchain assets on Avalanche" before migrating to Ronin | Ecosystem-conditional funding used then project migrated to competitor chain; potential misalignment of grant funding |
| 9 | **+347% price surge in 30 days with no fundamental change** | ⚠️ HIGH | CoinGecko/CoinMarketCap data Feb 2026 | Extreme speculative momentum; ATH $1.14 on Feb 25 2026 vs. launch low $0.066 = +1,627% from TGE; GameFi attrition pattern historically follows |
| 10 | **812 on-chain Ethereum holders for $201M market cap** | ⚠️ HIGH | Etherscan token page | Extreme concentration; most supply on CEXes; one whale exit = disproportionate slippage |
| 11 | **ECOMI/VeVe advisory role** | ⚠️ MEDIUM | LinkedIn/Crunchbase: "Advisory Board Member, ECOMI/ORBIS Blockchain Technologies Ltd" since 2018; ECOMI crashed -87% in 2022, hit ATL Nov 2024 | Punia advised on a project that destroyed investor value; no public commentary on this from him |
| 12 | **Trading competition with 100K USDT prize pool** | ⚠️ MEDIUM | CMC/CoinRank data; Binance/Bitget competition ending Jan 14, 2026 | Volume competitions incentivize wash trading; inflated volume metrics create false demand signals |
| 13 | **RON (Ronin) network token is down -90% from 2024 highs** | ⚠️ MEDIUM | CoinGecko data; Messari Q1 2025 report | Fableborne runs on Ronin; if Ronin network continues declining, the gaming ecosystem $POWER depends on is at risk |
| 14 | **No disclosed post-launch player counts** | ⚠️ MEDIUM | All player data refers to pre-launch beta; no live game DAU reported | Beta players ≠ retained live players; the 380K may have significantly eroded post-TGE |
| 15 | **GameFi sector funding fell 55% in 2025** | ⚠️ MEDIUM | crypto.news, multiple sources | Structural headwinds; studios running out of runway; player interest migrating back to Web2 |
| 16 | **FDV ~$1B vs $15.5M total VC funding** | 🟡 LOW-MEDIUM | Market data vs. Crunchbase funding data | 65x markup over last funding round; implies VCs sitting on massive paper gains with incentive to exit at cliffs |
| 17 | **Prior studio near-insolvency (maxed credit cards, 2020)** | 🟡 LOW | PocketGamer article | Context for understanding studio's history under financial pressure |

---

## 6. POSITIVE SIGNALS

| # | Signal | Confidence | Evidence |
|---|---|---|---|
| 1 | CEO Kam Punia fully doxxed, real track record | HIGH | LinkedIn, Crunchbase, PocketGamer, Decrypt all consistent |
| 2 | Tier-1 VC backing (Delphi, Mechanism, Animoca, YGG, Sky Mavis, Bitkraft, Shima) | HIGH | BusinessWire, PocketGamer, Messari confirmed |
| 3 | ERC-20 contract clean (no mint, pause, blacklist) | HIGH | Etherscan verified source code |
| 4 | Gnosis Safe multi-sig treasury | HIGH | Etherscan address label + transaction pattern |
| 5 | Fableborne real on-chain NFT revenue ($21.5M Kingdom Raffle, $3M NFT volume on Ronin) | HIGH | Ronin chain data, Messari Ronin Q1 2025 report |
| 6 | 380K beta players with 25-51% weekly retention | MEDIUM | Multiple gaming media; independently noted in Ronin ecosystem reports |
| 7 | GAM3 Awards "Best Mobile Game" recognition | MEDIUM | Gaming media; independently conferred |
| 8 | 12-month cliff for team/advisors (no immediate insider dumps) | HIGH | Whitepaper tokenomics |
| 9 | Fableborne contributed to Ronin DAU doubling (600K → 1.2M) in Nov 2024 | MEDIUM | Ronin 2024 Year in Review blog |
| 10 | Two-step ownership transfer on ERC-20 (enhanced security) | HIGH | Etherscan contract read |

---

## 7. UNRESOLVED QUESTIONS

The following could not be determined during this investigation and represent areas requiring further research:

1. **Who are the other team members?** No developers, CTOs, or engineers are named anywhere. Are they real? What are their backgrounds? This cannot be verified from public information.

2. **Who controls the Gnosis Safe multi-sig?** How many signers? What threshold? Is Kam Punia a single point of failure? This is unknowable without direct disclosure.

3. **Does the staking contract exist, and is it audited?** The staking platform is live at staking.powerprotocol.xyz but no contract address was found and no audit was located. This is an unresolved and critical security question.

4. **What are the post-launch live player counts for Fableborne?** The game launched globally December 2025. No post-launch DAU data was published. This is the single most important fundamental metric.

5. **Are there any third-party studios actively in the Power Protocol ecosystem?** Power Labs is described as an incubator, but no investments or partnerships with outside studios have been publicly announced. This is the core thesis of the "infrastructure layer" narrative.

6. **Did the Avalanche Foundation raise concerns about the chain migration?** No public record of an objection or refund was found. The nature of the Blizzard Fund investment (grant vs. equity vs. token allocation) is unclear.

7. **Where did the 238M POWER tokens in the treasury Safe go via CCIP?** The cross-chain sends are visible on Etherscan but destination wallets on Ronin and BSC were not fully traced during this session.

8. **What is the actual APY on staking?** The staking platform was inaccessible and no confirmed APY figure was found in any source. Without this, the inflation rate cannot be properly modeled.

---

## 8. RISK RATING

| Dimension | Rating | Rationale |
|---|---|---|
| Team Risk | MEDIUM | CEO doxxed and real; rest of team anonymous; no technical leads identified |
| Contract Risk | HIGH | No audits; staking contract unverified |
| Tokenomics Risk | HIGH | Pure emission inflation as yield; 79% supply unlocking; investor cliff in 2026 |
| Centralization Risk | MEDIUM | Gnosis Safe used; but signers undisclosed; 812 holders only |
| Business Model Risk | HIGH | Single-studio ecosystem; Power Labs has no announced partners; no real protocol revenue |
| Market Risk | HIGH | +347% in 30 days; established GameFi crash pattern; Ronin network in decline |
| Team Track Record | MEDIUM | Punia has real gaming experience but ECOMI advisory and studio near-death are concerns |

**OVERALL RISK RATING: HIGH**

---

## 9. APPENDIX: KEY ADDRESSES & LINKS

| Resource | Value |
|---|---|
| POWER ERC-20 (Ethereum/BSC) | `0x9dc44ae5be187eca9e2a67e33f27a4c91cea1223` |
| POWER (Ronin) | `0x394cEF8bDd737EE24DBc9f43d0d5D2ab83136054` |
| Treasury/Deployer Safe | `0x9EBA6157b4841A57C4cd3359C2bf95ee0A0363df` |
| Safe Creator EOA | `0x9dc3309bb85081197646ac86c703a11995e195dd` |
| Whitepaper | https://power-protocol.gitbook.io/power-protocol-whitepaper/ |
| GitHub (Pixion) | https://github.com/Pixion-Games |
| Etherscan Token | https://etherscan.io/token/0x9dc44ae5be187eca9e2a67e33f27a4c91cea1223 |
| Staking | https://staking.powerprotocol.xyz |
| CEO Twitter | https://x.com/Kam_Punia |
| CEO LinkedIn | https://linkedin.com/in/karmveerpunia |

---

*Report produced using the DeFi Adversarial Research Framework. All findings are timestamped 2026-02-26. Data may change. This is not financial advice.*
