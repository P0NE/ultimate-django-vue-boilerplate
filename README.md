
# Projet Global - Django & Vue.js

## Introduction

Ce projet est une application web complète, utilisant **Django** pour le back-end et **Vue.js** pour le front-end. Il est conçu pour être performant, sécurisé, et facilement maintenable. L'intégration de **Celery** permet la gestion de tâches asynchrones, **Redis** est utilisé pour le cache, et **PostgreSQL** comme base de données principale. Le projet inclut aussi des outils de monitoring avec **Prometheus** et **Grafana**.

## Fonctionnalités

- **Django REST API** : Expose une API RESTful avec **Django REST Framework**.
- **Vue.js Front-end** : Application Vue.js avec **Axios** pour les appels API.
- **Celery** : Gestion des tâches asynchrones (par exemple, envoi d'emails, traitements lourds).
- **Redis** : Utilisé comme broker pour Celery et pour le cache.
- **PostgreSQL** : Base de données relationnelle.
- **Prometheus et Grafana** : Monitoring des performances et alertes.
- **Tests automatiques** : Utilisation de **Jest** pour les tests unitaires du front-end, **Cypress** pour les tests end-to-end, et **pytest** pour le back-end.
- **CI/CD avec GitHub Actions** : Pipeline de tests et déploiement automatique.

## Prérequis

- **Python 3.9+**
- **Node.js 16+**
- **Poetry** (pour la gestion des dépendances back-end)
- **Vue CLI** (pour la gestion du front-end Vue.js)
- **Docker et Docker Compose** (pour la base de données PostgreSQL, Redis, Prometheus, et Grafana)

## Installation

### 1. Back-end (Django)

1. Clonez le dépôt :
   ```bash
   git clone https://github.com/votre-projet.git
   cd votre-projet
   ```

2. Installez les dépendances Python avec Poetry :
   ```bash
   poetry install
   ```

3. Créez un fichier `.env` et configurez vos variables d'environnement (base de données, clé secrète, etc.) :
   ```bash
   cp .env.example .env
   ```

4. Lancez **Docker Compose** pour démarrer PostgreSQL, Redis, Prometheus et Grafana :
   ```bash
   docker-compose up
   ```

5. Appliquez les migrations de la base de données :
   ```bash
   poetry run python manage.py migrate
   ```

6. Démarrez le serveur Django :
   ```bash
   poetry run python manage.py runserver
   ```

### 2. Front-end (Vue.js)

1. Allez dans le répertoire `frontend` :
   ```bash
   cd frontend
   ```

2. Installez les dépendances avec npm :
   ```bash
   npm install
   ```

3. Lancez le serveur de développement Vue.js :
   ```bash
   npm run dev
   ```

Le front-end sera disponible à `http://localhost:3000` et communiquera avec le back-end Django via l'API.

## Tests

### Back-end (Django)

Exécutez les tests unitaires du back-end avec **pytest** :
```bash
poetry run pytest
```

### Front-end (Vue.js)

#### Tests unitaires avec Jest :
```bash
npm run test:unit
```

#### Tests end-to-end avec Cypress :
```bash
npm run test:e2e
```

## Linting et formatage du code

### Back-end (Django)

- **Flake8** : Vérification de la qualité du code Python :
  ```bash
  poetry run flake8
  ```

- **Black** : Formatage du code Python :
  ```bash
  poetry run black --check .
  ```

### Front-end (Vue.js)

- **ESLint** : Linting du code Vue.js :
  ```bash
  npm run lint
  ```

- **Prettier** : Formatage du code JavaScript :
  ```bash
  npm run format
  ```

## Déploiement

Ce projet est configuré pour être déployé automatiquement via **GitHub Actions**. Le pipeline de CI/CD exécute les tests et les vérifications de qualité avant de déployer l'application.

1. **Back-end (Django)** : Configurez le déploiement sur un service comme **Heroku**, **AWS**, ou **DigitalOcean**.
2. **Front-end (Vue.js)** : Déployez sur des services comme **Netlify** ou **Vercel**.

## Monitoring

1. **Prometheus** : Accessible via `http://localhost:9090`.
2. **Grafana** : Accessible via `http://localhost:3000` (nom d'utilisateur : `admin`, mot de passe : `admin`).

## Contribution

Les contributions sont les bienvenues ! Veuillez suivre les bonnes pratiques de développement :
1. Fork le projet.
2. Créez une branche (`git checkout -b feature/amazing-feature`).
3. Committez vos modifications (`git commit -m 'Add some amazing feature'`).
4. Poussez vers la branche (`git push origin feature/amazing-feature`).
5. Ouvrez une Pull Request.

## Licence

Ce projet est sous licence MIT. Consultez le fichier `LICENSE` pour plus d'informations.
