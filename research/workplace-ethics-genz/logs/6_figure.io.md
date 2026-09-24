# Figure (user-limited: one conceptual-model diagram only)

## INPUT
- FIGURE-SPEC type=framework in sections/conceptual_model.tex (fig:model).

## DECISIONS
- Image-model figure stages skipped per user instruction and because no image-model key is configured. The diagram is drawn in TikZ inside the LaTeX (born-vector, editable in source, no raster). This is a deliberate deviation from ts-paper-figure's image-model + grounding requirement; check_figure_critique / check_vector_pdf (which assume that pipeline) were not run.
- Vision critique (rendered with PyMuPDF and inspected):
  - Round 1: hyphenated labels in response boxes; P1 label collided with the moderator arrow; P2/P3 arrows landed ambiguously on a four-way fan; curved P3 arrow messy.
  - Round 2 (redesign: responses grouped as "venue of ethical voice" and "withdrawal"; internal voice safety placed between the two response paths): rival-accounts box text still hyphenated; IVS box touched the upper arrow; dotted arrow crossed the breach box.
  - Round 3: spacing/routing fixed; figure scaled to \linewidth; judged clean. Remaining accepted compromise: the dotted rival-accounts arrow to internal voice safety crosses the withdrawal arrow (unavoidable with IVS inside the wedge).

## OUTPUT
- Figure 1 in main.pdf (vector). No figures/ files needed.
