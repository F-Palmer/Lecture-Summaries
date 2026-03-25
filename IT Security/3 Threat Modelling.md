Prev: [[2 Bedrohungen, Angreifer, CVSS, STRIDE]] Next: [[4 Kryptographie]]

1. Scope your work
2. Determine Threats
3. Determine Countermeasures and Mitigation

## TM1: Scope your Work
Thread Model Information Document with the following: 
- Version Number
- Description
- Owner and Reviewer

![[Data Flow Diagram.png]]

> Trust Levels: 
> Access rights that the application will grant to external entities

> Assets: 
> Have something that attackers want
> Can be physical (list of clients) or abstract (organization reputation)

Trust Levels are cross-referenced with the entry points and assets -> able to define access rights to each entry point

> Entry Points: 
> Interfaces through which potential attackers can interact with the application or supply it with data

## TM2: Determine Threats

Beispiel: 

**Threat**: Account takeover via stolen credentials
**Asset**: User Login Details
**STRIDE category:** Spoofing (primary), Information Disclosure, Elevation
of Privilege
**Description**:
An attacker steals or guesses valid user login details (e.g., via phishing or
reused passwords) and logs in as a legitimate user or librarian, gaining
unauthorized access to data or admin functions.

## TM3: Determine Countermeasures and Mitigation

Risiko = Wahrscheinlichkeit * Auswirkung (siehe [[1 Concepts, Principles & Terminology]])

Wahrscheinlichkeit hängt von Einfachheit ab
Auswirkung basiert auf Schadenspotential und Ausweitung

Alternative dazu ist DREAD-D

### DREAD-D
Bewertung von Bedrohungen für Software
Jede Kategorie bekommt Wert
Skala ist nicht vordefiniert
Summierung aller Werte

> Damage: 
> Wie groß ist der Schaden bei Angriffsfall - Monetärer Verlust, Datenverlust ... 

> Reproducibility: 
> Wie einfach kann der Angriff durchgeführt werden

> Exploitability: 
> Aufwand und Expertise die der Angriff benötigt

> Affected Users: 
> Anzahl der betroffenen Nutzer

> Discoverability: 
> Wie einfach kann diese Lücke gefunden werden

