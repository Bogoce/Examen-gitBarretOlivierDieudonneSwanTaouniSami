# Site de l'association étudiante — Évaluation Git & GitHub

## Équipe

| Pseudonyme GitHub   | Nom       | Prénom  |
| ------------------- | --------- | ------- |
| @bogoce             | BARRET    | Olivier |
| @5wVn               | DIEUDONNE | Swan    |
| @taounisami-netizen | TAOUNI    | Sami    |

## Workflow

Git Flow : `main` (versions stables), `develop` (intégration), `feature/*`, `bugfix/*`, `release/*`, `hotfix/*`.

**4. Quelle différence entre correction classique et correction urgente de production ?**
Une correction urgente sur la production s'appelle hotfix et doit se faire dans l'urgence souvent sur des problèmes critique alors qu'une correction classique se fait en livraison planifié.

**5. Pourquoi répercuter une correction de production dans les développements en cours ?**
Il faut répércuter la correction sur les branches de développement car le bug critique s'y trouve toujours et lors d'une prochaine livraison le bug pourrait revenir.

**6. Quel est le rôle d'une branche de release ?**
La branche release permet de préparer la mise en production et de faire tester le produit fini aux clients pour qu'il puisse tester et que les derniers ajustement soit fait avant la mise en production.
