# Parchotage Planner

Calculateur du coût du parchotage pour **Dofus 3**. En quelques clics, trouvez la combinaison de parchemins la moins chère pour atteindre vos objectifs de statistiques.

## ✨ L'outil

- **6 caractéristiques** : Vitalité, Force, Intelligence, Chance, Agilité, Sagesse — chacune parchotable jusqu'à 100 points.
- **4 types de parchemins** par statistique (Petit, Parchemin, Grand, Puissant) avec leurs conditions d'utilisation.
- **2 modes de calcul** :
  - **Optimal** — la combinaison la moins chère en kamas, calculée par programmation dynamique.
  - **Classique** — la répartition standard (25 Petit · 25 Parchemin · 30 Grand · 10 Puissant).
- **Prix modifiables** : adaptez les prix à ceux de votre serveur. Vos saisies sont enregistrées automatiquement dans votre navigateur.
- Thème clair / sombre.

## 🔗 Accéder à l'outil

<!-- TODO : ajouter le lien GitHub Pages une fois le déploiement effectué -->

→ L'outil est disponible ici : **_(lien à venir)_**

## 🚀 Utilisation

1. Ouvrez le lien ci-dessus (ou ouvrez `index.html` dans un navigateur).
2. (Optionnel) Ajustez les **prix des parchemins** à ceux pratiqués sur votre serveur.
3. Renseignez votre **déjà-parchoté** et votre **objectif** pour chaque statistique.
4. Lisez la **combinaison recommandée** et le **coût total estimé**.

## 🛠️ Fonctionnement

Outil 100 % statique (HTML/CSS/JS, aucun serveur). Le catalogue des parchemins est embarqué ; les prix et le thème sont stockés localement (`localStorage`). Aucune donnée n'est envoyée à un serveur.

## ⚖️ Notes

- Projet personnel **non commercial**.
- Données fournies par l'auteur, sans dépendance à une API externe.
- Les prix des parchemins varient selon les serveurs et dans le temps : les valeurs pré-remplies sont des exemples à adapter.
