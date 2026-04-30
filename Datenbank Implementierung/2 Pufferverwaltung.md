Ziel: Reduzierung der Zugriffslücke

> Puffer:
> ausgezeichneter Bereich des Hauptspeichers
> in Pufferrahmen gegliedert (kann eine Seite aufnehmen)

$>$ 90% der Seitenzugriffe aus dem Puffer realisierbar

1. Suchen einer Seite im Puffer
2. Speicherzuteilung im Puffer 
3. Seitenersetzungsstrategien

## Suchen einer Seite
- Speichersystem fordert Seite mit Seitennummer an
- Pufferverwaltung prüft ob sie im Puffer ist

Direkte Pufferdurchsuchung: 
- In jedem Pufferrahmen wird auf der Seite die Seitennummer überprüft
Indirekte Pufferdurchsuchung:
- Suchen über Zusatzstrukturen: Seitenlisten (Liste von allen Seiten im Puffer)
	- Liste kann Sortiert und unsortiert sein

## Speicheraufteilung im Puffer
Puffer muss aufgeteilt werden unter den Transaktionen

Lokale Strategien:
- Jeder Transaktion werden bestimmte Pufferteile verfügbar gemacht
- Größe der Transaktionsbereiche:
	- Dynamisch: zur Programmlaufzeit
	- Statisch: vor Ablauf der Transaktionen
Globale Strategien: 
- "Berücksichtigen das Zugriffsverhalten aller Transaktionen insgesamt"
- Bessere Berücksichtigung von Seiten die parallel von mehreren Transaktionen gebraucht werden
Seitentypbezogene Strategien:
- Partition des Puffers in mehrere Typen von Pufferrahmen
- Pufferrahmen für
	- Datenseiten
	- Zugriffspfadseiten
	- Data-Dictionary-Seiten
	- usw.

## Seitenersetzung
> Demand-paging-Verfahren: 
> Eine Seite wird angefordert, eine Seit im Puffer wird ersetzt
> (Standardfall)

> Prefetching: 
> Seiten die in der Zukunft womöglich gebraucht werden, werden auch in den Puffer geladen

Seitenverdrängungsstrategien hatten wir bei Röthig schon

Adaptive Strategien:
Eine große Relation wird vollständig gelesen:
- Jede Seite muss in den Puffer gebracht werden und verdrängt ältere Seiten aus dem Puffer
-  auch wenn jede dieser Seiten nur einmal gelesen wird
-> Solche Scan-Operationen werden bei adaptive Strategien anders behandelt