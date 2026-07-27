# MaCSS Handbook

Shared conventions for the [macss-berkeley](https://github.com/macss-berkeley)
org, so courses are easy to find and look familiar to each other. They are
conventions, not requirements. How you run your course inside your repo is up to
you, and if something here gets in the way, open an issue or a PR.

## Naming

One repo per course, named `compss-XXX`, lowercase: `compss-211`, `compss-212`.
No semester or year in the name.

Each course keeps one repo that you revise in place, rather than a new
`compss-211-fa26` every term. That way there is one place to look and links stay
valid. How you organize things inside the repo is up to you.

## Tagging at the end of a semester

When grades are in, tag the repo at the state students saw:

```bash
git tag -a fa26 -m "COMPSS 211, Fall 2026"
git push origin fa26
```

This gives you something to point at when a student asks about an assignment
from two years ago. It only works if you do it at the time.

## Public vs. private

Private by default, public when the materials are meant to be open. Before going
public, check the licensing. The repo needs a license of its own (see the
[course template](https://github.com/macss-berkeley/macss-course-template)), and
you need the right to redistribute the readings and data in it. Git history
keeps what you delete.

## Transferring a repo into the org

Transferring brings the history, issues, and pull requests along. You need to be
a member of the org first. If the repo is not already named `compss-XXX`, rename
it before moving.

1. Go to the repo, then Settings.
2. Scroll to the Danger Zone at the bottom.
3. Click Transfer ownership, confirm the repo name, and enter `macss-berkeley`
   as the new owner.

It happens immediately, and you keep admin on the repo. GitHub redirects the old
path to the new one, so existing clones keep pushing and pulling and links in
your syllabus still resolve. Update the remote when it is convenient:

```bash
git remote set-url origin git@github.com:macss-berkeley/compss-XXX.git
```

The redirect breaks only if something new is created at the old path, so do not
reuse the old name.

If the repo is part of your own research line and the course is one use of it,
fork it into the org instead and keep your copy primary. Syncing is then manual.

## Access and teams

Access comes through teams rather than one-off invites, so you can see who can
write to a course repo in one place. The org's default permission is `none`, so
joining the org grants nothing by itself.

- `faculty`: standing team for faculty teaching or maintaining COMPSS courses.
- `gsis`: parent team that groups the per-semester teams below it. It grants no
  access on its own.

GSI teams cover one offering and are named `compss-XXX-gsis-SSYY`, for example
`compss-211-gsis-fa26`. They usually get `write` on the course repo. Retiring
the team once grades are in ends access with the appointment.

You can add and remove people on your own course teams. For a new team, a new
course repo, or anything org-wide, ask an owner. New courses get a repo and a
GSI team at the same time.

## Student work

Where student work lives is your call. The one thing to keep consistent:
students do not get write access to the `compss-XXX` repo, since that is the
copy you revise from one semester to the next.

Some options:

- A separate repo for the offering, such as `compss-211-fa26-projects`, for
  group work or shared scratch space.
- GitHub Classroom, if you want one repo per student generated from a template.
- bCourses, if the work is graded and you would rather not manage repos.

Solutions and answer keys belong out of a public course repo too. A private
`compss-XXX-instructors` repo is the usual place. Removing them later does not
retract them, since they stay in the history and in any forks students have
made.

Grades, feedback, and identifiable submissions are education records, so keep
them out of public repos wherever they live.
