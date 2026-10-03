# README Template

How to author the GitHub repository README for the new `endless-[name]-skill` repo. Read this file every run.

The core move: **position the skill as the primary deliverable, reference the sibling family, document installation and usage, and include citation + donate footer.** Mirrors the structure used for `endless-jimmy-skill` and `endless-hiro-skill`.

Filename: `README.md`, saved to `/mnt/user-data/outputs/`.

---

## Repository URL

Ask the user for the intended repo URL. If they don't provide one, use the placeholder `https://github.com/MushroomFleet/endless-[name]-skill` and flag it for them to confirm.

---

## Section structure (fixed, in order)

### 1. Title

```markdown
# endless-[name]-skill
```

### 2. One-line blockquote tagline

Describes what the skill does in one sentence. For a real-artist target, state the forbidden-name clause. Example:

> A Claude skill for generating full ten-track phantom albums of ready-to-paste Gemini music generation prompts in the [tradition description] — **without ever naming the [forbidden category] the tradition is shaped around.**

Horizontal rule after.

### 3. "What this is" section

A one-paragraph intro, followed by a bulleted list of what the skill invents:

- The phantom artist / composer / producer (details per Decision 4).
- The project alias (if applicable).
- The phantom label.
- The impossibly-high catalogue number.
- The ten-track album arc.
- The ten dense prose prompts (word count per Decision 6).
- Optional flourishes (phantom OST / vocalist / themed-album variants).

Close with a paragraph stating "The skill is the polished, packaged successor to the earlier ENH system-prompt project this repository was built around" and noting that the original ENH work (if applicable) is preserved in a subfolder.

### 4. "Why a skill instead of just a system prompt" section

Two paragraphs. First explains that single-prompt enhancement works for one-shot requests but doesn't give album coherence. Second says the skill collapses the work into one request: *"use endless-[name] on 'IDEA'."*

### 5. "What the skill produces" section

Numbered list of what the output artifact contains:

1. A concept paragraph.
2. An artist/composer/band card.
3. A "How this catalogue works" note.
4. Ten tracks with specs and full prompts.
5. An "Author your own" section for extending the discography.

### 6. "Family" section

Lists the sibling skills with one-line descriptions each:

- `endless-overtures` — phantom catalogues of classical works for real named composers.
- `endless-hardbass` — phantom hardbass albums in the Saint Petersburg lineage.
- `endless-jimmy` — phantom late-1960s psychedelic-blues-rock trio albums.
- `endless-hiro` — phantom 2010s Tokyo cinematic hybrid-score albums.
- `endless-creator` — the meta-skill that creates skills like this one.

(Omit any that haven't shipped yet; add the new skill to the list in future releases.)

Close with the family's shared idea: **the title carries the fiction; the prompt carries the sound.**

### 7. "The register dial" section

A short section explaining the two-poles-plus-blend concept, with:

- **[Pole A]** — one-paragraph description of the sonic/affective center.
- **[Pole B]** — one-paragraph description.
- **BLEND** — the default allocation.

Close with the inference rule: "Give it *'[VIGIL-example IDEA]'* and it lands on [A]. Give it *'[CHARGE-example IDEA]'* and it lands on [B]."

### 8. "[Tradition-specific] architecture" section (optional)

For traditions with distinctive structural logic — tier stacks, crescendo arcs, loop-and-vary structures — a short explainer. Can be omitted if the tradition's architecture is captured elsewhere.

### 9. "Installation" section

One paragraph on downloading the `.skill` file and clicking **Save skill** in Claude. Second paragraph on self-hosted installation via unzip.

### 10. "Repository contents" section

A markdown table:

| Path | Purpose |
|---|---|
| `endless-[name].skill` | The packaged skill archive. Primary deliverable. |
| `endless-[name]/SKILL.md` | The skill's system prompt. |
| `endless-[name]/references/[slug]-without-saying-[slug]-grounding.md` | Aesthetic source of truth. |
| `endless-[name]/references/phantom-[format]-method.md` | How to invent the artist, label, catalogue. |
| `endless-[name]/references/no[name]-prompt-craft.md` | Ten-part prose prompt structure. |
| `endless-[name]/references/example-album.md` | Complete worked example. |
| `[OriginalENH]-No-[OriginalENH]-ENH/` | **Preserved.** Original system-prompt project (if applicable). |

### 11. "Usage" section

One paragraph on trigger phrases. Followed by a worked **Example** sub-section with:

- A specific user request.
- A bullet list describing what the result contains (invented composer with X alias, invented label, Y-year release, which register the IDEA pushed to, the album's track-level summary).

### 12. "Hard rules" section

Bulleted list of the enforced constraints — exactly those from the SKILL.md hard rules section but prose-friendlier for a reader scanning the README.

### 13. "Extending or adapting" section

Four-step list for forking the skill pattern to another tradition:

1. Replace the grounding artifact.
2. Rewrite the register dial.
3. Update album arc, tempo bands, instrumentation palette, naming grammar.
4. Keep the ten-part prose-prompt structure intact.

Close with: "The three-file references pattern (grounding + phantom-artist-method + prompt-craft) plus one example album is a portable shape across all four `endless-*` skills."

### 14. "License" section

One short line.

### 15. Citation section

```markdown
## 📚 Citation

### Academic Citation

If you use this codebase in your research or project, please cite:

```bibtex
@software{endless_[name]_skill,
  title = {endless-[name]-skill: [One-line description of what this skill does]},
  author = {[Drift Johnson]},
  year = {[CURRENT YEAR]},
  url = {[Repo URL]},
  version = {1.0.0}
}
```
```

### 16. Donate badge

```markdown
### Donate:

[![Ko-Fi](https://cdn.ko-fi.com/cdn/kofi3.png?v=3)](https://ko-fi.com/driftjohnson)
```

---

## Style and tone of the README

- Confident, declarative, written for a GitHub browser.
- Technical where it serves the reader; prose where it doesn't.
- No emoji in body text (except the 📚 in the Citation heading, per house style).
- Code blocks for file paths, YAML, bash, BibTeX.
- Horizontal rules only between the tagline and the main body — not between every section.
- Avoid talking about Claude capabilities or developer internals; focus on what the skill does and how to use it.

---

## Reference examples

The two canonical examples:

- **`endless-jimmy-skill`** README — band tradition, instrumental-only, pre-1972 era. Shorter architecture section because the ensemble is a trio.
- **`endless-hiro-skill`** README — composer tradition, textural vocals, 2010s era. Includes the four-tier instrumentation stack as a bonus explainer section.

Read whichever is structurally closer to your target before authoring.

---

## Sanity check before saving

1. ✅ All 16 sections present, in order.
2. ✅ Repo URL correct (asked user) or flagged as placeholder.
3. ✅ Family section lists the correct sibling set.
4. ✅ Register dial names consistent with SKILL.md.
5. ✅ Hard rules list matches SKILL.md hard rules.
6. ✅ Citation BibTeX key matches skill name (`endless_[name]_skill`).
7. ✅ Citation URL matches the repo URL.
8. ✅ Donate badge at the bottom.
9. ✅ No forbidden names anywhere in the README.
