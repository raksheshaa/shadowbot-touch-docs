# Surveillance et logs

Surveillez vos bots et analysez leurs performances avec les outils de monitoring.

## Dashboard de monitoring

Accédez à **Monitoring** dans la sidebar pour voir la vue d'ensemble.

### Métriques en temps réel

```
┌──────────────────────────────────────────────────────┐
│ Métriques système                                    │
├──────────────────────────────────────────────────────┤
│                                                      │
│ CPU: ████████░░░░░░░░░░ 40%                         │
│ RAM: ████████████░░░░░░ 60% (4.8 / 8.0 GB)          │
│ Réseau: ↓ 125 KB/s  ↑ 45 KB/s                       │
│                                                      │
│ Bots actifs: 15 / 50                                 │
│ Connexions réussies: 342 (99.1%)                    │
│ Erreurs (24h): 3                                     │
└──────────────────────────────────────────────────────┘
```

### Graphiques de performance

**Graph 1: Activité des bots (24h)**
```
Nombre de bots connectés
20 ┤     ╭─────╮
15 ┤   ╭─╯     ╰─╮
10 ┤ ╭─╯         ╰─╮
5  ┤─╯             ╰───
   └────────────────────
   00h  06h  12h  18h  00h
```

**Graph 2: Ressources système**
```
% Utilisation
100┤                   ╭─
75 ┤         ╭────────╯
50 ┤    ╭────╯
25 ┤────╯
   └────────────────────
   CPU (bleu) | RAM (vert) | Réseau (orange)
```

## Console de logs

### Interface

```
┌─────────────────────────────────────────────────────┐
│ 🔍 [Rechercher...] [Niveau ▼] [Bot ▼] [Exporter]  │
├─────────────────────────────────────────────────────┤
│ 14:35:42 [INFO]  MonCompte1 - Connexion réussie    │
│ 14:35:45 [DEBUG] MonCompte1 - Chargement carte     │
│ 14:35:50 [WARN]  MonCompte2 - Latence élevée (520ms)│
│ 14:36:02 [ERROR] MonCompte3 - Échec connexion      │
│ 14:36:05 [INFO]  MonCompte1 - Récolte: Bois x15    │
│ 14:36:10 [INFO]  MonCompte4 - Combat vs Bouftou    │
│ 14:36:15 [DEBUG] MonCompte1 - Déplacement [5,2]    │
│ ...                                                 │
└─────────────────────────────────────────────────────┘
```

### Niveaux de logs

| Niveau | Couleur | Description | Exemple |
|--------|---------|-------------|---------|
| `DEBUG` | Gris | Détails techniques | Déplacement, actions |
| `INFO` | Bleu | Informations normales | Connexion, récolte |
| `WARN` | Orange | Avertissements | Latence élevée, inventaire plein |
| `ERROR` | Rouge | Erreurs | Échec connexion, crash |
| `FATAL` | Rouge foncé | Erreurs critiques | Corruption de données |

### Filtres

**Par niveau** :
```
[Tous] [Debug] [Info] [Warn] [Error]
```

**Par bot** :
```
[Tous les bots ▼]
├── MonCompte1
├── MonCompte2
├── MonCompte3
└── ...
```

**Par période** :
```
[Dernière heure] [Aujourd'hui] [7 jours] [30 jours] [Personnalisé]
```

**Recherche textuelle** :
```
🔍 Rechercher: "Récolte"
→ Affiche tous les logs contenant "Récolte"
```

## Alertes et notifications

### Types d'alertes

**Alertes système** :
- 🔴 Bot déconnecté de manière inattendue
- 🟡 Utilisation CPU > 80%
- 🟡 Utilisation RAM > 90%
- 🔴 Base de données corrompue

**Alertes de bot** :
- 🔴 Échec d'authentification (compte banni ?)
- 🟡 Latence élevée (> 500ms)
- 🟠 Inventaire plein
- 🔴 Erreur de proxy

**Alertes de sécurité** :
- 🔴 Tentative de connexion non autorisée
- 🟡 Limite IP proche (3/4 comptes)
- 🔴 Limite IP dépassée (4/4 comptes)

### Configuration des alertes

```
Paramètres → Notifications
┌─────────────────────────────────────┐
│ Types de notifications              │
├─────────────────────────────────────┤
│ ☑ Notifications navigateur          │
│ ☑ Notifications sonores             │
│ ☐ Email (non implémenté)            │
│ ☐ Webhook Discord                   │
│                                     │
│ Seuils d'alerte                     │
├─────────────────────────────────────┤
│ CPU élevé: [80]%                    │
│ RAM élevée: [90]%                   │
│ Latence élevée: [500]ms             │
│ Échecs connexion: [3] tentatives    │
└─────────────────────────────────────┘
```

### Notifications navigateur

Exemple de notification :

```
┌─────────────────────────────────┐
│ ShadowBot Touch                 │
├─────────────────────────────────┤
│ ⚠️ Bot déconnecté                │
│ MonCompte1 - Erreur de proxy    │
│ Il y a 2 minutes                │
└─────────────────────────────────┘
```

## Rapports détaillés

### Rapport par bot

Exportez un rapport complet pour un bot :

```markdown
# Rapport Bot: MonCompte1
Date: 14/12/2024
Période: 12:00 - 16:30 (4h 30m)

## Résumé
- Uptime: 95.3% (4h 17m)
- Déconnexions: 2
- Actions: 1,247

## Statistiques
### Ressources
- Bois: 156
- Fer: 89
- Blé: 203
**Total kamas**: 45,600

### Combats
- Victoires: 21
- Défaites: 2
- Taux de réussite: 91.3%

### Performance
- Latence moyenne: 47ms
- CPU moyen: 4.2%
- RAM moyenne: 98 MB

## Incidents
14:32 - Déconnexion (timeout proxy)
15:45 - Inventaire plein (résolu auto)

## Recommandations
- RAS, performances optimales
```

### Rapport global

Vue d'ensemble de tous les bots :

```markdown
# Rapport Global ShadowBot Touch
Date: 14/12/2024
Bots actifs: 15 / 50

## Performance globale
- Uptime moyen: 97.8%
- Erreurs totales: 12
- Ressources récoltées: 6,842

## Top 5 bots (par kamas)
1. MonCompte1: 45,600k
2. MonCompte5: 39,200k
3. MonCompte3: 34,100k
4. MonCompte7: 28,900k
5. MonCompte2: 25,400k

## Problèmes détectés
- Proxy "Principal": Latence élevée
- MonCompte8: Échecs répétés (vérifier compte)

## Utilisation ressources
- CPU: 42% (optimal)
- RAM: 5.8 GB / 8 GB (bon)
- Réseau: 890 KB/s (normal)
```

## Export des données

### Formats disponibles

**CSV** : Pour analyse Excel
```csv
timestamp,bot,level,action,result
2024-12-14 14:35:42,MonCompte1,INFO,Connexion,Réussite
2024-12-14 14:35:50,MonCompte1,INFO,Récolte,15 Bois
```

**JSON** : Pour traitement programmé
```json
[
  {
    "timestamp": "2024-12-14T14:35:42Z",
    "bot": "MonCompte1",
    "level": "INFO",
    "action": "Connexion",
    "result": "Réussite"
  }
]
```

**TXT** : Logs bruts
```
[2024-12-14 14:35:42] [INFO] MonCompte1 - Connexion réussie
[2024-12-14 14:35:50] [INFO] MonCompte1 - Récolte: Bois x15
```

### Procédure d'export

1. Monitoring → Logs
2. Appliquez les filtres souhaités
3. Cliquez sur **📥 Exporter**
4. Choisissez le format
5. Le fichier est téléchargé

## Analyse des performances

### Métriques clés

**Par bot** :
- Actions/heure
- Kamas/heure
- Uptime (%)
- Taux d'erreur (%)

**Globales** :
- Utilisation CPU/RAM
- Bande passante
- Nombre de connexions simultanées
- Latence moyenne

### Graphiques d'analyse

**Évolution temporelle** :
- Performance sur 7 jours
- Tendances d'activité
- Patterns de déconnexion

**Comparaison** :
- Bot A vs Bot B
- Serveur vs Serveur
- Avant/Après optimisation

## Maintenance et nettoyage

### Rotation des logs

**Configuration** :
```json
{
  "logs": {
    "maxSize": "10M",      // Taille max par fichier
    "maxFiles": 5,         // Nombre de fichiers à garder
    "compress": true,      // Compression des vieux logs
    "retention": 30        // Jours de rétention
  }
}
```

**Comportement** :
```
logs/
├── shadowbot.log (actif, 8.2 MB)
├── shadowbot.log.1 (9.8 MB)
├── shadowbot.log.2.gz (compressé)
├── shadowbot.log.3.gz
└── shadowbot.log.4.gz
```

### Nettoyage manuel

```
Paramètres → Maintenance
┌─────────────────────────────────────┐
│ Nettoyage des logs                  │
├─────────────────────────────────────┤
│ Logs actuels: 45 MB                 │
│ Fichiers: 12                        │
│                                     │
│ [🗑️ Vider les logs Debug]           │
│ [🗑️ Supprimer logs > 30 jours]      │
│ [🗑️ Nettoyer tout]                  │
└─────────────────────────────────────┘
```

## Monitoring distant

### API de monitoring

Accédez aux métriques via l'API :

```bash
# Métriques système
curl http://localhost:3000/api/metrics

# Statut des bots
curl http://localhost:3000/api/bots/status

# Logs récents
curl http://localhost:3000/api/logs?limit=100
```

### Webhooks

Configurez des webhooks pour recevoir des alertes :

```json
{
  "webhooks": [
    {
      "url": "https://discord.com/api/webhooks/...",
      "events": ["bot.disconnected", "error.critical"],
      "enabled": true
    }
  ]
}
```

**Exemple de payload** :
```json
{
  "event": "bot.disconnected",
  "bot": "MonCompte1",
  "timestamp": "2024-12-14T14:35:42Z",
  "reason": "Proxy timeout"
}
```

## Dépannage

### Logs incomplets

**Problème** : Logs manquants ou incomplets

**Solutions** :
- Vérifier le niveau de log (passer en DEBUG)
- Vérifier l'espace disque
- Vérifier les permissions d'écriture

### Performances dégradées

**Problème** : Interface lente avec beaucoup de logs

**Solutions** :
- Augmenter `maxSize` pour réduire la rotation
- Filtrer les logs DEBUG en production
- Activer la compression

### Erreurs dans les graphiques

**Problème** : Graphiques ne s'affichent pas

**Solutions** :
- Vider le cache navigateur
- Vérifier la console développeur
- Redémarrer l'application

---

**Prochaine étape** : Consultez la section [Architecture technique](../technical/overview.md) pour comprendre le fonctionnement interne.
