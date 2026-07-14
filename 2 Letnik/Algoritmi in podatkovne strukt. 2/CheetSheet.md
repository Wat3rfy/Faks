$$\sum_{k=0}^{n}k = \frac{n(n+1)}{2}$$
$$\sum_{0}^{n-1}x^{k} = \frac{x^{n}-1}{x-1}$$
$$\sum_{0}^{\infty}ax^{k} = a \cdot \frac{1}{1-x} \,;\; x \in (-1,1)$$
$$\sum_{1}^{\infty}k \cdot x^{k-1} = \frac{1}{(1-x)^{2}} \,;\; x \in (-1,1)$$

Višina drevesa z $a$ vejami na nivo je

$$h = \lceil \log_{a}{n} \rceil \,;\; \text{$n$ je št. el. v listih }$$
$$h = \lfloor \log_{a}{n} \rfloor \,;\; \text{$n$ je št. el. v drevesu }$$

Kopico z arrayem predstavimo tako da je vozl. na $i$-tem indeksu starš vozlišč na $2i+1$ in $2i+2$. Zgradimo jo v $O(n)$. Začnemo na $\lfloor \frac{i}{2} \rfloor -1$ elementu in ga pogrezamo, tj. primerjanje z otroci kjer ga zamenjamo z večjim od dveh če je potrebno. Vstavljamo tako da el. dodamo na konec in ga dvigujemo dokler gre. El. vzamemo tako da odstranimo koren, ga zamenjamo z zadnjim el. v seznamu in ga pogrezamo. 

Krovni izrek

$$T(n) = a \cdot T\left(\frac{n}{b}\right) + n^{d}$$
$$T(n) = \begin{cases}
 \Theta(n^{d})\,;\; a < b^{d}  \\
 \Theta(n^{d}\log_{}{n})\,;\; a = b^{d}  \\
\Theta( n^{\log_{b}{a}})\,;\; a > b^{d} 
\end{cases} $$

Potujoči trgovec ali najcenejši hamil. cikel
- $g(i,S) = \min_{k \in S}\{ c_{i,k} + g(S,S \setminus k)\}$
- $g(i,S)$ predstavlja njanajcenejšo pot od $i$ do končnega vozl. ki gre čez $S$
- uoprabljamo tabelo $2^{n} \cdot n$, kjer podmnožice predstavljamo z bitnim zapisom

Spuščanje jajc
- $S(n,k) = \min_{i \in \{ 1,...,n\}}  \max \{ S(i-1,k-1), S(n-i,k)\}$
- $S(n,1) = n, S(0,k) = 0$
- $N(s,k) = 1 + N(s-1,k-1) + N(s-1,k)$, $N$ je največje število ki jih lahko poskusimo s $s$ spusti in $k$ jajci


**Amortizacija**
Agregatna metoda
- Izračunamo dejanski čas izvajanja algoritma, delimo s številom operacij in dobimo amortizirano ceno

Računovodska metoda
- Pogledamo če lahko ugotovimo neko izmišljeno ceno za operacije tako da v nobeni točki ne velja da je dejanska cena presegla računovodsko ceno, ki naj bi nam olajšala računanje, potem skupno računovodsko ceno delimo z $n$ in dobimo amortizirano ceno.

Metoda potencialov
- Uvedemo funkcijo ki stanje strukture preslika v potencial $\Rightarrow$ izračunamo računovodsko ceno $\Rightarrow$ izračunamo amortizirano ceno
- Preslika se **stanje**, - razlika v potencialu stanja pred operacijo in stanja po operaciji
- $\Phi(D_{i}) \geq 0 \,;\; \forall i$
- Stanje lahko definiramo odvisno od katerihkoli parametrov strukture, npr. $\Phi(N_{i},C_{i})$  $N_{i}$ število elementov, $C_{i}$ kapaciteta.
- Naj bi pokazali $\sum_{}^{}c_{i} \leq \sum_{}^{}\hat{c_{i}}$
$$\hat{c}_{i} = c_{i-1} + \Phi_{D_{i+1}}-\Phi_{D_{i}}$$
- Za reševanje nalog poiščemo lastnost strukture ki se spremeni med operacijami
- Izračunamo razliko potencialov, preverimo da se ujema z drugimi operacijami, seštejemo razlike od $1$ do $n$ da dobimo končno enačbo za $\phi(n)$.
$$\sum_{i=1}^n c_i = \sum_{i=1}^n \hat{c}_i - \left(\Phi(D_n) - \Phi(D_0)\right)$$


**Požrešne metode**

Največ intervalov v času
- Uredimo po naraščajočih končnih časih
- Izbiramo tiste ki se ne prekrivajo naraščajoče
- Dokaz: predp. da $O$ začne z interv. $O_{1}$ mi izberemo $I_{1}$ ki se konča prej ali enako, to pomeni da imamo na izbiro vse intervale ki jih ima na voljo $O$ ali boljše, za vsako naslednjo izbiro izberemo $O_{k}$ ali pa interval ki se prej konča, ker imamo še vedno na izbiro vse intervale kot $O$ bo naša rešitev večja ali pa enaka kot $O$.

Minimizacija maks. zamude
- $n$ opravil, $t_{i}$ trajanje, $d_{i}$ pričakovan konec
- Določitev $s_i$ časov začetka da bo maksimalan zamuda najmanjša
- $f_{i} = s_{i}+t_{i}$, $l_{i} = f_{i}-d_{i}$, $\min(\max_{i} l_{i})$
- Razvrstimo jih po naraščajočih rokih $d_{i}$
- Za razpored ki ga dobimo velja da je strnjen in nima inverzij
- Dokažemo da vsak razpored lahk pretvorimo v razpored s temi lastnostmi, strnjenost je trivialna - če ima $O$ luknje se jih znebimo - zamuda se lahko le zmanjša
- Inverzija je ko velja $s_{i}<s_{j}$ ampak $d_{j}<d_{i}$, če obstaja potem obstaja sosednja inverzija, za ti velja
	- $s\rightarrow d_{1}\rightarrow f_{2}\rightarrow d_{2}\rightarrow f_{1}$
	- $l_{1}=s+t_{2}+t_{1}-d_{1} \quad,\quad l_{2}=s+t_{2}-d_2$
	- $l_{1}' = s+ t_{1} -d_{1}$, $l_{2}'= s + t_{1}+ t_{2}-d_{2}$
	- $l_{1}'<l_{1}$, $l_{2}' < l_{1}$
	- $\max(l_{1}',l_{2'})< \max(l_1,l_{2})$

Huffmanovo kodiranje
- $\gamma(c)$ je dolžina kode, $f_{c}$ je frekvenca
- Hočemo minimizirati $\sum_{c}^{}f_{c} \cdot \gamma(c)$
- Dokažemo da je drevo ki ima znaka z min. frekvencama v ne listnih vozl. bo drevo ki jih ima gotovo manjše ali enako
- Dokažemo da je opt. drevo ki ima v listu $z$ s $f_{z} = f_{x}+f_{y}$ enako opt. drevesu ki ima znaka v listih s $f_x$, $f_{y}$, $z$ pa postane njun starš.

Naivni pristop k iskanju niza $P$ v nizu $T$
- $O(nm)$ ker gremo čez $m$ črk $n$-krat

Rabin-Karpov algoritem

- Računanje potenc $|\Sigma|^{0},...,|\Sigma|^{|P|-1}$ - za vsako črko rabimo svoj simbol zato bodo simboli $0,...,|\Sigma|-1$
- Za $P$ izračunamo $f(P) = \sum_{}^{}|\Sigma|^{i} \cdot f(c_{i})$
  Obe operaciji sta $O(|P|)$.
- Za vsak odmik $s$ lahko izračunamo $f(T_{s}[1 : m])$ ampak tak algoritem da $O(nm)$ kar ni bolje
- $f(T_{s}[1:m])$ moramo računati po postopku
  $$|\Sigma| \cdot ({\color{orange}f(T_{s}[1:m])} - {\color{green}|\Sigma|^{m-1}f(T_{s}[1])}) + f(T_{s}[m+1])$$
- Če je $P$ prevelik uporabimo modul
- Če imamo $|\Sigma|$ je nizov dolžine $n$ natanko $|\Sigma|^{n}-1$ torej imajo vsi taki nizi vrednosti od $[0,|\Sigma|^{n}-1]$.
- To nam da čas. kompl. $O(mn)$ ampak je v praksi $O(n+m)$, če ni koliziij.

**Iskanje podniza s končnimi avtomati**

*   **Stanja avtomata** $0, 1, ..., |P|$ predstavljajo dolžino trenutno ujemajočega se predpone (prefiksa) vzorca $P$. Za vsak znak $a \in \Sigma$ potrebujemo definiran prehod.
*   **Začetno stanje** je $0$ (nič ujemanj), **sprejemno stanje** pa je $|P|$ (celoten vzorec je najden).
*   **Prehodno funkcijo** $\delta(q, a)$ (kjer je $q$ trenutno stanje in $a$ prebrani znak) je definiran kot dolžina najdaljše predpone vzorca $P$, ki je hkrati pripona $P[1:q]a$. *Torej ko dodamo $a$ pogledamo od zadaj nazaj najdaljši del ki se ujema z začetkom našega vzorca saj lahko nadaljujemo od tistega stanja.*
    $$\delta(q, a) = \max \{ k \mid P[1:k] \sqsupset {\color{orange}P[1:q]}{\color{green}a} \}$$
*   Za naivno gradnjo tabele prehodov $\delta$ velikosti $(|P|+1) \times |\Sigma|$ porabimo $O(|P|^3 \cdot |\Sigma|)$.
*   Z optimiziranim postopkom (z vzporednim sledenjem stanja neuspeha oz. *fallback state*) lahko tabelo $\delta$ zgradimo v času $O(|P| \cdot |\Sigma|)$.
*   **Iskanje v besedilu** $T$ dolžine $n$ izvedemo z enostavnim prehodom skozi stanja:
    $${\color{blue}q} = \delta({\color{blue}q}, T[i])$$
    Ker vsak korak v zanki zahteva le vpogled v tabelo prehodov (čas $O(1)$), je čas iskanja $O(n)$.
*   To nam da celotno časovno zahtevnost $O(n + |P| \cdot |\Sigma|)$ (gradnja avtomata + iskanje v besedilu).

**Knuth-Morris-Prattov (KMP) algoritem**

*   **Tabela prefiksov $\pi$** velikosti $|P|$ nadomesti tabelo prehodov. Znebimo se odvisnosti od velikosti abecede $|\Sigma|$ v prostorski zahtevnosti.
*   Vrednost $\pi[i]$ predstavlja dolžino najdaljšega pravega prefiksa podniza $P[1:i]$, ki je hkrati njegov sufiks:
    $$\pi[i] = \max \{ k < i \mid P[1:k] \sqsupset {\color{orange}P[1:i]} \}$$
*   **Gradnja tabele $\pi$** se začne z $\pi[1] = 0$, potem pa imamo števec $i = 1$, $k = 0$, za vsak indeks pogledamo če velja $k+1 == i$, če je, zapišemo $\pi[i] = k+1$ povečamo $i$ in $k$, če ni naredimo $k = \pi[k]$ in ponovimo dokler $k=0$ ali pa spet najdemo ujemanje.
* Gradjenje je v času $O(|P|)$, saj za izračun $\pi[i]$ uporabimo že izračunane prejšnje vrednosti.
*   **Iskanje v besedilu** $T$ dolžine $n$ uporablja kazalec $j$
	* $j = 0$ in $i = 1$, če se $j+1 == i$ ujemata potem povečamo oba, če se ne ujemata gre $j$ na $\pi[j]$ in se primerjamo $j+1 == i$ dokler $j$ ne gre do $0$ ko spet premikamo $i$ in preverjamo naprej.
*   Čeprav lahko v enem koraku večkrat skočimo nazaj v $\pi$, se vrednost $j$ lahko poveča največ $n$-krat *povečujemo jo samo ko povečujemo $i$*
*   Torej imamo **$O(n + |P|)$**, prostorska **$O(|P|)$** za tabelo $\pi$.

> $\sigma_{P}(S)$ je dolžina najdaljše pripone $S$ ki je hkrati predpona $P$.
> 
> $$\sigma_P(T) = \max \{ k : P_k \sqsupset T \}$$
> 
> $$\sigma_P(T) \ge 0$$
> 
> $$\sigma_P(T) \le \min(|P|, |T|)$$
> 
> $$\sigma_S(S) = |S|$$
> 
> $$\sigma_{SS}(S) = \sigma_S(SS) = |S|$$
> 
> $$S \sqsupset T \implies \sigma_P(S) \le \sigma_P(T)$$
> 
> $$\sigma_P(S) = \sigma_{S^R}(P^R)$$
> 
> $$\sigma_P(T) = |P| \iff P \sqsupset T$$
> 
> $\pi[i]$ je dolžina najdaljše predpone $P[1:i]$, ki je hkrati tudi pripona $P[1:i]$
> 
> Odmik je enak $j - \pi[j]$


Priponska tabela
- Priponska tabela vsebuje indekse vseh pripon $T$-ja urejene leksikografsko
- Za iskanje pri ogromnih $n$ in veliki količini vzorcev $Q$ imamo $O(Qn + Qm)$ zahtevnost
- Z dvojiškim iskanjem najdemo blok pripon ki vsebuje naš podniz in prebermo ven indekse
- S tem rabimo $Q \,m\log_{}{n}$ za $Q$ iskanj v $m \log_{}{n}$ času za dvojiško iskanje in preverjanje vzorca da dobimo meji
- Za gradnjo tabele naivno rabimo $n^{2}\log_{}{n}$ kar je $n \log_{}{n}$ število primerjav, $n$ čas primerjave
- Tabela rangov nam pove da je pripona na indeksu $i$ po abecedi na $r[i]$- tem mestu
- Gradimo jo tako da vzamemo po $2^{i}$ dolge podnize in jim dodelimo leksikografsko mesto, potem naredimo pare teh leksikografksih mest, jih uredimo po velikosti in jim dodelimo nova mesta, nato jih damo nazaj po indeksih in ponovimo 
- priponsko tabelo dobimo tako da tabelo razvrstimo po rangih
- za tabelo rangov bo to $\log_{}{n}$ iteracij, $n \log_{}{n}$ v vsaki iteraciji za urejanje, $n \log^{2}_{}{n}$ skupaj, če uporabimo korensko urejanje samo $n \log_{}{n}$.

Z funkcija
- $Z_{i}(S)$ je dolžina najdaljšega podniza $S$ ki se začne na indeksu $i$ in je predpona $S$
- pripadajoča $Z$-škatla je $T_{i-1}[1:Z_{i}]$, kjer je $Z_{i}$ dolžina tega niza
- za $i$ naj bo $Z$ škatla ki vsebuje $i$ in sega najdlje desno najdlje segajoče škatla
- za gradnjo Z tabele lahko uporabimo najdalje segajočo Z škatlo indeksa ker je ista vrednost že na začetku in jo prepišemo drugače jo izračunamo naivno

Tabela najdaljših predon
- Tabela ki hrani dolžino najdaljše skupne predpone zaporednih pripon v priponski tabeli

Maksimalni pretoki
- $s$ je izvor, $t$ je ponor, $c_{e}$ je kapaciteta na povezavah, $f(e)$ je pretok na povezavi, maksimiziramo $\sum_{e \in\text{In(t)}}^{}f(e)$
- $\text{In}(v)$ je množica pov. ki kaže v $v$, $\text{Out}(v)$ je mn. pov. ki kažejo iz $v$.
- Kirchhoffov zakon $\sum_{e \in \text{In}(v)}^{}f(e) = \sum_{e \in  \text{Out}(v)}^{}f(v)$
- Če imamo nek pretok na grafu, bo graf rezerv tak graf kjer za vsako povezavo naredimo dve kjer povezava v originalno smer dobi vrednost preostale kapacitete, povezava v obratno smer pa dobi vrednost pretoka po njej
- $B(P,f) = \min{r_{1},...,r_{k}}$ je bottleneck na poti $P$ in ji pripada tako imenovana kritična povezava
- Če obstaja pot v grafu rezerv potem lahko povečamo pretok, pretok se na povezavi zmanjša če je smer povezave v $G^{f}$ nasprotna smeri povezave v $G$, če je smer enaka pa se pretok po njej poveča.
- Kapaciteta prereza je $c(A,B) = \sum_{\substack{e \in \text{Out}(A)\\e \in \text{In}(B)}}^{}c_{e}$
- Velja da je $\max |f| = \min c(A,B)$ in vedno velja $|f| \leq c(A,B)$, dokaz temelji na vsoti krichoffovih zakonov po množici $A$, s čimer dokažemo šibko dualnost, nato pa konsturiramo prerez, kjer je $A$ množica točk do katerih lahko pridemo v grafu rerezv še za enakost.
- Za polj. prerez velja da je razlika med tokom ven in tokom not enaka pretoku.
- Celoštevilski maksimalen pretok vedno obstaja če so kapacitete cela števila.

Ford Fulkersenova metoda
- Za vsako povezavo poišči pot v $G^{f}$ od $s$ do $t$, $f(e_{i})$ povečaj oz. zmanjšaj če je pripadajoča $e_{i}^{f}$ enako oz. nasprotno obrnjena. In ponovi. Te poti lahko iščemo na polj. način.
- Metoda se ustavi zaradi zgornje meje kapacitet izhodnih povezav.
- Imamo največ $\sum_{e}^{}c_{e}$ iteracij glavne zanke in vsaka iteracija traja $O(E)$ časa $\Rightarrow$ $O(CE)$, polinomska v odvisnosti od parametrov vhoda, eksponentna v odvisnosti dolžine vhoda $O(2^{b(C)}E)$
- Za dokaz optimalnosti lahko za $A$ definiramo množico vozl. ki so dosegljiva iz $S$ v $G^{f}$, $B$ so preostal vozl., za ta prerez velja da so vse povezave v smeri od $A$ proti $B$ nasičene, povezave v smeri od $B$ proti $A$ pa prazne, torej bo vrednost pretoka enaka kapaciteti, torej bo maks.

Edmonds-Karpov algoritem
- Naraščajoče poti iščemo po naraščajoči dolžini
- Dolžina poti od $s$ do $t$ pri algoritmu ne pada
- Vsaka povezava postane kritična največ $\frac{|V|}{2}\text{ - krat}$, za povezavo $uv$ pridemo do $u$ po $d$ korakih, če hočemo uporabiti $uv$ spet jo moramo odblokirati in iti do $v$ najprej, če bi lahko to storili v $d$ korakih bi v prejšnjem koraku obstajala pot v $d-1$ korakih ki bi jo morali vzeti, po tej logiki se mora pot povečati za vsaj 2, če hočemo neko povezavo uporabiti dvakrat
- Imamo $|E|$ povezav
- Algoritem najde $O(VE)$ krit- poti
- Vsako zasičevanje traja $O(E)$ časa
- Torej bo $O(VE^{2})$

Prirejanja
- Prirejanje je množica povezav tako da se eno vozlišče ne pojavi kot krajišče več povezav, iščemo maksimalno prirejanje, popolno prirejanje je če so vsa vozl. pokrita. Lahko ga prevedemo na problem maks. pretoka.

Grafi
 - DAG je polpovezan če obstaja enolična topološka urejenost.
 - Komponentni graf je acikličen.
- Graf je polpovezan če v toploškem urejanju komponentnega grafa obstaja povezava od $v_{i-1}$ do $v_{i}$

BFS
- V vrsto damo vozl., ga izpišemo, vržemo ven, v vrsto damo vse njegove sosede in jih obdelujemo - izpišemo, vržemo ven, dodamo sosede, če prvič srečamo vozl. ga označimo, če je vozl. že označeno in v vrsti ga preskočimo.
- BFS z matriko sosednosti da $O(V^{2})$, s seznamom sosedov pa $O(V + E)$, kjer za vsako $v$ preverimo vse sosede torej v usmerjenem grafu $E$ časa v neusmerjenem pa $2E$, $V$ porabimo za incializacijo vozlišč.
- Če je graf povezan velja $E \ge V-1$ torej je $V+E \sim E$ torej imamo $O(E)$. Isto velja pri DFS.

Dijsktrov algoritem
- Za vsako vozl. shranjujemo trenutno najkrajšo pot, iz kopice urejene naraščajoče po dolžinah poti vzamemo vozl. za obdelat, $v$ postane obiskan, pogledamo njegove neobiskane sosede in če je pot čez $v$ do soseda krajša kot trenutna jo posodobimo, posodobimo sosede v kopici, ponavljamo.
- $O(E \log_{}{V})$, v poevzanem grafu

DFS
- Vozl. označimo, kličemo DFS na belih sosedih, če je sivo ga preskočimo, lahko tudi shranjujemo prednike.
- Če je voz. neodkrito je belo, prvič obiskane postane sivo, ko zaključimo rek. klic na njem pa črno
- Sledimo času odkritja in času konca, $v.d, v.f$
- Drevesne so povezave od sivih do belih, povratne povezave so od sivih do sivih, od sivih do črnih so neopredeljene
- Za potomce velja da je $I_{u} \subseteq I_{v}$, če  je $I_{v} \cap I_{u} = \emptyset$ noben ni potomec nobenega
- Vozl. sta topološko primerljivi $\Leftrightarrow$ $\exists$ usmerjena pot $u$ do $v$
- Graf ima top. urejenost če je usmerjen in brez ciklov
- Vsaka povezava na neusmerjenem grafu je povratna ali pa drevesna
- vozlišči pripadata isti krepko povezani komponenti $\Leftrightarrow$ obstaja usmerjena pot v obe smeri med njima
- Komponentni graf je acikličen
- Velja ali $I_{v}$ in $I_{u}$ sta disj. - noben ni potomec nobenega ali en vsebuje drugega popolnoma - en je potomec drugega

Iskanje krepko povezanih komponent
- Krepko povezane komponente so množice vozl. kjer za vsak $u,v$ obstaja pot v obe smeri.
- DFS na grafu, zabeležiš končne čase, obrneš povezave v grafu : $G^{T}$, izvedeš DFS po padajočih končnih časih, vsa vozl. ki jih dosežemo tvorijo krepko povezano kompontento.
- Grajenje komponentnega grafa zahteva samo sledenje številom komponent pri iskanju, in katera $v$ pripadajo kateri. Nato samo prehodimo vse prvotne povezave in pogledamo katere komponente so povezane.
- $O(E)$


Topološko urejanje
- DFS in naredimo drevesa po padajočih časih zaključitve, $O(E)$


Vektorski produkt na pove kam gleda $b$ glede na $a$, če je $\sin$ pozitiven je $a$ na levi od $b$, drugače pa na desni

$$a \times b = |a||b|\sin \varphi$$

Grahamov algoritem
 - Vzamemo najbolj spodnjo koordinato, točke ravzrstimo po kotih, za kar primerjamo vektorske produkte, na sklad potisnemo prve 3 in nato preverjamo če $S_{0}$ in $S_{1}$ ter $p_{i}$ ne tvorijo levega zasuka, odstranimo $S_{0}$ s sklada, preverjamo dokler ne dobimo levega zasuka, in dodamo $p_{i}$ na sklad.
- $O(n \log_{}{n})$ za urejanje, $O(n)$ za obravnavo točk

Iskanje parov
- Razdelimo na levo in desno, najdemo min. razdaljo teh, vzamemo min. teh dveh razdalj, naredimo pas dolžine $2\delta$ potem pa za vsako točko naredimo pravokotnik $\delta \times 2\delta$ kjer je točka na spodnji stranici, ker je maksimalno 8 točk z min. razdaljo $\delta$ s tem omejimo časovno kompleksnost
- $O(n \log_{}{n})$ za urejanje elementov, $O(n)$ za iskanje premice za delitev, $O(n)$ za izdelavo, $X_{L},X_{R},Y_{L},Y_{R}$, $O(n)$ za obravnavo v pravoktnikih, $T(n) = 2T\frac{n}{2}+ \Theta(n)$
- $O(n \log_{}{n})$

Iskanje presečišč
- Vrsta dogodkov $D$ se napolni s točkami, premica se pomika po točkah dol, za vsako zgornjo točko se pripadajoče daljice $d$ vstavijo v drevo statusa $S$ ki hrani sosede daljic, preveri se če se pod premico sekata $d$ in leva, ali pa $d$ in desna soseda, za vsako spodnjo točko se odstranijo daljice končujoče v $d$ iz drevesa, preveri če se novi sosedi sekata. Če je točka na sredini daljic potem se tiste ki se končujejo v njej odstranijo in tiste ki začenjajo dodajo na novo.
- če se sosede sekajo potem dodamo presečišče v $D$, če je dogodek na katerega naleti premica presečišče daljic potem se njuna mesta uredijo v $S$ in ker imajo nove sosede se leva preveri z levim in desna z desnim sosedom
- Uporaba prioritetne vrste in uravnoteženega drevesa da vsaka operacija nad strukturo $\log_{}{n}$ časa - torej bo $O((n+k )\cdot \log_{}{n})$, $n$ je število vhodnih daljic, $k$ pa število presečišč.
- Daljici $AB$ in $CD$ se sekata če velja da je predznak $AB \times AC$ $\neq$ $AB \times AD$  in predznak $CD \times CA$ $\neq$ $CD \times CB$.
- Če se v isti točki seka več daljic jih moramo iz $S$ odstraniti in dodati nazaj po naraščajočem spodnjem kotu od leve proti desni
- Če je daljica vodoravna se njeno levo krajišče obravanava kot prvo in desno kot drugo



Sprotni algoritem
- Probamo minimizirati konkurenčno razmerje
$$\max\left\{ \frac{I(i)}{O(i)}\,;\; i \in D \right\}$$
- $I$ je naša implementacija, $O$ pa je optimalen algoritem ki pozna vhod vnaprej
- To razmerje je večje ali enako $1$.
