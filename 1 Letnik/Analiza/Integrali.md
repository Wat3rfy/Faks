


> Funkcija $F$, definirana na intervalu $I$, se imenuje **primitivna funkcija** ali **nedoločeni integral** funkcije $f$, če je na $I$ funkcija $f$ enaka odvodu funkcije $F$; torej če velja
> $$F'(x) = f(x) \;  \text{za vsak } x \in I.$$

$$ $$

> 
> Naj bo $F$ primitivna funkcija funkcije $f$ na intervalu $I$. Tedaj je za vsako konstanto $C$ tudi funkcija $G$,
> $$G(x) = F(x) + C, \quad x \in I$$
> primitivna funkcija funkcije $f$.
>>[!|dokaz]- Dokaz:
> > **Dokaz:** $G'(x) = (F(x) + C)' = F'(x) + C' = F'(x) = f(x)$. $G$ je primitivna funkcija.


**Oznaka:** Če je $F$ primitivna funkcija funkcije $f$, je diferencial
$$dF(x) = F'(x)dx$$
oziroma
$$dF(x) = f(x)dx$$
Zato pišemo tudi
$$F(x) = \int f(x)dx.$$
*Seštevamo vse majhne spremembe $dF(x)$ čez 0 do x*

Ker je integriranje nasprotna operacija odvajanju, pravila za integriranje sledijo iz pravil za odvajanje.

1.
$$\int (f(x) + g(x))dx = \int f(x)dx + \int g(x)dx$$
2.
$$\int (\lambda f)(x)dx = \lambda \int f(x)dx, \quad \lambda \text{ je konstanta}$$
3.
$$\int (\lambda f + \mu g)(x)dx = \lambda \int f(x)dx + \mu \int g(x)dx, \quad \lambda, \mu \text{ sta konstanti}$$
4.
$$\text{per partes: }\int f(x)g'(x)dx = f(x)g(x) - \int g(x)f'(x)dx$$
$$\int udv = uv - \int vdu.$$
>[!|dokaz]- Dokaz:
>
> $$(f(x)g(x))' = f'(x)g(x) + f(x)g'(x)$$
> sledi
> $$f(x)g(x) = \int (f'(x)g(x) + f(x)g'(x))dx$$
> $$= \int f'(x)g(x)dx + \int f(x)g'(x)dx,$$
> torej
> $$\int f(x)g'(x)dx = f(x)g(x) - \int g(x)f'(x)dx$$

5. Uvedba nove spremenljivke Naj bo $F$ primitivna funkcija funkcije $f$ in $\varphi$ takšna odvedljiva funkcija, da je $F \circ \varphi$ definirana. Tedaj je
$$(F \circ \varphi)'(t) = F'(\varphi(t))\varphi'(t)$$
$$= f(\varphi(t))\varphi'(t),$$
torej
$$F(\varphi(t)) + C = \int f(\varphi(t))\varphi'(t)dt.$$

>[!|txt]- **Integral racionalne funkcije**
> 
> 
> $$\int \frac{P(x)}{Q(x)}dx, \quad P(x), Q(x) \text{ polinoma z realnimi koeficienti}$$
> 
> i) če je $\text{st}(P(x)) \ge \text{st}(Q(x))$, ju delimo in dobimo
> 
> $$P(x) = R(x)Q(x) + T(x)$$
> 
> oziroma
> 
> $$\frac{P(x)}{Q(x)} = R(x) + \frac{T(x)}{Q(x)},$$
> 
> pri čemer je $\text{st}(T(x)) < \text{st}(Q(x))$. Naprej sledi:
> 
> $$\int \frac{P(x)}{Q(x)}dx = \int R(x)dx + \int \frac{T(x)}{Q(x)}dx.$$
> 
> ii) poiščemo vse ničle polinoma $Q(x)$.
> 
> - polinom $Q(x)$ ima vse ničle realne
> 
> $$Q(x) = a(x - x_1)^{k_1}(x - x_2)^{k_2} \ldots (x - x_n)^{k_n}$$
> 
> Potem lahko izraz $T(x)/Q(x)$ zapišemo:
> 
> $$\frac{T(x)}{Q(x)} = \frac{A_1^1}{x - x_1} + \frac{A_2^1}{(x - x_1)^2} + \ldots + \frac{A_{k_1}^1}{(x - x_1)^{k_1}} + \frac{A_1^2}{x - x_2} + \frac{A_2^2}{(x - x_2)^2} + \ldots, \quad A_j^i \text{ so realna števila}$$

**Približek ploščine pod krivuljo**

Naj bo $f$ pozitivna zvezna funkcija na zaprtem intervalu $[a, b]$. 

Na $x$-osi izberemo delilne točke
$$a = x_0 < x_1 < \ldots < x_{n-1} < x_n = b,$$
tj. točke, ki razdelijo interval $[a, b]$ na $n$-kosov. Naj bo za vsak $k, k \in \{1, 2, \ldots, n\}$,
$$x_k - x_{k-1} = \delta_k$$
dolžine $k$-tega kosa podintervala intervala $[a, b]$. V vsakem podintervalu izberemo neko točko $\xi_k$, torej
$$\xi_k \in [x_{k-1}, x_k], \quad k \in \{1, 2, \ldots, n\}.$$
Ploščina $k$-tega pravokotnika je enaka $f(\xi_k)\delta_k$, slika 5.1. Vsota ploščin vseh pravokotnikov pa je
$$f(\xi_1)\delta_1 + f(\xi_2)\delta_2 + \ldots + f(\xi_n)\delta_n = \sum_{k=1}^{n} f(\xi_k)\delta_k.$$

To je približek za ploščino pod krivuljo. Ploščina je enaka limiti teh približkov, ko gre dolžina najdaljšega intervala proti 0 (pri tem pa se seveda število delilnih točk čez vse meje). 




Velja da ko za vsak $\varepsilon$ obstaja $\delta$ da za vsako delitev $D$ velja $\delta > \sup \delta_i$ kot dolžina najdaljšega intervala, bo **riemannova vsota konvergirala k $I$** natanko tedaj ko velja
$$\left(\sum_{i=1}^{n}f(\xi_{i})\delta_{i}\right) - I < \varepsilon$$


Če za funkcijo $f$, definirano na $[a,b]$, obstaja limita $I$ Riemannovih vsot, ko gre dolžina najdaljšega intervala proti 0, pravimo da je funkcija na intervalu $[a,b]$ **integrabilna**, limito $I$ pa imenujemo **določen integral** funkcije $f$ v mejah od $a$ do $b$ in pišemo:
$$I = \int_{a}^{b} f(x)dx.$$

Število $I$ imenujemo tudi **Riemannov integral** oz. **določeni integral** funkcije $f$ na $[a,b]$.


>Če je funkcija $f$ integrabilna na $[a,b]$, je funkcija $f$ na $[a,b]$ omejena.
>
> >[!|dokaz]- Dokaz:
> >Naj bo $f$ na $[a,b]$ integrabilna. Recimo, da $f$ ni navzgor omejena. Naj bo $\varepsilon > 0$. Naj bo $I$ integral funkcije $f$. Tedaj obstaja $\delta > 0$, da je
> > $$\left| \sum_{k=1}^{n} f(\xi_k)\delta_k - I \right| < \varepsilon, \quad \text{čim je } \max \delta_k < \delta.$$
> > Naj bo $a = x_0 < x_1 < \ldots < x_n = b$ neka delitev, kjer je dolžina $\max \delta_k < \delta$.
> > Tedaj velja $(\ast)$ za vsako izbiro točk $\xi_k \in [x_{k-1}, x_k]$. Ker $f$ ni navzgor omejena, lahko vsaj na enem od intervalov $[x_{k-1}, x_k]$ izberemo $\xi_{k_0}$ tako, da bo $f(\xi_{k_0})$ poljubno veliko pozitivno število, torej tudi $f(\xi_{k_0})\delta_{k_0}$ poljubno veliko pozitivno število. To pa je v protislovju z $(\ast)$. Protislovje kaže, da je začetna predpostavka, da $f$ ni navzgor omejena, napačna. Torej je funkcija $f$ navzgor omejena. Podobno pokažemo, da je funkcija $f$ navzdol omejena. $\square$
> > 

**Darbouxeva vsota**

Naj bo $f$ omejena na $[a,b]$. Naj bo
$$m = \inf \{f(x) : x \in [a,b]\}$$
in
$$M = \sup \{f(x) : x \in [a,b]\}.$$
$\mathcal{D}$ naj bo poljubna delitev
$$a = x_0 < x_1 < \ldots < x_{n-1} < x_n = b.$$
Naj bo
$$m_k = \inf \{f(x) : x \in [x_{k-1}, x_k]\}$$
in
$$M_k = \sup \{f(x) : x \in [x_{k-1}, x_k]\}.$$
Jasno je
$$m \le m_k \le M_k \le M, \quad k \in \{1, 2, \ldots, n\}.$$
Vsota
$$m_1\delta_1 + m_2\delta_2 + \ldots + m_n\delta_n$$
je natančno določena z delitvijo $\mathcal{D}$. Imenujemo jo **spodnja Darbouxova vsota**, prirejena delitvi $\mathcal{D}$. Označimo jo $s(\mathcal{D})$.
$$s(\mathcal{D}) := \sum_{k=1}^{n} m_k\delta_k, \quad k \in \{1, 2, \ldots, n\},$$
pri tem je
$$\delta_k = x_k - x_{k-1}.$$
**Zgornja Darbouxova vsota**, prirejena delitvi $\mathcal{D}$, je
$$S(\mathcal{D}) := \sum_{k=1}^{n} M_k\delta_k, \quad k \in \{1, 2, \ldots, n\}.$$
Vedno velja
$$s(\mathcal{D}) \le S(\mathcal{D}),$$
ker je $m \le m_k \le M_k \le M$ za vsak $k$ in zato tudi
$$\sum_{k=1}^{n} m\delta_k \le \sum_{k=1}^{n} m_k\delta_k \le \sum_{k=1}^{n} M_k\delta_k \le \sum_{k=1}^{n} M\delta_k.$$
Torej
$$m(b-a) \le s(\mathcal{D}) \le S(\mathcal{D}) \le M(b-a).$$
$$ $$
>Pravimo da je delitev $D'$ finejša če vsebuje vse delitvene točke $D$ oz. $D \subset D'$


> Naj bo $D \subset D'$. Tedaj je $s(D) \le s(D')$, $S(D') \le S(D)$, tj. pri prehodu na finejšo delitev se spodnja vsota ne zmanjša, zgornja vsota pa se ne poveča.
> 
> >[!|dokaz]- Dokaz:
> > Delitev $D'$ lahko dobimo iz delitve $D$ tako, da dodajamo po eno točko naenkrat. Zato je dovolj dokazati izrek za primer, ko ima $D'$ natanko eno točko več od $D$.
> > 
> > Naj bo $x_i' \in (x_{i-1}, x_i)$ nova delilna točka. Razdelimo $[x_{i-1}, x_i]$ na dva dela, tj. $[x_{i-1}, x_i']$ in $[x_i', x_i]$. Naj bo $m_i' = \inf\{f(x), x \in [x_{i-1}, x_i']\}$, $M_i' = \sup\{f(x), x \in [x_{i-1}, x_i']\}$ in $m_i'' = \inf\{f(x), x \in [x_i', x_i]\}$, $M_i'' = \sup\{f(x), x \in [x_i', x_i]\}$. Na skupnih intervalih delitve $D'$ in $D$ imata vsoti $s(D')$ in $s(D)$ iste člene. Na $i$-tem intervalu ima $s(D)$ člen $m_i \delta_i$, $s(D')$ pa ima dva člena: $m_i'(x_i' - x_{i-1})$ in $m_i''(x_i - x_i')$.
> > 
> > 
> > Ker je $m_i' \ge m_i$ in $m_i'' \ge m_i$, sledi
> > $$m_i'(x_i' - x_{i-1}) + m_i''(x_i - x_i') \ge m_i(x_i' - x_{i-1}) + m_i(x_i - x_i')$$
> > $$= m_i(x_i' - x_{i-1} + x_i - x_i')$$
> > $$= m_i \delta_i.$$
> > Sledi $s(D') \ge s(D)$. Podobno velja za $S(D') \le S(D)$.

>Omejena funkcija $f$ je na $[a,b]$ integrabilna po Darbouxu natanko tedaj, ko za vsak $\varepsilon > 0$ obstaja takšna delitev $D$, da je:
$$|S(D) - s(D)| < \varepsilon.$$
> 
>>[!|dokaz]- Dokaz:
>>
> >
> >($\Rightarrow$) Recimo, da je $f$ integrabilna po Darbouxu. Potem je
> > $$I_1 = I_2 \quad \text{oz.} \quad I := \sup s(D) = \inf S(D).$$
> > Naj bo $\varepsilon > 0$ poljubno majhen. Ker je $I = I_1$, obstaja takšna delitev $D_1$, da je $|s(D_1) - I| < \varepsilon/2$. Ker je $I = I_2$, obstaja takšna delitev $D_2$, da je $|S(D_2) - I| < \varepsilon/2$. Sledi:
> > $$S(D_2) - s(D_1) = |S(D_2) - s(D_1)|$$
> > $$\le |s(D_1) - I| + |I - S(D_2)|$$
> > $$< \frac{\varepsilon}{2} + \frac{\varepsilon}{2} = \varepsilon$$
> > Naj bo $D = D_1 \cup D_2$. Vemo: $s(D_1) \le s(D)$ in $S(D) \le S(D_2)$. Zato je
> > $$S(D) - s(D) \le S(D_2) - s(D_1) < \varepsilon.$$
> > ($\Leftarrow$) Naj za vsak $\varepsilon > 0$ obstaja takšna delitev $D$, da je $|S(D) - s(D)| < \varepsilon$. Ker je $s(D) \le I_1 \le I_2 \le S(D)$, sledi, da za vsak $\varepsilon > 0$ velja $|I_2 - I_1| < \varepsilon$ oz. $I_1 = I_2$. Torej je $f$ integrabilna po Darbouxu. $\square$
> 

>Vsaka na $[a,b]$ zvezna funkcija je integrabilna po Darbouxu
>
>>[!|dokaz]- Dokaz:
>>
> >Naj bo $f$ zvezna na $[a,b]$. Tedaj vemo, da je $f$ na $[a,b]$ enakomerno zvezna in omejena. Naj bo $\epsilon > 0$ poljubno majhen. Ker je $f$ enakomerno zvezna na $[a,b]$, obstaja takšen $\delta > 0$, da je $|f(\tilde{x}) - f(x)| < \epsilon/(b-a)$, čim je $|\tilde{x} - x| < \delta$, $\tilde{x},x \in [a,b]$. Naj bo $D$ delitev, pri kateri je dolžina najdaljšega intervala manjša od $\delta$. Če sta $\tilde{x},x$ na enem od podintervalčkov $[x_{k-1},x_k]$, je $|f(\tilde{x})-f(x)| < \epsilon/(b-a)$ in zato $|M_k-m_k| \le \epsilon/(b-a)$, za vsak $k \in \{1,2,\dots,n\}$.
> > 
> > Ker je $\sum_{k=1}^n \delta_k = b-a$, sledi, da je
> > $$
 \begin{aligned} S(D) - s(D) &= \sum_{k=1}^n M_k\delta_k - \sum_{k=1}^n m_k\delta_k \\ &= \sum_{k=1}^n (M_k - m_k)\delta_k \\ &\le \sum_{k=1}^n \frac{\epsilon}{b-a}\delta_k \\ &= \frac{\epsilon}{b-a}\sum_{k=1}^n \delta_k \\ &= \epsilon. \end{aligned}
> >  $$
> > Po izreku 49 sledi, da je $f$ integrabilna po Darbouxu. $\square$


>Vsaka na $[a,b]$ monotona funkcija je integrabilna po Darbouxu.
>>[!|dokaz]- Dokaz:
> >Naj bo $f$ monotona, npr. naraščajoča na $[a,b]$. Naj bo $D = \{a = x_0 < a_1 < \dots < x_n = b\}$ delitev. Tedaj je $m = f(a)$, $M = f(b)$ in $M_k - m_k \le f(x_k) - f(x_{k-1})$. Zato je
> > $$\begin{aligned} S(D) - s(D) &= \sum_{k=1}^n M_k\delta_k - \sum_{k=1}^n m_k\delta_k \\ &= \sum_{k=1}^n (M_k - m_k)\delta_k \\ &\le \sum_{k=1}^n (f(x_k) - f(x_{k-1}))\delta_k \\ &\le (f(x_1) - f(a) + f(x_2) - f(x_1) + \dots + f(b) - f(x_{n-1}))\delta \\ &= (f(b) - f(a))\delta, \end{aligned}$$
> > 
> > kjer je $\delta$ dolžina najdaljšega intervala. Sklep: Če je dolžina najdaljšega intervala enaka $\delta$, je
> > $$ S(D) - s(D) \le \delta(f(b) - f(a)) = \delta(M - m), $$
> > kar pa je poljubno majhno ob dovolj fini delitvi, tj. ob dovolj majhnem $\delta$. Torej za vsak $\epsilon > 0$ lahko najdemo delitev $D$, da bo $S(D) - s(D) < \epsilon$. Delitev seveda vzamemo tako fino, da je $\delta(M - m) < \epsilon$. To pomeni, da je $f$ integrabilna po Darbouxu. $\square$



***
Dokaz izreka o substituciji temelji na **verižnem pravilu za odvajanje** sestavljenih funkcij. Integriranje je namreč obratna operacija odvajanja.

Tukaj je izpeljava korak za korakom.

---

### 1. Predpostavke
Naj bo:
1.  $f(u)$ funkcija, ki ima primitivno funkcijo $F(u)$. To pomeni, da velja:
    $$F'(u) = f(u)$$
2.  $u = g(x)$ odvedljiva funkcija spremenljivke $x$.

### 2. Izpeljava s pomočjo verižnega pravila
Zanima nas odvod sestavljene funkcije $F(g(x))$. Po **verižnem pravilu** (odvod zunanje funkcije krat odvod notranje) velja:

$$\frac{d}{dx} [F(g(x))] = F'(g(x)) \cdot g'(x)$$

Ker smo v predpostavki rekli, da je $F'(u) = f(u)$, lahko namesto $F'(g(x))$ zapišemo $f(g(x))$:

$$\frac{d}{dx} [F(g(x))] = f(g(x)) \cdot g'(x)$$

### 3. Prehod na integral
Zdaj uporabimo definicijo nedoločenega integrala. Če je odvod funkcije $A$ enak funkciji $B$, potem je integral funkcije $B$ enak funkciji $A$ (plus konstanta):

$$\int f(g(x)) \cdot g'(x) \, dx = F(g(x)) + C$$

### 4. Uvedba nove spremenljivke
Vemo, da je $F(u) + C$ pravzaprav integral funkcije $f(u) \, du$:
$$F(u) + C = \int f(u) \, du$$

Če združimo oba dela, dobimo končno formulo za substitucijo:

$$\int f(g(x)) \cdot g'(x) \, dx = \int f(u) \, du$$
kjer je $u = g(x)$.

---

### Povzetek v jeziku diferencialov (praktični dokaz)
V praksi dokaz pogosto vidimo skozi Leibnizov zapis diferencialov, kar je za računanje najbolj intuitivno:

1.  Vzamemo $u = g(x)$.
2.  Diferencial $u$-ja je $du = g'(x) dx$.
3.  Vstavimo to v integral:
    $$\int f(\underbrace{g(x)}_{u}) \cdot \underbrace{g'(x) \, dx}_{du} = \int f(u) \, du$$

**Sklep:** Izrek o substituciji je le prepis verižnega pravila za odvajanje v obratno smer. Kar je pri odvajanju "veriga" ($g'(x)$), je pri integriranju tisti del, ki ga moramo "pospraviti" v $du$, da lahko integral rešimo.


Če integral na prvi pogled nima oblike $f(g(x)) \cdot g'(x) \, dx$, imamo na voljo več strategij. Substitucija je namreč bolj prilagodljiva, kot se zdi na začetku.

Tukaj so trije najpogostejši scenariji:

### 1. Manjka nam samo konstanta (najpogostejši primer)
Če imamo v integralu "skoraj" odvod, a nam manjka številka, si jo preprosto sposodimo.

**Primer:** $\int \sin(5x) \, dx$
*   Notranja funkcija je $g(x) = 5x$.
*   Njen odvod je $g'(x) = 5$. V integralu nimamo petke.
*   **Rešitev:** Integral pomnožimo in delimo s 5.
    $$\int \sin(5x) \, dx = \frac{1}{5} \int 5 \cdot \sin(5x) \, dx$$
    Zdaj uvedemo $u = 5x$ in $du = 5 \, dx$:
    $$\frac{1}{5} \int \sin(u) \, du = -\frac{1}{5} \cos(u) + C = -\frac{1}{5} \cos(5x) + C$$

---

### 2. "Odvečni" $x$ (Izražava $x$ iz $u$)
Včasih imamo v integralu več $x$-ov, kot jih potrebujemo za odvod. Takrat iz enačbe za $u$ izrazimo $x$.

**Primer:** $\int x \sqrt{x-1} \, dx$
*   Izberemo $u = x - 1$.
*   Diferencial je $du = dx$.
*   **Težava:** Pred korenom nam ostane $x$.
*   **Rešitev:** Iz $u = x - 1$ izrazimo $x = u + 1$ in to vstavimo v integral.
    $$\int (u+1) \sqrt{u} \, du = \int (u \cdot u^{1/2} + u^{1/2}) \, du = \int (u^{3/2} + u^{1/2}) \, du$$
    To zdaj preprosto integriramo kot potenco.

---

### 3. Obratna substitucija (Trigonometrična substitucija)
Včasih $x$ namenoma zamenjamo s celo funkcijo (npr. $\sin t$ ali $\tan t$), da se znebimo korenov. To uporabljamo pri izrazih tipa $\sqrt{a^2 - x^2}$.

**Primer:** $\int \sqrt{1 - x^2} \, dx$
*   Tukaj sploh ni videti nobenega odvoda.
*   **Rešitev:** Uvedemo $x = \sin(t)$. Potem je $dx = \cos(t) \, dt$.
    $$\int \sqrt{1 - \sin^2(t)} \cdot \cos(t) \, dt = \int \sqrt{\cos^2(t)} \cdot \cos(t) \, dt = \int \cos^2(t) \, dt$$
    To nato rešimo s trigonometričnimi identitetami.

---

### 4. Kaj če substitucija sploh ne deluje?
Če nobena od zgornjih metod ne pomaga in v integralu ni nobene povezave med deli funkcije (npr. množenje dveh popolnoma različnih tipov funkcij), potem substitucija verjetno ni pravo orodje.

V tem primeru uporabimo:
1.  **Integracijo po delih (per partes):** Če imamo npr. $\int x \cdot e^x \, dx$. Tukaj $x$ ni odvod od $e^x$, zato uporabimo per partes.
2.  **Razcep na parcialne ulomke:** Če imamo racionalno funkcijo (ulomek), npr. $\int \frac{1}{x^2 - 5x + 6} \, dx$.
3.  **Linearne transformacije:** Če gre za preproste premike.

**Povzetek:** Substitucijo lahko "vsilimo" tako, da konstante premikamo ven iz integrala ali pa da iz $u$ izrazimo $x$. Če pa sta funkciji v produktu popolnoma tuji (npr. polinom in logaritem), raje poskusimo z metodo *per partes*.

Tale primer je odličen, ker pokaže, kako "prisilimo" integral, da ustreza definiciji in dokazu, ki smo ga spoznali prej.

Spomnimo se definicije:
$$\int f(g(x)) \cdot g'(x) \, dx = \int f(u) \, du$$

Poglejmo, kako tvoj primer $\int x \sqrt{x-1} \, dx$ razstavimo na te elemente:

### 1. Določitev $g(x)$ in $g'(x)$
Izberemo notranjo funkcijo:
*   **$g(x) = x - 1$** (to bo naš $u$)
*   Odvod te funkcije je $g'(x) = 1$.

### 2. Iskanje funkcije $f(u)$
Tukaj nastane težava: v integralu imamo še tisti "odvečni" $x$ spredaj. Da bi integral ustrezal obliki $f(g(x))$, moramo celoten izraz pod integralom zapisati le s pomočjo $g(x)$.

Če je $u = x - 1$, potem sledi, da je **$x = u + 1$**.

Zdaj lahko celoten integral zapišemo v obliki $f(g(x)) \cdot g'(x)$:
$$\int \underbrace{( \overbrace{(x-1)}^{g(x)} + 1 ) \cdot \sqrt{\overbrace{x-1}^{g(x)}}}_{f(g(x))} \cdot \underbrace{1}_{g'(x)} \, dx$$

Tukaj je naša funkcija $f(u)$ torej: **$f(u) = (u+1)\sqrt{u}$**.

### 3. Prehod na $u$ (po definiciji)
Po izreku o substituciji to postane:
$$\int f(u) \, du = \int (u+1)\sqrt{u} \, du$$

### 4. Izračun (algebrski del)
Integral razbijemo, da ga lahko rešimo s potencami ($\sqrt{u} = u^{1/2}$):
$$\int (u \cdot u^{1/2} + 1 \cdot u^{1/2}) \, du = \int (u^{3/2} + u^{1/2}) \, du$$
$$= \frac{u^{5/2}}{5/2} + \frac{u^{3/2}}{3/2} + C = \frac{2}{5}u^{5/2} + \frac{2}{3}u^{3/2} + C$$

### 5. Povezava z dokazom (Verižnim pravilom)
Dokaz pravi: če rezultat odvajamo, moramo dobiti prvotno funkcijo. Preverimo, če to drži za naš rezultat $F(x) = \frac{2}{5}(x-1)^{5/2} + \frac{2}{3}(x-1)^{3/2}$.

Odvajajmo po verižnem pravilu:
1.  Odvod prvega dela: $\frac{2}{5} \cdot \frac{5}{2}(x-1)^{3/2} \cdot 1 = (x-1)^{3/2}$
2.  Odvod drugega dela: $\frac{2}{3} \cdot \frac{3}{2}(x-1)^{1/2} \cdot 1 = (x-1)^{1/2}$

Skupaj:
$$(x-1)^{3/2} + (x-1)^{1/2}$$
Izpostavimo skupni faktor $(x-1)^{1/2}$ (kar je $\sqrt{x-1}$):
$$(x-1)^{1/2} \cdot [ (x-1) + 1 ] = \sqrt{x-1} \cdot x = x\sqrt{x-1}$$

**Dobili smo točno to, kar je bilo na začetku pod integralom!**

### Zaključek:
Ta primer deluje po definiciji tako, da:
1.  **$g(x)$** "pospravi" tisto, kar je pod korenom.
2.  **$f(u)$** mora vsebovati vse ostale $x$-e, ki smo jih morali izraziti z $u$.
3.  **$g'(x)$** je v tem primeru le nevidna "1", ki pa je ključna, da diferencial $dx$ postane $du$.

Da bi razumel, kako sinusna substitucija (npr. $x = \sin(t)$) deluje po **definiciji** in **dokazu**, moraš razumeti, da gre za isto formulo, le da jo beremo v **nasprotno smer**.

Standardna formula substitucije je:
$$\int f(g(x)) \cdot g'(x) \, dx = \int f(u) \, du$$

Pri sinusni substituciji pa uporabljamo **izrek o obratni substituciji**:
$$\int f(x) \, dx = \int f(g(t)) \cdot g'(t) \, dt$$
(Kjer je $x = g(t)$, v našem primeru $x = \sin(t)$).

---

### 1. Skladnost z definicijo
Definicija pravi, da moramo vsak del integrala na levi strani zamenjati z ustreznim delom na desni.

Poglejmo integral $I = \int \sqrt{1-x^2} \, dx$:

*   **Funkcija pod integralom $f(x)$:** To je $\sqrt{1-x^2}$.
*   **Substitucija (uvedba nove spremenljivke):** Izberemo $x = \sin(t)$. Torej je naša funkcija $g(t) = \sin(t)$.
*   **Diferencial $dx$:** Po definiciji je $dx = g'(t) \, dt$.
    Ker je $g(t) = \sin(t)$, je njegov odvod $g'(t) = \cos(t)$.
    Zato je **$dx = \cos(t) \, dt$**.

**Združitev po definiciji:**
Vstavimo $g(t)$ namesto $x$ in $g'(t)dt$ namesto $dx$:
$$\int f(g(t)) \cdot g'(t) \, dt = \int \sqrt{1-\sin^2(t)} \cdot \cos(t) \, dt$$

---

### 2. Skladnost z dokazom (Verižno pravilo)
Dokaz izreka o substituciji temelji na dejstvu, da je **integral odvoda enak prvotni funkciji**. Poglejmo, kako se to ujema pri $x = \sin(t)$.

Naj bo $F(x)$ primitivna funkcija od $f(x)$ (torej $F'(x) = f(x)$).
Zanima nas odvod sestavljene funkcije $F(g(t))$.

**Po verižnem pravilu:**
$$\frac{d}{dt} [F(g(t))] = F'(g(t)) \cdot g'(t)$$

Ker vemo, da je $F' = f$ in $g(t) = \sin(t)$ ter $g'(t) = \cos(t)$, dobimo:
$$\frac{d}{dt} [F(\sin(t))] = f(\sin(t)) \cdot \cos(t)$$

Če zdaj obe strani **integriramo po $t$**:
$$\int \frac{d}{dt} [F(\sin(t))] \, dt = \int f(\sin(t)) \cdot \cos(t) \, dt$$
$$F(\sin(t)) = \int \sqrt{1-\sin^2(t)} \cdot \cos(t) \, dt$$

**Bistvo dokaza:**
Leva stran $F(\sin(t))$ je pravzaprav $F(x)$. In ker je $F(x) = \int f(x) \, dx$, smo dokazali, da velja:
$$\int f(x) \, dx = \int f(\sin(t)) \cdot \cos(t) \, dt$$

---

### Zakaj to sploh delamo, če izgleda bolj zapleteno?

Čeprav dokaz in definicija pravita, da smo integral "povečali" (dodali smo $\cos(t)$), nam **trigonometrična identiteta** znotraj funkcije $f$ omogoči poenostavitev, ki je z $x$-i ni bilo mogoče izvesti:

1.  **Problem:** $\sqrt{1-x^2}$ je težko integrirati, ker je koren "zaklenjen".
2.  **Substitucija:** $\sqrt{1-\sin^2(t)}$ postane $\sqrt{\cos^2(t)}$, kar je le $\cos(t)$.
3.  **Rezultat:** Integral postane $\int \cos(t) \cdot \cos(t) \, dt = \int \cos^2(t) \, dt$.

**Povzetek:**
Po **definiciji** smo le zamenjali $x \to g(t)$ in $dx \to g'(t)dt$.
Po **dokazu** pa smo izkoristili verižno pravilo v obratni smeri, da smo težko funkcijo $f(x)$ spremenili v lažjo funkcijo spremenljivke $t$, pri čemer nam diferencial $g'(t)$ služi kot "ključ", ki odklene verižno pravilo.

***
Dokaz **iz leve proti desni** pomeni, da začnemo s preprostim integralom $\int_a^b f(x) dx$ in pokažemo, kako se naravno preoblikuje v bolj zapleteno obliko na desni, ko uvedemo novo spremenljivko $u$.

Tukaj je izpeljava:

### 1. Izhodišče (Leva stran)
Naj bo $F(x)$ primitivna funkcija funkcije $f(x)$ na intervalu $[a, b]$. Po Newton-Leibnizovi formuli velja:
$$\int_a^b f(x) \, dx = F(b) - F(a)$$

### 2. Uvedba funkcije $x(u)$
Vemo, da je $x$ odvisen od $u$ preko funkcije $x(u)$. Upoštevamo pogoje za meje, ki si jih zapisal:
*   $b = x(\beta)$
*   $a = x(\alpha)$

To vstavimo v naš rezultat:
$$\int_a^b f(x) \, dx = F(x(\beta)) - F(x(\alpha))$$

### 3. Ključni korak: Uporaba osnovnega izreka analize "v nazaj"
Izraz $F(x(\beta)) - F(x(\alpha))$ lahko zapišemo kot določeni integral odvoda sestavljene funkcije $F(x(u))$ na intervalu od $\alpha$ do $\beta$:
$$F(x(\beta)) - F(x(\alpha)) = \int_{\alpha}^{\beta} \frac{d}{du} [F(x(u))] \, du$$

*(To je v bistvu Newton-Leibnizova formula, le da jo tokrat beremo v smeri: "razlika vrednosti funkcije v krajnih točkah je enaka integralu njenega odvoda".)*

### 4. Uporaba verižnega pravila
Zdaj moramo izračunati odvod znotraj integrala: $\frac{d}{du} [F(x(u))]$.
Po **verižnem pravilu** je to:
$$\frac{d}{du} [F(x(u))] = F'(x(u)) \cdot x'(u)$$

Ker pa smo na začetku definirali, da je $F'(x) = f(x)$, sledi:
$$\frac{d}{du} [F(x(u))] = f(x(u)) \cdot x'(u)$$

### 5. Končni sklep
Ta izraz vstavimo nazaj v integral iz 3. koraka:
$$\int_{\alpha}^{\beta} \frac{d}{du} [F(x(u))] \, du = \int_{\alpha}^{\beta} f(x(u)) \cdot x'(u) \, du$$

Če povežemo vse korake od začetka do konca, dobimo:
$$\int_a^b f(x) \, dx = F(b) - F(a) = F(x(\beta)) - F(x(\alpha)) = \int_{\alpha}^{\beta} f(x(u)) x'(u) \, du$$

---

### Povzetek logike (zakaj to deluje?)
1.  **Leva stran** nam pove: "Izračunaj skupno spremembo funkcije $F$ med točkama $a$ in $b$."
2.  **Desna stran** pa pravi: "Izračunaj isto spremembo, ampak potuj po osi $u$ od $\alpha$ do $\beta$."
3.  **Faktor $x'(u)$** v dokazu nastopa kot "pretvornik hitrosti". Če se $x$ premika hitreje ali počasneje glede na $u$, mora $x'(u)$ to hitrost korigirati, da bo skupna sprememba (ploščina) na koncu ista.

To je najčistejši način dokaza, ker neposredno poveže **verižno pravilo** (za odvajanje) z **Newton-Leibnizovo formulo** (za integriranje).


https://aistudio.google.com/prompts/16KLBxeDhlvmqrsW6vW1jMG_SfFVi7_nO