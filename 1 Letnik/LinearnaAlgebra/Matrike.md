**Matrike**

**Definicija in primeri matrik**

Matrika velikosti $m \times n$ je zbirka $n$ vektorjev $m$ dimenzij, torej element prostora $(\mathbb{R}^n)^m$.

$$A = \begin{bmatrix} a_{1,1} & \dots & a_{1,n} \\ \vdots & & \vdots \\ a_{m,1} & \dots & a_{m,n} \end{bmatrix} $$


Stolpčnim vektorjem
$$\begin{bmatrix} a_{1,1} \\ \vdots \\ a_{m,1} \end{bmatrix}, \begin{bmatrix} a_{1,2} \\ \vdots \\ a_{m,2} \end{bmatrix}, \dots, \begin{bmatrix} a_{1,n} \\ \vdots \\ a_{m,n} \end{bmatrix}$$
pravimo stolpci matrike. Matriko lahko zapišemo kot
$$A = \begin{bmatrix} \begin{bmatrix} a_{1,1} \\ \vdots \\ a_{m,1} \end{bmatrix}, \begin{bmatrix} a_{1,2} \\ \vdots \\ a_{m,2} \end{bmatrix}, \dots, \begin{bmatrix} a_{1,n} \\ \vdots \\ a_{m,n} \end{bmatrix} \end{bmatrix}$$
Vrstičnim vektorjem
$$[ a_{1,1} \dots a_{1,n} ], [ a_{2,1} \dots a_{2,n} ], \dots, [ a_{m,1} \dots a_{m,n} ]$$
pravimo vrstice matrike. Na preseku $i$-te vrstice in $j$-tega stolpca matrike leži $(i,j)$-ti element (oziroma $(i,j)$-ti vhod) matrike.

**Operacije z matrikami**

Produkt matrike s skalarjem je definiran po komponentah
$$\alpha \begin{bmatrix} a_{1,1} & \dots & a_{1,n} \\ \vdots & & \vdots \\ a_{m,1} & \dots & a_{m,n} \end{bmatrix} := \begin{bmatrix} \alpha a_{1,1} & \dots & \alpha a_{1,n} \\ \vdots & & \vdots \\ \alpha a_{m,1} & \dots & \alpha a_{m,n} \end{bmatrix}$$
Tudi vsota dveh matrik enake velikosti je definirana po komponentah
$$\begin{bmatrix} a_{1,1} & \dots & a_{1,n} \\ \vdots & & \vdots \\ a_{m,1} & \dots & a_{m,n} \end{bmatrix} + \begin{bmatrix} b_{1,1} & \dots & b_{1,n} \\ \vdots & & \vdots \\ b_{m,1} & \dots & b_{m,n} \end{bmatrix} := \begin{bmatrix} a_{1,1} + b_{1,1} & \dots & a_{1,n} + b_{1,n} \\ \vdots & & \vdots \\ a_{m,1} + b_{m,1} & \dots & a_{m,n} + b_{m,n} \end{bmatrix}$$
Lastnosti teh dveh operacij so enake kot pri vektorjih.

**Produkt dveh matrik velikosti $m \times n$ in $n \times p$**

Produkt dveh matrik $A = \begin{bmatrix} a_{1,1} & \dots & a_{1,n} \\ \vdots & & \vdots \\ a_{m,1} & \dots & a_{m,n} \end{bmatrix}$ in $B = \begin{bmatrix} b_{1,1} & \dots & b_{1,p} \\ \vdots & & \vdots \\ b_{n,1} & \dots & b_{n,p} \end{bmatrix}$ je taka matrika $C = AB$ velikosti $m \times p$, katere $(i,j)$-ti element je
$$C_{i,j} = \sum_{k=1}^n a_{i,k}b_{k,j}$$
Torej je $C_{i,j}$ ravno skalarni produkt $i$-te vrstice matrike $A$ in $j$-tega stolpca matrike $B$. Definicijo $C_{i,j}$ lahko zapišemo tudi takole
$$\left[ C_{i,j} \right] = \left[ a_{i,1} \dots a_{i,n} \right] \begin{bmatrix} b_{1,j} \\ \vdots \\ b_{n,j} \end{bmatrix} = \left[ \sum_{k=1}^n a_{i,k}b_{k,j} \right]$$

Osnovne lastnosti množenja matrik so:
*   $(AB)C = A(BC)$
*   $(A+B)C = AC + BC$
*   $A(B+C) = AB + AC$
*   $(\lambda A)B = A(\lambda B) = \lambda (AB)$

**Transponiranka matrike**

Transponiranka matrike $A$ je taka matrika $A^T$, da za vsak $i$ in $j$ velja: $(i,j)$-ti element $A^T$ je enak $(j,i)$-temu elementu $A$. S formulo:
$$\left( \begin{bmatrix} a_{1,1} & \dots & a_{1,n} \\ \vdots & & \vdots \\ a_{m,1} & \dots & a_{m,n} \end{bmatrix} \right)^T := \begin{bmatrix} a_{1,1} & \dots & a_{m,1} \\ \vdots & & \vdots \\ a_{1,n} & \dots & a_{m,n} \end{bmatrix}$$

Primer transponiranja matrike
$$\left( \begin{bmatrix} 1 & 2 & 3 \\ 4 & 5 & 6 \end{bmatrix} \right)^T = \begin{bmatrix} 1 & 4 \\ 2 & 5 \\ 3 & 6 \end{bmatrix}$$
Osnovne lastnosti transponiranja matrik so:
*   $(A^T)^T = A$,
*   $(AB)^T = B^T A^T$, (izpeljava iz skalarnega produkta kot množenje matrik)
*   $(A+B)^T = A^T + B^T$,
*   $(\lambda A)^T = \lambda A^T$.

**Ničelna matrika in Identična matrika**

Ničelna matrika je taka matrika, ki ima vse elemente enake nič. Označimo jo z $0_{m,n}$ za matriko velikosti $m \times n$. Kadar sta $m$ in $n$ znana iz konteksta, pišemo kar $0$ namesto $0_{m,n}$. Velja:
*  $A + 0 = 0+ A = A$
*   $A0 = 0A = 0$
*  $0_{m,n}^{T} = 0_{n,m}$

Identična matrika je taka kvadratna matrika, ki ima po glavni diagonali same enke, drugod pa same ničle. Identično matriko velikosti $n \times n$ označimo z $I_n$. Kadar je $n$ znan iz konteksta, pišemo kar $I$ namesto $I_n$

- $AI = IA = A$
- $I^{T} = I$

**Matrični zapis sistema linearnih enačb**

Sistem linearnih enačb
$$a_{1,1}x_1 + \dots + a_{1,n}x_n = b_1$$
$$\vdots$$
$$a_{m,1}x_1 + \dots + a_{m,n}x_n = b_m$$
zapišemo s pomočjo matričnega množenja takole
$$\begin{bmatrix} a_{1,1} & \dots & a_{1,n} \\ \vdots & & \vdots \\ a_{m,1} & \dots & a_{m,n} \end{bmatrix} \begin{bmatrix} x_1 \\ \vdots \\ x_n \end{bmatrix} = \begin{bmatrix} a_{1,1}x_1 + \dots + a_{1,n}x_n \\ \vdots \\ a_{m,1}x_1 + \dots + a_{m,n}x_n \end{bmatrix} = \begin{bmatrix} b_1 \\ \vdots \\ b_m \end{bmatrix}$$
Na kratko to zapišemo kot $Ax = b$, kjer je
$$A = \begin{bmatrix} a_{1,1} & \dots & a_{1,n} \\ \vdots & & \vdots \\ a_{m,1} & \dots & a_{m,n} \end{bmatrix}, \quad x = \begin{bmatrix} x_1 \\ \vdots \\ x_n \end{bmatrix}, \quad b = \begin{bmatrix} b_1 \\ \vdots \\ b_m \end{bmatrix}$$

**Matrični zapis Gaussove metode**

Spomnimo se, da sistem rešujemo z uporabo naslednjih treh tipov elementarnih transformacij:
*   k eni od enačb lahko prištejemo večkratnik druge enačbe;
*   lahko zamenjamo vrstni red dveh enačb;
*   enačbo lahko pomnožimo z neničelno konstanto.

Poskusimo te transformacije zapisati z matrikami. Definirajmo elementarne $m \times m$ matrike $E_{i,j}(\alpha)$, $P_{i,j}$ in $E_i(\beta)$ takole:
*   matriko $E_{i,j}(\alpha)$ dobimo tako, da v identični matriki $I_m$ k $i$-ti vrstici prištejemo $\alpha$-kratnik $j$-te vrstice;
*   matriko $P_{i,j}$ dobimo tako, da v $I_m$ zamenjamo $i$-to in $j$-to vrstico;
*   matriko $E_i(\beta)$ dobimo tako, da v $I_m$ množimo $i$-to vrstico z $\beta$.

Primeri elementarnih $2 \times 2$ matrik
$$E_{1,2}(7) = \begin{bmatrix} 1 & 7 \\ 0 & 1 \end{bmatrix}, \quad P_{1,2} = \begin{bmatrix} 0 & 1 \\ 1 & 0 \end{bmatrix}, \quad E_2(5) = \begin{bmatrix} 1 & 0 \\ 0 & 5 \end{bmatrix}$$

Krajši račun pokaže, da lahko elementarne transformacije opišemo s pomočjo elementarnih matrik takole:
*   če v sistemu $Ax = b$ k $i$-ti enačbi prištejemo $\alpha$-kratnik $j$-te enačbe, potem dobimo sistem $E_{i,j}(\alpha)Ax = E_{i,j}(\alpha)b$;
*   če v sistemu $Ax = b$ zamenjamo $i$-to in $j$-to enačbo, potem dobimo sistem $P_{i,j}Ax = P_{i,j}b$;
*   če v sistemu $Ax = b$ pomnožimo $i$-to enačbo z $\beta$, potem dobimo sistem $E_i(\beta)Ax = E_i(\beta)b$.

Gaussovo metodo lahko povemo takole: sistem $Ax = b$ toliko časa množimo z elementarnimi matrikami z leve, dokler ne dobimo sistema $A'x = b'$, pri katerem je $A'$ reducirane stopničaste oblike.
$$\begin{bmatrix}
0 & \dots & 0 & 1 & \times & \dots & \times & 0 & \dots & 0 & \times & \dots \\
0 & \dots & 0 & 0 & 1 & \times & \dots & 0 & \dots & 0 & \times & \dots \\
0 & \dots & 0 & 0 & 0 & 1 & \dots & 0 & \dots & 0 & \times & \dots \\
\vdots & & \vdots & \vdots & \vdots & \vdots & \ddots & \vdots & & \vdots & \vdots & \\
0 & \dots & 0 & 0 & 0 & 0 & \dots & 1 & \dots & 0 & \times & \dots \\
0 & \dots & 0 & 0 & 0 & 0 & \dots & 0 & 1 & \dots & \times & \dots \\
\vdots & & \vdots & \vdots & \vdots & \vdots & & \vdots & \vdots & \ddots & \vdots & \\
0 & \dots & 0 & 0 & 0 & 0 & \dots & 0 & 0 & \dots & 0 & \dots
\end{bmatrix}$$

**Matrični zapis metode najmanjših kvadratov**

Kadar je sistem $Ax = b$ nerešljiv, poiščemo tak $x_0$, ki minimizira izraz
$$||Ax - b||$$
Takemu $x_0$ pravimo posplošena rešitev sistema $Ax=b$ (2).

Primerjajmo matrični zapis zgoraj z vektorskim zapisom od zadnjič. Če so $a_1, \dots, a_n$ stolpci matrike $A$, potem je $Ax = x_1a_1 + \dots + x_na_n$. Izraz $||x_1a_1 + \dots + x_na_n - b||$ je minimalen če je $x_1a_1 + \dots + x_na_n - b$ pravokoten na $a_1, \dots, a_n$. Če to razpišemo, dobimo
$$\begin{bmatrix} \langle a_1, a_1 \rangle & \dots & \langle a_1, a_n \rangle \\ \vdots & & \vdots \\ \langle a_n, a_1 \rangle & \dots & \langle a_n, a_n \rangle \end{bmatrix} \begin{bmatrix} x_1 \\ \vdots \\ x_n \end{bmatrix} = \begin{bmatrix} \langle a_1, b \rangle \\ \vdots \\ \langle a_n, b \rangle \end{bmatrix}$$
kar se v matričnem zapisu glasi $A^T Ax = A^T b$.

Skicirali smo dokaz naslednje trditve. Bolj podroben dokaz je spodaj.

**Trditev**
Posplošene rešitve sistema $Ax = b$ so enake običajnim rešitvam sistema
$$A^T Ax = A^T b $$

**Opomba:** Sistem (3) je vedno rešljiv v običajnem smislu (v 2. semestru).
**Opomba:** V dokazu bomo večkrat uporabili formulo $\langle c, d \rangle = c^T d$.

**Dokaz:** 

V desno smer je že dokazano v prejšnjih datotekah.

Dokaz v nasprotno smer je nekoliko daljši. 

Predpostavimo, da $x_0$ zadovoljuje $A^TAx_0 = A^Tb$.


Naj bo $x$ poljubna rešitev. Potem lahko zapišemo:
$\|Ax - b\|^2 = \|A(x - x_0) + Ax_0 - b\|^2$

Uporabimo lastnost, da za poljubna vektorja $u, v$ velja $\|u+v\|^2 = \|u\|^2 + \|v\|^2 + 2u^Tv$.
Tukaj naj bo $u = A(x - x_0)$ in $v = Ax_0 - b$.
$\|Ax - b\|^2 = \|A(x - x_0)\|^2 + \|Ax_0 - b\|^2 + 2(A(x - x_0))^T(Ax_0 - b)$
$= \|A(x - x_0)\|^2 + \|Ax_0 - b\|^2 + 2(x - x_0)^TA^T(Ax_0 - b)$

Ker predpostavljamo $A^TAx_0 = A^Tb$, sledi $A^TAx_0 - A^Tb = 0$, torej $A^T(Ax_0 - b) = 0$.
Zato je zadnji člen:
$2(x - x_0)^T \underbrace{A^T(Ax_0 - b)}_{=0} = 0$

Tako se enačba poenostavi na:
$\|Ax - b\|^2 = \|A(x - x_0)\|^2 + \|Ax_0 - b\|^2$

Ker je $\|A(x - x_0)\|^2 \ge 0$, velja:
$\|Ax - b\|^2 \ge \|Ax_0 - b\|^2$

*Pokažemo  da je katerakoli druga rešitev splošne enačbe večja ali enaka rešitivi novega sistema*

**Najkrajša rešitev sistema**

Kadar je sistem $Ax=b$ neenolično rešljiv, nas zanima najkrajša rešitev, se pravi rešitev z najmanjšo normo. Pokazali bomo, da najkrajšo rešitev dobimo z nastavkom $x = A^T y$.

**Trditev**
Najkrajša rešitev sistema $Ax=b$ je $A^T y_0$, kjer je $y_0$ poljubna rešitev

$$A A^T y = b$$

**Opomba:** Da iz rešljivosti sistema $Ax=b$ sledi rešljivost sistema $A A^T y = b$ bomo znali dokazati šele v drugem semestru.

**Dokaz:** 

Če obstaja partikularna rešitev potem tvori afino ravnino.

Splošna rešitev bo $x_{s}=x_{p}+x_{h}\,;\;x_{h}\in \ker A$.

*$x_{h} = x_{s}- x_{0}$
$Ax_{h}=A(x_{s}-x_{0}) = b-b= 0 \Rightarrow x_{h} \in \ker A$*

Naj velja da je $x_{0} = A^Ty_{0}$ rešitev o kateri še ne vemo nič, poskusimo dokazati da je najkrajša.

Velja da je $x_{0}$ v vrstičnem prostoru $A$. Vrstični prostor $A$ je ortogonalen $\ker A$. To pomeni da je $x_{0}$ pravokoten na $x_{h}$ ki je smerni vektor afine ravnine. To pomeni da je $x_{0}^2+x_{h}^2=x_{s}^2$.

**Inverz matrike**

Inverz kvadratne matrike $A$ je taka kvadratna matrika $B$, da velja
$$AB = BA = I$$
Matrika ima lahko kvečjemu en inverz. Če sta namreč $B_1$ in $B_2$ dva inverza matrike $A$, potem velja $AB_1 = I$, $B_1A = I$, $AB_2 = I$ in $B_2A = I$, torej je
$$B_1 = IB_1 = (B_2A)B_1 = B_2(AB_1) = B_2I = B_2$$
Če matrika $A$ ima inverz, ga označimo z $A^{-1}$. Ničelna matrika seveda nima inverza. Zanimivo pa je, da inverza nimajo tudi nekatere neničelne matrike.

**Primeri matrik, ki nimajo inverza**
*   Če ima matrika $A$ ničelno vrstico, potem nima inverza. Za vsako matriko $B$ ima namreč produkt $AB$ tudi ničelno vrstico, medtem ko matrika $I$ nima ničelne vrstice. Torej je $AB \ne I$ za vsak $B$.
*   Če ima matrika $A$ ničeln stolpec, potem nima inverza. Za vsako matriko $B$ ima namreč produkt $BA$ tudi ničeln stolpec, medtem ko matrika $I$ nima ničelnega stolpca. Torej je $BA \ne I$ za vsak $B$.

Če imajo matrike $A_1, \dots, A_n$ inverze, potem ima inverz tudi njihov produkt. Velja namreč
$$(A_1 \dots A_n)^{-1} = A_n^{-1} \dots A_1^{-1}$$
Inverze matrik lahko uporabimo pri reševanju kvadratnih linearnih sistemov. Če $Ax=b$ pomnožimo z leve z $A^{-1}$, dobimo
$$x = Ix = (A^{-1}A)x = A^{-1}(Ax) = A^{-1}b$$
Naredimo še preizkus
$$A(A^{-1}b) = (AA^{-1})b = Ib = b$$

**Računanje inverza z Gaussovo metodo**

Matriko $A$ razširimo na desno z identično matriko iste velikosti. Dobimo matriko $[A|I]$. To matriko obdelujemo z elementarnimi transformacijami po vrsticah toliko časa, dokler levo od črte ne dobimo bodisi matrike z ničelno vrstico bodisi identične matrike. V prvem primeru matrika $A$ nima inverza, v drugem primeru, pa je inverz tisto, kar stoji desno od črte.


Dokažimo sedaj, da ta metoda vedno deluje.
Naj bodo $E_1, \dots, E_n$ take elementarne matrike, da ima matrika $S = E_n \dots E_1 A$ reducirano stopničasto obliko. Ločimo dva primera.
*   Če ima matrika $S$ ničelno vrstico, potem ni obrnljiva, saj ima potem tudi matrika $S^T$ ničelno vrstico za vsak $T$ (glej prvi primer). Odtod sledi, da tudi matrika $A$ ni obrnljiva (uporabi drugi in tretji primer).
*   Če pa matrika $S$ nima ničelne vrstice, potem je enaka identični matriki. Odtod sledi $A^{-1} = E_n \dots E_1$. To pa je ravno tisto, kar dobimo na desni v
$$\left[ A|I \right] \xrightarrow{E_1} \left[ E_1A|E_1 \right] \xrightarrow{E_2} \dots \xrightarrow{E_n} \left[ E_n \dots E_1A | E_n \dots E_1 \right] = \left[ I|A^{-1} \right]$$
Spotoma smo dokazali, da ima matrika $A$ inverz natanko tedaj, ko je enaka produktu elementarnih matrik.