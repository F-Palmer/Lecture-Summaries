- Zur Verwendung müssen Daten in den Hauptspeicher geladen werden
	- Dort werden Daten im Puffer verwaltet und so lange wie möglich zwischengespeichert

### Speicherpyramide
![[Pasted image 20260427174603.png]]
- Nearline (Magenetband-Roboter), Offline (per Hand)

### Cache-Hierachrie
> **Zugriffslücke**:
> Unterschiede zwischen Zugriffszeiten zwischen den Ebenen

- Speicher von Daten auf Ebene "x" von Ebene "x+1" (Ebene eins weiter unten, langsamer) zwischen
- Caching Prinizip funktioniert nicht, wenn immer neue Daten benötigt werden

- Zeitliche Lokalität:
	- in kurzer Zeit wird häufig auf die gleichen Daten zugegriffen
- Räumliche Lokalität: 
	- zusammen angefragte Daten sind auf dem Hintergrundspeicher zusammen abgelegt

> **Prefetching**: 
> Derzeit noch nicht benötigte, aber wahrscheinlich bald benötigte und leicht erreichbare Daten mitlesen

> **Clustering**: 
> Daten in einer günstigen Reihenfolge anordnen

Ein Sector ist kein Pizza Stück!

## Magnetplatte
- Adressierung über Zylinder, Spur und Sectornummer

> **Zugriffszeit**: 
> Von Auftrag bis zur Übertragung des Blockinhalts
> - seek time: Zeit bis zum finden der richtigen Spur
> - latency time: Zeit bis zum richtigen Block gedreht wurde
> - data-transfer time: Übertragungszeit des Blocks
> Seek time > data-transfer time > latency time

> **Controller**: 
> Mapped von Speicheradresse auf physische Sektoren der Platte 

## Flash-Laufwerke (SSD)
- Daten in Flashblocks (Arrays von Speicherzellen)
- Jeder Block 128kB
- Jeder Block in 2kB große Seiten unterteilt
- Löschen (alles auf 1 zurücksetzen) nur auf ganzem Block möglich

> **Wahlfreier Zugriff**: 
> die Möglichkeit, in konstanter Zeit einen Speicherzugriff auf ein beliebiges Element durchführen zu können

- Schreibvorgänge gleichmäßig auf alle Blöcke verteilen

### Einsatz von Flash-DBMS
- einfach ersetzten nicht sinnvoll

- Schnellere Festplatte
- Zusätzlicher Cache zwischen Hauptspeicher und Magnetplatte
- Medium für Spezialzwecke

## Datenverteilung
1. RAID
2. Datencontainer auf Platten verteilt
3. Tabelle auf Datencontainer verteilt
4. Datensätze auf Tabellen verteilt

### RAID 
Redundant Array of Independent Disks
Verbinden mehrere Festplatten mit einem Controller zu einem einzigen logischen Laufwerk

- Ausfallsicherheit und Zuverlässigkeit wird erhöht
- Effizienzsteigerung durch parallele Zugriffe

Paritätsbits auf einer anderen Platte speichern

![[Pasted image 20260429163755.png]]

### Error Correction Codes
![[Pasted image 20260428182407.png|500]]
Wird nicht erklärt wie es funktioniert (Altklausuren?)

## Netzwerkspeicher
> Direct Attached Storage (DAS): 
> - Einem Server zugewiesen
> - Zugriff auf den Daten nur über Server

> Network Attached Storage (NAS):
> - Hängt am Netzwerk, nicht am Server
> - Übertragung an mehrere Clients möglich 

> Storage Area Network (SAN):
> - Beliebige Serverzuordnung (shared Disk)
> - Übertragung von Blöcken möglich (sinnvoll mit DBMS)

> Hadoop Distributed File System (HDFS):
> - Redundanzgrad und Blockgröße frei wählbar
> - Dynamische Lastverteilung auf verschiedene Slave Knoten
> - Ideal für große Dateien

## Dateiorganisation

Drei Möglichkeiten: 
- jede Relation und jeden Zugriffspfad in genau einer Betriebssystemdatei speichern
- eine oder mehrere Dateien durch das Betriebssystem an und verwaltet Relationen und Zugriffspfade selbst innerhalb dieser Dateien
- DBSystem steuert selbst die Magnetplatte an und arbeitet mit den Blöcken in ihrer Ursprungsform
	- DBSystem hat quasi ein eigenes Dateisystem

Warum nicht immer Betriebsystemdatein?
- Betriebssystemunabhängigkeit
- Betriebssystemseitige Pufferverwaltung genügt nicht den Anforderungen

## Blocken
-> Datensätze in die Blöcke einpassen
#### Satzlänge: 
- variabel: höherer Verwaltungsaufwand beim Lesen und Schreiben
- fest: höherer Speicheraufwand

#### Verteilung auf Seiten:
- Nichtspannsatz: jeder Datensatz in maximal einem Block
- Spannsatz: Datensatz eventuell in mehreren Blöcken
Nichtspannsätze sind üblich

#### Fixiert:
- Fixiert: Datensätze sind an ihre Position gebunden
	- Beim Verschieben müssen alle Verweise auf diese Daten gefunden und geändert werden
- Unfixiert: werden an einer Zentrale Stelle auf die derzeit aktuelle Adresse umgesetzt 
	- Beim Verschieben nur eine Adresse ändern
### Struktur einer Seite
![[Pasted image 20260430103225.png]]Tupel können über (Seitennummer, Offset), also der relativen Adresse in Bytes vom Seitenanfang, addressiert werden

Die Seitennummer besteht aus der Angabe des Speichermediums, des Zylinders, der Spur und
der Nummer des Blocks

Bottleneck ist der Seitenzugriff auf dem Hintergrundspeicher (Zugriffslücke)

### Speichern von Datensätzen variabler Länge
Strategie a):
- Jeder Datensatz variabler länge beginnt mit Längenanzeiger
![[Pasted image 20260430113234.png|600]]

Strategie b): 
![[Pasted image 20260430113437.png|600]]
Vorteil: leichtere Navigation innerhalb des Satzes

### Tupelidentifikator (TID) Addressierung
Adresse besteht aus:
- Seitennummer
- Offset
	- verweist auf den i-ten Eintrag in einer Liste von Tupelzeigern (sog. Satzverzeichnis), die am Anfang der Seite stehen
Vorteil: 
- Verschieben auf der Seite verändert nur Seite und nichts außenherum, da nur der Eintrag in Satzverzeichnis verändert werden muss

## Large Objects
eg. BLOBS (Binary Large Objects)
Werden in Datenbank selbst abgelegt, nicht mehr im Dateisystem

## Kompression von Daten
Run-Length Encoding
Delta Encoding
- Differenz zwischen Werten speichern
- Macht nur Sinn wenn sich Werte weniger unterscheiden als sie groß sind
Bit-Vector Encoding
- Für jeden Wert der Spalte einen Bitstring 
- ![[Pasted image 20260430120540.png]]
- macht nur Sinn wenn es wenig unterschiedliche Werte gibt
Dictionary Encoding
- ![[Pasted image 20260430120717.png]]
- Sinnvoll wenn einzelne Werte häufiger vorkommen