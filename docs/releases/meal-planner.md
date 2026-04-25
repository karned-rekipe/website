# Release d'orientation - Meal planner

## Intention

La release `meal-planner` doit transformer la base de recettes en outil concret de planification hebdomadaire.

Pour l'utilisateur, l'objectif est simple : répondre rapidement à "qu'est-ce qu'on mange cette semaine ?", puis ajuster le plan sans perdre la main.

## Valeur attendue

La release doit apporter :

- une semaine de repas lisible ;
- l'affectation rapide de recettes actives ;
- la prise en compte du nombre de personnes ;
- des notes ou tâches de préparation ;
- des suggestions saisonnières utiles ;
- une première lecture de l'équilibre et de la variété de la semaine.

## Périmètre proposé

Le premier lot devrait couvrir :

| Capacité | Orientation |
|---|---|
| Planning hebdomadaire | Vue semaine, repas par jour, statut du plan. |
| Repas | Date, moment, nombre de personnes, commentaire. |
| Affectation | Recette active, ingrédient simple ou note libre. |
| Eligibilité | Utiliser uniquement les recettes `active` exposées par `recipe`. |
| Suggestions | Recommandations simples selon saison, historique et variété. |
| Préparation | Notes de type "préparer", "décongeler", "mettre à mariner". |
| Indicateurs | Saison, variété, équilibre perçu, empreinte carbone plus tard. |

Cette orientation reprend les idées de travail existantes : "j'ai ça dans mon frigo", suggestion du moment selon la saison, empreinte carbone de la semaine et équilibre de la semaine.

## Hors périmètre du premier lot

Le premier lot ne doit pas encore porter :

- une optimisation nutritionnelle fine ;
- une gestion complète du stock ;
- une recommandation autonome sans validation ;
- un moteur complexe de contraintes ;
- la génération définitive des courses, qui relève du domaine `shopping`.

## Modèle métier à stabiliser

Objets probables :

- `MealPlan` : plan sur une période, souvent une semaine ;
- `MealSlot` : jour + moment de repas ;
- `MealItem` : recette, ingrédient simple, note ou tâche ;
- `MealPlanStatus` : `draft`, `confirmed`, `done`, `abandoned`.

Le point sensible est l'historique legacy : certaines lignes sont des recettes, d'autres des ingrédients seuls ou des tâches libres. Le modèle doit accepter cette réalité sans forcer trop tôt une normalisation artificielle.

## API et intégrations

Le service `meal-planner` devra :

- exposer le CRUD des plans ;
- lire les recettes via le contrat `meal_planner_eligible=true` ;
- conserver le nombre de personnes par repas ;
- préparer la génération future de courses ;
- exposer des outils MCP pour l'agent de planification.

Le frontend `gwel` devra offrir une vue semaine simple, dense, modifiable, avec sélection de recettes et ajout de notes.

## Rôle de l'agent

`meal-planner-agent` doit assister, pas décider seul.

Premières capacités utiles :

- proposer une semaine à partir de contraintes simples ;
- suggérer des recettes de saison ;
- éviter les répétitions évidentes ;
- tenir compte d'un signal "j'ai ça dans mon frigo" ;
- expliquer brièvement pourquoi une suggestion est proposée.

## Questions à valider

- Quels moments de repas sont nécessaires au démarrage ?
- Le planning doit-il être uniquement hebdomadaire ou accepter toute période ?
- Comment représenter précisément les notes de préparation ?
- Quel niveau minimal d'équilibre alimentaire est attendu sans créer un moteur nutritionnel ?
- Comment exploiter l'historique de planification sans importer ses ambiguïtés telles quelles ?

## Critère de réussite

La release est réussie si l'utilisateur peut préparer une semaine réelle de repas, l'ajuster rapidement, et disposer d'une base suffisamment structurée pour déclencher ensuite une liste de courses fiable.
