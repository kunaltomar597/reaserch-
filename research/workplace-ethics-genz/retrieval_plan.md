# Retrieval plan and verification record (ts-paper-cite)

Verification route: api.crossref.org, api.openalex.org and api.semanticscholar.org are blocked by this environment's egress policy (sandbox curl and WebFetch both returned EGRESS_BLOCKED / 403), so `doi2bib.py` and `citations_lint.py --resolve` could not run. Every entry was instead verified with one or more targeted WebSearch queries against publisher / index pages (journals.aom.org, onlinelibrary.wiley.com, journals.sagepub.com, link.springer.com, emerald.com, annualreviews.org, sciencedirect.com, psycnet, PhilPapers, RePEc, university repositories). Authors, year, title, journal, volume, issue, pages and DOI were checked against the search results; fields that could not be confirmed were omitted rather than guessed.

## Angles searched (query packs)
1. core / literal idea: Gen Z + whistleblowing + social media + psychological contract; Gen Z external voice (kept: Protect 2025 practitioner survey; rejected: blog/HR-magazine coverage, a student-sample Indonesian accounting study, TikTok trend journalism)
2. contrast / nearest neighbour: ideological psychological contract + online whistleblowing (kept: Yang & Fong 2026 JCOM; Deng et al. 2023; Yang, Brans & Vantilborgh 2022)
3. psychological contract foundations: Rousseau 1989, 2001; Morrison & Robinson 1997; Robinson & Morrison 2000; Zhao et al. 2007; Thompson & Bunderson 2003; Turnley & Feldman 1999; Coyle-Shapiro et al. 2019
4. exit-voice-loyalty: Hirschman 1970; Farrell 1983; Rusbult et al. 1988
5. voice / silence / safety: Morrison 2014, 2023; Morrison & Milliken 2000; Milliken et al. 2003; Van Dyne et al. 2003; Detert & Burris 2007; Detert & Edmondson 2011; Edmondson 1999; Kish-Gephart et al. 2009; Liang et al. 2012
6. whistleblowing channels: Near & Miceli 1985; Miceli, Near & Dworkin 2008; Dworkin & Baucus 1998; Kaptein 2011; Mesmer-Magnus & Viswesvaran 2005; Culiberg & Mihelic 2017; Xiao & Wong-On-Wing 2022
7. generations: Mannheim 1952; Twenge et al. 2010; Costanza et al. 2012; Parry & Urwin 2011; Lyons & Kuron 2014; Rudolph & Zacher 2017; Rudolph et al. 2018, 2021; Joshi et al. 2010
8. public promises / decoupling / employer branding / social media: Weaver et al. 1999; Bromley & Powell 2012; Backhaus & Tikoo 2004; Jones et al. 2014; Treem & Leonardi 2013; Miles & Mangold 2014; Briscoe & Gupta 2016; Trevino et al. 2006; Bauer et al. 2007
9. conceptual-paper method: Jaakkola 2020; Whetten 1989; Cornelissen 2017

## Rejected / dropped after checking
- Ravid, Costanza & Romero, "Generational differences at work? A meta-analysis and qualitative investigation" (JOB): sources disagreed on year/volume (2024 vs 2025 issue); dropped rather than cite with uncertain metadata.
- Costanza & Finkelstein 2015 (IOP): real, but one search summary misdescribed it as a meta-analysis; not needed, not cited.
- Practitioner/law-firm summaries of the Protect survey: secondary; the primary Protect page is cited instead, with no numbers reported.

## Corrections made during verification
- Cornelissen 2017 title ends "writing theory without a boilerplate" (initial recall said "boundary").
- Kish-Gephart et al. 2009 pages are 163-194 (two sources).
- Farrell 1983 DOI is 10.5465/255909 (10.5465/256220 belongs to a different article).
- Costanza et al. 2012 and Joshi et al. 2010: DOIs not confirmed by search, so entries carry a verified URL instead of a DOI.
- Mannheim 1952 page range reported as 276-320 or 276-322 by different sources; 276-320 used.
- Yang & Fong: Emerald lists it as ahead-of-print with year 2026; first names not confirmed, initials used.
