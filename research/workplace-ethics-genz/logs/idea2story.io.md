# ts-idea2story (web-search-only mode)

## INPUT
- idea: user brief; retrieval_focus = go_search_web; KG off (off-domain); embeddings off.

## DECISIONS
- idea_brief.json written with explicit vs inferred assumptions kept separate.
- Search packs: literal idea (Gen Z whistleblowing / social media / psychological contract), contrast (ideological contract + online whistleblowing), core theory (psychological contract, EVL), voice/whistleblowing channels, generational critique.
- Seed pattern: "reframe values -> venue": the channel of the response mirrors the channel of the promise; bounded by internal voice safety; Gen Z handled as rival cohort vs career-stage propositions.
- Critique round 1 (weakest axis = novelty): nearest neighbour Yang & Fong (JCOM, ahead-of-print) links ideological contracts + signaling to online whistleblowing. Response: sharpened the story to what that paper does not model (promise venue as a formation property, internal voice safety boundary, exit/silence outlets, cohort vs career-stage rivals). Faithfulness and narrative judged adequate; stopped after 1 round.
- Novelty: judgement-only (no embeddings) -> novelty_report.json verdict "proceed", risk "medium" because of the nearest neighbour.

## OUTPUT
- story.json (story_lint ok:true, 0 issues), story_proposal.md, novelty_report.json, retrieved_papers.json (53 papers; abstracts not fetched).
