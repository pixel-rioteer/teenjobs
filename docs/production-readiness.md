# Bobajob production-readiness checklist

This document describes requirements that must be addressed before the demonstration becomes a live service.

## Safeguarding and legal review

- [ ] Confirm the legal operating entity and adult oversight for business contracts.
- [ ] Obtain advice on UK child employment rules and the local authority byelaws applicable in each launch area.
- [ ] Confirm minimum permitted ages, permitted work types, hours, permits and supervision requirements.
- [ ] Define prohibited jobs and age-specific restrictions.
- [ ] Obtain appropriate insurance and professional advice on liability.
- [ ] Complete a safeguarding risk assessment and incident-response process.
- [ ] Decide how adult identity and age verification will be performed.
- [ ] Create clear reporting, blocking, escalation and account-suspension procedures.
- [ ] Complete a Children's Code / UK GDPR data protection impact assessment.
- [ ] Publish age-appropriate privacy information, retention rules and parental information.

## Authentication and account relationships

- Use Supabase Auth or another trusted identity provider. Never store plaintext passwords or ask a teen to enter a parent's password.
- Store role/authorization claims in trusted server-managed app metadata, not user-editable metadata.
- Verify parent/guardian relationships using a secure invitation and acceptance flow.
- Require parent approval for each individual job acceptance.
- Ensure the parent, teen and adult are the only participants in that job's private chat.
- Make public teen profiles username-based and exclude legal name, email, phone, date of birth and precise address.
- Verify adult accounts before they can contact or post jobs involving minors.
- Implement secure account recovery that does not disclose whether an email address has an account.

## Job workflow

1. Adult submits a listing with a fixed price and required details.
2. Listing enters pending admin review; it is not searchable or claimable.
3. Admin approves or rejects with an audit record.
4. Teen requests/accepts an available listing.
5. Parent reviews and approves that specific job.
6. Server re-checks that the listing is approved, age-appropriate, available and the teen-parent link is valid.
7. Only then is the job assigned and the three-person conversation created.
8. Adult and teen separately confirm completion.
9. Disputes, cancellation and safety reports pause payment release.
10. Reviews become available only after valid completion.

## Payments

- Do not hold customer funds in Bobajob's ordinary bank account.
- Obtain legal advice on payment-services regulation and marketplace responsibilities.
- Select a regulated provider that explicitly supports the proposed under-18 recipients and guardian arrangements.
- Keep payment card data with the provider; use hosted/tokenised checkout.
- Reconcile payment, cancellation, refund, chargeback and payout states server-side.
- Do not release payment based only on a client-side button or browser state.
- Keep a clear audit trail and prevent duplicate payout.

## Database and application security

- Enable RLS on every exposed table.
- Write ownership/relationship-based policies for every SELECT, INSERT, UPDATE and DELETE.
- Never expose Supabase service-role/secret keys in browser code or NEXT_PUBLIC variables.
- Use server-side validation for role changes, job approvals, parent approvals, job assignment, completion and payment state transitions.
- Do not trust client-provided role, user ID, price, approval state or payment status.
- Escape user-generated content and validate uploads.
- Apply rate limits, abuse monitoring and secure session handling.
- Test access as teen, parent, adult, admin and unauthenticated visitor.
- Keep admin actions in an append-only audit log.

## Suggested data entities

- profiles
- parent_guardian_links
- adult_verifications
- job_categories
- jobs
- job_applications
- job_approvals
- job_participants
- conversations
- messages
- job_completion_confirmations
- payment_intents
- payment_events
- subscriptions
- reviews
- reports
- admin_audit_log

A production schema and its RLS policies should be designed and reviewed before any real personal data is collected.
