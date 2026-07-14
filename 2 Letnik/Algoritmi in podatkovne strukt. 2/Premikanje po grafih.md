

## Osnove grafov in njihova predstavitev

### Definicija grafa
Graf $G$ je definiran kot par $(V, E)$, kjer je:
*   $V$: končna množica **vozlišč** (v našem primeru označena s števili $\{0, 1, \dots, n-1\}$).
*   $E$: množica **povezav**, kjer je $E \subseteq V \times V$.
*   Uporablja se tudi zapis $G.V$ za množico vozlišč in $G.E$ za množico povezav (v skladu z učbenikom Cormen et al.).

**Omejitve v tem poglavju:**
*   **Enostavni grafi:** Brez zank (povezava iz vozlišča vase) in brez vzporednih povezav (več povezav med istima vozliščema).
*   **Usmerjenost:** Grafi so lahko usmerjeni ali neusmerjeni.
*   **Uteži:** V tem poglavju obravnavamo izključno **neutežene** grafe.

### Predstavitev grafa v računalniku
Izbira podatkovne strukture je ključna za učinkovitost algoritmov:

1.  **Seznam sosednosti (Adjacency List):**
*   Struktura: Tabela $n$ tabel (ali seznamov).
*   $\text{Adj}[v] = [v_1, \dots, v_k]$ pomeni, da so sosedje vozlišča $v$ vozlišča $v_1, \dots, v_k$.
*   **Prednost:** 
	* Najpogostejša predstavitev za večino grafovskih algoritmov
	* omogoča hitro iteracijo po sosedih vozlišč oz. po povezavah - saj so shranjene samo tiste ki so pristone v grafu
	* Odličen za redke grafe - rabimo damo $O(E)$ prostora
*  **Slabost:**
	* Prostorsko neefektivna za gostejše grafe
	* Iskanje poveazve je $O(E)$


2.  **Matrika sosednosti (Adjacency Matrix):**
*   Struktura: Dvojiška matrika $A$ dimenzije $n \times n$.
*   $A[u, v] = 1 \iff (u, v) \in E$ (povezava obstaja), sicer $A[u, v] = 0$.
*   **Prednost:** 
	* Dostop je $O(1)$ - zelo učinkovita za preverjanje, ali med dvema konkretnima vozliščema obstaja povezava.
	* Prostorsko učinkovita **če imamo gost graf**
* **Slabost:**
	* Vedno zahteva $O(V^{2})$ prostora
	* Iteracija po vseh povezavah rabi $O(V^{2})$

---

## 2. BFS

BFS kot DFS pri implementaciji s poljem sosedov deluje v $O(V + E)$ saj za vsako vozlišče preveri vse njegove sosede torej za vsak vozlišče je $O(V)$, da za vsako preveri vse sosede pa bo $\sum_{}^{}\deg{v}$ kar bo $2E$ v neusmerjenm grafu in $E$ v usmerjenem torej $O(E)$ kar bo skupaj $O(V+E)$.

Če uporabljamo matriko sosednosti dobimo $O(V^{2})$ saj moramo za vsako vozlišče iti čez vsako polje v stolpcu matrike tega vozlišča da preverimo če obstaja povezava, drugače pa isti postopek.


BFS je algoritem, ki sistematično preiskuje graf tako, da se širi v "plasteh" stran od začetnega vozlišča.

### Koncept delovanja
*   Pričnemo v izbranem vozlišču $v_0$.
*   Vozlišča preiskujemo po **naraščajočih razdaljah** od $v_0$. Najprej obiščemo vse sosede $v_0$, nato sosede sosedov itd.
*   Uporabljamo podatkovno strukturo **vrsta** (FIFO - First-In-First-Out) za shranjevanje odkritih, a še ne obdelanih vozlišč.
*   **Lastnosti vozlišč:**
    *   `v.obiskano`: Boolean vrednost (false na začetku, true ko vozlišče odkrijemo).
    *   `v.predhodnik`: Hrani vozlišče, iz katerega smo prišli v $v$. To omogoča rekonstrukcijo poti.
*   **Glavni rezultat:** BFS za vsako vozlišče $v$ odkrije **najkrajšo pot** (z najmanjšim številom povezav) od $v_0$ do $v$.

### Algoritem (Psevdokoda)
```text
function BFS(v0)
    Q ← Inicializiraj-vrsto()
    Dodaj-v-vrsto(Q, v0)
    v0.obiskano ← true
    while ¬Je-vrsta-prazna(Q) do
        u ← Odstrani-iz-vrste(Q)
        Print(u)
        for all v ∈ Adj[u] do
            if ¬v.obiskano then
                v.obiskano ← true
                v.predhodnik ← u
                Dodaj-v-vrsto(Q, v)
```

---

## 3. Iskanje v globino (Depth-First Search - DFS)

DFS preiskuje graf tako, da gre čim globlje vzdolž veje, preden se vrne (backtracking).

### Začetna različica
Osnovna ideja je rekurzivna:
1. Označimo trenutno vozlišče $u$ kot obiskano.
2. Za vsakega neobiskanega soseda $v$ vozlišča $u$ rekurzivno poženemo DFS iz $v$.

Teče v $O(V+E)$.

### Prva nadgradnja: Označevanje z barvami
Za natančnejše spremljanje stanja vozlišča uvedemo tri barve:
*   **Bela:** Vozlišče še ni bilo odkrito.
*   **Siva:** Vozlišče je bilo odkrito, vendar še nismo obdelali vseh njegovih sosedov (je v rekurzivnem skladu).
*   **Črna:** Vozlišče in vsi njegovi sosedje so bili v celoti obdelani.

### Druga nadgradnja: Časovni žigi
Uvedemo globalni števec `čas` (inicializiran na 0), ki se poveča ob vsakem pomembnem dogodku:
*   `v.d` (**čas odkritja**): Trenutek, ko vozlišče postane sivo.
*   `v.f` (**čas zaključka**): Trenutek, ko vozlišče postane črno.

### Tretja nadgradnja: Celovito iskanje
Da zagotovimo obisk vseh vozlišč (tudi v usmerjenih ali nepovezanih grafih), DFS poženemo v zanki čez vsa vozlišča:
```text
function DFS(G)
    for all u ∈ G.V do
        u.barva ← bela
    čas ← 0
    for all u ∈ G.V do
        if u.barva = bela then
            DFS1(u)

function DFS1(u)
    čas ← čas + 1
    u.d ← čas
    u.barva ← siva
    for all v ∈ Adj[u] do
        if v.barva = bela then
            v.predhodnik ← u
            DFS1(v)
    u.barva ← črna
    čas ← čas + 1
    u.f ← čas
```

---

## 4. Struktura in lastnosti DFS

### DFS-gozd
DFS definira relacijo `v.predhodnik`, ki tvori množico dreves, imenovano **DFS-gozd**.
*   Vozlišča so ista kot v originalnem grafu ($V = G.V$).
*   Povezave v gozdu so tiste, kjer je $u = v.predhodnik$.

### Klasifikacija povezav v usmerjenem grafu
Pri izvajanju DFS lahko vse povezave v grafu razdelimo v štiri skupine glede na barvo ciljnega vozlišča v trenutku, ko povezavo pregledamo:
1.  **Drevesne povezave:** Vodijo do belega vozlišča (postanejo del DFS-drevesa).
2.  **Povratne (Back) povezave:** Vodijo do sivega vozlišča (povezava do prednika v drevesu).
3.  **Napredne (Forward) povezave:** Vodijo do črnega vozlišča, ki je potomec v drevesu.
4.  **Prečne (Cross) povezave:** Vodijo do črnega vozlišča, ki ni potomec (druga veja ali drugo drevo).

### Izrek o oklepajih (Lastnost 1)
Za poljubni vozlišči $u$ in $v$ velja natanko ena od dveg možnosti glede intervalov $[u.d, u.f]$ in $[v.d, v.f]$:
1.  Intervala sta popolnoma ločena ($[u.d, u.f] \cap [v.d, v.f] = \emptyset$). Vozlišči nista v sorodu.
2.  Interval $v$ je vsebovan v intervalu $u$ ($[v.d, v.f] \subset [u.d, u.f]$). $v$ je potomec $u$.


**Dokaz lastnosti 1 (skica):**
Predpostavimo $u.d < v.d$.
*   Če $v.d < u.f$, je bilo vozlišče $v$ odkrito, ko je bil $u$ še siv. Ker DFS deluje rekurzivno, se mora $v$ zaključiti ($v.f$), preden se zaključi $u$ ($u.f$). Torej $u.d < v.d < v.f < u.f$.
*   Če $v.d > u.f$, se je $u$ zaključil, preden se je $v$ sploh začel. Torej sta intervala ločena.

### Izrek o beli poti (Lastnost 3)
Vozlišče $v$ je potomec $u$ v DFS-gozdu natanko tedaj, ko ob času $u.d$ obstaja pot od $u$ do $v$, sestavljena iz samih belih vozlišč.

### Lastnost 4 (Neusmerjeni grafi)
Pri DFS na **neusmerjenem** grafu sta možni le dve vrsti povezav: **drevesne** ali **povratne**. Naprednih in prečnih povezav ni.

---


## 5. Detekcija ciklov

**Trditev:** Graf ima cikel (zanko) takrat in le takrat, ko pri izvajanju DFS naletimo na vsaj eno **povratno povezavo**.
*   *Zakaj?* Če vozlišče $v$ poskuša vzpostaviti povezavo z vozliščem $u$, ki je še sivo, to pomeni, da je $u$ prednik $v$-ja v trenutni veji raziskovanja. Povezava nazaj na prednika pa zapre krog.

## 6. Topološko urejanje


Topološko urejanje je možno le na grafih, ki so **usmerjeni in aciklični** (angl. *Directed Acyclic Graph* – **DAG**). To pomeni, da so vse povezave v grafu usmerjene in da v grafu ni ciklov (ni poti, ki bi se začela in končala v istem vozlišču).

### Topološki vrstni red vozlišč
Topološki vrstni red je linearna ureditev vseh vozlišč grafa, ki upošteva naslednja pravila (oznaka $\prec$ pomeni "je pred"):
*   **Osnovno pravilo:** Če v grafu obstaja pot od vozlišča $u$ do vozlišča $v$ ($u \leadsto v$), potem se mora v topološkem vrstnem redu $u$ pojaviti pred $v$ ($u \prec v$).
*   **Obratno:** Če obstaja pot $v \leadsto u$, potem velja $v \prec u$.
*   **Primer neprimerljivosti:** Če med vozliščema $u$ in $v$ ne obstaja nobena pot (niti od $u$ do $v$, niti od $v$ do $u$), je njun medsebojni vrstni red poljuben. Lahko izberemo $u \prec v$ ali $v \prec u$.

**Algoritem za topološko urejanje**
Algoritem temelji na iskanju v globino (**DFS** – *Depth-First Search*) in izkorišča čase zaključka obdelave posameznih vozlišč.

**Psevdokoda:**
```text
function Topološko-uredi(G)

1. Poženi DFS(G) na celotnem grafu.
       
2. Izračunaj čase zaključka (v.f) za vsako vozlišče.
       
3. Uredi (izpiši) vozlišča v padajočem vrstnem redu njihovih časov zaključka.
```
Vozlišče, ki se zaključi najkasneje (ima največji $v.f$), bo v topološkem vrstnem redu na prvem mestu.


**Dokaz pravilnosti (Zakaj algoritem deluje?)**

Dokazati moramo, da za vsako povezavo $u \to v$ v grafu velja, da se $u$ zaključi kasneje kot $v$ ($v.f < u.f$), kar zagotavlja, da bo $u$ v padajočem vrstnem redu pred $v$.

Recimo, da imamo povezavo $u \to v$ in da je DFS pravkar odkril vozlišče $u$ ($u$ postane sivo). V tem trenutku je vozlišče $v$ lahko v enem od dveh stanj:

### Primer 1: Vozlišče $v$ je belo
Če je $v$ še neodkrito (belo), bo postalo potomec vozlišča $u$ v DFS-gozdu. Po lastnostih iskanja v globino velja:
*   $u$ se odkrije pred $v$ ($u.d < v.d$).
*   $v$ se mora v celoti obdelati in zaključiti, preden se lahko zaključi obdelava njegovega prednika $u$.
*   Torej velja časovno zaporedje: $u.d < v.d < v.f < u.f$.
*   Iz tega neposredno sledi: **$v.f < u.f$**.

### Primer 2: Vozlišče $v$ je črno
Če je $v$ že zaključeno (črno), to pomeni, da je bila obdelava $v$ končana, preden smo sploh prišli do $u$. Ker smo $u$ šele zdaj odkrili, velja:
*   $v.f < u.d$ (zaključek $v$ pred odkritjem $u$).
*   Ker vemo, da je $u.d < u.f$, dobimo zaporedje: $v.f < u.d < u.f$.
*   Tudi v tem primeru velja: **$v.f < u.f$**.

### Zakaj $v$ ne more biti sivo?
Če bi bilo vozlišče $v$ v trenutku odkritja $u$ sivo, bi to pomenilo, da je $v$ prednik vozlišča $u$ v trenutnem rekurzivnem klicu. Povezava $u \to v$ bi bila v tem primeru **povratna povezava**. Obstoj povratne povezave pa pomeni, da graf vsebuje **cikel**. Ker smo predpostavili, da je graf acikličen (DAG), je to nemogoče.

**Sklep:** V vsakem primeru (ko je $v$ belo ali črno) bo veljalo $v.f < u.f$. Padajoče urejanje po časih zaključka torej pravilno postavi izvorno vozlišče $u$ pred ciljno vozlišče $v$.



## Krepko povezane komponente (SCC)

Naj bo $G = (V, E)$ usmerjen graf.
*   **Krepko povezana komponenta:** To je maksimalna množica vozlišč $V' \subseteq V$ takšna, da za vsak par vozlišč $u, v \in V'$ obstajata:
    1.  Pot od $u$ do $v$ ($u \leadsto v$).
    2.  Pot od $v$ do $u$ ($v \leadsto u$).
*   **Cilj problema:** Poiskati vse take ločene množice vozlišč v podanem usmerjenem grafu.

![[Pasted image 20260408122100.png]]

**Algoritem krepko povezanih komponent (Kosarajujev algoritem)**
Algoritem za iskanje SCC izkorišča lastnosti iskanja v globino (DFS) in transponiranega grafa.

**Postopek:**
1.  Poženi **DFS(G)** na originalnem grafu, da izračunaš čase zaključka $v.f$ za vsa vozlišča.
2.  Uredi vozlišča po **padajočih časih zaključka**: $\langle v_1, v_2, \dots, v_n \rangle$.
3.  Izdelaj **transponirani graf $G^T$**:
    *   Vozlišča ostanejo ista.
    *   Vse povezave se obrnejo: $(u, v) \in G.E \iff (v, u) \in G^T.E$.
4.  Poženi **DFS($G^T$)**, vendar v glavni zanki obravnavaj vozlišča v vrstnem redu, določenem v 2. koraku.
5.  **Rezultat:** Vsako posamezno drevo v nastalem DFS-gozdu predstavlja natanko eno krepko povezano komponento.


**Komponentni graf ($G^{SCC}$)**
Če vsako krepko povezano komponento obravnavamo kot eno samo vozlišče, dobimo **komponentni graf**.
*   Vozlišča $V^{SCC} = \{c_1, c_2, \dots, c_k\}$ so same komponente.
*   Povezava med komponentama $C_i \to C_j$ obstaja, če v originalnem grafu obstaja vsaj ena povezava $u \to v$, kjer je $u \in C_i$ in $v \in C_j$.

![[Pasted image 20260408122126.png]]

**Trditev 1: Komponentni graf je acikličen (DAG)**

**Dokaz:**
Recimo, da bi v komponentnem grafu obstajal cikel med komponentama $C$ in $C'$. To bi pomenilo, da obstaja pot $C \leadsto C'$ in pot $C' \leadsto C$. V tem primeru bi bila vsa vozlišča iz obeh komponent medsebojno dosegljiva, kar pomeni, da bi po definiciji morala pripadati isti krepko povezani komponenti. To je v protislovju s predpostavko, da sta $C$ in $C'$ različni komponenti.


 **Lastnosti časov zaključka v komponentah**
 
Definiramo čas zaključka komponente $C$ kot največji čas zaključka kateregakoli vozlišča v njej:
$$f(C) = \max_{v \in C} v.f$$

**Trditev 2: Povezave med komponentami in časi zaključka**

Naj bosta $C$ in $C'$ različni komponenti. Če v grafu $G$ obstaja povezava $(u, u')$, kjer je $u \in C$ in $u' \in C'$, potem velja:
$$f(C') < f(C)$$

**Dokaz:**
*   **Možnost 1:** DFS najprej obišče komponento $C$ (čas odkritja $u.d < u'.d$). Ker obstaja pot do $C'$, bodo vsa vozlišča v $C'$ postala potomci $u$ v DFS-drevesu. Zato se bodo vsa vozlišča v $C'$ zaključila pred $u$, torej $f(C') < u.f \le f(C)$.
*   **Možnost 2:** DFS najprej obišče komponento $C'$ ($u'.d < u.d$). Ker je komponentni graf acikličen, iz $C'$ ni poti nazaj v $C$. DFS bo zato v celoti obdelal in zaključil komponento $C'$, preden bo sploh dosegel vozlišče $u$. Ponovno velja $f(C') < f(C)$.

**Trditev 3: Lastnost v transponiranem grafu**

Če velja $f(C) > f(C')$, potem v transponiranem grafu $G^T$ **ne more** obstajati povezava iz $C$ v $C'$.
**Dokaz:**
Če bi v $G^T$ obstajala povezava $u \to u'$ ($u \in C, u' \in C'$), bi v originalnem grafu $G$ obstajala povezava $u' \to u$. Po Trditvi 2 bi to pomenilo $f(C) < f(C')$, kar je v neposrednem nasprotju z našo predpostavko.

---

**Pravilnost delovanja algoritma**

**Trditev:** Vsako DFS-drevo v drugem teku (na $G^T$) je natanko ena krepko povezana komponenta.

**Dokaz z indukcijo:**
Predpostavimo, da je prvih $k$ dreves pravilno identificiralo $k$ komponent. Naj bo $u$ koren $(k+1)$-tega drevesa in naj pripada komponenti $C$.
1.  Ker vozlišča obravnavamo po padajočih $v.f$ iz prvega teka, je $u$ vozlišče z največjim časom zaključka med vsemi še neobiskanimi vozlišči.
2.  Vsa ostala vozlišča v $C$ so še bela (neobiskana), zato bodo po izreku o beli poti postala potomci $u$ v tem DFS-drevesu.
3.  Ali lahko DFS "pobegne" v drugo komponento $C'$? V $G^T$ bi za to potrebovali povezavo iz $C$ v $C'$. Vendar vemo, da so vse komponente $C'$ z večjim $f(C')$ že obdelane. Za vse ostale pa velja $f(C') < f(C)$. Po Trditvi 3 v $G^T$ ni povezav iz $C$ v te neobdelane komponente.
4.  **Sklep:** Drevo bo zajelo vsa vozlišča komponente $C$ in nobene druge.


**Zakaj $G^T$ in padajoči časi?**

**Vprašanje:** Zakaj v drugi izvedbi ne bi enostavno pognali DFS na originalnem grafu z naraščajočimi časi zaključka?

**Odgovor:**
Bistvo algoritma je v tem, da v drugem teku obiskujemo komponente v **nasprotnem topološkem vrstnem redu** komponentnega grafa.
*   V prvem teku (na $G$) nam padajoči časi zaključka dajo topološki red komponent.
*   Z transponiranjem grafa ($G^T$) obrnemo vse povezave med komponentami.
*   Ko v $G^T$ začnemo pri komponenti z največjim $f(C)$ (ki je bila v $G$ "izvir"), je ta v $G^T$ postala "ponor". Ker iz nje v $G^T$ ni več izhodnih povezav v druge neobdelane komponente, se DFS omeji samo na to SCC.
*   Naraščajoči časi na originalnem grafu ne bi zagotovili te izolacije, saj bi DFS "ušel" po povezavah v druge sosednje komponente.






