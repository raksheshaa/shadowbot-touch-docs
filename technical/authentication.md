# Système d'authentification

Gestion de l'authentification pour ShadowBot Touch.

## Double authentification

### 1. Authentification UI (Claude.ai)

Protection de l'interface web avec clé API.

```javascript
// Middleware Express
app.use((req, res, next) => {
  const apiKey = req.headers['x-api-key'];
  if (apiKey !== process.env.SHADOWBOT_API_KEY) {
    return res.status(401).json({ error: 'Non autorisé' });
  }
  next();
});
```

### 2. Authentification Dofus Touch

Connexion aux serveurs de jeu avec credentials Ankama.

## Flux d'authentification

```
1. User entre clé API → Accès interface
2. User démarre bot → Récupération credentials compte
3. Bot se connecte → Auth serveur Ankama → Tokens
4. Connexion serveur jeu avec tokens
5. Sélection personnage
6. Bot opérationnel
```

## Gestion des tokens

```javascript
class TokenManager {
  constructor() {
    this.tokens = new Map();
  }

  async authenticate(username, password) {
    const response = await fetch(authUrl, {
      method: 'POST',
      body: JSON.stringify({ username, password })
    });
    
    const { access_token, refresh_token, expires_in } = await response.json();
    
    this.tokens.set(username, {
      access: access_token,
      refresh: refresh_token,
      expiresAt: Date.now() + (expires_in * 1000)
    });
    
    return access_token;
  }

  async refreshToken(username) {
    const tokenData = this.tokens.get(username);
    if (!tokenData) throw new Error('No token found');
    
    const response = await fetch(refreshUrl, {
      method: 'POST',
      headers: {
        'Authorization': `Bearer ${tokenData.refresh}`
      }
    });
    
    const { access_token } = await response.json();
    tokenData.access = access_token;
    tokenData.expiresAt = Date.now() + 3600000;
    
    return access_token;
  }
}
```

## Sécurité

- Clés API générées aléatoirement (32+ bytes)
- Tokens JWT avec expiration
- Refresh automatique avant expiration
- Stockage sécurisé (chiffrement AES-256)

---

**Prochaine section**: [Gestion des connexions](connections.md)
