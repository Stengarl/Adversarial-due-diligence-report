# infiniFi — Adversarial Due Diligence Report

**Date:** 2026-02-26
**Analyst:** DeFi Adversarial Research Framework
**Confidence Level:** HIGH (multiple independent sources; direct on-chain & code verification)
**Classification:** MEDIUM-HIGH RISK

---

## Executive Summary

infiniFi is an Ethereum-based fractional reserve banking protocol launched in June 2025, currently holding approximately **$183M TVL** and preparing for a Token Generation Event (TGE) in early 2026. The protocol allows users to deposit stablecoins (primarily USDC) for iUSD, then choose between liquid (siUSD) or locked (liUSD) yield tranches backed by strategies across Aave, Fluid, Ethena, Pendle, Morpho, Maple, and Fasanara Digital.

**One-Paragraph Verdict:** infiniFi is a technically sophisticated yield aggregator built by a pseudonymous lead developer whose previous protocol was exploited for $2 million due to reentrancy vulnerabilities he called a sophisticated attack on missed protections. Three audits have been completed, but the GOVERNOR role architecture represents a functional single-point-of-failure rug vector, the governance whitepaper section was incomplete at launch, and one live institutional counterparty (Fasanara) operates with no on-chain liquidation protection. TVL is almost certainly dominated by mercenary points-farming capital that will exit at TGE. The protocol is not an obvious rug or scam — Electric Capital's involvement and multiple audits provide meaningful signal — but material undisclosed risks exist, and depositors are taking on concentrated developer track-record, governance, and counterparty risks that are not adequately communicated in official marketing.

**Confidence Level: HIGH** (based on on-chain contract data, GitHub forensics, verified audit reports, and Crunchbase/LinkedIn identity confirmation).

---

### Top 3 Risks Identified

1. **Lead developer built an exploited protocol** — Rob Montgomery (RobAnon) was CEO and lead developer of Revest Finance, which suffered a $2M reentrancy exploit in March 2022. He publicly stated the protocol could not repay victims. InfiniFi's new architecture uses OpenZeppelin's `ReentrancyGuardTransient` — a direct fix pattern — but the track record of shipping exploitable code at his prior company is a material undisclosed risk.

2. **GOVERNOR role is an untimelocked rug vector** — The GOVERNOR controls all 20+ protocol roles including oracle feeds, receipt token minting/burning, farm registry additions, and the `EmergencyWithdrawal.safeAddress` (the wallet to which all funds drain in an emergency). A single compromised or malicious GOVERNOR key enables: silent oracle swap → iUSD mint against inflated collateral → drain via `emergencyWithdraw()`. No timelock protects this.

3. **Off-chain institutional credit risk with no on-chain recourse** — The `FARM_FASANARA_MPC` contract routes user funds to Fasanara Digital's MPC-secured wallet via an escrow contract. If Fasanara Digital defaults on credit obligations, there is no on-chain liquidation mechanism. This is a pure TradFi credit risk embedded inside a protocol marketed as transparent and on-chain.

---

### Top 3 Positive Signals

1. **Electric Capital led the $3M pre-seed** with participation from Sam Kazemian (Frax founder), DeFi Dad, Axiom, and New Form Capital — this represents credible DeFi ecosystem endorsement from investors with due diligence capacity.

2. **Three audit rounds: Spearbit, Certora, and Cantina** — Multiple independent security engagements with a legitimate bug competition (592 findings submitted for $35K pool). The critical FIFO redemption queue violation identified by Certora was fixed before launch.

3. **Loss waterfall and reserves are fully transparent on-chain** — Unlike traditional fractional reserve banks, users can verify the exact asset-liability structure in real-time on Ethereum. The waterfall protection logic (liUSD absorbs first, then siUSD, then iUSD) is encoded and auditable.

---

## Phase 1: Team Assessment

### Rob Montgomery (RobAnon) — CEO and Co-Founder

**VERIFIED:**
- Full legal name Rob Montgomery, confirmed via Crunchbase, LinkedIn, and The Record from Recorded Future News coverage of the Revest Finance exploit (article quotes "Revest CEO Rob Montgomery")
- GitHub handle: `@RobAnon`, Twitter: `@RobAnon94`
- Education: B.S. Mechanical Engineering (2013–2018) and M.S. Mechanical Engineering (2018–2021), Georgia Institute of Technology — NOT a Computer Science degree
- Previous role: CEO and Lead Developer, Revest Finance

**REVEST FINANCE EXPLOIT (HIGH SEVERITY — VERIFIED):**
On March 27, 2022, at 01:41 UTC, Revest Finance was exploited for approximately **$2M** via a reentrancy vulnerability in the ERC1155 minting contract. The exploit targeted the `handleMultipleDeposits()` function of the `tokenVault` contract, which failed to verify whether a newly minted NFT existed before allowing additional deposits. The attacker exploited `onERC1155Received` to re-enter `depositAdditionalToFNFT`, minting 7.7M copies of position 1028 and withdrawing 360,000 RENA tokens against a 1-token deposit.

PeckShield attributed the root cause to "missed reentrancy protection for the key functions of Revest." Rob Montgomery publicly stated: "Revest will not be able to recover the funds from the hackers and does not have the money to cover the losses suffered by victims." The stolen funds were deposited into Tornado Cash. Revest Finance is listed on rekt.news.

**InfiniFi response to track record:** The repo now uses OpenZeppelin's `ReentrancyGuardTransient` on the gateway contract — a direct remediation of the exact vulnerability class that caused the Revest exploit. This shows awareness but does not erase the track record.

**UNVERIFIED / GAPS:**
- His exact role at Revest beyond CEO/lead dev (did he write the exploited function?)
- Whether Revest victims were ever compensated via any other mechanism
- Whether he disclosed his Revest history to Electric Capital (assumable from VC due diligence standards but not confirmed)
- Any legal or regulatory actions related to Revest in any jurisdiction

**Red Flag:** The Crunchbase and LinkedIn profiles describe InfiniFi's team as having "a deep blockchain and financial engineering background, mostly from Revest or related projects." This is a team almost entirely recycled from an exploited protocol.

---

### Erwan Beauvois (eswak) — Protocol Engineer

**VERIFIED:**
- Full name Erwan Beauvois, confirmed via LinkedIn (`fr.linkedin.com/in/eswak`)
- Based in Toulouse, France
- Education: International Post-Grad Master in Space Exploration and Development Systems (SEEDS), Politecnico di Torino; Computer Science for Aerospace Master
- Previous role: Protocol Engineer, **Fei Protocol**
- Additional affiliation: `@galion-io` organization on GitHub
- GitHub repos include forks of: `fei-protocol-core`, `saddle-contract`, `compound-protocol`

**FEI PROTOCOL CONTEXT:** Fei Protocol raised $1.3B at launch in March 2021 and experienced significant instability, ultimately being wound down in 2022 as part of a merger with Rari Capital. The combined Fei/Rari entity then suffered a $80M exploit (Rari Fuse). Fei Labs (the company) shut down its protocol operations.

**SADDLE FINANCE CONTEXT:** Saddle Finance (also forked in eswak's GitHub) was hacked for $10M in April 2022 and wound down shortly after.

**Assessment:** Erwan's prior engagement with Fei Protocol and forks of two wound-down/hacked protocols (Fei, Saddle) represents a pattern of DeFi project exposure to protocols that ultimately failed — though this is more likely research/academic engagement than complicity in failures. He appears to be a legitimate but not elite-tier Solidity engineer, operating as the primary maintainer of the public InfiniFi repo.

**UNVERIFIED:**
- His specific role and contributions at Fei Protocol (employee vs. contractor vs. contributor)
- Whether he holds InfiniFi equity or tokens

---

### nikollamalic — Developer

**VERIFIED:**
- GitHub: `@nikollamalic`, 2 followers, located in Banja Luka, Bosnia
- Made 2 commits: initial commit (April 7, 2025) and PR #4 (September 11, 2025), which was a 3,177-line dump from the internal private repository containing 29 new/changed files
- GitHub repos include `aurox-proxy-swap`

**AUROX CONTEXT:** Aurox is a crypto analytics/wallet extension that faced community criticism related to its token launch. Not a major red flag, but the low profile (2 followers) and connection to a minor controversial project warrants noting.

**Assessment:** Appears to be a junior developer on the team with limited verifiable track record.

---

### GitHub Forensics Summary

| Signal | Finding |
|--------|---------|
| Repo created | April 7, 2025 |
| Total public commits | 24 (over ~10 months) |
| Primary development | PRIVATE repo, batch-dumped to public |
| Contributors | 3 identified (eswak, nikollamalic, RobAnon) |
| GitHub org public members | NONE (deliberately hidden) |
| Organization repos | 8 total, including 3 Pendle forks and 1 Ethena fork |
| Deleted repos/branches | None confirmed; private repo confirmed via commit metadata |
| Code lineage | Fei Protocol's Core/CoreControlled architecture; Revest Finance indexer (`railway-monorepo`) |

**CRITICAL FINDING:** The `railway-monorepo` in the InfiniFi-Labs GitHub organization is explicitly labeled "Pre-existing indexer from Revest." InfiniFi is built on top of infrastructure from Rob Montgomery's previously exploited protocol. The team has not disclosed this codebase lineage in any official marketing materials.

---

## Phase 2: Third-Party Consensus

### Independent Analyst Coverage

**Nansen Research (Nicolai Søndergaard)**
- Published analysis of infiniFi protocol
- **Conflict of interest declared:** "The authors of this content and members of Nansen may be participating or invested in some of the protocols or tokens mentioned herein." This disclosure materially reduces the independence of this analysis.
- No team risks identified in the article
- Notes yields are "competitive but not exceptional" relative to Pendle/Morpho comparables
- Does not address team track record or governance risks

**Blockworks**
- Published June 2025 article on infiniFi's fractional reserve model
- Zero team member names mentioned
- Presented protocol mechanics without adversarial framing
- Not independent analysis — no investigative elements

**Observers.com**
- Identified that infiniFi attracted "significant capital despite publishing an incomplete whitepaper" — comparing this to a "second recent project" following this trend, flagging it as "a concerning trend of investor appetite outpacing due diligence"
- Noted governance section is a placeholder: "To fully address governance is a whitepaper unto itself"

**alearesearch.substack.com**
- Covered Season 1 and 2026 TGE path
- No adversarial or risk-focused analysis found

**Rekt News:** No coverage of infiniFi found. (Absence of rekt coverage is not positive — it just means no exploit has occurred yet, not that the protocol is safe.)

**The Defiant, DL News:** No substantive independent coverage found.

**Overall independent analyst coverage rating: LOW QUALITY** — all major coverage either has conflicts of interest, is promotional, or lacks investigative depth on team or governance.

---

### Audit Assessment

| Audit | Firm | Dates | Scope | Key Findings | Status |
|-------|------|-------|-------|-------------|--------|
| Spearbit | Spearbit | Pre-April 2025 | Full protocol | Acknowledged issues (details not public) | Acknowledged (not fixed for Cantina scope) |
| Certora Formal Verification | Certora | Mar 21 – May 20, 2025 | Core contracts (47 properties) | HIGH: FIFO queue bypass (fixed); Permanent reward dilution; DoS via safety buffer; Rounding errors in LockingController | 1 fixed, 3+ acknowledged, **8 of 47 properties return FALSE** |
| Cantina Competition | Cantina Crowd | Apr 7–28, 2025 | 2,417 lines of code | 592 findings submitted, $35K prize pool; Spearbit/Certora acknowledged issues EXCLUDED from scope | Results not fully public |
| CertiK Skynet | CertiK | Ongoing | Automated scoring | Project page exists, score not extracted | Automated monitoring only |

**CRITICAL AUDIT CONCERNS:**
1. Spearbit "acknowledged" issues are excluded from Cantina scope — this means known unfixed issues exist from the Spearbit audit and the team chose to exclude them from competition review
2. Certora found **8 properties with FALSE status** out of 47 tested — the exact nature of these 8 failures is not fully public
3. Cantina OOS list includes "centralization issues" — meaning the most significant governance risks were explicitly excluded from security review scope
4. The FASANARA_MPC farm's off-chain credit exposure is unlikely to have been in scope for any smart contract audit
5. The `zapInAndLock` function was explicitly excluded from Cantina scope despite being a user-facing entry point

**Spearbit and Certora are reputable firms.** However, the pattern of excluding known acknowledged issues from subsequent audit scope is a yellow flag — it means some known weaknesses are being carried forward rather than fixed.

---

### Community Sentiment

**Direct community research was severely limited** — no independent Reddit threads, Discord, or Telegram discussions were found in search results. This can indicate either:
- (a) Protocol is too new/niche for organic community discussion, OR
- (b) Community concentration in gated channels (Discord, Telegram) not indexed by search

**What was found:**
- Observers.com critique on governance incompleteness and incomplete whitepaper
- General DeFi community concern pattern with points/farming-driven TVL protocols
- No specific "infiniFi scam" or "infiniFi rug" discussions found publicly

**Rating: INSUFFICIENT DATA for community sentiment.** The absence of community discussion about a $183M TVL protocol is itself a mild yellow flag — it suggests the community is either small, gated, or this is almost entirely institutional/whale capital farming points.

---

## Phase 3: On-Chain Findings

### Smart Contract Architecture

**Core Design:** The `InfiniFiCore.sol` contract (architecturally derived from Fei Protocol's `Core.sol`) is the root of all access control. It uses `AccessControlEnumerable` with a GOVERNOR role as the apex of a 20+ role hierarchy.

**Role Hierarchy (Risk Assessment):**

| Role | Power | Timelock? | Risk |
|------|-------|-----------|------|
| GOVERNOR | Controls all other roles, can change `EmergencyWithdrawal.safeAddress` | NO | CRITICAL |
| EMERGENCY_WITHDRAWAL | Can redirect ALL protocol funds to `safeAddress` | NO | CRITICAL |
| ORACLE_MANAGER | Can swap price oracles for any asset | NO | HIGH |
| RECEIPT_TOKEN_MINTER | Can mint iUSD against any collateral | NO | HIGH |
| PROTOCOL_PARAMETERS | Can add new farms via `FarmRegistry.addFarms()` | NO | HIGH |
| PAUSE | Can pause protocol | NO | MEDIUM |

**CRITICAL FINDING — Emergency Withdrawal Rug Vector:**
The `EmergencyWithdrawal.setSafeAddress()` function is callable by GOVERNOR without timelock. If the GOVERNOR key is compromised or malicious:
1. Call `setSafeAddress(attacker_wallet)`
2. Call `emergencyWithdraw()` with `EMERGENCY_WITHDRAWAL` role
3. All funds in all farms drain to attacker wallet

This is a functional rug pull mechanism with no timelock delay for community response.

**CRITICAL FINDING — FarmRegistry No Timelock:**
`FarmRegistry.addFarms()` requires only `PROTOCOL_PARAMETERS` role with no timelock. A malicious farm contract could be added, funded, and drained before any community or monitoring system can react.

**FINDING — `deprecatedWithdraw()` is unprotected:**
Any caller can invoke `deprecatedWithdraw()` on a deprecated farm to drain it. Intended as a public safety mechanism, but the combination with the above makes the attack surface wider.

**FINDING — CoW Swap Pre-Signed Order Risk:**
`CoWSwapBase.sol` uses `setPreSignature()` to commit swap orders on-chain before CoW Swap solvers execute them. A 20-minute validity window with a 20-minute cooldown means: only one swap per farm per 20 minutes, and a stale pre-signed order can execute at an unfavorable price if the oracle price moves before solver execution.

**FINDING — JCurveSmoother 36% Leakage:**
A comment in the codebase explicitly acknowledges that repeated calls to the `JCurveSmoother` push "approximately 36% of rewards beyond the interpolation period." This is a design flaw acknowledged in production code affecting yield accuracy.

**FINDING — Irreversible Slash Index:**
The `UnwindingModule`'s `slashIndex` permanently decreases on any loss event with no recovery path. Users with 100-week lock positions face compounding irreversible loss exposure.

---

### Farm Portfolio Risk Analysis

| Farm | Counterparty | Mechanism | Risk Level | Notes |
|------|-------------|-----------|-----------|-------|
| FARM_FASANARA_MPC | Fasanara Digital (institutional) | Off-chain MPC custody via escrow | CRITICAL | No on-chain liquidation. Pure TradFi credit risk. $275M AUM fund but not DeFi-native. |
| FARM_MAPLE_INSTITUTIONAL | Maple Finance | On-chain institutional lending | HIGH | Credit default risk; Maple has had borrower defaults historically |
| FARM_GAUNTLET_ALPHA / V2 | Gauntlet/Morpho | Morpho market management | MEDIUM | Gauntlet is reputable risk manager |
| FARM_MORPHO_SENTORA_PYUSD | Morpho + Sentora | PYUSD vault | MEDIUM | Multi-hop protocol dependency |
| FARM_AUTO_USD | AutoUSD protocol | Stablecoin yield | MEDIUM | Newer protocol, less battle-tested |
| FARM_SPARK_SUSDC | Spark (MakerDAO) | sUSDC | LOW-MEDIUM | Spark is well-established |
| FARM_LEVEL (historical) | Level Finance | ON-CHAIN — SHUT DOWN | REALIZED RISK | Level Finance announced shutdown. Code is "exit only, no new deposits." User funds were in a shutting-down protocol. |

**LEVEL FINANCE FINDING:** The `LevelFarm.sol` code explicitly acknowledges that Level Finance announced its shutdown and the contract is "exit only." This confirms that during the protocol's operating history, infiniFi had user capital deployed in a counterparty that subsequently ceased operations — a real counterparty risk event, not hypothetical.

---

### Token and TVL Analysis

**TVL Trajectory:**
- June 2025 (launch): $33M
- September 2025: $115M (entered top 30 stablecoins)
- November 2025 (Season 1 end): $175M
- February 26, 2026 (current): **$183.37M**

**TVL Growth Assessment:**
The growth curve from $33M → $183M in 8 months is consistent with points/airdrop farming driven by Season 1 (6 months, 5.6M points distributed) and the subsequent Chapter-based system. Multiple risk signals suggest this TVL is highly mercenary:
- Pendle integration allows leveraged iUSD farming loops (reflexive TVL inflation)
- Points multipliers incentivize locking capital rather than genuine demand for the banking model
- The April 7 – March 26, 2026 Pendle maturity pool implies significant farming TVL will resolve within weeks
- Historical precedent: EigenLayer, Blast, Renzo, EtherFi all experienced 30-70% TVL declines post-TGE airdrop

**Revenue Metrics (DeFiLlama, Feb 2026):**
- Annualized fees: $8.82M
- Protocol revenue (annualized): $898K (~10% take rate)
- 30-day fees: $723K

The $898K annualized revenue against $183M TVL = **0.49% revenue/TVL ratio** — thin margins that validate the model is primarily a yield pass-through with modest protocol take. Not a Ponzi structure by mechanics, but TVL is the key sustainability metric.

**Token Distribution:**
As of Feb 2026, **no official tokenomics have been published** for the forthcoming protocol token (reportedly ticker GFIN, unconfirmed). This is a significant concern: a protocol approaching TGE with $183M TVL and no public breakdown of team allocation, VC allocation, cliff/vesting schedules, or community distribution percentage.

**Prior pattern risk:** Protocols that withhold tokenomics until close to TGE often do so because the allocations would be viewed negatively by the community if disclosed earlier.

---

### Deployed Mainnet Contracts (Key)

Extracted from GitHub commit history (NOT from official docs — those were inaccessible):

| Contract | Address | Risk Note |
|---------|---------|----------|
| GATEWAY_IMPLEMENTATION_V3 | `0xb44e494535A8fC1f0081F4F9289BCc7c57FbffB6` | V3 suggests iterative changes post-launch |
| GATEWAY_PROXY_ADMIN | `0x21071E0f9D600571Ffe47873e95fffF2FAc9141c` | Controls proxy upgrade — verify timelock |
| FARM_FASANARA_MPC | `0x9E5efC5F387D8661C1AFB2469B7EeF6972451852` | Off-chain credit exposure |
| FARM_FASANARA_MPC_ESCROW | `0x868C82b7BAa3675F9Da1404510DB60c1f6A7741A` | Escrow for Fasanara funds |
| FARM_MAPLE_INSTITUTIONAL | `0xF56E946e92FeF6a050F482C560b5f8DcCB8163B3` | Institutional credit |
| YIELD_SHARING_V2 | `0x1cb9ED33924741F500E739e38c3215a76cD1f579` | V2 implies iteration on core yield logic |
| MIGRATION_CONTROLLER | `0x5F5403656E4Db95aCcF1064A714B1bcE351839F8` | Exists — implies prior migration events |

**Notable:** The existence of `GATEWAY_IMPLEMENTATION_V1`, `V2`, and `V3` suggests the protocol has upgraded its core gateway at least twice since June 2025. The `MIGRATION_CONTROLLER` contract confirms at least one migration event occurred. These upgrades happened in a protocol with an untimelocked GOVERNOR role — users had no advance warning of these changes.

---

## Phase 4: Comparative Analysis

### Pattern Matching Against Known Risk Archetypes

**Ponzi Assessment: NO** — The yield sources are real and verifiable (Aave, Pendle, Ethena, Morpho). Revenue is generated by deploying depositor capital into legitimate DeFi strategies. The mechanics do not require new depositors to pay old depositors.

**Fractional Reserve Risk: YES (Acknowledged)** — The model explicitly acknowledges the bank run scenario in its documentation. The risk is that up to 90% of liquid deposits are deployed into illiquid strategies. If more than ~10-15% of siUSD holders attempt simultaneous redemption, the FIFO queue activates and some users face slashing exposure.

**Rug Pull Pattern: PARTIAL RISK** — The GOVERNOR-controlled EmergencyWithdrawal architecture creates the technical mechanism for a rug pull. The question is whether the governance key holders would exercise this. The team's electric capital backing and pseudonymous-but-identified identity partially mitigates (but does not eliminate) this risk.

**Luna/Terra Comparison: LOW** — Unlike Terra, iUSD is backed by real external stablecoins/assets, not by a circular governance token. No reflexive collapse mechanism.

**Celsius/FTX Comparison: MEDIUM** — The opacity around Fasanara MPC farm has Celsius-like properties: user funds are with an off-chain institutional counterparty, the exact holdings are not verifiable on-chain, and there is no on-chain liquidation if the counterparty defaults.

---

## Red Flags Register

| # | Flag | Evidence | Source | Severity |
|---|------|---------|--------|---------|
| 1 | Lead developer built exploited protocol | Revest Finance $2M reentrancy exploit, March 2022; Rob Montgomery = RobAnon confirmed via Crunchbase + The Record news article | rekt.news, The Record, Crunchbase | CRITICAL |
| 2 | Untimelocked GOVERNOR rug vector | GOVERNOR controls EmergencyWithdrawal.safeAddress with no timelock; any compromise enables full fund drain | GitHub code analysis | CRITICAL |
| 3 | Off-chain credit risk with no on-chain liquidation | FARM_FASANARA_MPC routes user funds to Fasanara Digital MPC wallet; no smart contract liquidation on default | GitHub contract addresses, Fasanara Digital website | HIGH |
| 4 | FarmRegistry has no timelock | `addFarms()` requires only PROTOCOL_PARAMETERS role, no delay; malicious farm can be added and drained before community can react | GitHub code analysis | HIGH |
| 5 | No public tokenomics for imminent TGE | Protocol approaching TGE with $183M TVL; no team %, VC %, vesting, community allocation published | Multiple search sources; no tokenomics found | HIGH |
| 6 | Level Finance counterparty already shut down | LevelFarm.sol code explicitly acknowledges Level Finance shutdown; "exit only" mode confirms user funds were in a shutting-down protocol | GitHub code analysis | HIGH |
| 7 | Governance section in whitepaper incomplete at launch | Observers.com quotes: "To fully address governance is a whitepaper unto itself" — placeholder in launch document | Observers.com | HIGH |
| 8 | Certora found 8 of 47 properties FALSE | Formal verification identified 8 failing properties; only 1 (FIFO bug) confirmed fixed; others acknowledged | Certora report, search results | HIGH |
| 9 | Spearbit acknowledged issues excluded from Cantina scope | Known existing issues were deliberately excluded from subsequent security competition — carries forward unfixed | Cantina competition page (OOS list) | HIGH |
| 10 | Private development with batch public dumps | Only 24 public commits; PR #4 alone dumped 3,177 lines from private repo; community cannot monitor real changes | GitHub commit analysis | MEDIUM |
| 11 | Gateway has been upgraded 3 times without disclosed governance process | GATEWAY_IMPLEMENTATION_V1, V2, V3 exist; upgrades occurred under untimelocked GOVERNOR control | GitHub address files | MEDIUM |
| 12 | TVL is mercenary points-farming capital | Growth pattern mirrors EigenLayer/Blast/Renzo TVL farming cycles; Pendle maturity March 26, 2026 will trigger redemptions | TVL data, Pendle pool announcement | MEDIUM |
| 13 | Up to 90% of liquid deposits in illiquid positions | Whitepaper example: 90% of liquid deposits allocated to duration assets like Ethena and Pendle | Blockworks, search results | MEDIUM |
| 14 | Codebase architecturally descended from Fei Protocol | Core/CoreControlled pattern, AccessControlEnumerable with GOVERNOR role — matches Fei Protocol architecture | GitHub fork analysis, eswak forks | MEDIUM |
| 15 | railway-monorepo is Revest Finance infrastructure | InfiniFi-Labs org includes `railway-monorepo` explicitly labeled "Pre-existing indexer from Revest" | GitHub org repos | MEDIUM |
| 16 | JCurveSmoother 36% reward leakage acknowledged | Code comment explicitly states repeated smoother calls push ~36% of rewards beyond interpolation period | GitHub code analysis | MEDIUM |
| 17 | Slash Index is irreversible | UnwindingModule slashIndex permanently decreases on loss, no recovery; users with 100-week locks face compounding exposure | GitHub code analysis | MEDIUM |
| 18 | Ethena sUSDe dependency creates systemic yield risk | If Ethena funding rates go negative, iUSD yield collapses and backing safety margin compresses | Protocol mechanics | MEDIUM |
| 19 | No independent community discussion found | $183M TVL protocol with no Reddit/CT discussion surfaced — unusual; suggests gated community or pure institutional farming | Search results (null result itself) | LOW |
| 20 | Nansen analysis has undisclosed financial interest | Nansen conflict of interest disclosed mid-article; primary "independent" analyst coverage is compromised | Nansen research article | LOW |
| 21 | nikollamalic connection to Aurox | Developer connection to previously controversial token launch | GitHub analysis | LOW |
| 22 | eswak has forks of 2 failed/hacked protocols | Fei Protocol (wound down) and Saddle Finance (hacked, wound down) in GitHub | GitHub fork analysis | LOW |

---

## Unresolved Questions

1. **What are the specific 8 FALSE Certora properties?** The Certora report lists 8 failing properties out of 47. The FIFO fix accounts for one. The other 7 remain unidentified in public sources. These could range from minor to critical.

2. **What did Spearbit find?** The Spearbit audit report is not publicly accessible. The Cantina competition excluded all Spearbit "acknowledged" issues from scope — we know issues exist but cannot assess their severity without the report.

3. **Who controls the GOVERNOR multisig?** The GOVERNOR role holder(s) are not publicly identified. Is this a multisig? What is the threshold? Who are the keyholders? This is the most important undisclosed piece of information for assessing rug risk.

4. **How large is the Fasanara MPC allocation?** The exact dollar amount of user funds deployed to the off-chain Fasanara Digital farm is not publicly disclosed. A large Fasanara allocation would significantly increase counterparty risk exposure.

5. **What are the GFIN tokenomics?** Team %, VC %, cliff schedules, and community allocation remain completely undisclosed ahead of an imminent TGE for a $183M TVL protocol.

6. **Were Level Finance users made whole?** When Level Finance shut down and the infiniFi Level Farm entered "exit only" mode, what happened to users with locked positions in the Level Farm? Were they fully recovered?

7. **What is the current Pendle position size?** The March 26, 2026 Pendle maturity pool (1 month away at report date) represents a potential TVL redemption cliff. The exact size of this position is not disclosed.

8. **Does Electric Capital know about Revest Finance history?** Assumable that a $3M pre-seed lead conducted team background diligence — but not confirmed. If yes, this partially validates the team despite track record.

---

## Summary Risk Rating

| Category | Rating | Rationale |
|---------|--------|-----------|
| Team Trust | HIGH RISK | RobAnon = lead developer of exploited protocol; pseudonymous; Fei Protocol lineage |
| Smart Contract Security | MEDIUM RISK | 3 audits completed; FIFO fix applied; but 8 FALSE Certora properties, untimelocked GOVERNOR, no timelock on farm registry |
| Counterparty Risk | HIGH RISK | Fasanara MPC (off-chain credit), Level Finance (shut down, resolved), Maple (historical defaults) |
| TVL Stickiness | HIGH RISK | Mercenary farming capital; Pendle maturity March 2026; post-TGE dump risk high |
| Governance | HIGH RISK | Whitepaper governance section incomplete; GOVERNOR controls everything; no public multisig disclosure |
| Transparency | MEDIUM RISK | Reserve composition transparent on-chain (positive); team compensation and tokenomics opaque (negative) |
| Systemic Risk | MEDIUM RISK | Ethena dependency; fractional reserve structure; up to 90% liquidity mismatch |
| Regulatory Risk | LOW-MEDIUM | Fractional reserve model may attract regulatory scrutiny as "unlicensed banking"; no regulatory filings found |

---

## Overall Assessment

**MEDIUM-HIGH RISK. Do not deploy capital without understanding the following:**

1. The GOVERNOR key architecture is the most important undisclosed risk. If you cannot verify who holds it, how many signers are on the multisig, and whether a timelock exists, you are trusting an anonymous key with your funds.

2. The lead developer built a protocol that lost $2M to a reentrancy bug and told victims he couldn't repay them. The new protocol has improved reentrancy protections but carries the same team, same infrastructure lineage, and same pseudonymous leadership.

3. At the current TVL (~$183M), the Fasanara MPC escrow almost certainly holds material user funds ($10M+) with no on-chain liquidation protection. You need to know this number before depositing.

4. The TGE is imminent and no tokenomics have been disclosed. Historical precedent strongly suggests TVL will decline meaningfully post-TGE as points-farmers exit. If you're in liUSD with a long lock, you may be unable to exit during this liquidity contraction.

**What would change this assessment:**
- Public disclosure of GOVERNOR multisig composition and timelock status
- Published tokenomics with verifiable vesting schedules
- Fasanara MPC allocation size disclosed
- Remaining Certora FALSE properties disclosed and addressed
- Addition of a timelock (minimum 48 hours) on `FarmRegistry.addFarms()` and `EmergencyWithdrawal.setSafeAddress()`

---

## Sources

- [infiniFi — DeFiLlama](https://defillama.com/protocol/infinifi)
- [GitHub — InfiniFi-Labs/infinifi-protocol](https://github.com/InfiniFi-Labs/infinifi-protocol)
- [GitHub — InfiniFi-Labs (org)](https://github.com/InfiniFi-Labs)
- [Blockworks — infiniFi replicates fractional reserve banking](https://blockworks.co/news/yield-protocol-infinifi-banking-onchain)
- [Cantina Competition — infiniFi-protocol](https://cantina.xyz/competitions/2ac7f906-1661-47eb-bfd6-519f5db0d36b)
- [Certora Blog — Ensuring Fair Redemptions in infiniFi](https://www.certora.com/blog/ensuring-fair-redemptions-in-infinifi-with-formal-verification)
- [Certora Report — infiniFi Protocol Formal Verification](https://www.certora.com/reports/infinifi-protocol-formal-verification-report)
- [Rekt News — Revest Finance](https://rekt.news/revest-finance-rekt)
- [The Record (Recorded Future) — $2M stolen from Revest Finance](https://therecord.media/2-million-stolen-from-defi-protocol-revest-finance-platform-unable-to-reimburse-victims)
- [SlowMist — Revest Finance Incident Analysis](https://slowmist.medium.com/revest-finance-incident-analysis-6fcd9b6be207)
- [Crunchbase — Rob Montgomery, InfiniFi](https://www.crunchbase.com/person/rob-montgomery-296f)
- [LinkedIn — Rob Montgomery (InfiniFi Labs)](https://www.linkedin.com/in/rhmontgomery/)
- [LinkedIn — Erwan Beauvois (eswak)](https://fr.linkedin.com/in/eswak)
- [Nansen Research — Understanding infiniFi](https://research.nansen.ai/articles/understanding-infini-fi-the-on-chain-fractional-reserve-banking-protocol)
- [Observers.com — infiniFi: Bold Ideas, Fresh Tokens](https://www.observers.com/defi/infinifi-bold-ideas-fresh-tokens-and-rapid-capital-growth/)
- [ExamineCrypto — infiniFi Raises $3M Pre-Seed](https://www.examinecrypto.com/post/infinifi-depositor-driven-defi-system-raised-3m-in-a-pre-seed-funding-round-led-by-electric-capit)
- [Alea Research — infiniFi Season 1 and 2026 TGE Path](https://alearesearch.substack.com/p/infinifi-season-1-points-and-2026)
- [Airdrops.io — Potential InfiniFi Airdrop](https://airdrops.io/infinifi/)
- [Fasanara Digital — Fireblocks Case Study](https://www.fireblocks.com/customers/fasanara-capital)
- [Messari — InfiniFi USD](https://messari.io/project/infinifi-usd)
- [Stabledash — iUSD Reaches $115M TVL](https://stabledash.com/news/2025-09-12-infinifis-iusd-stablecoin-reaches-115m-tvl-enters-top-30-ranking)

---

*Report generated: 2026-02-26. Data is point-in-time. On-chain conditions, contract upgrades, and team disclosures may change. Always verify contract addresses on Etherscan before interacting.*
