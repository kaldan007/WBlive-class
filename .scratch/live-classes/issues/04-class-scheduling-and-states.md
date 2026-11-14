# Class scheduling and Class states

Status: needs-triage
Blocked by: 03
Spec: [spec.md](../spec.md) · Design: [tech-design.md](../tech-design.md)

## Summary

Instructors, Class coordinators and Community admins schedule Classes, which move through Scheduled, Live, Conducted and Cancelled.

## Scope

- `classes` table.
- Create and edit a Class: title, description, Instructor, start time, duration. Times display in the viewer's time zone.
- Reschedule and cancel a Scheduled Class.
- "Start" and "End" buttons for Instructors and Class coordinators.
- Render cron job, every 5 minutes: any Scheduled or Live Class 3 hours past its scheduled end becomes Conducted.
- A basic Class page showing details and status (later issues add the call, Materials, Recording and Q&A).
- A basic Upcoming list so Classes can be reached (issue 09 builds the full list).

## Acceptance criteria

- [ ] An Instructor, Class coordinator or Community admin can create a Class; an Attendee can't.
- [ ] Start time shows correctly for viewers in different time zones.
- [ ] Start moves the Class to Live; End moves it to Conducted.
- [ ] A Class nobody ends becomes Conducted 3 hours after its scheduled end, including one nobody started.
- [ ] A cancelled Class can't be started.
- [ ] Rerunning the cron job doesn't change Classes it already handled.

## Out of scope

- Notification emails (issue 10).
