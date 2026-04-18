# Maurice Prisn Escape

Multiplayer web game voor het afscheid van Maurice Laval bij Prins Petfoods — 24 april 2026.

## Inhoud

- `index.html` — het volledige spel (HTML + CSS + JS in één bestand)

## Setup voor livegang

### 1. Supabase instellen

1. Maak een gratis account op [supabase.com](https://supabase.com)
2. Maak een nieuw project: `maurice-prisn-escape`
3. Ga naar **SQL Editor** en voer dit uit:

```sql
CREATE TABLE rooms (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  code TEXT UNIQUE NOT NULL,
  status TEXT DEFAULT 'waiting',
  current_block INTEGER DEFAULT 0,
  current_phase TEXT DEFAULT 'runner',
  created_at TIMESTAMP DEFAULT now(),
  started_at TIMESTAMP,
  finished_at TIMESTAMP
);

CREATE TABLE players (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  room_id UUID REFERENCES rooms(id),
  name TEXT NOT NULL,
  avatar TEXT NOT NULL,
  score INTEGER DEFAULT 0,
  joined_at TIMESTAMP DEFAULT now()
);

ALTER TABLE rooms ENABLE ROW LEVEL SECURITY;
ALTER TABLE players ENABLE ROW LEVEL SECURITY;
CREATE POLICY "allow all" ON rooms FOR ALL USING (true);
CREATE POLICY "allow all" ON players FOR ALL USING (true);
```

4. Schakel Realtime in: **Table Editor → rooms → Enable Realtime** en hetzelfde voor **players**
5. Ga naar **Project Settings → API** en kopieer:
   - Project URL
   - anon/public key

### 2. Credentials invullen in index.html

Zoek bovenaan het `<script>` blok:

```javascript
const SUPABASE_URL  = 'VUL_HIER_IN';
const SUPABASE_ANON = 'VUL_HIER_IN';
```

Vervang de waarden door jouw eigen URL en key.

### 3. Persoonlijke berichten aanpassen

Zoek het `MESSAGES` object en pas de berichten aan. De sleutels (namen) moeten exact overeenkomen met hoe spelers zich aanmelden.

### 4. GitHub + Netlify deployen

```bash
git init
git add index.html README.md
git commit -m "Initial release - Maurice Prisn Escape v1.0"
git branch -M main
git remote add origin https://github.com/[GEBRUIKERSNAAM]/maurice-prisn-escape.git
git push -u origin main
```

Netlify: **Add new site → Import from GitHub → selecteer repo**
- Build command: *(leeg)*
- Publish directory: *(leeg)*

Stel domeinnaam in: `mauriceprisnescape` → live op `https://deadmaus3911.github.io/Maurice-Prisn-Escape`

### 5. QR-code

Maak een QR-code voor: `https://deadmaus3911.github.io/Maurice-Prisn-Escape/?code=MAUS`

## Speluitleg

- 7 spelers joinen via QR-code
- 6 blokken: Runner (30s) → Trivia (2 vragen) → Match-3 (45s) → Tussenstand (4s)
- Host: druk 1,5 sec op het logo → wachtwoord `afscheid2026`
- Aan het einde krijgt elke speler een persoonlijk bericht

## Controlelijst voor 24 april (ochtend)

- [ ] Supabase credentials ingevuld
- [ ] Persoonlijke berichten bijgewerkt
- [ ] index.html gepusht naar GitHub
- [ ] Netlify deployment groen
- [ ] URL getest op eigen telefoon
- [ ] QR-code geprint en getest
