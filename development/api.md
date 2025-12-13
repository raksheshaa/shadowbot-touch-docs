# API interne

Documentation des endpoints REST de ShadowBot Touch.

## Base URL

```
http://localhost:3000/api
```

## Authentification

Toutes les requêtes nécessitent un header d'authentification:

```http
X-API-Key: votre_cle_api
```

## Endpoints

### Comptes

**GET** `/api/accounts`
Récupère tous les comptes.

```json
{
  "success": true,
  "data": [
    {
      "id": 1,
      "username": "compte@ankama.com",
      "server": "Hélios",
      "proxy_id": 1,
      "created_at": "2024-01-15T10:00:00Z"
    }
  ]
}
```

**POST** `/api/accounts`
Crée un nouveau compte.

```json
{
  "username": "compte@ankama.com",
  "password": "password123",
  "server": "Hélios",
  "proxy_id": 1
}
```

**PUT** `/api/accounts/:id`
Modifie un compte existant.

**DELETE** `/api/accounts/:id`
Supprime un compte.

### Proxies

**GET** `/api/proxies`
Liste tous les proxies.

**POST** `/api/proxies`
Ajoute un proxy.

```json
{
  "description": "Proxy Principal",
  "type": "SOCKS5",
  "host": "192.168.1.100",
  "port": 1080,
  "username": "user",
  "password": "pass"
}
```

**POST** `/api/proxies/:id/test`
Teste la connexion d'un proxy.

### Bots

**GET** `/api/bots`
Liste tous les bots.

**POST** `/api/bots/start`
Démarre un bot.

```json
{
  "account_id": 1,
  "mode": "farm",
  "config": {
    "autoReconnect": true,
    "maxReconnectAttempts": 3
  }
}
```

**POST** `/api/bots/:id/pause`
Met un bot en pause.

**POST** `/api/bots/:id/stop`
Arrête un bot.

**GET** `/api/bots/:id/stats`
Statistiques d'un bot.

### Monitoring

**GET** `/api/metrics`
Métriques système.

```json
{
  "cpu": 42.5,
  "ram": 60.2,
  "bots": {
    "active": 15,
    "total": 50
  },
  "connections": {
    "success_rate": 99.1
  }
}
```

**GET** `/api/logs`
Récupère les logs.

Paramètres:
- `level`: DEBUG, INFO, WARN, ERROR
- `bot_id`: Filtrer par bot
- `limit`: Nombre de logs (défaut: 100)

## WebSocket Events

Connexion: `ws://localhost:3000`

### Events émis par le serveur

**bot.connected**
```json
{
  "bot_id": 1,
  "account": "MonCompte1",
  "server": "Hélios",
  "timestamp": "2024-12-14T14:35:42Z"
}
```

**bot.disconnected**
```json
{
  "bot_id": 1,
  "reason": "Proxy timeout"
}
```

**bot.action**
```json
{
  "bot_id": 1,
  "action": "resource_gathered",
  "data": {
    "resource": "Bois",
    "quantity": 15
  }
}
```

**metrics.update**
```json
{
  "cpu": 45.2,
  "ram": 62.1,
  "active_bots": 16
}
```

---

**Prochaine section**: [Contribuer](contributing.md)
