# Épic C. Réviser

Cahier des charges, section 3.3. Exigences EF-14 à EF-20, règles RG-24 à RG-33. Écrans 1 (Accueil), 5 (Séance) et 6 (Fin de séance). La story technique T-08 (FSRS) doit être terminée avant cet épic.

---

## US-11 Lancer une séance sur un cours
Épic C · Tranche 1 · Taille M
Exigences : EF-14, ENF-01 · Règles : RG-24 à RG-26, RG-40 · Écran : 1. Accueil · Dépend de : US-10, T-08

En tant qu'apprenant, je veux lancer une séance de révision sur un cours, afin de réviser les cartes du jour.

**Critères d'acceptation**
1. Étant donné un cours avec des cartes actives dans des modules débloqués, quand j'appuie sur « Réviser », alors une séance commence sur ce cours seulement (RG-24).
2. Étant donné 15 cartes à revoir et 20 cartes nouvelles, quand la série du jour est composée, alors elle contient d'abord les 15 cartes à revoir, puis 5 cartes nouvelles : 20 cartes au plus en tout (RG-25).
3. Étant donné 3 cartes à revoir et 30 cartes nouvelles, quand la série du jour est composée, alors elle contient les 3 cartes à revoir et 10 cartes nouvelles, pas plus (RG-25).
4. Étant donné une séance commencée, quand un module est débloqué pendant la séance, alors la série n'est pas recomposée : ses cartes entreront dans la série du lendemain (RG-26, RG-40).
5. Étant donné un cours sans module validé et débloqué, quand j'appuie sur « Réviser », alors la séance ne commence pas, et l'application explique pourquoi.
6. Étant donné un cours sans carte à revoir ni carte nouvelle aujourd'hui, quand j'appuie sur « Réviser », alors l'application l'indique, avec la date de la prochaine révision prévue.
7. Étant donné le téléphone sans connexion, quand je lance une séance, alors elle fonctionne (ENF-01).

---

## US-12 Répondre à un QCM
Épic C · Tranche 1 · Taille S
Exigences : EF-15 · Règles : RG-27, RG-29 à RG-31 · Écran : 5. Séance · Dépend de : US-11, T-08

En tant qu'apprenant, je veux choisir une réponse à un QCM puis voir la correction, afin de savoir tout de suite si je connais la réponse.

**Critères d'acceptation**
1. Étant donné une carte QCM affichée, tant que je n'ai rien choisi, alors la bonne réponse reste cachée.
2. Étant donné une carte QCM, quand je choisis la bonne proposition, alors l'application l'indique, et la révision est enregistrée avec la note « bien », jugée par l'application.
3. Étant donné une carte QCM, quand je choisis une mauvaise proposition, alors la correction montre la bonne réponse et la mienne, et la révision est enregistrée avec la note « à revoir » (point ouvert PO-01).
4. Étant donné une carte ratée, quand la séance continue, alors cette carte ne revient pas dans la même séance (RG-30).
5. Étant donné une révision enregistrée, quand on la consulte, alors elle porte sa date, son résultat, sa durée et l'indication « jugée par l'application » (RG-31).

---

## US-13 Répondre à une question ouverte et se noter
Épic C · Tranche 1 · Taille S
Exigences : EF-16, ENF-05 · Règles : RG-27 à RG-31 · Écran : 5. Séance · Dépend de : US-11, T-08

En tant qu'apprenant, je veux réfléchir à ma réponse, révéler la bonne réponse et juger moi-même si je la connaissais, afin de réviser les notions qui ne se corrigent pas automatiquement.

**Critères d'acceptation**
1. Étant donné une question ouverte affichée, tant que je n'ai pas appuyé sur « Révéler la réponse », alors la réponse reste cachée.
2. Étant donné la réponse révélée, quand l'écran s'affiche, alors quatre niveaux sont proposés, de ★ à ★★★★, chacun avec sa définition (RG-28).
3. Étant donné la réponse révélée, quand je choisis un niveau, alors la révision est enregistrée avec la note correspondante (★ → à revoir, ★★ → difficile, ★★★ → bien, ★★★★ → facile), et l'indication « jugée par l'apprenant ».
4. Étant donné une carte notée ★, quand la séance continue, alors cette carte ne revient pas dans la même séance (RG-30).
5. Étant donné le téléphone tenu d'une main, quand je choisis un niveau, alors les quatre boutons sont à portée de pouce (ENF-05).

---

## US-14 Voir la section d'origine d'une carte
Épic C · Tranche 2 · Taille S
Exigences : EF-17 · Règles : RG-07 · Écran : 5. Séance · Dépend de : US-12, US-13

En tant qu'apprenant, je veux voir la section de la ressource d'où vient une carte, une fois la réponse révélée, afin de relire le passage du cours quand je me suis trompé.

**Critères d'acceptation**
1. Étant donné la réponse révélée ou la correction affichée, quand j'appuie sur « Voir la section », alors le texte de la section d'origine s'affiche.
2. Étant donné une carte dont la réponse est encore cachée, quand je regarde l'écran, alors le bouton « Voir la section » n'apparaît pas.
3. Étant donné la section affichée, quand je la ferme, alors je reviens à la carte, là où j'en étais.

---

## US-15 Suivre l'avancement, interrompre et terminer une séance
Épic C · Tranche 1 · Taille M
Exigences : EF-18, EF-19, ENF-03, ENF-04 · Règles : RG-26, RG-32, RG-33 · Décisions : DT-10 · Écran : 5. Séance · Dépend de : US-12, US-13

En tant qu'apprenant, je veux voir où j'en suis et pouvoir m'arrêter entre deux cartes, afin de réviser au rythme de ma journée.

**Critères d'acceptation**
1. Étant donné une séance en cours, quand une carte s'affiche, alors l'avancement s'affiche aussi (par exemple « carte 5 sur 20 »).
2. Étant donné une carte notée, quand je passe à la suivante, alors elle s'affiche en moins d'une seconde (ENF-04).
3. Étant donné une séance en cours, quand j'appuie sur « Arrêter » entre deux cartes, alors la séance s'arrête, et les cartes déjà révisées restent enregistrées.
4. Étant donné 20 cartes révisées, ou une série épuisée, quand la dernière carte est notée, alors la séance se termine, et sa durée est enregistrée (RG-32).
5. Étant donné une séance interrompue après au moins une carte révisée, quand on compte les séances, alors elle compte pour C1. Ses cartes non vues restent à revoir (RG-33).
6. Étant donné une deuxième séance le même jour sur le même cours, quand elle se termine, alors elle a repris les cartes restantes, mais une seule séance est comptée pour ce jour, en date locale (RG-33, DT-10).
7. Étant donné l'application fermée brutalement pendant une séance, quand je la rouvre, alors les cartes déjà révisées sont enregistrées (ENF-03).

---

## US-16 Voir le bilan de la séance
Épic C · Tranche 2 · Taille S
Exigences : EF-20 · Écran : 6. Fin de séance · Dépend de : US-15, US-17

En tant qu'apprenant, je veux voir le bilan de ma séance, afin de mesurer ce que j'ai fait et ce que j'ai fait progresser.

**Critères d'acceptation**
1. Étant donné une séance terminée ou arrêtée, quand le bilan s'affiche, alors il indique les cartes révisées, réussies et ratées, et la durée.
2. Étant donné un module débloqué, devenu maîtrisé ou passé « à consolider » pendant la séance, quand le bilan s'affiche, alors il mentionne ce changement (par exemple « Module 2 débloqué »).
3. Étant donné le bilan, quand je le ferme, alors je reviens à l'accueil.

Une carte « réussie » est une carte notée autre chose que « à revoir ».
