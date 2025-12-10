# Integrali s parametrom

> Namesto funckijske vrste vepljemo vsoto čez realna števila neke funkcije preko parametra $r$:
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
> > Ker je $X$ podmnožica metričnega prostora, obstaja kompaktna okolica $K \subset X$ točke $x_0$. Ker je tudi interval $I$ kompakten, je produkt $I \times K$ kompaktna množica. Zvezna funkcija $f$ je na kompaktni množici $I \times K$ **enakomerno zvezna**. Zato obstaja $\delta_1>0$, da za vsak $x \in K$ z $\|x - x_0\| < \delta_1$ velja $|f(t, x) - f(t, x_0)| < \frac{\varepsilon}{2(b-a)}$ za vse $t \in I$.
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
> > Ker je po predpostavki **parcialni odvod $\frac{\partial f}{\partial x}$ zvezen** na $[a, b] \times J$, je na vsaki kompaktni podmnožici oblike $K_\delta =[a, b] \times [x-\delta, x+\delta] \subset [a, b] \times J$ enakomerno zvezen. 
> > 
> > Ker imamo kompaktno množico $K$ velja da lahko za vsak $\varepsilon$ najdemo $\delta_{0}$ tako da za vsak $(t,x)$ in $(t',x')$ v $K_{\delta_{0} }$ velja $|\int_{a}^{b}\frac{\partial f}{\partial x}(x,t)dt -\int_{a}^{b}\frac{\partial f}{\partial x}(x',t')| <\varepsilon$. Torej je **enakomerno zvezna**.
> >  
> > V našem primeru je $x' = \xi_{t,h}$. Ko gre $h \rightarrow 0$ bo zaradi enakomerne zveznosti funkcija $\int_{a}^{b}\frac{\partial f}{\partial x}(\xi_{h,t},t)dt$ enakomerno konvergirala k $\int_{a}^{b}\frac{\partial f}{\partial x}(x,t)dt$.
> > 
> > 
> > Zaradi enakomerne konvergence smemo zamenjati limito in integral:
> > *Izrek analogen menjavi limite pri integralih funkcijskih zaporedij ki enakomerno konvergirajo gl. Analiza 2/Funkcijska zaporedja in vrste*  
> > $$
> > F'(x) = \lim_{h \to 0} \frac{F(x+h) - F(x)}{h} = $$ 
> > $$=\lim_{h \to 0} \int_{a}^{b} \frac{\partial f}{\partial x}(t, \xi_{t,h}) dt = \int_{a}^{b} \lim_{h \to 0} \frac{\partial f}{\partial x}(t, \xi_{t,h}) dt = $$ 
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
**Posplošeni oz. izlimitirani integral**

Integral tipa

$$\lim_{T \to \infty}\int_{a}^{T}f(x,t) dt$$

oz. ekvivalentno zapisano 

$$\int_{a}^{\infty}f(x,t)dt$$

imenujemo izlimitiran integral. Temu pravimo integral po neskončnem intervalu.

Poznamo še integral z **neomejenim integrandom** oz. **polom**. Če ima funkcija $f(x,t)$ pol (je neomejena) v točki $t = a$, potem integral definiramo kot

$$\int_{a}^{b}f(x,t)dt :=\lim_{\varepsilon \to 0^{+}}\int_{a+\varepsilon}^{b}f(x,t)dt$$

Ta pomemben je **izlimtiran integral.** Delali bomo z integrali tipa $\int_{a}^{\infty}$ in analogno sklepali tudi za posplošene integrale drugih tipov. 

***

**Konvergenca integrala**
Naj bo $D$ neka množica. $f: D \times [a,\infty)$. Predpostavimo da je $f$ **integrabilna** $\forall x \in D$ na vsakem $[a,T]$.

Integral $I(x) = \int_{a}^{\infty}f(x,t)dt$ **konvergira točkovno** na intervalu $D$, če za **vsak $x \in D$ obstaja $\lim_{T \to \infty}\int_{a}^{\infty}f(x,t)dt$**.

$$\forall x \in D, \forall \varepsilon > 0, \exists T_{0} \ni: \forall T > T_{0} : \left|\int_{T}^{\infty} f(t,x)dt \right| < \varepsilon$$
$$ \color{light} \text{ekvivalentno:}\; ...  \forall T>T_{0}:\left| \int_{a}^{T}f(x,t)dt - \int_{a}^{\infty}f(x,t)dt \right| <\varepsilon$$

**$T_{0}$ je odvisna od $x$.**

***
Naj velja da $\int_{a}^{\infty}f(x,t)dt$ konvergira točkovno. Če velja da obstaja $T_{0}$ tak da $\forall  x \in D,\, \forall T : T > T_{0}$ velja $\left|\int_{T}^{\infty} f(t,x)dt\right| <\varepsilon$ potem **enakomerno konvergira**.

$$\forall \varepsilon > 0, \forall x \in D, \forall T \ni:  T>T_{0} : \left|\int_{T}^{\infty} f(x,t)dt \right|$$

**$T_{0}$ ni odvisna od $x$.**
***
> **Weierstrassov $M$-test za integrale**
> Naj bo $f : [a,\infty) \times X \rightarrow \mathbb{R}$.
> Naj bo za vsak $x \in X$ funkcija $t \mapsto f(t,x)$ **integrabilna** na $[a, \infty)$. 
> Naj obstaja taka integrabilna funkcija $\varphi:[a,\infty) \rightarrow \mathbb{R}^{+}$, da velja:
> 
> 1.  $|f(t,x)| \leq \varphi(t)$ za vse $t \in [a, \infty)$ in za vse $x \in X$.
> 2.  Posplošeni integral $\int_{a}^{\infty}\varphi(t)dt$ konvergira.
> 
> Potem integral $\int_{a}^{\infty}f(t,x)dt$ **konvergira enakomerno** na množici $X$.
> 
> >[!|dokaz]- Dokaz:
> > Izberimo poljuben $\epsilon > 0$.
> > 
> > Uporabimo predpostavko, da integral **$\int_{a}^{\infty}\varphi(t)dt$ konvergira**. 
> > Obstaja $b$ tako da $\forall c >b$ velja 
> > $$\left|\int_{c}^{\infty} \varphi(t)dt  \right| <\varepsilon$$
> > 
> > Sedaj lahko izpeljemo
> > 
> > $$\left|\int_{c}^{\infty} f(x,t)dt\right| \leq \int_{c }^{\infty}\left|f(x,t) \right|dt \leq \int_{c}^{\infty}\varphi(t)dt < \varepsilon$$
> > 
> > Ker je bil naš $b$ odvisen le od $\epsilon$ in ne od $x$, in ker ocena velja za *vse* $x \in X$, integral $\int_{a}^{\infty}f(t,x)dt$ konvergira enakomerno na $X$.

> **Zveznost posplošenega integrala s parametrom**
> Naj bo $X \subset \mathbb{R}^{n}$.
> Naj bo $f: [a,\infty) \times X \rightarrow \mathbb{R}$ **zvezna** funkcija in naj 
> $$\int_{a}^{\infty}f(t,x)dt$$
> **lokalno enakomerno** konvergira na $X$ t.j. da za vsak $\varepsilon > 0$ obstaja $c>a$ in $r > 0$ tako da $\forall x,y \in X$ če je $\|x-y\| < r$ potem velja da je $|\int_{c}^{\infty}f(x,t)dt|<\varepsilon$.
>
>Potem je
>$$x \mapsto \int_{a}^{\infty}f(t,x)dt$$
>zvezna funkcija. 
>*Lokalna enakomerna konvergenca namesto da obstaja $c$ za vsak $x$, obstaja $c$ za vsako dovolj majhno okolico. Torej za vsako točko obstaja dovolj majhna okolica kjer enakomerno konvergira.*
>>[!|dokaz]- Dokaz:
> > 
> > Naj bo $x_0 \in X$ poljubna točka. 
> > 
> > $$F(x) = \int_{a}^{\infty}f(t,x)dt$$
> > 
> > *Hočemo pokazati da za vsak $\varepsilon > 0$ obstaja okolica $x_{0}$ da če je $x$ v tej okolici potem velja $|F(x) - F(x_0)| < \varepsilon$*
> > 
> > Vzemimo poljuben $\varepsilon > 0$. Dokaz razdelimo na tri korake z uporab $\varepsilon/3$.
> > 
> > 
> > Uporabimo predpostavko **lokalne enakomerne konvergence**.
> > 
> > Za izbrani $x_0$ in za $\varepsilon_{0} = \varepsilon/3$, lok. enak. kon. zagotavlja, da obstaja okolica $U(x_0) \subset X$ točke $x_0$ in obstaja realno število $c > a$ takšno, da za vsak $x \in U(x_0)$ velja:
> > 
> > $$ \left| \int_{c}^{\infty} f(t, x) dt \right| < \frac{\varepsilon}{3}$$
> > 
> > Ker $x_0$ pripada $U(x_0)$, mora tudi veljati:
> > 
> > $$ \left| \int_{c}^{\infty} f(t, x_0) dt \right| < \frac{\varepsilon}{3}$$
> > 
> > Ocenimo razliko integralov.
> > 
> > Razliko $|F(x) - F(x_0)|$ razdelimo na končni del (od $a$ do $c$) in rep (od $c$ do $\infty$):
> > 
> > $$|F(x) - F(x_0)| = $$ 
> > $$\left| \left( \int_{a}^{c} f(t, x) dt + \int_{c}^{\infty} f(t, x) dt \right) - \left( \int_{a}^{c} f(t, x_0) dt + \int_{c}^{\infty} f(t, x_0) dt \right) \right|$$
> > 
> > Po trikotni neenakosti dobimo:
> > 
> > $$|F(x) - F(x_0)| \leq $$ 
> > $$\underbrace{\left| \int_{a}^{c} [f(t, x) - f(t, x_0)] dt \right|}_{\text{I}} + \underbrace{\left| \int_{c}^{\infty} f(t, x) dt \right|}_{\text{II}} + \underbrace{\left| \int_{c}^{\infty} f(t, x_0) dt \right|}_{\text{III}}$$
> > 
> > Obravnavamo repa $\text{II}, \text{III}$
> > 
> > Za vsak $x \in U(x_0)$ smo že na začetku ugotovili, da sta člena II in III ustrezno majhna z izbiro $c$:
> > 
> > $$ \text{II} < \frac{\varepsilon}{3} \quad \text{in} \quad \text{III} < \frac{\varepsilon}{3} $$
> > 
> > Obravnavamo končni del $\text{I}$
> > 
> > Definirajmo funkcijo $G(x)$ kot integral na končnem intervalu:
> > $$G(x) = \int_{a}^{c} f(t, x) dt$$
> > 
> > Uporabimo **Izrek o zveznosti integralov s parametrom na končnem intervalu**.
> > Ker je **integrand $f(t, x)$ zvezna funkcija** na kompaktnem območju $[a, c] \times U(x_0)$, sledi, da je funkcija $G(x)$ zvezna na $U(x_0)$.
> > 
> > Iz zveznosti sledi da obstaja okolica $x_{0}$ recimo $V(x_{0})\subset U(x_{0})$ tako da če je $x \in V(x_{0})$ potem je 
> > 
> > $$|G(x) - G(x_0)| = \left| \int_{a}^{c} [f(t, x) - f(t, x_0)] dt \right| < \frac{\varepsilon}{3}$$
> > $$ \text{I} < \frac{\varepsilon}{3} $$
> > 
> > Če združimo vse skupaj lahko izberemo $x \in V(x_{0})$.
> > 
> > Ker je $V(x_{0})\subset U(x_{0})$ veljajo vse ocene hkrati.
> > $$|F(x) - F(x_0)| \leq \text{I} + \text{II} + \text{III} < \frac{\varepsilon}{3} + \frac{\varepsilon}{3} + \frac{\varepsilon}{3} = \varepsilon$$
> > 
> > Ker smo dokazali, da za poljuben $\varepsilon > 0$ obstaja okolica $V(x_0)$ takšna, da je $|F(x) - F(x_0)| < \varepsilon$, je funkcija $F(x)$ zvezna v točki $x_0$. Ker je bila $x_0$ poljubna, je $F(x)$ zvezna na celotnem $X$.
> > 
> > 
> > | Predpostavka/Izrek | Kje se uporabi v dokazu? | Zakaj je potrebna? |
> > | :--- | :--- | :--- |
> > | **Premisa 1: Zveznost integranda $f(t, x)$** | Korak 3 (Obravnava I) | Da lahko uporabimo klasični **Izrek o zveznosti integralov na končnem intervalu**. Brez zveznosti $f$ ne moremo zagotoviti zveznosti $G_C(x)$. |
> > | **Premisa 2: Lokalna Enakomerna Konvergenca (LEK)** | Korak 1 in Korak 3 (Obravnava II in III) | Omogoča izbiro fiksne meje $C$ in okolice $U(x_0)$, tako da so repi integrala $|\int_C^\infty f(t, x) dt|$ majhni in omejeni, **neodvisno od $x$** znotraj te okolice. To je ključni prehod iz neskončnega na končni interval. |
> > | **Izrek o zveznosti integralov na končnem intervalu** | Korak 3 (Obravnava I) | Zagotavlja, da je funkcija $G_C(x) = \int_a^C f(t, x) dt$ zvezna, saj je njen integrand zvezna funkcija na kompaktnem območju. To nam omogoča, da najdemo okolico $V(x_0)$, kjer je tudi končni del razlike majhen. |
> > | **Trikotna neenakost** | Korak 2 | Za razdelitev celotne razlike v tri obvladljive dele. |


> **Integriranje izlimitiranega integrala**
> Naj bo $f:[c,d] \times [a,\infty)$ zvezna funkcija.
> Naj bo
> $$F(x) = \int_{a}^{\infty}f(x,t)dt$$
> enakomerno konvergentna na $[c,d]$ *$\Rightarrow$ F je zvezna.*
>Potem velja
>$$\int_{a}^{\infty}dt\int_{c}^{d}f(x,t)dx = \int_{c}^{d}dx \int_{a}^{\infty}f(x,t)dt$$
> >[!|dokaz]- Dokaz:
> >
> > 
> > Za dokaz izreka hočemo priti na izrek o integriranju integralov s parametrom *Funibijev izrek*.
> > 
> > ker je $f$ zvezna na $[c,d] \times [a,b]$ lahko po Funibijevem izreku zamenjamo vrstni red.
> > 
> > $$\int_{c}^{d}dx \int_{a}^{b}f(x,t)dt = \int_{a}^{b}dt \int_{c}^{d}f(x,t)dx$$
> > 
> > Vzamemo limito $b \rightarrow \infty$ na obeh straneh.
> > 
> > $$L: \lim_{b \to \infty} \int_{c}^{d}dx \int_{a}^{b}f(x,t)dt$$
> > $$D: \lim_{b \to \infty}\int_{a}^{b}dt \int_{c}^{d}f(x,t)dx$$
> > 
> > Ker je $f$ zvezna in enakomerno konvergira na $[c,d]$ lahko limito prenesemo v integral in dobimo
> > 
> > $$L:\int_{c}^{d}dx \lim_{b \to \infty}\int_{a}^{b}f(x,t)dt$$
> > $$L:\int_{c}^{d}dx \int_{a}^{\infty}f(x,t)dt$$
> > 
> > Kar pomeni da je
> > 
> > $L = D$.



>**Izrek o odvedljivost zlimitiranega integrala**
> Naj bo $J$ **odprt interval** in $f : [a, \infty) \times J \to \mathbb{R}$ **zvezna funkcija**. 
> Naj bo $f$ **zvezno parcialno odvedljiva** na $J\;\, \forall t \in [a, \infty) \times J$. 
> Naj za nek $x_{0} \in J$ integral
> $$F(x_{0}) = \int_a^\infty f(t, x_{0}) \, dt$$
> konvergira in naj integral iz odvodov
> $$\int_a^\infty \frac{\partial f}{\partial x}(t, x) \, dt$$
> enakomerno konvergira na $J$.
> 
> Tedaj je $F$ zvezno odvedljiva in
> $$F'(x) = \int_a^\infty \frac{\partial f}{\partial x}(t, x) \, dt.$$
> 
>In velja da je $\int_{a}^{\infty}f(t,x)$ enakomerno konvergentna na $J$.





