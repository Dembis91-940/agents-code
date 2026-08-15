# Pilotez vos agents de code

Formation 2026 : **piloter les agents de code** (CLI, IDE, autonomes) — choisir, cadrer,
missionner, vérifier, sécuriser, orchestrer. Pour devs, alternants et solopreneurs tech.

> Promesse : en 2 h, vous déléguez une mission complète à un agent de code sans perdre le contrôle.

## Offres (livraison par email)

| Offre | Prix | Contenu |
|---|---|---|
| **La formation** | 27 € | `formation-agents-code.md` (6 modules, exemples, exercices, checklist, glossaire) |
| **Pack complet** ⭐ Le plus choisi | 47 € | Formation + les 5 templates de prompts (`templates/`) |
| **Pack Mentor** | 97 € | Pack complet + session individuelle d'1 h (réservée via EmailJS) |

## Contenu des livrables

- `index.html` — landing page de vente (design terracotta/crème éditorial, formulaire EmailJS réel, FAQ, offres)
- `formation-agents-code.md` — LA formation : 6 modules (choisir son agent, setup d'un repo, prompt de mission, review, garde-fou tests, équipe d'agents), leçon + exemple réel + exercice par module, checklist finale, glossaire, annexe templates
- `formation-agents-code.pdf` — la formation au format PDF (livrable final, ≈ 30 pages, généré depuis le Markdown source)
- `templates/` — 5 templates prêts à l'emploi :
  - `prompt-mission.md` — le prompt en 7 blocs (avec exemple rempli)
  - `spec-fiche-tache.md` — la fiche de réflexion avant mission (+ graphe multi-agents)
  - `review-checklist.md` — checklist de review humaine + prompt de révision croisée
  - `garde-fou-tests.md` — contrat de tests à coller dans chaque prompt + grille de cas
  - `retrospective.md` — bilan chiffré post-mission + tableau de bord
- `README.md` — ce fichier

## Stack technique

- **Page** : HTML/CSS/JS statique, zéro dépendance de build. Polices Google Fonts (Fraunces + JetBrains Mono), fallbacks système.
- **Commande EmailJS réelle** : `serviceId=service_cy1ytdb`, `templateId=template_xpo58cv`, `publicKey=8Pui4ZEqxW2jRVF7h`. Payload : `{site, name, email, question}` avec `question = "Commande : <offre>" (+ contexte)`.
- **Paiement** : virement ou message privé, instructions envoyées par email (pas de passerelle Stripe branchée — le formulaire est un formulaire de commande, pas un paiement en ligne).
- **Livraison** : PDF envoyés par email après réception du paiement. La formation source est en Markdown → conversion PDF à la demande (ex. `markdown-to-pdf`).

## Lancer en local

```bash
cd ~/Documents/livrables/agents-code
python3 -m http.server 8000
# puis ouvrir http://localhost:8000
```

Ou simplement ouvrir `index.html` dans un navigateur.

## Déploiement

Statique : GitHub Pages, Netlify, Vercel, ou tout hébergement statique. Ne pas déployer
ni publier tant que le paiement réel n'est pas branché — le formulaire EmailJS envoie
des commandes réelles vers la boîte du vendeur, il faut être prêt à traiter les paiements
(virement / message privé) avant de mettre la page en ligne.

## Notes de vente

- Le formulaire EmailJS est **réel** (zéro simulateur) : une commande soumise déclenche un email vers la boîte configurée sur le template `template_xpo58cv`.
- Prix affichés sur la page : 27 € / 47 € / 97 €.
- Garantie annoncée : remboursement 14 jours sans justification.
