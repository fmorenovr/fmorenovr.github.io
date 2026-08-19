# Personal resume website

Personal resume site, built with Jekyll and served by GitHub Pages at
[resume.fmorenovr.com](https://resume.fmorenovr.com) (see `CNAME`).

Resume content lives in `index.md`. Page structure/styling lives in
`_layouts/resume.md` and `assets/css/style.scss`.

## Pre-requisites

* **ruby** >= 3.0.2p107
* **gem** >= 3.3.5
* **bundle** >= 2.5.9
* **quarto** >= 1.6.42

On a fresh machine, install Ruby and its build tools first:

```bash
sudo apt install ruby ruby-dev make gcc rubygems-integration
```

## Setup from scratch

```bash
git clone https://github.com/fmorenovr/fmorenovr.github.io.git
cd fmorenovr.github.io
bundle config set --local path 'vendor/bundle'
bundle install
```

The `bundle config` step matters: without it, Bundler installs gems into
the system-wide Ruby gem directory, which on most machines your user
can't write to. That fails with a confusing error (e.g. "Could not find
X.gem for installation" or "An error occurred while installing X") that
doesn't actually mention permissions. Pointing `path` at `vendor/bundle`
installs gems into the project instead, which always works without
needing `sudo`.

`.bundle/` and `vendor/bundle` are gitignored — don't commit them, and if
you delete `.bundle/`, re-run the `bundle config set` command above before
`bundle install` again, or you'll hit the same permission error.

## Running locally

```bash
bundle exec jekyll serve
```

Then open http://localhost:4000.

## Notes for editing

- `Gemfile.lock` is regenerated for local Ruby compatibility and is only
  used for local preview — this repo has no GitHub Actions workflow, so
  the live site is actually built by GitHub Pages' own fixed toolchain,
  independent of this lockfile.
- Kramdown (this site's Markdown renderer) requires a blank line before
  a pipe table, or it silently renders the table as plain text.
