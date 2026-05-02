Lösen von DGLs für eine beliebige rechte Seite $f(x)$.

> Dirac-Delta-Funktion:
> $\delta (x-y)$ 
> eine unendlich schmale, unendlich hohe Funktion am Punkt y (Punktquelle), mit der Gesamtfläche 1

Beispiel: $-u'' = f$

$G(x,y)$ (die Greensche Funktion) beschreibt, wie sich das System an Stelle x verhält, wenn es an Stelle y angestupst wird
$$-G''(x,y) = \delta(x-y)$$
Jede Funktion $f$ kann als Summe von vielen Punktlasten gedacht werden: 
$$f(x) = \int_\Omega f(y)\delta(x-y)dy$$
Wenn $G(x,y)$ die Antwort auf eine Punktlast bei y ist, dann ist auf Grund des Superpositionsprinzips die Gesamtlösung: 
$$u(x)= \int_\Omega G(x,y)f(y)dy$$
![[Green.pdf]]