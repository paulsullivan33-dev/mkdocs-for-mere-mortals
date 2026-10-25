# Limits

An honest inventory, so nothing here
surprises you in production.

**It's a build, not a service.**
Every change is edit → build →
publish. There is no live editing,
no comment system, no accounts, no
"who changed this page" beyond what
git tells you. Sites that need those
need a database behind them — a
different tool category (chapter
14's wikis), not a bigger MkDocs.

**Search is the whole site, in one
file.** The built-in search loads an
index of every page's text into the
reader's browser. Lovely at a
hundred pages; at a few thousand,
the index file itself becomes the
slow download. Sites that size
outsource search (a hosted search
service wired into the theme) or
split into several sites.

**One build, one language, one
version.** Multi-language sites and
"docs for version 2 and version 3
side by side" are achievable —
through plugins and conventions, not
through anything the core promises.
If either is a hard requirement on
day one, price Docusaurus (chapter
14) before you paint yourself into
this corner.

**Themes are other people's
projects.** Material is a substantial
piece of software with its own
release pace and its own opinions
about the future — its build banner
(chapter 3) is a reminder that your
site's face is rented. Pin versions
in automated builds and read your
theme's changelog at upgrade time;
this series' own sites have been
bitten by exactly one class of
surprise, and it was a theme's.

**Python is the toll.** Everything —
core, theme, plugins — arrives as
Python packages into an environment
you maintain. A machine with no
Python, or one where Python is
managed by someone else, turns a
ten-minute install into a negotiation.
The container route (chapter 3)
exists for that case.

**YAML fails like YAML.** The config
is powerful and its error messages
are about the file, not your intent.
A colon in the wrong place, a tab
where spaces belong — small file,
sharp edges (chapter 15 collects the
real wounds).

**Static means static.** Forms,
payments, anything per-reader or
secret has to live somewhere else and
be linked or embedded. That is the
bargain that buys the reliability:
a folder of files cannot be down in
any interesting way, cannot be
hacked into (there is nothing to log
into), and can be re-hosted in an
afternoon — but it cannot *do*
anything. When a page must do
something, the doing is another
system's job.
