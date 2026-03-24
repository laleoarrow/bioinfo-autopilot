# Manuscript Coherence Gate

Use when polishing a full manuscript, major rewrite, long review, or article-style draft where section-level edits can create inconsistency across the paper.

## Core Rule
Do not polish sections in isolation. Keep one thesis, one evidence level, and one journal fit across the whole manuscript.

## Manuscript Map
Before the final polish, define a compact map:
- Scientific question
- Why the question matters
- What prior work missed
- What this study adds
- Main result
- Main limitation
- Clinical or scientific implication
- Target journal fit

If the map cannot be written clearly, the manuscript is not ready for final polish.

## Introduction Check
- State the broad context briefly.
- Narrow to the specific knowledge gap.
- Explain why prior work was insufficient or incomplete.
- Make the research question explicit and keep the paper's core value proposition visible.
- Match the amount of background to the target journal and article type.
- Do not bury the main problem under literature density.

## Results Check
- Keep Results factual and tied to the evidence lock.
- Maintain the same naming, ordering, and direction of effect as the figures and tables.
- Do not introduce interpretation that belongs in the Discussion.

## Discussion Check
- Open with the key finding and the answer to the main scientific question, not a recap of every result.
- Explain how the finding fits with prior work.
- Distinguish confirmation, extension, and contradiction.
- State limitations plainly.
- State implications only to the extent supported by the evidence.
- End with a proportionate conclusion and future direction.

## Whole-Paper Consistency Check
- Abstract, Introduction, Results, Discussion, and Conclusion should all carry the same main message.
- Terms, abbreviations, cutoffs, units, and sample counts should match across sections.
- The scientific strength of the claim should not drift between sections.
- Check transitions and sentence-level flow, especially abstract-to-introduction, results-to-discussion, and discussion-to-conclusion.
- Figure legends, tables, and main text should tell one coherent story.
- If a section was rewritten heavily, re-read the neighboring sections for flow and logic.

## Journal Fit Lens
### Nature / Cell / Science
- Lead with the conceptual advance and broad relevance.
- Keep the narrative crisp, accessible, and non-redundant.
- Avoid overexplaining familiar background or overstating novelty.

### Medical Top Journals
- Lead with the clinical or translational importance.
- Keep causality and impact claims conservative and evidence-based.
- Make limitations and evidence quality visible, not hidden.

### Review Articles
- Organize by question, mechanism, syndrome, or decision point rather than by paper sequence.
- Make uncertainty explicit.
- Balance breadth with a clear argument.

## Post-Polish Recheck
After final language polishing, rerun:
1. The evidence lock on all numerical and factual claims.
2. The section-to-section coherence check.
3. The journal-fit check for tone, emphasis, and article type.

If any new inconsistency appears, revise the manuscript again before completion.

## Agent Prompts
### Coherence Prompt
`Build a one-line manuscript map for each section. Then check whether the Introduction states the gap clearly, the Discussion starts with the key finding, and the conclusion matches the evidence. Report any drift in claim strength, terminology, or journal fit.`

### Final Verification Prompt
`After polishing, re-audit every number, denominator, effect size, and key claim against the source tables/figures, then re-check whether the Introduction, Results, Discussion, and Conclusion still tell one coherent story. Do not approve if section strength or terminology drifts.`

## Primary Sources
- How to write your paper | Nature Portfolio: https://www.nature.com/nature-portfolio/for-authors/write
- Nature computational science writing guidance: https://www.nature.com/articles/s43588-025-00847-0
- Cell Press story and simplicity guidance: https://crosstalk.cell.com/blog/getting-your-paper-published-with-as-little-frustration-as-possible-4
- Cell Press abstract guidance: https://crosstalk.cell.com/blog/how-to-hook-an-audience-with-a-great-abstract
- JAMA Instructions for Authors: https://jamanetwork.com/journals/jama/pages/instructions-for-authors
