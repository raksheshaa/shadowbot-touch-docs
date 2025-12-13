# Base de données

Structure et gestion des données avec SQLite/sql.js.

## Choix de sql.js

**Pourquoi sql.js** (et pas better-sqlite3):
- ✅ Pure JavaScript (pas de compilation native)
- ✅ Fonctionne sur Windows sans problème  
- ✅ Portable et léger
- ✅ API similaire à SQLite standard

```javascript
import initSqlJs from 'sql.js';
const SQL = await initSqlJs();
const db = new SQL.Database();
```

## Schéma de base de données

### Table: accounts

```sql
CREATE TABLE accounts (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  username TEXT NOT NULL UNIQUE,
  password TEXT NOT NULL,  -- Chiffré AES-256
  server TEXT NOT NULL,
  proxy_id INTEGER,
  notes TEXT,
  created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
  updated_at DATETIME DEFAULT CURRENT_TIMESTAMP,
  FOREIGN KEY (proxy_id) REFERENCES proxies(id)
);
```

### Table: proxies

```sql
CREATE TABLE proxies (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  description TEXT NOT NULL,
  type TEXT NOT NULL,  -- 'HTTP', 'HTTPS', 'SOCKS4', 'SOCKS5'
  host TEXT NOT NULL,
  port INTEGER NOT NULL,
  username TEXT,
  password TEXT,  -- Chiffré
  active_connections INTEGER DEFAULT 0,
  created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
  CHECK (type IN ('HTTP', 'HTTPS', 'SOCKS4', 'SOCKS5')),
  CHECK (port BETWEEN 1 AND 65535)
);
```

### Table: bots

```sql
CREATE TABLE bots (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  account_id INTEGER NOT NULL,
  status TEXT DEFAULT 'created',
  mode TEXT DEFAULT 'farm',
  config TEXT,  -- JSON configuration
  created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
  last_connected_at DATETIME,
  FOREIGN KEY (account_id) REFERENCES accounts(id) ON DELETE CASCADE
);
```

### Table: sessions

```sql
CREATE TABLE sessions (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  bot_id INTEGER NOT NULL,
  start_time DATETIME NOT NULL,
  end_time DATETIME,
  resources_gathered INTEGER DEFAULT 0,
  kamas_earned INTEGER DEFAULT 0,
  combats_won INTEGER DEFAULT 0,
  combats_lost INTEGER DEFAULT 0,
  FOREIGN KEY (bot_id) REFERENCES bots(id) ON DELETE CASCADE
);
```

## Chiffrement des données

```javascript
const crypto = require('crypto');

function encrypt(text, key) {
  const iv = crypto.randomBytes(16);
  const cipher = crypto.createCipheriv('aes-256-cbc', Buffer.from(key), iv);
  let encrypted = cipher.update(text);
  encrypted = Buffer.concat([encrypted, cipher.final()]);
  return iv.toString('hex') + ':' + encrypted.toString('hex');
}

function decrypt(text, key) {
  const parts = text.split(':');
  const iv = Buffer.from(parts[0], 'hex');
  const encrypted = Buffer.from(parts[1], 'hex');
  const decipher = crypto.createDecipheriv('aes-256-cbc', Buffer.from(key), iv);
  let decrypted = decipher.update(encrypted);
  decrypted = Buffer.concat([decrypted, decipher.final()]);
  return decrypted.toString();
}
```

## Sauvegarde et restauration

```javascript
// Sauvegarde
const data = db.export();
const buffer = Buffer.from(data);
fs.writeFileSync('data/shadowbot.db', buffer);

// Restauration
const buffer = fs.readFileSync('data/shadowbot.db');
const db = new SQL.Database(buffer);
```

---

**Prochaine section**: [Protocoles réseau](network-protocols.md)
