---
name: nature-peer-review
description: Nature-family (Nature / Nature Medicine / Nature Communications / Nature Methods) reviewer-style manuscript critique. Reuses the generic 7-stage peer-review framework (CONSORT/STROBE/TRIPOD/PRISMA) and overlays Nature-specific reviewer criteria — scientific advance vs incremental, broad cross-discipline accessibility, Reporting Summary compliance, Editorial Policy Checklist, statistics in figure legends, and the "hard-but-fair reviewer #2" tone Nature-family reviewers are known for. Use when reviewing manuscripts targeted at Nature-family journals or when the user explicitly asks for a Nature reviewer-style report.
allowed-tools: Read Write Edit Bash Grep Glob
license: MIT
metadata:
    skill-author: passionfadesaway@gmail.com
    extends: peer-review
---

# Nature-Family Peer Review

## Overview

A specialised peer-review skill that produces reviewer reports in the style of Nature, Nature Medicine, Nature Communications, Nature Methods and Nature Biotechnology. It inherits the systematic 7-stage workflow from the `peer-review` skill and adds the four things that distinguish a Nature-family reviewer report from a generic one:

1. **Advance bar** — "what does this paper teach us that we did not already know" beats "is this technically correct"
2. **Audience breadth** — manuscript must be intelligible to cross-discipline scientists, not just specialists
3. **Reporting Summary + Editorial Policy Checklist** — Nature-family journals enforce these; reviewers are expected to flag non-compliance
4. **Reviewer tone** — terse, specific, falsifiable; quotes line numbers; asks for **the minimum experiment that would convince me**

## When to Use This Skill

Invoke this skill when any of the following applies:

- The manuscript explicitly targets a Nature-family journal (Nature / Nat Med / Nat Comm / Nat Methods / Nat Biotech / Nat Genet / etc.)
- The user asks for a "Nature reviewer-style" or "reviewer #2 style" report
- The manuscript is in a format consistent with Nature-family submission (compressed Results, broad-audience abstract, integrated Methods at end, ≤4-5 main figures)
- The user wants to stress-test a manuscript against the hardest reasonable reviewer they might draw

For generic journal review (clinical trials, mid-tier specialty journals, methods papers without Nature framing), use the parent `peer-review` skill instead. For quantitative scoring use `scholar-evaluation`. For evidence-quality grading (GRADE / Cochrane RoB) use `scientific-critical-thinking`.

## Relationship to `peer-review`

This skill **extends** `peer-review`. It does not replace it. Specifically:

- The 7-stage workflow (Initial assessment → Section review → Methodological rigor → Reproducibility → Figures → Ethics → Writing) is inherited as-is.
- The generic reporting-standards reference from the installed parent `peer-review` skill should be reused when available.
- The common-issues catalogue from the installed parent `peer-review` skill should be reused when available.
- This skill **adds** four Nature-specific overlays: Advance Bar, Audience Breadth, Reporting Summary, and Nature Tone.
- This skill **drops** the presentation/slide-deck workflow (Stage 7 sub-section in the parent), since Nature submissions are manuscripts not slide decks.

This repository ships only the Nature overlay. If your Claude environment does not already include `peer-review`, install that parent skill separately or adapt this overlay as a standalone workflow.

---

## Inherited Workflow (from `peer-review`)

Run all seven stages from the parent skill, but with the Nature overlays described below applied at each stage.

| Stage | Inherited purpose | Nature overlay |
|---|---|---|
| 1. Initial assessment | High-level evaluation | **Advance Bar** — does this clear the "significant advance for a broad audience" threshold? |
| 2. Section-by-section review | Section critique | **Audience Breadth** — every section judged for cross-discipline intelligibility; **strict word/figure limits** check |
| 3. Methodological/statistical rigor | Stats and design | **Statistics-in-figure-legends** check; **n per subgroup** required; **CIs not just p-values**; **multiple-testing policy stated and applied** |
| 4. Reproducibility/transparency | Data and code | **Reporting Summary** + **Editorial Policy Checklist** + **Code/Data Availability statement** compliance |
| 5. Figures and data presentation | Visualisation | **Statistical reporting inside figure legends** (n, test, effect size, CI, exact p); **panel limit**; **caption self-containment** |
| 6. Ethics | IRB / consent | UK Biobank / consortium ethics statements; competing interests; AI/LLM disclosure |
| 7. Writing quality | Clarity | **No jargon without definition**; **Title ≤ 15 words**; **Abstract ≤ 200 words (Nature) or ≤ 250 (Nat Med / Nat Comm)**; **First sentence accessible to a non-specialist** |

Detailed stage-by-stage criteria live in the installed parent `peer-review` skill. Do not duplicate that detail when running this skill; load the parent skill and this Nature overlay together when the parent is available.

---

## Nature Overlay 1 — Advance Bar

A Nature-family reviewer's first job is not to check that the work is correct. It is to decide whether the work is **interesting enough to be in this journal**. Apply these tests:

### The "would I tell a colleague about this paper" test
- Is there a finding that a non-specialist would find surprising or counter-intuitive?
- Does the paper change how someone in an adjacent field would think about the topic?
- Would the paper be cited in textbooks, reviews, or grant applications in 5 years?

### The "incremental vs significant advance" axis
Reject incremental work even if technically clean. Look for:
- **Genuine novelty**: a method, dataset, finding or framework that did not exist before. Not "an extension of X to Y".
- **Quantitative magnitude**: not just "statistically significant" but "biologically/clinically large enough to matter".
- **Generalisability**: works in more than one cohort/condition/system, OR has a clear mechanism that explains why it should generalise.

### The "alternative explanation" stress test
For the main claim, ask: *what is the most plausible alternative explanation, and has the paper ruled it out?* If the answer is "no", flag as Major.

### Output for Stage 1
Write the advance assessment as a single paragraph at the top of the report, structured as:

> *"The central claim is X. If true, this would be a [significant / moderate / incremental] advance over [specific prior work], because [why it changes the field]. The most plausible alternative explanation is Y, and the manuscript [does / does not] adequately rule it out."*

---

## Nature Overlay 2 — Audience Breadth

Nature-family journals serve broad readerships. A specialist-only paper is rejected on accessibility grounds even if scientifically excellent. Apply these checks:

### Abstract
- [ ] First sentence understandable to a scientist outside the specific subfield
- [ ] No undefined acronyms in the abstract
- [ ] Quantitative anchor included (effect size, N, key number)
- [ ] One-sentence "why it matters" near the end
- [ ] Word count: **Nature ≤ 200**; **Nat Med / Nat Comm ≤ 250**; **Nat Methods ≤ 200**

### Title
- [ ] ≤ 15 words (Nature: ≤ 90 characters strongly preferred)
- [ ] No colons unless they add clarity
- [ ] States the finding, not the method
- [ ] Comprehensible without specialist knowledge

### Introduction
- [ ] First paragraph readable by anyone with an undergraduate science degree
- [ ] Two-paragraph build to specific gap (NOT a textbook chapter)
- [ ] Last paragraph states the advance, not the contents of the paper
- [ ] Avoid "we hypothesised that..." in favour of "we asked whether..."

### Results
- [ ] Each subsection has a verbal claim title (not "Figure 2 results")
- [ ] First sentence of each subsection states the result, not the experimental setup
- [ ] Numbers are foreground; methods are background

### Discussion
- [ ] Opens with the answer, not a recap
- [ ] Explicitly states what the paper changes about prior thinking
- [ ] Limitations as concrete numbered items, not handwaving

---

## Nature Overlay 3 — Reporting Summary + Editorial Policy Checklist

Nature-family journals require authors to complete the Reporting Summary at acceptance. Reviewers are expected to flag absences during review. See `references/nature_reporting_summary.md` for the full checklist. Headline items:

### Statistics section (mandatory in every paper)
- [ ] Sample sizes per condition / cell / subgroup explicitly stated
- [ ] Statistical test named for every comparison (not "appropriate tests were used")
- [ ] Effect sizes and 95% CIs reported alongside p-values
- [ ] Multiple-testing correction stated and applied
- [ ] Replicates: technical vs biological distinguished
- [ ] Test assumptions checked (normality, homoscedasticity) or non-parametric used
- [ ] Exact p-values reported (not "p < 0.05") except when < 0.001

### Software and code
- [ ] All software versions listed
- [ ] Custom code deposited in public repository with DOI (Zenodo recommended)
- [ ] Reasonable instruction to reproduce key figures

### Data availability
- [ ] Statement is concrete, not "available upon request"
- [ ] Accession numbers for any deposited data
- [ ] Restrictions justified (e.g., patient consent terms)

### Reagents (when applicable)
- [ ] Antibodies validated with citation or knockout/knockdown
- [ ] Cell lines authenticated, mycoplasma-tested
- [ ] Animal sources, sex, age, weight, housing reported (ARRIVE)
- [ ] Human participant ethics and consent reported

### AI / LLM disclosure
- [ ] Any use of generative AI in writing, code, or figures disclosed in Methods

---

## Nature Overlay 4 — Reviewer Tone

Nature-family reviews land somewhere between *clinical* and *terse*. The standard structure for the reviewer-facing letter is:

1. **One-paragraph summary** of what the paper claims to do and the reviewer's overall recommendation
2. **Numbered major comments** — each one should, in principle, be addressable by a specific experiment or revision
3. **Numbered minor comments** — typos, clarifications, missing citations
4. Optional: **Specific questions for the authors**

Apply the following rules:

### Be specific
- Bad: *"The statistics are insufficient."*
- Good: *"Figure 2c reports a p-value but no effect size or 95% CI. Please report the mean difference (or Cohen's d / odds ratio as appropriate) with bootstrap 95% CIs for all comparisons in Fig. 2."*

### Be falsifiable
Each major comment should specify what the author could do to address it. Asking for "more rigor" is not falsifiable. Asking for "external validation in MESA with the 35-feature audit" is.

### Be proportionate
Do not request experiments outside the scope of the paper. Asking a clinical UKB paper to do animal work is bad reviewing. Asking it to validate in a second human cohort is good reviewing.

### Use the "minimum convincing experiment" framing
When requesting additional work, state the **minimum** that would change the recommendation, not a wishlist. Examples:

- *"At minimum, please report the cross-BMI inversion with prevalence-ratio 95% CIs from a single bootstrap. A full out-of-cohort replication is not required for the first revision."*
- *"At minimum, please demonstrate that the C-index improvement is statistically significant against the AgeSex+BMI+MetS reference using a likelihood-ratio test or DeLong test on bootstrapped C-indices."*

### Quote location, not vague gesture
- Bad: *"The Methods section is unclear."*
- Good: *"Methods §Statistical analysis, paragraph 2: the reference category for the Cox model is not specified. Is it within-stratum (Normal-C0 reference for Normal-C1/C2 only) or unified (Normal-C0 reference for all 9 subtypes)?"*

### Avoid the seven cardinal sins of bad reviewing
1. Personal attacks on authors
2. Demands rooted in reviewer preference rather than scientific standard
3. Out-of-scope experiments
4. Refusing to acknowledge any strengths
5. Vague criticism without action item
6. Recycled boilerplate that does not engage with the manuscript's specific content
7. Hidden agenda (citation pressure, competitor papers, undisclosed conflicts)

---

## Report Format (Nature-style)

Use this template. Full template available at `templates/nature_reviewer_report.md`.

```markdown
# Reviewer Report — [Manuscript ID or filename]

**Target venue:** [Nature / Nature Medicine / Nature Communications / etc.]
**Recommendation:** [Reject / Major revision / Minor revision / Accept]

---

## Summary of Contribution (1 paragraph)
[What the paper claims, why it would matter if true, and the reviewer's overall stance.]

---

## Advance Assessment (Nature-specific)
[Apply Overlay 1: is this a significant advance for a broad audience? Reference frame: which specific prior work does this build on, and how does it move beyond?]

---

## Major Comments
1. **[Short title].** [Issue.] [Why it matters.] [Minimum acceptable fix.]
2. **[Short title].** ...
...

---

## Minor Comments
1. [Location]. [Issue.] [Fix.]
2. ...

---

## Statistical / Reporting Checklist Audit
- [ ] CIs reported for all main effect estimates
- [ ] Multiple testing correction stated and applied
- [ ] Sample sizes per cell / subgroup reported
- [ ] Test assumptions checked or non-parametric used
- [ ] STROBE / TRIPOD / CONSORT compliance (as appropriate)
- [ ] Reporting Summary items addressed
- [ ] Data and code availability concrete

[For each unchecked item, brief one-line note on what is missing.]

---

## Reference Quality Audit
[If references contain placeholders or look thin: spot-check a sample for whether the cited *ideas* are correct, and whether any major prior work is missed.]

---

## Suggested Key Revisions (Minimum Acceptable for Resubmission)
**Must-fix (blocking):**
- ...

**Should-fix (substantially strengthens):**
- ...

**Nice-to-have:**
- ...

---

**Confidence in this review:** [High / Medium / Low]
**Reviewer expertise relevant to:** [list the specific subareas you reviewed against]
```

### Two-layer reporting (optional but recommended)
For sensitive reviews, separate:

- **For the editor (confidential):** overall recommendation, confidence, conflicts of interest, summary of major concerns
- **For the authors (visible):** numbered major and minor comments, no editorial recommendation, neutral professional tone

---

## Special Considerations for Common Nature-family Manuscript Types

### Original research articles (Nature, Nature Medicine, Nature Communications)
Apply all overlays. Emphasise advance bar and audience breadth.

### Methods papers (Nature Methods, Nature Biotechnology)
- Validation against gold standard mandatory
- Comparison to existing methods (head-to-head with numbers, not just citation)
- Code and protocol availability are hard requirements, not preferences
- Generalisability across datasets / labs / conditions
- Drop Advance Bar emphasis; substitute "Method Utility" — would a competent practitioner adopt this method, and what does it enable that prior methods did not?

### Brief Communications / Matters Arising
- Reviewer report should be proportionate to manuscript length
- One core claim, tested rigorously, is enough
- Do not demand a full-length paper's worth of validation

### Reviews and Perspectives (Nature Reviews family)
- Comprehensiveness of literature coverage critical
- Critical synthesis, not summary
- Identify gaps and forward-looking propositions
- Drop CONSORT/STROBE/TRIPOD checklists (not original research)

### Datasets / Resource papers (Scientific Data, Nature Communications resource format)
- Data quality and reusability are the contribution
- Detailed metadata documentation
- Tutorials or worked examples
- License clarity

---

## Reference Materials

### `references/nature_reviewer_guidelines.md`
Synthesised guidance from publicly available Nature-family reviewer-instruction pages: what Nature editors expect, common rejection reasons, recommendation calibration ("major revision" vs "reject").

### `references/nature_reporting_summary.md`
The Reporting Summary checklist Nature-family journals enforce at acceptance, reformulated as a reviewer-time check.

### `references/nature_journal_family.md`
Differences between Nature, Nature Medicine, Nature Communications, Nature Methods, Nature Biotechnology, Nature Genetics — what advances each looks for, format limits, audience expectations.

### `templates/nature_reviewer_report.md`
Filled-out template with placeholders matching the Report Format section above.

### Reuse from parent `peer-review` skill
- Parent reporting standards reference — CONSORT, STROBE, PRISMA, ARRIVE, MIAME, MINSEQE etc.
- Parent common-issues catalogue — methodological and statistical problems.

When the parent `peer-review` skill is installed, load both reused references when running this skill against a substantive manuscript; they are the inherited reference material.

---

## Final Checklist Before Returning a Review

- [ ] One-paragraph summary that captures the paper's claim accurately
- [ ] Overall recommendation stated and consistent with the body of the review
- [ ] Advance Bar paragraph included
- [ ] Audience Breadth comments raised where relevant
- [ ] Every Major comment has issue + impact + minimum-acceptable-fix
- [ ] Every Minor comment has location + issue + fix
- [ ] Statistical/Reporting checklist completed
- [ ] No request for out-of-scope experiments
- [ ] No personal language about authors
- [ ] Recommendation calibrated against Nature-family norms (do not give "major revision" for what is actually a "reject" or vice versa)
- [ ] Confidence statement at the end
