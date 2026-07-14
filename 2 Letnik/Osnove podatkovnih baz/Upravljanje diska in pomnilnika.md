

Sistem za upravljanje podatkovnih baz (SUPB) je sestavljen iz različnih elementov, ki skrbijo za abstrakcijo podatkov od fizične shrambe do logičnega pogleda.

Potek delovanja - najprej pridobimo nek ukaz - iz aplikacije ali konzole, potem preverimo ukaz in ugotovimo najhitrejši način izvajanja (sintaktični analizator, optimizator, izvajalec), za pretok podatkov poskrbijo **upravljalec medpomnilnika** in **upravljalec prostora na disku**, zraven pa še modula za nadzor sočasnoti in upravljalec obnove podatkov še poskrbita da več uporabnikov ne spremnija podatkov hkrati ali pa da se podatki ne izgubijo ob sesutju.


**Upravljalec z diskom** neposredno komunicira s strojno opremo oz. OS-om. Njegova naloga je **abstrakcija**.

Upravljalec deluje s fiksno pomnilniško enoto ki ji rečemo **stran**. Stran lahko vsebuje več zapisov in je analogna enemu bloku na disku.

Osnovne operacije s katerimi dela so dodeljevanje in sproščanje prostora na disku ter branje in pisanje podatkov.
Za zapis novih podatkov moramo vedeti kateri bloki so zasedeni in kateri prosti - to lahko storimo na dva načina

**Vzdrževanje seznama prostih blokov** - to je verižni seznam kjer vsak prosti blok vsebuje kazalec a naslednji prosti blok. Sistem mora poznati le lokacijo prvega bloka od kjer lahko posodablja kazalec preko njegovega kazalca.

**Vzdrževanje bitne mape** - to je tabela bitov kjer vsak bit ustreza enemu bloku na disku - bitne mape omgočajo **hitro iskanje zaporednih prostih blokov** - slabost je dolgo iskanje prostih mest pri zelo zasedenih diskih in zavzame fiksno količino prostora.

Ponavadi SUPB ustvari eno ali več velikih datotek ki vsebujejo celoten SUPB kjer potem upravlja samo z "notranjim" prostorom teh datotek - analogno temu da ustvari svoj datotečni sistem.

Visokozmogljivi sistemi včasih obidejo datotečni sistem in pišejo direktno na disk - pospeši in omogoči prenos med različnimi platformami - znebi se tudi dvojnega predpomennja saj SUPB kot OS shranita podatke v predpomnilnik.

***

Za nalaganje strani iz diska je odgovoren **upravljalec medpomnilnika**.

Baza je razdeljena na strani, v RAM-u pa se vzpostavi buffer pool sestavljen iz okvirjev, kjer je vsak okvir fiksne velikosti in lahko sprejme natanko eno stran z diska.

**Proces branja** - ko uporabnik izvede ukaz SELECT, SUPB ugotovi, na kateri strani se nahaja iskani podatek (npr. zaposleni s številko 10002). Upravljavec preveri, ali je ta stran že v medpomnilniku. Če je ni, jo mora prenesti z diska v enega izmed prostih okvirjev v RAM-u.

Za vsak okvir sta določeni **pin count** in **dirty bit**

Pin count šteje koliko procesov ali uporabnikov aktivno uporalbja to stran, in dokler to števil ni nič je ne sme odstraniti iz pomnilnika.

Dirty bit je flag ki upravljalcu pove da verzija na disku ni več enaka tisti v RAM-u in da mora stran ob odstranitvi iz pomnilnika to spremembo zapisati nazaj na disk.

Branje bi delovalo tako da najdemo stran, povečamo pin count na 1, in ker gre za branje ostane dirty pin false.
Pri posodabljanju povečamo pin count na 1 in ker se vsebina spremeni drity pin na true.

Proces iskanja določene strani s podatki se izvede v naslednjem vrstnem redu:
1. Najprej pogledamo prisotnost strani v RAM-u, če je stran tam rečemo ja in povečamo njen pin count. Če ni jo je treba prenesti z diska
2. Če je medpomnlnik poln mora sistem izbrati žrtev ki jo bo odstranil. Tukaj nastopi **strategija zamenjave**.
3. Pogleda se dirty bit izbrane strani, ob čimer jo moramo zapisati nazaj na disk - je bila spremenjena - če je true, drugače pa jo zavžremo.
4. Nova stran se naloži v sproščen okvir njen pin count, se nastavi na 1, njen naslov vpomnilniku pa se preda transakciji ki jo je zahtevala.

Pri izbiranju žrtve sistem lahko za zamenjavo izbere le tiste strani ki imajo pin count nič. Če so vsi okvirji zasedeni, kjer je pin count vseh večji od 0 potem moramo počakati dokler nekdo drug ne sprosti svoje strani. Če čakanje traja predolgo se lahko transakcija razveljavi, da se prepreči blokada sistema.

Zaradi problemov kjer je pin count večji od dva in lahko nek proces bere podatke ki so bili spremenjeni kot posledica drugega - **konfliktne spremembe**.

Za preprečevanje se poslužujemo **deljenega zaklepanja**, ki se uporablja za branje. več transakcij lahko hkrati drži deljen zaklep na isti strani - vsi lahko berejo a nihče ne sme pisati.

Lahko pa uporabimo **ekskluzivno zaklepanje** ki se uporablja za pisanje, kjer če transakcija dobi ekskluzivni zaklep nobena druga ne more niti brati niti pisati.

Za **strategijo zamenjave** si lahko izebremo **LRU - last recently used**ali **clock replacement**.

Pri LRU upravljalec vzdržuje linked list kazalcev na okvirje ki imajo pin count na 0. Takoj ko se nek okvir spusti na 0 se kazalec na okvir doda na konec vrste. Ko potrebujemo prostor za novo stran pogledamo na začetek vrste ki je najdlje v stanju mirovanja.
Čeprav je LRU logičen je v praksi potreten saj ob vsakem dostopu do strani posodabljamo vrsto kar ob tisoč prošnjah na sekundo upočasni sistem.

Clock replacement je pametna in hitra aproksimacija LRU ki ne zahteva seznamov. Vsak okvir ima flag r. Ko se pin count zmanjša na 0 sistem nastavi R na 1, to je "druga priložnost". Ko iščemo prostor za novo stran se kzalec pomika po krogu okvirjev - če je p > 0 kazalec preskoči okvir, če je p = 0 in r = 1 sistem okvirju nastavi r na 0 in kazalec pomakne naprej. Če je p 0 in r 0 potem ga zbrišemo. Kazalec se tako premakne le takrat ko dejansko poterbujemo prostor


---

#### **5. Algoritmi zamenjave strani: Izbira žrtve**

Ko je medpomnilnik poln in je potrebna nova stran, algoritem določi, katero obstoječo stran (`pin_count = 0`) odstraniti. Izbira vpliva na število I/O operacij.

*   **LRU (Least Recently Used):**
    *   Temelji na predpostavki, da bo nedavno uporabljena stran verjetneje potrebna ponovno.
    *   Vzdržuje **vrsto kazalcev** le na okvirje s `pin_count = 0`.
    *   Ko stran postane kandidat (`pin_count = 0`), se doda na **konec vrste**.
    *   Za zamenjavo se vedno izbere stran na **začetku vrste** (najdlje neuporabljena).
    *   **Pomanjkljivost:** Zahteva stalno posodabljanje vrste, kar je računsko zahtevno.

*   **Strategija urnega kazalca (Clock – "druga priložnost"):**
    *   Učinkovitejša aproksimacija LRU. Vsak okvir ima poleg `pin_count` in `dirty` bita še **referenčni bit (R)**.
    *   **Ključni dogodek:** Ko `pin_count` strani pade na 0, se **avtomatsko postavi bit R = 1**.
    *   **Delovanje algoritma:** Kazalec kroži po okvirjih.
        1.  Če najde stran z `P > 0`, jo preskoči (je v uporabi).
        2.  Če najde stran z `P = 0` in `R = 1`, ji da "drugo priložnost": **postavi `R = 0`** in gre naprej.
        3.  Če najde stran z **`P = 0` in `R = 0`**, jo izbere za zamenjavo.
    *   Ta pristop je računsko enostaven in učinkovito razlikuje med svežimi in zastarelimi stranmi.

Čeprav imajo operacijski sistemi lastne mehanizme za navidezni pomnilnik, jih večina SUPB ne uporablja. Namesto tega implementirajo lastne, specializirane upravljalce.

1.  **Vnaprejšnje branje (Prefetching):** SUPB pozna semantiko podatkov. Ob zaporednem branju tabele lahko **vnaprej naloži naslednjih N strani** v medpomnilnik, še preden jih poizvedba eksplicitno zahteva. OS te logične povezave ne vidi.
2.  **Nadzor nad zapisovanjem (Write Control):** Za zagotavljanje trajnosti (ACID) mora SUPB natančno določati **vrstni red in trenutek** pisanja "umazanih" strani na disk. Generični OS algoritmi za izrinjanje strani tega ne upoštevajo in bi lahko ogrozili možnost obnove po okvari.
3.  **Učinkovitost:** Lastna implementacija zmanjšuje število preklopov med uporabniškim in jedrnim načinom ter omogoča boljši nadzor nad sistemskimi viri.
