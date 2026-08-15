# Template — Fiche de tâche

> **Usage** : remplissez une fiche par mission, AVANT de rédiger le prompt (`prompt-mission.md`).
> La fiche est votre réflexion ; le prompt est son expression. Si vous ne pouvez pas la remplir en 10 minutes, la mission n'est pas mûre : découpez-la.

---

## FICHE-XX — [Titre court]

| Champ | Contenu |
|---|---|
| **Identifiant** | `FICHE-XX` (ex. FICHE-03) |
| **Titre** | [nom court, verbe + objet : « ajouter l'endpoint GET /orders »] |
| **Priorité** | haute / moyenne / basse |
| **Dépend de** | [identifiants des fiches qui doivent être terminées avant — sinon « aucune »] |
| **Estimation humaine** | [X h — si plus de 2 h, découper] |
| **Statut** | à faire / en cours / review / terminé |

---

### 1. Objectif (mesurable)
[Le comportement attendu en une phrase, avec un critère observable : test, commande, parcours précis.]
> Ex. : « Un client peut consulter la liste de ses commandes via GET /orders. Critère : les 3 tests d'intégration de tests/orders.test.js passent. »

### 2. Contexte
[2-3 phrases : où se situe cette tâche dans le projet, ce qui existe déjà, ce qui va changer.]
> Ex. : « Le modèle Order existe (FICHE-01). La route /api/orders est vide. L'auth est en place (FICHE-02) : le middleware requireAuth est disponible. »

### 3. Périmètre
- **Autorisé** : [fichiers / dossiers / commandes]
- **Interdit** : [fichiers / commandes / dépendances / modifications]

### 4. Contraintes techniques
- [style, sécurité, perf, i18n, accessibilité…]

### 5. Définition de fini (DoD)
- [ ] [condition 1 vérifiable]
- [ ] [condition 2 vérifiable]
- [ ] `make lint` passe
- [ ] `make typecheck` (ou équivalent) passe
- [ ] Aucun test existant modifié (sauf justification écrite)
- [ ] Résumé des changements + risques fourni

### 6. Livrables attendus
- [commits en conventional commits, diff résumé, tests lancés…]

### 7. Notes pour le reviewer
[Points sensibles à vérifier en priorité : gestion d'erreur, secret, périmètre…]

---

## Modèle de graphe de mission (multi-agents)

| Vague | Fiches (parallèle si fichiers disjoints) | Jalon de validation |
|---|---|---|
| Vague 1 | FICHE-01, FICHE-02 | migration + tests rouges OK |
| Vague 2 | FICHE-03 (dépend FICHE-01) | API verte |
| Vague 3 | FICHE-04, FICHE-05 (dépendent FICHE-02/03) | front OK |
| Vague 4 | FICHE-06 review croisée | tout vert, merge |
