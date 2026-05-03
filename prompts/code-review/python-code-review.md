# Python Code Review

## Purpose
Ask an AI to review Python code with emphasis on PEP 8 compliance, type annotations, exception handling, and Pythonic idioms, in addition to the standard quality checks.

## When to use
Use this prompt when you want a Python-specific review. It covers everything in the general review and adds Python-specific checks.

---

## The 5 elements

**Goal**
Review the provided Python code for correctness, edge cases, exception handling, readability, maintainability, performance, and style. Specifically check PEP 8 compliance, type annotations, Pythonic idioms, and proper use of Python's standard library.

**Context**
- Python version: `[LANGUAGE]` (e.g., Python 3.11)
- Framework / libraries: `[FRAMEWORK]` (e.g., Django, FastAPI, pytest)
- OS / runtime: `[OS]`
- Dependencies (`requirements.txt` / `pyproject.toml`): `[DEPENDENCIES]`
- Project structure: `[PROJECT_STRUCTURE]`
- Team conventions: `[PROJECT_CONTEXT]`

**Expected vs Actual**
- Expected behavior: `[EXPECTED_BEHAVIOR]`
- Current behavior or concern: `[ACTUAL_BEHAVIOR]`

**Evidence**
- File path: `[FILE_PATH]`
- Relevant test file or output: `[LOGS]`

**Output Request**
Return a structured Python code review using the format described below.

---

## Reusable prompt

```
## Python Code Review Request

**Goal:** Review the following Python code for correctness, edge cases, exception handling, readability, maintainability, and performance. Also check:
- PEP 8 style compliance
- Type annotations (presence, correctness, completeness)
- Exception handling (specific vs. bare except, re-raise patterns)
- Pythonic idioms (list comprehensions, context managers, dataclasses, etc.)
- Use of the standard library over manual reimplementation

**Context:**
- Python version: [LANGUAGE]
- Framework / libraries: [FRAMEWORK]
- OS / runtime: [OS]
- Dependencies: [DEPENDENCIES]
- Project structure: [PROJECT_STRUCTURE]
- Team conventions: [PROJECT_CONTEXT]

**Expected behavior:**
[EXPECTED_BEHAVIOR]

**Current behavior or concern:**
[ACTUAL_BEHAVIOR]

**Code to review:**
```python
[paste code here]
```

**Additional evidence (test output, linter output, previous failures):**
[LOGS]

**Output format:**
1. Overall quality summary (2–4 sentences).
2. Numbered issue list — each item: severity (critical / major / minor), category (correctness / style / typing / idiom / performance), description, suggested fix.
3. Improved code snippet (show only changed sections).
4. Open questions or missing information needed before approval.
```

---

## Expected output format

- **Summary** paragraph
- **Issues** numbered list with severity and category labels
- **Suggested fixes** as Python code blocks
- **Open questions** bullet list (if any)

---

## Notes / limitations

- Replace every `[PLACEHOLDER]` before sending the prompt.
- If using a linter (flake8, pylint, ruff), paste its output into the Evidence section.
- AI may miss runtime-specific issues. Always run the test suite after applying suggestions.
- AI output must be reviewed by a human before merging.
