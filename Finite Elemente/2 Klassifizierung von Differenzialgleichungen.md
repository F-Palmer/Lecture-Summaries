# Gewöhnliche Differenzialgleichungen (ODE)
> **ODE**:
> Gleichung aus einer unbekannten Funktion (einer einzelnen Variablen) und deren Ableitungen besteht
> Beispiel $y' = 2xy'$

Lösung einer ODE ist eine Funktion (oder Funktionsmenge), die bei Einsetzen der Funktion die Gleichung und ihre Ableitungen erfüllt

## Klassifizierung von ODEs
- Ordnung (höchste Ableitung)
- Linearität
	Einfach gesagt: eine ODE ist linear, wenn die gesuchte Funktion $y(x)$ und ihre Ableitungen nur in der ersten Potenz vorkommen und nicht miteinander multipliziert werden
	Beispiele:
	- $y' + y = 0$: linear
	- $y^2 = 0$ nicht linear
	- $yy' + y = 0$ nicht linear
	- $\frac{1}{y} = 0$ nicht linear
- Homogenität (Vorhandensein einer Störfunktion)
- variable vs. konstante Koeffizienten
	Koeffizienten einer ODE beschreiben wie die Ableitungen gewichtet werden
	Konstante Koeffizienten:
		Koeffizienten sind Konstanten
		Beispiel:
		-  $y'' + 3y' + 2y = 0$
	Variable Koeffizienten: 
		Koeffizienten hängen selbst von der unabhängigen Variablen ab
		Sind oft nur numerisch (oder als Reihe) lösbar
		Beispiel: 
		- $y'' +xy' +x^2y = 0$
- explizite vs. implizite Darstellung

## Lösungsmöglichkeiten

### Analytische Lösungsmöglichkeiten
- Trennung der Variablen
- Variation der Konstanten
- Laplace-Transformation
- Substitution

### Numerische Lösungsmöglichkeiten
- Euler
- Heun 
- Runge-Kutta

> **Anfangswertproblem** (AWP): 
> Lösungen müssen zusätzliche Bedingungen an einem Punkt erfüllen
> "Anfang" weil der gegebene Wert häufig der Anfang des modellierten Prozesses ist, wie zum Beispiel "Ein Ball wird losgeworfen" $y(0) = 1, y'(0) = 5$
> 

> **Randwertprobleme** (RWP):
> Bedingungen werden an den Rändern eines Intervalls festgelegt
> Unterschied zu AWP, ist dass nur $y(x)$ an den Punkten gegeben ist

# Partielle Differentialgleichung (PDE)
> **PDE**:
> mathematische Gleichung, in der als Variablen eine unbekannte Funktion mit mehreren Veränderlichen sowie deren Ableitung auftreten
> Beispiel:
> $u(x,t) = u_{tt} -c^2*u_{xx} = 0$

## Klassifizierung
### Ordnung 
(Die höchste vorkommende Ableitung)
### Linearität
linear ⊂ semilinear ⊂ quasilinear ⊂ nichtlinear

**Linear**: 
Alle Koeffizienten hängen nur von den unabhängigen Variablen ab - nicht von $u$ oder den Ableitungen von $u$
Beispiel: 
$u_t = a \cdot u_{xx}$

**Semilinear**:
Die Koeffizienten der höchsten Ableitung sind wie bei linearen nur von unabhängigen Variablen abhängig.
Alle niedrigeren Terme dürfen nichtlinear in u sein.
Beispiel:
$u_t = u_{xx} + u^2$

**Quasilinear**: 
Die Koeffizienten der höchsten Ableitung dürfen von unabhängigen Variablen und niedrigeren Ableitungen abhängig sein.
Beispiel: 
$u_x\cdot u_{xx} + u_x^2 = 0$

**Nichtlinear**: 
Keine der anderen Strukturen liegt vor
Beispiel:
$u_x^2 + u = 0$

### Typ 2er Ordnung
Allgemeine Form einer PDE zweiter Ordnung in zwei Variablen:
$$A \cdot u_{xx} + B\cdot u_{xy} + C \cdot u_{yy} + ... = 0$$
> Satz von Schwarz:
> $u_{xy} = u_{yx}$
> Bei Stetigkeit

> Diskriminante: 
> $$D = B^2 - 4AC$$

| Diskriminante: | $D < 0$    | $D = 0$     | $D > 0$      |
| -------------- | ---------- | ----------- | ------------ |
| Definitheit:   | definit    | semidefinit | indefinit    |
| Typ:           | elliptisch | parabolisch | hyperbolisch |
Hinweis: Nur Homogenen Teil berücksichtigen. Und nur auf PDEs möglich, nicht auf ODEs
# Lösen von ODEs

## Trennung der Variablen
Beispielrechnung:
$$\begin{align*}
y' &=2x\cdot y \\
\frac{dy}{dx} &= 2x \cdot y \space | \space *dx * \frac{1}{y}\\
\int \frac{1}{y} dy &= \int2x dx \\
\ln y &= x^2 + C \\
y &= e^{x^2} + e^C
\end{align*}$$

$$y' = x^2 - \frac{x}{y}, y(1) = 1$$