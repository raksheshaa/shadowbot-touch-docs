# Gestion des proxies

Les proxies sont essentiels pour gérer plusieurs comptes sans risque de bannissement.

## Pourquoi utiliser des proxies ?

### Limite serveur : 4 comptes par IP

Le serveur Dofus Touch limite à **4 comptes simultanés par adresse IP**.

**Sans proxies** :
```
Votre IP : 203.0.113.1
└── Maximum 4 comptes connectés
```

**Avec proxies** :
```
Votre IP : 203.0.113.1
├── Proxy 1 : 198.51.100.10 → 4 comptes
├── Proxy 2 : 198.51.100.11 → 4 comptes
├── Proxy 3 : 198.51.100.12 → 4 comptes
└── Proxy 4 : 198.51.100.13 → 4 comptes
Total : 16 comptes simultanés
```

### Avantages

- ✅ Multiplier le nombre de comptes
- ✅ Isolation des connexions
- ✅ Éviter les bannissements
- ✅ Meilleure gestion des risques

## Types de proxies supportés

### HTTP/HTTPS

**Avantages** :
- Simple à configurer
- Largement disponible
- Compatible avec la plupart des fournisseurs

**Configuration** :
```
Type : HTTP
Hôte : proxy.example.com
Port : 8080
Auth : username:password (optionnel)
```

### SOCKS4/SOCKS5

**Avantages** :
- Plus rapide que HTTP
- Meilleur pour le gaming
- Support UDP (SOCKS5)

**Configuration** :
```
Type : SOCKS5
Hôte : 192.168.1.100
Port : 1080
Auth : username:password (optionnel)
```

**Recommandation** : SOCKS5 pour de meilleures performances

## Ajouter un proxy

### Via l'interface

1. **Proxies → + Ajouter un proxy**

```
┌─────────────────────────────────────┐
│ Ajouter un proxy                    │
├─────────────────────────────────────┤
│ Description *                       │
│ [Mon proxy principal]               │
│                                     │
│ Type *                              │
│ [SOCKS5 ▼]                          │
│                                     │
│ Hôte *                              │
│ [192.168.1.100]                     │
│                                     │
│ Port *                              │
│ [1080]                              │
│                                     │
│ ─── Authentification (optionnel)    │
│                                     │
│ Nom d'utilisateur                   │
│ [proxyuser]                         │
│                                     │
│ Mot de passe                        │
│ [••••••••]                          │
│                                     │
│     [Tester] [Annuler] [Enregistrer]│
└─────────────────────────────────────┘
```

2. **Cliquez sur "Tester"** pour vérifier la connexion

```
✅ Test réussi
Latence : 45ms
IP sortante : 198.51.100.10
Localisation : France, Paris
```

3. **Enregistrez** si le test est concluant

### Via import

**Format CSV** :
```csv
description,type,host,port,username,password
Proxy Principal,SOCKS5,192.168.1.100,1080,user1,pass1
Proxy Backup,HTTP,proxy.example.com,8080,,
Proxy US,SOCKS5,10.0.0.5,1080,user2,pass2
```

**Import** :
1. Proxies → Import
2. Sélectionnez le fichier CSV
3. Validez l'import

## Tester un proxy

### Test manuel

Cliquez sur l'icône 🧪 pour tester :

**Informations testées** :
- ✅ Connectivité
- ✅ Latence
- ✅ IP sortante
- ✅ Bande passante
- ✅ Compatibilité avec Dofus Touch

**Résultats possibles** :

```
✅ Test réussi
Latence : 45ms
Bande passante : 10 Mbps
Statut : Opérationnel

⚠️ Latence élevée
Latence : 850ms
Recommandation : Vérifier la connexion

❌ Test échoué
Erreur : Connection timeout
Cause : Proxy hors ligne ou bloqué
```

### Test automatique

**Activation** :
Paramètres → Proxies → Test automatique

**Fréquence** : Toutes les 5 minutes

**Action en cas d'échec** :
- Marquer le proxy comme indisponible
- Rediriger les comptes vers un autre proxy
- Notification d'alerte

## Distribution des comptes

### Distribution manuelle

Assignez manuellement les comptes aux proxies :

1. Sélectionnez un compte
2. Modifier → Proxy → Sélectionner dans la liste
3. Enregistrer

### Distribution automatique

**Stratégie intelligente** :
- Équilibre la charge (comptes répartis uniformément)
- Respecte la limite de 4 comptes/proxy
- Priorise les proxies avec meilleure latence

**Utilisation** :
1. Sélectionnez plusieurs comptes
2. Actions → Assigner des proxies
3. Choisir "Distribution automatique"
4. Confirmer

**Algorithme** :
```
Pour chaque compte :
  1. Trouver les proxies disponibles (< 4 comptes)
  2. Trier par latence (meilleurs en premier)
  3. Assigner au premier proxy disponible
  4. Marquer le proxy comme utilisé
```

### Rotation des proxies

**Activation** :
Paramètres → Proxies → Activer la rotation

**Fonctionnement** :
- Changement automatique toutes les X heures
- Évite la détection de patterns
- Répartit l'usure des proxies

**Configuration** :
```json
{
  "rotationEnabled": true,
  "rotationInterval": 21600,  // 6 heures en secondes
  "rotationStrategy": "random" // random, sequential, load-based
}
```

## Surveillance des proxies

### Indicateurs de santé

Pour chaque proxy, surveillez :

**Latence** :
- 🟢 < 100ms : Excellent
- 🟡 100-500ms : Acceptable
- 🔴 > 500ms : Problématique

**Utilisation** :
- `0/4` : Proxy inutilisé
- `2/4` : Utilisation normale
- `4/4` : Capacité maximale atteinte

**Disponibilité** :
- 🟢 Uptime > 99%
- 🟡 Uptime 95-99%
- 🔴 Uptime < 95%

### Dashboard de monitoring

```
┌─────────────────────────────────────────────────┐
│ Proxy Principal                                 │
├─────────────────────────────────────────────────┤
│ Statut : 🟢 Opérationnel                        │
│ Utilisation : 3/4 comptes                       │
│ Latence : 45ms                                  │
│ Uptime : 99.8%                                  │
│                                                 │
│ Graphique de latence (24h)                      │
│ ─────────────────────────────                   │
│                                                 │
│ Comptes actifs :                                │
│ • MonCompte1 - Connecté depuis 2h15            │
│ • MonCompte2 - Connecté depuis 1h48            │
│ • MonCompte5 - Connecté depuis 0h32            │
└─────────────────────────────────────────────────┘
```

## Gestion des erreurs

### Proxy indisponible

**Symptômes** :
- Connection timeout
- Échecs répétés de connexion
- Latence > 1000ms

**Actions automatiques** :
1. Marquer le proxy comme hors ligne
2. Arrêter les tentatives de connexion
3. Rediriger les comptes vers d'autres proxies
4. Envoyer une notification

**Actions manuelles** :
1. Vérifier la configuration
2. Tester la connexion
3. Contacter le fournisseur si nécessaire
4. Désactiver temporairement

### Limite IP atteinte

**Alerte** :
```
⚠️ Limite IP atteinte
Proxy "Principal" : 4/4 comptes connectés
Impossible d'ajouter plus de comptes
```

**Solutions** :
1. Ajouter un nouveau proxy
2. Déconnecter un compte existant
3. Utiliser la rotation automatique

### Bannissement IP

Si une IP proxy est bannie :

**Détection** :
- Erreur "IP bannie" du serveur
- Échecs systématiques de connexion

**Réaction** :
1. Supprimer le proxy immédiatement
2. Ne plus l'utiliser (blacklist)
3. Contacter le fournisseur
4. Utiliser une nouvelle IP

## Fournisseurs de proxies

### Caractéristiques recommandées

Pour Dofus Touch, privilégiez :
- ✅ Proxies résidentiels (plus fiables)
- ✅ Faible latence (< 100ms)
- ✅ Haute disponibilité (> 99%)
- ✅ Support SOCKS5
- ✅ IPs non partagées

### Liste de vérification

Avant d'acheter des proxies :

- [ ] Vérifier la latence vers le serveur Dofus
- [ ] Tester la stabilité sur 24h
- [ ] Confirmer que les IPs ne sont pas blacklistées
- [ ] Vérifier le support client
- [ ] Lire les avis d'autres utilisateurs
- [ ] Tester avec un compte secondaire d'abord

## Sécurité et confidentialité

### Chiffrement

- 🔒 Connexions chiffrées (HTTPS/WSS)
- 🔑 Credentials stockés de manière sécurisée
- 🛡️ Pas de logs des données de jeu

### Bonnes pratiques

**✅ À faire** :
- Utiliser des proxies dédiés
- Changer régulièrement les proxies
- Surveiller les performances
- Garder des proxies de backup

**❌ À éviter** :
- Proxies gratuits/publics
- Proxies datacenter bon marché
- Partager vos proxies
- Négliger le monitoring

## Configuration avancée

### Proxies en cascade

Pour plus de sécurité, chaînez plusieurs proxies :

```
Vous → Proxy 1 → Proxy 2 → Serveur Dofus
```

**Configuration** :
```json
{
  "type": "chain",
  "proxies": [
    {
      "type": "SOCKS5",
      "host": "first-proxy.com",
      "port": 1080
    },
    {
      "type": "HTTP",
      "host": "second-proxy.com",
      "port": 8080
    }
  ]
}
```

**Note** : Augmente la latence, à utiliser avec précaution

### Géolocalisation

Utilisez des proxies dans la même région que le serveur :

```
Serveur France → Proxy France (latence minimale)
Serveur USA → Proxy USA (latence minimale)
```

---

**Prochaine section** : [Connexion des bots](bots.md) pour lancer vos automatisations.
