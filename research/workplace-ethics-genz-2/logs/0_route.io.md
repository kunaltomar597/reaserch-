# Stage 0 - route + preflight (paper 2)

## INPUT
- Same brief as paper 1 (proposal_brief.md), with the request for a second, different paper produced the same way.

## DECISIONS
- Class (a) topic brief -> ts-idea2story (web-search only) -> plan. results_mode = proposal.
- Preflight unchanged from paper 1: no embedding endpoint (off-domain KG), no image-model key, metadata APIs blocked (WebSearch verification instead), TeX Live already installed.
- Template: conceptual_ob (article class, standard packages only), as in paper 1, with one change: the title page is anonymized for double-blind review instead of carrying "[AUTHORS TBD]" placeholders. This change was made because placeholders in paper 1's author block triggered part of paper 1's paper-audit acronym failure; it is disclosed rather than hidden.
- Other lessons from paper 1 applied while writing (not after the audit): no undefined all-caps acronyms in prose, a tie (~) before each author-year citation, paragraphs kept under about 180 words, no figure-spec comment left in the source (the figure was drawn directly in TikZ).
- Stage 5 review: Tier 3 in-context (no subagents without explicit request). Stage 8 (experiments): not applicable.
- Paper must differ from paper 1: paper 1 = voice venue after ideological contract breach; paper 2 = transmission and imprinting of enacted ethical norms under distributed entry.

## OUTPUT
- template.json, main.tex.tmpl (anonymized title page); route recorded.
