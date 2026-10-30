# ATHLETIC MASTERS — Rapport du laboratoire hybride V0.7

**Date :** 30 octobre 2026  
**STATUT :** PROTOTYPE NUMÉRIQUE EXPÉRIMENTAL, NON CANONIQUE  
**URL :** https://athleticmastersgame-beep.github.io/athletic-masters-artist-beta-demo/game-lab/hybride-v07.html

## Objectif
Prolonger la démonstration partielle D-05 V0.6 avec une sous-partie des règles D-02 (proposées, non validées), uniquement en navigateur. Les règles historiques officielles et l'application d'accueil restent inchangées. **Aucun playtest papier.**

## Références documentaires
- D-01 : trois manches, PC sportifs 3/1, plafond tactique +1 PC par manche, départage PC → score sportif **brut** → manches sportives gagnées → nul (validé pour playtests historiques).
- D-03 modèle A : 3 énergies par manche, sans report (validé pour playtests historiques).
- D-05 V0.4 : Défi (1), Parade (1), Impact strictement supérieur à Technique défensive, 1 Pression si réussite, 2 Pressions = K.O., pioche de récompense après K.O. (validé pour playtests historiques).
- D-02 V0.6 : **non validé** ; modèle de deck 6 Athlètes + 8 Techniques + 4 Équipements + 2 Événements ; 5 soutiens au départ, +2/+2 ; maximum 2 soutiens par manche, maximum un coût 0 ; fenêtres PRÉPARATION, RÉACTION, FINALE ; Équipement persistant (toutes hypothèses de laboratoire).

## Jeu numérique disponible
- 12 athlètes **entièrement fictifs** de 4 caractéristiques (total 30), répartis en deux équipes de 6.
- 14 soutiens par paquet, **7 identités fictives différentes** à 2 exemplaires chacune : T1 Ajustement technique, T2 Parade préparée, T3 Impulsion contrôlée, T4 Élan initial, E1 Matériel polyvalent, E2 Matériel technique, EV1 Second souffle.
- Choix secret de titulaire de chaque côté, révélation et cinq étapes numériques : préparation, Défi, réaction, résolution/K.O./remplacement, finale/scores.
- Énergie 3 par manche, débitée des Défis, Parades, soutiens ; réinitialisée à la manche suivante.
- Si K.O. : l'Équipement de ce titulaire est détruit, pioche d'un soutien pour son adversaire s'il reste des cartes, remplacement avant score.
- Un titulaire non K.O. peut revenir aux manches suivantes, avec sa Pression et ses Équipements conservés.
- Téléchargement local du journal JSON, graine reproductible, un adversaire automatique basique.

## Limitations explicites
1. Une seule carte de soutien peut être sélectionnée **par fenêtre** dans cette interface ; ceci est plus restrictif que le simple plafond global de 2 de D-02, et reste une convention UX du test.
2. Un Équipement ne peut être posé que sur **le titulaire courant**, et non n'importe quel athlète disponible ; convention de test plus étroite que la proposition D-02.
3. Remplacement automatique du **bot** ; remplacement choisi par l'humain. L'ordre simultané complet et les cas sans remplaçant restent à arbitrer.
4. **Capacités actives/passives historiques non implémentées** ; aucun coût ni texte n'a été inventé.
5. Pas de Capitaine, évolution, Arène, terrain, économie additionnelle ou compatibilité avec les autres moteurs.
6. Épreuves préprogrammées pour le laboratoire et non fixées officiellement : FOR×2+TEC, END×2+IMP, TEC×2+END.
7. La stratégie du bot n'est ni équilibrée ni représentative d'un joueur humain.
8. Mode solo local sans serveur. Il n'envoie ni données ni créations au projet.
9. Le terme « K.O. » est un mécanisme D-05 à évaluer sémantiquement pour les disciplines non combattantes.

## Contrôles effectués
- 25 tests fonctionnels **réussis** en environnement JavaScript avec DOM simulé, incluant : deck 8/4/2, 7 identités, cartes à total de statistiques 30, pioche initiale, tirage de 2 cartes entre manches, match complet en 3 manches, soutiens à coût 0, coût d'énergie, fenêtre de jeu, plafond de soutiens, persistance de l'équipement, K.O., perte de l'équipement, remplacement, bonus événement conditionnel, récompense de pioche K.O.
- **Limite :** ces tests vérifient la logique simulée, pas le rendu dans un vrai navigateur ni le ressenti d'utilisateurs.
- Aucun test d'équilibrage suffisant pour une mise en production. Aucun classement du plaisir des modes n'est établi.

## Prochaines étapes prioritaires
1. Vérifier visuellement le parcours complet dans un vrai navigateur, notamment les formulaires de Réaction et le remplacement.
2. Compléter les fenêtres D-02 (poser 2 soutiens dans une même fenêtre si légal, cible équipable autre que le titulaire).
3. Ajouter une batterie de scénarios automatisés : défis croisés, double K.O., pioche à paquet vide, attrition, cas d'énergie zéro.
4. Évaluer l'intérêt tactique des Équipements persistants face aux Techniques instantanées.
5. Étudier la compatibilité des capacités exactes des fiches historiques **seulement après vérification des données canoniques**.
6. Ajouter Conquête et Relais au laboratoire sans toucher à la bêta commerciale.

**État de décision :** GO pour développement expérimental numérique ; NO-GO pour règles officielles, cartes historiques imprimables, commande artistique et commercialisation.
