# Gestion des connexions

Système de connexion et reconnexion des bots.

## Manager de connexions

```javascript
class ConnectionManager {
  constructor() {
    this.connections = new Map();
    this.reconnectAttempts = new Map();
  }

  async connect(bot) {
    try {
      // 1. Connexion proxy (si configuré)
      if (bot.proxy) {
        await this.connectProxy(bot);
      }

      // 2. Authentification
      const token = await this.authenticate(bot.account);

      // 3. Connexion WebSocket
      const ws = await this.connectWebSocket(token, bot.server);

      // 4. Sélection personnage
      await this.selectCharacter(ws, bot.character);

      this.connections.set(bot.id, ws);
      bot.status = 'connected';

    } catch (error) {
      await this.handleConnectionError(bot, error);
    }
  }

  async reconnect(bot) {
    const attempts = this.reconnectAttempts.get(bot.id) || 0;
    
    if (attempts >= bot.config.maxReconnectAttempts) {
      bot.status = 'error';
      return;
    }

    this.reconnectAttempts.set(bot.id, attempts + 1);
    
    const delay = bot.config.reconnectDelay * Math.pow(2, attempts);
    await sleep(delay);
    
    await this.connect(bot);
  }
}
```

## États de connexion

```
CREATED → CONNECTING → AUTHENTICATING → CONNECTED → ACTIVE
   ↓         ↓             ↓               ↓           ↓
ERROR ←───────────────────────────────────────────────┘
   ↓
RECONNECTING (si auto-reconnect activé)
```

## Heartbeat et keep-alive

```javascript
class Heartbeat {
  constructor(connection, interval = 30000) {
    this.connection = connection;
    this.interval = interval;
    this.timer = null;
  }

  start() {
    this.timer = setInterval(() => {
      if (this.connection.readyState === WebSocket.OPEN) {
        this.connection.send(JSON.stringify({ type: 'ping' }));
      }
    }, this.interval);
  }

  stop() {
    if (this.timer) {
      clearInterval(this.timer);
      this.timer = null;
    }
  }
}
```

## Gestion des erreurs

```javascript
async handleConnectionError(bot, error) {
  logger.error(`[${bot.id}] Erreur: ${error.message}`);

  if (error.code === 'ECONNREFUSED') {
    // Serveur inaccessible
    bot.status = 'error';
    notify('Serveur inaccessible');
  } else if (error.code === 'AUTH_FAILED') {
    // Authentification échouée
    bot.status = 'error';
    notify('Identifiants invalides');
  } else if (bot.config.autoReconnect) {
    // Tenter une reconnexion
    await this.reconnect(bot);
  }
}
```

## Pool de connexions

Pour optimiser les ressources:

```javascript
class ConnectionPool {
  constructor(maxConnections = 50) {
    this.pool = [];
    this.maxConnections = maxConnections;
  }

  async acquire() {
    if (this.pool.length >= this.maxConnections) {
      throw new Error('Maximum connections reached');
    }
    const connection = await this.createConnection();
    this.pool.push(connection);
    return connection;
  }

  release(connection) {
    const index = this.pool.indexOf(connection);
    if (index > -1) {
      this.pool.splice(index, 1);
    }
  }
}
```

---

Documentation technique complète. Consultez les sections développement pour contribuer au projet.
