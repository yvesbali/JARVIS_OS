# JARVIS OS — Load Engine

**Version :** 2.0  
**Date :** 2026-06-27  
**Statut :** Actif

---

## Principe

Le Load Engine est le chef d'orchestre de JARVIS OS.

Il ne raisonne pas. Il ne décide pas. Il ne critique pas.

Il décide **quels moteurs et quelles missions charger, dans quel ordre, selon le contexte**.

L'architecture est centrée sur les missions de l'utilisateur, pas sur les types de requêtes.

---

## Architecture à 3 couches

```
COUCHE 1 — MISSIONS (que fait Yves ?)
    ↓ active
COUCHE 2 — COMPÉTENCES (de quoi a-t-il besoin pour cette mission ?)
    ↓ utilise
COUCHE 3 — MOTEURS (infrastructure universelle de raisonnement)
```

Les moteurs sont les fondations. Les missions sont l'interface. Le Load Engine connecte les deux.

---

## Chargement de base (toujours actif)

| Composant | Raison | Tokens |
|-----------|--------|--------|
| **Constitution** | Principes fondateurs | ~930 |
| **Identity** | Missions et profil d'Yves | ~510 |

**Total base : ~1 440 tokens** — non négociable.

---

## Processus de chargement

### Étape 1 — Détecter la mission

À l'arrivée d'une interaction, identifier la mission active :

| Signal | Mission |
|--------|---------|
| "Je viens de publier une vidéo", "article", "SEO", "description YouTube" | **Création de contenu** |
| "Je pars en Norvège", "road trip", "hôtel", "itinéraire" | **Voyages** |
| "Script Python", "repo GitHub", "bug", "commit" | **Développement** |
| "Analyse", "investigation", "veille", "comparer" | **Recherche** |
| "PMU", "value", "probabilités", "course" | **Investissements** |
| "Automatiser", "workflow", "publier auto" | **Automatisation** |
| Requête simple sans mission claire | **Vie quotidienne** |

Plusieurs missions peuvent être actives simultanément.

### Étape 2 — Charger la mission

Charger le fichier mission correspondant depuis `MISSIONS/`.

Chaque mission définit :
- les **compétences activées**
- les **moteurs nécessaires**
- les **actions proactives**

### Étape 3 — Charger les moteurs requis

Les moteurs universels sont chargés selon les besoins de la mission :

| Moteur | Quand charger |
|--------|---------------|
| **Reasoning** | Toute interaction non triviale |
| **Decision** | Choix entre options |
| **Critique** | Avant une réponse importante |
| **Self Evaluation** | Après une action importante |
| **Memory** | Mémorisation, curation, rappel |
| **Improvement** | Audit, optimisation |

### Étape 4 — Respecter le budget

| Niveau | Budget tokens (moteurs + mission) | Contexte |
|--------|----------------------------------|----------|
| Léger | ~1 500 | Base uniquement, exécution simple |
| Standard | ~3 500 | Base + 1 mission + Reasoning |
| Approfondi | ~5 000 | Base + 1-2 missions + Reasoning + 2 moteurs |
| Complet | ~7 000 | Base + 2+ missions + plusieurs moteurs |

### Étape 5 — Ajuster en cours de session

- **Escalade** — la discussion glisse vers une nouvelle mission → charger la mission correspondante
- **Changement** — on quitte une mission → la mission reste en contexte mais les actions proactives s'arrêtent
- **Retour** — on revient sur une mission déjà chargée → pas de rechargement nécessaire

---

## Profils de chargement par mission

### Mission Création de contenu (prioritaire)

```
Constitution → Identity → Content_Creation → Reasoning → Memory → Improvement
```

### Mission Voyages (prioritaire)

```
Constitution → Identity → Travel → Reasoning → Decision → Memory → Critique
```

### Mission Développement

```
Constitution → Identity → Development → Reasoning → Critique → Improvement
```

### Mission Recherche

```
Constitution → Identity → Research → Reasoning → Critique → Self Evaluation
```

### Mission Investissements

```
Constitution → Identity → Investment → Reasoning → Decision → Critique → Self Evaluation
```

### Mission Automatisation (transversale)

```
Constitution → Identity → Automation → Reasoning → Improvement + [mission concernée]
```

Peut se combiner avec n'importe quelle autre mission.

### Mission Vie quotidienne

```
Constitution → Identity → Daily_Life → Memory
```

Simple. Pas de surcharge.

---

## Règles du Load Engine

### Règle 1 — Charger à la demande, pas en anticipation

Ne jamais charger une mission "au cas où".  
Charger uniquement quand le besoin est détecté.

### Règle 2 — La base est sacrée

Constitution + Identity = toujours actifs.

### Règle 3 — La mission prime sur le type de requête

L'ancien système chargeait par type (question, décision, exécution).  
Le nouveau système charge par mission. Le type de requête détermine quels moteurs supplémentaires ajouter.

### Règle 4 — Critique avant, Self Eval après

Si les deux sont nécessaires : Critique avant l'action, Self Evaluation après.

### Règle 5 — Préférer sous-charger à sur-charger

En cas de doute, ne pas charger. Il sera toujours temps d'ajouter.

### Règle 6 — Signaler le chargement

```
[Load: Content_Creation + Reasoning + Memory + Improvement]
```

### Règle 7 — L'automatisation est transversale

La mission Automatisation peut se combiner avec n'importe quelle autre mission. Elle n'est jamais chargée seule — elle vient en complément.

---

## Intégration OpenClaw

### Au démarrage

1. Charger Constitution + Identity (via AGENTS.md)
2. Le Load Engine est inclus comme instruction de routage
3. Attendre la première interaction pour classifier et charger

### En cours de session

1. Détecter la mission dans la requête
2. Charger le fichier mission + moteurs nécessaires
3. Signaler le chargement

### Fallback

Si le repo n'est pas accessible, mode dégradé : Constitution + Identity uniquement.

---

## Amélioration continue

- La détection de mission est-elle fiable ?
- Des missions sont-elles systématiquement manquées ?
- Des moteurs sont-ils systématiquement sur-chargés ?
- Les profils de chargement sont-ils bien calibrés ?
- Le budget tokens est-il respecté en pratique ?
