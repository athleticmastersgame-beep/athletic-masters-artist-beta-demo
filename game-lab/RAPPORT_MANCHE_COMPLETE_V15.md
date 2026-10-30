# ATHLETIC MASTERS — Game Design V1.5 / Analyseur de manche complète

**Date :** 30 octobre 2026  
**STATUT :** PROTOTYPE NUMÉRIQUE DE LABORATOIRE, NON CANONIQUE.  
**Périmètre :** Championnat hybride. Aucun playtest papier, aucune modification de carte historique, d'œuvre ou des règles approuvées.

## 1. Livrable

**[Ouvrir l'analyseur de manche complète V1.5](https://athleticmastersgame-beep.github.io/athletic-masters-artist-beta-demo/game-lab/manche-v15.html)**

Page HTML autonome et statique avec export JSON des combinaisons et du contexte. Aucun réseau, compte, paiement, téléversement ni base de données. Elle n'altère pas le Championnat numérique V1.2 ; elle en constitue un **outil complémentaire de décision et de contrôle**.

### Données reprises et limites d'autorité

- D-01, D-03 modèle A et D-05 V0.4 : validés pour **anciens playtests uniquement**. Trois manches, 3/1/0 PC sportifs, plafond +1 PC tactique par joueur/manche, 3 énergies par manche sans report, Défi coût 1, Parade coût 1 apportant +1 Technique, Défi réussi seulement si IMPACT > Technique défensive, 1 Pression par succès, K.O. à 2 Pressions sur **le même athlète**.
- D-02 V0.6 : **proposition NON VALIDÉE**. Hypothèses : équipe de six, deck 14 soutiens, main 5 puis +2/+2, maximum 2 soutiens par manche et 1 soutien de coût zéro, fenêtres Préparation / Réaction / Finale, Équipement persistant, capacité active avec coût imprimé. Les sept soutiens T1/T2/T3/T4/E1/E2/EV1 sont **des fixtures fictives**, avec effets et coûts propres au laboratoire.
- Fiches V4 : quatre statistiques FORCE, TECHNIQUE, ENDURANCE, IMPACT, chacune entre 2 et 9, somme 30 ; passive/active et coût identiques entre C/R/SR/L. Aucune capacité réelle n'est simulée ni inventée.

## 2. Mécanisme de calcul V1.5

L'interface recueille : épreuve (3 manches préprogrammées), titulaire de chaque équipe, 5 emplacements de main (deux exemplaires maximum par identité), déclaration de Défi adverse fixée, défense adverse fixée, Pressions 0/1 sur chaque titulaire, remplaçants éventuels, équipement déjà attaché à chacun, cible d'un nouvel Équipement, PC relatifs au début de la manche pour EV1 et énergie réservée pour une éventuelle active.

L'algorithme **énumère, plutôt que devine** :
1. Sous-ensembles de soutiens légaux en **Préparation** (T4, E1, E2), au maximum deux soutiens par manche. L'interface de référence V1.2 n'autorise pas deux équipements posés dans une même Préparation ; cette même restriction est respectée dans V1.5.
2. **Défi / Passer** (coût 1 si Défi).
3. **Parade / Passer** si le Défi adverse est fixé à « oui », et éventuellement T2 (coût 0) si Parade payée, dans la limite d'un soutien gratuit et du plafond global.
4. Résolution des deux Défis selon IMPACT strictement supérieur à la TECHNIQUE défensive. Attribution d'1 PC tactique par succès ; Pression et K.O. éventuels.
5. Si K.O. : remplacement explicite nécessaire pour connaître la performance finale. Sans remplaçant désigné, le calcul de PC est marqué **indéterminé** ; l'outil ne suppose aucun athlète fictif par défaut.
6. **Finale** : T1 uniquement lorsque TECHNIQUE est secondaire ; T3 et EV1 selon leurs textes fictifs. Les bonus de Préparation liés au titulaire éliminé ne sont pas transférés. L'équipement éventuel sur un remplaçant peut être pris en compte si son porteur devient titulaire.
7. Performance sportive, PC sportifs (victoire +3, égalité +1 chacun, défaite 0) et PC tactiques (au plus +1 par côté). Le tableau classe par **écart de PC immédiat**, puis par potentiel conditionnel d'équipement pour les manches restantes et dépense énergétique. Ce tri **ne représente pas une politique optimale réelle**.
8. Une éventuelle **active** est traitée exclusivement comme une **réserve de coût 0/1/2/3**, sans effet mécanique inventé. Les plans qui ne laissent pas assez d'énergie pour ce coût sont exclus ; la valeur d'une active est donc **hors évaluation**.

### Équipement futur : avertissement essentiel

Le laboratoire calcule la somme arithmétique des bonus **sportifs possibles** de E1 (+1 par manche où son porteur concourt) ou de E2 (+2 si Technique est principale) sur les manches **restantes**. Ce chiffre n'est **ni une espérance statistique, ni un PC gagné** : il suppose que l'athlète concerné soit choisi lors de chaque manche pertinente, qu'il ne subisse pas de K.O. et que l'équipement reste applicable. Les futures pioches et la stratégie adverse ne sont pas simulées.

### Information imparfaite

Le simulateur connaît par **hypothèse de scénario** la décision de Défi adverse et sa réponse défensive au Défi du joueur. Dans une vraie partie, ces informations peuvent être secrètes au moment où le joueur choisit Préparation ou Défi. L'énumération de la manche est donc **rétrospective et conditionnelle**, pas une recommandation d'action à information parfaite pour le jeu réel.

## 3. Vérifications réalisées

### Contrôles ciblés

**22/22 contrôles fonctionnels réussis** en environnement JavaScript avec DOM simulé :
- 12 identités fictives avec quatre statistiques de somme 30 ;
- 7 identités de soutien ;
- plafond 3 énergies, 2 soutiens, 1 soutien gratuit et usage unique d'une carte de main ;
- absence de T2 sans Parade et de Parade sans Défi adverse ;
- réservation d'énergie pour une active hypothétique, y compris 3 énergies réservées ;
- K.O. à deux Pressions, score indéterminé sans remplaçant, score défini avec remplaçant ;
- équipement futur +2 conditionnel pour E1 acquis en manche 1, ciblage d'un remplaçant et interdiction d'un deuxième équipement sur un titulaire déjà équipé.

### Énumération des trois manches

**216 situations orientées** = 72 couples orientés × 3 épreuves, avec la main fictive fixe T4/E1/T2/T3/EV1, sans Défi adverse ni Parade, zéro Pression, aucune active réservée : **4 752 plans légaux distincts**, soit **22 par situation en moyenne**, **0 erreur et 0 violation de ressources**. Ce n'est pas 4 752 matchs : chaque plan représente seulement une série de décisions pour **une seule manche**.

L'analyse ne déduit **aucun taux de stratégie optimale** de ces cas : de nombreux plans peuvent donner les mêmes PC immédiats malgré des dépenses différentes. La page affiche donc aussi la variation contre « Passer » et le **plus faible coût en énergie permettant d'atteindre le meilleur écart connu**.

### Robustesse à mains et situations variables

**600 scénarios additionnels pseudo-aléatoires et reproductibles** : mains de cinq positions, certaines vides, Pressions, Défis et défenses, équipements, coût réservé d'active et choix de remplaçants variables. **5 892 plans distincts légaux** produits sans erreur ou dépassement des trois énergies / deux soutiens. Certains scénarios de K.O. ont volontairement été laissés sans remplaçant : les scores correspondants restent « indéterminés » plutôt que chiffrés à tort. Il ne s'agit pas de 600 parties complètes ni d'un test d'équilibre humain.

### Contrôles à faire ultérieurement

- Rendu réel dans différents navigateurs et tailles d'écran ;
- tests différentiels automatisés entre le moteur du Championnat V1.2 et l'analyseur V1.5 sur une **même séquence d'actions validée**, y compris les fenêtres simultanées ;
- comparaison de stratégies avant révélation des actions adverses, et pas uniquement avec des décisions adverses imposées ;
- intégration d'une active uniquement après extraction/validation de ses **effets exacts**, et tests de leur coût d'opportunité ;
- simulation sur 3 manches de l'attachement des équipements, des cartes restant en main, des pioches et des Pressions persistantes.

## 4. Constat de conception

**Fait calculé dans ces fixtures :** le plafond des ressources impose des choix d'allocation, et les sous-combinaisons comprenant un Défi et/ou deux soutiens ne sont pas toujours comparables à une simple action isolée. Certaines décisions donnent des PC identiques pour une dépense différente : le coût et la valeur future d'un Équipement doivent être distingués du score immédiat.

**Inférence de design (non vérifiée auprès de joueurs) :** la profondeur potentielle réside probablement dans les **combinaisons et le calendrier des décisions** (Préparation, menace de Défi, réaction et Finale), plutôt que dans une fréquence artificiellement élevée des K.O. Pour déterminer si cela se traduit en plaisir, il faudra des essais **numériques humains** et une règle précise sur la gestion des informations cachées.

**Décision :** conserver D-01 / D-03 / D-05 comme référence des anciens playtests ; **ne pas changer le seuil 2 Pressions**, ne pas réécrire les effets V4 et ne pas modifier D-02 silencieusement. Le simulateur est un outil de travail supplémentaire, pas une mise à jour canonique.

## 5. Prochaine étape recommandée

Développer un moteur **de trois manches reliées** utilisant les mêmes règles :
- suivre la main, la pioche +2/+2, l'attachement des équipements, les Pressions et les K.O. sur toute la rencontre ;
- comparer sur plusieurs graines, avec les mêmes décisions de chaque camp, la valeur d'un Équipement posé tôt plutôt que d'une Technique finale ;
- mesurer l'utilisation réelle des ressources et la fréquence de plans dominés ;
- préserver le caractère simultané des fenêtres et signaler toute information privée non observable.

**État : GO analyse numérique supplémentaire. NO-GO validation officielle, modification de fiches historiques, production artistique, papier ou commercialisation.**
