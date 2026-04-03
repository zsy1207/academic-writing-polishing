---
name: academic-writing-polishing
description: Polish, rewrite, or draft academic manuscript prose, cover letters, or reviewer responses. Use when clarity, concision, sentence variety, verb strength, paragraph logic, section fit, journal alignment, claim calibration, literature synthesis, table/figure integration, numerical presentation, or AI-sounding phrasing are concerns.
---

# Academic Writing Polishing

## Overview

Polish, rewrite, or draft academic prose without changing the underlying science unless the user explicitly requests substantive changes backed by supplied facts. Choose the lightest mode that solves the problem, load only the needed reference sections, and stop once the text is safe, clear, and fit for purpose.

Handle one task per turn. If the user supplies multiple passages or multiple task types, process each separately and state which one you are working on.

Default audience by task type (override when the user or journal says otherwise):

- Manuscript prose → an educated scientific reader outside the exact subfield.
- Cover letters → the handling editor deciding fit and interest.
- Reviewer responses → the editor and reviewers checking traceability, accuracy, and tone.

## When Not to Use

- The task is pure translation rather than editorial writing.
- The task is fact-checking, literature search, citation gathering, or source verification only.
- The task is standalone scientific peer review, methods critique, or statistical critique with no writing objective.
- The task is a grant proposal, review-article strategy session, recommendation letter, personal statement, press release, lay summary, or media-prep request that needs domain-specific structure beyond local prose polishing.
- The user wants new conclusions, stronger claims, or speculative mechanisms not supported by supplied evidence.

## Fast Workflow

1. **Identify inputs**: source text, target section, target journal, implied audience, intervention level, and whether minimum inputs are present.
   - If the target section is not stated, infer it from rhetorical features (see Section Resolution). If ambiguous, ask.
2. **Gate check**: if minimum inputs for the matched task type are missing, enter `Intake` and ask only for the missing items. Do not proceed until all required items are confirmed.
3. **Journal check**: if a journal is named and instructions are not provided, retrieve only the official publisher guidance and apply it as a hard constraint. If retrieval fails, say so and ask the user.
4. **Route**: select one base mode from the Routing Priority (evaluate top to bottom; stop at the first match). Add `Example-guided polish` only when the user explicitly asks for examples, templates, or before/after models.
5. **Load references**: read only the sections listed in the Mode Map for the selected mode.
6. **Execute passes**: run the listed passes in the order given. Do not skip or reorder passes.
7. **Post-pass verification**: verify meaning preservation, claim strength, logic, section fit, protected tokens, and any applicable journal constraints.
8. **Review loop**: if the selected mode requires a review loop (see Review Rules), enter the Iteration Loop now.
9. **Deliver**: output following the Output Contract. Revised text first; notes brief and limited to trade-offs, risks, or missing information.

## Minimum Inputs by Task

Do not draft around missing required items. Ask only for what is missing, then wait.

| Task type | Required inputs | Conditionally required |
| --- | --- | --- |
| Polish or rewrite existing prose | Source text | Target section (if section fit matters) |
| Section drafting | Target section + topic or research question + facts or bullet points | — |
| Data-bearing section (`Abstract`, `Results`, `Discussion`) | Source text or drafting inputs + study context + main findings + claim limits | — |
| Cover letter | Manuscript title or type + key finding + target journal | Confirmed submission declarations; use placeholders if unconfirmed |
| Reviewer response (draft from scratch) | Reviewer comment + confirmed action or intended stance | Revision location if known |
| Reviewer response (polish only) | Draft response text | Reviewer comment (for context) |

## Section Resolution

When the Mode Map says "resolved section from `manuscript-sections.md`," match the user's target section to the corresponding heading:

| User's target | Read from `manuscript-sections.md` |
| --- | --- |
| Introduction | `Introduction` |
| Methods | `Methods` |
| Results | `Results` |
| Discussion | `Discussion` |
| Abstract | `Abstract` |
| Tables, figures, or displays | `Tables and figures` |
| Cover letter | `Cover letters for journal submission` |
| Multiple sections or full manuscript | Read each relevant heading; process one section at a time |

If the user does not name a section, infer from the text's rhetorical features:
- States background and ends with a question or aim → Introduction
- Describes procedures, materials, or protocols → Methods
- Reports data, cites tables or figures → Results
- Interprets findings, compares to literature, addresses limitations → Discussion
- Self-contained summary of the full study → Abstract

If still ambiguous after inference, ask the user.

## Journal Rules

1. User-supplied journal instructions are the primary authority.
2. Otherwise, use only the journal's official publisher or society page. Do not rely on third-party blogs, submission anecdotes, or aggregator summaries.
3. Extract only the constraints that matter for the current task: word limit, section structure, reference style, spelling variant, or explicit style rules.
4. If the official guidance cannot be retrieved reliably, say so and ask the user for the instructions or a direct link.
5. When journal rules are applied, state which guidelines were used and cite the source URL in the output notes.

## Routing Priority

Evaluate the conditions below in order. Stop at the first condition that matches.

1. User asks only for examples, templates, or before/after models and does not ask for live revision or drafting → `Examples-only`.
2. Minimum inputs for the requested task are missing → `Intake`.
3. No source text, generation requested, and minimum inputs present → `Generation`.
4. Reviewer-response request → `Response rewrite`.
5. Section does the wrong rhetorical job (the section exists but fails to do what that section type requires) → `Section rewrite`.
6. Logic or order is weak across sentences or paragraphs but the section role is correct → `Structural polish`.
7. None of the above → `Light polish`.

After selecting the base mode, add `Example-guided polish` as a supplementary layer only if the user explicitly wants examples, templates, before/after models, or rewrite rationale illustrated with a compact example.

Once a mode is selected, complete it before switching. If the mode turns out to be wrong mid-task, state why and switch explicitly.

## Mode Map

| Mode | Read only these sections | Run these passes in order |
| --- | --- | --- |
| Intake | none | request minimum inputs → stop |
| Examples-only | matching subsection from `academic-revision-examples.md` via the Quick Matching Guide; plus `publishing-and-review.md`: `Response to reviewers` for reviewer-response examples, or `manuscript-sections.md`: `Cover letters for journal submission` for cover-letter examples | show 1-3 examples → one-line takeaway → stop |
| Light polish | `core-editing.md`: `Cut clutter`, `Work with verbs`, `Build better sentences and paragraphs`; add `Logic and argumentation`, `Calibrate hedging`, `Present numbers effectively`, or `Micro-grammar reminders` only if the passage needs them | sentence pass → integrity pass → fit pass → review |
| Structural polish | `core-editing.md`: `Build better sentences and paragraphs`, `Logic and argumentation`, `Cut clutter`, `Work with verbs`; plus resolved section from `manuscript-sections.md` | outline recovery → paragraph pass → sentence pass → integrity pass → fit pass → review |
| Section rewrite | resolved section from `manuscript-sections.md`; matching examples from `academic-revision-examples.md` if useful | section-role reset → paragraph design → sentence pass → integrity pass → fit pass → review |
| Response rewrite | `publishing-and-review.md`: `Response to reviewers`; Section 7 of `academic-revision-examples.md` if useful | classify → choose stance → draft → tone check → integrity pass → review |
| Generation | resolved section from `manuscript-sections.md`; `core-editing.md`: `Principles`, `Build better sentences and paragraphs`, `Logic and argumentation`; add sentence-level, hedging, and numbers sections only if needed | outline design → paragraph drafting → sentence pass → integrity pass → fit pass → review |
| Example-guided polish | matching subsection from `academic-revision-examples.md` | consult one compact example → apply main mode; show the example only if the user explicitly asked |

Read only the named sections. Do not load an entire reference file unless the task genuinely needs most of it.

## Review Rules

- `Intake` and `Examples-only`: no review loop. Deliver and stop.
- `Light polish`: run the Iteration Loop with a targeted review in each cycle.
- `Structural polish`, `Section rewrite`, `Response rewrite`, and `Generation`: run the Iteration Loop with a full review in each cycle.

Definitions:
- **Substantive issue**: one that affects meaning preservation, logic, evidence-claim alignment, claim strength, section fit, journal compliance, protected-token integrity, or professional credibility.
- **Cosmetic issue**: one where the only improvement is word-choice variety, sentence-opening variation, or synonym substitution that does not affect meaning, clarity, or section fit.

Do not keep revising only to resolve cosmetic issues or chase a higher score once the text is already safe and section-fit.

## Iteration Loop

Run this cycle for every mode except `Intake` and `Examples-only`.

1. After completing all passes for the selected mode, perform a scored review. This counts as iteration 1.
2. Score on a 0-100 scale using this rubric:
   - meaning preservation and token integrity: 25
   - logic, argumentation, and literature synthesis: 20
   - section fit and audience/journal fit: 20
   - claim calibration and evidence-claim alignment: 15
   - clarity, concision, verb strength, and sentence variety: 15
   - skimmability and table/figure integration: 5
3. Score only against the requested scope. Do not penalize the output for not adding content, sections, citations, or reframings that the user did not ask for.
4. After each scored review, list only the top substantive issues that still block a score above 98.
5. Revise only those listed issues. Do not expand scope or introduce new changes beyond the listed issues.
6. Score again after each revision.
7. Stop when any of these conditions is met:
   - the score exceeds 98, or
   - the score already exceeded 98 on the first review (stop immediately; do not create stylistic variation), or
   - 10 iterations are reached (stop and report remaining trade-offs instead of claiming perfection).
8. Keep scores and intermediate suggestions internal unless the user explicitly asks to see them.

## Diagnostic Checks

Use these as a checklist during review passes. Not every check applies to every passage.

- **Clarity and concision**: clutter, nominalization, empty openings, filler, buried verbs.
- **Verbs and sentence variety**: strong verbs carry key claims; sentence length and structure vary enough to maintain rhythm; no monotonous subject-verb-object chains.
- **Logic and paragraph architecture**: one job per paragraph, key sentence early, explicit reasoning, no unsupported leaps.
- **Literature synthesis**: prior work compared and contrasted across studies, not summarized study-by-study.
- **Hedging and claim strength**: no causal overreach, no stacked hedges, qualifiers match evidence type.
- **Numbers and data**: comparison over duplication, meaningful precision, absolute risk when clearer.
- **Section and audience fit**: the section does its rhetorical job; jargon matches audience and journal.
- **Skimmability**: a busy editor or reviewer can grasp the point from opening sentences and any cited display item.
- **Integrity**: claims, numbers, citations, equations, variables, and markup remain intact.
- **Cross-section consistency**: numbers in abstract match text, tables, and figures; claims in Discussion answer the Introduction's question.

## Pass Definitions

- **request minimum inputs**: Ask only for the smallest missing set needed to proceed. Do not draft around missing facts. Stop after asking.
- **sentence pass**: Cut clutter, strengthen verbs, undo nominalizations, enforce parallelism, and vary sentence length and structure. Ask "WHO does what to whom?" only when active voice would improve clarity; keep purposeful passive in Methods or when the actor is irrelevant. After this pass, every sentence should carry its weight.
- **paragraph pass**: One idea per paragraph, key sentence early, first and last sentences carry the most weight. Explicit logical movement from claim to evidence to implication. Synthesize literature across studies rather than summarizing one paper at a time.
- **outline recovery**: Tag each paragraph with its one-sentence job; reorder, merge, or split before sentence-level edits. The goal is a logical paragraph sequence; do not polish sentences yet.
- **outline design**: Build paragraph-level structure from the section's rhetorical requirements before drafting any prose.
- **paragraph design**: Build paragraph structure from scratch when reordering cannot recover the logic.
- **classify**: Identify whether the reviewer comment is about wording, structure, evidence framing, missing detail, or an actual scientific concern. Reviewers sometimes mislabel the problem — look for the real issue underneath.
- **choose stance**: State `We agree`, `We agree in part`, or `We respectfully disagree`, then support that stance with the confirmed action or reason.
- **draft**: Write the actual reviewer-response text or manuscript prose. Never claim an unconfirmed manuscript change; use explicit placeholders instead.
- **integrity pass**: Verify meaning, claim strength, numbers, citations, equations, variables, and all protected tokens (see Protected Tokens). Check that numbers in prose match any referenced tables or figures.
- **fit pass**: Verify the section does its rhetorical job, the audience calibration is correct, and journal constraints are met.
- **section-role reset**: State what the section must do per `manuscript-sections.md` and restructure to match.
- **consult one compact example**: Use one matching before/after example to set revision direction. Show it only when the user explicitly asked for examples or rationale.
- **tone check**: Keep reviewer responses grateful, specific, and technical rather than defensive or vague.
- **review**: Re-read the full output as a critical reviewer. Assign a score using the Iteration Loop rubric. List only the top substantive issues that still block a score above 98.

## Protected Tokens

Never modify these unless the user explicitly asks:

- Citations and reference markers (e.g., `[1]`, `(Smith et al., 2024)`, `\cite{...}`)
- LaTeX commands and environments (e.g., `\begin{equation}`, `\textbf{...}`)
- Mathematical expressions and equations (e.g., `\(HR = e^{\beta_1}\)`, inline or display math)
- Variable names, statistical symbols, and units (e.g., `p < 0.05`, `β₁`, `N = 500`)
- URLs, DOIs, and hyperlinks
- Placeholders and template markers (e.g., `[confirm ...]`, `[TODO]`)
- Table structure, column alignment, and cell contents
- Figure labels and panel references (e.g., `Figure 3A`)
- Code blocks and markup syntax

During every integrity pass, scan the output for each token type above and verify it matches the input.

## Common Failure Modes

- Treating the task as sentence cleanup when the real problem is section fit or paragraph order.
- Letting `Results` read like narrated tables or figures instead of a take-home summary that highlights comparisons and trends.
- Letting `Discussion` start with limitations or drift into generic filler; it should open with the main finding and end with a real take-home message.
- Over-explaining `Introduction` background instead of moving briskly from known → unknown → question.
- Summarizing literature study-by-study instead of synthesizing patterns, conflicts, and gaps across studies.
- Producing monotonous sentence rhythm — every sentence the same length and structure, or every sentence starting with the subject.
- Writing reviewer responses that sound polite but are not numbered, traceable, or explicit about what changed.
- Expanding beyond the requested scope into grant writing, review-article planning, or lay-audience adaptation.
- Revising beyond the requested scope during the iteration loop — adding unrequested sections, citations, or content.
- Providing lengthy explanatory notes that overshadow the revised text.

## Hard Constraints

- Preserve meaning, evidence, numbers, citation intent, equations, variables, and markup unless the user explicitly asks for substantive changes.
- Do not invent data, methods, results, mechanisms, references, or limitations.
- Do not silently strengthen or weaken claims.
- Never convert correlation into causation.
- Do not smooth over scientific or logical flaws. Name them, then offer the safest rewrite.
- Do not break protected tokens (see Protected Tokens).
- Do not add, remove, or swap citations for style, and do not imply source support you cannot verify from the available material.
- Prefer active voice by default, but preserve purposeful passive voice in Methods or when the actor is irrelevant.
- Keep key terminology stable. Repeat the right keyword rather than forcing awkward synonyms.
- Use only user-supplied journal instructions or the journal's official publisher page. Never rely on third-party summaries.
- Do not enter `Generation` unless the minimum inputs are present.
- Do not claim reviewer-requested changes were made unless the change is confirmed; otherwise use explicit placeholders.
- Flag self-plagiarism or recycled-text risk directly rather than polishing it away.

When constraints conflict, prioritize in this order: (1) meaning and evidence preservation, (2) protected-token integrity, (3) section fit and journal compliance, (4) clarity and concision, (5) stylistic improvement.

## Output Contract

### Format rules

- Return revised text as the primary content. Place it first, before any notes.
- Do not wrap the revised text in labels like "Revised:" or "Output:" unless needed to disambiguate multiple versions.
- Keep notes to at most 3-5 concise bullet points. Each bullet should state one trade-off, risk, unresolved issue, or placeholder warning.
- Do not include rubric scores or iteration details in the output unless the user explicitly asks to see them.

### By task type

- **Missing minimum inputs**: ask only for the missing items and stop. Do not draft.
- **Examples-only request**: return 1-3 compact examples or templates first, then one line on the pattern. Do not rewrite the user's text unless asked.
- **Polish or rewrite**: return revised text first, then brief notes only when they clarify a structural change, trade-off, or unresolved issue.
- **Polish or rewrite with explicit example request**: return revised text first, then at most one compact example after the main rewrite.
- **Reviewer response**: return the point-by-point response text first, then brief notes only when they clarify a concession, disagreement, or unresolved scientific risk.
- **Generation**: return drafted text first, then brief notes on structural choices or placeholders.
- **Both writing and science problems detected**: state the scientific risk briefly, then provide the strongest safe rewrite.
- **Multiple rewrites genuinely useful**: provide 2-3 options with one-line trade-offs.
- **Journal lookup performed**: state which official guidelines were applied and cite the source URL.
- **Iteration loop stopped at cap**: state the remaining trade-offs briefly instead of claiming perfection.

## Final Checks

Before delivering output, verify each applicable item:

- Does the revised prose still match the provided evidence and claim limits?
- Did any edit change claim strength, scope, or causality?
- If arguments or interpretation were involved, is the reasoning explicit and sound?
- If a manuscript section was targeted, is it doing the job of that section?
- If tables, figures, or cross-referenced numbers were available, do the numbers still agree locally?
- If citations or protected tokens were present, are they intact and correctly positioned?
- Is the jargon level right for the target audience and any named journal?
- If journal rules applied, were they taken from the official source or from user-supplied instructions?
- Do the abstract, text, tables, and figures agree on all reported numbers?
- If a review loop was required for the selected mode, was at least one scored iteration completed?
- Is the output format compliant with the Output Contract?
