### Linearne preslikave 1. del

#### Definicija linearne preslikave

Zanimajo nas preslikave med vektorskimi prostori, ki ohranjajo strukturo (se pravi ohranjajo vsoto in produkt s skalarjem). Običajno jim pravimo linearne preslikave, včasih pa tudi homomorfizmi vektorskih prostorov.

**Definicija linearne preslikave**
Naj bosta $U$ in $V$ vektorska prostora nad istim poljem $F$.
* Preslikava $L: U \to V$ je **aditivna**, če velja $L(u_1 + u_2) = L(u_1) + L(u_2)$ za vsaka $u_1, u_2 \in U$.
* Preslikava $L: U \to V$ je **homogena**, če velja $L(\alpha u) = \alpha L(u)$ za vsak $u \in U$ in vsak $\alpha \in F$.
* Preslikava $L: U \to V$ je **linearna**, če je aditivna in homogena.

**Opomba:** Namesto $L(u)$ bomo pogosto pisali kar $Lu$. Za linearno preslikavo torej velja $L(u_1 + u_2) = Lu_1 + Lu_2$ in $L(\alpha u) = \alpha Lu$.
**Opomba:** Aditivna preslikava iz $U$ v $V$ je isto kot homomorfizem Abelovih grup iz $(U, +)$ v $(V, +)$.

Aditivnost in homogenost lahko združimo v eno lastnost:

**Trditev**
Naj bosta $U$ in $V$ vektorska prostora nad istim poljem $F$. Preslikava $L: U \to V$ je linearna natanko tedaj, ko velja
$L(\alpha_1 u_1 + \alpha_2 u_2) = \alpha_1 Lu_1 + \alpha_2 Lu_2$ (1)
za vsaka $u_1, u_2 \in U$ in vsaka $\alpha_1, \alpha_2 \in F$.

**Dokaz:**
* Pokažimo najprej, da iz linearnosti sledi lastnost (1). Če je $L$ aditivna, velja $L(\alpha_1 u_1 + \alpha_2 u_2) = L(\alpha_1 u_1) + L(\alpha_2 u_2)$. Če je $L$ homogena, velja $L(\alpha_1 u_1) = \alpha_1 Lu_1$ in $L(\alpha_2 u_2) = \alpha_2 Lu_2$. Če je $L$ tako aditivna kot homogena, potem torej velja (1).
* Pokažimo še, da iz lastnosti (1) sledi linearnost. Če $L$ zadošča (1), potem velja $L(u_1 + u_2) = L(1 \cdot u_1 + 1 \cdot u_2) = 1 \cdot Lu_1 + 1 \cdot Lu_2 = Lu_1 + Lu_2$ in $L(\alpha u) = L(\alpha u + 0 \cdot u) = \alpha \cdot Lu + 0 \cdot Lu = \alpha Lu$. Torej je $L$ tako aditivna kot homogena.

**Primer - Projekcija na x os**
Če točko $(x, y)$ v ravnini projeciramo na x os, dobimo točko $(x, 0)$. Dokažimo, da je $L(x, y) = (x, 0)$ linearna preslikava. To sledi iz
$L(\alpha_1(x_1, y_1) + \alpha_2(x_2, y_2)) = L(\alpha_1 x_1 + \alpha_2 x_2, \alpha_1 y_1 + \alpha_2 y_2)$
$= (\alpha_1 x_1 + \alpha_2 x_2, 0) = \alpha_1(x_1, 0) + \alpha_2(x_2, 0) = \alpha_1 L(x_1, y_1) + \alpha_2 L(x_2, y_2)$.

**Primer - Vrtež okrog izhodišča**
Če točko $(x, y) = (r \cos \phi, r \sin \phi)$ v ravnini zavrtimo okrog izhodišča za kot $\tau$ v nasprotni smeri od urinega kazalca, potem dobimo točko $(r \cos(\phi + \tau), r \sin(\phi + \tau)) = (x \cos \tau - y \sin \tau, x \sin \tau + y \cos \tau)$, kjer smo uporabili adicijska izreka za $\cos$ in $\sin$. Dokažimo, da je $L(x, y) = (x \cos \tau - y \sin \tau, x \sin \tau + y \cos \tau)$ linearna preslikava:
$L(\alpha_1(x_1, y_1) + \alpha_2(x_2, y_2)) = L(\alpha_1 x_1 + \alpha_2 x_2, \alpha_1 y_1 + \alpha_2 y_2)$
$= ((\alpha_1 x_1 + \alpha_2 x_2) \cos \tau - (\alpha_1 y_1 + \alpha_2 y_2) \sin \tau, (\alpha_1 x_1 + \alpha_2 x_2) \sin \tau + (\alpha_1 y_1 + \alpha_2 y_2) \cos \tau)$
$= \alpha_1(x_1 \cos \tau - y_1 \sin \tau, x_1 \sin \tau + y_1 \cos \tau) + \alpha_2(x_2 \cos \tau - y_2 \sin \tau, x_2 \sin \tau + y_2 \cos \tau)$
$= \alpha_1 L(x_1, y_1) + \alpha_2 L(x_2, y_2)$.

**Primer - Odvajanje**
Vemo, da za odvod velja
$(f+g)' = f' + g'$ in $(cf)' = cf'$
kjer je $c$ konstanta. Odvod je torej linearna preslikava iz vektorskega podprostora vseh odvedljivih funkcij v $\mathbb{R}^{[a,b]}$ v vektorski prostor $\mathbb{R}^{[a,b]}$.

**Primer - Integriranje**
Vemo, da je določeni integral definiran za zvezne funkcije in da velja
$\int_a^b (f(x) + g(x)) dx = \int_a^b f(x) dx + \int_a^b g(x) dx$
in
$\int_a^b cf(x) dx = c \int_a^b f(x) dx$
Torej je $\int_a^b$ linearna preslikava iz vektorskega podprostora vseh zveznih funkcij v $\mathbb{R}^{[a,b]}$ v vektorski prostor $\mathbb{R}$.

#### Posplošitve linearnih preslikav

**Opomba:** Če sta $U$ in $V$ vektorska prostora nad različnima poljema, potem ne moremo definirati linearne preslikave iz $U$ v $V$. Lahko pa definiramo neko posplošitev linearne preslikave.
Recimo, da je $U$ vektorski prostor nad poljem $F$ in $V$ vektorski prostor nad poljem $K$. Naj bo $\phi: F \to K$ homomorfizem polj. Preslikava $L: U \to V$ je $\phi$-homogena, če velja $L(\alpha u) = \phi(\alpha)L(u)$ za vsak $u \in U$ in vsak $\alpha \in F$. Preslikava $L: U \to V$ je $\phi$-linearna, če je aditivna in $\phi$-homogena.
**Primer:** Če je $F = K = \mathbb{C}$ in $\phi(z) = \bar{z}$ (se pravi $\phi(a+bi) = a-bi$), potem $\phi$-linearni preslikavi iz $U$ v $V$ pravimo **konjugirano linearna** preslikava.

**Opomba:** Naj bosta $U$ in $V$ vektorska prostora nad poljem $F$ in naj bo $K$ podpolje v $F$. Preslikava $L: U \to V$ je $K$-homogena, če velja $L(\alpha u) = \alpha L(u)$ za vsak $\alpha \in K$ in vsak $u \in U$. Preslikava $L: U \to V$ je $K$-linearna, če je aditivna in $K$-homogena.
**Primer:** Konjugiranje je $\mathbb{R}$-linearna preslikava iz $\mathbb{C}$ v $\mathbb{C}$, ni pa $\mathbb{C}$-linearna.
**Opomba:** Če sta $U$ in $V$ modula nad kolobarjem $F$, potem linearni preslikavi iz $U$ v $V$ rečemo **homomorfizem modulov**.

#### Linearni izomorfizmi

**Definicija linearnega izomorfizma**
Bijektivni linearni preslikavi pravimo **linearni izomorfizem**.

**Trditev 1**
Inverzna preslikava od linearnega izomorfizma je spet linearni izomorfizem.
**Dokaz:** Naj bosta $U$ in $V$ vektorska prostora nad poljem $F$ in naj bo $L: U \to V$ bijektivna linearna preslikava. Radi bi pokazali, da je tudi njena inverzna preslikava $L^{-1}: V \to U$ linearna.
Za vsaka vektorja $v_1, v_2 \in V$ in vsaka skalarja $\alpha_1, \alpha_2 \in F$ velja
$L(\alpha_1 L^{-1} v_1 + \alpha_2 L^{-1} v_2) = \alpha_1 L(L^{-1} v_1) + \alpha_2 L(L^{-1} v_2)$ $= \alpha_1 v_1 + \alpha_2 v_2 = L(L^{-1}(\alpha_1 v_1 + \alpha_2 v_2))$
Ker je $L$ injektivna preslikava, sledi
$\alpha_1 L^{-1} v_1 + \alpha_2 L^{-1} v_2 = L^{-1}(\alpha_1 v_1 + \alpha_2 v_2)$.
Torej je $L^{-1}$ res linearna preslikava.

**Trditev 2**
Kompozitum dveh linearnih izomorfizmov je spet linearni izomorfizem.
**Dokaz:** Zadošča dokazati, da je kompozitum dveh linearnih preslikav spet linearna preslikava. Naj bosta $L: U \to V$ in $K: V \to W$ dve linearni preslikavi. Potem velja
$(K \circ L)(\alpha_1 u_1 + \alpha_2 u_2) = K(L(\alpha_1 u_1 + \alpha_2 u_2)) = K(\alpha_1 Lu_1 + \alpha_2 Lu_2)$
$= \alpha_1 K(Lu_1) + \alpha_2 K(Lu_2) = \alpha_1 (K \circ L)u_1 + \alpha_2 (K \circ L)u_2$.
**Opomba:** Pravimo, da sta dva vektorska prostora (nad istim poljem) **linearno izomorfna**, če obstaja linearni izomorfizem iz prvega v drugega. Iz Trditev 1 in 2 sledi, da je linearna izomorfnost ekvivalenčna relacija. (Trditev 1 da simetričnost, Trditev 2 pa tranzitivnost. Refleksivnost sledi iz dejstva, da je identična preslikava linearni izomorfizem.)
**Opomba:** Iz naslednjega primera sledi, da sta katerakoli dva enako-razsežna vektorska prostora nad istim poljem linearno izomorfna.

**Primer - Linearni izomorfizem iz $F^n$ v $n$-razsežen vektorski prostor**
Radi bi dokazali, da je vsak $n$-razsežen vektorski prostor nad $F$ linearno izomorfen $F^n$.
Naj bo $V$ $n$-razsežen vektorski prostor nad $F$ in naj bo $\mathcal{B} = \{v_1, \dots, v_n\}$ baza za $V$. Definirajmo preslikavo $\Phi_\mathcal{B}: F^n \to V$ s predpisom
$\Phi_\mathcal{B}(x_1, \dots, x_n) = x_1 v_1 + \dots + x_n v_n$.
Ker je $\mathcal{B}$ ogrodje, je $\Phi_\mathcal{B}$ surjektivna. Ker je $\mathcal{B}$ linearno neodvisna, je $\Phi_\mathcal{B}$ injektivna. Pokažimo še, da je $\Phi_\mathcal{B}$ linearna preslikava. To sledi iz
$\Phi_\mathcal{B}(\alpha(x_1, \dots, x_n) + \beta(y_1, \dots, y_n)) = \Phi_\mathcal{B}(\alpha x_1 + \beta y_1, \dots, \alpha x_n + \beta y_n)$
$= (\alpha x_1 + \beta y_1)v_1 + \dots + (\alpha x_n + \beta y_n)v_n$
$= \alpha(x_1 v_1 + \dots + x_n v_n) + \beta(y_1 v_1 + \dots + y_n v_n)$
$= \alpha \Phi_\mathcal{B}(x_1, \dots, x_n) + \beta \Phi_\mathcal{B}(y_1, \dots, y_n)$.
Torej je $\Phi_\mathcal{B}$ linearni izomorfizem. Njegova inverzna preslikava je $v \mapsto [v]_\mathcal{B}$. Po trditvi je tudi inverzna preslikava linearni izomorfizem.

**Primer - Linearni izomorfizem iz $M_{m,n}(F)$ v $\mathcal{L}(F^n, F^m)$**
Naj bo $F$ polje in naj bosta $m$ in $n$ naravni števili. Naj bo $\mathcal{L}(F^n, F^m)$ vektorski prostor vseh linearnih preslikav iz $F^n$ v $F^m$. Seštevanje je definirano z $(L_1 + L_2)u := L_1 u + L_2 u$, množenje s skalarjem pa z $(\alpha L)u := \alpha L u$. Naj bo $M_{m,n}(F)$ vektorski prostor vseh $m \times n$ matrik nad $F$. Konstruirali bomo linearni izomorfizem iz $M_{m,n}(F)$ v $\mathcal{L}(F^n, F^m)$.
Za vsako $m \times n$ matriko $A = [a_{i,j}]$ definirajmo preslikavo $L_A$ iz $F^n$ v $F^m$:
$L_A(x_1, \dots, x_n) = (a_{1,1}x_1 + \dots + a_{1,n}x_n, \dots, a_{m,1}x_1 + \dots + a_{m,n}x_n)$.
To lahko zapišemo kot $L_A x = Ax$, kjer $x$ smatramo za stolpčni vektor. Iz lastnosti matričnega množenja sledi, da je $L_A$ linearna preslikava.
Radi bi pokazali, da je preslikava $A \mapsto L_A$ iz $M_{m,n}(F)$ v $\mathcal{L}(F^n, F^m)$ linearni izomorfizem. Linearnost sledi iz
$L_{\alpha A + \beta B} x = (\alpha A + \beta B)x = \alpha Ax + \beta Bx = \alpha L_A x + \beta L_B x = (\alpha L_A + \beta L_B)x$.

Bijektivnost dokažemo tako, da konstruiramo inverzno preslikavo.
Vsaki linearni preslikavi $L: F^n \to F^m$ lahko priredimo $m \times n$ matriko $[Le_1 \dots Le_n]$, kjer je $e_1, \dots, e_n$ standardna baza za $F^n$. Pokažimo, da je $L \mapsto [Le_1 \dots Le_n]$ inverzna preslikava od preslikave $A \mapsto L_A$.
Najprej preverimo, da je kompozitum $A \mapsto L_A \mapsto [L_A e_1 \dots L_A e_n]$ identična preslikava. Če upoštevamo, da je $[e_1 \dots e_n] = I$, dobimo
$[L_A e_1 \dots L_A e_n] = [Ae_1 \dots Ae_n] = A[e_1 \dots e_n] = AI = A$.
Preverimo še, da je kompozitum $L \mapsto [Le_1 \dots Le_n] \mapsto L_{[Le_1 \dots Le_n]}$ identična preslikava. Za vsak $x \in F^n$ velja
$L_{[Le_1 \dots Le_n]} x = [Le_1 \dots Le_n] \begin{pmatrix} x_1 \\ \vdots \\ x_n \end{pmatrix} = x_1 Le_1 + \dots + x_n Le_n = L(x_1 e_1 + \dots + x_n e_n) = Lx$.
kjer smo pri prvem enačaju upoštevali definicijo $L_A$, pri drugem bločno množenje matrik in pri tretjem linearnost preslikave $L$.

#### Matrika linearne preslikave

Linearni preslikavi med dvema vektorskima prostoroma bi radi priredili matriko. To prirejanje bo odvisno od izbire baz v obeh vektorskih prostorih.
Naj bosta $U$ in $V$ vektorska prostora nad istim poljem $F$ in naj bo $L: U \to V$ linearna preslikava. Izberimo bazo $\mathcal{B} = \{u_1, \dots, u_n\}$ za $U$ in bazo $\mathcal{C} = \{v_1, \dots, v_m\}$ za $V$. Razvijmo vektorje $Lu_1, \dots, Lu_n$ po bazi $\mathcal{C}$:
$Lu_1 = \alpha_{1,1} v_1 + \dots + \alpha_{1,m} v_m$
$\vdots$
$Lu_n = \alpha_{n,1} v_1 + \dots + \alpha_{n,m} v_m$ (2)
Skalarje $\alpha_{i,j}$ iz (2) zložimo v matriko
$[L]_{\mathcal{C} \leftarrow \mathcal{B}} := \begin{pmatrix} \alpha_{1,1} & \dots & \alpha_{n,1} \\ \vdots & \ddots & \vdots \\ \alpha_{1,m} & \dots & \alpha_{n,m} \end{pmatrix}$ (3)
ki ji pravimo **matrika linearne preslikave** $L$ glede na bazi $\mathcal{B}$ in $\mathcal{C}$.

**Opomba:** Bodite pozorni na to, da smo skalarje iz $i$-te vrstice v (2) zložili v $i$-ti stolpec v (3). To si najlažje zapomnimo tako, da (3) zapišemo kot
$[L]_{\mathcal{C} \leftarrow \mathcal{B}} := [[Lu_1]_\mathcal{C} \dots [Lu_n]_\mathcal{C}]$ (4)
kjer je $[v]_\mathcal{C}$ stolpčni vektor iz koeficientov razvoja vektorja $v$ po bazi $\mathcal{C}$.
**Opomba:** Do definicije matrike linearne preslikave lahko pridemo tudi preko linearnih izomorfizmov. Kompozitum linearnih preslikav
$F^n \xrightarrow{\Phi_\mathcal{B}} U \xrightarrow{L} V \xrightarrow{\Phi_\mathcal{C}^{-1}} F^m$
je linearna preslikava $\Phi_\mathcal{C}^{-1} \circ L \circ \Phi_\mathcal{B}$ iz $F^n$ v $F^m$. Linearni izomorfizem iz $\mathcal{L}(F^n, F^m)$ v $M_{m,n}(F)$ ji priredi matriko
$[(\Phi_\mathcal{C}^{-1} \circ L \circ \Phi_\mathcal{B})(e_1) \dots (\Phi_\mathcal{C}^{-1} \circ L \circ \Phi_\mathcal{B})(e_n)]$ (5)
Ker je $(\Phi_\mathcal{C}^{-1} \circ L \circ \Phi_\mathcal{B})(e_i) = \Phi_\mathcal{C}^{-1}(L(\Phi_\mathcal{B}(e_i))) = \Phi_\mathcal{C}^{-1}(Lu_i) = [Lu_i]_\mathcal{C}$ za vsak $i=1, \dots, n$, se matrika (5) ujema z matriko (4).


#### Lastnosti matrik linearnih preslikav

Matrike linearnih preslikav imajo podobne lastnosti kot prehodne matrike.

**Izrek 1 - Osnovna formula**
Naj bo $L: U \to V$ linearna preslikava in naj bo $u$ element $U$. Naj bo $\mathcal{B}$ baza za $U$ in $\mathcal{C}$ baza za $V$. Potem velja $[Lu]_\mathcal{C} = [L]_{\mathcal{C} \leftarrow \mathcal{B}} [u]_\mathcal{B}$.
**Dokaz:** Razvijmo vektor $u$ po bazi $\mathcal{B} = \{u_1, \dots, u_n\}$. Dobimo
$u = \beta_1 u_1 + \dots + \beta_n u_n$ (6)
Ker je $L$ linearna preslikava, iz (6) sledi
$Lu = \beta_1 Lu_1 + \dots + \beta_n Lu_n$ (7)
Za vsak $i = 1, \dots, n$ razvijmo $Lu_i$ po bazi $\mathcal{C} = \{v_1, \dots, v_m\}$. Dobimo
$Lu_i = \alpha_{i,1} v_1 + \dots + \alpha_{i,m} v_m$ (8)
Če razvoje (8) vstavimo v razvoj (7), dobimo
$Lu = \beta_1(\alpha_{1,1}v_1 + \dots + \alpha_{1,m}v_m) + \dots + \beta_n(\alpha_{n,1}v_1 + \dots + \alpha_{n,m}v_m)$
$= (\beta_1 \alpha_{1,1} + \dots + \beta_n \alpha_{n,1})v_1 + \dots + (\beta_1 \alpha_{1,m} + \dots + \beta_n \alpha_{n,m})v_m$ (9)
Iz (9) sledi
$[Lu]_\mathcal{C} = \begin{pmatrix} \beta_1 \alpha_{1,1} + \dots + \beta_n \alpha_{n,1} \\ \vdots \\ \beta_1 \alpha_{1,m} + \dots + \beta_n \alpha_{n,m} \end{pmatrix} = \begin{pmatrix} \alpha_{1,1} & \dots & \alpha_{n,1} \\ \vdots & \ddots & \vdots \\ \alpha_{1,m} & \dots & \alpha_{n,m} \end{pmatrix} \begin{pmatrix} \beta_1 \\ \vdots \\ \beta_n \end{pmatrix} = [L]_{\mathcal{C} \leftarrow \mathcal{B}} [u]_\mathcal{B}$. (10)

**Izrek 2 - Matrika kompozituma linearnih preslikav**
Naj bodo $U, V$ in $W$ vektorski prostori nad istem poljem in naj bosta $L: U \to V$ in $K: V \to W$ linearni preslikavi. Naj bo $\mathcal{B}$ baza za $U$, $\mathcal{C}$ baza za $V$ in $\mathcal{D}$ baza za $W$. Potem velja $[K \circ L]_{\mathcal{D} \leftarrow \mathcal{B}} = [K]_{\mathcal{D} \leftarrow \mathcal{C}} [L]_{\mathcal{C} \leftarrow \mathcal{B}}$.
**Dokaz:** Naj bo $\mathcal{B} = \{u_1, \dots, u_n\}$. Po formuli (4) velja
$[K \circ L]_{\mathcal{D} \leftarrow \mathcal{B}} = [[(K \circ L)u_1]_\mathcal{D} \dots [(K \circ L)u_n]_\mathcal{D}]$
$= [[K(Lu_1)]_\mathcal{D} \dots [K(Lu_n)]_\mathcal{D}]$ (10)
Po izreku 1 za vsak $i = 1, \dots, n$ velja
$[K(Lu_i)]_\mathcal{D} = [K]_{\mathcal{D} \leftarrow \mathcal{C}}[Lu_i]_\mathcal{C}$ (11)
Če (11) vstavimo v (10), dobimo
$[K \circ L]_{\mathcal{D} \leftarrow \mathcal{B}} = [ [K]_{\mathcal{D} \leftarrow \mathcal{C}}[Lu_1]_\mathcal{C} \dots [K]_{\mathcal{D} \leftarrow \mathcal{C}}[Lu_n]_\mathcal{C} ]$
$= [K]_{\mathcal{D} \leftarrow \mathcal{C}} [ [Lu_1]_\mathcal{C} \dots [Lu_n]_\mathcal{C} ] = [K]_{\mathcal{D} \leftarrow \mathcal{C}} [L]_{\mathcal{C} \leftarrow \mathcal{B}}$.
Pri tretjem enačaju smo uporabili formulo (4).

**Izrek 3 - Prehod na novo bazo**
Naj bo $L: U \to V$ linearna preslikava. Naj bosta $\mathcal{B}$ in $\mathcal{B}'$ bazi za $U$ ter $\mathcal{C}$ in $\mathcal{C}'$ bazi za $V$. Potem velja $[L]_{\mathcal{C}' \leftarrow \mathcal{B}'} = P_{\mathcal{C}' \leftarrow \mathcal{C}} [L]_{\mathcal{C} \leftarrow \mathcal{B}} (P_{\mathcal{B}' \leftarrow \mathcal{B}})^{-1}$.
**Dokaz:** Najprej zapišemo $L$ kot $\text{id}_V \circ L \circ \text{id}_U$. Po izreku 2 velja
$[\text{id}_V \circ L \circ \text{id}_U]_{\mathcal{C}' \leftarrow \mathcal{B}'} = [\text{id}_V]_{\mathcal{C}' \leftarrow \mathcal{C}} [L]_{\mathcal{C} \leftarrow \mathcal{B}} [\text{id}_U]_{\mathcal{B} \leftarrow \mathcal{B}'}$.
Upoštevajmo še $[\text{id}_V]_{\mathcal{C}' \leftarrow \mathcal{C}} = P_{\mathcal{C}' \leftarrow \mathcal{C}}$ in $[\text{id}_U]_{\mathcal{B} \leftarrow \mathcal{B}'} = P_{\mathcal{B} \leftarrow \mathcal{B}'} = (P_{\mathcal{B}' \leftarrow \mathcal{B}})^{-1}$.


#### Jedro linearne preslikave

**Definicija jedra**
**Jedro** linearne preslikave $L: U \to V$ je množica
$\text{Ker } L = \{u \in U \mid Lu = 0\}$.
**Opomba:** Angleški izraz za jedro je "kernel". Nekateri uporabljajo tudi izraz "null-space" in potem jedro označijo z $N(L)$.

**Trditev 1**
Jedro linearne preslikave $L: U \to V$ je vektorski podprostor v $U$.
**Dokaz:** Radi bi pokazali, da za vsaka $u_1, u_2 \in \text{Ker } L$ in $\alpha_1, \alpha_2 \in F$ velja $\alpha_1 u_1 + \alpha_2 u_2 \in \text{Ker } L$. Po definiciji jedra iz $u_1, u_2 \in \text{Ker } L$ sledi $Lu_1 = 0$ in $Lu_2 = 0$. Po definiciji linearne preslikave odtod sledi
$L(\alpha_1 u_1 + \alpha_2 u_2) = \alpha_1 Lu_1 + \alpha_2 Lu_2 = \alpha_1 0 + \alpha_2 0 = 0$.
Po definiciji jedra odtod sledi, da velja $\alpha_1 u_1 + \alpha_2 u_2 \in \text{Ker } L$.

**Definicija ničnosti**
**Ničnost** linearne preslikave $L$ je število
$n(L) = \text{dim Ker } L$.
**Opomba:** Angleški izraz za ničnost je "nullity".

**Trditev 2**
Naslednje lastnosti linearne preslikave $L$ so ekvivalentne:
1. $\text{Ker } L = \{0\}$.
2. $n(L) = 0$.
3. $L$ je injektivna.
**Dokaz:**
* Ekvivalenca med (1) in (2) je očitna.
* Če velja (3), potem iz $Lu = L0$ sledi $u = 0$, torej velja (1).
* Recimo, da velja (1). Vzemimo taka $u_1, u_2 \in U$, da velja $Lu_1 = Lu_2$. Ker je $L$ linearna, je $L(u_1 - u_2) = Lu_1 - Lu_2 = 0$, torej je $u_1 - u_2 \in \text{Ker } L$. Iz (1) sledi, da je $u_1 - u_2 = 0$, torej je $u_1 = u_2$. Torej iz (1) sledi (3).

#### Slika linearne preslikave

**Definicija slike**
**Slika** linearne preslikave $L: U \to V$ je množica
$\text{Im } L = \{Lu \mid u \in U\}$.
**Opomba:** Angleški izraz za sliko je "image". Nekateri uporabljajo tudi izraz "range" in potem sliko označijo z $R(L)$.

**Trditev 3**
Slika linearne preslikave $L: U \to V$ je vektorski podprostor v $V$.
**Dokaz:** Radi bi pokazali, da za vsaka $v_1, v_2 \in \text{Im } L$ in vsaka $\beta_1, \beta_2 \in F$ velja $\beta_1 v_1 + \beta_2 v_2 \in \text{Im } L$. Po definiciji slike iz $v_1, v_2 \in \text{Im } L$ sledi, da obstajata taka $u_1, u_2 \in U$, da velja $v_1 = Lu_1$ in $v_2 = Lu_2$. Odtod sledi
$\beta_1 v_1 + \beta_2 v_2 = \beta_1 Lu_1 + \beta_2 Lu_2 = L(\beta_1 u_1 + \beta_2 u_2)$
ker je $L$ linearna preslikava. Po definiciji slike odtod sledi, da element $\beta_1 v_1 + \beta_2 v_2$ pripada $\text{Im } L$, saj je slika elementa $\beta_1 u_1 + \beta_2 u_2 \in U$.

**Definicija ranga**
**Rang** linearne preslikave $L$ je število
$r(L) = \text{dim Im } L$.

Direktno iz definicij dobimo:

**Trditev 4**
Naslednje lastnosti linearne preslikave $L: U \to V$ so ekvivalentne:
1. $\text{Im } L = V$.
2. $r(L) = \text{dim } V$.
3. $L$ je surjektivna.

**Opomba:** Linearna preslikava $L: U \to V$ je **ničelna**, če velja $Lu = 0$ za vsak $u \in U$. Če sta $U$ in $V$ končno-razsežna vektorska prostora, potem so ekvivalentne trditve: (1) $L$ je ničelna, (2) $\text{Ker } L = U$, (3) $n(L) = \text{dim } U$, (4) $\text{Im } L = \{0\}$, (5) $r(L) = 0$.

#### Osnovna formula

Osnovna formula povezuje ničnost in rang.

**Izrek 1: Osnovna formula**
Za vsako linearno preslikavo $L: U \to V$ velja
$n(L) + r(L) = \text{dim } U$.

**Dokaz:** Naj bo $w_1, \dots, w_k$ baza za $\text{Ker } L$ in naj bo $u_1, \dots, u_l$ njena dopolnitev do baze $U$. Velja torej $\text{dim Ker } L = k$ in $\text{dim } U = k + l$.
Naj bodo $w$ baza za ker in $u$ dopolnitev, torej $u + w$ naj bo baza za $U$.
Dokazati moramo še, da velja $\text{dim Im } L = l$.
Zadošča dokazati, da je $Lu_1, \dots, Lu_l$ baza za $\text{Im } L$. Vzemimo poljuben $v \in \text{Im } L$ in izberimo tak $u$, da je $v = Lu$. Razvijmo $u$ po bazi za $U$:
$u = \alpha_1 w_1 + \dots + \alpha_k w_k + \beta_1 u_1 + \dots + \beta_l u_l$.
Ker je $L$ linearna in ker je $Lw_1 = \dots = Lw_k = 0$, odtod sledi
$Lu = \alpha_1 Lw_1 + \dots + \alpha_k Lw_k + \beta_1 Lu_1 + \dots + \beta_l Lu_l = \beta_1 Lu_1 + \dots + \beta_l Lu_l$.
Torej so $Lu_1, \dots, Lu_l$ ogrodje za $\text{Im } L$.

Pokažimo sedaj, da so vektorji $Lu_1, \dots, Lu_l$ linearno neodvisni. Če je
$\beta_1 Lu_1 + \dots + \beta_l Lu_l = 0$, potem $\beta_1 u_1 + \dots + \beta_l u_l \in \text{Ker } L$. Ker je $w_1, \dots, w_k$ baza za $\text{Ker } L$, obstajajo taki $\gamma_1, \dots, \gamma_k \in F$, da je
$\beta_1 u_1 + \dots + \beta_l u_l = \gamma_1 w_1 + \dots + \gamma_k w_k$.
Ker je $w_1, \dots, w_k, u_1, \dots, u_l$ baza za $U$, odtod sledi $\beta_1 = \dots = \beta_l = 0$ (in $\gamma_1 = \dots = \gamma_k = 0$).

**Posledica 1**
Za vsako linearno preslikavo $L: U \to V$ obstaja taka baza $\mathcal{B}$ za $U$ in taka baza $\mathcal{C}$ za $V$, da velja
$[L]_{\mathcal{C} \leftarrow \mathcal{B}} = \begin{pmatrix} I & 0 \\ 0 & 0 \end{pmatrix}$
kjer je $I$ identična matrika velikosti $r(L)$.

**Dokaz:** Naj bodo $w_1, \dots, w_k$ in $u_1, \dots, u_l$ baza za $U$ kot v dokazu osnovne formule. Naj bo $z_1, \dots, z_s$ dopolnitev $Lu_1, \dots, Lu_l$ do baze za $V$. Vzemimo
$\mathcal{B} = \{u_1, \dots, u_l, w_1, \dots, w_k\}$ in $\mathcal{C} = \{Lu_1, \dots, Lu_l, z_1, \dots, z_s\}$.
Torej imamo $l = r(L)$ in $k = n(L)$. Ker $Lw_j = 0$, je matrika res v želeni obliki.

Ker se $u_{i}$ slika v $L(u_{i})$ in je $L(u_i)$ bazni vektor $C$ velja da se v bazi $C$ ta vektor napiše kot $(1,0,0,...)$. 

#### Ocena za ničnost

V nadaljevanju bomo potrebovali oceno za ničnost kompozituma.

**Trditev 5**
Naj bosta $L: U \to V$ in $K: V \to W$ linearni preslikavi. Potem velja
$n(K \circ L) \le n(K) + n(L)$.
**Dokaz:** Če uporabimo osnovni izrek za linearno preslikavo
$\tilde{L}: \text{Ker}(K \circ L) \to \text{Ker } K, \quad \tilde{L}(u) = L(u)$
*Gledamo če se kateri $u$ ki se slika v jedro obeh slika v kateri $v$ ki se slika preko $K$ v jedro obeh. Torej gledamo če gre $u$ preko L v nek $v$ ki gre preko K v 0*
dobimo $n(\tilde{L}) + r(\tilde{L}) = \text{dim Ker}(K \circ L)$.
*Vsi členi ki se slikajo ali v 0 v $V$ ali v element $\text{Ker } K$ v $V$, se bojo slikali v 0 potem čez $K$*
Ker je $\text{Ker } \tilde{L} = \text{Ker } L \subseteq \text{Ker}(K \circ L)$, velja
$n(\tilde{L}) = \text{dim Ker } L = n(L)$.
Ker je $\text{Im } \tilde{L} = L(\text{Ker}(K \circ L)) \subseteq \text{Ker } K$, 
*v $V$ je mogoče še kakšen element ki nima praslike v U, ki se slika v 0*
velja
$r(\tilde{L}) = \text{dim Im } \tilde{L} \le \text{dim Ker } K = n(K)$.
Torej je $\text{dim Ker}(K \circ L) = n(\tilde{L}) + r(\tilde{L}) \le n(L) + n(K)$

#### Jedro in slika matrike

Vsaki $m \times n$ matriki $A$ z elementi iz $F$ lahko priredimo linearno preslikavo
$L_A: F^n \to F^m, \quad L_A v = Av$.
Jedro in sliko matrike $A$ definiramo takole
$\text{Ker } A := \text{Ker } L_A$ in $\text{Im } A := \text{Im } L_A$.
Se pravi
$\text{Ker } A = \{v \in F^n \mid Av = 0\}$.
in
$\text{Im } A = \{Av \mid v \in F^n\}$.
Elemente $F^n$ si obakrat predstavljamo kot stolpčne vektorje.

**Trditev 6**
Slika matrike je enaka linearni ogrinjači njenih stolpcev. Rang matrike je enak maksimalnemu številu linearno neodvisnih stolpcev te matrike.
**Dokaz:** Če so $a_1, \dots, a_n$ stolpci matrike $A$ in $\alpha_1, \dots, \alpha_n$ komponente vektorja $v$, potem je $Av = \alpha_1 a_1 + \dots + \alpha_n a_n$. Torej je
$\text{Im } A = \{\alpha_1 a_1 + \dots + \alpha_n a_n \mid \alpha_1, \dots, \alpha_n \in F\} = \text{Lin}\{a_1, \dots, a_n\}$.
Izberimo take stolpce $a_{i_1}, \dots, a_{i_r}$, ki so linearno neodvisni in ki zadoščajo $\text{Lin}\{a_1, \dots, a_n\} = \text{Lin}\{a_{i_1}, \dots, a_{i_r}\}$. Potem so stolpci $a_{i_1}, \dots, a_{i_r}$ baza podprostora $\text{Im } A$. Odtod sledi, da je rang matrike $A$ enak $r$, se pravi maksimalnemu številu linearno neodvisnih stolpcev matrike $A$.
**Opomba:** Linearni ogrinjači stolpcev matrike $A$ pravimo **stolpčni prostor** matrike $A$ in jo označimo z $\text{Col } A$. Dokazali smo, da je $\text{Im } A = \text{Col } A$.
**Opomba:** Linearni ogrinjači vrstic matrike $A$ pravimo **vrstični prostor** matrike $A$ in jo označimo z $\text{Row } A$. Očitno elemente $\text{Row } A$ dobimo tako, da transponiramo elemente $\text{Col } A^T = \text{Im } A^T$.

