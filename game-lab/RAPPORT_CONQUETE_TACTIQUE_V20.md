# ATHLETIC MASTERS — CONQUÊTE TACTIQUE V2.0

**Statut : LABORATOIRE UNIQUEMENT — NON CANONIQUE.**  
**Date : 31 octobre 2026.** Carte blanche donnée par le créateur pour repenser le gameplay expérimental. Aucune modification des cartes historiques, des statistiques approuvées, de la collection V4, ni des règles officielles du Championnat.

## Prototype

[Ouvrir le prototype tactique V2.0](https://athleticmastersgame-beep.github.io/athletic-masters-artist-beta-demo/game-lab/tactique-v20.html)

Le nouveau prototype autonome dérive du moteur de Conquête V1.1, dont il préserve les douze athlètes fictifs LAB, les trois arènes et les six identités de soutiens compatibles. Il reste indépendant du duel simplifié Artist Beta et de l'application principale.

## Intention ludique

Le joueur doit être confronté à une **concurrence entre objectifs** : consolider une arène pour gagner des points maintenant, déployer un spécialiste, ou repositionner un athlète en abandonnant éventuellement son arène précédente. Ce ne sont pas des objectifs d'addiction comportementale : nous cherchons des décisions intelligibles, variées et intéressantes, sans mécanique de rétention manipulatrice.

## Modifications effectives de la V2

- **Cinq tours** (auparavant quatre) ; mêmes trois arènes FORCE, TECHNIQUE, ENDURANCE.
- **Arène à l'honneur publique** : FORCE → ENDURANCE → TECHNIQUE → FORCE → ENDURANCE. Contrôler cette arène rapporte **2 prestige** à la fin du tour, contre **1** pour chacune des deux autres. Arènes vides ou contestées : 0.
- Un athlète est déployé ou repositionné par joueur et par tour ; les positions et équipements persistent. Les soutiens restent limités à **un par tour** et à un budget de 2 énergies avec recharge à chaque tour.
- Chaque agent prépare son mouvement et le soutien associé **avant** que l'humain valide son ordre du tour. Le bot utilise uniquement les positions publiques, son roster et sa main ; il ne reçoit pas la sélection secrète du joueur.
- Deux politiques conservées : **Réactif** et **Planificateur** (tous deux heuristiques ; difficultés non calibrées). L'arène à l'honneur influe désormais sur leur évaluation.
- Interface portrait : trois arènes visibles et mises en avant, **cartes Athlètes et Soutiens sélectionnables au toucher**, choix de la destination en touchant une arène, détails de carte, choix par liste accessibles en secours, bouton d'ordre mobile.
- Les 12 cartes de soutiens compatibles sont T1, T3, T4, E1, E2, EV1 (2 copies chacune). T2 n'est pas distribuée dans ce mode et demeure dans le Codex expérimental.

### Ce que la V2 n'est pas encore

- Pas de score prédictif fiable des choix secrets, de partie multijoueur réseau ou de matchmaking.
- Les illustrations des cartes de laboratoire sont des **substituts graphiques CSS**, pas les œuvres approuvées d'ATHLETIC MASTERS.
- Le mode ne possède ni les Défis / Parades / K.O. du Championnat D-05, ni les capacités individuelles des athlètes historiques.
- Les soutiens restent liés à la même arène que le déploiement ou repositionnement de leur titulaire, selon la règle de Conquête V1.1 ; la nouvelle liberté de ciblage envisagée pour un prochain moteur Lovable n'est pas importée silencieusement.
- Les animations sont limitées ; l'ergonomie doit encore être validée **sur de vrais téléphones** et auprès de joueurs.
- Ce mode n'est **pas** une nouvelle règle canonique et ne remplace pas l'ancien Championnat.

## Tests numériques vérifiés

Évaluation du code JavaScript exact de `tactique-v20.html` par environnement DOM simulé :
- intégrité des 12 athlètes fictifs, chacun avec 4 statistiques totalisant 30 ;
- composition d'un deck compatible de 12 soutiens, sans T2 ;
- séquence des cinq arènes à l'honneur ;
- **480 parties complètes de cinq tours** : 120 graines pour chaque combinaison de deux équipes (A/B) × deux adversaires (Réactif/Planificateur) ; joueur automatisé choisissant un placement légal selon une politique déterministe ;
- **480/480 parties terminées**, 0 erreur signalée ;
- décompte de trois arènes par tour et de leur valeur maximale de prestige vérifié sur tous les tours ;
- séquence de l'arène à l'honneur vérifiée dans les 2 400 historiques de tours.

Ces tests **ne prouvent ni équilibre, ni plaisir de jeu, ni absence totale de bug**. Ils n'incluent pas d'essai sur appareil physique.

## Suite de travail

1. Tester en navigateur réel le tap, les zones tactiles, la sélection et l'affichage à 360–430 px.
2. Faire jouer des bots différents en miroir, instrumenter contrôles d'arènes, écarts, repositionnements et utilisation des soutiens.
3. Recueillir du feedback humain **numérique** sur les décisions intéressantes, sans playtest papier.
4. Comparer ce prototype au Championnat hybride, sans imposer prématurément un gagnant.
5. Continuer la refonte Lovable mobile de manière isolée et n'intégrer que des comportements techniques confirmés.

**Décision de cette version : GO expérimentation numérique ; NO-GO adoption canonique, impression ou commercialisation.**
