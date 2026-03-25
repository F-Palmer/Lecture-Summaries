(Linear verschiebungsinvariante Operatoren)

## Faltung 
$$I' = I * H$$
$$I'(u,v) = \sum_{i=-\infty}^\infty \sum_{j=-\infty}^\infty I(u-i, v-j) * H(i,j)$$
H: Filterfunktion
I' neues Bild
-> Gespiegelt!!


- Kommutativ
- Assoziativ
- Distributiv

Beispiele: 
- Mittelwert-Filter 
- Sobel
Negativ Beispiel: 
- Medianfilter

## Problembeispiel:
Durchmesser von Objekt messen
Idee: 
- Helligkeit im Bild messen
- erste zweite Ableitung bilden 
- Abstand zwischen Nullpunkten ist Durchmesser
-> funktioniert nicht wegen Noise

## Diskrete Ableitungen in 2D
Horizontale Ableitung (bei vertikalen wird n verändert)
Ableitung in x-Richtung des Bildes
$I'_x(m,n) = I(m+1,n) - I(m,n)$
-> Vorwärtsdifferenz 
$I'_x(m,n) = I(m,n) - I(m-1,n)$
-> Rückwärtsdifferenz

#### Faltungsoperatoren
**Horizontale Ableitung:**
$$h'_x =
\begin{bmatrix}
1 & -1 \\
\end{bmatrix}$$
kommt von der Vorwärtsdifferenz
wird bei der Berechnung gespiegelt

**Zweite Ableitung horizontale:**
$$
h_x'' = \begin{bmatrix}
1 & -1 \\
\end{bmatrix} * \begin{bmatrix}
1 & -1 \\
\end{bmatrix} = \begin{bmatrix}
1 & -2 & 1 \\
\end{bmatrix} $$

**2D Laplace Operator:** 
$$
h_x'' = \begin{bmatrix}
1 & -2 & 1 \\
\end{bmatrix} + \begin{bmatrix}
1\\
-2\\
1\\
\end{bmatrix} = \begin{bmatrix}
0 & 1 & 0 \\
1 & -4 & 1 \\
0 & 1 & 0 \\
\end{bmatrix} $$
-> Kantenverstärker

**Mittlungsoperator:**
$$\frac{1}{9}\begin{bmatrix}
1 & 1 & 1 \\
1 & 1 & 1 \\
1& 1 & 1 \\
\end{bmatrix} $$
-> Der soll auch irgendwie nicht gut sein
-> Mexican Hat ist besser

**Zentrale Differenz:** 
$$I_m'^{cd} = c =\begin{bmatrix}
1 & 0 & -1 \\
\end{bmatrix}$$
zentrale approximation der Ableitung
- genauer als Vorwärts- und Rückwertsdifferenzen
- keine Verzerrung in eine Richtung 

Steigt das Signal nach rechts -> positiv
Fällt das Signal nach rechts -> negativ
gleich bleibend = 0
(ist so weil das ja umgedreht wird... aus Gründen)

**Binomialfilter:** 
$B_x = \begin{bmatrix}1  & 1 \\ \end{bmatrix}$
$B_x^2 = \begin{bmatrix}1  & 2 & 1 \\ \end{bmatrix}$

**Previtt:** 
$$\begin{bmatrix}
1 & 0 & -1 \\
1 & 0 & -1 \\
1& 0& -1 \\
\end{bmatrix} $$
benutzt kein Mensch

**Sobel:** 
Kombi aus Zentraler Differenz und Binomialfilter
$$S_x = \begin{bmatrix}
1 & 0 & -1 \\
2 & 0 & -2 \\
1& 0& -1 \\
\end{bmatrix} $$
Mittel in y und Ableitung in x

**Nicht linearer Median Filter:**

Median aller Werte in 3x3 Bereich

**Diagonale Ableitung**
$$R_x = \begin{bmatrix}
0 & 1 \\
-1& 0 \\
\end{bmatrix} \\
R_y = \begin{bmatrix}
1 & 0 \\
0& -1 \\
\end{bmatrix} $$
**LoG-Filter** -> Laplace of Gaussion
Zwei Schritte (geht auch als einzelner Kernel):
1. Gaußglättung
2. Laplace Operator zur Kantenerkennung
4er Laplace ist weniger Noise empfindlich
Kombinierter Kernel:
$$\begin{bmatrix}
0 & 0 & -1 & 0 & 0 \\
0 & -1 & -2 & -1 & 0 \\
-1 & -2 & 16 & -2 & -1 \\
0 & -1 & -2 & -1 & 0 \\
0 & 0 & -1 & 0 & 0
\end{bmatrix}$$


### Problem der Bildränder

1) Rand nicht rechnen
2) Äußeren Rand mit 0en ergänzen
3) Verdopplung des Randes
4) Extrapolation
5) Zyklische Vertauschung