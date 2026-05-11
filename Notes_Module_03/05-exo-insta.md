# Exercice – Étude de cas start‑up : Instagram, de zéro à 100M utilisateurs

> Objectif : appliquer de façon concrète tous les acquis de la formation (modèles cloud, sécurité, migration, FinOps, architectures bien conçues, etc.) pour concevoir **une architecture cloud moderne** pour une application type Instagram en 2026.[web:455]

---

## 0. Contexte de l’étude de cas

Vous travaillez dans une start‑up qui lance **InstaPix**, une application de partage de photos et de courtes vidéos inspirée d’Instagram :

- Lancement prévu en **MVP** dans 3 mois.
- Objectif : tenir si le produit passe de **10 000** à **100 millions d’utilisateurs** en quelques années.
- L’application doit être disponible dans plusieurs régions (Europe, US), avec des contraintes RGPD (données utilisateurs EU).
- L’équipe est réduite : 6 développeurs, 2 DevOps/Cloud, 1 Product Owner.

L’application est **cloud‑native par design**, construite directement sur un cloud public.

---

## 1. Phase 1 – Analyse & exigences (15–20 min)

En groupe, remplissez les blocs suivants pour cadrer le besoin.

### 1.1 Exigences fonctionnelles clés

- [ ] Inscription / authentification utilisateur (email / réseaux sociaux)
- [ ] Upload de photos et vidéos courtes
- [ ] Fil d’actualité (feed)
- [ ] Likes, commentaires, abonnements
- [ ] Notifications (push / in‑app)

**À vous :**
- Ajoutez 2–3 fonctionnalités différenciantes que vous voudriez tester (ex : filtres IA, stories, chat, recommandation…).  

```text
Fonctionnalités différenciantes :
- …
- …
```

### 1.2 Exigences non fonctionnelles (à discuter)

Cochez / complétez selon votre vision :

- [ ] Scalabilité forte (pics trafics imprévisibles)
- [ ] Haute disponibilité (SLA visé : …)
- [ ] Latence faible pour l’upload/affichage des médias
- [ ] Gouvernance des données (RGPD, consentement, droit à l’oubli)
- [ ] Time‑to‑market très court
- [ ] Budget limité au départ, mais capable de grossir en cas de succès

---

## 2. Phase 2 – Choix du modèle cloud & stratégie d’adoption (15 min)

### 2.1 Modèle de déploiement et de service

En vous basant sur le cours :

- Quel **modèle de déploiement** choisissez‑vous comme base ?
  - [ ] Cloud public
  - [ ] Cloud privé
  - [ ] Cloud hybride
  - [ ] Multicloud ciblé

- Quels **modèles de service** allez‑vous combiner ?
  - [ ] IaaS (VM)
  - [ ] PaaS (DB managée, message broker, cache…)
  - [ ] FaaS / Serverless
  - [ ] SaaS (auth, monitoring, mailing, etc.)

**Expliquez vos choix en 4–5 lignes (vitesse, coût, sécurité, souveraineté, IA) :**

```text
Nos choix de modèles cloud et pourquoi :
- …
```

### 2.2 Stratégie d’adoption / roadmap

Supposez que le MVP existe déjà en local chez un développeur (monolithe + base PostgreSQL) :

- Sur la base des **5R** (Réhéberger, Refactoriser, Réviser, Reconstruire, Remplacer), que faites‑vous pour :
  - le backend API ?
  - la base de données ?
  - le stockage des images/vidéos ?
  - l’authentification ?

```text
Stratégie 5R par composant :
- Backend :
- Base de données :
- Stockage médias :
- Authentification :
```

---

## 3. Phase 3 – Esquisser l’architecture cible (30–40 min)

### 3.1 Dessiner les grandes briques

Sur un tableau / papier / outil en ligne, dessinez votre architecture cible en couches (ou décrivez‑la ici) :

- Couche **accès client** : appli mobile / web, CDN.
- Couche **connectivité & edge** : Internet, CDN, éventuel edge (si pertinent).
- Couche **services applicatifs & data** :
  - API (microservices ou monolithe containerisé),
  - Base(s) de 
