# Configuration initiale

Après l'installation, vous devez configurer ShadowBot Touch pour votre environnement.

## Fichier de configuration

Le fichier `config.json` contient tous les paramètres de l'application.

### Structure du fichier

```json
{
  "server": {
    "port": 3000,
    "host": "localhost"
  },
  "security": {
    "apiKey": "votre-cle-api-securisee",
    "sessionTimeout": 3600
  },
  "database": {
    "path": "./data/shadowbot.db",
    "autoBackup": true,
    "backupInterval": 86400
  },
  "bots": {
    "maxInstances": 50,
    "reconnectDelay": 5000,
    "maxReconnectAttempts": 3
  },
  "proxy": {
    "maxAccountsPerIP": 4,
    "rotationEnabled": true,
    "timeout": 10000
  },
  "logging": {
    "level": "info",
    "path": "./logs",
    "maxSize": "10M",
    "maxFiles": 5
  }
}
```

## Configuration détaillée

### Serveur web

```json
"server": {
  "port": 3000,        // Port d'écoute du serveur
  "host": "localhost"  // Adresse d'écoute (0.0.0.0 pour accès externe)
}
```

**Recommandations** :
- Utilisez `localhost` si vous accédez localement uniquement
- Utilisez `0.0.0.0` pour un accès depuis d'autres machines (attention à la sécurité)
- Changez le port si 3000 est déjà utilisé

### Sécurité

```json
"security": {
  "apiKey": "changez-moi-maintenant",  // Clé pour l'authentification
  "sessionTimeout": 3600                // Durée de session en secondes
}
```

**⚠️ IMPORTANT** : Changez immédiatement la clé API par défaut !

**Générer une clé sécurisée** :

```bash
# Linux/macOS
openssl rand -hex 32

# Windows (PowerShell)
[Convert]::ToBase64String((1..32|%{Get-Random -Max 256}))

# Node.js
node -e "console.log(require('crypto').randomBytes(32).toString('hex'))"
```

### Base de données

```json
"database": {
  "path": "./data/shadowbot.db",  // Chemin du fichier SQLite
  "autoBackup": true,              // Sauvegarde automatique
  "backupInterval": 86400          // Intervalle en secondes (24h par défaut)
}
```

**Notes** :
- Les sauvegardes sont créées dans `./data/backups/`
- Le format est `shadowbot_YYYYMMDD_HHMMSS.db`
- Les anciennes sauvegardes sont conservées 30 jours

### Configuration des bots

```json
"bots": {
  "maxInstances": 50,           // Nombre maximum de bots simultanés
  "reconnectDelay": 5000,       // Délai avant reconnexion (ms)
  "maxReconnectAttempts": 3     // Tentatives max de reconnexion
}
```

**Ajustement de maxInstances** :
- Dépend de votre RAM disponible
- ~100 Mo par bot en moyenne
- Commencez avec 10-20 et augmentez progressivement

### Configuration des proxies

```json
"proxy": {
  "maxAccountsPerIP": 4,     // Maximum de comptes par adresse IP
  "rotationEnabled": true,   // Rotation automatique des proxies
  "timeout": 10000           // Timeout de connexion (ms)
}
```

**⚠️ Limite serveur** : Ne dépassez **JAMAIS** 4 comptes par IP pour éviter un bannissement automatique.

### Journalisation (Logging)

```json
"logging": {
  "level": "info",           // Niveaux : debug, info, warn, error
  "path": "./logs",          // Dossier des logs
  "maxSize": "10M",          // Taille max par fichier
  "maxFiles": 5              // Nombre de fichiers à conserver
}
```

**Niveaux de log** :
- `debug` - Très verbeux, pour le développement
- `info` - Informations normales (recommandé)
- `warn` - Avertissements uniquement
- `error` - Erreurs uniquement

## Configuration avancée

### Variables d'environnement

Vous pouvez surcharger les paramètres via des variables d'environnement :

```bash
# Linux/macOS
export SHADOWBOT_PORT=8080
export SHADOWBOT_API_KEY="ma-cle-securisee"

# Windows (PowerShell)
$env:SHADOWBOT_PORT=8080
$env:SHADOWBOT_API_KEY="ma-cle-securisee"
```

Variables disponibles :
- `SHADOWBOT_PORT` - Port du serveur
- `SHADOWBOT_HOST` - Adresse d'écoute
- `SHADOWBOT_API_KEY` - Clé API
- `SHADOWBOT_DB_PATH` - Chemin de la base de données

### Configuration pour la production

Pour un environnement de production :

```json
{
  "server": {
    "port": 8080,
    "host": "0.0.0.0"
  },
  "security": {
    "apiKey": "UTILISEZ_UNE_CLE_TRES_LONGUE_ET_COMPLEXE",
    "sessionTimeout": 1800
  },
  "logging": {
    "level": "warn",
    "maxSize": "50M",
    "maxFiles": 10
  }
}
```

**Recommandations production** :
- ✅ Clé API forte (64+ caractères)
- ✅ HTTPS avec reverse proxy (nginx/Apache)
- ✅ Firewall configuré
- ✅ Logs rotatifs
- ✅ Sauvegardes automatiques activées

### Configuration réseau

Pour Dofus Touch, l'application se connecte à :

```
Serveur d'authentification : dt-proxy-production-login.ankama.com:443
Serveur de jeu : dt-proxy-production-france.ankama.com:443
Protocole : HTTPS/WSS (WebSocket Secure)
```

**Pare-feu** : Assurez-vous que ces connexions sortantes sont autorisées.

## Première connexion

1. Démarrez l'application : `npm start`
2. Ouvrez `http://localhost:3000`
3. Entrez votre clé API configurée
4. Vous accédez au dashboard ✅

## Vérification de la configuration

Après le démarrage, vérifiez les logs :

```
[INFO] Configuration chargée depuis config.json
[INFO] Base de données initialisée : ./data/shadowbot.db
[INFO] Serveur démarré sur http://localhost:3000
[INFO] Authentification activée
```

Si vous voyez des `[ERROR]`, consultez la section [Dépannage](../reference/troubleshooting.md).

## Sauvegarder votre configuration

```bash
# Créer une sauvegarde
cp config.json config.backup.json

# Sauvegarder avec Git
git add config.json
git commit -m "Configuration personnalisée"
```

**⚠️ Ne partagez JAMAIS** votre `config.json` contenant votre clé API !

---

**Prochaine étape** : [Première utilisation](quickstart.md) pour découvrir l'interface et ajouter vos premiers comptes.
