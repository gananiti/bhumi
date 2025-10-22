# 📜 मन्त्र-तालिका

> *mantra-tālika* — `mantra-talika` — (table storing canonical mantras in Bhūmi)

---

## 1. Nāma (Identity)

| Bhāṣā | Diacritic | ASCII | Bolī |
|-------|------------|--------|------|
| मन्त्र-तालिका | *mantra-tālika* | `mantra-talika` | table of conceptual units |

---

## 2. Uddeshya (Purpose)

The **mantra-tālika** is the **SQLite table** used by *Bhūmi* to persist the **canonical record** of every *mantra*.  
Each mantra represents a conceptual unit defined within some *śāstra* and described through the *nāma-catuṣṭaya* (Bhāṣā, Diacritic, ASCII, Bolī).

This table stores:
- the *four canonical names* (minus Bolī translations, which live in the mantra-boli-tālika),
- the **canonical Bhāṣā README** (formal explanation),
- URIs to its **yantra**, **anurāga**, and **chitra**,
- and provenance data such as creator gaṇa and creation time.

---

## 3. Siddhānta (Principle)

A mantra is not a file or string — it is a **conceptual locus of meaning**.  
The *mantra-tālika* is the field that anchors those loci inside Bhūmi’s persistence.

> **शास्त्र → मन्त्र → व्याख्या → रूपा**  
> *śāstra → mantra → vyākhyā → rūpā*  
> *(context → concept → explanation → form)*

Each record defines:
1. The *contextual identity* (which śāstra it belongs to),
2. The *names* by which it may be invoked,
3. The *canonical explanation* (README in Bhāṣā),
4. Pointers to its *yantra* (visual), *anurāga* (aural), and *chitra* (relational representation).

---

## 4. Rūpa (Canonical Folder Structure)

```
gananiti/bhumi/shashtra/mantra-talika/
├── README.md
├── README.en.md
├── yantra.svg         ← pictogram of idea anchored in structure
├── chitra.json        ← schema/relationship graph
└── anurag.ogg         ← sound motif of clarity / recognition
```

---

## 5. Schema Definition (SQLite)

```sql
CREATE TABLE mantra (
    shastra_id   TEXT NOT NULL,     -- śāstra namespace (scope)
    bhasha       TEXT NOT NULL,     -- canonical Sanskrit name (भाषा)
    diacritic    TEXT NOT NULL,     -- IAST transliteration
    ascii_name   TEXT NOT NULL,     -- code-safe name
    canonical_id TEXT NOT NULL,     -- full id: <shastra>/<ascii_name>
    readme_md    TEXT,              -- canonical README.md content (Bhāṣā)
    yantra_uri   TEXT,              -- URI for yantra.svg
    anurag_uri   TEXT,              -- URI for anurag.ogg
    chitra_uri   TEXT,              -- URI for chitra.json
    created_by   TEXT,              -- gaṇa who defined the mantra
    created_at   INTEGER NOT NULL,  -- timestamp of creation
    version      INTEGER DEFAULT 1, -- schema or semantic version
    metadata     TEXT,              -- operational JSON (optional)
    deleted      INTEGER DEFAULT 0, -- logical deletion flag
    PRIMARY KEY (shastra_id, ascii_name)
);
```

---

## 6. Relations

| Column | Refers to | Description |
|---------|-----------|-------------|
| `shastra_id` | [`shashtra-talika`](../shashtra-talika/README.md) | scope of the mantra |
| `created_by` | [`gana-talika`](../gana-talika/README.md) | creator gaṇa |
| `ascii_name` | local identity of the mantra within its śāstra |
| referenced by | [`mat-talika`](../mat-talika/README.md) | mats refer to mantras here |

---

## 7. Dharma (Invariants)

1. **Context-scoped identity:** uniqueness only within a śāstra.
2. **Canonical README:** Bhāṣā explanation lives here; translations live elsewhere.
3. **Externalized assets:** yantra/anurāga/chitra stored as URIs (content-addressed).
4. **Provenance:** every mantra knows who and when defined it.
5. **Append-only semantics:** edited mantras increment `version`; old ones are archived.

---

## 8. Example

```sql
INSERT INTO mantra (
  shastra_id, bhasha, diacritic, ascii_name, canonical_id,
  readme_md, yantra_uri, anurag_uri, chitra_uri,
  created_by, created_at
) VALUES (
  "gananiti/shashtra",
  "नामचतुष्टय",
  "nāma-catuṣṭaya",
  "nama_chatushtaya",
  "gananiti/shashtra/nama_chatushtaya",
  "# नामचतुष्टय\n\nFormal README content…",
  "ipfs://QmYantraCID",
  "ipfs://QmAnuragCID",
  "ipfs://QmChitraCID",
  "gan:amitu",
  1732140000
);
```

---

## 9. Antarmukhya (Inner Commentary)

Where *mat-tālika* records thought as expression,  
the *mantra-tālika* records the **concepts themselves** — the dictionary of awareness.  
It is Bhūmi’s index of meaning: compact, local, yet infinitely extensible.

---

## 10. Closing Śloka

> **मन्त्राणां तालिका ज्ञानस्य कोशः।**  
> *mantrāṇāṃ tālikā jñānasya kośaḥ* —  
> “The table of mantras is the treasury of knowledge.”

---

### 🔖 Summary

- **Mantra ID:** `gananiti/bhumi/shashtra/mantra-talika`
- **Meaning:** persistence surface for canonical mantras.
- **Essence:** structured index of ideas and their canonical forms.
- **Function:** written by matgaḍana when defining concepts; read by matdāna and other processes to interpret or communicate meaning.
