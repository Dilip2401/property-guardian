# Property Guardian V30 — Production Architecture Direction

## Roles
- Admin: system/operator authority; manages CRM master data, assignments, schedules, workflow corrections and operational records.
- Guardian: field operator; observes, checks in, completes checklist, captures evidence and reports findings.
- Customer/Owner: property decision maker; reviews approved reports, findings, quotes and maintenance outcomes.

## Source of truth
Property CRM is maintained by Admin. Guardian visits read the assigned property, owner context, access rule, rooms and assets from the CRM.

## Workflow
Guardian observes -> Admin validates -> Owner decides -> Vendor executes -> Admin verifies -> Property History improves.

## Production services
- Web/mobile clients
- API service with RBAC and audit logging
- PostgreSQL for users, properties, visits, rooms, assets, issues, evidence metadata, vendors, quotes, work orders, maintenance plans, documents, access records and financials
- Object storage for inspection/repair evidence
- Background worker for reminders, SLA escalation and report generation
- Notification service for in-app + email/SMS
- Optional AI service for summaries/patterns only; never automatic diagnosis or approval

## Security
- Admin actions require explicit authorization and are audited.
- Customer personal data is visible only to authorized Admin/customer contexts.
- Evidence files use signed/private storage URLs in production.
- Access events record who, when, property, purpose and outcome.
- Production must implement rate limiting, CSRF protection where applicable, secure cookies, password hashing, MFA for Admin, backup/restore and retention policies.
