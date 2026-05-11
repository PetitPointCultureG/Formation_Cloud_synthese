# Étude de cas personnalisée : mon use case cloud

> Objectif : chaque participant prend **un cas réel de son organisation** et applique l’ensemble des acquis de la formation (adoption, sécurité, Well‑Architected, 5R, FinOps, GRC, etc.) pour construire une **mini‑étude de cas de migration / mise en place dans le cloud**.[web:465][web:467]

---

## 0. Choisir son use case (5 min)

**Consigne :** sélectionnez **un cas concret** dans votre contexte (domaine, entreprise, projet).

Exemples possibles :
- Portail client, application interne métier, outil de reporting, pipeline data/IA, e‑commerce, IoT, etc.

```text
Mon use case :
- Nom / description courte :
- Domaine (métier / organisation) :
- Utilisateurs principaux :
```

---

## 1. Cadrage métier & objectifs (10–15 min)

### 1.1 Problème métier / opportunité

Expliquez **le problème actuel** ou l’opportunité que le cloud doit adresser.

- [ ] Problème de performance / scalabilité  
- [ ] Problème de disponibilité / résilience  
- [ ] Problème de coûts / rigidité CAPEX  
- [ ] Besoin d’IA / analytics / temps réel  
- [ ] Conformité / sécurité / audit  
- [ ] Autre : …

```text
Problème(s) / opportunité(s) métier :
- …
```

### 1.2 Objectifs business & KPIs

Décrivez ce que votre organisation attend de ce passage au cloud.

```text
Objectifs business principaux :
- (ex : réduire le temps de mise en production de X à Y)
- (ex : absorber un trafic xN sans dégrader la performance)
- (ex : répondre à NIS2 / RGPD / DORA, etc.)

KPIs de succès :
- …
```

---

## 2. Analyse de l’existant (10–15 min)

### 2.1 Architecture actuelle (simplifiée)

Décrivez rapidement l’existant :

```text
Type d’architecture actuelle :
- On‑prem / datacenter / hébergeur :
- Monolithe / microservices / batchs :
- Type de base(s) de données :
- Intégrations externes clés (SaaS, partenaires, API) :
```

### 2.2 Contraintes & risques

- Techniques (dette, obsolescence, mainframe, monolithe…)
- Organisationnelles (compétences, silos, process)
- Réglementaires (RGPD, NIS2, secteur, localisation de la donnée)

```text
Contraintes / risques principaux :
- …
```

---

## 3. Stratégie cloud & modèles choisis (15–20 min)

### 3.1 Modèle de déploiement & services

Cochez vos choix :

- **Modèle de déploiement :**
  - [ ] Cloud public
  - [ ] Cloud privé
  - [ ] Hybride
  - [ ] Multicloud ciblé

- **Modèle(s) de service :**
  - [ ] IaaS (VM)
  - [ ] PaaS (DBaaS, messaging, cache, etc.)
  - [ ] FaaS / Serverless
  - [ ] SaaS (auth, mail, monitoring, etc.)

```text
Justification (vitesse, coûts, sécurité, souveraineté, IA, etc.) :
- …
```

### 3.2 Application des 5R

Pour les principaux composants de votre use case, choisissez un **R** (Réhéberger / Refactoriser / Réviser (Replatform) / Reconstruire / Remplacer).

```text
Composants & stratégies 5R :
- Composant 1 :
- Composant 2 :
- Composant 3 :
- …
Justification rapide :
- …
```

---

## 4. Esquisser l’architecture cible (20–25 min)

### 4.1 Couches de l’architecture

Remplissez (et/ou dessinez sur un tableau) votre architecture en vous basant sur les **couches vues en cours** :

```text
Couche Accès client :
- (web, mobile, API publique, CDN…)

Couche Connectivité & edge :
- (Internet, VPN, SD‑WAN, CDN, edge…)

Couche Identité / sécurité / gouvernance :
- (IAM, rôles, secrets, policies, Zero Trust…)

Couche Services applicatifs & data :
- (API / microservices / fonctions, DB, cache, queues, moteurs de recherche…)

Couche IA / analytics (si applicable) :
- (LLM, modèles ML, data lake, data warehouse…)

Couche Ressources virtuelles :
- (VM, clusters Kubernetes, serverless…)

Couche Ressources physiques (si concerné, cloud privé / edge) :
- (sites, appliances, contraintes spécifiques…)
```

### 4.2 Résilience & scalabilité

Répondez :

1. Comment votre architecture encaisse‑t‑elle **un x10 du trafic** ?  
2. Que se passe‑t‑il si :
   - une zone / région tombe,
   - un service externe critique est indisponible ?  
3. Quels patterns utilisez‑vous (autoscaling, files, retries, circuit breaker, cache, multi‑AZ/région…) ?

```text
Stratégie de résilience & scalabilité :
- …
```

---

## 5. Sécurité, GRC & conformité (20–25 min)

### 5.1 Surfaces d’attaque principales de votre use case

Cochez / complétez :

- [ ] APIs (clients, partenaires, internes)
- [ ] Interfaces d’admin
- [ ] Stockage de données sensibles (client, santé, finance…)
- [ ] CI/CD & registry (code, images, secrets)
- [ ] Services SaaS connectés
- [ ] Autre : …

```text
Surfaces d’attaque identifiées :
- …
```

### 5.2 Mesures de sécurité & GRC

Pour chaque axe, notez vos choix :

- **IAM & Zero Trust** (MFA, rôles, segmentation, accès Just‑In‑Time)  
- **Protection des données** (chiffrement, localisation, RGPD/NIS2, masquage, sauvegardes)  
- **Sécurité des APIs & intégrations** (gateway, OAuth/OIDC, rate limiting, WAF)  
- **Détection & réponse** (logs, SIEM/XDR, CNAPP/CSPM, playbooks d’incident)  

```text
Mesures prévues :
- IAM / Zero Trust :
- Données / RGPD / NIS2 :
- APIs / intégrations :
- Détection / réponse :
```

---

## 6. Processus de migration & étapes (15–20 min)

En vous basant sur le **processus de migration** vu en cours :

- [ ] Étape 1 : Analyse & cadrage (coûts, archi, sécurité)
- [ ] Étape 2 : POC / pilote
- [ ] Étape 3 : Migration des données
- [ ] Étape 4 : Migration des applications
- [ ] Étape 5 : Optimisation initiale
- [ ] Étape 6 : Supervision & amélioration continue

```text
Adaptation à mon use case :
- Ce que je mets dans le POC :
- Ordre des migrations (données / applis) :
- Principaux risques de migration & mitigations :
```

---

## 7. FinOps & optimisation (10–15 min)

### 7.1 Postes de coûts & leviers

Identifiez les **3 principaux postes de coût** et au moins **2 leviers** d’optimisation par poste (droitsizing, réservations, archivage, politique de logs, etc.).

```text
Postes de coût clés :
- Poste 1 :
- Poste 2 :
- Poste 3 :

Leviers d’optimisation :
- …
```

### 7.2 Gouvernance FinOps

Qui suit quoi, à quelle fréquence, avec quels outils / dashboards ?

```text
Organisation FinOps pour ce use case :
- Rôles impliqués :
- KPIs suivis :
- Rituels (revues mensuelles, alertes, etc.) :
```

---

## 8. Synthèse & pitch (5–10 min)

Préparez un **pitch de 3–5 minutes** pour le reste du groupe :

1. Mon **use case** et le **problème métier** adressé.  
2. Mes **choix cloud** (modèles, architecture, sécurité, FinOps).  
3. Les **principaux risques / compromis** et comment je les gère.  
4. Une **évolution future** (multicloud, cloud souverain, IA, extension fonctionnelle…).

```text
Points clés de mon pitch :
- …
```

> À la fin de l’exercice, chaque participant doit être capable de **raconter l’histoire cloud** de son propre cas d’usage, en montrant qu’il sait mobiliser les concepts vus pendant la formation : modèles de services & déploiement, stratégies de migration, sécurité & GRC, FinOps, Well‑Architected, Zero Trust, IA, etc.
