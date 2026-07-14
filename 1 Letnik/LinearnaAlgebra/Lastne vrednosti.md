#### 1. Lastni problem

Za dano kvadratno matriko iščemo čimpreprostejšo matriko (npr. diagonalno ali zgornje trikotno matriko), ki ji je podobna.
Vemo, da pri tem zelo pomaga, če ima matrika invarianten podprostor. Vprašajmo se, kdaj ima matrika enorazsežen invarianten podprostor.

**Trditev 1**
Za vsako matriko $A \in M_n(F)$ sta ekvivalentni trditvi:
1. Obstaja enorazsežen podprostor v $F^n$, ki je invarianten za $A$.
2. Obstaja tak skalar $\lambda \in F$ in tak neničeln vektor $v \in F^n$, da velja $Av = \lambda v$.

**Dokaz:**
* Če velja (2), potem je očitno $\text{Lin}\{v\}$ enorazsežen invarianten podprostor za $A$. Torej velja (1).
* Če velja (1), potem obstaja tak neničeln vektor $v \in F^n$, da je podprostor $\text{Lin}\{v\}$ invarianten za $A$. Ker je $Av \in \text{Lin}\{v\}$, obstaja tak skalar $\lambda \in F$, da velja $Av = \lambda v$. Torej velja (2).

Trditev 1 služi kot motivacija za študij enačbe
$Av = \lambda v$
kjer je $A \in M_n(F)$ dana matrika, iščemo pa skalar $\lambda \in F$ in vektor $v \in F^n$.
Enačbi $Av = \lambda v$ rečemo **lastni problem** za matriko $A$. Trivialna rešitev lastnega problema je $v = 0$ in $\lambda = \text{karkoli}$. Ta rešitev za nas ni zanimiva. Če je $(\lambda, v)$ netrivialna rešitev lastnega problema, potem pravimo, da je $\lambda$ **lastna vrednost** matrike $A$, $v$ pa **lastni vektor** matrike $A$. Bolj natančno:

**Definicija lastne vrednosti in lastnega vektorja**
Skalar $\lambda \in F$ je **lastna vrednost** matrike $A \in M_n(F)$, če obstaja tak neničeln vektor $v \in F^n$, da velja $Av = \lambda v$. Vsakemu takemu vektorju $v$ pravimo **lastni vektor** matrike $A$, ki pripada lastni vrednosti $\lambda$.
**Pozor:** Vsak lastni vektor matrike $A$ je po definiciji neničeln vektor.
**Posledica:** Iz Trditve 1 sledi, da ima matrika $A$ enorazsežen invarianten podprostor natanko tedaj, ko ima kako lastno vrednost.

Pri iskanju lastnih vrednosti in lastnih vektorjev matrike $A$ si pomagamo z naslednjo trditvijo:

**Trditev 2**
Za vsako matriko $A \in M_n(F)$ in vsak skalar $\lambda \in F$ so ekvivalentne naslednje trditve:
1. $\lambda$ je lastna vrednost matrike $A$.
2. $\text{Ker}(A - \lambda I) \ne \{0\}$.
3. Matrika $A - \lambda I$ ni obrnljiva.
4. $\det(A - \lambda I) = 0$.

**Dokaz:** Enačbo $Av = \lambda v$ lahko zapišemo v obliki $(A - \lambda I)v = 0$. Velja namreč, da je $(A - \lambda I)v = Av - \lambda Iv = Av - \lambda v$. Odtod sledi, da je točka (1) ekvivalentna s točko (2).
Ekvivalentnost točk (2), (3) in (4) sledi iz karakterizacij obrnljivih matrik. Matrika $A - \lambda I$ je namreč obrnljiva natanko tedaj, ko je $\det(A - \lambda I) \ne 0$, in natanko tedaj, ko so stolpci matrike $A - \lambda I$ linearno neodvisni.

#### Karakteristični polinom

Prvi korak pri reševanju lastnega problema za matriko $A$ je izračun karakterističnega polinoma za matriko $A$.

**Definicija karakterističnega polinoma**
**Karakteristični polinom** matrike $A \in M_n(F)$ je polinom $p_A(x) = \det(A - xI)$. ($I$ je identična matrika velikosti $n$.)
S pomočjo karakterističnega polinoma potem izračunamo vse lastne vrednosti matrike. Velja namreč:

**Trditev 3**
Skalar $\lambda \in F$ je lastna vrednost matrike $A \in M_n(F)$ natanko tedaj, ko je $\lambda$ ničla karakterističnega polinoma matrike $A$.
**Dokaz:** To je ekvivalenca med (1) in (4) v Trditvi 2.

**Dogovor:** V nadaljevanju se bomo omejili na primer $F = \mathbb{C}$.
**Razlog:** Osnovni izrek algebre pravi, da ima vsak nekonstanten polinom s kompleksnimi koeficienti vsaj eno kompleksno ničlo. Odtod sledi, da ima vsaka kompleksna kvadratna matrika vsaj eno lastno vrednost.
Karakteristični polinom lahko razcepimo na linearne faktorje:
$p_A(x) = (-1)^n (x - \lambda_1)^{n_1} \dots (x - \lambda_k)^{n_k}$
kjer so $\lambda_1, \dots, \lambda_k$ vse paroma različne lastne vrednosti matrike $A$. Naravna števila $n_1, \dots, n_k$ očitno zadoščajo $n_1 + \dots + n_k = n$. Pravimo jim **algebraične večkratnosti** lastnih vrednosti $\lambda_1, \dots, \lambda_k$. Bolj natančno:

**Definicija algebraične večkratnosti**
Če je lastna vrednost $\lambda$ $m$-kratna ničla karakterističnega polinoma, potem pravimo, da je njena **algebraična večkratnost** enaka $m$.

**Karakteristični polinom zgornje trikotne matrike**
Če je
$A = \begin{pmatrix} a_{1,1} & a_{1,2} & \dots & a_{1,n} \\ 0 & a_{2,2} & \dots & a_{2,n} \\ \vdots & \vdots & \ddots & \vdots \\ 0 & 0 & \dots & a_{n,n} \end{pmatrix}$
potem je $\det(A - xI) = (-1)^n (x - a_{1,1})(x - a_{2,2})\dots(x - a_{n,n})$.
**Dokaz:** Determinanta gornjetrikotne matrike je produkt njenih diagonalnih elementov, torej je $\det(A - xI) = (a_{1,1} - x)(a_{2,2} - x)\dots(a_{n,n} - x)$.

**Trditev 4**
Če sta matriki $A$ in $B$ podobni, potem je $\det(A - xI) = \det(B - xI)$. Torej imata $A$ in $B$ enake lastne vrednosti z enakimi algebraičnimi večkratnostmi.
**Dokaz:** Če je $A = PBP^{-1}$, potem je $A - xI = PBP^{-1} - xI = PBP^{-1} - xPIP^{-1} = P(B - xI)P^{-1}$. Torej je
$\det(A - xI) = \det(P(B - xI)P^{-1}) = \det P \det(B - xI) \det P^{-1} = \det P \det P^{-1} \det(B - xI) = \det(PP^{-1}) \det(B - xI) = \det I \det(B - xI) = \det(B - xI)$.

#### Lastni podprostori

Množica vseh lastnih vektorjev matrike $A$, ki pripadajo lastni vrednosti $\lambda$, je enaka $\text{Ker}(A - \lambda I) \setminus \{0\}$. Ta množica je vedno neskončna.

Vektor $0$ ni nikoli lastni vektor. Če ga dodamo k množici lastnih vektorjev, dobimo množico $\text{Ker}(A - \lambda I)$, ki je vektorski podprostor v $\mathbb{C}^n$.

**Definicija lastnega podprostora in geometrijske večkratnosti**
Če je $\lambda$ lastna vrednost matrike $A$, potem vektorskemu podprostoru $\text{Ker}(A - \lambda I)$ pravimo **lastni podprostor** matrike $A$ za lastno vrednost $\lambda$, njegovi dimenziji pa **geometrijska večkratnost** lastne vrednosti $\lambda$.
**Opomba:** Lastne podprostore matrike $A$ poiščemo tako, da za vsako njeno lastno vrednost $\lambda$ rešimo homogen sistem linearnih enačb $(A - \lambda I)v = 0$, kjer smatramo, da so komponente vektorja $v$ spremenljivke.


**Trditev 5**
Naj bosta $A$ in $B$ podobni matriki in naj bo $\lambda$ lastna vrednost za $A$ z geometrijsko večkratnostjo $m$. Potem je $\lambda$ tudi lastna vrednost za $B$ z geometrijsko večkratnostjo $m$.
**Opomba:** Ker so pri diagonalni matriki geometrijske večkratnosti lastnih vrednosti enake algebraičnim večkratnostim, je to res tudi za vse matrike, ki so podobne diagonalnim.

#### Diagonalizacija matrik

S pomočjo lastnih vrednosti in lastnih vektorjev matrike $A$ lahko včasih poiščemo diagonalno matriko, ki je podobna matriki $A$.
Recimo, da ima matrika $A$ $n$ linearno neodvisnih vektorjev $v_1, \dots, v_n$ in naj bodo $\lambda_1, \dots, \lambda_n$ pripadajoče lastne vrednosti, se pravi
$Av_1 = \lambda_1 v_1, \dots, Av_n = \lambda_n v_n$.
Odtod sledi, da je matrika
$P = [v_1 \dots v_n]$
obrnljiva in velja
$AP = [Av_1 \dots Av_n] = [\lambda_1 v_1 \dots \lambda_n v_n] = PD$
kjer je
$D = \begin{pmatrix} \lambda_1 & \dots & 0 \\ \vdots & \ddots & \vdots \\ 0 & \dots & \lambda_n \end{pmatrix}$.

#### 2. Schurjev izrek

Vemo, da ni vsaka kvadratna matrika nad $\mathbb{C}$ podobna kaki diagonalni matriki. Pokažimo pa, da je vedno podobna kaki zgornje trikotni matriki. Kasneje se bo izkazalo, da je podobna zelo posebni zgornje trikotni matriki (Jordanovi kanonični formi).

**Schurjev izrek**
Vsaka kvadratna matrika nad $\mathbb{C}$ je podobna kaki zgornje trikotni matriki.

**Dokaz** bo z popolno indukcijo po velikosti matrike. Očitno trditev velja za matrike velikosti $1$, ker so te že same zgornje trikotne. Recimo sedaj, da trditev velja za vse matrike velikosti $n-1$ in vzemimo poljubno matriko $A$ velikosti $n$. Radi bi dokazali, da trditev velja tudi za matriko $A$.
Naj bo $\lambda$ lastna vrednost matrike $A$ in naj bo $v_1$ pripadajoči lastni vektor. Naj bodo $v_2, \dots, v_n$ dopolnitev $v_1$ do baze za $F^n$. Potem je matrika
$P = [v_1 \dots v_n]$
obrnljiva. Razvijmo vektorje $Av_2, \dots, Av_n$ po bazi $v_1, v_2, \dots, v_n$.
$Av_2 = \alpha_{2,1} v_1 + \alpha_{2,2} v_2 + \dots + \alpha_{2,n} v_n$
$\vdots$
$Av_n = \alpha_{n,1} v_1 + \alpha_{n,2} v_2 + \dots + \alpha_{n,n} v_n$.
Potem velja
$AP = A [v_1 v_2 \dots v_n] = [Av_1 Av_2 \dots Av_n]$
$= [\lambda v_1 \quad \alpha_{2,1}v_1 + \alpha_{2,2}v_2 + \dots + \alpha_{2,n}v_n \quad \dots \quad \alpha_{n,1}v_1 + \alpha_{n,2}v_2 + \dots + \alpha_{n,n}v_n]$
$= [v_1 v_2 \dots v_n] \begin{pmatrix} \lambda & \alpha_{2,1} & \dots & \alpha_{n,1} \\ 0 & \alpha_{2,2} & \dots & \alpha_{n,2} \\ \vdots & \vdots & \ddots & \vdots \\ 0 & \alpha_{2,n} & \dots & \alpha_{n,n} \end{pmatrix} = P \begin{pmatrix} \lambda & c \\ 0 & B \end{pmatrix}$.
Po indukcijski predpostavki obstaja taka obrnljiva matrika $Q'$ velikosti $n-1$ in taka zgornje trikotna matrika $T'$ velikosti $n-1$, da velja
$B = Q' T' (Q')^{-1}$.
Odtod sledi
$P^{-1} A P = \begin{pmatrix} \lambda & c \\ 0 & B \end{pmatrix}$.
Definirajmo matriko $Q = \begin{pmatrix} 1 & 0 \\ 0 & Q' \end{pmatrix}$. Ta matrika je obrnljiva in njen inverz je $Q^{-1} = \begin{pmatrix} 1 & 0 \\ 0 & (Q')^{-1} \end{pmatrix}$.
Potem je
$Q^{-1} (P^{-1} A P) Q = \begin{pmatrix} 1 & 0 \\ 0 & (Q')^{-1} \end{pmatrix} \begin{pmatrix} \lambda & c \\ 0 & B \end{pmatrix} \begin{pmatrix} 1 & 0 \\ 0 & Q' \end{pmatrix}$
$= \begin{pmatrix} \lambda & cQ' \\ 0 & (Q')^{-1} B Q' \end{pmatrix} = \begin{pmatrix} \lambda & cQ' \\ 0 & T' \end{pmatrix}$.
kar je zgornje trikotna matrika. S tem je indukcijski korak dokazan.


#### 3. Obstoj diagonalizacije

Še vedno delamo s kvadratnimi matrikami, ki imajo kompleksne elemente.

**Definicija diagonalizacije**
Diagonalizacija matrike $A$ je razcep $A = PDP^{-1}$, kjer je $P$ obrnljiva matrika, $D$ pa diagonalna matrika.

Naj bodo $v_1, \dots, v_n$ stolpci matrike $P$, $d_1, \dots, d_n$ pa diagonalni elementi matrike $D$. Očitno velja $AP = [Av_1 \dots Av_n]$ in $PD = [d_1 v_1 \dots d_n v_n]$. Torej velja $AP = PD$ natanko tedaj, ko je $Av_i = d_i v_i$ za vsak $i = 1, \dots, n$.
Matrika $P$ je obrnljiva natanko tedaj, ko so $v_1, \dots, v_n$ linearno neodvisni.

**Povzetek:**
*   Diagonalni elementi matrike $D$ so ravno lastne vrednosti matrike $A$.
*   Stolpci matrike $P$ so linearno neodvisni lastni vektorji matrike $A$.
*   Matrika $A$ ima diagonalizacijo natanko tedaj, ko ima $n$ linearno neodvisnih lastnih vektorjev.

**Trditev 1**

V nadaljevanju se bomo večkrat sklicevali na naslednjo trditev.

**Naslednje lastnosti matrike $A$ so ekvivalentne:**
*   Matrika $A$ ima diagonalizacijo.
*   Matrika $A$ je podobna diagonalni matriki.
*   Matrika $A$ ima $n$ linearno neodvisnih lastnih vektorjev.
*   Vsota lastnih podprostorov matrike $A$ je enaka $\mathbb{C}^n$.

**Dokaz:** Iz definicij sledi, da sta prva in druga lastnost ekvivalentni. Dokazali smo že, da sta druga in tretja lastnost ekvivalentni. Tretja in četrta trditev obe pravita, da so lastni vektorji $A$ ogrodje za $\mathbb{C}^n$.

**Trditev 2**

Naslednja trditev je bolj tehnične narave, ampak ima zanimive posledice.

**Lastni vektorji, ki pripadajo paroma različnim lastnim vrednostim, so linearno neodvisni.**

**Dokaz:** Naj bodo $\lambda_1, \dots, \lambda_k$ paroma različne lastne vrednosti matrike $A$ in naj bodo $v_1, \dots, v_k$ pripadajoči lastni vektorji. Se pravi
$Av_1 = \lambda_1 v_1$
$\dots$
$Av_k = \lambda_k v_k \quad (1)$
in $v_1, \dots, v_k$ so neničelni vektorji. Z indukcijo po $j$ bomo pokazali, da je za vsak $j \le k$ množica $\{v_1, \dots, v_j\}$ linearno neodvisna.

**Baza indukcije:** Ker je $v_1 \neq 0$, je množica $\{v_1\}$ linearno neodvisna.

**Indukcijski korak:** Recimo, da je množica $\{v_1, \dots, v_j\}$ linearno neodvisna, kjer je $j < k$. Radi bi pokazali, da je potem tudi množica $\{v_1, \dots, v_{j+1}\}$ linearno neodvisna. Recimo, da je
$\alpha_1 v_1 + \dots + \alpha_j v_j + \alpha_{j+1} v_{j+1} = 0 \quad (2)$
Če (2) pomnožimo z leve z matriko $A$ in upoštevamo (1), dobimo
$\alpha_1 \lambda_1 v_1 + \dots + \alpha_j \lambda_j v_j + \alpha_{j+1} \lambda_{j+1} v_{j+1} = 0 \quad (3)$
Če od enačbe (3) odštejemo z $\lambda_{j+1}$ pomnoženo enačbo (2), dobimo
$\alpha_1 (\lambda_1 - \lambda_{j+1}) v_1 + \dots + \alpha_j (\lambda_j - \lambda_{j+1}) v_j = 0 \quad (4)$
Po indukcijski predpostavki odtod sledi, da je
$\alpha_1 (\lambda_1 - \lambda_{j+1}) = 0, \dots, \alpha_j (\lambda_j - \lambda_{j+1}) = 0 \quad (5)$
Ker so $\lambda_1, \dots, \lambda_k$ paroma različne, odtod sledi $\alpha_1 = 0, \dots, \alpha_j = 0$.
Iz enačbe (2) sedaj sledi, da je $\alpha_{j+1} v_{j+1} = 0$. Odtod sledi $\alpha_{j+1} = 0$, saj je $v_{j+1} \neq 0$.
Dokazali smo, da iz (2) sledi $\alpha_1 = \dots = \alpha_{j+1} = 0$, torej so $v_1, \dots, v_{j+1}$ linearno neodvisni.

**Posledica 1**

**Če je $A$ $n \times n$ matrika, ki ima $n$ paroma različnih lastnih vrednosti, potem ima $A$ diagonalizacijo.**

**Dokaz:** Ker ima $A$ $n$ paroma različnih lastnih vrednosti, ima po Trditvi 2 tudi $n$ linearno neodvisnih lastnih vektorjev. Odtod po Trditvi 1 sledi, da ima $A$ diagonalizacijo.

**Posledica 2**

**Vsota vseh lastnih podprostorov matrike je direktna.**

**Dokaz:** Naj bodo $\lambda_1, \dots, \lambda_k$ vse paroma različne lastne vrednosti matrike $A \in M_n(\mathbb{C})$. Pripadajoči lastni podprostori so potem $V_i = \text{Ker}(A - \lambda_i I)$ za $i = 1, \dots, k$. Trdimo, da je vsota podprostorov $V_1, \dots, V_k$ direktna. Treba je dokazati, da so poljubni vektorji $v_1 \in V_1, \dots, v_k \in V_k$, ki zadoščajo $v_1 + \dots + v_k = 0$, enaki nič. To sledi iz Trditve 2.


**Opomba**

Matrike z večkratnimi lastnimi vrednostmi včasih imajo diagonalizacijo (npr. $\begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix}$), včasih pa ne (npr. $\begin{pmatrix} 0 & 1 \\ 0 & 0 \end{pmatrix}$).
Izkaže se, da je to povezano z algebraično in geometrijsko večkratnostjo lastnih vrednosti. V prvem primeru sta obe večkratnosti enaki ($a(1) = g(1) = 2$), v drugem pa sta različni ($a(0) = 2$ in $g(0) = 1$).

**Lema**

**Za vsako lastno vrednost $\lambda$ je njena geometrijska večkratnost $g(\lambda)$ manjša ali enaka njeni algebraični večkratnosti $a(\lambda)$.**

**Dokaz:** Naj bo $v_1, \dots, v_m$ baza za $\text{Ker}(A - \lambda I)$ in naj bo $v_{m+1}, \dots, v_n$ njena dopolnitev do baze $\mathcal{B}$ za $\mathbb{C}^n$. Običajen račun potem pokaže, da je
$P^{-1}AP = \begin{pmatrix} \lambda I_m & B \\ 0 & C \end{pmatrix}$,
kjer je $P = [v_1 \ \dots \ v_m \ v_{m+1} \ \dots \ v_n]$ obrnljiva matrika. Sledi
$\det(A - xI_n) = \det(\lambda I_m - xI_m) \det(C - xI_{n-m}) = (\lambda - x)^m \det(C - xI_{n-m})$.
Ker $(\lambda - x)^m$ deli karakteristični polinom, je $a(\lambda) \ge m = g(\lambda)$.

**Trditev 3**

**Matrika $A$ ima diagonalizacijo natanko tedaj, ko se za vsako lastno vrednost $A$ njena geometrijska in algebraična večkratnost ujemata.**

**Dokaz:** Naj bodo $\lambda_1, \dots, \lambda_k$ vse paroma različne lastne vrednosti matrike $A$. Njen karakteristični polinom je $p_A(x) = (-1)^n (x - \lambda_1)^{n_1} \dots (x - \lambda_k)^{n_k}$, kjer je $n_i$ algebraična večkratnost za $\lambda_i$. Očitno je $n_1 + \dots + n_k = n$.
Geometrijska večkratnost za $\lambda_i$ je $m_i := \dim \text{Ker}(A - \lambda_i I)$.
Po Trditvi 1 ima matrika $A$ diagonalizacijo natanko tedaj, ko je $U = \mathbb{C}^n$, kjer je $U$ vsota vseh lastnih podprostorov matrike $A$. Po Posledici 2 je $\dim U = m_1 + \dots + m_k$. Torej ima matrika $A$ diagonalizacijo natanko tedaj, ko je $m_1 + \dots + m_k = n_1 + \dots + n_k$.
Ker je $m_i \le n_i$ za vsak $i$ (Lema), to velja natanko tedaj, ko je $m_i = n_i$ za vsak $i$.

**Trditev 4** *Nisem delal*

**Naj bodo $\lambda_1, \dots, \lambda_k$ vse paroma različne lastne vrednosti matrike $A$. Potem ima matrika $A$ diagonalizacijo natanko tedaj, ko je produkt matrik $A - \lambda_1 I, \dots, A - \lambda_k I$ enak ničelni matriki.**

**Dokaz:** Označimo $L_i = A - \lambda_i I$ za $i = 1, \dots, k$. Potrebovali bomo formulo
$\dim \text{Ker}(L_1 L_2 \dots L_k) \le \dim \text{Ker}(L_1) + \dim \text{Ker}(L_2) + \dots + \dim \text{Ker}(L_k) \quad (1)$.
Primer $k = 2$ formule (1) smo dokazali v prejšnjem poglavju. Za splošen $k$ formulo (1) dokažemo z indukcijo.
Če velja $L_1 L_2 \dots L_k = 0$, potem je $\text{Ker}(L_1 \dots L_k) = \mathbb{C}^n$, kjer je $n$ velikost matrike $A$, torej je $\dim \text{Ker}(L_1 \dots L_k) = n$.
Označimo z $m_i = \dim \text{Ker}(L_i)$ geometrijsko večkratnost $\lambda_i$. Iz formule (1) torej sledi $n \le m_1 + \dots + m_k$.
Naj bo $n_i$ algebraična večkratnost $\lambda_i$. Iz $n = n_1 + \dots + n_k$ in iz $m_i \le n_i$ sledi, da je $m_i = n_i$ za vsak $i$. Po Trditvi 3 ima torej matrika $A$ diagonalizacijo.

Dokažimo še drugo smer. Recimo, da ima matrika $A$ diagonalizacijo $A = PDP^{-1}$. S permutacijo diagonalnih elementov matrike $D$ dobimo matriko, ki ji je podobna. Zato lahko predpostavimo, da enake lastne vrednosti ležijo skupaj na diagonali $D$, se pravi, da je
$D = \begin{pmatrix} \lambda_1 I_{m_1} & & & \\ & \lambda_2 I_{m_2} & & \\ & & \ddots & \\ & & & \lambda_k I_{m_k} \end{pmatrix} \quad (2)$
(kjer so $\lambda_i$ na diagonali ponovljene $m_i$-krat).
Iz (2) sledi, da je $i$-ti diagonalni blok matrike $D - \lambda_i I$ enak $0$, torej je
$(D - \lambda_1 I)(D - \lambda_2 I) \dots (D - \lambda_k I) = 0 \quad (3)$.

Iz (3) izpeljemo

$P(D - \lambda_1 I)P^{-1} P(D - \lambda_2 I)P^{-1} \dots P(D - \lambda_k I)P^{-1} = 0 \quad (4)$

kjer je $P(D - \lambda_i I)P^{-1} = PDP^{-1} - \lambda_i I = A - \lambda_i I$

## 4. Minimalni polinom matrike

Označimo s $\mathbb{C}[x]$ množico vseh polinomov v $x$ s kompleksnimi koeficienti. Z $M_n(\mathbb{C})$ označimo množico vseh kompleksnih $n \times n$ matrik.

V polinom $p(x) = c_n x^n + c_{n-1} x^{n-1} + \dots + c_1 x + c_0 \in \mathbb{C}[x]$, bi radi namesto $x$ vstavili matriko $A \in M_n(\mathbb{C})$. Problem je v tem, ker so členi $c_n A^n, c_{n-1} A^{n-1}, \dots, c_1 A$ matrike, člen $c_0$ pa je skalar. Zato v $p(x)$ člen $c_0$ pomnožimo z $x^0 = 1$, v $p(A)$ pa ga pomnožimo z $A^0 := I$. Torej je
$$ p(A) := c_n A^n + c_{n-1} A^{n-1} + \dots + c_1 A + c_0 I $$

**Opomba:** V nadaljevanju bomo večkrat potrebovali, da iz $p(x) = p_1(x)p_2(x)$ sledi $p(A) = p_1(A)p_2(A)$. To ni povsem očitno, ampak je treba napraviti kratek račun.

### Definicija minimalnega polinoma

Polinom $m \in \mathbb{C}[x]$ je **minimalni polinom** matrike $A \in M_n(\mathbb{C})$, če velja:
1.  $m(A) = 0$,
2.  $m$ ima vodilni koeficient 1,
3.  med vsemi polinomi, ki zadoščajo (1) in (2), ima $m$ najnižjo stopnjo.

Prepričajmo se najprej, da je definicija smiselna.

**Trditev 1: (Obstoj in enoličnost minimalnega polinoma)**

Vsaka matrika $A$ ima natanko en minimalni polinom. Označimo ga z $m_A$.

**Dokaz bomo razbili v več korakov:**

**1. korak:** Konstruirajmo najprej tak polinom $p \in \mathbb{C}[x]$, ki zadošča $p(A) = 0$ in ki ima vodilni koeficient enak ena.
Očitno je $M_n(\mathbb{C})$ vektorski prostor nad $\mathbb{C}$ dimenzije $n^2$. Ker ima množica $\{I, A, A^2, \dots, A^{n^2}\}$ en element več od dimenzije, je linearno odvisna. Obstajajo torej taki $c_0, c_1, c_2, \dots, c_{n^2} \in \mathbb{C}$, od katerih je vsaj en neničeln, da velja $\sum_{i=0}^{n^2} c_i A^i = 0$. Polinom $p(x)$ dobimo tako, da polinom $\sum_{i=0}^{n^2} c_i x^i$ delimo z njegovim vodilnim koeficientom.

**2. korak:** Matrika $A$ ima vsaj en minimalni polinom.
Naj bo $\mathcal{M}$ množica vseh polinomov, ki zadoščajo točkam (1) in (2) iz definicije minimalnega polinoma. Po 1. koraku je množica $\mathcal{M}$ neprazna. Vzemimo v množici $\mathcal{M}$ polinom z najnižjo stopnjo. Tak polinom potem zadošča vsem trem točkam iz definicije minimalnega polinoma.

**3. korak:** Naj bo $m$ minimalni polinom matrike $A$ in naj bo $p$ tak polinom, ki zadošča $p(A) = 0$. Potem $m$ deli $p$.
Po izreku o deljenju z ostankom obstajata taka polinoma $k$ in $r$, da velja $p = km + r$ in $\deg r < \deg m$. Ker je $m(A) = 0$ in $p(A) = 0$, je tudi $r(A) = 0$. Če bi bil $r$ neničeln polinom, bi ga delili z vodilnim koeficientom in bi dobili tak polinom, ki zadošča točkam (1) in (2) iz definicije minimalnega polinoma in je nižje stopnje od $m$. To je v nasprotju s predpostavko, da $m$ zadošča točki (3) iz definicije minimalnega polinoma. Torej je $r$ ničeln polinom.

**4. korak:** Če sta $m_1$ in $m_2$ minimalna polinoma matrike $A$, potem je $m_1 = m_2$.
Ker je $m_2(A) = 0$, po 3. koraku $m_1$ deli $m_2$. Ker je $m_1(A) = 0$, po 3. koraku $m_2$ deli $m_1$. Torej obstaja taka konstanta $c \ne 0$, da je $m_2 = c m_1$. Ker imata oba polinoma vodilni koeficient enak 1, je $c = 1$.

### Trditev 2: (Cayley-Hamiltonov izrek)

Naj bo $p_A(x)$ karakteristični polinom matrike $A$. Potem velja $p_A(A) = 0$.


**Dokaz:**
Spomnimo se formule $B^{-1} = \frac{1}{\det B} \mathrm{adj}(B)$ za inverz matrike, kjer matriko $\mathrm{adj}(B)$ dobimo tako, da v matriki $B$ vsak element $b_{i,j}$ zamenjamo z $(-1)^{i+j} \det B_{i,j}$ (kjer je $B_{i,j}$ matrika $B$ s pobrisano $i$-to vrstico in $j$-tim stolpcem).
Če to formulo pomnožimo z $\det(B)B$ z leve, dobimo $\det(B)I = B \mathrm{adj}(B)$.
Sedaj vstavimo $B = A - xI$ in dobimo $p_A(x)I = (A - xI) \mathrm{adj}(A - xI)$.
Elementi matrike $\mathrm{adj}(A - xI)$ so polinomi v $x$ stopnje $\le n-1$. (So namreč determinante velikosti $n-1$, katerih elementi so polinomi stopnje $\le 1$.)
Zato lahko $\mathrm{adj}(A - xI)$ zapišemo kot $\mathrm{adj}(A - xI) = B_0 + xB_1 + \dots + x^{n-1}B_{n-1}$, kjer so $B_i \in M_n(\mathbb{C})$.
Prav tako $p_A(x) = c_0 + c_1 x + \dots + c_n x^n$, kjer $c_i \in \mathbb{C}$.
V enačbo $p_A(x)I = (A - xI) \mathrm{adj}(A - xI)$ vstavimo te izraze:
$(c_0 + c_1 x + \dots + c_n x^n)I = (A - xI)(B_0 + xB_1 + \dots + x^{n-1}B_{n-1})$.
Primerjajmo koeficiente pri potencah $x^i$, kjer $i = 0, 1, 2, \dots, n-1, n$:
$c_0 I = AB_0$
$c_1 I = AB_1 - B_0$
$c_2 I = AB_2 - B_1$
$\vdots$
$c_{n-1} I = AB_{n-1} - B_{n-2}$
$c_n I = -B_{n-1}$
Pomnožimo $i$-to enačbo z $A^i$ z leve in vse enačbe seštejmo:
$c_0 I + c_1 A + c_2 A^2 + \dots + c_{n-1} A^{n-1} + c_n A^n$
$= AB_0 + A(AB_1 - B_0) + A^2(AB_2 - B_1) + \dots + A^{n-1}(AB_{n-1} - B_{n-2}) + A^n(-B_{n-1})$.
Na desni strani odpravimo oklepaje in opazimo, da se vse pokrajša (teleskopska vsota):
$AB_0 - AB_0 + A^2B_1 - A^2B_1 + \dots + A^nB_{n-1} - A^nB_{n-1} = 0$.
Torej $p_A(A) = 0$.

Radi bi dokazali, da minimalni polinom matrike $A$ deli karakteristični polinom matrike $A$. Po 3. koraku dokaza Trditve 1, je dovolj dokazati, da $p_A(A) = 0$. Cayley-Hamiltonov izrek nam to potrjuje.

### Trditev 3

Vsaka lastna vrednost matrike $A$ je ničla minimalnega polinoma $m_A$.

**Dokaz:**
Naj bo $\lambda$ lastna vrednost matrike $A$ in naj bo $v$ pripadajoči lastni vektor ($v \ne 0$). Iz $Av = \lambda v$ s popolno indukcijo izpeljemo, da velja $A^k v = \lambda^k v$ za vsak $k$. Če namreč velja $A^{k-1}v = \lambda^{k-1}v$ za nek $k$, potem je
$A^k v = A(A^{k-1}v) = A(\lambda^{k-1}v) = \lambda^{k-1}(Av) = \lambda^{k-1}(\lambda v) = \lambda^k v$.
Recimo, da je minimalni polinom oblike $m_A(x) = \sum_{i=0}^r c_i x^i$. Potem velja:
$m_A(A)v = \left(\sum_{i=0}^r c_i A^i\right)v = \sum_{i=0}^r c_i (A^i v) = \sum_{i=0}^r c_i (\lambda^i v) = \left(\sum_{i=0}^r c_i \lambda^i\right)v = m_A(\lambda)v$.
Ker je $m_A(A) = 0$, je $m_A(A)v = 0$. Torej $m_A(\lambda)v = 0$. Ker je $v$ neničeln, odtod sledi $m_A(\lambda) = 0$.

### Zveza med minimalnim polinomom in obstojem diagonalizacije

**Trditev 4:**
Matrika ima diagonalizacijo natanko tedaj, ko njen minimalni polinom nima večkratnih ničel.

**Dokaz:**
Naj bodo $\lambda_1, \dots, \lambda_k$ vse paroma različne lastne vrednosti matrike $A$. Iz 3. razdelka vemo, da ima $A$ diagonalizacijo natanko tedaj, ko je produkt matrik $A - \lambda_i I$ enak nič. Označimo z $m(x)$ produkt polinomov $x - \lambda_i$, se pravi $m(x) = (x - \lambda_1)\dots(x - \lambda_k)$. Torej ima $A$ diagonalizacijo natanko tedaj, ko je $m(A) = 0$. Po 3. koraku v dokazu Trditve 1 velja, da $m(A) = 0$ natanko tedaj, ko minimalni polinom $m_A(x)$ deli polinom $m(x)$. Po Trditvi 3 velja to natanko tedaj, ko je $m_A(x) = m(x)$. To pa pomeni, da so vse ničle minimalnega polinoma enostavne.

*Če $m_A(x)$ deli $m(x)$ in imata oba polinoma iste korene, poleg tega pa je $m(x)$ produkt enostavnih faktorjev, potem mora tudi $m_A(x)$ imeti samo enostavne korene. Če bi imel $m_A(x)$ kakšen koren z večkratnostjo (npr. $(x-\lambda_i)^2$), potem $m(x)$ ne bi mogel biti le produkt $(x-\lambda_i)$, ampak bi moral imeti vsaj faktor $(x-\lambda_i)^2$, da bi ga $m_A(x)$ delil. Toda $m(x)$ je definiran kot produkt enostavnih faktorjev.
Ker sta oba polinoma monična, imata iste korene (vsakega z enostavno večkratnostjo), sta torej **identična**.
    $m_A(x) = (x - \lambda_1)\dots(x - \lambda_k) = m(x)$.*

## 5. Korenski podprostori

Naj bodo $\lambda_1, \dots, \lambda_k$ vse paroma različne lastne vrednosti matrike $A \in M_n(\mathbb{C})$. Vemo, da je karakteristični polinom matrike $A$ oblike $p_A(x) = (-1)^n (x - \lambda_1)^{n_1} \dots (x - \lambda_k)^{n_k}$, minimalni polinom matrike $A$ pa je oblike $m_A(x) = (x - \lambda_1)^{r_1} \dots (x - \lambda_k)^{r_k}$, kjer števila $r_1, \dots, r_k$ zadoščajo $1 \le r_i \le n_i$. Števila $r_i$ potrebujemo v definiciji korenskega podprostora:

### Definicija korenskih vektorjev in korenskega podprostora

Množica $\mathrm{Ker}(A - \lambda_i I)^{r_i}$ je vektorski podprostor v $\mathbb{C}^n$. Pravimo ji **korenski podprostor** matrike $A$ za lastno vrednost $\lambda_i$. Njenim neničelnim elementom pravimo **korenski vektorji** matrike $A$ za lastno vrednost $\lambda_i$.

Korenske podprostore matrike $A$ bomo potrebovali pri konstrukciji Jordanske kanonične forme matrike $A$ v naslednjem razdelku. Oglejmo si najprej nekaj njihovih osnovnih lastnosti.

### Izrek o korenskem razcepu

Naj bodo $A, \lambda_i, n_i$ in $r_i$ kot zgoraj.
1.  Velja $\mathrm{Ker}(A - \lambda_i I) \subset \mathrm{Ker}(A - \lambda_i I)^2 \subset \dots \subset \mathrm{Ker}(A - \lambda_i I)^{r_i} = \mathrm{Ker}(A - \lambda_i I)^{r_i+1} = \mathrm{Ker}(A - \lambda_i I)^{r_i+2} = \dots$, kjer je inkluzija stroga.
2.  $\dim \mathrm{Ker}(A - \lambda_i I)^{r_i} = n_i$, se pravi, da je dimenzija korenskega podprostora $A$ za $\lambda_i$ enaka algebraični večkratnosti $\lambda_i$.
3.  $\mathbb{C}^n = \bigoplus_{i=1}^k \mathrm{Ker}(A - \lambda_i I)^{r_i}$, kar pomeni, da za vsak $w \in \mathbb{C}^n$ obstajajo natanko določeni $w_i \in \mathrm{Ker}(A - \lambda_i I)^{r_i}$, ki zadoščajo $w = \sum_{i=1}^k w_i$.

Označimo z $W_i = \mathrm{Ker}(A - \lambda_i I)^{r_i}$ korenski podprostor $A$ za $\lambda_i$, z $V_i = \mathrm{Ker}(A - \lambda_i I)$ pa lastni podprostor $A$ za $\lambda_i$. Iz prve točke sledi, da je $V_i$ vsebovan v $W_i$ in da sta enaka natanko tedaj, ko je $r_i = 1$.

**Izrek o korenskem razcepu nam pove, da imamo naslednjo situacijo:**
Prostor $\mathbb{C}^n$ se razdeli na direktno vsoto korenskih podprostorov, vsak izmed njih pa vsebuje "ugnjezdene" podprostore (npr. $\mathrm{Ker}(A-\lambda_i I) \subset \mathrm{Ker}(A-\lambda_i I)^2 \subset \dots$).
Velike škatle $\mathrm{Ker}(A - \lambda_i I)^{r_i}$ so korenski podprostori matrike $A$. Njihova vsota je $\mathbb{C}^n$. Male škatle $\mathrm{Ker}(A - \lambda_i I)$ so lastni podprostori matrike $A$.

### Priprave na dokaz izreka (o korenskem razcepu)

V dokazu izreka bomo potrebovali pojem invariantnega podprostora.

**Definicija invariantnega podprostora:**
Vektorski podprostor $U$ v $\mathbb{C}^n$ je **invarianten** za matriko $A \in M_n(\mathbb{C})$, če za vsak $u \in U$ velja $Au \in U$.

**Primeri invariantnih podprostorov matrike $A$:**
*   Trivialni podprostor $\{0\}$.
*   Lastni podprostori matrike $A$.
*   Korenski podprostori matrike $A$.
*   Presek invariantnih podprostorov za $A$ je invarianten podprostor za $A$.

Dokažimo invariantnost korenskega podprostora $W_i = \mathrm{Ker}(A - \lambda_i I)^{r_i}$.
Za vsak $w \in W_i$ velja $(A - \lambda_i I)^{r_i}w = 0$. Če to pomnožimo z $A$ z leve, dobimo $A(A - \lambda_i I)^{r_i}w = A \cdot 0 = 0$. Ker je $A(A - \lambda_i I)^{r_i} = (A - \lambda_i I)^{r_i}A$ (matrika $A$ komutira s $A - \lambda_i I$), odtod sledi $(A - \lambda_i I)^{r_i}Aw = 0$. Torej $Aw \in W_i$. Dokaz ostalih točk je še lažji.

### Trditev 1 (vsak invarianten podprostor vsebuje lastni vektor)

Vsak netrivialen invarianten podprostor za matriko $A$ vsebuje vsaj en lastni vektor matrike $A$.

**Dokaz:**
Naj bo $U$ netrivialen invarianten podprostor za $A$. Ker je $U \ne \{0\}$, ima $U$ bazo, recimo $\mathcal{B} = \{u_1, \dots, u_m\}$. Ker je $U$ invarianten za $A$, lahko definiramo linearno preslikavo $L: U \to U$ z $L(u) = Au$.
Naj bo $\begin{bmatrix} x_1 \\ \vdots \\ x_m \end{bmatrix}$ lastni vektor matrike $[L]_{\mathcal{B}}$ za lastno vrednost $\lambda$. Očitno $v := x_1 u_1 + \dots + x_m u_m$ pripada $U$. Pokažimo, da je $v$ lastni vektor za $A$.
Velja namreč $[Lv]_{\mathcal{B}} = [L]_{\mathcal{B}}[v]_{\mathcal{B}} = \lambda[v]_{\mathcal{B}} = [\lambda v]_{\mathcal{B}}$. Torej je $Lv = \lambda v$.

### Dokaz točke (3) (direktna vsota korenskih podprostorov)

Dokaz točke (3) v izreku bomo razdelili na več trditev.

**Trditev 2:**
Presek dveh različnih korenskih podprostorov matrike $A$ je trivialen.

**Dokaz:**
Ker sta korenska podprostora $W_i$ in $W_j$ invariantna za $A$, je invarianten za $A$ tudi njun presek $W_i \cap W_j$. Če je njun presek netrivialen, potem po Trditvi 1 vsebuje lastni vektor za $A$. Torej je $Av = \lambda v$ za nek neničeln $v \in W_i \cap W_j$. Odtod sledi, da za vsak polinom $p(x)$ velja $p(A)v = p(\lambda)v$.
Če vzamemo $p(x) = (x - \lambda_i)^{r_i}$, dobimo $0 = (A - \lambda_i I)^{r_i}v = (\lambda - \lambda_i)^{r_i}v$, odkoder sledi $\lambda = \lambda_i$ (ker $v \ne 0$).
Če pa vzamemo $p(x) = (x - \lambda_j)^{r_j}$, potem dobimo $0 = (A - \lambda_j I)^{r_j}v = (\lambda - \lambda_j)^{r_j}v$, odkoder sledi $\lambda = \lambda_j$.
Torej je $\lambda_i = \lambda_j$. Odtod sledi $W_i = W_j$, kar je v nasprotju s predpostavko.

**Trditev 3:**
Če vektorji $w_1 \in W_1, \dots, w_k \in W_k$ zadoščajo $w_1 + \dots + w_k = 0$, potem velja $w_1 = \dots = w_k = 0$.

**Dokaz:** Dokazali bomo, da za vsak $i = 1, \dots, k$ velja naslednja trditev:
$(T_i)$ Če vektorji $w_1 \in W_1, \dots, w_i \in W_i$ zadoščajo $w_1 + \dots + w_i = 0$, potem velja $w_1 = \dots = w_i = 0$.
Baza indukcije: Trditev $(T_1)$ je očitna (če $w_1=0$, potem $w_1=0$).
Indukcijski korak: Recimo, da velja trditev $(T_i)$, kjer $i < k$. Radi bi dokazali trditev $(T_{i+1})$. Vzemimo take vektorje $w_1 \in W_1, \dots, w_i \in W_i, w_{i+1} \in W_{i+1}$, da velja $w_1 + \dots + w_i + w_{i+1} = 0$.
Če to enačbo pomnožimo z $(A - \lambda_{i+1}I)^{r_{i+1}}$ z leve, dobimo:
$(A - \lambda_{i+1}I)^{r_{i+1}}w_1 + \dots + (A - \lambda_{i+1}I)^{r_{i+1}}w_i + (A - \lambda_{i+1}I)^{r_{i+1}}w_{i+1} = 0$.
Ker $w_{i+1} \in W_{i+1} = \mathrm{Ker}(A - \lambda_{i+1}I)^{r_{i+1}}$, je $(A - \lambda_{i+1}I)^{r_{i+1}}w_{i+1} = 0$.
Označimo $w_j' := (A - \lambda_{i+1}I)^{r_{i+1}}w_j$.
Ker je vsak korenski podprostor $W_j$ invarianten, in ker vsebuje $w_j$, vsebuje tudi $w_j'$.
Iz $w_1' + \dots + w_i' = 0$ torej po indukcijski predpostavki sledi, da velja $w_1' = \dots = w_i' = 0$.
To pomeni, da za vsak $j \in \{1, \dots, i\}$ velja $(A - \lambda_{i+1}I)^{r_{i+1}}w_j = 0$.
Ker $w_j \in W_j = \mathrm{Ker}(A - \lambda_jI)^{r_j}$, to pomeni, da $w_j \in \mathrm{Ker}(A - \lambda_jI)^{r_j} \cap \mathrm{Ker}(A - \lambda_{i+1}I)^{r_{i+1}}$.
Po Trditvi 2 je presek dveh različnih korenskih podprostorov trivialen. Ker $\lambda_j \ne \lambda_{i+1}$ za $j \in \{1, \dots, i\}$, sledi, da je $\mathrm{Ker}(A - \lambda_jI)^{r_j} \cap \mathrm{Ker}(A - \lambda_{i+1}I)^{r_{i+1}} = \{0\}$.
Odtod sledi $w_1 = \dots = w_i = 0$.
Ker $w_1 + \dots + w_i + w_{i+1} = 0$, sledi še $w_{i+1} = 0$.

**Trditev 4:**
Vsota vseh korenskih podprostorov matrike $A$ je enaka $\mathbb{C}^n$.

**Dokaz:**
Če v oceno $n(L_1 \dots L_k) \le n(L_1) + \dots + n(L_k)$ iz prejšnjega poglavja (o rangu in ničelnosti produkta operatorjev), vstavimo $L_i = (A - \lambda_i I)^{r_i}$ in upoštevamo $L_1 \dots L_k = m_A(A) = 0$ ter $n(L_i) = \dim \mathrm{Ker}(A - \lambda_i I)^{r_i} = \dim W_i$, dobimo, da velja ocena $n \le \dim W_1 + \dots + \dim W_k$.
Po opombi, da je $\dim(W_1 + \dots + W_k) = \dim W_1 + \dots + \dim W_k$ (zaradi direktne vsote, kar sledi iz Trditve 3), ker so preseki trivialni.
Ker je torej $\dim(W_1 + \dots + W_k) \ge n$, velja $W_1 + \dots + W_k = \mathbb{C}^n$.
Opomba: Trditvi 3 in 4 nam dasta ravno točko (3) v izreku o korenskem razcepu.

### Dokaz točke (2) ($\dim W_i = n_i$)

Označimo $t_i := \dim W_i$ za vsak $i = 1, \dots, k$. Radi bi pokazali, da je $t_i = n_i$.
Naj bo $\mathcal{B}_i = \{v_{i,1}, \dots, v_{i,t_i}\}$ baza za $W_i$. Ker je podprostor $W_i$ invarianten za $A$, obstajajo taka števila $\alpha_{i,j,j'}$ da velja $Av_{i,j} = \sum_{j'=1}^{t_i} \alpha_{i,j,j'}v_{i,j'}$.
V matrični obliki to zapišemo kot $AP_i = P_i A_i$, kjer je $P_i = \begin{bmatrix} v_{i,1} & \dots & v_{i,t_i} \end{bmatrix}$ in $A_i = [\alpha_{i,j,j'}]$.
Odtod sledi, da je matrika $P := \begin{bmatrix} P_1 & \dots & P_k \end{bmatrix}$ obrnljiva, ker je (po že dokazani točki (3) v izreku) unija baz $\mathcal{B}_i$ baza za $\mathbb{C}^n$. Označimo z $A'$ bločno diagonalno matriko iz $A_i$-jev. Po formuli $A_i$ je $A' = P^{-1}AP$, torej imata $A$ in $A'$ enak karakteristični polinom.
$ \det(A - xI) = \det(A_1 - xI) \dots \det(A_k - xI) $.
Pokažimo, da je $\lambda_i$ edina lastna vrednost matrike $A_i$. Potem je $\det(A_i - xI) = (\lambda_i - x)^{t_i}$. To vstavimo v formulo in dobimo $n_i = t_i$.
Naj bo $\mu_j$ poljubna lastna vrednost matrike $A_i$ in naj bo $u_j \in \mathbb{C}^{t_i}$ pripadajoči lastni vektor. Potem je $A_i u_j = \mu_j u_j$.
$A(P_iu_j) = (AP_i)u_j = (P_iA_i)u_j = P_i(A_iu_j) = P_i(\mu_j u_j) = \mu_j (P_iu_j)$.
Ker je $P_iu_j$ linearna kombinacija stolpcev $P_i$ in ker so stolpci $P_i$ v $W_i$, je $P_iu_j \in W_i$. Poleg tega je $P_iu_j \ne 0$, ker je $u_j \ne 0$ in ker so stolpci $P_i$ linearno neodvisni. Po definiciji $W_i$ je $(A - \lambda_i I)^{r_i} (P_iu_j) = 0$. Iz formule zgoraj sledi, da je $(A - \lambda_i I)^{r_i} (P_iu_j) = (\mu_j - \lambda_i)^{r_i} (P_iu_j)$. Torej je $\mu_j = \lambda_i$.

### Dokaz točke (1) (inkuzije korenskih podprostorov)

Dokaz točke (1) v izreku bomo razdelili v več korakov.

**1. korak:** Če je $m \le m'$, potem velja $\mathrm{Ker}(A - \lambda_i I)^m \subseteq \mathrm{Ker}(A - \lambda_i I)^{m'}$.
Za vsak $v \in \mathrm{Ker}(A - \lambda_i I)^m$ velja $(A - \lambda_i I)^mv = 0$. Pomnožimo to z leve z $(A - \lambda_i I)^{m'-m}$ in dobimo $(A - \lambda_i I)^{m'}v = 0$. Torej je $v \in \mathrm{Ker}(A - \lambda_i I)^{m'}$.

**2. korak:** Za vsak $m < r_i$ je $\mathrm{Ker}(A - \lambda_i I)^m \ne \mathrm{Ker}(A - \lambda_i I)^{m+1}$.
Označimo $W_i' := \mathrm{Ker}(A - \lambda_i I)^m$ in $n_i' = \dim W_i'$. Po 1. koraku je $W_i \subseteq W_i'$, zato je $n_i \le n_i'$. Kot v dokazu Trditve 3 vidimo, da za poljubne $w_1 \in W_1, \dots, w_k \in W_k$ (kjer so to korenski podprostori za $A$ in $\lambda_j$ kjer $j \ne i$) ki zadoščajo $w_1 + \dots + w_k = 0$, velja $w_1 = \dots = w_k = 0$. Kot v opombi za Trditvijo 3 odtod sledi, da je $n_1 + \dots + n_k = n$. Odtod in iz $n_i \le n_i'$ sledi, da je $n_i' = n_i$ za vsak $i$. Torej je $W_i' = W_i$ za vsak $i$.

**3. korak:** Za vsak $i$ je $\mathrm{Ker}(A - \lambda_i I)^{r_i-1} \ne \mathrm{Ker}(A - \lambda_i I)^{r_i}$.
Če bi za nek $i$ veljal enačaj, potem bomo pokazali, da bi polinom $m_i(x) := m_A(x)/(x - \lambda_i)$ zadoščal $m_i(A) = 0$, kar bi bilo v nasprotju z definicijo minimalnega polinoma (ker bi imel nižjo stopnjo). Vzemimo poljuben $w \in \mathbb{C}^n$. Po Trditvi 4 obstajajo taki $w_j \in W_j$, da velja $w = \sum_{j=1}^k w_j$.
Za vsak $j \ne i$ velja $w_j \in W_j = \mathrm{Ker}(A - \lambda_jI)^{r_j}$. To pomeni, da $m_i(A)w_j = \frac{m_A(A)}{A - \lambda_i I}w_j = \frac{0}{A-\lambda_i I} w_j = 0$.
Za $j=i$: $w_i \in W_i = \mathrm{Ker}(A - \lambda_iI)^{r_i}$. Predpostavka, da $\mathrm{Ker}(A - \lambda_iI)^{r_i-1} = \mathrm{Ker}(A - \lambda_iI)^{r_i}$, pomeni $w_i \in \mathrm{Ker}(A - \lambda_iI)^{r_i-1}$. Torej $(A-\lambda_i I)^{r_i-1}w_i = 0$.
To pomeni, da $m_i(A)w_i = (x-\lambda_1)^{r_1}\dots(x-\lambda_i)^{r_i-1}\dots(x-\lambda_k)^{r_k} w_i = 0$.
Odtod sledi $m_i(A)w = 0$. Ker je to res za vsak $w \in \mathbb{C}^n$, je $m_i(A) = 0$.

**4. korak:** Če velja $\mathrm{Ker}(A - \lambda_i I)^m \ne \mathrm{Ker}(A - \lambda_i I)^{m+1}$ za nek $m \ge 1$ in nek $i = 1, \dots, k$, potem velja tudi $\mathrm{Ker}(A - \lambda_i I)^{m-1} \ne \mathrm{Ker}(A - \lambda_i I)^m$.
Predpostavimo, da velja $\mathrm{Ker}(A - \lambda_i I)^{m-1} = \mathrm{Ker}(A - \lambda_i I)^m$.
Dokazujemo, da velja $\mathrm{Ker}(A - \lambda_i I)^m = \mathrm{Ker}(A - \lambda_i I)^{m+1}$. Vzemimo poljuben $v \in \mathrm{Ker}(A - \lambda_i I)^{m+1}$. Potem $(A - \lambda_i I)v \in \mathrm{Ker}(A - \lambda_i I)^m$. Torej $(A - \lambda_i I)v \in \mathrm{Ker}(A - \lambda_i I)^{m-1}$ po predpostavki. Odtod sledi, da $v \in \mathrm{Ker}(A - \lambda_i I)^m$. Torej je $\mathrm{Ker}(A - \lambda_i I)^m \supseteq \mathrm{Ker}(A - \lambda_i I)^{m+1}$. Obratna inkluzija sledi iz 1. koraka. To je v protislovju s predpostavko.