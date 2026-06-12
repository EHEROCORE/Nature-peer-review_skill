# Nature Peer Review Skill

This repository contains two compatible versions of a `nature-peer-review` skill:

- a **Claude skill** version under `claude/skills/`;
- a **Codex skill** version under `codex/skills/`.

The skill is designed for Nature-family manuscript review and revision, including Nature, Nature Medicine, Nature Communications, Nature Methods, Nature Biotechnology and related journals.

## Repository Layout

```text
.
├── claude/
│   └── skills/
│       └── nature-peer-review/
├── codex/
│   └── skills/
│       └── nature-peer-review/
└── docs/
    └── nature_peer_review_codex_skill.md
```

## What the Skill Does

`nature-peer-review` combines a standard scientific peer-review workflow with Nature-family-specific overlays:

1. **Advance bar**: asks whether the manuscript is a meaningful advance for a broad audience.
2. **Audience breadth**: checks whether title, abstract, introduction, Results and Discussion are readable outside the narrow specialty.
3. **Reporting Summary / Editorial Policy**: audits confidence intervals, sample sizes, statistical tests, multiple testing, ethics, data/code availability and study-specific reporting standards.
4. **Reviewer tone**: produces specific, falsifiable, proportionate comments framed around the minimum convincing fix.

## Claude Version

Claude-compatible files are in:

```text
claude/skills/nature-peer-review/
```

The Claude `nature-peer-review` skill is designed as an overlay that extends a generic `peer-review` skill. This repository now ships only the Nature overlay. If your Claude setup does not already include `peer-review`, install that parent skill separately or adapt the Nature overlay as a standalone workflow.

Typical invocation:

```text
/nature-peer-review manuscript.tex
```

or:

```text
Use nature-peer-review skill to review this manuscript for Nature Medicine.
```

## Codex Version

Codex-compatible files are in:

```text
codex/skills/nature-peer-review/
```

The Codex version is standalone and uses Codex-compatible frontmatter. It removes Claude-specific fields such as `allowed-tools`, `metadata` and `extends`, and includes copied reporting references in its own `references/` folder.

To install into a Codex project, copy:

```text
codex/skills/nature-peer-review/
```

to:

```text
<your-project>/.agents/skills/nature-peer-review/
```

Typical invocation:

```text
Use nature-peer-review to review overleaf_template/main.tex for Nature Medicine.
```

For revision tasks:

```text
Use nature-peer-review to revise overleaf_template/main.tex according to the attached reviewer comments.
Create a new revised tex file and do not overwrite the original.
```

## Included References

The skill includes:

- Nature reviewer guidelines;
- Nature Reporting Summary reviewer-time checklist;
- Nature-family journal expectations;
- generic reporting standards such as STROBE, CONSORT, PRISMA and TRIPOD;
- common methodological and statistical issues;
- a Nature-style reviewer report template.

## Recommended Use Cases

- Pre-submission Nature-family manuscript critique.
- Reviewer #2-style stress testing.
- Statistical reporting and confidence-interval audit.
- Figure and caption audit for Nature-style main figures.
- Overleaf / LaTeX manuscript revision while preserving the original file.
- Response-to-review planning.

## Notes

- The skill should not fabricate citations.
- Placeholder references should remain explicit until replaced by verified BibTeX.
- The skill is intentionally strict about confidence intervals, reference categories, sample sizes, multiple testing and external-validation limits.
- For observational clinical and cohort manuscripts, it emphasizes STROBE and TRIPOD-relevant reporting.
