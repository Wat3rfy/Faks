


Eulerjeva funkcija Gama je definirana s predpisom:
$$\Gamma(x) = \int_{0}^{\infty} t^{x-1} e^{-t} dt $$

Za realna števila je funkcija dobro definirana za $x > 0$.

Do te oblike lahko pridemo s tem ko vidimo da nam odvajanje $t^x$ da $x$. Potem dodamo le še člen ki se nam bo ob per partesu ponavljal in popravljal predznak $e^{-t}$.

Sledi

$$\int_{0}^{\infty}t^{x}e^{-t}dt \Rightarrow 0-\int_{0}^{\infty}xt^{x-1}e^{-t}(-1) = x\int_{0}^{\infty}t^{x-1}e^{-t}$$

Če definiramo $\int_{0}^{\infty}t^{x-1}e^{-t}dt = \Gamma(x)$ potem je 

$$\Gamma(x+1) = x \Gamma(x)$$



**Konvergenca:**
Gama funkcija konvergira pri $t = \infty$ za vsak $x$ (zaradi eksponentne funkcije), pri $t = 0$ pa konvergira za $x > 0$. Konvergenca je enakomerna na vsakem zaprtem intervalu $[a, b] \subset (0, \infty)$. 

Pri $t \to \infty$ integral konvergira najpočasneje pri največjem $x$ v intervalu, t.j. $x=b$.

**Osnovna vrednost:**
$$\Gamma(1) = \int_{0}^{\infty} t^{1-1} e^{-t} dt = \int_{0}^{\infty} e^{-t} dt = \left[ -e^{-t} \right]_{0}^{\infty} = -(e^{-\infty} - e^0) = -(0 - 1) = 1$$

---

**Trditev:** Za vsak $x > 0$ velja rekurzivna zveza:
$$\Gamma(x+1) = x \Gamma(x)$$

**Dokaz:**
Uporabimo metodo integracije po delih (*per partes*):
$u = t^x \quad \Rightarrow \quad du = x t^{x-1} dt$
$dv = e^{-t} dt \quad \Rightarrow \quad v = -e^{-t}$

$$\Gamma(x+1) = \int_{0}^{\infty} t^x e^{-t} dt = \left[ -t^x e^{-t} \right]_{0}^{\infty} + \int_{0}^{\infty} x t^{x-1} e^{-t} dt$$

Prvi del (izvenintegralski člen) pri zgornji meji izgine, saj eksponentna funkcija raste hitreje od katere koli potence:
$$\lim_{t \to \infty} \frac{t^x}{e^t} = 0$$
Pri spodnji meji ($t=0$) je člen prav tako enak 0 (za $x > 0$). Ostane:
$$\Gamma(x+1) = 0 + x \int_{0}^{\infty} t^{x-1} e^{-t} dt = x \Gamma(x) \quad \square$$

---

**Posledica:** Za vsako naravno število $n \in \mathbb{N}$ velja:
$$\Gamma(n+1) = n!$$

**Dokaz:**
Z zaporedno uporabo rekurzije dobimo:
$$\Gamma(n+1) = n \Gamma(n) = n(n-1)\Gamma(n-1) = \dots = n(n-1) \dots 2 \cdot 1 \cdot \Gamma(1)$$
Ker je $\Gamma(1) = 1$, sledi $\Gamma(n+1) = n!$. Funkcija Gama je torej posplošitev fakultete za realna (in kompleksna) števila.

---



**Vrednost $\Gamma\left(\frac{1}{2}\right)$**

$$\Gamma\left(\frac{1}{2}\right) = \int_{0}^{\infty} t^{-1/2} e^{-t} dt$$
Vpeljemo novo spremenljivko $t = u^2 \Rightarrow dt = 2u \, du$:
$$\Gamma\left(\frac{1}{2}\right) = \int_{0}^{\infty} \frac{1}{u} e^{-u^2} (2u \, du) = 2 \int_{0}^{\infty} e^{-u^2} du$$

Vrednost integrala $I = \int_{0}^{\infty} e^{-u^2} du$ (Gaussov integral) izračunamo s prehodom na dvojni integral v polarnih koordinatah. Originalni integral kvadriramo in ker sta spremenljivki $x$ in $y$ neodvisni lahko integrala združimo in integriramo po celotni ravnini.
$$I^2 = \left( \int_{0}^{\infty} e^{-x^2} dx \right) \left( \int_{0}^{\infty} e^{-y^2} dy \right) = \int_{0}^{\infty} \int_{0}^{\infty} e^{-(x^2+y^2)} dx \, dy$$
Preidemo v polarne koordinate $x^2+y^2 = r^2$
$$I^2 = \int_{0}^{\pi/2} d\phi \int_{0}^{\infty} e^{-r^2} r \, dr = \frac{\pi}{2} \left[ -\frac{1}{2} e^{-r^2} \right]_{0}^{\infty} = \frac{\pi}{2} \left( 0 - \left(-\frac{1}{2}\right) \right) = \frac{\pi}{4}$$
Torej je $I = \frac{\sqrt{\pi}}{2}$, iz česar sledi:
$$\Gamma\left(\frac{1}{2}\right) = 2 \cdot \frac{\sqrt{\pi}}{2} = \sqrt{\pi}$$

---

**Trditev (Polovične vrednosti):**

$$\Gamma\left(n + \frac{1}{2}\right) = \frac{(2n)!}{2^{2n} n!} \sqrt{\pi}$$

**Dokaz:**
Z rekurzijo:

$$\Gamma\left(n + \frac{1}{2}\right) = \left(n - \frac{1}{2}\right) \left(n - \frac{3}{2}\right) \dots \frac{3}{2} \cdot \frac{1}{2} \cdot \Gamma\left(\frac{1}{2}\right) = \frac{2n-1}{2} \cdot \frac{2n-3}{2} \dots \frac{1}{2} \sqrt{\pi}$$

Če števec in imenovalec pomnožimo s produktom sodih števil $(2n \cdot (2n-2) \dots 2) = 2^n n!$, dobimo v števcu polno fakulteto $(2n)!$, v imenovalcu pa $2^n \cdot 2^n n! = 2^{2n} n!$.

---

### 2. Eulerjeva funkcija Beta

**Definicija:**
Funkcija Beta je funkcija dveh spremenljivk, definirana za $p, q > 0$:
$$B(p, q) = \int_{0}^{1} t^{p-1} (1-t)^{q-1} dt$$

Velja 

$$B(p, q) = B(q, p)$$ 

kar lahko dokažemo z vpeljavo substitucije $t = 1-u$.

**Povezava s funkcijo Gama:**
  
$$B(p, q) = \frac{\Gamma(p) \Gamma(q)}{\Gamma(p+q)}$$

[!|dokaz]- Dokaz:

$B(p, q) = \int_{0}^{1} x^{p-1} (1-x)^{q-1} dx$

Da bi uporabili polarne koordinate, v integralu za $\Gamma(p)$ spet vpeljemo substitucijo $t = u^2$ ($dt = 2u \, du$):

$$\Gamma(p) = \int_{0}^{\infty} (u^2)^{p-1} e^{-u^2} (2u \, du) = 2 \int_{0}^{\infty} u^{2p-1} e^{-u^2} du$$

Podobno storimo za $\Gamma(q)$, le da uporabimo drugo spremenljivko:

$$\Gamma(q) = 2 \int_{0}^{\infty} v^{2q-1} e^{-v^2} dv$$

Zapišemo produkt $\Gamma(p)\Gamma(q)$ kot dvojni integral

$$\Gamma(p)\Gamma(q) = \left( 2 \int_{0}^{\infty} u^{2p-1} e^{-u^2} du \right) \left( 2 \int_{0}^{\infty} v^{2q-1} e^{-v^2} dv \right)$$
$$= 4 \int_{0}^{\infty} \int_{0}^{\infty} u^{2p-1} v^{2q-1} e^{-(u^2+v^2)} du \, dv$$

Uvedemo polarne koordinate


$$\Gamma(p)\Gamma(q) = 4 \int_{0}^{\pi/2} \int_{0}^{\infty} (r \cos \phi)^{2p-1} (r \sin \phi)^{2q-1} e^{-r^2} r \, dr \, d\phi$$

Razbijemo na radialni in kotni del:

$$\Gamma(p)\Gamma(q) = 4 \left( \int_{0}^{\infty} r^{(2p-1) + (2q-1) + 1} e^{-r^2} dr \right) \left( \int_{0}^{\pi/2} \cos^{2p-1} \phi \sin^{2q-1} \phi \, d\phi \right)$$

Poenostavimo potenco pri $r$: $(2p-1) + (2q-1) + 1 = 2(p+q)-1$.

$$\Gamma(p)\Gamma(q) = \left( 2 \int_{0}^{\infty} r^{2(p+q)-1} e^{-r^2} dr \right) \cdot \left( 2 \int_{0}^{\pi/2} \cos^{2p-1} \phi \sin^{2q-1} \phi \, d\phi \right)$$



Dobili smo
$$\Gamma(p)\Gamma(q) = \Gamma(p+q) \cdot B(p, q)$$
Oziroma
$$B(p, q) = \frac{\Gamma(p)\Gamma(q)}{\Gamma(p+q)}$$

*Izpeljava še drugih oblik beta funckija to come mogoce ce se mi bo dal nevem ciws zihr nism idk upam al neki who knows*