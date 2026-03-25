## Hough-Transformationen
Ziel: Linien finden in einem Kantenbild
> Kantenbild: Bild das nur aus (1-Pixel) breiten Kanten besteht -> keine Ausgefüllten Flächen

Linien können mit Polar Koordinaten $(r, \theta)$ dargestellt werden
![[Polar Coordinates for Lines.png|300]]

Für jeden Pixel in dem Kantenbild werden alle möglichen Geraden die durch diesen Pixel gehen in den Hough-Raum ($r_{max} \times 180°$) eingetragen. 
Danach wird durch Statistische Überhöhung eine Peak-Suche durchgeführt.
Durch die Rücktransformation wird dann die Gerade wieder im Bild angezeigt.

Kann erweitert werden um viele verschiedene Formen zu erkennen. Kreise zum Beispiel brauchen einen 3D Raum ($r, m_x, m_y$)

Beliebige Formeln (wie ein Panzer) können erkannt werden in dem der Panzer mit $n$ Parametern vordefiniert wird und dann jeder mögliche Panzer in einem Pixel in den $n$-Dimensionalen Hough-Raum eingetragen wird. 

## Harris Corner Detection
Idee: Pixel im Bild finden, die zwei starke Gradienten haben. Also z.B. einen signifikanten Anstieg der Helligkeit in zwei Richtungen.

> **Lokale Strukturmatrix:** 
>$$M =
\begin{pmatrix}
\frac{\partial^{2}}{\partial x^{2}} &
\frac{\partial}{\partial x}\frac{\partial}{\partial y} \\[6pt]
\frac{\partial}{\partial y}\frac{\partial}{\partial x} &
\frac{\partial^{2}}{\partial y^{2}}
\end{pmatrix}$$
  wobei $\frac{\partial}{\partial x}$ dem horizontalen Sobel Operator entspricht.
>
> Sie fasst zusammen wie sich die Helligkeit eines Bildes um einen Pixel herum verändert

> **Eigenwerte von M**: 
> Wie stark sich das Bild in zwei senkrechte Hauptrichtungen verändert.

Um zu erkennen ob ein Pixel eine Ecke ist muss die Lokale Struktur Matrix an diesem Pixel berechnet werden. $\lambda_1, \lambda_2$ sind die Eigenwerte dieser Matrix. 
Wenn beide Eigenwerte groß sind, dann ist eine Ecke vorhanden. Ist ein Wert deutlich größer als der andere dann liegt eine Kante vor.

![[Harris_Corner_Detection.png|400]]

Die Berechnung der Eigenwerte für jeden Pixel braucht zu viel Rechenzeit. Deswegen wird eine Cornerresponse Function als Approximation verwendet, diese Berechnet nicht direkt die Eigenwerte.
$$R = det(M)- k \cdot (spur(M)^2)$$
Kante: $R<0$
Corner: $R>0$
Homogen: $R \approx 0$

k ist ein empirischer Parameter
