# Guide d'utilisation de la documentation

Cette documentation GitBook pour ShadowBot Touch est prête à l'emploi.

## 📁 Structure des fichiers

```
shadowbot-docs/
├── README.md                    # Page d'accueil
├── SUMMARY.md                   # Table des matières GitBook
├── .gitbook.yaml               # Configuration GitBook
├── getting-started/            # Guide de démarrage
│   ├── installation.md
│   ├── configuration.md
│   └── quickstart.md
├── guide/                      # Guide d'utilisation
│   ├── interface.md
│   ├── accounts.md
│   ├── proxies.md
│   ├── bots.md
│   └── monitoring.md
├── technical/                  # Documentation technique
│   ├── overview.md
│   ├── database.md
│   ├── network-protocols.md
│   ├── authentication.md
│   └── connections.md
├── development/                # Guide développeurs
│   ├── structure.md
│   ├── api.md
│   └── contributing.md
├── reference/                  # Référence
│   ├── configuration.md
│   ├── limits.md
│   ├── faq.md
│   └── troubleshooting.md
└── appendix/                   # Annexes
    ├── glossary.md
    └── changelog.md
```

## 🚀 Publication sur GitBook

### Option 1 : Via GitHub (recommandé)

1. **Créer un repository GitHub**
   ```bash
   cd shadowbot-docs
   git init
   git add .
   git commit -m "Documentation ShadowBot Touch"
   git remote add origin https://github.com/votre-username/shadowbot-docs.git
   git push -u origin main
   ```

2. **Connecter à GitBook**
   - Allez sur [gitbook.com](https://www.gitbook.com)
   - Créez un compte / Connectez-vous
   - Cliquez sur "New Space"
   - Sélectionnez "Import from GitHub"
   - Autorisez GitBook à accéder à votre repository
   - Sélectionnez votre repository
   - GitBook synchronisera automatiquement !

3. **Configuration automatique**
   - GitBook détectera `SUMMARY.md` et `.gitbook.yaml`
   - La documentation sera immédiatement disponible
   - Chaque push sur GitHub mettra à jour GitBook

### Option 2 : Import manuel

1. Sur GitBook, créez un nouvel espace
2. Allez dans Settings → Import/Export
3. Uploadez tous les fichiers .md
4. GitBook organisera selon SUMMARY.md

## 📖 Test en local

### Avec GitBook CLI (legacy)

```bash
# Installer GitBook CLI
npm install -g gitbook-cli

# Dans le dossier de documentation
cd shadowbot-docs

# Installer les dépendances GitBook
gitbook install

# Lancer le serveur de preview
gitbook serve

# Ouvrir http://localhost:4000
```

### Avec un viewer Markdown

Vous pouvez aussi utiliser n'importe quel viewer Markdown :
- VS Code avec extension Markdown Preview
- Typora
- Mark Text
- Obsidian

## ✏️ Personnalisation

### Modifier le contenu

Éditez simplement les fichiers .md avec votre éditeur préféré :

```markdown
# Titre

Votre contenu en Markdown...

## Sous-titre

- Liste à puces
- Autre item

```code```
```

### Ajouter une page

1. Créez le fichier .md dans le dossier approprié
2. Ajoutez une entrée dans `SUMMARY.md` :

```markdown
* [Nouvelle page](chemin/vers/page.md)
```

### Modifier l'organisation

Éditez `SUMMARY.md` pour réorganiser les sections.

## 🎨 Thèmes GitBook

Une fois publié sur GitBook :
- Choisissez un thème dans les paramètres
- Personnalisez les couleurs
- Ajoutez votre logo
- Configurez le domaine personnalisé

## 📊 Statistiques

Cette documentation contient :
- **24 fichiers Markdown**
- **~15,000 mots**
- **8 sections principales**
- **Exemples de code**
- **Illustrations textuelles**

## 🔄 Mise à jour

Pour mettre à jour la documentation :

1. Éditez les fichiers .md
2. Commit et push vers GitHub
3. GitBook se met à jour automatiquement

Ou directement dans l'éditeur GitBook en ligne.

## 💡 Conseils

- Utilisez les liens relatifs entre pages : `[texte](../autre/page.md)`
- Ajoutez des images dans un dossier `assets/`
- Gardez une structure cohérente
- Mettez à jour le Changelog pour chaque version

## 📞 Support

Pour toute question sur la documentation :
- Issues GitHub
- Discord ShadowBot
- Email contact

---

Bonne documentation ! 📚
