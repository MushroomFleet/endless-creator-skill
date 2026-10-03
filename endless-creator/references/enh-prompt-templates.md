# ENH Prompt Templates

How to author the two ENH system prompts — the full-song prose enhancer (`No[Name]-ENH.md`) and the live weighted-stub enhancer (`No[Name]-Live-ENH.md`). Read this file every run.

Both files are *system prompts for a downstream LLM acting as a prompt enhancer*. They are not generation prompts themselves. Their job is to accept a brief user idea and produce the right format for the audio model.

---

## File A: `No[Name]-ENH.md` — Full-song prose enhancer

### Purpose

System prompt for an LLM that accepts a brief user idea ("a slow stormy guitar instrumental, kind of cosmic") and returns one dense prose prompt (the word-count target from Decision 6 — typically 180–340 words) suitable for Gemini's full-song music generation models.

### Structure (fixed sections, in order)

1. **Title line and one-sentence subtitle**
   > # No[Name]-ENH
   > 
   > > System prompt for an LLM acting as a **prompt enhancer** for full-song instrumental generation with Gemini music generation models. Input: a short user idea. Output: one production-ready music prompt that evokes the [tradition description] described in the grounding artifact, **without naming [the specific forbidden category]**.

2. **Role section**
   One paragraph identifying the enhancer's job. Second paragraph stating the aesthetic grounding (reference the grounding artifact) and the forbidden-names scope.

3. **Hard Constraints section** (bulleted)
   - Never name [forbidden category] bullet.
   - Never reproduce signature [licks/motifs/beats] bullet.
   - Vocal policy bullet (per Decision 5).
   - One prompt out — no preamble/postamble.
   - Era-locked bullet (specific to this tradition's era).
   - Any invention rules (lyrics / titles / collaborators etc).

4. **What the Output Must Contain section** — the ten-part structure

   Fixed scaffolding, content varies by tradition. The ten parts are:
   1. **Genre triangulation** — one sentence placing the piece in the tradition.
   2. **Tempo and feel** — explicit BPM number, time signature, pocket.
   3. **Form and duration** — length, structural sketch, where peak sits.
   4. **Instrumentation / tone architecture** — specific instruments/sounds/treatments.
   5. **Playing technique / arrangement vocabulary** — the techniques that should appear.
   6. **Note-choice / harmonic grammar** — key, mode, resolution habits.
   7. **Rhythm section / rhythmic palette** — groove-level detail.
   8. **Production and mix** — era-specific production stance.
   9. **Affective target** — one or two from the grounding's affect list.
   10. **Avoid clause** — short closing clause naming what to avoid + vocal policy restatement.

5. **Tone and Style of the Output section** (bulleted)
   - Dense, technical, written for audio model not human.
   - Confident declarative sentences, no hedging.
   - No proper nouns from popular music.
   - No emoji, headers, lists inside the prompt itself.
   - Length target (from Decision 6).

6. **Translation Behavior section**
   Rules for silently translating forbidden references and informal language into the stub vocabulary. Explicit substitution table for the most common user shorthand.

7. **Example Behavior section**
   One worked example — a user input followed by a sample enhanced prompt that follows the ten-part structure and hits the word-count target. This is the single most important part of the file; it anchors tone.

8. **Refusal Behavior section**
   One paragraph on how to refuse direct-copy requests.

9. **Output Format section**
   One paragraph confirming: no preamble, no labels, no quotation marks, just the prompt text. The next consumer is the audio model.

### Length target

Full-song ENH file total: ~150–220 lines of markdown. The worked example is the single densest part.

---

## File B: `No[Name]-Live-ENH.md` — Live weighted-stub enhancer

### Purpose

System prompt for an LLM that accepts a brief user idea or a steering instruction during live playback, and returns 3–5 lines in `Stub Name : 0.XX` format with weights in [0.10, 1.00] — the format Gemini 3's live music model expects.

### Structure (fixed sections, in order)

1. **Title line and one-sentence subtitle**
   > # No[Name]-Live-ENH
   > 
   > > System prompt for an LLM acting as a **prompt enhancer** for the Gemini 3 *live* music generation model. Input: a short user idea or a steering instruction during live playback. Output: **3–5 single-line stubs**, each a named musical element followed by a numeric weight in the range **0.10–1.00**.

2. **Role section**
   One paragraph on the live model's stub-mixing behavior. Second paragraph on the aesthetic grounding.

3. **Hard Constraints section** (bulleted)
   - Output 3–5 stubs. Not fewer, not more.
   - Format exactly `Stub Name : 0.XX`.
   - Weights in [0.10, 1.00], two decimals.
   - Weights are independent prominence values, not probabilities.
   - No proper nouns from popular music.
   - No commentary — only stub lines.
   - Vocal policy bullet.
   - Era-locked bullet.

4. **Stub Vocabulary section** — grouped palette

   The core content. Group stubs into categories appropriate to the tradition. The typical groupings:
   - **Instrumentation stubs** (named instruments / sound sources).
   - **Tone / technique / production stubs** (treatments, effects, mix moves).
   - **Form and feel stubs** (tempo, structure, pocket).
   - **Harmony / architecture stubs** (key, mode, motivic moves).
   - **Vocal stubs** (if vocals apply).
   - **Production stubs** (mix stance, reverb, dynamics).
   - **Affective stubs** (moods from the grounding's affect list).

   Each stub is a concrete, specific noun phrase — short enough to fit on one line, specific enough to steer the model. Example:
   > `germanium fuzz cleaning up on volume rollback`
   > `French horn section in heroic parallel fifths`

   Target 40–70 stubs total across all groups. Enough variety to cover every steering direction without becoming an unusable soup.

5. **How to Choose Stubs section**
   The selection algorithm. Typical:
   1. One affective stub anchors the mood (weight 0.55–0.80).
   2. One form-and-feel stub sets tempo and posture (weight 0.60–0.90).
   3. One or two orchestration/tone stubs define the foreground (weight 0.45–1.00).
   4. Optionally one production stub for color (weight 0.20–0.60).

6. **Steering Behavior section** — the live-nudge table

   For each common steering phrase the user might say during playback ("harder," "softer," "drop it," "vocals in," "bluesier," "weirder"), name the specific stubs to emphasize. This is the live-performance interface.

   Table should have 8–12 steering phrases paired with 3–5 stubs each.

7. **Translation Behavior section**
   Rules for silently translating forbidden references into stub vocabulary.

8. **Example Behavior section**
   Three worked examples — three different user inputs, each with the exact stub-line output format. The examples should cover:
   - A fresh-start request (idea → initial stub set).
   - A mid-playback steering nudge.
   - A specific request for a particular element.

9. **Output Format section**
   One paragraph: only the stub lines, no fences, no labels, no quotes, no commentary. The next consumer is the live model's stub parser.

### Length target

Live ENH file total: ~180–240 lines of markdown. The stub vocabulary and the steering behavior sections are the longest parts.

---

## Shared design principles

### Silent translation (both files)

The user will often reference forbidden names, adjacent genres they're confusing with this one, or incompatible modern conventions. Both files instruct the enhancer to **silently translate** these into the stub/prose vocabulary of the tradition — never echo the forbidden term back.

Translation table should cover at minimum:
- Direct name references (the artist, their aliases, their collaborators).
- Signature-track references by title.
- Franchise/series references.
- Adjacent-genre terms (what's close but wrong).
- Era-wrong production terms (modern gestures that don't belong, or vintage gestures where the tradition is modern).
- Common user shorthand ("heavy," "trippy," "slow jam," "epic") that should be interpreted into the tradition's specific vocabulary.

### Era-lock (both files)

Every file has an explicit era-lock bullet that names:
- The target era of the tradition.
- Specific production/stylistic gestures from other eras that must not appear in the output.

### Refusal (full-song file only)

The full-song file includes a refusal clause for direct-copy requests. The live file doesn't need this — stub format can't produce a direct copy.

### Vocal policy (both files)

The vocal policy from Decision 5 is stated explicitly in both files. For instrumental-only traditions, there's a hard "no vocals" line. For textural-only traditions, there's a "vocals as texture only — pseudo-Latin / wordless / abstract fragments only" line. For lyrical-permitted traditions, there's an "invented lyrics only — never quoted or paraphrased" line.

---

## Reference examples

The two canonical examples in the output folder (or project context):

- **`NoHendrix-ENH.md` / `NoHendrix-Live-ENH.md`** — band tradition, instrumental-only, pre-1972 era, 180–320 word prose target. Shorter example because the ensemble is a trio.
- **`NoHiro-ENH.md` / `NoHiro-Live-ENH.md`** — composer tradition, textural vocals, 2010s era, 200–340 word prose target. Longer example because the four-tier stack is denser.

Read whichever matches your target's complexity before authoring.

---

## Sanity check before finalizing

For `No[Name]-ENH.md`:
1. ✅ All nine sections present, in order.
2. ✅ The ten-part output structure is explicit and matches `no[name]-prompt-craft.md`.
3. ✅ Hard constraints include vocal policy, era-lock, and no-copy rule.
4. ✅ Worked example exists and hits the word-count target.
5. ✅ Translation table covers the top forbidden references.

For `No[Name]-Live-ENH.md`:
1. ✅ All nine sections present, in order.
2. ✅ Stub vocabulary has 40–70 stubs grouped sensibly.
3. ✅ Selection algorithm is explicit.
4. ✅ Steering behavior table covers 8–12 common nudges.
5. ✅ Three worked examples cover fresh-start, steering, specific-element.
6. ✅ No stubs name any forbidden proper noun.
