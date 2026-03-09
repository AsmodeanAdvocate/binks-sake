# 🎵 binks-sake

> *"Sing it to the winds, sing it to the seas — the song belongs to everyone."*

Public card database for the One Piece TCG Analytical System.  
Built by [AsmodeanAdvocate](https://github.com/AsmodeanAdvocate) | March 2026

---

## What's In Here

| File | Description |
|------|-------------|
| `optcg_cards_combined.json` | Full card database — 2297 cards, OP01–OP14, EB01–EB04, ST01–ST29 |
| `optcg_schema_and_decklist.json` | Schema definition + active Blue/Purple Sanji decklist |

---

## Schema Version: 1.1.0

Every card record follows the schema defined in `optcg_schema_and_decklist.json`.  
Key fields: `id`, `name`, `card_category`, `color[]`, `type[]`, `attribute[]`, `cost`, `power`, `life`, `counter_value`, `effect_text`, `effect_parsed`, `card_versions[]`, `data_status`, `data_sources[]`

### Verification Levels
| Status | Meaning |
|--------|---------|
| `L2_pulled` | From 1 source, not yet cross-referenced |
| `L3_verified` | Confirmed by 2+ sources with no content conflicts |
| `flagged` | Sources disagree — needs QC review |

### Source Hierarchy (highest to lowest authority)
1. `en.onepiece-cardgame.com` — Official Bandai site, ground truth
2. `github:buhbbl/punk-records` — Built from official site via vegapull
3. `onepiece.limitlesstcg.com` — Well-maintained, usually current
4. `optcgapi.com` — Bulk data, may lag errata
5. Manual pull — Single source, lowest confidence

---

## Current Dataset Status
- **Total cards:** 2297
- **L3 Verified:** 118
- **Flagged:** 231
- **Missing:** OP15 (English April 3, 2026)
- **Sources used:** optcgapi.com, onepiece.limitlesstcg.com

---

## Important Rules
- All decks are exactly **50 cards**. This is a hard OPTCG rule.
- The `counter_value` field on Characters is the printed counter symbol — distinct from `effect_parsed.counter` on Events.
- `life` field only exists on Leader cards. `cost` does NOT exist on Leaders.
- Errata history is tracked in `card_versions[]` — every version with effective dates.

---

## For Claude Sessions
Paste the contents of `optcg_system_state.json` from [thousand-sunny](https://github.com/AsmodeanAdvocate/thousand-sunny) at the start of any session to brief Claude on current project status.

---

*Card data is copyright ©Eiichiro Oda/Shueisha, Toei Animation, Bandai Namco Entertainment Inc.*  
*This repository contains structured data derived from public sources for personal analytical use.*
