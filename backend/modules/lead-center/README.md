# Lead Center

Lead Center is the first business module of Drum Family OS.

It is responsible for the operational path from first incoming interest to a qualified opportunity for conversion into an active student. It is not a standalone CRM and it must not become a generic contact database. Its purpose is to protect and improve the lead-to-active-student funnel.

## Status

This module is an architectural scaffold only.

There is no business logic, controller implementation, UI, database connection, runtime framework, or infrastructure integration in this directory.

## Architectural Position

Lead Center is designed as an independent service inside a modular monolith.

The module must expose clear contracts for:

- Web application.
- Telegram bot.
- Mobile application.
- AI Assistant.
- External API.
- Internal Drum Family OS modules.

No interface may own Lead Center business rules. Interfaces should call module contracts and let the module protect its own domain invariants.

## Module Goal

Lead Center exists to reduce lead loss and increase the number of active students by making the first stage of the student lifecycle visible, measurable, and operationally controlled.

Primary outcomes:

- Capture incoming demand from multiple sources.
- Track first response and qualification.
- Route leads to the right branch or responsible user.
- Support trial lesson booking flow without owning the Schedule module.
- Track conversion from lead to active student without owning the Student lifecycle.
- Emit reliable events for Analytics, AI Assistant, CRM, Schedule, and other modules.

## Non-Goals

Lead Center does not own:

- Full CRM relationship history.
- Student profile after conversion.
- Lesson scheduling engine.
- Payments and invoices.
- Learning progress.
- Marketing automation.
- Community features.
- Franchise operations.
- UI-specific workflows.

## Directory Structure

```text
backend/modules/lead-center/
|-- README.md
|-- application/
|   `-- README.md
|-- contracts/
|   |-- README.md
|   `-- openapi.yaml
|-- docs/
|   |-- API.md
|   |-- DATA_MODEL.md
|   |-- DOMAIN_MODEL.md
|   |-- ER_DIAGRAM.md
|   `-- EVENTS.md
|-- domain/
|   `-- README.md
|-- infrastructure/
|   `-- README.md
`-- interfaces/
    `-- README.md
```

## Layer Responsibilities

| Layer | Responsibility |
| --- | --- |
| `domain/` | Domain concepts, aggregates, invariants, value objects, domain events. |
| `application/` | Future use case orchestration, command/query contracts, authorization boundaries. |
| `interfaces/` | Future adapters for HTTP, Telegram, mobile, AI Assistant, and external API. |
| `infrastructure/` | Future persistence, event publication, external source adapters, and technical gateways. |
| `contracts/` | Public and internal contracts such as OpenAPI and event schemas. |
| `docs/` | Architecture and product design documentation for the module. |

## Core Lifecycle

```text
captured
  -> contacted
  -> qualified
  -> trial_requested
  -> trial_scheduled
  -> trial_completed
  -> converted
```

Alternative terminal states:

```text
lost
duplicate
archived
```

The lifecycle is intentionally module-local. Student activation belongs to downstream modules, but Lead Center must preserve the conversion link.

## Integration Principles

- Integrations must use contracts, not direct data access.
- Other modules must consume Lead Center events or application contracts.
- Lead Center may reference external module identifiers, but must not own external module data.
- Schedule owns final lesson availability and booking confirmation.
- CRM owns long-term relationship management after conversion.
- Analytics consumes events and read models.
- AI Assistant may recommend actions but must not bypass module permissions or invariants.

## Key Documents

- [Domain Model](docs/DOMAIN_MODEL.md)
- [Data Model](docs/DATA_MODEL.md)
- [API Description](docs/API.md)
- [Events](docs/EVENTS.md)
- [ER Diagram](docs/ER_DIAGRAM.md)
- [OpenAPI Draft](contracts/openapi.yaml)

