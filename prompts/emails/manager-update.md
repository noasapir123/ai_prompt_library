# Manager Update

## Purpose
Ask an AI to help write a clear, concise status update message or email to a manager or stakeholder.

## When to use
Use this prompt when you need to send a progress update, blocker notification, or decision request to your manager, a team lead, or a stakeholder.

---

## The 5 elements

**Goal**
Write a professional, concise message to `[PROJECT_CONTEXT]` (the manager/stakeholder) with a status update on `[GOAL]`.

**Context**
- Recipient: `[PROJECT_CONTEXT]` (manager name / role)
- Relationship: `[FRAMEWORK]` (e.g., direct manager, skip-level, external stakeholder)
- Platform: `[OS]` (e.g., email, Slack, Teams)
- Topic: `[GOAL]`
- Tone: professional, clear, concise — not overly casual

**Expected vs Actual**
- Desired output: a polished update message ready to send
- Current state: `[ACTUAL_BEHAVIOR]` (e.g., no draft, or rough notes to transform)

**Evidence**
- Progress so far: `[LOGS]`
- Blockers or risks: `[ERROR_MESSAGE]`
- Upcoming milestones or deadlines: `[RECENT_CHANGE]`
- Decisions needed from the manager: `[CONFIG_FILE]`
- Current draft (if any): `[ACTUAL_BEHAVIOR]`

**Output Request**
Return a ready-to-send message with: a brief summary of progress, current blockers (if any), next steps, and a clear action item or question for the manager (if needed). Offer a subject line if writing an email.

---

## Reusable prompt

```
## Manager Update Request

**Goal:** Write a professional status update message to [PROJECT_CONTEXT] about [GOAL].

**Context:**
- Recipient: [PROJECT_CONTEXT]
- Relationship: [FRAMEWORK]
- Platform: [OS]
- Tone: professional, concise, clear

**Desired output:**
A ready-to-send update message. Include a subject line if writing an email.

**Current state / rough notes:**
[ACTUAL_BEHAVIOR]

**Progress so far:**
[LOGS]

**Blockers or risks:**
[ERROR_MESSAGE]

**Upcoming milestones / deadlines:**
[RECENT_CHANGE]

**Decisions needed:**
[CONFIG_FILE]

**Current draft (if any):**
[STACK_TRACE]

**Output format:**
Subject: [subject line — for email only]

[Message body]

---
Key sections to include:
- Brief progress summary
- Blockers or risks (if any)
- Next steps
- Action item or question for the manager (if any)
```

---

## Expected output format

A ready-to-send message. For email: subject line + body. For chat: a single clear message under 200 words. Key sections: progress summary, blockers, next steps, action item.

---

## Notes / limitations

- Replace every `[PLACEHOLDER]` before sending.
- Be factual and concise — managers prefer a short, clear update over a long explanation.
- Avoid including confidential or sensitive project details in the prompt.
- Always review the message before sending to make sure facts and tone are correct.
