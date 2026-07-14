

# Uvedba novih spremenljivk

Spomnimo se formule za uvedbo nove spremenljivke v integral funkcije ene spremenljivke:
$$\int_a^b f(x) \, dx$$
Naj bo $x(u) : [\alpha, \beta] \longrightarrow [a, b]$ monotono naraščajoča odvedljiva funkcija. Potem velja:
$$\int_a^b f(x) \, dx = \int_\alpha^\beta f(x(u)) \cdot \frac{dx}{du} \, du = \int_\alpha^\beta f(x(u)) \cdot x'(u) \, du$$

Naš cilj v tem razdelku je izpeljati analogno formulo za dvojni integral.

Če hočemo iti iz $(x,y)$ v $(u,v)$ se mora vsaka točka na $xy$ ravnini izraziti z neko točko v $uv$ ravnini. Torej se mora neka točka iz $uv$ preslikati v $xy$ točko, torej imamo $F: (u,v) \mapsto (x(u,v),y(u,v))$. Potem lahko uporabimo točko v $uv$ in vemo katero točko v $xy$ v resnici obdelujemo.

Ker se ukvarjamo z integracijo in govorimo o majhni spremembi ploščine si lahko predstavljamo da ko se nek vektor iz $uv$ ravnine preslika v $xy$ ravnino se lahko spremeni njegova smer s čimer se na primer vektorja ki označujeta ploščino kot kvadrat spremenita v paralelogram. Zaradi tega moramo ob prehodu pri integriranju še upoštevati morebitno spremembo vrednosti neskončno majhne  ploščine $dA$.

Naj bo
$$F : D \longrightarrow \Omega$$
$$(u, v) \longmapsto (x(u,v), y(u,v))$$
preslikava, ki je bijektivna in odvedljiva. Spomnimo se, kaj je odvod (diferencial) preslikave $F$. Odvod preslikave $F$ v točki $(u_0, v_0)$ je linearna preslikava $A : \mathbb{R}^2 \longrightarrow \mathbb{R}^2$, za katero velja:
$$F((u_0, v_0) + (h, k)) = F(u_0, v_0) + A \begin{pmatrix} h \\ k \end{pmatrix} + o(h, k)$$
kjer je $\lim_{\|(h,k)\| \to 0} \frac{o(h, k)}{\|(h, k)\|} = 0$. Če takšna preslikava obstaja, pravimo, da je $F$ v $(u_0, v_0)$ odvedljiva in odvod $D_{(u_0, v_0)} F$ je enak $A$.

Izrek in razmislek pokažeta:
$$D_{(u_0, v_0)} F = \begin{pmatrix} \frac{\partial x}{\partial u} & \frac{\partial x}{\partial v} \\ \frac{\partial y}{\partial u} & \frac{\partial y}{\partial v} \end{pmatrix}_{(u_0, v_0)}$$

Označimo Jacobijevo determinanto:
$$\text{Jac}(F)(u, v) = \det(D_{(u, v)} F)$$

Formula za uvedbo nove spremenljivke v dvojni integral se glasi:
$$\iint_D f(x, y) \, dx dy = \iint_\Omega f(x(u, v), y(u, v)) \cdot |\text{Jac}(F)(u, v)| \, du dv$$

---


# Izračun ploščine z novimi spremenljivkami

Vrnimo se k naši preslikavi $F: \Omega \to D$. Ploščina območja $D$ je:
$$A(D) = \iint_D dx dy$$
V Greenovi formuli vzamemo $Q = x$ in $P = 0$. Potem:
$$\iint_D dx dy = \oint_{\partial D} x \, dy = \int_\alpha^{\tilde{\alpha}} x(t) \dot{y}(t) \, dt$$
Uporabimo nove spremenljivke $u, v$:
$x(t) = x(u(t), v(t))$, $y(t) = y(u(t), v(t))$
$$\iint_D dx dy = \int_\alpha^{\tilde{\alpha}} \left( x \frac{\partial y}{\partial u} \dot{u} + x \frac{\partial y}{\partial v} \dot{v} \right) \, dt \quad (**)$$
Z uporabo Greenove formule na območju $\Omega$ za $P = x \frac{\partial y}{\partial u}$ in $Q = x \frac{\partial y}{\partial v}$:
$$\iint_\Omega \left[ \frac{\partial}{\partial u} \left( x \frac{\partial y}{\partial v} \right) - \frac{\partial}{\partial v} \left( x \frac{\partial y}{\partial u} \right) \right] \, du dv = \iint_\Omega \left( \frac{\partial x}{\partial u} \frac{\partial y}{\partial v} + x \frac{\partial^2 y}{\partial u \partial v} - \frac{\partial x}{\partial v} \frac{\partial y}{\partial u} - x \frac{\partial^2 y}{\partial v \partial u} \right) \, du dv$$
$$= \iint_\Omega \left( \frac{\partial x}{\partial u} \frac{\partial y}{\partial v} - \frac{\partial x}{\partial v} \frac{\partial y}{\partial u} \right) \, du dv = \iint_\Omega \text{Jac}(F) \, du dv$$
Torej:
$$A(D) = \iint_D dx dy = \iint_\Omega |\text{Jac}(F)(u, v)| \, du dv$$

---

# Posebni koordinatni sistemi

### Polarne koordinate
$$x(r, \varphi) = r \cos \varphi$$
$$y(r, \varphi) = r \sin \varphi$$
Jacobijeva matrika:
$$\text{Jac}(r, \varphi) = \begin{pmatrix} \cos \varphi & -r \sin \varphi \\ \sin \varphi & r \cos \varphi \end{pmatrix}$$
$$\det(\text{Jac}) = r \cos^2 \varphi + r \sin^2 \varphi = r$$
Torej:
$$\iint_D f(x, y) \, dx dy = \iint_\Omega f(r \cos \varphi, r \sin \varphi) \cdot r \, dr d\varphi$$

### Sferne koordinate
$$x = r \cos \varphi \cos \vartheta$$
$$y = r \sin \varphi \cos \vartheta$$
$$z = r \sin \vartheta$$
Jacobijeva determinanta:
$$\det \begin{pmatrix} \frac{\partial x}{\partial \varphi} & \frac{\partial x}{\partial \vartheta} & \frac{\partial x}{\partial r} \\ \dots & \dots & \dots \end{pmatrix} = r^2 \cos \vartheta$$

---

# Posplošeni dvojni integral

Če ima funkcija $f$ v točki $(x_0, y_0) \in \text{Int}(D)$ singularnost, definiramo posplošeni integral:
$$\iint_D f(x, y) \, dx dy = \lim_{\epsilon \to 0} \iint_{D \setminus K((x_0, y_0), \epsilon)} f(x, y) \, dx dy$$

### Primer: Gaussov integral
Izračunajmo $I = \int_{-\infty}^\infty e^{-x^2} \, dx$.
Vemo: $\iint_{\mathbb{R}^2} e^{-(x^2+y^2)} \, dx dy = \pi$.
$$\iint_{\mathbb{R}^2} e^{-x^2} e^{-y^2} \, dx dy = \left( \int_{-\infty}^\infty e^{-x^2} \, dx \right) \left( \int_{-\infty}^\infty e^{-y^2} \, dy \right) = \left( \int_{-\infty}^\infty e^{-x^2} \, dx \right)^2 = \pi$$
Torej:
$$\int_{-\infty}^\infty e^{-x^2} \, dx = \sqrt{\pi}$$

---



### Uvedba novih spremenljivk


>[!|hide]- **Uvedba novih spremenljivk v eni spremenljivki**
> $$\int_{\alpha}^{\beta} f(x(u)) x'(u) du$$
> 
> $f$ ima prafunkcijo $F$. Torej velja 
> 
> $$F(x(u))' = F'(x(u))x'(u)$$
> 
> Ker je $F$ prafunkcija velja $F'(x(u)) = f(x(u))$.
> 
> $$F(x(u))' = f(x(u))x'(u)$$
> 
> Integriramo obe strani in dobimo
> 
> $$\int_{\alpha}^{\beta} (F(x(u)))' du = \int_{\alpha}^{\beta} f(x(u)) x'(u) du$$
> 
> Po **Newton-Leibnizovi formuli** vemo, da velja
> 
> $$F(x(\beta)) - F(x(\alpha)) = \int_{\alpha}^{\beta} f(x(u)) x'(u) du$$
> 
> Ker pa je $F$ prafunkcija $f$ (torej $F' = f$), leva stran predstavlja določeni integral $f$ od $x(\alpha)$ do $x(\beta)$:
> 
> $$\int_{x(\alpha)}^{x(\beta)} f(x) dx = F(x(\beta)) - F(x(\alpha))$$
> 
> Sledi da je
> 
> $$\int_{\alpha}^{\beta} f(x(u)) x'(u) du = \int_{x(\alpha)}^{x(\beta)} f(x) dx$$
> 
> **Lahko izpeljemo tudi na drug način**
> 
> Substitucija: $x(u) : [\alpha, \beta] \rightarrow [a, b]$, pri čemer je $x(\alpha) = a$ in $x(\beta) = b$.
> 
> $$\int_{a}^{b} f(x) dx =$$
> $$=\int_{x(\alpha)}^{x(\beta)} f(x) dx =$$ $$ F(x(\beta))-F(x(\alpha))=\int_{\alpha}^{\beta}F(x(u))'du=$$
> $$=\int_{\alpha}^{\beta}F'(x(u))x'(u)du=\int_{\alpha}^{\beta}f(x(u))x'(u) du$$
> 
> Torej je
> 
> $$\int_{x(\alpha)}^{x(\beta)} f(x) dx =$$ 
> $$=\int_{\alpha}^{\beta}f(x(u))x'(u) du$$
> 
> Ta način lahko interpretiramo kot menjava koordinatnega sistema v eni spremenljivki.
> 
> Npr. $\sqrt[]{1-x^{2}}$. Vemo da je $x = \cos\,\!  u$, če je $u$ kot. Torej imamo $\sqrt[]{1-\cos^{2} u}(-\sin\,\! u) = \sin\,\! u(- \sin\,\! u)$ ...



**Uvedba novih spremenljivk v dveh spremenljivkah**

$$\iint_D f(x, y) dx dy$$

Enačbo bomo dokazali po zadnjem načinu dokaza ene spremenljivke. Torej **zamenjavo koordinatnega sistema**.

**Preslikava mora biti bijektivna in diferenciabilna** $F : \Omega \subset \mathbb{R}^2 \rightarrow D \subset \mathbb{R}^2$
$(u, v) \mapsto F(u, v) \in D = (x(u, v), y(u, v))$

Potrebujemo vektorsko funkcijo $F$ ki slika iz $\Omega$ v $D$ oz. zamenja koordinatni sistem. Torej če opisujemo enotsko krožnico v $(x,y)$ imamo $x \in  [-1,1], y \in   [-1,1]$. Ko se damo v polarne imamo $u \in [0,2\pi]$ in $r \in [0,1]$

$$\iint_{\Omega} f(x, y) dx dy = \iint_{D} f(x(u, v), y(u, v)) \left| \det \begin{bmatrix} \frac{\partial x}{\partial u} & \frac{\partial x}{\partial v} \\ \frac{\partial y}{\partial u} & \frac{\partial y}{\partial v} \end{bmatrix} \right| du dv$$

Preslikava mora biti diferenciabilna kar pomeni, da v točki $(u_0, v_0)$ odvedljiva obstaja taka linearna preslikava $A : \mathbb{R}^2 \rightarrow \mathbb{R}^2$, da velja:

$$F(u_0 + h, v_0 + k) = F(u_0, v_0) + A \begin{pmatrix} h \\ k \end{pmatrix} + \sigma(h, k)$$

in $\lim_{\|(h,k)\| \rightarrow 0} \frac{\sigma(h, k)}{\|(h,k)\|} = 0$.

Potem je $A = D(u_0, v_0)F$ odvod v $(u_0, v_0)$. 

$$F((u_0, v_0) + (\Delta u, \Delta v)) \approx F(u_0, v_0) + (D(u_0, v_0)F) \begin{pmatrix} \Delta u \\ \Delta v \end{pmatrix}$$

Definiramo $\Delta u$ in $\Delta v$ kot stranici kvadrata v $\Omega$. Ploščina kvadrata je tako $\Delta u\Delta v$. Ko preslikamo vektorja $\Delta u$ in $\Delta v$ v $D$ dobimo paralelogram katere ploščina vemo da je njun vektorski produkt oz. determinanta. Torej

$$a = F(u_0+\Delta u, v_0) - F(u_0,v_0) \approx \begin{pmatrix} \frac{\partial x}{\partial u} & \frac{\partial x}{\partial v}\\ \frac{\partial y}{\partial u} &\frac{\partial y}{\partial v} \end{pmatrix}\cdot \begin{pmatrix} \Delta u \\ 0\end{pmatrix}$$

$$b = F(u_0, v_0 + \Delta v) - F(u_0,v_0) \approx \begin{pmatrix} \frac{\partial x}{\partial u} & \frac{\partial x}{\partial v}\\ \frac{\partial y}{\partial u} &\frac{\partial y}{\partial v} \end{pmatrix}\cdot \begin{pmatrix} 0 \\ \Delta v\end{pmatrix}$$

$$\Rightarrow$$

$$\vec{a} = \begin{pmatrix} \frac{\partial x}{\partial u} \\ \frac{\partial y}{\partial u} \end{pmatrix} \Delta u, \quad \vec{b} = \begin{pmatrix} \frac{\partial x}{\partial v} \\ \frac{\partial y}{\partial v} \end{pmatrix} \Delta v$$

$$\Rightarrow$$

$$a = \left(\frac{\partial x}{\partial u} \Delta u, \frac{\partial y }{\partial u} \Delta u\right)$$
$$b = \left(\frac{\partial x}{\partial v} \Delta v, \frac{\partial y}{\partial v}\Delta v\right)$$




Ploščina slike v $D$ je približno paralelogram določen z $a$ in $b$ katerega ploščina vemo da je vektorski produkt le teh, oz. determinanta. 

$$\Delta A = |a_1b_2 - a_2b_1|$$

Vstavimo komponente

$$\Delta A \approx \left| \left( \frac{\partial x}{\partial u} \Delta u \right) \left( \frac{\partial y}{\partial v} \Delta v \right) - \left( \frac{\partial y}{\partial u} \Delta u \right) \left( \frac{\partial x}{\partial v} \Delta v \right) \right|$$

Izpostavimo $\Delta u \Delta v$

$$\Delta A \approx \left| \frac{\partial x}{\partial u} \frac{\partial y}{\partial v} - \frac{\partial y}{\partial u} \frac{\partial x}{\partial v} \right| \Delta u \Delta v$$

Ker je integral po območju $D$ limita vsote

$$\iint_D f(x, y) \, dA \approx \sum f(x_i, y_i) \Delta A_i$$

Vstavimo našo transformacijo ploščine

$$\sum f(x(u_i, v_i), y(u_i, v_i)) \cdot |J(u_i, v_i)| \Delta u \Delta v$$

Ko gresta $\Delta u, \Delta v \to 0$, ta vsota postane dvojni integral po območju $D$


$$\iint_D f(x, y) dx dy = \iint_{\Omega} f(x(u, v), y(u, v)) |\det D(u, v) F| du dv$$

### Dokaz formule za zamenjavo spremenljivk

Ker se ukvarjamo z vektorsko funkcijo za preslikavo v novi koordinatni sistem si poglejmo pomemben izrek o integriranju vektorksih funkcij na krivulji.

**Integral vektorskega polja po krivulji**

Če hočemo integrirati vektorsko polje po krivulji moramo imeti vektrosko polje $F(x,y)=(P(x,y),Q(x,y))$ in krivuljo $r(t) = (x(t),y(t))$.
Diferencial po krivulji označimo kot $dr = (dx,dy)$ kje vemo da je $dx = x'(t)dt$ in $dy=y'(t)dt$. Tako velja $\mathbf{dr} = (x'(t),y'(t))dt$. Integral je tako definiran kot skalarni produkt med $F$ in $\mathbf{dr}$.


$$\oint_{\partial D} (P,Q) \cdot   \mathbf{dr}$$

$$\oint_{\partial D} P \cdot dx + Q \cdot dy$$
$$\oint_{\partial D} (P \cdot x'(t) + Q \cdot y'(t))dt$$

*Kjer sta $P,Q = P(x(t),y(t)),Q(x(t),y(t))$ ker se premikamo po krivulji.*



$$\color{green}\oint_{\partial D} P \cdot dx + Q \cdot dy$$

**Greenova formula**

Imamo funkcijo $P(x,y)$. Naj bo definirana na kvadratu. Če želimo dobiti robni integral funkcije $\oint P \cdot  dx$ (samo po $dx$) na robu kvadrata gremo čez vse stranice. Leva in desna stranica nimata $dx$ oz. je $0$. Za spodnjo in zgornjo pa velja da pri spodnji prištevamo vrednost pri zgornji pa odštevamo (gremo v nasprotno smer kot pri spodnji). Vidimo da je robni integral enak $P(\text{top}) - P(\text{bottom})$ kar je po definiciji enako $\iint_{\text{bottom}}^{\text{ top}}\frac{\partial P}{\partial y}dy$. 

Ker je naš integral $\text{bottom}-\text{top}$ dobimo še minus.

$$\oint_{\partial D}P \cdot dx = \int_{\text{left}}^{\text{right}}\int_{\text{top}}^{\text{ bottom}}\frac{\partial P}{\partial y}dy = \iint_{D}-\frac{\partial P}{\partial y}dy dx$$

Če te kvadrate pomanjšamo da opišemo dejansko območje integracije vidimo da se pri integriranju vsakega kvadrata, kjer se spodnji in zgornji rob dveh kvadratov dotikata prištejeta in odštejeta. To pomeni da jih lahko pokrajšamo. Edini ki se ne pokrajšajo so tisti ki tvorijo rob $\partial D$.

Na enak način velja

$$\oint_{\partial D}Q \cdot dy = \int_\text{bottom}^{\text{top}}\int_{\text{left}}^{\text{right}} \frac{\partial Q}{\partial x}dxdy =\iint_{D} \frac{\partial Q}{\partial x} dxdy$$

Na ta način lahko zapišemo območje omejeno z $g_{1}(x)$ in $g_{2}(x)$

Spet gledamo spodnjo in zgronjo mejo. Dodajamo vse kar je spodaj in odštevamo vse kar je zgoraj, torej velja

$$\oint_{\partial D} P(x,y)dx = \int_{a}^{b} P(x,g_{1}(x))-P(x,g_{2}(x))dx=$$
$$= \int_{a}^{b}\int_{g_{2}(x)}^{g_{1}(x)}\frac{\partial P}{\partial y}(x,y)dA=$$
$$=\int_{a}^{b}\int_{g_{1}(x)}^{g_{2}(x)}-\frac{\partial P}{\partial y}(x,y)dA=$$
$$=\iint_{D}-\frac{\partial P}{\partial y}(x,y)dA$$

*Seštevamo po $x$ od $a$ do $b$ razlike med spodnjo vrednostjo $P$ in zgornjo vrednostjo $P$, to je po definiciji integral parcialnega odvoda po $y$, kar je potem združeno v integral po $D$.*

Analogno naredimo za $Q$

$$\oint_{\partial D} Q(x,y)dy = \int_{c}^{d} Q(h_{2}(y),y)-Q(h_{1}(y),y)dy=$$
$$= \int_{c}^{d}\int_{h_{1}(y)}^{h_{2}(y)}\frac{\partial Q}{\partial x}(x,y)dA=$$
$$=\iint_{D}\frac{\partial Q}{\partial x}(x,y)dA$$

Če te ugotovitve združimo dobimo Greenovo formulo

$$\oint_{\partial D}(P \cdot  dx + Q \cdot dy) = \iint_{D}\left(\frac{\partial Q}{\partial x} - \frac{\partial P}{\partial y}\right)dxdy$$

> **Greenova formula**
> 
> Naj bo $D \subset \mathbb{R}^2$ območje in $\partial D$ njegov rob.
> Naj bo $(x, y) \mapsto (P(x, y), Q(x, y))$ vektorsko polje na $D$. 
> 
> Naj bo  parametrizacija roba $\partial D$ funkcija $\gamma(t) : [\alpha, \beta] \rightarrow \mathbb{R}^2$, kjer je $r(t) = (x(t), y(t))$.
> 
> Tedaj velja:
> 
> $$\int_{\partial D} \langle (P(\gamma(t)), Q(\gamma(t))), \dot{r}(t) \rangle dt = \int_{\partial D} \langle (P, Q), (\dot{x}(t), \dot{y}(t)) \rangle dt$$
> 
> $$\int_{\alpha}^{\beta} (P(x(t), y(t)) \dot{x}(t) + Q(x(t), y(t)) \dot{y}(t)) dt = \iint_D \left( \frac{\partial Q}{\partial x}(x, y) - \frac{\partial P}{\partial y}(x, y) \right) dx dy$$
> 
> Splošna oblika:
> 
> $$\int_{\partial D} (P dx + Q dy) = \iint_D \left( \frac{\partial Q}{\partial x} - \frac{\partial P}{\partial y} \right) dx dy$$



**Dokaz Greenove formule**

Naj bo $r(t) = (x(t), y(t))$ parametrizacija $\partial D$.
$t = \alpha \implies r(\alpha) = A$
$t = \beta \implies r(\beta) = B$
$t = \alpha^* \implies r(\alpha^*) = A$

Dokazujemo:

$$\int_{\alpha}^{\alpha^*} P dx + Q dy = \iint_D \left( \frac{\partial Q}{\partial x} - \frac{\partial P}{\partial y} \right) dx dy$$
$$\int_{\alpha}^{\alpha^*} (P \dot{x} + Q \dot{y}) dt = \iint_D \left( \frac{\partial Q}{\partial x} - \frac{\partial P}{\partial y} \right) dx dy$$

Oglejmo si najprej $\iint_D \frac{\partial Q}{\partial x} dx dy$:

$$\iint_D \frac{\partial Q}{\partial x} dx dy = \int_c^d \left[ \int_{\phi(y)}^{\psi(y)} \frac{\partial Q}{\partial x} dx \right] dy = \int_c^d (Q(\psi(y), y) - Q(\phi(y), y)) dy$$

$$\int_c^d Q(\psi(y), y) dy - \int_c^d Q(\phi(y), y) dy = \int_c^d Q(\psi(y), y) dy + \int_d^c Q(\phi(y), y) dy$$

Uporabimo parametrizacijo $r(t) = (x(t), y(t))$ in zvezo $dy = \dot{y} dt$:

$$\int_{\alpha}^{\beta} Q(x(t), y(t)) \dot{y} dt + \int_{\beta}^{\alpha^*} Q(x(t), y(t)) \dot{y} dt = \int_{\alpha}^{\alpha^*} Q(x(t), y(t)) \dot{y} dt$$

Analogno velja:

$$\iint_D \frac{\partial P}{\partial y} dx dy = - \int_{\alpha}^{\alpha^*} P(x(t), y(t)) \dot{x} dt$$

Torej res:

$$\iint_D \left( \frac{\partial Q}{\partial x} - \frac{\partial P}{\partial y} \right) dx dy = \int_{\partial D} (P \dot{x} + Q \dot{y}) dt$$

**Izpeljava ploščine in Jacobiana**

Vrnimo se k preslikavi $F : \Omega \rightarrow D$, kjer je $F(u, v) = (x(u, v), y(u, v))$. Izračunajmo ploščino $A(D)$:

$$A(D) = \iint_{D }dx dy = \iint_{D}1-0dxdy$$
$$1 = \frac{\partial Q}{\partial x}, 0 = \frac{\partial P }{\partial y}$$

Naj bo v Greenovi formuli $Q = x$ in $P = 0$:

$$A(D) = \iint_D 1 dx dy = \int_{\partial D} x \cdot \dot{y} \cdot  dt$$

Uporabimo za $\partial D$ parametrizacijo $t \mapsto (x(u(t), v(t)), y(u(t), v(t)))$ za $t \in [\alpha,\alpha^{*}]$:

$$\int_{\partial D} x \dot{y} dt = \int_{\alpha}^{\alpha^{*}} x \left( \frac{\partial y}{\partial u} \dot{u} + \frac{\partial y}{\partial v} \dot{v} \right) dt = \int_{\alpha}^{\alpha^{*}} \left[ \left(x \frac{\partial y}{\partial u}\right) \dot{u} + \left(x \frac{\partial y}{\partial v}\right) \dot{v} \right] dt$$

Uporabimo Greenovo formulo za $P = x \frac{\partial y}{\partial u}$ in $Q = x \frac{\partial y}{\partial v}$:

$$\iint_{\Omega} \left[ \frac{\partial}{\partial u} \left(x \frac{\partial y}{\partial v}\right) - \frac{\partial}{\partial v} \left(x \frac{\partial y}{\partial u}\right) \right] du dv$$

$$\iint_{\Omega} \left[ \frac{\partial x}{\partial u} \frac{\partial y}{\partial v} + x \frac{\partial^2 y}{\partial u \partial v} - \frac{\partial x}{\partial v} \frac{\partial y}{\partial u} - x \frac{\partial^2 y}{\partial v \partial u} \right] du dv$$

$$\iint_{\Omega} \left[ \frac{\partial x}{\partial u} \frac{\partial y}{\partial v} - \frac{\partial x}{\partial v} \frac{\partial y}{\partial u} \right] du dv = \iint_{\Omega} \det \begin{bmatrix} \frac{\partial x}{\partial u} & \frac{\partial x}{\partial v} \\ \frac{\partial y}{\partial u} & \frac{\partial y}{\partial v} \end{bmatrix} du dv$$

Imamo torej:

$$A(D) = \iint_{\Omega} J(x(u, v), y(u, v)) du dv$$

V nadaljevanju uporabimo izrek o povprečni vrednosti (IPV). Obstajata $u_p, v_p \in \Omega$ tako, da velja:

$$A(D) = J(x(u_p, v_p), y(u_p, v_p)) \iint_{\Omega} du dv = J(x(u_p, v_p), y(u_p, v_p)) \cdot A(\Omega)$$

# Dokaz splošne formule za uvedbo novih spremenljivk

Naj bo $f : D \rightarrow \mathbb{R}$ integrabilna. Izračunajmo $\iint_D f(x, y) dx dy$. Naj bo $F : \Omega \rightarrow D$ odvedljiva bijektivna preslikava. Vpeljemo na $\Omega$ delitev na pravokotnike s ploščino $(\Delta u)_k (\Delta v)_l$.

$\Omega_{kl} = \{(u_k, u_{k-1}) \times (v_l, v_{l-1})\}$

To mrežo s preslikavo $F : \Omega \rightarrow D$ preslikamo na mrežo $D_{kl} = F(\Omega_{kl})$.

$$\iint_D f(x, y) dx dy = \lim_{\delta \rightarrow 0} \sum_{k,l} f(\xi_{kl}, \eta_{kl}) A(D_{kl})$$

Po izreku o povprečni vrednosti obstajajo v $\Omega_{kl}$ točke $(u_{kl}, v_{kl})$, za katere velja:

$$\iint_{\Omega_{kl}} |J(u, v)| du dv = |J(u_{kl}, v_{kl})| \cdot A(\Omega_{kl})$$

Iz definicije sledi:

$$\iint_D f(x, y) dx dy = \lim \sum_{k,l} f(x_{kl}, y_{kl}) A(D_{kl})$$

Pri tem je $\delta = \max A(D_{kl})$. Velja $A(D_{kl}) = |J(u_{kl}, v_{kl})| A(\Omega_{kl})$.

Sestavimo vsoto:

$$\sum_{k,l} f(x_{kl}, y_{kl}) A(D_{kl}) = \sum_{k,l} f(x(u_{kl}, v_{kl}), y(u_{kl}, v_{kl})) \cdot |J(u_{kl}, v_{kl})| \cdot A(\Omega_{kl})$$

Ker je preslikava bijektivna, velja $A(D_{kl}) \rightarrow 0 \iff A(\Omega_{kl}) \rightarrow 0$. Ko pošljemo $\delta \rightarrow 0$, integralska vsota konvergira k integralu:

$$\iint_D f(x, y) dx dy = \iint_{\Omega} f(x(u, v), y(u, v)) |J(u, v)| du dv$$

**Izrek**

Naj bo $f : D \rightarrow \mathbb{R}$ integrabilna in naj bo $S : \Omega \rightarrow D$ preslikava $(u, v) \mapsto (x(u, v), y(u, v))$, ki je bijektivna in odvedljiva. Potem velja:

$$\iint_D f(x, y) dx dy = \iint_{\Omega} f(x(u, v), y(u, v)) |J(u, v)| du dv$$

Najpomembnejše nekartezijske koordinate so polarne in sferične.