# Checklist 24 april — Maurice Prisn Escape

## 's Ochtends (voor aanvang)

### Supabase reset
- [ ] Ga naar supabase.com → project PRISN → SQL Editor
- [ ] Voer uit:
```sql
UPDATE rooms SET status='waiting', current_block=0, current_phase='runner', started_at=NULL, finished_at=NULL WHERE code='MAUS';
DELETE FROM players WHERE room_id IN (SELECT id FROM rooms WHERE code='MAUS');
```
- [ ] Of vraag Claude Code om het te doen ("reset de MAUS room")

### Netlify / game
- [ ] Open https://mauriceprisnescape.netlify.app/?code=MAUS op je eigen telefoon
- [ ] Vul een testnaam in, klik Doe mee → lobby laadt ✓
- [ ] Druk 1,5 sec op het logo → wachtwoord `afscheid2026` → host-dashboard laadt ✓
- [ ] Reset daarna de room opnieuw (zie boven)

### QR-code
- [ ] Maak QR-code via qr-code-generator.com voor:
  `https://mauriceprisnescape.netlify.app/?code=MAUS`
- [ ] Print op A4 of toon op laptop/scherm
- [ ] Test QR op een andere telefoon

### Wifi / netwerk
- [ ] Check wifi op locatie — alle 7 telefoons verbonden
- [ ] Of: iedereen op 4G (geen wifi nodig, Supabase is cloud)

### Berichten
- [ ] Open index.html → zoek op `MESSAGES` → controleer alle namen exact
- [ ] Namen moeten EXACT overeenkomen met hoe spelers zich aanmelden
- [ ] Sla op + push naar GitHub zodat Netlify herdeployt

---

## Tijdens het spel

### Jij als host (Maurice)
1. Laat iedereen joinen via QR-code
2. Druk 1,5 sec op logo in lobby → `afscheid2026` → host-dashboard
3. Controleer: "X van 7 aanwezig"
4. Klik **Start het spel** → iedereen ziet intro → blok 1 start

### Tijdens elke ronde
- Paars 🎮 knopje rechtsonder = jouw host-knop
- Tik erop voor de quizmaster-view
- "Sla ronde over" als iemand problemen heeft
- "Finaliseer" na blok 6 of als je wilt stoppen

### Trivia antwoorden (voor de quizmaster)
| # | Vraag | Antwoord |
|---|-------|----------|
| 1 | Hoeveel jaar bij Prins? | **5,5 jaar** |
| 2 | Wie in CCT-team bij start? | **Martijn, Robert, Elsemieke, Bas, Pieter en Laura** |
| 3 | Welk bedrijfsuitje meegeweest? | **Kwintelooijen House of Bird** |
| 4 | Blikjes in Toonbank display? | **42** |
| 5 | Teams profielfoto? | **Gele trui, scheidingswanden** |
| 6 | Hoeveel collega's vertrokken? | **Minimaal 12** |
| 7 | Slechtste kersttrui? | **Een onesie** |
| 8 | Hoeveel stagiaires begeleid? | **7** |

---

## Na afloop
- [ ] Eindscherm verschijnt automatisch na blok 6
- [ ] Iedereen tikt "Open je persoonlijk bericht"
- [ ] Namen moeten exact matchen — controleer dit van tevoren!
