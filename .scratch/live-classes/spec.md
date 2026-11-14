# PRD: Live Classes for Buddhist Communities

Status: final · Label: needs-triage

## Problem

Buddhist Communities teach short sutras and practices informally over WhatsApp and Google Meet.

- **Voice/video messages in WhatsApp (Case 1):** teachers can't present prepared slides, recording video is inconvenient, and nobody can search later for a concept that was taught or discussed.
- **Meet links shared in WhatsApp (Case 2):** Attendees need a Google account, materials are scattered in chat and hard to find, and Q&A vanishes when the meeting ends.

## Goal

A web platform where a Community registers, invites its Members, and holds free live Classes, keeping each Class's Recording, Materials and Q&A in one searchable place.

**Success (v1):** one Community runs a full Class end to end on the platform: schedule, teach live, publish Recording, Materials and Q&A, and later find it in the past-Class list.

## Users and Roles

See `GLOSSARY.md` for definitions.

- **Platform admin**: approves, rejects and suspends Communities; full control.
- **Community admin**: creates the Community, manages Members and the Invite link, assigns Instructors and Class coordinators; has all privileges of the Roles below.
- **Instructor** and **Class coordinator**: run Classes (schedule, start, end, cancel, teach, upload Materials, add Recording link, moderate Q&A).
- **Attendee**: joins Classes, asks and answers questions, reads Materials, watches Recordings.
- One Account can be a Member of many Communities and hold different Roles in each. Within a Community, a Member can hold several Roles.

Primary user: the **Class coordinator**, who runs the day-to-day work currently done over WhatsApp.

## Scope (v1)

### Communities and Members

1. **Community registration**: an organization submits name, description, contact person and location. The Platform admin approves it or rejects it with a reason. The Platform admin can later suspend a Community.
2. **Accounts**: sign up and log in with email and password or with Google sign-in. Email-and-password Accounts can reset a forgotten password through an emailed link.
3. **Invite link**: the Community admin shares an Invite link. The invitee signs up (or logs in) and joins the Community as an Attendee. The Community admin can reset the Invite link, which disables the old one. Optional per Community: new Members need Community admin approval before joining.
4. **Member management**: the Community admin assigns and removes the Instructor and Class coordinator Roles, and can remove Members.

### Classes

5. **Scheduling**: an Instructor, Class coordinator or Community admin creates a Class with title, description, start time and duration. Times display in the viewer's time zone.
6. **Class states**:
   - **Scheduled**: created, not yet started. Can be edited, rescheduled or cancelled.
   - **Live**: an Instructor or Class coordinator clicked "Start".
   - **Conducted**: an Instructor or Class coordinator clicked "End". If nobody ends it, the Class becomes Conducted automatically a few hours after its scheduled end.
   - **Cancelled**: cancelled before it was held. Not shown on the Past list.
7. **Live teaching**: Jitsi embedded in the Class page via JaaS (ADR 0001). Only Members of the Community can enter the room. Instructors and Class coordinators join as moderators (mute and remove participants); Attendees join as participants. The Instructor presents slides with screen share.
8. **Email notifications**: sent when a Class is scheduled, rescheduled or cancelled; reminders 24 hours and 1 hour before it starts. Members can turn reminders off.

### Class content

9. **Materials**: Instructors and Class coordinators attach files (PDF, PPT/PPTX, images; max 100 MB each) and external links to the Class page. Members can view and download them.
10. **Recording**: the Class coordinator records locally, uploads to YouTube or Vimeo, and pastes the link on the Class page. The link can be edited at any time. The page shows an embedded player, or "recording pending" when no link exists yet. Unlisted links are recommended.
11. **Q&A**: on the Class page, before, during and after the Class, kept permanently.
    - Any Member can post a question or reply; Instructor replies are marked.
    - Authors can edit their own posts. Instructors, Class coordinators and the Community admin can delete any post.
    - The asker gets an email when an Instructor answers.

### Finding past Classes

12. **Classes list**: per Community, tabs Upcoming and Past. Past lists every Conducted Class newest first, with Instructor, date, and indicators for Recording, Materials and Q&A. Filter by Instructor and date range.
13. **Search**: over Class titles, descriptions, Material names and Q&A text.
14. **Privacy**: everything is visible only to the Community's Members.

### Devices

15. **Responsive web app**, usable on phone browsers. Test the JaaS embed on mobile browsers early: if it pushes users to install the Jitsi app, revisit the video decision.

## Non-functional requirements

- **Scale (v1):** about 10 Communities, up to 500 Members each, up to 100 people in one live Class.
- **Performance:** pages load in under 2 seconds and search returns in under 1 second on a normal connection.
- **Availability:** best effort, no formal uptime guarantee in v1.
- **Backups:** daily database backups, kept for 7 days.
- **Security:** HTTPS everywhere; hashed passwords; every request checks that the Account is a Member of the Community whose data it touches; Materials served only through short-lived download links.
- **Data retention:** a Member can delete their Account; their Q&A posts remain, shown as "deleted user". A suspended Community's data is kept, not deleted.
- **Accessibility:** keyboard navigation, readable contrast, alt text on images.
- **Browsers:** latest two versions of Chrome, Safari, Firefox and Edge, on desktop and mobile.

## Non-goals (v1)

- Series, courses or recurring Classes; Classes are independent.
- Attendance tracking (revisit with series or courses).
- Payments; Classes are free.
- Platform-hosted recording or video storage; recording transcripts and transcript search.
- Multiple languages (English-only UI).
- Public browsing or cross-Community visibility.
- Native mobile apps.

## Constraints and risks

- **Recording privacy**: Recording links live on external platforms and the platform can't enforce their privacy. Mitigation: guidance to use unlisted links; Vimeo's paid domain-restricted playback if stronger control is needed.
- **JaaS free tier** has usage limits. Monitor them and plan a move to self-hosting if exceeded.
- **Manual recording**: Classes may stay "recording pending".
- **Mobile Jitsi**: the embedded call may behave poorly in phone browsers (see scope item 15).
- **Forwarded Invite links**: mitigated by link reset, Member removal and optional join approval.

## Decisions

- **Materials size limit:** 100 MB per file.
- **Video:** JaaS free tier for the kickoff (ADR 0001).
- **Tech stack:** FastAPI (backend), React (frontend), PostgreSQL (database).
- **Hosting:** Render for now.
- **Materials storage:** S3-compatible object storage (Cloudflare R2 or AWS S3), uploaded directly from the browser via presigned URLs and served only to Community Members.
- **Email:** Resend (or Postmark) for password resets, Class notifications and Q&A answers.
- **Auth:** email and password plus Google sign-in; the Invite link works with either.

## Open questions

None outstanding.
