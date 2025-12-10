# Funkcije več spremenljivk

**Odprt interval** $(a,b)$ v realnih številih je definiran kot $\{ x \in \mathbb{R} \,;\; a<x<b\}$.

**Okolica** točke $a$ je vsak odprti interval $(a-\varepsilon, a +\varepsilon)$ oz. množica da velja $\{ x \in \mathbb{R} \,;\; |x-a| <\varepsilon\}$

Točka je **notranja** če velja da obstaja njena okolica, ki vsebuje samo elemente iz množice. 
Točka je **robna** če velja, da za vsako njeno okolico velja da vsebuje vsaj en element iz množice in en element izven množice. 
Točka je **zunanja** če obstaja okolica, ki vsebuje samo elemente izven množice.


Množica je **odprta**, natanko tedaj ko za vsak $a$ obstaja taka okolica $a$, ki je popolnoma vsebovana v množici.
*Vse njene točke so notranje* 
Naj bo $X$ podmnožica $\mathbb{R}$. Množica $A \subset X$ je **odprta v $X$** če obstaja odprta množica $B \subset \mathbb{R}$ tako da velja $A = B \cap X$


Množica je **zaprta** če je komplement odprte. 
*Vsebuje vse svoje robne točke.*
***
> Množica $A$ je zaprta, natanko tedaj ko za vsako zaporedje v $A$ velja, če je $s$ stekališče potem je $s$ element $A$.
> $$ A \text{ je zaprta } \Leftrightarrow  \forall a_{n}\in A : \text{ ima stekališče }s  \Rightarrow s \in A$$
> >[!|dokaz]- Dokaz:
> >$\Rightarrow$
> >
> >**Predpostavimo, da je $A$ zaprta množica.**
> >
> >To pomeni, da je njen komplement $A^c$ odprt. 
> >
> >Vzemimo poljubno zaporedje $\{a_n\}$ v $A$, ki konvergira k $s$. Če bi bilo $s \in A^c$, bi obstajala okolica $s$, ki je v celoti vsebovana v $A^c$. 
> >
> >Ker $\{a_n\}$ konvergira k $s$, bi moralo biti neskončno členov zaporedja v tej okolici, kar pa je nemogoče, ker so vsi člani zaporedja v $A$. Zato mora biti $s \in A$.  
> >
> >$\Leftarrow$
> >
> >**Predpostavimo, da za vsako zaporedje $\{a_n\}$ v $A$, ki konvergira k $s$, velja $s \in A$.**
> >
> >Dokazati želimo, da je $A$ zaprta, torej da je $A^c$ odprta. Vzemimo poljuben $x \in A^c$. 
> >
> >Če bi vsaka okolica $x$ vsebovala elemente iz $A$, bi lahko konstruirali zaporedje v $A$, ki konvergira k $x$. Po predpostavki bi moralo biti $x \in A$, kar je v protislovju z $x \in A^c$. 
> >
> >Kar pomeni da ne velja da vsaka okolica $x$ vsebuje elemente iz $A$.
> >
> >Zato mora obstajati okolica $x$, ki je v celoti vsebovana v $A^c$, kar pomeni, da je $A^c$ odprta in posledično $A$ zaprta.

^4ca9f3
***
Množica je **kompaktna** če je zaprta in omejena hkrati.
***
> Množica $A$ je kompaktna natanko tedaj ko za vsako zaporedje v $A$ velja da ima stekališče v $A$.
> $$A \text{ je kompaktna } \Leftrightarrow \text{ vsako } a_{n} \in A \text{ ima stekališče v } A$$
> 
> >[!|dokaz]- Dokaz:
> >
> > $\Rightarrow$
> > 
> > **Predpostavimo da je $A$ kompaktna**
> > 
> > Vzamemo poljubno zaporedja $a_n$. 
> > 
> > Kompaktna množica je zaprta in omejena. 
> > 
> > Če je zaporedje omejeno v $\mathbb{R}^{n}$ ima vsaj eno stekališče. 
> > 
> > Ker je $A$ zaprta mora le to ležati v $A$. 
> > 
> > Torej ima zaporedje $a_n$ stekališče v $A$.
> > 
> > $\Leftarrow$
> > 
> > **Predpostavimo da ima vsako zaporedje v $A$ stekališče v $A$**
> > 
> > **Zaprtost:** Vzamemo poljubno zaporedje $a_{n}$, ki konvergira k $a$. Ker ima vsako zaporedje v $A$ stekališče v $A$ mora biti $a$ stekališče $a_{n}$, torej je $a \in A$, kar pomeni da je množica zaprta. 
> > 
> > *Izhaja iz izreka o zaprtih množicah in stekališčih.*
> > 
> > **Omejenost:** Recimo da $A$ ni omejena. Potem obstaja zaporedje za katerega velja da je $a_{n} \rightarrow \infty$. Takšno zaporedje nima stekališča v $A$, kar je prostislovje s predpostavko, torej mora biti $A$ omejena.
***
**Evklidski prostor **

$$\mathbb{R}^{k} = \{ x = (x_1,...,x_{k}) \;;\; x_i \in \mathbb{R} \}$$

je vektorski prostor, kjer definiramo seštevanje po komponentah, množenje s sklarjem po komponentah in dolžino oz. normo.

**Norma** oz .dolžina je oddaljenost $x$ od $O(\mathbb{R}^n)$
$$\Vert x \Vert = \sqrt[]{x_{1}^{2}+...+x_{k}^{2}}$$

Razdalja med dvema točkama pa je

$$\Vert x -y\Vert = \sqrt[]{(x_{1}-y_{1})^{2}+ ...+ (x_{k}-y_{k})^2}$$

Definirana je tudi **trikotniška neenakost**

$$\Vert x+y \Vert \leq \Vert x \Vert + \Vert y \Vert$$

$$\left| \Vert x \Vert - \Vert y \Vert \right| \leq \Vert x+y \Vert$$


**Odprta krogla** s središčem v $a$ in radijem $r$ v $\mathbb{R}^{k}$ je $K(a, r) = \{ x \in \mathbb{R}^{k} \;;\; \Vert x-a \Vert < r\}$

**Epsilonska okolica** točke $x$ je odprta krogla $K(x, \varepsilon)$, $\varepsilon > 0$

Množica je **omejena**, če obstaja $M > 0$, da je $A \subset K(0, M)$ oz. $\Vert x \Vert < \Vert M \Vert$

Množica je **končna**, če ima končno število elementov oz. obstaja bijektivna preslikava $A \rightarrow \{ 1,2,...,n\}$


Točka je **stekališče** **množice** $A$ če vsaka njena okolica seka $A\backslash \{x\}$.

$$K(x, \varepsilon) \cap (A\backslash \{ x\}) \neq \emptyset$$

*Točka je stekališče množice $A$ če za vsako njeno okolico velja da vsebuje neskončno členov množice*

Točka $a$ je **izolirana točka**, če ni stekališče.
***
> Vsaka točka v zaprti množici je limita nekega zaporedja v množici.
> >[!|dokaz]- Dokaz:
>>Za vsako točko $x$ konsturiramo zaporedje tako da za vsak $n$ velja da je $x_{n}$ bližje kot $\frac{1}{n}$
>>$$\forall n : \Vert x_{n}-x \Vert < \frac{1}{n}$$
>>Po definiciji zaprtosti, ker je $x$ limita zaporedja $x_{n}$, ki so v množici, potem je $x$ v množici in hkrati limita zaporedja.

***



**Zaporedje v $\mathbb{R}^{k}$** je preslikava

$$\mathbb{N} \rightarrow \mathbb{R}^{k}$$
$$n \mapsto (x_{1}^{n},...,x_{k}^{n})$$

**Limita** $a_n$ je $a$, če $\forall \varepsilon>0 \;\; \exists n_{0} \,\ni: n>n_{0} :  \Vert a-a_{n} \Vert < \varepsilon$
***
> Če zaporedje konvergira k $L$, potem vsako podzaporedje konvergira k $L$
> >[!|dokaz]- Dokaz:
> > **Naj bo $a_{n}$ zaporedje ki konvergira k $L$ in $a_{n_{j}}$ poljubno podzaporedje. Naj bo $n_{j}$ strogo naraščujoče.**
> > 
> > Velja da za vsak $\varepsilon > 0$ obstaja $N$ da za vsak $n > N$
> > 
> > $$\Vert a_{n} - L \Vert < \varepsilon$$
> > 
> > Ker je $n_{j}$ strogo naraščujoče obstaja tak $J$ tako da je za vsak $j > J$ velja $n_{j} > N$, torej za vse $j > J$ velja
> > 
> > $$\Vert a_{n_{j}} - L \Vert < \varepsilon$$
***
Zaporedje ima **limito v neskočnosti**, če velja da so za vsak $M > 0$ vsi členi zaporedja od nekega indeksa naprej zunaj $K(0, M)$.

**Stekališče** $s$ zaporedja $a_{n}$ je če vsaka njegova okolica vsebuje neskončno elementov.
*Je stekališče, če obstaja podzaporedje, ki konvergira k $s$.*
***
> Vsako konvergetno zaporedje je omejeno in ima natanko 1 stekališče, ki je njegova limita.
> 
> >[!|dokaz]- Dokaz:
> >
> >1.$\;$ Vsako konvergentno zaporedje je omejeno:
> >
> > **Vzamemo konvergentno zaporedje $a_{n}$**
> > 
> > Pomeni da za vsak $\varepsilon$ obstaja $n_{0}$, da so vsi členi od tam naprej v neki okolici limite $L$.
> > 
> > Če razdelimo zaporedje na del od $n_{0}$ naprej in nazaj, vemo da je eno omejeno v okolici $L$, drugo pa je končno, končno zaporedje pa je **omejeno**.
> > 
> > 2.$\;$ Zaporedje ima limito $L$ $\Leftrightarrow$ $L$ je edino stekališče zaporedja
> > 
> > $\Rightarrow$
> > 
> > **Predpostavimo da ima limito $L$**
> > 
>> Predpostavimo da obstaja drugo stekališče. 
>> 
>> Potem obstaja podzaporedje, ki konvergira k tej limiti.
>> 
>> Ker $a_n$ konvergira k $L$ mora tudi vsako podzaporedje konvergirati k $L$. (ref.)
>> 
>> 
>> To je protislovje, ker lahko vzmamemo dovolj majhen epsilon da sta množici disjunktni, element zaporedja pa ne more biti hkrati v dveh disjunktnih množicah. Torej je limita edino stekališče.
>> 
> > $\Leftarrow$ 
> > 
> > **Predpostavimo da je $L$ edino stekališče zaporedja.**
> > 
> > Ker vemo, da je v vsaki $\varepsilon$ okolici $L$ neksončno členov, potem mora biti zunaj okolice končno členov. Torej mora obstajati končno število elementov za katere velja da niso v okolici. 
> > 
> > Naj bo $N$ indeks zadnjega elementa izven okolice. To pomeni da za vse člene $n>N$ velja da so v $\varepsilon$ okolici $L$ oz. $|L - a_{n}| < \varepsilon$ kar je definicija limite.
***

> Vsako omejeno zaporedje ima stekališče
> 
> $$ a_{n} \text{ je omejeno } \Leftrightarrow a_{n}\text{ ima stekališče}$$
> 
> >[!|dokaz]- Dokaz Bolzano-Weierstrassovega izreka:
> >
> >**Naj bo $(a_n)$ omejeno zaporedje realnih števil.** 
> >
> >To pomeni, da obstajata takšni realni števili $m$ in $M$, da za vsak člen zaporedja velja:
> >$$ m \leq a_n \leq M \quad \text{za vse } n \in \mathbb{N}.$$
> > Začnemo z intervalom $I_0 = [m, M]$, ki vsebuje vse člene zaporedja $(a_n)$.
> > Interval $I_0$ razdelimo na dva sklenjena podintervala: $[m, \frac{m+M}{2}]$ in $[\frac{m+M}{2}, M]$.
> >Vsaj eden od teh dveh podintervalov vsebuje neskončno členov zaporedja $(a_n)$. Izberemo ta podinterval in ga označimo z $I_1$.
> > Postopek ponavljamo: vsak interval $I_k$ razdelimo na dva sklenjena podintervala in izberemo tistega, ki vsebuje neskončno členov zaporedja. Tako dobimo zaporedje intervalov $I_0 \supseteq I_1 \supseteq I_2 \supseteq \dots$, kjer je dolžina intervala $I_k$ enaka $\frac{M - m}{2^k}$.
> >
> > V vsakem intervalu $I_k$ izberemo en člen zaporedja $(a_n)$, ki pripada temu intervalu. Ker vsak $I_k$ vsebuje neskončno členov, lahko vedno izberemo nov člen, ki še ni bil izbran v prejšnjih korakih.
> >Tako dobimo podzaporedje $(a_{n_k})$, kjer je $a_{n_k} \in I_k$ za vsak $k$.
> >
> >
> >Ker so intervali $I_k$ vedno manjši (njihova dolžina konvergira k 0) in se vedno bolj "zožajo" okoli neke točke, obstaja točka $L$, ki je presečišče vseh intervalov $I_k$.
> >Podzaporedje $(a_{n_k})$ konvergira k $L$, saj so vsi členi $a_{n_k}$ vsebovani v intervalih $I_k$, ki se zožujejo okoli $L$.
> >
> >
> >Točka $L$ je stekališče zaporedja $(a_n)$, saj obstaja podzaporedje $(a_{n_k})$, ki konvergira k $L$.

***

> Stekališče zaporedja je limita konvergentnega podzaporedja
> >[!|dokaz]- Dokaz:
> >**Naj bo $L$ točka, za katero velja, da v vsaki $\epsilon$-okolici točke $L$ leži neskončno členov zaporedja $(a_n)$.** 
> >
> >Potem lahko konstruiramo podzaporedje $(a_{n_k})$, ki konvergira k $L$, na naslednji način:
> >
> >Izberemo $\epsilon = 1$. V okolici $L$ z radijem $1$ obstaja neskončno členov zaporedja $(a_n)$. Izberemo poljuben člen iz te okolice in ga označimo z $a_{n_1}$.
> >
> > Nato izberemo $\epsilon = \frac{1}{2}$. V okolici $L$ z radijem $\frac{1}{2}$ obstaja neskončno členov zaporedja $(a_n)$. Izberemo člen $a_{n_2}$, kjer je $n_2 > n_1$, da zagotovimo, da gre za podzaporedje.
> >
> >Postopek ponavljamo za $\epsilon = \frac{1}{k}$ za vsak $k \in \mathbb{N}$. V vsakem koraku izberemo člen $a_{n_k}$, kjer je $n_k > n_{k-1}$, tako da $|a_{n_k} - L| < \frac{1}{k}$.
> >
> >Tako konstruirano podzaporedje $(a_{n_k})$ konvergira k $L$, saj za vsak $\epsilon > 0$ obstaja takšen $K$, da za vse $k \geq K$ velja:
> >$$|a_{n_k} - L| < \frac{1}{k} \leq \epsilon.$$
***

> Če so $K_{1},...,K_{k}$ kompaktne je kompaktna $K_{1} \times...\times K_{k}$ kompaktna v $\mathbb{R}^{k}$.
> >[!|dokaz]- Dokaz:
> >
> >Vsaka množica $K_{i}$ ($i = 1, 2, \dots, k$) je kompaktna v $\mathbb{R}$. Toje  ekvivalentno temu, da je vsaka $K_{i}$ zaprta in omejena.
> >
> > **Zaprto:** Element množice $K$ naj bo $(x_{1},...,x_{k})$ in naj velja da $x_{1} \in K_{1},...,x_{k} \in K_{k}$. Ker so $K_{i}$ množice zaprte vemo da je $x_{i}$ limita nekega zaporedja v množici $K_{i}$. Torej je $(x_{1},...,x_{k})$ limita nekega zaporedja $(x_{1}^{(n)},...,x_{k}^{(n)})$ kar je definicija zaprtosti.
> > 
> > Zato je $K$ zaprta.
> > 
> > **Omejeno:** Kartezični produkt omejenih množic je omejen. Ker je vsaka $K_i$ omejena, obstaja neka konstanta $M_i > 0$, da velja $|x_i| \leq M_i$ za vsak $x_i \in K_i$. Potem je vsak vektor $(x_1, x_2, \dots, x_k) \in K$ omejen z:
> >  $$ \|(x_1, x_2, \dots, x_k)\| \leq \sqrt{M_1^2 + M_2^2 + \dots + M_k^2}.$$
> >  Zato je $K$ omejena.
   
### Funkcije več spremenljivk


Funkcije več spremenljivk so funkcije, odvisne od dveh ali več spremenljivk. Slikajo iz $\mathbb{R}^{k}$ v $\mathbb{R}$, kjer je $k \geq 2$.

Graf funkcije $f$ je množica 

$$\Gamma = \{ (x, f(x)) \;;\; x \in D \}$$
$$\Gamma  \subset \mathbb{R}^{k} \times \mathbb{R} = \mathbb{R}^{k+1}$$

**Defincijsko območje** je množica vrednosti neodvisnih spr., za katere je $f$ definirana.

**Kodomena** je množica v katero funkcija slika svoje elemente, ta pa lahko vsebuje elemente, ki niso z definicijskega območja.

**Zaloga vrednosti** je množica vseh dejanskih vrednosti, ki jih funkcija zazvzame.

**Izolipse** so krivulje, ki povezujejo točke z enako vrednostjo neke funkcije dveh spremenljivk. *\[ "isos" (enak) in "lipsa" (vrednost)]*
*Izolipsa za dano $f(x,y)$ je množica točk za katero velja $f(x,y) = C$.*

Izolipse se ne sekajo, ker bi drugače to pomenilo da ima $f$ dve različni vrednosti pri istem $x$.

Goste izolipse nakazuje strmost, redke položnost.

Izolipse so tudi presek grafa z ravnino.

**Limita funkcije** naj bo $(a,b) \in \mathbb{R}^k$ **stekališče**. Potem velja da je $L$ limita funkcije če velja

$$ \forall  \varepsilon > 0\;\; \exists \delta > 0 \;\;\forall (x,y) \in D : $$ 
$$ 0 < \Vert  (x,y)-(a,b)\Vert < \delta \Rightarrow   | f(x,y) - L | < \varepsilon$$

Desna in leva limita v večdimnezijah nimata pomena.
**Limita v izolirani točki ne obstaja**.

***

> Če obstaja limita je enolična
> >[!|dokaz]- Dokaz:
> > Dokaz je analogen tistemu z eno spremenljivko. 
> > 
> > **Predpostavimo da obstajata 2 limiti.** 
> > 
> > Izberemo 2 disjunktni okolici teh limit.
> > Ker velja da so vsi členi od neke točke naprej v eni od teh, nastane protislovje saj bi za obe limit moralo veljati da so členi v eni okolici hkrati v drugi, ti sta pa disjunktni.

***

> Limita vsote, razlike, produkta in kvocienta funkcij je enaka vsoti, razliki, produktu, kvocientu limit funkcij.
> >[!|dokaz]- Dokaz:
> >Naj bosta $f(x,y)$ in $g(x,y)$ funkciji dveh spremenljivk, ki imata limiti, ko $(x,y) \to (a,b)$:
> >
> >$$\lim\limits_{(x,y) \to (a,b)} f(x,y) = L \quad \text{in} \quad \lim\limits_{(x,y) \to (a,b)} g(x,y) = M.$$
> >Potem je limita **vsote** funkcij:
> >
> >$$\lim\limits_{(x,y) \to (a,b)} [f(x,y) + g(x,y)] = L + M.$$
> >
> >
> >Za vsak $\varepsilon > 0$ obstajata $\delta_1 > 0$ in $\delta_2 > 0$, tako da:
> >
> >$$ \Vert (x,y) - (a,b) \Vert < \delta_1 \Rightarrow |f(x,y) - L| < \frac{\varepsilon}{2}, $$
> >$$ \Vert (x,y) - (a,b) \Vert < \delta_2 \Rightarrow |g(x,y) - M| < \frac{\varepsilon}{2}. $$
> >
> >Izberimo $\delta = \min(\delta_1, \delta_2)$. Potem za $\Vert (x,y) - (a,b) \Vert < \delta$ velja:
> >
> >$$ |f(x,y) + g(x,y) - (L + M)| \leq |f(x,y) - L| + |g(x,y) - M| < \frac{\varepsilon}{2} + \frac{\varepsilon}{2} = \varepsilon. $$
> >
> >Torej, limita vsote je res $L + M$.
> >
> >Podobno kot pri vsoti velja:
> >
> >$$\lim\limits_{(x,y) \to (a,b)} [f(x,y) - g(x,y)] = L - M.$$
> >
> >Dokaz je podoben kot pri vsoti, le da uporabimo:
> >
> >$$ |f(x,y) - g(x,y) - (L - M)| \leq |f(x,y) - L| + |g(x,y) - M|. $$
> >Za **produkt** funkcij velja:
> >
> >$$\lim\limits_{(x,y) \to (a,b)} [f(x,y) \cdot g(x,y)] = L \cdot M.$$
> >
> >$$ |f(x,y) \cdot g(x,y) - L \cdot M| = |f(x,y) \cdot g(x,y) - f(x,y) \cdot M + f(x,y) \cdot M - L \cdot M| $$
> >$$\leq |f(x,y)| \cdot |g(x,y) - M| + |M| \cdot |f(x,y) - L|. $$
> >
> >Ker je $f(x,y)$ omejena v okolici $(a,b)$ (saj ima limito $L$), lahko izberemo $\delta$, tako da oba člena postaneta manjša od $\frac{\varepsilon}{2}$.
> >
> >Za **kvocient** funkcij velja (pod pogojem, da je $M \neq 0$):
> >$$\lim\limits_{(x,y) \to (a,b)} \frac{f(x,y)}{g(x,y)} = \frac{L}{M}.$$
> >
> >Najprej pokažemo, da je $\frac{1}{g(x,y)}$ omejena v okolici $(a,b)$, saj $M \neq 0$. Nato uporabimo:
> >
> >$$\left| \frac{f(x,y)}{g(x,y)} - \frac{L}{M} \right| = \left| \frac{f(x,y) \cdot M - g(x,y) \cdot L}{g(x,y) \cdot M} \right|.$$
> >
> >Števec ocenimo s podobno metodo kot pri produktu, imenovalec pa je omejen, ker $g(x,y)$ ne more biti poljubno blizu 0.
***
Funkcija je **zvezna** v $(a,b)$, če velja

$$\forall \varepsilon > 0, \exists \delta > 0,  \forall (x,y) \in D$$
$$\Vert (x,y)-(b,a) \Vert < \delta \Rightarrow \Vert f(x,y)-f(a,b) \Vert < \varepsilon$$

Pogoj da je stekališče tukaj ni potreben. Če je točka **izolirana** je avtomatično zvezna v njej.

Če je graf zvezen v $(a,b)$ in je $(a,b)$ stekališče potem je limita v točki $(a,b)$ enaka vrednosti $f(a,b)$.

Funkcija je zvezna če je zvezna v vsaki točki na svojem $D$.

***
> Vsota, razlika, prdoukt in kvocient zveznih funkcij je zvezna funkcija. 
>>[!|dokaz]- Dokaz:
>> Če je $a$ izolirana točka je trivialno resnično
>> 
>> **Predpostavimo da sta obe funkciji zvezni**
>> 
>>  $$ \lim (f(x) + g(x)) = \lim f(x) + \lim g(x)$$
>>  Zaradi zveznosti obeh funkcij velja
>>  
>> $$\lim f(x) + \lim g(x) = f(x) + g(x)$$
>> 
>> Torej je 
>> $$ \lim (f(x) + g(x)) = f(x) + g(x)$$
***
**Vsaka elementarna funkcija je zvezna funkcija.**

**Kompozitum** funkcij je slikanje preko več funkcij zapored.

$$A \subset \mathbb{R}^{n}, B \subset \mathbb{R}^{m}, C \subset \mathbb{R}^{p}$$
$$f: A \rightarrow B$$
$$g: B \rightarrow C$$
$$f(x_{1},...,x_{n}) = (f_{1}(x_{1},...,x_{n}),...,f_{m}(x_{1},...,x_{n})) \text { - vektorska funckija}$$
$$g \circ f = g(f(x_{1},x_{2},...,x_{n})) : A \rightarrow C$$

***
> Naj bo $f$ zvezna v $a$ in $g$ zvezna v $f(a)$. Potem je zvezna $g(f(a))$.
> >[!|dokaz]- Dokaz:
> >
> >**Predpostavimo da sta $f$ in $g$ zvezni**
> >
> > Ker vemo d je $g$ zvezna v $f(a)$ vemo da za vsako $\varepsilon_{0}$ okolico $g(f(a))$ obstaja taka $\delta_{0}$ okolica  $f(a)$ da se vse vrednosti zvezno slikajo iz ene v drugo.
> > 
> > Hkrati vemo da je $f$ zvezna v $a$ kar pomeni da za vsako $\varepsilon_{1}$ okolico obstaja $\delta_{1}$ okolica $a$, da se vse vrednosti $\delta_{1}$ okolice zvezno preslikajo v $\varepsilon_{1}$ okolico. 
> > 
> > Sedaj lahko vzamemo tak $\varepsilon_{1}$ enak $\delta_{0}$. Ker za vsako okolico $f(a)$ velja da obstaja zadosten $\delta_{1}$ da se vse vrednosti zvezno preslikajo v $\varepsilon_1$, velja da se vsi $x$ iz okolice $a$ zvezno preslikajo v okolico $f(a)$, iz le te pa se vse vrednosti zvezno preslikajo v $g(f(a))$.

***

> Če je $a_{n}$ konvergentno zaporedje s členi iz $D$ in limito $a$ v $D$ in je $f$ zvezna v $a$ $\Rightarrow$ $f(a_{n})$ je konvergentno zaporedje z limito v $f(a)$
> >[!|dokaz]- Dokaz:
> >
> >**Predpostavimo da je zaporedje konvergentno in da je $f$ zvezna v $a$**
> >
> > Naj bo $\epsilon > 0$ poljuben.
> > Ker je funkcija $f$ zvezna v točki $a$, po definiciji zveznosti obstaja takšen $\delta > 0$, da za vsak $x$ iz definicijskega območja $D$ velja: če je $|x - a| < \delta$, potem je $|f(x) - f(a)| < \epsilon$.
> > 
> > Ker zaporedje $a_n$ konvergira k $a$, po definiciji konvergence zaporedja za ta $\delta$ obstaja naravno število $N$ takšno, da za vsak $n > N$ velja $|a_n - a| < \delta$.
> > 
> > Za vsak $n > N$ torej velja $|a_n - a| < \delta$. Ker so vsi členi $a_n$ po predpostavki v definicijskem območju $D$ funkcije $f$, lahko uporabimo definicijo zveznosti za $x = a_n$. Iz tega sledi, da je $|f(a_n) - f(a)| < \epsilon$.
> > 
> > Dokazali smo, da za vsak $\epsilon > 0$ obstaja $N$ takšen, da za vsak $n > N$ velja $|f(a_n) - f(a)| < \epsilon$. To pomeni, da zaporedje $f(a_n)$ konvergira k $f(a)$.

***
> $A$ je kompaktna množica in $f: A \rightarrow  \mathbb{R}$ zvezna $\Rightarrow$ $f$ je omejena in doseže svoj minimum in maksimum.
> >[!|dokaz]- Dokaz:
> >
> > Vzemimo poljubno zaporedje $(y_n)$ v $f(K)$.
> > Ker je $y_n \in f(K)$, za vsak $n$ obstaja $x_n \in K$, tako da je $y_n = f(x_n)$
> > Tako dobimo zaporedje $(x_n)$ v $K$.
> > Ker je $K$ kompaktna, ima zaporedje $(x_n)$ konvergentno podzaporedje $(x_{n_k})$, ki konvergira k neki točki $x \in K$.
> > Ker je $f$ zvezna, velja $\lim_{k \to \infty} f(x_{n_k}) = f(x)$.
> > Po definiciji je $y_{n_k} = f(x_{n_k})$, zato podzaporedje $(y_{n_k})$ konvergira k $f(x)$.
> > Ker $x \in K$, je $f(x) \in f(K)$.
> > S tem smo pokazali, da ima vsako zaporedje v $f(K)$ konvergentno podzaporedje, katerega limita leži v $f(K)$, kar pomeni, da je $f(K)$ kompaktna množica.
> > Ker imamo zvezno funkcijo in kompaktno množico sledi da za vsak element kompaktne množice (ki vključuje supremum in infimum) obstaja $x$ ki se slika vanj.

***

Naj bo $U \subset  \mathbb{R}^{k}$ okolica $a$, $f: U \rightarrow \mathbb{R}$.

**Parcialni odvod** funkcije $f$ v točki $a$ na spremenljivki $x_{i}$ je odvod $i$-te koordinate funkcije $x_{i} \mapsto f(a_{1},...,x_{i},...,a_{k})$ v točki $a = (a_{1},...,a_{i},...,a_{k})$.

$$\frac{\partial f}{\partial x_{i}} (a) = \lim_{x_{i} \to a_{i}} \frac{f(a_{1},...,x_{i},...,a_{k}) - f(a_{1},...,a_{i},...,a_{k})}{x_{i}-a_{i}}$$

Funkcije več spremenljivk odvajamo po $i$-ti spremenljivki tako da fiksiramo vse druge točke in odvajamo kot $f$ ene spremenljike.

Rečemo da je funkcija $f$ v toki $a$ **parcialno odvedljiva** na spremenljivko $x_{i}$, če obstaja parcialni odvod funkcije $f$ na spremenljivko $x_{i}$ v točki $a$.

Iz dejstva da obstajajo vsi paricalni odvodi v neki točki pa še **ne sledi, da je funkcija $f$ v tisthi točki zvezna**. To je torej drugače kot pri funkcijah ene spremenljivke.

*Za zveznost mora funkcija iz vseh strani konvergirati proti točki.*

$$\frac{\partial f}{\partial x_{i}}(a) := f_{x_{i}}(a) :=\partial _{x_{i}}f(a) :=\partial _{i}f(a)$$

>[!|dokaz]- Primer:
$$f(x,y) = x^{2}-y^{2}$$
$$\frac{\partial f}{\partial x}(x,y)=2x$$
$$\frac{\partial f}{\partial y}(x,y) = -2y$$

Ker so parcialni odvodi funkcije spet funkcije več spremenljivk, poznamo **parcialne odvode $k$-tega reda**, če jih lahko odvajamo.

$$\frac{\partial^{2}f}{\partial x^{2}} = \frac{\partial }{\partial x}\left(\frac{\partial f}{\partial x}\right)$$
$$\frac{\partial^{2}f}{\partial x \partial y} = \frac{\partial }{\partial x}\left(\frac{\partial f}{\partial y}\right)$$
$$\frac{\partial^{2}f}{\partial y^{2}} = \frac{\partial }{\partial y}\left(\frac{\partial f}{\partial y}\right)$$
$$ $$
$$f_{xy} = \frac{\partial^{2} f}{\partial y \partial x}$$

> Če mešana parcialna odvoda $\frac{\partial^{2} f}{\partial x \partial y}$ in $\frac{\partial^{2} f}{\partial y \partial x}$ obstajata in sta zvezni funkciji sta med seboj enaka.
> $$\frac{\partial^{2} f}{\partial x \partial y} = \frac{\partial^{2} f}{\partial y \partial x}$$
> >[!|dokaz]- Dokaz:
>>
Izberemo poljubno točko $(a,b)$, kjer obstajata mešana odvoda, ter predpostavimo da bosta $a<x$ in $b<y$ v enačbi
>>
$$(f(x,y)-f(a,y)) - (f(x,b)-f(a,b)) $$ 
$$= (f(x,y)-f(x,b))-(f(a,y)-f(a,b))$$
>>
Zaradi Lagranga vemo da med $x$ in $a$ obstaja $c$ ter med $y$ in $b$ obstaja $d$ tako da lahko uporabimo Lagrangeov izrek in dobimo
>>
$$\frac{\partial f}{\partial x}(c,y)\cdot (x-a) - \frac{\partial f}{\partial x}(c,b)\cdot (x-a)$$
$$= \frac{\partial f}{\partial y}(x,d)\cdot (y-b) - \frac{\partial f}{\partial y}(a,d)\cdot (y-b)$$
>>
Izpostavimo skupne faktorje dobimo
>>
$$\left(\frac{\partial f}{\partial x}\left(c,y\right) - \frac{\partial f}{\partial x}(c,b)\right)\cdot (x-a)$$
$$= \left(\frac{\partial f}{\partial y}\left(x,d\right) - \frac{\partial f}{\partial y}(a,d)\right)\cdot (y-b)$$
>>
Še enkrat uporabimo Lagrangeov izrek
>>
$$\frac{\partial^{2}f}{\partial y \partial x}(c,d') \cdot (y-b) \cdot (x-a) =  \frac{\partial^{2} f}{\partial x \partial y}(c',d) \cdot (x-a) \cdot (y-b) $$
>>
Pokrajšamo $(x-a)(y-b)$. Velja da je $a < c' < x$ in $b < d' < y$. Če konvergira $x \rightarrow a$ in $y \rightarrow b$ velja da tudi $c, c' \rightarrow a$ in $d, d' \rightarrow b$. 
>>
Zaradi zveznosti mešanih odvodov dobimo limiti
>>
$$\frac{\partial^{2}y}{\partial x \partial y}(a,b) = \frac{\partial^{2} f}{\partial y \partial x} (a,b)$$
>
Za odvode višjega reda velja enako
$$\frac{\partial^{3} f}{\partial x^{2} \partial y} = \frac{\partial^{3} f}{\partial x \partial y \partial x} = \frac{\partial^{3} f}{\partial y \partial x^{2}}$$
>
Brez predpostavke da so mešani odvodi zvezni, le-ti med seboj niso nujno enaki. To je torej potreben pogoj.


Pri funkcijah parcialna odvedljivost še ne pomeni prave odvedljivosti.
Funkcija $f: \mathbb{R}^{n}\rightarrow \mathbb{R}$ je v točki $a$ odvedljiva ali diferenciabilna, če je funkcija definirana v neki okolici $a$ in obstaja taka $n$-terica $\mathbf{k}=(k_{1},k_{2},...,k_{n})\in \mathbb{R}^{n}$ da velja

$$\lim_{\Vert h \Vert \to 0} \frac{f(\mathbf{a}+\mathbf{h})-f(\mathbf{a})-\mathbf{k}\mathbf{h}}{\left\Vert h \right\Vert} $$

kjer so $a,k,h$ $n$-terice oz. točke v $\mathbb{R}^{n}$. $kh$ pa je skalarni produkt dveh vektorjev.


Za točko $(a,b)$ lahko definiramo tangentno ravnino $z$ kjer vemo da sta vektorja katera jo sestavljata enaka razliki med $f(a,b)$ in $\frac{\partial f}{\partial x}(a,b) \cdot (x-a)$ ter  $f(a,b)$ in $\frac{\partial f}{\partial x}(a,b) \cdot (y-b)$.

$$z(x,y) = f(a,b) + \frac{\partial f}{\partial x}(a,b)\cdot (x-a)+ \frac{\partial f}{\partial y}(a,b)\cdot (y-b)$$

Nato lahko deifniramo $R_{(a,b)}(x,y)$, ki označuje razliko med funkcijsko vrednostjo in aproksimacijo na ravnini oz. vrednostjo $z(x,y)$.

$$f(x,y) = z_{(a,b)}(x,y) + R_{(a,b)}(x,y) $$
$$:= z + R_{a}(x,y)$$

Funkcija je diferenciabilna v točki $\mathbf{a}=(a,b)$ če velja da je 

$$\lim_{\left\Vert h \right\Vert  \to 0} \frac{R_{\mathbf{a}}(\mathbf{a + h})}{\left\Vert h \right\Vert} = 0 $$

$$\lim_{\left\Vert h \right\Vert  \to 0} \frac{f(a+h_{1},b+h_{2}) - z(a+h_{1},b+h_{2})}{\Vert h \Vert}$$

$$\lim_{\left\Vert h \right\Vert  \to 0} \frac{f(a+h_{1},b+h_{2}) - f(a,b)- \frac{\partial f}{\partial x}(a,b) \cdot (a+h_{1}-a) - \frac{\partial f}{\partial y}(a,b) \cdot (b+h_{2}-b)}{\Vert h \Vert}$$

$$\lim_{\left\Vert h \right\Vert  \to 0} \frac{f(a+h_{1},b+h_{2}) - f(a,b)- \frac{\partial f}{\partial x}(a,b)\cdot h_{1} - \frac{\partial f}{\partial y}(a,b) \cdot h_{2}}{\Vert h \Vert}$$

$$\mathbf{k} = \left(\frac{\partial f}{\partial x}(a,b), \frac{\partial f}{\partial y}(a,b)\right), \mathbf{h} = (h_{1},h_{2}) \rightarrow\text{ (Vektorja)} $$

$$\lim_{\left\Vert h \right\Vert  \to 0} \frac{f(a+h_{1},b+h_{2}) - f(a,b)- \mathbf{k} \cdot \mathbf{h}}{\Vert h \Vert} = 0$$

 >[!|dokaz]- Nepomembno verjetno:
>
$$\lim_{\left\Vert h \right\Vert  \to 0} \frac{f(a+h_{1},b+h_{2}) - f(a,b)}{\Vert h \Vert}- \mathbf{k} \cdot \frac{\mathbf{h}}{\left\Vert h \right\Vert }$$
$$\lim_{\left\Vert h \right\Vert  \to 0} \frac{f(a+h_{1},b+h_{2}) - f(a,b)}{\Vert h \Vert}- \mathbf{k} \cdot \left(\frac{h_{1}}{\left\Vert h \right\Vert} ,\frac{h_{2}}{\left\Vert h \right\Vert }\right)$$
$$\lim_{\left\Vert h \right\Vert  \to 0} \frac{f(a+h_{1},b+h_{2}) - f(a,b)}{\Vert h \Vert}- \mathbf{k} \cdot \mathbf{e_{h}}$$


S tem tudi pridelamo **totalni diferencial.** (za 2 spremenljivki)

$$\mathbf{kh} = df(\mathbf{h}) = f_{x}(a,b)h_{1} + f_{y}(a,b)h_{2}$$

Na tem mestu pa lahko še omenimo da je $\nabla f (a,b) = \mathbf{k}$ formalno pa je **gradient funkcije** vektor parcialnih odvodov vsake osi v $\mathbf{a}$. 

$$\nabla f (\mathbf{a}) = \left(\frac{\partial f}{\partial x_{1}}(\mathbf{a}),...,\frac{\partial f}{\partial x_{k}}(\mathbf{a})\right)$$

Vektor gradienta je vedno pravokoten na izolipso.


**Totalni diferencial** je torej definiran kot skalrani produkt gradienta in vektorja spremembe $x$

$$df = {\nabla f(\mathbf{a})}\cdot  \mathbf{dx}$$

Torej da je funkcija diferenciabilna mora veljati da razmerje med razliko linearne aproksimacije in oddaljenostjo od točke konvergira k 0 bližje kot smo točki. Če bi rekli da konvergira h kateremu drugemu številu bi si zagotavljali da bi v okolici točke imeli zagotovljeno napako naprimer:

$$\lim_{h \to 0}\frac{R(h)}{h} = 0.2$$
$$0.2 \cdot  h = R(h)$$

Za vsako število ($0.2, 0.1, 0.05$) lahko vzamemo neko manjše da bi bila razlika vedno manjša oz. razmerje med oddaljenostjo in razliko vedno manjše zato preprosto rečemo da razmerje limitira proti 0.

Hkrati to pomeni da lahko najdeš poljubno natančno bližnjo točko. Recimo za vsak $h$ lahko najdemo neko drugo $a+h_{1}< a+h$ točko bližje $a$, za katero vemo da velja da bo bolj natančno aproksimirana kot prejšnja. Če bi stvar konvergirala k neki drugi konstanti bi veljalo da v najboljšem primeru naša aproksimacija, bolj kot se bližamo $a$ doseže vrednosti z napako v razmerju $0.2 \cdot h$, kjer bi na isti točki veljalo da lahko dosežemo boljšo aproskimacijo z linearno funkcijo katere razmerje med napako in oddaljenostjo bi konvergiralo k npr. $0.1$.

Malo bolj grafičen način predstavitve je da gledamo graf $R(h)$ in ugotavljamo kdaj je le ta najpoložnejši na točki na kateri aproksimiramo, saj to pomeni da bojo tam vrednosti najbližje vrednosti naše dejanske funkcije. Bolj kot je graf položen, bolje je. Najbolj položen graf ima odvod 0 in zato rečemo da naj odvod grafa $R(h)$ konvergira k $0$ kar je ravno $\frac{R(h)}{h}$. 

Vse nadaljne izpeljave pa pravijo, da ko je funkcija diferenciabilna in obstaja linearna aproksimacija, obstajata vektorja $\nabla f, \mathbf{dx}$, ki aproksimirata funkcijo *(z razliko $R(h)$*. Skalarnemu produktu le teh pravimo totalni diferencial in ga označimo z $df$, z njim pa lahko ocenjujemo funkcije. *($df$ je vrednost aprkosimacije)*.

**Funkcija je diferenciabilna ko velja**

$$\lim_{\left\Vert dx \right\Vert   \to 0} \frac{f(a+dx_{1},b+dx_{2}) - f(a,b)- \mathbf{\nabla f} \cdot \mathbf{dx}}{\Vert dx \Vert} = 0$$


***

> Zvezna funkcija je diferenciabilna če so zvezni njeni parcialni odvodi
>>[!|dokaz]- Dokaz:
>> **Naj bosta $f_{x}$ in $f_{y}$ zvezni**
>> 
>> Definirajmo razliko med dvema točkama
>> 
>> $$\Delta f = f(x+h_{1},y+h_{2})- f(x,y)$$
>> 
>> $$\Delta f = f(x+h_{1},y+h_{2}) -f(x+h_{1},y)+f(x+h_{1},y)-f(x,y)$$
>> 
>> Po Lagrangu sledi da je
>> 
>> $$f(x+h_{1},y+h_{2}) -f(x+h_{1},y) = h_{2} \cdot \frac{\partial f}{\partial y}(\mathbf{\xi_{1}})$$
>> $$\xi_{1} = (x+h_{1}, y + k_{1} \cdot h_{2}) \,;\; k_{1} \in (0,1)$$
>> $$f(x+h_{1},y) -f(x,y) = h_{1} \cdot \frac{\partial f}{\partial x}(\mathbf{\xi_{2}})$$
>> $$\xi_{2} = (x + k_{2} \cdot h_{1}, y ) \,;\; k_{2} \in (0,1)$$
>> 
>> Zaradi zveznosti lahko izrazimo 
>>
>>$$\frac{\partial f}{\partial y}(\mathbf{\xi_{1}}) = \frac{\partial f}{\partial y}({x,y}) + \eta_{1} $$
>>$$\frac{\partial f}{\partial x}(\mathbf{\xi_{2}}) = \frac{\partial f}{\partial x}({x,y}) + \eta_{2} $$
>>In vemo da ko gre $h_{1}$ in $h_{2}$ proti $0$ gresta $\eta_{1}$ in $\eta_{2}$ proti $0$.
>>
>> Sedaj je 
>> $$\Delta f =\left( \frac{\partial f}{\partial y}({x,y}) + \eta_{1}  \right)\cdot h_{2} + \left( \frac{\partial f}{\partial x}({x,y}) + \eta_{2}  \right)\cdot h_{1} $$
>> $$\Delta f =\frac{\partial f}{\partial y}({x,y})\cdot h_{2} +  \frac{\partial f}{\partial x}({x,y})\cdot h_{1}+ \eta_{1}  \cdot h_{2}  + \eta_{2}  \cdot h_{1} $$
>> 
>> To vstavimo v standardno definicijo diferenciabilnosti
>> $$\lim_{\left\Vert h \right\Vert  \to 0} \frac{f(x+h_{1},y+h_{2}) - f(x,y)- \frac{\partial f}{\partial x}(x,y)\cdot h_{1} - \frac{\partial f}{\partial y}(x,y) \cdot h_{2}}{\Vert h \Vert} = 0$$
>> $$\lim_{\left\Vert h \right\Vert  \to 0} \frac{\Delta f- \frac{\partial f}{\partial x}(x,y)\cdot h_{1} - \frac{\partial f}{\partial y}(x,y) \cdot h_{2}}{\Vert h \Vert} = 0$$
>> $$\lim_{\left\Vert h \right\Vert  \to 0} \frac{\frac{\partial f}{\partial y}({x,y})\cdot h_{2} +  \frac{\partial f}{\partial x}({x,y})\cdot h_{1}+ \eta_{1}  \cdot h_{2}  + \eta_{2}  \cdot h_{1} - \frac{\partial f}{\partial x}(x,y)\cdot h_{1} - \frac{\partial f}{\partial y}(x,y) \cdot h_{2}}{\Vert h \Vert} = 0$$
>> $$\lim_{\left\Vert h \right\Vert  \to 0} \frac{ \eta_{1}  \cdot h_{2}  + \eta_{2}  \cdot h_{1} }{\Vert h \Vert} = 0$$
>> To pa limitira k 0 ker vemo da je 
>> $$\left|\eta_{1} \cdot k + \eta_{2} \cdot h \right| \leq |\eta_{1}| \cdot |k |+| \eta_{2}| \cdot |h | $$
>> Ker je $\left|h \right| \leq \sqrt[]{h^{2}+k^{2}}$ in $\left|k \right| \leq \sqrt[]{h^{2}+k^{2}}$
>> je
>> $$\left|\eta_{1} \cdot k + \eta_{2} \cdot h \right|  \leq (|\eta_{1}| + |\eta_{2}|) \cdot  \sqrt[]{h^{2} + k^{2}}$$
>> $$\left|\frac{\eta_{1} \cdot k + \eta_{2} \cdot h }{\sqrt[]{h^{2} + k^{2}}}\right| \leq |\eta_{1}| + |\eta_{2}|$$
>> $$\lim_{\left\Vert h \right\Vert  \to 0} (|\eta_{1}| + |\eta_{2}|) = 0$$
>> $$\Rightarrow $$
>> $$\lim_{\left\Vert h \right\Vert  \to 0} \frac{ \eta_{1}  \cdot h_{2}  + \eta_{2}  \cdot h_{1} }{\Vert h \Vert} = 0$$

***

> Če je funkcija diferenciabilna v $a$ je zvezna v $a$
> >[!|dokaz]+ Dokaz:
> > **Predpostavimo da je funkcija diferenciabilna.**
> > 
> > Da je funkcija zvezna v $a$ mora veljati, da je $a$ izolirana ali pa da je  $\lim_{\left\Vert h \right\Vert  \to 0}f(\mathbf{x}+\mathbf{h}) = f(\mathbf{x})$.
> > 
> > Velja
> > 
> >$$f(a+h)-f(a) = df + R(h)$$
> > $$\lim_{\left\Vert h \right\Vert  \to 0} f(a+h_{1},b+h_{2})-f(a,b)=\lim_{\left\Vert h \right\Vert  \to 0}   \mathbf{k}\mathbf{h} + R(\mathbf{h})$$
> > $$\lim_{\left\Vert h \right\Vert  \to 0} f(a+h_{1},b+h_{2})-f(a,b)= 0$$
> > Torej je funkcija zvezna
***


**Verižno pravilo** pri odvajanju funkcij več spremenljivk nam podaja gradient funkcije po posrednih spremenljivkah.

Naprej poglejmo in izpeljimo pravilo za funkcijo več spremenljivk, posredno odvisno od le ene.

Imamo funkcijo $f: U \rightarrow \mathbb{R}$, kjer je $U \subset \mathbb{R}^k$ in $f$ je diferenciabilna na $U$.
Naj bo $J \subset \mathbb{R}$ odprti interval in $g_{1},...,g_{k}$ funkcije za katere velja $g_{i}: J \rightarrow \mathbb{R}$, naj bodo odvedljive in naj velja da je $\forall t \in U:\mathbf{g(\!t\!)} = (g_{1}(t), ...,g_{k}(t)) \in U$

*Imamo diferenciabilno funkcijo $f$ s $k$ spremenljivkami in imamo $k$ funkcij $g$ z 1 spremenljivkaimo, ki služijo, kot posredne funkcije za $f$.*

Pomembno je dejstvo da so funkcije $g$ funkcije ene spremenljivke.

Potem velja da je odvod funkcije $F({t}) = f(\mathbf{\!g(\!t\!)\!})$ enak

$$F'({t}) = f'(\!{\mathbf{g}(\!t\!)\!})$$
$$\nabla f = \left(\frac{\partial f}{\partial x_{1}},..., \frac{\partial f}{\partial x_{k}}\right) \,,\; dg_{i} = \frac{dg_{i}}{dt}dt$$
$$ $$
$$df = \nabla f \cdot (dg_{1},...,dg_{k}) $$
$$df = \frac{\partial f}{\partial x_{1}}\cdot \frac{dg_{1}}{dt}dt\, +\, ...\,+\, \frac{\partial f}{\partial x_{k}}\cdot \frac{dg_{k}}{dt}dt$$
$$df =\left( \frac{\partial f}{\partial x_{1}}\cdot \frac{dg_{1}}{dt}\, +\, ...\,+\, \frac{\partial f}{\partial x_{k}}\cdot \frac{dg_{k}}{dt} \right)\cdot dt$$
$$\frac{df}{dt} = \frac{\partial f}{\partial x_{1}}\cdot \frac{dg_{1}}{dt}\, +\, ...\,+\, \frac{\partial f}{\partial x_{k}}\cdot \frac{dg_{k}}{dt} $$
$$ $$
$$\frac{df}{dt} = \frac{\partial f}{\partial x_{1}}\!(\mathbf{\!g}(\!t\!)\!)\cdot g_{1}'(\mathbf{t}) + 
... + \frac{\partial f}{\partial x_{k}}\!(\mathbf{\!g}(\!t\!)\!)\cdot g_{k}'(\mathbf{t})$$

*Za funkcijo več spremenljivk, ki je odvisna od 1 spremenljivke $t \in \mathbb{R}$ velja da diferenciabilnost lahko definiramo tudi kot*

$$ \color{light}\frac{df}{dt} = \lim_{\left\Vert h \right\Vert  \to 0}\frac{f(x(t+h), y(t+h))-f(x(t),y(t))}{h} $$

*iz česar lahko na drug način izpeljemo tudi verižno pravilo.*

*Kar smo dobili je v resnici parcialni odvod $f(g(x))$ po prvi spremenljivki, ki pa je v našem primeru edina.*

*Primer funkcije z dvema spremenljivkama posredno odvisna od le ene:*
*https://www.math3d.org/Ee9FRHkSZY*

*Kar se dogaja je da imamo funkcijo za os $x$ in $y$ iz katere lahko sestavimo parametrično krivuljo. Presek krivulje in kompozituma funkcije je naša končna funkcija.*

Poglejmo si še diferenciabilnost kompozicije, kjer sta obe funkciji lahko funkciji več spremenljivk in je $f$ lahko tudi vektorska funkcija.

Preden začnemo moramo vedeti da nam verižno pravilo ne da diferenciala ampak gradient funkcije po posredni spremenljivki.

Ker je diferencial definiran kot skalarni produkt med gradientom in spremembo $x$, bo diferencial funkcije ki slika v več dimenzionalen prostor (vektorske funkcije) le vektor parcialnih odvodov.
Naj velja $f: \mathbb{R}^{n} \rightarrow \mathbb{R}^{m}$

$$f(a+dx) = f(a) + Df(a) \cdot dx + R(dx)$$
$$ $$

$$f(a + dx) = f(a) + 
\begin{bmatrix}
    \frac{\partial f_1}{\partial x_1} (a) & \frac{\partial f_1}{\partial x_2} (a) & \cdots & \frac{\partial f_1}{\partial x_n} (a) \\
    \frac{\partial f_2}{\partial x_1} (a) & \frac{\partial f_2}{\partial x_2} (a) & \cdots & \frac{\partial f_2}{\partial x_n} (a) \\
    \vdots & \vdots & \ddots & \vdots \\
    \frac{\partial f_m}{\partial x_1} (a) & \frac{\partial f_m}{\partial x_2} (a) & \cdots & \frac{\partial f_m}{\partial x_n} (a)
\end{bmatrix}
\begin{bmatrix}
    dx_1 \\ dx_2 \\ \vdots \\ dx_n
\end{bmatrix}
+ R(dx)$$

*$f$ je vektor tako da se po komponentah sešteva oz. imamo vektor  $f$ plus skalarni produkt med matriko in $dx$ ki nam da vektor plus vektor $R$*

Funkcija, ki slika iz $\mathbb{R}^{n}$ v $\mathbb{R}^{m}$ je neka parametričen zapis, ki točke $n$ razdežnega prostora slika v točke $m$ razsežnega prostora.

**Jacobijeva matrika** velikosti $m \times n$ je matrika, ki v $m$ vrsticah vsebuje gradiente za vsako od funkcij z $n$ spremenljivkami.

>[!|dokaz]- Nepomembno:
>
>$$(Dg)(\!f(a)\!) = \begin{bmatrix}
\frac{\partial g_1}{\partial y_1} (f(a)) & \frac{\partial g_1}{\partial y_2} (f(a)) & \cdots & \frac{\partial g_1}{\partial y_m} (f(a)) \\
\frac{\partial g_2}{\partial y_1} (f(a)) & \frac{\partial g_2}{\partial y_2} (f(a)) & \cdots & \frac{\partial g_2}{\partial y_m} (f(a)) \\
\vdots & \vdots & \ddots & \vdots \\
\frac{\partial g_p}{\partial y_1} (f(a)) & \frac{\partial g_p}{\partial y_2} (f(a)) & \cdots & \frac{\partial g_p}{\partial y_m} (f(a))
\end{bmatrix}$$


$$(Df)(a) =
\begin{bmatrix}
\frac{\partial f_1}{\partial x_1} (a) & \frac{\partial f_1}{\partial x_2} (a) & \cdots & \frac{\partial f_1}{\partial x_n} (a) \\
\frac{\partial f_2}{\partial x_1} (a) & \frac{\partial f_2}{\partial x_2} (a) & \cdots & \frac{\partial f_2}{\partial x_n} (a) \\
\vdots & \vdots & \ddots & \vdots \\
\frac{\partial f_m}{\partial x_1} (a) & \frac{\partial f_m}{\partial x_2} (a) & \cdots & \frac{\partial f_m}{\partial x_n} (a)
\end{bmatrix}$$

Kar opazimo je da **Jacobijeva matrika nastopa namesto gradienta.**

Pomaga nam pri računanju vektorja diferenciala vektorske funkcije

$$df = Df(a) \cdot dx$$

kjer je $f$ vektorska funkcija ene spremenljivke.

Jacobijeva matrika ima toliko stolpcev kolikor spremenljivk je funkcija $f$ in toliko vrstic kolikor vektorska je funckija $f$ torej $f_{1},...,f_{k}$. Hkrati velja če imamo vektorsko funkcijo imamo vektor diferencialov in vektor. $dx$ je vektor če ima $f$ več spremenljivk torej $f(x_{1},...,x_{n}) \Rightarrow dx \in R^{n}$.

$$\begin{pmatrix} df_1 \\ df_2 \\ \vdots \\ df_m \end{pmatrix} = \begin{pmatrix}
\frac{\partial f_1}{\partial x_1}(a) & \frac{\partial f_1}{\partial x_2}(a) & \cdots & \frac{\partial f_1}{\partial x_n}(a) \\
\frac{\partial f_2}{\partial x_1}(a) & \frac{\partial f_2}{\partial x_2}(a) & \cdots & \frac{\partial f_2}{\partial x_n}(a) \\
\vdots & \vdots & \ddots & \vdots \\
\frac{\partial f_m}{\partial x_1}(a) & \frac{\partial f_m}{\partial x_2}(a) & \cdots & \frac{\partial f_m}{\partial x_n}(a)
\end{pmatrix} \begin{pmatrix} dx_1 \\ dx_2 \\ \vdots \\ dx_n \end{pmatrix}$$


Definirajmo $F(x)$ kot kompozitum $f(\!g(\!a\!)\!)$.

Kako bi logično odvajali $f(g(a))$. Veljalo bi da je

$$df = f'(g(a)) \cdot dg$$

kjer je $df$ vektor ker je $f$ vektorska funkcija in $dg$ vektor ker je $f$ funkcija $n$ spremenljivk. Še več, ker nam kot odvod služi jacobijeva matrika dobimo

$$df = Df(g(a)) \cdot dg$$
$$\begin{pmatrix} df_1 \\ df_2 \\ \vdots \\ df_k \end{pmatrix} = \begin{pmatrix}
\frac{\partial f_1}{\partial y_1}(g(a)) & \frac{\partial f_1}{\partial y_2}(g(a)) & \cdots & \frac{\partial f_1}{\partial y_n}(g(a)) \\
\frac{\partial f_2}{\partial y_1}(g(a)) & \frac{\partial f_2}{\partial y_2}(g(a)) & \cdots & \frac{\partial f_2}{\partial y_n}(g(a)) \\
\vdots & \vdots & \ddots & \vdots \\
\frac{\partial f_k}{\partial y_1}(g(a)) & \frac{\partial f_k}{\partial y_2}(g(a)) & \cdots & \frac{\partial f_k}{\partial y_n}(g(a))
\end{pmatrix} \begin{pmatrix} dg_1 \\ dg_2 \\ \vdots \\ dg_n \end{pmatrix}$$

Sedaj se vprašamo kako je definiran $dg_{i}$. To je seveda produkt gradienta in $dx$ torej za vsak $dg_{i}$ velja

$$dg_{i} = \nabla g_{i} \cdot dx$$

S tem dobimo 

$$df = Df(g(a)) \cdot Dg(a) \cdot dx$$


$$\begin{pmatrix} df_1 \\ \vdots \\ df_k \end{pmatrix} = \begin{pmatrix}
\frac{\partial f_1}{\partial y_1}(g(a)) & \cdots & \frac{\partial f_1}{\partial y_n}(g(a)) \\
\vdots & \ddots & \vdots \\
\frac{\partial f_k}{\partial y_1}(g(a)) & \cdots & \frac{\partial f_k}{\partial y_n}(g(a))
\end{pmatrix} \begin{pmatrix}
\frac{\partial g_1}{\partial x_1}(a) & \cdots & \frac{\partial g_1}{\partial x_m}(a) \\
\vdots & \ddots & \vdots \\
\frac{\partial g_n}{\partial x_1}(a) & \cdots & \frac{\partial g_n}{\partial x_m}(a)
\end{pmatrix} \begin{pmatrix} dx_1 \\ \vdots \\ dx_m \end{pmatrix} $$

Torej za diferencial velja

$$dF = Df(g(a)) \cdot Dg(a) \cdot dx$$
$$ $$
$$dF = DF(a) \cdot dx$$
$$DF(a) = Df(\!g(a)\!) \cdot Dg(a)$$
$$ $$
$$
\begin{pmatrix}
\frac{\partial F_1}{\partial x_1}(a) & \cdots & \frac{\partial F_1}{\partial x_n}(a) \\
\vdots & \ddots & \vdots \\
\frac{\partial F_m}{\partial x_1}(a) & \cdots & \frac{\partial F_m}{\partial x_n}(a)
\end{pmatrix}
=
\begin{pmatrix}
\frac{\partial f_1}{\partial y_1}(\mathbf{g}_a) & \cdots & \frac{\partial f_1}{\partial y_p}(\mathbf{g}_a) \\
\vdots & \ddots & \vdots \\
\frac{\partial f_m}{\partial y_1}(\mathbf{g}_a) & \cdots & \frac{\partial f_m}{\partial y_p}(\mathbf{g}_a)
\end{pmatrix}
\cdot
\begin{pmatrix}
\frac{\partial g_1}{\partial x_1}(a) & \cdots & \frac{\partial g_1}{\partial x_n}(a) \\
\vdots & \ddots & \vdots \\
\frac{\partial g_p}{\partial x_1}(a) & \cdots & \frac{\partial g_p}{\partial x_n}(a)
\end{pmatrix}
$$



Označimo dimenzijo $f$ s $p$, št. spremenljivk $f$ z $m$ in število spremenljivk $g$ z $n$. Če podrobno pogledamo opazimo naslednje. Ker ne delamo pri pouku s $p$-ji večjimi od 1 velja da je $p = 1$.


Za $n = 1$ *($g$ je 1 spremenljivke)* dobimo prejšnjo izpeljavo za kompozitum funckije odvisne od 1 spremenljivke.

$$df(\mathbf{g}(t)) = Df(\mathbf{g}(t)) \cdot  Dg(\!t\!) \cdot dt$$
$$df(\!\mathbf{g}(\!t\!)\!) = \begin{bmatrix}
\frac{\partial f}{\partial x_1}(\!\mathbf{g}(\!t\!)\!) & \frac{\partial f}{\partial x_2}(\!\mathbf{g}(\!t\!)\!) &
\dots & \frac{\partial f}{\partial x_m}(\!\mathbf{g}(\!t\!)\!) 
\end{bmatrix}
\!\!\cdot \!\!\begin{bmatrix}
\frac{\partial g_1}{\partial x_1} (a)\\
\frac{\partial g_2}{\partial x_1} (a) \\
\vdots \\
\frac{\partial g_m}{\partial x_1} (a) 
\end{bmatrix} \cdot  \;dt$$
$$df(\!\mathbf{g}(\!t\!)\!) =\frac{\partial f}{\partial x_1}(\!\mathbf{g}(\!t\!)\!)\cdot dg_{1}(t)\,+ \,...+\,\frac{\partial f}{\partial x_m}(\!\mathbf{g}(\!t\!)\!)\cdot  dg_{m}(\!t\!)$$
$$df(\!\mathbf{g}(\!t\!)\!) =\frac{\partial f}{\partial x_1}(\!\mathbf{g}(\!t\!)\!)\cdot \frac{dg_{1}}{dt}\!(\!t\!)dt\,+ \,...+\,\frac{\partial f}{\partial x_m}(\!\mathbf{g}(\!t\!)\!)\cdot  \frac{dg_{m}}{dt}\!(\!t\!)dt $$
$$\frac{d f}{dt}(\! \mathbf{g}(\!t\!)\!) = \frac{\partial f}{\partial x_1}(\!\mathbf{g}(\!t\!)\!)\cdot \frac{dg_{1}}{dt}\!(\!t\!)\,+ \,...+\,\frac{\partial f}{\partial x_m}(\!\mathbf{g}(\!t\!)\!)\cdot  \frac{dg_{m}}{dt}\!(\!t\!) = {\color{green}f'(t)}$$

Za $n = 1$ in $m = 1$ pa dobimo originalno verižno pravilo:

$$df(\!g(x)\!) = Df(\!g(x)\!) \cdot  Dg(\!x\!) \cdot dx$$
$$df(\!g(x)\!) = \frac{\partial f}{\partial x_{1}}(\!g(x)\!) \cdot  \frac{dg}{dx}\!(\!x\!) \cdot dx$$
$$\frac{df}{dx}(\!g(x)\!) = \frac{df}{dg}(\!g(x)\!)\cdot \frac{dg}{dx}(\!x\!)$$


**Posplošen kompozitum**, kjer originalna funkcija ni vektorska funkcija, kjer je $n,m \in \mathbb{N}$ pa je 

$$ df(g(a)) = Df(g(a)) \cdot dg(a) = $$
$$ = \begin{bmatrix}
\frac{\partial f}{\partial g_1}(\!\mathbf{g}(\!a\!)\!) & 
\dots & \frac{\partial f}{\partial g_m}(\!\mathbf{g}(\!a\!)\!) 
\end{bmatrix} 
\cdot 
\begin{bmatrix}
\frac{\partial g_1}{\partial x_1} (a) & \cdots & \frac{\partial g_1}{\partial x_n} (a) \\
\frac{\partial g_2}{\partial x_1} (a) & \cdots & \frac{\partial g_2}{\partial x_n} (a) \\
\vdots & \ddots & \vdots \\
\frac{\partial g_m}{\partial x_1} (a) & \cdots & \frac{\partial g_m}{\partial x_n} (a)
\end{bmatrix} \cdot \;dx$$
$$ = \begin{bmatrix}
\frac{\partial f}{\partial g_1}(\!\mathbf{g}(\!a\!)\!) \cdot \frac{\partial g_{1}}{\partial x_{1}} (a)\, + \,... +\, \frac{\partial f}{\partial g_m}(\!\mathbf{g}(\!a\!)\!) \cdot \frac{\partial g_m}{\partial x_1} (a) & \cdots &
\end{bmatrix} \cdot \,
\begin{bmatrix}
dx_{1} \\dx_{2}\\ \vdots \\dx_{n}
\end{bmatrix}$$

Torej je gradient $f(\!g(\!a\!)\!)$ enak 
$$\begin{bmatrix}
\frac{\partial f}{\partial g_1}(\!\mathbf{g}(\!a\!)\!) \cdot \frac{\partial g_{1}}{\partial x_{1}} (a)\, + \,... +\, \frac{\partial f}{\partial g_m}(\!\mathbf{g}(\!a\!)\!) \cdot \frac{\partial g_m}{\partial x_{1}} (a) \;\;\dots\;\,\end{bmatrix}$$

kar pomeni da je 

$${\color{green}\frac{\partial F}{\partial x_{i}} = \frac{\partial f}{\partial g_1}(\!\mathbf{g}(\!a\!)\!) \cdot \frac{\partial g_{1}}{\partial x_{i}} (a)\, + \,... +\, \frac{\partial f}{\partial g_m}(\!\mathbf{g}(\!a\!)\!) \cdot \frac{\partial g_m}{\partial x_{i}} (a)}$$

Pomembno je povedati da je odvod vrstični vektor parcialnih odvodov oz. funkcij ki dajo koeficient funkcije v tisti točki oz. gradient $F$ po $n$ spremenljivkah.

$$F'(a) = \left[\frac{\partial F}{\partial x_{1}}(a),...,\frac{\partial F}{\partial x_{n}}(a)\right]$$
$${\color{green}F'(a) = Df(g(a)) \cdot dg(a)}$$
$$\frac{df}{dx}(\!g(\!a\!)\!) := F'(a) := \nabla F(a)$$

*Tukej dejansko ni definirano deljenje ampak izhajamo iz funkcij z eno spremenljivko.*


>[!|dokaz]- Dokaz:
>Predpostavimo da je $f$ diferenciabilna v $g(x)$ in $g$ diferenciabilna v $x$. 
> Po definiciji odvoda je $F'(t) = \lim_{h \to 0} \frac{F(t+h) - F(t)}{h} = \lim_{h \to 0} \frac{f(g(t+h)) - f(g(t))}{h}$.
> 
> Ker je funkcija $f$ diferenciabilna v točki $g(t) \in U$, lahko razliko v števcu zapišemo kot:
> $$
> f(g(t+h)) - f(g(t)) = \nabla f(g(t)) \cdot (g(t+h) - g(t)) + o(\|g(t+h) - g(t)\|) \quad \text{za } h \to 0.
> $$
> Ko izraz delimo s $h$ in pošljemo $h$ proti 0, dobimo:
> $$
> F'(t) = \lim_{h \to 0} \left( \nabla f(g(t)) \cdot \frac{g(t+h) - g(t)}{h} + \frac{o(\|g(t+h) - g(t)\|)}{h} \right)
> $$
> Prvi člen konvergira k $\nabla f(g(t)) \cdot g'(t)$, saj $\frac{g(t+h) - g(t)}{h} \to g'(t)$.
> 
> Drugi člen, tj. ostanek, preoblikujemo in izračunamo njegovo limito:
> $$
> \lim_{h \to 0} \frac{o(\|g(t+h) - g(t)\|)}{h} = \lim_{h \to 0} \frac{o(\|g(t+h) - g(t)\|)}{\|g(t+h) - g(t)\|} \cdot \frac{\|g(t+h) - g(t)\|}{h}
> $$
> Ker so komponente funkcije $g$ odvedljive, je $g$ zvezna, zato $g(t+h) \to g(t)$ in $\|g(t+h) - g(t)\| \to 0$, ko $h \to 0$. Po definiciji simbola $o$ je prvi faktor v limiti enak 0. Drugi faktor konvergira proti $\|g'(t)\|$, saj je norma zvezna funkcija. Limita ostanka je torej $0 \cdot \|g'(t)\| = 0$.
> 
> Sledi $F'(t) = \nabla f(g(t)) \cdot g'(t)$.

***

Funkcija je **zvezno odvedljiva** če je odvedljiva in njen odvod je zvezna funkcija.

Množico vseh $n$-krat zvezno odvedljivih funkcij na $U$ označimo $C^{n}(U)$.

$C^{0}(U)$ je množica vseh zveznih funkcij.
$C^{1}(U)$ je množica vseh zvezno odvedljivih funkcij.
$C^{\infty}(U)$ je množica vseh neskončno odvedljivih funkcij.



Definirajmo zožitev funkcije $f$ na daljico od $\mathbf{x}$ do $\mathbf{x}+ \mathbf{d}$ v definicijskem območju,

$$F(k) = f(\mathbf{x}+k \mathbf{d}) \,;\; k \in [0,1]$$

> Če $f$ je $n+1$-krat odvedljiva na $U$ potem je $F(s)$ je $n+1$-krat odvedljiva na $[0,1]$. 
> >[!|dokaz]- Dokaz:
> >Gremo z indukcijo in kot osnovni primer rečemo da če je $f$ enkrat odvedljiva je $F$ enkrat odvedljiva, kar je ker po verižnem pravilu, velja
> > $$F'(k) = \nabla f(\mathbf{x}+k \mathbf{d}) \cdot \mathbf{d}$$
> > Za indukcijsko predpostavko rečemo da če je $f$ $k$-krat odveljiva na $U$ je $F$ $k$-krat odvedljiva na $[0,1]$.
> > Če je $f$ odvedljiva $k+1$-krat, je $\nabla f$ odvedljiva $k$-krat. Iz tega sledi da je $F'(s) = \nabla f(x + kd) \cdot d$ odvedljiv $k$-krat. 
> > 
> > Ker je odvod $k$-krat odveljiv je $F$  po dokazu z indukcijo $k+1$-krat odvedlijv.

Vemo da če je funkcija diferenciabilna velja da je

$$f(a+h) \approx f(a) + df(a)h$$
$$f(a+h) \approx f(a) + \frac{\partial f}{\partial x_{1}}h_{1}+...+ \frac{\partial f}{\partial x_{n}}h_{n}$$

Sedaj pa želimo najti najboljši približek funkcije z upoštevanjem odvodov višjih redov. Z vsakim odvodom poskušamo oponašati obanašanje funkcije v točki $a$. 

Poglejmo kaj velja za našo funkcijo, ki opisuje daljico med dvema točkama.

Imamo funkcijo s katero je podana funkcijska vrednost v odvisnosti od vrednosti na neki daljici med $x$ in $x+h$. ($x+h$ bo nastopala kot točka v kateri je aproksimirana funkcija)

$$\mathbf{g(} k\mathbf{)} = \mathbf{x} + k \mathbf{h}$$
$$F(k) = f(g(k))\,;\;k \in [0,1]$$

Vrednost $F(1)$ bi po taylorjevem izreku, če bi aproksimirali v točki $k = 0$ dobili s spodnjo enačbo

$$F(1) = \frac{F\,(0)}{0!}\cdot 1^{0} + \frac{F'(0)}{1!}\cdot 1^{1 }+...+\frac{F^{(n)}(0)}{n!}\cdot 1^{n} + \frac{F^{(n+1)}(t)}{(n+1)!} \cdot 1^{n+1}$$

Poglejmo če lahko iz te konstrukcije razvijemo celotno taylorjevo formulo. 

*Ta enačba nam bo v resnici služila kot dokaz ker vemo da je to taylorjev izrek v eni spremenkljivki, potem če pravilno vstavimo funkcije več spremenljivk v to enačbo lahko dobimo taylorjev izrek v več spremenljivkah.*

Diferencial naše funkcije je po verižnem pravilu enak




$$dF = \left(\frac{\partial f}{\partial x_{1}}\cdot \frac{dg_1}{dk} +... + \frac{\partial f}{\partial x_{m}} \cdot \frac{dg_{m}}{dk}\right)dk$$
$$F'(k) = \frac{\partial f}{\partial x_{1}}\cdot \frac{dg_1}{dk} +... + \frac{\partial f}{\partial x_{m}} \cdot \frac{dg_{m}}{dk}$$
$$F'(k) = \frac{\partial f}{\partial x_{1}}\cdot h_{1} +... + \frac{\partial f}{\partial x_{m}} \cdot h_{m}$$
$$F'(k) = \nabla f \cdot g' = \nabla f \cdot h$$

Ta zapis je primerljiv z alternativnim zapisom taylorjeve formule v eni spremenljivki. Če rečemo da je $x-a = h$ dobimo

$$f(a) + f'(a)(x-a) + \frac{1}{2}f''(a)(x-a)^{2} = $$
$$f(x-h) + f'(x-h)h +\frac{1}{2}f''(x-h)h^{2}$$

To pomeni da namesto da imamo neko funkcijo aproksimirano v točki $a$ imamo funkcijo za vsak $x$ aproksimirano za $h$ stran.
Torej namesto aproksimiranja v eni točki $a$, je funkcija aproksimirana za vsak $x$ v točki za $x-h$ torej se premika skupaj z $x$.

S tem zapisom v glavi izpeljemo taylorjevo formulo v več spremenljivkah.

Poskusimo izpeljati Taylorjevo formulo za 2 spremenljivki

$$F(k) = f(a+kh)$$
$$a \in \mathbb{R}^{2}, h \in \mathbb{R}^{2}, k \in \mathbb{R}$$

Iščemo $F^{(i)}(0)$.
Naredimo za $k = 2$ oz. da je $f$ dveh spremenljivk

$$F(k) = f(a_{1}+kh_{1},a_{2}+kh_{2})$$

Po verižnem pravilu je odvod

$$F'(k) = {\color{green}f_{x_{1}}}(a_{1}+kh_{1},a_{2}+kh_{2}) {\color{green}\cdot h_{1} +f_{x_{2}}}(a_{1}+kh_{1},a_{2}+kh_{2}){\color{green}\cdot h_{2}}$$

$\Rightarrow$

$$F'(0) = f_{x_{1}}(a_{1},a_{2}) \cdot h_{1} +f_{x_{2}}(a_{1},a_{2})\cdot h_{2}$$
$$ $$
$$\color{light} F''(0) =(f_{x_{1}}(g(0)) \cdot h_{1} +f_{x_{2}}(g(0))\cdot h_{2})'$$
$$ \color{light}F''(0) = h_{1} \cdot  (\!f_{x_{1}}\!(\!g(\!0\!)\!)\!)'  +h_{2} \cdot (\!f_{x_{2}}\!(\!g(\!0\!)\!)\!)'$$
$$ \color{light}F''(0) = h_{1} \cdot  (\!f_{x_{1}x_{1}} \!(\!g(\!0\!)\!) \cdot  h_{1} + f_{x_{1}x_{2}}(\!g(\!0\!)\!)\cdot h_{2}\!)  +h_{2} \cdot (\!f_{x_{2}x_{1}} \!(\!g(\!0\!)\!) \cdot  h_{1} + f_{x_{2}x_{2}}(\!g(\!0\!)\!)\cdot h_{2}\!) $$
$$ $$

$$F''(0) = f_{x_{1}x_{1}}(a_{1},a_{2})h_{1}^{2} + f_{x_{1}x_{2}}(a_1,a_{2})h_{1}h_{2} + f_{x_{1}x_{2}}(a_1,a_{2})h_{1}h_{2} + f_{x_{2}x_{2}}(a_{1},a_{2})h_{2}^{2}$$
$$ = f_{x_{1}x_{1}}h_{1}^{2} + 2\cdot f_{x_{1}x_{2}}h_{1}h_{2}  + f_{x_{2}x_{2}}h_{2}^{2}$$

$$F'''(0) = f_{x_{1}x_{1}x_{1}}h_{1}^{3} + f_{x_{2}x_{2}x_{2}}h_{2}^{3} +  3\cdot f_{x_{1}x_{2}x_{2}}h_{1}h_{2}^{2}  + 3\cdot f_{x_{1}x_{1}x_{2}}h_{1}^2h_{2}$$

Če nadaljujemo opazimo podobnost s formulo za $n$-to stopnjo dvočlenika

Definirajmo operator

$$\frac{d}{dk}F(k)  = $$
$$= \frac{\partial f}{\partial x_{1}}\!(\!a+kh\!) \cdot h_{1} + \frac{\partial f}{\partial x_{2}}\!(\!a+kh\!) \cdot h_{2} =$$ $$= \!\!\left[  \left(\frac{\partial}{\partial x_{1}} \cdot h_{1} + \frac{\partial}{\partial x_{2}}\cdot h_{2} \right) f\right]\!(a+kh)$$
$$ $$
$$\frac{d^{2}}{dk^{2}}F(k)  = $$
$$= \frac{\partial^{2} f}{\partial x_{1}^{2}}\!(\!a+kh\!) \cdot h_{1}^{2} + \frac{\partial f^{2}}{\partial x_{2}^{2}}\!(\!a+kh\!) \cdot h_{2}^{2} +\frac{\partial f}{\partial x_{1}x_{2}}(a+kh)\cdot h_{1}h_{2}  =$$ $$= \!\!\left[ \left(\frac{\partial}{\partial x_{1}} \cdot h_{1} + \frac{\partial}{\partial x_{2}}\cdot h_{2} \right) \left(\frac{\partial}{\partial x_{1}} \cdot h_{1} + \frac{\partial}{\partial x_{2}}\cdot h_{2} \right) f\right](a+kh)$$
$$ $$
$$\frac{d^{n}}{dk^{n}}F(k) = $$
$$ = \left[\left(\frac{\partial }{\partial x_{1}} \cdot h_{1} + \frac{\partial }{\partial x_{2}} \cdot h_{2}  \right)^{\!n} \; f \right](a+kh)$$
$$ $$


Če vstavimo $F(1)$ in $F^{(i)} (0)$ v taylorjevo formulo za eno spremenljivko

$$F(1) = \frac{F\,(0)}{0!}\cdot 1^{0} + \frac{F'(0)}{1!}\cdot 1^{1 }+...+\frac{F^{(n)}(0)}{n!}\cdot 1^{n} + \frac{F^{(n+1)}(t)}{(n+1)!} \cdot 1^{n+1}$$
$$ $$
$$F(1)  = f(\mathbf{a}+ \mathbf{h})$$
$$ $$
$$F^{(n)}(0)=\frac{d^{n}}{dk^{n}}F(0)$$
$$ = \left[\left(\frac{\partial }{\partial x_{1}} \cdot h_{1} + \frac{\partial }{\partial x_{2}} \cdot h_{2}  \right)^{\!n} \; f \right](a)$$
$$ $$
dobimo natanko formulo za več spremenljivk.

$$f(\mathbf{a}+ \mathbf{h}) {\color{light} - R(h)} = f(a) + (\nabla f \cdot \mathbf{h})f(a) + \frac{1}{2!}(\nabla f \cdot \mathbf{h})^{2}f(a)+\,\dots$$


Tako naša taylorjeva formula za 2 spremenljivki postane

$$T_{a,n}(h) = \sum_{0}^{n} \frac{1}{i!}\cdot \!\left[\left   (\frac{\partial }{\partial x_{1}} \cdot h_{1} + \frac{\partial }{\partial x_{2}} \cdot h_{2}  \right)^{\!i}  f \right]\!(a) $$

**Posplošena taylorjeva formula pa je**

$$\color{green}T_{a,n}(h) = \sum_{0}^{n} \frac{1}{i!}\cdot \!\left[\left   (\frac{\partial }{\partial x_{1}} \cdot h_{1} +...+ \frac{\partial }{\partial x_{m}} \cdot h_{m}  \right)^{\!i}  f \right]\!(a) $$

oz.

$$T_{a,n}(h) = \sum_{0}^{n} \frac{1}{i!}\cdot \!\left[   (\nabla \cdot \mathbf{h})^{i}  f \right]\!(a) $$

Nadaljno velja da je

$$f(a+h) = f(a) + T_{a,n}(h) + R(h)$$
$$R(h) = \frac{1}{(n+1)!}\cdot \left[  \left(\frac{\partial }{\partial x_{1}} \cdot h_{1} + ... + \frac{\partial }{\partial x_{m}} \cdot  h_{m} \right)^{n+1}f\right](a+kh)$$
$$k \in [0,1]$$



Obstaja konstanta $M_0 \geq 0$ takšna, da za vsak $x$ na daljici med $a$ in $a+h$ velja $\left\Vert D^{n+1}f(x) \right\Vert \leq M_0$.
Za ostankov člen $R_{a,n}(h)$ velja ocena:

$$ |R_{a,n}(h)| \leq \frac{M_0}{(n+1)!} \left\Vert h \right\Vert^{n+1} $$

Iz tega sledi, da je red ostanka pri $h \to 0$ enak $(n+1)$:

$$ \frac{|R_{a,n}(h)|}{\left\Vert h \right\Vert^{n+1}} \leq \frac{M_0}{(n+1)!} $$



Če za nek $r > 0$ taylorjeva vrsta neskončnokrat zvezno odvedljive funkcije za vse $h$, kjer velja $\left\Vert h \right\Vert < r$, konvergira in je njena vsota enaka $f(a+h)$ potem je $f$ analitična v okolici točke $a$. 

>[!|dokaz]- Dokaz taylorjeve vormule na kratko:
> Naj bo $f: U \to \mathbb{R}$ funkcija razreda $C^{n+1}$ na odprti množici $U \subseteq \mathbb{R}^d$. Izberimo $\mathbf{a} \in U$ in $\mathbf{x} \in U$ tako, da je celoten odsek $[\mathbf{a}, \mathbf{x}] = \{\mathbf{a} + t(\mathbf{x}-\mathbf{a}) : t \in [0,1]\}$ vsebovan v $U$.
> 
> Definirajmo enospremenljivko funkcijo $g(t) = f(\mathbf{a} + t(\mathbf{x}-\mathbf{a}))$ za $t \in [0, 1]$
> Ker je $f$ razreda $C^{n+1}$ in so argumenti $f$ zvezno odvedljivi, je tudi $g(t)$ razreda $C^{n+1}$ na $[0,1]$. Po Taylorjevem izreku za eno spremenljivko, ki se nanaša na funkcijo $g(t)$ okoli $t=0$, obstaja $c \in (0, 1)$ tak, da velja:
> $g(1) = g(0) + g'(0) \cdot 1 + \frac{g''(0)}{2!} \cdot 1^2 + \dots + \frac{g^{(n)}(0)}{n!} \cdot 1^n + \frac{g^{(n+1)}(c)}{(n+1)!} \cdot 1^{n+1}$
> 
> Označimo $\mathbf{h} = \mathbf{x}-\mathbf{a}$. Z uporabo verižnega pravila lahko izračunamo odvode funkcije $g(t)$:
> $g'(t) = \nabla f(\mathbf{a} + t\mathbf{h}) \cdot \mathbf{h} = \sum_{i=1}^d h_i \frac{\partial f}{\partial x_i}(\mathbf{a} + t\mathbf{h})$.
> To lahko zapišemo z operatorjem smernega odvoda kot $(\mathbf{h} \cdot \nabla) f(\mathbf{a} + t\mathbf{h})$.
> Z indukcijo ugotovimo, da je $k$-ti odvod funkcije $g(t)$:
> $g^{(k)}(t) = (\mathbf{h} \cdot \nabla)^k f(\mathbf{a} + t\mathbf{h})$,
> kjer $(\mathbf{h} \cdot \nabla)^k$ pomeni $k$-kratno uporabo operatorja smernega odvoda.
> 
> Sedaj vstavimo te izraze za odvode v Taylorjevo formulo za $g(1)$:
> $g(0) = f(\mathbf{a})$.
> $g^{(k)}(0) = (\mathbf{h} \cdot \nabla)^k f(\mathbf{a})$ za $k=1, \dots, n$.
> Ostanek pa je:
> $R_n = \frac{g^{(n+1)}(c)}{(n+1)!} = \frac{1}{(n+1)!} (\mathbf{h} \cdot \nabla)^{n+1} f(\mathbf{a} + c\mathbf{h})$.
> 
> Če nadomestimo $\mathbf{h}$ z $\mathbf{x}-\mathbf{a}$ in upoštevamo $g(1) = f(\mathbf{x})$, dobimo Taylorjev izrek v več spremenljivkah:
> $f(\mathbf{x}) = f(\mathbf{a}) + (\mathbf{x}-\mathbf{a}) \cdot \nabla f(\mathbf{a}) + \frac{1}{2!} ((\mathbf{x}-\mathbf{a}) \cdot \nabla)^2 f(\mathbf{a}) + \dots + \frac{1}{n!} ((\mathbf{x}-\mathbf{a}) \cdot \nabla)^n f(\mathbf{a}) + R_n(\mathbf{x})$,
> kjer je ostanek (v Lagrangeevi obliki) podan z:
> $R_n(\mathbf{x}) = \frac{1}{(n+1)!} ((\mathbf{x}-\mathbf{a}) \cdot \nabla)^{n+1} f(\boldsymbol{\xi})$,
> pri čemer je $\boldsymbol{\xi} = \mathbf{a} + c(\mathbf{x}-\mathbf{a})$ neka točka na daljici med $\mathbf{a}$ in $\mathbf{x}$.

### Ekstremi

Funkcija ima ekstrem v točki $a$ če obstaja odprta krogla da za funkcijske vrednosti notri velja da so  vse ali manjše ali večje od $f(a)$.

Naj bo funkcija $k$ spremenljivk in diferenciabilna v $a$. Če ima $f$ v točki $a$ lokalni eksterem velja ali da so vsi parcialni odvodi v $a$ enaki nič - $(\nabla f = 0)$, ali pa da vsaj en parcialen odvod ne obstaja drugi pa so lahko poljubni.

**To je potreben pogoj** torej to še ne pomeni da je tam ekstrem - to so le naši kandidati.

Točkam kjer so vsi parcialni odvodi 0 pravimo **stacionarne točke** oz. **kritične točke.**

V kritični točki velja da je $df(a) = 0$. Ni nujno da je kritična točka lokalni ekstrem.

Za zadostni pogoj bomo potrebovali drugi odvod.

Naj bo $f(x,y)$ funkcija $\in C^3(a)$ potem za majhne $h$ velja 

$$f(a+h) = f(a) + (\nabla \cdot h)f(a) + (\nabla \cdot h)^{2}f(a) \cdot \frac{1}{2} =$$
$$ $$
$$\begin{align}
\ =\; &f(a) \;+\\ \\ 
& \left(\frac{\partial f}{\partial x}(a) \cdot h_{1} + \frac{\partial f}{\partial y}(a) \cdot h_{2}\right) \;+ \\\\ 
 & \left(\frac{\partial^{2} f}{\partial x^{2}}\cdot h_{1}^{2} + \frac{\partial^{2} f}{\partial xy}\cdot 2h_{1}h_{2} + \frac{\partial^{2} f}{\partial y^{2}}\cdot h_{2} \right)\cdot \frac{1}{2} =
\end{align}$$
$$ $$
$$= f(\!a\!) +
 (f_{x}(\!a\!)  \cdot h_{1} + f_{y}(\!a\!) \cdot h_{2}) +  
 (f_{xx}(\!a\!) \cdot h_{1}^{2} + f_{xy}(\!a\!) \cdot 2h_{1}h_{2} + f_{yy}(\!a\!) \cdot h_{2} )\cdot \frac{1}{2} =$$
$$ $$
Če je $a$ stacionarna točka potem dobimo

$$f(a+h)=  
 f(a) + (f_{xx}(\!a\!) \cdot h_{1}^{2} + f_{xy}(\!a\!) \cdot 2h_{1}h_{2} + f_{yy}(\!a\!) \cdot h_{2} )\cdot \frac{1}{2} $$
 $$\Delta f = f(a+h)-f(a) = (f_{xx}(\!a\!) \cdot h_{1}^{2} + f_{xy}(\!a\!) \cdot 2h_{1}h_{2} + f_{yy}(\!a\!) \cdot h_{2} )\cdot \frac{1}{2}$$

>[!|hide]- Blabber
> *Precej pomemembna stvar za razumevanje napake je da ko dodamo $n$-ti člen hočemo da $\frac{R(h)}{h^{n}}$ konvergira proti 0. Ker ne dodajamo novega člena bi to naravno pomenilo da $\frac{R(h)}{h^{n+1}}$ ne konvergira k 0, tista vrednosti h kateri konvergira in kako daleč je od 0 pa nam pove kako močno je funkcija odvisna od $n$-tega člena v aproksimaciji.*
> 
> *Torej če imamo aproksimacijo prve stopnje oz. samo z odvodom prvega reda pravimo da mora konvergirati koeficient ostanka v $a$ proti 0. Hkrati pa opazimo da drugi odvod ostanka ponavadi ne kovergira k 0.*
> 
> *Če imamo aproksimacijo druge stopnje oz. z odvodom prvega in drugega reda potem velja da gre drugi koeficient oz. koeficient koeficienta ostanka proti 0.*
> 
> *Iz tega izhaja pogoj da za vsak n-ti člen, ki ga dodamo velja da bo $\frac{R_{a,n}}{h^{n}}$ konvergiral k 0.*
> 
> *Nadaljujemo z oceno ker pravimo da če imamo npr. aproksimacijo 2. stopnje potem je aproksimacija taka da velja da je 3. odvod konvergira dovolj blizu k 0 da če bi dodali 3. člen ki bi poskrbel da konvergira k 0, ne bi močno spremenil funkcije v okolici $a$.*
> 
> https://www.desmos.com/calculator/czcxu54lcn

Ostanek lahko z lagrangom zapišemo kot $\frac{1}{3!}D^3f(c)h^{3}$, kar pomeni da obstaja $C$ da velja

$$|R_{3}(h)| \leq C \left\Vert h \right\Vert ^{3}$$
$$ \frac{|R_{3}(h)|}{\left\Vert h \right\Vert ^{3}}\leq C $$


Gledamo kvocient

$$ \frac{R_{3}(h)}{O(h^{2})} = \frac{Ch^{3}}{Dh^{2}}=Eh$$

vzamemo limito ko gre $h \rightarrow 0$. In vidimo da gre kvocient k nič, to je dovolj da zanemarimo člen $R(h)$ saj za dovolj majhne $h$ postane zanemarljiv v primerjavi z glavnim delom.



Torej na obnašanje funkcija vpliva $Q(h)$. 

Naj bo 

$$Q(h) = f_{xx}(\!a\!) \cdot h_{1}^{2} + f_{xy}(\!a\!) \cdot 2h_{1}h_{2} + f_{yy}(\!a\!) \cdot h_{2} $$
$$ $$
$$ A = f_{xx}(\!a\!) , B = f_{xy}(\!a\!) , C = f_{yy}(\!a\!)$$
$$ $$
$$\Rightarrow Q(h) =  A \cdot h_{1}^{2} + B \cdot 2h_{1}h_{2} + C \cdot h_{2}$$

>[!|hide]-  Jibber Jabber
> 
> Kot smo videli je sprememba funkcijske vrednosti odvisna od $Q(h)$. Kar se dogaja je da gledamo taylorjevo aproksimacijo 2. stopnje kjer vemo da je prvi odvod v tej točki enak 0. To pomeni da se bo funkcija obnašala zelo podobno kot $Q(h)$ iz česar ugotavljamo ali je tam ekstrem ali sedlo.
> 
> Če je $Q(h)$ enak nič nam funkcija o predznaku ne pove ničesar. To pomeni da je najboljša taylorjeva aproksimacija v točki $a$ linearna aproksimacija, še več, mora veljati da je linearna aproksimacija boljša od aproksimacije s taylorjem 2. stopnje, ker vemo da je ta linearna aproksimacija enaka 0, mora biti okolica $a$ tako ploščata, da kvadratna aproksimacija slabše opiše okolico $a$ kot linearna v katerem primeru si lahko predstavljamo primera kjer v točki $a$ nastane ekstrem ali sedlo, a je okolica v tej točki tako ploščata, da je najboljša aproksimacija ravna ploskev.
> 
> *Da ponovimo, vsak n-ti člen aproksimacije v taylorjevem polinomu zahteva da koeficient n-te razlike konvergira proti 0.*
> 
> V tem primeru bi veljalo da $\frac{R(h)}{\left\Vert h \right\Vert^2}$ konvergira k 0 natanko tedaj ko je koeficient $f''(a)$ enak 0. 
> 
> *Da smo si na jasnem če uporabimo kvadratno aproksimacijo, bo prvi koeficient napake $\frac{R(h)}{\left\Vert h \right\Vert}$ konvergiral k 0, ampak njegova krivulja ne bo ploščata pri nič kar pomeni da koeficient koeficienta $\frac{R(h)}{\left\Vert h \right\Vert^2}$ ne konvergira k 0 - kar bi morala če imamo dobro aproksimacijo. Če vzamemo linearno aproksimacijo, bo koeficient koeficienta razlike konvergiral k 0, oz. bo bolje aproksimiral funckijo oz. bo koeficient kvadratne funkcije ki najbolje aproksimira okolica $a$ enak 0.*
> 
> 
> 
> Očitno je, kako ravna črta bolje aproksimira, saj 2. koeficient napake pri aproksimaciji s kavdratom proti aproksimaciji z linearnim členom ne konvergira k 0. 
> 
> https://www.desmos.com/calculator/l246ynjfrw
> 
> Vprašanje je kdaj je $Q(h)$ negativen ali pozitiven.
> 
> 
>[!|dokaz]- Intuicija
>
$f_{xx} > 0$ - koeficient x funkcij po x se veča (neka kvadratna f recimo)
$f_{xy} < 0$ - koeficient x funkcij po y se manjša (kvadratna funkcija, ki če ji sledimo po y osi ratuje vedno bolj ploska in nato se obrne)
>
ko gledamo $f_{xx}f_{yy}-f_{xy}^{2}> 0$ gledamo ali koeficienti x funkcij po x in y funkcij po y dovolj močno vlečejo funkcijo v svojo smer da izničijo vpliv na koeficient funkcije x po y osi in obratno. 
>
$$f_{xx}f_{yy} > f_{xy}^2$$
>
ta pogoj nam torej omogča da preverimo ali sta prvo kot prvo predznaka naraščanja koficienta enaka, drugo kot drugo pa ali je jakost naraščanja koeficienta po svoji osi dovolj velika da izniči spremembo koeficienta po drugi osi.
>
Potem drugi pogoj $f_{xx} > 0$ ali $< 0$ pa preverja ali koeficient narašča ali pada, s prejšnjim pogojem pa preverjamo ujemanje predznakov le teh, torej lahko gledamo $f_{xx}$ ali $f_{yy}$
>
Če je $f_{xx}f_{yy}-f_{xy}^{2}<0$ pomeni da koeficent funkcije na osi (x) sicer narašča, ampak ob premiku po drugi osi (y) pa celotna funkcija postaja bolj položna recimo in koeficient pada, to padanje pa je dovolj močno da vrednosti padejo pod izhodišče in tako dobimo sedlo.
>
To pomeni da če gremo za nek dx po x se bo vrednost funkcije po x dovolj povečala da bo kljub spremembi koeficienta y funkcije ne bo dovolj hitro padla in bo še vedno obstajala okolica $a$ s samimi večjimi vrednostmi
>
Če velja da je $f_{xx}f_{yy}-f_{xy}^{2}=0$ pa velja da se ravno dovolj vlečejo da smo vsaj v eni smeri tolik oploščati da aproksimacija z drugo stopnjo ni več dovolj natančna,



Naredimo še izpeljavo 

1. Če sta $A$ in $C$ enaka 0 potem je $Q(h)$ lahko pozitivna ali negativna, torej imamo neko sedlasto točko.

2. Drugače, če vsaj ena od $A,C$ ni nič lahko zapišemo naslednje. Predpostavimo da $A \neq 0$ (analogno za $C$)

$$Q(h) =  A \cdot h_{1}^{2} + B \cdot 2h_{1}h_{2} + C \cdot h_{2}^{2}$$
$$Q(h) = \frac{1}{A}(A^{2}  h_{1}^{2} + BA  2h_{1}h_{2} + CA  h_{2}^{2})$$
$$Q(h) = \frac{1}{A}({\color{green}A^{2}  h_{1}^{2} + BA  2h_{1}h_{2}} + CA  h_{2}^{2})$$
$$Q(h) = \frac{1}{A}({\color{green}(Ah_{1} + Bh_{2})^{2}-B^2h_{2}^{2}} + CA  h_{2}^{2})$$
$$Q(h) = \frac{1}{A}((Ah_{1} + Bh_{2})^{2}-{\color{green}B^2h_{2}^{2} + CA  h_{2}^{2}})$$
$$Q(h) = \frac{1}{A}((Ah_{1} + Bh_{2})^{2}+{\color{green}h_{2}^{2}( CA - B^2 )})$$
$$Q(h) = \frac{1}{A}((Ah_{1} + Bh_{2})^{2}+h_{2}^{2}( CA - B^2 ))$$

Če pogledamo od česa je odvisen predznak vidimo najprej da je celoten oklepaj pozitiven če je 

$$(CA-B^{2}) > 0$$

kar pomeni da je predznak odvisen le od $A$, torej imamo maks, če je $A < 0$ in min. če je $A > 0$.

Če je

$$(CA-B^{2}) < 0$$

pa opazimo da dosežemo negativne in pozitivne vrednosti za enake, a različno usmerjene $h$-je oz. v eni smeri funkcija pada, v drugi smeri narašča.
V smeri $(h_{1},0)$ ima funkcija enak predznak kot $A$ v smeri $(-B,A)$ pa ima funkcija različen predznak od $A$. Torej imamo spet sedlasto točko.

Če je 

$$(CA-B^{2}) = 0$$

pa pomeni da obstaja vsaj ena smer v kateri je drugi odvod enak 0. To je naprimer $Ah_{1}+Bh_{2}\Rightarrow\left(\frac{-Bh_{1}}{A},h_{2} \right)$, torej je relativna razlika $\Delta f$ odvisna od funkcije ostanka.

$$ $$

**Pogoji so sledeči:**

$$\,\,\,\,\,\,\,f_{xx}f_{yy} - f_{xy}^{2}=0 \Leftrightarrow \text{Nedoločeno}$$
$$f_{xx}f_{yy} - f_{xy}^{2}>0 \Leftrightarrow \text{Ekstrem}$$
$$\!\!\!\!\!\!\!\!\!f_{xx}f_{yy} - f_{xy}^{2}<0 \Leftrightarrow \text{Sedlo}$$

Ko vemo da je ekstrem pogledamo še

$$f_{xx} > 0 \Leftrightarrow \text{Minimum}$$
$$f_{xx} < 0 \Leftrightarrow \text{Maksimum}$$

To je ekvivalentno geldanja determinante Hessianove matrike.

1.  **$\det(H_f(a)) > 0$**:
    *   Če $A = f_{xx}(a) > 0$, je lokalni minimum.
    *   Če $A = f_{xx}(a) < 0$, je lokalni maksimum.
2.  **$\det(H_f(a)) < 0$**: Sedlasta točka.
3.  **$\det(H_f(a)) = 0$**: Test je neodločljiv.

>[!|dokaz]- Dokaz o obstoju lokalnega ekstrem:
> **1\. $D > 0, A > 0$ oz. vemo da je $Q(h)$ pozitivno definitna**
> 
> Hočemo dokazati da obstaja minimum torej da je $\forall h: \Delta f(h) > 0$
> 
>Za $Q(h)$ vemo da je pozitivno definitna.
>
>*$Q(h)$ je zvezna na enotski krožnici zato doseže minimalno vrednost $m$, ker vemo da je $Q(h)> 0$ za vse vrednosti $h$, mora biti $m > 0$, nato pa da zagotovimo da velja za vse vektorje $h$ še pomnožimo z $\left\Vert h \right\Vert$ zaradi kvadratne komponente.*
>Izberemo poljuben $h \neq 0$ in vemo da $\frac{h}{\left\Vert h \right\Vert }$ leži na enotski krožnici radija $h$.
>
>$$Q(h) = Ah_{1}^{2} + Bh_{1}h_{2} + Ch_{2}^2$$
>$$= \Vert h^{2}\Vert \left(  A\frac{h_{1}^{2}}{\Vert h^{2}\Vert} +B\frac{h_{1}h_{2}}{\Vert h^{2}\Vert} + C\frac{h_{2}^{2}}{\Vert h^{2}\Vert}  \right)$$
>$$= \left\Vert h^{2} \right\Vert Q\left(\frac{h}{\left\Vert h \right\Vert } \right)$$
>$$\geq \left\Vert h^{2} \right\Vert m $$
>
>$\Rightarrow$ za vse $h$ velja da bo $Q(h)$ večji od $\left\Vert h^{2} \right\Vert m$.
>
Iz česar lahko ocenimo $Q(h)$ 
>
Če ocenimo $\Delta f$, za katero hočemo da je za vse $h : \Delta f \geq 0$.
>
$$\Delta f = \frac{1}{2}Q(h) + R_{a,2}(h)$$
$$\geq \frac{1}{2}Q(h) - |R_{a,2}(h)|$$
$$\geq \frac{1}{2}\left\Vert h^{2} \right\Vert m - C' \left\Vert h^{3} \right\Vert $$
$$=\left\Vert h^{2} \right\Vert\left(\frac{1}{2} m - C' \left\Vert h \right\Vert\right) \geq 0$$
>
Torej če je $h$ v okolici da velja $\left\Vert h \right\Vert < \frac{m}{2C'}$ potem po definiciji imamo okolico kjer so vsi $\Delta f \geq 0$ kar je minimum.
>
 **2\. $D > 0, A < 0$ je simetrično**
 > Za $M$ velja da je gotovo negativen, za $Q(h)$ pa $Q(h) < M \left\Vert h^2 \right\Vert$.
$$\Delta f = \frac{1}{2}Q(h) + R_{a,2}(h)$$
$$\leq \frac{1}{2}Q(h) + |R_{a,2}(h)|$$
$$\leq \frac{1}{2}\left\Vert h^{2} \right\Vert M + C' \left\Vert h^{3} \right\Vert $$
$$=\left\Vert h^{2} \right\Vert\left(C' \left\Vert h \right\Vert +\frac{1}{2} M \right) \leq 0$$
$$\Rightarrow \left\Vert h \right\Vert \leq -\frac{M}{2C'} $$
>
kar velja ker je $M$ negativno število 
>
> **3\. $D < 0$ oz. $Q(h)$ ni definitna**
>
Vemo da obstajata vektorja $h_{1}$ in $h_{2}$ za katera velja da bosta vsak v svoji smeri v neki okolici $a$ nasprotnih predznakov.
>
$$\Delta f(h_{1}) = \frac{1}{2}Q(h_{1}) + R_{a,2}(h_{1}) > 0$$
>
$$\Delta f(h_{2}) = \frac{1}{2}Q(h_{2}) + R_{a,2}(h_{2}) < 0$$
>
Ker vemo da je ostanek dovolj majhen ga izpustimo in rečemo da je v smeri $h_{1}$ $\Delta f$ pozitivna v smeri $h_{2}$ pa pozitivna.
>
> **4\. $D = 0$**
> V zapiskih ni dokazan oz. je dokazan z dvema primeroma $x^{3} + y^{3}$ in $x^{4} + y^{4}$. 
> Js sm pa len in se mi ne da neke nove toerije delat.

### Hessejeva matrika

$f$ je funkcija $n$ spremenljivk. **Hessejeva matrika** je definirana kot

$$H(f,a) = \begin{bmatrix}
f_{x_{1}x_{1}}(a) & \dots & f_{x_{1}x_{n}}(a) \\
\vdots & \ddots & \vdots \\
f_{x_{n}x_{1}}(a) & \dots & f_{x_{n}x_{n}}(a) 
\end{bmatrix}$$
$$ $$
$$D = \det H(\!f,a)$$

> Naj bo funkcija $f$ dvakrat zvezno odvedljiva v okolici svoje stacionarne točke. 
> Funkcija $f$ ima v tej točki lokalni ekstrem, če je determinanta njene Hessejeve matrike pozitivna. 
> V tem primeru ima $f$ v točki lokalni **minimum**, če je njena **sled pozitivna**, in lokalni **maksimum**, če je njena **sled negativna**.

Za funkcije več spremenljivk velja

$$Q(h) = \frac{1}{2}\left(\frac{\partial }{\partial x_{1}}h_{1} + ... \frac{\partial }{\partial x_{k}}h_{k}\right)^{2}f(a) =  h^{T} H h$$

Naj bo $H \in \mathbb{R}^{k\times k}$ simetrična $k \times k$ matrika in $Q(h) = h^{T}H h$ pripadajoča kvadratna forma. Pravimo:
- $H$ je pozitivno semidefinitna, če je $Q(h) \geq 0$ za vse $h$
- $H$ je **pozitivno definitna**, če je $Q(h) > 0$ za vse $h \!\backslash \! \{ 0\}$
- $H$ je negativno semidefinitna, če je $Q(h) \leq 0$ za vse $h$
- $H$ je **negativno definitna**, če je $Q(h) < 0$ za vse $h \!\backslash \! \{ 0\}$
- $H$ je **nedefinitna**, če obstajata $h_{+}, h_{-} \in \mathbb{R}^{k}$, da je $Q(h_{+}\!) > 0$ in $Q(h_{-}\!) < 0$

> Naj bo $f$ funkcija $k$ spremenljivk, ki je dvakrat zvezno odvedljiva v okolici točke $a$. Otnačimo s $H = H(f,a)$. Potem velja:
> - če je $H$ pozitivno definitna ima $f$ v točki $a$ lokalni minimum
> - če je $H$ negativno definitna ima $f$ v točki $a$ lokalni maksimum
> - če je $H$ nedefinitna nima $f$ v točki $a$ lokalnega ekstrema
> - v drugih primerih pa ni mogoče določiti ali je ali ni tam ekstrem.

> $H$ je pozitivno definitna $\Leftrightarrow$ vse njene lastne vrednosti so pozitivne
> $H$ je pozitivno definitna $\Leftrightarrow$ vse njene glavne poddeterminante so pozitivne

### Globalni ekstremi, vezani ekstremi in Langrangevi večkratniki

Ekstremi funkcij z definicijskim območjem neke kompaktne množice lahko nastopijo znotraj ali na robni točki.

V prvem primeru imamo lokalni ekstrem.

V drugem primeru pa pravimo da ima funkcija vezani ekstrem.

Omejimo se na funkcijo dveh spremenljivk, katere rob je krivulja v ravnini.


*Kdaj ko je rob $D$ podan z nekimi ravnimi črtami se lahko lotimo iskanja ekstremov tudi tako da pogledamo kako zgleda funkcija na tistih premicah in ugotovimo ekstreme na vsaki daljici.*

To pomeni da je definicijsko območje omejeno z neko krivuljo. Krivulja v ravnini pa je lahko izražena tudi kot izolipsa neke druge funkcije pri neki konstanti.


*Torej primer je $x^{2}+ y^{2} = 1$ predstavlja krog a je to hkrati funkcija $g(x,y) = x^{2} + y^{2}$ kjer vstavimo vrednost $g(x,y) =1$.*

Pomembna stvar je da vemo da ima ta krivulja svoj gradient v vsaki od teh točk, saj je le izsek funkcije $g(x)$.

Torej predpostavimo da je funkcija omejena z nekim izsekom funkcije $g(x,y) = C$, kjer je $g(x,y) = x^{2} +y^{2} \text{ in }C = 1$.

Vzamemo še funkcijo $f(x) = -2x^{2} - y^{2} + 1$ za presdstavo

https://www.math3d.org/gbKRSbge8C

> Gradient funkcije v točkah, ki pripadajo neki izolipsi je vedno pravokoten na izolipso
> >[!|dokaz]- Dokaz:
> > Imamo funkcijo $f(x,y)$. Iz nje dobimo izolipso pri $f(x,y) = C$. Nastalo krivuljo izrazimo kot funkcijo ene spremenljivke $r(t) = (x(t), y(t))$.
> > Sedaj je $f(x,y) = f(r(t))$, gradient oz. odvod $f$ pa je enak 
> > 
> > $$\frac{\partial f}{\partial x_{1}}\cdot r_{1}'(t) + \frac{\partial f}{\partial x_{2}}\cdot r_{2}'(t)$$
> > 
> Hkrati velja $f(r(t)) = k$
> $\Rightarrow$
> $$ \frac{\partial f}{\partial x_{1}}\cdot r_{1}'(t) + \frac{\partial f}{\partial x_{2}}\cdot r_{2}'(t) = 0$$
> $$ \nabla f(r(t)) \cdot Dr(t) = 0$$
> Torej sta vektor gradienta in vektor tangente na ravnino pravokotna oz. je vektor gradienta normalen na krivuljo izolipse.


Gradient funkcije $g(x)$ na izolipsi je vedno pravokoten na krivuljo.

*Za nadaljevanje si moramo predstavljati dejstvo da če imamo gradient funkcije $f$, ki je pravokoten na odvod krivulje bo to pomenilo da je tam neka stacionarna točka. To si lahko intuitivno razlagamo kot da če se premikamo pravokotno glede na naraščanje vrednosti $f$ potem v tej točki ne večamo niti ne manjšamo vrednosti krivulje, kar definira našo stacionarno točko.*

Matematično gledano vemo da je gradient $f$ pravokoten na odvod krivulje izolipse $f$. 

Imamo torej krivuljo $g(x,y) = C$, naj bo funckija $r(t)$ parametrizacija te krivulje $g(r(t)) = C$ torej bo $r(t)$ parametrična krivulja, s katero je omejena $f$.

$f(r(t))$ je sedaj funkcija krivulje, kjer je $r(t)$ enaka kot pri $g(r(t))$. To pomeni da ko ima $f$ v neki točki enak odvod kot neka izolipsa  - $(f(r_{1}(t)))' = 0$, potem vemo da je v tisti točki gradient pravokoten na vektor odvodov $r'(t) = (\dot r_{1}(t), \dot r_{2}(t))$.

$$\nabla f \perp r_{1}'(t)$$
$$\nabla f \cdot r'(t) = \nabla f \cdot r_{1}'(t)$$
$$ $$
$$\Rightarrow r'(t) = r_{1}'(t)$$
$$\Rightarrow \nabla f \cdot r'(t) = 0$$
$$\Rightarrow \nabla f \perp r'(t)$$


Ker iščemo kandidate za ekstreme iščemo stacionarne točke.

Torej bomo po zgornji razlagi hoteli ugotoviti kje bo gradient $f$ pravokoten na odvod $r(t)$.

Če imamo v točki $a = (r_{1}(t), r_{2}(t))$ gradient $g$ pravokoten na $g(r(t))$ in gradient $f$ pravokotern na $f(r(t))$ potem sta vektorja linearno odvisna oz. lahko zapišemo

$$\nabla f = \lambda \nabla g$$

oz. po drugi definiciji linearne odvisnosti

$$\nabla f + \lambda \nabla g =0$$

Iz tega dejstva izpeljemo funkcijo 

$$F(x,y,\lambda ) = f(x,y) + \lambda g(x,y)$$
$$F'(x,y,\lambda ) = \left({\color{green}\frac{\partial f}{\partial x} + \lambda \frac{\partial g}{\partial x}}\;\;,\;\; {\color{blue}\frac{\partial f}{\partial y} + \lambda \frac{\partial g}{\partial y}}\;\;,\;\; g(x,y)\right)$$

Kjer opazimo da so njene stacionarne točke pri tistih vrednostih kjer sta gradienta linearno odvisna

$$0 = \nabla f(x,y) + \lambda \nabla g(x,y)$$

in velja

$$g(x) = 0$$

V primeru da je $\nabla g = 0$ je po Lagrangevi funkciji tudi $\nabla f = 0$, in je še ena točka, ki jo preverjamo

> Izrek oz. metoda Lagrangevih multiplikatorjev
> 
> Naj bo $D \in \mathbb{R}^{2}$ odprta in $f,g \in C^1(D)$. Če ima funkcija $f$ pri vrednostih $x,y$ za katere velja $g(x,y)=0$ lokalni ekstrem v točki $(x_{0},y_{0}) \in D$ in je $\nabla g (x_{0},y_{0}) \neq (0,0)$ potem obstaja $\lambda_{0} \in \mathbb{R}$, da je $(x_{0},y_{0},\lambda_{0})$ stacionarna točka Lagrangeove funkcije
> $$F(x,y,\lambda )=f(x,y) + \lambda g(x,y)$$

***

> **Kandidati za lokalne ekstreme na robu kompaktne množice omejena z neko $g(\!\mathbf{x}\!) = C$ so točke kjer velja**
> 
> 1\. Točke kjer $f$ ali $g$ ni zvezno odvedljiva
> 2\. Točke, kjer je $\nabla g (x,y) = 0$
> 3\. Stacionarne točke Lagrangeve funkcije $f + \lambda  g$
>>[!|dokaz]- Dokaz:
> >     
> > 1.  **Prevedba problema na eno dimenzijo:**
> >     *   Predpostavimo, da lahko vez $g(x,y)=0$ v okolici točke ekstrema lokalno izrazimo kot funkcijo $y=h(x)$. To pomeni, da točke na vezi lahko pišemo kot $(x, h(x))$.
> >     *   Sedaj funkcijo $f(x,y)$ nadomestimo s $H(x) = f(x, h(x))$, kjer je $x$ edina neodvisna spremenljivka. Iskanje ekstremov $f(x,y)$ na vezi je s tem prevedeno na iskanje ekstremov funkcije $H(x)$.
> > 
> > 2.  **Iskanje ekstremov $H(x)$:**
> >     *   Za iskanje lokalnih ekstremov funkcije $H(x)$ izračunamo njen odvod in ga izenačimo z nič: $H'(x)=0$.
> >     *   **Po verižnem pravilu** je odvod $H(x)$ glede na $x$:
> >         $H'(x) = \frac{\partial f}{\partial x} \frac{dx}{dx} + \frac{\partial f}{\partial y} \frac{dy}{dx} = f_x(x, h(x)) \cdot 1 + f_y(x, h(x)) \cdot h'(x)$.
> >         Torej, na ekstremu velja: $f_x(x, h(x)) + f_y(x, h(x)) \cdot h'(x) = 0 \quad (\times)$
> > 
> > 3.  **Uporaba pogoja $g(x,h(x))=0$:**
> >     *   Ker točke $(x, h(x))$ ležijo na krivulji $g(x,y)=0$, velja $g(x,h(x))=0$ za vse $x \in J$.
> >     *   To enačbo odvajamo po $x$ (spet po verižnem pravilu, kar je **implicitno odvajanje**):
> >         $\frac{\partial g}{\partial x} \frac{dx}{dx} + \frac{\partial g}{\partial y} \frac{dy}{dx} = g_x(x, h(x)) \cdot 1 + g_y(x, h(x)) \cdot h'(x) = 0 \quad (\times\times)$
> > 
> > 4.  **Interpretacija z gradienti:**
> >     *   Enačbi $(\times)$ in $(\times\times)$ lahko prepišemo kot skalarna produkta:
> >         *   $\nabla f(x, h(x)) \cdot (1, h'(x)) = 0$
> >         *   $\nabla g(x, h(x)) \cdot (1, h'(x)) = 0$
> >     *   Vektor $(1, h'(x))$ je **smerni vektor tangente na krivuljo vezi $g(x,y)=0$** v točki $(x, h(x))$.
> >     *   Ker sta oba gradienta, $\nabla f$ in $\nabla g$, pravokotna na isti smerni vektor (tangento na vezno krivuljo), sta **kolinearna** (vzporedna) med seboj.
> > 
> > 5.  **Uvedba Lagrangeovega multiplikatorja $\lambda$:**
> >     *   Če sta dva vektorja kolinearna, pomeni, da je eden večkratnik drugega. Torej, če je $\nabla g(x_0, y_0) \neq 0$ (zelo pomemben pogoj, o katerem bomo govorili kasneje), obstaja skalar $\lambda_0$ tak, da velja:
> >         $\nabla f(x_0, y_0) = -\lambda_0 \nabla g(x_0, y_0)$, kar lahko prepišemo kot $\nabla f(x_0, y_0) + \lambda_0 \nabla g(x_0, y_0) = 0$.
> >     *   Ta enačba velja komponentno:
> >         *   $f_x(x_0, y_0) + \lambda_0 g_x(x_0, y_0) = 0$
> >         *   $f_y(x_0, y_0) + \lambda_0 g_y(x_0, y_0) = 0$
> > 
> > 6.  **Lagrangeova funkcija:**
> >     *   Te pogoje lahko elegantno zberemo z uvedbo **Lagrangeove funkcije** $L(x,y,\lambda) = f(x,y) + \lambda g(x,y)$.
> >     *   Stacionarne točke te funkcije najdemo tako, da vse njene parcialne odvode izenačimo z nič:
> >         *   $\frac{\partial L}{\partial x} = f_x(x,y) + \lambda g_x(x,y) = 0$
> >         *   $\frac{\partial L}{\partial y} = f_y(x,y) + \lambda g_y(x,y) = 0$
> >         *   $\frac{\partial L}{\partial \lambda} = g(x,y) = 0$ (Ta zadnji pogoj zagotavlja, da je točka $(x,y)$ dejansko na vezni krivulji.)
> > 
> >     Reševanje tega sistema enačb nam da kandidatne točke $(x,y,\lambda)$ za lokalne ekstreme funkcije $f$ pod pogojem $g(x,y)=0$.

***


### Izrek o implicitni funkciji


Imamo implicitno vektorsko enačbo $F(x,y,z,w) = 0$. 

*Če hočemo izraziti ven $z(x,y), w(x,y)$ moramo imeti sistem dveh enačb $\Rightarrow$ dve implicitni enačbi $\Rightarrow$ vektorska funkcija*

$$\color{light} a_{1}x+b_{1}y+z+w = 0$$
$$\color{light}a_{2}x+b_{2}y+z+w = 0$$
$$\color{light}w = -(a_{2}x+b_{2}y+z)$$
$$\color{light}z = (a_{1}-a_{2})x +...$$
$$\color{light}w=...$$
$$\Rightarrow \text{dobimo } w(x,y) = 0,\,  z(x,y) = 0$$

Torej imamo v tem primeru $F_{1}(x,y,z,w) = 0, F_{2}(x,y,z,w) = 0$.

Za formalno postavitev izreka moramo definirati okolje in lastnosti naše implicitne enačbe.

*   **Domena $U$:** Začnemo z odprto množico $U$ v večrazsežnem Evklidskem prostoru $\mathbb{R}^n$. Ta $U$ predstavlja regijo, kjer je naša implicitna enačba definirana.
*   **Razdelitev spremenljivk:** $n$ spremenljivk razdelimo v dve skupini:
    *   $k$ spremenljivk, označene kot $\mathbf{x} = (x_1, \dots, x_k) \in \mathbb{R}^k$. To bodo naše neodvisne spremenljivke.
    *   $m$ spremenljivk, označene kot $\mathbf{y} = (y_1, \dots, y_m) \in \mathbb{R}^m$. To bodo naše odvisne spremenljivke, tiste, ki jih želimo izraziti kot funkcijo $\mathbf{x}$.
    Tako je $n = k+m$, in naša domena $U$ je podmnožica $\mathbb{R}^k \times \mathbb{R}^m$.
*   **Funkcija $F$:** Našo implicitno enačbo predstavlja funkcija $F$, ki preslikava iz $U$ v $\mathbb{R}^m$:
    $$U \subseteq \mathbb{R}^k \times \mathbb{R}^m$$
    $$F: U \to \mathbb{R}^m$$
    Izrek zahteva, da je $F$ **$C^1$-funkcija**, kar pomeni, da vsi njeni parcialni odvodi prvega reda obstajajo in so zvezni na $U$. 
*   **Specifična točka $\mathbf{u}^{(0)} = (\mathbf{x}^{(0)}, \mathbf{y}^{(0)})$:** Izberemo določeno točko $\mathbf{u}^{(0)}$ znotraj naše domene $U$.
*   **Pogoj $F(\mathbf{u}^{(0)}) = \mathbf{0}$:** Ta izbrana točka $\mathbf{u}^{(0)}$ mora zadoščati implicitni enačbi. Ko je funkcija $F$ ovrednotena v $\mathbf{u}^{(0)}$, mora dati ničelni vektor v $\mathbb{R}^m$:
    $$F(\mathbf{x}^{(0)}, \mathbf{y}^{(0)}) = \mathbf{0}$$
    To pomeni, da $\mathbf{u}^0$ leži na nivojski množici (ali konturi), definirani z $F(\mathbf{x}, \mathbf{y}) = \mathbf{0}$.

Najpomembnejši pogoj za Teorem o implicitni funkciji je povezan z odvedljivostjo $F$ v točki $\mathbf{u}^{(0)}$.

*   **Jacobijeva matrika $F$:** Jacobijeva matrika funkcije $F$ v kateri koli točki $(\mathbf{x}, \mathbf{y})$ v $U$ je podana z:
    $$J_F(\mathbf{x}, \mathbf{y}) = \begin{pmatrix}
    \frac{\partial F_1}{\partial x_1} & \dots & \frac{\partial F_1}{\partial x_k} & \frac{\partial F_1}{\partial y_1} & \dots & \frac{\partial F_1}{\partial y_m} \\
    \vdots & \ddots & \vdots & \vdots & \ddots & \vdots \\
    \frac{\partial F_m}{\partial x_1} & \dots & \frac{\partial F_m}{\partial x_k} & \frac{\partial F_m}{\partial y_1} & \dots & \frac{\partial F_m}{\partial y_m}
    \end{pmatrix}$$
    To je $m \times (k+m)$ matrika.
    *Jacobijeva matrika ker je $F$ definirana kot vektorska funkcija s toliko enačbami kolikor spremenljivk hočemo izpostaviti.*
*   **Razdelitev Jacobijanke:** Jacobijevo matriko $J_F$ lahko razdelimo v dve podmatriki glede na našo razdelitev spremenljivk:
    *   Jacobijeva matrika glede na $\mathbf{x}$: $\frac{\partial F}{\partial \mathbf{x}}(\mathbf{x}, \mathbf{y})$ je $m \times k$ matrika.
    *   Jacobijeva matrika glede na $\mathbf{y}$: $\frac{\partial F}{\partial \mathbf{y}}(\mathbf{x}, \mathbf{y})$ je $m \times m$ **kvadratna matrika**.
*   **Pogoj neničelne determinante:** Kritični pogoj Teorema o implicitni funkciji je, da mora biti determinanta $m \times m$ Jacobijeve matrike glede na $\mathbf{y}$, ovrednotena v točki $\mathbf{u}^{(0)}$, neničelna:
    $$\det \left( \frac{\partial F}{\partial \mathbf{y}}(\mathbf{x}^{(0)}, \mathbf{y}^{(0)}) \right) \neq 0$$
    *   **Interpretacija:** Neničelna determinanta pomeni, da je matrika $\frac{\partial F}{\partial \mathbf{y}}(\mathbf{x}^0, \mathbf{y}^0)$ invertibilna (obrnljiva). To je pomebno pri nadaljni izpeljavi odvoda pridobljenih funkcij.

Če so izpolnjeni vsi prejšnji pogoji, Teorem o implicitni funkciji zagotavlja naslednje:

*   **Obstoj odprtih množic:** Obstajajo odprte množice $V_1 \subseteq \mathbb{R}^k$ in $V_2 \subseteq \mathbb{R}^m$, tako da:
    *   $\mathbf{x}^0 \in V_1$ (kar pomeni, da je $V_1$ okolica $\mathbf{x}^0$).
    *   $\mathbf{y}^0 \in V_2$ (kar pomeni, da je $V_2$ okolica $\mathbf{y}^0$).
*   **Obstoj in enoličnost $C^1$-preslikave $\mathbf{g}$:** Obstaja enolična $C^1$-funkcija (zvezno odvedljiva)
    $$\mathbf{g}: V_1 \to V_2$$
    tako da:
    *   $\mathbf{g}(\mathbf{x}^0) = \mathbf{y}^0$.
    *   Za vsak $\mathbf{x} \in V_1$ funkcija zadošča implicitni enačbi:
        $$F(\mathbf{x}, \mathbf{g}(\mathbf{x})) = \mathbf{0}$$
    To pomeni, da se lahko, lokalno okoli točke $\mathbf{u}^0$, implicitna enačba $F(\mathbf{x}, \mathbf{y}) = \mathbf{0}$ eksplicitno reši za $\mathbf{y}$ glede na $\mathbf{x}$ kot $\mathbf{y} = \mathbf{g}(\mathbf{x})$.

Poleg tega, da zagotavlja obstoj $\mathbf{g}$, Teorem o implicitni funkciji ponuja tudi formulo za izračun njenega odvoda, Jacobijeve matrike $\mathbf{g}$, označene z $J_{\mathbf{g}}(\mathbf{x})$. To je izjemno uporabno, kadar ne morete eksplicitno najti izraza za $\mathbf{g}(\mathbf{x})$, vendar vseeno potrebujete njen odvod.

Formula je:
$$J_{\mathbf{g}}(\mathbf{x}) = - \left[ \frac{\partial F}{\partial \mathbf{y}} (\mathbf{x}, \mathbf{g}(\mathbf{x})) \right]^{-1} \left[ \frac{\partial F}{\partial \mathbf{x}} (\mathbf{x}, \mathbf{g}(\mathbf{x})) \right]$$
Razčlenimo komponente te formule:
*   $\left[ \frac{\partial F}{\partial \mathbf{y}} (\mathbf{x}, \mathbf{g}(\mathbf{x})) \right]^{-1}$: To je inverz $m \times m$ Jacobijeve matrike $F$ glede na spremenljivke $\mathbf{y}$, ovrednotene v točki $(\mathbf{x}, \mathbf{g}(\mathbf{x}))$. Njen obstoj je zagotovljen s pogojem neničelne determinante.
*   $\left[ \frac{\partial F}{\partial \mathbf{x}} (\mathbf{x}, \mathbf{g}(\mathbf{x})) \right]$: To je $m \times k$ Jacobijeva matrika $F$ glede na spremenljivke $\mathbf{x}$, prav tako ovrednotena v točki $(\mathbf{x}, \mathbf{g}(\mathbf{x}))$.

Ta formula je izpeljana z uporabo verižnega pravila (natančneje, implicitnega odvajanja) na enačbi $F(\mathbf{x}, \mathbf{g}(\mathbf{x})) = \mathbf{0}$. Omogoča izračun odvodov implicitno definirane funkcije $\mathbf{g}$ brez potrebe po eksplicitni obliki same $\mathbf{g}$.

$$F(\mathbf{x},\mathbf{g(x)}) = 0$$
***

*   $\mathbf{x} = (x_1, \dots, x_k)$ so neodvisne spremenljivke.
*   $\mathbf{y} = (y_1, \dots, y_m)$ so odvisne spremenljivke, kjer $\mathbf{y} = \mathbf{g}(\mathbf{x})$.
*   $F: \mathbb{R}^k \times \mathbb{R}^m \to \mathbb{R}^m$  definira implicitno enačbo $F(\mathbf{x}, \mathbf{y}) = \mathbf{0}$.
*   $\mathbf{g}: \mathbb{R}^k \to \mathbb{R}^m$ je implicitno definirana funkcija $\mathbf{y} = \mathbf{g}(\mathbf{x})$.


Po verižnem pravilu je Jacobijeva matrika $F(\mathbf{x})$ podana z:

$$J_H(\mathbf{x}) = \frac{\partial F}{\partial \mathbf{x}} (\mathbf{x}, \mathbf{g}(\mathbf{x})) + \frac{\partial F}{\partial \mathbf{y}} (\mathbf{x}, \mathbf{g}(\mathbf{x})) J_{\mathbf{g}}(\mathbf{x})$$

Ker je $J_H(\mathbf{x})$ ničelna matrika ($m \times k$ dimenzij), lahko to prepišemo kot:

$$ \frac{\partial F}{\partial \mathbf{x}} (\mathbf{x}, \mathbf{g}(\mathbf{x})) + \frac{\partial F}{\partial \mathbf{y}} (\mathbf{x}, \mathbf{g}(\mathbf{x})) J_{\mathbf{g}}(\mathbf{x}) = \mathbf{0}_{m \times k} $$

**Razpisano v matrični obliki:**

$$dF = 
\begin{pmatrix}
\frac{\partial F_1}{\partial x_1} & \dots & \frac{\partial F_1}{\partial x_k} & \frac{\partial F_1}{\partial y_1} & \dots & \frac{\partial F_1}{\partial y_m} \\
\vdots & \ddots & \vdots & \vdots & \ddots & \vdots \\
\frac{\partial F_m}{\partial x_1} & \dots & \frac{\partial F_m}{\partial x_k} & \frac{\partial F_m}{\partial y_1} & \dots & \frac{\partial F_m}{\partial y_m}
\end{pmatrix}
% J_F, size m x (k+m)
\begin{pmatrix}
1 & \dots & 0 \\
\vdots & \ddots & \vdots \\
0 & \dots & 1 \\
% I_k, size k x k
\frac{\partial g_1}{\partial x_1} & \dots & \frac{\partial g_1}{\partial x_k} \\
\vdots & \ddots & \vdots \\
\frac{\partial g_m}{\partial x_1} & \dots & \frac{\partial g_m}{\partial x_k}
% J_g, size m x k
\end{pmatrix}
% M, size (k+m) x k
 \begin{pmatrix} dx_1 \\ \vdots \\ dx_k \end{pmatrix}
$$

$$\Rightarrow$$

$$F' = \begin{pmatrix}
\frac{\partial F_1}{\partial x_1} & \dots & \frac{\partial F_1}{\partial x_k} & \frac{\partial F_1}{\partial y_1} & \dots & \frac{\partial F_1}{\partial y_m} \\
\vdots & \ddots & \vdots & \vdots & \ddots & \vdots \\
\frac{\partial F_m}{\partial x_1} & \dots & \frac{\partial F_m}{\partial x_k} & \frac{\partial F_m}{\partial y_1} & \dots & \frac{\partial F_m}{\partial y_m}
\end{pmatrix}
% J_F, size m x (k+m)
\begin{pmatrix}
1 & \dots & 0 \\
\vdots & \ddots & \vdots \\
0 & \dots & 1 \\
% I_k, size k x k
\frac{\partial g_1}{\partial x_1} & \dots & \frac{\partial g_1}{\partial x_k} \\
\vdots & \ddots & \vdots \\
\frac{\partial g_m}{\partial x_1} & \dots & \frac{\partial g_m}{\partial x_k}
% J_g, size m x k
\end{pmatrix}
% M, size (k+m) x k
$$


Jacobijeva matrika $F$ glede na $\mathbf{x}$ je $m \times k$ matrika:

$$ \frac{\partial F}{\partial \mathbf{x}} = \begin{pmatrix}
    \frac{\partial F_1}{\partial x_1} & \dots & \frac{\partial F_1}{\partial x_k} \\
    \vdots & \ddots & \vdots \\
    \frac{\partial F_m}{\partial x_1} & \dots & \frac{\partial F_m}{\partial x_k}
\end{pmatrix} $$

Jacobijeva matrika $F$ glede na $\mathbf{y}$ je $m \times m$ matrika:
$$ \frac{\partial F}{\partial \mathbf{y}} = \begin{pmatrix}
    \frac{\partial F_1}{\partial y_1} & \dots & \frac{\partial F_1}{\partial y_m} \\
    \vdots & \ddots & \vdots \\
    \frac{\partial F_m}{\partial y_1} & \dots & \frac{\partial F_m}{\partial y_m}
\end{pmatrix} $$

Jacobijeva matrika $\mathbf{g}$ glede na $\mathbf{x}$ je $m \times k$ matrika:
$$ J_{\mathbf{g}}(\mathbf{x}) = \begin{pmatrix}
    \frac{\partial g_1}{\partial x_1} & \dots & \frac{\partial g_1}{\partial x_k} \\
    \vdots & \ddots & \vdots \\
    \frac{\partial g_m}{\partial x_1} & \dots & \frac{\partial g_m}{\partial x_k}
\end{pmatrix} $$

Vsi parcialni odvodi so ovrednoteni v točki $(\mathbf{x}, \mathbf{g}(\mathbf{x}))$.

Torej, enačba v matrični obliki je:

$$
\begin{pmatrix}
    \frac{\partial F_1}{\partial x_1} & \dots & \frac{\partial F_1}{\partial x_k} \\
    \vdots & \ddots & \vdots \\
    \frac{\partial F_m}{\partial x_1} & \dots & \frac{\partial F_m}{\partial x_k}
\end{pmatrix}
+
\begin{pmatrix}
    \frac{\partial F_1}{\partial y_1} & \dots & \frac{\partial F_1}{\partial y_m} \\
    \vdots & \ddots & \vdots \\
    \frac{\partial F_m}{\partial y_1} & \dots & \frac{\partial F_m}{\partial y_m}
\end{pmatrix}
\begin{pmatrix}
    \frac{\partial g_1}{\partial x_1} & \dots & \frac{\partial g_1}{\partial x_k} \\
    \vdots & \ddots & \vdots \\
    \frac{\partial g_m}{\partial x_1} & \dots & \frac{\partial g_m}{\partial x_k}
\end{pmatrix}
=
\begin{pmatrix}
    0 & \dots & 0 \\
    \vdots & \ddots & \vdots \\
    0 & \dots & 0
\end{pmatrix}
$$



>[!|hide]- Primer
> **Scenarij:** Imamo sistem dveh enačb, ki implicitno določata dve spremenljivki ($y_1, y_2$) kot funkcijo drugih dveh spremenljivk ($x_1, x_2$).
> 
> **1. Definicija spremenljivk in funkcije $F$:**
> 
> *   **Neodvisne spremenljivke:** $\mathbf{x} = (x_1, x_2) \in \mathbb{R}^2$ ($k=2$)
> *   **Odvisne spremenljivke:** $\mathbf{y} = (y_1, y_2) \in \mathbb{R}^2$ ($m=2$)
> *   **Funkcija $F: \mathbb{R}^2 \times \mathbb{R}^2 \to \mathbb{R}^2$**, definirana z:
>     $$F(x_1, x_2, y_1, y_2) = \begin{pmatrix} F_1(x_1, x_2, y_1, y_2) \\ F_2(x_1, x_2, y_1, y_2) \end{pmatrix} = \begin{pmatrix} x_1 y_1 + x_2 y_2 - 3 \\ x_1 y_2 - x_2 y_1 - 1 \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \end{pmatrix}$$
>     Naš cilj je ugotoviti, ali lahko okoli neke točke $(x_1^0, x_2^0, y_1^0, y_2^0)$ izrazimo $y_1$ in $y_2$ kot funkciji $x_1$ in $x_2$, torej najti funkcijo $\mathbf{g}(x_1, x_2) = (y_1(x_1, x_2), y_2(x_1, x_2))$.
> 
> **2. Izbira točke $\mathbf{u}^0 = (\mathbf{x}^0, \mathbf{y}^0)$, ki zadošča $F(\mathbf{u}^0) = \mathbf{0}$:**
> 
> Izberimo $\mathbf{x}^0 = (1, 2)$. Poiščimo ustrezne $y_1^0, y_2^0$:
> *   $1 \cdot y_1^0 + 2 \cdot y_2^0 - 3 = 0 \Rightarrow y_1^0 + 2y_2^0 = 3$
> *   $1 \cdot y_2^0 - 2 \cdot y_1^0 - 1 = 0 \Rightarrow -2y_1^0 + y_2^0 = 1$
> 
> Rešimo ta sistem linearnih enačb za $y_1^0$ in $y_2^0$:
> Iz druge enačbe: $y_2^0 = 1 + 2y_1^0$. Vstavimo v prvo:
> $y_1^0 + 2(1 + 2y_1^0) = 3$
> $y_1^0 + 2 + 4y_1^0 = 3$
> $5y_1^0 = 1 \Rightarrow y_1^0 = 1/5$
> Sedaj izračunamo $y_2^0$: $y_2^0 = 1 + 2(1/5) = 1 + 2/5 = 7/5$.
> 
> Torej, naša točka je $\mathbf{u}^0 = (x_1^0, x_2^0, y_1^0, y_2^0) = (1, 2, 1/5, 7/5)$.
> 
> **3. Preverjanje pogojev Teorema o implicitni funkciji:**
> 
> *   **Gladkost $F$:** Funkcija $F$ je sestavljena iz polinomov, zato je $C^1$ (in celo $C^\infty$) povsod na $\mathbb{R}^4$. Ta pogoj je izpolnjen.
> *   **Ničelna vrednost $F$ v $\mathbf{u}^0$:** To smo zagotovili z izbiro $\mathbf{y}^0$.
> 
> *   **Ključni pogoj: Jacobijeva matrika glede na $\mathbf{y}$ in njena determinanta:**
>     Izračunajmo parcialne odvode $F_1$ in $F_2$ glede na $y_1$ in $y_2$:
>     $$\frac{\partial F}{\partial \mathbf{y}}(x_1, x_2, y_1, y_2) = \begin{pmatrix}
>     \frac{\partial F_1}{\partial y_1} & \frac{\partial F_1}{\partial y_2} \\
>     \frac{\partial F_2}{\partial y_1} & \frac{\partial F_2}{\partial y_2}
>     \end{pmatrix} = \begin{pmatrix}
>     x_1 & x_2 \\
>     -x_2 & x_1
>     \end{pmatrix}$$
>     Sedaj ovrednotimo to matriko v točki $\mathbf{u}^0 = (1, 2, 1/5, 7/5)$:
>     $$\frac{\partial F}{\partial \mathbf{y}}(\mathbf{u}^0) = \begin{pmatrix}
>     1 & 2 \\
>     -2 & 1
>     \end{pmatrix}$$
>     Izračunajmo determinanto:
>     $$\det \left( \frac{\partial F}{\partial \mathbf{y}}(\mathbf{u}^0) \right) = (1)(1) - (2)(-2) = 1 - (-4) = 5$$
>     Ker je determinanta $5 \neq 0$, je ključni pogoj izpolnjen!
> 
> **4. Zaključek Teorema o implicitni funkciji:**
> 
> Ker so vsi pogoji izpolnjeni, Teorem o implicitni funkciji zagotavlja:
> *   Obstajata odprti okolici $V_1 \subseteq \mathbb{R}^2$ okoli $\mathbf{x}^0 = (1, 2)$ in $V_2 \subseteq \mathbb{R}^2$ okoli $\mathbf{y}^0 = (1/5, 7/5)$.
> *   Obstaja **enolična $C^1$-funkcija $\mathbf{g}: V_1 \to V_2$**,
>     $$\mathbf{g}(x_1, x_2) = (y_1(x_1, x_2), y_2(x_1, x_2))$$
>     tako da velja $\mathbf{g}(1, 2) = (1/5, 7/5)$ in za vsak $(x_1, x_2) \in V_1$:
>     $$F(x_1, x_2, y_1(x_1, x_2), y_2(x_1, x_2)) = \begin{pmatrix} 0 \\ 0 \end{pmatrix}$$
>     To pomeni, da lahko *lokalno* okoli točke $(1, 2, 1/5, 7/5)$ izrazimo $y_1$ in $y_2$ kot funkciji $x_1$ in $x_2$, čeprav eksplicitne oblike funkcij $y_1(x_1, x_2)$ in $y_2(x_1, x_2)$ morda ne znamo najti.
> 
> **5. Izračun odvoda implicitne funkcije $\mathbf{g}$ (Jacobijeva matrika $J_{\mathbf{g}}$):**
> 
> Teorem nam omogoča tudi izračun Jacobijeve matrike funkcije $\mathbf{g}$ v točki $\mathbf{x}^0$, ne da bi poznali eksplicitno obliko $\mathbf{g}$. Formula je:
> $$J_{\mathbf{g}}(\mathbf{x}) = - \left[ \frac{\partial F}{\partial \mathbf{y}} (\mathbf{x}, \mathbf{g}(\mathbf{x})) \right]^{-1} \left[ \frac{\partial F}{\partial \mathbf{x}} (\mathbf{x}, \mathbf{g}(\mathbf{x})) \right]$$
> Izračunajmo najprej $\frac{\partial F}{\partial \mathbf{x}}$:
> $$\frac{\partial F}{\partial \mathbf{x}}(x_1, x_2, y_1, y_2) = \begin{pmatrix}
> \frac{\partial F_1}{\partial x_1} & \frac{\partial F_1}{\partial x_2} \\
> \frac{\partial F_2}{\partial x_1} & \frac{\partial F_2}{\partial x_2}
> \end{pmatrix} = \begin{pmatrix}
> y_1 & y_2 \\
> y_2 & -y_1
> \end{pmatrix}$$
> Ovrednotimo jo v točki $\mathbf{u}^0 = (1, 2, 1/5, 7/5)$:
> $$\frac{\partial F}{\partial \mathbf{x}}(\mathbf{u}^0) = \begin{pmatrix}
> 1/5 & 7/5 \\
> 7/5 & -1/5
> \end{pmatrix}$$
> Potrebujemo tudi inverz $\left[ \frac{\partial F}{\partial \mathbf{y}} (\mathbf{u}^0) \right]^{-1}$:
> $$\left[ \begin{pmatrix} 1 & 2 \\ -2 & 1 \end{pmatrix} \right]^{-1} = \frac{1}{5} \begin{pmatrix} 1 & -2 \\ 2 & 1 \end{pmatrix}$$
> Sedaj izračunajmo $J_{\mathbf{g}}(\mathbf{x}^0)$:
> $$J_{\mathbf{g}}(\mathbf{x}^0) = - \left( \frac{1}{5} \begin{pmatrix} 1 & -2 \\ 2 & 1 \end{pmatrix} \right) \left( \begin{pmatrix} 1/5 & 7/5 \\ 7/5 & -1/5 \end{pmatrix} \right)$$
> $$J_{\mathbf{g}}(\mathbf{x}^0) = - \frac{1}{25} \begin{pmatrix} 1 & -2 \\ 2 & 1 \end{pmatrix} \begin{pmatrix} 1 & 7 \\ 7 & -1 \end{pmatrix}$$
> Pomnožimo matriki:
> $$J_{\mathbf{g}}(\mathbf{x}^0) = - \frac{1}{25} \begin{pmatrix} (1)(1)+(-2)(7) & (1)(7)+(-2)(-1) \\ (2)(1)+(1)(7) & (2)(7)+(1)(-1) \end{pmatrix}$$
> $$J_{\mathbf{g}}(\mathbf{x}^0) = - \frac{1}{25} \begin{pmatrix} 1-14 & 7+2 \\ 2+7 & 14-1 \end{pmatrix}$$
> $$J_{\mathbf{g}}(\mathbf{x}^0) = - \frac{1}{25} \begin{pmatrix} -13 & 9 \\ 9 & 13 \end{pmatrix} = \begin{pmatrix} 13/25 & -9/25 \\ -9/25 & -13/25 \end{pmatrix}$$
> 
> **Pomen rezultata:**
> Jacobijeva matrika $J_{\mathbf{g}}(\mathbf{x}^0)$ nam pove, kako se $y_1$ in $y_2$ spreminjata, ko se $x_1$ in $x_2$ spreminjata v bližini točke $\mathbf{x}^0=(1,2)$.
> *   $\frac{\partial y_1}{\partial x_1} (\mathbf{x}^0) = 13/25$
> *   $\frac{\partial y_1}{\partial x_2} (\mathbf{x}^0) = -9/25$
> *   $\frac{\partial y_2}{\partial x_1} (\mathbf{x}^0) = -9/25$
> *   $\frac{\partial y_2}{\partial x_2} (\mathbf{x}^0) = -13/25$
> 
> Ta primer jasno prikazuje, kako Teorem o implicitni funkciji potrjuje obstoj lokalne funkcijske odvisnosti in nam omogoča izračun odvodov te funkcije, tudi če je eksplicitno ne moremo izraziti.






***






> Izrek o implicitni funkciji
> 
> Naj bo $F$, $k$ spremenljivk, ki je $r$-krat zvezno odvedljiva v okolici točke $a \in \mathbb{R}^{k}$. 
> 
> Če velja $F(a)= 0$ in $\frac{\partial F}{\partial x_{k}}(a)\neq 0$ potem obstaja 
> 
> \- okolica $U$ točke $a'=(a_{1},...,a_{k-1}) \in \mathbb{R}^{k-1}$, 
>\- okolica $V$ točke $a_{k}$ ter 
>\- $r$-krat odvedljiva funkcija $k-1$ spremenljivk $g: U \rightarrow V$, 
> $\,\,\,$za katero velja:
> 
> $$g(a') = a_{k}$$
> $$\forall  t \in U,\, \forall  x_{k} \in V : F(t, x_{k}) = 0 \Leftrightarrow x_{k} = g(t)$$
> $$\forall i \in \{ 1,...,k-1\},\,\forall t \in U:  \frac{\partial g}{\partial x_{i}}(t) = - \frac{\frac{\partial F}{\partial x_{i}}(t,g(t))}{\frac{\partial F}{\partial x_{k}}(t,g(t))}$$
> >[!|dokaz]+ Dokaz:
> > Naj bo $f: U \to \mathbb{R}$ zvezno odvedljiva funkcija, kjer je $U \subseteq \mathbb{R}^k \times \mathbb{R}$ odprta množica. Predpostavimo, da obstaja točka $(x_0, y_0) \in U$ za katero velja $f(x_0, y_0) = 0$ in $\frac{\partial f}{\partial y}(x_0, y_0) \neq 0$.
> > 
> > Definirajmo preslikavo $F: U \to \mathbb{R}^k \times \mathbb{R}$ s predpisom $F(x, y) = (x, f(x, y))$. Ker je $f$ zvezno odvedljiva, je tudi $F$ zvezno odvedljiva.
> > 
> > Jacobijeva matrika preslikave $F$ v točki $(x_0, y_0)$ je
> > $$ J_F(x_0, y_0) = \begin{pmatrix}
> > I_k & 0 \\
> > \nabla_x f & \frac{\partial f}{\partial y}
> > \end{pmatrix}_{(x_0, y_0)} $$
> > kjer je $I_k$ identična matrika velikosti $k \times k$, $0$ ničelni vektor velikosti $k \times 1$ in $\nabla_x f = \left(\frac{\partial f}{\partial x_1}, \dots, \frac{\partial f}{\partial x_k}\right)$.
> > Determinanta te matrike je $det(J_F(x_0, y_0)) = \frac{\partial f}{\partial y}(x_0, y_0)$. Po predpostavki je ta determinanta različna od nič.
> > 
> > Po izreku o inverzni funkciji obstajata 
> > odprta okolica $U_0 \subseteq U$ točke $(x_0, y_0)$ in 
> > odprta okolica $V_0 \subseteq \mathbb{R}^k \times \mathbb{R}$ točke $F(x_0, y_0) = (x_0, f(x_0, y_0)) = (x_0, 0)$, 
> > 
> > tako da je $F|_{U_0}$ bijekcija iz $U_0$ na $V_0$, in njena inverzna funkcija $F^{-1}: V_0 \to U_0$ je zvezno odvedljiva.
> > 
> > Definirajmo $F^{-1}(u, v) = (h(u, v), k(u, v))$, kjer je $h: V_0 \to \mathbb{R}^k$ in $k: V_0 \to \mathbb{R}$. Iz definicije $F(x, y) = (x, f(x, y))$ sledi, da mora biti $h(u, v) = u$. Torej je $F^{-1}(u, v) = (u, k(u, v))$.
> > 
> > Naj bo $V = \{x \in \mathbb{R}^k \mid (x, 0) \in V_0\}$. $V$ je odprta okolica točke $x_0$. Definirajmo funkcijo $g: V \to \mathbb{R}$ s predpisom $g(x) = k(x, 0)$. Ker je $k$ zvezno odvedljiva (saj je komponenta zvezno odvedljive funkcije $F^{-1}$), je tudi $g$ zvezno odvedljiva.
> > 
> > Preverimo lastnosti funkcije $g$:
> > 1.  **Implicitna zveza:** Za vsak $x \in V$ velja:
> >     $F(x, g(x)) = F(x, k(x, 0))$. Ker je $F^{-1}(x, 0) = (x, k(x, 0))$, je $F(x, k(x, 0)) = F(F^{-1}(x, 0)) = (x, 0)$.
> >     Hkrati po definiciji $F$ velja $F(x, g(x)) = (x, f(x, g(x)))$.
> >     Iz $(x, f(x, g(x))) = (x, 0)$ sledi $f(x, g(x)) = 0$.
> > 2.  **Vrednost v $x_0$:** Ker je $f(x_0, y_0) = 0$, je $F(x_0, y_0) = (x_0, 0)$. Sledi, da je $F^{-1}(x_0, 0) = (x_0, y_0)$.
> >     Iz definicije $F^{-1}(u, v) = (u, k(u, v))$ dobimo $F^{-1}(x_0, 0) = (x_0, k(x_0, 0))$.
> >     Primerjava da $y_0 = k(x_0, 0)$. Po definiciji $g$ je torej $g(x_0) = y_0$.
> > 3.  **Edinstvenost:** Za dani $x \in V$ je iskanje $y$, da $f(x, y) = 0$ in $(x,y) \in U_0$, ekvivalentno iskanju $y$ takega, da $F(x, y) = (x, 0)$ in $(x,y) \in U_0$. Ker je $F|_{U_0}$ bijektivna preslikava na $V_0$, obstaja natanko en takšen $y$, in ta je določen z $y = k(x, 0)$, kar je $g(x)$. S tem je dokazana lokalna edinstvenost funkcije $g$.