# CLAUDE.md — Mathemagie Blog

Context for AI assistants working in this repository.

## What this is

A **French-language technical blog** by [mathemagie](https://github.com/mathemagie), built with **Jekyll 4** and published on **GitHub Pages**.

- **Live URL:** https://mathemagie.github.io/log
- **GitHub repo:** https://github.com/mathemagie/log (`origin` remote)
- **Local workspace folder:** `blog2` (name differs from the GitHub repo `log`)

Topics: IA/LLM, IoT, bidouilles, dev workflows. Posts are written in French.

## Tech stack

| Piece | Choice |
|-------|--------|
| Generator | Jekyll ~> 4.4 |
| Theme | `jekyll-theme-hacker` (terminal aesthetic) |
| Plugins | `jekyll-feed`, `jekyll-seo-tag`, `jekyll-sitemap` |
| Deploy | GitHub Actions (`.github/workflows/jekyll.yml`) |
| Ruby (CI) | 3.3 |
| Ruby (local) | 3.3.11 via rbenv (see README) |

The theme provides `default` and `post` layouts. There is no custom `post` layout — posts use the theme's built-in `post` layout.

## URL structure

Configured in `_config.yml`:

```yaml
url: "https://mathemagie.github.io"
baseurl: "/log"
permalink: /:title/
```

Implications:

- Homepage: `https://mathemagie.github.io/log/`
- A post titled "Le Lapin Cosmique" → `https://mathemagie.github.io/log/lapin-cosmique/`
- **Always use `relative_url`** for internal links and assets: `{{ "/assets/images/foo.png" | relative_url }}`
- Local preview runs at `http://localhost:4000/log/` (baseurl included)

## Repository layout

```
blog2/
├── _config.yml          # Site settings (title, baseurl, theme, plugins)
├── _layouts/
│   └── default.html     # Overrides theme default — drops site-description <h2>
├── _posts/              # Blog articles (YYYY-MM-DD-slug.md)
├── assets/
│   ├── images/          # Post images (committed to repo)
│   └── videos/          # Post videos
├── index.md             # Homepage — lists all posts with tags
├── Gemfile / Gemfile.lock
├── .github/workflows/jekyll.yml
└── README.md
```

Build artifacts (`_site/`, `.jekyll-cache/`) are gitignored.

## Writing a new post

1. Create `_posts/YYYY-MM-DD-slug.md`
2. Add YAML front matter:

```yaml
---
layout: post
title: "Titre de l'article"
date: 2026-06-06 10:00:00 +0100
categories: ia llm          # space-separated
tags: [claude, python]      # YAML array — shown on homepage
---
```

3. Write body in Markdown (French)
4. `git commit` + `git push` to `main` → GitHub Actions builds and deploys

### Post conventions observed in this repo

- **Commit messages:** `Add post: <short title>` (matches existing history)
- **Language:** French for post content; English OK in code/URLs
- **Tags:** YAML array; homepage renders them as `#tag` next to each post title
- **Categories:** space-separated string in front matter
- **Images:** store under `assets/images/`, reference with Liquid `relative_url`
- **Videos:** raw HTML `<video>` block + `relative_url` on `<source src>`
- **Embeds:** GitHub gists via `<script src="https://gist.github.com/...">` (see SKILL.md post)
- **External content:** when importing from another mathemagie page (e.g. `mathemagie.github.io/bidouille/...`), download media into `assets/` rather than hotlinking

### Current posts (as of June 2026)

| File | Title | Tags |
|------|-------|------|
| `2026-05-30-bienvenue.md` | Bienvenue sur le blog | jekyll, github-pages |
| `2026-06-06-skill-md-apprendre-avec-ia.md` | SKILL.md : transformer l'IA en véritable professeur | claude, prompt-engineering, apprentissage |
| `2026-06-06-lapin-cosmique.md` | Le Lapin Cosmique — ISS + Nabaztag | iss, nabaztag, python, iot |

## Customizations

- **`_layouts/default.html`:** custom header — only site title, no subtitle/description, no "View on GitHub" button
- **`index.md`:** simple post list with date and tags (no welcome paragraph)
- No `_includes/`, no about page (removed in prior commits)
- `head-custom.html` is referenced in the layout but comes from the theme (not overridden locally)

## Local development

```bash
bundle install          # first time
bundle exec jekyll serve
# → http://localhost:4000/log/
```

Requires Ruby 3.x. System Ruby 2.6 on macOS will fail (Bundler version mismatch) — use rbenv Ruby 3.3.11.

## Deployment

- Trigger: push to `main` or manual `workflow_dispatch`
- Build: `bundle exec jekyll build --baseurl "<pages base_path>"`
- Deploy: `actions/deploy-pages@v4`
- GitHub Pages source must be set to **GitHub Actions** (not `gh-pages` branch)

## Related mathemagie projects

- **lapin_cosmique** — https://github.com/mathemagie/lapin_cosmique (ISS tracking → Nabaztag ears)
- **bidouille pages** — https://mathemagie.github.io/bidouille/ (interactive demos, separate from this blog)

## Agent guidelines

- **Do not** change `url` / `baseurl` without understanding GitHub Pages project-site URLs
- **Do not** commit `_site/`, `.jekyll-cache/`, or `vendor/`
- **Prefer** minimal diffs; match existing post/front-matter style
- **Use** `relative_url` for all assets and internal links
- **Only commit** when explicitly asked
- **Only push** when explicitly asked
- Posts are the primary content — avoid unrelated refactors to theme/layout unless requested
