# General Code Review

## Purpose
Ask an AI to review a code snippet or file for quality, correctness, and maintainability, regardless of programming language.

## When to use
Use this prompt when you want a thorough review of any code and you do not need language-specific rules. For Python or C, use the dedicated prompts in this folder.

---

## The 5 elements

**Goal**
Review the provided code for correctness, edge cases, error handling, readability, maintainability, performance, thread safety, and style. Suggest concrete fixes.

**Context**
- Language: `[LANGUAGE]`
- Framework / libraries: `[FRAMEWORK]`
- OS / runtime: `[OS]`
- Dependencies: `[DEPENDENCIES]`
- Project structure summary: `[PROJECT_STRUCTURE]`
- Coding standards or conventions in use: `[PROJECT_CONTEXT]`

**Expected vs Actual**
- Expected behavior: `[EXPECTED_BEHAVIOR]`
- Current behavior or concern: `[ACTUAL_BEHAVIOR]`

**Evidence**
- Code under review: `[FILE_PATH]`
- Related tests (if any): included below
- Previous failures or known issues: `[LOGS]`

**Output Request**
Return a structured code review with:
1. A short summary of the overall code quality.
2. A numbered list of issues, each with: severity (critical / major / minor), description, and suggested fix.
3. Improved code snippet where relevant.
4. Any questions that need clarification before the code can be approved.

---

## Reusable prompt

```
## Code Review Request

**Goal:** Review the following code for correctness, edge cases, error handling, readability, maintainability, performance, thread safety (if applicable), and style. Suggest concrete fixes for every issue found.

**Context:**
- Language: [LANGUAGE]
- Framework / libraries: [FRAMEWORK]
- OS / runtime: [OS]
- Dependencies: [DEPENDENCIES]
- Project structure: [PROJECT_STRUCTURE]
- Conventions / standards: [PROJECT_CONTEXT]

**Expected behavior:**
[EXPECTED_BEHAVIOR]

**Current behavior or concern:**
[ACTUAL_BEHAVIOR]

**Code to review:**
```[LANGUAGE]
[paste code here]
```

**Additional evidence (tests, logs, previous failures):**
[LOGS]

**Output format:**
1. Overall quality summary (2–4 sentences).
2. Numbered issue list — each item: severity (critical / major / minor), description, suggested fix.
3. Improved code snippet (show only changed sections).
4. Open questions or missing information needed before approval.
```

---

## Expected output format

- **Summary** paragraph
- **Issues** numbered list with severity labels
- **Suggested fixes** as code blocks
- **Open questions** bullet list (if any)

---

## Notes / limitations

- Replace every `[PLACEHOLDER]` before sending the prompt.
- If the code file is large, paste only the relevant section and note the file path.
- For Python-specific rules (PEP 8, typing, idioms) use `python-code-review.md`.
- For C-specific rules (memory, undefined behavior, pointers) use `c-code-review.md`.
- AI output is not a substitute for human code review. Always review the suggestions before applying them.
