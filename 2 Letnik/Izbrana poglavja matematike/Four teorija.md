
Naj bo skalarni produkt funkcij definiran kot

$$\langle f(x),g(x) \rangle $$
$$\int_{-\pi}^{\pi} f(t)g(t)dt$$

Izkaže se da so $\{ \sin\,\! mt , \cos\,\! nt\}, n \in \mathbb{N}$ vedno ortogonalni in $\{ \sin\,\! mt, \sin\,\! nt\}$, $\{ \cos\,\! mt, \cos\,\! nt\}$ ortogonalni če $n \neq m$.

$$\int_{-\pi}^{\pi}\sin\,\! mt \cdot \cos\,\! nt \;dt = 0$$
$$\int_{-\pi}^{\pi}\sin\,\! mt \cdot \sin\,\! nt \;dt = 0$$
$$\int_{-\pi}^{\pi}\cos\,\! mt \cdot \cos\,\! nt \;dt = 0$$

Ker funkcije niso vedno $2\pi$ periodične, recimo da je $T$ periodična. Torej da bosta sinus in kosinus ortogonalna na intervalu $[- \frac{T}{2}, \frac{T}{2}]$ lahko v originalnem integralu od $[-\pi,\pi]$ izvedemo substitucijo  zato uvedemo "bazno krožno frekvenco funkcije $f$" kjer je $\omega = \frac{2\pi}{T}$. Sedaj bomo integrirali po $[-\frac{T}{2}, \frac{T}{2}]$ ampak bo ohranjena ortogonalnost. *Torej če imamo funkcijo ki gre od $t \in [- \frac{T}{2}, \frac{T}{2}]$ nam bo $t \cdot \frac{2 \pi}{T}$ dala pripadajočo točko v $[\pi,-\pi]$ intervalu.*

$$\int_{-\frac{T}{2}}^{\frac{T}{2}}\cos\,\! (m \cdot t \omega) \sin\,\! (n \cdot t \omega) dt$$

Torej lahko neko **$T$ peridoično** funkcijo izrazimo kot linearno kombinacijo *ortogonalmih vektorjev oz. funkcij, ki služijo kot baza*

$$f(t) = \frac{a_{0}}{2} + \sum_{1}^{\infty}a_{n}\cos\,\! (\omega n t) + b_{n}\sin\,\! (\omega n t)$$

kjer je $$\omega = \frac{2\pi}{T}$$

Tukaj si $\cos$ in $\sin$ predstalvjamo kot bazo funkcijskega prostora, $a_n,b_{n}$ pa kot pripadajoče koeficiente.

Enačba za $a_{n},b_{n}$ je motivirana preko projekcije. Pri vektorjih lahko dobimo določeno komponento oz. koeficient s pomočjo skalarnega množenja z baznim vektorjem, torej izvajamo projekcijo. Če bazni vektor ni normaliziran oz. enotski moramo projekcijo še deliti z njegovo dolžino. 

Absolutna dolžina vektorja za pravokotno projeckijo bi bila

$$\Vert v \Vert  \cos\,\! \varphi$$

to lahko prevedemo na skalarni produkt če zgoraj in spodaj pomnožimo z $\left\Vert \vec{e} \right\Vert$

$$\frac{\Vert v \Vert \Vert \vec{e}\Vert \cos\,\! \varphi}{\Vert \vec{e}\Vert}$$

$$\frac{\vec{v} \cdot \vec{e}}{\left\Vert \vec{e} \right\Vert}$$

Da dobimo dejanski vektor pomnožimo z normaliziranim baznim vektorjem $\frac{\vec{e}}{\Vert e \Vert }$.

$$\frac{\vec{v} \cdot \vec{e}}{\left\Vert \vec{e} \right\Vert} \cdot \frac{\vec{e}}{\left\Vert \vec{e} \right\Vert }$$

$$\frac{\vec{v} \cdot \vec{e}}{\left\Vert \vec{e} \right\Vert^{2}} \cdot \vec{e}$$

Podobno naredimo tu **spektralno projekcijo**

Naše bazne funkcije ($\cos(n\omega t)$ in $\sin(n\omega t)$) **niso enotske dolžine**. Izračunajmo *preko identitet $\cos^{2}x = \frac{1-\cos 2x}{2}$ in $\sin^{2}x = \frac{1+\cos2x}{2}$*

$$\|\cos(n\omega t)\|^2 = \int_{-T/2}^{T/2} \cos^2(n\omega t) \, dt = \frac{T}{2}$$

$$\|\sin(n\omega t)\|^2 = \int_{-T/2}^{T/2} \sin^2(n\omega t) \, dt = \frac{T}{2}$$

*še za $a_{0}$ kjer je  funkcija konstantna $1$*

$$\|1\|^2 = \int_{-T/2}^{T/2} 1^2 \, dt = T$$

Sedaj lahko izvedemo projekcijo

$$a_n = \frac{\langle f(t), \cos(n\omega t) \rangle}{\|\cos(n\omega t)\|^2} = \frac{\int_{-T/2}^{T/2} f(t) \cos(n\omega t) \, dt}{\frac{T}{2}}$$

$$a_n = \frac{2}{T} \int_{-T/2}^{T/2} f(t) \cos(n\omega t) \, dt$$

Za $b_{n}$ enako

$$b_n = \frac{\langle f(t), \sin(n\omega t) \rangle}{\|\sin(n\omega t)\|^2} = \frac{\int_{-T/2}^{T/2} f(t) \sin(n\omega t) \, dt}{\frac{T}{2}}$$

$$b_n = \frac{2}{T} \int_{-T/2}^{T/2} f(t) \sin(n\omega t) \, dt$$


Za $a_{0}$ je striktno gledano projekcija definirana kot

$$a_{0} = \frac{\langle f(t), 1 \rangle}{\|1\|^2} = \frac{\int_{-T/2}^{T/2} f(t) \cos(n\omega t) \, dt}{T}$$
$$a_{0} = \frac{1}{T}\int_{-T/2}^{T/2} f(t) \cos(n\omega t) \, dt$$

Tukaj je problem ker za vse $a_n$ iammo lepo formulo

$$a_n = \frac{2}{T} \int_{-T/2}^{T/2} f(t) \cos(n\omega t) \, dt$$

razen za $a_{0}$

$$a_{0} = \frac{1}{T}\int_{-T/2}^{T/2} f(t) \cos(n\omega t) \, dt$$

Vrsta pa je definirana kot

$$f(t) = a_{0} + \sum_{1}^{\infty}a_{n}\cos\,\! (\omega n t) + b_{n}\sin\,\! (\omega n t)$$

<br>

Kar lahko storimo je da **v enačbi člena $a_{0}$ pomnožimo desno stran z $2$**. S tem moramo seveda tudi **v definiciji vrste $a_{0}$ deliti z $2$** da se enakost ohrani. S tem samo poskušamo poenotiti enačbe za koeficiente s tem da žrtvujemo izgled vrste.

Torej naj bo $a_{0}$ sedaj

$$a_{0} = \frac{{\color{green}2}}{T}\int_{-T/2}^{T/2} f(t) \cos(n\omega t) \, dt$$

*kar je v skladu z enačbo za $a_{n}$*

$$\color{light}a_n = \frac{2}{T} \int_{-T/2}^{T/2} f(t) \cos(n\omega t) \, dt$$

V vrsti pa postane

$$f(t) = \frac{a_{0}}{{\color{green}2}} + \sum_{1}^{\infty}a_{n}\cos\,\! (\omega n t) + b_{n}\sin\,\! (\omega n t)$$

Torej je to standardna **realna oblika**.

<br>

To lahko zapišemo v strenjni obliki v kompleksni obliki. Velja

$$e^{i\theta} = \cos\theta + i\sin\theta$$

Izpostavimo lahko $\cos\,\!$ in $\sin$

$$\cos\theta = \frac{e^{i\theta} + e^{-i\theta}}{2}$$
$$\sin\theta = \frac{e^{i\theta} - e^{-i\theta}}{2i} = -i \frac{e^{i\theta} - e^{-i\theta}}{2} \quad \left(\text{ker je } \frac{1}{i} = -i\right)$$

Vstavimo v

$$f(t) = \frac{a_0}{2} + \sum_{n=1}^{\infty} \Big( {\color{green}a_n \cos(n\omega t) + b_n \sin(n\omega t)} \Big)$$

$$ $$
$${\color{green}\text{kjer naj bo $\theta = n\omega t$}}$$
$$ $$

$${\color{green}a_n \cos(\theta) + b_n \sin(\theta)} = a_n \left( \frac{e^{i\theta} + e^{-i\theta}}{2} \right) + b_n \left( -i \frac{e^{i\theta} - e^{-i\theta}}{2} \right)$$

Združimo člene po  $e^{i\theta}$ in $e^{-i\theta}$

$$= \left( \frac{a_n - i b_n}{2} \right) e^{i\theta} + \left( \frac{a_n + i b_n}{2} \right) e^{-i\theta}$$

Za sedaj dobimo

$$f(t) = \frac{a_0}{2} + \sum_{n=1}^{\infty} \left( {\color{green}\left( \frac{a_n - i b_n}{2} \right) e^{i\theta} + \left( \frac{a_n + i b_n}{2} \right) e^{-i\theta}}  \right)$$


Sedaj uvedemo nove, kompleksne koeficiente $c$, s katerimi nadomestimo realne koeficiente:

Za pozitivne indekse $n > 0$

$$c_n = \frac{a_n - i b_n}{2}$$

Za negativne indekse $n < 0$, ker je $c_{-n}$ konjugirano kompleksna vrednost od $c_n$, velja:

$$c_{-n} = \frac{a_n + i b_n}{2}$$

Za $n=0$ pa še vedno velja

$$c_0 = \frac{a_0}{2}$$

Če te definicije vstavimo nazaj v vrsto, vidimo, da členi z $e^{i \theta}$ pokrivajo pozitivne indekse od $1$ do $\infty$. Členi z $e^{-i \theta}$ pokrivajo negativne indekse od $-1$ do $-\infty$. Člen $c_0$ pokriva $n = 0$. **Velja $\theta = i \omega n$, zato bo $c_{-n}e^{-i \omega n}$ ko gre $n \in [1,\infty)$ pokrito ko gre $c_{n}e^{i \omega n}$ po $n \in (-\infty, -1]$**

$$f(t) = \frac{a_0}{2} + \sum_{n=1}^{\infty} \left( {\color{green}c_{n} e^{i\theta} + c_{-n}  e^{-i\theta}}  \right)$$

Celotno vrsto združimo v eno samo vsoto

$$f(t) = \sum_{n=-\infty}^{\infty} c_n e^{i\theta}$$

Zamenjamo nazaj $\theta= n \omega t$

$${\color{green}f(t) = \sum_{n=-\infty}^{\infty} c_n e^{i n \omega t}}$$

<br><br><br>

Da dobimo še $c_{n}, n > 0$ pa vzamemo defincijo


$$c_n = \frac{a_n - i b_n}{2}$$

in vanjo vstavimoformuli za $a_n$ in $b_n$

$$c_n = \frac{1}{2} \left[ \left( \frac{2}{T} \int_{-T/2}^{T/2} f(t) \cos(n\omega t) \, dt \right) - i \left( \frac{2}{T} \int_{-T/2}^{T/2} f(t) \sin(n\omega t) \, dt \right) \right]$$

Vidimo da se $\frac{1}{2}$ in $\frac{2}{T}$ pokrajšata. Izpostavimo  $\frac{1}{T}$ in združimo integrala

$$c_n = \frac{1}{T} \int_{-T/2}^{T/2} f(t) \Big( \cos(n\omega t) - i \sin(n\omega t) \Big) \, dt$$

Velja $\cos\theta - i\sin\theta = e^{-i\theta}$, torej je 

$$c_n = \frac{1}{T} \int_{-T/2}^{T/2} f(t) e^{-i n \omega t} \, dt$$

Izkaže se da velja tudi za $n<0$ in $n=0$, če ju vstavimo not

$$c_{-n} = \frac{1}{T} \int_{-T/2}^{T/2} f(t) e^{i n \omega t} \, dt$$
$$c_{-n} = \frac{1}{T} \int_{-T/2}^{T/2} f(t) \Big( \cos(n\omega t) + i \sin(n\omega t) \Big) \, dt$$
$$c_{-n} = \frac{1}{2} \left[ \left( \frac{2}{T} \int_{-T/2}^{T/2} f(t) \cos(n\omega t) \, dt \right) + i \left( \frac{2}{T} \int_{-T/2}^{T/2} f(t) \sin(n\omega t) \, dt \right) \right]$$
$$c_{-n} = \frac{a_n + i b_n}{2}$$

Če vstavimo $n=0$ pa je očtino da dobimo 

$$c_n = \frac{1}{T} \int_{-T/2}^{T/2} f(t)  \, dt$$
$$2 c_{n}=\frac{2}{T} \int_{-T/2}^{T/2} f(t)  \, dt = a_{0}$$
$$c_{n}=\frac{a_{0}}{2}$$


<br>
<br>
<br>

**Zvezna Fourierjeva transfomracija**

S to obliko lahko preidemo na neperdiočne funkcije kjer jih obravnavamo kot da gre preioda v $\infty$ torej $T \rightarrow \infty$. 

Razdalja med diskretnimi frekvencami bo šla $\Delta\omega = \omega = \frac{2\pi}{T}$ proti $0$ ko gre $T \rightarrow \infty$ torej bo $d \omega$. Ker ne delamo več z diskretnimi frekvencami $n \omega$ se zgoščijo v realna števila in uporabljamo samo $\omega \in \mathbb{R}$.

Najprej vstavimo enačbo za $c_{n}$ v enačbo vrste

$$f(t) = \sum_{n=-\infty}^{\infty} c_n e^{i n \omega t}$$
$$c_n = \frac{1}{T} \int_{-T/2}^{T/2} f(t) e^{-i n \omega t} \, dt$$

da dobimo

$$f(t) = \sum_{n=-\infty}^{\infty} \left(\frac{1}{T} \int_{-T/2}^{T/2} f(t) e^{-i n \omega t} \, dt\right) e^{i n \omega t}$$

premislili smo da velja $\Delta\omega=\frac{2\pi}{T} \Rightarrow$ $\frac{1}{T} = \frac{\Delta\omega}{2\pi}$ kar vstavimo in izpostavimo *$\frac{1}{2 \pi}$ gre na začetek, $\Delta \omega$ na konec.*

$$f(t) =\frac{1}{2\pi}\sum_{n=-\infty}^{\infty} \left( \int_{-T/2}^{T/2} f(t) e^{-i n \omega t} \, dt\right) e^{i n \omega t}\Delta\omega$$

ko gre $T \rightarrow \infty$ se raztegnejo meje integrala, $\Delta \omega$ gre v $d \omega$, $n \omega \rightarrow n$, $\sum_{}^{}\Delta \omega \rightarrow \int_{}^{}d \omega$

$$f(t) =\frac{1}{2\pi}\int_{-\infty}^{\infty} \left( \int_{-\infty}^{\infty} f(t) e^{-i \omega t} \, dt\right) e^{i \omega t}d\omega$$

Opazimo da je notranji integral odvisen le še od $\omega$. Temu pravimo **zvezna fourierjeva transfomracija $\hat{f}(w)$**.

$$\hat{f}(w) =  \int_{-\infty}^{\infty} f(t) e^{-i \omega t} \, dt$$

zunanjem delu pa pravimo **inverzna Fourierjeva transfomracija**

$$f(t) =\frac{1}{2\pi}\int_{-\infty}^{\infty} \hat{f}(t) e^{i \omega t}d\omega$$



> **Primer**
> 
> 
> $$S_a(x) = \begin{cases} 1 & x \in [-a, a] \\ 0 & \text{sicer} \end{cases}$$
> 
> $$\hat{S}_a(\omega) = \frac{1}{2\pi} \int_{-a}^{a} 1 \cdot e^{-i\omega x} \, dx = \frac{1}{2\pi} \int_{-a}^{a} \left( \cos(\omega x) - i \sin(\omega x) \right) \, dx$$
> $$= \frac{1}{2\pi} \left[ \frac{\sin(\omega x)}{\omega} \right]_{-a}^{a} + \frac{i}{2\pi} \left[ \frac{\cos(\omega x)}{\omega} \right]_{-a}^{a}$$
> $$= \frac{1}{2\pi} \left( \frac{\sin(a\omega) - \sin(-a\omega)}{\omega} \right) + 0 = \frac{2 \sin(a\omega)}{2\pi \omega} = \frac{\sin(a\omega)}{\pi \omega}$$
> 
> 

> **Primer**
> $$f(x) = \begin{cases} e^{-ax} & x \ge 0 \\ 0 & x < 0 \end{cases} \quad (a > 0)$$
> 

> $$\hat{f}(\omega) = \frac{1}{2\pi} \int_{0}^{\infty} e^{-ax} e^{-i\omega x} \, dx = \frac{1}{2\pi} \int_{0}^{\infty} e^{-(a+i\omega)x} \, dx$$
> $$= \frac{1}{2\pi} \left[ \frac{-1}{a+i\omega} e^{-(a+i\omega)x} \right]_{0}^{\infty} = \frac{1}{2\pi} \left( 0 - \frac{-1}{a+i\omega} \right) = \frac{1}{2\pi(a+i\omega)}$$
> 
> Racionaliziramo
> $$\hat{f}(\omega) = \frac{a}{2\pi(a^2 + \omega^2)} - \frac{i\omega}{2\pi(a^2 + \omega^2)}$$



**Lastnosti Fourierove transformacije**

1. **Linearnost**
   $$\mathcal{F}(f(x) + g(x)) = \hat{f}(x) + \hat{g}(x)$$
2. **Riemann-Lebesgueova lema:** Če je $f$ absolutno integrabilna, potem:
   $$\lim_{\omega \to \infty} \hat{f}(\omega) = 0$$
3. **Inverzna Fourierova transformacija (IFT):** Če je $f$ absolutno integrabilna, jo lahko rekonstruiramo z:
   $$f(x) = \int_{-\infty}^{\infty} \hat{f}(\omega) e^{i\omega x} \, d\omega$$
4. **Transformacija odvoda:**
   $$\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\mathcal{F}(f') = i\omega \hat{f}(\omega) \quad\text{ kjer velja da je $f$ zvezna}$$
   $$\hat{f}'(\omega) = -i \widehat{g}(\omega), \quad \text{kjer je } g(x) = x f(x)$$
5. **Gaussova funkcija:** Fourierova transformacija Gaussove funkcije je ponovno Gaussova funkcija:
   $$f(x) = e^{-\frac{x^2}{2}} \implies \hat{f}(\omega) = \frac{1}{\sqrt{2\pi}} e^{-\frac{\omega^2}{2}}$$



**Konvolucija**

Za dve absolutno integrabilni funkciji $f, g: \mathbb{R} \to \mathbb{R}$ definiramo konvolucijo kot:

$$(f * g)(x) = \int_{-\infty}^{\infty} f(t) g(x-t) \, dt$$

Lastnosti konvolucije:
* Komutativnost
* Asociativnost
* Distributivnost

**Izrek o konvoluciji:**

$$\widehat{f * g} = 2\pi \hat{f} \cdot \hat{g}$$
$$\widehat{f \cdot g} = \hat{f} * \hat{g} \cdot 2\pi$$

---

## Diskretna in hitra Fourierova transformacija (FFT)

Zaradi lastnosti konvolucije velja shema:
$$f, g \xrightarrow{\text{FT}} \hat{f}, \hat{g} \xrightarrow{\text{množenje}} \hat{f} \cdot \hat{g} \xrightarrow{\text{IFT}} f * g$$

Ta pristop je računsko učinkovit, če imamo na voljo hiter algoritem za računanje FT (hitra FT - FFT).

Pri diskretizaciji lahko prehod zapišemo z matriko $\mathcal{F}_N$. Njen inverz je konjugirana matrika:
$$\mathcal{F}_N^{-1} = \overline{\mathcal{F}_N}$$

* Klasično računanje diskretne FT (po točkah) zahteva časovno zahtevnost:
  $$\mathcal{O}(n^2)$$
* Hitra diskretna FT (FFT) zmanjša zahtevnost na:
  $$\mathcal{O}(n \log n)$$

