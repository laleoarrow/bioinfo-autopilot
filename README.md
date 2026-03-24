# bioinfo-autopilot

### Bioinformatics Autopilot — End-to-End Analysis Automation

**[🇨🇳 中文](README.zh-CN.md)** | **🇺🇸 English**

<p>
  <img src="https://img.shields.io/badge/Claude_Code-black?style=flat-square&logo=anthropic&logoColor=white" alt="Claude Code">
  <img src="https://img.shields.io/badge/OpenAI_Codex_CLI-412991?style=flat-square&logo=openai&logoColor=white" alt="OpenAI Codex CLI">
  <img src="https://img.shields.io/badge/Workflow-GWAS-blue?style=flat-square" alt="GWAS">
  <img src="https://img.shields.io/badge/Workflow-RNA--seq-green?style=flat-square" alt="RNA-seq">
  <img src="https://img.shields.io/badge/License-MIT-green?style=flat-square" alt="MIT License">
</p>

> End-to-end automation of bioinformatics workflows: GWAS, RNA-seq, single-cell, cohort analysis, and more. Official-doc verified, reproducible completion, evidence-backed interpretation.

An AI Agent skill for automated bioinformatics analysis. Owns the analysis until the workflow is reproducible and scientifically defensible.

## Workflow

```
User invokes bioinfo-autopilot
                ↓
        ┌───────────────────┐
        │  Preflight Check  │
        │  - Tool versions  │
        │  - Input inventory│
        │  - Expected output│
        └───────────────────┘
                ↓
           Execute Analysis
                ↓
         ┌─ Success → QC Check → Deliver
         │
         └─ Failure
                ↓
         Auto-load pua-academic
                ↓
         ┌─ L1 Lab Meeting → Switch hypothesis
         │
         ├─ L2 Reviewer 2 → 3 competing hypotheses
         │
         ├─ L3 Grant Revision → 7-item checklist
         │
         └─ L4 Editorial Rejection → Switch tools
```

## Supported Workflows

| Workflow | Description |
|----------|-------------|
| **GWAS** | QC → Association → Annotation → Visualization |
| **RNA-seq** | QC → Alignment → Quantification → DE Analysis |
| **Single-cell** | QC → Clustering → Annotation → Differential |
| **Cohort** | Data prep → Analysis → Survival → Visualization |
| **Meta-analysis** | Harmonization → Aggregation → Forest plots |

## Core Capabilities

### 1. Official-Docs-First

Before changing any command, parameter, or assumption:
1. Identify all tools in the workflow
2. Open official documentation
3. Verify input fields, flags, output semantics
4. Record links and key constraints

### 2. Scientific Evidence Chain

Before declaring a result trustworthy, verify:
- **Data provenance**: raw inputs, genome build, annotation release
- **Method contract**: commands match official source
- **Design contract**: covariates, contrasts match study question
- **Diagnostic evidence**: QC outputs show expected behavior
- **Stage-to-stage integrity**: counts tracked, losses explained
- **Interpretation boundary**: conclusion doesn't overreach data

### 3. Pressure Escalation (with pua-academic)

| Attempt | Level | Academic Mode | Required Response |
|---------|-------|---------------|-------------------|
| 1st | Baseline | Normal execution | Follow standard procedure |
| 2nd | L1 | Lab Meeting | Switch hypothesis class |
| 3rd | L2 | Reviewer 2 | 3 competing hypotheses |
| 4th | L3 | Grant Revision | 7-item checklist |
| 5th+ | L4 | Editorial Rejection | Switch tools |

## Completion Criteria

Declare completion only when:
- [ ] Main command exits successfully on intended workload
- [ ] All expected output files exist and are non-empty
- [ ] QC/diagnostic summaries are produced
- [ ] Preflight expectations match final observed counts
- [ ] Remaining warnings are explained and scoped
- [ ] Re-run is reproducible with same commands

## 7-Item Academic Checklist (L3+)

- [ ] **Method Verification**: Assumptions tested? Official docs cited?
- [ ] **Result Verification**: QC checked? Biologically plausible?
- [ ] **Evidence Chain**: Data provenance clear? Steps traceable?
- [ ] **Reproducibility**: Seed fixed? Versions recorded?
- [ ] **Statistical Rigor**: Multiple testing correction? Effect sizes?
- [ ] **Biological Significance**: Interpretable? Literature consistent?
- [ ] **Publication Ready**: Methods standalone? Figures ready?

## Integration with pua-academic

```
┌─────────────────────────────────────────────────────┐
│  bioinfo-autopilot (main skill)                     │
│  - Bioinformatics methodology                       │
│  - GWAS/RNA-seq/cohort workflows                    │
│  - QC checks, evidence chain validation             │
│                                                      │
│  On failure ↓ invokes                               │
├─────────────────────────────────────────────────────┤
│  pua-academic (pressure engine)                     │
│  - Reviewer 2 / Lab Meeting / Grant rhetoric        │
│  - Academic anti-rationalization                    │
│  - Proactivity level enforcement                    │
└─────────────────────────────────────────────────────┘
```

## Installation

### Quick Install for AI Agents

**For Codex CLI:**
```
Tell Codex: "Install bioinfo-autopilot and pua-academic according to instructions at https://github.com/laleoarrow/bioinfo-autopilot#installation"
```

**For Claude Code:**
```
Tell Claude: "Install bioinfo-autopilot and pua-academic according to instructions at https://github.com/laleoarrow/bioinfo-autopilot#installation"
```

### Option 1: Using cc-switch (Recommended)

If you use [cc-switch](https://github.com/laleoarrow/cc-switch) for skill management:

```bash
# Clone both repos
git clone https://github.com/laleoarrow/bioinfo-autopilot.git ~/.cc-switch/skills/bioinfo-autopilot
git clone https://github.com/laleoarrow/pua-academic.git ~/.cc-switch/skills/pua-academic

# Create symlinks (cc-switch auto-manages this)
# Or let cc-switch handle the linking automatically
```

### Option 2: Manual Install (Without cc-switch)

**Claude Code:**

```bash
# Clone repos to a location of your choice
git clone https://github.com/laleoarrow/bioinfo-autopilot.git ~/agents/bioinfo-autopilot
git clone https://github.com/laleoarrow/pua-academic.git ~/agents/pua-academic

# Create symlinks
ln -s ~/agents/bioinfo-autopilot/skills/bioinfo-autopilot ~/.claude/skills/bioinfo-autopilot
ln -s ~/agents/pua-academic/skills/pua-academic ~/.claude/skills/pua-academic
```

**Codex CLI:**

```bash
# Clone repos
git clone https://github.com/laleoarrow/bioinfo-autopilot.git ~/agents/bioinfo-autopilot
git clone https://github.com/laleoarrow/pua-academic.git ~/agents/pua-academic

# Create symlinks
ln -s ~/agents/bioinfo-autopilot/codex/bioinfo-autopilot ~/.codex/skills/bioinfo-autopilot
ln -s ~/agents/pua-academic/codex/pua-academic ~/.codex/skills/pua-academic
```

**Cursor:**

```bash
# Clone and copy rules
git clone https://github.com/laleoarrow/bioinfo-autopilot.git ~/agents/bioinfo-autopilot
mkdir -p .cursor/rules
cp ~/agents/bioinfo-autopilot/cursor/rules/*.mdc .cursor/rules/
```

### Verify Installation

```bash
# Check Claude Code skills
ls ~/.claude/skills/ | grep -E "bioinfo-autopilot|pua-academic"

# Check Codex skills
ls ~/.codex/skills/ | grep -E "bioinfo-autopilot|pua-academic"
```

## Trigger Conditions

Auto-triggers when:
- User requests bioinformatics analysis
- User mentions GWAS, RNA-seq, single-cell, cohort, etc.
- User invokes `btw` or `/btw` for side questions

## Side Thread: BTW Mode

When user starts with `btw` or `/btw`:
1. Open dedicated subagent
2. Seed with task context + last 3 messages
3. Keep main thread unchanged

## Related Skills

- **pua-academic**: Academic pressure engine for failed analyses
- **academic-editing**: Manuscript polishing after evidence lock
- **gwas-plink-trans-ancestry**: Trans-ancestry GWAS meta-analysis

## License

MIT License

---

**GitHub**: https://github.com/laleoarrow/bioinfo-autopilot
