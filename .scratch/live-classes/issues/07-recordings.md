# Recordings

Status: needs-triage
Blocked by: 04
Spec: [spec.md](../spec.md) · Design: [tech-design.md](../tech-design.md)

## Summary

The Class coordinator pastes a YouTube or Vimeo link, and the Class page plays the Recording.

## Scope

- Recording link field on a Class (Instructor, Class coordinator, Community admin can add, edit and remove).
- Accept only YouTube and Vimeo URLs.
- Class page shows an embedded player, or "recording pending" for a Conducted Class without a link.
- A short hint next to the field recommending unlisted links.

## Acceptance criteria

- [ ] Pasting a YouTube or Vimeo link shows an embedded player on the Class page.
- [ ] Other URLs are rejected with a clear message.
- [ ] A Conducted Class without a link shows "recording pending".
- [ ] The link can be changed or removed later.
- [ ] Attendees can't edit the link.

## Out of scope

- Hosting or uploading video on the platform.
