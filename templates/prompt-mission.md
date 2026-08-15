# Template — Prompt de mission

> **Usage** : copiez ce fichier, remplacez les zones entre `[crochets]`, envoyez le résultat à votre agent de code.
> **Règle d'or** : remplissez la fiche de tâche (`spec-fiche-tache.md`) AVANT de rédiger ce prompt. Si vous ne pouvez pas remplir la fiche, la mission n'est pas prête.

---

## MISSION [IDENTIFIANT] — [TITRE COURT]

### 1. Rôle & contexte
Tu es développeur senior sur le repo `[nom-du-repo]`.
Stack : `[langage, frameworks, versions, gestionnaire de paquets — reprendre l'AGENTS.md]`.
Tu travailles sur la branche `feature/[identifiant]` (déjà créée, basée sur `main`).
Contexte utile : `[2-3 phrases max : ce que fait le projet, où se situe cette mission]`.

### 2. Objectif (mesurable)
`[Une phrase : le comportement attendu, observable. Le meilleur objectif cite un test, une commande ou un critère précis.]`
Critère de réussite : `[ex. « le parcours complet passe les 5 tests d'intégration de tests/paiement.test.js »]`.

### 3. Périmètre
- **Autorisé** : `[fichiers, dossiers, zones où tu peux écrire]`.
- **Interdit** : `[fichiers à ne pas toucher, commandes à ne pas lancer, dépendances à ne pas ajouter]`.
- En cas de doute sur le périmètre : demande, ne décide pas seul.

### 4. Contraintes techniques
- `[ex. clé API lue depuis process.env, jamais en dur]`
- `[ex. erreurs retournées en JSON {error: "…"}]`
- `[ex. style : async/await, TypeScript strict]`
- `[ex. accessibilité, i18n, performance]`

### 5. Définition de fini (DoD)
Tous les points suivants doivent être vérifiés avant de déclarer la mission terminée :
- [ ] `[ex. les 5 tests d'intégration passent]`
- [ ] `npm run lint` (ou `make lint`) passe
- [ ] `npm run typecheck` (ou équivalent) passe
- [ ] `[ex. la migration est appliquée]`
- [ ] Aucun test existant modifié (sauf justification écrite)
- [ ] Résumé des changements + risques fournis en fin de mission

### 6. Livrables
- Un commit atomique par étape logique, messages en conventional commits (`feat:` / `fix:` / `test:` / `refactor:`).
- Un diff résumé à relire : `git diff main...HEAD --stat` + liste des fichiers hors périmètre (s'il y en a).
- **Ne pas pousser** sur la branche distante : je pousse après review.

### 7. Format de sortie
Réponse finale en français, **max 250 mots**, structurée ainsi :
1. Ce qui a été fait (avec la liste des commits)
2. Ce qui n'a pas été fait (et pourquoi)
3. Les risques restants / points d'attention pour la review
4. Les tests que tu as lancés et leurs résultats

---

## Exemple rempli (à supprimer avant usage)

**Mission PAIEMENT-STRIPE — ajouter le paiement par carte**

1. **Rôle** : développeur senior sur le repo `caissevite` (Node 20, Express, SQLite). Branche `feature/paiement-stripe` (déjà créée).
2. **Objectif** : un client peut payer une commande par carte. Critère de réussite : le parcours complet (créer la commande → payer → confirmer) passe les 5 tests d'intégration de `tests/paiement.test.js`.
3. **Périmètre** : autorisé — `src/paiement/`, `src/routes/`, `db/migrations/`, `tests/paiement.test.js` ; interdit — `src/front/`, `package.json` (sauf ajout de `stripe`), modifier les tests existants.
4. **Contraintes** : clé API Stripe lue depuis `process.env.STRIPE_SECRET_KEY` (jamais en dur) ; erreurs en JSON `{error: "…"}` ; async/await.
5. **DoD** : 5 tests verts · lint ✓ · typecheck ✓ · migration appliquée · aucun test existant modifié · résumé des risques.
6. **Livrables** : commits atomiques en conventional commits, diff résumé.
7. **Format** : réponse en français, 250 mots max : fait / non fait / risques / tests lancés.

---

## Checklist avant envoi
- [ ] L'objectif contient un critère observable (test, commande, comportement précis)
- [ ] Le périmètre « interdit » existe et cite des fichiers précis
- [ ] La DoD contient au moins 4 conditions vérifiables
- [ ] Une seule mission par prompt (sinon : découper)
- [ ] Le format de sortie est défini (langue, longueur, structure)
- [ ] La fiche de tâche (`spec-fiche-tache.md`) est remplie et jointe en référence
