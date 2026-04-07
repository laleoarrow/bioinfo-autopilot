# Vendor Catalog Notes

This directory documents optional vendor content that `bioinfo-autopilot` can
route into when first-party local skills are not specific enough.

## bioSkills Source

- Upstream repository: [GPTomics/bioSkills](https://github.com/GPTomics/bioSkills)
- Purpose: imported bioinformatics leaf-skill catalog used as an internal
  routing target, not as a user-facing top-level skill

## Supported Layouts

`bioinfo-autopilot` may look for the vendor catalog in either of these forms:

1. Adapted cc-switch layout
   - Path: `~/.cc-switch/vendor/bioskills-library/`
   - Expected shape: curated import with category index plus leaf `SKILL.md`
     files
2. Repo-local upstream clone
   - Path: `vendor/bioSkills/`
   - Expected shape: raw clone of the upstream `GPTomics/bioSkills` repository

## Recommended Setup

For a portable install of this repository, clone the upstream catalog next to
this file:

```bash
git clone https://github.com/GPTomics/bioSkills.git vendor/bioSkills
```

If you already maintain a central adapted vendor tree via cc-switch, keep using
that instead:

```bash
mkdir -p ~/.cc-switch/vendor
# Put the adapted bioSkills import at:
# ~/.cc-switch/vendor/bioskills-library
```

## Usage Rule

- Do not expose `bioSkills` as a separate top-level skill when using this
  repository.
- Let `bioinfo-autopilot` decide whether vendor guidance is needed and which
  vendor leaf skill to open.
