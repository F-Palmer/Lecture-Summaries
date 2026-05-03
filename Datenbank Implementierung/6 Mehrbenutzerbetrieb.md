- Lost Update
- Dirty Read
	- TA liest den Wert einer laufenden Transaktion, die später mit einem Rollback abbricht
- Incorrect Summary
	- Während eine TA eine Summe über mehrere Zeilen ausrechnet schreibt eine andere Transaktion Werte um

## ACID
**Atomizität**:
TA erscheint anderen TAs unsichtbar (atomar) , Abbrüche haben keinerlei Effekt

**Konsistenz**:
Jede TA hinterläßt die Datenbank in einem konsistenten Zustand

**Isolation**:
TAs dürfen sich nicht gegenseitig beeinflussen, sondern müssen isoliert ablaufen

**Dauerhaftigkeit**:
Auch bei einem Programmabbruch oder Systemabsturz müssen die Daten einer abgeschlossenen Transaktion erhalten bleiben

## Locking
Zugriffsobjekte: Ganze Tabelle oder Index, Mehrere Pages, Eine Page, Datensatz
Die einzeln gelockt werden

### Locking Scheduler
Erhöht oder reduziert Lock Granularität
Nutzt spezielle Locking Tabellen, die gelockte Objekte und Lockarten enthalten
Hält Transaktionen an bzw. gibt sie frei

> Optimistische Transaktionskontrolle:
> Transaktion wird immer ausgeführt, erst bei Commit wird entschieden ob sie durchgeht oder zurückgerollt wird
> -> schnell aber anfällig
> -> wird nur bei wenigen Locks genutzt

> Pessimistische Transaktionskontrolle: 
> Erst wird geprüft ob Locks bestehen, nur bei Konfliktfreiheit startet Transaktion
> -> langsamer aber sicherer
> -> wird genutzt wenn häufige Konkurrenzsituationen entstehen

> Semi Optimistisch: 
> abhängig von historischem Zugriff

### Zwei-Phasen-Sperrprotokoll
1. Jedes Objekt das benutzt werden soll, wird gesperrt
2. Eine Sperre darf nicht zwei mal angefordert werden
3. Eine Transaktion muss die Sperren anderer Transaktionen auf ein Objekt beachten
4. Zwei Phasen:
	1. Wachstumsphase, in der sie Sperren anfordern, aber keine freigeben kann
	2. Schrumpfungsphase, in der sie ihre bisher erworbenen Sperren freigibt, aber keine weiteren anfordern darf
5. Bei Transaktionsende muss eine Transaktion alle ihre Sperren zurückgeben


Wenn eine Transaktion einen Rollback ausführt, kann die anderen einen dirty read gelesen haben -> muss dann auch gerollbackt werden.
-> kaskadierender Rollback

Vermeidbar durch strenges Zwei-Phasen-Sperrprotokoll:
- alle Sperren werden auf einen Schlag erst zum Ende der Transaktion freigegeben
- Keine Schurmpfungsphase 

### Dead-Locks
Deadlock Erkennung: 
1. Timeout
	- Nach einer festgelegter Dauer ohne Veränderungen, wird ein Deadlock angenommen
	- Eine betroffene Transaktion wird zurückgesetzt und später erneut gestartet
		- Wound-Wait: jüngere TA wird zurückgesetzt
		- Wait-Die: ältere TA wird zurückgesetzt
2. Zentralisierte Deadlock-Erkennung
	- Stationen (ein Rechner des Verteilten Systems) melden wenn sie auf einen Un-Lock warten
	- Melden das an einen Zentralen Knoten der einen Wartegraph aufbaut
	- Zyklus -> Deadlock
3. Dezentrale Deadlock-Erkennung
	- An den einzelnen Stationen werden lokale Wartegraphen geführt -> Lokale Deadlocks

