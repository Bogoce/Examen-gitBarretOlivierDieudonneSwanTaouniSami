# Asso'Events — Site de l'association étudiante
 
Évaluation Git & GitHub — travail collaboratif en Git Flow.
 
## Équipe
 
| Pseudonyme GitHub | Nom | Prénom | Rôle |
|---|---|---|---|
| @taounisami-netizen | TAOUNI | Sami | Étudiant 1 |
| @Bogoce | BARRET | Olivier | Étudiant 2 |
| @5wVn | DIEUDONNE | Swan | Étudiant 3 |
 
## Présentation du projet
 
Site vitrine en HTML/CSS pour une association étudiante organisatrice d'événements : présentation de l'association, catalogue des événements à venir et formulaire d'inscription. Le site est composé de trois pages reliées par une barre de navigation commune et adapté aux écrans mobiles.
 
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
| `feature/*` | Développement d'une fonctionnalité, créée depuis `develop` |
| `bugfix/*` | Correction d'une anomalie dans `develop` |
| `release/*` | Préparation d'une version stable, depuis `develop` vers `main` |
| `hotfix/*` | Correction urgente de la production, depuis `main` |
 
Règles appliquées :

- `main` et `develop` sont protégées par un ruleset GitHub : Pull Request obligatoire, 2 approbations, force push et suppression interdits.

- Toute intégration passe par une Pull Request relue par les deux autres membres.

- Chaque commit et chaque Pull Request référencent l'Issue correspondante.

- Les Pull Requests sont fusionnées avec un merge commit pour conserver l'historique Git Flow.
 
## Étapes du développement
 
1. Création du dépôt, de `develop` et des protections, puis organisation des Issues dans GitHub Projects.

2. Squelette du site (3 pages et navigation commune).

3. Développement en parallèle des Features A, B et C.

4. Améliorations parallèles identité visuelle et adaptation mobile, avec conflit volontaire.

5. Correction du débordement des cartes sur mobile dans `develop`.

6. Release v1.0.

7. Hotfix v1.0.1 après l'incident de production.
 
## Conflit et résolution
 
Les branches `feature/identite-visuelle` (Sami) et `feature/adaptation-mobile` (Olivier) ont été créées depuis le même état de `develop`. Toutes les deux modifiaient les mêmes lignes du bloc `nav` dans `style.css` : la première pour les couleurs, la bordure et la typographie, la seconde pour la mise en page flex adaptée au mobile.
 
La PR identité visuelle (#17) a été fusionnée en premier. La PR adaptation mobile est alors entrée en conflit sur `style.css`, car Git ne pouvait pas choisir entre deux valeurs différentes pour les mêmes propriétés.
 
Résolution coordonnée par Swan : le conflit est arrivé sur la PR #18 (adaptation mobile), dans `style.css`. Olivier avait ajouté sa media query mobile à la fin du fichier, mais Sami avait mis ses styles de présentation (`.slogan`, `.presentation`) exactement au même endroit sur `develop`. Comme on avait besoin des deux, on a choisi « Accept both changes » dans l'éditeur de GitHub, donc on a gardé les deux blocs. On a vérifié qu'il ne restait plus de `<<<<<<<`, `=======` ou `>>>>>>>`. On a fait ça directement dans la branche de la feature, pas dans `develop`, et on l'a expliqué dans un commentaire sur la PR avant de la fusionner.
 
## Versions publiées
 
| Version | Description |
|---|---|
| v1.0 | À COMPLÉTER |
| v1.0.1 | À COMPLÉTER |
 
## Difficultés rencontrées
 
- Les PR #1 (pseudos du README, modifiés via l'interface web de GitHub) et #2 (squelette) ont été fusionnées dans `main` au lieu de `develop`, car la branche par défaut du dépôt était `main`. Correction : PR de synchronisation `main` vers `develop` avec résolution d'un conflit sur `style.css`, puis passage de la branche par défaut sur `develop`.

- La PR #4 (synchronisation directe `main` vers `develop`) ne pouvait pas être résolue, les deux branches étant protégées. Elle a été fermée et remplacée par une branche intermédiaire `chore/sync-main-develop`.

- Un résidu de marqueur de conflit (`HEAD`) est resté dans `style.css` après la synchronisation. Il a été signalé en revue de code et corrigé ensuite.

- Des commits ont été réalisés par erreur sur `develop` en local au lieu de la branche de feature. Ils ont été déplacés sur `feature/adaptation-mobile` avant le push.
 
## Questions de synthèse
 
**1. Quel est l'intérêt de séparer développements en cours et versions stables ?**

*Réponse de Sami TAOUNI (@taounisami-netizen), Étudiant 1*

Séparer `develop` et `main` permet de toujours disposer d'une version stable et livrable sur `main`, pendant que les nouvelles fonctionnalités sont intégrées et testées sur `develop`. Un développement inachevé ou bogué ne peut ainsi pas casser la version utilisée en production.
 
**2. Pourquoi imposer une revue de code avant intégration ?**

*Réponse de Sami TAOUNI (@taounisami-netizen), Étudiant 1*

La revue permet de repérer les erreurs avant qu'elles n'atteignent les branches principales, de vérifier que le code respecte les conventions de l'équipe et de partager la connaissance du code entre les membres. Dans ce projet, elle a par exemple permis de détecter un résidu de marqueur de conflit dans `style.css`.
 
**3. Quelles situations provoquent un conflit Git et pourquoi sa résolution n'est-elle pas toujours automatique ?**

*Réponse de Sami TAOUNI (@taounisami-netizen), Étudiant 1*

Un conflit survient lorsque deux branches modifient les mêmes lignes d'un même fichier, ou lorsqu'une branche modifie un fichier que l'autre supprime. Git sait fusionner des modifications sur des zones différentes, mais quand les mêmes lignes changent de deux façons différentes, il ne peut pas deviner l'intention des développeurs : seul un humain peut décider de la version à garder ou de la manière de combiner les deux.
 
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

Les Issues, ça sert à écrire ce qu'il y a à faire pour chaque tâche, avec des cases à cocher et la personne responsable. Dans GitHub Projects, on les met dans un tableau (À faire, En cours, En relecture, Terminé), donc on voit tout de suite qui fait quoi et où on en est. Et comme on écrit le numéro de l'Issue dans chaque commit et chaque PR (par exemple `Closes #8`), tout est relié : on sait pourquoi on a fait un changement, et l'Issue se ferme toute seule quand la PR est fusionnée.
 
**8. Comment retrouver l'origine d'une modification dans l'historique GitHub ?**

*Réponse de Swan DIEUDONNE (@5wVn), Étudiant 3*

Sur GitHub, on ouvre le fichier et on clique sur « Blame » : pour chaque ligne, on voit le dernier commit qui l'a modifiée et qui l'a fait. Avec « History », on voit tous les commits du fichier. Ensuite, à partir du commit, on retrouve la Pull Request, et dedans l'Issue (`Closes #8`) qui explique pourquoi on a changé ça. Par exemple, pour le `HEAD` qui traînait dans `style.css`, on a pu retrouver que ça venait de la synchro entre `main` et `develop`.
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
