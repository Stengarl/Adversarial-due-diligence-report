# Fira Protocol (fira.money) — Adversarial Due Diligence Report

**Research Date:** February 25, 2026
**Investigator:** DeFi Adversarial Research Agent
**Classification:** MEDIUM-HIGH RISK — Legitimate underlying architecture, critical gaps in audit coverage and team transparency
**Confidence Level:** Medium (limited by JS-rendered site, anonymous team, no GitHub)

---

## EXECUTIVE SUMMARY

Fira Protocol (fira.money) is a fixed-rate DeFi lending protocol launched on Ethereum Mainnet on January 14–22, 2026 — **just five weeks before this report.** It is deeply integrated with Usual Protocol's USD0 stablecoin ecosystem, functioning as Usual's protocol-owned, DAO-governed credit engine. Its first live market, **Usual Zero Rate (UZR)**, enables zero-rate borrowing of USD0 against bUSD0 collateral with a maturity of June 11, 2028. The USLLendingMarket contract currently holds approximately **$450M** in assets, primarily inherited from migrated Euler USL positions.

Fira is NOT an independent rug-pull vector in the traditional sense — it operates within an established ecosystem (Usual) with real TVL and real institutional backing. However, it carries **critical transparency deficiencies**: no publicly named team, no published audit for Fira-specific smart contracts despite managing $450M, and heavy systemic dependency on a protocol (Usual) that suffered a significant depeg crisis in January 2025 amid insider trading allegations.

**Verdict:** This is a legitimate DeFi product embedded in a controversial ecosystem, with concerning audit gaps at the contract level. Not a rug pull — but not safe for users who haven't done deep research.

### Top 3 Risks
1. **No published audit for Fira's deployed contracts** (USLLendingMarket, SisuVault, deployed Nov–Dec 2025) despite $450M TVL
2. **Systemic dependency on Usual Protocol**, which previously depegged USD0++ and whose founder had undisclosed conflicts of interest with MEV Capital
3. **Anonymous team and anonymous deployer chain** — no independently verifiable developer identities

### Top 3 Positive Signals
1. $450M TVL reflects meaningful market adoption; the system migrated Euler's entire USL book successfully
2. Oracle is immutable Chainlink-based with no admin override capability
3. Usual Protocol's core contracts (USD0, bUSD0) have extensive audit coverage from top-tier firms (Sherlock, Cantina, Spearbit, Halborn) spanning May 2024 through November 2025

---

## PHASE 1: TEAM ASSESSMENT

### 1.1 Protocol Ownership & Attribution

**UNVERIFIED CLAIM:** Fira describes itself as "protocol-owned, DAO-governed" and aligned with Usual's architecture. This implies the Usual DAO controls Fira.

**INDEPENDENTLY VERIFIED:** Usual Protocol was founded by:
- **Pierre Person** — CEO and Co-Founder, Usual Labs
- **Adli Takkal Bataille** — DEO (Design Executive Officer), Co-Founder, Usual Labs; previously Partner & Strategy Advisor at Ø Crypto Union; President of Le Cercle du Coin

Usual Labs raised **$8.5M total**: $7.5M strategic round (April 2024) from IOSG Ventures, Kraken Ventures, GSR Ventures, Mantle, and others.

**CRITICAL GAP:** No named developers or founders for *Fira specifically* have been publicly identified. The project presents itself as part of Usual but the deployer addresses are anonymous.

### 1.2 Deployer Address Analysis

**Fira Vault Deployer:** `0x7Da82CBD315923d75dBb2c62f099392705FF97f9`
- **No Etherscan name tag** — unlabeled, anonymous
- **First funded:** August 27, 2025, approximately 90 days before report date
- **Funded by:** `0xbb927BC1d844c372282A4E6346b182F3884693bb` (also unlabeled, 2 total transactions, funded by `0x6942eeC2...ba786e7C3`)
- **Contracts deployed by this address:**
  - SisuVaultPriceFeed — December 29, 2025
  - USLMigrator — December 3, 2025
  - PermissionedSisuVaultFactory — November 27, 2025
  - StaleOracleFeed — November 27, 2025
  - ChainlinkOracleV2 — November 2025
  - USLLendingMarket (UZR Vault) — ~90 days ago

**This deployer is DISTINCT from the Usual Deployer** (`0xab175f3ed4e9e021fa491ae12c7a08d85b27feef`), which deployed the bUSD0 token.

**Assessment:** The use of an unlabeled deployer funded through a chain of anonymous EOAs, rather than Usual's established deployer, is a **MEDIUM-severity concern**. It could indicate a separate developer team contracted by Usual, or a privacy-preserving operational pattern. Without more transparency, the ultimate controlling party cannot be independently confirmed.

### 1.3 GitHub Analysis

**FINDING:** No GitHub repository found under any variant searched:
- github.com/fira-protocol — 404
- github.com/firaprotocol — 404
- github.com/firamoney — 404

No public code repository means the contract source code can only be read through Etherscan (which does have the contracts verified), but the full development history, test coverage, and deployment scripts are not publicly auditable. The absence of a GitHub is **atypical for legitimate DeFi protocols** claiming to be infrastructure-level.

### 1.4 Social Media Forensics

- **Twitter/X:** @fira_money referenced in Usual's announcement posts but account has minimal independent presence searchable through standard tools
- **Website:** fira.money — Framer-built single-page site (sitemap.xml confirms only 1 URL), orange branding (#fc5700)
- **Documentation:** docs.fira.money (exists), app.fira.money (live), simulator.fira.money (live)
- **Telegram/Discord:** No public community found
- **Reddit:** No discussions found on r/DeFi, r/CryptoCurrency, or r/ethfinance
- **Medium/Substack:** No team blog posts found; all coverage via Usual's blog

**Assessment:** Social media footprint is minimal for an independent protocol, consistent with it being a Usual sub-product rather than an independently marketed project. However, the absence of community channels is a transparency gap.

---

## PHASE 2: THIRD-PARTY INTELLIGENCE

### 2.1 Independent Coverage

**Coverage found:**
- [Blockworks](https://blockworks.co/news/usual-depeg-spurs-defi-instability): Covered the Usual USD0++ depeg crisis (January 2025) and its DeFi market impact — critical context for Fira
- [Usual Blog](https://usual.money/blog/usual-zero-rate-a-native-credit-primitive-for-usd0): Official announcement of UZR/Fira integration
- No coverage found from: The Defiant, Rekt News, DL News, Decrypt, CoinDesk, or independent DeFi researchers

**Assessment:** Fira has effectively zero independent analyst coverage. All published information derives from Usual's own marketing channels. This is consistent with a very new (5-week-old) protocol but means no independent verification of claims exists.

### 2.2 Audit and Security Assessment

**Usual Protocol Audits** (covering core USD0/bUSD0 contracts — NOT Fira's vault contracts):

| Date | Auditor(s) | Scope |
|------|-----------|-------|
| May 2024 | Cantina | Mint engine, launch contracts |
| Jun 2024 | Cantina | Public security competition |
| Oct 2024 | Paladin | L2 token contracts, OFT adapters |
| Nov 2024 | Cantina, Halborn, Sherlock | bUSD0, DAO Collateral, USUAL token |
| Dec 2024 | Blackthorn, Cantina | WrappedM, bUSD0 unwrap, USUALx |
| Jan 2025 | Spearbit | Claim Redirect, DistributionModule, bUSD0 |
| **Feb 2025** | **Sherlock, Spearbit, OAK Security** | **Euler USL vault/oracle, USL Economic Risk** *(closest to Fira)* |
| Mar 2025 | Sherlock, Spearbit, Halborn | bUSD0 Investment Vault |
| May 2025 | Hexens, Halborn, Sherlock, Spearbit | ETH0, USUALx Lockup |
| Jul 2025 | Sherlock, Spearbit | bUSD0 Upgrade (Burn Redemption) |
| Oct 2025 | Sherlock | EUR0 |
| Nov 2025 | Hexens, Halborn, Sherlock | sUSD0, sEUR0, bUSD0 Upgrade |

**⚠️ CRITICAL GAP: The Fira-specific contracts (USLLendingMarket, SisuVault, ChainlinkOracleV2, USLMigrator, PermissionedSisuVaultFactory — all deployed November–December 2025) do NOT appear in any published audit.** The audit list extends only through November 2025 and does not cover the contracts deployed for Fira's live vaults.

The February 2025 Sherlock audit of "Euler USL vault/oracle" covered the *predecessor* system (the Euler-based USL), which Fira migrated users away from. Whether that audit's findings were incorporated into Fira's new contract design is unknown.

**Etherscan note:** The USLLendingMarket Etherscan page shows "No Contract Security Audit submitted" — consistent with no published audit.

### 2.3 Community Sentiment

**No community discussion found.** The protocol has no publicly visible community forums. The Usual Discord and Telegram are presumed to carry discussion, but no protocol-specific Fira community exists to surface independent critique.

---

## PHASE 3: ON-CHAIN FINDINGS

### 3.1 Contract Architecture

**Ethereum Mainnet Contracts:**

| Contract | Address | Notes |
|----------|---------|-------|
| USLLendingMarket (UZR Vault) | `0xa428723eE8ffD87088C36121d72100B43F11fb6A` | Main lending contract; $450M TVL |
| bUSD0 Token | `0x35D8949372D46B7a3D5A56006AE77B215fc69bC0` | TransparentUpgradeableProxy (ERC1967) |
| rt-bUSD0 | `0x82DCA22b48B14DE38ccf83B03330120c4b8acFe9` | Return token |
| Oracle (ChainlinkOracleV2) | `0x30Da78355FcEA04D1fa34AF3c318BE203C6F2145` | Immutable Chainlink-based |
| Sisu Vault | `0xFE7C47895eDb12a990b311Df33B90Cfea1D44c24` | Secondary vault |
| USD0 (Usual) | `0x73A15FeD60Bf67631dC6cd7Bc5B6e8da8190aCF5` | Core stablecoin (separate Usual contract) |

**USLLendingMarket Analysis:**
- Deployer: Anonymous (see Team section)
- Verified source code: Yes (Exact Match)
- Compiler: Solidity v0.8.30, EVM Prague, optimization enabled (200 runs)
- **Current Holdings:** ~$434.5M in bUSD0 + ~$16.3M USD0 = ~$450M total
- **Transactions:** 437 total, live borrow activity confirmed
- **Admin functions identified:** `setUslLiquidator()`, `setFee()`, `setFeeRecipient()`, owner-controlled market creation
- **Flash loan capability:** PRESENT — standard but adds attack surface
- **Pause mechanism:** Not visible in primary contract analysis
- **Special function:** `liquidateExpiredUSL()` — liquidates positions when USD0++ (note: USD0++, not USD0) reaches maturity plus grace period. This function name is confusing given bUSD0 is the collateral; further review needed.

**bUSD0 Token Analysis:**
- Deployer: Usual: Deployer (`0xab175f3ed4e9e021fa491ae12c7a08d85b27feef`) — this IS the main Usual deployer ✓
- Deployed: June 5, 2024 (predates Fira's launch by ~18 months)
- **Proxy type:** TransparentUpgradeableProxy (ERC1967) — implementation at `0x9F2BD21b...3a89BC85B`
- **UPGRADE RISK:** ProxyAdmin can upgrade the bUSD0 implementation, potentially altering behavior
- Contract holds ~$525M in USD0 backing all outstanding bUSD0
- No Etherscan security audit tag submitted

**Oracle Analysis:**
- Contract: ChainlinkOracleV2
- **Immutable:** All parameters (feed addresses, vault addresses, scale factor) set at deployment; NO admin controls
- Uses Chainlink AggregatorV3Interface + ERC4626 vault conversions
- **Cannot be manipulated by any party post-deployment** — positive security property
- Deployer: same anonymous deployer as vault

### 3.2 Token Distribution Analysis

The FIRA token found on Etherscan (`0xef764855f98c5ef9cbe29b908510dd4e101616d1`) with 45 holders and TokenMint deployment appears to be an **unrelated legacy token** — likely from Defira/Defiraverse (a separate Harmony blockchain project). Fira Protocol (fira.money) does not appear to have its own native token; it operates with Usual's token stack (USD0, bUSD0, USUAL).

### 3.3 TVL and Activity Analysis

- The USLLendingMarket contains assets migrated from Euler's USL (Usual Stability Loan) positions that reached $400M within six months of operation
- The one-way migration from Euler → Fira means these positions are locked in Fira until June 2028 maturity
- The LLTV of 99.99% with a 0% borrow rate means **virtually no liquidations will occur before maturity** — all protocol risk is deferred to June 2028
- Active borrow operations confirm real user activity (not simulated volume)

### 3.4 Suspicious Pattern Analysis

**⚠️ One-way migration:** The migration from Euler's USL to Fira was one-directional. Users who migrated cannot exit back to Euler. This effectively gives Fira custodial control over $400M+ in positions until June 2028 with no exit.

**⚠️ Maturity concentration:** By design, all the risk (borrowers redeeming bUSD0 for USD0) concentrates at a single date: June 11, 2028. If Usual's treasury or USD0 peg has issues at that date, there could be a systemic redemption failure. This is a structural risk, not fraud, but it is a design concern.

**⚠️ Upgradeability:** bUSD0 is an upgradeable proxy. While Usual has a solid audit history for bUSD0 upgrades, the upgrade key introduces centralization risk.

---

## PHASE 4: COMPARATIVE ANALYSIS

### 4.1 Comparison to Known Failure Patterns

| Pattern | Status in Fira |
|---------|----------------|
| Anonymous team | ⚠️ YES — no public developers identified |
| No audit on live contracts | ⚠️ YES — Fira-specific contracts unaudited (publicly) |
| Ruggable admin keys | PARTIAL — vault has admin functions; oracle is immutable |
| Unrealistic yields | NO — 0% borrow rate is the product (not a promise of high returns) |
| Ponzi tokenomics | NO — no native token, revenue model is straightforward |
| Wash trading / fake TVL | NO — TVL is migration of real historical Euler positions |
| Fake partnerships | NO — Usual integration is verifiable on-chain |
| Excessive centralization | PARTIAL — proxy upgrade risk; one-way migration lock-in |

### 4.2 Comparison to USD0++ Depeg Event

The January 2025 USD0++ depeg crisis is the closest historical analog:
- **USD0++:** A 4-year locked version of USD0 that users believed was 1:1 redeemable any time. The protocol changed the floor to $0.87 without adequate warning, causing liquidation cascades on Morpho.
- **bUSD0 (in Fira):** A zero-coupon bond with a fixed June 2028 maturity. Designed explicitly as a maturity instrument from day one — the "discount to par" behavior is the feature, not a bug.

**Key difference:** bUSD0 was never marketed as a 1:1 stable instrument before maturity. The USD0++ crisis was partly caused by user misunderstanding. bUSD0's design is more transparent about its bond nature. However, if the broader USD0 ecosystem faces stress, Fira positions are equally exposed since USD0 is the loan token.

### 4.3 Sustainability Assessment

- **Yield source:** 0% borrow rate is funded by the protocol (Usual DAO absorbs the cost) — this is intentional and disclosed
- **Fixed Rate markets (Q1 2026):** The planned expansion to real fixed-rate markets will create actual interest income, but those contracts don't yet exist on-chain
- **Dependencies:** Fira is fully dependent on:
  1. USD0 maintaining its peg (backed by T-bills — verifiable but not risk-free)
  2. Usual DAO governance acting in users' interests
  3. The integrity of bUSD0's redemption mechanism at June 2028 maturity
  4. Ethereum network functionality

---

## RED FLAGS REGISTER

| # | Flag | Severity | Evidence | Why It Matters |
|---|------|----------|---------|----------------|
| 1 | **No published audit for Fira vault contracts** | CRITICAL | tech.usual.money/audits shows no Fira contract coverage; Etherscan shows no submitted audit | $450M in assets managed by unaudited contracts (as of report date) |
| 2 | **Anonymous deployer chain** | HIGH | Etherscan: deployer unlabeled; funded by two-hop anonymous EOA chain | Cannot independently verify who controls upgrade keys or admin functions |
| 3 | **bUSD0 is an upgradeable proxy** | HIGH | Etherscan: TransparentUpgradeableProxy confirmed | ProxyAdmin can alter bUSD0 behavior, potentially affecting collateral value |
| 4 | **Usual founder conflict of interest (Adli/MEV Capital)** | HIGH | Blockworks investigation; Adli.eth was MEV Capital shareholder during USD0++ crisis | Raises questions about governance trustworthiness of the parent ecosystem |
| 5 | **One-way migration lock-in** | HIGH | app.fira.money/migrate documentation | Users who migrated cannot exit until June 2028 maturity — 2+ year lockup |
| 6 | **No public GitHub repository** | MEDIUM | Multiple GitHub org variants searched — all 404 | Cannot audit development history, test coverage, or deployment procedures |
| 7 | **Single-page marketing website** | MEDIUM | sitemap.xml: only one URL | Extremely sparse web presence for a protocol managing $450M |
| 8 | **No independent community** | MEDIUM | No Reddit, Discord, or Telegram found for Fira specifically | No independent error-checking or whistleblowing surface |
| 9 | **Maturity risk concentration (June 2028)** | MEDIUM | Confirmed from app.fira.money and simulator | All redemption pressure hits at one date; systemic if Usual has issues then |
| 10 | **USD0++ depeg precedent** | MEDIUM | Blockworks January 2025 coverage | The parent ecosystem (Usual) has already shown it can make unannounced changes that harm users |
| 11 | **Admin functions on USLLendingMarket** | MEDIUM | Etherscan source code: setFee(), setFeeRecipient(), setUslLiquidator() | Owner can adjust fee parameters and liquidation authority |
| 12 | **Flash loan capability** | LOW | Etherscan source code review | Adds attack surface; has been the entry vector for many DeFi exploits |
| 13 | **No pause mechanism confirmed** | LOW | Etherscan analysis (absence of visible pausing) | If exploit occurs, protocol may have no emergency stop capability |

---

## UNRESOLVED QUESTIONS

1. **Is there an undisclosed/private audit of Fira's contracts?** Usual may have commissioned audits not yet published. The November 2025 audit cycle ended just before Fira's contracts were deployed. An audit may be pending publication or conducted privately. *This is the most consequential unknown.*

2. **Who exactly are Fira's developers?** Are they Usual Labs employees, an external contracted team, or a pseudonymous external builder? The different deployer address from Usual's known deployer suggests at least partial separation.

3. **What controls ProxyAdmin of bUSD0?** The ProxyAdmin contract for the bUSD0 TransparentUpgradeableProxy has not been identified. If a single EOA or a small multisig controls it, upgrade risk is high. If it's a timelock with governance, risk is lower.

4. **What triggers `liquidateExpiredUSL()`?** This function references "USD0++ maturity plus grace period" — USD0++'s maturity date and bUSD0's maturity date (June 2028) may differ, creating confusion about when positions can be liquidated.

5. **Is the $434.5M in bUSD0 all from migrated Euler USL positions?** If so, the effective TVL Fira has "attracted" organically is closer to the $19.5M shown in the app's active UZR market — a different risk profile.

6. **What is the Usual governance structure's actual power over Fira?** "DAO-governed" is a claim; the technical reality of multisig keys vs. on-chain governance has not been independently verified.

7. **Who funded the ultimate wallet in the deployer chain (`0x6942eeC2...ba786e7C3`)?** Tracing further back might reveal whether this is Usual Labs' operational wallet or an external party.

---

## LESSONS LEARNED

*To be recorded in lessons.md*

1. **JS-rendered sites (Framer) are a major research obstacle.** Always probe subdomains (docs., app., simulator.) and robots.txt/sitemap first.

2. **Sitemap.xml is a fast indicator of site maturity.** A single-URL sitemap for a "$450M protocol" is a strong signal of marketing-first development.

3. **Deployer address forensics is high-value.** Comparing a protocol's vault deployer to its known core deployer can reveal whether a protocol is truly integrated or operating as a separate entity.

4. **"Protocol-owned, DAO-governed" is a marketing claim, not a verified technical state.** Always verify what governance actually controls what contracts.

5. **Audit lists have gaps.** Even protocols with extensive audit histories can have new contracts deployed between audit cycles. Check contract deployment dates against audit dates.

6. **On-chain TVL ≠ organic TVL.** A large inherited TVL from a migration doesn't indicate organic demand for the new protocol.

---

*Report generated: February 25, 2026*
*Research tools: WebSearch, WebFetch, Etherscan, docs.fira.money, app.fira.money, simulator.fira.money, tech.usual.money*
*Data limitations: JS-rendered sites required documentation-based inference; team anonymity limits social media forensics; private audits may exist but are unverifiable*
