
**Absolutna vrednost**

$$|x| = \begin{cases}
& x;\; x\geq 0 \\ \,
-\!\!\!\!\!\! & x;\; x\leq 0 
\end{cases}$$

Na številski premici označuje razdaljo od 0.

Velja

$$|x| \ge 0$$ 
$$|x| = 0 \iff x = 0$$ 
$$|-x| = |x|$$ 
$$-|x| \le x \le |x|$$

**Trikotniška neenakost**

$$|a+b| \leq |a|+|b|$$

>Posledično velja
>$$  \left| \sum_{}^{}a_{i} \right| \leq \sum_{}^{}|a_{i}|$$
>$$||a|-|b|| \leq |a-b| \leq |a|+|b|$$
>$$||a|-|b|| \leq |a+b| \leq |a|+|b|$$

>Za poljubni realni števili velja $|a||b| = |ab|$


### Fakulteta in binomski simbol


$$n! := 1 \cdot 2 \cdot ... \cdot n$$
$$0! = 1$$
$$\binom{\,n\,}{\,k\,} := \frac{n!}{k!(n-k)!} $$
$$(a+b)^{n} = \sum_{0}^{n}\binom{\,n\,}{\,k\,}a^{k}b^{n-k}$$


### Zadosten in potreben pogoj

Pogoj je **zadosten**, če lahko posledica obstaja brez pogoja. B velja neodvisno od A ampak to da velja A nam da vedeti da velja B.

Pogoj je **potreben**, če velja da posledica ne obstaja če pogoj ne obstaja, ampak pogoj lahko obstaja brez da bi obstajala posledica. Ob $\neg$B vemo da $\neg$ A, ob B pa ne vemo ali A velja ali ne.

![[Pasted image 20250828013415.png]]


### Notacija $o$ (Malo o) in $O$ (Veliko O) v podrobnostih

Notaciji "malo o" ($o$) in "veliko O" ($O$) sta matematični notaciji, ki se uporabljata za opis asimptotičnega obnašanja funkcij. Povejta nam, kako hitro se ena funkcija približuje določeni vrednosti (ponavadi 0 ali $\infty$) ali kako hitro raste/pada v primerjavi z drugo funkcijo. To sta zelo uporabni orodji v analizi, teoriji kompleksnosti algoritmov, numerični analizi in verjetnostni teoriji.

#### $o$ (Malo o notacija)

**Formalna definicija:**
Pravimo, da je funkcija $f(x)$ **malo o** od $g(x)$ ko $x \to a$, in zapišemo
$f(x) = o(g(x)) \quad \text{ko } x \to a$,
če velja
$$\lim_{x \to a} \frac{f(x)}{g(x)} = 0$$
To pomeni, da $f(x)$ konvergira k 0 "hitreje" kot $g(x)$. Funkcija $g(x)$ mora biti različna od 0 v okolici točke $a$ (razen morda v $a$ sami).

**Kaj to pomeni v praksi:**
$f(x) = o(g(x))$ pomeni, da je $f(x)$ zanemarljiva v primerjavi z $g(x)$, ko se $x$ približuje $a$.
Pogosto se uporablja za opisovanje ostankov pri Taylorjevih in podobnih razvoji, kjer ostanek gre proti nič hitreje kot najnižji red členov, ki jih ne zanemarimo.

**Primeri:**
1.  $x^2 = o(x)$ ko $x \to 0$, ker $\lim_{x \to 0} \frac{x^2}{x} = \lim_{x \to 0} x = 0$.
    To pomeni, da se $x^2$ približuje 0 hitreje kot $x$.
2.  $\sin(x) = x + o(x^2)$ ko $x \to 0$. To pomeni, da je $\sin(x) - x = o(x^2)$, torej $\lim_{x \to 0} \frac{\sin(x) - x}{x^2} = 0$.
    (Pravzaprav je to $o(x^3)$ za $\sin(x)$ Taylorjev razvoj, ampak $o(x^3)$ je tudi $o(x^2)$).
3.  $x = o(x^2)$ ko $x \to \infty$, ker $\lim_{x \to \infty} \frac{x}{x^2} = \lim_{x \to \infty} \frac{1}{x} = 0$.
    To pomeni, da $x$ raste počasneje kot $x^2$.

**V vašem dokazu:**
$o(\|g(t+h) - g(t)\|)$ pomeni funkcijo, recimo $R(h)$, za katero velja:
$$\lim_{h \to 0} \frac{R(h)}{\|g(t+h) - g(t)\|} = 0$$
To je točno lastnost ostanka diferenciabilnosti, kot je bilo že razloženo.

#### $O$ (Veliko O notacija)

**Formalna definicija:**
Pravimo, da je funkcija $f(x)$ **veliko O** od $g(x)$ ko $x \to a$, in zapišemo
$f(x) = O(g(x)) \quad \text{ko } x \to a$,
če obstajata pozitivni konstanti $M$ in $\delta$ (ali $N$ za $x \to \infty$), tako da velja
$|f(x)| \le M |g(x)|$
za vse $x$ v neki okolici točke $a$ (npr. $0 < |x-a| < \delta$) ali za vse $x > N$ (če $x \to \infty$).
To pomeni, da je $f(x)$ zgoraj omejena s konstanto krat $g(x)$.

**Kaj to pomeni v praksi:**
$f(x) = O(g(x))$ pomeni, da $f(x)$ raste (ali pada) **največ** tako hitro kot $g(x)$ (do konstantnega faktorja), ko se $x$ približuje $a$ (ali $\infty$). Pove nam zgornjo mejo za rast funkcije. To je zelo pomembno pri analizi časovne ali prostorske kompleksnosti algoritmov, kjer $N$ pomeni velikost vhoda.

**Primeri:**
1.  $3x^2 + 2x + 5 = O(x^2)$ ko $x \to \infty$.
    Za dovolj velike $x$ je $3x^2 + 2x + 5 \le M x^2$ za neko konstanto $M$ (npr. $M=4$ bo deloval za $x \ge 3$).
    To pomeni, da rast $3x^2 + 2x + 5$ ni hitrejša kot rast $x^2$.
2.  $\sin(x) = O(1)$ ko $x \to \infty$, ker $|\sin(x)| \le 1$ za vse $x$.
3.  $f(x) = O(1)$ ko $x \to 0$ pomeni, da je $f(x)$ omejena v okolici 0.
4.  $O(x) = o(x^2)$ ko $x \to \infty$. Če je funkcija $f(x)$ reda $O(x)$, to pomeni, da je $f(x) \le M|x|$. Potem $\lim_{x \to \infty} \frac{M|x|}{x^2} = 0$, torej je $f(x)$ tudi $o(x^2)$.

### Razlika med $o$ in $O$

*   **$o(g(x))$**: Funkcija $f(x)$ je zanemarljiva v primerjavi z $g(x)$. Pade na 0 **bistveno hitreje** kot $g(x)$ (ali raste bistveno počasneje).
*   **$O(g(x))$**: Funkcija $f(x)$ je zgoraj omejena s konstanto krat $g(x)$. Pade na 0 **vsaj tako hitro** kot $g(x)$ (ali raste največ tako hitro).

**Povezava med $o$ in $O$:**
Če je $f(x) = o(g(x))$, potem je tudi $f(x) = O(g(x))$. Nasprotno pa ne velja.
Primer: $x = o(x^2)$ ko $x \to \infty$, in tudi $x = O(x^2)$ ko $x \to \infty$.
Toda $x^2 = O(x^2)$ ko $x \to \infty$, ampak $x^2 \ne o(x^2)$ ko $x \to \infty$ (ker $\lim_{x \to \infty} \frac{x^2}{x^2} = 1 \ne 0$).

### Zakaj sta ti notaciji uporabni?

1.  **Poenostavljanje izrazov:** Omogočata, da se osredotočimo na prevladujoče člene v asimptotičnem obnašanju funkcije, medtem ko zanemarimo nižje redove.
2.  **Diferenciabilnost:** Kot ste videli v dokazu verižnega pravila, notacija $o$ elegantno povzame lastnost ostanka pri linearni aproksimaciji.
3.  **Analiza algoritmov:** V računalništvu se $O$ notacija uporablja za opisovanje časovne in prostorske kompleksnosti algoritmov. Npr., algoritem z zapletenostjo $O(N^2)$ pomeni, da se čas izvajanja poveča sorazmerno s kvadratom velikosti vhoda $N$ (v najslabšem primeru).

Upam, da je ta podrobna razlaga koristna!