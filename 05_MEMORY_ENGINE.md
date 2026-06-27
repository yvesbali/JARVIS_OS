# JARVIS OS — Memory Engine

**Version :** 1.0  
**Date :** 2026-06-27  
**Statut :** Actif

---

## Principe

La mémoire est ce qui transforme un outil en partenaire.

Sans mémoire, chaque interaction repart de zéro.  
Avec mémoire, chaque échange enrichit les suivants.

JARVIS OS gère trois niveaux de mémoire.

---

## 1. Mémoire de session

**Durée :** le temps d'une session active.

**Contenu :**
- le contexte de la conversation en cours
- les décisions prises dans la session
- les fichiers lus ou modifiés
- les commandes exécutées

**Règle :** Ne pas s'appuyer sur la mémoire de session au-delà de la session. Elle disparaît.

---

## 2. Mémoire court terme

**Durée :** jours à semaines.

**Support :** fichiers quotidiens (`memory/YYYY-MM-DD.md`).

**Contenu :**
- événements du jour
- tâches en cours
- décisions récentes
- observations

**Règle :** Écrire systématiquement ce qui mérite d'être retenu. Un fait non écrit est un fait oublié.

**Format :**
```markdown
# YYYY-MM-DD

## Événements
- [description factuelle]

## Décisions
- [décision] → raison : [justification]

## Tâches en cours
- [tâche] → statut : [en cours / bloqué / terminé]

## Observations
- [observation utile pour plus tard]
```

---

## 3. Mémoire long terme

**Durée :** permanente.

**Support :** `MEMORY.md` (fichier unique, curaté).

**Contenu :**
- principes validés
- préférences utilisateur
- leçons apprises
- patterns identifiés
- architecture décisions

**Règle :** C'est la mémoire distillée, pas le journal brut. On y transfère ce qui mérite de durer.

**Processus de curation :**
1. Périodiquement, relire les fichiers quotidiens
2. Identifier ce qui est obsolète → retirer
3. Identifier ce qui est pérenne → ajouter à MEMORY.md
4. Identifier ce qui est redondant → consolider

---

## Règles de gestion

### Écriture
- Toujours dater les entrées dans les fichiers quotidiens
- Toujours justifier les décisions enregistrées
- Toujours séparer les faits des opinions

### Lecture
- Charger MEMORY.md au démarrage de chaque session
- Ne pas charger les fichiers quotidiens sauf besoin
- Ne jamais supposer qu'une information est encore valide sans vérification

### Sécurité
- La mémoire longue peut contenir des informations sensibles
- Ne jamais exposer MEMORY.md dans des contextes partagés (groupes, sessions tierces)
- La mémoire est personnelle — elle appartient à la relation utilisateur-JARVIS

---

## Amélioration continue

Questions à se poser régulièrement :

- Y a-t-il des informations obsolètes dans MEMORY.md ?
- Des patterns récurrents méritent-ils d'être promus en principe ?
- La structure des fichiers quotidiens est-elle optimale ?
- La charge cognitive de la mémoire est-elle maîtrisée (taille de MEMORY.md) ?
- Des informations sont-elles dupliquées entre fichiers ?

---

## Évolutions futures (V2+)

- Index thématique de la mémoire
- Mémoire par projet (séparation des contextes)
- Mémoire partagée entre sessions
- Archivage automatique des entrées anciennes
- Résumé automatique des fichiers quotidiens
