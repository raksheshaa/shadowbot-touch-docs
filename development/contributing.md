# Contribuer

Guide pour contribuer à ShadowBot Touch.

## Prérequis

- Node.js 16+
- Git
- Connaissance de JavaScript/React
- (Optionnel) Expérience avec Dofus Touch

## Setup développement

```bash
# Fork et clone
git clone https://github.com/votre-fork/shadowbot-touch.git
cd shadowbot-touch

# Installer dépendances
npm install

# Créer une branche
git checkout -b feature/ma-nouvelle-fonctionnalite

# Lancer en mode dev
npm run dev
```

## Guidelines

### Code

- Suivre les conventions du projet
- Écrire des tests pour les nouvelles fonctionnalités
- Commenter le code complexe
- Respecter ESLint et Prettier

### Commits

Format des messages:
```
type(scope): description courte

Description longue (optionnelle)

Refs: #issue-number
```

Types:
- `feat`: Nouvelle fonctionnalité
- `fix`: Correction de bug
- `docs`: Documentation
- `style`: Formatage
- `refactor`: Refactoring
- `test`: Tests
- `chore`: Maintenance

Exemple:
```
feat(bots): ajouter support du mode PvP

- Implémente stratégie de combat
- Ajoute sélection des cibles
- Configure fuite conditionnelle

Refs: #42
```

### Pull Requests

1. Créer une issue avant de coder
2. Garder les PR focalisées (une fonctionnalité = une PR)
3. Ajouter des tests
4. Mettre à jour la documentation
5. Demander une review

Template PR:
```markdown
## Description
Brève description des changements

## Type de changement
- [ ] Bug fix
- [ ] Nouvelle fonctionnalité
- [ ] Breaking change
- [ ] Documentation

## Tests
- [ ] Tests unitaires ajoutés
- [ ] Tests d'intégration
- [ ] Testé manuellement

## Checklist
- [ ] Code respecte les conventions
- [ ] Documentation mise à jour
- [ ] Pas de warning ESLint
- [ ] Testé en local
```

## Tests

```bash
# Lancer tous les tests
npm test

# Tests unitaires
npm run test:unit

# Tests d'intégration
npm run test:integration

# Coverage
npm run test:coverage
```

## Priorités actuelles

- [ ] Améliorer la stabilité des connexions
- [ ] Optimiser les performances (RAM/CPU)
- [ ] Ajouter plus de modes de bot
- [ ] Améliorer l'interface utilisateur
- [ ] Documentation des protocoles réseau

## Questions?

- Discord: [lien]
- Issues GitHub: [lien]
- Email: [contact]

Merci de contribuer à ShadowBot Touch! 🙏
