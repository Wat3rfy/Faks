Tukaj je natančen prepis vsebine rokopisnih zapiskov o osnovah kompleksne analize:

---

### **Stran 1**
**Osnove kompleksne analize**

**Funkcije kompleksne spremenljivke**

Naj bo $\Omega \subset \mathbb{C}$ območje v kompleksni ravnini in naj bo podana funkcija
$$f: \Omega \longrightarrow \mathbb{C}$$
Taka funkcija vsakemu kompleksnemu številu $z \in \Omega$ priredi kompleksno število $f(z) = w \in \mathbb{C}$.

$$z \longmapsto w = f(z)$$
*(Na strani sta dva grafa, ki prikazujeta preslikavo točke $z$ iz kompleksne ravnine $z$ (z osema $Re$ in $Im$) v točko $w = f(z)$ v kompleksni ravnini $w$.)*

---

### **Stran 2**
**Kompleksni odvod**

**Definicija:** Naj bo
$$f: \Omega \longrightarrow \mathbb{C}$$
funkcija kompleksne spremenljivke. Funkcija $f$ je v $z_0 \in \Omega$ zvezna, če velja:
Za $\forall \varepsilon > 0$ obstaja $\delta > 0$, tako da velja
$$|z - z_0| < \delta \implies |f(z) - f(z_0)| < \varepsilon$$

Poglejmo si, kaj to pomeni:
Spomnimo se:
$$z = x + iy$$
in
$$|z| = (x^2 + y^2)^{\frac{1}{2}}$$
Torej

---

### **Stran 3**
$$|z - z_0| = |(x + iy) - (x_0 + iy_0)| =$$
$$= |(x - x_0) + i(y - y_0)| =$$
$$= \left( (x - x_0)^2 + (y - y_0)^2 \right)^{\frac{1}{2}}$$

Torej, funkcija $f$ je v $z_0$ zvezna, če za vsak $\varepsilon > 0$ obstaja tak $\delta$, da se z $f$ ves krog
$$B_\delta(z_0) = \{z = (x + iy) ; (x - x_0)^2 + (y - y_0)^2 < \delta^2\}$$
preslika v krog
$$B_\varepsilon(f(z_0)) = \{w = (a + ib) ; (a - a_0)^2 + (b - b_0)^2 < \varepsilon^2\}$$
Pri čemer je $(a_0 + ib_0) = w_0 = f(z_0)$.

Vidimo, da je včasih praktično opisati kompleksno funkcijo v koordinatah.

---

### **Stran 4**
Označimo
$$f(z) = u(z) + i v(z)$$
$u$ - realna komponenta $f$
$v$ - imaginarna komponenta $f$

Še bolj eksplicitno:
$$f(x + iy) = u(x, y) + i v(x, y)$$
Kompleksna števila so točke v $\mathbb{R}^2$, torej vektorji v $\mathbb{R}^2$. Pišemo lahko:
$$z = x + iy = \begin{pmatrix} x \\ y \end{pmatrix}$$
in
$$f(z) = u(x, y) + i v(x, y) = \begin{pmatrix} u(x, y) \\ v(x, y) \end{pmatrix}$$

**Primer:** $f(z) = z^2$
$$f(z) = (x + iy)^2 = (x^2 - y^2) + i \cdot 2xy$$
$f(z) = z^3 = ((x^2 - y^2) + i \cdot 2xy)(x + iy) = x^3 - xy^2 - 2xy^2 + \dots$

---

### **Stran 5**
$$\dots + i(2x^2y + x^2y - y^3) = (x^3 - 3xy^2) + i(3x^2y - y^3)$$

**Kompleksni odvod**

**Definicija:** Funkcija
$$f: \Omega \longrightarrow \mathbb{C}$$
je v točki $z_0 \in \Omega$ **kompleksno odvedljiva**, če obstaja tako kompleksno število $A$, da velja
$$f(z_0 + h) = f(z_0) + A \cdot h + \mathcal{O}(h)$$
$$\lim_{h \to 0} \frac{\mathcal{O}(h)}{h} = 0$$

Če tako število obstaja, pišemo
$$A = f'(z_0)$$

Definicijo lahko zapišemo tudi v drugačni obliki:
$$f(z_0 + h) - f(z_0) = A \cdot h + \mathcal{O}(h) \quad / :h$$

---

### **Stran 6**
$$\frac{f(z_0 + h) - f(z_0)}{h} = A + \frac{\mathcal{O}(h)}{h} \quad / \lim_{h \to 0}$$
$$\lim_{h \to 0} \frac{f(z_0 + h) - f(z_0)}{h} = f'(z_0) = A$$

Pri tem je pomembno naslednje. Spremenljivka $h$ potuje proti $0$ v kompleksni ravnini $\mathbb{C} \approx \mathbb{R}^2$. Proti $0$ lahko potuje po različnih poteh.
**Število $A = f'(z_0)$ je neodvisno od izbire poti, po kateri $h$ potuje proti $0$.**

Oglejmo si situacijo v koordinatah. Videli smo: vsaka kompleksna funkcija
$$z \longmapsto f(z)$$
je preslikava $\Omega \subset \mathbb{R}^2$ v $\mathbb{R}^2$. V koordinatah
$$\begin{pmatrix} x \\ y \end{pmatrix} \longmapsto \begin{pmatrix} u(x, y) \\ v(x, y) \end{pmatrix} = \tilde{f}\begin{pmatrix} x \\ y \end{pmatrix}$$

---

### **Stran 7**
Vemo, da je odvod take preslikave podan z matriko $J$:
$$\tilde{f}\left( \begin{pmatrix} x \\ y \end{pmatrix} + \begin{pmatrix} h_1 \\ h_2 \end{pmatrix} \right) = \tilde{f}\begin{pmatrix} x \\ y \end{pmatrix} + J_{(x, y)} \begin{pmatrix} h_1 \\ h_2 \end{pmatrix} + \mathcal{O}(h_1, h_2)$$
$$\lim_{(h_1, h_2) \to (0, 0)} \frac{\mathcal{O}(h_1, h_2)}{\|(h_1, h_2)\|} = 0$$

Vemo:
$$J = \begin{pmatrix} \frac{\partial u}{\partial x} & \frac{\partial u}{\partial y} \\ \frac{\partial v}{\partial x} & \frac{\partial v}{\partial y} \end{pmatrix}$$
Torej:
$$D_{(x, y)} f = \begin{pmatrix} \frac{\partial u}{\partial x} & \frac{\partial u}{\partial y} \\ \frac{\partial v}{\partial x} & \frac{\partial v}{\partial y} \end{pmatrix}_{(x, y)}$$

V primeru, ko je $f$ **kompleksno odvedljiva**, velja:

---

### **Stran 8**
$$f(x + iy) + (h_1 + ih_2) = f(x + iy) + (\alpha + i\beta)(h_1 + ih_2) + \mathcal{O}(h_1 + ih_2)$$

Torej:
$$(\alpha + i\beta)(h_1 + ih_2) = (\alpha h_1 - \beta h_2) + i(\beta h_1 + \alpha h_2)$$

Desno stran lahko zapišemo v vektorsko-matrični obliki:
$$(\alpha h_1 - \beta h_2) + i(\beta h_1 + \alpha h_2) = \begin{pmatrix} \alpha h_1 - \beta h_2 \\ \beta h_1 + \alpha h_2 \end{pmatrix} =$$
$$= \begin{pmatrix} \alpha & -\beta \\ \beta & \alpha \end{pmatrix} \begin{pmatrix} h_1 \\ h_2 \end{pmatrix}$$

Iz zgornjega zapisa vidimo, da je naša matrika $\begin{pmatrix} \alpha & -\beta \\ \beta & \alpha \end{pmatrix}$ natanko Jacobijeva matrika. Torej:
$$\begin{pmatrix} \frac{\partial u}{\partial x} & \frac{\partial u}{\partial y} \\ \frac{\partial v}{\partial x} & \frac{\partial v}{\partial y} \end{pmatrix} = \begin{pmatrix} \alpha & -\beta \\ \beta & \alpha \end{pmatrix}$$

---

### **Stran 9**
Od tod vidimo:
Če je $f$ v $z = z_0$ **kompleksno odvedljiva**, potem mora veljati:
$$\boxed{\begin{aligned} \frac{\partial u}{\partial x} &= \phantom{-}\frac{\partial v}{\partial y} \\ \frac{\partial u}{\partial y} &= -\frac{\partial v}{\partial x} \end{aligned}} \quad (CR)$$

Sistem (CR) se imenuje **Cauchy-Riemannov sistem**.

Dokazali smo izrek:
**Izrek:** Funkcija kompleksne spremenljivke
$$f: \Omega \longrightarrow \mathbb{C}$$
je v $z_0 \in \Omega$ kompleksno odvedljiva natanko

---

### **Stran 10**
takrat, ko v $z_0 = (x_0 + iy_0)$ funkcija
$$f(x + iy) = u(x, y) + i v(x, y)$$
zadošča Cauchy-Riemannovemu sistemu (CR).

**Definicija:** Funkcija, ki je na nekem območju $\Omega \subset \mathbb{C}$ kompleksno odvedljiva, se imenuje **holomorfna funkcija** na $\Omega$.

**Opomba:** Velikokrat je zelo pomembno navesti območje $\Omega$ holomorfnosti.

Oglejmo si še, kaj matrika odvoda holomorfne funkcije dela:
$$\begin{pmatrix} \alpha & -\beta \\ \beta & \alpha \end{pmatrix} = \sqrt{\alpha^2 + \beta^2} \begin{pmatrix} \frac{\alpha}{(\alpha^2 + \beta^2)^{1/2}} & -\frac{\beta}{(\alpha^2 + \beta^2)^{1/2}} \\ \frac{\beta}{(\alpha^2 + \beta^2)^{1/2}} & \frac{\alpha}{(\alpha^2 + \beta^2)^{1/2}} \end{pmatrix}$$

---

### **Stran 11**
Ker je
$$\left( \frac{\alpha}{(\alpha^2 + \beta^2)^{1/2}} \right)^2 + \left( \frac{\beta}{(\alpha^2 + \beta^2)^{1/2}} \right)^2 \equiv 1$$
obstaja $t \in [0, 2\pi)$, tako da je
$$\begin{pmatrix} \alpha & -\beta \\ \beta & \alpha \end{pmatrix} = r \begin{pmatrix} \cos(t) & -\sin(t) \\ \sin(t) & \cos(t) \end{pmatrix}$$
kjer je $r = \sqrt{\alpha^2 + \beta^2}$.

Matrika $J$ torej vektor $(h_1, h_2)^T$ zarotira za kot $t$ in ga podaljša (ali skrajša) za faktor $r = |f'(z_0)|$.
Torej:
$$\begin{pmatrix} \alpha & -\beta \\ \beta & \alpha \end{pmatrix} = |f'(z_0)| \begin{pmatrix} \cos(\text{arg}(f'(z_0))) & -\sin(\text{arg}(f'(z_0))) \\ \sin(\text{arg}(f'(z_0))) & \cos(\text{arg}(f'(z_0))) \end{pmatrix}$$

To pa je natanko opis geometrijskega pomena množenja s kompleksnim številom $f'(z_0)$.

---

### **Stran 12**
**Elementarne holomorfne funkcije**

V prvem letniku ste spoznali funkcijo
$$f(z) = e^z = \exp(z)$$

Spomnimo se razvoja nekaterih funkcij v Taylorjevo vrsto:
$$e^z = e^{x + iy} = e^x \cdot e^{iy} =$$
$$= e^x \left( \sum_{n=0}^\infty \frac{(iy)^n}{n!} \right) = e^x \left( \sum_{k=0}^\infty \frac{(iy)^{2k}}{(2k)!} + \sum_{k=0}^\infty \frac{(iy)^{2k+1}}{(2k+1)!} \right) =$$
$$= e^x \left( \sum_{k=0}^\infty (-1)^k \frac{y^{2k}}{(2k)!} + i \sum_{k=0}^\infty (-1)^k \frac{y^{2k+1}}{(2k+1)!} \right) =$$
$$= e^x (\cos(y) + i \sin(y))$$

Predpis $z \longmapsto e^z$ je torej dobro definiran za vsak $z \in \mathbb{C}$.

---

### **Stran 13**
Poglejmo, ali je $f(z) = e^z$ holomorfna:
$$e^z = e^x (\cos(y) + i \sin(y)) =$$
$$= e^x \cos(y) + i e^x \sin(y)$$

$$u(x, y) = e^x \cos(y)$$
$$v(x, y) = e^x \sin(y)$$

Imamo:
$$\frac{\partial u}{\partial x} = e^x \cos(y), \quad \frac{\partial v}{\partial y} = e^x \cos(y) \implies \frac{\partial u}{\partial x} = \frac{\partial v}{\partial y} \quad \checkmark$$
$$\frac{\partial u}{\partial y} = -e^x \sin(y), \quad \frac{\partial v}{\partial x} = e^x \sin(y) \implies \frac{\partial u}{\partial y} = -\frac{\partial v}{\partial x} \quad \checkmark$$

Torej $e^z$ je holomorfna na celem $\mathbb{C}$.

---

### **Stran 14**
**Def:** Funkcije, ki so holomorfne na celem $\mathbb{C}$, se imenujejo **cele (entire)** funkcije.

Na tem mestu omenimo še en pomemben način ugotavljanja holomorfnosti.

**Laplaceov operator**

**Definicija:** Naj bo funkcija
$$u(x, y) : \Omega \subset \mathbb{R}^2 \longrightarrow \mathbb{R}$$
funkcija dveh spremenljivk. Laplaceov operator
$$\Delta = \frac{\partial^2}{\partial x^2} + \frac{\partial^2}{\partial y^2}$$
priredi funkcijo
$$\Delta(u) = \frac{\partial^2 u}{\partial x^2} + \frac{\partial^2 u}{\partial y^2}$$

---

### **Stran 15**
**Definicija:** Funkcija $u(x, y) : \Omega \longrightarrow \mathbb{R}$, za katero velja
$$\Delta(u) \equiv 0$$
je **harmonična funkcija** na $\Omega$.

**Izrek:** Naj bo
$$f = u + iv : \Omega \longrightarrow \mathbb{C}$$
holomorfna. Potem sta $u$ in $v$ harmonični na $\Omega$.

**Dokaz:** Ker je $f$ holomorfna, velja (CR)
$$u_x = v_y \quad / \frac{\partial}{\partial x}$$
$$u_y = -v_x \quad / \frac{\partial}{\partial y}$$
$$u_{xx} = v_{yx}$$
$$u_{yy} = -v_{xy}$$
Seštejemo in dobimo

---

### **Stran 16**
$$\Delta(u) = u_{xx} + u_{yy} = 0$$
Podobno za $v$. $\square$

Funkcijo $e^z$ smo spoznali preko njene Taylorjeve vrste.

Ali so vse kompleksne funkcije oblike
$$f(z) = \sum_{n=0}^\infty a_n z^n$$
holomorfne?

Oglejmo si najprej holomorfnost $f(z) = z^n$.
$$f(z) = z^n$$

---

### **Stran 17**
$$f(z + h) - f(z) = (z + h)^n - z^n =$$
$$= z^n + \binom{n}{1} z^{n-1} h + \binom{n}{2} z^{n-2} h^2 + \dots + \binom{n}{n-1} z h^{n-1} + h^n - z^n =$$
$$= h \cdot n z^{n-1} + h^2(\dots)$$

Torej
$$\frac{f(z + h) - f(z)}{h} = n z^{n-1} + h(\dots)$$

Limita $\lim_{h \to 0}$ je neodvisna od poti $h$ proti $0$. Torej
$$f'(z) = (z^n)' = n z^{n-1}$$

Vse funkcije $z^n$ so holomorfne.

Očitno je vsaka linearna kombinacija holomorfnih funkcij holomorfna. Dokaz je enak kot pri realni odvedljivosti.

---

### **Stran 18**
Torej: Vsi polinomi
$$f(z) = \sum_{n=0}^N a_n z^n$$
so holomorfne funkcije na $\mathbb{C}$ (cele funkcije).

Kaj pa neskončni polinomi, oz. vrste:
$$f(z) = \sum_{n=0}^\infty a_n z^n$$
Denimo, da zgornja vrsta konvergira za neko $z = z_0$.
To pomeni, da za $\forall \varepsilon > 0$ obstaja $N$, tako da velja
$$m \geq N \implies \left| \sum_{n=m}^\infty a_n z_0^n \right| < \varepsilon$$
Od tod:
$$\left| \sum_{n=m}^\infty a_n z_0^n \right| \geq \left| \sum_{n=m+1}^\infty a_n z_0^n \right|$$

---

### **Stran 19**
$$\left| \sum_{n=m}^\infty a_n z_0^n \right| \leq |a_m z_0^m| + \left| \sum_{n=m+1}^\infty a_n z_0^n \right|$$
$\dots$
Torej:
$$|a_m z_0^m| < 2\varepsilon \quad \text{za } \forall m > N$$

Naj bo sedaj $|z| < |z_0|$. Potem:
$$\sum_{n=0}^\infty |a_n z^n| = \sum_{n=0}^{m-1} |a_n z^n| + \sum_{n=m}^\infty |a_n z^n| =$$
$$= \sum_{n=0}^{m-1} |a_n z^n| + \sum_{n=m}^\infty \left| \frac{z}{z_0} \right|^n |a_n z_0^n| <$$
$$< \sum_{n=0}^{m-1} |a_n z^n| + 2\varepsilon \sum_{n=m}^\infty q^n < \infty$$
kjer je $q = \left| \frac{z}{z_0} \right| < 1$.

Torej: Če vrsta konvergira za neko $z_0$, potem konvergira absolutno za vsak $z$; $|z| < |z_0|$.
Naj bo $r < |z_0|$. Vsaka $\sum a_n z^n$

---

### **Stran 20**
konvergira na $B(0, r) = \{z ; |z| \leq r < |z_0|\}$ enakomerno.

Uporabili smo dejstvo: če vrsta konvergira absolutno, potem konvergira tudi sama, saj
$$\left| \sum_{n=1}^N a_n z^n \right| \leq \sum_{n=1}^N |a_n z^n|$$
za $\forall N$ in zato tudi za $\infty$.

$$\sum_{n=0}^\infty a_n (z + h)^n - \sum_{n=0}^\infty a_n z^n =$$
$$= \sum_{n=0}^\infty a_n z^n + a_n n z^{n-1} h + \dots$$

---

### **Stran 21**
Nazaj k funkciji $f(z) = e^z$.
Ker je
$$e^z = e^{x+iy} = e^x \cos(y) + i e^x \sin(y)$$
sta funkciji
$$u(x, y) = e^x \cos(y)$$
$$v(x, y) = e^x \sin(y)$$
harmonični.

**Vprašanje:** Ali realna (imaginarna) komponenta holomorfne funkcije enolično določa celotno holomorfno funkcijo?
$$z \longmapsto f(z) = u(x, y) + i v(x, y)$$
velja:
$$\frac{\partial u}{\partial x} = \frac{\partial v}{\partial y}$$
$$\frac{\partial u}{\partial y} = -\frac{\partial v}{\partial x}$$

---

### **Stran 22**
Denimo, da poznamo $u$:

Vektorsko polje
$$\left( \frac{\partial v}{\partial x}, \frac{\partial v}{\partial y} \right) = \left( -\frac{\partial u}{\partial y}, \frac{\partial u}{\partial x} \right)$$
je torej potencialno in $v$ je potencial tega polja.
$$v(x, y) = \int_{(x_0, y_0)}^{(x, y)} \left( -\frac{\partial u}{\partial y}, \frac{\partial u}{\partial x} \right) \cdot d\vec{s}$$

Iz eksponentne funkcije lahko prikličemo še nekatere druge pomembne holomorfne funkcije.
Spomnimo se identitete:
$$e^{ix} = \cos(x) + i \sin(x)$$
Potem:
$$e^{-ix} = \cos(x) - i \sin(x)$$

---

### **Stran 23**
Zato
$$\cos(x) = \frac{e^{ix} + e^{-ix}}{2}$$
$$\sin(x) = \frac{e^{ix} - e^{-ix}}{2i}$$

**Definicije:**
$$\cos(z) = \frac{e^{iz} + e^{-iz}}{2}$$
$$\sin(z) = \frac{e^{iz} - e^{-iz}}{2i}$$
$$\cosh(z) = \frac{e^z + e^{-z}}{2}$$
$$\sinh(z) = \frac{e^z - e^{-z}}{2}$$

Lahko je videti, da so Taylorjeve vrste teh funkcij prav take kot vrste za njihove realne analize.

---

# Funkcije kompleksne spremenljivke 2

## Kompleksna integracija

Naj bo $f: \Omega \longrightarrow \mathbb{C}$ funkcija kompleksne spremenljivke. Integral $f$ bo krivuljni integral. Seštevali bomo vrednosti funkcije vzdolž 1-dim objekta. Izkazalo se bo, da je ta konstrukcija najbolj plodna. (Med drugim nam bo dala operator, ki bo na prostorih holomorfnih funkcij "inverzen" kompleksnemu odvajanju).

**Def:** Naj bo $\gamma: [\alpha, \beta] \longrightarrow \Omega$ krivulja in $f: \Omega \longrightarrow \mathbb{C}$.

---

Naj bo $D: \alpha = t_0 < t_1 < \dots < t_n = \beta$ delitev intervala $[\alpha, \beta]$. Integralska vsota funkcije $f$ po krivulji $\gamma$ je:
$$S_D = \sum_{n=0}^{N-1} f(\gamma(t_n)) (\gamma_{n+1} - \gamma_n) = \sum_{n=0}^{N-1} f(\gamma(t_n)) (\gamma(t_{n+1}) - \gamma(t_n))$$

Integral $\int_\gamma f$ je podan s predpisom:
$$\int_\gamma f = \lim_{\delta(D) \to 0} S_D$$

Imamo: $\gamma(t_{n+1}) - \gamma(t_n) \approx \dot{\gamma}(\tau_n)(t_{n+1} - t_n)$, kjer je $\tau_n \in [t_n, t_{n+1}]$.

---

$$S_D \approx \sum_{n=0}^{N-1} f(\gamma(t_n)) \dot{\gamma}(\tau_n) (t_{n+1} - t_n) \approx \sum_{n=0}^{N-1} f(\gamma(\tau_n)) \dot{\gamma}(\tau_n) (t_{n+1} - t_n)$$

Torej:
$$\boxed{\int_\gamma f = \int_\alpha^\beta f(\gamma(t)) \dot{\gamma}(t) dt}$$

### Primeri:
1) $f(z) = z^m$, $\gamma$ enotska krožnica.
Parametrizirajmo $\gamma(t)$:
$\gamma(t) = e^{it} = (\cos(t) + i \sin(t))$, $t \in [0, 2\pi]$.

$$\int_{S^1} z^m dz = \int_0^{2\pi} (e^{it})^m \dot{\gamma}(t) dt = \int_0^{2\pi} e^{imt} (e^{it})' dt = \int_0^{2\pi} e^{imt} i e^{it} dt = i \int_0^{2\pi} e^{i(m+1)t} dt$$

---

$$= \left. \frac{i}{i(m+1)} e^{i(m+1)t} \right|_0^{2\pi} = \frac{1}{m+1} (e^{2\pi i(m+1)} - e^{i(m+1)0})$$

Če $m \neq -1 \Rightarrow \dots = 0$
$$\boxed{\int_{S^1} z^m dz = 0, \quad m \in \mathbb{Z} \setminus \{-1\}}$$

$m = -1$:
$$\int_{S^1} \frac{1}{z} dz = i \int_0^{2\pi} e^{-it} e^{it} dt = i \int_0^{2\pi} dt = 2\pi i$$
$$\boxed{\int_{S^1} \frac{1}{z} dz = 2\pi i}$$

2) Naj bo sedaj $f(z) = \sum_{m=-\infty}^\infty a_m z^m$ vrsta, ki je konvergentna povsod na kolobarju $K(R_1, R_2)$.
*(Slika kolobarja)*

---

Naj bo $S(0, r)$ krožnica s središčem 0 in radijem $r$; $R_1 < r < R_2$.
$$\int_{S(0, r)} f(z) dz = \int_0^{2\pi} \sum_{m=-\infty}^\infty a_m r^m e^{im\phi} i r e^{i\phi} d\phi = \sum_{m=-\infty}^\infty a_m i r^{m+1} \int_0^{2\pi} e^{i(m+1)\phi} d\phi$$
Po zgornjem: $= a_{-1} \cdot 2\pi i$

Torej:
$$\boxed{\int_{S(0, r)} \sum_{m=-\infty}^\infty a_m z^m dz = 2\pi i a_{-1}}$$

**Trditev:** Naj bo $f \in \mathcal{C}(\Omega)$ in $\gamma: [\alpha, \beta] \to \Omega$ pot. Potem je:
$$\left| \int_\gamma f(z) dz \right| \leq \int_\gamma |f(\gamma(s))| ds$$
kjer je $ds = |\dot{\gamma}(t)| dt$.

---

**Dokaz:**
$$\left| \int_\gamma f(z) dz \right| = \left| \int_\alpha^\beta f(\gamma(t)) \dot{\gamma}(t) dt \right| \leq \int_\alpha^\beta |f(\gamma(t))| |\dot{\gamma}(t)| dt = \int_\gamma |f(z)| ds$$
kjer je $ds$ dolžinski element.

## Integracija holomorfnih funkcij

Naj bo sedaj $f: D \longrightarrow \mathbb{C}$ funkcija, ki je holomorfna na omejenem območju $D \subset \mathbb{C}$. Naj bo $\Omega \subset D$ podobmočje s kosoma gladkim robom.
Potem velja:
$$\int_{\partial \Omega} f(z) dz = 0$$

Dokažimo zgornjo trditev:
Označimo: $f(z) = u(z) + i v(z)$

---

Parametrizirajmo $\partial \Omega$; $\partial \Omega: \gamma(t)$ in označimo $\gamma(t) = x(t) + i y(t)$, torej $\dot{\gamma}(t) = \dot{x}(t) + i \dot{y}(t)$.

Imamo:
$$\int_{\partial \Omega} f(z) dz = \int_{\partial \Omega} (u + iv)(\dot{x} + i\dot{y}) dt = \int_{\partial \Omega} (u\dot{x} - v\dot{y}) + i(u\dot{y} + v\dot{x}) dt =$$
$$= \int_{\partial \Omega} (u, -v) \cdot (\dot{x}, \dot{y}) dt + i \int_{\partial \Omega} (v, u) \cdot (\dot{x}, \dot{y}) dt =$$
*Greenove formule:*
$$= \iint_\Omega (-v_x - u_y) dx dy + i \iint_\Omega (u_x - v_y) dx dy =$$
*Cauchy-Riemannove enačbe:*
$$= 0 + i 0 = 0. \quad \square$$

V nadaljevanju bomo potrebovali rezultat, ki je nekoliko močnejši od zgornjega.

---

### Izrek (Cauchyejev izrek)

Naj bo $f: \Omega \longrightarrow \mathbb{C}$ funkcija, ki je zvezna na $\Omega$ in holomorfna na $\Omega \setminus \{a\}$. (Torej, holomorfna povsod na $\Omega$ razen morda v eni točki $a \in \text{Int}(\Omega)$.)
Potem velja:
$$\int_{\partial \Omega} f(z) dz = 0.$$

**Dokaz:** Naj bo $\Delta(a, \varepsilon) = \{z \in \Omega; |z-a| < \varepsilon \}$.
*(Slika območja z majhnim krogom okoli a)*

Označimo: $\Omega_\varepsilon = \Omega \setminus \Delta(a, \varepsilon)$

---

Potem je $\partial \Omega_\varepsilon = \partial \Omega - \partial \Delta(a, \varepsilon)$.

Funkcija $f$ je zvezna na $\Omega$, torej je zvezna na vsakem $\Delta(a, \varepsilon)$ in za $\forall \varepsilon > 0$ velja:
$$|f(z)| \leq \max_{w \in \partial \Delta(a, \varepsilon)} |f(w)|, \quad \forall z \in \partial \Delta(a, \varepsilon)$$

Po zgornjem rezultatu velja:
$$\int_{\partial \Omega_\varepsilon} f(z) dz = \int_{\partial \Omega} f(z) dz + \dots - \int_{\partial \Delta(a, \varepsilon)} f(z) dz = \int_{\partial \Omega} f(z) dz - \int_{\partial \Delta(a, \varepsilon)} f(z) dz = 0$$

Poleg tega velja:
$$\int_{\partial \Omega} f(z) dz = \lim_{\varepsilon \to 0} \int_{\partial \Omega_\varepsilon} f(z) dz$$

---

$$\lim_{\varepsilon \to 0} \int_{\partial \Omega_\varepsilon} f(z) dz = \int_{\partial \Omega} f(z) dz - \lim_{\varepsilon \to 0} \int_{\partial \Delta(a, \varepsilon)} f(z) dz$$

Imamo:
$$\lim_{\varepsilon \to 0} \left| \int_{\partial \Delta(a, \varepsilon)} f(z) dz \right| \leq \lim_{\varepsilon \to 0} \int_{\partial \Delta(a, \varepsilon)} |f(z)| dz \leq \lim_{\varepsilon \to 0} \max_{\partial \Delta(a, \varepsilon)} |f(z)| \cdot 2\pi \varepsilon = 0.$$

Torej:
$$0 = \lim_{\varepsilon \to 0} \int_{\partial \Omega_\varepsilon} f(z) dz = \int_{\partial \Omega} f(z) dz. \quad \square$$

Izrek lahko formuliramo nekoliko drugače:

**Izrek:** Naj bo $f: \Delta(a, R) \to \mathbb{C}$ zvezna in holomorfna na $\Delta(a, R) \setminus \{a\}$. Potem velja:
$$\int_{\partial \Delta(a, \rho)} f(z) dz = 0.$$

---

Še več: Za vsako sklenjeno krivuljo $\gamma: [a, b] \longrightarrow \Delta(a, R)$ velja:
$$\int_\gamma f(z) dz = 0.$$

**Definicija:** Območje $\Omega \subset \mathbb{C}$, ki nima lukenj, je **enostavno povezano območje**.
- Kadarkoli prerežemo enostavno povezano območje, dobimo dva kosa. (To ne velja npr. za kolobar).
- Vsako sklenjeno krivuljo $\gamma \subset \Omega$ (v enostavno p. o.) lahko stisnemo v točko tako, da vse vmesne sklenjene krivulje ostanejo v $\Omega$.

Naj bo sedaj $\Omega \subset \mathbb{C}$ enostavno povezano območje in $f: \Omega \longrightarrow \mathbb{C}$ holomorfna funkcija na $\Omega$.

---

### "Nedoločeni integral" - Aside

**Def:** Nedoločeni integral (primitivna funkcija) holomorfne funkcije $f(z)$ je funkcija $F: \Omega \longrightarrow \mathbb{C}$, podana s predpisom:
$$F(z) = \int_{z_0}^z f(\xi) d\xi,$$
kjer integriramo po poljubni krivulji $\gamma; \gamma(0)=z_0, \gamma(1)=z$ v $\Omega$.

Ker velja $\int_{\gamma \text{ sklenjena}} f(z) dz = 0$, je $F(z)$ neodvisna od izbire poti $\gamma$.
*(Opomba rdeče: $\frac{\int_z^{z+h} f(\xi) d\xi}{h} \to f(z)$)*

**End of aside**

---

Definirajmo sedaj funkcijo:
$$F(z; a) = \begin{cases} \frac{f(z) - f(a)}{z-a} ; & z \neq a \\ f'(a) ; & z = a \end{cases}$$

To je holomorfna funkcija $z$ na $\Omega \setminus \{a\}$ in je zvezna na celotnem $\Omega$. Zato zanjo velja:
$$\int_\gamma F(z; a) dz = 0$$
za vsako sklenjeno pot $v \Omega$.

Naj sedaj krivulja $\gamma$ enkrat obkroži $a \in \Omega$. Velja:
$$0 = \int_\gamma F(z; a) dz = \int_\gamma \frac{f(z) - f(a)}{z-a} dz = \int_\gamma \frac{f(z)}{z-a} dz - f(a) \int_\gamma \frac{dz}{z-a}$$

Za $\gamma$ lahko vzamemo krog $\partial \Delta(a, r)$ za dovolj majhen $r$ in lahko izračunamo $\int_\gamma \frac{dz}{z-a}$:

---

$\gamma(t) = r e^{it} + a \Rightarrow z-a = \gamma(t)-a = r e^{it}, \dot{\gamma}(t) = i r e^{it}$.
$$\int_\gamma \frac{dz}{z-a} = \int_0^{2\pi} \frac{i r e^{it}}{r e^{it}} dt = 2\pi i.$$

Torej:
$$0 = \int_\gamma \frac{f(z)}{z-a} dz - f(a) 2\pi i$$
oziroma:
$$\frac{1}{2\pi i} \int_\gamma \frac{f(z)}{z-a} dz = f(a)$$

Dokazali smo:

### Izrek (Cauchyejeva formula)

Naj bo $\Omega$ enostavno sklenjeno območje, $\gamma$ poljubna (odsekom gladka) krivulja, ki enkrat obkroži $a \in \Omega$ in $f: \Omega \longrightarrow \mathbb{C}$ holomorfna funkcija. Potem velja:
$$\boxed{f(a) = \frac{1}{2\pi i} \int_\gamma \frac{f(z)}{z-a} dz}$$

---

Cauchyejev izrek smo podali bolj splošno, kot velja za območja, ki niso nujno enostavno povezana.

### Izrek (Cauchy)

Naj bo $D \subset \mathbb{C}$ območje in $\Omega \subset D$ podobmočje z odsekovoma gladkim robom. Potem velja za vsak $a \in \text{Int}(\Omega)$:
$$\boxed{f(a) = \frac{1}{2\pi i} \int_{\partial \Omega} \frac{f(z)}{z-a} dz}$$

**Dokaz:**
*(Slika večkratno povezanega območja)*

$$\int_{\partial \Omega} \frac{f(z)}{z-a} dz - \int_{\partial \Delta(a, r)} \frac{f(z)}{z-a} dz = 0$$

---

$$= \int_{\partial \Omega} \frac{f(z)}{z-a} dz - 2\pi i f(a) = 0$$

Torej spet:
$$\int_{\partial \Omega} \frac{f(z)}{z-a} dz = 2\pi i f(a). \quad \square$$

Cauchyejev izrek ima veliko zelo pomembnih posledic. Prva med njimi je dejstvo, da je vsaka holomorfna funkcija tudi analitična.

**Trditev:** Naj bo $\Omega$ enostavno povezano območje in $\gamma \subset \Omega$ sklenjena krivulja z odsekovoma gladkim robom. Naj bo $a \in \Omega$ točka, ki jo $\gamma$ obkroži. Naj bo funkcija $F(a)$ podana z:
$$F(a) = \int_\gamma \frac{f(z)}{z-a} dz$$

Torej velja:
1.) $F(a)$ je odvedljiva po $a$ in
$$F'(a) = \int_\gamma \frac{f(z)}{(z-a)^2} dz$$

---

2.) Naj bo funkcija $F_n$ podana s predpisom:
$$F_n(a) = \int_\gamma \frac{f(z)}{(z-a)^n} dz$$
Tudi $F_n(a)$ je odvedljiva in velja:
$$F_n'(a) = n \int_\gamma \frac{f(z)}{(z-a)^{n+1}} dz$$

**Dokaz:** Očitno odvajanje.

**Izrek:** Če je $f(z)$ na $\Omega$ holomorfna (enkrat kompleksno odvedljiva), potem je neskončnokrat odvedljiva. Na dovolj majhnem krogu $\Delta(a, r)$ velja:
$$z \in \Delta(a, r) \Rightarrow f(z) = \sum_{n=0}^\infty \frac{f^{(n)}(a)}{n!} (z-a)^n$$

**Dokaz:** Spomnimo se, da velja na $\partial \Delta(a, r) = \gamma$:
$$f(a) = \frac{1}{2\pi i} \int_\gamma \frac{f(z)}{z-a} dz$$

---

Torej:
$f'(a) = \frac{1}{2\pi i} \int_\gamma \frac{f(z)}{(z-a)^2} dz$
$f''(a) = \frac{2}{2\pi i} \int_\gamma \frac{f(z)}{(z-a)^3} dz$
$f'''(a) = \frac{3 \cdot 2}{2\pi i} \int_\gamma \frac{f(z)}{(z-a)^4} dz$
$\vdots$
$f^{(n)}(a) = \frac{n!}{2\pi i} \int_\gamma \frac{f(z)}{(z-a)^{n+1}} dz$

Naj bo sedaj, kakor zgoraj, $\Delta(a, r)$ krog s središčem $a$ in radijem $r$. Na $\Delta(a, r)$ je $f(z)$ holomorfna. Naj bo $z \in \text{Int} \Delta(a, r)$. Potem po Cauchyejevi formuli velja:
$$f(z) = \frac{1}{2\pi i} \int_{\partial \Delta(a, r)} \frac{f(\xi)}{\xi-z} d\xi \quad (*)$$

Oglejmo si podrobneje $\frac{1}{\xi-z}$:
$$\frac{1}{\xi-z} = \frac{1}{(\xi-a) + (a-z)} = \frac{1}{\xi-a} \cdot \frac{1}{1 - \frac{z-a}{\xi-a}}$$
Na desni imamo vsoto geometrijske vrste za:

---

$q = \frac{z-a}{\xi-a}$.
Ker je $\xi \in \partial \Delta(a, r)$, $z$ pa je znotraj kroga, je $|\xi-a| > |z-a|$, in zato:
$$|q| = \frac{|z-a|}{|\xi-a|} < 1.$$

*(Slika kroga s točkami a, z, ξ)*

Torej:
$$\frac{1}{\xi-z} = \frac{1}{\xi-a} \sum_{n=0}^\infty \left( \frac{z-a}{\xi-a} \right)^n$$

Vstavimo $v (*)$ in dobimo:
$$f(z) = \frac{1}{2\pi i} \int_{\partial \Delta(a, r)} f(\xi) \frac{1}{\xi-a} \cdot \sum_{n=0}^\infty \left( \frac{z-a}{\xi-a} \right)^n d\xi = \sum_{n=0}^\infty (z-a)^n \cdot \frac{1}{2\pi i} \int_{\partial \Delta(a, r)} \frac{f(\xi)}{(\xi-a)^{n+1}} d\xi$$

Zgoraj smo videli:
$$\frac{1}{n!} f^{(n)}(a) = \frac{1}{2\pi i} \int_{\partial \Delta(a, r)} \frac{f(\xi)}{(\xi-a)^{n+1}} d\xi$$

---

Torej:
$$\boxed{f(z) = \sum_{n=0}^\infty \frac{f^{(n)}(a)}{n!} (z-a)^n}$$

Zapisano nekoliko drugače:
$$f(z) = \sum_{n=0}^\infty c_n (z-a)^n,$$
kjer je
$$c_n = \frac{1}{2\pi i} \int_{\partial \Delta(a, r)} \frac{f(\xi)}{(\xi-a)^{n+1}} d\xi. \quad \square$$

## Laurentova vrsta

Vrste oblike $\sum_{m=-\infty}^\infty c_m (z-a)^m$ se imenujejo **Laurentove vrste**.

Zgornja vrsta je v točki $z_0$ konvergentna, če konvergira vsota:
$$\sum_{n=0}^\infty c_n (z_0-a)^n \quad (1)$$

---

in če prav tako konvergira vsota:
$$\sum_{n=-1}^{-\infty} c_n (z_0-a)^n = \sum_{n=1}^\infty c_{-n} \frac{1}{(z_0-a)^n} \quad (2)$$

Denimo, da vrsta (1) konvergira na disku:
$\Delta(a, R) = \{ z; |z-a| < R \}$

Označimo $\frac{1}{z-a} = t$. Vrsta (2) postane potenčna vrsta:
$\sum_{n=1}^\infty c_{-n} t^n$

Denimo, da je konvergentna na $\Delta(0, 1/\rho) = \{ t; |t| < 1/\rho \}$.
Potem vrsta konvergira na:
$\tilde{\Delta}(a, \rho) = \{ z; |z-a| > \rho \}$

Če je $\rho < R$, potem Laurentova vrsta konvergira na območju:

---

$K(a, \rho, R) = \{ z; \rho < |z-a| < R \}$
To je kolobar s središčem v $a$.

Zunaj $K(a, \rho, R)$ vrsta $\sum_{m=-\infty}^\infty c_m (z-a)^m$ divergira, ker divergira vsaj eden od njenih delov $m < 0, n \geq 0$.

## Razvoj holomorfne funkcije v Laurentovo vrsto

Denimo, da je funkcija:
$$f: K \subset \mathbb{C} \longrightarrow \mathbb{C}$$
holomorfna na nekem kolobarju
$$K = K(a, \rho_1, R) = \{ z; \rho < |z-a| < R \}$$

**Izrek:** Funkcijo, ki je holomorfna na kolobarju $K$, lahko na $K$ razvijemo v Laurentovo vrsto.

**Dokaz:** Vzamemo po potrebi malo manjši kolobar:

---

$K_1 = K(a, \rho_1, R_1); \quad \rho_1 > \rho, \quad R_1 < R$

Dokazali smo, da za holomorfno funkcijo na $K_1 \subset K$ velja:
$$f(z) = \frac{1}{2\pi i} \int_{\partial K_1} \frac{f(\xi)}{\xi-z} d\xi = \frac{1}{2\pi i} \int_{\partial \Delta(a, R_1)} \frac{f(\xi)}{\xi-z} d\xi - \frac{1}{2\pi i} \int_{\partial \Delta(a, \rho_1)} \frac{f(\xi)}{\xi-z} d\xi$$

*(1) in (2) na sliki)*

(1) Naj bo $\xi \in \partial \Delta(a, R_1)$. Spomnimo se:
$$\frac{1}{2\pi i} \int_{\partial \Delta(a, R_1)} \frac{f(\xi)}{\xi-z} d\xi = \sum_{m=0}^\infty c_m (z-a)^m$$
$$c_m = \frac{1}{2\pi i} \int_{\partial \Delta(a, R_1)} \frac{f(\xi)}{(\xi-a)^{n+1}} d\xi$$

(2) Naj bo sedaj $\xi \in \partial \Delta(a, \rho_1)$. Preoblikujemo podintegralno, kot smo že:
$$-\frac{1}{\xi-z} = \frac{1}{(z-a) - (\xi-a)} = \frac{1}{z-a} \cdot \frac{1}{1 - \frac{\xi-a}{z-a}} = \sum_{k=0}^\infty \frac{(\xi-a)^k}{(z-a)^{k+1}}$$
Če $\xi$ leži na $\partial \Delta(a, \rho_1)$, potem $|\frac{\xi-a}{z-a}| = \frac{\rho}{r(z)} < 1$.

---

Torej:
$$-\frac{f(\xi)}{\xi-z} = \sum_{k=0}^\infty \frac{f(\xi)}{(z-a)^{k+1}} (\xi-a)^k$$

Integriramo po $\partial \Delta(a, \rho)$, postavimo $k+1 = -m$ in dobimo:
$$-\int_{\partial \Delta(a, \rho)} \frac{f(\xi)}{\xi-z} d\xi = \sum_{m=-1}^{-\infty} c_m (z-a)^m,$$
kjer je:
$$c_m = \frac{1}{2\pi i} \int_{\partial \Delta(a, \rho)} \frac{f(\xi)}{(\xi-a)^{n+1}} d\xi$$

Kot smo videli, krivuljni integrali, ki nastopajo v izrazih koeficientov $c_n$, niso odvisni od izbire poti $v K$, če so le te poti med seboj homotopne. Torej lahko za integracijski poti pri obeh delih Laurentove vrste vzamemo isto krožnico $\Delta(a, R_0)$, $\rho < R_0 < R$, ali pa kar katerokoli krivuljo v $K$, ki je homotopna.

Zgoraj:
$$f(z) = \sum_{n=-\infty}^\infty c_n (z-a)^n; \quad c_n = \frac{1}{2\pi i} \int_{\partial \Delta(a, R_0)} \frac{f(\xi)}{(\xi-a)^{n+1}} d\xi.$$

---

### Primer:
Razvijmo funkcijo $f(z) = \frac{1}{(1-z)(z+2)}$ v možne vrste.

Imamo:
$$\frac{1}{(1-z)(z+2)} = \frac{A}{1-z} + \frac{B}{z+2} = \frac{A(z+2) + B(1-z)}{(1-z)(z+2)} = \frac{z(A-B) + 2A+B}{(1-z)(z+2)}$$
$A-B = 0, \quad 2A+B = 3A = 1 \Rightarrow A = 1/3, B = 1/3$.

$$\frac{1}{(1-z)(z+2)} = \frac{1}{3} \left( \frac{1}{1-z} + \frac{1}{z+2} \right)$$

Funkcija $\frac{1}{1-z}$ je regularna na $|z|<1$, pa tudi $\frac{1}{z+2}$ je regularna na $|z|<2$.
*(Slika s krožnicama |z|=1 in |z|=2)*

---

Funkcijo pa se da razviti v Laurentovo vrsto na $1 < |z| < 2$.
Ker se da $\frac{1}{1-z}$ razviti v vrsto po potencah $1/z$ za $|z|>1$:
$$\frac{1}{1-z} = -\frac{1}{z} \frac{1}{1 - 1/z} = -\frac{1}{z} \sum_{n=0}^\infty \left( \frac{1}{z} \right)^n = -\sum_{n=1}^\infty \left( \frac{1}{z} \right)^n = -\sum_{n=1}^\infty \frac{1}{z^n}$$

Razvijmo še funkcijo $\frac{1}{z+2}$ v krogu $|z|<2$:
$$\frac{1}{z+2} = \frac{1}{2(1 + z/2)} = \sum_{n=0}^\infty \frac{(-1)^n z^n}{2 \cdot 2^n} = \sum_{n=0}^\infty (-1)^n \frac{z^n}{2^{n+1}}$$

*Rdeče: $f(z) = -\sum_{n=1}^\infty \frac{1}{3z^n} + \sum_{n=0}^\infty \frac{(-1)^n}{3 \cdot 2^{n+1}} z^n$*

Torej: Na območju $|z|<1$ lahko $f(z)$ razvijemo v vrsto:
$$f(z) = \frac{1}{3} \sum (z^n + \frac{(-1)^n}{2^{n+1}} z^n) = \frac{1}{3} \sum (1 + \frac{(-1)^n}{2^{n+1}}) z^n$$

---

To je enostavna Taylorjeva vrsta.
Območje $1 < |z| < 2$ (kolobar):
$$f(z) = \frac{1}{3} \left[ -\sum_{n=1}^\infty \frac{1}{z^n} + \sum_{n=0}^\infty \frac{(-1)^n}{2^{n+1}} z^n \right]$$

Od tod lahko po Cauchyejevi formuli izračunamo:
$$\int_{\partial \Delta(0, \frac{3}{2})} f(z) dz = \frac{1}{3} c_{-1} = -1/3.$$

Po območju $|z|>2$ dobimo samo člene $(1/z)^n$:
$$f(z) = \sum_{n=1}^\infty \frac{(-1)^{n-1} 2^{n-1} - 1}{3 z^n}$$

Spet lahko preverimo:
$$\int_{\partial \Delta(0, \frac{3}{2})} f(z) dz = -1/3.$$

---

## Ničle in poli funkcij kompleksne spremenljivke

**Definicija:** Naj bo $f$ holomorfna na $\Delta(a, R)$. Funkcija $f$ ima **ničlo stopnje $n$** v točki $a$, če obstaja holomorfna funkcija $g$, tako da velja:
$$\frac{f(z)}{(z-a)^n} = g(z)$$

Torej:
$f(z) = (z-a)^n g(z)$
$f(z) = (z-a)^{n+1} h(z); \quad h \text{ ni holomorfna v } z=a$.

Naj bo $f(z)$ razvita v Taylorjevo vrsto okoli $a$:
$f(z) = c_0 + c_1(z-a) + c_2(z-a)^2 + \dots$
Naj bo $n$ najmanjše število, tako da je $c_n \neq 0$.

---

Potem imamo:
$$f(z) = c_n(z-a)^n + c_{n+1}(z-a)^{n+1} + \dots = (z-a)^n (c_n + c_{n+1}(z-a) + \dots) = (z-a)^n g(z).$$
$g(z)$ je že razvita v Taylorjevo vrsto in je zato holomorfna.

Ničle holomorfnih funkcij so izolirane. Naj bo $\Omega$ povezano območje. Ničle holomorfne $f: \Omega \to \mathbb{C}$ na $\text{Int}(\Omega)$ ne morejo imeti stekališča. Če obstaja kakšno stekališče, je $f(z) \equiv 0$. (Se pa lahko stekališče nahaja na $\partial \Omega$).

---

## Izolirane singularne točke in izrek o ostankih

**Definicija:** Naj bo $f: \Omega \setminus \{a\} \longrightarrow \mathbb{C}$ holomorfna, v $a$ pa ne. Potem je $a$ **izolirana singularna točka**.

Naj bo $f$ okoli $a$ razvita v Laurentovo vrsto:
$$f(z) = \sum_{n=0}^\infty c_n (z-a)^n + \sum_{n=-1}^{-\infty} c_n (z-a)^n$$

*(Slika območja z a)*

$R$ - regularni del
$G$ - glavni del

Vedenje regularnega dela v bližini $a$: $R(a) \approx c_0$.

---

Kako pa se vede glavni del?
Predpostavimo, da je glavni del končen:
$$G(z) = \sum_{n=-1}^{-m} c_n (z-a)^n$$

Imamo:
$$G(z) = \frac{c_{-1}}{z-a} + \frac{c_{-2}}{(z-a)^2} + \dots + \frac{c_{-m}}{(z-a)^m} = \frac{1}{(z-a)^m} (c_{-m} + c_{-m+1}(z-a) + \dots + c_{-1}(z-a)^{m-1}).$$

V bližini $z=a$ je:
$$G(z) \approx c_{-m} \frac{1}{(z-a)^m}$$
$$\lim_{z \to a} |G(z)| = \infty.$$

To pomeni, da ima $f(z)$ v $z=a$ **pol stopnje $m$**.

Če ima $G(z)$ neskončno členov, ima $f(z)$ v $z=a$ **bistveno singularnost**.

---

## Izrek o ostankih

Naj bo $f: \Omega \longrightarrow \mathbb{C}$ holomorfna povsod na $\Omega$ razen morda v končno mnogih točkah $a_1, a_2, \dots, a_n \in \Omega$.
Naj bo $\Omega$ kompaktno območje in $\partial \Omega$ kosoma gladka krivulja. ($\partial \Omega \cap \{a_1, \dots, a_n\} = \emptyset$).
Potem velja:
$$\int_{\partial \Omega} f(z) dz = 2\pi i \sum_{a_j \in \Omega} \text{Res}(f, a_j),$$
kjer je $\text{Res}(f, a_j)$ koeficient pri členu $\frac{1}{z-a_j}$ pri razvoju $f$ v Laurentovo vrsto okoli $a_j$.

$\text{Res}(f, a_j)$ - ostanek ali residuum funkcije $f$ v točki $a_j$.

Spomnimo se: Videli smo
$$\int_{\partial \Delta(a, r)} f(z) dz = \int_{\partial \Delta(a, r)} \sum_{n=-\infty}^\infty c_n (z-a)^n dz =$$

---

$$= \sum c_n \int_{\partial \Delta(a, r)} (z-a)^n dz = c_{-1} \int_{\partial \Delta(a, r)} \frac{dz}{z-a} = 2\pi i c_{-1}.$$

**Primer:** $\Omega = \mathbb{C} \setminus \{-1, 3\}$; $f(z) = \frac{1}{(z+1)(z-3)}$.
*(Slika območja s točkama -1, 3 in krivuljo ∂K okoli -1)*

Po izreku velja:
$$\int_{\partial K} f(z) dz = 2\pi i \text{Res}(f, -1)$$

**Primer:** Funkcijo $f(z)$ moramo razviti po potencah $(z+1)$.
$f(z) = \frac{1}{z+1} \cdot \frac{1}{z-3}$. Ta del že imamo, moramo razviti še po $(z+1)$.

---

$\frac{1}{z-3} = \frac{1}{(z+1)-4} = (-1/4) \frac{1}{1 - \frac{z+1}{4}} = (-1/4) \sum_{n=0}^\infty \left( \frac{z+1}{4} \right)^n$

$f(z) = \frac{1}{z+1} \cdot (-1/4) (1 + \frac{z+1}{4} + (\frac{z+1}{4})^2 + \dots) = (-1/4) \frac{1}{z+1} - 1/16 + \dots$

Torej $c_{-1} = -1/4$.
*(Opomba: Integral bi bil po tem $2\pi i (-1/4) = -\pi i/2$, v zapiskih piše le -1/4)*

**Dokaz izreka:**
*(Slika območja z luknjami)*
$\tilde{K} = K \setminus \bigcup_{i=1}^n \Delta(a_i, \rho_i)$

---

Po Cauchyejevem izreku velja:
$$\int_{\partial \tilde{K}} f(z) dz = 0$$

Po drugi strani pa:
$$\int_{\partial \tilde{K}} f(z) dz = \int_{\partial K} f(z) dz - \sum_{n=1}^m \int_{\partial \Delta(a_n, \rho_n)} f(z) dz = 0$$
$$\dots \Rightarrow 2\pi i \text{Res}(f, a_j). \quad \square$$