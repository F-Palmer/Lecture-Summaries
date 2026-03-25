Prev: [[7 Network Security]]

Frühes Handeln spart Geld
Design Änderungen billiger als Post-Release

Anwendungsentwickler denken nicht oft an die Sicherheit

## Designgrundsätze nach Salzer und Schröder

#### Economy of Mechanism
- Reduction of Complexity
- Sicherheitsmaßnahmen sollen so einfach wie möglich sein

#### Fail-safe defaults
- Use secure default settings
- Fehlermeldungen sind allgemein -> Zusatzinformationen sind nur in den Log files
- Deny als default action

#### Complete mediation
- complete access control
- Prüfe jeden Zugriff auf jedes Objekt
- Werte die der Benutzer beeinflussen kann, sind nicht vertrauenswürdig

#### Open Design
- Kerckhoff's  Prinzip (siehe [[4 Kryptographie]])

#### Seperation of privilege
- Aufteilung von Zugriffsprivilegien
- Beispielsweise braucht man zwei Schlüssel für den Zugriff auf eine Ressource

#### Least privilege
- nur unbedingt notwendige Privilegien
- zeitliche Gültigkeit von Rechten

#### Least common mechanism
- Komponenten, Benutzer oder Prozesse sollten möglichst wenig Infrastruktur, Logik oder Ressourcen gemeinsam nutzen

#### Psychological Acceptability
- Sicherheitsmaßnahmen, die sich leicht durchführen lassen
- Nicht Nutzer verärgern
- Nicht zu viele Warnungen. Sonst werden die wichtigen ignoriert

Cyber Resilience Act (CRA)

## Security Development Lifecycle (CRA) Grundsätze

![[SDL Grundsätze.png]]



