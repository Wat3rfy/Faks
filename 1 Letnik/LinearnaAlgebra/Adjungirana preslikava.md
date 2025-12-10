

## 1. Definicija adjungirane linearne preslikave

V tem razdelku bomo delali z več vektorskimi prostori s skalarnim produktom, zato bomo pri vsakem skalarnem produktu označili, iz katerega vektorskega prostora prihaja. Izbrani skalarni produkt na $U$ bomo označili z $\langle u_1, u_2 \rangle_U$, izbrani skalarni produkt na $V$ bomo označili z $\langle v_1, v_2 \rangle_V$, itd.

### Definicija adjungirane linearne preslikave

Naj bo $L: U \to V$ linearna preslikava med dvema vektorskima prostoroma s skalarnim produktom. Pravimo, da je linearna preslikava $L^*: V \to U$ **adjungirana linearna preslikava** linearne preslikave $L$, če velja
$\langle Lu, v \rangle_V = \langle u, L^*v \rangle_U$
za vsak $u \in U$ in vsak $v \in V$.

Iz definicije še ne sledi, da $L^*$ obstaja. Dokažimo obstoj in enoličnost v končnorazsežnem primeru.

### Izrek o obstoju in enoličnosti adjungirane linearne preslikave

Vsaka linearna preslikava med končnorazsežnima vektorskima prostoroma s skalarnim produktom ima natanko eno adjungirano linearno preslikavo.

**Dokaz:**
Recimo, da sta $U$ in $V$ končnorazsežna vektorska prostora s skalarnim produktom in da je $L: U \to V$ linearna preslikava.

**Enoličnost:** Naj bosta $L^*$ in $L'$ dve adjungirani linearni preslikavi linearne preslikave $L$. Potem za vsak $u \in U$ ter $v \in V$ velja:
$\langle Lu, v \rangle_V = \langle u, L^*v \rangle_U$ in $\langle Lu, v \rangle_V = \langle u, L'v \rangle_U$.
Če enačbi odštejemo, dobimo, da za vsak $u \in U$ in vsak $v \in V$ velja:
$\langle u, L^*v - L'v \rangle_U = \langle u, L^*v \rangle_U - \langle u, L'v \rangle_U = \langle Lu, v \rangle_V - \langle Lu, v \rangle_V = 0$.
Če vstavimo $u = L^*v - L'v$, dobimo $\langle L^*v - L'v, L^*v - L'v \rangle_U = 0$, se pravi $L^*v - L'v = 0$ za vsak $v \in V$. Torej je $L^* = L'$.

**Obstoj:** Vzemimo poljuben vektor $v \in V$ in si oglejmo preslikavo $\phi_v(u) = \langle Lu, v \rangle_V$, ki slika iz $U$ v skalarje. Preverimo najprej, da je $\phi_v$ linearen funkcional na $U$:
$\phi_v(\alpha_1 u_1 + \alpha_2 u_2) = \langle L(\alpha_1 u_1 + \alpha_2 u_2), v \rangle_V = \langle \alpha_1 Lu_1 + \alpha_2 Lu_2, v \rangle_V = \alpha_1 \langle Lu_1, v \rangle_V + \alpha_2 \langle Lu_2, v \rangle_V = \alpha_1 \phi_v(u_1) + \alpha_2 \phi_v(u_2)$.
Po Rieszovem izreku o reprezentaciji linearnih funkcionalov obstaja natanko en vektor $w \in U$, ki zadošča $\phi_v(u) = \langle u, w \rangle_U$ za vsak $u \in U$. Definirajmo $L^*v := w$.
S tem smo definirali preslikavo $L^*: V \to U$, ki zadošča $\langle Lu, v \rangle_V = \langle u, L^*v \rangle_U$ za vsak $u \in U$ in vsak $v \in V$.

**Linearnost $L^*$: ** Preverimo še, da je $L^*$ res linearna preslikava.
Vzemimo poljubna vektorja $v_1, v_2 \in V$ in poljubna skalarja $\alpha_1, \alpha_2$.
Po definiciji so $L^*v_1, L^*v_2$ in $L^*(\alpha_1 v_1 + \alpha_2 v_2)$ taki vektorji iz $U$, da velja za vsak $u \in U$:
1. $\langle u, L^*v_1 \rangle_U = \langle Lu, v_1 \rangle_V$
2. $\langle u, L^*v_2 \rangle_U = \langle Lu, v_2 \rangle_V$
3. $\langle u, L^*(\alpha_1 v_1 + \alpha_2 v_2) \rangle_U = \langle Lu, \alpha_1 v_1 + \alpha_2 v_2 \rangle_V$
Iz (1), (2) in (3) sledi, da za vsak $u \in U$ velja:
$\langle u, L^*(\alpha_1 v_1 + \alpha_2 v_2) - \alpha_1 L^*v_1 - \alpha_2 L^*v_2 \rangle_U$
$= \langle u, L^*(\alpha_1 v_1 + \alpha_2 v_2) \rangle_U - \langle u, \alpha_1 L^*v_1 \rangle_U - \langle u, \alpha_2 L^*v_2 \rangle_U$
$= \langle Lu, \alpha_1 v_1 + \alpha_2 v_2 \rangle_V - \overline{\alpha_1} \langle u, L^*v_1 \rangle_U - \overline{\alpha_2} \langle u, L^*v_2 \rangle_U$
$= \alpha_1 \langle Lu, v_1 \rangle_V + \alpha_2 \langle Lu, v_2 \rangle_V - \overline{\alpha_1} \langle Lu, v_1 \rangle_V - \overline{\alpha_2} \langle Lu, v_2 \rangle_V$
$= \alpha_1 \langle Lu, v_1 \rangle_V + \alpha_2 \langle Lu, v_2 \rangle_V - \alpha_1 \langle Lu, v_1 \rangle_V - \alpha_2 \langle Lu, v_2 \rangle_V = 0$.
Ker to velja za vsak $u \in U$, in ker je skalarni produkt pozitiven definiten, sledi:
$L^*(\alpha_1 v_1 + \alpha_2 v_2) - \alpha_1 L^*v_1 - \alpha_2 L^*v_2 = 0$.
Torej je preslikava $L^*$ res linearna.

### Primer računanja adjungirane preslikave

Naj bo $U = V = \mathbb{C}^2$ vektorski prostor z nestandardnim skalarnim produktom $\langle (\alpha_1, \alpha_2), (\beta_1, \beta_2) \rangle = 2\alpha_1 \overline{\beta_1} + 3\alpha_2 \overline{\beta_2}$. Izračunaj adjungirano linearno preslikavo linearne preslikave $L(x, y) = (ax + by, cx + dy)$.

Ker je $L^*$ linearna preslikava iz $\mathbb{C}^2$ v $\mathbb{C}^2$, je oblike $L^*(x, y) = (ex + fy, gx + hy)$.
Poleg tega mora veljati $\langle L(x_1, y_1), (x_2, y_2) \rangle = \langle (x_1, y_1), L^*(x_2, y_2) \rangle$ za vse $x_1, x_2, y_1, y_2 \in \mathbb{C}$. Ko upoštevamo definiciji $L$ in $L^*$ dobimo:
$\langle (ax_1 + by_1, cx_1 + dy_1), (x_2, y_2) \rangle = \langle (x_1, y_1), (ex_2 + fy_2, gx_2 + hy_2) \rangle$.
Uporabimo definicijo skalarnega produkta:
$2(ax_1 + by_1)\overline{x_2} + 3(cx_1 + dy_1)\overline{y_2} = 2x_1\overline{(ex_2 + fy_2)} + 3y_1\overline{(gx_2 + hy_2)}$.
$2(ax_1\overline{x_2} + by_1\overline{x_2}) + 3(cx_1\overline{y_2} + dy_1\overline{y_2}) = 2x_1(\overline{e}\overline{x_2} + \overline{f}\overline{y_2}) + 3y_1(\overline{g}\overline{x_2} + \overline{h}\overline{y_2})$.
Primerjajmo istoležne koeficiente (npr. pri $x_1\overline{x_2}, y_1\overline{x_2}, x_1\overline{y_2}, y_1\overline{y_2}$):
1. Pri $x_1\overline{x_2}$: $2a = 2\overline{e} \implies e = \overline{a}$.
2. Pri $y_1\overline{x_2}$: $2b = 3\overline{g} \implies g = \frac{2}{3}\overline{b}$.
3. Pri $x_1\overline{y_2}$: $3c = 2\overline{f} \implies f = \frac{3}{2}\overline{c}$.
4. Pri $y_1\overline{y_2}$: $3d = 3\overline{h} \implies h = \overline{d}$.
Odtod izrazimo $e, f, g, h$ z $a, b, c, d$ in vstavimo v definicijo $L^*$. Dobimo:
$L^*(x, y) = \left(\overline{a}x + \frac{3}{2}\overline{c}y, \frac{2}{3}\overline{b}x + \overline{d}y\right)$.

## 2. Matrika adjungirane linearne preslikave

Naj bosta $U$ in $V$ končnorazsežna vektorska prostora s skalarnim produktom. Zanima nas, kakšna je zveza med matriko linearne preslikave $L: U \to V$ in matriko njene adjungirane linearne preslikave $L^*: V \to U$. Odgovor je odvisen od izbire baz za $U$ in $V$. V splošnem ni nobene zveze, če pa za $U$ in $V$ izberemo ortonormirani bazi, potem velja naslednje:

### Trditev

Naj bo $\mathcal{B}$ ortonormirana baza za $U$ in $\mathcal{C}$ ortonormirana baza za $V$. Naj bo $L: U \to V$ linearna preslikava in $L^*: V \to U$ njena adjungirana linearna preslikava. Potem matriko $[L^*]_{\mathcal{B} \leftarrow \mathcal{C}}$ dobimo tako, da v matriki $[L]_{\mathcal{C} \leftarrow \mathcal{B}}$ vse elemente konjugiramo in dobljeno matriko še transponiramo.

**Dokaz:**
Naj bo $\mathcal{B} = \{u_1, \dots, u_m\}$ in $\mathcal{C} = \{v_1, \dots, v_n\}$. Izračunajmo matriko $[L]_{\mathcal{C} \leftarrow \mathcal{B}}$. S pomočjo Fourierovega razvoja dobimo:
$Lu_j = \sum_{i=1}^n \langle Lu_j, v_i \rangle_V v_i$.
Torej je $i$-ti element $j$-tega stolpca matrike $[L]_{\mathcal{C} \leftarrow \mathcal{B}}$ enak $a_{ij} = \langle Lu_j, v_i \rangle_V$.

Podobno za $L^*$. Izračunajmo matriko $[L^*]_{\mathcal{B} \leftarrow \mathcal{C}}$. $L^*v_j = \sum_{i=1}^m \langle L^*v_j, u_i \rangle_U u_i$.
Torej je $i$-ti element $j$-tega stolpca matrike $[L^*]_{\mathcal{B} \leftarrow \mathcal{C}}$ enak $b_{ij} = \langle L^*v_j, u_i \rangle_U$.

Opazimo, da je $(i, j)$-ti element matrike $[L^*]_{\mathcal{B} \leftarrow \mathcal{C}}$ enak
$b_{ij} = \langle L^*v_j, u_i \rangle_U = \overline{\langle u_i, L^*v_j \rangle_U} = \overline{\langle Lu_i, v_j \rangle_V}$.
To je enako konjugiranemu $(j, i)$-temu elementu matrike $[L]_{\mathcal{C} \leftarrow \mathcal{B}}$.
Če torej vse elemente matrike $[L]_{\mathcal{C} \leftarrow \mathcal{B}}$ konjugiramo in dobljeno matriko še transponiramo, dobimo ravno matriko $[L^*]_{\mathcal{B} \leftarrow \mathcal{C}}$.

Zadnji rezultat motivira naslednjo definicijo.

### Definicija adjungirane matrike

Naj bo $A$ kompleksna $m \times n$ matrika in naj bo $\overline{A}$ matrika, ki jo dobimo tako, da v matriki $A$ konjugiramo vse elemente. Potem matriki
$A^* := (\overline{A})^T$
pravimo **adjungirana matrika** matrike $A$.

**Opomba:** Torej je $[L^*]_{\mathcal{B} \leftarrow \mathcal{C}} = ([L]_{\mathcal{C} \leftarrow \mathcal{B}})^*$, če sta $\mathcal{B}$ in $\mathcal{C}$ ortonormirani bazi.

##

## 3. Lastnosti adjungiranja

Adjungiranje matrik je preslikava iz matrik v matrike, ki vsaki matriki $A$ priredi adjungirano matriko $A^* = (\overline{A})^T$. Z direktnim računom lahko preverimo naslednje lastnosti te preslikave:

1.  $(\alpha A + \beta B)^* = \overline{\alpha} A^* + \overline{\beta} B^*$
2.  $(A^*)^* = A$
3.  $(AB)^* = B^* A^*$
4.  $0^* = 0$, $I^* = I$

Iz lastnosti (1) sledi, da je na realnih matrikah fiksne velikosti adjungiranje linearna preslikava. Na kompleksnih matrikah fiksne velikosti adjungiranje ni linearna, ampak konjugirano linearna preslikava.

**Dokaz (skica):**
Vemo, da za konjugiranje kompleksnih števil velja $\overline{z_1 + z_2} = \overline{z_1} + \overline{z_2}$, $\overline{z_1 z_2} = \overline{z_1}\overline{z_2}$, $\overline{\overline{z}} = z$.
Odtod sledi, da za kompleksne matrike velja $\overline{\alpha A + \beta B} = \overline{\alpha}\overline{A} + \overline{\beta}\overline{B}$, $\overline{AB} = \overline{A}\overline{B}$, $\overline{\overline{A}} = A$.
Upoštevajmo še lastnosti transponiranja: $(\alpha A + \beta B)^T = \alpha A^T + \beta B^T$, $(AB)^T = B^T A^T$, $(A^T)^T = A$.
Odtod sledi:
1.  $(\alpha A + \beta B)^* = (\overline{\alpha A + \beta B})^T = (\overline{\alpha}\overline{A} + \overline{\beta}\overline{B})^T = (\overline{\alpha}\overline{A})^T + (\overline{\beta}\overline{B})^T = \overline{\alpha}\overline{A}^T + \overline{\beta}\overline{B}^T = \overline{\alpha} A^* + \overline{\beta} B^*$.
2.  $(A^*)^* = ((\overline{A})^T)^* = (\overline{(\overline{A})^T})^T = ((A^T)^T) = \overline{\overline{A}} = A$.
3.  $(AB)^* = (\overline{AB})^T = (\overline{A}\overline{B})^T = (\overline{B})^T (\overline{A})^T = B^* A^*$.

Podoben razmislek lahko naredimo tudi za adjungiranje linearnih preslikav.
Naj bosta $U$ in $V$ vektorska prostora s skalarnim produktom. Označimo z $\mathcal{L}(U, V)$ množico vseh linearnih preslikav iz $U$ v $V$. To množico lahko spremenimo v vektorski prostor, če za linearni preslikavi $L_1, L_2$ in skalarja $\alpha_1, \alpha_2$ definiramo linearno preslikavo $\alpha_1 L_1 + \alpha_2 L_2$ s predpisom $(\alpha_1 L_1 + \alpha_2 L_2)(u) = \alpha_1 L_1(u) + \alpha_2 L_2(u)$.
Adjungiranje je preslikava $L: \mathcal{L}(U, V) \to \mathcal{L}(V, U)$. Preverimo, da zadošča:

1.  $(\alpha_1 L_1 + \alpha_2 L_2)^* = \overline{\alpha_1} L_1^* + \overline{\alpha_2} L_2^*$
    Za vsaka $u \in U$ in $v \in V$ velja:
    $\langle u, (\alpha_1 L_1 + \alpha_2 L_2)^*(v) \rangle_U = \langle (\alpha_1 L_1 + \alpha_2 L_2)(u), v \rangle_V$
    $= \langle \alpha_1 L_1 u + \alpha_2 L_2 u, v \rangle_V = \alpha_1 \langle L_1 u, v \rangle_V + \alpha_2 \langle L_2 u, v \rangle_V$
    $= \alpha_1 \langle u, L_1^* v \rangle_U + \alpha_2 \langle u, L_2^* v \rangle_U = \langle u, \overline{\alpha_1} L_1^* v + \overline{\alpha_2} L_2^* v \rangle_U = \langle u, (\overline{\alpha_1} L_1^* + \overline{\alpha_2} L_2^*)(v) \rangle_U$.
    Če upoštevamo enoličnost adjungirane preslikave, odtod sledi (1). Lastnost (1) bi lahko dokazali tudi s prehodom na matrike.

2.  $(L^*)^* = L$
    Dokažemo tako, da preverimo, da sta $L$ in $(L^*)^*$ adjungirani linearni preslikavi linearne preslikave $L^*$. Za vsaka $u \in U$ in $v \in V$ velja:
    $\langle v, (L^*)^* u \rangle_V = \overline{\langle (L^*)^* u, v \rangle_V} = \overline{\langle u, L^* v \rangle_U} = \langle L^* v, u \rangle_U = \overline{\overline{\langle u, L^* v \rangle_U}} = \overline{\langle Lu, v \rangle_V} = \langle v, Lu \rangle_V$.
    (Opomba: tukaj sem uporabil $\overline{\overline{z}} = z$ in $\langle x,y \rangle = \overline{\langle y,x \rangle}$).
    Zato $(L^*)^* = L$.

3.  $(L_2 L_1)^* = L_1^* L_2^*$
    Recimo, da $L_1$ slika iz $U$ v $V$, $L_2$ pa iz $V$ v $W$. Potem $L_2 L_1: U \to W$. Njen adjungiran je $(L_2 L_1)^*: W \to U$.
    Za vsak $u \in U$ in vsak $w \in W$ velja naslednji račun:
    $\langle u, (L_2 L_1)^* w \rangle_U = \langle L_2 L_1 u, w \rangle_W = \langle L_1 u, L_2^* w \rangle_V = \langle u, L_1^* (L_2^* w) \rangle_U = \langle u, (L_1^* L_2^*) w \rangle_U$.
    Seveda bi tudi lastnosti (2) in (3) lahko dokazali s prehodom na matrike.



## 5. Jedro in slika adjungirane preslikave

Recimo, da poznamo jedro in sliko linearne preslikave $L: U \to V$. Radi bi odtod dobili jedro in sliko adjungirane linearne preslikave $L^*: V \to U$. Spomnimo se, da velja $\langle Lu, v \rangle = \langle u, L^*v \rangle$ za vsak $u \in U$ in vsak $v \in V$.

### Izrek

Za vsako linearno preslikavo $L: U \to V$, kjer sta $U$ in $V$ končnorazsežna vektorska prostora s skalarnim produktom, velja:
$$ \mathrm{Ker} L^* = (\mathrm{Im} L)^\perp \quad (1) $$

**Dokaz:**
Vzemimo poljuben vektor $v \in V$. Opazimo, da velja $L^*v = 0$ natanko tedaj, ko je $\langle u, L^*v \rangle = 0$ za vsak $u \in U$. Po definiciji $L^*$ velja to natanko tedaj, ko je $\langle Lu, v \rangle = 0$ za vsak $u \in U$. Po definiciji $\mathrm{Im} L$ velja to natanko tedaj, ko je $\langle w, v \rangle = 0$ za vsak $w \in \mathrm{Im} L$. Po definiciji ortogonalnega komplementa velja to natanko tedaj, ko $v \in (\mathrm{Im} L)^\perp$.

### Posledice formule (1)

Oglejmo si nekaj preprostih posledic formule (1).
*   Če na obeh straneh (1) uporabimo ortogonalni komplement in upoštevamo, da je $((\mathrm{Im} L)^\perp)^\perp = \mathrm{Im} L$, dobimo:
    $$ \mathrm{Im} L = (\mathrm{Ker} L^*)^\perp \quad (2) $$
*   Če v formuli (1) zamenjamo $L$ z $L^*$, dobimo:
    $$ \mathrm{Ker} L = (\mathrm{Im} L^*)^\perp \quad (3) $$
*   Če v formuli (2) zamenjamo $L$ z $L^*$, dobimo:
    $$ \mathrm{Im} L^* = (\mathrm{Ker} L)^\perp \quad (4) $$
Isto formulo dobimo, če na obeh straneh v (3) uporabimo ortogonalni komplement.

### Matrična interpretacija

Pokažimo sedaj, da formule (1)-(4) veljajo tudi za matrike.
Najprej standardni skalarni produkt zapišemo v matrični obliki:
$$ \langle v, w \rangle = v_1 \overline{w_1} + \dots + v_n \overline{w_n} = \begin{bmatrix} \overline{w_1} & \dots & \overline{w_n} \end{bmatrix} \begin{bmatrix} v_1 \\ \vdots \\ v_n \end{bmatrix} = w^* v \quad (5) $$
Naj bo $A$ kompleksna $m \times n$ matrika. Opazimo, da iz (5) sledi:
$$ \langle Au, v \rangle = v^*Au = v^*(A^*)^*u = (A^*v)^*u = \langle u, A^*v \rangle \quad (6) $$
za vsak $u \in \mathbb{C}^n$ in vsak $v \in \mathbb{C}^m$. V $\langle Au, v \rangle$ nastopa standardni skalarni produkt na $\mathbb{C}^m$, v $\langle u, A^*v \rangle$ pa standardni skalarni produkt na $\mathbb{C}^n$. Naj bo $L_A$ linearna preslikava iz $\mathbb{C}^n$ v $\mathbb{C}^m$ definirana z $L_A u = Au$. Potem velja:
$$ (L_A)^* = L_{A^*} \quad (7) $$
saj po (6) velja $\langle u, (L_A)^*v \rangle = \langle L_A u, v \rangle = \langle Au, v \rangle = \langle u, A^*v \rangle = \langle u, L_{A^*}v \rangle$ za vsak $u \in \mathbb{C}^n$ in vsak $v \in \mathbb{C}^m$. Iz (7) sledi recimo verzija (3) za matrike:
$$ \mathrm{Ker} A = \mathrm{Ker} L_A = (\mathrm{Im} (L_A)^*)^\perp = (\mathrm{Im} L_{A^*})^\perp = (\mathrm{Im} A^*)^\perp $$

### Jedro in slika $L^*L$ in $LL^*$

Če je $L: U \to V$ linearna preslikava, potem $L^*L$ slika iz $U$ v $U$, $LL^*$ pa iz $V$ v $V$. Poleg tega iz lastnosti adjungiranja sledi $(L^*L)^* = L^*L$ in $(LL^*)^* = LL^*$.

**Trditev:**
Za vsako linearno preslikavo $L: U \to V$, kjer sta $U$ in $V$ končnorazsežna vektorska prostora s skalarnim produktom, velja:
$$ \mathrm{Ker} L^*L = \mathrm{Ker} L \quad (8) $$

**Dokaz:**
Vzemimo poljuben $u \in U$. Če $u \in \mathrm{Ker} L$, potem je $Lu = 0$. Odtod sledi $L^*Lu = L^*0 = 0$, torej $u \in \mathrm{Ker} L^*L$.
Dokažimo še obratno. Če $u \in \mathrm{Ker} L^*L$, potem $L^*Lu = 0$. Po definiciji $L^*$ je $\langle Lu, Lu \rangle = \langle u, L^*Lu \rangle = \langle u, 0 \rangle = 0$. Odtod sledi $Lu = 0$, torej je $u \in \mathrm{Ker} L$.

### Posledice formule (8)

Oglejmo si nekaj posledic formule (8).
*   Če na obeh straneh formule (8) vzamemo ortogonalni komplement in upoštevamo, da po formuli (4) velja $\mathrm{Im} L^* = (\mathrm{Ker} L)^\perp$ in $\mathrm{Im} L^*L = (\mathrm{Ker} L^*L)^\perp$, potem dobimo:
    $$ \mathrm{Im} L^*L = \mathrm{Im} L^* \quad (9) $$
*   Če v formulah (8) in (9) zamenjamo $L$ z $L^*$, potem dobimo:
    $$ \mathrm{Ker} LL^* = \mathrm{Ker} L^* \quad (10) $$
    $$ \mathrm{Im} LL^* = \mathrm{Im} L \quad (11) $$

**Opomba:** Pravimo, da je $L: V \to V$ **normalna** linearna preslikava, če velja $LL^* = L^*L$. Za normalne linearne preslikave iz (8) in (10) sledi, da je $\mathrm{Ker} L^* = \mathrm{Ker} L$, iz (9) in (11) pa sledi, da je $\mathrm{Im} L^* = \mathrm{Im} L$.

## 6. Lastne vrednosti adjungirane matrike

Recimo, da je $A$ kompleksna $n \times n$ matrika. Zanima nas, kakšna je zveza med lastnimi vrednostmi matrike $A$ in lastnimi vrednostmi matrike $A^*$.

### Izrek o lastnih vrednostih adjungirane matrike

Naj bo $A$ kvadratna matrika nad $\mathbb{C}$ in naj bo $\lambda \in \mathbb{C}$. Potem je $\lambda$ lastna vrednost za $A$ natanko tedaj, ko je $\overline{\lambda}$ lastna vrednost za $A^*$.

**Dokaz (prvi način - dimenzionalni):**
Radi bi dokazali, da velja $\mathrm{Ker}(A - \lambda I) \ne \{0\}$ natanko tedaj, ko velja $\mathrm{Ker}(A^* - \overline{\lambda}I) \ne \{0\}$. Zadošča dokazati, da velja:
$$ \dim \mathrm{Ker}(A - \lambda I) = \dim \mathrm{Ker}(A^* - \overline{\lambda}I) \quad (12) $$
Označimo $B = A - \lambda I$. Iz lastnosti operacije adjungiranja sledi, da je $B^* = A^* - \overline{\lambda}I$. Torej zadošča dokazati, da je $\dim \mathrm{Ker} B = \dim \mathrm{Ker} B^*$.
Iz izreka $\mathrm{Ker} B^* = (\mathrm{Im} B)^\perp$ (formula (1)) sledi:
$$ \dim \mathrm{Ker} B^* = \dim (\mathrm{Im} B)^\perp \quad (13) $$
Po izreku o ortogonalnem razcepu (za podprostor $\mathrm{Im} B$), je:
$$ \dim (\mathrm{Im} B)^\perp = n - \dim \mathrm{Im} B \quad (14) $$
kjer je $n$ velikost matrike $A$. Po osnovnem izreku o rangu in ničelnosti, je:
$$ n - \dim \mathrm{Im} B = \dim \mathrm{Ker} B \quad (15) $$
Iz formul (13), (14) in (15) sledi $\dim \mathrm{Ker} B^* = \dim \mathrm{Ker} B$, kar dokazuje formulo (12).

**Dokaz (drugi način - računski):**
Najprej opazimo, da za vsako kompleksno kvadratno matriko $B$ velja:
$$ \det B^* = \det((\overline{B})^T) = \det(\overline{B}) = \overline{\det B} $$
Če vstavimo $B = A - \lambda I$, dobimo:
$$ \det(A^* - \overline{\lambda}I) = \overline{\det(A - \lambda I)} $$
Torej za karakteristična polinoma $p_A(\lambda) = \det(A - \lambda I)$ in $p_{A^*}(\lambda) = \det(A^* - \lambda I)$ velja:
$$ p_{A^*}(\overline{\lambda}) = \overline{p_A(\lambda)} $$
Torej je $p_A(\lambda) = 0$ natanko tedaj, ko je $p_{A^*}(\overline{\lambda}) = 0$, kar dokaže izrek.
**Opomba:** Iz tega dokaza je razvidno, kako se $p_{A^*}(\lambda)$ izraža z $p_A(\lambda)$. Iz $p_A(\lambda) = c_0 + c_1\lambda + \dots + c_n\lambda^n$ namreč sledi, da velja $p_{A^*}(\lambda) = \overline{p_A(\overline{\lambda})} = \overline{c_0 + c_1\overline{\lambda} + \dots + c_n\overline{\lambda}^n} = \overline{c_0} + \overline{c_1}\lambda + \dots + \overline{c_n}\lambda^n$


## 7. Simetrične in hermitske matrike

### Definicija sebiadjungirane preslikave

Naj bo $V$ končnorazsežen vektorski prostor s skalarnim produktom. Linearna preslikava $L: V \to V$ je **sebiadjungirana**, če velja $L = L^*$.

**Opomba:** Če je $A$ matrika sebiadjungirane preslikave $L: V \to V$ glede na ortonormirano bazo $\mathcal{B}$ za $V$, potem je $A^* = ([L]_{\mathcal{B}})^* = [L^*]_{\mathcal{B}} = [L]_{\mathcal{B}} = A$. Taki matriki včasih pravimo **sebiadjungirana matrika**, vendar se pogosteje uporablja naslednja terminologija:

### Definicija simetrične in hermitske matrike

Kompleksna matrika $A$ je **hermitska**, če zadošča $A = A^*$. Realnim hermitskim matrikam pravimo tudi **simetrične matrike**.

**Opomba:** Za vsako matriko $A$ sta $A^*A$ in $AA^*$ hermitski matriki. Vsaka potenca hermitske matrike je spet hermitska matrika.

### Primer: Ortogonalni projektorji

Naj bo $V$ vektorski prostor s skalarnim produktom, $W$ podprostor v $V$ in $L: V \to V$ taka linearna preslikava, ki vsakemu vektorju iz $V$ priredi njegovo ortogonalno projekcijo na $W$. Pokažimo, da je $L = L^*$ in $L = L^2$.

**Dokaz:**
Naj bo $\{w_1, \dots, w_k\}$ ortonormirana baza za $W$. Potem za vsak $v \in V$ velja $Lv = \sum_{i=1}^k \langle v, w_i \rangle w_i$.

*   **$L = L^*$:** Za vsaka $v, v' \in V$ velja:
    $$ \langle Lv, v' \rangle = \left\langle \sum_{i=1}^k \langle v, w_i \rangle w_i, v' \right\rangle = \sum_{i=1}^k \langle v, w_i \rangle \langle w_i, v' \rangle $$
    $$ \langle v, Lv' \rangle = \left\langle v, \sum_{i=1}^k \langle v', w_i \rangle w_i \right\rangle = \sum_{i=1}^k \overline{\langle v', w_i \rangle} \langle v, w_i \rangle = \sum_{i=1}^k \langle w_i, v' \rangle \langle v, w_i \rangle $$
    Torej je za vsaka $v, v' \in V$ velja $\langle Lv, v' \rangle = \langle v, Lv' \rangle$, kar pomeni $L = L^*$.

*   **$L = L^2$:** Ker je $Lw_i = w_i$ za vsak $i$ (projektor projicira bazne vektorje na same sebe), je:
    $$ L^2v = L(Lv) = L\left(\sum_{i=1}^k \langle v, w_i \rangle w_i\right) = \sum_{i=1}^k \langle v, w_i \rangle Lw_i = \sum_{i=1}^k \langle v, w_i \rangle w_i = Lv $$
    Torej $L^2v = Lv$ za vsak $v \in V$, kar pomeni $L^2 = L$.

### Lastne vrednosti hermitskih matrik

**Trditev 1:**
Vse lastne vrednosti hermitske matrike so realne.

**Dokaz:**
Naj bo $\lambda$ lastna vrednost hermitske matrike $A$ in naj bo $v$ pripadajoči lastni vektor ($v \ne 0$). Potem za standardni skalarni produkt velja:
$$ \lambda \langle v, v \rangle = \langle \lambda v, v \rangle = \langle Av, v \rangle = \langle v, A^*v \rangle = \langle v, Av \rangle = \langle v, \lambda v \rangle = \overline{\lambda} \langle v, v \rangle $$
Ker je $v \ne 0$, je $\langle v, v \rangle > 0$, zato lahko pokrajšamo $\langle v, v \rangle$ in dobimo $\lambda = \overline{\lambda}$, kar pomeni, da je $\lambda$ realno število.

**Trditev 2:**
Lastna vektorja hermitske matrike, ki pripadata različnim lastnim vrednostim, sta ortogonalna glede na standardni skalarni produkt.

**Dokaz:**
Naj bo $A$ hermitska matrika in naj bosta $u$ in $v$ njena lastna vektorja. Naj bosta $\lambda$ in $\mu$ pripadajoči lastni vrednosti, se pravi $Au = \lambda u$ in $Av = \mu v$.
Po Trditvi 1 sta $\lambda$ in $\mu$ realni števili. Odtod sledi:
1.  $\langle Au, v \rangle = \langle \lambda u, v \rangle = \lambda \langle u, v \rangle$.
2.  $\langle u, Av \rangle = \langle u, \mu v \rangle = \overline{\mu} \langle u, v \rangle = \mu \langle u, v \rangle$ (ker je $\mu$ realen).
Ker je $A$ hermitska matrika, velja $\langle Au, v \rangle = \langle u, A^*v \rangle = \langle u, Av \rangle$.
Iz (1) in (2) sledi $\lambda \langle u, v \rangle = \mu \langle u, v \rangle$, kar lahko zapišemo kot $(\lambda - \mu) \langle u, v \rangle = 0$.
Če je $\lambda \ne \mu$, sledi, da je $\langle u, v \rangle = 0$.

### Jordanska forma hermitske matrike

**Trditev 3:**
Vsaka hermitska matrika je podobna diagonalni matriki.

**Dokaz (skica):**
Zadošča dokazati, da se korenski podprostori ujemajo z lastnimi podprostori. Odtod namreč sledi, da so vse Jordanske kletke velikosti 1.
Naj bo $\lambda$ lastna vrednost hermitske matrike $A$. Radi bi dokazali, da za vsako naravno število $m$ velja $\mathrm{Ker}(A - \lambda I)^m = \mathrm{Ker}(A - \lambda I)$.
Označimo $B = A - \lambda I$. Ker je $A$ hermitska in $\lambda$ realen (Trditev 1), je tudi matrika $B$ hermitska (tj. $B^* = B$).
Iz formule $\mathrm{Ker} B^*B = \mathrm{Ker} B$ (formula (8)) torej sledi, da je $\mathrm{Ker} B^2 = \mathrm{Ker} B$ (ker $B^*=B$ za hermitsko $B$).
Če namesto $B$ vstavimo $B^{2^k}$ za $k = 1, \dots, m-1$, dobimo:
$$ \mathrm{Ker} B^{2^m} = \mathrm{Ker} B^{2^{m-1}} = \dots = \mathrm{Ker} B^2 = \mathrm{Ker} B $$
Ker je $2^m \ge m$ za vsak $m \ge 1$, odtod sledi $\mathrm{Ker} B \subseteq \mathrm{Ker} B^m \subseteq \mathrm{Ker} B^{2^m} = \mathrm{Ker} B$.
Torej res za vsak $m \ge 1$ velja $\mathrm{Ker} B^m = \mathrm{Ker} B$.

### Definicija unitarne in ortogonalne matrike

Kompleksna $n \times n$ matrika je **unitarna**, če njeni stolpci tvorijo ortonormirano bazo za $\mathbb{C}^n$ glede na standardni skalarni produkt. Realni unitarni matriki pravimo tudi **ortogonalna matrika**.

**Opomba:** Za unitarno matriko $P$ velja $PP^* = I$. Za ortogonalno matriko $P$ velja $PP^T = I$. V obeh primerih je torej $P^{-1} = P^*$.

### Izrek (Spektralni izrek)

*   Za vsako hermitsko matriko $A$ obstaja taka unitarna matrika $P$ in taka realna diagonalna matrika $D$, da velja $A = PDP^{-1}$.
*   Za vsako simetrično matriko $A$ obstaja taka ortogonalna matrika $P$ in taka realna diagonalna matrika $D$, da velja $A = PDP^{-1}$.

**Dokaz prvega dela (za hermitske matrike):**
Naj bo $A$ hermitska $n \times n$ matrika. Za vsak lastni podprostor matrike $A$ izberimo ortonormirano bazo. Naj bo $\mathcal{B}$ unija izbranih ortonormiranih baz po vseh lastnih podprostorih matrike $A$.
Ker so lastni podprostori matrike $A$ paroma ortogonalni (po Trditvi 2), je $\mathcal{B}$ ortogonalna množica. Ker je $\mathbb{C}^n$ direktna vsota lastnih podprostorov matrike $A$ (po Trditvi 3), je $\mathcal{B}$ ogrodje za $\mathbb{C}^n$. Torej je $\mathcal{B}$ ortonormirana baza za $\mathbb{C}^n$. Sestavljena je iz lastnih vektorjev matrike $A$.
Naj bo $P$ matrika, katere stolpci so elementi baze $\mathcal{B}$. Potem je $P$ unitarna matrika (ker so stolpci ortonormirani). Stolpci $P$ so lastni vektorji matrike $A$, torej je:
$$ AP = A \begin{bmatrix} v_1 & \dots & v_n \end{bmatrix} = \begin{bmatrix} Av_1 & \dots & Av_n \end{bmatrix} = \begin{bmatrix} \lambda_1 v_1 & \dots & \lambda_n v_n \end{bmatrix} = \begin{bmatrix} v_1 & \dots & v_n \end{bmatrix} \begin{bmatrix} \lambda_1 & & 0 \\ & \ddots & \\ 0 & & \lambda_n \end{bmatrix} = PD $$
Torej $AP = PD$, kar pomeni $A = PDP^{-1}$. Lastne vrednosti $\lambda_i$ so realne (Trditev 1), zato je $D$ realna diagonalna matrika.

**Dokaz drugega dela (za simetrične matrike) - z indukcijo:**
Dokažimo s popolno indukcijo, da ima $\mathbb{R}^n$ ortonormirano bazo iz lastnih vektorjev matrike $A$.
Baza indukcije: Za $n=1$ je matrika trivialno diagonalizabilna.
Indukcijski korak: Recimo, da izrek velja za $n-1$.
Naj bo $A$ simetrična $n \times n$ matrika. Simetrična matrika je tudi hermitska, zato ima realne lastne vrednosti (Trditev 1). Naj bo $\lambda_1$ realna lastna vrednost in $v_1$ normiran lastni vektor.
Naj bo $\mathcal{B} = \{v_1, \dots, v_n\}$ ortonormirana baza za $\mathbb{R}^n$ (kjer je $v_1$ prvi vektor). Pustimo $U = \mathrm{Lin}\{v_1\}$. Potem je $U^\perp = \mathrm{Lin}\{v_2, \dots, v_n\}$.
Dokažimo, da je $U^\perp$ invarianten za $A$. Za vsak $u \in U^\perp$ in za $v_1$ velja $\langle Au, v_1 \rangle = \langle u, A^*v_1 \rangle = \langle u, Av_1 \rangle = \langle u, \lambda_1 v_1 \rangle = \lambda_1 \langle u, v_1 \rangle = \lambda_1 \cdot 0 = 0$.
Torej $Au \in U^\perp$. Matrika $A$ je tako v bazi $\mathcal{B}$ oblike $\begin{bmatrix} \lambda_1 & 0 \\ 0 & A_1 \end{bmatrix}$, kjer je $A_1$ simetrična $(n-1) \times (n-1)$ matrika. Po indukcijski predpostavki obstaja ortogonalna matrika $P_1$ in diagonalna matrika $D_1$ tako, da $A_1 = P_1 D_1 P_1^{-1}$. Sestavimo matriko $P = \begin{bmatrix} 1 & 0 \\ 0 & P_1 \end{bmatrix}$, ki je ortogonalna. Potem $A = P \begin{bmatrix} \lambda_1 & 0 \\ 0 & D_1 \end{bmatrix} P^{-1}$, kar dokazuje izrek.

### Primer

Naj bo $A = \begin{bmatrix} 1 & 1 & 1 \\ 1 & 3 & -1 \\ 1 & -1 & 3 \end{bmatrix}$. Poišči tako ortogonalno matriko $P$ in tako diagonalno matriko $D$, da je $A = PDP^{-1}$.

**Rešitev:**
Karakteristični polinom matrike $A$ je $\det(A - \lambda I) = -\lambda^3 + 7\lambda^2 - 12\lambda = -\lambda(\lambda - 3)(\lambda - 4)$.
Lastne vrednosti so $\lambda_1 = 4, \lambda_2 = 3, \lambda_3 = 0$.

Lastni vektorji, ki pripadajo lastnim vrednostim $4, 3, 0$ (v tem vrstnem redu) so:
Za $\lambda = 4$: $v_1 = \begin{bmatrix} 0 \\ -1 \\ 1 \end{bmatrix}$
Za $\lambda = 3$: $v_2 = \begin{bmatrix} 1 \\ 1 \\ 1 \end{bmatrix}$
Za $\lambda = 0$: $v_3 = \begin{bmatrix} -2 \\ 1 \\ 1 \end{bmatrix}$

Očitno so to vektorji paroma ortogonalni:
$\langle v_1, v_2 \rangle = 0(1) + (-1)(1) + 1(1) = 0$
$\langle v_1, v_3 \rangle = 0(-2) + (-1)(1) + 1(1) = 0$
$\langle v_2, v_3 \rangle = 1(-2) + 1(1) + 1(1) = 0$

Normirajmo jih:
$||v_1|| = \sqrt{0^2 + (-1)^2 + 1^2} = \sqrt{2} \implies \hat{v}_1 = \frac{1}{\sqrt{2}}\begin{bmatrix} 0 \\ -1 \\ 1 \end{bmatrix}$
$||v_2|| = \sqrt{1^2 + 1^2 + 1^2} = \sqrt{3} \implies \hat{v}_2 = \frac{1}{\sqrt{3}}\begin{bmatrix} 1 \\ 1 \\ 1 \end{bmatrix}$
$||v_3|| = \sqrt{(-2)^2 + 1^2 + 1^2} = \sqrt{6} \implies \hat{v}_3 = \frac{1}{\sqrt{6}}\begin{bmatrix} -2 \\ 1 \\ 1 \end{bmatrix}$

Iskana matrika $P$ je torej (stolpci so normirani lastni vektorji):
$$ P = \begin{bmatrix} 0 & 1/\sqrt{3} & -2/\sqrt{6} \\ -1/\sqrt{2} & 1/\sqrt{3} & 1/\sqrt{6} \\ 1/\sqrt{2} & 1/\sqrt{3} & 1/\sqrt{6} \end{bmatrix} $$
Iskana diagonalna matrika $D$ pa je (na diagonali so lastne vrednosti v enakem vrstnem redu kot lastni vektorji v $P$):
$$ D = \begin{bmatrix} 4 & 0 & 0 \\ 0 & 3 & 0 \\ 0 & 0 & 0 \end{bmatrix} $$

## 8. Normalne matrike

Običajno matrika ne komutira s svojo adjungirano matriko. Kadar pa komutira, ima zelo lepe lastnosti.

### Definicija normalne matrike

Kompleksna matrika $A$ je **normalna**, če zadošča $A^*A = AA^*$.

### Trditev

Vsaka normalna matrika je kvadratna.

**Dokaz:**
Če je $A$ matrika dimenzij $m \times n$, potem je $A^* = (\overline{A})^T$ matrika dimenzij $n \times m$. Matrika $A^*A$ je potem $n \times n$ matrika, matrika $AA^*$ pa $m \times m$ matrika. Če je $A$ normalna ($A^*A = AA^*$), potem velja $n=m$, torej je $A$ kvadratna matrika.

### Primeri normalnih matrik

1.  **Hermitske matrike so normalne:** Če je $A$ hermitska, potem velja $A^* = A$. Odtod sledi $A^*A = A \cdot A = A^2$ in $AA^* = A \cdot A = A^2$. Torej $A^*A = AA^*$, kar pomeni, da je $A$ normalna matrika.
2.  **Unitarne matrike so normalne:** Če je $A$ unitarna, potem je $A^* = A^{-1}$. Odtod sledi $A^*A = A^{-1}A = I$ in $AA^* = AA^{-1} = I$. Torej $A^*A = AA^*$, kar pomeni, da je $A$ normalna matrika.
3.  **Diagonalne matrike so normalne:** Če je $A$ diagonalna, potem je tudi $A^*$ diagonalna. Dve diagonalni matriki vedno komutirata, zato je $A^*A = AA^*$. Torej je $A$ normalna matrika.
4.  **Iz $A = A^T$ ne sledi nujno, da je $A$ normalna:** Matrika $A = \begin{bmatrix} 1 & i \\ i & 0 \end{bmatrix}$ zadošča $A = A^T$, vendar ni normalna.
    $A^* = \begin{bmatrix} 1 & -i \\ -i & 0 \end{bmatrix}$.
    $A^*A = \begin{bmatrix} 1 & -i \\ -i & 0 \end{bmatrix} \begin{bmatrix} 1 & i \\ i & 0 \end{bmatrix} = \begin{bmatrix} 1 + (-i)i & i + (-i)0 \\ -i + 0i & (-i)i + 0 \end{bmatrix} = \begin{bmatrix} 2 & i \\ -i & 1 \end{bmatrix}$.
    $AA^* = \begin{bmatrix} 1 & i \\ i & 0 \end{bmatrix} \begin{bmatrix} 1 & -i \\ -i & 0 \end{bmatrix} = \begin{bmatrix} 1 + i(-i) & -i + i0 \\ i + 0(-i) & i(-i) + 0 \end{bmatrix} = \begin{bmatrix} 2 & -i \\ i & 1 \end{bmatrix}$.
    Ker $A^*A \ne AA^*$, matrika $A$ ni normalna.

### Primer 5: Normalne $2 \times 2$ matrike

Matrika $A = \begin{bmatrix} a & b \\ c & d \end{bmatrix}$ je normalna natanko tedaj, ko velja $|b| = |c|$ in $c(a - d) = b(\overline{a} - \overline{d})$.

**Dokaz:**
$A^* = \begin{bmatrix} \overline{a} & \overline{c} \\ \overline{b} & \overline{d} \end{bmatrix}$.
$A^*A = \begin{bmatrix} \overline{a} & \overline{c} \\ \overline{b} & \overline{d} \end{bmatrix} \begin{bmatrix} a & b \\ c & d \end{bmatrix} = \begin{bmatrix} \overline{a}a + \overline{c}c & \overline{a}b + \overline{c}d \\ \overline{b}a + \overline{d}c & \overline{b}b + \overline{d}d \end{bmatrix}$.
$AA^* = \begin{bmatrix} a & b \\ c & d \end{bmatrix} \begin{bmatrix} \overline{a} & \overline{c} \\ \overline{b} & \overline{d} \end{bmatrix} = \begin{bmatrix} a\overline{a} + b\overline{b} & a\overline{c} + b\overline{d} \\ c\overline{a} + d\overline{b} & c\overline{c} + d\overline{d} \end{bmatrix}$.
Matrika $A$ je normalna natanko tedaj, ko $A^*A = AA^*$, kar pomeni, da morajo biti vsi elementi enaki:
1.  $\overline{a}a + \overline{c}c = a\overline{a} + b\overline{b} \implies |c|^2 = |b|^2 \implies |c| = |b|$.
2.  $\overline{a}b + \overline{c}d = a\overline{c} + b\overline{d}$.
3.  $\overline{b}a + \overline{d}c = c\overline{a} + d\overline{b}$.
4.  $\overline{b}b + \overline{d}d = c\overline{c} + d\overline{d} \implies |b|^2 = |c|^2 \implies |b| = |c|$.

Prva in četrta enakost sta ekvivalentni z $|b| = |c|$.
Tretja enakost je konjugirana druga enakost. Torej sta druga in tretja enakost ekvivalentni z $c(\overline{a} - \overline{d}) = b(\overline{a} - \overline{d})$, kar je ekvivalentno $c(a - d) = b(\overline{a} - \overline{d})$.

### Lastne vrednosti in lastni vektorji normalnih matrik

Če je $\lambda$ lastna vrednost matrike $A$, potem vemo, da je $\overline{\lambda}$ lastna vrednost matrike $A^*$. Vemo tudi, da v splošnem iz $Av = \lambda v$ ne sledi $A^*v = \overline{\lambda}v$. Velja pa to za normalne matrike, kar bomo dokazali v dveh korakih.

**Trditev:**
Če je matrika $A$ normalna, potem je za vsak $\lambda \in \mathbb{C}$ tudi $A - \lambda I$ normalna.

**Dokaz:**
Označimo $B = A - \lambda I$. Iz lastnosti adjungiranja sledi, da je $B^* = A^* - \overline{\lambda}I$.
Ker je $A$ normalna, velja $A^*A = AA^*$. Odtod sledi:
$BB^* = (A - \lambda I)(A^* - \overline{\lambda}I) = AA^* - \lambda A^* - \overline{\lambda}A + \lambda \overline{\lambda}I$.
$B^*B = (A^* - \overline{\lambda}I)(A - \lambda I) = A^*A - \lambda A^* - \overline{\lambda}A + \overline{\lambda} \lambda I$.
Ker $AA^* = A^*A$ in $\lambda \overline{\lambda} = \overline{\lambda}\lambda$, sledi $BB^* = B^*B$. Torej je $A - \lambda I$ normalna.

**Trditev:**
Če je matrika $A$ normalna, potem imata $A$ in $A^*$ enake lastne vektorje.

**Dokaz:**
Naj bo $\lambda$ lastna vrednost normalne matrike $A$. Po prejšnji trditvi je tudi $B = A - \lambda I$ normalna matrika. Vemo že, da za normalne matrike velja $\mathrm{Ker} B^*B = \mathrm{Ker} B$.
Ker je $B$ normalna, velja $B^*B = BB^*$. Torej $\mathrm{Ker} B = \mathrm{Ker} B^*B = \mathrm{Ker} BB^* = \mathrm{Ker} B^*$.
Zato za normalno matriko $A$ velja $\mathrm{Ker}(A - \lambda I) = \mathrm{Ker}(A^* - \overline{\lambda}I)$. To pomeni, da je $v$ lastni vektor za $A$ s lastno vrednostjo $\lambda$ natanko tedaj, ko je $v$ lastni vektor za $A^*$ z lastno vrednostjo $\overline{\lambda}$.

### Izrek (Spektralni izrek za normalne matrike)

Vsaka normalna matrika je podobna diagonalni matriki.

**Dokaz (skica):**
Radi bi dokazali, da je vsak korenski podprostor normalne matrike že kar lastni podprostor. Iz korenskega razcepa potem sledi, da ima matrika $n$ linearno neodvisnih lastnih vektorjev, torej se da diagonalizirati.
Naj bo $A$ normalna matrika in naj bo $\lambda$ njena lastna vrednost. Vemo, da je potem tudi matrika $B = A - \lambda I$ normalna. Radi bi dokazali, da velja $\mathrm{Ker} B^2 = \mathrm{Ker} B$.
Vemo že, da za vsako matriko $B$ velja $\mathrm{Ker} B^*B = \mathrm{Ker} B$. (Formula (8) iz prejšnjega predavanja.)
Če v to formulo namesto $B$ vstavimo $B^*B$, dobimo $\mathrm{Ker}(B^*B)^*B^*B = \mathrm{Ker} B^*B$.
Ker je $B$ normalna, je tudi $B^*B$ normalna ($ (B^*B)^*(B^*B) = B^*B B^*B = B^* (BB^*)B = B^* (B^*B)B = (B^*B)(B^*B) = (B^*B)^*(B^*B) $). Torej $\mathrm{Ker}(B^*B)^2 = \mathrm{Ker} B^*B$.
Če v formulo $\mathrm{Ker} X^*X = \mathrm{Ker} X$ namesto $X$ vstavimo $B^2$, dobimo $\mathrm{Ker}(B^2)^*B^2 = \mathrm{Ker} B^2$.
Ker je $B$ normalna preslikava, velja $B^* = B$. Torej $(B^2)^* B^2 = (B^*B^*)(B B) = B^* (B^*B) B = B^* (BB^*) B = (B^*B)(B^*B) = (B^*B)^2$.
Torej $\mathrm{Ker} B^2 = \mathrm{Ker} B$.
Odtod s popolno indukcijo dokažemo, da velja $\mathrm{Ker} B^k = \mathrm{Ker} B$ za vsak $k$. To pomeni, da je korenski podprostor za $\lambda$ res enak lastnemu podprostoru za $\lambda$.

### Izrek (Lastni podprostori normalne matrike)

Lastni podprostori normalne matrike so paroma ortogonalni.

**Dokaz:**
Recimo, da je $A$ normalna matrika in da sta $\lambda$ in $\mu$ različni lastni vrednosti za $A$. Radi bi pokazali, da je vsak vektor $u \in \mathrm{Ker}(A - \lambda I)$ pravokoten na vsak vektor $v \in \mathrm{Ker}(A - \mu I)$ glede na standardni skalarni produkt na $\mathbb{C}^n$.
Dokazali smo že, da za normalne matrike velja $\mathrm{Ker}(A - \mu I) = \mathrm{Ker}(A^* - \overline{\mu}I)$.
Torej je $A^*v = \overline{\mu}v$.
$\lambda \langle u, v \rangle = \langle \lambda u, v \rangle = \langle Au, v \rangle = \langle u, A^*v \rangle = \langle u, \overline{\mu}v \rangle = \mu \langle u, v \rangle$.
Ker je $\mu \ne \lambda$, odtod sledi $\langle u, v \rangle = 0$, kar smo želeli dokazati.

### Izrek (Spektralni izrek - unitarna diagonalizacija)

Matrika $A$ je normalna natanko tedaj, ko obstajata taka diagonalna matrika $D$ in taka unitarna matrika $P$, da velja $A = PDP^{-1}$.

**Dokaz (prvi del - "če je A unitarno diagonalizabilna, potem je normalna"):**
Če je $A = PDP^{-1}$, kjer je $D$ diagonalna in $P$ unitarna matrika (torej $P^{-1} = P^*$), potem velja:
$A^*A = (PDP^*)^*(PDP^*) = (P^*)^*D^*P^*PDP^* = PD^*P^*PDP^*$.
$AA^* = PDP^*(PDP^*)^* = PDP^*(P^*)^*D^*P^* = PDP^*PD^*P^*$.
Ker je $D$ diagonalna, je $D^*D = DD^*$ (ker diagonalne matrike komutirajo).
Ker je $P$ unitarna, je $P^*P = I$.
Torej $A^*A = PD^*D P^*$.
In $AA^* = PDD^* P^*$.
Ker je $D^*D = DD^*$, sledi $A^*A = AA^*$, torej je $A$ normalna.

**Dokaz (drugi del - "če je A normalna, potem je unitarno diagonalizabilna"):**
Privzemimo sedaj, da je $A$ normalna $n \times n$ matrika. Vemo, da je vsota vseh lastnih podprostorov matrike $A$ enaka $\mathbb{C}^n$ in da so lastni podprostori paroma pravokotni glede na standardni skalarni produkt. Če za vsak lastni podprostor izberemo ortonormirano bazo, potem je unija teh baz ortonormirana baza za $\mathbb{C}^n$. Označimo to ortonormirano bazo z $v_1, \dots, v_n$. Naj bodo $\lambda_1, \dots, \lambda_n$ pripadajoče lastne vrednosti.
Označimo $P = \begin{bmatrix} v_1 & \dots & v_n \end{bmatrix}$ in $D = \begin{bmatrix} \lambda_1 & & 0 \\ & \ddots & \\ 0 & & \lambda_n \end{bmatrix}$.
Ker je $v_1, \dots, v_n$ ortonormirana baza glede na standardni skalarni produkt, je $P$ unitarna matrika (torej $P^*P = I$).
Ker so $v_1, \dots, v_n$ lastni vektorji z lastnimi vrednostmi $\lambda_1, \dots, \lambda_n$, je:
$AP = A \begin{bmatrix} v_1 & \dots & v_n \end{bmatrix} = \begin{bmatrix} Av_1 & \dots & Av_n \end{bmatrix} = \begin{bmatrix} \lambda_1 v_1 & \dots & \lambda_n v_n \end{bmatrix} = \begin{bmatrix} v_1 & \dots & v_n \end{bmatrix} D = PD$.
Odtod sledi $A = PDP^{-1}$.

### Normalne linearne preslikave

Oglejmo si še normalne preslikave in njihovo zvezo z normalnimi matrikami.

**Definicija:**
Naj bo $V$ končnorazsežen vektorski prostor s skalarnim produktom. Linearna preslikava $L: V \to V$ je **normalna**, če velja $L^*L = LL^*$.

**Trditev:**
Naj bo $V$ končnorazsežen vektorski prostor s skalarnim produktom in $\mathcal{B}$ ortonormirana baza za $V$. Potem je linearna preslikava $L: V \to V$ normalna natanko tedaj, ko je njena matrika $[L]_{\mathcal{B}}$ normalna.

**Dokaz:**
Vemo, da velja $[L^*]_{\mathcal{B}} = ([L]_{\mathcal{B}})^*$. Odtod sledi, da je
$[L^*L]_{\mathcal{B}} = [L^*]_{\mathcal{B}}[L]_{\mathcal{B}} = ([L]_{\mathcal{B}})^*[L]_{\mathcal{B}}$ in
$[LL^*]_{\mathcal{B}} = [L]_{\mathcal{B}}[L^*]_{\mathcal{B}} = [L]_{\mathcal{B}}([L]_{\mathcal{B}})^*$.
Torej velja $([L]_{\mathcal{B}})^*[L]_{\mathcal{B}} = [L]_{\mathcal{B}}([L]_{\mathcal{B}})^*$ natanko tedaj, ko je $[L^*L]_{\mathcal{B}} = [LL^*]_{\mathcal{B}}$. Slednje velja natanko tedaj, ko je $L^*L = LL^*$.

**Opomba:** Naš glavni izrek za normalne matrike lahko povemo tudi takole: Linearna preslikava $L: V \to V$ je normalna natanko tedaj ko obstaja taka ortonormirana baza $\mathcal{B}$ za $V$, da je matrika $[L]_{\mathcal{B}}$ diagonalna. (Velja nad $\mathbb{C}$.)

## 8. Izometrije

Izometrije so preslikave, ki ohranjajo razdaljo. Ker razdaljo definiramo z normo, jih definiramo kot linearne preslikave, ki ohranjajo normo.

### Definicija izometrije

Naj bosta $U$ in $V$ končnorazsežna vektorska prostora s skalarnim produktom. Pravimo, da je linearna preslikava $L: U \to V$ **izometrija**, če za vsak $u \in U$ velja $||Lu||_V = ||u||_U$.

**Opomba:** Vsaka izometrija je injektivna, saj iz $Lu = 0$ in iz $||Lu|| = ||u||$ sledi $u = 0$. Izometrija je surjektivna natanko tedaj, ko je $\dim U = \dim V$.

### Primer izometrije, ki ni surjektivna

Preslikava $L: \mathbb{C}^2 \to \mathbb{C}^5$, kjer $L(x, y) = (x, y, 0, 0, 0)$ je izometrija, če sta $\mathbb{C}^2$ in $\mathbb{C}^5$ opremljena s standardnim skalarnim produktom.
$||L(x,y)||^2 = |x|^2 + |y|^2 + 0 + 0 + 0 = |x|^2 + |y|^2 = ||(x,y)||^2$.
Ker je $\dim \mathbb{C}^2 = 2 < \dim \mathbb{C}^5 = 5$, $L$ ni surjektivna.

**Opomba:** Kadar je $V = U$ pravimo izometriji tudi **unitarna linearna preslikava**. Vsaka unitarna linearna preslikava je bijektivna.

### Karakterizacije izometrij

**Trditev:**
Za linearno preslikavo $L: U \to V$, kjer sta $U$ in $V$ končnorazsežna vektorska prostora s skalarnim produktom, so ekvivalentne trditve:
1.  $L$ je izometrija.
2.  $\langle Lu, Lu' \rangle_V = \langle u, u' \rangle_U$ za vsaka $u, u' \in U$. (Preslikava ohranja skalarni produkt).
3.  $L^*L = \mathrm{id}_U$ (identična preslikava na $U$).
4.  Za vsako ortonormirano bazo $u_1, \dots, u_n$ v $U$ je $Lu_1, \dots, Lu_n$ ortonormirana množica v $V$.
5.  Za neko ortonormirano bazo $u_1, \dots, u_n$ v $U$ je $Lu_1, \dots, Lu_n$ ortonormirana množica v $V$.

**Opomba:** Te karakterizacije seveda veljajo tudi za unitarne linearne preslikave, saj so te posebni primeri izometrij (kadar $U=V$).

**Dokaz (ekvivalenca med (1) in (2)):**
*   **$(2) \implies (1)$:** Če velja (2), potem je $||Lu||^2 = \langle Lu, Lu \rangle = \langle u, u \rangle = ||u||^2$ za vsak $u \in U$, torej je $L$ izometrija.
*   **$(1) \implies (2)$:** Recimo, da je $L$ izometrija ($||Lu|| = ||u||$).
    V kompleksnem primeru velja polarizacijska identiteta:
    $\langle Lu, Lu' \rangle = \frac{1}{4} \sum_{k=0}^3 i^k ||Lu + i^k Lu'||^2 = \frac{1}{4} \sum_{k=0}^3 i^k ||L(u + i^k u')||^2$.
    Ker je $L$ izometrija, velja $||L(u + i^k u')||^2 = ||u + i^k u'||^2$.
    Torej $\langle Lu, Lu' \rangle = \frac{1}{4} \sum_{k=0}^3 i^k ||u + i^k u'||^2 = \langle u, u' \rangle$.
    Torej $L$ zadošča (2). Podobno velja tudi v realnem primeru, samo drugo polarizacijsko identiteto uporabimo.

**Dokaz (ekvivalenca med (2) in (3)):**
*   **$(3) \implies (2)$:** Če velja (3), potem je $L^*L = \mathrm{id}_U$. Za vsaka $u, u' \in U$ velja:
    $\langle Lu, Lu' \rangle_V = \langle u, L^*Lu' \rangle_U = \langle u, \mathrm{id}_U u' \rangle_U = \langle u, u' \rangle_U$.
    Torej velja (2).
*   **$(2) \implies (3)$:** Obratno, če velja (2), potem je za vsaka $u, u' \in U$:
    $\langle u, L^*Lu' \rangle_U = \langle Lu, Lu' \rangle_V = \langle u, u' \rangle_U$.
    Odtod sledi $\langle u, L^*Lu' - u' \rangle_U = 0$ za vsaka $u, u' \in U$. Če vstavimo $u = L^*Lu' - u'$, dobimo $||L^*Lu' - u'||_U^2 = 0$, kar pomeni $L^*Lu' = u'$ za vsak $u' \in U$. Torej velja (3), $L^*L = \mathrm{id}_U$.

**Dokaz (ekvivalenca med (1), (4) in (5)):**
Očitno iz (2) sledi (4) (če $u_i$ tvorijo ONB, potem $Lu_i$ tvorijo ortonormirano množico).
In iz (4) sledi (5) (splošno vedno implicira obstoj).
Dokažimo še, da iz (5) sledi (1).
Naj bo $u_1, \dots, u_n$ taka ortonormirana baza za $U$, da je $Lu_1, \dots, Lu_n$ ortonormirana množica v $V$. Vzemimo poljuben element $u \in U$ in ga razvijmo po ortonormirani bazi; recimo $u = \alpha_1 u_1 + \dots + \alpha_n u_n$. Po Parsevalovi identiteti velja $||u||^2 = |\alpha_1|^2 + \dots + |\alpha_n|^2$.
Podobno iz $Lu = \alpha_1 Lu_1 + \dots + \alpha_n Lu_n$ in ortonormiranosti $Lu_1, \dots, Lu_n$ sledi, da je $||Lu||^2 = |\alpha_1|^2 + \dots + |\alpha_n|^2$.
Torej je $||Lu|| = ||u||$ za vsak $u \in U$.

### Matrika izometrije

**Trditev:**
Naj bosta $U, V$ končnorazsežna vektorska prostora s skalarnim produktom. Naj bo $\mathcal{B}$ ortonormirana baza za $U$ in naj bo $\mathcal{C}$ ortonormirana baza za $V$. Potem je linearna preslikava $L: U \to V$ izometrija natanko tedaj, ko za njeno matriko $A = [L]_{\mathcal{C} \leftarrow \mathcal{B}}$ velja $A^*A = I$.

**Dokaz:**
Vemo, da je linearna preslikava $L: U \to V$ izometrija natanko tedaj, ko je $L^*L = \mathrm{id}_U$.
Očitno to velja natanko tedaj, ko je $[L^*L]_{\mathcal{B}} = [\mathrm{id}_U]_{\mathcal{B}} = I$.
Upoštevajmo še, da je $[L^*L]_{\mathcal{B}} = [L^*]_{\mathcal{B} \leftarrow \mathcal{C}}[L]_{\mathcal{C} \leftarrow \mathcal{B}}$ in $[L^*]_{\mathcal{B} \leftarrow \mathcal{C}} = ([L]_{\mathcal{C} \leftarrow \mathcal{B}})^*$.
Torej je $L$ izometrija natanko tedaj, ko je $([L]_{\mathcal{C} \leftarrow \mathcal{B}})^* ([L]_{\mathcal{C} \leftarrow \mathcal{B}}) = I$. Če označimo $A = [L]_{\mathcal{C} \leftarrow \mathcal{B}}$, to pomeni $A^*A = I$.

**Opomba:** Če ortonormirani bazi $\mathcal{B}$ in $\mathcal{C}$ spretno izberemo, se matrika izometrije zelo poenostavi. Izberimo tako ortonormirano bazo $\mathcal{B} = \{u_1, \dots, u_n\}$ v $U$, da je $v_1 = Lu_1, \dots, v_n = Lu_n$ ortonormirana množica v $V$. Naj bo $v_{n+1}, \dots, v_m$ njena dopolnitev do ortonormirane baze $\mathcal{C}$ za $V$. Potem je matrika $[L]_{\mathcal{C} \leftarrow \mathcal{B}}$ oblike $\begin{bmatrix} I_n \\ 0 \end{bmatrix}$.

### Trditev (Stolpci matrike $A^*A = I$)

Za pravokotno kompleksno matriko $A$ velja $A^*A = I$ natanko tedaj, ko so stolpci $A$ ortonormirana množica glede na standardni skalarni produkt.

**Dokaz:**
Naj bodo $v_1, \dots, v_n$ stolpci matrike $A$. Potem velja:
$A^*A = \begin{bmatrix} v_1^* \\ \vdots \\ v_n^* \end{bmatrix} \begin{bmatrix} v_1 & \dots & v_n \end{bmatrix} = \begin{bmatrix} v_1^*v_1 & \dots & v_1^*v_n \\ \vdots & \ddots & \vdots \\ v_n^*v_1 & \dots & v_n^*v_n \end{bmatrix}$.
kjer je $v_i^*v_j = \langle v_j, v_i \rangle$ standardni skalarni produkt. Odtod sledi, da velja $A^*A = I$ natanko tedaj, ko je:
$\langle v_j, v_i \rangle = \begin{cases} 1 & \text{če } i = j \\ 0 & \text{če } i \ne j \end{cases}$.
Torej natanko tedaj, ko je $\{v_1, \dots, v_n\}$ ortonormirana množica glede na standardni skalarni produkt.

### Povzetek ugotovitev o matrikah izometrij

**Trditev:**
Za vsako kompleksno $m \times n$ matriko $A$, kjer je $m \ge n$, so ekvivalentne naslednje trditve:
1.  $A^*A = I_n$.
2.  Stolpci matrike $A$ so ortonormirana množica v $\mathbb{C}^m$ glede na standardni skalarni produkt.
3.  Linearna preslikava $L_A: \mathbb{C}^n \to \mathbb{C}^m$, $v \mapsto Av$ je izometrija.
4.  Obstaja taka izometrija $L: U \to V$, kjer $\dim U = n$ in $\dim V = m$, in taki ortonormirani bazi $\mathcal{B}$ za $U$ in $\mathcal{C}$ za $V$, da velja $A = [L]_{\mathcal{C} \leftarrow \mathcal{B}}$.
5.  Obstaja taka unitarna $m \times m$ matrika $P$ in taka unitarna $n \times n$ matrika $Q$, da velja $A = P \begin{bmatrix} I_n \\ 0 \end{bmatrix} Q$.

## 9. Ortogonalne in unitarne matrike

Začnimo kar z definicijo.

### Definicija ortogonalne in unitarne matrike

Naj bo $A$ kompleksna kvadratna matrika, ki zadošča $A^*A = I$. Potem pravimo, da je $A$ **unitarna matrika**. Realni unitarni matriki pravimo tudi **ortogonalna matrika**.

**Opomba:** Vemo, da za kvadratne matrike iz lastnosti $A^*A = I$ sledi $AA^* = I$. Odtod sledijo naslednje preproste lastnosti unitarnih matrik:
*   Vsaka unitarna matrika je normalna.
*   Vsaka unitarna matrika $A$ je obrnljiva in zadošča $A^{-1} = A^*$.
*   Če je $A$ unitarna matrika, potem je tudi $A^*$ unitarna matrika.

**Opomba:** Dokazali smo že, da je kvadratna matrika unitarna natanko tedaj, ko njeni stolpci tvorijo ortonormirano bazo glede na standardni skalarni produkt. To nam da veliko primerov unitarnih matrik.

### Primer: Klasifikacija ortogonalnih $2 \times 2$ matrik

Za vsak realen $\varphi$ sta matriki
$A = \begin{bmatrix} \cos\varphi & -\sin\varphi \\ \sin\varphi & \cos\varphi \end{bmatrix}$ in $B = \begin{bmatrix} \cos\varphi & \sin\varphi \\ \sin\varphi & -\cos\varphi \end{bmatrix}$
ortogonalni. Vsaka ortogonalna $2 \times 2$ matrike je ene od teh dveh oblik.

**Dokaz:**
Obe matriki sta realni, kvadratni in zadoščata $A^TA = I$, torej sta ortogonalni.
Če je matrika $M = \begin{bmatrix} a & b \\ c & d \end{bmatrix}$ ortogonalna, potem velja $M^TM = I$, se pravi:
$\begin{bmatrix} a & c \\ b & d \end{bmatrix} \begin{bmatrix} a & b \\ c & d \end{bmatrix} = \begin{bmatrix} a^2+c^2 & ab+cd \\ ab+cd & b^2+d^2 \end{bmatrix} = \begin{bmatrix} 1 & 0 \\ 0 & 1 \end{bmatrix}$.
Iz $a^2+c^2 = 1$ sledi, da obstaja tak realen $\varphi$, da velja $a = \cos\varphi$ in $c = \sin\varphi$.
Podobno iz $b^2+d^2 = 1$ sledi, da obstaja tak realen $\psi$, da je $b = \cos\psi$ in $d = \sin\psi$.
Iz $ab+cd = 0$ potem sledi, da je $\cos\varphi\cos\psi + \sin\varphi\sin\psi = 0$.
To je $\cos(\varphi-\psi) = 0$. Odtod sledi, da je $\varphi-\psi = \frac{\pi}{2} + k\pi$, torej $\psi = \varphi - \frac{\pi}{2} - k\pi$.
Potem je:
$b = \cos\psi = \cos(\varphi - \frac{\pi}{2} - k\pi) = \sin(\varphi - k\pi) = (-1)^k \sin\varphi$.
$d = \sin\psi = \sin(\varphi - \frac{\pi}{2} - k\pi) = -\cos(\varphi - k\pi) = -(-1)^k \cos\varphi$.
Torej je matrika $M$ oblike:
$\begin{bmatrix} \cos\varphi & (-1)^k \sin\varphi \\ \sin\varphi & -(-1)^k \cos\varphi \end{bmatrix}$.
Za sode $k$ (npr. $k=0$) dobimo prvo matriko $A = \begin{bmatrix} \cos\varphi & \sin\varphi \\ \sin\varphi & -\cos\varphi \end{bmatrix}$ (tukaj je $\psi = \varphi - \pi/2$, torej $\cos\psi = \sin\varphi$, $\sin\psi = -\cos\varphi$).
Za lihe $k$ (npr. $k=1$) dobimo drugo matriko $B = \begin{bmatrix} \cos\varphi & -\sin\varphi \\ \sin\varphi & \cos\varphi \end{bmatrix}$ (tukaj je $\psi = \varphi - 3\pi/2$, torej $\cos\psi = -\sin\varphi$, $\sin\psi = \cos\varphi$).

### Unitarne matrike kot grupa

**Trditev:**
Množica vseh unitarnih $n \times n$ matrik je grupa za matrično množenje.

**Dokaz:**
*   **Zaprtost:** Če sta $A$ in $B$ unitarni matriki, potem velja $A^*A = I$ in $B^*B = I$.
    $(AB)^*(AB) = (B^*A^*)(AB) = B^*(A^*A)B = B^*IB = B^*B = I$.
    Torej je tudi $AB$ unitarna matrika.
*   **Asociativnost:** Matrično množenje je asociativno.
*   **Identiteta:** Identitetna matrika $I$ je unitarna ($I^*I=I$).
*   **Inverz:** Če je $A$ unitarna matrika, potem velja $A^{-1} = A^*$. Odtod sledi:
    $(A^{-1})^*A^{-1} = (A^*)^*A^{-1} = AA^{-1} = I$.
    Torej je tudi $A^{-1}$ unitarna matrika.

### Grupe matrik

*   Za vsak obseg $F$ označimo z $\mathrm{GL}(n, F)$ grupo vseh obrnljivih $n \times n$ matrik z elementi iz $F$. Tej grupi pravimo **splošna linearna grupa**.
*   Grupo vseh $n \times n$ matrik nad $F$ z determinanto $1$ označimo z $\mathrm{SL}(n, F)$ in ji pravimo **specialna linearna grupa**.
*   Grupo vseh unitarnih $n \times n$ matrik označimo z $\mathrm{U}(n)$ in ji pravimo **splošna unitarna grupa**.
*   Grupo vseh unitarnih $n \times n$ matrik z determinanto $1$ označimo z $\mathrm{SU}(n)$ in ji pravimo **specialna unitarna grupa**.
*   Grupo vseh ortogonalnih $n \times n$ matrik označimo z $\mathrm{O}(n)$ in ji pravimo **splošna ortogonalna grupa**.
*   Grupo vseh ortogonalnih $n \times n$ matrik z determinanto $1$ označimo z $\mathrm{SO}(n)$ in ji pravimo **specialna ortogonalna grupa**.
Grupi $\mathrm{O}(2)$ in $\mathrm{SO}(2)$ smo eksplicitno izračunali.

Relacije med grupami:
$\mathrm{GL}(n, \mathbb{C}) \supset \mathrm{U}(n)$
$\quad \cap \quad \cap$
$\mathrm{SL}(n, \mathbb{C}) \supset \mathrm{SU}(n)$

$\mathrm{GL}(n, \mathbb{R}) \supset \mathrm{O}(n)$
$\quad \cap \quad \cap$
$\mathrm{SL}(n, \mathbb{R}) \supset \mathrm{SO}(n)$

### Lastne vrednosti unitarnih matrik

**Trditev:**
Lastne vrednosti unitarne matrike imajo absolutno vrednost $1$.

**Prvi dokaz:**
Naj bo $\lambda$ lastna vrednost za unitarno matriko $A$ in naj bo $v$ pripadajoči lastni vektor. Ker je $A^*A = I$, velja:
$\langle v, v \rangle = \langle v, Iv \rangle = \langle v, A^*Av \rangle = \langle Av, Av \rangle = \langle \lambda v, \lambda v \rangle = \lambda \overline{\lambda} \langle v, v \rangle = |\lambda|^2 \langle v, v \rangle$.
Ker je $v \ne 0$, lahko krajšamo $\langle v, v \rangle$ in dobimo $1 = |\lambda|^2$. Torej $|\lambda| = 1$.

**Drugi dokaz:**
Ker je vsaka unitarna matrika normalna, ima faktorizacijo $A = PDP^{-1}$, kjer je $D$ diagonalna in $P$ unitarna matrika. Odtod sledi:
$D^*D = (P^*AP)^*(P^*AP) = (P^*A^*P)(P^*AP) = P^*A^*P P^*AP = P^*A^*IA P = P^*A^*A P = P^*IP = I$.
Torej imajo diagonalni elementi matrike $D$ absolutno vrednost $1$. Toda diagonalni elementi matrike $D$ so ravno lastne vrednosti matrike $A$.

### Lastni vektorji unitarnih matrik

**Trditev:**
Različnim lastnim vrednostim unitarne matrike pripadata ortogonalna lastna vektorja.

**Prvi dokaz:**
Vsaka unitarna matrika je normalna in za normalne matrike smo to že dokazali.

**Drugi dokaz:**
Naj bo $Au = \lambda u$ in $Av = \mu v$ in $\lambda \ne \mu$. Ker je $A$ unitarna, je $\langle v, v \rangle = |\lambda|^2 \langle v, v \rangle$. Torej $|\lambda|=1$. Podobno $|\mu|=1$.
$\lambda \langle u, v \rangle = \langle \lambda u, v \rangle = \langle Au, v \rangle = \langle u, A^*v \rangle$.
Ker je $A$ unitarna, je $A^*=A^{-1}$. Torej $A^*v = A^{-1}v$.
Torej $\lambda \langle u, v \rangle = \langle u, A^{-1}v \rangle$.
Uporabimo $A v = \mu v \implies v = \mu A^{-1}v \implies A^{-1}v = \overline{\mu} v$ (ker $|\mu|=1 \implies \mu \overline{\mu}=1 \implies \mu^{-1}=\overline{\mu}$).
Zato $\lambda \langle u, v \rangle = \langle u, \overline{\mu}v \rangle = \mu \langle u, v \rangle$.
Odtod $(\lambda - \mu)\langle u, v \rangle = 0$. Ker $\lambda \ne \mu$, sledi $\langle u, v \rangle = 0$.