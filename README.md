# Observatoire de la vie associative — Pays de la Loire

Tableau de bord web des chiffres clés de la vie associative (focus Maine-et-Loire, comparaison régionale).

**Production (cible) :** [https://observatoireVA.bb49.uk](https://observatoireVA.bb49.uk) (déploiement Coolify)

## Structure du dépôt

```
observatoireVA/
├── index.html                          # Application web (prototype)
├── PRD.md                              # Spécifications produit (v1.1)
├── README.md
├── Données Vie associative/
│   ├── structure-donnees.md            # Documentation des sources Excel
│   ├── TableauxBord_ChiffresClesAsso-Version-web_2025-12.xlsx
│   └── Tableau FLORES 2023 réalisé par Insee PDL.xlsx
└── (à venir) scripts/ public/        # ETL et site déployable — voir PRD.md
```

## Documentation

| Fichier | Contenu |
|---------|---------|
| [PRD.md](PRD.md) | Vision, exigences, déploiement GitHub + Coolify |
| [Données Vie associative/structure-donnees.md](Données%20Vie%20associative/structure-donnees.md) | Structure des onglets Excel et modèle de données |

## Développement local

Ouvrir `index.html` dans un navigateur ou servir le dossier :

```bash
npx serve .
```

## Mise à jour des données

1. Remplacer les fichiers `.xlsx` dans `Données Vie associative/`
2. Lancer le script ETL (à implémenter — voir PRD Phase 0)
3. Pousser sur `master` → déploiement Coolify

## Licence et sources

Données : RNA_waldec (data.gouv), Florès (Insee), tableaux Le Compas / DRAJES Pays de la Loire. Voir les crédits dans l’application et `structure-donnees.md`.
