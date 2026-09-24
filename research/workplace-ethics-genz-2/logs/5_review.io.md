# Stage 5 - adversarial review (paper 2)

## INPUT
- All sections + figure caption (about 8,800 words). resultsMode = proposal. Knobs: lean (maxRounds 2, dryStop 1, verify true). Execution tier: Tier 3 (in-context sequential; simulated isolation, not separate contexts).

## DECISIONS
rounds_run = 2 (round 2 on the edited text raised no new surviving issue). Round 1 candidates = 7; refuted = 2; dropped_no_criterion = 0.

| id | severity | section | evidence_quote (verbatim, pre-fix) | close_criterion | bucket | fix |
|---|---|---|---|---|---|---|
| I-01 | major | conceptual_model | "The clearer the newcomer's grasp of what the unit actually practices, the more that practice should shape the newcomer's conduct, in whichever direction it points." | Acknowledge that clarity can enable recognition/resistance; justify the average-tendency claim; name the boundary | fix-now | Added paragraph (gradual drawing-in per Ashforth & Anand; newcomers' low power and pursuit of social acceptance per Bauer et al.; strong personal commitments as boundary, repeated in Discussion) |
| I-02 | major | theoretical_framework / conceptual_model | "Recent theory adds that vicarious learning need not require silent observation" | State that social learning theory already includes learning from verbal/symbolic models and use it to ground P2 | fix-now | Added symbolic-modeling sentence (Bandura 1977) in theory and in P2 rationale |
| I-03 | minor | discussion | "The most informative field design would compare distributed and co-located entrants within the same organizations." | Address selection into distributed entry | fix-now | Added selection sentence |
| I-04 | minor | introduction | "Most organizations have, in effect, two sets of ethical norms." | Remove overgeneralization | fix-now | "Organizations convey ethical norms in two ways." |
| I-05 | minor | title | "the Ethical Imprinting of Generation Z Newcomers" | Title should not imply a Gen Z-specific cause, given P5 | author-required | Left for the author; abstract and P5 state the entry-conditions framing |
| R-01 | nit | conceptual_model | "including the gaps left by limited observation" (imprint by absence unclear) | clarify | refuted (already clear; severity) | none |
| R-02 | minor | discussion | "In units where misconduct has become normal, distance may partly protect newcomers" (could be read as endorsing distance) | clarify | refuted (already addressed: "it does nothing to change the unit") | none |

## OUTPUT (written after fixes landed)
- Re-gate at `Thu Sep 24 09:45:13 UTC 2026` after fix-now edits: draft_lint {"ok": true, "n": 0}; citations_lint {"ok": true, "n_issues": 0, "n_warnings": 0}.
- Later edits (paragraph split, boundary sentence, Bauer citation) re-gated by the final run_gates all: all gates passed.
- Author-required: I-05 (title wording).
