# Configuration

`mkdocs.yml` is a YAML file — nested
settings written as indented
`key: value` pairs. This chapter
takes the keys in the order a growing
project meets them. The lab's full
file is at
`mkdocs-lab/garden-handbook/mkdocs.yml`;
this guide's own `mkdocs.yml` is
beside this chapter, and is much
shorter — both facts are deliberate.

## The one required key

```yaml
site_name: Maple Street Community Garden Handbook
```

Nothing else is mandatory. Everything
below trades a line of typing for a
behaviour you want.

## The keys that describe the site

```yaml
site_description: The members handbook for a fictional community garden.
site_url: https://example.org/garden-handbook/
copyright: Copyright &copy; 2026 The Garden Committee
```

- **`site_description`** — a sentence
  about the site. Themes put it in the
  page's HTML description, where
  search engines find it. One trap,
  learned by this series the hard
  way: in YAML, a colon followed by
  a space inside an unquoted value
  ends the value and breaks the file
  ("mapping values are not allowed
  here"). Either keep descriptions
  colon-free or wrap them in quotes.
- **`site_url`** — where the finished
  site will live. It sets canonical
  addresses, the sitemap, and — the
  part people trip over — the path
  the dev server mounts the site at:
  with the URL above, `mkdocs serve`
  answers at `/garden-handbook/`, not
  at `/` (transcript t03 has the 302
  redirect as evidence). Set it early,
  to the real address.
- **`copyright`** — a line shown in
  the footer by most themes.

## The keys that place things

```yaml
docs_dir: docs        # where the Markdown lives (the default)
site_dir: site        # where the build lands (the default)
use_directory_urls: true
```

`use_directory_urls` is why
`compost.md` becomes `compost/`
rather than `compost.html` — prettier
addresses, and the default. Turning
it off gives file-style addresses,
which some very plain hosting (or
opening the site from disk) prefers.

## The keys that point back at the source

```yaml
repo_url: https://github.com/example/garden-handbook
repo_name: GitHub
edit_uri: edit/main/docs/
```

With these set, Material shows a link
to the repository and an "edit this
page" pencil on every page — the
difference between a reader spotting
a typo and a reader *fixing* it.
`edit_uri` is the fiddly one: it is
the path from the repository root to
the page files, and it differs
between hosts. The lab's fictional
project sets none of these, so its
pages carry no pencils; this guide's
own repository is where to see the
effect.

## The keys for files that are not pages

```yaml
extra_css:
  - stylesheets/extra.css
extra_javascript:
  - javascripts/extra.js
exclude_docs: drafts/*
```

`extra_css` and `extra_javascript`
load your files after the theme's —
the supported way to adjust a site
without forking the theme (chapter
9 uses one small stylesheet). Files
referenced this way live inside
`docs/`. `exclude_docs` keeps chosen
files out of the build entirely;
this guide uses it for its lab
folder, which is a fixture for
readers to build themselves, not a
set of extra chapters.

## Reading a YAML error

When the file is malformed the build
stops before anything else, naming a
line. Nine times out of ten it is
indentation: YAML nesting is spaces,
never tabs, and a child must sit
deeper than its parent *every* time.
Fix the line it names, then look at
the line above it — the actual
mistake usually lives there.
