# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

Personal website of Atibhi Agrawal, hosted on GitHub Pages and built with Jekyll (the `github-pages` gem, so only Pages-whitelisted plugins work). Custom theme, no JavaScript: Liquid layouts plus one plain CSS file. White background, Cormorant Garamond headings, Jost body text, one blush accent (`--accent`).

## Commands

```sh
bundle install                                                  # install dependencies
bundle exec jekyll serve --config _config.yml,_config-dev.yml   # local dev at http://localhost:4000
bundle exec jekyll build                                        # build to _site/
bundle exec htmlproofer ./_site                                 # validate built site links
```

The `_config-dev.yml` override sets `url` to localhost. Templates use `relative_url`, so local links work either way.

## Architecture

Deployment is automatic on push to `master`. `_site/`, `.sass-cache/` and `vendor/` are gitignored build output.

- `_data/*.yml` holds the home page content (intro, work, projects, art, books). Prefer editing these over the templates.
- `_layouts/default.html` is the shell (head, `{% seo %}`, header, footer). `home.html` renders the numbered home sections from `_data/`. `page.html` and `post.html` wrap Markdown in `.prose`.
- `_includes/header.html` and `footer.html` are the only includes. Footer links come from handles in `_config.yml`.
- `assets/css/main.css` holds all styles, plain CSS with custom properties on `:root`.
- `_posts/` are the 2018–2020 posts, permalinks `/:title/`. Keep those URLs stable. New writing lives on Substack.
- `projects.html` is a meta-refresh redirect from the old `/projects/` URL to `/#projects`.
