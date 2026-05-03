# Output Format Template

Use this template to specify exactly how you want the AI to format its response. Add the relevant section(s) from below to the **Output Request** section of any prompt.

---

## Available output formats

Choose one or more of the formats below and paste the instruction into your prompt's **Output Request** field.

---

### Step-by-step guide
```
Return a numbered step-by-step guide. Each step should include:
- What to do (one clear action).
- The exact command or code to run (if applicable).
- What to expect after completing the step.
```

---

### Code fix / suggested fix
```
Return the fix as a code block. Show only the changed lines with enough surrounding context to locate them. Add a one-line comment above each change explaining why it was made.
```

---

### Diff
```
Return the changes in unified diff format (--- / +++ with line numbers). Include a short explanation above the diff describing what changed and why.
```

---

### Code review
```
Return a structured code review:
1. Overall quality summary (2–4 sentences).
2. Numbered issue list — each item: severity (critical / major / minor), description, suggested fix.
3. Improved code snippet for each critical or major issue.
4. Open questions (if any).
```

---

### Summary (prose)
```
Return a concise prose summary of no more than [N] sentences / [N] words. Cover: what it is, why it matters, and what action (if any) is needed.
```

---

### Bullet list
```
Return the answer as a bullet list. Each bullet should be one clear, complete sentence. Group related bullets under a bold heading if there are more than 5 items.
```

---

### Checklist
```
Return the answer as a Markdown checklist (- [ ] item). Each item should be one clear action or verification step. Group related items under a heading.
```

---

### Table
```
Return the answer as a Markdown table. Columns: [specify columns here, e.g., Item | Description | Severity | Recommended action]. One row per item. Add a short summary paragraph after the table.
```

---

### Explanation
```
Return a plain-language explanation suitable for [audience: junior developer / non-technical stakeholder / QA engineer]. Avoid jargon. Use an analogy if it helps. Keep it under [N] paragraphs.
```

---

### Gap analysis
```
For each identified gap, return a section with these six fields:
- Problem: what is missing or incorrect.
- Evidence: specific line, case, or reference.
- Possible explanation: why this gap may exist.
- Risk: what could go wrong if not addressed.
- Recommended action: what to do next.
- Questions / missing information: what else is needed.
```

---

### Professional message
```
Return 2–3 tone variations of the message (friendly / neutral / brief). Each version should be ready to copy and send. Include a subject line for email.
```

---

### Release notes
```
Return formatted release notes with these sections:
- New Features
- Bug Fixes
- Breaking Changes
- Deprecations
- Known Issues
Each item is one clear sentence. Breaking changes include a brief migration note.
```

---

### Risk analysis
```
Return a risk analysis table with columns: Risk | Likelihood (high/medium/low) | Impact (high/medium/low) | Mitigation. Add a short executive summary above the table.
```

---

## How to use this template

1. Identify which format best matches what you need.
2. Copy the format instruction block.
3. Paste it into the **Output Request** section of your prompt (replacing `[OUTPUT_FORMAT]`).
4. Customize the format description if needed (e.g., specify the number of sentences, table columns, audience).
