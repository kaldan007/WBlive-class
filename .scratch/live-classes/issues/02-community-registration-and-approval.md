# Community registration and approval

Status: needs-triage
Blocked by: 01
Spec: [spec.md](../spec.md) · Design: [tech-design.md](../tech-design.md)

## Summary

An organization registers a Community, and the Platform admin approves, rejects or suspends it.

## Scope

- `communities` table.
- Registration form: name, description, contact person, contact email, location. The registering Account becomes the Community's first Member with the Community admin Role (needs the `members` and `member_roles` tables, created here).
- Community status: pending, approved, rejected (with reason), suspended.
- Platform admin screen: list pending Communities; approve; reject with a reason; suspend.
- The Community admin sees the status of their Community and any rejection reason.
- A pending, rejected or suspended Community can't be used beyond its status page.

## Acceptance criteria

- [ ] A logged-in Account can register a Community and lands on a "pending approval" page.
- [ ] The Platform admin can approve it, after which the Community admin can use it.
- [ ] The Platform admin can reject with a reason, which the Community admin sees.
- [ ] The Platform admin can suspend an approved Community; its data is kept but it can't be used.
- [ ] Non-Platform-admins get no access to the admin screen.

## Out of scope

- Emails about approval or rejection (issue 10).
