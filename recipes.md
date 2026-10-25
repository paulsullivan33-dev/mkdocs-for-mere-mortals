# Recipes

Four shapes of site this guide's
machinery covers well, with the
parts that differ each time. All
four assume the install from chapter
3 and a `build --strict` before
anything is published (chapter 11).

## A club or society handbook

The lab's shape, retold as a recipe:
six to twenty pages of "how we do
things", written by whoever holds
the job this year.

- Pages by task, not by author:
  getting started, everyday jobs,
  the reference lists, the meetings.
- The boring pages matter most —
  fees, rotas, who holds which post.
  Write them first; the welcome page
  can be short forever.
- One editor with the password, a
  repository anyone in the club can
  read. Decisions get written into
  the handbook at the meeting that
  makes them, or they evaporate.

## A software project's documentation

The shape MkDocs was born for:

- A `README`-style home page that
  says what the project is and how
  to install it in five commands.
- A tutorial that does one real
  thing end to end, before any
  reference material — new readers
  judge the project by whether the
  tutorial worked.
- Reference pages generated or
  checked against the thing they
  describe, and a changelog page,
  newest first. Version tabs (chapter
  10) suit "current / previous
  release" instructions.
- `repo_url` and `edit_uri` set
  (chapter 6), so a reader's typo
  fix is two clicks from the page
  that has the typo.

## A personal notebook, published

Notes you keep for yourself, in the
open because closed notes rot:

- One folder per subject, awesome-pages
  (chapter 7) keeping order so adding
  a note never means editing a central
  list.
- Dates on pages that are really
  journal entries — a line of front
  matter or the first line of the
  page, your convention, kept.
- Say on the home page that it is a
  notebook: unfinished, corrected in
  place. Readers forgive a notebook
  anything except pretending to be a
  textbook.

## A runbook for a small team

The pages you want at 3 a.m.:

- One page per failure you have
  actually met, titled by the symptom
  the pager shows, not by the cause
  you eventually found.
- Commands in copy-button code blocks
  (chapter 8), in the order to run
  them, with the expected output
  quoted — at 3 a.m. nobody should be
  guessing what success looks like.
- A strict build in the publish path,
  because a runbook with a dead link
  to the one page you need is worse
  than no runbook: it costs you the
  minutes you spend discovering it.
