![[Pasted image 20260326161610.png]]

## Trennung der Variablen
1. Ansatz $u(x,t) = X(x) \cdot T(t)$ (bzw. $u_x(x,t) = X'(x) \cdot T(t)$) einsetzten 
2. Trennung der Variablen
$$\frac{T^{(n)}}{T} = \frac{X^{(m)}}{X} = - \lambda$$
	Lambda "irgendwie schlau" festlegen
3. Lösen der ODE für $X(x)$ und $T(t)$
4. Superposition der Eigenlösung
### Beispielrechnung:
$$u_t = 4\cdot u_{xx}$$
Lösungsansatz $u(x,t) = X(x) \cdot T(t)$:
Ableitungen die gebraucht werden: 
$$\begin{align*}
u_t  &= X(x) \cdot T'(t) \\
u_{xx} &= X''(x)\cdot T(t)
\end{align*}$$
In Aufgabe einsetzten: 
$$X(x)\cdot T'(t) =4\cdot X''(x) \cdot T(t)$$
Variablen Trennen:
$$
\begin{align*}
X(x)\cdot T'(t) &=4\cdot X''(x) \cdot T(t) \space | \space :T(t):X(x) \\
\frac{T'}{T} &= 4 \frac{X''}{X} = -\lambda
\end{align*}$$
"Als Konstante wird $- \lambda$ gewählt, damit schöne Sinus/Cosinus-Lösungen entstehen" 🙃

Beide entstehende ODEs lösen:
$$
\begin{align*}
 &I \space \space \space T'(t) = -\lambda * T(t)\\
 &II  \space  X''(x) = -0.25\lambda*X(x)
\end{align*}$$
I: 
$$
\begin{align*}
T'(t) &= -\lambda * T(t)\\
\frac{dT}{dt} &= -\lambda dt \\
\int\frac{dT}{dt} &= \int -\lambda dt \\
\ln |T| &= -\lambda t + C \\
T(t) &= C* e^{-\lambda t}
\end{align*}
$$
II: 
(1) Überlegung:
Welche Funktion $X(x)$ gibt zwei mal abgeleitet $-X(x)$. Da kommen eigentlich nur $\sin(x)$ und $\cos(x)$ in Frage. 
(2) wird $\sin(\mu x)$ zwei mal abgeleitet entsteht $-\mu^2 \sin(\mu x)$ somit muss $\mu^2 = 0.25\lambda$
$$
\begin{align*}
X''(x) &= -0.25\lambda * X(x)\\
\Rightarrow^{(1)} X_1(x) &= A\sin(\mu x) \\
\Rightarrow^{(1)} X_1(x) &= B\cos(\mu x) \\
\mu &=^{(2)} \sqrt{0.25\lambda} \\
X(x) &= A\sin(\sqrt{0.25\lambda} x) + B\cos(\sqrt{0.25\lambda} x)
\end{align*}
$$
Ergebnis: 
$$\begin{align*}
u(x,t) &= X(x) \cdot T(t) \\
u(x,t) &= A\sin(\sqrt{0.25\lambda} x) + B\cos(\sqrt{0.25\lambda} x) \cdot C\cdot e^{-\lambda t}
\end{align*}$$
## Methode der Charakteristiken
1. Charakteristiken aufstellen
2. Lösen der Charakteristiken
3. Eliminieren des Parameters $s$
4. Lösung für $u$ bestimmen
5. Anfangsbedinungen einsetzten
6. Spezielle Lösung bestimmen
### Beispielaufgabe
$$2 u_x + 3u_y = 0$$
Charakteristiken aufstellen: 
$$\begin{align*}
\frac{dx}{ds} &= 2\\
\frac{dy}{ds} &= 3\\
\frac{du}{ds} &= 0\\
\end{align*}$$
Lösen der Charakteristiken:
I:
$$\begin{align*}
\frac{dx}{ds} &= 2\\
x(s) &= 2s + C_1
\end{align*}$$
II:
$$\begin{align*}
\frac{dy}{ds} &=3\\
y(s) &= 3s + C_2
\end{align*}$$
Eliminieren des Parameters $s$
$$\begin{align*}
&I. &x &= 2s+C_1 \\
&II. &y&= 3s+C_2
\end{align*}$$
$$\begin{align*}
s &= \frac{x-C_1}{2} \\
y &= 3(\frac{x-C_1}{2} + C_2) \\
y &= \frac{3}{2}x - \frac{3}{2}C_1 + C_2\\
3x - 2y &= C  &\texttt{mit } C = 3C_1 - 2C_2 
\end{align*}$$
Lösung für $u$ bestimmen
Da $c = 0$ ist $u$ konstant entlang der Charakteristik. Also $u$ hängt nur von $3x-2y$ ab.
Dh. allgemeine Lösung:
$$
u(x,y) = f(3x-2y) , \texttt{  für eine belibige Funktion } f(x,y)
$$

