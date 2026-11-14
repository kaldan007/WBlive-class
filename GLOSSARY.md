# Live Buddhist Classes

A web platform where Buddhist Communities register, invite their Members, and hold live Classes taught by an Instructor, with the teaching material, questions and answers kept and searchable afterwards.

## Language

**Platform admin**:
The super user of the whole platform, with full control over every Community.
_Avoid_: Super admin, root

**Community**:
An organization (sangha, temple, center or teaching group) that registers itself on the platform and gathers its own Members.
_Avoid_: Group, org, sangha, tenant

**Account**:
A person's single identity on the platform. One Account can be a Member of many Communities.
_Avoid_: User, profile

**Member**:
An Account's membership in one Community, holding one or more Roles in that Community.
_Avoid_: User, student

**Invite link**:
A shareable link by which a Community onboards Members; the invitee must still sign up on the platform.
_Avoid_: Invitation code

**Role**:
A responsibility a Member holds within a Community: Community admin, Instructor, Class coordinator or Attendee. One Member can hold several.

**Community admin**:
The Member who creates the Community and assigns Instructors and Class coordinators. Has all the privileges of the other Roles.
_Avoid_: Owner

**Instructor**:
A Member who teaches a Class, such as a Buddhist teacher explaining a short sutra or a practice.
_Avoid_: Teacher, lama

**Class coordinator**:
A Member who helps the Instructor run a Class.
_Avoid_: Moderator, host

**Attendee**:
A Member who joins a Class to learn.
_Avoid_: Student, participant

**Class**:
A single live teaching session, free of charge and independent of any other Class.
_Avoid_: Webinar, meeting, master class, session

**Scheduled**:
The state of a Class that has been planned but not yet started.
_Avoid_: Upcoming, planned

**Live**:
The state of a Class while it is being taught.
_Avoid_: In progress, ongoing

**Conducted**:
The state of a Class after it has been held. Conducted Classes make up the Community's past-Class list.
_Avoid_: Completed, finished, past

**Cancelled**:
The state of a Class called off before it was held. A Cancelled Class never becomes Conducted.
_Avoid_: Deleted, aborted

**Recording**:
A video of a Conducted Class that the Class coordinator made locally and published on YouTube or Vimeo, then linked from the Class page. The platform stores only the link.
_Avoid_: Replay, video

**Q&A**:
The questions Attendees post on a Class page and the answers given, kept permanently with that Class.
_Avoid_: Chat, comments

**Materials**:
Files and links the Instructor or Class coordinator attach to a Class, such as slides and PDFs.
_Avoid_: Resources, attachments
