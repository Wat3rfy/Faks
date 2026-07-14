
# Krivuljni in ploskovni integrali

### Dolžina krivulje
Naj bo $\gamma(t) : [\alpha, \beta] \longrightarrow \mathbb{R}^3$ krivulja. Dolžina krivulje $L(\gamma)$ je definirana kot:
$$L(\gamma) = \int_\alpha^\beta \|\dot{\gamma}(t)\| \, dt = \int_\alpha^\beta \sqrt{\dot{x}(t)^2 + \dot{y}(t)^2 + \dot{z}(t)^2} \, dt$$

Če imamo dve parametrizaciji za isto krivuljo velja da je njuna tangenta v isti točki vzporedna ne pa nujno enako dolga.

Če velja $r_{1}(t) = r_{2}(u(t))$ potem je $r_{1}' = \frac{dr_{2}}{du} \cdot \frac{du}{dt}$

S tem lahko tudi pokažemo da je dolžina krivulje neodvisna od parametrizacije.

Parametrizaciji pravimo **naravna** ko velja da je dolžine odvoda parametrizacije vedno ena in velja $\int_{K}^{}dr=\int_{a}^{b}|\dot r(s)|ds = \int_{a}^{b}ds= b-a$.

### Integral skalarna polja po krivulji
$$\int_\gamma f = \int_\alpha^\beta f(\gamma(t)) \|\dot{\gamma}(t)\| \, dt$$

### Integral vektorskega polja po krivulji
Naj bo $V = (X(x,y,z),Y(x,y,z),Z(x,y,z))$ vektorsko polje. Integral polja $V$ po krivulji $\gamma$ je:
$$\int_\gamma V = \int_\alpha^\beta V(\gamma(t)) \cdot \dot{\gamma}(t) \, dt = \int_\gamma X \, dx + Y \, dy + Z \, dz$$

Če je $V$ potencialno polje ($V = \nabla u$, $V$ je gradient neke funkcije), potem je integral neodvisen od poti:
$$\int_\gamma \nabla u = u(\gamma(\beta)) - u(\gamma(\alpha))$$

> Če je $\gamma$ sklenjena krivulja, je integral potencialnega polja enak 0.
> 
> $\Rightarrow$
> $$\oint_\gamma \vec{V} = \int_\alpha^\beta \left( \frac{\partial u}{\partial x} \dot{x} + \frac{\partial u}{\partial y} \dot{y} + \frac{\partial u}{\partial z} \dot{z} \right) dt = \int_\alpha^\beta \frac{d}{dt} u(r(t)) dt = u(r(\beta)) - u(r(\alpha)) = 0.$$
> 
> $\Leftarrow$
> Fiksiramo točko $(x_0, y_0, z_0)$. Definiramo $u(x, y, z) = \int_{\gamma} \vec{V}$, kjer je $\gamma$ poljubna krivulja od $(x_0, y_0, z_0)$ do $(x, y, z)$. Ker je $\oint \vec{V} = 0$, je integral neodvisen od poti in definicija je dobra.
> 
> Pokažimo $\frac{\partial u}{\partial x} = X$. Izberemo pot $\gamma_1$ do $(x, y, z)$ in podaljšek $\gamma_2$ po daljici do $(x + h, y, z)$.
> $u(x + h, y, z) - u(x, y, z) = \int_{\gamma_2} \vec{V} = \int_{0}^{h} X(x + t, y, z)dt$.
> 
> Po izreku o povprečni vrednosti: $\int_{0}^{h} X(x + t, y, z)dt = X(x + \xi, y, z) \cdot h$.
> Torej $\frac{u(x+h, y, z) - u(x, y, z)}{h} = X(x + \xi, y, z)$. Ko $h \to 0$, dobimo $\frac{\partial u}{\partial x} = X$. Analogno za $Y$ in $Z$.
> 
---

# Površina ploskve

Naj bo $M \subset \mathbb{R}^3$ ploskev, podana s parametrizacijo:
$$r : \Omega \subset \mathbb{R}^2 \longrightarrow M \subset \mathbb{R}^3$$
$$(u, v) \longmapsto (x(u,v), y(u,v), z(u,v))$$
Tangentna vektorja sta $r_u = \frac{\partial r}{\partial u}$ in $r_v = \frac{\partial r}{\partial v}$.
Površina ploskve $A(M)$ je definirana kot:
$$A(M) = \iint_\Omega \|r_u \times r_v\| \, du dv$$

### Prva fundamentalna forma
Definiramo koeficiente:
$E = \langle r_u, r_u \rangle$
$F = \langle r_u, r_v \rangle$
$G = \langle r_v, r_v \rangle$

Dolžina krivulje na ploskvi $(u(t), v(t)): L(\gamma) = \int_{a}^{b} \sqrt{E\dot{u}^2 + 2F\dot{u}\dot{v} + G\dot{v}^2} dt$

Z uporabo Lagrangeeve identitete $\|a \times b\|^2 = \|a\|^2 \|b\|^2 - \langle a, b \rangle^2$ dobimo:
$$\|r_u \times r_v\| = \sqrt{EG - F^2}$$
Torej:
$$A(M) = \iint_\Omega \sqrt{EG - F^2} \, du dv$$

Matrika $\begin{pmatrix} E & F \\ F & G \end{pmatrix}$ se imenuje matrika prve fundamentalne forme ploskve $M$.

## Ploskovni integral in vektorska analiza

### Ploskovni integral

**Definicija:** Naj bo $M \subset \mathbb{R}^3$ neka regularna ploskev z regularno parametrizacijo:
$$r : D \longrightarrow M \subset \mathbb{R}^3$$
$$(u, v) \longmapsto (x(u,v), y(u,v), z(u,v))$$

Naj bo $f : M \longrightarrow \mathbb{R}$ funkcija (skalarno polje) na $M$.

Ploskovni integral funkcije $f$ po $M$ je podan s predpisom:
$$\int_M f \, dS = \iint_D f(r(u,v)) \, |r_u \times r_v| \, du \, dv$$

Če je $f \equiv 1$, nam zgornja formula da površino $M$.

---

Tako kot definicija površine ploskve, je tudi zgornja definicija neodvisna od izbire parametrizacije. Dokaz je modifikacija dokaza za neodvisnost površine.

**Primer:** Naj bo $M$ zgornja polovica homogene sfere z radijem $a$ v $\mathbb{R}^3$. Izračunajmo težišče $(x_T, y_T, z_T)$.

Iz simetrije takoj sledi $x_T = y_T = 0$. Izračunajmo samo $z_T$.
$$z_T = \frac{1}{m(M)} \int_M z \, dm = \frac{1}{2\pi a^2 \rho} \iint_M z \rho \, dS = \frac{1}{2\pi a^2} \iint_M z \, dS$$

Hemisfero parametriziramo s sferičnimi koord.:
$$r(\varphi, \vartheta) = (a \cos \varphi \sin \vartheta, a \sin \varphi \sin \vartheta, a \cos \vartheta)$$
$\varphi \in [0, 2\pi], \vartheta \in [0, \pi/2]$.

Ker je $r_\varphi \perp r_\vartheta$ in $\|r_\varphi\| = a \sin \vartheta$, $\|r_\vartheta\| = a$,
je $|r_\varphi \times r_\vartheta| = \|r_\varphi\| \|r_\vartheta\| = a^2 \sin \vartheta$.

---

Torej:
$$z_T = \frac{1}{2\pi a^2} \int_0^{2\pi} d\varphi \int_0^{\pi/2} a \cos \vartheta \cdot a^2 \sin \vartheta \, d\vartheta$$
$$z_T = a \int_0^{\pi/2} \sin \vartheta \cos \vartheta \, d\vartheta = \frac{a}{2}$$

**Definicija:** Naj bo $M$ ploskev z orientacijo $\vec{N}$. Ploskovni integral druge vrste vektorskega polja
$$\vec{F} : M \longrightarrow \mathbb{R}^3$$
je definiran s predpisom
$$\iint_M \vec{F} \cdot d\vec{S} = \iint_M \vec{F} \cdot \vec{N} \, dS$$

(Predznak integrala je odvisen od smeri orientacije.)
Lahko si mislimo, da ta integral izmeri pretok v.p. $\vec{F}$ skozi $M$.

---

Naj bo $r(u,v)$ regularna parametrizacija $M$. Potem imamo:
$$\vec{N} = \frac{r_u \times r_v}{|r_u \times r_v|}$$

Torej:
$$\iint_M \vec{F} \cdot d\vec{S} = \iint_D \vec{F} \cdot \frac{r_u \times r_v}{|r_u \times r_v|} |r_u \times r_v| \, du \, dv = \iint_D \vec{F} \cdot (r_u \times r_v) \, du \, dv$$

Tudi ta integral ni odvisen od parametrizacije.

## Gaussov in Stokesov izrek

Spomnimo se osnovnega izreka dif. računa:
$$\int_a^b f'(x) \, dx = f(b) - f(a) = \oint_{\partial[a,b]} f(x) \, dx$$

Tudi zadnja enakost dejansko ima matematični smisel: Diferencialna forma.

V matematiki obstajajo večdimenzionalne analogije tega izreka (splošno: Stokesov izrek).

---

### Izrek (Gaussov izrek)

Naj bo $\Omega$ odprta omejena množica v $\mathbb{R}^3$ z odsekoma gladkim robom $\partial\Omega$ (Torej je $\partial\Omega$ odsekoma gladka sklenjena ploskev z orientacijo $\vec{N}$, ki kaže ven iz $\Omega$). Naj bo
$$\vec{F} : \Delta \longrightarrow \mathbb{R}^3$$
vektorsko polje na območju $\Delta \supset \overline{\Omega}$. Potem velja:
$$\iint_{\partial\Omega} \vec{F} \cdot d\vec{S} = \iiint_\Omega \nabla \cdot \vec{F} \, dV$$

**Dokaz (skica):** Naj bo naše območje tako, da ga lahko opišemo z dvema grafoma funkcij za vsako od koord. $(x,y)$, $(x,z)$ in $(y,z)$.

Pišimo $\vec{F} = (X, Y, Z)$. Torej $\nabla \cdot \vec{F} = X_x + Y_y + Z_z$.
Orientacija $\vec{N} = (N_1, N_2, N_3)$.

---

Dokazati moramo:
$$\iint_{\partial\Omega} (X N_1 + Y N_2 + Z N_3) \, dS = \iiint_\Omega (X_x + Y_y + Z_z) \, dV$$

Problem razpade na 3 dele. Dovolj je dokazati enakost za vsako komponento posebej, npr. $Z$:
$$\iint_{\partial\Omega} Z N_3 \, dS = \iiint_\Omega Z_z \, dV$$

Naj bo
$$\Omega = \{ (x,y,z) \in \mathbb{R}^3 : (x,y) \in D, f(x,y) < z < g(x,y) \}$$
kjer sta $f, g : D \longrightarrow \mathbb{R}$ dve zvezni funkciji na območju $D = \pi_z(\Omega)$ (projekcija na $xy$ ravnino).

$L.S. = \iint_{\partial\Omega} Z N_3 \, dS = \iint_{\Gamma_f} Z N_3 \, dS + \iint_{\Gamma_g} Z N_3 \, dS + \iint_{\text{navpični del}} Z N_3 \, dS$

---

Zadnji člen je enak 0, saj je $N_3 = 0$ (ker je normala $N$ pravokotna na navpični del).

Parametriziramo graf $\Gamma_f$:
$$r(x,y) = (x, y, f(x,y)), \quad (x,y) \in D$$
$$r_x = (1, 0, f_x)$$
$$r_y = (0, 1, f_y)$$
$$r_x \times r_y = \begin{vmatrix} i & j & k \\ 1 & 0 & f_x \\ 0 & 1 & f_y \end{vmatrix} = (-f_x, -f_y, 1)$$

Torej (upoštevamo, da spodnja normala kaže navzdol, zato $N_3 \cdot dS = -1 \cdot dx dy$):
$$\iint_{\Gamma_f} Z N_3 \, dS = \iint_D Z(x,y, f(x,y)) \cdot \frac{(r_x \times r_y)_z}{|r_x \times r_y|} \cdot |r_x \times r_y| \, dx \, dy$$
$$= \iint_D Z(x,y, f(x,y)) \cdot (-1) \, dx \, dy$$

Torej:
$$L.S._Z = \iint_D [Z(x,y, g(x,y)) - Z(x,y, f(x,y))] \, dx \, dy \quad (*)$$

---

Na drugi strani:
$$D.S._Z = \iiint_\Omega Z_z \, dV = \iint_D \left( \int_{f(x,y)}^{g(x,y)} Z_z \, dz \right) dx \, dy =$$
$$= \iint_D [Z(x,y, g(x,y)) - Z(x,y, f(x,y))] \, dx \, dy \quad (**)$$

$(*) = (**)$ $\square$

**Primeri:**
1. Naj bo $\Omega = K(0,1)$ enotska krogla, $R=1$.
   Naj bo $\vec{F}(x,y,z) = (x,y,z)$ (radialno v.p.).
   Imamo:
   $$\iint_{\partial\Omega} \vec{F} \cdot d\vec{S} = \iiint_\Omega \nabla \cdot \vec{F} \, dV = 3 V(\Omega) = 4\pi$$

2. $M = \{ (x,y,z) \in \mathbb{R}^3 : x^2 + y^2 = 9, 0 \le z \le 1 \}$ – plašč valja.
   $\vec{F}(x,y,z) = (y^2, z^3, x^2)$. Izračunajmo:
   $$I = \iint_M \vec{F} \cdot d\vec{S}$$

---

Imamo $\nabla \cdot \vec{F} = 0 + 0 + 0 = 0$.
Naj bo $\Omega$ "zapolnjen" valj. Potem je $\partial\Omega = M \cup K_0 \cup K_1$, kjer sta $K_i$ dno in pokrov.
Uporabimo Gaussov izrek:
$$\iint_{\partial\Omega} \vec{F} \cdot d\vec{S} = \iint_M \vec{F} \cdot d\vec{S} + \iint_{K_0} \vec{F} \cdot d\vec{S} + \iint_{K_1} \vec{F} \cdot d\vec{S} = \iiint_\Omega \nabla \cdot \vec{F} \, dV = 0$$

Od tod:
$$\iint_M \vec{F} \cdot d\vec{S} = - \iint_{K_0} \dots - \iint_{K_1} \vec{F} \cdot (0,0,1) \, du \, v = \dots$$

**Posledica (Gaussovega izreka):**
Operator divergence je neodvisen od izbire ortonormirane baze v $\mathbb{R}^3$.

**Dokaz:**
Naj bo $\vec{F} = (U, V, W)$ vektorsko polje v okolici točke $r_0 \in \mathbb{R}^3$. Potem imamo (povprečna vrednost):
$$(\nabla \cdot \vec{F})(r_0) = \left( \frac{\partial U}{\partial x} + \frac{\partial V}{\partial y} + \frac{\partial W}{\partial z} \right)(r_0) = \lim_{\epsilon \to 0} \frac{1}{V(K(r_0, \epsilon))} \iiint_{K(r_0, \epsilon)} \nabla \cdot \vec{F} \, dV =$$
$$= \lim_{\epsilon \to 0} \frac{1}{\frac{4}{3}\pi \epsilon^3} \iint_{S^2(r_0, \epsilon)} \vec{F} \cdot d\vec{S}$$
To ni niti najmanj odvisno na od izbire koord., niti kakšne baze.
(neodvisno od koord. sist.)

---

### Izrek (Greenova formula)

Naj bo $D \subset \mathbb{R}^2$ območje z odsekoma gladkim robom in naj bo $\vec{F}$ odvedljivo vektorsko polje na neki okolici $\overline{D}$.
Potem velja, če je $\vec{F} = (X, Y)$:
$$\oint_{\partial D} X \, dx + Y \, dy = \iint_D (Y_x - X_y) \, dx \, dy$$

**Skica dokaza:**
Dvodimenzionalna verzija Gaussovega izreka se glasi:
$$\oint_{\partial D} \vec{G} \cdot \vec{N} \, ds = \iint_D \nabla \cdot \vec{G} \, dx \, dy \quad (*)$$

---

Če bi namesto normale $\vec{N}$ imeli tangentno $\vec{T}$, bi bil izraz na levi krivuljni integral po $\partial D$.
$\vec{T}$ pridobimo iz $\vec{N}$ z rotacijo za $\frac{\pi}{2}$. Naj bo:
$$R = \begin{pmatrix} 0 & -1 \\ 1 & 0 \end{pmatrix}$$
Potem velja:
$$R \vec{N} = \vec{T} \implies \vec{N} = R^{-1} \vec{T}$$

Poiščimo polje $\vec{H}$, za katero velja:
$$\vec{H} \cdot \vec{T} = \vec{G} \cdot \vec{N}$$
$$\vec{H} \cdot \vec{T} = \vec{G} \cdot R^{-1} \vec{T} = R\vec{G} \cdot \vec{T}$$

Torej, išči polje $\vec{H} = R\vec{G}$.
Torej če $\vec{G} = (U, V)$, je
$$\vec{H} = (-V, U)$$

---

Imamo torej:
$$\oint_{\partial \Omega} \vec{G} \cdot \vec{N} \, ds = \oint_{\partial \Omega} \vec{H} \cdot \vec{T} \, ds = \oint_{\partial \Omega} \vec{H} \cdot d\vec{r} =$$
$$= \oint_{\partial \Omega} (-V \, dx + U \, dy)$$

Na desni strani $(*)$ imamo:
$$\iint_\Omega \nabla \cdot \vec{G} \, dS = \iint_\Omega (U_x + V_y) \, dx \, dy$$

Če za $(U, V)$ vzamemo $(Y, -X)$, res dobimo Greenovo formulo:
$$\oint_{\partial \Omega} X \, dx + Y \, dy = \iint_\Omega \left( \frac{\partial Y}{\partial x} - \frac{\partial X}{\partial y} \right) dx \, dy \quad \square$$