## Zveznost



**Definicija:** Naj bo $I \subseteq \mathbb{R}$ interval, $a \in I$ in $f: I \rightarrow \mathbb{R}$ funkcija.

Pravimo, da je $f$ **zvezna** v točki $a$, če za vsak $\varepsilon > 0$ obstaja $\delta > 0$ tako, da za vsak $x \in I$ velja:
$$ |x-a| < \delta \implies |f(x) - f(a)| < \varepsilon \quad (*)$$
Če $\delta$ obstaja je odvisen od $f, a, \varepsilon$.

Če je neki $\delta > 0$ ustrezen, je ustrezen tudi vsak $\delta' \in (0, \delta]$

**Definicija:** Funkcija $f$ je **zvezna na množici** $I$, če je zvezna v vsaki točki $x \in I$.

---

**Limita funkcije**

**Definicija:** Naj bo funkcija $f$ definirana na neki okolici $U$ točke $a \in \mathbb{R}$, toda ne nujno v $a$. Pravimo, da je število $L \in \mathbb{R}$ **limita funkcije** $f$ v točki $a$, oznaka: $L = \lim_{x \to a} f(x)$, če za vsak $\varepsilon > 0$ obstaja $\delta > 0$ tako, da za vsak $x \in U$ velja:
$$ 0 < |x-a| < \delta \implies |f(x) - L| < \varepsilon $$
**Opomba:** Razlika med definicijo limite in zveznosti je v pogoju $0 < |x-a|$, kar pomeni, da vrednost funkcije v točki $a$ (t.j. $f(a)$) ni pomembna ali pa sploh ni definirana.

**Opombe k pojmu limite**

*   Pojem limite smo doslej spoznali na zaporedjih.
*   Limita funkcije je neodvisna od izbire (ali celo obstoja!) funkcijske vrednosti v točki $a$ ($f(a)$)!


**Izrek:**

$$\text{predpostavimo da je }f(a) \text{ je definiran}$$
$$f \text{ je zvezna v točki }a \in U \Leftrightarrow \lim_{x \to a} f(x) \text{ obstaja in je enaka } f(a) $$

>[!|dokaz]- Dokaz:
> 
> **$(\Rightarrow)$ Zveznost $\implies \lim_{x \to a} f(x) = f(a)$:**
> Predpostavimo, da je $f$ zvezna v točki $a$. Po definiciji zveznosti to pomeni, da za vsak $\epsilon > 0$ obstaja $\delta > 0$ tak, da za vse $x \in U$, če $|x - a| < \delta$, potem $|f(x) - f(a)| < \epsilon$.
> Ta pogoj avtomatično velja tudi za $0 < |x - a| < \delta$ (saj je $0 < |x-a|$ strožji pogoj, ki izključi le točko $x=a$). To pa je natančno definicija limite $\lim_{x \to a} f(x) = f(a)$.
> 
> **$(\Leftarrow) \lim_{x \to a} f(x) = f(a) \implies$ Zveznost:**
> Predpostavimo, da $\lim_{x \to a} f(x) = f(a)$. To pomeni, da za vsak $\epsilon > 0$ obstaja $\delta > 0$ tak, da za vse $x \in U$, če $0 < |x - a| < \delta$, potem $|f(x) - f(a)| < \epsilon$.
> Sedaj želimo pokazati, da je $f$ zvezna v $a$, kar pomeni, da za vsak $\epsilon > 0$ obstaja $\delta > 0$ tak, da za vse $x \in U$, če $|x - a| < \delta$, potem $|f(x) - f(a)| < \epsilon$.
> Razlikujmo dva primera za $x$ pri danem $\delta$:
> 1.  **Če $0 < |x - a| < \delta$**: Iz predpostavke o limiti neposredno sledi $|f(x) - f(a)| < \epsilon$.
> 2.  **Če $|x - a| = 0$ (t.j. $x = a$)**: Potem je $|f(x) - f(a)| = |f(a) - f(a)| = 0$. Ker je $0 < \epsilon$ za vsak $\epsilon > 0$, pogoj $|f(x) - f(a)| < \epsilon$ velja tudi v tem primeru.
> Ker pogoj $|f(x) - f(a)| < \epsilon$ velja za oba primera ($x \neq a$ in $x = a$), velja za vse $x$ z $|x - a| < \delta$. To je definicija zveznosti funkcije $f$ v točki $a$.
---

Vsota, razlika, produkt in kvocient limit je enak limiti vsote, razlike, produkta in kvocienta
>[!|dokaz]- Dokaz:
> Naj bosta $f$ in $g$ funkciji, za kateri velja $\lim_{x \to c} f(x) = L_1$ in $\lim_{x \to c} g(x) = L_2$.
> 
> **Vsota (in razlika) limit:**
> Želimo pokazati, da je $\lim_{x \to c} (f(x) + g(x)) = L_1 + L_2$.
> Za dani $\epsilon > 0$ iščemo $\delta > 0$.
> Imamo $|(f(x) + g(x)) - (L_1 + L_2)| = |(f(x) - L_1) + (g(x) - L_2)|$.
> Po trikotni neenakosti je to $\le |f(x) - L_1| + |g(x) - L_2|$.
> Ker je $\lim_{x \to c} f(x) = L_1$, obstaja $\delta_1 > 0$ tako, da $0 < |x-c| < \delta_1 \implies |f(x) - L_1| < \epsilon/2$.
> Ker je $\lim_{x \to c} g(x) = L_2$, obstaja $\delta_2 > 0$ tako, da $0 < |x-c| < \delta_2 \implies |g(x) - L_2| < \epsilon/2$.
> Izberemo $\delta = \min(\delta_1, \delta_2)$. Potem za $0 < |x-c| < \delta$ velja:
> $|f(x) - L_1| + |g(x) - L_2| < \epsilon/2 + \epsilon/2 = \epsilon$.
> Torej je $\lim_{x \to c} (f(x) + g(x)) = L_1 + L_2$.
> Dokaz za razliko poteka analogno.
> 
> **Produkt limit:**
> Želimo pokazati, da je $\lim_{x \to c} (f(x) \cdot g(x)) = L_1 \cdot L_2$.
> Za dani $\epsilon > 0$ iščemo $\delta > 0$.
> Imamo $|f(x)g(x) - L_1L_2| = |f(x)g(x) - f(x)L_2 + f(x)L_2 - L_1L_2| = |f(x)(g(x) - L_2) + L_2(f(x) - L_1)|$.
> Po trikotni neenakosti je to $\le |f(x)||g(x) - L_2| + |L_2||f(x) - L_1|$.
> Ker ima $f$ limito $L_1$, obstaja $\delta_0 > 0$ tako, da za $0 < |x-c| < \delta_0$ velja $|f(x) - L_1| < 1$, kar pomeni $|f(x)| < |L_1| + 1$. Naj bo $M = \max(|L_1|+1, 1)$.
> Izberemo $\delta_1$ tako, da $0 < |x-c| < \delta_1 \implies |g(x) - L_2| < \frac{\epsilon}{2M}$.
> Izberemo $\delta_2$ tako, da $0 < |x-c| < \delta_2 \implies |f(x) - L_1| < \frac{\epsilon}{2(|L_2|+1)}$.
> Izberemo $\delta = \min(\delta_0, \delta_1, \delta_2)$. Potem za $0 < |x-c| < \delta$ velja:
> $|f(x)||g(x) - L_2| + |L_2||f(x) - L_1| < M \cdot \frac{\epsilon}{2M} + |L_2| \cdot \frac{\epsilon}{2(|L_2|+1)} < \frac{\epsilon}{2} + \frac{\epsilon}{2} = \epsilon$.
> Torej je $\lim_{x \to c} (f(x) \cdot g(x)) = L_1 \cdot L_2$.
> 
> **Kvocient limit:**
> Želimo pokazati, da je $\lim_{x \to c} \frac{f(x)}{g(x)} = \frac{L_1}{L_2}$, pod pogojem, da je $L_2 \neq 0$.
> Najprej dokažemo, da je $\lim_{x \to c} \frac{1}{g(x)} = \frac{1}{L_2}$.
> Ker $L_2 \ne 0$, izberemo $\epsilon_0 = |L_2|/2$. Obstaja $\delta_0 > 0$ tako, da za $0 < |x-c| < \delta_0$ velja $|g(x) - L_2| < |L_2|/2$. To pomeni, da $|g(x)| > |L_2|/2$.
> Zdaj obravnavajmo $|\frac{1}{g(x)} - \frac{1}{L_2}| = |\frac{L_2 - g(x)}{g(x)L_2}| = \frac{|g(x) - L_2|}{|g(x)||L_2|}$.
> Upoštevajoč $|g(x)| > |L_2|/2$, imamo $\frac{1}{|g(x)|} < \frac{2}{|L_2|}$.
> Torej je $\frac{|g(x) - L_2|}{|g(x)||L_2|} < \frac{|g(x) - L_2|}{\frac{|L_2|}{2} \cdot |L_2|} = \frac{2|g(x) - L_2|}{|L_2|^2}$.
> Za dani $\epsilon > 0$ izberemo $\delta_1$ tako, da za $0 < |x-c| < \delta_1$ velja $|g(x) - L_2| < \frac{\epsilon |L_2|^2}{2}$.
> Izberemo $\delta = \min(\delta_0, \delta_1)$. Potem za $0 < |x-c| < \delta$ velja:
> $\frac{2|g(x) - L_2|}{|L_2|^2} < \frac{2}{|L_2|^2} \cdot \frac{\epsilon |L_2|^2}{2} = \epsilon$.
> Sledi, da je $\lim_{x \to c} \frac{1}{g(x)} = \frac{1}{L_2}$.
> Sedaj uporabimo pravilo za produkt limit:
> $\lim_{x \to c} \frac{f(x)}{g(x)} = \lim_{x \to c} \left(f(x) \cdot \frac{1}{g(x)}\right) = \left(\lim_{x \to c} f(x)\right) \cdot \left(\lim_{x \to c} \frac{1}{g(x)}\right) = L_1 \cdot \frac{1}{L_2} = \frac{L_1}{L_2}$

**Razširitev funkcije in limita**

Koncept limite ter karakterizacijo zveznosti z limitami lahko uporabimo za zvezno razširjanje funkcije v dano točko (če je to mogoče).

**Izrek:** Naj bosta $D \subseteq \mathbb{R}$ in $a \in \mathbb{R}$ takšni, da je $d(a,D) = \inf\{|x-a| \mid x \in D \setminus \{a\}\} = 0$.
(Pomen: ne želimo, da bi bila $D$ in $f$ "narazen".)

Imamo funkcijo $f: D \setminus \{a\} \rightarrow \mathbb{R}$. Naslednji izjavi sta ekvivalentni:
i) $\lim_{x \to a} f(x) = L$
ii) Funkcija $\bar{f}: D \cup \{a\} \rightarrow \mathbb{R}$, definirana s predpisom
$$ \bar{f}(x) = \begin{cases} f(x); & x \in D \setminus \{a\} \\ L; & x = a \end{cases} $$
je zvezna v točki $a$.

Dokaz sledi iz definicije.


---

**Enostranske limite**

**Definicija:** Naj bo $D \subseteq \mathbb{R}$ takšen, da je $D \cap (a, a+\varepsilon) \neq \emptyset$ za vsak $\varepsilon > 0$. Naj bo še $f: D \rightarrow \mathbb{R}$. Število $L_+ \in \mathbb{R}$ je **desna limita** funkcije $f$ v točki $a$, če za vsako zaporedje $(a_n)_{n \in \mathbb{N}} \subseteq D \cap (a, \infty)$ takšno, da $a_n \to a$, sledi $f(a_n) \to L_+$.
Označba: $L_+ = \lim_{x \to a^+} f(x) = f(a+0)$.

**Podobno definiramo levo limito:**
**Definicija:** Število $L_- \in \mathbb{R}$ je **leva limita** funkcije $f$ v točki $a$, če za vsako zaporedje $(a_n)_{n \in \mathbb{N}} \subseteq D \cap (-\infty, a)$ takšno, da $a_n \to a$, sledi $f(a_n) \to L_-$.
Označba: $L_- = \lim_{x \to a^-} f(x) = f(a-0)$.

**Trditev:** Imejmo $D \subseteq \mathbb{R}$ in $a \in \mathbb{R}$ takšen, da za vsak $\varepsilon > 0$ je $D \cap (a, a-\varepsilon) \neq \emptyset$ in $D \cap (a, a+\varepsilon) \neq \emptyset$. Naj bo še $f: D \rightarrow \mathbb{R}$. Tedaj:
$$ \exists \lim_{x \to a} f(x) = L \quad \iff \quad \begin{cases} \exists \lim_{x \to a^+} f(x) =: L_+ \\ \exists \lim_{x \to a^-} f(x) =: L_- \\ L_+ = L_- \end{cases} $$
V tem primeru je $L=L_+=L_-$.

**Definicija:** Naj bodo izpolnjeni pogoji trditve. Če $L_-$ in $L_+$ obstajata, a sta različna, pravimo, da ima $f$ v točki $a$ **skok**.

---

**Odsekoma zvezne funkcije**

**Definicija:** Funkcija $f$ je na intervalu $D$ **odsekoma zvezna**, če je zvezna povsod na $D$, razen morda v končno mnogo točkah, v katerih pa ima skok.
>
> Velja
> $$\lim_{x \to 0}\frac{\sin(x) }{x} = 1$$
> >[!|dokaz]- Dokaz:
> >Predpostavimo geometrijsko neenakost za $x \in (0, \frac{\pi}{2})$:
> > $\sin x < x < \tan x$.
> > 
> > Delimo neenakost s $\sin x$:
> > $1 < \frac{x}{\sin x} < \frac{\tan x}{\sin x}$.
> > Poenostavimo desno stran:
> > $1 < \frac{x}{\sin x} < \frac{1}{\cos x}$.
> > 
> > Vzamemo recipročne vrednosti in s tem obrnemo neenakosti:
> > $\cos x < \frac{\sin x}{x} < 1$.
> > 
> > Ko $x \to 0^+$, velja $\lim_{x \to 0^+} \cos x = 1$.
> > Po izreku o sendviču sledi, da je $\lim_{x \to 0^+} \frac{\sin x}{x} = 1$.
> > 
> > Za $x \to 0^-$, naj bo $x = -y$, kjer $y \to 0^+$.
> > $\lim_{x \to 0^-} \frac{\sin x}{x} = \lim_{y \to 0^+} \frac{\sin (-y)}{-y} = \lim_{y \to 0^+} \frac{-\sin y}{-y} = \lim_{y \to 0^+} \frac{\sin y}{y} = 1$.
> > 
> > Ker sta leva in desna limita enaki, velja:
> > $\lim_{x \to 0} \frac{\sin x}{x} = 1$.


Torej lahko funkcijo $f(x)=\frac{\sin x}{x}$ zvezno razširimo v $x=0$ tako, da določimo $f(0)=1$.

**Sendvič izrek (Squeeze Theorem)**

**Trditev:** Naj bo $a \in \mathbb{R}$ in naj za funkcije $f, g, h$ velja:
*   $f(x) \le g(x) \le h(x)$ na neki okolici točke $a$.
*   $\lim_{x \to a} f(x) = L$ in $\lim_{x \to a} h(x) = L$ (če limiti obstajata in sta enaki).
Tedaj je tudi $\lim_{x \to a} g(x) = L$.

>[!|dokaz]- Dokaz:
> Naj bodo funkcije $f, g, h$ definirane na nekem odprtem intervalu, ki vsebuje $c$, morda razen pri $c$ samem.
> Predpostavimo, da za vse $x$ na tem intervalu velja $g(x) \le f(x) \le h(x)$.
> Prav tako predpostavimo, da je $\lim_{x \to c} g(x) = L$ in $\lim_{x \to c} h(x) = L$.
> 
> Naj bo $\epsilon > 0$ poljubno.
> 
> Ker $\lim_{x \to c} g(x) = L$, obstaja $\delta_1 > 0$ tako, da za vsak $x$, ki zadošča $0 < |x-c| < \delta_1$, velja $L - \epsilon < g(x) < L + \epsilon$. Iz tega potrebujemo le $L - \epsilon < g(x)$.
> 
> Ker $\lim_{x \to c} h(x) = L$, obstaja $\delta_2 > 0$ tako, da za vsak $x$, ki zadošča $0 < |x-c| < \delta_2$, velja $L - \epsilon < h(x) < L + \epsilon$. Iz tega potrebujemo le $h(x) < L + \epsilon$.
> 
> Izberemo $\delta = \min(\delta_1, \delta_2)$. Za vsak $x$, ki zadošča $0 < |x-c| < \delta$, veljajo obe neenakosti:
> $L - \epsilon < g(x)$ in $h(x) < L + \epsilon$.
> 
> Ker je po predpostavki $g(x) \le f(x) \le h(x)$, lahko združimo neenakosti:
> $L - \epsilon < g(x) \le f(x) \le h(x) < L + \epsilon$.
> 
> Torej, za vsak $x$, za katerega velja $0 < |x-c| < \delta$, imamo $L - \epsilon < f(x) < L + \epsilon$.
> To je enakovredno $|f(x) - L| < \epsilon$.
> 
> Ker smo za poljuben $\epsilon > 0$ našli ustrezen $\delta > 0$, po definiciji limite sledi, da je $\lim_{x \to c} f(x) = L$.

---

**Karakterizacija limite s pomočjo zaporedij**

**Izrek:** Naj bo $a \in \mathbb{R}$ in $U$ okolica točke $a$. Naj bo $f: U \setminus \{a\} \rightarrow \mathbb{R}$. Tedaj na $L \in \mathbb{R}$ velja:
$\lim_{x \to a} f(x) = L \iff$ za vsako zaporedje $(x_n)_{n \in \mathbb{N}}$ iz $U \setminus \{a\}$ velja:
$x_n \to a \implies f(x_n) \to L$.

Dokaz ($\implies$): Vzamemo $\varepsilon > 0$. Po definiciji limite funkcije obstaja $\delta > 0$ takšen, da $0 < |x-a| < \delta \implies |f(x)-L| < \varepsilon$. Naj bo $(x_n)_{n \in \mathbb{N}}$ zaporedje iz $U \setminus \{a\}$ z $x_n \to a$. Po definiciji konvergence zaporedja obstaja $N \in \mathbb{N}$ takšen, da je $|x_n-a| < \delta$ za $n \ge N$. Posledično za takšne $n$ velja $|f(x_n)-L| < \varepsilon$. To pomeni, da $f(x_n) \to L$.

Dokaz ($\impliedby$, s protislovjem): Denimo, da $f \not\to L$. Torej obstaja $\varepsilon > 0$ takšen, da za vsak $n \in \mathbb{N}$ obstaja $x_n \in U \setminus \{a\}$ takšen, da $0 < |x_n-a| < 1/n$ (lahko izberemo $\delta_n=1/n$) in $|f(x_n)-L| \ge \varepsilon$.
Torej $x_n \to a$, toda $f(x_n) \not\to L$, kar je ravno negacija druge izjave (naše predpostavke).


***

Predpostavimo da $f(a)$ obstaja oz. je $a \in U$.

$f: U \rightarrow \mathbb{R} \text{ je zvezna v }a \in U \iff \text{ je zvezna po zaporedjih v }a$

tj., za vsako zaporedje $(x_n)_{n \in \mathbb{N}} \subseteq U$ na katero je $\lim_{n \to \infty} x_n = a$, velja $\lim_{n \to \infty} f(x_n) = f(a)$.

---

**Zveznost aritmetičnih operacij in kompozituma**

Spomnimo se definicij operacij na funkcijah:
$(f+g)(x) := f(x)+g(x)$
$(fg)(x) := f(x)g(x)$
$(f/g)(x) := f(x)/g(x)$, kjer $D_{f/g} := \{x \in D_f \cap D_g \mid g(x) \neq 0\}$

**Trditev:** Vsota, razlika, produkt in kvocient zveznih funkcij so spet zvezni.

>[!|dokaz]- Dokaz:
> Naj bosta $f$ in $g$ zvezni funkciji v točki $c$. To pomeni, da je $\lim_{x \to c} f(x) = f(c)$ in $\lim_{x \to c} g(x) = g(c)$.
> 
> **Vsota:**
> $\lim_{x \to c} (f(x) + g(x)) = \lim_{x \to c} f(x) + \lim_{x \to c} g(x) = f(c) + g(c) = (f+g)(c)$.
> Zato je $f+g$ zvezna pri $c$.
> 
> **Razlika:**
> $\lim_{x \to c} (f(x) - g(x)) = \lim_{x \to c} f(x) - \lim_{x \to c} g(x) = f(c) - g(c) = (f-g)(c)$.
> Zato je $f-g$ zvezna pri $c$.
> 
> **Produkt:**
> $\lim_{x \to c} (f(x) \cdot g(x)) = \lim_{x \to c} f(x) \cdot \lim_{x \to c} g(x) = f(c) \cdot g(c) = (f \cdot g)(c)$.
> Zato je $f \cdot g$ zvezna pri $c$.
> 
> **Kvocient:**
> Predpostavimo, da je $g(c) \neq 0$.
> $\lim_{x \to c} \frac{f(x)}{g(x)} = \frac{\lim_{x \to c} f(x)}{\lim_{x \to c} g(x)} = \frac{f(c)}{g(c)} = \left(\frac{f}{g}\right)(c)$.
> Zato je $\frac{f}{g}$ zvezna pri $c$, če $g(c) \neq 0$.

**Posledica:** Vsi polinomi so zvezni, vse racionalne funkcije so zvezne na svojih definirnih območjih.


**Trditev (o zveznosti kompozituma):** Naj bosta $D, E \subseteq \mathbb{R}$. Če sta $f: D \rightarrow E$ in $g: E \rightarrow \mathbb{R}$ obe zvezni, tedaj je tudi $g \circ f: D \rightarrow \mathbb{R}$ zvezna.
To je, komponiranje ohranja zveznost.

>[!|dokaz]- Dokaz:
> Ker je $f$ zvezna v točki $g(c)$, za vsak $\epsilon > 0$ obstaja $\delta_1 > 0$ tako, da če $|y - g(c)| < \delta_1$, potem velja $|f(y) - f(g(c))| < \epsilon$.
> 
> Ker je $g$ zvezna v točki $c$, za to določeno $\delta_1$ (ki jo obravnavamo kot $\epsilon$ za funkcijo $g$) obstaja $\delta_2 > 0$ tako, da če $|x - c| < \delta_2$, potem velja $|g(x) - g(c)| < \delta_1$.
> 
> Sedaj združimo ti dve ugotovitvi. Izberemo $x$ tako, da velja $|x - c| < \delta_2$. Po drugi izjavi to pomeni, da je $|g(x) - g(c)| < \delta_1$. Naj bo $y = g(x)$. Potem velja $|y - g(c)| < \delta_1$. Po prvi izjavi to pa pomeni, da je $|f(y) - f(g(c))| < \epsilon$.
> Torej, če $|x - c| < \delta_2$, potem je $|f(g(x)) - f(g(c))| < \epsilon$.
> 
> S tem smo pokazali, da za poljuben $\epsilon > 0$ obstaja $\delta_2 > 0$ (ki jo lahko preprosto poimenujemo $\delta$), tako da če $|x - c| < \delta$, potem $|(f \circ g)(x) - (f \circ g)(c)| < \epsilon$. Po definiciji limite to pomeni, da je $\lim_{x \to c} (f \circ g)(x) = (f \circ g)(c)$, in torej je kompozitum $f \circ g$ zvezna funkcija v točki $c$.

**Izrek:** Vsaka elementarna funkcija je zvezna povsod na svojem definicijskem območju.


---

**Zvezne funkcije na kompaktnih množicah v $\mathbb{R}$**

**Odprte podmnožice poljubne množice**

Množica je odprta natanko tedaj ko velja da za vsako točko v množici obstaja odprta krogla oz. interval ki je poplnoma vsebovan v njej.

Naj bo $D$ množica v $\mathbb{R}$. $A$ je **odprta v $D$** če velja da obstaja odprta množica $A'$ v $\mathbb{R}$ tako da je $A' \cap D = A$.


**Trditev:** Naj bo $A \subseteq D$.
$A$ je odprta v $D \iff$ za vsak $a \in A$ obstaja $\delta_a > 0$ takšen, da $K(a, \delta_a) \cap D \subseteq A$.
> [!|dokaz]- Dokaz:
> 
> **$(\Rightarrow)$**
> 1. Predpostavimo, da je $A$ odprta v $D$. Po definiciji torej obstaja odprta množica $A'$ takšna, da $A = A' \cap D$.
> 2. Vzemimo poljuben $a \in A$. Ker $A = A' \cap D$, je $a \in A'$.
> 3. Ker je $A'$ odprta, obstaja $\delta_a > 0$ takšen, da $K(a, \delta_a) \subseteq A'$.
> 4. Potem $K(a, \delta_a) \cap D \subseteq A' \cap D$. Ker $A' \cap D = A$, sledi $K(a, \delta_a) \cap D \subseteq A$.
> 
> **$(\Leftarrow)$**
> 1. Predpostavimo, da za vsak $a \in A$ obstaja $\delta_a > 0$ takšen, da $K(a, \delta_a) \cap D \subseteq A$.
> 2. Definirajmo $A' = \bigcup_{a \in A} K(a, \delta_a)$. Množica $A'$ je odprta, saj je unija odprtih množic vedno odprta.
> 3. Pokažimo, da $A = A' \cap D$:
>     *   **$A \subseteq A' \cap D$:** Za vsak $a \in A$, je $a \in K(a, \delta_a)$ (po definiciji krogle), torej $a \in A'$. Ker $a \in A \subseteq D$, je $a \in A' \cap D$.
>     *   **$A' \cap D \subseteq A$:** Za vsak $x \in A' \cap D$, obstaja $a \in A$ tak, da $x \in K(a, \delta_a)$. Ker tudi $x \in D$, je $x \in K(a, \delta_a) \cap D$. Po predpostavki pa $K(a, \delta_a) \cap D \subseteq A$. Zato $x \in A$.
> 4. Ker je $A = A' \cap D$ in je $A'$ odprta v $X$, je po definiciji $A$ odprta v $D$.
> 

**Trditev: Če** je $D$ odprta v $\mathbb{R}$ in $A \subseteq D$, tedaj je $A$ odprta v $D \iff A$ odprta v $\mathbb{R}$.



>[!|dokaz]- Dokaz:
>
> $(\implies)$ $W = D \cap U'$ za $U'$ odprta v $\mathbb{R}$. Ker je $D$ odprta v $\mathbb{R}$ in $U'$ odprta v $\mathbb{R}$, je $W$ presek dveh odprtih množic, torej je $W$ odprta v $\mathbb{R}$.
> $(\impliedby)$ Velja $W = W \cap D$. Ker je $W$ odprta v $\mathbb{R}$, je po definiciji odprta v $D$.

**Karakterizacija zveznosti z inverznimi slikami odprtih množic**

**Trditev:** 
Naj bo $D \subseteq \mathbb{R}$ in $f: D \rightarrow \mathbb{R}$. 

$f$ je zvezna $\iff$ za vsako odprto množico $V \subseteq \mathbb{R}$ je $f^{-1}(V)$ spet odprta množica v $D$

*V je množica na $y$ osi. $f^{-1}(V)$ je množica iz katere slikamo v $V$. Predstavljamo si da je odprta množica ki zahteva sliko iz roba $D$, to pomeni da je odprta v $D$ in ne v $\mathbb{R}$.*

To pomeni: $f^{-1}(V) = U \cap D$, kjer je $U$ odprta v $\mathbb{R}$.

Ekvivalentno, za vsak $a \in f^{-1}(V)$ obstaja $\delta_a > 0$ takšen, da $K(a, \delta_a) \cap D \subseteq f^{-1}(V)$.

>[!|dokaz]- Dokaz:
>
> Dokaz $(\implies)$: 
> Vzamemo $V$ odprto v $\mathbb{R}$ *( y os )* in $a \in f^{-1}(V)$.
> Torej $f(a) \in V$. 
> Ker je $V$ odprta, obstaja $\varepsilon > 0$ takšen, da $K(f(a), \varepsilon) \subseteq V$. 
> Ker je $f$ zvezna v točki $a$, obstaja $\delta > 0$ takšen, da za $x \in D$ in $|x-a|<\delta$ velja $|f(x)-f(a)| < \varepsilon$.
> To pomeni, da $f(K(a, \delta) \cap D) \subseteq K(f(a), \varepsilon)$.
> 
> Drugače rečeno, $K(a, \delta) \cap D \subseteq f^{-1}(K(f(a), \varepsilon))$. Ker je $K(f(a), \varepsilon) \subseteq V$, je $f^{-1}(K(f(a), \varepsilon)) \subseteq f^{-1}(V)$.
> Zato je $K(a, \delta) \cap D \subseteq f^{-1}(V)$. Po prejšnji trditvi je $f^{-1}(V)$ odprta v $D$.
> 
> Dokaz $(\impliedby)$: Vzamemo $a \in D, \varepsilon > 0$ in definiramo $V:= K(f(a), \varepsilon)$. Ker je $V$ odprta v $\mathbb{R}$, je po predpostavki $f^{-1}(V) = \{x \in D \mid f(x) \in V\} = \{x \in D \mid |f(x)-f(a)| < \varepsilon\}$ odprta v $D$. Ker je $a \in f^{-1}(V)$, torej obstaja $\delta > 0$ takšen, da $K(a, \delta) \cap D \subseteq f^{-1}(V)$.
> To pomeni, da za $x \in K(a, \delta) \cap D$ velja $|f(x)-f(a)| < \varepsilon$, kar je ravno zveznost $f$ v točki $a$. Ker je bil $a \in D$ poljuben, je dokaz končan.

**Definicija:** 
Množica $K \subseteq \mathbb{R}$ je **kompaktna**, če je v $\mathbb{R}$ zaprta in omejena.
To tudi pomeni da ima vsako zaporedje stekališče v množici.
*Zaprtost je da če ima zaporedje limito je vsebovana v množici, omejenost pa da ima vsako zaporedje stekališče.*

**Izrek (Weierstrassov izrek o ekstremnih vrednostih)**

**Izrek:** Naj bo $K \subseteq \mathbb{R}$ kompaktna in $f: K \rightarrow \mathbb{R}$ zvezna. Tedaj je $f$ omejena in doseže minimum ter maksimum.

>[!|dokaz]- Dokaz:
>
> Če dokažemo da je $f(K)$ kompaktna potem vemo da je zaprta in omejena, torej velja da vsebuje svoj $\min$ in $\max$.
> 
> Vzemimo poljubno zaporedje $(y_n)$ v $f(K)$.
> Ker je $y_n \in f(K)$, za vsak $n$ obstaja $x_n \in K$, tako da je $y_n = f(x_n)$.
> Tako dobimo zaporedje $(x_n)$ v $K$.
> Ker je $K$ kompaktna, ima zaporedje $(x_n)$ konvergentno podzaporedje $(x_{n_k})$, ki konvergira k neki točki $x \in K$.
> Ker je $f$ zvezna, velja $\lim_{k \to \infty} f(x_{n_k}) = f(x)$.
> Po definiciji je $y_{n_k} = f(x_{n_k})$, zato podzaporedje $(y_{n_k})$ konvergira k $f(x)$.
> Ker $x \in K$, je $f(x) \in f(K)$.
> S tem smo pokazali, da ima vsako zaporedje v $f(K)$ konvergentno podzaporedje, katerega limita leži v $f(K)$, kar pomeni, da je $f(K)$ kompaktna množica.
> 
> Ker je $f(K)$ kompaktna je omejena torej obstaja $\inf$ in $\sup$. Ker sta to stekališči in je $f(K)$ zaprta sta vsebovani v $f(K)$ in sta $\max$ in $\min$ vsebovani v $f(K)$ torej obstaja $x_{1,2}$ ki dosežeta pripdajoči vrednosti. 

---

**Bolzanov izrek (Intermediate Value Theorem)**

**Izrek:** Naj bo $f: [a,b] \rightarrow \mathbb{R}$ zvezna in $f(a)f(b) < 0$. Tedaj obstaja $\xi \in (a,b)$ takšen, da $f(\xi) = 0$.


Dokaz: Interval $I_0=[a,b]$ razpolovimo. To pomeni, da pogledamo levo in desno polovico intervala $I_0$, torej $[a, \frac{a+b}{2}]$ in $[\frac{a+b}{2}, b]$.
Če je $f(\frac{a+b}{2}) = 0$, smo iskano $\xi$ že našli (in sicer $\xi = \frac{a+b}{2}$).
Če pa ne, potem za $I_1$ označimo tisto izmed polovic, na kateri ima $f$ v krajiščih različno predznačene vrednosti. Torej:
$$ I_1 = \begin{cases} [a, \frac{a+b}{2}]; & \text{če } f(a)f(\frac{a+b}{2}) < 0 \\ [\frac{a+b}{2}, b]; & \text{če } f(\frac{a+b}{2})f(b) < 0 \end{cases} $$
S postopkom nadaljujemo. Če se ustavi po končno mnogo korakih, smo našli točko $\xi$, kjer je $f(\xi) = 0$. Sicer pa dobimo zaporedje zavitih intervalov $I_n = [a_n, b_n] \subseteq [a,b] = I_0$ takšnih, da:
*   $a_n \leq a_{n+1}$ in $b_{n+1} \leq b_n$
*   $|I_n| = 2^{-n} |I_0|$
*   $f(a_n)f(b_n) < 0$.
Ker sta zaporedji $(a_n)_{n \in \mathbb{N}}$ ter $(b_n)_{n \in \mathbb{N}}$ omejeni in monotoni, imata limiti:
$\alpha := \lim_{n \to \infty} a_n = \sup a_n$
$\beta := \lim_{n \to \infty} b_n = \inf b_n$
Ker je $[a_n, b_n]$ zaprt interval, sta $\alpha, \beta \in I_0$. Sledi:
$|\alpha-\beta| = \beta-\alpha = b_n-a_n = |I_n| = 2^{-n}|I_0| \to 0$ ko $n \to \infty$.
Torej $\alpha = \beta =: \xi$.
Ker je $f$ zvezna in $a_n, b_n, \xi \in I_0$, sledi:
$f(\xi) = \lim_{n \to \infty} f(a_n)$
$f(\xi) = \lim_{n \to \infty} f(b_n)$
Iz $f(a_n)f(b_n) < 0$ sledi $f(\xi)f(\xi) \le 0$, to je, $f(\xi)^2 \le 0$. Ker pa je $f(\xi) \in \mathbb{R}$, mora biti $f(\xi)^2 \ge 0$. Edina možnost je $f(\xi)^2=0$, kar pomeni $f(\xi)=0$.
Torej smo spet našli takšno $\xi$.

**Posledica:** Naj bo $-\infty < a < b < \infty$, $I := [a,b]$ in $f: I \rightarrow \mathbb{R}$ zvezna. Tedaj obstajata $x_-, x_+ \in I$ takšna, da:
*   za vsak $x \in I$ je $f(x) \in [f(x_-), f(x_+)]$ (omejenost)
*   za vsak $y \in [f(x_-), f(x_+)]$ obstaja $x \in I$ takšen, da $y = f(x)$ (doseže vse vmesne vrednosti).


---

**Inverzna funkcija zvezne funkcije**

**Izrek:** Naj bo $I$ (kakršenkoli interval v $\mathbb{R}$ med $a$ in $b$ (tu sta $-\infty \le a < b \le \infty$)) in naj bo $f: I \rightarrow \mathbb{R}$ zvezna in strogo monotona. Tedaj je $f(I)$ interval med točkama $f(a^+)$ in $f(b^-)$. Inverzna funkcija $f^{-1}: f(I) \rightarrow I$ je zvezna.

Dokaz: Označimo $g = f^{-1}: f(I) \rightarrow \mathbb{R}$. Uporabimo karakterizacijo zveznosti s pomočjo praslike odprtih množic. Torej dokazujemo:
Za vsako odprto množico $V \subseteq \mathbb{R}$ je $g^{-1}(V)$ spet odprta množica v $f(I)$.
Velja $g^{-1}(V) = \{x \in f(I) \mid g(x) \in V\}$. Ker $g(x)=f^{-1}(x)$, je $g(x) \in V \iff x = f(g(x)) \in f(V)$.
Torej $g^{-1}(V) = \{x \in f(I) \mid f^{-1}(x) \in V\} = f(V \cap I)$.
Torej dokazujemo, da je za vsako odprto množico $V \subseteq \mathbb{R}$, množica $f(V \cap I)$ spet odprta množica v $f(I)$.
Ekvivalentno, za vsak $y \in f(V \cap I)$ obstaja $\delta > 0$ takšen, da $K(y, \delta) \cap f(I) \subseteq f(V \cap I)$.

Pišimo $y = f(x)$, $x \in V \cap I$. Privzemimo, da $f$ narašča (če pada, ravnamo analogno).
Če je $x \in \operatorname{Int}(I)$, obstaja $\sigma > 0$ takšen, da $K(x, \sigma) \subseteq V \cap I$. Ker je $f$ zvezna in naraščajoča, je $f(K(x, \sigma)) = (f(x-\sigma), f(x+\sigma))$. Za
$\delta := \min\{f(x)-f(x-\sigma), f(x+\sigma)-f(x)\}$ (kar pomeni $(f(x)-\delta, f(x)+\delta) \subseteq (f(x-\sigma), f(x+\sigma))$)
je $K(y, \delta) \cap f(I) \subseteq f(K(x, \sigma)) \subseteq f(V \cap I)$.
Naj bo sedaj $x \in \partial I = \{a,b\}$. Privzemimo, da $x=a \in I$.
Ker $a \in V$, obstaja $\sigma \in (0, b-a)$ takšen, da $K(a, \sigma) \subseteq V$. Tedaj je $[a, a+\sigma) = K(a, \sigma) \cap I \subseteq V \cap I$.
Velja:
$K(y, \delta) \cap f(I) = K(f(a), \delta) \cap f(I)$.
Za $\delta := f(a+\sigma)-f(a)$ dobimo $K(f(a), \delta) \cap f(I) = [f(a), f(a)+\delta) = [f(a), f(a+\sigma)) = f([a, a+\sigma))$.
Saj $f$ narašča in je zvezna, zato $f([a, a+\sigma)) \subseteq f(V \cap I)$. Kar je bilo treba dokazati.


***

Funkcija je **enakomerno zvezna** če velja da za vsak $\varepsilon$ velja da obstaja tak $\delta$ da za vsak $x,a$ na $D$ velja 

$$|x-a|<\delta \Rightarrow |f(a)-f(x)| < \varepsilon$$



>**Izrek**
>Če je funkcija definirana na zaprtem intervalu potem velja da je enakomerno zvezna.
>>[!|dokaz]+ Dokaz:
>> Predpostavimo da smo na $[a,b]$ in da funkcija ni enakomerno zvezna. To pomeni da obstaja $\varepsilon$ - izberimo $\varepsilon_{0}$ tako da velja da za vsak $\delta$ obstaja $x,a$  da velja $|x-a| < \delta$ in $|f(a)-f(x)| > \varepsilon_{0}$
>> 
>> 
>> Izrek naj bi deloval za vse $\delta$ kar pomeni da lahko sestavimo zaporedje $\delta_{n} = \frac{1}{n}$, ki nam bo pomagal pokazati protislovje.
>> Sedaj lahko izberemo poljubno zaporedje $x_{n}$, ker je na kompaktni množici obstaja konvergentno podzapordje $x_{n_{k}} =: x_{k}$.
>> Ko gre $x_{k}$ k $a$ velja da gre $|x_{k}-a|$ v 0. Ker je funkcija zvezna velja da gre $f(x_{k})$v $f(a)$ kar pomeni da gre $|f(x_{k})-f(a)|$ v 0 kar pomeni da si lahko izebremo taka $x,a$ da je  večje od $\varepsilon_{0}$.
