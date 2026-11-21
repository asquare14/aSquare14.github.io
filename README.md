# asquare14.github.io

Personal site of Atibhi Agrawal, served by GitHub Pages from `master`.

## Editing content

Almost everything on the home page is plain YAML in `_data/`:

| File | What it controls |
| --- | --- |
| `_data/home.yml` | Intro heading, paragraph, the "right now" pills, section blurbs |
| `_data/work.yml` | Work rows |
| `_data/projects.yml` | Project groups and rows |
| `_data/art.yml` | Paintings (images go in `assets/images/art/`) |
| `_data/books.yml` | Library shelf |

Social handles and the site description are in `_config.yml`. Old posts are in `_posts/` and listed at `/blog/`.

## Running locally

```sh
bundle install
bundle exec jekyll serve --config _config.yml,_config-dev.yml
```
