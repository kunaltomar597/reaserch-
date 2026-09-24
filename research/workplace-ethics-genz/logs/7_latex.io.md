# Stage 7 - latex (assemble + compile)

## INPUT
- sections/*.tex, refs.bib, blueprint.json, template.json (conceptual_ob), main.tex.tmpl.

## DECISIONS
- Attempt 1 (with --backup -> sections.bak/): compile error "Package pgfkeys Error: The key '/tikz/out' requires a value" (a TikZ style named `out` clashes with a reserved key). Minimal syntax fix: style renamed `resp`. No content change.
- Subsequent compiles after figure redraws and review fixes: 0 errors each time.
- Template post-processes: canonical headings from template.json; merge_adjacent disabled (author-year style); no tables.

## OUTPUT
- main.tex, main.pdf: 25 pages (A4, 12pt, 1.5 spacing, single column), error_count = 0, main.bbl resolves all 53 citations, 0 undefined citations/references, 0 overfull boxes.
- run_gates.py all: ALL GATES PASSED (citations_lint 0 issues; draft_lint 0 violations; check_vector_pdf and figure-critique gates pass vacuously because no image-model figures exist; latex compiled, 0 errors).
