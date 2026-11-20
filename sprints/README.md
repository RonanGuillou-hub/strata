# Sprints Strata

Le suivi des sprints est dans le classeur **`Strata - sprints.xlsx`** :

- **Kanban** : vision globale, une bande par épic et une colonne par état (à faire, en cours, en revue, terminée) ; on peut filtrer sur un sprint.
- **Backlog** : rappel des 31 stories ; la colonne Sprint se modifie ici, la colonne État est lue dans la feuille du sprint.
- **Sprint 0 à Sprint 5** : une story par ligne avec son état ; en bas, la revue et la rétrospective.

Le contenu des stories (story, critères d'acceptation) est dans [`../backlog/`](../backlog/), qui fait foi. Le classeur fait foi pour le sprint et l'état.

Le classeur est régénéré par `outils/build_sprints.py` du projet iFastLearn, qui conserve ce qui a été saisi et vérifie que chaque story vient après celles dont elle dépend. Fermer le classeur avant de le régénérer.

| Sprint | Objectif | Points |
|---|---|---|
| 0. Socle | Squelette qui marche ; import OneDrive et lecture des PDF tranchés | 8 |
| 1. Préparer | Cours, modules, clé d'accès ; base de données ; consigne réglée | 9 |
| 2. Générer et vérifier | Ressource, génération, vérification, validation du module | 10 |
| 3. Réviser | Séance et rétention : fin de la tranche 1 | 10 |
| 4. Corriger et consulter | Retirer, annuler, liste des cartes, section, bilan, plafond | 7 |
| 5. Piloter | Rejets et doublons, accueil, tableau de progression, messages | 7 |

Sprints d'une semaine, à ajuster selon la vitesse mesurée (points terminés par sprint). Points : S = 1, M = 2, L = 3.
