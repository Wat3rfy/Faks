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
Naj velja da $\int_{a}^{\infty}f(x,t)dt$ konvergira točkovno. 

Če velja da $\exists T_{0}$ tak da $\forall  x \in D,\, \forall T : T > T_{0}$ velja $\left|\int_{T}^{\infty} f(t,x)dt\right| <\varepsilon$ potem **enakomerno konvergira**.

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
> > Za vsak $\varepsilon$ obstaja $b$ tako da $\forall c >b$ velja 
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
> **enakomerno** konvergira na $X$ t.j. da za vsak $\varepsilon > 0$ obstaja $c>a$ in $r > 0$ tako da $\forall x,y \in X$ če je $\|x-y\| < r$ potem velja da je $|\int_{c}^{\infty}f(x,t)dt|<\varepsilon$.
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
> **enakomerno konvergira** na $J$.
> 
> Tedaj je $F$ zvezno odvedljiva in
> $$F'(x) = \int_a^\infty \frac{\partial f}{\partial x}(t, x) \, dt.$$
> 
>In velja da je $\int_{a}^{\infty}f(t,x)$ enakomerno konvergentna na $J$.
>
>>[!|dokaz]- Dokaz:
> > 
> > Imamo funkcijo 
> > $$F(x) = \int_{a}^{\infty}f(t,x)dt$$
> > Definirajmo funkcijo $G(x)$, ki predstavlja integral parcialnih odvodov:
> > $$G(x) = \int_a^\infty \frac{\partial f}{\partial x}(t, x) \, dt$$
> > Po predpostavki ta integral konvergira **enakomerno** na intervalu $J$. Ker je $\frac{\partial f}{\partial x}$ zvezna funkcija, je zaradi enakomerne konvergence tudi funkcija $G(x)$ **zvezna** na $J$. *S tem smo pokazali da je $F'$ zvezna funkcija.*
> > 
> > *Hočemo pokazati še da je $F' = G$.*
> > 
> > Vzemimo poljuben končen $b > a$ in definirajmo funkcijo:
> > $$F_b(x) = \int_a^b f(t, x) \, dt.$$
> > $$\text{ po predpostavki velja } \lim_{b \to \infty}F_{b}(x_{0})= F(x_{0})$$
> > Ker integriramo na končnem intervalu $[a, b]$, kjer sta $f$ in $\frac{\partial f}{\partial x}$ zvezni, lahko uporabimo standardno Leibnizovo pravilo za odvajanje pod integralom:
> > $$F_b'(x) = \int_a^b \frac{\partial f}{\partial x}(t, x) \, dt.$$
> > 
> > 
> > Zdaj uporabimo **Osnovni izrek analize** (Newton-Leibnizovo formulo) za funkcijo $F_b(x)$ na intervalu med $x_0$ in poljubnim $x \in J$:
> > $$F_b(x) - F_b(x_0) = \int_{x_0}^x F_b'(u) \, du = \int_{x_0}^x \left( \int_a^b \frac{\partial f}{\partial x}(t, u) \, dt \right) du.$$
> > 
> > Radi bi poslali $b \to \infty$. Poglejmo, kaj se zgodi s posameznimi deli enačbe:
> > 
> >  **Desna stran:** Ker $\int_a^b \frac{\partial f}{\partial x}(t, u) \, dt$ enakomerno konvergira h $G(x) = \int_a^\infty \frac{\partial f}{\partial x}(t, x) \, dt$ na $J$ (*po predpostavki*), smemo zamenjati limito in integral:
> > $$\lim_{b \to \infty} \int_{x_0}^x \left( \int_a^b \frac{\partial f}{\partial x}(t, u) \, dt \right) du = \int_{x_0}^x \left( \lim_{b \to \infty} \int_a^b \frac{\partial f}{\partial x}(t, u) \, dt \right) du = \int_{x_0}^x G(u) \, du$$
> > 
> > Če preoblikujemo originalno enačbo brez limite lahko dobimo
> > 
> > $$F_b(x) = \lim_{b \to \infty}F_b(x_0) + \int_{x_0}^x G_b(u) \, du$$
> > 
> > Ker vemo da je $$\lim_{b \to \infty}F_{b}(x_{0}) = F(x_{0})$$ in $$\lim_{b \to \infty}\int_{x_0}^{x}G_b(u) \, du= \int_{x_0}^x G(u) \, du$$
> > 
> > dobimo
> > $$\lim_{b \to \infty}F_{b}(x) =F(x_0) + \int_{x_0}^{x }G(u) \, du= F(x)$$
> > 
> > Ker $F_b(x)$ konvergira k $F(x)$ za 
> > 
> > Iz te enačbe sledi po osnovnem integralskem izreku sledi
> > 
> > $$F'(x) = \frac{d}{dx} \left( F(x_0) + \int_{x_0}^x G(u) \, du \right) = G(x).$$
> > 
> > S tem smo dokazali, da je:
> > $$F'(x) = \int_a^\infty \frac{\partial f}{\partial x}(t, x) \, dt.$$
> > Ker je desna stran ($G(x)$) zvezna, je $F$ zvezno odvedljiva. *Dokazali da je F odvedljiva in njen odvod je enak $G$.*
> > 
> > Da $F$ enakomerno konvergira izhaja iz 
> > 
> > $$F_b(x) = F_b(x_0) + \int_{x_0}^x G_b(u) \, du$$
> > 
> > $$F(x) = F(x_0) + \int_{x_0}^x G(u) \, du$$
> > 
> > 
> > $$|F(x) - F_b(x)| = \left| \left( F(x_0) + \int_{x_0}^x G(u) \, du \right) - \left( F_b(x_0) + \int_{x_0}^x G_b(u) \, du \right) \right|$$
> > $$|F(x) - F_b(x)| = \left| (F(x_0) - F_b(x_0)) + \int_{x_0}^x (G(u) - G_b(u)) \, du \right|$$
> > 
> > Uporabimo trikotniško neenakost:
> > $$|F(x) - F_b(x)| \leq |F(x_0) - F_b(x_0)| + \left| \int_{x_0}^x |G(u) - G_b(u)| \, du \right|$$
> > Obstaja $B$ da za $b > B$ velja
> > 
> > $$|F(x_0) - F_b(x_0)| <\varepsilon$$
> >     $$|G(u) - G_b(u)| < \varepsilon$$
> > 
> > Vstavimo ti dve oceni v našo neenakost:
> > $$|F(x) - F_b(x)| < \varepsilon + \left| \int_{x_0}^x \varepsilon \, du \right| \leq \varepsilon + \varepsilon \cdot |x - x_0|$$
> > 