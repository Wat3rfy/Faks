

**V. Odvod**



Pogledamo relativno/normalizirano spremembo količine med točkama $x$ in $x+h$. Nato točko $x+h$ pošljemo v $x$.

$$ \text{Naklon} = \frac{f(x+h)-f(x)}{h} $$
To je "limita sekant" oz. zveznic med $(x, f(x))$ in $(x+h, f(x+h))$ ko $h \to 0$.

Infinitezimalno sprememba količine / funkcije $f$ v točki $x$ je po definiciji podana z:
$$ f'(x) := \lim_{h \to 0} \frac{f(x+h)-f(x)}{h}$$
če ta limita obstaja, in se imenuje **odvod** funkcije $f$ v točki $x \in \mathbb{R}$.

>**Odvedljivost funkcije v točki $x$**
>V tem primeru (če $f'(x)$ obstaja) pravimo, da je funkcija $f$ **odvedljiva** v točki $x$. Funkcija je odvedljiva na množici $I \subseteq \mathbb{R}$, če je odvedljiva v vsaki točki iz $I$.


Izrazu $\frac{f(x+h)-f(x)}{h}$ oz. $\frac{f(t)-f(x)}{t-x}$ pravimo **diferenčni kvocient**.



**Definicija**
Denimo, da v točki $x_0$ obstaja $f'(x_0)$. Premica skozi točko $(x_0, f(x_0))$ in z naklonom $f'(x_0)$ se imenuje **tangenta** oz. dotikalnica na graf funkcije $f$ v točki $x_0$.


**Trditev (Pravilo za potence)**
Za poljuben $n \in \mathbb{N}$ so funkcije $f(x)=x^n$ odvedljive v vsaki točki $x \in \mathbb{R}$ in:
$$ f'(x)=nx^{n-1} $$
>[!|dokaz]- Dokaz:
>
> Imamo $f(x+h)-f(x) = (x+h)^n-x^n$. Uporabimo binomski izrek:
> $(x+h)^n = \sum_{k=0}^n \binom{n}{k} x^{n-k} h^k = x^n + nx^{n-1}h + \binom{n}{2} x^{n-2}h^2 + \ldots + h^n$.
> Torej:
> $$ \frac{f(x+h)-f(x)}{h} = \frac{x^n+nx^{n-1}h + \binom{n}{2} x^{n-2}h^2 + \ldots + h^n - x^n}{h} $$
> $$ = nx^{n-1} + \binom{n}{2} x^{n-2}h + \ldots + h^{n-1} $$
> Ko $h \to 0$, vsi členi z $h$ izginejo, ostane le $nx^{n-1}$.
> Alternativa: $\frac{t^n-x^n}{t-x} = t^{n-1}+t^{n-2}x+\ldots+x^{n-1} \to nx^{n-1}$ ko $t \to x$.

**Trditev (Odvod trigonometričnih funkcij)**

$\sin' x = \cos x$
$\cos' x = -\sin x$
>[!|dokaz]- Dokaz:
>
> Naj bo $f(x) = \sin x$. Tedaj je:
> $$ \frac{f(x+h)-f(x)}{h} = \frac{\sin(x+h)-\sin x}{h} $$
> Uporabimo adicijski izrek $\sin(x+h) = \sin x \cos h + \cos x \sin h$:
> $$ = \frac{\sin x \cos h + \cos x \sin h - \sin x}{h} = \sin x \frac{\cos h - 1}{h} + \cos x \frac{\sin h}{h} $$
> Izračunali smo limite (prej v L'Hôpitalovem pravilu):
> $\lim_{h \to 0} \frac{\cos h - 1}{h} = 0$
> $\lim_{h \to 0} \frac{\sin h}{h} = 1$
> Sledi $f'(x) = \sin x \cdot 0 + \cos x \cdot 1 = \cos x$.
> Podobno dokažemo $(\cos x)' = -\sin x$.

**Trditev (Odvod eksponentne funkcije)**
Naj bo $a>0$ in $f(x) = a^x$. Tedaj $f'(x) = a^x \log a$.
Na kratko: $(a^x)' = a^x \log a$.
**Dokaz** z verižnim pravilom.



**Izrek (Zveznost odvedljive funkcije)**
Če je $f$ odvedljiva v točki $x \in \mathbb{R}$, je tam tudi zvezna.
**Dokaz**
Velja:
$$ f(x+h) - f(x) = \frac{f(x+h)-f(x)}{h} \cdot h $$
Ko $h \to 0$, $\frac{f(x+h)-f(x)}{h} \to f'(x)$ (če obstaja) in $h \to 0$.
Torej $f(x+h)-f(x) \to f'(x) \cdot 0 = 0$ ko $h \to 0$.
Kar implicira zveznost v točki $x$.



**Povzetek:**
*   Odvedljivost $\Rightarrow$ Zveznost
*   Zveznost = Nepretrganost
*   Odvedljivost = Gladkost

>**Izrek (Pravila za odvajanje vsote, razlike, produkta in kvocienta)**
Naj bosta $f, g$ odvedljivi v točki $x \in \mathbb{R}$. Tedaj so tudi funkcije $f+g, f-g, fg, f/g$ odvedljive in velja:
>
$(f \pm g)' = f' \pm g'$
$(fg)' = f'g+fg'$ (**Leibnizovo pravilo**)
$(f/g)' = \frac{f'g-fg'}{g^2}$ (če $g(x) \neq 0$)


>[!|hide]- **Dokaz vsote**
> $$ (f+g)'(x) = \lim_{h \to 0} \frac{(f+g)(x+h)-(f+g)(x)}{h} $$
> $$ = \lim_{h \to 0} \frac{[f(x+h)+g(x+h)]-[f(x)+g(x)]}{h} $$
> $$ = \lim_{h \to 0} \left[ \frac{f(x+h)-f(x)}{h} + \frac{g(x+h)-g(x)}{h} \right] $$
> $$ = f'(x)+g'(x) $$
> Enako za $f-g$.

>[!|hide]- **Dokaz produkta**
> $$ (fg)'(x) = \lim_{h \to 0} \frac{(fg)(x+h)-(fg)(x)}{h} = \frac{f(x+h)g(x+h)-f(x)g(x)}{h} $$
> Dodamo in odštejemo $f(x)g(x+h)$ v števcu:
> $$ = \lim_{h \to 0} \frac{f(x+h)g(x+h)-f(x)g(x+h)+f(x)g(x+h)-f(x)g(x)}{h} $$
> $$ = \lim_{h \to 0} \left[ \frac{f(x+h)-f(x)}{h} g(x+h) + f(x) \frac{g(x+h)-g(x)}{h} \right] $$
> Ker je $g$ odvedljiva v $x$, je tam tudi zvezna, zato $g(x+h) \to g(x)$ ko $h \to 0$.
> Posledično smo dobili:
> $$ (fg)'(x) = f'(x)g(x) + f(x)g'(x) $$

>[!|hide]- **Dokaz kvocienta**
> $$ (f/g)'(x) = \lim_{h \to 0} \frac{(f/g)(x+h)-(f/g)(x)}{h} = \lim_{h \to 0} \frac{\frac{f(x+h)}{g(x+h)}-\frac{f(x)}{g(x)}}{h} $$
> $$ = \lim_{h \to 0} \frac{f(x+h)g(x)-f(x)g(x+h)}{h g(x+h)g(x)} $$
> Dodamo in odštejemo $f(x)g(x)$ v števcu:
> $$ = \lim_{h \to 0} \frac{f(x+h)g(x)-f(x)g(x)+f(x)g(x)-f(x)g(x+h)}{h g(x+h)g(x)} $$
> $$ = \lim_{h \to 0} \frac{\frac{f(x+h)-f(x)}{h}g(x) - f(x)\frac{g(x+h)-g(x)}{h}}{g(x+h)g(x)} $$
> $$ = \frac{f'(x)g(x)-f(x)g'(x)}{g(x)^2} $$

>[!|hide]- **Primer - Odvod tangensa**
> Naj bo $f(x) = \operatorname{tg} x = \frac{\sin x}{\cos x}$. Tedaj je:
> $$ f'(x) = \frac{(\sin x)' \cos x - \sin x (\cos x)'}{\cos^2 x} = \frac{\cos x \cos x - \sin x (-\sin x)}{\cos^2 x} $$
> $$ = \frac{\cos^2 x + \sin^2 x}{\cos^2 x} = \frac{1}{\cos^2 x} $$
> Dokazali smo: $\operatorname{tg}' x = \frac{1}{\cos^2 x}$.

>**Izrek : Verižno pravilo**
Naj bo $f$ odvedljiva v točki $x$ in $g$ odvedljiva v točki $f(x)$. Tedaj je njun kompozitum $g \circ f$ odvedljiv v točki $x$ in velja:
$$ (g \circ f)'(x) = g'(f(x)) \cdot f'(x) $$
>
> >[!|hide]- **Dokaz Verižnega Pravila**
> > 
> > 
> > Odvod kompozituma $(f \circ g)(x) = f(g(x))$ v točki $x$ je po definiciji:
> > 
> > $$ (f \circ g)'(x) = \lim_{h \to 0} \frac{f(g(x+h)) - f(g(x))}{h} $$
> > 
> > Izraz prepišemo z množenjem in deljenjem z $g(x+h) - g(x)$ (predpostavimo, da je $g(x+h) - g(x) \ne 0$ za majhne $h \ne 0$):
> > 
> > $$ (f \circ g)'(x) = \lim_{h \to 0} \left( \frac{f(g(x+h)) - f(g(x))}{g(x+h) - g(x)} \cdot \frac{g(x+h) - g(x)}{h} \right) $$
> > 
> > Ker obe limiti obstajata, lahko limito produkta zapišemo kot produkt limit:
> > 
> > $$ (f \circ g)'(x) = \left( \lim_{h \to 0} \frac{f(g(x+h)) - f(g(x))}{g(x+h) - g(x)} \right) \cdot \left( \lim_{h \to 0} \frac{g(x+h) - g(x)}{h} \right) $$
> > 
> > Druga limita je po definiciji odvod $g$ v točki $x$, torej $g'(x)$
> > Za prvo limito opazimo, da ko $h \to 0$, se zaradi zveznosti funkcije $g$ tudi količina $g(x+h) - g(x)$ približuje $0$. Če torej označimo $u = g(x)$, je ta prva limita enaka $\lim_{\Delta u \to 0} \frac{f(u + \Delta u) - f(u)}{\Delta u}$, kar je po definiciji odvod $f$ v točki $u=g(x)$, torej $f'(g(x))$.
> > Sledi:
> > 
> > $$ (f \circ g)'(x) = f'(g(x)) \cdot g'(x) $$




>**Izrek (Odvod inverza)**
> Naj bo $f$ strogo monotona na okolici točke $x \in \mathbb{R}$. Označimo z $f^{-1}$ njen (lokalni) inverz. Če je $f$ odvedljiva in $f'(x) \neq 0$, tedaj je tudi $f^{-1}$ odvedljiva v $t = f(x)$ in velja:
> $$ (f^{-1})'(t) = \frac{1}{f'(f^{-1}(t))} $$
> 
> >[!|hide]- **Dokaz**
> > Odvod inverzne funkcije v točki $y_0$ je po definiciji:
> > $$ (f^{-1})'(y_0) = \lim_{h \to 0} \frac{f^{-1}(y_0+h) - f^{-1}(y_0)}{h} $$
> > Naj bo $x_0 = f^{-1}(y_0)$, torej $y_0 = f(x_0)$.
> > Definirajmo $k$ tako, da bo $x_0+k = f^{-1}(y_0+h)$. Iz tega sledi $y_0+h = f(x_0+k)$.
> > Potem je $h = f(x_0+k) - y_0 = f(x_0+k) - f(x_0)$.
> > 
> > Ker je $f$ strogo monotona in zvezna, je tudi $f^{-1}$ zvezna. Ko $h \to 0$, $y_0+h \to y_0$, kar zaradi zveznosti $f^{-1}$ pomeni, da $f^{-1}(y_0+h) \to f^{-1}(y_0)$. Torej, $x_0+k \to x_0$, kar implicira $k \to 0$.
> > 
> > Diferenčni kvocient lahko sedaj prepišemo kot:
> > $$ \frac{f^{-1}(y_0+h) - f^{-1}(y_0)}{h} = \frac{(x_0+k) - x_0}{f(x_0+k) - f(x_0)} = \frac{k}{f(x_0+k) - f(x_0)} = \frac{1}{\frac{f(x_0+k) - f(x_0)}{k}} $$
> > Zato je:
> > $$ (f^{-1})'(y_0) = \lim_{h \to 0} \frac{1}{\frac{f(x_0+k) - f(x_0)}{k}} $$
> > Ker $h \to 0 \implies k \to 0$, lahko limito spremenimo:
> > $$ (f^{-1})'(y_0) = \lim_{k \to 0} \frac{1}{\frac{f(x_0+k) - f(x_0)}{k}} $$
> > Ker je $f'(x_0) \neq 0$, lahko limito prenesemo v imenovalec:
> > $$ (f^{-1})'(y_0) = \frac{1}{\lim_{k \to 0} \frac{f(x_0+k) - f(x_0)}{k}} = \frac{1}{f'(x_0)} $$
> > Ker je $x_0 = f^{-1}(y_0)$, lahko končni rezultat zapišemo tudi kot:
> > $$ (f^{-1})'(y_0) = \frac{1}{f'(f^{-1}(y_0))} $$

>[!|hide]- **Primeri**
> 1.) $(\arcsin x)'$
> $f(y)=\sin y$. $f^{-1}(x)=\arcsin x$. $f'(y)=\cos y$.
> $y = \arcsin x$. $(\arcsin x)' = \frac{1}{\cos(\arcsin x)} = \frac{1}{\sqrt{1-\sin^2(\arcsin x)}} = \frac{1}{\sqrt{1-x^2}}$.
> (Velja za $y \in [-\pi/2, \pi/2]$)
> 
> 2.) $(\operatorname{arctg} x)' = \frac{1}{1+x^2}$.
> Uporabimo: $\operatorname{arctg} = (\operatorname{tg}|_{(-\pi/2, \pi/2)})^{-1}$.
> 
> 3.) $(\log x)' = \frac{1}{x}$.
> Uporabimo: $\log = \exp^{-1}$.
> 
> 4.) $(x^\alpha)' = \alpha x^{\alpha-1}$ za $\forall \alpha \in \mathbb{R}, x>0$.
> Najprej dokažemo zvezo za $\alpha=1/n$, kjer je $n \in \mathbb{N}$, z uporabo inverza: $f(x)=x^n \implies f^{-1}(x)=\sqrt[n]{x}$.
> V naslednjem koraku funkcijo $g(x) = x^{m/n}$ zapišemo kot kompozitum naravne potence in korena. Tako zvezo dokažemo za $\alpha \in \mathbb{Q}$.



**Diferencial**


Naj bo $f$ diferencijabilna v točki $a \in \mathbb{R}$. **Diferencial** funkcije $f$ v točki $a$ je linearna preslikava (linearni funkcional) $df(a): \mathbb{R} \rightarrow \mathbb{R}$, definirana z zahtevo:
$$ \lim_{h \to 0} \frac{|f(a+h)-f(a)-df(a)(h)|}{|h|} = 0 $$


**Trditev**
Funkcija $f$ je diferencijabilna v točki $a$ ($\iff$ diferencial obstaja) $\iff$ je odvedljiva pri $a$. V tem primeru je:
$$ df(a)(h) = f'(a)h $$
Torej je $df(a)$ diferencial s predpisom $h \mapsto f'(a)h$.

**Dokaz**
Pišimo $df(a)(h) = \lambda h$ (če naj $df(a)$ obstaja, mora biti te oblike).
Sledi:
$$ \lim_{h \to 0} \frac{|f(a+h)-f(a)-\lambda h|}{|h|} = 0 $$
$$ \iff \lim_{h \to 0} \left| \frac{f(a+h)-f(a)}{h} - \lambda \right| = 0 $$
Ta izraz pa ima limito $0$ pri $h \to 0$ natanko tedaj, ko je $\lambda = f'(a)$.
To je, $f(a+h) \approx f(a) + f'(a)h$. (2)


>[!|hide]- **Primer (približni izračun z diferencialom)**
>  
> Želimo približno izračunati $\sqrt{2}$. Uporabimo formulo (2):
> $f(x) = \sqrt{x}$
> $a+h = 2$.
> Ker je $f'(x) = \frac{1}{2\sqrt{x}}$, iz (2) dobimo:
> $$ \sqrt{a+h} \approx \sqrt{a} + \frac{1}{2\sqrt{a}}h $$
> oz.
> $$ \sqrt{2} \approx \sqrt{a} + \frac{1}{2\sqrt{a}}(2-a) = \frac{2a+(2-a)}{2\sqrt{a}} = \frac{a+2}{2\sqrt{a}} \quad (3) $$
> Za $a$ vzamemo točko, ki je blizu točke $2$ in v kateri znamo izračunati $\sqrt{a}$. Izberemo tri možnosti:
> (i) $a=1$. Iz (3) dobimo $\sqrt{2} \approx \frac{1+2}{2\sqrt{1}} = \frac{3}{2} = 1.5$.
> Test: $(3/2)^2 = 2.25$. Napaka: $f(a+h)-f(a) \approx \frac{1}{4}$.
> (ii) $a=1.96$. Iz (3) dobimo $\sqrt{2} \approx \frac{1.96+2}{2\sqrt{1.96}} = \frac{3.96}{2 \cdot 1.4} = \frac{3.96}{2.8} = \frac{396}{280} = \frac{99}{70} \approx 1.4142857$.
> Test: $(99/70)^2 = \frac{9801}{4900} \approx 2.000204$. Napaka: $\frac{1}{4900}$.
> (iii) $a=2.25$. Iz (3) dobimo $\sqrt{2} \approx \frac{2.25+2}{2\sqrt{2.25}} = \frac{4.25}{2 \cdot 1.5} = \frac{4.25}{3} = \frac{17}{12} \approx 1.4166667$.
> Test: $(17/12)^2 = \frac{289}{144} \approx 2.0069$. Napaka: $\frac{1}{144}$.


**Lagrangeov izrek in posledice**


**Izrek (Lagrange)**
Naj bo $f: [a,b] \rightarrow \mathbb{R}$ zvezna in odvedljiva na $(a,b)$. Tedaj obstaja $\xi \in (a,b)$ takšen, da:
$$ f(b) - f(a) = f'(\xi) (b-a) $$


**Izpostavimo poseben primer, ko je $f(a) = f(b)$:**

**Izrek (Rolle)**
Naj bo $f: [a,b] \rightarrow \mathbb{R}$ zvezna, odvedljiva na $(a,b)$ in naj bo $f(a) = f(b)$. Tedaj obstaja $\xi \in (a,b)$ takšen, da:
$$ f'(\xi)=0 $$

>[!|dokaz]+ Dokaz:
> Ker je $f$ zvezna na zaprtem intervalu $[a,b]$, po izreku o ekstremnih vrednostih (Weierstrassov izrek) doseže svoj minimum $m$ in maksimum $M$ na $[a,b]$.
> 
> 
> 1.   $m=M$.
>     Moramo imeti konstantno funkcijo ker sta minimum in maximum enaka.
> 
> 2.  $m < M$.
>     V tem primeru funkcija $f$ ni konstantna. Ker je $f(a)=f(b) = 0$, in ker $m < M$, absolutni minimum in absolutni maksimum ne moreta biti oba dosežena samo v krajiščih $a$ in $b$. To pomeni, da mora biti vsaj eden izmed ekstremov dosežen v notranjosti intervala $(a,b)$.
>     
>     Torej obstaja točka $\xi \in (a,b)$, v kateri $f$ doseže lokalni ekstrem.
> 
>     Brez izgube splošnosti predpostavimo, da $f$ doseže lokalni maksimum v točki $\xi \in (a,b)$. To pomeni, da za dovolj majhne $h \ne 0$ velja $f(\xi+h) \le f(\xi)$, kar implicira $f(\xi+h) - f(\xi) \le 0$.
>     *   Če je $h > 0$: $\frac{f(\xi+h) - f(\xi)}{h} \le 0$. Zato je $\lim_{h \to 0^+} \frac{f(\xi+h) - f(\xi)}{h} \le 0$.
>     *   Če je $h < 0$: $\frac{f(\xi+h) - f(\xi)}{h} \ge 0$ (saj delimo negativen števec z negativnim imenovalcem). Zato je $\lim_{h \to 0^-} \frac{f(\xi+h) - f(\xi)}{h} \ge 0$.
>     Ker je $f$ odvedljiva v $\xi$, mora odvod $f'(\xi)$ obstajati, kar pomeni, da morata biti leva in desna limita enaki. Edina možnost, da je $f'(\xi) \le 0$ in hkrati $f'(\xi) \ge 0$, je $f'(\xi)=0$.
> 

>[!|dokaz]- Dokaz Lagrengevega izreka:
>
> Definirajmo pomožno funkcijo $h(x)$ kot:
> $$ h(x) = f(x) - \frac{f(b)-f(a)}{b-a}(x-a) $$
> Izračunajmo vrednosti $h(x)$ na krajiščih intervala:
> $h(a) = f(a) - \frac{f(b)-f(a)}{b-a}(a-a) = f(a)$.
> $h(b) = f(b) - \frac{f(b)-f(a)}{b-a}(b-a) = f(b) - (f(b)-f(a)) = f(a)$.
> Torej velja $h(a)=h(b)$.
> 
> Ker je $f$ zvezna na $[a,b]$ in odvedljiva na $(a,b)$, in ker je izraz $\frac{f(b)-f(a)}{b-a}(x-a)$ linearna funkcija (zvezna in odvedljiva povsod), je tudi funkcija $h(x)$ zvezna na $[a,b]$ in odvedljiva na $(a,b)$.
> 
> Po Rolleovem izreku, saj $h(a)=h(b)$, obstaja vsaj eno število $\xi \in (a,b)$, za katerega je $h'(\xi)=0$.
> Izračunajmo odvod $h'(x)$:
> $$ h'(x) = f'(x) - \frac{f(b)-f(a)}{b-a} $$
> Ker je $h'(\xi)=0$, sledi:
> $$ f'(\xi) - \frac{f(b)-f(a)}{b-a} = 0 $$
> Kar preuredimo v:
> $$ f'(\xi) = \frac{f(b)-f(a)}{b-a} $$
> S tem je izrek dokazan.


**Posledica Lagrangeovega izreka (Lipschitzova funkcija)**
Neposredno iz Lagrangeovega izreka dobimo naslednji rezultat.
Če je $f: (a,b) \rightarrow \mathbb{R}$ odvedljiva in ima omejen odvod, tedaj je $f$ **Lipschitzova** (in posledično enakomerno zvezna), to je, $\exists M > 0$ takšen, da za $\forall x, y \in (a,b)$ velja:
$$ |f(x)-f(y)| \le M|x-y| $$
V podobnem to velja, če je $f$ zvezno odvedljiva na $[a,b]$.

**Posledica (o monotonosti funkcije in predznaku odvoda)**
Naj bo $I \subseteq \mathbb{R}$ odprt interval in $f: I \rightarrow \mathbb{R}$ odvedljiva. Tedaj je:
(1) $f$ naraščajoča na $I \iff f'(x) \ge 0$ na $I$
(2) $f$ padajoča na $I \iff f'(x) \le 0$ na $I$
(1') $f$ strogo naraščajoča na $I \impliedby f'(x) > 0$ na $I$
(2') $f$ strogo padajoča na $I \impliedby f'(x) < 0$ na $I$

**Dokaz**
Vse implikacije "$\impliedby$" sledijo neposredno iz Lagrangeovega izreka, saj če sta $x, y \in I, x<y$, tedaj je (za neko $\xi \in (x,y)$):
$$ f(y) - f(x) = f'(\xi) (y-x) $$
Ker je $y-x > 0$, je predznak $f(y)-f(x)$ enak predznaku $f'(\xi)$.

Dokažemo še "$\implies$" iz (1) & (2): to sledi iz definicije odvoda:
$$ f'(u) = \lim_{s \to u} \frac{f(s)-f(u)}{s-u} $$
Podobno kot v dokazu Rolleovega izreka.

Da v (1') & (2') implikacija "$\implies$" ne velja, pokažeta npr. funkciji $f(x)=x^3$ (kjer $f'(0)=0$ a $f$ je strogo nar.) in $f(x)=-x^3$ (kjer $f'(0)=0$ a $f$ je strogo pad.).

**Posledica (Konstantnost funkcije)**
Če je $I \subseteq \mathbb{R}$ odprt interval in $f: I \rightarrow \mathbb{R}$ odvedljiva ter $f'(x) = 0$ za vsak $x \in I$, tedaj je $f$ konstanta na $I$.
**Dokaz:** Ker je $f'(x) \ge 0$, je $f$ naraščajoča. Ker je $f'(x) \le 0$, je $f$ padajoča. Sledi $f = \operatorname{const}$ na $I$.

---

**Konveksnost**

>[!|hide]- Geometrijska lastnost
> *   **konveksnost** $\equiv$ vse tetive so nad grafom
> *   **konkavnost** $\equiv$ vse tetive so pod grafom
> 


**Konveksnost - 1. karakterizacija ($\varphi$)**
Naj bo $I \subseteq \mathbb{R}$ interval in $f: I \rightarrow \mathbb{R}$. Funkcija $f$ je **konveksna**, če za $\forall a, b \in I$ velja:

$$ $$
$$ x \in (a,b) \implies f(x) \le f(a) + \frac{f(b)-f(a)}{b-a}(x-a) \quad (1) $$
$$ $$

Funkcija $f$ je **konkavna**, če v zgornji neenakosti vzamemo $\ge$.

Lastnost (1) očitno lahko napišemo kot:


$$ $$
$$ \frac{f(x)-f(a)}{x-a} \le \frac{f(b)-f(a)}{b-a} \quad \forall x: a < x < b \quad (2) $$
$$ $$


To pomeni, da diferenčni kvocienti naraščajo kot funkcija desnega krajišča (ali padajo kot funkcija levega krajišča).

Daljico $[a,b]$ lahko zapišemo kot:
$$[a,b] = \{ a + (b-a)t \,;\; t \in [0,1]\}$$
To imenujemo **konveksna kombinacija**.
Od tod sledi, da (1) lahko ekvivalentno formuliramo kot:

$$ $$
$$ f(a + (b-a)t) \le f(a) + (f(b)-f(a))t \quad \forall t \in (0,1) \quad (3) $$
$$ $$

Videli bomo, da je konveksna funkcija vedno zvezna. Če pa vnaprej vemo, da je $f$ zvezna, tedaj je pogoj konveksnosti v obliki (3) dovolj preverjati za $t=1/2$:

**Trditev**
Naj bo $I \subseteq \mathbb{R}$ interval in $f: I \rightarrow \mathbb{R}$ zvezna. Tedaj je $f$ konveksna $\iff$ na $\forall x, y \in I$ je:
$$ f\left(\frac{x+y}{2}\right) \le \frac{f(x)+f(y)}{2} \quad (4) $$
**Dokaz**

**$(\implies)$**
Predpostavimo, da je funkcija $f$ konveksna. Po definiciji konveksnosti velja $f((1-t)x + ty) \le (1-t)f(x) + tf(y)$ za vse $x,y \in I$ in $t \in [0,1]$. Za $t=1/2$ neposredno dobimo:
$$ f\left(\frac{x+y}{2}\right) \le \frac{f(x)+f(y)}{2} $$
S tem je smer $(\implies)$ dokazana.

**$(\impliedby)$**
Predpostavimo, da je funkcija $f$ zvezna na $I$ in da velja neenakost (4) za vse $x, y \in I$.
Z indukcijo se lahko pokaže, da iz neenakosti (4) sledi splošna neenakost konveksnosti $f((1-t)x+ty) \le (1-t)f(x)+tf(y)$ za vse dyadične racionalne vrednosti $t = m/2^n$, kjer $n \in \mathbb{N}$ in $m \in \{0, 1, \ldots, 2^n\}$. Osnovni primer za $n=1$ (tj. $t=1/2$) drži po predpostavki (4). Induktivni korak za $t=\frac{m}{2^{n+1}}$ se izvede z uporabo (4) na sredini dveh že dokazanih dyadičnih točk.
Ker so dyadična racionalna števila gosta v intervalu $[0,1]$, lahko za vsak $t \in [0,1]$ najdemo zaporedje dyadičnih števil $(t_k)_{k \in \mathbb{N}}$ takšno, da $t_k \to t$ ko $k \to \infty$. Ker neenakost velja za vsak $t_k$:
$$ f((1-t_k)x+t_ky) \le (1-t_k)f(x)+t_kf(y) $$
Zaradi zveznosti funkcije $f$ in zveznosti linearne funkcije se neenakost ohrani pri limitiranju, ko $k \to \infty$:
$$ f((1-t)x+ty) \le (1-t)f(x)+tf(y) $$
S tem je dokazano, da je $f$ konveksna funkcija.


<br><br>

Potrebujemo bolj praktičen pogoj. Pišimo:
$$ g_a(x) = \frac{f(x)-f(a)}{x-a} \quad \forall a \in I, x \neq a $$
Pogoj (2) se torej glasi $g_a(x) \le g_a(b)$, za $a < x < b$. Torej je $g_a$ naraščajoča funkcija na $(a, \infty) \cap I$.
Ker lahko (1) napišemo tudi kot:
$$ f(x) \le f(b) + \frac{f(b)-f(a)}{b-a}(x-b) \quad \forall a<x<b $$
oz.
$$ \frac{f(x)-f(b)}{x-b} \ge \frac{f(a)-f(b)}{a-b} \quad (5) $$
je $g_b(x)$ naraščajoča tudi na $(-\infty, b) \cap I$.

**Povzetek:** Za vsak $a \in I$ je funkcija $g_a: I \setminus \{a\} \rightarrow \mathbb{R}$, definirana z $g_a(x) := \frac{f(x)-f(a)}{x-a}$, naraščajoča na $I \setminus \{a\}$.

**Posledica (Enostranski odvodi in monotonost)**
Naj bo $f$ konveksna na odprtem intervalu $I$. Za vsak $a \in I$ obstajata:
*   $(D_+f)(a) = \lim_{x \to a^+} g_a(x) = \inf_{x \in I, x>a} g_a(x)$ (desni odvod funkcije $f$ v točki $a$)
*   $(D_-f)(a) = \lim_{x \to a^-} g_a(x) = \sup_{x \in I, x<a} g_a(x)$ (levi odvod funkcije $f$ v točki $a$)
Funkciji $D_-f, D_+f$ sta naraščajoči na $I$.
**Dokaz:** Obstoj $D_-f, D_+f$ sledi neposredno iz monotonosti $g_a$.
Vz. $x_1 < x_2 < x$. Iz (2) sledi $g_{x_1}(x) \le g_{x_2}(x)$. Ker je $g_s(t)=g_t(s)$, lahko to neenakost zapišemo kot:
$$ g_x(x_1) \le g_x(x_2) \quad \forall x_1 < x_2 < x $$
Sledi:
$$ \inf_{x \in I, x>x_1} g_x(x_1) \le \inf_{x \in I, x>x_2} g_x(x_2) $$
Torej $(D_+f)(x_1) \le (D_+f)(x_2)$.
Podobno dokažemo, da je $D_-f$ naraščajoča.

**Posledica (Konveksnost implicira zveznost)**
Konveksna funkcija je nujno zvezna.
**Dokaz:** Za $x \in I \setminus \{a\}$ je $f(x) = g_a(x)(x-a) + f(a)$. Sledi: $f(a+0)=f(a-0)=f(a)$, kar pomeni, da je zvezna v točki $a$.

**Primer (Konveksna funkcija ni nujno odvedljiva):**
$f(x)=|x|$ je konveksna na $\mathbb{R}$, ni pa odvedljiva v točki $0$.

**Konveksnost - 2. karakterizacija ($f'$)**

**Trditev**
Če je konveksna funkcija $f$ odvedljiva, tedaj $f'$ narašča.
**Dokaz:** Sledi neposredno iz posledice o $D_+f, D_-f$. Ker je $f$ odvedljiva, je $f'(x) = D_+f(x) = D_-f(x)$. Ker sta $D_+f$ in $D_-f$ naraščajoči, je tudi $f'$ naraščajoča.

**Izrek**
Naj bo $I \subseteq \mathbb{R}$ odprt interval in $f: I \rightarrow \mathbb{R}$ odvedljiva. Tedaj:
$f$ konveksna $\iff f'(x)$ naraščajoča na $I$.
$f$ konkavna $\iff f'(x)$ padajoča na $I$.

**Dokaz**
$(\implies)$ Sledi iz (2) & (5).
$(\impliedby)$ Vz. $a,b \in I$ ter $t \in [0,1]$. Pišimo $c = (1-t)a+tb$.
Velja:
$f(a) \ge f(c) + f'(c)(a-c)$ (ker $f'$ narašča, je $f'(c) \ge f'(\xi)$ za $\xi < c$)
$f(b) \ge f(c) + f'(c)(b-c)$
Pomnožimo prvo z $(1-t)$ in drugo s $t$:
$(1-t)f(a) \ge (1-t)f(c) + (1-t)f'(c)(a-c)$
$tf(b) \ge tf(c) + tf'(c)(b-c)$
Seštejemo neenakosti:
$(1-t)f(a)+tf(b) \ge f(c) + f'(c)((1-t)(a-c)+t(b-c))$
Ker je $(1-t)(a-c)+t(b-c) = (1-t)a-(1-t)c+tb-tc = (1-t)a+tb-c = c-c=0$, sledi:
$$ (1-t)f(a)+tf(b) \ge f(c) $$
kar je ravno formulacija (3) konveksnosti.

---

**Konveksnost - 3. karakterizacija ($f''$)**

**Izrek**
Naj bo $f$ dvakrat odvedljiva. Tedaj je:
$f$ konveksna $\iff f''(x) \ge 0$.
$f$ konkavna $\iff f''(x) \le 0$.
(Natančneje: $I$ odprt interval, $f: I \rightarrow \mathbb{R}$. $f$ konv./konk. na $I \iff f'' \ge 0 / \le 0$ na $I$).

**Dokaz**
$(\implies)$ Sledi iz zadnje trditve (konveksnost $\iff f'$ narašča) in posledice o monotonosti funkcije in predznaku odvoda ($f'$ narašča $\iff f'' \ge 0$).
$(\impliedby)$ Vz. $x, a \in I$. Po Lagr. izreku je:
$f(x)-f(a) = f'(\xi)(x-a)$ za neki $\xi$ med $x$ in $a$.
Iz privzetka o $f'' \ge 0$ sledi, da $f'$ narašča.
Če je $x > \xi > a$, tedaj je $f'(\xi) \ge f'(a)$, zato $f'(\xi)(x-a) \ge f'(a)(x-a)$, saj je $x-a > 0$.
Če pa je $x < \xi < a$, tedaj je $f'(\xi) \le f'(a)$, zato je spet $f'(\xi)(x-a) \ge f'(a)(x-a)$, saj je $x-a < 0$.
Analogno obravnavamo konkavnost.

---

**Stroga konveksnost**

**Definicija & Izrek**
Funkcija $f: I \rightarrow \mathbb{R}$ je **strogo konveksna**, če:
(i) $f((1-t)x+ty) < (1-t)f(x)+tf(y) \quad \forall x,y \in I, x \neq y, t \in (0,1)$.
Ekvivalentno, če je:
(ii) za vsak $a \in I$ funkcija $g_a(x) = \frac{f(x)-f(a)}{x-a}$ strogo naraščajoča na $I \setminus \{a\}$.
Če je $f$ odvedljiva, je to ekvivalentno temu, da:
(iii) $f'$ strogo narašča na $I$.
Kar je ekvivalentno pogoju:
(iv) $f(x) > f(a) + f'(a)(x-a) \quad \forall x,a \in I, x \neq a$.
Če je $f$ dvakrat odvedljiva, je to ekvivalentno:
(v) $f''(x) > 0 \quad \forall x \in I$.
Za strogo konkavnost obrnemo vse predznake.

**Dokaz (i) $\iff$ (ii)**
Pogoj (ii) pomeni $g_a(x)$ je strogo naraščajoča. To je:
$\frac{f(x)-f(a)}{x-a} < \frac{f(b)-f(a)}{b-a} \quad \forall a<x<b$. (Iz (2) z ostro neenakostjo).
To je ekvivalentno: $f(x) < f(a) + \frac{f(b)-f(a)}{b-a}(x-a)$.
Kar je ekvivalentno (i) z $t = (x-a)/(b-a)$. Torej sta (i) in (ii) ekvivalentna.

**Dokaz (ii) $\implies$ (iii)**
Vz. $x_1, x_2 \in I$ takšna, da $x_1 < x_2$. Sledi $(D_+f)(x_1) < (D_+f)(x_2)$.
Torej $D_+f$ strogo narašča.
Ker je $f$ odvedljiva, je $D_+f = f'$ in zato $f'(x_1) < f'(x_2)$.
Torej $f'$ strogo narašča.

**Dokaz (iii) $\implies$ (ii)**
Velja $f'$ strogo narašča $\implies g_a(x)$ strogo narašča na $\forall a \in I$.
Če $g_a$ ne bi strogo naraščala, bi obstajali $a \in I$, $b, c \in I \setminus \{a\}$ takšni, da $a < b < c$ in $g_a(b) \ge g_a(c)$ (ali $g_a(b) = g_a(c)$).
To bi pomenilo, da obstajata dve točki z enakim diferenčnim kvocientom glede na $a$.
$$ \frac{f(b)-f(a)}{b-a} \ge \frac{f(c)-f(a)}{c-a} $$
Tedaj ima funkcija $h(x) := f(x) - \left[ f(a) + \frac{f(c)-f(a)}{c-a}(x-a) \right]$ (funkcija $f$ minus tetiva med $a$ in $c$) ničle v $a, c$.
Če bi bila $g_a(b) = g_a(c)$, bi imela tudi $h(b)$ ničlo, saj bi bila točka $b$ na tetivi.
Po Rolleovem izreku torej obstajata $\xi_1, \xi_2 \in (a,c)$ takšni, da $h'(\xi_1)=0$ in $h'(\xi_2)=0$.
To pomeni $f'(\xi_1) = \frac{f(c)-f(a)}{c-a}$ in $f'(\xi_2) = \frac{f(c)-f(a)}{c-a}$.
Torej $f'(\xi_1) = f'(\xi_2)$ za $\xi_1 \ne \xi_2$. To pa je v nasprotju s strogo monotonostjo $f'$. Torej $g_a$ strogo narašča na $\forall a \in I$.

**Dokaz (iii) $\implies$ (iv)**
Velja $f(x)-f(a) = f'(\xi)(x-a)$ za neki $\xi$ med $x$ in $a$.
Če je $x > a$, je $f'(\xi) > f'(a)$ (ker $f'$ strogo narašča). Zato $f'(\xi)(x-a) > f'(a)(x-a)$, saj je $x-a > 0$.
Če je $x < a$, je $f'(\xi) < f'(a)$ (ker $f'$ strogo narašča). Zato $f'(\xi)(x-a) > f'(a)(x-a)$, saj je $x-a < 0$.
V obeh primerih sledi $f(x) > f(a) + f'(a)(x-a)$.

**Dokaz (iv) $\iff$ (v)**
Uporabimo, da $F$ strogo narašča $\iff F' > 0$ povsod.
(iv) implicira konveksnost, kar implicira $f'$ narašča.
Če $f'$ ne bi strogo naraščala, bi imela $f'$ na nekem intervalu konstanten odvod, nato bi bila tam linearna (oz. afina; $y=kx+n$), takšne funkcije pa ne zadoščajo (iv).
Za (v): $f''(x) > 0 \iff f'$ strogo narašča. Torej je to ekvivalentno (iii).

**Definicija (Prevoj)**
Naj bo funkcija $f$ definirana v okolici točke $c \in \mathbb{R}$. Če obstaja $\delta > 0$ takšen, da:
*   na $(c, c+\delta)$ je $f$ strogo konveksna
*   na $(c-\delta, c)$ je $f$ strogo konkavna
ali obratno, pravimo, da ima $f$ v $c$ **prevoj**.
(Grafična predstavitev: $f'' < 0$ na eni strani in $f'' > 0$ na drugi strani prevoja.)
Prevoj ni nujno stacionarna točka (tangenta ni nujno vodoravna).

**Trditev**
Če je $f \in C^2(I)$ in ima v $c \in I$ prevoj, tedaj je $f''(c)=0$.
**Dokaz:** Na $(c, c+\delta)$ je $f''>0$, zato $f''(c) = \lim_{x \to c^+} f''(x) \ge 0$ (zaradi zveznosti $f''$).
Podobno na $(c-\delta, c)$ je $f''<0$, zato $f''(c) = \lim_{x \to c^-} f''(x) \le 0$.
Iz obeh sledi $f''(c)=0$.

***

**Ekstremi funkcij ene spremenljivke**



**Definicija**
Naj bo $I \subseteq \mathbb{R}$ interval, $a \in I$ in $f: I \rightarrow \mathbb{R}$ funkcija. Pravimo, da ima $f$ v točki $a$ **lokalni minimum/maksimum**, če obstaja $\varepsilon > 0$ takšen, da za vsak $x \in I \cap (a-\varepsilon, a+\varepsilon)$ velja $f(x) \ge f(a)$ (za min) oz. $f(x) \le f(a)$ (za max).
**Lokalni ekstrem** je točka, ki je bodisi lok. min bodisi lok. max.

**Izrek (nujni pogoj za ekstrem)**
Naj bo $I \subseteq \mathbb{R}$ odprt interval. Če je $f: I \rightarrow \mathbb{R}$ odvedljiva in ima v točki $a \in I$ lok. ekstrem, tedaj je $f'(a)=0$.
**Dokaz**
Denimo, da ima $f$ v $a$ lok. min. in naj bo $\varepsilon > 0$ kot v def. lok. minimuma. Z analizo diferenčnega kvocienta $\frac{f(x)-f(a)}{x-a}$ podobno kot v dokazu Rolleovega izreka, dokažemo, da $f'(a)=0$.
(Ko $x \to a^-$, je $\frac{f(x)-f(a)}{x-a} \le 0$, torej $f'(a) \le 0$. Ko $x \to a^+$, je $\frac{f(x)-f(a)}{x-a} \ge 0$, torej $f'(a) \ge 0$. Sledi $f'(a)=0$.)

Pomen izreka je v tem, da močno zoža množico, v kateri iščemo lok. ekstreme (namesto celega intervala lahko iščemo le med točkami, kjer je $f'(a)=0$).

**Definicija**
Točka $a \in \mathbb{R}$, v kateri je $f'(a)=0$, se imenuje **stacionarna točka** funkcije $f$.
Torej: če ima $f$ v $a$ lok. ekstrem, tedaj je $a$ stacionarna točka funkcije $f$.
Hkrati ne velja (npr. $f(x)=x^3, a=0$; $f'(0)=0$, a ni ekstrem).

**Ali imamo kriterij na ugotavljanje, ali je stacionarna točka tudi lok. ekstrem?**

**Izrek (postopek z drugim odvodom)**
Naj bo $I \subseteq \mathbb{R}$ odprt interval, $a \in I$ in funkcija $f: I \rightarrow \mathbb{R}$ dvakrat odvedljiva. Denimo, da je $f'(a)=0$.
*   Če je $f''(a) > 0$, tedaj ima $f$ v $a$ lok. minimum.
*   Če je $f''(a) < 0$, tedaj ima $f$ v $a$ lok. maksimum.

**Dokaz**
Denimo, da je $f''(a) > 0$. Od tod iz def. odvoda sledi, da obstaja $\varepsilon > 0$ takšen, da na $x \in I \cap (a-\varepsilon, a+\varepsilon) \setminus \{a\}$ velja:
$$ \frac{f'(x)-f'(a)}{x-a} > 0 $$
Ker je $f'(a)=0$, sledi:
*   $f'(x)>0$ za $x \in I \cap (a, a+\varepsilon)$
*   $f'(x)<0$ za $x \in I \cap (a-\varepsilon, a)$
Po Lagrangeovem izreku na intervalu $(a, x)$ (za $x>a$) ali $(x, a)$ (za $x<a$):
$\forall x \in I \cap (a, a+\varepsilon) \ \exists \xi \in (a,x): f(x)-f(a) = f'(\xi)(x-a)$.
$\forall x \in I \cap (a-\varepsilon, a) \ \exists \xi \in (x,a): f(x)-f(a) = f'(\xi)(x-a)$.
*   Če $x>a$: $x-a>0$. Ker $f'(\xi)>0$ za $\xi \in (a,x)$, je $f(x)-f(a) > 0$.
*   Če $x<a$: $x-a<0$. Ker $f'(\xi)<0$ za $\xi \in (x,a)$, je $f(x)-f(a) > 0$.
Posledično je $f(x)-f(a) > 0$ na $x \in I \cap (a-\varepsilon, a+\varepsilon) \setminus \{a\}$, zato ima $f$ v točki $a$ lok. minimum.

---

**L'Hôpitalovo pravilo**

**Poenostavljena različica:**
Če v točki $a$ velja $f,g \to 0$ ali $f,g \to \pm\infty$, tedaj:
$$ \lim_{x \to a} \frac{f(x)}{g(x)} = \lim_{x \to a} \frac{f'(x)}{g'(x)} $$
(če limita na desni obstaja).

**Geometrični pomen:**
Poglejmo si primer $f(a)=g(a)=0$. Definirajmo krivuljo $\gamma(t) = (g(t), f(t))$.
(Grafična predstavitev: krivulja $\gamma(t)$ v ravnini, točka $(g(t), f(t))$.)
Naklon sekante $= \frac{f(t)}{g(t)}$. Tu upoštevamo, da je $f(a)=g(a)=0$ oz. $\gamma(a)=(0,0)$.
Naklon tangente v $\gamma(0)$ je $\lim_{t \to 0} \frac{f(t)}{g(t)}$.
Naklon tangente v $\gamma(t)$ je $\frac{f'(t)}{g'(t)}$.
L'Hôpitalovo pravilo pove, da naklon tangente v $\gamma(t)$ teži k naklonu tangente v $\gamma(0)$, ko $t \to 0$.
To je smiselno, saj pričakujemo, da se tangenta v $\gamma(t)$ "približuje" k tangenti v $\gamma(0)$. Izrek lahko razumemo kot ilustracijo L'Hôpitalovega pravila.

**Izrek (L'Hôpital)**
Privzemimo, da:
(i) $a \in \mathbb{R} \cup \{-\infty, \infty\}$, $I \subseteq \mathbb{R}$ (odprt) interval takšen, da $a \in \bar{I}$.
To pomeni, da bodisi:
*   $a \in \mathbb{R}$ in bodisi $I=(b,a)$ (enostranska limita), $I=(a,c)$ (enostranska limita), ali $I=(b,c)$ (dvostranska limita), kjer $b<a<c$.
*   $a=\infty$ in $I=(b,\infty)$
*   $a=-\infty$ in $I=(-\infty,c)$
(ii) $f, g: I \setminus \{a\} \rightarrow \mathbb{R}$
*   odvedljivi povsod
*   $g(x), g'(x) \neq 0$ na $I \setminus \{a\}$
(iii) $\lim_{x \to a} f(x) = \lim_{x \to a} g(x) \in \{0, \pm\infty\}$
(iv) $\exists \lim_{x \to a} \frac{f'(x)}{g'(x)} \in \mathbb{R} \cup \{\pm\infty\}$.
Tedaj obstaja tudi $\lim_{x \to a} \frac{f(x)}{g(x)}$ in velja:
$$ \lim_{x \to a} \frac{f(x)}{g(x)} = \lim_{x \to a} \frac{f'(x)}{g'(x)} $$

**Dokaz št. 1 (primer, ko sta $f,g$ odvedljivi v $a$ in $f(a)=g(a)=0, g'(a) \ne 0$)**
Imamo:
$$ \frac{f(x)}{g(x)} = \frac{f(x)-f(a)}{g(x)-g(a)} = \frac{\frac{f(x)-f(a)}{x-a}}{\frac{g(x)-g(a)}{x-a}} $$
Sledi (ko $x \to a$):
$$ \lim_{x \to a} \frac{f(x)}{g(x)} = \frac{f'(a)}{g'(a)} = \lim_{x \to a} \frac{f'(x)}{g'(x)} $$
(q.e.d.)

**Dokaz št. 2 (< motivacija: graf zgoraj, $g$ strogo monotona in odvedljiva v $a$)**
$g(a)=0$.
$\lim_{x \to a} \frac{f(x)}{g(x)} = \lim_{t \to 0} \frac{(f \circ g^{-1})(t) - (f \circ g^{-1})(0)}{t-0} = (f \circ g^{-1})'(0)$.
Ker sta $f,g$ zvezno odvedljivi, je $(f \circ g^{-1})'(0) = f'(g^{-1}(0)) \cdot (g^{-1})'(0) = f'(a) \cdot \frac{1}{g'(a)} = \frac{f'(a)}{g'(a)}$.
(q.e.d.)

**Dokaz št. 3 (s pomočjo Lagrangeovega izreka)**
Iz Lagrangeovega izreka sledi (za neki $\xi, \eta \in [0,h]$):
$f(a+h) = f(a) + f'(a+\xi h)h$
$g(a+h) = g(a) + g'(a+\eta h)h$
Posledično, če $f(a)=g(a)=0$, tedaj:
$$ \frac{f(a+h)}{g(a+h)} = \frac{f'(a+\xi h)h}{g'(a+\eta h)h} = \frac{f'(a+\xi h)}{g'(a+\eta h)} $$
In upoštevamo, da sta $f,g$ zvezno odvedljivi ter $g'(a) \ne 0$. Ko $h \to 0$, tudi $\xi h \to 0$ in $\eta h \to 0$.
$$ \lim_{h \to 0} \frac{f(a+h)}{g(a+h)} = \frac{\lim_{h \to 0} f'(a+\xi h)}{\lim_{h \to 0} g'(a+\eta h)} = \frac{f'(a)}{g'(a)} $$

---

**Taylorjev izrek**

**Cilj/ideja:** V okolici točke $a$ želimo funkcijo $f$ aproksimirati s preprostimi funkcijami – polinomi.
(Grafična predstavitev: funkcija $f(x)$ z različnimi polinomskimi aproksimacijami (konstanta, tangenta, kvadratni) v okolici točke $a$.)
Za izračun funkcijskih vrednosti potrebujemo le seštevanje in množenje.

Naj bo $T_n$ najustreznejši polinom stopnje $n$ ali manj, ki aproksimira funkcijo $f$ v okolici točke $a$. Iščemo formulo zanj.
Za $n=0,1$ jo že poznamo:
*   **konstanta ($n=0$):** $f(a+h) \approx f(a)$ (zveznost), pomen: razlika je $o(1)$.
*   **premica ($n=1$):** $f(a+h) \approx f(a) + f'(a)h$ (tangenta) (linearni približek), pomen: razlika je $o(h)$.

Nekoliko bolj natančno: Naj bo $f$ dovoljkrat odvedljiva v okolici točke $a \in \mathbb{R}$. Želeli bi $f(a+h)$ aproksimirati (= približno izračunati) s polinomi stopnje $n$ v $h$, katerih koeficienti so odvisni od $a$ (in $f$, seveda). Višji red polinoma pomeni bolj zapleteno, toda natančnejšo aproksimacijo.

**Za $n=2$ (kvadratni približek):**
Kaj pa kvadratni (= boljši) približek?
Želimo najti $\alpha_0, \alpha_1, \alpha_2 \in \mathbb{R}$, odvisne od $f$ in $a$, za katere bo:
$$ f(a+h) \approx \alpha_0 + \alpha_1 h + \alpha_2 h^2 $$
v smislu, da:
$$ \lim_{h \to 0} \frac{f(a+h) - [\alpha_0 + \alpha_1 h + \alpha_2 h^2]}{h^2} = 0 \quad (1) $$
Če naj velja (1), mora števec imeti limito $0$, zato dobimo:
$\alpha_0 = f(a)$.
Prav tako mora biti limita enaka $0$, če delimo zgolj s $h$ (in ne $h^2$), kar implicira:
$\alpha_1 = f'(a)$.
To sta potrebna pogoja za (1). Končno iz (1) sledi še:
$\alpha_2 = \lim_{h \to 0} \frac{f(a+h) - f(a) - hf'(a)}{h^2}$.
Če limita obstaja, od koder L'Hôpitalovo pravilo da:
$\alpha_2 = \lim_{h \to 0} \frac{f'(a+h)-f'(a)}{2h} = \frac{1}{2} f''(a)$.
Torej so koeficienti: $\alpha_0=f(a), \alpha_1=f'(a), \alpha_2=\frac{f''(a)}{2}$.
Kaj pa $\alpha_3$? Domnevamo, da bo torej $\alpha_3 = \frac{f'''(a)}{6}$.

Bolj splošno:
$$ \alpha_j = \frac{f^{(j)}(a)}{j!} $$
To so kandidati za koeficiente aproksimacije funkcije $f(a+h)$, $\alpha_0+\alpha_1 h+\alpha_2 h^2+\ldots+\alpha_n h^n$, če je $f$ v točki $a$ $n$-krat odvedljiva.

**Izrek (Taylor)**
Naj bo $n \in \mathbb{N}$, $I$ odprt interval v $\mathbb{R}$, $a \in I$ ter $f: I \rightarrow \mathbb{R}$ $n$-krat odvedljiva v točki $a$. Tedaj obstaja funkcija $g_n: I-a \rightarrow \mathbb{R}$ (kjer $I-a := \{x-a \mid x \in I\}$), za katero je:
(i) $f(a+h) = f(a) + f'(a)h + \frac{f''(a)}{2}h^2 + \ldots + \frac{f^{(n)}(a)}{n!}h^n + g_n(h)h^n$
(ii) $\lim_{h \to 0} g_n(h) = 0$.

**Komentar:** Točko (i) lahko domačimo, enostavno kot:
$$ g_n(h) := \frac{f(a+h) - \left[ f(a) + f'(a)h + \frac{f''(a)}{2}h^2 + \ldots + \frac{f^{(n)}(a)}{n!}h^n \right]}{h^n} $$
(Polinom reda $n$ v $h$; koeficienti odvisni od $f, a$).
Težji del je dokazati (ii). Vedno lahko napišemo $B=A+\text{ostanek}$, saj vzamemo ostanek := $B-A$. Toda bistvo izreka je, da je ostanek majhen (v smislu, da ...).
Torej sklep izreka lahko zapišemo kot:
$$ \lim_{h \to 0} \frac{f(a+h) - \left[ f(a) + f'(a)h + \frac{f''(a)}{2}h^2 + \ldots + \frac{f^{(n)}(a)}{n!}h^n \right]}{h^n} = 0 \quad (2) $$

**Dokaz**
Zaporedoma uporabimo L'Hôpitalov izrek; po $(n-1)$-kratnem odvajanju števca ter imenovalca v (2) po $h$ dobimo:
$$ \lim_{h \to 0} \frac{f^{(n-1)}(a+h) - \left[ 0+\ldots+\frac{f^{(n-1)}(a)}{(n-1)!}(n-1)! + \frac{f^{(n)}(a)}{n!}n! h \right]}{n!h} $$
$$ = \lim_{h \to 0} \frac{f^{(n-1)}(a+h) - f^{(n-1)}(a) - f^{(n)}(a)h}{n!h} $$
$$ = \frac{1}{n!} \lim_{h \to 0} \left( \frac{f^{(n-1)}(a+h) - f^{(n-1)}(a)}{h} - f^{(n)}(a) \right) $$
$$ = \frac{1}{n!} (f^{(n)}(a) - f^{(n)}(a)) = 0 $$
po definiciji $f^{(n)}(a)$.

Če pišemo $x=a+h$, lahko (i) & (ii) napišemo kot:
(i) $f(x) = \sum_{k=0}^n \frac{f^{(k)}(a)}{k!}(x-a)^k + \tilde{g}_n(x)(x-a)^n$, kjer je
(ii) $\lim_{x \to a} \tilde{g}_n(x) = 0$.
Tu je $\tilde{g}_n(x) = g_n(x-a)$.

**Oznaka**
Izrazu $T_n(x) = T_{f,a,n}(x) := \sum_{k=0}^n \frac{f^{(k)}(a)}{k!}(x-a)^k$ pravimo **$n$-ti Taylorjev polinom** za $f$ okoli točke $a$.
Pišemo $R_n := f-T_n$.
Oz. $R_n(x) = R_{f,a,n}(x) := \tilde{g}_n(x)(x-a)^n$. Tej funkciji pravimo **ostanek** ("remainder"), včasih tudi napaka.

Pod strožjimi predpostavkami na $f$ lahko $R_n$ opišemo še drugače:

**Izrek (Lagrangeova oblika ostanka)**
Naj bo $f$ $(n+1)$-krat odvedljiva na odprtem intervalu $I$ in $a \in I$. Tedaj za vsak $x \in I$ obstaja $\xi \in I$, ki leži med $a$ in $x$, takšen, da:
$$ R_n(x) = \frac{f^{(n+1)}(\xi)}{(n+1)!}(x-a)^{n+1} $$
[Za $n=0$ je to samo Lagrangeov izrek: $f(x)-f(a) = f'(\xi)(x-a)$.]
Dokaz: Glej npr. zapiske B. Magajne, str. 73-74.

**Posledica**
Če je $f^{(n+1)}$ omejena na $I$, to je, $\exists M>0$ takšen, da $|f^{(n+1)}(x)| \le M$ za $\forall x \in I$, tedaj lahko ostanek (napako) ocenimo, in sicer:
$$ |R_n(x)| \le \frac{M}{(n+1)!}|x-a|^{n+1} $$
Ta rezultat poda oceno na velikost napake oz. na hitrost aproksimacije.
(Grafična predstavitev: $h, h^2, h^3$ prikazuje, kako se napaka zmanjšuje z višjo stopnjo polinoma.)


---

**Taylorjeva vrsta**

Če je $f$ neskončnokrat odvedljiva v okolici točke $a$, lahko obravnavamo Taylorjeve polinome poljubne stopnje $(n)$, oz. ko $n \to \infty$ dobimo **Taylorjevo vrsto** za $f$ okoli točke $a$:
$$ \sum_{k=0}^\infty \frac{f^{(k)}(a)}{k!}(x-a)^k $$
To je poseben primer potenčne vrste; o tem smo govorili v poglavju o vrstah.

**Definicija**
Funkcija $f$, ki je na neki okolici točke $a$ enaka svoji Taylorjevi vrsti, se imenuje **(realno) analitična** v točki $a$.
**Opomba:** Če je $f$ $\infty$-krat odvedljiva v točki $a$, še ni nujno realno analitična. Res, poglejmo npr.:
$$ f(x) = \begin{cases} 0; & x \le 0 \\ e^{-1/x}; & x > 0 \end{cases} $$
Velja:
(I) $f$ je $\infty$-krat odvedljiva na $\mathbb{R} \setminus \{0\}$ (očitno).
(II) $f'(0+) = \lim_{x \to 0^+} \frac{f(x)-f(0)}{x} = \lim_{x \to 0^+} \frac{e^{-1/x}}{x} = \lim_{t \to \infty} \frac{t}{e^t} = 0$. (z L'Hôpitalovim pravilom).
$f'(0-) = 0$ (očitno).
Torej:
$$ f'(x) = \begin{cases} 0; & x \le 0 \\ \frac{1}{x^2}e^{-1/x}; & x > 0 \end{cases} $$
Podobno vidimo, da $\exists f^{(k)}(0)$ za $\forall k \in \mathbb{N}_0$.
Torej je res $f \in C^\infty(\mathbb{R})$ in hkrati $f^{(k)}(0)=0$ za $\forall k \in \mathbb{N}_0$.
(III) Če bi veljalo $f(x) = \sum_{k=0}^\infty \frac{f^{(k)}(0)}{k!}x^k = 0$ za $x$ iz neke okolice točke $0$, bi torej veljalo $f(x)=0$ na neki okolici točke $0$, kar pa očitno ne velja (ker $e^{-1/x} \ne 0$ za $x>0$).



***
## ANA datoteka
Iz **analize datoteke**

Odvod funckije v točki $a$ je koeficient tangente na funkcijo. Pove kako se spreminja vrednost funkcije pri še tako majhnih razlikah v $x$.

$$f'(x) = \lim_{h \to 0}\frac{f(x+h) - f(x)}{h}$$

je odvod če ta limita obstaja. V tem primeru pravimo da je funkcija odvedljiva v $x$.

$\frac{f(x+h) - f(x)}{h}$ se imenuje diferenčni koeficient.

Odvod lahko zapišemo tudi kot 

$$f'(x_{0}) = \frac{df}{dx}(x_{0})$$



>[!|]- Pravila za odvajanje elementranih funkcij
   $$\frac{d}{dx} c = 0, $$
   $$\frac{d}{dx} x^n = n x^{n-1}, \quad n \in \mathbb{R}$$
   $$\frac{d}{dx} e^x = e^x$$  
   $$\frac{d}{dx} a^x = a^x \ln a, \quad a > 0$$
   $$\frac{d}{dx} \ln x = \frac{1}{x}$$  
   $$\frac{d}{dx} \log_a x = \frac{1}{x \ln a}, \quad a > 0, a \neq 1$$
   $$\frac{d}{dx} \sin x = \cos x$$  
   $$\frac{d}{dx} \cos x = -\sin x$$  
   $$\frac{d}{dx} \tan x = \sec^2 x, \quad x \neq \frac{\pi}{2} + k\pi$$  
   $$\frac{d}{dx} \cot x = -\csc^2 x, \quad x \neq k\pi$$  
   $$\frac{d}{dx} \sec x = \sec x \tan x, \quad x \neq \frac{\pi}{2} + k\pi$$  
   $$\frac{d}{dx} \csc x = -\csc x \cot x, \quad x \neq k\pi$$  
   $$\frac{d}{dx} \arcsin x = \frac{1}{\sqrt{1 - x^2}}, \quad |x| < 1$$  
   $$\frac{d}{dx} \arccos x = \frac{-1}{\sqrt{1 - x^2}}, \quad |x| < 1$$  
   $$\frac{d}{dx} \arctan x = \frac{1}{1 + x^2}$$  
   $$\frac{d}{dx} \text{arccot } x = \frac{-1}{1 + x^2}$$  
   $$\frac{d}{dx} \sinh x = \cosh x$$  
   $$\frac{d}{dx} \cosh x = \sinh x$$  


> Če je $f$ odvedljiva v točki $x$ je tam tudi zvezna.

> Če sta $f$ in $g$ odvedljivi potem je vsota, razlika, produkt, kvocientm kompozitum teh funkcij odvedljiva.

$$(fg)' = f'g+fg'$$

$$\left(\frac{f}{g}\right)' = \frac{f'g-fg'}{g^{2}}$$

$$(f \circ g)' = f'(g(x))g'(x)$$

Če je $f$ odvedljiva na intervalu $I$ in $f'(a) \neq 0$ za nek $a$ na intervalu potem je funkcija $f^{-1}$ diferanciabilna v $b = f(a)$.

$$(f^{-1}(b))' = \frac{1}{f'(a)}$$
$$(f^{-1}(b))' = \frac{1}{f'(f^{-1}(b))}$$

Naj bo $f$ deifnirana v točki $a$. Diferencial v točki je definiran kot 

$$df = f'(a)dx$$

oz. kot linearna funkcija

$$df(h) = Kh$$

kjer je $K$ poljubna konstanta. Ta konstanta naj bi zaradi naše zahteve da je

$$\lim_{h \to 0} \frac{|f(a+h)-f(a)-df(h)h|}{|h|} = 0$$

bila enaka $f'(a)$.

> Funkcija je odvedljiva v točki $a$ natanko tedaj ko je diferenciabilna v $a$

**Langrangev izrek** pravi da je če imamo funkcijo definirano na zaprtem intervalu in odvedljivo na istem ampak odprtem intervalu potem obstaja število $\xi \in (a,b)$ tako da velja $f(b)-f(a) = f'(\xi)(b-a)$

**Rollejev izrek** pravi da če imamo enako definirano funkcijo kot prej in vemo da je $f(a) = f(b)$ potem obstaja tako število $\xi \in (a,b)$ tako da velja $f'(\xi)= 0$ 

Funkcija je **Lipshitzova** če velja da obstaja konstanta $L$ nemanjša od 0 tako da za vse $x_{1}, x_{2}$ velja 

$$|f(x_1)-f(x_{2})| \leq L \cdot |x_{1}-x_{2}|$$

L deluje kot meja strmosti, ki je funkcija ne preseže.

> Če je funkcija zvezno odvedljiva na $[a,b]$, je Lipshitzova.

> Funkcija je na intervalu padajoča/naraščajoča če velja da je na istem intervalu odvod funkcije negativna/pozitivna.

Funkcija ke **konveksna** če velja

$$\forall x,a,b \in (a,b): f(x)\leq f(a) + \frac{f(b)-f(a)}{b-a}(x-a)
$$
$$ $$
$$\forall x,y \in I : f\left(\frac{x+y}{2}\right)\leq \frac{f(x)+f(y)}{2}$$

Funkcija ke **konkavna** če velja

$$\forall x,a,b \in (a,b): f(x)\geq f(a) + \frac{f(b)-f(a)}{b-a}(x-a)
$$
$$ $$
$$\forall x,y \in I : f\left(\frac{x+y}{2}\right)\geq \frac{f(x)+f(y)}{2}$$

> Konveksa funkcija je nujno zvezna

> Če je konveksna funkcija odvedljiva potem odvod funkcije narašča


***
Iz starih zapskov

### Taylorjev polinom in taylorjeva vrsta

Mi lahko funkcijo aproksimiramo v točki $a$ s konstanto. Konstanta očitno ne upošteva spreminjanje vrednosti funkcije zato v točki $a$ definiramo linearno aproksimacijo kar je neka linearna funkcija $kx$.

Kaj je najboljša linearna aproksimacija? 

Hočemo da je blizu vrednosti $a$ najmanjša razlika med funkcijama. Če pogledamo funkcijo razlike med aproksimacijo in dejansko funkcijo lahko vidimo da bo razlika v okolici najmanjša takrat ko bo krivulja razlike najbolj ploščata v $a$. To pomeni da mora biti odvod funkcije razlike enak 0.

Najprej poglejmo kakšen mora biti nastavek za funkcijo:

$$f(a)+kx = r(x)$$
$$r(a) = 0$$
$$f(a)+ka=0$$
$$ka = 0$$

Iz tega sledi da mora $kx$ člen v resnici zgledati kot $k(x-a)$.

Za koeficient pa se izkaže da je enak odvodu funkcije. (Če razvijemo po definiciji odvoda.)

$$f(x) = f(a) + k(x-a) + r(x)$$
$$\frac{f(x)-f(a)}{x-a}=k + \frac{r(x)}{x-a}$$
$$\lim_{x \to a}\frac{f(x)-f(a)}{x-a}=\lim_{x \to a}k + \frac{r(x)}{x-a}$$
$$f'(a) = k + \lim_{x \to a}\frac{r(x)}{x-a}$$

Da imamo najbolšo aproksimacijo mora iti desna limita v 0 iz kjer dobimo da je $k = f'(a)$ res najbolša aproksimacija.

Naša linearna aproksimacija pa ne upošteva spremembo koeficienta. Zato se odločimo da bomo raje linearno aproksimirali odvod funkcije $f$. 
S tem dobimo linearno funkcijo (oz. odvod aproksimacije) kot aproksimacijo odvoda dejanske funkcije, ki jo moramo nato integrirati da dobimo aproksimacijo originalne funkcije.

$f'(a) + f''(a)(x-a) = p'(x) = p_{1}$ sledi iz popolnoma istega postopka kot prej.

$$\int_{{\color{green}a}}^{{\color{green}x}} f'(a) + f''(a)\cdot (x-a) \cdot dx = p(x) $$
$$f'(a)(x-a) + f''(a)\frac{(x-a)^{2}}{2} + C =p(x)$$

Da dobimo konstantni člen moramo vedeti da je $p(a) = f(a)$ kar pomeni da $C$ mora biti $f(a)$.

Torej imamo $p_{1}$ ki linearno aproksimira $f'$. Ampak ta spet ne upošteva spremembo koeficienta odvoda zato linearno aproksimiramo drugi odvod in tako naprej.

Na neki točki se ustavimo. Linearno smo aproksimirali $n$-ti odvod funkcije enačba pa zgleda kot

$$f^{(n)}(x) \approx p_{n}(x) = f^{(n)}(a) + f^{(n+1)}(a)(x-a)$$

Ker je naša funkcija $p_{n}$ aproksimacija $n$-tega odvoda, mi pa hočemo aproksimacijo funkcije moramo $p_{n}$ $n$-krat integrirati. Pri integriranju pa vemo da beležimo le spremembo vrednosti ne pa njene začetne vrednosti.

To pomeni da ko aproksimiramo $n$-ti odvod, ter ga integriramo, dobimo funkcijo podobno $n-1$ odvoda le da ni pravilno premaknjen na $y$ osi. Ker pa je vse kar vemo pri integriranju kako se spreminja vrednost funkcije in ničesar o izhodiščni vrednosti funkcije, bo naša integrirana aproksimacija naraščala in padal podobno kot izhodiščna a se v točki $a$ ne bosta ujemali. 

Ker je izhodišče integracije v $a$ pa vemo da bo tam naša izhodiščna vrednost. To pomeni da le prištejemo originalno vrednost oz. $f^{(n-1)}(a)$ in dobimo pravilno aproksimacijo.

Tak korak ponovimo dokler ne pridemo do originalne funkcije.

Vzemimo primer kjer bo $n=2$

$$p_{2}\left(x\right)=f''\left(a\right)+f'''\left(a\right)\left(x-a\right)$$
$$p_{1}\left(x\right)=\int_{a}^{x}p_{2}\left(t\right)dt+f'\left(a\right) $$
$$p\left(x\right)=\int_{a}^{x}p_{1}\left(t\right)dt+f\left(a\right)$$
$$p\left(x\right)=\int_{a}^{x}\left(\int_{a}^{t}p_{2}(u)du\ +\ f'\left(a\right)\right)dt\ +\ f\left(a\right)$$

$$p\left(x\right)=\int_{a}^{x}\left(\int_{a}^{t}{\color{green}\left(f''\left(a\right)+f''''\left(a\right)\left(u-a\right)\right)}du\ +\ f'\left(a\right)\right)dt\ +\ f\left(a\right)$$

$$p(x) =f\left(a\right)+f'\left(a\right)\left(x-a\right)+\frac{f''\left(a\right)\left(x-a\right)^{2}}{2}+\frac{f'''\left(a\right)\left(x-a\right)^{3}}{6}$$

https://www.desmos.com/calculator/spyu5vxgxd

Najpomembnejša stvar tukej je kako prištevanje večjih stopenj $x$ in ustrezni koeficient zagotovita da bo funkcija razlike imela odvod enak 0 v $a$.

Realistično lahko govorimo o aproskimaciji z drugimi funkcijami ampak imajo polinomi najmanjše napake na okolici $a$. Zaradi ujemanja odvodov.


Taylorjev polinom centriran v točki $a$ stopnje $n$ je funkcija za katero velja

$$p(x) = A_{0} + A_{1}(x-a) + A_{2}(x-a)^{2}+...+A_{n}(x-a)^{n}$$
$$f(x) = p(x) + R_{n}(x)$$

tako da velja 

$$R_n(h) = f(a+h)-p_{n}(a+h)$$
$$\lim_{h \to 0}\frac{R_{n}(h)}{h} = 0$$
$$\lim_{h \to 0}\frac{R_{n}(h)-R_{n}(0)}{h} = 0$$
$$\Rightarrow R_{n}'(0) = 0$$

Ni popolnoma standarden zapis limite ker je funkcija definirna preko $h$-ja drugače je:

$$\lim_{h \to 0}\frac{R_{n}(a+h)-R_{n}(a)}{h} = 0$$
$$R_{n}'(a) = 0$$

To pomeni da morajo koeficienti biti taki da je odvod funkcije razlike v $a$ enak 0. To zato ker hočemo da je razlika na okolici $a$ čim manjša in če odvod v točki $a$ ne gre proti nič, obstaja boljši $p(x)$, s katerim lahko funkcijo ocenimo.

$$\lim_{h \to 0}\frac{R_{a}(h)}{h} = 0$$

*S tem hočemo povedati da ostanek ni odvisen od $h$. Recimo da je ostanek odvisen od $h$ na nek način potem bi veljalo da bi se dalo razčleniti kot produkt $h$ s konstantno in nekim izrazom ki ni več odvisen od $h$*

$$\color{light} R(h) = Ch + o(h^2)$$

*kjer $o(h^2)$ le presdtavlja nek izraz ki ni več odvisen od $h$, namesto $h^{2}$ je lahko karkoli kar ni $h$ ali slabše (npr $h^\frac{1}{2}$)*
*Potem bi veljalo*

$$\color{light}p(h) = f(x-h) + f'(x-h)h + Ch + o(h^2)$$

*Torej odvod ne bi bila najboljša aproksimacija, in še vedno nam ostane nek izraz oz. ostanek ki ni odvisen od $h$. To velja za vse nadaljne potence.*

*Hočemo da dobimo*

$$\color{light}\lim_{h \to 0}\frac{R(h)}{h^{n}} = \frac{Ch^{n+1}}{h^{n}} = Ch = 0$$

*To v resnici spet predsstavlja razmerje med členom $n$-tega reda in $n+1$-reda torej*

$$\color{light}\lim_{h \to 0}\frac{R_{n+1}(h)}{f^{(n)}(a-h)h^{n} \frac{1}{n!}} = \frac{O(h^{n+1})}{O(h^{n})} = \frac{Ch^{n+1}}{Dh^{n}} = Eh = 0$$

*To je pogoj ki nam pove da je ostanek zanemarljiv v primerjavi z zadnjim členom oz postane veliko manjši. *

Preostane nam samo še zapis ostanka z nekim izrazom idealno po istem vzorcu.


Ob $n$ kratnem integriranju dobimo spet taylorjev polinom s tem da imamo še pravilno ocenjen ostanek preko Lagrangevega izreka.

Velja 

$$p(x) = f(a)+...+f^{(n)}(a)(x-a)^{n} \frac{1}{n!} $$
$$p^{(n+1)}(x) = 0$$

Če vzamemo funkcijo

$$T(x) = f(x)-p(x)-K(x-a)^{n+1}$$
$$f(a) = p(a) \Rightarrow f(a)-p(a) = 0 $$

Vidimo da je $T(a) = 0$, za lažji dokaz pa naj bo tudi $T(x) = 0$, torej po Rollejevemu izreku velja da obstaja $c_{1}$ da velja $T'(c_{1}) = 0$. 

Ker  po konstrukciji funkcije velja $T'(a) = T'(c_{i}) = 0$ lahko Rolleta ponavljamo dokler ne pridemo do $n+1$ koraka. V tem koraku dobimo enačbo

$$T^{(n+1)}(c_{n+1}) = f^{(n+1)}(c_{n+1}) - 0 - K(n+1)!\, $$

Po Rolletu je $T^{(n+1)}(c_{n+1}) = 0$

$$K = \frac{f^{(n+1)}(c_{n+1})}{(n+1)!}$$

Ker leži $c_{n+1}$ na intervalu velja da napaka ne presega največjega $n+1$ odvoda na intervalu $a$ in $x$.

Ta člen je pomemben kjer njegova izpeljava zagotavlja da lahko napako smiselno omejimo.



