# ATHLETIC MASTERS — Rapport multi-modes V0.8

**30 octobre 2026 · Statut : LABORATOIRE NUMÉRIQUE NON CANONIQUE.**

**Aucun playtest papier.** La bêta principale, les fiches historiques, les capacités canoniques et les commandes artistiques restent inchangées.

## 1. Jeux jouables dans le navigateur

- [Championnat hybride V0.8](https://athleticmastersgame-beep.github.io/athletic-masters-artist-beta-demo/game-lab/hybride-v08.html) : trois manches, Défi, Parade, Pression, K.O., soutiens, pioche et remplacement.
- [Conquête des Arènes V0.8](https://athleticmastersgame-beep.github.io/athletic-masters-artist-beta-demo/game-lab/conquete-v08.html) : quatre tours, trois arènes, déploiements, repositionnements et prestige.
- [Accueil Game Lab](https://athleticmastersgame-beep.github.io/athletic-masters-artist-beta-demo/game-lab/) : accès aux deux moteurs et aux versions archivées.

## 2. Championnat hybride — changements V0.8

- Jouer jusqu'à **deux soutiens dans la même fenêtre** si légaux ; maximum deux sur la manche et un seul soutien de coût zéro.
- Poser un Équipement sur **n'importe quel athlète disponible**, y compris un remplaçant.
- Conserver la réserve de trois énergies, les Défis, Parades, Pressions, K.O., pioche de récompense et départages expérimentaux.
- Restriction UI encore provisoire : pas plus d'un Équipement posé dans une seule fenêtre.
- Textes et capacités historiques absents du laboratoire par précaution.

## 3. Conquête des Arènes — règles expérimentales

- **Mêmes 12 identités d'athlètes LAB-A01 à LAB-B06 et mêmes 7 identités de soutiens** T1…T4, E1…E2, EV1, que dans Championnat hybride.
- Trois arènes fondées sur FORCE, TECHNIQUE, ENDURANCE ; IMPACT départage une égalité de performance.
- Quatre tours, un déploiement ou repositionnement par tour et par joueur, simultanément.
- Une arène contrôlée donne un point de prestige par tour ; départage final par arènes contrôlées puis total des performances sportives.
- Un soutien maximum par tour, deux énergies par tour ; équipements persistants, bonus temporaires non persistants.
- La technique T2 **Parade préparée est incompatible** avec Conquête : aucune Parade n'y existe. T2 est conservée dans le paquet uniquement pour rendre visible ce problème de compatibilité ; un deck commercial ne devrait pas comprendre ainsi des cartes volontairement mortes.

## 4. Contrôles numériques

- Conquête : **23 tests ciblés sur 23 réussis** en JavaScript/DOM simulé. **400 matchs automatiques sur 400 terminés** sans exception, dont 200 depuis chaque siège. Avec deux politiques heuristiques apparentées : 208 victoires côté joueur, 192 côté bot, 0 nul ; 9,885 points de prestige attribués par partie en moyenne et 5,36 soutiens utilisés par match.
- Hybride V0.8 : contrôles des lots de soutiens, coûts, équipement sur remplaçant, K.O. et récompense de pioche. **400 matchs automatiques sur 400 terminés** sans exception avec un joueur scripté.
- **Aucun K.O. dans ces 400 matchs hybrides scriptés**, malgré un déclenchement de K.O. correct dans des scénarios ciblés. Il faut examiner la fréquence et les incitations à réussir plusieurs Défis contre un même athlète.
- Tests non réalisés sur le navigateur réel de l'utilisateur. **Les résultats ne prouvent ni équilibrage ni plaisir de jeu.**

## 5. Enseignement sur les cartes universelles

Le support T2 illustre l'impossibilité de présumer qu'une capacité destinée à un mode fonctionne automatiquement dans un autre. Les six autres soutiens sont **adaptés expérimentalement** à Conquête via son règlement ; ces adaptations ne sont pas des pouvoirs canoniques ni des textes d'impression approuvés.

Proposition non validée : identifiants Gameplay, Artwork, Printing, Edition et Copy séparés ; compatibilité par couple (identité ludique, moteur/règlement) et statuts documentaires **UTILISABLE / ADAPTE_REGLE / INACTIF / INTERDIT / EN_ETUDE**. Conserver les statistiques et la puissance invariantes entre finitions.

Le modèle V4 comprend une passive, une active et un coût sur le recto. Il **ne doit pas** être modifié simplement parce que les prototypes multi-modes suggèrent une architecture différente.

## 6. Priorités suivantes

1. Vérifier les parcours sur un vrai navigateur et recueillir des retours numériques.
2. Concevoir **Relais des Champions** comme troisième mode de navigateur, avec les mêmes athlètes LAB.
3. Comparer en numérique des règles de score Conquête (chaque tour vs score final) et étudier les Défis et le K.O. dans l'Hybride.
4. Dresser la matrice de compatibilité de chaque identité de carte par mode, puis seulement déterminer les informations à figer dans les illustrations complètes.

**GO : poursuite du laboratoire numérique. NO-GO : modification canonique, impression, commande commerciale d'illustrations.**
