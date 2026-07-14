Deli in vladaj je način reševanja problemov, kjer problem **razbijemo** v manjše dele katere lahko **rešimo posebej** in potem **združimo** da dobimo **rešitev prvotnega problema**.

Govorimo o rekurziji, kjer vzamemo neko funkcijo ki nam rešuje problem in z isto funkcijo rešimo manjši problem dokler ne postane trivialen.

**Primer 1 - Urejanje tabele**

Tabelo lahko razdelimo na dve manjši, vsako posebej uredimo, nato pa ju zlijemo skupaj tako da vedno vzamemo ta manjši element iz vsake in jih postavljamo drug za drugega.



Naj bo $T(n)$ časovna zahtevnost za urejanje $n$ elementne tabele. Če pogledamo časovno zahtevnost se izkaže da je algoritem sestavljen iz delitve tabele, urejanja dveh manjših tabel in zlivanja tabele.

- $\Theta(1)$ za razbijanje tabele
- $\Theta(n)$ za zlivanje
- $2T(\frac{n}{2})$ za urejanje dveh za pol manjših tabel

$$T(n) = 2T\left(\frac{n}{2}\right)+ \Theta(n)$$

**Primer 2 - Quicksort**

Če imamo tabelo se lahko odločimo da izberemo nek specifičen element. Nato vse elemente manjše od njega damo na levo in vse večje na desno od njega. Tako nam ostaneta dve manjši tabeli ki ju uredimo na isti način.

Tukaj ne razdelimo tabele vedno na pol.
Poglejmo si 3 možnosti.

V najboljšem primeru razdelimo tabelo na pol in dobimo

$$T(n) = 2T\left(\frac{n}{2}\right)+ \Theta(n)$$

kjer velja da rabimo $\Theta(n)$ časa za porazdelitev razdelitev $n$ dolge tabele.

V slabšem primeru lahko predpostavimo da tabelo razdelimo na neko poljubno razmerje in dobimo

$$T(n) = T\left(\frac{n}{a}\right)+ T\left(1-\frac{n}{a}\right) + \Theta(n)$$

In v nasjlabšem primeru kjer ena od tabel vedno vsebuje po en element

$$T(n) = T(n-1) + T(1) + \Theta(n)$$

oz. se izkaže da če se tabela deli z nekim konstantnim odmikom bo težava podobna torej lahko rečemo da je to še vedno obupen primer

$$T(n) = T(n-k) + T(k) + \Theta(n)$$


**Primer 3 - Dvojiško iskanje**

Pri dvojiškem iskanju delamo na urejeni tabeli kjer vemo da če pogledamo srednji element lahko omejimo meje iskanja na zgornjo ali pa spodnjo polovico. Torej če iskanje v $n$ dolgi tabeli traja $T(n)$ potem bo časovna kompleksnot

$$T(n) = T\left(\frac{n}{2}\right)+ \Theta(1)$$

***

Radi bi računali te enačbe. Za dokazovanje časovne kompleksnosti takih postopkov se uporablja več metod.

**Substitucijska metoda**

Rešitev uganemo in z indukcijo dokažemo da je pravilna.

**Drevesna metoda**

Razvijemo drevo in iz tega dobimo oceno katero lahko dokažemo s substitucijsko metodo.

**Krovni izrek**

Formula z omejenimi aplikacijami.

**Primer 1 - Drevesna metoda**

*Najprej bomo rešili z drevesno metodo da ugotovimo oceno za časovno zahtevnost.*

$$T(n) = 2T\left(\frac{n}{2}\right)+ \Theta(n)$$

$$\Leftrightarrow$$

$$T(n) = 2T\left(\frac{n}{2}\right)+ kn + c$$



Če si predstavljamo drevo vemo da bomo potrebovali $T(n)$ časa. Postavimo to v koren. 

Če je $T(n) = aT\left(\frac{n}{b}\right)+ \Theta(f(n))$ potem drevo gradimo tako da v vozlišče postavimo $f(n)$ iz njega naredimo $a$ vej vsaka od teh vej pa predstavlja $T(\frac{n}{b})$


$\Theta(f(n))$ predstavlja delo ki ga opravimo za deljenje problema in združevanje rešitev plus vsak rekurzivni klic ki je predstavljen kot svoja veja.

To ponavljamo dokler ne pridemo do $T(1)$.


Torej ob aplikaciji rekurzije ugotovimo da dobimo drevo z $n$ otroci za katere predpostaivmo da so vsa na istem nivoju. To bo zahtevalo drevo z $l = \lceil \log_{2}{n} \rceil+1$ nivoji. V vsakem vozlišču smo ugotovili da se izvaja neko delo $k \frac{n}{2^{i}} + c$, $i \in \{ 0,...,l-1\}$, kjer je $l$ število nivojev. 

V končnih listih se opravi $\Theta(1)$ dela torej bomo imeli $\Theta(n)$.

Seštejemo še delo ki se opravi v nelistnih vozliščih. Imeli bomo $\lceil \log_{2}{n}\rceil$ nivojev, indeks $i$ pa gre po $\{ 0,...,\lceil \log_{2}{n}\rceil -1\}$, seštevamo pa produkt števila vozlišč na nivo $2^{i}$ in delo ki ga opravi vsako vozl. kar bo $n \frac{k}{2^{i}}$.

$$\sum_{0}^{\lceil \log_{2}{n}\rceil -1} 2^{i} \cdot k \cdot  \frac{n}{2^{i}} = nk \cdot \sum_{0}^{\lceil \log_{2}{n}\rceil -1}1 =$$
$$= nk \lceil \log_{2}n\rceil$$
$$= \Theta(n \log_{}{n})$$

Torej imamo

$$\Theta(n \log_{}{n}) + \Theta(n) = \Theta(n \log_{}{n})$$

**Substitucijska metoda**

Sedaj moramo dokazati da je $n \log_{}{n}$ pravilna časovna zahtevnost. To dokažemo z indukcijo.

Najprej dokažemo $O(n \log_{}{n})$

Predpostavimo da velja $T(n) \leq k \cdot n\log_{2}{n} - b$, kjer sta $k,b$ poljubni neničelni konstanti.

Dokaži da je 

$$T(n) = 2T\left(\frac{n}{2}\right) + kn + c \in \Theta(n \log n)$$

Naj bo induktivna predpostavka

$$T(n') = 2T\left(\frac{n'}{2}\right) + kn' + c \le C n' \log n'$$

$$\forall n : n_0 \le n' < n  \text{ in naj bo } T(1) = d$$

Velja

$$T(n) = 2T\left(\frac{n}{2}\right) + kn + c$$
$$T(n) \le 2C \frac{n}{2} \log \frac{n}{2} + kn + c$$
$$T(n) \le Cn \log n - Cn + kn + c$$
$$T(n) \le Cn \log n \impliedby kn + c \le Cn$$
$$\implies C \ge k + \frac{c}{n}$$
$$C = k + \frac{c}{n_0} = k + \frac{c}{2}$$

$$ $$

$$T(2) = 2T(1) + k2 + c$$
$$= 2d + 2k + c$$
$$\le \left(k + \frac{c}{2}\right) 2 \log 2$$
$$= 2k + c \quad \checkmark$$

torej je $T(n)$ v $O(n \log_{}{n})$. Če samo obrnemo neenačaj v predpostavki se izkaže da velja enako za $\Omega(n \log_{}{n})$ iz česar lahko sklepamo da je v $\Theta(n \log_{}{n})$

**Primer 2**

Naj bo $T(n) = T\left(\frac{n}{10}\right) + T\left(\frac{9n}{10}\right) + cn$

$$\begin{array}{ccccc}
     & & \!\!\!\!cn & & \\
     & \swarrow & & \!\!\!\!\!\!\!\!\!\!\!\!\!\!\searrow & \\
     & \!\!\!\!\!\!\!\!\!\!\!\!\frac{cn}{10} & & \quad\frac{9cn}{10} & \\
   \swarrow & \searrow & & \swarrow & \!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\searrow \\
   \!\!\!\!\!\!\!\!\!\!\frac{cn}{100} & \frac{9cn}{100} & & \!\!\!\!\!\!\!\!\!\!\!\frac{9cn}{100} & \frac{81cn}{100} \\
     & & \vdots & & 
\end{array}
\quad
\begin{array}{l}
\Sigma = cn \\
\\
\Sigma = cn \\
\\
\Sigma = cn \\ \\ 
\end{array}
\quad \Bigg| \quad \log_{\frac{10}{9}} n \text{ nivojev}$$

$$\implies cn \cdot \log_{\frac{10}{9}} n = \Theta(n \log n)$$

$$T(n') = T\left(\frac{n'}{10}\right) + T\left(\frac{9n'}{10}\right) + cn' \le K n' \log n'$$
$$n_0 \le n' < n$$

$$T(n) = T\left(\frac{n}{10}\right) + T\left(\frac{9n}{10}\right) + cn$$
$$\le K \frac{n}{10} \log \frac{n}{10} + K \frac{9n}{10} \log \frac{9n}{10} + cn$$
$$\le K \frac{n}{10} \left( \log n - \log 10 \right) + K \frac{9n}{10} \left( \log n - \log \frac{10}{9} \right) + cn$$
$$= K \frac{n}{10} \log n - K \frac{n}{10} \log 10 + K \frac{9n}{10} \log n - K \frac{9n}{10} \log \frac{10}{9} + cn$$
$$= Kn \log n - Kn \left( \frac{1}{10} \log 10 + \frac{9}{10} \log \frac{10}{9} \right) + cn$$
$$= Kn \log n - KFn + cn \le Kn \log n$$

$$\implies KFn \ge cn$$
$$K \ge \frac{cn}{Fn}$$
$$K \ge \frac{c}{F}$$

**Krovni izrek**

Če imamo enačbo oblike

$$T(n) = a T\left(\frac{n}{b}\right)+ \Theta(n^{d})$$

Potem velja

$$T(n) = \begin{cases}
\Theta(n^{d}) &;& a < b^{d} \\
\Theta(n^{d}\log_{}{n}) &;& a = b^{d} \\
\Theta(n^{\log_{b}{a}}) &;& a > b^d 
\end{cases}$$



Dokaz lahko izpeljemo z **drevesno metodo**.

Za poenostavitev dokaza predpostavimo, da je $n = b^k$ za neko celo število $k$. Prav tako predpostavimo, da je robni pogoj $T(1) = \Theta(1) = c_0$ za neko konstanto $c_0$.

Izhajamo iz enačbe:

$$T(n) = a T\left(\frac{n}{b}\right) + c n^{d}$$

Predstavljajmo si delo, ki se opravi na vsakem nivoju drevesa:

*   **Nivo 0 (koren):** Imamo $1$ vozlišče velikosti $n$. Opravljeno delo je $c n^d$.
*   **Nivo 1:** Imamo $a$ vozlišč, vsako velikosti $\frac{n}{b}$. Opravljeno delo je $a \cdot c \left(\frac{n}{b}\right)^d = c n^d \cdot \left(\frac{a}{b^d}\right)$.
*   **Nivo 2:** Imamo $a^2$ vozlišč, vsako velikosti $\frac{n}{b^2}$. Opravljeno delo je $a^2 \cdot c \left(\frac{n}{b^2}\right)^d = c n^d \cdot \left(\frac{a}{b^d}\right)^2$.
*   **Nivo $j$:** Imamo $a^j$ vozlišč, vsako velikosti $\frac{n}{b^j}$. Opravljeno delo je $a^j \cdot c \left(\frac{n}{b^j}\right)^d = c n^d \cdot \left(\frac{a}{b^d}\right)^j$.

Drevo se spusti do globine $k = \log_b n$, kjer dosežemo liste (velikost problema je $1$).

*   **Nivo $k$ (listi):** Število listov je $a^{\log_b n}$. Z uporabo logaritemske identitete $a^{\log_b n} = n^{\log_b a}$ ugotovimo, da imamo $n^{\log_b a}$ listov. Vsak list opravi $\Theta(1)$ dela, torej je skupno delo v listih enako:
    $$\Theta(n^{\log_b a})$$

Skupno delo $T(n)$ je vsota dela v vseh nelistnih vozliščih (od nivoja $0$ do $k-1$) plus delo v listih:

$$T(n) = \sum_{j=0}^{\log_b n - 1} c n^d \left(\frac{a}{b^d}\right)^j + \Theta(n^{\log_b a})$$

Konstanto $c$ in $n^d$ lahko izpostavimo pred vsoto:

$$T(n) = c n^d \sum_{j=0}^{\log_b n - 1} \left(\frac{a}{b^d}\right)^j + \Theta(n^{\log_b a})$$

Vrednost te vsote je odvisna od kvocienta geometrijskega zaporedja, ki ga označimo z $q = \frac{a}{b^d}$.


Glede na vrednost $q = \frac{a}{b^d}$ razlikujemo tri primere.

> $1)$ $a < b^d$ oz. $q < 1$
> 
> Če je $a < b^d$, je kvocient $q < 1$. Vsota v enačbi je končna geometrijska vrsta z naraščajočim številom členov, ki pa konvergira proti konstanti, ko gre $n \to \infty$:
> 
> $$\sum_{j=0}^{\log_b n - 1} q^j < \sum_{j=0}^{\infty} q^j = \frac{1}{1-q} = \Theta(1)$$
> 
> Zato je prispevek nelistnih vozlišč enak:
> $$c n^d \cdot \Theta(1) = \Theta(n^d)$$
> 
> Ker velja $a < b^d$, z logaritmiranjem dobimo $\log_b a < d$. To pomeni, da delo v listih $\Theta(n^{\log_b a})$ raste počasi in ga nadvlada delo v korenu $\Theta(n^d)$.
> 
> Skupna zahtevnost je:
> $$T(n) = \Theta(n^d) + \Theta(n^{\log_b a}) = \Theta(n^d)$$

> $2)$ $a = b^d$ (oz. $q = 1$)
> 
> Če je $a = b^d$, je kvocient $q = 1$. Vsak člen v vsoti je enak $1$. Število členov v vsoti je natanko $\log_b n$:
> 
> $$\sum_{j=0}^{\log_b n - 1} 1^j = \log_b n$$
> 
> Zato je prispevek nelistnih vozlišč enak:
> $$c n^d \cdot \log_b n = \Theta(n^d \log n)$$
> 
> Ker je $a = b^d$, velja tudi $\log_b a = d$, kar pomeni, da je delo v listih enako $\Theta(n^{\log_b a}) = \Theta(n^d)$.
> 
> Skupna zahtevnost je:
> $$T(n) = \Theta(n^d \log n) + \Theta(n^d) = \Theta(n^d \log n)$$
> 

>  $3)$ $a > b^d$ (oz. $q > 1$)
> 
> Če je $a > b^d$, je kvocient $q > 1$. V tem primeru vsota narašča in prevladuje njen zadnji člen. Za končno geometrijsko vrsto velja:
> 
> $$\sum_{j=0}^{k-1} q^j = \frac{q^k - 1}{q - 1} = \Theta(q^k)$$
> 
> Vstavimo nazaj $q = \frac{a}{b^d}$ in $k = \log_b n$:
> 
> $$q^k = \left( \frac{a}{b^d} \right)^{\log_b n} = \frac{a^{\log_b n}}{(b^{\log_b n})^d} = \frac{n^{\log_b a}}{n^d}$$
> 
> Sedaj izračunamo prispevek nelistnih vozlišč:
> $$c n^d \cdot \Theta\left( \frac{n^{\log_b a}}{n^d} \right) = \Theta(n^{\log_b a})$$
> 
> Prispevek listov je prav tako $\Theta(n^{\log_b a})$. Ker velja $\log_b a > d$, ta člen nadvlada začetni člen $n^d$.
> 
> Skupna zahtevnost je:
> $$T(n) = \Theta(n^{\log_b a}) + \Theta(n^{\log_b a}) = \Theta(n^{\log_b a})$$

Torej velja

$$T(n) = \begin{cases}
\Theta(n^{d}) & \text{če } a < b^{d} \\
\Theta(n^{d}\log n) & \text{če } a = b^{d} \\
\Theta(n^{\log_{b}{a}}) & \text{če } a > b^d 
\end{cases}$$