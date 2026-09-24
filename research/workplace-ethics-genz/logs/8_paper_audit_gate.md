# paper-audit - gate mode

Skill: paper-audit v6.0 (standalone install; sibling writing skills not installed -> limited coverage).
Delivery level: T1 (default). Execution: sequential single-agent (no delegated reviewers).
Command: `uv run python -B scripts/audit.py <paper> --mode gate`

## Run 1 - main.tex as assembled (NOT a valid full-paper result)
Verdict printed: PASS. The audit scripts do not expand \input, and main.tex pulls every section in via \input{build/*.proc}, so this run only saw the preamble, title block and abstract. Reported for completeness; not used as the gate result.
Findings in run 1: [PRESUBMISSION][A1] abstract five-element check incomplete (missing background, objective, results); [PRESUBMISSION][G2] long paragraph at line 31 (abstract, 209 words, 7 sentences).

## Run 2 - main_flat.tex (same document, \input files inlined; PDF text verified identical, 25 pages)
### Verdict: FAIL

### Blocker (failed checklist item) [Script]
- Acronyms defined on first use: FAIL. Potentially undefined: UK, SPEC, TBD, EMAIL, FIGURE.
  - UK: main_flat.tex lines 45 and 221 ("A UK practitioner survey"), prose, never expanded.
  - TBD, EMAIL: line 25, author block placeholders "[AUTHORS TBD]", "[Affiliation TBD]", "[CORRESPONDING EMAIL TBD]" (no author details were supplied).
  - SPEC, FIGURE: line 123, LaTeX comment "%% FIGURE-SPEC type=framework" left in the figure source (not rendered in the PDF, but present in the .tex).

### Checklist items that passed [Script]
No placeholder text (TODO, FIXME, XXX); all figures referenced; all tables referenced; anonymous submission check; consistent math notation.

### Advisory (non-blocking) [Script]
- [REFERENCES] line 120: \ref{fig:model} appears before \label definition at line 154 (forward reference).
- [PRESUBMISSION][A1] abstract five-element check incomplete: missing background, objective, results.
- [PRESUBMISSION][G2] long paragraphs (5): line 31 abstract (209 words, 7 sentences); line 38 introduction paragraph 1 (200 words, 8 sentences); line 51 introduction contribution list (215 words, 6 sentences); line 90 literature review closing paragraph (182 words, 8 sentences); line 107 theoretical framework, second EVL paragraph (196 words, 7 sentences).
- [PRESUBMISSION][L1] 124 citations without a non-breaking tie before \citep/\citet, at main_flat.tex lines: 39 (x3), 41 (x3), 43 (x2), 45 (x3), 47 (x2), 52 (x2), 53 (x2), 54 (x2), 62, 64 (x3), 66 (x2), 72 (x5), 74 (x3), 76, 80 (x6), 82 (x3), 84 (x2), 86 (x3), 90, 95 (x3), 99, 101, 105 (x3), 107, 111 (x3), 159 (x2), 161 (x2), 163 (x2), 165 (x2), 167 (x2), 169 (x3), 173, 175 (x2), 181 (x2), 187, 189 (x3), 199 (x5), 201, 211 (x4), 221, 223, 225 (x3), 231, 238 (x3), 240 (x2), 242 (x2), 248 (x2), 250 (x2), 252, 258 (x6), 260 (x2), 262, 270 (x2), 272, 276.

### Checks that did not run (missing evidence) [Script]
- format, bib, figures, pseudocode: "script not found" (they live in sibling skills - latex-paper-en etc. - that were not installed; only paper-audit was copied, as instructed at setup).
- visual: not applicable to .tex.

## EIC screening (Phase 0.5) [LLM, sequential single-agent; the screener is the same model that drafted the paper, so treat as a self-assessment]
```json
{
  "reviewer": "editor_in_chief",
  "screening_scores": {"pitch_quality": 7.0, "venue_fit": 7.0, "fatal_flaw_detection": 8.0, "presentation_baseline": 6.0},
  "weighted_score": 7.1,
  "verdict": "Pass to Review",
  "fatal_flaws": [],
  "justification": "The research question (where employees take an ethical complaint after an employer breaks an ethical commitment, and whether the Generation Z pattern is cohort or career stage) is identifiable by the second sentence of the abstract and restated in the introduction, and the two grounding theories are named and fit the question. No overclaims were found in the abstract or introduction: every novel element is labelled as a proposition. Venue fit cannot be fully judged because no target journal was named and the manuscript uses a generic layout; the content fits conceptual work in organizational behavior, HRM and business ethics outlets. Presentation falls short of a submission baseline because the author block holds placeholders and the abstract, by design, has no results element.",
  "desk_reject_risks": [
    {"dimension": "pitch_quality", "concern": "The abstract opens by critiquing the prior framing before stating the paper's own question; a busy editor may read the first sentence as a negative rather than a hook.", "severity": "minor"},
    {"dimension": "fatal_flaw_detection", "concern": "The motivating Generation Z channel pattern rests on a single non-peer-reviewed practitioner survey of stated intentions; the paper discloses this, but an editor may question whether the phenomenon is established enough to theorize.", "severity": "moderate"},
    {"dimension": "venue_fit", "concern": "No target journal and a generic article layout; the manuscript would need reformatting to a specific outlet.", "severity": "minor"},
    {"dimension": "presentation_baseline", "concern": "Author, affiliation and email placeholders in the title block; abstract lacks a results element (inherent to a conceptual paper, but flagged by the five-element check).", "severity": "minor"}
  ]
}
```
Weighted score: 0.3*7.0 + 0.2*7.0 + 0.3*8.0 + 0.2*6.0 = 7.1 -> Pass to Review (not a gate blocker).

## Raw gate output (run 2)
```
[audit] File: main_flat.tex | Format: .tex | Language: en | Mode: gate
[audit] SKIP format: script not found
[audit] SKIP bib: script not found
[audit] SKIP figures: script not found
[audit] SKIP pseudocode: script not found
[audit] RUN references: check_references.py (origin=audit, own)
[audit] SKIP visual: not applicable to .tex
[audit] RUN presubmission: pre_submission_check.py (origin=audit, own)
[audit] references: 1 issues found
[audit] presubmission: 130 issues found

# Quality Gate Report

**File**: `/home/user/reaserch-/research/workplace-ethics-genz/main_flat.tex` | **Language**: EN
**Generated**: 2026-09-24 09:20

## Verdict: FAIL

## Checklist

- [PASS] No placeholder text (TODO, FIXME, XXX)
- [PASS] All figures referenced in text
- [PASS] All tables referenced in text
- [PASS] Anonymous submission (blind review check)
- [PASS] Consistent math notation
- [FAIL] Acronyms defined on first use
  - Potentially undefined: ['UK', 'SPEC', 'TBD', 'EMAIL', 'FIGURE']

## Advisory Recommendations (non-blocking)

These are advisory recommendations, not submission blockers.

- [INFO] **[REFERENCES]** (Line 120) Reference before definition: \ref{fig:model} at line 120 appears before label definition at line 154
- [INFO] **[PRESUBMISSION]** [A1] Abstract five-element check is incomplete; missing background, objective, results.
- [INFO] **[PRESUBMISSION]** (Line 31) [G2] Long paragraph detected (209 words, 7 sentences); split or add a clearer topic sentence.
- [INFO] **[PRESUBMISSION]** (Line 38) [G2] Long paragraph detected (200 words, 8 sentences); split or add a clearer topic sentence.
- [INFO] **[PRESUBMISSION]** (Line 51) [G2] Long paragraph detected (215 words, 6 sentences); split or add a clearer topic sentence.
- [INFO] **[PRESUBMISSION]** (Line 90) [G2] Long paragraph detected (182 words, 8 sentences); split or add a clearer topic sentence.
- [INFO] **[PRESUBMISSION]** (Line 107) [G2] Long paragraph detected (196 words, 7 sentences); split or add a clearer topic sentence.
- [INFO] **[PRESUBMISSION]** (Line 39) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 39) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 39) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 41) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 41) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 41) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 43) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 43) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 45) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 45) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 45) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 47) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 47) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 52) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 52) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 53) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 53) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 54) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 54) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 62) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 64) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 64) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 64) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 66) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 66) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 72) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 72) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 72) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 72) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 72) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 74) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 74) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 74) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 76) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 80) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 80) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 80) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 80) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 80) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 80) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 82) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 82) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 82) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 84) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 84) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 86) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 86) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 86) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 90) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 95) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 95) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 95) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 99) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 101) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 105) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 105) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 105) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 107) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 111) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 111) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 111) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 159) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 159) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 161) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 161) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 163) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 163) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 165) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 165) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 167) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 167) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 169) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 169) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 169) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 173) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 175) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 175) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 181) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 181) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 187) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 189) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 189) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 189) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 199) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 199) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 199) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 199) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 199) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 201) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 211) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 211) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 211) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 211) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 221) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 223) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 225) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 225) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 225) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 231) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 238) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 238) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 238) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 240) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 240) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 242) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 242) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 248) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 248) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 250) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 250) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 252) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 258) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 258) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 258) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 258) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 258) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 258) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 260) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 260) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 262) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 270) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 270) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 272) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
- [INFO] **[PRESUBMISSION]** (Line 276) [L1] LaTeX citation should use a non-breaking tie before citation, e.g. `Method~\cite{key}`.
```

---

# Re-run after the user's go-ahead (refine round 2)

## Changes made (refine, targeted at the gate report)
Blocker fixes (acronyms defined on first use):
- "UK" (two places) -> "in the United Kingdom".
- "TBD" / "EMAIL" came from the author-block placeholders -> title page anonymized for double-blind review (main.tex.tmpl), as in paper 2. Author details can be added at submission.
- "SPEC" / "FIGURE" came from the leftover "%% FIGURE-SPEC" source comment -> removed with its "%% DESC" line.
Advisory fixes:
- [L1] 124 non-breaking ties added before \citep/\citet (exactly the 124 flagged instances).
- [G2] long paragraphs split at existing topic breaks (introduction paragraph 1; theory exit-voice-loyalty paragraph and alternatives paragraph; literature review closing paragraph; model P1 rationale paragraph, with one sentence moved up next to the argument it contrasts; discussion measurement paragraph); blank lines added between the three contribution items; abstract tightened from 206 to 171 words (template linter floor 170). No content added or removed beyond the abstract wording.
Not changed: [A1] abstract elements (no results exist in a conceptual paper); the conclusion (template requires one paragraph of 200-320 words); the forward figure reference; the title (still awaiting the author's decision).

## Result (main_flat.tex, PDF text verified identical to main.pdf, 25 pages)
### Verdict: PASS (was FAIL)
```
[audit] File: main_flat.tex | Format: .tex | Language: en | Mode: gate
[audit] SKIP format: script not found
[audit] SKIP bib: script not found
[audit] SKIP figures: script not found
[audit] SKIP pseudocode: script not found
[audit] RUN references: check_references.py (origin=audit, own)
[audit] SKIP visual: not applicable to .tex
[audit] RUN presubmission: pre_submission_check.py (origin=audit, own)
[audit] references: 1 issues found
[audit] presubmission: 3 issues found

# Quality Gate Report

**File**: `/home/user/reaserch-/research/workplace-ethics-genz/main_flat.tex` | **Language**: EN
**Generated**: 2026-09-24 10:07

## Verdict: PASS

## Checklist

- [PASS] No placeholder text (TODO, FIXME, XXX)
- [PASS] All figures referenced in text
- [PASS] All tables referenced in text
- [PASS] Anonymous submission (blind review check)
- [PASS] Consistent math notation
- [PASS] Acronyms defined on first use

## Advisory Recommendations (non-blocking)

These are advisory recommendations, not submission blockers.

- [INFO] **[REFERENCES]** (Line 132) Reference before definition: \ref{fig:model} at line 132 appears before label definition at line 164
- [INFO] **[PRESUBMISSION]** [A1] Abstract five-element check is incomplete; missing background, objective, results.
- [INFO] **[PRESUBMISSION]** (Line 134) [G2] Long paragraph detected (358 words, 5 sentences); split or add a clearer topic sentence.
- [INFO] **[PRESUBMISSION]** (Line 294) [G2] Long paragraph detected (221 words, 7 sentences); split or add a clearer topic sentence.
```
Notes on the remaining advisories: line 132 is the forward reference to Figure 1; line 134 is the figure environment (TikZ source plus caption read as one paragraph by the heuristic); line 294 is the conclusion. draft_lint ok, citations_lint ok (2 unchanged band warnings), run_gates all passed, LaTeX 0 errors.
