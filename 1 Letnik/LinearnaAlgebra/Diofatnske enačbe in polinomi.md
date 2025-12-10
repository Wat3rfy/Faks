

**Kolobarji $\mathbb{Z}_n$ in $F[x]/(p)$**

V tem razdelku bomo konstruirali dva tipa komutativnih kolobarjev, v nadaljevanju pa se bomo ukvarjali s tem, kdaj so ti kolobarji polja.

**Kolobar $\mathbb{Z}_n$**
Vzemimo neko naravno število $n$ in označimo $\mathbb{Z}_n = \{0, 1, \dots, n-1\}$. Za vsaka $x, y \in \mathbb{Z}_n$ naj bo
$x \oplus y := (x+y) \pmod n$ in $x \odot y := (x \cdot y) \pmod n$
kjer sta $+$ in $\cdot$ operaciji na $\mathbb{Z}$ in je $z \pmod n$ ostanek pri deljenju z $n$. Trdimo, da je $(\mathbb{Z}_n, \oplus, \odot)$ komutativen in asociativen kolobar z enoto.
Komutativnost $\oplus$ in $\odot$ sledi direktno iz komutativnosti $+$ in $\cdot$.
Pokažimo asociativnost $\oplus$. Vzemimo $x, y, z \in \mathbb{Z}_n$ in označimo $u = x \oplus y$ in $v = y \oplus z$. Vzemimo take $i, j, k, l \in \mathbb{N}$, da je
$x+y = in+u$
$u+z = kn+(u \oplus z)$
$y+z = jn+v$
$x+v = ln+(x \oplus v)$

Odtod sledi
$(x \oplus y) \oplus z = u \oplus z = u+z-kn = (x+y-in)+z-kn$
$x \oplus (y \oplus z) = x \oplus v = x+v-ln = x+(y+z-jn)-ln$
torej je $(x \oplus y) \oplus z - x \oplus (y \oplus z) = (j+l-i-k)n$. Ker sta $(x \oplus y) \oplus z$ in $x \oplus (y \oplus z)$ med $0$ in $n-1$ in ker je njuna razlika deljiva z $n$, sta enaka.
Podobno dokažemo tudi asociativnost $\odot$ in distributivnost. Aditivna enota je $0$, multiplikativna enota pa $1$. Aditivni inverz elementa $x \neq 0$ je $n-x$.

Opomba: Preslikava
$f: \mathbb{Z} \to \mathbb{Z}_n$, $f(z) := z \pmod n$
je homomorfizem kolobarjev z enoto iz $(\mathbb{Z}, +, \cdot)$ v $(\mathbb{Z}_n, \oplus, \odot)$.
Opomba: Če $n$ ni praštevilo, potem kolobar $(\mathbb{Z}_n, \oplus, \odot)$ ni obseg. Iz razcepa $n = rs$, kjer $r, s < n$, namreč sledi, da je $r \odot s = 0$ in $r \neq 0$ in $s \neq 0$.

**Kolobar $F[x]/(p)$**
Naj bo $F$ polje. Označimo s $F[x]$ množico vseh polinomov v spremenljivki $x$ s koeficienti iz $F$. Običajno seštevanje in množenje polinomov označimo s $+$ in $\cdot$. Potem je $(F[x], +, \cdot)$ komutativen in asociativen kolobar z enoto.
Vzemimo nek nekonstanten polinom $p \in F[x]$ in označimo z $F[x]/(p)$ množico vseh polinomov iz $F[x]$, ki so nižje stopnje kot $p$. Za vsaka polinoma $r, s \in F[x]/(p)$ definirajmo polinoma
$r \oplus s := r+s$ in $r \odot s := (r \cdot s) \pmod p$
kjer je $q \pmod p$ ostanek pri deljenju polinoma $q \cdot s$ s polinomom $p$.
Podobno kot v prejšnjem primeru pokažemo, da je $(F[x]/(p), \oplus, \odot)$ komutativen in asociativen kolobar z enoto.

Opomba: Preslikava
$\phi: F[x] \to F[x]/(p)$, $\phi(q) := q \pmod p$
je homomorfizem kolobarjev z enoto iz $(F[x], +, \cdot)$ v $(F[x]/(p), \oplus, \odot)$.

**Definicija razcepnega in nerazcepnega polinoma**
Polinom $p \in F[x]$ je **razcepen**, če obstajata taka polinoma $p_1, p_2 \in F[x]$ stopnje $\ge 1$, da je $p = p_1 p_2$. Polinom, ki ni razcepen, je **nerazcepen**.

Opomba: Konstantni in linearni polinomi so nerazcepni.

**Primer**
Polinom $x^2 - 3$ leži tako v $\mathbb{Q}[x]$ kot v $\mathbb{R}[x]$. V $\mathbb{Q}[x]$ je nerazcepen, ker nima racionalne ničle. V $\mathbb{R}[x]$ je razcepen, ker velja $x^2 - 3 = (x + \sqrt{3})(x - \sqrt{3})$.

Opomba: Preslikavi $\phi: \mathbb{Q}[x]/(x^2 - 3) \to \mathbb{Q}(\sqrt{3})$, $\phi(q) = q(\sqrt{3})$ in $\psi: \mathbb{R}[x]/(x^2 - 3) \to \mathbb{R} \times \mathbb{R}$, $\psi(q) = (q(\sqrt{3}), q(-\sqrt{3}))$ sta izomorfizma kolobarjev. Ker je $\mathbb{Q}(\sqrt{3})$ polje, je tudi $\mathbb{Q}[x]/(x^2 - 3)$ polje. $\mathbb{R} \times \mathbb{R}$ ni polje.

**Trditev**
Če je polinom $p \in F[x]$ razcepen, potem kolobar $(F[x]/(p), \oplus, \odot)$ ni obseg.

Dokaz je podoben kot pri $\mathbb{Z}_n$. Če je $p$ razcepen v $F[x]$, potem obstajata taka neničelna polinoma $p_1, p_2 \in F[x]/(p)$, da je $p_1 \odot p_2 = 0$.

**Linearna diofantska enačba**
V dokazu glavnega izreka bomo potrebovali naslednji tehnični rezultat.

**Izrek o linearni diofantski enačbi**
Če sta celi števili $a_1$ in $a_2$ tuji (= njun največji skupni delitelj je 1), potem obstajata taki celi števili $x$ in $y$, da velja $a_1 x + a_2 y = 1$.

Dokaz: Brez škode lahko predpostavimo, da sta $a_1$ in $a_2$ naravni števili. Po izreku o deljenju z ostankom obstajajo taka naravna števila $k_1, \dots, k_n$ in $a_3, \dots, a_{n+1}$, da velja:
$a_1 = k_1 a_2 + a_3 \quad \text{kjer } a_3 < a_2 \quad (1)$
$a_2 = k_2 a_3 + a_4 \quad \text{kjer } a_4 < a_3 \quad (2)$
$\vdots$
$a_{n-1} = k_{n-1} a_n + a_{n+1} \quad \text{kjer } a_{n+1} < a_n \quad (n-1)$
$a_n = k_n a_{n+1} \quad (n)$
Postopek smo nadaljevali toliko časa, dokler ni ostanek padel na nič. Ker se ostanek v vsakem koraku zmanjša, je korakov samo končno mnogo.

Pokažimo najprej, da je $a_{n+1} = 1$. Iz enačbe (n) sledi, da $a_{n+1}$ deli $a_n$. Odtod in iz enačbe (n-1) sledi, da $a_{n+1}$ deli $a_{n-1}$. Odtod in iz enačbe (n-2) sledi, da $a_{n+1}$ deli $a_{n-2}$. Ta postopek nadaljujemo, dokler ne pridemo do prve enačbe. Torej $a_{n+1}$ deli tako $a_1$ kot $a_2$. Ker sta $a_1$ in $a_2$ tuji, odtod sledi, da je $a_{n+1} = 1$.

Pokažimo sedaj, da za vsako naravno število $m = 1, \dots, n$ obstajata taki celi števili $x_m$ in $y_m$, da velja
$a_1 x_m + a_2 y_m = a_{m+1} \quad (*)$
Pri $m = 1$ lahko vzamemo kar $x_1 = 0$ in $y_1 = 1$. Iz enačbe (1) sledi $a_3 = a_1 - k_2 a_2$, torej lahko vzamemo $x_2 = 1$ in $y_2 = -k_2$. Izpeljimo sedaj še rekurzivni zvezi za $x_m$ in $y_m$. Iz enačbe (m-1) sledi, da je $a_{m+1} = a_{m-1} - k_{m-1} a_m$, kar je po indukcijski predpostavki enako $(a_1 x_{m-2} + a_2 y_{m-2}) - k_{m-1}(a_1 x_{m-1} + a_2 y_{m-1})$. Če to primerjamo z želeno relacijo $(*)$, dobimo $x_m = x_{m-2} - k_{m-1} x_{m-1}$ in $y_m = y_{m-2} - k_{m-1} y_{m-1}$. Ko je $m$ enak $n$, dobimo ravno izrek: $a_1 x_n + a_2 y_n = a_{n+1} = 1$.

Naš glavni rezultat je:

**Izrek o $\mathbb{Z}_p$**
Če je $p$ praštevilo, potem je kolobar $\mathbb{Z}_p$ polje.

Dokaz. Vemo že, da je $\mathbb{Z}_p$ komutativen in asociativen kolobar z enoto. Pokazati moramo še, da ima vsak neničelni element multiplikativen inverz. Vzemimo $a_2 = p$ in naj bo $a_1$ poljuben neničeln element v $\mathbb{Z}_p$. Vidimo, da sta $a_1$ in $a_2$ tuji števili. Po izreku o linearni diofantski enačbi obstajata taki celi števili $x$ in $y$, da je $a_1 x + a_2 y = 1$. Odtod sledi, da je $a_1^{-1} = x \pmod p$.

Podobno dokažemo tudi naslednji rezultat:

**Izrek o $F[x]/(p)$**
Če je $p \in F[x]$ nerazcepen polinom stopnje $\ge 1$, potem je $F[x]/(p)$ polje.

Dokaz: Dva polinoma sta tuja, če nimata skupnega faktorja stopnje $\ge 1$. Če vzamemo $p_2 = p$ iz izreka in $p_1 \neq 0$ polinom, ki je nižje stopnje kot $p$, potem sta $p_1$ in $p_2$ tuja. Za vsaka tuja polinoma $p_1$ in $p_2$ konstruiramo kot zgoraj taka polinoma $q_1$ in $q_2$, da je $p_1 q_1 + p_2 q_2 = 1$ in dobimo izrek.

**Primer**
Poiščimo inverz elementa $12$ v polju $\mathbb{Z}_{41}$.
Iščemo tak $x \in \mathbb{Z}$, da je $12x \pmod{41} = 1$. To velja natanko tedaj, ko obstaja tak $y \in \mathbb{Z}$, da velja $12x + 41y = 1$. Evklidov algoritem nam da
$$41 = 3 \cdot 12 + 5 \implies 5 = 41 - 3 \cdot 12$$
$$12 = 2 \cdot 5 + 2 \implies 2 = 12 - 2 \cdot 5$$
$$5 = 2 \cdot 2 + 1 \implies 1 = 5 - 2 \cdot 2$$
Ko vstavimo prvo enačbo v drugo, dobimo
$2 = 12 - 2 \cdot (41 - 3 \cdot 12) = -2 \cdot 41 + 7 \cdot 12$
Ko to in prvo enačbo vstavimo v tretjo enačbo, dobimo
$1 = (41 - 3 \cdot 12) - 2 \cdot (-2 \cdot 41 + 7 \cdot 12) = 5 \cdot 41 + (-17) \cdot 12$
Torej je $x = -17$, kar pa ni v $\mathbb{Z}_{41}$. Sledi $12^{-1} = x \pmod{41} = 24$.

**Primer**
Izračunajmo inverz polinoma $x^3 - 2x + 2$ v polju $\mathbb{Q}[x]/(x^4 + 1)$.
Najprej uporabimo Evklidov algoritem
$$x^4 + 1 = x(x^3 - 2x + 2) + 2x^2 - 2x + 1$$
$$x^3 - 2x + 2 = \frac{x+1}{2}(2x^2 - 2x + 1) + \frac{3-3x}{2}$$
$$2x^2 - 2x + 1 = -\frac{4x}{3}\left(\frac{3-3x}{2}\right) + 1$$
Iz prve enačbe dobimo
$2x^2 - 2x + 1 = (x^4 + 1) - x(x^3 - 2x + 2)$
Iz druge enačbe potem dobimo
$$\frac{3-3x}{2} = (x^3 - 2x + 2) - \frac{x+1}{2}(2x^2 - 2x + 1)$$
$$= (x^3 - 2x + 2) - \frac{x+1}{2}((x^4 + 1) - x(x^3 - 2x + 2))$$
$$= -\frac{x+1}{2}(x^4 + 1) + \frac{x^2+x+2}{2}(x^3 - 2x + 2)$$

Upoštevajmo sedaj oba izraza v tretji enačbi. Dobimo
$$1 = (2x^2 - 2x + 1) + \frac{4x}{3}\left(\frac{3-3x}{2}\right)$$
$$= ((x^4 + 1) - x(x^3 - 2x + 2)) + \frac{4x}{3}\left(-\frac{x+1}{2}(x^4 + 1) + \frac{x^2+x+2}{2}(x^3 - 2x + 2)\right)$$
$$= \frac{3-2x(x+1)}{3}(x^4 + 1) + \frac{-3x+2x(x^2+x+2)}{3}(x^3 - 2x + 2)$$
Inverz polinoma $x^3 - 2x + 2$ v $\mathbb{Q}[x]/(x^4 + 1)$ je torej
$$\frac{-3x + 2x(x^2+x+2)}{3} = \frac{2x^3 + 2x^2 + x}{3}$$
Produkt polinoma in njegovega inverza je res enak $1$ v $\mathbb{Q}[x]/(x^4 + 1)$, ker
$$\frac{2x^3 + 2x^2 + x}{3}(x^3 - 2x + 2) = \frac{2x^2+2x-3}{3}(x^4 + 1) + 1$$

**Polja s $p^n$ elementi**
Radi bi opisali vsa končna polja. Ideja konstrukcije je naslednja:
* Vzemi praštevilo $p$ in naravno število $n$. Vemo, da je $\mathbb{Z}_p$ polje.
* Dokaži, da v $\mathbb{Z}_p[x]$ obstaja nerazcepen polinom $q(x)$ stopnje $n$.
* Dokaži, da je $\mathbb{Z}_p[x]/(q(x))$ polje s $p^n$ elementi.
Izrek o klasifikaciji končnih obsegov pravi:
* Vsako končno polje je izomorfno enemu od zgornjih polj.
* Dve končni polji z enakim številom elementov sta izomorfni.
Podrobnosti bomo izpustili. Raje si oglejmo primer.

**Polje s štirimi elementi**
Iščemo polje, ki ima štiri elemente. Kolobar $\mathbb{Z}_4$ sicer ima štiri elemente, ampak ni polje. Iskano polje je $\mathbb{Z}_2[x]/(x^2 + x + 1)$.
Množica $\mathbb{Z}_2[x]/(x^2 + x + 1)$ se sestoji iz vseh polinomov v $\mathbb{Z}_2[x]$, ki so nižje stopnje kot $x^2 + x + 1$. To so polinomi $0, 1, x, x+1$.

Operaciji na množici $\mathbb{Z}_2[x]/(x^2 + x + 1)$ sta seštevanje in množenje modulo $x^2 + x + 1$. Njuni tabeli sta:
$\oplus$ | $0$ | $1$ | $x$ | $x+1$
--- | --- | --- | --- | ---
$0$ | $0$ | $1$ | $x$ | $x+1$
$1$ | $1$ | $0$ | $x+1$ | $x$
$x$ | $x$ | $x+1$ | $0$ | $1$
$x+1$ | $x+1$ | $x$ | $1$ | $0$

$\odot$ | $0$ | $1$ | $x$ | $x+1$
--- | --- | --- | --- | ---
$0$ | $0$ | $0$ | $0$ | $0$
$1$ | $0$ | $1$ | $x$ | $x+1$
$x$ | $0$ | $x$ | $x+1$ | $1$
$x+1$ | $0$ | $x+1$ | $1$ | $x$

Pokazali smo že, da je $(\mathbb{Z}_2[x]/(x^2 + x + 1), \oplus, \odot)$ komutativen in asociativen kolobar z enoto. Iz tabele za $\odot$ se vidi, da ima vsak neničeln element inverz. Torej je ta kolobar polje.

Opomba: Tudi brez tabele za $\odot$ lahko dokažemo, da je ta kolobar polje. Zadošča dokazati, da je $x^2 + x + 1$ nerazcepen polinom v $\mathbb{Z}_2[x]$.
V $\mathbb{Z}_2[x]$ imamo dva polinoma stopnje $1$ in štiri polinome stopnje $2$. Polinoma stopnje $1$ sta $x$ in $x+1$. Razcepni polinomi stopnje $2$ so torej $x^2$, $x(x+1) = x^2+x$ in $(x+1)^2 = x^2+1$. Polinom $x^2+x+1$ ni eden od teh, torej je nerazcepen.