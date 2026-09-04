---
name: cosmos-arxiv
description: Generate the user's daily or latest-batch arXiv report by screening the official recent listings for astronomy, cosmology, gravitational waves, and relevant machine learning. Use only when the user explicitly asks for an arXiv daily report, today's arXiv report, the latest arXiv batch, or an equivalent recurring briefing. Do not use for individual-paper reading or explanation, standalone citation-fit assessment, citation-email drafting or rewriting, research-idea discussion, general literature review, or project planning, even when those tasks mention arXiv papers or the user's research.
---

# Cosmos arXiv

Use this skill only to generate an in-chat daily arXiv report from the newest official arXiv batch. Citation-fit checks and email drafts are allowed only as embedded subsections of that daily report.

## Trigger Gate

- Proceed only when the user explicitly requests a daily, today's, yesterday's, latest-batch, or recurring arXiv report.
- Do not apply this skill to a question about one named paper, even if the paper is on arXiv.
- Do not apply this skill to standalone paper explanation, method comparison, citation suitability, email writing or rewriting, literature review, project ideation, or research planning.
- Topic keywords such as cosmology, gravitational waves, 21-cm, deep learning, normalizing flows, or an arXiv ID are not sufficient triggers by themselves.
- If this skill was loaded for an out-of-scope request, stop using its workflow and answer with the appropriate paper-reading, writing, literature, or research skill instead.

## Core Workflow

0. Confirm that the task is a daily briefing.
   - Screen the newest visible arXiv batch and report relevant papers.
   - Treat citation assessment and email drafting only as optional components inside this report.
   - For every other task, do not use this skill.

1. Confirm the arXiv batch.
   - For a daily astronomy/cosmology briefing, use `https://arxiv.org/list/astro-ph/recent` as the primary official batch source, not `astro-ph.CO/new` or `astro-ph.CO/recent`. Isolate the newest visible date block and screen every non-replacement entry across all astronomy subcategories, including entries labelled `(cross-list from ...)`.
   - Then supplement that primary scan with the newest visible blocks of `gr-qc`, `cs.LG`, `stat.ML`, and `hep-ph`, deduplicating papers already listed under `astro-ph/recent`. Use category-specific `new` pages only as secondary checks.
   - Do not assume the current date equals the latest visible arXiv update.
   - Prefer `astro-ph.CO`, `gr-qc`, `astro-ph.IM`, `cs.LG`, `stat.ML`, and `hep-ph` when relevant.
   - Treat new submissions and relevant cross submissions as candidates. Explicitly label a selected cross-list with its source category. Exclude replacements unless the user explicitly asks for updated papers.
   - Before output, record the visible entry count for the date block and verify that each entry was either selected or deliberately excluded as outside the screening boundary.
   - Report an auditable count for every scanned category: visible total in the newest date block, entries actually parsed, entries excluded as replacements or outside scope, entries removed as duplicates (both cross-category and previously reported), final candidates after screening, and papers finally reported. Do not give only a combined total.
   - If the newest visible date is not the user's calendar date, state that explicitly and do not present the calendar date as the batch date.

2. Search by topic and source.
   - Deep learning/GW/SBI terms: `simulation-based inference`, `likelihood-free`, `neural posterior`, `normalizing flow`, `flow matching`, `diffusion`, `machine learning`, `gravitational wave`, `glitch`, `standard siren`.
   - Cosmology terms: `dark energy`, `dynamical dark energy`, `Quintom`, `phantom`, `DESI`, `BAO`, `CMB`, `ACT`, `SPT`, `Planck`, `Euclid`, `weak lensing`, `21-cm`, `HI intensity mapping`.
   - For Tian-Yang Sun relevance, compare against the research profile in `references/tian-yang-sun-profile.md`.

3. Deduplicate and group.
   - Use these groups unless the user requests a different structure: `Deep learning related`, `Cosmology related`, `Related to my work`.
   - If a paper is highly related to Tian-Yang Sun's work, put it in `Related to my work` and do not repeat the full entry in earlier groups.
   - If a group has no good papers, explicitly say no suitable paper was found and state the screening boundary.

4. Write each paper entry.
   - Include title, arXiv number with link, short author list, relevance judgement, and a 2-4 sentence Chinese summary.
   - Clearly distinguish direct relevance from broad method/background relevance.
   - For every paper in `Related to my work`, add one required sentence in this exact shape: `分析结果：本文与用户文章的相关程度为[高度相关/中等相关/弱相关/不相关]。本文的主要贡献为[用中文说明主要贡献，不夹杂英文术语，必要术语也要译成中文]。`
   - Keep the `主要贡献` clause fully Chinese-readable. Translate technical terms instead of leaving English phrases such as `simulation-based inference`, `normalizing flow`, `standard siren`, or `pipeline`; when unavoidable, put the English only after the Chinese term in parentheses.
   - Provide source links used, especially official arXiv pages or paper pages.
   - Prefer the user's archived daily-report format: Chinese output, grouped into the three standard groups, with each entry written as title, authors, clickable arXiv link, and a concise Chinese description of what the paper did.
   - Do not use a sparse metadata table for daily reports unless the user explicitly asks for a table.
   - Output the complete daily report directly in the final answer. Do not create a `.md`, `.docx`, PDF, JSON, or other report file unless the user explicitly asks to save/export/generate a file.

5. Within the daily report only, assess citation-request suitability for `Related to my work`.
   - Only Tian-Yang Sun papers on which he is the first author may be proposed as citation targets or included in citation-request emails. Coauthored but non-first-author papers may be used to assess topical relevance, but must not be recommended for citation.
   - When deciding whether citation is needed, do not rely on the arXiv listing or abstract alone. Open or download the paper and inspect the introduction, related-work/background, method/analysis sections, conclusion when useful, and references.
   - Search the paper text for Tian-Yang Sun, key coauthors, title keywords, and arXiv IDs from the profile.
   - Check whether the target paper already cites the relevant anchor paper. If it does, say so and do not draft an email.
   - If the paper cannot be opened or the references cannot be checked, label the citation recommendation as `正文未核查，暂不建议发引用请求`; do not label it `strong`.
   - Label the request fit as `strong`, `weak/conditional`, or `not recommended` with a concrete reason.
   - Draft an email only when the fit is strong or clearly appropriate. Do not draft one merely because keywords overlap.
   - When two Tian-Yang Sun first-author anchor papers each have a direct, distinct connection to the target paper, include both in the same citation request rather than choosing one arbitrarily. Explain each connection concisely.
   - In daily reports, after the three groups, add a final `Most relevant and citation emails` section when any `Related to my work` paper has a strong citation fit. Before declaring an email unavailable, check the submitter email exposed on the logged-in arXiv submission record. Then fall back to arXiv source, PDF, author page, or institutional profile. Always state the email source next to the address. If no verified email is found, say the email was not found instead of inventing or guessing one.

6. For automation/daily-briefing tasks.
   - Return the full report body in the final answer so the automation inbox contains readable content.
   - Treat "生成 arXiv 日报", "arxiv 日报", "整理今天 arXiv", and similar requests as requests for an in-chat report, not a file-generation request.
   - Never return an empty result. If there are few matches, say so and explain the screening boundary.
   - Do not ask the user to rerun the task.

## CHECKPOINTS And Failure Branches

STOP and state the limitation before writing the report if the official arXiv pages cannot be accessed or the visible batch date is ambiguous.

Use this fallback shape:

```text
arXiv batch status:
- official page checked:
- visible date:
- limitation:

Screening boundary:
- categories:
- search terms:
- replacements included/excluded:
```

If browsing/search fails:

1. Do not invent a daily report.
2. Use only user-provided arXiv IDs, PDFs, titles, or local files.
3. Mark the result as `source-limited`.
4. Ask for a batch page, arXiv IDs, or permission to retry only if no useful source remains.

If no relevant papers are found:

- explicitly say no suitable paper was found;
- state which categories and terms were screened;
- do not pad the report with weakly related papers.

If the task starts to require project-level decisions:

- stop at paper evidence and relevance;
- output a compact handoff summary for `cosmos-pilot`;
- do not choose validation gates, implementation plans, or final journal targets inside `cosmos-arxiv`.

## Red Lines

Do not:

- assume today's date is the latest arXiv batch date
- create a Markdown/report file for a daily briefing unless the user explicitly requests file output
- include replacements unless the user asked for updates
- draft citation-request emails from keyword overlap alone
- recommend or request citation of a Tian-Yang Sun paper for which he is not the first author
- invent, infer, or guess author emails; every email must have a stated source
- put a paper in `Related to my work` unless the connection is concrete
- claim a paper should cite the user's work without checking abstract/introduction/method/references when available
- turn every daily briefing into a project idea list

## Standard Report Shape

```text
Batch:
- arXiv categories:
- visible date:
- source links:

Deep learning related:
- [Title]
  Authors:
  arXiv:
  Summary in Chinese:

Cosmology related:
- [Title]
  Authors:
  arXiv:
  Summary in Chinese:

Related to my work:
- [Title]
  Authors:
  arXiv:
  Summary in Chinese:
  分析结果：本文与用户文章的相关程度为[高度相关/中等相关/弱相关/不相关]。本文的主要贡献为[全中文主要贡献说明]。
  Concrete connection:
  citation-request fit: strong / weak-conditional / not recommended

Most relevant and citation emails:
- most relevant paper(s):
- target email(s):
- citation email draft(s):

Screening boundary:
- included:
- excluded:
- source limitations:

Count audit:
- astro-ph: visible total / parsed / excluded / duplicate-removed / final candidates / reported
- gr-qc: visible total / parsed / excluded / duplicate-removed / final candidates / reported
- cs.LG: visible total / parsed / excluded / duplicate-removed / final candidates / reported
- stat.ML: visible total / parsed / excluded / duplicate-removed / final candidates / reported
- hep-ph: visible total / parsed / excluded / duplicate-removed / final candidates / reported
- cross-category unique total:
- previously reported arXiv IDs removed:
```

## User-Preferred Archived Daily Format

Use this format whenever the user asks for a daily/yesterday/latest arXiv整理, unless they request another layout. Keep the report primarily in Chinese and retain the three skill groups.

```text
Deep Learning Related

**NS-UNO: Neutron Star EoS Inference from an Unconstrained Number of Observations**
作者：Valeria Carvalho, Marcio Ferreira, Michal Bejger, Constanca Providencia
[arXiv:2608.30573](https://arxiv.org/abs/2608.30573)
这篇把深度集合网络和条件归一化流结合，使同一个神经后验模型能处理数量、精度不同的中子星质量半径观测。它在训练分布之外的状态方程上仍保持较好的后验校准，对观测集合规模变化下的神经推断有参考价值。
```

```text
Related To My Work

**Automated Identification and Subtraction of Gravitational-Wave Glitches Using Boundary Refinement**
作者：Mohammad Abu Thaher Chowdhury, Soumya D. Mohanty
[arXiv:2608.29295](https://arxiv.org/abs/2608.29295)
这篇提出三种 glitch 时间边界定位方法，并结合自适应样条和小波收缩进行针对性扣除。其注入测试表明，组合方法能保留约 95%--97% 的信噪比，显著优于仅用小波收缩。
分析结果：本文与用户文章的相关程度为高度相关。本文的主要贡献为自动确定引力波瞬态噪声的时间边界并进行针对性扣除，从而减少噪声处理对重叠引力波信号和参数估计的损害。
引用请求适合度：strong。
```

After the three groups, add citation emails like this when fit is strong:

```text
Most relevant and citation emails

**Automated Identification and Subtraction of Gravitational-Wave Glitches Using Boundary Refinement**
收件人：chowdm4@rpi.edu, soumya.mohanty@utrgv.edu（来源：arXiv HTML 正文作者信息）
引用锚点：arXiv:2312.08122 和 arXiv:2604.13867。前者研究地面探测器瞬态噪声下的快速参数推断，后者研究 Taiji 中 glitch 鲁棒的参数推断。
```

## Out of Scope

Do not use this skill for project ideas, paper explanations, method discussions, standalone citation decisions, standalone email writing, code implementation, validation planning, or journal selection. Those tasks must be handled independently by the appropriate specialized skill.

## Citation Email Style

Use the user's three-paragraph citation-request template only when a daily report identifies a strong citation fit:

1. Paragraph 1: congratulate the authors and give specific praise for what their paper did well. Mention the target title and arXiv ID when known.
2. Paragraph 2: introduce the user's related work, naming the exact paper title(s), arXiv ID(s), and venue/status when useful. Summarize what the user did in one or two sentences.
3. Paragraph 3: explain the concrete shared theme or technical connection, then politely ask whether they would consider citing the user's work in a future revision.

Keep the tone warm, modest, and non-accusatory. Avoid phrases that imply the authors made a mistake, such as `you missed` or `should cite`. Prefer `we would be very grateful if you would consider citing`, `given the shared theme`, and `in a future revision`.

Use `references/citation-email-template.md` for the default email shape and user-approved examples. The visible email heading should be `Suggestion for your arXiv:[target-id]`, followed by the full body in the same paragraph order as the examples. Use `references/citation-fit.md` for the decision rubric, and `references/tian-yang-sun-profile.md` for anchor papers.


