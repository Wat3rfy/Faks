


> Funkcija $F$, definirana na intervalu $I$, se imenuje **primitivna funkcija** ali **nedoločeni integral** funkcije $f$, če je na $I$ funkcija $f$ enaka odvodu funkcije $F$; torej če velja
> $$F'(x) = f(x) \;  \text{za vsak } x \in I.$$

$$ $$

> 
> Naj bo $F$ primitivna funkcija funkcije $f$ na intervalu $I$. Tedaj je za vsako konstanto $C$ tudi funkcija $G$,
> $$G(x) = F(x) + C, \quad x \in I$$
> primitivna funkcija funkcije $f$.
>>[!|dokaz]- Dokaz:
> > **Dokaz:** $G'(x) = (F(x) + C)' = F'(x) + C' = F'(x) = f(x)$. $G$ je primitivna funkcija.


**Oznaka:** Če je $F$ primitivna funkcija funkcije $f$, je diferencial
$$dF(x) = F'(x)dx$$
oziroma
$$dF(x) = f(x)dx$$
Zato pišemo tudi
$$F(x) = \int f(x)dx.$$
*Seštevamo vse majhne spremembe $dF(x)$ čez 0 do x*

Ker je integriranje nasprotna operacija odvajanju, pravila za integriranje sledijo iz pravil za odvajanje.

1.
$$\int (f(x) + g(x))dx = \int f(x)dx + \int g(x)dx$$
2.
$$\int (\lambda f)(x)dx = \lambda \int f(x)dx, \quad \lambda \text{ je konstanta}$$
3.
$$\int (\lambda f + \mu g)(x)dx = \lambda \int f(x)dx + \mu \int g(x)dx, \quad \lambda, \mu \text{ sta konstanti}$$
4.
$$\text{per partes: }\int f(x)g'(x)dx = f(x)g(x) - \int g(x)f'(x)dx$$
$$\int udv = uv - \int vdu.$$
>[!|dokaz]- Dokaz:
>
> $$(f(x)g(x))' = f'(x)g(x) + f(x)g'(x)$$
> sledi
> $$f(x)g(x) = \int (f'(x)g(x) + f(x)g'(x))dx$$
> $$= \int f'(x)g(x)dx + \int f(x)g'(x)dx,$$
> torej
> $$\int f(x)g'(x)dx = f(x)g(x) - \int g(x)f'(x)dx$$

5. Uvedba nove spremenljivke Naj bo $F$ primitivna funkcija funkcije $f$ in $\varphi$ takšna odvedljiva funkcija, da je $F \circ \varphi$ definirana. Tedaj je
$$(F \circ \varphi)'(t) = F'(\varphi(t))\varphi'(t)$$
$$= f(\varphi(t))\varphi'(t),$$
torej
$$F(\varphi(t)) + C = \int f(\varphi(t))\varphi'(t)dt.$$

>[!|txt]- **Integral racionalne funkcije**
> 
> 
> $$\int \frac{P(x)}{Q(x)}dx, \quad P(x), Q(x) \text{ polinoma z realnimi koeficienti}$$
> 
> i) če je $\text{st}(P(x)) \ge \text{st}(Q(x))$, ju delimo in dobimo
> 
> $$P(x) = R(x)Q(x) + T(x)$$
> 
> oziroma
> 
> $$\frac{P(x)}{Q(x)} = R(x) + \frac{T(x)}{Q(x)},$$
> 
> pri čemer je $\text{st}(T(x)) < \text{st}(Q(x))$. Naprej sledi:
> 
> $$\int \frac{P(x)}{Q(x)}dx = \int R(x)dx + \int \frac{T(x)}{Q(x)}dx.$$
> 
> ii) poiščemo vse ničle polinoma $Q(x)$.
> 
> - polinom $Q(x)$ ima vse ničle realne
> 
> $$Q(x) = a(x - x_1)^{k_1}(x - x_2)^{k_2} \ldots (x - x_n)^{k_n}$$
> 
> Potem lahko izraz $T(x)/Q(x)$ zapišemo:
> 
> $$\frac{T(x)}{Q(x)} = \frac{A_1^1}{x - x_1} + \frac{A_2^1}{(x - x_1)^2} + \ldots + \frac{A_{k_1}^1}{(x - x_1)^{k_1}} + \frac{A_1^2}{x - x_2} + \frac{A_2^2}{(x - x_2)^2} + \ldots, \quad A_j^i \text{ so realna števila}$$

**Približek ploščine pod krivuljo**

Naj bo $f$ pozitivna zvezna funkcija na zaprtem intervalu $[a, b]$. 

Na $x$-osi izberemo delilne točke
$$a = x_0 < x_1 < \ldots < x_{n-1} < x_n = b,$$
tj. točke, ki razdelijo interval $[a, b]$ na $n$-kosov. Naj bo za vsak $k, k \in \{1, 2, \ldots, n\}$,
$$x_k - x_{k-1} = \delta_k$$
dolžine $k$-tega kosa podintervala intervala $[a, b]$. V vsakem podintervalu izberemo neko točko $\xi_k$, torej
$$\xi_k \in [x_{k-1}, x_k], \quad k \in \{1, 2, \ldots, n\}.$$
Ploščina $k$-tega pravokotnika je enaka $f(\xi_k)\delta_k$, slika 5.1. Vsota ploščin vseh pravokotnikov pa je
$$f(\xi_1)\delta_1 + f(\xi_2)\delta_2 + \ldots + f(\xi_n)\delta_n = \sum_{k=1}^{n} f(\xi_k)\delta_k.$$

To je približek za ploščino pod krivuljo. Ploščina je enaka limiti teh približkov, ko gre dolžina najdaljšega intervala proti 0 (pri tem pa se seveda število delilnih točk čez vse meje). 




Velja da ko za vsak $\varepsilon$ obstaja $\delta$ da za vsako delitev $D$ velja $\delta > \sup \delta_i$ kot dolžina najdaljšega intervala, bo **riemannova vsota konvergirala k $I$** natanko tedaj ko velja
$$\left(\sum_{i=1}^{n}f(\xi_{i})\delta_{i}\right) - I < \varepsilon$$


Če za funkcijo $f$, definirano na $[a,b]$, obstaja limita $I$ Riemannovih vsot, ko gre dolžina najdaljšega intervala proti 0, pravimo da je funkcija na intervalu $[a,b]$ **integrabilna**, limito $I$ pa imenujemo **določen integral** funkcije $f$ v mejah od $a$ do $b$ in pišemo:
$$I = \int_{a}^{b} f(x)dx.$$

Število $I$ imenujemo tudi **Riemannov integral** oz. **določeni integral** funkcije $f$ na $[a,b]$.


>Če je funkcija $f$ integrabilna na $[a,b]$, je funkcija $f$ na $[a,b]$ omejena.
>
> >[!|dokaz]- Dokaz:
> >Naj bo $f$ na $[a,b]$ integrabilna. Recimo, da $f$ ni navzgor omejena. Naj bo $\varepsilon > 0$. Naj bo $I$ integral funkcije $f$. Tedaj obstaja $\delta > 0$, da je
> > $$\left| \sum_{k=1}^{n} f(\xi_k)\delta_k - I \right| < \varepsilon, \quad \text{čim je } \max \delta_k < \delta.$$
> > Naj bo $a = x_0 < x_1 < \ldots < x_n = b$ neka delitev, kjer je dolžina $\max \delta_k < \delta$.
> > Tedaj velja $(\ast)$ za vsako izbiro točk $\xi_k \in [x_{k-1}, x_k]$. Ker $f$ ni navzgor omejena, lahko vsaj na enem od intervalov $[x_{k-1}, x_k]$ izberemo $\xi_{k_0}$ tako, da bo $f(\xi_{k_0})$ poljubno veliko pozitivno število, torej tudi $f(\xi_{k_0})\delta_{k_0}$ poljubno veliko pozitivno število. To pa je v protislovju z $(\ast)$. Protislovje kaže, da je začetna predpostavka, da $f$ ni navzgor omejena, napačna. Torej je funkcija $f$ navzgor omejena. Podobno pokažemo, da je funkcija $f$ navzdol omejena. $\square$
> > 

**Darbouxeva vsota**

Naj bo $f$ omejena na $[a,b]$. Naj bo
$$m = \inf \{f(x) : x \in [a,b]\}$$
in
$$M = \sup \{f(x) : x \in [a,b]\}.$$
$\mathcal{D}$ naj bo poljubna delitev
$$a = x_0 < x_1 < \ldots < x_{n-1} < x_n = b.$$
Naj bo
$$m_k = \inf \{f(x) : x \in [x_{k-1}, x_k]\}$$
in
$$M_k = \sup \{f(x) : x \in [x_{k-1}, x_k]\}.$$
Jasno je
$$m \le m_k \le M_k \le M, \quad k \in \{1, 2, \ldots, n\}.$$
Vsota
$$m_1\delta_1 + m_2\delta_2 + \ldots + m_n\delta_n$$
je natančno določena z delitvijo $\mathcal{D}$. Imenujemo jo **spodnja Darbouxova vsota**, prirejena delitvi $\mathcal{D}$. Označimo jo $s(\mathcal{D})$.
$$s(\mathcal{D}) := \sum_{k=1}^{n} m_k\delta_k, \quad k \in \{1, 2, \ldots, n\},$$
pri tem je
$$\delta_k = x_k - x_{k-1}.$$
**Zgornja Darbouxova vsota**, prirejena delitvi $\mathcal{D}$, je
$$S(\mathcal{D}) := \sum_{k=1}^{n} M_k\delta_k, \quad k \in \{1, 2, \ldots, n\}.$$
Vedno velja
$$s(\mathcal{D}) \le S(\mathcal{D}),$$
ker je $m \le m_k \le M_k \le M$ za vsak $k$ in zato tudi
$$\sum_{k=1}^{n} m\delta_k \le \sum_{k=1}^{n} m_k\delta_k \le \sum_{k=1}^{n} M_k\delta_k \le \sum_{k=1}^{n} M\delta_k.$$
Torej
$$m(b-a) \le s(\mathcal{D}) \le S(\mathcal{D}) \le M(b-a).$$
$$ $$
>Pravimo da je delitev $D'$ finejša če vsebuje vse delitvene točke $D$ oz. $D \subset D'$


> Naj bo $D \subset D'$. Tedaj je $s(D) \le s(D')$, $S(D') \le S(D)$, tj. pri prehodu na finejšo delitev se spodnja vsota ne zmanjša, zgornja vsota pa se ne poveča.
> 
> >[!|dokaz]- Dokaz:
> > Delitev $D'$ lahko dobimo iz delitve $D$ tako, da dodajamo po eno točko naenkrat. Zato je dovolj dokazati izrek za primer, ko ima $D'$ natanko eno točko več od $D$.
> > 
> > Naj bo $x_i' \in (x_{i-1}, x_i)$ nova delilna točka. Razdelimo $[x_{i-1}, x_i]$ na dva dela, tj. $[x_{i-1}, x_i']$ in $[x_i', x_i]$. Naj bo $m_i' = \inf\{f(x), x \in [x_{i-1}, x_i']\}$, $M_i' = \sup\{f(x), x \in [x_{i-1}, x_i']\}$ in $m_i'' = \inf\{f(x), x \in [x_i', x_i]\}$, $M_i'' = \sup\{f(x), x \in [x_i', x_i]\}$. Na skupnih intervalih delitve $D'$ in $D$ imata vsoti $s(D')$ in $s(D)$ iste člene. Na $i$-tem intervalu ima $s(D)$ člen $m_i \delta_i$, $s(D')$ pa ima dva člena: $m_i'(x_i' - x_{i-1})$ in $m_i''(x_i - x_i')$.
> > 
> > 
> > Ker je $m_i' \ge m_i$ in $m_i'' \ge m_i$, sledi
> > $$m_i'(x_i' - x_{i-1}) + m_i''(x_i - x_i') \ge m_i(x_i' - x_{i-1}) + m_i(x_i - x_i')$$
> > $$= m_i(x_i' - x_{i-1} + x_i - x_i')$$
> > $$= m_i \delta_i.$$
> > Sledi $s(D') \ge s(D)$. Podobno velja za $S(D') \le S(D)$.

>Omejena funkcija $f$ je na $[a,b]$ integrabilna po Darbouxu natanko tedaj, ko za vsak $\varepsilon > 0$ obstaja takšna delitev $D$, da je:
$$|S(D) - s(D)| < \varepsilon.$$
> 
>>[!|dokaz]- Dokaz:
>>
> >
> >($\Rightarrow$) Recimo, da je $f$ integrabilna po Darbouxu. Potem je
> > $$I_1 = I_2 \quad \text{oz.} \quad I := \sup s(D) = \inf S(D).$$
> > Naj bo $\varepsilon > 0$ poljubno majhen. Ker je $I = I_1$, obstaja takšna delitev $D_1$, da je $|s(D_1) - I| < \varepsilon/2$. Ker je $I = I_2$, obstaja takšna delitev $D_2$, da je $|S(D_2) - I| < \varepsilon/2$. Sledi:
> > $$S(D_2) - s(D_1) = |S(D_2) - s(D_1)|$$
> > $$\le |s(D_1) - I| + |I - S(D_2)|$$
> > $$< \frac{\varepsilon}{2} + \frac{\varepsilon}{2} = \varepsilon$$
> > Naj bo $D = D_1 \cup D_2$. Vemo: $s(D_1) \le s(D)$ in $S(D) \le S(D_2)$. Zato je
> > $$S(D) - s(D) \le S(D_2) - s(D_1) < \varepsilon.$$
> > ($\Leftarrow$) Naj za vsak $\varepsilon > 0$ obstaja takšna delitev $D$, da je $|S(D) - s(D)| < \varepsilon$. Ker je $s(D) \le I_1 \le I_2 \le S(D)$, sledi, da za vsak $\varepsilon > 0$ velja $|I_2 - I_1| < \varepsilon$ oz. $I_1 = I_2$. Torej je $f$ integrabilna po Darbouxu. $\square$
> 

>Vsaka na $[a,b]$ zvezna funkcija je integrabilna po Darbouxu
>
>>[!|dokaz]- Dokaz:
>>
> >Naj bo $f$ zvezna na $[a,b]$. Tedaj vemo, da je $f$ na $[a,b]$ enakomerno zvezna in omejena. Naj bo $\epsilon > 0$ poljubno majhen. Ker je $f$ enakomerno zvezna na $[a,b]$, obstaja takšen $\delta > 0$, da je $|f(\tilde{x}) - f(x)| < \epsilon/(b-a)$, čim je $|\tilde{x} - x| < \delta$, $\tilde{x},x \in [a,b]$. Naj bo $D$ delitev, pri kateri je dolžina najdaljšega intervala manjša od $\delta$. Če sta $\tilde{x},x$ na enem od podintervalčkov $[x_{k-1},x_k]$, je $|f(\tilde{x})-f(x)| < \epsilon/(b-a)$ in zato $|M_k-m_k| \le \epsilon/(b-a)$, za vsak $k \in \{1,2,\dots,n\}$.
> > 
> > Ker je $\sum_{k=1}^n \delta_k = b-a$, sledi, da je
> > $$
 \begin{aligned} S(D) - s(D) &= \sum_{k=1}^n M_k\delta_k - \sum_{k=1}^n m_k\delta_k \\ &= \sum_{k=1}^n (M_k - m_k)\delta_k \\ &\le \sum_{k=1}^n \frac{\epsilon}{b-a}\delta_k \\ &= \frac{\epsilon}{b-a}\sum_{k=1}^n \delta_k \\ &= \epsilon. \end{aligned}
> >  $$
> > Po izreku 49 sledi, da je $f$ integrabilna po Darbouxu. $\square$


>Vsaka na $[a,b]$ monotona funkcija je integrabilna po Darbouxu.
>>[!|dokaz]- Dokaz:
> >Naj bo $f$ monotona, npr. naraščajoča na $[a,b]$. Naj bo $D = \{a = x_0 < a_1 < \dots < x_n = b\}$ delitev. Tedaj je $m = f(a)$, $M = f(b)$ in $M_k - m_k \le f(x_k) - f(x_{k-1})$. Zato je
> > $$\begin{aligned} S(D) - s(D) &= \sum_{k=1}^n M_k\delta_k - \sum_{k=1}^n m_k\delta_k \\ &= \sum_{k=1}^n (M_k - m_k)\delta_k \\ &\le \sum_{k=1}^n (f(x_k) - f(x_{k-1}))\delta_k \\ &\le (f(x_1) - f(a) + f(x_2) - f(x_1) + \dots + f(b) - f(x_{n-1}))\delta \\ &= (f(b) - f(a))\delta, \end{aligned}$$
> > 
> > kjer je $\delta$ dolžina najdaljšega intervala. Sklep: Če je dolžina najdaljšega intervala enaka $\delta$, je
> > $$ S(D) - s(D) \le \delta(f(b) - f(a)) = \delta(M - m), $$
> > kar pa je poljubno majhno ob dovolj fini delitvi, tj. ob dovolj majhnem $\delta$. Torej za vsak $\epsilon > 0$ lahko najdemo delitev $D$, da bo $S(D) - s(D) < \epsilon$. Delitev seveda vzamemo tako fino, da je $\delta(M - m) < \epsilon$. To pomeni, da je $f$ integrabilna po Darbouxu. $\square$

