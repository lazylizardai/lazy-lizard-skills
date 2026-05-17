---
name: pre-mortem
description: Voer een pre-mortem risicoanalyse uit voor een product, feature, project of launch. Gebruik deze skill wanneer de gebruiker een launch of go/no-go beslissing voorbereidt, vraagt om risicoanalyse, "wat kan er misgaan", "pre-mortem", "risicoinventarisatie", "Tigers Paper Tigers Elephants", of een stress-test van een plan wil voor er resources gecommitteerd worden. Classificeert risico's als Tigers (echte, evidence-backed risico's), Paper Tigers (overschatte zorgen) en Elephants (onuitgesproken concerns), en wijst urgentie toe (Launch-Blocking, Fast-Follow, Track) met owner en mitigatie. Trigger ook op "ga dit door op risico's", "wat zie ik over het hoofd", "voor we launchen even kritisch kijken", of vergelijkbare prospective-hindsight vragen.
license: MIT + Commons Clause
---

# Pre-Mortem Risk Analysis Expert

## Overzicht

Een pre-mortem is een prospective hindsight oefening: stel je voor dat je product gelanceerd is en gefaald, en werk terug om te begrijpen waarom. Deze skill gebruikt de **Tiger / Paper Tiger / Elephant** classificatie om risico's te categoriseren op type en urgentie, zodat launch-blocking issues worden aangepakt voor de launch, zonder tijd te verspillen aan onwaarschijnlijke risico's.

### Wanneer te gebruiken

* Voor je significant resources commit aan build (post-ideation, post-validation).
* Voor een grote launch, migratie of architecturale wijziging.
* Wanneer het team "een raar gevoel" heeft maar niet kan benoemen waarom.
* Wanneer stakeholders erg overtuigd zijn en je het wil stress-testen.

## Kern Concept

### Het gedachte-experiment

> "Het is 14 dagen na launch. Het product is gefaald. Wat ging er mis?"

Deze framing exploit een cognitieve bias: mensen zijn beter in het verklaren van gebeurtenissen in het verleden dan in het voorspellen ervan. Door de mislukking in het "verleden" te plaatsen (ook al is het fictief), genereren deelnemers concretere en eerlijkere risicobeoordelingen.

## Risk Classificatie

### Tigers (Echte Risico's)

Tigers zijn echte, evidence-backed risico's die serieuze schade kunnen veroorzaken als ze niet worden aangepakt.

**Kenmerken:**
* Ondersteund door data, eerdere ervaring of waarneembare trends.
* Het team kan een plausibel faalscenario concreet beschrijven.
* Ze negeren zou nalatig zijn.

**Voorbeelden:**
* "Onze authentication service is 3 keer uitgevallen vorige maand. Een launch-day outage is plausibel."
* "We hebben 0 klanten in het enterprise segment. Sales heeft geen enterprise relaties."
* "De EU regulatie treedt in werking over 60 dagen. We zijn nog niet begonnen met compliance."

### Paper Tigers (Lijken Eng, Maar Onwaarschijnlijk)

Paper Tigers zijn risico's die alarmerend klinken maar bij nadere inspectie onwaarschijnlijk zijn of minimale echte impact hebben.

**Kenmerken:**
* Gebaseerd op hypothetische scenario's zonder ondersteunend bewijs.
* Waarschijnlijkheid is laag, of impact zou beheersbaar zijn.
* Vaak ingebracht uit algemene angst, niet specifieke kennis.

**Voorbeelden:**
* "Een concurrent kopieert onze feature misschien" — kan, maar hun execution timeline is 6-12 maanden.
* "De server kan misschien 100x verkeer niet aan" — maar onze realistische projectie is 5x, met auto-scaling.
* "Gebruikers haten de nieuwe UI misschien" — maar usability testing met 8 gebruikers liet hoge tevredenheid zien.

### Elephants (Onuitgesproken Zorgen)

Elephants zijn de risico's die iedereen weet maar niemand bespreekt. De "olifant in de kamer".

**Kenmerken:**
* Het team vermijdt het onderwerp door politiek, hiërarchie of ongemak.
* Vaak mensen, proces of organisatorische issues, geen technische.
* Vaak de werkelijke oorzaak van mislukking als projecten falen.

**Voorbeelden:**
* "De tech lead gelooft niet in dit project en is al weken disengaged."
* "De CEO's pet feature stuurt de roadmap, maar klanten hebben er nooit om gevraagd."
* "We hebben geen plan voor wat er gebeurt als het contract van de contractor afloopt volgende maand."

## Tiger Urgentie Classificatie

Zodra een risico als Tiger is geclassificeerd, ken je urgentie toe:

| Urgentie | Definitie | Actie Vereist |
| --- | --- | --- |
| **Launch-Blocking** | Als niet opgelost, mag de launch niet doorgaan. | Concrete mitigatie, toegewezen owner, decision date voor launch. |
| **Fast-Follow** | Moet binnen 2 weken na launch worden aangepakt. | Gedocumenteerd plan, owner, ingepland voor eerste post-launch sprint. |
| **Track** | Monitoren en aanpakken bij escalatie. | Toegevoegd aan risk register, reviewed op vaste cadence. |

## Methodologie

### Fase 1: Set the Scene (5 min)

De facilitator leest deze prompt voor:

> "Stel je voor dat het 14 dagen na onze launch is. Het product is gefaald. Gebruikers adopteren niet, key metrics zijn down, leadership vraagt wat er mis ging. Neem 10 minuten om elke reden op te schrijven waarom we faalden. Wees specifiek. Wees eerlijk. Niks is off limits."

**Grondregels:**
* Anonieme bijdragen (sticky notes of digitaal equivalent).
* Geen attributie, geen blame, geen oordeel.
* Kwantiteit boven kwaliteit in de eerste ronde.

### Fase 2: Risico's Genereren (10 min)

Elke deelnemer schrijft onafhankelijk failure scenarios op. Eén risico per sticky. Streef naar 5-10 per persoon.

**Prompts om denken te stimuleren:**
* Welk technisch systeem is het meest waarschijnlijk om te breken?
* Welk klant-bezwaar hebben we niet geadresseerd?
* Welke teamdynamiek kan ons doen ontsporen?
* Welke externe gebeurtenis kan onze aannames veranderen?
* Wat doen we alsof het geen probleem is?
* Welke beslissing vermijden we?

### Fase 3: Delen en Clusteren (15 min)

1. Lees elk risico hardop (zonder attributie).
2. Plaats op het bord.
3. Groepeer vergelijkbare risico's.
4. Merge duplicaten.

### Fase 4: Classificeren (15 min)

Voor elke cluster beslist de groep:

| Classificatie | Criteria |
| --- | --- |
| **Tiger** | Ondersteund door evidence. Plausibel faalscenario. |
| **Paper Tiger** | Klinkt eng maar onwaarschijnlijk of lage impact bij inspectie. |
| **Elephant** | De kamer werd stil toen dit werd voorgelezen. Mensen wisselden blikken uit. |

Voor elke Tiger, ken urgentie toe: Launch-Blocking, Fast-Follow of Track.

### Fase 5: Mitigatie Plannen (15 min)

Voor elke **Launch-Blocking Tiger**, vul in:

| Veld | Beschrijving |
| --- | --- |
| **Risico** | Heldere beschrijving |
| **Evidence** | Welke data of ervaring ondersteunt dat dit een echt risico is? |
| **Mitigatie** | Specifieke, concrete actie om het risico te verminderen |
| **Owner** | Eén persoon verantwoordelijk |
| **Decision Date** | Datum waarop de mitigatie compleet moet zijn of de launch-beslissing opnieuw bekeken wordt |

### Fase 6: Elephants Aanpakken (10 min)

Elephants vragen een andere aanpak dan Tigers:

1. **Acknowledge** — Noem de elephant expliciet. "Het team is bezorgd dat..."
2. **Assess** — Is dit eigenlijk een Tiger in vermomming? Zo ja, herclassificeer.
3. **Decide** — Pak het aan (wijs owner toe) of accepteer het bewust (documenteer acceptatie en rationale).

## Python Tool: risk_categorizer.py

Categoriseer en analyseer risico's met de CLI tool:

```bash
# Run met demo data
python3 scripts/risk_categorizer.py --demo

# Run met custom input
python3 scripts/risk_categorizer.py input.json

# Output als JSON
python3 scripts/risk_categorizer.py input.json --format json
```

### Input Formaat

```json
{
  "risks": [
    {
      "description": "Authentication service heeft 3 outages gehad in de afgelopen maand",
      "category": "tiger",
      "evidence": "Incident reports van laatste 30 dagen",
      "urgency": "launch_blocking"
    }
  ]
}
```

### Output

Risk distribution summary, actieplannen voor launch-blocking tigers, en flags voor elephants die mogelijk verder onderzoek vereisen.

Zie `scripts/risk_categorizer.py` voor volledige documentatie.

## Output Formaat

### Pre-Mortem Summary

```
Pre-Mortem Analyse: [Product/Feature Naam]
Datum: YYYY-MM-DD
Deelnemers: [lijst]
Totaal risico's geïdentificeerd: N
  - Tigers: X (Launch-Blocking: A, Fast-Follow: B, Track: C)
  - Paper Tigers: Y
  - Elephants: Z
```

### Risk Registry

| # | Risico | Categorie | Urgentie | Evidence | Mitigatie | Owner | Decision Date |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | ... | Tiger | Launch-Blocking | ... | ... | ... | ... |
| 2 | ... | Tiger | Fast-Follow | ... | ... | ... | ... |
| 3 | ... | Paper Tiger | -- | ... | -- | -- | -- |
| 4 | ... | Elephant | TBD | ... | ... | ... | ... |

Gebruik `assets/pre_mortem_template.md` voor het volledige document template.

## Troubleshooting

| Symptoom | Waarschijnlijke Oorzaak | Oplossing |
| --- | --- | --- |
| Team genereert vooral paper tigers | Risico-aversie of oppervlakkig denken; team gaat niet vol in het faalscenario | Lees het gedachte-experiment langzaam opnieuw; verleng silent writing van 10 naar 15 min; gebruik specifieke prompts |
| Geen elephants opgekomen | Psychologische veiligheid te laag, of facilitator is een manager wat power dynamics creëert | Gebruik anonieme bijdragen; overweeg externe facilitator; scheid van performance reviews |
| Alle risico's geclassificeerd als tigers | Team mist kalibratie voor wat echt evidence is vs. angst | Eis concrete evidence voor elke tiger; als hypothetisch, herclassificeer als paper tiger |
| Launch-blocking tigers zonder owners | Fase 5 mitigatie planning overgeslagen | Reserveer altijd 15 min voor mitigatieplannen; sla Fase 5 nooit over |

## Succes Criteria

* Pre-mortem gehouden voor elke grote launch, migratie of significante resource commitment
* Minimaal 5-10 risico's per persoon gegenereerd in silent writing fase
* Distributie omvat alle drie categorieën (niet alleen tigers, niet alleen paper tigers)
* Elke launch-blocking tiger heeft owner, concrete mitigatie en decision date
* Elephants expliciet benoemd en óf aangepakt óf bewust geaccepteerd met documentatie
* Pre-mortem findings gereviewed tegen werkelijke uitkomsten post-launch om toekomstige sessies te kalibreren
* Sessieduur blijft binnen 60-90 min totaal over alle 6 fases

## Scope & Limitaties

**In Scope:**
* Prospective hindsight oefeningen met "14 dagen na launch" framing
* Tiger / Paper Tiger / Elephant classificatie met urgentielevels
* Risk registry generatie met categoriedistributie en actieplannen
* Facilitatie-methodologie voor in-person én remote teams

**Out of Scope:**
* Doorlopend risicomanagement (gebruik een risk matrix tool)
* Kwantitatieve risicoanalyse met probability/impact scoring
* Product discovery en hypothesevalidatie

**Caveats:**
* Pre-mortems werken het best met 4-8 deelnemers. Minder dan 4 beperkt perspectief; meer dan 10 maakt classificatie onhandelbaar.
* Psychologische veiligheid is een vereiste. Als het team niet eerlijk kan spreken, krijg je gesteriliseerde resultaten.

## Referenties

* Gary Klein, "Performing a Project Pre-Mortem," *Harvard Business Review* (2007)
* Daniel Kahneman, *Thinking, Fast and Slow* (2011) — prospective hindsight
* Chip Heath & Dan Heath, *Decisive* (2013) — beslissen onder onzekerheid
* Amy Edmondson, *The Fearless Organization* (2018) — psychologische veiligheid

---

**Bron:** [borghei/Claude-Skills](https://github.com/borghei/Claude-Skills/tree/main/project-management/discovery/pre-mortem) · MIT + Commons Clause
