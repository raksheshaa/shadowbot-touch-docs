# Configuration avancée

Options de configuration détaillées pour ShadowBot Touch.

## Structure config.json

```json
{
  "server": {
    "port": 3000,
    "host": "localhost",
    "cors": {
      "enabled": true,
      "origins": ["http://localhost:3000"]
    }
  },
  "security": {
    "apiKey": "CHANGEZ_MOI",
    "sessionTimeout": 3600,
    "rateLimit": {
      "windowMs": 900000,
      "max": 100
    }
  },
  "database": {
    "path": "./data/shadowbot.db",
    "autoBackup": true,
    "backupInterval": 86400,
    "backupPath": "./data/backups",
    "retentionDays": 30
  },
  "bots": {
    "maxInstances": 50,
    "reconnect": {
      "enabled": true,
      "maxAttempts": 3,
      "delayMs": 5000,
      "exponentialBackoff": true
    },
    "heartbeat": {
      "enabled": true,
      "intervalMs": 30000
    }
  },
  "proxy": {
    "maxAccountsPerIP": 4,
    "rotationEnabled": false,
    "rotationInterval": 21600,
    "healthCheck": {
      "enabled": true,
      "intervalMs": 300000
    }
  },
  "logging": {
    "level": "info",
    "path": "./logs",
    "maxSize": "10M",
    "maxFiles": 5,
    "compress": true,
    "console": true
  },
  "notifications": {
    "browser": true,
    "sound": false,
    "webhook": {
      "enabled": false,
      "url": ""
    }
  }
}
```

## Variables d'environnement

```bash
# Serveur
SHADOWBOT_PORT=3000
SHADOWBOT_HOST=localhost

# Sécurité
SHADOWBOT_API_KEY=votre_cle_api_securisee
SHADOWBOT_JWT_SECRET=secret_jwt_tres_long

# Base de données
SHADOWBOT_DB_PATH=./data/shadowbot.db

# Logs
LOG_LEVEL=info        # debug, info, warn, error
LOG_PATH=./logs
```

## Profils de configuration

### Développement

```json
{
  "logging": { "level": "debug", "console": true },
  "bots": { "maxInstances": 5 },
  "notifications": { "browser": false }
}
```

### Production

```json
{
  "logging": { "level": "warn", "console": false },
  "bots": { "maxInstances": 50 },
  "security": { "rateLimit": { "max": 50 } }
}
```

### Test

```json
{
  "database": { "path": ":memory:" },
  "bots": { "maxInstances": 2 },
  "logging": { "level": "error" }
}
```

---

**Prochaine section**: [Limites et contraintes](limits.md)
