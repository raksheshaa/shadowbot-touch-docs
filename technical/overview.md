# Vue d'ensemble technique

Architecture et principes de conception de ShadowBot Touch.

## Architecture globale

```
Interface Web (React) 
        ↓
Serveur Express (API REST + WebSocket)
        ↓
sql.js (SQLite pure JavaScript)
        ↓
Moteur de connexion (Primus/WebSocket)
        ↓
Serveurs Dofus Touch
```

## Stack technologique

- **Frontend**: React, recharts, axios
- **Backend**: Node.js, Express, Socket.io
- **Base de données**: sql.js (SQLite sans compilation native)
- **Réseau**: Primus (WebSocket wrapper), SOCKS/HTTP proxies
- **Sécurité**: JWT, AES-256, bcrypt

## Flux de connexion bot

1. User démarre bot via UI
2. API récupère compte + proxy en BDD
3. Connexion via proxy (si configuré)
4. Auth serveur Ankama → tokens
5. Connexion serveur de jeu via Primus/WebSocket
6. Sélection personnage
7. Bot opérationnel → Updates UI temps réel

## Principes clés

- **Modularité**: Modules indépendants (api, bot, database, network)
- **Scalabilité**: Multi-instances isolées
- **Fiabilité**: Auto-reconnexion, sauvegardes, rollback
- **Sécurité**: Chiffrement, validation, rate limiting

## Optimisations

- Lazy loading modules
- Caching en mémoire
- Connection pooling
- Limite instances configurée

Voir sections suivantes pour détails techniques.
