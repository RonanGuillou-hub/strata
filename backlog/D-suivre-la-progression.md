# Épic D. Suivre la progression

Cahier des charges, section 3.4. Exigences EF-21 à EF-24, règles RG-34 à RG-41. Écrans 1 (Accueil), 2 (Modules du cours), 6 (Fin de séance) et 7 (Progression).

---

## US-17 Voir l'état et la rétention de chaque module
Épic D · Tranche 1 · Taille L
Exigences : EF-21 · Règles : RG-23, RG-34 à RG-41 · Écran : 2. Modules du cours · Dépend de : US-12, US-13

En tant qu'apprenant, je veux voir l'état et la rétention de chaque module, afin de savoir ce que je retiens vraiment et ce qui se débloque.

**Critères d'acceptation**
1. Étant donné une carte dont la prochaine révision est prévue dans 21 jours ou plus, quand on calcule la rétention, alors elle compte comme retenue durablement (RG-34).
2. Étant donné 30 QCM et 40 questions ouvertes, dont 20 et 24 retenues durablement, quand on calcule la rétention du module, alors elle vaut 64 % : les QCM comptent double, et les cartes jamais vues comptent dans le total (RG-35).
3. Étant donné une carte révisée, quand sa note est enregistrée, alors la rétention de son module est recalculée (RG-36).
4. Étant donné un module débloqué qui atteint 50 % de rétention, quand la rétention est recalculée, alors le module suivant est débloqué, définitivement (RG-39).
5. Étant donné un module dont toutes les cartes ont été vues au moins une fois, quand sa rétention atteint 80 %, alors il devient maîtrisé (RG-37).
6. Étant donné un module maîtrisé, quand sa rétention passe sous 70 %, alors il devient « à consolider ». Il redevient maîtrisé quand il remonte à 80 %, pas avant (RG-38).
7. Étant donné un module « sans carte », quand la liste s'affiche, alors il n'a pas de rétention, et le module suivant est débloqué dès que lui-même l'est (RG-23).
8. Étant donné un changement d'état, quand il se produit, alors il est enregistré dans le journal des changements d'état, avec la séance pendant laquelle il a eu lieu.
9. Étant donné la liste des modules, quand elle s'affiche, alors chaque module montre son état de préparation, son état de progression et sa rétention.

---

## US-18 Voir les cartes du jour et le prochain cap sur l'accueil
Épic D · Tranche 2 · Taille M
Exigences : EF-22 · Règles : RG-25, RG-37, RG-39 · Écran : 1. Accueil · Dépend de : US-11, US-17

En tant qu'apprenant, je veux voir sur l'accueil, pour chaque cours, ce qui m'attend aujourd'hui et mon prochain cap, afin d'avoir envie de lancer la séance.

**Critères d'acceptation**
1. Étant donné un cours, quand l'accueil s'affiche, alors il indique les cartes du jour, en séparant les cartes à revoir et les cartes nouvelles (par exemple « 17 cartes : 9 à revoir, 8 nouvelles »).
2. Étant donné plusieurs modules débloqués, quand l'accueil s'affiche, alors il nomme le module le plus proche de son prochain cap, avec l'écart restant (par exemple « Module 3 : 72 %, encore 8 points pour le maîtriser »).
3. Étant donné un module dont le prochain cap est le déblocage du suivant, quand il est le plus proche, alors l'écart est donné par rapport à 50 %.
4. Étant donné une séance terminée, quand je reviens à l'accueil, alors les chiffres sont à jour.

---

## US-19 Voir le tableau de progression du cours
Épic D · Tranche 2 · Taille M
Exigences : EF-23 · Règles : RG-22, RG-33 · Critères de réussite : C1, C2 · Écran : 7. Progression · Dépend de : US-17

En tant qu'apprenant, je veux voir un tableau de progression du cours, afin de lire d'un coup d'œil où j'en suis par rapport aux deux critères de réussite.

**Critères d'acceptation**
1. Étant donné un cours, quand j'ouvre le tableau, alors chaque module montre son état, sa rétention et ses cartes vues sur le total (par exemple « 18 sur 26 »).
2. Étant donné un cours avec 12 séances comptées, quand j'ouvre le tableau, alors il indique « 12 séances sur 30 » (C1).
3. Étant donné des modules validés, quand j'ouvre le tableau, alors il indique la fiabilité des cartes du cours, cartes acceptées ÷ cartes vérifiées (C2), et le nombre de cartes vérifiées.
4. Étant donné le téléphone sans connexion, quand j'ouvre le tableau, alors il s'affiche (ENF-01).

---

## US-20 Être prévenu des changements d'état des modules
Épic D · Tranche 2 · Taille S
Exigences : EF-24 · Règles : RG-37 à RG-39 · Écrans : 5. Séance, 6. Fin de séance · Dépend de : US-17

En tant qu'apprenant, je veux être prévenu quand un module est débloqué, devient maîtrisé ou passe « à consolider », afin de voir mes progrès au moment où ils arrivent.

**Critères d'acceptation**
1. Étant donné une carte révisée qui fait débloquer le module suivant, quand la rétention est recalculée, alors un message s'affiche dans l'application (par exemple « Module 2 débloqué »).
2. Étant donné un module qui devient maîtrisé, ou qui passe « à consolider », quand la rétention est recalculée, alors un message l'annonce.
3. Étant donné un message affiché, quand je continue la séance, alors il ne m'interrompt pas : il disparaît seul ou d'un geste.

Les messages sont internes à l'application ; il n'y a pas de notification du téléphone.
