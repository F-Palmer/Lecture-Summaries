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

Horizontale Fragmentierung: 
Teilung einer Tabelle, sodass manche Datensätze auf einer Station laufen während andere wo anderes gelagert werden
-> sinnvollerwise nach Kritierien wie z.B: Personen die in Deutschland wohnen kommen auf eine Station

Vertikale Fragmentierung: 
Spalten einer Tabelle auf andere Station