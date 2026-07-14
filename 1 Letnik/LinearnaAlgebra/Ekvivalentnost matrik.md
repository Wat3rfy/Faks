

#### Stolpčna in vrstična ekvivalentnost matrik

Pravimo, da sta matriki $A$ in $B$ **stolpčno ekvivalentni**, če lahko dobimo eno iz druge s pomočjo elementarnih stolpčnih transformacij, se pravi, če obstaja taka obrnljiva matrika $Q$, da je $B = AQ$.
Pravimo, da sta matriki $A$ in $B$ **vrstično ekvivalentni**, če lahko dobimo eno iz druge s pomočjo elementarnih vrstičnih transformacij, se pravi, če obstaja taka obrnljiva matrika $P$, da je $B = PA$.

**Trditev 7**
Naj bosta $A$ in $B$ $m \times n$ matriki nad poljem $F$.
1. Če sta $A$ in $B$ stolpčno ekvivalentni, potem imata enak stolpčni prostor in enako sliko. Imata tudi enak rang in enako ničnost.
2. Če sta $A$ in $B$ vrstično ekvivalentni, potem imata enak vrstični prostor in enako jedro. Imata tudi enako ničnost in enak rang.

**Dokaz:**
1. Če sta $A$ in $B$ stolpčno ekvivalentni, potem obstaja taka obrnljiva matrika $Q$, da je $B = AQ$. Pokažimo najprej, da velja $\text{Im } AQ = \text{Im } A$. Za vsak $v \in F^n$ so ekvivalentne trditve: (a) $v \in \text{Im } AQ$, (b) $v = AQu$ za nek $u \in F^n$, (c) $v = Au'$ za nek $u' \in F^n$, (d) $v \in \text{Im } A$. Ekvivalentnost med (b) in (c) sledi iz obrnljivosti matrike $Q$.
   Iz $\text{Im } A = \text{Im } B$ sledi $r(A) = \text{dim Im } A = \text{dim Im } B = r(B)$. Po osnovni formuli odtod sledi $n(A) = n - r(A) = n - r(B) = n(B)$.
2. Če sta matriki $A$ in $B$ vrstično ekvivalentni, potem obstaja taka obrnljiva matrika $P$, da velja $B = PA$. Pokažimo, da je $\text{Ker } PA = \text{Ker } A$. Za vsak $v \in F^n$ je $Av = 0$ ekvivalentno s $PAv = 0$ zaradi obrnljivosti matrike $P$.
   Iz $\text{Ker } A = \text{Ker } B$ sledi $n(A) = \text{dim Ker } A = \text{dim Ker } B = n(B)$. Po osnovni formuli je torej $r(A) = n - n(A) = n - n(B) = r(B)$.

**Opomba:** Poglejmo si, kakšna je zveza med $\text{Ker } A$ in $\text{Row } A$. Očitno je vektor iz $F^n$ v $\text{Ker } A$ natanko tedaj, ko je "pravokoten" na vse vrstice matrike $A$, se pravi, natanko tedaj, ko je "pravokoten" na $\text{Row } A$. Učeno se temu reče, da je $\text{Ker } A$ "ortogonalni komplement" od $\text{Im } A^T = (\text{Row } A)^T$.

#### Ekvivalentnost matrik

**Definicija**
Matriki $A$ in $B$ sta **ekvivalentni** (oznaka $A \sim B$) natanko tedaj, ko obstajata taki obrnljivi matriki $P$ in $Q$, da velja $B = PAQ$.
**Opomba:** Dve matriki sta ekvivalentni natanko tedaj ko lahko dobimo eno iz druge s pomočjo elementarnih vrstičnih in stolpčnih transformacij.

**Trditev 8**
Ekvivalentnost matrik je ekvivalenčna relacija.
**Dokaz:** Ekvivalentnost matrik $A$ in $B$ označimo z $A \sim B$. Dokažimo najprej $A \sim A$. To sledi iz $A = I_m A I_n$ in obrnljivosti matrik $I_m$ in $I_n$.
Če je $A \sim B$, potem je $B = PAQ$ za obrnljivi matriki $P, Q$. Odtod sledi $A = P^{-1}BQ^{-1}$, kjer sta tudi $P^{-1}, Q^{-1}$ obrnljivi. Torej je $B \sim A$.
Če je $A \sim B$ in $B \sim C$, potem je $B = P_1 A Q_1$ in $C = P_2 B Q_2$ za neke obrnljive matrike $P_1, Q_1, P_2, Q_2$. Odtod sledi, da je $C = P_2 P_1 A Q_1 Q_2$ in da sta matriki $P_2 P_1$ in $Q_1 Q_2$ obrnljivi. Torej je $A \sim C$.

**Primer**
Naj bo $L: U \to V$ linearna preslikava, $\mathcal{B}, \mathcal{B}'$ bazi za $U$ in $\mathcal{C}, \mathcal{C}'$ bazi za $V$. Potem sta matriki $[L]_{\mathcal{C} \leftarrow \mathcal{B}}$ in $[L]_{\mathcal{C}' \leftarrow \mathcal{B}'}$ ekvivalentni. Velja namreč
$[L]_{\mathcal{C}' \leftarrow \mathcal{B}'} = P_{\mathcal{C}' \leftarrow \mathcal{C}} [L]_{\mathcal{C} \leftarrow \mathcal{B}} P_{\mathcal{B} \leftarrow \mathcal{B}'}$
in matriki $P_{\mathcal{C}' \leftarrow \mathcal{C}}$ ter $P_{\mathcal{B} \leftarrow \mathcal{B}'}$ sta obrnljivi.
**Opomba:** Velja tudi obratno. Če sta matriki $A$ in $A'$ ekvivalentni, potem obstaja taka linearna preslikava $L: U \to V$ in take baze $\mathcal{B}, \mathcal{B}'$ za $U$ in $\mathcal{C}, \mathcal{C}'$ za $V$, da je $[L]_{\mathcal{C} \leftarrow \mathcal{B}} = A$ in $[L]_{\mathcal{C}' \leftarrow \mathcal{B}'} = A'$.
**Dokaz:** Recimo, da je $A' = PAQ$, kjer sta $P$ in $Q$ obrnljivi matriki. Naj bo $U = F^n$ in $V = F^m$ in naj bo $L = L_A$, se pravi linearna preslikava, ki vektor množi z matriko $A$. Naj bo $\mathcal{B}$ standardna baza za $F^n$ in $\mathcal{C}$ standardna baza za $F^m$. Potem velja $[L]_{\mathcal{C} \leftarrow \mathcal{B}} = A$. Naj bodo $\mathcal{B}'$ stolpci matrike $Q^{-1}$ in naj bodo $\mathcal{C}'$ stolpci matrike $P^{-1}$. Potem velja $P_{\mathcal{C}' \leftarrow \mathcal{C}} = P$ in $P_{\mathcal{B} \leftarrow \mathcal{B}'} = Q$. Torej je $[L]_{\mathcal{C}' \leftarrow \mathcal{B}'} = P_{\mathcal{C}' \leftarrow \mathcal{C}} [L]_{\mathcal{C} \leftarrow \mathcal{B}} P_{\mathcal{B} \leftarrow \mathcal{B}'} = PAQ = A'$.

**Trditev 9**
Vsaka matrika ranga $r$ je ekvivalentna matriki $\begin{pmatrix} I_r & 0 \\ 0 & 0 \end{pmatrix}$.
**Dokaz:** Naj bo $A$ $m \times n$ matrika nad $F$. Po Posledici 1 obstajata taka baza $\mathcal{B}$ za $F^n$ in taka baza $\mathcal{C}$ za $F^m$, da velja
$[L_A]_{\mathcal{C} \leftarrow \mathcal{B}} = \begin{pmatrix} I_r & 0 \\ 0 & 0 \end{pmatrix}$.
Naj bosta $S_n$ in $S_m$ standardni bazi za $F^n$ in $F^m$. Potem je
$A = [L_A]_{S_m \leftarrow S_n} = P_{S_m \leftarrow \mathcal{C}} [L_A]_{\mathcal{C} \leftarrow \mathcal{B}} P_{\mathcal{B} \leftarrow S_n} = P_{S_m \leftarrow \mathcal{C}} \begin{pmatrix} I_r & 0 \\ 0 & 0 \end{pmatrix} P_{\mathcal{B} \leftarrow S_n}$
kjer sta $P_{S_m \leftarrow \mathcal{C}}$ in $P_{\mathcal{B} \leftarrow S_n}$ obrnljivi matriki. Torej je $A \sim \begin{pmatrix} I_r & 0 \\ 0 & 0 \end{pmatrix}$.
**Opomba:** Bolj računski dokaz poteka takole. Najprej matriko $A$ s pomočjo elementarnih vrstičnih transformacij prevedemo v reducirano vrstično stopničasto formo $R$. Potem matriko $R$ s pomočjo elementarnih stolpčnih transformacij prevedemo v želeno obliko.

**Izrek 2 - Karakterizacija ekvivalentnosti matrik**
Dve matriki sta ekvivalentni natanko tedaj, ko imata enako velikost in enak rang.
**Dokaz:**
* Recimo, da sta $A$ in $B$ ekvivalentni matriki. Potem obstajata taki obrnljivi matriki $P$ in $Q$, da velja $B = PAQ$. Ker so vse obrnljive matrike kvadratne, je matrika $PAQ$ enake velikosti kot matrika $A$. Torej sta $A$ in $B$ enake velikosti. Po Trditvi 7 velja $r(PAQ) = r(PA) = r(A)$. Torej imata $A$ in $B$ enak rang.
* Recimo sedaj, da imata matriki $A$ in $B$ enako velikost $m \times n$ in enak rang $r$. Po Trditvi 9 sta tako $A$ kot $B$ ekvivalentni $m \times n$ matriki $\begin{pmatrix} I_r & 0 \\ 0 & 0 \end{pmatrix}$. Odtod po Trditvi 8 sledi, da sta $A$ in $B$ ekvivalentni.

#### Enakost stolpčnega in vrstičnega ranga

Rangu matrike $A$ pravimo tudi **stolpčni rang** matrike $A$, ker je enak maksimalnemu številu linearno neodvisnih stolpcev matrike $A$.
Rangu matrike $A^T$ pravimo tudi **vrstični rang** matrike $A$, ker je enak maksimalnemu številu linearno neodvisnih vrstic matrike $A$.
Radi bi pokazali, da sta stolčni in vrstični rang matrike $A$ enaka.

**Izrek 3**
Za vsako matriko $A$ je $r(A) = r(A^T)$.
**Dokaz:** Če je $A$ $m \times n$ matrika ranga $r$, potem po Trditvi 9 obstajata taki obrnljivi matriki $P$ in $Q$, da velja
$A = P \begin{pmatrix} I_r & 0 \\ 0 & 0 \end{pmatrix} Q$.
Odtod sledi
$A^T = Q^T \begin{pmatrix} I_r & 0 \\ 0 & 0 \end{pmatrix}^T P^T = Q^T \begin{pmatrix} I_r & 0 \\ 0 & 0 \end{pmatrix} P^T$.
Ker sta $P$ in $Q$ obrnljivi matriki, sta tudi $P^T$ in $Q^T$ obrnljivi. Po Trditvi 7 odtod sledi
$r(A^T) = r\left(Q^T \begin{pmatrix} I_r & 0 \\ 0 & 0 \end{pmatrix} P^T\right) = r\left(\begin{pmatrix} I_r & 0 \\ 0 & 0 \end{pmatrix}\right) = r$.
Torej je
$r(A) = r = r(A^T)$.
**Opomba:** Matrika $\begin{pmatrix} I_r & 0 \\ 0 & 0 \end{pmatrix}$ je velikosti $m \times n$, matrika $\begin{pmatrix} I_r & 0 \\ 0 & 0 \end{pmatrix}^T$ pa je velikosti $n \times m$. Imata pa obe enak rang $r$.


#### Podobnost kvadratnih matrik

**Definicija podobnosti matrik**
Kvadratni matriki $A$ in $B$ sta **podobni**, če obstaja taka obrnljiva matrika $P$, da velja $B = PAP^{-1}$.

**Trditev**
Podobnost matrik je ekvivalenčna relacija.
**Dokaz:**
* Ker je $A = IAI^{-1}$, kjer je $I$ identična matrika, je $A$ podobna $A$.
* Če je matrika $A$ podobna matriki $B$, potem je $B = PAP^{-1}$ za neko obrnljivo matriko $P$. Odtod sledi, da je $A = P^{-1}BP = P^{-1}B(P^{-1})^{-1}$ in da je matrika $P^{-1}$ obrnljiva. Torej je tudi matrika $B$ podobna matriki $A$.
* Če je matrika $A$ podobna matriki $B$ in če je matrika $B$ podobna matriki $C$, potem velja $B = PAP^{-1}$ in $C = QBQ^{-1}$ za obrnljivi matriki $P$ in $Q$. Odtod sledi $C = Q(PAP^{-1})Q^{-1} = (QP)A(P^{-1}Q^{-1}) = (QP)A(QP)^{-1}$ in da je matrika $QP$ obrnljiva. Torej je matrika $A$ podobna matriki $C$.

**Opomba:** Iz podobnosti sledi ekvivalentnost matrik, obratno pa ni res.

**Primer: Podobnost ni ekvivalentnost**
Matriki $A = \begin{pmatrix} 1 & 0 \\ 0 & 0 \end{pmatrix}$ in $B = \begin{pmatrix} 0 & 1 \\ 0 & 0 \end{pmatrix}$ sta ekvivalentni, ker imata enako velikost in enak rang. Če bi bili matriki $A$ in $B$ podobni, potem bi obstajala taka obrnljiva matrika $P$, da bi veljalo $B = PAP^{-1}$. Odtod bi sledilo
$\begin{pmatrix} 0 & 1 \\ 0 & 0 \end{pmatrix} = \begin{pmatrix} x & y \\ u & v \end{pmatrix} \begin{pmatrix} 1 & 0 \\ 0 & 0 \end{pmatrix} \begin{pmatrix} x & y \\ u & v \end{pmatrix}^{-1}$, kjer $P = \begin{pmatrix} x & y \\ u & v \end{pmatrix}$.
Z množenjem matrik bi dobili
$\begin{pmatrix} x & 0 \\ u & 0 \end{pmatrix} = \begin{pmatrix} 0 & 1 \\ 0 & 0 \end{pmatrix} \begin{pmatrix} x & y \\ u & v \end{pmatrix} = \begin{pmatrix} u & v \\ 0 & 0 \end{pmatrix}$.
Odtod pa bi sledilo $u=x=v=0$. To bi bilo protislovje s predpostavko, da je matrika $P$ obrnljiva.

**Primer podobnih matrik**
Naj bo $L: V \to V$ linearna preslikava in naj bosta $\mathcal{B}$ in $\mathcal{B}'$ bazi vektorskega prostora $V$. Potem sta matriki $[L]_{\mathcal{B} \leftarrow \mathcal{B}}$ in $[L]_{\mathcal{B}' \leftarrow \mathcal{B}'}$ podobni, ker velja
$[L]_{\mathcal{B}' \leftarrow \mathcal{B}'} = P_{\mathcal{B}' \leftarrow \mathcal{B}} [L]_{\mathcal{B} \leftarrow \mathcal{B}} P_{\mathcal{B} \leftarrow \mathcal{B}'} = P_{\mathcal{B}' \leftarrow \mathcal{B}} [L]_{\mathcal{B} \leftarrow \mathcal{B}} (P_{\mathcal{B}' \leftarrow \mathcal{B}})^{-1}$
kjer je $P_{\mathcal{B}' \leftarrow \mathcal{B}}$ obrnljiva matrika.
**Opomba:** Velja tudi obratno. Če sta kvadratni matriki $A$ in $A'$ podobni, potem obstaja taka linearna preslikava $L: V \to V$ in taki bazi $\mathcal{B}$ in $\mathcal{B}'$ za $V$, da velja $[L]_{\mathcal{B} \leftarrow \mathcal{B}} = A$ in $[L]_{\mathcal{B}' \leftarrow \mathcal{B}'} = A'$.

**Trditev**
Podobni matriki imata enako determinanto.
**Dokaz:** $\det(PAP^{-1}) = \det(P) \det(A) \det(P^{-1}) = \det(A) \det(P) \det(P^{-1}) = \det(A) \det(PP^{-1}) = \det(A) \det(I) = \det(A)$.
**Opomba:** Odtod sledi, da je za vsako linearno preslikavo $L: V \to V$ vrednost izraza $\det([L]_{\mathcal{B} \leftarrow \mathcal{B}})$ neodvisna od izbire baze $\mathcal{B}$. To vrednost vzamemo za definicijo $\det L$.

**Primer**
Naj bo $A$ kvadratna $n \times n$ matrika nad $F$. Recimo, da obstaja tak vektor $v \in F^n$, da so vektorji $v, Av, \dots, A^{n-1}v$ linearno neodvisni (=baza). Razvijmo vektor $A^n v$ po tej bazi: $A^n v = \alpha_0 v + \alpha_1 Av + \dots + \alpha_{n-1} A^{n-1}v$. Trdimo, da je $A = PBP^{-1}$, kjer je
$B = \begin{pmatrix} 0 & 0 & \dots & 0 & \alpha_0 \\ 1 & 0 & \dots & 0 & \alpha_1 \\ 0 & 1 & \dots & 0 & \alpha_2 \\ \vdots & \vdots & \ddots & \vdots & \vdots \\ 0 & 0 & \dots & 1 & \alpha_{n-1} \end{pmatrix}$
in je $P = [v \quad Av \quad \dots \quad A^{n-2}v \quad A^{n-1}v]$ obrnljiva matrika. To sledi iz
$AP = [Av \quad A^2v \quad \dots \quad A^{n-1}v \quad A^nv]$
$= [Av \quad A^2v \quad \dots \quad A^{n-1}v \quad \alpha_0 v + \alpha_1 Av + \dots + \alpha_{n-1} A^{n-1}v] = PB$.
**Definicija:** $B$ je **pridružena matrika** polinoma $p(x) = x^n - \sum_{i=0}^{n-1} \alpha_i x^i$.

#### Kaj želimo?

**Glavni cilj**
Za dano kvadratno matriko $A$ iščemo čimpreprostejšo matriko (=matriko z veliko ničlami), ki ji je podobna.
**Ekvivalentno:** Za dano linearno preslikavo $L: V \to V$ iščemo tako bazo $\mathcal{B}$ za $V$, da bo matrika $[L]_{\mathcal{B} \leftarrow \mathcal{B}}$ čimpreprostejša.
**Opomba:** Morali se bomo omejiti na kompleksne matrike.
Preproste matrike so recimo:
* diagonalne matrike (Ni vsaka k. matrika podobna diagonalni.)
* zgornje trikotne matrike (Vsaka k. matrika je podobna zg. trikotni.)
* Jordanske kanonične forme (Zelo posebni primeri zgornje trikotnih. Vsaka kompleksna matrika je podobna Jordanski kanonični formi.)
* Frobeniusove kanonične forme (Bločno diagonalne matrike iz pridruženih matrik polinomov. Vsaka matrika je podobna taki.)

#### Invariantni podprostori

**Definicija**
Naj bo $V$ vektorski prostor nad $F$ in naj bo $L: V \to V$ linearna preslikava. Vektorski podprostor $W \subseteq V$ je **invarianten za $L$**, če za vsak $w \in W$ velja $Lw \in W$.
**Opomba:** Kadar govorimo o invariantnih podprostorih matrike $A \in M_n(F)$ imamo v mislih invariantne podprostore pripadajoče linearne preslikave $L_A: F^n \to F^n, v \mapsto Av$.

**Primeri invariantnih podprostorov**
Naj bo $A \in M_n(F)$ in naj bo $e_1, \dots, e_n$ standardna baza za $F^n$.
* Če je $A$ zgornje trikotna, potem so naslednji podprostori invariantni za $A$:
$\text{Lin}\{e_1\}, \text{Lin}\{e_1, e_2\}, \dots, \text{Lin}\{e_1, e_2, \dots, e_n\}$.
* Če je $A$ diagonalna, potem so naslednji podprostori invariantni za $A$:
$\text{Lin}\{e_1\}, \text{Lin}\{e_2\}, \dots, \text{Lin}\{e_n\}$.

**Primer invariantnega podprostora**
Naj bo $V = F[x]$ vektorski prostor vseh polinomov s koeficienti v $F$ in naj bo $D: V \to V$ odvajanje polinomov. Za vsako naravno število $n$ je $F[x]_{\le n}$ (se pravi vektorski podprostor vseh polinomov v $F[x]$, ki so stopnje $\le n$) invarianten podprostor za $D$.

**$\text{Ker } L$ in $\text{Im } L$ sta invariantna podprostora za $L$**
Naj bo $L: V \to V$ linearna preslikava. Očitno $L$ pošlje elemente $\text{Ker } L$ v $0$. Ker je $0 \in \text{Ker } L$, torej $L$ pošlje vse elemente $\text{Ker } L$ v elemente $\text{Ker } L$. Torej je $\text{Ker } L$ invarianten podprostor za $L$.
Očitno $L$ pošlje vse elemente $V$ v elemente $\text{Im } L$. Torej pošlje tudi vse elemente $\text{Im } L$ v elemente $\text{Im } L$. To pomeni, da je $\text{Im } L$ invarianten podprostor za $L$.

Oglejmo si zdaj posplošitev zadnjega primera na polinome v $L$.
Naj bo $V$ vektorski prostor nad $F$. Za vsak polinom
$p(x) = a_0 + a_1 x + a_2 x^2 + \dots + a_k x^k \in F[x]$.
in vsako linearno preslikavo $L: V \to V$ definirajmo
$p(L) = a_0 \text{id}_V + a_1 L + a_2 L^2 + \dots + a_k L^k$
kjer je $L^2 = L \circ L$, $L^3 = L \circ L \circ L$, itd. Očitno je $p(L)$ linearna preslikava iz $V$ v $V$, ki pošlje vektor $v \in V$ v $p(L)v = a_0 v + a_1 Lv + \dots + a_k L^k v$.
**Opomba:** Podobno za vsako matriko $A \in M_n(F)$ definiramo
$p(A) = a_0 I_n + a_1 A + a_2 A^2 + \dots + a_k A^k$.

**Trditev**
Naj bo $V$ vektorski prostor nad $F$ in naj bo $L: V \to V$ linearna preslikava. Za vsaka polinoma $p(x), q(x) \in F[x]$ sta podprostora $\text{Ker } q(L)$ in $\text{Im } q(L)$ invariantna za $p(L)$.
**Dokaz:** V dokazu bomo uporabili, da je
$p(L) \circ q(L) = q(L) \circ p(L)$
kar sledi iz $L^r \circ L^s = L^{r+s} = L^s \circ L^r$ z direktnim računom.
* Če je $v \in \text{Ker } q(L)$, potem je $q(L)v = 0$. Odtod sledi $p(L)(q(L)v) = p(L)(0) = 0$. Po prvem odstavku odtod sledi $q(L)(p(L)v) = 0$. Torej je $p(L)v \in \text{Ker } q(L)$.
* Če je $v \in \text{Im } q(L)$, potem obstaja tak $u \in V$, da je $v = q(L)u$. Odtod sledi $p(L)v = p(L)(q(L)u) = q(L)(p(L)u) = q(L)u'$, kjer je $u' = p(L)u$ element $V$. Odtod sledi, da je $p(L)v \in \text{Im } q(L)$.

#### Invariantni podprostori in glavni cilj

Če ima linearna preslikava invarianten podprostor, potem ji lahko priredimo matriko z veliko ničlami.

**Trditev**
Naj bo $L: V \to V$ linearna preslikava in naj bo $W$ invarianten podprostor za $L$. Izberimo bazo $w_1, \dots, w_k$ za $W$ in jo dopolnimo do baze $\mathcal{B}$ za $V$. Potem je $[L]_{\mathcal{B} \leftarrow \mathcal{B}}$ bločno zgornje trikotna matrike, se pravi
$[L]_{\mathcal{B} \leftarrow \mathcal{B}} = \begin{pmatrix} A & B \\ 0 & C \end{pmatrix}$
za neko $k \times k$ matriko $A$ in neki matriki $B$ in $C$.
**Dokaz:** Naj bodo $v_1, \dots, v_l \in V$ taki vektorji, da je $w_1, \dots, w_k, v_1, \dots, v_l$ baza za $V$. Označimo to bazo z $\mathcal{B}$. Ker je $W$ invarianten podprostor za $L$, so $Lw_1, \dots, Lw_k$ v $W$. Torej lahko $Lw_1, \dots, Lw_k$ razvijemo po $w_1, \dots, w_k$:
$Lw_1 = \alpha_{1,1} w_1 + \dots + \alpha_{1,k} w_k$
$\vdots$
$Lw_k = \alpha_{k,1} w_1 + \dots + \alpha_{k,k} w_k$.
Vektorje $Lv_1, \dots, Lv_l$ razvijmo po bazi $w_1, \dots, w_k, v_1, \dots, v_l$:
$Lv_1 = \beta_{1,1} w_1 + \dots + \beta_{1,k} w_k + \gamma_{1,1} v_1 + \dots + \gamma_{1,l} v_l$
$\vdots$
$Lv_l = \beta_{l,1} w_1 + \dots + \beta_{l,k} w_k + \gamma_{l,1} v_1 + \dots + \gamma_{l,l} v_l$.
Označimo $\mathcal{B} = \{w_1, \dots, w_k, v_1, \dots, v_l\}$. Potem je
$[L]_{\mathcal{B} \leftarrow \mathcal{B}} = \begin{pmatrix} \alpha_{1,1} & \dots & \alpha_{k,1} & \beta_{1,1} & \dots & \beta_{l,1} \\ \vdots & \ddots & \vdots & \vdots & \ddots & \vdots \\ \alpha_{1,k} & \dots & \alpha_{k,k} & \beta_{1,k} & \dots & \beta_{l,k} \\ 0 & \dots & 0 & \gamma_{1,1} & \dots & \gamma_{l,1} \\ \vdots & \ddots & \vdots & \vdots & \ddots & \vdots \\ 0 & \dots & 0 & \gamma_{1,l} & \dots & \gamma_{l,l} \end{pmatrix}$.

#### Direktna vsota invariantnih podprostorov

V nadaljevanju bomo naleteli na naslednjo situacijo:

**Trditev**
Naj bo vektorski prostor $V$ direktna vsota podprostorov $W_1, \dots, W_k$. Naj bo $L: V \to V$ taka linearna preslikava, da so $W_1, \dots, W_k$ invariantni za $L$. Naj bo $\mathcal{B}_i$ baza za $W_i$ za $i = 1, \dots, k$ in naj bo $\mathcal{B} = \mathcal{B}_1 \cup \dots \cup \mathcal{B}_k$. Potem obstajajo take matrike $A_1, \dots, A_k$ velikosti $\text{dim } W_1, \dots, \text{dim } W_k$, da velja
$[L]_{\mathcal{B} \leftarrow \mathcal{B}} = \begin{pmatrix} A_1 & 0 & \dots & 0 \\ 0 & A_2 & \dots & 0 \\ \vdots & \vdots & \ddots & \vdots \\ 0 & 0 & \dots & A_k \end{pmatrix}$.
Dokaz je podoben kot pri prejšnji trditvi.

#### Enorazsežni invariantni podprostori

Pokažimo, da ima vsaka linearna preslikava $L: V \to V$, kjer je $V$ netrivialen vektorski prostor nad $\mathbb{C}$, enorazsežen invarianten podprostor.
Naslednje trditve so očitno ekvivalentne:
1. $L$ ima enorazsežen invarianten podprostor.
2. Obstaja tak neničeln $v \in V$ in tak $\lambda \in \mathbb{C}$, da je $Lv = \lambda v$.
3. Obstaja tak neničeln $v \in V$ in tak $\lambda \in \mathbb{C}$, da je $(L - \lambda \text{id})v = 0$.
4. Obstaja tak $\lambda \in \mathbb{C}$, da je $\text{Ker}(L - \lambda \text{id}) \ne \{0\}$.
5. Obstaja tak $\lambda \in \mathbb{C}$, da linearna preslikava $L - \lambda \text{id}$ ni injektivna.
6. Obstaja tak $\lambda \in \mathbb{C}$, da linearna preslikava $L - \lambda \text{id}$ ni obrnljiva.
7. Obstaja tak $\lambda \in \mathbb{C}$, da velja $\det(L - \lambda \text{id}) = 0$.
Ker smo v kompleksnih številih, ima polinomska enačba $\det(L - \lambda \text{id}) = 0$ vsaj eno netrivialno rešitev $\lambda$.

#### Kongruentnost matrik

Poleg ekvivalentnosti matrik in podobnosti matrik obstajajo še druge ekvivalenčne relacije na matrikah. Čisto na koncu semestra bomo pri teoriji kvadratnih form srečali še kongruentnost matrik.

**Definicija kongruentnosti matrik**
Pravimo, da sta kvadratni matriki $A$ in $B$ **kongruentni**, če obstaja taka obrnljiva matrika $P$, da velja $B = PAP^T$.
**Opomba:** Če sta dve matriki kongruentni, potem sta očitno tudi ekvivalentni. Obratno ni res. Recimo matriki $[1]$ in $[-1]$ sta ekvivalentni, nista pa kongruentni. Imamo torej naslednjo situacijo:

$$\text{podobnost} \Rightarrow \text{ekvivalentnost}$$
$$\text{kongruentnost} \Rightarrow \text{ekvivalentnost}$$


Če v definiciji ekvivalentnosti matrik in podobnosti matrik zamenjamo obrnljive matrike z ortogonalnimi matrikami, potem dobimo definiciji ortogonalne ekvivalentnosti matrik in ortogonalne podobnosti matrik.

**Definicije**
* Kvadratna matrika $P$ je **ortogonalna**, če velja $PP^T = I$.
* Matriki $A$ in $B$ sta **ortogonalno ekvivalentni**, če obstajata taki ortogonalni matriki $P$ in $Q$, da velja $B = PAQ^{-1}$ ($\Leftrightarrow B = PAQ^T$).
* Kvadratni matriki $A$ in $B$ sta **ortogonalno podobni**, če obstaja taka ortogonalna matrika $P$, da velja $B = PAP^{-1}$ ($\Leftrightarrow B = PAP^T$).


$$\text{ortogonalna podobnost}\Rightarrow \text{podobnost}$$
$$\text{podobnost} \Rightarrow \text{ekvivalentnost}$$
$$\text{kongruentnost} \Rightarrow \text{ekvivalentnost}$$

