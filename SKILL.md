---
name: craft-ai-prompts
description: Turn vague ideas, goals, or rough questions into clear, ready-to-copy prompts for AI models. Use when the user asks how to ask an AI, requests a prompt or question template, wants an existing prompt improved, needs requirements converted into a structured prompt, or needs prompts for research, planning, comparison, coding, learning, writing, image generation, video, or storyboards.
---

# Craft AI Prompts

Transform the user's intent into a prompt that another AI can execute reliably. Match the user's language and keep domain-specific terminology intact.

## Workflow

1. Identify the intended outcome, target AI or tool if known, available context, constraints, deliverables, and success criteria.
2. Select the closest pattern from [references/prompt-patterns.md](references/prompt-patterns.md). Read only the relevant section unless the request spans several task types.
3. Combine patterns when necessary; do not force a request into a single category.
4. Fill every field supported by the user's message. Use explicit placeholders such as `[请填写预算]` only for genuinely missing values.
5. Ask one to three focused questions only when the missing information would materially change the prompt. Otherwise, state brief assumptions and proceed.
6. Return a complete, ready-to-copy prompt in a fenced `text` block.

## Prompt Construction Rules

- Prefer the structure: role, objective, context, tasks, constraints, output format, quality criteria, and uncertainty handling.
- Make the requested deliverable measurable and explicit. Replace vague words such as “详细” with concrete sections, quantities, formats, or evaluation criteria when possible.
- Include only useful constraints. Do not inflate prompts with ceremonial role-play or repeated instructions.
- Tell the target AI to distinguish facts, assumptions, and recommendations when accuracy matters.
- For current or research-heavy topics, require fresh authoritative sources, dates, direct links, and transparent treatment of conflicting evidence.
- For creative tasks, preserve room for creative judgment while locking continuity, mandatory elements, forbidden elements, aspect ratio, and output count.
- For technical tasks, include environment, inputs, expected behavior, full errors, reproducibility, validation, and runnable deliverables.
- Never invent personal details, requirements, sources, tool capabilities, or facts the user did not provide.
- Do not answer the underlying task unless the user asks for both the prompt and the result.

## Output Modes

Choose the smallest useful mode:

- **Quick:** One polished prompt only.
- **Standard:** One polished prompt plus a short list of placeholders or assumptions.
- **Professional:** A polished prompt, a compact alternative, and optional model-specific notes when those differences materially affect results.

Default to Standard. Do not present multiple versions unless they provide a meaningful tradeoff.

## Output Format

Use this structure when applicable:

```text
【可直接复制的提问词】
...
```

Then add only what helps the user apply it:

- `需要补充：` unresolved fields that materially affect the result.
- `使用建议：` at most three concise notes, only when model or tool behavior matters.

## Quality Check

Before returning, verify that the prompt:

1. States the real outcome rather than only a broad topic.
2. Supplies enough context to avoid obvious guessing.
3. Defines tasks, constraints, and output structure without contradiction.
4. Includes a success standard or self-check where useful.
5. Handles missing or uncertain information without fabrication.
6. Can be copied directly without requiring the user to rewrite its structure.
