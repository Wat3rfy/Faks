


Imamo LP v standardni obliki

$$\begin{array}
\\
\max &c^{T}x \\
\text{p.p.} &Ax \leq b \\ 
&x \geq 0
\end{array}$$

**Metoda simpleksov**

LP naj bo podan z neenačbami in pogoji nenegativnosti:

$$
\begin{aligned}
a_{1,1}x_1 + a_{1,2}x_2 + \dots + a_{1,n}x_n &\le b_1 \\
a_{2,1}x_1 + a_{2,2}x_2 + \dots + a_{2,n}x_n &\le b_2 \\
&\vdots \\
a_{m,1}x_1 + a_{m,2}x_2 + \dots + a_{m,n}x_n &\le b_m
\end{aligned}
$$
$$x_1, x_2, \dots, x_n \ge 0$$

Za uporabo **osnovne variante** mora veljati **$b_1, \dots, b_m \ge 0$**. 

V tem primeru je linearni program v standardni obliki **dopusten**, saj je naša trivialna **začetna dopustna rešitev** kar $x_1 = x_2 = \dots = x_n = 0$.

Z uvedbo **dopolnilnih spremenljivk** $x_{n+1}, x_{n+2}, \dots, x_{n+m}$ neenačbe spremenimo v enačbe.

$$
\begin{aligned}
a_{1,1}x_1 + \dots + a_{1,n}x_n + x_{n+1} &= b_1 \\
&\vdots \\
a_{m,1}x_1 + \dots + a_{m,n}x_n + x_{n+m} &= b_m
\end{aligned}
$$
Pri tem zahtevamo, da so vse spremenljivke nenegativne: $x_{n+1}, \dots, x_{n+m} \ge 0$.

Sistem enačb (skupaj s ciljno funkcijo $z$) zapišemo v obliki **slovarja**. Nove spremenljivke damo na levo stran - **bazne spremenljivke**, prvotne  spremenljivke in prosti člen pa na desno - **nebazne oz. proste spremenljivke**.

V zadnji vrstici napišemo ciljno funkcijo.

$$
\begin{aligned}
x_{n+1} &= b_1 - a_{1,1}x_1 - a_{1,2}x_2 - \dots - a_{1,n}x_n \\
x_{n+2} &= b_2 - a_{2,1}x_1 - a_{2,2}x_2 - \dots - a_{2,n}x_n \\
&\vdots \\
x_{n+m} &= b_m - a_{m,1}x_1 - a_{m,2}x_2 - \dots - a_{m,n}x_n \\
\hline
z &= 0 + c_1x_1 + c_2x_2 + \dots + c_nx_n
\end{aligned}
$$

Slovar je **dopusten**, če so vsi prosti členi ($b_i$) nenegativni.  Tak linearen program je vedno dopusten - $x = 0$ je dopustna rešitev.

V tem primeru lahko za prvo trivialno rešitev vse nebazne spremenljivke damo na $0$.

Bazna dopustna rešitev oz. BDR je rešitev linearnega programa če velja da obstaja slovar, kjer vse nebazne spremenljivke nastavimo na 0, bazne pa so enake prostim členom **in** je dopustna - velja da so vse spremenljivke $\geq 0$.

Na vsakem koraku poskušamo izboljšati trenutno tako, da spremenimo bazo: ena od nebaznih spremenljivk vstopi v bazo, ena od baznih pa izstopi.

1. **Izbira vstopajoče spremenljivke ($x_j$):** V bazo lahko vstopi nebazna spremenljivka, s pozitivnim koeficientom - vrednost kriterijske funkcije se poveča.
2. **Izbira izstopajoče spremenljivke ($x_k$):** Vrednost vstopajoče spremenljivke želimo čim bolj povečati, pogoji nenegativnosti baznih spremenljivk pa to povečanje omejujejo. Izstopajočo izberemo med tistimi, ki povečanje **najbolj omejujejo**.
3. **Preoblikovanje slovarja:** Enačbo z izstopajočo spremenljivko imenujemo **pivotna enačba**. Iz nje na levi strani izrazimo vstopajočo spremenljivko in to vstavimo v vse preostale enačbe slovarja ter v funkcional.

Iteracijo ponavljamo, dokler ni več nobene spremenljivke s pozitivnim koeficientom v funkcionalu. 

Obstaja več strategij za izbiro vstopajoče spremenljivke:
*   **Največji koeficient:** Prinaša največje povečanje na enoto vstopajoče spremenljivke.
*   **Največje povečanje:** Vzame tisto, ki $z$ najbolj poveča (računsko zamudno).
*   **Najboljša smer:** Največji premik vzdolž vektorja $c$.
*   **Najmanjši indeks:** Prepreči cikliranje, a v praksi postopek upočasni.

Veljalo bo da vsak slovar ki sledi iz dopustnega je dopusten. Če dobimo nedopusten slovar - prosti koeficient je negativen - potem smo izbrali napačno izhodno spremenljivko.



> **Izrek o koncu postopka**
> Bazna dopustna rešitev, ki ustreza zadnjemu slovarju simpleksne metode (ko so vsi koeficienti v kriterijski funkciji nepozitivni), je **optimalna rešitev** danega linearnega programa.
> 
> Algoritem se ustavi.
> 
> > [!|dokaz]+ Dokaz:
> > Dokaz temelji na **končnem številu možnih slovarjev** in **lastnostih spreminjanja vrednosti kriterijske funkcije**.
> > 
> > **Strogo naraščanje kriterijske funkcije**
> > Naj bo $z$ vrednost kriterijske funkcije (prosti člen v vrstici za $z$). Pri vsakem koraku izberemo vstopno spremenljivko $x_e$ s pozitivnim koeficientom $c_e > 0$. Če se lahko ta spremenljivka poveča za vrednost $\Delta > 0$, se nova vrednost kriterijske funkcije spremeni v:
> > $$z_{nova} = z_{stara} + c_e \cdot \Delta > z_{stara}$$
> > 
> > Mi imamo v linearnem programu z $n$ omejitvami in $m$ prvotnimi spremenljivkami skupaj $\binom{n+m}{n}$ vseh možnih slovarjev. Ker imamo končno število slovarjev bi se moral z neskončnim izvajanjem nek slovar ponoviti.
> > 
> > Ker se vrednost $z$ strogo veča, se slovar ne more nikoli ponoviti, saj smo v prejšnjih korakih imeli nižje vrednosti $z$. V tem primeru se algoritem ustavi v končnem številu korakov (najde optimalno rešitev ali ugotovi neomejenost).
>>
> > Lahko se zgodi da  je korak **degeneriran**, ko je prosti člen v pivotni vrstici enak $0$. V tem primeru je $\Delta = 0$ in vrednost kriterijske funkcije ostane nespremenjena:
> > $$z_{nova} = z_{stara}$$
> > Čeprav se baza spremeni (zamenjamo bazno in nebazno spremenljivko), se BDR v prostoru ne premakne. Če si sledi zaporedje takšnih degeneriranih korakov, se lahko zgodi, da se vrnemo v že videni slovar. To imenujemo **ciklanje**.
> > 
> > **Preprečevanje ciklanja:**
> > Ciklanje v praksi ni pogosto, teoretično pa se mu izognemo z uporabo  **Blandovega pravila** (izbiranje spremenljivk z najmanjšim indeksom).
> > 
> >  Če uporabljamo Blandovo pravilo, je ciklanje nemogoče. Ker je slovarjev končno mnogo in se ne morejo ponavljati, se algoritem nujno ustavi.



> **Trditev o neomejenosti**
> Če nobena bazna spremenljivka ne omejuje povečanja vstopajoče spremenljivke $x_j$, je linearni program **neomejen**.
>
>  S tem lahko potem parametriziramo **območje vseh optimalnih rešitev**.
> 
> > [!|dokaz]+ Dokaz:
> > Vstopajočo spremenljivko $x_j$ izberemo tako, da ima v kriterijski funkciji pozitiven koeficient ($c_j > 0$). V slovarju so bazne spremenljivke $x_i$ izražene z vstopajočo spremenljivko v obliki:
> > $$x_i = b_i + \dots + a_{ij}x_j$$
> > Če so vsi koeficienti $a_{ij}$ pri vstopajoči spremenljivki $x_j$ v slovarju nenegativni ($\ge 0$), potem nobena bazna spremenljivka ne omejuje njenega naraščanja. Ko povečujemo $x_j$, se vrednosti baznih spremenljivk $x_i$ bodisi povečujejo bodisi ostajajo enake, kar pomeni, da nikoli ne postanejo negativne. 
> > 
> > Ker so vse spremenljivke ob poljubno velikem $x_j$ še vedno nenegativne, rešitev ostaja dopustna. Ker pa ima $x_j$ v kriterijski funkciji pozitiven koeficient, vrednost funkcije $z$ z naraščanjem $x_j$ neomejeno raste. Tako lahko dobimo BDR s poljubno veliko vrednostjo, kar po definiciji pomeni, da je dani linearni program neomejen.


Časovna zahtevnost je v praksi $m \log_{}{n}$ korakov. So pa neki umetni primeri ki so v eksponentni kompleknosti. Za vsako pravilo povečanja lahko najdemo nek primer ki nam da eksponentno kompleksnost. A to ni realistično.




**Dokaz optimalnosti - Zakaj je zadnji slovar optimalen? **

Naj bo $S$ zadnji slovar, dobljen z metodo simpleksov, ki je ekvivalenten začetnemu (ima isto množico dopustnih rešitev). Naj bo $x$ katerakoli dopustna rešitev tega sistema.
Funkcional pri slovarju $S$ lahko zapišemo kot:
$$ z = v^* + \sum_{k=1}^{n+m} \tilde{c}_k x_k $$

Ker smo v zadnjem koraku in ni več kandidatov za vstopajočo spremenljivko, velja $\tilde{c}_k \le 0$ za vsak $k$. Hkrati velja pogoj nenegativnosti $x_k \ge 0$. 
Posledično je celotna vsota manjša ali enaka $0$, kar pomeni, da je za vsako dopustno rešitev $x$:
$$ z \le v^* $$
Ker bazna dopustna rešitev $x^*$ (kjer so nebazne spremenljivke enake $0$) doseže točno vrednost $v^*$, je $x^*$ optimalna rešitev, $v^*$ pa optimalna vrednost linearnega programa.


**Posebni primeri in robni pogoji**

Pri izbiri spremenljivk lahko naletimo na določene težave:

*   **Kaj, če ni nobenega kandidata za izstopajočo spremenljivko?**
    To se zgodi, če nobena bazna spremenljivka ne omejuje povečanja vstopajoče spremenljivke (vsi koeficienti ob njej so nenegativni v smislu omejitve $x_j \ge - \frac{\tilde{b}_k}{\tilde{a}_{kj}}$). V tem primeru lahko vstopajočo spremenljivko poljubno povečamo, z njo pa raste tudi funkcional. Zato pravimo, da je **linearni program neomejen**.
*   **Kaj, če je več kandidatov za vstop/izstop?**
    Načeloma je vseeno, katerega izberemo, vendar moramo biti pozorni na **izrojene iteracije**, kjer se vrednost kriterijske funkcije ne poveča (povečanje je omejeno na $0$). Če se postopek ne konča, se lahko baza (in s tem celoten slovar) sčasoma ponovi — postopek se **zacikla**. 
    Da to preprečimo, uporabimo **Pravilo najmanjšega indeksa**

***

**Dvofazna simpleksna metoda**

Kaj pa, če začetna rešitev ni dopustna (kateri izmed $b_i < 0$)? 

Torej rešitev $x=0$ ni avtomatično dopustna iz česar smo originalno sklepali da je LP dopusten.

Hočemo ugotoviti ali je LP dopusten - obstaja dopusten $x_{1},...,x_{n}$ ki zadošča omejitvam.

Z dodajanjem nove "umetne" spremenljivke ${\color{green}x_{0}  \geq 0}$ na desni strani ustvarimo nov LP. Veljalo bo da imamo npr. trivialno dopustno rešitev $x_{1},...,x_{n} = 0, x_{0} = \max(|b_{i}|)$ ampak mi ugotavljamo ali je prvotni problem dopustni kjer mora veljati da je $x_{0} = 0$. To pomeni da hočemo minimizirati $x_{0}$ in če ugotovimo da minimalna vrednost $x_{0}$ ni $0$ potem ne obstaja dopustna rešitev za prvotni LP.

<br>

>Pomožni problem je vedno dopusten in omejen
>>[!|dokaz]+ Dokaz:
>> $x_{0} = \max \{|b_{i}|\}, x_{1},...,x_{n} = 0$ je dopustna rešitev.
>> 
>> $-x_{0}$ je omejen z $0$ saj je $x_{0} \geq 0$ oz. $-x_{0} \leq 0$.


> Prvotni linearni program je dopusten natanko tedaj, ko je optimalna vrednost pomožnega problema enaka $0$.
> 
> > [!|dokaz]+ Dokaz:
> > 
> > $(\Rightarrow)$ Naj bo $(x_1, \dots, x_n)$ dopustna rešitev začetnega LP. To pomeni, da velja $\sum a_{ij}x_j \le b_i$ za vse $i$. Če v pomožnem problemu nastavimo $x_0 = 0$, dobimo dopustno rešitev $(0, x_1, \dots, x_n)$ z vrednostjo kriterijske funkcije $-x_0 = 0$. Ker smo že ugotovili, da je $0$ največja možna vrednost pomožnega problema (saj je $x_0 \ge 0$), je ta rešitev nujno optimalna.
> > 
> > $(\Leftarrow)$ Naj bo $0$ optimalna vrednost pomožnega problema. To pomeni, da obstaja optimalna rešitev oblike $(x_0, x_1, \dots, x_n)$, kjer je $x_0 = 0$. Če ta $x_0$ vstavimo v omejitve pomožnega problema $\sum a_{ij}x_j - x_0 \le b_i$, dobimo $\sum a_{ij}x_j \le b_i$. To pa so natanko omejitve začetnega LP, kar pomeni, da je vektor $(x_1, \dots, x_n)$ dopustna rešitev začetnega problema.


**I. faza (Iskanje začetne dopustne rešitve):**
1. Uvedemo **umetno spremenljivko** $x_0$, ki jo prištejemo desnim stranem slovarja in zanjo zahtevamo $x_0 \ge 0$.
2. Za začasni funkcional vzamemo $w = -x_0$.
3. V bazo vključimo $x_0$, iz nje pa odstranimo tisto bazno spremenljivko, ki ima najbolj negativno vrednost (najmanjši prosti člen). Tako na silo dobimo dopusten slovar.
4. Uporabimo standardno metodo simpleksov in maksimiziramo $w$. 
    *   Če postopek končamo in je $w \neq 0$, to pomeni, da je začetni problem **nedopusten**.
    *   Če se konča in je $w = 0$, smo našli dopustno bazo. Spremenljivko $x_0$ odstranimo in nadaljujemo v drugo fazo.

**II. faza (Standardni postopek):**
Iz slovarja izpustimo vse člene z $x_0$. Funkcional zamenjamo nazaj za pravi funkcional $z = c^Tx$ in ga izrazimo z nebaznimi spremenljivkami trenutnega slovarja. Nato metodo simpleksov izvajamo po običajnem postopku.

> **Osnovni izrek linearnega programiranja**
> 
> Za vsak LP v standardni obliki velja točno ena od naslednjih možnosti:
> 1. Je bodisi **nedopusten** bodisi **neomejen** bodisi **ima optimalno rešitev**.
> 2. Če ima dopustno rešitev, potem ima tudi **bazno dopustno rešitev**.
> 3. Če ima optimalno rešitev, potem ima tudi **bazno optimalno rešitev**.


***
