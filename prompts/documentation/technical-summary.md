# Technical Summary

## Purpose
Ask an AI to write a concise technical summary of a feature, change, investigation, or system component for a technical audience.

## When to use
Use this prompt when you need to communicate a technical topic clearly — for example, summarizing an investigation for a ticket, explaining a new component to your team, or writing the technical section of a design document.

---

## The 5 elements

**Goal**
Write a clear, concise technical summary of `[GOAL]` for `[FRAMEWORK]` (the audience), based on the provided notes and evidence.

**Context**
- Topic: `[GOAL]`
- Audience: `[FRAMEWORK]` (e.g., engineering team, tech lead, QA)
- Project: `[PROJECT_CONTEXT]`
- Language / technology stack: `[LANGUAGE]`
- OS / environment: `[OS]`

**Expected vs Actual**
- Desired output: a clear, well-structured technical summary
- Current state: raw notes, code comments, or investigation findings

**Evidence**
- Raw notes or findings: `[LOGS]`
- Code or config references: `[FILE_PATH]`
- Spec or ticket references: `[SPEC_REFERENCE]`
- Error or behavior details: `[ERROR_MESSAGE]`

**Output Request**
Return a structured technical summary with: overview, key details, impact or implications, and recommended next steps (if any). Use plain technical English. Aim for 200–400 words unless more detail is needed.

---

## Reusable prompt

```
## Technical Summary Request

**Goal:** Write a concise technical summary of [GOAL] for [FRAMEWORK].

**Context:**
- Topic: [GOAL]
- Audience: [FRAMEWORK]
- Project: [PROJECT_CONTEXT]
- Technology stack: [LANGUAGE]
- Environment: [OS]

**Desired output:**
A clear, structured technical summary for the audience above.

**Current state:**
Raw notes or findings provided below.

**Evidence — notes / findings:**
[LOGS]

**Code or config references:**
[FILE_PATH]

**Spec / ticket references:**
[SPEC_REFERENCE]

**Error or behavior details:**
[ERROR_MESSAGE]

**Output format:**
### Technical Summary: [GOAL]

**Overview**
[2–3 sentence description of what this is about]

**Key details**
- [bullet: important fact or finding]
- [bullet: important fact or finding]

**Impact / implications**
[Short paragraph: what this means for the project, system, or team]

**Recommended next steps**
- [action item]
- [action item]
```

---

## Expected output format

Markdown document with four sections: Overview, Key details (bullet list), Impact / implications (short paragraph), Recommended next steps (bullet list). Aim for 200–400 words.

---

## Notes / limitations

- Replace every `[PLACEHOLDER]` before sending.
- Adjust length to the audience — a quick Slack message to a teammate needs less detail than a design document section.
- Always review for technical accuracy before sharing — AI may misunderstand domain-specific details.
