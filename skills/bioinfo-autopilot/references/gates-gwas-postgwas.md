# GWAS / Post-GWAS QC Gates

- Confirm genome build, rsID/position convention, effect allele semantics, and sample-size fields before harmonization.
- Track variant counts across each stage: raw input, post-QC, post-harmonization, post-meta/post-GWAS.
- Check allele flips, strand handling, ambiguous SNP policy, and whether variant loss is expected.
- Review QQ/lambda/intercept-style diagnostics or equivalent inflation checks when the method provides them.
- For MR, colocalization, or fine-mapping, record instrument/variant counts and whether the result is being driven by too few surviving variants.
- Treat direction or effect-size patterns that conflict with study design, known positive controls, or orthogonal summaries as blockers until explained.
