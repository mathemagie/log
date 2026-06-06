# blog2

A Jekyll blog published via GitHub Pages.

## Local preview

```bash
bundle install          # first time only
bundle exec jekyll serve # http://localhost:4000/log/
```

> Requires Ruby 3.x (Jekyll 4). Installed locally via `rbenv` (Ruby 3.3.11).

## Publish a new post

Create `_posts/YYYY-MM-DD-title.md` with front matter:

```markdown
---
layout: post
title: "My title"
date: 2026-05-30 10:00:00 +0100
categories: meta
---

Content in Markdown.
```

Then `git commit` and `git push`. GitHub rebuilds automatically.

## Deploy to GitHub Pages

This repo publishes at **https://mathemagie.github.io/log** via GitHub Actions
(`.github/workflows/jekyll.yml`), which builds with the latest Jekyll 4.x.

Pages must be configured with **Settings → Pages → Source: GitHub Actions**.
Every push to `main` triggers a build and deploy.
