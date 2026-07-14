### APS

Linarne APS
- Seznam - urejena multimnožica elementov - poljuben dostop do elementov - get, delete, insert, size
- Sklad - urejena multimnožica elementov - LIFO, dostop do zadnjega dodanega elementa - top, pop, push 
- Vrsta - urejena multimnožica elementov - FIFO, dostop do prvega elementa - add, remove, front
- Dvojna vrsta - urejena multimnožica elementov - FIFO, dostop do prvega ali zadnjega elementa, addFront, addBack, getFront, getLast, removeFront, removeBack.
- Prioritetna vrsta ali kopica - multimnožica s elementov s prioritetami - add, pullWithHighestPrio

Asociativne APS
- Množica - neurejenea množica elementov - add, remove, contatins, union, intersection
- Slovar - preslikava oz. množica parov - add(key,value), get(key), remove(key)
- Multimnožica - neurejena multimnožica elementov - add, remove, contains, count, union, interseciton

## Vrsta (Queue)

- Je abstraktna podatkovna vrsta.
- Vrsta sledi načelu **FIFO (First In, First Out)**, kjer prvi element, ki vstopi, prvi izstopi.
- Implementira funkcije
	- Dodaj na konec vrste `push(x)`
	- Odstrani iz začetka vrste `pop()`
	- Poglej prvi element `front()`
	- Velikost `size()`

*V cpp-ju imamo `push(x), pop(), front(), back(), empty(), size()`*
*Inicializiramo z `queue<int> s`, queue je v cpp-ju dequeue*

Vse operacije so v $O(1)$ razen pridobivanje $i$-tega elemnta po vrsti $O(n)$.

## Prioritetna vrsta

- Je abstraktna podatkovna vrsta
- Vrsta hrani informacijo o prioriteti elementov, iz nje lahko vzamemo le najpomembnejši element.
- Implementira
	- Doajanje novega elementa `push(x)`
	- Odstranjevanje najpomembnejšega elementa `pop()`
	- Branje najpomembnejšega elementa `top()`
	- Velikost `size()`

*V cpp-ju imamo `push(x), pop(), top(), empty(), size()`*
*Inicializiramo z `priority_queue<int> pq` ali `priority_queue<int, vector<int>, greater<int>> minPq`, če ga delamo iz že obstoječega vektorja uporabimo `priority_queue<int> pq(v.begin(), v.end())`*
*Po privzetem je v cpp max-heap.*

Kot implementacije prioritetne vrste poznamo min in max-kopico, kjer ena vrne največji element ena najmanjši. Hitrost je odvisna od implementacije.

Kompleksnost je odvisna od implementacije

Uporaba sortiranega seznama bo $O(n)$ za vstavljanje elementa. *Hitro dvojišk iskanje za pravilno mesto in premikanje elementov v desno za luknjo, kjer imamo $\log_{}{n} + n$.*

Uporaba dvojiškega drevesa kjer bo dostop $O(1)$, saj je v korenu. Vstavljanje in odstranjevanje pa v $\log_{}{n}$. Če dodamo element ga damo na konec drevesa, potem moramo primerjati s staršem dokler ne pride do pravega mesta.
Za odstranjevanje pa velja da odstranimo koren, ga zamenjamo s členom na koncu drevesa in potem preverjamo če je večji od obeh otrok, če ni vzamemo ta večjega od otrok in ga zaamenjamo z njim in to ponavljamo.

Če se vstavlja redko in pobira pogosto je sorted arrray boljši.
Če se vstavlja pogosto in pobira pogosto je binary tree boljši.

Grajenje kopice lahko poteka na dva načina. Začnemo s prazno in uoprabljamo `push`. To pride $n \log_{}{n}$.

Lahko uporabimo **Floydov algoritem** kjer začenmo s poljem z elemnenti. In preko implementacije dvojiškega drevesa s poljem preverjamo za vsak zadnji element ali ga zamenjamo z njegovim trenutnim staršem. Zdi se da je $n \log_{}{n}$ a je v resnici $O(n)$, saj se večina vozlišč nahaja blizu dna drevesa in se jim ni treba pogrezniti daleč ali pa sploh ne. Vsota teh premikov konvergira k $n$.


## Preskočna vrsta

Gre za povezan seznam z več nivoji bližnjic, ki omogočajo hitrejše iskanje.

Vsak element ima lahko poleg originalnih kazalcev še kazalec za vsak drugi element in tako naprej.
Vsakemu dodanemu kazalcu bomo rekli plast in je podmnožica originalne vrste.

Za iskanje najprej preiščemo najvišjo plast in ko je vrednost naslednjega elementa večja od iskanega se premaknemo v nižji nivo.

Tako tudi vstavljamo v vrsto. Najdemo kam mora iti element in ga vstavimo v plast 0 potem pa ga vključimo v druge plasti z neko naključno možnostjo.

Realistično za vse operacije rabimo $O(\log_{}{n})$.



## Krovni izrek

- Nek problem velikosti $n$ lahko razbijemo na več podproblemov.
<br>
- Ob klicu rekurzije razbijemo problem velikosti $n$ na več podproblemov velikosti $\frac{n}{b}$.
- Vpeljali smo faktor **$b$** - število podproblemov ki nastane. *To ni enako številu podproblemov ki jih moramo rešiti.*
<br>
- Ker ni nujno da algoritem preverja vse veje/podprobleme nam konstanta $a$ pove koliko vej se obravnava.
- Idealno je $a \leq b$. *Lahko se  zgodi da katero vejo obravnavamo večkrat v katerem primeru je $a \ge b$*
  
> Primer je dvojiško iskanje kjer vzamemo vhod $n$, ga damo na dva dela velikost $\frac{n}{2} \Rightarrow b=2$. Vzamemo pa le enega torej $a = 1$.

- prištejemo še $f(n)$ kot strošek kakšrnih koli drugih operacij zunaj rekurzivnega klica

> Pri dvojiškem iskanju je na primer potrebna primerjava sredinskega elementa z iskanim elementom kar je $O(1)$.

- Splošna oblika rekurzije bo torej
  $$T(n) = a \cdot T\left(\frac{n}{b}\right) + f(n)$$

- Na vrhu imamo en problem velikosti $n$ s stroškom $f(n)$.
  Na nivoju 1 imamo $a$ podproblemov velikosti $n/b$, skupni strošek je $a \cdot f(n/b)$.
- Na nivoju $i$ imamo $a^{i}$ podproblemov velikosti $n/b^{i}$ skupni strošek je $a^{i} \cdot f(n/b^{i})$
<br>
- Višina drevesa je $\log_{b}{n}$ torej bo število listov v drevesu $a^{\log_{b}{n}}$ ta izraz lahko preoblikujemo v $n^{\log_{b}{a}}$ kar predstavlja skupno delo v listih - osnovnih delih rekurzije. Temu pravimo tudi **kritična funkcija**.
<br>
- Bistvo izreka je da primerjamo kritično funkcijo z delom v vozliščih - $f(n)$.
<br>
- Če funkcija $f(n)$ raste **polinomsko počasneje** kot $n^{\log_{b}{a}}$ potem večino dela opravijo listi.
- Velja $f(n) = O(n^{\log_{b}{a}-C})$ za nek $C > 0$ in **$T(n) = \Theta(n^{\log_{b}{a}})$**.
  *Ker se delo z vsakim nivojem rekurzije eksponentno povečuje, je celotna vsota asimptotično določena z zadnjim nivojem (listi).*
  <br>
- Če funkcija $f(n)$ raste **asimptotično** enako kot $n^{\log_{b}{a}}$ potem je opravljeno delo približno enako.
- Velja $f(n) = \Theta(n^{\log_{b}{a}})$ in **$T(n) = \Theta(n^{\log_{b}{a}} \log_{}{n})$**.
  *Na vsakem nivoju drevesa opravimo približno enako količino dela. Ker je nivojev $\log_b n$, skupno delo pomnožimo s tem faktorjem.*
<br>
- Če funkcija $f(n)$ raste **polinomsko hitreje** kot $n^{\log_b a}$, potem se večina dela opravi na vrhu drevesa (v trenutnem vozlišču).
- Velja $f(n) = \Omega(n^{\log_b a + C})$ za nek $C > 0$ **in** izpolnjen mora biti pogoj regularnosti: $a f(n/b) \le c f(n)$ za nek $c < 1$ in dovolj velik $n$. Tako pride **$T(n) = \Theta(f(n))$**.
  *Delo se z globino rekurzije tako hitro zmanjšuje, da je vsota vseh nivojev asimptotično določena s stroškom prvega koraka (koren drevesa).*

<BR>
- V splošnem označimo $\log_{b}{a} = c$.

### BST

Za vstavljanje v BST začnemo v korenu in za vsak element pogledamo ali je manjši oz. večji od vozlišča.

Za brisanje imamo 3 primere. Če je element v listu ga zbrišemo. Če je element z enim otrokom ga zbrišemo in njegovega otroka povežemo s strašem orginalnega.

Če ima $x$ dva otroka moramo poiskati zamenjavo. Najlažji način je da poiščemo naslednika $x$ v desnem poddrevesu torej če gremo in-order - torej gremo v desno poddrevo in potem čisto levo najdemo naslednika $x$. Tega prekopiramo v vozlišče $x$ in izbrišemo $x$.

Enako lahko storimo za in order predhodnika. Ga najdemo zamenjamo $x$ z njim.

Obe sta v $\log_{}{n}$ saj poiščemo element za zbrisati in pot do in-order naslednika ali mesto za vstaviti nato pa konstantno števil operacij za izbris ali vstavljanje.


### AVL drevo

AVL drevo je selfbalancing binary search tree. Osnovna omejitev je da je višina levega poddrevesa lahko za največ $BF$ večja od višine desnega poddrevesa, kjer velja da je $BF$ balancing factor in predstavlja maksimalno razliko med levim in desnim poddrevesom. $BF \in \{ -1,0,1\}$.

Vsako vozlišče shranjuje velikost njegovega poddrevesa.

V najslabših primerih se lahko z vstavljanjem že urejenih podatkov drevo spremeni v drevo dolžine $n$. Torej nam ne bo pomagalo pri iskanju. AVL zagotavlja da je višina približno $1.44 \log_{}{n} \sim \frac{1}{\ln 2}\log_{}{n}$.

Formula za najmanjše število vozlišč za AVL drevo višine $h$ je $N(h) = N(h-1) + N(h-2) + 1$ iz česar lahko izpeljemo splošni člen.

Iskanje poteka $O(\log_{}{n})$, kot tudi vstavljanje in brisanje.

Za vstavljanje najprej poiščemo primerno mesto, vstavimo element, ko gremo po rekurziji nazaj posodobimo balancing factor za vsakega starša. Če je faktor prevelik se izvede **rotacija**.

Brisanje naredimo enako kot v BST, nato preverimo BF v vsakem od vozlišč od vključno z izbirsanim vozliščem gor. Po potrebi se izvedejo rotacije.

Obstajajo štirje tipi neuravnoteženosti in štiri ustrezne rotacije:

Za neko vozlišče z nepravilnim BF pogledamo njegovega otroka, nato pa še otroka tega otroka. Če velja 

![[Pasted image 20260210155913.png]]

**Enojni rotaciji**
Če sta oba istega predznaka - $x$
1.  **Levo-Levo (LL) $\rightarrow$ Desna rotacija:**
    *   *Situacija:* Levo poddrevo levega otroka je previsoko.
    *   *Rešitev:* Vozlišče $A$ zarotiramo v desno okoli njegovega levega otroka $B$. $B$ postane novi koren tega poddrevesa.
2.  **Desno-Desno (RR) $\rightarrow$ Leva rotacija:**
    *   *Situacija:* Desno poddrevo desnega otroka je previsoko.
    *   *Rešitev:* Vozlišče $A$ zarotiramo v levo okoli njegovega desnega otroka $B$.

#### B) Dvojni rotaciji
Uporabljata se, ko sta "težava" in njen "otrok" nagnjena v nasprotni smeri (oblika "cik-cak").

1.  **Levo-Desno (LR) $\rightarrow$ Leva + Desna rotacija:**
    *   *Situacija:* Desno poddrevo levega otroka je previsoko.
    *   *Rešitev:* Najprej izvedemo levo rotacijo na levem otroku, nato pa desno rotacijo na prvotnem vozlišču.
2.  **Desno-Levo (RL) $\rightarrow$ Desna + Leva rotacija:**
    *   *Situacija:* Levo poddrevo desnega otroka je previsoko.
    *   *Rešitev:* Najprej izvedemo desno rotacijo na desnem otroku, nato pa levo rotacijo na prvotnem vozlišču.

Veljalo bo da je isaknje, vstavljanje in brisanje v $\log_{}{n}$.


### 1. Poizvedbe na območjih (Range Queries)

Problem: Imamo tabelo $A$ in želimo hitro odgovarjati na vprašanja o lastnostih (vsota, minimum, maksimum) podintervala $[l, r)$.

#### **A) Range Sum Query (RSQ) – Vsota na območju**
*   **Tehnika:** Kumulativne (prefix) vsote.
*   **Postopek:** Izračunamo tabelo $c$, kjer je $c_r = a_0 + a_1 + \dots + a_{r-1}$.
*   **Formula:** $sum(l, r) = c_r - c_l$.
*   **Zahtevnost:** Predobdelava $O(n)$, poizvedba **$O(1)$**.
*   **Omejitev:** Deluje le, če se tabela **ne spreminja**.

#### **B) Range Minimum Query (RMQ) – Minimum na območju**
1.  **Korensko razbitje (Square Root Decomposition):**
    *   Tabelo razdelimo na bloke velikosti $\sqrt{n}$. Za vsak blok si zapomnimo minimum.
    *   **Zahtevnost:** Poizvedba **$O(\sqrt{n})$**, posodobitev $O(1)$.
2.  **Segmentno drevo (Segment Tree):**
    *   Statično dvojiško drevo, kjer koren hrani minimum celotne tabele, otroci pa minimume polovic.
    *   **Zahtevnost:** Predobdelava $O(n)$, poizvedba **$O(\log n)$**, posodobitev **$O(\log n)$**.
    *   **Prednost:** Omogoča hitre posodobitve elementov (dinamičnost).

---

### Problem nahrbtnika

Za nahbtnik s kapaciteto $v$ in $k$ elementi ki jih lahko damo noter velikosti $v_{1},...,v_{k}$ moramo maksimizirati vrednost v nahrbtniku.

To storimo tako da za vsako možno kapaciteto pogledamo makimalno vrednost če vzamemo naslednji element. Naredimo tabelo kjer vsak stolpec predstavlja kapaciteto od 0 do $v$ vsaka vrstica pa $i$-ti element. Najprej pogledamo zapolnimo vrstico za prvi element in vidimo da lahko za vsako kapaciteto večjo od velikosti elementa dobimo vrednost v nahrbtniku tega elementa. Za naslednji element prepišemo vse vrednosti kjer je kapaciteta premajhna. Če pa je kapaciteta dovolj velika vstavimo noter element, pogledamo koliko prostora ostane, pogledamo v prejšnjo vrstico kakšna je maksimalan zapolnitev tega prostora in če je skupna zapolnitev - torej vsota teh večja od vrednosti prejnšje zapolnitve - torej vrstice gor potem posodobimo vrednost s to vsoto.


### 2. Uravnotežena dvojiška iskalna drevesa

Osnovna dvojiška iskalna drevesa (BST) se lahko v najslabšem primeru (vstavljanje urejenih podatkov) izrodijo v seznam z višino $O(n)$. Uravnotežena drevesa vzdržujejo višino **$O(\log n)$**.

#### **AVL drevo**
*   **Pogoj:** Za vsako vozlišče se višini levega in desnega poddrevesa razlikujeta za največ **1**.
*   **Faktor ravnovesja ($b$):** $height(desno) - height(levo) \in \{-1, 0, 1\}$.
*   **Operacije:** Če postane $|b| > 1$, izvedemo **rotacije**:
    *   **Enojna rotacija (Leva ali Desna):** Če je drevo nagnjeno v isto stran (npr. levo-levo).
    *   **Dvojna rotacija (Leva-Desna ali Desna-Leva):** Če je "koleno" (npr. levo-desno).
*   **Zahtevnost:** Iskanje, vstavljanje in brisanje so vedno **$O(\log n)$**.

#### **Drugi tipi uravnoteženih dreves**
*   **Rdeče-črno drevo:** Manj strogo uravnoteženo kot AVL (višina do $2 \log n$), a zahteva manj rotacij pri vstavljanju/brisanju. Standard v C++ (`std::map`).
*   **Treap (Naključno drevo):** Vsako vozlišče ima ključ (za BST) in naključno prioriteto (za kopico/heap). Ravnovesje vzdržuje statistično.
*   **Splay drevo:** Nima strogega pogoja višine. Zadnji dostopani element premakne v koren. Amortizirana zahtevnost $O(\log n)$.
*   **B-drevesa:** Vozlišča imajo več ključev in več otrok. Optimizirana za diske in baze podatkov.

---

### 3. Izpitni namigi in pomembna dejstva

#### **Range Queries: Kdaj kaj uporabiti?**
1.  **Samo vsote in ni posodobitev?** $\to$ Kumulativne vsote ($O(1)$ poizvedba).
2.  **Minimumi/Maksimumi in ni posodobitev?** $\to$ Sparse Table (v zapiskih ni omenjena, a je $O(1)$ poizvedba) ali Segmentno drevo.
3.  **Potrebne so posodobitve (updates)?** $\to$ Segmentno drevo ali Fenwickovo drevo (BIT).

#### **AVL Drevesa: Ključne točke za izpit**
1.  **Višina:** Minimalno število vozlišč $N(h)$ za višino $h$ sledi Fibonaccijevemu zaporedju: $N(h) = N(h-1) + N(h-2) + 1$. To dokazuje, da je višina vedno logaritemska.
2.  **Rotacije:** Na izpitu boš verjetno moral ročno vstaviti elemente in narisati rotacije.
    *   *Zapomni si:* Vedno preverjaj ravnovesje od spodaj navzgor (od vstavljenega lista proti korenu). Prvo vozlišče, kjer je $|b| = 2$, je mesto rotacije.
3.  **Brisanje:** Pri brisanju v AVL drevesu se lahko zgodi več rotacij po celotni poti do korena (pri vstavljanju je dovolj ena ali ena dvojna).

#### **Segmentno drevo: Podrobnosti**
*   Če $n$ ni potenca 2, tabelo dopolnimo z nevtralnimi elementi (npr. $\infty$ za minimum, $0$ za vsoto).
*   Število vozlišč v segmentnem drevesu je približno $2n$ (natančneje $2 \cdot 2^{\lceil \log_2 n \rceil}$).
*   Poizvedba `query(l, r)` deluje tako, da razbije interval na $O(\log n)$ kanoničnih vozlišč, ki v celoti pokrivajo iskano območje.

#### **Razno**
*   **Amortizirana zahtevnost:** Ne pozabi, da pri **Splay drevesih** posamezna operacija lahko traja $O(n)$, vendar bo zaporedje $M$ operacij vedno trajalo $O(M \log n)$.
*   **B-drevesa:** Njihova glavna prednost je **majha višina** (velik razvejanostni faktor), kar minimizira število dostopov do počasnega spomina (disk).

> **Osnove grafov: Strukture in algoritmi**
> 
> Graf $G = (V, E)$ je sestavljen iz vozlišč ($V$) in povezav ($E$). Predstavlja temeljno strukturo za modeliranje relacij.
> 
> ### 1. Predstavitve grafov v pomnilniku
> 
> | Lastnost | Seznam sosedov (`adj[u]`) | Matrika sosednosti (`mat[u][v]`) |
> | :--- | :--- | :--- |
> | **Prostor** | $O(V + E)$ (optimalno za redke) | $O(V^2)$ (dobro za goste) |
> | **Preverjanje sosedov** | Počasno ($O(\text{stopnja } u)$) | Hitro ($O(1)$) |
> | **Iskanje vseh sosedov** | Hitro (pregledaš le obstoječe) | Počasno (pregledaš celo vrstico $V$) |
> | **Uporaba** | Večina algoritmov (BFS, DFS, Dijkstra) | Floyd-Warshall, algoritmi na gostih grafih |
> 
> ---
> 
> ### 2. Temeljna preiskovanja (BFS in DFS)
> 
> *   **BFS (Iskanje v širino):**
>     *   **Struktura:** Vrsta (FIFO).
>     *   **Glavna lastnost:** Najde **najkrajšo pot** (najmanjše število povezav) v neuteženih grafih.
>     *   **Časovna zahtevnost:** $O(V + E)$.
> 
> *   **DFS (Iskanje v globino):**
>     *   **Struktura:** Sklad (Stack) ali rekurzija.
>     *   **Glavna lastnost:** Raziskovanje strukture (komponente, cikli).
>     *   **Časovna zahtevnost:** $O(V + E)$.
> 
> ---
> 
> ### 3. Posebni algoritmi in problemi
> 
> #### **A) Detekcija ciklov**
> *   **Neusmerjeni grafi:** Cikel obstaja, če med DFS obiščemo vozlišče, ki je že označeno kot obiskano in **ni neposredni starš** trenutnega vozlišča.
> *   **Usmerjeni grafi:** Cikel obstaja, če med DFS naletimo na vozlišče, ki je trenutno še v **rekurzivnem skladu** (označeno kot "v obdelavi"). Takšni povezavi rečemo **povratna povezava** (*back-edge*).
> 
> #### **B) Topološko urejanje**
> *   Deluje samo na **DAG** (usmerjenih acikličnih grafih).
> *   Linearna ureditev vozlišč: če obstaja povezava $u \to v$, mora biti $u$ pred $v$.
> *   **Kahnov algoritem:** Uporablja vhodne stopnje (`indegree`). Vozlišča z `indegree == 0` dajemo v vrsto, jih odstranjujemo in njihovim sosedom zmanjšujemo `indegree`.
> 
> #### **C) Kritična pot (Najdaljša pot v DAG)**
> *   V splošnih grafih je iskanje najdaljše poti NP-težek problem, v **DAG** pa je rešljiv z dinamičnim programiranjem.
> *   **Postopek:** Vozlišča urediš topološko in nato za vsako izračunaš $d(u) = \max(w(u,v) + d(v))$.
> 
> #### **D) Eulerjev obhod**
> *   Pot, ki preide **vsako povezavo natanko enkrat** in se konča v istem vozlišču.
> *   **Pogoj:** Graf mora biti povezan, vsa vozlišča pa morajo imeti **sodo stopnjo** (v usmerjenih grafih: $indegree(v) = outdegree(v)$).
> 
> ---
> 
> ### 4. Izpitni namigi in pomembna dejstva (Cheat Sheet)
> 
> 1.  **Lema o rokovanju (Handshaking Lemma):**
>     Vsota stopenj vseh vozlišč je vedno enaka **dvakratnemu številu povezav**: $\sum deg(v) = 2|E|$. 
>     *Izpitno vprašanje: "Ali obstaja graf s 5 vozlišči, kjer ima vsako stopnjo 3?" Odgovor: Ne, ker bi bila vsota stopenj 15 (liho število).*
> 
> 2.  **Drevesa:**
>     Graf je drevo, če je povezan in nima ciklov. Za drevesa vedno velja $|E| = |V| - 1$.
> 
> 3.  **Preverjanje dvodelnosti (Bipartitnost):**
>     Graf je dvodelen, če ga lahko pobarvamo z dvema barvama tako, da nobena sosednja vozlišča niso iste barve. To preverimo z BFS/DFS. Graf je dvodelen $\iff$ **nima lihih ciklov**.
> 
> 4.  **Pasti pri časovni zahtevnosti:**
>     Če te vprašajo za zahtevnost BFS/DFS na **matriki sosednosti**, je odgovor $O(V^2)$. Če je na **seznamu sosedov**, je $O(V + E)$.
> 
> 5.  **Povezanost:**
>     *   V neusmerjenih grafih govorimo o **povezanih komponentah**.
>     *   V usmerjenih grafih govorimo o **krepko povezanih komponentah** (obstaja pot iz $u \to v$ in $v \to u$).
> 
> 6.  **Euler vs. Hamilton:**
>     *   **Euler:** Vsaka **povezava** enkrat (Enostavno, preverjamo stopnje).
>     *   **Hamilton:** Vsako **vozlišče** enkrat (Zelo težko, NP-poln problem).
> 
> 7.  **Zanke in vzporedne povezave:**
>     Vedno preveri, ali je graf **enostaven**. Večina osnovnih algoritmov (kot je Dijkstra brez prilagoditve) predvideva enostavne grafe brez negativnih ciklov.

---

> **Osnove grafov in preiskovanja**
> 
> Graf $G = (V, E)$ je struktura, ki jo sestavljajo **vozlišča** ($V$) in **povezave** ($E$). Uporabljamo jih za modeliranje omrežij, relacij in procesov. Glavni parametri so $n = |V|$ (število vozlišč) in $m$ ali $e = |E|$ (število povezav).
> 
> ### 1. Predstavitve grafov
> 
> Izbira podatkovne strukture vpliva na časovno in prostorsko zahtevnost operacij:
> 
> | Lastnost | Seznam povezav | Seznam sosedov | Matrika sosednosti |
> | :--- | :--- | :--- | :--- |
> | **Prostor** | $O(E)$ | **$O(V + E)$** | $O(V^2)$ |
> | **Sosednost $u \sim v$** | $O(E)$ | $O(degree(v))$ | **$O(1)$** |
> | **Dodajanje povezave** | $O(1)$ | $O(1)$ | $O(1)$ |
> | **Primeren za...** | Enostavne izpise | **Redke grafe** ($E \approx V$) | **Goste grafe** ($E \approx V^2$) |
> 
> ---
> 
> ### 2. Osnovna algoritma preiskovanja
> 
> 1.  **BFS (Iskanje v širino):**
>     *   **Logika:** Uporablja **vrsto (Queue)**. Obiskuje vozlišča po nivojih (vsi sosedje nivoja $d$ pred nivojem $d+1$).
>     *   **Uporaba:** Najkrajše poti v neuteženih grafih.
>     *   **Zahtevnost:** $O(V + E)$.
> 
> 2.  **DFS (Iskanje v globino):**
>     *   **Logika:** Uporablja **sklad (Stack)** ali rekurzijo. Gre čim globje, dokler ne doseže lista, nato se vrne (backtracking).
>     *   **Uporaba:** Detekcija ciklov, topološko urejanje, krepko povezane komponente.
>     *   **Zahtevnost:** $O(V + E)$.
> 
> ---
> 
> ### 3. Napredni algoritmi in problemi
> 
> *   **Detekcija ciklov:**
>     *   V **neusmerjenem** grafu cikel obstaja, če med DFS obiščemo že videno vozlišče, ki ni starš.
>     *   V **usmerjenem** grafu cikel obstaja, če naletimo na vozlišče, ki je trenutno še v rekurzivnem skladu (povratna povezava).
> 
> *   **Topološko urejanje (Toposort):**
>     *   Deluje le na **DAG** (usmerjenih acikličnih grafih).
>     *   Vozlišča razvrsti v vrsto tako, da za vsako povezavo $u \to v$ velja, da je $u$ pred $v$.
>     *   **Kahnov algoritem:** Uporablja vhodne stopnje (`indegree`) vozlišč.
> 
> *   **Kritična pot:**
>     *   Najdaljša pot v usmerjenem acikličnem grafu (DAG).
>     *   Rešuje se z dinamičnim programiranjem v topološkem vrstnem redu.
> 
> *   **Eulerjev obhod:**
>     *   Pot, ki obišče vsako **povezavo** natanko enkrat in se vrne v izvor.
>     *   Pogoj za neusmerjen graf: Vsa vozlišča morajo imeti **sodo stopnjo**.
> 
> ---
> 
> ### 4. Terminologija na kratko
> *   **Enostaven graf:** Brez zank in vzporednih povezav.
> *   **Stopnja vozlišča:** Število sosedov (pri usmerjenih ločimo vhodno in izhodno stopnjo).
> *   **Pot vs. Steza:** Pot nima ponovljenih vozlišč, steza nima ponovljenih povezav.
> *   **Dvodelni (Bipartitni) graf:** Vozlišča lahko razdelimo v dve množici, kjer povezave tečejo le med množicama.



> **Kruskalov algoritem**
> 
> Algoritem se uporablja za iskanje **najmanjšega vpetega drevesa (MST - Minimum Spanning Tree)** v povezanem, neusmerjenem in uteženem grafu. MST je podmnožica povezav, ki poveže vsa vozlišča brez ciklov in ima minimalno skupno vsoto uteži.
> 
> ### 1. Postopek po korakih
> 
> 1.  **Inicializacija:**
>     *   Ustvarimo prazno množico povezav $A$, ki bo na koncu predstavljala MST.
>     *   Za vsako vozlišče $v \in V$ ustvarimo svojo disjunktno množico (vsako vozlišče je na začetku svoja komponenta/drevo).
>     *   Vse povezave $E$ iz grafa razvrstimo (sortiramo) po teži **naraščajoče** (od najmanjše do največje).
> 
> 2.  **Glavna zanka (Pregled povezav):**
>     Za vsako povezavo $(u, v) \in E$ iz sortiranega seznama:
>     *   Preverimo, ali vozlišči $u$ in $v$ pripadata **različnima** komponentama (uporabimo operacijo `FIND-SET(u)` in `FIND-SET(v)`).
>     *   **Če sta v različnih komponentah** (povezava ne tvori cikla):
>         1.  Povezavo $(u, v)$ dodamo v množico $A$.
>         2.  Združimo množici (komponenti), ki jima pripadata $u$ in $v$ (uporabimo operacijo `UNION(u, v)`).
>     *   **Če sta v isti komponenti**, povezavo zavržemo, saj bi njena vključitev povzročila cikel.
> 
> 3.  **Zaključek:**
>     Postopek se ustavi, ko so vsa vozlišča povezana v eno samo komponento (oziroma ko imamo $V-1$ povezav). Množica $A$ je najmanjše vpeto drevo.
> 
> ---
> 
> ### 2. Časovna zahtevnost
> 
> *   Je **požrešni (greedy)** algoritem.
> *   **Sortiranje povezav:** To je najzahtevnejši del. Če imamo $E$ povezav, je čas $O(E \log E)$. Ker je $E \le V^2$, je to ekvivalentno **$O(E \log V)$**.
> *   **Operacije z disjunktnimi množicami (Union-Find):** 
>     *   Če uporabimo optimizaciji (stiskanje poti in združevanje po rangu), je zahtevnost teh operacij skoraj linearna: $O(E \cdot \alpha(V))$, kjer je $\alpha$ inverzna Ackermannova funkcija.
> *   **Skupna zahtevnost:** Prevladuje sortiranje, torej **$O(E \log E)$** ali **$O(E \log V)$**.
> *   Algoritem je še posebej učinkovit za **redke grafe**.
> 
> ---
> 
> ### 3. Prostorska zahtevnost
> 
> *   **Shranjevanje povezav:** $O(E)$ za seznam vseh povezav, ki jih sortiramo.
> *   **Disjunktne množice:** $O(V)$ za polja, ki hranijo starše in range v strukturi Union-Find.
> *   **Skupaj:** **$O(E + V)$**.
> 
> ---
> 
> ### 4. Ključne lastnosti
> 
> *   **Cikli:** Algoritem eksplicitno preprečuje nastanek ciklov z uporabo strukture Union-Find.
> *   **Gozd:** Med izvajanjem Kruskalov algoritem gradi "gozd" (več ločenih dreves), ki se na koncu združijo v eno samo vpeto drevo.
> *   **Primerjava s Primovim algoritmom:** Kruskalov algoritem se osredotoča na **povezave** (primerno za redke grafe), Primov pa na **vozlišča** (primerno za goste grafe).

> **Floyd-Warshallov algoritem**
> 
> Algoritem rešuje problem **najkrajših poti med vsemi pari vozlišč (APSP - All-Pairs Shortest Paths)** v usmerjenem ali neusmerjenem grafu. Za razliko od prejšnjih algoritmov, ki iščejo poti iz enega izvora, ta hkrati izračuna najkrajše poti med vsemi možnimi kombinacijami vozlišč.
> 
> ### 1. Postopek po korakih
> 
> 1.  **Inicializacija:**
>     *   Pripravimo matriko razdalj $D$ dimenzije $V \times V$.
>     *   Za vsak par vozlišč $(i, j)$:
>         *   Če sta vozlišči enaki ($i = j$), je $D[i][j] = 0$.
>         *   Če obstaja neposredna povezava med $i$ in $j$, je $D[i][j] = w(i, j)$.
>         *   Če povezave ni, je $D[i][j] = \infty$.
>     *   (Opcijsko) Pripravimo matriko $\Pi$ za rekonstrukcijo poti, kjer shranimo predhodnike.
> 
> 2.  **Glavna zanka (Tri gnezdena zanke):**
>     Algoritem postopoma vključuje vsa vozlišča kot potencialna **vmesna vozlišča** na poti:
>     Za vsako vozlišče $k$ od $1$ do $V$ (vmesno vozlišče):
>     *   Za vsako vozlišče $i$ od $1$ do $V$ (začetno vozlišče):
>         *   Za vsako vozlišče $j$ od $1$ do $V$ (končno vozlišče):
>             *   Preverimo, ali je pot od $i$ do $j$ **preko** vozlišča $k$ krajša od trenutno znane poti:
>             *   `če (D[i][k] + D[k][j] < D[i][j])`:
>                 *   $D[i][j] = D[i][k] + D[k][j]$
> 
> 3.  **Zaključek:**
>     Po končanih vseh zankah matrika $D$ vsebuje dolžine najkrajših poti med vsemi pari vozlišč. Če po koncu postopka na diagonali ($D[i][i]$) opazimo negativno vrednost, graf vsebuje **negativni cikel**.
> 
> ---
> 
> ### 2. Časovna zahtevnost
> 
> *   Algoritem temelji na **dinamičnem programiranju**.
> *   Zaradi treh gnezdenih zank, kjer vsaka teče od $1$ do $V$, je časovna zahtevnost vedno **$O(V^3)$**.
> *   Zahtevnost je neodvisna od števila povezav $E$, zato je algoritem zelo učinkovit za **goste grafe**.
> *   Čeprav bi lahko Dijkstrov algoritem pognali $V$-krat (kar bi v redkih grafih naneslo $O(V \cdot E \log V)$), je Floyd-Warshall zaradi svoje preprostosti in nizkih konstant pogosto hitrejši na realnih podatkih pri gostih grafih.
> 
> ---
> 
> ### 3. Prostorska zahtevnost
> 
> *   **Matrika razdalj:** Algoritem primarno uporablja matriko $V \times V$, zato je prostorska zahtevnost **$O(V^2)$**.
> *   To je hkrati tudi prostor, potreben za shranjevanje rezultata (razdalj med vsemi pari).
> 
> ---
> 
> ### 4. Lastnosti in omejitve
> 
> *   **Negativne uteži:** Algoritem deluje pravilno z negativnimi utežmi povezav.
> *   **Negativni cikli:** Algoritem ne more poiskati najkrajše poti, če obstaja negativni cikel, vendar ga lahko uspešno **zazna**.
> *   **Uporaba:** Najboljša izbira, ko potrebujemo informacije o vseh razdaljah v grafu in je število vozlišč zmerno (npr. do nekaj sto ali tisoč).


> **Bellman-Fordov algoritem**
> 
> Algoritem rešuje problem **najkrajših poti iz enega izvora (SSSP)** v usmerjenem ali neusmerjenem grafu. Za razliko od Dijkstrovega algoritma, Bellman-Ford dopušča **negativne uteži** povezav in zna **zaznati negativne cikle**.
> 
> ### 1. Postopek po korakih
> 
> 1.  **Inicializacija:**
>     *   Izberemo začetno vozlišče $s$ (izvor).
>     *   Vsem vozliščem $v \in V$ določimo razdaljo $dist[v] = \infty$, razen začetnemu vozlišču, kjer je $dist[s] = 0$.
>     *   Nastavimo starše vseh vozlišč $parent[v] = NIL$.
> 
> 2.  **Glavna zanka (Sproščanje povezav):**
>     Postopek ponovimo **$(|V| - 1)$-krat** (kjer je $|V|$ število vozlišč):
>     *   Za vsako povezavo $(u, v) \in E$ v grafu:
>         *   Izvedemo **sproščanje (relaxation)**:
>         *   Če je `dist[u] + w(u, v) < dist[v]`:
>             1.  Posodobimo razdaljo: $dist[v] = dist[u] + w(u, v)$.
>             2.  Posodobimo starša: $parent[v] = u$.
> 
> 3.  **Preverjanje negativnih ciklov:**
>     Še enkrat se sprehodimo skozi vse povezave $(u, v) \in E$:
>     *   Če velja `dist[u] + w(u, v) < dist[v]`:
>         *   **Algoritem javi napako:** "Graf vsebuje negativni cikel, dosegljiv iz izvora." (Najkrajša pot v tem primeru ne obstaja, saj bi lahko v neskončnost zmanjševali razdaljo s kroženjem v ciklu).
> 
> 4.  **Zaključek:**
>     Če negativni cikel ni bil zaznan, polje $dist$ vsebuje dolžine najkrajših poti, polje $parent$ pa njihovo strukturo.
> 
> ---
> 
> ### 2. Časovna zahtevnost
> 
> *   Algoritem temelji na **dinamičnem programiranju**.
> *   **Glavna zanka:** Izvede se $(V-1)$ iteracij, v vsaki iteraciji pregledamo vseh $E$ povezav.
> *   **Skupna zahtevnost: $O(V \cdot E)$**.
>     *   V polnih grafih ($E \approx V^2$) lahko zahtevnost naraste do $O(V^3)$.
>     *   Je bistveno **počasnejši od Dijkstre**, a nujno potreben, če graf vsebuje negativne uteži.
> 
> ---
> 
> ### 3. Prostorska zahtevnost
> 
> *   **Struktura grafa:** $O(V + E)$ (običajno seznam povezav).
> *   **Dodatni prostor:** Potrebuje $O(V)$ prostora za polji `dist` in `parent`.
> 
> ---
> 
> ### 4. Glavne razlike: Dijkstra vs. Bellman-Ford
> 
> | Lastnost | Dijkstra | Bellman-Ford |
> | :--- | :--- | :--- |
> | **Negativne uteži** | Ne deluje | Deluje |
> | **Negativni cikli** | Ne zazna | Zazna in javi napako |
> | **Strategija** | Požrešna (Greedy) | Dinamično programiranje |
> | **Zahtevnost** | $O(E \log V)$ ali $O(V^2)$ | $O(V \cdot E)$ |

> **Primov algoritem**
> 
> Algoritem vzdržuje dve množici vozlišč:
> 1.  Vozlišča, ki so že vključena v MST.
> 2.  Vozlišča, ki še niso vključena.
> 
> V vsakem koraku algoritem išče najcenejšo povezavo, ki povezuje vozlišče iz prve množice z vozliščem iz druge množice. Ko to povezavo najde, drugo vozlišče premakne v prvo množico.
> 
> 
> 1.  **Inicializacija:**
>     *   Izberemo poljubno začetno vozlišče $s$.
>     *   Vsem vozliščem $v \in V$ določimo ključ $key[v] = \infty$, razen začetnemu vozlišču, kjer je $key[s] = 0$. Ključ predstavlja minimalno težo povezave, s katero se vozlišče $v$ lahko poveže z nastajajočim drevesom.
>     *   Nastavimo starše vseh vozlišč $parent[v] = NIL$.
>     *   Vsa vozlišča vstavimo v prioriteto vrsto $Q$, kjer je prioriteta določena z vrednostjo $key$.
> 
> 2.  **Glavna zanka:**
>     Dokler prioriteta vrsta $Q$ ni prazna:
>     *   Iz $Q$ izločimo vozlišče $u$ z najmanjšo vrednostjo $key[u]$ (operacija `EXTRACT-MIN`). To vozlišče je zdaj dodano v MST.
>     *   Za vsako sosednje vozlišče $v$ vozlišča $u$ preverimo naslednje:
>         *   Če je $v$ še vedno v prioriteti vrsti $Q$ in je utež povezave $w(u, v)$ manjša od trenutne vrednosti $key[v]$:
>             1.  Posodobimo starša: $parent[v] = u$.
>             2.  Posodobimo ključ: $key[v] = w(u, v)$.
>             3.  Posodobimo prioriteto vozlišča $v$ v vrsti $Q$ (operacija `DECREASE-KEY`).
> 
> 3.  **Zaključek:**
>     Ko je vrsta $Q$ prazna, polje $parent$ definira robove najmanjšega vpetega drevesa.
> 
> Velja
> - greedy algoritem za iskanje min MST.
> - če je gost graf - $V^{2}$ uporabimo adj. matrix in linearno iskanje ;-; zahtevnost $O(V^{2})$ za iskanje min vozl., in $O(E)$ za posodabljanje sosedov kar je v matriki $O(1)$ torej je optimalno za goste grafe, kjer je število povezav okoli $V^{2}$. *V primerjavi z $V^{2} \log_{}{V}$*
> - drugače se uporablja nehibour list in binary min heap, kjer se extrakcija min vozl. izvede $V$ krat, zmajnšanje moči pa $E$ krat. Obe v bin heapu trajata $\log_{}{V}$. Torej $O(E \log_{}{V})$.
>   - prostorska je $O(V^{2})$ z matriko in $O(V+E)$ s seznamom plus $O(V)$ dodatnega prostora za algoritem


> **Dijkstrov algoritem**
> 
> Algoritem rešuje problem **najkrajših poti iz enega izvora (SSSP)** v usmerjenem ali neusmerjenem grafu z **ne-negativnimi** utežmi povezav.
> 
> ### 1. Postopek po korakih
> 
> 1.  **Inicializacija:**
>     *   Izberemo začetno vozlišče $s$ (izvor).
>     *   Vsem vozliščem $v \in V$ določimo razdaljo $dist[v] = \infty$, razen začetnemu vozlišču, kjer je $dist[s] = 0$.
>     *   Nastavimo starše vseh vozlišč $parent[v] = NIL$.
>     *   Vsa vozlišča vstavimo v prioriteto vrsto $Q$, kjer je prioriteta določena z vrednostjo $dist$.
> 
> 2.  **Glavna zanka:**
>     Dokler prioriteta vrsta $Q$ ni prazna:
>     *   Iz $Q$ izločimo vozlišče $u$ z najmanjšo vrednostjo $dist[u]$ (operacija `EXTRACT-MIN`). To vozlišče je zdaj "fiksirano" z najkrajšo možno potjo.
>     *   Za vsako sosednje vozlišče $v$ vozlišča $u$ izvedemo **sproščanje (relaxation)**:
>         *   Izračunamo potencialno novo razdaljo: `nova_razdalja = dist[u] + w(u, v)`.
>         *   Če je `nova_razdalja < dist[v]`:
>             1.  Posodobimo starša: $parent[v] = u$.
>             2.  Posodobimo razdaljo: $dist[v] = nova\_razdalja$.
>             3.  Posodobimo prioriteto vozlišča $v$ v vrsti $Q$ (operacija `DECREASE-KEY`).
> 
> 3.  **Zaključek:**
>     Ko je vrsta $Q$ prazna, polje $dist$ vsebuje dolžine najkrajših poti od $s$ do vseh ostalih vozlišč, polje $parent$ pa omogoča rekonstrukcijo teh poti.
> 
> ---
> 
> ### 2. Časovna zahtevnost
> 
> *   Je **požrešni (greedy)** algoritem. Deluje le, če so **uteži povezav $\ge 0$**.
> *   **Gosti grafi:** Uporabimo matriko sosedstva in linearno iskanje minimuma.
>     *   Iskanje minimuma: $V \cdot O(V) = O(V^2)$.
>     *   Sproščanje povezav: $E \cdot O(1) = O(E)$.
>     *   **Skupaj: $O(V^2)$**. To je optimalno, ker je v gostem grafu $E \approx V^2$.
> *   **Redki grafi:** Uporabimo seznam sosedov in binarno kopico (binary heap).
>     *   Iskanje minimuma: $V \cdot O(\log V)$.
>     *   Sproščanje (decrease-key): $E \cdot O(\log V)$.
>     *   **Skupaj: $O(E \log V)$**.
>     *   *(Opomba: S Fibonaccijevo kopico bi šlo $O(E + V \log V)$, a se v praksi redko uporablja).*
> 
> ---
> 
> ### 3. Prostorska zahtevnost
> 
> *   **Matrika sosedstva:** $O(V^2)$ — primerno za goste grafe.
> *   **Seznam sosedov:** $O(V + E)$ — primerno za redke grafe.
> *   **Dodatni prostor:** Algoritem sam potrebuje $O(V)$ prostora za polja `dist`, `parent` in prioriteto vrsto.


Tukaj je povzetek za **BFS (Breadth-First Search – Iskanje v širino)**, pripravljen v isti obliki kot vaš primer za Dijkstrov algoritem.

---

> **BFS (Iskanje v širino)**
> 
> Algoritem rešuje problem **najkrajših poti iz enega izvora (SSSP)** v usmerjenem ali neusmerjenem grafu, kjer so **vse uteži povezav enake** (neutežen graf). Vozlišča obiskuje v nivojih glede na oddaljenost od izvora.
> 
> ### 1. Postopek po korakih
> 
> 1.  **Inicializacija:**
>     *   Izberemo začetno vozlišče $s$ (izvor).
>     *   Vsem vozliščem $v \in V$ določimo razdaljo $dist[v] = \infty$ in barvo `BELA` (neobiskano), razen začetnemu vozlišču, kjer je $dist[s] = 0$ in barva `SIVA`.
>     *   Nastavimo starše vseh vozlišč $parent[v] = NIL$.
>     *   Ustvarimo prazno **vrsto (Queue)** $Q$ in vanjo vstavimo začetno vozlišče $s$.
> 
> 2.  **Glavna zanka:**
>     Dokler vrsta $Q$ ni prazna:
>     *   Iz vrste $Q$ vzamemo prvo vozlišče $u$ (operacija `DEQUEUE`).
>     *   Za vsako sosednje vozlišče $v$ vozlišča $u$:
>         *   Če je vozlišče $v$ še **neobiskano** (barva `BELA`):
>             1.  Spremenimo barvo v `SIVA` (označimo kot obiskano).
>             2.  Posodobimo razdaljo: $dist[v] = dist[u] + 1$.
>             3.  Posodobimo starša: $parent[v] = u$.
>             4.  Vozlišče $v$ vstavimo na konec vrste $Q$ (operacija `ENQUEUE`).
>     *   Ko pregledamo vse sosede, vozlišče $u$ pobarvamo `ČRNO` (popolnoma pregledano).
> 
> 3.  **Zaključek:**
>     Ko je vrsta $Q$ prazna, polje $dist$ vsebuje najmanjše število povezav od $s$ do vseh dosegljivih vozlišč, polje $parent$ pa omogoča rekonstrukcijo najkrajših poti.
> 
> ---
> 
> ### 2. Časovna zahtevnost
> 
> *   Algoritem obišče vsako vozlišče in vsako povezavo natanko enkrat.
> *   **V splošnem:** $O(V + E)$, kjer je $V$ število vozlišč in $E$ število povezav.
>     *   **Inicializacija:** $O(V)$ za nastavitev začetnih vrednosti.
>     *   **Operacije z vrsto:** Vsako vozlišče gre v vrsto in iz nje natanko enkrat ($2 \cdot O(V)$).
>     *   **Pregled sosedov:** Vsaka povezava se pregleda največ enkrat (pri usmerjenih grafih) ali dvakrat (pri neusmerjenih grafih) ($O(E)$).
> *   Če je graf predstavljen z **matriko sosedstva**, je časovna zahtevnost **$O(V^2)$**, ker moramo za vsako vozlišče preveriti vseh $V$ možnih sosedov.
> 
> ---
> 
> ### 3. Prostorska zahtevnost
> 
> *   **Seznam sosedov:** $O(V + E)$ — najpogostejša in najbolj učinkovita predstavitev za BFS.
> *   **Matrika sosedstva:** $O(V^2)$.
> *   **Dodatni prostor:** Algoritem potrebuje $O(V)$ prostora za polja `dist`, `parent`, barve vozlišč in za samo vrsto $Q$.

Tukaj je povzetek za **DFS (Depth-First Search – Iskanje v globino)** v enakem formatu.

---

> **DFS (Iskanje v globino)**
> 
> Algoritem za sistematičen pregled vseh vozlišč in povezav v grafu. Namesto da bi raziskoval sosede nivo za nivojem (kot BFS), DFS prodira **čim globje** vzdolž vsake veje, preden se vrne (backtracking). Uporablja se za topološko urejanje, iskanje krepko povezanih komponent in odkrivanje ciklov.
> 
> ### 1. Postopek po korakih
> 
> 1.  **Inicializacija:**
>     *   Vsem vozliščem $v \in V$ nastavimo barvo `BELA` (neobiskano) in $parent[v] = NIL$.
>     *   Nastavimo globalni števec časa `time = 0`.
> 
> 2.  **Glavna zanka (DFS Wrapper):**
>     Za vsako vozlišče $u \in V$:
>     *   Če je vozlišče $u$ še vedno `BELO`, pokličemo rekurzivno funkcijo `DFS-VISIT(u)`. (To zagotovi, da obiščemo vse komponente grafa).
> 
> 3.  **Rekurzivna funkcija `DFS-VISIT(u)`:**
>     *   `time++`.
>     *   Zapišemo čas odkritja: $d[u] = time$.
>     *   Spremenimo barvo $u$ v `SIVA` (obiskano, a še obdelujemo sosede).
>     *   Za vsako sosednje vozlišče $v$ vozlišča $u$:
>         *   Če je vozlišče $v$ **neobiskano** (`BELO`):
>             1.  Postavimo starša: $parent[v] = u$.
>             2.  Rekurzivno pokličemo `DFS-VISIT(v)`.
>     *   Ko so vsi sosedje pregledani:
>         1.  Spremenimo barvo $u$ v `ČRNA` (popolnoma obdelano).
>         2.  `time++`.
>         3.  Zapišemo čas zaključka: $f[u] = time$.
> 
> ---
> 
> ### 2. Časovna zahtevnost
> 
> *   Podobno kot BFS, algoritem pregleda vsako vozlišče in vsako povezavo.
> *   **V splošnem:** $O(V + E)$.
>     *   **Inicializacija:** $O(V)$.
>     *   **Obisk vozlišč:** Funkcija `DFS-VISIT` se pokliče natanko enkrat za vsako vozlišče v grafu.
>     *   **Pregled povezav:** Vsaka povezava se v seznamu sosedov pregleda natanko enkrat (pri usmerjenih) oziroma dvakrat (pri neusmerjenih grafih).
> *   Če uporabljamo **matriko sosedstva**, je časovna zahtevnost **$O(V^2)$**, ker moramo za vsako vozlišče preveriti vseh $V$ vrstic v matriki.
> 
> ---
> 
> ### 3. Prostorska zahtevnost
> 
> *   **Seznam sosedov:** $O(V + E)$.
> *   **Dodatni prostor:**
>     *   Za polja `parent`, `color`, `d` (discovery) in `f` (finish) potrebujemo $O(V)$ prostora.
>     *   **Sklad (Stack):** DFS uporablja rekurzivni sklad (ali eksplicitni sklad). V najslabšem primeru (ko je graf ena dolga pot) je globina sklada $O(V)$.
> *   Skupna dodatna prostorska zahtevnost je torej **$O(V)$**.
> 
> ---
> 
> ### 4. Klasifikacija povezav (dodatek DFS)
> DFS med izvajanjem omogoča razvrstitev povezav $(u, v)$:
> *   **Drevesne povezave:** $v$ je bil obiskan prvič preko $u$.
> *   **Povratne (Back) povezave:** $v$ je prednik vozlišča $u$ v DFS drevesu (kažejo na cikel).
> *   **Prečne (Cross) in napredne (Forward) povezave:** Povezave med vejami ali proti potomcem, ki niso neposredni.



### 1. Polje (Array) in Dinamično polje (Vector)

Polje je osnovna struktura s strnjenim pomnilnikom, ki omogoča **dostop do elementov v konstantnem času $O(1)$** preko indeksa. V C++ se pogosto uporablja `std::vector`, ki predstavlja razširljivo tabelo.

- **Primeri uporabe:**
    - Shranjevanje podatkov fiksne velikosti ali vnaprej znanega števila elementov.
    - Implementacija drugih struktur, kot so kopice ali zgoščene tabele.
    - Poizvedbe na območjih, npr. izračun kumulativnih vsot za hitro iskanje vsote v podintervalu v času $O(1)$.
- **Nasveti in triki:**
    - **Amortizirana zahtevnost:** Dinamično polje podvoji svojo velikost, ko se zapolni, kar zagotavlja amortizirano časovno zahtevnost dodajanja $O(1)$. Če bi velikost povečevali le za 1, bi bila skupna zahtevnost $O(n^2)$.
    - **Indeksiranje:** Če želite preprečiti nepotrebno kopiranje pri uporabi v rekurzivnih funkcijah (npr. pri vsoti seznama), uporabljajte indekse namesto ustvarjanja novih podseznamov.

### 2. Sklad (Stack)

Sklad deluje po načelu **LIFO (Last In, First Out)**, kjer dostopamo le do zadnjega dodanega elementa.

- **Primeri uporabe:**
    - Upravljanje rekurzije in funkcij (v ozadju računalnika).
    - Algoritmi, kot je **Grahamov pregled** za iskanje konveksne ovojnice, kjer na sklad dodajamo točke in jih odstranjujemo, če povzročijo "desni zavoj".
    - Preiskovanje v globino (**DFS**).
- **Nasveti in triki:**
    - Sklad je zelo preprost za implementacijo s povezanim seznamom ali dinamičnim poljem, pri čemer so vse operacije $O(1)$.
    - Uporabite ga, ko vas zanima le najnovejši podatek ali ko potrebujete obratni vrstni red obdelave.



### 4. Povezani seznam (Linked List)

Sestavljen je iz vozlišč, kjer vsako hrani vrednost in kazalec na naslednika.

- **Primeri uporabe:**
    - Ko potrebujete **hitro vstavljanje ali brisanje** elementov kjerkoli v seznamu (če že imate kazalec na tisto mesto), saj to ne zahteva zamikanja ostalih elementov.
    - Implementacija skladov in vrst.
- **Nasveti in triki:**
    - Izogibajte se povezanim seznamom, če potrebujete pogost dostop do $i$-tega elementa, saj je ta operacija počasna ($O(n)$).

### 5. Vrsta s prednostjo (Priority Queue) in Kopica (Heap)

Vrsta s prednostjo je APT, ki vedno vrne element z najvišjo prioriteto. Najpogostejša implementacija je **dvojiška kopica**.

- **Primeri uporabe:**
    - **Dijkstrov algoritem** za najkrajše poti v uteženih grafih ($O(e \log n)$).
    - **Primov algoritem** za minimalno vpeto drevo.
    - **Urejanje s kopico (Heapsort)**, ki je izboljšava urejanja z izbiranjem.
- **Nasveti in triki:**
    - **Majhen nabor prioritet:** Če so prioritete majhna cela števila (1 do $K$), lahko vrsto s prednostjo implementirate bolj učinkovito z uporabo polja vrst, kar omogoča hitrejše operacije kot splošna kopica.
    - Kopico lahko zgradite v linearnem času $O(n)$ z uporabo Floydovega algoritma.

### 6. Slovar (Map) in Zgoščena tabela (Hash Table)

Slovar hrani pare ključ-vrednost. Zgoščena tabela je ena od možnih implementacij slovarja.

- **Primeri uporabe:**
    - Hitro iskanje podatkov po ključu (npr. ime osebe -> njena starost).
    - **Memoizacija** pri dinamičnem programiranju (shranjevanje že izračunanih rezultatov podproblemov).
- **Nasveti in triki:**
    - **Zgoščena tabela** nudi pričakovano zahtevnost $O(1)$, vendar lahko v najslabšem primeru zaradi trkov postane počasna.
    - **Uravnotežena drevesa** (npr. `std::map` v C++, ki uporablja rdeče-črna drevesa) zagotavljajo zahtevnost $O(\log n)$ in so v nekaterih primerih prostorsko bolj učinkovita od zgoščenih tabel.

