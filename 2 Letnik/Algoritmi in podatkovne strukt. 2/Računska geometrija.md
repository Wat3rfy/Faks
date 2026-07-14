Točka je lahko predstavljena s polarnimi ali kratezičnimi koordinatami.

Krajevni vektor v $\mathbb{R}^{2}$ je usmerjena puščica predstavljena z $(x,y)$. Vektor med dvema točkama je razlika njunih krajevnih vektorjev.

Vektorski produkt je definiran v treh dimenzijah in vrne vektor pravokoten na ravnino ki jo napenjata faktorja. Dolžina dobljenega vektorja je enaka ploščini paralelograma ki ga napenjata vektorja.

Kot med vektorjema merimo v **nasprotni smeri urinega kazalca**.

Vektorski produkt v dveh dimenzijah $(z = 0)$ je samo

$$(x_1, y_1) \times (x_2, y_2) = \begin{vmatrix} x_1 & x_2 \\ y_1 & y_2 \end{vmatrix} = x_1 y_2 - x_2 y_1 $$

Če imamo dva vektorja in je vektorski prod. večji od 0 potem pravimo da imamo **levi zasuk**, če je vektorski prod. negativen imamo **negativen zasuk**. *Gledamo sinus kota med vektorji.*

Večkotnik je podan z zaporedjem vozlišč $A_{1,...,n}$v nasprotni smeri urinega kazalca.

Predpostavljamo $A_{n+1} = A_{1} ,... A_{n+k}=A_{k}$.

Poznamo **konveksen** večkotnik. Konevksen vsebuje vse točke daljice med polj. točkama, oz. velja

$$\forall x,y \in A\,, \lambda \in [0,1]:$$
$$\lambda x + (1-\lambda)y \in A$$

Če ni konveksen je nekonveksen.

Karakterizacije je da vsi koti tvorijo **levi zasuk**.

**Konveksna ovojnica** množice $A$ je najmanjša konveksna množica ki vsebuje $A$. **Predpostavljamo da mn. vsebuje vsaj $3$ nekolinearne elemente.**

Za iskanje konveksne množice uporabljamo Grahamov algoritem.

1. Vzamemo točko z najmanjšo $y$ koord., če jih je več vzamemo najbolj levo. Naj bo to $p_{1}= (x_{1},y_{1})$.
2. Ostale točke uredimo po naraščajočem kotu glede na premico $y = y_{1}$.
   Kot vektorja $p_{1}p_{i}$ je večji od $p_{1}p_{j}$ če velja $p_{1}p_{i} \times p_{1}p_{j} > 0$ *ker je $p_{1}p_{i}$ na levi glede na $p_{i}p_{j}$* Torej za urejanje lahko uporabimo quicksort kjer dva vektorja primerjamo z vek. produktom.
   Ker je $p_{1}$ najbolj levo spodaj za vse $p_{1}p_{i} \times  (0,1)> 0$ oz vsi vektorji so levo od vodoravne premice.
3. Sedaj vzdržujemo sklad. Začenmo s $p_{1}$, nalagamo po naraščajočem kotu v nasprotni smeri urinega kazalca. Naj bo $(S,p_{i})$ vektor, kjer je $S$ točka na vrhu sklada. Primerjamo $S-1,S$ in $S,p_{i}$ če je vekt. prod. negativen pomeni da smo zavili desno. V tem primeru odvzamemo $S$ in dodamo $p_{i}$ in nadaljujemo.

> **Trditev:** Po obravnavi $p_{i}$ so na skladu točke ki tvorijo konv. ovojnico $p_{1},...,p_{i}$.
> >[!|dokaz]+ Dokaz:
> > Za $i=3$ drži. Predpostavimo da drži za $i-1$. Torej imamo konv. ovojnico za $p_{1},...,p_{i-1}$. Ker so vse točke urejene po kotu $p_{i}$ gotovo leži zunaj ovojnice. Ko jo dodajmo na vrh sklada preverimo zasuk.
> > Če točke $s_{k-1}, s_k, p_i$ tvorijo **levi zasuk**, je meja konveksna. Točko $p_i$ dodamo na sklad in končamo.
> > 
> > Če tvorijo **desni zasuk**, točka $s_k$ ustvari vdrtino in ne more biti del konveksne ovojnice. Odstranimo jo s sklada in preverjanje ponavljamo za točke pod njo, dokler ne dobimo levega zasuka.
> > 
> > Ko odstranimo vse točke, ki povzročajo desne zasuke, in na vrh sklada končno dodamo $p_i$, so na njem le tiste točke, ki tvorijo pravilno konveksno ovojnico za $\{p_1, \dots, p_i\}$. 

Časovna zahtevnost:
- urejanje točk $O(n \log_{}{n})$
- iterativna obravnava točk $O(n)$
- $\Rightarrow O(n \log_{}{n})$


***

Podano imamo množico z $n \geq 2$ točkami. Hočemo poiskati najbližji si točki.

Z naivnim pristopom rešimo v $O(n^{2})$.

Na začetku izdelamo tabeli $X$ in $Y$. $X$ vsebuje točke po naraščujoči $x$ koord., $Y$ pa po naraščujoči $y$ koord.

Predpostavimo da so indeksi točk urejeni po $x$ koordinati, če sta $x$ koord. enaki pa po $y$.

$$i < j \Leftrightarrow x_{i} < x_{j} \,\veebar\, x_{i}=x_{j}, y_{i}< y_{j} $$

Ustvarimo navpično premico ki razdeli točke na $\lfloor\frac{n}{2}\rfloor$ levo od nje kar bo $T_{L}$, desno pa $T_{R}$.

Rekurzivno poiščemo najbližji par v $T_{L}$ in $T_{R}$.

Da združimo rešitve iz $T_{L}$ in $T_{R}$ preverimo najbližji par iz $T_{L}$ in $T_{R}$ in najbližji pari med $x \in T_{L},y \in  T_{R}$.

Najprej vzamemo min. razdaljo najbližjih točk iz $T_{L}$ in $T_{R}$ kar naj bo $\delta$. Potem s to vrednostjo ustvarimo pas centriran v prvotni navpični premici in primerjamo vse kombinacije parov točk iz $T_L$ in $T_{R}$ v tem pasu.

Nato za vsako točko po naraščujočem $y$ gledamo pravokotnik $\delta \times 2\delta$ v katerem je lahko maksimalno 6 točk z razdaljo $\delta$, torej moramo preveriti 6 točk *5 točk če so vse v pravokotniku in še eno če je ena točka preveč v pravokotniku* da lahko sklepamo da je ta točka oddaljena za več kot $\delta$ od vseh ostalih. Torej je časovna kompleknost tega koraka konstantna.

$O(n \log_{}{n})$ za urejanje elementov in izdelavo tabel $X,Y$. $O(n)$, za izdelavo, $X_{L},X_{R},Y_{L},Y_{R}$, $O(n)$ za obravnavo v pravoktnikih, 

$$T(n) = 2T\left(\frac{n}{2}\right)+ \Theta(n)$$

kar je

$$O(n \log_{}{n})$$

**Presečišča daljic**

Hočemo algoritem kjer je računska zahtevnost odvisna od presečišč.

Uporabimo vodoravno premico ki jo pomikamo navzdol in sledimo številu daljic ki jih seka, te shranimo v urejeno dvojiško drevo ki ga imenujemo **status** $S$, urejene naraščajoče po koordianti $x$ začetnega krajišča.

Daljici ki sta v urejenem seznamu drug zraven druge sta sosednji. Za iskanje presečišč bomo preverjali samo sosednje daljice.

Hkrati vzdržujemo kopico dogodkov $E$ v kateri shranjujemo vsa krajišča daljic in najdena presečišča, kjer je kopica urejena padajoče po $y$ komponenti.

Najprej vse daljice podane z $(t_{i},t_{i}')$ shranimo v $U = \{ t_{i} \,;\; i \in [n]\}$, $L =  \{ t_{i}' \,;\; \in [n]\}$, torej $U$ so zgornja krajišča, $L$ pa spodnja. Nato za vsak $t \in U$ ugotovimo pripadajočo množico daljic $D$ ki se začnejo v tej točki in pripadajoč par $(t,D)$ shranimo v vrsto dogodkov $E$. Za vsako spodnje krajišče v $E$ vstavimo $(t, \emptyset)$.

Dokler kopica dogodkov ni prazna bomo vsak element obravnavali.

Za element $(t,D)$ naj bo $U(t) = D$, naj bo $L(t)$ daljice kjer je $t$ spodnje krajišče, $C(t)$ daljice kjer je $t$ vmesna točka.

Vse daljice v $L(t), C(t)$ odstranimo iz $S$, vanj pa vstavimo daljice $U(t)$, $C(t)$ da popravimo vrstni red.

Če je unija $U(t)$ in $C(t)$ prazna množica, torej da je $t$ spodnje krajišče nekih črt, ki so bile odstranjene, nastavimo $l$ na levega soseda in $r$ na desnega soseda $t$ v $S$ in pogledamo če se črti sekata pod potuojočo premico ter potencialno presečišče vstavimo v $E$ kot $(p, \emptyset)$, še ni noter.

Če ta unija ni prazna množica potem nastavimo $d'$ na skrajno levo daljico iz $U(t) \cup C(t)$ v $S$, $l$ naj bo levi sosed $d'$, pogledamo če se $d'$ in $l$ sekata in po potrebi presečišče dodamo v $E$, $d''$ naj bo skrajno desna v $U(t)$ in $C(t)$, $r$ naj bo desni sosed in spet pogledamo če se sekata ter po potrebi presečišče dodamo v $E$.

To ponavljamo dokler se ne sprazne kopica dogodkov.

Časovno gledano potrebujemo $O(n \log_{}{n})$ za izdelavo $E$, $O(\log_{}{n})$ za vsako operacijo nad $E$ in $S$. Naj bo $m(t)$ število daljic v $t$, rabimo $O(m(t) \log_{}{n})$ za njihovo obelavo. Naj bo $M$ množica vseh dogodkov torej bo $m= \sum_{t \in M}^{}m(t)$, kar bo $m = O(n+k)$.

Vse skupaj bo torej $O(m \log_{}{n}) = O((n+k) \log_{}{n})$

**Ploščina večktonikov**

Ideja je preprosta. Najprej ugotovimo da je asb. vr. vektorskega produkta dveh 2D vektorjev ploščina paralelgorama ki ga razpenjata.

Če pogledamo konveksen večkotnik ki vsebuje središčno točko lahko za $I_{i}$ točko izračunamo vektorski produkt $OI_{i} \times OI_{i+1}$ s čimer dobimo ploščino paralelgorama, to prepolovimo in dobimo ploščino pripadajočega trikotnika. To naredimo za vse nadaljne pare točk da dobimo ploščino.

Da dobimo ploščino nekonveksnega lika bomo naprej prišteli oba konveksna dela, nato bomo odšteli ploščino nekonveksnega dela, ki bo odštela del ki je zunaj lika in podvojen del znotraj lika. Na primeru vidimo da $A_{1}A_{2}$ prišteje notranjost, $A_{3}A_{4}$ podvoji del notranjosti in prišteje zunanjost, nato pa vidimo da del $A_{2}A_{3}$ to prekrivajočo ploščino znotraj lika enkrat odšteje hkrati poa odštejemo še ploščino zunaj lika ki jo dobimo z $A_{3}A_{4}$. 
 
![[Pasted image 20260627183446.png]]

Ker to velja za večkotnika ki vsebujejo središče za splošen večkotnik velja da ga lahko premaknemo v središče in izračunamo po istem postopku.

**Položaj točke glede na večkotnik**

Da ugotovimo če je točka znotraj ali zunaj večkotnika naprej opazimo da bo vsota kotov ki jih tvorijo vektorji med notranjo točko in zunanjimi točkami $\angle I_{i}TI_{i+1}$ znaša $2\pi$.

Če je točka zunaj takega lika je očitno da to ne drži saj se vsi koti pokrajšajo, vsota kotov je lahk le $0$ saj bi drugače pomenilo da ne pridemo do iste točke kjer smo začeli.

**KD drevo**

Je struktura kjer so vsi podatki v listih drevesa, notranja vozlišča pa so namenjena usmerjanju oz. iskanju vrednosti v listih. Če imamo množico elementov kjer je definirna popolna urejenost lahko zgradimo tako drevo.

Začnemo tako da v množici poiščemo sredinski element oz. mediano, vse elemente manjše ali enake damo na levo druge pa na desno, nato pa kličemo grajenje drevesa na levi in desni strani.

Vidimo da je gradnja v $O(n \log_{}{n})$, dejanska gradnja je $\Theta(n)$, urejanje je v $O(n \log_{}{n})$.

Hočemo poiskati vse točke na intervalu $[l,r]$.

Vsako vozlišče v drevesu predstavlja interval $[l_{v},r_{v}]$, če $v$ levi otrok starša $s$ z vrednostjo $n$ velja $(l_{s},n]$, če je $v$ desni otrok starša $s$ z vrednostjo $n$ velja $(n, r_{s}]$.

Pri iskanju $[l,r]$ moramo preveriti če je presek $[l_{v},r_{v}]$ neprazen preverimo če je vozlišče list ali notranje vozlišče, če je list preverimo če je vrednost v intervalu, če je ntoranjo vozl. rekurzivno obdelamo otroka.



Da poiščemo $l$ in $r$ moramo opraviti dve poti do robnih vozlišč kar je $\log_{}{n}$. Ko najdemo vozlišči ki služita kot roba, so vsi drugi intervali vsebovani v $[l,r]$ kar pomeni da samo potujemo čez ta poddrevesa kar bo $O(k).$

S tem dobimo časovno zahtevnost $O(\log_{}{n} + k)$, kjer je $k$ število elementov v množici v intervalu.

**KD drevo v več dimenzijah**

Če imamo drevo za točke v več dimenzijah, moramo za vsako dimenzijo, naj jih bo $n$ imeti svoje nivoje, torej prva dimenzija bo imela nivoje $1,n+1,...$, druga dimenzija $2,n+2,...$, $k$-ta dimenzija $k,n+k,...$

Ko tabelo razdelimo po eni koordinati moramo vedeti katere točke iz druge tabele so tudi na levi oz. desni strani da lahko v naslednjem koraku pravilno razdelimo levo in desno stran po $Y$ in da se ohrani urejenost, zato moramo po tem ko razdelimo array $X$ v $Y$ iterativno preveriti katera točka je na levi strani po $X$ in katera na desni. To nam na vsakem koraku da $\Theta(n)$ korakov.

V naslednjem koraku vzamemo $X_{L},Y_{L}$ kar so točke urejene po $X$ in točke urejene po $Y$ na levi strani $X$, ter jih razdelimo glede na $Y$, potem pa še za $X_{R},Y_{R}$ in jih nato ponovno razporedimo v $X_{L},Y_{L},X_{R},Y_{R}$.


Na začetku za vsako dimenzijo uredimo točke kar nam da $O(n \log_{}{n})$. Gradnja pa traja $T(n) = 2T\left(\frac{n}{2}\right)+ \Theta(n)$ kar je $O(n \log_{}{n})$ skupaj $O(n \log_{}{n})$.

Za iskanje bomo imeli 

Naj bo naše območje omejeno z eno premico navpično premico $p$, ta bo v prvem razpadu na levi strani torej v $1$ od $2$ poddreves, v naslednjem razpadu po $y$ bo v $2$ od skupno $4$ poddreves na naslednjem nivoju se spet razdeli imamo $2$ od $8$ ampak pri naslednjem spet $4$ od $16$ in tako naprej.

Po 2 nivojih deljenja se prostor razdeli na 4 enake dele $n/4$ naša premica pa seka $2$ od teh.


To zapišemo kot

$$M(n) = 2 M \left(\frac{n}{4}\right) + \Theta(1)$$

kar bo

$$O(n^{\frac{1}{2}} + k)$$

Iskanje v 2D se praktično vedno razcepi kar nam da $\sqrt[]{n}$ vozlišč, vsa območja popolnoma znotraj pravokotnika pa le prepišemo kar je $O(k)$.

Intuitivno gledano je $\sqrt[]{n}$ čas iskanja. Recimo da imamo $n$ točk, v vsaki dimenziji naredimo čim bolj enakomerno $n$ razdelitev, dobimo $\sqrt[]{n}$ velike kvadrate, kjer vsaka premica seka $\sqrt[]{n}$ kvadratov, ker vsak kvadrat corresponda z eno potjo ki jo vzamemo v drevesu dobimo $\sqrt[]{n}$ poti za vsako mejo.

*Tako je v 3 dimenzijah rob ploskev ki se dotakne $\sqrt[3]{n}^{2}$ kock oz. $n^{\frac{2}{3}}$, v 4 dimenzijah bi imeli $\sqrt[4]{n}$ kock na dimenzijo in ker je meja volumen se dotaknemo $\sqrt[4]{n}^{3}$ oz. $n^\frac{3}{4}$ kock, torej v splošnem $n^{\frac{k-1}{k}}$.*

**Ponavljanje komponent**

Zaenkrat smo predpostavljali da točke nimajo enakih vrednosti.

Naj se točke ponavljajo, v tem primeru lahko poljubnoi točko $p = (x,y)$ pretvorimo v točko $\hat{p}(x|y,y|x)$, kjer za vsako točko uoprabljamo leksikografski vrstni red za vsako dimenzijo, torej po $X$ primerjamo $xy$ leksikografsko, za $Y$ pa $yx$.

S tem moramo pretvoriti še iskalno območje da iz $I = [x,x'] \times [y,y']$ dobimo $\hat{I} = [(x|-\infty), (x'|\infty|)] \times [(y|-\infty) , (y'|\infty)]$

Če imamo točko $p$ ki leži na levi meji pravokotnika $(x,y)$, ko jo pretvorimo dobimo $(x|y,y|x)$ da bo prva komponenta še vedno v intervalu mora biti $x|y$ v območju na meji torej mora veljati $(x|-\infty) \le (x|y)$ kar očitno je.

Za vse velja

$$(x|-\infty) \le (x|y)$$
$$(x|y) \le (x|\infty) $$
$$ (y|-\infty) \le (y|x)$$
$$(y|x) \le (y|\infty)$$