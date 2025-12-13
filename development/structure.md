# Structure du projet

Organisation des fichiers et dossiers de ShadowBot Touch.

## Arborescence

```
shadowbot-touch/
├── src/
│   ├── api/               # API REST endpoints
│   │   ├── accounts.js
│   │   ├── proxies.js
│   │   ├── bots.js
│   │   └── auth.js
│   ├── bot/               # Logique des bots
│   │   ├── BotManager.js
│   │   ├── FarmBot.js
│   │   └── PvPBot.js
│   ├── database/          # Couche données
│   │   ├── Database.js
│   │   ├── models/
│   │   └── migrations/
│   ├── network/           # Protocoles réseau
│   │   ├── AuthClient.js
│   │   ├── GameClient.js
│   │   └── ProxyManager.js
│   ├── ui/                # Interface React
│   │   ├── components/
│   │   ├── pages/
│   │   └── App.jsx
│   └── server.js          # Serveur Express principal
├── data/                  # Données persistantes
│   ├── shadowbot.db
│   └── backups/
├── logs/                  # Fichiers de logs
├── config.json            # Configuration
├── package.json
└── README.md
```

## Modules principaux

### /src/api
Endpoints REST pour l'interface web.

### /src/bot
Logique métier des bots et gestion des instances.

### /src/database
Couche d'abstraction base de données avec sql.js.

### /src/network
Gestion des connexions réseau, proxies, WebSocket.

### /src/ui
Interface React avec composants réutilisables.

## Conventions

### Nommage
- **Fichiers**: PascalCase pour classes, camelCase pour utilitaires
- **Variables**: camelCase
- **Constantes**: UPPER_SNAKE_CASE
- **Composants React**: PascalCase

### Code style
```javascript
// ESLint + Prettier recommandés
// async/await préféré aux promesses .then()
// Commentaires JSDoc pour fonctions publiques

/**
 * Connecte un bot au serveur de jeu
 * @param {Object} bot - Instance du bot
 * @param {string} server - Serveur cible
 * @returns {Promise<void>}
 */
async function connectBot(bot, server) {
  // Implementation
}
```

---

**Prochaine section**: [API interne](api.md)
