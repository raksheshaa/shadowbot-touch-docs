# Gestion des comptes

Gérez efficacement vos comptes Dofus Touch avec ShadowBot Touch.

## Ajouter un compte

### Via l'interface

1. **Accédez à la section Comptes**
2. **Cliquez sur "+ Ajouter un compte"**
3. **Remplissez le formulaire** :

```
┌─────────────────────────────────────┐
│ Ajouter un compte                   │
├─────────────────────────────────────┤
│ Nom d'utilisateur *                 │
│ [votre_login_ankama]                │
│                                     │
│ Mot de passe *                      │
│ [••••••••••••••]                    │
│                                     │
│ Serveur *                           │
│ [Sélectionner... ▼]                 │
│                                     │
│ Proxy (optionnel)                   │
│ [Aucun ▼]                           │
│                                     │
│ Notes (optionnel)                   │
│ [Description du compte]             │
│                                     │
│     [Annuler]  [Enregistrer]        │
└─────────────────────────────────────┘
```

4. **Cliquez sur Enregistrer**

### Via import CSV

Pour ajouter plusieurs comptes rapidement :

1. **Créez un fichier CSV** :

```csv
username,password,server,proxy,notes
compte1@ankama.com,password123,Hélios,proxy1,Compte principal
compte2@ankama.com,password456,Oshimo,proxy1,Alt farm
compte3@ankama.com,password789,Terra,proxy2,Compte PvP
```

2. **Importez le fichier** :
   - Comptes → Import → Sélectionner le fichier CSV
   - Vérifiez l'aperçu
   - Validez l'import

## Modifier un compte

### Informations modifiables

Vous pouvez modifier :
- ✅ Mot de passe
- ✅ Serveur
- ✅ Proxy associé
- ✅ Notes

> ⚠️ Le nom d'utilisateur ne peut pas être modifié (créez un nouveau compte)

### Procédure

1. Cliquez sur l'icône ⚙️ du compte
2. Modifiez les champs souhaités
3. Cliquez sur "Enregistrer"

## Organiser les comptes

### Groupes de comptes

Créez des groupes pour organiser vos comptes :

```
📁 Mes comptes
├── 👤 Comptes principaux (5)
│   ├── MonMain1
│   ├── MonMain2
│   └── ...
├── 🌾 Farm automatique (15)
│   ├── FarmBot1
│   ├── FarmBot2
│   └── ...
└── ⚔️ PvP (8)
    ├── PvPBot1
    └── ...
```

**Créer un groupe** :
1. Comptes → Groupes → "+ Nouveau groupe"
2. Nommez le groupe
3. Glissez-déposez les comptes dans le groupe

**Avantages** :
- Organisation claire
- Actions en masse par groupe
- Filtrage rapide

### Tags et labels

Ajoutez des tags pour catégoriser :

```
Compte: MonMain1
Tags: #principal #hélios #tank #level50+
```

**Filtrer par tags** :
- Utilisez la barre de recherche
- Syntaxe : `#tag1 #tag2`
- Exemple : `#farm #oshimo` affiche tous les comptes farm sur Oshimo

## Gestion des proxies par compte

### Règles d'association

**Règle 1** : Maximum 4 comptes par proxy
- ⚠️ Limite serveur stricte
- Bannissement automatique si dépassement

**Règle 2** : Distribution intelligente
- ShadowBot répartit automatiquement
- Évite la surcharge d'un proxy

### Assigner un proxy

**Méthode 1 - Manuelle** :
1. Modifier le compte
2. Sélectionner le proxy dans la liste
3. Enregistrer

**Méthode 2 - Glisser-déposer** :
1. Glissez le compte sur la carte proxy
2. Confirmation automatique

**Méthode 3 - Automatique** :
1. Sélectionnez plusieurs comptes
2. Actions en masse → "Assigner des proxies"
3. Distribution automatique optimale

### Vérifier l'attribution

Vue "Proxies" → Voir quels comptes utilisent quel proxy :

```
Proxy Principal (3/4)
├── MonCompte1 - 🟢 Connecté
├── MonCompte2 - 🔴 Déconnecté
└── MonCompte5 - 🟢 Connecté
```

## Sécurité des comptes

### Chiffrement des mots de passe

- 🔒 Chiffrement AES-256 dans la base de données
- 🔑 Clé unique par installation
- 🛡️ Jamais stockés en clair

### Bonnes pratiques

**✅ À faire** :
- Utiliser des mots de passe uniques par compte
- Changer régulièrement les mots de passe
- Activer l'authentification 2FA Ankama (si disponible)
- Sauvegarder régulièrement la base de données

**❌ À éviter** :
- Réutiliser le même mot de passe partout
- Partager vos identifiants
- Exporter les comptes sans chiffrement
- Négliger les sauvegardes

## Actions en masse

Sélectionnez plusieurs comptes pour effectuer des actions groupées.

### Sélection

**Méthode 1 - Cases à cocher** :
- Cochez les comptes un par un

**Méthode 2 - Sélection par filtre** :
- Filtrez d'abord (serveur, tag, groupe)
- "Tout sélectionner" dans les résultats

**Méthode 3 - Raccourci** :
- `Ctrl + A` : Tout sélectionner
- `Ctrl + Clic` : Sélection multiple

### Actions disponibles

Avec plusieurs comptes sélectionnés :

- 🌐 **Assigner des proxies** - Distribution automatique
- 🗑️ **Supprimer** - Suppression groupée (avec confirmation)
- 📁 **Déplacer vers un groupe** - Organisation
- 🏷️ **Ajouter des tags** - Étiquetage en masse
- 📤 **Exporter** - Export CSV/JSON
- 🔄 **Changer de serveur** - Migration groupée

## Export et import

### Exporter des comptes

**Format CSV** :
```csv
username,server,proxy,notes,created_at
compte1@ankama.com,Hélios,proxy1,Main,2024-01-15
compte2@ankama.com,Oshimo,proxy1,Alt,2024-01-16
```

**Format JSON** :
```json
[
  {
    "username": "compte1@ankama.com",
    "server": "Hélios",
    "proxy": "proxy1",
    "notes": "Main",
    "created_at": "2024-01-15"
  }
]
```

> ⚠️ **Sécurité** : Les exports ne contiennent **JAMAIS** les mots de passe

### Importer des comptes

1. Comptes → Import
2. Sélectionnez le fichier (CSV ou JSON)
3. Mappez les colonnes si nécessaire
4. Prévisualisez les données
5. Validez l'import

**Options d'import** :
- ☑️ Ignorer les doublons
- ☑️ Mettre à jour les comptes existants
- ☑️ Assigner automatiquement des proxies

## Statistiques par compte

Chaque compte dispose de statistiques détaillées.

### Informations de connexion

```
┌─────────────────────────────────────┐
│ MonCompte1                          │
├─────────────────────────────────────┤
│ Première connexion: 15/01/2024      │
│ Dernière connexion: 14/12/2024      │
│ Temps total connecté: 157h 32m      │
│ Nombre de connexions: 342           │
│ Taux de réussite: 98.5%             │
└─────────────────────────────────────┘
```

### Activité du compte

- 📊 Graphique d'activité (connexions/jour)
- 📈 Évolution du niveau
- ⚡ Actions effectuées
- 💰 Kamas gagnés (si trackés)

### Historique

Logs des 100 dernières actions :

```
14/12/2024 14:35 - Connexion réussie (Hélios)
14/12/2024 12:22 - Déconnexion normale
14/12/2024 10:15 - Connexion réussie (Hélios)
13/12/2024 20:45 - Erreur de connexion (Timeout)
```

## Gestion des serveurs

### Serveurs disponibles

Liste des serveurs Dofus Touch supportés :
- Hélios
- Oshimo
- Terra
- Dodge
- Brutas
- Grandapan

### Changer de serveur

1. Modifier le compte
2. Sélectionner le nouveau serveur
3. Enregistrer

> ℹ️ Le changement est immédiat, mais le bot doit se reconnecter

### Distribution par serveur

Vue globale de la répartition :

```
┌──────────────┬─────────┐
│ Serveur      │ Comptes │
├──────────────┼─────────┤
│ Hélios       │    45   │
│ Oshimo       │    32   │
│ Terra        │    28   │
│ Dodge        │    15   │
│ Brutas       │     5   │
└──────────────┴─────────┘
```

## Suppression de comptes

### Supprimer un compte

1. Cliquez sur l'icône 🗑️
2. Confirmez la suppression
3. Le compte est définitivement supprimé

> ⚠️ **Irréversible** : Assurez-vous d'avoir une sauvegarde

### Suppression en masse

1. Sélectionnez plusieurs comptes
2. Actions → Supprimer
3. Confirmez (liste affichée)
4. Suppression groupée

### Récupération

Si sauvegarde activée :
1. Paramètres → Base de données → Restaurer
2. Sélectionnez une sauvegarde antérieure
3. Les comptes supprimés sont restaurés

## Dépannage

### "Identifiants invalides"

**Causes** :
- Mot de passe incorrect
- Compte banni
- Serveur en maintenance

**Solution** :
1. Vérifiez les identifiants
2. Testez la connexion manuellement
3. Contactez le support serveur

### Compte ne se connecte pas

**Checklist** :
- [ ] Identifiants corrects
- [ ] Serveur en ligne
- [ ] Proxy fonctionnel (si utilisé)
- [ ] Limite IP non atteinte (4 max)
- [ ] Pare-feu autorise la connexion

### Perte de mot de passe

Le mot de passe est chiffré et **non récupérable**.

**Solution** :
1. Modifiez le compte
2. Entrez le nouveau mot de passe
3. Enregistrez

---

**Prochaine section** : [Gestion des proxies](proxies.md) pour optimiser vos connexions multi-comptes.
