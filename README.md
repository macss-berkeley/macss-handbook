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

## Datahub and nbgitpuller

Course materials reach Datahub through
[nbgitpuller](https://curriculum-guide.datahub.berkeley.edu/workflows/nbgitpuller-link):
you generate a link, students click it, and the repo is cloned into their own
Datahub account. They need no GitHub account and no git.

**nbgitpuller only works with public repos.** Berkeley's
[guidance on distributing files](https://curriculum-guide.datahub.berkeley.edu/workflows/distributing-files/)
is explicit that links will not work with private repositories. Embedding a
personal access token in the link is the only workaround and is the same as
publishing your password, so treat it as unavailable.

This cuts against the private-by-default convention above. If you distribute
through Datahub, your course repo is public, and everything in "Public vs.
private" applies before you flip the switch: check that you may redistribute
every dataset and reading in it, add a license, and remember that git history
keeps what you deleted.

If a course cannot be public — restricted data, licensed readings — distribute
through bCourses instead, where students download the files and upload them to
Datahub by hand. It is clumsier, and it is the honest fallback.

### Solutions

An nbgitpuller link pulls the **whole repo**. A `solutions/` folder in a public
repo is a folder your students have, and deleting it later does not help:
history keeps it, and anyone who already pulled still has the files.

Keep solutions, answer keys, exams, and rubrics in a separate private repo, or
out of git entirely.

### Links

Generate the link with the
[link generator](https://curriculum-guide.datahub.berkeley.edu/workflows/nbgitpuller-link)
and put it at the top of your README, so a student who lands on GitHub has one
obvious way out. Clicking it again pulls new files; nbgitpuller merges rather
than overwrites, so student edits survive.

Transfers and renames are the usual way links break. GitHub redirects the old
path, so existing links keep working, but the redirect dies the moment anything
is created at the old path. Regenerate your links after a transfer rather than
relying on it.

When a link misbehaves, the
[troubleshooting guide](https://curriculum-guide.datahub.berkeley.edu/support/troubleshooting/nbgitpuller/)
covers the usual causes. New to Datahub? Start with
[Getting Started for Instructors](https://rtl.berkeley.edu/datahub-instructor-getting-started).

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
`compss-XXX-instructors` repo is the usual place.

Grades, feedback, and identifiable submissions are education records, so keep
them out of public repos wherever they live.
