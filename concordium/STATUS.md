# Concordium × BillSettle — Status (for AGY)

Updated: 15 Nov 2026 ~20:08 Bangkok. Source of truth: `concordium/INTEGRATION_PLAN.md` (Thai, steps 0–6).

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

1. **Demo video ≤3 min + final submission** on Encode Club by **10 Dec 2026 06:59 Bangkok**. x402 = stretch/droppable (badge + registry + live on-chain card SHA-256 verification alone satisfy "meaningful use").
2. **Workshops (optional):** Mon 16 Nov 22:00 + Tue 18 Nov 22:00 Bangkok. *(Note: `verifyUrl` endpoint `https://agent-registry-mcp.concordium.com/v1/badge-check/JyP9WvdiYC2ADhyQTirr5` was tested live 15 Nov and already returns `badge_valid: true`, CORS `*`.)*

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

## Encode Club final submission text (ready to paste)

**Project Name:** BillSettle — Verified by Concordium

**Short Summary:**
A small-shop stablecoin invoice settlement agent built on NEAR Testnet (`BSDD`), anchored with on-chain human accountability on Concordium Testnet via CIS-8004 Agent Registry (`Agent #1185`), an A2A Agent Card (`SHA-256` pinned on-chain), and live `badge_valid: true` verification across dashboard and customer receipts.

**Description & How Concordium Is Used:**
Small shops often settle bills informally over chat, leaving buyers with no proof of who stands behind a payment request or whether a payment actually cleared. BillSettle separates settlement and trust cleanly without disrupting the working NEAR stablecoin rail:
- **Human Accountability (Concordium Testnet):** The merchant owner (`3fFCiJ13LTXL9j2GaNAAMq5C3xMNpcdQGTyt6VgkCkxjz1SKW9`) registered BillSettle natively in Concordium's **CIS-8004 Agent Registry (`<12802,0>`)** as **Agent `#1185`** (badge `JyP9WvdiYC2ADhyQTirr5`, CAIP-19 `ccd:4221332d34e1694168c2a0c0b3fd0f27/cis-2:JyP9WvdiYC2ADhyQTirr5`).
- **On-Chain Agent Card Integrity (`setAgentURI`):** The A2A Agent Card (`/.well-known/agent-card.json`) embeds the `concordium-badge/v1` extension and has its canonical URL and SHA-256 hash (`bd4e0a744cd4489979afaf737d67725e415048b588deabf3a037ee497fff3e07`) anchored on-chain via `CIS-8004.setAgentURI` (tx `99cb30caac8d100394b519d8d13e0e0bccc551f75127a94aa871eca9f2b3f861`, block `50844557`).
- **Live Verification UX + Receipts:** Every page load runs `verifyBadge()` against Concordium's Registry verifier and hashes the served Agent Card in-browser (`crypto.subtle.digest("SHA-256")`), displaying live **Verified by Concordium** proof (`badge_valid: true`, `issues: []`) alongside NEAR Testnet settlement receipts on every bill.

**Key Links (Testnet):**
- Live Demo: https://techfrontiers.github.io/billsettle-concordium/
- GitHub Repo: https://github.com/Techfrontiers/billsettle-concordium
- Hosted Agent Card: https://techfrontiers.github.io/billsettle-concordium/.well-known/agent-card.json
- Live Badge-Check Endpoint: https://agent-registry-mcp.concordium.com/v1/badge-check/JyP9WvdiYC2ADhyQTirr5
- Registration Tx (CCDExplorer): https://ccdexplorer.io/testnet/transaction/8d81b6b70c22a92e2c3590906586ea0d8256f629139b1126771571d504e2bb0e
- `setAgentURI` Tx (CCDExplorer): https://ccdexplorer.io/testnet/transaction/99cb30caac8d100394b519d8d13e0e0bccc551f75127a94aa871eca9f2b3f861
- Token #1185 (CCDScan): https://testnet.ccdscan.io/?dcount=1&dentity=token&did=a104000000000000&dcontractAddressIndex=12802&dcontractAddressSubIndex=0
