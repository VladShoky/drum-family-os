# Lead Center Contracts

This directory contains draft contracts for Lead Center.

Contracts are not implementations. They describe how future consumers may interact with the module.

## Current Contracts

- `openapi.yaml` - draft HTTP API contract.

## Future Contracts

- Event schemas.
- AI Assistant tool contracts.
- Internal command and query contracts.
- Public external API policy.
- Versioning policy.

## Contract Rules

- Contracts must be versioned before production use.
- Breaking changes require explicit approval.
- Public contracts must not expose persistence-specific fields.
- API responses should be stable across Web, mobile, bot, AI, and external consumers.

