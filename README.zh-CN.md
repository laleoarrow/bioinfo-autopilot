# bioinfo-autopilot

### 生信自动执行 — 端到端分析自动化

**[🇺🇸 English](README.md)** | **🇨🇳 中文**

<p>
  <img src="https://img.shields.io/badge/Claude_Code-black?style=flat-square&logo=anthropic&logoColor=white" alt="Claude Code">
  <img src="https://img.shields.io/badge/OpenAI_Codex_CLI-412991?style=flat-square&logo=openai&logoColor=white" alt="OpenAI Codex CLI">
  <img src="https://img.shields.io/badge/Workflow-GWAS-blue?style=flat-square" alt="GWAS">
  <img src="https://img.shields.io/badge/Workflow-RNA--seq-green?style=flat-square" alt="RNA-seq">
  <img src="https://img.shields.io/badge/License-MIT-green?style=flat-square" alt="MIT License">
</p>

> 端到端自动化生信工作流：GWAS、RNA-seq、单细胞、队列分析等。官方文档验证、可复现完成、证据支撑解读。

一个 AI Agent 生信分析自动化技能。负责分析直到工作流可复现且科学上可靠。

## 工作流程

```
用户调用 bioinfo-autopilot
                ↓
        ┌───────────────────┐
        │   预跑检查        │
        │  - 工具版本       │
        │  - 输入清单       │
        │  - 预期输出       │
        └───────────────────┘
                ↓
           执行分析
                ↓
         ┌─ 成功 → QC 检查 → 交付
         │
         └─ 失败
                ↓
         自动加载 pua-academic
                ↓
         ┌─ L1 Lab Meeting → 切换假设
         │
         ├─ L2 Reviewer 2 → 3 个竞争假设
         │
         ├─ L3 Grant Revision → 7 项检查清单
         │
         └─ L4 Editorial Rejection → 换工具
```

## 支持的工作流

| 工作流 | 描述 |
|--------|------|
| **GWAS** | QC → 关联分析 → 注释 → 可视化 |
| **RNA-seq** | QC → 比对 → 定量 → 差异分析 |
| **单细胞** | QC → 聚类 → 注释 → 差异分析 |
| **队列分析** | 数据准备 → 分析 → 生存分析 → 可视化 |
| **Meta 分析** | 调和 → 聚合 → Forest 图 |

## 核心能力

### 1. 官方文档优先

在修改任何命令、参数或假设之前：
1. 识别工作流中的所有工具
2. 打开官方文档
3. 验证输入字段、参数、输出语义
4. 记录链接和关键约束

### 2. 科学证据链

在声明结果可信之前，验证：
- **数据溯源**：原始输入、基因组版本、注释版本
- **方法契约**：命令与官方来源匹配
- **设计契约**：协变量、对比与研究问题匹配
- **诊断证据**：QC 输出显示预期行为
- **阶段间完整性**：计数追踪、损失解释
- **解释边界**：结论不超出数据支撑

### 3. 压力升级（配合 pua-academic）

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
# 克隆两个仓库
git clone https://github.com/laleoarrow/bioinfo-autopilot.git ~/.cc-switch/skills/bioinfo-autopilot
git clone https://github.com/laleoarrow/pua-academic.git ~/.cc-switch/skills/pua-academic

# 创建 symlinks（cc-switch 会自动管理）
# 或让 cc-switch 自动处理链接
```

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
ln -s ~/agents/bioinfo-autopilot/codex/bioinfo-autopilot ~/.codex/skills/bioinfo-autopilot
ln -s ~/agents/pua-academic/codex/pua-academic ~/.codex/skills/pua-academic
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

- **pua-academic**：分析失败时的学术压力引擎
- **academic-editing**：证据锁定后的稿件润色
- **gwas-plink-trans-ancestry**：跨祖源 GWAS meta 分析

## License

MIT License

---

**GitHub**: https://github.com/laleoarrow/bioinfo-autopilot
