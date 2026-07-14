
**Aproksimacijski algoritmi**

**Optimizacijski problem** $\Pi$ je družina opt. nalog "istega tipa":

$\Pi = \{\pi_1, \pi_2, \dots \}$

**Optimizacijska naloga** je problem z določenimi parametri.

$\pi_i = (D_i, f_i, \text{Opt})$, kjer:
*   $D_i \neq \emptyset$
*   $f_i: D_i \to \mathbb{R}_0^+$
*   $\text{Opt} \in \{\min, \max\}$ (za vse $\pi_i$ isto)

**Oznaka:** $\text{Opt}(\pi_i)$ ... optimalna vrednost optimizacijske naloge $\pi$.

> **Def:** Naj bo $\Pi$ opt. problem in $\mathcal{A}$ algoritem, ki za vsako nalogo iz $\Pi$ vrne dopustno rešitev. Naj bo $\varepsilon > 0$.
> 
> $\mathcal{A}$ je **$\varepsilon$-aproksimacijski algoritem** za $\Pi$, če za vsak $\pi \in \Pi$ velja: (kjer je $\pi = (D, f, \min/\max)$)
> 
> $$\left| \frac{\text{Opt}(\pi) - f(\mathcal{A}(\pi))}{\text{Opt}(\pi)} \right| \leq \varepsilon$$
> 
*relativna napaka alg. $\mathcal{A}$ pri nalogi $\pi$ manjša ali enaka $\varepsilon$.*


**Pri minimizacijski nalogi:**

$$\frac{f(\mathcal{A}(\pi)) - \text{Opt}(\pi)}{\text{Opt}(\pi)} \leq \epsilon $$ 
$$\Downarrow$$

$$f(\mathcal{A}(\pi)) \leq (1 + \epsilon) \text{Opt}(\pi)$$

$(1+\epsilon)$ je **faktor aproksimacije**.

**Pri maksimizacijski nalogi:**


$$\frac{\text{Opt}(\pi) - f(\mathcal{A}(\pi))}{\text{Opt}(\pi)} \leq \epsilon $$ 
$$\Downarrow$$

$$f(\mathcal{A}(\pi)) \geq (1 - \epsilon) \text{Opt}(\pi)$$

$(1-\epsilon)$ je **faktor aproksimacije**.

---

**Maksimalno prirejanje**

**Def:** $G = (V, E)$ graf, $M \subseteq E$ prirejanje.
Prirejanje $M$ je **maksimalno**, če velja:
$\forall e \in E \setminus M, M \cup \{e\}$ ni prirejanje.


> **Trditev:** Naj bosta $M_1, M_2$ maksimalni prirejanji v grafu $G$.
> $\implies |M_1| \leq 2 |M_2|$
> 
> >[!|dokaz]+ Dokaz:
> >
> > Naj bosta $M_1, M_2$ maks. prirejanji v $G$ in recimo, da velja $|M_1| > 2 |M_2|$.
> > Sestavimo graf $H$:
> > *   $V(H) = V(G)$
> > *   $E(H) = M_1 \oplus M_2$ (simetrična razlika)
> > 
> > Vozlišča v $H$ imajo stopnjo 0, 1 ali 2. $H$ je unija poti in ciklov, na katerih se izmenjujejo povezave iz $M_1$ in $M_2$.
> > 
> > 
> > 
> > Ker $|M_1| > 2 |M_2|$:
> > v $H$ obstaja pot dolžine 1 iz $M_1$: (slika posamezne povezave $e \in M_1$).
> > 
> > *(Sicer $|M_1| \leq 2 |M_2|$: na ciklih je št. povezav iz $M_1$ in $M_2$ enako, samo na poteh dolžine 3 pa je lahko povezav iz $M_1$ kvečjemu $2\times$ več kot iz $M_2$; pri vseh drugih potih jih je kvečjemu manj kot toliko).*
> > 
> > Potem je $M_2 \cup \{e\}$ prirejanje, saj $e$ nima skupnih krajišč s povezavami iz $M_2$.
> > Potem pa $M_2$ ni maksimalno prirejanje.

***

**Algoritem za maks. prirejanje $M$**

**Vhod:** $G = (V, E)$
**Izhod:** maksimalno prirejanje $M$

**Postopek:**
$M = \emptyset$
za vse $uv \in E$ ponovi:
$\quad$če $u, v \in \text{prosto}(M)$
$\quad$$\quad$$M = M \cup \{uv\}$
vrni $M$

**Časovna zahtevnost:** $O(|E|)$

> **Trditev:** Algoritem $M$ je $\frac{1}{2}$-aproksimacijski algoritem za iskanje največjega prirejanja.
> 
> >[!|dokaz]+ Dokaz:
> >
> > *   $M_1 \dots$ največje prirejanje ($\text{Opt}(\pi) = |M_1|$)
> > *   $M_2 \dots$ prirejanje, ki ga vrne algoritem ($f(\mathcal{A}(\pi)) = |M_2|$)
> > 
> > $M_1$ in $M_2$ sta maksimalni prirejanji (iz prejšnje trditve vemo):
> > $\implies |M_1| \leq 2 |M_2|$
> > $\implies f(\mathcal{A}(\pi)) = |M_2| \geq \frac{1}{2} |M_1|$
> > 
> > Ker velja $1 - \epsilon = \frac{1}{2} \implies \epsilon = \frac{1}{2}$.
> > Torej je algoritem $\frac{1}{2}$-aproksimacijski algoritem.

---


**Aproksimacijski algoritem za najmanjše pokritje**

**Ideja:** Če je $M$ maksimalno prirejanje $\implies P = \bigcup_{uv \in M} \{u, v\}$ je pokritje.

*Če kakšna povezava ne bi bila pokrita, bi jo lahko dodali v $M$ in $M$ ne bi bilo maksimalno prirejanje.*

**Vhod:** $G = (V, E)$
**Izhod:** pokritje $P$

**Postopek:**
$P = \emptyset$
$E' = E$
$V' = V$
dokler $E' \neq \emptyset$ ponavljaj:
$\quad$ izberi $uv \in E'$
$\quad$ $P = P \cup \{u, v\}$
$\quad$ $V' = V' - \{u, v\}$
$\quad$ $E' = E' - \{ e\text{ s koncem v } u \text{ ali } v\}$
vrni $P$

> **Trditev:** Algoritem B je $1$-aproksimacijski algoritem za problem pokritja.
> 
> >[!|dokaz]+ Dokaz:
> >
> > Naj bo $P^*$ najmanjše pokritje grafa $G = (V, E)$, $P$ pa pokritje, ki ga vrne algoritem B.
> > 
> > 
> > Množica $M = \{e \in E(G); e \text{ je bila izbrana v algoritemu B}\}$ je prirejanje, saj nobeni dve izbrani povezavi nimata skupnega krajišča (zaradi koraka, kjer odstranimo vse povezave s sosednjimi vozlišči).
> > 
> > Velja:
> > *   $|P^*| \geq |M|$, saj je moč vsakega pokritja kvečjemu večja od moči poljubnega prirejanja (šibka dualnost).
> > *   $|P| = 2 |M|$ po konstrukciji algoritma (za vsako povezavo v $M$ vzamemo obe krajišči v množico $P$).
> > 
> > Iz tega sledi:
> > $|P| = 2 |M| \leq 2 |P^*| = (1 + \epsilon) |P^*|$
> > 
> > $\implies \epsilon = 1$. $\blacksquare$