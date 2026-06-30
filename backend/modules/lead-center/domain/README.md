# Lead Center Domain Layer

This directory is reserved for Lead Center domain concepts.

No executable domain code exists yet. The current purpose is to define the intended module boundaries before implementation.

## Future Responsibilities

- Aggregates.
- Entities.
- Value objects.
- Domain services.
- Domain events.
- Domain invariants.

## Domain Ownership

The domain layer must own Lead Center rules independently from any delivery interface.

Examples of rules that belong here:

- A lead must have at least one contact method before operational processing.
- A converted lead must preserve a reference to the created student or conversion target.
- A lost lead must include a loss reason.
- A duplicate lead must reference the primary lead.
- Status transitions must follow the approved lifecycle.

## Forbidden Dependencies

The domain layer must not depend on:

- HTTP controllers.
- Telegram bot handlers.
- Mobile-specific models.
- Database clients.
- External APIs.
- Framework-specific dependency injection.

