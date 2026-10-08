# Site de l'association étudiante — Évaluation Git & GitHub

## Équipe

| Pseudonyme GitHub | Nom | Prénom | Rôle |
| @5wVn | BARRET | Olivier | Étudiant 2 |
| @Bogogce | DIEUDONNE | Swan | Étudiant 1 |
| @taounisami-netizen | TAOUNI | Sami | Étudiant 3 |


## Workflow
Git Flow : `main` (versions stables), `develop` (intégration), `feature/*`, `bugfix/*`, `release/*`, `hotfix/*`.
**1. Quel est l'intérêt de séparer développements en cours et versions stables ?**
*Réponse de Sami TAOUNI (@taounisami-netizen), Étudiant 1*
Comme ça, `main` reste toujours propre et utilisable. On bosse sur `develop` sans risquer de casser la version en prod si un truc n'est pas fini ou bugué.

**2. Pourquoi imposer une revue de code avant intégration ?**
*Réponse de Sami TAOUNI (@taounisami-netizen), Étudiant 1*
Un deuxième regard repère des erreurs qu'on ne voit pas soi-même. Et tout le monde sait ce qui a changé dans le code. Ici, c'est en revue qu'on a vu un reste de conflit (`HEAD`) oublié dans `style.css`.

**3. Quelles situations provoquent un conflit Git et pourquoi sa résolution n'est-elle pas toujours automatique ?**
*Réponse de Sami TAOUNI (@taounisami-netizen), Étudiant 1*
Quand deux branches modifient les mêmes lignes d'un fichier, ou qu'une branche modifie un fichier que l'autre a supprimé. Git ne peut pas deviner quelle version est la bonne, donc c'est à nous de choisir quoi garder.