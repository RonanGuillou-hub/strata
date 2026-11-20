# Backlog Strata

**Version 1.0, 20 novembre 2026, validée par l'utilisateur.**

Ce dossier est la source texte du backlog : la liste ordonnée de ce qu'il faut construire. Il découle du cahier des charges (version 0.19), dont il reprend les identifiants : EF pour les exigences fonctionnelles, RG pour les règles de gestion, ENF pour les exigences non fonctionnelles, DT pour les décisions techniques. Le document Word du backlog, rangé dans `iFastLearn/docs/`, est généré à partir de ces fichiers.

## Fichiers

| Fichier | Épic | Contenu |
|---|---|---|
| [0-socle-technique.md](0-socle-technique.md) | 0. Socle technique | T-01 à T-09 : environnement, tests, base, intégration continue, spikes |
| [A-preparer-un-module.md](A-preparer-un-module.md) | A. Préparer un module | US-01 à US-06 |
| [B-verifier-les-cartes.md](B-verifier-les-cartes.md) | B. Vérifier les cartes | US-07 à US-10 |
| [C-reviser.md](C-reviser.md) | C. Réviser | US-11 à US-16 |
| [D-suivre-la-progression.md](D-suivre-la-progression.md) | D. Suivre la progression | US-17 à US-20 |
| [E-regler-l-application.md](E-regler-l-application.md) | E. Régler l'application | US-21 et US-22 |

## Ordre de livraison

| Ordre | Contenu | Résultat |
|---|---|---|
| 1. Socle | T-01 à T-07, puis T-09 | L'application vide tourne sur le téléphone, les tests passent à chaque envoi sur GitHub, et les trois incertitudes sont levées : OneDrive, PDF, consigne. |
| 2. Tranche 1 : parcours minimal | US-01, US-02, US-21, US-03, US-05, US-07, US-10, T-08, US-11, US-12, US-13, US-15, US-17 | On prépare un module, on vérifie ses cartes, on les révise, et on voit la rétention monter. |
| 3. Tranche 2 : confort et pilotage | US-04, US-06, US-08, US-09, US-14, US-16, US-18, US-19, US-20, US-22 | Ajouts autour du parcours : corriger ses choix, consulter, piloter la progression. |

Dans la tranche 1, l'ordre suit les dépendances : il faut un cours pour créer un module, une clé d'accès pour générer, des cartes validées pour réviser. T-08 (FSRS) se place juste avant l'épic C, où il sert pour la première fois.

## Format d'une story

```
## US-12 Répondre à un QCM
Épic C · Tranche 1 · Taille S · Statut : à faire
Exigences : EF-15 · Règles : RG-27, RG-30, RG-31 · Écran : 5. Séance · Dépend de : US-11, T-08

En tant qu'apprenant, je veux …, afin de …

Critères d'acceptation
1. Étant donné …, quand …, alors …
```

- **Rôles.** On dit « auteur » quand on prépare un module ou qu'on vérifie les cartes, « apprenant » quand on révise ou qu'on suit sa progression. C'est la même personne, dans deux rôles.
- **Tests.** Chaque critère d'acceptation porte un numéro (CA-1, CA-2…). Le test automatique qui le couvre reprend la référence dans son nom, par exemple `US-12 CA-2`. On retrouve ainsi le test d'un critère, et le critère d'un test.
- **Taille.** La taille compare les stories entre elles ; ce n'est pas une durée.
  - **S** : un seul écran ou une règle simple.
  - **M** : plusieurs règles, ou un écran qui change d'état.
  - **L** : un service extérieur, ou plusieurs écrans.
- **Statut.** Trois valeurs : à faire, en cours, terminée.
- **Stories techniques (épic 0).** Elles s'écrivent avec un objectif et des critères vérifiables, sans « En tant que… » : elles n'apportent rien de visible à l'utilisateur.

## Prête et terminée

Une story est **prête** (elle peut entrer dans un sprint) quand :
- elle renvoie à au moins une exigence du cahier des charges, ou à une décision technique ;
- ses critères d'acceptation sont écrits et vérifiables ;
- sa taille est estimée ;
- les stories dont elle dépend sont terminées.

Une story est **terminée** quand :
- chaque critère d'acceptation est couvert par au moins un test automatique, et tous les tests passent dans l'intégration continue ;
- elle respecte les exigences non fonctionnelles qui la concernent (fonctionnement sans internet, aucune perte, réactivité…) ;
- l'utilisateur l'a essayée sur le téléphone et l'a acceptée ;
- son statut est à jour dans ce backlog.

## Points ouverts et décisions

PO-01, PO-04, PO-05 et PO-06 ont été tranchés le 20 novembre 2026 : la proposition est retenue.

| Réf. | Question | Proposition |
|---|---|---|
| PO-01 | Quelle note FSRS reçoit un QCM faux ? Le cahier des charges ne fixe que le QCM juste (« bien »). | « à revoir » (Again), la note la plus basse. À ajouter au cahier des charges (RG-28 et DT-09). |
| PO-02 | Quelle bibliothèque pour SQLite (accès direct, ou bibliothèque qui génère le code d'accès) ? | À trancher dans T-04 et à consigner en DT-15. |
| PO-03 | Les tests de bout en bout ont besoin du téléphone : ils ne peuvent pas tourner dans l'intégration continue. | Les lancer à la main avant de déclarer une story terminée. |
| PO-04 | Qu'est-ce qu'une carte « réussie » dans le bilan de séance (EF-20) ? Le cahier des charges ne le dit pas. | Toute carte notée autre chose que « à revoir » (US-16). |
| PO-05 | Le prochain cap affiché sur l'accueil (EF-22) : le déblocage du suivant se mesure-t-il par rapport à 50 % ? | Oui : cap = 50 % tant que le suivant est bloqué, puis 80 % (US-18). |
| PO-06 | Le prototype de consigne (DT-08) manquait dans la liste des stories techniques annoncée. | Ajouté en T-09, avant US-05. |

## Lexique

| Terme | Définition |
|---|---|
| Backlog | Liste ordonnée de tout ce qu'il faut construire, tenue à jour pendant le projet. |
| Épic | Ensemble de stories qui portent une même grande fonction. |
| User story (story) | Besoin exprimé du point de vue de l'utilisateur : « En tant que…, je veux…, afin de… ». |
| Story technique | Travail nécessaire au développement mais invisible pour l'utilisateur, décrit par un objectif et des critères vérifiables. |
| Critère d'acceptation | Condition vérifiable qu'une story doit remplir pour être acceptée, écrite « Étant donné… quand… alors… ». |
| Tranche | Ensemble de stories qui, livrées ensemble, forment un parcours utilisable de bout en bout. |
| Taille | Estimation relative de l'effort d'une story (S, M, L), qui permet de les comparer. |
| Spike | Investigation technique courte et limitée dans le temps, qui répond à une question précise pour réduire une incertitude ; elle livre une réponse, pas une fonction. |
| Squelette qui marche | Première version minimale de l'application qui fonctionne de bout en bout, sur laquelle on ajoute les fonctions une par une. |
| Intégration continue | Lancement automatique de tous les tests à chaque envoi de code sur GitHub. |
| Test unitaire | Test d'une règle ou d'un calcul isolé, sans écran ni téléphone. |
| Test d'écran | Test d'un écran simulé : on vérifie ce qu'il affiche et sa réaction aux gestes, sans téléphone. |
| Test de bout en bout | Test qui fait tourner la vraie application sur le téléphone et parcourt plusieurs écrans. |
| Débogage sans fil | Liaison Wi-Fi entre le PC et le téléphone, qui permet d'installer et de suivre l'application sans câble. |
