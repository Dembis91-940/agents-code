# Template — Garde-fou tests (contrat de tests)

> **Usage** : collez la section « Contrat de tests » dans le bloc **Définition de fini** de chaque prompt de mission.
> Complétez la « Grille des cas à couvrir » dans la fiche de tâche pour les missions avec logique métier.

---

## Contrat de tests (à coller dans chaque prompt)

```
CONTRAT DE TESTS — règles non négociables :

1. Tu ne supprimes JAMAIS un test existant. Si un test te semble erroné,
   tu le signales dans ton résumé, sans le modifier.
2. Tu ne modifies JAMAIS un test pour le faire passer. Si un test échoue,
   tu corriges le code, pas le test.
3. Pour toute nouvelle fonctionnalité : tu écris d'abord les tests (qui
   échouent), tu montres le rouge, puis tu implémentes jusqu'au vert.
4. Un test doit échouer si la fonctionnalité casse. Les assertions vérifient
   le comportement (valeurs, statuts, effets), pas l'implémentation.
5. La suite COMPLÈTE passe : make test en entier (tests existants + nouveaux).
   Tu exécutes la suite complète, pas seulement tes nouveaux tests.
6. Tu indiques dans ton résumé : la liste exacte des commandes de test
   lancées et leurs résultats.
```

---

## Grille des cas à couvrir (à remplir par mission)

| # | Cas | Comportement attendu | Test (fichier) |
|---|---|---|---|
| 1 | Nominal | [ex. « une commande valide est créée, statut 201 »] | tests/… |
| 2 | Limite | [ex. « prix à 0 € → refusé »] | |
| 3 | Erreur | [ex. « payload vide → 400 {error: "…"} »] | |
| 4 | Sécurité | [ex. « utilisateur non authentifié → 401 »] | |
| 5 | Bord | [ex. « montant négatif → erreur »] | |
| 6 | Régression | [ex. « le parcours existant fonctionne toujours »] | |

**Règle** : chaque ligne de la grille doit exister dans les tests AVANT que l'agent implémente.

---

## Le test ultime (étalonnage de confiance)

Après chaque mission importante, vérifiez que le filet est réel :

1. Prenez une fonctionnalité livrée par l'agent.
2. Retirez (ou commentez) son implémentation dans le code.
3. Relancez la suite : **au moins un test doit échouer**.
4. Restaurez l'implémentation, relancez : tout vert.

Si aucun test n'échoue à l'étape 3, les tests sont creux — la fonctionnalité n'est pas protégée.
Ajoutez un test qui vérifie le comportement, puis refaites le test ultime.

---

## Rappel validation machine

- La validation est TOUJOURS relancée par l'humain : `make test && make lint && make build`.
- Le « j'ai lancé les tests » de l'agent est une information, jamais une preuve.
- La CI est l'arbitre final : rien ne merge sans elle (si configurée).
