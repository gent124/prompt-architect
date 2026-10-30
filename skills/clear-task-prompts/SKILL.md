---
name: clear-task-prompts
description: Rewrite rough requests into clear, concise prompts for any domain. Use when asked to draft or improve a prompt; preserve intent and constraints without executing the underlying task.
---

# Clear Task Prompts

Turn the user's request into a standalone prompt that clearly communicates the intended outcome. Preserve the user's meaning, scope, and constraints. Use direct, natural language and only as much detail as the task needs.

## Understand the intent

- Use the request, supplied materials, and relevant conversation context. Let later explicit corrections replace earlier conflicting choices.
- Identify what the user wants accomplished or produced. Preserve the full requested scope without adding new goals.
- Distinguish requirements from suggestions, examples, and reference material. Do not turn optional ideas or example-specific details into requirements.
- Preserve exact names, numbers, paths, and required wording when relevant.
- Do not invent facts, sources, constraints, permissions, available resources, or completed work.
- Ask a concise clarification only when missing information would materially change the prompt and cannot reasonably be left open or resolved during the task. Otherwise proceed without filling gaps with guesses.

## Write the prompt

Lead with the action and intended result. Include whichever of these help the recipient complete the task:

- Relevant context and source material.
- Requirements and scope boundaries.
- Existing content, behavior, or decisions that must remain intact.
- The expected deliverable, including audience, tone, format, or length when supported by the request.
- Appropriate success criteria or verification steps when useful.

Make the prompt understandable without access to earlier conversation. Include essential context and identify any materials the recipient needs; do not imply access to unavailable files or tools.

Clarify vague wording using details supported by the request. Do not choose an unrequested solution or narrow intentionally open-ended or creative work.

When refining existing work, preserve relevant conventions and unaffected parts. Do not expand a focused change into a broader project.

Make success criteria fit the task. Use concrete checks for functional requirements and relevant qualities for subjective work. Do not invent numerical targets or force testing onto every prompt.

Carry forward existing approval boundaries and limits on external actions. Rewriting a prompt does not grant additional authorization.

Use one paragraph for a simple request. Use a short opening and a flat list for multiple requirements. Add headings only when they improve readability; do not impose a fixed template or word count.

## Final check

Remove repetition, filler, unsupported assumptions, and process instructions that do not affect the result. Check that no important requirement was lost while shortening.

Return only the ready-to-use prompt unless the user requests explanation or alternatives. Do not execute, research, or create artifacts for the underlying task unless separately requested.