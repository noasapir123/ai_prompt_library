# Release Notes

## Purpose
Ask an AI to write clear, concise, professional release notes for a software release based on commits, tickets, or a list of changes.

## When to use
Use this prompt when you need to communicate what changed in a release to an internal or external audience (developers, QA, customers, management).

---

## The 5 elements

**Goal**
Write release notes for version `[PROJECT_CONTEXT]` that clearly communicate new features, bug fixes, breaking changes, and known issues to `[FRAMEWORK]` (the audience).

**Context**
- Project name: `[PROJECT_CONTEXT]`
- Release version: `[LANGUAGE]` (e.g., v2.4.0)
- Audience: `[FRAMEWORK]` (e.g., end users, developers, QA team)
- Tone: professional, concise, non-technical where possible
- OS / platform: `[OS]`

**Expected vs Actual**
- Desired output: polished release notes in the standard format
- Current state: raw list of commits, tickets, or change descriptions

**Evidence**
- Commits or change list: `[LOGS]`
- Ticket references: `[SPEC_REFERENCE]`
- Config or dependency changes: `[CONFIG_FILE]`
- Previous release notes for style reference: `[RECENT_CHANGE]`

**Output Request**
Return formatted release notes with sections for: New Features, Bug Fixes, Breaking Changes, Deprecations, and Known Issues. Use plain language. Each item should be one clear sentence.

---

## Reusable prompt

```
## Release Notes Request

**Goal:** Write release notes for [PROJECT_CONTEXT] version [LANGUAGE] targeting [FRAMEWORK].

**Context:**
- Project: [PROJECT_CONTEXT]
- Version: [LANGUAGE]
- Audience: [FRAMEWORK]
- Tone: professional, concise, plain language
- Platform: [OS]

**Desired output:**
Polished release notes organized by section (New Features, Bug Fixes, Breaking Changes, Deprecations, Known Issues).

**Current state:**
Raw change list or commits provided below.

**Evidence — commits / change list:**
[LOGS]

**Ticket references:**
[SPEC_REFERENCE]

**Config or dependency changes:**
[CONFIG_FILE]

**Previous release notes (for style reference):**
[RECENT_CHANGE]

**Output format:**
## Release Notes — [PROJECT_CONTEXT] [LANGUAGE]

### New Features
- [one-sentence description per item]

### Bug Fixes
- [one-sentence description per item]

### Breaking Changes
- [description + migration guidance if needed]

### Deprecations
- [what is deprecated and what to use instead]

### Known Issues
- [short description + workaround if available]
```

---

## Expected output format

Markdown document with five sections: New Features, Bug Fixes, Breaking Changes, Deprecations, Known Issues. Each item is a single clear sentence. Breaking Changes include a short migration note.

---

## Notes / limitations

- Replace every `[PLACEHOLDER]` before sending.
- If there are no items in a section (e.g., no known issues), omit that section.
- Keep language non-technical for end-user audiences; include technical detail for developer audiences.
- Always review the generated notes to ensure accuracy — AI may misinterpret commit messages.
