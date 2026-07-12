# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

Personal website/blog of Atibhi Agrawal, hosted on GitHub Pages. Built with Jekyll using the [Indigo](https://github.com/sergiokopplin/indigo) minimalist template. No JavaScript by design — just Jekyll, Sass, and SVG.

## Commands

```sh
bundle install                                                  # install dependencies
bundle exec jekyll serve --config _config.yml,_config-dev.yml   # local dev at http://localhost:4000
bundle exec jekyll build                                        # build to _site/
bundle exec htmlproofer ./_site                                 # validate built site links
rake test                                                       # build + htmlproofer in one step
```

The `_config-dev.yml` override sets `url` to localhost — always include it when serving locally, otherwise absolute links point at the production URL. The jekyll-admin plugin provides a local post editor at `http://localhost:4000/admin` (local only, not on GitHub Pages).

## Architecture

Standard Jekyll structure; deployment is automatic on push to `master` (GitHub Pages builds the site — `_site/` is a local build artifact, don't hand-edit it).

- `_config.yml` — all site content toggles live here: which nav pages exist (`about`, `blog`, `projects`, `talks`, `lists`, `tce`), social links, post features (`read-time`, `show-tags`, `related`, `show-author`), and the `authors` map used by `_includes/author.html`.
- `_posts/` — blog posts, named `YYYY-MM-DD-title.md`. Permalinks are `/:title/` (no date in URL).
- `_layouts/` — `default.html` wraps everything and runs through `compress.html` to minify HTML; `page.html` and `post.html` build on it.
- `_includes/` — nav, footer, social links, Disqus, analytics snippets; `style.scss` is the Sass entry point pulling from `_sass/{base,components,pages}`.
- Top-level `.md`/`.html` files (`about.md`, `talks.md`, `projects.html`, etc.) are the site pages; their visibility is controlled by the corresponding boolean in `_config.yml`.
