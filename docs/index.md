# Rekipe

Rekipe est un projet personnel et familial pour organiser les repas du quotidien : garder une mémoire fiable des recettes, préparer les repas de la semaine, puis transformer ces repas en courses utiles.

L'objectif n'est pas de faire une application de cuisine de plus. L'objectif est de réduire la friction réelle du foyer : retrouver une recette, savoir quoi manger, anticiper les préparations, acheter ce qu'il faut et éviter les pertes.

<div class="grid" markdown>

<div class="card" markdown>
## Recettes

Le socle en cours de stabilisation. Il centralise les recettes, ingrédients, équipements, tags, saisons et sources.

<span class="status">En construction avancée</span>
</div>

<div class="card" markdown>
## Planification

Le prochain lot. Il doit transformer les recettes actives en menus hebdomadaires simples à ajuster.

<span class="status">Release à cadrer</span>
</div>

<div class="card" markdown>
## Courses

Le troisième lot. Il doit produire des listes de courses contrôlables à partir des repas planifiés.

<span class="status">Release à cadrer</span>
</div>

</div>

## Pour qui ?

Rekipe vise d'abord un usage de foyer : une famille, plusieurs personnes qui peuvent consulter ou modifier les données, et une base isolée par foyer.

Le produit reste volontairement pragmatique :

- aider à choisir quoi manger ;
- capitaliser les bonnes recettes ;
- cuisiner davantage avec les saisons ;
- réduire les oublis et le gaspillage ;
- garder l'IA comme assistance, pas comme pilote automatique.

## Ce qui existe déjà

La nouvelle base technique est en place :

- un backend `recipe` en FastAPI ;
- un frontend `gwel` en Vue 3 ;
- des socles techniques pour `meal-planner`, `meal-planner-agent`, `shopping` et `shopping-agent` ;
- un pack de cadrage complet dans le repo `recipe-project`.

Le cadrage de référence reste disponible ici pour les contributeurs ayant accès à l'organisation GitHub :

- [Pack de cadrage interne sur GitHub](https://github.com/karned-rekipe/recipe-project/blob/main/docs/README.md)

## Prochaine lecture

- [Comprendre Rekipe](comprendre-rekipe.md) pour la vision utilisateur.
- [Etat actuel](etat-actuel.md) pour savoir ce qui est déjà fait.
- [Trajectoire](trajectoire.md) pour comprendre les prochaines étapes.
- [Contributeurs](contributeurs.md) pour entrer dans les repos et l'architecture.
