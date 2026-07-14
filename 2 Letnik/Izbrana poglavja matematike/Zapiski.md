

## Imamo $\text{Im } f$ in $\text{Ker } f$

$f : K \rightarrow L$

$\text{Im } f := \{f(x) ; x \in K\} \subseteq L$ in je podkolobar $\leq L$
$\text{Ker } f := \{x \in K ; f(x) = 0\} \subseteq K$ in je ideal $\unlhd K$

Tu velja **idealna lastnost**:
$a \in \text{Ker } f$ in $x \in K \Rightarrow$
$ax \in \text{Ker } f$
$xa \in \text{Ker } f$
Recimo, da jedro $f$ "absorbira" množenje z elementi iz $K$.

### Naj bo $K$ kolobar, $I \subseteq K$

$I$ je **ideal** $\Leftrightarrow$ ima idealno lastnost:
$v K, I \unlhd K$ pomeni:
$k \cdot i \in I$ in $i \cdot k \in I$ za vse $k \in K, i \in I$.

* $\text{Ker } f \unlhd K$ ; $f : K \rightarrow L$ na.
* $\{0\} \unlhd K, K \unlhd K \longrightarrow$ **nepravi ideali**.
* $\{f : \mathbb{R} \rightarrow \mathbb{R} ; f(a) = 0\} \unlhd \text{Fun}(\mathbb{R}, \mathbb{R})$ (to je jedro $\varphi_a$).

* Najmanjši ideal, ki vsebuje neko podmnožico el. oz. kakšen ideal generira podana podmnožica.
* **Presek idealov je ideal** (razlaga).
* Za $a \in K$ je $(a)$ ideal, generiran z $a$-jem $\hookrightarrow (a) = Ka$.
* $a \in K$ je obrnljiv $\Leftrightarrow (a) = K$ (+ dokaz).
* $K$ je obseg $\Leftrightarrow K$ nima pravih idealov.
* Vsi ideali v $\mathbb{Z}$ so glavni.
* $K$ je obseg $\Rightarrow$ vsi ideali v $K[x]$ so glavni (+ Dokaz).
* Kolobar, v katerem so vsi ideali glavni, imenujemo **glavni idealni kolobar**.


Sledi prepis zapiskov v formatu LaTeX markdown:

**27.2 in 6.3!!!**

---

### IPM 13.3.

$I \unlhd K$

* $\mathbb{Z}$ je **glavnoidealni** $\rightarrow$ vsi ideali so glavni $\rightarrow$ vsak $x \in I$ je oblike $a \cdot k, k \in \mathbb{Z}$.
* $K$ obseg $\Rightarrow K[x]$ glavnoidealni.
* $\mathbb{Z}[x]$ ni glavnoidealni: primer je ideal $(2, x)$.
* $K[x, y]$ ni glavnoidealni.
  Primer: $2(x+1) = 2x + 2$, $x(\dots) = 2x + 2$
  $\hookrightarrow$ ne moremo dobiti skupnega generatorja.
  V $\mathbb{R}$ pa recimo velja $x(2 + \frac{1}{x}) = 2x + 1$.

#### Kvocientni kolobar
$K \unrhd I$ (dvostranski ideal)

Na $K$ vpeljemo relacijo $\sim_I$:
$a \sim_I b \Leftrightarrow a - b \in I$

$\sim_I$ je ekvivalenčna relacija.
$K / \sim_I \equiv K/I$ je množica ekvivalenčnih razredov.

**Primer:** $\mathbb{Z} \unrhd n\mathbb{Z}$
$a \sim b \Leftrightarrow a - b \in n\mathbb{Z}$
$a$ in $b$ imata isti ostanek pri deljenju z $n$.
$\mathbb{Z}/n\mathbb{Z} = \{ [0], [1], \dots, [n-1] \} = \mathbb{Z}_n$

**Operacije:**
$[a] + [b] = [a + b]$
Ali je to dobra definicija?
Naj bo $a' \sim a \Rightarrow a' - a \in I$ in $b' \sim b \Rightarrow b' - b \in I$.
Preverimo, če velja $[a' + b'] = [a + b]$:
$(a' - a) + (b' - b) = (a' + b') - (a + b) \in I$
$\Rightarrow a' + b' \sim a + b$ (Definicija je dobra).

$[a] \cdot [b] = [a \cdot b]$
...

$(K/I, +_I, \cdot_I)$ je **kvocientni kolobar** in podeduje lastnosti $K$.

$K/_{(0)} \cong K, \quad K/K \cong (0)$

> Primer: $5\mathbb{Z} \unlhd \mathbb{Z}$
> $[2] = \{ \dots, -8, -3, 2, 7, 12, 17, \dots \} = 2 + 5\mathbb{Z}$

---

### Primeri kvocientnih kolobarjev

$\mathbb{Z}/n\mathbb{Z} = \{0, \dots, n-1\} = \mathbb{Z}_n$

**$\mathbb{R}[x]/(x) = ?$**
$p(x) + (x)$, kjer je $p(x) = a_0 + a_1x + \dots + a_nx^n$.
$p \sim q \Leftrightarrow$ njuna razlika je deljiva z $x \Leftrightarrow$ imata enak prosti člen.
$\Rightarrow a_0 + \underbrace{x(a_1 + \dots + a_nx^{n-1})}_{\in (x)}$
Vsak element $p(x) + (x)$ je predstavljen s prostim členom.
$(\mathbb{R}[x]/(x), +, \cdot) \cong (\mathbb{R}, +, \cdot)$

**$\mathbb{R}[x]/(x^2)$**
$p(x) = a_0 + a_1x + (x^2)$
$q(x) = b_0 + b_1x + (x^2)$
$\cong \mathbb{R}^2$ (kot vektorski prostor) s preslikavo $p(x) \mapsto (a_0, a_1)$.
$p + q = (a_0 + b_0) + (a_1 + b_1)x + (x^2) \rightarrow (a_0 + b_0, a_1 + b_1) \in \mathbb{R}^2$
$pq = a_0b_0 + (a_0b_1 + a_1b_0)x + (x^2) \rightarrow (a_0b_0, a_0b_1 + a_1b_0) \in \mathbb{R}^2$

**V kolobarju $\mathbb{R}[x]/(x^2 + 1)$:**
$x^2 + 1 \equiv 0 \Rightarrow x^2 \equiv -1$.
Polinoma $p \equiv ax + b$ in $q \equiv cx + d$.
Množenje:
$(ax + b)(cx + d) = acx^2 + bdx + adx + bd = acx^2 + bd + (bc + ad)x$
Zamenjamo $x^2$ z $-1$:
$-ac + bd + (bc + ad)x$
$\Rightarrow \mathbb{R}[x]/(x^2+1) \cong \mathbb{C}$

---

### Izrek o homomorfizmu

Kaj pa $\mathbb{R}[x]/(x^2-1), \mathbb{R}[x]/(x^2+2)$? Kdaj so to obsegi?

Naj bo $f : K \rightarrow L$ homomorfizem kolobarjev.
* $\text{Im } f \leq L$ je podkolobar.
* $\text{Ker } f \unlhd K$ je ideal.
* $f$ je surjektiven $\Leftrightarrow \text{Im } f = L$.
* $f$ je injektiven $\Leftrightarrow \text{Ker } f = \{0\}$.

Gledamo $K / \text{Ker } f$:
$a + \text{Ker } f \mapsto f(a) \in L$.
Če je $a' \sim a$, potem $a' - a \in \text{Ker } f$, torej $f(a') = f(a + (a' - a)) = f(a) + f(a' - a) = f(a)$.
Ta homomorfizem inducira funkcijo $\bar{f} : K/\text{Ker } f \rightarrow L$:
$\bar{f}(a + \text{Ker } f) = f(a)$.

$\bar{f}$ je injektiven, saj $\bar{f}(a + \text{Ker } f) = 0 \Rightarrow f(a) = 0 \Rightarrow a \in \text{Ker } f$.
$\text{Im } \bar{f} = \text{Im } f$.

**Izrek: Homomorfizem $f : K \rightarrow L$ inducira izomorfizem:**
**$\bar{f} : K/\text{Ker } f \cong \text{Im } f$**
**$a + \text{Ker } f \mapsto f(a)$**

> To imenujemo kanonični razcep oz. kanonična dekompozicija $f$.

---

### Ideali v kvocientnih kolobarjih

**Primeri:**
* $\varphi_0 : \mathbb{R}[x] \rightarrow \mathbb{R}, p(x) \mapsto p(0)$.
  $\text{Ker } \varphi_0 = (x)$, $\text{Im } \varphi_0 = \mathbb{R} \Rightarrow \mathbb{R}[x]/(x) \cong \mathbb{R}$.
* $\varphi_i : \mathbb{R}[x] \rightarrow \mathbb{C}, p(x) \mapsto p(i)$.
  $\text{Ker } \varphi_i = (x^2 + 1)$, $\text{Im } \varphi_i = \mathbb{C} \Rightarrow \mathbb{R}[x]/(x^2+1) \cong \mathbb{C}$.

**Kako ugotoviti, ali je kvocientni kolobar obseg?**
Če v $K/I$ najdemo pravi ideal, potem ni obseg.

**Izrek o korespondenci idealov:**
Kvocientna preslikava $q : K \rightarrow K/I$ določa bijekcijo med:
$\{ \text{ideali } J' \unlhd K/I \} \longleftrightarrow \{ \text{ideali } J \unlhd K, \text{ki vsebujejo } I \}$.

**Primer $\mathbb{Z}_{12} = \mathbb{Z}/(12)$:**
Ideali v $\mathbb{Z}_{12}$ ustrezajo idealom v $\mathbb{Z}$, ki vsebujejo $(12)$, torej $(n)$, kjer $n|12$:
$(1), (2), (3), (4), (6), (12)=(0)$.

Struktura podalov (Hassejev diagram):
$(12) \rightarrow (6) \rightarrow (3) \rightarrow (1)$
$(12) \rightarrow (6) \rightarrow (2) \rightarrow (1)$
$(12) \rightarrow (4) \rightarrow (2) \rightarrow (1)$

**Kdaj je $K/I$ obseg?**
$K/I$ je obseg natanko takrat, ko nima pravih idealov. To pomeni, da med $I$ in $K$ ni drugih idealov.
Ideal $I \unlhd K$ je **maksimalen**, če ne obstaja ideal $J$ tak, da $I \subsetneq J \subsetneq K$.
**Izrek: $K/I$ je obseg $\Leftrightarrow I$ je maksimalen ideal v $K$.**


Tukaj je prepis vaših ročno napisanih zapiskov v formatu LaTeX markdown:

---

### IPM 20.3.

ideali v $K/I \longleftrightarrow$ ideali v $K$, ki vsebujejo $I$

$K/I$ je obseg $\iff I$ je max. ideal v $K$

**Trditev:** v glavnoidealnem kolobarju so maksimalni ideali natanko tisti, ki jih generirajo nerazcepni elementi.

(Če imamo el. $a = b \cdot c$, nočemo da je $b$ ali $c$ obrnljiv, ker drugače vedno velja $a = (a \cdot c^{-1}) \cdot c$
npr. $x^2 + 1 = \frac{1}{5}(5x^2 + 5)$ 
$\hookrightarrow$ obrnljiv)

$\downarrow$ $k \in K$ je nerazcepen $\iff (\nexists a, b \in K : k = ab ; a, b \text{ nista obrnljiva })$

$I \unlhd K$ je max : $I = (a)$
predp. da $a$ je razcepen $\Rightarrow a = b \cdot c$

$I = (a) \subsetneq (b) \subsetneq K$
$a = c \cdot b \Rightarrow b \mid a \Rightarrow (a) \subseteq (b)$
ker $b$ ni obrnljiv $\Rightarrow (b) \neq K$ (ker $b \in K$)

$a$ je nerazcepen, če ne obstaja $J$
$(a) \subsetneq J \subsetneq K$
$\uparrow$
$(b)$ je pravi ideal $\Rightarrow b$ ni obrnljiv
$a = b \cdot c$
$c$ ni obrnljiv, ker bi $(a) = (b)$

### OBSEGI

$\mathbb{Q}, \mathbb{R}, \mathbb{C}, \mathbb{Z}_p$, ...

$\mathbb{Q}[x] \rightarrow$ kolobar brez deliteljev niča

$\text{Frac}(\mathbb{Q}[x]) = \mathbb{Q}(x)$ tudi $\mathbb{R}(x), \mathbb{C}(x), \mathbb{Z}_p(x)$
$\downarrow$ racionalne funkcije

**Primer**
$a + b\sqrt{2}, a, b \in \mathbb{Q} \quad \{3 - \sqrt{2}, \frac{1}{2} + 2\sqrt{2}, \dots \}$ $\rightarrow$ števna
$\mathbb{Q} \subseteq \mathbb{Q}(\sqrt{2}) \subseteq \mathbb{R} \rightarrow$ nešt.

$(a + b\sqrt{2})(a' + b'\sqrt{2}) = aa' + bb' \cdot 2 + (ab' + a'b)\sqrt{2}$

$\mathbb{Q}(\sqrt{2})$ je obseg.
$\frac{a + b\sqrt{2}}{a' + b'\sqrt{2}} = \dots = \frac{aa' - 2bb'}{a'^2 - 2b'^2} + \frac{a'b - ab'}{a'^2 - 2b'^2}\sqrt{2}$

$\mathbb{Q}(\sqrt{3}) \neq \mathbb{Q}(\sqrt{2})$

$\mathbb{Q}(\sqrt[3]{2}) = \{a + b\sqrt[3]{2} \mid a, b \in \mathbb{Q}\}$ ni obseg ($\cdot$ ni zaprta)
$\{a + b\sqrt[3]{2} + c\sqrt[3]{4} \mid a, b, c \in \mathbb{Q}\}$ je obseg.

$a \in \mathbb{R}$
$\mathbb{Q}(a)$ najmanjši podobseg $\mathbb{R}$, ki vsebuje $a$. (presek vseh obsegov je vedno obseg)

---

### Konstruktibilna števila

geometrijska konstrukcija = ravnilo in šestilo

* pravokotnice in vzporednice
*(skici sekajočih se premic in lokov)*

izkaže se, da kota ne moremo razdeliti na ne-$2^n$ delov, ne gre.

znamo narediti 3, 4, 5, 6, —, 8, —, 10, —, 12, —, —, 15, 16, 17
*(skica kvadrata v krogu)*  $\leftarrow$ Gauss

problem konstrukcije pravilnega n-kotnika

**Glavni problemi:**
* trisekcija kota
* podvojitev kocke (dvakrat večja prostornina) - rabil bi $\sqrt[3]{2}a$, ampak to ne obstaja
* kvadratura kroga (konstrukcija kvadrata z enako ploščino kot nek krog)

**Kaj lahko konstruiramo z ravnilom in šestilom:**

$O$ (origin), $E$ (enota)

čez dve točki lahko potegnemo premico, krožnico z radijem $|EO|$
*(skica sekajočih se krožnic)*
$K_0 = \{O, E\}$
$K_1 = K_0 \cup \{\text{presečišča krožnic in premic iz } K_0\}$
$K_2 = K_0 \cup K_1 \cup \{ \dots K_0, K_1 \}$
$K_{i+1} = \{ \dots K_i \}$
$K_0 \subset K_1 \subset K_2 \subset \dots \subseteq K = \bigcup_{i=0}^\infty K_i \Rightarrow$ množica konstruktibilnih točk v ravnini

Vsaka točka je sestavljena iz $(x, y)$
torej naj bo $K_x = \text{vse abscise točk v } K$
$K_y = K_x$
$K = K_x \times K_x$

**Izrek:** $K$ je obseg, še več, $K$ je najmanjši podobseg $\mathbb{R}$, ki vsebuje kvadratne korene vseh svojih pozitivnih el.

**Dokaz:** 
$\fbox{+}$ zaprtost
$+, -$ je konstruktibilna: $\circ \rule{1cm}{0.4pt} \circ \rightarrow$ je zaprto

$\cdot, \div$ je tudi konstr... potrebujemo še eno dimenzijo in enoto
*(skica podobnih trikotnikov)* $ab$ (zaradi podobnosti)
in za deljenje $\frac{a}{b} \cdot b = a$

$\sqrt{a} \dots$
*(skica polkroga)* $a:x = x:1 \Rightarrow x^2 = a \Rightarrow x = \sqrt{a}$

$L_i \subseteq \mathbb{R}$, $L_i \times L_i =$
rac. preseki premic in krožnic
$\downarrow$
potrebujemo $+,-,\cdot$
lin. sistemi
$\downarrow$
potrebujemo $\sqrt{\quad}, \div$
zaradi kvadratnih enačb

ali je to najmanjši obseg $\mathbb{Q} \subsetneq K_x \subsetneq \mathbb{R}$
$\downarrow$ ne more biti $=$, če bi bile vse geometrijske konstr. možne
na vsakem koraku imamo končno mnogo točk, torej je unija vseh teh števna in ni enaka $\mathbb{R}$.
Ker vemo $\mathbb{R}$ št. ni konstruktibilno.


Here is a transcription of the provided mathematical notes into LaTeX markdown.

---

# IPM 27.3

$\mathbb{Q}(\sqrt{2}) = \{a + b\sqrt{2} ; a, b \in \mathbb{Q} \}$ je obseg (field).

## Konstruktibilna števila
Iz dveh podanih dolžin $a, b$ lahko konstruiramo: $a+b, a-b, a \cdot b, \frac{a}{b}, \sqrt{a}$.

Vsak korak je matematično gledano reševanje enačb:
* Presečišče premic: linearni sistem.
* Premica in krožnica: kvadratna enačba.
* Krožnica in krožnica: kvadratna enačba.

K obstoječim številom lahko dodamo korene kvadratnih enačb.
Začnemo s $\mathbb{Q} = K_0 \subset K_1 \subset \dots \subset K_n$.
Vsak $K_{i+1}$ je dobljen iz $K_i$ z dodajanjem korenov kvadratne enačbe s koeficienti iz $K_i$.

$K = \bigcup_i K_i \quad ; \quad \mathbb{Q} \subset K \subseteq \mathbb{R}$
$\hookrightarrow$ števna (countable) množica.

**Katera realna števila so konstruktibilna?**

Če imamo $K \leq F$ ($K$ je podobseg, $F$ je razširitev obsega $K$):
* $F$ je vedno $K$-vektorski prostor.
* V $F$ obstaja nabor elementov (baza), s katerimi lahko izrazimo vsak element.
* Govorimo o dimenziji $[F : K] := \dim_K F$.

**Primeri:**
* $\mathbb{R} \subset \mathbb{C} \Rightarrow [\mathbb{C} : \mathbb{R}] = 2$ ($a+bi$, baza $\{1, i\}$).
* $\mathbb{Q} \subset \mathbb{R} \Rightarrow [\mathbb{R} : \mathbb{Q}] = \infty$ (neskončno).
* $[\mathbb{Q}(\sqrt{2}) : \mathbb{Q}] = 2$.
* $[\mathbb{Q}(\sqrt[3]{2}) : \mathbb{Q}] = 3$ (baza $\{1, \sqrt[3]{2}, \sqrt[3]{4}\}$).

### Izrek (za končne razširitve)
$K \subseteq F \subseteq E \Rightarrow [E : K] = [E : F] \cdot [F : K]$

**Dokaz:**
Naj bo $[F : K] = m$ z bazo $\{x_1, \dots, x_m\} \subseteq F$. Vsak $f \in F$ je oblike $\sum_{i=1}^m k_i x_i = f$.
Naj bo $[E : F] = n$ z bazo $\{y_1, \dots, y_n\} \subseteq E$. Vsak $e \in E$ je oblike $\sum_{j=1}^n f_j y_j = e$.
Potem je $[E : K] = m \cdot n$ z bazo $\{x_i y_j ; i \in [m], j \in [n]\}$.

$e = \sum_j f_j y_j = \sum_j (\sum_i k_{ij} x_i) y_j = \sum_{i,j} k_{ij} x_i y_j$.
To kaže, da $\{x_i y_j\}$ napenjajo prostor. Linearna neodvisnost:
$0 = \sum_{i,j} k_{ij} (x_i y_j) = \sum_j (\sum_i k_{ij} x_i) y_j = 0 \xrightarrow{\text{v } E/F} \sum_i k_{ij} x_i = 0 \xrightarrow{\text{v } F/K} k_{ij} = 0 \quad \forall i,j$.

---

## Algebraični in transcendentni elementi

Naj bo $K \subseteq F$ in $a \in F$.
Definiramo evalvacijski homomorfizem $\varphi_a : K[x] \rightarrow F, \quad p(x) \mapsto p(a)$.

* $\text{Im } \varphi_a = K[a]$ (najmanjši podkolobar v $F$, ki vsebuje $K$ in $a$) $\subseteq K(a)$ (najmanjši podobseg).
* $\text{Ker } \varphi_a = \{ p(x) \in K[x] ; p(a) = 0 \}$.

1. Če je $\text{Ker } \varphi_a = \{0\}$, je $a$ **transcendenten** nad $K$ (npr. $e, \pi$ nad $\mathbb{Q}$).
2. Če je $\text{Ker } \varphi_a \neq \{0\}$ (pravi ideal), je $a$ **algebraičen** nad $K$ (npr. $\sqrt{2}$ nad $\mathbb{Q}$, $i$ nad $\mathbb{R}$).

Razširitev $K \subseteq F$ je algebraična, če so vsi njeni elementi algebraični nad $K$.

### Minimalni polinom
Naj bo $a$ algebraičen nad $K$. Ker je $K[x]$ glavnoidealni kolobar, obstaja tak polinom $g_a(x)$, da je $\text{Ker } \varphi_a = (g_a(x))$.
Če zahtevamo, da je $g_a(x)$ **moničen** (vodilni koeficient je 1), ga imenujemo **minimalni polinom** za $a$ nad $K$.

* Minimalni polinom je **nerazcepen**.
* $(g_a(x))$ je **maksimalen ideal** v $K[x]$.

---

## Struktura algebraične razširitve

Iz izreka o homomorfizmu sledi:
$K[x] / \text{Ker } \varphi_a \cong \text{Im } \varphi_a = K[a]$.
Ker je $\text{Ker } \varphi_a$ maksimalen ideal, je $K[a]$ obseg, torej $K[a] = K(a)$.

Dimenzija razširitve $[K(a) : K]$ je enaka stopnji minimalnega polinoma $n = \deg g_a(x)$.
Baza $K(a)$ nad $K$ je $\{1, a, a^2, \dots, a^{n-1}\}$.

### Izrek
Naj bo $a \in F$ algebraičen nad $K$:
1. Obstaja enoličen moničen nerazcepen polinom $g_a(x)$, ki ima $a$ za ničlo.
2. $K(a) = K[a] \cong K[x]/(g_a(x))$.
3. $[K(a) : K] = \deg g_a(x)$.

### Posledica
Če je $F$ končna razširitev $K$ in $a \in F$, potem $\deg_K a \mid [F : K]$.
(Kjer je $\deg_K a := \deg g_a(x)$).

---

## Uporaba pri konstruktibilnosti

### Izrek
Če je $a \in \mathbb{R}$ konstruktibilno število, potem je $\deg_{\mathbb{Q}} a = 2^n$ za nek $n \in \mathbb{N}$.

**Dokaz (skica):** Presečišča premic in krožnic vodijo do razširitev stopnje 2. Po $k$ korakih dobimo razširitev stopnje $2^k$.

**Primeri:**
1. **Podvojitev kocke:** Ali je $\sqrt[3]{2}$ konstruktibilen?
   Minimalni polinom je $x^3 - 2$, ki je nerazcepen nad $\mathbb{Q}$.
   $\deg_{\mathbb{Q}} \sqrt[3]{2} = 3 \neq 2^n \Rightarrow$ konstrukcija **ni možna**.
2. **Kvadratura kroga:** Ali je $\pi$ konstruktibilen?
   $\pi$ je transcendenten nad $\mathbb{Q}$, zato **ni konstruktibilen**.

Tukaj so zapiski iz vseh štirih slik prepisani v format LaTeX markdown.

---

### 1. stolpec: Konstrukcija pravilnega n-kotnika

**3.4. Konstrukcija pravilnega n-kotnika**

$\zeta = e^{i \frac{2\pi}{n}} = \cos \frac{2\pi}{n} + i \sin \frac{2\pi}{n}$ (lahko določimo iz osi)

Zanima nas, kdaj:
$\deg_{\mathbb{Q}} \cos \frac{2\pi}{n} = 2^k \ ; \ k \in \mathbb{N}$

$\zeta = \cos \frac{2\pi}{n} + i \sin \frac{2\pi}{n} \rightarrow$ je ničla polinoma
$x^n - 1$
ni nerazcepen
$\Rightarrow (x-1)(x^{n-1} + x^{n-2} + \dots + 1)$
$\dots$
$\Phi_n(x)$ so nerazcepni nad $\mathbb{Q}$
$\deg \Phi_n = \varphi(n)$

Gauss: minimalni polinom za $\zeta = e^{i \frac{2\pi}{n}}$ je stopnje $\varphi(n)$.
Eulerjeva funkcija (brez dokaza)

$\Rightarrow$ Pravilni $n$-kotnik je konstruktibilen
$\iff \varphi(n)$ je potenca $2$.

Lastnosti Eulerjeve funkcije:
* $a, b$ tuji $\Rightarrow \varphi(ab) = \varphi(a)\varphi(b)$
* $\varphi(p^k) = p^k - p^{k-1} = p^{k-1}(p-1)$

Primer: $\varphi(12) = \varphi(2^2 \cdot 3) = \varphi(2^2) \cdot \varphi(3) = (2^2 - 2^1) \cdot 2 = 4$

$n = 2^k \cdot n' \ ; \ n'$ je lih
$n'$ mora biti produkt različnih lihih praštevil.
$\varphi(p) = p - 1$
Dopustna praštevila so oblike
$p = 2^k + 1$
$k$ ne sme imeti lihih faktorjev:
$(k = m \cdot l \Rightarrow 2^{m \cdot l} + 1 = (2^m)^l + 1 = (2^m + 1)((2^m)^{l-1} - \dots + 1))$
Torej mora biti $k = 2^m \ ; \ m \in \mathbb{N}_0$
$\Rightarrow p = 2^{2^m} + 1 \rightarrow$ Fermatova praštevila

**Izrek (Gauss-Wantzel):**
Pravilni $n$-kotnik je konstruktibilen natanko tedaj, ko je
$n = 2^k \cdot (\text{produkt različnih Fermatovih praštevil})$

(brez dokaza)

---

### 2. stolpec: Končni obsegi (uvod)

**Končni obsegi**

$K$ je končen obseg $\Rightarrow |K| = p^n$

$\mathbb{Z}_4$ ni obseg: ima delitelje niča.
$\mathbb{Z}_2 \times \mathbb{Z}_2 : (0,0), (0,1), (1,0), (1,1)$ ima delitelje niča.

Struktura obsega s 4 elementi $\{0, 1, a, b\}$:
| $+$ | 0 | 1 | a | b |
|---|---|---|---|---|
| 0 | 0 | 1 | a | b |
| 1 | 1 | 0 | b | a |
| a | a | b | 0 | 1 |
| b | b | a | 1 | 0 |
$\rightarrow$ seštevanje = po elementih (bitno)
Množenje $\rightarrow$ določimo tako, da vsaka vrstica/stolpec vsebuje vse elemente (razen ničle).

$\mathbb{R}(i) = \mathbb{C} \quad (x^2 + 1 = 0)$

**Izrek**
a) Vsaka končna razširitev je algebraična.
b) Če je $K \subseteq F$ in $A \subseteq F$ množica elementov algebraičnih nad $K$, potem je razširitev $K(A)$ algebraična nad $K$.
c) Če je $F$ algebraična razširitev $K$ in $E$ algebraična razširitev $F$, je $E$ algebraična razširitev $K$.

**Dokaz a)**
Naj bo $[F:K] = n$.
Vzemimo $a \in F$. Elementi $\{1, a, a^2, \dots, a^n\}$ tvorijo množico $n+1$ elementov v $n$-dimenzionalnem prostoru nad $K$, zato so linearno odvisni.
$\exists k_0, \dots, k_n \in K$ (ne vsi nič) tako, da $\sum_{i=0}^n k_i a^i = 0$
$\Rightarrow a$ je ničla nekega polinoma v $K[x]$, torej je $a$ algebraičen nad $K$.

**Končni obsegi (nadaljevanje)**
$K$ je končen obseg $\Rightarrow$ karakteristika char $K$ je praštevilo $p$.
$\Rightarrow K$ je vektorski prostor nad $\mathbb{Z}_p$.
$\Rightarrow |K| = p^n$, kjer je $n = \dim_{\mathbb{Z}_p} K$.
Multiplikativna grupa $K^* = K \setminus \{0\}$ ima $p^n - 1$ elementov.
Po Lagrangeu: za vsak $a \in K^* \Rightarrow a^{p^n - 1} = 1 \Rightarrow a^{p^n} = a$.
To velja tudi za $a=0$.
$\Rightarrow$ Vsi elementi $a \in K$ so ničle polinoma $x^{p^n} - x$.

**Trditev**
Če je $K$ končen obseg s karakteristiko $p$ in $|K|=p^n$, potem je $K$ razpadni obseg polinoma $x^{p^n} - x$ nad $\mathbb{Z}_p$.
$K = \mathbb{Z}_p(x^{p^n} - x)$

---

### 3. stolpec: Razpadni obsegi

**Dokaz c)** nadaljevanje: $a \in E$, $a$ je algebraičen nad $F$.
Obstaja minimalni polinom $p(x) = f_0 + f_1 x + \dots + f_n x^n \in F[x]$, tako da $p(a) = 0$.
Ker so vsi $f_i$ algebraični nad $K$, je $K(f_0, \dots, f_n)$ končna razširitev $K$.
$a$ je algebraičen nad $K(f_0, \dots, f_n, \dots)$, kar je končna razširitev $\Rightarrow a$ je algebraičen nad $K$.

---

**Razpadni obseg**
Naj bo $K$ obseg in $p(x) \in K[x]$.
Polinom $p(x)$ razpade na linearne faktorje v razširitvi $L$, ko $L$ vsebuje vse njegove ničle.

Primeri:
* $x^2 - 2$ nad $\mathbb{Q} \rightarrow$ razpadni obseg je $\mathbb{Q}(\sqrt{2})$.
* $x^3 - 2$ nad $\mathbb{Q} \rightarrow$ razpadni obseg je $\mathbb{Q}(\sqrt[3]{2}, \sqrt[3]{2}\omega, \sqrt[3]{2}\omega^2)$, kjer je $\omega = e^{i \frac{2\pi}{3}}$.

Konstrukcija razpadnega obsega za polinom $p(x) \in K[x]$:
Dobimo ga z zaporednimi razširitvami:
$K = K_0 \subseteq K_1 \subseteq K_2 \dots \subseteq K_n = K(p(x))$
V vsakem koraku, če $p(x)$ še ne razpade, vzamemo nerazcepen faktor $q(x)$ in definiramo $K_{i+1} = K_i[x] / (q(x))$.

Razpadni obseg je enoličen do izomorfizma.
Za vsak polinom $p(x)$ obstaja razpadni obseg $K(p(x))$, ki je določen do izomorfizma natančno.

---

### 4. stolpec: Galoisovi obsegi (GF)

V vsakem končnem obsegu $K$:
$|K| = p^n$ elementov.
$K$ je razpadni obseg polinoma $x^{p^n} - x$ nad $\mathbb{Z}_p$.
Imenujemo ga **Galoisov obseg**, oznaka $GF(p^n)$ ali $\mathbb{F}_{p^n}$.

Ničle polinoma $x^{p^n} - x$ tvorijo obseg:
Naj bosta $a, b$ korenini ($a^{p^n}=a, b^{p^n}=b$):
* $(a \cdot b)^{p^n} = a^{p^n} \cdot b^{p^n} = ab$
* $(a + b)^{p} = a^p + b^p$ (v obsegu s karakteristiko $p$)
  $\Rightarrow (a + b)^{p^n} = a^{p^n} + b^{p^n} = a + b$ (t.i. "Freshman's dream")

Primeri:
* $GF(4) \cong \mathbb{Z}_2 [x] / (x^2 + x + 1)$. Če je $\alpha$ koren, potem $\alpha^2 = \alpha + 1$.
* $GF(p^n) = \mathbb{Z}_p[x] / (p(x))$, kjer je $p(x)$ nerazcepen polinom stopnje $n$.
* Primer v $\mathbb{Z}_3$: $x^2 + 2x + 1$ ni nerazcepen, saj je $(x+1)^2$.
* $GF(27) \cong \mathbb{Z}_3[x] / (x^3 + x^2 + 1)$ (če je polinom stopnje 3 nerazcepen nad $\mathbb{Z}_3$).