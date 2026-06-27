# JARVIS OS — Planning Engine

**Version :** 1.0  
**Date :** 2026-06-27  
**Statut :** Actif

---

## Principe

Planifier, c'est transformer un objectif en séquence d'actions exécutables.

Un plan n'est pas une prédiction. C'est une feuille de route qui sera ajustée en cours de route.

---

## Processus de planification

### 1. Définir l'objectif

- **Objectif principal** — qu'est-ce qu'on veut accomplir ?
- **Critères de succès** — comment saura-t-on que c'est terminé et réussi ?
- **Contraintes** — temps, ressources, budget, technologies
- **Non-objectifs** — ce qu'on ne cherche PAS à faire (aussi important que l'objectif)

### 2. Décomposer en étapes

Chaque étape doit être :

- **Atomique** — une seule action ou un seul livrable
- **Vérifiable** — on peut dire "fait" ou "pas fait" sans ambiguïté
- **Estimable** — on peut estimer le temps et l'effort nécessaires

### 3. Identifier les dépendances

- Quelles étapes doivent être terminées avant d'autres ?
- Y a-t-il des étapes parallélisables ?
- Y a-t-il des goulots d'étranglement ?

### 4. Estimer les temps

Pour chaque étape :

- Estimation optimiste
- Estimation réaliste
- Estimation pessimiste

Privilégier l'estimation réaliste pour la planification.

### 5. Identifier les risques

Pour chaque étape :

- Qu'est-ce qui peut mal tourner ?
- Quelle est la probabilité ?
- Quel est l'impact ?
- Quelle est la mitigation ?

Les risques élevés doivent avoir un plan B.

### 6. Séquencer

Organiser les étapes en respectant :

- les dépendances
- les priorités
- les contraintes de temps
- les risques (traiter les plus risqués en premier quand c'est possible)

### 7. Définir les jalons

Des points de vérification intermédiaires où :

- on valide que tout est sur la bonne voie
- on peut ajuster le plan si nécessaire
- on peut décider de continuer, pivoter ou abandonner

---

## Format de plan

```markdown
# Plan : [nom du projet]

## Objectif
[description]

## Critères de succès
- [critère 1]
- [critère 2]

## Non-objectifs
- [ce qu'on ne fait pas]

## Étapes

| # | Étape | Dépendances | Temps estimé | Risque | Statut |
|---|-------|-------------|-------------|--------|--------|
| 1 | ... | — | ... | ... | ⬜ |
| 2 | ... | 1 | ... | ... | ⬜ |

## Jalons
- [jalon 1] → après étape N
- [jalon 2] → après étape M

## Risques majeurs
- [risque] → mitigation : [plan]
```

---

## Principes de planification

### Règle 1 — Plans imbriqués

Un plan peut contenir des sous-plans.

Mais chaque niveau reste lisible : 5 à 9 étapes maximum par plan.

Au-delà, décomposer en sous-plans.

### Règle 2 — Ajuster en cours de route

Un plan qui ne change pas est un plan qui n'est pas utilisé.

À chaque jalon :
- Ce qui est fait est-il conforme aux attentes ?
- Les hypothèses sont-elles toujours valides ?
- Faut-il ajuster les étapes suivantes ?

### Règle 3 — Commencer par le plus risqué

Quand c'est possible, traiter d'abord les étapes les plus incertaines.

Échouer vite = apprendre vite.

### Règle 4 — Ne pas sur-planifier

Planifier le niveau de détail nécessaire, pas plus.

Pour les étapes lointaines, rester macro.

La précision augmente en approchant de l'exécution.

---

## Amélioration continue

- Les estimations de temps sont-elles réalistes ? (comparer prévu vs réel)
- Les risques identifiés sont-ils les bons ?
- Les jalons sont-ils aux bons moments ?
- La granularité des étapes est-elle adéquate ?

---

## Évolutions futures (V2+)

- Planification avec allocation de ressources
- Gantt automatique
- Détection de retards et réplannification
- Templates de plans par type de projet
