Izvajanje programa je analogno **iskanju dokaza**.

Uoprabljamo **hornove formule**

$$\forall x_{1},...,x_{m}\,. (\phi_{1}\, \land ... \land \,\phi_{n} \Rightarrow \psi)$$

Kjer so $\phi_{1},...,\phi_{n}$ in $\psi$ **osnovne formule** oblike

$$P(t_{1},...,t_{m})$$

kjer je $P$ **relacija** in $t_{1},...,t_{m}$ **termi**, ki so lahko sestavljeni iz konstant, funkcijsih simbolov in spremenljivk.

Primer:

```
less(
	plus(
		times(X,X), 
		times(Y, Y)
	),
		times(succ(succ(zero)),
		times(X, Y)
	)
)
```

je program ki nam pove ali je

$$X^{2} + Y^{2} < 2XY$$

Če nimamo pogojev imamo **dejstvo**

$$\forall x_{1},...,x_{m}\,. \psi$$

Če imamo formulo brez kvantifikatorjev - torej samo s konstantami dobimo

$$\phi_{1},...,\phi_{m} \Rightarrow \psi$$

Funkcije definiramo kot

$$f(x) = y \Leftrightarrow f(x,y)$$

**Primer:** Vsoto predstavimo kot 

$$x+y=z \Leftrightarrow \text{vsota}(x,y,z)$$

$$\forall n : \text{vsota}(n,0,n)$$
$$\forall k,m,n : \text{vsota(k,m,n)} \Rightarrow \text{vsota}(k,\text{succ }m, \text{succ }n) $$

**Primer:** Množenje predstavimo kot

 $$\forall n.\text{produkt}(n,0,0)$$
 $$\forall k,m,n,p.(\text{produkt(k,m,n)}\land \text{vsota}(k,n,p) )\Rightarrow \text{produkt}(k,\text{succ }m, n)$$

**Opomba:** Negacije in eksistence se ne da izraziti s Hornovimi formulami.

***

**Logično programiranje**

V logičnem programiranju je program podan s seznamo pravil oz. Hornovih formul

$$H_{1},...,H_{k}$$

in poizvedbe $G$ oblike 

$$G = \exists y_{1},...,y_{n}.P(t_{1},...,t_{m})$$

Zanima nas ali velja $H_{1},...,H_{k} \Rightarrow G$.
*Zanima nas ali iz predpostavk $H_{i}$ lahko sklepamo da obstajajo elementi $y_{i}$ in pripadajoči termi $t_{i}$ da velja $P$.*

**Primer:**

$$H_{1}: \text{parent}(\text{Jože, Marija})$$
$$H_{2}: \text{parent}(\text{Marija, Ana})$$
$$H_{3}: \forall x,y,z.(\text{parent}(x,y) \land \text{parent}(y,z) \Rightarrow \text{grandparent}(x,z))$$

zanima nas pa

$$G : \exists Y.\text{grandparent}(Y,\text{Ana}) $$

Vidimo da je $G$ združljiv s sklepom iz $H_{3}$ torej ga lahko razdelimo na $\text{parent}(Y,x) \land \text{parent}(x,\text{Ana})$.

Sedaj lahko preverimo če za kateri $x$ velja $\text{parent}(x,\text{Ana})$ in vidimo da je lahko $x = \text{Marija}$.
Sedaj preverimo če velja $\text{parent}(Y,\text{Marija})$, kjer vidimo da je $Y$ lahko $\text{Jože}$.

<br>

Naj bo $G$ poizvedba

$$G = \exists y_{1},...,y_{n}.P(t_{1},...,t_{m})$$

V seznamu predpostavk $H_1, \dots, H_m$ poišči prvo formulo, ki je oblike

$$ \forall x_1, \dots, x_n . \phi_1 \land \dots \land \phi_m \Rightarrow \psi, $$

katere sklep $\psi$ je **združljiv** s $P(t_1, \dots, t_m)$. To pomeni da lahko za $y_1, \dots, y_n$ vstavimo take vrednosti $u_1, \dots, u_n$ in za $x_1, \dots, x_n$ take vrednosti $v_1, \dots, v_m$, da sta formuli

$$ P(u_1, \dots, u_n) $$

in

$$ \psi(v_1, \dots, v_m) $$

enaki. Možno je, da izbira vrednosti $u_1, \dots, u_n$ in $v_1, \dots, v_m$ ni enolična. V tem primeru izberemo *najbolj splošne vrednosti*, ki jih najdemo s postopkom združevanja.

S tem smo poizvedbo predelali na poizvedbe $\phi_1(v_1, \dots, v_m), \dots, \phi_n(v_1, \dots, v_m)$, ki jih rešujemo po vrsti rekurzivno. (Če se v teh poizvedbah pojavljajo spremenljivke, jih obravnavamo, kot da smo jih kvantificirali z $\exists$.)

***

**Prolog**

V prologu uporabljamo naslednjo sintakso

*   za $A \land B$ pišemo `A, B`
*   za $A \lor B$ pišemo `A ; B`
*   za $A \Rightarrow B$ pišemo `B :- A` (pozor, zamenjal se je vrstni red, $B \Leftarrow A$!)
*   kvantifikatorjev $\forall$ in $\exists$ ne pišemo, ampak **kvantificirane spremenljivke pišemo z velikimi črkami**
*   **konstante, predikate in funkcije pišemo z malimi črkami**.
* za preverjanje neenakosti pišemo `dif(X,Y)`

Na koncu vsake formule zapišemo piko.

Primer:

```prolog
sodo(zero).
sodo(succ(Y)) :- liho(Y).
liho(succ(X)) :- sodo(X).
```

Datoteko naložimo v interaktivno zanko. Ta nam omogoča, da vpišemo poizvedbo in dobimo odgovor:

```prolog
?- liho(Z).
Z = succ(zero) ;
Z = succ(succ(succ(zero))) ;
Z = succ(succ(succ(succ(succ(zero))))) .
```

Ko nam prolog poda odgovor, lahko z znakom `;` zahtevamo, da išče še naprej. Z znakom `.` zaključimo iskanje.

Za delanje seznamov se uporablja `findall(<Var>, <Predikat>, <List>)`, za list brez duplikatov in z abecedno urejenostjo obstaja tudi `setof(<Var>, <Predicat>, <List>)` da se ne grupira po drugih poljih predikata lahko uporabimo 

```prolog
all_capitals(List) :-
    setof(Capital, Name^ID^Prov^Size^Pop^country(Name, ID, Capital, Prov, Size, Pop), List).
```

kjer ^ označuje izločanje grupiranja tistega polja.

Če hočemo preveriti ali je vrednost šrevilka uporabimo `number(P)`.

Če hočemo sešteti vsa števila iz lista $L$ v spremenljivko $N$ uporabimo `sum_list(L,N)`.

Za matematične operacije se uoprablja `˙is`

```prolog
whoSpeaks(Lang, Country, NumOfSpeakers):-
    country(Country,Id,_,_,_,Pop),
    language(Id,Lang,POS),
    NumOfSpeakers is Pop * POS / 100.
```

