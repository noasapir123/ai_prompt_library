# Weak vs. Good Prompt — Example

> **Note:** This file is for reference only. AI agents should not return this content by default. Share it only when the user explicitly asks for a prompt example.

---

## The same task — two different prompts

**Task:** Ask an AI to help debug a Python script that is not producing any output.

---

## ❌ Weak prompt

```
My Python script doesn't work. Can you help?
```

### Why this is weak
- No **Goal** — what does "doesn't work" mean?
- No **Context** — which script? what Python version? what OS?
- No **Expected vs Actual** — what should it do? what does it do instead?
- No **Evidence** — no code, no error, no logs.
- No **Output Request** — what kind of help is needed?

The AI can only guess. It will ask multiple clarifying questions or return a generic, unhelpful answer.

---

## ✅ Good prompt

```
## Debug: Python script runs but produces no output

**Goal:**
Diagnose why my Python script `process_data.py` runs without errors but prints nothing to the terminal.

**Context:**
- Language: Python 3.11
- OS: Ubuntu 22.04
- Dependencies: pandas 2.0, numpy 1.24
- The script is run with: `python process_data.py --input data.csv`
- No virtual environment issues — dependencies are installed and import correctly.

**Expected behavior:**
The script should read `data.csv`, process each row, and print a summary line for each record.

**Actual behavior:**
The script finishes in under 1 second with exit code 0. Nothing is printed. No file is written.

**Evidence:**
```python
import pandas as pd

def process(filepath):
    df = pd.read_csv(filepath)
    for _, row in df.iterrows():
        if row["status"] == "active":
            print(f"Processing: {row['name']}")

if __name__ == "__main__":
    import sys
    process(sys.argv[1])
```

Run command output:
```
$ python process_data.py --input data.csv
$
```

**Output Request:**
Return:
1. Possible root causes (ranked most to least likely).
2. Step-by-step checks with exact commands to run.
3. What each check means.
4. Likely fixes for each root cause.
```

### Why this is a good prompt

| Element | What was provided |
|---------|------------------|
| **Goal** | Clearly stated: diagnose missing output in a specific script. |
| **Context** | Python version, OS, dependencies, run command — all provided. |
| **Expected vs Actual** | Expected: summary line per record. Actual: silent exit. |
| **Evidence** | The actual code and terminal output are included. |
| **Output Request** | Exact format requested: root causes, checks, commands, fixes. |

The AI now has everything it needs to give a precise, useful answer — no guessing required.

---

## What the AI would likely answer (summary)

**Root cause (most likely):** The `--input` argument is passed as `--input data.csv`, but the script reads `sys.argv[1]` which captures `--input`, not `data.csv`. So `filepath` = `"--input"`, which either fails silently or returns an empty DataFrame.

**Fix:** Change the run command to `python process_data.py data.csv`, or use `argparse` to handle named arguments properly.
