# Changelog

Historique des versions et changements de ShadowBot Touch.

## [Non publié]

### En cours de développement
- Analyse complète des protocoles réseau Dofus Touch
- Implémentation de la connexion réelle aux serveurs
- Système de gestion multi-bots

## [0.3.0] - Phase actuelle

### Ajouté
- Documentation GitBook complète
- Captures mitmproxy pour analyse de protocoles
- Identification des serveurs cibles (login + game)

### En cours
- Implémentation connexion serveur via Primus
- Analyse des messages WebSocket
- Système d'authentification Ankama

## [0.2.0] - Infrastructure

### Ajouté
- Interface web React avec dashboard
- Système de gestion des comptes (CRUD)
- Gestion des proxies avec tests de connexion
- Base de données SQLite via sql.js
- Authentification par clé API
- Sidebar navigation
- Affichage des bots connectés (simulé)

### Modifié
- Migration de better-sqlite3 vers sql.js (résolution problèmes Windows)
- Optimisation de la structure de données

### Corrigé
- Problèmes de compilation native sur Windows
- Persistance des données (excepté états de connexion)

## [0.1.0] - Prototype initial

### Ajouté
- Architecture de base (Express + React)
- Système d'authentification simple
- Interface utilisateur basique
- Premiers tests de concepts

### Notes
- Proof of concept fonctionnel
- Pas de connexion réelle au serveur

---

## Versions futures planifiées

### [0.4.0] - Connexion serveur
- Connexion authentification Ankama
- Connexion serveur de jeu via Primus
- Sélection de personnage
- Heartbeat et maintien de connexion

### [0.5.0] - Actions de base
- Déplacement sur la carte
- Récolte de ressources
- Combat basique
- Gestion inventaire

### [0.6.0] - Automatisation
- Mode farm automatique
- Chemins prédéfinis
- Évitement de combats
- Retour banque automatique

### [1.0.0] - Release stable
- Tous les modes fonctionnels
- Tests complets
- Documentation finalisée
- Optimisations performances
- Support production

---

## Convention de versioning

ShadowBot Touch suit le [Semantic Versioning](https://semver.org/):

- **MAJOR** : Changements incompatibles
- **MINOR** : Nouvelles fonctionnalités compatibles
- **PATCH** : Corrections de bugs

Format: `MAJOR.MINOR.PATCH`

Exemple: `1.2.3`
- 1 = Version majeure
- 2 = Fonctionnalités ajoutées
- 3 = Corrections de bugs

---

[Retour au sommaire](../SUMMARY.md)
