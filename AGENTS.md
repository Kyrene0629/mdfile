# Repository Guidelines

## Project Structure & Module Organization
- Root contains the working script `assignment6.R`, the R Markdown handout `Assignment 6.Rmd`, companion markdown answers, and the `smartass6.md` notes file.
- Data inputs live alongside the code: `mpls-violent-crime.csv` (crime time series) and `evaluations.csv` (course evaluations). Keep these immutable; stage new data files explicitly.
- Generated artifacts include `q1_scatterplot.png` and any PDFs you knit; place additional figures or tables in the root or a clearly named `output/` folder if you add one.

## Build, Test, and Development Commands
- Run the full analysis and regenerate derived outputs: `Rscript assignment6.R`.
- Install required R packages (tidyverse/modelr/broom stack) before running: `Rscript -e "install.packages(c('ggplot2','dplyr','modelr','purrr','broom','tidyr','readr'))"` if they are missing.
- For interactive work, open R and source the script incrementally: `source('assignment6.R')`.

## Coding Style & Naming Conventions
- Use tidyverse-friendly style: 2-space indents, `<-` for assignment, and `snake_case` object names that describe intent (e.g., `cv_results`, `mpls_crime`).
- Prefer piped workflows for readability and break long pipelines onto new lines after `|>`.
- Comment sections to explain analysis intent, not obvious syntax; keep comments current with code.
- Keep figures saved with descriptive filenames that encode the question or step (e.g., `q1_scatterplot.png`).

## Testing Guidelines
- There is no formal test suite; use `Rscript assignment6.R` as a smoke test to ensure models run end-to-end without errors.
- When adding functions, write quick checks with `stopifnot()` or small simulated examples to confirm expected output shapes and column names.
- Set seeds for any resampling (e.g., `set.seed(1000)`) to keep cross-validation results reproducible.

## Commit & Pull Request Guidelines
- Commit messages: short, imperative, and scoped (e.g., `add loocv helper`, `update cv results table`, `refresh crime plot`). Group related changes together.
- In PRs, summarize the analysis change, list generated outputs affected (plots, tables, PDFs), and note any new dependencies or data files. Include before/after screenshots for plots when practical.
- Do not commit changes to raw CSVs unless intentionally updating source data; note any data provenance in the PR description.
