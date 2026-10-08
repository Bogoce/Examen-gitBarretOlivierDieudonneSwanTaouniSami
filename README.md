# Asso'Events — Site de l'association étudiante

Évaluation Git & GitHub — travail collaboratif en Git Flow.

## Équipe

| Pseudonyme GitHub | Nom | Prénom | Rôle |
|---|---|---|---|
| @taounisami-netizen | TAOUNI | Sami | Étudiant 1 |
| @Bogoce | BARRET | Olivier | Étudiant 2 |
| @5wVn | DIEUDONNE | Swan | Étudiant 3 |

## Présentation du projet

Site vitrine en HTML/CSS pour une association étudiante qui organise des événements : présentation de l'association, catalogue des événements à venir et formulaire d'inscription. Trois pages reliées par une barre de navigation commune, adaptées au mobile.

## Fonctionnalités et responsabilités

| Fonctionnalité | Responsable | Issue |
|---|---|---|
| Mise en place du dépôt, Git Flow, protections, Project | Sami (Étudiant 1) | |
| Squelette du site | Sami (Étudiant 1) | #10 |
| Feature A — Présentation et navigation | Sami (Étudiant 1) | #12 |
| Feature B — Catalogue d'événements | Olivier (Étudiant 2) | |
| Feature C — Inscription | Swan (Étudiant 3) | #6 |
| Amélioration A — Identité visuelle | Sami (Étudiant 1) | #13 |
| Amélioration B — Adaptation mobile | Olivier (Étudiant 2) | #15 |
| Coordination et résolution du conflit | Swan (Étudiant 3) | #7 |
| Bugfix — cartes qui débordent sur mobile | Swan (Étudiant 3) | #8 |
| Release v1.0 | Swan (Étudiant 3) | #9 |
| Hotfix v1.0.1 — lien de navigation | Olivier (Étudiant 2) | |
| README et questions de synthèse | Sami (Étudiant 1) | #14 |

## Workflow Git Flow

| Branche | Rôle |
|---|---|
| `main` | Versions stables publiées, identifiées par des tags |
| `develop` | Intégration des développements en cours |
| `feature/*` | Nouvelle fonctionnalité, créée depuis `develop` |
| `bugfix/*` | Correction d'une anomalie dans `develop` |
| `release/*` | Préparation d'une version, de `develop` vers `main` |
| `hotfix/*` | Correction urgente de la production, depuis `main` |

- `main` et `develop` sont protégées par un ruleset : Pull Request obligatoire, 2 approbations, pas de force push ni de suppression.
- Toute intégration passe par une Pull Request relue par les deux autres membres.
- Chaque commit et chaque Pull Request référencent leur Issue.
- Fusion en merge commit pour garder l'historique Git Flow visible.

## Étapes du développement

1. Dépôt, `develop`, protections et organisation des Issues dans GitHub Projects.
2. Squelette du site (3 pages et navigation commune).
3. Features A, B et C en parallèle.
4. Identité visuelle et adaptation mobile en parallèle, avec conflit volontaire.
5. Correction du débordement des cartes sur mobile dans `develop`.
6. Release v1.0.
7. Hotfix v1.0.1 après l'incident de production.

## Conflit et résolution

`feature/identite-visuelle` (Sami) et `feature/adaptation-mobile` (Olivier) sont parties du même `develop` et modifiaient toutes les deux les mêmes lignes du bloc `nav` de `style.css` : couleurs et typographie d'un côté, mise en page flex mobile de l'autre. La PR identité visuelle (#17) a été fusionnée en premier, la PR mobile est alors entrée en conflit sur `style.css`.

Résolution coordonnée par Swan : À COMPLÉTER PAR SWAN.

## Versions publiées

| Version | Description |
|---|---|
| v1.0 | À COMPLÉTER |
| v1.0.1 | À COMPLÉTER |

## Difficultés rencontrées

- Les PR #1 (pseudos du README, modifiés via l'interface web) et #2 (squelette) ont été fusionnées dans `main` au lieu de `develop`, car la branche par défaut était `main`. Correction : PR de synchronisation `main` vers `develop`, puis branche par défaut passée sur `develop`.
- La PR #4 (synchronisation directe `main` vers `develop`) ne pouvait pas être résolue car les deux branches sont protégées. Elle a été remplacée par une branche intermédiaire `chore/sync-main-develop`.
- Un résidu de marqueur de conflit (`HEAD`) est resté dans `style.css` après la synchronisation. Il a été repéré en revue de code.
- Des commits ont été faits par erreur sur `develop` en local au lieu de la branche de feature. Ils ont été déplacés sur `feature/adaptation-mobile` avant le push.

## Questions de synthèse

**1. Quel est l'intérêt de séparer développements en cours et versions stables ?**
*Réponse de Sami TAOUNI (@taounisami-netizen), Étudiant 1*
Comme ça, `main` reste toujours propre et utilisable. On bosse sur `develop` sans risquer de casser la version en prod si un truc n'est pas fini ou bugué.

**2. Pourquoi imposer une revue de code avant intégration ?**
*Réponse de Sami TAOUNI (@taounisami-netizen), Étudiant 1*
Un deuxième regard repère des erreurs qu'on ne voit pas soi-même, et tout le monde sait ce qui a changé dans le code. Ici, c'est en revue qu'on a vu un reste de conflit (`HEAD`) oublié dans `style.css`.

**3. Quelles situations provoquent un conflit Git et pourquoi sa résolution n'est-elle pas toujours automatique ?**
*Réponse de Sami TAOUNI (@taounisami-netizen), Étudiant 1*
Quand deux branches modifient les mêmes lignes d'un fichier, ou qu'une branche modifie un fichier que l'autre a supprimé. Git ne peut pas deviner quelle version est la bonne, donc c'est à nous de choisir quoi garder.

**4. Quelle différence entre correction classique et correction urgente de production ?**
*Réponse d'Olivier BARRET (@Bogoce), Étudiant 2*
À COMPLÉTER

**5. Pourquoi répercuter une correction de production dans les développements en cours ?**
*Réponse d'Olivier BARRET (@Bogoce), Étudiant 2*
À COMPLÉTER

**6. Quel est le rôle d'une branche de release ?**
*Réponse d'Olivier BARRET (@Bogoce), Étudiant 2*
À COMPLÉTER

**7. Comment GitHub Projects et les Issues facilitent-ils organisation et traçabilité ?**
*Réponse de Swan DIEUDONNE (@5wVn), Étudiant 3*
À COMPLÉTER

**8. Comment retrouver l'origine d'une modification dans l'historique GitHub ?**
*Réponse de Swan DIEUDONNE (@5wVn), Étudiant 3*
À COMPLÉTER