> **Verteilte Datenbank**: 
> Verbund mehrerer logisch miteinander zusammenhängender Datenbanken, die jeweils auf verschiedenen Knoten eines Rechnernetzes liege

> **Verteiltes Datenbank Managementsystem**: 
> Software System zur Verwaltung einer verteilten Datenbank, wobei dem Benutzer die Verteilung der Daten (weitgehend) verborgen bleibt

#### Entwurf einer verteilten Datenbank
![[Pasted image 20260504101534.png|400]]

Allokation von Fragmenten: 
- Anhand der erwarteten Anwendungen
- Entwurfskonflikte: Ein Fragment wird auf 2 Stationen häufig benötigt
	- Bei der Redundanzfreien Allokation muss eine Station bevorzugt werden und damit die andere benachteiligt

Horizontale Fragmentierung/ Partitionierung: 
Teilung einer Tabelle, sodass manche Datensätze auf einer Station laufen während andere wo anderes gelagert werden
-> sinnvollerwise nach Kritierien wie z.B: Personen die in Deutschland wohnen kommen auf eine Station

Vertikale Fragmentierung/ Partitionierung: 
Spalten einer Tabelle auf andere Station

Bereichspartitionierung:
Auftrennung der Tupel in Bereiche
z.B In 5 Bereiche nach Geburtstag: < 1925 < 1950 < 1975 < 2000 < 2025
-> Horizontale Fragmentierung

Round-Robi-Partitionierung: 
eder neue Datensatz wird der nächsten Partition zugewiesen, zyklisch von Partition 1 bis N, dann wieder von vorne:
- Datensatz 1 → Partition 1
- Datensatz 2 → Partition 2
- Datensatz 3 → Partition 3
- Datensatz 4 → Partition 1 (wieder von vorne)
- usw.

Hash Partitionierung: 
Hashfunktion auf einen Schlüsselwert angewendet wird, um zu bestimmen, auf welche Partition ein Datensatz kommt

