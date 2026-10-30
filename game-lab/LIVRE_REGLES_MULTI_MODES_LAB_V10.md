# ATHLETIC MASTERS — LIVRE DES RÈGLES DE LABORATOIRE MULTI-MODES V1.0

**Statut : PROTOCOLE DE TEST NUMÉRIQUE SEULEMENT.**  
Ce document ne remplace pas les documents D-01/D-03/D-05 approuvés pour les anciens playtests, ni les fiches canoniques V4. Les choix D-02 et les règles de Conquête et Relais restent expérimentaux.

## 0. Lecture des cartes LAB

**Athlètes** : 12 sujets fictifs (6 équipe A / 6 équipe B). Chacun possède exactement 4 statistiques — FORCE, TECHNIQUE, ENDURANCE, IMPACT — dont le total est 30. Identifiants LAB-A01…LAB-B06. Les mêmes valeurs sont employées dans les trois jeux.

**Soutiens** : 7 identités fictives (T1 à T4 ; E1 à E2 ; EV1), deux exemplaires par identité dans la collection de laboratoire. Un soutien n'est légal que dans les modes dont le Codex lui attribue un effet. Aucun de ces effets n'est canonique.

**Statuts** : UTILISABLE / ADAPTÉ / INCOMPATIBLE. Toute adaptation est définie dans le règlement du mode. Aucun effet n'est déduit automatiquement d'un autre jeu.

**À ne pas confondre** : identité ludique, artwork, édition, rareté et copie individuelle. La rareté n'est pas un bonus mécanique.

## 1. Championnat hybride — LAB V0.8

**Composition** : six athlètes visibles + 14 soutiens (8 Techniques T1–T4, 4 Équipements E1–E2, 2 Événements EV1).

**Début** : mélanger le paquet de soutiens, en piocher cinq. Trois manches, avec deux cartes supplémentaires au début des manches 2 et 3. Trois énergies par manche, sans report.

**Épreuves préprogrammées, uniquement dans ce labo** :
1. 2 × FORCE + TECHNIQUE
2. 2 × ENDURANCE + IMPACT
3. 2 × TECHNIQUE + ENDURANCE

**Ordre des opérations** :
1. Choix simultané des titulaires puis révélation.
2. Fenêtre de Préparation : soutiens légaux et équipements, éventuellement sur un remplaçant disponible.
3. Défi (coût 1), au maximum un par joueur et par manche.
4. Réaction : Parade (coût 1) si défi adverse ; soutiens de réaction.
5. Résoudre les Défis simultanément : succès si IMPACT du défieur > TECHNIQUE défensive (+1 par Parade, et supplément éventuel T2) ; +1 PC tactique au maximum pour le joueur dont le Défi réussit ; 1 Pression sur le titulaire adverse ; à 2 Pressions, K.O. pour le match, équipement défaussé, pioche de récompense pour l'adversaire si la pile le permet, remplacement avant performance.
6. Fenêtre Finale, puis comparaison des performances.
7. La meilleure performance donne **3 PC sportifs**, égalité 1 PC chacun. Ajouter les PC tactiques ; après trois manches, total PC détermine la victoire. Départages expérimentaux : performances brutes cumulées puis manches sportives gagnées, sinon nul.

**Soutiens** : maximum deux par manche, y compris deux dans une même fenêtre ; maximum un soutien coût zéro ; la somme des coûts (soutiens, Défi, Parade) ne peut dépasser trois. Un équipement maximum par athlète, persistant jusqu'au K.O.

**Limitations du logiciel** : pas plus d'un Équipement posé par fenêtre ; aucun véritable pouvoir historique ni Capitaine ; joueur vs bot, sans multiplayer. Les divergences avec D-01/D-05 sont suivies dans le rapport V0.7 et restent ouvertes.

## 2. Conquête des Arènes — LAB V1.0

**Composition** : six athlètes disponibles, **12 soutiens compatibles** (2 × T1, T3, T4, E1, E2, EV1). T2 exclue du deck mais présente au Codex.

**Quatre tours**. Trois arènes : FORCE, TECHNIQUE, ENDURANCE.

À chaque tour : choisir secrètement un athlète à **déployer** depuis la réserve ou **repositionner** depuis son arène ; choisir une arène différente de sa position actuelle. Un soutien au plus par tour, deux énergies au maximum. Les joueurs révèlent les décisions, posent/mutent les athlètes et appliquent les soutiens. Les Équipements restent attachés.

**Force d'arène** : somme des valeurs de la statistique de l'arène des athlètes sur place, plus équipement/bonus temporaire. Comparer les totaux ; si égalité, départager par la somme des **IMPACT** présents. Si égalité persistante, l'arène est contestée.

Fin de chaque tour : une arène contrôlée vaut **1 point de prestige**. Après quatre tours : victoire au total de prestige. Départager par arènes contrôlées au dernier tour, puis total des forces finales, sinon nul.

**Pioche** : quatre soutiens au départ, puis +1 au début des tours 2–4. Les effets temporaires expirent après le score du tour courant. L'ordre des bonus est défini par le moteur de laboratoire.

## 3. Relais des Champions — LAB V1.0

**Composition** : sélectionner exactement **trois athlètes parmi six** ; **12 soutiens compatibles** (2 × T1, T3, T4, E1, E2, EV1). T2 exclue du paquet mais conservée au Codex.

**Cinq étapes** :
1. Puissance : 2 × FORCE + TECHNIQUE
2. Endurance : 2 × ENDURANCE + IMPACT
3. Technique : 2 × TECHNIQUE + ENDURANCE
4. Impact : 2 × IMPACT + FORCE
5. Finale d'endurance : 2 × ENDURANCE + TECHNIQUE

À chaque étape : choisir un de ses trois titulaires ; éventuellement jouer un soutien compatible (maximum un, deux énergies disponibles). Les équipements peuvent rester attachés à leur porteur.

**Fatigue** : départ à zéro ; au moment de l'étape, performance = max(0, base sportive − 3 × fatigue avant effort + bonus de soutiens et équipements) ; le soutien EV1 réduit la fatigue de 1 **avant** le calcul si elle est positive ; après l'effort, le titulaire gagne 1 fatigue ; aucun repos automatique. Les points sont conservés sans arrondi en cases.

**Pioche** : quatre soutiens au départ, puis +1 avant les étapes 2–5.

**Victoire** : meilleur total de progression sur cinq étapes ; départage par nombre d'étapes gagnées ; sinon match nul.

## 4. Codex, règles imprimées et corrections

Chaque identité de carte devrait posséder : identifiant stable, version de texte canonique, quatre statistiques si Athlète, type, effets complets si Soutien, et statut de compatibilité par mode. Les livres de règles indiquent les coûts, ressources, timing et exceptions. Les œuvres et leurs licences ont des identifiants distincts. Les détails historiques et les capacités réellement attribuées aux légendes demandent vérification et approbation.

### Blocages avant publication de règles officielles

- Dans le Championnat, les termes Pression/K.O. et les interactions avec sports non combattants sont toujours à auditer.
- Tous les effets actuels T1…EV1 sont **fictifs de laboratoire** ; pas de transposition silencieuse vers Sandow ou d'autres athlètes historiques.
- Une carte inapte à un jeu ne doit pas apparaître dans le deck de départ conseillé de ce jeu.
- Aucune règle de laboratoire n'a été validée comme cahier des charges pour artistes.
- Pas de test papier demandé ; les validations de jouabilité restent **numériques**.

Pour observer l'état de l'étude et ses limites : voir RAPPORT_EQUILIBRAGE_V10.md et le tableau de bord expérimental en ligne.
