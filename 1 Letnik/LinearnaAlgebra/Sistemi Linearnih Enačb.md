> Vsebuje
> Kaj je linerarna enačba, kaj je trivialna enačba kaj predstavlja in dokaz
> Sistem linearnih enačb
> 


## Sistemi linearnih enačb

### Linearna enačba
Linearna enačba v $n$ spremenljivkah je enačba oblike:
$$a_1x_1 + a_2x_2 + \dots + a_nx_n = b \quad (*)$$
kjer so $a_1, a_2, \dots, a_n, b$ dana realna števila, $x_1, x_2, \dots, x_n$ pa so spremenljivke. Vsaki $n$-terici realnih števil $a_{i}$, ki zadoščajo enačbi, pravimo rešitev enačbe.

Če je $a_1 = \dots = a_n = 0$, potem pravimo, da je enačba $(*)$ **trivialna**. 
Ločimo dva primera trivialne enačbe. Če je $b=0$, potem je njena množica rešitev enaka $\mathbb{R}^n$. Če je $b \neq 0$, potem je njena množica rešitev prazna.

Če je linearna enačba $(*)$ netrivialna, potem je njena množica rešitev hiperravnina v $\mathbb{R}^n$. Vsako hiperravnino v $\mathbb{R}^n$ lahko dobimo na ta način.

*Dokaz:* Če je enačba $(*)$ netrivialna, obstaja tak $i \in \{1, \dots, n\}$, da je $a_i \neq 0$. Torej jo lahko zapišemo v obliki:
$$a_1x_1 + \dots + a_i(x_i - \frac{b}{a_i}) + \dots + a_nx_n = 0 \quad (**)$$
Opazimo, da je vektor $\mathbf{n} := (a_1, \dots, a_i, \dots, a_n)$ neničeln, ker je $a_i \neq 0$. Če definiramo še $\mathbf{r} := (x_1, \dots, x_i, \dots, x_n)$ in $\mathbf{r}_0 := (0, \dots, \frac{b}{a_i}, \dots, 0)$, potem je enačba $(**)$ ravno enačba hiperravnine $\langle \mathbf{n}, \mathbf{r} - \mathbf{r}_0 \rangle = 0$.
Vzemimo sedaj poljubno hiperravnino v $\mathbb{R}^n$. Potem obstajata tak neničeln $\mathbf{n} = (a_1, \dots, a_n)$ in tak $\mathbf{r}_0 = (c_1, \dots, c_n)$ v $\mathbb{R}^n$, da je hiperravnina množica rešitev vektorske enačbe $\langle \mathbf{n}, \mathbf{r} - \mathbf{r}_0 \rangle = 0$. Če razpišemo, dobimo netrivialno linearno enačbo $a_1x_1 + \dots + a_nx_n = b$, kjer je $b = a_1c_1 + \dots + a_nc_n$.

### Uvod v sisteme linearnih enačb
Sistem $m$ linearnih enačb v $n$ spremenljivkah je sistem enačb oblike:
$$
\begin{align*}
a_{1,1}x_1 + \dots + a_{1,n}x_n &= b_1 \\
&\vdots \\
a_{m,1}x_1 + \dots + a_{m,n}x_n &= b_m
\end{align*} 
$$
kjer so $a_{i,j}$ in $b_k$ realna števila, $x_1, \dots, x_n$ pa so spremenljivke. 


Geometrijski pomen rešitev sistema
Če so vsi koeficienti in vse desne strani $m \times n$ sistema enaki nič, potem je njegova množica rešitev enaka $\mathbb{R}^n$. V vseh ostalih primerih je množica rešitev presek hiperravnin v $\mathbb{R}^n$. To vključuje tudi primer, ko je množica rešitev prazna, saj je prazna množica presek dveh vzporednih hiperravnin.

*Dokaz:* Množica rešitev sistema je presek množic rešitev posameznih enačb. Vemo že, da je množica rešitev vsake netrivialne enačbe hiperravnina. Če so torej vse enačbe v sistemu netrivialne, je njegova množica rešitev presek hiperravnin.


Oglejmo si še kako trivialne enačbe vplivajo na množici rešitev. Če ima ena od trivialnih enačb sistema prazno množico rešitev, potem ima tudi sistem prazno množico rešitev, torej trditev drži. Oglejmo si še nasprotni primer, ko imajo vse trivialne enačbe sistema za množico rešitev $\mathbb{R}^n$. Take trivialne enačbe lahko izpustimo, saj ne vplivajo na množico rešitev sistema. Torej trditev drži tudi v tem primeru.


Tudi množica rešitev $3 \times 2$ sistema je bodisi cela ravnina bodisi premica v ravnini bodisi točka v ravnini bodisi prazna množica.
Množica rešitev $2 \times 3$ sistema je bodisi cel prostor $\mathbb{R}^3$ bodisi ravnina v prostoru bodisi premica v prostoru bodisi prazna množica. Ne more pa biti množica rešitev $2 \times 3$ sistema točka v prostoru.

Algebraični pomen rešitev sistema
Sistem enačb:
$$
\begin{align*}
a_{1,1}x_1 + \dots + a_{1,n}x_n &= b_1 \\
&\vdots \\
a_{m,1}x_1 + \dots + a_{m,n}x_n &= b_m
\end{align*}
$$
lahko zapišemo kot:
$$(b_1, \dots, b_n) = (a_{1,1}x_1 + \dots + a_{1,n}x_n, \dots, a_{m,1}x_1 + \dots + a_{m,n}x_n)$$
$$ = x_1(a_{1,1}, \dots, a_{m,1}) + \dots + x_n(a_{1,n}, \dots, a_{m,n})$$
se pravi kot razvoj v linearno kombinacijo:
$$\mathbf{b} = x_1\mathbf{a}_1 + \dots + x_n\mathbf{a}_n$$
kjer $\mathbf{b} = (b_1, \dots, b_n)$ in $\mathbf{a}_1 = (a_{1,1}, \dots, a_{m,1}), \dots, \mathbf{a}_n = (a_{1,n}, \dots, a_{m,n})$. Vektorju $\mathbf{b}$ pravimo tudi vektor desnih strani sistema, vektorjem $\mathbf{a}_1, \dots, \mathbf{a}_n$ pa tudi stolpci sistema. Množica rešitev sistema nam da torej vse možne razvoje vektorja desnih strani po stolpcih sistema.

Klasifikacija sistemov linearnih enačb
Sisteme linearnih enačb lahko klasificiramo glede na velikost, rešljivost in obliko desnih strani.
Glede na velikost delimo sisteme na:
* **kvadratne** (število enačb je enako številu spremenljivk),
* **predoločene** (število enačb je večje od števila spremenljivk),
* **poddoločene** (število enačb je manjše od števila spremenljivk).

Glede na rešljivost delimo sisteme na:
* **nerešljive** (če je množica rešitev prazna)
* **enolično** rešljive (če ima množica rešitev en element)
* **neenolično** rešljive (če ima množica rešitev več kot en element)

Glede na obliko desnih strani delimo sisteme na:
* **homogene** (če so vse desne strani enake nič)
* **nehomogene** (če je vsaj ena desna stran različna od nič)

Če sta $x$ in $y$ dve rešitvi istega sistema, potem je za vsak realen $t$ tudi $(1-t)x+ty$ rešitev tega sistema. Vsak neenolično rešljiv sistem ima torej neskončno množico rešitev.


Pogosto (nikakor pa ne vedno) je kvadraten sistem enolično rešljiv, predoločen sistem nerešljiv in poddoločen sistem neenolično rešljiv.
Homogen sistem je vedno rešljiv. Ima namreč trivialno rešitev $(0, \dots, 0)$. Glavno vprašanje je, kdaj je neenolično rešljiv. Pokazali bomo, da to velja za vse poddoločene homogene sisteme.

**Gaussova metoda** nam pove, kako s pomočjo elementarnih vrstičnih transformacij prevedemo sistem v obliko iz katere se da odčitati rešitev. Ker se pri elementarnih vrstičnih transformacijah nič ne dogaja z spremenljivkami, ni potrebe, da jih pišemo. Zato najprej pretvorimo:
$$
\begin{bmatrix}
a_{1,1}x_1 + \dots + a_{1,n}x_n = b_1 \\
\vdots \\
a_{m,1}x_1 + \dots + a_{m,n}x_n = b_m
\end{bmatrix}
\to
\begin{bmatrix}
a_{1,1} & \dots & a_{1,n} & b_1 \\
\vdots & \ddots & \vdots & \vdots \\
a_{m,1} & \dots & a_{m,n} & b_m
\end{bmatrix}
$$
Temu zapisu pravimo razširjena matrika sistema.

Na razširjeni matriki napravimo naslednje zaporedje korakov:
* Poišči prvi stolpec, ki vsebuje kak neničeln element. Označimo z $j_1$ njegovo zaporedno številko. Velja torej $a_{i,j}=0$, za vse $(i,j)$ z $j < j_1$.
* Če je $a_{1,j_1}=0$ in $a_{r,j_1} \neq 0$, potem zamenjamo prvo in $r$-to vrstico. Torej lahko predpostavimo, da je $a_{1,j_1} \neq 0$.
* Prvo vrstico delimo z $a_{1,j_1}$. Torej lahko predpostavimo, da je $a_{1,j_1}=1$.
* Za vsak $i=2, \dots, m$ odštejemo od $i$-te vrstice z $a_{i,j_1}$ pomnoženo prvo vrstico. Torej lahko predpostavimo, da je $a_{2,j_1}=\dots=a_{m,j_1}=0$.

S temi koraki smo razširjeno matriko prevedli v obliko:
$$
\begin{bmatrix}
0 & \dots & 0 & 1 & a'_{1,j_1+1} & \dots & a'_{1,n} & b'_1 \\
0 & \dots & 0 & 0 & a'_{2,j_1+1} & \dots & a'_{2,n} & b'_2 \\
\vdots & \ddots & \vdots & \vdots & \vdots & \ddots & \vdots & \vdots \\
0 & \dots & 0 & 0 & a'_{m,j_1+1} & \dots & a'_{m,n} & b'_m
\end{bmatrix}
$$
Sedaj za hip pozabimo na prvo vrstico in ponovimo gornje zaporedje korakov na zadnjih $m-1$ vrsticah. Dobimo:
$$
\begin{bmatrix}
0 & \dots & 0 & 1 & a'_{1,j_1+1} & \dots & a'_{1,j_2-1} & a''_{1,j_2} & a''_{1,j_2+1} & \dots & a'_{1,n} & b'_1 \\
0 & \dots & 0 & 0 & a'_{2,j_1+1} & \dots & a'_{2,j_2-1} & a''_{2,j_2} & a''_{2,j_2+1} & \dots & a'_{2,n} & b'_2 \\
\vdots & \ddots & \vdots & \vdots & \vdots & \ddots & \vdots & \vdots & \vdots & \ddots & \vdots & \vdots \\
0 & \dots & 0 & 0 & a'_{m,j_1+1} & \dots & a'_{m,j_2-1} & a''_{m,j_2} & a''_{m,j_2+1} & \dots & a'_{m,n} & b'_m
\end{bmatrix}
$$
Sedaj za hip pozabimo na prvi dve vrstici in ponovimo gornje zaporedje korakov na preostalih $m-2$ vrsticah. Postopek ponavljamo, dokler gre (se pravi, dokler ne zmanjka neničelnih vrstic). Na koncu dobimo:

$$
\begin{bmatrix}
0 & \dots & 0 & 1 & \times & \dots & \times & \times & \dots & \times & \times \\
0 & \dots & 0 & 0 & 1 & \dots & \times & \times & \dots & \times & \times \\
0 & \dots & 0 & 0 & 0 & \dots & 1 & \times & \dots & \times & \times \\
\vdots & \ddots & \vdots & \vdots & \vdots & \ddots & \vdots & \vdots & \ddots & \vdots & \vdots \\
0 & \dots & 0 & 0 & 0 & \dots & 0 & 1 & \dots & \times & \times \\
\vdots & \ddots & \vdots & \vdots & \vdots & \ddots & \vdots & \vdots & \ddots & \vdots & \vdots \\
0 & \dots & 0 & 0 & 0 & \dots & 0 & 0 & \dots & 0 & 0
\end{bmatrix}
$$

Temu pravimo **vrstična stopničasta forma** sistema. Simbol $\times$ označuje, da je tam število, ki je lahko neničelno. Pod "stopniščem" so same ničle.
Če vrstična stopničasta forma vsebuje vrstico oblike $[0 \dots 0 \mid \times]$, kjer je element $\times$ neničeln, potem sistem ni rešljiv. Torej končamo.
Recimo, da ima vrstična stopničasta forma $k$ neničelnih vrstic. Recimo, da se začetne enke teh vrstic (=pivoti) nahajajo na mestih $(1,j_1), \dots, (k,j_k)$. Najprej z zadnjim pivotom "uničimo" vse elemente nad njim. (To pomeni, da od prvih $k-1$ vrstic odštejemo ustrezne večkratnike $k$-te vrstice, da se na mestih $(1,j_k), \dots, (k-1,j_k)$ pojavijo ničle.) Nato s predzadnjim pivotom uničimo vse elemente nad njim. Postopek ponavljamo, dokler ne pridemo do prvega pivota (nad katerim ne moremo nič uničiti). Dobimo:
$$

\begin{bmatrix}
0 & \dots & 0 & 1 & \times & \dots & \times & 0 & \dots & 0 & \times \\
0 & \dots & 0 & 0 & 1 & \dots & \times & 0 & \dots & 0 & \times \\
\vdots & \ddots & \vdots & \vdots & \vdots & \ddots & \vdots & \vdots & \ddots & \vdots & \vdots \\
0 & \dots & 0 & 0 & 0 & \dots & 1 & 0 & \dots & 0 & \times \\
\vdots & \ddots & \vdots & \vdots & \vdots & \ddots & \vdots & \vdots & \ddots & \vdots & \vdots \\
0 & \dots & 0 & 0 & 0 & \dots & 0 & 1 & \dots & 0 & \times \\
\vdots & \ddots & \vdots & \vdots & \vdots & \ddots & \vdots & \vdots & \ddots & \vdots & \vdots \\
0 & \dots & 0 & 0 & 0 & \dots & 0 & 0 & \dots & 0 & 0
\end{bmatrix}
$$

Temu pravimo reducirana vrstična stopničasta forma sistema. Sedaj spet pišemo spremenljivke. Iz dobljenih enačb izrazimo spremenljivke $x_{j_1}, \dots, x_{j_k}$ s pomočjo preostalih spremenljivk. To je iskana rešitev.

### Homogeni sistemi
Sistem linearnih enačb je homogen, če je oblike:
$$
\begin{align*}
a_{1,1}x_1 + \dots + a_{1,n}x_n &= 0 \\
&\vdots \\
a_{m,1}x_1 + \dots + a_{m,n}x_n &= 0
\end{align*} 
$$
Opazimo, da je $(0, \dots, 0)$ vedno rešitev tega sistema. 

Vsak poddoločen homogen sistem ima vsaj eno netrivialno rešitev.

*Dokaz:* Dokazujemo s popolno indukcijo po številu vrstic.
Dokažimo najprej za eno linearno enačbo $a_1x_1 + \dots + a_nx_n = 0$, kjer $n \ge 2$. 

Če je $a_n = 0$, potem je $x = (0, \dots, 0, 1)$ netrivialna rešitev. Če je $a_n \neq 0$, potem je $x = (0, \dots, 0, -a_n, a_{n-1})$ netrivialna rešitev.

Recimo, da trditev drži za vse homogene sisteme z $m-1$ vrsticami. Vzemimo poljuben homogen sistem z $m$ vrsticami in $n > m$ stolpci. Ločimo dva primera. Če so vsi koeficienti pri $x_n$ enaki nič, potem je $(0, \dots, 0, 1)$ netrivialna rešitev. V nasprotnem primeru lahko iz ene od enačb izrazimo $x_n$ s preostalimi spremenljivkami. Ta izraz potem vstavimo v preostalih $m-1$ enačb in uredimo. Dobimo homogen sistem $m-1$ enačb v $n-1$ spremenljivkah $x_1, \dots, x_{n-1}$. Po indukcijski predpostavki ima novi sistem netrivialno rešitev, recimo $(\alpha_1, \dots, \alpha_{n-1})$. To rešitev vstavimo v izraz za $x_n$ in dobimo $\alpha_n$. Potem je $(\alpha_1, \dots, \alpha_{n-1}, \alpha_n)$ netrivialna rešitev prvotnega sistema. $\blacksquare$

Linearna kombinacija dveh rešitev homogenega sistema je spet rešitev tega sistema.

*Dokaz:* Če sta $(s_1, \dots, s_n)$ in $(t_1, \dots, t_n)$ dve rešitvi homogenega sistema, potem velja:

$$ $$
$$
\begin{align*} a_{1,1}s_1 + \dots + a_{1,n}s_n &= 0 \\ &\vdots \\ a_{m,1}s_1 + \dots + a_{m,n}s_n &= 0 \end{align*}$$
$$ $$$$ $$


$$\begin{align*} a_{1,1}t_1 + \dots + a_{1,n}t_n &= 0 \\ &\vdots \\ a_{m,1}t_1 + \dots + a_{m,n}t_n &= 0 \end{align*}
$$
$$ $$
$$As = 0 \quad At = 0$$

Preverimo, da je $(\alpha s_1 + \beta t_1, \dots, \alpha s_n + \beta t_n)$ rešitev sistema za vse $\alpha, \beta \in \mathbb{R}$:

$$As = 0 \quad At = 0$$
$$A(\alpha s + \beta t) = 0$$
$$\alpha As + \beta At = 0$$
$$\alpha \cdot 0 + \beta \cdot 0 = 0$$


Ker so vse enačbe izpolnjene, je linearna kombinacija res rešitev. $\blacksquare$


Če imamo rešitev nehomogenega sistema in rešitev homogenega sistema $p$ in $h$ potem je $p+h$ tudi rešitev nehomogenega sistema.

$A\mathbf{p} = \mathbf{b}$
$A\mathbf{h} = \mathbf{0}$

$A \mathbf{p} = b$
$A\mathbf{p} + A\mathbf{h} = \mathbf{b} + A \mathbf{h}$
$A(\mathbf{p} + \mathbf{h}) = \mathbf{b} + 0$
$A(\mathbf{p} + \mathbf{h}) = \mathbf{b}$
$\implies \mathbf{p} + \mathbf{h}$ je rešitev. $\blacksquare$

Če pa imamo rešitvi $x$ in $p$ nehomogenega sistema velja da je $x-p$ rešitev pripadajočega homogenega sistema.


$A\mathbf{p} = \mathbf{b}$
$A\mathbf{x} = \mathbf{b}$

Potem:
$A\mathbf{x} = \mathbf{b}$
$A\mathbf{x}-A \mathbf{p} = \mathbf{b}-A \mathbf{p}$
$A(\mathbf{x} - \mathbf{p}) = \mathbf{b} - \mathbf{b}$
$A(\mathbf{x} - \mathbf{p}) = \mathbf{0}$

Torej je $\mathbf{x} - \mathbf{p}$ rešitev homogenega sistema. Če to rešitev označimo kot $\mathbf{h}$, dobimo $\mathbf{x} = \mathbf{p} + \mathbf{h}$. $\blacksquare$



### Predoločeni sistemi

Sistem linearnih enačb je predoločen, če ima več enačb kot spremenljivk. Predoločen sistem je običajno nerešljiv, vendar lahko posplošimo definicijo rešitve sistema tako, da bo vsak predoločen sistem posplošeno rešljiv.

**Posplošena rešitev** sistema linearnih enačb
$$
\begin{align*} a_{1,1}x_1 + \dots + a_{1,n}x_n &= b_1 \\ &\vdots \\ a_{m,1}x_1 + \dots + a_{m,n}x_n &= b_m \end{align*} \quad (1)
$$
je taka $n$-terica realnih števil $(x_1, \dots, x_n)$, pri kateri je vektor levih strani $(a_{1,1}x_1 + \dots + a_{1,n}x_n, \dots, a_{m,1}x_1 + \dots + a_{m,n}x_n)$ najbližje vektorju desnih strani $(b_1, \dots, b_m)$.

Sistem linearnih enačb lahko zapišemo v matrični obliki in po geometrijski predstavi vidimo da iščemo pravokotno projekcijo točke $b$ na stolpični prostor matrike koeficientov. To je ekvivalentno temu da iščemo kdaj je vektor razlike pravokoten na vse stolpce matrike.

To pomeni da gledamo kdaj je skalrani produkt vseh stolpcev matrike $A$ in vseh možnih razlik enak 0.

To matrično zapišemo kot

$$A^{T}(Ax-b) = 0$$

to lahko razširimo

$$A^{T}Ax = A^{T}b$$

In tako dobimo posplošeno rešitev kateregakoli predoločenega sistema



### Poddoločeni sistemi
Sistem linearnih enačb je poddoločen, če ima manj enačb kot neznank.
Če je poddoločen sistem linearnih enačb rešljiv, potem ima neskončno rešitev.

Seveda se lahko zgodi, da je nehomogen poddoločen sistem nerešljiv. Recimo $2 \times 3$ sistem $x+y+z=1, x+y+z=2$ je nerešljiv. Tudi $1 \times 2$ sistem $0x+0y=1$ je nerešljiv.

Kadar je poddoločen rešljiv, nas pogosto zanima njegova najkrajša rešitev. 

Geometrijsko gledano iščemo pravokotno projekcijo izhodišča na presek hiperravnin.

Za reševanje takih problemov naprej zapišemo matrično obliko

$$Ax = b$$

Ker iščemo pravokotno projekcijo izhodišča na presek hiperravnin moramo naprej spoznati da so vrstice $A$ normale teh hiperravnin. Ker so normale hiperravnin vedno pravokotne na presek hiperavnin velja da lahko z njimi lahko pridemo do premice tako da bo linearna kombinacija pravokotna na premico.

To pomeni da je naš vektor $x$ neka linearna kombinacija normal.

$$x = A^{T}y$$

kjer je $y$ vektor koeficientov. $A^{T}y$ je vedno pravilnih dimenzij ker se $y$ prilagaja številu normal.

To pomeni da lahko to vstavimo v enačbo 

$$AA^{T}y = b$$

S tem pa lahko izračunamo $y$, s čimer nato izračunamo še $x$ za katerega velja 

$$x = A^{T}y$$ 

$\blacksquare$

<br>

Množico rešitev je afina ravnina izražena kot $x = x_{p} + \ker(A)$, kjer je $x_{p}$ partikularna rešitev.

$$Ax' = A(x_{p}+x_{h}) = Ax_{p} + Ax_{h} = Ax_{p} = b$$

Iščemo rešitev iz te množice tako da ima najmanjšo normo - je pravokotna projekcija izhodišča na afino ravnino. Naj bo rešitev $x_{0}$ - ta mora biti pravokotna na smer afine ravnine - $x_{h} \Rightarrow x_{h} \perp x_{0}$. Ker je $\ker A \perp (\text{row} A^T)$ oz vrstični prostor $A$ je praovkoten na $\ker A$. To pomeni da je $x_{0}$ v vrstičnem prostoru $A$ $\Rightarrow$: $A^{T}y = x_{0}$