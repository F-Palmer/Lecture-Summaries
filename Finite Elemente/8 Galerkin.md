**Idee**: 
Raten, dass die Lösung der DGL ungefähr so aussieht wie eine Kombination aus einfachen Funktionen
-> Galerkin ist ein Näherungsverfahren
Wenn man den geratenen Ansatz in eine DGL einsetzt entsteht ein Fehler $R(x)$. Dieser Fehler soll minimiert werden
Also für die DGL: $u''(x) = f(x)$
Ist der Fehler $R(x) = \hat u''(x) - f(x)$, wobei $\hat u$ die approximation der idealen Lösung der DGL ist.

$$\int_\Omega R(x) * \varphi_1(x) dx = 0$$


1. Schwache Formulierung aufstellen
$$a(u,v) = L(v)$$
2. Ansatzfunktion(en) wählen
$$u(x) \approx c_1 \varphi_1(x) + c_2 \varphi_2(x) ...$$
	-> Man sucht die Faktoren $c_i$ für die Ansatzfunktionen $\varphi_i$
3. Für Ansatz Linke ($a(u,v)$) Seite lösen 
4. Für Ansatz Rechte ($L(v)$) Seite lösen
5. Zusammen führen und $c_1$ berechnen

![[Galerkin.pdf]]

Mit mehreren Ansatzfunktionen (Ergebnis is absolut Bullshit, aber Rechenweg sollte eigentlich passen): 
![[Galerkin2.pdf]]