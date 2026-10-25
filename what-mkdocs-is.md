# What MkDocs Is

MkDocs is a **static site generator**
aimed at documentation. You write
pages in **Markdown** — plain text
with light markup for headings, lists
and links — keep them in a folder,
and MkDocs turns that folder into a
finished website: HTML pages with
navigation, a search box, and a theme
that makes it look like it was
designed on purpose.

"Static" is the load-bearing word.
There is no database, no program
running on the server, no login. The
build produces a folder of files, and
any web host that can serve files can
serve the result — including GitHub
Pages, for free (chapter 11). Editing
means editing text files; publishing
means rebuilding and copying files.

## The shape of a project

A MkDocs project is deliberately
small:

```text
mkdocs.yml      the configuration file
docs/
  index.md      the home page
  ...           more Markdown pages,
                images, stylesheets
```

One configuration file, one folder of
content. `mkdocs serve` shows you the
site in your browser while you write,
rebuilding on every save; `mkdocs
build` produces the finished site in
a `site/` folder. That is nearly the
whole of it, and the smallness is the
point: there is very little between
your text and the published page.

Check: chapter 4 builds exactly this,
and the lab's sample project — a
fictional community garden's members'
handbook — sits in `mkdocs-lab/`
complete with its six pages, ready to
build with the commands in chapter 4.

## Who it is for

MkDocs suits anyone whose writing is
documentation-shaped: longer than a
README, read in pieces, found by
search and by browsing a table of
contents. The software project
documenting itself; the club or small
organisation writing down how it runs
(our lab's garden); the team keeping
a runbook; the hobbyist publishing
notes they are tired of losing. The
common thread is *text that should
outlast a chat thread*, kept in files
its owners control.

## What it is not

MkDocs is not a **wiki**: there is no
edit-in-the-browser, no page history
of its own. The files live in a
folder — usually a git repository —
and the version control is git's
(chapter 13 covers tools that differ).
It is not a **blog engine** out of
the box: pages have no dates, tags or
front page of latest posts unless you
add them. It is not a **web
framework**: it makes one kind of
thing, a documentation site, and
makes it well. And it is not a hosted
service: nothing phones home, and the
site works the same in ten years if
the files survive.
