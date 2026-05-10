# Companion compendium: zzcollab CI strategy

*2026-05-06 18:26 PDT*

This compendium accompanies the qblog post 'A tiered CI strategy
for zzcollab research compendia'. The post body lives at
`analysis/report/index.qmd`; the symlinked `index.qmd` at the
repository root exposes it to Quarto's blog listing mechanism.

## What this directory contains

The deliverable for this post is the white paper
`docs/ci-strategy-tiered-model.qmd`, a distillation of the
analytic work behind the migration described in the post body.
The white paper covers the four-workspace typology, the
verification of the synchronisation check at scale, and the
classification of failure modes observed during the multi-repo
deployment. The post body is the procedural distillation; the
white paper is the analytic source.

The same white paper is mirrored in the zzcollab repository at
`~/prj/sfw/07-zzcollab/zzcollab/docs/ci-strategy-tiered-model.md`
so both copies evolve together.

## Make targets

The standard zzcollab targets all work in this compendium:

- `make build`: build the Docker image used for local development
- `make r`: enter the Docker container with the project library
- `make render`: render `index.qmd` to HTML and PDF
- `make check`: run `R CMD check`
- `make check-renv`: validate package declarations against source

## Directory layout

```
zzcollab-ci-strategy/
  index.qmd                       symlink -> analysis/report/index.qmd
  DESCRIPTION
  Dockerfile
  Makefile
  NAMESPACE
  renv.lock
  zzcollab.yaml
  .Rprofile
  .Rbuildignore
  .gitignore
  .github/workflows/              CI workflows for this companion
  R/                              empty; this post ships no R code
  analysis/
    report/
      index.qmd                   the post body (Section 'Migrating ...')
    media/                        symlinked from media/
    data/                         empty for this post
    figures/                      empty for this post
  docs/
    README.md                     this file
    ci-strategy-tiered-model.qmd  white paper (deliverable)
    DATA_WORKFLOW_GUIDE.md        generic; kept
    ZZCOLLAB_BLOG_SETUP.md        generic; kept
    ZZCOLLAB_USER_GUIDE.md        generic; kept
  media/
    images/                       hero + 3 ambiance images
      hero.png                    Section 'Hero image'
      ambiance1.png               Section 'Objectives' (after)
      ambiance2.png               Section 'Things to Watch Out For' (before)
      ambiance3.jpg               Section 'What did we learn?' (before)
      README.md                   image attribution log
  tests/                          empty; this post ships no tests
  vignettes/                      empty
```

## How to navigate the post

The post body has the following sections, in order:

- Hero + lede
- Introduction (why the existing CI was misleading)
- Motivations (5 bullets)
- Objectives (4 verifiable end states)
- Ambiance image 1
- What is the tiered CI model?
- Prerequisites
- Migrating an existing zzcollab project (5 steps)
- Ambiance image 2
- Things to Watch Out For (6 symptom-and-fix patterns)
- Uninstall / Rollback
- Ambiance image 3
- What did we learn? (Conceptual / Technical / Gotchas)
- Limitations
- Opportunities for Improvement
- Wrapping Up + Main Takeaways
- See Also
- Reproducibility
- Let's Connect

The 'AUTHOR PROVIDES' and 'PRE-PUBLISH QA CHECKLIST' HTML comment
blocks bracket the body. They are template scaffolding, not
content; readers can ignore them.
