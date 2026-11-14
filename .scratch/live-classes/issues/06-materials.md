# Materials

Status: needs-triage
Blocked by: 04
Spec: [spec.md](../spec.md) · Design: [tech-design.md](../tech-design.md)

## Summary

Instructors and Class coordinators attach files and links to a Class page, and Members download them.

## Scope

- `materials` table; private R2 or S3 bucket.
- Upload flow: request presigned PUT URL (validate type and size ≤ 100 MB), upload directly from the browser, confirm.
- Allowed types: PDF, PPT/PPTX, images. Also external links with a title.
- Download through a presigned GET URL valid 5 minutes, after a membership check.
- Delete a Material (Instructor, Class coordinator, Community admin).

## Acceptance criteria

- [ ] An Instructor can upload a 90 MB PDF; a 110 MB file is rejected.
- [ ] An unsupported type (for example `.exe`) is rejected.
- [ ] Members can download Materials; a non-Member can't, even with an old download URL after 5 minutes.
- [ ] An Attendee can't upload or delete Materials.
- [ ] Links open in a new tab.

## Out of scope

- Previewing slides inside the page.
