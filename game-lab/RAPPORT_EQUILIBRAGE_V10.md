# ATHLETIC MASTERS — ÉQUILIBRAGE NUMÉRIQUE ET DECKS COMPATIBLES V1.0
**Date :** 2026-10-30 (heure Europe/Paris)  
**Statut :** DOCUMENT EXPÉRIMENTAL, NON CANONIQUE  
**Contrainte :** aucun playtest papier ; application principale et données des athlètes historiques inchangées.

## Livrables en ligne
- [Observatoire numérique V1.0](https://athleticmastersgame-beep.github.io/athletic-masters-artist-beta-demo/game-lab/equilibrage-v10.html)
- [Relais des Champions V1.0](https://athleticmastersgame-beep.github.io/athletic-masters-artist-beta-demo/game-lab/relais-v10.html)
- [Conquête des Arènes V1.0](https://athleticmastersgame-beep.github.io/athletic-masters-artist-beta-demo/game-lab/conquete-v10.html)
- [Championnat hybride V0.8](https://athleticmastersgame-beep.github.io/athletic-masters-artist-beta-demo/game-lab/hybride-v08.html) (pas de changement de règle)
- [Codex universel fictif V1.0](https://athleticmastersgame-beep.github.io/athletic-masters-artist-beta-demo/game-lab/codex-v10.html)

## 1 — Méthodologie

Total **8 000 parties numériques artificielles** dans cette campagne, sans joueur humain :
- **Relais** : 3 effectifs (3, 4, 5 titulaires) × 3 pénalités de fatigue (2, 3, 4) × 320 courses = **2 880**.
- **Conquête** : 3 méthodes de score (tous les tours ; tours 2–4 ; tour 4 uniquement) × 2 options de départage d'Impact × 320 parties = **1 920**.
- **Championnat** : seuil 2 Pressions (référence de laboratoire) ; seuil 1 Pression (stress test de modification non approuvée) ; seuil 2 avec malus -2 par Pression (variante non adoptée) × 2 politiques de sélection × 320 matchs = **1 920**.
- **Decks** : 14 cartes dont 2 T2 incompatibles contre 12 cartes autorisées, pour Conquête et Relais × 320 parties = **1 280**.

Chaque condition a été testée sur les deux sièges A et B avec les mêmes 160 graines : Relais 780000…780159, Conquête 770000…770159, Championnat 880000…880159, Decks 760000…760159. Moteurs exécutés depuis les versions JavaScript du Game Lab, avec des modifications textuelles ciblées des règles pour les comparaisons. Les deux politiques/agents artificiels sont limités ; les résultats sont **corrélés par graine et influencés par les décisions des agents**. Les nombres ci-dessous ne constituent **aucun test d'équilibrage humain**, ni une estimation de l'engagement, de la satisfaction, de la stratégie optimale ou de la solidité commerciale.

## 2 — Relais : fatigue

Pénalité de fatigue **3** :
| Titulaires | % d'engagements pénalisés après récupération | Pénalité moyenne totale par course | % de courses nulles |
|---|---:|---:|---:|
| 3 | 17,34 % | 5,20 | 4,06 % |
| 4 | 5,84 % | 1,75 | 7,50 % |
| 5 | 1,81 % | 0,54 | 14,38 % |

À **3 titulaires**, test de pénalité :
| Pénalité | % d'engagements pénalisés | Pénalité moyenne par course |
|---|---:|---:|
| 2 | 20,22 % | 4,04 |
| 3 | 17,34 % | 5,20 |
| 4 | 17,09 % | 6,84 |

**Inférence :** augmenter les titulaires à 4 ou 5 incite l'agent à éviter presque totalement les réutilisations. L'effectif de 3 semble être une meilleure base de développement pour une course à 5 étapes. Conserver provisoirement la pénalité 3 uniquement comme **paramètre de laboratoire**, à comparer à 2 et 4 avec une IA plus réaliste.

## 3 — Conquête : prestige

Avec départage d'**Impact actif** :
| Attribution du prestige | Prestige moyen total / match | Retournements de leader pour 100 matchs | Égalités |
|---|---:|---:|---:|
| Tous les tours | 9,74 | 12,19 | 0,63 % |
| Tours 2 à 4 | 8,14 | 6,88 | 0,63 % |
| Tour 4 uniquement | 2,91 | 0 | 0,94 % |

Désactiver le départage d'Impact augmente légèrement la proportion d'arènes contestées : 0,566 → 0,597 arène contestée par tour avec score à tous les tours. **Inférence :** conserver le score par tour pour des expérimentations futures, car il donne une progression de prestige visible, mais il reste à évaluer si l'avance initiale est rattrapable par des joueurs humains.

## 4 — Championnat : Défis et K.O.

Deux politiques de joueur contre le même bot heuristique : « Sélection au score » ou « Titulaire conservé ». Les matchs de cette campagne sont **fortement biaisés en faveur du bot**, qui exploite davantage les soutiens ; ne pas lire leurs résultats comme des taux de victoire normatifs.

| Variante fictive | Politique | Défis tentés par le joueur / match | Défis réussis / match | K.O. pour 100 matchs (2 équipes) |
|---|---|---:|---:|---:|
| 2 Pressions = K.O. | Sélection au score | 0,27 | 0,16 | 0 |
| 2 Pressions = K.O. | Titulaire conservé | 3,00 | 0,28 | 0 |
| 1 Pression = K.O. (stress test) | Sélection au score | 0,27 | 0,16 | 15,63 |
| 1 Pression = K.O. (stress test) | Titulaire conservé | 3,00 | 0,28 | 27,50 |
| 2 Pressions + -2 performance | Sélection au score | 0,27 | 0,16 | 0 |
| 2 Pressions + -2 performance | Titulaire conservé | 3,00 | 0,28 | 0 |

**Décision :** pas de modification au seuil de **2 Pressions = K.O.** déjà approuvé pour anciens playtests D-05. Les Défis réussis sont trop rares chez les agents testés ; il faut réexaminer les décisions de sélection, la récompense du Défi, le rôle de la Parade et les capacités, et non modifier aveuglément le seuil pour faire augmenter le chiffre des K.O.

## 5 — Decks autorisés : retirer les cartes mortes

La collection expérimentale contient **12 athlètes et 7 identités de soutiens**. La carte fictive **T2 Parade préparée** n'a pas d'effet en Conquête et Relais. Garder T2 dans les paquets a été utile pour mettre ce problème en évidence, mais **pas souhaitable pour un deck conseillé**.

| Mode | Deck de soutiens | % des tours avec T2 dans la main | Soutiens joués / match (2 équipes) |
|---|---|---:|---:|
| Relais V0.9 | 14, dont T2 ×2 | 68,38 % | 9,69 |
| Relais V1.0 | 12 compatibles | 0 % | 9,92 |
| Conquête V0.8 | 14, dont T2 ×2 | 63,75 % | 5,58 |
| Conquête V1.0 | 12 compatibles | 0 % | 5,28 |

**Mise en œuvre numérique expérimentale effective :**
- **Championnat V0.8** : 14 soutiens — T1, T2, T3, T4, E1, E2, EV1, deux copies chacun.
- **Conquête V1.0** et **Relais V1.0** : 12 soutiens — T1, T3, T4, E1, E2, EV1, deux copies chacun.
- **Codex V1.0** : T2 reste dans le **catalogue** et porte la mention INCOMPATIBLE dans les deux derniers modes.
- Les valeurs des 12 athlètes sont identiques dans les trois modes. Les effets de soutiens restent **adaptés de manière expérimentale** ; ils ne sont pas les effets canoniques imprimables.

**Attention :** enlever les cartes mortes ne signifie pas nécessairement jouer plus de soutiens ; Conquête passe de 5,58 à 5,28 dans ces simulations. Il s'agit d'une correction de **validité des decks**, pas d'une promesse d'amélioration du nombre de cartes utilisées.

## 6 — Architecture recommandée à l'étude

- Une **identité ludique de carte** stable, distincte de l'illustration, de l'impression et de l'édition.
- Un **Codex versionné** déclarant la compatibilité par mode ; statuts de laboratoire : UTILISABLE, ADAPTÉE, INACTIVE, INTERDITE, EN ÉTUDE.
- Des **paquets autorisés par mode**, des conditions de victoire et des ressources documentées dans des livrets spécifiques.
- Des statistiques et raretés **inchangées** entre modes et finitions, conformément au projet.
- Ne pas verrouiller le recto des cartes **entièrement créées par les artistes** avant d'avoir approuvé les champs, les capacités et les conséquences de compatibilité. Le modèle V4 existant inclut toujours active/passive/coût ; toute refonte requiert autorisation.

## 7 — Critères de passage à une version officielle (non atteints)

1. Tests UX de trois jeux dans de vrais navigateurs et sur mobile.
2. Des bots non trivialement dominants, plusieurs stratégies et vérifications croisées d'équité des sièges.
3. Compréhension humaine des fenêtres d'effets, des réactions et des cartes compatibles.
4. Harmonisation des niveaux de texte imprimés / Codex ; contrôle précis des fiches historiques.
5. Liste de decks autorisés, règles de tournoi et procédures de mise à jour.
6. Validation expresse des règles avant tout brief graphique complet.

**Conclusion : GO développement numérique ; NO-GO approbation de règles, production artistique ou commercialisation.**
