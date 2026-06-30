# Lead Center Infrastructure Layer

This directory is reserved for future technical implementations.

No database connection, repository implementation, queue, event bus, external service adapter, or infrastructure configuration exists yet.

## Future Responsibilities

- Persistence adapters.
- Event publication adapters.
- External lead source adapters.
- Search index adapters.
- Audit log sinks.
- Integration gateways.

## Infrastructure Rule

Infrastructure must implement ports defined by the application layer. It must not define domain behavior.

## Persistence Status

The data model is documented as a conceptual model only. No database technology has been selected or connected.

