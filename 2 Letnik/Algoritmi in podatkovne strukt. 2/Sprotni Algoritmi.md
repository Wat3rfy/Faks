


**Sproten algoritem** (online algorithm) ne prejme vseh podatkov naenkrat, ampak jih dobiva sproti (zaporedno).

Pri snovanju takih algoritmov imamo dve možnosti:

1. Lahko ustvarimo **verjetnostni (probabilistični) model**, kjer predpostavimo, da bo vhod porazdeljen po neki verjetnosti, ki jo model pričakuje.
    
2. Druga možnost je **brez kakršnihkoli predpostavk** o prihodnosti, kjer želimo minimizirati skupni strošek ali slabost odločitve za še tako neugoden (slab) vhod.
    

Učinkovitost te druge možnosti analiziramo tako, da primerjamo našo sprotno rešitev z optimalno rešitvijo, ki bi jo dobili, če bi bil celoten vhod znan vnaprej (offline). Vzamemo najslabše možno razmerje med njima in ga poskušamo čim bolj zmanjšati. Temu pravimo **konkurenčno razmerje** (competitive ratio).

Prvi problem je problem dvigala kjer se odločamo ali bomo vzeli stopnice ali dvigalo do $k$-tega nadstropja
- vemo da dvigalo rabi $m$ minut da pride do nas in $1$ minuto do $k$-tega nadstoprja torej bo celoten čas enak $m+1$
- vemo da lahko prehodimo 1 nadstropje na minuto torej bo skupen čas $k$ minut
- mi ne poznamo $m$-ja, hočemo pa da je naša rešitev vsaj približno tako dobra kot od nekoga ki pozna $m$.

Oseba ki pozna $m$ bi v primeru da je $m < k$ počakala na dvigalo, če je $m \geq k$ pa lahko vzame stopnice torej lahko v odvisnosti $m$ oz. minut da pride dvigalo do nas zapišemo celoten čas kot

$$t(m) = \begin{cases}
m+1 & \,;\;m < k \;\text{ vzamemo dvigalo}\\ 
k &\,;\; m \geq k \;\text{ vzamemo stopnice}
\end{cases}$$

Za analizo konkurenčnega razmerja potrebujemo $\mathcal{U}$ ki vsebuje vse možne vhode, naj bo $I \in \mathcal{U}$ nek vhod. Če sprotni algoritem $A$ dobi rešitev $A(I)$ in je rešitev optimalnega algoritma $F$ ki pozna vhod vnaprej $F(I)$ potem je konkurenčno razmerje enako

$$\max \left\{ \frac{A(I)}{F(I)} \,;\; I \in \mathcal{U} \right\}  $$

Če je to razmerje enako $c$ potem praivmo da je $c$-konkurnečni. Spodnja meja je $1$, torej hočemo čim manjšo vrednost.

Naj bo $A$ algoritem ki vedno vzame stopnice - torej $k$ minut. Naj bo $0 \leq m \leq B-1$, kjer je $m$ število minut ki jih počakamo da dvigalo pride, konkurenčno razmerje bo torej

$$\max \{ \frac{k}{1},\frac{k}{2},...,\frac{k}{k-1},\frac{k}{k},...,\frac{k}{k} \}$$

kar lahko zapišemo kot

$$t(m) = \begin{cases}
m+1 & \,;\;m < k \;\text{ vzamemo dvigalo}\\ 
k &\,;\; m \geq k \;\text{ vzamemo stopnice}
\end{cases}$$
$$\max \{ \frac{k}{t(m)} \,;\; m \in {0,...,B-1} \}$$

torej bo konkurenčno razmerje enako $\frac{k}{1} = k$. 

Druga možnost je če vsakič vzamemo dvigalo, kar lahko zapišemo kot

$$t(m) = \begin{cases}
m+1 & \,;\;m < k \;\text{ vzamemo dvigalo}\\ 
k &\,;\; m \geq k \;\text{ vzamemo stopnice}
\end{cases}$$
$$\max \{ \frac{m+1}{t(m)} \,;\; m \in {0,...,B-1} \}$$
$$\max \{ \frac{1}{1},\frac{2}{2},...,\frac{k-1}{k-1},\frac{k}{k},\frac{k+1}{k},...,\frac{B}{k} \} = \frac{B}{k}$$

Operiramo predpostavko da mi poznamo $k$, torej je $k$ konstanta, mi pa ne vemo $B$-ja torej je optimalnost odvisna od $B$.

Imamo razmerje $k$ in razmerje $\frac{B}{k}$. Ker je razmerje maksimum neke množice bi bilo optimalno razmerje tisto ki ne more več rasti, v našem primeru je to $k$ saj je $k$ določen maksimum za celotno množico, medtem ko $B/k$ lahko raste če $B$ raste. *Če nimamo predpostavke da je $k$ konstanta in da jo poznamo vnaprej potem ne moremo trditi kateri od teh je optimalen saj bi lahko B bil konstanten in $k$ tisti ki raste.*

Ker je vzemanje stopnic relativno ekstremna opcija lahko pogledamo kaj se zgodi če počakamo $k$ minut na dvigalo nato pa gremo po stopnicah.

Če čakamo $m$ minut na dvigalo in bo $m < k$ potem bo čas enak $m + 1$, drugače bo enak $2k$.

$$\max \{ \frac{1}{1}, \frac{2}{2},..., \frac{k-1}{k-1}, \frac{k}{k}, \frac{2k}{k},...,\frac{2k}{k} \}$$
$$\max \{ ...\} = 2$$

V tem primeru je konkurenčno razmerje enako $2$ in je neodvisno od $k$-ja, to je primer algoritma ki bi ga lahko uoprabili tudi če ne vemo vnaprej koliko nadstropij je oz. $k$-ja.

**Problem sprotnega predpomnenja**

Če imamo sprotni algoritem LIFO, kjer izvržemo najnovejši blok, potem lahko za najslabši primer vzamemo zaporedje $1,2,3,...,k,k+1,k,k+1,k,k+1,...$ kjer bomo imeli vse skupaj $n$ zgrešitev, če je zaporedje dolog $n$, optimalni offline algoritem bo imel $k$ zgrešitev torej *prvih $k$ elementov* torej bo konkurenčno razmerje $\frac{n}{k}$.

FIFO in LRU, kjer sta to algoritma kjer izvržemo najstarejši blok in kjer izvržemo najstarejše uporabljeni blok imata konkurenčno razmerje v $\Theta(k).$

Če pogledamo LRU algoritem, lahko zaporedje zahtevkov razdelimo na dele kjer vsak del vsebuje $k$ različnih zahtevkov. Optimalni algoritem v tem primeru dobi eno zgrešitev za vsak del. Naš algoritem po drugi strani za vsak blok dobi največ $k$ zgrešitev, saj po $k$ zgrešitvah za isti del velja da imamo vse zahtevke v predpomnilniku, torej naš algoritem porabi $k$ zgrešitev na en del, optimalni pa enega, torej bo konkurenčno razmerje $\frac{k}{1}$ kar je $\Theta(k)$.

**Splošna spodnja meja konkurenčnega razmerja**

Vemo da optimalen algoritem v najslabšem primeru zgreši vsakih $k$ zahtevkov torej imamo $k$ prvotnih zgrešitev nato pa $\frac{n}{k}$ v najslabšem primeru $\Rightarrow k + \frac{n}{k}$. Če uporabljamo katerikoli sproten algoritem v najslabšem prmieru zgrešimo vsakič torej imamo $n$ zgrešitev. Konkurenčno razmerje v tem primeru postane

$$\frac{n}{k+\frac{n}{k}} = \frac{nk}{k^{2}+n }$$
$$\frac{nk}{k^{2}+n } \leq \frac{nk}{2n} = \frac{k}{2} \text{, če je $n > k^{2}$}$$

Torej velja da je konkurenčno razmerje sprotnih algoritmov proti optimalenm velja $\Omega(k)$.

***

**Problem preurejanja povezanega seznama**

Naj bo seznam $n$ elementov $(x_{1},...,x_{n})$, kjer je $L$ seznam, $r_{L}(x_{i})$ pa indeks $i$-tega elementa v seznamu $L$, kjer je $r_{L}\in \{ 1,...,n\}.$
Element na $r_L$ mestu lahko poiščemo v $\Theta(r_{L}(x_{i}))$ času.

Recimo da iščemo isti element na koncu seznama $m$-krat, to bi pomenilo kompleksnot $\Theta(m n)$, temu bi se lahko izognili če preuredimo list.

Če imamo neko zaporedje iskanj elementov bi lahko hoteli preurejati seznam z nekim algoritmom da bi zmanjšali čas iskanja.

To je težko brez da bi vedeli katere elemnte bomo iskali.

Nekatera zaporedja iskanj so tako rekoč težja kot druga. Algoritma, ki spreminja vrstni red lista torej ne bomo preverjali po temu kakšen rezultat dobimo ob najsabšem možnem zaporedju iskanj temveč po temu ali je njegov rezultat, za katerokoli zaporedje iskanj, konkurenčen z rezultatom algoritma, ki vnaprej pozna zaporedje iskanj. Algoritem ki vnaprej pozna zaporedje iskanj še vedno ne nujno zagotovi neko pospešitev iskanja saj mogoče to zaporedje iskanj tega ne dopušča, ampak če dopušča pa hočemo da bo naš slep algoritem dal relativno ugoden seznam za katerokoli iskanje.

Predpostavimo da iskanje $i$-tega elementa traja kar $i$ časa. Predpostavimo da je preudreditev možna samo z zamenjavo dveh sosednjih elementov.

Torej bi iskanje 6. elementa in premikanje le-tega na 4. mesto porabilo $8$ korakov, mi hočemo minimizirati vsoto cene vseh iskanj in cene premikov elementov.

Algoritem ki ga uporabimo naj vsak najdeni element premakne na začetek, če je element na $r_{L}(x_{i}) = r$ tem mestu potem bomo potrebovali $2r-1$ korakov, kjer rabimo  $r$ korakov da ga najdemo, in $r-1$ korakov da ga damo na prvo mesto.

**Izkaže se da je konkurenčno razmerje enako $4$.**

Naj bo $M$ algoritem ki vsak element ki ga najde premakne na začetek, naj bo $F$ algoritem ki optimalno preureja seznam.

Naj bo $L^M_i$ stanje seznama algoritma $M$ takoj po $i$-tem iskanju, in $L^F_i$ stanje seznama algoritma $F$ po $i$-tem iskanju.

Inverzija para elementov dveh listov naj bo par elementov ki je v enem listu v obratnem zaporedju kot v drugem - $(a,b,c)$, $(b,a,c)$ ima eno inverzijo $(a,b)$.

Naj bo $I(L_{1},L_{2})$ število inverzij v seznamih.

Naj bo

  $$c^M_i = 2 \cdot r_{L^M_{i-1}}(x) - 1$$
  
strošek ki ga v $i$-tem koraku opravi $M$ za iskanje in premikanje elementa na začetek in

  $$c^F_i = r_{L^F_{i-1}}(x) + t_i$$

strošek ki ga opravi $F$, kjer je $t_{i}$ število zamenjav ki jih opravi v tem koraku.

Naj bo $x$ element v obeh seznamih, ostale elemente lahko razporedimo v tri disj. množice

* **$BB$** - elementi, ki ležijo pred $x$ v obeh seznamih.
* **$BA$** - elementi, ki ležijo pred $x$ v prvem seznamu in za $x$ v drugem.
* **$AB$** - elementi, ki ležijo za $x$ v prvem seznamu in pred $x$ v drugem.


Položaj elementa $x$ v lahko izrazimo s pomočjo teh množic:

$$r_{L^M_{i-1}}(x) = |BB| + |BA| + 1$$
$$r_{L^F_{i-1}}(x) = |BB| + |AB| + 1$$

Podobnost seznamov $L^{M}$ in $L^{F}$ bomo merili s številom inverzij med njima $I(L^{M}_{i},L_{i}^{F})$. Manj inverzij kot je bolj sta si podobna.

Naj bo $L_{i-1}^{M}$ in $L_{i-1}^{F}$ stanje v seznamih po $i-1$ koraku. Naj se najprej izvede iskanje $x$ samo z algoritmom $M$. Ker vemo da je $x$ na $|BB| + |BA| + 1$ mestu se bo potem ko se ga najde izvedlo $|BB| +|BA|$ zamenjav, kjer dobimo $|BB|$ novih inverzij in zgubimo $|BA|$ invezij. Torej bo $I(L_{i}^{M},L_{i-1}^{F}) = I(L_{i-1}^{M},L_{i-1}^{F}) + |BB|  - |BA|$ oz. bo razlika v številu inverzij enaka $|BB|-|BA|$.

$$I(L_{i}^{M},L_{i-1}^{F})-I(L_{i-1}^{M},L_{i-1}^{F}) =  |BB|  - |BA|$$

Število inverzij ki se zgodi iz  $I(L_{i}^{M},L_{i-1}^{F})$ do $I(L_{i}^{M},L_{i}^{F})$ pa bo omejeno z največ $t_{i}$, torej imamo 

$$I(L_{i}^{M},L_{i}^{F})-I(L_{i-1}^{M},L_{i-1}^{F}) \leq  |BB|  - |BA|+t_{i}$$

S tem lahko pogledamo kako bi definirali potencial. 
Če pogledamo 

$$c_{i}^{M} = 2|BB| + 2|BA| + 1$$

vemo da nam v primerjavi da  bo razlika v inverzijah$I(L_{i}^{M},L_{i-1}^{F})-I(L_{i-1}^{M},L_{i-1}^{F}) = |BB|-|BA|$. Torej za vsak element v $|BB|$ porabimo 2 enoti časa da povečamo število inverzij in za vsak element v $|BA|$ porabimo 2 enoti časa da zmanjšamo število inverzij.

Nato ko izvedemo še $c_{i}^F$ se število inverzov poveča še za $t_{i}$.

Naj bo sprememba v potencialih natanko to. Rečemo da iz premika $\Phi_{i-1}$ v $\Phi_i$ povečamo potencial za število novih inverzij ki jih moramo rešiti, minus število inverzov ki smo jih rešili, plus morebitni inverzi ki pridejo od $t_{i}$. Ker smo videli da za vsak element v $|BB|$ porabimo dve enoti časa da  iz njega naredimo slabo inverzijo, dodamo $2$ enoti v potencial in enako za obračanje, ker očitno rabimo v koraku $c_{i}^{M}$ za vsak element v $|BA|$ 2 enoti časa da ga popravimo

Torej bo

$$2|BB| - 2|BA|  \le \Phi_{i} - \Phi_{i-1} \le 2|BB|- 2|BA| + t_{i}$$
$$2|BB| - 2|BA|  \le\Delta\Phi_{i}  \le 2|BB|- 2|BA| + t_{i}$$

Vse kar nam ostane je izračun stroška

Amortizirani strošek $\hat{c}^M_i$ algoritma $M$ je

$$\hat{c}^M_i = c^M_i + \Phi_i - \Phi_{i-1}$$

Vstavimo razliko potenciala in dejanski strošek

$$\hat{c}^M_i \le \left(2 \cdot r_{L^M_{i-1}}(x) - 1\right) + 2 \cdot |BB| - 2 \cdot |BA| + 2 \cdot t_i$$


$$\hat{c}^M_i \le 2 \cdot (|BB| + |BA| + 1) - 1 + 2 \cdot |BB| - 2 \cdot |BA| + 2 \cdot t_i$$
$$\hat{c}^M_i \le 4 \cdot |BB| + 2t_i + 1$$

Ker vemo, da velja 

$$r_{L^F_{i-1}}(x) = |BB| + |AB| + 1$$
$$|BB| + |AB| + 1 \ge |BB| + 1$$
$$r_{L^F_{i-1}}(x) \ge |BB| + 1$$
$$|BB| \le r_{L^F_{i-1}}(x) - 1$$

$$\Downarrow$$

$$\hat{c}^M_i \le 4 \cdot (r_{L^F_{i-1}}(x) - 1) + 2t_i + 1$$
$$\hat{c}^M_i \le 4 \cdot r_{L^F_{i-1}}(x) + 2t_i - 3$$
$$\hat{c}^M_i \le 4 \cdot r_{L^F_{i-1}}(x) + 2t_i$$
$$\hat{c}^M_i \le 4 \cdot r_{L^F_{i-1}}(x) + 4t_i$$
$$\hat{c}^M_i \le 4 \cdot c_{i}^{F}$$
$$\sum_{i=1}^{n} c^{M}_{i} \le 4 \cdot \sum_{i=1}^{n}c_{i}^{F}$$



Torej je konkurenčno razmerje algoritma $M$ enako $4$.



