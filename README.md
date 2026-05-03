# AI Prompt Library

A shared library of reusable prompts, prompt templates, examples, and agent instructions for AI-assisted work.

---

## What this repository is

This repository stores structured, reusable prompts that you and your AI agents can use every day. Instead of writing the same prompt from scratch each time, you pick the closest match, fill in the placeholders, and get consistent, high-quality results.

---

## Why it exists

Vague prompts produce vague answers. By organizing every prompt around a clear 5-element framework, you give the AI exactly the information it needs to return practical, reviewable output.

---

## The 5 elements of an effective prompt

Every prompt in this library is built around these five elements:

| # | Element | What to include |
|---|---------|----------------|
| 1 | **Goal** | What you want to achieve — build, fix, review, summarize, decide, write. |
| 2 | **Context** | Environment and background — language, framework, OS, dependencies, project structure, tool, workflow, constraints, assumptions, business or technical context. |
| 3 | **Expected vs Actual** | The gap — what should happen versus what does happen. For non-debugging tasks: the desired result versus the current state. |
| 4 | **Evidence** | Supporting information — code snippets, error messages, stack traces, logs, config files, screenshots, command output, spec references, coverage results, previous attempts. |
| 5 | **Output Request** | The exact answer format — step-by-step debug guide, code review, suggested fix, diff, explanation, professional email, technical summary, risk analysis, checklist, table. |

---

## How to use this repo manually

1. Browse the `prompts/` folder and find the category that matches your task.
2. Open the prompt file and read the **When to use** section.
3. Copy the fenced code block (the reusable prompt).
4. Replace every `[PLACEHOLDER]` with your actual values.
5. Paste the filled-in prompt into your AI chat or IDE.
6. Review the AI's output before using it.

---

## How to use it with an AI agent in VS Code

Place this repository **next to your other project folders** inside the same VS Code workspace:

```
workspace/
├── my-project/
└── ai_prompt_library/
```

Open the workspace folder in VS Code (`code .` from the workspace root). When GitHub Copilot or another agent works on `my-project`, it can see `ai_prompt_library` as a sibling folder. Point the agent to `agent-instructions.md` so it knows how to find and use the prompts automatically.

Example instruction to the agent:

> "Read `../ai_prompt_library/agent-instructions.md` and follow those rules when helping me."

---

## Recommended workspace structure

```
workspace/
├── my-project/          ← your actual code lives here
└── ai_prompt_library/   ← this repo
    ├── README.md
    ├── agent-instructions.md
    ├── prompts/
    │   ├── code-review/
    │   ├── debugging/
    │   ├── documentation/
    │   ├── emails/
    │   └── validation/
    ├── templates/
    └── examples/
```

---

## Best practices for adding new prompts

1. Copy `templates/prompt-template.md` as your starting point.
2. Fill in all five sections: Goal, Context, Expected vs Actual, Evidence, Output Request.
3. Use the standard placeholders (`[GOAL]`, `[LANGUAGE]`, `[ERROR_MESSAGE]`, etc.) so prompts stay generic and reusable.
4. Write in simple, plain English — avoid jargon.
5. Keep each file self-contained and copy-pasteable.
6. Place the file in the most relevant subfolder under `prompts/`.
7. Use a fenced code block for the reusable prompt body.

---

## Folder overview

| Folder | Purpose |
|--------|---------|
| `prompts/code-review/` | Prompts for reviewing code quality, correctness, and style. |
| `prompts/debugging/` | Prompts for diagnosing and fixing bugs or unexpected behavior. |
| `prompts/documentation/` | Prompts for writing release notes and technical summaries. |
| `prompts/emails/` | Prompts for writing professional messages and manager updates. |
| `prompts/validation/` | Prompts for analyzing coverage gaps and spec alignment. |
| `templates/` | Generic skeletons for creating new prompts and output formats. |
| `examples/` | Reference examples showing weak vs. good prompts. Agents should not use these by default. |

---

## ⚠️ Important warning

> **AI output must always be reviewed by a human before use.**
>
> These prompts help you get better answers from AI tools, but no AI output is guaranteed to be correct, complete, or safe. Always read, verify, and approve AI-generated content before committing code, sending a message, or publishing documentation.