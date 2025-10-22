# 📜 शास्त्र-तालिका
> *śāstra-tālika* — `shashtra-talika` — (table storing śāstras — collections / fields of mantras)

---

## 1. Nāma (Identity)

| Bhāṣā (भाषा) | Diacritic | ASCII | Bolī |
|---------------|------------|--------|------|
| शास्त्र-तालिका | *śāstra-tālika* | `shashtra-talika` | table of bodies of knowledge |

---

## 2. Uddeshya (Purpose)

A **śāstra-tālika** records **śāstras** — organized collections or domains of mantras.  
Long-form descriptions, explanatory matter, and translations are **not** stored here; they live as mantras and README.* files within the mantra folders (and in `mantra-tālika` when structured).

This talika stores identity, custodianship (gaṇa), and minimal administrative metadata for each śāstra.

---

## 3. Siddhānta (Principle)

- **Structural metadata only:** the śāstra record names the field and links to its custodial gaṇa(s).
- **Meaning lives as mantras:** substantive descriptions of the śāstra (purpose, scope, examples) should be authored as mantras and mats or be present in the śāstra’s README languages — not as a `varnan` column in this table.
- **Contextual authorship:** records are context-scoped; equivalence across Bhūmi instances is resolved by mat exchanges.

---

## 4. Schema Definition (SQLite)

```sql
CREATE TABLE shashtra (
    id TEXT PRIMARY KEY,         -- śāstra identifier (e.g., 'gananiti/shashtra/mat')
    nama TEXT,                   -- human label
    datr TEXT,                   -- gaṇa who primarily maintains / created this śāstra
    created_at INTEGER,          -- registration / creation timestamp
    metadata TEXT,               -- JSON for administrative fields (version pointer, tags)
    deleted INTEGER DEFAULT 0
);
```

**Notes**
- Do not store long descriptive text here. Use mantras to encode canonical statements about the śāstra, and README.* files in the shastra folder for localized explanations.

---

## 5. Referential Semantics

| Column | Meaning |
|--------|---------|
| `id` | canonical local path/id for the śāstra |
| `nama` | human-friendly label for browsing |
| `datr` | gaṇa (owner/maintainer) — references `gana-talika` |
| `created_at` | when the śāstra was first recorded locally |
| `metadata` | operational JSON (e.g., current schema version) |
| `deleted` | logical deletion / archival staging flag |

---

## 6. Lifecycle & Responsibility

- **Creation:** matgaḍana or curator gaṇas produce new śāstra rows (metadata). The rich description is authored as mantras and stored in mantra folders (or persisted into `mantra-tālika`).
- **Use:** tools and humans look up śāstra rows to enumerate namespaces and locate mantra folders.
- **Evolution:** new versions or migrations are recorded in metadata; substantive changes are done by adding/authoring mantras or mats.
- **Cleanup:** śuddhikāraṇa archives or merges obsolete śāstras.

---

## 7. Example

```sql
INSERT INTO shashtra (id, nama, datr, created_at, metadata)
VALUES ("gananiti/shashtra/mat", "Mat Shastra", "gan:amitu", 1732000000, '{"schema_version":1}');
```

Detailed description and canonical mantras that define the śāstra’s scope should be present as mantras in `mantra-tālika` or as README.md files in the Git shashtra folder.

---

## 8. Antarmukhya (Inner Commentary)

By keeping śāstra rows minimal and delegating meaning to mantras and README files, Bhūmi preserves a clean separation between **indexing** and **semantics** — making later migration of content from Git to DB straightforward and principled.

---

## 9. Closing Śloka

> **यत्र मन्त्रसमूहः तत्र शास्त्रस्य नाम।**  
> *yatra mantra-samūhaḥ tatra śāstrasya nāma.* —  
> “Where a gathering of mantras exists, there lies the name of a śāstra.”

---

### 🔖 Summary

- **Mantra ID:** `gananiti/bhumi/shashtra/shashtra-talika`
- **Essence:** minimal administrative registry for śāstras — descriptive content belongs to mantras/mats, not to the talika table.
