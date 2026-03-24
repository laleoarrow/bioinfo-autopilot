# Workflow QC Gates Index

Use this file after defining the workflow type in the preflight manifest. Pick the narrowest gate file that matches the concrete task.

## Choose One Primary Gate File
- GWAS / Meta-analysis / Post-GWAS:
  `/Users/leoarrow/.cc-switch/skills/bioinfo-autopilot/references/gates-gwas-postgwas.md`
- Bulk RNA-seq / Differential Expression:
  `/Users/leoarrow/.cc-switch/skills/bioinfo-autopilot/references/gates-bulk-rna.md`
- Cohort / Clinical Epidemiology / Survival:
  `/Users/leoarrow/.cc-switch/skills/bioinfo-autopilot/references/gates-cohort.md`
- Single-Cell / Single-Nucleus / Spatial:
  `/Users/leoarrow/.cc-switch/skills/bioinfo-autopilot/references/gates-single-cell-spatial.md`

## Loading Rule
- Load exactly one primary gate file for most tasks.
- Load a second gate file only when the task genuinely spans two domains, for example a post-GWAS plus cohort interpretation bridge.
- Do not read all gate files "just in case".

## General Rule
- If any stage shows an unexpected collapse in rows, samples, variants, genes, cells, or spots, stop and explain it before accepting downstream results.
- If the method has no standard diagnostic plot, invent a minimal quantitative check rather than skipping QA.
- If a claimed result cannot be defended with design, diagnostics, and tracked counts, downgrade it to a hypothesis rather than a finished conclusion.
