# Étude de cas gouvernementale : NOAA – E‑mail & collaboration dans le cloud

> Objectif : appliquer les acquis de la formation à un cas réel de **migration SaaS dans un environnement public / gouvernemental** (NOAA → Google Apps), en traitant les dimensions : stratégie cloud, sécurité, GRC, migration, conduite du changement, FinOps.[web:465][web:467]

Contexte simplifié :

- Agence fédérale (NOAA), plus de 25 000 agents.
- Mission : compréhension et prévision du climat, de la météo, des océans et zones côtières.
- En 2012, migration vers une suite cloud (Gmail + chat, visioconférence, calendriers, documents partagés).
- Objectifs : réduire les coûts, simplifier la gestion d’un environnement très distribué et multi‑appareils, améliorer la collaboration.

---

## Phase 1 – Comprendre le besoin métier & les contraintes (15 min)

### 1.1 Problèmes à résoudre avant migration

En groupe, listez les principaux problèmes probables de la NOAA avant la migration (faites des hypothèses réalistes) :

- [ ] Multiples serveurs de messagerie on‑prem, hétérogènes.
- [ ] Coûts élevés d’infrastructure (serveurs, stockage, sauvegardes).
- [ ] Problème de capacité de stockage des boîtes mail.
- [ ] Difficulté à collaborer entre bureaux / régions (fuseaux horaires, déplacements).
- [ ] Gestion compliquée des mises à jour logicielles / matérielles.
- [ ] Complexité de support sur de nombreux terminaux (PC, laptops, mobiles…).

```text
Nos 3–5 principaux problèmes de départ pour NOAA :
- …
```

### 1.2 Contraintes spécifiques au secteur public

Cochez / complétez les contraintes probables :

- [ ] Exigences fortes de sécurité (informations sensibles, attaques ciblées).
- [ ] Obligations de conformité (lois fédérales, protection des données, archivage légal).
- [ ] Besoin de transparence & traçabilité (logs, audits).
- [ ] Gestion d’utilisateurs nombreux, répartis sur plusieurs sites, avec des profils très variés (scientifiques, administratifs, opérationnels…).

```text
Contraintes propres au contexte gouvernemental :
- …
```

---

## Phase 2 – Stratégie cloud & choix de la solution (20 min)

### 2.1 Pourquoi une solution SaaS ?

Listez les **avantages d’un SaaS collaboratif** pour un organisme comme la NOAA :

- [ ] Réduction des coûts d’infrastructure (CAPEX → OPEX).
- [ ] Mises à jour logicielles gérées par le fournisseur.
- [ ] Scalabilité pour 25 000+ utilisateurs.
- [ ] Accès simple depuis de multiples sites / terminaux.
- [ ] Fonctions collaboratives natives (partage docs, chat, visio, agendas).

```text
Avantages SaaS pour la NOAA :
- …
```

### 2.2 Modèle de déploiement & risques

- Modèle retenu : **cloud public SaaS** (Google Apps / Workspace).

Répondez :

1. Quels sont les **risques perçus** en choisissant une suite SaaS publique (sécurité, souveraineté, dépendance fournisseur) ?  
2. Comment peut‑on les **mitiger** (clauses contractuelles, certifications, options de résidence des données, chiffrement, réversibilité) ?

```text
Risques SaaS & moyens de mitigation pour la NOAA :
- …
```

---

## Phase 3 – Cadrage sécurité & GRC (25 min)

### 3.1 Exigences sécurité & conformité

Pour une agence comme la NOAA, cochez / complétez les exigences majeures :

- [ ] Chiffrement des données au repos / en transit.
- [ ] Authentification forte (MFA) pour les agents et admin.
- [ ] Journaux d’accès et d’activité détaillés (audit).
- [ ] Gestion des identités centralisée (fédération, SSO).
- [ ] Respect de normes / certifications (ex. FedRAMP, ISO, SOC…).
- [ ] Archivage légal des e‑mails pour des durées définies.
- [ ] Protection contre le phishing / malware / spam.

```text
Exigences / contrôles prioritaires :
- …
```

### 3.2 Zero Trust & contrôle des accès

Décrivez comment appliquer des **principes Zero Trust** pour cette solution SaaS :

- Séparation des rôles (admin / user).
- Limitation des accès depuis certains pays / réseaux.
- Vérification continue du terminal (PC géré vs perso).
- Conditions d’accès (Conditional Access).

```text
Idées pour une approche Zero Trust côté NOAA :
- …
```

---

## Phase 4 – Plan de migration fonctionnelle (30 min)

### 4.1 Périmètre de migration

Listez les briques à migrer vers la suite collaborative :

- [ ] Messagerie (e‑mail)
- [ ] Messagerie instantanée / chat
- [ ] Visioconférence
- [ ] Calendriers partagés
- [ ] Stockage & partage de documents
- [ ] Autres (intranet, formulaires, workflows…)

```text
Périmètre exact de notre scénario :
- …
```

### 4.2 Stratégie de migration (par vagues)

Proposez un plan en vagues (phases) :

- Vague 1 : pilote (petit groupe, direction, IT, early adopters…)
- Vague 2 : certains départements
- Vague 3 : généralisation à l’ensemble de l’agence

Pour chaque vague, précisez :

- Volume approximatif d’utilisateurs.
- Données migrées (tout l’historique ou partiel ?).
- Accompagnement (formation, support, communication).
- Critères de succès avant de passer à la vague suivante.

```text
Plan de migration par vagues :
- Vague 1 :
- Vague 2 :
- Vague 3 :
```

---

## Phase 5 – Technique de migration (données & identités) (20–25 min)

### 5.1 Migration des boîtes mail & calendriers

Répondez :

1. Quelles options techniques pensez‑vous utiliser pour migrer les **e‑mails et calendriers** (connecteurs, IMAP, outils de migration fournis) ?  
2. Gardez‑vous **tout l’historique** ou seulement une partie ? Quels impacts (coûts, perfs, expérience utilisateur, obligations légales) ?

```text
Stratégie de migration mail / calendriers :
- …
```

### 5.2 Gestion des identités & des groupes

Comment gérez‑vous :

- La **synchronisation** des identités (AD / LDAP interne → Google / IdP SaaS) ?
- Les **groupes / listes de diffusion** existants ?
- La **gestion du départ / arrivée** des agents (joiner/mover/leaver) ?

```text
Stratégie IAM pour la NOAA :
- …
```

---

## Phase 6 – Conduite du changement & formation (20 min)

La réussite de ce type de projet dépend énormément de l’**adoption par les utilisateurs**.

Répondez :

1. Quels **profils d’utilisateurs** sont les plus impactés (scientifiques sur le terrain, administratifs, direction, support…) ?  
2. Quels **formats de formation** proposez‑vous (MOOC interne, live, vidéos, fiches pratiques, ambassadeurs) ?  
3. Quels **messages clés** pour le sponsoring exécutif (bénéfices, risques, engagements de sécurité) ?

```text
Plan de conduite du changement :
- Profils ciblés :
- Actions de formation :
- Messages clés / communication :
```

---

## Phase 7 – FinOps & gains attendus (15 min)

### 7.1 Avant / après

En groupe, estimez qualitativement :

- Les grands **postes de coûts** avant migration (serveurs mail, stockage, licences, administration, énergie…).  
- Les **coûts après migration** (abonnements SaaS, connectivité, support, formation).

```text
Comparatif coûts (haut niveau) :
- Avant :
- Après :
```

### 7.2 Indicateurs de suivi

Quels KPIs FinOps / opérationnels mettez‑vous en place :

- Coût par utilisateur / par mois.
- Taux d’utilisation des fonctionnalités collaboratives.
- Réduction des incidents / tickets liés à la messagerie.
- Satisfaction utilisateur.

```text
KPIs de suivi & revue :
- …
```

---

## Phase 8 – Synthèse & restitution (5–10 min par groupe)

Chaque groupe prépare un **pitch de 3–5 minutes** :

1. Situation de départ & contraintes gouvernementales.  
2. Choix de la solution cloud et principaux **contrôles de sécurité / conformité**.  
3. Stratégie de migration (vagues, technique, accompagnement).  
4. Bénéfices attendus (collaboration, coûts, simplification IT) et risques résiduels.

L’objectif est de démontrer que vous savez **transposer la démarche d’adoption cloud** à un cas réel de migration SaaS dans le secteur public, en intégrant les dimensions : **stratégie, sécurité, GRC, FinOps, conduite du changement**.
