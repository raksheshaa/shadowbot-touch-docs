# Protocoles réseau

Comprendre les protocoles de communication avec Dofus Touch.

## Architecture réseau

```
ShadowBot → [Proxy] → Auth Server → Game Server
                         ↓             ↓
                      Tokens      WebSocket (Primus)
```

## Serveurs Dofus Touch

### Serveur d'authentification

```
Hôte: dt-proxy-production-login.ankama-games.com
Port: 443 (HTTPS)
Protocol: REST API + WebSocket
```

**Endpoints**:
- `/api/auth/login` - Authentification
- `/api/servers` - Liste des serveurs
- `/api/characters` - Liste des personnages

### Serveur de jeu

```
Hôte: dt-proxy-production-france.ankama-games.com
Port: 443 (WSS - WebSocket Secure)
Protocol: Primus (WebSocket wrapper)
```

## Primus WebSocket

Dofus Touch utilise **Primus**, un wrapper WebSocket.

### Connexion

```javascript
const Primus = require('primus');
const client = new Primus('wss://dt-proxy-production-france.ankama-games.com', {
  transformer: 'websockets',
  plugin: {
    emitter: require('primus-emitter')
  }
});

client.on('open', () => {
  console.log('Connexion établie');
});

client.on('data', (message) => {
  console.log('Message reçu:', message);
});
```

### Messages

Format des messages (exemple):
```json
{
  "type": "GameMessage",
  "action": "move",
  "data": {
    "x": 5,
    "y": 2,
    "mapId": 12345
  }
}
```

## Authentification

### Séquence

1. **POST** `/api/auth/login` avec credentials
2. Réception des **tokens** (access_token, refresh_token)
3. Utiliser le token pour se connecter au serveur de jeu
4. WebSocket établi avec le token dans le header

```javascript
const response = await fetch('https://dt-proxy-production-login.ankama-games.com/api/auth/login', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({
    username: 'compte@ankama.com',
    password: 'password123'
  })
});

const { access_token, refresh_token } = await response.json();
```

## Proxies

### Configuration SOCKS5

```javascript
const { SocksProxyAgent } = require('socks-proxy-agent');

const agent = new SocksProxyAgent({
  hostname: '192.168.1.100',
  port: 1080,
  username: 'proxyuser',
  password: 'proxypass'
});

const response = await fetch(url, { agent });
```

### Configuration HTTP

```javascript
const { HttpProxyAgent } = require('http-proxy-agent');

const agent = new HttpProxyAgent({
  host: 'proxy.example.com',
  port: 8080,
  auth: 'user:pass'
});
```

## Analyse des captures mitmproxy

Les captures fournies contiennent:
- Requêtes d'authentification complètes
- Séquence de création de personnage
- Communications WebSocket
- Headers et tokens

Structure type:
```
Flow:
  Request:
    URL: https://dt-proxy-production-login.ankama-games.com/...
    Method: POST
    Headers: {...}
    Body: {...}
  Response:
    Status: 200
    Headers: {...}
    Body: {...}
```

---

**Prochaine section**: [Système d'authentification](authentication.md)
