# Debugging Example — Full Prompt and Sample Output

> **Note:** This file is for reference only. AI agents should not return this content by default. Share it only when the user explicitly asks for a debugging example.

---

## Scenario

A regression test that previously passed is now failing after a recent refactor of a data processing module.

---

## Full debugging prompt (using `debug-regression-failure.md`)

```
## Debug: Regression Failure

**Goal:**
Investigate why the test `test_process_records` in `tests/test_processor.py` started failing after the refactor of `processor.py` in commit `a3f9c12`, identify the root cause, and suggest a fix.

**Context:**
- Language: Python 3.11
- Test framework: pytest 7.4
- OS: Ubuntu 22.04
- Dependencies: pandas 2.0, numpy 1.24
- Project structure:
  project/
  ├── processor.py
  ├── tests/
  │   └── test_processor.py
  └── data/
      └── sample.csv
- Commit of regression: a3f9c12 ("Refactor: replace iterrows with vectorized operations")

**Expected behavior (before the change):**
`test_process_records` passes. The function returns a list of dicts, one per active record, with keys `name` and `score`.

**Actual behavior (after the change):**
`test_process_records` fails with an AssertionError. The function returns an empty list when the input DataFrame has active records.

**Failing test:**
```python
def test_process_records():
    df = pd.DataFrame({
        "name": ["Alice", "Bob", "Carol"],
        "status": ["active", "inactive", "active"],
        "score": [92, 78, 85]
    })
    result = process_records(df)
    assert len(result) == 2
    assert result[0]["name"] == "Alice"
```

**Error message:**
```
AssertionError: assert 0 == 2
```

**Stack trace:**
```
tests/test_processor.py:14: AssertionError
```

**Recent change (diff):**
```diff
-    results = []
-    for _, row in df.iterrows():
-        if row["status"] == "active":
-            results.append({"name": row["name"], "score": row["score"]})
-    return results
+    filtered = df[df["status"] == "Active"]
+    return filtered[["name", "score"]].to_dict(orient="records")
```

**Output format:**
1. Probable root causes (most likely first).
2. Step-by-step checks with exact commands.
3. What each check means.
4. Likely fixes for each root cause.
5. Missing information (if any).
```

---

## Sample AI output

### 1. Probable root causes

1. **Case mismatch (most likely):** The original code filtered on `"active"` (lowercase). The refactored code filters on `"Active"` (capitalized). If the data contains `"active"`, the filter never matches, and the result is always an empty list.

2. **Data type change:** The refactor converts the result to a list of dicts using `to_dict(orient="records")`. If the test expects a different structure (e.g., list of named tuples), it could fail for a different reason.

### 2. Step-by-step checks

**Check 1 — Confirm the status values in the test data**
```python
print(df["status"].unique())
# Expected: ['active' 'inactive'] (lowercase)
# If this prints lowercase values, the filter "Active" will never match.
```

**Check 2 — Run the filter manually**
```python
filtered = df[df["status"] == "Active"]
print(len(filtered))
# If this prints 0, the case mismatch is confirmed.
```

**Check 3 — Confirm output structure**
```python
result = process_records(df)
print(type(result), result)
# Confirm it returns a list of dicts with keys "name" and "score".
```

### 3. What each check means

| Check | Result | Meaning |
|-------|--------|---------|
| Check 1 | `['active' 'inactive']` | Data uses lowercase — filter `"Active"` is wrong. |
| Check 2 | `0` rows | Case mismatch confirmed. |
| Check 3 | Empty list or wrong structure | Fix the filter and re-run. |

### 4. Likely fixes

**Fix for root cause 1 (case mismatch):**
```python
# Change this line in processor.py:
filtered = df[df["status"] == "Active"]
# To:
filtered = df[df["status"] == "active"]
```

**Alternative (case-insensitive filter):**
```python
filtered = df[df["status"].str.lower() == "active"]
```

### 5. Missing information

- Are there other call sites that pass `"Active"` (capitalized) as a status value? If so, the original lowercase filter was the bug, not the refactor.
- Is there a data contract or spec that defines the expected casing of `status` values?

---

> ⚠️ Review this output carefully before applying the fix. The AI identified the likely cause from the diff, but you should confirm by running the checks above on your actual data.
