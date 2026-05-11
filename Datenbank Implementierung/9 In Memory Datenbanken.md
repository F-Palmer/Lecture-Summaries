Idee/ Vision: 
- alles wird zur Laufzeit errechnet
- alle Daten befinden sich im Hauptspeicher
- keine Aggregate 
- keine Views

Online Transaction Processing (OLTP):
- Operativer Alltag (z.B. Kassensystem)
- viele kleine, schnelle Transaktionen
- viele parallele Nutzer
- viele schreib UND Lesezugriffe

Online Analytical Processing (OLAP)
- für Analysen und Auswertungen gebaut
- Weniger dafür komplexere Transaktionen
- viele Lesezugriffe


Hardware: 
- Infiniband
	- Hauptspeicher mehrerer Cores miteinander verbinden
	- Übertragungsraten von bis 2,5 GB/s
- Parallele Ausnutzung mehrerer Core CPUs, die auf ein Shared Memory zugreifen, erhöht Verarbeitungsgeschwindigkeit signifikant (→ Blade Server)

Prefix Komprimierung: 
Aufeinanderfolgende sortierte Schlüssel teilen oft einen gemeinsamen Anfang – statt jeden Schlüssel vollständig zu speichern, wird nur der abweichende Rest gespeichert.

Cluster Komprimierung: 
Ähnliche oder identische Werte werden räumlich gruppiert, sodass sie gemeinsam mit einer einzigen komprimierten Repräsentation gespeichert werden können, anstatt jeden Wert einzeln abzulegen.

Sparse Komprimierung: 
Daten mit vielen leeren oder Null-Werten werden so gespeichert, dass nur die tatsächlich vorhandenen Werte mit ihrer Position abgelegt werden – die Nullen werden weggelassen.

## Column Store
Was Spricht für einen Column Store?
- Viele Spalten werden gar nicht benutzt
- Viele Spalten haben sehr niedrige Kardinalitäten (z.b: Geschlecht)
- Viele Null Werte
![[Pasted image 20260509125415.png|200]]

RecID: Zeilennummer im AV, identifiziert einen Datensatz Spaltenübergreifend
ValID: Zeigt auf einen Eintrag im Dictionary
### Einfügen in Column Store: 
(Ein AV pro Spalte)
1. Suche den einzufügenden Wert im Dictionary der Spalte:
	1. Wert existiert bereits im Dictionary: 
		- Dictionary wird nicht verändert
		- Es wird nur eine Zeile an den Attributsvektor gehängt (RecID, ValID)
	2. Wert existiert noch nicht: 
		- Dictionary bekommt einen neuen Wert mit neuer ValID
		- Wenn das Dictionary sortiert ist, muss womöglich das ganze Dictionary neu sortiert werden
		- Es wird nur eine Zeile an den Attributsvektor gehängt (RecID, ValID)


## Vermeidung von Reorg im Column Store
Ansatz 1: 
Datensätze nie löschen (Gültigkeit mit Zeitstempel kenntlich machen)
Ansatz 2:
Delta Buffer (HANA)
Einführung eines separaten Bereichs, der alle Änderungen beinhaltet
-> ab und zu Reorg
Lesen zuerst aus dem DiffBuff, dann aus dem Hauptspeicher
Veränderte Werte im Hauptspeicher werden mit Gültigkeitsvektor ungültig geflagged
Hauptspeicher ist read-only, außer bei Verschmelzung
Verlangsamt Performance

1. Schritt: Gültigkeitscheck, ungültige Records landen im History File
2. Schritt: Dictionary kombinieren
3. Schritt: Mapping von altem Diffbuff + HSP Dictionary auf das neue Dictionary
4. Schritt: Aktualisierung des Attributvektors
5. Schritt: Differential Buffer auflösen und neue HSP Attributvektor und Dictionary aufbauen
6. Schritt: Snapshot schreiben

Riesen Verschmelzungsbespiel

![[Pasted image 20260509174938.png]]
