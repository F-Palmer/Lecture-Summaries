Prev: [[1 Concepts, Principles & Terminology]] Next: [[3 Threat Modelling]]

> Security (Sicherheit): 
> Schutz gegen vorsätzliche Bedrohungen

> Safety (Sicherheit): 
> Schutz gegen zufällige schadhafte Bedrohungen

### Klassifizierung von Bedrohungen

Enthüllung (Disclosure) -> unberechtigter Zugang zu Informationen
Täuschung (Deception) -> Entgegennahme falscher Daten
Störung (Disruption) -> Unterbrechung oder Verhinderung der Richtigen Funktion
Übernahme (Usurpation) -> unberechtigte Kontrolle über Ressourcen

## Angreifer Modelle

> Netzwerk-Angreifer: 
> Sitzt in der Kommunikationsverbindung zwischen zwei Teilnehmern
> - Beobachten des Netzverkehrs
> - Unterbrechen "
> - Erzeugen von "
> 
> Man-in-the-middle: Gezielte Veränderung des Netzwerkverkehrs 

> Entfernter Angreifer: 
> Kann mit einem entfernten System über ein Netzwerk interagieren
> - Ausführen von Code
> - Denial of Service
> - Abschöpfen von Informationen

> Lokaler Angreifer: 
> Führt beliebigen Code aus (aber mit beschränkten Zugriffsrechten)
> Beispiel: Mehrbenutzer Systeme

> Web-Angreifer:
> Spezifisch für Web-Anwendungen
> 
> Man-in-the-browser: Kann HTTP Anfragen aus dem Browser des Benutzers heraus erzeugen
> 
> XSS-Angreifer: Kann JS im clientseitigen Kontext der angegriffenen Anwendung ausführen

## Classifying cyber attackers

> Amateurs: 
> little or skill 
> use existing tools and methods

> Hackers: 
> White hats: with permission and to improve security
> Gray hats: compromise systems without permissions
> Black hats: for illegal personal, financial or political gain

> Cyber criminals: 
> For financial gain

> Hacktivist:
> Protest against organisations or governments
> Leak information

> State-sponsored
> obvious

## Common Vulnerability Scoring System (CVSS)

**Common Vulnerabilites and Exposures (CVE)** ist eine Schwachstelle die im Rahmen des **Vulnerability Discolsure Prozesses (CVD)** eine Nummer von einer **CVE Numbering Authority (CNA)** erhalten hat, nach dem **Common Vulnerability Scoring System (CVSS)** bewertet wurde und in der CVE-Liste veröffentlicht wurde. 

Liste wird von Mitre Corporation verwaltet

### Ablauf CVD
1) Sicherheitslücke wird entdeckt
2) CVE Nummer wird mit Beschreibung beantragt
3) Einreichen der Schwäche in die Liste (Keine Veröffentlichung)
4) Weitergabe des CVE an den Hersteller
5) Zeit für Korrektur durch den Hersteller
6) Veröffentlichung des CVE in den offiziellen Listen

### Berechnung CVS
- Base Metrics
	- Attack Complexity
	- Privileges Required
- Temporal Metrics
	- Report confidence
- Environmental Metrics
	- Confidential Requirement 

## STRIDE

![[STRIDE.png]]

## Datenflussdiagramme
![[Datenflussdiagramme.png]]
![[STRIDE in Datenflusselementen.png]]

Beispiel: 
![[Beispiel Datenflussdiagram.png]]
