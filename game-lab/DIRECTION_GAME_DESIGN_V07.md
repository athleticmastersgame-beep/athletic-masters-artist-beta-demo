# ATHLETIC MASTERS — Décision de direction Game Design V0.7

**Date :** 30 octobre 2026  
**Statut :** DIRECTION DE DÉVELOPPEMENT EXPÉRIMENTALE choisie par délégation ; **aucune validation canonique**, aucun changement à l'application principale, aux illustrations ou aux cartes historiques.

## Choix de produit
- **Gameplay prioritaire à approfondir : Championnat hybride** (architecture historique D-01 + D-03 modèle A + D-05, avec D-02 encore en proposition).
- **Mode Initiation : Championnat simplifié V0.5**, conservé comme tutoriel / expérience légère, et non adopté en remplacement des règles historiques.
- **Autres moteurs : Conquête des Arènes, Relais des Champions**, maintenus comme extensions numériques candidates, sans promesse de calendrier.
- **Aucun playtest papier** : laboratoire navigateur, tests de règles et simulations uniquement pour la prochaine phase.

## Raison du choix (hypothèse de conception)
Un athlète non K.O. peut revenir, ce qui pourrait donner une vraie utilité aux équipements attachés et aux décisions de gestion d'effectif. Les Défis, Parades, Pressions et ressources créent des interactions absentes du Championnat simplifié. Cela peut offrir davantage de décisions, mais **ce gain n'est pas encore prouvé par des joueurs**. Le thème K.O. peut être inadéquat à certains sports : à tester, ou éventuellement reformuler sans altérer ses effets mécaniques.

## Invariants déjà validés pour anciens playtests
- D-01 : 3 manches ; 3 PC sportifs pour une victoire, 1 PC chacun pour une égalité ; maximum +1 PC tactique par joueur et par manche ; départages : total des PC, scores sportifs **bruts**, manches sportives gagnées, nul.
- D-03 modèle A : 3 énergies par manche, sans report.
- D-05 V0.4 : 1 Défi maximum par joueur et par manche, coût 1 ; succès si IMPACT attaquant > TECHNIQUE défenseur (+1 défensive pour Parade coût 1) ; succès = +1 PC tactique et 1 Pression ; 2 Pressions sur un athlète = K.O. pour le match ; remplacement avant performance et pioche d'un soutien si K.O. infligé et paquet disponible.
- Quatre statistiques : FORCE, TECHNIQUE, ENDURANCE, IMPACT. Rareté/finition sans influence sur le gameplay. Textes et effets des athlètes historiques jamais changés silencieusement.

## D-02 — Propositions à tester, non adoptées
- Deck « Championnat 20 » : 6 athlètes uniques + 8 Techniques + 4 Équipements + 2 Événements.
- Athlètes visibles et soutiens mélangés séparément, pioche 5 puis +2/+2.
- Maximum 2 soutiens par manche, fenêtre PRÉPARATION / RÉACTION / FINALE, coûts de fixture explicites 0/1/2 ; au maximum 1 soutien à coût 0 par manche.
- Un Équipement attaché au plus par athlète, persistant avec un athlète encore disponible, défaussé au K.O.
- Réutilisation du même athlète non K.O. lors des manches ultérieures.
- Ces éléments sont **des hypothèses D-02 non validées**, pas les règles officielles.

## Tests bloquants à terminer avant tout choix définitif
1. Implémenter séparément D-05 et les fenêtres D-02, avec résolution simultanée, légalité de cible et d'énergie.
2. Intégrer la pioche de récompense sur K.O. et le plafond tactique +1 PC, sans dépassement.
3. Ajouter des fixtures de Techniques, Équipements et Événements clairement fictives, jamais présentées comme cartes officielles.
4. Vérifier que les Équipements persistent et produisent un choix stratégique utile lors d'une deuxième titularisation.
5. Comparer le mode simplifié et l'Hybride **à données/decks comparables** en inversant les deux sièges et en variant les agents.
6. Tester séparément les pouvoirs passifs/actifs **existants**, après récupération et vérification exacte de leurs textes (pas d'invention).
7. Auditer la cohérence sémantique « Défi / Pression / K.O. » avec les différentes disciplines sportives.
8. Réaliser des sessions de jeu **numériques** avec des humains et recueillir les décisions prises, les incompréhensions et les frustrations.
9. Définir un noyau de données stable sur les cartes imprimées et un contrat de compatibilité pour les différents modes.
10. Tout écart documentaire est enregistré et doit recevoir un arbitrage explicite avant passage au statut canonique.

## Règles du programme multi-modes
- Un même `play_card_id` peut posséder plusieurs `print_id` artistiques ; ces variantes n'accordent pas de puissance supplémentaire.
- Chaque mode possède son `ruleset_id`, son livret, ses formats et sa table de compatibilité.
- Éviter d'imprimer une mécanique propre à un seul mode sur toutes les cartes sans solution d'usage claire dans les autres modes.
- La fiche Codex contient les références historiques vérifiées, l'identité ludique, les variantes illustrées et les versions des règles.

## État
**GO pour le développement numérique expérimental du Championnat hybride. NO-GO pour une déclaration de gameplay officiel, une commande d'illustrations complètes, une impression ou une publication commerciale.**
