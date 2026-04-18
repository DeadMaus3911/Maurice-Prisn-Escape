# Reset handleiding — tussen testruns en na gebruik

## Snel resetten (via Claude Code)
Zeg tegen Claude: **"reset de MAUS room"**
Claude doet de rest automatisch.

## Handmatig resetten (Supabase dashboard)
1. Ga naar supabase.com → project **PRISN**
2. Klik **SQL Editor** in het linkermenu
3. Plak dit en klik **Run**:

```sql
-- Reset de room naar beginstand
UPDATE rooms
SET status = 'waiting',
    current_block = 0,
    current_phase = 'runner',
    started_at = NULL,
    finished_at = NULL
WHERE code = 'MAUS';

-- Verwijder alle testspelers
DELETE FROM players
WHERE room_id IN (
  SELECT id FROM rooms WHERE code = 'MAUS'
);
```

## Wat dit doet
- Room status → `waiting` (spelers kunnen weer joinen)
- Blok en fase → terug naar begin (blok 0, runner)
- Alle spelers uit vorige sessie verwijderd
- Scores gereset

## Wanneer resetten?
- Na elke testrun
- Op de ochtend van 24 april (vóór het echte spel)
- Als iemand per ongeluk "Finaliseer" heeft gedrukt

## Berichten aanpassen
Open `index.html` → zoek op `const MESSAGES` → pas namen/teksten aan → sla op → push naar GitHub (Netlify herdeployt automatisch binnen 1 minuut).

Naam in MESSAGES moet EXACT overeenkomen met de naam die de speler invult bij "Doe mee".

## URL's
- **Spel**: https://mauriceprisnescape.netlify.app/?code=MAUS
- **Netlify dashboard**: https://app.netlify.com/projects/mauriceprisnescape
- **GitHub repo**: https://github.com/DeadMaus3911/Maurice-Prisn-Escape
- **Supabase**: https://supabase.com/dashboard/project/hxouixcbspmqcizoavdr
