

# Osnove kompleksne analize

## Funkcije kompleksne spremenljivke

Naj bo $\Omega \subset \mathbb{C}$ območje v kompleksni ravnini in naj bo podana funkcija:
$$f: \Omega \longrightarrow \mathbb{C}$$

Taka funkcija vsakemu kompleksnemu številu $z \in \Omega$ priredi kompleksno število $f(z) = w \in \mathbb{C}$.

$$z \longmapsto w = f(z)$$


---

## Kompleksna zveznost

**Definicija:** Naj bo $f: \Omega \longrightarrow \mathbb{C}$ funkcija kompleksne spremenljivke. Funkcija $f$ je v $z_0 \in \Omega$ zvezna, če velja:
Za vsak $\epsilon > 0$ obstaja $\delta > 0$, tako da velja:
$$|z - z_0| < \delta \implies |f(z) - f(z_0)| < \epsilon$$

Poglejmo si, kaj to pomeni:
Spomnimo se:
$$z = x + iy \quad \text{in} \quad |z| = (x^2 + y^2)^{\frac{1}{2}}$$

Torej:
$$|z - z_0| = |(x + iy) - (x_0 + iy_0)| =$$ $$= |(x - x_0) + i(y - y_0)| = \left( (x - x_0)^2 + (y - y_0)^2 \right)^{\frac{1}{2}}$$

Torej, funkcija $f$ je v $z_0$ zvezna, če za vsak $\epsilon > 0$ obstaja tak $\delta$, da se $z$ iz kroga
$$B_\delta(z_0) = \{ z = x + iy \mid (x - x_0)^2 + (y - y_0)^2 < \delta^2 \}$$
preslika v krog
$$B_\epsilon(f(z_0)) = \{ w = a + ib \mid (a - a_0)^2 + (b - b_0)^2 < \epsilon^2 \}$$
pri čemer je $a_0 + ib_0 = w_0 = f(z_0)$.

Vidimo, da je včasih praktično opisati kompleksno funkcijo v koordinatah.

---

## Komponente kompleksne funkcije

Označimo:
$$f(z) = u(z) + i v(z)$$
$u$ – realna komponenta $f$
$v$ – imaginarna komponenta $f$

Še bolj eksplicitno:
$$f(x + iy) = u(x, y) + i v(x, y)$$

Kompleksna števila so točke v $\mathbb{R}^2$, torej uvrstimo v $\mathbb{R}^2$. Pišemo lahko:
$$z = x + iy = \begin{pmatrix} x \\ y \end{pmatrix}$$
in
$$f(z) = u(x, y) + i v(x, y) = \begin{pmatrix} u(x, y) \\ v(x, y) \end{pmatrix}$$

**Primeri:**
1. $f(z) = z^2$
   $f(z) = (x + iy)^2 = (x^2 - y^2) + i 2xy$
2. $f(z) = z^3 = (x^2 - y^2 + i 2xy)(x + iy) = x^3 - 3xy^2 + i(3x^2y - y^3)$

---

## Kompleksni odvod

**Definicija:** Funkcija $f: \Omega \longrightarrow \mathbb{C}$ je v točki $z_0 \in \Omega$ **kompleksno odvedljiva**, če obstaja tako kompleksno število $A$, da velja:
$$f(z_0 + h) = f(z_0) + A \cdot h + o(h)$$
pri čemer je $\lim_{h \to 0} \frac{o(h)}{h} = 0$.

Če tako število obstaja, pišemo:
$$A = f'(z_0)$$

Definicijo lahko zapišemo tudi v drugačni obliki:
$$f(z_0 + h) - f(z_0) = A \cdot h + o(h)$$
$$\frac{f(z_0 + h) - f(z_0)}{h} = A + \frac{o(h)}{h} \quad \Big/ \lim_{h \to 0}$$
$$\lim_{h \to 0} \frac{f(z_0 + h) - f(z_0)}{h} = f'(z_0) = A$$

Pri tem je pomembno naslednje: spremenljivka $h$ potuje proti $0$ v kompleksni ravnini $\mathbb{C} \approx \mathbb{R}^2$. Proti $0$ lahko potuje po različnih poteh. Število $A = f'(z_0)$ je neodvisno od izbire poti, po kateri $h$ proti $0$.

---

## Cauchy-Riemannov sistem (CR)

Vemo, da je odvod take preslikave podan z matriko $J$.
$$Df_{(x,y)} = \begin{pmatrix} \frac{\partial u}{\partial x} & \frac{\partial u}{\partial y} \\ \frac{\partial v}{\partial x} & \frac{\partial v}{\partial y} \end{pmatrix}$$

V primeru, ko je $f$ kompleksno odvedljiva, velja:
$$f((x + iy) + (h_1 + ih_2)) = f(x + iy) + (\alpha + i\beta)(h_1 + ih_2) + o(h_1, h_2)$$
Torej:
$$(\alpha + i\beta)(h_1 + ih_2) = (\alpha h_1 - \beta h_2) + i(\beta h_1 + \alpha h_2)$$

Desno stran lahko zapišemo v vektorsko-matrični obliki:
$$\begin{pmatrix} \alpha h_1 - \beta h_2 \\ \beta h_1 + \alpha h_2 \end{pmatrix} = \begin{pmatrix} \alpha & -\beta \\ \beta & \alpha \end{pmatrix} \begin{pmatrix} h_1 \\ h_2 \end{pmatrix}$$

Iz zgornjega zapisa vidimo, da je naša matrika $Df$ oblike:
$$\begin{pmatrix} \frac{\partial u}{\partial x} & \frac{\partial u}{\partial y} \\ \frac{\partial v}{\partial x} & \frac{\partial v}{\partial y} \end{pmatrix} = \begin{pmatrix} \alpha & -\beta \\ \beta & \alpha \end{pmatrix}$$

Od tod vidimo:
Če je $f$ v $z = z_0$ kompleksno odvedljiva, potem mora veljati:
$$\begin{aligned} \frac{\partial u}{\partial x} &= \frac{\partial v}{\partial y} \\ \frac{\partial u}{\partial y} &= -\frac{\partial v}{\partial x} \end{aligned} \quad \text{(CR)}$$

Sistem (CR) se imenuje **Cauchy-Riemannov sistem**.

**Izrek:** Funkcija kompleksne spremenljivke $f: \Omega \longrightarrow \mathbb{C}$ je v $z_0 \in \Omega$ kompleksno odvedljiva natanko tedaj, ko v $z_0 = (x_0, y_0)$ funkciji $u(x, y)$ in $v(x, y)$ zadoščata Cauchy-Riemannovemu sistemu (CR).

**Definicija:** Funkcije, ki so na nekem območju $\Omega \subset \mathbb{C}$ kompleksno odvedljive, se imenujejo **holomorfne** funkcije na $\Omega$.

---

## Geometrijski pomen kompleksnega odvoda

Oglejmo si še, kaj matrika odvoda holomorfne funkcije dela:
$$\begin{pmatrix} \alpha & -\beta \\ \beta & \alpha \end{pmatrix} = \sqrt{\alpha^2 + \beta^2} \begin{pmatrix} \frac{\alpha}{\sqrt{\alpha^2 + \beta^2}} & -\frac{\beta}{\sqrt{\alpha^2 + \beta^2}} \\ \frac{\beta}{\sqrt{\alpha^2 + \beta^2}} & \frac{\alpha}{\sqrt{\alpha^2 + \beta^2}} \end{pmatrix}$$

Ker je $\left( \frac{\alpha}{\dots} \right)^2 + \left( \frac{\beta}{\dots} \right)^2 = 1$, obstaja $t \in [0, 2\pi)$, tako da je:
$$A=\begin{pmatrix} \alpha & -\beta \\ \beta & \alpha \end{pmatrix} = r \begin{pmatrix} \cos(t) & -\sin(t) \\ \sin(t) & \cos(t) \end{pmatrix}$$
kjer je $r = \sqrt{\alpha^2 + \beta^2} = |f'(z_0)|$.

Torej bo matrika vektor $(h_1, h_2)^T$ zavrti za kot $t = \text{arg}(f'(z_0))$ in ga podaljša (skalira) za faktor $r = |f'(z_0)|$.
To pa je natanko opis geometrijskega pomena množenja s kompleksnim številom $f'(z_0)$.

Vsota, razlika, množenje in kvocient je holomorfna funkcija.



Ali je $f(z) = \overline{z}$ kompleksno odv.?


$$f'(z) = \lim_{h \to 0} \frac{\overline{(z+h)} - \overline{z}}{h} = \lim_{h \to 0} \frac{\overline{h}}{h} = \lim_{r \to 0} \frac{re^{-i\phi}}{re^{i\phi}} = \frac{e^{-i\phi}}{e^{i\phi}} = e^{-2i\phi}$$

NI kompleksno odvedljiva

---

## Elementarne holomorfne funkcije

Poglejmo funkcijo $f(z) = e^z = \exp(z)$.
Spomnimo se razvoja te funkcije v Taylorjevo vrsto:
$$e^z = e^{x+iy} = e^x e^{iy} = e^x \left( \sum_{n=0}^\infty \frac{(iy)^n}{n!} \right) = e^x \left( \sum_{k=0}^\infty \frac{(iy)^{2k}}{(2k)!} + \sum_{k=0}^\infty \frac{(iy)^{2k+1}}{(2k+1)!} \right)$$
$$= e^x \left( \sum_{k=0}^\infty (-1)^k \frac{y^{2k}}{(2k)!} + i \sum_{k=0}^\infty (-1)^k \frac{y^{2k+1}}{(2k+1)!} \right)$$
$$= e^x (\cos y + i \sin y)$$

Predpis $z \longmapsto e^z$ je torej dobro definiran za vsak $z \in \mathbb{C}$.
Poglejmo, ali je $f(z) = e^z$ holomorfna:
$$e^z = e^x \cos y + i e^x \sin y$$
$$u(x, y) = e^x \cos y, \quad v(x, y) = e^x \sin y$$
Preverimo CR:
$$\frac{\partial u}{\partial x} = e^x \cos y, \quad \frac{\partial v}{\partial y} = e^x \cos y \implies \frac{\partial u}{\partial x} = \frac{\partial v}{\partial y} \quad \checkmark$$
$$\frac{\partial u}{\partial y} = -e^x \sin y, \quad \frac{\partial v}{\partial x} = e^x \sin y \implies \frac{\partial u}{\partial y} = -\frac{\partial v}{\partial x} \quad \checkmark$$
Torej $e^z$ je holomorfna na vsem $\mathbb{C}$.

Velja da je periodična po $e^{z +2\pi i}$. *Samo preko spremembe imaginarne komponente.*

> **Definicija:** Funkcije, ki so holomorfne na vsem $\mathbb{C}$, se imenujejo **cele** (entire) funkcije.

---

## Trigonometrične in hiperbolične funkcije

Spomnimo se identitete:
$$e^{ix} = \cos x + i \sin x$$
$$e^{-ix} = \cos x - i \sin x$$
Tako dobimo:
$$\cos x = \frac{e^{ix} + e^{-ix}}{2}, \quad \sin x = \frac{e^{ix} - e^{-ix}}{2i}$$

**Definicije:**
$$\cos z = \frac{e^{iz} + e^{-iz}}{2}, \quad \sin z = \frac{e^{iz} - e^{-iz}}{2i}$$
$$\cosh z = \frac{e^z + e^{-z}}{2}, \quad \sinh z = \frac{e^z - e^{-z}}{2}$$
Lahko je videti, da so Taylorjeve vrste teh funkcij prav take, kot vrste za njihove realne analoge.

---

## Laplaceov operator in harmonične funkcije

> **Definicija:** Naj bo funkcija $u(x, y): \Omega \subset \mathbb{R}^2 \longrightarrow \mathbb{R}$ funkcija dveh spremenljivk. Laplaceov operator $\Delta$ je:
> $$\Delta = \frac{\partial^2}{\partial x^2} + \frac{\partial^2}{\partial y^2}$$
> priredi jo funkciji
> $$\Delta(u) = \frac{\partial^2 u}{\partial x^2} + \frac{\partial^2 u}{\partial y^2}$$

> **Definicija:** Funkcija $u(x, y)$, za katero velja $\Delta(u) = 0$, je **harmonična funkcija** na $\Omega$.

> **Izrek:** Naj bo $f = u + iv: \Omega \longrightarrow \mathbb{C}$ holomorfna. Potem sta $u$ in $v$ harmonični na $\Omega$.
> 
> **Dokaz:** Ker je $f$ holomorfna, velja CR:
> $$u_x = v_y \quad \text{in} \quad u_y = -v_x$$
> Odvedemo prvo po $x$ in drugo po $y$:
> $$u_{xx} = v_{yx}, \quad u_{yy} = -v_{xy}$$
> Seštejemo in dobimo:
> $$\Delta(u) = u_{xx} + u_{yy} = v_{yx} - v_{xy} = 0$$
> Podobno za $v$. $\square$



> **Trditev:** Naj bo $u : \Omega \to \mathbb{R}^2$ harmonična funkcija.
> Potem je holomorfna funkcija, ki ima $u$ za realno komponento  natančno določena. $v$ pravimo **harmoničen konjugat**.
> 
> **Dokaz:**
> Velja:
> $$u_x = v_y$$
> $$u_y = -v_x$$
> 
> Iščemo $v$ 
Za $v$ velja: 
$$v_x = -u_{y}, v_y = u_x$$
> $$\nabla v = \begin{pmatrix} -u_y \\ u_x \end{pmatrix}$$
> 
> Izberimo polj. tč. $(x_0, y_0) \in \Omega$
> Naj bo $\gamma : [a, b] \to \Omega$ pot, za katero velja:
> $$\gamma(a) = (x_0, y_0)$$
> $$\gamma(b) = (x, y)$$
> 
> Potem velja:
>  $$v(x, y) = \int_{(x_0, y_0)}^{(x, y)}\nabla v\cdot \dot{\gamma}(t) \, dt$$
> $$v(x, y) = \int_{(x_0, y_0)}^{(x, y)} (-u_y, u_x) \cdot \dot{\gamma}(t) \, dt$$

---

## Kompleksne potence in polinomi

Ali so vse kompleksne funkcije oblike $f(z) = \sum a_n z^n$ holomorfne?
Oglejmo si najprej holomorfnost $f(z) = z^n$:
$$f(z+h) - f(z) = (z+h)^n - z^n = z^n + \binom{n}{1}z^{n-1}h + \binom{n}{2}z^{n-2}h^2 + \dots + h^n - z^n$$
$$= h(nz^{n-1} + h(\dots))$$
Torej:
$$\frac{f(z+h) - f(z)}{h} = nz^{n-1} + h(\dots)$$
Limita $\lim_{h \to 0}$ je neodvisna od poti $h$ proti $0$. Torej:
$$f'(z) = (z^n)' = n z^{n-1}$$
Vse funkcije $z^n$ so holomorfne.
Ker je vsaka linearna kombinacija holomorfnih funkcij holomorfna, so vsi polinomi holomorfni na $\mathbb{C}$ (cele funkcije).

---

## Neskončne vrste

Kaj pa neskončni polinomi oz. vrste: $f(z) = \sum_{n=0}^\infty a_n z^n$?
Denimo, da zgornja vrsta konvergira za neko vrednost $z = z_0$. To pomeni, da za vsak $\epsilon > 0$ obstaja $N$, tako da velja:
$$m \ge N \implies \left| \sum_{n=m}^\infty a_n z_0^n \right| < \epsilon$$
Od tod: $|a_m z_0^m| \le \left| \sum_{n=m}^\infty a_n z_0^n \right| + \left| \sum_{n=m+1}^\infty a_n z_0^n \right| < 2\epsilon$ za $\forall m > N$.
Naj bo sedaj $|z| < |z_0|$. Potem vrsta konvergira absolutno.

Velja da na vsakem zaprtem krogu, kjer velja da je radij kroga $r \le |z_{0}|$ konvergira enakomerno.




---



## Kompleksna integracija

Naj bo $f: \Omega \longrightarrow \mathbb{C}$ funkcija kompleksne spremenljivke. Integral funkcije $f$ bo krivuljni integral. Seštevali bomo vrednosti funkcije vzdolž 1-dimenzionalnega objekta. Izkazalo se bo, da je ta konstrukcija najbolj plodna. (Med drugim nam bo dala operator, ki bo na prostoru holomorfnih funkcij "inverzen" kompleksnemu odvajanju).

**Definicija:** Naj bo $\gamma : [\alpha, \beta] \longrightarrow \Omega$ krivulja in $f: \Omega \longrightarrow \mathbb{C}$ zvezna funkcija.

Naj bo $D: \alpha = t_0 < t_1 < \dots < t_N = \beta$ delitev intervala $[\alpha, \beta]$. Integralska vsota funkcije $f$ po krivulji $\gamma$ je:
$$S_D = \sum_{n=0}^{N-1} f(\gamma(t_n)) (z_{n+1} - z_n) = \sum_{n=0}^{N-1} f(\gamma(t_n)) (\gamma(t_{n+1}) - \gamma(t_n))$$

Integral $\int_\gamma f$ je podan kot limita integralskih vsot:
$$\int_\gamma f = \lim_{\delta(D) \to 0} S_D$$

Ker je $\gamma(t_{n+1}) - \gamma(t_n) \approx \dot{\gamma}(\tau_n)(t_{n+1} - t_n)$, lahko integral zapišemo kot:
$$\int_\gamma f = \int_\alpha^\beta f(\gamma(t)) \dot{\gamma}(t) \, dt$$

---

### Primeri

1. **Integral potence:** $f(z) = z^n$, kjer je $\gamma$ enotska krožnica.
Parametrizacija: $\gamma(t) = e^{it} = \cos t + i \sin t$, za $t \in [0, 2\pi]$. Odvod je $\dot{\gamma}(t) = i e^{it}$.
$$\int_{S^1} z^n \, dz = \int_0^{2\pi} (e^{it})^n \cdot i e^{it} \, dt = i \int_0^{2\pi} e^{i(n+1)t} \, dt$$
Za $n \neq -1$:
$$i \left[ \frac{e^{i(n+1)t}}{i(n+1)} \right]_0^{2\pi} = \frac{1}{n+1} (e^{2\pi i(n+1)} - e^0) = 0$$
Za $n = -1$:
$$\int_{S^1} \frac{1}{z} \, dz = i \int_0^{2\pi} e^{-it} e^{it} \, dt = i \int_0^{2\pi} dt = 2\pi i$$
**Zaključek:** $\int_{S^1} z^n \, dz = 0$ za $n \in \mathbb{Z} \setminus \{-1\}$ in $\int_{S^1} \frac{1}{z} \, dz = 2\pi i$.

2. **Integracija vrste:** Naj bo $f(z) = \sum_{n=-\infty}^\infty a_n z^n$ Laurentova vrsta, ki konvergira na kolobarju $K(R_1, R_2)$. Za krožnico $S(0, r)$ z $R_1 < r < R_2$ velja:
$$\int_{S(0, r)} \left( \sum_{n=-\infty}^\infty a_n z^n \right) dz = 2\pi i a_{-1}$$

---

## Integracija holomorfnih funkcij

**Izrek (Cauchyjev izrek):** Naj bo $f$ holomorfna na območju $D \subset \mathbb{C}$ in naj bo $\Omega \subset D$ podobmočje z odsekoma gladkim robom $\partial \Omega$. Potem velja:
$$\int_{\partial \Omega} f(z) \, dz = 0$$

**Dokaz (skica):** Z uporabo Greenove formule za $f = u + iv$:
$$\int_{\partial \Omega} (u + iv)(dx + i dy) = \int_{\partial \Omega} (u \, dx - v \, dy) + i \int_{\partial \Omega} (v \, dx + u \, dy)$$
Z Greenovim izrekom dobimo:
$$\iint_\Omega (-v_x - u_y) \, dx dy + i \iint_\Omega (u_x - v_y) \, dx dy$$
Zaradi Cauchy-Riemannovih enačb ($u_x = v_y$ in $u_y = -v_x$) sta oba integrala enaka 0. $\square$

> **Cauchyjev izrek za točko:** Če je $f$ zvezna na $\Omega$ in holomorfna na $\Omega \setminus \{a\}$, še vedno velja $\int_{\partial \Omega} f(z) \, dz = 0$.
> 
> 
> We know that if $f$ were holomorphic everywhere inside $\Omega$, the integral would be $0$. Since it might not be holomorphic at the point $a$, we isolate it.
> 
> 1.  **Deform the Path:** By Cauchy’s theorem for multiply connected domains, the integral around the outer boundary $\partial \Omega$ is equal to the integral around a tiny circle $C_\epsilon$ of radius $\epsilon$ centered at the point $a$.
>     $$\int_{\partial \Omega} f(z) dz = \int_{C_\epsilon} f(z) dz$$
> 
> 2.  **Use Continuity to Bound the Function:** Because $f$ is **continuous** at $a$, it is bounded in a small neighborhood around $a$. This means there exists some constant $M$ such that $|f(z)| \le M$ for all $z$ on the tiny circle $C_\epsilon$.
> 
> 3.  **Estimate the Integral:** Use the "Estimation Lemma" (the $ML$-inequality). The length of the tiny circle $C_\epsilon$ is $2\pi\epsilon$.
>     $$\left| \int_{C_\epsilon} f(z) dz \right| \le \text{Max}|f(z)| \cdot \text{Length}(C_\epsilon) \le M \cdot 2\pi\epsilon$$
> 
> 4.  **Take the Limit:** Since the original integral $\int_{\partial \Omega} f(z) dz$ does not depend on $\epsilon$, we can let $\epsilon$ go to zero.
>     $$\lim_{\epsilon \to 0} (M \cdot 2\pi\epsilon) = 0$$

---

## Cauchyjeva integralska formula

**Izrek:** Naj bo $\Omega$ enostavno povezano območje in $f: \Omega \longrightarrow \mathbb{C}$ holomorfna funkcija. Za poljubno točko $a \in \Omega$ velja:
$$f(a) = \frac{1}{2\pi i} \int_{\partial \Omega} \frac{f(z)}{z-a} \, dz$$

>[!|dokaz]- Dokaz:
> 
> Definirajmo novo pomožno funkcijo $h(z)$:
> $$h(z) = \frac{f(z) - f(a)}{z-a}$$
> Preverimo zveznost te funkcije $h(z)$ v točki $a$:
> $$\lim_{z \to a} h(z) = \lim_{z \to a} \frac{f(z) - f(a)}{z-a} = f'(a)$$
> Ker $f$ kot holomorfna funkcija ima odvod $f'(a)$, je ta limita končno število. Torej je funkcija $h(z)$ **zvezna v točki $a$**
> 
> **Po prejšnjem izreku:**
> Ker je $h(z)$ zvezna v $a$ in holomorfna drugje, izrek pravi:
> $$\int_{\partial \Omega} h(z) \, dz = 0$$
> $$\int_{\partial \Omega} \frac{f(z) - f(a)}{z-a} \, dz = 0$$
> Razbijmo integral na dva dela:
> $$\int_{\partial \Omega} \frac{f(z)}{z-a} \, dz - \int_{\partial \Omega} \frac{f(a)}{z-a} \, dz = 0$$
> $$\int_{\partial \Omega} \frac{f(z)}{z-a} \, dz = f(a) \int_{\partial \Omega} \frac{1}{z-a} \, dz$$
> Vemo (z izračunom po krožnici), da je $\int \frac{1}{z-a} \, dz = 2\pi i$. In dobimo:
> $$\int_{\partial \Omega} \frac{f(z)}{z-a} \, dz = 2\pi i f(a)$$

**Posledica:** Holomorfne funkcije so neskončnokrat odvedljive. Za $n$-ti odvod velja:
$$f^{(n)}(a) = \frac{n!}{2\pi i} \int_{\partial \Omega} \frac{f(z)}{(z-a)^{n+1}} \, dz$$

Vsako holomorfno funkcijo lahko v okolici točke $a$ razvijemo v Taylorjevo vrsto:
$$f(z) = \sum_{n=0}^\infty \frac{f^{(n)}(a)}{n!} (z-a)^n$$

---

## Definicija Laurentove vrste

Če je funkcija $f$ holomorfna na kolobarju $K(a, \rho, R) = \{z; \rho < |z-a| < R\}$, jo lahko razvijemo v **Laurentovo vrsto** oblike:
$$f(z) = \sum_{n=-\infty}^\infty c_n (z-a)^n$$

Vrsto sestavljata dva dela:
1.  **Regularni del (R):** $\sum_{n \ge 0} c_n (z-a)^n$. Ta del se obnaša kot potenčna vrsta in konvergira znotraj kroga $\Delta(a, R)$.
2.  **Glavni del (G):** $\sum_{n = -1}^{-\infty} c_n (z-a)^n = \sum_{m \ge 1} \frac{c_{-m}}{(z-a)^m}$. Ta del določa naravo singularnosti v točki $a$.

**Konvergenca:**
*   Regularni del $R$ konvergira na disku $|z-a| < R$.
*   Glavni del $G$ konvergira na zunanjosti diska $|z-a| > \rho$.
*   Celotna Laurentova vrsta konvergira na preseku obeh območij, kar je **kolobar** $K = \{z; \rho < |z-a| < R\}$.

---

## Klasifikacija singularnosti glede na glavni del

Glede na glavni del Laurentove vrste v okolici točke $a$ ločimo:

1.  **Odstranljiva singularnost:** Glavni del je enak 0 (vsi $c_n = 0$ za $n < 0$).
2.  **Pol stopnje $m$:** Glavni del je končen:
    $$G(z) = \frac{c_{-1}}{z-a} + \frac{c_{-2}}{(z-a)^2} + \dots + \frac{c_{-m}}{(z-a)^m}$$
    V tem primeru pravimo, da je $f$ **meromorfna funkcija** v okolici točke $a$.
3.  **Bistvena (esencialna) singularnost:** Glavni del ima neskončno mnogo členov ($c_n \neq 0$ za neskončno mnogo negativnih indeksov $n$).

***
### Konvergenca Laurentove vrste

Laurentovo vrsto razbijemo na dva dela:
$$\sum_{n=-\infty}^{\infty} c_n(z-a)^n = \underbrace{\sum_{n \ge 0} c_n(z-a)^n}_{R} + \underbrace{\sum_{n=-1}^{-\infty} c_n(z-a)^n}_{G}$$

1.  **Regularni del ($R$):**
    Denimo, da regularni del $R$ konvergira na disku (krogu) $\Delta(a, R)$. To je običajna potenčna vrsta s polmerom konvergence $R$.

2.  **Glavni del ($G$):**
    Glavni del je definiran kot:
    $$G = \sum_{n=-1}^{-\infty} c_n(z-a)^n$$
    Uvedemo novo spremenljivko $t = \frac{1}{z-a}$. S to substitucijo dobimo:
    $$G = \sum_{n \ge 1} c_{-n} t^n$$
    Če ta nova vrsta $G(t)$ konvergira za $t \in \Delta(0, \frac{1}{\rho})$, potem prvotni glavni del $G(z)$ konvergira za vse $z$, kjer velja:
    $$|z-a| > \rho$$
    To pomeni, da glavni del konvergira na **zunanjosti kroga** $\Delta(a, \rho)$.

**Sklep:**
Če velja pogoj $\rho < R$, potem celotna Laurentova vrsta $\sum_{n=-\infty}^{\infty} c_n(z-a)^n$ konvergira na **kolobarju**:
$$K = \{z; \rho < |z-a| < R\}$$

---

## Razvoj holomorfne funkcije v Laurentovo vrsto

**Izrek:** Naj bo $f(z)$ funkcija, ki je holomorfna na kolobarju $K = \{z; \rho < |z-a| < R\}$. Potem jo na $K$ lahko razvijemo v Laurentovo vrsto, kjer so koeficienti podani z:
$$c_n = \frac{1}{2\pi i} \int_{\partial \Delta(a, R_0)} \frac{f(\xi)}{(\xi-a)^{n+1}} \, d\xi$$
kjer je $\rho < R_0 < R$.

>[!|dokaz]+ Dokaz:
> Po Cauchyjevi integralni formuli za kolobar $K$ zapišemo $f(z)$ kot razliko integralov po zunanjem krogu $R$ in notranjem krogu $\rho$ (v pozitivni orientaciji):
> $$f(z) = \frac{1}{2\pi i} \int_{\partial \Delta(a,R)} \frac{f(\xi)}{\xi - z} d\xi - \frac{1}{2\pi i} \int_{\partial \Delta(a,\rho)} \frac{f(\xi)}{\xi - z} d\xi$$
> 
> 1. **Regularni del ($|z-a| < |\xi-a| = R$):**
>    Jedro integrala razvijemo v geometrijsko vrsto po potencah $(z-a)$:
>    $$\frac{1}{\xi - z} = \frac{1}{(\xi - a) - (z - a)} = \frac{1}{\xi - a} \cdot \frac{1}{1 - \frac{z-a}{\xi-a}} = \sum_{n=0}^\infty \frac{(z-a)^n}{(\xi-a)^{n+1}}$$
>    Z zamenjavo integrala in vrste dobimo $\sum_{n=0}^\infty c_n (z-a)^n$, kjer je $c_n = \frac{1}{2\pi i} \int_{\partial \Delta(a,R)} \frac{f(\xi)}{(\xi-a)^{n+1}} d\xi$.
> 
> 2. **Glavni del ($|z-a| > |\xi-a| = \rho$):**
>    Drugi člen (z minusom) razvijemo po negativnih potencah $(z-a)$:
>    $$-\frac{1}{\xi - z} = \frac{1}{(z-a) - (\xi-a)} = \frac{1}{z-a} \cdot \frac{1}{1 - \frac{\xi-a}{z-a}} = \sum_{k=0}^\infty \frac{(\xi-a)^k}{(z-a)^{k+1}}$$
>    Vstavimo v integral in uvedemo substitucijo indeksa $n = -(k+1)$. Ko gre $k: 0 \to \infty$, gre $n: -1 \to -\infty$. Dobimo:
>    $$\sum_{n=-\infty}^{-1} (z-a)^n \left( \frac{1}{2\pi i} \int_{\partial \Delta(a,\rho)} \frac{f(\xi)}{(\xi-a)^{n+1}} d\xi \right)$$
> 
> 3. **Združitev:**
>    Ker je funkcija $g(\xi) = \frac{f(\xi)}{(\xi-a)^{n+1}}$ holomorfna v celotnem kolobarju $K$, sta po Cauchyjevem izreku integrala po $\partial \Delta(a,R)$ in $\partial \Delta(a,\rho)$ enaka integralu po poljubni vmesni poti $\partial \Delta(a, R_0)$. Združimo obe sumaciji:
>    $$f(z) = \sum_{n=-\infty}^{\infty} c_n (z-a)^n, \quad c_n = \frac{1}{2\pi i} \int_{\partial \Delta(a, R_0)} \frac{f(\xi)}{(\xi-a)^{n+1}} d\xi$$

### Primer razvoja v kolobarju
Razvijmo $f(z) = \frac{1}{(z-1)(z+2)}$ na kolobarju $1 < |z| < 2$ okoli točke $a=0$.
1.  **Razcep na parcialne ulomke:** $f(z) = \frac{1}{3} \left( \frac{1}{z-1} - \frac{1}{z+2} \right)$
2.  **Razvoj prvega člena ($|z| > 1$):**
    $$\frac{1}{3} \cdot \frac{1}{z-1} = \frac{1}{3z} \cdot \frac{1}{1 - \frac{1}{z}} = \frac{1}{3z} \sum_{n=0}^\infty \left( \frac{1}{z} \right)^n = \sum_{n=0}^\infty \frac{1}{3 z^{n+1}}$$
3.  **Razvoj drugega člena ($|z| < 2$):**
    $$-\frac{1}{3} \cdot \frac{1}{z+2} = -\frac{1}{3 \cdot 2} \cdot \frac{1}{1 - (-\frac{z}{2})} = -\frac{1}{6} \sum_{n=0}^\infty \left( -\frac{z}{2} \right)^n$$

---

## Izrek o ostankih (reziduumih)

**Izrek:** Naj bo $f$ holomorfna na območju $\Omega$ razen v izoliranih singularnostih $\{a_1, a_2, \dots, a_m\}$. Naj bo $\gamma$ sklenjena krivulja, ki v pozitivni smeri obkroži te točke. Potem velja:
$$\int_{\gamma} f(z) \, dz = 2\pi i \sum_{k=1}^m \text{Res}(f, a_k)$$

**Definicija ostanka (rezidua):**
Ostanek $\text{Res}(f, a_i)$ je koeficient **$c_{-1}$** v Laurentovem razvoju funkcije $f$ okoli točke $a_i$:
$$\text{Res}(f, a_i) = c_{-1}$$

**Primer izračuna ostanka:**
Za $f(z) = \frac{1}{(z+1)(z-3)}$ v točki $a = -1$:
Ker gre za pol 1. stopnje, lahko ostanek izračunamo kot limito (ali z razvojem):
$$\text{Res}(f, -1) = \lim_{z \to -1} (z+1) f(z) = \lim_{z \to -1} \frac{1}{z-3} = -\frac{1}{4}$$
Integral okoli točke $-1$ je torej $2\pi i \cdot (-1/4) = -\frac{\pi i}{2}$.

