# Template — Checklist de review

> **Usage humain** : remplissez cette checklist pendant votre review d'un diff d'agent (module 4).
> **Usage agent (révision croisée)** : collez le bloc « Prompt de review » en bas de fichier dans le prompt d'un agent reviewer, en lecture seule.

---

## Mission reviewée

- Identifiant : `FICHE-XX`
- Branche : `feature/…`
- Diff : `git diff main...HEAD --stat` → [N] fichiers, [N] lignes
- Auteur du diff : [agent / humain]

---

## 1. Périmètre

- [ ] Tous les fichiers modifiés sont dans le périmètre autorisé
- [ ] Aucun fichier hors périmètre touché (« refactorisation au passage »)
- [ ] Aucune dépendance ajoutée sans justification dans le résumé
- [ ] Le nombre de lignes est proportionné à la mission

## 2. Les 7 signatures du code d'agent

- [ ] **Sur-ingénierie** : pas d'abstraction/factory/interface pour un seul usage
- [ ] **Hallucination d'API** : fonctions, options, paramètres vérifiés (types, docs)
- [ ] **Tests vidés/supprimés** : aucune assertion retirée, aucun test modifié pour passer
- [ ] **Refactorisation hors périmètre** : aucune
- [ ] **Dépendances gratuites** : aucune lib ajoutée pour 3 lignes
- [ ] **Code mort/copié** : pas d'imports inutilisés, de blocs commentés, de doublons
- [ ] **Commentaires bavards** : les commentaires expliquent le « pourquoi », pas le « quoi »

## 3. Sécurité

- [ ] Aucun secret en dur (clé, mot de passe, token) — `grep` sur le diff
- [ ] Pas de concaténation dans SQL / shell / HTML (`innerHTML`)
- [ ] Nouvelles dépendances vérifiées (réputation, `npm audit` / `pip-audit`)
- [ ] Pas de permissions élargies (endpoint, route, fichier) au-delà du nécessaire
- [ ] Entrées utilisateur validées (types, bornes, échappement)

## 4. Tests

- [ ] Les tests couvrent : cas nominal, cas limite, cas d'erreur
- [ ] Aucun test creux (assertion vide, test qui teste l'implémentation)
- [ ] Test ultime fait : retirer la fonctionnalité → au moins un test échoue
- [ ] Les tests existants n'ont pas été modifiés (ou justification écrite acceptée)

## 5. Validation machine (relancée par MOI, pas confiance dans le « déjà fait »)

- [ ] `make test` → verts
- [ ] `make lint` → propre
- [ ] `make build` / typecheck → OK
- [ ] CI verte (si configurée)

## 6. Validation manuelle

- [ ] Parcours principal testé à la main (5 minutes d'usage réel)
- [ ] Cas d'erreur testé à la main (réponse attendue : pas de 500 brut)

## 7. Décision

- [ ] **Merge** — tout est vert
- [ ] **Corrections demandées** — liste numérotée ci-dessous (fichier, problème, correction, référence DoD)

### Liste de corrections

1. `[fichier]` : [problème] → [correction demandée] (DoD : [référence])
2. …

---

## Prompt de review (révision croisée entre agents)

> Collez ce bloc dans un agent reviewer. Il ne modifie JAMAIS le code : il produit une liste.

```
Rôle : reviewer senior, tu ne modifies aucun fichier. Tu travailles en lecture seule.
Objectif : vérifier que le diff de la branche feature/[identifiant] respecte la fiche
FICHE-XX et la checklist templates/review-checklist.md (7 signatures, sécurité, tests).
Périmètre : lecture seule. Interdit : éditer, committer, lancer autre chose que les tests.
Contraintes : ne signale que des problèmes concrets, fichier par fichier.
Définition de fini : tu as couvert les 4 sections (périmètre, signatures, sécurité, tests)
et produit la liste complète.
Livrables : liste numérotée : fichier, problème, correction proposée. Max 15 items.
Si tout est bon, écris : « Rien à corriger. »
Format : réponse en français, max 400 mots.
```
