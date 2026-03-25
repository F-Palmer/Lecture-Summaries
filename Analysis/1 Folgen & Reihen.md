> **Folge**:
> Eine Vorschrift, die jeder natürlichen Zahl $n$ eine reelle Zahl $a_n$ zuordnet
> $a_n = f(n); n\in \mathbb{N}$

> **Nullfolge**:
> Wenn zu jedem $\epsilon > 0$ ein Index $N$ existiert, so dass $|a_n| < \epsilon$ für alle $n >= N$
> $a_n$ konvergiert gegen null

> **Beschränkte Folge**:
> Die Folge hat eine obere und untere Schranke

> **Konvergenz einer Folge**:
> $|a_n - L| < \epsilon$ 
> Konvergenz gegen L
> Eine Folge ist konvergent gegen $L$ wenn $\{a_n - L\}$ eine Nullfolge ist

> **Majorante**:
> $a_n$ ist Majorante von $b_n$ wenn $\forall n: |b_n|<=|a_n|$ (Achtung Betrag!)
> Die Majorante ist immer größer oder gleich groß

> **Bestimmt divergent**:
> $\lim_{n -> \infty} n = \infty$ 

> **Unbestimmt divergent**:
> $\lim_{n -> \infty} \sin(n)$

> **Häufungspunkt**:
> Eine Zahl $a$ heißt Häufungspunkt, wenn in ihrer Epsilonumgebung unendlich viele Folgeglieder liegen.

> **Cauchy-Folge**:
> Eine Folge heißt Cauchy-Folge wenn es zu jedem $\epsilon$ ein Index $N$ gibt, so dass ab diesem Index alle Folgeglieder weniger als $\epsilon$ voneinander entfernt sind.

> **Bolzano's erstes Hauptkriterium**:
> Eine monotone und beschränkte Folge ist konvergent.

> Bolzano's zweites Hauptkriterium:
> Eine Folge konvergiert in den reellen Zahlen genau dann, wenn sie eine Cauchy-Folge ist.

> Cauchyscher Konvergenzsatz: 
> Es sei $\{A_n\}$ eine streng monoton wachsende, unbeschränkte Folge und {$a_n$} eine beliebige Folge. Dann gilt:
> $$\lim_{n \to \infty} \frac{a_{n+1} - a_n}{A_{n+1}-A_n} = g \Rightarrow \lim_{n \to \infty} \frac{a_n}{A_n} = g$$

## Beweisen dass $a_n$ eine Nullfolge ist

**Beispiel**: $\{ a_n\} = \{ \frac{1}{n}\}$ 
$\epsilon$ ist vorgegeben

$$|a_n -0| = \frac{1}{n}$$
$$\forall n>N: \frac{1}{n}< \epsilon => n>\frac{1}{\epsilon}$$
$$|a_n -0| = \frac{1}{n} < \frac{1}{N} < \epsilon$$
## Berechnung von Grenzwerten

1. Rückführung auf Nullfolgen
Man benötigt eine Vermutung was der Grenzwert a ist. 
-> Wenn $a$ ein Grenzwert ist, dann ist {$a_n-a$} eine Nullfolge.

2. Mit Rechenregeln (see [[_Analysis Formelsammlung#Limes Rechenregeln 1]])
Beispiel:
$$\lim_{n \to \infty} a_n = \lim_{n \to \infty} \frac{4n^3 - 6}{6n^3 + 2n} = \lim_{n \to \infty} \frac{4-6/n^3}{g+2/n^2} = \frac{4}{6}$$

3. Einschließungskriterien 
Wenn zwei Folgen auf den gleichen Wert konvergieren und immer größer bzw. kleiner sind als eine Folge $a_n$, dann konvergiert auch die Folge $a_n$ auf diesen Wert.
![[Einschließungskriterien.png]]
Wahl der oberen Schranke:
$$1+x^n \leq 1+|x^n| \leq 1+1 = 2$$
Wahl der unteren Schranke:
$$\begin{align*}
x^n \geq -|x|^n \geq -|x| \\
1+x^n \geq 1- |x|\\
1- |x| > 0
\end{align*}$$
4. Cauchyscher Konvergenzsatz
Eignet sich zur Berechnung von Grenzwerten, in denen $a_n$ eine Folge von Quotienten ist, oder für Folgen $\sqrt[n]{a_n}$ die auf Quotientenfolgen $a_{n+1}/{a_n}$ zurück geführt werden können.
**Beispiel**: 
Zeige: $$\lim_{n \to \infty} \frac{\sum_{k=1}^{n}k^p}{n^{p+1}} = \frac{1}{p+1}$$
Somit: 
$$\begin{align*}
a_n &= \sum_{k=1}^{n}k^p \\
A_n &= n^{p+1}
\end{align*}$$
Cauchyscher Konvergenzsatz: 
$$\lim_{n \to \infty} \frac{a_{n+1} - a_n}{A_{n+1}-A_n} = \lim_{n \to \infty} \frac{\sum_{k=1}^{n+1}k^p - \sum_{k=1}^{n}k^p}{(n+1)^{p+1}- n^{p+1}} = \lim_{n \to \infty} \frac{(n+1)^p}{(n+1)^{p+1}- n^{p+1}} = \frac{1}{p+1}$$
	**Exkurs**:
		Warum ist $\lim_{n \to \infty} \frac{(n+1)^p}{(n+1)^{p+1}- n^{p+1}} = \frac{1}{p+1}$ ?
	**Schritt 1**: Den Nenner verstehen
		Für große $n$ ändert sich $u^{p+1}$ zwischen n und n+1 nicht viel
		Diese Änderung kann mit der Ableitung $(p+1)u^p$ und der Schrittweite $(n+1) - n = 1$ berechent werden.
		Für große $n$ gilt also:
		$(n+1)^{p+1}- n^{p+1} \approx (p+1)n^p$ -> approx weil Schrittweite 1 nicht genau genug ist
	**Schritt 2**: Einsetzten
		$$\approx \lim_{n \to \infty} \frac{(n+1)^p}{(p+1)n^p} $$
	**Schritt 3**: Umformen
		$$\frac{(n+1)^p}{(p+1)n^p} = \frac{1}{p+1} \cdot \frac{(n+1)^p}{n^p} =  \frac{1}{p+1} \cdot (\frac{n+1}{n})^p$$
	**Schritt 4:** Grenzwert
		$$\lim_{n \to \infty} \frac{n+1}{1} = \lim_{n \to \infty} (1+\frac{1}{n}) = 1$$
	$$\lim_{n \to \infty} \frac{1}{p+1} \cdot (\frac{n+1}{n})^p = \frac{1}{p+1} \cdot 1 = \frac{1}{p+1}$$
5. Behandlung als Funktion
Es sei $f: \mathbb{R} \rightarrow \mathbb{R}$ eine Funktion mit $f(n) = a_n$, dann folgt aus $\lim_{x \rightarrow \infty} f(x) = g$ auch $\lim_{x \rightarrow \infty} a_n = g$.
Diese Technik gestattet die Verwendung der l’Hospitalschen-Regeln, vorausgesetzt $f$
ist differenzierbar. #TODO_add_reference #TODO

## Reihen

> **Reihen**:
> Die aus Folgegliedern gebildete Summen $s_n= \sum^n_{k=0}a_k$.
> Die Folge aus diesen Summen heißt Reihe.

> **Geometrische Reihe**:
> $$\sum^\infty_{k=0}q^k$$

> **Harmonische Reihe**:
> $$\sum^\infty_{k=1}\frac{1}{k}$$
> Die Reihe ist Divergent!

> **absolut konvergente Reihe**:
> Wenn $\sum^\infty_{k=0} |a_k|$ endlich ist
> Reihen die konvergieren aber nicht absolut konvergieren (also ohne Betrag) heißen bedingt konvergent.
> In einer Konvergenten Reihe bilden die Glieder {$a_k$} eine Nullfolge. Die Umkehrung ist nicht wahr (siehe harmonische Reihe)

> **Leibniz-Kriterium**:
> Eine alternierende Reihe $a_0 - a_1 + a_2 - a_3 ...$ konvergiert, wenn die Folge {$a_k$} eine Nullfolge ist.

> **Potenzreihen**: 
> Reihen der Form:
> $$\sum_{k=0}^\infty a_k(x-x_0)^k$$
> Ihre Partialsummen sind Polynome.
> Mit einer Substitution $x:=x-x_0$ brauchen nur Reihen der Form $\sum_{k=0}^\infty a_kx^k$ untersucht werden.

> Entwicklungspunkt:
> $x_0$ in der Potenzreihe. 

### Warum die Harmonische Reihe divergiert
Harmonische Reihe:

$$\begin{aligned}
1
&+ \frac{1}{2} \\
&+ \left( \frac{1}{3} + \frac{1}{4} \right) \\
&+ \left( \frac{1}{5} + \frac{1}{6} + \frac{1}{7} + \frac{1}{8} \right) \\
&+ \left( \frac{1}{9} + \dots + \frac{1}{16} \right)\\
&+ \dots
\end{aligned}$$

Jede dieser Gruppen ist also größer als 1/2:
$$\begin{aligned}
\frac{1}{3} + \frac{1}{4} &> 2 \cdot \frac{1}{4} = \frac{1}{2}, \\
\frac{1}{5} + \dots + \frac{1}{8} &> 4 \cdot \frac{1}{8} = \frac{1}{2}, \\
\frac{1}{9} + \dots + \frac{1}{16} &> 8 \cdot \frac{1}{16} = \frac{1}{2}, 
\end{aligned}$$

Daraus Folgt: 
$$\sum^\infty_{k=1}\frac{1}{k} > 1 + \infty*\frac{1}{2}$$
## Konvergenzkriterien für Reihen
1. Majorantenkriterium
Ist $\sum^\infty_{k=0}a_k$ absolut konvergent, und gilt $|b_k|\leq|a_k|$ für alle k ab einem $k_0$, so ist $\sum^\infty_{k=0}b_k$ absolut konvergent.
2. Quotientenkriterium
Für eine Reihe existiere $\lim_{k\to \infty}|\frac{a_{k+1}}{a_k}| = c$ ($a_k \neq 0$ für alle $k$), dann folgt aus c die Konvergenz der Reihe: 
- $c<1$ absolute Konvergenz
- $c>1$ Divergenz
- $c=1$ keine Aussage möglich
3. Wurzelkriterium
Für eine Reihe existiere $\lim_{k \to \infty} \sqrt[k]{|a^k|} = c$, dann folgt aus c die Konvergenz der Reihe: 
- $c < 1$ absolute Konvergenz
- $c>1$ Divergenz
- $c=1$ keine Aussage möglich
4. Integralkriterium
Kann man die Glieder der Reihe $\sum^\infty_{k=1} a_k$ als Funktionswerte $f(k) = a_k$ einer in $\mathbb{R}^>$ stetigen, monoton fallenden Funktion $f(x)$ darstellen, dann ist die Reihe genau dann konvergent, wenn das Integral $\int^\infty_1 f(x)dx$ existiert = endlich ist.
	$f(x)$ muss stetig, positiv und monoton fallend sein


## Konvergenzradius einer Potenzreihe

> Konvergenzradius: 
> Beschreibt für welche Werte von $x$ eine Potenzreihe konvergiert.

Es gibt eine Zahl $r \geq 0$ mit folgender Eigenschaft: 
- Für alle $x$ mit $|x-x_0| < r$ konvergiert die Reihe
- Für alle $x$ mit $|x-x_0| > r$ konvergiert die Reihe
- Für $|x-x_0| = r$, also die Randpunkte, muss die konvergenz extra überprüft werden

Berechnung durch Quotientenkriterium:
$$\limsup_{n \to \infty}|\frac{a_{n+1}}{a_n}| = \frac{1}{r}$$
Oder Wurzelkriterium:
$$\limsup_{n\to\infty} \sqrt[n]{|a_n|} = \frac{1}{r}$$

Exkurs: 
> **Limes superior**:
> Der größte Häufungswert, den die Folge für $n \to\infty$ annimmt.
> $$\limsup_{n\to\infty}$$
> Der Limes einer alternierenden Folge ist nicht existent, obwohl eigentlich ein oberer Wert existiert.