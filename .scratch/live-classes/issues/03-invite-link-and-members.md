# Invite link and Member management

Status: needs-triage
Blocked by: 02
Spec: [spec.md](../spec.md) · Design: [tech-design.md](../tech-design.md)

## Summary

Members join a Community through its Invite link, and the Community admin manages Members and Roles.

## Scope

- Invite link (`/join/{invite_token}`) shown to the Community admin, with a "reset link" action.
- Joining: log in or sign up, then become a Member with the Attendee Role.
- Per-Community setting "new Members need approval"; pending Members wait for the Community admin.
- Members page: list Members and their Roles; assign or remove Instructor and Class coordinator Roles; remove a Member.
- A person can be a Member of several Communities and switch between them.
- The permission check for every Community-scoped endpoint: no active Member record means 404.

## Acceptance criteria

- [ ] Opening the Invite link and signing up makes the person an Attendee of that Community.
- [ ] After a reset, the old Invite link no longer works and the new one does.
- [ ] With approval turned on, a new Member can't see anything until the Community admin approves them.
- [ ] The Community admin can give and take away the Instructor and Class coordinator Roles.
- [ ] A removed Member immediately loses access to the Community.
- [ ] An Account in two Communities sees only the data of the Community it's viewing.
- [ ] A non-Member requesting any Community URL gets 404.

## Out of scope

- Invite emails (Members join by link; issue 10 covers email).
