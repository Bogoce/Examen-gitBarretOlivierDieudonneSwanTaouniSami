# Asso'Events — Site de l'association étudiante
 
Évaluation Git & GitHub — travail collaboratif en Git Flow.
 
## Équipe
 
| Pseudonyme GitHub | Nom | Prénom | Rôle |
|---|---|---|---|
| @taounisami-netizen | TAOUNI | Sami | Mise en place du dépôt, squelette, présentation et identité visuelle |
| @Bogoce | BARRET | Olivier | Catalogue d'événements, adaptation mobile et hotfix |
| @5wVn | DIEUDONNE | Swan | Inscription, coordination du conflit, bugfix et release |
 
## Présentation du projet
 
Site vitrine en HTML/CSS pour une association étudiante organisatrice d'événements : présentation de l'association, catalogue des événements à venir et formulaire d'inscription. Le site est composé de trois pages reliées par une barre de navigation commune et adapté aux écrans mobiles.
 
## Fonctionnalités et responsabilités
 
| Fonctionnalité | Responsable | Issue |
|---|---|---|
| Mise en place du dépôt, Git Flow, protections, Project | Sami | |
| Squelette du site | Sami | #10 |
| Feature A — Présentation et navigation | Sami | #12 |
| Feature B — Catalogue d'événements | Olivier | |
| Feature C — Inscription | Swan | #6 |
| Amélioration A — Identité visuelle | Sami | #13 |
| Amélioration B — Adaptation mobile | Olivier | #15 |
| Coordination et résolution du conflit | Swan | #7 |
| Bugfix — cartes qui débordent sur mobile | Swan | #8 |
| Release v1.0 | Swan | #9 |
| Hotfix v1.0.1 — lien de navigation | Olivier | |
| README et questions de synthèse | Sami | #14 |
 
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
 
Les branches `feature/identite-visuelle` (Sami) et `feature/adaptation-mobile` (Olivier) touchaient toutes les deux `style.css`. Les PR de Sami (présentation #16 et identité visuelle #17) ont été fusionnées dans `develop` en premier, avec leurs styles (`.slogan`, `.presentation`, couleurs et typographie).
 
La PR adaptation mobile (#18) est alors entrée en conflit sur `style.css`, car Git ne pouvait pas choisir entre deux contenus ajoutés au même endroit du fichier.
 
Résolution coordonnée par Swan : le conflit est arrivé sur la PR #18 (adaptation mobile), dans `style.css`. Olivier avait ajouté sa media query mobile à la fin du fichier, mais Sami avait mis ses styles de présentation (`.slogan`, `.presentation`) exactement au même endroit sur `develop`. Comme on avait besoin des deux, on a choisi « Accept both changes » dans l'éditeur de GitHub, donc on a gardé les deux blocs. On a vérifié qu'il ne restait plus de `<<<<<<<`, `=======` ou `>>>>>>>`. On a fait ça directement dans la branche de la feature, pas dans `develop`, et on l'a expliqué dans un commentaire sur la PR avant de la fusionner.
 
## Versions publiées
 
| Version | Description |
|---|---|
| v1.0 | Première version stable : accueil, catalogue des événements, inscription, identité visuelle, adaptation mobile et correction des cartes qui débordent. Correction du menu Événements avant la release. |
| v1.0.1 | À COMPLÉTER |
 
## Difficultés rencontrées
 
- Les PR #1 (pseudos du README, modifiés via l'interface web de GitHub) et #2 (squelette) ont été fusionnées dans `main` au lieu de `develop`, car la branche par défaut du dépôt était `main`. Correction : PR de synchronisation `main` vers `develop` avec résolution d'un conflit sur `style.css`, puis passage de la branche par défaut sur `develop`.

- La PR #4 (synchronisation directe `main` vers `develop`) ne pouvait pas être résolue, les deux branches étant protégées. Elle a été fermée et remplacée par une branche intermédiaire `chore/sync-main-develop`.

- Un résidu de marqueur de conflit (`HEAD`) est resté dans `style.css` après la synchronisation. Il a été signalé en revue de code et corrigé ensuite.

- Des commits ont été réalisés par erreur sur `develop` en local au lieu de la branche de feature. Ils ont été déplacés sur `feature/adaptation-mobile` avant le push.
 
## Questions de synthèse
 
**1. Quel est l'intérêt de séparer développements en cours et versions stables ?**

*Réponse de Sami TAOUNI (@taounisami-netizen)*

Séparer `develop` et `main` permet de toujours disposer d'une version stable et livrable sur `main`, pendant que les nouvelles fonctionnalités sont intégrées et testées sur `develop`. Un développement inachevé ou bogué ne peut ainsi pas casser la version utilisée en production.
 
**2. Pourquoi imposer une revue de code avant intégration ?**

*Réponse de Sami TAOUNI (@taounisami-netizen)*

La revue permet de repérer les erreurs avant qu'elles n'atteignent les branches principales, de vérifier que le code respecte les conventions de l'équipe et de partager la connaissance du code entre les membres. Dans ce projet, elle a par exemple permis de détecter un résidu de marqueur de conflit dans `style.css`.
 
**3. Quelles situations provoquent un conflit Git et pourquoi sa résolution n'est-elle pas toujours automatique ?**

*Réponse de Sami TAOUNI (@taounisami-netizen)*

Un conflit survient lorsque deux branches modifient les mêmes lignes d'un même fichier, ou lorsqu'une branche modifie un fichier que l'autre supprime. Git sait fusionner des modifications sur des zones différentes, mais quand les mêmes lignes changent de deux façons différentes, il ne peut pas deviner l'intention des développeurs : seul un humain peut décider de la version à garder ou de la manière de combiner les deux.
 
**4. Quelle différence entre correction classique et correction urgente de production ?**

*Réponse d'Olivier BARRET (@Bogoce)*

Une correction urgente sur la production s'appelle un hotfix : elle se fait dans l'urgence, souvent pour un problème critique, directement depuis `main`. Une correction classique se fait dans `develop` et part avec la prochaine livraison planifiée.
 
**5. Pourquoi répercuter une correction de production dans les développements en cours ?**

*Réponse d'Olivier BARRET (@Bogoce)*

Il faut répercuter la correction dans les branches de développement, car le bug s'y trouve toujours : sinon, il reviendrait à la prochaine livraison.
 
**6. Quel est le rôle d'une branche de release ?**

*Réponse d'Olivier BARRET (@Bogoce)*

La branche de release permet de préparer la mise en production : on teste le produit fini et on fait les derniers ajustements avant la mise en production, sans ajouter de nouvelles fonctionnalités.
 
**7. Comment GitHub Projects et les Issues facilitent-ils organisation et traçabilité ?**

*Réponse de Swan DIEUDONNE (@5wVn)*

Les Issues, ça sert à écrire ce qu'il y a à faire pour chaque tâche, avec des cases à cocher et la personne responsable. Dans GitHub Projects, on les met dans un tableau (À faire, En cours, En relecture, Terminé), donc on voit tout de suite qui fait quoi et où on en est. Et comme on écrit le numéro de l'Issue dans chaque commit et chaque PR (par exemple `Closes #8`), tout est relié : on sait pourquoi on a fait un changement, et l'Issue se ferme toute seule quand la PR est fusionnée.
 
**8. Comment retrouver l'origine d'une modification dans l'historique GitHub ?**

*Réponse de Swan DIEUDONNE (@5wVn)*

Sur GitHub, on ouvre le fichier et on clique sur « Blame » : pour chaque ligne, on voit le dernier commit qui l'a modifiée et qui l'a fait. Avec « History », on voit tous les commits du fichier. Ensuite, à partir du commit, on retrouve la Pull Request, et dedans l'Issue (`Closes #8`) qui explique pourquoi on a changé ça. Par exemple, pour le `HEAD` qui traînait dans `style.css`, on a pu retrouver que ça venait de la synchro entre `main` et `develop`.
