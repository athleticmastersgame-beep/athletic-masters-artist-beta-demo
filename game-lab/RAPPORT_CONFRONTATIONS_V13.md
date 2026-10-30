# ATHLETIC MASTERS — RAPPORT DE CONFRONTATIONS D-05 / LAB V1.3

**Date :** 30 octobre 2026  
**Statut :** EXPÉRIMENTAL / ANALYSE NON CANONIQUE. Aucun playtest papier. Aucune modification aux cartes historiques ni aux règles approuvées pour les anciens playtests.

**Outil interactif :** https://athleticmastersgame-beep.github.io/athletic-masters-artist-beta-demo/game-lab/confrontations-v13.html

## 1. Sources et règles conservées

Les règles D-05 V0.4 sont reprises telles qu'elles figurent dans `ATHLETIC_MASTERS_D02_COMPOSITION_DECK_SOUTIENS_V0_6_PROPOSITION.md` et `ATHLETIC_MASTERS_D07_POUVOIRS_UNIQUES_ET_CARTES_EXCEPTIONNELLES_V0_9_PROPOSITION.md` :

- Au maximum **1 Défi par joueur et par manche**, coût **1 énergie**.
- Défi réussi uniquement lorsque **IMPACT de l'attaquant est strictement supérieur à TECHNIQUE du défenseur**.
- Parade coût **1 énergie** : **+1 TECHNIQUE défensive**.
- Défi réussi : **+1 PC tactique** (plafond D-01 : +1 PC tactique par joueur/manche) et **1 Pression** sur le défenseur.
- **2 Pressions sur le même athlète = K.O.** pour le match ; remplacement avant performance et pioche d'une carte de soutien pour le joueur qui provoque le K.O., si paquet disponible.
- D-03 modèle A : réserve de 3 énergies par manche, sans report.

Le soutien fictif **T2 « Parade préparée »** possède un effet **proposé dans D-02 non validée** : une Parade payée et T2 donnent **+2 en tout** à la TECHNIQUE défensive, dont +1 par la Parade et +1 par T2 ; T2 coûte zéro énergie mais compte comme un soutien utilisé. Cette hypothèse n'a pas été promue en canon.

## 2. Calcul exhaustif des confrontations

**Fixtures :** 12 athlètes fictifs LAB-A01…LAB-B06, 6 par équipe, valeurs communes aux trois Game Labs. Pour chaque couple `A_i vs B_j`, on évalue le Défi dans les deux directions. Il y a **6 × 6 × 2 = 72 situations orientées**.

| Défense supposée | Réussites sur 72 | Réussites théoriques |
|---|---:|---:|
| Sans Parade | 28 | 38,89 % |
| Parade (+1 TECHNIQUE) | 10 | 13,89 % |
| Parade + T2 (+2 TECHNIQUE) | 2 | 2,78 % |

Par rapport à l'absence de Parade, **18 confrontations** réussies sont bloquées par une Parade. L'ajout d'un T2 bloque **8 autres** confrontations auparavant réussies après la simple Parade. Deux Défis restent réussis même avec la défense +2.

**Portée du constat :** il s'agit d'un décompte des différences entre IMPACT et TECHNIQUE, **pas** d'une probabilité de réussite contre un joueur humain. La disponibilité d'énergie, la main, les fenêtres, la sélection du titulaire et la possibilité de défendre ne sont pas pondérées dans ce tableau.

## 3. Trois manches : énumération exhaustive des K.O.

### Méthode de calcul

Pour chaque scénario de défense fixe :
1. Les deux joueurs commencent avec six athlètes disponibles, aucune Pression.
2. À chaque manche, chacun sélectionne **uniformément et indépendamment** un de ses athlètes **non K.O.**, avec remplacement de la même identité autorisé aux manches suivantes si elle est encore disponible.
3. **Chacun tente systématiquement un Défi** et dispose par hypothèse des ressources pour payer sa défense, si celle-ci est imposée.
4. Le Défi réussit si `IMPACT > TECHNIQUE + bonus_défense`. Les Pressions sont enregistrées et persistent entre les manches.
5. Un athlète atteignant deux Pressions est exclu des sélections ultérieures. L'énumération se poursuit jusqu'à trois manches.
6. Chaque embranchement est pondéré par `1 / (nombre de titulaires A disponibles × nombre de titulaires B disponibles)`. La somme totale des poids est vérifiée numériquement ≈ 1.
7. On relève si **au moins un K.O.** est survenu pendant le match. Ce calcul ne modélise ni performance sportive, ni soutien offensif, ni active, ni remplacement pendant la même manche (seulement l'exclusion au tour suivant). La pioche de récompense n'a pas de rôle dans ce sous-modèle.

| Défense hypothétique à chaque manche | Branches terminales | Part de parcours avec au moins un K.O. |
|---|---:|---:|
| Aucune Parade | 45 992 | **20,89 %** |
| Parade payée systématique (+1) | 46 526 | **4,34 %** |
| Parade + T2 systématiques (+2) | 46 644 | **0,45 %** |

**Avertissement majeur :** l'hypothèse « T2 disponible et joué à chaque manche » **n'est pas réalisable avec un paquet D-02 standard** de seulement deux exemplaires maximum de cette identité par joueur. Cette ligne est exclusivement un **contrefactuel de puissance défensive**, pas une fréquence réalisable dans une partie valide.

Même les lignes sans T2 reposent sur des comportements extrêmes (« toujours Défier », « toujours Parrer ») qui ne sont pas ceux de vrais joueurs ou des bots V1.2. Ces chiffres ne sont donc **pas des taux de K.O. attendus commercialement**.

## 4. Contrôles techniques

- Le laboratoire numérique `confrontations-v13.html` rend les 72 confrontations et les résultats du calcul strict, permet de choisir attaquant/défenseur, défense, énergie 0–3, T2 disponible ou non et Pression initiale 0/1.
- Les ressources illégales interrompent la simulation ciblée sans attribuer de PC ni de Pression.
- 14 scénarios fonctionnels réussis sous DOM simulé après initialisation explicite des valeurs `select`.
- Les trois probabilités exactes de K.O. ont été recalculées **dans le JavaScript de la page** ; somme des poids ≈ 1 dans chacun des trois scénarios.
- **Aucun test utilisateur dans son navigateur réel effectué** ; le code a été vérifié dans un environnement simulé.

## 5. Diagnostic de conception

**Observations appuyées par les calculs** :

- La Parade simple fait passer le nombre de rencontres où un Défi serait réussi de 28 à 10 sur 72. Son effet défensif peut être déterminant.
- Deux Pressions sur **la même identité** sont nécessaires pour le K.O. : les changements de titulaire réduisent les occasions de cumuler ces Pressions.
- Les agents des laboratoires précédents effectuent relativement peu de Défis réussis et très peu de K.O. ; cette observation doit être traitée comme un problème de politique de décision, d'incitation et d'économie de ressources avant d'envisager un changement de seuil.

**Inférences non vérifiées auprès de joueurs** :

- Le Défi pourrait être utile surtout comme moyen d'obtenir +1 PC tactique et non comme moyen de provoquer un K.O. ; sa valeur doit être comparée à une Technique ou à une active coûtant la même énergie.
- Le K.O. pourrait être un événement rare, mais marquant, plutôt qu'une mécanique fréquente. Son intérêt pour un TCG multisport doit être évalué, notamment son nom et les disciplines non combattantes.
- La défense systématique pourrait rendre la phase de Défi peu intéressante ; ce risque dépend entièrement de la main et du coût de la Parade.

## 6. Décision de la V1.3

**Aucune règle D-01 / D-03 / D-05 modifiée.** Conserver le seuil de **2 Pressions**, la Parade à **1 énergie pour +1 Technique**, et le plafond **1 Défi par manche** pour les anciens playtests.

**Prochain chantier numérique :** analyser l'opportunité du Défi face à la dépense des mêmes énergies pour les soutiens ou les actives. Construire des situations dans lesquelles le Défi améliore un résultat puis des situations dans lesquelles il fait perdre une meilleure action sportive. Cela demande des effets de soutiens explicites et des politiques réellement diversifiées.

**Statut commercial : non validé.** Ne pas modifier la V4, les pouvoirs historiques, la commande artistique ni le recto des cartes sur la base de ce seul diagnostic.
