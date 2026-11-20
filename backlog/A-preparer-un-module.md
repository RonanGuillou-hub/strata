# Épic A. Préparer un module

Cahier des charges, section 3.1. Exigences EF-01 à EF-05, règles RG-04 à RG-14. Écrans 1 (Accueil), 2 (Modules du cours) et 3 (Module).

---

## US-01 Créer un cours
Épic A · Tranche 1 · Taille S
Exigences : EF-01 · Écran : 1. Accueil · Dépend de : T-04

En tant qu'auteur, je veux créer un cours en lui donnant un nom, afin d'y ranger les modules que j'étudie.

**Critères d'acceptation**
1. Étant donné le premier lancement, quand l'accueil s'affiche, alors il invite à créer un premier cours.
2. Étant donné l'accueil, quand j'appuie sur « + » et que je saisis un nom, alors le cours est créé et apparaît sur l'accueil.
3. Étant donné la création d'un cours, quand je remplis aussi la description et l'origine, alors elles sont enregistrées. Quand je les laisse vides, le cours est créé quand même.
4. Étant donné un cours déjà nommé « Python », quand j'en crée un autre avec le même nom, alors l'application refuse et explique pourquoi.
5. Étant donné un nom vide, quand je valide, alors le cours n'est pas créé.

---

## US-02 Créer et ordonner les modules d'un cours
Épic A · Tranche 1 · Taille M
Exigences : EF-02 · Règles : RG-05, RG-14 · Écran : 2. Modules du cours · Dépend de : US-01

En tant qu'auteur, je veux créer les modules de mon cours dans l'ordre où je les étudie, afin que chacun se débloque après le précédent.

**Critères d'acceptation**
1. Étant donné un cours, quand je crée un module, alors il s'ajoute à la fin de la liste, à l'état « en préparation ».
2. Étant donné un cours sans module, quand je crée le premier module, alors il est débloqué d'office ; les modules suivants sont bloqués.
3. Étant donné un module « en préparation », quand je le renomme ou que je change sa place, alors la modification est enregistrée.
4. Étant donné un module « généré » ou « validé », quand j'ouvre la liste, alors il n'est plus possible de le renommer ni de le déplacer.
5. Étant donné un module, quand je cherche à le supprimer, alors aucune action ne le permet (RG-14).

---

## US-03 Ajouter une ressource à un module
Épic A · Tranche 1 · Taille L
Exigences : EF-03 · Règles : RG-04, RG-05, RG-07 · Décisions : DT-05, DT-06 · Écran : 3. Module · Dépend de : US-02, T-06, T-07

En tant qu'auteur, je veux ajouter à un module un PDF ou un notebook choisi dans mon espace de stockage en ligne, afin que les cartes soient générées à partir de mes cours.

**Critères d'acceptation**
1. Étant donné un module « en préparation », quand j'appuie sur « Ajouter une ressource », alors le sélecteur de fichiers d'Android s'ouvre et je peux choisir un fichier dans OneDrive.
2. Étant donné un PDF contenant du texte, quand je le choisis, alors la ressource est ajoutée au module, et son texte est découpé en sections d'après ses titres.
3. Étant donné un notebook, quand je le choisis, alors la ressource est ajoutée, et ses sections suivent ses titres.
4. Étant donné un fichier dans un autre format, quand je le choisis, alors l'application refuse l'ajout et indique les formats acceptés.
5. Étant donné un PDF scanné ou imprimé sous forme d'image, quand je le choisis, alors l'application refuse l'ajout et explique pourquoi.
6. Étant donné un module « généré », quand je l'ouvre, alors le bouton « Ajouter une ressource » n'apparaît pas (RG-06).

---

## US-04 Voir et retirer les ressources d'un module
Épic A · Tranche 2 · Taille S
Exigences : EF-04 · Règles : RG-05, RG-06 · Écran : 3. Module · Dépend de : US-03

En tant qu'auteur, je veux voir les ressources d'un module et en retirer une, afin de corriger une erreur avant la génération.

**Critères d'acceptation**
1. Étant donné un module, quand je l'ouvre, alors je vois la liste de ses ressources, avec leur nom et leur type.
2. Étant donné un module « en préparation », quand je retire une ressource, alors elle disparaît de la liste et n'est pas utilisée pour la génération.
3. Étant donné un module « généré », quand je l'ouvre, alors le bouton « Retirer » n'apparaît pas.

---

## US-05 Générer les cartes d'un module
Épic A · Tranche 1 · Taille L
Exigences : EF-05, ENF-04, ENF-07 · Règles : RG-01, RG-06 à RG-08, RG-11 à RG-13 · Décisions : DT-07 · Écran : 3. Module · Dépend de : US-03, US-21, T-09

En tant qu'auteur, je veux lancer la génération des cartes d'un module, afin d'obtenir des cartes à vérifier sans les écrire moi-même.

**Critères d'acceptation**
1. Étant donné un module « en préparation » avec au moins une ressource et une clé d'accès enregistrée, quand j'appuie sur « Générer les cartes », alors l'application montre qu'elle travaille pendant toute la génération (ENF-04).
2. Étant donné une génération réussie, quand elle se termine, alors le module passe à « généré », ses cartes sont prêtes à vérifier, et le bouton « Vérifier les cartes » apparaît.
3. Étant donné les cartes générées, quand on les examine, alors chacune a un type (QCM ou question ouverte, RG-01), est rattachée à la section d'où elle vient, rédigée dans la langue du cours, et liée à la génération qui l'a produite, avec le modèle utilisé (RG-07, RG-08, RG-11).
4. Étant donné un plafond de 30 cartes, quand la génération se termine, alors le module a au plus 30 cartes (RG-12).
5. Étant donné un module sans ressource, quand je l'ouvre, alors la génération ne peut pas être lancée.
6. Étant donné une absence de connexion, un service indisponible, ou une clé absente ou refusée, quand je lance la génération, alors un message clair l'explique, et le module reste « en préparation ». Sans clé, le message renvoie vers les paramètres.
7. Étant donné une génération interrompue (application fermée), quand je rouvre le module, alors les cartes déjà produites sont effacées, et le module est « en préparation », prêt à relancer.

---

## US-06 Tenir compte des rejets passés et écarter les doublons
Épic A · Tranche 2 · Taille M
Exigences : EF-05 · Règles : RG-09, RG-10 · Décisions : DT-13 · Dépend de : US-05, US-10

En tant qu'auteur, je veux que la génération apprenne de mes rejets et écarte les cartes en double, afin d'avoir moins de cartes à rejeter au fil des modules.

**Critères d'acceptation**
1. Étant donné des cartes rejetées dans les modules précédents du cours, quand je génère un nouveau module, alors la consigne envoyée contient leurs motifs de rejet et des exemples de cartes acceptées.
2. Étant donné une carte générée dont la question est très proche d'une carte déjà présente dans le cours, quand la génération se termine, alors cette carte est écartée avant la vérification (seuil réglé dans T-09).
3. Étant donné une carte écartée comme doublon, quand on consulte la génération, alors elle est enregistrée comme écartée, et elle n'apparaît pas dans les cartes à vérifier.

Remarque : cette story vient du même besoin que US-05 (EF-05), coupé en deux. La génération de base apporte déjà de la valeur ; l'apprentissage des rejets et le tri des doublons l'améliorent ensuite.
