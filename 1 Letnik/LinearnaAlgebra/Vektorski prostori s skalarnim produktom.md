
## 1. Skalarni produkt

V tem razdelku bomo definirali skalarni produkt na realnih in kompleksnih vektorskih prostorih ter si ogledali nekaj primerov.

### Definicija skalarnega produkta nad $\mathbb{R}$

Naj bo $V$ vektorski prostor nad obsegom realnih števil $\mathbb{R}$. Preslikava, ki vsakemu paru vektorjev $u, v \in V$ priredi realno število $\langle u, v \rangle$, je **skalarni produkt**, če zadošča naslednjim lastnostim:
1. Za vsak neničeln $v \in V$ velja $\langle v, v \rangle > 0$. (Pozitivna definitnost)
2. Za vsaka $u, v \in V$ velja $\langle v, u \rangle = \langle u, v \rangle$. (Simetričnost)
3. Za vsake $u_1, u_2, v \in V$ ter $\alpha_1, \alpha_2 \in \mathbb{R}$ velja $\langle \alpha_1 u_1 + \alpha_2 u_2, v \rangle = \alpha_1 \langle u_1, v \rangle + \alpha_2 \langle u_2, v \rangle$. (Linearnost v prvem faktorju)

**Posledice aksiomov (za $\mathbb{R}$):**
*   **Linearnost v drugem faktorju:** Za vse $u, v_1, v_2 \in V$ ter vse $\beta_1, \beta_2 \in \mathbb{R}$ velja $\langle u, \beta_1 v_1 + \beta_2 v_2 \rangle = \beta_1 \langle u, v_1 \rangle + \beta_2 \langle u, v_2 \rangle$. (Dokaz: Iz simetričnosti in linearnosti v prvem faktorju).
*   Za vsak $v \in V$ velja $\langle v, 0 \rangle = \langle 0, v \rangle = 0$.
*   Za vsak $v \in V$ velja $\langle v, v \rangle \ge 0$. Enačaj velja natanko tedaj, ko je $v = 0$.

### Primeri skalarnih produktov na realnih vektorskih prostorih

**Standardni skalarni produkt na $\mathbb{R}^n$**
Za $(\alpha_1, \dots, \alpha_n), (\beta_1, \dots, \beta_n) \in \mathbb{R}^n$ je definiran kot:
$\langle (\alpha_1, \dots, \alpha_n), (\beta_1, \dots, \beta_n) \rangle = \alpha_1 \beta_1 + \dots + \alpha_n \beta_n$.

**Dodatni primeri skalarnih produktov na $\mathbb{R}^n$**
Za vsako $n$-terico $\delta = (\delta_1, \dots, \delta_n)$ strogo pozitivnih realnih števil je skalarni produkt definiran kot:
$\langle (\alpha_1, \dots, \alpha_n), (\beta_1, \dots, \beta_n) \rangle = \delta_1 \alpha_1 \beta_1 + \dots + \delta_n \alpha_n \beta_n$.

**Standardni skalarni produkt na $C[a, b]$** (prostor zveznih funkcij na intervalu $[a,b]$)
Za dve zvezni funkciji $f, g \in C[a, b]$ je definiran kot:
$\langle f, g \rangle = \int_a^b f(x)g(x)dx$.

**Dodatni primeri skalarnih produktov na $C[a, b]$**
Naj bo $w \in C[a, b]$ taka funkcija, ki zadošča $w(x) > 0$ za vsak $x \in [a, b]$. Skalarni produkt je definiran kot:
$\langle f, g \rangle = \int_a^b w(x)f(x)g(x)dx$.

### Definicija skalarnega produkta nad $\mathbb{C}$

Naj bo $V$ vektorski prostor nad obsegom kompleksnih števil $\mathbb{C}$. Preslikava, ki vsakemu paru vektorjev $u, v \in V$ priredi kompleksno število $\langle u, v \rangle$, je **skalarni produkt**, če zadošča naslednjim lastnostim:
1. Za vsak neničeln $v \in V$ velja $\langle v, v \rangle \in \mathbb{R}$ in $\langle v, v \rangle > 0$.
2. Za vsaka $u, v \in V$ velja $\langle v, u \rangle = \overline{\langle u, v \rangle}$. (Konjugirana simetričnost)
3. Za vsake $u_1, u_2, v \in V$ ter $\alpha_1, \alpha_2 \in \mathbb{C}$ velja $\langle \alpha_1 u_1 + \alpha_2 u_2, v \rangle = \alpha_1 \langle u_1, v \rangle + \alpha_2 \langle u_2, v \rangle$. (Linearnost v prvem faktorju)

**Posledice aksiomov (za $\mathbb{C}$):**
*   **Konjugirana linearnost v drugem faktorju:** Za vse $u, v_1, v_2 \in V$ ter vse $\beta_1, \beta_2 \in \mathbb{C}$ velja $\langle u, \beta_1 v_1 + \beta_2 v_2 \rangle = \overline{\beta_1} \langle u, v_1 \rangle + \overline{\beta_2} \langle u, v_2 \rangle$.
*   Za vsak $v \in V$ velja $\langle v, 0 \rangle = \langle 0, v \rangle = 0$.
*   Za vsak $v \in V$ velja $\langle v, v \rangle \ge 0$. Enačaj velja natanko tedaj, ko je $v = 0$.

### Primeri skalarnih produktov na kompleksnih vektorskih prostorih

**Standardni skalarni produkt na $\mathbb{C}^n$**
Za $(\alpha_1, \dots, \alpha_n), (\beta_1, \dots, \beta_n) \in \mathbb{C}^n$ je definiran kot:
$\langle (\alpha_1, \dots, \alpha_n), (\beta_1, \dots, \beta_n) \rangle = \alpha_1 \overline{\beta_1} + \dots + \alpha_n \overline{\beta_n}$.
(Opomba: za razliko od realnega primera imamo tu $\overline{\beta_i}$ namesto $\beta_i$).

**Dodatni primeri skalarnih produktov na $\mathbb{C}^n$**
Če $\sum_i \alpha_i \overline{\beta_i}$ zamenjamo z $\sum_i \delta_i \alpha_i \overline{\beta_i}$, kjer so $\delta_i > 0$ fiksni, dobimo drug skalarni produkt na $\mathbb{C}^n$.

**Standardni skalarni produkt na $C([a, b], \mathbb{C})$**
Za dve zvezni funkciji $f, g \in C([a, b], \mathbb{C})$ je definiran kot:
$\langle f, g \rangle = \int_a^b f(x)\overline{g(x)}dx$.
(Opomba: za razliko od realnega primera imamo tu $\overline{g(x)}$ namesto $g(x)$).

## 2. Norma porojena iz skalarnega produkta

### Definicija norme

Naj bo $V$ realen ali kompleksen vektorski prostor s skalarnim produktom. Za vsak element $v \in V$ definiramo njegovo **normo** z:
$||v|| = \sqrt{\langle v, v \rangle}$.

### Trditev (Cauchy-Schwartzova neenakost)

Naj bo $V$ vektorski prostor s skalarnim produktom. Za vsaka $u, v \in V$ je:
$|\langle u, v \rangle| \le ||u|| ||v||$.

**Dokaz:** (Skica)
Definirajmo $\alpha = \langle v, v \rangle$ in $\beta = \langle u, v \rangle$. Vektor $w = \alpha u - \beta v$ ima nenegativno normo: $0 \le \langle w, w \rangle$. Z razpisom $\langle w, w \rangle$ in upoštevanjem lastnosti skalarnega produkta ter dejstva, da je $z\bar{z}=|z|^2$, dobimo:
$0 \le ||v||^4 ||u||^2 - |\langle u, v \rangle|^2 ||v||^2$.
Če je $v \ne 0$, lahko krajšamo z $||v||^2$ in dobimo $|\langle u, v \rangle|^2 \le ||v||^2 ||u||^2$. S korenjenjem dobimo Cauchy-Schwartzovo neenakost. Če je $v=0$, neenakost očitno drži.

### Trditev (Osnovne lastnosti norme)

Naj bo $V$ vektorski prostor s skalarnim produktom. Pripadajoča norma zadošča naslednjim lastnostim:
1. Za vsak neničeln $v \in V$ je $||v|| > 0$.
2. Za vsak $v \in V$ in vsak skalar $\alpha$ je $||\alpha v|| = |\alpha| ||v||$.
3. Za vsaka $u, v \in V$ je $||u + v|| \le ||u|| + ||v||$. (Trikotniška neenakost)

**Dokaz:** (Skica)
1. Sledi iz pozitivne definitnosti skalarnega produkta.
2. $||\alpha v||^2 = \langle \alpha v, \alpha v \rangle = \alpha \overline{\alpha} \langle v, v \rangle = |\alpha|^2 ||v||^2$. S korenjenjem dobimo $||\alpha v|| = |\alpha| ||v||$.
3. $||u+v||^2 = \langle u+v, u+v \rangle = \langle u, u \rangle + \langle u, v \rangle + \langle v, u \rangle + \langle v, v \rangle = ||u||^2 + 2\mathrm{Re}(\langle u, v \rangle) + ||v||^2$. Ker je $2\mathrm{Re}(z) \le 2|z|$ in po Cauchy-Schwartzu $|\langle u, v \rangle| \le ||u|| ||v||$, sledi:
$||u+v||^2 \le ||u||^2 + 2||u||||v|| + ||v||^2 = (||u|| + ||v||)^2$. S korenjenjem dobimo trikotniško neenakost.

### Trditev (Polarizacijske identitete)

*   Če je $V$ vektorski prostor nad $\mathbb{R}$, potem za vsaka $u, v \in V$ velja:
    $\langle u, v \rangle = \frac{1}{4} (||u+v||^2 - ||u-v||^2)$.
*   Če je $V$ vektorski prostor nad $\mathbb{C}$, potem za vsaka $u, v \in V$ velja:
    $\langle u, v \rangle = \frac{1}{4} \sum_{k=0}^3 i^k ||u+i^k v||^2$.

**Dokaz:** (Skica)
Identiteti se dokažeta z razpisom norm in uporabo lastnosti skalarnega produkta (linearnost, simetričnost/konjugirana simetričnost).

## 3. Ortogonalne baze

### Definicija ortogonalnosti vektorjev

Naj bo $V$ vektorski prostor s skalarnim produktom. Vektorja $u, v \in V$ sta **pravokotna** (s tujko ortogonalna), če velja $\langle u, v \rangle = 0$.

**Opombe:**
*   Ničelni vektor je pravokoten na vse vektorje.
*   Neničeln vektor ne more biti pravokoten sam nase (ker je $\langle v, v \rangle > 0$ za $v \ne 0$).

**Primer:** Vektorja $(1,2)$ in $(2,-3)$ iz $\mathbb{R}^2$ sta pravokotna glede na skalarni produkt $\langle (\alpha_1,\alpha_2), (\beta_1,\beta_2) \rangle = 3\alpha_1\beta_1 + \alpha_2\beta_2$, nista pa pravokotna glede na standardni skalarni produkt.

### Definicija ortogonalne množice

Naj bo $V$ vektorski prostor s skalarnim produktom. Množica vektorjev iz $V$ je **ortogonalna**, če ne vsebuje ničelnega vektorja in če sta vsaka dva različna vektorja iz te množice pravokotna.

**Primer:** Vektorji $(1, 1, 1, 1, 1, 1, 1, 1)$, $(-1, -1, -1, -1, 1, 1, 1, 1)$, $(-1, -1, 1, 1, -1, -1, 1, 1)$ in $(-1, 1, -1, 1, -1, 1, -1, 1)$ tvorijo ortogonalno množico v $\mathbb{R}^8$ za standardni skalarni produkt.

**Primer:** Funkcije $f_k(x) = \sin\left(\frac{k\pi x}{a}\right)$, kjer $k = 1, 2, 3, \dots$, tvorijo neskončno ortogonalno množico v $C[0, a]$ za standardni skalarni produkt.

### Trditev

Vsaka ortogonalna množica je linearno neodvisna.

**Dokaz:** (Skica)
Recimo, da je $\sum_{j=1}^k \alpha_j v_j = 0$ za ortogonalno množico $\{v_1, \dots, v_k\}$. Potem za vsak $i \in \{1, \dots, k\}$ velja $\langle \sum_{j=1}^k \alpha_j v_j, v_i \rangle = \langle 0, v_i \rangle = 0$. Zaradi linearnosti in ortogonalnosti se vsi členi razen $\alpha_i \langle v_i, v_i \rangle$ izničijo. Torej $\alpha_i \langle v_i, v_i \rangle = 0$. Ker so vektorji neničelni, je $\langle v_i, v_i \rangle > 0$, zato mora biti $\alpha_i = 0$. To velja za vse $i$, kar pomeni linearno neodvisnost.

### Definicija ortogonalne baze

Ortogonalna množica v $V$, ki je ogrodje (baza) za $V$, je **ortogonalna baza** za $V$.

**Primer:** Standardna baza v $\mathbb{R}^n$ je ortogonalna baza glede na standardni skalarni produkt.

### Definicija ortonormirane baze

*   Vektorjem z normo 1 pravimo **normirani vektorji**.
*   Ortogonalni množici, v kateri so vsi elementi normirani, pravimo **ortonormirana množica**.
*   Ortonormirani množici, ki je baza, pravimo **ortonormirana baza**.

Definicijo ortonormiranosti množice $\{v_1, \dots, v_n\}$ se običajno na kratko pove z naslednjo formulo:
$\langle v_i, v_j \rangle = \begin{cases} 0 & \text{če } i \ne j \\ 1 & \text{če } i = j \end{cases}$.

**Primer normiranja ortogonalne baze**
Vsak neničeln vektor lahko spremenimo v normiran vektor tako, da ga delimo z njegovo normo.
Vektorji $(-1, 1, 1)$, $(1, -\frac{1}{2}, 1)$, $(1, 1, -\frac{1}{2})$ tvorijo ortogonalno bazo za $\mathbb{R}^3$, ki ni normirana. Če te vektorje normiramo (delimo s $\frac{3}{2}$), dobimo vektorje $(-\frac{2}{3}, \frac{2}{3}, \frac{2}{3})$, $(\frac{2}{3}, -\frac{1}{3}, \frac{2}{3})$, $(\frac{2}{3}, \frac{2}{3}, -\frac{1}{3})$, ki tvorijo ortonormirano bazo za $\mathbb{R}^3$.


## 4. Obstoj ortogonalne baze

Najprej ponovimo osnovne definicije. Naj bo $V$ vektorski prostor s skalarnim produktom. Množica $\{v_1, \dots, v_n\} \subset V$ je:
*   **Ortogonalna množica**, če velja $\langle v_i, v_j \rangle = 0$ za vsaka $i, j = 1, \dots, n$, kjer $i \ne j$, in če velja $v_i \ne 0$ za vsak $i = 1, \dots, n$.
*   **Ortonormirana množica**, če je ortogonalna množica in če velja $||v_i|| = 1$ za vsak $i = 1, \dots, n$.
*   **Ortogonalna baza**, če je ortogonalna množica in če je ogrodje (baza) za $V$.
*   **Ortonormirana baza**, če je ortonormirana množica in če je ogrodje (baza) za $V$.

Spomnimo se, da je vsaka ortogonalna množica linearno neodvisna. Obratno seveda ni res. Lahko pa vsako linearno neodvisno množico s preprostim postopkom predelamo v ortogonalno množico, ne da bi pri tem spremenili njeno linearno ogrinjačo. Temu postopku pravimo **Gram-Schmidtova ortogonalizacija**.

### Trditev (Gram-Schmidtova ortogonalizacija)

Naj bo $\{u_1, \dots, u_n\}$ baza. Definirajmo:
$v_1 = u_1$
$v_2 = u_2 - \frac{\langle u_2, v_1 \rangle}{\langle v_1, v_1 \rangle} v_1$
$v_3 = u_3 - \frac{\langle u_3, v_1 \rangle}{\langle v_1, v_1 \rangle} v_1 - \frac{\langle u_3, v_2 \rangle}{\langle v_2, v_2 \rangle} v_2$
$\vdots$
$v_n = u_n - \frac{\langle u_n, v_1 \rangle}{\langle v_1, v_1 \rangle} v_1 - \frac{\langle u_n, v_2 \rangle}{\langle v_2, v_2 \rangle} v_2 - \dots - \frac{\langle u_n, v_{n-1} \rangle}{\langle v_{n-1}, v_{n-1} \rangle} v_{n-1}$
Potem je $\{v_1, \dots, v_n\}$ ortogonalna baza.

**Dokaz (skica):**
S popolno indukcijo dokažemo, da je za vsak $k = 1, \dots, n$ množica $\{v_1, \dots, v_k\}$ ortogonalna.
Baza indukcije: $v_1 = u_1 \ne 0$, torej je $\{v_1\}$ ortogonalna.
Indukcijski korak: Recimo, da trditev drži za nek $k < n$. S pomočjo formule
$v_{k+1} = u_{k+1} - \sum_{i=1}^k \frac{\langle u_{k+1}, v_i \rangle}{\langle v_i, v_i \rangle} v_i \quad (1)$
dokazujemo, da trditev velja tudi za $k+1$. Če (1) skalarno pomnožimo z $v_j$ za vsak $j = 1, \dots, k$ in upoštevamo ortogonalnost $\{v_1, \dots, v_k\}$, dobimo:
$\langle v_{k+1}, v_j \rangle = \langle u_{k+1}, v_j \rangle - \sum_{i=1}^k \frac{\langle u_{k+1}, v_i \rangle}{\langle v_i, v_i \rangle} \langle v_i, v_j \rangle = \langle u_{k+1}, v_j \rangle - \frac{\langle u_{k+1}, v_j \rangle}{\langle v_j, v_j \rangle} \langle v_j, v_j \rangle = 0$.
Torej so elementi množice $\{v_1, \dots, v_k, v_{k+1}\}$ paroma ortogonalni.
Za dokaz ortogonalnosti množice moramo še preveriti, da je $v_{k+1} \ne 0$. Če bi veljalo $v_{k+1} = 0$, potem bi iz zgornje formule sledilo $u_{k+1} = \sum_{i=1}^k \frac{\langle u_{k+1}, v_i \rangle}{\langle v_i, v_i \rangle} v_i \in \mathrm{Lin}\{v_1, \dots, v_k\}$.
Iz prvih $k$ formul v Gram-Schmidtovi ortogonalizaciji sledi tudi $u_1, \dots, u_k \in \mathrm{Lin}\{v_1, \dots, v_k\}$.
Torej $u_{k+1} \in \mathrm{Lin}\{v_1, \dots, v_k\}$. Ker pa je $\mathrm{Lin}\{v_1, \dots, v_k\} = \mathrm{Lin}\{u_1, \dots, u_k\}$, bi to pomenilo $u_{k+1} \in \mathrm{Lin}\{u_1, \dots, u_k\}$, kar je v protislovju z linearno neodvisnostjo baze $\{u_1, \dots, u_n\}$.

### Izrek o obstoju ortogonalne baze

Vsak končnorazsežen vektorski prostor s skalarnim produktom ima ortogonalno bazo. Poleg tega lahko vsako ortogonalno množico dopolnimo do ortogonalne baze.

**Dokaz (skica):**
Prvi del dokažemo tako, da vzamemo poljubno bazo in jo s pomočjo Gram-Schmidtove ortogonalizacije predelamo v ortogonalno bazo.
Drugi del dokažemo tako, da ortogonalno množico $\{u_1, \dots, u_m\}$ najprej dopolnimo do običajne baze $\{u_1, \dots, u_m, \dots, u_n\}$ in potem uporabimo Gram-Schmidtovo ortogonalizacijo. Dobimo $v_1 = u_1, \dots, v_m = u_m, \dots$, torej dobljena ortogonalna baza res vsebuje množico $\{u_1, \dots, u_m\}$.
Odtod z normiranjem vektorjev dobimo:

### Posledica

Vsak končnorazsežen vektorski prostor s skalarnim produktom ima ortonormirano bazo. Poleg tega lahko vsako ortonormirano množico dopolnimo do ortonormirane baze.

### Primer (Gram-Schmidtova ortogonalizacija za polinome)

Naj bo $V$ vektorski prostor vseh realnih polinomov stopnje $\le 3$ in naj bo skalarni produkt na $V$ definiran z $\langle p, q \rangle = \int_{-1}^1 p(x)q(x)dx$. Konstruirajmo ortonormirano bazo za $V$.
Vzemimo standardno bazo $\{u_1=1, u_2=x, u_3=x^2, u_4=x^3\}$.
Z Gram-Schmidtovo ortogonalizacijo dobimo:
$v_1 = 1$
$v_2 = x - \frac{\langle x, 1 \rangle}{\langle 1, 1 \rangle} 1 = x - \frac{0}{2} \cdot 1 = x$
$v_3 = x^2 - \frac{\langle x^2, 1 \rangle}{\langle 1, 1 \rangle} 1 - \frac{\langle x^2, x \rangle}{\langle x, x \rangle} x = x^2 - \frac{2/3}{2} \cdot 1 - \frac{0}{2/3} \cdot x = x^2 - \frac{1}{3}$
$v_4 = x^3 - \frac{\langle x^3, 1 \rangle}{\langle 1, 1 \rangle} 1 - \frac{\langle x^3, x \rangle}{\langle x, x \rangle} x - \frac{\langle x^3, x^2 - 1/3 \rangle}{\langle x^2 - 1/3, x^2 - 1/3 \rangle} (x^2 - 1/3) = x^3 - 0 - \frac{2/5}{2/3} x - 0 = x^3 - \frac{3}{5}x$

Vektorji $v_1, v_2, v_3, v_4$ so ortogonalna baza za $V$.
Izračunamo njihove norme in normalizacije:
$||v_1||^2 = \int_{-1}^1 1 dx = 2 \implies \frac{v_1}{||v_1||} = \frac{1}{\sqrt{2}}$
$||v_2||^2 = \int_{-1}^1 x^2 dx = \frac{2}{3} \implies \frac{v_2}{||v_2||} = \sqrt{\frac{3}{2}} x$
$||v_3||^2 = \int_{-1}^1 (x^2 - \frac{1}{3})^2 dx = \frac{8}{45} \implies \frac{v_3}{||v_3||} = \sqrt{\frac{45}{8}} (x^2 - \frac{1}{3})$
$||v_4||^2 = \int_{-1}^1 (x^3 - \frac{3}{5}x)^2 dx = \frac{8}{175} \implies \frac{v_4}{||v_4||} = \sqrt{\frac{175}{8}} (x^3 - \frac{3}{5}x)$
Normalizirani vektorji tvorijo ortonormirano bazo za $V$.

**Opomba:** Iz tega primera vidimo, da je ortonormirana baza običajno vključuje komplicirane korene. Za računske namene so zato pogosto boljše ortogonalne baze. Za teoretične namene pa so boljše ortonormirane baze.

## 5. Prednosti ortogonalnih baz

Glavna prednost je, da je vektor preprosteje razviti po ortogonalni bazi.

### Izrek (Fourierov razvoj)

Naj bo $V$ vektorski prostor s skalarnim produktom in $\{v_1, \dots, v_n\}$ ortogonalna baza za $V$. Potem za vsak element $v \in V$ velja:
$v = \sum_{i=1}^n \frac{\langle v, v_i \rangle}{\langle v_i, v_i \rangle} v_i$.
Če je baza ortonormirana, se formula poenostavi v $v = \sum_{i=1}^n \langle v, v_i \rangle v_i$.

**Dokaz (skica):**
Ker je $\{v_1, \dots, v_n\}$ baza za $V$, obstajajo taki skalarji $\alpha_1, \dots, \alpha_n$, da velja $v = \sum_{i=1}^n \alpha_i v_i$. Če to enakost skalarno pomnožimo z $v_j$ za nek $j$, dobimo:
$\langle v, v_j \rangle = \langle \sum_{i=1}^n \alpha_i v_i, v_j \rangle = \sum_{i=1}^n \alpha_i \langle v_i, v_j \rangle = \alpha_j \langle v_j, v_j \rangle$.
Pri zadnjem enačaju smo upoštevali, da je $\langle v_i, v_j \rangle = 0$ za vse $i$, ki so različni od $j$.
Odtod izrazimo $\alpha_j = \frac{\langle v, v_j \rangle}{\langle v_j, v_j \rangle}$.

Druga prednost ortogonalnih baz je, da je iz razvoja elementa po taki bazi zelo preprosto izračunati njegovo normo. Iz $v = \sum_{i=1}^n \alpha_i v_i$ namreč sledi:
$||v||^2 = \langle v, v \rangle = \langle \sum_{i=1}^n \alpha_i v_i, \sum_{j=1}^n \alpha_j v_j \rangle = \sum_{i=1}^n \sum_{j=1}^n \alpha_i \overline{\alpha_j} \langle v_i, v_j \rangle = \sum_{i=1}^n \alpha_i \overline{\alpha_i} \langle v_i, v_i \rangle = \sum_{i=1}^n |\alpha_i|^2 \langle v_i, v_i \rangle$.

### Izrek (Parsevalova identiteta)

Naj bo $V$ vektorski prostor s skalarnim produktom in $\{v_1, \dots, v_n\}$ ortogonalna baza za $V$. Potem za vsak element $v \in V$ velja:
$||v||^2 = \sum_{i=1}^n \frac{|\langle v, v_i \rangle|^2}{\langle v_i, v_i \rangle}$.
Če je baza ortonormirana, se formula poenostavi v $||v||^2 = \sum_{i=1}^n |\langle v, v_i \rangle|^2$.

Tretja prednost ortogonalnih baz je, da je zelo preprosto izračunati ortogonalno projekcijo vektorja na podprostor.

### Definicija ortogonalne projekcije

Naj bo $V$ vektorski prostor s skalarnim produktom, $v$ vektor iz $V$ in $W$ vektorski podprostor v $V$. Vektorju iz $W$, ki je najbližje vektorju $v$, pravimo **ortogonalna projekcija** vektorja $v$ na podprostor $W$.
**Opomba:** Razdalja med dvema vektorjema v $V$ je definirana kot norma njune razlike. Ortogonalna projekcija vektorja $v \in V$ na podprostor $W \subset V$ je torej tak vektor $v' \in W$, da velja $||v - w|| > ||v - v'||$ za vsak vektor $w \in W$, ki je različen od $v'$.

### Izrek o ortogonalni projekciji

Naj bo $V$ vektorski prostor s skalarnim produktom in $W$ končnorazsežen vektorski podprostor v $V$ z ortogonalno bazo $\{w_1, \dots, w_k\}$. Potem je ortogonalna projekcija vektorja $v \in V$ na podprostor $W$ dana s formulo:
$v' = \sum_{i=1}^k \frac{\langle v, w_i \rangle}{\langle w_i, w_i \rangle} w_i$.
Če je baza ortonormirana, se formula poenostavi v $v' = \sum_{i=1}^k \langle v, w_i \rangle w_i$.

**Opomba:** V dokazu bomo uporabili Pitagorov izrek, ki pravi, da za pravokotna vektorja $a$ in $b$ velja $||a + b||^2 = ||a||^2 + ||b||^2$. To dokažemo z direktnim računom: $\langle a+b, a+b \rangle = \langle a,a \rangle + \langle a,b \rangle + \langle b,a \rangle + \langle b,b \rangle = \langle a,a \rangle + \langle b,b \rangle$, ker sta $a$ in $b$ pravokotna ($\langle a,b \rangle = \langle b,a \rangle = 0$).

**Dokaz izreka o ortogonalni projekciji (skica):**
Ker je $v'$ linearna kombinacija vektorjev $w_i$ iz $W$, je $v'$ element $W$. Radi bi pokazali, da za vsak $w \in W$, ki je različen od $v'$, velja $||v - w|| > ||v - v'||$. Vzemimo poljuben $w \in W$ in ga razvijmo po bazi za $W$. Dobimo $w = \sum_{i=1}^k \beta_i w_i$, kjer je $\beta_i = \frac{\langle w, w_i \rangle}{\langle w_i, w_i \rangle}$ za vse $i$. Pišimo $v' = \sum_{i=1}^k \alpha_i w_i$, kjer je $\alpha_i = \frac{\langle v, w_i \rangle}{\langle w_i, w_i \rangle}$ za vse $i$.
1.  **Korak:** Dokažemo, da je vektor $v - v'$ pravokoten na vse $w_j$.
    $\langle v - v', w_j \rangle = \langle v, w_j \rangle - \langle v', w_j \rangle = \langle v, w_j \rangle - \sum_{i=1}^k \alpha_i \langle w_i, w_j \rangle = \langle v, w_j \rangle - \alpha_j \langle w_j, w_j \rangle = 0$.
2.  **Korak:** Dokažemo, da je vektor $v - v'$ pravokoten na vektor $v' - w$.
    $\langle v - v', v' - w \rangle = \langle v - v', \sum_{i=1}^k (\alpha_i - \beta_i) w_i \rangle = \sum_{i=1}^k (\alpha_i - \beta_i) \langle v - v', w_i \rangle = 0$ po 1. koraku.
3.  **Korak:** Dokažemo, da je $||v - w||^2 = ||v - v'||^2 + ||v' - w||^2$.
    To je ravno Pitagorov izrek za vektorja $a = v - v'$ in $b = v' - w$, ki sta pravokotna po 2. koraku.
Iz 3. koraka sledi, da je $||v - w||^2 > ||v - v'||^2$, če je $v' \ne w$.

## 6. Ortogonalni komplement

### Definicija ortogonalnega komplementa

Naj bo $V$ vektorski prostor s skalarnim produktom in naj bo $S$ podmnožica v $V$. Pravimo, da je vektor $v \in V$ **ortogonalen** na množico $S$, če velja $\langle v, s \rangle = 0$ za vsak $s \in S$. Množico vseh vektorjev iz $V$, ki so ortogonalni na množico $S$, označimo z $S^\perp$ in ji pravimo **ortogonalni komplement $S$**.

### Trditev

Za vsako podmnožico $S$ v $V$ je $S^\perp$ vektorski podprostor v $V$.

**Dokaz (skica):**
Če $v_1, v_2 \in S^\perp$, je (po definiciji $S^\perp$) $\langle v_1, s \rangle = 0$ in $\langle v_2, s \rangle = 0$ za vsak $s \in S$. Potem je za vsaka skalarja $\alpha_1, \alpha_2$ tudi $\langle \alpha_1 v_1 + \alpha_2 v_2, s \rangle = \alpha_1 \langle v_1, s \rangle + \alpha_2 \langle v_2, s \rangle = 0 + 0 = 0$ za vsak $s \in S$. Odtod sledi (spet po definiciji $S^\perp$), da je $\alpha_1 v_1 + \alpha_2 v_2 \in S^\perp$, torej je $S^\perp$ vektorski podprostor.

### Trditev

Za vsako podmnožico $S$ v $V$ je $S^\perp = (\mathrm{Lin}S)^\perp$.

**Dokaz (skica):**
Če je vektor $v$ ortogonalen na elemente $s_1, \dots, s_k \in S$, potem je ortogonalen tudi na vsako njihovo linearno kombinacijo, saj velja:
$\langle v, \alpha_1 s_1 + \dots + \alpha_k s_k \rangle = \overline{\alpha_1} \langle v, s_1 \rangle + \dots + \overline{\alpha_k} \langle v, s_k \rangle = \overline{\alpha_1} \cdot 0 + \dots + \overline{\alpha_k} \cdot 0 = 0$.

### Primer ortogonalnega komplementa

Naj bo $V$ končnorazsežen vektorski prostor s skalarnim produktom, $\{u_1, \dots, u_k\}$ ortogonalna množica v $V$ in $\{v_1, \dots, v_l\}$ njena dopolnitev do ortogonalne baze za $V$. Potem je $(\mathrm{Lin}\{u_1, \dots, u_k\})^\perp = \mathrm{Lin}\{v_1, \dots, v_l\}$.

**Dokaz (skica):**
Vzemimo poljuben element $v \in V$ in ga razvijmo po bazi za $V$. Dobimo $v = \sum_{i=1}^k \alpha_i u_i + \sum_{j=1}^l \beta_j v_j$. Ker je $\langle v, u_i \rangle = \alpha_i \langle u_i, u_i \rangle$, je $v$ ortogonalen na vse $u_i$ natanko tedaj, ko so vsi $\alpha_i$ enaki nič. To pa velja natanko tedaj, ko je $v \in \mathrm{Lin}\{v_1, \dots, v_l\}$.

### Izrek o ortogonalnem razcepu

Naj bo $V$ končnorazsežen prostor s skalarnim produktom in naj bo $U$ podprostor v $V$. Potem velja naslednje:
1.  $\dim U^\perp = \dim V - \dim U$.
2.  $(U^\perp)^\perp = U$.
3.  $V = U \oplus U^\perp$.

**Dokaz (skica):**
Naj bo $\{u_1, \dots, u_k\}$ ortogonalna baza za $U$ in naj bo $\{v_1, \dots, v_l\}$ njena dopolnitev do ortogonalne baze za $V$.
Po zgornjem primeru je $U^\perp = \mathrm{Lin}\{v_1, \dots, v_l\}$. Torej je $\dim U + \dim U^\perp = k + l$, kar je enako $\dim V$. To nam da prvo trditev.
Drugi del dokažemo tako, da v primeru zamenjamo bazo iz $u_i$ z bazo iz $v_j$. Ker je $\{v_1, \dots, v_l\}$ ortogonalna baza za $U^\perp$, in ker je $\{u_1, \dots, u_k\}$ njena dopolnitev do ortogonalne baze za $V$, je $(U^\perp)^\perp = \mathrm{Lin}\{u_1, \dots, u_k\} = U$.
Tretji del sledi iz $V = \mathrm{Lin}\{u_1, \dots, u_k\} \oplus \mathrm{Lin}\{v_1, \dots, v_l\}$ in primera.

**Opomba:** Formuli $V = U \oplus U^\perp$ pravimo **ortogonalni razcep** prostora $V$ glede na podprostor $U$.
To formulo lahko dokažemo tudi s pomočjo izreka o ortogonalni projekciji. Za vsak element $v \in V$ lahko izračunamo njegovo projekcijo $v'$ na podprostor $U$. Iz dokaza izreka o ortogonalni projekciji vemo, da je vektor $v - v'$ pravokoten na vse vektorje podprostora $U$. Velja torej $v - v' \in U^\perp$. Iz $v = v' + (v - v')$ torej sledi, da je vsak element iz $V$ vsota elementa iz $U$ in elementa iz $U^\perp$, kar dokaže formulo $V = U + U^\perp$. Treba je preveriti še $U \cap U^\perp = \{0\}$. Vsak element $u \in U \cap U^\perp$ je pravokoten tudi sam nase, torej je $\langle u, u \rangle = 0$, kar pomeni $u=0$.

## 5. Linearni funkcionali (ponovitev)

Linearni funkcionali so zelo posebni primeri linearnih preslikav.

### Definicija linearnega funkcionala

Naj bo $V$ vektorski prostor nad obsegom $F$. Linearni preslikavi iz $V$ v $F$ pravimo **linearen funkcional** na $V$.
**Opomba:** V definiciji smo upoštevali, da je tudi $F$ vektorski prostor nad $F$. To je poseben primer vektorskega prostora $F^n$ za $n=1$.

### Primera linearnih funkcionalov

Naj bo $V$ vektorski prostor vseh realnih polinomov stopnje $\le n$. Potem sta:
$\phi(p) = \int_0^1 p(x)dx$ in $\psi(p) = p(1)$
dva primera linearnih funkcionalov na $V$.

### Trditev (Matrika linearnega funkcionala)

Naj bo $L$ linearen funkcional na vektorskem prostoru $V$, naj bo $\mathcal{B} = \{v_1, \dots, v_n\}$ baza za $V$ in naj bo $\mathcal{S} = \{1\}$ standardna baza za $F$. Matrika $L$ glede na ti dve bazi ima eno vrstico in $n$ stolpcev. Velja:
$[L]_{\mathcal{S} \leftarrow \mathcal{B}} = [L(v_1) \ \dots \ L(v_n)]$.

**Nadaljevanje primera (matrike funkcionalov):**
Naj bo $\mathcal{B} = \{1, x, \dots, x^n\}$ in naj bosta $\phi$ ter $\psi$ kot zgoraj. Potem je:
$[\phi]_{\mathcal{S} \leftarrow \mathcal{B}} = [1 \ \frac{1}{2} \ \frac{1}{3} \ \dots \ \frac{1}{n+1}]$
$[\psi]_{\mathcal{S} \leftarrow \mathcal{B}} = [1 \ 1 \ 1 \ \dots \ 1]$

O linearnih funkcionalih na vektorskih prostorih s skalarnim produktom lahko povemo precej več.

### Primer (linearen funkcional, definiran s skalarnim produktom)

Naj bo $V$ vektorski prostor s skalarnim produktom in $w \in V$. Potem je
$\phi_w(v) := \langle v, w \rangle$
linearen funkcional na $V$.
**Dokaz:** To sledi iz linearnosti skalarnega produkta v prvem faktorju.

### Rieszov izrek o reprezentaciji linearnih funkcionalov

Naj bo $V$ končnorazsežen vektorski prostor s skalarnim produktom in naj bo $\phi$ linearen funkcional na $V$. Potem obstaja tak vektor $w \in V$, da je
$\phi(v) = \langle v, w \rangle$
za vsak $v \in V$. Vektor $w$ je enolično določen.

Izrek lahko povemo tudi takole: Vsak linearen funkcional na $V$ je oblike $\phi_w$ (glej primer) za natanko določen $w \in V$.

**Dokaz (skica):**
Naj bo $\{v_1, \dots, v_n\}$ ortonormirana baza za $V$. Vzemimo poljuben $v \in V$ in ga razvijmo po tej bazi. Velja $v = \sum_{i=1}^n \langle v, v_i \rangle v_i$. Odtod sledi:
$\phi(v) = \phi(\sum_{i=1}^n \langle v, v_i \rangle v_i) = \sum_{i=1}^n \langle v, v_i \rangle \phi(v_i)$ (zaradi linearnosti $\phi$).
Če upoštevamo še konjugirano linearnost skalarnega produkta v drugem faktorju, dobimo:
$\phi(v) = \sum_{i=1}^n \langle v, v_i \rangle \phi(v_i) = \sum_{i=1}^n \langle v, \overline{\phi(v_i)} v_i \rangle = \langle v, \sum_{i=1}^n \overline{\phi(v_i)} v_i \rangle$.
Označimo $w = \sum_{i=1}^n \overline{\phi(v_i)} v_i$. Opazimo, da ta vektor ni odvisen od $v$, ampak samo od $\phi$ in od baze. Dokazali smo, da velja $\phi(v) = \langle v, w \rangle$ za vsak $v \in V$.
Pokažimo še, da je vektor $w$ enolično določen s funkcionalom $\phi$.
Če velja $\phi(v) = \langle v, w_1 \rangle$ za vsak $v \in V$ in $\phi(v) = \langle v, w_2 \rangle$ za vsak $v \in V$, potem:
$0 = \phi(v) - \phi(v) = \langle v, w_1 \rangle - \langle v, w_2 \rangle = \langle v, w_1 - w_2 \rangle$ za vsak $v \in V$.
Vstavimo $v = w_1 - w_2$ in dobimo $\langle w_1 - w_2, w_1 - w_2 \rangle = 0$. Vemo, da odtod sledi $w_1 - w_2 = 0$, se pravi $w_1 = w_2$.