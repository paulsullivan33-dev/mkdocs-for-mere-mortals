# Writing Pages

A page is a Markdown file. This
chapter is the Markdown that MkDocs
projects actually use, in the order
you will reach for it. (For Markdown
itself — headings, emphasis, lists —
any intro will do; what follows is
where MkDocs adds its own rules.)

## Links between pages

Link to another page the way you
link to a file: relative, with the
`.md` on the end.

```markdown
Wondering what may go on the heap?
See [Compost](compost.md).
```

At build time MkDocs rewrites that
to the finished page's address
(`compost/`), checks the target
exists, and warns if it doesn't —
which, under `build --strict`,
fails the build (chapter 4's
transcript t04 is that happening).
Links to a section of a page work
the same way: `[the fees](getting-a-plot.md#fees)`.

Links to the outside world are
ordinary Markdown links with the
full `https://` address, and MkDocs
leaves them alone.

## Images and other files

Anything in `docs/` that isn't
Markdown is copied to the site
unchanged, so an image sits next to
the pages that use it:

```text
docs/
  compost.md
  images/
    heap-diagram.png
```

```markdown
![The three bays of the heap](images/heap-diagram.png)
```

The same trick carries downloads —
a PDF of the membership form, a
spreadsheet rota. Link to the file;
it arrives in the site byte for
byte.

## Code blocks

Fenced blocks with a language name
get syntax highlighting when the
right extensions are on (chapter
10). The lab's plot-care page keeps
a tiny Python helper script this
way — prose explains it, the block
holds it:

````markdown
```python
def harvest_window(sown, weeks):
    ...
```
````

A block with no language name is
plain monospaced text, which is the
right choice for terminal sessions
and file excerpts.

## Tables, lists, quotes

Tables are the pipe style every
Markdown writer knows, and they are
the handbook's workhorse — fees,
rotas, tool counts. Long lists of
steps belong in numbered lists;
decisions and rules read well as
blockquotes only when they truly
are quotations. Keep a page to one
job: a reader who lands from search
should know within a screen whether
they are in the right place.

## Page titles and the first heading

A page's title — what the tab, the
navigation and search results show —
comes from its first `#` heading
unless configuration says otherwise
(chapter 7). Write the heading a
reader would search for; "Getting a
Plot" earns its place, "Page 3"
doesn't.

## Front matter

A page may open with a small YAML
block between `---` lines — *front
matter* — for per-page instructions
the theme understands, most often a
title that differs from the heading,
or hiding a page from navigation
drafts:

```markdown
---
title: Fees for 2026
---
# Getting a Plot
```

Most pages never need it. Reach for
it when one page misbehaves, not as
a habit.
