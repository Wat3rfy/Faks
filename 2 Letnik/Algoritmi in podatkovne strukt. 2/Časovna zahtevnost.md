
**Časovno zahtevnost** opisujemo s številom izvedenih ukazov glede na dolžino vhoda.

Veljalo bo da je dolžina izvajanja programa predstavljena s **pozitivno** funkcijo $f : \mathbb{N} \rightarrow \mathbb{R}, n \mapsto f(n)$, kjer $n$ predstavlja dolžino niza. *Pravimo da program teče v $f(n)$ času, kjer velja da ob $n$ dolgem vhodu izvajamo $f(n)$ ukazov.*
*Pozitivnost je predpostavljena za nadaljne dokaze.*

Poznamo nekaj notacij ki opisujejo razmerja v obnašanju funkcij v neskončnosti.

$$O(g(n)) = \{ f(n) \;;\; \exists C > 0,\exists  n_{0} : \forall n > n_{0} : f(n)\leq Cg(n)   \}$$

*kjer $g(n)$ predstavlja neko zgornjo mejo.*

$$\Omega (g(n)) = \{ f(n) \;;\;   \exists C > 0,\exists  n_{0} : \forall n > n_{0} : f(n)\geq Cg(n ) \}$$



*Idejo lahko izrazimo z limito. Naj bo $\lim_{n \to \infty} \frac{f(n)}{g(n)} = L$. Za vsak $\varepsilon > 0$ obstaja tak $n_0 \in \mathbb{N}$, da za vse $n \geq n_0$ velja $\left| \frac{f(n)}{g(n)} - L \right| < \varepsilon$.Zgornjo neenakost lahko zapišemo brez absolutnih vrednosti kot $L - \varepsilon < \frac{f(n)}{g(n)} < L + \varepsilon$. Da pokažemo da je $f(n)$ v $O(n)/\Omega(n)$ moramo najti $C$. Torej ob predpostavki da limita kvocienta obstaja in je končna in ni enaka 0 lahko za $C$ vzamemo $L+\varepsilon$ (pomnožimo neenačbo z $g(n)$). Za $L = 0$ bo veljalo $-\varepsilon \leq \frac{f(n)}{g(n)} \leq \varepsilon$ torej je v $O(g(n))$ a ne v $\Omega(g(n))$, saj mora biti konstanta pozitivna, ta pa za levo stran neenakosti ne obstaja. Za $L = \infty$ velja da za vsako število $M$ velja da obstaja $n_{0}$ da za vsak večji $n$ velja $\frac{f(n)}{g(n)} > M$, torej za $\Omega$ lahko izberemo $C = M$ a zua $O(n)$ bi morali izbrati $C$ da velja $\frac{f(n)}{g(n)} \leq C$, kar ne moremo saj vemo da za vsak $M$ (torej vsak $C$) obstajajo členi kjer presežemo vrednost $C$. *

*Intuituvni si lahko predstavljamo da če je limita neenaka nič in končna lahko iščemo $C$ pod ali nad limito da dobimo pripadajoč $C$ za $O$ in $\Omega$. Pri limiti $0$ lahko razumemo kot da je $g$ tako večja da je števec $f$ zanemarljivo majhen proti $g$ - torej je gotovo zgornja meja $O(g(n))$ pri limiti $\infty$ pa da je imenovalec $g$ tako zanemarljiv - torej je gotovo spodnja meja $\Omega(g)$.*

Ekvivalentna deifnicija $O(g(n))$ in $\Omega(g(n))$ je

$$O(g(n)) = \{ f(n) \;;\; \lim_{n \to \infty}\frac{f(x)}{g(x)} < \infty \}$$
$$\Omega(g(n)) = \{ f(n) \;;\; \lim_{n \to \infty}\frac{f(x)}{g(x)} > 0 \}$$

Če za $f$ velja da je hkrati v $O(f)$ in $\Omega(g)$ potem velja da je $f \in \Theta(g)$.

$$\Theta (g(n)) =$$ $$ \{ f(n) \;;\;   \exists C_{1},C_{2} > 0,\exists  n_{0} : \forall n > n_{0} : C_{1}g(n )\leq f(n)\leq C_{2}g(n ) \}$$

oz.

$$\Theta (g(n)) = \{ f(n) \;;\;  \lim_{n \to \infty}\frac{f(x)}{g(x)} \in (0,\infty)  \}$$

$O$ in $\Omega$ služita kot spodnja in zgornja meja medtem ko $\Theta$ služi kot enakost v časovni zahtevnosti funkcij.

Poznamo še $o(g(n))$ in $\omega(g(x))$ definirani kot

$$o(g(x)) = \{ f(x) \;;\;  \lim_{n \to \infty}\frac{f(x)}{g(x)} = 0 \}$$
$$\omega(g(x)) = \{ f(x) \;;\;  \lim_{n \to \infty}\frac{f(x)}{g(x)} = \infty \}$$

ki služita kot strogi neenakosti.

> Velja da če $\exists C :f = Cg \Rightarrow f \in \Theta (g(n))$
> >[!|dokaz]+ Dokaz:
> > Če velja dvojna neenakost velja enakost in obratno.
> > $$Cg \leq f \leq Cg \Leftrightarrow Cg = f$$

>Velja
>$$f \in \Theta (g) \Leftrightarrow f \in O(g) \land f \in \Omega(g)$$
>$$f \in \Theta (g) \Leftrightarrow f \notin o(g) \land f \notin \omega(g)$$
>*Uporabno za določanje odnosov.*
>>[!|dokaz]- Dokaz je trivialen


> Velja
> $$f \in o(g) \Rightarrow f \in O(g)  \land f \notin \Omega(g)$$
> $$f \in \omega(g) \Rightarrow f \in \Omega(g) \land f \notin O(g)$$
> *Uporabno za določanje odnosov - ali je $f$ v $O$ - če ni v $O$ ni niti v $o$.*
> >[!|dokaz]- Dokaz je trivialen

> Vse notacije so tranzitivne.
> $O, \Omega, \Theta$ so tudi refleksivne.
> $\Theta$ je tudi simetrična.
> >[!|dokaz]- Dokaz je trivialen

>Velja
>$$f \in O(g) \Leftrightarrow g \in \Omega(f)$$
>$$f \in o(g) \Leftrightarrow g \in \omega(f)$$


> Velja $\Theta (\log_{a}{n}) = \Theta (\log_{b}{n})$
> >[!|dokaz]+ Dokaz:
> >
> >$$\log_{a}{n} = \frac{\log_{b}{n}}{\log_{b}{a}} = C \log_{b}{n}$$
> >$$\Rightarrow \log_{a}{n} \in \Theta (\log_{b}{n})$$

> $n^{a} = o(b^{n}) \,;\;a \geq 0, b>1$ 
> 
> *$n^{a}$ je lahko konstantna funkcija ali poljubna potenca. $b^{n}$ je nekonstantna eksponentna funkcija.*
> >[!|dokaz]+ Dokaz po L'Hopitalu


> Velja
> $$\log^{k}_{}{n} = o(n)$$
> >[!|dokaz]- Dokaz po L'Hopitalu

> Velja
> 
> $$P_{k}[n] \in \Theta (n ^{k})$$
> >[!|dokaz]+ Dokaz:
> > Pogledamo ali je limita kvocienta neko neničelno število in ugotovimo da je.

>Velja
>$$\log_{}{n!} = \Theta (n \log_{}{n})$$
>>[!|dokaz]+ Dokaz:
>$$\sum_{1}^{n}\log_{}{i} \approx \int_{1}^{n}\log_{}{i} \, di = n \log_{}{n} + n \in \Theta (n \log_{}{n})$$

> Stirlingova aproksimacija $n! \approx (\frac{n}{e})^{n}\sqrt[]{2\pi n}$
> >[!|dokaz]+ Dokaz:
> >Dokazujemo le $\frac{n}{e}^{n}$
> > $$n! = 1 \cdot 2 \cdot 3 \cdot \dots \cdot n$$
> > $$\ln(n!) = \ln(1 \cdot 2 \cdot \dots \cdot n) = \ln 1 + \ln 2 + \dots + \ln n$$
> > $$\ln(n!) = \sum_{i=1}^{n} \ln i$$
> > Ker je $\ln x$ naraščajoča funkcija, lahko vsoto za velike $n$ zamenjamo z integralom:
> >     $$\sum_{i=1}^{n} \ln i \approx \int_1^n \ln x \, dx$$
> >     $$\int \ln x \, dx = x \ln x - x$$
> >     $$[x \ln x - x]_1^n = (n \ln n - n) - (1 \cdot \ln 1 - 1) = n \ln n - n + 1$$
> >     $$\ln(n!) \approx n \ln n - n$$
> >     $$n! \approx e^{n\ln n -n }=\left(\frac{n}{e}\right)^{n}$$
> >     
> >    Ostalo pride iz integrala, menjave spremenljivk, mej integracije, reševanje gaussovega integrala na delu kjer je funkcija v integralu največja,...


>Velja
>$$b^{\log_{a}{n}} = n^{\log_{a}{b}} $$ 
>>[!|dokaz]+ Dokaz:
>>$$n^{\log_{a}{b}} =e^{\log_{a}{b}\,\cdot\,\ln n  } = e^{  \frac{\ln n\ln b}{ \ln a}} = b^{\frac{\ln n}{\ln a}}= b^{\log_{a}{n}}$$
