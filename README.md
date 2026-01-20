# Le Globule - Exercice 1 Display

Projet HTML/CSS avancé présentant un site web sur les globules avec deux versions distinctes pour différents environnements de déploiement.

## 🌐 Liens de démonstration

- **Portfolio** : https://portfolio.clairtyx.com
- **Démo en ligne** : https://html-avancer-1-devoir-exercice-1.clairtyx.com

## 📁 Structure du projet

Ce projet contient deux versions distinctes du site :

### `/docs` - Version GitHub Pages (Production)
Version complète et responsive avec toutes les fonctionnalités modernes :
- **Navigation responsive** avec menu hamburger pour mobile
- **JavaScript interactif** (`/scripts/sheet.js`) pour le comportement dynamique
- **Flexbox et Grid CSS** pour une mise en page moderne et adaptative
- **Classes utilitaires** inspirées de Tailwind CSS
- **Support mobile optimisé** avec breakpoints et drawer navigation
- Structure complète avec toutes les pages de navigation (choix, contacts, triangles)

**Déploiement** : Cette version est déployée automatiquement via GitHub Pages et utilisée dans mon portfolio professionnel.

### `/site` - Version Docker (Développement local)
Version simplifiée utilisant principalement des techniques CSS classiques :
- **Mise en page traditionnelle** avec `display: table-cell`
- **Navigation desktop uniquement** sans fonctionnalités mobiles
- **CSS pur** sans JavaScript interactif
- **Menus déroulants** utilisant `:hover` et `position: absolute`
- Structure allégée pour les tests locaux rapides

**Déploiement** : Cette version fonctionne avec Docker Compose via Apache (httpd:alpine) sur le port 3001.

## 🎨 Différences techniques majeures

### CSS et mise en page

#### Version `/docs`
```css
/* Utilise Flexbox et Grid massivement */
.flex { display: flex; }
.grid { display: grid; }
.cols-2 { display: grid; grid-template-columns: repeat(2, 1fr); }

/* Classes utilitaires modernes */
.items-center { align-items: center; }
.justify-between { justify-content: space-between; }
.gap-2 { gap: 0.5rem; }

/* Responsive avec breakpoints */
@media (min-width: 768px) {
    .md:flex-row { flex-direction: row; }
    .md:hidden { display: none; }
}
```

**Fichier CSS** : ~1260 lignes avec système complet de classes utilitaires

#### Version `/site`
```css
/* Utilise des techniques classiques */
.table-layout { display: table; }
.table-cell-layout { display: table-cell; }
.inline-block-top { display: inline-block; vertical-align: top; }

/* Positionnement traditionnel */
.submenu-content { position: absolute; }
.cols-2 { /* colonnes via inline-block */ }
```

**Fichier CSS** : ~837 lignes avec approches traditionnelles

### HTML et structure

#### Version `/docs`
- **447 lignes** avec navigation complète mobile/desktop
- Menu hamburger avec overlay et drawer
- JavaScript pour interactions (toggle menu, gestion états)
- Meta viewport et responsive design
- Attributs aria pour l'accessibilité
- Structure sémantique moderne

#### Version `/site`
- **302 lignes** avec navigation desktop uniquement
- Menu statique simplifié
- Pas de JavaScript
- Pas d'optimisation mobile
- Structure traditionnelle

## 🔧 Pourquoi Flexbox et Grid ?

### Dominance dans le développement moderne

**Flexbox** et **Grid** sont devenus les standards de mise en page CSS pour plusieurs raisons :

1. **Alignement puissant** : Centrage vertical/horizontal trivial
2. **Responsive naturel** : Adaptation automatique aux conteneurs
3. **Maintenabilité** : Code plus lisible et prévisible
4. **Performance** : Rendu optimisé par les navigateurs modernes

### Tailwind CSS : La référence qui guide les bonnes pratiques

**Tailwind CSS** est aujourd'hui **LA référence incontournable** dans le domaine du CSS moderne et des frameworks utilitaires. Utilisé par des millions de développeurs et adopté par les plus grandes entreprises tech, Tailwind dicte les bonnes pratiques en matière de mise en page web.

**Le constat révélateur** : Bien que Tailwind propose techniquement les classes `table` et `table-cell` (pour compatibilité avec tous les cas d'usage possibles), **leur documentation et leurs exemples ne les utilisent pratiquement jamais (1 seule foix dans la doc https://tailwindcss.com/docs/display#table)**. 

```css
/* ⚠️ Classes présentes mais rarement utilisées/recommandées */
.table { display: table; }
.table-cell { display: table-cell; }

/* ✅ Classes massivement utilisées et documentées par Tailwind */
.flex { display: flex; }
.flex-col { flex-direction: column; }
.items-center { align-items: center; }
.justify-between { justify-content: space-between; }
.grid { display: grid; }
.grid-cols-2 { grid-template-columns: repeat(2, minmax(0, 1fr)); }
```

### Pourquoi Flexbox et Grid dominent

La documentation officielle de Tailwind et les ressources de la communauté montrent une préférence écrasante pour Flexbox et Grid :

- **Tutoriels et exemples** : 95%+ utilisent Flexbox/Grid
- **Composants officiels** : Tous les layouts modernes sont construits avec Flexbox/Grid
- **Best practices** : Tailwind recommande Flexbox pour les layouts 1D et Grid pour les layouts 2D
- **Tables HTML** : Même pour les tableaux, Tailwind encourage l'usage de vraies balises `<table>` plutôt que `display: table` en CSS

Les propriétés `display: table` et `display: table-cell` sont des **vestiges d'une époque révolue** (pré-Flexbox), conservées uniquement pour :
- La compatibilité avec du code legacy
- Des cas d'usage très spécifiques et rares
- Permettre aux développeurs de migrer progressivement

### Philosophie adoptée dans ce projet

La version `/docs` suit les **meilleures pratiques modernes** recommandées par Tailwind, utilisant massivement Flexbox et Grid pour :
- **Composition rapide** de layouts complexes sans CSS personnalisé
- **Cohérence visuelle** dans tout le projet grâce aux utilitaires
- **Prototypage rapide** directement dans le HTML
- **Code moderne** aligné avec les standards actuels de l'industrie

La version `/site` avec ses `table-layout` et `table-cell-layout` représente une approche **pré-2017** (avant l'adoption massive de Grid), conservée uniquement pour illustrer l'évolution des techniques CSS.

## 🚀 Déploiement

### Version locale avec Docker

```bash
# Lancer le serveur Apache
docker compose up -d

# Accéder au site
open http://localhost:3001

# Arrêter le serveur
docker compose down
```

Le fichier `docker-compose.yaml` configure :
- **Image** : `httpd:alpine` (serveur Apache léger)
- **Port** : 3001:80 (évite les conflits avec d'autres services)
- **Volumes** : Monte `/site` en lecture seule dans Apache
- **Configuration** : Utilise `apache.conf` personnalisé
- **Network** : Bridge pour isolation

### Version production avec GitHub Pages

La version `/docs` est déployée automatiquement :
1. Push sur la branche `main`
2. GitHub Pages sert le contenu du dossier `/docs`
3. Accessible via le domaine personnalisé configuré dans `CNAME`

## 📝 Pourquoi deux versions ?

### Raison 1 : Environnements différents
- **Docker/Local** : Tests rapides, pas besoin de responsive
- **GitHub Pages/Production** : Expérience utilisateur complète

### Raison 2 : Portfolio professionnel
La version `/docs` est intégrée dans mon portfolio (https://portfolio.clairtyx.com) pour démontrer :
- Maîtrise des techniques CSS modernes
- Développement responsive
- Utilisation de Flexbox/Grid
- Intégration JavaScript
- Accessibilité web

### Raison 3 : Séparation des préoccupations
- **Développement** : Itération rapide avec Docker
- **Production** : Version optimisée et complète pour les visiteurs

## 🛠 Technologies utilisées

- **HTML5** : Structure sémantique
- **CSS3** : Variables CSS, Flexbox, Grid, animations
- **JavaScript (ES6+)** : Modules, manipulation DOM (version `/docs`)
- **Docker** : Conteneurisation Apache
- **GitHub Pages** : Hébergement statique
- **Apache httpd** : Serveur web pour la version locale

## 📦 Contenu du projet

- `docs/` : Version production (GitHub Pages)
- `site/` : Version développement (Docker)
- `docker-compose.yaml` : Configuration Docker
- `apache.conf` : Configuration Apache personnalisée
- `LICENSE` : Licence du projet
- `CNAME` : Configuration domaine personnalisé

---

**Auteur** : clairtyx  
**Projet** : HTML Avancé 1 - Exercice 1  
**Date** : 2026