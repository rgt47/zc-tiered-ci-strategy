# Workflow templates by workspace type

*2026-05-07 08:57 PDT*

Four CI workflow YAML files, mapped to the four observed zzcollab
workspace types. Copy the appropriate file (or pair) to your
project's `.github/workflows/` directory.

| Workspace type | Files to copy | Source repo |
|---|---|---|
| Tool package | `r-package-compendium.yml` only (rename to `r-package.yml`) | from `alz/15-mcid-cdr` (the validate+check variant) |
| LaTeX manuscript compendium | `r-package-compendium.yml` plus `render-report.yml` | both from `alz/15-mcid-cdr` |
| Quarto compendium | `r-package-compendium.yml` plus `render-report.yml` (which now handles `.qmd` after the canonical patch) | same |
| Quarto blog post | `r-package-blog.yml` plus `blog-render.yml` | both from `qblog/14-penguins1zzcollab` |

Two notes.

First, the `r-package-compendium.yml` and `r-package-blog.yml`
files differ only in whether the `check` job is present.
Tool packages and compendia run `R CMD check`; blog posts skip it
because the package skeleton is scaffolding, not the deliverable.

Second, `blog-render.yml` (Quarto) builds the project's
`Dockerfile` in CI and runs `quarto render` inside the container.
The current `render-report.yml` (rmarkdown) does not use Docker;
it uses `r-lib/actions/setup-tinytex@v2` for the LaTeX toolchain.
Both approaches are correct for their respective workspace
types; the difference reflects the maturity of each render
toolchain in CI.

After copying, edit each file to match your project's branch
names (`main`, `master`, both) and customise the path filters in
`blog-render.yml` and `render-report.yml` if your project's
deliverable lives at a non-standard path.
