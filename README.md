# Mathemagie Blog

Blog technique en français — IA, LLM, IoT et bidouilles — généré avec [Jekyll 4](https://jekyllrb.com/) et publié sur GitHub Pages.

- **Site en ligne :** https://mathemagie.github.io/log
- **Dépôt GitHub :** [mathemagie/log](https://github.com/mathemagie/log)
- **Dossier local :** `blog2`

## Aperçu local

```bash
bundle install              # première fois uniquement
bundle exec jekyll serve    # → http://localhost:4000/log/
```

> Nécessite Ruby 3.x (Jekyll 4). En local, utiliser `rbenv` avec Ruby 3.3.11.

## Publier un nouvel article

1. Créer un fichier `_posts/AAAA-MM-JJ-slug.md`
2. Ajouter le front matter YAML en tête du fichier
3. Rédiger le contenu en Markdown (français)
4. `git commit` puis `git push` sur `main` — GitHub Actions reconstruit le site automatiquement

### Exemple de front matter

```markdown
---
layout: post
title: "Titre de l'article"
date: 2026-06-06 10:00:00 +0100
categories: ia llm
tags: [claude, python]
---

Contenu en Markdown.
```

- **categories** : chaîne séparée par des espaces
- **tags** : tableau YAML — affichés sur la page d'accueil sous forme `#tag`
- **URL de l'article** : `https://mathemagie.github.io/log/slug/` (sans date, voir `permalink` dans `_config.yml`)

### Images et vidéos

Placer les fichiers dans `assets/images/` ou `assets/videos/`, puis utiliser le filtre `relative_url` (obligatoire à cause du `baseurl: "/log"`) :

```markdown
![Description]({{ "/assets/images/mon-image.png" | relative_url }})
```

```html
<video controls playsinline preload="metadata" style="max-width: 100%;">
  <source src="{{ '/assets/videos/demo.mp4' | relative_url }}" type="video/mp4">
</video>
```

## Structure du projet

```
├── _config.yml       # Titre, baseurl, thème, plugins
├── _layouts/         # Surcharge du layout default (thème Hacker)
├── _posts/           # Articles du blog
├── assets/           # Images et vidéos des articles
├── index.md          # Page d'accueil — liste des articles
├── Gemfile           # Dépendances Ruby
└── .github/workflows/jekyll.yml
```

## Déploiement

Le site est publié via **GitHub Actions** (`.github/workflows/jekyll.yml`), pas via la branche `gh-pages`.

- **URL de base :** `baseurl: "/log"` dans `_config.yml`
- **Thème :** `jekyll-theme-hacker` (style terminal)
- **Plugins :** `jekyll-feed`, `jekyll-seo-tag`, `jekyll-sitemap`
- **Déclencheur :** chaque push sur `main`
- **Configuration Pages :** Settings → Pages → Source : **GitHub Actions**
