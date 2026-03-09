# Dont Drink & Drive & Text

Et 2D top-down Python-spill bygget med pygame-ce for trafikksikkerhet og forebygging.

Spilleren styrer en bil samtidig som hen blir presset til å drikke og svare på meldinger på en telefon ved siden av veien. Opplevelsen starter lystig, men eskalerer til en alvorlig slutt som viser konsekvensene av ruspåvirket og distrahert kjøring.

## Beta-status

### Prosjektbeskrivelse
`Dont Drink & Drive & Text` er et interaktivt præventivspill som bruker ubehagelig spillmekanikk for å øke bevissthet omkring risikoen ved ruspåvirket og distrahert kjøring. Spilleren møter eskalerende utfordringer: kjøreoppdrag, telefonmeldinger og drikkepress som legger vekt på multitasking. Etter to minutter oppstår uunngåelig krasj, noe som gir et tydelig og alvorlig budskap om konsekvensene.

### Hva virker i beta?
✅ **Fungerende funksjoner:**
- Top-down kjøring i tre kjørefelt med møtende trafikk
- Interaktiv telefonpanel med tekstmeldinger som skal besvares
- Klikkbart on-screen tastatur (norsk layout med Æ, Ø, Å)
- Beruselsesskala som eskalerer og påvirker bilkontroll
- Case-insensitive tekstvalidering med hint-system
- Balansert spillengde (~2 minutter til uunngåelig krasj)
- Krasjsekvens med statistikk og alvorlig budskap

❌ **Kjente begrensninger i beta:**
- Web-deployment via Pygbag under utprøving
- Grafisk elementer og animasjoner er minimale
- Ingen lyd eller musikk implementert ennå
- Kun 5 meldingsoppdrag (kan utvides)

### Hvordan kjøre

**Krav:**
- Python 3.10 eller høyere
- pygame-ce 2.5.7 eller høyere

**Installasjon (Windows):**
```powershell
cd c:\Users\olr\UGNASync\DontDrinkDriveText2D
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
python main.py
```

**Kjør på annet OS (Mac/Linux):**
```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python main.py
```

### Demo-scenario: Kort opplevelse av kjernefunksjonen

1. **Start spillet:** `python main.py`
2. **Kjør rett fremover:** Bruk `A`/`D` eller piltaster for å holde deg i kjørefeltene
3. **Møt første meldingsoppgave:** En tekstmelding dukker opp på telefonpanelet (høyre side)
4. **Svar på meldingen:** Klikk på bunn-tastaturet og skriv et svar (se hint hvis du er usikker)
5. **Drikk når oppfordret:** Trykk `Space` når "Drikk"-knappen vises
6. **Opplev eskalasjon:** Trafikk og beruselsesskala øker gradvis
7. **Krasj oppstår:** Etter ~120 sekunder oppstår uunngåelig krasj – det er intentjonelt!
8. **Se konsekvensen:** Krasjskjermen viser statistikk og alvorlig budskap

### Kjente feil og risiko

| Feil/Risiko | Alvorlighetsgrad | Status |
|-------------|-----------------|--------|
| Tekstfelt kan fryses hvis man skriver for raskt i begge paneler simultant | Lav | Observert, kreves testing |
| Web-versjon (Pygbag) krever ytterligere testing på ulike nettlesere | Medium | Planlagt arbeid |
| Grafisk ytelse ved høy trafikktetthet | Lav | Ikke kritisk ved 60 FPS |
| No-sound situasjon kan gjøre opplevelsen mindre engasjerende | Lav | Fremtidig forbedring |

## Konkurransepitch

`Dont Drink & Drive & Text` er bevisst laget for å være ubehagelig:
- Tidlig i spillet belønnes farlig multitasking med positiv feedback.
- Vanskelighetsgrad og beruselse øker gradvis til kontrollen svikter.
- Krasjsekvensen gir tydelig budskap om konsekvenser og forebygging.

Hovedmålet er at spilleren sitter igjen med en sterkere risikoforståelse.

## Funksjoner

- Top-down kjøring i felt med møtende/hindrende trafikk
- Telefonpanel med meldingsmål og klikkbart tastatur på skjermen
- Flere meldinger har flere gyldige svaralternativer
- Svar valideres uten krav om store bokstaver (caps)
- Økende beruselsesnivå som påvirker kontrollen
- Dynamisk økning av fart og trafikk
- Krasj gjennom kollisjon eller uunngåelig tidsbegrensning
- Konsekvensskjerm med statistikk og tydelig budskap

## Kontroller

- `A` / `Venstre pil`: flytt til venstre felt
- `D` / `Høyre pil`: flytt til høyre felt
- `Space`: drikk når du blir oppfordret
- Musklikk på telefontastaturet: skriv/slett/send melding
- `R`: start på nytt etter krasj
- `Esc`: avslutt

## Krav

- Python 3.10+
- pygame-ce 2.5+

## Installer og kjør

```powershell
cd c:\Users\olr\UGNASync\DontDrinkDriveText2D
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
python main.py
```

## Prosjektstruktur

```text
DontDrinkDriveText2D/
├─ docs/
│  ├─ CONTEST_SUBMISSION.md
│  ├─ GAME_DESIGN.md
│  └─ TECHNICAL_DOCUMENTATION.md
├─ src/
│  └─ dddt_game/
│     ├─ __init__.py
│     ├─ config.py
│     ├─ entities.py
│     ├─ game.py
│     └─ phone.py
├─ main.py
└─ requirements.txt
```

## Pedagogisk ramme

Spillet viser farlig adferd for å motvirke den:
- Dette er forebyggingsinnhold, ikke oppmuntring.
- Spillet er med vilje tragisk i utviklingen.
- Bruk gjerne korte refleksjonsspørsmål etter spilløkten.


# Endringslogg - Dont Drink & Drive & Text

## Versjon 1.0 - "Web-klar utgivelse" (6. mars 2026)
**Første offisielle utgivelse**
- 🎮 Ferdig spillbart konsept: topp-ned kjøring + interaktiv telefon
- 🇳🇴 Fullstendig norsk språk (UI, meldinger, dokumentasjon, krasjtekst)
- ⌨️ Norsk telefontastatur med Æ, Ø, Å som dedikerte knapper
- 📝 Flere gyldige svar per meldingsoppgave
- 🔤 Case-insensitive tekstvalidering (ingen caps-krav)
- 💬 Skriverlinje (blinkende cursor) i tekstfeltet
- 🚗 Myk bilkontroll med WASD - kontinuerlig interpolert bevegelse mellom felt
- ⏱️ Balansert spillengde: ~2 minutter før uunngåelig krasj
- 📚 Komplett dokumentasjon for konkurranseinnlevering
- 🌐 Forberedt for web-deployment via Pygbag

### Tekniske detaljer
- Smooth lane-switching med `actual_x` og `target_lane_index`
- Justert beruselsesskala og trafikkeskalering for lengre spilleopplevelse
- Klikkbart on-screen tastatur i stedet for fysisk tastaturinput
- Hint-system som viser alle godkjente svar ved feil

---

## Versjon 0.6 - "Norsk tastatur-oppdatering"
- ⌨️ Implementert QWERTY telefontastatur med klikkbare knapper
- 🔤 Lagt til Æ, Ø, Å som egne tastaturknapper
- 📝 Oppdatert meldingsoppgaver til å kreve norske tegn i svar
- 🎯 Flere meldinger har nå multiple gyldige svaralternativer
- 🔠 Fjernet caps-krav, case-insensitive validering

---

## Versjon 0.5 - "Norsk språkversjon"
- 🇳🇴 Oversatt all spillerrettet tekst til norsk
- 🇳🇴 Oversatt all dokumentasjon til norsk
- 🎮 Beholdt engelske variabelnavn og kode-kommentarer
- 📄 Norske UI-tekster, meldinger, crash-screens og prompts

---

## Versjon 0.4 - "Balanseringsoppdatering"
- ⏱️ Redusert beruselseshastighet drastisk (fra 0.08 til 0.02 per sekund)
- 🚗 Justert trafikkeskalering for mykere progresjon
- 🎯 Økt tid før første drikkeoppfordring (30 → 45 sekunder)
- ⚖️ Balansert for ~2 minutters spilletid før krasj
- 🔧 Finjustert lateral drift og spawn-rates

---

## Versjon 0.3 - "Telefonsystem"
- 📱 Implementert komplett telefonsystem med tekstoppgaver
- 💬 10 unike meldingsscenarier (familie, venner, jobb, skole)
- ⌨️ Tastaturinput for å svare på meldinger
- ✅ Oppgavemål: fullfør alle meldinger før krasj
- 📊 Visuell fremdriftsindikator på telefonen
- ⏱️ Feedback-timer for riktig/feil svar

---

## Versjon 0.2 - "Kjernelogikk og spillmekanikk"
- 🚗 Top-down kjøresystem med 3 felt
- 🚙 Trafikksystem med tilfeldige biler og eskalering
- 🍺 Beruselsessystem med progressiv svekkelse
- 🎯 "Drink prompt" overlay - press space for å drikke
- 💥 Kollisjonsdeteksjon og crash-håndtering
- 😢 Trist crash-skjerm med konsekvenser og statistikk
- 🎨 Fargekodet feedback (grønn fase → rød fare)
- 📊 Session stats (distanse, meldinger, drikkevarer)

---

## Versjon 0.1 - "Initial oppsett"
- 🏗️ Prosjektstruktur opprettet
- 📦 Pygame-CE integrering (Python 3.14 kompatibilitet)
- 🎨 Grunnleggende rendering-system
- 📁 Modulær kodebase (game.py, entities.py, phone.py, config.py)
- 📝 README og grunnleggende dokumentasjon
- 🧪 Virtual environment setup med requirements.txt
- ✅ Import smoke tests bestått