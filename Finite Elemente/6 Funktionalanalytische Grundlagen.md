## Normierte Räume
Ein Raum mit einer Norm👍, der folgende Eigenschaften erfüllt: 
Positivität: $||x|| \geq 0, ||x|| = 0 \Leftrightarrow x = 0$
Homogenität: $||ax|| = |a| \space ||x||$
Dreiecksungleichung: $||x+y|| \leq ||x|| + ||y||$

## Funktionenräume
Idee: Funktionen als unendlich dimensionale Vektoren
#### Wichtige Räume:
- $C([a,b])$: alle Funktionen die auf dem Bereich definiert und stetig sind
- $C^k(\Omega)$: alle Funktionen die auf der Menge $\Omega \subset \mathbb{R}$ definiert sind und k mal stetig ableitbar ist
- $L^2(\Omega)$: alle Funktionen deren Quadrat in ihrem Definitionsbereich integrierbar ist
	- Müssen nicht stetig sein -> nicht alle Funktionen sind ableitbar -> schwache Lösungen
	- Ist eine große Klasse an Funktionen
	- Ist ein Hilbertraum

## Bilinearform
$$a(u, v) = \int_0^1 u'(x) v'(x)dx$$

## Lax-Milgram
Ein Konitinuierliches Problem hat eine eindeutige Lösung

Schwache Formulierung einer DGL: $a(u,v) = F(v)$
Wenn $a(u,v)$ zwei Eigenschaften erfüllt, gibt es genau eine Lösung:
- Stetigkeit: $|a(u,v)| \leq ||u|| * ||v||$
- Koerzivität: $a(u,u) \geq a ||u||^2$

Irgendwas mit linearität des Funktionals

# Kochrezept: Stetigkeit & Koerzivität einer Bilinearform
## Schritt 1: Norm identifizieren

Lies aus der Aufgabe ab, welcher Raum $V$ gegeben ist:

|Raum|Norm $\|\cdot\|_V$|
|---|---|
|$H_0^1(\Omega)$|$\|v\|_V = \|v'\|_{L^2}$|
|$H^1(\Omega)$|$\|v\|_V = \left(\|v\|_{L^2}^2 + \|v'\|_{L^2}^2\right)^{1/2}$|
|$L^2(\Omega)$|$\|v\|_V = \|v\|_{L^2}$|
## Schritt 2: Stetigkeit zeigen
Ziel Finde $M > 0$, sodass $|a(u,v)| \leq M|u|_V|v|_V$ für alle $u,v \in V$.
### Vorgehen

1. Schreibe $|a(u,v)|$ hin
2. Ziehe den Betrag ins Integral: $$\left|\int_\Omega \ldots , dx\right| \leq \int_\Omega |\ldots| , dx$$
3. Wende **Cauchy-Schwarz** an: $$\int_\Omega f \cdot g , dx \leq |f|_{L^2} \cdot |g|_{L^2}$$
4. Erkenne die $V$-Normen in dem, was übrig bleibt
5. Lies $M$ ab

### Typisches Ergebnis
$$|a(u,v)| \leq \int_\Omega |u'||v'|,dx \leq |u'|_{L^2}|v'|_{L^2} = |u|_V|v|_V$$
Fertig $M = 1$ (oder eine Konstante aus den Koeffizienten) $\Rightarrow$ Stetigkeit gezeigt ✓

## Schritt 3: Koerzivität zeigen
Ziel Finde $\alpha > 0$, sodass $a(v,v) \geq \alpha |v|_V^2$ für alle $v \in V$.
### Vorgehen

1. Setze $u = v$ in $a(u,v)$ ein
2. Vereinfache — oft verschwinden Terme oder werden positiv
3. Erkenne $|v|_V^2$ in dem, was übrig bleibt
4. Lies $\alpha$ ab
### Typisches Ergebnis

$$a(v,v) = \int_\Omega (v')^2,dx = |v'|_{L^2}^2 = |v|_V^2 \geq 1 \cdot |v|_V^2$$

Fertig $\alpha = 1$ $\Rightarrow$ Koerzivität gezeigt ✓
## Schritt 4: Koerzivität bei komplizierten Termen

Falls nach $u = v$ noch zusätzliche Terme übrig bleiben, z.B. $\int_\Omega c(x), v^2,dx$:
Fallunterscheidung 
 - $c(x) \geq 0$: Term **weglassen** — macht die Ungleichung nur stärker ✓
 - $c(x) < 0$: Term muss weiter abgeschätzt werden (selten in Grundvorlesungen)
## Abschluss-Check
 - [ ] $V$ ist Hilbertraum _(meist geschenkt, einfach benennen)_
 - [ ] $F \in V^*$ — stetig und linear
 - [ ] **Stetigkeit:** $|a(u,v)| \leq M|u|_V|v|_V$ mit $M = \ldots$
 - [ ] **Koerzivität:** $a(v,v) \geq \alpha|v|_V^2$ mit $\alpha = \ldots$

Alle vier erfüllt $\Rightarrow$ **Lax-Milgram anwendbar** $\Rightarrow$ eindeutige Lösung existiert.