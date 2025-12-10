
## 1. Pozitivno semidefinitne matrike

Matrike, ki jih bomo potrebovali pri konstrukciji singularnega razcepa.

### Definicija pozitivno semidefinitne in pozitivno definitne matrike

Matrika $A$ je **pozitivno semidefinitna**, če je sebiadjungirana ($A=A^*$) in če velja $\langle Av, v \rangle \ge 0$ za vsak vektor $v$.
Matrika $A$ je **pozitivno definitna**, če je sebiadjungirana ($A=A^*$) in če velja $\langle Av, v \rangle > 0$ za vsak neničeln vektor $v$.

**Oznake:** Če je matrika $A$ pozitivno semidefinitna pišemo $A \ge 0$. Če je matrika $A$ pozitivno definitna, pišemo $A > 0$.

**Opomba:** V obeh definicijah uporabljamo standardni skalarni produkt, ki je definiran z $\langle u, v \rangle = v^*u$. Torej je $\langle Av, v \rangle = v^*Av$.
**Opomba:** Pozitivno definitne matrike so poseben primer pozitivno semidefinitnih matrik. Te pa so poseben primer sebiadjungiranih matrik.
**Opomba:** Lahko bi definirali tudi pojem pozitivno (semi)definitne linearne preslikave iz $V$ v $V$, kjer je $V$ vektorski prostor s skalarnim produktom.

### Izrek (Karakterizacije pozitivno semidefinitnih matrik)

Za kompleksno matriko $A$ so ekvivalentne naslednje trditve:
1.  $A$ je pozitivno semidefinitna.
2.  $A$ je sebiadjungirana in vse njene lastne vrednosti so $\ge 0$.
3.  Obstaja taka unitarna matrika $P$ in taka diagonalna matrika $D$, ki ima vse elemente realne in $\ge 0$, da velja $A = PDP^{-1}$.
4.  Obstaja taka sebiadjungirana matrika $B$, da velja $A = B^2$.
5.  Obstaja taka matrika $B$ (ne nujno kvadratna), da velja $A = B^*B$.

**Dokaz (skica):**
*   **$(1) \implies (2)$:** Če velja (1) (A je pozitivno semidefinitna), potem za vsako lastno vrednost $\lambda$ matrike $A$ in za vsak pripadajoči lastni vektor $v$ velja $\lambda \langle v, v \rangle = \langle \lambda v, v \rangle = \langle Av, v \rangle \ge 0$. Ker je $v \ne 0$, je $\langle v, v \rangle > 0$, odtod sledi $\lambda \ge 0$. Ker je $A$ pozitivno semidefinitna, je tudi sebiadjungirana.
*   **$(2) \implies (3)$:** Vemo, da se da vsako sebiadjungirano matriko $A$ izraziti kot $A = PDP^{-1}$, kjer je $P$ unitarna matrika in $D$ realna diagonalna matrika, ki ima po diagonali lastne vrednosti matrike $A$. Torej iz (2) sledi (3).
*   **$(3) \implies (4)$:** Če velja (3), lahko diagonalne elemente matrike $D$ korenimo. Torej obstaja taka realna diagonalna matrika $E$, da je $D = E^2$ (ker so vsi elementi $D$ realni in $\ge 0$). Definirajmo matriko $B := PEP^{-1}$. Ker je matrika $P$ unitarna, je matrika $B$ sebiadjungirana ($B^* = (PEP^{-1})^* = (P^{-1})^* E^* P^* = PE^*P^{-1} = PEP^{-1} = B$, saj je $E$ realna diagonalna). In velja $B^2 = (PEP^{-1})^2 = PE^2P^{-1} = PDP^{-1} = A$. Torej velja (4).
*   **$(4) \implies (5)$:** Očitno iz (4) sledi (5), saj če je $A=B^2$ in $B$ sebiadjungirana, potem $A=B^*B$.
*   **$(5) \implies (1)$:** Če velja (5) ($A=B^*B$), potem je $A^* = (B^*B)^* = B^*(B^*)^* = B^*B = A$. Torej je $A$ sebiadjungirana. Poleg tega je $\langle Av, v \rangle = \langle B^*Bv, v \rangle = \langle Bv, Bv \rangle = ||Bv||^2 \ge 0$ za vsak $v$. Torej velja (1).

### Pozitivno definitna verzija izreka

Za kompleksno matriko $A$ so ekvivalentne trditve:
1.  $A$ je pozitivno definitna.
2.  $A$ je sebiadjungirana in vse njene lastne vrednosti so $> 0$.
3.  $A = PDP^{-1}$ za unitarno matriko $P$ in diagonalno matriko $D > 0$.
4.  $A = B^2$ za obrnljivo sebiadjungirano matriko $B$.
5.  $A = B^*B$ za matriko $B$ z linearno neodvisnimi stolpci.

### Realna verzija izreka

Za vsako realno matriko $A$ so ekvivalentne trditve:
1.  $A$ je pozitivno semidefinitna (sebiadjungirana postane simetrična, $A=A^T$).
2.  $A$ je simetrična in vse njene lastne vrednosti so $\ge 0$.
3.  $A = PDP^{-1}$ za ortogonalno matriko $P$ in diagonalno matriko $D \ge 0$.
4.  $A = B^2$ za simetrično matriko $B$.
5.  $A = B^TB$ za realno matriko $B$, ki ni nujno kvadratna.

**Opomba:** Pogosto se zastavi vprašanje ali že iz pogoja $\langle Av, v \rangle \ge 0$ za vsak $v$ sledi, da je $A$ pozitivno semidefinitna (tj. $A=A^*$). V realnem primeru je odgovor ne, v kompleksnem primeru pa je odgovor da.

**Prvi del dokaza (realen primer):** Če je $A$ neničelna realna matrika, ki zadošča $A^T = -A$, potem $A$ ni sebiadjungirana (razen če $A=0$), vendar velja $\langle Av, v \rangle = 0$ za vsak realen $v$. Velja namreč $v^TAv = (v^TAv)^T = v^TA^Tv = v^T(-A)v = -v^TAv$, torej je $2v^TAv = 0$, kar pomeni $v^TAv = 0$.

**Drugi del dokaza (kompleksen primer):** Pokažimo, da je kompleksna $n \times n$ matrika $A$ sebiadjungirana natanko tedaj, ko velja $\langle Av, v \rangle \in \mathbb{R}$ za vsak $v \in \mathbb{C}^n$.
Za $B := A - A^*$ velja $\langle Bv, v \rangle = \langle Av, v \rangle - \langle A^*v, v \rangle = \langle Av, v \rangle - \overline{\langle Av, v \rangle}$.
Torej je $\langle Av, v \rangle \in \mathbb{R}$ natanko tedaj, ko je $\langle Bv, v \rangle = 0$. Če je $\langle Bv, v \rangle = 0$ za vsak $v$, potem vstavimo $v = u + u'$ in dobimo $\langle Bu, u' \rangle + \langle Bu', u \rangle = 0$ za vsaka $u, u'$ (ker je $\langle Bu, u \rangle = \langle Bu', u' \rangle = 0$). Če namesto $u$ vstavimo $iu$, dobimo $i\langle Bu, u' \rangle - i\langle Bu', u \rangle = 0$ za vsaka $u, u'$. Če to enačbo delimo z $i$ in jo prištejemo k gornji enačbi, dobimo $2\langle Bu, u' \rangle = 0$ za vsaka $u, u'$. Če vstavimo $u' = Bu$, dobimo $Bu = 0$ za vsak $u$. Torej je $B = 0$.

## 2. Klasifikacija skalarnih produktov

V tem razdelku bomo opisali vse skalarne produkte na $\mathbb{R}^n$ in $\mathbb{C}^n$. Standardni skalarni produkt je definiran z $\langle u, v \rangle = v^*u$. Na dolgo:
$$ \left\langle \begin{bmatrix} \alpha_1 \\ \vdots \\ \alpha_n \end{bmatrix}, \begin{bmatrix} \beta_1 \\ \vdots \\ \beta_n \end{bmatrix} \right\rangle = \alpha_1\overline{\beta_1} + \dots + \alpha_n\overline{\beta_n} = \begin{bmatrix} \overline{\beta_1} & \dots & \overline{\beta_n} \end{bmatrix} \begin{bmatrix} \alpha_1 \\ \vdots \\ \alpha_n \end{bmatrix} $$
Vsak drug skalarni produkt bomo označili z $[u, v]$.

### Trditev

Če je $A$ kompleksna pozitivno definitna $n \times n$ matrika, potem je z $[u, v] := \langle Au, v \rangle$ definiran skalarni produkt na $\mathbb{C}^n$. Če je $A$ realna pozitivno definitna $n \times n$ matrika, potem nam ista formula da skalarni produkt na $\mathbb{R}^n$.

**Dokaz:** Preverimo, da $[u, v]$ zadošča vsem trem lastnostim iz definicije skalarnega produkta.
1.  **Pozitivna definitnost:** Ker je $A$ pozitivno definitna matrika, velja $\langle Au, u \rangle > 0$ za vsak neničeln vektor $u$. Torej velja $[u, u] > 0$ za vsak neničeln vektor $u$.
2.  **Konjugirana simetričnost:** Ker je $A = A^*$, velja za vsak $u$ in vsak $v$:
    $[v, u] = \langle Av, u \rangle = \langle v, A^*u \rangle = \langle v, Au \rangle = \overline{\langle Au, v \rangle} = \overline{[u, v]}$.
3.  **Linearnost v prvem faktorju:** Velja:
    $[\alpha_1 u_1 + \alpha_2 u_2, v] = \langle A(\alpha_1 u_1 + \alpha_2 u_2), v \rangle = \langle \alpha_1 Au_1 + \alpha_2 Au_2, v \rangle$
    $= \alpha_1 \langle Au_1, v \rangle + \alpha_2 \langle Au_2, v \rangle = \alpha_1[u_1, v] + \alpha_2[u_2, v]$
    za vektorje $u_1, u_2, v$ in skalarja $\alpha_1, \alpha_2$.

### Trditev

Za vsak skalarni produkt $[u, v]$ na $\mathbb{C}^n$ obstaja taka kompleksna pozitivno definitna $n \times n$ matrika $A$, da za vsak $u \in \mathbb{C}^n$ in vsak $v \in \mathbb{C}^n$ velja $[u, v] = \langle Au, v \rangle$.
Za vsak skalarni produkt $[u, v]$ na $\mathbb{R}^n$ obstaja taka realna pozitivno definitna $n \times n$ matrika $A$, da za vsaka $u, v \in \mathbb{R}^n$ velja $[u, v] = \langle Au, v \rangle$.

**Dokaz:**
Naj bo $e_1, \dots, e_n$ standardna baza za $\mathbb{C}^n$. Pokažimo, da je iskana matrika $A$ definirana z $A_{ij} = [e_j, e_i]$.
$$ A = \begin{bmatrix} [e_1, e_1] & [e_2, e_1] & \dots & [e_n, e_1] \\ [e_1, e_2] & [e_2, e_2] & \dots & [e_n, e_2] \\ \vdots & \vdots & \ddots & \vdots \\ [e_1, e_n] & [e_2, e_n] & \dots & [e_n, e_n] \end{bmatrix} $$
Iz konjugirane simetričnosti skalarnega produkta $[u, v]$ sledi, da je $A^* = A$. (Element $A^*_{ij} = \overline{A_{ji}} = \overline{[e_i, e_j]} = [e_j, e_i] = A_{ij}$).
Po drugi strani za $u = \sum_{i=1}^n \alpha_i e_i$ in $v = \sum_{j=1}^n \beta_j e_j$ velja:
$$ [u, v] = \sum_{i=1}^n \sum_{j=1}^n \alpha_i \overline{\beta_j} [e_i, e_j] $$
Medtem ko je $\langle Au, v \rangle = v^*Au = \left( \sum_{j=1}^n \overline{\beta_j} e_j^* \right) A \left( \sum_{i=1}^n \alpha_i e_i \right) = \sum_{i=1}^n \sum_{j=1}^n \overline{\beta_j} \alpha_i A_{ji} = \sum_{i=1}^n \sum_{j=1}^n \alpha_i \overline{\beta_j} [e_i, e_j]$.
Torej $[u, v] = \langle Au, v \rangle$.
Odtod sledi, da je $A$ pozitivno definitna, saj za vsak neničeln $u$ velja $\langle Au, u \rangle = [u, u] > 0$.

## 3. QR razcep in razcep Choleskega

Oglejmo si dva znana razcepa matrik.

### Izrek (QR razcep)

Če je matrika $A$ obrnljiva kompleksna matrika, potem obstaja unitarna matrika $Q$ in taka zgornje trikotna matrika $R$, da je $A = QR$. Če je $A$ realna, lahko $Q$ in $R$ izberemo tako, da sta realni.

**Dokaz:**
Naj bodo $v_1, \dots, v_n$ stolpci matrike $A$. Ker je $A$ obrnljiva, so ti vektorji baza za $\mathbb{C}^n$. Napravimo Gram-Schmidtovo ortogonalizacijo (za ortonormirano bazo):
$w_1 = v_1$, $e_1 = \frac{w_1}{||w_1||}$
$w_2 = v_2 - \langle v_2, e_1 \rangle e_1$, $e_2 = \frac{w_2}{||w_2||}$
$\vdots$
$w_n = v_n - \langle v_n, e_1 \rangle e_1 - \dots - \langle v_n, e_{n-1} \rangle e_{n-1}$, $e_n = \frac{w_n}{||w_n||}$
Pomnožimo $i$-to enačbo ($w_i = v_i - \sum_{j=1}^{i-1} \langle v_i, e_j \rangle e_j$) skalarno z $e_j$:
$\langle w_i, e_j \rangle = \langle v_i, e_j \rangle - \sum_{k=1}^{i-1} \langle v_i, e_k \rangle \langle e_k, e_j \rangle = \langle v_i, e_j \rangle - \langle v_i, e_j \rangle = 0$ za $j<i$.
Torej je $w_i = ||w_i|| e_i$. Odtod sledi $v_i = ||w_i|| e_i + \sum_{j=1}^{i-1} \langle v_i, e_j \rangle e_j$.
Kar lahko po matrično zapišemo z:
$$ A = \begin{bmatrix} v_1 & v_2 & \dots & v_n \end{bmatrix} = \begin{bmatrix} e_1 & e_2 & \dots & e_n \end{bmatrix} \begin{bmatrix} ||w_1|| & \langle v_2, e_1 \rangle & \dots & \langle v_n, e_1 \rangle \\ 0 & ||w_2|| & \dots & \langle v_n, e_2 \rangle \\ \vdots & \vdots & \ddots & \vdots \\ 0 & 0 & \dots & ||w_n|| \end{bmatrix} $$
Torej je res $A = QR$, kjer je $Q = \begin{bmatrix} e_1 & e_2 & \dots & e_n \end{bmatrix}$ unitarna in $R = \begin{bmatrix} ||w_1|| & \langle v_2, e_1 \rangle & \dots & \langle v_n, e_1 \rangle \\ 0 & ||w_2|| & \dots & \langle v_n, e_2 \rangle \\ \vdots & \vdots & \ddots & \vdots \\ 0 & 0 & \dots & ||w_n|| \end{bmatrix}$ zgornje trikotna.

### Izrek (Razcep Choleskega)

Če je matrika $A$ pozitivno definitna, potem obstaja taka zgornje trikotna matrika $R$, da je $A = R^*R$.

**Dokaz (prvi del):**
Če je matrika $A$ pozitivno definitna, potem obstaja taka obrnljiva matrika $B$ (npr. $B=A^{1/2}$), da velja $A = B^*B$. Naj bo $B = QR$ (po QR razcepu), kjer je $Q$ unitarna in $R$ zgornje trikotna. Potem je $A = (QR)^*(QR) = R^*Q^*QR = R^*IR = R^*R$.

**Opomba.** Matriko $R$ v razcepu Choleskega lahko izračunamo tudi z naslednjim algoritmom. Začnimo z $A_1 := A$.
Recimo, da je $A_i$ pozitivno definitna matrika oblike:
$$ A_i = \begin{bmatrix} I_{i-1} & 0 & 0 \\ 0 & a_{i,i} & \mathbf{b}_i^* \\ 0 & \mathbf{b}_i & B_i \end{bmatrix} $$
Potem je $a_{i,i} > 0$, torej lahko definiramo obrnljivo zgornje trikotno matriko:
$$ R_i = \begin{bmatrix} I_{i-1} & 0 & 0 \\ 0 & \sqrt{a_{i,i}} & \frac{1}{\sqrt{a_{i,i}}}\mathbf{b}_i^* \\ 0 & 0 & I_{n-i} \end{bmatrix} $$
Potem velja $A_i = R_i^* A_{i+1} R_i$, kjer je
$$ A_{i+1} = \begin{bmatrix} I_{i-1} & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & B_i - \frac{1}{a_{i,i}}\mathbf{b}_i\mathbf{b}_i^* \end{bmatrix} $$
Ta postopek ponovimo $n$-krat in upoštevamo, da je $A_{n+1} = I$. Dobimo $A = R^*R$, kjer je $R = R_n \dots R_1$.

### Drugi dokaz QR razcepa (iz razcepa Choleskega)

Naj bo $A$ obrnljiva matrika. Potem je matrika $A^*A$ pozitivno definitna, torej ima razcep Choleskega $A^*A = R^*R$, kjer je $R$ zgornje trikotna matrika. Pokažimo, da je matrika $Q := AR^{-1}$ unitarna.
To sledi iz $Q^*Q = (AR^{-1})^* (AR^{-1}) = (R^{-1})^* A^* A R^{-1} = (R^{-1})^* R^* R R^{-1}$.
Ker je $R$ zgornje trikotna in obrnljiva, je $R^*$ spodnje trikotna in obrnljiva. Tudi $R^{-1}$ je zgornje trikotna in $(R^{-1})^* = (R^*)^{-1}$ je spodnje trikotna.
$Q^*Q = (R^{-1})^* R^* R R^{-1} = ((R^*)^{-1}R^*)(RR^{-1}) = I \cdot I = I$.
Iz $Q = AR^{-1}$ sledi, da je $A = QR$.

## 4. Singularni razcep (=SVD)

V tem in naslednjih razdelkih bomo imeli opravka s pravokotnimi (ne nujno kvadratnimi) diagonalnimi matrikami.

### Definicija pravokotne diagonalne matrike

Pravokotna matrika $A = [a_{i,j}]$ je **diagonalna**, če je $a_{i,j} = 0$ za vsaka $i \ne j$.

### Primera pravokotnih diagonalnih matrik

Pravokotni matriki
$\begin{bmatrix} 1 & 0 & 0 & 0 \\ 0 & 2 & 0 & 0 \\ 0 & 0 & 3 & 0 \end{bmatrix}$ in $\begin{bmatrix} 1 & 0 & 0 \\ 0 & 2 & 0 \\ 0 & 0 & 3 \\ 0 & 0 & 0 \end{bmatrix}$
sta diagonalni.

### Izrek o singularnem razcepu (SVD)

Naj bo $A$ kompleksna $m \times n$ matrika. Potem obstajajo taka unitarna $m \times m$ matrika $Q_1$, taka unitarna $n \times n$ matrika $Q_2$ in taka diagonalna $m \times n$ matrika $D$, kjer $d_{i,i} \ge 0$ za vsak $i = 1, \dots, \min\{m, n\}$, da velja
$$ A = Q_1 D Q_2^{-1} $$
Če je $A$ realna matrika, potem lahko matriki $Q_1$ in $Q_2$ izberemo tako, da sta obe realni (se pravi ortogonalni). Matrika $D$ je že itak realna.

**Opomba:** Singularnemu razcepu se v angleščini reče "singular value decomposition", kar se okrajša v "SVD".

**Opomba:** Iz $A = Q_1DQ_2^{-1} = Q_1DQ_2^*$ sledi, da je:
$$ A^*A = (Q_1DQ_2^*)^*(Q_1DQ_2^*) = Q_2^{**}D^*Q_1^*Q_1DQ_2^* = Q_2D^*IDQ_2^* = Q_2D^*DQ_2^* \quad (1) $$
$$ AA^* = Q_1DQ_2^*(Q_1DQ_2^*)^* = Q_1DQ_2^*Q_2^{**}D^*Q_1^* = Q_1DID^*Q_1^* = Q_1DD^*Q_1^* \quad (2) $$
Iz (1) sledi, da so stolpci $Q_2$ ortonormirana baza iz lastnih vektorjev matrike $A^*A$. Podobno iz (2) sledi, da so stolpci $Q_1$ ortonormirana baza iz lastnih vektorjev matrike $AA^*$.
Če je $m \ge n$, je:
$$ D^*D = \begin{bmatrix} d_{1,1}^2 & & & 0 \\ & \ddots & & \\ & & d_{n,n}^2 & \\ 0 & & & 0 \end{bmatrix} $$
$$ DD^* = \begin{bmatrix} d_{1,1}^2 & & 0 \\ & \ddots & \\ 0 & & d_{n,n}^2 \end{bmatrix} $$
kjer so $d_{1,1}^2, \dots, d_{n,n}^2$ lastne vrednosti matrike $A^*A$, torej so $d_{1,1}, \dots, d_{n,n}$ singularne vrednosti matrike $A$. Podobno je v primerih $m=n$ in $m<n$.

**Dokaz izreka (skica):** Naj bo $A$ kompleksna $m \times n$ matrika.
Konstrukcijo singularnega razcepa za $A$ razdelimo v štiri dele: konstrukcije $Q_2$, $D$ in $Q_1$ ter dokaz formule $AQ_2 = Q_1D$.

1.  **Konstrukcija matrike $Q_2$.** Najprej uredimo lastne vrednosti matrike $A^*A$ po velikosti. Nato izračunamo pripadajoče lastne podprostore. Za vsakega od njih določimo ortonormirano bazo. Elemente v uniji teh baz označimo z $v_1, \dots, v_n$, pripadajoče lastne vrednosti pa z $\lambda_1, \dots, \lambda_n$. Velja torej $A^*Av_i = \lambda_i v_i$ za vsak $i = 1, \dots, n$ in $\lambda_1 \ge \dots \ge \lambda_n \ge 0$.
    Definirajmo $Q_2 = \begin{bmatrix} v_1 & \dots & v_n \end{bmatrix}$. Ker je $v_1, \dots, v_n$ ortonormirana baza za $\mathbb{C}^n$, je matrika $Q_2$ unitarna.

2.  **Konstrukcija matrike $D$.** Naj bo $r$ rang matrike $A$. Vemo, da je $r$ enak rangu matrike $A^*A$, zato velja $\lambda_1 \ge \dots \ge \lambda_r > 0$, $\lambda_{r+1} = \dots = \lambda_n = 0$.
    Naj bo $\sigma_i = \sqrt{\lambda_i}$ za $i = 1, \dots, r$ in naj bo $D$ diagonalna $m \times n$ matrika, ki ima po diagonali $\sigma_1, \dots, \sigma_r$ in morda ničle. Eksplicitno:
    $$ D = \begin{bmatrix} \sigma_1 & & & & & 0 \\ & \ddots & & & & \\ & & \sigma_r & & & \\ & & & 0 & & \\ & & & & \ddots & \\ 0 & & & & & 0 \end{bmatrix} $$

3.  **Konstrukcija matrike $Q_1$.** Za $i = 1, \dots, r$ definirajmo $u_i = \frac{1}{\sigma_i} Av_i$.
    Pokažimo, da ti vektorji tvorijo ortonormirano množico v $\mathbb{C}^m$. Velja:
    $\langle u_i, u_j \rangle = \left\langle \frac{1}{\sigma_i} Av_i, \frac{1}{\sigma_j} Av_j \right\rangle = \frac{1}{\sigma_i \sigma_j} \langle Av_i, Av_j \rangle = \frac{1}{\sigma_i \sigma_j} \langle A^*Av_i, v_j \rangle = \frac{1}{\sigma_i \sigma_j} \langle \lambda_i v_i, v_j \rangle = \frac{\lambda_i}{\sigma_i \sigma_j} \langle v_i, v_j \rangle$.
    Ker so $v_i$ ortonormirani, je $\langle v_i, v_j \rangle = \delta_{ij}$.
    Torej $\langle u_i, u_j \rangle = \frac{\lambda_i}{\sigma_i \sigma_j} \delta_{ij} = \frac{\sigma_i^2}{\sigma_i \sigma_j} \delta_{ij} = \delta_{ij}$.
    Za vsaka $i, j = 1, \dots, r$, ti vektorji $u_i$ tvorijo ortonormirano množico. Naj bo $u_{r+1}, \dots, u_m$ dopolnitev ortonormirane množice $u_1, \dots, u_r$ do ortonormirane baze za $\mathbb{C}^m$. Definirajmo $Q_1 = \begin{bmatrix} u_1 & \dots & u_r & u_{r+1} & \dots & u_m \end{bmatrix}$.

4.  **Dokaz formule $AQ_2 = Q_1D$.** Iz $Q_2 = \begin{bmatrix} v_1 & \dots & v_r & v_{r+1} & \dots & v_n \end{bmatrix}$ sledi, da je:
    $$ AQ_2 = \begin{bmatrix} Av_1 & \dots & Av_r & Av_{r+1} & \dots & Av_n \end{bmatrix} $$
    Pri drugem delu matrike ($i = r+1, \dots, n$) smo upoštevali, da velja $A^*Av_i = \lambda_i v_i = 0$, odkoder zaradi $\mathrm{Ker} A^*A = \mathrm{Ker} A$ sledi $Av_i = 0$. Torej:
    $$ AQ_2 = \begin{bmatrix} Av_1 & \dots & Av_r & 0 & \dots & 0 \end{bmatrix} $$
    Iz $Q_1 = \begin{bmatrix} u_1 & \dots & u_r & u_{r+1} & \dots & u_m \end{bmatrix}$ in definicije $D$ sledi, da je:
    $$ Q_1D = \begin{bmatrix} \sigma_1 u_1 & \dots & \sigma_r u_r & 0 & \dots & 0 \end{bmatrix} $$
    Pri drugem enačaju smo upoštevali, da je $u_i = \frac{1}{\sigma_i} Av_i$, kar pomeni $\sigma_i u_i = Av_i$ za $i = 1, \dots, r$. Torej $AQ_2 = Q_1D$.

### Posledica (Geometrijski pomen singularnega razcepa)

Naj bo $A$ realna $m \times n$ matrika in naj bo $K$ enotska krogla v $\mathbb{R}^n$ ($K = \{v \in \mathbb{R}^n : ||v|| \le 1\}$). Potem je množica $\{Av \mid v \in K\}$ elipsoid v podprostoru $\mathrm{Im} A \subset \mathbb{R}^m$. Polosi tega elipsoida so ravno neničelne singularne vrednosti matrike $A$.

**Dokaz (skica):**
Naj bo $A = Q_1DQ_2^{-1}$ singularni razcep matrike $A$, ki smo ga konstruirali v dokazu prejšnjega izreka. Vzemimo poljuben vektor $v$ iz enotske krogle v $\mathbb{R}^n$ in ga razvijmo po stolpcih $v_1, \dots, v_n$ matrike $Q_2$. Velja $v = x_1 v_1 + \dots + x_n v_n$, kjer $x_1^2 + \dots + x_n^2 \le 1$.
Naj bodo $\sigma_1, \dots, \sigma_r$ neničelni elementi matrike $D$ in naj bodo $u_1, \dots, u_r$ začetni stolpci matrike $Q_1$. Potem velja:
$Av = AQ_2Q_2^{-1}v = Q_1DQ_2^{-1}v$. Ker je $Q_2^{-1}$ unitarna matrika, $Q_2^{-1}v$ je tudi v enotski krogli. Let $v' = Q_2^{-1}v$, then $v' = x_1' v_1 + \dots + x_n' v_n$ where $\sum (x_i')^2 \le 1$.
Then $Av = Q_1 D v' = Q_1 D \sum x_i' e_i = Q_1 \sum x_i' \sigma_i e_i = \sum_{i=1}^r x_i' \sigma_i u_i$.
Definirajmo $y_i = x_i' \sigma_i$. Potem $Av = y_1 u_1 + \dots + y_r u_r$.
Velja $\sum_{i=1}^r \left(\frac{y_i}{\sigma_i}\right)^2 = \sum_{i=1}^r (x_i')^2 \le \sum_{i=1}^n (x_i')^2 \le 1$.
Torej $Av$ res leži v $r$-razsežnem elipsoidu v $\mathrm{Im} A$ s polosmi $\sigma_1, \dots, \sigma_r$.
Velja tudi obratno. Vsak element $y_1 u_1 + \dots + y_r u_r$ tega elipsoida je slika nekega elementa iz enotske krogle, namreč slika od $\frac{y_1}{\sigma_1}v_1 + \dots + \frac{y_r}{\sigma_r}v_r$.


## 5. Primeri singularnega razcepa

### Primer (izračun singularnega razcepa)

Izračunajmo singularni razcep matrike $A = \begin{bmatrix} 1 & 1 & -1 & -1 \\ -1 & 0 & 1 & 0 \\ 0 & -1 & 0 & 1 \end{bmatrix}$.

**Rešitev:**
Najprej izračunamo lastne vrednosti in lastne vektorje matrike $A^TA$.
$A^TA = \begin{bmatrix} 1 & -1 & 0 \\ 1 & 0 & -1 \\ -1 & 1 & 0 \\ -1 & 0 & 1 \end{bmatrix} \begin{bmatrix} 1 & 1 & -1 & -1 \\ -1 & 0 & 1 & 0 \\ 0 & -1 & 0 & 1 \end{bmatrix} = \begin{bmatrix} 2 & 1 & -2 & -1 \\ 1 & 2 & -1 & -2 \\ -2 & -1 & 2 & 1 \\ -1 & -2 & 1 & 2 \end{bmatrix}$.
Lastni polinom matrike $A^TA$ je $\det(A^TA - \lambda I) = \lambda^2(\lambda - 2)(\lambda - 6)$.
Neničelne singularne vrednosti matrike $A$ sta $\sigma_1 = \sqrt{6}$ in $\sigma_2 = \sqrt{2}$.

Lastni vektorji, ki pripadajo lastnim vrednostim 6, 2 in 0 so:
*   Za $\lambda = 6$: $w_1 = \begin{bmatrix} 1 \\ 1 \\ -1 \\ -1 \end{bmatrix}$
*   Za $\lambda = 2$: $w_2 = \begin{bmatrix} 1 \\ -1 \\ -1 \\ 1 \end{bmatrix}$
*   Za $\lambda = 0$: lastni podprostor je dvo-dimenzionalen, tvorita ga $w_3 = \begin{bmatrix} 1 \\ 0 \\ 1 \\ 0 \end{bmatrix}$ in $w_4 = \begin{bmatrix} 0 \\ 1 \\ 0 \\ 1 \end{bmatrix}$. Na srečo sta že ortogonalna, zato ne rabimo Gram-Schmidtove ortogonalizacije.

Odtod dobimo ortonormirano bazo za $\mathbb{R}^4$:
$v_1 = \frac{w_1}{||w_1||} = \frac{1}{2}\begin{bmatrix} 1 \\ 1 \\ -1 \\ -1 \end{bmatrix}$
$v_2 = \frac{w_2}{||w_2||} = \frac{1}{2}\begin{bmatrix} 1 \\ -1 \\ -1 \\ 1 \end{bmatrix}$
$v_3 = \frac{w_3}{||w_3||} = \frac{1}{\sqrt{2}}\begin{bmatrix} 1 \\ 0 \\ 1 \\ 0 \end{bmatrix}$
$v_4 = \frac{w_4}{||w_4||} = \frac{1}{\sqrt{2}}\begin{bmatrix} 0 \\ 1 \\ 0 \\ 1 \end{bmatrix}$

Tvorimo matriki $Q_2 = \begin{bmatrix} v_1 & v_2 & v_3 & v_4 \end{bmatrix}$ in $D$:
$$ Q_2 = \begin{bmatrix} 1/2 & 1/2 & 1/\sqrt{2} & 0 \\ 1/2 & -1/2 & 0 & 1/\sqrt{2} \\ -1/2 & -1/2 & 1/\sqrt{2} & 0 \\ -1/2 & 1/2 & 0 & 1/\sqrt{2} \end{bmatrix} $$
$$ D = \begin{bmatrix} \sqrt{6} & 0 & 0 & 0 \\ 0 & \sqrt{2} & 0 & 0 \\ 0 & 0 & 0 & 0 \end{bmatrix} $$

Ostane nam še konstrukcija matrike $Q_1$. Najprej izračunajmo vektorja $u_i = \frac{1}{\sigma_i}Av_i$:
$u_1 = \frac{1}{\sqrt{6}} A v_1 = \frac{1}{\sqrt{6}} \begin{bmatrix} 1 & 1 & -1 & -1 \\ -1 & 0 & 1 & 0 \\ 0 & -1 & 0 & 1 \end{bmatrix} \frac{1}{2}\begin{bmatrix} 1 \\ 1 \\ -1 \\ -1 \end{bmatrix} = \frac{1}{2\sqrt{6}} \begin{bmatrix} 4 \\ -2 \\ 0 \end{bmatrix} = \frac{1}{\sqrt{6}}\begin{bmatrix} 2 \\ -1 \\ 0 \end{bmatrix}$.
$u_2 = \frac{1}{\sqrt{2}} A v_2 = \frac{1}{\sqrt{2}} \begin{bmatrix} 1 & 1 & -1 & -1 \\ -1 & 0 & 1 & 0 \\ 0 & -1 & 0 & 1 \end{bmatrix} \frac{1}{2}\begin{bmatrix} 1 \\ -1 \\ -1 \\ 1 \end{bmatrix} = \frac{1}{2\sqrt{2}} \begin{bmatrix} 0 \\ -2 \\ 2 \end{bmatrix} = \frac{1}{\sqrt{2}}\begin{bmatrix} 0 \\ -1 \\ 1 \end{bmatrix}$.
Poiščimo sedaj tak vektor $u_3$, ki bo $u_1$ in $u_2$ dopolnil do ortonormirane baze za $\mathbb{R}^3$. Rešimo enačbo $AA^T u_3 = 0$ in rešitev normirajmo.
$AA^T = \begin{bmatrix} 1 & 1 & -1 & -1 \\ -1 & 0 & 1 & 0 \\ 0 & -1 & 0 & 1 \end{bmatrix} \begin{bmatrix} 1 & -1 & 0 \\ 1 & 0 & -1 \\ -1 & 1 & 0 \\ -1 & 0 & 1 \end{bmatrix} = \begin{bmatrix} 4 & -2 & 0 \\ -2 & 2 & -1 \\ 0 & -1 & 2 \end{bmatrix}$.
$\det(AA^T - \lambda I) = \det \begin{bmatrix} 4-\lambda & -2 & 0 \\ -2 & 2-\lambda & -1 \\ 0 & -1 & 2-\lambda \end{bmatrix} = (4-\lambda)((2-\lambda)^2-1) - (-2)(-2(2-\lambda)) = (4-\lambda)(4-4\lambda+\lambda^2-1) - 4(2-\lambda) = (4-\lambda)(\lambda^2-4\lambda+3) - 8 + 4\lambda = 4\lambda^2-16\lambda+12-\lambda^3+4\lambda^2-3\lambda - 8 + 4\lambda = -\lambda^3+8\lambda^2-15\lambda+4$.
$\lambda=0$ je tudi lastna vrednost za $AA^T$.
$AA^T u_3 = 0 \implies \begin{bmatrix} 4 & -2 & 0 \\ -2 & 2 & -1 \\ 0 & -1 & 2 \end{bmatrix} \begin{bmatrix} x \\ y \\ z \end{bmatrix} = \begin{bmatrix} 0 \\ 0 \\ 0 \end{bmatrix}$.
$4x - 2y = 0 \implies y = 2x$.
$-2x + 2(2x) - z = 0 \implies -2x + 4x - z = 0 \implies z = 2x$.
Izberemo $x=1$, potem $y=2, z=2$. Torej $w_3' = \begin{bmatrix} 1 \\ 2 \\ 2 \end{bmatrix}$. Normiramo ga: $u_3 = \frac{1}{3}\begin{bmatrix} 1 \\ 2 \\ 2 \end{bmatrix}$.
Ker so $u_1, u_2$ in $u_3$ lastni vektorji matrike $AA^T$, ki pripadajo različnim lastnim vrednostim 6, 2 in 0, so paroma ortogonalni. Normiramo $u_3$: $u_3 = \frac{1}{\sqrt{1^2+2^2+2^2}} \begin{bmatrix} 1 \\ 2 \\ 2 \end{bmatrix} = \frac{1}{3} \begin{bmatrix} 1 \\ 2 \\ 2 \end{bmatrix}$.
Sedaj lahko tvorimo $Q_1 = \begin{bmatrix} u_1 & u_2 & u_3 \end{bmatrix}$:
$$ Q_1 = \begin{bmatrix} 2/\sqrt{6} & 0 & 1/3 \\ -1/\sqrt{6} & -1/\sqrt{2} & 2/3 \\ 0 & 1/\sqrt{2} & 2/3 \end{bmatrix} $$
Konstruirali smo razcep $A = Q_1DQ_2^T$, kjer sta $Q_1$ in $Q_2$ ortogonalni matriki, $D$ pa diagonalna matrika.

### Primer (singularni razcep normalne matrike)

Pojasni kako preprosto izračunamo singularni razcep normalne matrike.

**Rešitev:**
Naj bo $A$ $n \times n$ matrika, ki zadošča $A^*A = AA^*$.
Najprej izračunamo singularne vrednosti matrike $A$. Vemo, da ima $A$ $n$ linearno neodvisnih lastnih vektorjev $v_1, \dots, v_n$. Pripadajoče lastne vrednosti označimo z $\lambda_1, \dots, \lambda_n$. Ker za normalne matrike iz $Av_i = \lambda_i v_i$ sledi $A^*v_i = \overline{\lambda_i}v_i$, imamo $A^*Av_i = A^*(\lambda_i v_i) = \lambda_i A^*v_i = \lambda_i \overline{\lambda_i} v_i = |\lambda_i|^2 v_i$ za vsak $i = 1, \dots, n$.
Torej so $\sigma_i := \sqrt{|\lambda_i|^2} = |\lambda_i|$ vse singularne vrednosti $A$.
Permutirajmo vektorje $v_1, \dots, v_n$ tako, da velja $|\lambda_1| \ge \dots \ge |\lambda_r| > 0$, $\lambda_{r+1} = \dots = \lambda_n = 0$.
Označimo $Q_2 = \begin{bmatrix} v_1 & \dots & v_n \end{bmatrix}$.
Upoštevamo, da za $i = 1, \dots, r$ velja $\sigma_i = |\lambda_i|$ in dobimo $u_i = \frac{1}{\sigma_i} Av_i = \frac{1}{|\lambda_i|} \lambda_i v_i = \frac{\lambda_i}{|\lambda_i|} v_i$.
Za dopolnitev do baze $\mathbb{C}^n$ lahko vzamemo kar $v_{r+1}, \dots, v_n$. Torej je $Q_1 = \begin{bmatrix} \frac{\lambda_1}{|\lambda_1|} v_1 & \dots & \frac{\lambda_r}{|\lambda_r|} v_r & v_{r+1} & \dots & v_n \end{bmatrix}$.
Naj bo $D$ matrika, ki ima po diagonali $|\lambda_1|, \dots, |\lambda_n|$. Singularni razcep je $A = Q_1 |D| Q_2^*$.

**Dodatek: Primerjava singularnega razcepa z lastnim razcepom**
Za normalno matriko $A$ je $A = Q_2 D Q_2^*$ (lastni razcep), kjer je $D$ diagonalna matrika lastnih vrednosti $\lambda_i$.
Singularni razcep je $A = Q_1 |D| Q_2^*$.
Označimo s $\mathrm{sgn}(D)$ matriko, ki ima po diagonali $\frac{\lambda_1}{|\lambda_1|}, \dots, \frac{\lambda_r}{|\lambda_r|}, 1, \dots, 1$.
Opazimo, da je $D = \mathrm{sgn}(D)|D|$ in $Q_1 = Q_2 \mathrm{sgn}(D)$, torej je $A = Q_2 D Q_2^* = Q_2 \mathrm{sgn}(D)|D| Q_2^* = Q_2 \mathrm{sgn}(D) (\mathrm{sgn}(D))^* |D| Q_2^* = Q_1 |D| Q_2^*$.
Za pozitivno semidefinitne matrike se oba razcepa ujemata (ker so lastne vrednosti že nenegativne, torej $\lambda_i = |\lambda_i|$ in $\mathrm{sgn}(D) = I$).

### Posledica (Singularni razcep za linearne preslikave)

Za vsako linearno preslikavo $L: U \to V$ med končnorazsežnima vektorskima prostoroma s skalarnim produktom obstaja taka ortonormirana baza $\mathcal{B}$ za $U$ in taka ortonormirana baza $\mathcal{C}$ za $V$, da je matrika $[L]_{\mathcal{C} \leftarrow \mathcal{B}}$ diagonalna z elementi $\ge 0$.

**Dokaz:**
Najprej izberemo poljubni ortonormirani bazi $\mathcal{B}' = \{b_1', \dots, b_n'\}$ za $U$ in $\mathcal{C}' = \{c_1', \dots, c_m'\}$ za $V$. Potem naredimo singularni razcep matrike $[L]_{\mathcal{C}' \leftarrow \mathcal{B}'} = Q_1DQ_2^{-1}$.
Če je $Q_2 = [r_{i,j}]$, potem z $b_i = \sum_{k=1}^n r_{k,i}b_k'$ definiramo novo bazo $\mathcal{B}$ za $U$. Ker so stolpci matrike $Q_2$ ortonormirani, je tudi $\mathcal{B}$ ortonormirana baza.
Podobno definiramo tudi novo bazo $\mathcal{C}$ za $V$ in dokažemo ortonormiranost.
Velja $[L]_{\mathcal{C} \leftarrow \mathcal{B}} = P_{\mathcal{C} \leftarrow \mathcal{C}'} [L]_{\mathcal{C}' \leftarrow \mathcal{B}'} P_{\mathcal{B}' \leftarrow \mathcal{B}} = Q_1^{-1} (Q_1DQ_2^{-1}) Q_2 = D$.

**Opomba:** Če ne zahtevamo ortonormiranosti baz $\mathcal{B}$ in $\mathcal{C}$, potem ju lahko izberemo tako, da ima $[L]_{\mathcal{C} \leftarrow \mathcal{B}}$ po diagonali enke in ničle, drugod pa ničle.

### Posledica (Še ena reformulacija singularnega razcepa)

Za vsako matriko $A \in \mathbb{C}^{m \times n}$ ranga $r$ obstaja taka ortonormirana množica $u_1, \dots, u_r$ v $\mathbb{C}^m$ in taka ortonormirana množica $v_1, \dots, v_r$ v $\mathbb{C}^n$, da velja
$$ A = \sigma_1 u_1 v_1^* + \dots + \sigma_r u_r v_r^* $$
kjer so $\sigma_1, \dots, \sigma_r$ neničelne singularne vrednosti matrike $A$.

**Dokaz:**
Sledi iz singularnega razcepa $A = Q_1DQ_2^*$ in formule:
$Q_1 = \begin{bmatrix} u_1 & \dots & u_r & \dots & u_m \end{bmatrix}$ in $Q_2^* = \begin{bmatrix} v_1^* \\ \vdots \\ v_r^* \\ \vdots \\ v_n^* \end{bmatrix}$.
Potem $Q_1 D Q_2^* = \begin{bmatrix} u_1 & \dots & u_m \end{bmatrix} \begin{bmatrix} \sigma_1 & & & & \\ & \ddots & & & \\ & & \sigma_r & & \\ & & & \ddots & \\ & & & & 0 \end{bmatrix} \begin{bmatrix} v_1^* \\ \vdots \\ v_n^* \end{bmatrix} = \sum_{i=1}^r \sigma_i u_i v_i^*$.

## 6. Aproksimacija z matrikami nizkega ranga

Naj bo $\mathbb{C}^{m \times n}$ vektorski prostor vseh kompleksnih $m \times n$ matrik. Na tem vektorskem prostoru lahko definiramo skalarni produkt z
$$ \langle B, C \rangle := \mathrm{Sled}(BC^*) = \sum_{i=1}^m \sum_{j=1}^n b_{i,j}\overline{c_{i,j}} $$
Pripadajoča norma je $||B|| := \sqrt{\langle B, B \rangle} = \sqrt{\sum_{i=1}^m \sum_{j=1}^n |b_{i,j}|^2}$. Tej normi pravimo **Frobeniusova norma**. Pogosto se označuje z $||B||_F$.

### Trditev

Če je $Q_1$ unitarna $m \times m$ matrika in $Q_2$ unitarna $n \times n$ matrika, potem za vsako $m \times n$ matriko $A$ velja $||Q_1AQ_2||_F = ||A||_F$.

**Dokaz:**
Upoštevamo definicijo norme in lastnost $\mathrm{Sled}(XY) = \mathrm{Sled}(YX)$.
$||Q_1AQ_2||_F^2 = \mathrm{Sled}((Q_1AQ_2)(Q_1AQ_2)^*) = \mathrm{Sled}(Q_1AQ_2Q_2^*A^*Q_1^*) = \mathrm{Sled}(Q_1AI A^*Q_1^*) = \mathrm{Sled}(Q_1AA^*Q_1^*)$.
Zaradi ciklične lastnosti sledi: $\mathrm{Sled}(Q_1AA^*Q_1^*) = \mathrm{Sled}(AA^*Q_1^*Q_1) = \mathrm{Sled}(AA^*I) = \mathrm{Sled}(AA^*) = ||A||_F^2$.

### Problem (Aproksimacija matrike)

Naj bo $A \in \mathbb{C}^{m \times n}$ dana matrika in $k \in \mathbb{N}$ dano število. Iščemo tako matriko $A_k$ ranga $\le k$, da za vsako drugo matriko $B$ ranga $\le k$ velja $||A - A_k||_F \le ||A - B||_F$.
To pomeni, da se med vsemi matrikami v $\mathbb{C}^{m \times n}$, ki so ranga $\le k$, matrika $A_k$ najbolje prilega matriki $A$. Odgovor nam daje naslednji izrek.

### Izrek (Eckart & Young 1936)

Naj bo $A \in \mathbb{C}^{m \times n}$ matrika ranga $r$ in naj bo $k < r$. Naj bo $A = Q_1DQ_2^*$ singularni razcep matrike $A$, kjer $\sigma_1 \ge \dots \ge \sigma_r > 0$. Definirajmo matriko $D_k$ tako, da v $D$ zamenjamo $\sigma_{k+1}, \dots, \sigma_r$ z nič. Med vsemi matrikami v $\mathbb{C}^{m \times n}$, ki so ranga $\le k$, se $A_k := Q_1D_kQ_2^*$ najbolje prilega $A$.

**Dokaz (skica):**
Najprej izračunajmo razdaljo med $A$ in $A_k$:
$||A - A_k||_F^2 = ||Q_1DQ_2^* - Q_1D_kQ_2^*||_F^2 = ||Q_1(D - D_k)Q_2^*||_F^2$.
Zaradi unitarnosti $Q_1, Q_2$ in trditve o Frobeniusovi normi, je to enako
$||D - D_k||_F^2 = \sum_{i=1}^m \sum_{j=1}^n |(D - D_k)_{ij}|^2 = \sum_{i=k+1}^r \sigma_i^2$.

Naj bo $B$ $m \times n$ matrika ranga $\le k$, ki se najbolje prilega matriki $A$. Radi bi dokazali, da je $||A - B||_F^2 = \sigma_{k+1}^2 + \dots + \sigma_r^2$.
Začnimo tokrat s singularnim razcepom matrike $B$:
$B = U \begin{bmatrix} \Sigma & 0 \\ 0 & 0 \end{bmatrix} V^*$,
kjer je $\Sigma$ diagonalna $k \times k$ matrika (singularne vrednosti $\ne 0$), in $U, V$ unitarni matriki.
Pišimo $A = U(U^*AV)V^* = U \begin{bmatrix} E & F \\ G & H \end{bmatrix} V^*$, kjer je $E$ $k \times k$ matrika.
Iz definicije norme in lastnosti $||UXV^*|| = ||X||$ sledi:
$||A - B||_F^2 = ||U \begin{bmatrix} E & F \\ G & H \end{bmatrix} V^* - U \begin{bmatrix} \Sigma & 0 \\ 0 & 0 \end{bmatrix} V^*||_F^2 = || \begin{bmatrix} E-\Sigma & F \\ G & H \end{bmatrix} ||_F^2 = ||E-\Sigma||_F^2 + ||F||_F^2 + ||G||_F^2 + ||H||_F^2$.
Naj bo $C = U \begin{bmatrix} E & F \\ 0 & 0 \end{bmatrix} V^*$ in $C' = U \begin{bmatrix} E & 0 \\ G & 0 \end{bmatrix} V^*$. Rang $C$ in $C'$ je $\le k$.
$||A - C||_F^2 = ||\begin{bmatrix} 0 & 0 \\ G & H \end{bmatrix}||_F^2 = ||G||_F^2 + ||H||_F^2$.
$||A - C'||_F^2 = ||\begin{bmatrix} 0 & F \\ 0 & H \end{bmatrix}||_F^2 = ||F||_F^2 + ||H||_F^2$.
Ker se matrika $B$ najbolje prilega $A$, so vsi elementi $J$ pod vsemi elementi $D$.
$||A - B||_F^2 \le ||A - C||_F^2$ in $||A - B||_F^2 \le ||A - C'||_F^2$.
Odtod sledi $||E-\Sigma||_F^2 + ||F||_F^2 \le 0$ in $||E-\Sigma||_F^2 + ||G||_F^2 \le 0$.
Torej $||E-\Sigma||_F^2 = ||F||_F^2 = ||G||_F^2 = 0$; se pravi $E=\Sigma$ in $F=G=0$.
Naj bo $H = WJZ^*$ singularni razcep matrike $H$.
Singularni razcep matrike $B$ popravimo v $B = U \begin{bmatrix} \Sigma & 0 \\ 0 & 0 \end{bmatrix} V^*$.
Če je $H$ matrika rang $k_H$, $J$ je diagonalna matrika $k_H \times k_H$.
Ker se $B$ najbolje prilega $A$, so vsi elementi $J$ pod vsemi elementi $D$.
Torej je (1) singularni razcep matrike $A$. Iz (1) in (2) sedaj sledi $||A - B||_F^2 = \sigma_{k+1}^2 + \dots + \sigma_r^2$.

**Uporaba pri zgoščevanju slik:**
Recimo, da imamo sliko velikosti $m \times n$. Za vsako točko si moramo zapomniti njeno barvo, se pravi neko realno število (odtenek sive ali kombinacija odtenkov modre, zelene in rdeče). Dobimo torej realno $m \times n$ matriko $A$.
Naredimo singularni razcep in si zapomnimo prvih $k$ singularnih vrednosti, ter vektorje $u_1, \dots, u_k$ in $v_1, \dots, v_k$ za katere velja
$A_k = \sigma_1 u_1 v_1^T + \dots + \sigma_k u_k v_k^T$.
Vektorji $u_i$ so dolžine $m$, vektorji $v_i$ pa dolžine $n$, torej je $A_k$ podana z $k(m + n + 1)$ podatki. Razmerje z začetno količino podatkov je $\frac{k(m + n + 1)}{mn} = k\left(\frac{1}{n} + \frac{1}{m} + \frac{1}{mn}\right)$, kjer lahko zadnji člen zanemarimo. Če je recimo $m = n = 1000$ in $k = 50$, si moramo zapomniti samo $10\%$ od začetne količine podatkov.

## 7. Psevdoinverz

Kot ponavadi, se omejimo na realna in kompleksna števila.
Za diagonalno $m \times n$ matriko $D$ z neničelnimi elementi $\sigma_1, \dots, \sigma_r$ definiramo njen **psevdoinverz** $D^+$ kot diagonalno $n \times m$ matriko z neničelnimi elementi $\frac{1}{\sigma_1}, \dots, \frac{1}{\sigma_r}$.

### Primer

$D = \begin{bmatrix} \sigma_1 & 0 & 0 & 0 \\ 0 & \sigma_2 & 0 & 0 \\ 0 & 0 & 0 & 0 \end{bmatrix}$. Potem $D^+ = \begin{bmatrix} 1/\sigma_1 & 0 & 0 \\ 0 & 1/\sigma_2 & 0 \\ 0 & 0 & 0 \\ 0 & 0 & 0 \end{bmatrix}$.

**Opomba:** Očitno velja $(D^+)^+ = D$ za vsako diagonalno matriko $D$.
**Opomba:** Če je $D$ obrnljiva, potem velja $D^+ = D^{-1}$.

Za splošno matriko $A$ najprej izračunamo singularni razcep $A = Q_1DQ_2^*$ in potem definiramo
$$ A^+ = Q_2D^+Q_1^* $$

**Opomba:** Za vsako matriko $A$ je $(A^+)^+ = Q_2(D^+)^+Q_1^* = Q_2DQ_1^* = A$.
**Opomba:** Če je matrika $A$ obrnljiva, potem velja $A^+ = A^{-1}$.

### Primer

Izračunajmo psevdoinverz matrike $A = \begin{bmatrix} 1 & 1 & -1 & -1 \\ -1 & 0 & 1 & 0 \\ 0 & -1 & 0 & 1 \end{bmatrix}$.

**Rešitev:**
Najprej izračunamo singularni razcep matrike $A$:
$A = Q_1 D Q_2^T$, kjer
$$ Q_1 = \begin{bmatrix} 2/\sqrt{6} & 0 & 1/3 \\ -1/\sqrt{6} & -1/\sqrt{2} & 2/3 \\ 0 & 1/\sqrt{2} & 2/3 \end{bmatrix} $$
$$ D = \begin{bmatrix} \sqrt{6} & 0 & 0 & 0 \\ 0 & \sqrt{2} & 0 & 0 \\ 0 & 0 & 0 & 0 \end{bmatrix} $$
$$ Q_2 = \begin{bmatrix} 1/2 & 1/2 & 1/\sqrt{2} & 0 \\ 1/2 & -1/2 & 0 & 1/\sqrt{2} \\ -1/2 & -1/2 & 1/\sqrt{2} & 0 \\ -1/2 & 1/2 & 0 & 1/\sqrt{2} \end{bmatrix} $$
Potem je
$$ D^+ = \begin{bmatrix} 1/\sqrt{6} & 0 & 0 \\ 0 & 1/\sqrt{2} & 0 \\ 0 & 0 & 0 \\ 0 & 0 & 0 \end{bmatrix} $$
In $A^+ = Q_2 D^+ Q_1^T$:
$$ A^+ = \begin{bmatrix} 1/2 & 1/2 & 1/\sqrt{2} & 0 \\ 1/2 & -1/2 & 0 & 1/\sqrt{2} \\ -1/2 & -1/2 & 1/\sqrt{2} & 0 \\ -1/2 & 1/2 & 0 & 1/\sqrt{2} \end{bmatrix} \begin{bmatrix} 1/\sqrt{6} & 0 & 0 \\ 0 & 1/\sqrt{2} & 0 \\ 0 & 0 & 0 \\ 0 & 0 & 0 \end{bmatrix} \begin{bmatrix} 2/\sqrt{6} & -1/\sqrt{6} & 0 \\ 0 & -1/\sqrt{2} & 1/\sqrt{2} \\ 1/3 & 2/3 & 2/3 \end{bmatrix} $$
$$ A^+ = \frac{1}{6} \begin{bmatrix} 1 & -2 & 1 \\ 1 & 1 & -2 \\ -1 & 2 & -1 \\ -1 & -1 & 2 \end{bmatrix} $$

### Izračun psevdoinverza brez singularnega razcepa

Za pozitivno semidefinitno matriko $B$ vemo, da se njen singularni razcep ujema z njenim lastnim razcepom $B = QDQ^*$, kjer je $Q$ unitarna in $D$ diagonalna z nenegativnimi elementi. Torej je $B^+ = QD^+Q^*$. Splošni primer lahko prevedemo na pozitivno semidefinitni primer takole:

### Trditev

Za vsako kompleksno matriko $A$ velja $A^+ = (A^*A)^+A^* = A^*(AA^*)^+$.

**Dokaz:**
Če je $A = Q_1DQ_2^*$ singularni razcep, potem sta tudi $A^*A = Q_2D^*DQ_2^*$ in $AA^* = Q_1DD^*Q_1^*$ singularna razcepa. Torej je $A^* = Q_2D^*Q_1^*$.
$(A^*A)^+ = Q_2(D^*D)^+Q_2^*$ in $(AA^*)^+ = Q_1(DD^*)^+Q_1^*$.
Trditev sedaj sledi iz identitet za diagonalne matrike:
$D^+ = (D^*D)^+D^* = D^*(DD^*)^+$.

### Posledica

*   Če so stolpci $A$ linearno neodvisni, je $A^+ = (A^*A)^{-1}A^*$.
*   Če so vrstice $A$ linearno neodvisne, je $A^+ = A^*(AA^*)^{-1}$.

### Izrek o enoličnosti psevdoinverza

Matrika $A^+$ je enolično določena z matriko $A$.

**Dokaz:**
Dokažimo najprej nekaj identitet, ki jim zadošča matrika $A^+$ (imenovane Penroseovi pogoji):
1.  $AA^+A = A$
2.  $A^+AA^+ = A^+$
3.  $(AA^+)^* = AA^+$
4.  $(A^+A)^* = A^+A$
Če bi z dvema singularnima razcepoma dobili različna psevdoinverza $B$ in $C$, potem bi oba zadoščala tem štirim identitetam. Odtod sledi $B=C$.
Uporabimo (1) in (3): $AB = ACAB \implies (AB)^* = (ACAB)^* \implies B^*A^* = B^*A^*C^*A^*$.
Podobno dokažemo, da je tudi $BA = CA$. Oboje uporabimo v računu $B=BAB=BAC=CAC=C$.

## 8. Najkrajša posplošena rešitev sistema linearnih enačb

Psevdoinverz se rabi pri iskanju rešitev sistemov linearnih enačb.
Naj bo $A$ pravokotna matrika. Spomnimo se definicije posplošene rešitve sistema $Ax = b$. To je tak vektor $x_0$, da je $Ax_0$ najbližje vektorju $b$.
Posplošena rešitev ni enolično določena. Med vsemi posplošenimi rešitvami sistema $Ax = b$ poiščimo najkrajšo ($||x||$ je minimalen). Izkaže se, da je to ravno $A^+b$.

### Izrek

Naj bo $A$ kompleksna $m \times n$ matrika in $b$ vektor iz $\mathbb{C}^m$. Najkrajša posplošena rešitev sistema $Ax = b$ je $x_0 = A^+b$.

**Dokaz:**
Naj bo $A = Q_1DQ_2^*$ singularni razcep. Označimo $b' = Q_1^*b$.
Primerjajmo posplošene rešitve sistema $Ax = b$ s posplošenimi rešitvami sistema $Dx' = b'$. Za vsak vektor $x \in \mathbb{C}^n$ velja:
$||Ax - b|| = ||Q_1DQ_2^*x - b|| = ||Q_1(DQ_2^*x - Q_1^*b)|| = ||DQ_2^*x - Q_1^*b||$.
Označimo $x' = Q_2^*x$ in $b' = Q_1^*b$. Ker sta $Q_1, Q_2$ unitarni, velja $||x|| = ||x'||$ in $||b|| = ||b'||$.
Odtod očitno sledi dvoje:
*   Če je $x_0$ posplošena rešitev sistema $Ax = b$, potem je $x_0' := Q_2^*x_0$ posplošena rešitev sistema $Dx' = b'$. Velja tudi $||x_0'|| = ||x_0||$.
*   Če je $x_0'$ posplošena rešitev sistema $Dx' = b'$, potem je $x_0 := Q_2x_0'$ posplošena rešitev sistema $Ax = b$. Velja tudi $||x_0|| = ||x_0'||$.
Torej je $x_0$ najkrajša posplošena rešitev sistema $Ax = b$ natanko tedaj, ko je $x_0'$ najkrajša posplošena rešitev sistema $Dx' = b'$.

Poiščimo sedaj najkrajšo posplošeno rešitev sistema $Dx' = b'$.
To pomeni, da iščemo najkrajšega izmed vseh vektorjev $x'$, ki minimizirajo izraz $||Dx' - b'||$.
Če vstavimo $x' = (x_1', \dots, x_n')$ in $b' = (b_1', \dots, b_m')$ dobimo:
$||Dx' - b'||^2 = (\sigma_1 x_1' - b_1')^2 + \dots + (\sigma_r x_r' - b_r')^2 + (b_{r+1}')^2 + \dots + (b_m')^2$.
Minimum tega izraza dobimo pri $x_i' = b_i'/\sigma_i$ za $i=1, \dots, r$, kjer so $x_{r+1}', \dots, x_n'$ poljubni.
Najkrajša od teh posplošenih rešitev je $x_0' = (b_1'/\sigma_1, \dots, b_r'/\sigma_r, 0, \dots, 0)$.
Opazimo, da je izraz na desni enak $D^+b'$. Odtod sledi, da je
$x_0 := Q_2x_0' = Q_2D^+b' = Q_2D^+Q_1^*b = A^+b$
najkrajša posplošena rešitev sistema $Ax = b$.

### Primer

Sistem linearnih enačb:
$x_1 + x_2 - x_3 - x_4 = 1$
$-x_1 + x_3 = 0$
$-x_2 + x_4 = 1$
ni rešljiv v običajnem smislu. Poiščimo najkrajšo posplošeno rešitev.

**Rešitev:** Sistem najprej zapišemo v matrični obliki $Ax = b$:
$A = \begin{bmatrix} 1 & 1 & -1 & -1 \\ -1 & 0 & 1 & 0 \\ 0 & -1 & 0 & 1 \end{bmatrix}$, $x = \begin{bmatrix} x_1 \\ x_2 \\ x_3 \\ x_4 \end{bmatrix}$, $b = \begin{bmatrix} 1 \\ 0 \\ 1 \end{bmatrix}$.
Uporabimo $A^+$ iz prejšnjega primera:
$A^+ = \frac{1}{6} \begin{bmatrix} 1 & -2 & 1 \\ 1 & 1 & -2 \\ -1 & 2 & -1 \\ -1 & -1 & 2 \end{bmatrix}$.
Najkrajša posplošena rešitev je $x_0 = A^+b$:
$x_0 = \frac{1}{6} \begin{bmatrix} 1 & -2 & 1 \\ 1 & 1 & -2 \\ -1 & 2 & -1 \\ -1 & -1 & 2 \end{bmatrix} \begin{bmatrix} 1 \\ 0 \\ 1 \end{bmatrix} = \frac{1}{6} \begin{bmatrix} 1(1) - 2(0) + 1(1) \\ 1(1) + 1(0) - 2(1) \\ -1(1) + 2(0) - 1(1) \\ -1(1) - 1(0) + 2(1) \end{bmatrix} = \frac{1}{6} \begin{bmatrix} 2 \\ -1 \\ -2 \\ 1 \end{bmatrix}$.