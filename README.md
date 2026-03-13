# Site web Bitcoin Alsace

Site statique de l'association [Bitcoin Alsace](https://bitcoinalsace.fr), développé avec [Astro](https://astro.build).

## Stack

- **Framework :** [Astro](https://astro.build) (site statique, zéro JS par défaut)
- **Contenu des événements :** Markdown (dans `src/content/events/`)
- **Styles :** CSS natif (pas de framework CSS)
- **RSS :** généré automatiquement via `@astrojs/rss`

## Ajouter ou modifier un événement

Les événements sont des fichiers Markdown dans `src/content/events/`. Toute personne ayant accès au dépôt Git peut en ajouter ou en modifier.

### Format d'un fichier événement

Nommez le fichier `AAAA-MM-slug.md` dans `src/content/events/`, par exemple `2026-04-mon-evenement.md` :

```markdown
---
title: "Mon événement Bitcoin"
date: 2026-04-08              # date seule, ou avec heure : 2026-04-08 19:30
# endDate: 2026-04-09         # optionnel — pour les événements sur plusieurs jours
category: meetup              # meetup | conference | actu | autre
description: "Courte description affichée dans les cartes d'événement."
location: "Strasbourg"        # optionnel
image: "/images/events/mon-evenement.webp"  # optionnel — chemin depuis /public/
eventUrl: "https://t.me/+xyz" # optionnel — lien bouton en bas de la page
urlText: "S'inscrire"         # optionnel — texte du bouton (défaut : "Rejoignez-nous sur Telegram")
free: true                    # true par défaut
# price: 25                   # optionnel — si free: false
draft: false                  # true = non publié
---

## Contenu complet de l'événement

Écrivez ici le détail de l'événement en Markdown.
```

### Champs disponibles

| Champ | Type | Requis | Description |
|-------|------|--------|-------------|
| `title` | texte | oui | Titre de l'événement |
| `date` | date | oui | Date (et heure optionnelle) de début : `2026-04-08` ou `2026-04-08 19:30` |
| `endDate` | date | non | Date (et heure optionnelle) de fin |
| `category` | enum | non | `meetup`, `conference`, `actu` ou `autre` (défaut : `autre`) |
| `description` | texte | non | Résumé court affiché dans les cartes et le SEO |
| `location` | texte | non | Lieu de l'événement |
| `image` | chemin | non | Image de couverture, depuis `/public/` (ex : `/images/events/foo.webp`) |
| `eventUrl` | URL | non | Lien du bouton d'action en bas de page |
| `urlText` | texte | non | Texte du bouton (défaut : `Rejoignez-nous sur Telegram`) |
| `free` | booléen | non | Entrée gratuite ? (défaut : `true`) |
| `price` | nombre | non | Prix en euros si `free: false` |
| `draft` | booléen | non | `true` = non publié (défaut : `false`) |

### Catégories disponibles

| Valeur | Affichage |
|--------|-----------|
| `meetup` | 🤝 Bitcoin Meetup |
| `conference` | 🗣️ Conférence |
| `actu` | 🎭 Actualité |
| `autre` | 📅 Événement |

### Workflow Git

1. Clonez le dépôt ou créez une branche
2. Ajoutez votre fichier Markdown dans `src/content/events/`
3. Ouvrez une Pull Request
4. Une fois mergée, le site se reconstruit automatiquement

## Développement local

```sh
npm install
npm run dev       # http://localhost:4321
npm run build     # build de production dans ./dist/
npm run preview   # prévisualisation du build
```


## Licence

Voir [LICENSE](./LICENSE).
