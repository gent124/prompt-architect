---
name: prompt-architect
description: Transform rough developer requests into concise, outcome-focused prompts optimized for autonomous coding agents such as OpenAI Codex, Claude Code, Cursor, and similar agentic development tools. Use when a user asks to rewrite, improve, structure, or optimize a coding, debugging, feature, migration, security, performance, or refactoring prompt.
---

# Prompt Architect

Rewrite the user's request into a standalone prompt that an autonomous coding agent can execute directly.

Transform implementation guesses into the outcome to achieve, the constraints that matter, and the checks that verify completion. Give the agent enough context to make good engineering decisions without turning the prompt into a design document.

## Transformation Workflow

1. Identify the actual desired outcome.
2. Extract only relevant context:
   - technology stack
   - architecture
   - existing behavior
   - affected modules
   - important constraints
   - previous decisions
3. Remove premature implementation choices unless they are required.
4. Convert step-by-step instructions into outcome-based requirements.
5. Preserve technical details that materially affect implementation.
6. Add only strongly implied constraints.
7. Classify the task type.
8. Add only the expectation sections that materially apply.
9. Return only the rewritten prompt unless the user asks for an explanation.

## Core Rules

### Prefer Outcomes Over Implementation

Do not preserve guesses as requirements.

Bad:

> Replace Prisma with raw SQL.

Good:

> Investigate query performance and apply the appropriate optimization while preserving existing behavior.

### Do Not Invent Context

Include only facts provided by the user. Do not assume frameworks, databases, architecture patterns, infrastructure, deployment models, or existing tools.

If information is missing, instruct the agent to inspect the repository and follow existing patterns.

### Avoid Over-Specification

Do not prescribe implementation details unless:

- migration order matters
- deployment order matters
- security approval is required
- an operation is irreversible
- data integrity depends on sequence

Otherwise, prefer:

> Inspect the existing implementation and make the required changes following the current architecture.

### Keep the Prompt Concise

Include only information that affects implementation decisions, constraints that prevent incorrect behavior, acceptance criteria, and validation requirements.

Avoid generic engineering advice, unnecessary theory, exhaustive edge cases, and speculative requirements.

## Required Output Structure

Always use the following core sections.

### Goal

Describe the desired outcome and behavior that must be preserved.

### Context

Include the relevant stack, architecture, current implementation, affected areas, and previous decisions. If these are unknown, instruct the agent to inspect the repository.

### Requirements

Include functional requirements, compatibility requirements, constraints, prohibited outcomes, and testing expectations.

### Engineering Expectations

Always add this section for coding tasks:

- Follow existing project architecture, conventions, utilities, and patterns.
- Keep changes focused.
- Add or update appropriate tests.
- Avoid unnecessary dependencies.
- Explain important architectural decisions.

### Success Criteria

Define observable completion checks, such as required behavior working, existing behavior being preserved, tests passing, migrations completing safely, measurable performance improvements, or documentation being updated.

### Deliverables

List the expected outputs, such as implementation changes, tests, migrations, documentation, validation results, and a concise summary of decisions.

## Conditional Expectation Sections

Add only the sections that materially apply.

### Feature Expectations

Use for new feature implementation:

- Inspect the current architecture before implementation.
- Identify affected areas.
- Briefly explain the implementation approach.
- Then implement the solution.

Do not add this section for simple fixes or migrations unless a new capability is introduced.

### Debugging Expectations

Use for debugging tasks:

- Investigate and fix the root cause rather than only symptoms.
- Identify affected areas.
- Explain the fix.
- Describe the validation performed.

### Refactoring Expectations

Use only when the main goal is refactoring existing code:

- Preserve existing behavior.
- Improve maintainability and readability.
- Reduce unnecessary complexity.
- Strengthen test coverage where appropriate.

Do not add this section only because old code is removed during a migration.

### Migration Expectations

Use for migrations:

- Identify the current and target states.
- Preserve compatibility where required.
- Consider deployment impact.
- Remove old paths only after the replacement is validated.

Do not automatically add rollback planning unless the migration is high-risk.

### Security Expectations

Use when the task involves authentication, authorization, credentials, secrets, permissions, trust boundaries, or external input handling:

- Preserve secure defaults.
- Do not weaken protections for convenience.
- Validate failure cases.
- Consider affected trust boundaries.

Do not turn normal feature work into a security audit.

### Performance Expectations

Use when the task involves performance:

- Establish a baseline where possible.
- Identify bottlenecks using evidence.
- Avoid speculative optimization.
- Compare results before and after changes.

Do not assume caching, database indexes, or rewrites are needed without evidence.

## Task Classification

Classify the request as one or more of:

- Feature
- Debugging
- Refactoring
- Migration
- Performance
- Security
- General Change

Apply multiple expectation sections only when they materially affect implementation. For example:

- Removing old code during migration is not automatically refactoring.
- Authentication migration is migration and security.
- Performance investigation is debugging and performance.
- Adding a new endpoint is a feature.

## Example

Input:

> make notes endpoint faster

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

# Engineering Expectations

- Follow existing project architecture, conventions, utilities, and patterns.
- Keep changes focused.
- Add or update appropriate tests.
- Avoid unnecessary dependencies.
- Explain important architectural decisions.

# Debugging Expectations

- Investigate and address the root cause rather than only patching symptoms.
- Report affected areas, solution, and validation steps.

# Performance Expectations

- Establish a baseline.
- Use evidence to identify bottlenecks.
- Compare results after optimization.

# Success Criteria

- The performance issue is resolved.
- Improvement is measurable where possible.
- Existing behavior remains unchanged.
- Tests pass.

# Deliverables

- Code changes.
- Tests.
- Root cause summary.
- Validation results.
```
