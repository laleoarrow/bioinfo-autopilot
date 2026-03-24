# Official Sources (Use Primary Docs First)

This list is representative, not exhaustive.

If a workflow uses a tool, package, portal, database, or file format that is not listed here, do not guess. Search immediately for the official manual, official repository, official package page, official vignette, or official vendor/consortium documentation, then verify the exact version in use before editing commands or interpreting outputs.

If an official page says a tool is deprecated, archived, unsupported, or migrated, do not stop there. Follow that notice to the current maintained official source before adopting commands, defaults, or output interpretations.

## GWAS / Summary Stats / Meta-analysis
- PLINK 1.9 docs: https://www.cog-genomics.org/plink/1.9/
- PLINK 2 docs: https://www.cog-genomics.org/plink/2.0/
- PLINK 1.9 meta-analysis postproc (`weighted-z`, `p-field`, `ess-field`):
  - https://www.cog-genomics.org/plink/1.9/postproc
- METAL (official repository):
  - https://github.com/statgen/METAL

## Post-GWAS / Heritability / Genetic Correlation / MR / Fine-Mapping
- LDSC (official repository): https://github.com/bulik/ldsc
- HDL (official repository): https://github.com/zhenin/HDL
- GCTA (official docs): https://yanglab.westlake.edu.cn/GCTA.html
- GSMR (official docs): https://yanglab.westlake.edu.cn/software/gsmr/
- SMR (official docs): https://yanglab.westlake.edu.cn/software/smr/
- gsMap (official docs): https://yanglab.westlake.edu.cn/gps_data/website_docs/html/index.html
- gsMap tutorials: https://yanglab.westlake.edu.cn/gps_data/website_docs/html/tutorials.html
- FUMA (official platform/docs): https://fuma.ctglab.nl/
- MAGMA (official docs/downloads): https://cncr.nl/research/magma/
- coloc (official docs): https://chr1swallace.github.io/coloc/
- susieR (official docs): https://stephenslab.github.io/susieR/
- TwoSampleMR (official docs): https://mrcieu.github.io/TwoSampleMR/
- ieugwasr / OpenGWAS interface (official docs): https://mrcieu.github.io/ieugwasr/
- Open Targets Genetics (official docs/API): https://genetics-docs.opentargets.org/ and https://api.genetics.opentargets.org/
- GenomicSEM (official repository): https://github.com/GenomicSEM/GenomicSEM
- LAVA (official repository/docs): https://github.com/josefin-werme/LAVA
- MetaXcan / PrediXcan / S-PrediXcan (official repository): https://github.com/hakyimlab/MetaXcan
- FUSION TWAS (official docs): https://gusevlab.org/projects/fusion/

## Variant Data / Alignment / Utilities
- SAMtools (official docs): https://www.htslib.org/doc/
- BCFtools (official docs): https://samtools.github.io/bcftools/
- HTSlib: https://www.htslib.org/
- BEDTools (official docs): https://bedtools.readthedocs.io/
- VCF specification (GA4GH/hts-specs): https://samtools.github.io/hts-specs/

## RNA-seq / Differential Expression
- DESeq2 (Bioconductor): https://bioconductor.org/packages/DESeq2/
- edgeR (Bioconductor): https://bioconductor.org/packages/edgeR/

## Cohort / Clinical Epidemiology / Survival
- STROBE Statement (official): https://www.strobe-statement.org/
- STROBE at EQUATOR (official guideline entry): https://www.equator-network.org/reporting-guidelines/strobe/
- R `survival` package (official CRAN manual): https://cran.r-project.org/package=survival
- CRAN Task View: Survival Analysis: https://cran.r-project.org/view=Survival

## Functional Enrichment / Pathway-Level Interpretation
- clusterProfiler (Bioconductor): https://bioconductor.org/packages/clusterProfiler/
- GSVA (Bioconductor): https://bioconductor.org/packages/GSVA/

## Single-Cell / Single-Nucleus / Spatial
- Seurat (official docs): https://satijalab.org/seurat/
- Scanpy (official docs): https://scanpy.readthedocs.io/en/stable/
- Cell Ranger (official 10x docs): https://www.10xgenomics.com/support/software/cell-ranger/latest
- Space Ranger (official 10x docs): https://www.10xgenomics.com/support/software/space-ranger/latest
- Signac (official docs): https://stuartlab.org/signac/
- SingleR (Bioconductor): https://bioconductor.org/packages/SingleR/
- scater (Bioconductor): https://bioconductor.org/packages/scater/
- scran (Bioconductor): https://bioconductor.org/packages/scran/
- scDblFinder (Bioconductor): https://bioconductor.org/packages/scDblFinder/
- ArchR (official docs): https://www.archrproject.com/
- Monocle 3 (official docs): https://cole-trapnell-lab.github.io/monocle3/
- scvi-tools (official docs): https://docs.scvi-tools.org/en/stable/
- CellChat v2 (official repository): https://github.com/jinworks/CellChat
- inferCNV (Bioconductor package and official wiki; check current support status first): https://bioconductor.org/packages/infercnv/ and https://github.com/broadinstitute/inferCNV/wiki

## Genome References / Annotation
- Ensembl documentation: https://www.ensembl.org/info/docs/
- NCBI dbSNP: https://www.ncbi.nlm.nih.gov/snp/
- UCSC Genome Browser docs: https://genome.ucsc.edu/goldenPath/help/

## Bioconductor Infrastructure
- Bioconductor packages portal: https://bioconductor.org/packages/
- BSgenome: https://bioconductor.org/packages/BSgenome/
- SNPlocs.Hsapiens.dbSNP155.GRCh37: https://bioconductor.org/packages/SNPlocs.Hsapiens.dbSNP155.GRCh37/

## Workflow Engines
- Nextflow docs: https://www.nextflow.io/docs/latest/
- Snakemake docs: https://snakemake.readthedocs.io/

## Usage Rule
Before editing workflow parameters, open relevant official pages above and confirm required fields, flags, defaults, version-specific behaviors, and output definitions for the exact tool/version in use.

If a required tool is missing from this file, search for the official source first and add the chosen URL(s) to your working notes before changing anything.
