Naj bo $G$ neusmerjen graf.

**Prirejanje** je podmnožica povezave $M \subseteq   E$ za katero velja da nobeni povezavi nimata skupnih vozlišč oz. $e,f \in M, e \neq f \Rightarrow e \cap f \neq \emptyset$.
**Pokritje** je podmnožica vozlišč $P \subset  V$ če velja da $\forall  e \in E$ obstaja $v \in P$ da je $v \in e$.

**Popolno prirejanje** je če je vsako vozlišče krajišče neke povezave v prirejanju.

Iščemo **največje prirejanje** in **najmanjše pokritje**. *Največje prirejanje na grafu.*

**Maksimalno prirejanje** je prirejanje kateremu ne moremo dodati več povezav.

$$\mu(G) = \text{ velikost največjega prirejanja}$$
$$\tau (G) = \text{ velikost najmanjšega pokritja}$$

> Naj bo $M$ prirejanje, $P$ pa pokritje.
> Velja da je $|M| \leq |P|$.
> >[!|dokaz]+ Dokaz:
> > Za $e \in M$ obstaja $v \in P, v \in e$. Za različne $e$ dobimo različne $v$ *ker imamo prirejanje.*
> > Dobimo injektivno preslikavo iz $M \rightarrow P$.

>$\mu(G) \leq \tau(G)$. *Sledi neposredno iz prejšnjega izreka.*


> Če je $|M| = |P|$ je $M$ največje prirejanje $P$ pa najmanjše pokritje torej $\mu(G) = \tau(G) = |M| = |T|$.
>  *Sledi neposredno iz prejšnjega izreka.*


**Opomba:** V splošnem ne velja da je $\tau(G) = \mu(G)$.

Naj bo $M$ prirejanje. 

Velja da je $e \in M$ **vezana povezava**, $e \notin M$ pa **prosta**.  *Vezane so vijugaste, proste pa navadne.*

Če za $v$ obstaja $e \in M$ da je $v \in e$ potem je **vozlišče vezano**, če ne obstaja pa **prosto**.

Če je $uv \in M$ potem je $u$ **par** $v$.

**Alternirajoča pot** je pot na kateri si izmenjujejo proste in vezane povezave.

**Povečujoča pot** je alternirajoča pot ki se začne in konča s prostim vozliščem. *Pazimo da gledamo vozlišča ne povezave.*

> Če na povečujoči poti zamenjamo proste in vezane povezave dobimo ravno za 1 večje prirejanje.

**Opomba:** Povečujoča pot ima vedno liho število prostih povezav.

**Def.:** $A \oplus B = (A \setminus B) \cup (B \setminus A)$

> **Bergeev izrek**
> Naj bo $G$ graf, $M$ prirejanje.
> $M$ je največje prirejanje $\Leftrightarrow$ ne obstaja povečujoča pot
> >[!|dokaz]+ Dokaz:
> > $(\Rightarrow)$ že dokazano saj obstoj povečujoče poti pomeni da obstaja večje prirejanje ampak že imamo največje prirejanje
> > 
> > $(\Leftarrow)$
> > Naj bo $M$ prirejanje ki ni največje in $M' : |M'| > |M|$ večje prirejanje. Hočemo dokazati da obstaja povečujoča pot da dobimo $M'$.
> > Vzamemo graf $H := M \oplus M', V(H) = V(G)$.
> > Stopnja vozlišča v grafu $H$ bo $d_{H}(v)\leq 2$. 
> > 
> > *V $v$-ju je največ ena povezava iz $M$ in največ ena povezava iz $M'$ torej stopnje 2, lahko je samo iz ene od teh ali pa iz nobene.*
> >
> > Komponente grafa $H$ so poti in sodi cikli (ker se morajo $M$ in $M'$ izmenjevati). V sodih ciklih in poteh imamo enako število $M$ in $M'$-jev zato mora obstajati pot ki ima več $M'$ kot $M$-jev kar pomeni da se začne in konča z $M'$.
> >Velja da obstaja $M',M,M',...,M,M'$ za katero trdimo da je povečujoča glede na $M$.
> > 
> > Najprej preverimo ali je pot alternirajoča. $M$ povezave so vezane, povezave v $M'$ pa vemo da niso v $M$ saj smo njun presek odšteli torej morajo biti nepovezane.
> > 
> > Preverimo še da sta prvo in končno vozlišče prosti oz. ali je lahko $v_{0}$ še povezano s kakšno povezavo iz $M$ *za $v_{k}$ velja isto.*
> > 
> > Če $v_{0}$ ni prost v $M$ potem obstaja neka povezava $e$ ki pripada prirejanju $M$ in se dotika $v_{0}$.
> > 
> > Ta povezava je lahko v $H$ oz. ekvivalentno v $M$ in ne v $M'$. To bi pomenilo da se pot začne s povezavo iz $M$. To ni mogoče ker potem imamo enako število $M$ in $M'$ kar potem ni naša komponenta.
> > 
> > Če ta povezava ni v $H$ potem sovpada z $M'$ in bi se ta povezava morala izbrisati. Ker je $v_{0}$ povezan s povezavo iz $M'$ to očitno ne more veljati.
> > 
> > Torej je to povečujoča pot.

Za iskanje največjega prirejanja **iščemo povečujoče poti** in jih dodajamo v prirejanje dokler ne obstajajo več.

Iskanje povečujočih poti v splošnih grafih je zapleten $O(|E| \cdot |V|)$.

***

**Madžarska metoda** je iskanje povečujočih poti v dvodelnih grafih.

Naj bo $G$ dvodelni graf in $M$ prirejanje.

$$V = X \cup Y$$
$$S = \{ \text{prosta vozlišča v } X\}$$
$$T = \{ \}$$

Na vsakem koraku bo

$$S' = S \cup \{ v \in X \text{ do katerih lahko pridemo po vezanih povezavah iz $T$}\}$$
$$T' = T \cup  \{ \text{$v \in Y$ do katerih lahko pridemo po prostih povezavah iz $S$}\}$$

Če v nekem trenutku $T$ vsebuje prosto vozlišče smo našli povečujočo pot.

Sicer dobimo $S' = S$ in $T' = T$.

> Naj se madžarska metoda ustavi. $S'=S$, $T'=T$. 
> Velja da je $P := (X \setminus S) \cup T\,$ pokritje in da je  $|P| = |M|$.
> Iz tega neposredno sledi da $M$ je največje prirejanje, $P$ najmanjše pokritje, $\mu(G) = \tau (G)$.
> >[!|dokaz]+ Dokaz:
> > Imamo $S$ in $X \setminus S$ in $T$ in $Y \setminus T$.
> >
> >Trdimo da se nekatere povezave ne morejo pojaviti.
> >
> >Med $S$ in $Y \setminus T$ ni vezanih povezav, ker je vozlišče iz $S$ posledica obstoja vezane povezave vozlišča iz $T$.
> >Hkrati ne morajo obstajati proste povezave med $S$ in $Y \setminus T$ ker drugače bi lahko še dodajali vozlišča v $T$.
> >Med $X \setminus S$ in $T$ pa ne morejo obstajati vezane povezave, ker bi drugače lahko z njimi povečali $S$. 
> > 
> > Torej obstajajo samo spodnje povezave, kjer je bela povezava prosta, rdeča pa vezana.
> > 
> > $$
> > \begin{array}{ccc}
> > S & & X \setminus S \\
> > | \color{red}{|} & \diagup & | \color{red}{|} \\
> > T & & Y \setminus T
> > \end{array}
> > $$
> > 
> > Torej je $P$ pokritje, saj velja da je $P$ definiran kot $(X \setminus S) \cup T$ in vidimo da obstaja povezava med vsemi vozlišči saj je $T$ povezan s $S$ in $X \backslash S$,ta pa je povezan še z $Y \backslash T$.
> > 
> > Dokažimo še $|M| = |P|$.
> > $$M_{1} := \{ \text{vezane povezave med $S$ in $T$}\}$$
> > $$M_{2} := \{ \text{vezane povezave med $X \setminus S$ in $Y \setminus T$}\}$$
> > *torej vse rdeče povezave*
> > 
> > Očitno je da je $|M| = |M_{1}|+|M_{2}|$
> > 
> > Trdimo da je $|M_{1}|=|T|$, saj v $T$ ne more biti prostih vozlišč ker bi drugače imeli povečujočo pot.
> > Trdimo da je $|M_{2}|=|X\backslash S|$, saj so po definciiji vsa prosta vozlišča že v $S$.
> > 
> > $\Rightarrow$ $|M| = |T| + |X\backslash S| = |P|$
> > 

**Posledica:** V vsakem dovdelnem grafu je $\mu(G) = \tau(G)$. *Madžarska metoda nam da prirejanje velikosti $T \cup (X \setminus S)$, kar je enako pokritju.*

Iz tega dobimo 4 probleme

Iskanje največjega prirejanja in najmanjšega pokritja v dvodelnem grafu.

Iskanje največjega prirejanja in najmanjšega pokritja v splošnem grafu.

Prvi trije so lahki, medtem ko je iskanje najmanjšega pokrtija $NP$-poln.

***

**Hallov izrek** pravi da če imamo dvodelen graf potem obstaja popolno prirejanje iz $X$ v $Y$ $\Leftrightarrow$ $\forall A \subset X : |A| \leq |N(A)|$ .
>[!|dokaz]+ Dokaz:
> ($\Rightarrow$) 
> Ker imamo že prirejanje nam za vsako podmnožico določa injektivno preslikavo v $N(A)$. 
> Torej naj bo $A$ polj. podmn. $X$, s pop. prirejanjem imamo bijekcijo $A \rightarrow B$ kjer je $B \subseteq N(A)$ oz. torej injekcijo $A \rightarrow N(A)$. Torej velja $|A| \leq |N(A)|$.
> ($\Leftarrow$)
> Naj bo $M$ največje prirejanje in $S,T$ pridobljena iz madžarske metode. Velja da je $|S| \leq |N(S)|$ *po predpostavki.*
> Hkrati velja tudi $N(S) \subseteq T$ torej velja $|N(S)| \leq |T|$ $\Rightarrow |S| \leq |T|$
> Iz prejšnjega izreka vemo da je $|M| = |P| = |X \backslash S| + |T| \geq |X\backslash S| + |S| = |X|$
> $|M| \geq |X|$, ampak ker prirejanje ne more imeti več povezav kolikor je vozlišč v $X$ velja $|M| = |X|$
> $\Rightarrow$ $M$ je popolno prirejanje iz $X$ v $Y$.

**Posledica:** Če je $G$ dvodelen graf kjer velja $|X|=|Y|$ potem obstaja popolno prirejanje v $G$.

***


** Sistem različnih predstavnikov (SDR)**

Naj bo $A_{i}$ družina množic.

Zaporedje elementov $x_1, x_2, \dots, x_n$ je **sistem različnih predstavnikov** za družino končnih množic $A_1, A_2, \dots, A_n$, če za vse $i, j \in \{1, 2, \dots, n\}$ velja:
1.  $x_i \in A_i$ (vsak element je iz "svoje" množice)
2.  $x_i \neq x_j$, če $i \neq j$ (vsi predstavniki so različni)

**Primer:**
$A_1 = \{a, b\}$, $A_2 = \{a, c\}$, $A_3 = \{b, c, d\}$, $A_4 = \{a, d\}$
Možen SDR je:
*   predstavnik($A_1$) = $a$
*   predstavnik($A_2$) = $c$
*   predstavnik($A_3$) = $b$
*   predstavnik($A_4$) = $d$

*V resnici iščemo pooplno prirejanje iz družine množic v množico vseh elementov.*

**Posledica (Hallov pogoj):**
Sistem različnih predstavnikov za družino množic $A_1, A_2, \dots, A_n$ obstaja $\iff \forall I \subseteq \{1, 2, \dots, n\} : |\bigcup_{i \in I} A_i| \geq |I|$.

**Dokaz:**
Definiramo dvodelni graf $G = (X \cup Y, E)$ takole:
*   $X = \{1, 2, \dots, n\}$ (indeksi množic)
*   $Y = \bigcup_{i=1}^n A_i$ (vsi možni elementi)
*   Povezava $ix \in E$ obstaja, če velja $x \in A_i$.
Nato uporabimo **Hallov izrek**.

***

**Iskanje najcenejšega uteženega prirejanja**

Naj bo $G = K_{n,n}$ poln dvodelen graf. Vemo da obstaja $n!$ popolnih prirejanj.

Naj ima povezava med $x_{i}$ in $y_{j}$ utež $c_{ij}$.

$$C = [c_{ij}] \in \mathbb{R}^{n \times n}$$

Popolno prirejanje je podano z neko $\pi \in S_{n}$

$$x_{i} \sim y_{\pi(i)}$$

in utežjo

$$\sum_{i=1}^{n}c_{i \pi(i)}$$

Iščemo prirejanje z najmanjšo težo.

Torej 

$$\min_{\pi \in  S_{n}} \sum_{i=1}^{n}c_{i\pi(i)}$$

To se ponavadi interpretira kot razporeditev opravil, kjer so elementi v $X$ ljudje v $Y$ pa opravila, cene da nek človek opravlji opravilo pa so podane s $c_{ij}$.

To rešujemo z **madžarsko metodo z utežmi**.

V matriki bomo morali seveda za popolno prirejanje izbrati natanko en element vsake vrstice oz. stolpca.

Najprej opazimo da prištevanje konstante stolpcu ali vrstici ne vpliva na to kakšno prirejanje izberemo na koncu. 

Na vsak način moramo izbrati en element iz vsakega stolpca oz. vrstice, torej če v isti vrstici vse povečamo za konstanto ne vpliva na izbiro ampak le na končen rezultat. *Minimum v vrstici bo še vedno min. v vrstici oz. stolpcu.*

**Madžarska metoda z utežmi**

Od vsake vrstice odštejemo min. in od vsakega stolpca odštejemo njegov min.

V vsaki vrstici oz. stolpcu dobimo vsaj eno ničlo.

Najdemo neodvisne ničle ki nam dajo rešitev, če se to ne da moramo pokriti vse ničle z manj kot $n$ vrsticami in stolpci.

Naj bo $\varepsilon$ najmanjše nepokrito polje večje od $0$. Od nepokritih polj odštejemo $\varepsilon$, dvakrat pokritim poljem pa prištejemo $\varepsilon$. *Če se to ne da obstajajo neodvisne ničle.*

Nato ponovimo postopek

Neodvisne ničle nam dajejo najcenejše popolno prirejanje kjer velja $e \in M$ kjer je $e = ij$, kjer je $c_{ij}=0$ neodvisna ničla.

***

**Zakaj MMU deluje in kako poiščemo vrstice in stolpce oz. ničle**
 
> **Dfn.:** Ničelni graf za pripadajočo matriko.
> 
> Naj bodo vozlišča na levi $v_{1},...,v_{n}$ za vrstice in $s_{1},...,s_{n}$ za stolpce.
> 
> Povezave so definirane kot $v_{i} \sim s_{j} \Leftrightarrow c_{ij}=0$.

Vsak korak nas privede na dve opciji

V ničelnem grafu poiščemo največje prirejanje $M$. Imamo dve možnosti:
- največje prirejanje je manjše od $n$ $\Rightarrow|P| < n$, $P$ določa manj kot $n$ vrstic in stolpcev ki pokrijejo vse ničle. *Če izberemo neko vrstico s $k$ ničlami, v grafu izberemo vozlišče s $k$ povezavami do vseh vozlišč stolpcev v katerih so ničle.*
  *V praksi na ničelnem grafu izvedemo madžarsko metodo, če je manj kot $n$ povezav v prirejanju, torej nimamo popolnega prirejanja, bo manj kot $n$ povezav v pripadajočem najmanjšem pokritju z manj kot $n$ elementi kar nam pove katere stolpce in vrstice moramo vzeti.*
- $|M| = n$, $M$ je najcenejše popolno prirejanje.

**Pokažemo še da odštevanje min. elementa nepokritih še vedno da isti problem.**

Naj bo $P= (X\setminus S)\cup T$ pokritje ničelnega grafa.

Vrstice označujejo elemente $X \cup (X\setminus S)$, stolpci pa označujejo elemente $T \cup (Y \setminus T)$. V pokritju so elementi $X \setminus S$ *torej vrstice ki označujejo vozlišča ki pripadajo $X \setminus S$*, in elementi $T$ *torej stolpci ki označujejo vozlišča ki pripadajo $T$*. Ker pokrivamo vrstice in stolpce, ki vsebujejo ničle, bodo dvojno pokrite ravno tiste povezave ki grejo iz $X\setminus S$ v $T$. Nepokrite pa bodo tiste ki gredo iz $S$ v $Y \setminus T$.

Naj bo $\varepsilon = \min(c_{ij} \,;\;i \in S, j \in Y \setminus T)$ oz. najmanjša nepokrita povezava.

Če prištejem $\varepsilon$ vsem povezavam iz $X \setminus S$ oz. vsem vrsticam, ki vsebujejo vozl. v $X \setminus S$ in odštejemo $\varepsilon$ vsem povezavam iz $Y \setminus T$ oz. vsem stolpcem ki vsebujejo vozl. iz $Y \setminus T$ dobimo spodnjo sliko.

![[Pasted image 20260511172854.png|500]]

Pokritim prištejemo $\varepsilon$, nepokritim pa odštejemo $\varepsilon$.
Enkrat pokritim se ne spermeni vrednost. *En del pokritih je nedotaknjen enemu pa prištejemo in odštejemo $\varepsilon$.*

Ker smo prištevali in odštevali vrsticam in stolpcem, nismo spremenili optimalne rešitve.



**Poakazati moramo še da se algoritem ustavi.**

Naj bo $P = T \cup (X \setminus S)$ še vedno pokritje ki ga dobimo z izvajanjem metode. Ko odštejemo in prištejemo $\varepsilon$, dobimo nove cene. Povezave med $S,T$ in $X\setminus S, Y \setminus T$ ostanejo enake in posledično ostanejo enake tudi v ničelnem grafu. *V novem ničelnem grafu, ki ga dobimo po uporabi $\varepsilon$ imamo še vedno isto prirejanje, ki pa ni nujno največje.*

Ker so povezave med $T$ in $X \setminus S$ samo takrat ko je utež $0$, jih v novem ničelnem grafu ne bo več*, saj smo prišteli $\varepsilon$*.

Nove povezave nastanejo med $S$ in $Y \setminus T$, *saj smo odšteli $\varepsilon$ in dobili ničle.* Dobimo vsaj eno povezavo, označena z $xy$ *ta povezava ni v prirejanju $M$ oz. je prosta.*

Dobimo dve možnosti - $y$ je lahko prost ali vezan. V obeh primerih lahko iz $S$-ja gremo po prosti povezavi, in dobimo povečujočo pot
- Če je $y$ prosto vozlišče pomeni da obstaja povečujoča pot. Poveča se $|M|$.
- Če je $y$ vezano vozlišče pomeni da se poveča $T$ *ker gremo po prosti povezavi iz $S$ v vozl. $y$ ki ga dodamo $T$*, ker vemo da je $y$ vezan pa bo vezana pot v $X \setminus S$ do nekega vozl. ki ga dodamo $S$, torej se poveča $S$.

Torej se na vsakem koraku poveča največje prirejanje ali pa, prirejanje ostane enako in se $S$ poveča. $S$ se lahko poveča največ $n$-krat.

Torej $\text{MMU}$ se gotovo konča po $O(n^{2})$ korakih.

Vsak korak je korak madžarske metode ki rabi $n^{2}$ operacij.

**Opomba:** Najdražje prirejanje dobimo če rešimo metodo z negativno matriko $C$.

***

**Aproksimacijski algoritem za iskanje minimialnega pokritja.**


$$G = (V, E)$$
$$c: V \rightarrow \mathbb{R}$$
$$\min \sum_{v \in V} c(v)$$

$$x_v = \begin{cases} 1; & v \in P \\ 0; & \text{sicer} \end{cases}$$

**Pogoji:** vsaka povezava mora biti pokrita

$$uv \in E: x_u + x_v \geq 1$$

**CLP $\Pi$ - Celoštevilski LP:**



$$\begin{array}{ll}
\\
\min & \sum_{v \in V} c_v \cdot x_v\\
\text{p.p.} & x_u \in \{0, 1\}\\ 
& x_u + x_v \geq 1 \,;\; \forall uv \in E
\end{array}$$



$$ $$
$$\downarrow$$

**$\Pi_R$ (Linearna relaksacija):**


$$\begin{array}{ll}
\\
\min & \sum_{v \in V} c_v \cdot x_v\\
\text{p.p.} & x_u \geq 0 , x_{u} \leq 1 \, ; \, \forall u \in V\\ 
& x_u + x_v \geq 1 \,;\, \forall uv \in E
\end{array}$$


Naj bo $x^* = (x_{v_1}^*, \dots, x_{v_n}^*)$ optimalna rešitev $\Pi_R$.

**Poiščemo dopustno rešitev $\Pi$ z zaokroževanjem:**
$$x_v' = \begin{cases} 1; & x_v^* \geq 1/2 \\ 0; & x_v^* < 1/2 \end{cases}$$

To je res dopustna (dop.) rešitev, saj $\forall uv \in E$ velja $x_u' + x_v' \geq 1$.

**Def. pokritje:** $P = \{ v \,;\; x_v' = 1 \}$. To je res pokritje.

Preverimo če je  $c(P) \leq (1 + \epsilon) c(P^*)$

*   $P$ je pokritje, ki smo ga definirali.
*   $P^*$ je najmanjše uteženo pokritje (optimalna celoštevilska rešitev).
*   Velja $\text{Opt}(\Pi_R) \leq \text{Opt}(\Pi)$ (vrednost relaksacije je vedno $\leq$ od celoštevilske).

**Dokaz faktorja:**

$$c(P) = \sum_{v \in V} c(v) \cdot x_v' \leq \sum_{v \in V} c(v) \cdot 2x_v^*$$
$$\sum_{v \in V} c(v) \cdot 2x_v^* = 2 \cdot \text{Opt}(\Pi_R)$$
$$2 \cdot \text{Opt}(\Pi_R) \leq 2 \cdot \text{Opt}(\Pi) = 2 \cdot c(P^*)$$


(Opomba: $x_v' \leq 2x_v^*$ velja, ker če je $x_v' = 1$, je $x_v^* \geq 1/2$, torej $2x_v^* \geq 1$).

$\implies c(P) \leq 2 \cdot c(P^*)$

$2 = (1 + \epsilon) \implies \epsilon = 1$

Torej je to **1-aproksimacijski algoritem** (oziroma faktor aproksimacije je 2).