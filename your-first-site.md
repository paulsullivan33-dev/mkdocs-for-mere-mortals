# Your First Site

Everything in this chapter is the
lab's real first hour, with the
transcripts to prove it
(`mkdocs-lab/transcripts/`, t01–t03).
The site is the fictional Maple
Street Community Garden handbook —
six pages, chosen because a club
handbook is the shape of writing
MkDocs eats best.

## Start the project

```bash
mkdocs new garden-handbook
cd garden-handbook
```

`mkdocs new` makes exactly two files
(transcript t01):

```text
garden-handbook/
  mkdocs.yml     one line: site_name: My Docs
  docs/
    index.md     a starter home page
```

Open `docs/index.md` and replace the
starter text with your own first
page. The home page of every MkDocs
site is `docs/index.md` — there is
no separate setting for it.

## Look at it while you work

```bash
mkdocs serve
```

This builds the site, serves it at
`http://127.0.0.1:8000`, and rebuilds
on every saved change — edit,
alt-tab, the page is already new.
Two honest notes:

- The address ends where `site_url`
  says. The lab's config sets
  `site_url: https://example.org/garden-handbook/`,
  so the dev server mounts the site
  at `/garden-handbook/` and the bare
  address answers with a redirect to
  it. Chapter 6 explains why; the
  curl evidence is in transcript t03.
- `serve` is a *preview*. It is a
  small development server, not a
  thing to expose to a network.

## Name it, theme it

Replace the one-line `mkdocs.yml`
with the handful of lines every
project wants (each is explained in
chapter 6):

```yaml
site_name: Maple Street Community Garden Handbook
site_description: The members handbook for a fictional community garden.
site_url: https://example.org/garden-handbook/

theme:
  name: material
```

Then add pages. A page is a `.md`
file in `docs/`; the lab's other
five are `getting-a-plot.md`,
`plot-care.md`, `compost.md`,
`tool-shed.md` and
`meetings-and-jobs.md`, written the
way chapter 5 describes.

## Build it for real

```bash
mkdocs build --strict
```

Transcript t02 is the lab's run:
clean, built in about two seconds.
`site/` now holds the finished
website — one folder per page, the
theme's assets, and a
`search/search_index.json` the search
box will read. Copy `site/` anywhere
that serves files and the handbook
is published; chapter 11 does it
properly.

**Build with `--strict` habitually.**
Without it, a broken link is a
warning printed on the way to a
successful-looking build (transcript
t04 shows both runs: warning and
exit 0 without `--strict`; "Aborted
with 1 warnings in strict mode!" and
exit 1 with it). Strict turns the
build into a check you can trust —
and the one automation can act on.

Check: these are the lab's own
numbers, from transcript t02 and the
files it produced — six pages built,
a search index written, and the
finished site 2.7 MB on disk, most
of it the theme's own assets rather
than the handbook's words.
