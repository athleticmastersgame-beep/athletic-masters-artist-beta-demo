# ATHLETIC MASTERS — Contrat de données universel V1.1 (PROPOSITION À VALIDER)

**Date :** 2026-10-30. **Statut :** architecture proposée, non canonique.  
**Objet :** préparer une collection jouable dans plusieurs modes et des cartes **entièrement finalisées par les artistes**.  
**Sources internes utilisées :** `02_STRUCTURE_ET_DONNEES_CANONIQUES_V4.md` (V4.1), `05_MODELE_FICHE_ATHLETE_V4.md` (V4.1), D-02 (PROPOSITION) et laboratoires numériques V0.8–V1.1. Les instructions historiques de direction artistique V4 et la décision plus récente de liberté créative des artistes demandent encore une conciliation explicite : aucune révision implicite de V4.

## 1. Principe : séparer quatre niveaux

- **A — Fiche maître de l'athlète :** les données historiques et mécaniques exactes, vérifiées et approuvées. **Invariantes entre variantes C/R/SR/L.**
- **B — Fiche de variante de carte :** scène historique, exploit, rareté, légende exacte et références visuelles. **La scène peut différer d'une rareté à l'autre**, mais ne change aucune valeur de jeu de l'athlète.
- **C — Fiche de l'œuvre / impression :** artiste, droits d'exploitation, fichiers source, vérifications, édition et impression. Ne modifie pas les règles de la carte.
- **D — Fiche de mode et d'autorisation :** légalité et éventuelle adaptation d'une **identité ludique** dans une version d'un mode. Non imprimée par défaut ; documentée dans le Codex. Cette couche est NOUVELLE et NON VALIDÉE.

L'ancienne règle de production selon laquelle l'image est la source de vérité est **explicitement fausse** : les valeurs proviennent de la fiche maître, l'image ne les atteste pas.

## 2. Couche A — Fiche maître (champs existants V4.1)

**Identité à remplir :**
- `athlete_id`, forme `P-XXX`, identifiant unique ;
- `collection`, `display_name_exact`, `full_name_verified`, `discipline_exact` ;
- `life_dates_exact`, `nationality_label_exact`, `flag_iso` et références de validation ;
- `historical_sources[]` : institution/auteur, URL, titre, date de consultation, décision de fiabilité ;
- `gameplay_stats` avec quatre clés exactes `FORCE`, `TECHNIQUE`, `ENDURANCE`, `IMPACT`, chacune entière de 2 à 9, somme exactement **30** ;
- `passive.name_exact`, `passive.effect_exact`, `active.name_exact`, `active.effect_exact`, `active.energy_cost` de 1 à 3 ;
- `gameplay_approval` et `historical_approval` distincts, auteur/date ;
- `master_revision`, source/version de la fiche.

**Règles de blocage :** une statistique absente, une somme différente de 30, un coût invalide, une capacité non sourcée/validée ou une identité historique encore `À_VALIDER` bloquent toute livraison artistique finale. Les capacités ne sont pas devinées à partir de vieilles images ou de prototypes.

**Attention :** le modèle V4 impose les deux capacités, leurs effets exacts et le coût. Le modèle multi-modes n'a **pas autorité** pour remplacer ces champs par des mots-clés sans consentement.

## 3. Couche B — Variante C / R / SR / L (V4.1)

- `card_id` = identifiant athlète + suffixe rareté, ex. `P-XXX-C` (exemple de format, pas une carte approuvée).
- `rarity` = `C` / `R` / `SR` / `L` uniquement dans les spécifications V4.1 ; les autres codes de rareté vus dans les explorations de collection **ne sont pas adoptés** par ce contrat.
- `historical_feat_exact`, `feat_date`, `history_caption_exact`, `primary_historical_source`.
- `visual_reference_source`, `visual_source_type`, présence/absence de photo directe, reconstruction artistique déclarée.
- `visual_difference_v4` et résultats des contrôles de différenciation propres à C/R/SR/L.
- `visual_approval` et `historical_caption_approval` séparés.
- Sur chaque variante, reprise littérale des statistiques, passive, active et coût **sans bonus de rareté**.

Les quatre scènes restent, d'après V4.1, à documenter indépendamment. Les contraintes de style artistique des anciens documents et la liberté de style donnée aux artistes sont encore en arbitrage : **aucune obligation artistique contradictoire ne doit être envoyée aux partenaires avant révision explicite**.

## 4. Couche C — Livraison de la carte complète par l'artiste (nouvelle proposition)

L'artiste rend **la carte complète**, non un simple visuel : illustration, mise en page, habillage, textes exacts et statistiques exactes.

**Avant commande / invitation :**
- fiche maître et variante verrouillées ;
- gabarit et spécifications techniques validées avec l'imprimeur ;
- droits, rémunération, crédit et utilisation des références réglés **par écrit**, sans affirmer aujourd'hui un budget existant ;
- liste des fichiers livrables et nombre de variantes précisés (une carte ou toute une collection).

**Dépôt attendu** : aperçu complet, fichier source modifiable, export haute qualité aux spécifications à définir, métadonnées d'auteur, références/éléments tiers, autorisation et historique des modifications. Aucun fichier n'est juridiquement cédé par le seul dépôt.

**Validation manuelle distincte** : conformité mécanique, conformité historique, lisibilité/technique, qualité artistique, droits et accord écrit. Une validation artistique n'est ni une validation historique ni une cession de droits.

**Paramètres encore non fixés** : fond perdu, marges de coupe, profil colorimétrique, résolution et format du fichier source. Le format nominal V4 de la carte est **63 × 88 mm**, sans pouvoir en déduire les valeurs de production supplémentaires.

## 5. Couche D — Registre de compatibilité par mode (PROPOSITION)

Pour chaque paire `play_card_id` × `ruleset_id` :
- `status`: `UTILISABLE`, `ADAPTE_REGLE`, `INACTIF`, `INTERDIT`, `EN_ETUDE` ;
- `ruleset_version` et `effective_from` ;
- `adapted_effect_exact` lorsque `ADAPTE_REGLE`, avec texte non ambigu ;
- `rules_reference` (livre + section numérotée), test de cohérence, approbation ;
- `deck_legality` et raison d'éventuelle exclusion.

**Exemple de laboratoire, non canonique :** T2 « Parade préparée » est jouable dans Championnat, mais incompatible dans Conquête et Relais. Le Codex la référence, mais les decks compatibles V1.0 de Conquête et Relais ne la distribuent pas. Les vrais soutiens historiques D-02 restent une proposition.

L'existence de `ADAPTE_REGLE` soulève un risque commercial : l'effet d'une carte peut différer selon le jeu. **À arbitrer avant impression** : conserver les textes physiques V4 pour un mode principal et référencer les adaptations dans le Codex, ou concevoir des effets suffisamment communs. Aucun des deux choix n'est adopté.

## 6. Versionnement et errata (PROPOSITION)

- `athlete_id` : identifiant de personne et de fiche maître ;
- `play_card_id` : identité ludique stable (pas nécessairement identique à une variante imprimée) ;
- `card_id` : variante C/R/SR/L ;
- `artwork_id` : œuvre autorisée, distincte de l'identité ludique ;
- `printing_id` / `edition_id` : impression et édition ;
- `ruleset_id` + `ruleset_version` : règlement applicable.

Une correction doit distinguer : erreur factuelle, erreur de traduction/typographie, clarification non fonctionnelle, changement mécanique et changement de légalité. Les errata restent consultables par date ; aucune modification silencieuse du sens imprimé.

## 7. Contrôles bloquants avant diffusion à des artistes

1. Tous les onze éléments obligatoires de la carte V4.1 sont présents, y compris en L.
2. Quatre statistiques entières 2–9, somme 30, ordre et libellé exacts.
3. Passive/active/coût identiques entre les quatre raretés d'un même athlète.
4. Chaque scène et exploit est vérifié, sourcé et validé individuellement.
5. Aucun drapeau, date, record ou décor historique inventé.
6. Différence de composition vérifiée avec le protocole V4 ; ne pas imposer en silence un style obsolète aux artistes.
7. Chaque mode déclare la compatibilité et ses exceptions, mais n'altère pas la fiche maître.
8. Tous les contrats, licences et conditions de création sont clarifiés avant usage commercial.
9. Règlement du mode principal, périmètre du deck et coûts mécaniques **stabilisés et explicitement approuvés**.

## 8. Feuille de route

**P0** : conserver V4 intact, auditer ses effets individuels sans changement.  
**P0** : tester la stabilité des mêmes quatre statistiques dans trois gameplays numériques.  
**P1** : définir le lexique d'effets et sa matrice de compatibilité.  
**P1** : formaliser le livre des règles générales, puis les trois livres de modes.  
**P1** : réviser explicitement le cahier des charges artiste, en conciliant liberté artistique actuelle et DA historique V4.  
**P2** : seulement ensuite, finaliser le gabarit de carte complète et inviter des artistes.

**Ce fichier est une spécification de travail, pas une modification du canon ATHLETIC MASTERS.**
