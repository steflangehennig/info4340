# INFO 4340 Analytics and AI

Jekyll site for INFO 4340 Analytics and AI at the University of Denver's Daniels College of Business.

Live at: `https://steflangehennig.github.io/info4340`

## Adding content

**New page:** Create a `.md` file anywhere with front matter:
```yaml
---
layout: page
title: Your Page Title
---
Your content here in Markdown.
```

**New guide:** Drop a `.html` or `.md` file in `guides/` and add a card to `guides/index.md`.

**Update "This week":** Edit the sidebar in `index.md`.

## Local preview (optional)

```bash
gem install bundler jekyll
bundle exec jekyll serve
# → http://localhost:4000/info4340
```

## Config

Edit `_config.yml` to update instructor name, term, meeting time, contact, and nav links.
