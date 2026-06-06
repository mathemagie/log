---
layout: post
title: "Le Lapin Cosmique — quand la Station Spatiale fait bouger les oreilles du Nabaztag"
date: 2026-06-06 18:00:00 +0100
categories: iot bidouille
tags: [iss, nabaztag, python, iot]
---

![Le Lapin Cosmique — artwork]({{ "/assets/images/lapin_cosmique_artwork.png" | relative_url }})

Mon Nabaztag **fait bouger ses oreilles** à chaque passage de la Station Spatiale Internationale au-dessus de la France ! Ce projet IoT un peu loufoque fait le pont entre la Terre et l'espace — la mécanique orbitale se transforme en chorégraphie d'oreilles de lapin.

## Comment ça marche

Derrière la scène, un script Python surveille en continu la position de l'ISS via l'[API Open-Notify](http://open-notify.org/). Quand la station entre dans l'espace aérien français, le script envoie des commandes de mouvement d'oreilles au Nabaztag par connexion socket TCP. De la magie simple : le suivi spatial rencontre les jouets connectés vintage.

## Démo vidéo

<video controls playsinline preload="metadata" muted loop style="max-width: 100%;">
  <source src="{{ '/assets/videos/nabaztag.mp4' | relative_url }}" type="video/mp4">
  Votre navigateur ne supporte pas la lecture vidéo.
</video>

## Code source

Envie de construire votre propre compagnon conscient de l'espace ? Le code Python complet est open source :

- [Voir le projet sur GitHub](https://github.com/mathemagie/lapin_cosmique)
- [Script `ear.py`](https://raw.githubusercontent.com/mathemagie/lapin_cosmique/main/ear.py)

La page interactive avec carte de suivi en direct est disponible sur [mathemagie.github.io/bidouille/lapin_cosmique/](https://mathemagie.github.io/bidouille/lapin_cosmique/).
