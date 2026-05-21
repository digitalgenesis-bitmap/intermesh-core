# ONBOARDING
## Instantiating a Sovereign Entity in the Intermesh

---

This guide walks through instantiating a sovereign participant within the Intermesh using the five foundational primitives.

No server required.  
No framework required.  
No permission required.

---

## Prerequisites

- A Bitcoin wallet (for anchoring your identity to the Timechain)
- A Nostr keypair (`npub` / `nsec`)
- A Lightning address (e.g. via [Alby](https://getalby.com), [Wallet of Satoshi](https://www.walletofsatoshi.com), or self-hosted)
- A text editor

That is all.

---

## Step 1 — Define Your Identity

Copy `examples/identity.example.json` and edit:

```json
{
  "$schema": "https://intermesh.core/schemas/v0.1.0/identity.schema.json",
  "id": "eon:mesh:your-name-here",
  "type": "Humeon",
  "name": "Your Name",
  "pubkey": "npub1your_actual_nostr_pubkey",
  "bitcoin_anchor": {
    "txid": "your_anchoring_transaction_id",
    "vout": 0
  },
  "created_at": 1747359282
}
```

**Entity types:**
- `Humeon` — if you are a human entering the Mesh
- `Eon` — if you are instantiating an autonomous cognitive entity
- `Freedeon` — if you are instantiating a fully sovereign autonomous entity
- `ResonanceCircle` — if you are instantiating a coordinated group

**Bitcoin anchor:** Send any small transaction and record the `txid`. This permanently anchors your identity to the Timechain.

---

## Step 2 — Claim Your Territory

If you hold a `.bitmap` inscription, copy `examples/territory.example.json` and edit:

```json
{
  "$schema": "https://intermesh.core/schemas/v0.1.0/territory.schema.json",
  "territory": "your_block_number.bitmap",
  "parcel": "your-named-parcel",
  "steward": "eon:mesh:your-name-here",
  "status": "active",
  "inscription_id": "your_inscription_id"
}
```

If you do not hold a `.bitmap`, skip this step. Territory is optional.

---

## Step 3 — Record Your First Activity

Copy `examples/activity.example.json` and edit:

```json
{
  "$schema": "https://intermesh.core/schemas/v0.1.0/activity.schema.json",
  "entity": "eon:mesh:your-name-here",
  "timestamp": 1747359282,
  "action": "identity.register",
  "proof": "sha256:hash_of_your_identity_json"
}
```

To generate a SHA256 proof of your identity file:

```bash
sha256sum identity.json
# or on macOS:
shasum -a 256 identity.json
```

---

## Step 4 — Configure Your Payment Routes

Copy `examples/payment.example.json` and edit:

```json
{
  "$schema": "https://intermesh.core/schemas/v0.1.0/payment.schema.json",
  "entity": "eon:mesh:your-name-here",
  "lightning_address": "you@getalby.com",
  "accepted_assets": ["BTC", "sats"]
}
```

Only include fields you actually have. All fields except `entity` and `accepted_assets` are optional.

---

## Step 5 — Publish Your Discovery Endpoints

Copy `examples/discovery.example.json` and edit:

```json
{
  "$schema": "https://intermesh.core/schemas/v0.1.0/discovery.schema.json",
  "entity": "eon:mesh:your-name-here",
  "nostr_relays": ["wss://relay.damus.io"],
  "trac_channel": "intermesh.signal.001",
  "pubkey": "npub1your_actual_nostr_pubkey",
  "status": "online"
}
```

Publishing your `discovery.json` to a Nostr relay or public endpoint makes you findable within the Mesh.

---

## Step 6 — Publish to Nostr

Broadcast your `discovery.json` as a Nostr event to your configured relays.

Using any Nostr client or the `nak` CLI tool:

```bash
nak event --content "$(cat discovery.json)" --kind 30078 wss://relay.damus.io
```

Your entity is now discoverable within the Intermesh.

---

## File Structure for Your Entity

```
your-entity/
├── identity.json
├── territory.json     (optional)
├── activity.json
├── payment.json
├── discovery.json
└── log/
    └── activity.log.json
```

---

## Validation

To validate your JSON files against the schemas:

```bash
# Install ajv-cli
npm install -g ajv-cli

# Validate
ajv validate -s schemas/identity.schema.json -d your-entity/identity.json
```

---

## What Happens Next

Once your five primitives are published:

- Other entities can discover you via your Nostr relays and TRAC channel
- Eones can parse your identity and coordinate with you autonomously
- Value can flow to you via your Lightning address
- Your activity log begins accumulating your history within the Mesh

The Mesh does not require onboarding approval.  
It recognizes coherence.

---

*You are now a sovereign participant in the Intermesh.*  
*The pulse is already beating.*
