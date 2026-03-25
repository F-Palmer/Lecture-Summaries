> **FEM (Finite Elemente Methode)**:
> ein numerisches Näherungsverfahren
> Das gängigste Verfahren zur Berechnung und Simulation komplexer physikalischer Probleme
> 
## Anwendungsgebiete
komplexes Materialverfahren simulieren
Materialien unter verschiedenen Belastungen und Umgebungsbedingungen simulieren
#### Mechanische Probleme:
Strukturanalyse von Materialien
#### Thermische Analyse:
Simulation von Wärmefluss und Temperaturverteilung
#### Strömungsanalyse
Wärmeübertragung und der Flüssigkeitsfluss um oder durch Materialien

## Vorteile
- detaillierte Einblicke in das Verhalten komplexer Systeme
- weniger physikalische Tests

## Grobes Vorgehen
Aufteilen des komplexen Problems in viele kleine Probleme (Diskretisierung)
Lösen der einzelnen Probleme durch Analyse des Verhaltens jedes einzelnen Elements 
Zusammensetzung der kleinen Lösungen


## FEM-Analyse
![[Pasted image 20260306181400.png]]
Idealisierung: Vereinfachung des CAD Models an Stellen die nicht für die Berechnung benötigt werden

### Fehler bei der FEM-Analyse
- Model zu weit von Realität weg
- Unrealistische Randbedingungnen
- nicht aufeinanderliegende Knoten 
- windschiefe Linien

## Meshing
> **Diskretisierung**:
> Aufteilung der Struktur viele Elemente deren Verhalten exakt oder näherungsweise bekannt sind
> Dieses Elemente sind durch Knoten verbunden
> -> Netz/ Mesh

Elemente können 1/2/3-Dimensional sein

#### Mesh Typen
> **strukturiertes Mesh:**
> regelmäßige Elementstruktur
> hohe numerische Genauigkeit
> schwer umzusetzten bei komplexen Geometrien

> **unstrukturiertes Mesh**: 
> flexible Elementanordnung
> gut für komplexe Bauteile
> schlechte numerische Genauigkeit
> häufig bei automatischer Netzgenerierung

## Freiheitsgrade (DOF)
**Freiheitsgrad eines Elements:** 
	Anzahl unabhängiger Parameter
	Also alle Verschiebemöglichkeiten und andere Variablen eines Knotens
	2D:
		Verschiebung: in x und y Richtung: 2
		Drehung: um die z Achse: 1
	3D:
		Verschiebung in x, y und z Richtung: 3
		Drehung: um die x, y und z Achse: 3 

**Gesamtfreiheit**: 
	Summe aller Knotenfreiheitsgrade

