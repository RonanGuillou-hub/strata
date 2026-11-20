# Épic 0. Socle technique

Objectif : un squelette qui marche, c'est-à-dire l'application vide installée sur le téléphone, avec ses tests, sa base de données et l'intégration continue. Il lève aussi les trois incertitudes qui pourraient changer les stories : l'import OneDrive, la lecture des PDF et la consigne de génération.

Limite : on construit seulement ce qu'il faut pour livrer US-01 avec ses tests, et le reste viendra avec les stories.

Ordre : T-01 à T-07, puis T-09. T-08 (FSRS) se fait plus tard, juste avant l'épic C.

---

## T-01 Environnement de développement
Épic 0 · Taille M · Statut : à faire
Décisions : DT-02, DT-03 · Dépend de : rien

**Objectif.** Installer Flutter et Android SDK dans Ubuntu (WSL), relier le téléphone par le débogage sans fil, et développer dans VS Code connecté à WSL.

**Critères d'acceptation**
1. Étant donné le téléphone (Android 13 ou plus récent) et le PC sur le même Wi-Fi, quand on associe le téléphone par le débogage sans fil, alors la commande `adb devices` le voit depuis Ubuntu.
2. Étant donné une application Flutter vide, quand on la lance, alors elle s'installe et s'affiche sur le téléphone.
3. Étant donné l'application lancée, quand on modifie un texte dans le code, alors la modification apparaît sur le téléphone en quelques secondes, sans réinstaller l'application.
4. Étant donné un redémarrage du téléphone ou du PC, quand on suit la procédure écrite dans `docs/environnement.md`, alors la liaison se rétablit en moins de 5 minutes.
5. Étant donné VS Code connecté à WSL, quand on appuie sur F5, alors l'application se lance sur le téléphone.

Repli : si le critère 1 ou 4 ne tient pas, passer au câble USB avec `usbipd-win`, et noter pourquoi.

---

## T-02 Projet Flutter et thème Strata
Épic 0 · Taille S · Statut : à faire
Décisions : DT-02 · Exigences : ENF-05, ENF-06 · Dépend de : T-01

**Objectif.** Créer le projet avec sa structure en couches (données, règles, écrans), l'analyse automatique du code, et le thème du design system Strata.

**Critères d'acceptation**
1. Étant donné le projet, quand on lance l'analyse du code (`flutter analyze`), alors elle ne signale aucun problème.
2. Étant donné l'écran d'accueil vide, quand il s'affiche, alors il reprend les couleurs du design system (fond F4F7FA, texte 15233A, couleur principale 0B7A84) et ses polices (Bricolage Grotesque pour les titres, Atkinson Hyperlegible pour le texte).
3. Étant donné le téléphone sans connexion, quand l'application démarre, alors les polices s'affichent quand même : elles sont incluses dans l'application, pas téléchargées (ENF-01).
4. Étant donné l'application, quand elle s'affiche, alors tous ses textes sont en français (ENF-06).

---

## T-03 Framework de tests
Épic 0 · Taille M · Statut : à faire
Dépend de : T-02

**Objectif.** Mettre en place les trois sortes de tests (unitaire, d'écran, de bout en bout), avec une convention qui relie chaque test au critère d'acceptation qu'il couvre.

**Critères d'acceptation**
1. Étant donné un test unitaire, un test d'écran et un test de bout en bout d'exemple, quand on les lance, alors ils passent tous les trois.
2. Étant donné la convention de nommage (référence de la story et du critère, par exemple `US-12 CA-2`), quand on cherche une référence dans le code des tests, alors on trouve le ou les tests qui la couvrent.
3. Étant donné le projet, quand on lance une seule commande, alors elle exécute les tests unitaires et d'écran et affiche la couverture du code.
4. Étant donné le téléphone relié, quand on lance les tests de bout en bout, alors ils s'exécutent sur le téléphone.

---

## T-04 Base de données SQLite
Épic 0 · Taille M · Statut : à faire
Décisions : DT-10, DT-11 · Données : partie 6 du cahier des charges · Exigences : ENF-02, ENF-03 · Dépend de : T-03

**Objectif.** Créer la base avec les 14 tables du dictionnaire de données, selon les conventions de la section 6.2, et préparer la façon de la faire évoluer sans perdre de données.

**Critères d'acceptation**
1. Étant donné une installation neuve, quand l'application démarre, alors la base est créée avec les 14 tables, leurs champs et leurs identifiants externes.
2. Étant donné une ligne ajoutée dans une table, quand on la relit, alors `date_creation` est remplie automatiquement, en temps universel (DT-10).
3. Étant donné une installation neuve, quand la base est créée, alors les tables de référence (types de ressource, types de carte, motifs de rejet, consigne) contiennent leurs valeurs de départ.
4. Étant donné une base existante et une nouvelle version du schéma, quand l'application démarre, alors la base est mise à jour sans perte de données.
5. Étant donné une écriture interrompue (application fermée brutalement), quand l'application redémarre, alors la base est intacte (ENF-03).

À consigner : la bibliothèque SQLite retenue, en DT-15 (point ouvert PO-02).

---

## T-05 Intégration continue
Épic 0 · Taille S · Statut : à faire
Dépend de : T-03

**Objectif.** Lancer automatiquement les tests à chaque envoi sur GitHub, avec GitHub Actions.

**Critères d'acceptation**
1. Étant donné un envoi sur la branche `main`, quand GitHub le reçoit, alors l'analyse du code et les tests unitaires et d'écran se lancent automatiquement.
2. Étant donné un test qui échoue, quand l'intégration continue se termine, alors GitHub l'affiche en échec et nomme le test.
3. Étant donné le dépôt, quand on ouvre sa page sur GitHub, alors un badge indique si les derniers tests sont passés.

Les tests de bout en bout restent lancés à la main sur le téléphone (point ouvert PO-03).

---

## T-06 Spike : import d'un fichier OneDrive
Épic 0 · Taille S · Durée limitée : 1 jour · Statut : à faire
Décisions : DT-05 · Dépend de : T-01

**Question.** Depuis l'application, le sélecteur de fichiers d'Android permet-il de choisir un PDF ou un notebook rangé dans OneDrive, et de lire son contenu ?

**Critères d'acceptation**
1. Étant donné l'application OneDrive installée sur le téléphone, quand on ouvre le sélecteur de fichiers depuis un prototype, alors OneDrive apparaît parmi les emplacements.
2. Étant donné un PDF présent seulement dans OneDrive (pas encore téléchargé), quand on le choisit, alors le prototype lit son contenu.
3. Étant donné la fin de la journée prévue, quand le spike s'arrête, alors une conclusion est écrite dans `docs/spikes/T-06-onedrive.md` : solution retenue ou solution de repli, et effets sur US-03.
4. Étant donné la conclusion, quand elle est acceptée, alors DT-05 passe de « À vérifier » à « Décidé » dans le cahier des charges.

Le code du prototype est jetable : il n'entre pas dans l'application.

---

## T-07 Spike : lecture du texte d'un PDF et d'un notebook
Épic 0 · Taille S · Durée limitée : 1 jour · Statut : à faire
Décisions : DT-06 · Règles : RG-04, RG-07 · Dépend de : T-01

**Question.** Une bibliothèque Dart extrait-elle le texte d'un vrai PDF de cours, et peut-on le découper en sections d'après ses titres ?

**Critères d'acceptation**
1. Étant donné 3 PDF d'un cours écrit, quand on en extrait le texte, alors le texte obtenu est lisible et dans le bon ordre.
2. Étant donné ces 3 PDF, quand on les découpe d'après leurs titres, alors les sections obtenues correspondent aux titres du document.
3. Étant donné un PDF scanné (sans texte), quand on tente l'extraction, alors le prototype détecte qu'il n'y a pas de texte exploitable.
4. Étant donné un notebook, quand on le lit cellule par cellule, alors on retrouve ses sections d'après ses titres.
5. Étant donné la fin de la journée prévue, quand le spike s'arrête, alors une conclusion est écrite dans `docs/spikes/T-07-pdf.md`, et DT-06 est mis à jour.

---

## T-08 Intégration de FSRS
Épic 0 · Taille S · Statut : à faire
Décisions : DT-09, DT-10 · Règles : RG-28, RG-29, RG-34 · Dépend de : T-04 · Placée juste avant l'épic C

**Objectif.** Intégrer le paquet `fsrs` 2.0.1 derrière un point d'accès unique, avec la correspondance des notes.

**Critères d'acceptation**
1. Étant donné une carte jugée par l'apprenant, quand il donne ★, ★★, ★★★ ou ★★★★, alors FSRS reçoit respectivement « à revoir », « difficile », « bien » ou « facile ».
2. Étant donné un QCM, quand la réponse est juste, alors FSRS reçoit « bien » ; quand elle est fausse, il reçoit « à revoir » (point ouvert PO-01).
3. Étant donné une carte, quand elle reçoit une note meilleure, alors sa prochaine révision est plus lointaine (RG-29).
4. Étant donné une révision, quand l'échéance est calculée, alors elle est enregistrée en temps universel, et l'intervalle se calcule par `date_echeance − date_revision` (DT-09, DT-10).

---

## T-09 Prototype de la consigne de génération
Épic 0 · Taille M · Durée limitée : 2 jours · Statut : à faire
Décisions : DT-07, DT-08, DT-13 · Règles : RG-08 à RG-13 · Critère de réussite : C2 · Dépend de : T-07

**Objectif.** Régler, avec un prototype Python jetable, la consigne envoyée au service d'intelligence artificielle, avant de coder la génération dans l'application (US-05).

**Critères d'acceptation**
1. Étant donné 2 modules réels d'un cours écrit, quand le prototype génère leurs cartes, alors les cartes respectent le plafond de 30 et mêlent QCM et questions ouvertes (RG-12, RG-13).
2. Étant donné les cartes générées, quand l'auteur les vérifie à la main, alors la part de cartes acceptées est mesurée. Elle doit approcher la cible de C2 : au moins 80 %.
3. Étant donné des cartes de sens très proche, quand on les compare, alors le seuil de détection des doublons est réglé (DT-13).
4. Étant donné la fin du prototype, quand il s'arrête, alors la consigne retenue est enregistrée comme première valeur de la table `consigne`, et ses résultats sont écrits dans `docs/spikes/T-09-consigne.md`.

Le prototype n'est pas livré (DT-08).
