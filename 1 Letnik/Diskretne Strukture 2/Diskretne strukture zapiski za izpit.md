
**Graf** je množica vozlišč in množica povezav med njimi

$$G = (V, E)$$

$V$ je **množica vozlišč**.
$E$ je **množica povezav**, katere elementi so podmnožice 2 vozlišč med katerimi je povezava.

$$E = \{\{ u,v\} \,;\;  u,v \in  V \,,\;u \neq v\}$$

Povezavo lahko zapišemo kot:

$$uv := \{ u,v\} := u \sim v$$

**Enostaven graf** je graf brez zank, vzporednih, in usmerjenih povezav. *Kjer so zanke povezazve same s seboj.*

**Komplement grafa** $G$ je $\overline{G}$ in velja

$$\overline{G} = (V, \overline{E})$$
$$\overline{E} = \{ uv \,;\; uv \notin E\}$$

**Matrika sosednosti** je kvadratna matrika, ki opisuje katera vozlišča grafa so med seboj povezana. 
Za graf $G = (V,E)\,;\; V = \{ v_{1},... v_{n}\}$
je velikosti $n \times n$, kjer je $A_{ij} = 1$, če obstaja povezava med vozliščema $v_{i}, v_{j}$ oz. 0 če ne obstaja.

Matrika je vedno simetrična, na diagonali ima same ničle (pri enostavnih), vsota vrednosti vrstic oz. stolpcev za vozlišče $v_{i}$ je enaka stopnji $v_{i}$.

**Incidenčna matrika** je matrika ki povezuje vozlišča in povezave grafa. 

Za graf $G = (V,E)$ z $n$ vozlišči in $m$ povezazavami je velikosti $n \times m$ kjer je $B_{ij} = 1$, če je vozlišče $v_{i}$ povezano s povezavo $e_{j}$ in $B_{ij} = 0$, če ni.

Vsak stolpec ima natanko 2 enici. Vsota vrednosti vrstic je enaka stopnji vozlišča $v_{i}$.

Za predstavitev grafa lahko uporabimo tudi **seznam sosedov**. Vsako vozlišče ima svojo množico sosednjih vozlišč s katerimi je povezano.

$$N_{G}(v) = \{ u \in  V \,;\; u \sim v\}$$
$$ (N_{G}(v_{1}),...,N_{G}(v_{n}))$$

**Stopnja vozlišča** je število povezav, katerim pripada vozlišče.
$$\deg_{G}u = \left|\{ e \,;\; u \in e\} \right|$$

**Maksimalna stopnja** $\Delta(G)$ je največja stopnja grafa.

**Minimalna stopnja** $\delta(G)$ je najmanjša stopnja grafa.


**Izolirano vozlišče** je nepovezano vozlišče oz. $\deg_{G}u = 0.$

***
>**Izrek o rokovanju** 
>Vsota stopenj vseh vozlišč je enaka dvakratniku števila povezav. 
>
>$$\sum_{v \in V}^{}\deg(v) = 2 |E|$$
>>[!|dokaz]- Dokaz:
>>Vsaka povezava prispeva 1 k stopnji dveh vozlišč.
>>Če seštevamo stopnje vseh vozlišč, vsako povezavo štejemo dvakrat - enkrat za vsako vozlišče, ki jo povezuje.
>>To pomeni da je vsota stopenj enaka dvakratniku števila povzav.
***
> $\Rightarrow$ V vsakem grafu je sodo število vozlišč lihe stopnje.
> >[!|dokaz]- Dokaz:
> > Uporabimo izrek o rokovanju, kjer vsoto stopenj vozlišč razdelimo na vsoto stopenj sodih in vsoto stopenj lihih vozlišč.
> > Vsota lihih števil je soda če je število lihih števil sodo.
> > Vsota sodih števil je soda.
> > $2|E|$ je sodo in vsota sodih stopenj je soda torej mora biti število lihih stopenj sodo.
***

$G$ je **$k$-regularen**, če je stopnja vsakega vozlišča $k$.
$3$-regularni grafi so **kubični**.

$$\text{Graf je regularen } \Rightarrow |V| \cdot k = 2x$$

**Sprehod** je zaporedje vozlišč $v_{0},...,v_{k} \in V_{G}$ tako da velja $v_{i} \sim v_{i+1}$.
**Dolžina sprehoda** je število povezav.

**Sklenjen sprehod** je sprehod kjer velja $v_{0} = v_{k}$.

**Enostaven sprehod** je sprehod kjer se nobena **povezava** ne ponovi.

**Pot** je sprehod, kjer se nobeno **vozlišče** ne ponovi.

**Cikel** je sklenjen sprehod, kjer se ponovi natanko prvo vozlišče.

**Ožina** grafa je dolžina najkrajšega cikla.

> Obstaja sprehod od $u$ do $v$ $\Rightarrow$ obstaja pot od $u$ do $v$.

> V $G$ obstajata 2 različni poti med $u$ in $v$ $\Rightarrow$ v $G$ obstaja cikel.

> Če v $G$ obstaja sklenjen sprehod lihe dolžine obstaja tudi cikel lihe dolžine.
> >[!|dokaz]- Dokaz:
> > **Predpostavimo da obstaja sklenjen sprehod $W = (v_{0}, v_{1},...,v_{k})$ lihe dolžine.**
> > 
> > Če je $W$ že cikel, je to cikel lihe dolžine.
> > 
> > Drugače pa lahko $W$ razdelimo na manjše sklenjene sprehode.
> > 
> > Recimo da se ponovi vozlišče $v_{i} = v_{j}$.
> > Velja da obstajata $W_{1} = (v_{i},...,v_{j})$ in $W_{2} = (v_{1},...,v_{i},v_{j+1},...,v_{k})$.
> > 
> > Ker vemo da je liho število vsota sodega in lihega števila velja da mora eden od njiju biti sodo in eno liho. Če se izkaže da je lihi sklenjen sprehod cikel lahko končamo. Drugače ponovimo isti postopek, dokler ne dosežemo lihega cikla.
***

**Razdalja med vozliščema** $[d(u,v)]$ je najkrajša pot med njima.

Če pot ne obstaja je $d(u,v) = \infty$

**Ekscentričnost** vozlišča $\text{ecc}(u) = \underset{v\, \in\, V}{\max}(d(u,v))$.

**Diameter** grafa je največja ekscentričnost v grafu: $\text{diam}(G).$

**Radij** je najmanjša ekscentričnost v grafu: $\text{rad}(G)$.

***
> Če $G$ ni povezan potem je $\text{dia}(\overline{G}) \leq 2$
> >[!|dokaz]- Dokaz:
> >**Predpostavimo da graf ni povezan**
> >
> > V nepovezanem grafu velja da obstaja tako vozlišče $u$, ki ni povezano z nobenim vozliščem povezanega dela. To pomeni da bodo vsa vozlišča iz povezanega dela v komplementu grafa povezana z $u$. To pomeni da če vozlišče ne bosta že direktno povezani, bo obstajal najkrajša pot med njima. Torej od $v$ do $u$ in do $v'$, ki je dolga 2.
> > 
> > Daljša pot ne more obstajati saj bo komplement povezanega dela vseboval direktne povezave in poti dolžine 2 do katerega koli vozlišča, ki ni povezano, enako pa bi bilo v drugem povezanem delu.
> > Torej je diameter komplementa nepovezanega grafa večji ali enak 2.

> Posledica: $G$ ali $\overline{G}$ je povezan
***

Urejen par $(V(G), d)$ je **metrični prostor**, kjer je $d$ **metrika**.

<br>

**Metrični prostor:**
$d: X \times X \rightarrow \mathbb{R}$. Za $d$ mora veljati da je:

$$d(x,y)\geq 0$$
$$d(x,y) = 0 \Leftrightarrow x = y$$
$$d(x,y) = d(y,x)$$
$$d(x,z) \leq d(x,y) + d(y,z)$$

s tem dobimo metrični prostor, $d$ pa je metrika

**Evklidski prostor:** 

$$d(x,y) = \sqrt[]{\sum_{i=1}^{n}(x_{i}-y_{i})^{2}}$$

**Diskretni metrični prostor:** 

$$d(x,y) = 1\Leftrightarrow x\neq y$$ 
$$d(x,y) = 0\Leftrightarrow  x = y$$

V grafih je $d$:

$$d(u,v) = \text{dolžina najkrajše poti med } u,v$$
$$d(u,v) \geq 0$$
$$d(u,v) = 0 \Leftrightarrow u = v$$
$$d(u,v) = d(v,u)$$
$$d(u,v) \leq d(u,z) + d(z,v)$$

$(G, d)$ tvorita metrični prostor.

***
$G$ je dvodelen (bipartite) graf če sta $X,Y$ disjunktni, 

$$X \cup Y = V(G)$$
$$x,y \in X \lor x,y \in Y \Rightarrow x \nsim y$$ 
$$\forall e : \left|e \cap X \right| = \left|e \cap Y \right| = 1$$

Če je graf dvodelen določimo tako da izberemo točko in njene sosede označimo potem pogledamo sosede sosedov in pogledamo ali jih moramo označiti, če moramo neko točko označiti dvakrat ni oz. označiti in pustiti na miru hkrati, pomeni da graf ni dvodelen. Če je točka bela morajo biti sosedi vsi črni (**Izrek o segregaciji**)
***


> Graf je dvodelen, natanko tedaj ko ne vsebuje nobenega lihega cikla
> >[!|dokaz]- Dokaz:
> > 
> > $\Rightarrow$
> > 
> > **Predpostavimo da je graf dvodelen in da obstaja razdelitev $V = V_{1} \cup V_{2}$**
> > 
> > Če obstaja cikle mora potekati izmenično iz $V_{1}$ v $V_{2}$. Da cikel obstaja se mora začeti in končati v isti množici, kar pa je možno le z sodim številom povezav, saj gremo z eno vedno v drugo množico in z drugo nazaj v prvo.
> > Zelo preprosto si lahko pomagamo tudi z izrekom o segregaciji.
> > 
> > $\Leftarrow$
> > 
> > **Predpostavimo da $G$ ne vsebuje cikel lihe dolžine**
> > 
> > Izberemo poljuben $v$ in ga damo v množico $V_{1}$.
> > 
> > Za vsako vozlišče $u$ definiramo njegovo razdaljo od $v$ kot dolžino najkrajše poti do $u$.
> > 
> > Vozlišča glede na razdaljo razdelimo v množici $V_{1}$ in $V_{2}$, kjer so tista z sodo razdaljo v $V_{1}$ in tista z liho pa v $V_{2}$.
> > 
> > Sedaj lahko vidimo da če obstaja cikel lihe dolžine imata vsaj 2 vozlišči isto razdaljo do $v$, in sta hkrati povezana, to pomeni da sta povezana vozlišča iz iste množice, mi pa vemo da $G$ ne vsebuje cikla lihe dolžine torej so vsa povezana le vozlišča
***


$H$ je **podgraf** če je $V_{H} \subset V_{G}$ in $E_{H} \subset E_{G}$, kjer so vse povezave v $E_{H}$ le med vozlišči $V_{H}$.

$H$ je **vpet podgraf** če velja da je $V_{H} = V_{G}$ oz. smo odstranili le povezave.

$H$ je **induciran podgraf** če velja da ob izbiri podmnožice vozlišč, ta ohranjajo vse medsebojne povezave originalnega grafa, torej smo odstranili le vozlišča.

**Odstranjevanje povezav:**

$$F \subset E$$
$$G - F = (V, E\backslash F)$$

**Odstranjevanje vozlišč:**

$$U \subset V$$
$$G-U = (V\backslash U, E \cap \{ \{ u,v\} \;;\; u,v \notin U \})$$



$H$ je podgraf $G$ $\Rightarrow$ $H = (G - U) - F$ 

**Skrčitev povezave $e$** je $G\backslash e$, kjer odstanimo povezavo med $u,v$ in $u,v$ ter  ustvarimo $v'$ kot novo vozlišče in ga povežemo z vsemi vozlišči ki so bila prej povezana z $u, v$ in odstranimo vse večkratne povezave do $v'$.

$$>\!\!\!-\!-\!\!\!<\;\; \rightarrow \;\;>\!\!<$$

$H$ je **minor** grafa $G$, če smo nekemu podgrafu $G' \subset G$ skrčili povezave. Torej če je $H = G' \backslash E'$, $E' \subset E_{G}$.

Primer skrčitve je $K_{5}$ kot skrčenje petersonovega grafa.

Graf $H$ je **subdivizija** grafa $G$ če nekatere povezave zamenjamo s potmi dolžine 2 in novim vozliščem.

**Glajenje povezav** je postopek kjer vozlišče stopnje 2 odstranimo ter povežemo njuna soseda.

Grafa $G_{1}$ in $G_{2}$ sta **homeomorfna**, če dobimo izomorfizem grafa $G_{1}$, ko zgladimo vse povezave $G_{2}$. *Če lahko iz $G_{1}$ dobimo graf $G_{2}$ s subdivizijo.*

***

Graf je **povezan** če za vsak par vozlišč obstaja pot med njima.

**Komponenta grafa** je tak podgraf za katerega velja da za vse  pare vozlišč $G$ velja, da če sta v množici podgrafa potem obstaja pot med njima.

$$u,v \in V \land \exists P(u,v) \Rightarrow u,v \in V' \land E(P(u,v)) \in E'$$

**Število komponent**: $\Omega(G)$ 

**Povezan graf** je graf z eno komponento.
Če graf ni povezan ga sestavlja več komponent.

Definiramo **relacijo med vozlišči** če obstaja pot med njima. Le ta je tudi **ekvivalenčna**.

**Ekvivalenčni razredi** te relacije so **povezane komponente**.

Vozlišče $v$ je **prerezno vozlišče** če velja da je število komponent v grafu manjše z vozliščem.

$$\Omega(G-v) > \Omega(G)$$

Povezava $e$ je **prerezna povezava** če velja da je števil komponenta v grafu s povezavo manjše. 

$$\Omega(G-e) > \Omega(G)$$


***
> Pri prereznem vozlišču se lahko število komponent poveča za največ $\deg(v)-1$, pri prerezni povezavi pa za največ 1
> >[!|dokaz]- Dokaz:
> > Ob odstranitvi povezave med vozlišči ostaneta 2 nepovezani ali povezani vozlišči preko druge povezave torej lahko nastane kvečjemu 1 nova komponenta.
> > Pri odstranjevanju vozlišča odstranjujemo $\deg (v)$ povezav, vsaka od katerih lahko poveča število komponent za največ 1 minus komponenta, ki nastane ob izoliranem vozlišču, ki ga odstranimo kar je $\deg(v) -1$.
***
$S \subset V(G)$ je prerezna množica če je $\Omega(G-S)>\Omega(G)$

$F \subset E(G)$ je povezavno prerezna množica če je $\Omega(G-F) > \Omega(G)$

$G$ je **$k$-povezan**, če je $\left|V_G \right| \geq k+1$ in ima vsaka prerezna množica vsaj $k$ elementov. *Odstraniti moramo najmanj $k$ vozlišč da dobimo več komponent.*

***
> Če je graf $k$-povezan je $k$ in $k-1$ povezan hkrati

***

$\mathcal{K}(G) :=\,$ povezanost grafa $G$ oz. največja $k$-povezanost grafa oz. najmanjše število vozlišč ki jih je treba odstaniti da dobimo nepovezan graf $G$

$\mathcal{K}(P_{n}) = 1$

$\mathcal{K}(C_{n}) = 2$

$\mathcal{K}(K_{n}) = n-1$

Poti $P_{1}$ in $P_{2}$ z začetkom v $v$ in koncem v $u$ sta **notranje disjunktni** če sta $u$ in $v$ edini skupni vozlišči.

***
>**Whitnejev izrek**: G z vsaj 3 vozlišči: G je $2$-povezan $\Leftrightarrow$ med poljubnimi vozlišči obstajata notranje disjunktni poti

***
>**Mengerjev izrek**: Graf z vsaj $k+1$ vozlišči je $k$ povezan natanko tedaj ko med poljubnimi vozlišči obstaja vsaj $k$ notranje disjunktnih poti.
>>[!|dokaz]- Dokaz:
>> $\Rightarrow$
>> 
>>  **Predpostavimo da je graf $k$-povezan**
>>
>>  Naj bosta $u$ in $v$ poljubni vozlišči v grafu $G$.
>>  
>>  Ker je graf $k$-povezan mora biti povezan po odstranitvi $k-1$ vozlišč (razen $u$ in $v$)
>>
>> Najdemo $k-1$ notranje disjunktnih poti tako da vsakič ko najdemo pot zbrišemo njena vozlišča.
>> 
>> Če je graf postal nepovezan smo v protislovju saj lahko iz vsake disjunknte poti vzamemo eno točko in jo odstranimo s čimer smo odstranili $k-1$ ali manj točk, graf, je postal nepovezan kar je protislovje s $k$-povezanostjo.
>> 
>> Če je graf ostal povezan po $k-1$ disjunktnih poti smo našli še $k$-to pot.
>> 
>>  $\Leftarrow$
>>  
>>  **Predpostavimo da je med $u$ in $v$ $k$ notranje disjunktnih poti**
>>  
>>  To pomeni da če odstranimo manj kot $k$ vozlišč, bi zagotovo ostala ena disjunktna pot ki povezuje $u$ in $v$ kar pomeni da bi graf ostal povezan.
>>  
>>  To pa pomeni da moramo odstraniti vsaj $k$ točk, kar je definicija $k$-povezanosti.
***

> **Mengerjev** **(lokalen)** : Največje število notranje disjunktnih poti med $u$ in $v$ je enako velikosti najmanjše prerezne množice za katero sta $u$ in $v$ v različnih komponentah.
***

***
Naj bosta $G,H$ grafa. 
**Homomorfizem grafov** je preslikava 

$$\varphi : G \rightarrow H $$
$$ V_{H} \mapsto V_{H}$$ 

tako da velja

$$u \sim v \Rightarrow \varphi(u) \sim \varphi(v)$$

Če je $\varphi$ surjektivna je **epimorfizem**.

Če je $\varphi$ injektivna je **monomorfizem** oz. **vložitev**. 

Če za $\varphi$ velja $d(u,v) = d(\varphi(u), \varphi(v))$ je to **izometrična vložitev**.

Če je $\varphi$ bijektivna in velja $u \sim v \Leftrightarrow \varphi(u) \sim \varphi(v)$ potem pravimo da je $\varphi$ **izomorfizem.**

**Izomorfizem** je bijektiven homomorfizem katerega inverz je homomorfizem.

Če je graf izomorfičen drugemu pišemo

$$G \cong H$$

**Avtomorfizem** grafa je izomorfizem 

$$\varphi : G \rightarrow G$$
$$V_{G} \mapsto V_{G}$$

$\text{Avt}(G)$ je množica vseh avtomorfnih funkcij grafa $G$.

$$\left|\text{Avt}(K_{n}) \right| = n!$$
$$\left|\text{Avt}(C_{n}) \right| = 2n$$

| Koncept            | Tip preslikave | $v_{i} \sim v_{j}$ |
| :----------------- | :------------- | :----------------- |
| **Homomorfizem**   | Poljubna       | $\Rightarrow$|
| **Epimorfizem**    | Surjektivna    | $\Rightarrow$|
| **Monomorfizem**   | Injektivna     |$\Rightarrow$|
| **Izometrična vložitev** | Injektivna |$\Leftrightarrow$|
| **Izomorfizem**    | Bijektivna | $\Leftrightarrow$|
| **Avtomorfizem**   | Izomorfizem | $\Leftrightarrow$|

***

> Če sta $\varphi_{1} : G_{1} \rightarrow G_{2}$ in $\varphi_{2} : G_{2} \rightarrow G_{3}$ homomorfizma je tudi $\varphi_{2} \circ \varphi_{1}$ homomorfizem
> >[!|dokaz]- Dokaz:
> > Če $\varphi_{1}$ ohranja sosdesnot velja da bosta $u$ in $v$ povezani natanko takrat ko sta $\varphi_{1}(u)$ in $\varphi_1(v)$ povezana. Ker $\varphi_{2}$ ohranja povezanost pomeni da bosta $\varphi_{2}(\varphi_{1}(u))$ in $\varphi_{2}(\varphi_1(v))$ tudi povezana. Ker je ohranjenja sosednost grafa je kompozitum tudi homomorfizem.
***
> $$\text{Avt}(G) = \text{Avt} (\overline{G})$$
> >[!|dokaz]- Dokaz:
> > Če avtomorfizem ohranja sosednost potem hkrati ohranja nesosednost. Torej je ohranjanje nesosednost v $G$ ekvivalnentno ohranjanju sosednosti v $G$.
> > Torej mora biti število vseh avtomorfizmov obeh grafov enaka.


***

Graf je **gozd** če nima ciklov.

Povezan graf je **drevo**, če nima ciklov.

Komponenta gozda so **drevesa**.

**List** je vozlišče stopnje 1.
***
> Vsako drevo z vsaj 2 vozliščema ima list.
> >[!|dokaz]- Dokaz:
> > Ker je vsako vozlišče povezano preko natanko ene poti velja da obstajata robni vozlišči stopnje 1 za vsako drevo.
***
> Gozd $|E_{G}| = |V_{G}| - \Omega (G)$
> >[!|dokaz]- Dokaz:
> > Za vsako komponento odštevamo 1, torej odštejemo število komponent.
***
> V drevesu z vsaj 2 vozliščema sta vsaj 2 lista
***
> $G$ je povezan graf in $e$ je povezava na nekem ciklu
>  potem je $G\backslash e$ tudi povezan graf.  
***
>$|E_{G}| = |V_{G}|-1 \Leftrightarrow G$ je drevo
***
Naslednje trditve so ekvivalentne:

$\Leftrightarrow$ med poljubnimi vozlišči $G$ obstaja natanko 1 pot
$\Leftrightarrow$ $G$ je drevo
$\Leftrightarrow$ $G$ je povezan, vrsta povezave je **most**
$\Leftrightarrow$ $G$ je povezan, št. povezav je $|E_{G}| = |V_{G}| - 1$

**Most** je povezava, ki razdeli graf na 2 komponenti.

$T$ je **vpeto drevo** grafa $G$ če je drevo in je vpet podgraf grafa $G$.

**$\tau (G):\,$** število vpetih dreves grafa

***
> Graf je povezan natanko tedaj ko obstaja vpeto drevo $G$ oz. 
> 
> $$\tau(G)\geq 1 \Leftrightarrow \text{graf je povezan}$$ 
> >[!|dokaz]- Dokaz je trivialen

***
> Obstaja rekurzivna zveza za $\tau(G)$ kjer je $G$ multigraf (to pomeni da dovolimo večkratne povezave) : 
> 
> $$\tau(G) = \tau (G-e)+ \tau (G\backslash e)$$
> >[!|dokaz]- Dokaz:
> >  Intuicija je da je $G-e$ graf ki vsebuje vpeta drevesa, ki ne vsebujejo povezave $e$. (Tista vpeta drevesa, ki jih najdemo v $G$, ki nimajo $e$).
> >  
> >  $G\backslash e$ pa je graf, ki vsebuje vpeta drevesa, ki vsebujejo povezavo $e$. (To pomeni da če v grafu $G$ najdemo vpeto drevo, ki vsebuje $e$ bo le to ob skrčitvi $e$ še vedno obstajalo, le z eno povezavo manj saj smo prej recimo šli do vozlišča $A$, sedaj pa je le to vozlišče neko $A'$, ki je nastalo ob skrčitvi. V $G\backslash e$ pa ni nobenega vpetega drevesa, ki ne bi vseboval $e$, ker je povezava postala vozlišče, kar pomeni da drevo, ki ni vsebovalo povezave $e$, dobi cikel namesto $e$, kar pomeni da ni več vpeto drevo. ) *Ko se ti da lahko to boljš opišeš //tba*

***

**Laplaceova matrika** je matrika, ki vsebuje stopnjo vozlišč na diagonali in -št. povezav med $v_{i}$ in $v_{j}$ na $i,j$ tem mestu.

$$L(G) \in \mathbb{R}^{n \times n} \,;\; n = |V_{G}|$$
$$L(G)_{ij} = 
\begin{cases}
\deg(v_{i}) \,;\; i = j\\ 
-(\text{št povezav med }v_{i},v_{j}) \,;\; i \neq j
\end{cases}
$$

Prva lastnost je da je vsota elementov vrstic in stolpcev enaka 0.

Druga lastnost je da je determinanta $L_{ii}$ enaka številu vpetih dreves grafa. Kjer je $L_{ii}$ matrika, ki jo dobimo ko odstranimo $i$-ti stolpec in vrstico.

Tretja lastnost je da je simetrična.

Četrta lastnost je da je determinatna matrika 0.
***
> **Cayleyjev izrek**
> $$\tau(K_{n}) = n^{n-2}$$
> >[!|dokaz]- Dokaz
> >1\. Izpeljava je iz Kirchhoffove matrike
> >  
> >2\. Pruferjevo kodiranje:
> >
> > Za dano vpeto drevo z $n$ vozlišči konstruiramo zaporedje dolžine $n-2$ imenovano Pruferjeva koda.
> > 
> > 
> >- Najdemo list (vozlišče s stopnjo 1) z najmanjšo oznako.
> >- Dodamo njegovega soseda v Pruferjevo kodo.
> >- Odstranimo list iz drevesa.
> > - Postopek ponavljamo, dokler ne ostaneta samo dve vozlišči.
> >-  Pruferjeva koda je zaporedje $n - 2$ števil, kjer je vsako število med $1$ in $n$.
> >
> > Bijekcija:
> >- Vsaka Pruferjeva koda dolžine $n - 2$ ustreza natanko enemu vpetemu drevesu.
> >- Ker je število možnih Pruferjevih kod enako $n^{n-2}$ sledi, da je število vpetih dreves tudi $n^{n-2}$.

***
**Eulerjev sprehod** je sprehod, ki gre skozi vsako povezavo natanko enkrat.
**Eulerjev obhod** je sklenjen Eulerjev sprehod.
Graf je **eulerjev** če ima eulerjev obhod.

>  Povezan graf je eulerjev natanko tedaj, ko so vsa vozlišča soda.
>  >[!|dokaz]- Dokaz:
>  >
> > $\Rightarrow$
> > 
> > **Predpostavimo da so vsa vozlišča soda**
> > 
> > Vsakič ko Eulerjev obhod vstop v vozlišče $v$ mora tudi izstopiti iz njega kar pomeni da je število vstopov in izstopov enako, vsak od katerih porabi eno povezavo, zato mora biti stopnja vozlišča soda in posledično stopnja vseh vozlišč v grafu soda.
> > 
> > $\Leftarrow$
> > 
> > **Predpostavimo da je graf eulerjev**
> > 
> > Ker so vsa vozlišča soda lahko začnemo s poljubnim vozliščem in sledimo povezavam pri čemer ne uporabimo iste povezave dvakrat, ker so vsa vozlišča soda lahko vstopimo in izstopimo iz vozlišča razen v začetnem kjer so obhod konča. Ta postopek zagotovi da gremo čez vsako povezavo natanko enkrat kar pomeni da je graf eulerjev.

> $G$ ima eulerjev sprehod natanko tedaj ko sta največ 2 vozlišča lihe stopnje in so vse povezave v eni komponenti. (Graf se začne v enem lihem in konča v drugem lihem)
> >[!|dokaz]- Dokaz je trivialen

**Hamiltonova pot** je pot, ki mora iti skozi vsako vozlišče grafa natanko enkrat.
**Hamiltonov cikel** je cikel, ki mora iti čez vsako vozlišče grafa natanko enkrat. 
*(Sklenjena hamiltonova pot)*
Graf je **hamiltonov** če vsebuje hamiltonov cikel.

Za manjše grafe jih iščemo s preverjanjem vseh možnosti. Za večje pa ne obstaja alogritem, ki bi rešil ta problem za vse grafe v polinomskem času.

> Če je $G$ hamiltonov graf in $(S \subset V_{G}) \neq \emptyset$ potem je število komponent brez $S$ manjše ali enako številu elementov $S$ oz.
> $$\text{graf je hamiltonov} \Rightarrow\Omega(G-S) \leq |S|$$
> >[!|dokaz]- Dokaz:
> > Če odstranimo $|S|$ vozlišč se cikel razbije na največ $|S|$ poti, ker vsako odstranjeno vozlišče prereže cikel $C$ na enem mestu.

> Če obstaja $S$ da je $\Omega(G-S) > |S| \Rightarrow$ graf ni hamiltonov.
> 
>*Zgornji pogoj je potreben a ne zadosten (obstajajo grafi, ki izpolnjujejo neenakost a niso hamiltonovi.)*


> Če obstaja $S$ da je $\Omega(G-S) > |S|+1 \Rightarrow$ graf nima hamiltonove poti

> $G$ je dvodelen in hamiltonov $\Rightarrow$ $|X| = |Y|$

> Če vemo da je vsota stopenj vsakih 2 nepovezanih in neenakih vozlišč večja ali enaka številu vozlišč $u, v$ potem velja da je graf hamiltonov natanko tedaj ko je $G + \{uv\}$ hamiltonov graf oz.
> $$\forall u,v \ni: u \neq v \land u \nsim v$$
> $$ \deg(u) + \deg(v)\geq |V| $$ 
> $$\Rightarrow $$ 
> $$G \text{ je hamiltonov} \Leftrightarrow G + \{ uv\} \text{ je hamiltonov}$$
> >[!|dokaz]- Dokaz:
>> Če grafu dodamo povezavo jo lahko le ignoriramo in je graf še vedno hamiltonov.
>> Če grafu odstanimo $uv$ in ga ne uporabljamo v ham. ciklu vse deluje. Če pa je $uv$ prisoten v ham. ciklu lahko konstruiramo ham. cikel brez $uv$, saj velja da je $\deg(u) + \deg(v) \geq |V|$ kar pomeni da obstajata vsaj 2 vozlišči ki sta sosdenji $u$ in $v$ hkrati po katerem lahko njuno povezavo obidemo.

> Orejev izrek: Naj bo $G$ povezan graf z $n \geq 3$ vozlišči. Če za vsaki dve nepovezani vozlišči $u$ in $v$ velja 
> $$\deg(u) + \deg(v) \geq n$$
> potem je $G$ hamiltonov.
> >[!|dokaz]- Dokaz spet temlji na obstoju vozlišča ki povezuje $uv$

> Diracov izrek: če ima vsako vozlišče v grafu z vsaj 3 vozlišči stopnjo vsaj $n/2$ potem je graf hamiltonov.
> >[!|dokaz]- Dokaz spet temelji na obstoju vozlišča za neko povezavo ki poveže obe vozlišči prisotni v povezavi.

$$ $$
$\delta (G) :=$ minimalna stopnja vozlišča grafa $G$


> Diracov izrek lahko zapišemo 
> $$\delta(G) \geq \frac{|V_{G}|}{2}$$
***

### Znani / pomembni grafi

**Polni graf** $[K_{n}]$ je graf v katerem so vsa vozlišča povezana med sabo.

$$V = [n] \;\;\;\;\;E = \{ i\sim j \,;\; i \neq j \land i,j \in V\}$$ 
$$|E(K_{n})| = \frac{n(n-1)}{2} $$

je $n-1$ povezan, $n-1$ regularen, premer je $1$, vsebuje hamiltonove, eulerjeve cikle in poti

**Pot** $[P_{n}]$ je graf v katerem so povezana samo zaporedna vozlišča.

$$V = [n] \;\;\;\;\;E = \{ i \sim (i+1) \,;\; i \in \{ 0,...,n\}\}$$

$$|E(P_{n})| =n-1 $$

je $1$-povezan, ni regularen, premer je $n-1$, izomorfen dvodelnemu grafu 

**Cikel** $[C_{n}]$ je graf kjer so povezana samo zaporedna vozlišča ter prvo in zadnje.

$$V = [n] \;\;\;\;\;E = \{ i \sim j \,;\; i-j = 1 \lor j-i = 1\}$$
$$|E| = n-1$$

je $2$-povezan, premer je $⌊n/2⌋$, je dvodelen če je $n$ sodo

**Hiperkocka** $[Q_{n}]$ je graf, ki predstavlja $n$-dimenzionalno kocko.

$$V = \{ (\varepsilon_{1} ... \varepsilon_{n}) \,;\; \varepsilon_{i} \in \{ 0,1\}\} $$ 
$$E = \{ (\varepsilon_{1} ... \varepsilon_{n}) \sim (\delta_{1}...\delta_{n}) \,;\; \text{razlikujeta v samo enem mestu}\}$$
$$|E| = n2^{n-1}$$

Vozlišča so binarni listi, dolžine $n$, povezave pa so tvorjene med tistimi vozlišči, ki se razlikujejo v natanko eni števki. 
Ob večanju $n$ se nova števka postavi na konec lista.

Ima $2^{n}$ vozlišč in je $n$-regularen graf torej ima $n2^{n-1}$ povezav.

Je dvodelni graf, kjer vozlišča lahko razdelimo po tem da imajo liho število enic, sodo število enic.

Za $n\geq 2$ vedno vsebuje hamiltonov cikel in hamiltonovo pot.
Ima Eulerjev cikel če je $n$ sodo število.

2 vozlišči sta tako oddaljeni kot se razlikujeta v številu števk.

**Polni dvodelni graf** $[K_{m,n}]$ je graf, kjer je množica vozlišč razdeljena na 2 disjunktni podmnožici, kjer so vozlišča povezana le iz ene množice v drugo, povezave med vozlišči v isti podmnožici pa ne obstajata.

$$V = [m] \times \{ 0\} \cup [n] \times \{ 1\}$$
$$E = \{ (i,j) \sim (i',j') \;;\; j \neq j' \}$$
$$|E| = mn$$

**Posplošeni petersonov graf** $[P_{n,k}]$ je graf tvorjen iz $C_{n}$ in $G_{n}$ z množico vozlišč, ki se porazdeli v $C_{n}$ in $G_{n}$, tako da so v $C$ in $G$ indeksi od $1$ do $n$, kjer je $C_{n}$ cikel indeksov, vsako $i$ vozl. iz $C$ je povezano z vsakim $i$ vozl. iz $G$, povezave v $G_{n}$ pa so tvorjene med vozlišči, katera razlika je enaka $k$ po modulu.

$$V(P_{n,k}) = \{ u_{1},...,u_{n},v_{1},...,v_{n}\}$$
$$A = \{ u_{i} \sim u_{i+1} \land u_{1} \sim u_{n}\}$$
$$B = \{ u_{i} \sim v_{i}\}$$
$$C = \{ v_{i} \sim v_{\,i+k \;(\text{mod } n)}\}$$
$$E(P_{n,k}) = A \cup B \cup C$$
$$|E| = 3n$$

Večina jih ima hamiltonov cikel, klasični ga nima.
Večina jih ima hamiltonovo pot.
Noben nima eulerjevega cikla.
Noben nima eulerjeve poti.


Petersonov graf je $P_{5,2.}$


***

**Ravninski graf** je tak graf, ki ga lahko narišemo brez sekanja povezav. 

$$\varphi : V \rightarrow \mathbb{R}^{2} \text{ je injektivna}$$

$$\forall e \in  E \,,\Psi_{e} : [0,1] \rightarrow \mathbb{R}^{2} \text{ je zvezna}$$
$$e = uv, \Psi_{e}(0) = \varphi(u)$$
$$\Psi_{e}(1) = \varphi (u)$$

*Injektivnost je zahtevana da se vozlišče ne slikata v isto točko. $\Psi$ povezavo predstavlja kot krivuljo v ravnini - povezuje $\varphi(u)$ in $\varphi(v)$ kjer je vrednost na 0 in 1 enaka usstreznim $\varphi$ preslikavam v $\mathbb{R}^{2}$.*

Za ravninske grafe torej velja da se $\Psi_{e}$ ne sekajo, razen v vozliščih.


> Jordanov izrek: Enostavna sklenjena krivulja razdeli $\mathbb{R}^{2}$ na 2 območji.
> $\Psi(0) = \Psi(1)$ *neka sklenjena krivulja*

Naj bo $G$ graf vložen v ravnino *(t.j. ravninski s podano neko sliko grafa)*. Če odstranimo iz $\mathbb{R}^{2}$ slike vozlišč in povezav dobimo območja njegove povezanih komponent. Le-te imenujemo **lica**. (ang. face)

$F_G$ je množica vseh lic, $f$ je lice.

$l(f) :=$ št. povezav na robu lica oz. **dolžina lica**

> Dolžina vseh lic je dvakrat večja od števila robov.
> $$\sum_{f \,\in\, F_{G}}l(f)= 2|E_{G}|$$

Ožina grafa $g(G)$ je dolžina najkrajšega cikla. (V gozdu je $g(G) = \infty$)

>Dolžina vseh lic je večja ali enaka dolžini najkrajšega cikla.
> $$l(F) \geq g(G)$$
> Iz tega sledi da je
> $$2|E_{G}| \geq g(G)\cdot |F_{G}| \,;\; G\text{ ni gozd}$$
***
> Eulerjeva formula: $G$ je ravninski graf
> $$|V_{G}| - |E_{G}| + |F_{G}|= \Omega(G) +1$$
> Če imamo $|V_{G}|$ vozlišč imamo toliko komponent. Če neki vozlišči povežemo zguibimo eno komponento, če povežemo te povezave v lice, pridobimo komponento. Vedno prištejemo 1 na desni ker imamo vedno 1 lice torej v resnici odštevamo 1 na levi ker je $F_{G}$ vedno 1 ali več čeprav to lice ni komponenta.
> >[!|dokaz]- Dokaz se gre z indukcijo po številu ciklov grafa. tba

> Če je $G$ ravninski graf, ki ni gozd velja
> $$|E_{G}| \leq \frac{g(G)}{g(G)-2}(|V_{G}|-2)$$
> >[!|dokaz]- Dokaz:
> > $$2 \leq 1 + \Omega(G) = |V_{G}| - |E_{G}| + |F_{G}| $$
> > $$1 + \Omega(G) \leq |V_{G}| - |E_{G}| + \frac{2|E_{G}|}{g(G)}$$
> > $$\Rightarrow \left(1-\frac{2}{g(G)}\right)|E_{G}| \leq V_{G} - 2 $$
> 
> Iz tega sledi da če je
> - $|V_{G}| \geq 3$, 
>  - $G$ je ravninski, 
> - nima trikotnikov
> - $\Rightarrow|E_{G}| \leq 2(|V_{G}|-2)$, 
> $$ $$ 
> - $|V_{G}| \geq 3$, 
>  - $G$ je ravninski, 
> - ima trikotnike
> - $\Rightarrow|E_{G}| \leq 3(|V_{G}|-2)$, 

> $K_{5}$ in $K_{3,3}$ nista ravninska

> Graf je ravninski $\Leftrightarrow$ ne vsebuje podgrafa, izomorfnega sobdiviziji $K_{5}$ ali $K_{3,3}$
> *Uporaben za dokazaovanje da graf ni ravninski*

> Graf je ravninski $\Leftrightarrow$ $K_{5}$ in $K_{3,3}$ nista njegova minorja

***

$G$ je graf in $K$ množica barv. 
**Barvanje grafa** $C$ je preslikava 

$$b: V(G) \rightarrow K$$

Barvanje je **dobro**, če velja 

$$u \sim v \Rightarrow b(u) \neq b(v)$$

**Kromatično število** $\chi(G)$ je najmanjšte število barv s katerim je graf dobro pobarvan.

$\Huge{\chi}\!\!$ $(K_{n}) = n$,
$\Huge{\chi}\!\!$ $( \overline{K_{n}} ) = 1$,
$\Huge{\chi}\!\!$ $(P_{n}) = 2$,

$\Huge{\chi}\!\!$ $(C_n ) = \begin{cases}2 \;;\, \text{sodo} \\3 \;;\, \text{liho}\end{cases}$
$\Huge{\chi}\!\!$ $(P) = 3$

> ${\Huge{\chi}}\!(G)  \leq 2 \Leftrightarrow G \text{ je dvodelen}$

> $H$ je podgraf $G$ $\Rightarrow$ ${\Huge{\chi}\!}(H) \leq {\Huge{\chi}\!}(G)$
> >[!|dokaz]- Dokaz:
> > če je $b$ dobro barvanje bo tudi $b|_{V_{H}}$ dobro barvanje
***

**Klika** grafa je polni podgraf npr. povezava (2), trikotnik (3)
**Velikost največje klike** je $\omega(G)$



Za barvanje poznamo **požrešno metodo barvanja** kjer za vsako vozlišče vse pobarvamo z neko novo barvo razen če to ne gre, ko uporabimo novo barvo za tiste za katere ne gre.



> Velikost največje klike je manjša ali enaka kromatičnemui številu kar je manjše ali enako največji stopnji grafa + 1. 
> $$\omega(G)\leq{\Huge{\chi}\!}(G) \leq \Delta(G) + 1$$
> Ena prištevamo ker mora imeti vozlišče poleg barv za sosede še barvo zase. 
> Velikost največje klike pa je omejuje spodaj, ker polni graf zahteva toliko barv kolikor elementov je v povezanem grafu saj so vse povezhane med sabo torej morajo biti vsi različnih barv.

> Za vsak povezan graf ki ni lih cikel ali polni graf velja
> $$\omega(G) \leq \,{\Huge{\chi}\!}(G) \leq \Delta(G)$$

Če imamo nek zemljevid ki ga barvamo tako da nobena sosednje območje ni enake barve bo graf ki ga dobimo ravninski.

Spodnje trditve veljajo za ravninske grafe:
> $${\Huge{\chi}\!}(G) \leq  5$$
> >[!|dokaz]- Dokaz z indukcijo tba

> $${\Huge{\chi}\!}(G) \leq  4$$
> >[!|dokaz]- Dokaz z uporabo računalnika 1976 Appel Hagem (2005) preveril COG
***
**$P_{G}(k)$**$\;:=$ število dobrih barvanj grafa s $k$ barvami 


- $P_{\overline{K}_{n}}(k) = k^{n}$
- $P_{K_{n}}(k) = k(k-1)...(k-n+1)$

> Število dobrih barvanj grafa brez povezave je enako originalnemu številu plus številu s skrčeno povezavo
> $$P_{G-e}(k) = P_{G}(k) + P_{G\backslash e}(k)$$
> >[!|dokaz]- Basically gledamo število pobarvanj kjer sta vozlišči kjer smo odstanili povezavo iste barve ($P_{G}(k)$) in število pobarvanj kjer sta enako pobaravni ($P_{G\backslash e}(k)$)


<br>

**Kromatični Polinom**

Namesto da iščemo samo *minimalno* število barv, se lahko vprašamo, na *koliko načinov* lahko graf $G$ dobro pobarvamo s $k$ barvami.

**Definicija:** Naj bo $G=(V, E)$ graf in $k \in \mathbb{N}$. **Kromatični polinom** grafa $G$, označen s $P_G(k)$, je funkcija, ki za dani $k$ pove število različnih dobrih barvanj vozlišč grafa $G$ z barvami iz množice $\{1, 2, \dots, k\}$.

*Primeri:*
*   $G = N_n$ (graf brez povezav z $n$ vozlišči): Vsako vozlišče lahko pobarvamo neodvisno s katero koli od $k$ barv. Torej $P_{N_n}(k) = k^n$.
*   $G = K_n$: Prvo vozlišče lahko pobarvamo na $k$ načinov, drugo na $k-1$ načinov, ..., $n$-to na $k-n+1$ načinov. Torej $P_{K_n}(k) = k(k-1)(k-2)\dots(k-n+1)$. To je padajoča fakulteta $(k)_n$.
*   $G = P_3$ (pot z vozlišči $v_1, v_2, v_3$ in povezavama $\{v_1,v_2\}, \{v_2,v_3\}$):
    *   $v_1$ lahko pobarvamo na $k$ načinov.
    *   $v_2$ mora imeti drugo barvo kot $v_1$, torej $k-1$ načinov.
    *   $v_3$ mora imeti drugo barvo kot $v_2$. Koliko možnosti je? Odvisno od barve $v_1$. Ampak ne, $v_3$ mora biti le drugačen od $v_2$. Torej imamo spet $k-1$ možnosti za $v_3$.
    *   Skupaj: $P_{P_3}(k) = k(k-1)(k-1) = k(k-1)^2 = k^3 - 2k^2 + k$.

Opazimo, da so vsi ti primeri polinomi v spremenljivki $k$. To velja na splošno.

**Lastnosti kromatičnega polinoma $P_G(k)$:**
Naj bo $G$ graf z $n$ vozlišči in $m$ povezavami.
1.  $P_G(k)$ je polinom v $k$ stopnje $n$.
2.  Vodili koeficient (pri $k^n$) je 1.
3.  Konstantni člen je $P_G(0) = 0$.
4.  Koeficient pri $k^{n-1}$ je $(-|E|)$
5.  Koeficienti alternirajo v predznaku: $P_G(k) = a_n k^n - a_{n-1} k^{n-1} + a_{n-2} k^{n-2} - \dots + (-1)^{n-1} a_1 k$, kjer so $a_i \ge 0$ za $i=1, \dots, n$.
***
**Dobro barvanje povezav grafa** je 

$$b : E_{G} \rightarrow K$$
$$e \neq f, e\cap f \neq \emptyset \Rightarrow b(e) \neq b(f)$$

**Najmanjše število barv s katerimi lahko pobarvamo povezave grafa:**

$${\Huge{\chi}\!}'(G)$$

imenujemio **kromatični indeks.**

- ${\Huge{\chi}\!}'(P_{n}) = 2$
- ${\Huge{\chi}\!}'(C_{n}) 0 \begin{cases}2\,; \text{ sod}\\3\,; \text{  lih}\end{cases}$
- ${\Huge{\chi}\!}'(K_{1}) = 0$, ${\Huge{\chi}\!}'(K_{2}) = 1$, ${\Huge{\chi}\!}'(K_{3}) = 3$, ${\Huge{\chi}\!}'(K_{4}) = 3$, ${\Huge{\chi}\!}'(K_{5}) = 5$, ${\Huge{\chi}\!}'(K_{6}) = 5$

> Kromatični indeks je večji ali enak največji stopnji grafa
> $${\Huge{\chi}\!}'(G) \geq \Delta(G)$$

$\Rightarrow$

> $$ n-1 \leq {\Huge{\chi}\!}'(K_{n}) \leq n$$
> $$b: b(ij) = (i+j)\!\!\!\mod n \,;\; b(ij)\neq b(ih)$$



***

Dobro barvanje povezav grafa $G$ je preslikava $b: E(G) \to k$, tako da velja: če sta $e, f \in E(G)$ različna (t.j. $e \neq f$) in imata skupno krajišče, potem $b(e) \neq b(f)$. Najmanjše število barv, s katerimi lahko pobarvamo povezave grafa, je $X^1(G)$, kromatični indeks.

$M \subseteq E$ je **prirejanje**, če $\forall e,f \in M, e \neq f \Rightarrow e \cap f = \emptyset$ (angl. matching). Torej podmnožica povezav ki si ne delijo vozlišč.

**Popolno prirejanje** je tisto ki zazvame vsa vozlišča v grafu.
<br>

>Vizingov izrek
>$$\Delta(G) \le X'(G) \le \Delta(G) + 1$$

Tisti ki spadajo v kategorijo $\Delta (G)$ so razreda 1, tisti ki pa v drugo pa razreda 2.

> Če je $G$ dvodelni graf, potem je $X'(G) = \Delta(G)$.
(t.j., dvodelni grafi so razreda 1)

> Regularen graf na lihih vozliščih je razreda 2

**Neodvisna množica:** Podmnožica vozlišč $U \subseteq V(G)$ je **neodvisna**, če za vsaka dva vozlišča $u, v \in U$ velja, da nista sosednja (t.j., med njima ni povezave). Formalno: $\forall u, v \in U \Rightarrow u \not\sim v$.

**$\alpha(G)$:** Označuje **velikost največje neodvisne množice** v grafu $G$. To je maksimalno število vozlišč, ki jih lahko izberemo v grafu, tako da nobena dva izbrana vozlišča nista povezana.

**Dominantna množica:** Podmnožica vozlišč $U \subseteq V(G)$ je **dominantna**, če je vsako vozlišče v grafu, ki ni v $U$ (t.j., $v \in V(G) \setminus U$), sosednje vsaj enemu vozlišču v $U$. Formalno: $\forall v \in V(G) \setminus U \Rightarrow \exists u \in U: u \sim v$.

 **$\gamma(G)$:** Označuje **velikost najmanjše dominantne množice** v grafu $G$. To je minimalno število vozlišč, ki jih potrebujemo, da "pokrijemo" vsa ostala vozlišča v grafu (tako da je vsako vozlišče zunaj dominantne množice sosednje vsaj enemu vozlišču znotraj nje).

> Za graf $G$ (ki ni polni graf $K_n$) velja:
$$ \frac{|V(G)|}{\chi(G)} \le \alpha(G) \le |V(G)| - \frac{|E(G)|}{\Delta(G)} $$


> Za graf $G$, ki nima izoliranih vozlišč (t.j., vsako vozlišče ima stopnjo vsaj 1), velja:
$$ \frac{|V(G)|}{\Delta(G)+1} \le \gamma(G) \le \frac{|V(G)|}{2} $$

Ti izreki so pomembni za ocenjevanje velikosti neodvisnih in dominantnih množic, saj sta iskanje natančnih vrednosti $\alpha(G)$ in $\gamma(G)$ v splošnem težka problema.

> $$\alpha(G) = \omega(\overline{G})$$

>Če graf nima izoliranih vozlišč
> $$\gamma(G)\leq \alpha(G) = \omega(\overline{G}) \leq \chi(\overline{G})$$

**Produkti grafov**

Za dva grafa $G$ in $H$ je množica vozlišč produkta vedno kartezični produkt množic vozlišč $V(G) \times V(H)$. Razlika med posameznimi produkti je v definiciji povezav.

Simbol $*$ lahko predstavlja enega od treh produktov: $\square$, $\times$, $\boxtimes$.

---

### 1. Kartezični produkt ($G \square H$)

Dve vozlišči $(g, h)$ in $(g', h')$ sta povezani v kartezičnem produktu $G \square H$ (označeno z $(g, h) \sim_{\square} (g', h')$), če velja eno od naslednjih dveh pogojev:
*   $g \sim_G g'$ in $h = h'$ (povezava v $G$ in enako vozlišče v $H$)
*   **ali** $g = g'$ in $h \sim_H h'$ (enako vozlišče v $G$ in povezava v $H$)

**Razdalja v kartezičnem produktu ($G \square H$)**

$$d_{G \square H}((g, h), (g', h')) = d_G(g, g') + d_H(h, h')$$

**Pojasnilo:**
V kartezičnem produktu se lahko premikamo med vozlišči na dva načina:
1.  Spremenimo komponento $g$ (premaknemo se po povezavi v $G$), medtem ko komponenta $h$ ostane enaka.
2.  Spremenimo komponento $h$ (premaknemo se po povezavi v $H$), medtem ko komponenta $g$ ostane enaka.

Najkrajša pot med $(g, h)$ in $(g', h')$ je sestavljena iz $d_G(g, g')$ korakov v smeri $G$ in $d_H(h, h')$ korakov v smeri $H$. Ker se ti koraki lahko izvajajo neodvisno (ali prepletajo), je skupna dolžina najkrajše poti preprosto vsota razdalj v posameznih grafih. To je zelo intuitivno in spominja na Manhattan razdaljo v mreži.

---

### 2. Direktni produkt (tenzorski produkt) ($G \times H$)

Dve vozlišči $(g, h)$ in $(g', h')$ sta povezani v direktnem produktu $G \times H$ (označeno z $(g, h) \sim_{\times} (g', h')$), če velja:
*   $g \sim_G g'$ **in** $h \sim_H h'$ (povezava v $G$ in povezava v $H$)


**Razdalja v direktnem produktu ($G \times H$)**

$$d_{G \times H}((g, h), (g', h')) =$$
$$ \text{najmanjši } k, \text{ da obstajata sprehoda dolžine } k \text{ od } g \text{ do } g' \text{ in od } h \text{ do } h'$$
$$ \text{če takšna ne obstajata, pa } \infty $$

**Pojasnilo:**
V direktnem produktu je povezava med $(g, h)$ in $(g', h')$ le, če $g \sim_G g'$ **in** $h \sim_H h'$. To pomeni, da se lahko premaknemo iz $(g, h)$ v $(g', h')$ le, če hkrati naredimo korak v $G$ in korak v $H$.

To ima pomembne posledice:
*   **Pariteta:** Pot med $(g, h)$ in $(g', h')$ obstaja le, če imata najkrajši poti med $g$ in $g'$ ter med $h$ in $h'$ enako pariteto (obe sta sode ali obe sta lihe dolžine). Če imata različno pariteto, pot v direktnem produktu ne obstaja, in razdalja je $\infty$.
*   **Dolžina poti:** Če pot obstaja, je njena dolžina enaka dolžini poti v $G$ (ki je enaka dolžini poti v $H$). Zato je dolžina najkrajše poti $k$, kjer je $k = d_G(g, g') = d_H(h, h')$.
*   **Sprehod namesto poti:** Zapis "sprehoda dolžine $k$" je pomemben. V direktnem produktu se lahko zgodi, da najkrajša pot med $g$ in $g'$ ter med $h$ in $h'$ nimata enake dolžine ali paritete. Vendar pa lahko vedno najdemo sprehod (ki lahko ponavlja vozlišča in povezave) enake dolžine v obeh komponentah, če sta vozlišči povezani.
    *   Če $d_G(g, g')$ in $d_H(h, h')$ nimata enake paritete, potem $d_{G \times H}((g, h), (g', h')) = \infty$.
    *   Če imata enako pariteto, potem je $d_{G \times H}((g, h), (g', h')) = \max\{d_G(g, g'), d_H(h, h')\}$ (če sta oba grafa dvodelna) ali bolj splošno, najmanjši $k$ tak, da obstajata sprehoda dolžine $k$ v $G$ in $H$.


---

### 3. Močni produkt ($G \boxtimes H$)

Dve vozlišči $(g, h)$ in $(g', h')$ sta povezani v močnem produktu $G \boxtimes H$ (označeno z $(g, h) \sim_{\boxtimes} (g', h')$), če velja:
*   $(g, h) \sim_{\square} (g', h')$ **ali** $(g, h) \sim_{\times} (g', h')$
*   To pomeni, da je močni produkt unija povezav kartezičnega in direktnega produkta.


**Razdalja v močnem produktu ($G \boxtimes H$)**

$$d_{G \boxtimes H}((g, h), (g', h')) = \max\{d_G(g, g'), d_H(h, h')\}$$

**Pojasnilo:**
V močnem produktu imamo poleg povezav iz kartezičnega produkta tudi povezave iz direktnega produkta. To pomeni, da se lahko premaknemo iz $(g, h)$ v $(g', h')$ tudi, če sta $g \sim_G g'$ **in** $h \sim_H h'$ hkrati. To omogoča "diagonalne" premike.

Zaradi teh "diagonalnih" povezav lahko potujemo hitreje. Najkrajša pot je določena z daljšo izmed dveh komponentnih poti. Če je na primer $d_G(g, g') = 3$ in $d_H(h, h') = 5$, lahko v vsakem koraku naredimo korak v $G$ in $H$ hkrati (če sta sosednja). Ko je krajša pot končana, nadaljujemo samo po daljši. Zato je dolžina najkrajše poti enaka maksimumu razdalj v posameznih grafih. To spominja na razdaljo Čebiševa (šahovska razdalja).

> Vsi so asociativni in komutativni.



**Izrek (Weichselov izrek):**
Naj bosta $G$ in $H$ povezana grafa na vsaj 2 vozliščih.
*   Če vsaj eden od $G$ ali $H$ ni dvodelen, je $G \times H$ povezan.
*   Če sta oba $G$ in $H$ dvodelna, ima $G \times H$ dve povezani komponenti.

**Pojasnilo:**
Weichselov izrek obravnava povezanost **direktnega produkta** grafov ($G \times H$). Povezanost direktnega produkta je bolj zapletena kot pri kartezičnem ali močnem produktu, saj je odvisna od paritete poti v komponentnih grafih.

*   **Prvi del (vsaj eden ni dvodelen):** Če ima vsaj eden od grafov $G$ ali $H$ cikel lihe dolžine (kar pomeni, da ni dvodelen), potem je direktni produkt $G \times H$ povezan. To je zato, ker prisotnost lihega cikla omogoča "preklapljanje" med paritetami poti, kar zagotavlja, da je vsako vozlišče dosegljivo iz vsakega drugega.
*   **Drugi del (oba sta dvodelna):** Če sta oba grafa $G$ in $H$ dvodelna, potem ima $G \times H$ natanko dve povezani komponenti. To je posledica dejstva, da v dvodelnih grafih vse poti med dvema vozliščema iste particije (v dvodelni razdelitvi) imajo sodo dolžino, poti med vozliščema različnih particij pa liho dolžino. V direktnem produktu se lahko premikamo le, če se hkrati premaknemo v obeh komponentah. To ohranja pariteto "vsote" razdalj, kar povzroči dve ločeni komponenti.

---


**Posledica:**
Naj bodo $G_1, \dots, G_n$ povezani grafi.
*   $G_1 \square \dots \square G_n$ je povezan.
*   $G_1 \boxtimes \dots \boxtimes G_n$ je povezan.

**Pojasnilo:**
Ta posledica se nanaša na kartezični in močni produkt. Za razliko od direktnega produkta, sta kartezični in močni produkt vedno povezana, če so povezani tudi vsi komponentni grafi. To je zato, ker njune definicije povezav omogočajo "neodvisno" potovanje po posameznih komponentah, kar zagotavlja povezanost.

*   **Razdalja v kartezičnem produktu več grafov:**
    $$d_{G_1 \square \dots \square G_n}((g_1, \dots, g_n), (g_1', \dots, g_n')) = d_{G_1}(g_1, g_1') + \dots + d_{G_n}(g_n, g_n')$$
    To je posplošitev formule za dva grafa. Razdalja je vsota razdalj v posameznih komponentah.

*   **Razdalja v močnem produktu več grafov:**
    $$d_{G_1 \boxtimes \dots \boxtimes G_n}((g_1, \dots, g_n), (g_1', \dots, g_n')) = \max\{d_{G_1}(g_1, g_1'), \dots, d_{G_n}(g_n, g_n')\}$$
    To je posplošitev formule za dva grafa. Razdalja je maksimum razdalj v posameznih komponentah.

---


**Posledica:**
Naj bodo $G_1, \dots, G_n$ netrivialni grafi (t.j., imajo vsaj eno povezavo).
*   Če je največ 1 od $G_1, \dots, G_n$ dvodelen, je $G_1 \times \dots \times G_n$ povezan.
*   Če je $\ge 2$ od teh grafov dvodelnih, ima $G_1 \times \dots \times G_n$ $2^{k-1}$ povezanih komponent, kjer je $k$ število dvodelnih grafov med $G_1, \dots, G_n$.

**Pojasnilo:**
Ta posledica posplošuje Weichselov izrek na direktni produkt več kot dveh grafov.

*   **Prvi del (največ en dvodelen graf):** Če je med vsemi grafi $G_1, \dots, G_n$ največ eden dvodelen (torej, vsi ostali so nedvodelni), potem je njihov direktni produkt povezan. To je logična razširitev Weichselovega izreka, saj prisotnost vsaj enega nedvodelnega grafa omogoča "premostitev" paritetnih omejitev.
*   **Drugi del (vsaj dva dvodelna grafa):** Če sta vsaj dva grafa dvodelna, potem se število povezanih komponent poveča. Vsak dvodelen graf prispeva k "razcepu" na dve komponenti. Če je $k$ dvodelnih grafov, potem je število komponent $2^{k-1}$. To je zato, ker vsak dvodelen graf "deli" prostor na dve paritetni skupini, in te delitve se kombinirajo.





## Algebraične Strukture

Seveda, tukaj so organizirani zapiski, osredotočeni na teorijo iz pobarvanih delov, z dodanimi pojasnili in popravki morebitnih napak v originalnih zapiskih.

---

### Algebraične Strukture: Osnovni Koncepti

**Definicija Algebraične Strukture:**
Algebraična struktura je množica $A$ skupaj z eno ali več **notranjimi operacijami**. Notranja operacija $f$ na $A$ je preslikava $f: A \times A \to A$. Običajno jo pišemo v obliki $a * b$ namesto $f(a,b)$.

---

### 1. Grupoid

**Definicija:**
**Grupoid** je algebraična struktura $(A, *)$, tj. množica $A$ z eno samo notranjo operacijo $*$.

---

### 2. Polgrupa (Semigroup)

**Definicija:**
**Polgrupa** je grupoid $(A, *)$ pri katerem je operacija $*$ **asociativna**.
Torej, $(a * b) * c = a * (b * c)$ za vse $a, b, c \in A$.

---

### 3. Monoid

**Definicija Identitete (Enote):**
V polgrupi $(A, *)$ lahko definiramo elemente z naslednjimi lastnostmi:
*   **Leva enota $e_L$:** $e_L * a = a$ za vse $a \in A$.
*   **Desna enota $e_D$:** $a * e_D = a$ za vse $a \in A$.
*   **Enota $e$:** Element $e$ je enota, če je tako leva kot desna enota, torej $e * a = a * e = a$ za vse $a \in A$.

**Trditev (O Enoličnosti Enote):**
Če ima polgrupa (ali monoid/grupa) levo enoto $e_L$ in desno enoto $e_D$, potem je $e_L = e_D$. Posledično, v polgrupi obstaja največ ena enota.
**Dokaz:** $e_L = e_L * e_D$ (ker je $e_D$ desna enota) $= e_D$ (ker je $e_L$ leva enota). Torej $e_L = e_D$.

**Definicija:**
**Monoid** je polgrupa $(A, *)$ ki ima **enoto** $e$.



---

### 4. Inverzni Element

**Definicija Inverza:**
V monoidu $(A, *)$ z enoto $e$ za element $a \in A$:
*   **Levi inverz $b$ od $a$:** $b * a = e$.
*   **Desni inverz $c$ od $a$:** $a * c = e$.
*   **Inverz $b$ od $a$:** Element $b$ je inverz od $a$, če je hkrati levi in desni inverz, torej $b * a = a * b = e$.
**Oznaka:** Če inverz obstaja, ga označimo z $a^{-1}$. Pri aditivnih operacijah (npr. seštevanje) se inverz pogosto označuje z $-a$.

**Trditev (O Enoličnosti Inverza):**
Če ima element $a$ v monoidu levi inverz $b$ in desni inverz $c$, potem je $b=c$. Posledično, inverz elementa (če obstaja) je enoličen.

**Trditev (O Inverzu Produkta):**
Če sta $a$ in $b$ invertibilna (obrnljiva) elementa v monoidu $(A, *)$, potem je tudi njun produkt $a * b$ invertibilen, in velja: $(a * b)^{-1} = b^{-1} * a^{-1}$.
**Dokaz:** Pokažemo, da je $b^{-1} * a^{-1}$ inverz elementa $a * b$.
1.  $(a * b) * (b^{-1} * a^{-1}) = a * (b * b^{-1}) * a^{-1}$ (asociativnost) $= a * e * a^{-1}$ (definicija inverza) $= a * a^{-1}$ (lastnost enote) $= e$.
2.  $(b^{-1} * a^{-1}) * (a * b) = b^{-1} * (a^{-1} * a) * b$ (asociativnost) $= b^{-1} * e * b$ (definicija inverza) $= b^{-1} * b$ (lastnost enote) $= e$.
Ker je $b^{-1} * a^{-1}$ tako levi kot desni inverz za $a * b$, je to njegov enoličen inverz.

**Posledica:** Množica vseh invertibilnih elementov monoida $M$ (označena kot $M^{\times}$) tvori grupo pod isto operacijo.

---

### 5. Grupa

**Definicija:**
**Grupa** je monoid $(A, *)$ v katerem ima vsak element inverz.
Če je operacija $*$ v grupi komutativna, potem grupi rečemo **Abelova grupa** (ali komutativna grupa).

**Trditve o Grupah (Lastnosti Grup):**
Naj bo $(G, *)$ grupa.
*   **Pravilo krajšanja z leve:** Če $a * b = a * c$, potem $b = c$ za vse $a, b, c \in G$.
*   **Pravilo krajšanja z desne:** Če $b * a = c * a$, potem $b = c$ za vse $a, b, c \in G$.
*   **Enolična rešljivost enačb:** Za vsaka $a, b \in G$ velja:
    -   Enačba $a * x = b$ ima enolično rešitev $x = a^{-1} * b$.
    -   Enačba $x * a = b$ ima enolično rešitev $x = b * a^{-1}$.
**Opomba za Cayleyjevo tabelo:** Ta lastnost pomeni, da se v vsaki vrstici in vsakem stolpcu Cayleyjeve tabele (za končno grupo) vsak element pojavi natanko enkrat.


---

### 6. Cayleyjeva Tabela

**Definicija:**
**Cayleyjeva tabela** je tabela, ki prikazuje rezultate vseh možnih operacij med elementi v končni grupi (ali polgrupi/monoidu). Vrstice in stolpci so označeni z elementi grupe, celice pa vsebujejo rezultat operacije med elementom vrstice in elementom stolpca.

---

### 7. Potence Elementa in Red Elementa

**Potence Elementa:**
Za element $a$ v monoidu/grupi:
*   $a^n = a * a * \ldots * a$ (n-krat) za $n \ge 1$, kjer je $n \in \mathbb{N}$.
*   $a^0 = e$ (enota).
*   $a^{-n} = (a^{-1})^n$ za $n > 0$.
**Splošno:** Za $n \in \mathbb{Z}$, $a^n$ je definirano kot:
    *   $a \cdot  \ldots \cdot  a$ (n-krat), če $n > 0$
    *   $e$, če $n = 0$
    *   $(a^{-1}) \cdot  \ldots \cdot  (a^{-1})$ ($-n$-krat), če $n < 0$
**Lastnosti (za $n, m \in \mathbb{Z}$):**
*   $a^{n+m} = a^n * a^m$
*   $(a^n)^m = a^{nm}$

$(a * b)^n = a^n * b^n$ (velja **samo**, če sta $a$ in $b$ komutativna, tj. $a*b = b*a$)

**Red Elementa:**
Naj bo $G$ končna grupa in $a \in G$.
Ker je $G$ končna, se potence elementa $a^1, a^2, a^3, \ldots$ morajo ponoviti. Torej obstajata $m, n \in \mathbb{N}$ z $m > n$ takšna, da je $a^m = a^n$. To implicira $a^{m-n} = e$ (kjer je $m-n > 0$). 
**Red elementa $a$** je najmanjše pozitivno celo število $k$ takšno, da je $a^k = e$.
**V končni grupi imajo vsi elementi nek red.**


Red nevtralnega elementa je 1: $\text{red}(e) = 1$.

$a^k = e \iff \text{red}(a) \text{ deli } k$ (za $k \in \mathbb{Z}$).

Red elementa $a$ je enak redu ciklične podgrupe, ki jo generira $a$: $|\langle a \rangle| = \text{red}(a)$.

**Lagrangeov izrek (za končne grupe):** Če je $G$ končna grupa, potem red vsakega elementa $a \in G$ deli red grupe $G$. Tj. $\text{red}(a) \mid |G|$.

**Posledica Lagrangeovega izreka:** Za vsak element $a$ v končni grupi $G$ velja $a^{|G|} = e$.

**Red inverza:** $\text{red}(a^{-1}) = \text{red}(a)$.

Red potence elementa: $\text{red}(a^k) = \frac{\text{red}(a)}{gcd(\text{red}(a), k)}$.
- **Pomembna posledica:** Element $a^k$ generira isto ciklično podgrupo kot $a$ (tj. $\langle a^k \rangle = \langle a \rangle$) natanko takrat, ko je $gcd(\text{red}(a), k) = 1$.
- **Število generatorjev ciklične grupe reda $n$ je $\phi(n)$** (Eulerjeva fi funkcija).


Vse ciklične grupe so nujno Abelove, oz. če je grupa končna in ni abelova zagotovo ni ciklična.
Vsaka grupa katere red je praštevilo je izomorfna $\mathbb{Z}_{p}$ in je ciklična.

---

### 8. Podgrupa (Subgroup)

**Definicija:**
Naj bo $(G, *)$ grupa. Neprazna podmnožica $H \subseteq G$ je **podgrupa** grupe $G$, če je sama po sebi grupa za isto operacijo $*$. Označimo $H \le G$.

**Lastnosti in Pogoji za Podgrupo:**
Za $H \subseteq G$ velja, da je $H \le G$, če izpolnjuje naslednje pogoje:
1.  $H \ne \emptyset$ (Neprazna množica: vsaj enota grupe $e \in H$).
2.  **Zaprtost za operacijo:** Za vsaka $a, b \in H$ velja $a * b \in H$.
3.  **Zaprtost za inverz:** Za vsak $a \in H$ velja $a^{-1} \in H$.
*(Iz teh treh pogojev sledi tudi obstoj enote v $H$, saj če je $a \in H$, potem je tudi $a^{-1} \in H$, in iz zaprtosti za operacijo sledi $a \cdot a^{-1} = e \in H$.)*

**Izreka (Testi za Podgrupo):**
Za neprazno podmnožico $H \subseteq G$:
1.  **Enostopenjski test:** $H \le G \iff \forall a, b \in H: a * b^{-1} \in H$.
2.  **Test za končne grupe:** Če je $H$ končna in neprazna podmnožica grupe $G$, potem $H \le G \iff \forall a, b \in H: a * b \in H$ (tj. $H$ je zaprta za operacijo).
    *   *Pojasnilo:* Pri končni $H$ zaprtost za operacijo avtomatično implicira obstoj inverzov in enote. Če je $a \in H$, potem so $a, a^2, a^3, \ldots$ vsi v $H$. Ker je $H$ končna, se potence ponovijo, torej $a^m = a^n$ za $m > n$, kar pomeni $a^{m-n} = e$. Torej je enota $e \in H$. Prav tako je $a^{m-n-1} = a^{-1}$ (če $m-n>1$) ali $a^{n-1}$ (če $a^{n}=e$ in $a$ ima red $n$) inverz elementa $a$ v $H$.

**Vrste podgrup:**
*   $H = \{e\} \le G$: **Trivialna podgrupa**.
*   $H = G \le G$: **Neprava podgrupa**.
*   $H < G$: **Prava podgrupa**, če $H \le G$ in $H \ne G$ ter $H \ne \{e\}$.

---

### 9. Center Grupe

**Definicija:**
Naj bo $G$ grupa. **Center grupe $G$**, označen z $Z(G)$, je množica vseh elementov v $G$, ki komutirajo z vsemi drugimi elementi v $G$.
$Z(G) = \{a \in G \mid a * b = b * a \quad \forall b \in G\}$.

**Trditev:**
$Z(G)$ je **Abelova podgrupa** grupe $G$.
*   **Dokaz skica:**
    1.  **Nepraznost:** Enota $e$ vedno komutira z vsemi elementi ($e * b = b * e = b$), torej $e \in Z(G)$, zato $Z(G) \ne \emptyset$.
    2.  **Zaprtost za operacijo:** Naj bosta $a, b \in Z(G)$. Pokažemo, da $(a*b)$ komutira z vsakim $x \in G$: $(a*b)*x = a*(b*x) = a*(x*b) = (a*x)*b = (x*a)*b = x*(a*b)$. Torej $a*b \in Z(G)$.
    3.  **Zaprtost za inverz:** Naj bo $a \in Z(G)$. Pokažemo, da $a^{-1}$ komutira z vsakim $x \in G$: $a*x = x*a$. Pomnožimo z $a^{-1}$ z leve in desne: $a^{-1}*(a*x)*a^{-1} = a^{-1}*(x*a)*a^{-1}$. To da $x*a^{-1} = a^{-1}*x$. Torej $a^{-1} \in Z(G)$.
    4.  **Abelovost:** Po definiciji so vsi elementi v $Z(G)$ med seboj komutativni, saj komutirajo z *vsemi* elementi v $G$.

---

### 10. Ciklična Grupa in Ciklična Podgrupa

**Definicija:**
**Ciklična podgrupa**, generirana z elementom $a \in G$, je množica vseh celoštevilskih potenc elementa $a$:
$\langle a \rangle = \{a^m \mid m \in \mathbb{Z}\}$.

**Trditev:**
$\langle a \rangle$ je **Abelova podgrupa** grupe $G$.
*   **Pojasnilo:** Zaprtost za operacijo: $a^m * a^n = a^{m+n} \in \langle a \rangle$. Zaprtost za inverz: $(a^m)^{-1} = a^{-m} \in \langle a \rangle$. Enota: $a^0 = e \in \langle a \rangle$. Abelovost: $a^m * a^n = a^{m+n} = a^{n+m} = a^n * a^m$.

**Trditev (o elementih ciklične podgrupe):**
*   Če je red elementa $a$ **neskončen**, potem so vse potence $a^m$ (za različne $m \in \mathbb{Z}$) med seboj različne.
*   Če je red elementa $a$ **končen** in enak $n$, potem $\langle a \rangle = \{e, a^1, a^2, \ldots, a^{n-1}\}$. V tem primeru velja $a^i = a^j$ natanko takrat, ko je $i \equiv j \pmod n$.

**Trditev (o generatorjih ciklične grupe):**
Naj bo $G = \langle x \rangle$ ciklična grupa reda $n \in \mathbb{N}$ (kar pomeni, da je $x$ generator grupe $G$ in red $x$ je $n$). Element $a \in G$ je generator grupe $G$ (tj. $G = \langle a \rangle$) natanko takrat, ko je $a = x^k$ za neko celo število $k$ in velja $\gcd(k, n) = 1$.
*   **Dokaz skica:**
    *   $(\Rightarrow)$ Če $G = \langle a \rangle$, potem $a$ generira $G$. Ker je $a \in G = \langle x \rangle$, obstaja $k$ takšen, da $a = x^k$. Red elementa $a$ je $n$. Ker je red $a$ enak $n$, in $a=x^k$, potem je $n/\gcd(k,n)$ red $x^k$. Torej $n = n/\gcd(k,n)$, kar pomeni $\gcd(k,n)=1$.
    *   $(\Leftarrow)$ Če $a=x^k$ in $\gcd(k,n)=1$. Ker $\gcd(k,n)=1$, obstajata celi števili $u, v$ takšni, da $uk + vn = 1$. Torej $x^1 = x^{uk+vn} = x^{uk} * x^{vn} = (x^k)^u * (x^n)^v = a^u * e^v = a^u$. Ker je $x$ potenca elementa $a$ ($x=a^u$), lahko $a$ generira $x$. S tem pa $a$ lahko generira vse elemente, ki jih generira $x$, torej $G$. Zato je $a$ generator.

Velja da je homomorfizem v celoti definiran s preslikavo generatorja.
Homomorfizmi so si različni če slikajo generator v nek drug generator. Pri izomorfizmih se mora nujno ohranjati red generatorja.

---

### 11. Simetrična Grupa $S_n$ in Alternirajoča Grupa $A_n$

**Simetrična grupa $S_n$:**
*   **Definicija:** Simetrična grupa $S_n$ je množica vseh bijektivnih preslikav (permutacij) množice $\{1, 2, \ldots, n\}$ samo vase. Operacija v $S_n$ je kompozitum funkcij (množenje z desne).
*   **Velikost:** $|S_n| = n!$.
*   **Transpozicija:** Permutacija, ki zamenja samo dva elementa, ostale pa pusti pri miru, npr. $(i, j)$.
*   **Preprosta transpozicija:** Transpozicija oblike $(i, i+1)$.
*   Vsako permutacijo lahko zapišemo kot produkt transpozicij.

**Pariteta Permutacije (Sodost/Lihost):**
*   **Inverzija:** Par $(i, j)$ je inverzija permutacije $\pi \in S_n$, če je $i < j$ in $\pi(i) > \pi(j)$.
*   **Pariteta:** Permutacija $\pi$ je **soda (sodo permutacija)**, če ima sodo število inverzij (kar je enakovredno, če se jo da zapisati kot produkt sodega števila transpozicij). Permutacija $\pi$ je **liha (liha permutacija)**, če ima liho število inverzij (kar je enakovredno, če se jo da zapisati kot produkt lihega števila transpozicij).
*   **Pariteta ciklov:** Cikel dolžine $k$ je soda permutacija, če je $k-1$ sodo (tj. $k$ je liho), in liha permutacija, če je $k-1$ liho (tj. $k$ je sodo).
*   **Pravila za produkt parnosti:**
    *   Produkt dveh sodih permutacij je soda permutacija.
    *   Produkt dveh lihh permutacij je soda permutacija.
    *   Produkt sode in lihe permutacije je liha permutacija.

**Alternirajoča grupa $A_n$:**
*   **Definicija:** Alternirajoča grupa $A_n$ je množica vseh **sodih permutacij** v $S_n$.
*   **Trditev:** $A_n \le S_n$ (je podgrupa).
    *   **Dokaz skica:** $id \in A_n$ (ima 0 inverzij, kar je sodo). $A_n$ je zaprta za množenje (produkt dveh sodih je soda). $A_n$ je zaprta za inverze (inverz sode je soda).
*   **Velikost:** $|A_n| = |S_n| / 2 = n! / 2$.
    *   **Dokaz skica:** Obstaja bijekcija med množico sodih in množico lihh permutacij (npr. s pomnožitvijo z desne z neko fiksno transpozicijo, npr. $(1,2)$). Zato je število sodih enako številu lihh permutacij.

---

### 12. Odseki (Cosets)

**Definicija:**
Naj bo $G$ grupa in $H \le G$ podgrupa.
*   **Levi odsek podgrupe $H$ po elementu $a \in G$:** $aH = \{a * h \mid h \in H\}$.
*   **Desni odsek podgrupe $H$ po elementu $a \in G$:** $Ha = \{h * a \mid h \in H\}$.

**Pomembna opomba:** Levi odsek $aH$ ni nujno enak desnemu odseku $Ha$.

Odseki so za vsak element si različni, ali pa popolnoma enaki. Ker se lahko zgodi da dva elementa predstavljata isti odsek

**Trditve o odsekih:**
Naj bo $G$ grupa, $H \le G$ in $a, b \in G$.
1.  $a \in aH$.
2.  $aH = H \iff a \in H$.
3.  **Dva leva odseka sta bodisi enaka ali disjunktna: $aH = bH$ ali $aH \cap bH = \emptyset$.**
4.  $aH = bH \iff a^{-1} * b \in H$.
5.  Vsi levi (in desni) odseki imajo enako moč (število elementov) kot podgrupa $H$: $|aH| = |H|$.

**Posledica (Particija grupe):**
Grupa $G$ se razpade na disjunktno unijo levih odsekov podgrupe $H$.
$G = a_1H \cup a_2H \cup \ldots \cup a_kH$, kjer so $a_iH$ paroma disjunktni levi odseki.


---
### 15. Normalna Podgrupa (Normal Subgroup)

**Motivacija za definicijo:**
Za definicijo operacije na množici odsekov $G/H$ (ki so levi odseki $aH$), da bi dobili grupo, potrebujemo, da je operacija $(aH) * (bH) = (ab)H$ dobro definirana (tj. neodvisna od izbire predstavnikov $a$ in $b$ za odseke $aH$ in $bH$). To vodi do potrebe po "normalnosti".

**Definicija:**
Podgrupa $H \le G$ je **normalna podgrupa** grupe $G$, označena $H \triangleleft G$, če za vsak $g \in G$ velja $gHg^{-1} = H$.
*   **Ekvivalentne definicije/pogoji:**
    *   Za vsak $g \in G$ in vsak $h \in H$ velja $ghg^{-1} \in H$.
    *   Za vsak $g \in G$ velja $gH = Hg$ (tj. vsak levi odsek je tudi desni odsek).

**Primeri normalnih podgrup:**
*   Trivialna podgrupa $\{e\}$ in neprava podgrupa $G$ sta vedno normalni podgrupi.
*   Vsaka podgrupa Abelove grupe je normalna (saj $ghg^{-1} = gg^{-1}h = eh = h \in H$).
*   Center grupe $Z(G)$ je vedno normalna podgrupa.
*   Alternirajoča grupa $A_n$ je normalna podgrupa simetrične grupe $S_n$ za $n \ge 2$.

Za vse Abelove grupe velja da je njena podgrupa avtomatično normalna podgrupa.

---

### 16. Kvocientna Grupa (Quotient Group / Factor Group)

**Trditev:**
Naj bo $G$ grupa in $H \triangleleft G$ normalna podgrupa. Potem je na množici levih odsekov $G/H = \{aH \mid a \in G\}$ operacija $(aH) * (bH) = (ab)H$ **dobro definirana**, in $G/H$ je z njo **grupa**.
Ta grupa $G/H$ se imenuje **kvocientna grupa** ali **faktorska grupa**.

**Dokaz skica (ključne točke):**
1.  **Dobro definiranost operacije:** Pokažemo, da če $aH = a'H$ in $bH = b'H$, potem $(ab)H = (a'b')H$.
    *   $aH=a'H \implies a^{-1}a' \in H$. Podobno $b^{-1}b' \in H$.
    *   Želimo pokazati, da $(ab)^{-1}(a'b') \in H$.
    *   $(ab)^{-1}(a'b') = b^{-1}a^{-1}a'b' = b^{-1}(a^{-1}a')b'$. Ker je $a^{-1}a' \in H$, recimo $a^{-1}a' = h_1 \in H$. Izraz postane $b^{-1}h_1b'$. Ker je $H$ normalna podgrupa, $b^{-1}h_1b'$ mora biti v $H$ (ker $b^{-1}h_1b \in H$ in $b' \in bH$, to zahteva malo več formalizma, vendar se na koncu opira na $gHg^{-1}=H$ lastnost).
    *   Bolj direktno: $(ab)H = (a'b')H$ je ekvivalentno $(a'b')^{-1}(ab) \in H$. To je $(b')^{-1}(a')^{-1}ab \in H$. Ker $a' = ah_1$ in $b' = bh_2$ za $h_1, h_2 \in H$.
    *   $(b'^{-1}) (a'^{-1}) ab = (bh_2)^{-1} (ah_1)^{-1} ab = h_2^{-1}b^{-1}h_1^{-1}a^{-1}ab = h_2^{-1}b^{-1}h_1^{-1}b$
    *   Ker je $H$ normalna, $b^{-1}h_1^{-1}b \in H$. Označimo ga z $h_3 \in H$.
    *   Torej imamo $h_2^{-1}h_3 \in H$. Ker sta $h_2, h_3 \in H$ in je $H$ grupa, je tudi $h_2^{-1}h_3 \in H$. Torej je operacija dobro definirana.
2.  **Asociativnost:** Sledi iz asociativnosti v $G$: $((aH)(bH))(cH) = (ab)H(cH) = ((ab)c)H = (a(bc))H = (aH)((bc)H) = (aH)((bH)(cH))$.
3.  **Enota:** Enota je $eH = H$. Za vsak $aH \in G/H$ velja $(aH)(eH) = (ae)H = aH$ in $(eH)(aH) = (ea)H = aH$.
4.  **Inverz:** Inverz elementa $aH$ je $a^{-1}H$. Za vsak $aH \in G/H$ velja $(aH)(a^{-1}H) = (aa^{-1})H = eH = H$ in $(a^{-1}H)(aH) = (a^{-1}a)H = eH = H$.



---

### 13. Lagrangeev Izrek

**Izrek (Lagrangeov Izrek):**
Naj bo $G$ končna grupa in $H$ njena podgrupa. Potem moč podgrupe $H$ deli moč grupe $G$.
Število levih (ali desnih) odsekov podgrupe $H$ v grupi $G$ se imenuje **indeks podgrupe $H$ v $G$** in je enak $[G:H] = |G| / |H|$.

**Posledice Lagrangeovega izreka:**
1.  **Red elementa deli red grupe:** Če je $G$ končna grupa in $a \in G$, potem red elementa $a$ deli moč grupe $G$.
    *   **Dokaz skica:** Ciklična podgrupa $\langle a \rangle$ ima moč enako redu elementa $a$. Ker je $\langle a \rangle$ podgrupa, njen red deli red grupe $G$ po Lagrangeovem izreku.
2.  **$a^{|G|} = e$:** Če je $G$ končna grupa in $a \in G$, potem velja $a^{|G|} = e$.
    *   **Dokaz skica:** Naj bo $n$ red elementa $a$. Po prejšnji posledici $n$ deli $|G|$, torej $|G| = nk$ za neko celo število $k$. Potem $a^{|G|} = a^{nk} = (a^n)^k = e^k = e$.
3.  **Grupe praštevilskega reda so ciklične:** Če je $G$ grupa, katere moč $|G|$ je praštevilo $p$, potem je $G$ ciklična.
    *   **Dokaz skica:** Vzamemo poljuben element $a \in G$, $a \ne e$. Red elementa $a$ deli $|G|=p$. Ker je $p$ praštevilo in $a \ne e$, red $a$ ne more biti $1$. Torej mora biti red $a$ enak $p$. To pomeni, da $\langle a \rangle$ vsebuje $p$ elementov. Ker ima tudi $G$ $p$ elementov, sledi $G = \langle a \rangle$.

> Vsaka podgrupa z indeksom 2 je edinka.


**Mali Fermatov izrek (posledica Lagrangeovega izreka):**
Če je $p$ praštevilo in $a$ celo število, potem velja $a^p \equiv a \pmod p$.
*   **Dokaz skica:**
    *   Če $a \equiv 0 \pmod p$, potem $a^p \equiv 0^p \equiv 0 \pmod p$, kar je $a \equiv a \pmod p$.
    *   Če $a \not\equiv 0 \pmod p$, potem $a$ pripada grupi $(\mathbb{Z}_p \setminus \{0\}, \cdot)$, ki ima red $p-1$. Po posledici Lagrangeovega izreka ($a^{|G|} = e$) velja $a^{p-1} \equiv 1 \pmod p$. Pomnožimo z $a$: $a \cdot a^{p-1} \equiv a \cdot 1 \pmod p$, kar da $a^p \equiv a \pmod p$.
*   **Uporaba:** Ta izrek se uporablja za testiranje praštevilskosti (Fermatov test praštevilskosti).

---

### 14. Konjugiranost (Conjugacy)

**Definicija:**
Rečemo, da sta elementa $g, g' \in G$ **konjugirana**, če obstaja element $h \in G$ takšen, da velja $g' = hgh^{-1}$.
*   $g'$ je torej konjugat elementa $g$ s pomočjo elementa $h$.

**Trditev:**
Konjugiranost je **ekvivalenčna relacija** na grupi $G$.
*   **Pojasnilo:** Ekvivalenčna relacija pomeni:
    1.  **Refleksivnost:** $g \sim g$ (vsak element je konjugiran samemu sebi, s pomočjo $e$: $g = ege^{-1}$).
    2.  **Simetričnost:** Če $g \sim g'$, potem $g' \sim g$ (če $g' = hgh^{-1}$, potem $g = h^{-1}g'(h^{-1})^{-1}$).
    3.  **Tranzitivnost:** Če $g \sim g'$ in $g' \sim g''$, potem $g \sim g''$.
*   Ekvivalenčni razredi, ki jih tvori relacija konjugiranosti, se imenujejo **konjugiranostni razredi**.

**Trditev:**
Če sta $g$ in $g'$ konjugirana, potem imata **isti red**.
*   **Dokaz skica:** Naj bo $g' = hgh^{-1}$. Potem $(g')^n = (hgh^{-1})^n = hg^nh^{-1}$. Če je $g^n = e$, potem $(g')^n = heh^{-1} = e$. Torej, če ima $g$ red $n$, ima tudi $g'$ red $n$. In obratno.

**Konjugiranost v $S_n$:**
Dve permutaciji v $S_n$ sta konjugirani natanko takrat, ko imata **isto ciklično strukturo** (tj. enako število ciklov iste dolžine).

**Trditev (Konjugirana podgrupa):**
Če je $H \le G$ podgrupa in $g \in G$, potem je množica $gHg^{-1} = \{ghg^{-1} \mid h \in H\}$ tudi podgrupa grupe $G$. Imenuje se **konjugirana podgrupa** podgrupe $H$ (s pomočjo $g$).

---


### 17. Homomorfizmi Grup

**Definicija:**
Preslikava $f: G_1 \to G_2$, kjer sta $G_1$ in $G_2$ grupi (z operacijama $*_1$ v $G_1$ in $*_2$ v $G_2$), je **homomorfizem grup**, če ohranja grupno operacijo, torej:
$f(g * _1 g') = f(g) * _2 f(g')$ za vse $g, g' \in G_1$.
(Množenje na levi strani je v grupi $G_1$, množenje na desni strani je v grupi $G_2$).

**Lastnosti Homomorfizma:**
Naj bosta $G$ in $G'$ grupi (z enotama $e$ in $e'$) in $f: G \to G'$ homomorfizem.
1.  **Slika enote je enota:** $f(e) = e'$.
2.  **Slika inverza je inverz slike:** $f(g^{-1}) = (f(g))^{-1}$ za vse $g \in G$.
3.  **Slika (Imidž):** Množica vseh slik elementov domene, $\text{Im} f = \{f(g) \mid g \in G\}$, je **podgrupa** grupe $G'$.
4.  **Jedro (Kernel):** Množica vseh elementov v $G$, ki se preslikajo v enoto grupe $G'$, $\text{Ker} f = \{g \in G \mid f(g) = e'\}$, je **normalna podgrupa** grupe $G$.
5.  **Injektivnost in jedro:** Homomorfizem $f$ je injektiven (1-1), natanko takrat, ko je njegovo jedro trivialna podgrupa, $\text{Ker} f = \{e\}$.
>[!|dokaz]- Dokaz:
> 
> **1. ($\Rightarrow$) Predpostavimo, da je $f$ injektiven. Dokažimo, da je $\text{Ker } f = \{e_G\}$.**
> 
> *   Naj bo $x \in \text{Ker } f$ poljuben element.
> *   Po definiciji jedra velja $f(x) = e_H$, kjer je $e_H$ nevtralni element v grupi $H$.
> *   Ker je $f$ homomorfizem, vemo, da preslika nevtralni element grupe $G$ v nevtralni element grupe $H$, torej $f(e_G) = e_H$.
> *   Imamo torej $f(x) = e_H$ in $f(e_G) = e_H$, kar pomeni $f(x) = f(e_G)$.
> *   Ker je $f$ injektiven (po predpostavki), iz $f(x) = f(e_G)$ sledi, da mora biti $x = e_G$.
> *   To pomeni, da je edini element v jedru $f$ nevtralni element $e_G$. Torej, $\text{Ker } f = \{e_G\}$.
> 
> ---
> 
> **2. ($\Leftarrow$) Predpostavimo, da je $\text{Ker } f = \{e_G\}$. Dokažimo, da je $f$ injektiven.**
> 
> *   Da dokažemo, da je $f$ injektiven, moramo pokazati, da če $f(x_1) = f(x_2)$ za neka $x_1, x_2 \in G$, potem mora nujno veljati $x_1 = x_2$.
> *   Predpostavimo $f(x_1) = f(x_2)$.
> *   Ker je $f$ homomorfizem, vemo, da $f(x_2^{-1}) = (f(x_2))^{-1}$.
> *   Pomnožimo (oziroma operiramo) z $(f(x_2))^{-1}$ na desni strani obeh strani enakosti:
>     $f(x_1) (f(x_2))^{-1} = f(x_2) (f(x_2))^{-1}$
>     $f(x_1) f(x_2^{-1}) = e_H$
> *   Ponovno uporabimo lastnost homomorfizma, da $f(a)f(b) = f(ab)$:
>     $f(x_1 x_2^{-1}) = e_H$
> *   Po definiciji jedra, vsak element, ki se preslika v $e_H$, pripada jedru $f$. Torej $x_1 x_2^{-1} \in \text{Ker } f$.
> *   Po naši predpostavki je $\text{Ker } f = \{e_G\}$. To pomeni, da mora biti $x_1 x_2^{-1} = e_G$.
> *   Sedaj pomnožimo (oziroma operiramo) z $x_2$ na desni strani obeh strani enakosti:
>     $x_1 x_2^{-1} x_2 = e_G x_2$
>     $x_1 e_G = x_2$
>     $x_1 = x_2$
> *   S tem smo dokazali, da če je $f(x_1) = f(x_2)$, potem je $x_1 = x_2$, kar pomeni, da je $f$ injektiven.
> 

1.  **Kompozicija homomorfizmov:** Če sta $f: G_1 \to G_2$ in $g: G_2 \to G_3$ homomorfizma, potem je tudi njun kompozitum $g \circ f: G_1 \to G_3$ homomorfizem.
2.  **Inverz bijektivnega homomorfizma:** Če je $f: G_1 \to G_2$ bijektiven homomorfizem, potem je tudi njegova inverzna preslikava $f^{-1}: G_2 \to G_1$ homomorfizem.

---

### 18. Izomorfizmi Grup

**Definicija:**
**Izomorfizem** je bijektiven homomorfizem.
Rečemo, da sta grupi $G$ in $G'$ **izomorfni** (označeno z $G \cong G'$), če obstaja izomorfizem $f: G \to G'$. Izomorfne grupe imajo enake algebraične lastnosti (so "enake" z vidika grupne strukture).

**Trditev (Injektivnost in izomorfizem na sliko):**
Če je $f: G \to G'$ injektiven homomorfizem, potem je grupa $G$ izomorfna podgrupi $Im f \le G'$. (To je formalnejša verzija lastnosti 8 iz originalnih zapiskov).

**Prvi Izrek o Izomorfizmu:**
Naj bo $f: G \to G'$ homomorfizem grup. Potem je kvocientna grupa $G / Ker f$ izomorfna sliki $Im f$:
$G / Ker f \cong Im f$.
Ta izrek je temeljni kamen teorije grup in povezuje pojme homomorfizma, jedra, slike in kvocientne grupe.

Pri preverjanju kateri grupi je neka izomorfna lahko preverjamo ohranjanje lasntosti: komutativnost, redi elementov, red grupe, cikličnost, center grupe

---

### 19. Cayleyjev Izrek

**Izrek (Cayleyjev izrek):**
Vsaka grupa $G$ je izomorfna podgrupi neke grupe permutacij.
*   Natančneje: Obstaja podgrupa $H$ simetrične grupe $S(|G|)$ (permutacij množice $G$), tako da je $G \cong H$.
*   Če je $G$ končna grupa z $n$ elementi, je izomorfna podgrupi simetrične grupe $S_n$.

**Pojasnilo:** Cayleyjev izrek je pomemben, ker nam pove, da lahko vsako abstraktno grupo obravnavamo kot grupo permutacij.

---

### 20. Direktni Produkt Grup

**Definicija:**
Naj bosta $G_1$ in $G_2$ grupi (z operacijama $*_1$ in $*_2$). **Direktni produkt** grup $G_1$ in $G_2$, označen z $G_1 \times G_2$, je množica vseh urejenih parov $(g_1, g_2)$, kjer $g_1 \in G_1$ in $g_2 \in G_2$. Operacija na $G_1 \times G_2$ je definirana po komponentah:
$(g_1, g_2) * (g_1', g_2') = (g_1 * _1 g_1', g_2 * _2 g_2')$.

**Lastnosti Direktnega Produkta:**
*   Če sta $G_1$ in $G_2$ Abelovi grupi, potem je tudi njun direktni produkt $G_1 \times G_2$ Abelova grupa.
*   **Komutativnost:** $G_1 \times G_2 \cong G_2 \times G_1$.
*   **Asociativnost:** $(G_1 \times G_2) \times G_3 \cong G_1 \times (G_2 \times G_3)$.

**Primeri in Trditev (Kitajski Ostanek):**
*   $\mathbb{Z}_6 \cong \mathbb{Z}_2 \times \mathbb{Z}_3$. (Elementi $(0,0), (0,1), (0,2), (1,0), (1,1), (1,2)$ v $\mathbb{Z}_2 \times \mathbb{Z}_3$ imajo rede: (0,0) red 1; (1,0) red 2; (0,1) red 3; (0,2) red 3; (1,1) red 6; (1,2) red 6.)
*   **Trditev (Kitajski ostanek izrek za grupe):** $\mathbb{Z}_{mn} \cong \mathbb{Z}_m \times \mathbb{Z}_n$, če sta $m$ in $n$ **tuja** (t.j. njun največji skupni delitelj je $1$, $\gcd(m,n)=1$).
*   **Kontraprimer:** $\mathbb{Z}_4 \not\cong \mathbb{Z}_2 \times \mathbb{Z}_2$. (V $\mathbb{Z}_4$ obstaja element reda 4 (npr. 1). V $\mathbb{Z}_2 \times \mathbb{Z}_2$ pa so vsi elementi (razen enote) reda 2: $(1,0)$ red 2, $(0,1)$ red 2, $(1,1)$ red 2. Zato nista izomorfni.)

---

### 21. Enostavne Grupe (Simple Groups)

**Definicija:**
**Enostavna grupa** je grupa, ki ima samo dve edini normalni podgrupi: trivialno podgrupo $\{e\}$ in samo sebe $G$. (To pomeni, da nima pravih netrivialnih normalnih podgrup).

**Primeri Enostavnih Grup:**
*   Ciklične grupe $\mathbb{Z}_p$, kjer je $p$ praštevilo (ker nimajo nobenih pravih podgrup, zato tudi normalnih ne).
*   Alternirajoče grupe $A_n$ za $n \ge 5$. (Za $n=1,2,3,4$ niso enostavne, npr. $A_4$ ima normalno podgrupo Kleinovo grupo $V_4 = \{id, (12)(34), (13)(24), (14)(23)\}$).
*   Grupe Liejevega tipa.
*   26 sporadičnih enostavnih grup (npr. "Monster Group", ki ima približno $8 \times 10^{53}$ elementov).

**Pomen:**
Klasifikacija končnih enostavnih grup je eden največjih dosežkov matematike 20. stoletja. Vsako končno grupo je mogoče "zgraditi" iz enostavnih grup na določen način.


### 22. Kolobar (Ring)

**Definicija:**
**Kolobar** je algebraična struktura $(R, +, \cdot)$ z dvema binarnima operacijama (seštevanjem in množenjem), za kateri velja:
1.  $(R, +)$ je **Abelova grupa** (komutativna grupa).
    *   To pomeni, da je seštevanje asociativno, komutativno, ima nevtralni element (oznaka $0_R$ ali $0$) in za vsak element $a \in R$ obstaja nasprotni element $-a \in R$.
2.  $(R, \cdot)$ je **polgrupa** (asociativno glede na množenje).
    *   To pomeni, da je množenje asociativno: $(a \cdot b) \cdot c = a \cdot (b \cdot c)$ za vse $a, b, c \in R$.
3.  **Distributivnost:** Množenje je distributivno glede na seštevanje (z leve in z desne):
    *   $a \cdot (b + c) = (a \cdot b) + (a \cdot c)$ (leva distributivnost)
    *   $(a + b) \cdot c = (a \cdot c) + (b \cdot c)$ (desna distributivnost)
    za vse $a, b, c \in R$.

**Dodatne lastnosti kolobarja:**
*   Kolobar $R$ je **komutativen**, če je $(R, \cdot)$ komutativna polgrupa (tj. $a \cdot b = b \cdot a$ za vse $a, b \in R$).
*   Kolobar $R$ ima **enoto** (oznaka $1_R$ ali $1$), če je $(R, \cdot)$ monoid (tj. obstaja multiplikativna enota $1_R$ takšna, da $1_R \cdot a = a \cdot 1_R = a$ za vse $a \in R$).

**Trditev (Osnovne lastnosti množenja v kolobarju):**
Za vsak kolobar $R$ in $a, b \in R$ velja:
1.  $0_R \cdot a = 0_R = a \cdot 0_R$ (multiplikacija z aditivno enoto da aditivno enoto).
2.  $(-a) \cdot b = a \cdot (-b) = -(a \cdot b)$.
    *   *Dokaz skica za prvo točko:* $0_R \cdot a = (0_R + 0_R) \cdot a = 0_R \cdot a + 0_R \cdot a$. Odštejemo $0_R \cdot a$ na obeh straneh in dobimo $0_R = 0_R \cdot a$. Podobno za $a \cdot 0_R = 0_R$.
    *   *Dokaz skica za drugo točko:* $(-a) \cdot b + a \cdot b = (-a+a) \cdot b = 0_R \cdot b = 0_R$. Torej $(-a) \cdot b$ je aditivni inverz od $a \cdot b$, tj. $-(a \cdot b)$. Podobno za $a \cdot (-b)$.

---

### 23. Podkolobar (Subring)

**Definicija:**
Naj bo $(R, +, \cdot)$ kolobar. Neprazna podmnožica $S \subseteq R$ je **podkolobar**, če je sama po sebi kolobar glede na omejeni operaciji iz $R$.
**Pogoja za podkolobar:**
$S \subseteq R$ je podkolobar, če velja:
1.  $S \ne \emptyset$. (običajno se zahteva $0_R \in S$)
2.  Za vsaka $a, b \in S$: $a - b \in S$ (zaprtost za odštevanje, kar implicira, da je $(S, +)$ podgrupa grupe $(R, +)$).
3.  Za vsaka $a, b \in S$: $a \cdot b \in S$ (zaprtost za množenje).

---

### 24. Ideal

**Definicija:**
Naj bo $(R, +, \cdot)$ kolobar. Podmnožica $I \subseteq R$ je **ideal** kolobarja $R$, označeno $I \triangleleft R$, če:
1.  $(I, +)$ je **podgrupa** Abelove grupe $(R, +)$ (kar pomeni, da $I \ne \emptyset$, in za $a,b \in I \implies a-b \in I$).
2.  Za vsak $x \in I$ in vsak $a \in R$:
    *   $a \cdot x \in I$ (zaprtost za množenje z elementi iz $R$ z leve - **levi ideal**).
    *   $x \cdot a \in I$ (zaprtost za množenje z elementi iz $R$ z desne - **desni ideal**).
    Če veljata oba pogoja, je $I$ **dvosmerni ideal** (ali samo ideal).

**Primeri idealov:**
*   $n\mathbb{Z} = \{nk \mid k \in \mathbb{Z}\}$ je ideal kolobarja celih števil $\mathbb{Z}$.
*   $R$ je vedno ideal samega sebe. $\{0_R\}$ je vedno ideal.

**Trditev:**
Če je $I \triangleleft R$ ideal in $R$ je kolobar z enoto $1_R$, in če $1_R \in I$, potem je $I = R$.
*   **Dokaz skica:** Če $1_R \in I$, potem za vsak $a \in R$, po definiciji ideala, velja $a \cdot 1_R \in I$, kar pomeni $a \in I$. Torej $R \subseteq I$. Ker po definiciji $I \subseteq R$, sledi $I=R$.

---

### 25. Kvocientni Kolobar (Quotient Ring / Factor Ring)

**Definicija:**
Naj bo $(R, +, \cdot)$ kolobar in $I \triangleleft R$ ideal.
Množica **odsekov** $R/I = \{a+I \mid a \in R\}$ (kjer $a+I = \{a+i \mid i \in I\}$) je kvocientna grupa $(R/I, +)$ glede na seštevanje odsekov: $(a+I) + (b+I) = (a+b)+I$.
Za definicijo množenja na $R/I$ definiramo:
$(a+I) \cdot (b+I) = (a \cdot b)+I$.

**Trditev:**
Če je $I \triangleleft R$ ideal, je operacija množenja odsekov $(a+I) \cdot (b+I) = (a \cdot b)+I$ **dobro definirana**.
*   **Dokaz skica:** Moramo pokazati, da če $a+I = a'+I$ in $b+I = b'+I$, potem $(a \cdot b)+I = (a' \cdot b')+I$.
    *   Iz $a+I = a'+I$ sledi $a' = a+i_1$ za nek $i_1 \in I$.
    *   Iz $b+I = b'+I$ sledi $b' = b+i_2$ za nek $i_2 \in I$.
    *   Potem $a'b' = (a+i_1)(b+i_2) = ab + ai_2 + i_1b + i_1i_2$.
    *   Ker je $I$ ideal, vemo, da $ai_2 \in I$, $i_1b \in I$ in $i_1i_2 \in I$.
    *   Torej je $a'b' = ab + (\text{element v } I)$.
    *   To pomeni $a'b' - ab \in I$, kar je ekvivalentno $(a'b')+I = (ab)+I$. Množenje je torej dobro definirano.

**Trditev:**
S tako definiranim seštevanjem in množenjem je $(R/I, +, \cdot)$ **kolobar**, imenovan **kvocientni kolobar** ali **faktorski kolobar**.

---

### 26. Karakteristika Kolobarja (Characteristic of a Ring)

**Definicija:**
Karakteristika kolobarja $R$ je **najmanjše pozitivno naravno število $n$**, za katerega velja $n \cdot a = 0_R$ za vse $a \in R$.
Če tako število $n$ ne obstaja (tj. $k \cdot a = 0_R$ le za $k=0$ ali pa $k \cdot a = 0_R$ ni res za vse $a$), potem je karakteristika enaka $0$.

**Oznaka:** char $R = n$.
*   $n \cdot a$ pomeni $a + a + \ldots + a$ ($n$-krat).
*   Če je $n \in \mathbb{Z}$ in $a \in R$, $n \cdot a$ lahko definiramo tudi za negativne $n$ (kot $(-n)(-a)$) in za $n=0$ (kot $0_R$).

**Primeri:**
*   char $\mathbb{Z}_n = n$ (saj $n \cdot a \equiv 0 \pmod n$ za vse $a \in \mathbb{Z}_n$).
*   char $\mathbb{Z} = 0$.
*   char $\mathbb{Q} = 0$.
*   char $\mathbb{R} = 0$.
*   char $\mathbb{C} = 0$.
*   char $(\mathbb{Z}_2[x] / (x^2+x))$ (kvocientni kolobar polinomov nad $\mathbb{Z}_2$) je 2.

**Trditev:**
Če je $R$ kolobar z enoto $1_R$, potem je karakteristika kolobarja $R$ **najmanjše pozitivno naravno število $n$**, za katerega je $n \cdot 1_R = 0_R$. Če tako število $n$ ne obstaja, je karakteristika $0$.
*   **Dokaz skica:** Če $n \cdot 1_R = 0_R$, potem za vsak $a \in R$ velja $n \cdot a = n \cdot (1_R \cdot a) = (n \cdot 1_R) \cdot a = 0_R \cdot a = 0_R$.
    Če je $n$ najmanjše takšno število, potem je to tudi karakteristika kolobarja.

---

### 27. Homomorfizmi Kolobarjev

**Definicija:**
Naj bosta $R$ in $R'$ kolobarja. Preslikava $f: R \to R'$ je **homomorfizem kolobarjev**, če ohranja obe operaciji:
1.  $f(a + b) = f(a) + f(b)$ za vse $a, b \in R$ (homomorfizem grup glede na seštevanje).
2.  $f(a \cdot b) = f(a) \cdot f(b)$ za vse $a, b \in R$ (ohranja množenje).

Če je $f$ bijektiven homomorfizem, mu rečemo **izomorfizem kolobarjev**. Kolobarja $R$ in $R'$ sta **izomorfna** (označeno z $R \cong R'$), če obstaja izomorfizem $f: R \to R'$.

**Trditev (Lastnosti homomorfizma kolobarjev):**
Naj bo $f: R \to R'$ homomorfizem kolobarjev.
1.  $f(0_R) = 0_{R'}$.
2.  $f(-a) = -f(a)$ za vse $a \in R$.
3.  **Slika:** $Im f = \{f(a) \mid a \in R\}$ je **podkolobar** kolobarja $R'$.
4.  **Jedro:** $Ker f = \{a \in R \mid f(a) = 0_{R'}\}$ je **ideal** kolobarja $R$.
5.  **Injektivnost in jedro:** Homomorfizem $f$ je injektiven, natanko takrat, ko je $Ker f = \{0_R\}$.
6.  **Inverz bijektivnega homomorfizma:** Inverz bijektivnega homomorfizma je tudi izomorfizem.

**Prvi Izrek o Izomorfizmu za Kolobarje:**
Naj bo $f: R \to R'$ homomorfizem kolobarjev. Potem je kvocientni kolobar $R / Ker f$ izomorfen sliki $Im f$:
$R / Ker f \cong Im f$.
*   **Dokaz skica (elementi):**
    *   **Dobro definiranost in injektivnost:** Definicija preslikave $\Phi: R/Ker f \to Im f$ z $\Phi(a+Ker f) = f(a)$.
        *   Dobro definiranost: če $a+Ker f = b+Ker f$, potem $a-b \in Ker f$, torej $f(a-b)=0_{R'}$, kar pomeni $f(a)-f(b)=0_{R'}$, torej $f(a)=f(b)$.
        *   Injektivnost: če $\Phi(a+Ker f) = \Phi(b+Ker f)$, potem $f(a)=f(b)$, torej $f(a-b)=0_{R'}$, $a-b \in Ker f$, zato $a+Ker f = b+Ker f$.
    *   **Surjektivnost:** Za vsak $y \in Im f$ obstaja $a \in R$ takšen, da $f(a)=y$. Potem $y = \Phi(a+Ker f)$.
    *   **Homomorfizem:**
        *   $\Phi((a+Ker f) + (b+Ker f)) = \Phi((a+b)+Ker f) = f(a+b) = f(a)+f(b) = \Phi(a+Ker f) + \Phi(b+Ker f)$.
        *   $\Phi((a+Ker f) \cdot (b+Ker f)) = \Phi((ab)+Ker f) = f(ab) = f(a)f(b) = \Phi(a+Ker f) \cdot \Phi(b+Ker f)$.

**Primeri uporabe izreka:**
*   Preslikava $f: \mathbb{Z} \to \mathbb{Z}_n$ definirana z $f(i) = i \pmod n$ je surjektiven homomorfizem kolobarjev. Jedro je $Ker f = n\mathbb{Z}$. Po prvem izreku o izomorfizmu velja $\mathbb{Z} / n\mathbb{Z} \cong \mathbb{Z}_n$.
*   Preslikava $f: \mathbb{Z}[x] \to \mathbb{Z}_2[x]$ definirana z $f(p(x)) = p(x) \pmod 2$ (koeficiente vzamemo modulo 2) je surjektiven homomorfizem kolobarjev. Jedro je $Ker f = 2\mathbb{Z}[x]$ (polinomi s sodimi koeficienti). Zato $\mathbb{Z}[x] / 2\mathbb{Z}[x] \cong \mathbb{Z}_2[x]$.

---

### 28. Delitelji Niča (Zero Divisors)

**Definicija:**
V kolobarju $R$ sta $a, b \in R$ **delitelja niča**, če $a \ne 0_R$ in $b \ne 0_R$, pa kljub temu velja $a \cdot b = 0_R$.
*   $a$ je levi delitelj niča, $b$ je desni delitelj niča.

**Primeri:**
*   V $\mathbb{Z}_6$: $2 \cdot 3 = 6 \equiv 0 \pmod 6$. Torej sta $2$ in $3$ delitelja niča.
*   V kolobarju matrik: $\begin{pmatrix} 1 & 0 \\ 0 & 0 \end{pmatrix} \cdot \begin{pmatrix} 0 & 0 \\ 0 & 1 \end{pmatrix} = \begin{pmatrix} 0 & 0 \\ 0 & 0 \end{pmatrix}$.

---

### 29. Cel Kolobar (Integral Domain)

**Definicija:**
**Cel kolobar** je komutativen kolobar z enoto ($1_R \ne 0_R$), ki nima deliteljev niča.

**Primeri Celih Kolobarjev:**
*   $\mathbb{Z}$ (cela števila)
*   $\mathbb{Q}$ (racionalna števila)
*   $\mathbb{R}$ (realna števila)
*   $\mathbb{C}$ (kompleksna števila)
*   $\mathbb{Z}_p$, kjer je $p$ praštevilo (saj so vsi elementi razen 0 obrnljivi, torej ni deliteljev niča).
*   Kolobarji polinomov $\mathbb{Z}[x]$, $\mathbb{Q}[x]$, $\mathbb{R}[x]$, $\mathbb{C}[x]$.
*   $\mathbb{Q}[\sqrt{2}] = \{a+b\sqrt{2} \mid a, b \in \mathbb{Q}\}$.

**Trditev (Pravilo krajšanja):**
V celem kolobarju $R$, če $a \ne 0_R$ in $a \cdot b = a \cdot c$, potem $b = c$.
*   **Dokaz skica:** $a \cdot b = a \cdot c \implies a \cdot b - a \cdot c = 0_R \implies a \cdot (b-c) = 0_R$.
    Ker $R$ nima deliteljev niča in $a \ne 0_R$, mora biti $b-c = 0_R$, kar pomeni $b=c$.

**Trditev (Karakteristika celega kolobarja):**
Če je $R$ cel kolobar, potem je njegova karakteristika **0 ali pa praštevilo**.
*   **Dokaz skica:** Predpostavimo, da je char $R = n > 0$. Moramo pokazati, da je $n$ praštevilo.
    *   Ker je $R$ cel kolobar, ima enoto $1_R \ne 0_R$. Po trditvi o karakteristiki je $n$ najmanjše pozitivno celo število, za katerega $n \cdot 1_R = 0_R$.
    *   Predpostavimo, da $n$ ni praštevilo, torej $n = ab$ za $1 < a, b < n$.
    *   Potem $(a \cdot 1_R) \cdot (b \cdot 1_R) = (ab) \cdot 1_R = n \cdot 1_R = 0_R$.
    *   Ker je $R$ cel kolobar, nima deliteljev niča. To pomeni, da mora biti bodisi $a \cdot 1_R = 0_R$ ali $b \cdot 1_R = 0_R$.
    *   Vendar sta $a < n$ in $b < n$, kar pomeni, da $a \cdot 1_R \ne 0_R$ in $b \cdot 1_R \ne 0_R$ (saj je $n$ najmanjše takšno število).
    *   To je protislovje. Zato mora biti $n$ praštevilo.
---

### 30. Kolobar Polinomov $R[x]$

**Definicija:**
Naj bo $R$ kolobar. **Polinom v $R$** je zaporedje koeficientov $(a_0, a_1, a_2, \ldots)$ iz $R$, tako da obstaja naravno število $N \in \mathbb{N}$ (ali $N \in \mathbb{N}_0$), za katerega je $a_n = 0_R$ za vse $n \ge N$.
To pomeni, da je zaporedje končno mnogo neničelnih členov.
Množica vseh polinomov nad $R$ se označuje z $R[x]$:
$R[x] = \{(a_0, a_1, \ldots) \mid a_i \in R, \exists N \in \mathbb{N}: \forall n \ge N: a_n = 0_R\}$.

Za polinom $(a_0, a_1, \ldots, a_n, 0, 0, \ldots)$ običajno uporabljamo oznako:
$a_n x^n + \ldots + a_1 x + a_0$.
*   Simbol $x$ ni "spremenljivka" in ni "potenciranje", temveč je "seštevanje" (po dogovoru). Formalno je $x = (0, 1, 0, 0, \ldots)$.

**Operacije na $R[x]$:**
Naj bosta $p(x) = (a_0, a_1, a_2, \ldots)$ in $q(x) = (b_0, b_1, b_2, \ldots)$ polinoma v $R[x]$.
1.  **Seštevanje (komponentno):**
    $p(x) + q(x) = (a_0+b_0, a_1+b_1, a_2+b_2, \ldots)$.
    *   Definicija je dobro definirana, saj če sta $a_n=0$ za $n \ge N_1$ in $b_n=0$ za $n \ge N_2$, potem je $a_n+b_n=0$ za $n \ge \max(N_1, N_2)$.
2.  **Množenje (konvolucijski produkt):**
    $p(x) \cdot q(x) = (c_0, c_1, c_2, \ldots)$, kjer je $c_k = \sum_{i=0}^k a_i b_{k-i}$.
    *   $c_0 = a_0 b_0$
    *   $c_1 = a_0 b_1 + a_1 b_0$
    *   $c_2 = a_0 b_2 + a_1 b_1 + a_2 b_0$
    *   ...
    *   $c_n = a_0 b_n + a_1 b_{n-1} + \ldots + a_n b_0$.
    *   Tudi ta definicija je dobro definirana (končno mnogo neničelnih členov).

**Stopnja Polinoma (Degree):**
Za polinom $p(x) = (a_0, a_1, \ldots, a_n)$ je **stopnja polinoma**, označena $\deg p(x)$, definirana kot največji indeks $k$, za katerega je $a_k \ne 0_R$.
*   $\deg p(x) = \max\{k \mid a_k \ne 0_R\}$.
*   Stopnja ničelnega polinoma $0_R[x]$ (ki ima vse koeficiente $0_R$) je običajno definirana kot $-\infty$ (ali včasih kot $-1$).

**Trditev (Kolobar Polinomov):**
$R[x]$ je **kolobar** (imenovan kolobar polinomov nad $R$).
*   Komutativnost seštevanja v $R[x]$ sledi iz komutativnosti seštevanja v $R$.
*   Če je $R$ komutativen, je tudi $R[x]$ komutativen.
*   Če $R$ ima enoto $1_R$, ima tudi $R[x]$ enoto, ki je polinom $1 = (1_R, 0, 0, \ldots)$.
*   Če je $R$ **cel kolobar**, je tudi $R[x]$ **cel kolobar**.
    *   **Dokaz skica:** $R[x]$ je komutativen (če je $R$ komutativen), ima enoto (če jo ima $R$). Pokazati moramo, da nima deliteljev niča. Naj bosta $p(x), q(x) \in R[x]$ neničelna polinoma. Naj bo $\deg p(x) = m$ in $\deg q(x) = n$. Potem je vodilni koeficient $a_m \ne 0_R$ in $b_n \ne 0_R$. Vodilni koeficient produkta $p(x)q(x)$ je $a_m b_n$. Ker je $R$ cel kolobar, $a_m b_n \ne 0_R$. Torej je $p(x)q(x) \ne 0_R$.
    *   Posledično: $\deg(f(x) \cdot g(x)) = \deg f(x) + \deg g(x)$ velja, če $R$ nima deliteljev niča.
    *   Splošno: $\deg(f(x) \cdot g(x)) \le \deg f(x) + \deg g(x)$ (če so možni delitelji niča v $R$).

**Primer deliteljev niča v kolobarju polinomov:**
V $\mathbb{Z}_6[x]$ sta $2$ in $3$ delitelja niča, saj $2 \cdot 3 = 0$ (koeficienti so iz $\mathbb{Z}_6$).
$\deg((1+x)(2+3x)) = \deg(2+5x+3x^2) = 2 \le 1+1=2$.

---

### 31. Izrek o Deljenju Polinomov (Division Algorithm for Polynomials)

**Izrek:**
Naj bo $F$ polje, in naj bosta $p(x), g(x) \in F[x]$ polinoma, pri čemer $g(x) \ne 0$. Potem obstajata enolično določena polinoma $r(x), o(x) \in F[x]$, tako da velja:
$p(x) = r(x) \cdot g(x) + o(x)$, in $\deg o(x) < \deg g(x)$ (ali $o(x)$ je ničelni polinom).

---

### 32. Ničle Polinoma

**Definicija:**
Naj bo $F$ polje in $p(x) \in F[x]$. Za $a \in F$ je $f(a)$ vrednost polinoma $p(x)$ pri $x=a$.
Če je $p(a) = 0_F$, rečemo, da je $a$ **ničla polinoma** $p(x)$.

**Trditev (Faktorski izrek):**
Naj bo $F$ polje in $p(x) \in F[x]$. Potem je $a \in F$ ničla polinoma $p(x)$ natanko takrat, ko je $(x-a)$ faktor polinoma $p(x)$, tj. $p(x) = r(x) \cdot (x-a)$ za nek polinom $r(x) \in F[x]$.
*   **Dokaz skica:** Po izreku o deljenju polinomov lahko zapišemo $p(x) = r(x)(x-a) + o(x)$, kjer je $\deg o(x) < \deg(x-a) = 1$. Torej je $o(x)$ konstanten polinom, recimo $o(x)=b$.
    Zato $p(x) = r(x)(x-a) + b$.
    Vstavimo $x=a$: $p(a) = r(a)(a-a) + b = r(a) \cdot 0 + b = b$.
    Torej je $p(a)=0$ natanko takrat, ko je $b=0$, kar pomeni, da je $o(x)$ ničelni polinom in $(x-a)$ je faktor $p(x)$.

**Trditev (O številu ničel):**
Naj bo $F$ polje in $p(x) \in F[x]$ neničelni polinom stopnje $n$. Potem ima $p(x)$ največ $n$ ničel v $F$.
*   **Dokaz skica (z indukcijo po stopnji $n$):**
    *   **Baza ($n=0$):** Polinom stopnje 0 je neničelna konstanta. Nima ničel. Izrek velja.
    *   **Indukcijski korak:** Predpostavimo, da izrek velja za vse polinome stopnje manjše od $n$.
    *   Naj bo $p(x)$ polinom stopnje $n$.
    *   Če $p(x)$ nima ničel, izrek velja.
    *   Če ima $p(x)$ ničlo $a \in F$, potem po faktorskem izreku $p(x) = r(x)(x-a)$, kjer je $\deg r(x) = n-1$.
    *   Vsaka druga ničla $b \ne a$ od $p(x)$ mora biti ničla polinoma $r(x)$, saj $p(b) = r(b)(b-a) = 0$. Ker $F$ je polje in $b-a \ne 0$, mora biti $r(b)=0$.
    *   Po indukcijski predpostavki ima $r(x)$ največ $n-1$ ničel. Zato ima $p(x)$ (ki ima ničlo $a$ in ničle polinoma $r(x)$) največ $1 + (n-1) = n$ ničel.

---

### 33. Nerazcepen Polinom (Irreducible Polynomial)

**Definicija:**
Naj bo $F$ polje in $p(x) \in F[x]$. Rečemo, da je $p(x)$ **nerazcepen** nad $F$, če ni konstantni polinom in ne obstajata neničelna polinoma $q(x), r(x) \in F[x]$ s stopnjo $\ge 1$, tako da je $p(x) = q(x) \cdot r(x)$.
Drugače rečeno, $p(x)$ je nerazcepen, če ga ne moremo razcepiti na produkt dveh nekonstantnih polinomov nad $F$.

**Pomembni izreki o nerazcepnih polinomih:**
1.  **Fundamentalni Izrek Algebre:** V $\mathbb{C}[x]$ (kolobarju polinomov nad kompleksnimi števili) ni nerazcepnih polinomov stopnje $\ge 2$.
    *   To pomeni, da ima vsak nekonstanten polinom v $\mathbb{C}[x]$ vsaj eno ničlo. Posledično se lahko vsak polinom $p(x) \in \mathbb{C}[x]$ zapiše kot produkt linearnih faktorjev: $p(x) = c(x-r_1)(x-r_2)\ldots(x-r_n)$.
2.  V $\mathbb{R}[x]$ (kolobarju polinomov nad realnimi števili) ni nerazcepnih polinomov stopnje $\ge 3$.
    *   To pomeni, da se lahko vsak realen polinom zapiše kot produkt linearnih in/ali kvadratnih polinomov (z realnimi koeficienti in z negativno diskriminanto, npr. $x^2+1$).

---

### 34. Polje (Field)

**Definicija:**
**Polje** je komutativen kolobar z enoto $1_R \ne 0_R$, v katerem ima vsak neničelni element multiplikativni inverz.
Torej, za vsak $a \in R, a \ne 0_R$, obstaja $a^{-1} \in R$ takšen, da $a \cdot a^{-1} = a^{-1} \cdot a = 1_R$.

**Primeri Polj:**
*   $\mathbb{Z}_p$, kjer je $p$ praštevilo (končna polja).
*   $\mathbb{Q}$ (racionalna števila).
*   $\mathbb{R}$ (realna števila).
*   $\mathbb{C}$ (kompleksna števila).
*   $\mathbb{Q}[\sqrt{2}] = \{a+b\sqrt{2} \mid a, b \in \mathbb{Q}\}$.
*   Racionalne funkcije (kvocientni kolobar polinomov nad poljem).

**Trditev (Polje je cel kolobar):**
Če je $R$ polje, potem je $R$ cel kolobar.
*   **Dokaz skica:** Polje je po definiciji komutativen kolobar z enoto. Moramo pokazati, da nima deliteljev niča. Naj bosta $a, b \in R$ in $a \cdot b = 0_R$. Če $a \ne 0_R$, potem ima $a$ inverz $a^{-1}$. Pomnožimo enačbo z $a^{-1}$ z leve: $a^{-1}(a \cdot b) = a^{-1} \cdot 0_R \implies (a^{-1}a) \cdot b = 0_R \implies 1_R \cdot b = 0_R \implies b = 0_R$. Torej, če je $a \ne 0_R$, mora biti $b=0_R$. Zato ni deliteljev niča.

**Trditev (Končni cel kolobar je polje):**
Če je $R$ končen cel kolobar, potem je $R$ polje.
*   **Dokaz skica:** Naj bo $R$ končen cel kolobar. Za vsak neničelni element $a \in R$, $a \ne 0_R$, želimo pokazati, da obstaja njegov inverz.
    *   Razmislimo o funkciji $f_a: R \to R$ definirani z $f_a(x) = a \cdot x$.
    *   Ker $R$ nima deliteljev niča in $a \ne 0_R$, je $f_a$ injektivna: če $ax_1=ax_2$, potem $a(x_1-x_2)=0$, torej $x_1-x_2=0$, kar pomeni $x_1=x_2$.
    *   Ker je $R$ končna množica in $f_a$ injektivna preslikava iz $R$ v $R$, mora biti $f_a$ tudi surjektivna.
    *   To pomeni, da za vsak element $y \in R$ (vključno z $1_R$) obstaja nek $x \in R$ takšen, da $f_a(x) = y$. Še posebej, za $y=1_R$, obstaja $x \in R$ takšen, da $a \cdot x = 1_R$. Ta $x$ je inverz elementa $a$. Torej je $R$ polje.

**Trditev (Ideal v polju):**
V polju (ali obsegu) sta edina ideala **trivialni ideal** $\{0_F\}$ in **nepravi ideal** $F$.
*   **Dokaz skica:** Naj bo $I$ ideal v polju $F$. Če $I \ne \{0_F\}$, potem obstaja neničelni element $x \in I$. Ker $F$ je polje, ima $x$ inverz $x^{-1} \in F$. Po definiciji ideala, ker $x \in I$ in $x^{-1} \in F$, velja $x^{-1} \cdot x \in I$, kar pomeni $1_F \in I$. Ker $1_F \in I$, in $I$ je ideal, po prejšnji trditvi sledi $I=F$.

**Homomorfizem Polj:**
Homomorfizem polj $f: F \to F'$ je homomorfizem kolobarjev, ki preslika $1_F$ v $1_{F'}$.
Pomembna posledica: Vsak homomorfizem polj je **injektiven**.
*   **Dokaz skica:** Jedro homomorfizma polj $Ker f$ je ideal v $F$. Ker sta edina ideala v $F$ $\{0_F\}$ in $F$, mora biti $Ker f = \{0_F\}$ (saj $f$ ni ničelna preslikava, ker $f(1_F)=1_{F'}$). Če je $Ker f = \{0_F\}$, je homomorfizem injektiven.

---
**Končna Polja:**
*   Niso nujno komutativna, čeprav vsa končna polja so komutativna (izrek Wedderburna).
*   Karakteristika končnega polja je vedno **praštevilo** $p$.
*   Obstoj in velikost: Za vsako praštevilo $p$ in vsako naravno število $k \ge 1$ obstaja polje velikosti $p^k$.
*   Do izomorfizma natančno obstaja natanko eno polje velikosti $p^k$. Označimo ga z $\mathbb{F}_{p^k}$ (ali $GF(p^k)$).

---
**Druge Algebraične Strukture (Omenjeno):**
*   **Vektorski prostor:** Abelova grupa $(V, +)$ in polje skalarjev $F$, z operacijo množenja s skalarjem $F \times V \to V$.
*   **Modul:** Podobno kot vektorski prostor, le da imamo namesto polja kolobar $R$. $R$-modul je Abelova grupa $(M, +)$ z operacijo $R \times M \to M$ in določenimi aksiomi.
*   **Algebra:** Vektorski prostor nad poljem $F$ z dodatno binarno operacijo (množenjem) med vektorji, ki je distributivna in združljiva z množenjem s skalarjem.
    *   Primeri: $R^{n \times n}$ (nekomutativna algebra), $F[x]$ (komutativna algebra).

---



# Vsi izreki

Seveda, tukaj so vsi izreki, trditve in pomembne posledice iz navedenega besedila, brez dokazov in dodatnih pojasnil, z matematičnimi izrazi v LaTeX obliki:

### Izreki o Grafih

1.  **Izrek o rokovanju:**
    Vsota stopenj vseh vozlišč je enaka dvakratniku števila povezav.
    $$\sum_{v \in V}^{}\deg(v) = 2 |E|$$
2.  **Posledica izreka o rokovanju:**
    V vsakem grafu je sodo število vozlišč lihe stopnje.
3.  **Trditev o poteh in sprehodih:**
    Obstaja sprehod od $u$ do $v$ $\Rightarrow$ obstaja pot od $u$ do $v$.
4.  **Trditev o poteh in ciklih:**
    V $G$ obstajata 2 različni poti med $u$ in $v$ $\Rightarrow$ v $G$ obstaja cikel.
5.  **Trditev o ciklih lihe dolžine:**
    Če v $G$ obstaja sklenjen sprehod lihe dolžine obstaja tudi cikel lihe dolžine.
6.  **Trditev o premeru komplementa nepovezanega grafa:**
    Če $G$ ni povezan potem je $\text{dia}(\overline{G}) \leq 2$.
7.  **Posledica o povezanosti grafa in njegovega komplementa:**
    $G$ ali $\overline{G}$ je povezan.
8.  **Izrek o dvodelnih grafih:**
    Graf je dvodelen, natanko tedaj ko ne vsebuje nobenega lihega cikla.
9.  **Trditev o kompoziciji homomorfizmov grafov:**
    Če sta $\varphi_{1} : G_{1} \rightarrow G_{2}$ in $\varphi_{2} : G_{2} \rightarrow G_{3}$ homomorfizma je tudi $\varphi_{2} \circ \varphi_{1}$ homomorfizem.
10. **Trditev o avtomorfizmih grafa in njegovega komplementa:**
    $$\text{Avt}(G) = \text{Avt} (\overline{G})$$
11. **Trditev o številu komponent pri odstranitvi vozlišča/povezave:**
    Pri prereznem vozlišču se lahko število komponent poveča za največ $\deg(v)-1$, pri prerezni povezavi pa za največ $1$.
12. **Trditev o $k$-povezanosti:**
    Če je graf $k$-povezan je $k$ in $k-1$ povezan hkrati.
13. **Whitnejev izrek:**
    Za graf $G$ z vsaj 3 vozlišči: $G$ je $2$-povezan $\Leftrightarrow$ med poljubnimi vozlišči obstajata notranje disjunktni poti.
14. **Mengerjev izrek (globalen):**
    Graf z vsaj $k+1$ vozlišči je $k$ povezan natanko tedaj ko med poljubnimi vozlišči obstaja vsaj $k$ notranje disjunktnih poti.
15. **Mengerjev izrek (lokalen):**
    Največje število notranje disjunktnih poti med $u$ in $v$ je enako velikosti najmanjše prerezne množice za katero sta $u$ in $v$ v različnih komponentah.
16. **Trditev o listih drevesa:**
    Vsako drevo z vsaj 2 vozliščema ima list.
17. **Trditev o gozdu:**
    Gozd: $|E_{G}| = |V_{G}| - \Omega (G)$.
18. **Trditev o listih v drevesu:**
    V drevesu z vsaj 2 vozliščema sta vsaj 2 lista.
19. **Trditev o odstranjevanju povezav v ciklu:**
    Če je $G$ povezan graf in $e$ je povezava na nekem ciklu, potem je $G\backslash e$ tudi povezan graf.
20. **Izrek o značilnosti drevesa:**
    $|E_{G}| = |V_{G}|-1 \Leftrightarrow G$ je drevo.
21. **Ekvivalentne trditve o drevesu:**
    Naslednje trditve so ekvivalentne za graf $G$:
    *   Med poljubnimi vozlišči $G$ obstaja natanko 1 pot.
    *   $G$ je drevo.
    *   $G$ je povezan, vsaka povezava je **most**.
    *   $G$ je povezan, št. povezav je $|E_{G}| = |V_{G}| - 1$.
22. **Trditev o obstoju vpetega drevesa:**
    Graf je povezan natanko tedaj ko obstaja vpeto drevo $G$ oz. $\tau(G)\geq 1 \Leftrightarrow \text{graf je povezan}$.
23. **Rekurzivna zveza za število vpetih dreves (za multigraf):**
    $$\tau(G) = \tau (G-e)+ \tau (G\backslash e)$$
24. **Cayleyjev izrek (število vpetih dreves v polnem grafu):**
    $$\tau(K_{n}) = n^{n-2}$$
25. **Izrek o Eulerjevem obhodu:**
    Povezan graf je eulerjev natanko tedaj, ko so vsa vozlišča soda.
26. **Izrek o Eulerjevem sprehodu:**
    $G$ ima eulerjev sprehod natanko tedaj ko sta največ 2 vozlišča lihe stopnje in so vse povezave v eni komponenti.
27. **Trditev o Hamiltonovem grafu in odstranitvi vozlišč:**
    Če je $G$ hamiltonov graf in $(S \subset V_{G}) \neq \emptyset$ potem je število komponent brez $S$ manjše ali enako številu elementov $S$ oz. $\text{graf je hamiltonov} \Rightarrow\Omega(G-S) \leq |S|$.
28. **Posledica Hamiltonove trditve:**
    Če obstaja $S$ da je $\Omega(G-S) > |S| \Rightarrow$ graf ni hamiltonov.
29. **Trditev o Hamiltonovi poti:**
    Če obstaja $S$ da je $\Omega(G-S) > |S|+1 \Rightarrow$ graf nima hamiltonove poti.
30. **Trditev o Hamiltonovem polnem dvodelnem grafu:**
    $K_{m,n}$ je hamiltonov $\Leftrightarrow$ $m = n$.
31. **Trditev o Hamiltonovem dvodelnem grafu:**
    $G$ je dvodelen in hamiltonov $\Rightarrow$ $|X| = |Y|$.
32. **Orejev izrek:**
    Naj bo $G$ povezan graf z $n \geq 3$ vozlišči. Če za vsaki dve nepovezani vozlišči $u$ in $v$ velja $\deg(u) + \deg(v) \geq n$, potem je $G$ hamiltonov.
33. **Diracov izrek:**
    Če ima vsako vozlišče v grafu z vsaj 3 vozlišči stopnjo vsaj $n/2$, potem je graf hamiltonov.
34. **Jordanov izrek:**
    Enostavna sklenjena krivulja razdeli $\mathbb{R}^{2}$ na 2 območji.
35. **Trditev o dolžini lic:**
    Dolžina vseh lic je dvakrat večja od števila robov.
    $$\sum_{f \,\in\, F_{G}}l(f)= 2|E_{G}|$$
36. **Trditev o dolžini lic in ožini grafa:**
    Dolžina vseh lic je večja ali enaka dolžini najkrajšega cikla.
    $$l(F) \geq g(G)$$
    Iz tega sledi, da je
    $$2|E_{G}| \geq g(G)\cdot |F_{G}| \,;\; G\text{ ni gozd}$$
37. **Eulerjeva formula za ravninske grafe:**
    Za ravninski graf $G$:
    $$|V_{G}| - |E_{G}| + |F_{G}|= \Omega(G) +1$$
38. **Trditev o številu povezav ravninskega grafa (za grafe, ki niso gozd):**
    Če je $G$ ravninski graf, ki ni gozd velja
    $$|E_{G}| \leq \frac{g(G)}{g(G)-2}(|V_{G}|-2)$$
39. **Posledica za ravninske grafe brez trikotnikov:**
    Če je $|V_{G}| \geq 3$, $G$ je ravninski in nima trikotnikov, potem $|E_{G}| \leq 2(|V_{G}|-2)$.
40. **Posledica za ravninske grafe s trikotniki:**
    Če je $|V_{G}| \geq 3$, $G$ je ravninski in ima trikotnike, potem $|E_{G}| \leq 3(|V_{G}|-2)$.
41. **Trditev o neravninosti $K_5$ in $K_{3,3}$:**
    $K_{5}$ in $K_{3,3}$ nista ravninska.
42. **Kuratowskijev izrek:**
    Graf je ravninski $\Leftrightarrow$ ne vsebuje podgrafa, izomorfnega subdiviziji $K_{5}$ ali $K_{3,3}$.
43. **Wagnerjev izrek:**
    Graf je ravninski $\Leftrightarrow$ $K_{5}$ in $K_{3,3}$ nista njegova minorja.
44. **Trditev o dvodelnih grafih in kromatičnem številu:**
    ${\Huge{\chi}}\!(G) \leq 2 \Leftrightarrow G \text{ je dvodelen}$.
45. **Trditev o kromatičnem številu podgrafa:**
    Če je $H$ podgraf $G$, potem ${\Huge{\chi}}\!(H) \leq {\Huge{\chi}}\!(G)$.
46. **Meje za kromatično število:**
    Velikost največje klike je manjša ali enaka kromatičnemu številu, kar je manjše ali enako največji stopnji grafa plus 1.
    $$\omega(G)\leq{{\Huge{\chi}}\!}(G) \leq \Delta(G) + 1$$
47. **Izboljšane meje za kromatično število:**
    Za vsak povezan graf, ki ni lih cikel ali polni graf, velja
    $$\omega(G) \leq \,{{\Huge{\chi}}\!}(G) \leq \Delta(G)$$
48. **Izrek o petih barvah (Five-Color Theorem):**
    Za ravninski graf $G$: ${\Huge{\chi}}\!(G) \leq 5$.
49. **Izrek o štirih barvah (Four-Color Theorem):**
    Za ravninski graf $G$: ${\Huge{\chi}}\!(G) \leq 4$.
50. **Formula za kromatični polinom (Deletion-Contraction Formula):**
    Število dobrih barvanj grafa brez povezave je enako originalnemu številu plus številu s skrčeno povezavo.
    $$P_{G-e}(k) = P_{G}(k) + P_{G\backslash e}(k)$$
51. **Spodnja meja za kromatični indeks:**
    Kromatični indeks je večji ali enak največji stopnji grafa.
    $${\Huge{\chi}\!}'(G) \geq \Delta(G)$$
52. **Meje za kromatični indeks polnega grafa:**
    $$ n-1 \leq {\Huge{\chi}\!}'(K_{n}) \leq n$$
53. **Vizingov izrek:**
    $$\Delta(G) \le {\Huge{\chi}\!}'(G) \le \Delta(G) + 1$$
54. **Posledica Vizingovega izreka za dvodelne grafe:**
    Če je $G$ dvodelni graf, potem je ${\Huge{\chi}\!}'(G) = \Delta(G)$.
55. **Trditev o kromatičnem indeksu regularnih grafov z lihim številom vozlišč:**
    Regularen graf na lihih vozliščih je razreda 2.
56. **Meje za neodvisno množico:**
    Za graf $G$ (ki ni polni graf $K_n$) velja:
    $$ \frac{|V(G)|}{{\Huge{\chi}}\!(G)} \le \alpha(G) \le |V(G)| - \frac{|E(G)|}{\Delta(G)} $$
57. **Meje za dominantno množico:**
    Za graf $G$, ki nima izoliranih vozlišč (t.j., vsako vozlišče ima stopnjo vsaj 1), velja:
    $$ \frac{|V(G)|}{\Delta(G)+1} \le \gamma(G) \le \frac{|V(G)|}{2} $$
58. **Relacija med neodvisno množico in kliko komplementa:**
    $$\alpha(G) = \omega(\overline{G})$$
59. **Neenakosti med dominantno množico, neodvisno množico, kliko in kromatičnim številom komplementa:**
    Če graf nima izoliranih vozlišč
    $$\gamma(G)\leq \alpha(G) = \omega(\overline{G}) \leq {\Huge{\chi}}\!(\overline{G})$$
60. **Formula za razdaljo v kartezičnem produktu grafov:**
    $$d_{G \square H}((g, h), (g', h')) = d_G(g, g') + d_H(h, h')$$
61. **Formula za razdaljo v močnem produktu grafov:**
    $$d_{G \boxtimes H}((g, h), (g', h')) = \max\{d_G(g, g'), d_H(h, h')\}$$
62. **Formula za razdaljo v direktnem produktu grafov:**
    $$d_{G \times H}((g, h), (g', h')) = \text{najmanjši } k, \text{ da obstajata sprehoda dolžine } k \text{ od } g \text{ do } g' \text{ in od } h \text{ do } h'$$
    $$ \text{če takšna ne obstajata, pa } \infty $$
63. **Weichselov izrek (o povezanosti direktnega produkta):**
    Naj bosta $G$ in $H$ povezana grafa na vsaj 2 vozliščih.
    *   Če vsaj eden od $G$ ali $H$ ni dvodelen, je $G \times H$ povezan.
    *   Če sta oba $G$ in $H$ dvodelna, ima $G \times H$ dve povezani komponenti.
64. **Posledica o povezanosti kartezičnega in močnega produkta več grafov:**
    Naj bodo $G_1, \dots, G_n$ povezani grafi.
    *   $G_1 \square \dots \square G_n$ je povezan.
    *   $G_1 \boxtimes \dots \boxtimes G_n$ je povezan.
65. **Formula za razdaljo v kartezičnem produktu več grafov:**
    $$d_{G_1 \square \dots \square G_n}((g_1, \dots, g_n), (g_1', \dots, g_n')) = d_{G_1}(g_1, g_1') + \dots + d_{G_n}(g_n, g_n')$$
66. **Formula za razdaljo v močnem produktu več grafov:**
    $$d_{G_1 \boxtimes \dots \boxtimes G_n}((g_1, \dots, g_n), (g_1', \dots, g_n')) = \max\{d_{G_1}(g_1, g_1'), \dots, d_{G_n}(g_n, g_n')\}$$
67. **Posledica o povezanosti direktnega produkta več grafov:**
    Naj bodo $G_1, \dots, G_n$ netrivialni grafi (t.j., imajo vsaj eno povezavo).
    *   Če je največ 1 od $G_1, \dots, G_n$ dvodelen, je $G_1 \times \dots \times G_n$ povezan.
    *   Če je $\ge 2$ od teh grafov dvodelnih, ima $G_1 \times \dots \times G_n$ $2^{k-1}$ povezanih komponent, kjer je $k$ število dvodelnih grafov med $G_1, \dots, G_n$.

### Izreki o Algebraičnih Strukturah

68. **Trditev o enoličnosti enote v polgrupi:**
    Če ima polgrupa (ali monoid/grupa) levo enoto $e_L$ in desno enoto $e_D$, potem je $e_L = e_D$. Posledično, v polgrupi obstaja največ ena enota.
69. **Trditev o enoličnosti inverza v monoidu:**
    Če ima element $a$ v monoidu levi inverz $b$ in desni inverz $c$, potem je $b=c$. Posledično, inverz elementa (če obstaja) je enoličen.
70. **Trditev o inverzu produkta v monoidu:**
    Če sta $a$ in $b$ invertibilna (obrnljiva) elementa v monoidu $(A, *)$, potem je tudi njun produkt $a * b$ invertibilen, in velja: $(a * b)^{-1} = b^{-1} * a^{-1}$.
71. **Posledica o invertibilnih elementih monoida:**
    Množica vseh invertibilnih elementov monoida $M$ (označena kot $M^{\times}$) tvori grupo pod isto operacijo.
72. **Pravila krajšanja v grupi:**
    Naj bo $(G, *)$ grupa.
    *   **Pravilo krajšanja z leve:** Če $a * b = a * c$, potem $b = c$ za vse $a, b, c \in G$.
    *   **Pravilo krajšanja z desne:** Če $b * a = c * a$, potem $b = c$ za vse $a, b, c \in G$.
73. **Enolična rešljivost enačb v grupi:**
    Za vsaka $a, b \in G$ velja:
    *   Enačba $a * x = b$ ima enolično rešitev $x = a^{-1} * b$.
    *   Enačba $x * a = b$ ima enolično rešitev $x = b * a^{-1}$.
74. **Trditev o multiplikativni grupi $\mathbb{Z}_n$:**
    $(\mathbb{Z}_n \setminus \{0\}, \cdot_n)$ je Abelova grupa, če in samo če je $n$ praštevilo.
75. **Trditev o ciklični podgrupi:**
    $\langle a \rangle = \{a^m \mid m \in \mathbb{Z}\}$ je Abelova podgrupa grupe $G$.
76. **Trditev o elementih ciklične podgrupe:**
    *   Če je red elementa $a$ neskončen, potem so vse potence $a^m$ (za različne $m \in \mathbb{Z}$) med seboj različne.
    *   Če je red elementa $a$ končen in enak $n$, potem $\langle a \rangle = \{e, a^1, a^2, \ldots, a^{n-1}\}$. V tem primeru velja $a^i = a^j$ natanko takrat, ko je $i \equiv j \pmod n$.
77. **Trditev o generatorjih ciklične grupe:**
    Naj bo $G = \langle x \rangle$ ciklična grupa reda $n \in \mathbb{N}$. Element $a \in G$ je generator grupe $G$ (tj. $G = \langle a \rangle$) natanko takrat, ko je $a = x^k$ za neko celo število $k$ in velja $\gcd(k, n) = 1$.
78. **Pravila za produkt parnosti permutacij:**
    *   Produkt dveh sodih permutacij je soda permutacija.
    *   Produkt dveh lihh permutacij je soda permutacija.
    *   Produkt sode in lihe permutacije je liha permutacija.
79. **Trditev o Alternirajoči grupi:**
    $A_n$ je podgrupa grupe $S_n$ ($A_n \le S_n$).
80. **Trditev o velikosti Alternirajoče grupe:**
    $|A_n| = |S_n| / 2 = n! / 2$.
81. **Lastnosti levih odsekov:**
    Naj bo $G$ grupa, $H \le G$ in $a, b \in G$.
    *   $a \in aH$.
    *   $aH = H \iff a \in H$.
    *   Dva leva odseka sta bodisi enaka ali disjunktna: $aH = bH$ ali $aH \cap bH = \emptyset$.
    *   $aH = bH \iff a^{-1} * b \in H$.
    *   Vsi levi (in desni) odseki imajo enako moč (število elementov) kot podgrupa $H$: $|aH| = |H|$.
82. **Posledica o particiji grupe z odseki:**
    Grupa $G$ se razpade na disjunktno unijo levih odsekov podgrupe $H$.
    $G = a_1H \cup a_2H \cup \ldots \cup a_kH$, kjer so $a_iH$ paroma disjunktni levi odseki.
83. **Lagrangeov izrek:**
    Naj bo $G$ končna grupa in $H$ njena podgrupa. Potem moč podgrupe $H$ deli moč grupe $G$. Število levih (ali desnih) odsekov podgrupe $H$ v grupi $G$ se imenuje indeks podgrupe $H$ v $G$ in je enak $[G:H] = |G| / |H|$.
84. **Posledica Lagrangeovega izreka (red elementa):**
    Če je $G$ končna grupa in $a \in G$, potem red elementa $a$ deli moč grupe $G$.
85. **Posledica Lagrangeovega izreka ($a^{|G|}=e$):**
    Če je $G$ končna grupa in $a \in G$, potem velja $a^{|G|} = e$.
86. **Posledica Lagrangeovega izreka (grupe praštevilskega reda):**
    Če je $G$ grupa, katere moč $|G|$ je praštevilo $p$, potem je $G$ ciklična.
87. **Mali Fermatov izrek:**
    Če je $p$ praštevilo in $a$ celo število, potem velja $a^p \equiv a \pmod p$.
88. **Trditev o konjugiranosti kot ekvivalenčni relaciji:**
    Konjugiranost je ekvivalenčna relacija na grupi $G$.
89. **Trditev o redu konjugiranih elementov:**
    Če sta $g$ in $g'$ konjugirana, potem imata isti red.
90. **Karakterizacija konjugiranosti v $S_n$:**
    Dve permutaciji v $S_n$ sta konjugirani natanko takrat, ko imata isto ciklično strukturo (tj. enako število ciklov iste dolžine).
91. **Trditev o konjugirani podgrupi:**
    Če je $H \le G$ podgrupa in $g \in G$, potem je množica $gHg^{-1} = \{ghg^{-1} \mid h \in H\}$ tudi podgrupa grupe $G$.
92. **Trditev o Centru grupe:**
    Center grupe $G$, $Z(G) = \{a \in G \mid a * b = b * a \quad \forall b \in G\}$, je Abelova podgrupa grupe $G$.
93. **Trditev o Alternirajoči grupi kot normalni podgrupi:**
    Alternirajoča grupa $A_n$ je normalna podgrupa simetrične grupe $S_n$ za $n \ge 2$.
94. **Izrek o kvocientni grupi:**
    Naj bo $G$ grupa in $H \triangleleft G$ normalna podgrupa. Potem je na množici levih odsekov $G/H = \{aH \mid a \in G\}$ operacija $(aH) * (bH) = (ab)H$ dobro definirana, in $G/H$ je z njo grupa.
95. **Lastnosti homomorfizma grup:**
    Naj bosta $G$ in $G'$ grupi (z enotama $e$ in $e'$) in $f: G \to G'$ homomorfizem.
    *   $f(e) = e'$.
    *   $f(g^{-1}) = (f(g))^{-1}$ za vse $g \in G$.
    *   Slika $Im f = \{f(g) \mid g \in G\}$ je podgrupa grupe $G'$.
    *   Jedro $Ker f = \{g \in G \mid f(g) = e'\}$ je normalna podgrupa grupe $G$.
    *   Homomorfizem $f$ je injektiven (1-1), natanko takrat, ko je njegovo jedro trivialna podgrupa, $Ker f = \{e\}$.
    *   Če sta $f: G_1 \to G_2$ in $g: G_2 \to G_3$ homomorfizma, potem je tudi njun kompozitum $g \circ f: G_1 \to G_3$ homomorfizem.
    *   Če je $f: G_1 \to G_2$ bijektiven homomorfizem, potem je tudi njegova inverzna preslikava $f^{-1}: G_2 \to G_1$ homomorfizem.
96. **Trditev o injektivnosti in izomorfizmu na sliko:**
    Če je $f: G \to G'$ injektiven homomorfizem, potem je grupa $G$ izomorfna podgrupi $Im f \le G'$.
97. **Prvi Izrek o Izomorfizmu (za grupe):**
    Naj bo $f: G \to G'$ homomorfizem grup. Potem je kvocientna grupa $G / Ker f$ izomorfna sliki $Im f$:
    $$G / Ker f \cong Im f$$
98. **Cayleyjev izrek (za grupe):**
    Vsaka grupa $G$ je izomorfna podgrupi neke grupe permutacij.
99. **Lastnosti direktnega produkta grup:**
    *   Če sta $G_1$ in $G_2$ Abelovi grupi, potem je tudi njun direktni produkt $G_1 \times G_2$ Abelova grupa.
    *   Komutativnost: $G_1 \times G_2 \cong G_2 \times G_1$.
    *   Asociativnost: $(G_1 \times G_2) \times G_3 \cong G_1 \times (G_2 \times G_3)$.
100. **Kitajski ostanek izrek za grupe:**
    $$\mathbb{Z}_{mn} \cong \mathbb{Z}_m \times \mathbb{Z}_n$$, če sta $m$ in $n$ tuja ($\gcd(m,n)=1$).
101. **Osnovne lastnosti množenja v kolobarju:**
    Za vsak kolobar $R$ in $a, b \in R$ velja:
    *   $0_R \cdot a = 0_R = a \cdot 0_R$.
    *   $(-a) \cdot b = a \cdot (-b) = -(a \cdot b)$.
102. **Trditev o idealu, ki vsebuje enoto:**
    Če je $I \triangleleft R$ ideal in $R$ je kolobar z enoto $1_R$, in če $1_R \in I$, potem je $I = R$.
103. **Trditev o dobro definiranosti množenja v kvocientnem kolobarju:**
    Če je $I \triangleleft R$ ideal, je operacija množenja odsekov $(a+I) \cdot (b+I) = (a \cdot b)+I$ dobro definirana.
104. **Izrek o kvocientnem kolobarju:**
    Če je $I \triangleleft R$ ideal, je z definiranim seštevanjem in množenjem $(R/I, +, \cdot)$ kolobar.
105. **Trditev o karakteristiki kolobarja z enoto:**
    Če je $R$ kolobar z enoto $1_R$, potem je karakteristika kolobarja $R$ najmanjše pozitivno naravno število $n$, za katerega je $n \cdot 1_R = 0_R$. Če tako število $n$ ne obstaja, je karakteristika $0$.
106. **Lastnosti homomorfizma kolobarjev:**
    Naj bo $f: R \to R'$ homomorfizem kolobarjev.
    *   $f(0_R) = 0_{R'}$.
    *   $f(-a) = -f(a)$ za vse $a \in R$.
    *   Slika $Im f = \{f(a) \mid a \in R\}$ je podkolobar kolobarja $R'$.
    *   Jedro $Ker f = \{a \in R \mid f(a) = 0_{R'}\}$ je ideal kolobarja $R$.
    *   Homomorfizem $f$ je injektiven, natanko takrat, ko je $Ker f = \{0_R\}$.
    *   Inverz bijektivnega homomorfizma je tudi izomorfizem.
107. **Prvi Izrek o Izomorfizmu (za kolobarje):**
    Naj bo $f: R \to R'$ homomorfizem kolobarjev. Potem je kvocientni kolobar $R / Ker f$ izomorfen sliki $Im f$:
    $$R / Ker f \cong Im f$$
108. **Pravilo krajšanja v celem kolobarju:**
    V celem kolobarju $R$, če $a \ne 0_R$ in $a \cdot b = a \cdot c$, potem $b = c$.
109. **Trditev o karakteristiki celega kolobarja:**
    Če je $R$ cel kolobar, potem je njegova karakteristika $0$ ali pa praštevilo.
110. **Izrek o kolobarju polinomov:**
    $R[x]$ je kolobar (imenovan kolobar polinomov nad $R$).
111. **Trditev o komutativnosti $R[x]$:**
    Če je $R$ komutativen, je tudi $R[x]$ komutativen.
112. **Trditev o enoti $R[x]$:**
    Če $R$ ima enoto $1_R$, ima tudi $R[x]$ enoto, ki je polinom $1 = (1_R, 0, 0, \ldots)$.
113. **Trditev o celosti $R[x]$:**
    Če je $R$ cel kolobar, je tudi $R[x]$ cel kolobar.
114. **Posledica o stopnji produkta polinomov v celem kolobarju:**
    $\deg(f(x) \cdot g(x)) = \deg f(x) + \deg g(x)$ velja, če $R$ nima deliteljev niča.
115. **Izrek o Deljenju Polinomov (Division Algorithm for Polynomials):**
    Naj bo $F$ polje, in naj bosta $p(x), g(x) \in F[x]$ polinoma, pri čemer $g(x) \ne 0$. Potem obstajata enolično določena polinoma $r(x), o(x) \in F[x]$, tako da velja:
    $$p(x) = r(x) \cdot g(x) + o(x)$$
    in $\deg o(x) < \deg g(x)$ (ali $o(x)$ je ničelni polinom).
116. **Faktorski izrek:**
    Naj bo $F$ polje in $p(x) \in F[x]$. Potem je $a \in F$ ničla polinoma $p(x)$ natanko takrat, ko je $(x-a)$ faktor polinoma $p(x)$, tj. $p(x) = r(x) \cdot (x-a)$ za nek polinom $r(x) \in F[x]$.
117. **Trditev o številu ničel polinoma:**
    Naj bo $F$ polje in $p(x) \in F[x]$ neničelni polinom stopnje $n$. Potem ima $p(x)$ največ $n$ ničel v $F$.
118. **Fundamentalni Izrek Algebre:**
    V $\mathbb{C}[x]$ (kolobarju polinomov nad kompleksnimi števili) ni nerazcepnih polinomov stopnje $\ge 2$.
119. **Trditev o nerazcepnih polinomih v $\mathbb{R}[x]$:**
    V $\mathbb{R}[x]$ (kolobarju polinomov nad realnimi števili) ni nerazcepnih polinomov stopnje $\ge 3$.
120. **Trditev o polju kot celem kolobarju:**
    Če je $R$ polje, potem je $R$ cel kolobar.
121. **Trditev o končnem celem kolobarju:**
    Če je $R$ končen cel kolobar, potem je $R$ polje.
122. **Trditev o idealih v polju:**
    V polju (ali obsegu) sta edina ideala trivialni ideal $\{0_F\}$ in nepravi ideal $F$.
123. **Trditev o injektivnosti homomorfizmov polj:**
    Vsak homomorfizem polj je injektiven.
124. **Trditev o karakteristiki končnega polja:**
    Karakteristika končnega polja je vedno praštevilo $p$.
125. **Trditev o obstoju in edinstvenosti končnih polj:**
    Za vsako praštevilo $p$ in vsako naravno število $k \ge 1$ obstaja polje velikosti $p^k$. Do izomorfizma natančno obstaja natanko eno polje velikosti $p^k$.