# Odyssey Finance — Adversarial Due Diligence Report

**Research Date:** 2026-03-06
**Analyst Stance:** Maximum adversity assumption — guilty until proven innocent
**Confidence Level:** Medium-High (limited by: SPA website blocking static fetch, Twitter/X programmatic block, audit PDFs not fetchable, no confirmed token contract)

---

## ⚠️ EXECUTIVE SUMMARY

Odyssey Finance is a DeFi yield aggregator / super-app built by the core team behind Vesper Finance and Metronome Synth, both of which are Bloq Inc. portfolio projects. The project is structurally legitimate — it is not a rug pull operation and the team is identifiable with a real track record. However, it carries **significant conflict-of-interest, centralization, and circular TVL risks** that are underreported relative to the marketing narrative.

**Verdict:** Proceed with caution. This is a real product from a real team, but the architecture is an intra-ecosystem loop: the CEO (formerly Bloq's strategy lead for Vesper and Metronome) now runs a protocol that routes capital back into Vesper and Metronome, both Bloq properties, while the admin keys for core contracts are controlled by the same EOA wallet used to deploy Hemi — yet another Bloq/Roszak project. The leverage strategies offered (up to 27.1x) create extreme liquidation risk for retail users who may not understand the mechanics.

**Confidence:** Medium-High in structural analysis; Low in precise TVL verification and audit quality (PDFs not accessible).

### Top 3 Risks
1. **Core proxy upgrade controlled by a single, untimelocked EOA labeled "Hemi: Deployer 1"** — any compromise of that private key allows arbitrary contract replacement with no delay.
2. **Recursive/circular TVL between Odyssey, Vesper, and Metronome** is reported as combined "Bloq DeFi TVL" ($125M), obscuring that Odyssey's standalone TVL is ~$12M and the growth in affiliated protocols is partly self-generated.
3. **Extreme leverage strategies (up to 27.1x) with no discernible risk guardrails or prominent disclosure** exposed to users still in a beta product with a 14-month-old codebase and unverifiable audit quality.

### Top 3 Positive Signals
1. **Named, verifiable team** with a decade-long, public DeFi track record at real protocols (Vesper TVL peaked at $750M+, Metronome was a legitimate ICO project since 2018).
2. **No exploit, no rekt.news listing** — despite Vesper having two oracle attacks in 2021 and Metronome's Curve exposure in 2023, Odyssey Finance itself has no documented security incident as of March 2026.
3. **Real protocol integrations** — Aave V2/V3, Compound V2/V3, Morpho, Euler V2, Ajna — battle-tested counterparties with industry-standard OpenZeppelin proxy patterns in the deployment stack.

---

## SECTION 1 — TEAM ASSESSMENT

### 1.1 Zane Huffman — CEO (appointed April 2025)

**Verified claims:**
- Real identity confirmed via LinkedIn, RootData, Messari, and Vesper Finance's own Medium publication
- Crypto native since 2013 (self-reported; consistent with long-standing engagement visible in public records)
- 4+ years as strategy lead at both **Vesper Finance** and **Metronome Synth**, both Bloq Inc. products
- Published governance proposals co-authored with Jordan Kruger for Frax Finance, confirming an active, identifiable track record
- Was "Vesper Chief of Strategy" on Flywheel Podcast

**Unverified claims:**
- Exact scope of "over a decade of DeFi experience" — Messari confirms "crypto native since 2013" but strategy-specific DeFi work is documented only from ~2020 onward
- Prior credentials before Bloq are sparse in public record

**Red Flag — Pseudonym Usage:**
Zane Huffman operates on X/Twitter as **"Jeff Green"**. This is unusual for a publicly named CEO. The rationale for maintaining a pseudonym in a leadership role has not been disclosed. While not itself evidence of wrongdoing, it creates an accountability gap between his formal identity and his social media presence.

**Conflict of Interest — Critical:**
Huffman spent four years running strategy for Vesper Finance and Metronome Synth. Both protocols are deeply embedded in Odyssey's product architecture:
- Odyssey's **Loopr** routes capital through Metronome's flash loan and synthetic leverage mechanism
- Odyssey's **Yieldr** lists Vesper as one of its primary vault providers
- The fee structure explicitly prices Vesper+Metronome combos at 2% (vs. 6% or 10% for non-integrated paths), creating a financial incentive to funnel user capital into affiliated protocols

This is a structural conflict of interest that has not been prominently disclosed in public materials.

---

### 1.2 Jordan Kruger

**Verified claims:**
- CEO and co-founder of **Vesper Finance** (confirmed via LinkedIn and Bloq press materials)
- Head of DeFi at **Bloq Inc.**
- Co-founder of **Metronome Synth**
- Currently employed at **Odyssey** per LinkedIn

**Role at Odyssey:** LinkedIn shows employment at Odyssey but his specific title is obscured in publicly accessible content. He may be a board member or silent partner rather than an active product role.

---

### 1.3 Jeff Garzik — Co-founder, Bloq (Odyssey's parent entity)

**Verified claims:**
- Co-founder and CEO of Bloq Inc.
- Co-founder of **Hemi blockchain** alongside Matthew Roszak
- Former Bitcoin Core contributor (contributions ended around 2015)

**Controversy — On Record:**
- Led the **SegWit2x hard fork proposal (2017)**, described by the Bitcoin community as "the most universally hated hard-fork proposal in Bitcoin's history"
- His implementation code (btc1) contained bugs that caused nodes to "grind to a halt" before the fork even activated
- Was **expelled from the Bitcoin Core GitHub repository** during this period
- After the fork failed, community members nicknamed it "Jeffcoin"

While these events are 8+ years old, they demonstrate a pattern of **overreach, poor community coordination, and buggy code delivery** in a high-stakes context.

**Indirect Impact on Odyssey:**
- Garzik co-founded Hemi, which is named as a target deployment chain for Odyssey Finance
- The wallet labeled "Hemi: Deployer 1" on Etherscan controls the proxy upgrade path for Odyssey Finance's core registry contract
- This creates a governance entanglement between Odyssey Finance and Hemi that is not disclosed to Odyssey users

---

### 1.4 Matthew Roszak — Chairman, Bloq

**Verified claims:**
- American billionaire venture capitalist and cryptocurrency investor
- Co-founder and Chairman, Bloq Inc. (since 2016)
- Co-founder, Vesper Finance
- Co-founder, Hemi blockchain
- Founding Partner, Tally Capital

**Assessment:** Roszak is a legitimate, well-documented figure with a long track record in institutional crypto. His involvement adds credibility, but his role is investor/chairman — not hands-on builder. He is not a technical risk factor but is central to the conflict-of-interest picture.

---

### 1.5 Marcelo Morgado — Lead Developer

**Verified claims:**
- GitHub: [github.com/marcelomorgado](https://github.com/marcelomorgado)
- 48 total repositories; Blockchain engineer based in Portugal
- Affiliated with **Bloq, autonomoussoftware (Metronome), Vesper, Hemi Labs, and Odyssey Finance** on GitHub simultaneously
- Pinned repos include `vesper-contracts` (Vesper) and `metronome-synth-public` (Metronome)
- Published Solidity educational content on Medium consistent with genuine expertise

**Assessment:** Morgado appears to be a legitimate, experienced Solidity developer. His cross-affiliation across all Bloq ecosystem projects is expected given the incubator structure, but reinforces the single-team concentration.

---

### 1.6 What Could NOT Be Verified
- Identities of Gnosis Safe signers for the fee policy admin contract
- Whether any team members have prior negative legal or regulatory history
- The prior CEO or founder of Odyssey Finance before Zane Huffman — public records do not name a previous CEO distinct from the Bloq/Vesper/Metronome leadership

---

## SECTION 2 — THIRD-PARTY CONSENSUS

### 2.1 Independent Analyst Coverage

| Source | Coverage Found? | Notes |
|--------|----------------|-------|
| The Defiant | ❌ No | No indexed articles on Odyssey Finance |
| Blockworks | ❌ No | No indexed articles |
| DL News | ❌ No | No indexed articles |
| Rekt News | ✅ Absence | No incident listed — positive signal |
| Messari | ✅ Yes | One research report published Q2 2025 — architectural overview, not an adversarial assessment |
| IQ.wiki / CoinGecko | Partial | Basic profile pages only |

**Assessment:** The absence of independent critical coverage from major DeFi publications (The Defiant, Blockworks) is notable. The only substantive third-party coverage is a single Messari report that is descriptive, not evaluative. No independent security researchers have published analysis.

---

### 2.2 Audit and Security Assessment

**Audits in GitHub Repository** (`/audits` directory):
- `Audit_Report_BLOQ-OEI_FINAL_20.pdf`
- `Audit_Report_BLOQ-Odyssey_REVIEW_11 (3).pdf`
- `Audit_Report_BLOQ-SWA_REVIEW_11 (2).pdf`

⚠️ **Critical Audit Opacity Finding:** The naming convention (`BLOQ-` prefix, internal codes `OEI` and `SWA`) suggests these are internally commissioned audits using project-internal identifiers. The auditing firms themselves **could not be independently identified** from search results. The PDFs are not fetchable via web tools. No audit from any named firm (Halborn, Trail of Bits, OpenZeppelin, Cyfrin, Sherlock, Code4rena) was found in any public audit database.

- **Solodit:** No Odyssey Finance entries
- **Code4rena:** No Odyssey Finance contest
- **Sherlock:** No Odyssey Finance listing
- **Halborn public audit list:** No Odyssey Finance entry
- **SourceHat 2022 audit:** Belongs to a different "Odyssey" (a BNB dividend token), not this project

**Previous Security Incidents — Affiliated Protocols:**

| Date | Protocol | Incident | Loss |
|------|----------|----------|------|
| Nov 2021 | Vesper Finance | Oracle manipulation (Rari Fuse Pool #23) | ~$3M |
| Dec 2021 | Vesper Finance | Second oracle manipulation (same pool) | ~$1M |
| Jul 2023 | Metronome Synth | Curve/Vyper compiler reentrancy exploit | ~$3.4M |

All three incidents involved the same core team now building Odyssey. None resulted in rug behavior — the teams responded appropriately and recovered significant funds. However, being hit by two oracle attacks within two months (late 2021) on the same pool raises questions about the team's security responsiveness at the time.

---

### 2.3 Community Sentiment

- **Reddit:** Zero results found on r/DeFi, r/CryptoCurrency, or r/ethfinance
- **Twitter/X:** @0xOdysseyApp exists but content could not be retrieved programmatically; no critical community posts surfaced in secondary search results
- **Competing protocol discord/forums:** No independent commentary surfaced
- **Airdrops.io:** Lists the airdrop as "unconfirmed" with a disclaimer about scam risk

**Assessment:** The near-total absence of community discussion is a neutral-to-negative signal. For a product in public beta since 2024, this suggests either a very small user base or a predominantly closed/incentivized community that has not generated organic discourse.

---

## SECTION 3 — ON-CHAIN FINDINGS

### 3.1 Smart Contract Analysis

**Deployment:** Contracts deployed to Ethereum mainnet around late January 2025 (Block ~21,732,500).

**Chains:** Ethereum mainnet, Base, Optimism, Hemi, Plasma

**Architecture:** OpenZeppelin TransparentUpgradeableProxy pattern for core contracts. Each position is isolated in a smart contract account (ERC-4337). Uses ERC7579 and ERC7710 executor standards. Integrates flash loans (DyDx, Morpho, AaveV2/V3).

**Contract Verification:** The PositionRegistry_Proxy (`0xeE156D8ea7b96a5524CcC3CF9283ab85E80E9534`) is verified on Etherscan.

---

### 3.2 CRITICAL — Admin Key Centralization

**PositionRegistry Proxy Admin:**
- ProxyAdmin Contract: `0x3F6da0A118B3A0ddfdbaB4690cC96b2cF73B488D`
- **Owner: `0xF5F5195cF6998c57C651f9f0bBFA7cFC72a6FaC1`**
- **Type: EOA (Externally Owned Account)** — NOT a multisig
- **Etherscan Label: "Hemi: Deployer 1"**

This single private key can upgrade the PositionRegistry contract — the central contract that manages all user positions — with **no timelock and no multisig protection**. If this key is compromised or acts maliciously, all user positions could be drained through a malicious upgrade with zero on-chain warning.

This wallet is labeled as a Hemi blockchain deployer, confirming the governance entanglement between Odyssey Finance and the Hemi project, another Bloq/Roszak entity.

**PerformanceFeePolicy Proxy Admin:**
- Owner: `0xd44A3e93A256c445F17a12f35A0ffEf975ec6817`
- **Type: Gnosis Safe (SafeProxy)** — an improvement
- **Creator: "Vesper Finance: Deployer"** — also receives transactions from "Hemi: Deployer 1" and "Metronome: Deployer 2"
- Signers: Unknown — not publicly disclosed
- Holdings: Contains DeFi tokens (sUSDe, ynETHx, rswETH), suggesting it functions as both treasury and admin

**No timelock contract found in the deployment directory.** Without a timelock, users cannot exit positions before a malicious upgrade takes effect.

---

### 3.3 Token and Treasury Analysis

- **No native token exists.** The platform runs a "Calories" (Fatstronauts) points system with an unconfirmed future airdrop.
- No token distribution, vesting schedule, or insider allocation to analyze — but this also means the airdrop terms are entirely at the team's discretion.
- Odyssey Finance reported **~$12M in deposits** as of an early 2025 update. The $125M "Bloq DeFi TVL" figure aggregates Vesper, Metronome, and Odyssey together.
- The Gnosis Safe admin holds DeFi tokens including Odyssey-related assets, suggesting it is a combined treasury/governance wallet.

---

### 3.4 Circular TVL Pattern — Structural Finding

Odyssey Finance's Loopr product creates leveraged loops using Metronome's synthetic asset infrastructure (msETH). Each leveraged position:

1. Deposits collateral into Vesper vaults → increases Vesper TVL
2. Borrows synthetics (msETH) from Metronome → increases Metronome's minted supply and reported TVL
3. Re-deposits the borrowed synthetics → repeats

**On-chain evidence of this loop:**
- Metronome's own August 2025 performance report states: "Most of the TVL increase occurred on Ethereum and Base, consistent with Odyssey's footprint. More loops meant more msETH minted and/or borrowed."
- Vesper's recent TVL recovery to ~$55M (highest since 2022) is attributed to "new integrations, including with @0xOdysseyApp"
- Odyssey's blog states it "quickly became one of [Origin's] largest TVL sources — its Morpho markets account for roughly 35% of Origin's staked TVL and nearly 20% of YieldNest's TVL"

**Assessment:** This is **recursive leverage TVL**, not organic depositor growth. The practice is not inherently fraudulent — leveraged looping is a standard DeFi strategy — but presenting it as combined ecosystem growth ($125M) without clearly attributing the intra-protocol circularity is misleading. Bloq is reporting its own capital flows between its own protocols as aggregate TVL expansion.

---

### 3.5 Leverage Risk — Unhedged Exposure

Live strategies observed in Odyssey's Loopr product (as of Q4 2025):

| Strategy | Max APY | Max Leverage | Chain |
|----------|---------|--------------|-------|
| Synth Vesper vaFRAX | 45.37% | 4.8x | Ethereum |
| Morpho Ethena sUSDe | 38.64% | 11.2x | Ethereum |
| Euler V2 EtherFi weETH | 38.3% | 13.6x | Plasma |
| **Morpho Lido wstETH** | **35.21%** | **27.1x** | Ethereum |
| Aave v3 EtherFi weETH | 21.73% | 13.6x | Ethereum |
| Morpho Origin wsuperOETHb | 19.94% | 17.3x | Base |

27.1x leverage on wstETH means a **3.7% adverse price move wipes out 100% of collateral**. At 13.6x leverage, a 7.4% move triggers liquidation. These are beta-stage products. There is no visible disclosure that matches the severity of these risk parameters.

---

## SECTION 4 — RED FLAGS REGISTER

| # | Flag | Severity | Evidence | Why It Matters |
|---|------|----------|----------|----------------|
| 1 | Core PositionRegistry proxy admin is an EOA ("Hemi: Deployer 1"), no timelock | **CRITICAL** | Etherscan: `0xF5F5195...A6FaC1` is EOA, labeled Hemi deployer | Single key can upgrade all user position contracts with no delay |
| 2 | Core admin wallet is entangled with Hemi blockchain, a separate Bloq project | **CRITICAL** | Etherscan label + Hemi co-founders = Roszak & Garzik | Users of Odyssey Finance are exposed to the governance of a separate protocol's deployer |
| 3 | Circular TVL between Odyssey, Vesper, and Metronome reported as unified ecosystem metric | **HIGH** | Metronome August 2025 report + Vesper TVL attribution + Bloq $125M aggregate | Inflated perception of ecosystem health; Odyssey standalone TVL is ~$12M, not $125M |
| 4 | Audit firms not independently identifiable; no crowdsourced audit on major platforms | **HIGH** | PDFs unfetchable; BLOQ- prefix naming; Solodit/C4/Sherlock: no results | Cannot verify audit quality, coverage, or whether critical findings exist |
| 5 | CEO (Zane Huffman) uses pseudonym "Jeff Green" on Twitter | **HIGH** | RootData, Odyssey blog | Accountability gap between formal identity and social media; unusual for a named CEO |
| 6 | Fee structure explicitly favors affiliated protocols (2% Vesper+Metronome vs 6-10% competitors) | **HIGH** | Odyssey documentation | Built-in financial incentive to route user capital into Bloq ecosystem, not best-available yield |
| 7 | Leverage strategies up to 27.1x with minimal disclosed risk | **HIGH** | Loopr product listings | Retail users can be liquidated on small price moves; beta product with 14-month codebase |
| 8 | Parent company Bloq's co-founder (Garzik) has history of failed, buggy high-stakes code delivery | **MEDIUM** | SegWit2x btc1 bugs, Bitcoin Core expulsion | Organizational pattern of overreach and poor code quality at critical junctures |
| 9 | Vesper Finance (same team) suffered two oracle attacks in two months (2021) | **MEDIUM** | Web3isgoinggreat.com, Quadriga Initiative | Pattern of security responsiveness issues from this team in production |
| 10 | Metronome lost $3.4M in 2023 Curve/Vyper exploit | **MEDIUM** | MetronomeDAO post-mortem, CoinTelegraph | Compiler-level vulnerability; funds partially recovered, but same team exposure |
| 11 | No public funding round disclosed | **MEDIUM** | Tracxn search returns no Odyssey Finance entry; Crunchbase silent | Unknown runway; entirely Bloq-funded = no independent governance check from external investors |
| 12 | GitHub: 1 commit on main branch, 0 stars, 0 forks | **MEDIUM** | github.com/odyssey-finance/odyssey-contracts-public | History squashing hides development progression; no external developer interest |
| 13 | No independent media coverage from major DeFi outlets | **MEDIUM** | The Defiant, Blockworks, DL News: zero indexed results | Projects with real traction typically attract some third-party scrutiny by beta stage |
| 14 | Airdrop unconfirmed; "Calories" points system terms entirely at team's discretion | **MEDIUM** | Airdrops.io disclaimer; no token announcement | Points farming attraction without binding commitment to users; could be changed or cancelled |
| 15 | Gnosis Safe admin signers not publicly identified | **MEDIUM** | Etherscan: Safe at `0xd44A3e...` has no public tag; funded by Bloq deployers | No way to assess signer independence or threshold; effectively anonymous multisig |
| 16 | Hemi chain integration (Bloq/Roszak project) adds further ecosystem concentration | **LOW** | Deployment folder contains /hemi directory; Messari confirms Hemi as planned chain | Each new Bloq-affiliated chain integration deepens vertical control |
| 17 | msETH has only 203 holders on Ethereum mainnet | **LOW** | Etherscan token tracker | Thin underlying market creates peg risk in leveraged Metronome strategies |

---

## SECTION 5 — UNRESOLVED QUESTIONS

1. **Who audited the contracts?** The three PDF audit reports in the repository use internal BLOQ naming conventions. The actual auditing firms remain unidentified through public search. This is the single most important unresolved question.

2. **What is the multisig threshold for the Gnosis Safe admin?** If it is 1-of-N, it provides no meaningful security improvement over an EOA. If it is 3-of-5 with independent signers, it is a meaningful control. The signer count and identities are not publicly disclosed.

3. **Is there a planned transition to a timelock or DAO governance?** No roadmap for decentralizing the admin key has been found in public communications.

4. **What are the actual unlock terms for the Fatstronauts points?** The program has no binding on-chain commitment to a specific conversion ratio, token contract, or airdrop date.

5. **Who was the CEO or lead product person before Zane Huffman joined in April 2025?** The project launched its beta in 2024 but no earlier leadership is named in public materials. The "Fatstronauts" blog predates Huffman's appointment.

6. **What is the actual standalone TVL as of March 2026?** DeFiLlama's page exists but the data was not directly accessible during this research. The $12M figure is from a mid-2025 reference.

7. **Does the "Hemi: Deployer 1" wallet have any contractual or operational obligation to Odyssey Finance, or could it be reassigned to Hemi's use without notice?**

8. **Have any of the 71 mainnet deployment contracts been upgraded since initial deployment?** The PositionRegistry shows 11 total transactions, but whether any were upgrades is unclear.

---

## SECTION 6 — OVERALL RISK ASSESSMENT

### Probability of Deliberate Exit Scam: **LOW**
The team is publicly identified, has a decade-long DeFi track record, and has not shown exit behavior. The protocols they built (Vesper, Metronome) are still operating.

### Probability of Security Exploit: **MEDIUM**
- EOA-controlled upgradeable proxy with no timelock is a material exploit vector
- Leveraged positions create cascade liquidation risk
- Audit opacity means no independent confirmation of contract security
- Predecessor protocols had documented exploits

### Probability of Structural Failure / Unsustainability: **MEDIUM-HIGH**
- Circular TVL between affiliated protocols inflates metrics
- High leverage yields (35-45% APY at 11-27x leverage) are not sustainable in flat/bear markets
- Concentrated Bloq ecosystem dependency means a failure in Vesper, Metronome, or Hemi could cascade into Odyssey
- No confirmed token means user loyalty rests entirely on speculative airdrop expectations

### Probability of Conflict-of-Interest Self-Dealing: **HIGH (Already Occurring)**
- Fee structure, TVL reporting, and product architecture are all structured to benefit Bloq ecosystem protocols at the expense of neutral best-yield routing for users

---

## APPENDIX — KEY CONTRACT ADDRESSES

| Contract | Address | Chain | Control Type |
|----------|---------|-------|-------------|
| PositionRegistry_Proxy | `0xeE156D8ea7b96a5524CcC3CF9283ab85E80E9534` | Ethereum | Upgradeable Proxy |
| PositionRegistry_ProxyAdmin | `0x3F6da0A118B3A0ddfdbaB4690cC96b2cF73B488D` | Ethereum | ProxyAdmin |
| PositionRegistry_ProxyAdmin Owner | `0xF5F5195cF6998c57C651f9f0bBFA7cFC72a6FaC1` | — | **EOA ("Hemi: Deployer 1")** |
| PerformanceFeePolicy ProxyAdmin Owner | `0xd44A3e93A256c445F17a12f35A0ffEf975ec6817` | Ethereum | Gnosis Safe (anonymous signers) |

---

## APPENDIX — KEY SOURCES

- Odyssey Finance blog: [odyssey.finance/blogs/a-new-chapter-for-odyssey](https://odyssey.finance/blogs/a-new-chapter-for-odyssey)
- GitHub org: [github.com/odyssey-finance](https://github.com/odyssey-finance)
- Messari report: [messari.io/report/odyssey-finance-a-multichain-defi-hub-built-on-erc-4337](https://messari.io/report/odyssey-finance-a-multichain-defi-hub-built-on-erc-4337)
- RootData — Zane Huffman: [rootdata.com/member/Zane%20Huffman](https://www.rootdata.com/member/Zane%20Huffman?k=MzA0NDE%3D)
- Vesper oracle attack: [web3isgoinggreat.com/?id=2021-11-02-0](https://www.web3isgoinggreat.com/?id=2021-11-02-0)
- Metronome Vyper exploit post-mortem: [metronomedao.medium.com/vyper-curve-exploit-post-mortem-6a42d6d9fa07](https://metronomedao.medium.com/vyper-curve-exploit-post-mortem-6a42d6d9fa07)
- Metronome August 2025 performance: [paragraph.com/@metronomedao/metronome-performance-analysis-august-2025](https://paragraph.com/@metronomedao/metronome-performance-analysis-august-2025)
- Garzik SegWit2x failure: [bitcoinmagazine.com/technical/now-segwit2x-hard-fork-has-really-failed-activate](https://bitcoinmagazine.com/technical/now-segwit2x-hard-fork-has-really-failed-activate)
- Etherscan — PositionRegistry Proxy: [etherscan.io/address/0xeE156D8ea7b96a5524CcC3CF9283ab85E80E9534](https://etherscan.io/address/0xeE156D8ea7b96a5524CcC3CF9283ab85E80E9534)
- Etherscan — Hemi Deployer 1: [etherscan.io/address/0xF5F5195cF6998c57C651f9f0bBFA7cFC72a6FaC1](https://etherscan.io/address/0xF5F5195cF6998c57C651f9f0bBFA7cFC72a6FaC1)
- Airdrops.io — Odyssey Finance: [airdrops.io/odyssey-finance/](https://airdrops.io/odyssey-finance/)
- DeFiLlama — Odyssey Finance: [defillama.com/protocol/odyssey-finance](https://defillama.com/protocol/odyssey-finance)
- Marcelo Morgado GitHub: [github.com/marcelomorgado](https://github.com/marcelomorgado)
