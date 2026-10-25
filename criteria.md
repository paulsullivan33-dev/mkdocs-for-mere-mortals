# Writing Criteria

Every guide in this repo is written to the same
standard. If you're adding or editing a guide —
human or AI — hold it to these.

1. **Plain words, real ideas.** Simple language,
   never dumbed-down concepts. Explain jargon on
   first use; collect terms in the glossary.
2. **No hype.** No marketing adjectives, no
   "revolutionary," no promises about what
   something will do for the reader.
3. **Honest about limits.** Say what the thing
   *can't* do. State uncertainty instead of
   smoothing it over. Validation notes include
   what remains unverified.
4. **No invented numbers.** Benchmarks, defaults,
   and specs are either measured or qualified with
   "depends on your setup." If it wasn't tested,
   say so.
5. **Checkable.** Commands are meant to be run,
   with "Check:" blocks showing what success looks
   like. Sources are linked, not asserted.
6. **Respect the reader's setup.** Call out
   Windows/Mac/Linux differences. Don't assume a
   GPU, a budget, or prior experience.
7. **Safety isn't skipped.** Real risks get
   stated plainly, not buried.
8. **Scoped.** Each guide says what it covers and
   points elsewhere for the rest. No guide
   pretends to be the whole subject.
9. **Structure over prose.** Tables, before/after
   examples, symptom → fix. Scannable beats essay.

## Verification notes for this guide

Built and verified 2026-10-24 against
**MkDocs 1.6.1** and **mkdocs-material
9.7.7**, installed from PyPI into a
dedicated virtual environment
(`mkdocs-venv`, Python 3.12.3), with
mkdocs-minify-plugin 0.8.0 and
mkdocs-awesome-pages-plugin 2.10.1,
on a sandbox machine running Ubuntu
24.04. Nothing was installed
system-wide; deleting the venv deletes
the whole toolchain.

**Primary sources read, not remembered:**
the MkDocs configuration and commands
documentation (chapters 4 and 6), the
Material theme's setup, palette and
feature documentation (chapter 8), the
PyMdown Extensions documentation
(chapter 9), and the GitHub Pages and
GitHub Actions publishing documentation
(chapter 11).

**The lab site.** A complete sample
project lives in `mkdocs-lab/`: the
*Maple Street Community Garden
Handbook*, a fictional club handbook of
six pages (`garden-handbook/` — config,
pages and one small stylesheet), built
and served from a venv on the sandbox
for exactly the length of each
transcript. The fictional garden is a
fixture, written for any reader to
reproduce; nothing in it is modelled
on any real club, person, organisation
or event.

**Ran for real** (transcripts in
`mkdocs-lab/transcripts/`):

- t00 — `mkdocs --version` → 1.6.1, and
  `pip show` for the Material theme
  (9.7.7), the minify plugin (0.8.0) and
  the awesome-pages plugin (2.10.1), all
  in the one venv.
- t01 — `mkdocs new garden-handbook`;
  the scaffold is two files (a one-line
  `mkdocs.yml`, a starter `docs/index.md`).
- t02 — `mkdocs build --strict` on the
  full handbook: exit 0, six pages. The
  output was then inspected, not merely
  built: the light and dark palette
  choices are present in the HTML with
  the configured toggle labels, the
  search component and its index
  (`search/search_index.json`, 8,630
  bytes) are in the site, code blocks
  carry the copy feature's markup and
  line-number anchors, and the
  admonition, tabbed and task-list
  markup classes all appear. The whole
  finished site is 2.7 MB, nearly all
  of it theme assets.
- t03 — `mkdocs serve` answered over
  HTTP: the configured `site_url` path
  means the bare address redirects (302)
  to `/garden-handbook/`, the home page
  and the compost page return 200 with
  the right titles, and the search
  index is served as JSON. The transcript
  keeps the initial requests to the wrong
  path alongside the corrected ones.
- t04 — a deliberately broken link was
  added and then removed. A plain build
  prints the "link not found" warning
  and exits 0; `mkdocs build --strict`
  aborts with "Aborted with 1 warnings
  in strict mode!" and exit 1. Both
  runs are in the transcript.
- t05 — the same site built with and
  without the minify plugin: total HTML
  120,313 bytes plain, 95,242 bytes
  minified, about a fifth smaller.
- t06 — in a scratch copy, `nav` was
  removed from `mkdocs.yml`, a
  `docs/.pages` file written, and the
  awesome-pages plugin added: the site
  builds `--strict`-clean with the
  `.pages` order in force. The scratch
  copy was deleted afterwards.

**Errors hit and diagnosed for real,**
written up in the troubleshooting
chapter: the `.pages` file's first
attempt listed bare titles instead of
file names and the plugin failed the
build with `NavEntryNotFound: Nav
entry "Getting a Plot" not found`
(first t06 run); the dev server's 302
to the `site_url` path (t03); and the
broken-link warning pair (t04).
Material 9.7.7 also prints the theme
project's banner about an announced
"MkDocs 2.0" at the top of every
build; it is advocacy text from the
theme package, not a build warning,
and does not affect strict exit codes
— noted in chapters 3 and 15 so
readers do not chase it.

**Documented only, and labelled as
such in the chapters:** publishing
with `mkdocs gh-deploy` (the command
is present in 1.6.1 — `mkdocs
gh-deploy --help` was read in the
lab — but no real repository or
GitHub account was used from the
sandbox, so no live publish is
claimed); the GitHub Actions workflow
in chapter 11, described generically —
the workflow file shipped with this
guide (`.github/workflows/deploy-docs.yml`)
is the standard pattern and is the
same mechanism this series publishes
with, and this guide's own build was
run locally exactly as that workflow
will run it (staging steps included)
before being called done; the
neighbours in chapter 13 (Hugo,
Jekyll, Sphinx, mdBook, Docusaurus,
wikis), characterised from their own
documentation; Material features
beyond the lab's four switches and
palette pair; per-page front matter
options beyond title; and the
multilingual and versioned-site
arrangements discussed in Limits.
