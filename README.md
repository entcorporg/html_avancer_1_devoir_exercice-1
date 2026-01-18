# Le Globule - Exercice 1

## Description

Site web éducatif présentant des informations détaillées sur les globules et leurs caractéristiques scientifiques. Ce projet utilise HTML, CSS et JavaScript pour créer une expérience interactive.

## Structure du projet

```
exercice-1/
├── apache.conf          # Configuration Apache
├── docker-compose.yaml  # Configuration Docker
└── site/
    ├── index.html       # Page d'accueil
    ├── 404.html         # Page d'erreur
    ├── contacts/        # Section contacts
    ├── choix/           # Sections de choix (1-3)
    ├── triangle/        # Sections triangle
    ├── surtriangle/     # Sections surtriangle
    ├── css/             # Feuilles de style
    ├── scripts/         # Scripts JavaScript
    └── img/             # Images
```

## Technologies utilisées

- HTML5
- CSS3 (avec classes utilitaires)
- JavaScript (modules ES6)
- Docker & Docker Compose
- Apache HTTP Server

## Installation et démarrage

### Avec Docker (recommandé)

```bash
# Démarrer le conteneur
docker compose up -d

# Arrêter le conteneur
docker compose down
```

Le site sera accessible sur le port configuré dans `docker-compose.yaml`.

### Sans Docker

Servez le contenu du dossier `site/` avec n'importe quel serveur web (Apache, Nginx, etc.).

## Fonctionnalités

- Navigation interactive
- Sections multiples avec sous-navigation
- Design responsive
- Page d'erreur 404 personnalisée
- Interface moderne avec animations

## Auteur

**entcorporg**

## Licence

Ce projet est sous licence MIT. Voir le fichier [LICENSE](LICENSE) pour plus de détails.
