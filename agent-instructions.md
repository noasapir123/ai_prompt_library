# Agent Instructions

These instructions tell an AI agent how to use this repository when helping a user.

---

## When to apply these instructions

Apply these instructions whenever you are helping a user in a workspace that contains this `ai_prompt_library` folder as a sibling repository.

---

## Step-by-step process

### 1. Understand the user's task
Before searching for prompts, make sure you clearly understand what the user is trying to do. If the request is ambiguous, ask one focused clarifying question — not a list of questions.

### 2. Search this repository for a relevant prompt
Look in the `prompts/` folder for the closest match:

| Task type | Where to look |
|-----------|--------------|
| Code review | `prompts/code-review/` |
| Debugging | `prompts/debugging/` |
| Documentation | `prompts/documentation/` |
| Email or message | `prompts/emails/` |
| Validation or coverage | `prompts/validation/` |
| Unknown / general | `templates/prompt-template.md` |

### 3. Use the closest matching prompt as your base
Open the prompt file. Read the **Purpose** and **When to use** sections to confirm it is the right fit. If multiple prompts are relevant, combine them.

### 4. Ensure all 5 elements are present
Before generating your answer, confirm that the following five elements are covered — either from what the user already provided or from what you will ask:

1. **Goal** — What does the user want to achieve?
2. **Context** — What is the environment, language, framework, project structure, or relevant background?
3. **Expected vs Actual** — What should happen versus what is happening (or desired state versus current state)?
4. **Evidence** — Has the user provided code, errors, logs, configs, stack traces, or spec references?
5. **Output Request** — What format does the user want? (step-by-step, code fix, summary, email draft, etc.)

### 5. Ask for missing context — but only when necessary
If one of the five elements is missing and you cannot reasonably infer it, ask the user for that specific piece of information. Do not ask for information that is already clear from context.

**Ask for:**
- Language or framework if not obvious and it changes the answer
- Specific error message or log output if debugging
- Desired output format if not specified

**Do not ask for:**
- Information you can infer from the code or project
- Personal preferences that do not affect correctness

### 6. Do not invent project-specific facts
Never assume specific class names, function names, file paths, database schemas, API contracts, or business logic that the user has not provided. Use the placeholders (`[FILE_PATH]`, `[FUNCTION_NAME]`, etc.) and ask the user to fill them in if needed.

### 7. Generate a structured, reviewable answer
Structure your response so it is easy for a human to review:

- State which prompt or guideline you used (e.g., "Using `prompts/debugging/debug-regression-failure.md`").
- Organize the output using the sections the user expects (see the relevant prompt file for its **Expected output format**).
- Use headings, numbered lists, or code blocks as appropriate.
- Keep the language plain and practical.

### 8. Remind the user to review the output
End any AI-generated fix, document, or message with a short reminder:

> ⚠️ Review this output carefully before using it. AI answers can contain mistakes.

---

## Rules summary

| Rule | Description |
|------|-------------|
| Use existing prompts | Always base answers on a prompt from this library when one exists. |
| Cover all 5 elements | Goal, Context, Expected vs Actual, Evidence, Output Request must all be addressed. |
| Ask minimally | Ask only for what is genuinely missing. |
| No invented facts | Never make up project-specific details. |
| Cite the prompt | Always say which prompt file or guideline you followed. |
| Structured output | Format answers so they are easy to read and review. |
| Human review | Always remind the user to review AI output before use. |

---

## Examples folder note

The `examples/` folder contains reference-only material. Do **not** surface examples by default. Only share them if the user explicitly asks to see an example prompt or a demonstration.
