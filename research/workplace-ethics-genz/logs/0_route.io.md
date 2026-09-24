# Stage 0 - route + preflight

## INPUT
- User brief (condensed in ../proposal_brief.md): conceptual paper, workplace ethics x Generation Z, proposal mode, no data, max one figure, save under research/workplace-ethics-genz/.

## DECISIONS
- Class (a) bare idea / topic brief (no method, no evaluation plan, no data) -> run ts-idea2story first, then plan. results_mode = proposal.
- Preflight:
  - Version check: check_update.py printed no notice.
  - Embedding endpoint (TS_EMBED_*): not configured. Bundled KG is signal-processing (off-domain). Degraded to web-search-only idea2story (skill-sanctioned); novelty check is judgement/lexical only.
  - Image-model key (PaperBanana / TS_FIG_*): not configured. Per the user's instruction, the image-figure stages (ts-paper-figure, ts-figure-svg, ts-figure-optimize) were skipped. The single conceptual-model diagram was drawn directly in TikZ inside the LaTeX source (deterministic, vector, editable). This departs from the skill's figure pipeline (which requires an image-model render and would flag a non-image-model figure in check_figure_critique); recorded here as a deliberate, user-directed deviation.
  - Network: api.crossref.org, api.openalex.org, api.semanticscholar.org and publisher sites are blocked by the environment egress policy (curl 403; WebFetch EGRESS_BLOCKED). doi2bib.py and citations_lint --resolve cannot run. Citation verification done via WebSearch instead (see ../retrieval_plan.md).
  - LaTeX: not installed; self-provisioned via apt (texlive-latex-base/recommended/extra, fonts-recommended, bibtex-extra, latexmk).
- Template: bundled ts_iieta (signal-processing journal, unofficial) and neurips do not fit a conceptual HR/OB paper, and the user named no journal. Created `conceptual_ob` template.json + main.tex.tmpl using only the standard `article` class and standard CTAN packages (natbib/apalike, amsthm, geometry, setspace, tikz). No .sty/.cls authored, so the ts-paper-latex HARD RULE against fabricating venue styles is respected. Section list mirrors the user's requested structure.
- Stage 5 (ts-paper-review) runs by default; executed on Tier 3 (in-context) because subagents are not spawned in this session without an explicit user request.
- Stage 8 (ts-paper-experiment) not run: conceptual paper with no experiments, data or code; the user's instruction sets paper-audit gate as the post-compile step.

## OUTPUT
- template.json (conceptual_ob), main.tex.tmpl; route = idea2story -> plan -> cite -> write -> refine -> review -> (TikZ figure) -> latex -> paper-audit gate.
