# Dépannage

Solutions aux problèmes courants de ShadowBot Touch.

## Installation

### npm install échoue

**Symptômes**: Erreurs pendant `npm install`

**Solutions**:
```bash
# Nettoyer le cache npm
npm cache clean --force

# Supprimer node_modules
rm -rf node_modules package-lock.json

# Réinstaller
npm install
```

### Port déjà utilisé

**Erreur**: `EADDRINUSE: address already in use :::3000`

**Solution**:
```bash
# Changer le port
export SHADOWBOT_PORT=8080
npm start

# Ou tuer le processus sur port 3000
# Linux/Mac:
lsof -ti:3000 | xargs kill

# Windows:
netstat -ano | findstr :3000
taskkill /PID <PID> /F
```

## Base de données

### Base corrompue

**Symptômes**: Erreurs au démarrage, données manquantes

**Solution**:
```bash
# Restaurer depuis backup
cp data/backups/shadowbot_<date>.db data/shadowbot.db

# Si pas de backup, réinitialiser
rm data/shadowbot.db
# Relancer l'app (créera nouvelle BDD)
```

### Migration échoue

**Erreur**: Erreur de migration de schéma

**Solution**:
```bash
# Backup actuel
cp data/shadowbot.db data/shadowbot.db.backup

# Forcer recréation
rm data/shadowbot.db
npm start
```

## Connexions

### Bot ne se connecte pas

**Checklist**:
- [ ] Identifiants corrects
- [ ] Serveur en ligne
- [ ] Internet fonctionnel
- [ ] Firewall n'bloque pas
- [ ] Proxy fonctionnel (si utilisé)

**Debug**:
```bash
# Passer en mode DEBUG
export LOG_LEVEL=debug
npm start

# Vérifier les logs
tail -f logs/shadowbot.log
```

### Proxy timeout

**Cause**: Proxy hors ligne ou trop lent

**Solutions**:
1. Tester le proxy manuellement
2. Augmenter timeout dans config.json:
   ```json
   { "proxy": { "timeout": 30000 } }
   ```
3. Changer de proxy

### Déconnexions fréquentes

**Causes possibles**:
- Latence réseau élevée
- Proxy instable
- Limite IP atteinte

**Solutions**:
1. Activer auto-reconnect
2. Utiliser proxy de meilleure qualité
3. Vérifier nombre de connexions par IP

## Performance

### Utilisation RAM élevée

**Symptômes**: >90% RAM utilisée

**Solutions**:
1. Réduire nombre de bots
2. Redémarrer l'application régulièrement
3. Nettoyer les logs:
   ```bash
   rm -rf logs/*.log.gz
   ```

### CPU 100%

**Causes**: Trop de bots ou boucle infinie

**Solutions**:
1. Arrêter tous les bots
2. Vérifier logs pour erreurs
3. Redémarrer l'application
4. Réduire `maxInstances`

### Interface lente

**Solutions**:
1. Vider cache navigateur
2. Réduire nombre de bots affichés
3. Désactiver logs DEBUG
4. Utiliser Chrome/Firefox

## Erreurs spécifiques

### "Maximum connections reached"

**Cause**: Limite d'instances atteinte

**Solution**: Augmenter `maxInstances` dans config.json

### "Authentication failed"

**Causes**:
- Mauvais identifiants
- Compte banni
- Token expiré

**Solutions**:
1. Vérifier identifiants
2. Tester connexion manuelle
3. Vérifier statut compte

### "Proxy banned"

**Cause**: IP proxy bannie par le serveur

**Solution**:
1. Supprimer ce proxy immédiatement
2. Ne plus l'utiliser
3. Contacter fournisseur proxy
4. Obtenir nouvelle IP

## Logs et debugging

### Activer debug complet

```bash
# Dans config.json
{
  "logging": {
    "level": "debug",
    "console": true
  }
}
```

### Exporter les logs

```bash
# Créer archive des logs
tar -czf logs-$(date +%Y%m%d).tar.gz logs/

# Envoyer pour analyse
```

### Analyser un crash

1. Vérifier `logs/error.log`
2. Noter le timestamp
3. Chercher la stack trace
4. Reproduire le problème
5. Créer issue GitHub avec logs

## Récupération d'urgence

### Reset complet

```bash
# ATTENTION: Perte de toutes les données

# Sauvegarder si possible
cp data/shadowbot.db backup.db

# Reset
rm -rf data/ logs/
npm start
```

### Restauration

```bash
# Depuis backup
cp backup/shadowbot.db data/shadowbot.db

# Vérifier intégrité
sqlite3 data/shadowbot.db "PRAGMA integrity_check;"
```

## Support

Si le problème persiste:

1. **GitHub Issues**: Créer une issue détaillée
2. **Discord**: Support communautaire
3. **Logs**: Toujours joindre les logs pertinents
4. **Reproduction**: Décrire étapes pour reproduire

**Format issue GitHub**:
```markdown
## Description
Description claire du problème

## Étapes pour reproduire
1. ...
2. ...

## Comportement attendu
Ce qui devrait se passer

## Comportement actuel
Ce qui se passe réellement

## Environnement
- OS: Windows 10
- Node: v18.12.0
- Version ShadowBot: 1.0.0

## Logs
```
[coller logs pertinents]
```
```

---

Documentation complète. Retour au [Sommaire](../SUMMARY.md).
