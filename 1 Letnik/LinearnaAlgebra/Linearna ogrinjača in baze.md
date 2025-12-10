#### Linearna ogrinjača

**Definicija linearne ogrinjače**
Naj bo $V$ vektorski podprostor nad $F$ in naj bodo $v_1, \dots, v_k$ elementi $V$. Pravimo, da je vektor $v \in V$ **linearna kombinacija** vektorjev $v_1, \dots, v_k$, če obstajajo taki skalarji $\alpha_1, \dots, \alpha_k \in F$, da velja $v = \alpha_1 v_1 + \dots + \alpha_k v_k$.
Množico vseh linearnih kombinacij vektorjev $v_1, \dots, v_k$ označimo z $\text{Lin}\{v_1, \dots, v_k\}$ in ji pravimo **linearna ogrinjača** množice $\{v_1, \dots, v_k\}$.
S formulo: $\text{Lin}\{v_1, \dots, v_k\} := \{\alpha_1 v_1 + \dots + \alpha_k v_k \mid \alpha_1, \dots, \alpha_k \in F\}$.

**Trditev**
Za vsako končno podmnožico $S$ v vektorskem prostoru $V$ je njena linearna ogrinjača $\text{Lin } S$ vektorski podprostor v $V$.
**Dokaz:** Če $u_1, u_2 \in \text{Lin}\{v_1, \dots, v_k\}$ in $\gamma_1, \gamma_2 \in F$, potem bi radi dokazali, da $\gamma_1 u_1 + \gamma_2 u_2 \in \text{Lin}\{v_1, \dots, v_k\}$. Izberimo take skalarje $\alpha_1, \dots, \alpha_k$ in $\beta_1, \dots, \beta_k$, da je $u_1 = \alpha_1 v_1 + \dots + \alpha_k v_k$ in $u_2 = \beta_1 v_1 + \dots + \beta_k v_k$. 

Sledi
$\gamma_1 u_1 + \gamma_2 u_2 =$
$=\gamma_1(\alpha_1 v_1 + \dots + \alpha_k v_k) + \gamma_2(\beta_1 v_1 + \dots + \beta_k v_k) =$
$=(\gamma_1 \alpha_1 + \gamma_2 \beta_1)v_1 + \dots + (\gamma_1 \alpha_k + \gamma_2 \beta_k)v_k \in \text{Lin}\{v_1, \dots, v_k\}$



#### Definicija baze

Naj bo $V$ vektorski prostor. Vektor $v \in V$ se da izraziti kot linearna kombinacija vektorjev $v_1, \dots, v_n \in V$, če obstajajo taki skalarji $\alpha_1, \dots, \alpha_n$, da velja $v = \alpha_1 v_1 + \dots + \alpha_n v_n$. Pogosto lahko te skalarje izberemo na več različnih načinov.

**Definicija baze**
Naj bo $V$ vektorski prostor.

1\. Vektorji $v_1, \dots, v_n \in V$ so **ogrodje**, če se da vsak vektor $v \in V$ na vsaj en način izraziti kot linearna kombinacija $v_1, \dots, v_n$.

2\. Vektorji $v_1, \dots, v_n \in V$ so **linearno neodvisni**, če se da vsak vektor $v \in V$ na največ en način izraziti kot linearna kombinacija $v_1, \dots, v_n$.

>Vektorji $v_1, \dots, v_n \in V$ so **baza**, če se da vsak vektor $v \in V$ na natanko en način izraziti kot linearna kombinacija $v_1, \dots, v_n$.
>Očitno so vektorji $v_1, \dots, v_n \in V$ **baza** natanko tedaj, **ko so linearno neodvisni in ko so ogrodje.**


**Opomba:** Vektorji $v_1, \dots, v_n \in V$ so ogrodje natanko tedaj, ko je njihova linearna ogrinjača enaka $V$.

**Izrek 1 - Karakterizacije linearne neodvisnosti**
Za vektorje $v_1, \dots, v_n$ iz vektorskega prostora $V$ so ekvivalentne trditve:
1. Vektorji $v_1, \dots, v_n$ so linearno neodvisni.
2. Za vsake skalarje $\alpha_1, \dots, \alpha_n$, ki zadoščajo $\alpha_1 v_1 + \dots + \alpha_n v_n = 0$, velja $\alpha_1 = \dots = \alpha_n = 0$.
3. Nobeden od vektorjev $v_1, \dots, v_n$ se ne da izraziti kot linearna kombinacija preostalih vektorjev.

Dokas že opisan v [[Vektorji, Operacije, Lin. Neodvisnost#Linearna neodvisnost vektorjev|drugi datoteki]]



#### Obstoj baze

Spomnimo se, da je ogrodje vektorskega prostora $V$ taka podmnožica v $V$, da je njena linearna ogrinjača enaka $V$.

**Definicija**
Vektorski prostor je **končno-razsežen**, če ima končno ogrodje.

Spomnimo se, da je baza vektorskega prostora $V$ taka podmnožica v $V$, ki je linearno neodvisna in je ogrodje za $V$.

**Primer:** Prazna množica je baza vektorskega prostora $\{0\}$ oz. vsak vektorski prostor ima linearno neodvisno ogrodje - bazo.

**Izrek 2 - Obstoj baze**
Vsak končno-razsežen vektorski prostor ima končno bazo.

**Dokaz:** Naj bo $V$ končno-razsežen vektorski prostor in naj bo $S = \{v_1, \dots, v_n\}$ ogrodje z najmanj elementi. Dokazujemo da če to velja so tudi lin. neodvisni.
Recimo, da so vektorji $S$ linearno odvisni. Potem obstaja tak element $v_i \in S$, ki je linearna kombinacija elementov iz $S \setminus \{v_i\}$. To pomeni da lahko katerikoli vektor ki ga lahko izrazimo z originalnim ogrodjem lahko izrazimo z novim s tem da za $v_i$ vstavimo pripadajočo linearno kombinacijo. To pomeni da obstaja manjše ogrodje kar je v protislovju, torej morajo biti v tem ogrodju vektorji linearno neodvisni. 

**Primeri iz obstoja baze**
Zanima nas, kako za dano množico $\{v_1, \dots, v_m\} \subset F^n$ preverimo ali je ogrodje in kako poiščemo tako njeno podmnožico, ki je baza. Matriko $[v_1 \dots v_m]$ z Gaussovo metodo prevedemo v reducirano vrstično stopničasto formo $R$. Če ima $R$ ničelno vrstico, potem $\{v_1, \dots, v_m\}$ ni ogrodje. Če $R$ nima ničelne vrstice in če so $i_1, \dots, i_n$ zaporedne številke njenih pivotnih stolpcev potem je množica $\{v_{i_1}, \dots, v_{i_n}\}$ baza za $F^n$.

**Utemeljitev:** Če matriko $[v_1 \dots v_m]$ z leve množimo z elementarno matriko, se ohranijo vse linearne relacije med stolpci.

**Primer te metode**

Pokažimo, da so stolpci matrike

$$
A = \begin{bmatrix}
1 & 0 & 1 & 0 & 1 & 0 \\
1 & 0 & 0 & 1 & 0 & 1 \\
0 & 1 & 0 & 1 & 1 & 0 \\
0 & 1 & 1 & 0 & 0 & 1
\end{bmatrix}
$$

ogrodje za $F^4$ in poiščimo take štiri stolpce, ki so baza za $F^4$.


Z Gaussovo metodo izračunamo njeno reducirano vrstično kanonično formo

$$
R = \begin{bmatrix}
1 & 0 & 0 & 1 & 0 & 1 \\
0 & 1 & 0 & 1 & 0 & 1 \\
0 & 0 & 1 & -1 & 0 & 0 \\
0 & 0 & 0 & 0 & 1 & -1
\end{bmatrix}
$$

Ker matrika $R$ nima ničelne vrstice, so stolci matrike $A$ ogrodje za $F^4$. Zaporedne številke pivotnih stolpcev v $R$ so 1, 2, 3, 5. Stolpci v $A$ z istimi zaporednimi številkami so potem baza za $F^4$. Iz $R$ lahko odčitamo tudi, kako se s temi stolpci izražata preostala stolpca matrike $A$.

**Primer: $F[x]$ ni končno-razsežen**
Spomnimo se, da je $F[x]$ vektorski prostor vseh polinomov v $x$ s koeficienti iz $F$. Množica $\{1, x, x^2, \dots\}$ je ogrodje $F[x]$. Če bi imeli končno ogrodje $\{p_1, \dots, p_n\}$, potem bi vsak polinom $p$ iz $F[x]$ lahko izrazili kot
$p = \alpha_1 p_1 + \dots + \alpha_n p_n$, odkoder bi sledilo $\deg p \le \max\{\deg p_1, \dots, \deg p_n\}$, kar je protislovje, saj imajo lahko polinomi poljubno visoko stopnjo.

#### Enoličnost moči baze

**Trditev 2**
Naj bo $V$ vektorski prostor. Če so $u_1, \dots, u_m$ linearno neodvisni vektorji v $V$ in če so vektorji $v_1, \dots, v_n$ ogrodje za $V$, potem je $m \le n$.


**Dokaz:** 
Recimo da je $m>n$.
Množica $S_u = \{u_1, \dots, u_m\}$ naj bo linearno neodvisna. Ker $S_v$ razpenja prostor $V$, lahko vsak vektor $u_i \in S_u$ izrazimo kot linearno kombinacijo vektorjev iz $S_v$:
$$u_i = \sum_{j=1}^n \alpha_{ij} v_j \quad \text{za } i = 1, \dots, m.$$
Iščemo netrivialno rešitev, torej skalarje $x_1, \dots, x_m$, ki niso vsi enaki nič, za enačbo:
$$\sum_{i=1}^m x_i u_i = \vec{0}.$$
Z vstavitvijo izrazov za $u_i$ in zamenjavo vrstnega reda seštevanja dobimo:
$$\sum_{i=1}^m x_i \left(\sum_{j=1}^n \alpha_{ij} v_j\right) = \sum_{j=1}^n \left(\sum_{i=1}^m \alpha_{ij} x_i\right) v_j = \vec{0}.$$
Zadosten pogoj za veljavnost te enakosti je, da so vsi koeficienti pred vektorji $v_j$ enaki nič. To nas pripelje do homogenega sistema $n$ linearnih enačb za $m$ neznank $x_1, \dots, x_m$:
$$\sum_{i=1}^m \alpha_{ij} x_i = 0 \quad \text{za } j = 1, \dots, n.$$
Ker je po predpostavki $m > n$, ima ta sistem več neznank kot enačb, zato obstaja netrivialna rešitev $(x_1, \dots, x_m) \neq (0, \dots, 0)$. S tem smo našli skalarje, ki niso vsi enaki nič in za katere je $\sum_{i=1}^m x_i u_i = \vec{0}$. To pomeni, da je množica $S_u$ linearno odvisna, kar je v protislovju z našo začetno domnevo. $\blacksquare$

Oglejmo si nekaj posledic te trditve.

**Izrek 3 - Enoličnost moči baze**
Če ima vektorski prostor $V$ bazo z $n$ elementi, potem velja:
* Vsaka linearno neodvisna množica v $V$ ima $\le n$ elementov.
* Vsako ogrodje v $V$ ima $\ge n$ elementov.
* Vsaka baza v $V$ ima $n$ elementov.

>[!|dokaz]- Dokaz za enoličnost baze brez izreka prej:
> Naj bo $V$ končno-razsežen vektorski prostor.
> Obstajata dve bazi $X = \{x_1, x_2, \dots, x_m\}$ z $m$ elementi in $Y = \{y_1, y_2, \dots, y_n\}$ z $n$ elementi.
> Želimo dokazati, da mora veljati $m=n$.
> 
> Ker sta tako $X$ kot $Y$ bazi, obe razpenjata celoten prostor in sta linearno neodvisni.
> 
> Predpostavimo za protislovje, da je $m > n$. Torej ima baza $X$ več elementov kot baza $Y$.
> Ker $Y = \{y_1, \dots, y_n\}$ razpenja celoten prostor $V$, lahko vsak element $x_k \in X$ izrazimo kot linearno kombinacijo elementov iz $Y$. Vzemimo prvi element $x_1 \in X$. Ker je $x_1 \neq 0$, mora imeti vsaj en $y_j$ v tej kombinaciji neničelni koeficient. Recimo, da je to $y_1$. Potem lahko $y_1$ izrazimo kot linearno kombinacijo $x_1, y_2, \dots, y_n$. Dobimo novo množico $Y_1 = \{x_1, y_2, \dots, y_n\}$ ki **še vedno razpenja $V$**.
> 
> Ta postopek nadaljujemo. V vsakem koraku vzamemo naslednji element $x_k$ iz $X$. Ker je $X$ linearno neodvisna množica, $x_k$ ne more biti linearna kombinacija samo že vnesenih $x_j$ (za $j<k$). Zato mora v kombinaciji $x_k$ z elementi trenutne razpenjalne množice obstajati vsaj en originalni $y_j$ (ki še ni bil nadomeščen) z neničelnim koeficientom. Tega $y_j$ lahko nato izrazimo in ga zamenjamo z $x_k$. 
> 
> Dobimo novo razpenjalno množico $X' = \{x_1, x_2, \dots, x_n\}$, ki ima $n$ elementov in razpenja $V$.
> 
> Ker pa smo predpostavili, da je $m > n$, obstaja še vsaj en element $x_{n+1} \in X$.
> Ker $X'$ razpenja celoten prostor, mora biti $x_{n+1}$ mogoče izraziti kot linearno kombinacijo njenih elementov: $x_{n+1} = c_1 x_1 + c_2 x_2 + \dots + c_n x_n$.
> To pa implicira, da so vektorji $\{x_1, x_2, \dots, x_n, x_{n+1}\}$ linearno odvisni.
> Vendar je $X = \{x_1, \dots, x_m\}$ baza in je po definiciji linearno neodvisna množica.
> S tem smo prišli do protislovja. Naša prvotna predpostavka, da je $m > n$, je torej napačna. Sledi, da mora veljati $m \le n$.
> Naredimo enako le da obrnemo neenakosti in dobim $m=n$

**Dokaz:** Recimo, da je $v_1, \dots, v_n$ baza za $V$ in so $u_1, \dots, u_m \in V$ poljubni.
* Prvo točko dokažemo takole. Predpostavimo, da so $u_1, \dots, u_m$ linearno neodvisni. Ker so $v_1, \dots, v_n$ ogrodje, je po Trditvi 2 $m \le n$.
* Drugo točko dokažemo takole. Predpostavimo, da so $u_1, \dots, u_m$ ogrodje. Ker so $v_1, \dots, v_n$ linearno neodvisni, je po Trditvi 2 $n \le m$.
* Očitno tretja točka sledi iz prvih dveh.

**Definicija dimenzije**
Razsežnost (=dimenzija) vektorskega prostora je število elementov katerekoli njegove baze. Pravimo, da je vektorski prostor $n$-razsežen (=$n$-dimenzionalen), če ima razsežnost $n$.

**Primer dimenzije**
Vektorski prostor $F^n$ je $n$-razsežen, ker ima standardna baza $n$ elementov. Vektorski prostor $M_{m,n}(F)$ $m \times n$ matrik nad $F$ je $mn$-razsežen, ker ima bazo iz $mn$ koordinatnih matrik $E_{i,j}$.

Iz dokaza Izreka 2 sledi:

**Trditev 3**
Naj bo $V$ $n$-razsežen vektorski prostor. Potem je vsako ogrodje za $V$, ki ima $n$ elementov, baza za $V$.

**Primer iz enoličnosti moči baze**
Naj bo $F$ polje in $S$ neskončna množica. Pokažimo, da vektorski prostor $F^S$ vseh funkcij iz $S$ v $F$ ni končno-razsežen. Recimo, da ima $F^S$ ogrodje iz $n$ elementov. Konstruirali bomo linearno neodvisno množico v $F^S$, ki ima $n+1$ elementov, kar je v nasprotju z Izrekom 3.
Za vsak $s \in S$ označimo z $\delta_s$ funkcijo, ki pošlje element $s$ v $1$, elemente iz $S \setminus \{s\}$ pa v nič. Ker je $S$ neskončna množica, lahko izberemo $n+1$ paroma različnih elementov $s_1, \dots, s_{n+1} \in S$. Pokažimo, da so funkcije $\delta_{s_1}, \dots, \delta_{s_{n+1}}$ linearno neodvisne. Recimo, da velja
$\alpha_1 \delta_{s_1} + \dots + \alpha_{n+1} \delta_{s_{n+1}} = 0$
za neke skalarje $\alpha_1, \dots, \alpha_{n+1} \in F$. Potem za vsak $x \in S$ velja
$\alpha_1 \delta_{s_1}(x) + \dots + \alpha_{n+1} \delta_{s_{n+1}}(x) = 0$.
Ko vstavimo $x = s_i$ za $i = 1, \dots, n+1$, in upoštevamo $\delta_j(s_i) = 0$ za vsak $j \ne i$, dobimo $\alpha_i \delta_{s_i}(s_i) = 0$. Ker je $\delta_{s_i}(s_i) = 1$, sledi $\alpha_i = 0$.

#### Dopolnitev linearno neodvisne množice do baze

V tem razdelku bomo dokazali, da vsako linearno množico dopolnimo do baze. Začnimo z pomožno trditvijo.

**Trditev 4**
Če so vektorji $v_1, \dots, v_m$ linearno neodvisni, in če vektor $v_{m+1}$ ne leži v njihovi linearni ogrinjači, potem so tudi vektorji $v_1, \dots, v_m, v_{m+1}$ linearno neodvisni.

**Dokaz:** Recimo, da so vektorji $v_1, \dots, v_m$ linearno neodvisni, in da vektor $v_{m+1}$ ne leži v njihovi linearni ogrinjači. Vzemimo take $\alpha_1, \dots, \alpha_m, \alpha_{m+1}$, da velja $\alpha_1 v_1 + \dots + \alpha_m v_m + \alpha_{m+1} v_{m+1} = 0$. Radi bi dokazali, da velja $\alpha_1 = \dots = \alpha_m = \alpha_{m+1} = 0$. Ločimo dva primera.
* Če je $\alpha_{m+1} \ne 0$, potem velja $v_{m+1} = -\frac{1}{\alpha_{m+1}}(\alpha_1 v_1 + \dots + \alpha_m v_m)$, kar je v nasprotju s predpostavko, da $v_{m+1}$ ne leži v linearni ogrinjači $v_1, \dots, v_m$.
* Če je $\alpha_{m+1} = 0$, potem velja $\alpha_1 v_1 + \dots + \alpha_m v_m = 0$. Ker so vektorji $v_1, \dots, v_m$ linearno neodvisni, je $\alpha_1 = \dots = \alpha_m = 0$.

**Trditev 5**
Naj bo $V$ $n$-razsežen vektorski prostor. Vsaka linearno neodvisna množica v $V$, ki ima $n$ elementov, je baza.

**Dokaz:** Če so vektorji $v_1, \dots, v_n \in V$ linearno neodvisni, niso pa baza, potem niso ogrodje. Torej obstaja tak vektor $v_{n+1}$, ki ne leži v linearni ogrinjači vektorjev $v_1, \dots, v_n$. Po Trditvi 4 so vektorji $v_1, \dots, v_n, v_{n+1}$ linearno neodvisni. Ker je $V$ $n$-razsežen, ima ogrodje z $n$ elementi. Po Trditvi 2 ima vsaka linearno neodvisna množica manj ali enako elementov kot vsako ogrodje. Torej je $n+1 \le n$, kar je protislovje.

**Izrek 4 - Dopolnitev do baze**
Vsaka linearno neodvisna množica v končno-razsežnem vektorskem prostoru je vsebovana v neki bazi.

**Dokaz:** Če je $V$ $n$-razsežen vektorski prostor in so vektorji $v_1, \dots, v_m \in V$ linearno neodvisni, potem je $m \le n$ po Izreku 3. Če je $m = n$, potem so vektorji $v_1, \dots, v_m$ baza po Trditvi 5. Če je $m < n$, potem:
* Izberimo tak $v_{m+1} \in V$, da $v_{m+1} \notin \text{Lin}\{v_1, \dots, v_m\}$.
* Izberimo tak $v_{m+2} \in V$, da $v_{m+2} \notin \text{Lin}\{v_1, \dots, v_m, v_{m+1}\}$.
* Izberimo tak $v_{m+3} \in V$, da $v_{m+3} \notin \text{Lin}\{v_1, \dots, v_m, v_{m+1}, v_{m+2}\}$.
$\dots$
* Izberimo tak $v_n \in V$, da $v_n \notin \text{Lin}\{v_1, \dots, v_m, v_{m+1}, \dots, v_{n-1}\}$.
Obstoj takih $v_{m+1}, \dots, v_n$ sledi iz dejstva, da nobena podmnožica v $n$-razsežnem prostoru, ki ima manj kot $n$ elementov, ni ogrodje (drugi del Izreka 3). Če $n-m$ krat uporabimo Trditev 4, dobimo, da so vektorji $v_1, \dots, v_m, v_{m+1}, \dots, v_n$ linearno neodvisni. Po Trditvi 5 so torej baza.

**Primer iz dopolnjevanja linearno neodvisnih množic**
Zanima nas, kako za dano množico $\{v_1, \dots, v_m\}$ v $F^n$ ugotovimo ali je linearno neodvisna in kako jo dopolnimo do baze. Tvorimo matriko
$A = [v_1 \dots v_m \quad e_1 \dots e_n]$
kjer je $e_1, \dots, e_n$ standardna baza za $F^n$. Z Gaussovo metodo prevedemo matriko $A$ na reducirano vrstično stopničasto formo $R$.
Zaporedne številke pivotnih stolpcev matrike $R$ naj bodo $i_1, \dots, i_n$. Vektorji $v_1, \dots, v_m$ so linearno neodvisni natanko tedaj, ko velja $i_1 = 1$ in $\dots$ in $i_m = m$. Stolpci v $A$ z zaporednimi številkami $i_{m+1}, \dots, i_n$ so potem dopolnitev množice $\{v_1, \dots, v_m\}$ do baze.

**Primer**
Dopolni vektorja $\begin{pmatrix} 1 \\ -1 \\ 0 \\ 2 \end{pmatrix}$ in $\begin{pmatrix} 2 \\ 2 \\ 0 \\ 1 \end{pmatrix}$ do baze za $\mathbb{R}^4$.
Najprej tvorimo matriko
$A = \begin{pmatrix} 1 & 2 & 1 & 0 & 0 & 0 \\ -1 & 2 & 0 & 1 & 0 & 0 \\ 0 & 0 & 0 & 0 & 1 & 0 \\ 2 & 1 & 0 & 0 & 0 & 1 \end{pmatrix}$.
Njena reducirana vrstična stopničasta forma je
$R = \begin{pmatrix} 1 & 0 & 0 & -\frac{1}{5} & 0 & \frac{2}{5} \\ 0 & 1 & 0 & \frac{2}{5} & 0 & -\frac{1}{5} \\ 0 & 0 & 1 & -\frac{3}{5} & 0 & \frac{4}{5} \\ 0 & 0 & 0 & 0 & 1 & -1 \end{pmatrix}$.
Njeni pivotni stolpci imajo zaporedne številke $1, 2, 3$ in $5$. Torej sta $\begin{pmatrix} 1 \\ -1 \\ 0 \\ 2 \end{pmatrix}$ in $\begin{pmatrix} 2 \\ 2 \\ 0 \\ 1 \end{pmatrix}$ linearno neodvisna in $\begin{pmatrix} 1 \\ 0 \\ 0 \\ 0 \end{pmatrix}, \begin{pmatrix} 0 \\ 0 \\ 1 \\ 0 \end{pmatrix}$ ju dopolnita do baze.


#### Primeri baz

V nadaljevanju bomo potrebovali, da se vse karakterizacije obrnljivih matrik nad poljem $\mathbb{R}$ posplošijo na vsako polje $F$.

**Primer - Baze v $F^n$**
Stolpčni vektorji $v_1, \dots, v_n \in F^n$ so baza natanko tedaj, ko je
$\det [v_1 \dots v_n] \ne 0$.
To sledi iz karakterizacij obrnljivih matrik. Posebna primera sta:
* Standardna baza $e_1 = \begin{pmatrix} 1 \\ 0 \\ \vdots \\ 0 \end{pmatrix}, e_2 = \begin{pmatrix} 0 \\ 1 \\ \vdots \\ 0 \end{pmatrix}, \dots, e_n = \begin{pmatrix} 0 \\ 0 \\ \vdots \\ 1 \end{pmatrix}$.
* Vektorji $\begin{pmatrix} 1 \\ 0 \\ 0 \\ 0 \end{pmatrix}, \begin{pmatrix} 1 \\ 1 \\ 0 \\ 0 \end{pmatrix}, \begin{pmatrix} 1 \\ 1 \\ 1 \\ 0 \end{pmatrix}, \begin{pmatrix} 1 \\ 1 \\ 1 \\ 1 \end{pmatrix}$ so baza za $F^n$.

**Opomba:** Standardna baza v $M_{m,n}(F)$ so koordinatne matrike $E_{i,j}$. Matrika $E_{i,j}$ ima na $(i,j)$-tem mestu enko, drugod pa same ničle.

#### Povzetek - Karakterizacije baz in razsežnosti

Povzemimo vse karakterizacije baz v en izrek.

**Povzetek 1**
Za vsako podmnožico $S$ v $n$-razsežnem prostoru $V$ so ekvivalentne trditve:
* $S$ je baza.
* $S$ je linearno neodvisna in je ogrodje.
* $S$ je linearno neodvisna in ima $n$ elementov.
* $S$ je ogrodje in ima $n$ elementov.
* $S$ je linearno neodvisna in nima nobene prave linearno neodvisne nadmnožice.
* $S$ je ogrodje in nima nobene prave podmnožice, ki bi bila ogrodje.

Povzemimo še vse karakterizacije razsežnosti v en izrek.

**Povzetek 2**
Za vsak vektorski prostor $V$ so ekvivalentne naslednje trditve:
* $V$ je $n$-razsežen.
* $V$ ima ogrodje z $n$ elementi, nima pa ogrodja z $n-1$ elementi.
* $V$ ima bazo z $n$ elementi.
* $V$ ima linearno neodvisno množico z $n$ elementi, nima pa linearno neodvisne množice z $n+1$ elementi.


#### Prehod na novo bazo

> **Intuicija:**
> Če je vektor v standardni bazi imamo $ae_{1}+ be_{2}$. Torej je skalarno množenje koeficientov vektorja z baznimi vektorji.
> Če imamo vektor v bazi $X$ potem imamo $ax_{1}+ax_{2}$, sedaj razlikujemo med tem ali je $x_{1},x_{2}$ predstavljen v standardni bazi ali ne. Če ni potem imamo $(1,0), (0,1)$ vektorja in to nam nič ne pomaga. Zato moramo bazo imeti vedno podani v standardni bazi. Recimo $(1,0), (1,1)$. Sedaj nam množenje poda vektor zapisan v standardni bazi. To pomeni da je matrika z baznimi vektorji druge baze vedno prehodna matrika iz baze $X$ v bazo $S$.
> Velja torej da če imamo nek vektor podan v $X$ bazi, ga pretvorimo v $S$ tako da ga le pomnožmo z baznimi vektorji $X$.
> Če je podan v $S$ pa moramo ugotoviti katera linearna kombinacija baznih vektorjev $X$ bo enaka vektorju $S$ kjer bo potem vektor podan v bazi $X$ sestavljen iz dobljenih koeficientov.
> 
> Nazadnje še pogledamo kako deluje prehodna matrika.
> Ker imamo nek vektor $(x_{1},..,x_{n})$ ki ga hočemo izraziti v $Y$ potem moramo storiti naslednje.
> Naprej velja $X \cdot (x_{1},...,x_n)$, kjer je baza $X$ izražena v standardni bazi (drugače nam ne pomaga). Ker hočemo dobiti bazo $Y$ lahko bazne vektorje $X$ izrazimo z bazo $Y$. To pomeni da je vsak bazni vektor $X$ tudi enak neki linearni kombinaciji vektorjev baze $Y$. To pomeni da lahko naredimo matrično množenje $Y(y^1_{1},...,y^1_{n})$ kot prvi bazni vektor izražen v $Y$. Iz tega dobimo matriko z i-tim stolpcem $y^i_{1},...,y^i_{n}$. Če dobljeno matriko pomnožimo z originalnim vektorjem bomo dobili vektor v novi bazi.

Naj bo $V$ $n$-razsežen vektorski prostor in naj bosta $\mathcal{B} = \{u_1, \dots, u_n\}$ ter $\mathcal{C} = \{w_1, \dots, w_n\}$ dve bazi za $V$. ($\mathcal{B}$ je stara baza, $\mathcal{C}$ pa nova baza.)
Vsak vektor $v \in V$ lahko enolično razvijemo tako po bazi $\mathcal{B}$ kot po bazi $\mathcal{C}$:
$v = \beta_1 u_1 + \dots + \beta_n u_n$ (1)
$v = \gamma_1 w_1 + \dots + \gamma_n w_n$ (2)
V tem primeru pišemo
$[v]_\mathcal{B} = \begin{pmatrix} \beta_1 \\ \vdots \\ \beta_n \end{pmatrix}$ in $[v]_\mathcal{C} = \begin{pmatrix} \gamma_1 \\ \vdots \\ \gamma_n \end{pmatrix}$ (3)
Konstruirali bomo tako matriko $P_{\mathcal{C} \leftarrow \mathcal{B}}$, da bo za vsak $v \in V$ veljalo
$[v]_\mathcal{C} = P_{\mathcal{C} \leftarrow \mathcal{B}} [v]_\mathcal{B}$ (4)
Taki matriki bomo rekli **prehodna matrika** iz baze $\mathcal{B}$ na bazo $\mathcal{C}$.

Vsak element baze $\mathcal{B}$ lahko razvijemo po bazi $\mathcal{C}$. Dobimo
$u_1 = \alpha_{1,1} w_1 + \dots + \alpha_{1,n} w_n$
$\vdots$
$u_n = \alpha_{n,1} w_1 + \dots + \alpha_{n,n} w_n$ (5)
Skalarje $\alpha_{i,j}$ potem zložimo v matriko
$P_{\mathcal{C} \leftarrow \mathcal{B}} = \begin{pmatrix} \alpha_{1,1} & \dots & \alpha_{n,1} \\ \vdots & \ddots & \vdots \\ \alpha_{1,n} & \dots & \alpha_{n,n} \end{pmatrix}$ (6)
**Pozor**, skalarje iz $i$-tega razvoja smo zložili v $i$-ti stolpec (in ne v $i$-to vrstico kot bi pričakovali). Na kratko definicijo $P_{\mathcal{C} \leftarrow \mathcal{B}}$ zapišemo kot
$P_{\mathcal{C} \leftarrow \mathcal{B}} = [[u_1]_\mathcal{C} \dots [u_n]_\mathcal{C}]$ (7)

Dokažimo sedaj formulo (4). Če formule (5) vstavimo v formulo (1) in uredimo, dobimo razvoj
$v = \beta_1 u_1 + \dots + \beta_n u_n$
$= \beta_1(\alpha_{1,1}w_1 + \dots + \alpha_{1,n}w_n) + \dots + \beta_n(\alpha_{n,1}w_1 + \dots + \alpha_{n,n}w_n)$
$= (\beta_1 \alpha_{1,1} + \dots + \beta_n \alpha_{n,1})w_1 + \dots + (\beta_1 \alpha_{1,n} + \dots + \beta_n \alpha_{n,n})w_n$ (8)
Če primerjamo koeficiente v razvojih (2) in (8), dobimo
$\gamma_1 = \beta_1 \alpha_{1,1} + \dots + \beta_n \alpha_{n,1}$
$\vdots$
$\gamma_n = \beta_1 \alpha_{1,n} + \dots + \beta_n \alpha_{n,n}$ (9)
V matričnem zapisu se (9) glasi
$\begin{pmatrix} \gamma_1 \\ \vdots \\ \gamma_n \end{pmatrix} = \begin{pmatrix} \alpha_{1,1} & \dots & \alpha_{n,1} \\ \vdots & \ddots & \vdots \\ \alpha_{1,n} & \dots & \alpha_{n,n} \end{pmatrix} \begin{pmatrix} \beta_1 \\ \vdots \\ \beta_n \end{pmatrix}$ (10)
Če v formuli (10) upoštevamo definiciji (3) in (6) dobimo formulo (4).


#### Lastnosti prehodnih matrik

Doslej smo dokazali naslednjo lastnost prehodnih matrik.

**Izrek 1 (Osnovna formula za prehodne matrike)**
Naj bosta $\mathcal{B}$ in $\mathcal{C}$ dve bazi končno-razsežnega vektorskega prostora $V$. Potem za vsak vektor $v \in V$ velja $[v]_\mathcal{C} = P_{\mathcal{C} \leftarrow \mathcal{B}}[v]_\mathcal{B}$.

Oglejmo si nekaj posledic izreka 1.

**Izrek 2 (Produkt prehodnih matrik)**
Naj bodo $\mathcal{B}$, $\mathcal{C}$ in $\mathcal{D}$ tri baze končno-razsežnega vektorskega prostora $V$. Potem velja $P_{\mathcal{D} \leftarrow \mathcal{B}} = P_{\mathcal{D} \leftarrow \mathcal{C}} P_{\mathcal{C} \leftarrow \mathcal{B}}$.
**Dokaz:** Naj bo $\mathcal{B} = \{u_1, \dots, u_n\}$. Upoštevajmo formulo (7) in Izrek 1.
$P_{\mathcal{D} \leftarrow \mathcal{C}} P_{\mathcal{C} \leftarrow \mathcal{B}} = P_{\mathcal{D} \leftarrow \mathcal{C}} [[u_1]_\mathcal{C} \dots [u_n]_\mathcal{C}]$
$= [ P_{\mathcal{D} \leftarrow \mathcal{C}} [u_1]_\mathcal{C} \dots P_{\mathcal{D} \leftarrow \mathcal{C}} [u_n]_\mathcal{C} ]$
$= [ [u_1]_\mathcal{D} \dots [u_n]_\mathcal{D} ]$
$= P_{\mathcal{D} \leftarrow \mathcal{B}}$.

**Izrek 3 (Inverz prehodne matrike)**
Naj bosta $\mathcal{B}$ in $\mathcal{C}$ dve bazi končno-razsežnega vektorskega prostora. Potem velja $(P_{\mathcal{C} \leftarrow \mathcal{B}})^{-1} = P_{\mathcal{B} \leftarrow \mathcal{C}}$.
**Dokaz:** Če uporabimo Izrek 2 z $\mathcal{D} = \mathcal{B}$, dobimo $P_{\mathcal{B} \leftarrow \mathcal{C}} P_{\mathcal{C} \leftarrow \mathcal{B}} = P_{\mathcal{B} \leftarrow \mathcal{B}}$. Po definiciji prehodne matrike je $P_{\mathcal{B} \leftarrow \mathcal{B}}$ identična matrika. Odtod sledi, da je $P_{\mathcal{C} \leftarrow \mathcal{B}}$ obrnljiva matrika in da velja
$(P_{\mathcal{C} \leftarrow \mathcal{B}})^{-1} = P_{\mathcal{B} \leftarrow \mathcal{C}}$.

**Posledica**
Naj bosta $\mathcal{B} = \{u_1, \dots, u_n\}$ in $\mathcal{C} = \{w_1, \dots, w_n\}$ bazi vektorskega prostora $F^n$. Potem velja $P_{\mathcal{C} \leftarrow \mathcal{B}} = [w_1 \dots w_n]^{-1} [u_1 \dots u_n]$.
**Dokaz:** Naj bo $\mathcal{S}$ standardna baza $F^n$. Potem je $[v]_\mathcal{S} = v$ za vsak $v \in F^n$. Iz formule (7) sledi $P_{\mathcal{S} \leftarrow \mathcal{B}} = [[u_1]_\mathcal{S} \dots [u_n]_\mathcal{S}] = [u_1 \dots u_n]$. Podobno dokažemo $P_{\mathcal{S} \leftarrow \mathcal{C}} = [w_1 \dots w_n]$. Po izrekih 2 in 3 je
$P_{\mathcal{C} \leftarrow \mathcal{B}} = P_{\mathcal{C} \leftarrow \mathcal{S}} P_{\mathcal{S} \leftarrow \mathcal{B}} = (P_{\mathcal{S} \leftarrow \mathcal{C}})^{-1} P_{\mathcal{S} \leftarrow \mathcal{B}} = [w_1 \dots w_n]^{-1} [u_1 \dots u_n]$


#### Razsežnosti podprostorov

Naj bo $V$ končno-razsežen vektorski prostor. Njegovo razsežnost označimo z $\text{dim } V$. Lahko jo definiramo na več ekvivalentnih načinov:
* Kot minimum moči ogrodij za $V$.
* Kot moč katerekoli baze za $V$. (Vse baze imajo enako moč.)
* Kot maksimum moči linearno neodvisnih množic v $V$.
Če $V$ ni končno-razsežen, potem pišemo $\text{dim } V = +\infty$.

**Trditev**
Če je $V$ končno-razsežen vektorski prostor in če je $U$ vektorski podprostor v $V$, potem je tudi $U$ končno-razsežen vektorski prostor in $\text{dim } U \le \text{dim } V$.
**Dokaz:** Naj bo $n = \text{dim } V$. Če $\text{dim } U = +\infty$ ali če $\text{dim } U > n$, potem $U$ nima ogrodja z $\le n$ elementi. Torej obstajajo taki $u_1, u_2, \dots, u_{n+1} \in U$ da $u_1 \notin \text{Lin}\{\}$, $u_2 \notin \text{Lin}\{u_1\}$, $u_3 \notin \text{Lin}\{u_1, u_2\}$, $\dots$, $u_{n+1} \notin \text{Lin}\{u_1, \dots, u_n\}$. Po Trditvi 3 od zadnjič odtod sledi, da so vektorji $u_1, u_2, \dots, u_{n+1}$ linearno neodvisni v $U$ (in zato tudi linearno neodvisni v $V$). Toda vsaka linearno neodvisna množica v $V$ ima največ $n$ elementov. To je protislovje.

**Trditev (Dimenzijska formula za podprostore)**
Če je $V$ končno-razsežen vektorski prostor in če sta $U_1$ in $U_2$ vektorska podprostora v $V$, potem velja naslednja formula
$\text{dim}(U_1 + U_2) = \text{dim } U_1 + \text{dim } U_2 - \text{dim }(U_1 \cap U_2)$.
**Dokaz:** Naj bo $f_1, \dots, f_k$ baza za podprostor $U_1 \cap U_2$. Naj bo $g_1, \dots, g_l$ njena dopolnitev do baze za $U_1$ in naj bo $h_1, \dots, h_m$ njena dopolnitev do baze za $U_2$. Dokazali bomo, da je $f_1, \dots, f_k, g_1, \dots, g_l, h_1, \dots, h_m$ baza za $U_1 + U_2$. Potem je $\text{dim}(U_1 + U_2) = k + l + m$, $\text{dim}(U_1 \cap U_2) = k$, $\text{dim } U_1 = k + l$ in $\text{dim } U_2 = k + m$. Torej formula v trditvi drži.

Pokažimo najprej, da so $f_1, \dots, f_k, g_1, \dots, g_l, h_1, \dots, h_m$ ogrodje za $U_1 + U_2$. Po definiciji vsote dveh podprostorov lahko vsak vektor $u \in U_1 + U_2$ izrazimo kot $u = u_1 + u_2$, kjer $u_1 \in U_1$ in $u_2 \in U_2$. Ker je $f_1, \dots, f_k, g_1, \dots, g_l$ baza za $U_1$, lahko izrazimo $u_1$ kot linearno kombinacijo $f_1, \dots, f_k, g_1, \dots, g_l$. Ker je $f_1, \dots, f_k, h_1, \dots, h_m$ baza za $U_2$, lahko izrazimo $u_2$ kot linearno kombinacijo $f_1, \dots, f_k, h_1, \dots, h_m$. Torej lahko $u$ izrazimo kot linearno kombinacijo $f_1, \dots, f_k, g_1, \dots, g_l, h_1, \dots, h_m$.

Pokažimo še, da so $f_1, \dots, f_k, g_1, \dots, g_l, h_1, \dots, h_m$ linearno neodvisni. Če $\alpha_1 f_1 + \dots + \alpha_k f_k + \beta_1 g_1 + \dots + \beta_l g_l + \gamma_1 h_1 + \dots + \gamma_m h_m = 0$, potem $\alpha_1 f_1 + \dots + \alpha_k f_k + \beta_1 g_1 + \dots + \beta_l g_l = (-\gamma_1) h_1 + \dots + (-\gamma_m) h_m$ leži v $U_1 \cap U_2$ (ker leva stran leži v $U_1$, desna pa v $U_2$.) Torej obstajajo taki skalarji $\delta_1, \dots, \delta_k$, da je $(-\gamma_1) h_1 + \dots + (-\gamma_m) h_m = \delta_1 f_1 + \dots + \delta_k f_k$. Ker je $f_1, \dots, f_k, h_1, \dots, h_m$ baza za $U_2$, odtod sledi $\gamma_1 = \dots = \gamma_m = 0$ (in $\delta_1 = \dots = \delta_k = 0$). Sledi $\alpha_1 f_1 + \dots + \alpha_k f_k + \beta_1 g_1 + \dots + \beta_l g_l = 0$. Ker je $f_1, \dots, f_k, g_1, \dots, g_l$ baza za $U_1$, odtod sledi $\alpha_1 = \dots = \alpha_k = 0$ in $\beta_1 = \dots = \beta_l = 0$. Dokaz linearne neodvisnosti je s tem končan.

**Posledica dimenzijske formule**
Za vsaka podprostora $U_1$ in $U_2$ v $V$ velja $\text{dim}(U_1 + U_2) \le \text{dim } U_1 + \text{dim } U_2$. Enčaj velja natanko tedaj, ko je $U_1 \cap U_2 = \{0\}$.
**Dokaz.** V dimenzijski formuli upoštevamo, da je $\text{dim}(U_1 \cap U_2) \ge 0$ in da velja $\text{dim}(U_1 \cap U_2) = 0$ natanko tedaj, ko je $U_1 \cap U_2 = \{0\}$.
**Opomba:** Dimenzijsko formulo lahko posplošimo tudi na tri podprostore:
$\text{dim}(U_1 + U_2 + U_3) = \text{dim } U_1 + \text{dim } U_2 + \text{dim } U_3 - \text{dim}(U_1 \cap U_2) - \text{dim}(U_1 \cap U_3) - \text{dim}(U_2 \cap U_3) + \text{dim}(U_1 \cap U_2 \cap U_3)$.

#### Direktne vsote podprostorov

Pojme linearne ogrinjače, ogrodja, linearne neodvisnosti in baze lahko posplošimo iz vektorjev na vektorske podprostore. Terminologija ni ista. Posplošitev pojma linearne ogrinjače vektorjev je pojem vsote vektorskih podprostorov.

**Definicija vsote vektorskih podprostorov**
Vsota vektorskih podprostorov $U_1, \dots, U_n$ (nekega vektorskega prostora) je vektorski podprostor
$U_1 + \dots + U_n := \{u_1 + \dots + u_n \mid u_1 \in U_1, \dots, u_n \in U_n\}$.
**Opomba:** Vektorske podprostore $U_1, \dots, U_n$ lahko smatramo za "ogrodje" vektorskega prostora $V$, če lahko vsak vektor $v \in V$ na vsaj en način izrazimo kot $v = u_1 + \dots + u_n$, kjer $u_1 \in U_1, \dots, u_n \in U_n$. To velja natanko tedaj, ko je $V = U_1 + \dots + U_n$.

**Definicija (interne) direktne vsote podprostorov**
Vsota vektorskih podprostorov $U_1, \dots, U_n$ je **direktna**, če za vsake vektorje $v_1, w_1 \in U_1, \dots, v_n, w_n \in U_n$, ki zadoščajo $v_1 + \dots + v_n = w_1 + \dots + w_n$ velja $v_1 = w_1, \dots, v_n = w_n$.
**Opomba:** Vektorske podprostore $U_1, \dots, U_n$ lahko smatramo za "linearno neodvisne", če lahko vsak vektor $v \in V$ na največ en način izrazimo kot $v = u_1 + \dots + u_n$, kjer $u_1 \in U_1, \dots, u_n \in U_n$. To velja natanko tedaj, ko je vsota $U_1 + \dots + U_n$ direktna.
**Opomba:** **Eksterna direktna vsota** podprostorov $U_1, \dots, U_n$ je definirana kot množica vseh $n$-teric $(u_1, \dots, u_n)$, kjer $u_i \in U_i$ za vsak $i=1, \dots, n$. Označimo jo z $U_1 \oplus \dots \oplus U_n$. Naj bo $\Phi$ preslikava iz $U_1 \oplus \dots \oplus U_n$ v $V$, ki pošlje $(u_1, \dots, u_n)$ v $u_1 + \dots + u_n$. Njena zaloga vrednosti je ravno vsota $U_1 + \dots + U_n$. Preslikava $\Phi$ je injektivna natanko tedaj, ko je vsota $U_1 + \dots + U_n$ direktna. Torej lahko preko $\Phi$ identificiramo interno direktno vsoto $U_1 + \dots + U_n$ z eksterno direktno vsoto $U_1 \oplus \dots \oplus U_n$. Zato tudi interno direktno vsoto označimo z $U_1 \oplus \dots \oplus U_n$.

**Osnovni primer**
Za vse vektorje $v_1, \dots, v_n \in V$ velja
$\text{Lin}\{v_1\} + \dots + \text{Lin}\{v_n\} = \text{Lin}\{v_1, \dots, v_n\}$.
Torej so vektorji $v_1, \dots, v_n$ ogrodje za $V$ natanko tedaj, ko velja $\text{Lin}\{v_1\} + \dots + \text{Lin}\{v_n\} = V$ ($\Leftrightarrow \text{Lin}\{v_1\}, \dots, \text{Lin}\{v_n\}$ so "ogrodje").
Neničelni vektorji $v_1, \dots, v_n$ v $V$ so LN natanko tedaj, ko je vsota $\text{Lin}\{v_1\} + \dots + \text{Lin}\{v_n\}$ direktna ($\Leftrightarrow \text{Lin}\{v_1\}, \dots, \text{Lin}\{v_n\}$ so "LN").
**D:** Vsota $\text{Lin}\{v_1\} + \dots + \text{Lin}\{v_n\}$ je direktna natanko tedaj, ko za vsake skalarje $\alpha_i, \beta_j$ velja, da iz $\alpha_1 v_1 + \dots + \alpha_n v_n = \beta_1 v_1 + \dots + \beta_n v_n$ sledi $\alpha_1 v_1 = \beta_1 v_1, \dots, \alpha_n v_n = \beta_n v_n$. Ker so vektorji $v_1, \dots, v_n$ neničelni je to ekvivalentno lastnosti, da iz $\alpha_1 v_1 + \dots + \alpha_n v_n = \beta_1 v_1 + \dots + \beta_n v_n$ sledi $\alpha_1 = \beta_1, \dots, \alpha_n = \beta_n$. To pa je ravno linearna neodvisnost $v_1, \dots, v_n$.
**Opomba:** Vektorske podprostore $U_1, \dots, U_n$ lahko smatramo za "bazo" vektorskega prostora $V$, če lahko vsak vektor $v \in V$ na natanko en način izrazimo kot $v = u_1 + \dots + u_n$, kjer $u_1 \in U_1, \dots, u_n \in U_n$. To velja natanko tedaj, ko je $V = U_1 \oplus \dots \oplus U_n$.

#### Karakterizacije direktnih vsot

Direktno vsoto vektorskih podprostorov bi radi opisali na čimveč različnih načinov. Mnoge od teh opisov bomo potrebovali v naslednjih poglavjih.

**Izrek (Karakterizacije direktnih vsot)**
Za vsako naravno število $n$ in za vsake podprostore $U_1, \dots, U_n$ v vsakem končno-razsežnem vektorskem prostoru $V$ so ekvivalentne lastnosti:
1. Vsota $U_1 + \dots + U_n$ je direktna.
2. Če vektorji $u_1 \in U_1, \dots, u_n \in U_n$ zadoščajo $u_1 + \dots + u_n = 0$ (v $V$), potem velja $u_1 = \dots = u_n = 0$.
3. Če so $u_{1,1}, \dots, u_{1,r_1}$ baza za $U_1$ in $\dots$ in so $u_{n,1}, \dots, u_{n,r_n}$ baza za $U_n$, potem so $u_{1,1}, \dots, u_{1,r_1}, \dots, u_{n,1}, \dots, u_{n,r_n}$ baza za $U_1 + \dots + U_n$.
4. Velja $\text{dim}(U_1 + \dots + U_n) = \text{dim } U_1 + \dots + \text{dim } U_n$.
5. Za vsak $i = 1, \dots, n-1$ velja $(U_1 + \dots + U_i) \cap U_{i+1} = \{0\}$.

**Dokaz:**
* $(1) \Rightarrow (2)$ Recimo da velja (1). Vzemimo take $u_i \in U_i$, da velja $0 = u_1 + \dots + u_n$. Ker velja tudi $0 \in U_i$ za vse $i$ in $0 = 0 + \dots + 0$, sledi po (1), da je $u_1 = 0, \dots, u_n = 0$. Torej velja (2).
* $(2) \Rightarrow (1)$ Recimo, da velja (2). Vzemimo take $u_i, v_i \in U_i$, da velja $u_1 + \dots + u_n = v_1 + \dots + v_n$. Odtod sledi $(u_1 - v_1) + \dots + (u_n - v_n) = 0$ in $u_i - v_i \in U_i$ za vse $i$. Iz (2) sledi $u_i - v_i = 0$ za vse $i$. Torej velja (1).
* $(2) \Rightarrow (3)$ Recimo, da velja (2) in da je za vsak $i$ $u_{i,1}, \dots, u_{i,r_i}$ baza za $U_i$. Vsak vektor $u \in U_1 + \dots + U_n$ lahko izrazimo kot $u = u_1 + \dots + u_n$, kjer $u_i \in U_i$ za vse $i$. Vsak $u_i$ lahko izrazimo kot linearno kombinacijo vektorjev $u_{i,1}, \dots, u_{i,r_i}$, ker so ti ogrodje za $U_i$. Torej lahko $u$ izrazimo kot linearno kombinacijo vektorjev $u_{1,1}, \dots, u_{1,r_1}, \dots, u_{n,1}, \dots, u_{n,r_n}$. Torej so ti vektorji ogrodje za $U_1 + \dots + U_n$. Pokažimo še, da so linearno neodvisni. Recimo, da velja $\alpha_{1,1}u_{1,1} + \dots + \alpha_{1,r_1}u_{1,r_1} + \dots + \alpha_{n,1}u_{n,1} + \dots + \alpha_{n,r_n}u_{n,r_n} = 0$. Za vsak $i$ označimo $u_i := \alpha_{i,1}u_{i,1} + \dots + \alpha_{i,r_i} u_{i,r_i}$. Očitno $u_i \in U_i$ za vsak $i$ in $u_1 + \dots + u_n = 0$. Po točki (2) odtod sledi, da je $u_i = 0$ za vse $i$. Ker so $u_{i,1}, \dots, u_{i,r_i}$ linearno neodvisni, res velja $\alpha_{i,1} = \dots = \alpha_{i,r_i} = 0$ za vse $i$.
* $(3) \Rightarrow (4)$ Upoštevamo, da je razsežnost enaka moči baze.
* $(4) \Rightarrow (5)$ Če $n$-krat uporabimo posledico dimenzijske formule, dobimo
$\text{dim}(U_1 + \dots + U_n) \le \text{dim}(U_1 + \dots + U_{n-1}) + \text{dim } U_n \le$
$\le (\text{dim}(U_1 + \dots + U_{n-2}) + \text{dim } U_{n-1}) + \text{dim } U_n \le \dots \le \text{dim } U_1 + \dots + \text{dim } U_n$.
Če velja (4), potem se začetek in konec ujemata, torej imamo povsod enčaj. Odtod sledi, da za vsak $i = 1, \dots, n-1$ velja
$\text{dim}((U_1 + \dots + U_i) + U_{i+1}) = \text{dim}(U_1 + \dots + U_i) + \text{dim } U_{i+1}$.
Če za vsak $i$ uporabimo posledico dimenzijske formule, dobimo (5).
* $(5) \Rightarrow (2)$ Recimo, da velja (5). Vzemimo take vektorje $u_1 \in U_1, \dots, u_n \in U_n$, da velja $u_1 + \dots + u_n = 0$. Odtod sledi, da vektor $u_1 + \dots + u_{n-1} = -u_n$ pripada podprostoru $(U_1 + \dots + U_{n-1}) \cap U_n$, ki je po predpostavki enak $\{0\}$. Torej je $u_1 + \dots + u_{n-1} = 0$ in $u_n = 0$. Odtod sledi, da vektor $u_1 + \dots + u_{n-2} = -u_{n-1}$ pripada podprostoru $(U_1 + \dots + U_{n-2}) \cap U_{n-1}$, ki je po predpostavki enak $\{0\}$. Torej je $u_1 + \dots + u_{n-2} = 0$ in $u_{n-1} = 0$. Po nekaj korakih dobimo, da so vsi $u_i$ enaki nič. Torej velja (2).
