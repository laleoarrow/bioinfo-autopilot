# Clinical Accuracy Gate

Use when preparing clinical, epidemiologic, or biomedical manuscripts for final language polish, especially when a human or agent is being asked to refine prose after the analysis is complete.

## Workflow Order
1. Lock the evidence.
2. Map the reporting guideline.
3. Verify manuscript text against the locked evidence.
4. Polish language only after the factual layer is stable.

## Evidence Lock Checklist
- Sample size, group size, and analysis set size.
- Numerators and denominators for every percentage or rate.
- Event counts, follow-up time, person-years, and censoring logic.
- Effect estimates, confidence intervals, P values, and direction of effect.
- Units, cutoffs, thresholds, and time points.
- Labels in text, tables, figures, and supplements.
- Whether a claim is descriptive, associative, predictive, or causal.

If any item is missing or inconsistent, stop and report the mismatch before polishing.

## Guideline Map
- Randomized trials: CONSORT
- Trial protocols: SPIRIT
- Observational studies: STROBE
- Systematic reviews and meta-analyses: PRISMA
- Search reporting for systematic reviews: PRISMA-S
- Diagnostic accuracy studies: STARD
- Prognostic or prediction model studies: TRIPOD
- Systematic reviews of prediction models: TRIPOD-SRMA
- Clustered prediction models: TRIPOD-Cluster
- Case reports: CARE
- Quality improvement studies: SQUIRE
- Clinical practice guidelines: RIGHT or AGREE depending on journal requirements
- Genetic association studies: STREGA
- Mendelian randomization: STROBE-MR
- Single-cell and related omics manuscripts: the matching domain guideline plus the target journal checklist
- AI-enabled clinical trials: CONSORT-AI or SPIRIT-AI when relevant
- AI-enabled diagnostic/prognostic studies: STARD-AI or TRIPOD-LLM when relevant

When multiple guidelines could apply, choose the one that matches the main study design and add the extension only if the study really triggers it.

## Agent Prompt Pattern
### Stage 1: Evidence Lock Prompt
Use this before rewriting:

`Audit the manuscript against the locked facts table. Do not rewrite style yet. List only factual mismatches, missing denominators, inconsistent labels, unsupported claims, or guideline gaps. If everything matches, say the text is evidence-consistent.`

### Stage 2: Final Polish Prompt
Use this only after the evidence pass succeeds:

`Rewrite for a top-tier biomedical journal. Preserve every locked number, unit, cutoff, direction of effect, and citation meaning. Improve clarity, flow, and concision only. Do not add new claims, do not soften inconsistencies, and do not change the scientific strength of the conclusions. If anything is still inconsistent, return an issue block instead of polishing.`

### Stage 3: Post-Polish Recheck Prompt
Use this after a long or heavily revised manuscript:

`Re-audit the polished manuscript against the locked facts table. Confirm that no number, denominator, unit, effect size, cutoff, or direction of effect changed, and that the strength of the claim is still aligned across the abstract, Introduction, Results, Discussion, and Conclusion. Flag any drift before approval.`

## AI Use and Disclosure
- Nature-family journals state that AI-assisted copy editing for readability, style, grammar, spelling, punctuation, and tone does not need to be declared, but human accountability remains.
- JAMA requires disclosure when AI is used to create content or assist with writing or editing manuscript text.
- When the target journal is unclear, follow the stricter disclosure rule and keep a short AI-use note for the methods, acknowledgments, or internal submission record as appropriate.
  
## Long-Manuscript Sanity Check
- If the manuscript is long, run a second evidence lock after the final language pass.
- If any factual sentence was changed during language polishing, rerun the evidence lock on the affected sections even if the manuscript is not long.
- Reconcile any changes in emphasis between the abstract, Introduction, Results, Discussion, and Conclusion.
- If the rewrite strengthened or weakened the claim in one section, restore the intended balance before completion.

## Primary Sources
- EQUATOR reporting guidelines: https://www.equator-network.org/reporting-guidelines/
- STROBE: https://www.equator-network.org/reporting-guidelines/strobe/
- CONSORT: https://www.equator-network.org/reporting-guidelines/consort/
- PRISMA: https://www.equator-network.org/reporting-guidelines/prisma/
- STARD: https://www.equator-network.org/reporting-guidelines/stard/
- TRIPOD-SRMA: https://www.equator-network.org/reporting-guidelines/tripod-srma/
- TRIPOD: https://www.tripod-statement.org/
- CARE: https://www.equator-network.org/reporting-guidelines/care/
- SQUIRE: https://www.equator-network.org/reporting-guidelines/squire/
- Nature writing and language: https://www.nature.com/natcomputsci/natcomputsci/submission-guidelines/writing-and-language
- Nature Portfolio editorial policies (AI section): https://www.nature.com/authors/editorial_policies/
- Nature Communications submission guidance on AI use: https://www.nature.com/ncomms/submit/how-to-submit
- Cell Press title and abstract guidance: https://crosstalk.cell.com/blog/getting-your-paper-published-with-as-little-frustration-as-possible-1
- JAMA Instructions for Authors: https://jamanetwork.com/journals/jama/pages/instructions-for-authors
- AAAS Communication Toolkit: https://www.aaas.org/resources/communication-toolkit
