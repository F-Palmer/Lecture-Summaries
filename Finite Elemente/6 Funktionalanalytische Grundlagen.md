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
