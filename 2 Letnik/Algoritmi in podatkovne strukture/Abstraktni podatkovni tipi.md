Tukaj so pregledni zapiski na podlagi predloženega gradiva o abstraktnih podatkovnih tipih (APT) in podatkovnih strukturah (PS).

---

# Zapiski: Abstraktni podatkovni tipi in podatkovne strukture

## 1. Osnovni pojmi
*   **Abstraktni podatkovni tip (APT / ADT):** Definira množico vrednosti in dovoljene operacije (funkcionalnost), ne pa tudi konkretne implementacije. (Primer: "Sklad" pove, da gre za LIFO strukturo, ne pove pa, ali uporablja polje ali seznam).
*   **Podatkovna struktura (PS / DS):** Konkreten način organizacije in hrambe podatkov v pomnilniku, ki omogoča učinkovito uporabo (dostop, obdelava, spreminjanje).

---

## 2. Linearni podatkovni tipi

### Polje (*Array*)
*   **Kot APT:** Urejen nabor elementov z dostopom preko celoštevilskih indeksov (`get(i)`, `set(i, x)`).
*   **Kot PS:** Zaporedni bloki pomnilnika enake velikosti.
*   **Časovna zahtevnost:** Dostop do poljubnega elementa je $O(1)$.

### Sklad (*Stack*)
*   **Načelo:** LIFO (*Last In, First Out*) – zadnji noter, prvi ven.
*   **Operacije:**
    *   `push(x)`: Dodaj na vrh.
    *   `pop()`: Odstrani z vrha.
    *   `top()` / `peek()`: Preglej vrhnji element.
*   **Uporaba:** Rekurzija, procesni sklad, razčlenjevanje izrazov.

### Seznam (*List*)
*   **Povezani seznam (*Linked List*):** Vozlišča s podatki in kazalci na naslednike.
    *   *Prednost:* Hitro vstavljanje/brisanje (če imamo referenco).
    *   *Slabost:* Dostop do $i$-tega elementa zahteva $O(n)$.
*   **Dinamično polje (*Dynamic Array*):**
    *   Ob dosegu kapacitete se alocira novo (običajno 2x večje) polje.
    *   **Amortizirana zahtevnost:** Dodajanje na konec je $O(1)$, čeprav je posamezna operacija ob povečanju lahko $O(n)$.

### Vrsta (*Queue*)
*   **Načelo:** FIFO (*First In, First Out*) – prvi noter, prvi ven.
*   **Operacije:** `enqueue(x)` (dodaj na konec), `dequeue()` (vzemi z začetka).
*   **Implementacije:**
    *   Povezani seznam (potrebujemo kazalec na začetek in konec).
    *   Krožno polje (učinkovita poraba prostora).
    *   Z dvema skladoma (amortizirano $O(1)$).

---

## 3. Vrsta s prednostjo (*Priority Queue*)
Elementi se ne vračajo po vrstnem redu vstavljanja, temveč glede na prioriteto.

### Kopica (*Binary Heap*)
*   **Struktura:** Poravnano dvojiško drevo.
    *   *Min-heap:* Starš je manjši ali enak otrokoma (koren je najmanjši).
*   **Predstavitev s poljem:**
    *   Element na indeksu $i$ ima otroka na $2i$ in $2i+1$.
    *   Starš elementa $i$ je na $\lfloor i/2 \rfloor$.
*   **Zahtevnost:** `push` in `pop` sta $O(\log n)$.
*   **Floydov algoritem:** Izgradnja kopice iz poljubnega polja v času $O(n)$.

### Druge strukture za prioriteto:


### 1. Korenska dekompozicija (Square Root Decomposition)
*   **Logika:** Seznam z $n$ elementi razdelimo na **$\sqrt{n}$ skupin**, kjer vsaka skupina vsebuje **$\sqrt{n}$ elementov**.
*   **Postopek:** Pri iskanju najprej "skačemo" po skupinah, dokler ne najdemo prave, nato pa znotraj nje poiščemo točen element.
*   **Zahtevnost:** $O(\sqrt{n})$ za iskanje in vstavljanje (ker preiščemo največ dve korenski razdalji).
*   **Prednost:** Izjemno preprosta implementacija; primerna za hitre operacije na celih blokih podatkov.

### 2. Preskočni seznam (Skip List)
*   **Logika:** Nadgradnja povezanega seznama z več **nivoji "ekspresnih prog"**. Višji nivoji preskakujejo večje število vozlišč.
*   **Postopek:** Iščemo od najvišjega nivoja navzdol. Na vrhu delamo dolge skoke, nato se spustimo nižje za natančnejše iskanje.
*   **Verjetnost:** Višina vsakega elementa (število nivojev, v katerih se pojavi) je določena naključno (npr. z metom kovanca).
*   **Zahtevnost:** Pričakovano **$O(\log n)$** za vse operacije (iskanje, vstavljanje, brisanje).
*   **Prednost:** Hitrost primerljiva z uravnoteženimi drevesi, a z lažjim algoritmom in boljšo podporo za vzporedno (multithreaded) delo.

---

## 4. Asociativni podatkovni tipi

### Množica (*Set*)
*   Hrani unikatne elemente (brez ponovitev).
*   Ne predpisuje vrstnega reda.

### Slovar (*Map / Dictionary*)
*   Hrani pare **(ključ, vrednost)**. Vsak ključ je unikaten.
*   **Zgoščena tabela (*Hash Table*):**
    *   **Zgoščevalna funkcija ($h(x)$):** Preslika ključ v indeks v tabeli.
    *   **Trk (*Collision*):** Ko se dva različna ključa preslikata v isti indeks.
    *   **Reševanje trkov:**
        *   *Veriženje (Chaining):* Vsak indeks v tabeli kaže na seznam elementov.
        *   *Odprto naslavljanje:* Iskanje naslednjega prostega mesta v tabeli.
    *   **Zahtevnost:** Ob primernem razmerju zasedenosti (*load factor*) $\alpha$ in ponovnem zgoščevanju (*rehashing*) so operacije v povprečju $O(1)$.

---

## Povzetek časovnih zahtevnosti (povprečno)

| Podatkovna struktura | Dostop / Iskanje | Vstavljanje | Brisanje |
| :--- | :--- | :--- | :--- |
| **Polje** | $O(1)$ | $O(n)$ | $O(n)$ |
| **Dinamično polje** | $O(1)$ | $O(1)^*$ | $O(n)$ |
| **Povezani seznam** | $O(n)$ | $O(1)$ | $O(1)$ |
| **Sklad / Vrsta** | / | $O(1)$ | $O(1)$ |
| **Dvojiška kopica** | $O(1)$ (min) | $O(\log n)$ | $O(\log n)$ |
| **Zgoščena tabela** | $O(1)$ | $O(1)$ | $O(1)$ |
| **Preskočni seznam** | $O(\log n)$ | $O(\log n)$ | $O(\log n)$ |

*\*amortizirano*