# Lead Center Domain Model

## Purpose

The Lead Center domain captures and manages demand before a person becomes an active student.

It owns the operational funnel from initial lead capture to conversion handoff. It does not own the full student lifecycle after conversion.

## Bounded Context

Lead Center is a bounded context inside Drum Family OS.

It owns:

- Lead identity.
- Lead contact methods.
- Lead source.
- Lead lifecycle status.
- Lead qualification state.
- Lead assignment.
- Lead activities and timeline.
- Trial lesson intent and handoff.
- Conversion handoff record.
- Lead loss and duplicate resolution.

It references but does not own:

- Branch.
- User.
- Teacher.
- Student.
- Schedule slot.
- Payment.
- Marketing campaign.

## Aggregate: Lead

`Lead` is the aggregate root.

Primary responsibility:

- Protect lifecycle transitions.
- Keep lead contact data coherent.
- Track operational ownership.
- Preserve conversion history.
- Emit domain events.

Core attributes:

- `id`
- `organization_id`
- `branch_id`
- `source`
- `status`
- `qualification`
- `person_name`
- `preferred_instrument`
- `age_group`
- `contact_methods`
- `assigned_user_id`
- `created_at`
- `updated_at`

## Entities

### LeadContact

Represents a contact method for a lead.

Examples:

- Phone.
- Telegram.
- Email.
- Parent phone.
- Social network profile.

Rules:

- A lead must have at least one contact method before operational processing.
- Contact methods may require consent metadata.
- One contact method may be marked as primary.

### LeadActivity

Represents an operational action or note in the lead timeline.

Examples:

- Incoming request received.
- First call made.
- Message sent.
- Trial discussed.
- Follow-up scheduled.
- Loss reason recorded.

### LeadAssignment

Represents responsibility for lead processing.

Examples:

- Assigned to administrator.
- Reassigned to branch manager.
- Escalated to owner.

### TrialRequest

Represents intent to book or complete a trial lesson.

Lead Center tracks the request and handoff. Schedule owns final calendar availability and confirmed lesson slots.

### ConversionHandoff

Represents the result of successful conversion from lead to downstream student lifecycle.

Lead Center must preserve:

- Converted lead id.
- Target student id if available.
- Conversion timestamp.
- Conversion source status.

## Value Objects

### LeadSource

Describes where the lead came from.

Examples:

- Website.
- Telegram.
- Phone.
- Referral.
- Instagram.
- Event.
- Walk-in.
- Partner.

### LeadStatus

Allowed draft statuses:

- `captured`
- `contacted`
- `qualified`
- `trial_requested`
- `trial_scheduled`
- `trial_completed`
- `converted`
- `lost`
- `duplicate`
- `archived`

### Qualification

Describes whether the lead is operationally ready for conversion work.

Draft fields:

- `interest_level`
- `preferred_instrument`
- `preferred_branch_id`
- `preferred_schedule`
- `budget_readiness`
- `age_group`
- `decision_maker`

### LossReason

Required when a lead moves to `lost`.

Examples:

- No response.
- Too expensive.
- Wrong location.
- Schedule mismatch.
- Chose competitor.
- Not ready yet.
- Duplicate.

## Lifecycle Rules

Draft lifecycle:

```text
captured -> contacted -> qualified -> trial_requested -> trial_scheduled -> trial_completed -> converted
```

Allowed alternative transitions:

- Any active status may move to `lost` with a reason.
- Any active status may move to `duplicate` with a primary lead reference.
- `lost` may move back to `contacted` when reactivated.
- `converted` should be terminal inside Lead Center.

## Domain Events

Lead Center should emit events for important state changes.

See [Events](EVENTS.md).

