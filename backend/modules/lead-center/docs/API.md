# Lead Center API Description

## Status

This document describes the intended API surface for Lead Center.

No controllers, routes, handlers, or server implementation exist yet.

The draft HTTP contract is documented in [OpenAPI](../contracts/openapi.yaml).

## API Design Goals

- Support Web, Telegram bot, mobile application, AI Assistant, and external API consumers.
- Keep business rules inside Lead Center, not in client interfaces.
- Use stable resource names.
- Keep transport-specific concerns outside the domain layer.
- Provide enough information for operational workflows and analytics.

## Versioning

Draft base path:

```text
/api/v1/lead-center
```

Versioning rules will be finalized before implementation.

## Resources

### Leads

Represents incoming demand from a person or decision maker.

Draft operations:

- Create lead.
- Search leads.
- Get lead by id.
- Update lead.
- Change status.
- Assign lead.
- Mark lead as lost.
- Merge duplicate lead.
- Convert lead.

### Lead Contacts

Represents ways to reach a lead.

Draft operations:

- Add contact method.
- Update contact method.
- Mark primary contact.
- Capture consent.

### Lead Activities

Represents the operational timeline.

Draft operations:

- Add activity.
- Get lead timeline.

### Trial Requests

Represents a request to schedule or track a trial lesson.

Draft operations:

- Create trial request.
- Mark trial as scheduled.
- Mark trial as completed.
- Mark trial as cancelled or no-show.

### Pipeline

Represents aggregate operational view of lead flow.

Draft operations:

- Get pipeline summary.
- Get conversion funnel.
- Get stale leads.

## Draft Endpoint List

| Method | Path | Purpose |
| --- | --- | --- |
| POST | `/api/v1/lead-center/leads` | Create a lead. |
| GET | `/api/v1/lead-center/leads` | Search and filter leads. |
| GET | `/api/v1/lead-center/leads/{leadId}` | Get lead details. |
| PATCH | `/api/v1/lead-center/leads/{leadId}` | Update lead profile fields. |
| POST | `/api/v1/lead-center/leads/{leadId}/status` | Change lead status. |
| POST | `/api/v1/lead-center/leads/{leadId}/assignments` | Assign lead to a user. |
| POST | `/api/v1/lead-center/leads/{leadId}/activities` | Add timeline activity. |
| GET | `/api/v1/lead-center/leads/{leadId}/timeline` | Get lead timeline. |
| POST | `/api/v1/lead-center/leads/{leadId}/trial-requests` | Request trial lesson. |
| PATCH | `/api/v1/lead-center/trial-requests/{trialRequestId}` | Update trial request state. |
| POST | `/api/v1/lead-center/leads/{leadId}/convert` | Convert lead to student handoff. |
| GET | `/api/v1/lead-center/pipeline` | Get operational pipeline summary. |

## Authorization Model Draft

Detailed permissions are not implemented yet.

Initial permission concepts:

- Owner can view network-level data.
- Branch Manager can view and manage branch leads.
- Administrator can process and update leads in assigned branches.
- Teacher may receive limited trial context.
- AI Assistant may read context and propose actions under user authorization.
- External API clients require scoped access.

## Idempotency

Create and state-changing operations should support idempotency before production use, especially for:

- External lead capture.
- Telegram bot submissions.
- Mobile submissions.
- AI-assisted actions.
- External API integrations.

## Error Model Draft

Future API errors should distinguish:

- Validation error.
- Permission error.
- Not found.
- Conflict.
- Invalid lifecycle transition.
- Duplicate lead.
- External dependency unavailable.

