### Vektorski prostori 1. del

#### Definicija vektorskega prostora

Vektorski prostor nad poljem $(F, \oplus, \odot)$ je podan s tremi podatki:
1. Neprazno množico $V$.
2. Tako operacijo $+$ na $V$, da je $(V, +)$ Abelova grupa.
3. Tako preslikavo $\cdot : F \times V \to V$, da velja:
   (i) $\alpha \cdot (u + v) = (\alpha \cdot u) + (\alpha \cdot v)$ za vse $\alpha \in F$ in $u, v \in V$.
   (ii) $(\alpha \oplus \beta) \cdot v = (\alpha \cdot v) + (\beta \cdot v)$ za vse $\alpha, \beta \in F$ in $v \in V$.
   (iii) $(\alpha \odot \beta) \cdot v = \alpha \cdot (\beta \cdot v)$ za vse $\alpha, \beta \in F$ in $v \in V$.
   (iv) $1 \cdot v = v$ za vse $v \in V$.

**Opomba:** Elementom množice $V$ pravimo vektorji. Elementom množice $F$ pravimo skalarji. Operaciji $+$ pravimo vsota vektorjev. Funkciji $\cdot$ pravimo produkt vektorja s skalarjem.
**Opomba:** Namesto $\alpha \oplus \beta$ bomo pisali kar $\alpha + \beta$. Namesto $\alpha \odot \beta$ bomo pisali kar $\alpha\beta$. Namesto $\alpha \cdot v$ bomo pisali kar $\alpha v$. Produkt vektorja s skalarjem naj ima višjo prioriteto kot vsota vektorjev (manj oklepajev).

Vektorski prostor nad poljem $F$ lahko definiramo tudi kot Abelovo grupo $(V, +)$ skupaj z homomorfizmom kolobarjev z enoto iz $F$ v $\text{End}(V, +)$, kjer je $\text{End}(V, +)$ kolobar endomorfizmov Abelove grupe $(V, +)$.

Pokažimo zdaj, da sta obe definiciji ekvivalentni. Za vsak $\alpha \in F$ naj bo
$\Phi_\alpha: V \to V, \quad \Phi_\alpha(v) := \alpha v$.
Po lastnosti (i) je
$\Phi_\alpha(u + v) = \alpha(u + v) = \alpha u + \alpha v = \Phi_\alpha(u) + \Phi_\alpha(v)$,
torej je $\Phi_\alpha$ endomorfizem Abelove grupe $(V, +)$. Oglejmo si preslikavo
$\Phi: F \to \text{End}(V, +), \quad \Phi(\alpha) := \Phi_\alpha$.

Pokažimo, da je $\Phi$ homomorfizem kolobarjev z enoto.
Za vsaka $\alpha, \beta \in F$ in za vsak $v \in V$ po lastnostih (ii)-(iv) velja
$\Phi(\alpha+\beta)(v) = (\alpha+\beta)v = \alpha v + \beta v = \Phi(\alpha)(v) + \Phi(\beta)(v) = (\Phi(\alpha)+\Phi(\beta))(v)$
$\Phi(\alpha\beta)(v) = (\alpha\beta)v = \alpha(\beta v) = \Phi(\alpha)(\Phi(\beta)(v)) = (\Phi(\alpha) \circ \Phi(\beta))(v)$
$\Phi(1)(v) = 1v = v = \text{id}(v)$
torej je $\Phi(\alpha + \beta) = \Phi(\alpha) + \Phi(\beta)$, $\Phi(\alpha\beta) = \Phi(\alpha) \circ \Phi(\beta)$ in $\Phi(1) = \text{id}$.

Pokažimo še obratno. Naj bo $\Phi: F \to \text{End}(V, +)$ homomorfizem kolobarjev z enoto. Za vsaka $\alpha \in F$ in $v \in V$ definirajmo
$\alpha v := \Phi(\alpha)(v)$.
Ker je $\Phi(\alpha)$ endomorfizem Abelove grupe $(V, +)$, velja
$\alpha(u + v) = \Phi(\alpha)(u + v) = \Phi(\alpha)(u) + \Phi(\alpha)(v) = \alpha u + \alpha v$.
Ker je $\Phi$ homomorfizem kolobarjev z enoto, velja
$(\alpha+\beta)v = \Phi(\alpha+\beta)(v) = (\Phi(\alpha)+\Phi(\beta))(v) = \Phi(\alpha)(v)+\Phi(\beta)(v) = \alpha v+\beta v$
$(\alpha\beta)v = \Phi(\alpha\beta)(v) = (\Phi(\alpha) \circ \Phi(\beta))(v) = \Phi(\alpha)(\Phi(\beta)(v)) = \alpha(\beta v)$
$1v = \Phi(1)(v) = \text{id}(v) = v$.

#### Primeri vektorskih prostorov

**Primer: Vektorski prostor $F^n$**
Naj bo $F$ polje in $n$ naravno število. Označimo z $F^n$ množico vseh $n$-teric elementov iz $F$. Vsota dveh vektorjev in produkt vektorja s skalarjem naj bosta definirana po komponentah.
$(\alpha_1, \dots, \alpha_n) + (\beta_1, \dots, \beta_n) := (\alpha_1 + \beta_1, \dots, \alpha_n + \beta_n)$
$\gamma(\alpha_1, \dots, \alpha_n) := (\gamma\alpha_1, \dots, \gamma\alpha_n)$
Potem je $F^n$ vektorski prostor nad $F$.
**Opomba:** Pri $n = 1$ dobimo, da je $F$ vektorski prostor nad $F$.

**Primer: Vektorski prostor $M_{m,n}(F)$**
Naj bo $F$ polje in naj bosta $m$ in $n$ naravni števili. Označimo z $M_{m,n}(F)$ množico vseh $m \times n$ matrik z elementi iz $F$. Definirajmo vsoto dveh matrik in produkt matrike s skalarjem na običajen način, se pravi po komponentah. Potem je $M_{m,n}(F)$ vektorski prostor nad $F$.

**Primer: Vektorski prostor $F^S$**
Naj bo $F$ polje in naj bo $S$ neprazna množica. Množico vseh funkcij iz $S$ v $F$ označimo z $F^S$. Vsota funkcij je definirana po elementih:
$(f + g)(s) := f(s) + g(s)$
Tudi produkt funkcije s skalarjem je definiran po elementih
$(\gamma f)(s) := \gamma f(s)$
Potem je $F^S$ vektorski prostor.
**Opomba:** Če je $S = \{1, \dots, n\}$ potem lahko $F^S$ identificiramo s $F^n$. Če je $S = \{1, \dots, m\} \times \{1, \dots, n\}$ potem lahko $F^S$ identificiramo s $M_{m,n}(F)$.

**Primer: Trivialni vektorski prostor nad $F$**
Množica $V = \{0\}$ je vektorski prostor nad poljem $F$. Vsota vektorjev je definirana z $0 + 0 = 0$. Produkt vektorja s skalarjem je definiran z $\alpha 0 = 0$.

**Primer: Vektorski prostor polinomov**
Naj bo $F$ polje in naj bo $F[x]$ množica vseh polinomov v spremenljivki $x$ s koeficienti iz $F$. Vsoto dveh polinomov in produkt polinoma s skalarjem definiramo na običajen način. Potem je $F[x]$ vektorski prostor nad $F$.

**Primer: Razširitev polj**
Če je $F$ podpolje polja $K$, potem je $K$ vektorski prostor nad $F$ za običajno vsoto na $K$ in običajen produkt na $K$. (Funkcija iz $F \times K \to K$ je skrčitev operacije množenja, ki je funkcija iz $K \times K \to K$.)
**Opomba:** Ker je polje $F$ podpolje polja racionalnih funkcij $F(x)$, je $F(x)$ vektorski prostor nad $F$.

**Primer: Direktna vsota vektorskih prostorov**
Naj bo $F$ polje in naj bodo $V_1, \dots, V_k$ vektorski prostori nad $F$. Označimo z $V_1 \oplus \dots \oplus V_k$ množico vseh $k$-teric $(v_1, \dots, v_k)$, kjer $v_i \in V_i$ za vse $i$. Vsota dveh $k$-teric in produkt $k$-terice s skalarjem sta definirana po komponentah. Potem je $V_1 \oplus \dots \oplus V_k$ vektorski prostor nad $F$.

#### Vektorski podprostori

**Definicija vektorskega podprostora**
Naj bo $V$ vektorski prostor nad poljem $F$. 

Neprazna podmnožica $U \subseteq V$ je vektorski podprostor v $V$, če velja:
* Za vsaka $u_1, u_2 \in U$ velja $u_1 + u_2 \in U$.
* Za vsak $u \in U$ in vsak $\alpha \in F$ velja $\alpha u \in U$.
**Opomba:** Vsak vektorski podprostor vsakega vektorskega prostora nad $F$ je spet vektorski prostor nad $F$. (Vsoto dveh vektorjev v $U$ izračunamo kot v $V$. Tudi produkt vektorja iz $U$ s skalarjem izračunamo kot v $V$.)


**Trditev**
Vsak vektorski podprostor vsebuje ničelni vektor.
**Dokaz:** Naj bo $V$ vektorski prostor nad poljem $F$. Enoto Abelove grupe $V$ označimo z $0_V$. Naj bo $U$ vektorski podprostor v $V$ in naj bo $u$ poljuben element $U$. Po drugi lastnosti iz definicije vektorskega podprostora velja $0u \in U$. Iz $0_V + 0u = 0u = (0 + 0)u = 0u + 0u$ sledi $0_V = 0u \in U$.

**Opomba:** Če je $W$ vektorski podprostor v $V$ in če je $U$ vektorski podprostor v $W$, potem je $U$ vektorski podprostor v $V$.

**Trditev**
Naj bo $V$ vektorski prostor nad poljem $F$. Neprazna podmnožica $U \subseteq V$ je vektorski podprostor v $V$ natanko tedaj, ko za vsaka $u_1, u_2 \in U$ in vsaka $\alpha_1, \alpha_2 \in F$ velja $\alpha_1 u_1 + \alpha_2 u_2 \in U$.
**Dokaz:**
* Najprej dokažimo, da ima vsak vektorski podprostor $U \subseteq V$ lastnost iz trditve. Vzemimo $u_1, u_2 \in U$ in $\alpha_1, \alpha_2 \in F$. Ker je $U$ zaprta za množenje s skalarji, velja $\alpha_1 u_1 \in U$ in $\alpha_2 u_2 \in U$. Ker je $U$ zaprta za seštevanje, odtod sledi $\alpha_1 u_1 + \alpha_2 u_2 \in U$.
* Dokažimo še, da je vsaka podmnožica $U \subseteq V$, ki zadošča lastnosti iz trditve, vektorski podprostor v $V$. Za vsaka $u_1, u_2 \in U$ je po lastnosti iz trditve $1u_1 + 1u_2 \in U$. Torej je $U$ zaprta za seštevanje. Za vsak $u \in U$ in vsak $\alpha \in F$ je po lastnosti iz trditve $\alpha u + 0u \in U$. Torej je $U$ zaprta za množenje s skalarjem.

**Trditev**
Naj bodo $U_1, \dots, U_k$ podprostori vektorskega prostora $V$. Potem velja:
* Njihov presek $U_1 \cap \dots \cap U_k$ je vektorski podprostor v $V$.
* Njihova vsota $U_1 + \dots + U_k$ je vektorski podprostor v $V$.
  (To je množica vseh vektorjev $u_1 + \dots + u_k$, kjer $u_i \in U_i$ za vsak $i$.)

**Dokaz za presek:** Vzemimo $w, z \in U_1 \cap \dots \cap U_k$ in $\alpha, \beta \in F$. Radi bi dokazali, da $\alpha w + \beta z \in U_1 \cap \dots \cap U_k$. Za vsak $i = 1, \dots, k$ je $U_i$ tak podprostor v $V$, ki vsebuje tako $w$ kot $z$, torej vsebuje tudi $\alpha w + \beta z$. Ker $\alpha w + \beta z$ leži v vseh $U_i$, leži tudi v preseku.

**Dokaz za vsoto:** Vzemimo $w, z \in U_1 + \dots + U_k$ in $\alpha, \beta \in F$. Radi bi dokazali, da $\alpha w + \beta z \in U_1 + \dots + U_k$. Po definiciji vsote podprostorov lahko $w$ in $z$ izrazimo kot $w = w_1 + \dots + w_k$ in $z = z_1 + \dots + z_k$, kjer $w_i, z_i \in U_i$ za vsak $i = 1, \dots, k$. Ker so vsi $U_i$ podprostori v $V$ velja $\alpha w_i + \beta z_i \in U_i$ za vsak $i = 1, \dots, k$. Odtod sledi
$\alpha w + \beta z = \alpha(w_1 + \dots + w_k) + \beta(z_1 + \dots + z_k) = (\alpha w_1 + \beta z_1) + \dots + (\alpha w_k + \beta z_k) \in U_1 + \dots + U_k$.

#### Primeri vektorskih podprostorov

**Primer: Trivialni in nepravi vektorski podprostor**
Če je $V$ vektorski prostor nad $F$, potem sta $\{0\}$ in $V$ vedno vektorska podprostora v $V$. Prvemu pravimo trivialni vektorski podprostor, drugemu pa nepravi vektorski podprostor.
Če je $V = F$ sta to edina vektorska podprostora v $V$. Vsak netrivialen vektorski podprostor $U$ v $F$ namreč vsebuje neničeln element $\alpha \in F$. Potem za vsak $\beta \in F$ velja $\beta = (\beta\alpha^{-1})\alpha \in U$. Torej je $U = F$.

**Primer: Vektorski podprostori v $F^2$**
Naj bo $F$ polje in $u \in F^2$. Množica $U := \{\alpha u \mid \alpha \in F\}$ je očitno zaprta za seštevanje in množenje s skalarjem, torej je vektorski podprostor v $F^2$.
Pokažimo, da je $U$ pravi vektorski podprostor. Če $U = F^2$, bi obstajala taka $\alpha_1, \alpha_2 \in F$, da bi veljalo $(1,0) = \alpha_1 u$ in $(0,1) = \alpha_2 u$. Odtod bi sledilo, da je $\alpha_2(1, 0) = \alpha_1(0, 1)$, se pravi $\alpha_1 = \alpha_2 = 0$, kar da protislovje.
**Naloga:** Pokažite, da smo dobili vse prave vektorske podprostore v $F^2$.

**Primer: Množica rešitev homogenega sistema linearnih enačb**
Naj bo $A$ $m \times n$ matrika z elementi iz $F$. Množico vseh $n$-teric $x \in F^n$, ki rešijo homogeni sistem linearnih enačb $Ax = 0$ označimo z $\text{Ker } A$ in ji pravimo jedro matrike $A$. Vemo, da je $\text{Ker } A$ vektorski podprostor v $F^n$.

**Primer: Matrični prostori**
Naj bo $V = M_n(F)$ vektorski prostor $n \times n$ matrik. Naslednje podmnožice v $V$ so vektorski podprostori v $V$.
* Vse simetrične matrike. (Matrika $A$ je simetrična, če je $A^T = A$.)
* Vse antisimetrične matrike. ($A$ je antisimetrična, če $A^T = -A$.)
* Vse matrike $X$, ki zadoščajo enačbi $A_1 X B_1 + \dots + A_k X B_k = 0$.
* Vse matrike, ki imajo sled enako nič.
* Vse matrike, ki imajo ničle na predpisanih mestih $(i_1, j_1), \dots, (i_k, j_k)$.
  (Npr. vse diagonalne matrike, vse zgornje trikotne matrike, vse matrike z ničelnim prvim stolpcem, vse matrike z $a_{1,n} = 0$, itd.)

**Primer: Prostori polinomov in racionalnih funkcij**
Naj bo $F$ polje. Množica vseh polinomov $F[x]$ je vektorski podprostor v vektorskem prostoru $F(x)$ vseh racionalnih funkcij. Množica $F[x]_{\le n}$ vseh polinomov stopnje $\le n$ je vektorski podprostor v vektorskem prostoru $F[x]$.

**Primer: Funkcijski prostori**
Naj bo $V = \mathbb{R}^{[a,b]}$ vektorski prostor vseh funkcij iz intervala $[a, b]$ v $\mathbb{R}$. Naslednje podmnožice v $V$ so vektorski podprostori v $V$:
* Vse omejene funkcije.
* Vse integrabilne funkcije.
* Vse zvezne funkcije.
* Vse odvedljive funkcije.
* Vse dvakrat odvedljive funkcije $y(x)$, ki rešijo dano homogeno linearno diferencialno enačbo 2. reda $p(x)y''(x) + q(x)y'(x) + r(x)y(x) = 0$.
* Vse funkcije, ki zadoščajo $f(a) = 0$.
* Vse funkcije, ki zadoščajo $f(a) = f(b)$.

