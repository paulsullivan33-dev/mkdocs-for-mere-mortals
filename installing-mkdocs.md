# Installing MkDocs

MkDocs is a Python program, so the
install is: have Python, then let
Python's package installer fetch
MkDocs and the Material theme. Ten
minutes, most of it watching a
progress bar.

## Step 1 — Python

You need Python 3.8 or newer (the
lab's MkDocs 1.6.1 asks for 3.8+;
check the release notes of whatever
is current when you read this).

```bash
python3 --version
```

Linux usually has it; if not, your
distribution's package manager does
(`python3` and `python3-venv` on
Debian and Ubuntu). On Windows,
install Python from python.org and
tick "add to PATH"; commands in this
guide are the same, with `python`
often spelled `py`. On macOS, Python
comes from python.org or Homebrew.

## Step 2 — a virtual environment

A **virtual environment** (venv) is a
private folder holding one project's
Python packages, so the documentation
tools for one project never fight
another's — and never fight your
system's Python, which your operating
system may be using for its own
purposes and will defend, sometimes
by refusing system-wide installs.

```bash
python3 -m venv ~/mkdocs-venv
source ~/mkdocs-venv/bin/activate   # Windows: ~\mkdocs-venv\Scripts\activate
```

Your prompt changes to show the
environment is active. Everything
`pip` installs now lands in that
folder. `deactivate` leaves it; the
folder can simply be deleted to
uninstall everything in it.

## Step 3 — install

```bash
pip install mkdocs mkdocs-material
```

That is the whole shopping list for
most projects: the builder, and the
theme worth having. Plugins (chapter
11) are installed the same way, into
the same environment, when you decide
you want them.

Check: ask for the version.

```bash
mkdocs --version
```

The lab's answer, and the one this
guide's chapters were verified
against:

```text
mkdocs, version 1.6.1 from ... (Python 3.12)
```

The Material theme's version is
Python's to report: `pip show
mkdocs-material` answered 9.7.7 in
the lab. Versions move; the commands
in this guide are the ones that
matter, and any recent version runs
them the same way.

## The banner you may see

Material 9.7.7 prints a notice about
the announced "MkDocs 2.0" at the top
of every build. It is the theme's
authors talking about the project's
future, printed by their package —
not a warning about your site, and
not something your build did wrong.
The build's real verdict is its last
lines and its exit code; chapter 15
returns to this.

## Other ways people install it

- **System packages.** Debian and
  Ubuntu carry an `mkdocs` package.
  It is convenient and usually older,
  and the Material theme may not be
  packaged at all — which is why this
  guide teaches the `pip` route.
- **A container image.** The Material
  project publishes one
  (`squidfunk/mkdocs-material`) for
  people who keep Python off their
  machines entirely. Same commands,
  run inside the container.
- **Per-project requirements.** Teams
  often write the package list to a
  `requirements.txt` and install with
  `pip install -r requirements.txt`,
  so every builder — human or CI
  machine — gets identical versions.
  Chapter 11's workflow does the
  simple form of this.
