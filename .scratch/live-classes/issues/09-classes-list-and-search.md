# Classes list and search

Status: needs-triage
Blocked by: 04, 06, 07, 08
Spec: [spec.md](../spec.md) · Design: [tech-design.md](../tech-design.md)

## Summary

Members browse Upcoming and Past Classes and search across the Community's teaching.

## Scope

- Classes page with tabs Upcoming (Scheduled and Live, soonest first) and Past (Conducted, newest first). Cancelled Classes appear in neither.
- Past rows show title, date, Instructor, and indicators for Recording, Materials and Q&A.
- Filters: Instructor, date range.
- Search: PostgreSQL full-text search over Class titles and descriptions, Material titles and Q&A text, always limited to the current Community. Results link to the Class.

## Acceptance criteria

- [ ] The Past tab lists every Conducted Class, newest first, with correct indicators.
- [ ] Cancelled Classes don't appear in either tab.
- [ ] Filtering by Instructor and date range works together.
- [ ] Searching a word that appears only in a Q&A answer finds that Class.
- [ ] Search never returns results from another Community.
- [ ] Search returns in under 1 second with realistic data (about 500 Classes).

## Out of scope

- Searching inside Recordings (transcripts).
