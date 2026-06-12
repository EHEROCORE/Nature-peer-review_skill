# Nature Peer Review Skill for Codex

This document describes the Codex-compatible version of the `nature-peer-review` skill added to this repository.

## Location

```text
.agents/skills/nature-peer-review/
├── SKILL.md
├── agents/
│   └── openai.yaml
├── references/
│   ├── common_issues.md
│   ├── nature_journal_family.md
│   ├── nature_reporting_summary.md
│   ├── nature_reviewer_guidelines.md
│   └── reporting_standards.md
└── templates/
    └── nature_reviewer_report.md
```

## Purpose

The skill helps Codex review or revise manuscripts in a Nature-family style, especially for Nature, Nature Medicine, Nature Communications, Nature Methods and related journals.

It is designed for:

- reviewer-style manuscript critique;
- pre-submission stress testing;
- Nature-family editorial fit checks;
- reporting and statistics audits;
- revision planning after reviewer comments;
- Overleaf / LaTeX manuscript revision while preserving the original file.

## What Changed from the Claude Version

The original Claude skill used Claude-specific metadata, including `allowed-tools`, `license`, `metadata` and `extends: peer-review`. Codex skills only need `name` and `description` in frontmatter, so the Codex version removes those extra fields.

The Claude version inherited a separate `peer-review` skill. The Codex version is more self-contained:

- the essential seven-stage peer-review workflow is summarized directly in `SKILL.md`;
- shared reporting references are copied into the same `references/` folder;
- Nature-specific references remain available for progressive loading;
- a Codex-facing `agents/openai.yaml` file is included.

This avoids hard-coded `.claude` paths and makes the skill portable inside this repository.

## Core Review Logic

The skill combines a generic scientific peer-review workflow with four Nature-family overlays:

1. **Advance bar**  
   Ask whether the manuscript is a meaningful advance for a broad audience, not only technically correct.

2. **Audience breadth**  
   Check whether the title, abstract, introduction, results and discussion are readable by adjacent-field scientists.

3. **Reporting Summary and Editorial Policy**  
   Check confidence intervals, sample sizes, statistical tests, multiple testing, data/code availability, ethics, AI disclosure and study-specific reporting guidelines such as STROBE or TRIPOD.

4. **Reviewer tone**  
   Write specific, falsifiable, proportionate comments framed around the minimum convincing fix.

## How to Use

Example prompt:

```text
Use nature-peer-review to review overleaf_template/main.tex for Nature Medicine.
```

For revision rather than review:

```text
Use nature-peer-review to revise overleaf_template/main.tex according to the attached reviewer comments.
Create a new revised tex file and do not overwrite the original.
```

For a targeted audit:

```text
Use nature-peer-review to check only the statistical reporting, confidence intervals and Nature Medicine fit of this manuscript.
```

## Expected Output

For review tasks, the skill defaults to a structured report with:

- Summary of contribution;
- Advance assessment;
- Major comments;
- Minor comments;
- Section-by-section critique;
- Statistical / methodological reporting checklist;
- Headline-claim audit;
- Reference quality audit;
- Suggested key revisions;
- optional confidential comments to editor.

For revision tasks, Codex should create a new file such as:

```text
overleaf_template/main_peer_review_revised.tex
```

and report:

- what changed;
- what reviewer concerns were addressed;
- which blockers remain;
- whether static checks passed.

## GitHub Upload / Commit Checklist

Before uploading this skill to GitHub, include these files:

```text
.agents/skills/nature-peer-review/SKILL.md
.agents/skills/nature-peer-review/agents/openai.yaml
.agents/skills/nature-peer-review/references/*.md
.agents/skills/nature-peer-review/templates/nature_reviewer_report.md
docs/nature_peer_review_codex_skill.md
```

Suggested commit message:

```text
Add Codex-compatible Nature peer review skill
```

## Notes

- This skill does not fabricate citations. Placeholder references should remain explicit until replaced by verified BibTeX.
- It does not require slide-deck review or visual schematic generation.
- For cohort manuscripts, it emphasizes STROBE, TRIPOD where prediction claims are made, confidence intervals, effect sizes, reference categories and selection bias.
- For Nature Medicine-style manuscripts, it should prioritize clinical relevance, reporting rigor and practical interpretability over purely technical novelty.
