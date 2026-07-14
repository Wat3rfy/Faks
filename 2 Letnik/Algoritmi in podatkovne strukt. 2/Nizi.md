**Niz** (string) je končno zaporedje simbolov iz neke končne, neprazne množice, ki jo imenujemo **abeceda** $\Sigma$. 

Niz dolžine $n$ zapišemo kot $S = a_1 a_2 \dots a_n$, kjer za vsak simbol velja $a_i \in \Sigma$. Dolžino niza označimo z $|S| = n$.

Pri analizi algoritmov nad nizi se običajno uporablja indeksiranje od 1 naprej, kar nam omogoča natančen zapis matematičnih izpeljav:
* $S[i] = a_i$ označuje simbol na $i$-tem mestu v nizu.
* $S[i : j]$ predstavlja podniz, ki se začne na indeksu $i$ in konča na indeksu $j$ (vključno z obema).
* $S[i :]$ označuje podniz od indeksa $i$ do konca niza.
* $S[: i]$ označuje začetni podniz od začetka niza do indeksa $i$.

Definiram lahko dve lastnosti
* **Predpona oz. prefiks** $R \sqsubseteq S$: Niz $R$ je predpona niza $S$, če velja $|R| \le |S|$ in je $R$ enak začetnemu delu niza $S$, torej $R = S[: |R|]$.
* **Pripona oz. sufiks** $R \sqsupseteq S$: Niz $R$ je pripona niza $S$, če velja $|R| \le |S|$ in je $R$ enak končnemu delu niza $S$, torej $R = S[|S| - |R| + 1 :]$.

***

**Problem iskanja vzorca v besedilu**

Problem iskanja v nizih definiramo z dvema vhodnima nizoma nad isto abeceda $\Sigma$
1. **Besedilo $T$:** Niz dolžine $n$ ($|T| = n$).
2. **Vzorec $P$:** Niz dolžine $m$ ($|P| = m$).

Pri tem običajno predpostavimo omejitev $1 \le m \le n$.

Naš cilj je poiskati vse pojavitve vzorca $P$ v besedilu $T$. Pojavitev določimo z **odmikom $s$**. Pravimo, da se vzorec $P$ pojavi z odmikom $s$, če velja

$$T[s + 1 : s + m] = P$$

To lahko označimo kot 

$$T_{s}[1:m] = P$$

To lahko zapišemo tudi s pomočjo pripone, in sicer da je vzorec $P$ pripona dela besedila do mesta $s+m$

$$P \sqsupseteq T[: s + m]$$

Najpreprostejši način za iskanje je naivni algoritem, ki preveri vse možne odmike. Ker imamo $n - m + 1$ možnih položajev za odmik in za vsako primerjavo podnizov porabimo $O(m)$ operacij, je skupna časovna zahtevnost naivnega pristopa v najslabšem primeru

$$O(m \cdot (n - m + 1)) = O(mn)$$

Spodnja meja za reševanje tega problema je sicer $\Omega(n)$, saj moramo v splošnem pregledati skoraj vsak znak v besedilu.

***

**Rabin-Karpov algoritem**


Če abecedo predstavimo kot množico $\Sigma = \{a_1, a_2, \dots, a_B\}$, si lahko vsak niz nad to abecedo predstavljamo kot število v sistemu z osnovo $|\Sigma| = B$. Vsakemu simbolu $a_i$ najprej priredimo vrednost $f(a_i) = i - 1$. Vrednost celotnega niza dolžine $n$ potem izračunamo kot:
$$f(a_{i_1} a_{i_2} \dots a_{i_n}) = \sum_{j=1}^{n} (i_j - 1) B^{n-j}$$

Pri fiksni dolžini niza $m$ je ta funkcija bijektivna, zato velja:
$$P = T[s + 1 : s + m] \iff f(P) = f(T[s + 1 : s + m])$$

Če bi za vsak odmik računali to vrednost na novo, ne bi pridobili ničesar, saj bi še vedno potrebovali $O(m)$ časa na odmik. Vendar pa lahko naslednjo vrednost (v t.i. drsečem oknu oziroma *rolling hash*) izračunamo iz prejšnje v konstantnem času $O(1)$:
$$f(T[s + 2 : s + m + 1]) = B \cdot \left( f(T[s + 1 : s + m]) - T[s + 1] \cdot B^{m-1} \right) + f(T[s + m + 1])$$

V praksi so vrednosti $f(P)$ lahko prevelike za običajne registre, zato celoten izračun izvajamo po modulu nekega velikega praštevila $q$. Ker s tem izgubimo bijektivnost, se lahko pojavi **trk (kolizija)**. Če sta zgoščeni vrednosti različni, se niza zagotovo ne ujemata. Če sta enaki, pa moramo niza še dejansko primerjati znak po znaku ($O(m)$), da potrdimo ujemanje.

Časovna zahtevnost z uporabo modula znaša:
* V povprečnem primeru: $O(n + m)$.
* V najslabšem primeru (ko pride do velikega števila trkov): $O(mn)$.

Psevdokoda algoritma je naslednja:

```python
function RABIN-KARP(T, P, B, q)
    n = |T|
    m = |P|
    f = 0  # hash za vzorec P
    g = 0  # hash za trenutno okno v T
    h = B^(m-1) mod q
    
    # Predobdelava: izračun hash vrednosti za P in prvi podniz T
    for i = 1 to m do
        f = (B*f + P[i]) mod q
        g = (B*g + T[i]) mod q
        
    # Iskanje po besedilu
    for s = 0 to n - m do
        if f == g then
            # Če se hasha ujemata, preveri dejansko ujemanje nizov
            if P == T[s + 1 : s + m] then
                PRINT(s)
        
        # Izračunaj hash za naslednje okno (rolling hash)
        if s < n - m then
            g = (B*(g - T[s + 1]*h) + T[s + m + 1]) mod q
```

***

**Priponska funkcija in izboljšava naivnega iskanja**

Naivni algoritem je neučinkovit, ker po neujemanju odmik vedno premakne le za $1$, pri čemer pozabi vse informacije, ki jih je pridobil z ujemanjem predhodnih znakov. 

V splošnem je največje varno povečanje odmika ($\Delta s$) odvisno od treh dejavnikov:
1. Strukture vzorca $P$ (ponavljanje delov znotraj vzorca). *Če je vzorec abab in se ujema z delom teksta potem lahko vzorec premaknemo za 2, če bi ga  morali za manj bi moralo veljati da je pripona velikosti 3, tudi predpona velikosti 3, tega vzorca, edina taka pripona je velikosti 3.*
2. Položaja neujemanja $r$ (število ujemajočih se znakov). *Če se vzorec ne ujema popolnoma, recimo da je vzorec ababcd in se ujema abab del potem po istem razmisleku vemo da lahko vzorec premaknemo za 2 saj, če bi gamorali za manj bi spet moralo veljati da ababa vsebuje pripono velikosti 3, ki je tudi pripona velikosti 3.*
3. Znaka v besedilu na točki neujemanja ($T[s + r + 1]$).

Za formalno določitev varnih premikov definiramo **priponsko funkcijo** $\sigma(S)$, ki predstavlja dolžino najdaljše pripone vzorca $S$, ki je hkrati predpona niza $P$

$$\sigma(S) = \max \{k \mid P[: k] \sqsupseteq S \}$$

To lahko uporabimo za določanje premika. 

Če pogledamo odsek besedila $T$ kjer imamo $r$ ujemajočih znakov in prvega neujemajočega bo to $T_{s}[1:r+1]$.

Mi lahko prestavimo vzorec naprej za dolžino že preverjenega besedila, razen če velja da je v tem intervalu $T_{s}[1:r+1]$ pripona dolžine $k$ ki je hkrati predpona v $P$ potem bi preskočili potencialno ujemanje zato moramo vzorec zamakniti nazaj da se dela besedila ujemata.

$$\Delta s = r + 1 - \sigma(T[s + 1 : s + r + 1])$$

***

**Iskanje z determinističnim končnim avtomatom (DKA)**

Da ne računamo $\sigma$ vsakič ko preverjamo besedilo sestavimo končni avtomat ki sledi koliko znakov se ujema, ob nepredvidenem znaku pa avtomat ve da je pred njim že prebral neke znake in če velja da zaporedje znakov ki jih je že prebral skupaj s tem nepredvidenim znakom tvori že nek del vzorca nas vrne direktno v to stanje.
* Stanj je $Q = \{0, 1, \dots, m\}$, kjer $q$ predstavlja število ujemajočih se znakov. Začetno stanje je $q_0 = 0$, končno stanje pa $F = \{m\}$.
* Prehodna funkcija $\delta(q, a)$, ki določa prehod v naslednje stanje ob branju znaka $a$
  
$$\delta(q, a) = \sigma(P[: q]a)$$

Ko je tak avtomat enkrat zgrajen, je iskanje izjemno hitro, saj za vsak znak besedila naredimo natanko en prehod. Časovna zahtevnost iskanja je tako **$O(n)$**, kar je optimalno.

Težava pa se lahko pojavi pri pripravi avtomata. Izračunati moramo prehode za vseh $m$ stanj in vse možne znake iz abecede $\Sigma$. V naivni izvedbi izračun funkcije $\sigma$ zahteva primerjavo nizov, kar vodi do časovne zahtevnosti gradnje

$$O(m \cdot |\Sigma| \cdot m \cdot m) = O(m^3 |\Sigma|)$$

kjer je $m |\Sigma|$ posledica vseh možnih prehodov in stanj, *za vsako stanje $m$ računamo vse prehode $|\Sigma|$*, za vsako od teh moramo vsako predpono preveriti z vsako pripono, kar bo $m^{2}$ da izračunamo $\sigma$, torej $m^{2} \cdot m|\Sigma|$.

Za daljše vzorce ali večje abecede je ta časovna zahtevnost lahko prevelika, zato se v praksi uporabljajo naprednejši pristopi, kot je algoritem Knuth-Morris-Pratt.

***

**Knutt-Morris-Prattov algoritem**



Pri računanju **maksimalnega varnega premika** vzorca vzdolž besedila upoštevamo le lastnosti vzorca in položaj neujemajočega se znaka v vzorcu, ne pa tudi pripadajočega neujemajočega se znaka v besedilu.

Ker ne poznamo stanja v katerega pridemo iz znaka v besedilu na mestu neujemanja preverimo če se pripona trenutno preverjenega dela z ujema s predpono vzorca, nato preverimo če se naslednji znak ujema z vzorcem če se ne moramo ponoviti postopek, s čimer ugotavljamo prehodno funkcijo od prej sproti.

Na ta način se izognemo odvisnosti od velikosti abecede $\Sigma$. Za predobdelavo vzorca bomo potrebovali le $O(m)$ časa, premiki pa v resnici ne bodo nič manjši kot pri iskanju z avtomatom le mogoče bo trajalo malo dlje.

---

**Največji varen premik in predponska funkcija**



Za določitev premikov definiramo **predponsko funkcijo** $\pi[j]$.

Vrednost $\pi[j]$ predstavlja dolžino najdaljše prave predpone $P[1:j]$ ki je prava pripona $P[1:j]$.

$$\pi[j] = \max \{ k < j \,;\; T[j - k + 1 : i] = P[1 : k] \}$$



Izračunan premik $\Delta s$ po neujemanju določimo kot
* Pri $j = 0$ je $\Delta s = 1$
* Sicer je $\Delta s = j - \pi[j]$


---

**Učinkovit izračun predponske funkcije**

Neposreden izračun $\pi[j]$ po definiciji za vsak indeks zahteva $O(m^2)$ primerjav. Z indukcijo pa lahko tabelo $\pi$ zgradimo v času $O(m)$.

Vemo, da je $\pi[1] = 0$. Predpostavimo, da smo že izračunali vrednosti $\pi[1], \dots, \pi[j-1]$ in želimo določiti $\pi[j]$. Pri tem vzdržujemo kazalec $k$, ki predstavlja dolžino trenutno najdaljše veljavne predpone, ki je hkrati pripona. Če se naslednji znak $P[k+1]$ ne ujema s $P[j]$, se moramo pomakniti nazaj na naslednjo krajšo predpono, kar storimo z določitvijo $k \leftarrow \pi[k]$.

Psevdokoda postopka predobdelave:

```python
function IZRAČUNAJ-PREDPONSKO-FUNKCIJO(P)
    m = |P|
    Izdelaj tabelo pi[1 : m]
    pi[1] = 0
    k = 0
    for j = 2 to m do
        while k > 0 and P[k + 1] != P[j] do
            k = pi[k]
        if P[k + 1] == P[j] then
            k = k + 1
        pi[j] = k
    return pi
```

**Časovna zahtevnost predobdelave:**
Čeprav vsebuje zanka `for` notranjo zanko `while`, časovna zahtevnost ni $O(m^2)$.
* Vrednost $k$ se poveča za največ $1$ v vsaki iteraciji zunanje zanke, torej se skupno poveča največ $(m-1)$-krat.
* Znotraj zanke `while` se vrednost $k$ zmanjša vsaj za $1$ v vsakem koraku (saj velja $\pi[i] < i$), pri čemer nikoli ne postane negativna.
* Skupno število zmanjšanj v zanki `while` zato ne more presegati skupnega števila povečanj. Skupno število korakov zanke `while` skozi celoten tek algoritma je omejeno z $m-1$.
* Iz tega sledi, da je časovna zahtevnost predobdelave **$O(m)$**.

---

**Iskanje pojavitev z algoritmom KMP**

Ko imamo vnaprej izračunano tabelo $\pi$, lahko izvedemo iskanje vzorca $P$ v besedilu $T$ s pomočjo dveh kazalcev: $i$ (za tek po besedilu $T$) in $j$ (za sledenje ujemanju v vzorcu $P$). Iskanje z algoritmom KMP deluje analogno iskanju z avtomatom, vendar prehode računamo sproti z uporabo tabele $\pi$.

Psevdokoda iskanja:

```python
function KMP(T, P)
    n = |T|
    m = |P|
    pi = IZRAČUNAJ-PREDPONSKO-FUNKCIJO(P)
    j = 0  # število ujemajočih se znakov
    
    for i = 1 to n do
        while j > 0 and P[j + 1] != T[i] do
            j = pi[j]
        if P[j + 1] == T[i] then
            j = j + 1
        if j == m then
            PRINT(i - m)  # izpis odmika uspešnega ujemanja
            j = pi[j]     # pripravi se na iskanje naslednje pojavitve
```

**Časovna zahtevnost iskanja:**
Z enakim razmislekom kot pri predobdelavi analiziramo spreminjanje spremenljivke $j$:
* $j$ se poveča za največ $1$ v vsaki iteraciji zunanje zanke `for` (torej največ $n$-krat).
* V vsaki iteraciji zanke `while` se $j$ strogo zmanjša.
* Skupno število zmanjšanj $j$ ne more biti večje od skupnega števila povečanj.
* Skupna časovna zahtevnost iskalne faze je zato **$O(n)$**.

Celoten algoritem KMP (gradnja tabele in iskanje) se tako izvede v optimalnem času

$$O(n + m)$$


**Priponska tabela**

Priponska tabela je tabela ki vsebuje indekse pripon besedila $T$ po abecednem redu. To pomeni da primarno uredimo po črkah nato pa po dolžinah.

Ker vemo da če se vzorec $P$ pojavi v $T$ se mora pojaviti kot začetek neke pripone v $T$ oz. se mora pojaviti kot predpona neke pripone v $T$. Ker so pripone urejene po abecedne vrstnem redu bodo vse pripone ki vsebujejo $P$ blizu skupaj, torej bo iskanje vseh pojavitev, ko imamo veliko vzorcev za preverit veliko hitreje kot KMP.

Potrebujemo

$$O(m \log_{}{n} + k)$$

kjer je $k$ število pojavitev vzorca. VIdimo lahko da je $m\log_{}{n}$ dvojiško iskanje začetka in konca intervala, kjer pri vsaki od $\log_{}{n}$ primerjav preverjamo $m$  znakov.

$O(k)$ je čas izpisa $k$ indeksov.

Naivna izdelava tabele rabi $O(n^{2} \log_{}{n})$, kar je $n \log_{}{n}$ za urejanje pripon, za vsako primerjavo pa rabimo $n$ časa.

To lahko izboljšamo, saj vemo da za polj. niza $x = x_{1}x_{2}$, $y= y_{1}y_{2}$ velja

$$x \prec y \Leftrightarrow x_{1} \prec y_{1} \lor (x_{1}=y_{1} \land x_{2}\prec y_{2})$$

Pripone lahko uredimo v $\lceil \log_{}{n}\rceil +1$ iteracijah kjer jih v $k$-ti iterciji uredimo glede na prvih $2^{k-1}$ znakov.

Naj bo **rang** $r_{k}(i)$ zaporedno mesto po abecedi ki ga dobi pripona ki se začne na indeksu $i$ dolžine $2^{k-1}.$ Rang nam pove kako so razporejeni podnizi dolžine $2^{k-1}$.



| $i$ | $T[i:][:1]$ | $r_1(i)$ |
| :---: | :--- | :---: |
| 1 | `a` | 1 |
| 2 | `b` | 2 |
| 3 | `r` | 5 |
| 4 | `a` | 1 |
| 5 | `k` | 4 |
| 6 | `a` | 1 |
| 7 | `d` | 3 |
| 8 | `a` | 1 |
| 9 | `b` | 2 |
| 10 | `r` | 5 |
| 11 | `a` | 1 |

| $i$ | $T[i:][:2]$ | $(r_1(i), r_1(i+1))$ | $r_2(i)$ | $i$ | $T[i:][:2]$ | $(r_1(i), r_1(i+1))$ | $r_2(i)$ |
| :---: | :--- | :---: | :---: | :---: | :--- | :---: | :---: |
| 1 | `ab` | (1,2) | 2 | 11 | `a` | (1,0) | 1 |
| 2 | `br` | (2,5) | 5 | 1 | `ab` | (1,2) | 2 |
| 3 | `ra` | (5,1) | 8 | 8 | `ab` | (1,2) | 2 |
| 4 | `ak` | (1,4) | 4 | 6 | `ad` | (1,3) | 3 |
| 5 | `ka` | (4,1) | 7 | 4 | `ak` | (1,4) | 4 |
| 6 | `ad` | (1,3) | 3 | 2 | `br` | (2,5) | 5 |
| 7 | `da` | (3,1) | 6 | 9 | `br` | (2,5) | 5 |
| 8 | `ab` | (1,2) | 2 | 7 | `da` | (3,1) | 6 |
| 9 | `br` | (2,5) | 5 | 5 | `ka` | (4,1) | 7 |
| 10 | `ra` | (5,1) | 8 | 3 | `ra` | (5,1) | 8 |
| 11 | `a` | (1,0) | 1 | 10 | `ra` | (5,1) | 8 |

| $i$ | $T[i:][:4]$ | $(r_2(i), r_2(i+2))$ | $r_3(i)$ | $i$ | $T[i:][:4]$ | $(r_2(i), r_2(i+2))$ | $r_3(i)$ |
| :---: | :--- | :---: | :---: | :---: | :--- | :---: | :---: |
| 1 | `abra` | (2,8) | 2 | 11 | `a` | (1,0) | 1 |
| 2 | `brak` | (5,4) | 6 | 1 | `abra` | (2,8) | 2 |
| 3 | `raka` | (8,7) | 10 | 8 | `abra` | (2,8) | 2 |
| 4 | `akad` | (4,3) | 4 | 6 | `adab` | (3,2) | 3 |
| 5 | `kada` | (7,6) | 8 | 4 | `akad` | (4,3) | 4 |
| 6 | `adab` | (3,2) | 3 | 9 | `bra` | (5,1) | 5 |
| 7 | `dabr` | (6,5) | 7 | 2 | `brak` | (5,4) | 6 |
| 8 | `abra` | (2,8) | 2 | 7 | `dabr` | (6,5) | 7 |
| 9 | `bra` | (5,1) | 5 | 5 | `kada` | (7,6) | 8 |
| 10 | `ra` | (8,0) | 9 | 10 | `ra` | (8,0) | 9 |
| 11 | `a` | (1,0) | 1 | 3 | `raka` | (8,7) | 10 |


| $i$ | $T[i:][:8]$ | $(r_3(i), r_3(i+4))$ | $r_4(i)$ | $i$ | $T[i:][:8]$ | $(r_3(i), r_3(i+4))$ | $r_4(i)$ |
| :---: | :--- | :---: | :---: | :---: | :--- | :---: | :---: |
| 1 | `abrakada` | (2,8) | 3 | 11 | `a` | (1,0) | 1 |
| 2 | `brakadab` | (6,3) | 7 | 8 | `abra` | (2,0) | 2 |
| 3 | `rakadabr` | (10,7) | 11 | 1 | `abrakada` | (2,8) | 3 |
| 4 | `akadabra` | (4,2) | 5 | 6 | `adabra` | (3,9) | 4 |
| 5 | `kadabra` | (8,5) | 9 | 4 | `akadabra` | (4,2) | 5 |
| 6 | `adabra` | (3,9) | 4 | 9 | `bra` | (5,0) | 6 |
| 7 | `dabra` | (7,1) | 8 | 2 | `brakadab` | (6,3) | 7 |
| 8 | `abra` | (2,0) | 2 | 7 | `dabra` | (7,1) | 8 |
| 9 | `bra` | (5,0) | 6 | 5 | `kadabra` | (8,5) | 9 |
| 10 | `ra` | (9,0) | 10 | 10 | `ra` | (9,0) | 10 |
| 11 | `a` | (1,0) | 1 | 3 | `rakadabr` | (10,7) | 11 |


| $i$ | $T[i:]$ | $r(i)$ | $SA[i]$ | $T[SA[i]]$ |
| :---: | :--- | :---: | :---: | :--- |
| 1 | `abrakadabra` | 3 | 11 | `a` |
| 2 | `brakadabra` | 7 | 8 | `abra` |
| 3 | `rakadabra` | 11 | 1 | `abrakadabra` |
| 4 | `akadabra` | 5 | 6 | `adabra` |
| 5 | `kadabra` | 9 | 4 | `akadabra` |
| 6 | `adabra` | 4 | 9 | `bra` |
| 7 | `dabra` | 8 | 2 | `brakadabra` |
| 8 | `abra` | 2 | 7 | `dabra` |
| 9 | `bra` | 6 | 5 | `kadabra` |
| 10 | `ra` | 10 | 10 | `ra` |
| 11 | `a` | 1 | 3 | `rakadabra` |

Imamo $O(\log_{}{n})$ iteracij, $O(n \log_{}{n})$ v vsaki iteraciji za urejanje rangov, torej dobimo

$$O(n \log^{2}_{}{n})$$

uoprabimo lahko korensko urejanje ker so rangi vedno v $\{ 1,...,n\}$ da dobimo $O(n)$ in posledično

$$O(n \log_{}{n})$$

**Z-funkcija**

$Z_{i}(S)$ je funkcija ki nam pove dolžino najdaljšega podniza $S$, ki se začne na indeksu $i$, in je hkrati predpona $S$, torej

$$\text{najdaljši niz }S[i:i+k-1] \text{ ki je hkrati predpona $S$}$$

oz.

$$\text{najdaljši niz }S_{i-1}[1 : k] \sqsubseteq S$$

$Z_{i}(S)$ torej definiramo kot

$$Z_{i}(S) = \max \{ k \,;\; S_{i-1}[1:k] \sqsubseteq S\,\}$$

Definiramo lahko tudi $Z$ škatlo kot interval $S_{i-1}[1:Z_{i}]$, kar je preprosto pripadajoč niz.

Nato naj bo $\mathcal{Z}_{i}$ najdlje segajoča Z-škatla ki vsebuje indeks $i$. Desni rob $r_{i}$ je končni indeks Z-škatle ki od vseh Z-škatel ki vsebujejo $i$ sega najdlje, levi rob pa naj bo začetni indeks iste škatle. Če jih je več, jo izberemo poljubno.

Naivno lahko Z funkcijo računamo tako da za $n$ indeksov zaporedno preverimo kako dolgo predpono tvori, kar traja $n$ časa, tako pridemo do $n^{2}$. Če hočemo dobiti $O(n)$ pa lahko sproti računamo $r_{i},l_{i},Z_{i}$.

**Sprotno računanje tabele $Z_{i}$**

Naj bo najdlje segajoča Z-škatla ki vsebuje indeks $i$ in se začne na indeksu $l$ označena kot $S_{l-1}[1:r]$, kjer je $l-1$ odmik, $r$ pa dolžina niza. 

*Torej bo to niz $S[l-1+1:l-1+r] = S[l :l+r-1]$.*

Na začetku neposredno izračunamo $Z_{2}, l_{2}, r_{2}$.

Naj za splošen $Z_{i}$ velja naslednje.

Naj bo $i$ v svoji najdlje segajoči škatli $S[i] \in S_{l-1}[1:r]$.

Naj bo $S[i] = S_{l-1}[j]$ kar samo pomeni da je $i$-ta črka v $S$ dejansko $j$-ta zaporedna črka v svoji $Z$-škatli.

Po definiciji $Z$-škatle vemo da se $S_{l-1}[1:r]$ pojavi na začetku $S$. Torej velja

$$S_{l-1}[1:r] = S[1:r]$$

To pomeni da imamo na $S[1:r]$ niz za katerega imamo že izračunane vrednosti $Z$ torej lahko samo vzamemo pripadajočo $Z$ vrednost. 

Vemo da je $S[j]$ na istem mestu kot $S_{l-1}[j] = S[i]$, kar pomeni da mora veljati


$$Z_{j} = Z_{i}$$

kjer je

$$S[j] \in S[1:r]$$
$$S[i] \in S_{l-1}[1:r]$$
$$S[i] = S_{l-1}[j]$$

Če je $Z_{j}$ prevelik in  $S_{l-1}[j:Z_{j}-1]$ ni v nizu $S_{l-1}[1:r]$, torej da podniz presega meje $S_{l-1}[1:r]$, v tem primeru vzamemo $Z_{i} = r-j+1$ in nadaljevanje niza preverimo z naivnim algoritmom.

Iz tega dobimo $Z_{i}$ in hkrati nov $l_{i}$ in $r_{i}$ za naslednje $i+1,i+2,...$

Če $i$ ni v $Z$-škatli potem moramo zanj izračunati $Z_{i}$ in pripadajoča $l_{i},r_{i}$ naivno.

**Tabela najadljših skupnih prepdon**

 Če imamo že podano tabelo pripon, potem tabela najdaljših predpon na $i$ tem indeksu vsebuje največjo dolžino predpone $i$ tega niza ki je hkrati predpona $i-1$ niza.

Naj tabela $R[i]$ na $i$-tem indeksu vsebuje leksikografsko mesto pripone ki se začne na $i$-tem indeksu.

Definiramo še funkcijo $bp(i)$ ki nam da $R[SA[i] +1]$.
Če $i$ označuje leksikografsko mesto nam $bp(i)$ vrne leksikografsko mesto pripone ki je za ena krajše od pripone na $i$-tem leksikografksem mestu.

$bp(i)$ je definirana za vse $i$ razen za $i = 0$.

LPC lahko izdelamo po definiciji a za to potrebujemo $O(n^{2})$.

Lahko jo zgradimo pa v $O(n)$.

Mogoče dokončam
TODO