# Épic B. Vérifier les cartes

Cahier des charges, section 3.2. Exigences EF-06 à EF-13, règles RG-15 à RG-23. Écrans 4 (Vérification) et 9 (Cartes du module).

---

## US-07 Vérifier les cartes une par une
Épic B · Tranche 1 · Taille M
Exigences : EF-06, EF-07, EF-08, EF-11, EF-12, ENF-01, ENF-03 · Règles : RG-02, RG-03, RG-15 à RG-19 · Écran : 4. Vérification · Dépend de : US-05

En tant qu'auteur, je veux examiner chaque carte générée et l'accepter ou la rejeter avec un motif, afin que seules des cartes justes entrent en révision.

**Critères d'acceptation**
1. Étant donné un module « généré », quand j'appuie sur « Vérifier les cartes », alors la première carte à vérifier s'affiche en entier (question, réponse et, pour un QCM, les choix proposés), avec à côté la section de la ressource d'où elle vient.
2. Étant donné une carte affichée, quand j'appuie sur « Accepter », alors la décision est enregistrée aussitôt, et la carte suivante s'affiche.
3. Étant donné une carte affichée, quand j'appuie sur « Rejeter », alors je dois choisir un motif parmi « fausse », « hors sujet », « en double » et « mal formulée ». La carte n'est rejetée qu'une fois le motif choisi.
4. Étant donné la vérification en cours, quand je regarde l'écran, alors l'avancement s'affiche (par exemple « 12 cartes vérifiées sur 28 »).
5. Étant donné l'écran de vérification, quand je cherche à tout accepter d'un coup, à modifier une carte ou à la supprimer, alors aucune action ne le permet : une carte presque juste se rejette (RG-02, RG-03, RG-17).
6. Étant donné une vérification interrompue (je quitte l'écran ou l'application se ferme), quand je reprends, alors elle repart à la première carte non vérifiée, et les décisions déjà prises sont conservées.
7. Étant donné le téléphone sans connexion, quand je vérifie des cartes, alors tout fonctionne (ENF-01).

---

## US-08 Annuler la dernière décision
Épic B · Tranche 2 · Taille S
Exigences : EF-09 · Règles : RG-20 · Écran : 4. Vérification · Dépend de : US-07

En tant qu'auteur, je veux annuler en un geste ma dernière décision, afin de corriger tout de suite une erreur de doigt.

**Critères d'acceptation**
1. Étant donné une décision qui vient d'être prise, quand j'appuie sur « Annuler la dernière décision », alors la carte revient à l'écran, à vérifier, et l'avancement recule d'une carte.
2. Étant donné une carte rejetée puis remise à vérifier par l'annulation, quand je l'accepte, alors son motif de rejet est effacé.
3. Étant donné un module validé, quand j'ouvre l'écran, alors l'annulation n'est plus possible.

---

## US-09 Voir toutes les cartes du module et changer une décision
Épic B · Tranche 2 · Taille M
Exigences : EF-10, EF-11 · Règles : RG-20 · Écran : 9. Cartes du module · Dépend de : US-07

En tant qu'auteur, je veux voir toutes les cartes d'un module avec leur décision, afin de revenir sur un choix avant de valider.

**Critères d'acceptation**
1. Étant donné un module généré ou validé, quand j'ouvre la liste de ses cartes, alors chaque carte affiche sa décision : acceptée, rejetée (avec son motif) ou à vérifier.
2. Étant donné un module non validé, quand je change la décision d'une carte depuis la liste, alors le changement est enregistré, et l'avancement se met à jour.
3. Étant donné un module non validé avec des cartes à vérifier, quand j'appuie sur « Reprendre la vérification », alors l'écran de vérification s'ouvre sur la première carte à vérifier.
4. Étant donné un module validé, quand j'ouvre la liste, alors les décisions s'affichent sans pouvoir être changées.

---

## US-10 Relire le récapitulatif et valider le module
Épic B · Tranche 1 · Taille M
Exigences : EF-13 · Règles : RG-20 à RG-23, RG-40 · Écran : 4. Vérification · Dépend de : US-07

En tant qu'auteur, je veux relire le récapitulatif de mes décisions puis valider le module, afin de faire entrer ses cartes acceptées en révision.

**Critères d'acceptation**
1. Étant donné toutes les cartes du module vérifiées, quand la dernière décision est prise, alors le récapitulatif s'affiche (par exemple « 28 cartes : 24 acceptées, 4 rejetées ») avec le bouton « Valider le module ».
2. Étant donné des cartes encore à vérifier, quand je cherche à valider, alors la validation n'est pas possible.
3. Étant donné le récapitulatif, quand je confirme la validation, alors le module passe à « validé », ses cartes acceptées deviennent des cartes actives, et les décisions deviennent définitives.
4. Étant donné un module validé, quand on calcule la fiabilité des cartes (C2), alors elle vaut cartes acceptées ÷ cartes vérifiées (RG-22).
5. Étant donné un module dont toutes les cartes sont rejetées, quand je le valide, alors il porte la mention « sans carte » et ne bloque pas le module suivant (RG-23).
6. Étant donné un module déjà débloqué mais pas encore validé, quand je le valide, alors ses cartes actives peuvent entrer dans les séances suivantes (RG-40).
