# Stage 2 - cite

## INPUT
- Claims needing support from blueprint key_arguments; retrieved_papers seed from idea2story.

## DECISIONS
- DOI resolution unavailable (Crossref/OpenAlex/S2 blocked). Each of the 53 entries verified by targeted WebSearch; metadata transcribed by hand from matched publisher/index records; unconfirmed fields omitted (Costanza 2012 and Joshi 2010 DOIs replaced by verified URLs; Rudolph 2021 issue omitted).
- Dropped: Ravid et al. (conflicting year/volume). Corrected: Cornelissen 2017 title, Farrell 1983 DOI, Kish-Gephart 2009 pages.
- Non-peer-reviewed sources: one (Protect 2025 practitioner survey), used only as motivation, no numbers reported, caveated in intro, model section, and limitations.
- claims_map.json: every cited key has a claim + support_label + section (first section where cited).

## OUTPUT
- refs.bib (53 entries, 0 stubs), claims_map.json (53), retrieval_plan.md.
- citations_lint (post-write): ok:true, 53 cited / 53 entries, 0 issues, 2 warnings (non-fatal): introduction cites 22 distinct works vs band 8-16; literature_review cites 35 vs band 18-34. Left as is: redistributing would mean deleting real support from the introduction's contribution statements.
- citations_lint --resolve: NOT RUN (blocked hosts).
