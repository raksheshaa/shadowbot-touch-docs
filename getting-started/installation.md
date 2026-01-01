---
description: >-
  Ce guide vous accompagne dans l'installation de ShadowBot Touch sur votre
  système.
---

# Installation

## Prérequis système

### Configuration minimale

* **OS** : Windows 10+, macOS 10.15+, ou Linux (Ubuntu 20.04+)
* **Node.js** : Version 16.x ou supérieure
* **RAM** : 4 Go minimum (8 Go recommandé)
* **Espace disque** : 500 Mo pour l'application + espace pour les logs

### Logiciels requis

1.  **Node.js et npm**

    * Téléchargez depuis [nodejs.org](https://nodejs.org/)
    * Vérifiez l'installation :

    ```bash
    node --version  # Devrait afficher v16.x.x ou supérieur
    npm --version   # Devrait afficher 8.x.x ou supérieur
    ```
2. **Git** (optionnel, mais recommandé)
   * Téléchargez depuis [git-scm.com](https://git-scm.com/)

## Méthode 1 : Installation depuis les sources

### Étape 1 : Cloner le repository

```bash
git clone https://github.com/votre-repo/shadowbot-touch.git
cd shadowbot-touch
```

Ou téléchargez l'archive ZIP depuis GitHub et extrayez-la.

### Étape 2 : Installer les dépendances

```bash
npm install
```

Cette commande installera toutes les dépendances nécessaires, notamment :

* Express pour le serveur web
* sql.js pour la base de données
* Primus/WebSocket pour la communication
* Et d'autres modules auxiliaires

### Étape 3 : Configuration initiale

Copiez le fichier de configuration exemple :

```bash
cp config.example.json config.json
```

Éditez `config.json` pour personnaliser :

* Port du serveur (par défaut : 3000)
* Clé API initiale
* Paramètres de base de données

### Étape 4 : Lancer l'application

```bash
npm start
```

L'application devrait démarrer et afficher :

```
🚀 ShadowBot Touch démarré sur http://localhost:3000
🔒 Authentification activée - Utilisez votre clé API
```

## Méthode 2 : Installation avec Docker

### Prérequis

* Docker Desktop installé ([docker.com](https://www.docker.com/))

### Étapes

```bash
# Construire l'image
docker build -t shadowbot-touch .

# Lancer le conteneur
docker run -d \
  -p 3000:3000 \
  -v $(pwd)/data:/app/data \
  --name shadowbot \
  shadowbot-touch
```

Accédez à `http://localhost:3000`

## Vérification de l'installation

1. Ouvrez votre navigateur à l'adresse `http://localhost:3000`
2. Vous devriez voir la page de connexion
3. Entrez votre clé API (définie dans `config.json`)
4. Si vous accédez au dashboard, l'installation est réussie ! ✅

## Configuration des proxies (optionnel)

Si vous prévoyez d'utiliser plusieurs comptes, configurez vos proxies dès maintenant. Voir [Gestion des proxies](../guide/proxies.md).

## Problèmes courants

### Erreur de port déjà utilisé

```
Error: listen EADDRINUSE: address already in use :::3000
```

**Solution** : Changez le port dans `config.json` ou arrêtez l'application utilisant le port 3000.

### Erreur d'installation npm

```
npm ERR! code EACCES
```

**Solution** : Exécutez la commande avec les droits administrateur ou utilisez nvm pour gérer Node.js.

### Base de données corrompue

**Solution** : Supprimez le fichier `data/shadowbot.db` et relancez l'application (attention : perte de données).

## Mise à jour

Pour mettre à jour vers la dernière version :

```bash
git pull origin main
npm install
npm start
```

## Désinstallation

Pour désinstaller complètement ShadowBot Touch :

```bash
# Arrêter l'application
# Supprimer le dossier
cd ..
rm -rf shadowbot-touch
```

***

**Prochaine étape** : [Configuration initiale](configuration.md) pour personnaliser votre installation.
