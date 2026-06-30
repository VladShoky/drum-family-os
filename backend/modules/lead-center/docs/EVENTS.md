# Lead Center Events

## Status

This is the draft event catalog for Lead Center.

No event bus, queue, producer, consumer, or event schema implementation exists yet.

## Event Design Principles

- Events describe facts that already happened.
- Events must be useful to Analytics, AI Assistant, CRM, Schedule, and audit systems.
- Events must not expose transport-specific details as primary data.
- Event payloads should carry identifiers and operational context.
- Sensitive personal data should be minimized.

## Event Envelope Draft

All events should eventually follow a common envelope:

| Field | Purpose |
| --- | --- |
| event_id | Unique event identifier. |
| event_type | Stable event name. |
| event_version | Event schema version. |
| occurred_at | Timestamp when the fact happened. |
| organization_id | Owning network or tenant. |
| correlation_id | Request or workflow correlation id. |
| actor_user_id | User who triggered the action, if available. |
| source | Interface or system source. |
| payload | Event-specific data. |

## Domain Events

### LeadCreated

Emitted when a new lead is captured.

Primary consumers:

- Analytics.
- AI Assistant.
- CRM.
- Branch operations.

### LeadContactAdded

Emitted when a new contact method is attached to a lead.

Primary consumers:

- CRM.
- Audit.
- AI Assistant.

### LeadConsentCaptured

Emitted when communication consent is captured or updated.

Primary consumers:

- Audit.
- CRM.
- External communication systems.

### LeadStatusChanged

Emitted when a lead lifecycle status changes.

Primary consumers:

- Analytics.
- AI Assistant.
- Branch dashboards.

### LeadQualified

Emitted when a lead becomes qualified for conversion work.

Primary consumers:

- Analytics.
- Branch operations.
- AI Assistant.

### LeadAssigned

Emitted when responsibility for a lead changes.

Primary consumers:

- Notifications.
- Branch operations.
- Audit.

### LeadActivityAdded

Emitted when a timeline activity is recorded.

Primary consumers:

- CRM.
- AI Assistant.
- Audit.

### TrialRequested

Emitted when a lead expresses intent to book a trial lesson.

Primary consumers:

- Schedule.
- Branch operations.
- Analytics.

### TrialScheduled

Emitted when a trial lesson has a confirmed schedule reference.

Primary consumers:

- Schedule.
- Analytics.
- CRM.

### TrialCompleted

Emitted when a trial lesson is completed.

Primary consumers:

- Analytics.
- CRM.
- AI Assistant.

### LeadConverted

Emitted when the lead is handed off as a converted student or conversion target.

Primary consumers:

- CRM or Student module.
- Finance.
- Analytics.
- AI Assistant.

### LeadMarkedLost

Emitted when a lead is marked as lost.

Primary consumers:

- Analytics.
- AI Assistant.
- Branch manager dashboards.

### LeadReactivated

Emitted when a lost or inactive lead becomes active again.

Primary consumers:

- Analytics.
- CRM.
- Branch operations.

### DuplicateLeadDetected

Emitted when the module identifies or records a duplicate lead.

Primary consumers:

- CRM.
- Analytics.
- Audit.

### LeadsMerged

Emitted when duplicate lead records are merged or linked.

Primary consumers:

- CRM.
- Analytics.
- Audit.

## Event Ownership

Lead Center owns these events. Other modules may consume them but must not emit them on behalf of Lead Center without going through an approved application contract.

