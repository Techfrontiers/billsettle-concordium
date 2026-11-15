# BillSettle — Verified by Concordium

**Concordium Trusted Agents Hackathon** (solo entry, testnet only). Submit by 10 Dec 2026 06:59 Bangkok.

> **Separate repo — do NOT merge back into BillSettle (NEAR).**
> This repo is the Concordium entry, built on the BillSettle agent. The original BillSettle project (NEAR Hackathon entry, submitted 13 Nov 2026) lives in its own repo — https://github.com/Techfrontiers/billsettle — and is untouched (reverted to its pre-Concordium state). Same agent, different hackathon, different repo and demo link.

## What this is

BillSettle is a payment agent for small shops: it settles bills in stablecoin, confirms payment on-chain, and issues a receipt with the transaction hash. For Concordium, we add accountability — the shop owner verifies once (Verified by Concordium badge), the agent is registered in the Agent Registry with a CIS-8004 Agent Card, and payments flow via x402 (stretch).

- **NEAR testnet stays the payment rail** (`billsettle-bills.testnet` + `billsettle-token.testnet` BSDD, untouched).
- **Concordium testnet adds the trust layer** (badge + registry).

## Concordium registration & verification (done)

- Agent **#1185**, Token **#1185**, status **Active**, type **Native**, CIS-8004 contract **`<12802,0>`** (testnet)
- Badge (short): `JyP9WvdiYC2ADhyQTirr5`
- Badge (CAIP-19): `ccd:4221332d34e1694168c2a0c0b3fd0f27/cis-2:JyP9WvdiYC2ADhyQTirr5`
- Owner: `3fFCiJ13LTXL9j2GaNAAMq5C3xMNpcdQGTyt6VgkCkxjz1SKW9`
- Registration Tx: [`8d81b6b7…`](https://ccdexplorer.io/testnet/transaction/8d81b6b70c22a92e2c3590906586ea0d8256f629139b1126771571d504e2bb0e) ([CCDScan](https://testnet.ccdscan.io/?dcount=2&dentity=transaction&dhash=8d81b6b70c22a92e2c3590906586ea0d8256f629139b1126771571d504e2bb0e)) — block `50843126`, SUCCESS, 15 Nov 2026 19:12 Bangkok, fee `15.699899 CCD`
- `CIS-8004.setAgentURI` Pin Tx: [`99cb30ca…`](https://ccdexplorer.io/testnet/transaction/99cb30caac8d100394b519d8d13e0e0bccc551f75127a94aa871eca9f2b3f861) ([CCDScan](https://testnet.ccdscan.io/?dcount=2&dentity=transaction&dhash=99cb30caac8d100394b519d8d13e0e0bccc551f75127a94aa871eca9f2b3f861)) — block `50844557`, SUCCESS, 15 Nov 2026 20:00:30 Bangkok, fee `13.574567 CCD`
- Anchored `agent_uri`: https://techfrontiers.github.io/billsettle-concordium/.well-known/agent-card.json
- Anchored `metadata_hash_hex` (SHA-256): `bd4e0a744cd4489979afaf737d67725e415048b588deabf3a037ee497fff3e07`
- Live `badge-check`: https://agent-registry-mcp.concordium.com/v1/badge-check/JyP9WvdiYC2ADhyQTirr5 (`badge_valid: true`, `extension_conformant: true`, `verification_present: true`, `verify_url_matches: true`, `hash_matches_on_chain: true`, `issues: []`)
- Demo: https://techfrontiers.github.io/billsettle-concordium/

## Status / next steps

See `concordium/STATUS.md` (including the ≤3 min demo video script and Encode Club submission text). Plan: `concordium/INTEGRATION_PLAN.md` (Thai).

Next: record demo video ≤3 min + submit on Encode Club before 10 Dec 2026 06:59 Bangkok.
