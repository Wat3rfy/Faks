Seveda, poglejmo tehnično plat delovanja predpomnilnikov še podrobneje.

---

### Tehnična razlaga delovanja predpomnilnikov

Na najbolj tehnični ravni je predpomnilnik (PP) visoko hitrostni SRAM pomnilnik, ki shranjuje kopije podatkov iz počasnejšega DRAM glavnega pomnilnika (GP). Glavna naloga predpomnilnika je preslikava pomnilniških naslovov in upravljanje s shranjenimi bloki besed.

**1. Struktura predpomnilnika (Cache Organization)**

Vsak predpomnilnik je sestavljen iz dveh glavnih delov:
*   **Podatkovni del (Data Array):** Tukaj so dejansko shranjeni bloki besed, preneseni iz glavnega pomnilnika.
*   **Imeniški del (Tag Array):** Tukaj so shranjene oznake (Tags) in veljavni biti (Valid Bits) za vsak blok v predpomnilniku.

**2. Predstavitev pomnilniškega naslova**

Ko CPE (procesor) zahteva podatek, poda pomnilniški naslov (logični naslov, ki ga nato MMU pretvori v fizični naslov, če se uporablja navidezni pomnilnik). Ta fizični naslov se nato razdeli na tri glavne komponente, ki jih predpomnilniški krmilnik (Cache Controller) uporabi za iskanje podatka:

`[Oznaka (Tag)] [Indeks (Index)] [Odmik/Offset (Block Offset)]`

*   **Odmik/Offset (Block Offset):** To je najmanj bitov, ki določa položaj iskanega bajta znotraj bloka besed (cache line). Če je velikost bloka npr. 64 bajtov, potem potrebujemo $log_2(64) = 6$ bitov za odmik (od 0 do 63).
*   **Indeks (Index):** Ta del naslova določa, v kateri *vrstico* (ali *set*) v predpomnilniku se mora podatek shraniti ali iskati. Število bitov za indeks je odvisno od velikosti predpomnilnika in števila blokov v vsakem naboru (setu).
*   **Oznaka (Tag):** Preostali najpomembnejši biti naslova. Ta oznaka se shrani skupaj z blokom besed v imeniškem delu predpomnilnika. Ko se blok najde z uporabo indeksa, se mora oznaka shranjena v PP ujemati z oznako v iskanem naslovu, da se potrdi zadetek.

**Primer razčlenitve naslova:**
*   Predpostavimo 32-bitne pomnilniške naslove.
*   Velikost bloka besed: 64 bajtov ($2^6$ bajtov) -> **Offset = 6 bitov**.
*   Velikost predpomnilnika: 16 KB (16 * 1024 = 16384 bajtov).
*   Tip predpomnilnika: *Neposredno preslikavajoč (Direct-Mapped)*.
    *   Število blokov v predpomnilniku: 16384 bajtov / 64 bajtov/blok = 256 blokov.
    *   Ker je to direktno preslikavajoč PP, ima vsaka vrstica v PP en blok, torej je 256 vrstic.
    *   Število bitov za indeks: $log_2(256) = 8$ bitov.
*   Število bitov za oznako: 32 (skupaj) - 6 (offset) - 8 (indeks) = **18 bitov**.

Torej, 32-bitni naslov bi bil razdeljen: `[Tag (18 bitov)] [Index (8 bitov)] [Offset (6 bitov)]`

**3. Strategije preslikovanja (Mapping Schemes)**

Določajo, kako se pomnilniški naslov preslika na specifično lokacijo v predpomnilniku:

*   **1. Neposredno preslikavajoč (Direct-Mapped Cache):**
    *   **Princip:** Vsak blok iz glavnega pomnilnika se lahko shrani na *samo eno specifično lokacijo* (vrstico) v predpomnilniku. To lokacijo določa indeks (Address Modulo NumberOfCacheLines).
    *   **Prednosti:** Najenostavnejši za implementacijo, najhitrejše iskanje (ni primerjanja).
    *   **Slabosti:** Visoka verjetnost "konfliktnih zgrešitev" (conflict misses). Če programa pogosto dostopata do dveh blokov, ki se preslikata na isto vrstico v PP, se bosta neprestano izrivala, kar zmanjšuje stopnjo zadetkov.
    *   **Delovanje:** Indeks določi vrstico, oznaka se primerja. Če se ujemata in je veljavni bit nastavljen, je to zadetek.

*   **2. Naborno-asociativni (Set-Associative Cache):**
    *   **Princip:** Predpomnilnik je razdeljen na "nabore" (sets). Vsak nabor vsebuje `N` vrstic (blokov). Blok iz glavnega pomnilnika se lahko shrani na *katero koli od `N` vrstic* znotraj določenega nabora. Nabor določa indeks.
    *   **Prednosti:** Zmanjšuje konfliktne zgrešitve v primerjavi z neposredno preslikavajočim. Dobro ravnotežje med kompleksnostjo in zmogljivostjo. (Npr. 2-smerni, 4-smerni, 8-smerni asociativni).
    *   **Slabosti:** Bolj kompleksna implementacija in iskanje (potrebno je primerjati oznake vseh `N` blokov znotraj nabora hkrati). Potreben je algoritem za nadomeščanje (glej spodaj).
    *   **Delovanje:** Indeks določi nabor. Vse oznake znotraj tega nabora se preverijo (ponavadi paralelno). Če se ena ujema in je veljavni bit nastavljen, je to zadetek.

*   **3. Popolnoma asociativni (Fully Associative Cache):**
    *   **Princip:** Blok iz glavnega pomnilnika se lahko shrani na *katero koli lokacijo* (vrstico) v celotnem predpomnilniku. Za indeks ni bitov, celoten pomnilniški naslov (razen odmika) je oznaka.
    *   **Prednosti:** Najnižja stopnja zgrešitev za dano velikost PP. Ni konfliktnih zgrešitev.
    *   **Slabosti:** Najbolj kompleksna in draga implementacija, saj je potrebno primerjati oznake vseh blokov v predpomnilniku hkrati. Običajno se uporablja samo za zelo majhne predpomnilnike (npr. TLB - Translation Lookaside Buffer).
    *   **Delovanje:** Iskana oznaka se primerja z *vsemi* oznakami v celotnem predpomnilniku (paralelno). Če se ena ujema, je to zadetek.

**4. Postopek dostopa do predpomnilnika (Cache Access Flow)**

1.  **CPE poda naslov:** Procesor zahteva podatek na določenem pomnilniškem naslovu.
2.  **Razčlenitev naslova:** Predpomnilniški krmilnik razdeli fizični naslov na Oznako (Tag), Indeks (Index) in Odmik (Offset).
3.  **Dostop do imeniškega dela:** Z uporabo Indeksa (in Odmika za izbiro bajta znotraj bloka) se dostopa do ustrezne vrstice/nabora v imeniškem delu predpomnilnika.
4.  **Preverjanje:**
    *   Preveri se **Veljavni bit (Valid Bit):** Ta bit kaže, ali podatki v tej vrstici PP veljajo (tj. so bili dejansko preneseni in so ažurni). Če je 0, je to avtomatično zgrešitev.
    *   Primerjaj **Oznako (Tag):** Oznaka shranjena v imeniškem delu vrstice PP se primerja z Oznako, pridobljeno iz pomnilniškega naslova.
5.  **Zadetek (Hit):**
    *   Če sta Veljavni bit 1 IN se Oznaki ujemata, je to zadetek.
    *   Podatek se pridobi iz Podatkovnega dela PP na lokaciji, ki jo določa Indeks in Odmik, in se posreduje CPE-ju. To je izjemno hitro.
6.  **Zgrešitev (Miss):**
    *   Če Veljavni bit ni 1 ALI se Oznaki ne ujemata, je to zgrešitev.
    *   Predpomnilniški krmilnik ustavi CPE (stalling).
    *   **Pridobitev bloka:** Iskani blok besed se pridobi iz naslednje nižje ravni pomnilniške hierarhije (npr. iz L2, L3 ali GP).
    *   **Nadomeščanje bloka:** Če je nabor, kamor spada novi blok, že poln (pri naborno-asociativnih in popolnoma asociativnih PP), se mora en obstoječi blok nadomestiti (izgnati). Za to se uporablja **strategija nadomeščanja (Replacement Policy)**.
    *   **Zapisovanje bloka:** Novi blok se zapiše v Podatkovni del PP na ustrezno mesto. Njegova Oznaka se zapiše v Imeniški del, Veljavni bit pa se nastavi na 1.
    *   **Posredovanje podatka:** Iskani podatek iz novega bloka se posreduje CPE-ju.

**5. Strategije nadomeščanja (Replacement Policies)**

Ko pride do zgrešitve in je nabor poln, kateri blok naj se izrine, da se naredi prostor za novi blok?

*   **LRU (Least Recently Used):** Nadomesti blok, ki je bil najdlje časa neuporabljen.
    *   **Prednosti:** Teoretično najbolj učinkovit, saj najbolje izkorišča časovno lokalnost.
    *   **Slabosti:** Zelo kompleksen za implementacijo (zahteva sledenje času dostopa za vsak blok v naboru).
*   **FIFO (First-In, First-Out):** Nadomesti blok, ki je bil najdlje v predpomnilniku.
    *   **Prednosti:** Enostaven za implementacijo (uporaba vrste).
    *   **Slabosti:** Ne upošteva časovne lokalnosti in se lahko odreže slabše kot LRU.
*   **Random (Naključno):** Naključno izbere blok za nadomeščanje.
    *   **Prednosti:** Najenostavnejši za implementacijo.
    *   **Slabosti:** Zmogljivost je nepredvidljiva, vendar v praksi pogosto presenetljivo dobra.

**6. Strategije zapisovanja (Write Policies)**

Kako se obravnavajo operacije zapisovanja (ko CPE spreminja podatke)?

*   **1. Zapisovanje skozi (Write-Through):**
    *   **Princip:** Vsak zapis v PP se **takoj in istočasno** zapiše tudi v glavno pomnilniško lokacijo.
    *   **Prednosti:** Enostavno upravljanje podatkovne konsistence (GP je vedno ažuren).
    *   **Slabosti:** Počasnejše operacije zapisovanja, saj CPE mora čakati na dokončanje zapisa v počasnejši GP. To lahko omeji zmogljivost. Uporablja se pri L1 PP-jih, kjer je konsistentnost kritična.
*   **2. Zapisovanje nazaj (Write-Back):**
    *   **Princip:** Zapis se izvede samo v PP. Podatek v PP se označi kot "umazan" (dirty bit = 1). Posodobitev v GP se izvede šele, ko se umaknjen blok izrine iz PP nazaj v glavno pomnilniško lokacijo.
    *   **Prednosti:** Veliko hitrejše operacije zapisovanja, saj ni treba čakati na GP. Če se blok večkrat spreminja, se zapis v GP izvede samo enkrat.
    *   **Slabosti:** Kompleksnejša implementacija (potreben "dirty bit" za sledenje spremembam). Zahteva mehanizem za zagotavljanje **koherence predpomnilnika** v večjedrnih sistemih, da vsi procesorji vidijo iste, ažurne podatke. To je najpogostejša strategija za L2 in L3 PP.

**7. Koherenca predpomnilnika (Cache Coherency)**

V večjedrnih sistemih lahko ima isti podatek več kopij (v L1 PP jedra A, v L1 PP jedra B, v L3 PP, v GP). Ko eno jedro spremeni podatek v svojem PP, morajo ostala jedra to vedeti, da ne dostopajo do zastarele kopije.

*   **Protokoli koherence:** Za reševanje tega problema se uporabljajo protokoli, kot je **MESI (Modified, Exclusive, Shared, Invalid)** ali njegov naslednik MOESI.
    *   Ti protokoli definirajo različna stanja, v katerih je lahko blok v PP (spremenjen, ekskluziven, deljen, neveljaven) in določajo, kako se predpomnilniški krmilniki odzivajo na operacije branja in zapisovanja (npr. s pomočjo "snoopinga" - prisluškovanja po pomnilniškem vodilu).

**8. Metrike zmogljivosti (Performance Metrics)**

*   **Stopnja zadetkov (Hit Rate):** % dostopov do pomnilnika, ki se najdejo v PP. Višja je, boljše je.
*   **Stopnja zgrešitev (Miss Rate):** % dostopov, ki niso najdeni v PP (1 - Hit Rate). Nižja je, boljše je.
*   **Cena zgrešitve (Miss Penalty):** Čas (v taktih procesorja), ki je potreben za pridobitev bloka iz naslednje nižje ravni pomnilniške hierarhije po zgrešitvi.
*   **Povprečni čas dostopa do pomnilnika (AMAT - Average Memory Access Time):**
    `AMAT = Hit_Time + (Miss_Rate * Miss_Penalty)`
    (Hit_Time je čas za dostop do PP ob zadetku). Cilj je seveda zmanjšati AMAT.

---

Upam, da ta poglobljena razlaga ponuja bolj tehničen vpogled v kompleksnost in sofisticiranost delovanja predpomnilnikov. So temelj sodobne računalniške arhitekture.