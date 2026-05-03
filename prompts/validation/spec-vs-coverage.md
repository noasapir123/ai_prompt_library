# Spec vs. Coverage Comparison

## Purpose
Ask an AI to compare a specification (requirements, design doc, or test plan) against a coverage report to find items that appear in the spec but are missing or insufficiently covered.

## When to use
Use this prompt when you want to verify that every requirement, scenario, or opcode defined in a spec has corresponding coverage, and to understand the risk of any missing coverage.

---

## The 5 elements

**Goal**
Compare `[SPEC_REFERENCE]` (the specification) against `[COVERAGE_RESULT]` (the coverage results) and identify every spec item that is missing, partially covered, or not covered at all. Explain the risk and recommend actions.

**Context**
- Project / feature: `[PROJECT_CONTEXT]`
- Language / framework: `[LANGUAGE]`
- Coverage tool: `[FRAMEWORK]`
- OS / environment: `[OS]`
- Spec type: `[SPEC_REFERENCE]` (e.g., RTL design spec, test plan, user story, requirements doc)

**Expected vs Actual**
- Expected: every spec item has full, traceable coverage
- Actual: one or more spec items appear to have no or low coverage in the report

**Evidence**
- Spec document or excerpt: `[SPEC_REFERENCE]`
- Coverage results: `[COVERAGE_RESULT]`
- Logs or regression output: `[LOGS]`
- Config or tool output: `[CONFIG_FILE]`

**Output Request**
Return a structured comparison: for each spec item with a gap, provide — Problem, Evidence, Possible explanation, Risk, Recommended action, Questions / missing information.

---

## Reusable prompt

```
## Spec vs. Coverage Comparison Request

**Goal:** Compare the spec below against the coverage results and identify every spec item that is missing, partially covered, or not covered. For each gap, explain the risk and recommend an action.

**Context:**
- Project / feature: [PROJECT_CONTEXT]
- Language / framework: [LANGUAGE]
- Coverage tool: [FRAMEWORK]
- Environment: [OS]
- Spec type: [SPEC_REFERENCE]

**Expected:**
Every item in the spec has full, traceable coverage in the coverage results.

**Actual:**
Possible gaps between spec items and coverage results (details below).

**Specification (or relevant excerpt):**
[SPEC_REFERENCE]

**Coverage results:**
[COVERAGE_RESULT]

**Logs / regression output:**
[LOGS]

**Config / tool output:**
[CONFIG_FILE]

**Output format — for each spec item with a gap:**

### Spec item: [item name or ID]
- **Problem:** What spec item is missing or under-covered?
- **Evidence:** Which coverage line, branch, or case is affected?
- **Possible explanation:** Why might this item be uncovered?
- **Risk:** What could go wrong if this gap is not closed?
- **Recommended action:** Add a test, update the spec, trace to existing coverage, or accept and document?
- **Questions / missing information:** What else is needed to resolve this?

**Summary table (optional):**
| Spec item | Coverage status | Risk | Action |
|-----------|----------------|------|--------|
```

---

## Expected output format

One section per gap with six labeled fields: Problem, Evidence, Possible explanation, Risk, Recommended action, Questions / missing information. Optional summary table at the end.

---

## Notes / limitations

- Replace every `[PLACEHOLDER]` before sending.
- Provide both the spec and the coverage report as text — the AI cannot read files directly.
- If the spec is large, paste only the relevant section and note the full document reference.
- The AI performs a textual comparison and may miss semantic mismatches. Human review is required.
- Use `coverage-gap-analysis.md` if you only have a coverage report and no spec to compare against.
