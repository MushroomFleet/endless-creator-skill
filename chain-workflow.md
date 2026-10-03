# Chain Workflow

The step-by-step orchestration guide for building a new `endless-[name]` skill. Read this file every run.

The core move: **take a TARGET (artist, genre, era, or idea), research it against the oblique-musical-description framework, make six design decisions, and author seven files in order.** The design decisions precede authoring — never start writing without them.

---

## Research protocol

Before any writing, assess the target.

### If the TARGET is a specific real artist

1. **Check Claude's knowledge** — do you know this artist's:
   - Era / active decades
   - Core instrumentation / production tools
   - Signature techniques (performance, production, writing)
   - Famous collaborators / project aliases / bands
   - Representative tracks (for forbidden-names list only — never cite in output)
   - Lyrical content tendencies / vocal policy
   - Affective territory (what moods they occupy)

2. **If knowledge is confident on all seven**, proceed to design.

3. **If knowledge is thin or uncertain on two or more**, surface the gap:
   > "I have a working picture of [TARGET]'s [known areas], but I'm less sure about [uncertain areas]. Two paths — I can proceed with assumptions I'll flag in the grounding, or you can give me a few sentences on each. Which?"

4. **Build the forbidden-names list** — every proper noun that must never appear in any output file. For a real artist this typically includes: artist's name, all aliases, all project names, all band names, all major collaborators, 10–20 most famous track titles, 5–10 most famous album titles, 3–5 most famous associated franchises or events.

### If the TARGET is a genre, scene, or era

Naming the genre and era is fine. Research:

1. **Instrumentation palette** — what's canonical in this scene.
2. **Tempo and rhythmic feel** — standard BPM range, pocket, swing/straight.
3. **Production conventions** — recording / mixing / mastering stance.
4. **Vocal treatment** — if any.
5. **Era anchor** — when did the scene peak; what era does the model target.
6. **Scene vocabulary** — slang, pedal names, DAW traditions, label types.
7. **Avoid-list** — adjacent genres that this one specifically isn't.

### If the TARGET is an abstract idea

Ask 2–4 clarifying questions before proceeding:

1. "What era does this sit in?"
2. "Lean electronic, acoustic, hybrid, or orchestral?"
3. "What mood is dominant?"
4. "Any sonic touchstones you can describe in musical terms (not by artist name)?"

Translate the user's answers into a working stylistic territory, then follow the genre-research protocol above.

---

## The six design decisions

Make these before writing anything. Record them in the research summary; they drive every subsequent file.

### Decision 1 — The skill name

`endless-[name]` where `[name]` is a short evocative word. Guidance:

- For a real artist, the name is usually a nickname, wink, or truncation of their actual name (jimmy for Hendrix, hiro for Sawano).
- For a genre, use the genre name directly (hardbass for hardbass).
- For an era or scene, use a short period-evocative word.
- Avoid: the artist's actual full name; the full genre name if it's multi-word; anything that would read as a real track or album title.

If the user has proposed a name, use it. If not, suggest 2–3 options and let them pick.

### Decision 2 — The register dial

Two operational poles plus a BLEND default. Name each pole with a single evocative word that:

- Doesn't echo a canonical track, album, or project title in the target's catalogue.
- Resonates with the sonic/emotional center of that mode.
- Pairs well with the other pole (opposites or complements).

**Reference pairings:**
- Hendrix: CATHEDRAL (introspective ballad) / STORM (loud blues-jam).
- Sawano: VIGIL (piano-and-soprano lament) / CHARGE (full-stack action).
- Hardbass: DVOR (courtyard raw) / PODVAL (basement polish) / SMESH (blend).

**For your target**, think about the two most distinct sonic/emotional modes the artist/genre operates in. For a dub artist: ECHO (deep spacious) / RIDDIM (dense percussive). For a shoegaze artist: HAZE (wall-of-sound submerged) / SPIKE (bright piercing peak). Invent what fits.

### Decision 3 — The album arc

Ten-track default arc. Adapt the generic template to the tradition:

- **Band tradition** (rock, jazz quartet, folk ensemble): opener → single → first ballad → centerpiece jam → strange one → Side B opener → standard-shape → heaviest → second ballad → closer.
- **Composer tradition** (orchestral, film score, hybrid-score): main theme opener → signature cue → piano meditation → vocal feature → ostinato engine → lament → genre-hybrid → reprise variation → two-peak centerpiece → denouement.
- **Electronic producer** (techno, house, dubstep, ambient): opener → anthem → beatless → peak → edit → vocal collab → breakdown → epic → remix → outro.
- **DJ/mix tradition**: intro mix → first drop → vocal track → peak-time cut → breakdown → second drop → interlude → extended cut → cool-down → closer.
- **Rapper/MC tradition**: opener skit → first banger → feature track → introspective → club cut → political → romantic → collab → emotional peak → closer.

Record which arc you chose and your justification in the SKILL.md workflow.

### Decision 4 — The naming grammar

Define naming conventions for:

- **Phantom artist name** — format options, era-plausibility rules, what to avoid.
- **Project aliases** — if the tradition uses them (brackets, slashes, phonetic transliteration, numeric stylizations).
- **Album titles** — common title shapes in the tradition.
- **Track titles** — stylistic patterns, length range, language mix.
- **Phantom label** — label name shape, prefix format, era.
- **Catalogue number** — prefix + number format, impossibly-high range.
- **Release year** — the window in which the alternate-timeline albums appear.

### Decision 5 — The vocal policy

Pick one:
- **Instrumental only** (Hendrix pattern) — vocals forbidden entirely.
- **Textural only** (Sawano pattern) — pseudo-Latin, wordless, abstract fragments only; no coherent lyrics.
- **Lyrical permitted** — only if the tradition is centered on singing. Invented lyrics only; never quote or paraphrase existing songs. Constrain thematic territory to avoid obvious signature-song echoes.

### Decision 6 — The prompt word-count target

Varies by ensemble density:
- Small ensemble / trio / solo acoustic: **180–320 words** per prompt (Hendrix target).
- Full band / electronic producer: **200–320 words**.
- Hybrid orchestral stack / symphony: **220–340 words** (Sawano target).
- Big-band jazz / cinematic trailer / wall-of-sound: **240–360 words**.

Record in `no[name]-prompt-craft.md` and enforce in the ENH prompt.

---

## The seven files, in order

Build in this strict order — later files reference earlier ones.

### File 1: `[slug]-without-saying-[slug]-grounding.md`

The grounding artifact. See `grounding-artifact-template.md`. 300–500 lines. Save to `/mnt/user-data/outputs/`.

### File 2: `No[Name]-ENH.md`

Full-song prose enhancer. See `enh-prompt-templates.md`. ~150–200 lines. Save to `/mnt/user-data/outputs/`.

### File 3: `No[Name]-Live-ENH.md`

Live weighted-stub enhancer. See `enh-prompt-templates.md`. ~180–220 lines. Save to `/mnt/user-data/outputs/`.

### File 4: `endless-[name]/SKILL.md`

The main skill file. See `skill-structure-template.md`. **Pre-verify description length with Python before writing.** ~90–110 lines. Save to `/mnt/user-data/outputs/endless-[name]/`.

### Files 5a–5d: `endless-[name]/references/`

Four files:
- `[slug]-without-saying-[slug]-grounding.md` (copy of File 1).
- `phantom-[format]-method.md` (naming + catalogue + register dial detail).
- `no[name]-prompt-craft.md` (ten-part prose structure).
- `example-album.md` (worked example album — artist card + 3 full prose prompts + 7 spec stubs).

### File 6: `endless-[name].skill`

Packaged archive. Use bash:
```bash
cd /mnt/user-data/outputs && zip -r endless-[name].skill endless-[name]/ -x "*.DS_Store" "*/__pycache__/*"
```
Verify with `unzip -l` and confirm valid zip with `file`.

### File 7: `README.md`

GitHub repo README. See `readme-template.md`. ~160–200 lines. Save to `/mnt/user-data/outputs/`.

---

## Pre-flight checklist before packaging

Before running the zip command:

1. ✅ SKILL.md description measured under 1024 chars with ≥3-char headroom.
2. ✅ All four reference files present in `endless-[name]/references/`.
3. ✅ Grounding artifact copied into references (not just original location).
4. ✅ No forbidden names appear in any file (grep check).
5. ✅ Register dial names consistent across SKILL.md, phantom-method, prompt-craft, example-album.
6. ✅ Vocal policy consistent across all files.
7. ✅ Album arc shape consistent across SKILL.md and example-album.
8. ✅ Word-count target consistent across ENH prompt, prompt-craft, example-album.

---

## Post-flight checklist before presenting

Before calling `present_files`:

1. ✅ `.skill` archive built and verified as valid zip.
2. ✅ `.skill` archive contains the nested folder structure (not flat).
3. ✅ README references the correct new repo URL (ask user or use a placeholder).
4. ✅ All seven files saved to `/mnt/user-data/outputs/`.
5. ✅ Design summary ready to present inline.

Present with `present_files` using the `.skill` archive first, then README, then grounding, then both ENH files. Summarize the six design decisions.
