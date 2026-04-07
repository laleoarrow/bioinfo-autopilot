# bioinfo-autopilot

### Bioinformatics Autopilot — Official-Docs-First, No Hallucination

**[🇨🇳 中文](README.zh-CN.md)** | **🇺🇸 English**

<p>
  <img src="https://img.shields.io/badge/Claude_Code-black?style=flat-square&logo=anthropic&logoColor=white" alt="Claude Code">
  <img src="https://img.shields.io/badge/OpenAI_Codex_CLI-412991?style=flat-square&logo=openai&logoColor=white" alt="OpenAI Codex CLI">
  <img src="https://img.shields.io/badge/No_Hallucination-red?style=flat-square" alt="No Hallucination">
  <img src="https://img.shields.io/badge/License-MIT-green?style=flat-square" alt="MIT License">
</p>

> **任何涉及生物信息软件、概念的问题，必须先查官方文档，再回答。** 避免 AI 在生物信息领域产生幻觉，保持科学准确性。

An AI Agent skill that enforces **official-docs-first** for any bioinformatics-related task. Prevents hallucination and ensures scientific accuracy.

## Why This Skill Matters

AI 在生物信息领域的三大问题：

| 问题 | 表现 | 后果 |
|------|------|------|
| **幻觉参数** | 编造不存在的参数、默认值 | 分析结果不可信 |
| **过时信息** | 用训练数据中的旧版本信息 | 与最新工具不兼容 |
| **概念混淆** | 混淆相似概念（如 FDR vs FWE） | 统计方法错误 |

**bioinfo-autopilot 强制要求**：涉及任何生物信息软件、概念时，必须先查阅官方文档，验证后再回答。

## Workflow

```
用户提出生物信息相关问题
                ↓
        ┌───────────────────┐
        │  官方文档检查      │
        │  - 软件官方文档   │
        │  - Bioconductor   │
        │  - 原始 paper     │
        └───────────────────┘
                ↓
         ┌─ 有文档 → 验证后回答
         │
         └─ 无文档 → 搜索官方来源 → 验证后回答
                ↓
           科学证据链检查
                ↓
         ┌─ 成功 → 交付
         │
         └─ 失败 → 加载 pua-academic
```

## Core Principle: Official-Docs-First

### 适用范围（不限于此）

**任何涉及以下内容的问题，都必须先查官方文档：**

- 🧬 **基因组学工具**: PLINK, BCFtools, SAMtools, GATK, Minimap2...
- 📊 **R/Bioconductor 包**: DESeq2, edgeR, limma, Seurat, SingleCellExperiment...
- 🐍 **Python 生信库**: scanpy, pysam, biopython, anndata...
- 📈 **统计方法**: 多重检验校正、混合模型、生存分析、Meta 分析...
- 🗄️ **数据库**: Ensembl, UCSC, dbSNP, GTEx, UK Biobank...
- 🔬 **实验设计**: 样本量计算、效力分析、批次效应...

### 执行规则

```
规则 1: 识别工具/概念 → 搜索官方文档 → 验证参数/用法 → 再回答
规则 2: 优先级：官方文档 > 原始 paper > 教程 > 博客
规则 3: 记录来源链接，便于追溯
规则 4: 版本敏感，必须确认当前版本的行为
```

### 证据链检查

在声明结果可信之前，验证：
- **数据溯源**：原始输入、基因组版本、注释版本
- **方法契约**：命令与官方来源匹配
- **设计契约**：协变量、对比与研究问题匹配
- **诊断证据**：QC 输出显示预期行为
- **阶段间完整性**：计数追踪、损失解释
- **解释边界**：结论不超出数据支撑

### 压力升级（配合 pua-academic）

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
# Clone both repos to a normal location
git clone https://github.com/laleoarrow/bioinfo-autopilot.git ~/agents/bioinfo-autopilot
git clone https://github.com/laleoarrow/pua-academic.git ~/agents/pua-academic

# Link the actual skill roots into cc-switch
mkdir -p ~/.cc-switch/skills
ln -s ~/agents/bioinfo-autopilot/skills/bioinfo-autopilot ~/.cc-switch/skills/bioinfo-autopilot
ln -s ~/agents/pua-academic/skills/pua-academic ~/.cc-switch/skills/pua-academic
```

Use `skills/<name>` as the install target. That directory is the canonical skill root and contains `SKILL.md` plus any relative assets such as `references/` or `agents/`.

### Optional Vendor Catalog: bioSkills

If you want `bioinfo-autopilot` to route into the imported `bioSkills`
catalog when first-party guidance is not specific enough, see
[`vendor/README.md`](vendor/README.md).

Portable repo-local setup:

```bash
git clone https://github.com/GPTomics/bioSkills.git vendor/bioSkills
```

Upstream source:
- [GPTomics/bioSkills](https://github.com/GPTomics/bioSkills)

If you already maintain an adapted cc-switch vendor tree, keep using
`~/.cc-switch/vendor/bioskills-library` instead of exposing `bioSkills` as a
top-level skill.

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
ln -s ~/agents/bioinfo-autopilot/skills/bioinfo-autopilot ~/.codex/skills/bioinfo-autopilot
ln -s ~/agents/pua-academic/skills/pua-academic ~/.codex/skills/pua-academic
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

# Optional: check repo-local vendor catalog
test -d vendor/bioSkills && echo "bioSkills vendor catalog present"
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

| Skill | Purpose | GitHub |
|-------|---------|--------|
| **pua-academic** | 学术压力引擎，分析失败时加载 | https://github.com/laleoarrow/pua-academic |
| **academic-editing** | 论文润色，证据锁定后调用 | https://github.com/laleoarrow/academic-editing |

### Skill 协作流程

```
┌─────────────────────────────────────────────────────┐
│  bioinfo-autopilot                                  │
│  官方文档优先，执行生信分析                          │
│                                                      │
│  失败时 ↓ 加载                                       │
│  ┌─────────────────────────────────────────────┐    │
│  │  pua-academic                                │    │
│  │  学术压力引擎（Reviewer 2 / Lab Meeting）    │    │
│  └─────────────────────────────────────────────┘    │
│                                                      │
│  证据锁定后 ↓ 调用                                   │
│  ┌─────────────────────────────────────────────┐    │
│  │  academic-editing                            │    │
│  │  论文润色（稿件级文本处理）                  │    │
│  └─────────────────────────────────────────────┘    │
└─────────────────────────────────────────────────────┘
```

## License

MIT License

---

**GitHub**: https://github.com/laleoarrow/bioinfo-autopilot
