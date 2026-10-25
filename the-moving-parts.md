# The Moving Parts

Six parts, each small enough to hold
in your head. Most confusion with
MkDocs is one of these six wearing
another's coat.

## The `mkdocs` command

One program does nearly everything:

```bash
mkdocs new my-project   # start a project
mkdocs serve            # preview while writing
mkdocs build            # make the website
mkdocs build --strict   # ...and fail on warnings
mkdocs gh-deploy        # publish to GitHub Pages
```

It is written in **Python** and
installed with `pip`, Python's package
installer (chapter 3). When something
is wrong, it is usually this command
telling you so in plain words — the
build log is worth reading before
anything else (chapter 15).

## The configuration file

`mkdocs.yml`, in the project's root,
is a **YAML** file: indented
`key: value` settings. It names the
site, chooses the theme, lists the
navigation and turns extensions and
plugins on. Only one line is
required — `site_name` — and chapter
7 explains the rest line by line.
Almost every "MkDocs did something
odd" story is a line in this file
doing exactly what it says.

## The content folder

`docs/` holds the Markdown pages and
everything the site ships that isn't
generated: images, stylesheets,
downloads. A file `docs/compost.md`
becomes the page `compost/` in the
finished site. Files MkDocs doesn't
recognise are copied across untouched.

## The theme

The **theme** is the skin: page
layout, navigation furniture, search
box, colours. MkDocs ships two modest
themes (`mkdocs` and `readthedocs`);
the one most projects actually use is
**Material for MkDocs** — written
"Material" in this guide — installed
separately (chapter 3) and covered in
chapter 8. The theme renders every
page, so a theme problem looks like
an *every page* problem.

## Markdown extensions

Markdown itself is small. A set of
**extensions** — mostly from the
PyMdown Extensions package — adds the
documentation furniture: highlighted
code blocks, warning boxes
(admonitions), tabs, checklists,
footnotes. They are switched on in
`mkdocs.yml` and covered in chapter
10. When a page renders oddly —
a box showing as plain text, say —
an extension is usually missing.

## Plugins

**Plugins** are Python packages that
hook into the build itself: the
built-in **search** plugin that makes
the search box work, minifiers that
shrink the output, helpers that build
navigation from the folder layout.
Installed with `pip`, switched on in
`mkdocs.yml`, covered in chapter 10.
A plugin is code you run at build
time, so the rule is the same as for
any code: install ones you can name
a reason for.

## What breaks when each stops

| Part | Symptom when it's the problem |
| ---- | ----------------------------- |
| Command | `mkdocs: command not found`, or an old version building differently |
| Config | Site builds but with the wrong name, theme or order — or a YAML error and no build at all |
| Content | A page missing, a link dead, an image not copied |
| Theme | Every page looks wrong the same way |
| Extensions | One *kind* of markup renders as plain text |
| Plugins | Search dead, build slow, or a Python error at plugin import |
