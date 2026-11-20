# Épic E. Régler l'application

Cahier des charges, section 3.5. Exigences EF-25 à EF-27, règles RG-42 à RG-46. Écran 8 (Paramètres).

---

## US-21 Saisir et vérifier la clé d'accès au service d'IA
Épic E · Tranche 1 · Taille M · Statut : à faire
Exigences : EF-25, EF-27, ENF-02 · Règles : RG-42, RG-43 · Décisions : DT-07, DT-12 · Écran : 8. Paramètres · Dépend de : T-04

En tant qu'auteur, je veux saisir ma clé d'accès au service d'intelligence artificielle et savoir tout de suite si elle fonctionne, afin de pouvoir générer des cartes.

**Critères d'acceptation**
1. Étant donné l'écran Paramètres, quand je saisis une clé et que je l'enregistre, alors l'application la vérifie auprès du service, puis la conserve dans le coffre sécurisé d'Android, pas dans la base de données (DT-12).
2. Étant donné une clé enregistrée, quand j'ouvre les paramètres, alors seuls ses derniers caractères sont visibles (RG-42).
3. Étant donné une clé refusée par le service, quand je l'enregistre, alors l'application le signale, et l'ancienne clé, s'il y en avait une, reste en place.
4. Étant donné le téléphone sans connexion, quand j'enregistre une clé, alors elle est enregistrée sans vérification, et l'application le signale.
5. Étant donné une clé enregistrée, quand je la remplace par une nouvelle clé valide, alors seule la nouvelle est conservée.
6. Étant donné aucune clé enregistrée, quand je vérifie des cartes ou que je révise, alors tout fonctionne (RG-43).

---

## US-22 Régler le plafond de cartes par module
Épic E · Tranche 2 · Taille S · Statut : à faire
Exigences : EF-26, ENF-07 · Règles : RG-12, RG-44 à RG-46 · Écran : 8. Paramètres · Dépend de : US-05

En tant qu'auteur, je veux régler le nombre maximal de cartes par module, afin d'adapter le volume de cartes, et donc le coût de génération, à mes cours.

**Critères d'acceptation**
1. Étant donné une installation neuve, quand j'ouvre les paramètres, alors le plafond vaut 30.
2. Étant donné l'écran Paramètres, quand je règle le plafond, alors seules les valeurs de 5 à 100 sont acceptées (RG-44).
3. Étant donné un plafond passé de 30 à 20, quand je génère un nouveau module, alors il a au plus 20 cartes. Les modules déjà générés gardent leurs cartes (RG-45).
4. Étant donné l'écran Paramètres, quand je le parcours, alors les autres valeurs (20 cartes par séance, 10 nouvelles au plus, seuils de progression) ne sont pas réglables (RG-46).
