# Limites et contraintes

Limites techniques et recommandations pour ShadowBot Touch.

## Limites serveur (Dofus Touch)

### Connexions par IP

⚠️ **CRITIQUE** : Maximum **4 comptes** par adresse IP

Dépassement = bannissement automatique de l'IP

**Solutions** :
- Utiliser des proxies (1 proxy = 4 comptes max)
- Distribution intelligente avec `maxAccountsPerIP: 4`

### Rate limiting

- Requêtes API : ~100/minute
- Messages WebSocket : ~60/minute
- Connexions simultanées : 4/IP

## Limites application

### Ressources système

**Par bot** :
- CPU : ~1-3%
- RAM : 80-120 MB
- Réseau : 10-30 KB/s

**Recommandations par configuration** :

| RAM totale | CPU | Bots max recommandés |
|------------|-----|----------------------|
| 4 GB       | 2c  | 10-15                |
| 8 GB       | 4c  | 25-35                |
| 16 GB      | 8c  | 45-50                |

### Base de données

- Taille max : ~2 GB (SQLite)
- Comptes : Illimité (pratique: ~1000)
- Logs : Rotation automatique recommandée

### Proxies

- Proxies max : Illimité
- Comptes par proxy : 4 (STRICT)
- Test simultanés : 10

## Bonnes pratiques

### Démarrage progressif

```
Jour 1 : 5 bots
Jour 2 : 10 bots
Jour 3 : 15 bots
...
Stabiliser avant d'augmenter
```

### Monitoring continu

- Surveiller CPU/RAM
- Vérifier latence réseau
- Consulter logs régulièrement
- Tester reconnexions

### Sauvegardes

- Quotidiennes automatiques
- Avant modifications importantes
- Export régulier des comptes

---

**Prochaine section**: [FAQ](faq.md)
