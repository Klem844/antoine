# Outil de gestion d'infrastructure IT - Full Cloud

Application SPA JavaScript vanilla, 100% navigateur, sans Excel ni dependance locale.

## Fonctionnalites implementees

1. Section Equipements
- CRUD complet (ajout, modification, suppression)
- Colonnes conformes au besoin
- Listes deroulantes Type, Marque, Etat
- Coloration conditionnelle des lignes par Etat
- Recherche instantanee multi-champs
- Tri sur toutes les colonnes
- Filtre par localisation
- Import / export JSON
- Import / export CSV

2. Section Topologie Reseau
- CRUD complet des liaisons
- Listes source/destination basees sur les equipements existants
- Type de liaison + debit
- Recherche et tri

3. Section Statistiques (temps reel)
- Camembert des etats
- Graphique barres par type d'equipement
- Repartition du nombre de ports par switch

4. Section Guide d'utilisation
- Instructions de saisie
- Bonnes pratiques de nommage
- Explication des champs
- Exemple de topologie
- Historique des modifications (local)

5. Export cartographie HTML autonome
- Fichier Cartographie_Reseau.html genere et telecharge automatiquement
- Ouverture dans un nouvel onglet
- CSS inline et JavaScript inline
- Aucun CDN / aucune dependance externe
- Drag & drop des noeuds
- Disposition automatique en couches reseau
- Code couleur par type
- Bordure selon etat
- Liaisons avec etiquette debit/type
- Badge VLAN sur chaque noeud
- Tooltip au survol
- Barre de recherche
- Bouton Reorganiser
- Bouton Exporter en PNG
- Legendes couleurs + types de liaison

## Dossier du projet

- index.html: shell de l'application
- src/main.js: orchestration, etat central, autosave, theme sombre
- src/styles.css: styles responsive et theme clair/sombre
- src/services/cloud.js: chargement/sauvegarde cloud REST + fallback local
- src/modules/equipements.js: section equipements
- src/modules/topologie.js: section topologie
- src/modules/statistiques.js: statistiques SVG
- src/modules/guide.js: guide + historique
- src/modules/exportCartographie.js: generation HTML autonome

## Configuration cloud

Vous pouvez connecter une API REST via une variable globale.

```html
<script>
  window.__APP_CONFIG__ = {
    apiBaseUrl: "https://your-api.example.com",
    apiKey: "optional-api-key",
    saveMethod: "PUT",
    saveStrategy: "split",
    equipementsPath: "/equipements",
    topologiePath: "/topologie",
    bundlePath: "/infra",
    useLocalFallback: true
  };
</script>
```

Notes:
- saveStrategy="split": charge/sauve equipements et topologie sur 2 endpoints
- saveStrategy="bundle": charge/sauve un objet unique { equipements, topologie }
- En cas d'indisponibilite cloud, sauvegarde locale automatique

## Demarrage

1. Ouvrir index.html directement, ou
2. Servir le dossier en statique (ex: python -m http.server 5500)

## Compatibilite / hebergement

- Navigateurs: Chrome, Edge, Firefox
- Hebergement: GitHub Pages, Netlify, Vercel, serveur interne
