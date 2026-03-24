---
name: bioinfo-autopilot
description: "Use when users need end-to-end automation of bioinformatics or quantitative biomedical analysis workflows (GWAS, sequencing, expression, annotation, meta-analysis, cohort/survival analysis, clinical epidemiology, etc.), including official-doc verification, implementation, debugging, reruns, reproducible completion, QC, and evidence-backed interpretation, or when they explicitly invoke `btw` / `/btw` side-thread questions."
---

# Bioinfo Autopilot / 生信自动执行

## Overview / 概览
Bioinfo Autopilot helps finish bioinformatics work end-to-end: analysis design, implementation, reruns, QC, and evidence-backed interpretation. It owns the analysis until the workflow is reproducible and scientifically defensible. For broader prose, hand off to `academic-editing`. For user-initiated side questions, use the BTW side thread defined below.

## Core Rules / 核心规则
1. Verify official docs before changing commands, parameters, formats, or assumptions.
2. Prefer primary sources (official manuals, official repositories, Bioconductor package pages, standards docs).
3. Define expected deliverables, success checks, and restart points before the first run.
4. Run the full workflow end-to-end; do not stop at partial success, warning-heavy output, or silently incomplete files.
5. After every failed run, record the exact failure signal, attempt number, and what changed before the next rerun.
6. If the first full run passes all scientific and technical checks, accept first-pass completion; do not invent extra reruns for ceremony.
7. If two consecutive attempts are only micro-tuning of the same idea, stop and switch to a materially different hypothesis.
8. Escalate verification pressure with each repeat failure; do not relax QC standards just to force a nominal success.
9. Never mutate raw inputs in place; prefer derived files, explicit checkpoints, and reversible edits.
10. Keep outputs structured and report what changed, why, and how validated.
11. When the task is to implement or code a new concept, method, or statistical idea, explain it briefly and clearly first if the user seems unsure, then keep the explanation on the main task.
12. If that explanation would become too complex or uncertain, give a short prompt for a new agent or ChatGPT to help the user understand it there first, then return to the main task.
13. `btw` is a user-triggered side-thread mode: when a user starts a message with `btw`, `/btw`, `btw mode`, or `/btw mode`, treat that whole message as the BTW prompt, open or resume a dedicated subagent, seed it with a compact memory packet (task overview, current state, key constraints, and the last 3 messages) plus the side question, and keep the main line unchanged.

## Official-Docs-First Procedure / 先核对官方文档
1. Identify all tools touched by the workflow.
2. For each tool, open the official docs and verify:
   - Required input fields and formats.
   - Meaning of critical flags and defaults.
   - Output column semantics.
   - Version-specific behaviors.
3. Start with the bundled official-source list, but treat it as representative rather than exhaustive.
4. If a tool is not listed, search the web immediately for the official manual, official repository, official package page, or vendor/consortium documentation before editing anything.
5. Record links and key constraints before editing scripts.

Read: `/Users/leoarrow/.cc-switch/skills/bioinfo-autopilot/references/official-sources.md`.

## Preflight Manifest / 预跑清单
Before the first full run, record:
- Workflow type and target deliverables.
- Tool/package versions, reference build, annotation release, and container/environment identity if applicable.
- Input inventory: file paths, sample/cohort identifiers, key row counts, and any expected case/control or group sizes.
- Critical design objects: phenotype coding, covariates, contrasts, sample sheet, pairing, batch variables, and for cohort studies also eligibility criteria, time zero, follow-up window, censoring rules, and outcome/exposure definitions.
- Determinism settings: seeds, thread counts, temp/output directories, and restart/checkpoint strategy.
- Expected scientific shape of the result: rough variant/gene/cell counts, expected diagnostic plots, and major red flags that would invalidate a nominal success.

## Execution Procedure / 执行流程
1. Inspect current scripts/config and dataset schema.
2. Define the intended final artifacts, key QC metrics, and deterministic rerun command before editing anything.
3. Apply minimal, targeted edits.
4. Run syntax checks first.
5. Run full pipeline command(s).
6. Tail logs continuously and inspect intermediate artifacts, not just the final exit code.
7. On failure:
   - Capture the exact error text, failing step, attempt number, and affected files.
   - Map the failure to official docs, source code, and raw inputs.
   - Patch the root cause, not just a downstream symptom.
   - Rerun from a clean, deterministic state.
8. If the same failure class repeats, escalate by attempt count:
   - Attempt 2: ban parameter-only nudges; change hypothesis class or inspect raw inputs/source more deeply.
   - Attempt 3: re-read relevant official docs, verify all preconditions, and write down 3 competing root-cause hypotheses before rerunning.
   - Attempt 4+: isolate a minimal failing subset or alternate tool path, compare behaviors, and trace the defect upstream to the earliest corrupted artifact.
   - Never rerun the same failing command unless code, data, environment, or hypothesis changed and that change is explicit.
9. After success, run output QA checks (row counts, required files, key metrics, error summaries) on the intended full workload, not just a toy subset.

## Workflow-Specific QA Gates / 工作流特异 QA
Start with:
`/Users/leoarrow/.cc-switch/skills/bioinfo-autopilot/references/workflow-qc-gates.md`

Then load only the single most relevant workflow gate file for the current task. Load a second gate file only if the task truly spans two workflows.

Do not read every gate file by default. This skill should narrow to the concrete problem being solved, not drag broad checklists into context.

## Pressure Mechanism / 学术压力机制
When failure repeats, QC looks suspicious, or the workflow stalls, **automatically load `pua-academic` skill** to apply academic pressure.

Read: `/Users/leoarrow/.cc-switch/skills/pua-academic/SKILL.md`

### Pressure Escalation Ladder / 压力升级阶梯

| Attempt | Pressure Level | Academic Mode | Required Response |
|---------|---------------|---------------|-------------------|
| 1st | Baseline | Normal execution | Follow standard procedure |
| 2nd | L1 | Lab Meeting | Stop parameter-only nudges; switch hypothesis class; inspect raw inputs/source |
| 3rd | L2 | Reviewer 2 | Re-read official docs; verify preconditions; write 3 competing root-cause hypotheses |
| 4th | L3 | Grant Revision | Complete 7-item academic checklist; isolate minimal failing subset |
| 5th+ | L4 | Editorial Rejection | Alternative tool path; trace to earliest corrupted artifact |

### Pressure Mode Details / 压力模式详解

**🟡 Lab Meeting Mode (L1)** - 导师当众质疑
- "你这个对照组怎么选的？"
- "这个结果的生物学意义是什么？"
- 停止参数微调，换假设类

**🔴 Reviewer 2 Mode (L2)** - 方法学质疑
- "The methodological justification is insufficient."
- "Alternative explanations were not considered."
- 强制 3 个竞争假设

**🟢 Grant Revision Mode (L3)** - Significance 质疑
- "The preliminary data is not convincing."
- 完成 7 项检查清单

**⚫ Editorial Rejection Mode (L4)** - 退稿风险
- 最后手段，换技术栈/工具

### Anti-Rationalization / 学术抗合理化
- "这个参数大家都这么用" → Reviewer 会问 "cite the source"。官方文档链接在哪？
- "数据看起来没问题" → QC 了吗？count 追踪了吗？sample attrition 解释了吗？
- "结果显著就行了" → 显著 ≠ 正确。effect size 合理吗？混杂控制了吗？
- "我跑完流程了" → Pipeline 跑完 ≠ 分析完成。scientific question 回答了吗？
- "代码能跑" → 能 reproduce 吗？seed 固定了吗？version 记录了吗？
- "Maybe it is just the environment" → verify it with tools before claiming it.
- "It ran, so it must be fine" → inspect counts, diagnostics, and plausibility.
- "Let me just tweak the parameter one more time" → stop and re-frame the problem.

## Escalation Ladder / 迭代加压规则（详细版）
Use this ladder when failure repeats, QC looks suspicious, or the workflow is drifting toward parameter-only nudges.

| Trigger | Required response |
|---|---|
| Same failure class repeats | Stop parameter-only nudges; switch hypothesis class or inspect raw inputs/source more deeply. |
| Command exits 0 but QC is implausible | Refuse completion; trace the earliest collapse in rows, samples, variants, genes, cells, or spots. |
| Tool, flag, or output meaning is undocumented | Search the official source before editing commands or interpreting results. |
| User-only blocker appears after local checks | Report verified facts, ruled-out hypotheses, narrowed blocker boundary, and the exact missing item. |
| Third failed attempt | Re-read official docs, verify preconditions, and write down 3 competing root-cause hypotheses. |
| Fourth and later failed attempts | Isolate a minimal failing subset or alternate tool path, and trace upstream to the earliest corrupted artifact. |

## Scientific Evidence Chain / 科学证据链
Before declaring a bioinformatics result trustworthy, verify all applicable links in the chain:
- Data provenance: raw inputs, genome/reference build, annotation release, sample identifiers, and phenotype/group coding are explicit and consistent.
- Method contract: commands, flags, defaults, and required fields match the official source for the exact tool/version in use.
- Design contract: covariates, contrasts, pairing, batch variables, and inclusion/exclusion rules match the study question rather than an accidental default.
- Diagnostic evidence: standard QC outputs or a justified surrogate check show that the model/data behaved as expected.
- Stage-to-stage integrity: counts of samples, variants, genes, cells, or spots are tracked and unexpected losses are explained.
- Scientific interpretation boundary: the conclusion does not overreach what the surviving data, diagnostics, and sensitivity of the method can support.

If any link in this chain is weak or undocumented, completion is not yet scientific.

## Internal Modes / 内部模式
Think in two internal modes rather than requiring user-facing commands:

- PI (Principal Investigator): if the user explicitly says `PI`, or if the task may benefit from decomposition or subagent coordination, enter PI mode. Build the one-line map first, split only independent subtasks, assign and coordinate subagents as needed, keep evidence and QC aligned across stages, and reconcile outputs before the final claim. If the user explicitly asks not to use PI mode, keep the task single-threaded unless decomposition is required for completion.
  - **PI Team Protocol**: See `pua-academic/references/agent-team.md` for role hierarchy (PI → Postdoc → PhD → RA) and task delegation protocol.
- Loop (Revision Loop): PI may activate Loop when the task benefits from repeated iteration, reruns, debugging, or refinement. In Loop, re-scan changed files or sections after each edit or rerun, re-check counts, labels, versions, diagnostics, and cross-stage consistency, then keep iterating with changed evidence or a changed hypothesis until the analysis, function, or workflow satisfies the completion criteria or the blocker is proven to be truly user-only.
- BTW (By-the-way side thread): follow Core Rule 13 whenever a BTW prompt appears. Keep the main thread on task and point the user to the BTW subagent for that question instead of answering inline.

These modes are automatic behavior, not extra commands the user needs to type.

## 7-Item Academic Checklist / 学术检查清单（L3+ 强制完成）
When pressure reaches L3 (Grant Revision), complete all items before next attempt:

- [ ] **方法选择验证**: assumption 检验了吗？有官方文档/原始 paper 支撑吗？
- [ ] **结果验证**: QC 指标检查了吗？结果在生物学上合理吗？
- [ ] **证据链检查**: 数据来源清晰吗？处理步骤可追溯吗？
- [ ] **可复现性检查**: seed 固定了吗？软件版本记录了吗？
- [ ] **统计严谨性**: 多重检验校正做了吗？effect size 报告了吗？
- [ ] **生物学意义**: 结果能被生物学解释吗？和已有文献一致吗？
- [ ] **发表准备**: Methods 可独立成文吗？Figure 能直接放进 paper 吗？

## Reporting Boundary / 结果叙述边界
This skill can produce concise factual labels, figure/table notes, and short tutorial prose after evidence lock.

If the task needs broader prose work, abstract/title polishing, long reviews, or manuscript-level coherence, hand off to `academic-editing` after the evidence lock. Do not draft the full manuscript here.

## Debugging Checklist / 调试清单
- Input format mismatch.
- Field-name mismatch (case sensitivity, reserved column names).
- Build/version mismatch (reference genome/tool version).
- Strand/allele harmonization problems.
- Missing required covariates or sample-size fields.
- Invalid numeric ranges (`P`, `SE`, frequencies, positions).
- Resource bottlenecks (RAM, disk, temp files).

## Completion Criteria / 完成标准
Declare completion only when all are true:
- Main command exits successfully on the intended workload.
- All expected output files exist and are non-empty where applicable.
- QC/diagnostic summaries are produced.
- Preflight expectations and final observed counts/structures are either consistent or explicitly reconciled.
- Remaining warnings are explained, scoped, and do not invalidate the design contract, diagnostics, or interpretation boundary.
- Re-run is reproducible with same commands.
- No higher-impact unresolved blocker is merely deferred to "next step" without explanation.

## Post-Success Challenge / 成功后反证检查
Before saying "done", ask:
- Could this output be technically complete but scientifically wrong?
- Did any sample/variant/gene/cell count collapse unexpectedly between stages?
- Did any build, annotation, covariate, contrast, or grouping assumption remain implicit rather than verified?
- Did any conclusion depend on too few surviving variants/samples/cells to be robust for this method?
- Would a skeptical collaborator be able to rerun this from the reported commands and reach the same files and summary metrics?

## Self-Test / 自测
Before claiming this skill is improved, run at least one pressure scenario from:
`/Users/leoarrow/.cc-switch/skills/bioinfo-autopilot/references/pressure-scenarios.md`

Pass only if the run shows all of the following:
- The agent changes hypothesis class after repeated same-pattern failure.
- The agent rejects nominal success when QC signals are implausible.
- The agent keeps ownership until the blocker is truly user-only.
- The agent searches for a primary source when the required tool is absent from the bundled source list.
- The final report includes attempt history, evidence, and explicit next action.

## Output Contract / 输出约定
Always report:
- Exact commands run.
- Primary sources verified and versions relied on.
- State whether completion occurred on the first validated run or after reruns.
- If reruns occurred, report attempt count and what changed between failed reruns.
- Files modified.
- Preflight manifest summary and the final observed counts/metrics needed to justify completion.
- Validation checks performed.
- Final output file inventory.
- Residual risks (if any) and next actions.
