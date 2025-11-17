# Guidelines pour le projet BitGuard

## Git

### Stratégies de branches

On travaille avec des branches dédiées.
Ne jamais pousser directement sur la branch `main`.

#### Branches principales

- `main` -> code stable, branche déployée en production

#### Branches de travail

Une fonctionnalité = une branche = une PR.

- `feature/<nom-de-branche>` -> nouvelle fonctionnalité ou refonte importante
- `fix/<nom-de-branche>` -> correction de bug
- `hotfix/<nom-de-branche>` -> correctif urgent en production
- `chore/<nom>` -> maintenance, configuration, dépendances

### Règles de commits

Des commits clairs, courts et précis.

#### Format

`<type>(<scope>): <courte description>`

#### Exemples

`feat(auth): ajout du login avec JWT`
`fix(ui): corrige l'alignement du bouton sur mobile`
`chore(ci): met à jour la version Node de GitHub Actions`
`refactor(api): déplace la validation dans un middleware`
`docs(readme): ajoute les instructions d'installation`

#### Types courants

- `feat` -> nouvelle fonctionnalité
- `fix` -> correction de bug
- `chore` -> maintenance (dépendances, outils, config)
- `docs` -> documentation
- `style` -> modifiactions de style/formatage
- `refactor` -> amélioration du code sans changement de comportement
- `test` -> ajout/modification de tests

### Pull Requests (PR)

- toujours créer une PR avant de merge sur `main`
- titre clair: `feat: ajout du formulaire d'inscription`
- description rapide de ce que fait la PR
- vérification par un pair avant de merge

### Avant de pousser

- lancer les tests et le lint
- faire un `git pull pour être à jour`
- résoudre les conflits éventuels avant d'ouvrir la PR

### Exemple de workflow Git

1. se mettre à jour
  ```
  git checkout main
  git pull origin main
  ```
2. créer une nouvelle branche
  ```
  git checkout -b feature/login-page
  ```
3. travailler sur la fonctionnalité
  ```
  git add --all
  git commit -m "feat(auth): ajout du layout de la page login"
  ```
4. tester avant de pousser
  ```
  npm run lint # ou autres selon le dépôt
  npm run test #
  ```
5. pousser la branche sur le dépôt distant
  ```
  git push origin feature/login-page
  ```
6. créer une PR
  ```
  sur GitHub:
    - ouvrir une PR vers main
    - titre clair: feat(auth): add login page
    - décrire ce que fait la PR + captures d'écrans si besoin
    - demander une review à un membre de l'équipe
  ```
7. review et merge
  ```
  - l'autre membre vérifie le code
  - quand tout est validé, merge
  - suppression de la branche après le merge
  ```
8. remise à jour après merge
  ```
  git checkout main
  git pull origin main
  ```
