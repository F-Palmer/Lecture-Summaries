möglichst schnelle Anfragebearbeitung = möglichst wenig Seitenzugriffe

Teilziele der Optimierung: 
1. Selektion soll so früh wie möglich erfolgen
2. Basisoperationen zusammenfassen
	- Ohne Zwischenspeicherung von Zwischenergebnissen
3. Nur Berechnungen ausführen die das Gesamtergebnis beeinflussen
	- keine Redundante Operationen und nachweisbar leere Zwischenrelationen berechnen
4. Gleiche Teilausdrücke zusammenfassen

## Phasen der Optimierung
1. **Logische Optimierung**
- Anfrageterm der Relationalen Algebra wird umgeformt
- z.B. Selection so weit wie möglich nach innen schieben (1. Teilziel)

2. **Physische Optimierung**: 
- Zugriffspläne werden aus dem ungeformten Ausdruck erzeugt
- Braucht Informationen über die Indexstrukturen

3. Kostenbasierte Auswahl: 
- Auswahl aus mehreren alternativen Plänen
- Basierend auf gespeicherten statistischen Informationen
	- Kostenfunktionen zur Abschätzung der Kosten von Operationen
	- Statistiken über die Größe der Relationen

Hier kommt ein 30 Folien Beispiel, in Altklausuren nachschauen ob relevant