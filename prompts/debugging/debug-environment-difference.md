# Debug: Script Behaves Differently Across Environments

## Purpose
Ask an AI to help diagnose why the same script or program behaves differently on two different machines, environments, or deployment targets.

## When to use
Use this prompt when code works in one environment (e.g., your local machine) but fails or produces different results in another (e.g., CI, staging, production, a colleague's machine).

---

## The 5 elements

**Goal**
Identify why `[SCRIPT_NAME]` behaves differently between `[PROJECT_CONTEXT]` (working environment) and `[OS]` (failing environment), and provide a step-by-step plan to find and fix the difference.

**Context**
- Language / runtime and version: `[LANGUAGE]`
- Framework / libraries: `[FRAMEWORK]`
- Working environment: `[PROJECT_CONTEXT]`
- Failing environment OS / platform: `[OS]`
- Dependencies and versions: `[DEPENDENCIES]`
- Project structure: `[PROJECT_STRUCTURE]`

**Expected vs Actual**
- Expected (working environment): `[EXPECTED_BEHAVIOR]`
- Actual (failing environment): `[ACTUAL_BEHAVIOR]`

**Evidence**
- Script name: `[SCRIPT_NAME]`
- Error or unexpected output from failing environment: `[ERROR_MESSAGE]`
- Stack trace (if any): `[STACK_TRACE]`
- Logs from both environments: `[LOGS]`
- Config files: `[CONFIG_FILE]`
- Recent change that may have introduced the difference: `[RECENT_CHANGE]`

**Output Request**
Return a structured debugging plan: probable sources of environment difference, step-by-step checks with exact commands, what each check means, likely fixes, and any missing information.

---

## Reusable prompt

```
## Debug: Environment Difference

**Goal:** Diagnose why [SCRIPT_NAME] works in one environment but not another, and provide a step-by-step plan to identify and fix the difference.

**Context:**
- Language / runtime: [LANGUAGE]
- Framework / libraries: [FRAMEWORK]
- Working environment: [PROJECT_CONTEXT]
- Failing environment: [OS]
- Dependencies: [DEPENDENCIES]
- Project structure: [PROJECT_STRUCTURE]

**Expected behavior (working environment):**
[EXPECTED_BEHAVIOR]

**Actual behavior (failing environment):**
[ACTUAL_BEHAVIOR]

**Error message:**
[ERROR_MESSAGE]

**Stack trace:**
[STACK_TRACE]

**Logs (include both environments if possible):**
[LOGS]

**Config file:**
[CONFIG_FILE]

**Recent changes:**
[RECENT_CHANGE]

**Output format:**
1. Probable sources of the environment difference (ranked most to least likely).
2. Step-by-step checks — for each: exact command to run in each environment, what to compare, what it means.
3. Likely fixes for each root cause.
4. Missing information that would help narrow down the issue.
```

---

## Expected output format

- **Probable sources** — numbered list, most likely first
- **Step-by-step checks** — numbered, each with commands for both environments + comparison instructions
- **Likely fixes** — matched to each probable source
- **Missing information** — bullet list

---

## Notes / limitations

- Replace every `[PLACEHOLDER]` before sending.
- Common sources: different runtime/library versions, environment variables, file paths, permissions, locale/encoding, network access, available system tools, package versions pinned vs. floating.
- Always include the output of version commands (e.g., `python --version`, `node --version`, `gcc --version`) for both environments.
- AI cannot access either environment. The more output you paste as evidence, the more precise the diagnosis.
