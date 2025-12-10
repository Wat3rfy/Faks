## Definicija determinante

Vsaki kvadratni matriki $A$ bomo priredili realno število $\det A$, ki mu pravimo **determinanta** matrike $A$.

Najprej definirajmo determinanto za matrike velikosti $1 \times 1$.

$$\det[a] = a.$$

Za vsako matriko $A$ velikosti $n \times n$ in za vsak $i,j = 1, \dots, n$ označimo z $A_{i,j}$ matriko velikosti $(n-1) \times (n-1)$, ki jo dobimo tako, da v matriki $A$ zbrišemo $i$-to vrstico in $j$-ti stolpec. Definirajmo

$$\det A = a_{1,1} \det A_{1,1} - a_{1,2} \det A_{1,2} + a_{1,3} \det A_{1,3} - \dots + (-1)^{n+1} a_{1,n} \det A_{1,n}.$$

Na kratko to zapišemo s formulo

$$\det A = \sum_{i=1}^{n} (-1)^{1+i} a_{1,i} \det A_{1,i}.$$

Determinanta $2 \times 2$ matrike


$$ A = \begin{bmatrix} a_{1,1} & a_{1,2} \\ a_{2,1} & a_{2,2} \end{bmatrix}, $$

$$ \det A = a_{1,1} \det A_{1,1} - a_{1,2} \det A_{1,2} = a_{1,1} a_{2,2} - a_{1,2} a_{2,1}. $$

**Primer - determinanta $3 \times 3$ matrike**

Izpeljimo še formulo za determinanto $3 \times 3$ matrike. Naj bo

$$ A = \begin{bmatrix} a_{1,1} & a_{1,2} & a_{1,3} \\ a_{2,1} & a_{2,2} & a_{2,3} \\ a_{3,1} & a_{3,2} & a_{3,3} \end{bmatrix} $$


$$
\begin{bmatrix}
    \color{orange}{a_{11}} & \color{orange}{a_{12}} & \color{orange}{a_{13}} & a_{11} & a_{12} \\
    a_{21} & \color{orange}{a_{22}} & \color{orange}{a_{23}} & \color{orange}{a_{21}} & a_{22} \\
    a_{31} & a_{32} & \color{orange}{a_{33}} & \color{orange}{a_{31}} & \color{orange}{a_{32}}
\end{bmatrix}
$$
$$
\begin{bmatrix}
    a_{11} & a_{12} & \color{green}{a_{13}} & \color{green}{a_{11}} & \color{green}{a_{12}} \\
    a_{21} & \color{green}{a_{22}} & \color{green}{a_{23}} & \color{green}{a_{21}} & a_{22} \\
    \color{green}{a_{31}} & \color{green}{a_{32}} & \color{green}{a_{33}} & a_{31} & a_{32}
\end{bmatrix}
$$
$$ $$
$$\det(A) = \color{orange}{(a_{11}a_{22}a_{33})} + \color{orange}{(a_{12}a_{23}a_{31})} + \color{orange}{(a_{13}a_{21}a_{32})}$$ 
$$  \color{green}{-(a_{13}a_{22}a_{31})} - \color{green}{(a_{11}a_{23}a_{32})} - \color{green}{(a_{12}a_{21}a_{33})}$$

<br>

**Geometrijski pomen**

Determinanta $2 \times 2$ matrike:

$$\det \begin{bmatrix} a & b \\ c & d \end{bmatrix} = ad - bc$$

je enaka ploščini paralelograma, ki ga razpenjata stolpca te determinante.

Paralelogram, ki ga razpenjata vektorja $\mathbf{v} = \begin{bmatrix} a \\ c \end{bmatrix}$ in $\mathbf{w} = \begin{bmatrix} b \\ d \end{bmatrix}$ ima ploščino:
$(a+b)(c+d) - 2bc - 2\frac{ac}{2} - 2\frac{bd}{2} = ad - bc = \det A$

Če bi $\mathbf{w}$ ležal na drugi strani $\mathbf{v}$, bi dobili $bc - ad = -\det A$. **Predznak $\det A$ je torej povezan z orientacijo $\mathbf{v}$ in $\mathbf{w}$.**

Determinanta $3 \times 3$ matrike s stolpci $\mathbf{u}$, $\mathbf{v}$, $\mathbf{w}$ je enaka:
$u_1(v_2w_3 - v_3w_2) - v_1(u_2w_3 - u_3w_2) + w_1(u_2v_3 - u_3v_2)$
kar je enako mešanemu produktu:

$$\langle \mathbf{u} \times \mathbf{v}, \mathbf{w} \rangle = (u_2v_3 - u_3v_2)w_1 + (u_3v_1 - u_1v_3)w_2 + (u_1v_2 - u_2v_1)w_3$$

Predznak $\det \begin{bmatrix} \mathbf{u} & \mathbf{v} & \mathbf{w} \end{bmatrix}$ je povezan z orientacijo vektorjev $\mathbf{u}$, $\mathbf{v}$, $\mathbf{w}$. Če zadoščajo pravilu desnega vijaka, je predznak pozitiven.

**Izrek o razvoju determinante**

Če je $A$ matrika velikosti $n \times n$, potem za poljubna $i,j \in \{1, \dots, n\}$ veljata naslednji formuli:

*   Formula za razvoj det $A$ po $i$-ti vrstici:
    $$ \det A = \sum_{k=1}^{n} a_{i,k}(-1)^{i+k} \det A_{i,k}; $$
*   Formula za razvoj det $A$ po $j$-tem stolpcu:
    $$ \det A = \sum_{k=1}^{n} a_{k,j}(-1)^{k+j} \det A_{k,j}. $$

**Determinanta v splošnem ni linearna**
Naj bo
$$ A = \begin{bmatrix} 1 & 0 \\ 0 & 0 \end{bmatrix}, \quad B = \begin{bmatrix} 0 & 0 \\ 0 & 1 \end{bmatrix} $$
Potem je $\det(A + B) = \det I = 1$ in $\det A + \det B = 0 + 0 = 0$. Torej je
$$ \det(A + B) \ne \det A + \det B $$
Naj bo sedaj $C = I$ in $\alpha = 2$. Potem je $\det(\alpha C) = 4$ in $\alpha \det C = 2$, torej
$$ \det(\alpha C) \ne \alpha \det C $$

**Linearnost po vrsticah**
Velja naslednja formula, ki ji pravimo linearnost determinante v $i$-ti vrstici:
$$
\det \begin{bmatrix}
a_{1,1} & \cdots & a_{1,n} \\
\vdots & \ddots & \vdots \\
a_{i-1,1} & \cdots & a_{i-1,n} \\
\beta b_{i,1} + \gamma c_{i,1} & \cdots & \beta b_{i,n} + \gamma c_{i,n} \\
a_{i+1,1} & \cdots & a_{i+1,n} \\
\vdots & \ddots & \vdots \\
a_{n,1} & \cdots & a_{n,n}
\end{bmatrix} = \beta \det \begin{bmatrix}
a_{1,1} & \cdots & a_{1,n} \\
\vdots & \ddots & \vdots \\
a_{i-1,1} & \cdots & a_{i-1,n} \\
b_{i,1} & \cdots & b_{i,n} \\
a_{i+1,1} & \cdots & a_{i+1,n} \\
\vdots & \ddots & \vdots \\
a_{n,1} & \cdots & a_{n,n}
\end{bmatrix} + \gamma \det \begin{bmatrix}
a_{1,1} & \cdots & a_{1,n} \\
\vdots & \ddots & \vdots \\
a_{i-1,1} & \cdots & a_{i-1,n} \\
c_{i,1} & \cdots & c_{i,n} \\
a_{i+1,1} & \cdots & a_{i+1,n} \\
\vdots & \ddots & \vdots \\
a_{n,1} & \cdots & a_{n,n}
\end{bmatrix} \quad (1)
$$
>[!|dokaz]- Dokaz:
>
> $$
> A(\beta, \gamma) = \begin{bmatrix}
> a_{1,1} & \cdots & a_{1,n} \\
> \vdots & \ddots & \vdots \\
> a_{i-1,1} & \cdots & a_{i-1,n} \\
> \beta b_{i,1} + \gamma c_{i,1} & \cdots & \beta b_{i,n} + \gamma c_{i,n} \\
> a_{i+1,1} & \cdots & a_{i+1,n} \\
> \vdots & \ddots & \vdots \\
> a_{n,1} & \cdots & a_{n,n}
> \end{bmatrix}
> $$
> Razvijemo po $i$-ti vrstici. Dobimo
> $$
> \det A(\beta, \gamma) = \sum_{k=1}^{n} (-1)^{i+k}(\beta b_{i,k} + \gamma c_{i,k}) \det A_{i,k} \\
> = \beta \sum_{k=1}^{n} (-1)^{i+k} b_{i,k} \det A_{i,k} + \gamma \sum_{k=1}^{n} (-1)^{i+k} c_{i,k} \det A_{i,k}
> $$
> Odtod sledi želena formula
> $$
> \det A(\beta, \gamma) = \beta \det A(1,0) + \gamma \det A(0,1)
> $$

>**Zamenjava dveh vrstic v determinanti**
Če v matriki zamenjamo dve vrstici, se njeni determinanti spremeni predznak. Se pravi $\det P_{i,j}A = - \det A$.

**Dokaz:** 

Trditev velja za $2 \times 2$ matrike, ker je
$$\det \begin{bmatrix} a_{2,1} & a_{2,2} \\ a_{1,1} & a_{1,2} \end{bmatrix} = a_{2,1}a_{1,2} - a_{2,2}a_{1,1} = - (a_{1,1}a_{2,2} - a_{1,2}a_{2,1}) = - \det \begin{bmatrix} a_{1,1} & a_{1,2} \\ a_{2,1} & a_{2,2} \end{bmatrix}.$$
Predpostavimo, da trditev velja za $(n-1) \times (n-1)$ matrike, kjer je $n \ge 3$.
Vzemimo poljubno $n \times n$ matriko $A$ in poljubna $i$ in $j$, ki sta različna.
Potem za poljuben $k$, ki je različen od $i$ in $j$, lahko $\det P_{i,j}A$ izračunamo tako, da jo razvijemo po $k$-ti vrstici, upoštevamo indukcijsko predpostavko, izpostavimo $-1$ in upoštevamo formulo za razvoj $\det A$ po $k$-ti vrstici.
Dobimo ravno $-\det A$.

*Dokaz začnemo z neposredno potrditvijo trditve za $2 \times 2$ matrike, kjer zamenjava vrstic očitno spremeni predznak determinante. Nato predpostavimo, da trditev velja za $(n-1) \times (n-1)$ matrike kot indukcijsko predpostavko. Za dokazovanje veljavnosti za $n \times n$ matriko $A$, pri kateri sta zamenjani vrstici $i$ in $j$, izračunamo $\det P_{i,j}A$ z razvojem po $k$-ti vrstici, kjer $k$ ni niti $i$ niti $j$. Ker se $k$-ta vrstica ni premaknila, so minorne matrike $M_{k,l}(P_{i,j}A)$ v bistvu $M_{k,l}(A)$ z zamenjanima dvema vrsticama. Z uporabo indukcijske predpostavke ugotovimo, da je $\det(M_{k,l}(P_{i,j}A)) = - \det(M_{k,l}(A))$, kar pri vstavljanju v razvoj po $k$-ti vrstici omogoča izpostavljanje faktorja $-1$. To nazadnje dokaže, da je $\det P_{i,j}A = - \det A$.*

**Posledica**
Če ima matrika dve vrstici enaki, potem je njena determinanta enaka nič.

**Dokaz:** Če sta $i$-ta in $j$-ta vrstica matrike $A$ enaki, potem je $P_{i,j}A = A$. Odtod sledi $\det P_{i,j}A = \det A$. Toda zgoraj smo dokazali, da je $\det P_{i,j}A = -\det A$. Od tod sledi $\det A = -\det A$, torej je res $\det A = 0$.

>**Trditev**
Če v matriki $A$ k eni vrstici prištejemo večkratnik druge vrstice, potem se njena determinanta ne spremeni. Se pravi $\det(E_{i,j}(\alpha)A) = \det A$.

**Dokaz:** Po Trditvi 1 in po Posledici je
$$
\det(E_{i,j}(\alpha)A) = \det \begin{bmatrix}
\vdots \\
a_{i,1} + \alpha a_{j,1} & \cdots & a_{i,n} + \alpha a_{j,n} \\
\vdots \\
a_{j,1} & \cdots & a_{j,n} \\
\vdots
\end{bmatrix} =
$$
$$
= \det \begin{bmatrix}
\vdots \\
a_{i,1} & \cdots & a_{i,n} \\
\vdots \\
a_{j,1} & \cdots & a_{j,n} \\
\vdots
\end{bmatrix}
+ \alpha \det \begin{bmatrix}
\vdots \\
a_{j,1} & \cdots & a_{j,n} \\
\vdots \\
a_{j,1} & \cdots & a_{j,n} \\
\vdots
\end{bmatrix} =
$$
$$
= \det A + \alpha \cdot 0 = \det A
$$

**Gaussova metoda za računanje determinant**

>**Trditev**
>*   Če v matriki $A$ k eni vrstici prištejemo večkratnik druge vrstice, potem se njena determinanta ne spremeni.
>*   Če v matriki $A$ zamenjamo dve vrstici, potem se njeni determinanti spremeni predznak.
>*   Če v matriki $A$ eno vrstico pomnožimo z $\beta$, potem se tudi njena determinanta pomnoži z $\beta$.

**Trditev**
Determinanta zgornje trikotne matrike je enaka produktu elementov na njeni glavni diagonali.

**Dokaz:** Če večkrat uporabimo formulo za razvoj po prvem stolpcu, dobimo
$$
\det \begin{bmatrix}
a_{1,1} & a_{1,2} & \cdots & a_{1,n} \\
0 & a_{2,2} & \cdots & a_{2,n} \\
\vdots & \vdots & \ddots & \vdots \\
0 & 0 & \cdots & a_{n,n}
\end{bmatrix} = a_{1,1} \det \begin{bmatrix}
a_{2,2} & \cdots & a_{2,n} \\
\vdots & \ddots & \vdots \\
0 & \cdots & a_{n,n}
\end{bmatrix} =
$$
$$
= a_{1,1}a_{2,2} \det \begin{bmatrix}
a_{3,3} & \cdots & a_{3,n} \\
\vdots & \ddots & \vdots \\
0 & \cdots & a_{n,n}
\end{bmatrix} = \cdots = a_{1,1}a_{2,2}\cdots a_{n,n}.
$$

>**Determinanta produkta matrik**
Za poljubni kvadratni matriki $A$ in $B$ velja $\det AB = \det A \det B$.


**Dokaz:**

Če v formule
$$ \det(E_{i,j}(\alpha)B) =\det B =  \det E_{i,j}(\alpha)\det B, $$
$$ \det(P_{i,j}B) = - \det B = \det P_{i,j} \det B $$
$$ \det(E_i(\beta)B) = \beta \det B  = \det E_{i}(\beta) \det B$$


Torej formula $\det AB = \det A \det B$ velja, ko je $A$ elementarna matrika.

Formula $\det AB = \det A \det B$ velja tudi v primeru, ko ima matrika $A$ v eni vrstici same ničle, saj ima potem tudi matrika $AB$ v isti vrstici same ničle, torej je $\det A = \det AB = 0$, kar vidimo iz razvoja po tej vrstici.

Po Gaussu obstajajo take elementarne matrike $E_1, \ldots, E_n$, da ima matrika $S = E_n \cdots E_1 A$ reducirano vrstično stopničasto obliko. Ločimo dva primera.


Če ima matrika $S$ ničelno vrstico, potem velja
$$ \det E_n \cdots \det E_1 \det AB = \det(E_n \cdots E_1 A)B = \det SB = 0, $$
$$ \det E_n \cdots \det E_1 \det A = \det E_n \cdots E_1 A = \det S = 0. $$
Spodnjo enačbo množimo z $\det B$ in dobimo da sta obe enaki 0.

Če pa matrika $S$ nima ničelne vrstice, potem je $S = I$. Odtod sledi, da je


$\det B= \det IB  = \det(E_n \cdots E_{1} A)B = \det E_n \cdots \det E_1 \det AB$
 $\det B= \det I\det B  = \det(E_n \cdots E_{1} A) \det B = \det E_n \cdots \det E_{1} \det A\det B$

Po krajšanju spet dobimo $\det AB = \det A \det B$.

>**Izrek o determinanti obrnljive matrike**
Kvadratna matrika $A$ je obrnljiva natanko tedaj, ko je $\det A \neq 0$.

**Dokaz:** Če je matrika $A$ obrnljiva, potem obstaja taka matrika $B$, da velja $AB = I$. Če na obeh straneh uporabimo determinanto, dobimo
$$ \det A \det B = \det AB = \det I = 1. $$
Odtod sledi, da je $\det A \neq 0$.

Recimo sedaj, da je $\det A \neq 0$. Izberimo take elementarne matrike $E_1, \dots, E_n$, da je $S := E_n \cdots E_1 A$ reducirana vrstična stopničasta forma. Ker so elementarne matrike obrnljive, imajo neničelne determinante. Po predpostavki $\det A \neq 0$ odtod sledi, da je $\det S \neq 0$. Torej $S$ ne more imeti ničelne vrstice. Odtod sledi, da je $S = I$. Torej je $A = E_1^{-1} \cdots E_n^{-1}$ obrnljiva matrika.

>**Izrek o determinanti transponirane matrike**
Za vsako kvadratno matriko $A$ velja $\det A^T = \det A$.

**Dokaz.** Najprej opazimo, da izrek velja za elementarne matrike:
*   Iz $P_{i,j}^T = P_{i,j}$ sledi $\det P_{i,j}^T = \det P_{i,j}$.
*   Iz $E_i(\beta)^T = E_i(\beta)$ sledi $\det E_i(\beta)^T = \det E_i(\beta)$.
*   Iz $E_{i,j}(\alpha)^T = E_{j,i}(\alpha)$ sledi $\det E_{i,j}(\alpha)^T = 1 = \det E_{i,j}(\alpha)$.

Izberimo take elementarne matrike $E_1, \dots, E_n$, da je $S := E_n \cdots E_1 A$ reducirana vrstična stopničasta forma. Ločimo dva primera:
*   Če ima $S$ ničelno vrstico, potem ima $S^T$ ničeln stolpec, torej je $\det S^T = 0 = \det S$.
*   Če je $S = I$, potem $\det S^T = 1 = \det S$, ker je $I^T = I$.
Torej je v obeh primerih $\det S^T = \det S$.

Ker je determinanta produkta produkt determinant, velja
$$ \det S = \det(E_n \cdots E_1 A) $$
$$ = \det E_n \cdots \det E_1 \det A \quad (5) $$
in
$$ \det S^T = \det((E_n \cdots E_1 A)^T) $$
$$ = \det(A^T E_1^T \cdots E_n^T) = $$
$$ = \det A^T \det E_1^T \cdots \det E_n^T \quad (6) $$
Iz (5) in (6) sledi
$$ \det A^T = \det A \quad (7) $$
ker je $\det S^T = \det S$ in $\det E_i^T = \det E_i \neq 0$ za vsak $i = 1, \dots, n$.

>**Izrek o determinanti bločno zgornje trikotne matrike**
Za vsako bločno zgornje trikotno matriko velja
$$ \det \begin{bmatrix} A & B \\ 0 & C \end{bmatrix} = \det A \det C $$

**Dokaz:** Najprej opazimo, da velja
$$ \begin{bmatrix} A & B \\ 0 & C \end{bmatrix} = \begin{bmatrix} I & 0 \\ 0 & C \end{bmatrix} \begin{bmatrix} A & B \\ 0 & I \end{bmatrix} $$
Odtod sledi
$$ \det \begin{bmatrix} A & B \\ 0 & C \end{bmatrix} = \det \begin{bmatrix} I & 0 \\ 0 & C \end{bmatrix} \det \begin{bmatrix} A & B \\ 0 & I \end{bmatrix} $$
Dokažimo sedaj, da je
$$ \det \begin{bmatrix} A & B \\ 0 & I \end{bmatrix} = \det \begin{bmatrix} A & 0 \\ 0 & I \end{bmatrix} $$
S pomočjo elementarnih transformacij tipa $E_{i,j}(\alpha)$ lahko namreč eno matriko prevedemo na drugo. Natančneje
$$ \begin{bmatrix} A & B \\ 0 & I \end{bmatrix} = E \begin{bmatrix} A & 0 \\ 0 & I \end{bmatrix} $$

Z večkratno uporabo razvoja po prvi vrsti dobimo:
$$ \det \begin{bmatrix} I_m & 0 \\ 0 & C \end{bmatrix} = \det \begin{bmatrix} I_{m-1} & 0 \\ 0 & C \end{bmatrix} = \cdots = \det \begin{bmatrix} I_1 & 0 \\ 0 & C \end{bmatrix} = \det C $$
Z večkratno uporabo razvoja po zadnji vrsti dobimo
$$ \det \begin{bmatrix} A & 0 \\ 0 & I_n \end{bmatrix} = \det \begin{bmatrix} A & 0 \\ 0 & I_{n-1} \end{bmatrix} = \cdots = \det \begin{bmatrix} A & 0 \\ 0 & I_1 \end{bmatrix} = \det A $$
Torej je
$$ \det \begin{bmatrix} A & B \\ 0 & C \end{bmatrix} = \det \begin{bmatrix} I_m & 0 \\ 0 & C \end{bmatrix} \det \begin{bmatrix} A & 0 \\ 0 & I_n \end{bmatrix} = \det C \det A $$

**Schurov komplement**

>**Trditev**
Naj bodo $A, B, C$ in $D$ matrike velikosti $m \times m, m \times n, n \times m$ in $n \times n$.
*   Če je matrika $D$ obrnljiva, potem velja
    $$ \det \begin{bmatrix} A & B \\ C & D \end{bmatrix} = \det D \det(A - BD^{-1}C) $$
*   Če je matrika $A$ obrnljiva, potem velja
    $$ \det \begin{bmatrix} A & B \\ C & D \end{bmatrix} = \det A \det(D - CA^{-1}B) $$

**Dokaz:** Če je matrika $D$ obrnljiva, potem velja
$$ \begin{bmatrix} A & B \\ C & D \end{bmatrix} = \begin{bmatrix} A - BD^{-1}C & B \\ 0 & D \end{bmatrix} \begin{bmatrix} I_m & 0 \\ D^{-1}C & I_n \end{bmatrix} $$
Odtod sledi, da je
$$ \det \begin{bmatrix} A & B \\ C & D \end{bmatrix} = \det \begin{bmatrix} A - BD^{-1}C & B \\ 0 & D \end{bmatrix} \det \begin{bmatrix} I_m & 0 \\ D^{-1}C & I_n \end{bmatrix} $$
$$ = \det(A - BD^{-1}C) \det D \det I_m \det I_n $$

Če je matrika $A$ obrnljiva, potem velja
$$ \begin{bmatrix} A & B \\ C & D \end{bmatrix} = \begin{bmatrix} I_m & 0 \\ CA^{-1} & I_n \end{bmatrix} \begin{bmatrix} A & B \\ 0 & D - CA^{-1}B \end{bmatrix} $$
Odtod sledi, da je
$$ \det \begin{bmatrix} A & B \\ C & D \end{bmatrix} = \det \begin{bmatrix} I_m & 0 \\ CA^{-1} & I_n \end{bmatrix} \det \begin{bmatrix} A & B \\ 0 & D - CA^{-1}B \end{bmatrix} $$
$$ = \det I_m \det I_n \det A \det(D - CA^{-1}B) $$


>**Izrek - Cramerovo pravilo**
Če je $A$ $n \times n$ matrika z $\det A \neq 0$, potem je rešitev sistema (1) podana z
$$ x_i = \frac{\det A_i(\mathbf{b})}{\det A}, \quad i = 1, \dots, n. \quad (2) $$
Kjer za vsak $i = 1, \dots, n$ označimo z $A_i(\mathbf{b})$ matriko, ki jo dobimo iz matrike $A$ tako, da njen $i$-ti stolpec zamenjamo z vektorjem $\mathbf{b}$.

**Dokaz.** 
Naj bodo $\mathbf{a}_1, \dots, \mathbf{a}_n$ stolpci matrike $A$. Za vsak $i = 1, \dots, n$ je
$$ A_i(\mathbf{b}) = \begin{bmatrix} \mathbf{a}_1 & \cdots & \mathbf{a}_{i-1} & \mathbf{b} & \mathbf{a}_{i+1} & \cdots & \mathbf{a}_n \end{bmatrix} $$
Definiramo še matriko
$$ I_i(\mathbf{x}) = \begin{bmatrix} \mathbf{e}_1 & \cdots & \mathbf{e}_{i-1} & \mathbf{x} & \mathbf{e}_{i+1} & \cdots & \mathbf{e}_n \end{bmatrix} $$
kjer so $\mathbf{e}_1, \dots, \mathbf{e}_n$ stolpci identične matrike $I$ in je $\mathbf{x}$ rešitev sistema $Ax = \mathbf{b}$. Opazimo, da velja
$$\begin{array}
 AA I_i(\mathbf{x}) = A \begin{bmatrix} \mathbf{e}_1 & \cdots & \mathbf{e}_{i-1} & \mathbf{x} & \mathbf{e}_{i+1} & \cdots & \mathbf{e}_n \end{bmatrix} \\ = \begin{bmatrix} A\mathbf{e}_1 & \cdots & A\mathbf{e}_{i-1} & A\mathbf{x} & A\mathbf{e}_{i+1} & \cdots & A\mathbf{e}_n \end{bmatrix} \\ = \begin{bmatrix} \mathbf{a}_1 & \cdots & \mathbf{a}_{i-1} & \mathbf{b} & \mathbf{a}_{i+1} & \cdots & \mathbf{a}_n \end{bmatrix} \\ = A_i(\mathbf{b})
\end{array}  $$
Odtod sledi
$$ \det A \det I_i(\mathbf{x}) = \det A_i(\mathbf{b}). $$
Z razvojem $\det I_i(\mathbf{x})$ po $i$-ti vrstici dobimo še $\det I_i(\mathbf{x}) = x_i$

**Formula za inverz matrike**


**Definicija kofaktorske matrike**
Naj bo $A$ kvadratna matrika. Če v matriki $A$ vsak element $a_{i,j}$ zamenjamo z njegovim **kofaktorjem** $(-1)^{i+j} \det A_{i,j}$, dobimo **kofaktorsko matriko** matrike $A$. Oznaka zanjo je $\tilde{A}$. (Spomnimo se, da matriko $A_{i,j}$ dobimo tako, da v matriki $A$ pobrišemo $i$-to vrstico in $j$-ti stolpec.)

**Primer kofaktorske matrike**

$$ A = \begin{bmatrix} a & b \\ c & d \end{bmatrix} \implies \tilde{A} = \begin{bmatrix} d & -c \\ -b & a \end{bmatrix} $$
$$ A = \begin{bmatrix} a & b & c \\ d & e & f \\ g & h & i \end{bmatrix} \Rightarrow \tilde{A} = \begin{bmatrix} ei-fh & fg-di & dh-eg \\ ch-bi & ai-cg & bg-ah \\ bf-ce & cd-af & ae-bd \end{bmatrix} $$

**Izrek - Formula za $A^{-1}$**
Naj bo $A$ $n \times n$ matrika, ki zadošča $\det A \neq 0$. Potem velja
$$ A^{-1} = \frac{1}{\det A} \tilde{A}^T \quad (3) $$
kjer je $\tilde{A}$ kofaktorska matrika matrike $A$.

**Dokaz:** Matrika $A^{-1}$ je rešitev matrične enačbe
$$ AX = I. $$
Naj bodo $\mathbf{x}_1, \dots, \mathbf{x}_n$ stolpci matrike $X$. Potem velja
$$ A\mathbf{x}_1 = \mathbf{e}_1 \quad \dots \quad A\mathbf{x}_n = \mathbf{e}_n $$
kjer so $\mathbf{e}_1, \dots, \mathbf{e}_n$ stolpci matrike $I$.
Vzemimo poljubna $i$ in $j$ in izračunajmo $(i,j)$-ti element matrike $X$. Velja
$$ x_{i,j} = i\text{-ti element vektorja } \mathbf{x}_j = \frac{\det A_i(\mathbf{e}_j)}{\det A} $$
Pri drugem enačaju smo uporabili Cramerovo pravilo za sistem $A\mathbf{x}_j = \mathbf{e}_j$.

Determinanto $A_i(\mathbf{e}_j)$ izračunamo z razvojem po $i$-tem stolpcu pa dobimo
$$ \det A_i(\mathbf{e}_j) = (-1)^{i+j} \det A_{j,i} $$
odkoder sledi
$$ x_{i,j} = (-1)^{i+j} \frac{\det A_{j,i}}{\det A} = \frac{1}{\det A} (\text{kofaktor } a_{j,i}) $$
Torej je res
$$ A^{-1} = X = \frac{1}{\det A} \tilde{A}^T $$

**Determinante in permutacije**

Za vsako naravno število $n$ označimo $N_n = \{1, 2, \ldots, n\}$. Za vsako preslikavo $\sigma: N_n \to N_n$ so ekvivalentne naslednje lastnosti:
*   $\sigma$ je injektivna (=slika različne elemente v različne elemente),
*   $\sigma$ je surjektivna (=vsak element je slika nekega elementa),
*   $\sigma$ je bijektivna (=injektivna in surjektivna).
Preslikavi, ki zadošča eni od teh treh ekvivalentnih lastnosti, pravimo **permutacija** množice $N_n$. Množico vseh permutacij $N_n$ označimo s $S_n$.


Naj bo $e_i$ stolpčni vektor velikosti $n$, ki ima na $i$-tem mestu enko, drugod pa same ničle. Vsaki permutaciji $\sigma \in S_n$ priredimo matriko
$$P_{\sigma} := \begin{bmatrix} e_{\sigma(1)} & e_{\sigma(2)} & \ldots & e_{\sigma(n)} \end{bmatrix}$$
Determinanti te matrike pravimo **signatura** permutacije $\sigma$. Oznaka je
$$\text{sgn}(\sigma) := \det P_{\sigma}$$


Če za $\sigma$ vzamemo **transpozicijo** elementov $i$ in $j$, se pravi permutacijo
$$\sigma(k) = \begin{cases} j & \text{če } k = i \\ i & \text{če } k = j \\ k & \text{če } k \neq i, j \end{cases}$$
dobimo $P_\sigma = P_{i,j}$ in $\text{sgn}(\sigma) = \det P_{i,j} = -1$.

>Za vsako permutacijo $\sigma$ velja $\text{sgn}(\sigma) \in \{-1,1\}$

**Dokaz:**

**Najprej opazimo, da velja**
$$P_{\sigma}^T P_{\sigma} = \begin{bmatrix} e_{\sigma(1)}^T \\ e_{\sigma(2)}^T \\ \vdots \\ e_{\sigma(n)}^T \end{bmatrix} \begin{bmatrix} e_{\sigma(1)} & e_{\sigma(2)} & \ldots & e_{\sigma(n)} \end{bmatrix}$$
$$ = \begin{bmatrix} \langle e_{\sigma(1)}, e_{\sigma(1)} \rangle & \langle e_{\sigma(1)}, e_{\sigma(2)} \rangle & \ldots & \langle e_{\sigma(1)}, e_{\sigma(n)} \rangle \\ \langle e_{\sigma(2)}, e_{\sigma(1)} \rangle & \langle e_{\sigma(2)}, e_{\sigma(2)} \rangle & \ldots & \langle e_{\sigma(2)}, e_{\sigma(n)} \rangle \\ \vdots & \vdots & \ddots & \vdots \\ \langle e_{\sigma(n)}, e_{\sigma(1)} \rangle & \langle e_{\sigma(n)}, e_{\sigma(2)} \rangle & \ldots & \langle e_{\sigma(n)}, e_{\sigma(n)} \rangle \end{bmatrix}$$
$$ = I $$

**Odtod sledi, da je**
$$(\det P_{\sigma})^2 = \det P_{\sigma}^T \det P_{\sigma} = \det P_{\sigma}^T P_{\sigma} = \det I = 1$$

---

Pokažimo še, da za vsaki permutaciji $\sigma$ in $\tau$ velja
$\text{sgn}(\sigma \circ \tau) = \text{sgn}(\sigma) \text{sgn}(\tau)$

Očitno za vsak $i$ velja
$P_{\sigma} e_i = e_{\sigma(i)}$

Odtod sledi
$$P_{\sigma} P_{\tau} = P_{\sigma} \begin{bmatrix} e_{\tau(1)} & e_{\tau(2)} & \ldots & e_{\tau(n)} \end{bmatrix}$$
$$ = \begin{bmatrix} P_{\sigma} e_{\tau(1)} & P_{\sigma} e_{\tau(2)} & \ldots & P_{\sigma} e_{\tau(n)} \end{bmatrix}$$
$$ = \begin{bmatrix} e_{\sigma(\tau(1))} & e_{\sigma(\tau(2))} & \ldots & e_{\sigma(\tau(n))} \end{bmatrix}$$
$$ = P_{\sigma \circ \tau}$$

Če uporabimo determinanto na obeh straneh, dobimo želeno formulo.

***

Radi bi dokazali naslednjo formulo

$$\det A = \sum_{\pi \in S_n} \mathrm{sgn}(\pi) a_{1,\pi(1)} a_{2,\pi(2)} \dots a_{n,\pi(n)}$$

Ideja dokaza je, da vsako vrstico matrike $A$ izrazimo kot
$$[a_{i,1} \ a_{i,2} \ \dots \ a_{i,n}] = \sum_{j=1}^{n} a_{i,j} \mathbf{e}_{j}^{T}$$
in nato upoštevamo linearnost determinante v tej vrstici. Dobimo
$$\det A = \det \begin{bmatrix} a_{1,1} & a_{1,2} & \dots & a_{1,n} \\ \vdots & \vdots & \ddots & \vdots \\ a_{n,1} & a_{n,2} & \dots & a_{n,n} \end{bmatrix} = \det \begin{bmatrix} \sum_{j_1=1}^{n} a_{1,j_1} \mathbf{e}_{j_1}^{T} \\ \vdots \\ \sum_{j_n=1}^{n} a_{n,j_n} \mathbf{e}_{j_n}^{T} \end{bmatrix}$$
$$= \sum_{j_1=1}^{n} \dots \sum_{j_n=1}^{n} a_{1,j_1} \dots a_{n,j_n} \det \begin{bmatrix} \mathbf{e}_{j_1}^{T} \\ \vdots \\ \mathbf{e}_{j_n}^{T} \end{bmatrix} = \sum_{(j_1, \dots, j_n) \in (\mathbb{N}_n)^n} a_{1,j_1} \dots a_{n,j_n} \det \begin{bmatrix} \mathbf{e}_{j_1}^{T} \\ \vdots \\ \mathbf{e}_{j_n}^{T} \end{bmatrix}$$

Če sta dve izmed števil $j_1, \dots, j_n$ enaki, potem je
$$\det \begin{bmatrix} \mathbf{e}_{j_1}^{T} \\ \vdots \\ \mathbf{e}_{j_n}^{T} \end{bmatrix} = 0,$$
ker ima determinanta dve vrstici enaki. Če pa so števila $j_1, \dots, j_n$ paroma različna, potem je funkcija, ki pošlje vsak $k$ v $j_k$, injektivna, se pravi
$$\begin{pmatrix} 1 & 2 & \dots & n \\ j_1 & j_2 & \dots & j_n \end{pmatrix} \in S_n$$
V tem primeru je
$$\det \begin{bmatrix} \mathbf{e}_{j_1}^{T} \\ \vdots \\ \mathbf{e}_{j_n}^{T} \end{bmatrix} = \det [\mathbf{e}_{j_1} \ \dots \ \mathbf{e}_{j_n}] = \mathrm{sgn} \begin{pmatrix} 1 & 2 & \dots & n \\ j_1 & j_2 & \dots & j_n \end{pmatrix}$$

Dokazali smo, da velja
$$\det A = \sum_{\substack{(j_1 \ j_2 \ \dots \ j_n) \in S_n}} \mathrm{sgn} \begin{pmatrix} 1 & 2 & \dots & n \\ j_1 & j_2 & \dots & j_n \end{pmatrix} a_{1,j_1} \dots a_{n,j_n}$$
kar na kratko zapišemo kot
$$\det A = \sum_{\pi \in S_n} \mathrm{sgn}(\pi) a_{1,\pi(1)} a_{2,\pi(2)} \dots a_{n,\pi(n)}$$