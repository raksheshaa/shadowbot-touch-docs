# Interface utilisateur

ShadowBot Touch propose une interface web moderne et intuitive pour gérer vos bots.

## Architecture de l'interface

L'interface est organisée en trois zones principales :

```
┌─────────────────────────────────────────────────┐
│  Barre supérieure (Header)                      │
├──────────┬──────────────────────────────────────┤
│          │                                      │
│  Sidebar │  Zone de contenu principale         │
│          │                                      │
│          │                                      │
└──────────┴──────────────────────────────────────┘
```

## 1. Barre supérieure (Header)

La barre supérieure affiche les informations globales et les actions rapides.

### Éléments affichés

**Zone gauche** :
- 🎯 Logo ShadowBot Touch
- Titre de la page actuelle

**Zone droite** :
- 🟢 Indicateur de statut (connecté/déconnecté)
- 📊 Compteur de bots actifs : `5/50`
- 👤 Menu utilisateur
- 🚪 Bouton de déconnexion

### Menu utilisateur

Cliquez sur l'icône utilisateur pour accéder à :
- ⚙️ Paramètres du compte
- 🔑 Changer la clé API
- 📖 Documentation
- ℹ️ À propos
- 🚪 Se déconnecter

## 2. Barre latérale (Sidebar)

Navigation principale de l'application.

### Structure de navigation

```
🏠 Accueil (Dashboard)
├── 📊 Vue d'ensemble
└── 📈 Statistiques

👤 Comptes
├── 📋 Liste des comptes
├── ➕ Ajouter un compte
└── 📁 Groupes de comptes

🌐 Proxies
├── 📋 Liste des proxies
├── ➕ Ajouter un proxy
└── 🔄 État des proxies

🤖 Bots
├── 📋 Bots actifs
├── ⏸️ Bots en pause
├── 🔴 Bots déconnectés
└── ➕ Nouveau bot

📊 Monitoring
├── 📈 Graphiques en temps réel
├── 📋 Logs système
└── 🔔 Alertes

⚙️ Paramètres
├── 🔧 Configuration
├── 🎨 Apparence
└── 🔐 Sécurité
```

### Navigation réactive

- **Clic simple** : Accéder à la page
- **Icône dépliante** : Afficher/masquer les sous-menus
- **Badge de notification** : Nombre d'alertes ou d'éléments

### États visuels

- **Page active** : Fond coloré + texte en gras
- **Survol** : Fond légèrement coloré
- **Sous-menu ouvert** : Indentation visible

## 3. Zone de contenu principale

Affiche le contenu dynamique selon la section sélectionnée.

### Page d'accueil (Dashboard)

#### Cartes de statistiques

```
┌──────────────┬──────────────┬──────────────┬──────────────┐
│ Bots actifs  │ Total        │ Comptes      │ Proxies      │
│    15        │    50        │    125       │    32        │
│ 🟢 +3        │              │ 🔒 Sécurisés │ 🟢 En ligne  │
└──────────────┴──────────────┴──────────────┴──────────────┘
```

**Informations par carte** :
- Valeur principale (grand format)
- Indicateur de tendance
- Statut ou détail supplémentaire

#### Graphique d'activité

Graphique en temps réel montrant :
- Nombre de bots connectés (ligne bleue)
- Utilisation CPU (ligne orange)
- Utilisation RAM (ligne verte)

**Période** : 1h / 6h / 24h / 7j (sélectionnable)

#### Liste des bots actifs

Tableau des 10 derniers bots connectés :

| Statut | Compte | Personnage | Serveur | Niveau | Uptime | Actions |
|--------|--------|------------|---------|--------|--------|---------|
| 🟢 | MonCompte1 | Guerrier | Hélios | 50 | 02:15:32 | ⏸️ 🛑 |
| 🟢 | MonCompte2 | Mage | Oshimo | 45 | 01:48:12 | ⏸️ 🛑 |

**Actions rapides** :
- ⏸️ Mettre en pause
- 🛑 Arrêter
- 📊 Voir les détails

### Page Comptes

#### Barre d'outils

```
[🔍 Rechercher...] [🏷️ Filtrer] [👥 Grouper] [+ Ajouter]
```

**Fonctionnalités** :
- **Recherche** : Par nom, serveur, niveau
- **Filtres** : Serveur, statut, proxy
- **Regroupement** : Par serveur, par proxy, personnalisé
- **Actions en masse** : Sélectionner plusieurs comptes

#### Vue en grille

```
┌────────────────┐ ┌────────────────┐ ┌────────────────┐
│ MonCompte1     │ │ MonCompte2     │ │ MonCompte3     │
│ 🟢 Connecté    │ │ 🔴 Déconnecté  │ │ 🟡 En pause    │
│ Serveur: Hélios│ │ Serveur: Oshimo│ │ Serveur: Terra │
│ Niveau: 50     │ │ Niveau: 45     │ │ Niveau: 38     │
│ ⚙️ 🗑️          │ │ ⚙️ 🗑️          │ │ ⚙️ 🗑️          │
└────────────────┘ └────────────────┘ └────────────────┘
```

**Indicateurs** :
- 🟢 Connecté actuellement
- 🔴 Déconnecté
- 🟡 Bot en pause
- 🌐 Utilise un proxy

#### Vue en liste

Tableau détaillé avec colonnes :
- Sélection (checkbox)
- Statut
- Nom du compte
- Serveur
- Niveau
- Proxy associé
- Dernière connexion
- Actions

**Actions individuelles** :
- ⚙️ Modifier
- 🗑️ Supprimer
- 🔗 Affecter un proxy
- 📊 Statistiques

### Page Proxies

#### Tableau des proxies

| Statut | Description | Type | Hôte:Port | Comptes | Latence | Actions |
|--------|-------------|------|-----------|---------|---------|---------|
| 🟢 | Proxy Principal | SOCKS5 | 192.168.1.100:8080 | 3/4 | 45ms | 🧪 ⚙️ 🗑️ |
| 🟢 | Proxy Backup | HTTP | proxy.example.com:3128 | 1/4 | 120ms | 🧪 ⚙️ 🗑️ |
| 🔴 | Proxy Test | SOCKS5 | 10.0.0.5:1080 | 0/4 | Timeout | 🧪 ⚙️ 🗑️ |

**Légende des statuts** :
- 🟢 Opérationnel
- 🟡 Latence élevée (>500ms)
- 🔴 Hors ligne / Erreur

**Indicateur de capacité** :
- `3/4` = 3 comptes utilisés sur 4 maximum
- ⚠️ S'affiche en orange si proche de la limite

**Actions** :
- 🧪 Tester la connexion
- ⚙️ Modifier
- 🗑️ Supprimer

#### Détails d'un proxy

Cliquez sur une ligne pour voir les détails étendus :

```
┌─────────────────────────────────────────┐
│ Proxy Principal                         │
├─────────────────────────────────────────┤
│ Type: SOCKS5                            │
│ Hôte: 192.168.1.100                     │
│ Port: 8080                              │
│ Authentification: Oui                   │
│ Statut: 🟢 Opérationnel                 │
│                                         │
│ Comptes utilisant ce proxy:             │
│ • MonCompte1 (Hélios) - 🟢 Connecté     │
│ • MonCompte2 (Oshimo) - 🔴 Déconnecté   │
│ • MonCompte5 (Terra) - 🟢 Connecté      │
│                                         │
│ Statistiques:                           │
│ • Latence moyenne: 45ms                 │
│ • Uptime: 99.8%                         │
│ • Bande passante: 2.3 MB/s              │
└─────────────────────────────────────────┘
```

### Page Bots

#### Filtres rapides

```
[Tous (50)] [🟢 Actifs (15)] [🟡 Pause (5)] [🔴 Déconnectés (30)]
```

Cliquez pour filtrer instantanément.

#### Cartes de bots

Vue détaillée de chaque bot :

```
┌─────────────────────────────────────────────────┐
│ 🟢 MonCompte1 - Guerrier Niveau 50              │
├─────────────────────────────────────────────────┤
│ Serveur: Hélios                                 │
│ Position: [5,2] Forêt d'Astrub                  │
│ Temps de connexion: 02:15:32                    │
│                                                  │
│ ┌───────────────────────────────────┐           │
│ │ Activité récente:                 │           │
│ │ • 14:32 - Récolte de bois (x15)   │           │
│ │ • 14:35 - Déplacement [5,2]       │           │
│ │ • 14:37 - Combat vs Bouftou       │           │
│ └───────────────────────────────────┘           │
│                                                  │
│ [⏸️ Pause] [🛑 Arrêter] [📊 Détails]           │
└─────────────────────────────────────────────────┘
```

**Informations en temps réel** :
- Statut de connexion
- Position sur la carte
- Dernières actions effectuées
- Temps de connexion actif

### Page Monitoring

#### Graphiques de performance

**Graphique 1 : Utilisation des ressources**
- CPU (%)
- RAM (GB)
- Réseau (MB/s)

**Graphique 2 : Activité des bots**
- Connexions par heure
- Actions effectuées
- Erreurs rencontrées

#### Console de logs

```
┌─────────────────────────────────────────────────┐
│ 🔍 Filtrer les logs... [Niveau: Tous ▼]         │
├─────────────────────────────────────────────────┤
│ 14:35:42 [INFO] MonCompte1 - Connexion réussie  │
│ 14:35:45 [DEBUG] MonCompte1 - Chargement carte  │
│ 14:35:50 [WARN] MonCompte2 - Latence élevée     │
│ 14:36:02 [ERROR] MonCompte3 - Échec connexion   │
│ 14:36:10 [INFO] MonCompte1 - Action: Récolte    │
└─────────────────────────────────────────────────┘
                              [📥 Exporter] [🗑️ Vider]
```

**Niveaux de logs** :
- `[DEBUG]` - Gris - Informations détaillées
- `[INFO]` - Bleu - Informations normales
- `[WARN]` - Orange - Avertissements
- `[ERROR]` - Rouge - Erreurs

**Actions** :
- Filtrer par niveau
- Rechercher dans les logs
- Exporter en fichier .txt ou .json
- Vider les logs affichés

## Thèmes et personnalisation

### Thèmes disponibles

- **Clair** : Fond blanc, adapté au jour
- **Sombre** : Fond noir, confort visuel
- **Auto** : Suit les préférences système

**Changer de thème** :
Paramètres → Apparence → Thème

### Personnalisation des couleurs

Vous pouvez personnaliser :
- Couleur d'accentuation
- Taille de la police
- Densité de l'interface (compact / normal / spacieux)

## Notifications

### Types de notifications

**Toast (coin supérieur droit)** :
```
┌──────────────────────────────┐
│ ✅ Compte ajouté avec succès │
└──────────────────────────────┘
```

Disparaît automatiquement après 3-5 secondes.

**Alertes importantes** :
```
┌─────────────────────────────────────┐
│ ⚠️ Attention                        │
│ 4 comptes connectés sur cette IP    │
│ Limite atteinte                     │
│ [OK] [Voir les détails]             │
└─────────────────────────────────────┘
```

Requiert une action de l'utilisateur.

### Centre de notifications

Badge sur l'icône 🔔 : Nombre de notifications non lues

Cliquez pour voir :
- Alertes système
- Mises à jour disponibles
- Événements importants des bots

## Raccourcis et astuces

### Raccourcis globaux

| Touche | Action |
|--------|--------|
| `?` | Afficher l'aide |
| `/` | Focus sur la recherche |
| `Échap` | Fermer les modales |
| `Alt + 1-9` | Accès rapide aux sections |

### Astuces d'interface

**Double-clic** sur une carte de bot → Ouvrir les détails

**Clic droit** sur un compte → Menu contextuel rapide

**Glisser-déposer** un compte sur un proxy → Association automatique

**Ctrl + Clic** sur plusieurs comptes → Sélection multiple

## Responsive Design

L'interface s'adapte à toutes les tailles d'écran :

**Desktop (>1200px)** :
- Sidebar toujours visible
- Vue complète en grille

**Tablet (768-1200px)** :
- Sidebar repliable
- Vue en grille réduite

**Mobile (<768px)** :
- Navigation par menu hamburger
- Vue en liste uniquement
- Cartes empilées

---

**Prochaine section** : [Gestion des comptes](accounts.md) pour apprendre à organiser efficacement vos comptes.
