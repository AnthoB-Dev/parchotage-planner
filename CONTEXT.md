# Parchotage Planner

Outil web statique qui calcule la combinaison de parchemins la moins chère pour parchoter les statistiques d'un personnage Dofus 3, en respectant les règles officielles de parchotage. Catalogue source : API DofusDB. v1 : coût en kamas uniquement.

## Language

**Parchotage**:
Action d'augmenter une statistique de base d'un personnage en consommant des parchemins, jusqu'à un plafond.
_Avoid_: boos, parchottage

**Parchemin**:
Objet consommable de Dofus 3 qui confère +1 point de parchotage sur une statistique quand il est utilisé. Le catalogue (tous les types, normaux comme puissants) est tiré de l'API DofusDB.
_Avoid_: scroll, livre de sorts

**Parchemin puissant**:
Variante de parchemin qui n'est pas soumise à la limite d'utilisation des parchemins normaux. Rôle exact à verrouiller quand le catalogue DofusDB est résolu.
_Avoid_: parchemin supérieur

**Point de parchotage**:
Unité conférée par un parchemin (+1). C'est la quantité comptée par statistique.

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
Points de parchotage visés par statistique (défaut 100, modifiable). Le besoin en parchemins = objectif − déjà-parchoté.

**Kamas**:
Monnaie principale de Dofus. Coût de référence du v1.
_Avoid_: k

**Avitons**:
Monnaie secondaire. Coût en avitons hors périmètre v1.
_Avoid_: avitons → achetés via le Kolizéum

**DofusDB**:
Base de données communautaire (dofusdb.com) exposant une API du catalogue d'items Dofus 3. Source de vérité pour la liste des parchemins.
_Avoid_: wiki non structuré
