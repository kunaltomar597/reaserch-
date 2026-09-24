# Promises Made in Public: Ethical Voice After Ideological Contract Breach and the Generation Z Question

Conceptual paper produced with the spark-to-paper `ts-paper` pipeline, run in proposal mode (no data, no numbers).

- `main.pdf`: the compiled paper (25 pages). `main.tex` is the source, and it inputs the processed sections under `build/`.
- `sections/`: section source files (edit these, then re-assemble).
- `refs.bib`: 53 references, each verified by web search (see `retrieval_plan.md`). `claims_map.json` says what each citation supports.
- `blueprint.json`: the paper plan. `story.json` / `story_proposal.md` / `idea_brief.json` / `novelty_report.json`: idea-to-story stage.
- `template.json` + `main.tex.tmpl`: a generic article-class template built for this run (no journal style imitated).
- `logs/`: per-stage input/decision/output logs. `logs/8_paper_audit_gate.md` holds the paper-audit gate result.
- `main_flat.tex`: the same document with the section inputs inlined, created only so paper-audit could read the full text.

Rebuild: `python3 ~/.claude/skills/spark-to-paper-skills/skills/ts-paper-latex/scripts/assemble_paper.py .`
