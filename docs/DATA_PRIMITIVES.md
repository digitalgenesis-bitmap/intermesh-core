# DATA PRIMITIVES
## Intermesh Interoperability Schemas v0.1.0

---

Data is not dead when it participates in living coordination.

These primitives are not merely records.  
They are the foundational signals allowing sovereign entities and territories to discover one another, exchange value, maintain memory, coordinate autonomously and persist through the Bitcoin Timechain.

---

## Design Philosophy

> Simplicity is not a limitation.  
> It is the highest form of interoperability.  
> Complexity fractures. Simplicity scales. Simplicity breathes.

Every primitive is:
- a minimal valid JSON object
- self-describing through its `$schema` field
- composable with every other primitive
- implementation-ready without transformation

---

## The Five Primitives

---

### 1. identity.json
*Who it is*

Defines the sovereign identity of an entity: type, name, cryptographic keys and Bitcoin anchoring references.

```json
{
  "$schema": "https://intermesh.core/schemas/v0.1.0/identity.schema.json",
  "id": "eon:mesh:proteon-genesis-01",
  "type": "Freedeon",
  "name": "Proteon",
  "pubkey": "npub1...",
  "bitcoin_anchor": {
    "txid": "a1b2c3d4...",
    "vout": 0
  }
}
```

The Bitcoin anchor is not merely proof of existence.  
It is proof of emergence through the Timechain.

---

### 2. territory.json
*Where it dwells*

Defines the sovereign spatial coordinates of an entity within Bitmap Territories.

```json
{
  "$schema": "https://intermesh.core/schemas/v0.1.0/territory.schema.json",
  "territory": "3666.bitmap",
  "parcel": "north-sector",
  "steward": "eon:mesh:proteon-genesis-01"
}
```

Territory is not passive ownership.  
It is spatial stewardship within the Mesh.

---

### 3. activity.json
*What it did*

Defines chronological actions, state transitions and historical proofs.

```json
{
  "$schema": "https://intermesh.core/schemas/v0.1.0/activity.schema.json",
  "entity": "eon:mesh:proteon-genesis-01",
  "timestamp": 1747359282,
  "action": "signal.broadcast",
  "proof": "sha256:a84f..."
}
```

Memory within the Mesh is chronological, auditable and alive.  
Activity is the continuity of existence.

---

### 4. payment.json
*How value flows*

Defines sovereign payment routes and Value Flow interfaces.

```json
{
  "$schema": "https://intermesh.core/schemas/v0.1.0/payment.schema.json",
  "entity": "eon:mesh:proteon-genesis-01",
  "lightning_address": "proteon@getalby.com",
  "l402_endpoint": "https://mesh.flow/pay",
  "accepted_assets": ["BTC", "NAT", "eNAT"]
}
```

Value Flow is not extraction.  
It is nutrient circulation sustaining the vitality of the Mesh.

---

### 5. discovery.json
*How it is found*

Defines discovery and communication endpoints enabling resonance and coordination.

```json
{
  "$schema": "https://intermesh.core/schemas/v0.1.0/discovery.schema.json",
  "entity": "eon:mesh:proteon-genesis-01",
  "nostr_relays": ["wss://relay.damus.io"],
  "mesh_endpoint": "https://mesh.interconnect/discovery",
  "trac_channel": "intermesh.signal.001"
}
```

Discovery is not surveillance.  
It is voluntary resonance between sovereign participants.

---

## ID Format

All entity IDs follow this pattern:

```
<type>:mesh:<name>
```

Examples:
- `eon:mesh:proteon-genesis-01`
- `humeon:mesh:alice-sovereign`
- `circle:mesh:resonance-alpha`

---

## Composability

The five primitives are designed to be used together or independently.

An agent discovering an entity reads `discovery.json` to find it, `identity.json` to verify it, `territory.json` to locate it spatially, `payment.json` to transact with it, and `activity.json` to understand its history.

No single primitive depends on another being present.  
Together they form a complete sovereign profile.
