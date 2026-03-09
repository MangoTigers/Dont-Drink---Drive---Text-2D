# Mermaid Flytskjema: Dont Drink & Drive & Text

Kopier koden under og lim inn på [mermaid.live](https://mermaid.live) eller i en Markdown-fil med Mermaid-støtte.

---

```mermaid
flowchart TD
    %% Styling
    classDef mainLoop fill:#90EE90,stroke:#2d5016,stroke-width:2px,color:#000
    classDef input fill:#87CEEB,stroke:#104e8b,stroke-width:2px,color:#000
    classDef state fill:#FFE135,stroke:#8b7500,stroke-width:2px,color:#000
    classDef crash fill:#FF6B6B,stroke:#8b0000,stroke-width:3px,color:#fff
    classDef phone fill:#DDA0DD,stroke:#68228b,stroke-width:2px,color:#000
    
    %% Hovedflyt
    START([START]):::mainLoop
    START --> INIT[INITIALISER SPILL<br/>- Sett opp vindu<br/>- Opprett spiller<br/>- Nullstill tilstand]:::mainLoop
    
    INIT --> LOOP{HOVEDLØKKE<br/>60 FPS}:::mainLoop
    
    LOOP --> INPUT[HÅNDTER INPUT<br/>• WASD/Piler → Styr bil<br/>• SPACE → Drikk<br/>• Musklikk → Telefon<br/>• R → Reset]:::input
    
    INPUT --> UPDATE1[OPPDATER SPILLTILSTAND<br/>1. Øk timer og hastighet<br/>2. Øk beruselse over tid<br/>3. Sjekk drikkeoppfordring]:::mainLoop
    
    UPDATE1 --> UPDATE2[4. Spawn trafikk<br/>5. Flytt alle biler<br/>6. Fjern biler utenfor]:::mainLoop
    
    UPDATE2 --> UPDATE3[7. Sjekk beruselseseffekter<br/>Tilfeldig drift hvis høy]:::mainLoop
    
    UPDATE3 --> COLLISION{Kollisjon med<br/>annen bil?}:::state
    COLLISION -->|JA| CRASH1[CRASH: Kollisjon]:::crash
    COLLISION -->|NEI| DRUNK{Beruselse<br/>>= 100?}:::state
    
    DRUNK -->|JA| CRASH2[CRASH: Beruselse]:::crash
    DRUNK -->|NEI| TIME{Tid >= 120<br/>sekunder?}:::state
    
    TIME -->|JA| CRASH3[CRASH: Tretthet]:::crash
    TIME -->|NEI| PHONE_UPDATE[OPPDATER TELEFON]:::phone
    
    PHONE_UPDATE --> DRAW[TEGN ALT<br/>- Vei og trafikk<br/>- Spiller<br/>- UI og stats<br/>- Telefon<br/>- Crash-overlay]:::mainLoop
    
    DRAW --> CHECK_CRASHED{Crashed?}:::state
    CHECK_CRASHED -->|NEI| LOOP
    CHECK_CRASHED -->|JA| SHOW_CRASH[Vis konsekvenser<br/>og statistikk]:::crash
    
    SHOW_CRASH --> WAIT_INPUT{Vent på<br/>input...}:::crash
    WAIT_INPUT -->|R| INIT
    WAIT_INPUT -->|ESC| END([SLUTT]):::crash
    
    CRASH1 --> SHOW_CRASH
    CRASH2 --> SHOW_CRASH
    CRASH3 --> SHOW_CRASH
```

---

## Telefonsystem (Parallelt subsystem)

```mermaid
flowchart TD
    classDef phone fill:#DDA0DD,stroke:#68228b,stroke-width:2px,color:#000
    classDef input fill:#87CEEB,stroke:#104e8b,stroke-width:2px,color:#000
    classDef success fill:#90EE90,stroke:#2d5016,stroke-width:2px,color:#000
    classDef error fill:#FFB6C1,stroke:#8b1a1a,stroke-width:2px,color:#000
    
    CLICK[MUSKLIKK på tastatur?]:::input
    CLICK --> IDENTIFY[Identifiser knapp]:::phone
    
    IDENTIFY --> TYPE{Type?}:::phone
    TYPE -->|Bokstav| ADD_CHAR[Legg til tegn]:::phone
    TYPE -->|Mellomrom| ADD_SPACE[Legg til mellomrom]:::phone
    TYPE -->|Slett| DELETE[Fjern siste tegn]:::phone
    TYPE -->|Send| VALIDATE{VALIDER SVAR}:::phone
    
    VALIDATE -->|Riktig| SUCCESS[✓ Øk teller<br/>✓ Ny oppgave<br/>✓ Vis 'Sendt']:::success
    VALIDATE -->|Feil| ERROR[✗ Vis 'Feil'<br/>✗ Vis hint]:::error
    
    SUCCESS --> CLEAR[Tøm input]:::phone
    ERROR --> CLEAR
    
    ADD_CHAR --> BACK[Tilbake til<br/>hovedløkke]:::phone
    ADD_SPACE --> BACK
    DELETE --> BACK
    CLEAR --> BACK
```

---

## Tilstandsdiagram

```mermaid
stateDiagram-v2
    [*] --> NORMAL
    NORMAL --> SVEKKET : Beruselse > 40
    SVEKKET --> FARLIG : Beruselse > 70
    FARLIG --> CRASHED : Beruselse >= 100<br/>eller Kollisjon<br/>eller Tid >= 120s
    CRASHED --> [*]
    
    note right of NORMAL
        Beruselse: 0-40
        Farge: Grønn
        Normal kjøring
    end note
    
    note right of SVEKKET
        Beruselse: 40-70
        Farge: Gul
        Svekket kontroll
    end note
    
    note right of FARLIG
        Beruselse: 70-100
        Farge: Rød
        Tilfeldig drift
        Fare for crash
    end note
    
    note right of CRASHED
        Spillet stopper
        Vis konsekvenser
        Vent på reset
    end note
```