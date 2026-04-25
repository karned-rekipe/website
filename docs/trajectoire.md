# Trajectoire

## Le chemin cible

Rekipe avance par paliers.

| Palier | Objectif | Résultat attendu |
|---|---|---|
| Phase 1 | Stabiliser les recettes | Une base fiable, éditable, migrée et exploitable. |
| Phase 1.5 | Accélérer par l'agent recette | Saisir et normaliser plus vite, avec validation humaine. |
| Phase 2 | Planifier les repas | Construire une semaine de repas à partir des recettes actives. |
| Phase 3 | Générer les courses | Déduire une liste contrôlable depuis les repas planifiés. |
| Bascule finale | Remplacer l'ancien système | Retirer l'ancien outil quand les trois volets sont couverts. |

## Pourquoi cet ordre ?

La recette est la donnée de base. Tant que les recettes, les ingrédients et les saisons ne sont pas fiables, la planification et les courses produisent mécaniquement du bruit.

Le choix de trajectoire est donc :

1. consolider la mémoire recette ;
2. rendre la création de recette rapide ;
3. planifier avec des recettes suffisamment propres ;
4. transformer les repas en courses ;
5. retirer l'ancien système seulement quand l'ensemble est de nouveau couvert.

## Prochaines releases à orienter

Deux documents posent l'orientation générale avant spécification complète :

- [Release meal planner](releases/meal-planner.md)
- [Release shopping](releases/shopping.md)

Ces documents ne sont pas encore des spécifications détaillées. Ils servent à valider la direction produit, le périmètre initial et les arbitrages à traiter.

## Principe de delivery

Chaque release doit rester testable en usage réel :

- un périmètre utilisateur clair ;
- des données minimales mais solides ;
- des APIs simples ;
- un frontend utilisable ;
- des agents utiles mais optionnels ;
- des critères de passage visibles.
