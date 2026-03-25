> **Stetigkeit einer Funktion**:
> Eine Funktion heißt auf einem Intervall stetig, wenn $f$:
> - in jedem Punkt stetig ist 
> - falls Randpunkte zu dem Intervall gehören, müssen diese links- und rechtsseitig sein.
### Stetigkeit mit Hilfe des Folgekriteriums
> $f: D \to \mathbb{R}$ ist stetig in $x_0$, wenn für jede Folge {$x_k$} mit Elementen aus $D$, die gegen $x_0$ konvergiert, auch $f(x_k)$ gegen $f(x_0)$ konvergiert.

**Die Idee:** 
Das Ziel ist zu beweisen ob $f$ an der Stelle $x_0$ stetig ist.
Wenn man mit Zahlen aus dem Definitionsbereich immer näher an $x_0$ herangeht, dann müssen die Funktionswerte automatisch immer näher an $f(x_0)$ herangehen.
Man wählt also eine Folge $x_k$ die gegen diesen Wert konvergiert und setzt diese Folge für $x$ in $f(x)$. Lässt man nun die Folge gegen unendlich laufen, was kommt raus? 
Ist es das gleiche was bei $f(x_0)$ raus kommt? Wenn ja, dann ist die Funktion an dieser Stelle stetig.

**Positiv Beispiel:**
$f(x) = x^2; \space x_0 = 2$ 
Man wählt zum Beispiel die Folge: 
$$x_k = 2+ \frac{1}{k}$$
$$
\begin{align*}
f(x_k) &= (2+\frac{1}{k})^2 \\
\lim_{k\to\infty} (2+\frac{1}{k})^2 &= 4 \\
f(2) &= 4
\end{align*}$$
**Negativ Beispiel**:
$$\begin{align*}
f(x)&=
\begin{cases}
0, & \text{für } x \neq 0, \\
1, & \text{für } x = 0
\end{cases} \\
x_0 &= 1
\end{align*}$$
Folge: 
$$x_k = \frac{1}{k}$$
$$\begin{align*}
\lim_{k\to\infty} f(x_k) &= 0^* \\
f(0) &= 1 
\end{align*}$$
$^*$Ist 0, da es nie in den Fall $x=0$ auftritt sondern immer nur sehr nah daran

**Anmerkungen Stetigkeit:**
Der Stetigkeitsbegriff gilt nur auf dem Definitionsbereich. Außerhalb ist die Funktion weder stetig noch unstetig.
Elementare Funktionen sind dort wo sie definiert sind auch stetig.


**Wann das Kriterium nicht funktioniert**:
$$f(x) = \begin{cases}
0, & \text{für ein irrationales } x > 0, \\
\frac{1}{q}, & \text{für ein rationales } x > 0 \text{ der Form: } x = \frac{p}{q}
\end{cases}$$
An rationalen Stellen unstetig und an den irrationalen Stellen stetig.
1. Rationale Stelle
	 Folge: $x_k = x_0 + \frac{\sqrt2}{k}$ 
	 $f(x_0 + \frac{\sqrt2}{k}) = 0$ da $\sqrt2$ das Ergebnis immer irrational macht
	 $f(x_0) = 1$ da $x_0$ rational ist
	 -> unstetig
2. Irrationale Stelle
	Je näher man der irrationalen Stelle kommt desto genauer muss man den Wert beschreiben. Somit muss $q$ größer werden und $1/q$ strebt gegen 0.
	-> stetig

### Stetigkeit mit Hilfe des Epsilon-Delta-Kriteriums
> $f: D \to \mathbb{R}$ ist in $x_0 \in D$ stetig, wenn zu jedem $\epsilon > 0$ ein $\delta >0$ existiert, so dass für alle $x \in D$ mit $|x-x_0| < \delta$ stets $|f(x)-f(x_0)| <\epsilon$ gilt.

Egal wie nah man an $f(x_0)$ dran sein möchte ($\epsilon$), muss das immer mit einem $\delta$ (Wie nah man dafür an $x_0$ bleiben muss) funktionieren.
![[Epsilon-Delta-Kriterium.png]]

### Links und rechtsseitige Stetigkeit
> **Rechtsseite Stetigkeit**: 
> Eine (mindestens!) in einem Intervall $[x_0, x_0 +c]; \space c>0$ definierte Funktion $f$ heißt an der Stelle $x_0$ rechtsseitig stetig, wenn: 
> $$\lim_{x\to x_0+0^*} f(x) = f(x_0)$$
> $^*$von rechts an den Wert herangehen

## Unstetigkeit
1) Die links- und rechtsseitigen Grenzwerte sind gleich. 
   Hebbare Definitionslücke (in $x_0$ nicht definiert) oder hebbare Unstetigkeit ($f(x_0)$ weicht von links- und rechtsseitigen Grenzwerten ab)
2) Die links- und rechtsseitigen Grenzwerte existieren, sind aber unterschiedlich. 
   Durch einen Sprung an $x_0$
3) Einer der links- oder rechtsseitigen Grenzwerte divergiert $$f(x) = \begin{cases}
1, & \text{für } x\geq 0, \\
\ln x & \text{für } x > 0
\end{cases}$$
4) Bei links- und rechtsseitiger Näherung ist $f$ unbestimmt divergent
	-> oszillatorische Unstetigkeitsstelle 
   Beispiel: $sin\frac{1}{x}$

## Lipschitz-Stetigkeit
>Erfüllt $f$ auf dem Intervall $I$ die Liebschitzbedingung $$\forall x_1,x_2 \in I : ||f(x_1)-f(x_2)|| \leq L||x_1-x_2||$$
so heißt $f$ auf $I$ Lipschitz-stetig. 

$L$ ist eine Konstante, die nicht von $x_1$ und $x_2$ abhängt. So viel darf sich $f$ maximal ändern, wenn $x$ sich um 1 ändert.

Lipschitz-Stetigkeit garantiert kleine Änderungen des Ausgangs bei kleinen Änderungen des Eingangs. 
Lipschitz-Stetige Funktionen sind fast überall differenzierbar. 

Bedingung ist nicht erfüllt wenn:
- nicht stetig 
- unendlicher Anstieg
- unbeschränkte Variation z.B. $\sin \frac{1}{x}$ 

## Differenzierbarkeit 
> **differenzierbar in $x_0$**: 
> Eine Funktion $f$ heißt in $x_0$ differenzierbar wenn der folgende Grenzwert existiert:$$f'(x_0) =\lim_{h\to 0}\frac{f(x_0+h)-f(x_0)}{h}$$
> Eine differenzierbare Funktion ist stetig, eine stetige Funktion ist nicht unbedingt differenzierbar.

> **rechtsseitig differenzierbar**: 
> $$f'_{+0}(x_0)$$

> **differenzierbar in $I$**:
> Eine auf einem Intervall definierten Funktion $f$ heißt auf $I$ differenzierbar, wenn 
> - $f$ in jedem inneren Punkt von $I$ differenzierbar ist
> - an Randpunkten links- bzw. rechtsseitig differenzierbar ist

> **Weierstraß-Funktion**:
> $$f(x) = \sum_{k=0}^\infty (\frac{2}{3})^k \sin(2^kx)$$
> Eine Funktion die an Stellen stetig ist, aber nirgends differenzierbar ist.

### Partielle Ableitung
