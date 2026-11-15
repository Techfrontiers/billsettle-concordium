# Concordium × BillSettle — Status (for AGY)

Updated: 15 Nov 2026 ~20:00 Bangkok. Source of truth: `concordium/INTEGRATION_PLAN.md` (Thai, steps 0–6).

## ⚠️ Repo separation (15 Nov 19:53, sydear's order)

**This repo (`billsettle-concordium`) is the Concordium entry — SEPARATE from the BillSettle NEAR project.**
- Original BillSettle repo: https://github.com/Techfrontiers/billsettle — **reverted to its pre-Concordium state (commit `1c48a395`)**. All Concordium files (concordium/, agent-card.json, .nojekyll, badge UI, wc-bundle.js) were removed from it. Its demo is back to exactly what was submitted to NEAR. **Do NOT push Concordium work there again.**
- This repo holds ALL the Concordium work: the plan, the Agent Card, the badge UI demo, the setAgentURI signer.
- Demo: https://techfrontiers.github.io/billsettle-concordium/ (NOT the billsettle link)
- Agent Card: https://techfrontiers.github.io/billsettle-concordium/.well-known/agent-card.json

## What is done

- **Registered NATIVE on Concordium testnet — 15 Nov 2026 19:12:48 Bangkok.**
  - Agent **#1185**, Token **#1185**, status **Active**, type **Native**, contract **CIS-8004 #12802**
  - Badge (short): `JyP9WvdiYC2ADhyQTirr5`
  - Badge (full CAIP-19): `ccd:4221332d34e1694168c2a0c0b3fd0f27/cis-2:JyP9WvdiYC2ADhyQTirr5`
  - Owner: `3fFCiJ13LTXL9j2GaNAAMq5C3xMNpcdQGTyt6VgkCkxjz1SKW9`
  - Tx: `8d81b6b70c22a92e2c3590906586ea0d8256f629139b1126771571d504e2bb0e` (block 50843126, SUCCESS), fee 15.699899 CCD. Balance now 19,984.300101 CCD.
  - On-chain token id (hex): `a104000000000000`, supply 1.
- **Decision (sydear, 15 Nov 19:07): NO NEAR in the registration.** Native model A only, no MCP, no CIS-8 NEAR key binding. NEAR stays the bill-payment rail only.
- **Agent Card JSON** (`docs/.well-known/agent-card.json`, + `docs/.nojekyll`): filled from the registration, badge conformance fixed by AGY (the card + badge UI + signer were moved here from the old repo).
- **Badge UI live in this repo's demo** (`docs/index.html` + `docs/app.js`): "Verified by Concordium — Active · Pending URI Pin", with Agent Badge, Owner, Registry Contract, CCDExplorer/CCDScan links, Agent Card JSON link. `verifyBadge()` checks the live badge-check endpoint + the served card SHA-256.
- **setAgentURI signer built** (`docs/wc-bundle.js` + dashboard): owner can pin the card URI + hash on-chain in one click (Mobile Wallet WalletConnect QR or Browser Wallet).
- **Project created on Encode Club** ("BillSettle", solo, join code 8743a80a, expires 22 Nov 18:04). Checkpoint 1 deadline 23 Nov 06:59 already satisfied.

## What is next (AGY — work ONLY in this repo)

1. **Pin the card on-chain:** compute SHA-256 of the card as served from THIS repo's Pages URL (`curl -s https://techfrontiers.github.io/billsettle-concordium/.well-known/agent-card.json | sha256sum`), then `setAgentURI`. Needs the user's signing — the approval prompt may appear on his **phone (Mobile Wallet)**, not in the browser. Then the name "BillSettle" will show on-chain (right now the dashboard shows name "—" and Metadata URL: N/A).
2. **Demo video ≤3 min + submission** by 10 Dec 2026 06:59 Bangkok. x402 = stretch/droppable (badge + registry alone satisfy "meaningful use").
3. **Workshops:** Mon 16 Nov 22:00 + Tue 18 Nov 22:00 Bangkok. Confirm the badge-check testnet endpoint at the workshop.

## Open / watch

- `verifyUrl` in the card is the expected endpoint but **unconfirmed** — verify at the workshop before relying on it.
- Metadata hash discrepancy (dashboard Technical view `0x2d49…` matches the tx; Simple view `0x1c1e…` differs) — unresolved, re-check when pinning the card.
- Do NOT use mainnet contract numbers (CIS-8004 mainnet 10082) on testnet. Testnet only.
- NEAR Hackathon (BillSettle submitted 13 Nov) results due 19 Nov 06:59 — **separate work, separate repo. Do not touch the BillSettle repo.**

## Key accounts (testnet only)

- Concordium owner: `3fFCiJ13LTXL9j2GaNAAMq5C3xMNpcdQGTyt6VgkCkxjz1SKW9`
- NEAR bills contract: `billsettle-bills.testnet` · token: `billsettle-token.testnet` (BSDD) · shop: `billsettle-shop.testnet`
- This repo: https://github.com/Techfrontiers/billsettle-concordium · Demo: https://techfrontiers.github.io/billsettle-concordium/
- Original (NEAR, untouched): https://github.com/Techfrontiers/billsettle · Demo: https://techfrontiers.github.io/billsettle/
