# ATHLETIC MASTERS — CHAMPIONNAT HYBRIDE : BOTS ET TÉLÉMÉTRIE V1.2

**Date :** 30 octobre 2026 · **Statut : laboratoire de jeu numérique, non canonique**.

## Périmètre et livrable

- [Jouer au Championnat hybride V1.2](https://athleticmastersgame-beep.github.io/athletic-masters-artist-beta-demo/game-lab/hybride-v12.html)
- [Version précédente V0.8 conservée](https://athleticmastersgame-beep.github.io/athletic-masters-artist-beta-demo/game-lab/hybride-v08.html)

Le jeu conserve les cartes fictives, les coûts, les fenêtres, la Pression et le seuil de 2 Pressions pour K.O. **Aucune règle de laboratoire n'est promue en canon.** L'utilisateur n'effectue aucun playtest papier.

### Trois adversaires

1. **Exploration** : sélection et consommation de soutiens plus aléatoires, Défis/Parades variés.
2. **Réactif** : avantage sportif immédiat, Défi lorsque l'Impact peut surpasser la Technique défensive, Parade seulement si elle peut modifier l'issue selon les cartes du bot.
3. **Planificateur** : prend en compte équipements persistants, Pression déjà subie, probabilité simplifiée de Défi réussi et dépense des énergies dans la manche. Il n'a pas accès aux cartes cachées du joueur pour ses décisions ; il n'optimise pas encore l'arbre de décisions complet du match.

**Paramètre par défaut du laboratoire : Réactif.** Les noms ne sont pas des niveaux de difficulté officiellement équilibrés.

### Instrumentation nouvelle

Chaque journal de match JSON contient `botDifficulty` et `telemetry` : Défis tentés, succès, Parades, K.O. provoqués, soutiens joués, ventilés joueur / ordinateur. Une synthèse est également visible en fin de match.

## Vérification A : 720 matchs contre un joueur scripté sans soutiens

- 240 matchs × trois politiques, deux places A/B, graines appariées 931000–931119.
- Les 720 matchs se sont terminés sans erreur d'exécution.
- Le bot Réactif et le Planificateur remportent **100 %** contre ce joueur scripté. Ce résultat est **non interprétable comme une mesure de difficulté**, car le joueur de référence n'utilisait aucun soutien.
- K.O. moyens par match, tous camps : Exploration 0,03, Réactif 0, Planificateur 0.

## Vérification B : 720 matchs contre un joueur scripté Réactif utilisant des soutiens

Même fenêtre de 120 graines (939000–939119) pour chacun des deux sièges ; **240 matchs par politique**. Le joueur automatisé suit des choix Réactifs comparables et joue des soutiens légaux.

| Politique bot | Matchs | Erreurs | Victoires bot | Victoires joueur scripté | Nuls | Défis réussis par match par bot | Soutiens bot / match |
|---|---:|---:|---:|---:|---:|---:|---:|
| Exploration | 240 | 0 | 0 % | 100 % | 0 % | 0,11 | 2,38 |
| Réactif | 240 | 0 | 30,00 % | 38,75 % | 31,25 % | 0,11 | 5,32 |
| Planificateur | 240 | 0 | 34,17 % | 49,58 % | 16,25 % | 0,13 | 4,22 |

K.O. moyens par match (tous camps) : Exploration 0,02 ; Réactif 0 ; Planificateur 0.

**Interprétation limitée :** face à ce seul agent de référence, la politique Planificateur n'est **pas démontrée supérieure** à la politique Réactive. Il serait erroné de promouvoir le Planificateur en difficulté « Expert » sur ces seules données. Les Défis et K.O. restent très peu sollicités ou peu souvent réussis.

**Biais restants :** mêmes données fictives, stratégies simplifiées, ordre de tirage influencé par consommation pseudoaléatoire, arbitrage de remplaçant scripté, pas de test humain. Il est impossible d'inférer plaisir de jeu, profondeur stratégique ou équité réelle des cartes à partir de ces taux de victoire.

## Contrôles fonctionnels ciblés

Les scénarios de K.O., de pioche après K.O., de validation de l'énergie, de conservation de l'équipement et de la limite des soutiens ont été testés. Un test initial comportait une mauvaise hypothèse de statistiques (Impact 8 > Technique 6 était présenté à tort comme « Défi impossible »). **Cette assertion a été reconnue comme invalide et ne sert pas de preuve de défaut.** Les autres cas ciblés conformes ont réussi.

## Point de conception prioritaire

**Le faible taux de K.O. ne doit pas être « corrigé » en abaissant automatiquement le seuil à une Pression.** Il faut d'abord expliquer le rôle du Défi dans une compétition sportive et rechercher les possibilités de succès sans générer un système de combat artificiel pour les sportifs non combattants.

## Suite à étudier, sans modification canonique

1. Comparer les agents dans des matches croisés (Exploration × Réactif × Planificateur), pas uniquement contre une référence fixe.
2. Tester des choix de Défi / Parade stratégiquement variés et des situations avec un athlète déjà sous Pression.
3. Mesurer les décisions non triviales, pas seulement le taux de victoire.
4. Auditer la terminologie sportive des Défis / Pressions / K.O. et la compatibilité des capacités passives/actives **exactes** des fiches historiques V4 avant une impression.
5. Effectuer une vérification UI sur un vrai navigateur. Aucun test papier.

**GO pour recherche numérique. NO-GO pour adoption officielle, modification de cartes historiques et validation commerciale.**
