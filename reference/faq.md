# FAQ - Questions fréquentes

Réponses aux questions courantes sur ShadowBot Touch.

## Installation

**Q: Node.js version recommandée ?**
R: Node.js 16.x ou supérieur. La v18 LTS est idéale.

**Q: L'installation échoue sur Windows ?**
R: C'est pourquoi nous utilisons sql.js (pure JS) au lieu de better-sqlite3 qui nécessite une compilation native.

**Q: Puis-je utiliser Docker ?**
R: Oui, un Dockerfile est fourni. Voir [Installation](../getting-started/installation.md).

## Configuration

**Q: Comment générer une clé API sécurisée ?**
R: Utilisez : `node -e "console.log(require('crypto').randomBytes(32).toString('hex'))"`

**Q: Le port 3000 est déjà utilisé ?**
R: Changez-le dans `config.json` ou via `SHADOWBOT_PORT=8080`

**Q: Dois-je utiliser des proxies ?**
R: Si vous avez plus de 4 comptes, OUI obligatoirement.

## Comptes et Proxies

**Q: Combien de comptes par proxy ?**
R: **Maximum 4**, c'est une limite serveur stricte.

**Q: Les proxies gratuits fonctionnent-ils ?**
R: Non recommandé. Utilisez des proxies payants et fiables.

**Q: Un compte peut-il changer de proxy ?**
R: Oui, mais le bot doit se reconnecter.

**Q: Mes mots de passe sont-ils en sécurité ?**
R: Oui, chiffrés AES-256 dans la base de données.

## Bots

**Q: Combien de bots puis-je lancer ?**
R: Dépend de votre RAM. ~100 MB par bot. Voir [Limites](limits.md).

**Q: Le bot se déconnecte souvent ?**
R: Vérifiez :
- Qualité du proxy
- Stabilité réseau
- Auto-reconnexion activée
- Logs pour identifier la cause

**Q: Puis-je contrôler manuellement un bot ?**
R: ShadowBot est automatique. Pour contrôle manuel, utilisez le client officiel.

**Q: Les bots sont-ils détectables ?**
R: Sur serveur privé, généralement non. Sur serveurs officiels, c'est interdit.

## Performances

**Q: L'interface est lente avec 30+ bots ?**
R: Normal. Solutions :
- Augmenter RAM
- Réduire fréquence mise à jour
- Désactiver logs DEBUG

**Q: Utilisation CPU élevée ?**
R: Limitez le nombre de bots ou vérifiez les boucles infinies dans les logs.

## Erreurs courantes

**Q: "Identifiants invalides" ?**
R: Vérifiez username/password dans la gestion des comptes.

**Q: "Limite IP atteinte" ?**
R: Plus de 4 comptes sur une IP. Ajoutez un proxy.

**Q: "Proxy timeout" ?**
R: Proxy hors ligne ou trop lent. Testez le proxy.

**Q: Base de données corrompue ?**
R: Restaurez depuis une sauvegarde automatique dans `data/backups/`.

## Sécurité

**Q: Puis-je utiliser ShadowBot sur serveurs officiels ?**
R: **NON**. C'est strictement interdit et entraîne un ban permanent.

**Q: Les logs contiennent-ils des mots de passe ?**
R: Non, jamais. Les credentials sont masqués.

**Q: Puis-je partager ma clé API ?**
R: Non, elle donne accès complet à votre instance.

## Fonctionnalités

**Q: Puis-je ajouter des scripts personnalisés ?**
R: Oui, voir [Développement](../development/structure.md).

**Q: Support multi-langues ?**
R: Actuellement français uniquement. Contributions bienvenues.

**Q: Notifications mobiles ?**
R: Pas encore. Webhooks Discord disponibles.

## Contribution

**Q: Comment contribuer au projet ?**
R: Voir [Guide de contribution](../development/contributing.md).

**Q: Où signaler un bug ?**
R: GitHub Issues ou Discord.

**Q: Puis-je proposer une fonctionnalité ?**
R: Oui, créez une issue GitHub avec le tag "feature request".

---

**Prochaine section**: [Dépannage](troubleshooting.md)
