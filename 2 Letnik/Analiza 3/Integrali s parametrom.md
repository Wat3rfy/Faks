# Integrali s parametrom

> Namesto funckijske vrste vpeljemo vsoto čez realna števila neke funkcije preko parametra $r$:
> $$\int_{a}^{b}f(x,t)dt$$
> Velja da lahko zgornjo funkcijo zapišemo kot
> $$G(a,b,x) = \int_{a}^{b}f(x,t)dt$$

>[!|hide]- Podrobno
> Če imamo funkcijsko zaporedje $f_{n}$ si ga lahko predstavljamo kot funkcijo $g(x,n)$, kjer je za vsak $n \in \mathbb{N}$ neka druga funkcija - torej funkcijsko zaporedje. 
> 
> Predstava: https://www.math3d.org/kMoS6mej9a
> 
> Sedaj naredimo iz tega funkcijsko vrsto ampak hočemo seštevati ne samo čez naravna števila - torej kako se spremnija za vsak $n \in \mathbb{N}$ ampak za vsa realna števila $n \in \mathbb{R}$.
> 
> Z operatorjem vsote to ne gre več ampak poznamo operator za seštevanje funkcijskih vrednosti od ene meje do druge kar je integral.
> 
> Pomembno je da vemo da kot pri funkcijskih vrstah predpotavljamo da je $x$ pritrjen oz. deluje kot konstanta - mi ne gledamo kako se spremnija vrednost funkcijse po $x$ ampaka kako se funkcija spreminja glede na $n \in \mathbb{R}$.
> 
> Da bo jasneje pišimo $t := n \in \mathbb{R}$
> 
> Če hočemo sedaj sešteti vse funkcije glede na $t$ kot neko vsoto $f_{t}$ vpeljemo funkcijo $g(x,t) = f_{t}(x)$, kjer lahko uporabimo integral kot operator vsote in dobimo
> 
> $$\int_{a}^{b}g(x,t)dt$$
> 
> kjer je ključno da vemo da integriramo po $t$, meje za seštevanje pa so podane z $a,b$. $x$ pa se kot pri vrstah obravnava kot konstanta oz. kot da je pritrjen.
> 
> Tehnično gledano lahko za to vpeljemo še funkcijo
> 
> $$G(a,b,t) = \int_{a}^{b}g(x,t)dt$$
> 
> ker lahko spreminjamo meji integrala.

***

>**Izrek o zveznosti integrala s parametrom**
>1. Naj bo **$I = [a,b]$** in **$X \subset \mathbb{R}^n$ **. 
>2. Naj bo **$f: I \times X \to \mathbb{R}$ zvezna funkcija**. 
>
>Potem je funkcija $G: X \times I \times I \to \mathbb{R}$, definirana s formulo
$$G(x,u,w) = \int_u^w f(t,x)dt$$
zvezna.
>*Kjer je $x$ lahko spremenljivka v $\mathbb{R}^n$*
>>[!|dokaz]- Dokaz:
> > Naj bo $(x_0, u_0, w_0) \in X \times I \times I$ poljubna točka in naj bo $\varepsilon>0$.
> >
> > Ker je $X$ podmnožica metričnega prostora, obstaja kompaktna okolica $K \subset X$ točke $x_0$. Ker je tudi interval $I$ kompakten, je produkt $I \times K$ kompaktna množica. Zvezna funkcija $f$ je na kompaktni množici $I \times K$ **enakomerno zvezna**. Zato pri fiksnem $t$ za vsak $\varepsilon$ obstaja $\delta_1>0$, da za vsak $x \in K$ z $\|x - x_0\| < \delta_1$ velja $|f(t, x) - f(t, x_0)| < \frac{\varepsilon}{2(b-a)}$ za vse $t \in I$.
> >
> > Razliko ocenimo z uporabo trikotniške neenakosti:
> > $$|G(x, u, w) - G(x_0, u_0, w_0)| = \left|\int_{u}^{w} f(t, x) d t - \int_{u_0}^{w_0} f(t, x_0) d t\right|$$
> > $$= \left|\int_{u}^{w} f(t, x) d t - \int_{u}^{w} f(t, x_0) d t + \int_{u}^{w} f(t, x_0) d t - \int_{u_0}^{w_0} f(t, x_0) d t\right|$$
> > $$\leq \left|\int_{u}^{w} (f(t, x) - f(t, x_0)) d t\right| + \left|\int_{u}^{w} f(t, x_0) d t - \int_{u_0}^{w_0} f(t, x_0) d t\right|$$
> > $$ \leq \int_{\min(u,w)}^{\max(u,w)} |f(t, x) - f(t, x_0)| d t + \left|\int_{u_0}^{u} f(t, x_0) d t + \int_{w_0}^{w} f(t, x_0) d t\right|$$
> >
> > Za $x \in K$ z $\|x - x_0\| < \delta_1$ je prvi člen manjši od:
> > $$\int_{\min(u,w)}^{\max(u,w)} \frac{\varepsilon}{2(b-a)} dt = \frac{\varepsilon}{2(b-a)}|w-u| \leq \frac{\varepsilon}{2(b-a)}(b-a) = \frac{\varepsilon}{2}.$$
> >
> > Funkcija $t \mapsto f(t, x_0)$ je zvezna na kompaktnem intervalu $I$, zato je omejena. Obstaja $M>0$, da je $|f(t, x_0)| \leq M$ za vse $t \in I$. Drugi člen lahko zato ocenimo z:
> > $$ \left|\int_{u_0}^{u} f(t, x_0) d t\right| + \left|\int_{w_0}^{w} f(t, x_0) d t\right| \leq M|u-u_0| + M|w-w_0|. $$
> > Izberimo $\delta_2 = \frac{\varepsilon}{4M}$ (če je $M>0$). Za $|u-u_0| < \delta_2$ in $|w-w_0| < \delta_2$ je ta izraz manjši od $M\delta_2 + M\delta_2 = \varepsilon/2$. Če je $M=0$, je izraz enak 0 in pogoj trivialno izpolnjen.
> >
> > Izberimo $\delta = \min(\delta_1, \delta_2)$ (in $\delta$ mora biti dovolj majhen, da je $x \in K$). Potem za vse $(x, u, w)$, ki zadoščajo $\|x-x_0\|<\delta$, $|u-u_0|<\delta$ in $|w-w_0|<\delta$, velja:
> > $$|G(x,u,w) - G(x_0,u_0,w_0)| < \frac{\varepsilon}{2} + \frac{\varepsilon}{2} = \varepsilon.$$
> > Torej je $G$ zvezna funkcija.


> **Posledica**
> Naj bo $X \subset \mathbb{R}^n$ in $f : [a, b] \times X \to \mathbb{R}$
> zvezna. 
> 
> Tedaj je $F$, dana s predpisom
> $$
> F(x) = \int_a^b f(t, x) dt,
> $$
> zvezna funkcija na $X$.


***


> **Izrek o zveznosti integrala s parametrom s spremenljivimi mejami**
> 1. Naj bo $J = [c, d]$ zaprt interval in $X \subset \mathbb{R}^n$.
> 2. Naj bo $f: J \times X \to \mathbb{R}$ **zvezna funkcija**.
> 3. Naj bosta $a, b: X \to J$ **zvezni funkciji** (meji integrala).
> 
> Potem je funkcija $F: X \to \mathbb{R}$, definirana s formulo
> $$F(x) = \int_{a(x)}^{b(x)} f(t,x)dt$$
> zvezna na $X$.
> 
> 
> > [!|dokaz]- **Dokaz:**
> > Naj bo $x_0 \in X$ poljubna točka in naj bo $\varepsilon > 0$. Dokazati želimo, da obstaja tak $\delta > 0$, da iz $\|x - x_0\| < \delta$ sledi $|F(x) - F(x_0)| < \varepsilon$.
> >
> > Ker je $X$ podmnožica $\mathbb{R}^n$, obstaja kompaktna okolica $K \subset X$ točke $x_0$. Ker je tudi interval $J$ kompakten, je produkt $J \times K$ kompakten. Zvezna funkcija $f$ je na kompaktni množici $J \times K$ **enakomerno zvezna**. Zato za vsak $\varepsilon' > 0$ obstaja $\delta_1 > 0$, da za vse $x \in K$ z $\|x - x_0\| < \delta_1$ velja $|f(t, x) - f(t, x_0)| < \varepsilon'$ za vse $t \in J$.
> >
> > Razliko zapišemo in razbijemo na tri dele:
> > 
> > $$F(x) - F(x_0) = \int_{a(x)}^{b(x)} f(t, x) dt - \int_{a(x_0)}^{b(x_0)} f(t, x_0) dt$$
> > 
> > $$= \left( \int_{a(x)}^{b(x)} f(t, x) dt - \int_{a(x)}^{b(x)} f(t, x_0) dt \right) + \int_{a(x)}^{b(x)} f(t, x_0) dt - \int_{a(x_0)}^{b(x_0)} f(t, x_0) dt$$
> > 
> > $$= \int_{a(x)}^{b(x)} (f(t, x) - f(t, x_0)) dt + \left( \int_{a(x)}^{a(x_0)} f(t, x_0) dt + \int_{a(x_0)}^{b(x_0)} f(t, x_0) dt + \int_{b(x_0)}^{b(x)} f(t, x_0) dt \right) - \int_{a(x_0)}^{b(x_0)} f(t, x_0) dt$$
> > 
> > $$= \underbrace{\int_{a(x)}^{b(x)} (f(t, x) - f(t, x_0)) dt}_{A} + \underbrace{\int_{b(x_0)}^{b(x)} f(t, x_0) dt}_{B} + \underbrace{\int_{a(x)}^{a(x_0)} f(t, x_0) dt}_{C}$$
> >
> > Ocenimo vsak člen posebej z uporabo trikotniške neenakosti: $|F(x) - F(x_0)| \leq |A| + |B| + |C|$.
> >
> > Izberimo $\varepsilon' = \frac{\varepsilon}{3(d-c)}$. Če je $\|x-x_0\| < \delta_1$, potem je:
> > $$|A| \leq \int_{\min(a(x),b(x))}^{\max(a(x),b(x))} |f(t, x) - f(t, x_0)| dt \leq \varepsilon' \cdot |b(x) - a(x)| \leq \frac{\varepsilon}{3(d-c)}(d-c) = \frac{\varepsilon}{3}.$$
> >
> > Funkcija $t \mapsto f(t, x_0)$ je zvezna na $J$, zato je omejena: obstaja $M > 0$, da je $|f(t, x_0)| \leq M$ za vse $t \in J$.
> > Ker sta funkciji $a(x)$ in $b(x)$ zvezni v $x_0$, za vsak $\eta > 0$ obstajata $\delta_2, \delta_3 > 0$, da:
> > - če $\|x-x_0\| < \delta_2$, potem $|b(x) - b(x_0)| < \eta$,
> > - če $\|x-x_0\| < \delta_3$, potem $|a(x) - a(x_0)| < \eta$.
> >
> > Potem je:
> > $$|B| \leq \left| \int_{b(x_0)}^{b(x)} M dt \right| = M |b(x) - b(x_0)| < M \eta$$
> > $$|C| \leq \left| \int_{a(x)}^{a(x_0)} M dt \right| = M |a(x_0) - a(x)| < M \eta$$
> >
> > Izberemo $\eta = \frac{\varepsilon}{3M}$ (če je $M>0$, sicer sta člena 0).
> >
> > Izberemo $\delta = \min(\delta_1, \delta_2, \delta_3)$ (in pazimo, da je okolica znotraj $K$). Za vse $x$, kjer $\|x - x_0\| < \delta$, velja:
> > $$|F(x) - F(x_0)| < \frac{\varepsilon}{3} + \frac{\varepsilon}{3} + \frac{\varepsilon}{3} = \varepsilon.$$
> > S tem je dokazano, da je $F$ zvezna v $x_0$. Ker je bil $x_0$ poljuben, je $F$ zvezna na $X$.


***

> **Izrek o odvajanju integrala s parametrom** 
> 
> Naj bo **$J \subset \mathbb{R}$ odprt interval** in $f : [a, b] \times J \to \mathbb{R}$ **zvezna funkcija**. 
> 
> Naj za vsak $(t, x) \in [a, b] \times J$ obstaja $\frac{\partial f}{\partial x}(t, x)$ in naj bo **$\frac{\partial f}{\partial x}(t,x)$ zvezna funkcija** na $[a, b] \times J$. Tedaj velja
> ***
>**1\.** Funkcija $F$, dana s predpisom
> $$
> F(x) = \int_a^b f(t, x) dt,
> $$
> je zvezno odvedljiva na $J$ in velja
> $$
> F'(x) = \int_a^b \frac{\partial f}{\partial x}(t, x) dt,
> $$
> za $x \in J$.
> ***
> **2\.** Za poljubni **zvezno odvedljivi** funkciji $\alpha, \beta : J \to [a, b]$ je funkcija $G$
> $$
> G(x) = \int_{\alpha(x)}^{\beta(x)} f(t, x) dt,
> $$
> zvezno odvedljiva na $J$ in velja
> $$
> G'(x) = f(\beta(x), x) \beta'(x) - f(\alpha(x), x) \alpha'(x) + \int_{\alpha(x)}^{\beta(x)} \frac{\partial f}{\partial x}(t, x) dt.
> $$
> >[!|dokaz]- Dokaz:
> > Dokažimo najprej prvo trditev. Izberimo poljuben $x \in J$ in tak $h \in \mathbb{R}$, da je tudi $x+h \in J$. Zapišimo diferenčno količino za funkcijo $F$:
> > $$
> > \frac{F(x+h) - F(x)}{h} = \int_a^b \frac{f(t, x+h) - f(t, x)}{h} dt.
> > $$
> > Po predpostavki za vsak $t \in [a, b]$ obstaja parcialni odvod funkcije $f$ na drugo spremenljivko. 
> > Po Lagrangeovem izreku o srednji vrednosti za funkcijo $y \mapsto f(t, y)$ na intervalu med $x$ in $x+h$ obstaja število $\xi_{t,h}$, odvisno od $t$ in $h$, tako da $\xi_{t,h}$ leži med $x$ in $x+h$, in velja:
> > $$
> > f(t, x+h) - f(t, x) = h \cdot \frac{\partial f}{\partial x}(t, \xi_{t,h}).
> > $$
> > Izraz za diferenčno količino se tako preoblikuje v:
> > $$
> > \frac{F(x+h) - F(x)}{h} = \int_a^b \frac{\partial f}{\partial x}(t, \xi_{t,h}) dt.
> > $$
> > Ker je po predpostavki **parcialni odvod $\frac{\partial f}{\partial x}$ zvezen** in velja da če prilagodimo limito $\lim_{h \to 0} \rightarrow \lim_{\xi \to x}$ bo veljalo po izreku o zveznosti integrala s parametrom da je funkcija $y \mapsto \int_a^b \frac{\partial f}{\partial x}(t, \xi_{t,h}) dt$ zvezna in lahko vstavimo limito v intergal.
> > 
> > $$
> > F'(x) = \lim_{h \to 0} \frac{F(x+h) - F(x)}{h} = $$ 
> > $$=\lim_{\xi_{t,h} \to x} \int_{a}^{b} \frac{\partial f}{\partial x}(t, \xi_{t,h}) dt = \int_{a}^{b} \lim_{\xi_{t,h} \to x} \frac{\partial f}{\partial x}(t, \xi_{t,h}) dt = $$ 
> > $$= \int_a^b \frac{\partial f}{\partial x}(t, x) dt.
> > $$
> > Zveznost odvoda $F'$ sledi neposredno iz zveznosti parcialnega odvoda $\frac{\partial f}{\partial x}$ in lastnosti integrala.
> > 
> > Za dokaz **druge trditve** definirajmo pomožno funkcijo $H(x, y, z) = \int_y^z f(t, x) dt$, kjer je $x \in J$ in $y, z \in [a, b]$. Funkcija $G$ je tedaj kompozicija $G(x) = H(x, \alpha(x), \beta(x))$. Po totalnem odvodu je:
> > $$
> > G'(x) = \frac{\partial H}{\partial x}(x, \alpha(x), \beta(x)) + \frac{\partial H}{\partial y}(x, \alpha(x), \beta(x)) \alpha'(x) + \frac{\partial H}{\partial z}(x, \alpha(x), \beta(x)) \beta'(x).
> > $$
> > Parcialne odvode funkcije $H$ izračunamo:
> > *   Po pravkar dokazani prvi točki izreka je $\frac{\partial H}{\partial x}(x, y, z) = \int_y^z \frac{\partial f}{\partial x}(t, x) dt$.
> > *   Po osnovnem izreku integralskega računa, za katerega je ključna **zveznost funkcije $f$**, velja $\frac{\partial H}{\partial z}(x, y, z) = f(z, x)$ in $\frac{\partial H}{\partial y}(x, y, z) = -f(y, x)$.
> > 
> > Uporaba zgornjih izrazov v formuli za totalni odvod, kjer upoštevamo predpostavko o **zvezni odvedljivosti** funkcij $\alpha$ in $\beta$, nam da končni rezultat:
> > $$
> > G'(x) = f(\beta(x), x) \beta'(x) - f(\alpha(x), x) \alpha'(x) + \int_{\alpha(x)}^{\beta(x)} \frac{\partial f}{\partial x}(t, x) dt.
> > $$

>[!|hide]-  **Posledica** 
>Naj bo $G \subset \mathbb{R}^n$ odprta in $f : [a, b] \times G \to \mathbb{R}$ funkcija. Naj za vsak $(t, x) \in [a, b] \times G$ obstajajo
> $$
> \frac{\partial f}{\partial x_j}(t, x), \quad j \in \{1, 2, \dots, n\},
> $$
> ki naj bodo zvezne funkcije na $[a, b] \times G$. Tedaj je funkcija $F$ dana s predpisom
> $$
> F(x) = \int_{a}^{b} f(t, x) dt
> $$
> razreda $C^1$ na $G$ in velja
> $$
> \frac{\partial F}{\partial x_j}(x) = \int_{a}^{b} \frac{\partial f}{\partial x_j}(t, x) dt, \quad j \in \{1, 2, \dots, n\}.
> $$


**Izrek o integraciji integrala s parametrom**
Naj bo $f$ zvezna funkcija na $[a, b] \times [c, d]$ in $F(x) = \int_{a}^{b} f(t, x) dt$. *Vemo že, da je $F : [c, d] \to \mathbb{R}$ zvezna*

Tedaj velja
$$
\int_{c}^{d}  \left(\int_{a}^{b} f(t, x) dt\right) dx = \int_{a}^{b} \left(\int_{c}^{d} f(t, x) dx\right) dt,
$$
oziroma lahko zapišemo tudi kot
$$
\int_{c}^{d} dx \int_{a}^{b} f(t, x) dt = \int_{a}^{b} dt \int_{c}^{d} f(t, x) dx.
$$


*Pripomnimo še, da integrala*

$$\color{light}\int_{c}^{d} \left(\int_{a}^{b} f(t, x) dt\right) dx = \int_{c}^{d} dx \int_{a}^{b} f(t, x) dt$$

*in*
$$\color{light}
\int_{a}^{b} \left(\int_{c}^{d} f(t, x) dx\right) dt = \int_{a}^{b} dt \int_{c}^{d} f(t, x) dx
$$
*imenujemo dvakratna integrala (in ne dvojna integrala). Izrek torej reče, da sta oba dvakratna integrala enaka.*
>[!|dokaz]- Dokaz:
> 
> Naj bo $f: [a, b] \times [c, d] \to \mathbb{R}$ zvezna funkcija. Želimo dokazati, da je
> $$
> I_1 = \int_{c}^{d} \left( \int_{a}^{b} f(t, x) dt \right) dx = \int_{a}^{b} \left( \int_{c}^{d} f(t, x) dx \right) dt = I_2.
> $$
> 
> Dokaz bomo izvedli tako, da definiramo pomožni funkciji, ki predstavljata oba dvakratna integrala, vendar z zgornjo mejo $y$ namesto $d$. Nato bomo pokazali, da imata ti funkciji enake odvode in enako vrednost v začetni točki, kar pomeni, da sta enaki povsod.
> 
> 
> Definirajmo dve funkciji $J: [c, d] \to \mathbb{R}$ in $K: [c, d] \to \mathbb{R}$:
> 
> $J({\color{green}y}) = \int_{c}^{{\color{green}y}} \left( \int_{a}^{b} f(t, x) dt \right) dx$
>  $K({\color{green}y}) = \int_{a}^{b} \left( \int_{c}^{{\color{green}y}} f(t, x) dx \right) dt$
> 
> Naš cilj je dokazati, da je $J(y) = K(y)$ za vsak $y \in [c, d]$. Ker je $I_1 = J(d)$ in $I_2 = K(d)$, bo enakost dokazana.
> 
> **Odvod funkcije $J(y)$**
> 
> Funkcija $F(x) = \int_{a}^{b} f(t, x) dt$ je zvezna funkcija spremenljivke $x$. S pomočjo **osnovnega integralsekga izreka** dobimo:
> $$
> J'(y) = \frac{d}{dy} \left[ \int_{c}^{y} F(x) dx \right] = F(y) = \int_{a}^{b} f(t, y) dt.
> $$
> 
> *Po izreku ki pravi*
> 
> $$\color{light}G(x) = \int_{a}^{x}f(t)dt \Rightarrow G'(x) = f(x)$$
> 
> **Odvod funkcije $K(y)$**
> 
> Za odvod funkcije $K(y)$ uporabimo izrek o **diferenciranju pod integralskim znakom** *Prejšnji dokaz o odvedljivost integrala s parametrom*, ki se v tem primeru uporablja, ker je $f(t, x)$ zvezna funkcija in so parcialni odvodi zvezni (v tem koraku potrebujemo samo zveznost funkcije $f$).
> 
> $$
> K'(y) = \frac{d}{dy} \left[ \int_{a}^{b} \left( \int_{c}^{y} f(t, x) dx \right) dt \right]
> $$
> $$
> K'(y) = \frac{d}{dy} \left[ \int_{a}^{b} G(y,t)dt \right]
> $$
> 
> Ker so funkcije lepo zvezne, lahko zamenjamo vrstni red odvoda in zunanjega integrala:
> $$
> K'(y) = \int_{a}^{b} \left( \frac{\partial}{\partial y} \left[ \int_{c}^{y} f(t, x) dx \right] \right) dt
> $$
> Sedaj uporabimo **Osnovni izrek integralskega računa** na notranjem delu:
> $$
> \frac{\partial}{\partial y} \left[ \int_{c}^{y} f(t, x) dx \right] = f(t, y).
> $$
> To velja, ker integriramo glede na $x$ in odvajamo glede na zgornjo mejo $y$.
> 
> Vstavimo to nazaj v izraz za $K'(y)$:
> $$
> K'(y) = \int_{a}^{b} f(t, y) dt.
> $$
> 
> 
> 
> Ugotovili smo, da velja:
> $$
> J'(y) = \int_{a}^{b} f(t, y) dt \quad \text{in} \quad K'(y) = \int_{a}^{b} f(t, y) dt.
> $$
> Torej, $J'(y) = K'(y)$ za vsak $y \in [c, d]$.
> 
> Po posledici OII (če imata dve zvezno odvedljivi funkciji enak odvod na intervalu, se razlikujeta za konstanto) velja:
> $$
> J(y) - K(y) = C.
> $$
> 
> Preverimo še začetno točko $y=c$:
> $$
> J(c) = \int_{c}^{c} \left( \dots \right) dx = 0.
> $$
> $$
> K(c) = \int_{a}^{b} \left( \int_{c}^{c} f(t, x) dx \right) dt = \int_{a}^{b} 0 dt = 0.
> $$
> Ker $J(c) = K(c) = 0$, je konstanta $C = 0$.
> 
> Sledi, da je $J(y) = K(y)$ za vse $y \in [c, d]$. Z nastavitvijo $y=d$ dobimo:
> $$
> I_1 = J(d) = K(d) = I_2.
> $$
> S tem je izrek dokazan.


***
