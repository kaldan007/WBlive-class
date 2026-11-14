# Live Class with JaaS

Status: needs-triage
Blocked by: 04
Spec: [spec.md](../spec.md) · Design: [tech-design.md](../tech-design.md)

## Summary

Members join the live Class inside the Class page, using Jitsi through JaaS.

## Scope

- JaaS account and signing key in Render environment variables (ADR 0001).
- `POST /classes/{id}/join` returns a JWT for that Class's room, valid 2 hours: `moderator=true` for Instructors, Class coordinators and the Community admin.
- Attendees can join only while the Class is Live; Instructors and Class coordinators can also join while it's Scheduled.
- Embed the Jitsi iframe on the Class page with the JWT.
- Test on phone browsers (Chrome on Android, Safari on iOS) and write the result in a comment on this issue.

## Acceptance criteria

- [ ] An Instructor can start a Class, join the call and share their screen.
- [ ] An Attendee can join the call while the Class is Live, and can't before it starts.
- [ ] An Instructor or Class coordinator can mute and remove participants; an Attendee can't.
- [ ] Opening the room without a valid JWT from the platform fails.
- [ ] The mobile test result is recorded. If JaaS forces an app install on phones, flag it so the video decision can be revisited.

## Out of scope

- Platform-side recording (the Class coordinator records locally; see issue 07).
