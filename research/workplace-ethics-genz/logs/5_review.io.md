# Stage 5 - adversarial review (ts-paper-review)

## INPUT
- paperText: all sections + figure caption (~8,300 words). resultsMode = proposal (no results expected; judged on soundness, positioning, testability, internal consistency, unsupported claims).
- Knobs: lean (maxRounds 2, dryStop 1, verify true).
- Execution tier: Tier 3 (in-context sequential). Tier 2 (subagents) was not used because this session does not spawn subagents without an explicit user request. Honest note from the skill: Tier 3 simulates isolation; it is not equivalent to separate contexts.

## DECISIONS
rounds_run = 2 (round 2 produced no new surviving issues -> dry). Candidates filed in round 1 = 11; refuted by majority of 3 skeptic angles = 3; dropped_no_criterion = 0.

| id | severity | section | evidence_quote (verbatim, pre-fix) | close_criterion | bucket | fix |
|---|---|---|---|---|---|---|
| I-01 | major | conceptual_model | "A commitment stated publicly is explicit, repeated, and verifiable." | Acknowledge that public claims can be vague/aspirational and state the condition (specificity) under which P1's logic holds | fix-now | Sentence softened to "usually repeated and can be checked"; added paragraph on aspirational wording and specificity as a condition to measure |
| I-02 | major | conceptual_model | "The two parts make opposing predictions, so evidence that supports one counts against the other." | State in the model section that a single-period test cannot separate cohort from age | fix-now | Added caution paragraph after P5 |
| I-03 | minor | conceptual_model | "a distinction consistent with evidence that safety relates more strongly to prohibitive than to promotive voice" | Justify omission of loyalty as a response | fix-now | Added loyalty note (Farrell 1983; Van Dyne et al. 2003) |
| I-04 | minor | conceptual_model | "The moderation by promise publicity is new and untested." | Say whether breach has direct paths to responses or works through violation | fix-now | Added sentence: violation treated as proximal driver; no direct paths proposed |
| I-05 | minor | discussion | "Promise publicity has no existing measure." | Name organizational visibility as a confound for P1/P2 tests | fix-now | Added visibility paragraph |
| I-06 | minor | discussion | "Analytically, the four responses are best treated as alternatives rather than as independent outcomes" | Reconcile with co-occurring/sequential responses noted in Limitations | fix-now | Rewrote analytic paragraph: measure each response, model relative propensity |
| I-07 | minor | discussion | "Such a design gives causal leverage on Propositions 2 and 3." | Prevent publicity/specificity confound in the scenario manipulation | fix-now | Added constant-wording requirement |
| I-08 | minor | title/blueprint | "Venue Congruence and Generation Z's Ethical Voice" | Title should not imply a Gen Z-specific mechanism the model treats as an open rival question | author-required | Left for the author: the abstract states the rival-proposition framing; retitling is the author's call |
| R-01 | minor | discussion | "whose measurement and discriminant validity remain to be established" (retrospective recall bias in promise publicity) | measure before breach | refuted (already-addressed: entry-wave measurement in design 1; misreading angle agreed) | none |
| R-02 | nit | introduction/model/limitations | "It is a reason to ask the question, not evidence for an answer." (caveat repeated three times) | cut repetition | refuted (scope: repetition is deliberate honesty about the one non-peer-reviewed source) | none |
| R-03 | minor | discussion | "Where public criticism of an employer carries serious legal or social penalties" (whistleblower-protection law not discussed) | add legal-protection discussion | refuted (already-addressed as a boundary condition; severity angle agreed) | none |

Additional in-review wording fix: "leverage" removed from the I-07 sentence during the de-AI re-check ("supports causal inference").

## OUTPUT (written after fixes landed)
- Re-gate at `Thu Sep 24 09:17:41 UTC 2026` (after all fix-now edits were written to sections/*.tex):
  - draft_lint: {"ok": true, "n": 0}
  - citations_lint: {"ok": true, "n_issues": 0, "n_warnings": 2} (band warnings only)
- Final re-gate after the later de-AI/triad edits (latest edit to sections/*.tex precedes this stamp): `Thu Sep 24 09:19:34 UTC 2026`
  - draft_lint: {"ok": true, "n": 0}
  - citations_lint: {"ok": true, "n_issues": 0, "n_warnings": 2}
- Author-required: I-08 (title wording).

## Title decision (author-required item resolved)
Retitled so Generation Z is framed as the question the paper tests, not as a cause. All gates re-run after the change: run_gates all passed; paper-audit gate PASS with the same advisories as before.
