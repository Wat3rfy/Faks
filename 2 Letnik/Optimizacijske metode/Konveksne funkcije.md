
**Dfn.:** Naj bo $D^\text{konv.} \subseteq \mathbb{R}^{n}$  in naj bo $f : D \rightarrow \mathbb{R}$.
Pravimo da je $f$ konveksna funkcija natanko tedaj ko velja

$$\forall x,y \in D, \;\forall \lambda \in [0,1] :$$ $$ f((1-\lambda)x+\lambda y) \leq (1-\lambda)f(x) + \lambda f(y)$$

*Da je to smiselno mora biti celotne daljica v def. območju, zato mora biti $D$ konveksna množica.*

Pravimo da je $f$ strogo konveksna, če velja stroga neenakost.

**Dfn.:** Afina funkcija je $f(x) = a_{1}x_{1}+...+a_{n}x_{n}+b$ *premaknjena linearna funkcija*.

Afina funkcija $f$ je konveksna, še več, tudi $-f$ je konveksna kar pomeni da je $f$ tudi konkavna, torej so afine funkcije konveksne in konkavne hkrati.

*Pri definiciji konkavne funkcije mora definicijisko območje še vedno biti konveksno. Konkavna množica sploh ne obstaja.*

Če je funkcija konveksna in konkavna velja enakost

$$f((1-\lambda)x + \lambda y) = (1-\lambda)f(x) + \lambda f(y)$$

> **Trditev:**
> 
> $f$ je afina $\Leftrightarrow$ $f$ je konveksna in konkavna
> >[!|dokaz]+ Dokaz:
> > 
> > $(\Rightarrow)$
> > Vidimo da je $f((1-\lambda)x + \lambda y) = (1-\lambda)f(x) + \lambda f(y)$
> > 
> > $(\Leftarrow)$
> > Naj bo $b := f(0)$ in $g(x) := f(x)-b$, ki mora biti linearna.
> > 
> > Velja da je $g(0) = 0$.
> > 
> > Z računom preverimo da velja
> > $$g((1-\lambda)x + \lambda y) = (1-\lambda)g(x) + \lambda g(y)$$
> > 
> > Ker je $g(0) = 0$ dobimo
> > $$g((1-\lambda)x) = (1-\lambda)g(x)$$
> > 
> > Velja
> > 
> > $$g(x) = g\left(\frac{1}{\alpha}\alpha x\right)= \frac{1}{\alpha}g(\alpha x)$$
> > $$\Rightarrow \alpha g(x) = g(\alpha x)$$
> > $$\alpha \in [0,\infty)$$
> > 
> > Velja *za $\lambda = \frac{1}{2}$ in $y = -x$*
> > 
> > $$0 = g\left(\frac{1}{2}x + \left(-\frac{1}{2}x\right)\right)= \frac{1}{2}g(x)+ \frac{1}{2}g(-x)$$
> > $$\Rightarrow g(-x) = -g(x)$$
> > 
> > $$\alpha < 0 \Rightarrow g(\alpha x) = g(-(-\alpha x))=-g(-\alpha x)$$
> > 
> > *sedaj je $-\alpha$ pozitivno in ga lahko nesemo ven*
> > 
> > $$-(-\alpha g(x)) = \alpha g(x)$$
> > 
> > Torej velja da je $\alpha g(x) = \alpha g(x) \;;\; \forall \alpha \in \mathbb{R}$
> > 
> > Dokažemo še $g(x+y) = g(x)+g(y)$, *uporabimo $\lambda = \frac{1}{2}$ in $y = y$*
> > 
> > $$g\left(\frac{1}{2}x + \frac{1}{2}y\right)= \frac{1}{2}g(x) + \frac{1}{2}g(y)$$
> > $$g\left(\frac{1}{2}x + \frac{1}{2}y\right)=g\left(\frac{1}{2}(x+y)\right)= \frac{1}{2}g(x+y)$$
> > $$\Rightarrow g(x+y) = g(x)+g(y)$$

Velja da je **norma** na $\mathbb{R}^{n}$ konveksna funkcija.

> **Trditev:** 
> 
> Če je $f: D \rightarrow \mathbb{R}$ konveksna funkcija in $c \geq 0$ velja da je $c \cdot f$ konveksna.
> >[!|dokaz]+ Dokaz:
> >$$c f((1-\lambda)x + \lambda y) \leq c(1- \lambda)f(x) + c \lambda f(y)$$
> >Velja ker je $c \geq 0$.



> **Trditev:** 
> 
> Če sta $f,g : D \rightarrow \mathbb{R}$ konveksni funkciji potem je $f+g$ konveksna funkcija.
> >[!|dokaz]+ Dokaz:
> > Obe neenakosti za $f$ in $g$ lahko seštejmo in dobimo
> >$$f((1 - \lambda)x + \lambda y) + g((1 - \lambda)x + \lambda y)$$
> >$$\le (1 - \lambda)(f(x) + g(x)) + \lambda(f(y) + g(y))$$

> **Trditev:**
> 
> Če je $g : D \rightarrow \mathbb{R}^{n}$ afina *ali celo linearna* je $g(D)$ konveksna. Če je $f: g(D) \rightarrow \mathbb{R}$ konveksna potem je $f \circ g$ konveksna funkcija.
> >[!|dokaz]+ Dokaz:
> > Naj bosta $x,y \in g(D)$
> > 
> > $$x = g(x') = a^{T}x'+ b$$
> > $$y = g(y') = a^{T}y' + b$$
> > 
> > Dobimo
> > 
> > $$(1-\lambda)x + \lambda y =  (1 - \lambda)a^T x' + (1 - \lambda)b + \lambda a^T y' + \lambda b$$
> > $$= a^T((1 - \lambda)x' + \lambda y') + b = g((1 - \lambda)x' + \lambda y')$$
> > 
> > $$f \circ g((1 - \lambda)x + \lambda y) \stackrel{\text{afina}}{=} f((1 - \lambda)g(x) + \lambda g(y))$$
> > $$\underset{f \text{ konv.}}{\le} (1 - \lambda)f(g(x)) + \lambda f(g(y))$$

> **Trditev:** 
> 
> Če je $g : D \mapsto \mathbb{R}$ konveksna in $f: \text{Conv}(g(K)) \mapsto \mathbb{R}$, in je $f$ naraščujoča potem je  $f \circ g$ konveksna funkcija.
> >[!|dokaz]+ Dokaz:
> > Naj bosta $x, y \in D$ in $\lambda \in [0, 1]$.
> > 
> > $$(f \circ g)((1 - \lambda)x + \lambda y) = f(g((1 - \lambda)x + \lambda y))$$
> > 
> > Ker je $g$ konveksna, velja $g((1 - \lambda)x + \lambda y) \le (1 - \lambda)g(x) + \lambda g(y)$. Ker je $f$ naraščujoča, se neenakost ohrani:
> > 
> > $$f(g((1 - \lambda)x + \lambda y)) \underset{\begin{smallmatrix} g \text{ konv.} \\ f \text{ narasc.} \end{smallmatrix}}{\le} f((1 - \lambda)g(x) + \lambda g(y))$$
> > 
> > Uporabimo še konveksnost funkcije $f$:
> > 
> > $$f((1 - \lambda)g(x) + \lambda g(y)) \underset{f \text{ konv.}}{\le} (1 - \lambda)f(g(x)) + \lambda f(g(y))$$
> > 
> > S tem dobimo:
> > $$(f \circ g)((1 - \lambda)x + \lambda y) \le (1 - \lambda)(f \circ g)(x) + \lambda (f \circ g)(y)$$

Produkt konv. funkcij ni konveksen *recimo $x \cdot  -x = -x^{2}$.*

Splošen kompozitum konv. fuinkcij ni konveksen *recimo $-x$ in $x^{2}$ ker dobimo $-x^{2}$.*

Slika konveksne funkcije ni nujno konveksna *recimo neka nezvezna funkcija.*

