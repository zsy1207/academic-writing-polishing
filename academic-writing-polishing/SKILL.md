---
name: academic-writing-polishing
description: Use when polishing or rewriting existing academic or scientific text, excerpts, or manuscript sections for clarity, concision, logical flow, section fit, journal style alignment, reviewer-response revision, or AI-sounding phrasing reduction while preserving claims, numbers, citations, equations, and markup.
---

# Academic Writing Polishing

## Overview

Polish existing academic writing without changing the underlying science. Choose the lightest mode that solves the actual problem, load only the needed sections from the reference files, and stop once the passage does its job.

Default audience, when unspecified, is an educated scientific reader outside the exact subfield.

## When Not to Use

- The user wants a brand-new draft from scratch and has not provided source text, notes, or an outline.
- The real task is fact-checking, literature search, citation gathering, or source verification.
- The task is pure translation rather than editorial revision.
- The task is only scientific peer review, methods critique, or statistical critique with no language-editing objective.
- The user wants new conclusions, stronger claims, or speculative mechanisms that are not already supported by the text.

## Routing Priority

Apply these checks in order.

1. No source text: do not rewrite yet. Ask only for the minimum inputs.
2. Reviewer-response request: use `Response rewrite`.
3. Section does the wrong rhetorical job: use `Section rewrite`.
4. Logic or order is weak across sentences or paragraphs: use `Structural polish`.
5. Otherwise: use `Light polish`.
6. If the user explicitly asks for examples, add `Example-guided polish` on top of the selected mode.

## Mode Map

| Mode | Use when | Read only | Run | Skip | Stop when |
| --- | --- | --- | --- | --- | --- |
| Light polish | Structure and section role are basically sound | `core-editing.md`: `Cut clutter`, `Work with verbs`, `Build better sentences and paragraphs`, `Micro-grammar reminders`, `Example edits` | sentence pass -> integrity pass -> fit pass | outline rebuild, section reset, process coaching | the prose is cleaner, shorter, and clearer without changing meaning |
| Structural polish | Paragraph order, emphasis, or logic is weak | `core-editing.md`: `Build better sentences and paragraphs`, `Example edits`; plus the relevant section from `manuscript-sections.md` if needed | outline recovery -> paragraph pass -> sentence pass -> integrity pass -> fit pass | process coaching, reviewer-response logic | each paragraph has one job and the passage now moves in the right order |
| Section rewrite | The passage belongs to a section but is doing the wrong job | the relevant section only from `manuscript-sections.md`; plus matching examples from `academic-revision-examples.md` if needed | section-role reset -> paragraph design -> sentence pass -> integrity pass -> fit pass | full-document restructuring, unrelated sections | the passage now sounds like the right section in the paper |
| Response rewrite | The user needs point-by-point reviewer response text | `publishing-and-review.md`: `Submission and revision -> Response to reviewers`; plus Section 7 of `academic-revision-examples.md` if needed | classify comment -> decide agree / partly agree / disagree -> draft response -> tone check -> final check | full manuscript rewrite, publication-ethics sections unless directly asked | each comment has a polite, specific, traceable response |
| Example-guided polish | The user wants model rewrites, style analogies, or concrete before/after patterns | the matching subsection(s) from `academic-revision-examples.md` only | show one compact example -> apply the selected main mode | broad reference loading | the user has one clear example and one task-specific rewrite |

Load only the named sections. Do not load an entire reference file unless the task genuinely needs most of it.

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

