

# Napredno urejanje in dvojiško iskanje

Osnovni algoritmi (mehurčno, vstavljanje) imajo zahtevnost $O(n^2)$, kar je za velike podatke neuporabno. Napredni algoritmi to izboljšajo na $O(n \log n)$.

## 1. Napredni algoritmi (temeljijo na primerjavah)

### Urejanje z zlivanjem (Mergesort)
*   **Strategija:** "Deli in vladaj". Seznam razdelimo na dve polovici, ju rekurzivno uredimo in nato **zlijemo** (združimo).
*   **Zlivanje (Merge):** Primerjamo prva elementa dveh urejenih seznamov in manjšega prestavimo v rezultat.
*   **Zahtevnost:** Vedno **$O(n \log n)$** (najboljši, povprečni in najslabši primer).
*   **Prostor:** Običajno zahteva dodatnih $O(n)$ prostora za pomožne tabele.

### Hitro urejanje (Quicksort)
*   **Strategija:** Izberemo **pivot** (delilni element). Vse manjše elemente prestavimo levo, večje pa desno od pivota. Postopek rekurzivno ponovimo za oba dela.
*   **Particija:** Ključni korak, kjer elemente razdelimo glede na pivot.
*   **Zahtevnost:**
    *   Povprečna/Najboljša: **$O(n \log n)$**.
    *   Najslabša: **$O(n^2)$** (če je pivot slabo izbran, npr. pri že urejenem seznamu).
*   **Značilnost:** V praksi je pogosto hitrejši od Mergesorta, ker ima manjše konstante in se ga da učinkovito izvesti "na mestu".

### Urejanje s kopico (Heapsort)
- Na neurejenem arrayu naredimo max heap. Zamenjamo zadnji element in prvi. Znižamo mejo unsorted heapa kjer je sedaj element na koncu urejen in naredimo nov max heap iz elementov novega arraya te rponavljamo. Video: https://www.youtube.com/watch?v=2DmK_H7IdTo

---

## 2. Urejanje brez primerjav (Linearno urejanje)
Če poznamo dodatne lastnosti podatkov (npr. omejen razpon števil), lahko urejamo hitreje kot $O(n \log n)$.

*   **Urejanje s štetjem (Counting Sort):** Preštejemo pojavitve vsake vrednosti. Zahtevnost $O(n + m)$, kjer je $m$ razpon vrednosti. Učinkovito le, če $m$ ni prevelik. Video: https://www.youtube.com/watch?v=OKd534EWcdk
*   **Urejanje s koši (Bucket Sort):** Elemente razporedimo v "koše" glede na vrednost, nato vsak koš posebej uredimo.
*   **Korensko urejanje (Radix Sort):** Urejanje po posameznih znakih ali števkah (npr. od prve do zadnje črke). Zahtevnost $O(nd)$, kjer je $d$ dolžina najdaljšega elementa.


---

## 4. Dvojiško iskanje (Binary Search)
Urejanje je smiselno predvsem zato, ker omogoča hitro iskanje.

*   **Princip:** V urejenem seznamu preverimo srednji element. Če je iskani element manjši, iščemo v levi polovici, sicer v desni.
*   **Zahtevnost:** **$O(\log n)$**.
*   **Implementacija:** Iskanje meje med elementi, ki so `< x` in elementi, ki so `≥ x`.
*   **Invarianta:** Uporaba kazalcev `lo` (kaže na manjše) in `hi` (kaže na večje ali enako), dokler se ne srečata.
*   **Standardne funkcije (C++):**
    *   `std::lower_bound`: vrne prvo mesto, kamor lahko vstavimo element `x`, da ohranimo urejenost (prvi element $\ge x$).
    *   `std::upper_bound`: vrne zadnje mesto za vstavljanje (prvi element $> x$).

---

## Povzetek zahtevnosti (Napredni algoritmi)

| Algoritem | Čas (Povprečno) | Čas (Najslabše) | Prostor (Dodatno) |
| :--- | :--- | :--- | :--- |
| **Mergesort** | $O(n \log n)$ | $O(n \log n)$ | $O(n)$ |
| **Quicksort** | $O(n \log n)$ | $O(n^2)$ | $O(\log n)$ ali $O(n)$ |
| **Counting Sort** | $O(n + m)$ | $O(n + m)$ | $O(m)$ |
| **Radix Sort** | $O(nd)$ | $O(nd)$ | $O(n + a)$ |

**Poudarek:** Pri dvojiškem iskanju pazite na pravilno nastavljanje mej (`lo`, `hi`), da se izognete neskončnim zankam ali napakam pri praznih seznamih.