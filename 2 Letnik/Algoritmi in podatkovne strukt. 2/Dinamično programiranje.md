

## 1. Problem trgovskega potnika (Traveling Salesman Problem - TSP)

### Definicija problema
Cilj je poiskati **najcenejši Hamiltonov cikel** v polnem neusmerjenem grafu z utežmi (cenami) na povezavah.
### Formalizacija
*   Podan je neusmerjen graf $G = (V, E)$, kjer je $V = \{0, 1, \dots, n-1\}$.
*   $c(u, v)$ je cena povezave med vozliščema $u$ in $v$.
*   $S(u_1 \to u_2 \to \dots \to u_k)$ je cena celotnega sprehoda.
*   **Minimiziramo**: $S(\sigma(0) \to \sigma(1) \to \dots \to \sigma(n-1) \to \sigma(0))$ preko vseh možnih permutacij $\sigma$ množice vozlišč.
*   Zaradi ciklične narave fiksiramo začetek: $\sigma(0) = 0$.

### Naivno reševanje
*   Preizkusimo vse permutacije vozlišč $1, 2, \dots, n-1$.
*   Število permutacij je $(n-1)!$. Za vsako izračunamo ceno v času $O(n)$.
*   Skupna časovna zahtevnost: **$O(n!)$**.

### Dinamično programiranje (Held-Karpov algoritem)
Namesto preizkušanja vseh poti, gradimo optimalni cikel s pomočjo podproblemov.

**Rekurenčna enačba:**
Naj bo $u \in V$ in $M \subseteq V \setminus \{0, u\}$.
$S(u \to M)$ predstavlja ceno optimalnega sprehoda, ki:
1.  Se prične v vozlišču $u$.
2.  Obišče vsa vozlišča v množici $M$ natanko enkrat (v poljubnem vrstnem redu).
3.  Se konča v vozlišču $0$.

**Izračun $S(u \to M)$:**
*   **Robni primer**: $S(u \to \emptyset) = c(u, 0)$ (iz $u$ gremo neposredno v $0$).
*   **Splošni primer** ($M = \{v_1, \dots, v_k\}$):
    $$S(u \to M) = \min_{i=1}^k \left( c(u, v_i) + S(v_i \to M \setminus \{v_i\}) \right)$$
    *Najprej gremo iz $u$ do nekega $v_i \in M$, nato pa iz $v_i$ čez ostala vozlišča v $M$ do $0$.*

**Cilj**: Izračunati $S(0 \to \{1, 2, \dots, n-1\})$.

### Implementacija in tabela $D$
Za shranjevanje rezultatov potrebujemo dvodimenzionalno tabelo $D[u, b(M)]$:
*   **Vrstični indeks**: Trenutno vozlišče $u$.
*   **Stolpčni indeks**: Množica $M$, predstavljena s celoštevilskim indeksom.
*   **Predstavitev množice $M$**: Uporabimo **karakteristični vektor** (bitna maska).
    *   Primer: Za $n=5$ in množico $\{1, 2, 4\}$ je vektor `1101`, kar ustreza decimalnemu indeksu 13.
*   **Velikost tabele**: $n \times 2^{n-1}$.
*   **Vrstni red polnjenja**: Po naraščajočih vrednostih $b(M)$ (od manjših podmnožic k večjim).

### Rekonstrukcija poti
Vzdržujemo dodatno tabelo $Z[u, b(M)]$, kjer shranimo vozlišče $v$, ki je vodilo do minimuma v rekurenčni enačbi.
1.  $v_1 = Z[0, b(\{1, \dots, n-1\})]$ (začetek: $0 \to v_1$)
2.  $v_2 = Z[v_1, b(\{1, \dots, n-1\} \setminus \{v_1\})]$
3.  Nadaljujemo, dokler ne obiščemo vseh vozlišč.

### Časovna zahtevnost
*   Število celic v tabeli: $O(n \cdot 2^n)$.
*   Izračun vsake celice: $O(n)$ (iskanje minimuma).
*   Skupaj: **$O(n^2 \cdot 2^n)$**. To je bistveno boljše od $O(n!)$.

---

## 2. Problem spuščanja jajc (Egg Dropping Puzzle)

### Definicija problema
Imamo stavbo z $N$ nadstropji in $K$ enakih jajc. Ugotoviti želimo **trdnost jajca** (najvišje nadstropje, s katerega se jajce ne razbije) z minimalnim številom spustov v **najslabšem primeru**.

### Prvi pristop: $S(n, k)$
Naj bo $S(n, k)$ minimalno število spustov za $n$ zaporednih nadstropij in $k$ jajc.

**Robni primeri:**
*   $S(0, k) = 0$ (ni nadstropij, ni spustov).
*   $S(n, 1) = n$ (z enim jajcem moramo preizkusiti vsako nadstropje od spodaj navzgor).

**Rekurenčna enačba:**
Če prvo jajce spustimo z nadstropja $i$:
1.  Jajce se **razbije**: Ostane nam $k-1$ jajc in $i-1$ nadstropij pod njim $\implies 1 + S(i-1, k-1)$.
2.  Jajce se **ne razbije**: Ostane nam $k$ jajc in $n-i$ nadstropij nad njim $\implies 1 + S(n-i, k)$.

Ker iščemo najslabši primer, vzamemo $\max$, za optimalno strategijo pa izberemo $i$, ki ta $\max$ minimizira:
$$S(n, k) = 1 + \min_{i=1}^n \{ \max(S(i-1, k-1), S(n-i, k)) \}$$
Časovna zahtevnost tega algoritma z DP: **$O(N^2 K)$**.

---

### Druga možnost: Izboljšava $N(s, k)$
Problem pogledamo z druge strani: Koliko je najvišje nadstropje $N$, ki ga lahko pokrijemo s $s$ spusti in $k$ jajci?

**Logika izračuna $N(s, k)$:**
Spustimo jajce z nadstropja $x$.
*   Če se razbije, lahko z $s-1$ spusti in $k-1$ jajci pokrijemo $N(s-1, k-1)$ nadstropij **pod** $x$.
*   Če preživi, lahko z $s-1$ spusti in $k$ jajci pokrijemo $N(s-1, k)$ nadstropij **nad** $x$.
*   Vključno z nadstropjem $x$, je skupno število pokritih nadstropij:
    $$N(s, k) = N(s-1, k-1) + N(s-1, k) + 1$$

**Povezava s kombinatoriko:**
Z indukcijo se dokaže: $N(s, k) = \sum_{i=1}^k \binom{s}{i}$.

**Rešitev prvotne uganke s pomočjo $N(s, k)$:**
$S(n, k)$ je najmanjši $s$, pri katerem velja $N(s, k) \ge n$.
*   Ker $N(s, k)$ narašča s $s$, lahko $s$ iščemo z **bisekcijo** na intervalu $[1, n]$.
*   Za vsak korak bisekcije izračunamo $N(s, k)$ v času $O(K)$.
*   Časovna zahtevnost: **$O(K \log N)$**.

---

## 3. Dinamično programiranje kot graf

Izvajanje DP algoritma si lahko predstavljamo kot potovanje po **usmerjenem acikličnem grafu (DAG)**.

*   **Vozlišča**: Stanja (podproblemi).
*   **Povezave**: Prehodi (odvisnosti med podproblemi).
*   **Primer (0/1 nahrbtnik)**:
    *   Stanje $C(i, v)$ (maksimalna cena s predmeti od $i$ dalje pri preostali prostornini $v$).
    *   Prehodi so določeni s funkcijo prehodov: ali vzamemo predmet $i$ ali ne.

### Načini potovanja po grafu
1.  **Od zgoraj navzdol (Top-down)**:
    *   Memoizirana rekurzija.
    *   Obišče le vozlišča, ki so dosegljiva iz začetnega stanja.
    *   Slabost: rekurzivni klici, večja poraba prostora na skladu.
2.  **Od spodaj navzgor (Bottom-up)**:
    *   Iterativno polnjenje tabele.
    *   Izračuna vsa možna stanja.
    *   Prednost: boljša izraba predpomnilnika, možnost optimizacije prostora (npr. hranjenje le trenutnega in prejšnjega nivoja - prostor $O(V)$ namesto $O(nV)$).

---

## 4. Pregled časovnih zahtevnosti

| Problem | Stanja in prehod (splošni primer) | Časovna zahtevnost |
| :--- | :--- | :--- |
| **Nahrbtnik** | $C(i, v) = \max(C(i+1, v), c_i + C(i+1, v-v_i))$ | $O(nV)$ |
| **NNP (LIS)** | $\ell(i) = 1 + \max\{\ell(j) \mid j > i \wedge a_j > a_i\}$ | $O(n^2)$ |
| **Matrike** | $M(i, j) = \min_{t=i}^{j-1} (M(i, t) + M(t+1, j) + v_i v_{t+1} v_{j+1})$ | $O(n^3)$ |
| **Potnik (TSP)** | $S(u \to M) = \min_{v_i \in M} (c(u, v_i) + S(v_i \to M \setminus \{v_i\}))$ | $O(2^n \cdot n^2)$ |
| **Jajca** | $S(n, k) = 1 + \min_{i=1}^n \max(S(i-1, k-1), S(n-i, k))$ | $O(NK \log N)$ ali $O(N^2 K)$ |

---

## 5. V razmislek
Vsi rekurzivni problemi niso primerni za dinamično programiranje. Tipična primera, kjer DP ni smiseln (običajno zaradi pomanjkanja prekrivajočih se podproblemov ali narave iskanja), sta:
*   **Osem dam** (iskanje vseh postavitev na šahovnici).
*   **Skakačev obhod** (Knight's tour).
Ti problemi se rešujejo s preiskovanjem (backtracking).