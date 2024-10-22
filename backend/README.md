
# README - Projet Django avec Celery, Redis, PostgreSQL, Prometheus et Grafana

## Introduction
Ce projet est un projet Django optimisé, utilisant PostgreSQL pour la base de données, Redis pour la gestion du cache et des tâches asynchrones, Celery pour les tâches en arrière-plan, ainsi que Prometheus et Grafana pour le monitoring et la supervision des performances.

## Prérequis
- Python 3.9+
- Poetry (pour la gestion des dépendances)
- Docker et Docker Compose (pour l'exécution de PostgreSQL, Redis, Prometheus, et Grafana)
- Redis (comme broker pour Celery)
- PostgreSQL (comme base de données principale)

## Installation

1. Clonez le dépôt :
```bash
git clone https://github.com/votre_projet.git
cd votre_projet
```

2. Installez les dépendances via Poetry :
```bash
poetry install
```

3. Créez un fichier `.env` pour les variables d'environnement (en utilisant django-environ) :
```bash
cp .env.example .env
```

4. Lancez Docker Compose pour démarrer PostgreSQL, Redis, Prometheus, et Grafana :
```bash
docker-compose up
```

5. Appliquez les migrations de base de données :
```bash
poetry run python manage.py migrate
```

6. Démarrez le serveur Django :
```bash
poetry run python manage.py runserver
```

7. Démarrez le worker Celery :
```bash
celery -A config worker --loglevel=info
```

## Utilisation de Celery

Celery est utilisé pour gérer les tâches asynchrones dans le projet. Vous pouvez ajouter de nouvelles tâches dans le fichier `tasks.py` des apps Django.

Exemple pour appeler une tâche asynchrone :
```python
from myapp.tasks import add
add.delay(10, 20)
```

Cela exécutera la tâche en arrière-plan.

## Monitoring avec Prometheus et Grafana

Prometheus est configuré pour surveiller l'application, et Grafana est utilisé pour visualiser les métriques en temps réel.

1. Accédez à Prometheus via `http://localhost:9090`.
2. Accédez à Grafana via `http://localhost:3000` (utilisateur : `admin`, mot de passe : `admin`).

## Tests

Pour exécuter les tests unitaires, utilisez la commande suivante :
```bash
poetry run pytest
```

## Linting et Formatage

Le code est formaté avec **black** et vérifié avec **flake8**. Exécutez les commandes suivantes pour vérifier la qualité du code :
```bash
poetry run black .
poetry run flake8 .
```

## Déploiement

L'intégration continue (CI) est configurée avec GitHub Actions pour exécuter des tests automatiques, le linting et le formatage à chaque push sur la branche `main`.
