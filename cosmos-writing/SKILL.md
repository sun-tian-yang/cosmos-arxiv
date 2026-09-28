---
name: cosmos-writing
description: Review, revise, and quality-control long academic writing such as papers, books, textbooks, technical reports, and LaTeX projects. Use when Codex must inspect scientific writing from reader, editor, reviewer, expert, figure/table, typesetting, citation, formula, code, terminology consistency, publication-quality, and synchronization angles; verify literature through INSPIRE, DBLP, and documented fallback sources; enforce literature-grounded academic phrasing; produce issue and change logs; modify only after explicit user approval; and verify compilation, references, graphics, labels, captions, tables, formulas, and remote/local sync. This is a writing/document child skill for cosmos-pilot, not a research-project orchestrator.
---

# Cosmos Writing

Use this skill for deep review and controlled revision of long-form academic writing, especially LaTeX projects involving cosmology, deep learning, scientific figures, equations, code examples, citations, and multi-file Overleaf-style synchronization.

## Operating Rule

Default to **read-only review first**. Do not modify source files during the first pass unless the user explicitly asks for immediate edits. For review requests, produce a consolidated Excel issue list for user confirmation before changing the document.

When the user approves modification, batch the approved fixes in one coherent editing pass. Do not ask about every small issue one by one.

CHECKPOINT: before editing source files, confirm all of the following are true:

- the user approved edits, not just review;
- the approved issue list or scope is clear;
- the source files to edit are identified;
- the expected verification command or fallback verification method is known.

If any item is false, stay in read-only review mode.

## Literature-first writing and terminology provenance

Before drafting a new section, read representative papers that use the same
physical problem, data type, method, or journal style. Extract their section
logic, terminology, notation, and compact academic phrasing, then write an
original synthesis in the present paper's voice. Do not imitate sentences or
copy distinctive wording.

Do not invent specialist terminology, method names, physical mechanisms,
evaluation labels, or characteristic stock phrases. A new technical term or
non-obvious academic expression must either be canonical in the field or be
defined explicitly and supported by a source. If a phrase, term, or claimed
writing convention cannot be traced to a reliable paper, official release,
publisher page, or the user's project materials, flag it to the user before
putting it into the manuscript. Ordinary grammatical glue words need not be
cited; technical vocabulary and field-specific claims do.

### Citation-source order

For physics, astronomy, cosmology, and high-energy-physics papers, query
INSPIRE first. For computer-science and machine-learning conference or journal
papers, query DBLP first. Then inspect the linked formal journal, conference,
publisher, or proceedings record. Only if those routes fail may the workflow
use Crossref, arXiv, an official publisher page, ADS, or Google Scholar as a
fallback, in that order appropriate to the field. Preserve the arXiv identifier
as a preprint identifier; never treat an arXiv-only record as proof of a formal
publication. Report the source route and any unresolved or fallback citation to
the user before finalizing the bibliography.

## Required manuscript architecture

Use the following default structure unless the target journal or the user's
approved outline specifies otherwise.

### Abstract

Use the sequence: two sentences introducing the problem; one sentence beginning
with “In this work” that states the overall contribution; two sentences giving
the concrete method; two or three sentences stating the core quantitative or
physical conclusions; and one final sentence that explains the broader
significance without overstating it.

### Introduction

Move from the broad physical background to the specific physical setting, then
from that setting to the question being tested. Summarize conventional methods
and their limitations. Use the broader machine-learning or statistical context
only to motivate the method. Introduce the method used here. If prior work has
already applied that method to the same problem, give it a separate paragraph,
acknowledge what it established, identify a concrete limitation, and motivate
the present work in a collegial way. End with a precise statement of what this
paper does.

### Methods

Cover the physical meaning of the data, the dataset and selection, the
likelihood and covariance, the algorithmic principle, the concrete pipeline,
the priors and nuisance treatment, and the validation procedure. Keep physical
assumptions and computational implementation distinguishable.

### Results and discussion

The Results part first describes the figures, tables, and direct quantitative
outcomes. The Discussion part then gives the physical interpretation, compares
with established expectations and literature, and states the domain of
validity and limitations. Do not hide the primary result beneath workflow
history or internal audit details.

### Conclusion

Summarize the paper, then use two or three paragraphs for the core conclusions.
The final paragraph should state future work and limitations and end with a
carefully bounded broader implication.

## Self-review checklist

Before delivery, audit the manuscript in this order:

1. Every technical term and non-obvious phrase is canonical, defined, or
   flagged for the user.
2. Every citation exists, supports the sentence where it appears, and has a
   source route recorded as INSPIRE, DBLP, publisher/proceedings, Crossref,
   ADS, arXiv, or fallback search.
3. No citation is silently downgraded from a formal publication to an arXiv
   preprint, and no unresolved source is presented as verified.
4. The abstract follows the requested sentence functions and contains no
   unsupported number.
5. Introduction, Methods, Results/Discussion, and Conclusion have distinct
   jobs and do not repeat the same claim.
6. Equations, notation, units, figures, tables, captions, labels, and
   bibliography keys are mutually consistent.
7. All numerical claims map to a production artifact or a cited source; toy,
   smoke, bounded, and diagnostic outputs are labelled and excluded from paper
   claims.
8. Compile the document, inspect the log, rerun cross-references and BibTeX as
   needed, and visually inspect representative pages and figures.

If a check fails, report the exact item and its source route; do not silently
repair the scientific claim by changing the prose.

## Review Angles

Check the document from these angles, selecting the relevant subset for the project:

- Reader: whether explanations are understandable, prerequisites are clear, examples are reproducible, and section transitions make sense.
- Editor: grammar, punctuation, Chinese/English spacing, wording repetition, AI-like phrasing, tone consistency, and unnecessary verbosity.
- Reviewer/expert: scientific correctness, assumptions, mathematical notation, claim strength, derivation logic, terminology, and field conventions.
- Figures and tables: caption-content match, figure placement, legibility, axis labels, source attribution, figure numbering, table overflow, and whether the figure supports the surrounding text.
- LaTeX/publication quality: compile errors, warnings that indicate real layout issues, labels, refs, citations, graphics paths, float behavior, captions, tables, equations, and package compatibility.
- Code examples: hidden assumptions, shape/dimension consistency, missing boundary checks, runnable logic, and whether surrounding prose explains constraints.
- Consistency: notation such as `p(x \mid \theta)`, variable names, acronym definitions, chapter-to-chapter terminology, citation style, and caption style.
- Delivery/sync: whether local files, generated reports, compiled PDFs, and remote project state match after edits.

## Read-Only Review Workflow

1. Identify the project structure: main `.tex`, included chapter files, bibliography files, figures, generated PDFs, and sync/download scripts if present.
2. Run static checks before subjective review when practical:
   - labels vs refs, duplicate labels, missing refs
   - citation keys vs bibliography
   - graphics paths vs existing files
   - suspicious captions, table widths, equation notation, URLs, and code assumptions
3. Read enough source and rendered output to ground findings. For figures, inspect actual image/PDF pages when a visual issue is suspected.
4. Separate real problems from acceptable tradeoffs. Dense optimization-path figures or visually similar method plots may be acceptable if the surrounding explanation makes the limitation clear.
5. Produce one Excel issue list with at least:
   - ID
   - file/location
   - issue type
   - current text/object
   - suggested fix
   - reason
   - priority/severity
   - whether source edit is recommended
6. In the message to the user, summarize the major categories and ask for approval to modify. Avoid dumping large rewritten passages in chat.

## Modification Workflow

After the user clearly agrees to modify:

1. Reconfirm the intended scope from the approved issue list and latest user instruction.
2. Edit only the necessary source spans. Preserve existing style, labels, citations, and structure unless a change is required.
3. Keep changes small and auditable:
   - Fix wrong formulas or misleading notation directly.
   - Add boundary-condition text for code examples when needed.
   - Correct punctuation, spacing, captions, and table layout locally.
   - Prefer standard LaTeX forms such as `\mid` for conditional probabilities.
   - Do not replace large sections just to polish style.
4. For figures:
   - If the user says figure problems are minor or asks not to edit figures, do not edit image files.
   - Fix caption/source mismatch or surrounding explanatory text when that solves the issue.
   - Point out substantive figure defects before image replacement.
5. If the project is synchronized with an online editor, apply local edits first, then use the established sync script or workflow already present in the workspace.

## Verification Workflow

Run verification after edits, using the project's existing tools when available:

- Static scan for duplicate labels, missing refs, missing citation keys, and missing graphics.
- Targeted regex scans for the exact issues just fixed, excluding legitimate matches.
- Compile with the project's LaTeX command, normally `xelatex` for Chinese LaTeX projects; rerun if labels changed.
- Inspect compile logs. Distinguish fatal errors and newly introduced warnings from existing warnings such as single-pass unresolved citations when BibTeX was not run.
- Check table/caption/layout warnings that correspond to edited regions.
- If remote sync is involved, download the remote project after syncing and compare edited source files against local versions.
- Confirm generated artifacts exist and have plausible file sizes/timestamps.

If compilation or verification fails:

1. Report the exact failed command or check.
2. Separate pre-existing failures from failures likely introduced by the edit.
3. Do not claim the document is fixed.
4. If the failure is local and fixable within the approved scope, repair and rerun.
5. If the failure requires new scope or external state, stop and ask for confirmation.

## Excel Outputs

Produce spreadsheets for two stages:

- Before edits: issue list for confirmation.
- After edits: modification record with file, location, before, after, and reason.

Keep Excel rows concise. Group mechanical repeated edits, such as many identical conditional-probability notation fixes, into one row unless the user asks for every occurrence.

Prefer a clean workbook with frozen header row, wrapped text, reasonable column widths, and one main sheet. Verify the workbook can be opened or imported, and optionally render a preview when tooling supports it.

## Final Response

Keep the final response short and factual:

- State what was changed.
- State what was verified.
- Mention any residual non-fatal warnings or limits honestly.
- Provide links to the final Excel report and any relevant compiled or synced artifacts.

Do not claim the document is flawless unless review, compile, static checks, and sync checks all support that claim. If remaining issues are judgment calls rather than clear defects, say so explicitly.

## Red Lines

Do not:

- edit source files during a first-pass review unless the user explicitly requested immediate edits
- silently rewrite large sections for style
- treat compile success as proof of scientific correctness
- ignore figures, tables, citations, labels, or equations when the request is a full paper review
- claim remote/local sync succeeded without comparing the relevant files
- report "no issues" unless static checks, rendered output, and targeted reading support it
- overwrite user changes or unrelated files
