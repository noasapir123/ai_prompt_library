# Casual Work Message

## Purpose
Ask an AI to help write a clear, natural, polite casual message to a colleague — for chat (Slack, Teams), a quick email, or an informal update.

## When to use
Use this prompt when you need to write a short work message to a peer, teammate, or collaborator in a friendly but professional tone.

---

## The 5 elements

**Goal**
Write a short, natural, and polite work message to `[PROJECT_CONTEXT]` (the recipient) about `[GOAL]`.

**Context**
- Recipient: `[PROJECT_CONTEXT]` (name and role if relevant)
- Relationship: `[FRAMEWORK]` (e.g., close colleague, new teammate, external collaborator)
- Platform: `[OS]` (e.g., Slack, Teams, email)
- Tone: friendly, casual, professional — not overly formal

**Expected vs Actual**
- Desired output: a short, clear, natural message ready to send
- Current state: `[ACTUAL_BEHAVIOR]` (e.g., no draft yet, or current draft that needs improvement)

**Evidence**
- Key facts to include: `[LOGS]`
- Dates or deadlines: `[RECENT_CHANGE]`
- Decisions or constraints to mention: `[CONFIG_FILE]`
- Current draft (if any): `[ACTUAL_BEHAVIOR]`

**Output Request**
Return a ready-to-send message. Optionally offer 2–3 tone variations (friendly, neutral, brief) so the user can choose.

---

## Reusable prompt

```
## Casual Work Message Request

**Goal:** Write a short, natural, polite work message to [PROJECT_CONTEXT] about [GOAL].

**Context:**
- Recipient: [PROJECT_CONTEXT]
- Relationship: [FRAMEWORK]
- Platform: [OS]
- Tone: casual, friendly, professional

**Desired output:**
A ready-to-send message. Offer 2–3 tone options if helpful.

**Current state / draft:**
[ACTUAL_BEHAVIOR]

**Key facts to include:**
[LOGS]

**Dates or deadlines:**
[RECENT_CHANGE]

**Decisions or constraints to mention:**
[CONFIG_FILE]

**Output format:**
Option A (friendly):
[message]

Option B (neutral):
[message]

Option C (brief):
[message]
```

---

## Expected output format

Two or three short message options labeled by tone (friendly / neutral / brief). Each option is ready to copy and send. No explanations needed unless the user asks.

---

## Notes / limitations

- Replace every `[PLACEHOLDER]` before sending.
- Keep messages short — most casual work messages should be under 80 words.
- Always read the generated message before sending — make sure the tone fits your actual relationship with the recipient.
- Do not include sensitive information (personal data, confidential decisions) in the prompt.
