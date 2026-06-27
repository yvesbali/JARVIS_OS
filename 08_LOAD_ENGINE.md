# JARVIS OS — Load Engine

**Version :** 1.0  
**Date :** 2026-06-27  
**Statut :** Actif

---

## Principe

Le Load Engine est le chef d'orchestre de JARVIS OS.

Il ne raisonne pas. Il ne décide pas. Il ne critique pas.

Il décide **quels moteurs charger, dans quel ordre, selon le contexte**.

Sans lui, les moteurs sont une bibliothèque morte.  
Avec lui, chaque interaction reçoit exactement le contexte nécessaire — ni plus, ni moins.

---

## Règle fondamentale

> **Ne jamais charger tout. Charger uniquement ce qui est nécessaire.**

Chaque token chargé sans nécessité est :
- un coût
- du bruit
- une perte de qualité potentielle

L'objectif du Load Engine est d'offrir la qualité maximale avec le minimum de contexte.

---

## Architecture de chargement

### Couche 0 — Base (toujours chargée)

| Moteur | Raison | Tokens |
|--------|--------|--------|
| **Constitution** | Principes fondateurs — sans eux, rien n'a de sens | ~930 |
| **Identity** | Qui est JARVIS — sans lui, le comportement est indéfini | ~510 |

**Total base : ~1 440 tokens**

La base est non négociable. Tout interaction JARVIS OS démarre avec ces deux moteurs.

---

### Couche 1 — Core (chargée pour toute interaction non triviale)

| Moteur | Raison | Tokens |
|--------|--------|--------|
| **Reasoning** | Processus de réflexion — le moteur central | ~1 630 |

**Total base + core : ~3 070 tokens**

Le Reasoning Engine n'est chargé que si l'interaction nécessite de raisonner (question, décision, analyse, problème).

Pour une exécution simple sans ambiguïté ("liste ce dossier", "crée ce fichier"), la base seule suffit.

---

### Couche 2 — Spécialisée (chargée selon le contexte)

| Moteur | Raison | Tokens | Quand charger |
|--------|--------|--------|---------------|
| **Decision** | Grille multicritères, niveaux de décision | ~1 290 | Choix entre options, décision à prendre |
| **Critique** | Biais, erreurs, contradictions | ~1 130 | Avant une réponse importante, analyse critique demandée |
| **Self Evaluation** | Confiance, cohérence, limites | ~965 | Après une action importante, validation de résultat |
| **Memory** | Gestion mémoire court/long terme | ~870 | Tâches de mémorisation, curation, rappel |
| **Improvement** | Amélioration continue, cycle OAPVI | ~1 180 | Après un projet, audit, optimisation |

---

### Couche 3 — Domaines (V2+, plugins)

| Moteur | Quand charger |
|--------|---------------|
| **PMU** | Question hippique, pronostic |
| **Python** | Développement, debug, script |
| **GitHub** | Repo, PR, issues, CI |
| **YouTube** | Vidéo, SEO, chaîne |
| etc. | Selon le domaine |

---

## Processus de chargement

### Étape 1 — Classifier la requête

À l'arrivée d'une interaction, classifier :

| Type | Description | Base | Core | Spécialisé |
|------|-------------|------|------|-----------|
| **Exécution** | Action simple, sans ambiguïté | ✅ | ❌ | ❌ |
| **Question factuelle** | Réponse directe, pas de décision | ✅ | ✅ | ❌ |
| **Analyse** | Comprendre, évaluer, comparer | ✅ | ✅ | Critique |
| **Décision** | Choisir entre options | ✅ | ✅ | Decision + Critique |
| **Planification** | Organiser, séquencer | ✅ | ✅ | Decision + Memory |
| **Audit / Amélioration** | Évaluer et améliorer | ✅ | ✅ | Critique + Self Eval + Improvement |
| **Mémorisation** | Enregistrer, rappeler, curater | ✅ | ❌ | Memory |
| **Domaine spécialisé** | PMU, Python, GitHub, etc. | ✅ | ✅ | Domaine + moteurs pertinents |

### Étape 2 — Composer le contexte

À partir de la classification, assembler les moteurs nécessaires dans l'ordre :

```
Constitution → Identity → [Reasoning] → [Spécialisés selon le type]
```

L'ordre compte. La Constitution est lue en premier. L'Identity ensuite. Puis le Reasoning. Puis les moteurs spécialisés.

### Étape 3 — Respecter le budget

| Niveau d'interaction | Budget tokens (moteurs) | Moteurs |
|---------------------|------------------------|---------|
| Léger | ~1 500 | Base uniquement |
| Standard | ~3 000 | Base + Core |
| Approfondi | ~4 500 | Base + Core + 1-2 spécialisés |
| Complet | ~6 000 | Base + Core + 3+ spécialisés |
| Expert | ~7 500+ | Tous les moteurs pertinents |

Le budget n'est pas une limite stricte — c'est un guide. Si un moteur est nécessaire, on le charge. Mais on ne charge jamais un moteur "au cas où".

### Étape 4 — Ajuster en cours de session

Si la conversation change de nature :

- **Escalade** — la discussion passe d'une question factuelle à une décision → charger Decision + Critique
- **Changement de domaine** — on passe de Python à PMU → décharger Python, charger PMU
- **Simplification** — la discussion se résout en exécution simple → les moteurs spécialisés restent en mémoire mais ne guident plus le comportement

Le rechargement en cours de session est un mécanisme de dernier recours. Mieux vaut bien classifier au départ.

---

## Profils de chargement

### Profil par défaut — Équilibré

```
Constitution + Identity + Reasoning
```

Suffisant pour 80% des interactions.

### Profil décision

```
Constitution + Identity + Reasoning + Decision + Critique
```

Pour les choix importants.

### Profil audit

```
Constitution + Identity + Reasoning + Critique + Self Evaluation + Improvement
```

Pour les revues, audits, améliorations.

### Profil mémoire

```
Constitution + Identity + Memory
```

Pour les tâches de mémorisation et curation.

### Profil domaine (V2+)

```
Constitution + Identity + Reasoning + [Domaine] + [moteurs pertinents]
```

Exemples :
- **PMU** : Constitution + Identity + Reasoning + Decision + Critique + PMU
- **Python** : Constitution + Identity + Reasoning + Python + Improvement
- **YouTube** : Constitution + Identity + Reasoning + YouTube + Improvement

---

## Intégration OpenClaw

### Mécanisme

1. Au démarrage d'une session, OpenClaw charge la base (Constitution + Identity) via AGENTS.md
2. Le Load Engine lui-même est inclus dans AGENTS.md comme instruction de routage
3. À chaque nouvelle interaction, JARVIS classe la requête et charge les moteurs nécessaires en les lisant depuis le repo local
4. Les moteurs chargés sont ajoutés au contexte de la session en cours

### Implémentation pratique

Dans AGENTS.md, ajouter :

```markdown
## JARVIS OS — Chargement

Toujours charger au démarrage :
- JARVIS_OS/00_CONSTITUTION.md
- JARVIS_OS/01_IDENTITY.md

Pour chaque interaction, classifier et charger les moteurs nécessaires selon JARVIS_OS/08_LOAD_ENGINE.md.

Les moteurs sont dans : JARVIS_OS/
```

### Fallback

Si le repo n'est pas accessible, JARVIS fonctionne en mode dégradé avec uniquement la base (Constitution + Identity). Le comportement est réduit mais reste cohérent.

---

## Règles du Load Engine

### Règle 1 — Charger à la demande, pas en anticipation

Ne jamais charger un moteur "au cas où on en aurait besoin".

Charger uniquement quand le besoin est identifié.

### Règle 2 — La base est sacrée

Constitution et Identity sont toujours chargés. Pas d'exception.

### Règle 3 — Le Reasoning est le moteur pivot

Si un moteur spécialisé est chargé, le Reasoning Engine l'est aussi.

Reasoning est le cadre dans lequel les moteurs spécialisés opèrent.

### Règle 4 — Critique avant, Self Eval après

Si les deux sont nécessaires :
- Critique est chargé avant l'action
- Self Evaluation est appliqué après

L'ordre temporel est fondamental — c'est ce qui les distingue.

### Règle 5 — Préférer sous-charger à sur-charger

En cas de doute sur la nécessité d'un moteur, ne pas le charger.

Il sera toujours temps de le charger en cours de session si le besoin apparaît.

### Règle 6 — Documenter le chargement

Quand des moteurs sont chargés au-delà de la base, le signaler discrètement :

```
[Load: Reasoning + Decision + Critique]
```

Cela permet à l'utilisateur de comprendre quel contexte est actif.

---

## Amélioration continue

- Les profils de chargement sont-ils bien calibrés ?
- Des moteurs sont-ils systématiquement sur-chargés ?
- Des moteurs sont-ils systématiquement sous-chargés (manqués) ?
- Le budget tokens est-il respecté en pratique ?
- La classification des requêtes est-elle fiable ?

---

## Évolutions futures (V2+)

- Chargement dynamique automatique (IA classifie la requête et charge sans intervention)
- Déchargement intelligent (retirer les moteurs devenus inutiles en cours de session)
- Profils personnalisés par utilisateur
- Compression automatique des moteurs (résumer un moteur en 50 tokens quand le budget est serré)
- Métriques de qualité par profil de chargement
