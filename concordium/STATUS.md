# Concordium × BillSettle — Status (for AGY)

Updated: 18 Nov 2026 ~12:20 Bangkok. Source of truth: `concordium/INTEGRATION_PLAN.md` (Thai, steps 0–6).

## ⚠️ Repo separation (15 Nov 19:53, sydear's order)

**This repo (`billsettle-concordium`) is the Concordium entry — SEPARATE from the BillSettle NEAR project.**
- Original BillSettle repo: https://github.com/Techfrontiers/billsettle — **reverted to its pre-Concordium state (commit `1c48a395`)**. All Concordium files (concordium/, agent-card.json, .nojekyll, badge UI, wc-bundle.js) were removed from it. Its demo is back to exactly what was submitted to NEAR. **Do NOT push Concordium work there again.**
- This repo holds ALL the Concordium work: the plan, the Agent Card, the badge UI demo, the setAgentURI signer.
- Demo: https://techfrontiers.github.io/billsettle-concordium/ (NOT the billsettle link)
- Agent Card: https://techfrontiers.github.io/billsettle-concordium/.well-known/agent-card.json

## What is done

- **Registered NATIVE on Concordium testnet — 15 Nov 2026 19:12:48 Bangkok.**
  - Agent **#1185**, Token **#1185**, status **Active**, type **Native**, contract **CIS-8004 #12802** (`<12802,0>`)
  - Badge (short): `JyP9WvdiYC2ADhyQTirr5`
  - Badge (full CAIP-19): `ccd:4221332d34e1694168c2a0c0b3fd0f27/cis-2:JyP9WvdiYC2ADhyQTirr5`
  - Owner: `3fFCiJ13LTXL9j2GaNAAMq5C3xMNpcdQGTyt6VgkCkxjz1SKW9`
  - Registration Tx: `8d81b6b70c22a92e2c3590906586ea0d8256f629139b1126771571d504e2bb0e` (block `50843126`, SUCCESS), fee `15.699899 CCD`.
  - On-chain token id (hex): `a104000000000000`, supply 1.
- **Decision (sydear, 15 Nov 19:07): NO NEAR in the registration.** Native model A only, no MCP, no CIS-8 NEAR key binding. NEAR stays the bill-payment rail only.
- **Agent Card JSON anchored on-chain via `CIS-8004.setAgentURI` — 15 Nov 2026 20:00:30 Bangkok.**
  - `CIS-8004.setAgentURI` Tx: `99cb30caac8d100394b519d8d13e0e0bccc551f75127a94aa871eca9f2b3f861` (block `50844557`, SUCCESS, fee `13.574567 CCD`).
  - Anchored `agent_uri`: `https://techfrontiers.github.io/billsettle-concordium/.well-known/agent-card.json`
  - Anchored `metadata_hash_hex` (SHA-256): `bd4e0a744cd4489979afaf737d67725e415048b588deabf3a037ee497fff3e07` (`3,604 bytes`, LF locked via `.gitattributes`)
  - Live `badge-check` (`https://agent-registry-mcp.concordium.com/v1/badge-check/JyP9WvdiYC2ADhyQTirr5`): `badge_valid: true`, `extension_conformant: true`, `verification_present: true`, `verify_url_matches: true`, `hash_matches_on_chain: true`, `issues: []`.
- **Badge UI live in this repo's demo** (`docs/index.html` + `docs/app.js`): "Verified by Concordium — Verified · Card Hash Match ✓", with Agent Badge, Owner, Registry Contract, CCDExplorer (Reg Tx + URI Pin Tx) / CCDScan links, and Agent Card JSON link. `verifyBadge()` checks the live badge-check endpoint + the served card SHA-256.
- **setAgentURI signer built** (`docs/wc-bundle.js` + dashboard): owner can update the anchored card URI + hash on-chain in one click (Mobile Wallet WalletConnect QR or Browser Wallet).
- **Project created on Encode Club** ("BillSettle", solo, join code `8743a80a`, expires 22 Nov 18:04). Checkpoint 1 deadline 23 Nov 06:59 already satisfied.

## What is next (AGY — work ONLY in this repo)

1. **Demo video ≤3 min recorded & published on YouTube:** https://youtu.be/OZGID50FQqI (`2:48`, 1920×1080, public).
2. **Final submission on Encode Club:** Checkpoint 2 opens **Mon 23 Nov 2026 06:59 Bangkok** and closes **Thu 10 Dec 2026 06:59 Bangkok**. Copy-paste the prepared answers below directly when Checkpoint 2 opens. x402 remains an optional stretch (badge + registry + live on-chain card SHA-256 verification already satisfy "meaningful use").
3. *(Note: `verifyUrl` endpoint `https://agent-registry-mcp.concordium.com/v1/badge-check/JyP9WvdiYC2ADhyQTirr5` re-verified live 18 Nov 2026 and returns `badge_valid: true`, `issues: []`, CORS `*`.)*

## Open / watch

- Do NOT modify `docs/.well-known/agent-card.json` unless you intend to re-sign `CIS-8004.setAgentURI` with the new SHA-256 hash (`.gitattributes` locks LF).
- Do NOT use mainnet contract numbers (CIS-8004 mainnet 10082) on testnet. Testnet only.
- NEAR Hackathon (BillSettle submitted 13 Nov) results due 19 Nov 06:59 — **separate work, separate repo. Do not touch the BillSettle repo.**

## Key accounts (testnet only)

- Concordium owner: `3fFCiJ13LTXL9j2GaNAAMq5C3xMNpcdQGTyt6VgkCkxjz1SKW9`
- NEAR bills contract: `billsettle-bills.testnet` · token: `billsettle-token.testnet` (BSDD) · shop: `billsettle-shop.testnet`
- This repo: https://github.com/Techfrontiers/billsettle-concordium · Demo: https://techfrontiers.github.io/billsettle-concordium/
- Original (NEAR, untouched): https://github.com/Techfrontiers/billsettle · Demo: https://techfrontiers.github.io/billsettle/

## Demo video script (≤ 3 min walkthrough)

> Record screen at 1080p (~2:15–2:45 total) showing the live GitHub Pages site + Concordium explorer + Agent Card JSON.

1. **[0:00–0:25] Problem & Architecture:**
   - Open `https://techfrontiers.github.io/billsettle-concordium/`.
   - Explain: Small shops issue bills in chat and lose track of cash/transfer slips. **BillSettle** settles invoices in BSDD stablecoin on **NEAR Testnet**, while **Concordium Testnet** provides the **Verified by Concordium** human-accountability trust layer (`CIS-8004` contract `<12802,0>`).
2. **[0:25–1:05] Live Concordium Badge Verification (`verifyBadge()`):**
   - Point to the header badge `JyP9WvdiYC2ADhyQTirr5` and the **Verified by Concordium** dashboard card showing green **`Verified · Card Hash Match ✓`**.
   - Click **"Re-verify live"** and point out all 6 passing checks (`CIS-8004 Agent #1185`, `Status: Active`, `agent_uri Set`, `SHA-256 Match`, `A2A Extension Conformant`, `Verification Hints Present`) and the matching SHA-256 `bd4e0a744cd4489979afaf737d67725e415048b588deabf3a037ee497fff3e07`.
   - Open **"Live Badge-Check JSON ↗"** and **"Agent Card JSON ↗"** in new tabs to prove `badge_valid: true` and `issues: []`.
3. **[1:05–1:45] On-Chain Proof on Concordium Explorer:**
   - Open **"CCDExplorer Reg Tx ↗"** (`8d81b6b7…`, block `50843126`) and **"CCDExplorer URI Tx ↗"** (`99cb30ca…`, block `50844557`) or **"CCDScan Token #1185 ↗"** (`JyP9WvdiYC2ADhyQTirr5`), showing the verified human owner `3fFCiJ13LTXL9j2GaNAAMq5C3xMNpcdQGTyt6VgkCkxjz1SKW9` and pinned `agent_uri`.
4. **[1:45–2:30] Bill Settlement + Dual-Chain Verified Receipt:**
   - Click Bill **`B1`** (`#/bill/B1`), show the shop invoice items (`620 BSDD`), and scroll to **Verified Receipt**.
   - Show how **Settled On-Chain** on NEAR Testnet (`billsettle-customer.testnet`, tx `9fxsLpNo...`) sits directly above **Verified by Concordium** (`JyP9WvdiYC2ADhyQTirr5`, owner `3fFCiJ…z1SKW9`, contract `<12802,0>`), giving customers cryptographic proof of both payment and accountable human identity behind the merchant agent.

### Ready-to-Read Voiceover Script (~2:25, ~335 words)

> **Recording Setup:** Open Chrome at 1920×1080 (`100%` zoom) with 2 tabs preloaded:
> 1. `https://techfrontiers.github.io/billsettle-concordium/`
> 2. `https://techfrontiers.github.io/billsettle-concordium/#/bill/B1` (or click `B1` live during Scene 4)

- **[0:00–0:25] Intro & Problem:**
  > "Small shops issue bills in chat every day, and buyers have no cryptographic proof of who stands behind a payment link—or whether a transfer actually settled. Meet **BillSettle — Verified by Concordium**. It keeps fast stablecoin invoice settlement on **NEAR Testnet**, while adding a tamper-evident **Verified by Concordium** human-accountability layer on **Concordium Testnet** via the **CIS-8004** Agent Registry."

- **[0:25–1:05] Live Badge Verification:**
  > "Right in the header and dashboard, you see our live Concordium badge **`JyP9WvdiYC2ADhyQTirr5`** showing **`Verified · Card Hash Match`**. Let's click **Re-verify live**. In real time, the browser queries Concordium's Registry MCP verifier and hashes our served A2A Agent Card with SHA-256. All six checks pass—Native Agent `#1185` on contract `<12802,0>`, Status Active, `agent_uri` set, and exact SHA-256 hash match. Opening **Live Badge-Check JSON** confirms `badge_valid: true` and zero issues, and **Agent Card JSON** shows the `concordium-badge/v1` extension."

- **[1:05–1:45] On-Chain Explorer Proof:**
  > "Every claim is backed on-chain. Clicking **CCDExplorer Reg Tx** shows the native registration in block `50843126` signed by the verified human owner `3fFCiJ…z1SKW9`. Clicking **CCDExplorer URI Tx** shows the `CIS-8004.setAgentURI` transaction in block `50844557` anchoring both the canonical Agent Card URL and its SHA-256 metadata hash—also visible as Token `#1185` on CCDScan."

- **[1:45–2:25] Dual-Chain Verified Receipt & Outro:**
  > "Now let's open **Bill B1** for 620 BSDD. Scrolling to **Verified Receipt**, the customer sees two linked proofs side-by-side: **Settled On-Chain** on NEAR Testnet with the real Explorer transaction hash, directly paired with **Verified by Concordium** proving the accountable human owner behind the merchant agent. Fast stablecoin payments on NEAR, cryptographic human accountability on Concordium—thank you!"

- **Cover image saved for Encode Club:** `concordium/cover.jpg` (16:9 banner ready to drag-and-drop into Encode Club's Project Image uploader).

## Encode Club final submission text (ready to paste — Checkpoint 2 opens 23 Nov 2026 06:59 Bangkok)

**Project Name:** BillSettle — Verified by Concordium

**Short Summary (Project Card):**
A small-shop stablecoin invoice settlement agent built on NEAR Testnet (BSDD), anchored with on-chain human accountability on Concordium Testnet via CIS-8004 Agent Registry (Agent #1185, badge JyP9WvdiYC2ADhyQTirr5), an A2A Agent Card (SHA-256 pinned on-chain via setAgentURI), and live badge_valid: true verification across dashboard and customer receipts.

**1. Submission Details (`detailed_description`, Required):**
Small shops often settle bills informally over chat, leaving buyers with no proof of who stands behind a payment request or whether a payment actually cleared. BillSettle separates settlement and trust cleanly without disrupting the working NEAR stablecoin rail:
- **Human Accountability (Concordium Testnet):** The merchant owner (`3fFCiJ13LTXL9j2GaNAAMq5C3xMNpcdQGTyt6VgkCkxjz1SKW9`) registered BillSettle natively in Concordium's **CIS-8004 Agent Registry (`<12802,0>`)** as **Agent `#1185`** (badge `JyP9WvdiYC2ADhyQTirr5`, CAIP-19 `ccd:4221332d34e1694168c2a0c0b3fd0f27/cis-2:JyP9WvdiYC2ADhyQTirr5`).
- **On-Chain Agent Card Integrity (`setAgentURI`):** The A2A Agent Card (`/.well-known/agent-card.json`) embeds the `concordium-badge/v1` extension and has its canonical URL and SHA-256 hash (`bd4e0a744cd4489979afaf737d67725e415048b588deabf3a037ee497fff3e07`) anchored on-chain via `CIS-8004.setAgentURI` (tx `99cb30caac8d100394b519d8d13e0e0bccc551f75127a94aa871eca9f2b3f861`, block `50844557`).
- **Live Verification UX + Receipts:** Every page load runs `verifyBadge()` against Concordium's Registry MCP verifier (`https://agent-registry-mcp.concordium.com/v1/badge-check/JyP9WvdiYC2ADhyQTirr5`) and hashes the served Agent Card in-browser (`crypto.subtle.digest("SHA-256")`), displaying live **Verified by Concordium** proof (`badge_valid: true`, `issues: []`) alongside NEAR Testnet settlement receipts on every bill.

**2. Link to Code (`link_to_repository`, Required):**
https://github.com/Techfrontiers/billsettle-concordium

**3. Link to Demo Video (`link_to_video`, Required — ≤ 3 min):**
https://youtu.be/OZGID50FQqI

**4. Testnet Link (`CCDScan / CCDExplorer`, Required):**
https://ccdexplorer.io/testnet/transaction/99cb30caac8d100394b519d8d13e0e0bccc551f75127a94aa871eca9f2b3f861
*(Or Token #1185: https://testnet.ccdscan.io/?dcount=1&dentity=token&did=a104000000000000&dcontractAddressIndex=12802&dcontractAddressSubIndex=0)*

**5. Which Concordium components does your project use? (Required multiselect):**
- `Agent Registry & Verified by Concordium badge`
- `Agent Registry MCP server`
- `A2A`

**6. Your Path to Mainnet (Required):**
1. **Mainnet Registry Migration:** Re-register the merchant agent on Concordium Mainnet's CIS-8004 contract (`<10082,0>`) backed by a production Concordium ID / LEI corporate identity for the merchant, then pin the production `agent-card.json` URI and SHA-256 hash on mainnet via `setAgentURI`.
2. **Production Stablecoin & Fiat-Free UX:** Switch NEAR bills/settlement from mock `BSDD` on `testnet` to mainnet USDC/USDT (or Concordium Protocol-Level Tokens + sponsored transactions so shop customers never manage gas fees).
3. **Target Users & Rollout:** Independent retail merchants, social-commerce sellers (LINE/Telegram/WhatsApp shops), and B2B micro-vendors who need tamper-evident receipts and verifiable human accountability before buyers scan a QR code to pay.
4. **Remaining Build Items:** Add merchant onboarding flow (one-click Concordium ID verification + `setAgentURI`), optional x402 automated invoice-to-agent settlement, and receipt PDF/webhook export for shop POS/accounting.

**7. Live Demo Link (`link_to_live_product`, Optional):**
https://techfrontiers.github.io/billsettle-concordium/

**Key Links (Testnet):**
- Live Demo: https://techfrontiers.github.io/billsettle-concordium/
- GitHub Repo: https://github.com/Techfrontiers/billsettle-concordium
- Hosted Agent Card: https://techfrontiers.github.io/billsettle-concordium/.well-known/agent-card.json
- Live Badge-Check Endpoint: https://agent-registry-mcp.concordium.com/v1/badge-check/JyP9WvdiYC2ADhyQTirr5
- Registration Tx (CCDExplorer): https://ccdexplorer.io/testnet/transaction/8d81b6b70c22a92e2c3590906586ea0d8256f629139b1126771571d504e2bb0e
- `setAgentURI` Tx (CCDExplorer): https://ccdexplorer.io/testnet/transaction/99cb30caac8d100394b519d8d13e0e0bccc551f75127a94aa871eca9f2b3f861
- Token #1185 (CCDScan): https://testnet.ccdscan.io/?dcount=1&dentity=token&did=a104000000000000&dcontractAddressIndex=12802&dcontractAddressSubIndex=0
