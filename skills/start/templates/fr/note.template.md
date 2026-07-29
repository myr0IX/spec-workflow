<!--
Comment remplir ce fichier :
- Remplace chaque section entre <!-- --> par ton propre contenu, puis supprime le commentaire.
- Le but n'est pas d'être exhaustif au mot près, mais de ne pas sauter les catégories
  ci-dessous : ce sont exactement celles qui ont généré des allers-retours la dernière fois.
-->

# Fichiers concernés

<!--
Projet existant : pour chaque fichier/fonction pertinent, une ligne : chemin +
ce qu'il fait, tagué :
- [plomberie] : juste une interface, rien de spécial à en dire
- [risqué] : logique métier, calcul, ou comportement non trivial

Projet greenfield (aucun code existant pour cette feature) : écris-le
explicitement ("Pas de code existant, projet greenfield") plutôt que de
laisser la section vide, puis liste les fichiers/modules qu'on prévoit de
créer avec le même tag [plomberie]/[risqué] appliqué au rôle prévu de
chaque module (le tag porte sur la nature du composant, pas sur le fait
qu'il existe déjà).

Avant de clore cette liste, vérifie explicitement (les 2 pièges les plus fréquents) :
1. Y a-t-il un webhook / callback async quelque part dans le dossier de la feature,
   même s'il n'est appelé par aucun des fichiers "évidents" ? (grep sur "webhook" dans
   le dossier api concerné — en greenfield, vérifie plutôt si le flux prévu en implique un)
2. Un des fichiers touche-t-il à l'argent (credits, billing, facturation, débit) ?
   Ces deux éléments sont presque toujours ceux qu'on oublie de lister alors qu'ils
   pèsent le plus sur les décisions d'architecture.
-->

# Que faire

<!-- Objectif en 2-3 phrases : qu'est-ce qui doit exister à la fin. -->

# Comment

<!-- Approche technique de haut niveau, SEULEMENT ce qui est déjà tranché :
quel composant fait quoi, comment les pièces s'articulent (ex : "service Python
séparé qui écrit directement en base, le backend ne fait que lire"). Pas de
code, pas de schéma, pas de signature d'interface : ça, c'est le travail de
spec-workflow:ticket-plan une fois questions.md tranché.

Si un point du "comment" n'est pas encore décidé, ne l'écris PAS ici comme si
c'était acquis : laisse-le de côté, spec-workflow:analyze le fera remonter
comme question dans questions.md. Cette section ne doit contenir que des
décisions déjà prises, jamais une hypothèse ou un choix par défaut. -->

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
