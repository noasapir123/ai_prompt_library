# Debug: Script Runs But Gives No Output

## Purpose
Ask an AI to help diagnose why a script runs without errors but produces no visible output.

## When to use
Use this prompt when a script or program completes successfully (exit code 0) but nothing is printed, written, or returned when you expect it to be.

---

## The 5 elements

**Goal**
Identify why `[SCRIPT_NAME]` runs without errors but produces no output, and provide a step-by-step debugging plan with specific commands to run.

**Context**
- Language / runtime: `[LANGUAGE]`
- Framework / libraries: `[FRAMEWORK]`
- OS: `[OS]`
- Dependencies: `[DEPENDENCIES]`
- Project structure: `[PROJECT_STRUCTURE]`
- How the script is invoked: `[PROJECT_CONTEXT]`

**Expected vs Actual**
- Expected: `[EXPECTED_BEHAVIOR]`
- Actual: `[ACTUAL_BEHAVIOR]` (script exits cleanly, no output)

**Evidence**
- Script name: `[SCRIPT_NAME]`
- File path: `[FILE_PATH]`
- Command used to run it: `[LOGS]`
- Any config file relevant: `[CONFIG_FILE]`
- Recent changes: `[RECENT_CHANGE]`

**Output Request**
Return a structured debugging plan: possible root causes, step-by-step checks with exact commands to run, what each check means, likely fixes, and any missing information needed to complete the diagnosis.

---

## Reusable prompt

```
## Debug: Script Runs But Gives No Output

**Goal:** Diagnose why the following script runs without errors but produces no output, and provide a step-by-step debugging plan.

**Context:**
- Language / runtime: [LANGUAGE]
- Framework / libraries: [FRAMEWORK]
- OS: [OS]
- Dependencies: [DEPENDENCIES]
- Project structure: [PROJECT_STRUCTURE]
- How the script is invoked: [PROJECT_CONTEXT]

**Expected behavior:**
[EXPECTED_BEHAVIOR]

**Actual behavior:**
[ACTUAL_BEHAVIOR]

**Script name:** [SCRIPT_NAME]
**File path:** [FILE_PATH]
**Run command:** [LOGS]
**Config file:** [CONFIG_FILE]
**Recent changes:** [RECENT_CHANGE]

**Script source:**
```[LANGUAGE]
[paste script here]
```

**Output format:**
1. Possible root causes (ranked most to least likely).
2. Step-by-step checks — for each check: exact command to run, what to look for, what it means.
3. Likely fixes for each root cause.
4. Missing information that would help narrow down the issue.
```

---

## Expected output format

- **Possible root causes** — numbered list, most likely first
- **Step-by-step checks** — numbered, each with command + expected result + interpretation
- **Likely fixes** — matched to each root cause
- **Missing information** — bullet list of what the AI still needs

---

## Notes / limitations

- Replace every `[PLACEHOLDER]` before sending.
- Common causes: output buffering, logging misconfiguration, wrong file descriptor, early return/exit, condition never met, output redirected to a file.
- If the script uses logging instead of print/stdout, include the logging config in the Evidence section.
- AI cannot run the script. The step-by-step commands are suggestions — run them yourself and share results if the issue persists.
