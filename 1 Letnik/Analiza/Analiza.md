# Analiza 1

Kaj je popolna indukcija
Kaj je zaporedje
Operacije med zaporedji
Rekurzivno zaporedje
Aritmetično, geometrično zaporedje
Omejenost zaporedij
Kaj je supremum, infimum
Kaj je limita zaporedja, konvergenca divergenca
**Konvergentno zaporedje ima natanko eno limito**
**Vsako konvergentno zaporedje je omejeno**
**Operacije med limitami zaporedij**
**Če je zaporedje monotno ima limito v sup/inf zaporedja** 
(kot posledica) **Zaporedje je konvergentno natanko tedaj ko je monotno in omejeno**
**Bernoullijeva neenakost**
**Binomska formula**
**Zaporedje $(1+\frac{1}{n})^{n}$ je konvergentno**
Eulerjevo število
Kaj je podzaporedje
**Če je L limita zaporedja je L limita podzaporedja**
**Naj bo $(a_n)_n$ realno zaporedje in $L \in \mathbb{R}$. Tedaj velja:**
**$$ L = \lim_{n \to \infty} a_n \quad \Leftrightarrow \quad \text{Vsako podzaporedje zaporedja } (a_n)_n \text{ ima podzaporedje, ki konvergira k } L. $$**
Kaj je stekaliče
**Če je stekališče, je limita nekega podzaporedja**
**Če je L limita je edino stekališče**
**Vsako omejeno zaporedje ima kakšno stekališče**
**Če je $s$ eidno stekališče omejenega zaporedja je s limita zaporedja**
Kaj pomeni če ima zaporedje stekališče v neskončnosti ali limito v neskončnosti
Kaj sta limes superior in limes inferior
**lim sup in inf sta največje in najmanjše stekaliče**
Cauchyjevo zaporedje
**zap je konvergentno natanko tedaj ko je cauchyjevo**
Kaj je vrsta *(zaporedje delnih vsot)*
Kdaj je vrsta konvergentna **(ko zaporedje delni hvsot konvergira)**
Kaj je vsota vrste *(limita zaporedja delnih vsot)*
Geometrijska vrsta
**Vsota geometrijske vrste**
Harmonična vrsta
**Vsota harmonične vrste oz. da ne konvergira**
Konvergenčni kriteriji vrst
**Cauchyjev kriterij**
**Vrsta je konvergentna potem zaporedje konvergira k nič**
**Primerjalni kriterij**
**$1/k^{2}$ konvergira**
**Kvocientni oz. d'Aelmbertov kriterij**
**Korenski oz. Cauchyjev kriterij**
Alternirajoča vrsta
Liebnizov konvergenčni kriterij
Absolutno konvergentne vrste
Pogojno konvergentne vrste - brezpogojna konvergenca, pogojna konvergenca
Riemannov sumacijski izrek





### Podmnožice v evklidskem prostoru

Množica je **navzgor** omejena če velja, da obstaja število tako, da je večje od vsakega elementa v množici.

$$\exists A\;\forall a : A>a $$

Temu številu pravimo zgornja meja. Množica ima lahko več zgornjih mej. Najmanjša zgornja meja se imenuje **supremum**.
Če v množici obstaja največji element se imenuje **maksimum**.

Množica je **omejena** če je omejena navzgor in navzdol hkrati.

**Okolica** točke $a$ je vsak odprti interval $(a-\varepsilon, a +\varepsilon)$.

Točka je **notranja** če velja da obstaja njena okolica, ki vsebuje samo elemente iz množice. 
Točka je **robna** če velja, da za vsako njeno okolico velja da vsebuje vsaj en element iz množice in en element izven množice. 
Točka je **zunanja** če obstaja okolica, ki vsebuje samo elemente izven množice.

Množica je **odprta**, natanko tedaj ko za vsak $a$ obstaja taka okolica $a$, ki je popolnoma vsebovana v množici.
*Vse njene točke so notranje* 


Naj bo $X$ podmnožica $\mathbb{R}$. Množica $A \subset X$ je **odprta v $X$** če obstaja odprta množica $B \subset \mathbb{R}$ tako da velja $A = B \cap X$ ^ad8952

Množica je **zaprta** če je komplement odprte. 
*Vsebuje vse svoje robne točke.*

Množica je **kompaktna** če je zaprta in omejena hkrati. ^2de28b
Oziroma če lahko iz vsakega zaporedja točk vsaj 1 stekališče v množici.

Množica je **končna**, če ima končno število elementov.



Element $a$ je **stekališče množice** $A$ če velja da vsaka njena okolica vsebuje neskončno točk množice $A$.


***

Realno **zaporedje** je preslikava iz $\mathbb{N} \longrightarrow \mathbb{R}$. $(a_{n})_{n}$ kjer je $a_{n} = a(n)$. Lahko jih seštevamo, odštevamo, množimo in delimo.

Zapoerdje je **rekurzivno** s podanim prvim členom in formulo, s katero opisujemo naslednji element iz prejšnjega.

**Aritemtično zaporedje** je zaporedje s konstantno razliko med členi.

$$a_{n} = a_{n-1} + d = a_{1}+d(n-1)$$
$$S_{n} = \frac{n}{2} \cdot  (a_{1}+a_{n})$$

**Geometrično zaporedje** je zaporedje s konstantim koeficientom med členi.

$$a_{n} = a_{n-1} \cdot k = a_{1} \cdot k^{n-1}$$
$$S_{n} = \sum_{1}^{n} = a_{1} + a_{1}k + ... + a_{1}k^{n-1}$$
$$S_{n}k = k\sum_{1}^{n} = a_{1}k + a_{1}k^2 + ... + a_{1}k^{n}$$
$$...$$
$$S_{n} = a_{1}\frac{1-k^{n+1}}{1-k}$$
$$\sum_{1}^{\infty} = \frac{a_{1}}{k-1} ;\; |k |<1$$

Zaporedje je **omejeno navzgor**, če je množica $a_{n}$ omejena navzgor.

Množica ima **supremum** če za vsako manjše število obstaja element množice, večje od njega.

$$\sup A \Leftrightarrow \forall \varepsilon > 0 \;\exists a \in A \ni: a > \sup A - \varepsilon$$

Če ni omejeno je **neomejeno**.

**Naraščajoče zaporedje**: $a_{n+1} > a_{n}$ ; nenaraščajoče $\geq$

Zaporedje je **monotono** če je nepadajoče ali nenaraščajoče oz. strogo monotono če je naraščajoče ali padajoče $\forall n$.

Točka $t$ je **limita zaporedja** če za vsako njeno okolico velja da vsebuje vse elemente od nekega indeksa naprej.

$$ \forall \varepsilon \exists N \forall n\geq N : |a_{n}-L| < \varepsilon$$
$$\lim_{n \to \infty}a_{n}$$


>Konvergentno zaporedje v $\mathbb{R}$ ima natanko eno limito.  
>*Elementi ne morejo skakati iz okolico v okolico ker drugače niso vsi elementi v okolici ene od limit*

>Vsako konvergentno zaporedje v $\mathbb{R}$ je omejeno.
>*Izberemo okolico in vidimo da so vsi elementi naprej znotraj okolice, ostane pa končno število, obe sta omejeni.*

> Za konvergentni zaporedji velja da je vsota njunih limit enaka limiti vsote zaporedij. Enako za razliko, produkt in koeficient.
>*Lahko si izberemo tak $\varepsilon$ da je $|(a_n +b_n) - (A+B)| \leq \frac{\varepsilon}{2} + \frac{\varepsilon}{2} = e$*
>*Za produkt lahko razčlenimo izraz $|a_{n}b_{n} - AB|$ in ker vemo da je zaporedje ki ima limito omejeno lahko najdemo taka epsilona za vsako zaporedje da velja da sta oba manjša od nekega epsilona*
>*Za deljenje mora veljati $L_{2}\neq 0$ in dokazati $\lim_{n \to \infty} \frac{1}{b_{n}} = \frac{1}{L_{2}}$ nato uporabimo pravilo produkta*
>*Najprej damo v isti ulomek. Potem lahko $a_{n}$ omejimo z dejstvom da konvergira in trikotniškim pravilom, nato pa izberemo delto tako da velja da je celoten ulomek manjši od $\varepsilon$.*

>Če je zaporedje montono ima limito enako $\sup a_{n}$ če pada pa $\inf a_{n}$
>*Predpostavimo da je limita neko število manjše od sup. Vzamemo epsilon $a_{n}-L$ za nek $n$. Ker je $a_{n+1}$ večji od $a_{n}$ ne bo več noter, torej dobimo protislovje*


> Če je zaporedje monotono in omejeno, je konvergentno
> *$\sup - \varepsilon$ vsebuje vsaj en $a_n$, od kjer velja da vsebuje neskončno zaradi monotonosti.*


Bernoullijeva neenakost

$$\forall n \in \mathbb{N}, \;\forall \alpha \leq 1 : (1-\alpha)^{n} \geq 1 -\alpha n$$


Zaporedje $a_{n} := (1+ \frac{1}{n})^{n}$ je konvergentno.

**Podzaporedje** zaporedja $a_{n}$ je zaporedje $a_{n'}$, kjer je $n' : \mathbb{N} \rightarrow \mathbb{N}$ neka funkcija.

> Če je $L$ limita $a_{n}$ je $L$ limita vsakega podzaporedja.
> *Ko imamo podzaporedje velja da obstaja tak $K$ ki je večji ali enak $N$ torej so vsi členi podzaporedja tudi v okolici.*

Točka je **stekališče** zaporedja če v vsaki njeni okolici obstaja neskončno členov zaporedja *(oz. če je stekališče množice členov zaporedja, kot podmnožica metričnega prostora.)*

> Točka je stekališče zaporedja natanko tedaj ko je točka limita nekega njegovega podzaporedja
> *V levo smer imp. po definiciji limite, v desno smer lahko konstruriramo podzaporedje da vzamemo $a_{n_{k}}$ da velja da je v $L- \frac{1}{k}$*

> Če obstaja limita zaporedja je to edino stekališče zaporedja.
> *Po prejšnjem izreku da je limita zaporedja limita vsakega podzaporedja, stekališče zaporedja pa je limita podzaporedja*

> Vsako omejeno zaporedje v realnih številih ima kakšno stekališče v realnih številih.
> *Lahko razpolavljamo interval, kjer ima vsak neskončno členov, nato skonstruriramo podzaporedje tako da vzamemo element iz vsakega zaporedja, ta konvergira - imamo stekališče.*

> Če ima zaporedje natanko eno stekališče in je omejeno je to limita zaporedja.
> *Če definiramo podzaporedje zunaj okolice stekališča, lahko ker vemo da je omejeno najdemo drugo stekališče ker je v protislovju z predpostavko*

Pravimo da ima zaporedje **stekališče v $\infty$** če za vsak interval $(M, \infty)$ velja da vsebuje neskončno elementov.

Pravimo da ima zaporedje **limito v $\infty$** če vsak interval $(M, \infty)$ vsebuje neskončno elementov od nekega indeksa naprej.

**Limes superior** $\lim \sup$ je vrednost proti kateri gre supremum zaporedja.
**Limes inferior** $\lim \inf$ je vrednost proti kateri gre infimum zaporedja.
> Če je zaporedje navzgor oz. navzdol neomejeno sta ti vrednosti $\infty$ oz. $-\infty$.

> Lim sup in lim inf vedno obstajata.

> $\lim \sup$ oz. $\lim \inf$ je največje oz. najmanjše stekališče zaporedja $a_{n}$

**Zaporedjeje** **Cauchyjevo** če za vsako še tako majhno število, za vse pare členov velja da je njuna razlika manjša, za vse pare od nekega indeksa dalje. 



> Konvergentno zaporedje je natannko tedaj ko je Cauchyjevo


**Vrsta konvergira** če je konvergentno zaporedje delnih vsot. Taki limiti pravimo **vsota vrste**.

$$\lim_{n \to \infty}s_{n} = \sum_{1}^{\infty}a_{k}$$



**Geometrijska vrsta** je vrsta oblike

$$\sum_{1}^{\infty}k^j$$
$$S_{n} = \sum_{1}^{n} = 1 + k + ... + k^{n}$$
$$S_{n}k = k\sum_{1}^{n} = a_{1}k + a_{1}k^2 + ... + a_{1}k^{n+1}$$
$$...$$
$$S_{n} = \frac{1-k^{n+1}}{1-k}$$
$$\sum_{1}^{\infty} = \frac{1}{k-1} ;\; |k |<1$$

> Geomterijska vrsta je konvergentna če je $k \in (-1,1)$ konvergira pa k $\frac{1}{k-1}$.

**Hamonična vrsta** je vrsta oblike

$$\sum_{1}^{\infty} \frac{1}{j}$$

vemo da zaporedje $\frac{1}{n}$ konvergira k nič, a ta vrsta divergira.

> Vrsta je konvergentna natanko tedaj, ko je Cauchyjeva.
>$$\left| \sum_{n+1}^{m} a_{j}\right| < \varepsilon$$

>Če vrsta konvergira, zaporedje konvergira k 0.
>*$a_{n} = s_{n+1}-s_{n} \rightarrow s-s = 0$*







Vrsta je **absolutno konvergentna** če je 

$$\sum_{1}^{\infty}|a_{n}| < \infty$$

> Če je vrsta absolutno konvergentna je konvergentna.
> *Cauchyjev pogoj ... $|s_{m}-s_{n}| = |\sum_{n+1}^{m}a_{j}| \leq \sum_{n+1 }^{m}|a_{j}|<\varepsilon$*

**Primerjalni kriterij** je pravilo ki pravi da če imamo dve vrsti z nenegativnimi členi in ena konvergira, potem konvergira vsaka vrsta manjša od nje. Vrsta, ki omejuje manjše vrste se imenuje **majoranta**.

> Če neka vrsta divergira potem divergira vsak vrsta večja od nje.

**Kvocientni / d'Alembertov kriterij** je pravilo, ki pravi da če je limita kvocienta sosednjih členov manjša od 1 potem vrsta absolutno konvergira, če je večja od 1 divergira, če pa je 1 pa ne vemo.
Izhaja iz geometrijske vrste kjer vemo da če je kvocient manjši od 1 potem vrsta konvergira.

$$D_{n} = \left|\frac{a_{n+1}}{a_{n}} \right|$$

$$D \leq k < 1$$

**Korenski / Cauchyjev kriterij** je pravilo, ki pravi da če je limita n-tega korena n-tega člena manjša od 1 potem vrsta konvergira, če je večja od 1 divergira, če je 1 pa ne vemo.

$$C_{n} = \sqrt[n]{|a_{n}|}$$

Spet izhaja iz geomtrijske vrste kjer je geometrijska vrsta majoranta. 

$$\sqrt[n]{|a_{n}|} \leq k < 1 \Rightarrow |a_{n}| \leq k^{n} < 1$$

Vrsta je **alternirajoča** če za vse $n$ velja da je predznak prejšnjega člena drugačen trenutnemu.

**Leibnizov konvergenčni kriterij** trdi da če zaporedje konvergira k nič z desne potem konvergira vrsta $$\sum_{1 }^{\infty} (-1)^{j}a_{j}$$

> Ob tem velja da je $|s - s_{n}| \leq a_{n+1}$

Vrsta je **brezpogojno konvergentna**, če za vsako permutacijo indeksov konvergira.

Vrsta je **pogojno konvergentna** če je konvergentna, a ne brezpogojno.

**Funkcije** so predpis, ki slikajo iz ene množice v drugo. 

Funkcija mora biti definirana za celotno svoje defincijsko območje.

**Praslika množice $B$** pod funkcijo $f$, označena z$f^{-1}(B)$, je množica vseh elementov $x$ v domeni $f$ za katere velja  $f(x) \in  B$

$$f^{−1}(B)=\{x \in X ;\; f(x) \in B\}$$

**Praslika posameznega elementa**: Če imamo posamezen element $y$ in množico $B = \{ y \}$, potem je praslika $f^{-1}(\{ y \})$ množica vseh $x$, za katere velja $f(x) = y$. Če je $f$ injektivna, bo ta množica vsebovala največ en element, in če $f$ ima inverzno funkcijo, bo $f^{-1}(\{ y \}) = \{ f^{-1}(y) \}$.

**Zožitev funkcije** je funkcija ki slika iz podmnožice definicijskega območja.

**Kompozitum** je slikanje preko ene funckije nato pa slikanje pridobljene vrednosti čez še eno funkcijo.

Funkcija je **injektivna** če vsakemu elementu v zalogi vrednosti pripada en element v definicijskem območju.

$$f(x) = f(y) \Rightarrow x = y$$

Funkcija je **surjektivna** ko velja da imajo vse vrednosti iz zaloge vrednosti svojo prasliko.

$$Z_{f} = B$$

Funkcija je **bijektivna** natanko tedaj ko za vsak element v $B$ obstaja natanko en element v $A$, ki se preslika vanj.

Če je funkcija bijektivna lahko definiramo njen **inverz** kot funkcijo ki slika iz $B$ v $A$ : $f(x) \mapsto x$.
Velja da je $f^{-1} \circ f = \text{id}_{A}$ in $f \circ f^{-1} = \text{id}_{B}$

Funkcije lahko seštevamo, odštevamo, množimo, delimo med sabo.

Premiki oz. translacije

$$(\tau_{a}f)(x) :=f(x-a)$$
$$(\tau^{a}f)(x) :=f(x)+a$$
$$(\delta_{t}f)(x) :=f\left(\frac{x}{t}\right)$$
$$(\delta^{t}f)(x) :=t \cdot f(x)$$

Zrcaljenje

$$(\delta^{-1}f)(x) \text{ ali } (\delta_{-1}f)(x)$$

Funkcija ima **limito v točki $a$**, ko se $x$ približuje $x_{a}$, če velja, da za vsako okolico $a$, velja da obstaja okolica $x_{a}$ taka da če je $x$ v okolici $x_{a}$ a ne enak $x_{a}$ potem vemo da je $f(x)$ v okolici $a$;

$$\forall \varepsilon > 0 \; \exists \delta>0 \forall x \in D_{f} : 0<|x-x_{a}|<\delta \Rightarrow |f(x)-f(a)|<\varepsilon$$

Leva limita:

$$\forall \varepsilon \; \exists \delta \;\forall x \in D_{f} : 0<x_{a}-x <\delta \Rightarrow |f(x)-f(a)| < \varepsilon $$

$$\lim_{x \to a^{-}}f(x)$$

Desna limita

$$\forall \varepsilon \; \exists \delta \;\forall x \in D_{f} : 0<x- x_{a} <\delta \Rightarrow |f(x)-f(a)| < \varepsilon $$

$$\lim_{x \to a^{+}}f(x)$$


> Funkcija ima limito v točki tudi kadar je desna limita v točki $a$ enaka levi limiti $a$.

Če obstajata leva in desna limita a nista enaki potem ima funkcija tam **skok**.

Funkcija je **zvezna v točki $a$** če velja da za vsako okolico $a$ obstaja okolica $x_{a}$ tako da za vsak $x$ velja da če vemo da je v okolici $x_{a}$ vemo da je $f(x)$ v okolici $a$.

$$\forall \varepsilon > 0 \; \exists \delta>0 \forall x \in D_{f} : |x-x_{a}|<\delta \Rightarrow |f(x)-f(a)|<\varepsilon$$

Recimo da obstaja funkcija, ki je zvezna povsod razen v $a \in D_{f}$. Če v tej točki obstaja limita lahko definiramo funkcijo odsekovno tako da ob $x=a$ rečemo da je $f(a) = \lim_{x \to a}f(x)$, čemur pravimo **zvezna raširitev funkcije**.

Funkcija je **odsekoma zvezna** če velja da je zvezna povsod na $D_{f}$ razen na končno mnogih točkah v katerih ima skok.

> Če je limita $h$ in $g$ v točki $a$ enaka $L$ in velja da je $h \leq f \leq g$ potem je limita $f$ v točki $a$ enaka $L$.

> Funckija naj bo definirana povsod razen v $a$. Za vsako zaporedje $x_{n}$, ki konvergira k $a$ , $f(x_{n})$ konvergira k $L$, natanko tedaj ko je limita funkcije $f$ ko gre $x$ k $a$ enaka $L$.
>
>$$ L = \lim_{x \to a}f(x) \Leftrightarrow (\forall x_{n} : x_{n} \rightarrow a \Rightarrow f(x_{n}) \rightarrow L)$$

> Funkcija je zvezna v $a$ natanko tedaj, ko je v $a$ zvezna po zaporedjih.

>Vsaka vsota. razlika, produkt, kvocient zvzenih funkcij je spet zvezna funkcija.

> Vsi polinomi in racionalne funkcije so zvezne na scojih definicijskih območjih.
> *Iz prejšnje trditve kjer hkrati vemo da je identiteta in konstante zvezne funkcije.*

>Če sta $f$ in $g$ obe zvezni potem je $g \circ f$ zvezna funkcija.

Vsaka **elementarna funkcija** je zvezna na svojem definicijskem območju.

[[#^ad8952|Odprta množica v množici]]

> Naj bo $W \subset D \subset \mathbb{R}$. Velja da je $W$ odprta v $D$ natanko tedaj, ko velja da za vsak element v $W$ obstaja taka okolica da je presek okolice in množice $D$ prava podmnožica $W$.

>Velja tudi da, ko je $D$ odprta in $W \subset D$, je $W$ odprta v $D$ natanko tedaj ko je $W$ odprta v $\mathbb{R}$

>$f$ je zvezna natanko tedaj če za vsako odprto množico $V$ velja da je $f^{-1}(V)$ spet odprta množica v $D$. 


[[#^2de28b|Kompaktna množica]]

Tipičen predstavnik kompaktne množice je **zaprt interval**.

> Naj bo $D$ kompaktna in $f: D \rightarrow \mathbb{R}$ zvezna. Takrat velja da je $f$ omejena in doseže minimum in maksimum.

> Naj bo $f$ definirana na zaprtem intervalu $[a,b]$ zvezna in $f(a)f(b) < 0$. Tedaj velja da obstaja tako število $\xi$ na $(a,b)$ tako da velja $f(\xi ) = 0$

> Če je funkcija definirana na zaprtem intervalu zvezna, na njem doseže minimum, maksimum in vse vrednosti vmes.

Če za zvezno funkcijo velja, da izbran delta deluje za vse vrednosti $x$ ob izbranem $\varepsilon$ potem pravimo da je funkcija enakomerno zvezna.

$$\forall \varepsilon >0 \; \exists \delta > 0\;\forall x' \in D \;  \ni: \forall x \in D\; \;|x-x'|<\delta \Rightarrow |f(x)-f(x')|< \varepsilon$$

> Če je množica kompaktna velja da je funkcija zvezna natanko tedaj, ko je enakomerno zvezna.

