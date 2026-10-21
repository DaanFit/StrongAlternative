# Mijn Gym — jouw eigen workout-webapp

Een gratis, simpele Progressive Web App (PWA) met **onbeperkte templates**, workouts, gewicht/herhalingen per set, trainingshistorie, een kniecheck en JSON-back-ups.

## Wat zit er al in?

De app begint met het A/B/C-schema (de oefeningen uit het gesprek van 20 oktober 2026):

- **A — Dinsdag:** Pull-Ups + Weighted Dips (superset), Box Squat, Barbell Shoulder Press, Low Step-Down gevolgd door Standing Calf Raise, Dumbbell Lateral Raise en Cable Biceps Curl + Triceps Pushdown (superset).
- **B — Vrijdag:** Barbell Shoulder Press, Barbell Hip Thrust, Cable Lateral Raise + Face Pull (superset), Low Step-Down gevolgd door Standing Calf Raise, Bulgarian Split Squat en Sliding Hamstring Curl.
- **C — Zondag:** Pull-Ups + Weighted Dips (superset), Box Squat, Romanian Deadlift en Cable Biceps Curl + Overhead Triceps Extension (superset).

Iedere oefening heeft twee werksets. Oefeningen in een superset hebben elk hun eigen invoervelden zodat je ze apart kunt loggen. De Step-Down en Calf Raise zijn een duo **achter elkaar**, geen supersets. De actuele verdeling is zes blokken op dinsdag en vrijdag en vier op zondag. De Face Pull op zondag blijft optioneel en is daarom niet standaard toegevoegd.

**Bestaande app updaten:** publiceer de nieuwe bestanden over je bestaande website op exact dezelfde URL. Maak eerst via Instellingen een JSON-back-up. De browser bewaart de oude gegevens onder dezelfde opslagnaam. Omdat we niets automatisch willen overschrijven, klik je in de nieuwe app op **Templates → + A/B/C-schema** (of op de knop op de startpagina). Oude trainingshistorie en oude templates blijven behouden. Als je de app onder een andere URL opent, staan je oude gegevens daar niet automatisch; gebruik dan je JSON-back-up met beleid (importeren vervangt daar bestaande data). 

De suggesties voor kniebelasting zijn bewust voorzichtig. De app is een **trainingslogboek**, geen medisch hulpmiddel en geen vervanging voor een sportfysiotherapeut.

## Snel online zetten via GitHub Pages (zonder zelf code te hoeven schrijven)

1. Maak een gratis account op https://github.com (of log in).
2. Klik op **New repository** en geef het bijvoorbeeld de naam `mijn-gym`.
3. Kies **Public** en klik op **Create repository**. De **broncode** is dan openbaar; je ingevoerde trainingen staan daar niet in.
4. Pak eerst de gedownloade zip uit. Klik in je nieuwe repository op **Add file → Upload files**.
5. Upload **alle bestanden en de map `icons/`** uit `gym-tracker`. Het bestand `index.html` moet direct in de hoofdmap van de repository staan.
6. Klik op **Commit changes**.
7. Ga naar **Settings → Pages**. Kies **Deploy from a branch**, `main`, `/(root)` en sla op.
8. Wacht een paar minuten. Je site verschijnt op ongeveer `https://JOUWNAAM.github.io/mijn-gym/`. Zie de echte URL onder **Settings → Pages**.
9. Open de site op je telefoon. Gebruik **Installeren / Toevoegen aan startscherm** (Android met Chrome) of **Deel → Zet op beginscherm** (iPhone met Safari). Het uiterlijk van deze stappen kan per toestel en browserversie verschillen.

**Belangrijk:** een PWA moet via HTTPS (of `localhost`) geopend worden om als app installeerbaar te zijn. Alleen een los HTML-bestand openen is vooral een preview, niet de aanbevolen manier om blijvend trainingen bij te houden.

## Lokale ontwikkeling (optioneel)

Je hebt geen frameworks of Node.js nodig. Als Python geïnstalleerd is, kun je de uitgepakte map lokaal testen:

```bash
cd gym-tracker
python -m http.server 8000
```

Open vervolgens op je computer `http://localhost:8000/`.

## Hoe verander je de app?

- `index.html` — de basispagina.
- `styles.css` — alle kleuren, lettertypes en de indeling.
- `app.js` — oefeningen, templates, trainingen en kniescores.
- `manifest.webmanifest` — appnaam, icoon en installatiestand.
- `sw.js` — bestanden offline beschikbaar houden nadat de app eenmaal online is geladen.
- `icons/` — appicoontjes.

Je kunt ook **via de app zelf** nieuwe templates maken en oefeningen wijzigen: open **Templates → Bewerken**. Daarvoor hoef je helemaal geen code te veranderen.

## Waar worden mijn gegevens opgeslagen?

In de **localStorage van de browser op dat apparaat**, niet op GitHub. Dit is snel en gratis, maar geen volwaardige database. Het synchroniseert niet tussen telefoon en laptop. Gegevens kunnen verdwijnen als je browsergegevens wist of van apparaat wisselt.

Maak regelmatig een back-up via **Instellingen → Back-up downloaden**. Bewaar het JSON-bestand veilig. Via **Back-up importeren** kun je het herstellen. De gegevens in dat back-upbestand kunnen ook persoonlijke kniechecks bevatten.

**Deel je website-URL gerust, maar deel nooit het persoonlijke back-upbestand als je je trainingen/kniechecks privé wilt houden.**

## Wat kun je later uitbreiden?

- Account en synchronisatie (bijvoorbeeld Supabase/Firebase)
- Timer tussen sets
- PR's en grafieken per oefening
- Kopiëren van een workout of een andere squat-progressie
- Eenvoudige import van Strong-exportbestanden (vereist extra dataconversie)

## Bij problemen

- De app doet niks? Controleer of alle bestanden op GitHub staan (ook `app.js` en `styles.css`).
- Geen installatieknop? Open de online HTTPS-link op je telefoon; gebruik de deel-/browseroptie.
- Data verdwenen? Importeer je laatste JSON-back-up.
- Update zichtbaar op computer maar niet op telefoon? Sluit de app en open hem opnieuw; een PWA kan de vorige versie nog tijdelijk bewaren.
