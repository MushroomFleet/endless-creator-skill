# Skill Structure Template

How to author the `endless-[name]/` skill folder and its four reference files, and how to package into `.skill`. Read this file every run.

The core move: **mirror the shape of `endless-jimmy` and `endless-hiro` exactly** — same folder layout, same SKILL.md section order, same four reference files. The content varies entirely by target; the structure is fixed.

---

## Folder structure

```
endless-[name]/
├── SKILL.md
└── references/
    ├── [slug]-without-saying-[slug]-grounding.md    (copy of File 1 from chain-workflow)
    ├── phantom-[format]-method.md                    (naming, catalogue, register dial)
    ├── no[name]-prompt-craft.md                      (ten-part prose structure)
    └── example-album.md                              (worked example)
```

`[name]` matches the skill name. `[slug]` is the oblique-reference word used in the grounding filename (e.g. `hendrix`, `hiro`). `[format]` describes the artist/ensemble format — `trio`, `composer`, `producer`, `ensemble`, `band`, `quartet` — whichever fits.

---

## SKILL.md

### Frontmatter

```yaml
---
name: endless-[name]
description: [DESCRIPTION — pre-verified under 1024 chars with ≥3-char headroom]
---
```

**Pre-verify description length before writing.** Use this Python one-liner:

```python
python3 -c "
d = '''[paste draft description here]'''
print(f'Length: {len(d)} chars (limit 1024, headroom {1024 - len(d)})')
"
```

If over, trim and re-measure. If under with ≥3-char headroom, proceed.

### Body structure (fixed sections, in order)

1. **Title line**: `# Endless [Name]`
2. **One-paragraph summary** of what the skill does — invent phantom [artist type] + write ten-track album as Gemini music generation prompts, from one user-supplied IDEA.
3. **The guiding idea paragraph** — restate "the title carries the fiction; the prompt carries the sound." Explain the family lineage.
4. **"What you produce" section** — one paragraph on the single output artifact (markdown file in `/mnt/user-data/outputs/`).
5. **"Hard rules" section** — bulleted list of the enforced constraints. Must include at minimum:
   - Never name [forbidden category].
   - Never reproduce signature [licks/motifs/beats].
   - Vocal policy (per Decision 5).
   - Era-lock.
   - Never borrow real [artists/labels/tracks].
6. **"Workflow" section** — the 7-step workflow:
   1. **Take the IDEA** — prompt the user if not given.
   2. **Set the register dial** — pick VIGIL/CHARGE-style poles.
   3. **Invent the artist and catalogue** — follow `phantom-[format]-method.md`.
   4. **Load the sound and craft** — read all three reference files.
   5. **Shape the ten tracks** — follow the album arc.
   6. **Write each entry** — follow the per-track entry format.
   7. **Assemble and name the file** — save to `/mnt/user-data/outputs/[artist-slug]-[album-slug]-no[name]-lyria-prompts.md`.
7. **"Optional flourishes" section** — bulleted list of offer-when-fit variations (phantom OST, themed album, discography extension, variant-pole album).
8. **"Style reference" section** — one paragraph pointing at `references/example-album.md` as the standard.

### Length target

90–110 lines total. Section headings and bullets, prose where it adds value, no filler.

---

## references/[slug]-without-saying-[slug]-grounding.md

An exact copy of File 1 from the chain-workflow (the grounding artifact in `/mnt/user-data/outputs/`). Copy with bash:

```bash
cp /mnt/user-data/outputs/[slug]-without-saying-[slug]-grounding.md /mnt/user-data/outputs/endless-[name]/references/
```

This file is the self-contained aesthetic source of truth inside the skill.

---

## references/phantom-[format]-method.md

How to invent the artist, label, album, and catalogue. Read `phantom-method-structure` section below. Mirrors `phantom-trio-method.md` from endless-jimmy or `phantom-composer-method.md` from endless-hiro.

### Section structure (fixed, in order)

1. **One-paragraph intro** — "the core move" statement for inventing the phantom artist.
2. **The register dial** — VIGIL/CHARGE-style pole description, with:
   - **Pole A** — full description, sonic center, affective targets.
   - **Pole B** — full description, sonic center, affective targets.
   - **BLEND** — the default allocation (5+5 or 6+4 per ten tracks).
   - **Choosing** — rules for inferring the register from the IDEA.
3. **Naming the artist** — format options, period-plausibility rules, what to avoid.
4. **Naming the album** — title shapes, length range, era-feel.
5. **Naming the tracks** — ten tracks, variety across types.
6. **The phantom label** — name shapes, era-feel.
7. **The catalogue conceit** — prefix format, number range, release year window.
8. **Optional flourishes** — phantom OST framing, phantom vocalist, provenance line (where applicable).
9. **Sanity check** — numbered checklist before moving to tracks.

### Length target

150–200 lines. The register dial section is usually the longest.

---

## references/no[name]-prompt-craft.md

How to write each prose prompt. Read `prompt-craft-structure` section below. Mirrors `nohendrix-prompt-craft.md` or `nohiro-prompt-craft.md`.

### Section structure (fixed, in order)

1. **One-paragraph intro** — "the core move" statement for one dense prose prompt per track.
2. **The ten-part structure** — numbered list of the ten prompt sections (same as in `No[Name]-ENH.md` section 4), each with 1–2 sentences of guidance. Close with the word-count target from Decision 6.
3. **Style and tone of each prompt** — bulleted list.
4. **Silent translation** — rules for translating forbidden references, informal language, incompatible requests.
5. **Per-track entry format** — the exact markdown shape:
   ```
   ### N. Track Title
   > One-line program note.
   **BPM · Key · Register · Length**
   ```prompt
   [prose prompt]
   ```
   ```
6. **Variety rules across the ten tracks** — bulleted list of what to deliberately vary (tempo, key, length, solo length, pedal emphasis, tier allocation).
7. **Sanity check before finalizing each prompt** — numbered checklist.

### Length target

100–130 lines.

---

## references/example-album.md

The worked example — the gold-standard reference. One complete album with full composer/band card, three fully-written prose prompts, and seven spec-line stubs for the remaining tracks.

### Section structure (fixed, in order)

1. **Introductory note** — "A complete worked example — the standard for tone, density, and prompt quality. This is a reference, not a template to reuse."
2. **Album title header** (`# [Artist Name] — *[Album Title]*`)
3. **Concept paragraph** — alternate-timeline framing for this invented artist and album.
4. **Composer/band card** — all the fields from the phantom-method file populated for this example.
5. **"How this catalogue works" section** — three bullets explaining the artifact format.
6. **Tracklist header** (`## Tracklist`)
7. **Three fully-written tracks** — entries 1, 2, and 3, each with full prose prompts matching the word-count target.
8. **"Remaining tracks (spec lines only)" section** — tracks 4–10 as one-line specs plus bracketed prose-prompt sketch. Each has:
   - H3 heading with track number and title.
   - Blockquote program note.
   - Bold spec line.
   - Bracketed prose-prompt sketch summarizing what the full prompt would contain.
9. **"Author your own" section** — naming grammar summary, prompt skeleton, register cheat-sheet.

### Length target

110–130 lines. The three full prompts are the densest parts.

---

## Packaging into .skill

Once all four reference files exist and SKILL.md is written and verified:

```bash
cd /mnt/user-data/outputs && zip -r endless-[name].skill endless-[name]/ -x "*.DS_Store" "*/__pycache__/*"
```

Verify:

```bash
unzip -l endless-[name].skill
file endless-[name].skill
```

Expected result:
- Archive is a valid zip.
- Nested folder structure is preserved (not flat).
- Six entries total — the top-level folder, SKILL.md, the references subfolder, and the four reference files.

If the archive is flat (SKILL.md at the root alongside references/), re-run the zip from the correct working directory.

---

## Sanity check before packaging

1. ✅ SKILL.md description pre-verified under 1024 chars with ≥3-char headroom.
2. ✅ All four reference files exist in `endless-[name]/references/`.
3. ✅ Grounding artifact copied into references (not just original location).
4. ✅ Register dial names (VIGIL/CHARGE-style) consistent across SKILL.md, phantom-method, prompt-craft, example-album.
5. ✅ Vocal policy consistent across all files.
6. ✅ Album arc shape consistent across SKILL.md and example-album.
7. ✅ Word-count target consistent across ENH prompt, prompt-craft, example-album.
8. ✅ No forbidden names appear in any file.

If all pass, proceed to packaging.
