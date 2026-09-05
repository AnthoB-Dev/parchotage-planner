# Catalogue des parchemins Dofus 3 — API DofusDB

Résolution du ticket [Catalogue des parchemins Dofus 3 via l'API DofusDB](https://github.com/AnthoB-Dev/parchotage-planner/issues/2).

> Données issues de DofusDB. Utilisation soumise à la LPNC-IA 1.0 (non commerciale, partage à l'identique, attribution). Voir [licence complète](https://api.dofusdb.fr/) et ticket de conformité lié.

## Source et méthode

- API publique **DofusDB** : `https://api.dofusdb.fr` (pas le site web dofusdb.fr, protégé).
- Endpoint : `GET /items?typeId=76` (type « **Parchemin de caractéristique** », super-type « Consommable »).
- Type découvert par balayage des 260 typeIds d'items (type 76 ; noter que le type 82, qui était « Parchemin » dans Dofus 2, est « Bouclier » dans Dofus 3 — les ids ont changé).
- Échantillon brut : `data/dofusdb-items-type76-parchemins-caracteristique.json` (25 items, champ `data`), snapshot daté du 2026-09-05.
- **Comment les limites sont encodées** : uniquement dans le **texte FR du champ `description`** (tooltip in-game) — aucune structure type « usage limit » (champ `importantNotice` vide, `criterions` vide, effet non contraint). C'est le texte qui porte la condition d'utilisation. `price` = prix de base kamas (champ `price`), niveau 1, `usable: true`.

## Catalogue consolidé (6 stats × 4 paliers = 24 parchemins)

Chaque palier existe pour les 6 caractéristiques (Vitalité, Sagesse, Force, Intelligence, Chance, Agilité). Tous : niveau 1, +1 point de parchotage sur la stat (montant non structuré dans l'API — voir ambiguïtés).

Condition d'utilisation (texte officiel, « points additionnels de <stat> » = points de parchotage déjà consommés sur cette stat) :

| Paller | Utilisable tant que <stat> < | Prix de base (kamas, champ `price`) | effectId | characteristic |
|---|---|---|---|---|
| Petit Parchemin | 25 | 1 000 | 607/610/606/608/609/611 | 10/11/12/13/14/15 |
| Parchemin | 50 | 2 500 | idem | idem |
| Grand Parchemin | 80 | 5 000 | idem | idem |
| Puissant Parchemin | 100 | 8 000 | idem | idem |

Tableau détaillé par item (id API, slug, prix) :

| Stat | characteristic | Petit | Parchemin | Grand | Puissant |
|---|---|---|---|---|---|
| Force | 10 | 683 | 795 | 796 | 797 |
| Vitalité | 11 | 806 | 807 | 808 | 810 |
| Sagesse | 12 | 802 | 803 | 804 | 805 |
| Chance | 13 | 809 | 811 | 812 | 814 |
| Agilité | 14 | 798 | 799 | 800 | 801 |
| Intelligence | 15 | 686 | 815 | 816 | 817 |

Mapping effectId → stat (sur chaque palier) : 607=Force, 610=Vitalité, 606=Sagesse, 608=Chance, 609=Agilité, 611=Intelligence. `baseEffectId` : 26/32 selon stat.

## Item spécial hors paliers

- **Parchemin accélérant** (id 33672, type 76) : 6 effets (10→15), prix 0, non marchand. Texte : « donne des points additionnels de caractéristique dans une limite de 100 points maximum par caractéristique ». Hors périmètre v1 (non acheté en kamas) ; à écarter de l'optimisation.

## Réponses aux questions du ticket

- **Peut-on atteindre 100 dans chaque stat ?** Oui. Chaque stat a son Puissant Parchemin, utilisable tant que la stat < 100 → plafond 100 atteignable stat par stat.
- **Que peut-on atteindre sans Parchemin puissant ?** 80 par stat (le Grand Parchemin, dernier palier non-puissant, est utilisable tant que < 80). Le passage 80 → 100 exige le Puissant.
- **Le Puissant a-t-il une limite ?** Oui — mais c'est la sienne : utilisable tant que la stat < 100. Il n'est pas « illimité » ; il couvre la tranche haute que les autres paliers n'atteignent pas. (Corrige l'hypothèse CONTEXT « tous les parchemins sauf le puissant portent une limite d'utilisation ».)
- **Structure de paliers pour l'optimisation** : à un niveau de déjà-parchoté donné, plusieurs paliers peuvent être légaux (ex. stat=24 : petit ET parchemin ET grand ET puissant) → le plus économique gagne. C'est l'entrée du ticket [Modèle d'optimisation du parchotage](https://github.com/AnthoB-Dev/parchotage-planner/issues/3).

## Ambiguïtés / limites de la source

1. **Montant par parchemin non structuré** : `possibleEffects[].value = 0`, `effects[]` dérivés : `from:1/to:0` pour petit/parchemin/grand, `from:2/to:102` pour puissant — interprétation hasardeuse (pas une plage de dégâts). La règle connue « +1 point par parchemin » et le texte « gagner des points » concordent ; à confirmer côté modèle (#3) si besoin.
2. **Règles globales au personnage** (ex. plafond total sur les 6 stats, ordre d'utilisation) : non visibles au niveau item. Le texte ne mentionne que la condition par stat. Règle d'ensemble à verrouiller dans #3 (grilling avec l'humain).
3. `price` (1000/2500/5000/8000) est le **prix de base** du champ item ; le v1 prévoit des prix kamas saisis à la main → utile comme valeur par défaut éventuelle, pas comme vérité marché.
4. Licence API **LPNC-IA 1.0** (affichée sur `https://api.dofusdb.fr/`) : usage non commercial, attribution obligatoire, partage à l'identique, restrictions sur l'usage IA. À arbitrer pour un outil déployé publiquement et co-construit avec IA → ticket de conformité dédié.

## Sources

- API DofusDB, `GET /api.dofusdb.fr/items?typeId=76` — snapshot ci-joint (licence ci-dessus).
- Licence DofusDB : https://api.dofusdb.fr/
- Glossaire domaine : CONTEXT.md (repo).
