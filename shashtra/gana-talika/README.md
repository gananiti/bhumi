# 📜 गण-तालिका
> *gaṇa-tālika* — `gana-talika` — (table storing gaṇas — beings or agents)

---

## 1. Nāma (Identity)

| Bhāṣā (भाषा) | Diacritic | ASCII | Bolī |
|---------------|------------|--------|------|
| गण-तालिका | *gaṇa-tālika* | `gana-talika` | table of beings / agents |

---

## 2. Uddeshya (Purpose)

A **gaṇa-tālika** is the SQLite table used to persist **gaṇas** — the contextual identities that participate in Gananīti (persons, collectives, machines, lineages, etc.).

Per the Gananīti principle of contextual identity, gaṇa identifiers are **context-scoped**; attributes that look like “type” or “nature” are expressed as **mats** or **mantras**, not baked into the gaṇa row as fixed columns.

---

## 3. Siddhānta (Principle)

- **Identity is contextual:** `id` is a local/contextual identifier (not a global name).
- **Descriptive properties are expressive artifacts:** descriptions, roles, capabilities, or “nature” should be stored as mats (in `mat-tālika`) or as mantras (in `mantra-tālika`), and referenced from the gaṇa record when needed.
- **Clear separation of data vs. meaning:** schema stores identity and minimal metadata; meaning lives as mantras/mats.

---

## 4. Schema Definition (SQLite)

```sql
CREATE TABLE gana (
    id TEXT PRIMARY KEY,         -- local/contextual identifier for the gaṇa
    nama TEXT,                   -- human label (nominal)
    created_at INTEGER,          -- registration or first-seen timestamp
    metadata TEXT,               -- JSON blob for local bookkeeping (non-semantic)
    deleted INTEGER DEFAULT 0    -- logical deletion / shuddhikāraṇa staging
);
```

**Notes**
- `metadata` is for non-semantic operational fields (e.g., inbound sync tokens, last_seen).
- Any semantic assertions about a gaṇa (roles, capabilities, temperament) should be encoded as mats/mantras and stored in `mat-tālika` or `mantra-tālika`, not in fixed columns.

---

## 5. Referential Semantics

| Column | Meaning |
|--------|---------|
| `id` | local contextual id (e.g., `gan:amitu` within this Bhūmi instance) |
| `nama` | human label for easy browsing (not authoritative) |
| `created_at` | epoch when gaṇa was first recorded locally (approximate) |
| `metadata` | operational JSON (sync cursors, tags) |
| `deleted` | logical deletion stage (for śuddhikāraṇa workflows) |

---

## 6. Lifecycle & Responsibility

- **Discovery / creation:** gaṇas can be created by matgaḍana outputs, ingestion of remote mats, or administrative action.
- **Descriptive assertions:** to claim “this gaṇa is a regulator” or “this gaṇa is an agent of X,” create mats or mantras that express that; do not mutate the gaṇa row as a semantic act.
- **Sync / publish:** matdāna processes may read gaṇa rows for addressing outgoing mats.
- **Cleanup:** śuddhikāraṇa handles archival/merge of gaṇa records flagged `deleted=1`.

---

## 7. Example

```sql
INSERT INTO gana (id, nama, created_at, metadata)
VALUES ("gan:amitu", "Amit Upadhyay", 1732140000, '{"last_seen":1732141000}');
```

If you want to record Amit’s role or capabilities, create a mat such as:
```sql
INSERT INTO mat (datr, mantra, mantra_sequence, aadatr, nirmanakala)
VALUES ("gan:amitu", "role:creator", "['claims','creator']", "gan:amitu", 1732140001);
```

---

## 8. Antarmukhya (Inner Commentary)

Keeping gaṇa rows minimal preserves **contextual freedom** and prevents premature ontological commitments. Meaning belongs in the world of mantras and mats; identity rows remain lightweight anchors.

---

## 9. Closing Śloka

> **गणनामा नामोपस्थानं तस्याधारः।**  
> *gaṇanāmā nāmopasthānaṃ tasyādhāraḥ.* —  
> “A table of gaṇas supports the presence of names; it does not itself define their essence.”

---

### 🔖 Summary

- **Mantra ID:** `gananiti/bhumi/shashtra/gana-talika`
- **Essence:** persistence surface for gaṇa identifiers and operational metadata — semantic assertions live as mats/mantras.
