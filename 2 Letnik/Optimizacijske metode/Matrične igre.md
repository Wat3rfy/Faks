Matrična igra je igra dveh igralcev z ničelno vsoto in s končnim številom čistih strategij.

Če igralec plača $v$ drugemu potem zgubi $-v$, drugi pa dobi $v$ - njuna vsota je 0.

V splošnem so vrste problemov kjer imamo 2 igralca, kjer ima prvi igralec $n$ strategij 2. igralec pa $m$ strategij.

Če se prvi igralec odloči za $i$-to strategijo in drugi za $j$-to je $a_{ij}$ znesek ki ga drugi igralec plača prvemu.

Znesek $a_{ij} > 0$ pove da drugi igralec plača prvemu, $a_{ij} < 0$ pa da prvi plača drugemu *oz. $a_{ij}>0$ pove da prvi igralec dobi, $a_{ij} < 0$ pa da drugi igralec dobi.*

$[a_{ij}], i \in [n], j \in [m]$ je plačilna matrika.

***

1\. Kamen - škarje - papir

$$
\begin{array}{c|ccc}
2/1 & K & \check{S} & P \\
\hline
K & 0 & 1 & -1 \\
\check{S} & -1 & 0 & 1 \\
P & 1 & -1 & 0
\end{array}
$$

***

2\. Blotto

Polkovnik Blotto (1), major Clark, 2 strateški točki na katero lahko vsak da polj. število bataljon. Blotto ima na voljo 4, Clark pa 3.

Na vsaki točki zmaga tisti ki ima tam več bataljonov in sicer tisti ki zgubi plača zamgovalcu $k+1$, kjer je $k$ število bataljonov poraženca na strateški točki.

$$
\begin{array}{c|cccc}
1. B \setminus 2. C & 0 & 1 & 2 & 3 \\
\hline
0 & 4 & 2 & 1 & 0 \\
1 & 1 & 3 & 0 & -1 \\
2 & -2 & 2 & 2 & -2 \\
3 & -1 & 0 & 3 & 2 \\
4 & 0 & 1 & 2 & 4
\end{array}
$$

Igralca se sedaj odločata katero strategijo izbrati. Recimo da si izbira Blotto. Pri izbiri prve strategije vidimo da je v najslabšem primeru dobil 0, če igra druge strategije ima slabše najslabše primere razen zadnje. 

Igralca hočeta tvegati čim manj.

Torej izbereta strategijo kjer izgubita najmanj oz. minimizirata izgubo.

Prvi igralec išče minimum v vsaki vrstici.

$$M_{1} := \max_{i}\min_{j}a_{ij}$$

Drugi igralec zaradi tega ker je njegov dobiček negativen išče kje najmanj zgubi tako da poišče maksimum vsakega stolpca in potem vzame najmanjšega

$$M_{2} := \min_{j}\max_{i}a_{ij}$$

V tem primeru je $M_{1} = 0$ in $M_{2} = 4$

> Velja
> 
> $$M_{1} \leq M_{2}$$
> >[!|dokaz]+ Dokaz:
> > $M_{1}$ naj bo dosežen v $i',j'$.
> > $M_{2}$ naj bo dosežen v $i'',j''$.
> > 
> > $$
> > \begin{array}{ccc}
> >  & j' & j'' \\
> > i' & M_1 & x \\
> > i'' & & M_2
> > \end{array}
> > $$
> > 
> > $\Rightarrow M_1 \le x, \quad x \le M_2$
> > 
> > $\Rightarrow M_1 \le M_2$


Pravimo da je $(i_{0},j_{0})$ **sedlo plačilne matrike** $A$, če je $a_{i_{0},j_{0}}$ najmanjši v svoji vrstici in največji v svojem stolpcu

> $A$ ima sedlo $\Leftrightarrow$ $M_{1} = M_{2}$
> >[!|dokaz]+ Dokaz:
> >
> >Naj bo sedlo na $a_{i,j}$, velja da je $a_{i,j}$ najmanjši element v vrstici, ker je $M_{1}$ največji od minimumov vrstic velja $M_{1} \ge a_{i,j}$, enako velja $M_{2} \le a_{i,j}$. Ker velja $M_{1} \le M_{2}$ mora veljati $a_{i,j} = M_{1} = M_{2}$.


**Če ima igra sedlo sta pripadajoči strategiji optimalni za oba igralca.**

V tem primeru je sedlo **Neshevo ravnovesje**.

Če oba igrata optimalno se nobenemu ne splača spremeniti strategije.

***

**Mešana strategija**

**Mešana strategija** je vektor verjetnosti izbire ene od strategij. Množica vseh mešanih strategij so vektorji $(x_{1},...,x_{n}) \in \mathbb{R}^{n}$, kjer velja $\sum_{}^{}x_{i} = 1, x_i \ge0$.

Prvi igralec izbere nek $(x_{1},...,x_{n})$ kjer nam vsak $x_{i}$ predstavlja verjetnost izbire $i$-te strategije.

Enako velja za drugega igralca z $(y_{1},...,y_{n})$

Verjetnost da prvi izbere $i$ in drugi izbere $j$ je produkt $x_{i}y_{j}$ (neodvisna dogodka).

**Matematično upanje izplačila za prvega igralca** pa bi bilo $\sum_{i=1,j=1}^{n,m}x_{i}y_{j}a_{ij}$. *"povprečje"*

Vidimo da je $$\sum_{i=1,j=1}^{n,m}x_{i}y_{j}a_{ij} = \sum_{i=1}^{n}\left(\sum_{j=1}^{m}a_{ij}y_{j}\right)x_{i} = x^{T}Ay$$


Če prvi igralec uporabi strategijo $x$ in drugi $y$ bo matemaično upanje enako

$$x^{T}Ay$$

Prvi igralec za vsako potezo ki jo lahko stori pogleda kaj je minimalen dobiček ki ga dobi, nato pa izmed minimumov izbere tisto ki mu prinese največ, torej bo

$$\max_{x}\min_{y}x^{T}Ay$$

Za drugega igralca očitno potem pomeni da išče

$$\min_{y}\max_{x}x^{T}Ay$$


***

**Čista strategija** je strategija kjer velja $x_{i} = 1, x_{i'} = 0 \,;\; i' \neq i$ oz. je strategija kjer vedno izberemo $i$-to strategijo.


Če drugi igralec izbere čisto strategijo - recimo pri indeksu $j$ - dobimo

$$A = [a_{1},...,a_{j},...,a_{n}]$$


$$x^{T}Ay = x^{T}a_{j} = \sum_{i=1}^{n}a_{ij}x_{i}$$

> Naj bo $x$ fiksiran. Potem je
> $$\min_{y} x^{T}Ay = \min_{j=1,...,m} \sum_{i=1}^{n}a_{ij}x_{i}$$
>>[!|dokaz]+ Dokaz:
>>Vemo da je $\min_{y}x^{T}Ay \leq \min_{j=1,...,m} \sum_{i=1}^{n}a_{ij}x_{i}$.
>>
>>Naj bo
>>
>>$$\min_{j} \sum_{i=1}^{n}a_{ij}x_{i}=s$$
>>
>>in
>>
>>$$x^{T}Ay = \sum_{j=1}^{m}\left(\sum_{i=1}^{n}a_{ij}x_{i}\right)y_{j}$$
>>
>>$$ $$
>>
>>$$\sum_{i=1}^{n}a_{ij}x_{i} \geq s$$
>>
>>$$ $$
>>
>>$$\Rightarrow x^{T}Ay = \sum_{j=1}^{m}\left(\sum_{i=1}^{n}a_{ij}x_{i}\right)y_{j} \geq \sum_{j = 1}^{m}sy_{i} = s$$
>>
>>Torej je $\min_{y} x^{T}Ay \geq s$
>>
>>Torej mora biti $\min_{y} x^{T}Ay = \min_{j=1,...,m}\sum_{i=1}^{n}a_{ij}x_{i}$.

To nam pove da je optimalna strategija vedno enaka neki čisti strategiji oz. da če obstaja optimalna strategija bo obstajala tudi čista optimalna strategija z istim izidom.


Prvi igralec torej išče

$$\max_{x}\min_{y} x^{T}A y = \max_{x}\min_{j} \sum_{i=1 }^{n} a_{ij}x_{i}$$
$$\sum_{i=1}^{n}x_{i} = 1$$
$$x_{i} \geq 0$$

*kar drži po trditvi*

in podobno išče drugi igralec

$$\min_{y}\max_{x}x^{T}Ay = \min_{y}\max_{i} \sum_{j=1}^{m}a_{ij}y_{j}$$
$$\sum_{j=1}^{m}y_{j} = 1$$
$$y_{j} \geq 0$$

Edini problem je še da pri prvemu igralcu

$$\min_{j} \sum_{i=1}^{n}a_{ij}x_{i}$$

ni linearen program.

Problem za prvega pa bo ekvivalenten

$$\max s$$

p.p.

$$s \leq \sum_{i=1}^{n}a_{ij}x_{i} \,;\; j = 1,...,m $$
$$\sum_{i=1}^{n}x_{i}= 1$$
$$x_{i}\geq 0 \,;\; i = 1,...,n $$

Za drugega igralca pa velja

$$\min t$$

p.p.

$$t \geq \sum_{j=1}^{m}a_{ij}y_{j} \,;\; i=1,...,n$$
$$\sum_{j=1}^{m}y_{j} \geq 0$$
$$y_{j}\geq 0 \,;\; j = 1,...,m$$

> Vemo da je
> $$\max_{x}\min_{y}x^{T}Ay \leq \min_{y}\max_{x}x^{T}Ay$$
> 
> in vemo da sta oba problema vedno dopustna.
> 
> Iz tega vemo da sta oba vedno optimalna.
> 
> In po krepkem izreku vemo da je optimalna vrednost obeh problemov enaka.


Optimalni vrednosti pravimo **vrednost igre**.

Če je vrednost igre $0$ potem rečemo da je igra poštena.

Da preverimo optimalnost $x^{*}, y^{*}$ najprej preverimo dopustnost in še da je 

$$\min_{j} \sum_{i=1}^{n}a_{ij}x_{i} = \max_{i}\sum_{j=1}^{m}a_{ij}y_{j}$$



***

Matrična igra je **simetrična** če velja $-A = A^{T}$.

> Simetrična igra je poštena.  Njena vrednost je enaka 0. 
>>[!|dokaz]+ Dokaz: 
> > $$v = \max_x \min_y x^T Ay = \max_x \min_y x^T (-A^T y)$$
> > $$= \max_x \min_y -y^T Ax = -\min_x \max_y y^T Ax$$
> > $$= -\min_y \max_x x^T Ay = -v$$
> > $$\Rightarrow v = 0$$

> Če ima $A$ sedlo potem je $i$ optimalna strategija za prvega igralca in $j$ optimalna strategija drugega.
> 
> >[!|dokaz]+ Dokaz:
> > $$x = (0,...,1,...,0), y = (0,...,1,...0)$$
> > 
> > Preverimo če velja $$\min_{j}\sum_{i=1}^{n}a_{ij} x_{i} = \max_{i}\sum_{i=1}^{m}a_{ij}y_{j}$$
> > $$\min_{j} a_{i_{0}j} = \max_{i} a_{ij_{0}} =a_{i_{0}j_{0}}$$


***

**Dominacija**

Rečemo da vektor $x$ dominira $x'$ če je $\forall  i :x_{i} \geq x_{i}'$.

Naj bo $A$ plačilna matrika.
Če $i$-ta vrstica dominira $i'$-to vrstico, dobimo isto optimalno vrednost, če zbrišemo $i'$-to vrstico. 

Če $j$-ti stolpec dominira $j'$-ti stolpec, dobim isto optimalno vrednost, če zbrišemo $j$-ti stolpec.


> Naj bo $A$ plačilna matrika dimenzije $m \times n$. Optimalno vrednost igre $v$ določimo z:
> $$v = \max_{x \in X} \min_{y \in Y} x^T A y = \min_{y \in Y} \max_{x \in X} x^T A y$$
> 
> kjer velja $\sum_{}^{}x = \sum_{}^{}y = 1, x_{i},y_{i}>0$.
> 
> Če vrstica $x_{i}$ dominira $x_{i'}$ potem se vrednost igre ne spremeni če jo izbrišemo.
> >[!|dokaz]+ Dokaz:
> >
> > Igralec 1 želi maksimizirati svoj donos. Naj bo $x = (x_1, \dots, x_{i'}, \dots, x_m)^T$ poljubna mešana strategija igralca 1, kjer je $x_{i'} > 0$.
> > Definirajmo novo strategijo $\tilde{x}$, v kateri vso verjetnost iz $i'$-te vrstice prenesemo v $i$-to vrstico:
> > *   $\tilde{x}_i = x_i + x_{i'}$
> > *   $\tilde{x}_{i'} = 0$
> > *   $\tilde{x}_k = x_k$ za vse ostale $k$.
> > 
> > Primerjajmo pričakovana donosa za poljubno strategijo $y$ igralca 2:
> > 
> > $$\tilde{x}^T A y - x^T A y = \sum_{j=1}^n y_j (\tilde{x}^T A_{\cdot, j} - x^T A_{\cdot, j})=$$
> > $$= \sum_{j=1}^n y_j [ (x_i + x_{i'}) A_{i,j} + 0 \cdot A_{i',j} - (x_i A_{i,j} + x_{i'} A_{i',j}) ]=$$
> > $$ = \sum_{j=1}^n y_j [ x_{i'} (A_{i,j} - A_{i',j}) ]$$
> > 
> > Ker po predpostavki velja $A_{i,j} \ge A_{i',j}$ in so $y_j, x_{i'} \ge 0$, je razlika $\ge 0$. To pomeni, da je strategija $\tilde{x}$ vsaj tako dobra kot $x$ (ali boljša).
> > Zato obstaja optimalna strategija $x^*$, kjer je $x^*_{i'} = 0$. Izbris vrstice $i'$ torej ne spremeni optimalne vrednosti igre.
> 


Dominacija stolpcev deluje analogno
