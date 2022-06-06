## Résumés

Site web d'Orange County Lettings

## Développement local

### Prérequis

- Compte GitHub avec accès en lecture à ce repository
- Git CLI
- SQLite3 CLI
- Interpréteur Python, version 3.6 ou supérieure

Dans le reste de la documentation sur le développement local, il est supposé que la commande `python` de votre OS shell exécute l'interpréteur Python ci-dessus (à moins qu'un environnement virtuel ne soit activé).

### macOS / Linux

#### Cloner le repository

- `cd /path/to/put/project/in`
- `git clone https://github.com/OpenClassrooms-Student-Center/Python-OC-Lettings-FR.git`

#### Créer l'environnement virtuel

- `cd /path/to/Python-OC-Lettings-FR`
- `python -m venv venv`
- `apt-get install python3-venv` (Si l'étape précédente comporte des erreurs avec un paquet non trouvé sur Ubuntu)
- Activer l'environnement `source venv/bin/activate`
- Confirmer que la commande `python` exécute l'interpréteur Python dans l'environnement virtuel
`which python`
- Confirmer que la version de l'interpréteur Python est la version 3.6 ou supérieure `python --version`
- Confirmer que la commande `pip` exécute l'exécutable pip dans l'environnement virtuel, `which pip`
- Pour désactiver l'environnement, `deactivate`

#### Exécuter le site

- `cd /path/to/Python-OC-Lettings-FR`
- `source venv/bin/activate`
- `pip install --requirement requirements.txt`
- `python manage.py runserver`
- Aller sur `http://localhost:8000` dans un navigateur.
- Confirmer que le site fonctionne et qu'il est possible de naviguer (vous devriez voir plusieurs profils et locations).

#### Linting

- `cd /path/to/Python-OC-Lettings-FR`
- `source venv/bin/activate`
- `flake8`

#### Tests unitaires

- `cd /path/to/Python-OC-Lettings-FR`
- `source venv/bin/activate`
- `pytest`

#### Base de données

- `cd /path/to/Python-OC-Lettings-FR`
- Ouvrir une session shell `sqlite3`
- Se connecter à la base de données `.open oc-lettings-site.sqlite3`
- Afficher les tables dans la base de données `.tables`
- Afficher les colonnes dans le tableau des profils, `pragma table_info(Python-OC-Lettings-FR_profile);`
- Lancer une requête sur la table des profils, `select user_id, favorite_city from
  Python-OC-Lettings-FR_profile where favorite_city like 'B%';`
- `.quit` pour quitter

#### Panel d'administration

- Aller sur `http://localhost:8000/admin`
- Connectez-vous avec l'utilisateur `admin`, mot de passe `Abc1234!`

### Windows

Utilisation de PowerShell, comme ci-dessus sauf :

- Pour activer l'environnement virtuel, `.\venv\Scripts\Activate.ps1` 
- Remplacer `which <my-command>` par `(Get-Command <my-command>).Path`

## Intégration et déploiement (Pipeline CI/CD) :

  ### Docker : 
  - Aller sur le site de docker ou installer l'application hub desktop
  - Connectez-vous à votre compte docker et faire la laison avec l'application docker desktop 
  - Créer le fichier .dockerignore
  
  ### Sentry : 
  - Aller sur le site sentry ouvrer un compte et créer un projet Django
  - Sentry génére un code (SDK) en python à intégrer dans le fichier settings du projet
  
  ### Heroku
  - Aller sur le site de Heroku et créer un nouveau compte
  - Créer une apllication
  - ouvrer l'onglet setting et faire la laison avec github
  - Dans l'onglet deploy cochez la case Wait for CI to pass before deploy et sélectionnez la branche à deployer


  ### CircleCi :
  - Aller sur le site de CirecleCi et ouvrer un nouveau compte
  - Lier le compte github à votre compte Cercleci
  - Dans l'espace projects, sélectionnez le repository de notre projet en cliquant sur Set up project
  - Sélectionnez le project dans le dashboard CircleCi puis cliquez sur Project settings > Environnement variables
  - Enregistrez les variables environnements nécessaires lors de l'éxécution du pipeline CI/CD : DEBUG, DOCKERHUB_PASS, DOCKERHUB_USER, HEROKU_API_KEY, HEROKU_APP_NAME, SECRET_KEY, dsn,
  
  
  ## Exécution de l'intégration et déploiement 
  
  ### Les étapes du Pipeline CI/CD : 
  
  1) unittest-and-linter
  2) build-and-push-docker-image
  3) deploy-on-heroku.

  
  

