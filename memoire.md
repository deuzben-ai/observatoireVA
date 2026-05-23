# Journal de bord du Projet — `memoire.md`

Ce fichier est le journal de bord et la mémoire technique du projet. Il consigne l'historique des modifications, les choix d'architecture, les décisions clés et l'état d'avancement. Il doit être **actualisé à chaque étape importante du développement**.

---

## 1. État d'avancement du Projet

**Dernière mise à jour :** 23 mai 2026

| Phase / Tâche | Statut | Description / Notes |
| :--- | :---: | :--- |
| **Phase 0 : Cadrage & Spécifications** | **Terminé** | Initialisation de la documentation et du journal de bord. |
| -- Lecture du PRD et des données | **Terminé** | Analyse de `PRD.md` et `structure-donnees.md`. |
| -- Rédaction des spécifications de Design | **Terminé** | Analyse UX/UI et création du fichier `design.md`. |
| -- Initialisation du journal de bord | **Terminé** | Création du présent fichier `memoire.md`. |
| -- Implémentation design & responsivité v1 | **Terminé** | Intégration mobile-first et thème dynamique interactif dans `index.html`. |
| **Phase 1 : Shell HTML/CSS + couche JS** | **Terminé** | Task 1 (shell), Task 2–7 (JS complet) implémentées. |
| -- Task 1 : Shell CSS + structure HTML | **Terminé** | Commit `38fd8a4` — sidebar, hero, card grid, modal. |
| -- Bug fixes (Google Fonts, sidebar-toggle) | **Terminé** | Commit `7bb44ec`. |
| -- Task 2 : Couche données JS | **Terminé** | `excelDateToStr`, `parseTableRows`, `parseIndicators` — 108 indicateurs. |
| -- Task 3 : Rendu card grid | **Terminé** | `parseVal`, `renderMiniBar`, `renderCards` — grille 3 colonnes animée. |
| -- Task 4 : Hero KPIs dept 49 | **Terminé** | `getKpiVal`, `renderHero` — 4 KPIs par thème. |
| -- Task 5 : Sidebar animée | **Terminé** | `renderSidebar`, `movePill`, `switchTheme` — pillule CSS transition. |
| -- Task 6 : Modal 4 onglets | **Terminé** | `openModal`, `switchTab`, `closeModal` — onglets conditionnels selon imgs. |
| -- Task 7 : Polish mobile + commit final | **Terminé** | Hamburger, aria-label, grid-column, shadow-card. Commit `eeb0d49`. |
| **Phase 2 : Développement Front-end & Intégration** | **Terminé** | 100% des indicateurs affichés via couche JS sur `#data-source`. |
| **Phase 3 : DevOps & Déploiement** | Non démarré | Configuration de GitHub Actions et liaison avec Coolify. |

---

## 2. Choix d'Architecture & Décisions Clés

### 2.1 Décisions Produit (Arbitrées)
*   **Accès** : 100% public, aucune authentification requise.
*   **Validation** : Pas de processus de validation institutionnelle obligatoire avant le go-live.
*   **Domaine cible** : `https://observatoireVA.bb49.uk` via Coolify.
*   **Périmètre de données** : Couverture à 100% (DATA-FULL) des deux fichiers Excel sources de décembre 2025.

### 2.2 Décisions de Design & UX (Nouveau)
*   **Thématique dynamique par département** : La couleur de focus de l'interface (logo, KPIs, graphique, accents cartographiques) s'adaptera dynamiquement en fonction du département sélectionné par l'utilisateur (ex. Rouge pour le Maine-et-Loire, Cyan pour la Loire-Atlantique, Vert pour la Sarthe, etc.).
*   **Comportement Mobile (Responsive)** : Les panneaux se replient en une seule colonne empilée verticalement sur mobile (hauteur de carte fixe), et la sidebar de navigation d'indicateurs se replie dans un menu hamburger / tiroir coulissant.

### 2.3 Choix Techniques & Infrastructure
*   **Site Statique** : Choix de servir des fichiers HTML, CSS, JS et JSON statiques (sans serveur backend dynamique en v1) pour minimiser les coûts d'hébergement et simplifier le déploiement sur Nginx/Coolify.
*   **ETL Python** : Utilisation d'un script en Python (`build_data.py`) avec `pandas` et `openpyxl` pour automatiser l'importation récurrente des fichiers Excel vers des fichiers JSON statiques.

---

## 3. Historique des Modifications

*   **23 mai 2026 (session 1)** :
    *   Lecture et analyse approfondie des fichiers markdown du projet pour l'alignement de contexte.
    *   Création de **[design.md](file:///C:/Users/ben/Desktop/observatoireVA/design.md)** (Spécifications de design dynamique et responsive).
    *   Création de **[memoire.md](file:///C:/Users/ben/Desktop/observatoireVA/memoire.md)** (Journal de bord de suivi du projet).
    *   Refonte responsive Mobile-First de **index.html** avec prévention du défilement horizontal.
    *   Implémentation du changement de département focus dynamique par clic interactif.
    *   Refonte responsive Mobile-First et correction d'encodage sur **[observatoire.html](file:///C:/Users/ben/Desktop/observatoireVA/observatoire.html)**.
    *   Intégration dynamique par JavaScript du bouton menu Hamburger, header mobile et overlay.
    *   Commit `38fd8a4` — Task 1 : shell HTML/CSS complet (sidebar, hero, card grid, modal).
*   **23 mai 2026 (session 2 — reprise après interruption Claude Code)** :
    *   Commit `7bb44ec` — fix: Google Fonts déplacé dans `<head>`, `#sidebar-toggle` sans `!important`.
    *   Implémentation complète Tasks 2–7 dans **[observatoire.html](file:///C:/Users/ben/Desktop/observatoireVA/observatoire.html)** :
        *   Task 2 : `excelDateToStr`, `parseTableRows`, `parseIndicators` — 108 indicateurs chargés depuis `#data-source`.
        *   Task 3 : `parseVal`, `renderMiniBar`, `renderCards` — grille 3 colonnes avec barres mini 5 depts.
        *   Task 4 : `getKpiVal`, `renderHero` — bandeau rouge 4 KPIs par thème (dept 49 Maine-et-Loire).
        *   Task 5 : `renderSidebar`, `movePill`, `switchTheme` — sidebar animée avec pillule CSS.
        *   Task 6 : `openModal`, `switchTab`, `closeModal` — modal 4 onglets conditionnels (bar/map/hist/tableau).
        *   Task 7 : hamburger mobile fonctionnel, `aria-label`, `grid-column:1`, `--shadow-card` appliqué, commentaire `modal-overlay[hidden]`.
    *   Commit `eeb0d49` — feat: Tasks 2-7 JS complet.
