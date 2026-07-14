> **Def.:**
> Metrika na neki množici $X$ je $d: X \times X \to [0, \infty)$, kjer velja
> 
> $\forall x, x', x'' \in X$:
> 1) Simetrija: 
>    $d(x, x') = d(x', x)$
> 2) Definitnost:  
>    $d(x, x') = 0 \iff x = x'$ 
> 3) Trikotniška neenakost: $d(x, x') + d(x', x'') \ge d(x, x'')$ 

> **Def.:**
> $(X, d_x), (Y, d_y)$ metrična prostora
> 
> $$f \text{ je zv. v }x \in X$$
> $$\Leftrightarrow$$
> $$\forall \varepsilon > 0, \exists \delta > 0 : d_x(x, x') < \delta \Rightarrow d_y(f(x), f(x')) < \varepsilon$$
> 
> $f: X \to Y$ je zvezna, če je zvezna v vsaki točki $X$

**Primeri metrik:**
*   diskretna metrika $d(x, x') = \begin{cases} 0; & x = x' \\ 1; & x \neq x' \end{cases}$
*   $V$ vekt. prostor, $\|\cdot\|$ norma na $V$:
    $d_{\|\cdot\|}(\vec{x}, \vec{y}) :=\|\vec{x} - \vec{y}\|$
*   Hammingova metrika, kjer $u = (u_1, \dots, u_n)$ in $v = (v_1, \dots, v_n)$:
    $d_{Ham}(u, v) = \# \text{indeksov, kjer } u_i \neq v_i$



> **Def.:** Naj bo  $(X, d)$ metrični prostor, odprta krogla $K(x,r)$ je definirana kot 
> 
> $$K(x, r) := \{ x' \in X \mid d(x, x') < r \}$$
> $$x \in X, r > 0$$
> 
> Naj bo $A \subseteq X$ polj. podmnožica $X$.
> 
> $$x \text{ je notranja točka }A \Leftrightarrow \exists r > 0 : K(x, r) \subseteq A$$
> 
> $$x \text{ je mejna točka }A$$ $$ \Leftrightarrow$$ $$ \forall  r > 0 : K(x, r) \cap A \neq \emptyset \land K(x,r) \cap (X\backslash A) \neq \emptyset $$


> **Def.:** $A \subseteq X$ je odprta, če so vse točke $A$ notranje

>**Def.:** V splošni topologiji je točka v množici $A$ notranja natanko tedaj ko obstaja odprta podmnožica $A$ ki jo vsebuje.
>V splošni topologiji je točka v množici $A$ robna če za vsako odprto množico, ki jo vsebuje velja da vsebuje tudi elemente komplementa $A$.
 
> Unija družine odprtih množic v $X$ je odprta množica.
> 
> Presek **končne** družine odprtih množic ni nujno odprta množica.
> >[!|dokaz]+ Dokaz:
> >Če imamo odprto množico obtaja odprta okolica okoli vsake točke, če imamo unijo iste odprte okolice še vedno obstajajo torej je unija odprta množica
> >
> >Če imamo dve odprti množici in element v preseku vemo da obstaja odprta okolica za prvo in za drugo množico, vzamemo manjšo.



> **Trditev:** Naj bosta $(X, d_x), (Y, d_y)$ metrična prostora
> 
> $$\text{$f: X \to Y$ je zvezna}$$ 
> $$\Leftrightarrow$$
> $$\text{$\forall$ odp. mn. $V \subseteq Y$ je $f^{-1}(V)$ odprta v $X$}$$
> 
> *Praslika vsake odprte množice je odprta.*
> 
> >[!|dokaz]+ Dokaz:
> > $(\Rightarrow)$
> > 
> > $$y \in V, f(x) = y$$
> > 
> > $$\exists \varepsilon > 0: K(y, \varepsilon) \subseteq V$$
> > 
> > $$\Rightarrow \exists  \delta : d(x,x') < \delta \Rightarrow d(f(x),f(x')) < \varepsilon$$
> > 
> > za $K(x,\delta)$ velja
> > 
> > $$x' \in K(x,\delta) \Rightarrow f(x') \in K(y,\varepsilon)$$
> > 
> > torej je
> > 
> > $$f(K(x,\delta)) \subset  f(K(y,\varepsilon)) \subset V$$
> > 
> > $$f(K(x,\delta)) \subset V$$
> > 
> > $$K(x,\delta) \subset f^{-1}(V)$$
> > 
> > 
> > $\Rightarrow x$ je notranja točka $f^{-1}(V)$
> > 
> > $(\Leftarrow)$
> > 
> > $$V := K(f(x), \varepsilon)$$
> > 
> > $f^{-1}(V)$ je odprta v $X$ in vsebuje $x$
> > 
> > $\Rightarrow \exists \delta > 0 : K(x, \delta) \subseteq f^{-1}(V)$


> **Def.:**
> Naj bo $X$ neka množica.
> **Topologija** na $X$ je družina podmnožic $\mathcal{T} \subseteq 2^X$, za katero veljata pogoja:
> 
> (T1) Polj. unija elementov $\mathcal{T}$ je element $\mathcal{T}$
> 
> (T2) Končni preseki elementov $\mathcal{T}$ so elementi $\mathcal{T}$



Elemente $\mathcal{T}$ imenujemo **odprte množice**.

$(X, \mathcal{T})$ je **topološki prostor**.

Iz (T1) sledi da  je prazna množica vedno v topologiji $\emptyset \in \mathcal{T}$ (Prazna unija)

Iz (T2) sledi da  je celotna množica vedno v topologiji $X \in \mathcal{T}$ (Prazen presek)


**Primeri**

- $\mathcal{T}_{triv}=\{\emptyset, X\}$ je min. top. na $X$ 
  je trivialna topologija na $X$

- $\mathcal{T}_{diskr} = 2^X$ je max. top. na $X$
  je diskretna topologija na $X$

- $\mathcal{T}_{kk} = \{\emptyset\} \cup \{ A \subseteq X \mid X \setminus A \text{ je končna} \}$
  je  topologija končnih komplementov

	Če je $X$ končna $\Rightarrow \mathcal{T}_{kk} = 2^X = \mathcal{T}_{diskr.}$
	
	$X$ neskončna:
	$\mathcal{T}_1$: $(A \cap B)^{C} = A^{C} \cup B^{C}$. $A^C$ in $B^{C}$ sta končna $\Rightarrow A^{C} \cup B^{C}$ je končno torej je komplement preseka $A$, $B$ končen.
	$\mathcal{T}_2$: $(A \cup B)^{C} = A^{C} \cap B^{C}$. $A^C$ in $B^{C}$ sta končna $\Rightarrow A^{C} \cap B^{C}$ je končen torej je komplement preseka $A$, $B$ končen.

*   $(X, d)$ metrični prostor
$\mathcal{T}_d := \{ \text{odprte množice v } X \text{ glede na metriko } d \}$
je topologija na $X$ porojena z metriko $d$ kjer so odprte množice vse množice $U$ za katere velja $\forall u \in U,\exists \varepsilon > 0 : K(u,\varepsilon) \subset U$


> **Def.:** $(X, J)$ je metrizabilen, če obstaja metrika $d$ na $X$ tako da je $\mathcal{T} = \mathcal{T}_d$

$\mathcal{T}_{diskr}$ je porojena z diskretno metriko.

$\mathcal{T}_{kk}$ ni metrizabilna (če je $X$ neskončen).

V metrični topologiji velja:
- $x \neq x' \Leftrightarrow d(x, x') > 0$
- $K(x, \frac{d(x, x')}{2}), K(x', \frac{d(x, x')}{2})$ disjunktni odp. množici
- V $\mathcal{T}_{kk}$ je presek (nepraznih) odprtih množic neprazen

> **Def.:** V $(X, \mathcal{T})$ je $A \subseteq X$ zaprta, če je $X \setminus A \in \mathcal{T}$

> **Trditev:** Družina zaprtih množic vsebuje vse **poljubne preseke** *tudi neskončne* in vse **končne unije** svojih elementov.

> Če je $\mathcal{Z} \supseteq \{\emptyset, X\}$ družina podmnožic $X$, ki vsebuje poljubne preseke in končne unije svojih elementov, je $\mathcal{T} := \{ U \subseteq X \mid X \setminus U \in \mathcal{Z} \}$ topologija. *Topologija komplementov zaprtih množic. Dokažemo lahko z demorganovimi pravili.*

Primer:
Naj bo $\mathcal{Z} =$ končne podmnožice $X$. Velja da vse množice v $\mathcal{Z}$ vsebujejo poljubne preseke in končne unije. Torej po izreku ugotovimo da komplementi $\mathcal{Z}$ tvorijo topologijo, kar pa lahko potrdimo z dokazom od prej.

> **Definicije**
> 
> Naj bo $A \subseteq X$ v topološkem prostoru $(X, \mathcal{T})$.
> 
> *   **Notranjost $A$** ($\text{Int } A$ ali $\mathring{A}$):
>     *   Največja odprta podmnožica $A$.
>     *   Unija vseh odprtih podmnožic $A$.
> *   **Zaprtje $A$** ($\text{Cl } A$ ali $\overline{A}$):
>     *   Najmanjša zaprta nadmnožica $A$.
>     *   Presek vseh zaprtih nadmnožic $A$.
> *   **Meja $A$** ($\text{Fr } A$ ali $\dot{A}$):
>     *   Definicija: $\text{Cl } A \setminus \text{Int } A = \overline{A} \setminus \mathring{A}$.
> *   **Rob $A$** ($\text{Bd } A$ ali $\partial A$): enako kot meja $A$.
>     

**Posebni primeri:**
*   $\mathring{X} = X$
*   $\overline{X} = X$
*   $\text{Fr } X = \emptyset$

**Oznake**

*   $\text{Int } A = \mathring{A}$
*   $\text{Cl } A = \overline{A}$
*   $\text{Fr } A = \dot{A}$
*   $\text{Bd } A = \partial A$

> **Lastnost inkluzije (monotonost):**
> Če velja $A \subseteq B$, potem velja:
> *   $\mathring{A} \subseteq \mathring{B}$
> *   $\overline{A} \subseteq \overline{B}$
>   >[!|dokaz]+ Dokaz:
>   >Notranja točka $A$ je vsebovana v odprti množici $U$ v $A$, ta $U$ je tudi v $B$ torej je v notranjosti $B$-ja torej je $\mathring{A} \subseteq \mathring{B}$
>   >
>   >Zaprtje $B$ vsebuje $A$. Ker je zaprtje $A$ presek vseh množic ki vsebujejo $A$, kar vključuje zaprtje $B$ mora biti po definiciji preseka $\overline{A} \subseteq \overline{B}$.

> Naj bosta $A, B \subseteq X$:
> 
> 1.  **Unija in zaprtje:** $\overline{A \cup B} = \overline{A} \cup \overline{B}$
>   >[!|dokaz]+ Dokaz:
>  > Ker je $A,B \subseteq A \cup B$ je po prejšnjem izreku $\overline{A}, \overline{B} \subseteq \overline{A \cup B} \Rightarrow \overline{A} \cup \overline{B}\subseteq \overline{A \cup B}$
>  > 
> > Ker je $\overline{A \cup B}$ najmanjša zaprta množica ki vsebuje $A \cup B$, in je $\overline{A} \cup  \overline{B}$ zaprta množica ki vsebuje $A \cup B$ velja da je $\overline{A\cup B} \subseteq \overline{A} \cup \overline{B}$
> 1.  **Presek in zaprtje:** $\overline{A \cap B} \subseteq \overline{A} \cap \overline{B}$ *npr. presek $(0,1)$ in $(1,2)$ je $\emptyset$ ampak presek zaprtij bi bil $\{ 1\}$, torej $\emptyset \subseteq \{ 1\}$*
> 2.  **Unija in notranjost:** $\mathring{A \cup B} \supseteq \mathring{A} \cup \mathring{B}$ *npr. unija $[0,1]$ in $[1,2]$, kjer je notranjost unije $(0,2)$ unija notranjosti pa $(0,1)\cup(1,2)$.*
> 3.  **Presek in notranjost:** $\mathring{A \cap B} = \mathring{A} \cap \mathring{B}$
> >[!|dokaz]+ Dokaz:
> > Ker je $\mathring{A \cap B}$ največja odprta množica v $A \cap B$ in je $\mathring{A} \cap \mathring{B}$ odprta množica v $A \cap B$ je $\mathring{A} \cap \mathring{B}\subseteq \mathring{A \cap B}$
> > Ker je $A\cap B \subseteq A, B$ velja da je $\mathring{A \cap B}\subseteq \mathring{A}, \mathring{B}$, torej je $\mathring{A \cap B} \subseteq \mathring{A} \cap \mathring{B}$
> > Torej je $\mathring{A \cap B} = \mathring{A} \cap \mathring{B}$

Naj bo $(X, \mathcal{T})$ topologija in $A \subseteq X$. Na $A$ lahko konsturiramo topologijo $\mathcal{T}_{A}$.

$\mathcal{T}_A := \{ U \cap A \mid U \in \mathcal{T} \}$


$$\bigcup_{\lambda} (U_{\lambda} \cap A) = (\bigcup_{\lambda} U_{\lambda}) \cap A$$
$$\bigcap_{i=1}^{n} (U_i \cap A) = (\bigcap_{i=1}^{n} U_i) \cap A$$

> **Trditev:**
> Naj bo $(X, \mathcal{T})$ topologija in $A \subseteq X$.
> Množica $V$ je zaprta v $(A, \mathcal{T}_A)$ natanko tedaj ko je $V$ enak preseku $A$ z zaprto množico v $X$.
> 
> >[!|dokaz]+ Dokaz:
> >
> > 
> > ( $\Leftarrow$ )
> > $Z$ zaprta v $(X, \mathcal{T}), V = Z \cap A \Rightarrow$
> > $X \setminus Z \in \mathcal{T} \Rightarrow$
> > $(X \setminus Z) \cap A \in \mathcal{T}_A \Rightarrow$
> > $A \setminus (Z \cap A) \in \mathcal{T}_A \Rightarrow$
> > $Z \cap A$ zaprta v $(A, \mathcal{T}_{A)}\Rightarrow$
> > $V$ je zaprta
> > 
> > $(\Rightarrow)$
> > $Z^{\text{zap}} \subseteq A \Rightarrow$
> > $A \setminus Z \in \mathcal{T}_A \Rightarrow$
> > $A \setminus Z = A \cap U, U \in \mathcal{T} \Rightarrow$
> > $Z = A \cap (X \setminus U)$, $X \setminus U$ je zaprta ker je $U$ odprta
> > $\Rightarrow$ $Z$ je presek $A$ in zaprte množice


Naj bo $A \subseteq X$ podprostor in naj bo $V^{\text{odp}} \subseteq A$, ni nujno, da je $V$ odp. v $X$.

> Trditev
> $A^{\text{odp}} \subseteq X$
> $B^{\text{odp}} \subseteq A \Rightarrow B^{\text{odp}} \subseteq X$
>  Dokaz: *$A$ naj bo odprta v $X$, $B = U \cap A$ naj bo odprta v $A$, torej je $U$ odprta v $X$. Potem je $U \cap A$ odprta v $X$ oz. $B$ je odprta v $X$.*
> 
> $A^{\text{zap}} \subseteq X$
> $B^{\text{zap}} \subseteq A \Rightarrow B^{\text{zap}} \subseteq X$
> Dokaz: *$A$ naj bo zaprta v $X$, $B = U \cap A$ naj bo zaprta v $A$, torej je $U$ zaprta v $X$. Potem je $U \cap A$ zaprta v $X$ oz. $B$ je zaprta v $X$.*


> **Def.:** Naj bosta $(X, \mathcal{T}_x), (Y, \mathcal{T}_y)$ top. prostora.
> $f: X \to Y$ je zvezna, če $V \in \mathcal{T}_y \Rightarrow f^{-1}(V) \in \mathcal{T}_x$
> *Praslika odprte množice je odprta.*

> **Trditev:** Kompozitum zveznih funkcij je zvezna funkcija
> 
> >[!|dokaz]+ Dokaz:
> >
> > $$(X, \mathcal{T}_x) \xrightarrow{f} (Y, \mathcal{T}_y) \xrightarrow{g} (Z, \mathcal{T}_z)$$
> > $$(g \circ f)^{-1}(W) = f^{-1}(g^{-1}(W))$$
> > $$W \in \mathcal{T}_z \Rightarrow g^{-1}(W) \in \mathcal{T}_y \Rightarrow f^{-1}(g^{-1}(W)) \in \mathcal{T}_x$$

Primeri:
- vse zvezne funkcije na metričnih prostorih so zvezne
  *Dokaz: Če je $f$ zvezna v metr. prostoru obstaja $\delta$ okolica $f(x)$ tako da se vsak element v $\varepsilon$ okolici $x$ preslika vanj. Torej je praslika $\delta$ okolice odprta množica.*
  
  
- $f: (X, \mathcal{T}_{\text{diskr}}) \to (Y, \text{polj. topologija})$ je zvezna
  *Dokaz: Praslika neke odprte množice iz polj. topologije $Y$ bo vedno v diskretni topologiji oz. bo vedno odprta množica.*
  
- $g: (X, \text{katerakoli}) \to (Y, \mathcal{T}_{\text{triv}})$ je zvezna
  *Dokaz: Praslika prazne množice je prazna množica, praslika $Y$ pa je $X$.*
  
- $\text{Id}: (X, \mathcal{T}) \to (X, \mathcal{T}') \text{ je zv. } \iff \mathcal{T}' \subseteq \mathcal{T}$
  *Dokaz: Naj bo $x \in U$ in $U \in \mathcal{T}'$. Ker je $\text{Id}$ zvezna velja da je praslika $f(U) = U$ odprta. Torej $U \in \mathcal{T'} \Rightarrow U \in \mathcal{T}$ oz. $\mathcal{T'} \subseteq \mathcal{T}$.*
  *Če je $\mathcal{T'} \subseteq \mathcal{T}$, vemo da je praslika $U \in \mathcal{T'}$ enaka $U$. Ker je $U$ odprta v $\mathcal{T'}$ je odprta v $\mathcal{T}.$*
  
- $f: (\mathbb{R}, \mathcal{T}_{kk}) \rightarrow (\mathbb{R}, \mathcal{T}_{\text{evkl}}) \text{ zvezna } \iff f \text{ je konst.}$
  *Dokaz: ($\Leftarrow$) Naj bo $f(x) = c$, $V \in \mathcal{T}_\text{evkl}$, če je $c \in  V$, potem je $f^{-1}(V) = \mathbb{R}$, če $c \notin V$ potem je $f^{-1}(V) = \emptyset$, kar sta odprti množici.*
  *$(\Rightarrow)$ Ker $f$ ni konstantna obstajata vsaj dve točki da $f(x_{1}) \neq f(x_{2})$. V evklidski topologiji vzamemo disjunktni odprti krogli od $f(x_{1}), f(x_{2})$. Ker velja da je $f^{-1}(K_{1} \cap K_{2}) = f^{-1}(K_{1}) \cap f^{-1}(K_{2})$ mora biti presek praslik prazna množica. V topologiji končnih komplementov pa ne obstajata disjunktni množici torej mora biti $f$ konstantna.*
  
  *$f^{-1}(K_{1} \cap K_{2}) = f^{-1}(K_{1}) \cap f^{-1}(K_{2})$ - predpostavimo da je $x$ v prasliki $K_{1}$ in prasliki $K_{2}$, to pomeni da je $f(x)$ v $K_{1}$ in $K_{2}$ hkrati, torej je $x$ v $f^{-1}(K_{1} \cap K_{2})$*
  
  *V $(X,\mathcal{T}_{kk})$, kjer je $X$ neskončna množica (kar $\mathbb{R}$ je) so vse odprte množice prekrivajoče. Vzamemo polj. končno podmnožico neskončne množice $X$, edini način da je njen komplement disjunkten z neko drugo množico je če bi bil njen komplement končen - to po definiciji ne more biti odprta mn. v tej topologiji.*
  
- $(X, \mathcal{T}_x) \xrightarrow{\text{konst.}} (Y, \mathcal{T}_y) \text{ je zv.}$
  *Za poljubno odprto množico v $\mathcal{T}_{y}$ bo njena praslika*
  *$$\text{konst}_{y_0}^{-1}(V) = \begin{cases} X, & y_0 \in V \\ \emptyset, & y_0 \notin V \end{cases}$$*
- za vsak metrični prostor $(X,d)$ in inducirano topologijo $(X, \mathcal{T}_{d})$ je vsaka funkcija oblike $f(x) := d(x, x_0)$, $x_{0} \in X$ zvezna funkcija
  *Dokaz:  Vemo da velja $|d(x,x_{0})-d(x',x_{0})| \leq d(x,x')$, in imamo neko $\varepsilon$ okolico $f(x)$, kjer za vsak $x' \in X$ velja $|d(x,x_{0})-d(x',x_{0})| < \varepsilon$. Za $\delta$ lahko vzamemo $\varepsilon$ in vidimo da velja $d(x,x') \leq \varepsilon \Rightarrow |d(x,x_{0})-d(x',x_{0})| \leq d(x,x') \leq \varepsilon$*
  

- $i: (A, \mathcal{T}_A) \hookrightarrow (X, \mathcal{T})$
  $i^{-1}(U) = A \cap U \in \mathcal{T}_A$
- *Po definiciji - $U$ je odprta, $A \cap U$ je odprta v $A$.*

> Trditev:
> Naj bo $f: X \to Y$. Naslednje trditve so ekvivalentne.
> 
> (1) $f$ je zvezna
> (2) $f$ praslika vsake zaprte mn. je zaprta
> (3) $\forall A \subseteq X$ velja $f(\overline{A}) \subseteq \overline{f(A)}$ *Slika zaprtja je podmn. zaprtja slike.*
> 
> > [!|dokaz]+ Dokaz:
> >
> > (1) $\Leftrightarrow$ (2)
> > ($\Rightarrow$) $F^{\text{zap}} \subseteq Y \Rightarrow f^{-1}(F) = f^{-1}(Y \setminus U) = X \setminus \underbrace{f^{-1}(U)}_{\text{odp}} = \text{zap.}$
> > 
> > ($\Leftarrow$)
> > Praslika komplementa je komplement praslike. Torej je praslika komplementa zaprte mn., komplement praslike zaprte množice, kar je odprta mn.
> > 
> > (2) $\iff$ (3)
> > $A \subseteq X , f^{-1}(f(A)) \supseteq A \quad$ *velja enakost če je $f$ inj.*
> > $B \subseteq Y \quad f(f^{-1}(B)) \subseteq B \quad$ *velja enakost če je $f$ sur.*
> > 
> > (2) $\Rightarrow$ (3)
> > Vemo da je $f(A) \subseteq \overline{f(A)}$ $\Rightarrow$
> > $\Rightarrow f^{-1}(\overline{f(A)}) \supseteq f^{-1}(f(A)) \supseteq A \supseteq \overline{A}$
> > uporabimo $f$ na obeh straneh $\Rightarrow \overline{f(A)} \supseteq f(\overline{A})$
> > 
> > (3) $\Rightarrow$ (2)
> > $B^{\text{zap}} \subseteq Y \Rightarrow B = \overline{B}$
> > $\Rightarrow f(\overline{f^{-1}(B)}) \subseteq \overline{f(f^{-1}(B))} \subseteq \overline{B} = B$
> > $\Rightarrow \overline{f^{-1}(B)} \subseteq f^{-1}(B)$
> > hkrati vedno velja $\overline{f^{-1}(B)} \supseteq f^{-1}(B)$
> > $\Rightarrow \overline{f^{-1}(B)} = f^{-1}(B)$
> > $\Rightarrow  f^{-1}(B)$ je zap.

***

Naj bosta $(X, \mathcal{T}_x), (Y, \mathcal{T}_y)$ topologiji.

$[1]$ $f: X \to Y$ zvezna če $f^{-1}(\mathcal{T}_y) \subseteq \mathcal{T}_x$

Ekvivalence od nam povejo da je $f$ zvezna tudi
$\iff$ $f$ praslika vsake zaprte je zaprta
$\iff$ za vsak $A \subseteq X$ v domeni je $f(\overline{A}) \subseteq \overline{f(A)}$ $[2]$


$$f(\overline{A}) \subseteq \overline{f(A)} \implies f(\lim_{n \to \infty} a_n) = \lim_{n \to \infty} f(a_n)$$

Karakterizacija $[1]$ je računsko slaba df. (rač. inverzov je težka), $[2]$ je načeloma bolj uporabna.

***

Naj bo $(X, \mathcal{T}_x), (Y, \mathcal{T}_y)$ kot smo lahko knsturirali topologijo za podmnožico $X$ lahko konstruriramo topologijo na $X \times Y$.

Če pogledamo 

$$ \quad \{ U \times V \mid U \in \mathcal{T}_x, V \in \mathcal{T}_y \} \quad [3]$$

in preverimo če je topologija vidimo

*   preseki so škatle
*   unije niso škatle

Torej $[3]$ ne more biti topol.

Vzamemo $$\mathcal{T}_{X \times Y} := \{ \text{polj. unije produktov odprt. mn.} \}$$

unija teh el. je vsebovana v $\mathcal{T}_{X \times Y}$


Unija prod. odp. mn. je polj. unija prod. odp. mn., torej je v topologiji.

Za preseke velja

$$(\bigcup_{\lambda} U_{\lambda} \times V_{\lambda}) \cap (\bigcup_{\mu} U_{\mu} \times V_{\mu}) = \bigcup_{\lambda, \mu} (U_{\lambda} \times V_{\lambda}) \cap (U_{\mu} \times V_{\mu})$$
$$= \bigcup_{\lambda, \mu} (U_{\lambda} \cap U_{\mu}) \times (V_{\lambda} \cap V_{\mu})$$


$\Rightarrow$ torej so preseki v $\mathcal{T}_{X \times Y}$

Torej je $\mathcal{T}_{X \times Y}$ topologija na $X \times Y$.
Pravimo ji **produktna topologija**.

Primer:
$(\mathbb{R}, \mathcal{T}_{\text{evkl}}) \times (\mathbb{R}, \mathcal{T}_{\text{evkl}})$ $\implies$ odprta škatla

Če imamo metrična prostora $(X, d_x), (Y, d_y)$ na njunem prod. lahko definiramo meriko $d_{X \times Y}$

$$d_{X \times Y}((x_{1},y_{1}),(x_{2},y_{2})) := \max(d_{x}(x_{1},x_{2}), d_{y}(y_{1},y_{2}))$$

Odprta krogla $K((x,y), \varepsilon)$ je definirana kot

$$K((x, y), \epsilon) = \{ (x', y') \in X \times Y \mid d_{X \times Y}((x, y), (x', y')) < \epsilon \}$$
$$\Downarrow$$
$${\color{green}K((x, y), \epsilon) = \{ (x', y') \in X \times Y \mid \max \{ d_x(x, x'), d_y(y, y') \} < \epsilon \}}$$
$$\Downarrow$$

Iz tega lahko vidimo da je $K((x,y), \varepsilon)$ kartezični produkt

$$K((x, y), \epsilon) = \{ (x', y') \in X \times Y \mid d_x(x, x') < \epsilon \text{ in } d_y(y, y') < \epsilon \}$$

$$\Downarrow$$

$$K((x, y), \varepsilon)= K(x, \varepsilon) \times K(y, \varepsilon) $$

<br>

Preverimo lahko da je to ista topologija kot evklidska to. na $\mathbb{R}^{2}$. Da dokažemo njuno ekvivalentnost mora prva vsebovati drugo in druga prvo oz. $\mathcal{T}_{1} \subseteq \mathcal{T}_{2}$ om $\mathcal{T}_{2} \subseteq \mathcal{T}_{1}$.

Ekvivalentno velja da za vsako točko $x \in X$ in za vsako odprto množico $U \in \mathcal{T_{1}}$ ki vsebuje $x$, obstaja odprta množic $V \in \mathcal{T_{2}}$ tako da velja $x \in V \subseteq U$.


$U \subseteq \mathbb{R}^2$ odprta mn., torej je  vsaka točka notranja,
$\forall x \in U,  \exists r_x : K(x, r_x) \subseteq U \Rightarrow U = \bigcup_{x \in U} K(x, r_x)$

Torej lahko v vsaki krogli vzamemo za diagonalo premer in za kroglo v škatli pa polovico stranice.

Torej sta $(\mathbb{R}^2, \mathcal{T}_{\text{evkl}})$ in $(\mathbb{R}, \mathcal{T}_{\text{evkl}}) \times (\mathbb{R}, \mathcal{T}_{\text{evkl}})$ enaki.

***

Imamo $X, Y$ in $X \times Y$. Definiramo

$$\text{pr}_{x} : X \times Y \rightarrow X$$
$$\text{pr}_{x}(x,y) = x$$
$$ $$
$$\text{pr}_{y} : X \times Y \rightarrow Y$$
$$\text{pr}_{y}(x,y) = y$$

$$ $$

$$Z \rightarrow X \times Y$$
$$f = (f_{1}(z), f_{2}(z))$$
$$f_{1}:Z \rightarrow X$$
$$f_{2}: Z \rightarrow Y$$

> **Trditev:** Velja da sta  $\text{pr}_{x}, \text{pr}_{y} : X \times Y \to X, Y$ zv.
> >[!|dokaz]+ Dokaz:
> >
> > Vzamemo $U \in \mathcal{T}_x$.
> > $\text{pr}_{x}^{-1}(U) = U \times Y$ Praslika odprte množice je odprta. Torej je $\text{pr}_{x}$ zvezna.


> **Trditev:** Naj bodo $(X, \mathcal{T}_x), (Y, \mathcal{T}_y), (Z, \mathcal{T}_z)$ top. prostori. 
> 
> Velja da je $f : Z \to X \times Y$ zvezna $\iff$ komponenti $f_1, f_2$ sta zv.
> 
> >[!|dokaz]+ Dokaz:
> >
> > Naj bo $f := (f_1, f_2) : Z \to X \times Y$
> > 
> > $(\Rightarrow)$
> > Naj bo $f$ zvezna. Lahko definiramo $f_{1}$ in $f_{2}$ kot
> > $f_1 = pr_x \circ f$
> > $f_2 = pr_y \circ f$
> > $\Rightarrow$ kompozitum zveznih funkcij je zvezen, torej sta $f_{1},f_{2}$ zvezni
> > 
> > $(\Leftarrow)$
> > Pogledamo $f^{-1}(U \times V)$
> > $$f^{-1}(U \times V) = \{ z \mid f(z) \in U \times V \}$$
> > $$= \{ z \mid f_1(z) \in U, f_2(z) \in V \}$$
> > $$= \{ z \mid z \in f_1^{-1}(U), z \in f_2^{-1}(V) \}$$
> > $$= f_1^{-1}(U) \cap f_2^{-1}(V)$$
> >kar je odprta množica.
> >Poglejmo še poljubno unijo produktov odprtih podmnožic.
> > 
> > $$f^{-1}(\bigcup_{\lambda} U_{\lambda} \times V_{\lambda}) = \bigcup_{\lambda} f^{-1}(U_{\lambda} \times V_{\lambda})$$
> > $$= \bigcup_{\lambda} (f_1^{-1}(U_{\lambda}) \cap f_2^{-1}(V_{\lambda})) \in \mathcal{T}_z$$


### **Homeomorfizmi**

Naj bosta $(X, \mathcal{T}_x), (Y, \mathcal{T}_y)$ množici in pripadajoči topologiji.

Naj bo $f : X \to Y$ bijekcija med $X, Y$ in $\mathcal{T}_x, \mathcal{T}_y$

Naj bo funkcija $f: X \to Y$ bijekcija, ki inducira **bijekcijo med $\mathcal{T}_x$ in $\mathcal{T}_y$**

To je **topološka ekvivalenca**, $f$ pa je **homeomorfizem**.

$$X \approx Y$$

*Funkcija $f: X \rightarrow Y$ inducira funkcijo iz $\hat{f}: P(X) \rightarrow P(Y)$ tako da velja $f(U) = \{ f(x) \,;\; x \in U\}$. Inducirana funkcija bijeckije je bijekcija med $P(X)$ in $P(Y)$ ampak, ni nujno bijekcija med vsemi odprtimi podmn. $X$ in vsemi odprtimi podmn. $Y$. Za topološko ekvivalenco rabimo da je inducirana funkcija, **omejena na odprte množice, tudi bijekcija**. To funkcijo lahko zapišemo kot $\hat{f} |_{\mathcal{T}_X} : \mathcal{T}_X \to \mathcal{T}_Y$*

*Ker vemo da je inducirana funkcija bijekcije **že** bijekcija, moramo samo preveriti še da se vsaka odprta mn. slika v odprto mn. s čimer potrdimo da je bijekcija ohranjena med odprtimi podmn. $X$ in odprtimi podmn. $Y$ oz. $\mathcal{T}_{X}$ in $\mathcal{T}_{Y}.$*

*Če vemo da je $f$ bijekcija bo za to da je $f: \mathcal{T}_{X} \rightarrow \mathcal{T}_{Y}$ tudi bijekcija dovolj da preverimo samo pogoj *

$$f(U) \text{ je odprta} \Leftrightarrow U \text{ je odprta}$$ 

*oz. ekvivalentno* 

$$f(U) \in \mathcal{T}_{Y} \Leftrightarrow U \in \mathcal{T}_{X}$$


> **Trditev:**
> Naj bosta $(X, \mathcal{T}_X)$ in $(Y, \mathcal{T}_Y)$ topološka prostora.
> 
> $f: X \to Y$ je homeomorfizem $\Leftrightarrow$ $f$ je bijekcija, $f$ in $f^{-1}$ zvezni preslikavi.
> 
> >[!|dokaz]+ Dokaz:
> >
> > 
> > $(\Rightarrow)$
> > 
> > Naj bo $f$ homeomorfizem. Po definiciji homeomorfizma je $f$ bijektivna.
> >
> >
> >Ker je $f$ homeomorfizem, mora za vsako odprto množico $V \in \mathcal{T}_Y$ veljati, da je njena praslika $f^{-1}(V)$ odprta v $X$. To je natanko definicija **zveznosti preslikave $f$**.
> >
> >Ker je $f$ homeomorfizem, mora tudi slika vsake odprte množice $U \in \mathcal{T}_X$ biti odprta v $Y$. Ker je $f$ bijekcija, je $f(U) = (f^{-1})^{-1}(U)$. Pogoj, da je praslika množice $U$ s preslikavo $f^{-1}$ odprta, je natanko definicija **zveznosti preslikave $f^{-1}$**.
> > 
> > $(\Leftarrow)$
> > Privzemimo, da je $f$ bijekcija ter sta $f$ in $f^{-1}$ zvezni.
> > Ker je $f$ zvezna, velja: $V \in \mathcal{T}_Y \implies f^{-1}(V) \in \mathcal{T}_X$.
> >  Ker je $f^{-1}$ zvezna, velja: $U \in \mathcal{T}_X \implies (f^{-1})^{-1}(U) \in \mathcal{T}_Y$. Ker je $f$ bijekcija, je $(f^{-1})^{-1}(U) = f(U)$, torej: $U \in \mathcal{T}_X \implies f(U) \in \mathcal{T}_Y$.
> >  To nam da:
> > $$U \in \mathcal{T}_X \iff f(U) \in \mathcal{T}_Y$$
> > To pomeni, da preslikava $f$, ki je že bijketivna med $P(X)$ in $P(Y)$, vzpostavi bijekcijo med odprtimi množicami prostora $X$ in odprtimi množicami prostora $Y$ *zato ker je $f$ že bijekcija in se vsaka odprta mn. slika v odprto in obratno*.


Primeri:
-   zaprti intervali so homeomorfni : $[0, 1] \approx [a, b]$
-   odprti intervali so homeomorfni : $(0, 1) \approx (a, b)$
-   polodprti intervali so homeomorfni : $[0, 1) \approx [a, b)$

*Za vsako lahko uporabimo $f(t) = a +(b-a)t$.*

***

**Topološke lastnosti**

Če se neka lasnost ohranja pri homeomorfizmu ji pravimo **topološka lastnost.**

**Kompaktnost**

> **Dfn.:**
> Naj bo $(X, \mathcal{T})$ topologija na $X$.
> 
> **Odprto pokritje** $A$ je podmnožice $\mathcal{T}$ tako da velja
> $$A \subseteq \bigcup_{U \in \mathcal{T}}U$$
> 
> **Podpokritje** nekega pokritja je poddružina, ki je prav tako pokritje.

> **Dfn.:**
> $A \subseteq  X$ je kompaktna če za vsako odprto pokritje $A$ obstaja končno podpokritje.

**Primeri:**

*   Vse končne množice so kompaktne
    *   *Dokaz:* Za vsako točko izberemo množico, ki jo vsebuje, torej je končno pokritje.
*   Naj bo $a_n$ konv. zap. Množica $a_n$ je kompaktna
    *   *Dokaz:* Vzamemo okolico limite, ostane nam končno št. el.
*   $\mathbb{R}$ ni kompaktna



> **Trditev:** Če je $X$ metričen prostor, je vsaka kompaktna mn. $A \subseteq X$ omejena.
> 
> **Dokaz:**
> Naj bo $x_{0} \in X$. $X$ lahko pokrijemo z unijo
> $$X = \bigcup_{n \in \mathbb{N}} K(x_{0},n)$$
> 
> Ker je $A \subseteq X$ velja da je zgornje pokritje hkrati pokritje $A$. Ker je $A$ kompaktna mora obstajati končno pokritje $A$ oz. končno število odprtih krogel. Ker vsaka večja krogla vsebuje vse manjše mora veljati da
> $$\Rightarrow \exists N : A \subseteq K(x_0, N)$$
> 
> Ker je $A$ vsebovana v neki odprti krogli mora biti omejena.


Kompaktnost je **topološka lastnost.**

> **Primer:**
> Kompaktnost se ohranja pri homeo.
> 
> $$(a,b) \approx \mathbb{R} \text{ ; } \mathbb{R} \text{ je nekomp.} \Rightarrow (a,b) \text{ je nekomp.}$$

Vidimo, da omejenost ni topološka lastnost.

**Brez dokaza:** Če obstaja odprto pokritje v metričnem prost. potem obstaja odprto pokritje s kroglami.

> **Trditev:** $[a,b] \subseteq \mathbb{R}$ je kompakten
> 
> >[!|dokaz]+ Dokaz:
> > 
> > Za vsako pokritje moramo pokazati da obstaja končno podpokritje.
> > 
> > Polj. pokritje lahko zgradimo tako da vzamemo kroglo, ki pokrije $a$, in dodamo kroglo za vsako točko na robu do sedaj zgrajenega pokritja. *Lahko izberemo tako pokritje od $a$ do neke točke $x$ na $[a,b]$ da robna točka pokritja konvergira k $c$.*
> > 
> > Naj bo
> > 
> > $$S = \{ x \in [a,b] \,;\; [a,x] \text{ ima končno pokritje}\}$$
> > 
> > 
> > Naj bo
> > 
> > $$c := \sup \{ x \in [a,b] ; [a,x] \text{ ima končno podpokritje} \}$$
> > 
> > Ker je $c \in [a,b]$ mora biti vsebovana v neki odprti množici polj. pokritja, ker je ta mn. odprta mora vsbovati interval $(c-\varepsilon_1, c+\varepsilon_2)$, torej lahko končnemu podpokritju $[a,x]$ dodamo $(c-\varepsilon_1, c+\varepsilon_2)$. Torej imamo končno pokritje za $[a,x]$.
> > 
> > 
> > 
> > $c = b$, ker končno podpokritje za $[a,c]$ seže čez $c$.

---

**Trditev:** V metričnem prostoru so vsi kompaktni zaprti.

**Dokaz:**
Naj bo $K$ kompakt. Polj. $x \notin K$.
$$\forall a \in K \ \exists \text{ okolica } a \text{ tako da sta okolici } x \text{ in } a \text{ disj.}$$
$$\{ K(a, r_a) ; a \in K \} \Rightarrow \text{obstaja končno podpokritje.}$$
Vzamemo najmanjši $r_a$ in vidimo, da je $K(x, \min r_a)$ disj. s pokritjem.
Ker imamo končno, nimamo $\inf$, ki bi lahko bil $0$.

---

V metričnem prostoru je vsak kompakt zaprt in omejen.

---

**Trditev:**
$$X^{\text{komp.}} , A^{\text{zap.}} \subseteq X \Rightarrow A \text{ kompakt}$$

**Dokaz:**
Naj bo $U$ pokritje $A$. Dopolnimo pokritje $X$ tako, da dodamo $A^c$ (odprta mn.).
$X$ je komp. $\Rightarrow$ ima končno podpokritje.
Iz končnega pokritja odstranimo $A^c$ in dobimo končno podpokritje $A$.
























<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>


Ena izmed topoloških lastnosti je **povezanost**.

$X$ je povezan če ga lahko zapišemo kot unijo $U$ in $V$ za kateri velja da sta
- **odprti** in **neprazni**
- $U \cap V = \emptyset$
- $U \cup V = X$

> $(0, 1)$ in $[0, 1)$ nista homeomorfni.
> 
> >[!|dokaz]+ Dokaz:
> >
> > Predpostavimo nek homeomorfizem med $[0,1) \to (0,1)$. 
> > 
> > Če odvzamemo točko $f(0)$ iz $(0,1)$ in $0$ iz $[0,1)$, potem dobimo homeomorfizem iz $(0, 1) \to (0, f(0)) \cup (f(0), 1)$, kar sta disjunktni podmnožici.
> > $\implies$ **povezanost** se ne ohranja, torej polzaprt in odprt interval ne moreta biti homeomorfna.
> > 
> > *Primer bijekcije iz $[0,1) \to (0,1)$ : $f(0) = \frac{1}{2}, f(\frac{1}{n})= \frac{1}{n+1} \,;\; n \geq 2$, za ostale pa $f(x) = x$*

Tukaj uporabimo naslednji izrek


> Če je $f: X \to Y$ homeomorfizem, potem je za poljubno točko $x \in X$ tudi 
> $$f|_{X \setminus \{x\}}: X \setminus \{x\} \to Y \setminus \{f(x)\}$$
> homeomorfizem.
> >[!|dokaz]+ Dokaz:
> >
> > Če je $f$ bijekcija med $X$ in $Y$, potem je $f$ nujno tudi bijekcija med $X \setminus \{x\}$ in $Y \setminus \{f(x)\}$.
> > **Zveznost:** Če je $f$ zvezna na celotnem prostoru $X$, je po definiciji  zvezna tudi na vsaki njegovi podmnožici.
> > Enako velja za $f^{-1}$.
