# Grounding Artifact Template

How to author the grounding artifact — the source-of-truth document that encodes the target aesthetic in oblique musical terms. Read this file every run.

The core move: **describe the sound through internal musical evidence — instrumentation, technique, structure, production, affect — not through proper nouns.** The result is a 300–500-line document that a generation model (and any downstream enhancer prompt) can rely on without needing to know who or what the tradition is "about."

Filename: `[slug]-without-saying-[slug]-grounding.md`, where `[slug]` is the TARGET expressed in a word or two. Examples: `hendrix-without-saying-hendrix-grounding.md`, `hiro-without-saying-hiro-grounding.md`, `burial-without-saying-burial-grounding.md`.

---

## The twelve sections (in order)

Every grounding artifact must contain these twelve sections, in this order. Section lengths vary by target but the shape is fixed.

### 1. Purpose

One opening paragraph identifying the document as a generation-time grounding prompt for music generation models. Second paragraph stating the hard rule: the model never outputs the proper noun this document is shaped around (for real-artist targets) or any specific signature tracks (for genre/era targets).

Target length: ~2 paragraphs.

### 2. Core Aesthetic Stance

One or two paragraphs capturing the *paradoxical sensibility* at the heart of the tradition. Reach for the tensions:
- Hendrix: "rough but courtly, loud but intimate, masculine but unguarded, virtuosic but lazy-pocketed"
- Sawano: "operatic but modern, metallic but tender, enormous but intimate, globally allusive but unmistakably Japanese"

Every strong tradition has a core tension. Find it; name it.

Target length: ~1–2 paragraphs.

### 3. Genre Coordinates (without naming the artist)

Triangulation inside 3–5 adjacent musical territories. Each bullet should pin the tradition in relation to a nearby tradition the model does know.

Close with a line listing the user-request keywords that would imply this grounding ("If a user mentions 'X,' 'Y,' or 'Z,' this grounding likely applies").

Target length: 5–8 bullets + closing line.

### 4. Instrumentation

The longest section usually. Document every instrument / sound-source / production tool in play. For complex ensembles, use subsections (tiers, groups, ensembles). For each instrument, specify:

- What model/era/type it is (where distinctive).
- How it's typically played/used in this tradition.
- Processing applied (pedals, effects, treatments).
- Its role in the ensemble (lead, texture, rhythm, climax, etc.).

For traditions with large instrumentation (orchestra + rock + choir + electronic), use the **tier model** from Sawano's grounding. For traditions with small instrumentation (trio, duo, solo), use flat sections.

Target length: 60–150 lines depending on ensemble complexity.

### 5. Compositional / Structural Architecture

How pieces are built. Document:

- **Form shapes** — typical song/piece structures (verse-chorus, through-composed, crescendo arc, loop-and-vary, suite form).
- **Motivic development** — small cells → how they're reused/varied (reharmonization, register shift, mode change, augmentation).
- **Length conventions** — typical duration ranges.
- **Narrative arc** — where the peak sits, how the ending is handled.

Target length: 30–60 lines.

### 6. Harmonic / Melodic Language

What the pitch content is doing. Document:

- Scale/mode preferences — pentatonic? Mixolydian? Modal mixture? Atonal?
- Key tendencies — minor vs major, specific keys that recur.
- Chord vocabulary — triads, sevenths, extensions, cluster chords, suspensions.
- Resolution habits — where phrases land (root, 13th, suspended, Picardy).
- Note choice grammar — what makes a solo "sound like this tradition."

Target length: 20–40 lines.

### 7. Vocal / Choral Treatment

**Only include if the tradition has vocals.** For instrumental-only traditions, replace with "This tradition is instrumental; vocal elements are not part of its grammar."

If vocals are present:
- Register and projection style.
- Lyrical approach (narrative, textural, abstract, pseudo-language).
- Language choice.
- Role in the ensemble (lead, texture, counterpoint).
- Rules about lyric content (fully invented, no quotation/paraphrase).

Target length: 15–40 lines when applicable.

### 8. Rhythmic Palette

The time-feel of the tradition. Document:

- Tempo bands for different piece types.
- Pocket (laid-back / on top / pushed).
- Straight vs swing / shuffle.
- Characteristic rhythmic cells (dotted-eighth-sixteenth, four-on-the-floor, hemiola).
- Drum kit vs orchestral percussion vs electronic percussion handling.
- What rhythmic conventions this tradition specifically rejects.

Target length: 20–40 lines.

### 9. Production and Mix Aesthetic

How the recording sounds. Document:

- Era-specific production stance (analog tape, digital, hybrid).
- Stereo image (narrow, wide, hyper-wide, unstable).
- Dynamic range handling.
- Reverb conventions (what kind, where, how much).
- EQ/frequency balance (bright, dark, scooped, tubby).
- Modern mastering conventions (loudness, compression stance).

Target length: 30–60 lines.

### 10. Song-Form Conventions

Specific structural templates. Document 3–6 common piece types in this tradition. For each:
- Opening gesture.
- Build-up pattern.
- Climax placement.
- Ending type.
- Duration range.

This section partially overlaps with section 5 but is more concrete — it gives the model templates to populate.

Target length: 30–50 lines.

### 11. Affective Targets

Ordered list of 4–7 emotional registers this tradition occupies, with the dominant mood first. Each with a short description. Close with a short "Avoid" clause naming moods the tradition specifically never occupies.

Target length: 15–30 lines.

### 12. Things to Explicitly Avoid

Bullet list of hard-blocks. Include:

- Adjacent-genre conventions this tradition specifically rejects.
- Post-era or pre-era production gestures that would date the output wrongly.
- Instrumentation that would read as a different tradition.
- Modern/dated gestures that don't belong.
- Direct quotation of signature techniques/phrases (where applicable).
- For real-artist targets: artist name, aliases, collaborator names, project names, franchise names, specific track titles, specific album titles.

Target length: 10–25 bullets.

---

## The two closing sections

### Compact system-prompt version

A single dense paragraph (150–250 words) that captures the whole grounding, suitable for passing in token-constrained calls. This is a condensed restatement, not a summary — it should contain enough technical specificity to actually generate the sound.

### Notes for the generating model

A short closing section (1–3 paragraphs) that:
- Instructs the model to describe the sound in musical terms if asked whose style it's evoking, rather than naming anyone.
- Explains the copyright-safe design intent.
- States the refusal behavior for direct-copy requests.
- States the vocal policy (if applicable).

---

## Style and tone of the grounding artifact

- **Written for Claude and the audio model to read.** Dense, technical, declarative. No hedging. No apologies.
- **Oblique about the target.** The target is never named directly. For real artists, the whole document carefully avoids the name while describing exactly their style. For genres, the genre is named but canonical artists in it are not.
- **Specific not generic.** "A Stratocaster-style single-coil guitar through a cranked tube amp" is useful. "An electric guitar" is not.
- **Technical vocabulary.** Pedals by type (germanium fuzz, rocker-controlled treble filter), techniques by name (unison bends, behind-the-nut pulls), production stance by specifics (10 kHz roll-off, 30 Hz sub-bass extension).
- **Markdown structure.** H2 for section headings, bullets or prose as the content suggests, horizontal rules between major parts.

---

## Reference examples

The two canonical examples in the output folder (or project context):

- **`hendrix-without-saying-hendrix-grounding.md`** — band tradition, instrumental-only, pre-1972 analog production. ~145 lines total. Uses flat sections (no instrumentation tier model).
- **`hiro-without-saying-hiro-grounding.md`** — composer tradition, textural vocals, 2010s modern production. ~198 lines total. Uses the four-tier instrumentation stack.

Read whichever is structurally closer to your target before authoring your own.

---

## Sanity check before finalizing

1. ✅ All twelve sections present, in order.
2. ✅ Core aesthetic stance states a real tension.
3. ✅ Instrumentation section covers every sound-source in the tradition.
4. ✅ Section 7 is present if vocals exist, or replaced with the instrumental-only note.
5. ✅ Avoid-list in section 12 includes every forbidden name identified in the research phase.
6. ✅ Compact system-prompt version contains enough technical specificity to generate the sound.
7. ✅ No proper nouns from the target's canon appear anywhere in the document (grep check against the forbidden-names list).
8. ✅ Era anchor is stated and consistent across the document.

If yes to all eight, the grounding is ready to drive the downstream files.
