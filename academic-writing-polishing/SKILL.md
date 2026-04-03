---
name: academic-writing-polishing
description: Use when polishing or rewriting existing academic or scientific text, excerpts, or manuscript sections for clarity, concision, section fit, journal style alignment, reviewer-response revision, AI-sounding phrasing reduction, or broader-audience adaptation.
---

# Academic Writing Polishing

## Overview

Polish existing academic writing without changing the underlying science. Diagnose the request shape first, then choose the lightest mode that achieves the goal.

Default audience, when unspecified, is an educated scientific reader outside the exact subfield.

## When Not to Use

- The user wants a brand-new draft from scratch and has not provided source text, notes, or an outline.
- The real task is fact-checking, literature search, citation gathering, or source verification.
- The task is pure translation rather than editorial revision.
- The task is only scientific peer review, methods critique, or statistical critique with no language-editing objective.

## Dispatch Table

| User request shape | Mode | Load | Output shape |
| --- | --- | --- | --- |
| User provides text and wants cleaner prose | Light polish | `references/core-editing.md` and only the section-specific file if needed | Revised text first; brief notes only if useful |
| User provides text but the logic, order, or section job is wrong | Structural polish or Section rewrite | `references/core-editing.md` plus the relevant section file | Reorganized rewrite plus a short diagnosis |
| User provides existing text for a new audience or genre | Audience rewrite | `references/other-genres-and-public-audiences.md` plus any relevant section file | Adapted rewrite plus a one-line framing note |
| User wants reviewer-response help or submission-risk checks | Structural polish as needed | `references/publishing-and-review.md` plus any relevant section file | Point-by-point response or issue list |
| User asks for polishing but provides no source text | Do not rewrite yet | None | Ask only for the minimum inputs: source excerpt, target venue or audience, and intervention level |

Load only what the task needs.

## Hard Constraints

- Preserve meaning, evidence, numbers, citation intent, equations, variables, and markup unless the user explicitly asks for substantive rewriting.
- Do not invent data, methods, results, mechanisms, references, or limitations.
- Do not silently strengthen or weaken claims.
- Do not smooth over scientific or logical flaws. Name them directly, then offer the safest rewrite.
- Do not break protected tokens such as citation numbers or callouts, citation keys, placeholders, LaTeX labels or commands, inline math, Markdown anchors, LaTeX anchors, or table structure.
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

## Quick Reference

### Structure

- Make the take-home message explicit early enough for the reader to carry it forward.
- Favor general-to-specific or question-to-answer progression.
- Make the text do the job of its slot. A Discussion opening should not read like a limitation paragraph, and a Results paragraph should not sound like interpretation.
- Group support, counterarguments, and rebuttals instead of alternating them sentence by sentence.

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

- If the user has not provided source text, do not pretend the rewrite is complete. Ask only for the minimum inputs: source excerpt, target venue or audience, and intervention level.
- If the user provides text, return the revised text first. Add brief notes only when they materially help the user understand the structural change, trade-off, or unresolved scientific issue.
- If the text has both writing and science problems, state the scientific or logical risk briefly, then provide the strongest safe rewrite that does not fabricate missing support.
- If multiple rewrites are genuinely useful, provide 2-3 options with a one-line explanation of the trade-off.

## Final Checks

- Does the prose still match the evidence?
- Did any edit change claim strength, scope, or causality?
- Is the section doing the job of its exact slot?
- Do numbers agree across abstract, text, tables, and figures?
- Do citations still support the sentence they follow?
- Did the rewrite preserve protected tokens, equations, variables, citation keys, and markup?
- Is the jargon level right for the audience?
