# Debug: Regression Failure Investigation

## Purpose
Ask an AI to help identify why a test or behavior that previously worked is now failing after a recent change.

## When to use
Use this prompt when a test suite, CI pipeline, or manual check that used to pass is now failing, and you suspect a specific recent change caused it.

---

## The 5 elements

**Goal**
Identify why `[SCRIPT_NAME]` (or test `[SPEC_REFERENCE]`) regressed after `[RECENT_CHANGE]`, and provide a step-by-step investigation plan with likely root causes and fixes.

**Context**
- Language / runtime: `[LANGUAGE]`
- Framework / test framework: `[FRAMEWORK]`
- OS: `[OS]`
- Dependencies: `[DEPENDENCIES]`
- Project structure: `[PROJECT_STRUCTURE]`
- Branch or commit where the regression was introduced: `[RECENT_CHANGE]`

**Expected vs Actual**
- Expected (before the change): `[EXPECTED_BEHAVIOR]`
- Actual (after the change): `[ACTUAL_BEHAVIOR]`

**Evidence**
- Failing test or script: `[SCRIPT_NAME]` / `[SPEC_REFERENCE]`
- Error message: `[ERROR_MESSAGE]`
- Stack trace: `[STACK_TRACE]`
- CI or test runner logs: `[LOGS]`
- Diff or description of the recent change: `[RECENT_CHANGE]`
- Config file that changed: `[CONFIG_FILE]`

**Output Request**
Return a structured regression investigation: probable root causes, step-by-step checks with exact commands, what each check means, likely fixes, and missing information needed.

---

## Reusable prompt

```
## Debug: Regression Failure

**Goal:** Investigate why [SCRIPT_NAME] / test [SPEC_REFERENCE] regressed after a recent change, identify the root cause, and suggest fixes.

**Context:**
- Language / runtime: [LANGUAGE]
- Framework / test framework: [FRAMEWORK]
- OS: [OS]
- Dependencies: [DEPENDENCIES]
- Project structure: [PROJECT_STRUCTURE]
- Commit / branch of regression: [RECENT_CHANGE]

**Expected behavior (before the change):**
[EXPECTED_BEHAVIOR]

**Actual behavior (after the change):**
[ACTUAL_BEHAVIOR]

**Failing test / script:** [SCRIPT_NAME] / [SPEC_REFERENCE]

**Error message:**
[ERROR_MESSAGE]

**Stack trace:**
[STACK_TRACE]

**Logs:**
[LOGS]

**Recent change (diff or description):**
[RECENT_CHANGE]

**Config file (if changed):**
[CONFIG_FILE]

**Output format:**
1. Probable root causes (ranked most to least likely), tied to the specific recent change.
2. Step-by-step checks — for each: exact command, what to look for, what it means.
3. Likely fixes for each root cause.
4. Missing information that would help confirm the cause.
```

---

## Expected output format

- **Probable root causes** — numbered list tied to the recent change, most likely first
- **Step-by-step checks** — numbered, each with command + expected output + interpretation
- **Likely fixes** — matched to each root cause
- **Missing information** — bullet list

---

## Notes / limitations

- Replace every `[PLACEHOLDER]` before sending.
- The most useful evidence is the `git diff` of the recent change. Always include it.
- If the regression appears in CI but not locally, also use `debug-environment-difference.md`.
- AI cannot run the tests. Run the suggested commands yourself and share output if the issue continues.
