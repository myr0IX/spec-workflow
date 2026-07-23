# Plan dev : <Feature>

Voir `ticket.md` pour l'objectif, les décisions produit et les critères d'acceptation.
Ce fichier couvre l'exécution : fichiers touchés, étapes/commits, tests, vérification.

## Fichiers à créer / modifier

```
<même liste que ticket.md, tenue synchronisée>
```

## Plan d'implémentation : dans cet ordre (1 étape = 1 commit)

### Étape 1 : <titre> (scope `<scopes>`)

**Quoi** : <!-- reprend le "Ce qu'il faut faire" du ticket, reformulé exécution -->

**Pourquoi <choix technique>** : <!-- l'alternative rejetée et pourquoi -->

✅ **Validation** : <!-- identique au ticket -->

<!-- Répéter une section par étape, dans le même ordre que ticket.md. -->

## Tests (TDD, à forte valeur)

<!-- Par étape : quels cas valent vraiment la peine d'un test (comportement, pas
re-assertion du schéma zod ligne à ligne). Dire explicitement ce qu'on évite de tester. -->

- **Étape 1** : <cas nominal>, <cas d'erreur>
- **Éviter** : <tests bruit qui n'apportent rien>

## Vérification end-to-end manuelle

```bash
# 1. <étape>
curl -X <MÉTHODE> $BASE/api/v1/<route> -H "Authorization: Bearer $KEY" ...

# 2. <étape suivante>
```

Rejouer avec les cas d'erreur du ticket (scopes manquants, ressource cross-tenant,
entrée invalide) pour valider les rejets.
