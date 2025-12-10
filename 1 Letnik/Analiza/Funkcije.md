
## Osnove

Naj bosta $A, B$ množici. 

Preslikava iz $A$ v $B$ je pravilo ki vsakemu elementu iz množice $A$ priredi natanko en element množice $B$. Pri tem pišemo

$$f: A \rightarrow B$$
$$f: a \mapsto f(a)$$

pri tem je $A$ definicijsko območje, $B$ je kodomena.


**Slika** oz. zaloga vrednosti funkcije $f$  je množica:
    
$$ f(A) := \{f(a) \mid a \in A\} $$

Če je $M \subseteq A$, potem je **slika podmnožice** $M$ množica:
   
$$ f(M) := \{f(a) \mid a \in M\} $$

**Praslika:**
Če je $M \subseteq B$, se množica:
$$ f^{-1}(M) := \{a \in A \mid f(a) \in M\} $$
imenuje **praslika** množice $M$ glede na $f$.
***
**Realna funkcija** na $D$ je preslikava

$$f: D \rightarrow \mathbb{R}$$
$$f: x \mapsto f(x)$$

funkcija je enolično določena z definicijskim območjem in predpisom.

**Graf funkcije** $f$ je dvojiška množica $\Gamma_f$ urejenih parov:
$$ \Gamma_f := \{(a, f(a)) \mid a \in A\} $$



Če je $\tilde{A} \subseteq A$, funkcija:

$$ f|_{\tilde{A}} : \tilde{A} \rightarrow B $$
$$ a \mapsto f(a) $$

imenujemo **zožitev** funkcije $f$ na množico $\tilde{A}$.



Če imamo funkciji $f: A \rightarrow B$ in $g: B \rightarrow C$, tedaj lahko definiramo **kompozitum** $g \circ f: A \rightarrow C$ funkcij $f$ in $g$ kot:
$$ (g \circ f)(a) = g(f(a)) $$


Funkcija $f: A \rightarrow B$ je:

*   **injektivna**, če $(\forall a_1, a_2 \in A: a_1 \neq a_2 \Rightarrow f(a_1) \neq f(a_2))$.

*   **surjektivna**, če $(\forall b \in B \ \exists a \in A: b = f(a))$.

*   **bijektivna**, če $(\forall b \in B \ \exists ! a \in A: b = f(a))$.



Če je $f: A \rightarrow B$ bijektivna, tedaj lahko definiramo njen **inverz** $f^{-1}: B \rightarrow A$.

Za vsak $b \in B$ je $f^{-1}(b)$ definiran kot tisti (edini) element $a \in A$, za katerega je $b=f(a)$.


Velja:
*   $f^{-1} \circ f = id_A$
*   $f \circ f^{-1} = id_B$


**Graf inverzne funkcije:**
Graf inverzne funkcije $\Gamma_{f^{-1}}$ je množica:

$$ \Gamma_{f^{-1}} = \{(x,y) \mid y=f^{-1}(x)\} $$
$$ = \{(x,y) \mid x=f(y)\} $$
$$ = \{(y,x) \mid y=f(x)\} $$

To pomeni, da graf $\Gamma_{f^{-1}}$ dobimo iz grafa $\Gamma_f$ z zamenjavo koordinat, kar ustreza zrcaljenju čez simetralo $y=x$.

**Osnovne operacije na realnih funkcijah**



Naj bosta $A$ množica in $f, g: A \rightarrow \mathbb{R}$ realni funkciji. Tedaj definiramo:

*   **Vsoto** $f+g: A \rightarrow \mathbb{R}$ kot $(f+g)(x) = f(x)+g(x)$.
*   **Razliko** $f-g: A \rightarrow \mathbb{R}$ kot $(f-g)(x) = f(x)-g(x)$.
*   **Produkt** $fg: A \rightarrow \mathbb{R}$ kot $(fg)(x) = f(x)g(x)$.
*   **Kvocient** $f/g: A \rightarrow \mathbb{R}$ kot $(f/g)(x) = f(x)/g(x)$, le da je kvocient definiran samo na množici $\{x \in A \mid g(x) \neq 0\}$.



**Definicija:** Pravimo, da je točka $a \in A$ **ničla funkcije** $f: A \rightarrow \mathbb{R}$, če je $f(a)=0$.



Če je $A=\mathbb{R}$ oz. $f: \mathbb{R} \rightarrow \mathbb{R}$, definiramo še druge operacije:

*   **Premiki (translacije)**: za $a \in \mathbb{R}$ definiramo operaciji $\tau_a$ in $\tau^a$ kot:
    *   $(\tau_a f)(x) := f(x-a)$
    *   $(\tau^a f)(x) := f(x)+a$

*   **Raztegi (dilatacije)**: za $t>0$ definiramo operaciji $\delta_t$ in $\delta^t$ kot:
    *   $(\delta_t f)(x) := f(x/t)$
    *   $(\delta^t f)(x) := t f(x)$

*   **Zrcaljenja**: V posebnem primeru za $t=-1$ dobimo:
    *   $\delta_{-1} f(x) = f(x/(-1)) = f(-x)$ (zrcaljenje glede na $y$-os)
    *   $\delta^{-1} f(x) = (-1)f(x) = -f(x)$ (zrcaljenje glede na $x$-os)



| Operacija | Geometrijski učinek na $\Gamma_f$ |
| :-------- | :-------------------------------- |
| $\tau_a f(x) = f(x-a)$ | Vodoravni premik grafa: za $a$ enot v desno (če $a>0$) ali v levo (če $a<0$). |
| $\tau^a f(x) = f(x)+a$ | Navpični premik grafa: za $a$ enot navzgor (če $a>0$) ali navzdol (če $a<0$). |
| $\delta_t f(x) = f(x/t)$ | Vodoravni razteg/skrčitev grafa: za faktor $t$ od $y$-osi. (Razteg, če $t>1$; skrčitev, če $0<t<1$). |
| $\delta^t f(x) = t f(x)$ | Navpični razteg/skrčitev grafa: za faktor $t$ od $x$-osi. (Razteg, če $t>1$; skrčitev, če $0<t<1$). |
| $\delta_{-1} f(x) = f(-x)$ | Zrcaljenje grafa čez $y$-os. |
| $\delta^{-1} f(x) = -f(x)$ | Zrcaljenje grafa čez $x$-os. |

**Periodične funkcije**

**Definicija:** Naj bo $\lambda > 0$. Funkcija $f: \mathbb{R} \rightarrow \mathbb{R}$ je $\lambda$-**periodična**, če je $\tau_\lambda f = f$ oz. $f(x+\lambda) = f(x)$ za $\forall x \in \mathbb{R}$.

**Konstantna** $f(x) = a$ in **identiteta** $f(x) = x$.

 
Naj bo $A=B=\mathbb{R}$. Iz konstant in identitete z operacijami seštevanja (+), odštevanja (-) in množenja (v končno korakih) dobimo **polinome**.

Če potence pomnožimo s konstantami ter jih seštevamo in odštevamo, dobimo polinome. To so torej funkcije $p$ oblike:
$$ p(x) = c_m x^m + c_{m-1} x^{m-1} + \ldots + c_1 x + c_0 $$
kjer so $c_0, c_1, \ldots, c_m \in \mathbb{R}$ podani koeficienti, $c_m \neq 0$, $x \in \mathbb{R}$ pa je spremenljivka.
Pravimo, da je $m \in \mathbb{N}$ **stopnja polinoma** $p$.


*   **Linearne funkcije** so polinomi stopnje 1.

*   **Kvadratne funkcije** so polinomi stopnje 2.

### Racionalne funkcije

Če poleg operacij seštevanja (+), odštevanja (-), množenja ($\cdot$) uporabimo še deljenje (:), tedaj iz konstant in identitete dobimo racionalne funkcije.

Torej je **racionalna funkcija** funkcija oblike:
$$ f(x) = \frac{p(x)}{q(x)} $$
kjer sta $p$ in $q$ polinoma.

Definirana je na komplementu množice ničel funkcije $q$, to je, na:
$$ D_f = \{x \in \mathbb{R} \mid q(x) \neq 0\} $$

**Koreni**

Naj bo $n \in \mathbb{N}$. Tedaj $n$-ti **koren** $\sqrt[n]{x}$ definiramo kot inverz $n$-te potence, torej $\sqrt[n]{x} = f^{-1}(x)$, kjer je $f$ bijektivna funkcija:
$$ f: [0, \infty) \rightarrow [0, \infty) $$
$$ x \mapsto x^n $$

Če je $n=2$, tedaj se $\sqrt[2]{x} := \sqrt{x}$ imenuje **kvadratni koren** oz. zgolj **koren**.



Iz zvez $(a^m)^n = a^{mn}$ ter $a=a^1$ sledi, da je smiselno pisati:
*   $x^{1/m} = \sqrt[m]{x}$
*   $x^{m/n} = \sqrt[n]{x^m} = (\sqrt[n]{x})^m$


**Grafi funkcij $f(x) = x^b$**

Opis grafov funkcij $f(x)=x^b$ za različne vrednosti eksponenta $b$:

*   **$b>1$**: Graf je parabola, ki se odpre navzgor (npr. $x^2$). Funkcija je naraščajoča na $[0, \infty)$ in poteka skozi $(0,0)$ in $(1,1)$.
*   **$b=1$**: Graf je ravna črta $y=x$. Funkcija je linearna, naraščajoča in poteka skozi $(0,0)$ in $(1,1)$.
*   **$0<b<1$**: Graf je konkavna krivulja (npr. $\sqrt{x}$). Funkcija je naraščajoča na $[0, \infty)$ in poteka skozi $(0,0)$ in $(1,1)$.
*   **$b<0$**: Graf je hiperbola (npr. $x^{-1} = 1/x$). Funkcija je padajoča na $(0, \infty)$ in ima asimptote $x=0$ (navpično) in $y=0$ (vodoravno). Poteka skozi $(1,1)$.

**Eksponentna funkcija**

Za dano osnovo $a>0$ se funkcija:
$$ f: \mathbb{R} \rightarrow (0, \infty) $$
$$ x \mapsto a^x $$
imenuje **eksponentna funkcija** z osnovo $a$.

Posebej pomemben primer je naravna eksponentna funkcija $e^x$, kjer je $e \approx 2.71828$.

**Grafi funkcij $g(x) = a^x$**

Opis grafov eksponentnih funkcij $g(x)=a^x$ za različne vrednosti osnove $a$:

*   **$a>1$**: Graf je strogo naraščajoč. Poteka skozi točko $(0,1)$. Ko $x \to -\infty$, se vrednosti funkcije približujejo $0$.
*   **$a=1$**: Graf je ravna črta $y=1$. Poteka skozi točko $(0,1)$.
*   **$0<a<1$**: Graf je strogo padajoč. Poteka skozi točko $(0,1)$. Ko $x \to \infty$, se vrednosti funkcije približujejo $0$.

**Logaritem**

Naj bo $a>0$, $a \neq 1$. Eksponentna funkcija $f: \mathbb{R} \rightarrow (0, \infty)$, $x \mapsto a^x$ je bijektivna.

Njena inverzna funkcija, $\log_a: (0, \infty) \rightarrow \mathbb{R}$, se imenuje **logaritem** z osnovo $a$.

Torej velja definicijska zveza:

$$ y = \log_a x \quad \iff \quad x = a^y $$

**Kotne (trigonometrične) funkcije**

Za $x \in \mathbb{R}$ definiramo funkciji **sinus** in **kosinus**, z označbama $\sin x$ in $\cos x$.

Funkciji $\sin$ in $\cos$ sta $2\pi$-periodični.



Če je $\cos x \neq 0$, definiramo še:
$$ \operatorname{tg} x := \frac{\sin x}{\cos x} $$
Funkcija $\operatorname{tg}$ se imenuje **tangens**. Je $\pi$-periodična.

**Inverzne trigonometrične (oz. ciklometrične) funkcije**

*   **arcsin**:
    Funkcija $\sin$ ni bijektivna na $\mathbb{R}$, postane pa bijektivna, če gledamo zožitev $\sin|_{[-\pi/2, \pi/2]} : [-\pi/2, \pi/2] \rightarrow [-1, 1]$.
    Inverz te funkcije se imenuje **inverzni sinus** oz. **arkus sinus**.
    Označba:
    $$ \arcsin : [-1, 1] \rightarrow [-\pi/2, \pi/2] $$

*   **arccos**:
    Funkcija $\cos$ ni bijektivna na $\mathbb{R}$, postane pa bijektivna, če gledamo zožitev $\cos|_{[0, \pi]} : [0, \pi] \rightarrow [-1, 1]$.
    Inverz te funkcije se imenuje **inverzni kosinus** oz. **arkus kosinus**.
    Označba:
    $$ \arccos : [-1, 1] \rightarrow [0, \pi] $$

*   **arctg**:
    Funkcija $\operatorname{tg}$ ni bijektivna na $\mathbb{R}$, postane pa bijektivna, če gledamo zožitev $\operatorname{tg}|_{(-\pi/2, \pi/2)} : (-\pi/2, \pi/2) \rightarrow \mathbb{R}$.
    Inverz te funkcije se imenuje **inverzni tangens** oz. **arkus tangens**.
    Označba:
    $$ \operatorname{arctg} : \mathbb{R} \rightarrow (-\pi/2, \pi/2) $$




