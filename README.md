# Prompt Architect

[![skills.sh](https://skills.sh/b/gent124/prompt-architect)](https://skills.sh/gent124/prompt-architect)

Turn rough developer requests into concise, outcome-focused prompts that autonomous coding agents can execute directly.

Prompt Architect preserves the technical context that matters, removes premature implementation guesses, adds relevant engineering expectations, and defines observable success criteria.

## Install

Install with the open Agent Skills CLI:

```bash
npx skills add gent124/prompt-architect
```

Install globally for Codex:

```bash
npx skills add gent124/prompt-architect --global --agent codex --yes
```

The skill follows the portable Agent Skills format and can also be installed for other agents supported by the Skills CLI.

## Use

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
