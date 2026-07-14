Problem **pretoka** je iskanje maksimalne količine enot iz enega vozliša v drugo, kjer imamo na vsaki povezavi omejeno število enot ki jih lahko prenesemo. *angl. flow*

Imamo $G(V ,E)$ in dve vozlišči $s,t$ *angl. source, terminal*.

V $s$ ne gre nobena povezava in iz $t$ ne gre nobena povezava.

Omejtive na vsaki povezavi je utež $c : E \rightarrow \mathbb{R}^{+}$.

Preslikavo $c$ lahko razširimo v $V \times  V$, kjer velja da če imamo $ij$, ki ni v $E$ potem je $c(i,j) = 0$.

Preslikavi $f : V \times V \rightarrow \mathbb{R}$ je **pretok** če velja
- $f(i,j) = -f(j,i)$
- $\sum_{i}^{}f(i,j) = \sum_{k}^{}f(j,k)$ oz. velja Kirchhoffovi zakoni
- $f(i,j) \leq c(i,j)$

Radi bi maksimizirali velikost pretoka

$$|f|  = \sum_{j}^{}f(s,j) = \sum_{i}^{}f(i,t)$$

Če je $f(i,j) < 0$ je povezava usmerjena od $j$ do $i$.

Za ta problem lahko uporabimo simpleksno metodo na omrežjih ali pa **Ford-Fulkersonov** algoritem.



***

> Velja da je vsota enot ki grejo iz $s$ enaka vsoti enot ki grejo v $t$.
> >[!|dokaz]+ Dokaz:
> >
> > $$\forall v \in  V \backslash \{ s,t\} $$
> > $$\sum_{e \,\in\, \text{in}(v)}^{}x_{e}=\sum_{e \,\in\, \text{out}(v)}^{}x_{e}$$
> > 
> > To enakost seštejemo po vseh $v$-jih ki so v $V \backslash \{ s,t\}$. Vidimo da za povezavo z $x_{e}$ ki ne gre iz $s$ ali v $t$ se bo prištelo in odštelo $x_{e}$, torej se vsi $x_{e}$ ki ne peljejo iz $s$ ali v $t$ pokrajšajo.
> > 
> > $$\sum_{\text{end}(e) = t}^{}x_{e} - \sum_{\text{begin}(e) = s}^{}x_{e} = 0$$
> > 
> > Vrednosti pravimo **prostornina pretoka**.
> 
***

**Prevod na problem razvoza z omejitvami**

Ta problem lahko prevedemo na problem razvoza z omejitvami

$$b_{v} = 0 \;\; \forall v \in V$$
$$c_{e}=0 \;\;\forall e \in E$$
$$u_{e} \in [0,\infty)$$

Dodamo še povezavo $ts$ in ji dodelimo neskončno kapaciteto $u_{ts}= \infty$ in ceno $c_{ts}=-1$.

Ker minimiziramo ceno hočemo da gre čim več po $e_{ts}$ ker ima ceno $c_{ts}=-1$ torej rabimo čim več pripeljati v $t$ da lahko potem po povezavi $e_{ts}$ dobimo minimalno ceno oz. s tem dejansko poiščemo maksimalno količino ki jo lahko prenesemo od $s$ do $t$ in s tem maksimalen pretok.

Vsak dopusten pretok nam tako da dopusten razvoz, začetna dop. rešitev je lahko samo $x_{e}=0$ za vsak $e$. Izvedemo simpleksno metodo na omrežjih.

***

**Ford-Fulkersonov algoritem**

Če izvajamo simpl. metodo na omrežjih opazimo da pri nastalih ciklih vedno večamo prevoz na povezavah v smeri $s \rightarrow t$ in manjšamo na povezavah $s \leftarrow t$. Pri tej metodi le-te označimo za **preme** in **obratne**.

Če ima prema povezava maksimalen pretok ne moremo večati na premih, če pa je obratna prazna potem ne moremo zmanjštevati. Motivira definicijo *povečujoče poti*.

Definicija: **Povečujoča pot** je zaporedje vozlišč $v_{0},...,v_{k}$ tako da velja

$$v_{0} = s, v_{k}=t$$
$$ $$
$$\forall  i = 1,...,k \,\text{ velja} $$ 
$$v_{i-1}v_{i} \in E, x_{v_{i-1}v_{i}} < u_{v_{i-1}v_{i}}$$
$$\text{ali}$$
$$v_{i}v_{i-1} \in E, x_{v_{i}v_{i-1}} > 0$$


Če imamo povečujočo pot lahko na premih pretok povečamo za $\varepsilon$ na obratnih pa zmanjšamo za $\varepsilon$, kjer je

$$\varepsilon :=\min \{ x_{e} \,;\; e \text{ obratna}\} \cup \{ u_{e}-x_{e} \;;\; e \text{ prema} \}$$

s tem se prostornina pretoka poveča za $\varepsilon$. Velja da je $\varepsilon > 0$ (ni degeneriranih korakov).

*Vozlišča grafa se pri izvajanju simpleksne metode razdelijo na 2 skupini - tista ki imajo razvozno ceno enaka nič in tista ki imajo razvzno ceno enako 1.*

Algoritem išče povečujoče poti dokler ne obstaja več, če jo najde poveča maks. pretok za vrednost povečujoče poti, če je ne najde konča.

Število korakov ki jih opravi FF algoritem je omejen z $\frac{mn}{2}$.
V vsakem koraku lahko nezasičeno pot najdemo v $O(m)$. Torej imamo $O(m^{2}n)$.

>**Trditev:** Naj bodo omejiteve vseh povezav cela števila. Velja da v takem grafu obstaja celoštevilski maksimalni pretok.
>>[!|dokaz]+ Dokaz:
>>Da se dokazati s tem da prevedemo na graf z omejitvami za katerega določimo trivialno celoštevilsko rešitev, in po izreku o obstoju celoštevilskega maksimalnega razvoza obstaja tudi celoštevilski maksimalen pretok.


> **Dfn.: Prerez** je podmnožica vozlišč $C \subset V$ kjer velja $s \in C$, $t \notin C$. *angl. cut*
> 
> Prerezi tvorijo dualni problem.


>  **Dfn.: Kapaciteta prereza** je
> 
> $$\sum_{i \in C ,j \notin C}^{}u_{ij} \in  [0, \infty]$$
> 
> To je problem maksimalnega pretoka in minimalnega prereza.

> Naj bo $x$ pretok in $C$ prerez. Velja da je 
> $$\text{prostornina pretoka } \leq \text{ kapaciteti prereza}$$
> 
> Kot posledica velja da ko je prostornina pretoka enaka kapaciteti prereza je pretok maksimalen in prerez minimalen.
> >[!|dokaz]+ Dokaz:
> >
> >$$\sum_{e \,\in\, \text{out}(v)} x_e = \sum_{e \,\in\, \text{in}(v)} x_e $$
> >Seštejemo po vseh vozliščih razen $s$, velja Kirchhoffov zakon
> >
> >$$\sum_{e \,\in\, \text{out}(v)} x_e = \sum_{e \,\in\, \text{in}(v)} x_e \;\;\;\;/ \sum_{v \in C \,-\, \{s\}}$$
> >$$\sum_{e \,\in\, \text{out}(C\, - \,\{s\}\!) } x_e = \sum_{e \,\in\, \text{in}(C\, - \,\{s\}\!) } x_e$$
> >V tem se $x_{e}$ pojavi dvakrat če je povezava vsebovana v $C \backslash \{ s\}$ oz. če je sta krajišči v $C \backslash \{ s\}$ oz. ni tista ki pelje v drugo množico.
> >  
> > $$\sum_{\substack{\text{začetek}(e) \in C \setminus \{s\} \\ \text{konec}(e) \notin C \setminus \{s\}}} x_e = \sum_{\substack{\text{konec}(e) \in C \setminus \{s\} \\ \text{začetek}(e) \notin C \setminus \{s\}}} x_e$$
> > 
> > Torej je vsota iz prereza enaka vhodu v prerez, brez da upoštevamo $s$.
> > 
> > V vsoto dodajmo še $s$ in poračunamo. Naj bo razlika med izstopajočimi in vstopajočimi povezavami enaka
> > 
> > $$\sum_{\substack{i \in C \\ j \notin C}} x_{ij} - \sum_{\substack{i \notin C \\ j \in C}} x_{ij} = $$ $$\sum_{\substack{i \in C \setminus \{s\} \\ j \notin C}} x_{ij} + \sum_{j \notin C} x_{sj}- \sum_{\substack{i \notin C \setminus \{s\} \\ j \in C }} x_{ij} + \sum_{j \in C } x_{sj}$$
> >  *Prvo vsoto razbijemo na dva primera po $i$ kjer je $i$ lahko $s$ ali pa katerokoli drugo polj. vozl. v $C$.*
> >  *Pri drugi vsoti rabimo da $i$ **ni v $C \setminus \{ s\}$** , da lahko uporabimo prejšnjo enačbo, ampak sedaj smo odšteli poleg $i$-jev ki niso v $C$ tudi $i$-je ki so $s$ kar pomeni da jih moramo prišteti nazaj.* 
> >  
> >  Sedaj lahko pokrajšamo po prejšnji enačbi  $${\color{green}\sum_{\substack{i \in C \setminus \{s\} \\ j \notin C}} x_{ij} }+ \sum_{j \notin C} x_{sj} \; {\color{green}-\sum_{\substack{i \notin C \setminus \{s\} \\ j \in C }} x_{ij}} + \sum_{j \in C } x_{sj}$$
> >  
> >  Torej dobimo
> >  $$ \sum_{j \notin C} x_{sj} + \sum_{j \in C } x_{sj}$$
> >  
> >  Kar je vsota po vseh $j$-jih
> >  
> >  $$\sum_{j \in V}^{}x_{sj}$$
> >
> >kar pa je ravno prostornina pretoka.
> >
> >Torej velja da za vsak prerez velja
> >
> > $$\sum_{\substack{i \in C \\ j \notin C}} x_{ij} - \sum_{\substack{i \notin C \\ j \in C}} x_{ij} =\sum_{j \in V}^{}x_{sj}$$
> > 
> > oz. je **prostornina pretoka** enaka razliki celotnega pretoka ven iz prereza in pretoka v prerez. 
> > 
> > Velja da je $0 \leq x_{ij}\leq u_{ij}$ in lahko zgornjo vsoto ocenimo kot
> > 
> > $$\sum_{\substack{i \in C \\ j \notin C}} x_{ij} - \sum_{\substack{i \notin C \\ j \in C}} x_{ij} \leq \sum_{j \in V}^{}u_{ij}$$
> > 
> > Torej je 
> > $$\text{prostornina pretoka } \leq \sum_{\substack{i \in C \\ j \notin C}} u_{ij}  $$
> > $$\text{prostornina pretoka } \leq \text{kapaciteta prereza}$$

**Opomba:** če vzamemo $C = \{ s\}$ in $C = V \setminus\{t \}$ spet dokažemo da je tok iz $s$ enak toku v $t$.

> Velja ena od možnosti
> - Problem pretoka je neomejen, v katerem primeru velja da je kapaciteta vsakega prereza neskončna
> - Problem pretoka je optimalen, v katerem primeru obstaja prerez katerega kapaciteta je enaka temu max pretoku.
> 
> >[!|dokaz]+ Dokaz:
> >Problem prevedemo na problem min. razvoza, tako da vsem povezavam damo ceno 0, s prvotno kapaciteto, $t$ in $s$ pa povežemo s povezavo z neskončno kapaciteto in ceno $-1$.
> >
> >Ta problem je dopusten.
> >
> >Če velja da je problem neomejen sledi da je pretok neomejen oz. je kapaciteta vsakega prereza neskončna (iz prejšnjega izreka).
> >
> >Druga možnost je da je problem optimalen in ga rešimo preko simpleksne metode na omrežjih.
> >
> >Torej imamo $x_{e}$ za vsako povezavo in $y_{v}$ za vsako vozlišče.
> >
> >  Vemo da $ts$ ni nasičena $\Rightarrow$ $y_{t} + c_{ts} \geq y_{s}$
> >  
> >  *Če $ts$ ni v grafu je prazna ali pa je v grafu, torej velja neenakost.*
> >  
> >  Vemo da je $c_{ts} = -1$ torej je 
> >  
> >  $$y_{t} \geq y_{s}+1$$
> >  
> >  Definiramo $C = \{ v \in V \,;\; y_{v}\leq y_{s}\}$
> >  
> >  Velja da je $C$ prerez, saj velja
> >  
> >  $$s \in C \quad y_{s}\leq y_{s}$$
> >  $$t \notin C \quad y_{t}\geq y_{s}+1$$
> >  $$ $$
> >  $$i \in C, j \notin C \Rightarrow$$
> >  $$\Rightarrow y_{i}\leq y_{s}  \;\;,\;\,  y_{s} < y_{j} \Rightarrow$$
> >  $$\Rightarrow y_{i }< y_{j} \Rightarrow$$
> >  $$\Rightarrow \text{povezava $ij$ je nasičena}$$
> >  $$ $$
> >  $$i \notin C, j \in C$$
> >  $$y_{i}> y_{s} \quad  y_{s} \geq y_{j}$$
> >  $$y_{i} > y_{j}$$
> >  $$\Rightarrow \text{povezava $ij$ je prazna}$$
> >  
> >  $$ $$
> >  
> >  Če pogledamo
> >  
> >  $$\sum_{\substack{i \in C \\ j \notin C}} x_{ij} - \sum_{\substack{i \notin C \\ j \in C}} x_{ij} $$ 
> >  
> >  Vse leve vrednosti so nasičene, vse desne so prazne torej velja
> >  
> >  $$\sum_{\substack{i \in C \\ j \notin C}} x_{ij} - \sum_{\substack{i \notin C \\ j \in C}} x_{ij} = \sum_{\substack{i \in C \\ j \notin C}} u_{ij} - \sum_{\substack{i \notin C \\ j \in C}} 0$$
> >
> >Torej je prostornina pretoka enaka kapaciteti prereza, iz česar sledi da je **pretok maksimalen**

To lahko uporabimo za iskanje $\max$ pretoka.

Imamo $C = \{ s\}$.
Če je $i \in C, j \notin C,$ in velja da je $ij$ nenasičena, dodamo $j$ v $C$.
Če je $i \in C, j \notin C$ in je $ji$ neprazna, dodamo $j$ v $C$. 

S tem nadaljujemo. Če je $t \in C$, smo našli povečujočo pot. 
Če $t \notin C$, $C$ ne moremo več povečati. Takrat se ustavimo, $C$ je prerez in velja $i \in C, j \notin C \Rightarrow ij$  je nasičena, $i \notin C, j \in C \Rightarrow ij$ je prazna.

$$\sum_{\substack{i \in C \\ j \notin C}} x_{ij} - \sum_{\substack{i \notin C \\ j \in C}} x_{ij} = \sum_{\substack{i \in C \\ j \notin C}} u_{ij}$$

Torej imamo maksimalen pretok.


Običajno Ford-Fulkersonovega algoritem ne izvajamo na prvotnem grafu ampak na **priduženem grafu**. To je graf kjer za vsako povezavo $e$ ob nekem pretoku $x_{e}$ in omejtivi $u_{e}$ namesto usmerjene povezave napišemo neusmerjeno in na začetku damo $u_{e}-x_{e}$ na koncu pa $x_{e}$

To naredimo zato saj potem na vsaki povezavi gledamo levo številko ki je ta pomembna saj nam pove ali je povezava nasičena ali prazna

![[Pasted image 20260429230211.png|400]]

Da imamo povečujočo pot morajo biti na začetkih pozitivna števila.

**Opomba:** disjunknte poti lahko poiščemo v istem koraku.

***

Ford-Fulkersonov algoritem se ne konča nujno. Da se konstrurirati graf s 6 vozlišči in 8 povezavami in optimalno rešitvijo pri čemur izbiramo povečujoče poti v neskončnost. Prostornina konvergira vendar ne proti maksimalni prostornini.

Gotovo se konča če so kapacitete racionalne.

**Trditev:** Maksimalen tok vedno obstaja če so kapactitete končne in nenegativne.