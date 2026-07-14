https://www.youtube.com/watch?v=KHCAhwd7y-U&list=PL-47DDuiZOMDFbeI0tsri7Z2IKiPafwqB&index=2

https://www.andrej.com/zapiski/ISRM-PPJ-2026/book/07-izpeljava-tipov/07-izpeljava-tipov.html


**Podatkovni tip** je klasifikacija ki prevejalniku oz. interpreterju pove kakšne vrste podatkov vsebuje spremenljivka.

Tipi so lahko **statični**, ko mora biti podatkovni tip določen pred izvajanjem ali prevajanjem programa ali **dinamični**, kjer se preverjanje skladnosti tipov izvaja med **izvajanjem programa**.

Pri statičnem imajo spremenljivke določen tip.
Pri dinamičnem imajo vrednosti določen tip.

<br>

Ločimo tudi med **močno in šibko tipiziranimi**.

Šibko tipizirani dopuščajo implicitne pretvorbe oz. jezik samodejno pretvori en tip v drugega.

Močno tipizirani ne izvajajo implicitnih pretvorb. Če se podatkovna tipa ne ujemata vrne napako.

<br>

Porgramski jezik lahko tipe **preverja** ali **izpeljuje**.

Če jih preverjamo potem eksplicitno določimo za vsako spremenljivko jezik pa preveri če se ujemajo. *Tu javi napako če se tipi ne ujemajo.*

Če jih jezik izpeljuje potem ne pišemo tipa, programski jezik pa sam ugotovi katerega tipa mora biti. *Tu javi napako če se ne da izpeljati podatkovnega tipa.*

<br>

Vrednosti so lahko tudi **monomorfne in polimorfne**.

Če ima izraz lahko največ en tip je **monomorfen**, če ima izraz lahko več razlčinih tipov je **polimorfen**. *Na primer funkcija je polimorfna - lahko je int $\rightarrow$ int,..., lahko so tudi razredi in podrazredi (temu se reče ad-hoc polimorfizem)*

Poznamo več polimorfizmov, **parametrični polimorfizem** je lastnost kjer se tip podatkovne strukture ali izraza definira s spremenljivko, izvajanje pa je neodvisno od tipa vrednosti.

Pri ad-hoc polimorfizmu je izvajanje odvisno od tipa vrednosti. 

***
**Izpeljava tipov**

Glavni tip izraza je **najbolj splošen tip** ki ga lahko dodelimo nekemu izrazu ne da bi pri tem izgubili informacije o njegovem delovanju.

Če imamo neko funkcijo jo lahko včasih opišemo z več tipi. Glavni je tisti iz katerega lahko izpeljemo vse ostale veljavne tipe.

$$\lambda x.x$$

je lahko

$$\text{int} \rightarrow \text{int}$$
$$\text{string} \rightarrow \text{string}$$

zato je glavni tip

$$\alpha \rightarrow \alpha$$

kjerj je $\alpha$ poljuben tip.

<br>

Ocaml lahko za vsak izraz izpelje njegov glavni tip. *Razen za polimorfne rekurzivne funkcije kjer moramo opredeliti tip, saj algoritem za izpeljavo tipa za rek. f. ne obstaja.*

Glavni tip nekega izraza $e$ dobimo s tem da zanj definiramo enačbo nato pa rešimo za vse njegove neznanke.



Tukaj je prepis pravil za izračunavanje tipov in generiranje enačb, kot so prikazana na slikah. Ta pravila se uporabljajo pri **algoritmu za sklepanje o tipih** (type inference).

**Pravila izpeljave**

*   `true` ima tip `bool`, brez enačb
*   `false` ima tip `bool`, brez enačb
*   celoštevilska konstanta `0`, `1`, `2`, ... ima tip `int`, brez enačb
*   spremenljivka ima svoj dani tip (tipe spremenljivk sproti beležimo v *kontekstu*)
*   **aritmetični izraz $e_1 + e_2$:**
    *   izračunamo tip $\tau_1$ izraza $e_1$ in dobimo še enačbe $E_1$
    *   izračunamo tip $\tau_2$ izraza $e_2$ in dobimo še enačbe $E_2$
    *   Tip izraza $e_1 + e_2$ je `int`, z enačbami $E_1, E_2$ in $\tau_1 = \text{int}, \tau_2 = \text{int}$. Podobno obravnavamo ostale aritmetične izraze $e_1 * e_2, e_1 - e_2, \dots$
*   **boolov izraz $e_1 \&\& e_2$:** obravnavamo podobno kot aritmetični izraz, le da uporabimo pričakovani `bool` namesto `int`.
*   **primerjava celih števil $e_1 < e_2$:**
    *   izračunamo tip $\tau_1$ izraza $e_1$ in dobimo še enačbe $E_1$
    *   izračunamo tip $\tau_2$ izraza $e_2$ in dobimo še enačbe $E_2$
    *   Tip izraza $e_1 < e_2$ je `bool`, z enačbami $E_1, E_2$ in $\tau_1 = \text{int}, \tau_2 = \text{int}$
*   **pogojni stavek `if e1 then e2 else e3`:**
    *   izračunamo tip $\tau_1$ izraza $e_1$ in dobimo še enačbe $E_1$
    *   izračunamo tip $\tau_2$ izraza $e_2$ in dobimo še enačbe $E_2$
    *   izračunamo tip $\tau_3$ izraza $e_3$ in dobimo še enačbe $E_3$
    *   Tip izraza `if e1 then e2 else e3` je $\tau_2$, z enačbami $E_1, E_2, E_3, \tau_1 = \text{bool}, \tau_2 = \tau_3$



*   **urejeni par $(e_1, e_2)$:**
    *   izračunamo tip $\tau_1$ izraza $e_1$ in dobimo še enačbe $E_1$
    *   izračunamo tip $\tau_2$ izraza $e_2$ in dobimo še enačbe $E_2$
    *   Tip izraza $(e_1, e_2)$ je $\tau_1 \times \tau_2$, z enačbami $E_1, E_2$.
*   **prva projekcija `fst e`:**
    *   izračunamo tip $\tau$ izraza $e$ in dobimo še enačbe $E$
    *   Uvedemo nova parametra $\alpha$ in $\beta$ (se ne pojavljata v $E$). Tip izraza `fst e` je $\alpha$, z enačbami $E, \tau = \alpha \times \beta$.
*   **druga projekcija `snd e`:**
    *   izračunamo tip $\tau$ izraza $e$ in dobimo še enačbe $E$
    *   Uvedemo nova parametra $\alpha$ in $\beta$. Tip izraza `snd e` je $\beta$, z enačbami $E, \tau = \alpha \times \beta$.
*   **funkcija `fun x -> e`:** uvedemo nov parameter $\alpha$ in zabeležimo, da ima $x$ tip $\alpha$, ter
    *   izračunamo tip $\tau$ izraza $e$ (pri predpostavki, da ima $x$ tip $\alpha$) in dobimo še enačbe $E$
    *   Tip funkcije `fun x -> e` je $\alpha \to \tau$ z enačbami $E$.
*   **aplikacija $e_1 e_2$:**
    *   izračunamo tip $\tau_1$ izraza $e_1$ in dobimo še enačbe $E_1$
    *   izračunamo tip $\tau_2$ izraza $e_2$ in dobimo še enačbe $E_2$
    *   Uvedemo nov parameter $\alpha$. Tip izraza $e_1 e_2$ je $\alpha$, z enačbami $E_1, E_2, \tau_1 = \tau_2 \to \alpha$.
*   **prazen seznam `[]`:** uvedemo nov parameter $\alpha$, tip je $\alpha \text{ list}$.
*   **sestavljen seznam $e_1 :: e_2$:**
    *   izračunamo tip $\tau_1$ izraza $e_1$ in dobimo še enačbe $E_1$
    *   izračunamo tip $\tau_2$ izraza $e_2$ in dobimo še enačbe $E_2$
    *   Tip izraza $e_1 :: e_2$ je $\tau_1 \text{ list}$, z enačbami $E_1, E_2$ in $\tau_2 = \tau_1 \text{ list}$.
*   **rekurzivna definicija $x = e$** (kjer se $x$ pojavi v $e$): uvedemo nov parameter $\alpha$, zabeležimo, da ima $x$ tip $\alpha$, ter
    *   izračunamo tip $\tau$ izraza $e$ (pri predpostavki, da ima $x$ tip $\alpha$) in dobimo še enačbe $E$
    *   Tip izraza $x$ je $\tau$, z enačbami $E, \alpha = \tau$. *Opomba: običajno na ta način definiramo rekurzivne funkcije, torej bo $x$ v resnici funkcija.*