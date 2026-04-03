---
name: academic-writing-polishing
description: Use when polishing or rewriting existing academic or scientific text, excerpts, or manuscript sections for clarity, concision, logical flow, section fit, journal style alignment, reviewer-response revision, or AI-sounding phrasing reduction while preserving claims, numbers, citations, equations, and markup.
---

# Academic Writing Polishing

## Overview

Polish existing academic writing without changing the underlying science. Start by identifying what kind of academic text you have, what role the passage plays in the document, and how much intervention is appropriate. Then revise from structure to paragraph logic to sentence-level style, and finish with consistency and integrity checks.

Default audience, when unspecified, is an educated scientific reader outside the exact subfield.

## When Not to Use

- The user wants a brand-new draft from scratch and has not provided source text, notes, or an outline.
- The real task is fact-checking, literature search, citation gathering, or source verification.
- The task is pure translation rather than editorial revision.
- The task is only scientific peer review, methods critique, or statistical critique with no language-editing objective.
- The user wants new conclusions, stronger claims, or speculative mechanisms that are not already supported by the text.

## Dispatch Table

| User request shape | Mode | Load | Output shape |
| --- | --- | --- | --- |
| User provides text and wants cleaner prose | Light polish | `references/core-editing.md` and section-specific guidance only if needed | Revised text first; brief notes only if useful |
| User provides text but the logic, order, or paragraph jobs are wrong | Structural polish | `references/core-editing.md` plus `references/manuscript-sections.md` if section-specific | Reorganized rewrite plus a short diagnosis |
| User provides a section that does the wrong rhetorical job | Section rewrite | `references/manuscript-sections.md` plus `references/core-editing.md` | Rewritten section plus a short explanation of what changed |
| User wants point-by-point reviewer-response help | Response rewrite | `references/publishing-and-review.md` plus any relevant section file | Numbered response text or issue list |
| User asks for polishing but provides no source text | Do not rewrite yet | None | Ask only for the minimum inputs: source excerpt, target venue or audience, and intervention level |
| User asks for examples or model rewrites | Example-guided polish | `references/academic-revision-examples.md` as an example bank plus the relevant core file | Example first, then revised text if source text is available |

Load only what the task needs.

## Hard Constraints

- Preserve meaning, evidence, numbers, citation intent, equations, variables, and markup unless the user explicitly asks for substantive rewriting.
- Do not invent data, methods, results, mechanisms, references, or limitations.
- Do not silently strengthen or weaken claims.
- Never convert correlation into causation.
- Do not smooth over scientific or logical flaws. Name them directly, then offer the safest rewrite.
- Do not break protected tokens such as citation numbers or callouts, citation keys, placeholders, LaTeX labels or commands, inline math, Markdown anchors, LaTeX anchors, URLs, or table structure.
- Do not add, remove, or swap citations just to make the prose read better.
- Keep key terminology stable. Repeat the right keyword rather than forcing awkward synonyms.
- Use active voice by default, but allow passive voice where the action matters more than the actor, especially in Methods.
- If target discipline, journal, or voice materially affects the rewrite and cannot be inferred safely, ask before forcing a style.

## Core Workflow

1. Identify the genre, section role, audience, target style, and requested level of intervention.
2. Recover the controlling outline before doing line edits.
   - Name the job of each section or paragraph.
   - If the order is wrong, fix the order first.
3. Run the structural pass.
   - Check whether the piece answers the right question in the right order.
   - Group like ideas together.
   - Remove bait-and-switch movement across paragraphs.
4. Run the paragraph pass.
   - Keep one main idea per paragraph.
   - Move the punch line early.
   - Prefer logical order over transition-word overload.
5. Run the sentence pass.
   - Strengthen verbs.
   - Cut clutter, nominalizations, empty hedging, and weak openings.
   - Keep the subject and main verb close.
6. Run the integrity pass.
   - Check numbers, labels, claims, citations, tables, figures, equations, and section boundaries.
7. Run the fit pass.
   - Ask whether the revised passage sounds like the right section in the right paper for the right reader.

## Quick Reference

### Structure

- Make the take-home message explicit early enough for the reader to carry it forward.
- Favor general-to-specific or question-to-answer progression.
- Make the text do the job of its slot. A Discussion opening should not read like a limitation paragraph, and a Results paragraph should not sound like interpretation.
- Group support, counterarguments, and rebuttals instead of alternating them sentence by sentence.
- If the material is fundamentally hierarchical, procedural, or heavily numeric, consider whether prose should become a table or figure.

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

## Section Mini Templates

Use these as direction-of-travel templates, not fixed wording.

### Abstract mini template

- Sentence 1: background or problem
- Sentence 2: question, aim, or hypothesis
- Sentence 3: study design or method at a high level
- Sentence 4: key result
- Sentence 5: conclusion or implication

### Introduction mini template

- Paragraph 1: what is known and why it matters
- Paragraph 2: what remains unknown, inconsistent, or limited
- Paragraph 3: what this study asked or tested, and briefly how it addresses the gap

### Results mini template

- Opening sentence: main trend or contrast
- Middle sentence: one or two key values or comparisons
- Final sentence: cite the display item and move to the next result

### Discussion mini template

- Opening sentence: direct answer to the research question
- Middle sentences: interpretation, fit with prior literature, and important caveats
- Closing sentence: take-home message or implication without overselling

### Reviewer-response mini template

- Reviewer point
- Short agreement or disagreement statement
- Exact revision made or exact reason no revision was made
- Location of the change if available

## Output Contract

- If the user has not provided source text, do not pretend the rewrite is complete. Ask only for the minimum inputs: source excerpt, target venue or audience, and intervention level.
- If the user provides text, return the revised text first. Add brief notes only when they materially help the user understand the structural change, trade-off, or unresolved scientific issue.
- If the text has both writing and science problems, state the scientific or logical risk briefly, then provide the strongest safe rewrite that does not fabricate missing support.
- If multiple rewrites are genuinely useful, provide 2-3 options with a one-line explanation of the trade-off.
- If the user asks for examples, show one compact before-and-after example before or alongside the actual revision.

## Final Checks

- Does the prose still match the evidence?
- Did any edit change claim strength, scope, or causality?
- Is the section doing the job of its exact slot?
- Do numbers agree across abstract, text, tables, and figures?
- Do citations still support the sentence they follow?
- Did the rewrite preserve protected tokens, equations, variables, citation keys, and markup?
- Is the jargon level right for the audience?
