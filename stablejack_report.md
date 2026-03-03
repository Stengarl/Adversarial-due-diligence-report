# StableJack (JACK) — Adversarial DeFi Due Diligence Report

**Investigator:** Claude Code (Adversarial Research Mode)
**Date:** 2026-03-03
**Report Type:** Full-Spectrum Due Diligence — Guilty Until Proven Innocent
**Subject:** Stable Jack / StableJack (`stablejack.xyz`)
**Token:** $JACK
**Primary Chain:** Avalanche (v1), Sonic (v2)
**Confidence Level:** Medium-High

---

## EXECUTIVE SUMMARY

Stable Jack is **not a rug pull** in the conventional sense — the team has remained engaged, the protocol continues to operate, and TVL (~$5.4M total) is non-trivial. However, **this is a failed token launch with severe investor harm and unresolved structural risks that persist today.**

Every IDO participant (who paid $0.20/JACK) suffered losses from the moment of listing — the token's all-time high ($0.0998, April 9, 2025) was **50% below the IDO price**. Today's price (~$0.0127) represents a **93.65% loss from IDO price**, with 24-hour trading volume of approximately $155.80 — a near-dead market. The protocol pivoted away from its original v1 thesis (yield-bearing stablecoin on Avalanche) to a Pendle-like yield/volatility marketplace, now expanding to Sonic chain. IDO investors absorbed all the tuition.

The most structurally dangerous risk is **admin centralization**: the Dedaub audit explicitly acknowledges that the protocol admin can change "virtually all important parameters including oracles, hooks, fees" and can receive funds directly, with no timelock disclosed. This is the architecture — not a vulnerability queued for fixing.

### Top 3 Risks

1. Admin has unconstrained authority over all protocol parameters (oracles, fees, fund access) with no evident timelock — critical single point of failure for $5.4M in user TVL
2. Token is 93.65% below IDO price with near-zero liquidity ($155/day volume); team token cliff expired ~October 2025, initiating ongoing unlock pressure
3. 61.5% of total supply allocated to Team+Advisors (18%) and "Contributor Program" (43.5%) — insider supply massively outweighs public; Contributor Program beneficiaries are entirely opaque

### Top 3 Positive Signals

1. Lead founder partially doxxed (real name confirmed: Ulvi Kagan Dagdeviren), reducing anonymous exit risk
2. Real audit by legitimate firm (Dedaub, Dec 2024) with findings publicly disclosed and mostly resolved
3. Protocol has functional TVL ($5.14M on Avalanche, $273K on Sonic) indicating real usage — not zero

---

## 1. TEAM ASSESSMENT

### 1.1 Founders

**VERIFIED via multiple independent sources** (Avalaunch AMA recap, ICO Drops, HyperNest, Dedaub testimonial page):

| Person | Handle | Role | Real Name Status |
|--------|--------|------|-----------------|
| Caesar | @CaesarJulius0 | Co-Founder & CEO | Ulvi Kagan Dagdeviren — VERIFIED |
| Cihan / Sextus | Handle mapping UNCONFIRMED | Co-Founder | Dagdeviren (twin brother) — UNVERIFIED |
| Solomon | Handle mapping UNCONFIRMED | Co-Founder | Surname unknown — UNVERIFIED |

**Official handle listing:** @CaesarJulius0, @Solomon_nsi, @Dagdeviren1998 — but no public source maps which handle belongs to Cihan vs. Solomon. Since "Dagdeviren" is the family surname shared by Caesar and Cihan (twins), @Dagdeviren1998 likely belongs to Cihan, not Solomon. **The project's own published handle mapping may be inconsistent.**

**CLAIMED but entirely UNVERIFIED (official sources only, no independent confirmation):**

- Caesar: "in crypto since 2017," prior work at "Avalanche native protocols" — employer unspecified
- Cihan/Sextus: "worked for Avalanche native VC and research company," "advisor to Turkish bank on DeFi/tokenization" — no company named
- Solomon: "audit company experience" — no firm named
- All three: "in Avalanche ecosystem since mainnet launch"

### 1.2 GitHub Analysis

**Organization:** `github.com/stable-jack`

| Repository | Last Updated | Stars | Notes |
|------------|-------------|-------|-------|
| protocol-contracts-v1 | Jun 20, 2024 | 1 | V1 Avalanche contracts |
| EasyLz | Mar 25, 2025 | 0 | LayerZero OFT logic |
| events-filter | Sep 9, 2024 | 1 | Infrastructure |
| yield-server | Jul 1, 2024 | 0 | Forked from DefiLlama |
| DefiLlama-Adapters | Jun 24, 2024 | 0 | Forked from DefiLlama |
| postgre-apollo-server | Oct 26, 2024 | 0 | **Forked from ulas96** |
| events-filter-archive | Sep 5, 2024 | 0 | **Forked from ulas96** |
| websocket-server | Jul 8, 2024 | 0 | Point-system backend |

**GitHub Red Flags:**

The organization forks code from `ulas96` (GitHub: github.com/ulas96, real name: Yusuf Ulas Yildiz, website: ur.finance). This developer's pinned repos include `ur-stablecoin` and `ur-leverage` — DeFi stablecoin and leverage contracts — as well as `ur-leverage`. **Yusuf Ulas Yildiz is not named in any team materials** but contributed core infrastructure. This is an undisclosed team member or contractor, which is a transparency concern.

Additional flags:
- `protocol-contracts-v1` last updated June 2024 — 10 months before TGE. No contract activity in final months pre-launch.
- Zero external stars on original repos — minimal community scrutiny.
- Dedaub found a CRITICAL vulnerability at audit time, indicating code was not internally security-hardened.
- No individual GitHub profiles confirmed for any named founder.

### 1.3 Social Media

- @CaesarJulius0 confirmed on X with Avalanche affiliation ("caesar.avax" display name)
- No deep tweet history analysis possible through web search
- No evidence of prior failed/rugged project associations
- No connections to known bad actors identified

**COULD NOT VERIFY:** Follower quality, engagement ratios, deleted tweet archives, prior project promotion history.

### 1.4 Team Red Flag Summary

| Flag | Severity |
|------|----------|
| Undisclosed developer (ulas96) contributed core infrastructure | Medium |
| All employment claims self-reported, none independently confirmed | Medium |
| Solomon audit firm: unnamed | Low |
| Handle-to-founder mapping inconsistency | Low |
| Cihan and Solomon have minimal public footprint | Low |

---

## 2. THIRD-PARTY CONSENSUS

### 2.1 Independent Analyst Coverage

**Finding: NONE FOUND**

Exhaustive search across Rekt News, The Defiant, DL News, Messari, Bankless, DeFiLlama forums, Ethresear.ch, Reddit, and Crypto Twitter yielded **zero independent analyst coverage or critical research** on StableJack. The only available narrative is the project's own. No external expert has publicly validated or challenged the technical claims.

### 2.2 Audit Assessment

**Auditor:** Dedaub
**Date:** December 24, 2024
**Report:** https://dedaub.com/audits/stable-jack/stable-jack-dec-24-2024/
**Dedaub Reputation:** Legitimate, technically rigorous firm — not a rubber-stamp shop.

#### Findings Breakdown

| Severity | Count | Status |
|----------|-------|--------|
| Critical | 1 | Resolved |
| High | 1 | Resolved |
| Medium | 10 | 9 Resolved, 1 Partially Resolved |
| Low | 7 | 6 Resolved, 1 Open |
| Centralization | 1 | Acknowledged — NOT remediated |

**Critical C1 (Resolved):** Protocol queried a DEX for price estimates before forced swaps — enabling a pool manipulation attack to extract unfair prices. Fixed via Chainlink oracle integration. **The existence of this flaw pre-audit indicates the code was not internally security-hardened before third-party review.**

**High H1 (Resolved):** Fundamental accounting error in fee harvesting — function returned dollar amounts where base token amounts were required.

**Medium M5 (Partially Resolved):** Wrong token fetched for price; spot price used instead of TWAP. Token corrected; TWAP naming issue remains. Price oracle reliability partially compromised.

**Centralization N1 (Acknowledged — NOT Remediated):**

> "Admin can change virtually all important parameters including oracles, hooks, fees and receive funds directly. Requirement: Admin must be fully trusted with strong operational security."

This is the architecture. Implications:
- Compromised admin key = ability to manipulate oracles and redirect protocol funds
- No timelock documented in audit or in any public StableJack document
- No multisig configuration publicly disclosed
- Hexagate pause capability grants admin power to freeze all user funds

**Additional audit concerns:**
- "Multiple audits" referenced in official docs — only ONE audit found in research (Dedaub, Dec 2024). If others exist, they are not publicly indexed.
- No Code4rena contest, no Sherlock contest, no Immunefi bug bounty, no second auditor found.
- V2 contracts on Sonic chain are newer than December 2024 — unclear if they were in scope.

### 2.3 Community Sentiment

- **Reddit:** No subreddit, no significant threads found across r/CryptoCurrency, r/DeFi, r/Avalanche
- **Crypto Twitter:** Only promotional content surfaced
- **Post-TGE community reaction:** Not recoverable through web search
- **Competing protocols:** No commentary from Pendle, Yield Yak, or BENQI communities
- **No neutral community space** for critical discussion — all engagement gated through Discord/Telegram

---

## 3. ON-CHAIN FINDINGS

### 3.1 Contracts

| Item | Value |
|------|-------|
| JACK Token (Sonic) | `0x53a828455268139aee1b7ffd375ce03dafadacb6` |
| JACK Token (BSC) | `0xb4a9634f6e386b661c1fe9ec5aafe0e63fc54d51` — NOT in official docs |
| V1 Protocol Contracts | Avalanche — source claimed verified |
| Contract Framework | thirdweb ERC-20, ERC20BurnableUpgradeable, ERC20VotesUpgradeable |
| Security Monitoring | Hexagate (threat monitoring + pause capability) |

**CRITICAL FLAG:** A JACK token on BSC (0xb4a9634f6e386b661c1fe9ec5aafe0e63fc54d51) appears on BscScan but is mentioned nowhere in official StableJack documentation. This is either: (a) an undisclosed official bridge deployment, (b) a scam fork using the same name, or (c) a test/deprecated deployment. This requires direct verification — and the fact that it is undisclosed is itself a transparency failure.

**Admin Architecture (from audit):** Admin can modify all oracles, fees, hooks, and receive funds. Standard DeFi best practices call for:
- Timelocked upgrades (24-72+ hours minimum)
- Multi-signature control with external signers
- Role separation (operations / upgrade / emergency pause)

None of these mitigations are documented in public StableJack materials.

### 3.2 Token Distribution

**Total Supply:** 100,000,000 JACK
**Initial Circulating Supply:** 23,945,600 JACK (23.9%)

| Category | % | Tokens | Vesting |
|----------|---|--------|---------|
| **Contributor Program** | **43.5%** | **43.5M** | **900 days from TGE** |
| Team + Advisors | 18.0% | 18M | 180-day cliff, 730-day linear |
| Public Round | 10.0% | 10M | 100% TGE unlock |
| Discount Tickets | 10.0% | 10M | 100% TGE unlock |
| Treasury | 10.6% | 10.6M | 15% TGE, 365-day vest |
| Angel Round | 8.6% | 8.6M | 10% TGE, 365-day vest |
| Seed Round | 4.3% | 4.3M | 10% TGE, 365-day vest |
| Liquidity/MM | 2.0% | 2M | 60% TGE, 180-day vest |

**CONTRIBUTOR PROGRAM — HIGHEST PRIORITY FLAG:**
43.5% of total supply to unnamed "contributors" — larger than all investor rounds combined, larger than team allocation, larger than any other category. Beneficiaries are not named in any public document. At 900-day vesting from April 2025 TGE, this allocation unlocks through September 2027. No criteria, no wallet list, no accountability. This could be legitimate protocol incentives or a mechanism to funnel tokens to insiders without disclosure.

**Combined insider concentration (Team + Contributors): 61.5%.** Public buyers control a minority stake in a project where insiders hold supermajority.

**Team cliff:** 180 days from April 2, 2025 = approximately October 2, 2025. Team tokens began unlocking ~5 months ago as of this report. Team can sell into a market where retail is down 94%.

### 3.3 Token Price and Market Data

| Metric | Value |
|--------|-------|
| Angel Round Price | $0.125 |
| Seed Round Price | $0.150 |
| IDO Price (all public) | $0.200 |
| TGE Date | April 2, 2025 |
| All-Time High | $0.0998 (April 9, 2025) |
| ATH vs. IDO Price | -50.1% |
| ATH vs. Angel Price | -20.2% |
| Current Price (Mar 3, 2026) | ~$0.0127 |
| Loss from IDO Price | -93.65% |
| Loss from ATH | -87.3% |
| 24h Trading Volume | ~$155.80 |

**The JACK token never reached its IDO price at any point in its trading history.** The ATH of $0.0998 was still 50% below the cheapest public entry price. This means no IDO investor, no seed investor, and no angel investor was ever profitable. The implied $20M FDV at IDO had zero market support.

At $155/day trading volume, the secondary market is functionally dead. Token holders have no viable exit path.

### 3.4 TVL Assessment

| Chain | TVL |
|-------|-----|
| Avalanche (v1) | ~$5.14M |
| Sonic (v2) | ~$273K |
| Total | ~$5.41M |
| Average Pool APY | 15.44% |

TVL of $5.4M indicates real user deposits earning yield. This is not zero. However, the extreme disconnect between $5.4M TVL and $155/day token volume suggests: the yield products work, but the JACK token has zero investment demand. Could not directly verify TVL composition (recursive vs. genuine) due to block explorer access limitations.

---

## 4. RED FLAGS REGISTER

| # | Flag | Severity | Evidence Source |
|---|------|----------|----------------|
| 1 | Admin has full authority over all parameters, oracles, fees, and funds — no timelock documented | CRITICAL | Dedaub audit N1 |
| 2 | Token never reached IDO price; -93.65% from $0.20; all investors permanently underwater | CRITICAL | CryptoRank, CoinGecko, DEX Screener |
| 3 | 43.5% "Contributor Program" with unnamed beneficiaries — largest single allocation | HIGH | Avalaunch IDO announcement |
| 4 | 24h trading volume ~$155.80 — market functionally dead | HIGH | DEX Screener data |
| 5 | Team cliff expired ~Oct 2025; team tokens unlocking into dead market now | HIGH | Tokenomics + TGE date |
| 6 | Critical vulnerability (DEX price manipulation) existed pre-audit | HIGH | Dedaub C1 |
| 7 | No timelock, no disclosed multisig architecture for admin key | HIGH | Audit + official docs |
| 8 | Single auditor only; no bug bounty; no competitive audit contest | MEDIUM | Research across Code4rena, Sherlock, Immunefi |
| 9 | V2 Sonic contracts may lack audit coverage | MEDIUM | Audit date vs. V2 expansion timeline |
| 10 | JACK token on BSC not mentioned in any official document | MEDIUM | BscScan |
| 11 | Undisclosed developer (ulas96 / Yusuf Ulas Yildiz) contributed core infrastructure | MEDIUM | GitHub fork analysis |
| 12 | V1 product failed; full pivot to v2 — original investment thesis wrong | MEDIUM | Official v2 docs |
| 13 | Zero independent analyst coverage or critical research | MEDIUM | Exhaustive web search |
| 14 | No Reddit community; all engagement in controlled channels | MEDIUM | Web search |
| 15 | Angel investors at $0.125 also underwater — ATH was $0.0998 | MEDIUM | Market data + round pricing |
| 16 | M5 audit finding "largely resolved" — TWAP naming issue remains | LOW | Dedaub M5 |
| 17 | L1 storage gap convention issue remains OPEN | LOW | Dedaub L1 |
| 18 | All founder credentials self-reported, none independently confirmed | LOW | AMA vs. independent search |
| 19 | Blizzard Fund is ecosystem-aligned (mandate-driven), not independent VC validation | LOW | IDO announcement |
| 20 | Hexagate pause = admin can freeze user funds | LOW | Official docs |

---

## 5. UNRESOLVED QUESTIONS

These are explicitly undetermined — not filled with assumptions:

1. **Who are the "Contributor Program" beneficiaries (43.5% of supply)?** No wallets, no criteria, no public disclosure. Highest priority unresolved question.

2. **What is the admin key architecture?** Multisig? How many signers? Timelock duration? Internal vs. external signers? Not found in any public document.

3. **Is the BSC JACK token (0xb4a9634f6e386b661c1fe9ec5aafe0e63fc54d51) official?** Appears on BscScan; not in official docs.

4. **Has a v2 Sonic chain audit been conducted?** December 2024 Dedaub audit predates or is concurrent with Sonic expansion.

5. **Were vested angel/seed/team tokens sold on-chain?** Cannot determine without direct block explorer analysis. These tokens started unlocking in 2025.

6. **What is Yusuf Ulas Yildiz (ulas96)'s official relationship to the project?**

7. **What are the "multiple audits" referenced in official docs** beyond the Dedaub December 2024 report?

8. **Is TVL composed of genuine independent capital** or recursive/leveraged positions?

---

## 6. COMPARATIVE ANALYSIS

### Pattern Match Against Known Failed Launches

| Pattern | StableJack | Risk Indicator |
|---------|-----------|----------------|
| Token never reaches ICO/IDO price post-listing | YES | Common in failed launches |
| 60%+ insider token concentration | YES | Common in rug-adjacent projects |
| Product-market fit failure + full pivot | YES | Not exclusively scam indicator |
| Zero independent analyst coverage | YES | Echo chamber risk |
| High admin centralization, no timelock | YES | Present in both legitimate and malicious protocols |
| Dead secondary market post-launch | YES | Characteristic of failed launches |
| Single auditor, no bug bounty | YES | Lower security maturity |
| Ecosystem-insider backers only | YES | Mixed signal — not independent validation |

### Not Matching Known Scam Patterns

- No Wonderland parallel: No documented criminal history; team has not vanished
- No Terra/Luna parallel: No algorithmic stablecoin death spiral; 1:1 collateral maintained
- No Celsius parallel: No disclosed insolvency or hidden rehypothecation
- No complete abandonment: Protocol is live, v2 is being built

### Yield Sustainability Assessment

- v1 yield: sAVAX staking rewards (BENQI) — on-chain verifiable, legitimate
- v2 yield: Underlying lending markets (Silo, Aave on Sonic) — legitimate in concept, dependent on those protocols
- 15.44% average pool APY: Plausible for yield-splitting on LSTs; not Ponzi-level
- 1:1 collateralization claim: Mathematically sound model if maintained

---

## 7. FINAL VERDICT

### NOT A RUG PULL — A FAILED TOKEN LAUNCH WITH PERSISTENT STRUCTURAL RISKS

**What this is:** A real protocol built by a real (partially identified) team with a legitimate yield-splitting concept, a genuine audit, and real TVL. The team stayed through a v1 failure and is actively developing v2. These are not exit scam behaviors.

**What else this is:** A catastrophic token launch where every single investor class — angels, seeds, and public — suffered losses from day one and has never recovered. A protocol with an explicit, unmitigated admin centralization risk acknowledged in the audit. A token with $155/day trading volume and no visible recovery thesis. A project where 61.5% of tokens belong to insiders with ongoing unlock schedules.

**On the token ($JACK):** No investment case exists. The market has delivered its verdict. At $155/day volume, holders cannot exit. Team and contributor tokens are unlocking into this non-existent market.

**On the protocol (deposits/yield):** Operationally functional, but carries unmitigated admin key risk. If the admin key is ever compromised — through hack, social engineering, or insider action — an attacker can manipulate oracles and redirect $5.4M in user funds with no timelock defense. Do not deposit funds you cannot afford to lose entirely.

**For further investigation, priority actions:**
1. Obtain admin key architecture details (multisig configuration, timelock status)
2. Identify Contributor Program beneficiary wallets on-chain
3. Verify BSC JACK token legitimacy with the team
4. Confirm scope of any v2 Sonic audit

---

## SOURCES

| Source | URL |
|--------|-----|
| Avalaunch AMA Recap | https://blog.avalaunch.app/stable-jack-ama-project-overview-recap/ |
| Avalaunch IDO Announcement | https://blog.avalaunch.app/stable-jack-x-avalaunch-ido-announcement/ |
| Dedaub Audit Page | https://dedaub.com/audits/stable-jack/stable-jack-dec-24-2024/ |
| StableJack Audits Docs | https://docs.stablejack.xyz/stablejack/audits |
| StableJack V2 Docs | https://docs.stablejack.xyz/stablejack/stable-jack-v2/why-were-building-stable-jack-v2 |
| JACK Token Docs | https://docs.stablejack.xyz/stablejack/usdjack-tokenomics/usdjack-token |
| DeFiLlama V1 | https://defillama.com/protocol/stable-jack |
| DeFiLlama V2 | https://defillama.com/protocol/stable-jack-v2 |
| ICO Drops | https://icodrops.com/stable-jack/ |
| CryptoRank ICO | https://cryptorank.io/ico/stable-jack |
| CoinGecko | https://www.coingecko.com/en/coins/jack-2 |
| SonicScan JACK | https://sonicscan.org/token/0x53a828455268139aee1b7ffd375ce03dafadacb6 |
| BSCScan JACK | https://bscscan.com/token/0xb4a9634f6e386b661c1fe9ec5aafe0e63fc54d51 |
| StableJack GitHub | https://github.com/stable-jack |
| ulas96 GitHub | https://github.com/ulas96 |
| DEX Screener | https://dexscreener.com/avalanche/0xa40b49418c758ea0faa5d27662320adc7da16127 |
| CoinCarp | https://www.coincarp.com/currencies/stablejack/project-info/ |
| CBInsights | https://www.cbinsights.com/company/stable-jack |

---

*Report completed 2026-03-03. All findings reflect data available at time of research. This is investigative research, not financial advice.*
