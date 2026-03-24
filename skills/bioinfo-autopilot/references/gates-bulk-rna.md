# Bulk RNA-seq / Differential Expression QC Gates

- Confirm raw count matrix dimensions, sample-to-group mapping, design formula, contrasts, and batch handling.
- Check library sizes, normalization factors/size factors, and whether any sample was dropped or became an outlier.
- Track tested-gene counts before and after filtering; large collapses must be explained.
- Review PCA/MDS or equivalent sample-separation diagnostics when available.
- Sanity-check top hits, effect directions, and whether known markers, spike-ins, or positive controls behave as expected for the design.
