# blog2

A Jekyll blog published via GitHub Pages.

## Local preview

```bash
bundle install          # first time only
bundle exec jekyll serve # http://localhost:4000/log/
```

> Requires a Ruby with Bundler. The system Ruby 2.6 may be too old for the
> latest `github-pages` gem — install a newer Ruby (e.g. via `rbenv install 3.3.x`)
> if `bundle install` complains.

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

This repo is intended to publish at **https://mathemagie.github.io/log**.

1. Push this directory to a GitHub repo named `log` under the `mathemagie` account.
2. In the repo: **Settings → Pages → Build and deployment → Source: Deploy from a branch**.
3. Select branch `main` (or `master`), folder `/ (root)`, and Save.
