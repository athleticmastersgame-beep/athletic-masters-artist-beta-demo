# ATHLETIC MASTERS — V1.4 : COÛT D'OPPORTUNITÉ D'UNE ÉNERGIE

**Date :** 30 octobre 2026  
**Statut :** étude de laboratoire numérique, **non canonique** ; aucun test papier.  
**Outil :** https://athleticmastersgame-beep.github.io/athletic-masters-artist-beta-demo/game-lab/opportunite-v14.html

## 1. Objet

Le jeu « Championnat hybride » comporte une réserve commune de **trois énergies par manche**, sans report (D-03 modèle A, approuvé pour anciens playtests), un **Défi** coûtant une énergie (D-05), et des **soutiens** aux coûts explicites proposés dans D-02, non validée.

**Question :** pour une situation sportive donnée, que rapporte immédiatement **une énergie** dépensée en Défi plutôt que dans un soutien ? La comparaison ne prétend pas résoudre l'ensemble de l'arbre de décisions : on teste des choix alternatifs supposés légaux, à ressources disponibles, en fixant les autres actions.

## 2. Sources internes et niveau d'autorité

- \`ATHLETIC_MASTERS_D02_COMPOSITION_DECK_SOUTIENS_V0_6_PROPOSITION.md\` : D-01 (3/1/0 PC sportifs ; plafond tactique +1), D-03 (trois énergies), D-05 (Défi/parade, Pression, K.O.) explicitement présentés comme **validés pour anciens playtests uniquement** ; D-02 **non validée**.
- \`02_STRUCTURE_ET_DONNEES_CANONIQUES_V4.md\` : statistiques FORCE / TECHNIQUE / ENDURANCE / IMPACT, chacune dans [2,9], somme 30 ; passive/active et coûts exacts communs aux raretés C/R/SR/L ; aucune modification autorisée.
- \`game-lab/hybride-v12.html\` et \`game-lab/codex-v10.html\` : **fixtures fictives** T1 (bonus +2 si Technique secondaire), T3 (+1), T4 (+2 en Préparation), E1 (+1 avec porteur actif, persistant), E2 (+2 si Technique principale, persistant), EV1 (+1 ou +2 si le joueur était derrière en PC au début de la manche). Tous ces soutiens coûtent **une énergie dans le laboratoire**. Leurs textes ne sont **pas des textes de carte définitifs**.
- Le soutien de référence \`TEST-TECH-01\` du document D-02 propose bien un bonus +2 si TECHNIQUE est secondaire, mais **ne valide pas** le reste des cartes fictives de ce prototype.
- Les capacités actives individuelles ne sont **pas modélisées** : seule l'énergie suffisante pour payer un coût hypothétique 1, 2 ou 3 est affichée. Aucun effet historique inventé.

## 3. Méthode de calcul exact

Fixtures : 6 athlètes A et 6 B, à quatre statistiques dont la somme est 30. Pour chacune des trois manches **préprogrammées de laboratoire** (R1 FORCE×2+TECHNIQUE ; R2 ENDURANCE×2+IMPACT ; R3 TECHNIQUE×2+ENDURANCE), chacun des 36 couples peut attaquer dans les deux sens = **72 confrontations orientées par manche**, **216 cas de base**.

On calcule :
1. Score sportif sans action : \`2 × principale + secondaire\`, pour chaque titulaire.
2. Attribution des PC sportifs : victoire +3, égalité +1 chacun, défaite 0.
3. Action « Défi » : si \`IMPACT attaquant > TECHNIQUE défensive + parade fixée\`, alors **+1 PC tactique** au défieur et **1 Pression** sur le défenseur. La performance sportive reste identique si aucun K.O. n'a lieu.
4. Action « Soutien » : modification du seul **score sportif** comme écrit dans la fixture, puis nouvelle attribution des PC sportifs ; aucun PC tactique direct.
5. Mesure comparée : \`(PC personnels − PC adverses après action) − (PC personnels − PC adverses avant action)\`. Le soutien et le Défi ont tous deux coûté **une énergie**. Les cas de victoire/tie/perte utilisent les mêmes règles D-01.
6. Un « soutien meilleur » signifie **strictement davantage de variation d'écart de PC** que le Défi ; l'égalité est comptée séparément.
7. Dans la matrice exhaustive, le défenseur part de **zéro Pression** pour exclure un K.O. nécessitant un remplacement. L'outil individuel accepte une Pression initiale 1 et exige un remplaçant explicite lorsqu'un K.O. rendrait l'attribution sportive non déterminée.

**Limites majeures :** la carte est supposée présente dans la main, les actions de fenêtres différentes sont comparées **a posteriori** à information égale, l'adversaire ne lance aucun Défi dans ce sous-modèle, les bonus de long terme des Équipements ne sont pas chiffrés, la récompense de pioche après K.O. ne l'est pas non plus, et l'adversaire a une défense fixée. La comparaison ne rend pas ces actions mutuellement exclusives dans une vraie manche de 3 énergies : elle mesure uniquement la **valeur marginale immédiate d'une énergie**.

## 4. Résultats exacts de laboratoire — sans Parade, avant toute Pression

Chaque ligne compare **72 confrontations orientées**. Les totaux « soutien meilleur » + « Défi meilleur » + « égalité » valent 72.

| Manche | Soutien fictif à 1 énergie | Soutien meilleur | Défi meilleur | Égalité |
|---|---|---:|---:|---:|
| 1 | T1 Ajustement +2, Technique secondaire | **33** | 12 | 27 |
| 1 | T3 Impulsion +1 | 24 | 17 | 31 |
| 1 | T4 Élan initial +2 | **33** | 12 | 27 |
| 1 | E1 Matériel polyvalent +1 | 24 | 17 | 31 |
| 1 | E2 Matériel technique, bonus immédiat 0 | 0 | 28 | 44 |
| 1 | EV1 Second souffle +1 (sans retard initial) | 24 | 17 | 31 |
| 2 | T3 Impulsion +1 | 23 | 21 | 28 |
| 2 | T4 Élan initial +2 | **35** | 14 | 23 |
| 2 | E1 Matériel polyvalent +1 | 23 | 21 | 28 |
| 2 | E2 Matériel technique, bonus immédiat 0 | 0 | 28 | 44 |
| 2 | EV1 Second souffle +1 (sans retard initial) | 23 | 21 | 28 |
| 3 | T3 Impulsion +1 | 13 | 22 | 37 |
| 3 | T4 Élan initial +2 | 21 | 20 | 31 |
| 3 | E1 Matériel polyvalent +1 | 13 | 22 | 37 |
| 3 | E2 Matériel technique +2 | 21 | 20 | 31 |
| 3 | EV1 Second souffle +1 (sans retard initial) | 13 | 22 | 37 |

**Règle légale importante :** T1 ne peut être joué dans R2 ou R3, où la statistique secondaire n'est pas TECHNIQUE ; ce cas est indiqué comme **non applicable**, pas comme une défaite du soutien.

**Autre limite :** E2 procure un bonus sportif immédiat de zéro en R1/R2, mais sa persistance peut en faire un investissement pour R3. Le tableau **ne prouve pas** qu'il serait inutile ou dominé. T4 est joué avant la confrontation et peut être perdu si son titulaire est K.O., effet non compris dans ces lignes.

### Influence d'une Parade adverse fixe

Au R1, T1 +2 vs Défi :
- **Sans Parade :** soutien meilleur 33/72, Défi meilleur 12/72, égalité 27/72.
- **Avec Parade (+1 Technique) :** soutien meilleur 33, Défi meilleur 6, égalité 33.
- **Avec Parade + T2 (+2 Technique) :** soutien meilleur 33, Défi meilleur 0, égalité 39.

Le soutien continue de modifier les mêmes résultats sportifs, tandis que la Parade réduit le nombre de Défis réussis. La condition « Parade + T2 à disposition » ne reflète pas une probabilité réelle de main ; elle est imposée par le scénario.

## 5. Décisions de conception V1.4

**À conserver pour le prochain laboratoire, pas à canoniser :**
- Le **Défi** peut avoir une vraie valeur tactique lorsque le score sportif est trop éloigné pour qu'une Technique à petit bonus inverse le résultat ; il impose en plus une Pression qui peut devenir stratégique sur plusieurs manches.
- Les **soutiens sportifs** peuvent parfois créer un gain de PC **strictement supérieur** à un Défi qui ne donne qu'un PC tactique, parce que le score sportif attribue 3/1/0 PC et peut retirer simultanément des PC à l'adversaire.
- La **Parade** consomme elle aussi une énergie : son intérêt doit être mis en balance avec l'active ou la FINALE non jouées, et pas uniquement avec la fréquence des Défis bloqués.
- Le **K.O. à deux Pressions n'est pas modifié**. Toute politique le rendant arbitrairement plus fréquent doit être considérée comme une variante, pas comme une correction validée.
- Sans effets et textes exacts d'actives historiques approuvés, **aucune conclusion** sur « Défi vs active » n'est justifiée. Le simulateur indique seulement si une active resterait payable après la dépense.

## 6. Tests et intégrité

- Code autonome statique \`game-lab/opportunite-v14.html\`, aucun réseau ni compte.
- Vérification JavaScript de 16 contrôles ciblés : totaux de statistiques, PC 3/1/0, confrontations orientées, valeurs R1/R2/R3, énergie insuffisante, K.O. remplaçant non choisi puis explicitement choisi, maintien possible d'une active coût2 après dépense1 sur réserve3 et rendu HTML.
- Correction complémentaire : T1 est **explicitement non applicable** aux manches 2 et 3, et le comparateur gère ces cas sans division par zéro ni affichage \`NaN\` (5 contrôles de régression réussis).
- Vérifications réalisées avec DOM simulé ; **aucune validation visuelle sur un navigateur réel de l'utilisateur**.
- Un calcul Python indépendant sur les 216 confrontations de base a confirmé les décomptes sans Parade figurant au tableau.

## 7. Prochaine étape

Construire un **analyseur de décisions sur la manche entière**, avec combinaison légale de 0, 1 ou 2 soutiens, Défi, éventuelle Parade, et **capacité active uniquement après récupération et validation de son texte exact**. Mesurer l'usage des ressources sur les 3 énergies, et comparer les dénouements dans des parties numériques humaines sans jamais imposer de playtest papier. Distinguer l'espérance d'une stratégie selon les informations réellement connues au moment de chaque fenêtre.

**GO : poursuite du travail numérique. NO-GO : modification D-01/D-03/D-05, fabrication de cartes officielles, impression, engagement des artistes.**
