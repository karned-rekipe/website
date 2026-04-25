# Etat actuel

## Vue courte

Le projet n'est pas au stade idée. Le socle recette est déjà avancé et les deux prochains domaines existent comme bases techniques.

| Domaine | Etat | Lecture |
|---|---|---|
| Recettes | Fonctionnel en consolidation | Le backend et le frontend ont été retravaillés autour de catalogues référencés. |
| Planification | Socle technique créé | Le service existe, mais le modèle métier de release reste à valider. |
| Courses | Socle technique créé | Le service existe, mais la génération de liste reste à construire. |
| Agents IA | Socles créés par domaine | Les agents doivent rester des assistants branchés sur les APIs et MCP. |

## Recettes

Le travail récent a consolidé le volet recette :

- recettes avec références UUID vers ingrédients, équipements et tags ;
- catalogues dédiés pour ingrédients, équipements, tags, groupes et rayons ;
- hydratation des recettes à la lecture ;
- création et édition de recette via le frontend ;
- statut `draft` pour une recette sans ingrédient ;
- exclusion des recettes `draft` via `meal_planner_eligible=true` ;
- suppression refusée si une ressource est utilisée ;
- détection et fusion de doublons ingrédients / équipements ;
- listes frontend plus denses, réutilisables et restaurables.

La règle métier retenue est volontairement simple : une recette peut être créée avec seulement un nom et un nombre de portions. Elle devient exploitable pour la planification quand elle contient au moins un ingrédient.

## Données

La base historique SQL a été analysée. Elle contient notamment :

- environ 300 recettes ;
- environ 400 ingrédients ;
- des équipements ;
- des étapes partielles ;
- plusieurs années d'historique de planification.

La cible actuelle est MongoDB, avec conservation des identifiants legacy utiles pour tracer la migration.

## Interface

Le frontend `gwel` expose déjà :

- `/recipes`
- `/recipes/new`
- `/recipes/:id`
- `/recipes/:id/edit`
- `/ingredients`
- `/equipment`
- `/tags`
- `/settings/ingredients`
- `/planning`
- `/shopping`

Les écrans `planning` et `shopping` sont des points d'entrée prêts à brancher, pas encore les produits métier complets.

## Ce qui reste ouvert

Les prochains arbitrages structurants portent sur :

- le mode exact de versioning des recettes ;
- la profondeur du modèle de préférences alimentaires ;
- la reprise fine de l'historique de planification hybride ;
- la frontière initiale entre stock domestique et courses ;
- le niveau d'autonomie acceptable des recommandations IA.

## Ce qui n'est pas encore le sujet

Cette première trajectoire ne cherche pas à livrer :

- une optimisation nutritionnelle médicale ;
- un e-commerce ;
- une gestion de stock complète ;
- une automatisation sans validation humaine ;
- une architecture distribuée plus complexe que nécessaire.
