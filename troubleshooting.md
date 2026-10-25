# Troubleshooting

Every entry here either happened in
this guide's lab or is the common
cold of the MkDocs world. The build
log is the first tool for all of
them: MkDocs' errors name the file
and usually the fix.

## `mkdocs: command not found`

The environment isn't active, or
MkDocs was installed into a different
one than the shell thinks. Activate
the venv (chapter 3) and ask
`which mkdocs` — the answer should
point inside it. This is the single
most common MkDocs failure and it is
never MkDocs' fault.

## The build stops on the config file

A YAML error names a line. The usual
three:

- **A colon in an unquoted value.**
  `site_description: News: updated
  weekly` fails with "mapping values
  are not allowed here" — the colon
  and space look like a new key. Quote
  the value or drop the colon
  (chapter 6).
- **Tabs.** YAML indentation is
  spaces only; a file edited in an
  editor that inserted a tab fails
  far from the actual tab. Re-indent
  the block it names.
- **A list at the wrong depth.**
  Theme features, palette and nav are
  nested lists; one level too shallow
  and the key is silently ignored
  (the site builds, just not the way
  you asked) or rejected. Compare
  against the theme's own examples,
  level by level.

## A page is missing from the site

In order: is the file inside
`docs/`? Does its name end `.md`?
Is it in `nav` — and if not, did the
build's "not included in the nav"
list name it (chapter 7)? Did an
`exclude_docs` pattern catch it?
Four questions, one of which is
always yes.

## A link works in `serve` and fails in the build — or a strict build aborts

The strict run says which link and
which file. Transcript t04 is the
canonical example: a page linking to
`no-such-page.md` builds with a
warning and exit 0, and aborts with
exit 1 under `--strict`. Rename
drift causes most of these — the
page was renamed, the link wasn't.
Fix the link, not the strictness:
a build allowed to warn is a build
whose warnings nobody reads.

## `mkdocs serve` shows a different site, or a redirect

`site_url` decides where the dev
server mounts the site. The lab's
`/garden-handbook/` mount answered
the bare address with a 302 to the
mounted path (transcript t03) — not
a bug, but baffling the first time.
Either visit the mounted path, or
unset `site_url` while drafting and
set it before publishing. A stale
site at the expected address is
usually an old `serve` still running
in another terminal.

## A box, tab or checkbox renders as plain text

The markup is fine; the extension
isn't on. Plain-text `!!!` paragraphs
mean `admonition` (or
`pymdownx.details`) is missing from
`markdown_extensions`; literal `===`
headings mean `pymdownx.tabbed`;
`- [ ]` showing as text means
`pymdownx.tasklist`. Chapter 9 is
the checklist. The build will not
warn you — this class of failure is
silent, which is why a new page
deserves a look in `serve` before
it's published.

## The theme or a plugin "isn't installed"

An error naming the theme as
unrecognised, or an import error
naming a plugin: both mean the
package isn't in the environment
doing the building. Themes and
plugins are `pip` packages like any
other (chapters 3 and 10) — install
into the same venv you build with.
In CI, the same failure means the
workflow's install step doesn't list
it.

## The banner about "MkDocs 2.0"

Material 9.7.x prints the theme
project's own notice about an
announced future MkDocs at the top
of each build. It is not a warning,
it doesn't come from your config,
and it doesn't affect `--strict` —
the lab's strict builds exit 0 with
it on screen. Read your build's
verdict at its end, not its top.

## Publishing succeeds, the site doesn't change

A caching layer, a workflow that
published a stale checkout, or Pages
set to a different source than the
one you pushed to (chapter 11). And
the MkDocs-specific one: you edited
the *generated* files, or built
locally and pushed `site/` while the
workflow also builds — two sources
of truth fighting. Edit Markdown,
commit Markdown, let one builder
build.

## The check that proves a build

```bash
mkdocs build --strict && echo BUILD-OK
ls site/index.html site/search/search_index.json
```

Both files present after a strict
build: the site is whole and its
search index exists. Everything else
in this chapter is a variation on
one of those three lines failing.
