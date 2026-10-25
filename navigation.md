# Navigation

Navigation is the table of contents
a reader browses: the list down the
side (or across the top) of every
page. MkDocs will happily invent one
from your folder — files in
alphabetical order, titles from their
first headings — and for six pages
that is nearly respectable. The
moment order matters, say so.

## Saying it outright: `nav`

```yaml
nav:
  - Home: index.md
  - Getting a Plot: getting-a-plot.md
  - Looking After Your Plot: plot-care.md
  - Compost: compost.md
  - The Tool Shed: tool-shed.md
  - Meetings and Jobs: meetings-and-jobs.md
```

Each line is a label and the file it
opens. The label is yours to write
well — it needn't match the page's
heading ("Looking After Your Plot"
labels a page whose heading could be
shorter). Nesting makes sections:

```yaml
nav:
  - Home: index.md
  - Growing:
      - Getting a Plot: getting-a-plot.md
      - Looking After Your Plot: plot-care.md
      - Compost: compost.md
  - Running the Garden:
      - The Tool Shed: tool-shed.md
      - Meetings and Jobs: meetings-and-jobs.md
```

A section is a label with no file
and a deeper-indented list — with
Material's `navigation.sections`
feature (chapter 8) it becomes a
visible grouping instead of a
collapsible afterthought.

## The page you forgot

A file that exists in `docs/` but
not in `nav` is still built and
still reachable by its address; the
build lists it in an informational
message ("pages that exist in the
docs directory, but are not included
in the nav"). That is the right
behaviour for drafts you link to
deliberately — and a silent failure
for a finished page you simply
forgot. Read the build output; the
list is short and it is honest.

## Letting the folder decide: awesome-pages

The **awesome-pages** plugin moves
ordering out of `mkdocs.yml` into a
small `.pages` file per folder:

```yaml
# docs/.pages
nav:
  - index.md
  - getting-a-plot.md
  - plot-care.md
  - compost.md
  - tool-shed.md
  - meetings-and-jobs.md
```

The lab verified this in a scratch
copy (transcript t06): with `nav`
removed from `mkdocs.yml` and the
plugin installed, the same site
builds `--strict`-clean with the
`.pages` order in force. The lab
also recorded the plugin's sharp
edge: entries written as bare titles
(`- Getting a Plot`) fail the build
with `NavEntryNotFound` — in a
`.pages` file, entries are file
names, and titles come from the
pages themselves.

Choose one source of truth. A nav in
the config is visible in one place
and reviewed like code; `.pages`
files keep big folders self-managing.
What doesn't work is both at once —
the plugin wins, quietly.

## Order is an editorial act

However it is written down, order
the pages the way a newcomer needs
them: start here, then the everyday
tasks, then the reference material,
then the rarely-needed pages. The
navigation is the one part of the
site every reader reads.
