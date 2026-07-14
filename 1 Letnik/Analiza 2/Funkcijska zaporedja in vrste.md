# Funkcijska zaporedja in vrste

Naj bo $D \subset \mathbb{R}$ in $f_{n} : D \rightarrow \mathbb{R}$ funkcije za vsak $n \in \mathbb{N}$. Pravimo da je $f_{n}$ **funkcijsko zaporedje**.

Če za vsak $x \in D$ številsko zaporedje konvergira, pravimo da funkcijsko zaporedje $f_{n}$ **konvergira** na $D$.

Tako lahko definiramo $f(x) = \lim_{n \to \infty}f_{n}(x)$ čemur pravimo **limitna funkcija**. 

Temu pravimo tudi **konvergenca po točkah.**

$$\forall x, \forall \varepsilon, \exists N, \forall n: n>N \Rightarrow |f_{n}(x) - f(x)| < \varepsilon$$

Funkcijsko zaporedje **enakomerno konvergira** k funciji $f: D \rightarrow \mathbb{R}$ ko velja 

$$\forall \varepsilon, \exists N, \forall x, \forall n: n>N \Rightarrow |f_{n}(x) - f(x)| < \varepsilon$$

> Če funkcija konvergira enakomerno potem konvergira po točkah.

Funkcija konvergira enakomerno tudi če konvergira zaporedje supremumov razlike k $0$.

$$M_{n} = \sup|f_{n}(x)-f(x)|$$
$$\lim_{n \to \infty}M_{n} = 0$$

Funkcijsko zaporedje je **enakomerno Cauchyjevo** če velja

$$\forall \varepsilon, \exists N, \forall x, \forall m,n > N : \sup|f_{n}(x)-f_{m}(x)|<\varepsilon$$

>Funkcija je enakomerno konvergentna $\Leftrightarrow$ Funkcija je enakomerno Cauchyjeva
>>[!|dokaz]- Dokaz:
>> **Predpostavimo da imamo enakomerno konv. zap.** 
>> 
>> Izberemo poljuben $\varepsilon$. Izberemo $N$ da velja $n>N : |f_{n}-f|<\frac{\varepsilon}{2}$, nato si izberemo $f_{n}$ in $f_{m}$ in ker velja $|f_{n}-f|, |f_{m}-f|<\frac{\varepsilon}{2}$ velja da 
>>
>>$$ |f_{n}-f + f -f_{m}| \leq |f_{n}-f| + |f_{m}-f| \leq \varepsilon$$
>> $$|f_{n}-f_{m}| \leq \varepsilon$$
>> 
>> **Predpostavimo da imamo enakomerno Cauchyjevo zaporedje.**
>> 
>> Naprej dokažemo da obstaja limitna funkcija po točkah.
>> Če si izberemo fiksno točko dobimo Caucyjevo zaporedje ki vemo da konvergira. To velja za vse točke, torej točkovno konvergira za vse $x$, $f(x)$ pa je kandidat za limito.
>> 
>> Vzamemo $\varepsilon > 0$ in vemo da obstaja $N$ da velja $n,m > N:|f_{n}-f_{m}| <\frac{\varepsilon}{2}$.
>> 
>> Če fiksiramo $n$ in pustimo da gre $m$ v neskončnost lahko prepišemo neenakost v $|f_{n}- f| \leq \frac{\varepsilon}{2}$
>> Zgornjo konstrukcija velja za vse $n$ večje od $N$ kar pomeni da smo našli $N$ tako da za vsak $n > N$ velja da za vsak $x$ velja $|f_{n}(x)-f(x)|\leq \frac{\varepsilon}{2} < \varepsilon$

*Če so $f_n$ zvezne funkcije ni nujno da je limitna funkcija zvezna*

> Če zaporedje konvergira enakomerno in so vse $f_n$ zvezne je limitna funkcija zvezna
> >[!|dokaz]- Dokaz:
> > Predpostavimo, da zaporedje funkcij $f_n: D \to \mathbb{R}$ konvergira enakomerno proti funkciji $f: D \to \mathbb{R}$ in da so vse funkcije $f_n$ zvezne na $D$. Želimo pokazati, da je $f$ zvezna na $D$.
> > 
> > Vzemimo poljubno točko $x_0 \in D$ in poljuben $\epsilon > 0$. Pokazati moramo, da obstaja $\delta > 0$ takšen, da za vse $x \in D$ z $|x - x_0| < \delta$ velja $|f(x) - f(x_0)| < \epsilon$.
> > 
> > Zaradi enakomerne konvergence zaporedja $f_n$ proti $f$, za $\epsilon/3 > 0$ obstaja naravno število $N$ takšno, da velja $|f_N(y) - f(y)| < \epsilon/3$ za vse $y \in D$. To pomeni, da je $|f_N(x) - f(x)| < \epsilon/3$ in $|f_N(x_0) - f(x_0)| < \epsilon/3$.
> > 
> > Ker je funkcija $f_N$ zvezna v točki $x_0$, za $\epsilon/3 > 0$ obstaja $\delta > 0$ takšen, da za vse $x \in D$ z $|x - x_0| < \delta$ velja $|f_N(x) - f_N(x_0)| < \epsilon/3$.
> > 
> > Sedaj združimo te neenakosti. Za poljuben $x \in D$ z $|x - x_0| < \delta$ imamo:
> > $|f(x) - f(x_0)| = |f(x) - f_N(x) + f_N(x) - f_N(x_0) + f_N(x_0) - f(x_0)|$
> > S pomočjo trikotniške neenakosti dobimo:
> > $$|f(x) - f(x_0)| \le |f(x) - f_N(x)| + |f_N(x) - f_N(x_0)| + |f_N(x_0) - f(x_0)|$$
> > Po zgornjih sklepih so vsi trije členi manjši od $\epsilon/3$:
> > $$|f(x) - f(x_0)| < \epsilon/3 + \epsilon/3 + \epsilon/3 = \epsilon$$
> > Torej, za dani $\epsilon > 0$ smo našli $\delta > 0$ takšen, da za vse $x \in D$ z $|x - x_0| < \delta$ velja $|f(x) - f(x_0)| < \epsilon$. To dokazuje, da je $f$ zvezna v $x_0$. Ker je bila izbira $x_0$ poljubna, je $f$ zvezna na celotni domeni $D$.

**Funkcijska vrsta** je neskončna vsota funkcijskega zaporedja. Funckijska vrsta $\sum_{n=1}^{\infty}f_{n}$ konvergira po točkah če zaporedje delnih vsot $s_{n}(x) = f_{1}(x)+...+f_{n}(x)$ konvergira po točkah.

>Funkcijska vrsta konvergira enakomerno če zaporedje delnih vsot konvergira enakomerno.

> Če vrsta funkcij $\sum f_n$, kjer je **vsaka funkcija $f_{n}$ zvezna**, enakomerno konvergira k vsoti $S(x)$, potem je tudi limitna funkcija (vsota) $S(x)$ zvezna. *Implicirano je da je vsaka $S_{n}$ zvezna ker je vsota zveznih funkcij, torej je le prepis prejšnjega izreka.*

> Funkcijska vrsta enakomerno konvergira $\Leftrightarrow$ je enakomerno Cauchyjeva oz. velja da $\forall \varepsilon, \exists N \ni: \forall n,m > N \;\forall x : |\sum_{k=m}^{n}f_{k}| < \varepsilon$

**Weierstrassov M-kriterij za enakomerno konvergenco funkcijsih vrst** pravi da če obstaja zaporedje $a_{n}$ tako da velja $\left| f_{n} \right| \leq a_{n}, \forall x$ in je $\sum_{1}^{\infty} a_{n}$ konvergentna potem je funkcijska vrsta $\sum_{1}^{\infty}f_{n}$ absolutno in enakomerno konvergentna. Če so $f_n$ zvezne funkcije potem je tudi $f$ zvezna funckija.

>[!|dokaz]- Dokaz:
>Ker je funckijska vrsta majonizirana z $a_{n}$ gotovo konvergira po točkah. Ker je $\sum_{1}^{\infty}a_{n}$ konvergentna velja da za vsak $\varepsilon$ obstaja $N$ tako da za vse $m>n\geq N$ velja $\sum_{n+1}^{m}a_{k} < \varepsilon$, tako pa za vsak $x$ velja ocena $\sum_{n+1}^{m}\left|f_{n} \right| \leq \sum_{n+1}^{m}a_{n} < \varepsilon$ kar pomeni da zadošča Cauchyjevemu pogoju $\Rightarrow$ je enakomerno konvergentna.

Naj bo $f_n: [a, b] \to \mathbb{R}$ **zaporedje (Riemannovo) integrabilnih funkcij** na intervalu, ki **enakomerno konvergira** k funkciji $f: [a, b] \to \mathbb{R}$. Potem je tudi $f$ integrabilna na $[a, b]$ in velja:
$$
\lim_{n \to \infty} \int_{a}^{b} f_n(x) dx = \int_{a}^{b} \left( \lim_{n \to \infty} f_n(x) \right) dx = \int_{a}^{b} f(x) dx
$$

>[!|dokaz]- Dokaz enakosti (ne integrabilnosti):
>
Ker zaporedje $f_n$ enakomerno konvergira proti $f$, za poljuben $\varepsilon > 0$ obstaja tak $n_0 \in \mathbb{N}$, da za vse $n \ge n_0$ in za vse $x \in [a, b]$ velja:
$$|f_n(x) - f(x)| < \frac{\varepsilon}{b-a}$$
Ocenimo absolutno vrednost razlike integralov:
$$\left| \int_{a}^{b} f(x) dx - \int_{a}^{b} f_n(x) dx \right| = \left| \int_{a}^{b} (f(x) - f_n(x)) dx \right|$$
Z uporabo trikotniške neenakosti za integrale dobimo:
$$\le \int_{a}^{b} |f(x) - f_n(x)| dx < \int_{a}^{b} \frac{\varepsilon}{b-a} dx = \frac{\varepsilon}{b-a} \cdot (b-a) = \varepsilon$$
To velja za vse $n \ge n_0$, kar po definiciji pomeni, da limita integralov konvergira k integralu limite. 



Kot posledica sledi naslednji izrek

Naj bo $f_n: [a, b] \to \mathbb{R}$ funkcijsko zaporedje **zveznih funkcij** , za katerega vrsta $\sum_{n=1}^{\infty} f_n(x)$ **enakomerno konvergira** na intervalu $[a, b]$. Potem za vsak $x \in [a, b]$ velja:
$$
\int_{a}^{x} \left( \sum_{n=1}^{\infty} f_n(t) \right) dt = \sum_{n=1}^{\infty} \int_{a}^{x} f_n(t) dt
$$
Z drugimi besedami, vrsto smemo členoma integrirati.



Naj bo $f_n$ zaporedje **zvezno odvedljivih** funkcij na intervalu $[a, b]$. Predpostavimo:
1.  Zaporedje odvodov $f_n'$ enakomerno konvergira k neki funkciji $g: [a, b] \to \mathbb{R}$.
2. Obstaja vsaj ena točka $c \in [a, b]$, v kateri številsko zaporedje $f_n(c)$ konvergira.

Potem zaporedje $f_n$ enakomerno konvergira k neki funkciji $f$ na $[a, b]$, ki je prav tako odvedljiva, in za njen odvod velja:

$$f'(x) = g(x) = \lim_{n \to \infty} f_n'(x)$$

>[!|dokaz]- Dokaz:
>
Ker so funkcije $f_n$ zvezno odvedljive, po osnovnem izreku integralskega računa za poljuben $x \in [a, b]$ in dani $c \in [a, b]$ velja:
$$f_n(x) = f_n(c) + \int_{c}^{x} f_n'(t) dt$$
Po predpostavkah izreka vemo dvoje:
>*   Številsko zaporedje $\{f_n(c)\}$ konvergira. Označimo njegovo limito z $L = \lim_{n \to \infty} f_n(c)$.
>*   Zaporedje funkcij $\{f_n'\}$ enakomerno konvergira proti funkciji $g$. Ker je enakomerna konvergenca močnejša od konvergence po točkah, iz izreka o zamenjavi limite in integrala sledi, da za vsak $x \in [a, b]$ velja:
>
$$ \lim_{n \to \infty} \int_{c}^{x} f_n'(t) dt = \int_{c}^{x} \lim_{n \to \infty} f_n'(t) dt = \int_{c}^{x} g(t) dt $$
Ker oba člena na desni strani enačbe konvergirata, konvergira tudi zaporedje $\{f_n(x)\}$ za vsak $x$. Limito definiramo kot funkcijo $f(x)$:
$$f(x) := \lim_{n \to \infty} f_n(x) = L + \int_{c}^{x} g(t) dt$$
Ocenimo absolutno vrednost razlike $|f(x) - f_n(x)|$:
>$$ \begin{aligned} |f(x) - f_n(x)| &= \left| \left( L + \int_{c}^{x} g(t) dt \right) - \left( f_n(c) + \int_{c}^{x} f_n'(t) dt \right) \right| \\
&= \left| (L - f_n(c)) + \int_{c}^{x} (g(t) - f_n'(t)) dt \right| \\
&\le |L - f_n(c)| + \left| \int_{c}^{x} (g(t) - f_n'(t)) dt \right| \end{aligned}$$
Za poljuben $\varepsilon > 0$ lahko zaradi konvergence zaporedij $\{f_n(c)\}$ in $\{f_n'\}$ oba člena naredimo poljubno majhna:
>- Ker $f_n(c) \to L$, obstaja $n_1 \in \mathbb{N}$, da za vse $n \ge n_1$ velja $|L - f_n(c)| < \frac{\varepsilon}{2}$.
>- Ker $f_n' \to g$ enakomerno, obstaja $n_2 \in \mathbb{N}$, da za vse $n \ge n_2$ in za vse $t \in [a, b]$ velja $|g(t) - f_n'(t)| < \frac{\varepsilon}{2(b-a)}$. Zato je:
>$$\left| \int_{c}^{x} (g(t) - f_n'(t)) dt \right| \le \int_{a}^{b} |g(t) - f_n'(t)| dt < \int_{a}^{b} \frac{\varepsilon}{2(b-a)} dt = \frac{\varepsilon}{2(b-a)} (b-a) = \frac{\varepsilon}{2}$$
>
>Če izberemo $n_0 = \max(n_1, n_2)$, potem za vse $n \ge n_0$ in za vse $x \in [a, b]$ velja:
>$$|f(x) - f_n(x)| < \frac{\varepsilon}{2} + \frac{\varepsilon}{2} = \varepsilon$$
>Ker $n_0$ ni odvisen od $x$, je konvergenca $f_n \to f$ enakomerna.
>
>Funkcija $g$ je zvezna, saj je enakomerna limita zaporedja zveznih funkcij $\{f_n'\}$. Iz definicije funkcije $f$:
>$$f(x) = L + \int_{c}^{x} g(t) dt$$
>po osnovnem izreku integralskega računa sledi, da je $f$ odvedljiva in za njen odvod velja:
>$$f'(x) = \frac{d}{dx} \left( L + \int_{c}^{x} g(t) dt \right) = g(x)$$


---



Naj bo $f_{n}$ zaporedje zvezno odvedljivih funkcij na intervalu $[a, b]$ 
Predpostavimo:
1.  Vrsta odvodov $\sum_{n=1}^{\infty} f_n'(x)$ enakomerno konvergira na $[a, b]$.
2.  Obstaja točka $c \in [a, b]$, v kateri številska vrsta $\sum_{n=1}^{\infty} f_n(c)$ konvergira.

Potem tudi vrsta $\sum_{n=1}^{\infty} f_n(x)$ enakomerno konvergira na $[a, b]$ k odvedljivi funkciji $S(x)$, za katero velja:
$$
S'(x) = \left( \sum_{n=1}^{\infty} f_n(x) \right)' = \sum_{n=1}^{\infty} f_n'(x)
$$
To pomeni, da smemo vrsto odvajati po členih.
***
**Potenčna vrsta** je funkcijska vrsta oblike

$$\sum_{0}^{\infty}a_{n}(x-c)^{n}$$

kjer je $a_{n}$ številsko zaporedje $c$ pa realno število. $c$ predstavlja središče vrste, če je $c=0$ je to Maclaurinova vrsta. Glavni cilj teh je da ugotovimo za katere $x$ vrsta konvergira.

Velja da ob dani potenčni vrsti obstaja $R \in [0,\infty]$ da velja:
1. $\forall x:|x-c| < R$ je vrsta konvergentna in abs. konvergentna
2. $\forall x: |x-c| > R$ je vrsta divergentna
3. Če je $0 < r < R$ potem je vrsta enakomerno konvergentna na $[c-r, c+r]$.

>[!|dokaz]- Dokaz:
> Definirajmo množico $S = \{ |x| \in [0, \infty) \mid \text{vrsta } \sum_{n=0}^\infty a_n x^n \text{ konvergira} \}$.
> Če je $S$ prazna (razen $0$, saj vsaka potenčna vrsta konvergira za $x=c$), potem določimo $R=0$. To pomeni, da vrsta konvergira le v središču $c$.
> Če je $S$ neomejena, določimo $R=\infty$. To pomeni, da vrsta konvergira za vsa realna (ali kompleksna) števila $x$.
> V nasprotnem primeru, ko $S$ ni prazna in je omejena, definiramo $R = \sup S$. Pokažimo, da ta $R$ ustreza željenim lastnostim.
> 
> **1. Konvergenca za $|x| < R$:**
> Naj bo $|x_0| \in S$, kar pomeni, da vrsta $\sum_{n=0}^\infty a_n x_0^n$ konvergira. Ker konvergira, velja $\lim_{n \rightarrow \infty} a_n x_0^n = 0$. Iz tega sledi, da je zaporedje $|a_n x_0^n|$ omejeno, torej obstaja konstanta $M > 0$, da je $|a_n x_0^n| \le M$ za vse $n \ge 0$.
> Sedaj vzemimo poljuben $x$ takšen, da je $|x| < |x_0|$. Oblikujmo kvocient $q = \frac{|x|}{|x_0|}$. Ker je $|x| < |x_0|$, velja $0 \le q < 1$.
> Poglejmo absolutno vrednost členov vrste za $x$:
> $|a_n x^n| = |a_n x_0^n \left(\frac{x}{x_0}\right)^n| = |a_n x_0^n| \left|\frac{x}{x_0}\right|^n \le M q^n$.
> Ker je $q < 1$, geometrijska vrsta $\sum_{n=0}^\infty M q^n$ konvergira. Po primerjalnem kriteriju (za absolutno konvergenco) sledi, da vrsta $\sum_{n=0}^\infty |a_n x^n|$ konvergira. To pomeni, da vrsta $\sum_{n=0}^\infty a_n x^n$ absolutno konvergira za vse $x$ z $|x| < |x_0|$.
> Ta ugotovitev implicira, da če je $x_0$ v $S$, potem je celoten interval $[0, |x_0|)$ vsebovan v $S$. Posledično, če $R = \sup S$, potem za vsak $|x| < R$ vrsta konvergira (in sicer absolutno).
> 
> **2. Divergenca za $|x| > R$:**
> Predpostavimo, da vrsta divergira za nek $x_0$. Sedaj vzemimo poljuben $x$ takšen, da je $|x| > |x_0|$. Če bi vrsta konvergirala za ta $x$, bi po prvem delu dokaza (konvergenca za $|x| < R$) morala konvergirati tudi za $x_0$, saj $|x_0| < |x|$. To pa je v nasprotju z našo predpostavko, da vrsta divergira za $x_0$. Zato mora vrsta divergirati tudi za ta $x$.
> Ta ugotovitev implicira, da če $x_0$ ni v $S$, potem nobena točka $x$ z $|x| > |x_0|$ ne more biti v $S$. Posledično, za vsak $|x| > R$ vrsta divergira.
> 
> **3. Enakomerna konvergenca na kompaktnih podmnožicah:**
> Naj bo $0 < r < R$. Izberimo poljuben $x_r$ takšen, da je $r < |x_r| < R$. (Takšen $x_r$ obstaja, saj je $R=\sup S$ in $r<R$). Ker je $|x_r| < R$, po prvem delu dokaza vrsta $\sum_{n=0}^\infty a_n x_r^n$ absolutno konvergira. To pomeni, da so členi $a_n x_r^n$ omejeni, torej obstaja $M_r > 0$, da je $|a_n x_r^n| \le M_r$ za vse $n \ge 0$.
> Sedaj opazujmo vrsto na intervalu $[-r, r]$. Za vsak $x \in [-r, r]$ velja $|x| \le r$.
> Imamo: $|a_n x^n| = |a_n x_r^n \left(\frac{x}{x_r}\right)^n| = |a_n x_r^n| \left|\frac{x}{x_r}\right|^n \le M_r \left(\frac{r}{|x_r|}\right)^n$.
> Označimo $q' = \frac{r}{|x_r|}$. Ker je $r < |x_r|$, velja $0 \le q' < 1$.
> Torej, $|a_n x^n| \le M_r (q')^n$. Ker vrsta $\sum_{n=0}^\infty M_r (q')^n$ konvergira (geometrijska vrsta z $q'<1$), po Weierstrassovem M-testu vrsta $\sum_{n=0}^\infty a_n x^n$ enakomerno konvergira na intervalu $[-r, r]$.

$R$ pa imenujemo konvergenčni polmer.

**Na robovih intervala je treba konvergenco preveriti posebej.**

> Posledica je da je vsota potenčne vrste s polmerom $R>0$ zvezna funkcija na $(c-R,c+R)$.

Za konvergenčni radij potenčne vrste velja:

$$ $$
$$\frac{1}{R} = \lim_{n \to \infty}\frac{|a_{n+1}|}{|a_{n}|}$$
$$ $$
$$\frac{1}{R} =  \lim_{n \to \infty} \sqrt[n]{|a_{n}|}$$

Če je limita enaka $0$ potem je $R = \infty$, če je limita $\infty$ potem je $R = 0$ oz. vrsta konvergira samo v središču $x = c$.

Formuli delujeta le če limita obstaja, drugače uporabimo splošnejšo različico z limito superior.

>[!|dokaz]- Dokaz:
> Konvergenčni radij $R$ potenčne vrste $\sum_{n=0}^\infty a_n x^n$ določimo z uporabo kriterijev za absolutno konvergenco. Vrsta konvergira absolutno, če je $\sum_{n=0}^\infty |a_n x^n|$ konvergentna.
> 
> Z uporabo kvocientnega kriterija za konvergenco, vrsta konvergira, če je limita absolutne vrednosti kvocientov zaporednih členov manjša od 1:
> $$ \lim_{n \to \infty} \left| \frac{a_{n+1} x^{n+1}}{a_n x^n} \right| < 1 $$
> Kar se poenostavi v
> $$ \lim_{n \to \infty} \left| \frac{a_{n+1}}{a_n} \right| |x| < 1 $$
> Če obstaja limita $L = \lim_{n \to \infty} \left| \frac{a_{n+1}}{a_n} \right|$, potem vrsta konvergira za $L|x| < 1$, kar pomeni $|x| < \frac{1}{L}$. Po definiciji konvergenčnega radija $R$, je $R$ največja vrednost $|x|$, za katero vrsta konvergira. Zato je $R = \frac{1}{L}$, kar nam da prvo formulo:
> $$ \frac{1}{R} = \lim_{n \to \infty} \frac{|a_{n+1}|}{|a_n|} $$
> 
> Podobno, z uporabo korenskega kriterija za konvergenco, vrsta konvergira, če je limita $n$-tih korenov absolutnih vrednosti členov manjša od 1:
> $$ \lim_{n \to \infty} \sqrt[n]{|a_n x^n|} < 1 $$
> Kar se poenostavi v
> $$ \lim_{n \to \infty} \sqrt[n]{|a_n|} \sqrt[n]{|x^n|} < 1 $$
> in naprej v
> $$ \lim_{n \to \infty} \sqrt[n]{|a_n|} |x| < 1 $$
> Če obstaja limita $L' = \lim_{n \to \infty} \sqrt[n]{|a_n|}$, potem vrsta konvergira za $L'|x| < 1$, kar pomeni $|x| < \frac{1}{L'}$. Po definiciji konvergenčnega radija $R$, je $R = \frac{1}{L'}$, kar nam da drugo formulo:
> $$ \frac{1}{R} = \lim_{n \to \infty} \sqrt[n]{|a_n|} $$
> V obeh primerih velja: če je limita enaka 0, je $R=\infty$ (vrsta konvergira za vsa realna/kompleksna števila); če je limita enaka $\infty$, je $R=0$ (vrsta konvergira samo v središču $x=0$).

**Cauchy-Hadamardov izrek** pravi da za k. polmer $R$ potenčnih vrst velja

$$\frac{1}{R} = \limsup_{n \rightarrow \infty} \sqrt[n]{|a_{n}|}$$

Za razliko od limite od prej bo limes superior vedno obstajala zaradi česar je to univerzalen izrek. Če je lim sup enak 0 je $R = \infty$ če je lim sup enak $\infty$ potem je $R = 0$.

>[!|dokaz]- Dokaz:
>
> Obravnavajmo korenski kriterij za absolutno konvergenco vrste $\sum_{n=0}^\infty a_n x^n$. Limita superior n-tega korena absolutnih členov je $\limsup_{n \rightarrow \infty} \sqrt[n]{|a_n x^n|} = \limsup_{n \rightarrow \infty} \sqrt[n]{|a_n|} |x| = L|x|$. Po korenskem kriteriju vrsta konvergira absolutno, če je $L|x| < 1$, in divergira, če je $L|x| > 1$.
> 
> Če je $L|x| < 1$, to je $|x| < 1/L$, vrsta $\sum_{n=0}^\infty |a_n x^n|$ konvergira, kar pomeni, da prvotna vrsta $\sum_{n=0}^\infty a_n x^n$ konvergira absolutno. Torej je $R \ge 1/L$.
> 
> Sedaj predpostavimo, da je $L|x| > 1$, to je $|x| > 1/L$. Ker je $L = \limsup_{n \rightarrow \infty} \sqrt[n]{|a_{n}|}$, po definiciji limite superior obstaja neskončno mnogo indeksov $k$ takih, da je $\sqrt[k]{|a_k|} > 1/|x|$. To pomeni, da za te indekse $k$ velja $\sqrt[k]{|a_k|} |x| > 1$, oziroma $|a_k x^k| > 1^k = 1$. Ker neskončno mnogo členov vrste $a_n x^n$ po absolutni vrednosti presega 1, členi $a_n x^n$ ne konvergirajo proti nič. To pa je nujen pogoj za konvergenco vrste, zato v tem primeru vrsta $\sum_{n=0}^\infty a_n x^n$ divergira. Torej je $R \le 1/L$.
> 
> Iz obeh delov dokaza, $R \ge 1/L$ in $R \le 1/L$, sledi, da je $R = 1/L$, oziroma $\frac{1}{R} = \limsup_{n \rightarrow \infty} \sqrt[n]{|a_{n}|}$.
> 


**Abelov izrek** pravi da če je vrsta konvergentna pri $x = R$ ali $x = -R$ potem je njena vsota zvezna na intervalu ki vsebuje to robno točko.

**Odvajanje in integriranje potenčnih vrst**
Naj bo $R > 0$ in potenčna vrsta BŠS $\sum_{0}^{\infty}a_{n}x^{n}$.
Velja da ima vrsta ki jo dobimo s **členskim odvajanjem** $\sum_{}^{}na_{n}x^{n-1}$ in **členskim integriranjem** $\sum_{}^{}\frac{a_{n}}{n+1}x^{n+1}$ tudi konvergenčni polmer $R$.

>[!|dokaz]- Dokaz:
> Dokazati moramo, da imata tudi člensko odvajana in člensko integrirana vrsta enak konvergenčni polmer $R$.
> 
> **1. Člensko odvajanje:**
> 
> Vrsta, ki jo dobimo s členskim odvajanjem, je $\sum_{n=1}^\infty n a_n x^{n-1}$.
> Da lahko uporabimo Cauchy-Hadamardov izrek, moramo identificirati koeficiente te nove vrste. Naj bo $k = n-1$, torej $n = k+1$. Potem je vrsta zapisana kot $\sum_{k=0}^\infty (k+1) a_{k+1} x^k$.
> Koeficienti te vrste so $b_k = (k+1)a_{k+1}$.
> Konvergenčni polmer $R'$ te vrste je določen z:
> $\frac{1}{R'} = \limsup_{k \rightarrow \infty} \sqrt[k]{|b_k|} = \limsup_{k \rightarrow \infty} \sqrt[k]{|(k+1)a_{k+1}|}$
> $\frac{1}{R'} = \limsup_{k \rightarrow \infty} \left( \sqrt[k]{k+1} \cdot \sqrt[k]{|a_{k+1}|} \right)$
> 
> Znano je, da $\lim_{k \rightarrow \infty} \sqrt[k]{k+1} = 1$.
> Prav tako velja, da premik indeksa ne spremeni limite superior: $\limsup_{k \rightarrow \infty} \sqrt[k]{|a_{k+1}|} = \limsup_{j \rightarrow \infty} \sqrt[j]{|a_j|} = L$.
> Splošno pravilo za limite superior pravi, da če je $\lim_{n \rightarrow \infty} x_n = x > 0$ in $\limsup_{n \rightarrow \infty} y_n = Y$, potem je $\limsup_{n \rightarrow \infty} (x_n y_n) = xY$.
> Uporabimo to pravilo:
> $\frac{1}{R'} = \left( \lim_{k \rightarrow \infty} \sqrt[k]{k+1} \right) \cdot \left( \limsup_{k \rightarrow \infty} \sqrt[k]{|a_{k+1}|} \right) = 1 \cdot L = L$.
> Ker je $\frac{1}{R'} = L = \frac{1}{R}$, sledi, da je $R' = R$.
> 
> **2. Člensko integriranje:**
> 
> Vrsta, ki jo dobimo s členskim integriranjem, je $\sum_{n=0}^\infty \frac{a_n}{n+1} x^{n+1}$.
> Koeficienti te nove vrste (če jo prepišemo kot $\sum_{k=1}^\infty c_k x^k$) so $c_k = \frac{a_{k-1}}{k}$ (za $k \ge 1$, in $c_0=0$).
> Konvergenčni polmer $R''$ te vrste je določen z:
> $\frac{1}{R''} = \limsup_{k \rightarrow \infty} \sqrt[k]{|c_k|} = \limsup_{k \rightarrow \infty} \sqrt[k]{\left|\frac{a_{k-1}}{k}\right|}$
> $\frac{1}{R''} = \limsup_{k \rightarrow \infty} \frac{\sqrt[k]{|a_{k-1}|}}{\sqrt[k]{k}}$
> 
> Znano je, da $\lim_{k \rightarrow \infty} \sqrt[k]{k} = 1$.
> Prav tako velja, da premik indeksa ne spremeni limite superior: $\limsup_{k \rightarrow \infty} \sqrt[k]{|a_{k-1}|} = \limsup_{j \rightarrow \infty} \sqrt[j]{|a_j|} = L$.
> Splošno pravilo za limite superior pravi, da če je $\lim_{n \rightarrow \infty} x_n = x > 0$ in $\limsup_{n \rightarrow \infty} y_n = Y$, potem je $\limsup_{n \rightarrow \infty} \frac{y_n}{x_n} = \frac{Y}{x}$.
> Uporabimo to pravilo:
> $\frac{1}{R''} = \frac{\limsup_{k \rightarrow \infty} \sqrt[k]{|a_{k-1}|}}{\lim_{k \rightarrow \infty} \sqrt[k]{k}} = \frac{L}{1} = L$.
> Ker je $\frac{1}{R''} = L = \frac{1}{R}$, sledi, da je $R'' = R$.

Hkrati velja da je vsota neskončnokrat odvedljiva na $(-R, R)$ kot posledica prejšnjih lastnosti.


**Taylorjeva vrsta**

Velja da lahko vsako funkcijo aproksimiramo s taylorjevim polinomom.

[[Analiza#Taylorjev polinom in taylorjeva vrsta|Glej taylorjevi polinomi]]

>Če $f(x)$ lahko predstavimo s konvergentno potenčno vrsto $f(x) = \sum_{k=0}^\infty c_k (x-a)^k$ na nekem odprtem intervalu, potem so njeni koeficienti $c_k$ edinstveno določeni z odvodi funkcije $f$ v točki $a$ in je v tej okolici neskončnokrat odvedljiva. 
>
Konkretno velja, da je $c_k = \frac{f^{(k)}(a)}{k!}$ za vsak $k \ge 0$. 
>
Iz tega sledi, da je vsaka konvergentna potenčna vrsta za dano funkcijo okoli določene točke v resnici **Taylorjeva vrsta** te funkcije, centrirana v tej točki.

>Če je $f(x)$ v odprti okolici točke $a$ lahko predstavljena s konvergenčno vrsto ki konvergira k $f$ potem je **analitična** v točki $a$.



**Preureditev potenčne vrste okoli novega centra:**
Če je funkcija $f(x)$ definirana s potenčno vrsto $f(x) = \sum_{k=0}^\infty c_k x^k$, ki konvergira na odprtem intervalu $(-R, R)$, potem je za vsako točko $a$ znotraj tega intervala mogoče funkcijo $f$ predstaviti kot novo potenčno vrsto, centrirano v točki $a$. Ta nova vrsta je enaka vsoti svoje Taylorjeve vrste v točki $a$:
$$f(x) = \sum_{k=0}^\infty \frac{f^{(k)}(a)}{k!} (x-a)^k$$
Konvergenčni polmer te nove Taylorjeve vrste je $R' = R - |a|$. To pomeni, da vrsta konvergira za vse $x$, ki zadoščajo pogoju $|x-a| < R - |a|$. Geometrijsko gledano, konvergenčni interval nove vrste se razteza od centra $a$ do najbližje meje prvotnega intervala konvergence.

`----R----------0----|a|-----R--`



>[!|dokaz]- Dokaz:
> Naj bo funkcija $f$ podana s potenčno vrsto $f(x) = \sum_{k=0}^\infty c_k x^k$, ki konvergira za $|x|<R$. Želimo jo izraziti kot Taylorjevo vrsto, centrirano v točki $a \in (-R, R)$.
> 
> Zapišemo $x = (x-a) + a$. S tem lahko izvorni izraz za $f(x)$ preoblikujemo:
> $$f(x) = \sum_{k=0}^\infty c_k ((x-a) + a)^k$$
> Z uporabo binomskega izreka $((x-a) + a)^k = \sum_{j=0}^k \binom{k}{j} a^{k-j} (x-a)^j$ dobimo:
> $$f(x) = \sum_{k=0}^\infty c_k \left( \sum_{j=0}^k \binom{k}{j} a^{k-j} (x-a)^j \right)$$
> To je dvojna vsota, ki jo lahko zapišemo kot $\sum_{k=0}^\infty \sum_{j=0}^k A_{k,j}$, kjer je $A_{k,j} = c_k \binom{k}{j} a^{k-j} (x-a)^j$.
> 
> Da lahko zamenjamo vrstni red sumacije in izrazimo $f(x)$ kot potenčno vrsto v $(x-a)$, mora biti dvojna vrsta absolutno konvergentna. To je ključen korak pri delu z neskončnimi vsotami.
> 
> **Razumevanje območja sumacije:**
> Poglejmo območje sumacije indeksov $(k,j)$ v izrazu $\sum_{k=0}^\infty \left( \sum_{j=0}^k A_{k,j} \right)$:
> *   Zunanji indeks $k$ gre od $0$ do $\infty$.
> *   Notranji indeks $j$ gre od $0$ do $k$.
> To pomeni, da sumiramo po točkah $(k,j)$ v ravnini, ki tvorijo nekakšen "trikotnik", kjer $j \le k$:
> 
> $k=0: \quad (0,0)$
> $k=1: \quad (1,0), (1,1)$
> $k=2: \quad (2,0), (2,1), (2,2)$
> $k=3: \quad (3,0), (3,1), (3,2), (3,3)$
> ... in tako naprej v neskončnost.
> 
> Ko želimo zamenjati vrstni red sumacije, to pomeni, da želimo najprej sumirati po $k$ za fiksni $j$, nato pa po $j$. Spremenimo "vrstice" v "stolpce":
> *   Če fiksiramo $j$, od kod do kod gre $k$? Iz prvotnega pogoja $j \le k$ sledi, da mora $k$ teči od $j$ do $\infty$.
> *   Potem pa $j$ sam teče od $0$ do $\infty$.
> 
> Tako se vsota preoblikuje v:
> $$ \sum_{j=0}^\infty \left( \sum_{k=j}^\infty A_{k,j} \right) $$
> Pri tem se resnično spremenijo meje sumacije posameznih indeksov, vendar *območje* sumacije (tj. nabor vseh parov $(k,j)$ po katerih sumiramo) ostaja isto. Sumiramo po istih členih $A_{k,j}$, le v drugem vrstnem redu.
> 
> **Preverjanje absolutne konvergence:**
> Ključni pogoj, ki omogoča to zamenjavo vrstnega reda sumacije pri **neskončnih** vrstah, je **absolutna konvergenca** dvojne vsote. Če vrsta $\sum_{k=0}^\infty \sum_{j=0}^k A_{k,j}$ absolutno konvergira (torej, če konvergira vsota $\sum_{k=0}^\infty \sum_{j=0}^k |A_{k,j}|$), potem lahko vrstni red sumacije poljubno zamenjamo, ne da bi se spremenila vrednost vsote.
> 
> Preučimo vsoto absolutnih vrednosti:
> $$\sum_{k=0}^\infty \left| c_k \sum_{j=0}^k \binom{k}{j} a^{k-j} (x-a)^j \right|$$
> Ker so $\binom{k}{j}$ pozitivni koeficienti, in uporabimo lastnost, da je absolutna vrednost vsote manjša ali enaka vsoti absolutnih vrednosti:
> $$= \sum_{k=0}^\infty |c_k| \sum_{j=0}^k \binom{k}{j} |a|^{k-j} |x-a|^j$$
> Prepoznamo, da je notranja vsota natanko binomski razvoj $(|a| + |x-a|)^k$:
> $$= \sum_{k=0}^\infty |c_k| (|a| + |x-a|)^k$$
> Ta zadnja vsota je potenčna vrsta v $(|a| + |x-a|)$. Ker prvotna vrsta $f(x) = \sum_{k=0}^\infty c_k x^k$ konvergira za $|x|<R$, vemo, da konvergira tudi vrsta $\sum_{k=0}^\infty |c_k| x^k$ za $|x|<R$. Zato bo naša absolutna vsota konvergirala, če je $(|a| + |x-a|) < R$.
> Iz tega sledi, da mora biti $|x-a| < R - |a|$. Ko je ta pogoj izpolnjen, je dvojna vrsta absolutno konvergentna, kar pomeni, da lahko vrstni red sumacije zamenjamo.
> 
> **3. Zamenjava vrstnega reda in določitev koeficientov:**
> Ko je pogoj konvergence $(|a| + |x-a|) < R$ izpolnjen, lahko zamenjamo vrstni red sumacije:
> $$f(x) = \sum_{j=0}^\infty \left( \sum_{k=j}^\infty c_k \binom{k}{j} a^{k-j} \right) (x-a)^j$$
> To je potenčna vrsta v $(x-a)$. Označimo koeficiente te vrste z $C_j$:
> $$C_j = \sum_{k=j}^\infty c_k \binom{k}{j} a^{k-j}$$
> 
> **4. Primerjava s Taylorjevimi koeficienti:**
> Zdaj moramo pokazati, da so ti koeficienti res Taylorjevi koeficienti $f^{(j)}(a)/j!$. Potenčne vrste lahko členoma odvajamo znotraj konvergenčnega intervala.
> $$f(x) = \sum_{k=0}^\infty c_k x^k$$
> $$f'(x) = \sum_{k=1}^\infty k c_k x^{k-1}$$
> $$f''(x) = \sum_{k=2}^\infty k(k-1) c_k x^{k-2}$$
> Splohno, za $j$-ti odvod velja:
> $$f^{(j)}(x) = \sum_{k=j}^\infty k(k-1)\cdots(k-j+1) c_k x^{k-j}$$
> To lahko zapišemo tudi z uporabo fakultet:
> $$f^{(j)}(x) = \sum_{k=j}^\infty \frac{k!}{(k-j)!} c_k x^{k-j}$$
> Če to ovrednotimo v točki $x=a$ in delimo z $j!$, dobimo Taylorjeve koeficiente:
> $$\frac{f^{(j)}(a)}{j!} = \frac{1}{j!} \sum_{k=j}^\infty \frac{k!}{(k-j)!} c_k a^{k-j}$$
> Preuredimo izraz: $\frac{k!}{j!(k-j)!}$ je natanko binomski koeficient $\binom{k}{j}$.
> Zato je:
> $$\frac{f^{(j)}(a)}{j!} = \sum_{k=j}^\infty \binom{k}{j} c_k a^{k-j}$$
> To je natanko izraz, ki smo ga dobili za koeficiente $C_j$ v predhodno izpeljani potenčni vrsti, centrirani v $a$.
> 
> **Zaključek:**
> S tem je dokazano, da je funkcija $f(x)$ znotraj konvergenčnega intervala $(-R,R)$ enaka svoji Taylorjevi vrsti, centrirani v točki $a$. Ta Taylorjeva vrsta konvergira za $|x-a| < R - |a|$. To pomeni, da lahko potenčno vrsto razvijemo okoli katerekoli točke znotraj njenega konvergenčnega polmera in da je konvergenčni polmer nove vrste vsaj $R-|a|$.

Funkcija $f: I \to \mathbb{R}$ je **realno analitična** na odprtem intervalu $I \subseteq \mathbb{R}$, če za vsako točko $a \in I$ obstaja odprta okolica vsebovana v $I$, in na njej funkcijo $f(x)$ lahko zapišemo kot vsoto konvergentne potenčne vrste, centrirane v $a$:

$$f(x) = \sum_{k=0}^\infty c_k (x-a)^k \quad \text{za vse } x \in (a-r_a, a+r_a)$$

Množico vseh realno analitičnih funkcij na intervalu $I$ označimo s $C^\infty(I)$


**Taylorjev izrek o ostanku**.


Če imamo $f$ rarzeda $C^{n+1}$ na odprtem intervalu $I$, ki vsebuje $a$.

Pravi da je ostanek enak

$$R_{n,a} = \frac{f^{(n+1)}(c)}{(n+1)!}(x-a)^{n+1}$$

Za vsak $x$ na intervalu $I$ obstaja $c$ tako da velja zgornja enačba, še več $c$ je med $a$ in $x$.

Za izpeljevanje funkcij v Taylorjeve vrste uporabljamo ali preverjanje konvergence ostanka ali pa preverjanje konvergence nastale potenčne vrste ali z kvoceientnim in korenskim kriterijem ali Cauchy Hadamardovim kriterijem.

**Znane funkcijske vrste**

$$e^{x} = \sum_{0}^{\infty}\frac{x^{n}}{n!}$$

*Okoli točke $a$, kjer velja da je $e^{a} = 1\,;\;a = 0$*

$$\cos\,\! (x) = \sum_{0}^{\infty}\frac{x^{2n}}{2n!}(-1)^{n}$$

*FOra je da ostanejo samo sodi in indeksiramo po teh ki dejansko ostanejo torej $n$ ne odraža vsakega odvoda ampak samo tiste ki niso $0$*

$$\sin\,\! (x) = \sum_{0}^{\infty}\frac{x^{2n+1}}{(2n+1)!}(-1)^{n+1}$$

*Isto je tukej kjer vzemamo indekse samo kjer odvod ni 0. Omenjeno naj bo da je $a=0$ torej je sinus od 0 enak 0.*

$$\frac{1}{1-x} = \sum_{0}^{\infty}x^{n}$$

*Enačba za neskončno geometrijsko vrsto*

$$\ln(1-x) = \sum_{0}^{\infty}\frac{x^{n+1}}{n+1}$$

*Če vzamemo enačbo za geo. vrsto in obe strani integriramo dobimo to enačbo.*

$$\ln(1+x) = \sum_{0}^{\infty}\frac{(-x)^{n+1}}{n+1} = \sum_{1}^{\infty}\frac{(-x)^{n}}{n} = $$ 
$$\sum_{1}^{\infty}(-1)^{n}\frac{x^{n}}{n}$$

*Posplošena oz. skrajšana oblika oz. popularna oblika*

$$(1+x)^{r} = \sum_{n=0}^{\infty}\binom{\,r\,}{\,n\,}x^n$$

*Sledi iz binomskega izreka*

$$\arctan(x) = $$