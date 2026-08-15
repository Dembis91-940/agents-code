# Template — Rétrospective de mission

> **Usage** : remplissez ce bilan après CHAQUE mission (10 minutes max). C'est la boucle
> d'amélioration qui transforme la pratique en expertise — et qui fait grossir votre AGENTS.md.

---

## Mission

- Identifiant : `FICHE-XX` — [titre]
- Date : [JJ/MM/AAAA]
- Agent(s) utilisé(s) : [nom + modèle]
- Branche : `feature/…` → merge le [date] par [vous]

---

## 1. Chiffres

| Mesure | Estimation | Réel | Écart |
|---|---|---|---|
| Temps de pilotage (fiche + prompt + review) | [h] | [h] | |
| Temps d'exécution agent | [min] | [min] | |
| Tokens contexte (entrée) | | [si dispo] | |
| Tokens sortie | | [si dispo] | |
| Coût de la mission | [€] | [€] | |
| Nombre d'allers-retours de correction | 1 | [n] | |
| Fichiers modifiés / hors périmètre | | [n] / [n] | |

## 2. Ce qui a marché

- [ce que l'agent a bien fait, ce qui dans votre fiche/prompt a bien fonctionné]
- …

## 3. Ce qui a coincé

- [erreurs de l'agent, ambiguïtés du prompt, périmètre dépassé, tests…]
- …

## 4. Décisions pour la suite

- [règle à adopter, outil à configurer, template à ajuster…]
- …

## 5. Règles à ajouter à AGENTS.md

Si cette mission a révélé un piège du projet ou une convention manquante, ajoutez-la à
`AGENTS.md` (section « Pièges connus » ou « Règles absolues ») pour que tous les agents
futurs en profitent :

- [ ] Règle ajoutée : [texte court]
- [ ] Règle ajoutée : [texte court]

## 6. Verdict

- [ ] Mission terminée proprement (DoD remplie, merge validé)
- [ ] Mission terminée avec corrections
- [ ] Mission abandonnée — raison : [ ]

**Leçon en une phrase :** [ce que cette mission vous a appris sur le pilotage]

---

## Tableau de bord (à mettre à jour après chaque mission)

| Mission | Coût réel | Allers-retours | Hors périmètre | Leçon |
|---|---|---|---|---|
| FICHE-01 | | | | |
| FICHE-02 | | | | |
| … | | | | |

**Tendance à surveiller** : si le coût moyen ou le nombre d'allers-retours ne baisse pas
sur 3 missions, retournez au module 3 (structure du prompt) et au module 2 (AGENTS.md).
