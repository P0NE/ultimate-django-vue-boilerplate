
# README - Projet Frontend Vue.js

## Introduction
Ce projet Vue.js est conçu pour être le front-end d'une application web, interagissant avec un back-end Django via une API REST. Il est configuré pour être performant, bien structuré et facile à maintenir.

## Prérequis
- Node.js et npm
- Vue CLI (si vous ne l'avez pas déjà) :
```bash
npm install -g @vue/cli
```

## Installation

1. Clonez le dépôt :
```bash
git clone https://github.com/votre_projet_front.git
cd votre_projet_front
```

2. Installez les dépendances :
```bash
npm install
```

3. Lancez le serveur de développement :
```bash
npm run dev
```

Le serveur de développement sera disponible sur `http://localhost:3000`.

## Configuration

### Proxy API

Si vous interagissez avec un back-end (comme Django), vous pouvez configurer un proxy dans `vue.config.js` :
```javascript
module.exports = {
  devServer: {
    proxy: {
      '/api': {
        target: 'http://localhost:8000',
        changeOrigin: true,
      },
    },
  },
};
```

### Gestion de l'état avec Vuex ou Pinia

Si vous avez besoin de centraliser l'état de votre application, installez Vuex ou Pinia :
```bash
npm install vuex
# ou
npm install pinia
```

### Axios pour les appels API

Pour interagir avec une API REST, installez **Axios** :
```bash
npm install axios
```

Exemple d'utilisation :
```javascript
import axios from 'axios';

const apiClient = axios.create({
  baseURL: 'http://localhost:8000/api',
  headers: {
    Accept: 'application/json',
    'Content-Type': 'application/json',
  },
});

export default {
  getMyModels() {
    return apiClient.get('/mymodels/');
  },
};
```

## Linting et formatage

Ce projet utilise **ESLint** et **Prettier** pour garantir la qualité et la cohérence du code.

- Lancer ESLint :
```bash
npm run lint
```

- Formater le code avec Prettier :
```bash
npm run format
```

## Tests

Pour exécuter les tests unitaires, utilisez **Jest** :
```bash
npm run test:unit
```

Pour les tests end-to-end (E2E), utilisez **Cypress** :
```bash
npm run test:e2e
```

## Déploiement

Avant de déployer, générez une version optimisée pour la production :
```bash
npm run build
```

Cela créera un répertoire `dist` contenant les fichiers minimisés et optimisés pour le déploiement.
