# Plugins

A plugin is Python code that takes
part in the build: it can read and
change pages, navigation and config
before anything is written out.
Installing one is two steps — the
package, then its name in the
config:

```bash
pip install mkdocs-minify-plugin
```

```yaml
plugins:
  - search
  - minify:
      minify_html: true
```

Order in the list is the order
plugins run in. A plugin that isn't
installed stops the build with an
import error naming it — annoying,
and much better than one that fails
silently.

## Search — the one that's already there

MkDocs carries a built-in **search**
plugin, enabled by default. At build
time it writes every page's text into
`search/search_index.json`; in the
browser, the theme's search box reads
that file and answers entirely
client-side — no server component,
which is how a static site can have
search at all. The lab's evidence:
the index file written by transcript
t02's build, and the same JSON
served and read back by curl in
transcript t03.

With Material as the theme, search
also keys off the language settings
and offers the suggestions the lab
turns on (`search.suggest`). If your
site's search box ever answers
nothing, the first check is whether
that JSON file exists in the built
site — if it does, the problem is in
the browser; if it doesn't, a plugin
was disabled or displaced.

## Minify — the one the lab adds

The **minify** plugin strips
whitespace and optional quotes from
the finished HTML (and can do the
same for CSS and JavaScript), so
pages weigh less on the wire.
Measured on the lab's handbook,
built identically with and without
it (transcript t05):

| | HTML, all six pages |
| --- | ---: |
| Without minify | 120,313 bytes |
| With minify | 95,242 bytes |

About a fifth smaller, for one
plugin line — and a trade worth
naming: minified HTML is miserable
to read with "view source", which
you will want exactly once, the day
something looks wrong. Many projects
minify only in the publishing build
for that reason.

## awesome-pages — navigation from the folder

Chapter 7 covers what it does
(navigation from `.pages` files in
each folder). As a plugin it is the
honest example of the species:
installed in one command, configured
by files rather than code, and
strict about its inputs — the lab's
first attempt, with bare titles in
`.pages`, failed the build outright
rather than guessing (transcript
t06).

## Plugins the lab did not run

Named so you know the shelf exists,
labelled as untested here: plugins
that stamp each page with its git
revision date; that generate a PDF
or an ebook from the site; that
build a photo gallery or draw
diagrams from text (Mermaid diagrams
need only an extension and the
theme, for what it's worth); that
publish a blog section under the
docs. Each is somebody's maintained
project of varying age — the
criterion before installing is the
same as for themes: can you name
the reader problem it solves, and
does its last release suggest it is
still looked after?

## A restraint worth keeping

Every plugin is a dependency that
can break on the next MkDocs
upgrade, and a voice in your build
that isn't yours. The handbook runs
two. That is the right order of
magnitude: add the third when a
real page hurts without it.
