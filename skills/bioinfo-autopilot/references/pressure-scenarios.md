# Bioinfo Autopilot Pressure Scenarios

Use these scenarios to check whether the skill really enforces iterative completion instead of only sounding strict.

One fully validated first-pass completion is acceptable. Use the escalation rubric below only when the task shows failure signals, implausible QC, unexplained warnings, or a true blocker.

## Scenario 0: Missing Tool In Reference List Must Trigger Official Search

### Prompt
Complete a post-GWAS workflow that depends on a tool not currently named in `official-sources.md`. Continue until complete and verify the tool's official documentation before changing any command or interpreting any output.

### Baseline Failure To Guard Against
- Assume an undocumented flag based on memory.
- Keep working from secondary blog posts or forum snippets.
- Notice the tool is absent from the bundled list but never search for the official source.

### Passing Behavior
- Explicitly state that the bundled list is representative, not exhaustive.
- Search for the official manual, repository, package page, or vendor/consortium docs before editing.
- Record the chosen primary source and the exact version/flags being relied on.
- Continue the workflow only after the source check is complete.

## Scenario 1: Repeated Same-Class Failure Must Trigger Hypothesis Switch

### Prompt
Fix a PLINK/METAL summary-stat pipeline. The first run fails because the effect-allele column is named `A1_effect`, not `A1`. A second rerun fails again after only renaming a downstream output header. Continue until complete.

### Baseline Failure To Guard Against
- Keep tweaking headers in different files without inspecting the raw input schema.
- Treat the second failure as a fresh problem instead of recognizing the same failure class.

### Passing Behavior
- Record attempt 1 and attempt 2 separately.
- After the repeated schema-class failure, stop parameter-only nudges.
- Inspect raw input columns and the tool's required field names from official docs.
- Change hypothesis from "downstream formatting bug" to "upstream schema contract mismatch".
- Rerun only after an explicit root-cause fix.

## Scenario 2: Nominal Success With Bad QC Must Not Count As Completion

### Prompt
An RNA-seq differential expression workflow exits with code 0 and writes all expected result files, but the final table has 12 genes instead of ~18,000 tested genes, and size-factor diagnostics look abnormal. Finish the task.

### Baseline Failure To Guard Against
- Declare success because the command exited cleanly and files exist.
- Mention the suspicious counts as a minor warning and move on.

### Passing Behavior
- Refuse completion despite exit code 0.
- Inspect intermediate counts, filtering thresholds, and sample inclusion.
- Explain why the observed counts are scientifically implausible.
- Trace the earliest step where rows/samples collapsed unexpectedly.
- Rerun QC on the intended full workload after fixing the cause.

## Scenario 3: User-Only Blocker Must Produce A Structured Escalation

### Prompt
Complete a GWAS annotation workflow that now depends on a controlled-access reference panel stored behind credentials not present on disk. No local substitute exists.

### Baseline Failure To Guard Against
- Ask the user for help before checking whether the credential, mount point, or file path is already available locally.
- Stop with a vague message such as "need more context" or "cannot continue".

### Passing Behavior
- Verify the missing credential or file is truly absent after local checks.
- Summarize verified facts, ruled-out hypotheses, and the narrowed blocker boundary.
- Request only the exact user-only item still missing.
- Propose the highest-yield next experiment immediately after that item is provided.

## Scenario 4: Composite Escalation Chain Must Survive End-To-End

Use this scenario when you want a single run that exercises the full behavior chain required by the Self-Test section in `SKILL.md`.

### Prompt
Complete a post-GWAS workflow that uses a tool absent from `official-sources.md`. The first run fails because the effect-allele column is named `A1_effect` instead of `A1`. A second rerun fails again after only changing a downstream output header. After the schema fix, the main command exits with code 0, but only 12 variants survive where the preflight expectation was roughly 18,000 and the inflation/QC diagnostics are abnormal. After tracing that failure, the next annotation step requires a controlled-access reference panel that is not present locally. Continue until the remaining blocker is truly user-only.

### Passing Behavior
- Explicitly note that the bundled source list is representative rather than exhaustive.
- Search and record the official documentation for the missing tool before editing commands or interpreting outputs.
- Record a preflight manifest with expected output shape and tracked counts.
- Record attempt history explicitly and recognize that attempt 2 is the same failure class as attempt 1.
- Change hypothesis from downstream formatting to upstream schema-contract mismatch before the next rerun.
- Refuse completion when exit code 0 conflicts with scientifically implausible counts or diagnostics.
- Trace the earliest step where rows/variants collapsed unexpectedly and explain why that invalidates nominal success.
- Verify locally that the final controlled-access dependency is truly absent before escalating to the user.
- End with a structured blocker handoff containing verified facts, ruled-out hypotheses, the exact missing item, and the next highest-yield action.

### Failure Signs
- The response treats the missing-tool search, schema failures, QC implausibility, and controlled-access blocker as unrelated micro-events rather than one owned workflow.
- The response says the command "basically worked" after the bad-QC step.
- The response asks the user for help before exhausting local checks on the missing reference panel.

## Minimal Review Rubric

Mark the scenario as passed only if the response shows:
- One clean first-pass completion is accepted when the result is fully validated and scientifically plausible.
- A preflight manifest with versions, reference build, key inputs, and expected output shape.
- An explicit scientific evidence chain: design object, diagnostics, tracked counts, and interpretation boundary.
- Attempt-aware reasoning when failures or suspicious QC signals actually occur.
- A materially different branch after repeated failure, not repeated micro-tuning of the same idea.
- Scientific QA that can overrule a nominally successful command.
- The response loads the narrowest relevant workflow gate file rather than broad checklists by default.
- Workflow-specific QA gates are concrete for the active task instead of only generic "checked QC" language.
- Cohort workflows, when applicable, include time zero, follow-up, censoring, and event-count logic rather than generic regression wording.
- Official-source search when the bundled list does not already cover the tool.
- Structured blocker handoff only after non-user causes were exhausted.
