# Peer (peer.xyz / formerly ZKP2P) — Adversarial Due Diligence Report
**Research Date:** 2026-03-14
**Analyst:** DeFi Adversarial Research Agent
**Framework:** Maximum Adversity, Guilty Until Proven Otherwise

---

## ⚠️ CRITICAL FRAMING ALERT — READ BEFORE PROCEEDING

> **Peer (peer.xyz) is not a conventional DeFi protocol.** It has no native governance token, no yield product, no significant TVL (~$156K), and is 100% grant-funded by the Ethereum Foundation. It is a **zero-knowledge proof infrastructure project** building a trustless P2P fiat-to-crypto onramp/offramp. The standard adversarial framework for DeFi protocols (yield source legitimacy, token distribution, rug pull mechanics) is largely inapplicable in its traditional form.
>
> **This does not mean it is without risk.** The primary risks here are architectural and cryptographic — specifically a **centralized Attestation Service that, if compromised or controlled by the team, can authorize fraudulent withdrawals from user escrow**. This is a different class of risk from standard DeFi: it is a trust assumption baked into the architecture, self-documented by the team, with no current decentralization fix deployed.
>
> **Secondary alert:** The protocol's legitimate transaction flow — install a browser extension, send a non-refundable PayPal Friends & Family payment, communicate via Telegram, prove payment via extension — is **indistinguishable to a normal user from a phishing scam**. A real Trustpilot reviewer called the protocol a "SCAM" because the interaction pattern is identical to how scammers operate. This is not fraud on the team's part, but it is a serious user protection failure.

---

## 1. Executive Summary

**Verdict:** Peer (peer.xyz) is a **legitimate, grant-funded cryptographic research project** with verifiable team credentials and no evidence of fraudulent intent. It is built by engineers with a traceable decade-long track record in DeFi. It is **not a rug pull** — it has no token to dump and no significant user capital at risk. However, it carries **real, material architectural risks** that users of the escrow protocol must understand before depositing funds. Confidence in this verdict: **High**.

**Top 3 Risks:**
1. **The Attestation Service is a centralized trust bottleneck that can authorize theft from escrow.** The team's own documentation states: governance controls the public key of the witness associated with payment verifiers, and "if the new key is under their control, they could potentially forge proofs, sign them, and access the USDC deposited in the protocol." This is not a theoretical concern — it is a live, documented vulnerability in the current multisig-controlled governance architecture.
2. **No published smart contract audit was found.** Despite V1 being described as "live in production with audits" in external sources, no publicly accessible audit report from a recognized firm (Trail of Bits, OpenZeppelin, Spearbit, Ackee, ChainSecurity, etc.) was found for any version. This is a critical gap for any user placing funds into escrow contracts.
3. **The protocol's UX is structurally identical to P2P payment scams.** Non-refundable PayPal Friends & Family + browser extension download + Telegram contact instructions is the canonical workflow of crypto social engineering fraud. Ordinary users cannot distinguish the legitimate protocol from a scam impersonating it.

**Top 3 Positive Signals:**
1. **Ethereum Foundation PSE (Privacy and Scaling Explorations) grant funding and endorsement.** The PSE group is one of the most credible due diligence filters in crypto infrastructure — they fund genuine ZK research. PSE maintains a public project page for ZKP2P at pse.dev/projects/zkp2p.
2. **Fully verifiable team with continuous track record from 2018.** All four co-founders are ex-Set Protocol — a real, audited DeFi protocol they worked on together since 2018. Brian Weickmann has an identifiable pre-crypto career (DRW natural gas options market maker), a published whitepaper (Set Protocol v1.2, 2019), npm packages, and consistent GitHub activity. Richard Liang has a public GitHub with 31+ repos and active research talk invitations.
3. **Transparent self-documentation of risks.** Peer publishes its own risk documentation at docs.peer.xyz/developer/risks and directly discloses the multisig key forgery risk, proxy collusion risk, and MITM attack vector. Projects intending to steal from users do not document how they could steal from users.

---

## 2. Team Assessment

### 2.1 Brian Weickmann — Co-Founder
**Handle:** [@Bmwball56](https://twitter.com/Bmwball56) | **GitHub:** @bweick (npm) | **GitHub Org:** [github.com/zkp2p](https://github.com/zkp2p)

**Verified Claims:**
- **DRW natural gas options market maker** (pre-crypto) — DRW is one of the most respected quantitative trading firms in the world; employment there is verifiable via professional network references and is nearly impossible to fabricate
- **Co-authored Set Protocol whitepaper** (v1.2, April 2019, with Felix Feng) — publicly available PDF, permanently archived, titled "Set: A Protocol for Baskets of Tokenized Assets." This is a primary source that hard-anchors his pre-ZKP2P identity.
- **Technical Operations Lead at Set Protocol** (2018–2022 era) — confirmed via Messari AMA where he participated alongside Set co-founder Inje Yeo and Richard Liang in an official capacity
- **Published 15 npm packages** under handle `bweick` — primarily JavaScript libraries for Set Protocol v2 contract interaction; presence on npm is a soft technical credential verifier
- **ZK Podcast Episode 312 appearance** (with Richard Liang) — the Zero Knowledge Podcast (zeroknowledge.fm) maintains high technical standards for guests; this appearance independently confirms technical legitimacy in the ZK space

**Unverified:**
- Current equity structure and ownership percentage in P2P Labs Inc. — not publicly disclosed
- Whether Brian maintains a personal GitHub separate from the zkp2p org (personal repos not found)

**Red Flags:** None.

---

### 2.2 Richard Liang — Co-Founder
**GitHub:** [@richardzliang](https://github.com/richardzliang) / [@richardliang](https://github.com/richardliang) | **X:** [@zkp2p](https://x.com/zkp2p) (org account)

**Verified Claims:**
- **Growth Lead at Set Protocol** — confirmed via Messari AMA
- **Co-creator and maintainer of zkp2p GitHub organization** — confirmed via GitHub organization member listing (alongside 0xSachinK)
- **ZK Podcast Episode 312 appearance** — same as Brian, independently verifies ZK technical credibility
- **Speaker at applied cryptography meetup** (Luma event linked in public sources) — confirms ongoing public ZK research presence
- **31+ public GitHub repositories** — active engineering output

**Unverified:**
- Educational background (NUS implied by org team description but not independently confirmed)
- Full name disambiguation — there are multiple "Richard Liang" entries on GitHub; richardzliang is the confirmed ZKP2P handle

**Red Flags:** None.

---

### 2.3 0xSachinK (Sachin) — Co-Founder
**GitHub:** [@0xSachinK](https://github.com/0xSachinK) | Location: India

**Verified Claims:**
- Co-creator of the zkp2p GitHub organization alongside richardzliang — confirmed as org member
- Ex-Set Protocol colleague (Brian confirms "colleagues at Set Protocol before starting ZKP2P")
- Active in ZKP2P development across multiple repositories

**Unverified:**
- Full legal name — uses pseudonym 0xSachinK publicly
- Educational background
- Prior projects beyond Set Protocol

**Red Flags:** None identified. Pseudonymous handle is common in crypto engineering. Consistent track record in the same team since 2018 mitigates anonymity risk.

---

### 2.4 Alex — Co-Founder
**Identity: PARTIALLY UNVERIFIED.**

Brian Weickmann mentioned "Alex" as a fourth co-founder in podcast interviews. No further identification (GitHub handle, surname, LinkedIn, public profile) was found in any source accessed during this investigation.

**Risk Rating: LOW** in context — this project has no user capital at risk from a rug perspective, so unidentified co-founders are less critical here than in a token-bearing protocol. However, it is still a transparency gap.

---

### 2.5 P2P Labs Inc. — Corporate Entity
The Peer mobile wallet is explicitly attributed to **P2P Labs Inc.** in the Google Play Store listing. This confirms there is an incorporated legal entity behind the project, which:
- Creates accountability anchors (legal and regulatory)
- Suggests the team has access to legal counsel
- Implies formalized relationships for any future token launch or fundraising

The exact incorporation jurisdiction and ownership structure of P2P Labs Inc. were not identified in public sources — declared gap.

---

### 2.6 GitHub Activity Assessment (ZKP2P Org)

| Repository | Stars | Language | Last Activity |
|---|---|---|---|
| zkp2p-v1-monorepo | 334 | TypeScript | Active (pinned) |
| zkp2p-poc | 94 | TypeScript | Active (pinned) |
| zkp2p-contracts | 24 | TypeScript | **March 13, 2026** |
| providers | 19 | JavaScript | March 12, 2026 |
| zkp2p-dev-client | 4 | TypeScript | February 2026 |
| zkp2p-demo | 1 | TypeScript | February 2026 |

**Assessment:** Active, genuine development with recent commits as of the day before this report. No evidence of forks-and-cosmetic-commits pattern. The V1 monorepo having 334 stars suggests real developer community interest. All repos use MIT license — open source and transparent. No deleted or archived repos found in visible data.

**Code quality indicator:** The team built from circom and halo2 ZK libraries — these are technically demanding frameworks requiring real cryptography knowledge. Fakers do not build zkEmail proof systems from scratch.

---

## 3. Third-Party Consensus

### 3.1 Independent Analyst Coverage

**Ethereum Foundation PSE (Most Authoritative Signal Found):**
ZKP2P maintains an active project page at [pse.dev/projects/zkp2p](https://pse.dev/projects/zkp2p). PSE's grant program selects projects based on technical merit in zero-knowledge proofs. Their endorsement is not promotional — it is the output of a technical review process. This is the strongest positive signal in this investigation.

**ZK Podcast (Episode 312):**
Anna and Tarun from the Zero Knowledge Podcast (zeroknowledge.fm) interviewed Brian and Richard. The ZK Podcast is a technical research podcast with high guest quality standards. Their willingness to interview the team is an indirect quality signal — the protocol's technical claims were judged credible by ZK researchers.

**Messari AMA:**
A formal AMA was conducted via Messari featuring Set Protocol co-founder Inje Yeo alongside Brian and Richard, with their Set Protocol titles confirmed. Messari's curation of this AMA provides independent documentation of the team's institutional prior work.

**DL News:**
DL News ran a feature on ZKP2P as a "core contributor on trustless fiat ramps and the power of ZK TLS." The piece was described as more promotional than critical — it did not raise material adversarial concerns. Weight as a partially promotional signal.

**Rekt News:** No coverage found. Absence of Rekt coverage is a mild positive — no exploits or fraud have attracted their investigative attention.

**Note on coverage gap:** This project is explicitly a "proof of concept" category application per PSE's own classification. It is not covered by DeFi financial media in the same depth as protocols with billions in TVL. The research coverage is thin by design — this is academic-adjacent infrastructure, not a financial product.

### 3.2 Security Assessment

**Audits:** No published smart contract audit report from any recognized firm was found for any version of ZKP2P/Peer contracts.

This is a **material gap**. The V1 monorepo description in some sources mentions "productionized version with audits" but no audit document was publicly located during this investigation. If an audit exists, it is not indexed in press, not on the firm's public portfolio pages, and not surfaced by web search. Either:
- The audit is unpublished (private to the team)
- "With audits" refers to internal reviews, not third-party audits
- The source was imprecise

**ZK Circuit Bugs — Systemic Risk:**
The ZK Bug Tracker by 0xParc documents common vulnerabilities in zero-knowledge circuits. ZKP2P builds on the 0xParc/PSE zkEmail libraries and uses circom/halo2. ZK circuits are notoriously difficult to audit — a bug in the proof system can allow forged proofs to pass verification, silently enabling theft. There is no publicly known circuit vulnerability in zkEmail specifically, but the attack surface is non-trivial and requires deep cryptographic expertise to audit.

**Immunefi:** No bug bounty program found for ZKP2P/Peer. For a protocol where users place funds in escrow, the absence of an active bug bounty is a security process gap.

### 3.3 Community Sentiment

**Trustpilot (Only 1 Review — 1 Star):**
A September 2025 reviewer described what appears to be a legitimate protocol interaction but experienced it as a potential scam. The reviewer was directed to:
1. Send PayPal Friends & Family (non-refundable) to an individual named "Eric"
2. Download a browser extension to prove payment
3. Contact the counterparty via Telegram for dispute resolution
4. Faced a reported amount discrepancy with no resolution path

This review requires careful interpretation. **The workflow described is the actual ZKP2P protocol flow** — it is not a scam impersonating the protocol. However, the user experienced it as a scam because:
- Non-refundable payment to an individual on Venmo/PayPal is how crypto P2P scams operate
- Browser extension installation to access payment history is how credential stealers operate
- Telegram-only dispute resolution is how unaccountable operators work

The protocol is genuine. The UX is indistinguishable from fraud for a non-sophisticated user. **This is a user protection failure regardless of technical legitimacy.**

**GitHub Stars / Developer Reception:**
334 stars on the V1 monorepo is meaningful for a grant-funded ZK research project. The repo is cited in independent ZK developer communities. No pattern of artificial star inflation was identified.

**Reddit/Crypto Twitter:** No significant independent community discussion found. Volume of public discussion is proportional to the project's early stage — it is not widely known enough to have generated sustained community commentary.

---

## 4. On-Chain Findings

### 4.1 Protocol Architecture

Peer V3 operates across two layers:

**On-Chain (trustless):**
- **Escrow contracts** — hold deposited assets (USDC and other tokens)
- **Orchestrator** — manages intent lifecycle (signal, cancel, fulfill) and fee routing
- **UnifiedPaymentVerifier** — validates EIP-712 PaymentAttestations and enforces protocol rules

**Off-Chain (trusted):**
- **Attestation Service** — validates zkTLS/zkEmail/TLSNotary proofs and issues EIP-712 PaymentAttestations. This is the critical centralization point. The smart contracts accept whatever the Attestation Service certifies.
- **Gating Service** — curates intent visibility; does not touch funds
- **Quoter Backend** — indexes liquidity, provides REST API

**The critical trust assumption, in the team's own words:**
> "The protocol's governance can update the public key of the witness associated with payment verifiers. If the new key is under their control, they could potentially forge proofs, sign them, and access the USDC deposited in the protocol."

This means: whoever controls the governance multisig can, at will, replace the attestation signing key with one they control, then self-issue false PaymentAttestations that unlock any funds currently escrowed. The Escrow contracts do not verify the underlying payment — they verify the attestation signature. If the team controls the signing key, they control access to all escrowed funds.

**Current mitigation:** A multisig with undisclosed signer composition and quantity. The team states governance "will be decentralized in the future" — the same indefinite deferral pattern observed in Pendle and Threshold investigations.

### 4.2 TVL and Volume

| Metric | Value | Source |
|---|---|---|
| Current TVL | ~$156,900 | DeFiLlama (surge of 45% noted) |
| Weekly volume (late 2025) | ~$300,000+ | ZKP2P team announcement |
| Monthly volume | $1M+ | ZKP2P team (confirmed reaching milestone) |
| Total volume (self-reported) | $20M+ | peer.xyz home page claim |
| DeFiLlama listing | Yes | defillama.com/protocol/zkp2p |

**Assessment:** TVL is very small relative to the risks documented. At ~$156K, total maximum theft from attestation key compromise would be bounded by current escrow balances. This is a material mitigant — this is not a protocol managing hundreds of millions. However, if the protocol scales (which it is actively attempting to do) without fixing the attestation service centralization, the risk scales proportionally.

**Volume vs. TVL:** The $1M+ monthly volume figure with ~$156K TVL is consistent with a P2P escrow model where funds flow through quickly rather than sitting locked. Volume figures are not independently verifiable from available data — declared as team-reported.

### 4.3 Token Analysis

**Finding: No PEER governance token exists as of March 2026.**

Extensive search found no PEER token on any chain, no token sale, no announced tokenomics, and no confirmed airdrop. The project is token-free. This is simultaneously:
- A major **positive signal** for current risk (nothing to dump, no insider unlock cliff)
- A **future risk vector** (any token launch would create exit opportunity for team with undisclosed multisig structure)

DeFiLlama's tokenless protocols airdrop tracker was not checked directly, but the project did not appear in any standard airdrop farming guides or token announcement searches.

### 4.4 Treasury and Funding

**Confirmed funding:** 100% grant-funded via:
- Ethereum Foundation PSE group (primary funder)
- GCC (Gitcoin-affiliated)
- Other unspecified grants

**No VC funding found.** No announced investment rounds from a16z, Paradigm, Framework Ventures, or any venture fund were identified despite targeted searches. This is credible given the Ethereum Foundation's explicit grant focus on non-commercial ZK infrastructure.

**Implication:** No large VC exit pressure. No token unlock cliff from investors. The team is building to PSE's mission (public goods), not to a token listing. This dramatically reduces the traditional rug pull incentive structure.

---

## 5. Red Flags Register

| # | Flag | Severity | Evidence | Why It Matters |
|---|---|---|---|---|
| 1 | **Attestation Service controls access to all escrowed funds** — governance multisig can replace signing key and forge PaymentAttestations | HIGH | docs.peer.xyz/developer/risks (self-disclosed); confirmed by docs.peer.xyz/protocol architecture analysis | The entire "non-custodial" framing rests on the integrity of this off-chain service; compromise = total loss of all current escrow |
| 2 | **Governance multisig composition undisclosed** — number of signers, signer identities, and key custody arrangement not publicly documented | HIGH | No documentation found in any public source; protocol docs only say "initially multisig, will be decentralized in future" | Cannot independently verify that key rotation is protected by meaningful threshold or separation of duty |
| 3 | **No published smart contract audit from recognized firm found** | HIGH | Web search of audit firm public portfolios (Spearbit, ChainSecurity, Ackee, Trail of Bits) returned no Peer/ZKP2P results | Users placing funds in escrow have no independent security validation; ZK circuit bugs could silently allow proof forgery |
| 4 | **Protocol UX indistinguishable from P2P payment scams** — non-refundable PayPal F&F + browser extension + Telegram = canonical fraud template | HIGH | Trustpilot 1-star review (Sep 2025); confirmed by protocol documentation review | Ordinary users cannot distinguish the legitimate protocol from social engineering attacks impersonating it; high user harm vector |
| 5 | **Proxy/Notary collusion risk** (self-disclosed) — buyer + Notary/Proxy collusion can forge proofs to drain seller liquidity | MEDIUM | docs.peer.xyz/developer/risks (direct quote from team) | Third parties in the attestation chain are trusted actors; no on-chain verification of their integrity |
| 6 | **MAN-IN-THE-MIDDLE attack on proxy-TLS** (self-disclosed) — buyer can inject spoofed ciphertext during proxy-TLS session | MEDIUM | docs.peer.xyz/developer/risks (direct quote from team) | Allows buyer to prove a payment that never occurred; seller loses escrowed funds |
| 7 | **Alex co-founder identity unverified** | MEDIUM | Brian Weickmann podcast reference only; no GitHub, LinkedIn, or public profile found | One of four co-founders cannot be independently verified; minor transparency gap |
| 8 | **Context integrity attacks on zkTLS** — selective disclosure allows quoting data out of context (e.g., a $5K customer service message instead of actual bank balance) | MEDIUM | Academic zkTLS security literature; Oasis.net zkTLS analysis | Could allow buyers to prove "payment was made" using crafted partial email proofs |
| 9 | **No bug bounty program found** | MEDIUM | No Immunefi listing, no HackerOne page, no public bounty documentation | For a protocol where users place USDC in escrow, absence of white-hat incentive program leaves security gaps unreported |
| 10 | **"Decentralization in the future" governance deferral** — identical language used by multiple protocols that never decentralize | LOW | docs.peer.xyz/developer/risks + protocol docs | Pattern-matched against Pendle (4 years) and Threshold (4 years) — this phrase is an indefinite timeline, not a commitment |
| 11 | **TEE-based attestation variant introduces counterparty risk** — users trust TEE hardware and operator | LOW | Academic zkTLS analysis (Oasis blog, emergentmind.com) | TEE operators effectively hold encrypted session data; breaks trust-minimization claim for that attestation variant |
| 12 | **"Sketchy extension" user perception** — PeerAuth browser extension accessing payment platform data is a real security surface | LOW | Trustpilot review; confirmed by docs describing extension's payment data access | Browser extensions with financial data access are high-value attack targets; if the extension is compromised, buyer payment data is exposed |

---

## 6. Unresolved Questions

1. **What is the composition of the governance multisig?** How many signers? Who are they? What is the key rotation threshold? This is the most critical unresolved question — it determines whether the attestation key forgery attack is a realistic threat or a theoretical one constrained by trust in specific named individuals.

2. **Does a published smart contract audit exist?** The V1 monorepo description in some sources says the alpha is "productionized with audits" — but no audit document was found. If an audit exists, why is it not publicly accessible?

3. **Who is "Alex" (the fourth co-founder)?** No public identification found despite multiple searches.

4. **What is the exact legal status and ownership structure of P2P Labs Inc.?** Jurisdiction, incorporation date, and ownership shares are not publicly available.

5. **Has the Attestation Service ever been compromised, gone offline, or failed in production?** User reports of payment proof failures would indicate protocol reliability issues. Only one Trustpilot review exists, which is insufficient to assess failure rate.

6. **What is the current daily/weekly active user count and transaction success rate?** Volume figures are self-reported; independent on-chain verification of the $20M+ total volume claim was not performed.

7. **What is the plan and timeline for Attestation Service decentralization?** Specifically: will there be a network of independent attestors? What prevents them from colluding?

---

## 7. Comparative Analysis

### 7.1 Category Classification
Peer does not compare cleanly to any previously investigated protocol in this research series. The closest architectural analogues are:
- **Tornado Cash** (ZK proof-based escrow, similar trust model)
- **LocalBitcoins** (P2P fiat-to-crypto, manual escrow)
- **Wyre/MoonPay** (fiat onramps, but centralized)

The key differentiator from all three: ZKP2P is attempting to replace human arbitration (LocalBitcoins) and centralized custody (Wyre) with cryptographic attestation. This is a genuine technical innovation. The question is whether the cryptographic attestation is itself trustless.

**Answer:** At current stage, **it is not fully trustless.** The Attestation Service is a single point of trust that can be captured by governance.

### 7.2 Rug Pull Pattern Assessment

Classic rug pull checklist — applied to Peer:

| Factor | Status | Assessment |
|---|---|---|
| Native token to dump | ❌ None | Not applicable — no token exists |
| Significant user TVL | ❌ $156K | Too small to incentivize exit scam |
| Anonymous team | ❌ Verifiable | Brian, Richard, Sachin identifiable |
| Hidden insider allocation | ❌ Grant-funded | No token allocation exists |
| Fabricated audit claims | ⚠️ Unclear | "With audits" claim, no report found |
| Rapid TVL accumulation | ❌ Slow growth | $10K → $100K/day took months |
| Promises of unrealistic yield | ❌ None | Zero yield product |
| Delete + disappear pattern | ❌ Absent | Active development, public comms |

**Assessment:** Peer/ZKP2P fails to match any meaningful rug pull pattern. The architecture is technically novel, the team is traceable, and there is no token to exit with. This does not mean it is risk-free — the attestation service centralization is a real risk — but it is not a fraud risk in the classical sense.

### 7.3 Regulatory Risk Assessment
This project carries a **non-trivial regulatory surface** that is absent from most DeFi protocols:

- **FINCEN/FinTech regulation:** ZKP2P enables unlicensed P2P fiat-crypto conversion. In the US, operating a money transmission business without a license (or facilitating unlicensed ones) may violate federal law. PayPal Friends & Family payments for crypto onramps may additionally violate PayPal's Terms of Service, potentially resulting in account bans for users.
- **KYC/AML exposure:** The protocol is explicitly built to be KYC-free. The "Gating Service" offers *optional* identity verification but it is not mandatory. Regulators examining crypto onramps without KYC are likely to focus on this architecture.
- **Privacy-as-mixer framing:** DL News noted that the protocol's team acknowledged the "privacy-preserving" framing could attract regulatory scrutiny, and that the rebrand from ZKP2P to Peer was partly to move away from the "cyberpunk crowd" connotations.

---

## 8. Final Risk Matrix

| Category | Rating | Notes |
|---|---|---|
| Team Integrity | ✅ LOW RISK | Decade-long verifiable track record; DRW + Set Protocol + Ethereum Foundation credentials |
| Protocol Architecture Trust | 🔴 HIGH RISK | Attestation Service = custodial bottleneck; governance key can authorize theft |
| Smart Contract Security | 🟡 MEDIUM RISK | No published third-party audit found; ZK circuit bugs are non-trivial; small TVL mitigates scope |
| User Protection | 🔴 HIGH RISK | Protocol UX is indistinguishable from P2P scam template; users cannot defend themselves without deep protocol knowledge |
| Token Economics | ✅ NOT APPLICABLE | No token exists |
| Funding / Rug Incentive | ✅ LOW RISK | Grant-funded; no VC unlock pressure; team cannot "rug" what doesn't exist as an investment vehicle |
| Regulatory Risk | 🟡 MEDIUM RISK | KYC-free fiat-crypto conversion; PayPal ToS conflict; US money transmission law exposure |
| Development Activity | ✅ LOW RISK | Active GitHub commits as of March 13, 2026 |
| Exit Scam Probability | ✅ VERY LOW | No token, $156K TVL, verifiable team, Ethereum Foundation backing |

---

## 9. Conclusions

Peer/ZKP2P is **not a scam**. It is a technically genuine, grant-funded ZK infrastructure project built by a verifiable team with a decade of traceable work history. The Ethereum Foundation does not fund exit scams.

However, **two independent, material risks** demand explicit attention:

**For users placing funds into escrow:** The governance multisig can replace the Attestation Service signing key and drain all escrowed funds. This is self-documented. Until the Attestation Service is decentralized — with a public, verifiable network of independent attestors — users of the protocol are extending trust to the team's multisig in every transaction. The "non-custodial" label obscures this trust assumption.

**For ordinary users interacting with the protocol:** The transaction flow is functionally identical to how crypto P2P scammers operate. Users who do not deeply understand ZK proof attestation, zkTLS, and Telegram-based escrow resolution are at high risk of being defrauded by fake versions of this protocol — or simply by failing to understand the risk they are accepting in the legitimate protocol. There is no dispute resolution, no PayPal purchase protection (Friends & Family is non-refundable), and no recovery mechanism.

**What this protocol is not:**
- An investment vehicle (no token, no yield)
- A protocol managing significant institutional capital ($156K TVL)
- A fraud with exit scam mechanics

**What it is:**
- A technically innovative but early-stage ZK infrastructure project
- A protocol where protocol-level trust in the team's multisig is currently unavoidable
- A category of product that is genuinely difficult for ordinary users to safely use

---

*Sources consulted: pse.dev/projects/zkp2p, github.com/zkp2p, docs.peer.xyz/protocol/zkp2p-protocol, Set Protocol whitepaper (2019), Messari AMA (Inje Yeo + Brian Weickmann + Richard Liang), Zero Knowledge Podcast Episode 312, Web3 Galaxy Brain podcast (Brian Weickmann interview), Trustpilot review (zkp2p.xyz), DL News interview, DeFiLlama (defillama.com/protocol/zkp2p), DappRadar, ZKP2P GitHub (zkp2p-v1-monorepo, zkp2p-contracts, providers), Google Play Store (P2P Labs Inc.), npm (@bweick packages), oasis.net zkTLS security analysis, Stanford Blockchain Review (zkTLS + DECO protocol), emergentmind.com zkTLS vulnerability research.*
