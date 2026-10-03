# endless-creator-skill

> A Claude meta-skill that generates custom `endless-[name]` music prompt skills on demand — supply a target artist, genre, era, or stylistic idea, and the skill returns a complete, packaged `.skill` archive plus a repo-ready README, pre-verified against every structural rule the family requires.

---

## What this is

`endless-creator` is a **skill that creates other skills**. It automates the full chain used to build `endless-jimmy` (phantom late-1960s psychedelic-blues-rock trio) and `endless-hiro` (phantom 2010s Tokyo cinematic hybrid-score composer), so any target the user describes can become an installable Claude skill in a single request.

Give it a TARGET — an artist name, a genre, an era, or an abstract stylistic idea — and it:

- Researches the target against the oblique-musical-description framework.
- Makes six design decisions (skill name, register dial, album arc, naming grammar, vocal policy, prompt word-count target).
- Authors seven coordinated files: a grounding artifact, two ENH system prompts, a packaged skill folder with four reference files, a `.skill` zip archive, and a GitHub README.
- Pre-verifies the generated SKILL.md description length against Claude's 1024-char limit before writing.
- Checks forbidden-names consistency across every file before packaging.

The output is another `endless-[name]` skill, ready to install into Claude with the **Save skill** button.

## Why a meta-skill

Building a single `endless-*` skill by hand means authoring roughly seven markdown files that have to stay internally consistent — the grounding describes the aesthetic, the two ENH system prompts translate the grounding into runtime behaviours, the SKILL.md orchestrates everything, and three reference files extend the grounding into album-arc, naming grammar, and worked examples. The files cross-reference each other constantly. Register dial names, vocal policy, word-count targets, era anchors, and forbidden-names lists all have to match across every file.

Doing this once is a focused afternoon. Doing it for every tradition you want to encode — every artist you'd like to evoke, every scene you'd like to inhabit — is a lot of repeated authoring where the real creative work is the *design decisions*, not the mechanical consistency work.

`endless-creator` lifts the mechanical work out and leaves the user with the design decisions. The output of a single conversation is a complete, packaged, consistent skill ready to ship.

## What the skill produces

Seven files per run, written to `/mnt/user-data/outputs/`:

1. **The grounding artifact** — `[slug]-without-saying-[slug]-grounding.md` — a 300–500-line oblique description of the target aesthetic in musical, structural, and production terms. The source of truth that all other files draw from.
2. **The full-song ENH system prompt** — `No[Name]-ENH.md` — a system prompt for an LLM acting as a prose prompt enhancer for Gemini music generation models.
3. **The live ENH system prompt** — `No[Name]-Live-ENH.md` — a system prompt for the Gemini 3 live music model's weighted-stub format (3–5 stubs, weights 0.10–1.00).
4. **The packaged skill folder** — `endless-[name]/` containing SKILL.md and references/.
5. **The packaged `.skill` archive** — `endless-[name].skill` — the zip ready for Claude's **Save skill** button.
6. **The repo README** — `README.md` — GitHub-ready, with the family framing, installation, usage, hard rules, extending guidance, citation, and donate badge.
7. **A design-decisions summary** — presented inline in the conversation so the user sees the reasoning behind every choice.

## Family

`endless-creator` sits at the top of a growing family of music-prompt-writing skills:

- **`endless-creator`** (this skill) — the meta-skill that creates the family's members on demand.
- **`endless-overtures`** — phantom catalogues of classical works that never existed, for real named composers (Chopin, Debussy, Bach, Rachmaninoff). Uses Lyria 3.1.
- **`endless-hardbass`** — phantom ten-track hardbass albums by wholly invented artists in the Saint Petersburg pumping-house lineage. Uses Lyria 3.5.
- **`endless-jimmy`** — phantom ten-track psychedelic-blues-rock trio albums in the late-1960s single-coil-through-cranked-tube-amp tradition.
- **`endless-hiro`** — phantom ten-track hybrid-score albums in the 2010s Tokyo cinematic tradition.

All of them share the same guiding idea: **the title carries the fiction; the prompt carries the sound.** The audio model does not read a catalogue number or an artist alias — everything the listener should hear must be described in the prompt itself. `endless-creator` carries that principle into the meta-level: it generates new members of the family while preserving their shared discipline.

## The six design decisions

Every run makes these six decisions, in order, before writing any file:

1. **Skill name** — short evocative word for `endless-[name]`. A nickname/wink for a real artist (jimmy for Hendrix, hiro for Sawano), the genre name itself for a scene (hardbass), or an era-evocative word for a movement.
2. **Register dial** — two single-word thematically resonant poles plus a BLEND default. Hendrix got CATHEDRAL / STORM. Sawano got VIGIL / CHARGE. A dub artist would get ECHO / RIDDIM. A shoegaze act would get HAZE / SPIKE. The names resonate with each tradition's two most distinct emotional modes.
3. **Album arc** — the ten-track default shape, adapted to the ensemble type (band / composer / electronic producer / DJ / MC). Band traditions use song-list arcs. Composer traditions use cue-list arcs. Electronic producers use anthem/breakdown/peak arcs. DJs use mix arcs.
4. **Naming grammar** — the format for phantom artist names, project aliases (if any), album titles, track titles, label names, catalogue numbers, and the alternate-timeline release-year window.
5. **Vocal policy** — instrumental-only (Hendrix pattern), textural-only (Sawano pattern — pseudo-Latin / wordless / abstract fragments), or lyrical-permitted (only when the tradition is centered on singing, with invented lyrics only).
6. **Prompt word-count target** — scales with ensemble density. 180–320 words for trios and small ensembles. 200–320 for full bands and solo producers. 220–340 for hybrid orchestral stacks. 240–360 for big-band jazz or wall-of-sound traditions.

These decisions drive every subsequent file. Change the dial names or the vocal policy and the entire set of generated files changes with them, consistently.

## Installation

Download the packaged skill: [`endless-creator.skill`](./endless-creator.skill).

In Claude, present the file and click **Save skill** on the card that appears. The skill installs into your profile and becomes available in every future conversation.

Alternatively, if you're running your own Claude setup, unzip `endless-creator.skill` and place the resulting `endless-creator/` folder in your skills directory (usually `~/.claude/skills/` or your organization's equivalent).

## Repository contents

| Path | Purpose |
|---|---|
| `endless-creator.skill` | The packaged meta-skill archive. The primary deliverable of the repository. |
| `endless-creator/SKILL.md` | The meta-skill's system prompt — the 7-step workflow, hard rules, and design decisions. |
| `endless-creator/references/chain-workflow.md` | The step-by-step orchestration guide: research protocol, six design decisions, seven files in build order, pre-flight and post-flight checklists. |
| `endless-creator/references/grounding-artifact-template.md` | The twelve fixed sections every grounding artifact must contain, with per-section guidance and length targets. |
| `endless-creator/references/enh-prompt-templates.md` | The fixed nine-section structures for both the full-song prose enhancer and the live weighted-stub enhancer. |
| `endless-creator/references/skill-structure-template.md` | The SKILL.md body structure, the four reference files' section structures, the description-length pre-verification snippet, and the packaging bash commands. |
| `endless-creator/references/readme-template.md` | The sixteen-section README structure matching endless-jimmy-skill and endless-hiro-skill, with citation BibTeX and donate badge conventions. |
| `endless-creator/references/reference-examples.md` | Side-by-side comparison of endless-jimmy and endless-hiro with a decision table for which to use as structural reference based on target type. |

## Usage

Once installed, trigger the skill by:

- Naming it: *"use endless-creator to make an endless-[name] skill for [TARGET]"*
- Or by asking for its output shape directly: *"turn [artist / genre / era] into an endless skill"*, *"package this artist as a skill"*, *"build endless-[name] from [target]"*, *"create a music prompt skill for [X]"*

The TARGET can be:
- **A specific real artist** — handled with the phantom-artist pattern. The real artist is never named in any output file; their aesthetic is encoded as oblique musical vocabulary.
- **A genre or scene** — handled by describing the scene's canonical instrumentation, rhythmic feel, production conventions, and era anchor. The genre name itself can appear in outputs; canonical artists within it cannot.
- **An era or movement** — handled similarly to a genre, with a tighter era anchor.
- **An abstract stylistic idea** — the skill asks 2–4 clarifying questions to anchor the tradition before proceeding.

### Example

**Request:** *"use endless-creator to make an endless-burial skill for the UK 2-step garage / dubstep producer known for crackle, submerged pads, and ghostly vocal samples"*

**Result:** A complete new skill package. The run will:
- Confirm the target and suggest `endless-burial` as the skill name (or offer alternatives).
- Research the aesthetic (crackle-and-vinyl-dust foley, submerged pads, 2-step garage pocket, pitched-up vocal samples as texture, late-night nocturnal mood, dedicated sub-bass extension, London post-garage lineage).
- Propose a register dial — something like **FOG** (ambient / submerged / beatless / nocturnal) and **PATTER** (2-step garage pocket / sub-bass / rimshot-driven) with BLEND as the default.
- Propose a vocal policy of **textural only** — pitched-shifted vocal samples with no coherent lyrics.
- Set the prompt word-count target at ~200–320 words (solo producer with layered textural stack).
- Author the grounding artifact, both ENH prompts, the skill folder with its four references, package the `.skill` archive, and write the GitHub README.
- Present everything with a design-decisions summary showing why each choice was made.

The user gets a complete, installable skill at the end of a single conversation.

## Hard rules

The meta-skill enforces constraints that propagate into every skill it generates:

- **Pre-verify SKILL.md description length against Claude's 1024-char limit** before writing. The chain uses a Python one-liner to measure; if over, it trims and re-measures until compliant with ≥3-char headroom. (This avoids the back-and-forth of discovering a too-long description after packaging.)
- **For real-artist targets, never name the artist** in any generated file — no artist names, no project aliases, no collaborator names, no band names, no franchise names, no track or album titles. All forbidden references are translated silently into musical vocabulary.
- **For genre or era targets without a specific artist**, naming the genre is fine, but canonical artists within it are refused when the user names them.
- **Package as a proper nested `.skill` zip** — never flat. The archive is verified with `unzip -l` and `file` before being presented.
- **Match the output structure to the family** — every generated skill mirrors `endless-jimmy` and `endless-hiro` in shape: SKILL.md with the 7-step workflow, references/ holding grounding + method + prompt-craft + example-album.
- **Preserve consistency across all seven generated files** — register dial names, vocal policy, album arc, word-count target, era anchor, and forbidden-names list all have to match across every output file. The chain runs a pre-flight checklist before packaging.

## Extending the pattern

The meta-skill's own pattern can be forked for adjacent problems that need the same discipline:

- **Non-music creative traditions** — the chain pattern (grounding artifact + ENH prompts + packaged skill + README) adapts to visual-art generation prompts, screenwriting prompts, or any domain where a specific aesthetic needs to be encoded as reusable vocabulary. Replace the music-specific references with domain-equivalent ones.
- **Different output models** — the ENH prompts in `endless-creator` target Gemini music generation specifically. The templates in `enh-prompt-templates.md` can be re-skinned for Suno, Udio, Riffusion, or any other prompt-driven audio model whose format differs.
- **Non-phantom variants** — the chain defaults to the phantom-artist pattern. The optional `endless-overtures` variant (real composer, phantom works) is a different naming grammar. Future variants could handle real-genre + phantom-era, real-era + phantom-scene, and so on.
- **Beyond music** — the four-decision framework (what tradition / what register / what naming / what policy) and the three-reference pattern (grounding + method + prompt-craft) is a portable shape for any aesthetic-encoding task.

If you fork the meta-pattern for a new domain, the pre-verification, forbidden-names tracking, and nested-archive packaging patterns should carry over directly.

## License

Choose a license that suits your intended use and add a `LICENSE` file to the repository.

## 📚 Citation

### Academic Citation

If you use this codebase in your research or project, please cite:

```bibtex
@software{endless_creator_skill,
  title = {endless-creator-skill: A Claude meta-skill that generates custom endless-[name] music prompt skills from a user-supplied target artist, genre, era, or stylistic idea},
  author = {[Drift Johnson]},
  year = {2026},
  url = {https://github.com/MushroomFleet/endless-creator-skill},
  version = {1.0.0}
}
```

### Donate:

[![Ko-Fi](https://cdn.ko-fi.com/cdn/kofi3.png?v=3)](https://ko-fi.com/driftjohnson)
