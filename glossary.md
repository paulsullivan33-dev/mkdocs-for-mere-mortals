# Glossary

**Admonition** — A highlighted box
in a page (note, tip, warning,
danger), produced by the `admonition`
Markdown extension. (Chapter 9.)

**Awesome-pages** — A plugin that
builds navigation from the folder
layout, with optional `.pages` files
to set order and titles. (Chapter 7.)

**Build** — One run of `mkdocs
build`, turning `mkdocs.yml` plus
`docs/` into the finished site in
`site/`. `--strict` makes warnings
fail it. (Chapter 4.)

**Directory URLs** — The default
address style where `compost.md`
becomes the address `compost/`
rather than `compost.html`, set by
`use_directory_urls`. (Chapter 6.)

**Front matter** — A small YAML block
at the top of a page, between `---`
lines, carrying per-page settings
such as a title. (Chapter 5.)

**Material for MkDocs** — The most
widely used MkDocs theme; a separate
Python package, and the theme this
guide's lab and the whole series use.
Called "Material" in this guide.
(Chapter 8.)

**Minify** — Shrinking generated HTML
(and CSS/JavaScript) by removing
whitespace and optional quotes; in
MkDocs, a plugin. (Chapter 10.)

**`mkdocs.yml`** — The configuration
file at a project's root: site name,
theme, navigation, extensions,
plugins. YAML format. (Chapter 6.)

**Navigation (`nav`)** — The ordered
table of contents shown on every
page; written in `mkdocs.yml`, or
derived from the folder layout.
(Chapter 7.)

**Palette** — Material's colour
scheme settings, including the pair
of schemes (light and dark) behind
the reader's toggle. (Chapter 8.)

**Plugin** — A Python package that
takes part in the build itself —
search, minify, navigation helpers.
Installed with `pip`, listed under
`plugins:`. (Chapter 10.)

**PyMdown Extensions** — The package
supplying most of the Markdown
extensions MkDocs sites use
(highlighting, tabs, task lists,
details). (Chapter 9.)

**Search index** —
`search/search_index.json`, the file
the built-in search plugin writes,
holding every page's text so the
browser can search with no server.
(Chapter 10.)

**Site directory (`site/`)** — The
folder the build writes; the
finished, publishable website.
Never edited by hand. (Chapter 4.)

**Static site** — A website that is
only files: no database, no program
running per request. Cheap to host,
hard to break, unable to do anything
per-reader. (Chapter 1.)

**Strict mode** — `mkdocs build
--strict`: warnings become failures,
so a broken link stops a publish.
(Chapters 4 and 15.)

**Theme** — The skin that renders
every page: layout, navigation,
search box, colours. Built-ins are
`mkdocs` and `readthedocs`; most
projects install Material. (Chapter 8.)

**YAML** — The indented `key: value`
format of `mkdocs.yml` and front
matter. Spacing-sensitive, and its
unquoted values end at a colon
followed by a space. (Chapter 6.)
