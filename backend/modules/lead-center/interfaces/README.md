# Lead Center Interfaces Layer

This directory is reserved for delivery adapters.

No controllers, handlers, routes, bot commands, or UI adapters are implemented yet.

## Future Interface Adapters

- HTTP API adapter for Web and external clients.
- Telegram bot adapter.
- Mobile API adapter.
- AI Assistant tool adapter.
- Internal module adapter.

## Interface Rule

Interfaces must translate transport-specific requests into Lead Center application commands and queries.

They must not contain Lead Center business rules.

## Supported Future Consumers

| Consumer | Expected Integration Style |
| --- | --- |
| Web application | HTTP API and internal contracts. |
| Telegram bot | Application commands through an adapter. |
| Mobile application | HTTP API or mobile gateway. |
| AI Assistant | Tool contracts and read-only analytical context by default. |
| External API | Versioned public API with strict permissions. |

