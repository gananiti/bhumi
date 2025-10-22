# 📜 मन्त्र-बोली-तालिका
> *mantra-bolī-tālika* — `mantra-boli-talika` — (table storing translations and explanations of mantras in various Bolī)

---

## 1. Nāma (Identity)

| Bhāṣā | Diacritic | ASCII | Bolī |
|-------|------------|--------|------|
| मन्त्र-बोली-तालिका | *mantra-bolī-tālika* | `mantra-boli-talika` | table of mantra translations |

---

## 2. Uddeshya (Purpose)

The **mantra-bolī-tālika** stores **translations and local-language explanations (Bolī)**  
of canonical mantras recorded in the [`mantra-tālika`](../mantra-talika/README.md).

Each row represents one translation of a single mantra in a given language.  
It allows Bhūmi to serve multiple linguistic communities without conflating meaning and expression.

---

## 3. Siddhānta (Principle)

> **मन्त्रः अर्थः, बोली तस्य व्याख्या।**  
> *mantraḥ arthaḥ, bolī tasya vyākhyā* —  
> “The mantra is meaning; the Bolī is its explanation.”

Bolī tables separate **what something means** from **how it is said**,  
keeping canonical truth independent of linguistic surface.

---

## 4. Schema Definition (SQLite)

```sql
CREATE TABLE mantra_boli (
    shastra_id     TEXT    NOT NULL,   -- parent śāstra
    ascii_name     TEXT    NOT NULL,   -- mantra ascii id
    lang           TEXT    NOT NULL,   -- ISO language code (e.g. 'en', 'hi')
    boli_name      TEXT,               -- short name in this language
    readme_md      TEXT,               -- translated README.md content
    translated_by  TEXT,               -- gaṇa or person who provided translation
    translated_at  INTEGER,            -- timestamp
    notes          TEXT,               -- optional translator notes
    PRIMARY KEY (shastra_id, ascii_name, lang),
    FOREIGN KEY (shastra_id, ascii_name)
      REFERENCES mantra(shastra_id, ascii_name)
);
```

---

## 5. Relations

| Column | Refers to | Description |
|---------|-----------|-------------|
| `shastra_id`, `ascii_name` | [`mantra-talika`](../mantra-talika/README.md) | identifies canonical mantra |
| `translated_by` | [`gana-talika`](../gana-talika/README.md) | translator gaṇa |
| referenced by | translation interfaces, localization utilities | for displaying localized text |

---

## 6. Dharma (Invariants)

1. **One row per language per mantra.**
2. **Canonical reference required:** every Bolī must link to an existing mantra.
3. **Readme parity:** translated README aims for semantic, not literal, fidelity.
4. **Explicit authorship:** all translations record the translator gaṇa.
5. **Immutable provenance:** once published, translation text revisions increment external version or new row.

---

## 7. Example

```sql
INSERT INTO mantra_boli (
  shastra_id, ascii_name, lang, boli_name, readme_md,
  translated_by, translated_at
) VALUES (
  "gananiti/shashtra",
  "nama_chatushtaya",
  "en",
  "fourfold name",
  "# Fourfold Name\n\nExplanation in English…",
  "gan:translator1",
  1732141000
);
```

---

## 8. Antarmukhya (Inner Commentary)

Bolī records are **bridges** — they carry meaning from Sanskrit Bhāṣā to every other linguistic consciousness.  
They are part of Bhūmi’s cultural matgaḍana: translating is itself a creative mat.

By keeping Bolī entries separate, Bhūmi allows every community to build its own linguistic mirrors without rewriting the source idea.

---

## 9. Closing Śloka

> **बोलीभिः मन्त्राः सर्वेभ्यः प्राप्यन्ते।**  
> *bolībhiḥ mantrāḥ sarvebhyaḥ prāpyante.* —  
> “Through Bolī, the mantras become accessible to all.”

---

### 🔖 Summary

- **Mantra ID:** `gananiti/bhumi/shashtra/mantra-boli-talika`
- **Meaning:** table storing translations (Bolī) of canonical mantras.
- **Essence:** linguistic mirrors of canonical concepts.
- **Function:** provides multilingual access to the knowledge encoded in mantras; written by translator gaṇas, read by every user interface and matdāna process.

---
