# Prompt Architect

[![skills.sh](https://skills.sh/b/gent124/prompt-architect)](https://skills.sh/gent124/prompt-architect)

Turn rough developer requests into concise, outcome-focused prompts that autonomous coding agents can execute directly.

Prompt Architect preserves the technical context that matters, removes premature implementation guesses, adds relevant engineering expectations, and defines observable success criteria.

This repository also includes Clear Task Prompts for rewriting requests in any domain.

| Skill | Use it for |
| --- | --- |
| [prompt-architect](SKILL.md) | Coding and engineering prompts for autonomous agents. |
| [clear-task-prompts](skills/clear-task-prompts/SKILL.md) | Prompts for writing, research, analysis, planning, creative work, and coding. |

## Install

Install Prompt Architect with the open Agent Skills CLI:

```bash
npx skills add gent124/prompt-architect
```

Install globally for Codex:

```bash
npx skills add gent124/prompt-architect --global --agent codex --yes
```

Both skills follow the portable Agent Skills format and can be installed for agents supported by the Skills CLI.

Install Clear Task Prompts globally for Claude Code:

```bash
npx skills add gent124/prompt-architect --full-depth --skill clear-task-prompts --global --agent claude-code
```

For Codex, use `--agent codex` instead. To choose between both skills interactively:

```bash
npx skills add gent124/prompt-architect --full-depth
```

`--full-depth` includes the skill under `skills/` alongside the original root skill.

## Use

For a general request, ask:

```text
Use clear-task-prompts to improve this request:
write an email asking my landlord to repair the heating
```

Clear Task Prompts preserves your intent and constraints and returns a ready-to-use prompt without carrying out the underlying task.

Ask your agent to rewrite or improve a coding prompt:

```text
Use prompt-architect to improve this request:
make notes endpoint faster
```

The skill turns that request into a structured prompt covering:

- the desired outcome
- relevant repository context
- functional and compatibility requirements
- task-specific engineering expectations
- observable success criteria
- expected deliverables

## Example

Input:

```text
make notes endpoint faster
```

Output:

```markdown
# Goal

Improve the performance of the notes endpoint while preserving existing API behavior.

# Context

Inspect the current implementation, database access patterns, and performance infrastructure to identify the bottleneck.

# Requirements

- Identify the root cause before optimizing.
- Preserve API behavior.
- Follow existing architecture.
- Add regression coverage.
- Avoid unnecessary changes.

# Performance Expectations

- Establish a baseline where possible.
- Use evidence to identify bottlenecks.
- Compare results after optimization.

# Success Criteria

- The improvement is measurable where possible.
- Existing behavior remains unchanged.
- Tests pass.
```

## Supported Tasks

Prompt Architect adapts its output to:

- feature development
- debugging
- refactoring
- migrations
- performance work
- security-sensitive changes
- general engineering changes

## License

[MIT](LICENSE)
