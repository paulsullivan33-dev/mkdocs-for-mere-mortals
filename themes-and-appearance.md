# Themes and Appearance

The theme decides how every page
looks. MkDocs ships two built-in
themes; nearly every real project
ends up on the third one in this
chapter. Try the built-ins for a
first afternoon if you like — the
commands and content are identical,
only the skin changes.

## The built-in themes

```yaml
theme:
  name: mkdocs        # or: readthedocs
```

`mkdocs` is plain and serviceable;
`readthedocs` imitates the well-known
documentation host of that name.
Both are respectable, neither is
pretty, and both make fine proofs
that your content stands on its own.

## Material

**Material for MkDocs** ("Material"
in this guide) is a separate package
(chapter 3) and the theme this whole
series is published with:

```yaml
theme:
  name: material
```

Three lines, and the site gets a
clean layout, a proper search box,
and navigation that behaves on a
phone. This guide's own site uses
nothing more than that — the
restraint is deliberate, and the
lab site is where this chapter's
extras are demonstrated instead.

## Colour, and the light/dark toggle

Material's **palette** is the colour
scheme. The lab sets a green primary
colour and — the feature readers
actually thank you for — a toggle
between light and dark:

```yaml
theme:
  name: material
  palette:
    - scheme: default
      primary: green
      accent: lime
      toggle:
        icon: material/brightness-7
        name: Switch to dark mode
    - scheme: slate
      primary: green
      accent: lime
      toggle:
        icon: material/brightness-4
        name: Switch to light mode
```

Two schemes, each naming the other
as its destination. The lab verified
the result in the built HTML: both
choices present in the page, labelled
as written here (the evidence is in
the build of transcript t02).
Material also honours a reader's
operating-system preference when the
palette is set up with media queries
instead — the toggle is the simpler
gift, and the one the lab gives.

## Features are switches, not themes

Under `theme.features`, Material
takes a list of behaviour switches.
The lab turns on four:

```yaml
  features:
    - navigation.sections   # nav sections as groups (chapter 7)
    - navigation.top        # a "back to top" button on long pages
    - content.code.copy     # a copy button on every code block
    - search.suggest        # search-as-you-type suggestions
```

Each is one line and one idea; the
full list is long, and the discipline
is to add a switch when a reader
need names it, not because it exists.

## Your own CSS, and the favicon

Small adjustments belong in your own
stylesheet, loaded after the theme's
(chapter 6):

```yaml
extra_css:
  - stylesheets/extra.css
```

The lab's `extra.css` is ten
lines: a slightly larger table font
and a green rule under the header.
That is the right size for a theme
adjustment. The moment it reaches
for layouts and components, you are
no longer adjusting a theme — you
are maintaining one, which is a
different and larger job. A site
logo and favicon are single image
files named in the theme settings
(`logo:` and `favicon:` under
`theme:`), living in `docs/`.

## A word on chasing appearance

Every hour in the palette is an hour
not spent on the words, and readers
forgive a plain site with answers
faster than a beautiful site without
them. Set the palette, add the copy
button, publish; appearance has a
long tail and the content is the
dog.
