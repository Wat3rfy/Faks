Navadne diferencialne enačbe vsebujejo funkcije ene skupne spremenljivke in njene odvode

$$F(x,y,y',...,y^{(n)})=0$$

Stopnja diferencialnih enačb je enaka najvišjemu odvodu prisotnemu v enačbi.

Rešitve diferencialnih enačb so $n$-krat diferenciabilne funkcije, tako da za vse odvode funkcije $y$ velja da rešijo enačbo

$$F(x, y, y', y'', ..., y^{(n)}) = 0$$

Množica splošnih rešitev vsebuje ponavadi $n$ nedoločenih konstant. Temu pravimo družina rešitev.

Partikularna rešitev je če konstantam določimo vrednosti. Te so lahko določene preko dodatnih pogojev za funkcijo.

> **Trditev:** Če sta $y_1$ in $y_2$ rešitvi LDE, je njuna razlika $z = y_1 - y_2$ rešitev homogene enačbe.
> >[!|dokaz]- Dokaz:
> >
> > Naj bosta $y_1$ in $y_2$ rešitvi enačbe. Potem velja:
> > $a(x)y_1' + b(x)y_1 = c(x)$
> > $a(x)y_2' + b(x)y_2 = c(x)$
> > 
> > Definirajmo $z = y_1 - y_2$. Odvod $z$ je $z' = y_1' - y_2'$
> > Vstavimo $z$ in $z'$ v levo stran enačbe:
> > $a(x)z' + b(x)z = a(x)(y_1' - y_2') + b(x)(y_1 - y_2)$
> > $= a(x)y_1' - a(x)y_2' + b(x)y_1 - b(x)y_2$
> > $= (a(x)y_1' + b(x)y_1) - (a(x)y_2' + b(x)y_2)$
> > 
> > Ker sta $y_1$ in $y_2$ rešitvi enačbe, lahko zamenjamo izraza v oklepajih s $c(x)$:
> > $= c(x) - c(x)$
> > $= 0$


>**Izrek:** Naj bo $y_P$ (imenovana partikularna rešitev) rešitev nehomogene diferencialne enačbe $a(x)y' + b(x)y = c(x)$. Potem se poljubna rešitev $y_r$ te diferencialne enačbe izrazi v obliki $y_r = y_P + y_H$, kjer je $y_H$ neka rešitev pripadajoče homogene diferencialne enačbe $a(x)y' + b(x)y = 0$.
> 
> >[!|dokaz]- Dokaz:
> > **Pokažimo, da je vsota $y_P + y_H$ rešitev nehomogene enačbe, če je $y_H$ rešitev homogene.**
> >     Ker je $y_P$ partikularna rešitev nehomogene enačbe, velja:
> >     $a(x)y_P' + b(x)y_P = c(x)$
> >     Ker je $y_H$ rešitev homogene enačbe, velja:
> >     $a(x)y_H' + b(x)y_H = 0$
> >     Seštejemo ti dve enačbi:
> >     $(a(x)y_P' + b(x)y_P) + (a(x)y_H' + b(x)y_H) = c(x) + 0$
> >     $a(x)(y_P' + y_H') + b(x)(y_P + y_H) = c(x)$
> >     $a(x)(y_P + y_H)' + b(x)(y_P + y_H) = c(x)$
> >     To pomeni, da je $y_P + y_H$ res rešitev nehomogene enačbe.
> > 
> > **Pokažimo, da lahko vsako rešitev $y_r$ nehomogene enačbe zapišemo kot $y_P + y_H$.**
> >     Naj bo $y_r$ poljubna rešitev nehomogene enačbe, torej:
> >     $a(x)y_r' + b(x)y_r = c(x)$
> >     Ker je $y_P$ partikularna rešitev nehomogene enačbe, velja:
> >     $a(x)y_P' + b(x)y_P = c(x)$
> >     Odštejemo enačbo za $y_P$ od enačbe za $y_r$:
> >     $(a(x)y_r' + b(x)y_r) - (a(x)y_P' + b(x)y_P) = c(x) - c(x)$
> >     $a(x)(y_r' - y_P') + b(x)(y_r - y_P) = 0$
> >     $a(x)(y_r - y_P)' + b(x)(y_r - y_P) = 0$
> >     To pomeni, da je razlika $y_r - y_P$ rešitev homogene enačbe. Označimo to razliko z $y_H = y_r - y_P$. Potem lahko pišemo $y_r = y_P + y_H$.


## Dif enačbe prve stopnje

Splošno rešitev oz. družino funkcij lahko geometrijsko predstavimo kot vektorsko polje kjer puščice kažejo smer odvoda oz. smer poteka funkcije.

Lahko narišemo tudi izolipse kjer imajo potencialne funkcije enake koeficiente.

### Homogene enačbe


**Reševanje homogene linearne diferencialne enačbe:**
Homogena enačba je oblike $a(x)y' + b(x)y = 0$
To je enačba z ločljivima spremenljivkama. Prepišemo jo lahko kot:

$$\frac{y'}{y} = -\frac{b(x)}{a(x)}$$


$$\int \frac{dy}{y} = -\int \frac{b(x)}{a(x)} dx$$
$$\ln|y| = -\int \frac{b(x)}{a(x)} dx + \ln|A|$$

Torej je splošna rešitev homogene LDE:

$$y = Ae^{-\int \frac{b(x)}{a(x)} dx}$$



**Reševanje nehomogene LDE:**
Uporabimo metodo variacije konstante. Konstanto $A$ v splošni rešitvi homogene enačbe nadomestimo z neznano funkcijo $Z(x)$.
Partikularno rešitev $y_P$ iščemo v obliki:

$$y_P = Z(x)e^{-\int \frac{b(x)}{a(x)} dx}$$

Označimo $y_H^0 = e^{-\int \frac{b(x)}{a(x)} dx}$. Torej je $y_P = Z(x)y_H^0$.

Potrebujemo odvod $y_P'$:

$$y_P' = Z'y_H^0 + Z(y_H^0)'$$

Vemo, da je $(y_H^0)' = y_H^0 \left(-\frac{b(x)}{a(x)}\right)$.

Vstavimo to v nehomogeno enačbo 

$$a(x)y_P' + b(x)y_P = c(x)$$
$$a(x)\left(Z'y_H^0 + Z y_H^0 \left(-\frac{b(x)}{a(x)}\right)\right) + b(x)Z y_H^0 = c(x)$$
$$a(x)Z'y_H^0 - b(x)Z y_H^0 + b(x)Z y_H^0 = c(x)$$
$$a(x)Z'y_H^0 = c(x)$$

Od tod izrazimo $Z'$:

$$Z' = \frac{c(x)}{a(x)y_H^0} = \frac{c(x)}{a(x)} e^{\int \frac{b(x)}{a(x)} dx}$$

Integriramo $Z'$ za določitev $Z(x)$:

$$Z(x) = \int \frac{c(x)}{a(x)} e^{\int \frac{b(x)}{a(x)} dx} dx$$

Partikularna rešitev je torej $y_P = Z(x)y_H^0$.
Splošna rešitev nehomogene enačbe je $Y_S = y_P + y_H$.

To so pravzaprav vse rešitve v okolici točke $(x_0, y_0)$, za katero je $a(x_0) \neq 0$ in $y(x_0) = y_0$.
(Opomba: Če je $c(x) = 0$, potem $Z' = 0$, kar pomeni $Z(x) = A$ (konstanta). V tem primeru $y_P = A y_H^0$, kar je splošna rešitev homogene enačbe, torej $y_P$ postane $y_H$.)

Seveda, tukaj je kratek povzetek postopka za integracijski faktor:

**Integracijski Faktor (Integracijski dejavnik)**

To je funkcija ($\mu$), s katero pomnožimo diferencialno enačbo, da jo spremenimo v obliko, ki jo je mogoče neposredno integrirati (npr. v eksaktno enačbo ali v enačbo, kjer je leva stran odvod produkta).



**Postopek z integracijskim faktorjem**

Standardna oblika: $y' + P(x)y = Q(x)$

**Postopek:**

1.  **Določi $P(x)$** iz standardne oblike enačbe.
2.  **Izračunaj integracijski faktor $\mu(x)$:**
    $\mu(x) = e^{\int P(x)dx}$
3.  **Pomnoži** celotno standardno enačbo z $\mu(x)$:
    $\mu(x)\frac{dy}{dx} + \mu(x)P(x)y = \mu(x)Q(x)$
4.  **Prepoznaj levo stran** kot odvod produkta:
    $\frac{d}{dx}(\mu(x)y) = \mu(x)Q(x)$
5.  **Integriraj** obe strani glede na $x$:
    $\mu(x)y = \int \mu(x)Q(x)dx + C$
6.  **Izrazi $y$** in dobiš splošno rešitev.

$$\mu(x) = e^{\int P(x)dx}$$


**Bernoullijeva diferencialna enačba**

Bernoullijeva diferencialna enačba je oblike:
$$y' + ay = by^n$$
kjer je $a$ konstanta ($a \in \mathbb{R}$) in $b$ nenična funkcija (od $x$).

Če je $n = 0$ ali $n = 1$, je enačba linearna diferencialna enačba (LDE):
*   Za $n=0$: $y' + ay = b$
*   Za $n=1$: $y' + ay = by \Rightarrow y' + (a-b)y = 0$

Zato predpostavimo, da je $n \neq 0$ in $n \neq 1$.
Vpeljemo novo funkcijo $z$ s substitucijo:
$$z = y^{1-n}$$
Izračunamo odvod $z'$:
$$z' = (1-n)y^{-n}y'$$
Od tod izrazimo $y'$:
$$y' = \frac{y^n}{1-n}z'$$
Vstavimo $y'$ v Bernoullijevo enačbo:
$$\frac{y^n}{1-n}z' + ay = by^n$$
Delimo celotno enačbo z $y^n$ (predpostavljamo $y \neq 0$):
$$\frac{1}{1-n}z' + a \frac{y}{y^n} = b$$
$$\frac{1}{1-n}z' + a y^{1-n} = b$$
Sedaj nadomestimo $y^{1-n}$ z $z$:
$$\frac{1}{1-n}z' + az = b$$
To je linearna diferencialna enačba prvega reda za funkcijo $z(x)$, ki jo znamo rešiti.


**Prvi integral diferencialne enačbe**

Funkcija $u: D \subset \mathbb{R}^2 \rightarrow \mathbb{R}$ je prvi integral diferencialne enačbe $y'=f(x,y)$, če za vsako rešitev $y(x)$, katere graf leži v $D$, velja $u(x,y(x))=C$, kjer je $C \in \mathbb{R}$ konstanta.

Konstanta $C$ je določena z izbiro specifične rešitve in je konstantna vzdolž grafa te rešitve. Grafi rešitev diferencialne enačbe so pravzaprav nivojnice funkcije $u(x,y)$.

*Generalno imamo problem $F(x,y,...,y^{(n)})$ in iščemo izraz $I(x,y,...,y^{(n-1)})$ tako da velja da ko je $F = 0$ je $I = C$.
Ker imamo prej nek višji odvod, kjer je dif enačba enaka 0, imamo sedaj brez tega odvoda neko konstanto.*
*Iščemo izraz $I$ ki ima lastnost da pri $F = 0$ velja $I = C$, proces iskanja tega izraza ponavadi vključuje manipuliranje originalnega izraza $F$ dokler ne dobimo nekaj kar je očitno odvod neke funkcije $I' = F$.*

**Zgled:**
Imamo dif enačbo $f(x,y,y') = 0$, hočemo $g(x,y)=C$ oz. $g'(x,y) = 0$.

Za diferencialno enačbo $y'=-\frac{x}{y}$:
$$y'=-\frac{x}{y} \implies yy'=-x$$
Integriramo obe strani glede na $x$:
$$\int yy'dx = \int -xdx$$
$$\frac{y^2}{2} = -\frac{x^2}{2} + \tilde{C}$$
$$x^2+y^2 = C$$
Tako je $g(x,y)=x^2+y^2$ prvi integral te diferencialne enačbe. Nivojnice so krožnice s središčem v izhodišču.

**Opomba:** Če je $(x_0,y_0) \in D$ in $u_y(x_0,y_0) \neq 0$, potem lahko enačbo $u(x,y)=C$ v okolici točke $(x_0,y_0)$ eksplicitno rešimo na $y$ (po izreku o implicitni funkciji). Na ta način dobimo enoparametrično družino rešitev v okolici točke $(x_0,y_0)$.

**Obrazložitev:**
Če je $y=\phi(x,C)$ enoparametrična družina rešitev, lahko iz te zveze izrazimo konstanto $C$ kot funkcijo $x$ in $y$, tj. $C=u(x,y)$, če je $\frac{\partial \phi}{\partial C}(x,C) \neq 0$. Funkcija $u(x,y)$ je tedaj prvi integral.

**Pozor:**
Prvi integral ni enolično določen. Če je $u(x,y)$ prvi integral, je tudi $g(u(x,y))$ prvi integral za kakršnokoli zvezno in zvezno odvedljivo funkcijo $g$, ki ima neničelni odvod.

---

**Problem ortogonalnih trajektorij**

Za dano vektorsko polje $(P(x,y), Q(x,y))$ v $\mathbb{R}^2$ iščemo družino krivulj v $\mathbb{R}^2$, ki so v vsaki točki pravokotne na to vektorsko polje.

Naj bo $t \mapsto (x(t), y(t))$ ena od teh krivulj. Njen tangentni vektor je $(\dot{x}, \dot{y})$. Ker mora biti pravokoten na vektorsko polje $(P,Q)$, mora veljati njun skalarni produkt je enak nič:
$$P(x,y)\dot{x} + Q(x,y)\dot{y} = 0$$
To enačbo lahko zapišemo v diferencialni obliki, če upoštevamo $\frac{dx}{dt}=\dot{x}$ in $\frac{dy}{dt}=\dot{y}$ in pomnnožimo z $dt$
$$P(x,y)dx + Q(x,y)dy = 0$$
To je diferencialna 1-forma, katere rešitve (krivulje) so pravokotne na vektorsko polje $(P,Q)$.

Če je krivulja podana kot graf funkcije $y(x)$, potem je $dy = y'dx$. 
$$P(x,y)dx + Q(x,y)y'dx = 0$$
Predpostavimo $dx \neq 0$ (krivulja ni navpična - $x$ se spreminja) in delimo z $dx$:
$$P(x,y) + Q(x,y)y' = 0$$
Od tod sledi diferencialna enačba za družino krivulj:
$$y' = -\frac{P(x,y)}{Q(x,y)}$$

**Določanje ortogonalnih trajektorij za dano DE:**

Če je družina krivulj podana z diferencialno enačbo $y'=f(x,y)$, lahko to enačbo prepišemo v obliko 1-forme:
$$f(x,y)dx - dy = 0$$
Torej, identificiramo $P_{0}(x,y) = f(x,y)$ in $Q_{0}(x,y) = -1$.

Družina krivulj, ki so ortogonalne na to prvotno družino, je določena z diferencialno enačbo, kjer zamenjamo vlogi $P$ in $Q$ ter spremenimo predznak enega od členov (tj. $Q_{0}dx - P_{0}dy = 0$):
$$-1 dx - f(x,y) dy = 0$$
Od tod dobimo diferencialno enačbo za ortogonalne trajektorije:
$$y' = -\frac{1}{f(x,y)}$$

Če je vektorsko polje $(P,Q)$ potencialno, kar pomeni, da obstaja funkcija $u(x,y)$ taka, da je $(P,Q) = \nabla u = \left(\frac{\partial u}{\partial x}, \frac{\partial u}{\partial y}\right)$, potem je diferencialna enačba $Pdx+Qdy=0$ **eksaktna**. Njene rešitve so določene z $u(x,y)=C$. Nivojnice funkcije $u$ so vedno pravokotne na gradient $\nabla u$.

>[!|hide]- Eksaktne enačbe
>
> **Kaj je totalni diferencial?**
> Za funkcijo $u(x,y)$ je njen totalni diferencial $du = \frac{\partial u}{\partial x} dx + \frac{\partial u}{\partial y} dy$. Pove nam, kako se $u$ spremeni ob majhnih spremembah $x$ in $y$.
> 
> **Kaj pomeni, da je diferencialna enačba eksaktna?**
> Diferencialna enačba oblike $P(x,y) dx + Q(x,y) dy = 0$ je **eksaktna**, če je izraz $P(x,y) dx + Q(x,y) dy$ totalni diferencial neke skalarne funkcije $u(x,y)$. Torej, če obstaja $u(x,y)$ taka, da:
> $$P(x,y) = \frac{\partial u}{\partial x} \quad \text{in} \quad Q(x,y) = \frac{\partial u}{\partial y}$$
> **Rešitve** eksaktne diferencialne enačbe so dane z $u(x,y) = C$, kjer je $C$ konstanta (to so nivojnice funkcije $u$).
> 
> **Kako preverimo eksaktnost? (Pogoj za eksaktnost)**
> Diferencialna enačba $P(x,y) dx + Q(x,y) dy = 0$ je eksaktna, če in samo če velja:
> $$ \frac{\partial P}{\partial y} = \frac{\partial Q}{\partial x} $$
> Ta pogoj izhaja iz Clairautovega izreka o enakosti mešanih parcialnih odvodov ($\frac{\partial^2 u}{\partial y \partial x} = \frac{\partial^2 u}{\partial x \partial y}$), ob predpostavki zveznosti odvodov.
> 
> **Kako rešimo eksaktno DE?**
> 1.  Potrdimo eksaktnost s preverjanjem pogoja $\frac{\partial P}{\partial y} = \frac{\partial Q}{\partial x}$.
> 2.  Poiščemo funkcijo $u(x,y)$ tako, da integriramo $P$ po $x$ (dodamo funkcijo $h(y)$ namesto konstante) in odvajamo ta rezultat po $y$, nato pa ga izenačimo s $Q$, da določimo $h(y)$. Lahko tudi integriramo $Q$ po $y$ in nadaljujemo podobno.
> 3.  Splošna rešitev je $u(x,y) = C$.


Za iskanje ortogonalnih trajektorij družine krivulj, določene z $y'=f(x,y)$, moramo rešiti diferencialno enačbo $y'_{ort} = -\frac{1}{f(x,y)}$.

*Če imamo*

$$\color{light}y' = -\frac{P(x,y)}{Q(x,y)}$$

*je ortogonalno po definiciji koeficientov*

$$\color{light}y' = \frac{Q(x,y)}{P(x,y)}$$

$$ \color{light}k\perp -\frac{1}{k}$$

## Reševanje NDE višjih redov


1.  Če se najvišji odvod, $y^{(k)}$, pojavi in funkcija $y$ sama ne, potem vpeljemo novo neznano funkcijo $z=y^{(k)}$ (ali splošneje, če manjka odvisna spremenljivka $y$).
    
    **Zgled:**
    $y^{(4)} - y^{(3)} = 1$
    Vpeljemo $z = y^{(3)}$. Potem je $z' = y^{(4)}$.
    Enačba postane: $z' - z = 1$.
    To je linearna DE 1. reda. Rešimo jo:
    $\frac{dz}{dx} = 1 + z \implies \frac{dz}{1+z} = dx$
    $\int \frac{dz}{1+z} = \int dx \implies \ln|1+z| = x + C_0$
    $1+z = e^{x+C_0} \implies z = Ce^x - 1$ (kjer je $C = e^{C_0}$).

    Nadaljujemo z integracijo:
    $y^{(3)} = Ae^x - 1$ (uporabljena je konstanta $A$ namesto $C$)
    $y'' = Ae^x - x + B$
    $y' = Ae^x - \frac{x^2}{2} + Bx + C$
    $y = Ae^x - \frac{x^3}{6} + \frac{Bx^2}{2} + Cx + D$
	$$ $$

2.  Če se v enačbi ne pojavi neodvisna spremenljivka $x$, potem vpeljemo novo neznano funkcijo $z(y)=y'$, pri čemer je $y$ nova neodvisna spremenljivka.
   
    Tedaj je:
    $y'' = \frac{dy'}{dx} = \frac{dz}{dx} = \frac{dz}{dy} \frac{dy}{dx} = z \frac{dz}{dy}$
    $y''' = \frac{d}{dx} \left( z \frac{dz}{dy} \right) = \frac{d}{dy} \left( z \frac{dz}{dy} \right) \frac{dy}{dx} = \left( \left( \frac{dz}{dy} \right)^2 + z \frac{d^2z}{dy^2} \right) z$

    **Zgled:**
    $2yy'' - y'^{\,2} = 0$
    Vpeljemo $y' = z$. Tedaj je $y'' = z \frac{dz}{dy}$.
    Enačba postane: $2y \left( z \frac{dz}{dy} \right) - z^2 = 0$
    $z \left( 2y \frac{dz}{dy} - z \right) = 0$
    To ima dve možnosti:
    1) $z=0 \implies y'=0 \implies y=C$ (konstanta).
    2) $2y \frac{dz}{dy} - z = 0$
       $2y \frac{dz}{dy} = z$
       To je DE z ločljivimi spremenljivkami: $\frac{2dz}{z} = \frac{dy}{y}$
       Integriramo: $2 \ln|z| = \ln|y| + C_1$
       $\ln(z^2) = \ln(Ky)$ (kjer je $C_1 = \ln K$)
       $z^2 = Ky$
       Vstavimo nazaj $z=y'$: $(y')^2 = Ky$.
       To je ločljiva DE: $\frac{dy}{dx} = \pm \sqrt{Ky}$
       $\frac{dy}{\sqrt{y}} = \pm \sqrt{K} dx$
       Integriramo: $2\sqrt{y} = \pm \sqrt{K} x + C_2$
       $4y = (\pm \sqrt{K} x + C_2)^2$
       $y = (Ax+B)^2$ (kjer sta $A, B$ poljubni konstanti)


---

## LDE VIŠJEGA REDA

**Definicija:** Linearna diferencialna enačba (LDE) $n$-tega reda ima obliko:
$r_n(x)y^{(n)} + r_{n-1}(x)y^{(n-1)} + \dots + r_1(x)y' + r_0(x)y = g(x)$
kjer so $r_0, \dots, r_n: J \to \mathbb{R}$ funkcije na intervalu $J$.
*   Če je $g(x) = 0$, rečemo, da je enačba **homogena**.
*   Če so $r_0, \dots, r_n$ konstante, pa rečemo, da ima enačba **konstantne koeficiente**.

**Trditev (Princip superpozicije):**
1) Naj bosta $y_1$ in $y_2$ rešitvi linearne homogene d.e. in $c_1, c_2 \in \mathbb{R}$. Potem je $c_1y_1 + c_2y_2$ rešitev dane homogene d.e.
   Torej linearne homogene d.e. ustvarjajo vektorski prostor rešitev.

2) Naj bo $y_p$ partikularna rešitev nehomogene LDE in $y_h$ rešitev pripadajoče homogene d.e. Potem je $y_h + y_p$ splošna rešitev dane nehomogene LDE.

3) Splošna rešitev nehomogene LDE je oblike $y = y_h + y_p$, kjer je $y_p$ partikularna rešitev LDE, $y_h$ pa splošna rešitev pridružene homogene d.e.

**Dokaz:** Kot za LDE 1. reda.

>[!|hide]- Primer
> Rešiti diferencialno enačbo:
> $x^2 y'' - 2y = 0$
> 
> **Postopek reševanja:**
> 
> 1.  **Uganemo eno rešitev homogene enačbe:**
>     Opazimo, da je $y_1 = x^2$ rešitev dane homogene diferencialne enačbe. Preverimo:
>     Če je $y_1 = x^2$, potem je $y_1' = 2x$ in $y_1'' = 2$.
>     Vstavimo v enačbo: $x^2(2) - 2(x^2) = 2x^2 - 2x^2 = 0$. Rešitev je pravilna.
> 
> 2.  **Uvedemo nastavek za splošno rešitev:**
>     Nastavek za splošno rešitev diferencialne enačbe je oblike $y = u(x) \cdot y_1(x)$. V našem primeru je to:
>     $y = x^2 u$
> 
> 3.  **Izračunamo odvode $y'$ in $y''$:**
>     Uporabimo pravilo za odvajanje produkta:
>     $y' = (x^2 u)' = 2xu + x^2 u'$
>     $y'' = (2xu + x^2 u')' = (2xu)' + (x^2 u')'$
>     $y'' = (2u + 2xu') + (2xu' + x^2 u'')$
>     $y'' = 2u + 4xu' + x^2 u''$
> 
> 4.  **Vstavimo $y$ in $y''$ v prvotno diferencialno enačbo:**
>     $x^2 (2u + 4xu' + x^2 u'') - 2(x^2 u) = 0$
>     Razširimo in poenostavimo:
>     $2x^2 u + 4x^3 u' + x^4 u'' - 2x^2 u = 0$
>     Členi z $u$ se pokrajšajo:
>     $4x^3 u' + x^4 u'' = 0$
> 
> 5.  **Znižanje reda enačbe:**
>     Opazimo, da se v novi enačbi ne pojavlja funkcija $u$, ampak le njeni odvodi $u'$ in $u''$. To nam omogoča znižanje reda diferencialne enačbe.
>     Uvedemo substitucijo $z = u'$, kar pomeni, da je $z' = u''$.
>     Vstavimo v enačbo:
>     $4x^3 z + x^4 z' = 0$
> 
> 6.  **Rešimo diferencialno enačbo za $z$:**
>     To je linearna diferencialna enačba prvega reda, ki jo lahko rešimo z ločitvijo spremenljivk ali z opazovanjem, da je leva stran odvod produkta.
>     Deli z $x^3$ (ob predpostavki $x \neq 0$):
>     $4z + xz' = 0$
>     Enačbo lahko prepišemo kot:
>     $x z' = -4z$
>     $\frac{dz}{z} = -4 \frac{dx}{x}$
>     Integriramo obe strani:
>     $\int \frac{dz}{z} = \int -4 \frac{dx}{x}$
>     $\ln|z| = -4 \ln|x| + \ln|C|$
>     $\ln|z| = \ln|x^{-4}| + \ln|C|$
>     $\ln|z| = \ln|Cx^{-4}|$
>     $z = Cx^{-4}$
>     (Alternativno, iz $4x^3 z + x^4 z' = 0$ lahko opazimo, da je leva stran ravno odvod produkta $(x^4 z)'$. Torej $(x^4 z)' = 0$. Integracija da $x^4 z = C$, od koder sledi $z = Cx^{-4}$.)
> 
> 7.  **Izračunamo $u$ iz $z$:**
>     Ker je $z = u'$, imamo:
>     $u' = Cx^{-4}$
>     Integriramo $u'$ za določitev $u$:
>     $u = \int Cx^{-4} dx$
>     $u = C \frac{x^{-3}}{-3} + E$
>     $u = D x^{-3} + E$, kjer je $D = -\frac{C}{3}$ nova poljubna konstanta.
> 
> 8.  **Izračunamo splošno rešitev $y$:**
>     Vstavimo izračunani $u$ nazaj v nastavek $y = x^2 u$:
>     $y = x^2 (Dx^{-3} + E)$
>     $y = Dx^{-1} + Ex^2$
> 
> **Splošna rešitev homogene diferencialne enačbe $x^2 y'' - 2y = 0$ je:**
> $y = Dx^{-1} + Ex^2$



**Trditev:**
Funkcija $g(x)=e^{\lambda x}$ je rešitev homogene diferencialne enačbe s konstantnimi koeficienti
$$r_n y^{(n)} + r_{n-1} y^{(n-1)} + \dots + r_0 y = 0$$
natanko tedaj, kadar je $\lambda$ ničla karakterističnega polinoma
$$p(\lambda) = r_n \lambda^n + \dots + r_0.$$

**Dokaz:**
Izračunamo $k$-ti odvod funkcije $g(x)=e^{\lambda x}$:
$$g^{(k)}(x) = \lambda^k e^{\lambda x}$$
Če to vstavimo v diferencialno enačbo, dobimo:
$$r_n (\lambda^n e^{\lambda x}) + r_{n-1} (\lambda^{n-1} e^{\lambda x}) + \dots + r_0 (e^{\lambda x}) = 0$$
Izpostavimo $e^{\lambda x}$:
$$(r_n \lambda^n + r_{n-1} \lambda^{n-1} + \dots + r_0) e^{\lambda x} = 0$$
Ker je $e^{\lambda x} \neq 0$ za vse $x$, mora biti izraz v oklepaju enak nič:
$$r_n \lambda^n + r_{n-1} \lambda^{n-1} + \dots + r_0 = 0$$
To pa pomeni, da je $\lambda$ ničla karakterističnega polinoma $p(\lambda)$. Torej:
$$(r_n \lambda^n + \dots + r_0) e^{\lambda x} = 0 \iff \lambda \text{ je ničla karakt. polinoma.}$$

>[!|hide]- Primer
> **1) Diferencialna enačba:**
> $y'' + 2y' - 3y = 0$
> 
> **Karakteristična enačba:**
> $\lambda^2 + 2\lambda - 3 = 0$
> $(\lambda + 3)(\lambda - 1) = 0$
> 
> **Koreni karakteristične enačbe:**
> $\lambda_1 = -3$, $\lambda_2 = 1$ (različni realni koreni)
> 
> **Splošna rešitev:**
> $y(x) = ae^x + be^{-3x}$
> 
> ---
> 
> **2) Diferencialna enačba:**
> 1.  **Diferencialna enačba:** $y'' + 2y' + 2y = 0$
> 2.  **Karakteristična enačba:** $\lambda^2 + 2\lambda + 2 = 0$
> 3.  **Koreni karakteristične enačbe:** Z reševanjem kvadratne enačbe dobimo kompleksne konjugirane korene $\lambda_{1,2} = -1 \pm i$.
>     *   Te korene zapišemo v obliki $\lambda = \alpha \pm i\beta$, kjer je $\alpha = -1$ (realni del) in $\beta = 1$ (imaginarni del brez $i$).
> 4.  **Splošna realna rešitev:**
>     Ko ima karakteristična enačba kompleksne konjugirane korene oblike $\alpha \pm i\beta$, je splošna realna rešitev diferencialne enačbe dana z formulo:
>     $y(x) = e^{\alpha x} (A \cos(\beta x) + B \sin(\beta x))$
>     kjer sta $A$ in $B$ poljubni realni konstanti. Ta formula je izpeljana z uporabo Eulerjeve formule ($e^{ix} = \cos x + i\sin x$) iz kompleksnih eksponentnih rešitev.
> 5.  **Rešitev za naš primer:**
>     Z vstavljanjem $\alpha = -1$ in $\beta = 1$ v zgornjo formulo dobimo:
>     $y(x) = e^{-1 \cdot x} (A \cos(1 \cdot x) + B \sin(1 \cdot x))$
>     $y(x) = A e^{-x}\cos x + B e^{-x}\sin x$
> 
> Skratka, če dobite kompleksne korene $\alpha \pm i\beta$, preprosto vstavite $\alpha$ in $\beta$ v formulo $e^{\alpha x} (A \cos(\beta x) + B \sin(\beta x))$, da dobite realno obliko splošne rešitve.
> 
> 
> **3) Diferencialna enačba:**
> $y'' + 2y' + y = 0$
> 
> **Karakteristična enačba:**
> $\lambda^2 + 2\lambda + 1 = 0$
> $(\lambda + 1)^2 = 0$
> 
> **Koreni karakteristične enačbe:**
> $\lambda = -1$ (dvakratni realni koren)
> 
> **Splošna rešitev (za ponovljene korene):**
> $y(x) = A e^{-x} + B x e^{-x}$

***


>**Trditev.** Dana je nehomogena l.d.e. s konst. koeficienti:
$$r_n y^{(n)} + r_{n-1} y^{(n-1)} + \dots + r_0 y = S.$$
Če je $S$ ena od spodnjih oblik in $\lambda$ ničla karakt. polinoma, potem jo iščemo z nastavkom:

| $S(x)$ | $\lambda$ | $h(x)$ |
|---|---|---|
| $P_m(x)$ | $0$ | $x^k Q_m(x)$ |
| $e^{\alpha x}$ | $\alpha$ | $x^k e^{\alpha x}$ |
| $\sin \beta x$ | $i\beta$ | $x^k (d_1 \sin \beta x + d_2 \cos \beta x)$ |
| $\cos \beta x$ | $-i\beta$ | $x^k (\dots)$ |
| $P_m(x)e^{\alpha x}$ | $\alpha$ | $x^k Q_m(x) e^{\alpha x}$ |

Če lambda ni ničla karakterističnega polinoma potem je $k=0$, ker $k$ predstavlja kratnost vrednosti $\lambda$, kot ničla polinoma torej če imamo ničlo $\lambda = 1$ kot posledica $(\lambda -1)^2$ potem je $k=2$ za to $\lambda$.

**Kjer je**
$P_m$ polinom stopnje $m$
$Q_m, R_m$ splošna polinoma stopnje $m$

>[!|hide]- **Primer.** $y'' - 3y' + 2y = x+1$
> 
> Karakteristična enačba: $\lambda^2 - 3\lambda + 2 = 0$. Rešitvi sta $\lambda_1 = 2, \lambda_2 = 1$.
> Homogena rešitev: $y_H = Ae^x + Be^{2x}$.
> 
> Nastavek za partikularno rešitev:
> $y_P(x) = cx+B$
> $y_P'(x) = c$
> $y_P''(x) = 0$
> 
> Vstavimo v diferencialno enačbo:
> $0 - 3c + 2(cx+B) = x+1$
> $0 - 3c + 2cx + 2B = x+1$
> $2cx + (2B-3c) = 1x + 1$
> 
> Izenačimo koeficiente:
> $2c = 1 \implies c = \frac{1}{2}$
> $2B - 3c = 1 \implies 2B - 3(\frac{1}{2}) = 1 \implies 2B - \frac{3}{2} = 1 \implies 2B = \frac{5}{2} \implies B = \frac{5}{4}$
> 
> Splošna rešitev: $y_S(x) = \frac{1}{2}x + \frac{5}{4} + Ae^x + Be^{2x}$.

**SISTEMI DIFERENCIALNIH ENAČB**

**Obstoj in enoličnost**
Rešujemo Cauchyjevo nalogo:
*   $y_1, ..., y_n$ so neznane funkcije realne spremenljivke $x$.
*   $f_1, ..., f_n: \mathbb{R}^{n+1} \to \mathbb{R}$ so dane zvezne funkcije.

Potem sistem $n$ diferencialnih enačb 1. reda je:
$y'_1 = f_1(x, y_1, ..., y_n)$
$y'_2 = f_2(x, y_1, ..., y_n)$
...
$y'_n = f_n(x, y_1, ..., y_n)$

**V vektorski obliki**
$\vec{y}' = \vec{f}(x, \vec{y}) \quad (*)$

**Začetni pogoj**
$\vec{y}(x_0) = \vec{y}_0$

**Cauchyjeva naloga**
Iščemo rešitev sistema $(*)$, ki ustreza začetnemu pogoju.

**Eksistenčni in enoličnostni izrek**
Ta izrek pravi, da pri določenih pogojih rešitev Cauchyjeve naloge natanko ena.

**Eksistenčni izrek**
Naj bo $\vec{f}$ zvezno diferencialna na $[a,b] \times \mathbb{R}^n$. Potem za vsak $\vec{y}_0 \in \mathbb{R}^n$ obstaja natanko ena zvezno odvedljiva preslikava $\vec{y}: [a,b] \to \mathbb{R}^n$, ki reši Cauchyjevo nalogo:
$\vec{y}' = \vec{f}(x, \vec{y})$
$\vec{y}(x_0) = \vec{y}_0$

**SISTEMI LINEARNIH DIFERENCIALNIH ENAČB 1. REDA**

**Definicija.**
Naj bo $A: [a, b] \to \mathbb{R}^{n,n}$ matrična funkcija in
$\vec{b}: [a, b] \to \mathbb{R}^n$ vektorska funkcija.

Sistem
$\vec{y}' = A(x)\vec{y} + \vec{b}(x)$
imenujemo sistem n-linearnih diferencialnih enačb prvega reda.

**Opomba.**
1) Če sta $A$ in $\vec{b}$ zvezno diferenciabilni, potem so izpolnjeni pogoji eksistenčnega izreka.
2) Sistem lahko razpišemo po komponentah:
$y_1' = a_{11}(x)y_1 + a_{12}(x)y_2 + \dots + a_{1n}(x)y_n + b_1(x)$
...
$y_n' = a_{n1}(x)y_1 + a_{n2}(x)y_2 + \dots + a_{nn}(x)y_n + b_n(x)$

${y}_p + \vec{y}_H$, kjer je $\vec{y}_H$ rešitev pripadajočega homogenega sistema $\vec{y}' = A(x)\vec{y}$.

Množica rešitev homogenega sistema je vektorski podprostor v $(C[a,b])^n$ razsežnosti $n$.

**Dokaz**

Dokaz je podoben kot za linearne diferencialne enačbe.
Naj bo $\vec{y}$ poljubna rešitev nehomogenega sistema $\vec{y}'=A(x)\vec{y} + \vec{b}$. Potem za razliko $\vec{y}-\vec{y}_p$ velja:
$$ (\vec{y} - \vec{y}_p)' = \vec{y}' - \vec{y}_p' = (A(x)\vec{y} + \vec{b}) - (A(x)\vec{y}_p + \vec{b}) = A(x)(\vec{y}-\vec{y}_p) $$
To pomeni, da $\vec{y}-\vec{y}_p$ reši homogeni sistem.

Če sta $\vec{y}_{H_1}$ in $\vec{y}_{H_2}$ rešitvi homogenega sistema, je tudi njuna linearna kombinacija $\alpha \vec{y}_{H_1} + \beta \vec{y}_{H_2}$ rešitev homogenega sistema. Torej je množica rešitev homogenega sistema vektorski podprostor.

Po eksistenčnem izreku za vsak standardni bazni vektor $\vec{e}_i = (0, \dots, 1, \dots, 0)$ obstaja rešitev $\vec{y}_i$ Cauchyjeve naloge:
$$ \vec{y}_i' = A(x)\vec{y}_i, \quad \vec{y}_i(a) = \vec{e}_i $$

Trdimo, da so $\vec{y}_i$ linearno neodvisne rešitve v $(C[a,b])^n$.
Če to ne bi bilo res, bi obstajala netrivialna linearna kombinacija (ne vsi $\lambda_j$ enaki 0), za katero velja:
$$ \lambda_1 \vec{y}_1(x) + \dots + \lambda_n \vec{y}_n(x) \equiv 0 $$
Če vstavimo $x=a$, dobimo $\lambda_1 \vec{y}_1(a) + \dots + \lambda_n \vec{y}_n(a) = \lambda_1 \vec{e}_1 + \dots + \lambda_n \vec{e}_n = \vec{0}$, kar implicira $\lambda_1 = \dots = \lambda_n=0$, saj so vektorji $\vec{e}_i$ linearno neodvisni. To je protislovje.

Torej je vektorski prostor rešitev razsežnosti vsaj $n$.

Pokažimo še, da te rešitve razpenjajo celoten prostor rešitev. Izberimo poljubno rešitev $\vec{y}$ sistema $\vec{y}' = A(x)\vec{y}$. Njena začetna vrednost $\vec{y}(a)$ je nek vektor v $\mathbb{R}^n$, ki ga lahko razvijemo po bazi $\{\vec{e}_i\}$:
$$ \vec{y}(a) = \lambda_1 \vec{e}_1 + \dots + \lambda_n \vec{e}_n $$
Ker je $\vec{y}_i(a) = \vec{e}_i$, lahko to zapišemo kot:
$$ \vec{y}(a) = \lambda_1 \vec{y}_1(a) + \dots + \lambda_n \vec{y}_n(a) = \left(\sum_{j=1}^n \lambda_j \vec{y}_j\right)(a) $$
Potem sta $\vec{y}(x)$ in $\sum_{j=1}^n \lambda_j \vec{y}_j(x)$ rešitvi iste Cauchyjeve naloge (imata enako diferencialno enačbo in enak začetni pogoj).
Ker je po eksistenčnem in enoličnostnem izreku rešitev ena sama, sta funkciji enaki:
$$ \vec{y}(x) = \sum_{j=1}^n \lambda_j \vec{y}_j(x) $$
To pomeni, da je vsaka rešitev linearna kombinacija rešitev $\vec{y}_j$, zato tvorijo bazo prostora rešitev, ki je dimenzije $n$.


Če so $\vec{y}_1, \dots, \vec{y}_n$ linearno neodvisne rešitve sistema $\vec{y}' = A(x)\vec{y}$, jih lahko zapišemo v matrično funkcijo $Y(x) = [\vec{y}_1(x) \dots \vec{y}_n(x)]$, ki se imenuje **matrika Wronskega**.

Vsako drugo rešitev dobimo v obliki $Y(x)\vec{c}$, kjer je $\vec{c}$ vektor konstant. Velja $\det(Y(x)) \neq 0$.

$W(x) := \det(Y(x))$ je **determinanta Wronskega**.

Velja: $W'(x) = \text{sled}(A(x)) \cdot W(x)$.

**Liouvillova formula**
Odsod sledi Liouvillova formula:
$$ W(x) = c \cdot e^{\int_a^x \text{sled}(A(t))dt} $$

**Nehomogen sistem**
Rešujemo sistem $\vec{y}' = A(x)\vec{y} + \vec{b}(x) \quad (*)$ z metodo **variacije konstant**:

Naj bo $Y(x)$ matrika Wronskega, za katero velja $Y'(x) = A(x)Y(x)$.
Rešitev enačbe $(*)$ iščemo v obliki $\vec{y}(x) = Y(x)\vec{c}(x)$.

Odvod rešitve je:
$$ \vec{y}'(x) = Y'(x)\vec{c}(x) + Y(x)\vec{c}'(x) = A(x)Y(x)\vec{c}(x) + Y(x)\vec{c}'(x) $$
Ker je $Y(x)\vec{c}(x) = \vec{y}(x)$, lahko zgornji izraz zapišemo kot:
$$ \vec{y}'(x) = A(x)\vec{y}(x) + Y(x)\vec{c}'(x) $$
Ko to enačimo z desno stranjo originalne enačbe $(*)$, ki je $A(x)\vec{y}(x) + \vec{b}(x)$, sledi:
$$ Y(x)\vec{c}'(x) = \vec{b}(x) $$
$$ \vec{c}'(x) = Y^{-1}(x)\vec{b}(x) $$
Oziroma, ko zgornji izraz integriramo, dobimo splošno rešitev nehomogenega sistema:
$$ \vec{y}(x) = Y(x) \cdot \int_a^x Y^{-1}(t)\vec{b}(t)dt + Y(x)\vec{c} $$
Torej, za reševanje linearnih sistemov je potrebno znati rešiti homogeni sistem, nato pa znamo rešiti tudi nehomogenega.


**Reševanje homogenega sistema s konstantnimi koeficienti**

Rešujemo sistem: $\vec{y}' = A\vec{y}$, kjer je $A$ $n \times n$ matrika. Začetni pogoj je $\vec{y}(0) = \vec{y}_0$.

Rešitev sistema je: $\vec{y}(x) = e^{xA} \vec{y}_0 = \sum_{n=0}^{\infty} \frac{1}{n!} (xA)^n \vec{y}_0$.

Preverimo, ali je to res rešitev. Odvajamo po $x$:
$\vec{y}'(x) = \left( \sum_{n=0}^{\infty} \frac{x^n}{n!} A^n \vec{y}_0 \right)' = \sum_{n=1}^{\infty} \frac{n x^{n-1}}{n!} A^n \vec{y}_0 = \sum_{n=1}^{\infty} \frac{x^{n-1}}{(n-1)!} A^n \vec{y}_0$
(Opomba: vsaka vrsta mora konvergirati, mi smo to kar predpostavili).

Izpostavimo matriko $A$:
$\vec{y}'(x) = A \left( \sum_{n=1}^{\infty} \frac{x^{n-1}}{(n-1)!} A^{n-1} \vec{y}_0 \right)$
Uvedemo nov indeks $k=n-1$:
$\vec{y}'(x) = A \left( \sum_{k=0}^{\infty} \frac{x^k}{k!} A^k \vec{y}_0 \right) = A \left( e^{xA} \vec{y}_0 \right) = A\vec{y}$.

$Y(x) = e^{xA}$ je matrika Wronskega in $Y(0) = I$.
Matriko $e^{xA}$ izračunamo z uporabo Jordanove forme.

**Izračun matrike $e^{xA}$**

Naj bo $A = PJP^{-1}$, kjer je $J$ Jordanova kanonična forma matrike $A$ in $P$ prehodna matrika.
$e^{xA} = \sum_{n=0}^{\infty} \frac{x^n}{n!} A^n = \sum_{n=0}^{\infty} \frac{x^n}{n!} (P J^n P^{-1}) = P \left( \sum_{n=0}^{\infty} \frac{x^n}{n!} J^n \right) P^{-1} = P e^{xJ} P^{-1}$.

Dovolj je izračunati $e^{xJ}$ za Jordanovo kletko. Jordanova kletka velikosti $m \times m$ je oblike:
$J = \begin{bmatrix} \lambda & 1 & & 0 \\ & \lambda & \ddots & \\ & & \ddots & 1 \\ 0 & & & \lambda \end{bmatrix} = \lambda I + \begin{bmatrix} 0 & 1 & & 0 \\ & 0 & \ddots & \\ & & \ddots & 1 \\ 0 & & & 0 \end{bmatrix} = \lambda I + N$, kjer je $N$ nilpotentna matrika, za katero velja $N^m=0$.

Ker matriki $\lambda I$ in $N$ komutirata $(\lambda I \cdot N = N \cdot \lambda I)$, velja:
$e^{xJ} = e^{x(\lambda I + N)} = e^{x\lambda I} \cdot e^{xN}$.

Izračunamo vsak faktor posebej:
$e^{x\lambda I} = \sum_{n=0}^{\infty} \frac{(x\lambda)^n}{n!} I^n = \left(\sum_{n=0}^{\infty} \frac{(x\lambda)^n}{n!}\right) I = e^{x\lambda} I$.

$e^{xN} = \sum_{n=0}^{\infty} \frac{x^n}{n!} N^n = \sum_{n=0}^{m-1} \frac{x^n}{n!} N^n = I + xN + \frac{x^2}{2!}N^2 + \dots + \frac{x^{m-1}}{(m-1)!}N^{m-1}$.
To je matrika:
$e^{xN} = \begin{bmatrix} 1 & x & \frac{x^2}{2!} & \cdots & \frac{x^{m-1}}{(m-1)!} \\ 0 & 1 & x & \cdots & \frac{x^{m-2}}{(m-2)!} \\ \vdots & & \ddots & \ddots & \vdots \\ 0 & & & 1 & x \\ 0 & 0 & \cdots & 0 & 1 \end{bmatrix}$.

**Splošna rešitev**

Ker je splošna rešitev sistema $\vec{y}' = A\vec{y}$ enaka $\vec{y}(x) = e^{xA} \vec{c}$, kjer je $\vec{c}$ poljuben vektor konstant, dobimo:
$\vec{y}(x) = P e^{xJ} P^{-1} \vec{c}$.
Če definiramo nov vektor konstant $\vec{d} = P^{-1}\vec{c}$, je rešitev:
$\vec{y}(x) = P e^{xJ} \vec{d}$.

>[!|hide]- Primeri
> **Zgled (1)**
> 
> Sistem diferencialnih enačb:
> $$
> \begin{aligned}
> y' &= y + 4z \\
> z' &= y + z
> \end{aligned}
> $$
> V matrični obliki:
> $$
> A = \begin{bmatrix} 1 & 4 \\ 1 & 1 \end{bmatrix}
> $$
> Iskanje lastnih vrednosti:
> $$
> \det(A - \lambda I) = \begin{vmatrix} 1-\lambda & 4 \\ 1 & 1-\lambda \end{vmatrix} = (1-\lambda)^2 - 4 = \lambda^2 - 2\lambda - 3 = (\lambda-3)(\lambda+1)
> $$
> Lastne vrednosti so $\lambda_1 = -1$ in $\lambda_2 = 3$.
> 
> Lastni vektorji:
> Za $\lambda_1 = -1$:
> $$
> \begin{bmatrix} 2 & 4 \\ 1 & 2 \end{bmatrix} \vec{n}_1 = \vec{0} \implies \vec{n}_1 = \begin{bmatrix} -2 \\ 1 \end{bmatrix}
> $$
> Za $\lambda_2 = 3$:
> $$
> \begin{bmatrix} -2 & 4 \\ 1 & -2 \end{bmatrix} \vec{n}_2 = \vec{0} \implies \vec{n}_2 = \begin{bmatrix} 2 \\ 1 \end{bmatrix}
> $$
> Matrika prehodov $P$ in splošna rešitev homogenega sistema $\vec{y} = P e^{Jx} \vec{d}$:
> $$
> P = \begin{bmatrix} -2 & 2 \\ 1 & 1 \end{bmatrix}
> $$
> $$
> \begin{bmatrix} y \\ z \end{bmatrix} = \begin{bmatrix} -2 & 2 \\ 1 & 1 \end{bmatrix} \begin{bmatrix} e^{-x} & 0 \\ 0 & e^{3x} \end{bmatrix} \begin{bmatrix} c \\ d \end{bmatrix} = c e^{-x} \begin{bmatrix} -2 \\ 1 \end{bmatrix} + d e^{3x} \begin{bmatrix} 2 \\ 1 \end{bmatrix}
> $$
> *13.11.12*
> 
> **Opomba:** če je $A$ mogoče diagonalizirati, $A = PDP^{-1}$.
> Splošna rešitev je oblike:
> $$
> \vec{y} = P \begin{bmatrix} e^{\lambda_1 x} & & \\ & \ddots & \\ & & e^{\lambda_n x} \end{bmatrix} \vec{d} = d_1 e^{\lambda_1 x} \vec{n}_1 + \dots + d_n e^{\lambda_n x} \vec{n}_n
> $$
> 
> **Zgled (2)**
> Rešujemo nehomogen sistem:
> $$
> \begin{aligned}
> y' &= y + 4z + 3 \\
> z' &= y + z + 3e^{2x}
> \end{aligned}
> $$
> Matrika $P$ in njen inverz $P^{-1}$. Uporabimo formulo $\begin{bmatrix} a & b \\ c & d \end{bmatrix}^{-1} = \frac{1}{ad-bc} \begin{bmatrix} d & -b \\ -c & a \end{bmatrix}$.
> $$
> P = \begin{bmatrix} -2 & 2 \\ 1 & 1 \end{bmatrix}, \quad P^{-1} = \frac{1}{-4} \begin{bmatrix} 1 & -2 \\ -1 & -2 \end{bmatrix} = \frac{1}{4} \begin{bmatrix} -1 & 2 \\ 1 & 2 \end{bmatrix}
> $$
> Vemo: rešitev $\vec{y}' = A\vec{y} + \vec{b}(x)$ je oblike $\vec{y}(x) = Y(x) \int_{x_0}^x Y^{-1}(t) \vec{b}(t) dt + Y(x)\vec{c}$, kjer je $Y$ fundamentalna matrika.
> $$
> Y = P e^{Jx} P^{-1} = \begin{bmatrix} -2 & 2 \\ 1 & 1 \end{bmatrix} \begin{bmatrix} e^{-x} & 0 \\ 0 & e^{3x} \end{bmatrix} \frac{1}{4} \begin{bmatrix} -1 & 2 \\ 1 & 2 \end{bmatrix} = \frac{1}{4} \begin{bmatrix} -2e^{-x} & 2e^{3x} \\ e^{-x} & e^{3x} \end{bmatrix} \begin{bmatrix} -1 & 2 \\ 1 & 2 \end{bmatrix}
> $$
> $$
> = \frac{1}{4} \begin{bmatrix} 2e^{-x} + 2e^{3x} & -4e^{-x} + 4e^{3x} \\ -e^{-x} + e^{3x} & 2e^{-x} + 2e^{3x} \end{bmatrix}
> $$
> Inverzna fundamentalna matrika $Y^{-1}(x) = P e^{-Jx} P^{-1}$ (ker to deluje tudi za $n \ge 2$):
> $$
> Y^{-1}(x) = \frac{1}{4} \begin{bmatrix} 2e^{x} + 2e^{-3x} & -4e^{x} + 4e^{-3x} \\ -e^{x} + e^{-3x} & 2e^{x} + 2e^{-3x} \end{bmatrix}
> $$
> Produkt $Y^{-1}(x) \vec{b}(x)$, kjer je $\vec{b}(x) = \begin{bmatrix} 3 \\ 3e^{2x} \end{bmatrix}$:
> $$
> Y^{-1}(x)\vec{b}(x) = \frac{3}{4} \begin{bmatrix} (2e^x + 2e^{-3x}) - 4e^{x+2x} + 4e^{-3x+2x} \\ (-e^x + e^{-3x}) + 2e^{x+2x} + 2e^{-3x+2x} \end{bmatrix} = \frac{3}{4} \begin{bmatrix} 2e^x + 2e^{-3x} - 4e^{3x} + 4e^{-x} \\ -e^x + e^{-3x} + 2e^{3x} + 2e^{-x} \end{bmatrix}
> $$
> Integriranje:
> $$
> \int Y^{-1}(x)\vec{b}(x) dx = \frac{3}{4} \begin{bmatrix} 2e^x - \frac{2}{3}e^{-3x} - \frac{4}{3}e^{3x} - 4e^{-x} \\ -e^x - \frac{1}{3}e^{-3x} + \frac{2}{3}e^{3x} - 2e^{-x} \end{bmatrix}
> $$
> Partikularna rešitev $\vec{y}_p = Y(x) \int Y^{-1}(x) \vec{b}(x) dx$:
> $$
> \vec{y}_p = \frac{1}{4} \begin{bmatrix} 2e^{-x} + 2e^{3x} & -4e^{-x} + 4e^{3x} \\ -e^{-x} + e^{3x} & 2e^{-x} + 2e^{3x} \end{bmatrix} \frac{3}{4} \begin{bmatrix} \dots \end{bmatrix}
> $$
> Po dolgem računu dobimo:
> $$
> = \frac{3}{16} \begin{pmatrix} -\frac{16}{3} \\ -\frac{16}{3} \end{pmatrix} - \frac{16 \cdot 4 \cdot e^{2x}}{3} \begin{pmatrix} \dots \end{pmatrix} = \begin{bmatrix} 1 - 4e^{2x} \\ -1 - e^{2x} \end{bmatrix}
> $$
> **Splošna rešitev:**
> $$
> \vec{y} = \begin{bmatrix} 1 - 4e^{2x} \\ -1 - e^{2x} \end{bmatrix} + \frac{1}{4} \begin{bmatrix} 2e^{-x} + 2e^{3x} & -4e^{-x} + 4e^{3x} \\ -e^{-x} + e^{3x} & 2e^{-x} + 2e^{3x} \end{bmatrix} \begin{bmatrix} c \\ d \end{bmatrix}
> $$
> 
> ---
> **Hitreje:**
> Uganemo, da je partikularna rešitev podobne oblike kot $\vec{b}(x)$ in vstavimo nastavek:
> $$
> \begin{aligned}
> y &= A + Be^{2x} \\
> z &= C + De^{2x}
> \end{aligned}
> \quad \text{in odločimo } A, B, C, D \in \mathbb{R}.
> $$
> **Z vstavljanjem:**
> $$
> \begin{aligned}
> y' &= 2Be^{2x} \\
> z' &= 2De^{2x}
> \end{aligned}
> $$
> Vstavimo v sistem:
> $$
> \begin{aligned}
> 2Be^{2x} &= (A + Be^{2x}) + 4(C + De^{2x}) + 3 \\
> 2De^{2x} &= (A + Be^{2x}) + (C + De^{2x}) + 3e^{2x}
> \end{aligned}
> $$
> Primerjava koeficientov pri $e^{2x}$ in konstantah:
> $$
> \begin{cases}
> 2B = B + 4D \\
> 0 = A + 4C + 3
> \end{cases}
> \implies
> \begin{cases}
> B = 4D \\
> A + 4C + 3 = 0
> \end{cases}
> $$
> $$
> \begin{cases}
> 2D = B + D + 3 \\
> 0 = A + C
> \end{cases}
> \implies
> \begin{cases}
> D = B + 3 \\
> A = -C
> \end{cases}
> $$
> Reševanje sistema enačb:
> $D = (4D) + 3 \implies -3D = 3 \implies D = -1$.
> $B = 4D = 4(-1) = -4$.
> $A = -C$ vstavimo v $A + 4C + 3 = 0 \implies -C + 4C + 3 = 0 \implies 3C = -3 \implies C = -1$.
> $A = -(-1) = 1$.
> 
> Rešitev: $A=1, B=-4, C=-1, D=-1$.
> Partikularna rešitev je:
> $$
> \begin{aligned}
> y &= 1 - 4e^{2x} \\
> z &= -1 - e^{2x}
> \end{aligned}
> $$



>[!|]- Več nalog
> 
> Okay, let's solve some more non-homogeneous systems of differential equations. We'll continue using the method of undetermined coefficients where applicable.
> 
> ---
> 
> ### V. Sistemi diferencialnih enačb
> 
> #### B. Nehomogeni sistemi s konstantnimi koeficienti (Novi Primerni)
> 
> **Naloga 15 (nadaljevanje):** Določi splošno rešitev naslednjih nehomogenih sistemov diferencialnih enačb. Uporabi metodo nedoločenih koeficientov (nastavka) ali variacijo konstant, kot je primerno.
> 
> ---
> 
> **c) Sistem:**
> $y_1' = 2y_1 - y_2 + e^t$
> $y_2' = 3y_1 - 2y_2$
> 
> This system is $\mathbf{y}' = A\mathbf{y} + \mathbf{f}(t)$, where $A = \begin{pmatrix} 2 & -1 \\ 3 & -2 \end{pmatrix}$ and $\mathbf{f}(t) = \begin{pmatrix} e^t \\ 0 \end{pmatrix}$.
> 
> 1.  **Homogeneous Solution ($\mathbf{y}_h$):**
>     *   **Eigenvalues of A:**
>         $\det(A - \lambda I) = \det \begin{pmatrix} 2-\lambda & -1 \\ 3 & -2-\lambda \end{pmatrix} = (2-\lambda)(-2-\lambda) - (-1)(3) = -(4 - \lambda^2) + 3 = \lambda^2 - 4 + 3 = \lambda^2 - 1 = 0$
>         $\lambda^2 = 1 \implies \lambda = \pm 1$.
>         The eigenvalues are $\lambda_1 = 1$ and $\lambda_2 = -1$.
> 
>     *   **Eigenvectors:**
>         *   For $\lambda_1 = 1$:
>             $(A - I)\mathbf{v}_1 = \begin{pmatrix} 1 & -1 \\ 3 & -3 \end{pmatrix} \begin{pmatrix} v_{11} \\ v_{12} \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \end{pmatrix}$
>             From the first equation, $v_{11} - v_{12} = 0$, so $v_{11} = v_{12}$.
>             Choosing $v_{11} = 1$, we get $v_{12} = 1$. Thus, $\mathbf{v}_1 = \begin{pmatrix} 1 \\ 1 \end{pmatrix}$.
> 
>         *   For $\lambda_2 = -1$:
>             $(A - (-1)I)\mathbf{v}_2 = \begin{pmatrix} 3 & -1 \\ 3 & -1 \end{pmatrix} \begin{pmatrix} v_{21} \\ v_{22} \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \end{pmatrix}$
>             From the first equation, $3v_{21} - v_{22} = 0$, so $v_{22} = 3v_{21}$.
>             Choosing $v_{21} = 1$, we get $v_{22} = 3$. Thus, $\mathbf{v}_2 = \begin{pmatrix} 1 \\ 3 \end{pmatrix}$.
> 
>     *   **Homogeneous Solution:**
>         $$ \mathbf{y}_h(t) = c_1 e^{t} \begin{pmatrix} 1 \\ 1 \end{pmatrix} + c_2 e^{-t} \begin{pmatrix} 1 \\ 3 \end{pmatrix} $$
> 
> 2.  **Particular Solution ($\mathbf{y}_p$) using Undetermined Coefficients:**
>     Since $\mathbf{f}(t) = \begin{pmatrix} 1 \\ 0 \end{pmatrix} e^t$ and $t=1$ is an eigenvalue (meaning resonance occurs), we must assume a particular solution of the form $\mathbf{y}_p(t) = (\mathbf{a}t + \mathbf{b}) e^t$.
>     Then $\mathbf{y}_p'(t) = (\mathbf{a} + \mathbf{a}t + \mathbf{b}) e^t$.
>     Substitute into the non-homogeneous equation $\mathbf{y}_p' = A\mathbf{y}_p + \mathbf{f}(t)$:
>     $(\mathbf{a} + \mathbf{a}t + \mathbf{b})e^t = A(\mathbf{a}t + \mathbf{b})e^t + \begin{pmatrix} 1 \\ 0 \end{pmatrix} e^t$
>     Dividing by $e^t$:
>     $\mathbf{a} + \mathbf{a}t + \mathbf{b} = A(\mathbf{a}t + \mathbf{b}) + \begin{pmatrix} 1 \\ 0 \end{pmatrix}$
> 
>     Equating coefficients of $t$:
>     $\mathbf{a} = A\mathbf{a} \implies (A - I)\mathbf{a} = \mathbf{0}$.
>     This means $\mathbf{a}$ must be an eigenvector for $\lambda=1$. So, $\mathbf{a} = k \begin{pmatrix} 1 \\ 1 \end{pmatrix}$ for some constant $k$.
> 
>     Equating constant terms:
>     $\mathbf{a} + \mathbf{b} = A\mathbf{b} + \begin{pmatrix} 1 \\ 0 \end{pmatrix} \implies (A - I)\mathbf{b} = \mathbf{a} - \begin{pmatrix} 1 \\ 0 \end{pmatrix}$.
>     $\begin{pmatrix} 1 & -1 \\ 3 & -3 \end{pmatrix} \begin{pmatrix} b_1 \\ b_2 \end{pmatrix} = k \begin{pmatrix} 1 \\ 1 \end{pmatrix} - \begin{pmatrix} 1 \\ 0 \end{pmatrix} = \begin{pmatrix} k-1 \\ k \end{pmatrix}$.
>     For this system to have a solution, the right-hand side must be consistent. The rows of $(A-I)$ are linearly dependent (second row is 3 times the first). So, the equations must be consistent:
>     $3(k-1) = k$
>     $3k - 3 = k$
>     $2k = 3 \implies k = 3/2$.
>     So, $\mathbf{a} = \begin{pmatrix} 3/2 \\ 3/2 \end{pmatrix}$.
> 
>     Now, substitute $k=3/2$ back into the equation for $\mathbf{b}$:
>     $b_1 - b_2 = k-1 = 3/2 - 1 = 1/2$.
>     We can choose $b_2 = 0$ (as the system gives one equation for two variables, we can pick one freely).
>     Then $b_1 = 1/2$.
>     So, $\mathbf{b} = \begin{pmatrix} 1/2 \\ 0 \end{pmatrix}$.
> 
>     The particular solution is $\mathbf{y}_p(t) = \left( \begin{pmatrix} 3/2 \\ 3/2 \end{pmatrix}t + \begin{pmatrix} 1/2 \\ 0 \end{pmatrix} \right) e^t = \begin{pmatrix} (3/2)t + 1/2 \\ (3/2)t \end{pmatrix} e^t$.
> 
> 3.  **General Solution:**
>     The general solution is $\mathbf{y}(t) = \mathbf{y}_h(t) + \mathbf{y}_p(t)$.
>     $$ \mathbf{y}(t) = c_1 e^{t} \begin{pmatrix} 1 \\ 1 \end{pmatrix} + c_2 e^{-t} \begin{pmatrix} 1 \\ 3 \end{pmatrix} + \begin{pmatrix} \frac{3}{2}t + \frac{1}{2} \\ \frac{3}{2}t \end{pmatrix} e^t $$
>     In component form:
>     $$ \begin{aligned} y_1(t) &= c_1 e^{t} + c_2 e^{-t} + \left( \frac{3}{2}t + \frac{1}{2} \right) e^t \\ y_2(t) &= c_1 e^{t} + 3c_2 e^{-t} + \frac{3}{2}t e^t \end{aligned} $$
> 
> ---
> 
> **d) Sistem:**
> $y_1' = y_2 + \sin(t)$
> $y_2' = -2y_1 + 3y_2$
> 
> This system is $\mathbf{y}' = A\mathbf{y} + \mathbf{f}(t)$, where $A = \begin{pmatrix} 0 & 1 \\ -2 & 3 \end{pmatrix}$ and $\mathbf{f}(t) = \begin{pmatrix} \sin(t) \\ 0 \end{pmatrix}$.
> 
> 4.  **Homogeneous Solution ($\mathbf{y}_h$):**
>     *   **Eigenvalues of A:**
>         $\det(A - \lambda I) = \det \begin{pmatrix} -\lambda & 1 \\ -2 & 3-\lambda \end{pmatrix} = -\lambda(3-\lambda) - (1)(-2) = -3\lambda + \lambda^2 + 2 = \lambda^2 - 3\lambda + 2 = 0$
>         $(\lambda - 1)(\lambda - 2) = 0$.
>         The eigenvalues are $\lambda_1 = 1$ and $\lambda_2 = 2$.
> 
>     *   **Eigenvectors:**
>         *   For $\lambda_1 = 1$:
>             $(A - I)\mathbf{v}_1 = \begin{pmatrix} -1 & 1 \\ -2 & 2 \end{pmatrix} \begin{pmatrix} v_{11} \\ v_{12} \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \end{pmatrix}$
>             From the first equation, $-v_{11} + v_{12} = 0$, so $v_{11} = v_{12}$.
>             Choosing $v_{11} = 1$, we get $v_{12} = 1$. Thus, $\mathbf{v}_1 = \begin{pmatrix} 1 \\ 1 \end{pmatrix}$.
> 
>         *   For $\lambda_2 = 2$:
>             $(A - 2I)\mathbf{v}_2 = \begin{pmatrix} -2 & 1 \\ -2 & 1 \end{pmatrix} \begin{pmatrix} v_{21} \\ v_{22} \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \end{pmatrix}$
>             From the first equation, $-2v_{21} + v_{22} = 0$, so $v_{22} = 2v_{21}$.
>             Choosing $v_{21} = 1$, we get $v_{22} = 2$. Thus, $\mathbf{v}_2 = \begin{pmatrix} 1 \\ 2 \end{pmatrix}$.
> 
>     *   **Homogeneous Solution:**
>         $$ \mathbf{y}_h(t) = c_1 e^{t} \begin{pmatrix} 1 \\ 1 \end{pmatrix} + c_2 e^{2t} \begin{pmatrix} 1 \\ 2 \end{pmatrix} $$
> 
> 5.  **Particular Solution ($\mathbf{y}_p$) using Undetermined Coefficients:**
>     Since $\mathbf{f}(t)$ involves $\sin(t)$ and $\pm i$ are not eigenvalues, we assume a particular solution of the form $\mathbf{y}_p(t) = \mathbf{a}\cos(t) + \mathbf{b}\sin(t)$.
>     Then $\mathbf{y}_p'(t) = -\mathbf{a}\sin(t) + \mathbf{b}\cos(t)$.
>     Substitute into the non-homogeneous equation $\mathbf{y}_p' = A\mathbf{y}_p + \mathbf{f}(t)$:
>     $-\mathbf{a}\sin(t) + \mathbf{b}\cos(t) = A(\mathbf{a}\cos(t) + \mathbf{b}\sin(t)) + \begin{pmatrix} \sin(t) \\ 0 \end{pmatrix}$
> 
>     Equating coefficients of $\cos(t)$:
>     $\mathbf{b} = A\mathbf{a} \implies \begin{pmatrix} b_1 \\ b_2 \end{pmatrix} = \begin{pmatrix} 0 & 1 \\ -2 & 3 \end{pmatrix} \begin{pmatrix} a_1 \\ a_2 \end{pmatrix} = \begin{pmatrix} a_2 \\ -2a_1 + 3a_2 \end{pmatrix}$
>     So, $b_1 = a_2$ (Eq. 1) and $b_2 = -2a_1 + 3a_2$ (Eq. 2).
> 
>     Equating coefficients of $\sin(t)$:
>     $-\mathbf{a} = A\mathbf{b} + \begin{pmatrix} 1 \\ 0 \end{pmatrix} \implies \begin{pmatrix} -a_1 \\ -a_2 \end{pmatrix} = \begin{pmatrix} 0 & 1 \\ -2 & 3 \end{pmatrix} \begin{pmatrix} b_1 \\ b_2 \end{pmatrix} + \begin{pmatrix} 1 \\ 0 \end{pmatrix} = \begin{pmatrix} b_2 + 1 \\ -2b_1 + 3b_2 \end{pmatrix}$
>     So, $-a_1 = b_2 + 1$ (Eq. 3) and $-a_2 = -2b_1 + 3b_2$ (Eq. 4).
> 
>     Now we solve the system of linear equations for $a_1, a_2, b_1, b_2$:
>     From (Eq. 1), substitute $b_1 = a_2$ into (Eq. 4):
>     $-a_2 = -2a_2 + 3b_2 \implies a_2 = 3b_2 \implies b_2 = \frac{1}{3}a_2$.
> 
>     Substitute $b_2 = \frac{1}{3}a_2$ into (Eq. 3):
>     $-a_1 = \frac{1}{3}a_2 + 1$.
> 
>     Substitute $b_2 = \frac{1}{3}a_2$ into (Eq. 2):
>     $\frac{1}{3}a_2 = -2a_1 + 3a_2 \implies -2a_1 = \frac{1}{3}a_2 - 3a_2 = -\frac{8}{3}a_2 \implies a_1 = \frac{4}{3}a_2$.
> 
>     Now we have a system for $a_1$ and $a_2$:
>     $-a_1 = \frac{1}{3}a_2 + 1$
>     $a_1 = \frac{4}{3}a_2$
>     Substitute the second equation into the first:
>     $-\frac{4}{3}a_2 = \frac{1}{3}a_2 + 1 \implies -\frac{5}{3}a_2 = 1 \implies a_2 = -\frac{3}{5}$.
>     Then $a_1 = \frac{4}{3}(-\frac{3}{5}) = -\frac{4}{5}$.
> 
>     Now find $b_1$ and $b_2$:
>     $b_1 = a_2 = -\frac{3}{5}$.
>     $b_2 = \frac{1}{3}a_2 = \frac{1}{3}(-\frac{3}{5}) = -\frac{1}{5}$.
> 
>     So, $\mathbf{a} = \begin{pmatrix} -4/5 \\ -3/5 \end{pmatrix}$ and $\mathbf{b} = \begin{pmatrix} -3/5 \\ -1/5 \end{pmatrix}$.
>     The particular solution is $\mathbf{y}_p(t) = \begin{pmatrix} -4/5 \\ -3/5 \end{pmatrix}\cos(t) + \begin{pmatrix} -3/5 \\ -1/5 \end{pmatrix}\sin(t)$.
> 
> 6.  **General Solution:**
>     The general solution is $\mathbf{y}(t) = \mathbf{y}_h(t) + \mathbf{y}_p(t)$.
>     $$ \mathbf{y}(t) = c_1 e^{t} \begin{pmatrix} 1 \\ 1 \end{pmatrix} + c_2 e^{2t} \begin{pmatrix} 1 \\ 2 \end{pmatrix} + \begin{pmatrix} -\frac{4}{5} \\ -\frac{3}{5} \end{pmatrix}\cos(t) + \begin{pmatrix} -\frac{3}{5} \\ -\frac{1}{5} \end{pmatrix}\sin(t) $$
>     In component form:
>     $$ \begin{aligned} y_1(t) &= c_1 e^{t} + c_2 e^{2t} - \frac{4}{5}\cos(t) - \frac{3}{5}\sin(t) \\ y_2(t) &= c_1 e^{t} + 2c_2 e^{2t} - \frac{3}{5}\cos(t) - \frac{1}{5}\sin(t) \end{aligned} $$
> 
> ---
> 
> **e) Sistem:**
> $y_1' = y_1 + 2y_2 + t$
> $y_2' = -y_1 + 4y_2 + 2$
> 
> This system is $\mathbf{y}' = A\mathbf{y} + \mathbf{f}(t)$, where $A = \begin{pmatrix} 1 & 2 \\ -1 & 4 \end{pmatrix}$ and $\mathbf{f}(t) = \begin{pmatrix} t \\ 2 \end{pmatrix}$.
> 
> 7.  **Homogeneous Solution ($\mathbf{y}_h$):**
>     *   **Eigenvalues of A:**
>         $\det(A - \lambda I) = \det \begin{pmatrix} 1-\lambda & 2 \\ -1 & 4-\lambda \end{pmatrix} = (1-\lambda)(4-\lambda) - (2)(-1) = 4 - 5\lambda + \lambda^2 + 2 = \lambda^2 - 5\lambda + 6 = 0$
>         $(\lambda - 2)(\lambda - 3) = 0$.
>         The eigenvalues are $\lambda_1 = 2$ and $\lambda_2 = 3$.
> 
>     *   **Eigenvectors:**
>         *   For $\lambda_1 = 2$:
>             $(A - 2I)\mathbf{v}_1 = \begin{pmatrix} -1 & 2 \\ -1 & 2 \end{pmatrix} \begin{pmatrix} v_{11} \\ v_{12} \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \end{pmatrix}$
>             From the first equation, $-v_{11} + 2v_{12} = 0$, so $v_{11} = 2v_{12}$.
>             Choosing $v_{12} = 1$, we get $v_{11} = 2$. Thus, $\mathbf{v}_1 = \begin{pmatrix} 2 \\ 1 \end{pmatrix}$.
> 
>         *   For $\lambda_2 = 3$:
>             $(A - 3I)\mathbf{v}_2 = \begin{pmatrix} -2 & 2 \\ -1 & 1 \end{pmatrix} \begin{pmatrix} v_{21} \\ v_{22} \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \end{pmatrix}$
>             From the first equation, $-2v_{21} + 2v_{22} = 0$, so $v_{21} = v_{22}$.
>             Choosing $v_{21} = 1$, we get $v_{22} = 1$. Thus, $\mathbf{v}_2 = \begin{pmatrix} 1 \\ 1 \end{pmatrix}$.
> 
>     *   **Homogeneous Solution:**
>         $$ \mathbf{y}_h(t) = c_1 e^{2t} \begin{pmatrix} 2 \\ 1 \end{pmatrix} + c_2 e^{3t} \begin{pmatrix} 1 \\ 1 \end{pmatrix} $$
> 
> 8.  **Particular Solution ($\mathbf{y}_p$) using Undetermined Coefficients:**
>     Since $\mathbf{f}(t) = \begin{pmatrix} t \\ 2 \end{pmatrix}$ is a polynomial of degree 1 and $0$ is not an eigenvalue, we assume a particular solution of the form $\mathbf{y}_p(t) = \mathbf{a}t + \mathbf{b}$.
>     Then $\mathbf{y}_p'(t) = \mathbf{a}$.
>     Substitute into the non-homogeneous equation $\mathbf{y}_p' = A\mathbf{y}_p + \mathbf{f}(t)$:
>     $\mathbf{a} = A(\mathbf{a}t + \mathbf{b}) + \begin{pmatrix} t \\ 2 \end{pmatrix}$
>     $\mathbf{a} = A\mathbf{a}t + A\mathbf{b} + \begin{pmatrix} t \\ 2 \end{pmatrix}$
> 
>     Rearrange to group terms by $t$:
>     $\mathbf{0} = A\mathbf{a}t + A\mathbf{b} - \mathbf{a} + \begin{pmatrix} t \\ 2 \end{pmatrix}$
>     $\mathbf{0} = \left( A\mathbf{a} + \begin{pmatrix} 1 \\ 0 \end{pmatrix} \right) t + \left( A\mathbf{b} - \mathbf{a} + \begin{pmatrix} 0 \\ 2 \end{pmatrix} \right)$
> 
>     Equating coefficients of $t$ to $\mathbf{0}$:
>     $A\mathbf{a} + \begin{pmatrix} 1 \\ 0 \end{pmatrix} = \mathbf{0} \implies A\mathbf{a} = \begin{pmatrix} -1 \\ 0 \end{pmatrix}$
>     $\begin{pmatrix} 1 & 2 \\ -1 & 4 \end{pmatrix} \begin{pmatrix} a_1 \\ a_2 \end{pmatrix} = \begin{pmatrix} -1 \\ 0 \end{pmatrix}$
>     $a_1 + 2a_2 = -1$ (Eq. A)
>     $-a_1 + 4a_2 = 0$ (Eq. B)
>     From (Eq. B), $a_1 = 4a_2$. Substitute into (Eq. A):
>     $4a_2 + 2a_2 = -1 \implies 6a_2 = -1 \implies a_2 = -1/6$.
>     Then $a_1 = 4(-1/6) = -2/3$.
>     So, $\mathbf{a} = \begin{pmatrix} -2/3 \\ -1/6 \end{pmatrix}$.
> 
>     Equating constant terms to $\mathbf{0}$:
>     $A\mathbf{b} - \mathbf{a} + \begin{pmatrix} 0 \\ 2 \end{pmatrix} = \mathbf{0} \implies A\mathbf{b} = \mathbf{a} - \begin{pmatrix} 0 \\ 2 \end{pmatrix}$
>     $A\mathbf{b} = \begin{pmatrix} -2/3 \\ -1/6 \end{pmatrix} - \begin{pmatrix} 0 \\ 2 \end{pmatrix} = \begin{pmatrix} -2/3 \\ -13/6 \end{pmatrix}$
>     $\begin{pmatrix} 1 & 2 \\ -1 & 4 \end{pmatrix} \begin{pmatrix} b_1 \\ b_2 \end{pmatrix} = \begin{pmatrix} -2/3 \\ -13/6 \end{pmatrix}$
>     $b_1 + 2b_2 = -2/3$ (Eq. C)
>     $-b_1 + 4b_2 = -13/6$ (Eq. D)
>     Add (Eq. C) and (Eq. D):
>     $6b_2 = -2/3 - 13/6 = -4/6 - 13/6 = -17/6 \implies b_2 = -17/36$.
>     Substitute $b_2$ into (Eq. C):
>     $b_1 + 2(-17/36) = -2/3$
>     $b_1 - 17/18 = -2/3 = -12/18$
>     $b_1 = -12/18 + 17/18 = 5/18$.
>     So, $\mathbf{b} = \begin{pmatrix} 5/18 \\ -17/36 \end{pmatrix}$.
> 
>     The particular solution is $\mathbf{y}_p(t) = \begin{pmatrix} -2/3 \\ -1/6 \end{pmatrix}t + \begin{pmatrix} 5/18 \\ -17/36 \end{pmatrix}$.
> 
> 9.  **General Solution:**
>     The general solution is $\mathbf{y}(t) = \mathbf{y}_h(t) + \mathbf{y}_p(t)$.
>     $$ \mathbf{y}(t) = c_1 e^{2t} \begin{pmatrix} 2 \\ 1 \end{pmatrix} + c_2 e^{3t} \begin{pmatrix} 1 \\ 1 \end{pmatrix} + \begin{pmatrix} -\frac{2}{3} \\ -\frac{1}{6} \end{pmatrix}t + \begin{pmatrix} \frac{5}{18} \\ -\frac{17}{36} \end{pmatrix} $$
>     In component form:
>     $$ \begin{aligned} y_1(t) &= 2c_1 e^{2t} + c_2 e^{3t} - \frac{2}{3}t + \frac{5}{18} \\ y_2(t) &= c_1 e^{2t} + c_2 e^{3t} - \frac{1}{6}t - \frac{17}{36} \end{aligned} $$