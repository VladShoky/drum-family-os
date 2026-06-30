# AGENTS.md

## Purpose

This document defines the operating rules for all AI agents contributing to Drum Family OS. It is the primary source of guidance for repository conduct, implementation discipline, documentation standards, and collaboration workflows.

All agents must read this file before making changes to the repository.

## 1. Project Goal

Drum Family OS is a platform for organizing, operating, and scaling the Drum Family ecosystem. The project is intended to become the central digital operating system for community management, education, events, content, business processes, and future product modules related to Drum Family.

The repository must evolve deliberately from documentation and architecture toward implementation. Early work should clarify the product, domain model, technical foundation, and long-term maintainability before application code is introduced.

## 2. Platform Mission

The mission of Drum Family OS is to provide a reliable, extensible, and human-centered platform that helps the Drum Family team run its creative, educational, and business activities with clarity and consistency.

The platform should:

- Support real operational workflows, not speculative features.
- Keep the ecosystem organized as it grows.
- Reduce manual coordination where automation is appropriate.
- Preserve the identity, culture, and quality standards of Drum Family.
- Make future development faster by establishing strong architectural foundations.

## 3. Development Principles

All agents must follow these principles:

- Understand the existing repository before making changes.
- Prefer small, focused changes over broad rewrites.
- Keep documentation, architecture, and implementation aligned.
- Avoid premature application scaffolding until the project direction is approved.
- Optimize for maintainability, readability, and operational clarity.
- Treat the repository as a long-term open-source-quality codebase.
- Use established conventions consistently once they exist.
- Make decisions explicit when they affect architecture, product scope, or team workflow.
- Preserve user work and never overwrite unrelated changes.
- Leave the repository in a clean, understandable state after every task.

## 4. Actions Requiring Approval

Agents must not perform the following actions without explicit approval:

- Create an application, framework scaffold, package manager setup, or runtime implementation.
- Add production dependencies.
- Change the selected technology stack.
- Rewrite architecture documents or product direction.
- Delete, rename, or move existing project files.
- Modify CI/CD, deployment, hosting, or infrastructure configuration.
- Introduce authentication, payment, analytics, AI, or external service integrations.
- Add secrets, credentials, API keys, tokens, or private configuration.
- Change database schema strategy or persistence technology.
- Push changes to a remote repository unless explicitly requested.
- Create Pull Requests unless explicitly requested.
- Reformat the entire repository without a specific formatting task.

When in doubt, stop and ask for confirmation.

## 5. Code Style

No application code should be added until implementation is explicitly requested.

When code is eventually introduced:

- Follow the conventions of the chosen language, framework, and repository structure.
- Prefer simple, readable code over clever abstractions.
- Keep modules small and cohesive.
- Use meaningful names for files, functions, classes, variables, and types.
- Avoid hidden side effects and implicit global state.
- Validate inputs at system boundaries.
- Handle errors intentionally and consistently.
- Keep formatting deterministic through approved tooling.
- Do not mix unrelated refactoring with feature work.
- Add comments only when they explain non-obvious intent, tradeoffs, or constraints.

## 6. Commit Guidelines

Commits must be clear, focused, and easy to review.

Use concise imperative commit messages:

```text
Add initial repository structure
Document agent contribution rules
Define platform architecture principles
```

Commit rules:

- One logical change per commit.
- Keep unrelated changes out of the same commit.
- Do not commit generated files unless they are intentionally part of the repository.
- Do not commit secrets or local machine configuration.
- Review staged files before committing.
- Prefer clear wording over overly formal prefixes unless a convention is adopted later.

## 7. Pull Request Rules

Pull Requests must be reviewable and purpose-driven.

Each PR should include:

- A clear title.
- A short summary of what changed.
- The reason for the change.
- Links to related tasks, documents, or decisions when available.
- Testing or verification notes.
- Any risks, limitations, or follow-up work.

PR rules:

- Keep PRs small enough to review effectively.
- Do not combine unrelated product, architecture, and implementation changes.
- Do not hide breaking changes.
- Update documentation when behavior, architecture, or workflows change.
- Resolve review comments through follow-up commits unless the reviewer requests otherwise.
- Do not mark a PR ready for review until it is internally checked.

## 8. Documentation Rules

Documentation is part of the product and must be maintained with the same care as code.

Agents must:

- Write documentation in clear professional English unless instructed otherwise.
- Keep documents structured with descriptive headings.
- Prefer explicit decisions over vague intentions.
- Record assumptions when a decision depends on incomplete information.
- Update related documents when changing product scope, architecture, modules, or workflows.
- Avoid marketing language in technical documents.
- Avoid duplicating the same source of truth across multiple files.
- Use `docs/` for product, business, roadmap, and module documentation.
- Use `architecture/` for system design, technical decisions, and stack-level guidance.
- Use `tasks/` for implementation planning and execution notes when requested.
- Use `prompts/` for reusable AI prompts and agent workflows when requested.

Empty placeholder files may remain empty until their content is explicitly requested.

## 9. Testing Rules

No test framework should be added until application implementation is approved.

When tests are introduced:

- Add tests for business-critical behavior.
- Prefer meaningful coverage over superficial coverage.
- Keep tests deterministic and independent.
- Test public behavior rather than private implementation details.
- Include regression tests for bug fixes.
- Keep test data minimal, readable, and safe.
- Document how to run the test suite.
- Do not skip or weaken tests to make a change pass.
- If a test cannot be added, explain why in the PR or task notes.

## 10. Architecture Rules

Architecture must support long-term growth without forcing premature complexity.

Agents must:

- Start from documented product needs before selecting technical patterns.
- Keep boundaries clear between frontend, backend, mobile, API, database, and design concerns.
- Avoid framework lock-in until the stack is approved.
- Prefer modularity where it protects domain clarity.
- Avoid distributed systems complexity unless clearly justified.
- Keep data ownership and domain boundaries explicit.
- Treat authentication, authorization, billing, and personal data as high-risk areas.
- Document architectural decisions before implementing irreversible choices.
- Maintain a separation between conceptual architecture and implementation details.
- Ensure new modules can be understood, tested, and replaced independently.

The architecture should remain practical: simple enough for the current stage, strong enough for future scale.

## Agent Conduct

Before completing a task, every agent should verify:

- The requested scope was followed.
- No unrelated files were changed.
- No application code was introduced unless requested.
- Documentation remains consistent.
- The repository state is understandable for the next contributor.

If a task is ambiguous, agents should ask for clarification instead of guessing in ways that could affect product direction, architecture, or repository history.
