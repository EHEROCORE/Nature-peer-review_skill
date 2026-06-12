---
name: nature-peer-review
description: Nature-family manuscript peer review for Nature, Nature Medicine, Nature Communications, Nature Methods, Nature Biotechnology, and related journals. Use when the user asks Codex to review, stress-test, revise, or prepare a reviewer-style report for a Nature-family biomedical, clinical, cohort, methods, or computational manuscript; when a manuscript needs advance-bar, broad-audience, Reporting Summary, STROBE/TRIPOD/CONSORT, statistics, figure, citation, and editorial-policy checks; or when the user explicitly asks for a Nature reviewer #2 style critique.
---

# Nature-Family Peer Review

## Purpose

Review manuscripts as a hard-but-fair Nature-family reviewer. Combine the generic seven-stage scientific peer-review workflow with Nature-specific overlays: advance bar, broad-audience readability, Reporting Summary compliance, figure-statistics standards, and calibrated reviewer tone.

This Codex version is standalone. It does not rely on Claude-style `extends`, `allowed-tools`, or hard-coded `.claude` paths.

## Resource Loading

Load only the references needed for the task.

For a substantive original-research manuscript review, read these files before writing the report:

- `references/nature_reviewer_guidelines.md`
- `references/nature_reporting_summary.md`
- `references/nature_journal_family.md`
- `references/reporting_standards.md`
- `references/common_issues.md`
- `templates/nature_reviewer_report.md`

For a targeted review, load the relevant subset:

- Nature journal fit or novelty: `nature_reviewer_guidelines.md`, `nature_journal_family.md`
- Reporting/statistics audit: `nature_reporting_summary.md`, `reporting_standards.md`, `common_issues.md`
- Report formatting: `templates/nature_reviewer_report.md`

## Workflow

1. Identify the target journal, manuscript type, central claim, and user-requested output.
2. Inspect the manuscript artifact and nearby project files. For LaTeX or Overleaf projects, read the main `.tex`, bibliography, figure captions, and figure file inventory. Use `rg` to check repeated claims, placeholders, missing references, and figure paths.
3. Apply the seven-stage review:
   - initial assessment
   - section-by-section review
   - methodological and statistical rigor
   - reproducibility and transparency
   - figures and data presentation
   - ethics and reporting policies
   - writing quality and accessibility
4. Overlay Nature-family criteria at each stage:
   - advance bar: is the paper a significant advance or only technically sound?
   - audience breadth: can adjacent-field scientists understand the title, abstract, and Results?
   - reporting summary: are sample sizes, tests, CIs, multiple testing, data/code, ethics, and AI disclosure handled?
   - reviewer tone: specific, falsifiable, proportionate, and framed around the minimum convincing fix.
5. Separate blocking issues from strengthening suggestions. Do not request out-of-scope work.
6. If the user asks for revision rather than review, create a new revised file instead of overwriting the original unless explicitly asked. Keep unresolved items as explicit placeholders, not hidden claims.
7. Validate the output with static checks when possible: citation keys, figure paths, placeholder count, word count, LaTeX syntax balance, and forbidden overclaims.

## Nature-Specific Review Standards

### Advance Bar

Write an advance assessment early in the report:

> The central claim is X. If true, this would be a significant / moderate / incremental advance over Y because Z. The most plausible alternative explanation is A, and the manuscript does / does not / partially rules it out.

Reject or major-revision concerns should be tied to the central claim. For Nature Medicine, emphasize clinical or translational consequence. For Nature Communications, emphasize rigor, generality, and clarity. For Nature Methods, emphasize method utility, benchmarking, code, and reproducibility.

### Audience Breadth

Check:

- Title states the finding, not only the method.
- Abstract has a broad first sentence, a quantitative anchor, and a final meaning statement.
- Introduction builds to a gap rather than becoming a literature dump.
- Results subsection titles are claims.
- Discussion opens with what the paper changes.

### Reporting and Statistics

For every main quantitative claim, ask whether the manuscript reports:

- sample size per group or cell
- reference category or comparison frame
- effect size
- 95% confidence interval
- exact p value or corrected q value where relevant
- multiple-testing family and correction
- assumptions or non-parametric alternatives

For prediction or risk-model claims, check C-index/AUC uncertainty, model comparison, calibration, and whether TRIPOD-style reporting is appropriate.

### Figures

Nature-family figures should be self-contained:

- main message visible from the panel organization
- legends include n, test, effect size, CI, and p/q where relevant
- no duplicated placeholder figures
- no overpacked panels that hide the claim
- color palettes are restrained and interpretable

### Tone

Be direct but not performative. Each major comment should include:

- Issue
- Why it matters
- Minimum acceptable fix

Avoid vague objections, personal language, citation pressure, and unrealistic experiment requests.

## Output Format

Use the report template in `templates/nature_reviewer_report.md` unless the user asks for another format.

Default sections:

1. Summary of Contribution
2. Advance Assessment
3. Major Comments
4. Minor Comments
5. Section-by-Section Critique
6. Statistical / Methodological Reporting Checklist
7. Headline-Claim Audit
8. Reference Quality Audit
9. Suggested Key Revisions
10. Optional Confidential Comments to Editor
11. Confidence in Review

For manuscript revision tasks, produce a concise change summary and state remaining blockers clearly.

## Codex Implementation Notes

- Use `rg` first for searching manuscript text, citations, placeholders, figure references, and result numbers.
- Use `apply_patch` for manual edits.
- Preserve the original manuscript unless the user explicitly asks to overwrite it.
- For Overleaf projects, prefer creating `*_revised.tex` or similarly named files.
- Do not fabricate citations. If citations are placeholders, keep them visible or replace them only with verified BibTeX entries.
- Do not silently convert unresolved analyses into completed claims.
- If local LaTeX tools are unavailable, report that compilation was not run and provide static checks instead.
