<!--
Comment remplir ce fichier :
- Remplace chaque section entre <!-- --> par ton propre contenu, puis supprime le commentaire.
- Le but n'est pas d'être exhaustif au mot près, mais de ne pas sauter les catégories
  ci-dessous : ce sont exactement celles qui ont généré des allers-retours la dernière fois.
-->

# Fichiers concernés

<!--
Pour chaque fichier/fonction pertinent, une ligne : chemin + ce qu'il fait, tagué :
- [plomberie] : juste une interface, rien de spécial à en dire
- [risqué] : logique métier, calcul, ou comportement non trivial

Avant de clore cette liste, vérifie explicitement (les 2 pièges les plus fréquents) :
1. Y a-t-il un webhook / callback async quelque part dans le dossier de la feature,
   même s'il n'est appelé par aucun des fichiers "évidents" ? (grep sur "webhook" dans
   le dossier api concerné)
2. Un des fichiers touche-t-il à l'argent (credits, billing, facturation, débit) ?
   Ces deux éléments sont presque toujours ceux qu'on oublie de lister alors qu'ils
   pèsent le plus sur les décisions d'architecture.
-->

# Que faire

<!-- Objectif en 2-3 phrases : qu'est-ce qui doit exister à la fin. -->

# Pour qui ?

<!-- Le persona qui utilisera cette feature, ce qu'il sait déjà, ce qu'il n'a pas
(ex: pas d'interface, pas de contexte de session humaine). Ça tranche souvent des
questions de flux à lui seul (cf. flux script/render podcast : pas de review humaine
possible côté client API → pas d'étape d'édition intermédiaire à exposer). -->

# Hors scope

<!-- Ce qu'on ne veut explicitement PAS faire dans ce ticket, même si ça semble
lié. Le dire maintenant évite de le redécouvrir comme question ouverte plus tard. -->

# Précédent similaire

<!-- Un ticket/dossier existant (specs/<autre-feature>/) qui ressemble le plus à
celui-ci, à utiliser comme référence de structure et de décisions déjà prises
(scopes, gestion d'erreur, idempotence...). Si aucun n'existe, l'écrire explicitement. -->
