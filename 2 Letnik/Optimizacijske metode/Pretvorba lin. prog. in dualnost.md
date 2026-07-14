**Pretvorbe lin. progr.**

Pretvorba linearnega programa v standardno obliko:

$$\min c^T x \Rightarrow \max -c^T x \quad $$
$$ $$
$$a^T x \geq b \Rightarrow -a^T x \leq -b$$
$$ $$
$$a^T x = b \Rightarrow a^T x \leq b, \quad a^T x \geq b$$
$$ $$
$$x_i \leq 0 \Rightarrow (-x_i) \geq 0$$
$$ $$
$$x_i \text{ ni omejen} \Rightarrow x_i = x_i^+ - x_i^-, \quad x_i^+, x_i^- \geq 0$$

*Če imamo več prostih spremenljivk se izkaže da lahko $n$ prostih spremenljivk izrazimo z $n+1$ novih tako da rečemo $x = x^{+} - a^{-}$, $y = y^{+} - a^{-},...$*

Kompleksnejše pretvorbe

$$\min (\max \{f_1(x),...,f_n(x)\}) $$ $$\Rightarrow \min t, t \geq f_{1}(x),...,t\geq f_n (x)$$

$$ $$

$$\max (\min \{f_1(x),...,f_n(x)\}) $$ $$\Rightarrow \max t, t \leq f_{1}(x),...,t\leq f_n (x)$$

$$ $$

$$\min |f(x)| = \min (\max \{f(x), -f(x)\}) $$ $$\Rightarrow \min t, t \geq f(x), t \geq -f(x)$$

Pretvorba minimuma vsote maximumov

$$ \min \sum_{j=1}^{k}\max_{i \in I_{j}}\{f_{ij}(x)\}$$

Za vsak $j$-ti maksimum moramo uvesti novo spremenljivko.

$$\min \sum_{j=1}^{k} z_{j}$$

Za vsako $z_j$ pa mora veljati da je $z_j \geq f_{ij}(x)$ za vse $i$-je.





***

**Dualnost**

Za nek linear program bi našli zgornjo mejo.

Mi lahko neenakosti v našem linearnem programu pomnožimo z nenegativnimi spremenljivkami in jih seštejemo da dobimo novo neenakost.

$$\begin{array}
\\
\max &c^{T}x \\
\text{p.p.} &Ax \leq b \\ 
&x \geq 0
\end{array}$$

$$\begin{array}
\\
\max &3x_{1} + +5x_{2}+4x_{3} \\
\text{p.p.} & x_{1}+x_{2}+x_{3}\leq 50\\ 
& 3x_{1}+4x_{2}+5x_{3}\leq 250\\
& 10x_{1}+15x_{2}+12x_{3}\leq 600\\
& x_{1,2,3} \geq 0
\end{array}$$

$$\text{ }\;\;\;\;\;\;\Downarrow$$

$$ \begin{array}\\
y_1(x_1 + x_2 + x_3)  \leq 50y_1 \\
y_2(3x_1 + 4x_2 + 5x_3)  \leq 250y_2 \\
y_3(10x_1 + 15x_2 + 12x_3)  \leq 600y_3
\end{array}$$

$$\text{ }\;\;\;\;\;\;\Downarrow$$

$$y_1(x_{1} + x_{2} + x_{3}) + y_2(3x_{1} + 4x_{2} + 5x_{3}) + y_3(10x_{1} + 15x_{2} + 12x_{3}) $$ $$\leq 50y_1 + 250y_2 + 600y_3$$

oz. vidimo da je to zapisano z matrikami

$$\quad \quad\; x^{T}A^{T}y \leq b^{T}y\quad (1)$$

$$\sum_{j=1}^{n}a_{ij}x_{i} \leq b_{i}$$
$$\sum_{i=1}^{m}\sum_{j=1}^{n}a_{ij}x_{i}y_{j} \leq \sum_{i=1}^{m} b_{i}y_{i}$$


ampak $b^{T}y$ je zgornja meja šele če velja da je kriterijska funkcija manjša od $x^{T}A^{T}y$. **Iz tega množenja sledi da mora biti $y \geq 0$** saj bi se drugače neenačaju spremenil znak. *Iz tega tudi sledi da če imamo v pogojih enakost potem je $y_{i}$ pri tej enakosti prosta, saj enakost ni odvisna od predznaka števila s katerim množimo obe strani.*

To pomeni da mora za vsak $c_{i}$ pred vsakim $x_{i}$ iz krit. funkcije veljati

$$c_{i} \leq a_{i}^{T}y $$

kjer je $a_{i}^{T}$ $i$-ta vrstica v $A^{T}$.



**oz. da je**

$${\color{green}A^{T}y \geq c}$$

mi pa hočemo da je naša zgornja meja **$b^{T}y$ čim manjša** oz. jo minimiziramo. S tem pridemo do LP oblike

$$\begin{array}
\\
\min & b^{T}y \\
\text{p.p.} &A^{T}y \geq c \\ 
& y \geq 0
\end{array}$$


> Velja da je dual duala LP spet isti LP oz.
> $$P'' = P$$
> >[!|dokaz]+ Dokaz:
> >Začnemo z dualom $P'$
> >
> > $$
> > \begin{aligned}
> > \min \quad & \sum_{i=1}^{m} b_i y_i \\
> > \text{p.p.} \quad & \sum_{i=1}^{m} a_{ij} y_i \ge c_j,\; \forall j \\
> > & y_i \ge 0
> > \end{aligned}
> > $$
> > 
> > Če damo v standardno obliko dobimo
> > 
> > $$
> > \begin{aligned}
> > \max \;\; & -\sum_{i=1}^{m} b_i y_i \\
> > \text{p.p.} \; & -\sum_{i=1}^{m} a_{ij} y_i \le -c_j
> > \end{aligned}
> > $$
> > 
> > 
> > 
> > Dualni problem
> > $$
> > \begin{aligned}
> > \min \quad & \sum_{j=1}^{n} -c_j x_j \\
> > \text{p.p.} \quad & -\sum_{j=1}^{n} a_{ij} x_j \ge -b_i \\
> > \end{aligned}$$ 
> > 
> > $$\begin{aligned}
> > \max \;& \sum_{j=1}^{n}c_{j}x_{j} \\
> > \text{p.p. } & \sum_{j=1}^{n} a_{ij} x_j \le b_i \\
> > & x_j \ge 0
> > \end{aligned}
> > $$


> Šibki izrek o dualnosti
> 
> Predpostavimo da je 
> - **$x$ dopustna rešitev za $P$** 
> - **$y$ dopustna rešitev za $P'$** 
> 
> Potem velja $c^{T}x \leq b^{T}y$
> >[!|dokaz]+ Dokaz:
> > $$c^{T}x \leq (A^{T}y)^{T}x = y^{T}Ax \leq y^{T}b$$
> > 
> > $$ $$
> > 
> > Oz. podrobneje
> > 
> > $$
> > \text{ dopustnost } x \Rightarrow b_i \ge \sum_{j=1}^n x_j a_{ij}   $$
> > $$\Rightarrow \sum_{j=1}^{n} \sum_{i=1}^{m} a_{ij} x_{j} y_{i} \le \sum_{i=1}^m b_i y_i $$
> > 
> > $$ $$
> > 
> > $$\text{ dopustnost } y \Rightarrow c_j \le \sum_{i=1}^m a_{ij} y_i  $$ $$\Rightarrow \sum_{j=1}^n x_j c_j  \le \sum_{j=1}^n \sum_{i=1}^m a_{ij} x_j y_i$$
> > 
> > $$ $$
> > 
> > $$
> > \Rightarrow \sum_{j=1}^n c_j x_j  \le \sum_{i=1}^m b_i y_i
> > $$

Iz tega sledita dve posledici

> Predpostavimo 
> - $x$ je dopusten
> - $y$ je dopusten 
>  - $c^{T}x = b^{T}y$
> 
> $\Rightarrow$ Iz tega sledi da je $x$ optimalna rešitev. 
> *Dosežena je szgornja meja in v resnici dosežena tudi spodnja meja za dual torej je tudi $y$ optimalna rešitev.*
> *Preverjanje ali je rešitev optimalna sedaj zahteva le iskanje dopustne rešitve $y$ da velja $c^{T}x = b^{T}y$.*
> >[!|dokaz]+ Dokaz:
>> Iz šibkega izreka vemo da če imamo dve dopustni rešitvi velja da je $c^{T}x\leq b^{T}y$. Če sedaj velja $c^{T}x = b^{T}y$ potem za vsako dopustno rešitev $x'$ velja $c^{T}x \geq c^{T}x'$ torej je $c^{T}x$ optimalna vrednost.

> $P$ je neomejen $\Rightarrow$ $P'$ je nedopusten
> >[!|dokaz]- Dokaz:
> > Ker je $P$ neomejen ni zgornje meje za $P$ kar pomeni da če bi obstajala dopustna rešitev za $P'$ bi nam to dalo neko zgornjo mejo kar je protislovje. Torej $P'$ ne more imeti dopustne rešitve.

<br>

>**Krepki izrek o dualnosti**
>
>Predpostavmo 
>- $x^{*}$ je optimalna rešitev za $P$
>
>$\Rightarrow$ 
> - $P'$ ima optimalno rešitev $y^{*}$ 
> - $c^{T}x^{*} = b^{T}y^{*}$.
> - *Koeficienti pred dopolnilnimi spremenljivkami v zadnjem slovarju so nasprotne vrednosti optimalne rešitve prvotnega problema.*
>
>>[!|dokaz]+ Dokaz:
>>*V zadnjem slovarju so koeficienti pred dopolnilnimi spremenljivkami v kriterijski funkciji dualnega problema ravno nasprotne vrednosti optimalne rešitve prvotnega problema in obratno.*
>>
>>Predpostavimo da je $x^{*}$ optimalna in da velja $y^{*}_{i} = -c_{i+n}^{*}$. Preverjamo če iz tega sledi da je taka $y^{*}$ res optimalna rešitev.
>>
>>Uporabimo simpleksno metodo na $P$ in si pogledamo zadnji slovar
>>
>>$$z = v^{*} + \sum_{1}^{n+m}c^{*}_{i}x_{i}$$
>>
>>Ker smo v zadnjem slovarju vemo da so $c^{*}\leq 0$. 
>>
>>$$v^{*} + \sum_{j=1}^{n}c_{j}^{*}x_{j} + \sum_{i=1}^{m}c_{i+n}^{*}x_{i+n}$$
>>
>> Po predpostavki preverjamo ali so $c^{*}_{i+n}$ rešitve dualnega problema torej velja
>>
>>$$y^{*}_{i} = -c^{*}_{i+n}$$
>>
>>Sedaj bomo dokazali da so $y_{1}^{*},...,y_{m}^{*}$ dopustna rešitev in da je $\sum_{j=1}^{n}c_{j}x_{j}^{*} = \sum_{i=1}^{m}b_{i}y_{i}^{*}$.
>>*Pazimo na to da so $c_{j}$ koeficienti v kriterijski funckij medtem ko so $c_{i}^{\star}$  konstante optimalne rešitve.*
>>Dopolnilne spremenljivke $x_{i+n}$ so izražene v prvotnem slovarju kot $x' = b-Ax$ oz. je $x_{n+i} = b_{i}-\sum_{j=1}^{n}a_{ij}x_{j}$
>>
>>$$z = v^{*} + \sum_{j=1}^{n}c_{j}^{*}x_{j}+ \sum_{i=1}^{m}(-y_{i}^{*})\left(b_{i}-\sum_{j=1}^{n}a_{ij}x_{j}\right)$$
>>
>>Razdelimo vsote tako da se znebimo spremenljivk *Ne pozabimo da so spremenljivke samo $x_{i}$, druge spremenljivke $y^{\star}, c^{\star},...$ so dejanske vrednosti.*
>>
>>$$z=\left(v^{*}- \sum_{i=1}^{m}b_{i}y_{i}^{*}\right) + \sum_{j=1}^{n}c_{j}^{*}x_{j}+\left(\sum_{j=1}^{n}\left(\sum_{i=1}^{m}a_{ij}y_{i}^{*}\right)x_{j}\right)$$
>>$$z=\left(v^{*}- \sum_{i=1}^{m}b_{i}y_{i}^{*}\right) +  \left(\sum_{j=1}^{n}\left(\sum_{i=1}^{m}a_{ij}y_{i}^{*}\right)x_{j} + c_{j}^{*}x_{j}\right)$$
>>$$z=\left(v^{*}- \sum_{i=1}^{m}b_{i}y_{i}^{*}\right) +  \sum_{j=1}^{n}x_{j}\left(\sum_{i=1}^{m}a_{ij}y_{i}^{*} + c_{j}^{*}\right)$$
>>
>>Sedaj smo na točki kjer je kriterijska funkcija izražena s prvotnimi spremenljivkami. Mi imamo $z = \sum_{j=1}^{n}c_{j}x_{j}$ kot osnovno definicijo. Vidimo da je konstanta pri prvotni krit. funkciji enaka 0. Za ostale koeficiente pa mora veljati da so enaki $c_{i}$.
>>
>>$$z=z$$
>>$$ {\color{green}0}+{\color{orange}\sum_{j=1}^{n}c_{j}x_{j}}={\color{green}\left(v^{*}- \sum_{i=1}^{m}b_{i}y_{i}^{*}\right)} +  {\color{orange}\sum_{j=1}^{n}x_{j}\left(\sum_{i=1}^{m}a_{ij}y_{i}^{*} + c_{j}^{*}\right)}$$
>>$${\color{green}0 = v^{*}- \sum_{i=1}^{m}b_{i}y_{i}^{*}}$$
>>$${\color{green}v^{*} = \sum_{i=1}^{m}b_{i}y_{i}^{*}}$$
>>
>>Po definiciji optimalne vrednosti $v^{*}$ velja
>>
>>$$\Rightarrow {\color{green}v^{*} = \sum_{i=1}^{m}b_{i}y_{i}^{*} = \sum_{j=1}^{ n}c_{j}x_{j}^{*}}$$
>>$$ $$
>>$${\color{orange}c_{j} = \sum_{i=1}^{m}a_{ij}y_{i}^{*}+c_{j}^{*}}$$
>>$${\color{orange}\sum_{i=1}^{m}a_{ij}y_{i}^{*} = c_{j}-c_{j}^{*}}$$
>>Ampak velja $c_{j}^{*}\leq 0$ $\Rightarrow c_{j}-c_{j}^{*} \geq c_{j}$
>>
>>$${\color{orange}\sum_{i=1}^{m}a_{ij}y_{i}^{*} = c_{j}-c_{j}^{*} \geq c_{j}}$$
>>
>>In vemo da je $y_{i}^{*} = -c_{i+n}^{*} \geq 0$ *ker morajo te $c$-ji ker so v zandnjem slovarju biti $\leq 0$.*
>>
>>$${\color{orange}y_{i}^{*}=-c_{i+n}^{*}\geq 0}$$
>>To sta točno pogoja iz dualnega problema in nam pove da je $y^{*}$ dopustna rešitev. 
>>
>>Iz zelenega pa vidimo da je $y_{i}^{*}$ optimalna rešitev po šibkem izreku o dualnosti saj je $x^{*}$ dopustna, $y^{*}$ je dopustna in velja enakost torej morata biti obe optimalni.

<br>

> Za $P$ in $P'$ velja da sta 
> 1. Oba optimalna
> 2. Oba nedopustna
> 3. En neomejen in drugi nedopusten

<br>

>Izrek o dualnem dopolnjevanju ( DD )
>
>Predpostavimo 
> - $x$ je dopustna za $P$
> - $y$ je dopustna za $P'$
>
>$\Rightarrow$
>
>$x$ je opt. za $P$ $\Leftrightarrow$
>$\forall i=1,...,m : \sum_{j=1}^{n}a_{ij}x_{j}= b_{i}$ ali $y_{i}=0$ in
>$\forall j = 1,...,n : x_{j}=0$ ali $\sum_{j=1}^{m}a_{ij}y_{i}=c_{j}$
>oz. ekvivalentno
>$\sum_{j=1}^{n}a_{ij}x_{j}< b_{i} \Rightarrow y_{i}=0$
>$x_{j}>0 \Rightarrow \sum_{i=1}^{m}a_{ij}y_{i}=c_{j}$
>
>>[!|dokaz]+ Dokaz:
> > Po izreku o šibki dualnosti sta dopustni rešitvi $x$ in $y$ optimalni natanko tedaj, ko velja $\sum_{j=1}^{n}c_{j}x_{j} = \sum_{i=1}^{n}b_{i}y_{i}$. Iz dopustnosti $Ax \le b, x \ge 0$ in $A^{T}y \ge c, y \ge 0$ sledi veriga neenakosti:
> > $$\sum_{j = 1}^{n}c_{j}x_{j} \leq \sum_{1}^{n}\sum_{1}^{m}a_{ij}x_{j}y_{i} \leq \sum_{1}^{m}y_{i}b_{i}$$ 
> > Da velja enakost $c^T x = y^T b$, morata biti obe neenakosti v verigi v resnici enakosti:
> > 1. $(y^T A - c^T) x = 0$
> > 2. $y^T (b - Ax) = 0$
> > 
> > V skalarni obliki to zapišemo kot:
> > $$\sum_{j=1}^{n} \left( \sum_{i=1}^{m} a_{ij} y_i - c_j \right) x_j = 0$$
> > $$\sum_{i=1}^{m} y_i \left( b_i - \sum_{j=1}^{n} a_{ij} x_j \right) = 0$$
> > Ker so zaradi dopustnosti vsi faktorji v oklepajih in vsi $x_j, y_i$ nenegativni, je vsota nič natanko tedaj, ko je vsak posamezen produkt enak nič. Od tod sledi:
> > $\left( \sum_{i=1}^{m} a_{ij} y_i - c_j \right) x_j = 0$ za vsak $j$, kar pomeni $x_j > 0 \Rightarrow \sum_{i=1}^{m} a_{ij} y_i = c_j$.
> > $y_i \left( b_i - \sum_{j=1}^{n} a_{ij} x_j \right) = 0$ za vsak $i$, kar pomeni $\sum_{j=1}^{n} a_{ij} x_j < b_i \Rightarrow y_i = 0$.


**Ekonomski pomen dualnih spremenljivk**

Predpostavimo da imamo optimalno rešitev $x^{*}$. Glede na pogoje se lahko zgodita naslednji situaciji.

**Prva možnost**

Vse neenakosti so zadoščene tako da ni dosežena meja oz. da velja stroga neenakost.

To pomeni da smo dosegli optimalno rešitev brez da bi dosegli mejo oz. brez da bi rabili porabiti vse "vire", ki so nam na voljo.

V tem primeru če povečamo katerokoli od vrednosti na desni strani neenačb nam ne bi prineslo boljše optimalne vrednosti.

**Druga možnost**

Če pri eni ali več neenakosti dosežemo mejo pa lahko sklepamo da bi potencialno ob povečanju meje lahko dosegli še boljšo optimalno vrednost.

Torej če se pri neki neenakosti zgodi da smo mejo dosegli. Potem je mogoče da pridemo do bolj optimalne rešitve če bi imeli na voljo več "virov".

**Izkaže se da nam optimalna rešitev dualnega problema da koeficiente ki nam povejo za koliko se poveča naša optimalna rešitev primalnega problema, če povečamo mejo pri pripadajoči neenakosti.**

> Naj bo $P$ nek lin. program in naj ima v zadnjem slovarju **neizrojeno bazno optimalno** rešitev kjer so vse konstante v zadnjem slovarju pozitivne - $K > 0$.
> Potem obstaja $\varepsilon > 0$, da velja $\Delta z^{*}$ - sprememba optimalne vrednosti - $\Delta z^{*} = \sum_{i = 1}^{m}y_{i}^{*} \Delta b_{i}$ za $| \Delta b_{i}| \leq \varepsilon$.
> 
> *Torej če se desne strani spremenijo za manj kot $\varepsilon$ potem se bo optimalan vrdnosti spremenila za linearno kombinacijo $\Delta b_{i} y_{i}^{\star}$*
> *Epsilon samo nakazuje da na neki točki pridemo do konca in ne pridobimo več na optimalni vrednosti.*

<br>

**Dual splošnega linearnega problema**

Vsak lin. program znamo zapisati v std. obliki. Ampak kako bolj splošen lin. program pretvorimo v dual

**Prvotni problem (P):**
$$
\begin{array}{lll}
\max & \sum_{j=1}^{n} c_j x_j & \\
\text{p.p.} & \sum_{j=1}^{n} a_{ij} x_j \leq b_i, & i = 1, \dots, m' \\
& \sum_{j=1}^{n} a_{ij} x_j = b_i, & i = m'+1, \dots, m \\
& x_j \geq 0, & j = 1, \dots, n' \\
& x_j \in \mathbb{R}, & j = n'+1, \dots, n
\end{array}
$$

**Dualni problem (D):**
$$
\begin{array}{lll}
\min & \sum_{i=1}^{m} b_i y_i & \\
\text{p.p.} & \sum_{i=1}^{m} a_{ij} y_i \geq c_j, & j = 1, \dots, n' \\
& \sum_{i=1}^{m} a_{ij} y_i = c_j, & j = n'+1, \dots, n \\
& y_i \geq 0, & i = 1, \dots, m' \\
& y_i \in \mathbb{R}, & i = m'+1, \dots, m
\end{array}
$$


![[Pasted image 20260325194159.png]]

> **Splošno dualno dopolnjevanje**
> Naj bosta $x,y$ dopustni. Velja
> $x^{*},y^{*}$ sta optimalni $\Leftrightarrow$ $\sum_{j=1}^{n}a_{ij}x_{j}=b_{i}$ ali $y_{i} = 0$ samo za $i = 1,...m'$ oz. samo za $i$-je kjer imamo neenakosti.



 
**Dokaz pretvorbe in DD** temelji na tem da spremenimo nek splošen linearen program v standardnega, potem tega spremenimo v dual in ugtovimo da dobimo to kar smo dobili že prej.

$$ $$

Dokaz pretvorbe

$$ \max \quad \sum_{j=1}^{n'} c_{j} x_{j} + \sum_{j=n'+1}^{n} c_{j} x_{j}' + \sum_{j=n'+1}^{n} (-c_{j}) x_{j}'' $$

$\text{p. p.}$

$$ \sum_{j=1}^{n'} a_{ij} x_{j} + \sum_{j=n'+1}^{n} a_{ij} x_{j}' + \sum_{j=n'+1}^{n} (-a_{ij}) x_{j}'' \leq b_{i}, \quad i = 1, \dots, m $$

$$ \sum_{j=1}^{n'} -a_{ij} x_{j} + \sum_{j=n'+1}^{n} -a_{ij} x_{j}' + \sum_{j=n'+1}^{n} a_{ij} x_{j}'' \leq -b_{i}, \quad i = m'+1, \dots, m $$

$$x_{j}\geq 0 \quad j = 1,...,n'$$
$$x_{j}',x_{j}'' \geq 0 \quad j = n'+1,...,n$$

Zapišemo njegov dual

$$\min \quad \sum_{i=1}^{m'} b_{i} y_{i} + \sum_{i=m'+1}^{m} b_{i} y_{i}' + \sum_{i=m'+1}^{m} (-b_{i}) y_{i}''$$

$\text{p. p.}$

$$\sum_{i=1}^{m'} a_{ij} y_{i} + \sum_{i=m'+1}^{m} a_{ij} y_{i}' + \sum_{i=m'+1}^{m} (-a_{ij}) y_{i}'' \geq c_{j}, \quad j = 1, \dots, n$$

$$\sum_{i=1}^{m'} (-a_{ij}) y_{i} + \sum_{i=m'+1}^{m} (-a_{ij}) y_{i}' + \sum_{i=m'+1}^{m} a_{ij} y_{i}'' \geq -c_{j}, \quad j = n'+1, \dots, n$$

$$y_{i} \geq 0, \quad i = 1, \dots, m' \quad \text{in} \quad y_{i}', y_{i}'' \geq 0, \quad i = m'+1, \dots, m$$


Za dualno dopolnjevanje lahko iz duala vidimo da enakosti za dopustne rešitve pri $m'+1$  že veljajo kar pomeni da gledamo samo indekse kjer veljajo neenakosti.

$\sum_{j=1}^{n}a_{ij}x_{j}=b_{i}$ ali $y_{i} = 0$ samo za $i = 1,...m'$ oz. samo za $i$-je kjer imamo neenakosti.


***

**Analiza občutljivosti**

Kako se spremeni vrednost opt. rešitve, če malo spremenimo desne strani neenačb?

**Prvotni problem $\Pi$**

$$\quad \max c^T x$$
$$\text{p.p.} \; Ax \le b$$
$$\quad \quad x \ge 0$$

**spremenjena naloga $\Pi$**

$$\quad \max c^T x$$
$$\text{p.p.} \; Ax \le b+t$$
$$\quad \quad x \ge 0$$

Naj ima začetna naloga opt. rešitev:
$z^*$ ... opt. vrednost
$y^*$ ... opt. rešitev duala

> Naj bo $x$ poljubna dopustna rešitev spremenjene naloge. Potem velja $c^T x \le z^* + t^T y^*$.
> 
> >[!|dokaz]+ Dokaz:
> >
> > **Dual  začetne naloge**
> >
> >$$\begin{array}
\\
\min & b^{T}y\\
\text{p.p.} &  A^T y \ge c\\ 
& y \ge c
\end{array}$$
> >
> > 
> > **Dual spremenjene naloge**
> > 
> >$$\begin{array}
\\
\min & (b + t)^T y\\
\text{p.p.} &  A^T y \ge c\\ 
& y \ge 0
\end{array}$$
> > 
> > Množica dopustnih rešitev je pri obeh nalogah določena z neenačbami $A^T y \ge c, y \ge 0$.
> > $\implies$ obe nalogi imata isto množico dopustnih rešitev.
> > $\implies y^*$ je dop. rešitev za dual spremenjene naloge (ne nujno optimalna). Torej, če je $x$ dop. rešitev spr. naloge po šibki dualnosti velja
> > 
> > $$c^{T}x \leq (b+t)^{T}y^{*}=b^T y^* + t^T y^* $$
> > 
> > To pa je po krepki dualnosti pri $\Pi$ in $\Pi'$ enako
> > 
> > $$b^T y^* + t^T y^*=z^* + t^T y^*$$
> > 



---



**Zgled: Problem kmeta**

$$\max 3x_1 + 5x_2 + 4x_3$$

p.p. (pod pogojem):

$$x_1 + x_2 + x_3 \le 50$$
$$3x_1 + 4x_2 + 5x_3 \le 250$$
$$10x_1 + 15x_2 + 12x_3 \le 600$$
$$x_1, x_2, x_3 \ge 0$$

**Vemo:**
*   $x^* = (0, 40, 0)^T$
*   $z^* = 200$
*   $y^* = (0, 0, 1/3)^T$

**Ali se mu izplača:**
*   najeti več zemlje?
*   najeti dodatno delovno silo?
*   vzeti posojilo?

**Analiza:**
*   $y_1^* = 0$: zemlje se ne splača najeti (ostalo je 10 ha zemlje...)
*   $y_2^* = 0$: delovne sile se ne splača najeti (ostalo 90 enot...)
*   $y_3^* = \frac{1}{3}$: posojilo se splača najeti, če obresti ne presegajo $33 \frac{1}{3} \%$.
    Za vsako enoto, ki jo dodamo na desni, se dobiček lahko poveča za $1/3$.
    $$z \le z^* + (0, 0, 1/3) \begin{bmatrix} t_1 \\ t_2 \\ t_3 \end{bmatrix} = z^* + \frac{1}{3} t_3$$

**Koliko posojila?**
Posejmo dodatno koruzo (največji koef. v krit. funkciji)
Rešitev mora ostati dopustna.
Nova rešitev: $(0, 40+k, 0)$

$\text{zemlja: } 40+k \le 50 \Rightarrow k \le 10$
$\text{del. sila: } 160 + 4k \le 250 \Rightarrow k \le \frac{90}{4} = 22,5$
Skupaj sledi: $k \le 10$



$\bar{x} = (0, 50, 0)$
$\bar{z} = 250$ , povečanje za 50

Potrebni kapital: $15 \cdot 50 = 750$
Izposoditi si je treba 150
(oziroma $150 \cdot 40 = 6000$ eur, ker smo enačbo okrajšali s 40)

To se izplača, če so obresti manj kot 50.
Zdaj je kritična zemlja.
