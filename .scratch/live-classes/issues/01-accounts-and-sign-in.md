# Accounts and sign-in

Status: needs-triage
Blocked by: none
Spec: [spec.md](../spec.md) · Design: [tech-design.md](../tech-design.md)

## Summary

Set up the project skeleton and let a person create an Account and log in. This slice also proves the whole stack deploys to Render.

## Scope

- Repo skeleton: FastAPI backend, React frontend, PostgreSQL with migrations.
- Render setup: static site, web service, managed Postgres with daily backups; secrets in environment variables.
- `accounts` table (tech-design §2).
- Sign up and log in with email and password (argon2 hash).
- Sign in with Google (OAuth); an existing email links to the same Account.
- Session as an httpOnly, secure cookie; log out.
- Account settings: display name, time zone, reminders on/off.
- Delete Account: anonymize per tech-design §1 "Account deletion".
- A seed or CLI command to make an Account a Platform admin.

## Acceptance criteria

- [ ] A new person can sign up with email and password, log out, and log back in.
- [ ] A person can sign in with Google; signing in again reaches the same Account.
- [ ] Passwords are stored hashed, never in plain text.
- [ ] Deleting an Account clears email, name, password hash and Google ID, and the person can no longer log in.
- [ ] The app is deployed on Render over HTTPS.

## Out of scope

- Password reset (issue 10, which sets up email).
