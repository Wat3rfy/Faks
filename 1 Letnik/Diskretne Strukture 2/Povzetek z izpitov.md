

### **Pregled Vsebin in Ključnih Izrekov**

#### **I. Teorija Grafov**

**1. Osnovni Pojmi in Lastnosti Grafov**

*   **Definicije:** Graf $G=(V, E)$, enostaven graf, povezan graf, stopnja vozlišča $\deg(v)$, minimalna stopnja $\delta(G)$, maksimalna stopnja $\Delta(G)$, regularen graf, komplement grafa $\bar{G}$, podgraf, vpeti podgraf, dvodelni graf.
*   **Ključni Izreki:**
    *   **Lema o rokovanju (Handshaking Lemma):** $\sum_{v \in V} \deg(v) = 2|E|$.
    *   Graf je dvodelen natanko tedaj, ko ne vsebuje ciklov lihe dolžine.
*   **Tipi Nalog:**
    *   Določanje stopenj vozlišč in preverjanje regularnosti.
    *   Ugotavljanje, ali je graf dvodelen.
    *   Konstrukcija ali dokaz obstoja/neobstoja grafa z določenimi stopnjami.
    *   Določanje števila povezav v komplementu: $|E(\bar{G})| = \binom{n}{2} - |E(G)|$.
    *   Določanje, ali sta dva grafa izomorfna (preverjanje invariant: število vozlišč/povezav, zaporedje stopenj, število ciklov določene dolžine, etc.).

**2. Poti in Cikli (Euler in Hamilton)**

*   **Definicije:** Sprehod, pot, cikel. Eulerjev sprehod/obhod, Hamiltonova pot/cikel.
*   **Ključni Izreki:**
    *   **Eulerjev izrek:** Povezan graf ima Eulerjev obhod natanko tedaj, ko so vsa njegova vozlišča sode stopnje. Povezan graf ima Eulerjev sprehod natanko tedaj, ko ima 0 ali 2 vozlišči lihe stopnje.
    *   **Diracov izrek (zadostni pogoj za Hamiltonov cikel):** Če za enostaven graf $G$ z $n \ge 3$ vozlišči velja $\delta(G) \ge n/2$, potem je $G$ Hamiltonov.
    *   **Orejev izrek (posplošitev Diracovega):** Če za enostaven graf $G$ z $n \ge 3$ vozlišči za vsaki dve nesosednji vozlišči $u, v$ velja $\deg(u) + \deg(v) \ge n$, potem je $G$ Hamiltonov.
*   **Tipi Nalog:**
    *   Ugotavljanje, ali je graf Eulerjev ali Hamiltonov.
    *   Iskanje Hamiltonovega cikla ali dokaz, da ne obstaja (pogosto z uporabo razpadnega kriterija: če z odstranitvijo $k$ vozlišč dobimo več kot $k$ komponent, graf ni Hamiltonov).
    *   Koliko najmanj potez je potrebnih, da narišemo graf? (Odgovor je $|V_{lihe}|/2$, kjer je $V_{lihe}$ množica vozlišč lihe stopnje).

**3. Ravninskost Grafov**

*   **Definicije:** Ravninska risba, ravninski graf, lice (ploskev) v ravninski risbi. Subdivizija grafa, kontrakcija povezave.
*   **Ključni Izreki:**
    *   **Eulerjeva formula za ravninske grafe:** Za povezan ravninski graf z $n$ vozlišči, $m$ povezavami in $f$ lici velja: $n - m + f = 2$.
    *   **Posledice Eulerjeve formule:** Za enostaven povezan ravninski graf z $n \ge 3$ velja $m \le 3n - 6$. Če je graf še dvodelen, velja $m \le 2n - 4$.
    *   **Kuratowskega izrek:** Graf je ravninski natanko tedaj, ko ne vsebuje podgrafa, ki je subdivizija grafa $K_5$ ali $K_{3,3}$.
*   **Tipi Nalog:**
    *   Preverjanje, ali je graf ravninski (z risanjem ali z uporabo posledic Eulerjeve formule, npr. če je $m > 3n-6$, graf ni ravninski).
    *   Iskanje $K_5$ ali $K_{3,3}$ minorja za dokaz neravninskosti.
    *   Uporaba Eulerjeve formule za določanje števila lic, vozlišč ali povezav.

**4. Barvanje Grafov**

*   **Definicije:** Pravilno barvanje vozlišč/povezav, $k$-barvljivost. Kromatično število $\chi(G)$, kromatični indeks $\chi'(G)$. Kromatični polinom $P_G(k)$. Klika $\omega(G)$.
*   **Ključni Izreki:**
    *   **Osnovne meje:** $\chi(G) \ge \omega(G)$, $\chi(G) \ge \frac{n}{\alpha(G)}$ (kjer je $\alpha(G)$ število neodvisnosti).
    *   **Brooksov izrek:** Za povezan graf $G$, ki ni poln graf ali cikel lihe dolžine, velja $\chi(G) \le \Delta(G)$.
    *   **Vizingov izrek:** Za enostaven graf $G$ velja $\Delta(G) \le \chi'(G) \le \Delta(G) + 1$. Grafi so razreda 1, če je $\chi'(G) = \Delta(G)$, in razreda 2, če je $\chi'(G) = \Delta(G) + 1$.
    *   **Rekurzija za kromatični polinom:** $P_G(k) = P_{G-e}(k) - P_{G \cdot e}(k)$.
*   **Tipi Nalog:**
    *   Določanje kromatičnega števila in indeksa za dani graf.
    *   Iskanje največje klike.
    *   Izračun kromatičnega polinoma.
    *   Uporaba izrekov za ocenjevanje kromatičnega števila.

**5. Vpeta Drevesa in Povezanost**

*   **Definicije:** Drevo, gozd, vpeto drevo. Povezanost vozlišč $\kappa(G)$, povezanost po povezavah $\lambda(G)$.
*   **Ključni Izreki:**
    *   **Cayleyjeva formula:** Število vpetih dreves polnega grafa $K_n$ je $\tau(K_n) = n^{n-2}$.
    *   **Matrični drevesni izrek (Matrix Tree Theorem):** Število vpetih dreves grafa $G$ je enako kateremukoli kofaktorju Laplaceove matrike $L(G)$, kjer je $L = D - A$ ($D$ je diagonalna matrika stopenj, $A$ je matrika sosednosti).
    *   **Whitneyjev izrek:** Za vsak graf $G$ velja $\kappa(G) \le \lambda(G) \le \delta(G)$.
*   **Tipi Nalog:**
    *   Računanje števila vpetih dreves (z uporabo rekurzije, skrčenja/brisanja povezav, ali z matričnim drevesnim izrekom).
    *   Določanje $\kappa(G)$ in $\lambda(G)$.

**6. Operacije na Grafih**

*   **Definicije:** Kartezični produkt $G \square H$, linijski graf $L(G)$, join $G \circ H$.
*   **Tipi Nalog:**
    *   Risanje grafov, ki so rezultat operacij (npr. $C_3 \square C_3$).
    *   Določanje lastnosti (hamiltonskost, ravninskost, kromatično število) teh novih grafov.

#### **II. Teorija Grup**

To področje se osredotoča na abstraktne algebrske strukture, njihove lastnosti in preslikave med njimi.

**1. Osnovni Pojmi in Primeri Grup**

*   **Definicije:** Grupa, podgrupa, red grupe $|G|$, red elementa $o(g)$, Abelova (komutativna) grupa, center grupe $Z(G)$.
*   **Ključni Izreki:**
    *   **Lagrangeov izrek:** Če je $H$ podgrupa končne grupe $G$, potem red $H$ deli red $G$. Posledično red vsakega elementa deli red grupe.
*   **Primeri Grup:**
    *   Ciklične grupe $(Z_n, +)$.
    *   Multiplikativne grupe obrnljivih elementov $(Z_n^*, \cdot)$.
    *   Simetrične grupe $(S_n, \circ)$ in alternirajoče grupe $(A_n, \circ)$.
    *   Diedrske grupe $(D_n, \circ)$ (grupa simetrij n-kotnika).
    *   Matrične grupe $(GL(n, F), \cdot)$.
*   **Tipi Nalog:**
    *   Preverjanje, ali je dana struktura grupa.
    *   Iskanje reda elementov in podgrup.
    *   Delo s permutacijami: zapis v obliki ciklov, določanje reda, parnosti (sodo/liho).
    *   Delo z diedrskimi grupami z uporabo relacij med generatorji ($r^n=e, s^2=e, sr=r^{-1}s$).

**2. Homomorfizmi, Odseki in Kvocientne Grupe**

*   **Definicije:** Homomorfizem grup, izomorfizem, jedro homomorfizma $\ker(f)$, slika homomorfizma $\text{im}(f)$. Levi/desni odseki ($gH, Hg$). Indeks podgrupe $[G:H]$. Normalna podgrupa (edinka) $H \triangleleft G$. Kvocientna grupa $G/H$.
*   **Ključni Izreki:**
    *   Jedro homomorfizma je vedno normalna podgrupa.
    *   **Prvi izrek o izomorfizmu:** $G/\ker(f) \cong \text{im}(f)$.
    *   **Cayleyjev izrek:** Vsaka grupa je izomorfna neki podgrupi simetrične grupe.
    *   Podgrupa z indeksom 2 je vedno normalna.
    *   $G/Z(G)$ je ciklična $\implies$ $G$ je Abelova.
*   **Tipi Nalog:**
    *   Preverjanje, ali je dana preslikava homomorfizem.
    *   Iskanje jedra in slike.
    *   Določanje, ali je podgrupa normalna.
    *   Naštevanje odsekov.
    *   Identifikacija kvocientne grupe (npr. $D_{12}/H \cong ?$ ).
    *   Uporaba izreka o izomorfizmu za dokazovanje izomorfnosti med grupami.

**3. Produkti in Struktura Grup**

*   **Definicije:** Direkten produkt grup $G_1 \times G_2$.
*   **Ključni Izreki:**
    *   **Kitajski izrek o ostankih (za grupe):** Če sta $m, n$ tuji števili, potem je $Z_{mn} \cong Z_m \times Z_n$ in $Z_{mn}^* \cong Z_m^* \times Z_n^*$.
    *   Struktura končnih Abelovih grup.
*   **Tipi Nalog:**
    *   Določanje, ali je dana grupa izomorfna produktu cikličnih grup (npr. $Z_{26}^*$).
    *   Uporaba Kitajskega izreka o ostankih za razcep grup.

#### **III. Kolobarji in Obsegi**

To področje je manj poudarjeno, a se pojavlja redno, še posebej v kontekstu končnih obsegov.

**1. Osnovni Pojmi**

*   **Definicije:** Kolobar, komutativen kolobar, enota. Delitelji niča, obrnljivi elementi (enote). Integralni kolobar (domena celosti), obseg. Ideal.
*   **Ključni Izreki:**
    *   Kolobar $Z_n$ je obseg natanko tedaj, ko je $n$ praštevilo.
*   **Tipi Nalog:**
    *   Preverjanje, ali je dana struktura kolobar.
    *   Iskanje deliteljev niča in obrnljivih elementov v $Z_n$.
    *   Reševanje linearnih enačb in sistemov v $Z_n$.

**2. Polinomski Kolobarji**

*   **Definicije:** Kolobar polinomov $F[x]$. Deljenje polinomov, nerazcepni (ireducibilni) polinom.
*   **Ključni Izreki:**
    *   **Evklidov algoritem za polinome:** za iskanje največjega skupnega delitelja.
*   **Tipi Nalog:**
    *   Računanje s polinomi (seštevanje, množenje) v $Z_p[x]$.
    *   Iskanje inverza polinoma z razširjenim Evklidovim algoritmom.

**3. Končni Obsegi (Galois Fields)**

*   **Definicije:** Kvocientni kolobar $F[x]/\langle p(x) \rangle$. Končni obseg $GF(p^n)$.
*   **Ključni Izreki:**
    *   Če je $p(x)$ nerazcepen polinom stopnje $n$ nad obsegom $Z_p$, potem je $Z_p[x]/\langle p(x) \rangle$ obseg z $p^n$ elementi.
    *   Multiplikativna grupa končnega obsega $(F^*, \cdot)$ je vedno ciklična.
*   **Tipi Nalog:**
    *   Preverjanje, ali je polinom nerazcepen nad $Z_p$.
    *   Konstrukcija končnega obsega, npr. $GF(2^5)$.
    *   Iskanje inverza elementa v končnem obsegu (zapisanega kot polinom).

Upam, da vam ta podroben pregled pomaga pri pripravi na izpit! Vso srečo