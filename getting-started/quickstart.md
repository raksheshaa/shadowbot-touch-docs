# Première utilisation

Ce guide vous accompagne dans vos premiers pas avec ShadowBot Touch.

## Vue d'ensemble rapide

En 5 minutes, vous serez capable de :
1. ✅ Vous connecter à l'interface
2. ✅ Ajouter un compte Dofus Touch
3. ✅ Configurer un proxy (optionnel)
4. ✅ Lancer votre premier bot

## Étape 1 : Connexion à l'interface

### Accéder à l'application

1. Assurez-vous que l'application est démarrée :
   ```bash
   npm start
   ```

2. Ouvrez votre navigateur à l'adresse :
   ```
   http://localhost:3000
   ```

3. Vous voyez la page de connexion

### S'authentifier

<div class="img-container">
  <img src="../assets/login-screen.png" alt="Écran de connexion" />
</div>

1. Entrez votre **clé API** (définie dans `config.json`)
2. Cliquez sur **Se connecter**
3. Vous êtes redirigé vers le dashboard

> 💡 **Astuce** : La session reste active pendant 1 heure (configurable)

## Étape 2 : Découvrir le dashboard

<div class="img-container">
  <img src="../assets/dashboard.png" alt="Dashboard principal" />
</div>

Le dashboard se compose de :

- **Barre latérale gauche** - Navigation principale
  - 🏠 Accueil
  - 👤 Comptes
  - 🌐 Proxies
  - 🤖 Bots
  - ⚙️ Paramètres

- **Zone principale** - Contenu dynamique
  - Statistiques en temps réel
  - Liste des bots connectés
  - Graphiques d'activité

- **Barre supérieure** - Informations de session
  - Nombre de bots actifs
  - Statut de connexion
  - Bouton de déconnexion

## Étape 3 : Ajouter votre premier compte

### Navigation

1. Cliquez sur **Comptes** dans la barre latérale
2. Cliquez sur le bouton **+ Ajouter un compte**

### Formulaire de compte

<div class="img-container">
  <img src="../assets/add-account.png" alt="Ajouter un compte" />
</div>

Remplissez les informations :

```
Nom d'utilisateur : votre_login_ankama
Mot de passe : ••••••••••••
Serveur : Hélios (exemple)
Proxy : [Optionnel] Sélectionnez un proxy
Notes : [Optionnel] Description du compte
```

**Champs obligatoires** :
- ✅ Nom d'utilisateur
- ✅ Mot de passe
- ✅ Serveur

**Champs optionnels** :
- Proxy (recommandé pour multi-comptes)
- Notes personnelles

### Validation

1. Cliquez sur **Enregistrer**
2. Le compte apparaît dans la liste
3. Un message de confirmation s'affiche ✅

> ⚠️ **Sécurité** : Les mots de passe sont chiffrés dans la base de données

## Étape 4 : Configurer un proxy (optionnel mais recommandé)

Si vous prévoyez d'utiliser plusieurs comptes, configurez des proxies pour respecter la limite de 4 comptes par IP.

### Ajouter un proxy

1. Cliquez sur **Proxies** dans la barre latérale
2. Cliquez sur **+ Ajouter un proxy**

### Formulaire de proxy

```
Type : HTTP / SOCKS5
Hôte : 192.168.1.100
Port : 8080
Nom d'utilisateur : [Optionnel]
Mot de passe : [Optionnel]
Description : Mon proxy principal
```

**Formats supportés** :
- HTTP/HTTPS
- SOCKS4/SOCKS5

### Tester le proxy

Avant de sauvegarder, cliquez sur **Tester la connexion** pour vérifier que le proxy fonctionne.

```
✅ Connexion réussie
Latence : 45ms
IP sortante : 185.123.45.67
```

## Étape 5 : Lancer votre premier bot

### Sélectionner un compte

1. Allez dans **Bots** dans la barre latérale
2. Cliquez sur **+ Nouveau bot**
3. Sélectionnez le compte à connecter

### Configuration du bot

<div class="img-container">
  <img src="../assets/bot-config.png" alt="Configuration du bot" />
</div>

```
Compte : Choisir dans la liste
Personnage : [Auto-détecté après connexion]
Mode : Farm / PvP / Commerce
Statut : En attente
```

### Démarrer le bot

1. Cliquez sur **Démarrer**
2. Le bot lance la connexion au serveur
3. États possibles :
   - 🔵 **Connexion en cours...**
   - 🟢 **Connecté** - Le bot est opérationnel
   - 🔴 **Déconnecté** - Erreur de connexion
   - 🟡 **En pause** - Bot mis en pause

### Surveillance en temps réel

Une fois connecté, vous voyez :

```
┌─────────────────────────────────┐
│ 🟢 MonCompte - Niveau 50        │
│ Serveur : Hélios                │
│ Position : [0,0] Incarnam       │
│ Temps de connexion : 00:15:32   │
│ Actions effectuées : 42         │
└─────────────────────────────────┘
```

**Informations affichées** :
- Statut de connexion
- Niveau du personnage
- Position actuelle
- Statistiques d'activité
- Logs en temps réel

## Étape 6 : Arrêter le bot

Pour arrêter proprement un bot :

1. Cliquez sur le bot dans la liste
2. Cliquez sur **Arrêter**
3. Le bot se déconnecte proprement
4. Les données sont sauvegardées

> 💡 **Bonne pratique** : Toujours arrêter les bots avant de fermer l'application

## Raccourcis clavier

| Raccourci | Action |
|-----------|--------|
| `Alt + H` | Retour au tableau de bord |
| `Alt + C` | Gérer les comptes |
| `Alt + B` | Gérer les bots |
| `Alt + P` | Gérer les proxies |
| `Ctrl + S` | Sauvegarder (formulaires) |
| `Échap` | Fermer les modales |

## Checklist du débutant

Avant de commencer sérieusement, assurez-vous d'avoir :

- [x] Changé la clé API par défaut
- [x] Ajouté au moins un compte
- [x] Configuré un proxy (pour multi-comptes)
- [x] Testé la connexion d'un bot
- [x] Vérifié les logs pour détecter les erreurs
- [x] Sauvegardé votre configuration

## Conseils pour bien démarrer

### 🎯 Commencez petit
- Démarrez avec 1-2 bots maximum
- Observez leur comportement
- Augmentez progressivement

### 📊 Surveillez les performances
- Vérifiez l'utilisation CPU/RAM
- Consultez régulièrement les logs
- Identifiez les problèmes tôt

### 🔒 Respectez les limites
- **Maximum 4 comptes par IP**
- Utilisez des proxies pour plus de comptes
- Ne surchargez pas votre machine

### 💾 Sauvegardez régulièrement
- La base de données contient tous vos comptes
- Activez les sauvegardes automatiques
- Conservez une copie externe

## Problèmes fréquents (débutants)

### Le bot ne se connecte pas

**Causes possibles** :
- ❌ Identifiants incorrects
- ❌ Serveur indisponible
- ❌ Proxy non fonctionnel
- ❌ Pare-feu bloquant

**Solution** : Vérifiez les logs détaillés dans la section Bots

### Erreur "Trop de comptes connectés"

**Cause** : Plus de 4 comptes sur la même IP

**Solution** : Ajoutez un proxy ou attendez qu'un compte se déconnecte

### L'interface ne charge pas

**Causes possibles** :
- ❌ Port déjà utilisé
- ❌ Problème de navigation

**Solution** : Vérifiez que l'application est démarrée et accessible

## Aller plus loin

Maintenant que vous maîtrisez les bases, explorez :

- [Gestion avancée des comptes](../guide/accounts.md) - Organisation et stratégies
- [Monitoring](../guide/monitoring.md) - Surveillance approfondie
- [Configuration avancée](../reference/configuration.md) - Personnalisation poussée

---

**Félicitations ! 🎉** Vous maîtrisez maintenant les bases de ShadowBot Touch. Consultez le [Guide d'utilisation](../guide/interface.md) pour découvrir toutes les fonctionnalités.
