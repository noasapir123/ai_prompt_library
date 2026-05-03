# Coverage Gap Analysis

## Purpose
Ask an AI to analyze a coverage report and identify which cases, flows, or opcodes have low or missing coverage, and explain why this is a risk.

## When to use
Use this prompt when you have a coverage report and want to understand which gaps matter most, what they mean, and what to do about them.

---

## The 5 elements

**Goal**
Analyze the provided coverage results for `[PROJECT_CONTEXT]` and identify gaps — cases, flows, or code paths that are missing or under-covered. Explain the risk of each gap and recommend actions.

**Context**
- Project / feature: `[PROJECT_CONTEXT]`
- Language / framework: `[LANGUAGE]`
- Coverage tool and type: `[FRAMEWORK]` (e.g., pytest-cov, lcov, functional coverage model)
- OS / environment: `[OS]`
- Relevant spec or requirements: `[SPEC_REFERENCE]`

**Expected vs Actual**
- Expected: full coverage of all specified cases and flows
- Actual: gaps identified in the coverage results below

**Evidence**
- Coverage results: `[COVERAGE_RESULT]`
- Spec or requirements reference: `[SPEC_REFERENCE]`
- Logs or test output: `[LOGS]`
- Config file: `[CONFIG_FILE]`

**Output Request**
Return a structured gap analysis for each identified gap: Problem, Evidence, Possible explanation, Risk, Recommended action, Questions / missing information.

---

## Reusable prompt

```
## Coverage Gap Analysis Request

**Goal:** Analyze the following coverage results and identify gaps — cases, flows, or code paths with missing or insufficient coverage. For each gap, explain the risk and recommend an action.

**Context:**
- Project / feature: [PROJECT_CONTEXT]
- Language / framework: [LANGUAGE]
- Coverage tool: [FRAMEWORK]
- Environment: [OS]
- Relevant spec: [SPEC_REFERENCE]

**Expected:**
Full coverage of all specified cases and flows.

**Actual:**
Gaps identified in the coverage results below.

**Coverage results:**
[COVERAGE_RESULT]

**Spec / requirements reference:**
[SPEC_REFERENCE]

**Logs / test output:**
[LOGS]

**Config:**
[CONFIG_FILE]

**Output format — for each gap:**

### Gap: [short name]
- **Problem:** What is missing or under-covered?
- **Evidence:** Which line, branch, case, or flow is affected?
- **Possible explanation:** Why might this be uncovered?
- **Risk:** What could go wrong if this gap is not closed?
- **Recommended action:** Add a test, update the coverage model, or accept and document?
- **Questions / missing information:** What else is needed to confirm or fix this?
```

---

## Expected output format

One section per gap, each with six labeled fields: Problem, Evidence, Possible explanation, Risk, Recommended action, Questions / missing information.

---

## Notes / limitations

- Replace every `[PLACEHOLDER]` before sending.
- Paste the full coverage report or the relevant section as `[COVERAGE_RESULT]`.
- Include the spec reference so the AI can compare coverage against requirements.
- Coverage analysis is a starting point — a human must decide which gaps are acceptable.
- AI cannot run the tests or read the actual source. Provide enough context for a meaningful analysis.
