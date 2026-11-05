# waxhn.com

Personal blog built with [Jekyll](https://jekyllrb.com/) and a minimal customization of the [Chirpy theme](https://github.com/cotes2020/jekyll-theme-chirpy), hosted on GitHub Pages.

## Setup

Requires Ruby 3.2+ and Git LFS (assets in `assets/` are stored with LFS).

```bash
export GEM_HOME="$HOME/gems" PATH="$HOME/gems/bin:$PATH"   # add to ~/.bashrc
gem install jekyll bundler
bundle install
```

## Development

```bash
bundle exec jekyll serve --livereload            # add --drafts for drafts
JEKYLL_ENV=production bundle exec jekyll serve   # what gets deployed
```

Production minifies HTML onto one line, so inline `<script>`s must use `/* */` comments, not `//`.

Pushing to `main` deploys via `.github/workflows/pages-deploy.yml`.

## Posts

`_posts/YYYY-MM-DD-title.md`:

```yaml
---
title: "Post Title"
date: 2026-03-04 12:00:00 -0500
description: Shown under the title on the home page and the post.
categories: [Category]
tags: [tag1, tag2]
authors: [max_yu]   # optional, keys from _data/authors.yml
math: true          # optional, enables $inline$ and $$block$$ LaTeX
---
```

Images go in `assets/img/<post>/`. For figures that follow light/dark mode:

```markdown
![Alt](/assets/img/post/fig-light.svg){: .light }
![Alt](/assets/img/post/fig-dark.svg){: .dark }
```

## Theme overrides

`_layouts/` and `_includes/` override Chirpy 7.4.1 files of the same name, so theme updates don't reach them. Styles are in `assets/css/jekyll-theme-chirpy.scss`.

- `_includes/site-header.html` replaces Chirpy's sidebar. Header links come from `_tabs/`.
- `_includes/js-stubs.html` holds hidden elements Chirpy's JS requires on load. Don't remove it.
