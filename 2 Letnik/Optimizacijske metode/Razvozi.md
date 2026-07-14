Če imamo $3$ mesta in imamo v prvem mestu proizvodnjo $7$ enot v drugem in tretjem pa porabimo $3$ in $4$ enote pripadajoče.

Prevoz stane 3 na enoto iz prvega v drugega, iz prvega v tretjega porabimo 1 na enot o, iz drugega v tretjega porabimo 6 na enoto in iz tretjega v drugega 1 na enoto.

![[Pasted image 20260402192126.png|600]]
















Takšnemu problemu pravimo **problem razvoza**.

Na vhodu dobimo **usmerjen graf**, **uteži povezav** in **porabo oz. proizvodnjo** na vsakem vozlišču. Torej dobimo **utežen usmerjen graf** z utežmi na povezavah in vozliščih.

$$G=(V,E)$$

BŠS lahko prepdostavimo da je $G$ povezan kot neusmerjen graf - vsa vozlišča so povezana s povezavo ne pa nujno da lahko pridemo iz vsakega vozl. v vsakega.

V vozliščih imamo porabo $b_{v} \in \mathbb{R}$, kjer velja
- $b_{v} > 0$ potem porabimo $b_{v}$ enot
- $b_{v} < 0$ potem proizvedemo $b_{v}$ enot

Predpostavljamo $$\sum_{v \in V}^{}b_{v}=0$$

oz. da proizvedemo toliko kolikor porabimo. Če je vsota večja od nič potem nimamo dovolj proizvodnje, če je manjša od nič proizvajamo preveč.

Na vsaki povezavi imamo ceno povezave $c_{e} \in \mathbb{R} \,;\;\forall e \in E$.

Dopustna rešitev bo $x_{e} \,;\; e \in E$, kjer $x_{e}$ spremenljivka predstavlja koliko prevažamo po povezavi $e$.

$$x_{e} \geq 0$$

Če v vozlišče $v$ pripeljemo $x_{0}$ in odpeljemo $x_{1}$ mora biti proizvod v vozlišču enak $b_{v}=x_{0}-x_{1}$.

$$\sum_{\text{konec}(e)=v}^{}x_{e}-\sum_{\text{začetek}(e)=v}^{}x_{e}= b_{v}$$

kjer je $\text{konec}(e) = v$ povezave ki se konča v $v$ in $\text{začetek}(e) = v$ povezava ki se začne v $v$.
To pa velja za vse $v$.

Kriterijska funkcija pa je

$$\min\sum_{e \in E}^{}x_{e}c_{e}$$

***

Primer

$$\begin{array}
\\
\min & 3x_{12} + x_{13} + 6x_{23} + x_{32} \\
\text{p.p. } & -x_{12} - x_{13} = -7 \\
&x_{12} - x_{23} + x_{32} = 3 \\
&x_{13} + x_{23} - x_{32} = 4 \\
&x_{12}, x_{13}, x_{23}, x_{32} \ge 0 \end{array}$$

$$ $$

$$c = \begin{bmatrix} 3 \\ 1 \\ 6 \\ 1 \end{bmatrix} \quad b = \begin{bmatrix} -7 \\ 3 \\ 4 \end{bmatrix} \quad A = \begin{bmatrix} -1 & -1 & 0 & 0 \\ 1 & 0 & -1 & 1 \\ 0 & 1 & 1 & -1 \end{bmatrix}$$

$$ $$


$A$ je incidenčna matrika grafa $G=(V,E)$.

$$A = [a_{ve}]_{v \in V, e \in E}$$
$$a_{ve} = \begin{cases}
  1 &: \text{konec}(e) = v \\
  -1 &: \text{začetek}(e) = v \\
 0 & : \text{sicer}
\end{cases}$$

$$b = [b_{v}]_{v \in V}$$

$$c = [c_{e}]_{e \in E}$$

$$ $$

$$\begin{array}
\\
\min & c^{T}x \\
\text{p.p.} & Ax = b \\ 
& x \geq 0
\end{array}$$

Poznamo tudi njegov dual

$$\begin{array}
\\
\max & b^{T}y  \\
\text{p.p.} & A^{T}y \leq c \\ 
& y \text{ je prost}
\end{array}$$

>[!|hide]+ Izpeljava
> 
> 
> $$
> \begin{aligned}
> \min \quad & \sum c_j x_j \\
> \text{p.p.} \quad & \sum a_{ij} x_j = b_i \quad \forall i \in [n] \\
> & x_j \ge 0
> \end{aligned}
> $$
> 
> $$ $$
> $$\text{Direktno po pravilih o dualu}$$
> $$\downarrow$$
> $$ $$
> 
> $$
> \begin{aligned}
> \max \quad & \sum b_i y_i \\
> \text{p.p.} \quad & \sum a_{ij} y_i \le c_j \quad \forall j \in [m] \\
> & y_i \text{ je prost}
> \end{aligned}
> $$
> 
> **Dolga izpeljava**
> 
> $$
> \begin{aligned}
> \min \quad & \sum c_j x_j \\
> \text{p.p.} \quad & \sum a_{ij} x_j = b_i \quad \forall i \in [n] \\
> & x_j \ge 0
> \end{aligned}
> $$
> 
> $$\downarrow$$
> 
> 
> $$
> \begin{aligned}
> -\max \; & -\!\!\sum c_j x_j \\
> \text{p.p.} \; &\;\;\;\, \sum a_{ij} x_j = b_i \quad \forall i \in [n] \\
> & \quad  x_j \ge 0
> \end{aligned}
> $$
> 
> $$ $$
> $$\text{Dual}$$
> $$\downarrow$$
> $$ $$
> 
> $$
> \begin{aligned}
> -\min \quad & \sum b_i y_i \\
> \text{p.p.} \quad & \sum a_{ij} y_i \ge -c_j \quad \forall j \in [m] \\
> & y_i \text{ je prost}
> \end{aligned}
> $$
> 
> $$ $$
> $$\text{$y_i$ = $-y_i$}$$
> $$\downarrow$$
> $$ $$
> 
> $$
> \begin{aligned}
> -\min \quad & \sum -b_i y_i \\
> \text{s.t.} \quad & -\sum a_{ij} y_i \ge -c_j \quad \forall j \in [m] \\
> & y_i \text{ je prost}
> \end{aligned}
> $$
> 
> $$\downarrow$$
> 
> $$
> \begin{aligned}
> \max \quad & \sum b_i y_i \\
> \text{p.p.} \quad & \sum a_{ij} y_i \le c_j \quad \forall j \in [m] \\
> & y_i \text{ je prost}
> \end{aligned}
> $$
> 
> 
> **Še drug način**
> 
> 
> $$
> \begin{aligned}
> \min \quad & \sum cx \\
> \text{p.p.} \quad & \sum xa = b \\
> & x \ge 0
> \end{aligned}
> $$
> 
> $$
> \begin{aligned}
> -\max \quad & -\sum cx \\
> \text{p.p.} \quad & -\sum xa = -b \\
> & x \ge 0
> \end{aligned}
> $$
> 
> $$\text{Dual}$$
> $$\downarrow$$
> 
> $$
> \begin{aligned}
> -\min \quad & \sum -by \\
> \text{p.p.} \quad & -\sum ya \ge -c \\
> & y \text{ je prost}
> \end{aligned}
> $$
> 
> $$
> \begin{aligned}
> \max \quad & \sum by \\
> \text{p.p.} \quad & \sum ya \le c \\
> & y \text{ je prost}
> \end{aligned}
> $$


Dualne spremenljivke pripadajo vozliščem oz.

$$y = [y_{v}]_{v \in V}$$

Vsaka vrstica v transponirani matriki predstavlja povezavo in vsak stolpec vozlišče. Ker je matrika incidenčna je v vsaki vrstici ena $-y_{i}$ - začetno vozlišče in $y_{j}$ končno vozlišče. Torej velja da je razlika med $y_{j}$ v končnem volzišču in $y_{i}$ v začentem manjša od $c_{j}$. 

Torej

$$\forall (e = ij) \in E$$
$$y_{j}-y_{i} \leq c_{ij}$$

oz.

$$y_{i}+c_{ij}\geq y_{j}$$

torej $y_i$ začetnega vozlišča plus cena povezave mora biti večja ali enaka $y_{j}$ končnega vozl.

Po izreku o dualnem dopoljnjevanju tudi vemo da če je $x_{j} > 0$ potem mora veljati da je $\sum_{i=1}^{m}y_{i}a_{ij} = c_{j}$ in če je $\sum_{j=1}^{n}x_{j}a_{ij} < b_{i}$ potem je $y_{i} = 0$.

Ampak ker imamo v primalnem problemu že vse enakosti izpolnjene velja da sta $x$ in $y$ optimalna natanko tedaj ko velja da je $x_{j} = 0$ ali pa je $\sum_{i=1}^{m}y_{i}a_{ij} = c_{j}$ oz.

> Velja da sta $x,y$ optimalna natanko tedaj ko
> $$\forall ij \in E : x_{ij} =  0 \lor y_{i} + c_{ij} = y_{j}$$



To lahko rešimo s simpleksno metodo ampak poznamo tudi **simpleksno metodo na omrežjih**.

Primer

Vzamemo originalni problem

![[Pasted image 20260402223111.png]]

Poskusimo najti vrednosti dualnih spremenljivk. Torej iščemo vrednosti na vozliščih tako da bo veljalo

$$y_{i} + c_{ij} \geq y_{j}$$

Najprej vidimo da če prištejemo dualnim spremenljivkam oz. neki dopustni rešitvi neko konstano potem imam še vedno dopustno rešitev. Torej lahko poljubni dopustni rešitvi prištevam konstante. 

Tako tudi če je $y$ optimalna velja da prištevanje konstante vsaki spremenljivki ohranja optimalnost.

> $y$ je dopustna $\Leftrightarrow$ $y + \varepsilon$ je dopustna
> $y$ je optimalna $\Leftrightarrow$ $y + \varepsilon$ je optimalna

 Za kriterijsko funkcijo pa velja 
 
$$\sum_{V \in V}^{}b_{v} (y_{v}+\varepsilon) = \sum_{v \in V}^{}b_{v}y_{v}+\varepsilon \sum_{v \in V}^{}b_{v}$$
$$\varepsilon \sum_{v \in V}^{}b_{v} = 0$$

![[Pasted image 20260402224159.png]]

Vidimo da na dveh povezavah prevažamo $0$ oz. je $x_{23}$ in $x_{13}$ enak $0$. Na povezavah $x_{12}$ in $x_{23}$ pa imamo $7$ in $3$.

$$x_{12}= 7$$
$$x_{23}=3$$

iz tega po DD sledi da mora veljati

$$y_{i}+c_{ij}= y_{j}$$

$$y_{1}+1 = y_{2}$$
$$y_{2}+1=y_{3}$$

Vedno lahko najdemo vrednosti dualnih spremenljivk da postavimo $y_{1}$ na $0$ in potem nadaljujemo iz tega.

$$y_{1}=0$$
$$y_{2}=1$$
$$y_{3}=2$$

To pa mora biti dopustna rešitev kar poemni da mora veljati

$$y_{i}+c_{ij}\geq y_{j}$$

to pa moramo preveriti še za preostali dve povazavi kjer ne prevažamo ničesar.

$$y_{1} + 3 \geq y_{3}$$
$$y_{3} + 6 \geq y_{2}$$

torej

$$\quad\;0 + 3 \geq 2 \quad\checkmark$$
$$\quad\;2 + 6 \geq 1 \quad\checkmark$$

***

Zanima nas ali je v grafu vedno rešljivo $y_{i} + c_{ij} = y_{i}$.

Če graf nima ciklov velja da je vedno. Če ima cikle pa ni nujno.

Torej hočemo na grafu najti nek podgraf ki ne bo imel ciklov hkrati pa naj bi imel pot med vsemi vozlišči - **iščemo vpeto drevo**.

> Naj bo $x$ dopustna rešitev problema razvoza.
> Rečemo da je $x$ **drevesna dopustna rešitev** če obstaja tako vpeto drevo $T$ da je $x_{ij} = 0$ za vsak $e = \{ij\}$ ki ni v $T$

<br>

> Če obstaja dopustna rešitev za PR, obstaja tudi drevesna dopustna rešitev
> 
> >[!|dokaz]+ Dokaz:
> >Naj bo $x$ dopustna rešitev.
> >
> >Če ni drevesna obstaja cikel $C$ na katerem so vse vrednosti $x_{i}>0 \,;\; x_{i} \in C$ *če je na dopustni poveazvi v ciklu nula jo lahko damo ven in dobimo DDR*.
> >
> >Izberemo neko smer v ciklu. Povezave ki grejo v isto smer so preme, povezave ki grejo nasproti so obratne.
> >
> >Sedaj lahko na premih povezavah povečamo razvoz za $t$ na obratnih pa zmanjšamo razvoz za $t$. To je spet dopustna rešitev.
> >
> >Imamo možnosti za vsako vozlišče
> > - ima dve premi (pri obeh povečamo za $t$)
> > - dve obratni  (pri obeh zmanjšamo za $t$)
> > - premo in obratno  (pri eni povečamo pri drugi zmanjšamo za $t$)
> > - obratno in premo  (pri eni zmanjšamo pri drugi povečamo za $t$)
> >
> >Da bo rešitev še vedno dopustna je $t$ lahko enak najmanjši ceni vseh obratnih povezav v ciklu, saj če vzamemo predrago in povečamo za to predrago ceno ne bomo morali zmanjšati obratne oz. bo negativna kar je nedovoljeno.
> >
> >$$t = \min_{e \text{ je obratna}}x_{e}$$
> >
> >Tako dobimo obratno povezavo ki ima ničelni razvoz in uničimo cikel. Nadaljujemo z uničevanjem dokler ne dobimo drevesa.
> >
> >Če v ciklu ni obratnih povezav lahko samo rečemo da so vse obratne in odštejemo ta najmanjšo oz. samo poiščemo najmanjšo premo, jo damo na nič in pogledamo nov razvoz.
> >
> >Cena premih se spremeni 
> >
> >$$c_{e}x_{e} \rightarrow c_{e}(x_{e}+t)$$
> >
> >Cena obratnih se spremeni 
> >
> >$$c_{e}x_{e} \rightarrow c_{e}(x_{e}-t)$$
> >
> >Torej se cena spremeni za
> >
> >$$t(\sum_{\text{preme }e}^{}c_{e} - \sum_{\text{obratne }e}^{}c_{e})$$

<br>

Imamo torej drevesno dopustno rešitev $x$, $T$ je vpeto drevo.

$$y_{i} + c_{ij} = y_{j} \,;\; \{ ij\} \in E$$

je sedaj rešljiv.

Dualnim spremenljivkam pravimo **razvozne cene**. Če je $y$ dopusten za dual torej $y_{i} + c_{ij}\geq y_{j} \,;\; \forall \{ ij\} \in E$ je $x$ optimalna rešitev za PR. *Dokazano kasneje.*



Če to ne velja mora veljati da obstaja $\{ ij\} \in E \backslash T$ tako da je $y_{i} + c_{ij} < y_{j}$. Našli smo neko neoptimalnost.

<br>

> Če v DDR dodamo povezavo bomo dobili cikel. *Vsa vozlišča so že dosežena torej bo dodajanje nove povezave vedno šlo v neko vozlišče ki je že v drevesu - nastane cikel.*
> 
> *Recimo da imamo vstopno povezavo $ij$ kjer velja $y_{i} + c_{ij} < y_{j}$. Vse ostale povezave ki so v ciklu so bile v drevesu zato bo veljala enakost. Če gremo po ciklu  lahko izrazimo $y_{i} = y_{i-1}+c_{i-1}$, ko je povezava glede na vstopno obratna ali pa  $y_{i} = y_{i-1}-c_{i-1}$ če je prema. Naj bodo povezave $i,i+1,...,i+k,j$ .
> Na koncu v izraz $y_{j} = y_{k}\pm c_{kj}$ vsatvljamo vse enakosti dokler ne dobimo izraženega $y_{i}$ z $y_{j}$.
> Predpostavimo nek $y_{j} = y_{i}\pm c_{...} \pm c_{...} \pm\dots \pm c_{...}$.
> Ker je za vstopno povezavo velja $y_{i} + c_{ij} < y_{j}$ dobimo $y_{i}+c_{ij} < y_{i} \pm c_{...}\pm \dots \pm c_{...}$. Iz tega sledi $0 > c_{ij} \pm c_{...} \pm \dots \pm c_{...}$. Vse cene ki so negativne pripadajo obratnim povezavam, vse ki so pozitivne pa premim, glede na vstopno povezavo - $ij$.*
> 
> ![[Pasted image 20260429221000.png]]
> 
> Torej če $y$ ni dopustna rešitev obstaja $e = ij \notin T$ da za dobljen cikel *z dodajanjem $e = ij$* velja 
> 
> $$\sum_{e \text{ prema}}^{}c_{e} - \sum_{e\text{ obratna}}^{}c_{e} < 0$$
> 
> 
> Ker nimamo več DDR se moramo neke povezave znebiti. To naredimo po prejšnjem postopku, le da imamo določeno smer premih povezav in moramo izbrati obratno povezavo. *Če ta ne obstaja imamo neomejeno rešitev.* Od prej vemo da ko najdemo tako obratno povezavo in tam zmanjšamo prevoz se bo skupna cena prevoza po drevesu spremenila za
> 
> $$\Delta = t\left(\sum_{e \text{ prema}}^{}c_{e} - \sum_{e\text{ obratna}}^{}c_{e}\right) < 0$$
> 
> ker je izraz v oklepaju negativno število pomeni da če na premih povezavah povečamo za $t$ in na obratnih zmanjšamo za $t$ se skupna cena zniža.
> 

***

Simpleksna metoda po grafih

1. Poiščemo drevesno dopustno rešitev
2. Rešimo $y_{i} + c_{ij} = y_{j}$, če je $y_{i} +c_{ij} \geq y_{j}$ za vse povezave je $x$ opt. rešitev.
3. Če je $y_{i}+c_{ij}< y_{j}$ potem bo ta vstopna povezava ki jo bomo dali v rešitev, s tem pa bomo morali izbrati obratno povezavo ki gre ven za katero velja da je njena cena $\min$ cen vseh obratnih povezav.
4. Ponovno izračunamo dualne spremenljivke in ugotovimo koliko prevažamo in ponovimo dokler ne dobimo ooptimalne rešitve.

> Če je $x$ DDR in $y$ pripadajoče razvozne cene. Če  velja $y_{i} + c_{ij}\geq y_{j} \; \forall ij \in E$ potem velja da je $x$ optimalna rešitev.
> >[!|dokaz]+ Dokaz:
> > Naj bo $x'$ dopustna rešitev
> > 
> > Dokažemo lahko spodnjo neenakost
> > 
> > $$(y_{i}+c_{ij} -y_{j})x_{ij}' \geq (y_{i}+c_{ij}-y_{j}) x_{ij}$$
> > 
> > Če je $ij \in T$ velja $0 \geq 0$.
> > 
> > Će $ij \notin T$ velja $x_{ij}= 0$ in ker velja da je katerakoli dopustna $x_{ij}'\geq 0$ in $y_{i}+c_{ij} -y_{j}\geq 0$ torej velja neenakost.
> > 
> > 
> > 
> > $$(c + A^T y)^T x' \geq (c + A^T y)^T x$$
> > $$c^T x' + (A^T y)^T x' \geq c^T x + (A^T y)^T x$$
> > $$c^T x' + y^T (A x') \geq c^T x + y^T (A x)$$
> > $$c^T x' + y^T b \geq c^T x + y^T b$$
> > $$c^T x' \geq c^T x$$


**Opomba:** če se ne da izbrati vstopne povezave imamo optimalno rešitev. *Kot posledica zgornjega.*

**Opomba:** Če imamo dopustno rešitev in vstopno povezavo in če ne moremo izbrati izstopne povezave pomeni da so vse povezave v ciklu preme (torej v dobljenem ciklu pri izbrani povezavi ki jo hočemo dodati nimamo obratne povezave) s tem po prejšnji enačbi v našem ciklu velja da je $\sum_{}^{}c_{e} < 0$, kjer so $e$ preme povezave oz. vse povezave v ciklu. Torej bo celotna cena ko prevozimo po ciklu padla. To pomeni da lahko po tem ciklu hodimo v neskočnost in ceno manjšamo v neskončnost.
V tem primeru vemo da je problem **neomejen**. *Če imamo negaitven cikel še ne pomeni da je neomejen ker je lahko potencialno nedopusten.*

**Opomba:** Če izberemo drevo $T$ je DDR enolično določena torej so vrednosti $x_{i}$ enolično določene - to je očitno če gradimo razvoz od listov nazaj. 

**Opomba:** Simpleksna metoda na grafu se ne ustavi vedno. Ciklanju se lahko izognemo s pomočjo Cunninghamovega pravila.

Izberemo neko vozlišče  $r$ - **koren**.
Naj bo $e$ vstopna povezava - $e$ je ne nekem ciklu, $r$ je načelom izven tega cikla.
Ker imamo drevo obstaja pot od $r$ do  $v$ ,kjer je $v$ najbližje vozlišće našega cikla, in potem do $e$, če je $r$ že na ciklu imamo pač pot dolžine $0$.
Za izstopno izberemo tisto ki je prva med kandidatkami na poti od $v$ do $e$. Analogno najmanjšemu indeksu.

***

Kako poiščemo začetno DDR oz. dokažemo da je PR nedopusten?

Uporabimo dvofazno simpleksno metodo na omrežjih.

Imamo koren $r$ in rešimo dodaten problem.

Vozlišča ostanejo enaka ampak dodamo še naslednje povezave.

Če je $b_{v} \geq 0$, dodamo povezavo $rv$, če še ne obstaja. Če je $b_{v} < 0$, dodamo povezavo $vr$, če še ne obstaja. *Torej če vozlišče ne proizvaja naredimo povezavo v njega iz korena, če proizvaja pa nareidmo povezavo iz njega v koren.*

Dodanim povezavam pravimo **umetne povezave**.

*Ideja je da najdemo neko preprosto dopustno rešitev, kjer vse ki proizvajajo preko umetnih povezav damo do vseh ki pobirajo, nato pa peljemo po navadnem postopku do optimalne rešitev in pogledamo če vsebuje umetne povezave.*

Na povezavi $rv$ za $b_{v} \geq 0$ nastavimo prevoz $x_{rv} = b_{v}$
Na povezavi $vr$ za $b_{v} < 0$ nastavimo prevoz $x_{vr}=-b_{v}$
Vsem drugim $e$ dodelimo $x_{e} =0$.

Trdimo da je to DDR za dodatni problem.
>[!|dokaz]+ Dokaz:
>
> **Za $v \neq r$:**
> *   Če je $b_v \geq 0$:
>     $$\sum_{\text{konec}(e)=v} x_e - \sum_{\text{začetek}(e)=v} x_e = b_v - 0$$
> *   Če je $b_v < 0$:
>     $$\sum_{\text{konec}(e)=v} x_e - \sum_{\text{začetek}(e)=v} x_e = 0 - (-b_v)$$
> 
> **Za $v = r$:**
> 
> $$\sum_{\text{konec}(e)=r} x_e - \sum_{\text{začetek}(e)=r} x_e = \sum_{\substack{v: b_v < 0 \\ v \neq r}} (-b_v) - \sum_{\substack{v: b_v \geq 0 \\ v \neq r}} b_v$$
> $$= - \sum_{v \neq r} b_v = b_r \quad \left(\text{ker } \sum_{v \in V} b_v = 0\right)$$

Sedaj **vsem umetnim povezavam damo ceno $1$,**
**vsem prvotnim povezavam dodelimo ceno $0$.**

Problem je dopusten, je omejen $\sum_{e \in E}^{}c_{e}x_{e}\geq 0$ $\Rightarrow$ torej je optimalen.

Lahko uporabimo simpleksno metodo na omrežjih.

Prvotni problem je dopusten natanko tedaj ko velja da v pomožnem problemu velja da optimalna rešitev uoprablja le prvotne povezave oz. je **optimalna cena prevoza enaka 0**.

Če je **optimalna cena** večja od 0 potem imamo nedopusten problem.

**Opomba:** če je $\sum_{v}^{}b_{v} > 0$ potem imamo večjo porabo kot proizvod $\Rightarrow$ problem je avtomatično nedopusten.

**Opomba:** če je $\sum_{}^{}b_{v} < 0$ potem dodamo smetišče oz. dodatna vozlišča kamo damo za porabo ravno ostanek. Cene ki vodijo do smetišča imajo 0. Načeloma je rešljiv.


***

**Izrek o celoštevilskih rešitvah**

Problem razvoza, $b_{v} \in \mathbb{Z}$.

1\. Če obstaja dopustna rešitev potem obstaja celoštevilska dopustna rešitev.

2\. Če obstaja optimalna rešitev potem obstaja optimalna celoštevilska rešitev. 

>[!|dokaz]+ Dokaz:
> 
> Dokaz sledi iz simpleksne metode na omrežjih.
> 
> Dopustno rešitev najdemo z dvofazno simpleksno metodo. Začetna DDR pomožnega problema je celoštevilska *$x_{rv} = \pm b_{v} \in \mathbb{Z}$*.
> 
> Vsak korak simpleksne metode pa ima lastnost da če začnemo s celoštevilskim DDR potem bo naslednja DDR celoštevilska, saj prištevamo ali odštevamo min. prevoz $x_{ij}$ iz obratnih povezav ki je celoštevilski.
> 
> Če je problem neomejen je pač neomejen, drugače pridemo do celoštevilske optimalne rešitve.
<br>

Matrika $A^{n \times n}$ je **dvojno stohastična** natanko tedaj ko velja da so vsi $a_{ij} \geq 0$, $\sum_{i}^{}a_{ij} = 1 \; \forall j$ in $\sum_{j}^{}a_{ij} = 1 \; \forall i$.

**Permutacijska matrika** $A^{n \times n}$ je matrika ki ima v vsakem stolpcu in vrstici natanko eno $1$, vsi ostali elementi so $0$.

*V splošnem imamo $n!$ permutacijskih matrik.*

Naj bo $A^{n \times n}$ dvojno stohastična matrika. Velja,  da obstaja pripadajoča permuatcijska matrika $P^{n \times n}$ da velja

$$p_{ij} > 0 \Rightarrow a_{ij} > 0$$

*Trdimo da obstaja taka permtuacijska matrika ki ima enke lahko samo tam kjer imamo neničelne vrednosti v $A$.*

>[!|dokaz]+ Dokaz:

Skonsturiramo omrežje kjer imamo $n$ vozlišč na eni strani in $n$ na drugi.

Vsa vozlišča na levi označimo z $v_{i}$ kar predstavlja vrstico matrike $A$, desne pa bodo $s_{i}$ oz. stolpci matrike $A$. Povezava iz $v_{i}$ v $s_{j}$ naj obstaja natanko tedaj ko velja $a_{ij} > 0$.

Na levi strani so $b_{i} = -1$ na desni pa $b_{i} = 1$.

Cena vseh povezav pa je $c_{ij} = 0$.

Trdimo da je problem dopusten, res, za vsak $x_{ij}$ lahko vzamemo natanko $a_{ij}$ saj vsa vozl. iz istega st. v $A$ kažejo v eno vozl. in vemo da je vsota teh enaka 1, iz vsakega levega vozl. pa kažejo puščice ene vrstice za katere vemo da se seštejejo v $1$ torej bomo razvozili natanko 1 iz in natanko 1 v vsako vozlišče. 

Po izreku o celoštevilskih rešitvah pa vemo da obstaja celoštevilska rešitev $x \in \mathbb{Z}^{n^{2}}$

$$p_{ij} := x_{ij}$$

kjer je $x_{ij}$ seveda 0 če $v_i$ in $s_{j}$ sploh nista povezana.

Veljati mora $\sum_{j}^{}p_{ij} = 1$, $\sum_{i}^{}p_{ij}=1$, kjer velja da je $p_{ij}$ celo torej mora biti $p_{ij} =1$ ostali v vrstici / stolpcu pa $0$ oz. da je $P$ permutacijska matrika.

$$p_{ij} > 0 \Rightarrow p_{ij} = 1 \Rightarrow x_{v_{i}s_{j}} \Rightarrow v_{i}s_{j} \in E \Rightarrow a_{ij} > 0$$

***

**Könningov izrek o plesnih parih**

Recimo da imamo dvodelen graf $G$, kjer imamo na levi in na desni enako število vozl. in naj bo $r$-regularen.

Potem v $G$ obstaja popolno prirejanje. Vsa vozl. nastopajo v paru preko povezave.

>[!|dokaz]+ Dokaz:
> 
> Uporabimo zadnjo trditev o cleoštevilskih trditvah. Konstr. stohastično matriko:
> 
> $$a_{ij} \begin{cases}
> \frac{1}{r}: x_{i} \sim y_{j} \\
> 0 : x_{i} \nsim y_{j}
> \end{cases}$$
> 
> $$A = [a_{ij}] \text{ je dvojno stohastična}$$
> 
> $$a_{ij} \geq 0$$
> $$\sum_{j}^{}a_{ij}=r\frac{1}{r} = 1$$
> $$\sum_{i}^{}a_{ij}=r\frac{1}{r} = 1$$
> 
> $$\Rightarrow \exists  \text{ perm. matrika }P, p_{ij}=1 \Rightarrow a_{ij}>0$$
> $$p_{ij}=1 \Rightarrow x_{i} \sim y_{i}$$
> 
> določa popolno prirejanje.


***

**Problem razvoza z omejitevami**

Vse je enako le da imamo še vektor omejitev za vsako povezavo $u_{e} \in [0,\infty] \,;\; e \in E$ kjer velja $x_{e} \leq u_{e}$. Pravimo da je $u_e$ **kapaciteta povezave**. Torej

$$\begin{array}
\\
\min & c^{T}x\\
\text{p.p.} & Ax = b \\ 
& 0 \leq x\\
& x \leq u
\end{array}$$

Spet uporabimo (načeloma dvofazno) simpleksno metodo na omrežjih. 

Pravimo da je povezava **prazna** ko velja $x_{e} = 0$.
Pravimo da je povezava **nasičena** ko velja $x_{e} = e_{u}$

Dopustna rešitev $x$ je DDR natanko tedaj ko velja da obstaja vpeto drevo $T$, da je vsaka povezava ki ni v $T$-ju prazna ali nasičena. Če je povezava nasičena jo ponavadi označimo z valovito puščico.

Za dano DDR $x$ in pripadajoč $T$ zapišemo razvozne cene $y_{i}+c_{ij} = y_{j} \;\forall ij \in T$

> Naj bo $x$ DDR, $T$ drevo, $y$ pa razvozne cene- 
> 
> Če velja 
> - $y_{i}+c_{ij}\geq y_{j}$ $\forall ij \notin T, x_{ij}= 0$ *(za prazne mora veljati $\geq$)*
> - $y_{i}+c_{ij}\leq y_{j}$ $\forall  ij \notin T, x_{ij} = u_{ij}$ *(za nasičene pa  $\leq$)* 
>   
> potem je $x$ optimalna rešitev.
> 
> >[!|dokaz]+ Dokaz:
> > 
> > Naj bo $x$ dopustna rešitev in $x^{*}$ optimalna rešitev. Trdimo da velja
> > 
> > $$(y_{i}+c_{ij}-y_{j})x_{ij} \geq (y_{i}+c_{ij}-y_{j})x^{*}_{ij} \;\; \forall ij \in E$$
> > 
> > $$ $$
> > 
> > $$ij \in T \Rightarrow y_{i}+c_{ij} = y_{j} \Rightarrow 0 \geq 0$$
> > $$ij \notin T, x^{*}_{ij} = 0 \Rightarrow y_{i}+c_{ij} \geq y_{j}$$
> > $$\Rightarrow (y_{i}+c_{ij}-y_{j})x_{ij} \geq 0$$
> > $$ij \notin T, x^{*}_{ij} = u_{ij}, {\color{green}x^{*}_{ij}\geq x_{ij}} \Rightarrow y_{i} + c_{ij} \leq y_{j}$$
> > 
> > *če pomnožimo nenačbo v zelenem z oklepaji kjer  vemo da je to nepozitivno število se neenačaj obrne in dobimo*
> > 
> > $$\Rightarrow(y_{i}+c_{ij}-y_{j})x^{*}_{ij} \leq  x_{ij} (y_{i}+c_{ij}-y_{j})$$
> > 
> > Seštejemo neenakosti po vseh $ij \in E$, dobimo 
> > 
> > $$c^{T}x - (A^{T}y)x \geq c^{T}x^{*} - (A^{T}y)^{T}x^{*}$$
> > $$(A^{T}y)x = y^{T}Ax = y^{T}b$$
> > $$ (A^{T}y)^{T}x^{*} = y^{T}Ax^{*} = y^{T}b$$
> > $$c^{T}x-y^{T}b\geq c^{T}x^{*} - y^{T}b$$
> > $$c^{T}x\geq c^{T}x^{*}$$

Če imamo DDR kjer za pripadajoče razvozne cene ne veljajajo pogoji za optimalnost pa opravimo korak simpleksne metode.

Imamo DDR $x$, $T$, $y$.

Če $\exists ij \notin T,$ $x_{ij} = 0,$ $y_{i}+c_{ij}<y_{j}$ potem bo
$ij$ vstopna povezava, če vstopi dobimo cikel s premimi in obratnimi povezavami. Na premih povečamo za $t$ na obratnih zmanjšamo z $t$. Od prej vemo da pomanjšamo lahko z najmanjši razvoz na obratnih povezavah, sedaj pa tudi ne smemo povečati preveč saj imamo $u_{ij}$ torej velja da je

$$t := \min (\{ x_{e} \;;\; e \text{ je obratna} \} \cup \{ u_{e}-x_{e} \,;\; e \text{ je prema}) \}$$

Če $\exists  ij \notin T,$ $x_{ij}= u_{ij},$ $y_{i}+c_{ij}>y_{ij}$ potem bo
$ij$ vstopna povezava, spet se ustvari cikel, ker imamo nasičeno povezavo lahko le manjšamo razvoz - na premih manjšamo za $t$ na obratnih pa večamo za $t$. Torej iščemo $t$ da velja

$$t :=\min \{ x_{e} \;;\; e \text{ je prema} \} \cup \{ u_{e}-x_{e} \;;\; e \text{ je obratna} \}$$

Izstopna povezava je seveda tista kjer dosežemo $t$.

Po enakem postopku kot pri normalnem problemu dobimo neenačaj le da je tukaj večje.

$$\sum_{e \text{ prema}}^{}c_{e} - \sum_{e\text{ obratna}}^{}c_{e} > 0$$

Če pogledamo naš $t$ ki predstavlja zmanjševanje na premih in večanje na obratnih lahko zapišemo spremembo kot


$$\Delta =-t\left(\sum_{e \text{ prema}}^{}c_{e} - \sum_{e\text{ obratna}}^{}c_{e}\right) \leq 0$$

***


**Opomba:** Lahko se zgodi da se algoritem ne ustavi oz. pride do ciklanja. Tega lahko preprečimo s Cunninghamovim pravilom.

**Opomba:** vstopna in izstopna povezava sta lahko isti.

**Opomba:** do začetne DDR pridemo preko pomožnega problema - izberemo nek koren $r$ in iz vseh proizvajalcev pošljemo povezavo in prevoz če še ne obstaja, če porabljamo pošljemo od korena proti porabniku. Lahko se zgodi da če je povezava obstoječa ima lahko omejitev, zato če povezave iz $vr$ ali $rv$ povezave ni ali pa je omejitev ki ne dopušča zadostnega prevoza potem dodamo $vr$ ali $rv$ s kapaciteto neskončno in ji dodelimo ceno $1$, vsem originalnim pa damo ceno $0$. Torej bo optimalni problem dopustne ko je optimalna vrednost pomožnega problema enaka $0$.