**Definicija homomorfizma**
Naj bosta $(M_1, \circ_1)$ in $(M_2, \circ_2)$ dva grupoida. Pravimo, da je preslikava $f: M_1 \to M_2$ homomorfizem grupoidov, če za vsaka $x, y \in M_1$ velja
$$f(x \circ_1 y) = f(x) \circ_2 f(y) \quad (1)$$

**Primeri homomorfizmov**

Preslikava $f(x) = 2x$ je homomorfizem polgrup iz $(\mathbb{N}, +)$ v $(\mathbb{N}, +)$

$$f(x + y) = 2(x + y) = 2x + 2y = f(x) + f(y)$$

Preslikava $f(x) = x^2$ je homomorfizem monoidov iz $(\mathbb{N}, \cdot)$ v $(\mathbb{N}, \cdot)$, 

$$f(xy) = (xy)^2 = x^2y^2 = f(x)f(y)$$

**Primer: Homomorfizem polgrup, ki ne slika enote v enoto**

Vemo, da je $(\mathbb{Z}, \cdot)$ polgrupa z enoto $1$ in da je $(\mathbb{Z} \times \mathbb{Z}, \circ)$, kjer $(a, b) \circ (c, d) = (ac, bd)$, polgrupa z enoto $(1, 1)$. 

Preslikava $f: \mathbb{Z} \to \mathbb{Z} \times \mathbb{Z}:$ $f(x) = (x, 0)$ je homomorfizem polgrup, ker $f(xy) = (xy, 0) = (x, 0) \circ (y, 0) = f(x) \circ f(y)$, ampak ne slika enote v enoto, ker $f(1) = (1, 0) \neq (1, 1)$.



>**Trditev**
>
>$f$ je homomorfizem monoidov iz monoida $(M_1, \circ_1)$ v monoid $(M_2, \circ_2)$. 
>
>Če je $a$ obrnljiv element v $(M_1, \circ_1)$, potem je $f(a)$ obrnljiv element v $(M_2, \circ_2)$ in velja $f(a)^{-1} = f(a^{-1})$.
>
>**Dokaz:** 
>
>Ker je element $a \in M_1$ obrnljiv, obstaja tak element $b \in M_1$, da velja $a \circ_1 b = e_1$ in $b \circ_1 a = e_1$. 
>
>Ker je $f : M_1 \to M_2$ homomorfizem monoidov, odtod sledi 
>
>$f(a) \circ_2 f(b) = f(a \circ_1 b) = f(e_1) = e_2$ in $f(b) \circ_2 f(a) = f(b \circ_1 a) = f(e_1) = e_2$. Torej je element $f(a)$ obrnljiv in velja $f(a)^{-1} = f(b)$. Ker je $b = a^{-1}$, sledi $f(a)^{-1} = f(a^{-1})$.

**Primer**
Determinanta $\det: M_n(\mathbb{R}) \to \mathbb{R}$ zadošča $\det AB = \det A \det B$ in $\det I_n = 1$. Torej je $\det$ homomorfizem monoidov iz $(M_n(\mathbb{R}), \cdot)$ v $(\mathbb{R}, \cdot)$. Po zgornji trditvi $\det$ slika obrnljive matrike v neničelna realna števila in velja $\det A^{-1} = \frac{1}{\det A}$.

**Primer: Homomorfizmi monoidov**
Naj bo $M$ množica vseh funkcij iz $\mathbb{R}$ v $\mathbb{R}$ oblike $\phi_{k,l}(x) = kx + l$ in naj bo operacija $\circ$ kompozitum funkcij. Iz $k(k'x + l') + l = kk'x + kl' + l$ sledi $\phi_{k,l} \circ \phi_{k',l'} = \phi_{kk', kl'+l}$. Enota te polgrupe je $\phi_{1,0} = \text{id}$. Preslikava
$$f(\phi_{k,l}) = \begin{bmatrix} k & l \\ 0 & 1 \end{bmatrix}$$
je homomorfizem monoidov iz $(M, \circ)$ v $(M_2(\mathbb{R}), \cdot)$, ker je
$$f(\text{id}) = f(\phi_{1,0}) = \begin{bmatrix} 1 & 0 \\ 0 & 1 \end{bmatrix} = I_2$$
$$f(\phi_{k,l} \circ \phi_{k',l'}) = f(\phi_{kk',kl'+l}) = \begin{bmatrix} kk' & kl'+l \\ 0 & 1 \end{bmatrix} = \begin{bmatrix} k & l \\ 0 & 1 \end{bmatrix} \begin{bmatrix} k' & l' \\ 0 & 1 \end{bmatrix} = f(\phi_{k,l})f(\phi_{k',l'})$$


***

**Definicija homomorfizma grup**
Homomorfizem grup iz grupe $(G_1, \circ_1)$ v grupo $(G_2, \circ_2)$ je taka preslikava $f: G_1 \to G_2$, ki zadošča $f(x \circ_1 y) = f(x) \circ_2 f(y)$ za vsaka $x, y \in G_1$.

>**Trditev**
Homomorfizem grup slika enoto prve grupe v enoto druge grupe in inverz vsakega elementa iz prve grupe v inverz njegove slike.
>
**Dokaz:**
Naj bo $\phi: G \to H$ homomorfizem grup, kjer sta $e_G$ in $e_H$ enoti grup $G$ in $H$.
>
Najprej dokažimo, da $\phi(e_G) = e_H$.
>
Uporabimo homomorfizem $\phi$: $\phi(g \cdot e_G) = \phi(g)$.
Zaradi definicije homomorfizma je $\phi(g) \cdot \phi(e_G) = \phi(g)$.
Pomnožimo to enačbo z leve z inverzom elementa $\phi(g)$ v grupi $H$:
$(\phi(g))^{-1} \cdot \phi(g) \cdot \phi(e_G) = (\phi(g))^{-1} \cdot \phi(g)$.
Ker je $(\phi(g))^{-1} \cdot \phi(g) = e_H$, dobimo $e_H \cdot \phi(e_G) = e_H$.
Sledi, da je $\phi(e_G) = e_H$.
>
Sedaj dokažimo, da $\phi(g^{-1}) = (\phi(g))^{-1}$ za vsak $g \in G$.
Uporabimo homomorfizem $\phi$: $\phi(g \cdot g^{-1}) = \phi(e_G)$.
Zaradi lastnosti homomorfizma in prvega dela dokaza je $\phi(g) \cdot \phi(g^{-1}) = e_H$.
Po definiciji inverza v grupi $H$ je element, ki ga pomnožimo z $\phi(g)$, da dobimo enoto $e_H$, ravno inverz elementa $\phi(g)$.
Torej, $\phi(g^{-1})$ je inverz elementa $\phi(g)$, kar zapišemo kot $\phi(g^{-1}) = (\phi(g))^{-1}$.

**Primeri homomorfizmov grup**
* Determinanta je homomorfizem grup iz $(\text{GL}_n(\mathbb{R}), \cdot)$ v $(\mathbb{R}^\times, \cdot)$, ker velja $\det AB = \det A \det B$.
* **Preslikava $\sigma \mapsto P_\sigma := [\mathbf{e}_{\sigma(1)} \ldots \mathbf{e}_{\sigma(n)}]$ je homomorfizem grup iz $(\text{S}_n, \circ)$ v $(\text{GL}_n(\mathbb{R}), \cdot)$, ker velja $P_{\sigma \circ \tau} = P_\sigma P_\tau$.**
* Signatura permutacije je homomorfizem grup iz $(\text{S}_n, \circ)$ v $(\mathbb{R}^\times, \cdot)$, ker velja $\text{sgn}(\sigma \circ \tau) = \text{sgn}(\sigma)\text{sgn}(\tau)$.

>**Trditev**
Če je $f$ homomorfizem grup iz grupe $(G_1, \circ_1)$ v grupo $(G_2, \circ_2)$ in je $g$ homomorfizem grup iz grupe $(G_2, \circ_2)$ v grupo $(G_3, \circ_3)$, potem je $g \circ f$ homomorfizem grup iz grupe $(G_1, \circ_1)$ v grupo $(G_3, \circ_3)$.
**Dokaz:** Vzemimo poljubna $x, y \in G_1$. Ker je $f$ homomorfizem, velja $f(x \circ_1 y) = f(x) \circ_2 f(y)$.
Ker je $g$ homomorfizem, velja $g(f(x) \circ_2 f(y)) = g(f(x)) \circ_3 g(f(y))$.
Torej je
$$(g \circ f)(x \circ_1 y) = $$ 
$$g(f(x \circ_1 y)) = $$$$g(f(x) \circ_2 f(y)) = $$$$g(f(x)) \circ_3 g(f(y)) $$$$= (g \circ f)(x) \circ_3 (g \circ f)(y)$$
***

**Definicija izomorfizma**
Bijektivnemu homomorfizmu grup pravimo **izomorfizem** grup. Dve grupi sta izomorfni, če obstaja izomorfizem grup in ene v drugo.


>**Trditev**
Če je $f$ homomorfizem grup iz grupe $(G_1, \circ_1)$ v grupo $(G_2, \circ_2)$ in če je $f$ bijektivna preslikava, potem je preslikava $f^{-1}$ tudi homomorfizem grup iz grupe $(G_2, \circ_2)$ v grupo $(G_1, \circ_1)$.
**Dokaz:** Za poljubna elementa $x, y \in G_2$ velja
$f(f^{-1}(x) \circ_1 f^{-1}(y)) = f(f^{-1}(x)) \circ_2 f(f^{-1}(y)) = x \circ_2 y = f(f^{-1}(x \circ_2 y))$
>
Če upoštevamo, da je $f$ injektivna, odtod sledi $f^{-1}(x) \circ_1 f^{-1}(y) = f^{-1}(x \circ_2 y)$.

>**Cayleyev izrek**
Vsaka grupa je izomorfna kaki podgrupi v kaki grupi permutacij.
>
**Dokaz:** 
Naj bo $(G, *)$ grupa in naj bo $(P(G), \circ)$ grupa vseh permutacij množice $G$. Ideja je, da konstruiramo injektiven homomorfizem grup $\phi$ iz $(G, *)$ v $(P(G), \circ)$. 
>
Potem je $\phi(G)$ podgrupa v $(P(G), \circ)$ in $\phi$ je bijektiven homomorfizem grup iz $(G, *)$ v $(\phi(G), \circ_{\phi(G)})$. 
>
>Torej sta grupi $(G, *)$ in $(\phi(G), \circ_{\phi(G)})$ izomorfni.
>
>Za vsak $g \in G$ lahko definiramo preslikavo $\phi_g: G \to G$, $\phi_g(x) = g * x$. Pokažimo, da je $\phi_g$ permutacija množice $G$. Če je $\phi_g(x) = \phi_g(y)$, potem je $x = g^{-1} * (g * x) = g^{-1} * (g * y) = y$, torej je $\phi_g$ injektivna. Iz $x = g * (g^{-1} * x) = \phi_g(g^{-1} * x)$ sledi, da je $\phi_g$ surjektivna. (Za vsak $x$ obstaja praslika)
>
>Preslikavo $\phi: G \to P(G)$ definirajmo z $\phi(g) := \phi_g$. Pokažimo najprej, da je $\phi$ injektivna. Iz $\phi_g = \phi_h$ sledi $g = \phi_g(e) = \phi_h(e) = h$. Pokažimo še, da je $\phi$ homomorfizem, se pravi, da je $\phi_{g*h} = \phi_g \circ \phi_h$ za vsaka $g, h \in G$. To sledi iz $\phi_{g*h}(x) = (g * h) * x = g * (h * x) = g(\phi_h(x)) = (\phi_g \circ \phi_h)(x)$.
___

**Definicija homomorfizma kolobarjev**
Homomorfizem kolobarjev iz kolobarja $(M_1, +_1, \cdot_1)$ v kolobar $(M_2, +_2, \cdot_2)$ je taka preslikava $f: M_1 \to M_2$, ki zadošča
$f(x+y) = f(x) +_2 f(y)$ in $f(x \cdot_1 y) = f(x) \cdot_2 f(y)$
za vsaka $x, y \in M_1$. 

Bijektivnemu homomorfizmu kolobarjev pravimo izomorfizem kolobarjev.

**Primer homomorfizma kolobarjev, ki ne slika enote v enoto**
Preslikava
$$f: M_n(\mathbb{R}) \to M_{n+k}(\mathbb{R}), \quad f(A) := \begin{bmatrix} A & 0 \\ 0 & 0 \end{bmatrix}$$
je homomorfizem kolobarjev, ki ne slika enote v enoto.

**Primer izomorfizma kolobarjev**
Naj bo $B \in M_n(\mathbb{R})$ obrnljiva matrika. Preslikava
$$f: M_n(\mathbb{R}) \to M_n(\mathbb{R}), \quad f(A) := BAB^{-1}$$
je izomorfizem kolobarjev z enoto.

**Primer**
Preslikava
$$f: \mathbb{C} \to M_2(\mathbb{R}), \quad f(a+bi) := \begin{bmatrix} a & b \\ -b & a \end{bmatrix}$$
je homomorfizem kolobarjev z enoto.

**Primer**
Naj bo $a$ neko realno število. Preslikava
$f_a: \mathbb{R}[x] \to \mathbb{R}$, $f_a(p) := p(a)$
je homomorfizem kolobarjev z enoto. Pravimo ji evalvacija v točki $a$.

**Primer**
Množica $\mathbb{Z} \times \mathbb{Z}$ je kolobar za operaciji $(a, b) + (c, d) := (a+c, b+d)$ in $(a, b) \cdot (c, d) := (ac, bd)$. Preslikava
$f: \mathbb{Z} \times \mathbb{Z} \to \mathbb{Z}$, $f((a, b)) = a$
je homomorfizem kolobarjev z enoto.



**Homomorfizmi obsegov in polj**

**Definicija homomorfizma obsegov**
Homomorfizem obsegov je tak homomorfizem kolobarjev z enoto, ki slika iz obsega v obseg. Enako definiramo homomorfizem polj.

Opomba: Na dolgo povedano je homomorfizem polj iz polja $(K, +_K, \cdot_K)$ v polje $(L, +_L, \cdot_L)$ taka preslikava $f: K \to L$, ki za vsaka $x, y \in K$ zadošča $f(x+y) = f(x)+f(y)$ in $f(x \cdot y) = f(x) \cdot f(y)$ in tudi $f(1_K) = 1_L$.
Opomba: Definicijo homomorfizma polj iz polja $(K, +_K, \cdot_K)$ v polje $(L, +_L, \cdot_L)$ lahko povemo tudi takole: To je taka preslikava iz $K$ v $L$, ki je homomorfizem grup iz $(K, +_K)$ v $(L, +_L)$ in iz $(K \setminus \{0\}, \cdot_K)$ v $(L \setminus \{0\}, \cdot_L)$.

**Primer homomorfizma obsegov**
Preslikava iz realnih števil v kvaternione, ki je definirana z
$$f(a) := \begin{bmatrix} a & 0 \\ 0 & a \end{bmatrix}$$
je homomorfizem obsegov.

**Trditev**
Vsak homomorfizem obsegov je injektiven.

Dokaz: Recimo, da je $f: K \to L$ homomorfizem obsegov in da je $f(a_1) = f(a_2)$ za neka $a_1, a_2 \in K$. Radi bi pokazali, da je $a_1 = a_2$. Označimo $a := a_1 - a_2$. Potem je $f(a) = f(a_1) - f(a_2) = 0_L$. Če $a_1 \neq a_2$, potem je $a \neq 0$, torej obstaja tak $b$ iz $K$, da je $ab = 1_K$. Odtod sledi, da je $0_L = 0_L f(b) = f(a)f(b) = f(ab) = f(1_K) = 1_L$, kar je protislovje. Torej je res $a_1 = a_2$.

Opomba: Bijektivnemu homomorfizmu obsegov pravimo **izomorfizem obsegov**. Inverz izomorfizma obsegov je spet izomorfizem obsegov.

Opomba: Če je $f: K \to L$ homomorfizem obsegov, potem je $f(K)$ podobseg v $L$. Poleg tega je $f$ bijektiven homomorfizem obsegov iz obsega $K$ v obseg $f(K)$. Obsega $K$ in $f(K)$ sta zato izomorfna. Torej lahko smatramo $K$ za podobseg v $L$.
