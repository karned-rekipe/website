# Release d'orientation - Shopping

## Intention

La release `shopping` doit transformer un planning confirmé en liste de courses actionnable.

Pour l'utilisateur, l'objectif est de réduire les oublis, consolider les quantités, regrouper les achats de manière pratique et garder une liste simple à utiliser en magasin.

## Valeur attendue

La release doit apporter :

- une liste générée depuis les repas planifiés ;
- une consolidation par ingrédient ;
- un regroupement par rayon ou fournisseur ;
- des cases à cocher ;
- des ajouts manuels ;
- une possibilité de partager ou déléguer une sous-liste ;
- un contrôle simple des quantités incohérentes.

## Périmètre proposé

Le premier lot devrait couvrir :

| Capacité | Orientation |
|---|---|
| Génération | Depuis un plan de repas confirmé. |
| Consolidation | Regrouper les ingrédients identiques et additionner les quantités compatibles. |
| Organisation | Trier par rayon, groupe ou fournisseur. |
| Usage magasin | Cocher, masquer les éléments faits, garder l'ordre utile. |
| Ajout manuel | Ajouter un produit non issu d'une recette. |
| Sous-listes | Assigner une partie de la liste à une personne. |
| Fournisseurs | CRUD simple des fournisseurs et rattachement optionnel. |

Cette orientation reprend les idées de travail existantes : case à cocher, envoi de sous-liste à une personne, CRUD fournisseur et liste fournisseur.

## Hors périmètre du premier lot

Le premier lot ne doit pas encore porter :

- une intégration e-commerce ;
- un stock domestique complet ;
- une optimisation prix avancée ;
- une reprise des données legacy de courses ;
- une conversion d'unités exhaustive ;
- une gestion multi-magasins complexe.

## Modèle métier à stabiliser

Objets probables :

- `ShoppingList` : liste pour une période ou un plan ;
- `ShoppingItem` : produit à acheter, quantité, unité, statut ;
- `Supplier` : fournisseur ou lieu d'achat ;
- `ShoppingListStatus` : `draft`, `to_check`, `validated`, `in_progress`, `done`.

Une distinction est importante : un ingrédient de recette n'est pas toujours un produit à acheter. Le domaine `shopping` doit donc pouvoir mapper progressivement les ingrédients vers des produits achetables sans casser le catalogue recette.

## API et intégrations

Le service `shopping` devra :

- générer une liste depuis un `MealPlan` confirmé ;
- lire les lignes d'ingrédients hydratées via `recipe` et `meal-planner` ;
- exposer le CRUD des listes, items et fournisseurs ;
- gérer les statuts de coche ;
- exposer des outils MCP pour contrôle et assistance.

Le frontend `gwel` devra offrir une liste dense, utilisable sur mobile, avec coches rapides, regroupements et actions compactes.

## Rôle de l'agent

`shopping-agent` doit aider à contrôler la liste :

- repérer les doublons probables ;
- signaler les unités incompatibles ;
- proposer un regroupement par rayon ;
- vérifier les quantités aberrantes ;
- préparer une sous-liste pour une personne.

Il ne doit pas acheter ni valider automatiquement.

## Questions à valider

- Quel est le niveau minimal de conversion d'unités nécessaire ?
- Faut-il gérer le stock dès cette release ou seulement prévoir le raccord futur ?
- Comment partager une sous-liste au démarrage : export texte, lien, notification ?
- Les fournisseurs sont-ils des magasins, des producteurs, des rayons, ou les trois ?
- Quel niveau de contrôle carbone / saison doit être visible dans la liste ?

## Critère de réussite

La release est réussie si un planning réel peut produire une liste de courses utilisable en magasin, ajustable manuellement, et suffisamment structurée pour réduire les oublis sans imposer une gestion de stock complète.
