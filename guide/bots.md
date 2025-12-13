# Connexion des bots

Lancez et gérez vos bots Dofus Touch avec ShadowBot Touch.

## Créer un nouveau bot

### Processus de création

1. **Bots → + Nouveau bot**
2. **Sélectionnez un compte** dans la liste
3. **Configurez les paramètres** :

```
┌─────────────────────────────────────┐
│ Nouveau Bot                         │
├─────────────────────────────────────┤
│ Compte *                            │
│ [Sélectionner... ▼]                 │
│                                     │
│ Mode d'exécution                    │
│ ○ Farm automatique                  │
│ ○ Suivi de chemin                   │
│ ○ Combat PvP                        │
│ ○ Commerce                          │
│                                     │
│ Comportement                        │
│ ☑ Auto-reconnexion                  │
│ ☑ Esquiver les combats              │
│ ☐ Mode furtif                       │
│                                     │
│     [Annuler]  [Créer]              │
└─────────────────────────────────────┘
```

4. **Cliquez sur Créer**

## États des bots

### Cycle de vie

```
[Créé] → [Connexion] → [Connecté] → [Actif] → [Pause] → [Déconnecté]
           ↓              ↓           ↓         ↓
        [Erreur]      [Erreur]    [Erreur]  [Erreur]
```

### Codes couleur

- 🔵 **Connexion en cours** - Bot en cours de connexion
- 🟢 **Connecté** - Bot opérationnel
- 🟡 **En pause** - Suspendu temporairement
- 🔴 **Déconnecté** - Hors ligne
- 🟠 **Erreur** - Problème détecté

## Modes d'exécution

### Farm automatique

**Description** : Récolte automatique de ressources

**Paramètres** :
```
- Zone de farm : Sélectionner la carte
- Ressources ciblées : Bois, Minerai, etc.
- Inventaire plein : Retour banque / Continuer
- Durée max : 4 heures (recommandé)
```

**Comportement** :
1. Se déplace vers la zone
2. Détecte les ressources
3. Récolte automatiquement
4. Gère l'inventaire
5. Esquive les combats (optionnel)

### Suivi de chemin

**Description** : Suit un itinéraire prédéfini

**Configuration** :
```
- Chemin : Charger depuis fichier .path
- Vitesse : Lent / Normal / Rapide
- Répétition : Boucle / Aller-retour / Une fois
- Pauses : Toutes les X minutes
```

**Cas d'usage** :
- Parcours de quêtes
- Exploration de zones
- Transport de ressources

### Combat PvP

**Description** : Participation aux combats joueur vs joueur

**Stratégie** :
```
- Rôle : Tank / DPS / Support
- Cibles prioritaires : Heal / DPS / Tank
- Fuite si : HP < 30%
- Items à utiliser : Potions, sorts
```

### Commerce

**Description** : Gestion de l'hôtel de vente

**Opérations** :
- Mise en vente automatique
- Ajustement des prix (undercut)
- Achat d'opportunités
- Gestion du stock

## Lancer un bot

### Démarrage

1. Sélectionnez le bot dans la liste
2. Cliquez sur **▶ Démarrer**
3. Le bot lance la séquence de connexion

### Séquence de connexion

```
1. [00:00] Initialisation du bot
2. [00:01] Connexion au proxy (si configuré)
3. [00:02] Connexion au serveur auth
4. [00:05] Authentification réussie
5. [00:06] Connexion au serveur de jeu
6. [00:08] Sélection du personnage
7. [00:10] Chargement de la carte
8. [00:12] ✅ Bot opérationnel
```

**Durée typique** : 10-15 secondes

### Logs en temps réel

Pendant la connexion, les logs s'affichent :

```
[14:35:42] [INFO] Démarrage du bot MonCompte1
[14:35:43] [DEBUG] Connexion au proxy SOCKS5://192.168.1.100:1080
[14:35:44] [INFO] Proxy connecté - Latence: 45ms
[14:35:45] [INFO] Connexion au serveur d'authentification
[14:35:47] [INFO] Authentification réussie
[14:35:48] [INFO] Connexion au serveur Hélios
[14:35:50] [INFO] Personnage "Guerrier" sélectionné
[14:35:52] [INFO] Carte chargée: [0,0] Incarnam
[14:35:54] [INFO] ✅ Bot opérationnel
```

## Surveiller un bot

### Vue détaillée

Cliquez sur un bot pour voir ses détails :

```
┌─────────────────────────────────────────────────┐
│ 🟢 MonCompte1 - Guerrier Niveau 50              │
├─────────────────────────────────────────────────┤
│ Serveur: Hélios                                 │
│ Position: [5,2] Forêt d'Astrub                  │
│ État: Farm en cours                             │
│ Temps de connexion: 02:15:32                    │
│                                                  │
│ Statistiques de session:                        │
│ • Ressources récoltées: 156                     │
│ • Kamas gagnés: 12,450                          │
│ • Combats: 8 (7V - 1D)                          │
│ • Déplacements: 234                             │
│                                                  │
│ ┌────────────────────────────────────┐          │
│ │ Actions récentes:                  │          │
│ │ 14:32 - Récolte: Bois de Frêne x15│          │
│ │ 14:35 - Déplacement: [5,2] → [5,3]│          │
│ │ 14:37 - Combat: Bouftou (victoire) │          │
│ │ 14:40 - Récolte: Fer x8           │          │
│ └────────────────────────────────────┘          │
│                                                  │
│ [⏸ Pause] [🛑 Arrêter] [⚙ Paramètres]         │
└─────────────────────────────────────────────────┘
```

### Indicateurs de performance

**CPU** : Utilisation processeur du bot
- 🟢 < 5% : Normal
- 🟡 5-15% : Élevé
- 🔴 > 15% : Problème

**RAM** : Mémoire utilisée
- Typique : 80-120 MB par bot

**Réseau** : 
- Upload : 5-10 KB/s
- Download : 10-20 KB/s

**Latence** :
- Vers le serveur de jeu
- 🟢 < 50ms : Excellent
- 🟡 50-150ms : Bon
- 🔴 > 150ms : Problématique

## Gérer un bot actif

### Mettre en pause

**Action** : Cliquez sur ⏸ Pause

**Comportement** :
1. Termine l'action en cours
2. Se met en sécurité (sort du combat si nécessaire)
3. Reste connecté mais inactif
4. Peut être repris avec ▶ Reprendre

**Cas d'usage** :
- Interruption temporaire
- Vérification manuelle
- Attente d'événement

### Arrêter proprement

**Action** : Cliquez sur 🛑 Arrêter

**Comportement** :
1. Termine les actions en cours
2. Sauvegarde la progression
3. Se déconnecte proprement du serveur
4. Libère les ressources

> ⚠️ **Important** : Toujours arrêter proprement pour éviter la corruption des données

### Redémarrer

**Action** : 🔄 Redémarrer (disponible si erreur)

**Utilisation** :
- Après une erreur
- Changement de configuration
- Réinitialisation

## Auto-reconnexion

### Configuration

```json
{
  "reconnect": {
    "enabled": true,
    "maxAttempts": 3,
    "delayMs": 5000,
    "exponentialBackoff": true
  }
}
```

**Paramètres** :
- `enabled` : Activer/désactiver
- `maxAttempts` : Nombre de tentatives
- `delayMs` : Délai entre tentatives (ms)
- `exponentialBackoff` : Augmentation progressive du délai

### Comportement

```
Déconnexion détectée
↓
Attente: 5 secondes
↓
Tentative 1: Échec
↓
Attente: 10 secondes (backoff)
↓
Tentative 2: Échec
↓
Attente: 20 secondes (backoff)
↓
Tentative 3: Réussite ✅
```

Si toutes les tentatives échouent : Marquer comme erreur et notifier l'utilisateur

## Gestion des erreurs

### Types d'erreurs

**Erreur de connexion** :
```
❌ Impossible de se connecter au serveur
Cause: Timeout après 30 secondes
Solution: Vérifier la connexion internet / proxy
```

**Erreur d'authentification** :
```
❌ Authentification échouée
Cause: Identifiants invalides
Solution: Vérifier le compte dans les paramètres
```

**Erreur de gameplay** :
```
❌ Action impossible
Cause: Inventaire plein
Solution: Activer le retour banque automatique
```

**Erreur de proxy** :
```
❌ Proxy injoignable
Cause: Proxy hors ligne
Solution: Changer de proxy ou désactiver
```

### Actions correctives

**Automatiques** :
- Reconnexion (si activée)
- Changement de proxy (si backup disponible)
- Sauvegarde de l'état

**Manuelles** :
- Vérifier la configuration
- Consulter les logs détaillés
- Ajuster les paramètres
- Redémarrer le bot

## Actions en masse sur les bots

### Sélection multiple

1. Cochez plusieurs bots
2. Utilisez la barre d'actions en masse

**Actions disponibles** :
- ▶ Démarrer tous
- ⏸ Mettre tous en pause
- 🛑 Arrêter tous
- 🗑️ Supprimer tous

### Filtres rapides

```
[Tous (50)] [🟢 Actifs (15)] [🟡 Pause (5)] [🔴 Déconnectés (30)]
```

Cliquez pour filtrer et appliquer des actions groupées.

## Statistiques et rapports

### Rapport de session

Exportez les statistiques d'une session :

```json
{
  "bot": "MonCompte1",
  "session": {
    "start": "2024-12-14T12:00:00Z",
    "end": "2024-12-14T16:30:00Z",
    "duration": "4h 30m"
  },
  "stats": {
    "resourcesGathered": 342,
    "kamasEarned": 45600,
    "combats": {
      "total": 23,
      "victories": 21,
      "defeats": 2
    },
    "movements": 567
  }
}
```

### Graphiques de performance

Visualisez l'évolution :
- Kamas gagnés par heure
- Ressources récoltées
- Taux de victoire en combat
- Uptime du bot

## Optimisation

### Performances

**Réduire l'utilisation CPU** :
- Diminuer la fréquence de mise à jour
- Désactiver les logs DEBUG
- Limiter le nombre de bots simultanés

**Réduire l'utilisation RAM** :
- Nettoyer le cache régulièrement
- Limiter l'historique des actions
- Fermer les bots inactifs

### Fiabilité

**Améliorer la stabilité** :
- Utiliser des proxies de qualité
- Activer l'auto-reconnexion
- Surveiller les performances
- Mettre à jour régulièrement

---

**Prochaine section** : [Surveillance et logs](monitoring.md) pour un monitoring approfondi.
