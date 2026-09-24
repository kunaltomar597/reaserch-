# Stage 2 - cite (paper 2)

## INPUT
- Claims needing support per blueprint key_arguments.

## DECISIONS
- 51 references, each verified by targeted WebSearch (DOI resolution blocked). Details, rejected sources, and identifier decisions in ../retrieval_plan.md.
- Kept the introduction within its band (15 distinct works, band 8-16) and the literature review at 34 (band 18-34) by placing some citations in the model and theory sections where the claims they support are made.

## OUTPUT
- refs.bib (51, 0 stubs), claims_map.json (51).
- citations_lint: ok:true, 0 issues, 0 warnings. --resolve not run (blocked hosts).
