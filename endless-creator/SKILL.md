---
name: endless-creator
description: Meta-skill that creates custom endless-[name] music prompt skills from a user-supplied TARGET (artist, genre, era, or stylistic idea), following the proven chain used to build endless-jimmy and endless-hiro. Produces a grounding artifact describing the aesthetic in oblique musical terms (never naming the target if real), two ENH system prompts (full-song prose and live weighted-stub), a packaged .skill archive, and a GitHub README. Use whenever the user says "endless-creator", "make an endless skill for [X]", "create a music prompt skill for [X]", "build endless-[name] from [target]", "package this artist as a skill", "turn [X] into an endless skill", or supplies an artist/genre/era and wants a packaged skill back. Produces the full chain in one run — pre-verifies the SKILL.md description against the 1024-char limit and handles both the phantom-artist (jimmy/hiro/hardbass) and real-artist (overtures) patterns depending on the target.
---

# Endless Creator

Build a complete, packaged `endless-[name]` music prompt skill from a user-supplied TARGET, following the proven chain used to build `endless-jimmy` (phantom late-1960s psychedelic-blues-rock trio) and `endless-hiro` (phantom 2010s Tokyo cinematic hybrid-score composer). This is a **meta-skill**: its output is another installable skill.

The guiding idea is inherited from the whole `endless-*` family: **the title carries the fiction; the prompt carries the sound.** The target artist or genre is encoded as *musical vocabulary* — instrumentation, technique, production, affect — so the audio model generates work that evokes the tradition through internal musical evidence alone, without naming the real artist and without reproducing any specific protected expression.

## What you produce

Six to eight files in `/mnt/user-data/outputs/`, organized as:

1. **The grounding artifact** — `[slug]-without-saying-[slug]-grounding.md` — oblique musical description of the target aesthetic. The source of truth that everything else draws from.
2. **The full-song ENH prompt** — `No[Name]-ENH.md` — system prompt for an LLM acting as a full-song prose prompt enhancer.
3. **The live ENH prompt** — `No[Name]-Live-ENH.md` — system prompt for the live music model stub format (3–5 weighted stubs, 0.10–1.00 weights).
4. **The packaged skill folder** — `endless-[name]/` containing SKILL.md and references/.
5. **The packaged .skill archive** — `endless-[name].skill` — zip ready for the Save skill button.
6. **The GitHub README** — `README.md` — repo-ready, with family framing, installation, usage, hard rules, extending guidance, citation, and donate badge.

## Hard rules

These apply to every skill this meta-skill creates:

- **Pre-verify the SKILL.md description against the 1024-char limit** before writing the file, using a Python one-liner. If over, trim and re-measure until compliant with ≥3 chars of headroom.
- **For real-artist targets, never name the artist** in any generated file, nor the artist's bands, projects, aliases, collaborators, labels, song titles, or album titles. Translate forbidden references silently in all three enhancer-style outputs (grounding, ENH, live-ENH).
- **For genre or era targets without a specific artist**, naming the genre and the era is fine, but still refuse to echo any particular canonical track or artist name back when the user supplies one.
- **Match the output structure to the family** — the generated skill mirrors `endless-jimmy` and `endless-hiro` in shape: SKILL.md with a 7-step workflow, references/ holding the grounding + method + prompt-craft + example-album.
- **Package as a proper `.skill` zip** with nested folder structure (never flat).
- **Preserve the user's choice of skill name** — if they say "endless-foo", respect `foo`. If they don't propose one, suggest an evocative short name derived from the target.

## Workflow

### 1. Take the TARGET

The user supplies a TARGET: an artist name, a genre, an era, a scene, or an abstract stylistic idea. If none is given, ask what they want to build before doing anything. Clarify:

- Is this a specific real artist, a genre, or an abstract idea?
- Do they have a preferred skill name (`endless-[?]`)? If not, suggest one after the research phase.
- Are vocals allowed, textural-only, or instrumental-only? (Default decision based on the tradition — but confirm when ambiguous.)

### 2. Research the TARGET

Before writing anything, assess what you know about the target. Read `references/chain-workflow.md` for the full research protocol. Short version:

- If a famous artist with well-documented aesthetic → use Claude's knowledge; cross-check for key instrumentation, technique, production, era, affect.
- If a genre or scene → identify the canonical instrumentation palette, rhythmic feel, production conventions, and era anchor.
- If an abstract idea → ask the user 2–4 questions to anchor it: what era, what instrumentation feel, what mood, any sonic touchstones (described in musical terms, not by name).
- If knowledge seems thin, surface the gap to the user and offer two paths: (a) proceed with what you have and flag assumptions, or (b) have them supply key features.

**Produce a research summary** (internal, not output) covering: era anchor, core instrumentation, rhythmic feel, production stance, affective targets, canonical hard-blocks (forbidden names).

### 3. Design the register dial

Every endless-* skill has a two-poles-plus-blend dial. Pick two operational modes within the tradition and give each a thematically resonant single-word name. Guidance in `references/chain-workflow.md`:

- Hendrix (endless-jimmy): CATHEDRAL (introspective ballad) / STORM (loud blues-jam).
- Sawano (endless-hiro): VIGIL (piano-and-soprano lament) / CHARGE (full-stack action).

Pick names that evoke the two emotional/sonic registers of the target without echoing any canonical track or album title. State in the final SKILL.md.

### 4. Design the album arc

Define ten-track default arc appropriate to the tradition. The generic template (opener → single → first ballad → centerpiece → strange one → Side B opener → standard-shaped piece → heaviest → second ballad → closer) adapts to the ensemble:

- Band tradition → use arc shape close to endless-jimmy
- Composer/orchestral tradition → use arc shape close to endless-hiro
- Electronic producer → opener/anthem/breaker/beatless/peak/edit/vocal/breakdown/epic/outro
- DJ/mix tradition → intro mix / peak-time cuts / breakdown / closer

Choose and record the specific arc shape in the final SKILL.md.

### 5. Design the naming grammar

Define how the phantom artist, project aliases (if any), labels, and catalogue numbers are named. The grammar should feel period- and genre-plausible without echoing any real names. Guidance in `references/chain-workflow.md`.

### 6. Decide the vocal policy

Pick one:
- **Instrumental only** — Hendrix pattern. No vocals at all. Every prompt ends with "Instrumental only, no vocals."
- **Textural vocals only** — Sawano pattern. Pseudo-Latin, wordless, abstract non-semantic fragments. No coherent narrative lyrics.
- **Lyrical vocals permitted** — only if the tradition is centered on singing; constrain to invented lyrics never quoted/paraphrased from existing songs.

### 7. Author the grounding artifact

Follow `references/grounding-artifact-template.md`. The twelve-section structure is fixed; the content varies entirely by target. 300–500 lines of oblique musical description. Save to `/mnt/user-data/outputs/[slug]-without-saying-[slug]-grounding.md`.

### 8. Author the two ENH system prompts

Follow `references/enh-prompt-templates.md`. Both have fixed structural skeletons; content adapts to the tradition.

- `No[Name]-ENH.md` — full-song prose enhancer with the ten-part output structure.
- `No[Name]-Live-ENH.md` — live stub enhancer with 3–5 weighted stubs per call.

Save both to `/mnt/user-data/outputs/`.

### 9. Build the endless-[name] skill folder

Follow `references/skill-structure-template.md`. Pre-verify the SKILL.md description length with Python before writing it. Structure:

```
endless-[name]/
├── SKILL.md
└── references/
    ├── [slug]-without-saying-[slug]-grounding.md    (copy of step 7)
    ├── phantom-[format]-method.md                    (naming + catalogue + dial)
    ├── no[name]-prompt-craft.md                      (ten-part prose structure)
    └── example-album.md                              (worked example album)
```

The `example-album.md` contains an invented artist, a full composer/band card, and 3 fully-written prose prompts plus 7 spec-line stubs for the remaining tracks (the standard shape — a complete worked example without bloating the file).

### 10. Package into .skill archive

Use bash to zip the folder with nested structure preserved:

```bash
cd /mnt/user-data/outputs && zip -r endless-[name].skill endless-[name]/ -x "*.DS_Store" "*/__pycache__/*"
```

Verify the archive with `unzip -l` and confirm it's a valid zip.

### 11. Author the GitHub README

Follow `references/readme-template.md`. The README positions the skill as the primary deliverable, references the family of sibling skills, documents installation, usage, example, hard rules, extending/adapting, and includes the citation BibTeX + Ko-Fi badge. Save to `/mnt/user-data/outputs/README.md`.

### 12. Present everything

Call `present_files` with:
- The `.skill` archive (primary deliverable)
- The README
- The grounding artifact
- Both ENH prompts
- Optionally the SKILL.md for user review

Summarize the design decisions (register dial names chosen, vocal policy, album arc shape, naming grammar, description length) so the user sees the reasoning without having to read every file.

## Optional flourishes

Offer when they fit, or honor on request:

- **Variant pattern** — if the target is a classical composer, use the `endless-overtures` real-composer pattern instead of phantom-artist. State which pattern you chose and why.
- **Multiple register dials** — some traditions have three operational modes rather than two. Allow a three-pole dial (e.g. for traditions with ballad / mid / club modes).
- **Multi-album framing** — if the user wants, generate the first album plus a short note on how the composer's catalogue extends across adjacent eras.
- **Phantom-OST framing** — if the tradition is score-based, include optional phantom-OST framing in the composer card.
- **Alternative output model** — if the user wants Lyria 3.1 specifically (vs 3.5), adapt prompt lengths and style accordingly.

## Style reference

- `references/reference-examples.md` points to `endless-jimmy` (band tradition / instrumental-only / pre-1972 era) and `endless-hiro` (composer tradition / textural vocals / 2010s era) as the two canonical examples. Read it when you need to pick which existing skill to lean on for structural inspiration.
- Invent fresh everything for every run — never reuse names, titles, or prompts from existing skills in the family.
