# Email notifications

Status: needs-triage
Blocked by: 01, 04, 08
Spec: [spec.md](../spec.md) · Design: [tech-design.md](../tech-design.md)

## Summary

The platform emails Members about their Classes and Q&A answers, and lets Accounts reset a forgotten password.

## Scope

- Resend setup; sender domain verified; API key in Render environment variables.
- `notifications_sent` table for idempotency.
- Emails to active Members when a Class is scheduled, rescheduled or cancelled.
- Cron job sends reminders 24 hours and 1 hour before a Class to Members with reminders on.
- Email to the asker when an Instructor answers their question.
- Password reset: "Forgot password" on the login page emails a single-use link valid for 1 hour; using it sets a new password and ends existing sessions.
- On reschedule, clear earlier reminder records so new reminders go out.

## Acceptance criteria

- [ ] Scheduling, rescheduling and cancelling a Class each email the Community's active Members once.
- [ ] Reminders arrive 24 hours and 1 hour before; running the cron job twice sends no duplicates.
- [ ] A Member with reminders turned off gets no reminders but still gets cancellations.
- [ ] The asker gets one email when an Instructor answers, not for other replies.
- [ ] Deleted Accounts and removed Members get no email.
- [ ] "Forgot password" emails a reset link; it works once, expires after 1 hour, and logs out other sessions.
- [ ] Asking for a reset for an unknown email shows the same message as for a known one.

## Out of scope

- In-app or push notifications.
