# Markdown Extensions

Plain Markdown gives you headings,
lists, links and not much else.
Documentation wants more: warning
boxes, code that highlights itself,
tabs, checklists. Those come from
**extensions** — add-ons to the
Markdown processor, switched on in
`mkdocs.yml`:

```yaml
markdown_extensions:
  - admonition
  - attr_list
  - pymdownx.details
  - pymdownx.highlight:
      anchor_linenums: true
  - pymdownx.superfences
  - pymdownx.tabbed:
      alternate_style: true
  - pymdownx.tasklist:
      custom_checkbox: true
```

That list is the lab's, and every
entry on it is exercised by the
garden handbook. An extension that
is missing doesn't stop the build —
it quietly renders its markup as
ordinary text — so this chapter is
also a diagnostic: when one *kind*
of thing looks wrong on every page,
look here first.

## Admonitions — the boxes

`admonition` (with `pymdownx.details`
for the collapsible kind) turns a
marked paragraph into a coloured
box:

```markdown
!!! warning "One plot per household"
    Plots are in short supply...
```

`note`, `tip`, `warning` and
`danger` are the house styles; the
word after `!!!` picks the colour
and icon, the quoted text is the
title. `???` instead of `!!!` makes
the box start closed, for the
interesting-but-optional. The
handbook uses all of them — a
warning about plot rationing, a
danger list for the compost heap, a
closed note about the mower.

## Code that highlights itself

`pymdownx.superfences` is what lets
fenced code blocks live safely
inside lists and boxes, and
`pymdownx.highlight` colours them by
language, with line numbers when
asked (`anchor_linenums` makes each
line linkable). The handbook's one
script renders as numbered,
coloured Python (build evidence in
transcript t02). A block whose
language you don't name stays plain
— name your languages.

## Tabs

`pymdownx.tabbed` (with
`alternate_style`) writes tabbed
content as a list of `=== "Title"`
sections:

```markdown
=== "Dry spell rota"
    ...the rota table...

=== "Normal weeks"
    ...the general rule...
```

One fact, several cases — seasonal
instructions, per-platform commands —
without three pages saying nearly
the same thing. The handbook's
watering page uses it for exactly
that.

## Checklists

`pymdownx.tasklist` renders `- [ ]`
and `- [x]` as checkboxes instead of
a bulleted list with odd punctuation
— the meetings page's spring jobs
list. `custom_checkbox: true` lets
the theme draw them in its own
style, which the lab sets.

## The rest of the shelf

Two more are in nearly every project
sooner or later, though the lab's
handbook doesn't need them: `toc`
with `permalink: true` (a ¶ link on
every heading, so readers can cite a
section) and `footnotes` (numbered
notes at the page foot). The
PyMdown documentation lists twenty
more; add one at a time, when a
page is already straining against
plain Markdown to say something.
