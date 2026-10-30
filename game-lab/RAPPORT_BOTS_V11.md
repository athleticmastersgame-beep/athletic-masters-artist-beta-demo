# ATHLETIC MASTERS — Bots stratégiques numériques V1.1

**Date :** 30 octobre 2026  
**Statut :** EXPÉRIMENTAL, NON CANONIQUE ; aucun playtest papier ni changement de la bêta principale.

## Prototypes

- [Relais V1.1](https://athleticmastersgame-beep.github.io/athletic-masters-artist-beta-demo/game-lab/relais-v11.html)
- [Conquête V1.1](https://athleticmastersgame-beep.github.io/athletic-masters-artist-beta-demo/game-lab/conquete-v11.html)
- [Championnat hybride V0.8](https://athleticmastersgame-beep.github.io/athletic-masters-artist-beta-demo/game-lab/hybride-v08.html) (conservé ; prochaine analyse spécifique des Défis/K.O.)
- [Contrat de données universel V1.1](https://github.com/athleticmastersgame-beep/athletic-masters-artist-beta-demo/blob/main/game-lab/CONTRAT_DONNEES_UNIVERSEL_V11.md)

## 1. Trois politiques disponibles

**Exploration** : choix d'athlète ou de déplacement varié, avec soutien légal possible. Ne cherche pas systématiquement à maximiser le score.

**Réactif** : préférence pour le gain immédiat, en fonction des statistiques et soutiens connus. Hérite de la politique heuristique V1.0.

**Planificateur** :
- Dans **Relais**, calcule récursivement la meilleure suite théorique de ses propres titulaires sur les étapes restantes, en tenant compte de la fatigue et des équipements déjà visibles ; ne suppose pas connaître les pioches futures ou la décision adverse.
- Dans **Conquête**, compare les conséquences de chaque mouvement légal sur le contrôle actuel des trois arènes, en tenant compte de l'arène abandonnée ; il ne voit pas le mouvement encore secret de l'adversaire. Ce moteur n'est **pas** un minimax compétitif complet.

Les trois bots peuvent être choisis dans la configuration de chaque page. Ils ne sont pas des niveaux de difficulté calibrés.

## 2. Comparaisons automatisées

**Méthode :** chaque politique face au **même joueur automatisé Réactif**, 120 graines (910000–910119 pour Relais, 920000–920119 pour Conquête), inversion des côtés A/B. **240 parties par politique**, 720 pour chaque jeu, **1 440 parties** au total. Les bots conservent leur sélection initiale d'équipe ; les graines sont identiques mais l'usage variable du générateur aléatoire n'assure pas des états rigoureusement identiques à chaque décision.

### Relais (cinq étapes)

| Bot | Courses | Erreurs | Progression moyenne du bot | Victoires bot | Égalités |
|---|---:|---:|---:|---:|---:|
| Exploration | 240 | 0 | 106,91 | 0 % | 0,42 % |
| Réactif | 240 | 0 | 129,08 | 50,42 % | 8,33 % |
| Planificateur | 240 | 0 | 129,20 | 54,58 % | 6,67 % |

**Analyse :** le Planificateur améliore légèrement les performances de l'agent dans ce cadre ; les gains moyens sont faibles. Son avantage sur le Réactif n'est pas une preuve de meilleure jouabilité humaine.

### Conquête (quatre tours)

| Bot | Parties | Erreurs | Prestige moyen du bot | Victoires bot | Égalités |
|---|---:|---:|---:|---:|---:|
| Exploration | 240 | 0 | 4,06 | 18,33 % | 14,17 % |
| Réactif | 240 | 0 | 4,69 | 39,17 % | 8,75 % |
| Planificateur | 240 | 0 | 5,92 | 84,17 % | 10,42 % |

**Analyse :** la prise en compte de l'arène abandonnée et de l'ensemble du plateau confère un avantage **très important contre cette politique Réactive particulière**. Ce résultat ne permet pas de dire que le Planificateur est équilibré ni qu'il gagne 84 % du temps contre un humain. Il faudra tester d'autres adversaires et des miroirs IA–IA pour chercher les stratégies dominantes.

## 3. Limites

- Bots déterministes ou pseudo-aléatoires simples ; ni régression statistique robuste ni comportement humain.
- Même collection fictive de 12 athlètes à quatre statistiques total 30 et de 7 identités de soutiens, avec decks de 12 soutiens compatibles dans Relais et Conquête.
- Expériences exécutées dans une simulation JavaScript avec DOM simulé. Un contrôle sur appareils et navigateurs réels reste à effectuer.
- Les scores et win rates ne constituent **pas un classement compétitif**.
- Les capacités historiques individuelles, les effets D-02 non adoptés et les contrats artistiques ne changent pas.

## 4. Suite proposée

1. Tester les trois adversaires en jeu humain **numérique** (pas de papier) et les faire s'affronter entre eux.
2. Rendre le bot Championnat plus crédible : décisions de Défi, Parade, Pression, K.O., équipement et coût d'énergie ; garder les données historiques intactes.
3. Définir un score de diversité des décisions et des durées de parties réelles.
4. Intégrer le contrat de données V1.1 aux futures fiches Codex, **sans changer V4 silencieusement**.

**GO : développement technique. NO-GO : validation de l'équilibrage et commande artistique basée sur ces textes.**
