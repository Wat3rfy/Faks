> Premica, parametrična in normalna oblika, projekcija točke na premico
> alternativna enačba za razdaljo pravokotne projekcije točke do premice
> ravnine, hiperravnine, parametrična enačba ravnine, normalna enačba ravnine
> povezava med linearnimi enačbami in hiperravninami
> Pravokotna projekcija na hiperravnine

## Premice v $\mathbb{R}^n$

Premico v $\mathbb{R}^n$ najpogosteje podamo s točko na premici in smernimi vektorjem. Če je $\vec{r}_0$ dana točka na premici in $\vec{p}$ dani vektor v smeri premice, potem poljubno točko $\vec{r}$ na tej premici izrazimo kot:
$$ \vec{r} = \vec{r}_0 + t\vec{p} $$
kjer je $t$ poljubno realno število. Spremenljivki $t$ pravimo **parameter**, enačbi pa **parametrična enačba premice**.

Če sta $\vec{r}_0=(r_{01}, \dots, r_{0n})$ in $\vec{p}=(p_1, \dots, p_n)$, potem lahko parametrično enačbo zapišemo po komponentah kot:
$$ x_1 = r_{01} + tp_1$$ $$\dots$$ $$ x_n = r_{0n} + tp_n $$
Če se požvižgamo na morebitno deljenje z nič (torej če so vsi $p_i \ne 0$), lahko izrazimo $t$ iz vsake enačbe in zapišemo:
$$ \frac{x_1 - r_{01}}{p_1} = \dots = \frac{x_n - r_{0n}}{p_n} (=t) $$
Tej enačbi pravimo **normalna (ali simetrična) enačba premice**. Če je premica podana z normalno enačbo, jo je običajno najprej pretvoriti v parametrično enačbo, saj je ta najprimernejša za računanje.

>[!|hide]- **Primer:** 
> Poiščimo normalno enačbo premice v $\mathbb{R}^3$, ki gre skozi točki $\vec{r}_1=(0, -2, 1)$ in $\vec{r}_2=(3, -2, -1)$.
> Najprej poiščemo točko $\vec{r}_0$ na premici in vektor $\vec{p}$ v smeri premice. Vzamemo lahko $\vec{r}_0 = \vec{r}_1 = (0, -2, 1)$. Smerni vektor $\vec{p}$ dobimo z odštevanjem točk:
> $\vec{p} = \vec{r}_2 - \vec{r}_1 = (3-0, -2-(-2), -1-1) = (3, 0, -2)$.
> Normalna enačba se potem glasi:
> $$ \frac{x_1 - 0}{3} = \frac{x_2 - (-2)}{0} = \frac{x_3 - 1}{-2} $$
> Kar se poenostavi v:
> $$ \frac{x_1}{3} = \frac{x_2 + 2}{0} = \frac{x_3 - 1}{-2} $$


Opomba: deljenje z $0$ v normalni enačbi pomeni, da je ustrezna koordinata konstantna (npr. $x_2 = -2$).

**Osnovne naloge s premicami so:**
*   Pravokotna projekcija točke na premico.
*   Zrcaljenje točke čez premico.
*   Razdalja točke od premice.

Recimo, da bi radi pravokotno projecirali točko $\vec{r}_1$ na premico $\vec{r} = \vec{r}_0 + t\vec{p}$. Iskano točko projekcije označimo z $\vec{r}_1'$.
Ker točka $\vec{r}_1'$ leži na premici, obstaja tak skalar $t$, da velja:
$$ \vec{r}_1' = \vec{r}_0 + t\vec{p} $$
Skalar $t$ moramo določiti tako, da je vektor $\vec{r}_1 - \vec{r}_1'$ pravokoten na smerni vektor $\vec{p}$. To pomeni, da mora biti njun skalarni produkt enak nič:
$$ \langle\vec{r}_1 - \vec{r}_1', \vec{p}\rangle = 0 $$
Vstavimo izraz za $\vec{r}_1'$:
$$ \langle\vec{r}_1 - (\vec{r}_0 + t\vec{p}), \vec{p}\rangle = 0 $$
$$ \langle\vec{r}_1 - \vec{r}_0 - t\vec{p}, \vec{p}\rangle = 0 $$
Zaradi linearnosti skalarnega produkta:
$$ \langle\vec{r}_1 - \vec{r}_0, \vec{p}\rangle - t\langle\vec{p}, \vec{p}\rangle = 0 $$
Odtod izrazimo $t$:
$$ t = \frac{\langle\vec{r}_1 - \vec{r}_0, \vec{p}\rangle}{\langle\vec{p}, \vec{p}\rangle} $$
Ko izračunamo $t$, ga vstavimo nazaj v enačbo za $\vec{r}_1'$, da dobimo koordinate projekcije:
$$ \vec{r}_1' = \vec{r}_0 + \frac{\langle\vec{r}_1 - \vec{r}_0, \vec{p}\rangle}{\langle\vec{p}, \vec{p}\rangle}\vec{p} $$
Oddaljenost $d$ točke $\vec{r}_1$ od premice je enaka dolžini vektorja med točko in njeno projekcijo:
$$ d = \left\Vert \vec{r}_1 - \vec{r}_1'\right\Vert $$
Zrcalna slika $\vec{r}_1''$ točke $\vec{r}_1$ glede na premico je točka, za katero je projekcija $\vec{r}_1'$ razpolovišče daljice med $\vec{r}_1$ in $\vec{r}_1''$. Torej $\vec{r}_1' = \frac{1}{2}(\vec{r}_1 + \vec{r}_1'')$, od koder sledi:
$$ \vec{r}_1'' = 2\vec{r}_1' - \vec{r}_1 $$
Kadar smo v $\mathbb{R}^3$, lahko pri računanju oddaljenosti točke $\vec{r}_1$ od premice $\vec{r} = \vec{r}_0 + t\vec{p}$ uporabimo tudi vektorski produkt. Oddaljenost je enaka ploščini paralelograma, ki ga razpenjata vektorja $\vec{r}_1 - \vec{r}_0$ in $\vec{p}$, deljeni z dolžino vektorja $\vec{p}$:
$$ d = \frac{\left\Vert ( \vec{r}_1 - \vec{r}_0) \times \vec{p}\right\Vert}{\left\Vert \vec{p}\right\Vert} $$
Tako leva kot desna stran sta enaki $\left\Vert \vec{r}_1 - \vec{r}_0\right\Vert \sin \phi$, kjer je $\phi$ kot med vektorjema $\vec{r}_1 - \vec{r}_0$ in $\vec{p}$.

## Ravnine in hiperravnine v $\mathbb{R}^n$

Ravnino v $\mathbb{R}^3$ lahko podamo na dva načina, ki ju posplošimo na **hiperravnine** v $\mathbb{R}^n$:

1.  **Parametrična enačba (za ravnino v $\mathbb{R}^3$):** Podana s točko $\vec{r}_0$ na ravnini in dvema linearno neodvisnima smernima vektorjema $\vec{p}$ in $\vec{q}$. V tem primeru poljubna točka $\vec{r}$ na ravnini zadošča enačbi:
    $$ \vec{r} = \vec{r}_0 + s\vec{p} + t\vec{q} $$
    kjer sta $s$ in $t$ poljubna realna parametra. Ta način podajanja ravnin deluje tudi v $\mathbb{R}^n$, kjer določa $k$-razsežno podprostor (če je $k$ število smernih vektorjev).

2.  **Normalna enačba (za hiperravnino v $\mathbb{R}^n$):** Podana s točko $\vec{r}_0$ na ravnini in z neničelno **normalo** $\vec{n}$ (vektorjem, ki je pravokoten na ravnino). V tem primeru poljubna točka $\vec{r}$ na ravnini zadošča enačbi:
    $$ \langle\vec{n}, \vec{r} - \vec{r}_0\rangle = 0 $$
    Ta enačba določa $(n-1)$-razsežno podmnožico v $\mathbb{R}^n$, ki ji pravimo hiperravnina.

**Opombe o hiperravninah:**
*   Hiperravnine v $\mathbb{R}^1$ so točke.
*   Hiperravnine v $\mathbb{R}^2$ so premice.
*   Hiperravnine v $\mathbb{R}^3$ so ravnine.
*   Hiperravnine v $\mathbb{R}^4$ so trirazsežne množice.
>Hiperravnina v $\mathbb{R}^n$ je ravno množice rešitev  linearne enačbe v $n$ spremenljivkah. 
<br>Če v enačbo hiperravnine vstavimo $\vec{n}=(a_1, \dots, a_n)$ in $\vec{r}_0=(x_{01}, \dots, x_{0n})$ ter $\vec{r}=(x_1, \dots, x_n)$, dobimo linearno enačbo:
$a_1(x_1 - x_{01}) + \dots + a_n(x_n - x_{0n}) = 0$
kar je ekvivalentno $a_1 x_1 + \dots + a_n x_n = a_1 x_{01} + \dots + a_n x_{0n}$. Če desno stran označimo z $b$, dobimo splošno obliko $a_1 x_1 + \dots + a_n x_n = b$.<br> 
Velja tudi obratno: vsako linearno enačbo $a_1 x_1 + \dots + a_n x_n = b$, kjer $a_i \ne 0$ za vsaj en $i$, lahko zapišemo v obliki $\langle\vec{n}, \vec{r} - \vec{r}_0\rangle = 0$, kjer je $\vec{n}=(a_1, \dots, a_n)$ in $\vec{r}_0$ poljubna točka na ravnini (npr. $(b/a_1, 0, \dots, 0)$ če $a_1 \ne 0$).

**Primer: Prehod iz parametrične v normalno enačbo ravnine**
Poiščimo normalno enačbo ravnine v $\mathbb{R}^3$, ki ima parametrično enačbo:
$$ \vec{r} = (1, 2, -1) + s(2, 1, 3) + t(-1, 1, 1) $$
Zapišemo enačbo po komponentah:
$x = 1 + 2s - t$
$y = 2 + s + t$
$z = -1 + 3s + t$
Cilj je eliminirati parametra $s$ in $t$.
Iz prve enačbe izrazimo $t$: $t = 1 + 2s - x$.
Vstavimo $t$ v drugo in tretjo enačbo:
$y = 2 + s + (1 + 2s - x) \implies y = 3 + 3s - x \implies 3s = x + y - 3 \implies s = \frac{1}{3}x + \frac{1}{3}y - 1$
$z = -1 + 3s + (1 + 2s - x) \implies z = 5s - x$
Sedaj v enačbo za $z$ vstavimo izraz za $s$:
$z = 5\left(\frac{1}{3}x + \frac{1}{3}y - 1\right) - x$
$z = \frac{5}{3}x + \frac{5}{3}y - 5 - x$
$z = \left(\frac{5}{3} - 1\right)x + \frac{5}{3}y - 5$
$z = \frac{2}{3}x + \frac{5}{3}y - 5$
Preuredimo v obliko $ax+by+cz=d$:
$3z = 2x + 5y - 15$
$2x + 5y - 3z = 15$
To je iskana normalna enačba ravnine. (Lahko tudi $2x + 5y - 3z - 15 = 0$).
Normalni vektor ravnine je $\vec{n} = (2, 5, -3)$.

**Osnovne naloge z ravninami in hiperravninami:**
Poglejmo si, kako poiščemo pravokotno projekcijo točke $\vec{r}_1$ na implicitno podano hiperravnino $\langle\vec{n}, \vec{r} - \vec{r}_0\rangle = 0$. Iskana točka projekcije naj bo $\vec{r}_1'$.

Iskana točka $\vec{r}_1'$ leži na preseku hiperravnine in premice, ki gre skozi točko $\vec{r}_1$ in je pravokotna na hiperravnino. To pomeni, da je smerni vektor te premice ravno normala $\vec{n}$.
Torej, $\vec{r}_1'$ je na premici $\vec{r} = \vec{r}_1 + t\vec{n}$ za nek parameter $t$.
Poleg tega $\vec{r}_1'$ leži na hiperravnini, kar pomeni, da zadošča njeni enačbi:
$$ \langle\vec{n}, \vec{r}_1' - \vec{r}_0\rangle = 0 $$
Vstavimo izraz za $\vec{r}_1'$:
$$ \langle\vec{n}, (\vec{r}_1 + t\vec{n}) - \vec{r}_0\rangle = 0 $$
$$ \langle\vec{n}, \vec{r}_1 - \vec{r}_0 + t\vec{n}\rangle = 0 $$
Zaradi linearnosti skalarnega produkta:
$$ \langle\vec{n}, \vec{r}_1 - \vec{r}_0\rangle + t\langle\vec{n}, \vec{n}\rangle = 0 $$
Odtod izrazimo $t$:
$$ t = - \frac{\langle\vec{n}, \vec{r}_1 - \vec{r}_0\rangle}{\langle\vec{n}, \vec{n}\rangle} $$
Iskano točko $\vec{r}_1'$ dobimo tako, da ta skalar $t$ vstavimo v enačbo premice:
$$ \vec{r}_1' = \vec{r}_1 - \frac{\langle\vec{n}, \vec{r}_1 - \vec{r}_0\rangle}{\langle\vec{n}, \vec{n}\rangle}\vec{n} $$

>[!|hide]- **Primer projekcije točke na ravnino:** 
> 
> Izračunajmo pravokotno projekcijo točke $(1, 1, 1)$ na ravnino $x + 2y + 3z = 4$.
> Iz enačbe ravnine preberemo normalo $\vec{n} = (1, 2, 3)$. Za točko $\vec{r}_0$ na ravnini vzamemo katero koli točko, ki zadošča enačbi, npr. če postavimo $y=0, z=0$, dobimo $x=4$, torej $\vec{r}_0 = (4, 0, 0)$. Dana točka je $\vec{r}_1 = (1, 1, 1)$.
> Izračunajmo $\vec{r}_1 - \vec{r}_0 = (1-4, 1-0, 1-0) = (-3, 1, 1)$.
> Izračunajmo $\langle\vec{n}, \vec{r}_1 - \vec{r}_0\rangle = \langle(1, 2, 3), (-3, 1, 1)\rangle = 1(-3) + 2(1) + 3(1) = -3 + 2 + 3 = 2$.
> Izračunajmo $\langle\vec{n}, \vec{n}\rangle = \langle(1, 2, 3), (1, 2, 3)\rangle = 1^2 + 2^2 + 3^2 = 1 + 4 + 9 = 14$.
> Sedaj izračunajmo parameter $t$:
> $$ t = - \frac{2}{14} = -\frac{1}{7} $$
> Končno vstavimo $t$ v enačbo za $\vec{r}_1'$:
> $$ \vec{r}_1' = \vec{r}_1 + t\vec{n} = (1, 1, 1) - \frac{1}{7}(1, 2, 3) = \left(1 - \frac{1}{7}, 1 - \frac{2}{7}, 1 - \frac{3}{7}\right) $$
> $$ \vec{r}_1' = \left(\frac{6}{7}, \frac{5}{7}, \frac{4}{7}\right) $$
> Sedaj lahko določimo tudi oddaljenost $d$ točke $\vec{r}_1$ od (hiper)ravnine:
> $$ d = \left\Vert \vec{r}_1 - \vec{r}_1'\right\Vert = \left\Vert(1,1,1) - \left(\frac{6}{7}, \frac{5}{7}, \frac{4}{7}\right)\right\Vert = \left\Vert\left(\frac{1}{7}, \frac{2}{7}, \frac{3}{7}\right)\right\Vert $$
> 
> 
> $$ d = \sqrt{\left(\frac{1}{7}\right)^2 + \left(\frac{2}{7}\right)^2 + \left(\frac{3}{7}\right)^2} = \sqrt{\frac{1+4+9}{49}} = \sqrt{\frac{14}{49}} = \sqrt{\frac{2}{7}} = \frac{\sqrt{14}}{7} $$
> In pa zrcalno sliko $\vec{r}_1''$ točke $\vec{r}_1$ glede na (hiper)ravnino:
> $$ \vec{r}_1'' = 2\vec{r}_1' - \vec{r}_1 = 2\left(\frac{6}{7}, \frac{5}{7}, \frac{4}{7}\right) - (1, 1, 1) = \left(\frac{12}{7} - 1, \frac{10}{7} - 1, \frac{8}{7} - 1\right) $$
> $$ \vec{r}_1'' = \left(\frac{5}{7}, \frac{3}{7}, \frac{1}{7}\right) $$


