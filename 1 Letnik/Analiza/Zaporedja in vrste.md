# Zaporedja

Množica $U$ je okolica točke $u$ če velja da vsebuje kakšno odprto množico $I$ ki vsebuje točko $u$ 

Realno **zaporedje** je preslikava iz $\mathbb{N} \longrightarrow \mathbb{R}$. $(a_{n})_{n}$ kjer je $a_{n} = a(n)$. Lahko jih seštevamo, odštevamo, množimo in delimo.

Zapoerdje je **rekurzivno** s podanim prvim členom in formulo, s katero opisujemo naslednji element iz prejšnjega.

Zaporedje je **omejeno navzgor**, če je množica $a_{n}$ omejena navzgor oz. obstaja zgornja meja.

**Supremum** je zgornja meja za katero velja da katerakoli manjša vrednost ni več zgornja meja.

$$\sup A \quad\Leftrightarrow\quad \forall \varepsilon > 0 \;\exists a \in A \ni: a > \sup A - \varepsilon \quad\land\quad \forall a : \sup A \geq a$$

Če ni omejeno je **neomejeno**.

**Naraščajoče zaporedje** je $a_{n+1} > a_{n}$
**Nepadajoče** je $a_{n+1} \leq a_{n}$

Zaporedje je **monotono** če je nepadajoče ali nenaraščajoče oz. strogo monotono če je naraščajoče ali padajoče $\forall n$.


$L$ je **limita zaporedja** če za vsako njeno okolico velja da vsebuje vse elemente od nekega indeksa naprej.

$$ \forall \varepsilon \exists N \forall n\geq N : |a_{n}-L| < \varepsilon$$
$$\lim_{n \to \infty}a_{n}$$


Pravimo da ima zaporedje **limito v $\infty$** če vsak interval $(M, \infty)$ vsebuje vse člene od nekega indeksa naprej.

Če ima zaporedjo limito $|L| < \infty$ potem konvergira.

>Konvergentno zaporedje v $\mathbb{R}$ ima natanko eno limito.  
>*Elementi ne morejo skakati iz okolico v okolico ker drugače niso vsi elementi v okolici ene od limit*

>Vsako konvergentno zaporedje v $\mathbb{R}$ je omejeno.
>*Izberemo okolico in vidimo da so vsi elementi naprej znotraj okolice, ostane pa končno število, obe sta omejeni.*

> Za konvergentni zaporedji velja da je vsota njunih limit enaka limiti vsote zaporedij. Enako za razliko, produkt in koeficient.
>*Lahko si izberemo tak $\varepsilon$ da je $|(a_n +b_n) - (A+B)| \leq \frac{\varepsilon}{2} + \frac{\varepsilon}{2} = e$*
>*Za produkt lahko razčlenimo izraz $|a_{n}b_{n} - AB|$ in ker vemo da je zaporedje ki ima limito omejeno lahko najdemo taka epsilona za vsako zaporedje da velja da sta oba manjša od nekega epsilona*
>*Za deljenje mora veljati $L_{2}\neq 0$ in dokazati $\lim_{n \to \infty} \frac{1}{b_{n}} = \frac{1}{L_{2}}$ nato uporabimo pravilo produkta*
>*Najprej damo v isti ulomek. Potem lahko $a_{n}$ omejimo z dejstvom da konvergira in trikotniškim pravilom, nato pa izberemo delto tako da velja da je celoten ulomek manjši od $\varepsilon$.*

>Če je zaporedje montono ima limito enako $\sup a_{n}$ če pada pa $\inf a_{n}$
>*Vemo da obstaja $\sup$, vemo da za vsak $\varepsilon$ obstaja $a_N$ ki je v $\sup - \varepsilon$. Ker je monotono so vsi nadaljni $a_n$ tudi v $\sup - \varepsilon$.*


> Če je zaporedje monotono in omejeno, je konvergentno
> *$\sup - \varepsilon$ vsebuje vsaj en $a_n$, od kjer velja da vsebuje neskončno zaradi monotonosti.*


>[!|]- Primer: $x_{n+1} = \sqrt{a+x_n}$
>To prove the convergence of the sequence $x_{n+1} = \sqrt{a+x_n}$ with $x_0 = 0$ and $a > 0$:
> 
> **1. Monotonicity (Increasing):**
> *   **Base Case:** $x_0 = 0$, $x_1 = \sqrt{a+0} = \sqrt{a}$. Since $a > 0$, $x_1 > x_0$.
> *   **Inductive Step:** Assume $x_k > x_{k-1}$ for some $k \ge 1$.
>     Then $a+x_k > a+x_{k-1}$.
>     Taking the square root (all terms positive): $\sqrt{a+x_k} > \sqrt{a+x_{k-1}}$.
>     By definition, this means $x_{k+1} > x_k$.
> *   Therefore, the sequence $(x_n)$ is strictly increasing.
> 
> **2. Boundedness (Bounded Above):**
> If the sequence converges to a limit $L$, then $L$ must satisfy $L = \sqrt{a+L}$, which implies $L^2 - L - a = 0$. Since $x_n \ge 0$ for all $n$, the limit must be non-negative. The positive solution is $L = \frac{1 + \sqrt{1+4a}}{2}$.
> *   **Base Case:** $x_0 = 0$. Since $a > 0$, $L = \frac{1 + \sqrt{1+4a}}{2} > 1$, so $x_0 < L$.
> *   **Inductive Step:** Assume $x_k < L$ for some $k \ge 0$.
>     Then $a+x_k < a+L$.
>     Taking the square root: $\sqrt{a+x_k} < \sqrt{a+L}$.
>     Since $L = \sqrt{a+L}$ (by definition of $L$ as a fixed point), we have $x_{k+1} < L$.
> *   Therefore, the sequence $(x_n)$ is bounded above by $L = \frac{1 + \sqrt{1+4a}}{2}$.

>[!|]+ Primer: Dokaz da limiti $\sin$ in $\cos$ ne obstaja
> 
> 1.  **Predpostavimo nasprotno:** Predpostavimo, da limita zaporedja $\sin(n)$ obstaja in je enaka $L$, torej $\lim_{n \to \infty} \sin(n) = L$.
> 
> 2.  **Gostota vrednosti $\sin(n)$:** Ker je število $\pi$ iracionalno, zaporedje $\{n \pmod{2\pi}\}$ leži gosto v intervalu $[0, 2\pi]$. To pomeni, lahko $n$ zavzame neskončno poljubnih vrednosti iz $[0, 2\pi]$ oz. lahko funkcija doseže vrednosti od $[-1,1]$.
> 
> 3.  **Konstrukcija konvergentnih podzaporedij:** Iz lastnosti v koraku 2 sledi, da lahko vedno najdemo in izberemo:
> *   Podzaporedje $\sin(n_k)$ (za določena naravna števila $n_k$), ki konvergira k $1$, torej $\lim_{k \to \infty} \sin(n_k) = 1$.
> *   Podzaporedje $\sin(m_j)$ (za določena naravna števila $m_j$), ki konvergira k $-1$, torej $\lim_{j \to \infty} \sin(m_j) = -1$.
> 
> 4.  **Protislovje:** Če celotno zaporedje $\sin(n)$ konvergira k $L$, morajo po definiciji limite *vsa* njegova podzaporedja konvergirati k *istemu* $L$. To pa bi pomenilo, da je $L=1$ in hkrati $L=-1$, kar je očitno protislovje.

**Podzaporedje** zaporedja $a_{n}$ je zaporedje $a_{n'}$, kjer je $n' : \mathbb{N} \rightarrow \mathbb{N}$ strogo naraščujoča funkcija.

> Če je $L$ limita $a_{n}$ je $L$ limita vsakega podzaporedja.
> *Ko imamo podzaporedje velja da obstaja tak $K$ ki je večji ali enak $N$ torej so vsi členi podzaporedja tudi v okolici.*

Točka je **stekališče** zaporedja če v vsaki njeni okolici obstaja neskončno členov zaporedja.

Pravimo da ima zaporedje **stekališče v $\infty$** če za vsak interval $(M, \infty)$ velja da vsebuje neskončno elementov.


> Točka je stekališče zaporedja natanko tedaj ko je točka limita nekega njegovega podzaporedja
> *V levo smer imp. po definiciji limite, v desno smer lahko konstruriramo podzaporedje da vzamemo $a_{n_{k}}$ da velja da je v $L- \frac{1}{k}$*

> Če obstaja limita zaporedja je to edino stekališče zaporedja.
> *Po prejšnjem izreku da je limita zaporedja limita vsakega podzaporedja, stekališče zaporedja pa je limita podzaporedja*

> Vsako omejeno zaporedje v realnih številih ima kakšno stekališče v realnih številih.
> *Lahko razpolavljamo interval, kjer ima vsak neskončno členov, nato skonstruriramo podzaporedje tako da vzamemo element iz vsakega zaporedja, ta konvergira - imamo stekališče.*

> Če ima zaporedje natanko eno stekališče in je omejeno je to limita zaporedja.
> *Če definiramo podzaporedje zunaj okolice stekališča, lahko ker vemo da je omejeno najdemo drugo stekališče ker je v protislovju z predpostavko*



**Limes superior** $\lim \sup$ je vrednost proti kateri gre supremum zaporedja.

$$s_{n} = \sup \{ a_{k}\,;\;k>n\}$$
$$\limsup_{n \to \infty} = \lim_{n \to \infty}s_{n}$$

**Limes inferior** $\lim \inf$ je vrednost proti kateri gre infimum zaporedja.

$$s_{n} = \inf \{ a_{k}\,;\;k>n\}$$
$$\liminf{n \to \infty} = \lim_{n \to \infty}s_{n}$$

$\limsup_{n \to \infty} a_n = L_s$, če za vsak $\epsilon > 0$ velja:
1. Obstaja $N_1$ tak, da za vse $n > N_1$ velja $a_n < L_s + \epsilon$.
2.  Za vsak $N_2$ obstaja $n > N_2$ tak, da velja $a_n > L_s - \epsilon$.

$\liminf_{n \to \infty} a_n = L_i$, če za vsak $\epsilon > 0$ velja:
1. Obstaja $N_1$ tak, da za vse $n > N_1$ velja $a_n > L_i - \epsilon$.
2. Za vsak $N_2$ obstaja $n > N_2$ tak, da velja $a_n < L_i + \epsilon$.


Če je zaporedje navzgor oz. navzdol neomejeno sta ti vrednosti $\infty$ oz. $-\infty$.

**Lim sup** in **lim inf** torej vedno obstajata.

> $\lim \sup$ oz. $\lim \inf$ je največje oz. najmanjše stekališče zaporedja $a_{n}$
> >[!|dokaz]+ Dokaz:
> > 
> > Naj bo $(x_n)$ realna zaporedje in določimo
> > 
> > $$y_n := \sup_{k \geq n} x_k \quad \text{in} \quad L := \lim_{n \to \infty} y_n = \limsup_{n \to \infty} x_n.$$
> > 
> > Opomba: vrstica $y_n$ je padajoča (ne narašča), zato limit $L$ obstaja v razširjenih realnih številih.
> > 
> > Najprej dokažemo **da je največje stekališče**
> > 
> > Vzamemo poljuben $x_{n_{j}}$ ki konvergira k $l$. Za vse $j$ velja $x_{n_j} \leq y_{n_j}$.
> > Velja $y_{n_j} \to L$, vzamemo limit v neenakosti in dobimo
> > 
> > $$l = \lim_{j \to \infty} x_{n_j} \leq \lim_{j \to \infty} y_{n_j} = L.$$
> > 
> > Torej nobeno stekališče ne more biti večje od $L$.
> > 
> > **Dokažemo da je stekališče**
> > 
> > Vemo da imamo $s_{k} = \{ \sup a_{n}; n\geq k\}$ ki konvergira k $s$.
> > 
> > To pomeni da lahko konstruriramo naslednje zaporedje.
> > Recimo da že imamo $a_{n_{j-1}}$-ti člen ki je po tej konstrukciji v $(s-\frac{1}{j-1},s+ \frac{1}{j-1})$.
> > Izberemo $k_{j} > n_{j-1}$ tako da velja $s\leq s_{k_{j}} <s+\frac{1}{j}$. Tako lahko izberemo tak $a_{n_{j}}$ tako da velja $s_{kj }- \frac{1}{j}< a_{n_{j}} \leq s_{k_{j}}$ . Po razvoju bo za $a_{n_{j}}$ člen veljalo $s- \frac{1}{j}<a_{n_{j}}<s + \frac{1}{j}$.
> > To pomeni da obstaja neskončno členov v vsaki okolici.


**Zaporedje je** **Cauchyjevo** če za vsako še tako majhno število, za vse pare členov velja da je njuna razlika manjša, za vse pare od nekega indeksa dalje. 



> Konvergentno zaporedje je natanko tedaj ko je Cauchyjevo

>[!|dokaz]+ Dokaz:
> **Predpostavimo, da je zaporedje $(x_n)$ konvergentno k $L \in \mathbb{R}$.**
> To pomeni, da za vsak $\epsilon > 0$ obstaja naravno število $N$ tako, da za vse $n > N$ velja $|x_n - L| < \epsilon/2$.
> 
> Naj bo $\epsilon > 0$ poljuben. Izberimo $N$ po zgornji definiciji.
> Če sta $m, n > N$, potem velja:
> $$|x_m - x_n| = |(x_m - L) - (x_n - L)|$$
> Po trikotni neenakosti je
> $$|x_m - x_n| \le |x_m - L| + |x_n - L|$$
> Ker sta $m, n > N$, je $|x_m - L| < \epsilon/2$ in $|x_n - L| < \epsilon/2$.
> Torej je
> $$|x_m - x_n| < \epsilon/2 + \epsilon/2 = \epsilon$$
> To dokazuje, da je $(x_n)$ Cauchyjevo zaporedje.
> 
>
> **Predpostavimo, da je zaporedje $(x_n)$ Cauchyjevo. **
> Naj bo $(a_n)$ Cauchyjevo zaporedje.
> 
> Najprej dokažemo, da je $(a_n)$ omejeno. Po definiciji Cauchyjevega zaporedja za $\epsilon = 1$ obstaja $N \in \mathbb{N}$ tak, da za vse $n, m \ge N$ velja $|a_n - a_m| < 1$. Izberimo fiksni $m = N$. Potem za vse $n \ge N$ velja $|a_n - a_N| < 1$, kar pomeni $a_N - 1 < a_n < a_N + 1$. S tem so členi zaporedja $a_n$ za $n \ge N$ omejeni. Ker je končno mnogo členov $a_1, \ldots, a_{N-1}$ tudi omejenih, je celotno zaporedje $(a_n)$ omejeno.
> 
> Ker je $(a_n)$ omejeno zaporedje v $\mathbb{R}$, po Bolzano-Weierstrassovem izreku obstaja konvergentno podzaporedje $(a_{n_k})$. Naj bo $\lim_{k \to \infty} a_{n_k} = L$.
> 
> Zdaj pokažemo, da celotno zaporedje $(a_n)$ konvergira k $L$. Naj bo $\epsilon > 0$.
> Ker je $(a_n)$ Cauchyjevo zaporedje, obstaja $N_1 \in \mathbb{N}$ tak, da za vse $n, m \ge N_1$ velja $|a_n - a_m| < \epsilon/2$.
> Ker podzaporedje $(a_{n_k})$ konvergira k $L$, obstaja $K \in \mathbb{N}$ tak da je $n_{K}\geq N_{1}$, in da za vse $k \ge K$ velja $|a_{n_k} - L| < \epsilon/2$.
> 
> Potem za vsak $n \ge N_1$ velja:
> $|a_n - L| = |a_n - a_{n_K} + a_{n_K} - L|$
> Po trikotniški neenakosti je $|a_n - L| \le |a_n - a_{n_K}| + |a_{n_K} - L|$.
> Ker sta $n$ in $n_K$ oba večja ali enaka $N_1$, je $|a_n - a_{n_K}| < \epsilon/2$.
> Ker je $K \ge N_2$, je $|a_{n_K} - L| < \epsilon/2$.
> Torej, za vse $n \ge N_1$ velja $|a_n - L| < \epsilon/2 + \epsilon/2 = \epsilon$.
> Sledi, da zaporedje $(a_n)$ konvergira k $L$.


**Izrek o sednviču**

$$a_{n} \leq b_{n} \leq c_{n}$$
$$a_{n} \rightarrow L, c_{n} \rightarrow L$$
$$\Rightarrow b_{n} \rightarrow L$$

>[!|dokaz]- Dokaz:
>$a_n \le b_n \le c_n$ za vse $n \ge N_0$ (za neko naravno število $N_0$)
>
> Naj bo $\epsilon > 0$ poljubno.
> 
> Ker $\lim_{n \to \infty} a_n = L$, obstaja $N_1 \in \mathbb{N}$ tako, da za vse $n > N_1$ velja $|a_n - L| < \epsilon$. To pomeni $L - \epsilon < a_n < L + \epsilon$. Zadošča nam $L - \epsilon < a_n$.
> 
> Ker $\lim_{n \to \infty} c_n = L$, obstaja $N_2 \in \mathbb{N}$ tako, da za vse $n > N_2$ velja $|c_n - L| < \epsilon$. To pomeni $L - \epsilon < c_n < L + \epsilon$. Zadošča nam $c_n < L + \epsilon$.
> 
> Definirajmo $N = \max(N_0, N_1, N_2)$. Za vsak $n > N$ veljajo vse tri zgornje trditve.
> 
> Za vse $n > N$ imamo:
> Iz $L - \epsilon < a_n$ in $a_n \le b_n$ sledi $L - \epsilon < b_n$.
> Iz $b_n \le c_n$ in $c_n < L + \epsilon$ sledi $b_n < L + \epsilon$.
> 
> Združeno, za vse $n > N$ velja $L - \epsilon < b_n < L + \epsilon$. To je ekvivalentno $|b_n - L| < \epsilon$.
> 
> Ker je bil $\epsilon$ poljuben, po definiciji limite zaporedja sledi, da je $\lim_{n \to \infty} b_n = L$.
> 
> $\blacksquare$

**Aritemtično zaporedje** je zaporedje s konstantno razliko med členi.

$$a_{n} = a_{n-1} + d = a_{1}+d(n-1)$$
$$S_{n} = \frac{n}{2} \cdot  (a_{1}+a_{n})$$

**Geometrično zaporedje** je zaporedje s konstantim koeficientom med členi.

$$a_{n} = a_{n-1} \cdot k = a_{1} \cdot k^{n-1}$$

**Bernoullijeva neenakost**

$$\forall n \in \mathbb{N}, \;\forall \alpha \leq 1 $$ 
$$ (1-\alpha)^{n} \geq 1 -\alpha n$$

>[!|dokaz]+ Dokaz:
>$x \ge -1,$ $k \ge 1$.
> 
> Predpostavimo da drži $(1+x)^k \ge 1+kx$.
> Preverimo za $n=k+1$:
> $(1+x)^{k+1} = (1+x)^k (1+x)$
> $\ge (1+kx)(1+x)$
> $= 1+x+kx+kx^2$
> $= 1+(k+1)x+kx^2$
> $\ge 1+(k+1)x$
> Sledi $(1+x)^{k+1} \ge 1+(k+1)x$.
> Po principu matematične indukcije neenačba drži za vse $k \ge 1$.

**Zaporedje $a_{n} := (1+ \frac{1}{n})^{n}$ je konvergentno in konvergira k $e$.**
>[!|dokaz]- Dokaz:
> 
> Najprej pokažemo, da je zaporedje $a_n = \left(1 + \frac{1}{n}\right)^n$ naraščajoče.
> Uporabimo binomski izrek za $a_n$:
> $a_n = \sum_{k=0}^n \binom{n}{k} \left(\frac{1}{n}\right)^k = \sum_{k=0}^n \frac{n(n-1)\dots(n-k+1)}{k!} \frac{1}{n^k} = \sum_{k=0}^n \frac{1}{k!} \left(1 - \frac{1}{n}\right)\left(1 - \frac{2}{n}\right)\dots\left(1 - \frac{k-1}{n}\right)$
> 
> Podobno za $a_{n+1}$:
> $a_{n+1} = \sum_{k=0}^{n+1} \frac{1}{k!} \left(1 - \frac{1}{n+1}\right)\left(1 - \frac{2}{n+1}\right)\dots\left(1 - \frac{k-1}{n+1}\right)$.
> 
> Za vsak $k \in \{0, 1, \dots, n\}$, in vsak $j \in \{1, \dots, k-1\}$, velja $\frac{j}{n+1} < \frac{j}{n}$, torej $1 - \frac{j}{n+1} > 1 - \frac{j}{n}$.
> Zato je vsak člen v razvoju $a_{n+1}$ (razen $k=0$ in $k=1$, kjer sta člena $1$ in $1$ oziroma $\frac{1}{1!}$ in $\frac{1}{1!}$, ki sta enaka) večji ali enak kot ustrezen člen v razvoju $a_n$. Poleg tega ima $a_{n+1}$ še dodaten, pozitiven $(n+1)$-ti člen.
> Sledi $a_n < a_{n+1}$ za vse $n \in \mathbb{N}$, kar pomeni, da je zaporedje $a_n$ strogo naraščajoče.
> 
> Nato pokažemo, da je zaporedje $a_n$ navzgor omejeno.
> Iz binomskega razvoja $a_n = \sum_{k=0}^n \frac{1}{k!} \left(1 - \frac{1}{n}\right)\left(1 - \frac{2}{n}\right)\dots\left(1 - \frac{k-1}{n}\right)$ sledi, da je
> $a_n < \sum_{k=0}^n \frac{1}{k!} \quad$ (ker so vsi faktorji $1 - \frac{j}{n}$ manjši od 1).
> Za $k \ge 2$ velja $k! = 1 \cdot 2 \cdot 3 \dots k \ge 1 \cdot 2 \cdot 2 \dots 2 = 2^{k-1}$.
> Zato je $\frac{1}{k!} \le \frac{1}{2^{k-1}}$ za $k \ge 1$.
> $a_n < \frac{1}{0!} + \frac{1}{1!} + \sum_{k=2}^n \frac{1}{k!} = 1 + 1 + \sum_{k=2}^n \frac{1}{k!} \le 2 + \sum_{k=2}^n \frac{1}{2^{k-1}}$.
> Vsota $\sum_{k=2}^n \frac{1}{2^{k-1}}$ je delna vsota geometrijske vrste $1/2 + 1/4 + 1/8 + \dots$, katere vsota je 1.
> Torej, $a_n < 2 + \sum_{k=1}^\infty \frac{1}{2^k} = 2 + 1 = 3$.
> Zaporedje $a_n$ je navzgor omejeno s 3.
> 
> Ker je zaporedje $a_n$ naraščajoče in navzgor omejeno, po izreku o monotonih in omejenih zaporedjih konvergira. Naj bo $L = \lim_{n \to \infty} a_n$.
> 
> Sedaj pokažemo, da je $L = e = \sum_{k=0}^\infty \frac{1}{k!}$.
> Iz $a_n = \sum_{k=0}^n \frac{1}{k!} \left(1 - \frac{1}{n}\right)\left(1 - \frac{2}{n}\right)\dots\left(1 - \frac{k-1}{n}\right)$ in $1 - \frac{j}{n} < 1$ sledi $a_n < \sum_{k=0}^n \frac{1}{k!} \le \sum_{k=0}^\infty \frac{1}{k!} = e$.
> Zato je $L \le e$.
> 
> Za poljuben fiksiran $M \in \mathbb{N}$ in za $n \ge M$:
> $a_n = \sum_{k=0}^n \frac{1}{k!} \prod_{j=1}^{k-1} \left(1 - \frac{j}{n}\right) \ge \sum_{k=0}^M \frac{1}{k!} \prod_{j=1}^{k-1} \left(1 - \frac{j}{n}\right)$.
> Ko gre $n \to \infty$, vsak faktor $\left(1 - \frac{j}{n}\right) \to 1$.
> Zato $\lim_{n \to \infty} a_n \ge \sum_{k=0}^M \frac{1}{k!} \prod_{j=1}^{k-1} (1) = \sum_{k=0}^M \frac{1}{k!}$.
> Ker to velja za vsak $M$, lahko vzamemo limito, ko $M \to \infty$:
> $\lim_{n \to \infty} a_n \ge \lim_{M \to \infty} \sum_{k=0}^M \frac{1}{k!} = \sum_{k=0}^\infty \frac{1}{k!} = e$.
> 
> Ker je $L \le e$ in $L \ge e$, mora biti $L=e$.
> Tako je zaporedje $a_n = \left(1 + \frac{1}{n}\right)^n$ konvergentno in konvergira k $e$.
> 
> $\blacksquare$


***
Množica je **zaprta** če velja da je vsako stekališče zaporedij vsebovano v množici.

Množica je **omejena** če ima vsako zaporedje stekališče.

Množica je **kompaktna** če velja da ima vsako zaporedje stekališče vsebovano v množici.
***



**Vrsta** je zaporedje oblike

$$s_{1} = a_{1}$$
$$s_{2} = a_{1}+ a_{2}$$
$$s_{n} = a_{1}+...+a_{n}$$
$$s_{n} = \sum_{i=1}^{n} a_i = a_{1}+...+a_{n}$$

**Vrsta konvergira** če je konvergentno zaporedje delnih vsot. Taki limiti pravimo **vsota vrste**.

$$\lim_{n \to \infty}s_{n} = \sum_{1}^{\infty}a_{k}$$



**Geometrijska vrsta** je vrsta oblike

$$\sum_{0}^{\infty}k^j$$
$$S_{n} = 1 + k + ... + k^{n}$$
$$S_{n}k = k + k^2 + ... + k^{n+1}$$
$$...$$
$$S_{n} = \frac{1-k^{n+1}}{1-k}$$
$$\sum_{1}^{\infty} = \frac{1}{k-1} ;\; |k |<1$$

> Geomterijska vrsta je konvergentna če je $k \in (-1,1)$ konvergira pa k $\frac{1}{k-1}$.

**Hamonična vrsta** je vrsta oblike

$$\sum_{1}^{\infty} \frac{1}{j}$$

vemo da zaporedje $\frac{1}{n}$ konvergira k nič, a ta vrsta divergira.

> Vrsta je konvergentna natanko tedaj, ko je Cauchyjeva.
>$$\left| \sum_{n+1}^{m} a_{j}\right| < \varepsilon$$

>Če vrsta konvergira, zaporedje konvergira k 0.
>*$a_{n} = s_{n+1}-s_{n} \rightarrow s-s = 0$*







Vrsta je **absolutno konvergentna** če je 

$$\sum_{1}^{\infty}|a_{n}| < \infty$$

> Če je vrsta absolutno konvergentna je konvergentna.
> *Cauchyjev pogoj ... $|s_{m}-s_{n}| = |\sum_{n+1}^{m}a_{j}| \leq \sum_{n+1 }^{m}|a_{j}|<\varepsilon$*

**Primerjalni kriterij** je pravilo ki pravi da če imamo dve vrsti z **nenegativnimi členi** in ena konvergira, potem konvergira vsaka vrsta manjša od nje. Vrsta, ki omejuje manjše vrste se imenuje **majoranta**.

>[!|dokaz]- Dokaz:
>Če imamo dve zaporedji $a_{n} \geq b_{n} \geq 0 \; \forall n$ in $\sum_{0}^{\infty}a_{n}$ konvergira, potem lahko omejimo $a_{n}$ z $M$. Velja $b_{n} \leq a_{n} \leq M$, in ker ima vrsta $\sum_{0}^{\infty}b_{n}$ samo nenegativne člene je monotono nepadajoča. Monotono in omejeno zaporedje mora konvergirati.

> Če neka vrsta divergira potem divergira vsak vrsta večja od nje.

**Kvocientni / d'Alembertov kriterij** je pravilo, ki pravi da če je limita kvocienta sosednjih členov manjša od 1 potem vrsta absolutno konvergira, če je večja od 1 divergira, če pa je 1 pa ne vemo.
Izhaja iz geometrijske vrste kjer vemo da če je kvocient manjši od 1 potem vrsta konvergira.

$$D_{n} = \left|\frac{a_{n+1}}{a_{n}} \right|$$

$$D < 1$$

>[!|dokaz]- Dokaz:
> Ker je $L < 1$, lahko izberemo $\epsilon$, da velja $L + \epsilon < 1$.
> Obstaja $N$ da za vse $n \ge N$ velja:
> $\left| \frac{a_{n+1}}{a_n} \right| < L + \epsilon = q$.
> 
> Od tod sledi:
> $|a_{N+1}| < q|a_N|$
> $|a_{N+2}| < q|a_{N+1}| < q^2|a_N|$
> ...
> $|a_n| < q^{n-N}|a_N|$ za $n > N$.
> 
> Vrsto $\sum_{n=N+1}^\infty |a_n|$ lahko primerjamo z geometrijsko vrsto $\sum_{n=N+1}^\infty |a_N|q^{n-N} = |a_N| \sum_{k=1}^\infty q^k$. Ker je $0 < q < 1$, ta geometrijska vrsta konvergira.
> Po primerjalnem kriteriju vrsta $\sum_{n=N+1}^\infty |a_n|$ konvergira.
> Posledično konvergira tudi vrsta $\sum_{n=1}^\infty |a_n|$, kar pomeni, da prvotna vrsta $\sum_{n=1}^\infty a_n$ konvergira absolutno.
> 
> ---
$L > 1$
> 
> $|a_{N+1}| > r|a_N|$
> $|a_{N+2}| > r|a_{N+1}| > r^2|a_N|$
> ...
> $|a_n| > r^{n-N}|a_N|$ za $n > N$.
> 
> Ker je $r > 1$ in $|a_N| > 0$ (če bi bil $a_N=0$ za neko $N$, bi morali predpostaviti $a_n \ne 0$ za dovolj velike $n$, sicer bi bila limita $L=0<1$ ali nedefinirana), velja $\lim_{n \to \infty} |a_n| = \infty$.
> Zato $\lim_{n \to \infty} a_n \ne 0$.
> Po kriteriju za divergenco (n-ti člen vrste ne konvergira proti 0) vrsta $\sum_{n=1}^\infty a_n$ divergira.
> 
> ---
> $L=1$
> 
> *   Harmonična vrsta $\sum_{n=1}^\infty \frac{1}{n}$ divergira, vendar je $\lim_{n \to \infty} \left| \frac{1/(n+1)}{1/n} \right| = \lim_{n \to \infty} \frac{n}{n+1} = 1$.
> *   Vrsta $\sum_{n=1}^\infty \frac{1}{n^2}$ (p-vrsta z $p=2$) konvergira, vendar je $\lim_{n \to \infty} \left| \frac{1/(n+1)^2}{1/n^2} \right| = \lim_{n \to \infty} \left( \frac{n}{n+1} \right)^2 = 1$.
> 
> V obeh primerih je $L=1$, vendar je ena vrsta divergentna in druga konvergentna. Zato kriterij v primeru $L=1$ ne more določiti konvergence ali divergence.

**Korenski / Cauchyjev kriterij** je pravilo, ki pravi da če je limita n-tega korena n-tega člena manjša od 1 potem vrsta konvergira, če je večja od 1 divergira, če je 1 pa ne vemo.

$$C_{n} = \sqrt[n]{|a_{n}|}$$

Spet izhaja iz geomtrijske vrste kjer je geometrijska vrsta majoranta. 

$$\sqrt[n]{|a_{n}|} \leq k < 1 \Rightarrow |a_{n}| \leq k^{n} < 1$$

>[!|dokaz]- Dokaz:
> Predpostavimo, da je $\boldsymbol{L < 1}$. Izberimo realno število $r$ tako, da velja $L < r < 1$.
> 
> Po definiciji limite superior obstaja tak $N \in \mathbb{N}$, da za vse $n > N$ velja $\sqrt[n]{a_n} < r$.
> 
> To pomeni, da je $a_n < r^n$ za vse $n > N$.
> 
> Ker je $0 \le r < 1$, geometrijska vrsta $\sum_{n=1}^\infty r^n$ konvergira.
> 
> **Po primerjalnem kriteriju vrsta $\sum a_n$ konvergira.**
> 
Vrsta je **alternirajoča** če za vse $n$ velja da je predznak prejšnjega člena drugačen trenutnemu.

**Leibnizov konvergenčni kriterij** trdi da če zaporedje konvergira k nič in je padajoče in pozitivno potem konvergira vrsta 

$$\sum_{1 }^{\infty} (-1)^{j}a_{j}$$

>[!|dokaz]+ Dokaz:
> Označimo delne vsote z $S_N = \sum_{n=1}^N (-1)^{n+1} a_n$. Preučujmo zaporedji sodih in lihih delnih vsot.
> 
> **Zaporedje sodih delnih vsot:** $S_{2k} = a_1 - a_2 + a_3 - a_4 + \dots + a_{2k-1} - a_{2k}$.
> $S_{2k} = (a_1 - a_2) + (a_3 - a_4) + \dots + (a_{2k-1} - a_{2k})$.
> Ker je $a_n \ge a_{n+1}$, so vsi členi v oklepajih nenegativni: $a_{2j-1} - a_{2j} \ge 0$.
> **Zaporedje $S_{2k}$ je naraščajoče.**
> 
> Omejenost od zgoraj: $S_{2k} = a_1 - (a_2 - a_3) - (a_4 - a_5) - \dots - (a_{2k-2} - a_{2k-1}) - a_{2k}$.
> Ker so $a_j - a_{j+1} \ge 0$ in $a_{2k} > 0$, velja $S_{2k} \le a_1$.
> **Zaporedje $S_{2k}$ je naraščajoče in navzgor omejeno, zato konvergira k neki limiti $L_S$.**
> 
> ---
> 
> **Zaporedje lihih delnih vsot:** $S_{2k+1} = a_1 - a_2 + a_3 - a_4 + \dots + a_{2k-1} - a_{2k} + a_{2k+1}$.
> $S_{2k+1} = a_1 - (a_2 - a_3) - (a_4 - a_5) - \dots - (a_{2k} - a_{2k+1})$.
> Ker je $a_n \ge a_{n+1}$, so vsi členi v oklepajih nenegativni: $a_{2j} - a_{2j+1} \ge 0$.
> **Zaporedje $S_{2k+1}$ je padajoče.**
> 
> Omejenost od spodaj: $S_{2k+1} = (a_1 - a_2) + (a_3 - a_4) + \dots + (a_{2k-1} - a_{2k}) + a_{2k+1}$.
> Ker so $a_j - a_{j+1} \ge 0$ in $a_{2k+1} > 0$, velja $S_{2k+1} \ge 0$.
> **Zaporedje $S_{2k+1}$ je padajoče in navzdol omejeno, zato konvergira k neki limiti $L_L$.**
> 
> ---
> 
> **Konvergenca k isti limiti:**
> Preučimo razliko med sosednjimi delnimi vsotami: $S_{2k+1} - S_{2k} = a_{2k+1}$.
> Po pogoju 2 je $\lim_{k \to \infty} a_{2k+1} = 0$.
> Torej $\lim_{k \to \infty} (S_{2k+1} - S_{2k}) = 0$.
> To pomeni, da $L_L - L_S = 0$, oziroma $L_L = L_S$.
> **Obe zaporedji delnih vsot (sodih in lihih) konvergirata k isti limiti $L = L_S = L_L$.**
> 
> Ker obe podzaporedji, ki pokrivata vse delne vsote vrste, konvergirata k isti limiti, **zaporedje delnih vsot $S_N$ konvergira k $L$. S tem je dokazano, da alternirajoča vrsta konvergira.**

> Ob tem velja da je $|s - s_{n}| \leq a_{n+1}$

Vrsta je **brezpogojno konvergentna**, če za vsako permutacijo indeksov konvergira.

Vrsta je **pogojno konvergentna** če je konvergentna, a ne brezpogojno.


**Konvergentne vrste**

1. Geometrijska vrsta

$$\sum_{1}^{\infty}k^j$$
$$S_{n} = 1 + k + ... + k^{n}$$
$$S_{n}k = a_{1}k + a_{1}k^2 + ... + a_{1}k^{n+1}$$
$$...$$
$$S_{n} = \frac{1-k^{n+1}}{1-k}$$
$$\sum_{1}^{\infty} = \frac{1}{k-1} ;\; |k |<1$$

2. P-vrste, kjer je $p > 1$


$$ \sum_{n=1}^{\infty} \frac{1}{n^{p}}\text{ kjer je $p > 1$} $$

>[!|dokaz]- Dokaz:
> Formiramo kondenzirano vrsto $\sum_{k=1}^{\infty} 2^k a_{2^k}$.
> 
> $$a_{2^k} = \frac{1}{(2^k)^p} = \frac{1}{2^{kp}}$$
> 
> Kondenzirana vrsta je:
> $$\sum_{k=1}^{\infty} 2^k \frac{1}{2^{kp}} = \sum_{k=1}^{\infty} 2^{k - kp} = \sum_{k=1}^{\infty} (2^{1-p})^k$$
> 
> Ker je $2^0 = 1$, mora biti eksponent $1-p < 0$.
> To pomeni $1 < p$.
> 
> Torej, kondenzirana vrsta $\sum_{k=1}^{\infty} (2^{1-p})^k$ konvergira, če in samo če $p > 1$.
> Po Cauchyjevem kondenzacijskem kriteriju prvotna p-vrsta konvergira, če in samo če $p > 1$.

>[!|dokaz]- Dokaz za Cauchyjev kondenzacijski kriterij:
> **$(\Leftarrow)$ Predpostavimo, da vrsta $\sum_{k=0}^\infty 2^k a_{2^k}$ konvergira.**
> To pomeni, da je zaporedje delnih vsot $(T_K)$ omejeno od zgoraj. Naj bo $T = \lim_{K\to\infty} T_K$.
> Obravnavajmo delno vsoto $S_N$. Za poljuben $N$ izberemo $K$ tako, da je $N < 2^K$.
> $$S_N = \sum_{n=1}^N a_n \le \sum_{n=1}^{2^K-1} a_n$$
> Združimo člene v $\sum_{n=1}^{2^K-1} a_n$ v bloke:
> $$\sum_{n=1}^{2^K-1} a_n = a_1 + (a_2+a_3) + (a_4+a_5+a_6+a_7) + \dots + (a_{2^{K-1}} + \dots + a_{2^K-1})$$
> Ker je zaporedje $(a_n)$ ne-naraščajoče, za vsak blok $k \ge 1$ velja:
> $$a_{2^k} + a_{2^k+1} + \dots + a_{2^{k+1}-1} \le a_{2^k} + a_{2^k} + \dots + a_{2^k} = 2^k a_{2^k}$$
> (V vsakem bloku je $2^k$ členov, in vsak člen je manjši ali enak prvemu členu bloka $a_{2^k}$).
> Tako lahko zapišemo:
> $$S_N \le a_1 + 2a_2 + 4a_4 + \dots + 2^{K-1} a_{2^{K-1}}$$
> Desna stran te neenakosti je natanko $T_{K-1}$.
> Torej velja:
> $$S_N \le T_{K-1}$$
> Ker $\sum 2^k a_{2^k}$ konvergira, je $T_K$ omejena (npr. z $T$). Zato je $S_N \le T_{K-1} \le T$. Ker je zaporedje $(S_N)$ monotono naraščajoče in omejeno od zgoraj, konvergira.