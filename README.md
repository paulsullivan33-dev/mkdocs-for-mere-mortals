# MkDocs for Mere Mortals

A practical guide to **MkDocs**, the
static site generator that turns a
folder of Markdown files into a
finished documentation website — the
builder, the configuration file, the
Material theme, extensions, plugins,
and publishing to GitHub Pages,
explained from the ground up and
checked against a real sample site
built in a sandbox lab.

## Honest status

This guide was written with a real
lab: MkDocs 1.6.1 and the Material
theme 9.7.7 installed into a fresh
virtual environment on a sandbox
machine, a complete six-page sample
site scaffolded with `mkdocs new`
(a fictional community garden's
members' handbook), and every
load-bearing claim below checked
against that build.

What was verified live (transcripts
and the sample project in
`mkdocs-lab/`):

- The scaffold, the strict build of
  the full sample with the Material
  theme — palette toggle, navigation
  features, search and code-copy all
  present in the output — and the
  dev server answering pages and the
  search index over HTTP
- The failure that matters most: a
  broken link warns and passes a
  plain build, and aborts a
  `--strict` build with exit code 1
- The minify plugin's effect,
  measured: 120,313 bytes of HTML
  without it, 95,242 with it
- The awesome-pages plugin
  reordering navigation from a
  `.pages` file — including its
  refusal of bare-title entries,
  recorded as found
- The `site_url` side effect nobody
  expects: the dev server mounting
  the site under the URL's path and
  redirecting the bare address there

Deploying is the guide's one
chapter that rests on the standard
documentation rather than a live
run: `mkdocs gh-deploy` is verified
as present in 1.6.1 but was not
pointed at a real repository from
the sandbox, and the Actions
workflow is described generically —
though the workflow file shipped
with this guide is the live one its
series is published with, and this
guide's own strict build was run
exactly as that workflow will run
it.

## What this guide covers

- [What MkDocs Is](what-mkdocs-is.md) —
  the tool, the shape of a project,
  and what it is not
- [The Moving Parts](the-moving-parts.md) —
  command, config, content, theme,
  extensions, plugins
- [Installing MkDocs](installing-mkdocs.md) —
  Python, a virtual environment, and
  the two packages that matter
- [Your First Site](your-first-site.md) —
  `new`, `serve`, `build --strict`,
  and why strict is a habit
- [Writing Pages](writing-pages.md) —
  links between pages, images,
  code blocks, titles, front matter
- [Configuration](configuration.md) —
  `mkdocs.yml` line by line,
  including the colon trap
- [Navigation](navigation.md) —
  the `nav` list, forgotten pages,
  and the awesome-pages alternative
- [Themes and Appearance](themes-and-appearance.md) —
  built-ins, Material, palettes,
  feature switches, your own CSS
- [Markdown Extensions](markdown-extensions.md) —
  boxes, highlighting, tabs and
  checklists, and their silent
  failure mode
- [Plugins](plugins.md) — search,
  minify measured, awesome-pages,
  and the case for restraint
- [Deploying to GitHub Pages](deploying-to-github-pages.md) —
  `gh-deploy` versus the Actions
  workflow, step by step
- [Recipes](recipes.md) — a handbook,
  project docs, a public notebook,
  a runbook
- [The Neighbours](the-neighbours.md) —
  Hugo, Jekyll, Sphinx, mdBook,
  Docusaurus, and the wiki fork
- [Limits](limits.md) — what a static
  build cannot do, stated plainly
- [Troubleshooting](troubleshooting.md) —
  the failures the lab actually met,
  and the common colds
- [Glossary](glossary.md)
- [Writing Criteria](criteria.md) —
  the standard this guide had to meet

## What it doesn't cover

- **Material in depth.** The theme
  has hundreds of settings — icons,
  fonts, announcement bars, blog
  support. This guide sets up the
  core honestly and leaves the
  catalogue to the theme's own
  documentation.
- **Writing your own plugin or
  theme.** Both are real Python
  projects; this guide is about
  using the ones that exist.
- **Versioned or translated sites.**
  Possible, plugin-shaped, and
  covered in Limits as a decision to
  make before you start — not
  taught here.
- **Search beyond the built-in.**
  Hosted search services integrate
  with Material; choosing between
  them is a product decision, not
  an MkDocs one.
- **Markdown itself, beyond the
  extensions.** Chapter 5 assumes
  the basics and spends itself on
  the parts MkDocs changes.

## How to use this guide

Read chapters 1–4 in order once and
you have a site. After that the
chapters are reference-shaped: the
configuration and extension chapters
earn their keep open in a second
tab while you write your own
`mkdocs.yml`. The lab folder is a
worked example throughout — build
the garden handbook with chapter 4's
commands and you will have touched
every feature the middle chapters
describe.
