# Stage 4 - refine (holistic + de-AI pass)

## INPUT
- sections/*.tex after write (all within bands after the write-stage expansion).

## DECISIONS
- De-AI scan (grep): no em-dashes (---), no moreover/furthermore/additionally stacks, no delve/crucial/pivotal/landscape/tapestry/robust/nuanced/underscore/showcase, no "in order to". Fixed: "not only" (theoretical_framework, conclusion), "leverage" (discussion).
- Triads: reviewed all "x, y, and z" lists; kept those that list source variables or construct categories; rewrote mechanical ones (evidence "mixed, descriptive, inconsistent"; Jaakkola "identifies, specifies, explains"; complaint "audience, risk, what they ask"; duplicated Trevino "individual, group, organizational" in lit review).
- Redundancy: removed a duplicate Van Dyne citation sentence in lit review theme C.
- Attribution tightening: Yang et al. 2022 ("which the authors interpret as corrective behavior"); Coyle-Shapiro 2019 ("among directions needing research", not "most promising"); Xiao & Wong-On-Wing ("a study", not "experimental"); "In our reading" added to an unsourced assessment of the Gen Z ethics literature; overclaim "most often attributed" softened.
- Terminology held constant: ideological contract breach, promise publicity, felt ethical violation, internal voice safety, internal/public ethical voice, exit, silence, venue congruence, cohort account, career-stage account.

## OUTPUT
- draft_lint ok:true; citations_lint ok:true (0 issues, 2 non-fatal band warnings); reflow_tex applied.
