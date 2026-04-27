Starke Lösungen sind der klassische Fall
## Starke Lösungen
Erfüllen die Gleichung Punktweise, also an jedem einzelnen Punkt des Definitionsbereichs.
sind ausreichend oft differenzierbar
eg. in einer DGL $f(x) = u''(x)$ muss die Lösung von $u$ zweimal differenzierbar sein (Abhängig von der Ordnung der DGL)
Nicht immer möglich wenn $f(x)$ zum Beispiel einen Sprung hat

Diese Lösungen existieren nicht oft

## Schwache Lösungen
Erfüllt die Gleichung nicht punktweise, sondern im Integralen Mittel gegen alle Testfunktionen
Vorteil:
- geringere Glattheit notwending
- Existenz oft gesichert 

> Partielle Integration:
> $$\int u v' = [uv] - \int v u'$$

### Beispiel Aufgabe: 

$$-(k * u')' = f(x), \space \space \text{  auf } [0,1], \space \space \text{ }  f(0) = f(1) = 0$$
$$\begin{align}
\Rightarrow_{(1)} -(ku')' \phi &= f * \phi \\
\Rightarrow_{(2)} \int_0^1 -(ku')' \phi dx &=  \int_0^1f * \phi dx\\
\Rightarrow_{(3)} [-(ku')' * \phi]_0^1 -  \int_0^1 -ku' \phi' dx &=  \int_0^1f * \phi dx\\
\Rightarrow_{(4)} 0_{(4.1)} +  \int_0^1 ku' \phi' dx &=  \int_0^1f * \phi dx\\
\Rightarrow \int_0^1 ku(x)' \phi(x)' dx &=  \int_0^1f(x) * \phi(x) dx\\
\end{align}$$
$(1)$: mit Hilfsfunktion multiplizieren. $\phi(x) \in C^\infty_c$ -> unendlich ableitbar und compact, also bis auf einen kleinen Teil, gleich 0
$(2)$: Beide Seiten über den gesamten Bereich integrieren
$(3)$: Partielle Integration anwenden
$(4)$: Vereinfachen. Da $\phi$ compact ist, ist dieser Teil immer 0

Ergebnis ist die schwache Form der Gleichung

