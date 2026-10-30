# ATHLETIC MASTERS — Rapport multi-modes V0.9

**Date :** 30 octobre 2026  
**Statut :** LABORATOIRE NUMÉRIQUE / EXPÉRIMENTAL ; aucune règle canonique ni carte historique modifiée.  
**Contrainte explicite :** aucun playtest papier.

## 1. Trois moteurs disponibles dans le navigateur

- [Portail des gameplays](https://athleticmastersgame-beep.github.io/athletic-masters-artist-beta-demo/game-lab/)
- [Championnat hybride V0.8](https://athleticmastersgame-beep.github.io/athletic-masters-artist-beta-demo/game-lab/hybride-v08.html)
- [Conquête des Arènes V0.8](https://athleticmastersgame-beep.github.io/athletic-masters-artist-beta-demo/game-lab/conquete-v08.html)
- [Relais des Champions V0.9](https://athleticmastersgame-beep.github.io/athletic-masters-artist-beta-demo/game-lab/relais-v09.html)
- [Codex universel de laboratoire V0.9](https://athleticmastersgame-beep.github.io/athletic-masters-artist-beta-demo/game-lab/codex-v09.html)

Toutes les pages sont statiques, autonomes, sans stockage distant, comptes, contrats, commandes artistiques ou paiements.

## 2. Nouveau moteur : Relais des Champions

### Objectif
Une course en cinq étapes, en cumulant les points de progression sportifs. Trois athlètes de six candidats sont choisis avant la course. Le joueur choisit à chaque étape son athlète et éventuellement un soutien. Son adversaire est une politique heuristique numérique.

### Les cinq étapes fictives

| Étape | Statistique principale (x2) | Secondaire (x1) |
|---|---|---|
| Épreuve de puissance | FORCE | TECHNIQUE |
| Course d'endurance | ENDURANCE | IMPACT |
| Parcours technique | TECHNIQUE | ENDURANCE |
| Défi d'impact | IMPACT | FORCE |
| Finale d'endurance | ENDURANCE | TECHNIQUE |

### Fatigue révisée

- Fatigue initiale : 0.
- Performance de l'étape = max(0, 2 × principale + secondaire − 3 × fatigue avant effort + bonus de soutien + bonus d'équipement).
- Après chaque engagement : +1 fatigue ; pas de récupération automatique.
- Le soutien expérimental EV1 « Second souffle » réduit la fatigue actuelle de 1 avant le calcul.
- La progression conserve **tous les points** et n'est pas convertie en cases : les petits bonus ont une valeur arithmétique.
- En sélectionnant trois titulaires pour cinq étapes, les réutilisations sont nécessaires et la fatigue devient un arbitrage de conception.
- **La pénalité de 3 est une hypothèse**, pas un paramètre validé.

### Deck et ressources expérimentales

- **Même pool** que les deux autres jeux : 12 athlètes fictifs LAB-A01…B06, 7 identités de soutiens T1…T4 / E1…E2 / EV1, 2 exemplaires de chaque soutien.
- Un deck de laboratoire contient 14 soutiens ; main initiale de 4 puis +1 au début des étapes 2–5.
- Au plus 1 soutien par étape ; 2 énergies disponibles à chaque étape, sans report.
- Équipements permanents sur le porteur ; les bonus de Technique / Événement sont ponctuels.
- **T2 « Parade préparée » incompatible** : pas de Défi/Parade dans le Relais. Sa présence dans le deck est volontaire dans le laboratoire pour diagnostiquer le problème des cartes mortes, mais ne devrait pas persister dans un deck conseillé commercial.
- Départage : total de progression, puis nombre d'étapes gagnées, puis nul.

## 3. Contrôles effectués

### Vérifications du Relais

- **26 contrôles fonctionnels réussis sur 26**, exécutés en environnement JS simulant les éléments de page. Vérifications notamment : identité des 12 athlètes, total des statistiques 30, 7 soutiens/14 cartes, sélection des trois athlètes, cinq étapes, équipement permanent, fatigue, seconde utilisation, EV1 réduction de fatigue, restrictions de T2, calculs cumulés, résultats reproductibles avec la même graine, deux sièges A/B.
- **400 courses automatiques terminées sur 400 sans erreur d'exécution** (200 pour chaque siège), avec deux agents heuristiques simples. Résultats indicatifs : 169 victoires du côté joueur simulé, 195 du côté ordinateur et 36 égalités.
- Dans ces 400 courses artificielles, **690 engagements sur 4 000 (17,25 %) subissent une fatigue non nulle après l'application éventuelle d'un effet de récupération** ; 2 154 points de pénalité sont comptabilisés, soit 5,385 par course en moyenne.
- 3 837 soutiens joués au total ; 948 utilisations d'EV1. Le nombre est conditionné par les stratégies automatiques et **ne constitue pas une estimation de fréquence humaine**.
- **Aucun playtest utilisateur réel**, aucune mesure de plaisir, de durée réelle ni d'équilibre compétitif. Les tests ne remplacent pas une évaluation UX dans un vrai navigateur.

### Tests hérités

- Conquête V0.8 : 23 contrôles ciblés réussis, 400 matchs artificiels terminés.
- Championnat hybride V0.8 : 400 matchs artificiels terminés, zéro K.O. sous la politique testée malgré le déclenchement correct en scénario ciblé ; fréquence et intérêt des Défis toujours à étudier.

## 4. Codex universel de laboratoire

Premier référentiel numérique consultable, avec **19 entrées** :
- 12 fiches ATHLÈTE : même identifiant et mêmes statistiques dans les trois modes.
- 7 fiches SOUTIEN : texte de l'effet particulier aux trois modes et statut explicite.
- Dans Conquête et Relais, T2 est incompatible, les autres soutiens sont *adaptés à titre expérimental*.
- Les fiches historiques, biographies, dates, œuvres réelles, contrats et pouvoirs individuels n'y sont pas reproduits ni inventés.
- Les identifiants d'œuvres, d'impression, d'édition et de copies restent à spécifier définitivement avant la création de cartes complètes par des artistes.

### Diagnostic prioritaire

Le souhait « une seule collection, plusieurs gameplays » ne signifie pas nécessairement « toutes les cartes dans tous les decks ». Deux options ouvertes à comparer :

**Option A** — socle commun d'athlètes + listes de soutiens autorisés et decks de départ par mode. Des effets distincts peuvent être documentés dans chaque livret.

**Option B** — normaliser un lexique d'effets réellement universels, en imprimant des capacités qui possèdent le même sens dans chaque mode. Cela pourrait réduire les besoins de consulter les livrets mais impose une refonte des mécanismes et une vérification des fiches V4.

À ce stade, **Option A est la plus pragmatique pour les laboratoires**, sans adoption comme architecture officielle.

## 5. Priorités de conception après V0.9

1. **Expérience réelle en navigateur** : parcours accessibles, lisibilité sur téléphone, absence de blocage UX (tests numériques seulement).
2. **Mesures comparables** : mêmes graines / sièges, politiques de bot variées et comparaison des règles du Relais (fatigue 2, 3, 4 ; récupération ; nombre de titulaires).
3. **Conquête** : contrôler la sensibilité aux points marqués chaque tour vs contrôle uniquement final.
4. **Championnat** : analyser la faible fréquence des K.O., comparer coûts du Défi / Parade, tester plus d'agents.
5. **Codex** : définir des mots-clés de jeu communs et versionner la compatibilité de chaque soutien, sans modifier les fiches canoniques non encore auditées.
6. **Livre de règles** : conserver un socle commun de lecture des cartes et un livre distinct par moteur. Ne pas figer les textes des cartes à remettre aux artistes avant une validation explicite.

**GO : recherche et tests numériques supplémentaires. NO-GO : adoption de règles commerciales, données historiques ou impression.**
