_(Vorverarbeitung)_

### Running Length
$$5;5;5;5;6 = 4*5; 6$$
### Huffman
Verlustfreies Kompressionsverfahren
"Häufige Zeichen bekommen kurze Codes, seltene Zeichen lange"
1. Wie oft kommt jedes Zeichen vor?
2. Binärbaum erstellen 
	1. Zeichen nach Häufigkeiten sortieren
	2. While nicht alle Zeichen im Baum sind
		1. Suche das Zeichenpaar (können auch schon Verbundene Zeichenpaare sein) mit den kleinsten Wahrscheinlichkeiten
		2. Verbinde das Paar

Beispiel: 
![[Huffman_Erklärung.png]]

### JPEG
Verlustbehaftete Kompressionsverfahren

#### 1. Schritt: Farbtransformation
RGB -> YCbCr / LCbCr (weil Lausen dumm ist)
>**YCbCr**
>Y: Helligkeit
>Cb: Blau-Farbabweichung
>Cr: Rot-Farbabweichung

50% Datenreduktion durch ungenauere Farbauflösung

#### 2. Schritt: Subbilder
Bild in 8x8 aufteilen

#### 3. Schritt: Shift
Werte im Bild (Graustufen/ Oder YCbCr) haben Pixelwerte zwischen 0-255
Der nächste Schritt funktioniert am besten mit 0-zentrierten Werten
-> Schift um -128

#### 4. Schritt: Diskrete Kosinustransformation
Wandelt die Pixelwerte in Frequenzen um:
- Man versucht aus mit Kosinusfunktionen die Pixelwertmatrix abzubilden.
	-> wenig Veränderung bei den Pixelwerten -> kleine Frequenz der Cos
Kein Informationsverlust

#### 5. Schritt: Quantisierung
Eigentlicher Kompressionschritt
DCT-Koeffizienten werden durch Quantisierungsmatrix geteilt und gerundet
- Feine Details (Höhere Frequenzen) bekommen größere Teilungswerte -> stark reduziert oder gelöscht

#### 6. Schritt: Entropie-Kodierung
Gerundete Werte mit vielen nullen werden codiert: 
- Zickzack-Lesereihenfolge -> gruppiert Nullen zusammen
- Lauflängen oder Huffman Kodierung
Kein Informationsverlust

### JPEG Artefakte
1. Blockartefakte
	- Nach starker Quantisierung können die Grid Kanten sichtbar werden
	- bei nicht natürlichen Bildern entsteht mehr
2. Farbverfälschung
	- Farbauflösung wird reduziert
3. Quantisierungsrauschen
	- Durch starke Quantisierung gehen Details verloren

## Histogram def 
Statistik über die Besetzung von Helligkeitsklassen

Kontrastspreizung:
$$I_{\text{out}} = \frac{I_{\text{in}} - I_{\min}}{I_{\max} - I_{\min}} \cdot 255$$



