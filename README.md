# Drum Family OS

Drum Family OS is the future operating platform for the Drum Family ecosystem.

The project is currently in its foundation stage. This repository is being prepared as a professional, long-term codebase before application development begins. The first priority is to define the product vision, architecture, documentation standards, and collaboration rules.

## Purpose

Drum Family OS is intended to become a central digital system for organizing and scaling Drum Family operations across education, events, community, content, internal workflows, and future business modules.

The platform should help the team:

- Keep product and operational knowledge organized.
- Turn repeated manual processes into clear digital workflows.
- Support future web, mobile, API, backend, and database development.
- Preserve Drum Family identity while allowing the ecosystem to grow.
- Build a maintainable technical foundation before implementation starts.

## Current Status

This repository does not contain an application yet.

The current phase is focused on:

- Product documentation.
- Architecture planning.
- Technical decision-making.
- Repository structure.
- AI-agent and contributor guidelines.

Application code, framework scaffolding, dependencies, infrastructure, and runtime implementation should not be added until explicitly approved.

## Repository Structure

```text
.
|-- AGENTS.md
|-- README.md
|-- api/
|-- architecture/
|-- backend/
|-- database/
|-- design/
|-- docs/
|-- frontend/
|-- mobile/
|-- prompts/
`-- tasks/
```

## Key Documents

- `README.md` is the entry point for human contributors.
- `AGENTS.md` is the operating guide for AI agents.
- `docs/VISION.md` will define the long-term vision.
- `docs/ROADMAP.md` will define product milestones.
- `docs/PRODUCT.md` will define product requirements and scope.
- `docs/MODULES.md` will describe platform modules.
- `docs/BUSINESS.md` will describe business context and operating model.
- `architecture/ARCHITECTURE.md` will describe system architecture.
- `architecture/TECH_STACK.md` will describe approved technology choices.

## Working Principles

Contributors should keep the repository clear, intentional, and easy to review.

- Make small, focused changes.
- Update documentation when project direction changes.
- Avoid speculative implementation.
- Keep product, architecture, and technical decisions aligned.
- Do not add dependencies or framework scaffolding without approval.
- Do not commit secrets, credentials, tokens, or local configuration.
- Respect the separation between documentation, architecture, backend, frontend, mobile, API, database, and design work.

## For AI Agents

AI agents must read `AGENTS.md` before making changes.

That file defines repository rules for:

- Scope control.
- Code style.
- Commits.
- Pull Requests.
- Documentation.
- Testing.
- Architecture.
- Actions that require approval.

## For Human Contributors

Start with this README, then read the relevant files in `docs/` and `architecture/` as they are created.

Before contributing implementation work, make sure the corresponding product and architecture decisions are documented or explicitly approved.

## License

The project license has not been defined yet.
