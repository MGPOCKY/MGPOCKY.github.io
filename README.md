# mgpocky.github.io

Personal homepage of **Kyungmin Kim** — <https://mgpocky.github.io>

Built with [Jekyll](https://jekyllrb.com/) and the
[academic-homepage](https://github.com/luost26/academic-homepage) template (MIT, see `LICENSE`),
following the customizations of [purplepig4657.github.io](https://github.com/purplepig4657/purplepig4657.github.io).
GitHub Pages builds the `master` branch automatically on every push; no CI configuration is needed.

## Where things live

| What | Where |
| --- | --- |
| Name, bio, positions, contact links, education, experience, awards, teaching | `_data/profile.yml` |
| Which homepage sections are shown; footer text | `_data/display.yml` |
| Navigation bar entries | `_data/navigation.yml` |
| Author names to bold / link in publication lists | `_data/authors.yml` |
| News items (one file per item) | `_news/` |
| Publications (one file per paper) | `_publications/` — see `_publications/_example.md` |
| Blog posts | `_posts/` |
| Portrait, logos, blog figures | `assets/images/` |
| Site URL, timezone, Google Analytics, plugins | `_config.yml` |
| Layouts and reusable widgets | `_layouts/`, `_includes/widgets/` |

## Common edits

### News
Create `_news/YYYY-MM-DD-slug.md`:

```yaml
---
title: >-
    Text of the news item. HTML such as <b>bold</b> and <a href="...">links</a> is allowed.
date: 2026-09-09 12:00:00 +0900
# date_display: "Sep"   # optional: override the "Mon DD" label when the exact day is unknown ("" hides it)
---
```

### Publications
1. Copy `_publications/_example.md` to `_publications/<year>/<name>.md` and fill in the fields
   (files and folders starting with `_` are ignored by Jekyll).
2. Uncomment the **Publications** entry in `_data/navigation.yml`.
3. Set `show_selected_publications: true` in `_data/display.yml` to feature `selected: true`
   papers on the homepage.

### Blog posts
Create `_posts/YYYY-MM-DD-slug.md`:

```yaml
---
title: 'Post title'
date: 2026-09-09 12:00:00 +0900
tags: [Tag1, Tag2]
excerpt: One-line summary shown in the blog list (optional; the first paragraph is used otherwise)
---
Markdown body. Code blocks, tables, KaTeX math ($...$ / $$...$$), and a sticky table of
contents are supported.
```

Posts automatically use the `blog_post` layout and the URL `/blog/YYYY/MM/DD/slug/`
(add `permalink:` to override). Put figures in `assets/images/post_figures/<slug>/` and
reference them as `{{ '/assets/images/post_figures/<slug>/figure.png' | relative_url }}`.

## Running locally

Requires Ruby 3.x and Bundler.

```bash
bundle install
bundle exec jekyll serve --livereload
```

Then open <http://localhost:4000>. The `github-pages` gem pins the same Jekyll and plugin
versions that GitHub Pages uses, so the local build matches what gets published.
