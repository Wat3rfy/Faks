
# Greenov izrek

Zgornjo formulo moramo dokazati. Ena pot do neposrednega dokaza je preko Greenove formule.

Greenova formula pravi: Naj bo $(x, y) \longmapsto (P(x, y), Q(x, y))$ preslikava iz $D \subset \mathbb{R}^2 \longrightarrow \mathbb{R}^2$ (oz. vektorsko polje) in $\gamma(t) = (x(t), y(t)) : [\alpha, \beta] \longrightarrow \mathbb{R}^2$ pot, ki parametrizira rob $\partial D$. Potem:
$$\int_{\partial D} P \, dx + Q \, dy = \iint_D \left( \frac{\partial Q}{\partial x} - \frac{\partial P}{\partial y} \right) \, dx dy$$

### Dokaz Greenove formule
Naj bo $D$ območje v ravnini $(x, y)$. Naj bosta $P(x, y)$ and $Q(x, y)$ zvezno odvedljivi funkciji na $D$.
$$\iint_D \frac{\partial Q}{\partial x} \, dx dy = \int_c^d \left[ \int_{\varphi(y)}^{\psi(y)} \frac{\partial Q}{\partial x}(x, y) \, dx \right] \, dy = \int_c^d [Q(\psi(y), y) - Q(\varphi(y), y)] \, dy$$
$$\iint_D \frac{\partial Q}{\partial x} \, dx dy = \int_c^d Q(\psi(y), y) \, dy - \int_c^d Q(\varphi(y), y) \, dy \quad (*)$$

Naj bo $\gamma : [\alpha, \tilde{\alpha}] \longrightarrow D$ parametrizacija roba $\partial D$.
$\gamma(t) = (x(t), y(t))$ in naj bo $\gamma(\alpha) = A$, $\gamma(\beta) = B$ in $\gamma(\tilde{\alpha}) = A$.
Če na desni strani $(*)$ vpeljemo novo spremenljivko $t$: $y = y(t) \implies dy = \dot{y} \, dt$.

Dobimo:
$$\iint_D \frac{\partial Q}{\partial x} \, dx dy = \int_\alpha^\beta Q \cdot \dot{y} \, dt + \int_\beta^{\tilde{\alpha}} Q \cdot \dot{y} \, dt = \oint_{\partial D} Q \, dy \quad (1)$$
Analogno:
$$\iint_D \frac{\partial P}{\partial y} \, dx dy = - \oint_{\partial D} P \, dx \quad (2)$$
Iz $(1)$ in $(2)$ dobimo:
$$\oint_{\partial D} P \, dx + Q \, dy = \iint_D \left( \frac{\partial Q}{\partial x} - \frac{\partial P}{\partial y} \right) \, dx dy$$

---

# Konzetvarivno polje

Vektorsko polje $\mathbf{F}$ je konzervativno, če obstaja neka skalarna funkcija $\phi$, tako da velja

$$\mathbf{F} = \nabla \phi$$

To pomeni, da je vektorsko polje dejansko **gradient** neke funkcije.

> Če imamo krivuljni integral od po parametrizirani krivulji $r(t)$, $t \in [a,b]$ in je $F = (P,Q)$ konzervativno polje potem integral od točke $r(a)$ do $r(b)$ ni odvisen od poti oz. dobimo isti rezultat za vsako pot od $r(a)$ do $r(b)$
> >[!|dokaz]+ Dokaz:
> > Predpostavimo, da je $\vec{F} = \nabla \phi$. Naj bo $C$ poljubna gladka pot od točke $A$ do točke $B$, parametrizirana z $\vec{r}(t)$ za $t \in [a, b]$.
> > 
> > Krivuljni integral je definiran kot:
> > $$\int_C \vec{F} \cdot d\vec{r} = \int_a^b \vec{F}(\vec{r}(t)) \cdot \vec{r}'(t) \, dt$$
> > 
> > Ker je $\vec{F} = \nabla \phi$, vstavimo:
> > $$\int_a^b \nabla \phi(\vec{r}(t)) \cdot \vec{r}'(t) \, dt$$
> > 
> > Po **verižnem pravilu** za funkcije več spremenljivk vemo, da je $\frac{d}{dt} \phi(\vec{r}(t)) = \nabla \phi(\vec{r}(t)) \cdot \vec{r}'(t)$. Integral postane:
> > $$\int_a^b \frac{d}{dt} \phi(\vec{r}(t)) \, dt$$
> > 
> > Po **osnovnem izreku analize** (Newton-Leibniz) dobimo:
> > $$\phi(\vec{r}(b)) - \phi(\vec{r}(a)) = \phi(B) - \phi(A)$$
> > 
> >  Rezultat je torej odvisen le od vrednosti potenciala v končnih točkah, ne pa od same poti $C$.
> >  
> >  *Velja tudi da če je itnegral za vsako krivuljo od $a$ do $b$ enak ne glede na pot potem je $F$ konzervativno polje. To dokažemo z definicijo integrala $\phi(x,y) = \int_{(x_{0},y_{0})}^{(x,y)} \vec{F} \cdot \vec{dr}$ od poljubne točke $x_{0},y_{0}$ do $x,y$. Ker integral ni odvisen od poti je ta vrednosti enolično določena za vsak $x,y$ torej je veljavna defincija. Vidimo da velja $\frac{\partial \phi}{\partial x} = P$ in $\frac{\partial \phi}{\partial y} = Q$.*

<br>

> Če je polje konzervativno je integral po sklenjeni krivulji enak 0.
> >[!|dokaz]+ Dokaz:
> > Vemo da je integral po krivulji po konzervativnem vektorskem polju enak integralu skalarne funkcije po parametrizirani krivulji kjer vemo da je integral od $r(a)$ do $r(b)$ enak $\phi(a) - \phi(b).$ Če velja da je $a = b$ potem je to enako 0.
> > 
> > Dokaz v obratno smer deluje tako da vidimo da lahko za dve poljubni krivulji definiramo sklenjeno krivuljo ki gre naprej po eni in nazaj po drugi. Ker je sklenjena in je enaka 0 mora veljati da je pot po eni enaka pot po drugi torej sta obe enaki torej je polje konzervativno.


> Polje $F = (P,Q)$ je konzervativno $\Leftrightarrow \frac{\partial Q}{\partial x} = \frac{\partial P}{\partial y}$ 
> >[!|dokaz]+ Dokaz:
> >
> >$\Rightarrow$
> > Naj bo $C$ zaprta pot ($A = B$). Ker smo v konzervativnem polju je integral po sklenjeni krivulji vendo 0. Sledi da lahko z greenovo formulo zapišemo
> > 
> > $$\oint_{\partial K}P dx + Qdy = \int_{K}^{}\frac{\partial Q}{\partial x}- \frac{\partial P}{\partial y}dxdy$$
> > 
> > Ker velja da je integral po tej sklenjeni krivulji $K$ enak 0 mora biti integral na desni enak 0 torej mora veljati da je $\frac{\partial Q}{\partial x} = \frac{\partial P }{\partial y}$.
> > 
> > $\Leftarrow$
> > 
> > Vzamemo poljubno sklenjeno krivuljo $K$. Ta mora omejevati neko območje. Uporabimo greenovo formulo in vidimo da je integral enak 0. To pomeni da morata biti parcialna odvoda enaka.


