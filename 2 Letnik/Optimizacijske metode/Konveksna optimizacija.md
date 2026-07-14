**Globalni in lokalni minimum**
> Naj bo $A \subseteq \mathbb{R}^n, f: A \to \mathbb{R}$. 
> 
> Pravimo da ima $f$ v $x \in A$ globalen minimum če velja
> 
> $$ \forall x' \in A : f(x) \le f(x') $$
> Pravimo da ima $f$  v $x \in A$ lokalni maksimum če velja
> $$\exists \varepsilon > 0 ,\;\forall x' \in A : \|x - x'\| < \varepsilon \Rightarrow f(x) \le f(x')$$
> $(\text{oz. } \forall x' \in A \cap K_\varepsilon(x))$

Pravimo da ima $f$ v $x \in A$ lokalni maksimum če

$$\exists \varepsilon > 0 ,\;\forall x' \in A : \|x - x'\| < \varepsilon \Rightarrow f(x) \ge f(x')$$

oz.

$$\exists \varepsilon > 0 ,\;\forall x' \in K(x,\varepsilon) \Rightarrow f(x) \ge f(x')$$


kjer je $K_r(x) = \{y \in \mathbb{R}^n : \|x - y\| < r\}$
odprta krogla s polmerom $r$ in središčem v $x$

***

**Konveksna optimizacija**

Optimizacijska naloga $D, f, \text{opt}$ je konveksna opt. naloga če velja

1. $D \subseteq  \mathbb{R}^{n}$ je konv.
2. $f: D \rightarrow \mathbb{R}$ je konv. funkcija
3. $\text{opt} = \min$

*Ekvivalentno je $f$ lahko konkavna in iščemo maksimum.*

> **Trditev:** Če je $x \in K^\text{konv.} \subseteq \mathbb{R}^{n}$ lokalni minimum konveksne funkcije $f$, potem je $x$ tudi globalni minumum.
> >[!|dokaz]+ Dokaz:
> >Naj bo $x$ lokalni min.
> > Če $x$ ni globalni min. potem obstaja $y \in K$ tako da je $f(y)<f(x)$.
> > Naj bo $\lambda \in (0,1]$ vidimo da dobimo
> > 
> > 
> > $$f((1-\lambda)x + \lambda y) \leq (1-\lambda) f(x) + \lambda f(y) < (1-\lambda) f(x) + \lambda f(x)$$
> > $$f((1-\lambda)x + \lambda y)  < f(x)$$
> > 
> > Ker je $x$ lokalni min. vemo da obstaja $\varepsilon$ okolica kjer velja $f(x') > f(x)$,  $x' \in K(x,\varepsilon)$. Ampak če vzamemo $\lambda < \frac{\varepsilon}{y-x}$ oz. kar $\lambda = \frac{\varepsilon}{2(y-x)}$ bo ko vstavimo $\lambda$ veljalo da je $f(x + \lambda(y-x))$ enako $f(x+\frac{\varepsilon}{2})$ kar mora biti po definiciji lok. minimuma večje od $f(x)$ ampak ker je funkcija konveksna mora biti tudi manjša od $f(x)$ kar je protislovje.



> **Trditev** Naj bo $K \subseteq \mathbb{R}^n$ konveksna množica in $f : K \to \mathbb{R}$ strogo konveksna funkcija. Potem je globalni maksimum $f$ na $K$ v ekstremni točki množice $K$.
> 
> >[!|dokaz]+ Dokaz:
> >
> > Naj bo $x^{*}$ globalni max. $f$ na $K$.
> > 
> > Recimo, da $x^{*}$ ni ekstremna točka $K$.
> > 
> > Potem $\exists y, z \in K$ in $\lambda \in (0, 1) : x^* = (1 - \lambda) y + \lambda z$
> > 
> > $$f(x^{*}) \underset{\substack{\uparrow \\ f \text{ strogo} \\ \text{konveksna}}}{<} \underset{\geq 0}{(1 - \lambda)} \cdot \underset{\leq f(x^{*})}{f(y)} + \underset{\geq 0}{\lambda} \cdot  \underset{\leq f(x^{*})}{f(z)} \leq$$ 
> > $$\leq (1 - \lambda) f(x^{*}) + \lambda f(x^{*}) = f(x^{*})$$
> > 
> > Kar je protislovje saj $f(x^{*}) < f(x^{*})$ nima smisla.

> **Primer:**
> $$K = \{ (x, y) \in \mathbb{R}^2 \mid -1 \leq y \leq 1 \}$$
> $$f : K \to \mathbb{R}$$
> $$f(x, y) = y^2$$
> 
> Vidimo $f$ je konveksna, a ni strogo konveksna
> 
> To lahko vidimo tudi iz $$H_f(x, y) = \begin{bmatrix} 0 & 0 \\ 0 & 2 \end{bmatrix} \geq 0$$
> 
> Opazimo da ima $f$ globalni maksimum v $(x, \pm 1), x \in \mathbb{R}$
> 
> Nobeden od globalnih maksimumov ni ekstremna točka.
> 
> To se lahko zgodi, ko $f$ ni strogo konveksna.

**Opomba:** Če je $f$ strogo konveksna ni nujno da ima globalni maksimum, če ima globalni maksimum ni nujno da je edini.



Da je funkcija konveksna lahko preverimo z definicijo, z odvodi, če je odvedljiva s tangento, *kjer lahko konveksno funkcijo karakteriziramo s tem da je tangenta vedno pod funkcijo pri tangentni funkciji* ${\color{light}f(y) \geq f(x)+f'(x)(y-x)}$.
ponavadi pa uporabljamo drugi odvod, kjer mora veljati da je $f''(x) \geq 0$.

Ko delamo s funkcijami več spremenljivk uoprabljamo gradient, ki kaže v smer naraščanja funkcije. Delamo v konevksni množici nad konveksnimi funkcijami.

> **Izrek: Kriterij 1. odvoda**
> 
> Naj bo $K \subseteq \mathbb{R}^n$ konveksna in odprta in
> $f : K \to \mathbb{R}$ odvedljiva ($\Rightarrow$ obstajajo $\frac{\partial f}{\partial x_1}, \dots, \frac{\partial f}{\partial x_n}$), kjer **ni nujno, da so parcialni odvodi zvezni.**
> Velja:
> 
> $$f \text{ konveksna }$$
> $$\Leftrightarrow$$
> $$ \forall x, y \in K :f(y) \geq f(x) + \nabla f(x)^T (y - x)$$
> 
> Torej tangentna hiperravnina leži pod grafom funkcije.
> 
> 
>  >[!|dokaz]+ Dokaz:
> > 
> > 
> > $(\Leftarrow)$ 
> > Naj bodo $x, y \in K,\, \lambda \in [0, 1],\, z = (1 - \lambda)x + \lambda y$. Vemo da po predpostavki velja:
> > 
> > $$f(x) \geq f(z) + \nabla f(z)^T (x - z) \quad / \cdot (1 - \lambda)$$
> > $$f(y) \geq f(z) + \nabla f(z)^T (y - z) \quad / \cdot \lambda$$
> > 
> > $$(1 - \lambda) f(x) + \lambda f(y) \geq f(z) + \nabla f(z)^T (\underbrace{(1 - \lambda)(x - z) + \lambda(y - z)\;\;\;\;}_{(1 - \lambda)x + \lambda y - z = 0}\!\!\!\!\!\!\!)=$$ $$ = f(z) = f((1 - \lambda)x + \lambda y)$$
> > 
> > Torej je
> > 
> > $$(1 - \lambda) f(x) + \lambda f(y) \geq f((1 - \lambda)x + \lambda y)$$
> > 
> > $\Rightarrow f$ je konveksna.
> > 
> > $(\Rightarrow)$
> > 
> > Imamo konveksno mn. $K$. Naj bosta $x,y \in K$. Velja da je $(1-\lambda)x + \lambda y \in K$.
> > 
> > Trdimo da je v $K$ tudi $(1-\lambda)x + \lambda y \in K$, kjer je $\lambda \in [-\delta,1 + \delta]$. *To velja ker je $K$ odprta.*
> > 
> > $\exists  K(x,\varepsilon_{1}) \subseteq K$
> > $\exists  K(y,\varepsilon_{2}) \subseteq K$
> > 
> > Naj bo $\delta = \min \{ \frac{\varepsilon_{1}}{\left\Vert y-x \right\Vert }, \frac{\varepsilon_{2}}{\left\Vert y-x \right\Vert }\}$
> > 
> > Potem bo za vsak $\lambda \in [-\delta, 1+\delta]$ še vedno $(1-\lambda)x + \lambda y \in K$.
> > 
> > Definiramo $g(\lambda) = (1-\lambda)x + \lambda y$, $g: (-\delta, 1+ \delta) \mapsto K$.
> > 
> > $$f \circ g : (-\delta, 1+\delta) \rightarrow \mathbb{R}$$
> > 
> > Njen odvod bo
> > 
> > $$f(g(\lambda))' = \nabla f \cdot dg = \nabla f \cdot (g_{1}'(\lambda),..., g_{n}'(\lambda))$$
> >$$\sum_{i=1}^{n} \frac{\partial f}{\partial x_i} ((1-\lambda)x + \lambda y) \cdot (y_i - x_i)$$
> >
> >Vstavimo $\lambda = 0$ torej je
> >
> >$$f(g(0))' = \sum_{i=1}^{n} \frac{\partial f}{\partial x_i} (x) \cdot (y_i - x_i)$$
> >$$f(g(0))' = \lim_{\lambda \to 0}\frac{f(g(\lambda))-(f(g(0)))}{\lambda}$$
> >
> >zanima nas samo desna limita
> >
> >$$f(g(0))' = \lim_{\lambda \to 0^{+}}\frac{f(g(\lambda))-(f(g(0)))}{\lambda}$$
> >
> >kar je
> >
> >$$f(g(0))' = \lim_{\lambda \to 0^{+}}\frac{f((1-\lambda)x + \lambda y)-f(x)}{\lambda}$$
> >
> >ker je $f$ konveksna je $f((1-\lambda)x + \lambda y) \leq (1-\lambda)f(x) + \lambda f(y)$
> >
> >$$\leq \lim_{\lambda \to 0^{+}}\frac{(1-\lambda)f(x) + \lambda f(y)-f(x)}{\lambda}$$
> >
> >izračunamo limito in dobimo
> >
> >$$\lim_{\lambda \to 0^{+}}\frac{(1-\lambda)f(x) + \lambda f(y)-f(x)}{\lambda} = f(y)-f(x)$$
> >
> >torej je
> >
> >$$f(y)-f(x) \geq \nabla f(x) \cdot (y-x)$$



> **Def.:** 
> 
> $A \in \mathbb{R}^{n \times n}$ je **pozitivno semidefinitna**, če velja  $\forall x \in \mathbb{R}^n : x^T A x \ge 0$
> 
> $A$ je **pozitivno definitna**, če velja $x^T A x > 0$ $\forall x \in \mathbb{R}^n \setminus \{0\}$
> 
> Oznake:
> $A \ge 0$ (pozitivno semidefinitna)
> $A > 0$ (pozitivna oz. pozit. definitna)


> **Trditev:**
> 
> Naj bo $A \in \mathbb{R}^{n \times n}$, $A^T = A$
> $$\text{$A \ge 0$ $\Leftrightarrow$ vse lastne vrednosti $A$ so nenegativne  
$\Leftrightarrow$ glavni minorji $\ge 0$ }$$
> 
> 
> $$\text{$A > 0 \Leftrightarrow$ vse lastne vrednosti $A$ so večje od $0$ $\Leftrightarrow$ vodilni glavni minorji $>$ 0}$$
> 
> Glavni minorji matrike $A$ so determinante njenih podmatrik, ki jih dobimo tako, da izberemo isto množico indeksov vrstic in stolpcev.
> 
> Vodilni glavni minorji so tisti kjer izberemo začetnih $k$ indeksov.

> **Trditev:**
> 
> Naj bo $A = \begin{bmatrix}a & b \\ c & d\end{bmatrix}$.
> Velja
> 
> $$A \geq 0 $$ $$\Leftrightarrow \lambda_{1}, \lambda_{2} \geq 0  $$ $$\Leftrightarrow \lambda_{1}\lambda_{2}\geq 0, \lambda_{1}+\lambda_{2} \geq 0 $$ $$\Leftrightarrow ac-b^{2}\geq 0, a+c \geq 0 $$ $$\Leftrightarrow ac-b^{2},a\geq 0$$

> **Dfn.:** Hessejeva matrika funkcije je matrika drugih odvodov. 
> 
> $$ H_f(x) = \left[ \frac{\partial^2 f(x)}{\partial x_i \partial x_j} \right]_{i,j=1}^n$$
> 
> Velja da je simetrična oz. da velja $H_{f}^{T}=H_{f}$, ker je simetrična ima tudi same realne lastne vrednosti.


> **Kriterij 2. odvoda**
> 
> Naj bo $K \subseteq \mathbb{R}^n$ konveksna in odprta in naj bo $f : K \to \mathbb{R}$ dvakrat zvezno odvedljiva na K oz. $f \in C^{2}$
> 
> 
> $$\text{$f$ je konveksna na $K \Leftrightarrow H_f(x) \ge 0$ za vse $x \in K$ }$$ 
> 
> Če velja $H_f(x) > 0 \Rightarrow f$ je strogo konveksna
> 
*Obrat ne velja npr.: $f : x \to x^4$ je strogo konveksna,*  
*vendar je $f''(x) = 12x^2 = 0$ za $x = 0$*



***

**Pogoji Karusha, Kuhne in Tuckerja in vezani ekstremi z neenačbami**

Če iščemo globalni min/max diferenciabilne $f : D \rightarrow \mathbb{R}$ na $D^\text{komp.} \subseteq \mathbb{R}^n$.  
Pogledamo:
* lokalne ekstreme
* rob (npr. z Lagrangeevimi multiplikatorji)

**Analiza**  
Naj bo $D \subseteq \mathbb{R}^n$ odprta, $f : D \to \mathbb{R} \in C^{2}$. 

$$\text{Če je  $x^{*} \in D$ lokalni minimum} \Rightarrow \begin{cases} \nabla f(x^*) = 0 \\ H_f(x^*) \ge 0 \end{cases}$$

$$\left. \begin{matrix} x^{*} \in D,\\ \nabla f(x^{*}) = 0 \\ H_{f(x^{*})} > 0 \end{matrix} \right\}\Rightarrow x^{*} \text{ je lok. min.}$$

> **Obstoj globalnih ekstremov**  
> 
> Naj bo $K \subseteq \mathbb{R}^n$ kompaktna (zaprta in omejena)  in $f : K \to \mathbb{R}$ zvezna funkcija  
> Potem je $f$ omejena na $K$ in na $K$ zavzame maksimum in minimum

***

**Problem vezanih ekstremov z neenačbami (VEN)**

Povejmo predpostavke ki naj držijo za cel oddelek naprej.

1. $\Omega \subseteq \mathbb{R}^n$ odprta množica
2. $f, g_1, \dots, g_m : \Omega \to \mathbb{R}$ naj bodo odvedljive

Naj bo problem vezanih ekstremov z neenačbami problem s podatki

$$D = \{ x \in \Omega \mid g_i(x) \le 0 \text{ za } i = 1, \dots, m \}$$

kjer iščemo

$$\min_{x \in D} f(x)$$



> **Trditev:**
> Naj bo $\Omega \subseteq \mathbb{R}^n$ konveksna množica,
> $g_i : \Omega \to \mathbb{R}$ konveksne funkcije za $i = 1, \dots, m$
> Potem je $D = \{ x \in \Omega \mid g_i(x) \le 0, i = 1, \dots, m \}$ konveksna množica.
> 
> >[!|dokaz]+ Dokaz:
> >
> > Definirajmo $D_i = \{ x \in \Omega \mid g_i(x) \le 0 \}, i = 1, \dots, m$
> > $D_i$ je konveksna množica.
> > $x, y \in D_i, \lambda \in [0, 1]$
> > 
> > $$g_i((1-\lambda)x + \lambda y) \le (1-\lambda)g_i(x) + \lambda g_i(y) \le 0$$
> > 
> > *ker je $g_{i}$ konveksna, drugi neenačaj pa velja po dfn. $D_{i}$*
> > 
> > 
> > $\Rightarrow (1-\lambda)x + \lambda y \in D_i$
> > $\Rightarrow D = \bigcap_{i=1}^m D_i$ je presek konv. množic, torej je konveksna.


**Posledica:**
Če so $f, g_1, \dots, g_m$ konveksne funkcije, je problem VEN konveksna opt. naloga.

*Te naloge lahko rešujemo kot iskanje loklanih min., ter eksplicitno reševanje robnih enačb, lahko rešujemo robne enačbe z lagrangevimi multiplikatorji.* 

Lahko pa direktno začnemo z lagrangevo funkcijo in vzamemo obe mejni funkciji in obe hkrati šutdiramo v isti enačbi.

Naj bo primer $f(x) = 2x^{3}+ 4x^{2}+y^{2}-4xy$, $g_{1}=(y-4)$, $g_{2}= (x^{2}-y)$. *$g_{1,2}$ izhajata iz pogojev $y \leq 4$, $x^{2}\leq y$.*

Napišemo lagranga

$$L(x,y,\lambda,\mu) = 2x^{3}+4x^{2}+y^{2}-2xy+ \lambda(y-4) + \mu(x^{2}-y)$$
$$L_{x}=6x^{2}+8x-2y+2\mu x = 0$$
$$L_{y} = 2y - 2x + \lambda - \mu = 0$$

Če je $\lambda=0$, $\mu=0$ potem študiramo notranjost. Imamo $L_{x}$ in $L_{y}$

Če $\lambda\neq 0$ in je $\mu=0$, potem študiramo zgornji rob.
Če $\lambda = 0$ in je $\mu \neq 0$ potem študiramo spodnji rob.
Če $\lambda \neq 0$ in $\mu \neq 0$ potem gledamo presečišča robov.

Enačbam $L_{x}$ in $L_{y}$ dodamo še robne pogoje ko $\lambda \lor , \neq 0$, zraven pa še vedno veljajo neenakosti

$$L_{x}=6x^{2}+8x-2y+2\mu x = 0$$
$$L_{y} = 2y - 2x + \lambda - \mu = 0$$
$$\lambda(y-4) = 0$$
$$\mu(x^{2}-y) = 0$$
$$y-4 \leq 0$$
$$x^{2}-y \leq 0$$

temu rečemo KKT pogoji.


***

Torej imamo

$$\max / \min\; f(x)$$
$$x \in \Omega$$
$$g_{1},...,g_{m}(x) \leq 0$$
$$L(x,\lambda) = f(x) + \sum_{i=1}^{m}\lambda_{i}g_{i}(x)$$

Kjer je $L(x,\lambda)$ **lagrangeeva funkcija**, $\lambda, x$ pa sta vektorja  $\lambda \in \mathbb{R}^{m}$, $x \in \mathbb{R}^{n}$.

Skalarje $\lambda_1, \dots, \lambda_m$ imenujemo **Lagrangeevi multiplikatorji**.

Veljati mora

$$L_{x_{i}} = 0$$
$$\lambda_{j}g_{j} = 0$$
$$g_{j}\leq 0$$
$$\lambda_{j} \geq 0$$
$$ $$

Za reševanja VEN, zapišemo KKT pogoje, ločimo za vsak $j$ primer ko je $\lambda_{j}=0$ in $\lambda_{j}\neq 0$ torej $2^{m}$ možnosti.

Ko predelamo vse sisteme enačb dobimo vse kandidate za globalne ekstreme.

**Def.:** Točka $x^* \in \Omega$ zadošča pogojem KKT, če obstajajo skalarji $\lambda_1, \lambda_2, \dots, \lambda_m$, da velja:
1. KKT1: $\frac{\partial L}{\partial x_i} (x_1^*, \dots, x_n^*, \lambda_1, \dots, \lambda_m) = 0 \quad i = 1, \dots, n$
2. KKT2: $\lambda_i \cdot g_i(x^*) = 0 \quad i = 1, \dots, m$
3. KKT3: $g_i(x^*) \le 0 \quad i = 1, \dots, m$   $\Rightarrow$ $\lambda_i \ge 0 \quad i = 1, \dots, m$

V splošnem KKT pogoji niso niti zadostni niti potrebni pogoji za globalni oz. lokalni ekstrem.

Recimo $x^{2}-y^{2}, x \geq 0, y\geq 0$ dobimo $(0,0)$ kot lok. min. ampak vidimo da

**Iskanje KKT točk**

- Zapišemo pogoje KKT
- Za $\forall i$ ločimo primer $\lambda_i = 0$ in $\lambda_i > 0$  
  in rešimo ustrezen sistem enačb/neenačb
- $2^m$ primerov
- Za $m=2$, so 4 primeri:
  1a: $\lambda_1 = 0, \lambda_2 = 0$  
  1b: $\lambda_1 = 0, \lambda_2 > 0$  
  2a: $\lambda_1 > 0, \lambda_2 = 0$  
  2b: $\lambda_1 > 0, \lambda_2 > 0$

> **Izrek o zadostnosti pogojev**
> 
> Naj bo $\Omega \subseteq \mathbb{R}^n$ odprta in konveksna  mn. in 
> naj bodo $f, g_1, \dots, g_m : \Omega \to \mathbb{R}$ konveksne in odvedljive na $\Omega$
> 
> Velja da če $x^* \in \Omega$ ustreza pogojem KKT, potem je $x^*$ globalni minimum oz. rešitev problema VEN.
> 
> >[!|dokaz]+ Dokaz:
> >
> > Ker so $f, g_1, \dots, g_m$ konveksne, velja *kriterij 1. odvoda*  
> > 
> > $$f(x) \ge f(x^*) + \nabla f(x^*)^T (x - x^*)$$
> > $$g_i(x) \ge g_i(x^*) + \nabla g_i(x^*)^T (x - x^*)$$
> > 
> > Pomnožimo te neenačbe z $\lambda_i \ge 0$ in seštejemo:  
> > 
> > $$f(x) + \sum_{i=1}^{m} \lambda_{i} g_{i}(x) \ge $$ 
> > $$\ge f(x^*) + \sum_{i=1}^m \underbrace{\lambda_i g_i(x^*)}_{0 \text{ po KKT2}} + \left( \nabla f(x^*) + \sum_{i=1}^m \lambda_{i} \nabla g_{i}(x^*) \right)^T (x-x^*)$$
> > $$\left( \nabla f(x^{*}) + \sum_{i=1}^{m} \lambda_{i} \nabla g_{i}(x^{*}) \right) = \nabla L(x^{*})$$
> > 
> > Po KKT1 velja $L_{x_{i}} = 0$ torej dobimo
> > 
> > 
> > $$= f(x^*)$$
> > 
> > 
> > Velja torej 
> > 
> > $$f(x) + \sum_{i=1}^m \lambda_i g_i(x)  \ge f(x^*)$$  
> > $$f(x) \ge f(x^*) - \sum_{i=1}^m \lambda_i g_i(x)$$  
> > 
> > *ker je $g_{i}(x) \leq 0$ bo $\sum_{}^{}\lambda_{i}g_{i}(x) \leq 0$*
> > 
> > Torej dobimo
> > 
> >  $$f(x) \ge f(x^{*}) - \sum_{i=1}^{m} \lambda_{i} g_{i}(x) \geq f(x^{*})  $$ 
> > 
> > 
> > $\Rightarrow x^*$ je globalni minimum $f$ na $D = \{ x \in \Omega \mid g_i(x) \le 0 \text{ za } i=1, \dots, m \}$.

> **Dodatni izrek od potrebnih pogojih**
> 
> *S tem gledamo ali za vsak minimum lahko trdimo da zanj velja KKT pogoj, oz. da lahko s KKT pogoji najdemo vse minimume.*
> 
> Naj bo $\Omega$ odprta in $f: \Omega \rightarrow \mathbb{R}$ odvedljiva, $g_{1},...,g_{m} : \Omega \rightarrow \mathbb{R}$. Naj velja da je $x^{*}$ lokalni minimum. Če velja en od naslednjih pogojev potem  za $x^{*}$ veljajo KKT pogoji.
> $$g_{1},...,g_{n} \text{ so afine}$$
> $$\Omega, f,g_{1},...,g_{m} \text{ so konveksne, } \text{Interior}(D) \neq 0$$
> $$\text{množica } \{ \nabla g_{1}(x^{*}),...,\nabla g_{m}(x^{*}) \}\text{ je lin. neodvisna}$$
> 
> **Brez dokaza**

> **Posledica:**
> 
> Za konveksni problem, $\mathring{D} \neq \emptyset$ bodo KKT pogoji ekvivalentni globalnemu min.


**Primer:**

 Poišči min $$\frac{1}{x} + \frac{2}{y}$$

kjer velja

$$x > 0$$
$$y > 0$$
$$x+y \le 5$$
$$3x^2+2y^2 \le 35$$


$$\Omega = \{ (x,y) \in \mathbb{R}^2 \mid x > 0, y > 0 \}\text{ je odprta in konveksna}$$

Prevedemo v pravilno obliko

$$f, g_1, g_2 : \Omega \to \mathbb{R}$$
$$f(x,y) = \frac{1}{x} + \frac{2}{y}$$
$$g_1(x,y) = x+y-5$$
$$g_2(x,y) = 3x^2+2y^2-35$$
$$D = \{ (x,y) \in \Omega \mid x+y-5 \le 0, 3x^2+2y^2-35 \le 0 \}$$

Očitno: $f, g_1, g_2$ so na $\Omega$ 2x zvezno odvedljive

Preverimo, če so konveksne:

$$H_f = \begin{bmatrix} \frac{\partial^2 f}{\partial x^2} & \frac{\partial^2 f}{\partial x \partial y} \\ \frac{\partial^2 f}{\partial y \partial x} & \frac{\partial^2 f}{\partial y^2} \end{bmatrix} = \begin{bmatrix} \frac{2}{x^3} & 0 \\ 0 & \frac{4}{y^3} \end{bmatrix} \ge 0$$

Lastni vrednosti sta $\frac{2}{x^3}$ in $\frac{4}{y^3}$, ki sta pozitivni za $\forall x, y \in \Omega$
$\Rightarrow f$ je konveksna funkcija

$g_1$ je afina $\Rightarrow$ konveksna


$$H_{g_2} = \begin{bmatrix} 6 & 0 \\ 0 & 4 \end{bmatrix} \ge 0$$

saj sta lastni vrednosti 6, 4 pozitivni.  
Torej je tudi $g_2$ konveksna funkcija.  
Naloga VEN je konveksna $\Rightarrow$ vsako točko, ki ustreza pogojem KKT, je globalni minimum.  

$L(x, y, \lambda_1, \lambda_2) = \frac{1}{x} + \frac{2}{y} + \lambda_1(x+y-5) + \lambda_2(3x^2+2y^2-35)$

KKT1:  
$\frac{\partial L}{\partial x} = -\frac{1}{x^2} + \lambda_1 + 6\lambda_2 x = 0$  
$\frac{\partial L}{\partial y} = -\frac{2}{y^2} + \lambda_1 + 4\lambda_2 y = 0$

KKT2:  
$\lambda_1(x+y-5) = 0$  
$\lambda_2(3x^2+2y^2-35) = 0$

KKT3:  
$x+y \le 5$  
$3x^2+2y^2 \le 35$

neneg.: $\lambda_1, \lambda_2 \ge 0$

Preverimo različne možnosti za $\lambda_1, \lambda_2$:  
Ia: $\lambda_1=0, \lambda_2=0 \quad$ KKT1: $-\frac{1}{x^2} = 0 \quad \Rightarrow \times \quad //$

Ib: $\lambda_1 > 0, \lambda_2 = 0$  
KKT1:  
$\left. \begin{matrix} -\frac{1}{x^2} + \lambda_1 = 0 \\ -\frac{2}{y^2} + \lambda_1 = 0 \end{matrix} \right\} \Rightarrow \lambda_1 = \frac{1}{x^2} = \frac{2}{y^2} > 0$ (Torej $\lambda_1 > 0 \checkmark$)  
$\Rightarrow x^2 = \frac{y^2}{2}$

$\lambda_1 > 0 \underset{KKT2}{\Rightarrow} x+y-5=0 \Rightarrow y=5-x$

Dobimo $x^2 = \frac{y^2}{2} = \frac{(5-x)^2}{2} \Rightarrow 2x^2 = 25-10x+x^2$  
$x^2+10x-25 = 0$  
$x_{1,2} = \frac{-10 \pm \sqrt{100+4 \cdot 25}}{2}$  
$= -5 \pm 5\sqrt{2} \quad (x>0)$

$x = 5(\sqrt{2}-1)$  
$y = 5-x = 5-5(\sqrt{2}-1) = 5(2-\sqrt{2})$

Dobili smo točko $T(5(\sqrt{2}-1), 5(2-\sqrt{2}))$  
Ali ustreza vsem pogojem KKT?  
KKT1 $\checkmark$ (od tod smo izračunali $x, y, \lambda_1$)  
KKT2 $\checkmark$  
KKT3: $x+y-5 = 0 \le 0 \checkmark$  
$3x^2+2y^2-35 = -x^2-35 \le 0 \checkmark$  
$\nearrow$  
$2x^2=y^2$

$\lambda_1 > 0, \lambda_2 = 0 \checkmark$

Točka $T$ ustreza pogojem KKT. Ker je naloga konveksna, je v njej dosežen globalni min.  
(drugih možnosti za $\lambda_1, \lambda_2$ ni treba preveriti.)

***

