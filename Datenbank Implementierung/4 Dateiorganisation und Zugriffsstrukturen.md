> **Dateiorganisationsform**: 
> Grundlegende Dateiorganisationsform (ohne Index)
> Also der Unterschied zwischen:
> - unsortierter Speicherung (Heap-Organisation)
> - sortierte Speicherung (Sequenzielle Organisation)
> - gestreute Speicherung (Hash-Organisation)

> **Zugriffspfad**: 
> jede Zugriffsstruktur die über die grundlegende Dateiorganisationsform hinaus geht
> eg Indizes


## Indizes
Ohne Index muss statistisch gesehen die Hälfte aller Datensätze durchsucht werden bis zum Treffer

> **Composite Index**: 
> Ein Index der über eine Kombination von Spalten geht

#### Primär vs Sekundärschlüssel
Primärschlüssel: 
- Duplikatfreiheit der zugeordneten Attributwerte
- Verknüpfung von Relationen
Sekundärschlüssel: 
- Nicht unbedingt eindeutig
- Sehr sinnvoll zur Unterstützung bestimmter Aufgaben

#### Primärindex vs Sekundärindex
Pro interne Relation ein Primärindex, mehrere Sekundärindexe
Ein Primärindex ist ein Zugriffspfad auf die interne Relation
Primärindex über Primärschlüssel definiert

Sekundärindex wird auf Sekundärschlüssel aufgebaut
- mehrere Sekundärindizes pro Tabelle möglich
- Einträge im Index verweisen auf Pointer die dann auf die eigentlich Datensätze verweisen
- Wenn keine Sortierung nach zb. ID in der Datenbank vorliegt, muss ein Sekundärindex verwendet werden -> Einige kommerzielle relationale DBSysteme nutzen in der Regel nur Sekundärindexe als Zugriffspfad (Postgres und irgendwas von IBM)

#### Dünn vs Dicht besetzter Index
Dicht besetzt: 
- Für jeden Datensatz einen Eintrag in der Indexdatei
- Ermöglicht die Bearbeitung einiger Anfragen ohne Zugriff auf die gespeicherten Tupel
	(Index braucht weniger Speicherplatz als die Daten -> bessere Antwortzeiten)
Dünn besetzt: 
- Ein Eintrag in der Indexdatei pro Speicherseite (für den kleinsten Schlüsselwert dieser Seite)
- Funktioniert nur wenn die Daten physisch sortiert gespeichert sind
- Index sieht so aus: 
```
(K1=10, S1) für Seite 1 mit dem kleinsten Schlüssel 10
(K2=25), S2) Verweis auf Seitenanführer der Nachfolgeseite
```
- Sucht man den Datensatz mit ID=13 muss er auf S1 zu finden sein

#### Geclusterter vs. nicht-geclusterter Index 
Geclusterter Index: 
- physisch in derselben Reihenfolge gespeichert wie der Index
	-> Pro Tabelle nur ein geclusterter Index möglich
- Entspricht dem Primärindex (meistens)
	- Es ist technisch möglich Daten nach einem nicht-primärschlüssen zu sortieren, dann ist es ein geclusterter secundärindex
Nicht geclusterter Index:
- Anders sortiert als die Relation

## Speicherformen 
#### Statische vs. Dynamische Strukturen
Statisch:
- Struktur wird einmalig aufgebaut und ist auf eine bestimmte Datenmenge ausgelegt
- Sie verändert ihre grundlegende Form nicht
- Optimal nur bei fester Anzahl von Datensätzen
Dynamisch: 
- Struktur passt sich automatisch an wachsende oder schrumpfende Datenmengen an
- ohne Reorganisation
- In DBMS typisch

![[Pasted image 20260501111911.png]]

#### Heap-Organisation
Datensätze werden unsortiert auf einen Stapel gelegt
Physische Reihenfolge der Datensätze = Zeitliche Reihenfolge der Aufnahme in die Datenbank

INSERT: 
- Erfordert Zugriff auf letzte Seite der Datei
- Letzte Seite pro Datei in Data Dictionary festhalten

DELETE: 
- Lookup um den zu löschenden Satz zu löschen
- Im Header des Datensatzes Löschbit auf 0 setzten

LOOKUP: 
- Erfordert ein sequenzielles Durchsuchen der Gesamtdatei
- Aufwand kann durch Index reduziert werden

| Vorteile                                                                   | Nachteile                                  |
| -------------------------------------------------------------------------- | ------------------------------------------ |
| - extrem schneller INSERT<br>- Bei INSERT muss nie etwas verschoben werden | - Maximaler Aufwand beim LOOKUP und DELETE |
#### Sequenzielle Speicherung
Datensätze werden sortiert abgelegt
Sinnvollerweise nach Primärschlüssel

INSERT
- Sortierung muss eingehalten werden
- erst Seite suchen, auf der der Datensatz eingefügt werden soll
- Datensatz zwischen zwei exisitierenden Datensätzen einsortieren
	- nachfolgende Datensätze verschieben
	- Offset des TID-Zeigers verändern
- Schneller machen indem beim Anlegen auf jeder Seite Platz gelassen wird

DELETE
- Lookup um den zu löschenden Satz zu löschen
- Im Header des Datensatzes Löschbit auf 0 setzten

LOOKUP
- Schneller als Heap durch Sortierung

#### Indexsequenzielle Dateiorganisation
- Sequenzielle Dateiorganisation mit Indexdatei über dem Sortierattribut
- Sortierung der Hauptdatei und die Sortierung der Indexdatei sind gleich
- Dünner Index sinnvoll
![[Pasted image 20260501122538.png]]

Problem: stark wachsende Datenmengen
Indexdatei kann verschiednen Seiten bestehen und muss sequenziell durchsucht werden
-> Mehrstufiger Index (Baumstruktur an Indizes)
![[Pasted image 20260501122937.png|500]]

LOOKUP:
1. Indexdatei sequenziell durchlaufen
	- Finde den größten Indexeintrag (Ki, Si) mit $Ki \leq K$
2. Seite Si sequenziell durchsuchen
	- Datensatz gefunden oder nicht vorhanden

INSERT: 
- Mit LOOKUP passende Seite finden
- Falls genug Platz: 
	- Satz wird an der gefundenen Stelle eingefügt
- Falls kein Platz: 
	- Neue Seite hohlen
	- Sätze der vollen Seite gleichmäßig auf die beiden Seiten verteilen
	- Indexeintrag auf neue Seite erstellen

DELETE:
- Mit LOOKUP passende Seite finden
- Satz auf Seite löschen (Löschbit auf 0)
- Falls, erster Satz auf Seite: 
	- Index anpassen
- Falls, Seite nach löschen leer:
	- Seite zurückgeben, Index anpassen

#### Indexiert-nichtsequentieller Zugriffspfad
Datensätze sind nicht sortiert gespeichert
Dichter Index
Nur Direktzugriff sinnvoll
Einfügen einfach, da keine Sortierung


### Clustered Tables
Physische Anordnung von Datensätzen hängt von den Fremdschlüsselbeziehungen ab
Zusammengehörende Datensätze liegen auf einer Seite beinander

KUNDE – KundeNo – BESTELLUNG –ArtNo -- ARTIKEL
 “welcher Kunde hat was bestellt…” mit einem IO 

### Hash Verfahren
SUCHEN:
- aus Suchschlüssel Hashwert berechnen
- Hashwert bestimmt Bucket des gesuchten Datenobjektes
- Bei Kollision müssen der Suchschlüssel direkt mit den mehreren Ergebnissen den Hashs verglichen werden

Schlüsselwerte werden mit auf Bucket-Adressen abgebildet
Bucket = Speicherbereich von ein oder mehreren Seiten
Kollision häufig, da zum Beispiel Modulo aus Hash verwendet wird
 -> Overflow Seiten sind wichtig (bei Lookup müssen diese durchsucht werden, beim einfügen muss auf die erste freie Overflow seite geschrieben werden)

Leistungsfähigkeit stark abhängig von Hashfunktion
Schlechte Wahl kann fast alle Datensätze auf die gleiche Seite einordnen
Bei Änderung der Hash Funktion müssen alle Daten neu gehashed werden

#### Dynamische Hashing
Hashfunktionen mit feste Berechnungsvorschrift, aber deren Bildbereich dynamisch vergrößert werden kann
Kein komplettes Neu-Hashen erforderlich