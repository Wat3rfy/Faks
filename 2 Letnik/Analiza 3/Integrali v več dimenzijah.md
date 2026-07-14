# Integriranje funkcij več spremenljivk


**Dvojni integral**

Naj bo funkcija $f: \Omega \to \mathbb{R}$ definirana na pravokotniku $\Omega = [a,b] \times [c,d]$. 

Naj bo $D$ omejeno območje v $\Omega$. Predpostavimo, da je $D$ odprta množica z neprazno notranjostjo, njen rob $\partial D$ pa je (odsekoma) gladka krivulja. Celotno območje integracije označimo z zaprtjem $\bar{D} = D \cup \partial D$.

**Geometrijski pomen:**
Če je $f(x,y) \ge 0$ za vsak $(x,y) \in D$, potem dvojni integral $\iint_D f(x,y) \, dx \, dy$ predstavlja **prostornino (volumen) telesa**, ki ga omejujejo ravnina $z= 0$, graf funkcije $z = f(x,y)$ in rob območja $D$.

### Delitev območja
Delitev območja $D$ je družina ravninskih likov (običajno konveksnih mnogokotnikov) $\Delta = \{ D_1, D_2, \dots, D_N \}$, **za katero** velja:

1.  **Pokritje:** Unija vseh likov vsebuje območje $D$, torej $\bigcup_{k=1}^N D_k \supset D$.
2.  **Presek:** Notranjosti likov $D_k$ in $D_j$ so si za $k \ne j$ paroma tuje in naj velja $D \cap D_{k} \neq \emptyset$.
3.  **Konveksnost:** Zaradi enostavnosti predpostavimo, da so $D_k$ **konveksne množice**.

**Premer delitve** $\text{diam}(\Delta)$ je definiran kot največji premer med vsemi liki v delitvi:

$$\text{diam}(\Delta) = \max_{1 \le k \le N} \{ \text{diam}(D_k) \},$$

kjer je premer posameznega lika $D_k$ največja razdalja med katerimakoli točkama v tem liku.

### Integralska vsota
Za poljubno delitev $\Delta$ definiramo **Riemannovo integralsko vsoto**:

$$ I(f, \Delta) = \sum_{k} f(x_k, y_k) \cdot A(D_k) $$
pri čemer je:
*   $(x_k, y_k) \in D_k$ poljubna testna točka v posameznem liku,
*   $A(D_k)$ ploščina lika $D_k$,
*   seštevamo le po tistih likih, ki imajo z območjem $D$ neprezen presek.

---

### Definicija dvojnega integrala

$I \in \mathbb{R}$ je dvojni integral funkcije $f(x,y)$ po $D$ natanko tedaj ko velja

$$
\forall \epsilon > 0, \exists \delta > 0,  \forall \Delta: $$ 
$$ \text{diam}(\Delta) < \delta \implies \left| I - \sum_{k} f(x_k, y_k) A(D_k) \right| < \epsilon
$$

pri poljubni izbiri $(x_k, y_k) \in D_{k}$


V tem primeru pravimo, da je funkcija $f$ integrabilna na območju $D$, in pišemo:

$$ I = \iint_D f(x,y) \, dx \, dy = \lim_{\text{diam}(\Delta) \to 0} \sum_{k} f(x_k, y_k) \cdot A(D_k) $$

<br>

**Spodnja in zgornja vsota**


Naj bo $\Delta$ delitev $D$. Naj bo funkcija $f(x,y)$ na $D$ zvezna. $D_{k}$ naj bodo kompaktne, potem je $f$ zvezna tudi na vsakem $D_k$ iz delitve $\Delta$. 

Torej obstajata točki $(x_k, y_k)_m, (x_k, y_k)_M$ na $D_k$, za kateri velja:

$$f((x_k, y_k)_m) = \min_{(x,y) \in D_k} \{f(x,y)\}$$
$$f((x_k, y_k)_M) = \max_{(x,y) \in D_k} \{f(x,y)\}$$

oz. sta minimum in maksimum $f$ na $D_{k}$.

**Spodnja vsota** $f$ pri delitvi $\Delta$ je število:

$$s(f, \Delta) = \sum_{k} f((x_k, y_k)_m) A(D_k)$$

**Zgornja vsota**:

$$S(f, \Delta) = \sum_{k} f((x_k, y_k)_M) A(D_k)$$ 


Velja

$$S(f, \Delta) \ge s(f, \Delta)$$

Naj bo $\{\Delta_n\}_{n \in \mathbb{N}}$ neko zaporedje delitev, za katero velja: 
$\Delta_{n+1}$ je finejša delitev $\Delta_n$, $\forall n \in \mathbb{N}$.

Potem velja:

$$s(f, \Delta_{n+1}) \ge s(f, \Delta_n)$$
$$S(f, \Delta_{n+1}) \le S(f, \Delta_n)$$

Torej zaporedje $\{s(f, \Delta_n)\}_n$ je naraščajoče, navzgor omejeno, torej je konvergentno. 
Zaporedje $\{S(f, \Delta_n)\}_n$ pa je padajoče in navzdol omejeno.

Obstajata limiti:

$$\lim_{n \to \infty} s(f, \Delta_n) = \sigma$$
$$\lim_{n \to \infty} S(f, \Delta_n) = \Sigma$$

>Če je $f$ zvezna na $D$, velja $\sigma = \Sigma$.
>>[!|dokaz]- Dokaz:
>>Velja da je $f$ enakomerno zvezna na vsakem $D_{k}$.
>>$$|((x_{1},y_{1})-(x_{2},y_{2}))|<\delta \Rightarrow|f(x_{1},y_{1})-f(x_{2},y_{2})| < \varepsilon$$
>>Imamo zaporedje delitev $\Delta_{n}$.
>>Ker imamo enakomerno zveznost na vsakem $D_{k}$ za vsak $\varepsilon$ obstaja $\delta$ da je $|f(x_{1},y_{1})-f(x_{2},y_{2})| < \frac{\varepsilon}{A(D)}$
>>za vsak tak delta lahko najdemo $N$ tako da za vse finejše delitve velja $\text{diam}(\Delta_{n}) < \delta$.
>>Sedaj lahko ocenimo razliko med zgornjo in spodnjo vsoto.
>>Vemo da za vse delitve finejše od $N$ je $\text{diam}(\Delta_{n}) < \delta$ torej bo po enakomerni zveznosti
>>$$M_{k}-m_{k} < \frac{\varepsilon}{A(D)}$$
>>Vemo da velja
>>$$S(f,\Delta_{n})-s(f,\Delta_{n}) < \sum_{k}^{} \frac{\varepsilon}{A(D)}A(D_{k})= $$ $$= \frac{\varepsilon}{A(D)}\sum_{k}^{} A(D_{k}) = \frac{\varepsilon}{A(D)}A(D) = \varepsilon$$
>>$$\Rightarrow$$
>>$$S(f,\Delta_{n})-s(f,\Delta_{n}) < \varepsilon$$
>>
>>Torej za vsak $\varepsilon$ obstaja $n$ tako da za vse finejše delitve velja da je razlika vsote maksimumov in vsote minimumov manjša od $\varepsilon$.
>>Velja da ko gre $n$ v neskočnost gre razlika v $0$ torej sta limiti $S$ in $s$ enaki.
>>$$\lim_{n \to \infty}S(f,\Delta_{n}) = \Sigma = \lim_{n \to \infty}s(f,\Delta_{n})=\sigma$$
>>$$\Sigma = \sigma$$

**Definicija:**
Naj bo $f$ zvezna.
Če za vsako zaporedje delitev $\Delta_{n}$ kjer gre premer delitve proti 0, 
$$\lim_{n \to \infty} \text{diam}(\Delta_n) = 0$$
velja $\sigma = \Sigma$  , potem je funkcija $f(x,y)$ na $D$ **integrabilna** in 

$$\iint_D f(x,y) \, dD = \sigma = \Sigma$$

> **Trditev:**
> Zgornja definicija je ekvivalentna naši prejšnji definiciji.
> 
> **Dokaz:**
> 
> 
> 
> Naj bo $I$ integral $f$ po prejšnji definiciji. To pomeni:
> 
> $$\forall \varepsilon > 0, \exists \delta > 0 \text{ da za } \forall \text{ delitev } \Delta_n, \text{ za katero je } \text{diam}(\Delta_n) < \delta, \text{ velja:}$$
> $$\left| \sum_{k} f(x_k, y_k) A(D_k) - I \right| < \varepsilon$$
> 
> za poljuben izbor $(x_k, y_k) \in D_k$.
> 
> Torej velja tudi da za vsak epsilon obstaja delta in $N$ da velja
> 
> $$|s(f, \Delta_n) - I| < \varepsilon$$
> 
> Torej je
> 
> $$\lim_{n \to \infty} s(f, \Delta_n) = I$$
> 
> In velja da za vsak epsilon obstaja delta in $N$ da velja
> 
> $$|S(f, \Delta_{n}) - I| < \varepsilon$$
> 
> Torej je 
> 
> $$\lim_{n \to \infty} S(f, \Delta_n) = I$$
> 
> 
> Torej $\Sigma = \sigma$.
> 
> V drugo smer lahko z izrekom o sendviču, kjer vemo da je
> 
> $$s(f,\Delta) \leq \sum_{k}f(x_{k},y_{k})A(D_{k})  \leq S(f,\Delta)$$
> 
> in ko vzamemo limito vidimo da Riemannova vsota konvergira proti $I$.


> **Izrek:**
> 
> Naj bo $f: \Omega \to \mathbb{R}$ zvezna funkcija na $\Omega \subset \mathbb{R}^2$ in naj bo $D \subset \Omega$ kompaktno območje. Potem velja:
> 
> $$\iint_D f(x,y) \, dxdy \quad \text{obstaja.}$$
> 
> >[!|dokaz]- Dokaz:
> >Ker so $D_{k}$ kompaktna območja vemo da na njih dosežemo minimum in maksium. Lahko definiramo spodnjo in zgornjo Darbojevo vsoto.
> >
> >$$s(f,\Delta) = \sum_{k}^{}m_{k}A(D_{k})$$
> >$$S(f,\Delta) = \sum_{k}^{}M_{k}A(D_{k})$$
> >
> >Velja
> >
> $$S-s = \sum_{k}^{}(M_{k}-m_{k})A(D_{k})$$
> >
> >Ker smo na kompaktnem območju velja da je $f$ tam enakomerno zvezna.
> >Torej
> >$$\forall  \varepsilon \exists \delta : \forall x_{1},x_{2} : |x_{1}-x_{2}| < \delta \Rightarrow |f(x_{1})-f(x_{2})|  < \varepsilon$$
> >
> >
> >Velja da za vsak $\frac{\varepsilon}{A(D)}$ obstaja primerna delta $\delta$ zaradi enekomerne zveznosti. Če vzamemo razdelitev za katero velja da je diameter največjega $D_{k}$ manjši od $\delta$ torej
> >$\text{diam}(\Delta) < \delta$
> >potem velja da so vse točke znotraj manjše od $\delta$, vključho s točkami kjer dobimo $m_{k}$ in $M_{k}$ kar implicira da je 
> >
> >$$|M_{k}-m_{k}|< \frac{\varepsilon}{A(D)}$$
> >
> >To vstavimo nazaj v razliko $S-s$ kjer velja da je
> >
> >$$S-s < \sum_{k}^{}\frac{\varepsilon}{A(D)}A(D_{k}) = \varepsilon$$
> >Torej za vsak $\varepsilon$ obstaja razdelitev $\Delta$ da je razlika med $s$ in $S$ manjša od $\varepsilon$.
> >Ker limita zgornje in spodnje Darboujove vsote obstaja in je enaka velja da je $f$ integrabilna.



### **Osnovne lastnosti dvojnega integrala**

**1. linearnost:**
Naj bosta $f, g: D \rightarrow \mathbb{R}$ integrabilni in $a, b \in \mathbb{R}$ poljubni konstanti. Potem velja:
$$\iint_D (af(x,y) + bg(x,y)) \, dxdy = a \iint_D f(x,y) \, dxdy + b \iint_D g(x,y) \, dxdy$$

**2. aditivnost:**
Naj bo $D = D_1 \cup D_2$ in $D_1 \cap D_2 = \emptyset$. Potem velja:
$$\iint_D f(x,y) \, dxdy = \iint_{D_1} f(x,y) \, dxdy + \iint_{D_2} f(x,y) \, dxdy$$

Če je $D_1 \cap D_2 = D_3 \neq \emptyset$, potem:
$$\iint_D f(x,y) \, dxdy = \iint_{D_1} f(x,y) \, dxdy + \iint_{D_2} f(x,y) \, dxdy - \iint_{D_3} f(x,y) \, dxdy$$

<br>

**Izreki o povprečni vrednosti**

**Trditev 1:**

Naj bo $D \subset \mathbb{R}^2$ kompaktna in povezana. 
Naj bosta $f, g: D \to \mathbb{R}$ zvezni funkciji
Naj bo $f > 0$ na $D$. 
Potem obstaja taka točka $(\xi, \eta) \in D$, da za $k = g(\xi, \eta)$ velja:

$$\iint_D g(x,y) f(x,y) \, dxdy = k \iint_D f(x,y) \, dxdy$$

*Povprečje funkcije lahko izračunamo tako da integral delimo z dolžino intervala. Ker bo povprečje med $\max$ in $\min$ funkcije, obstaja $c$ da je $g(c)$ povprečje $g$. Pri navadme, povprečju  se vsaka vrednost pojavi enkrat. Če predstavimo funkcijo uteži, potem le ta deluje kot večkratnik vrednosti. Če smo prej imeli npr. eno enko imamo lahko sedaj 3 enke. To pomeni da moramo pomnožiti funkcije da dobimo novo vsoto, deliti pa moramo tudi z novo količino podatkov oz. integralom funkcije uteži - $f$.*

>[!|dokaz]- Dokaz:
>Ker je $D$ kompaktna in povezana in $g$ zvezna velja da $g$ doeseže svoj
>$\min$ in $\max$ in velja $m \leq g \leq M$.
>Ker je $f  >0$ velja da pomnožimo neenakost in dobimo
>
>$$f \cdot m \leq f \cdot g \leq f \cdot M$$
>
>$$\iint_{D }m\cdot f \cdot dA \leq \iint_{D} g \cdot  f \cdot dA \leq \iint_{D} M \cdot  f \cdot dA$$
>
>Lahko delimo z integralom $f$ ker je $f$ pozitivna
>
>$$m \leq \frac{\iint_D g(x,y) f(x,y) \, dA}{\iint_D f(x,y) \, dA} \leq M$$
> 
> Naj bo $A = \frac{\iint_D g f}{\iint_D f}$. Vidimo, da je $A$ število med $m$ in $M$.
> Ker je $D$ povezana in $g$ zvezna, $g$ na $D$ zavzame vse vrednosti med $m$ in $M$.
> Torej obstaja točka $(\xi, \eta) \in D$, da velja:
> 
> $$g(\xi, \eta) = A$$
> 
> Dobimo
> 
> $$g(\xi, \eta) = \frac{\iint_D g f}{\iint_D f} \implies \iint_D g f = g(\xi, \eta) \iint_D f$$


### Računanje dvojnih integralov

Naj bo $D \subset \mathbb{R}^{2}$ pravokotnik $[a,b] \times [c,d]$. Računamo $\iint_{D}f(x,y)dxdy$.
Najprej razdelimo pravokotnik na podintervale po $x$ in po $y$:
$$a = x_{0} < x_{1} < \dots < x_{n} = b$$
$$c = y_{0} < y_{1} < \dots < y_{m} = d$$

S tem dobimo mrežo podpravokotnikov $D_{kl} = [x_{k-1}, x_k] \times [y_{l-1}, y_l]$. 
Širina dela je $(\Delta x)_{k} = x_{k}-x_{k-1}$, višina pa $(\Delta y)_{l} = y_{l}-y_{l-1}$.

Naj bo $\delta_{kl} = \sqrt{(\Delta x)_{k}^{2} + (\Delta y)_{l}^{2}}$ diagonala podpravokotnika.
Označimo natančni spodnji in zgornji meji funkcije na vsakem delčku:
$m_{kl} = \inf \{f(x,y); (x,y) \in D_{kl} \}$
$M_{kl} = \sup \{f(x,y); (x,y) \in D_{kl} \}$

S pomočjo teh vrednosti lahko zapišemo spodnjo in zgornjo Darbouxjevo vsoto za dvojni integral:
$$s(f, P) = \sum_{k,l} m_{kl} \Delta x_k \Delta y_l \quad \text{in} \quad S(f, P) = \sum_{k,l} M_{kl} \Delta x_k \Delta y_l$$


> 
> **Fubinijev izrek za pravokotna območja**
> 
> Naj bo $f(x,y)$ na $D$ integrabilna in naj za vsak $x \in [a,b]$ obstaja integral $\int_{c}^{d}f(x,y)dy = F(x)$. Potem velja:
> $$\iint_D f(x,y) \, dxdy = \int_a^b F(x) \, dx = \int_a^b \left[ \int_c^d f(x,y) \, dy \right] dx$$
> 
> >[!|dokaz]- Dokaz:
> > Za poljuben fiksen $x^* \in [x_{k-1}, x_k]$ in za vsak $y \in [y_{l-1}, y_l]$ velja neenakost:
> > $$m_{kl} \leq f(x^*, y) \leq M_{kl}$$
> > 
> > Če to neenakost integriramo po spremenljivki $y$ na intervalu $[y_{l-1}, y_l]$, dobimo:
> > $$m_{kl} \Delta y_l \leq \int_{y_{l-1}}^{y_l} f(x^*, y) \, dy \leq M_{kl} \Delta y_l$$
> > 
> > Če te neenakosti seštejemo po vseh indeksih $l$ (vzdolž celotne stranice pravokotnika pri fiksni točki $x^*$), dobimo oceno za vrednost funkcije $F$ v tej točki:
> > $$\sum_{l=1}^m m_{kl} \Delta y_l \leq F(x^*) \leq \sum_{l=1}^m M_{kl} \Delta y_l$$
> > 
> > Ker zgornja neenakost velja za **vsak** $x^* \in [x_{k-1}, x_k]$, to pomeni, da sta leva in desna stran (ki sta konstantni na tem podintervalu) spodnja in zgornja meja za funkcijo $F(x)$ na celotnem odseku $[x_{k-1}, x_k]$. 
> > 
> > Zdaj celotno neenakost integriramo še po spremenljivki $x$ na intervalu $[x_{k-1}, x_k]$ in nato seštejemo po vseh indeksih $k$:
> > $$\sum_{k=1}^n \left( \sum_{l=1}^m m_{kl} \Delta y_l \right) \Delta x_k \leq \int_a^b F(x) \, dx \leq \sum_{k=1}^n \left( \sum_{l=1}^m M_{kl} \Delta y_l \right) \Delta x_k$$
> > 
> > Opazimo, da sta leva in desna stran ravno spodnja in zgornja Darbouxjeva vsota $s(f, P)$ in $S(f, P)$ za dvojni integral. Ker je funkcija $f$ integrabilna, gresta obe vsoti proti isti vrednosti $\iint_D f(x,y) \, dxdy$, ko postaja delitev $P$ poljubno drobna. Po izreku o sendviču mora biti temu številu enak tudi integral $\int_a^b F(x) \, dx$.



**Dvojni integrali na splošnih območjih**

Naj bo sedaj $D$ neko konveksno območje v $\Omega$ in $f: \Omega \to \mathbb{R}$ integrabilna funkcija. Želimo izračunati:
$$\iint_D f(x,y) \, dxdy$$

**Opis območja:**
Območje $D$ omejimo z minimalno in maksimalno $x$ koordinato: $x \in [a, b]$. 
Pri vsakem fiksnem $x \in [a, b]$ naj se vertikala (črta $x = x_0$) seka z robom $\partial D$ v dveh točkah. Ti točki določata spodnjo mejo $\varphi(x)$ in zgornjo mejo $\psi(x)$, pri čemer velja $\varphi(x) \leq \psi(x)$.

Potem velja:
$$\iint_D f(x,y) \, dxdy = \int_a^b \left[ \int_{\varphi(x)}^{\psi(x)} f(x,y) \, dy \right] dx$$

>[!|dokaz]- Dokaz:
> 
> Bistvo tega dokaza
> 1.  **"Ugasnemo" funkcijo** tam, kjer nas ne zanima (postavimo jo na 0).
> 2.  Uporabimo pravila za pravokotnike.
> 3.  Ugotovimo, da so **meje notranjega integrala** dejansko funkcije
> roba območja ($\varphi(x)$ in $\psi(x)$).
> 
> 
> **Vpeljava nove funkcije:**
> Naj bo $\tilde{D} = [a, b] \times [c, d]$ pravokotnik, ki v celoti vsebuje naše območje $D$. 
> Vpeljemo novo funkcijo $\chi: \tilde{D} \to \mathbb{R}$ (razširjena funkcija), definirano kot:
> $$\chi(x,y) = \begin{cases} f(x,y), & (x,y) \in D \\ 0, & (x,y) \in \tilde{D} \setminus D \end{cases}$$
> 
> **Izenačitev integralov:**
> Očitno velja, da je integral funkcije $\chi$ po celem pravokotniku $\tilde{D}$ enak integralu funkcije $f$ samo po območju $D$, saj je povsod drugje funkcija $\chi$ enaka nič:
> $$\iint_{\tilde{D}} \chi(x,y) \, dxdy = \iint_D f(x,y) \, dxdy$$
> 
> **Uporaba Fubinijevega izreka za pravokotnik:**
> Ker je $\tilde{D}$ pravokotnik, lahko uporabimo že dokazan Fubinijev izrek:
> $$\iint_{\tilde{D}} \chi(x,y) \, dxdy = \int_a^b \left[ \int_c^d \chi(x,y) \, dy \right] dx$$
> 
> **Razcep notranjega integrala:**
> Notranji integral po $y$ (od $c$ do $d$) razdelimo na tri dele glede na meje območja $D$ (to so točke $c$, $\varphi(x)$, $\psi(x)$ in $d$):
> $$\int_c^d \chi(x,y) \, dy = \underbrace{\int_c^{\varphi(x)} \chi(x,y) \, dy}_{=0} + \underbrace{\int_{\varphi(x)}^{\psi(x)} \chi(x,y) \, dy}_{=f(x,y)} + \underbrace{\int_{\psi(x)}^d \chi(x,y) \, dy}_{=0}$$
> 
> 
> Ko te delne rezultate vstavimo nazaj v zunanji integral, dobimo končno formulo:
> $$\iint_D f(x,y) \, dxdy = \int_a^b \left[ \int_{\varphi(x)}^{\psi(x)} f(x,y) \, dy \right] dx$$


---
