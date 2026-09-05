# Parchotage Planner

Outil web statique qui calcule la combinaison de parchemins la moins chère pour parchoter les statistiques d'un personnage Dofus 3, en respectant les règles officielles de parchotage. Catalogue source : liste statique embarquée dans l'outil (fournie et validée par l'auteur). v1 : coût en kamas uniquement.

## Language

**Parchotage**:
Action d'augmenter une statistique de base d'un personnage en consommant des parchemins, jusqu'à un plafond.
_Avoid_: boos, parchottage

**Parchemin**:
Objet consommable de Dofus 3 qui confère des points de parchotage sur une statistique quand il est utilisé. Le catalogue (tous les types, normaux comme puissants) est embarqué dans l'outil en données statiques.
_Avoid_: scroll, livre de sorts

**Paliers d'utilisation (d'un parchemin)**:
Condition d'utilisation d'un parchemin, exprimée sur les points additionnels (déjà-parchoté) de la stat : Petit < 25, Parchemin < 50, Grand < 80, Puissant < 100. À un niveau donné, plusieurs paliers peuvent être légaux en même temps.
_Avoid_: palier de rareté, niveau

**Parchemin puissant**:
Palier conférant +2 points de parchotage (les trois autres paliers : +1), utilisable tant que la stat < 100. Seul à couvrir la tranche 80 → 100. Comme il donne un nombre pair de points, un déjà-parchoté ≥ 80 impair est un état inatteignable en jeu.
_Avoid_: parchemin supérieur

**Point de parchotage**:
Unité comptée par stat : +1 par Petit/Parchemin/Grand, +2 par Puissant. C'est la quantité que fait monter le déjà-parchoté.

**Statistique parchotable (stat)**:
Une des six caractéristiques recevant du parchotage : Vitalité, Sagesse, Force, Intelligence, Chance, Agilité.
_Avoid_: carac, attribut

**Cap de parchotage**:
Nombre maximal de points de parchotage qu'une statistique peut recevoir : 100.
_Avoid_: max, plafond par niveau

**Déjà-parchoté**:
Points de parchotage déjà consommés sur une statistique (défaut 0, modifiable).
_Avoid_: base actuelle

**Objectif de parchotage**:
Points de parchotage visés par statistique (défaut 100, modifiable). Le besoin en parchemins = objectif − déjà-parchoté. Objectif et déjà-parchoté bornés à [0, 100].

**Recette de parchotage (recette)**:
Choix des quantités de parchemins par palier et par stat qui minimise le coût en kamas pour atteindre l'objectif. Calculé par plus court chemin (DP) sur le niveau de déjà-parchoté 0 → 100, stat par stat (aucun cap global au personnage). Départage à coût égal : nombre de parchemins minimal, puis palier le plus faible.
_Avoid_: combo, build, répartition optimale

**Kamas**:
Monnaie principale de Dofus. Coût de référence du v1.
_Avoid_: k

**Avitons**:
Monnaie secondaire. Coût en avitons hors périmètre v1.
_Avoid_: avitons → achetés via le Kolizéum

**Catalogue (statique)**:
Liste des parchemins embarquée dans l'outil (24 items : 6 stats × 4 paliers), fournie et validée par l'auteur. Aucune dépendance à une API externe au runtime ni au build.
_Avoid_: API externe, source distante
