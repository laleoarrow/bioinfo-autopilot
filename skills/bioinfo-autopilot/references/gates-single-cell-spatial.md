# Single-Cell / Spatial QC Gates

- Track cell/spot counts per sample before filtering, after QC, after doublet removal, and in the final object.
- Check mitochondrial/ribosomal or other modality-appropriate QC fractions and whether thresholds removed unexpected populations.
- Verify batch integration or sample mixing behavior rather than assuming integration worked.
- Confirm cluster annotations with marker evidence or transfer-confidence evidence; do not trust labels by name alone.
- For spatial workflows, verify image/spot alignment, tissue coverage, and whether low-count regions are technical or biological.
- Treat ambient RNA, doublets, barcode collisions, or reference-transfer mismatch as first-class failure modes, not minor warnings.
