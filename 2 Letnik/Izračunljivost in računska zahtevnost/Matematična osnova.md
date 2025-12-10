**Množica** je skupina **edinstvenih** matematičnih objektov katerim pravimo **elementi** množice.

**Podmnožica** je taka množica katere elementi so vsi tudi elementi **nadmnožice**.

**Prava podmnožica** je podmnožica ki ni enaka nadmnožici.

Množice nimajo ponavljajočih se elementov torej je $\{ 7,7,7\}$ enaka $\{ 7\}$. Če hočemo upoštevati število ponovljenih elementov govorimo o **multimnožicah**.

**Neskončna množica** vsebuje neskončno vrednosti. Pišemo $\mathbb{N} = \{ 1,2,...\}, \mathbb{Z} = \{ ...,-2,-1,0,1,2,...\}$. Množica brez elementov je **prazna množica** $\emptyset$. Množica z enim elementom je **singelton**. in množica z dvema elementom je **neurejen par**.

Poznamo **presek, unijo, komplement, razliko, in simetrično razliko**, kot operacije nad množicami.

**Zaporedje** objektov je urejen seznam - $(7,10,11)$. Vrstni red in ponavljanje elementov v množici nista pomembna medtem ko v zaporedju sta.

**Končno** zaporedje $n$ elementov kličemo **$n$-terica**. *- $n$-tuple*

**Potenčna množica** je množica vseh podmnožic.

**Krartezični produkt** množic je množica vseh urejenih parov množic.

**Funkcija** je pravilo ki slika elemente iz ene množice v elemente druge množice - element ne more imeti več slik.

$f: A \rightarrow B$

**Rigorozno:** 

Funkcija z domeno $X$ in kodomeno $Y$ je binarna relacija $R$ med $X$ in $Y$, ki zadovoljuje naslednja pogoja:

*   Za vsak $x$ v $X$ obstaja $y$ v $Y$ tako, da je $(x, y) \in R$.
*   Če velja $(x, y) \in R$ in $(x, z) \in R$, potem je $y = z$.

$A$ je domena in $B$ je kodomena $f$.
$f(A)$ je slika $f$ in velja $f(A) \subset B$.

Če $f$ slika vsak element iz $A$ v originalen element v $B$ potem je injektivna.

Če je $f(A) = B$ potem je $f$ **surjektivna**.

$f$ je **bijektivna** če je oboje hkrati.

Če obstaja surjektivna funkcija iz $A$ v $B$ potem obstaja injektivna funkcija iz $B$ v $A$. In obratno če obstaja injekcija v eno smer obstaja surjekcija v drugo.

Če je funkcija surjektivna pravimo tudi da slika **na** B.

Če imamo za vhod funkcije neko $n$-terico $(a_{1},...,a_{n})$ potem so $a_{i}$ argumenti $f$ in imamo funckijo $n$ spremenljivk. Tako imamo unarne in binarne funckije kot najpogostejše.

Nekatere binarne funckije pišemo z medponskim zapisom $+(a,b) := a + b$ namesto predponskim.

**Predikat** oz. **lastnost** je funkcija katere kodomena je $\{ \text{TRUE}, \text{FALSE}\}$. Primer je enakost - $\text{equal}(A \times B) = \{ \text{TRUE, FALSE}\}$. Funkcija ki ovrednosti neke elemente glede na trditev predikata.

$$S(x,y) = x\text{ je enak }y$$

***

**Grafi**

Neusmerjen graf oz. graf je množica točk in povezav.
Definiran je kot par množice vozlišč in povezav.

$$(V, E)$$

Število povezav ki pripadajo vozlišču rečemo stopnja vozlišča.

**Dovoljujemo povezavo samo nase oz. zanko.**

Neusmerjene povzeave predstavljamo z $(i,j)$ kjer sta $i$ in $j$ povezani vozlišči.

Podgraf je graf za katerega velja da je $V' \subset V$ in $E' \subset E$.

Pot je zaporedje vozlišč ki so povezani. Enostavna pot ne ponavlja vozlišč.

Graf je **povezan** če med vsakima vozliščema obstaja pot.

Enostavna pot je **cikel** če se začne in konča v istem vozlišču.

Grafu rečemo **drevo** če velja da je povezan in ne vsebuje nobnih ciklov.

**List** imenujemo vozlišča drevesa stopnje 1.

**Usmerjen graf** ima puščice namesto črt in za vsako vozlišče vsebuje vstopno stopnjo in izhodno stopnjo. 
Povezavo v usmerjenem grafu predstavimo kot par $(i,j)$.

Pot kjer vse puščice kažejo v isto smer kot njeni koraki imenujemo **usmerjena pot**. Le-ta je **močno povezan** če usmerjena pot povezuje vsaki dve vozlišči.

***


**Definicije** opisujejo objekte in pojme, ki jih uporabljamo. 

Ko definiramo različne objekte in pojme, običajno izjavimo **matematične trditve** o njih. 
Značilno je, da trditev izraža, da ima objekt določeno lastnost. 
Trditev je lahko resnična ali napačna; Dvomljivost glede njenega pomena ni dovoljena.

**Dokaz** je prepričljiv logični argument, da je trditev resnična.

**Teorem** je matematična trditev, ki je dokazano resnična. Na splošno to besedo uporabljamo za trditve posebnega pomena. Občasno dokazujemo trditve, ki so zanimive samo zato, ker pomagajo pri dokazovanju druge, pomembnejše trditve. Takšne trditve se imenujejo **leme**. Včasih nam teorem ali njegov dokaz omogoča, da z lahkoto sklepamo, da so resnične tudi druge, povezane trditve. Te trditve se imenujejo **posledice** teorema.

***



Za **dokazovanje** uporabljamo par popularnih strategij kot so **dokaz s protislovjem kot najsplošnejšo, dokaz z indukcijo, dokaz s konstrukcijo.**

**Dokaz sprotislovjem** temelji na predpostavljanju negacije posledice skupaj z originalnimi predpostavkami iz česar nato pridemo do protislovja.

**Dokaz z indukcijo** je dokaz ki temelji na lastnosti naranvih števil kjer če za neko število velja $P(n_{0})$ in hkrati velja $P(n) \Rightarrow P(n+1)$ potem velja $P(n) \forall n \geq n_{0}$. 

**Dokaz s konstrukcijo** je uporabljen pri dokazovanju obstoja nekega elementa kar lahko dokažemo s konstrukcijo.

Če dokazujemo **enako moč** množic lahko najdemo **bijekcijo** ali pa pokažemo da sta obe **podmnožici druga druge**.