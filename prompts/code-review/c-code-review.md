# C Code Review

## Purpose
Ask an AI to review C code with strong emphasis on memory management, undefined behavior, buffer safety, pointer and lifetime issues, and thread safety, in addition to standard quality checks.

## When to use
Use this prompt for any C (or C-adjacent) code where manual memory management, raw pointers, or low-level system calls are involved.

---

## The 5 elements

**Goal**
Review the provided C code for correctness, edge cases, error handling, readability, maintainability, and performance. Specifically focus on memory management (allocations, frees, leaks), undefined behavior, buffer overflows, pointer validity and lifetime, integer overflow, thread safety, and C standard compliance.

**Context**
- C standard: `[LANGUAGE]` (e.g., C99, C11, C17)
- Compiler and flags: `[FRAMEWORK]` (e.g., gcc -Wall -Wextra -O2)
- OS / platform: `[OS]`
- Libraries and dependencies: `[DEPENDENCIES]`
- Project structure: `[PROJECT_STRUCTURE]`
- Coding standard or safety guidelines: `[PROJECT_CONTEXT]` (e.g., MISRA-C, internal rules)

**Expected vs Actual**
- Expected behavior: `[EXPECTED_BEHAVIOR]`
- Current behavior or concern: `[ACTUAL_BEHAVIOR]`

**Evidence**
- File path: `[FILE_PATH]`
- Compiler warnings or sanitizer output: `[LOGS]`
- Valgrind or AddressSanitizer report: `[ERROR_MESSAGE]`

**Output Request**
Return a structured C code review using the format described below.

---

## Reusable prompt

```
## C Code Review Request

**Goal:** Review the following C code for correctness, edge cases, error handling, readability, maintainability, and performance. Pay special attention to:
- Memory management: malloc/free pairing, double-free, use-after-free, memory leaks
- Undefined behavior: signed integer overflow, uninitialized variables, invalid pointer arithmetic
- Buffer safety: bounds checking, string handling (strcpy vs. strncpy, sprintf vs. snprintf)
- Pointer and lifetime issues: dangling pointers, NULL dereference, aliasing
- Thread safety: shared state, missing locks, race conditions
- Error handling: checking return values of system calls and library functions
- C standard compliance: [LANGUAGE]

**Context:**
- C standard: [LANGUAGE]
- Compiler and flags: [FRAMEWORK]
- OS / platform: [OS]
- Libraries / dependencies: [DEPENDENCIES]
- Project structure: [PROJECT_STRUCTURE]
- Coding standard: [PROJECT_CONTEXT]

**Expected behavior:**
[EXPECTED_BEHAVIOR]

**Current behavior or concern:**
[ACTUAL_BEHAVIOR]

**Code to review:**
```c
[paste code here]
```

**Additional evidence (compiler warnings, sanitizer output, Valgrind report):**
[LOGS]
[ERROR_MESSAGE]

**Output format:**
1. Overall quality summary (2–4 sentences).
2. Numbered issue list — each item: severity (critical / major / minor), category (memory / UB / buffer / pointer / thread / error-handling / style), description, suggested fix.
3. Improved code snippet (show only changed sections).
4. Open questions or missing information needed before approval.
```

---

## Expected output format

- **Summary** paragraph
- **Issues** numbered list with severity and category labels
- **Suggested fixes** as C code blocks
- **Open questions** bullet list (if any)

---

## Notes / limitations

- Replace every `[PLACEHOLDER]` before sending the prompt.
- Always compile with `-Wall -Wextra -fsanitize=address,undefined` during development.
- Paste Valgrind or AddressSanitizer output into the Evidence section for best results.
- AI cannot run the code. Static analysis tools (cppcheck, clang-tidy) complement this prompt.
- AI output must be reviewed by a human before merging.
