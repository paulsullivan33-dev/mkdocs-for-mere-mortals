# Deploying to GitHub Pages

Publishing is two half-jobs: build
the site, then put `site/` somewhere
the web can see it. GitHub Pages —
free hosting for a repository's
website — is where most MkDocs sites
land, and there are two honest ways
to get one there.

## First, a setting

Pages must be told where its site
comes from: in the repository's
**Settings → Pages**, choose either
a branch (for the `gh-deploy` way)
or **GitHub Actions** (for the
workflow way). A site that builds
beautifully and never appears has
usually missed this step, or the
workflow below is failing — read its
log before touching your content.

## The short way: `mkdocs gh-deploy`

MkDocs carries a command for exactly
this:

```bash
mkdocs gh-deploy
```

It builds the site, commits the
output to a `gh-pages` branch of the
same repository, and pushes. Pages,
set to serve from that branch,
publishes it. It asks nothing about
CI and works from your own machine,
which is why tutorials start here.

Its honest costs: the published
files live in your repository's
history as a branch full of
generated HTML; the build that
publishes is whatever is on *your*
machine that day, versions and all;
and it needs your git credentials
with push rights at publish time.
Fine for a personal site; wearing
for a team.

## The steady way: a GitHub Actions workflow

The alternative builds on GitHub's
machines, from the committed source,
the same way every time. A workflow
for an MkDocs project does these
steps, in order:

1. Check out the repository.
2. Set up Python.
3. If the Markdown lives anywhere
   other than `docs/`, stage it there.
   (This series keeps guides at the
   repository root, so its workflow
   copies the `*.md` files into
   `docs/`, promotes `README.md` to
   `docs/index.md`, and copies the
   asset folders — the workflow file
   shipped with this very guide, at
   `.github/workflows/deploy-docs.yml`,
   is the working example, and every
   line of it is ordinary.)
4. `pip install mkdocs-material`
   (plus any plugins the project
   uses).
5. `mkdocs build --strict` — the
   strictness matters doubly here:
   a broken link should stop the
   publish, not ride along with it.
6. Upload `site/` as the Pages
   artifact, and deploy it.

Pushing to the main branch then
publishes, and the workflow's run
page is where a failed publish
explains itself — the exact log
lines a local `--strict` build would
have shown you first, if you'd run
one. Run one.

## Which should you choose?

`gh-deploy` to see your first site
live today, and because a one-person
project may never need more. The
workflow the day a second person
publishes, or the first time "it
worked on my machine" describes a
website. Both end at the same
place: files in, website out, and
the source of truth staying the
Markdown — never the generated HTML.

## Beyond GitHub

Nothing in the build is
GitHub-shaped: `site/` is plain
files. Any static host (Netlify,
Cloudflare Pages, an S3 bucket, a
plain web server, a Raspberry Pi on
your own shelf) takes the same
folder, usually with the same two
commands behind it — install, build
`--strict`, serve the folder. The
host is the replaceable part; the
habit of building strictly is not.
