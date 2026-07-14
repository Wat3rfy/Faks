**Kolobar** je trojica $(R, +, \cdot)$, za katero velja:

1.  **$(R, +)$ je Abelova grupa:**
    *   Asociativnost: $(a+b)+c = a+(b+c)$
    *   Komutativnost: $a+b = b+a$
    *   Nevtralni element: $a+0 = a$
    *   Inverz: $a+(-a) = 0$
2.  **Množenje je asociativno:** $(a \cdot b) \cdot c = a \cdot (b \cdot c)$
3.  **Distributivnost:**
    *   $a \cdot (b + c) = a \cdot b + a \cdot c$
    *   $(a + b) \cdot c = a \cdot c + b \cdot c$

Če je kolobar neasociativen oz. je grupoid za množenje, rečemo da je **neasociativen kolobar**.

Če imamo za množenje monoid imamo **kolobar z enoto** oz. **unitalni kolobar**

Če imamo za množenje grupo za neničelne elemente imamo **kolobar z deljenjem**.

Kolobarju z deljenjem pravimo tudi **obseg**, če je množenje v obsegu komutativno pa postane **polje**. 

V nadaljevanju uporabljamo izraz obseg za polje.

Ko rečemo kolobar govorimo o asociativnem unitalnem kolobarju, dodatno specificiramo če je komutativen ali pa če ima deljenje neničelnih elementov.

Primeri kolobarjev so npr.:

**Cela števila** - kom. kolobar

**Soda števila** - podkolobar celih, kom. kolobar brez enote.

**Racionalna, realna, kompleksna števila** - kom. kolobar z deljenjem 

**Polinomi nad $\mathbb{R}$** - kom. kolobar

**Polinomi nad $K$** - ohranja lastnosti $K$ razen deljenja, še več, polinomi na $K$ in množenje nikoli ne morejo biti grupa za vse neničelne elemente.

Vektorji v $\mathbb{R}^{3}$ in $\mathbb{R}^{7}$ - neasociativni kolobar

Matrike $n \times n$ nad $K$ - ohranjajo lastnosti $K$ razen inverzov, kjer velja da obstaja inverz če je matrika obrnljiva oz. determinanta ni nič.

Zvezne funkcije $f: \mathbb{R} \rightarrow {K}$ - lastnosti se podedujejo od $K$ razen obstoj inverza, kjer velja da za element $f$ obstaja inverz če nima ničel.

Podmnožice polj. množice nad presekom in unijo - $(2^{X},\cup, \cap )$ - **to ni kolobar!**
Strukturo popravimo s simetrično vsoto 

$$A \Delta B := (A\backslash B) \cup (B \backslash A)$$

$$A \Delta \emptyset =A$$
$$A \Delta A = \emptyset$$

**Torej bo $(2^{X}, \Delta, \cap)$ kom. kolobar.**

Temu pravimo **Booleov kolobar**.

Poznamo tudi $\mathbb{Z}_{n}$ - kom. kolobar ki ima deljenje natanko tedaj ko velja da je $n \in \mathbb{P}$.

> Naj velja $a,b \in K$. Potem veljajo
> - $a0 = 0a = 0$
> - $a(-b) = (-a)b = -(ab)$
> - $(-a)(-b) = ab$

Naj bo $(K, \circ)$ kolobar. **Podkolobar** $R$ kolobarja $K$ je podmnožica $R$ tako da je $(R, \circ)$ kolobar. 

Npr. 
- $n \mathbb{Z}$ je podkolobar $\mathbb{Z}$. *Vidimo lahko da ne zahtevamo da podkolobar vsebuje identiteto za množenje.*
- Velja $\mathbb{Z} \subset  \mathbb{Q} \subset  \mathbb{R} \subset  \mathbb{C}$
- Množica zgornje trikotnih matrik je podkolobar množice vseh matrik na $K$.


$R$ je podkolobar $K$ natanko tedaj ko velja 
- $R \neq \emptyset$, 
- $\forall a,b \in R : ab \in R$
- $\forall a,b \in R : a-b \in R$

<br>

Imamo kolobar $K$. Če obstajata $a,b \neq 0$ da velja $ab = 0$ potem sta $a,b$ **delitelja $0$**.


Če **kom. kolobar** $K$ ne vsebuje deliteljev niča mu pravimo **cel kolobar**. *Motivacija potrebe po kom. kolobarju je poenostavitev nadaljnih izrekov o razcepih, prafaktorjih,...*

Če ima element $a$ v kolobarju inverz pravimo da je **obrnljiv**.

Obrnljiv element ne more biti delitelj niča.

Če so vsi neničelni elementi v kolobarju obrnljivi pravimo da je **kolobar z deljenjem**.

$$ $$

> **Pravilo krajšanja**
> Naj bo $K$ cel kolobar $\Leftrightarrow$ $\forall a \in D \neq 0$ velja $ab = cb \Rightarrow a = c$
> 
> V splošnem velja da lahko krajšamo element ki ni delitelj niča.
> 
> Vsak obrnljiv element lahko krajšamo saj obstaja $a^{-1}$.

<br>



> Vsak končen cel kolobar je obseg.
> 
> >[!|dokaz]+ Dokaz:
> >
> > Naj bo $D$ končen cel kolobar in $D^*$ množica neničelnih elementov v $D$. Pokazati moramo, da ima vsak element v $D^*$ inverz. 
> > 
> > Za vsak $a \in D^*$ lahko definiramo preslikavo $\lambda_a : D^* \to D^*$ s predpisom $\lambda_a(d) = ad$. Ta preslikava je smiselna, ker če sta $a \neq 0$ in $d \neq 0$, potem je $ad \neq 0$ (saj v celem kolobarju po definiciji ni deliteljev niča). 
> > 
> > Preslikava $\lambda_a$ je injektivna, saj za $d_1, d_2 \in D^*$ velja:
> > $$ad_1 = \lambda_a(d_1) = \lambda_a(d_2) = ad_2$$
> > kar implicira $d_1 = d_2$ zaradi možnosti krajšanja z leve (v celih kolobarjih lahko neničelne elemente krajšamo). 
> > 
> > Ker je $D^*$ končna množica, mora biti preslikava, ki je injektivna, hkrati tudi surjektivna (na). Zato mora za nek $d \in D^*$ veljati $\lambda_a(d) = ad = 1$. 
> > 
> > Torej ima element $a$ levi inverz. Ker je $D$ komutativen, mora biti ta isti $d$ tudi desni inverz za $a$. Posledično je $D$ polje. $\square$

***

**Karakteristika kolobarja $K$** oz. **$\text{char }K$** je najmanjše število $n \neq 0$ tako da $\forall r \in K$ velja $nr = 0$. *Množenje $nr$ predstavlja večkratno seštevanje, ne multiplikativne operacije. To je poudarjeno ker je pri deliteljih niča dejanska mult. operacija in ne večkratno seštevanje. Dejansko ne nastopi noben problem pri analizi, tudi če ne vemo tega, a distinkcija še vedno obstaja, velja pa da ob večkratnem seštevanju  ne vedno velja da ima ta element inverz ker ponavadi $n$ ni del grupe oz. kolobarja ampak je zunanja operacija npr. v $\mathbb{Z}^{2 \times 2}_{2}$ to da je $2X = 0$ ne pomeni da je $X=0$ ker v takem kolobarju $2$ nima inverza in ne moramo krajšati, velja $X + X = 0$ torej je $X$ vsaka matrika. Ampak v tem primeru je očitno da $2$ ni v kolobarju, še več, ne obstaja kolobar kjer bi veljalo da je $xy$ kot večkratno seštevanje lahko enako $0$ hkrati pa bi veljalo da je $xy$ kot dejanska operacija množenja neničelna. Edini poskus demonstracije zahteva da je $n$ nek element zunaj kolobarja npr. tudi $3x=0$ v $Z_{2}[x]$, kjer bi lahko rekli da je $x$ delitelj niča (ker velja $3x=0$, čeprav mislimo $3x=x+x+x$ kar ne more biti 0) ali kakorkoli ne deluje, saj se izkaže da je $3$ v resnici $0$ torej ni dejansko težave.*

> *Velja da v kolobarju večkratno seštevanje postane mul. operacija natanko tedaj če imamo enoto za množenje, saj velja da lahko zapišemo $a \cdot b = a \cdot (1+...+1) = a+...+a = ab$.*

Za vsak $p \in \mathbb{P}$ velja da ima $\mathbb{Z}_{p}$ karakteristiko $p$.

> Če smo v kolobarju in ima $1$ stopnjo $n$ potem je karakteristika kolobarja enaka $n$.

> Karakteristika celega kolobarja je $p \in \mathbb{P}$ ali pa $0$.
> >[!|dokaz]+ Dokaz:
> > 
> > Naj bo $D$ cel kolobar in predpostavimo, da je karakteristika $D$ enaka $n$, pri čemer je $n \neq 0$. 
> > 
> > Če $n$ ni praštevilo, potem je sestavljeno število $n = ab$ kjer velja $1 < a < n$ in $1 < b < n$. Vemo da je $n \cdot 1 = 0$.
> > 
> > Ker velja:
> > $$0 = n \cdot 1 = (ab) \cdot 1 = (a \cdot 1)(b \cdot 1)$$
> > in ker v celem kolobarju $D$ **ni deliteljev niča**, mora biti bodisi $a \cdot 1 = 0$ bodisi $b \cdot 1 = 0$.
> > 
> > To pomeni, da bi bila karakteristika kolobarja $D$ manjša ali enaka $a$ oziroma $b$. Ker pa sta $a$ in $b$ oba strogo manjša od $n$ ($a < n$ in $b < n$), to vodi v **protislovje** z definicijo, da je $n$ *najmanjše* pozitivno celo število, za katero velja $n \cdot 1 = 0$.
> > 
> > Zato $n$ ne more biti sestavljeno število in mora biti praštevilo. $\square$


***

**Homomorfizmi**

Imamo kolobarja $K, L$. Pravimo da je $\varphi: K \rightarrow L$ **homomorfizem** kolobarjev natanko tedaj ko za vask $x,y \in K$ velja

$$\varphi(x+y) = f(x)+ f(y)$$
$$\varphi(xy) = f(x)f(y)$$

> $f(0) = 0$*, saj velja $f(0) = f(0)+f(0) = 0$*

> Velja da je $f(-a) = -f(a)$. *$f(0) = f(a-a) = f(a)+f(-a) = 0$*

> Če je $K$ kom. kolobar potem je $f(K)$ kom. kolobar.

<br>

V splošnem ne zahtevamo da je $f(1) = 1$. Če to velja imamo **unitalen homomorfizem.**

> Če imamo $f: K \rightarrow L$ in je $f$ surjekcija potem velja da je $f$ unitalen hm.
> >[!|dokaz]+ Dokaz:
> > Naj bo $k \in K$, vemo da obstaja $l$ da velja $f(k) = l$, velja
> > 
> > $$f(k) = f(k \cdot 1) = f(k) \cdot f(1) = k \cdot f(1) = r$$
> > 
> > torej mora biti $f(1_{K}) = 1_{L}$

> Če je homomorfizem unitalen in ja $a$ obrnljiv potem je $f(a)$ obrnljiv.
> >[!|dokaz]+ Dokaz:
> > $f(aa^{-1}) = f(a)f(a^{-1}) = 1$

***

Množici vseh elementov iz $K$ ki jih $\varphi$ slika v $0$ pravimo **jedro $\varphi$** označeno tudi z $\varphi^{-1}(0_{L})$.

$$\text{Ker }\varphi = \{ k \in K \,;\; \varphi(k) = 0_{L}\}$$

> Jedro je podkolobar $K$, saj velja
> 
> $$x,y \in \text{Ker }\varphi \Rightarrow \varphi(xy) = \varphi(x)\varphi(y) = 0 \Rightarrow xy \in \text{Ker }\varphi$$
> 
> $$ $$
> 
> $$x,y \in \text{Ker } \varphi \Rightarrow \varphi(x-y) = \varphi(x)-\varphi(y) = 0$$
> $$\Rightarrow \varphi(x-y)=0 \Rightarrow x-y \in \text{Ker }\varphi$$

<br>


Množici vseh elementov, ki jih lahko dobimo preko $\varphi : K \rightarrow L$ rečemo **slika $\varphi$** in označimo kot

$$\text{Im } \varphi = \{ l \in L \;;\; \exists k \in K : \varphi(k) = l \}$$


> Velja da je slika $\varphi$ podkolobar v $L$, saj velja
> 
> $$x,y \in \text{Im } \varphi \Rightarrow \exists a,b \in K : f(a-b) = x-y \Rightarrow $$ $$\Rightarrow f(a-b) \in \text{Im }\varphi \Rightarrow x-y \in \text{Im }\varphi$$
> $$ $$
> $$x,y \in \text{Im }\varphi \Rightarrow \exists a,b : f(ab) = xy \Rightarrow f(ab) \in \text{Im }\varphi \Rightarrow xy \in  \text{Im }\varphi$$

***

Če je $\text{Im }\varphi = L$ je $f$ surjektivna - *epimorfizem*.

Če je homomorfizem bijektiven mu pravimo **izomorfizem**.

***

**Primer:** Identiteta je homomorfizem. Naj bo $L \subset K$ in $\varphi: L \rightarrow K$ kjer je $\varphi(x) = x$.

**Primer:** Naj bo homomorfizem $\varphi :\mathbb{Z} \rightarrow \mathbb{Z}_{n}$ definiran kot $\varphi(x) = x \mod n$ kjer velja da je njegovo jedro enako $n \mathbb{Z}$.


**Primer:** Naj bo $C[a,b]$ množica vseh zvezih funckij na $[a,b]$. Definiramo lahko homomorfizem iz $C[a,b] \rightarrow \mathbb{R}$ za nek $\alpha \in [a,b]$

$$\varphi_{\alpha} = f(\alpha)$$

Takemu homomorfizmu pravimo **evaluacijski homomorfizmi.**

**Primer:** Konjugacija je hm. iz $\mathbb{C}$ v $\mathbb{C}$.

**Primer:** V kolobarju s karakteristiko dva je kvadriranje homomorfizem. Velja da je $\text{char} K = 2$. Torej bo $(a+b)^{2} = a^{2}+2ab+b^{2} = a^{2}+b^{2}$, množenje je trivialno. Torej imamo hm.

> Velja da v kolobarju s $\text{char } p$ velja da je $x \mapsto x^{p}$ hm.
> 
> >[!|dokaz]+ Dokaz:
> > 
> > $$(x+y)^{p}=\sum_{0}^{p}\binom{\,p\,}{\,k\,}x^{k}y^{p-k} = \binom{\,p\,}{\,0\,}x^{p}+...+ \binom{\,p\,}{\,p\,}y^{p}$$
> > 
> > v splošnem imamo člen
> > 
> > $$\frac{p!}{k!(p-k)!}$$
> > 
> > kjer se $p$ nima z ničemer z krajšat, torej mora biti enak $0$ kar pomeni da vse razen $\binom{\,p\,}{\,0\,}$ in $\binom{\,p\,}{\,p\,}$ postane $0$ torej je $(x+y)^{p} = x^{p}+y^{p}$. Za množenje je trivialno.

**Opomba:** Odvajanje ni primer hm.

> Naj bo $\phi: R \to S$ homomorfizem kolobarjev. Velja:
> 
> - Če je $R$ obseg in $\phi(R) \neq \{0\}$, potem je $\phi(R)$ obseg.


***

Za jedro velja **idelna lastnost**. To pomeni da če imamo element v jedru $a \in \text{Ker }f$ in element iz njegove nadmnožice $x \in K$ potem velja

$$xa \in \text{Ker }f$$
$$ax \in  \text{Ker }f$$

*Rečemo da jedro absorbira množenje.*

Podkolobarjem s to lastnostjo pravimo **ideali**.

Torej podkolobar $I \subset K$ je **ideal** natanko tedaj ko velja da $\forall r \in I$ in $\forall k \in K$ velja

$$kr \in I$$
$$rk \in I$$

torej če imamo element iz $I$ in element iz $K$ potem je njun produkt še vedno v $I$.

Torej je $rI \subset  I$ in $Ir \subset I$ za vse $r \in R$.

**Primer:** Velja da je $\{ f: \mathbb{R} \rightarrow \mathbb{R} \,;\; f(a) = 0\}$ je ideal v $\text{Fun}(\mathbb{R}, \mathbb{R})$. Ta množica je jedro $\varphi_{a}(f)$ - torej mora biti ideal.

>Vsak kolobar ima vsaj 2 ideala, to sta **trivialni ideal** in **polni ideal**. Tem pravimo **nepravi ideali**.

> Če sta $I$ in $J$ ideala v kolobarju $R$, potem je njun presek $I \cap J$ prav tako ideal v $R$.
> > [!|dokaz]+ Dokaz:
> > Najprej preverimo, ali je $I \cap J$ neprazna množica. Ker sta $I$ in $J$ ideala, vsebujeta ničelni element $0 \in R$, zato je $0 \in I \cap J$. 
> > 
> > Naj bosta $x, y \in I \cap J$ in $r \in R$. 
> > Ker sta $x$ in $y$ v $I$, njuna razlika $x - y$ prav tako pripada $I$ (ker je $I$ ideal). Ker sta $x$ in $y$ tudi v $J$, velja $x - y \in J$. Torej je $x - y \in I \cap J$.
> > 
> > Za množenje z elementom $r \in R$: ker je $x \in I \cap J$, sledi $x \in I$ in $x \in J$. Ker je $I$ ideal, velja $rx \in I$ in $xr \in I$. Prav tako, ker je $J$ ideal, velja $rx \in J$ in $xr \in J$. Od tod sledi, da sta $rx$ in $xr$ v $I \cap J$. 
> > 
> > Ker sta izpolnjena oba pogoja, je $I \cap J$ ideal v $R$.

> Če je $1$ v idealu je ideal $I = R$. *Velja $a \cdot 1 = a \Rightarrow a \in A \,;\; \forall a \in R$*

> Jedro vsakega homomorfizma kolobarjev $\phi : R \to S$ je ideal v $R$.
> 
> > [!|dokaz]+ Dokaz:
> > Iz teorije grup vemo, da je $\ker \phi$ aditivna podgrupa v $R$. Predpostavimo, da sta $r \in R$ in $a \in \ker \phi$. Pokazati moramo, da sta $ar$ in $ra$ v $\ker \phi$. Vendar velja:
> > $$\phi(ar) = \phi(a)\phi(r) = 0\phi(r) = 0$$
> > in
> > $$\phi(ra) = \phi(r)\phi(a) = \phi(r)0 = 0.$$

> Če je $a$ poljuben element v komutativnem kolobarju $R$ z enoto, potem je množica
> $$(a) = \{ar : r \in R\}$$
> ideal v $R$. 
> 
> Množica $(a)$ je zagotovo neprazna, saj sta $0 = a0$ in $a = a1$ oba v $(a)$. Vsota dveh elementov v $(a)$ je spet v $(a)$, saj velja $ar + ar' = a(r + r')$. Inverz elementa $ar$ je $-ar = a(-r) \in (a)$. Nazadnje, če pomnožimo element $ar \in (a)$ s poljubnim elementom $s \in R$, dobimo $s(ar) = a(sr)$. Zato $(a)$ zadošča definiciji ideala.

Če je $R$ **komutativen kolobar z enoto**, se ideal oblike $(a) = \{ar : r \in R\}$ imenuje **glavni ideal**.

> Element $a \in K$ je obrnljiv natanko tedaj, ko je $(a) = K$.
> 
> > [!|dokaz]+ Dokaz:
> > Najprej predpostavimo, da je $a$ obrnljiv. Potem v $K$ obstaja inverz $a^{-1}$, za katerega velja $a \cdot a^{-1} = 1$. Ker je $(a)$ ideal, ki vsebuje element $a$, mora vsebovati tudi produkt $a \cdot a^{-1} = 1$. Če ideal vsebuje enoto, potem vsebuje vse elemente kolobarja, zato velja $(a) = K$.
> > 
> > Za obratno smer predpostavimo, da velja $(a) = K$. Ker je $1 \in K$, mora biti tudi $1 \in (a)$. Po definiciji glavnega ideala so vsi njegovi elementi oblike $ax$ za neki $x \in K$. Sledi, da obstaja tak element $b \in K$, da velja $ab = 1$, kar po definiciji pomeni, da je $a$ obrnljiv.


> $K$ je obseg natanko tedaj, ko $K$ nima pravih idealov.
> 
> > [!|dokaz]+ Dokaz:
> > Najprej predpostavimo, da je $K$ obseg. Naj bo $I$ ideal v $K$. Če $I \neq \{0\}$, potem v njem obstaja neničeln element $a \in I$. Ker je $K$ obseg, ima element $a$ inverz $a^{-1} \in K$. Ker je $I$ ideal, mora biti v njem tudi produkt $a \cdot a^{-1} = 1$. Če ideal vsebuje enoto, potem sledi $I = K$. Torej sta edina ideala v $K$ le $\{0\}$ in $K$.
> > 
> > Za obratno smer predpostavimo, da sta edina ideala v $K$ le $\{0\}$ in $K$. Naj bo $a \in K$ poljuben neničeln element. Oglejmo si glavni ideal $(a) = \{ax \mid x \in K\}$. Ker $a \neq 0$ in $a \in (a)$, velja $(a) \neq \{0\}$. Ker po predpostavki $K$ nima pravih idealov, mora veljati $(a) = K$. To pomeni, da je $1 \in (a)$, zato obstaja tak element $b \in K$, da velja $ab = 1$. Ker ima vsak neničeln element v $K$ inverz, je $K$ obseg.



> Vsi ideali v $\mathbb{Z}$ so glavni.
> 
> > [!|dokaz]+ Dokaz:
> > Naj bo $I$ ideal v kolobarju celih števil $\mathbb{Z}$. Če je $I = \{0\}$, je $I$ glavni ideal, generiran z $0$, torej $I = (0)$. Če $I \neq \{0\}$, potem $I$ vsebuje vsaj eno neničelno celo število $a$. Ker je $I$ ideal, vsebuje tudi element $-a$. Eden od elementov $a$ ali $-a$ je pozitiven, zato $I$ vsebuje vsaj eno pozitivno celo število. Po principu dobre urejenosti obstaja najmanjše pozitivno celo število $n \in I$. Pokazali bomo, da je $I = (n)$. Ker je $n \in I$ in je $I$ ideal, velja $(n) \subseteq I$. Naj bo sedaj $x$ poljuben element iz $I$. Po izreku o deljenju z ostankom obstajata celi števili $q$ in $r$, da velja $x = nq + r$, kjer je $0 \leq r < n$. Od tod sledi $r = x - nq$. Ker sta $x$ in $nq$ v idealu $I$, je tudi $r \in I$. Ker je $n$ najmanjše pozitivno celo število v $I$ in velja $0 \leq r < n$, mora biti $r = 0$. To pomeni, da je $x = nq$, torej $x \in (n)$. Sledi $I \subseteq (n)$, iz česar zaključimo, da je $I = (n)$. Vsak ideal v $\mathbb{Z}$ je torej glavni.


> Če je $K$ obseg, potem so vsi ideali v $K[x]$ glavni.
> 
> > [!|dokaz]+ Dokaz:
> > Naj bo $I$ ideal v kolobarju polinomov $K[x]$. Če je $I = \{0\}$, je $I$ glavni ideal, generiran z ničelnim polinomom, torej $I = (0)$. 
> > 
> > Če $I \neq \{0\}$, potem v $I$ obstajajo neničelni polinomi. Naj bo $g(x) \in I$ neničeln polinom z najmanjšo stopnjo med vsemi neničelnimi polinomi v $I$. Pokazali bomo, da je $I = (g(x))$. Ker je $g(x) \in I$ in je $I$ ideal, velja $(g(x)) \subseteq I$. 
> > 
> > Naj bo sedaj $f(x)$ poljuben polinom iz $I$. Po izreku o deljenju polinomov z ostankom obstajata polinoma $q(x)$ in $r(x)$ iz $K[x]$, da velja $f(x) = g(x)q(x) + r(x)$, kjer je $r(x) = 0$ ali pa velja $\deg(r(x)) < \deg(g(x))$. Iz enačbe izrazimo ostanek $r(x) = f(x) - g(x)q(x)$. Ker sta $f(x)$ in $g(x)$ v idealu $I$, je tudi njuna kombinacija $r(x)$ v idealu $I$. 
> > 
> > Če bi veljalo $r(x) \neq 0$, bi bila stopnja polinoma $r(x)$ strogo manjša od stopnje polinoma $g(x)$, kar bi bilo v protislovju z izbiro $g(x)$ kot polinoma z najmanjšo stopnjo v $I$. Zato mora biti $r(x) = 0$, kar pomeni $f(x) = g(x)q(x)$. To dokazuje, da je $f(x) \in (g(x))$, oziroma $I \subseteq (g(x))$. 
> > 
> > Sledi $I = (g(x))$, kar pomeni, da je ideal $I$ glavni.


Kolobar v katerem so vsi ideali glavni imenujemo **glavnoidealni kolobar**.

<br>

Na $K$ vpeljemo relacijo $\sim$; $a \sim b$, če je $a - b \in I$. Relacija $\sim$ je ekvivalentna relacija.

> [!|dokaz]+ Dokaz:
> $a \sim a$, ker je $a - a = 0 \in I$.
> $a \sim b \Rightarrow b \sim a$, ker iz $a - b \in I$ sledi $b - a \in I$.
> $a \sim b, b \sim c \Rightarrow a \sim c$, ker iz $a - b \in I$ in $b - c \in I$ sledi $a - c \in I$.

Množico ekvivalentnih razredov označimo s $K/I$. Ekvivalenčni razred elementa $a \in K$ označimo z $[a]$ ali $a + I$. Ker $b \in [a]$ pomeni $b \sim a$ oziroma $b - a \in I$ (torej $b = a + x$ za nek $x \in I$), velja:

$$[a] = \{ a + x \mid x \in I \} = a + I$$

> Operaciji sta definirani kot
> $$(r+I)+(s+I) = (r+s)+I$$
> $$(r + I)(s + I) = rs + I.$$
> 
> > [!|dokaz]+ Dokaz:
> > Že vemo, da je $R/I$ Abelova grupa za seštevanje. 
> > 
> > Naj bosta $r + I$ in $s + I$ v $R/I$. Pokazati moramo, da je produkt $(r + I)(s + I) = rs + I$ neodvisen od izbire predstavnika.
> > 
> > To pomeni, če sta $r' \in r + I$ in $s' \in s + I$, potem mora biti $r's' \in rs + I$. Ker je $r' \in r + I$, obstaja element $a \in I$, tako da velja $r' = r + a$. Podobno obstaja $b \in I$, tako da velja $s' = s + b$. Opazimo, da je
> > $$r's' = (r + a)(s + b) = rs + as + rb + ab$$
> > in $as + rb + ab \in I$, ker je $I$ ideal; posledično velja $r's' \in rs + I$. Preverjanje asociativnosti za množenje in distributivnostnih zakonov pustimo za vajo.

Kolobar $R/I$ se imenuje faktorski ali **kvocientni kolobar**.

> Naj bo $I$ ideal v $R$. Preslikava $\psi : R \to R/I$, definirana s $\psi(r) = r + I$, je surjektiven homomorfizem kolobarjev iz $R$ na $R/I$ z jedrom $I$.
> 
> > [!|dokaz]+ Dokaz:
> > Zagotovo je $\psi : R \to R/I$ surjektiven homomorfizem Abelovih grup. Preostane nam pokazati, da $\psi$ deluje pravilno pri množenju v kolobarju. Naj bosta $r, s \in R$. Potem velja
> > $$\psi(r)\psi(s) = (r + I)(s + I) = rs + I = \psi(rs),$$

Tej preslikavi ponavadi rečemo **kanonični homorfizem** oz. **naravni homorfizem**.



![[Pasted image 20260415221959.png]]