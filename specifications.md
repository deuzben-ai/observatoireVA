# Spécifications Fonctionnelles et Techniques

## 1. Description Fonctionnelle
L'**Observatoire de la vie associative — Pays de la Loire** est une application web monopage (SPA) interactive. Elle permet de visualiser et d'analyser les indicateurs clés de la vie associative de la région Pays de la Loire et de ses 5 départements :
- Loire-Atlantique (44)
- Maine-et-Loire (49)
- Mayenne (53)
- Sarthe (72)
- Vendée (85)

### Fonctionnalités principales :
- **Navigation thématique** : Filtrage des indicateurs selon 5 grandes thématiques :
  - Démographie associative (16 indicateurs)
  - Emploi — tableau de bord (14 indicateurs)
  - Compléments par objet (33 indicateurs)
  - Aires urbaines et ZRR (32 indicateurs)
  - Emploi — Florès 2023 (13 indicateurs)
- **Focus Géographique Interactif** : L'utilisateur peut changer le territoire actif (Région Pays de la Loire ou l'un des 5 départements). Ce changement adapte dynamiquement la palette de couleurs de l'interface, met en valeur le territoire sélectionné sur les graphiques miniatures, et ajuste les KPIs affichés dans le bandeau supérieur.
- **Visualisation Détaillée (Modal)** : Cliquer sur un indicateur ouvre une modal contenant :
  - Un onglet **Graphique** (diagramme en barres généré par R).
  - Un onglet **Carte** interactive avec des hotspots permettant de cliquer directement sur un département pour changer le focus géographique, accompagnée d'une légende dynamique.
  - Un onglet **Historique** (graphique chronologique ou de distribution).
  - Les métadonnées de l'indicateur (Source, Date de mise à jour, Notes méthodologiques).

---

## 2. Architecture Technique
L'application est construite sous forme de fichier HTML unique intégrant la structure, le style CSS et la logique Javascript (Vanilla JS).

### Structure du projet :
```
├── index.html            # Fichier principal contenant la structure, le style et le JS
└── assets/               # Ressources statiques
    ├── logo.png          # Logo officiel du projet
    └── figures/          # Graphiques (.png) générés par R pour chaque indicateur
```

### Mécanisme de chargement des données :
Les données de l'ensemble des indicateurs sont stockées directement dans le DOM HTML sous forme de structure sémantique cachée (dans un conteneur `#data-source`). Au chargement de la page (`DOMContentLoaded`), la fonction `parseIndicators()` extrait ces données en parcourant les balises HTML et les tableaux pour alimenter un tableau d'objets Javascript. Cette approche évite des appels réseau AJAX/Fetch pour charger les indicateurs.

---

## 3. Choix Technologiques
- **Langages** : HTML5, CSS3, Javascript ES6 (Vanilla / sans framework externe).
- **Polices** : Google Fonts (`DM Sans` pour le corps du texte, `Outfit` pour les titres et badges).
- **Graphiques et Cartographie** : R (génération des figures statiques pré-enregistrées dans `assets/figures/`), complété par des overlays HTML/CSS interactifs (hotspots sur la carte).

---

## 4. Règles Métiers
- **Filtres de focus** :
  - "Région" affiche le total agrégé pour la région Pays de la Loire.
  - "Département (44, 49, 53, 72, 85)" applique les couleurs spécifiques du département aux barres et aux bordures de focus.
- **Zéro de référence (Mini-bars)** : Les graphiques miniatures de barres dans les cartes d'indicateurs gèrent le positionnement du zéro dynamiquement (pour les indicateurs à valeurs négatives).
- **Date Excel** : Les numéros de série de dates d'Excel (ex: 45689) sont convertis au format de date lisible français `DD/MM/YYYY`.

---

## 5. Contraintes du projet
- **Zéro dépendance JS** : Pas de bibliothèques externes lourdes de cartographie ou de graphes (comme Leaflet ou Chart.js), toute l'interactivité repose sur le CSS et Vanilla JS pour des performances maximales et un chargement instantané.
- **Responsive Web Design** : L'interface doit être utilisable sur mobile (menu tiroir latéral pour la navigation, adaptation de la grille d'indicateurs de 3 colonnes à 1 colonne sur les petits écrans).
