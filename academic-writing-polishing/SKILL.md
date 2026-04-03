---
name: academic-writing-polishing
description: Polish, rewrite, or draft academic manuscript prose, cover letters, or reviewer responses. Use when clarity, concision, sentence variety, verb strength, paragraph logic, section fit, journal alignment, claim calibration, literature synthesis, table/figure integration, numerical presentation, or AI-sounding phrasing are concerns.
---

# Academic Writing Polishing

## Overview

Polish, rewrite, or draft academic prose without changing the underlying science unless the user explicitly requests substantive changes backed by supplied facts. Choose the lightest mode that solves the problem, load only the needed reference sections, and stop once the text is safe, clear, and fit for purpose.

Audience follows task type unless the user or journal says otherwise:

- Manuscript prose: an educated scientific reader outside the exact subfield.
- Cover letters: the handling editor deciding fit and interest.
- Reviewer responses: the editor and reviewers checking traceability, accuracy, and tone.

## When Not to Use

- The task is pure translation rather than editorial writing.
- The task is fact-checking, literature search, citation gathering, or source verification only.
- The task is standalone scientific peer review, methods critique, or statistical critique with no writing objective.
- The task is a grant proposal, review-article strategy session, recommendation letter, personal statement, press release, lay summary, or media-prep request that needs domain-specific structure beyond local prose polishing.
- The user wants new conclusions, stronger claims, or speculative mechanisms not supported by supplied evidence.

## Fast Workflow

1. Identify source text, target section, target journal, implied audience, intervention level, and whether minimum inputs are present.
2. If minimum inputs are missing, switch to `Intake` and ask only for the missing items.
3. If a journal is named and instructions are not provided, retrieve only the official publisher guidance and apply it as a hard constraint.
4. Select one base mode from the Routing Priority. Add `Example-guided polish` only when the user explicitly asks for examples, templates, or before/after models.
5. Read only the sections listed in the Mode Map.
6. Run the listed passes in order.
7. Verify meaning preservation, claim strength, logic, section fit, protected tokens, and any applicable journal constraints.
8. Revise again only when a substantive issue remains. Avoid cosmetic churn.
9. Check whether the key message survives skim reading of the title-equivalent opening, abstract-level summary, and any referenced table or figure.
10. Deliver revised text first. Keep notes brief and limited to trade-offs, risks, or missing information.

## Minimum Inputs by Task

- For polishing or rewriting existing prose: source text. If section fit matters, identify the target section.
- For section drafting: target section, topic or research question, and the facts or bullet points the draft must be built from.
- For data-bearing sections (`Abstract`, `Results`, `Discussion`): study context, main findings, and claim limits that must be preserved.
- For cover letters: manuscript title or type, key finding, target journal, and any confirmed submission declarations. Use placeholders rather than inventing declarations.
- For reviewer responses drafted from scratch: reviewer comment, confirmed action taken or intended stance, and revision location if known. If the user wants polishing only, require the draft response itself.
- If any required item is missing, ask only for the missing items. Do not draft around the gap.

## Journal Rules

- User-supplied journal instructions are the primary authority.
- Otherwise, use only the journal's official publisher or society page. Do not rely on third-party blogs, submission anecdotes, or aggregator summaries.
- Extract only the constraints that matter for the current task: word limit, section structure, reference style, spelling variant, or explicit style rules.
- If the official guidance cannot be retrieved reliably, say so and ask the user for the instructions or a direct link.

## Routing Priority

1. User asks only for examples, templates, or before/after models and does not ask for live revision or drafting -> `Examples-only`.
2. Minimum inputs for the requested task are missing -> `Intake`.
3. No source text, generation requested, and minimum inputs present -> `Generation`.
4. Reviewer-response request -> `Response rewrite`.
5. Section does the wrong rhetorical job -> `Section rewrite`.
6. Logic or order is weak across sentences or paragraphs -> `Structural polish`.
7. Otherwise -> `Light polish`.

After selecting the base mode, add `Example-guided polish` only if the user explicitly wants examples, templates, before/after models, or rewrite rationale illustrated with one compact example.

## Mode Map

| Mode | Read only | Run |
| --- | --- | --- |
| Intake | `none` | request task-specific minimum inputs |
| Examples-only | matching subsection from `academic-revision-examples.md` via the Quick Matching Guide; plus `publishing-and-review.md`: `Response to reviewers` for reviewer-response examples, or `manuscript-sections.md`: `Cover letters for journal submission` for cover-letter examples | show 1-3 examples -> one-line takeaway |
| Light polish | `core-editing.md`: `Cut clutter`, `Work with verbs`, `Build better sentences and paragraphs`; add `Logic and argumentation`, `Calibrate hedging`, `Present numbers effectively`, or `Micro-grammar reminders` only if needed | sentence pass -> integrity pass -> fit pass -> targeted review |
| Structural polish | `core-editing.md`: `Build better sentences and paragraphs`, `Logic and argumentation`, `Cut clutter`, `Work with verbs`; plus relevant section from `manuscript-sections.md` | outline recovery -> paragraph pass -> sentence pass -> integrity pass -> fit pass -> review |
| Section rewrite | relevant section from `manuscript-sections.md`; matching examples from `academic-revision-examples.md` if useful | section-role reset -> paragraph design -> sentence pass -> integrity pass -> fit pass -> review |
| Response rewrite | `publishing-and-review.md`: `Response to reviewers`; Section 7 of `academic-revision-examples.md` if useful | classify -> choose stance -> draft -> tone check -> review |
| Generation | relevant section from `manuscript-sections.md`; `core-editing.md`: `Principles`, `Build better sentences and paragraphs`, `Logic and argumentation`; add sentence-level, hedging, and numbers sections only if needed | outline design -> paragraph drafting -> sentence pass -> integrity pass -> fit pass -> review |
| Example-guided polish | matching subsection from `academic-revision-examples.md` | consult one compact example -> apply main mode; show it only if the user explicitly asked |

Read only the named sections. Do not load an entire reference file unless the task genuinely needs most of it.

## Review Rules

- `Intake` and `Examples-only`: no review loop.
- `Light polish`: run the iteration loop with a targeted review in each cycle.
- `Structural polish`, `Section rewrite`, `Response rewrite`, and `Generation`: run the iteration loop with a full review in each cycle.
- Treat an issue as substantive when it affects meaning preservation, logic, evidence-claim alignment, claim strength, section fit, journal compliance, protected tokens, or professional credibility.
- Do not keep revising only to create stylistic variation or chase a score once the text is already safe and section-fit.

## Iteration Loop

- For every mode except `Intake` and `Examples-only`, run this cycle at least once: `check and review -> score and suggestions -> iterate`.
- Count the first scored review after the initial draft as iteration 1.
- Score on a 0-100 scale using this rubric:
  - meaning preservation and token integrity: 25
  - logic, argumentation, and literature synthesis: 20
  - section fit and audience/journal fit: 20
  - claim calibration and evidence-claim alignment: 15
  - clarity, concision, verb strength, and sentence variety: 15
  - skimmability and table/figure integration: 5
- Score only against the requested scope. Do not lower the score because the output did not add content, sections, citations, or reframings that the user did not ask for.
- After each scored review, list only the top substantive issues that still block a score above 98.
- Revise only those substantive issues, then score again.
- Stop when the score is greater than 98.
- Hard cap the loop at 10 iterations.
- If the score is already above 98 after the first scored review, stop immediately rather than creating stylistic variation.
- If iteration 10 still scores 98 or below, stop and report the remaining substantive trade-offs instead of claiming perfection.

## Diagnostic Checks

- Clarity and concision: clutter, nominalization, empty openings, filler, buried verbs.
- Verbs and sentence variety: strong verbs carry key claims; sentence length and structure vary enough to maintain rhythm; no monotonous subject-verb-object chains.
- Logic and paragraph architecture: one job per paragraph, key sentence early, explicit reasoning, no unsupported leaps.
- Literature synthesis: prior work compared and contrasted across studies, not summarized study-by-study.
- Hedging and claim strength: no causal overreach, no stacked hedges, qualifiers match evidence type.
- Numbers and data: comparison over duplication, meaningful precision, absolute risk when clearer.
- Section and audience fit: the section does its rhetorical job; jargon matches audience and journal.
- Skimmability: a busy editor or reviewer should be able to grasp the point quickly from the opening sentences and any cited display.
- Integrity: claims, numbers, citations, equations, variables, and markup remain intact.
- Cross-section consistency: numbers in abstract match text, tables, and figures; claims in Discussion answer the Introduction's question.

## Pass Definitions

- **request minimum inputs**: Ask only for the smallest missing set needed to proceed. Do not draft around missing facts.
- **sentence pass**: Cut clutter, strengthen verbs, undo nominalizations, enforce parallelism, and vary sentence length and structure. Ask "WHO does what to whom?" only when active voice would improve clarity; keep purposeful passive in Methods or when the actor is irrelevant.
- **paragraph pass**: One idea per paragraph, key sentence early, first and last sentences carry the most weight. Explicit logical movement from claim to evidence to implication. Synthesize literature across studies rather than summarizing one paper at a time.
- **outline recovery**: Tag each paragraph with its one-sentence job; reorder, merge, or split before sentence-level edits.
- **outline design**: Build paragraph-level structure from the section's rhetorical requirements before drafting.
- **paragraph design**: Build paragraph structure from scratch when reordering cannot recover the logic.
- **classify**: Identify whether the reviewer comment is about wording, structure, evidence framing, missing detail, or an actual scientific concern.
- **choose stance**: State `We agree`, `We agree in part`, or `We respectfully disagree`, then support that stance with the confirmed action or reason.
- **draft**: Write the actual reviewer-response text or manuscript prose. Never claim an unconfirmed manuscript change.
- **integrity pass**: Verify meaning, claim strength, numbers, citations, equations, variables, and protected tokens. Check that numbers in prose match any referenced tables or figures.
- **fit pass**: Verify section role, audience calibration, and journal fit.
- **section-role reset**: State what the section must do per `manuscript-sections.md` and restructure to match.
- **consult one compact example**: Use one matching before/after example to set revision direction. Show it only when the user explicitly asked for examples or rationale.
- **tone check**: Keep reviewer responses grateful, specific, and technical rather than defensive.
- **review**: Re-read the full output as a critical reviewer, assign a score using the Iteration Loop rubric, and note only the top substantive issues that still block a score above 98.

## Common Failure Modes

- Treating the task as sentence cleanup when the real problem is section fit or paragraph order.
- Letting `Results` read like narrated tables or figures instead of a take-home summary that highlights comparisons and trends.
- Letting `Discussion` start with limitations or drift into generic filler; it should open with the main finding and end with a real take-home message.
- Over-explaining `Introduction` background instead of moving briskly from known -> unknown -> question.
- Summarizing literature study-by-study instead of synthesizing patterns, conflicts, and gaps across studies.
- Producing monotonous sentence rhythm — every sentence the same length and structure, or every sentence starting with the subject.
- Writing reviewer responses that sound polite but are not numbered, traceable, or explicit about what changed.
- Expanding beyond the requested scope into grant writing, review-article planning, or lay-audience adaptation.

## Hard Constraints

- Preserve meaning, evidence, numbers, citation intent, equations, variables, and markup unless the user explicitly asks for substantive changes.
- Do not invent data, methods, results, mechanisms, references, or limitations.
- Do not silently strengthen or weaken claims.
- Never convert correlation into causation.
- Do not smooth over scientific or logical flaws. Name them, then offer the safest rewrite.
- Do not break protected tokens such as citations, LaTeX, math, URLs, placeholders, table structure, or markup.
- Do not add, remove, or swap citations for style, and do not imply source support you cannot verify from the available material.
- Prefer active voice by default, but preserve purposeful passive voice in Methods or when the actor is irrelevant.
- Keep key terminology stable. Repeat the right keyword rather than forcing awkward synonyms.
- Use only user-supplied journal instructions or the journal's official publisher page. Never rely on third-party summaries.
- Do not enter `Generation` unless the minimum inputs are present.
- Do not claim reviewer-requested changes were made unless the change is confirmed; otherwise use explicit placeholders.
- Flag self-plagiarism or recycled-text risk directly rather than polishing it away.

## Output Contract

- Missing minimum inputs: ask only for the missing items and stop.
- Examples-only request: return 1-3 compact examples or templates first, then one line on the pattern. Do not rewrite the user's text unless asked.
- Source text provided for polishing or rewriting: return revised text first, then brief notes only when they clarify a structural change, trade-off, or unresolved issue.
- Source text plus explicit example request: return revised text first, then at most one compact example after the main rewrite.
- Reviewer-response request: return the point-by-point response text first, then brief notes only when they clarify a concession, disagreement, or unresolved scientific risk.
- Generation with minimum inputs present: return drafted text first, then brief notes on structural choices or placeholders.
- Both writing and science problems: state the scientific risk briefly, then provide the strongest safe rewrite.
- Multiple rewrites genuinely useful: provide 2-3 options with one-line trade-offs.
- Journal lookup performed: state which official guidelines were applied and cite the source URL.
- Keep iteration scores and intermediate suggestions internal unless the user explicitly asks to see them.
- If the iteration loop stops at the 10-round cap: state the remaining trade-offs briefly instead of claiming perfection.

## Final Checks

- Does the revised prose still match the provided evidence and claim limits?
- Did any edit change claim strength, scope, or causality?
- If arguments or interpretation were involved, is the reasoning explicit and sound?
- If a manuscript section was targeted, is it doing the job of that section?
- If tables, figures, or cross-referenced numbers were available, do the numbers still agree locally?
- If citations or protected tokens were present and editable, are they intact and still locally aligned with the sentence?
- Is the jargon level right for the target audience and any named journal?
- If journal rules applied, were they taken from the official source or from user-supplied instructions?
- Do the abstract, text, tables, and figures agree on all reported numbers?
- If a review loop was required for the selected mode, was at least one scored iteration completed?
