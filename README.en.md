# Panda Zhuyin — Taiwanese (Taigi) Lexicon in Taiwanese Phonetic Symbols

Derived lexicon data from **Panda Zhuyin**, an iOS bopomofo keyboard: ~109K (word, reading) entries with frequencies, ~11K single-character reading frequencies, and ~104K Tâi-lô / Pe̍h-ōe-jī romanization mappings, all in **Taiwanese Phonetic Symbols** (方音符號, the extended bopomofo used for Taiwanese Hokkien). The format is [McBopomofo](https://github.com/openvanilla/McBopomofo)-compatible — it can be fed directly into McBopomofo / Megrez / [Homa](https://github.com/vChewing/vChewing-LibVanguard)-family composers as a language model. If you are building a Taigi input method (Android, iOS, Rime, desktop), this data is ready to use.

> **Licensing is per-file** — see the table below. GitHub's repo-level CC BY-SA 4.0 badge is a single-field platform convention; `emoji-annotations-taigi.txt` is actually CC0 + LGPL-3.0 lineage with no BY-SA obligation.

## Files & licenses

| File | Content | License |
|---|---|---|
| `phrases-taigi.txt` | Lexicon: `word freq syllable…` (space-separated) | **CC BY-SA 4.0** |
| `char-taigi.txt` | Single-character readings: `char ⇥ 0 ⇥ freq ⇥ reading` (the constant `0` is a McBopomofo placeholder column) | **CC BY-SA 4.0** |
| `lexicon-taigi-romanization.txt` | `word ⇥ phonetic ⇥ Tâi-lô ⇥ POJ` | **CC BY-SA 4.0** |
| `emoji-annotations-taigi.txt` | Taigi word → emoji | Mixed: words from iTaigi (**CC0**), emoji mapping derived from [rime-emoji](https://github.com/rime/rime-emoji) (**LGPL-3.0**, full text in `LICENSES/`) |

Lines starting with `#` are comments. Reusing the three BY-SA files requires **attribution** and releasing your derivative lexicon under the **same license** (doing what this repo does is sufficient). A copy-paste attribution template is in the Chinese README (再利用標示範本).

## Tone mark encoding

Compare by Unicode code point, not by glyph:

| Tone | Mark | Unicode |
|---|---|---|
| 1 (im-piânn) | none | — |
| 2 | `ˋ` | U+02CB |
| 3 | `˪` | U+02EA |
| 4 | bare entering-tone coda (ㆴㆵㆻㆷ) | — |
| 5 | `ˊ` | U+02CA |
| 7 | `˫` | U+02EB |
| 8 | coda + combining dot above | U+0307 |
| neutral | base + `˙` (or U+0307 on entering codas) | U+02D9 |

The `-k` coda always uses **ㆻ** (U+31BB). Nasalized and voiced symbols use the Bopomofo Extended block (U+31A0–U+31BF). All readings passed a legal-syllable whitelist based on the Ministry of Education phonetic system.

## Sources

Merged from seven sources — ChhoeTaigi 台華線頂對照典 & 台灣植物名彙 1928 (CC BY-SA 4.0), [iTaigi](https://itaigi.tw/) (CC0), [MoE Taiwanese dictionary](https://sutian.moe.edu.tw/) (CC BY-ND 3.0 TW, verbatim reproduction), PTS Taigi neologisms (CC BY 4.0), MoE academic terminology (Taiwan OGDL, CC BY-equivalent), with real-corpus frequencies from [iCorpus](https://github.com/Taiwanese-Corpus/icorpus_ke5_han3-ji7) © Sih Sing-hông (CC BY 4.0). Full per-source details, frequency formula, and modification statement: see [README.md](./README.md) (Chinese).

## Versioning & feedback

Git tags mirror App Store releases (tag `v2.5.0` = the lexicon shipped in app 2.5.0); CI syncs on every release. Found a wrong reading? Open an [issue](../../issues) — but please don't send PRs against the data files: they are overwritten wholesale by CI on the next release.
