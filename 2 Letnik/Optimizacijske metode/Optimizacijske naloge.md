

**Definicijia optimizacijske naloge**

**Optimizacijske naloga** je urejena troijca $(D,f, \text{opt})$, kjer je 
- $D$ ; množica dopustnih rešitev oz. množica vrednosti ki zadoščajo podanim omejitvam
- $f: D \rightarrow \mathbb{R}$ ; kriterijska funkcija *(lahko tudi ciljna ali namenska funkcija)*, funkcija ki možne rešitve preslika v mero kakovosti *(pri prejšnjem primeru je dobiček)*
- $\text{opt} \in \{ \min, \max\}$ ;  tip ekstrema funkcije $f$ ki ga iščemo


**Ponavadi iščemo optimalno rešitev** opt. naloge $(D,f,\text{opt})$, če za vsak $y \in D$ velja

$$\text{opt} = \min \Rightarrow f(x^{*}) \leq f(y)$$
$$\text{opt} = \max \Rightarrow f(x^{*}) \geq f(y)$$

Poznamo tudi

- **Optimalno vrednost  - $v^{*} = f(x^{*})$** 
- **Množico vseh optimalnih rešitev. $\text{Opt} \subset D, \text{Opt} = \{x \in D \,;\;f(x) = v^{*} \}$**, ki vsebuje vse elemente pri katerih funkcija $f$ doseže optimalno vrednost $f(x^{*})$.
- **Približek oz. aproksimacijo** - cilj je najti rešitev blizu optimalni, kadar je natančen izračun nemogoč ali nesmiseln
- **Dopustno rešitev** - cilj je zgolj najti katerikoi element $x$, ki pripada $D$ - ustreza pogojem - ne glede na $f(x)$.

**Opt. problem** je izraz ki ga uporabljamo za opis skupka optimizacijskih nalog istega tipa ki se razlikujejo le v parametrih. Definira strukturo in vrsto parametrov npr. iskanje poti v poljubnem grafu.
**Opt. naloga** je konkretna instanca problema s spceifičnimi vrednostmi parametrov.

$D$ je ponavadi podana kot podmnožica $\Omega$, ta pa vsebuje vse možne elemente - ponavadi vektorje - nad katerimi preverjamo pogoje naloge. Tem rečemo **rešitve** medtem ko elementom $D$ pravimo **dopustne rešitve**.

$$D = \{ x \in \Omega \;;\; x \text{ ustreza določenim pogojem problema} \}$$

Poznamo **minimizacijske** in **maksimizacijske** naloge.

Velja

$$ \min_{x \in D} f(x) = -\max_{x \in D}(-f(x)), $$

$$ \max_{x \in D} f(x) = -\min_{x \in D}(-f(x)). $$

***


Optimizacijske naloge delimo na **dopustne** in **nedopustne**.

Če je $D = \emptyset$ potem je **nedopustna**

Če množica $D$ ni prazna ($D \neq \emptyset$), je naloga **dopustna**.

Dopustne naloge se delijo še po svoji **omejenosti**.

Naloga se šteje za **omejeno** v dveh primerih
- kadar **iščemo maksimum** in je funkcija $f$ na množici $D$ **navzgor omejena**
- kadar **iščemo minimum** in je funkcija $f$ na množici $D$ **navzdol omejena**

Če funkcija $f$ v smeri iskanega ekstrema nima meje — torej pri iskanju minimuma funkcija ni navzdol omejena oziroma pri iskanju maksimuma ni navzgor omejena — je naloga **neomejena**.

Dejstvo, da je naloga omejena, še ne zagotavlja obstoja optimalne rešitve. Možno je, da se vrednosti funkcije $f$ približujejo določeni meji, vendar v množici $D$ ne obstaja točka, v kateri bi bila ta meja dejansko dosežena. V takšnih primerih je naloga **omejena, a nima optimalnih rešitev.** 

Če pa v množici $D$ obstaja vsaj en element, za katerega funkcija $f$ zavzame svojo minimalno oziroma maksimalno vrednost (odvisno od cilja $\text{opt}$), pravimo, da **ima naloga optimalne rešitve**.

Celoten klasifikacijski model tako optimizacijske naloge razvršča v: 
- naloge brez dopustnih rešitev, 
- dopustne a neomejene naloge, 
- omejene naloge brez doseženega optimuma ter 
- naloge, ki imajo vsaj eno optimalno rešitev.

Poznamo zadostne pogoje za obstoj maksimuma in minimuma.

**Zvezna optimizacija**
Naj bo $D \subset  \mathbb{R}^{n}$ zaprta in omejena in $D \neq \emptyset$. Naj bo $f : D \rightarrow \mathbb{R}$ zvezna funkcija. Potem $f$ na $D$ zavzame največjo in najmanjšo vrednost.

**Diskretna optimizacija**
Naj bo $D$ končna množica in $D \neq \emptyset$. Potem $f$ zazvzame najmanjšo in največjo vrednost.

***

**Linearni program v standardni obliki**

**Linearni program** je vrsta optimizacijskega problema, kjer so ciljna funkcija in vse omejitve **linearne**. 

V tej obliki iščemo maksimum funkcije pri omejitvah tipa "manjše ali enako" in ob upoštevanju nenegativnosti spremenljivk.

Definiran je s trojico $(D, f, \max)$:

$$\max f(x)$$
$$f(x) = c^{T} x = \sum_{j=1}^{n} c_{j} x_{j}$$
$$\Rightarrow\text{max} \;\sum_{j=1}^{n} c_{j} x_{j}$$

kjer je $x$ vektor opt. spremenljivk, $c$ pa verktor koeficientov iz ciljne funkcije.

Množica $D$ je določena s sistemom linearnih neenačb in pogoji za spremenljivke:

$$D = \{ x \in \mathbb{R}^n \mid Ax \le b, \ x \ge 0 \}$$

Pri tem elementi zapisa pomenijo:
*   **$x = (x_1, x_2, \dots, x_n)^T$**: Vektor $n$ odločitvenih spremenljivk.
*   **$A \in \mathbb{R}^{m \times n}$**: Matrika koeficientov omejitev velikosti $m \times n$. Vsaka vrstica predstavlja eno omejitev (npr. porabo določenega vira).
*   **$b = (b_1, b_2, \dots, b_m)^T$**: Vektor desnih strani omejitev, ki predstavlja razpoložljive kapacitete ali omejitve.
*   **$Ax \le b$**: Sistem $m$ linearnih neenačb, kjer mora biti leva stran (dejanska poraba) manjša ali enaka desni strani (omejitvi).
*   **$x \ge 0$**: Pogoj nenegativnosti, ki zahteva, da nobena odločitvena spremenljivka ne sme imeti negativne vrednosti ($x_j \ge 0$ za vsak $j$).

Torej velja

$$
\begin{aligned}
\text{maksimiziraj} \quad & c^T x \\
\text{pri pogojih} \quad & Ax \le b \\
& x \ge 0
\end{aligned}
$$

**Polieder v $\mathbb{R}^{n}$** je presek končnega števila zaprtih polprostorov - polovica prostora ki jo razdeljuje hiperravnina.

Če množico $D$ razbijemo na posamezne linearne neenačbe lahko opazimo da vsaka neenačba predstavlja zaprt polprostor v $\mathbb{R}^{n}$ kot tudi enačbe $x_{i} \geq 0$. Torej imamo presek zaprtih polprostorov kar je definicija konveksnega poliedra.

> **Velja da je $D$ konveksni polieder.**

Naj bo $v^{*}$ optimalna vrednost lin. programa. Množico optimalnih rešitev deifniramo kot 

$$\text{Opt} = \{ x \in D \,;\; c^{T}x = v^{*}\}$$

To lahko z razširitvijo sistema neenačb zapišemo kot

$$\text{Opt} = \{ x \in \mathbb{R}^{n} \;;\; Ax\leq b, x\geq 0, c^{T}x\geq v^{*} \}$$

$c^{T}x\geq v^{*}$ je pogoj ker če je $x \in D$ potem že velja $c^{T}x \leq v^{*}$ torej bo ekvivalentno temu da zapišemo $c^{T}x \leq v^{*}$ in $c^{T}x \geq v^{*}$.

Dodatni pogoj lahko obrnemo in dobimo $-c^{T}x \leq -v^{*}$ kar je zaprt polprostor in ker prejšnji pogoji že tvorijo zaprt polprostor imamo spet **konveksni polieder**.

