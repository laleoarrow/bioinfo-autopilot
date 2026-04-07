# bioinfo-autopilot

### 生信自动执行 — 官方文档优先，杜绝幻觉

**🇨🇳 中文**

<p>
  <img src="https://img.shields.io/badge/Claude_Code-black?style=flat-square&logo=anthropic&logoColor=white" alt="Claude Code">
  <img src="https://img.shields.io/badge/OpenAI_Codex_CLI-412991?style=flat-square&logo=openai&logoColor=white" alt="OpenAI Codex CLI">
  <img src="https://img.shields.io/badge/No_Hallucination-red?style=flat-square" alt="杜绝幻觉">
  <img src="https://img.shields.io/badge/License-MIT-green?style=flat-square" alt="MIT License">
</p>

> **任何涉及生物信息软件、概念的问题，必须先查官方文档，再回答。** 避免 AI 在生物信息领域产生幻觉，保持科学准确性。

一个 AI Agent 技能，强制要求对任何生信相关任务执行**官方文档优先**原则。防止幻觉，确保科学准确性。

## 为什么需要这个 Skill

AI 在生物信息领域的三大问题：

| 问题 | 表现 | 后果 |
|------|------|------|
| **幻觉参数** | 编造不存在的参数、默认值 | 分析结果不可信 |
| **过时信息** | 用训练数据中的旧版本信息 | 与最新工具不兼容 |
| **概念混淆** | 混淆相似概念（如 FDR vs FWE） | 统计方法错误 |

**bioinfo-autopilot 强制要求**：涉及任何生物信息软件、概念时，必须先查阅官方文档，验证后再回答。

## 工作流程

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

## 核心原则：官方文档优先

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

| 尝试次数 | 等级 | 学术模式 | 必须响应 |
|---------|------|----------|----------|
| 第 1 次 | 基线 | 正常执行 | 按标准流程 |
| 第 2 次 | L1 | Lab Meeting | 切换假设类 |
| 第 3 次 | L2 | Reviewer 2 | 3 个竞争假设 |
| 第 4 次 | L3 | Grant Revision | 7 项检查清单 |
| 第 5 次+ | L4 | Editorial Rejection | 换工具 |

## 完成标准

仅在以下条件满足时声明完成：
- [ ] 主命令在预期工作负载上成功退出
- [ ] 所有预期输出文件存在且非空
- [ ] QC/诊断摘要已生成
- [ ] 预跑预期与最终观察计数匹配
- [ ] 剩余警告已解释并限定范围
- [ ] 相同命令可复现

## 7 项学术检查清单（L3+）

- [ ] **方法验证**：假设检验了？官方文档引用了？
- [ ] **结果验证**：QC 检查了？生物学上合理？
- [ ] **证据链**：数据溯源清晰？步骤可追溯？
- [ ] **可复现性**：seed 固定了？版本记录了？
- [ ] **统计严谨性**：多重检验校正？效应量？
- [ ] **生物学意义**：可解释？文献一致？
- [ ] **发表准备**：Methods 独立？Figure 准备好？

## 与 pua-academic 的集成

```
┌─────────────────────────────────────────────────────┐
│  bioinfo-autopilot (主 skill)                        │
│  - 生信分析方法论                                    │
│  - GWAS/RNA-seq/cohort 等流程                       │
│  - QC 检查、证据链验证                               │
│                                                      │
│  失败时 ↓ 调用                                       │
├─────────────────────────────────────────────────────┤
│  pua-academic (压力引擎)                             │
│  - Reviewer 2 / Lab Meeting / Grant 话术            │
│  - 学术抗合理化                                      │
│  - 能动性等级鞭策                                    │
└─────────────────────────────────────────────────────┘
```

## 安装

### 快速安装（告诉 AI Agent）

**Codex CLI:**
```
告诉 Codex: "根据 https://github.com/laleoarrow/bioinfo-autopilot#installation 的说明安装 bioinfo-autopilot 和 pua-academic"
```

**Claude Code:**
```
告诉 Claude: "根据 https://github.com/laleoarrow/bioinfo-autopilot#installation 的说明安装 bioinfo-autopilot 和 pua-academic"
```

### 方式 1: 使用 cc-switch（推荐）

如果你使用 [cc-switch](https://github.com/laleoarrow/cc-switch) 管理 skills：

```bash
# 先把两个仓库克隆到普通目录
git clone https://github.com/laleoarrow/bioinfo-autopilot.git ~/agents/bioinfo-autopilot
git clone https://github.com/laleoarrow/pua-academic.git ~/agents/pua-academic

# 再把真正的 skill 根目录链接进 cc-switch
mkdir -p ~/.cc-switch/skills
ln -s ~/agents/bioinfo-autopilot/skills/bioinfo-autopilot ~/.cc-switch/skills/bioinfo-autopilot
ln -s ~/agents/pua-academic/skills/pua-academic ~/.cc-switch/skills/pua-academic
```

安装目标应当使用 `skills/<name>`。这个目录才是规范 skill 根目录，除了 `SKILL.md` 之外还包含 `references/`、`agents/` 等相对资源。

### 可选 vendor 目录：bioSkills

如果你希望 `bioinfo-autopilot` 在本地一方技能不够具体时，自动路由到
导入的 `bioSkills` 目录，请查看
[`vendor/README.md`](vendor/README.md)。

便携式仓库内安装方式：

```bash
git clone https://github.com/GPTomics/bioSkills.git vendor/bioSkills
```

上游地址：
- [GPTomics/bioSkills](https://github.com/GPTomics/bioSkills)

如果你已经在 cc-switch 中维护了适配后的中央 vendor 树，请继续使用
`~/.cc-switch/vendor/bioskills-library`，不要把 `bioSkills` 作为顶层 skill
暴露出去。

### 方式 2: 手动安装（无 cc-switch）

**Claude Code:**

```bash
# 克隆仓库到任意位置
git clone https://github.com/laleoarrow/bioinfo-autopilot.git ~/agents/bioinfo-autopilot
git clone https://github.com/laleoarrow/pua-academic.git ~/agents/pua-academic

# 创建 symlinks
ln -s ~/agents/bioinfo-autopilot/skills/bioinfo-autopilot ~/.claude/skills/bioinfo-autopilot
ln -s ~/agents/pua-academic/skills/pua-academic ~/.claude/skills/pua-academic
```

**Codex CLI:**

```bash
# 克隆仓库
git clone https://github.com/laleoarrow/bioinfo-autopilot.git ~/agents/bioinfo-autopilot
git clone https://github.com/laleoarrow/pua-academic.git ~/agents/pua-academic

# 创建 symlinks
ln -s ~/agents/bioinfo-autopilot/skills/bioinfo-autopilot ~/.codex/skills/bioinfo-autopilot
ln -s ~/agents/pua-academic/skills/pua-academic ~/.codex/skills/pua-academic
```

**Cursor:**

```bash
# 克隆并复制 rules
git clone https://github.com/laleoarrow/bioinfo-autopilot.git ~/agents/bioinfo-autopilot
mkdir -p .cursor/rules
cp ~/agents/bioinfo-autopilot/cursor/rules/*.mdc .cursor/rules/
```

### 验证安装

```bash
# 检查 Claude Code skills
ls ~/.claude/skills/ | grep -E "bioinfo-autopilot|pua-academic"

# 检查 Codex skills
ls ~/.codex/skills/ | grep -E "bioinfo-autopilot|pua-academic"

# 可选：检查仓库内 vendor 目录
test -d vendor/bioSkills && echo "bioSkills vendor catalog present"
```

## 触发条件

自动触发当：
- 用户请求生信分析
- 用户提及 GWAS、RNA-seq、单细胞、队列等
- 用户调用 `btw` 或 `/btw` 进行边问

## 边问模式：BTW

当用户以 `btw` 或 `/btw` 开头时：
1. 打开专用子代理
2. 传入任务上下文 + 最近 3 条消息
3. 主线程保持不变

## 相关 Skills

| Skill | 用途 | GitHub |
|-------|------|--------|
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
