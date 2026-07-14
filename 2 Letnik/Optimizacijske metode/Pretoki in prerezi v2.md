Problem **pretoka** je iskanje maksimalne količine enot iz enega vozliša v drugo, kjer imamo na vsaki povezavi omejeno število enot ki jih lahko prenesemo. *angl. flow*

> Naj bo $G(V,E)$ usmerjen graf. 
> V množici vozlišč izberemo $s,t$ *angl. source, terminal* vozlišči kjer ne obstaja povezava ki gre v $s$ ali iz $t$.
> Naj bo $c : V \times V \rightarrow \mathbb{R}^{+}$ funkcija omejitve na vsaki povezavi $ij$.
> 
> Naj bo  **pretok** $f : V \times V \rightarrow \mathbb{R}$ če velja
> - $f(i,j) = -f(j,i)$
> - $\sum_{i}^{}f(i,j) = \sum_{k}^{}f(j,k)$ oz. velja Kirchhoffovi zakoni
> - $f(i,j) \leq c(i,j)$

**Opombe:**
1.  $f(i, j) < 0$ je povezava usmerjena od $j$ do $i$.

2.  $f(i, i) = -f(i, i) \implies f(i, i) = 0$

3.  če je $f(i,j) \leq 0 = c_{ij}$ je $f(j,i) = -f(i,i)$ torej je $f(i,j) = 0$ kar je ekv. temu da $ij$ ne obstaja.

**Dfn.: Prostornina pretoka** omrežja $(G,c,s,t)$ je 

$$|f|  = \sum_{j}^{}f(s,j)$$

Problem **največjega pretoka** je iskanje maksimalne vrednosti $|f|$.

> **Trditev:** Vsota enot ki grejo iz $s$ je enaka vsoti enot ki grejo v $t$.
> >[!|dokaz]+ Dokaz:
> >
> > $$\forall v \in  V \backslash \{ s,t\} $$
> > $$\sum_{e \,\in\, \text{in}(v)}^{}x_{e}=\sum_{e \,\in\, \text{out}(v)}^{}x_{e}$$
> > 
> > To enakost seštejemo po vseh $v$-jih ki so v $V \backslash \{ s,t\}$. Vidimo da za povezavo z $x_{e}$ ki ne gre iz $s$ ali v $t$ se bo prištelo in odštelo $x_{e}$, torej se vsi $x_{e}$ ki ne peljejo iz $s$ ali v $t$ pokrajšajo.
> > 
> > $$\sum_{\text{end}(e) = t}^{}x_{e} - \sum_{\text{begin}(e) = s}^{}x_{e} = 0$$
> > 


**Dfn.: Prerez** $C$ omrežja $(G,s,t,c)$ je podmnžica $V$, kjer velja da je $s \in C, t \notin C$. 

**Dfn.: Kapaciteta prereza** je

$$|C| = \sum_{\substack{i \in C\\ j \notin C}}^{}c(ij)$$

**Problem najmanjšega prereza** je iskanje minimuma $|C|$.

**Dfn.:** Naj bo $C$ prerez. **Prostornina toka skozi prerez** $f(C)$ je enak $\sum_{\substack{i \in C\\ j \notin C}}^{}f(ij)$.

$$f(C) = \sum_{\substack{i \in C\\ j \notin C}}^{}f(ij)$$

> **Trditev:** Prostornina pretoka je enaka kapaciteti kateregakoli prereza.
> 
> $$|f| = f(C)$$
> 
> >[!|dokaz]+ Dokaz:
> >Za vsak $v \in C$ velja
> >
> >$$\sum_{e \,\in\, \text{out}(v)} x_e = \sum_{e \,\in\, \text{in}(v)} x_e $$
> >Seštejemo po vseh vozliščih razen $s$,
> >
> >$$\sum_{e \,\in\, \text{out}(v)} x_e = \sum_{e \,\in\, \text{in}(v)} x_e \;\;\;\;/ \sum_{v \in C \,-\, \{s\}}$$
> >$$\sum_{e \,\in\, \text{out}(C\, - \,\{s\}\!) } x_e = \sum_{e \,\in\, \text{in}(C\, - \,\{s\}\!) } x_e$$
> >V tem se $x_{e}$ pokrajša če je povezava v celoti vsebovana v $C \backslash \{ s\}$ oz. ne pelje v drugo množico.
> >  
> > $$\sum_{\substack{\text{začetek}(e) \in C \setminus \{s\} \\ \text{konec}(e) \notin C \setminus \{s\}}} x_e = \sum_{\substack{\text{konec}(e) \in C \setminus \{s\} \\ \text{začetek}(e) \notin C \setminus \{s\}}} x_e$$
> > 
> > Če sedaj pogledamo razliko med pretokom ven in pretokom v prerez oz. $f(C)$, lahko uporabimo identiteto
> > 
> > $$\sum_{\substack{i \in C \\ j \notin C}} x_{ij} - \sum_{\substack{i \notin C \\ j \in C}} x_{ij} = $$ $$\sum_{\substack{i \in C \setminus \{s\} \\ j \notin C}} x_{ij} + \sum_{\substack{i = s\\ j \notin C}} x_{ij}- \sum_{\substack{i \notin C \setminus \{s\} \\ j \in C }} x_{ij} + \sum_{\substack{i = s\\ j \in C}} x_{ij}$$
> >  *Prvo vsoto razbijemo po $i$ kjer je $i$ lahko $s$ ali pa polj. vozl. v $C$.*
> >  *Pri drugi vsoti rabimo da $i$ **ni v $C \setminus \{ s\}$** , da lahko uporabimo prejšnjo enačbo, ampak sedaj smo odšteli poleg $i$-jev ki niso v $C$ tudi $i$-je ki so $s$ kar pomeni da jih moramo prišteti nazaj.* 
> >  
> >  Sedaj uporabimo identiteto da pokrajšamo 
> >  
> >  $${\color{green}\sum_{\substack{i \in C \setminus \{s\} \\ j \notin C}} x_{ij} }+ \sum_{j \notin C} x_{sj} \; {\color{green}-\sum_{\substack{i \notin C \setminus \{s\} \\ j \in C }} x_{ij}} + \sum_{j \in C } x_{sj}$$
> >  
> >  Torej dobimo
> >  $$ \sum_{j \notin C} x_{sj} + \sum_{j \in C } x_{sj}$$
> >  
> >  Kar je vsota po vseh $j$-jih
> >  
> >  $$\sum_{j \in V}^{}x_{sj}$$
> >
> >kar pa je ravno prostornina pretoka.
> >
> >Torej velja da za vsak prerez velja
> >
> > $$\sum_{\substack{i \in C \\ j \notin C}} x_{ij} - \sum_{\substack{i \notin C \\ j \in C}} x_{ij} =\sum_{j \in V}^{}x_{sj}$$

**Posledica:** Tok skozi vse prereze je enak.

> **Šibki izrek o dualnosti:** Velja da je max. pretok manjši ali enak min. kapaciteti prereza. 
> 
> $$\max |f| \leq \min |C|$$
> 
> >[!|dokaz]+ Dokaz:
> > Če le malo dopolnimo dokaz od prej vidimo da je
> > 
> > $$|f| = f(C) \leq c(C) = |C|$$
> > 
> > kjer je $c(C) = \sum_{i \in C, j \notin C}^{}c(ij)$.

**Posledica:** Če je $|f| = |C|$ potem je $f$ maks. pretok in $C$ min. prerz.

*Naj bo $f'$ max pretok. Naj bo $f$ polj. pretok. Velja torej $|f|' \geq |f|$, hkrati po šibkem dual. izreku vemo $|f'| \leq |C| = |f|$, torej je $|f'| = |f|$.*

**Def.:** Preslikavo $r : V \times V \to \mathbb{R}^{+}$, kjer je $r(i, j) = c_{ij} - f(i, j)$, imenujemo residualna prepustnost omrežja $(G, c, s, t)$ glede na pretok $f$.

Povezava $ij$ je **zasičena**, če $f(i, j) = c_{ij}$.
Povezava $ij$ je **nezasičena**, če $f(i, j) < c_{ij}$.

Graf $G_f = (V_f, E_f)$, kjer je $V_f = V(G)$, $E_f = \{ i, j \,;\; r(i, j) > 0 \}$ skupaj s prepustnostjo $r$ in vozliščema $s, t$ imenujemo residualno omrežje glede na pretok $f$.

> **Trditev:**
> 
> Naj bo $f$ pretok v omrežju $(G, c, s, t)$ in $(G_f, s, t, r)$ residualno omrežje glede na $f$. 
> 
> Če je $f'$ pretok v $G_f$, je $f + f'$ pretok v $G$ in $|f + f'| = |f| + |f'|$
> 
> >[!|dokaz]+ Dokaz:
> >
> > 
> > Za dokaz, da je $f + f'$ pretok, preverimo
> > 
> > 1. **Antisimetričnost:** 
> >    $$ (f+f')(i,j) = f(i,j)+f'(i,j) = -f(j,i)-f'(j,i) = -(f+f')(j,i) $$
> > 2. **Kirchhoffovi pogoji:** Za vsak $i \neq s, t$ velja:
> >    $$ \sum_{j \in V} (f+f')(i,j) = \sum_{j \in V} f(i,j) + \sum_{j \in V} f'(i,j) = 0 + 0 = 0 $$
> > 3. **Ustreznost:** Ker je $f'(i, j) \le r(i, j)$, velja:
> >    $$ (f+f')(i,j) \le f(i,j) + r(i,j) = f(i,j) + c(i,j) - f(i, j) = c(i,j) $$
> > 
> > Vrednost pretoka se sešteje
> > $$ |f + f'| = \sum_{j \in V} (f + f')(s, j) = \sum_{j \in V} f(s, j) + \sum_{j \in V} f'(s, j) = |f| + |f'| $$
***

**Dfn.:** Pot od $s$ do $t$ je **nezasičena** v $G$, če so vse njene povezave nezasičene.


>**Trditev:** Naj bo $(G, c, s, t)$ omrežje in $f$ pretok v tem omrežju.
> 
> Naslednje trditve so ekvivalentne:
> (1) $f$ je največji pretok,
> (2) v $G_f$ ni nezasičenih poti,
> (3) obstaja prerez $C$, za katerega je $|f| = |C|$.
> 
> >[!|dokaz]+ Dokaz:
> >
> > $(1)\implies (2)$ Uporabimo protislovje. Predpostavimo, da v $G_f$ obstaja nezasičena pot $P$ od $s$ do $t$ z ozkim grlom $\Delta > 0$. Vzdolž te poti lahko v $G_f$ definiramo pretok $f'$ velikosti $\Delta$. Po Trditvi 3 je vsota $f + f'$ dopusten pretok v $G$ z velikostjo $|f + f'| = |f| + \Delta > |f|$, kar je v protislovju s predpostavko, da je $f$ največji pretok.
> > 
> > $(2)\implies (3)$ Definirajmo množico $A \subseteq V$ kot množico vseh vozlišč, ki so v rezidualnem grafu $G_f$ dosegljiva iz izvora $s$. Ker v $G_f$ ni nezasičene poti od $s$ do $t$, ponor $t$ ne leži v $A$. $A$, tvori prerez $C.$ Po definiciji množice $A$ morajo biti vse povezave od $u \in A$ do $v \in B$ popolnoma zasičene ($f(u, v) = c(u, v)$), pretok v obratni smeri pa mora biti enak nič. Neto pretok čez prerez $C$ je zato enak njegovi kapaciteti, $f(C) = |C|$. Ker za poljuben prerez velja $|f| = f(C)$, neposredno sledi $|f| = |C|$.
> > 
> > $(3)\implies (1)$ Uporabimo šibko dualnost.









Za ta problem lahko uporabimo simpleksno metodo na omrežjih ali pa **Ford-Fulkersonov** algoritem.