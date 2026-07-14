# Fourierova analiza

## Fourierova vrsta

Za razliko od Taylorjeve vrste, kjer funkcijo razvijemo po potencah:
$$f(x) = a_0 + a_1 x + a_2 x^2 + \dots$$
pri periodičnih funkcijah vzuamemo za osnovo periodične funkcije:
$$a_0 + a_1 \cos x + b_1 \sin x + a_2 \cos(2x) + b_2 \sin(2x) + \dots + a_k \cos(kx) + b_k \sin(kx)$$

Naj bo funkcija $f(x)$ sestavljena samo iz sinusov (primer lihe funkcije):
$$P(x) = b_1 \sin x + b_2 \sin(2x) + \dots + b_n \sin(nx)$$

Vektor koeficientov $(b_1, \dots, b_n)$ predstavlja **spekter funkcije** $f$, ki enolično določa $P(x)$.

### Ortogonalnost trigonometričnih funkcij

Z uporabo zveze:
$$\cos(kx - lx) - \cos(kx + lx) = 2 \sin(kx) \sin(lx)$$

lahko izračunamo integral produkta dveh sinusov:
$$\int_{-\pi}^{\pi} \sin(kx) \sin(lx) \, dx = \frac{1}{2} \int_{-\pi}^{\pi} \cos((k-l)x) \, dx - \frac{1}{2} \int_{-\pi}^{\pi} \cos((k+l)x) \, dx$$

$$= \frac{1}{2} \left[ \frac{\sin((k-l)x)}{k-l} \right]_{-\pi}^{\pi} - \frac{1}{2} \left[ \frac{\sin((k+l)x)}{k+l} \right]_{-\pi}^{\pi} = \begin{cases} 0 & k \neq l \\ \pi & k = l \end{cases}$$

Iz tega sledi določitev koeficientov $b_k$:
$$b_k = \frac{1}{\pi} \int_{-\pi}^{\pi} f(x) \sin(kx) \, dx$$

### Konvergenca Fourierove vrste

Naj bo $f(x)$ zvezna, $2\pi$-periodična in liha funkcija. Izračunamo koeficiente $b_1, b_2, \dots$
Ali vrsta $\tilde{f}(x) = \sum b_i \sin(ix)$ konvergira in ali je njena vsota enaka $f(x)$?

Da vrsta konvergira, se morajo koeficienti $b_n$ dovolj hitro zmanjševati. Z uporabo integracije po delih ($u = f(x) \implies du = f'(x)\,dx$, $dv = \sin(kx)\,dx \implies v = -\frac{1}{k}\cos(kx)$):

$$\pi \cdot b_k = \int_{-\pi}^{\pi} f(x) \sin(kx) \, dx = \left[ -\frac{1}{k} f(x) \cos(kx) \right]_{-\pi}^{\pi} + \frac{1}{k} \int_{-\pi}^{\pi} f'(x) \cos(kx) \, dx$$

Ker je $f$ $2\pi$-periodična in zvezna, je prvi člen enak $0$. Ostane:
$$b_k = \frac{1}{k \pi} \int_{-\pi}^{\pi} f'(x) \cos(kx) \, dx$$

Iz tega sledi:
$$\lim_{k \to \infty} b_k = 0$$

Če je $f$ dvakrat zvezno odvedljiva ($2\times$ zv. odv.), lahko postopek integracije po delih ponovimo, iz česar dobimo, da koeficienti padajo vsaj tako hitro kot $\frac{1}{k^2}$.

**Izrek:**
Če je $f$ dvakrat zvezno odvedljiva, $2\pi$-periodična in liha, potem Fourierova vrsta:
$$b_1 \sin(x) + b_2 \sin(2x) + \dots$$
**enakomerno konvergira** proti $f(x)$.

### Primer sode funkcije

Če je $f$ soda, velja podobno:
$$\int_{-\pi}^{\pi} \cos(kx) \cos(lx) \, dx = \begin{cases} 0 & k \neq l \\ \pi & k = l \neq 0 \\ 2\pi & k = l = 0 \end{cases}$$

**Izrek:**
Če je $f$ dvakrat zvezno odvedljiva, $2\pi$-periodična in soda, so koeficienti enaki:
$$a_k = \frac{1}{\pi} \int_{-\pi}^{\pi} f(x) \cos(kx) \, dx$$
Fourierova vrsta:
$$\frac{a_0}{2} + a_1 \cos x + a_2 \cos(2x) + \dots$$
enakomerno konvergira k $f(x)$.

Vsako funkcijo lahko razdelimo na sodo in liho komponento:
$$f(x) = \underbrace{\frac{f(x) + f(-x)}{2}}_{\text{soda}} + \underbrace{\frac{f(x) - f(-x)}{2}}_{\text{liha}}$$
kjer se soda razvije po kosinusih, liha pa po sinusih.

---

## Splošni zapis Fourierove vrste

Če je $f$ dvakrat zvezno odvedljiva in $2\pi$-periodična:
$$a_k = \frac{1}{\pi} \int_{-\pi}^{\pi} f(x) \cos(kx) \, dx \quad (k=0, 1, \dots)$$
$$b_k = \frac{1}{\pi} \int_{-\pi}^{\pi} f(x) \sin(kx) \, dx \quad (k=1, 2, \dots)$$
Fourierova vrsta za $f(x)$ je:
$$\frac{a_0}{2} + \sum_{k=1}^{\infty} (a_k \cos(kx) + b_k \sin(kx))$$
in enakomerno konvergira proti $f(x)$.

Če funkcija ni $2\pi$-periodična, jo lahko periodično razširimo iz intervala $[-\pi, \pi]$ na celo realno os $\mathbb{R}$.

### Konvergenca v točkah nezveznosti

Naj bo $f: \mathbb{R} \to \mathbb{R}$ odsekovoma zvezno odvedljiva (kar pomeni, da je odsekovoma zvezna in v točkah nezveznosti obstajata leva in desna limita odvoda).
Fourierova vrsta $\tilde{f}(x)$ je konvergentna in velja:
* $\tilde{f}(x) = f(x)$ v točkah $x$, kjer je $f$ zvezna.
* $\tilde{f}(x) = \frac{1}{2} \left( f(x_-) + f(x_+) \right)$ v točkah nezveznosti, kjer sta $f(x_-)$ in $f(x_+)$ leva in desna limita:
  $$f(x_-) = \lim_{t \uparrow 0} f(x+t), \quad f(x_+) = \lim_{t \downarrow 0} f(x+t)$$

---

## Kompleksni zapis Fourierove vrste

Z uporabo Eulerjevih formul:
$$\cos(kx) = \frac{e^{ikx} + e^{-ikx}}{2}, \quad \sin(kx) = \frac{e^{ikx} - e^{-ikx}}{2i}$$
lahko realni zapis pretvorimo v kompleksno obliko:
$$\tilde{f}(x) = \sum_{k=-\infty}^{\infty} c_k e^{ikx}$$

Zveze med koeficienti so:
$$c_k = \frac{a_k - i b_k}{2}, \quad c_{-k} = \frac{a_k + i b_k}{2}, \quad c_0 = \frac{a_0}{2}$$

**Trditev:**
Fourierjeva vrsta integrabilne funkcije $f$ je:
$$\tilde{f}(x) = \sum_{k=-\infty}^{\infty} c_k e^{ikx}$$
kjer so kompleksni koeficienti določeni z:
$$c_k = \frac{1}{2\pi} \int_{-\pi}^{\pi} f(x) e^{-ikx} \, dx$$

---

## Fourierova transformacija (FT)

Ko želimo diskretne frekvence razširiti na celotno realno os $\mathbb{R}$ (ko gre perioda $2\pi \to \infty$), preidemo od vsote k integralu:
$$\tilde{f}(x) = \int_{-\infty}^{\infty} c_u e^{iux} \, du$$

Definiramo preslikavo $F: \mathbb{R} \to \mathbb{R}$. Naj bo $c_{\omega} = \hat{f}(\omega)$.

**Fourierova transformiranka** $\hat{f}(\omega)$ funkcije $f(x)$ je definirana kot:
$$\hat{f}(\omega) = \frac{1}{2\pi} \int_{-\infty}^{\infty} f(x) e^{-i\omega x} \, dx, \quad \omega \in \mathbb{R}$$

**Pogoj za obstoj:** Funkcija $f(x)$ mora biti absolutno integrabilna na $\mathbb{R}$:
$$\int_{-\infty}^{\infty} |f(x)| \, dx < \infty$$

---

## Lastnosti Fourierove transformacije

1. **Linearnost:** FT je linearna operacija.
2. **Riemann-Lebesgueova lema:** Če je $f$ absolutno integrabilna, potem:
   $$\lim_{\omega \to \infty} \hat{f}(\omega) = 0$$
3. **Inverzna Fourierova transformacija (IFT):** Če je $f$ absolutno integrabilna, jo lahko rekonstruiramo z:
   $$f(x) = \int_{-\infty}^{\infty} \hat{f}(\omega) e^{i\omega x} \, d\omega$$
   Preslikava za inverzno FT je:
   $$g(\omega) \mapsto \int_{-\infty}^{\infty} g(\omega) e^{i\omega x} \, d\omega = \check{g}(x)$$
4. **Transformacija odvoda:**
   $$\widehat{f'} = i\omega \hat{f}(\omega) \quad (\text{ob predpostavki zveznosti})$$
   $$\hat{f}'(\omega) = -i \widehat{g}(\omega), \quad \text{kjer je } g(x) = x f(x)$$
5. **Gaussova funkcija:** Fourierova transformacija Gaussove funkcije je ponovno Gaussova funkcija:
   $$f(x) = e^{-\frac{x^2}{2}} \implies \hat{f}(\omega) = \frac{1}{\sqrt{2\pi}} e^{-\frac{\omega^2}{2}}$$

---

## Konvolucija

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


***


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

