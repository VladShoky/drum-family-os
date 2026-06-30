# Lead Center Data Model

## Status

This is a conceptual data model.

No database technology is selected. No migrations, repositories, schemas, ORM models, or database connections are implemented.

The model is intended to guide future persistence design while keeping the module independent from a specific storage engine.

## Design Principles

- Lead Center owns its own data.
- Other modules must not directly write Lead Center data.
- External module identifiers may be stored as references.
- Operational history must be preserved.
- Data required for analytics should be captured through events and status history.
- Personal data must be minimized and protected.

## Tables

### lead_center_leads

Primary lead record.

| Field | Type | Required | Notes |
| --- | --- | --- | --- |
| id | uuid | yes | Lead identifier. |
| organization_id | uuid | yes | Owning school network or tenant. |
| branch_id | uuid | no | Preferred or assigned branch reference. |
| source_id | uuid | no | Reference to lead source. |
| status | string | yes | Current lifecycle status. |
| qualification_status | string | no | Draft qualification state. |
| person_name | string | no | Lead or student name. |
| preferred_instrument | string | no | Initial instrument interest. |
| age_group | string | no | Child, teen, adult, unknown, or configured value. |
| assigned_user_id | uuid | no | Responsible staff member reference. |
| converted_student_id | uuid | no | Downstream student reference after conversion. |
| loss_reason | string | no | Required when status is lost. |
| duplicate_of_lead_id | uuid | no | Primary lead reference when duplicate. |
| created_at | datetime | yes | Creation timestamp. |
| updated_at | datetime | yes | Last update timestamp. |
| archived_at | datetime | no | Archive timestamp. |

### lead_center_contacts

Contact methods attached to a lead.

| Field | Type | Required | Notes |
| --- | --- | --- | --- |
| id | uuid | yes | Contact identifier. |
| lead_id | uuid | yes | Parent lead. |
| type | string | yes | phone, email, telegram, social, other. |
| value | string | yes | Contact value. |
| is_primary | boolean | yes | Primary contact marker. |
| consent_status | string | no | Consent state for communication. |
| consent_captured_at | datetime | no | Consent timestamp. |
| created_at | datetime | yes | Creation timestamp. |

### lead_center_sources

Lead source catalog.

| Field | Type | Required | Notes |
| --- | --- | --- | --- |
| id | uuid | yes | Source identifier. |
| organization_id | uuid | yes | Tenant reference. |
| name | string | yes | Human-readable source name. |
| type | string | yes | website, referral, event, telegram, phone, partner, other. |
| external_ref | string | no | External source identifier. |
| is_active | boolean | yes | Source availability. |

### lead_center_activities

Timeline of operational activity.

| Field | Type | Required | Notes |
| --- | --- | --- | --- |
| id | uuid | yes | Activity identifier. |
| lead_id | uuid | yes | Parent lead. |
| actor_user_id | uuid | no | Staff member reference. |
| type | string | yes | note, call, message, status_change, system, trial, conversion. |
| channel | string | no | phone, telegram, email, web, mobile, system. |
| summary | string | yes | Short activity description. |
| occurred_at | datetime | yes | Activity time. |
| metadata | object | no | Structured extension data. |

### lead_center_assignments

Assignment history.

| Field | Type | Required | Notes |
| --- | --- | --- | --- |
| id | uuid | yes | Assignment identifier. |
| lead_id | uuid | yes | Parent lead. |
| assigned_to_user_id | uuid | yes | Responsible user reference. |
| assigned_by_user_id | uuid | no | Actor reference. |
| reason | string | no | Assignment reason. |
| assigned_at | datetime | yes | Assignment timestamp. |
| released_at | datetime | no | End timestamp. |

### lead_center_trial_requests

Trial lesson request and handoff state.

| Field | Type | Required | Notes |
| --- | --- | --- | --- |
| id | uuid | yes | Trial request identifier. |
| lead_id | uuid | yes | Parent lead. |
| branch_id | uuid | no | Requested branch reference. |
| teacher_id | uuid | no | Requested or assigned teacher reference. |
| schedule_slot_id | uuid | no | Schedule module reference when available. |
| status | string | yes | requested, scheduled, completed, cancelled, no_show. |
| preferred_time_window | string | no | Human-friendly preference before scheduling. |
| scheduled_at | datetime | no | Confirmed trial time if available. |
| completed_at | datetime | no | Completion timestamp. |
| created_at | datetime | yes | Creation timestamp. |
| updated_at | datetime | yes | Last update timestamp. |

### lead_center_status_history

Lifecycle status history.

| Field | Type | Required | Notes |
| --- | --- | --- | --- |
| id | uuid | yes | History record identifier. |
| lead_id | uuid | yes | Parent lead. |
| from_status | string | no | Previous status. |
| to_status | string | yes | New status. |
| changed_by_user_id | uuid | no | Actor reference. |
| reason | string | no | Human-readable reason. |
| changed_at | datetime | yes | Change timestamp. |

## Data Ownership

| Data | Owner |
| --- | --- |
| Lead lifecycle | Lead Center |
| Lead source | Lead Center |
| Lead contact methods | Lead Center until converted, then shared by contract |
| Trial request intent | Lead Center |
| Final schedule slot | Schedule |
| Student profile after conversion | CRM or Student module |
| Payment state | Finance |
| Conversion analytics | Analytics, derived from Lead Center events |

## Privacy Notes

Lead Center will store personal contact information. Future implementation must define:

- Access control.
- Audit logging.
- Consent capture.
- Data retention.
- Data export policy.
- Data deletion or anonymization policy.

