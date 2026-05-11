```markdown
# Étude de cas d’entreprise établie : Netflix, du datacenter au cloud

> Objectif : appliquer les acquis de la formation (adoption, sécurité, FinOps, architectures bien conçues, migration 5R, GRC, etc.) pour analyser et concevoir la trajectoire de migration de **Netflix** d’un modèle sur site vers le cloud public.[web:455]

Contexte simplifié :

- Leader du streaming vidéo par abonnement.
- En 2009, 100 % du trafic client passait par les datacenters propres de Netflix.
- Fin 2010, une grande partie du trafic fonctionnait déjà sur AWS.
- L’augmentation massive du trafic a forcé à **repenser toute l’architecture**, à la fois pour **scaler** et **réduire les coûts**.

---

## Phase 1 – Comprendre le point de départ (15–20 min)

En groupe, remplissez les éléments suivants pour caractériser la situation initiale de Netflix (on‑prem en 2009).

### 1.1 SI de départ (hypothèses guidées)

- Monolithes applicatifs dans les datacenters Netflix.
- Bases de données relationnelles centralisées.
- Stockage vidéo sur SAN/NAS internes.
- Pics de charge forts le soir et le week‑end.

**À vous : décrivez en quelques lignes :**

```text
Architecture de départ (2009) :
- Applications :
- Données :
- Stockage vidéo :
- Réseau / distribution :
```

### 1.2 Limites du modèle sur site

Cochez et complétez :

- [ ] Évolutivité limitée (ajouter des serveurs prend des mois).
- [ ] Coût élevé des datacenters (capex + opex).
- [ ] Difficulté à gérer les pics de trafic (soirées, sorties de séries).
- [ ] Résilience limitée (pannes datacenter, sinistres).
- [ ] Time‑to‑market réduit pour lancer de nouvelles fonctionnalités / régions.

```text
Principales douleurs métiers et techniques :
- …
```

---

## Phase 2 – Stratégie d’adoption & modèle cloud (20 min)

### 2.1 Choix du modèle de déploiement et de services

En vous basant sur la formation :

- Netflix choisit un **cloud public** (AWS).  
  Quels avantages cela lui offre par rapport à un cloud privé ou un simple "colocation" ?

```text
Pourquoi un cloud public pour Netflix ?
- …
```

- Quels **modèles de service** sont les plus logiques pour Netflix ?
  - [ ] IaaS (VM, stockage, réseau)
  - [ ] PaaS (bases managées, queues, caches, services streaming)
  - [ ] FaaS / Serverless (certains traitements)
  - [ ] SaaS (email, analytics, monitoring tiers…)

Expliquez en quelques lignes vos choix :

```text
Combinaison IaaS / PaaS / FaaS / SaaS choisie :
- …
```

### 2.2 Application des stratégies de migration (5R / 7R)

Pour chaque composant, proposez une stratégie :

- Backend de gestion clients (facturation, abonnements)
- Service de recommandation
- Portail web / applis TV
- Pipeline d’encodage vidéo
- Stockage des vidéos

Utilisez les R : Réhéberger / Refactoriser / Réviser / Reconstruire / Remplacer (+ éventuellement Retain / Retire).

```text
Stratégie par composant :
- Gestion clients :
- Recommandation :
- Portail web / TV :
- Encodage vidéo :
- Stockage vidéos :
```

---

## Phase 3 – Architecture cible "Netflix‑like" sur le cloud (30–40 min)

### 3.1 Dessiner / décrire la vue d’ensemble

Structurez votre architecture autour des couches vues en cours :

- **Accès client** : applis TV, mobiles, web + CDN.
- **Connectivité & edge** : Internet, POPs, CDN, edge caching.
- **Services applicatifs** :
  - microservices (gestion catalogue, profils, facturation, recommandation),
  - APIs, gateways.
- **Données** :
  - bases transactionnelles (abonnés, paiements),
  - bases NoSQL / moteurs de recommandation,
  - data lake pour l’analytics.
- **Distribution & stockage vidéo** :
  - stockage objet pour les masters vidéo,
  - CDN/edge pour la diffusion.
- **Gestion & sécurité** :
  - IAM, clés/secrets,
  - logs / métriques / traces,
  - CNAPP/CSPM, sauvegardes, DR.

```text
Architecture cible (description / éléments de votre schéma) :
- Accès / CDN :
- Microservices / APIs :
- Données :
- Vidéo (stockage, CDN) :
- Sécurité / IAM / observabilité :
```

### 3.2 Résilience & disponibilité globale

Répondez aux questions :

1. Comment concevoir l’architecture pour éviter qu’une panne de **région AWS** ne coupe le service mondialement ?  
2. Quels patterns techniques utilisez‑vous pour rendre les microservices robustes (délais, retries, circuit breaker, files, cache) ?  
3. Comment gérez‑vous les **pannes partielles** (une zone en erreur, un service externe indisponible, une base en retard de réplication) ?

```text
Stratégies de résilience Netflix‑like :
- Multi‑région / multi‑AZ :
- Patterns de robustesse :
- Gestion des pannes partielles :
```

---

## Phase 4 – Sécurité, conformité & gouvernance (20–25 min)

### 4.1 Surfaces d’attaque principales pour Netflix

Listez quelques surfaces critiques :

- APIs d’authentification / compte, gestion des abonnements
- Gestion des DRM / licences de contenu
- Plateformes d’admin internes (catalogue, droits, CM)
- Infrastructure de paiement (PSP, PCI, etc.)
- Pipeline CI/CD (déploiement continu de centaines de microservices)

```text
Surfaces d’attaque clés :
- …
```

### 4.2 Mesures de sécurité & conformité

Pour chaque axe, proposez vos décisions :

- **IAM & Zero Trust** : comptes d’admin, permissions microservices, segmentation, MFA/passwordless.
- **Protection des données** : chiffrement, logs d’accès, séparation données EU / hors‑UE, rétention.
- **Protection du pipeline de déploiement** : gestion des secrets, scans IaC / containers, règles de promotion en prod.
- **Détection & réponse** : centralisation des logs, SIEM, playbooks d’incident, exercices de crise.

```text
Stratégie sécurité / conformité :
- IAM / Zero Trust :
- Données / RGPD / NIS2 :
- CI/CD sécurisé :
- Détection / réponse :
```

---

## Phase 5 – FinOps & optimisation à l’échelle Netflix (20 min)

### 5.1 Coûts et leviers d’optimisation

Netflix consomme massivement :

- calcul (encodage, microservices, recommandation),
- stockage (masters vidéo, copies optimisées),
- bande passante (diffusion via CDN).

Questions :

1. Quels sont, selon vous, les **3 grands postes de coût** principaux ?
2. Quels leviers FinOps peuvent être utilisés à grande échelle (réservations, spot instances, tiers de stockage, optimisation des encodages, politique de cache/CDN, etc.) ?
3. Comment intégrer FinOps dans les équipes (KPIs, revues régulières, outils) ?

```text
Analyse FinOps Netflix‑like :
- Postes de coût majeurs :
- Leviers d’optimisation :
- Organisation FinOps :
```

---

## Phase 6 – Débrief & lien avec la formation

En restitution (5–10 min par groupe), chaque équipe doit être capable de montrer :

1. Comment elle a appliqué :
   - les **modèles de déploiement et de service** (public, IaaS/PaaS/FaaS/SaaS),
   - les **stratégies de migration (5R)**,
   - les concepts de **Well‑Architected / Zero Trust / FinOps / GRC**.
2. Quels compromis ont été faits entre :
   - performance vs coûts,
   - vitesse vs résilience,
   - usage de services managés vs risque de lock‑in.
3. Une **évolution future** :
   - ajout d’un deuxième cloud,
   - mise en place d’un cloud souverain pour certaines régions,
   - intégration de nouveaux services IA / personnalisation.

L’objectif est que les participants sortent de cet exercice en sachant **concevoir et critiquer une trajectoire de migration vers le cloud à l’échelle d’un acteur comme Netflix**, en réutilisant tous les blocs vus pendant la formation.
```
