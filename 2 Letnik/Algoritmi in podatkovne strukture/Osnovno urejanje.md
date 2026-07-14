

# Urejanje (Sorting)

Urejanje je proces preurejanja zaporedja elementov v določen vrstni red (npr. po abecedi, po velikosti, po starosti). 

*   **Primerjalni algoritmi:** Vrstni red določajo izključno na podlagi primerjave dveh elementov ($A < B$).
*   **Stabilnost:** Algoritem je stabilen, če ohranja prvotni vrstni red enakih elementov (pomembno npr. pri urejanju oseb po starosti, kjer želimo ohraniti abecedni vrstni red pri tistih z isto starostjo).
*   **Urejanje na mestu (In-place):** Algoritem ne potrebuje dodatnega seznama, ampak elemente preuredi znotraj obstoječega pomnilnika ($O(1)$ dodatnega prostora).

---

## 1. Neuporabni algoritmi (Bogosort)
Ti algoritmi služijo le za ilustracijo ekstremne neučinkovitosti.

*   **Deterministično urejanje s permutacijami:** Sistematično preverja vse možne permutacije seznama ($n!$), dokler ne najde urejene. 
*   **Naključno urejanje (Bogo-sort):** Seznam naključno premeša (`shuffle`) in preveri, ali je urejen. Postopek ponavlja do uspeha.
*   **Analiza:**
    *   Število permutacij pri $n$ elementih je $n!$.
    *   V povprečju deterministični algoritem preveri $n! / 2$ permutacij, naključni pa $n!$.
    *   Pri $n=10$ je to že več kot 3,6 milijona operacij.

---

## 2. Osnovni urejevalni algoritmi
Vsi trije spodnji algoritmi imajo prostorsko zahtevnost **$O(n)$** (celoten prostor) oziroma **$O(1)$** (dodatni prostor).

### Urejanje z izbiranjem (Selection Sort)
*   **Logika:** Poiščemo najmanjši element v neurejenem delu seznama in ga zamenjamo s prvim elementom neurejenega dela.
*   **Invarianta:** Po $i$ korakih je prvih $i$ elementov na svojih končnih mestih.
*   **Značilnosti:**
    *   **Časovna zahtevnost:** Vedno **$O(n^2)$** (tudi če je seznam že urejen, mora poiskati minimum).
    *   **Stabilnost:** **Ni stabilen** (zaradi dolgih skokov pri menjavi elementov).
    *   **Primer:** `[7, 2, 5, 1]` $\rightarrow$ najde `1`, zamenja s `7` $\rightarrow$ `[1, 2, 5, 7]`.

### Urejanje z vstavljanjem (Insertion Sort)
*   **Logika:** Gradimo urejen del seznama tako, da vzamemo naslednji neurejen element in ga vstavimo na pravo mesto med že urejene elemente (ostale zamaknemo).
*   **Invarianta:** Po $i$ korakih je prvih $i$ elementov urejenih (vendar to niso nujno končni najmanjši elementi celotnega seznama).
*   **Značilnosti:**
    *   **Časovna zahtevnost:** Najslabša $O(n^2)$, najboljša **$O(n)$** (če je seznam že skoraj urejen).
    *   **Stabilnost:** **Je stabilen**.
    *   **Uporaba:** Odličen za majhne sezname ali sezname, ki se jim sproti dodajajo elementi.

### Mehurčno urejanje (Bubble Sort)
*   **Logika:** Večkrat se sprehodimo čez seznam in zamenjamo sosednja elementa, če sta v napačnem vrstnem redu. Največji elementi "odbrbotajo" na konec.
*   **Optimizacija:** Če v celotnem prehodu ne naredimo nobene zamenjave, je seznam urejen in lahko končamo.
*   **Značilnosti:**
    *   **Časovna zahtevnost:** Najslabša $O(n^2)$, najboljša **$O(n)$** (z optimizacijo).
    *   **Stabilnost:** **Je stabilen**.

---

## Povzetek zahtevnosti

| Algoritem | Najboljša | Povprečna | Najslabša | Stabilnost |
| :--- | :--- | :--- | :--- | :--- |
| **Izbiranje** | $O(n^2)$ | $O(n^2)$ | $O(n^2)$ | Ne |
| **Vstavljanje** | $O(n)$ | $O(n^2)$ | $O(n^2)$ | Da |
| **Mehurčno** | $O(n)$ | $O(n^2)$ | $O(n^2)$ | Da |
| **Bogosort** | $O(n)$ | $O(n \cdot n!)$ | $\infty$ | Ne |

**Opomba:** Za velike podatke so ti algoritmi (razen v posebnih primerih) prepočasni; v praksi se uporabljajo naprednejši algoritmi, kot sta *QuickSort* ali *MergeSort*.