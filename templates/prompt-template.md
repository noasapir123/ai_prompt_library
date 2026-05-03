# Prompt Template

Use this template as a starting point when creating any new prompt file in this library.

---

## Title
[Short, descriptive title — e.g., "Python Unit Test Generation"]

## Purpose
[One or two sentences explaining what this prompt does.]

## When to use
[Describe the situation or task where this prompt is the right choice. Be specific.]

---

## The 5 elements

**Goal**
[What the user wants to achieve. Be specific about the task: build, fix, review, summarize, write, analyze, etc.]

**Context**
- Language / runtime: `[LANGUAGE]`
- Framework / libraries: `[FRAMEWORK]`
- OS / environment: `[OS]`
- Dependencies: `[DEPENDENCIES]`
- Project structure: `[PROJECT_STRUCTURE]`
- Additional background: `[PROJECT_CONTEXT]`

**Expected vs Actual**
- Expected behavior or desired result: `[EXPECTED_BEHAVIOR]`
- Actual behavior or current state: `[ACTUAL_BEHAVIOR]`

**Evidence**
- Code or file: `[FILE_PATH]`
- Error message: `[ERROR_MESSAGE]`
- Stack trace: `[STACK_TRACE]`
- Logs: `[LOGS]`
- Config file: `[CONFIG_FILE]`
- Spec or requirement reference: `[SPEC_REFERENCE]`
- Coverage result: `[COVERAGE_RESULT]`
- Recent change: `[RECENT_CHANGE]`

**Output Request**
[Describe the exact output format you want: step-by-step guide, code fix, diff, summary, checklist, table, email draft, etc.]

---

## Reusable prompt

```
## [Title]

**Goal:** [GOAL]

**Context:**
- Language: [LANGUAGE]
- Framework: [FRAMEWORK]
- OS: [OS]
- Dependencies: [DEPENDENCIES]
- Project structure: [PROJECT_STRUCTURE]
- Additional context: [PROJECT_CONTEXT]

**Expected behavior:**
[EXPECTED_BEHAVIOR]

**Actual behavior:**
[ACTUAL_BEHAVIOR]

**Evidence:**
- File: [FILE_PATH]
- Error: [ERROR_MESSAGE]
- Stack trace: [STACK_TRACE]
- Logs: [LOGS]
- Config: [CONFIG_FILE]
- Spec reference: [SPEC_REFERENCE]
- Coverage: [COVERAGE_RESULT]
- Recent change: [RECENT_CHANGE]

**Output format:**
[OUTPUT_FORMAT]
```

---

## Expected output format
[Describe what the AI response should look like: numbered list, code block, markdown table, prose summary, etc.]

---

## Notes / limitations
- Replace every `[PLACEHOLDER]` before sending the prompt.
- Remove any placeholder lines that are not relevant to your task.
- Keep the prompt self-contained and copy-pasteable.
- AI output must be reviewed by a human before use.

---

## Placeholder reference

| Placeholder | What to fill in |
|-------------|----------------|
| `[GOAL]` | What the user wants to achieve |
| `[PROJECT_CONTEXT]` | Background, conventions, business rules |
| `[LANGUAGE]` | Programming language and version |
| `[FRAMEWORK]` | Framework, library, or tool |
| `[OS]` | Operating system or runtime environment |
| `[DEPENDENCIES]` | Package list, versions, or dependency file |
| `[PROJECT_STRUCTURE]` | Folder layout, key files, architecture |
| `[EXPECTED_BEHAVIOR]` | What should happen |
| `[ACTUAL_BEHAVIOR]` | What actually happens (or current state) |
| `[ERROR_MESSAGE]` | The exact error text |
| `[STACK_TRACE]` | Full stack trace |
| `[LOGS]` | Relevant log output |
| `[CONFIG_FILE]` | Config file name and relevant content |
| `[SCRIPT_NAME]` | Name of the script or file being run |
| `[FILE_PATH]` | Path to the relevant file |
| `[SPEC_REFERENCE]` | Spec section, requirement ID, or user story |
| `[COVERAGE_RESULT]` | Coverage report output or summary |
| `[RECENT_CHANGE]` | Description or diff of a recent change |
| `[OUTPUT_FORMAT]` | Desired format for the AI response |
