---
name: academic-writing-polishing
description: Use when polishing or rewriting existing academic or scientific text for clarity, concision, structure, discipline or journal style alignment, reviewer-response revision, AI-sounding phrasing reduction, or broader-audience adaptation while preserving claims, numbers, citations, equations, and markup.
---

# Academic Writing Polishing

## Overview

Polish existing academic writing without changing the underlying science. Diagnose the task type first, then revise from structure to paragraph logic to sentence-level style, and finish with consistency and integrity checks.

Default audience, when unspecified, is an educated scientific reader outside the exact subfield.

## When to Load References

| Situation | Load |
| --- | --- |
| Sentence, paragraph, or full-draft polish | `references/core-editing.md` |
| Manuscript section, abstract, table, figure, or full paper | `references/manuscript-sections.md` |
| Journal submission, reviewer response, or publication-risk check | `references/publishing-and-review.md` |
| Review article, grant, recommendation letter, personal statement, lay summary, media, science news, or social post | `references/other-genres-and-public-audiences.md` |

Load only what the task needs.

## Hard Constraints

- Preserve meaning, evidence, numbers, citation intent, equations, variables, and markup unless the user explicitly asks for substantive rewriting.
- Do not invent data, methods, results, mechanisms, references, or limitations.
- Do not silently strengthen or weaken claims.
- Do not smooth over scientific or logical flaws. Name them directly, then offer the safest rewrite.
- Do not break citation keys, equation syntax, LaTeX commands, table structure, or Markdown structure.
- Keep key terminology stable. Repeat the right keyword rather than forcing awkward synonyms.
- Use active voice by default, but allow passive voice where the action matters more than the actor, especially in Methods.
- If target discipline, journal, or voice materially affects the rewrite and cannot be inferred safely, ask before forcing a style.

## Modes

| Mode | Use when | Main action |
| --- | --- | --- |
| Light polish | Structure is sound | Tighten wording, verbs, flow, and grammar |
| Structural polish | Logic or order is weak | Rebuild the outline, reorder paragraphs, then line-edit |
| Section rewrite | A section does the wrong rhetorical job | Rewrite to match the section's purpose |
| Audience rewrite | The same content must serve a different audience | Reframe jargon, detail density, and opening order |

## Core Workflow

1. Identify the genre, section role, audience, target style, and requested level of intervention.
2. Recover the controlling outline before doing line edits.
   - Name the job of each section or paragraph.
   - If the order is wrong, fix the order first.
3. Run the structural pass.
   - Check whether the piece answers the right question in the right order.
   - Group like ideas together.
4. Run the paragraph pass.
   - Keep one main idea per paragraph.
   - Move the punch line early.
   - Prefer logical order over transition-word overload.
5. Run the sentence pass.
   - Strengthen verbs.
   - Cut clutter, nominalizations, empty hedging, and weak openings.
   - Keep the subject and main verb close.
6. Run the final safety pass.
   - Check numbers, labels, claims, citations, tables, figures, equations, and section boundaries.

## Core Editing Rules

### Structure

- Make the take-home message explicit early enough for the reader to carry it forward.
- Favor general-to-specific or question-to-answer progression.
- For arguments with competing points, group support, counterarguments, and rebuttals instead of alternating them sentence by sentence.
- Make the text do the job of its slot. A Discussion opening should not read like a limitation paragraph, and a Results paragraph should not sound like interpretation.

### Paragraphs

- Keep one controlling idea per paragraph.
- Use short, focused paragraphs when possible.
- Put the key sentence early.
- Use repetition of core terms when it improves clarity.
- Use parallel structure to move the reader through similar ideas.

### Sentences

- Prefer strong verbs over abstract noun phrases.
- Cut dead phrases, empty intensifiers, and needless prepositions.
- Replace `there is/there are` openings when a concrete subject can do the job.
- Turn negative constructions into positive ones when that makes the sentence clearer.
- Use punctuation for clarity and emphasis, not decoration.
- Keep jargon and acronyms only when they are standard for the intended reader.
- Reserve `significant` for statistical significance.
- If asked to reduce AI-sounding phrasing, cut filler, generic uplift, decorative symmetry, and over-patterned lists without changing substance.

## Output Contract

If the style target is unclear and the choice would materially change the rewrite, ask one focused question before revising.

If the user provides text, return the revised text first. Add brief notes only when they materially help the user understand the structural change, trade-off, or unresolved scientific issue.

If the text has both writing and science problems:
- State the scientific or logical risk briefly.
- Then provide the strongest safe rewrite that does not fabricate missing support.

If multiple rewrites are genuinely useful, provide 2-3 options with a one-line explanation of the trade-off.

## Final Checks

- Does the prose still match the evidence?
- Did any edit change claim strength, scope, or causality?
- Is the section doing the job of its exact slot?
- Do numbers agree across abstract, text, tables, and figures?
- Do citations still support the sentence they follow?
- Did the rewrite preserve equations, variables, citation keys, and markup?
- Is the jargon level right for the audience?
