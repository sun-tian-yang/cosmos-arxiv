# Citation-fit rubric

Use this rubric before drafting citation-request emails.

## Mandatory full-text check

Before deciding that a paper needs a citation request, open or download the target paper and inspect the full text enough to answer four questions:

1. What is the paper's main contribution?
2. Where would the user's anchor paper naturally belong: introduction, related work, method, analysis, or discussion?
3. Does the paper already cite Tian-Yang Sun, key coauthors, the relevant anchor-paper title, or the anchor arXiv ID?
4. Does the reference list cite nearby work where the anchor paper would be contextually appropriate?

Do not mark a fit as `strong` from the arXiv listing, abstract, title, or keyword overlap alone. If full text or references cannot be checked, write `正文未核查，暂不建议发引用请求` and do not draft an email.

When reporting the main contribution in a daily briefing, use Chinese. Translate technical terms into Chinese first; include English only in parentheses when it materially helps disambiguation.

## Strong fit

Draft an email when at least two conditions hold:

- The target paper's core topic overlaps directly with one of Tian-Yang Sun's anchor papers, not just the broad field.
- The target paper has an introduction, related-work, or methods paragraph where the anchor paper would naturally belong.
- The target paper cites nearby literature but appears not to cite the anchor paper.
- The anchor paper is recent, peer-reviewed or arXiv-visible, and provides context, method, benchmark, or review value.

Examples:

- A GW standard-siren cosmology paper that does not cite a recent GW standard-siren review coauthored by Tian-Yang Sun.
- A 21-cm likelihood-free / SBI / normalizing-flow paper that discusses 21-cm SBI examples but does not cite Tian-Yang Sun's 21-cm forest likelihood-free inference paper.
- A GW parameter-inference paper using neural posterior estimation or normalizing flows that discusses rapid ML inference and does not cite directly related Tian-Yang Sun GW inference work.

## Weak or conditional fit

Do not draft by default. Mention that a request is only reasonable if the target paper has a broad related-work scope.

Examples:

- Same method family but different observable or data regime.
- Same cosmological probe but different inference technique.
- A large collaboration catalog/result paper with strict collaboration citation conventions.

## Not recommended

Do not draft an email when the relation is only keyword-level, when the target paper is mostly theory/phenomenology unrelated to the user's method, or when the user's work would not help readers understand the target paper.

## Reference-check habits

When possible, inspect the PDF or text for:

- `Tian-Yang Sun`, `Sun`, key coauthors, and exact arXiv IDs.
- Title fragments from the anchor paper.
- Nearby citations that show where the user's work could fit.

If the PDF cannot be inspected, say the recommendation is provisional.
