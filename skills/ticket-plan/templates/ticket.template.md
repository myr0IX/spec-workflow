# <Feature> — <une ligne d'objectif>

⏱️ **Estimation : <N jours>** (<résumé des grosses pièces : N endpoints + migration + tests bout-en-bout...>)

## Objectif

<!-- 2-4 phrases : à la fin de ce ticket, le client peut faire X en appelant Y.
Mentionne les dépendances sur d'autres tickets s'il y en a. -->

Contexte : <!-- ce qui existe déjà (webapp, service tiers...) et ce que ce ticket
expose/durcit/centralise — pas une réinvention. -->

**Décisions produit tranchées :**
<!-- Une par ligne, format court, chacune traçable à une entrée TRANCHÉ de questions.md.
Ne pas réexpliquer le raisonnement complet ici — juste la décision, le détail est dans
questions.md. -->
- <décision 1>
- <décision 2>

## À lire avant de commencer

<!-- Fichiers/routes qui donnent le contexte nécessaire, avec ce qu'il faut en retenir
en une ligne chacun. Inclure le précédent similaire si un existe. -->

- `<fichier>` — <ce qu'il faut en retenir>

## Fichiers à créer / modifier

```
<chemin>                          ← <nouveau|étendre|supprimer> (<ce que ça fait>)
```

<!-- Ajouter une section risque (🚨) seulement si un vrai risque sécu/données existe
(ex: SSRF si le client fournit une URL). Ne pas en inventer un s'il n'y en a pas. -->

<!-- Ajouter une section piège (🪤) seulement s'il y a un vrai piège de vocabulaire/
convention interne à démêler avant de coder (ex: naming trompeur entre couches). -->

## Plan d'implémentation — dans cet ordre (1 étape = 1 commit)

### Étape 1 — <titre> — scope `<scopes>`

**Ce qu'il faut faire** : <!-- description actionnable, pas de prose vague -->

**Pour quoi / pour qui** : <!-- pourquoi cette approche plutôt qu'une alternative
évidente — référence la décision tranchée correspondante si utile -->

✅ **Validation** : <!-- ce qui prouve que l'étape marche, cas nominal + cas d'erreur -->

<!-- Répéter une section par étape. -->

## Critères d'acceptation

- [ ] <scénario bout-en-bout complet, au curl si possible>
- [ ] <cas d'erreur 1>
- [ ] <cas d'erreur 2>
- [ ] Documentation API à jour ; typecheck + tests passent

## Checklist sécu

<!-- Seulement les points réellement applicables — ne pas copier une checklist
générique si un point ne s'applique pas à cette feature. -->

- [ ] <point de sécu applicable>

## Hors scope

<!-- Repris de la section "Hors scope" de note.md + tout ce qui a été explicitement
déféré dans questions.md ("Hors ticket pour l'instant"). -->

- <item hors scope>
