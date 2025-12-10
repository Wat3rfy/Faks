
Na podlagi pregleda priloženih izpitnih pol (kolokvijev) za predmet **Analiza 3 (IŠRM)** iz let 2017, 2018, 2019, 2021 in 2022, lahko jasno identificiramo vzorce in tipe nalog, ki se redno pojavljajo.

Struktura kolokvija je zelo predvidljiva in je skoraj vedno sestavljena iz **4 ali 5 nalog**, ki pokrivajo naslednja štiri glavna področja:

### 1. Integrali s parametrom (Integrals with a Parameter)
To je skoraj vedno **1. ali 2. naloga**. Od študenta se pričakuje razumevanje odvajanja pod integralskim znakom.

*   **Tipične naloge:**
    *   **Odvajanje integrala:** Uporaba Leibnizovega pravila za odvajanje integrala po parametru $F(a) = \int f(x, a) dx$.
    *   **Spremenljive meje:** Pozor na primere, kjer so tudi meje integrala odvisne od parametra (npr. naloga iz leta 2017: $F(t) = \int_{t^2}^{2t^2} \dots$). Tu moraš uporabiti razširjeno Leibnizovo formulo.
    *   **Določanje definicijskega območja in konvergence:** Za katere $a$ integral konvergira? (npr. leto 2021, 2022).
    *   **Rekurzivne zveze:** Iskanje zveze med $F(a)$ in $F(a+2)$ (npr. leto 2021, uporaba per-partes).
    *   **Konkretni izračun:** Pogosto moraš najprej izračunati odvod $F'(a)$, da potem s pomočjo tega določiš vrednost originalnega integrala (npr. leto 2019, 2022).

### 2. Posplošeni integrali in funkcija Gamma/Beta
To se pogosto pojavlja kot samostojna naloga ali kot podvprašanje pri integralih s parametrom.

*   **Tipične naloge:**
    *   **Uporaba funkcije $\Gamma$ in $B$:** Integrali, ki vsebujejo $(\ln x)^n$ ali $e^{-x}$ in korene, se pogosto rešijo s prevedbo na Gamma funkcijo (npr. leto 2017: $\int_0^1 (\ln x)^4 \sqrt{-\ln x} dx$).
    *   **Nepravi integrali:** Računanje integralov z neskončnimi mejami ali singularnostmi (npr. leto 2018, 2019).

### 3. Dvojni integrali (Double Integrals)
To je standardna **3. ali 4. naloga**. Poudarek je na geometrijski predstavitev in zamenjavi vrstnega reda integracije.

*   **Tipične naloge:**
    *   **Zamenjava vrstnega reda integracije:** Dobiš integral $\int dy \int f(x,y) dx$, naloga zahteva, da zapišeš $\int dx \int f(x,y) dy$. Za to je nujno **skiciranje območja $D$** (npr. leto 2018, 2022, 2021).
    *   **Prevedba na polne koordinate:** Če je območje krog ali del kroga.
    *   **Uvedba novih koordinat (Jacobijeva determinanta):**
        *   Naloge pogosto vključujejo območja, omejena s parabolami (npr. $y^2 = ax$, $y = ax^2$), kjer je smiselno vpeljati nove spremenljivke $u$ in $v$, da se meje poenostavijo (npr. leto 2018, 2019).
        *   Naloga z $x^4 + y^4 \le 1$ (leto 2019) namiguje na posplošene polarne koordinate.
    *   **Območja med funkcijami:** Območje med $y=\sin x$ in $y=\sin^2 x$ (leto 2021).

### 4. Trojni integrali (Triple Integrals)
To je običajno **zadnja naloga (4. ali 5.)**.

*   **Tipične naloge:**
    *   **Izračun volumna ali integrala po telesu:** Telo je pogosto omejeno s paraboloidi, stožci ali sferami.
    *   **Cilindrične koordinate:** Zelo pogoste, ko se pojavlja simetrija okoli osi $z$ (npr. $x^2+y^2$).
    *   **Sferne koordinate:** Če je telo krogla ali del krogle.
    *   **Primeri teles:**
        *   Piramida (leto 2022) - tu je treba paziti na meje v kartezičnih koordinatah.
        *   Telo med dvema paraboloidoma (leto 2018).
        *   Valj/Cilinder (leto 2021).

---

### Povzetek ključnih veščin za uspeh:

1.  **Leibnizovo pravilo:** Nauči se formule za odvajanje integrala po parametru (tudi z mejami, ki so funkcije parametra).
2.  **Skiciranje v ravnini:** Pri dvojnih integralih je ključno, da znaš narisati območje, ki ga omejujejo parabole, premice ali trigonometrične funkcije, da lahko pravilno določiš meje.
3.  **Zamenjava vrstnega reda:** Vedeti moraš, kako "razrezati" območje v drugo smer (vodoravno vs. navpično).
4.  **Nove koordinate:** Obvladati moraš izračun **Jacobijeve determinante** (Jacobiana) za prehod na polarne, cilindrične, sferne ali poljubne nove koordinate ($u, v$).
5.  **Funkcija Gamma:** Zapomni si definicijo $\Gamma(z) = \int_0^\infty t^{z-1}e^{-t}dt$ in osnovne lastnosti ($\Gamma(n) = (n-1)!$, $\Gamma(1/2) = \sqrt{\pi}$), saj se pogosto uporablja kot bližnjica.

Glede na analizirane stare izpite je strategija učenja za **Analizo 3 (smer IŠRM)** precej jasna, saj se tipi nalog ponavljajo. Da dosežeš čim boljšo oceno, ne rabiš le "reševati nalog", ampak moraš sistematično osvojiti štiri specifične koncepte.

Tukaj je optimiziran načrt učenja po korakih:

### 1. korak: Obnovi temelje (Predpriprava)
Preden se lotiš "pravih" nalog, moraš obvladati dvoje orodij, brez katerih na tem izpitu ne gre:
*   **Skiciranje v ravnini (2D):** Znati moraš hitro narisati krivulje, kot so $y=x^2$, $x=y^2$, $y=1/x$, krožnice in premice. Brez skice ne moreš določiti mej pri dvojnih integralih.
*   **Integracijske metode (Analiza 1/2):** Per-partes in substitucija morata teči gladko. Pri integralih s parametrom je pogosto treba na koncu izračunati preprost, a zoprn integral.

### 2. korak: Sistematičen napad na 4 tipe nalog
Uči se po sklopih, ki ustrezajo nalogam na kolokviju.

#### Sklop A: Integrali s parametrom (Vedno 1. naloga)
To je običajno "najlažja" pot do točk, če poznaš postopek.
*   **Nauči se formulo:** Leibnizovo pravilo za odvajanje pod integralom. **Pozor:** Nauči se razširjeno formulo, kjer so tudi meje ($a(t)$ in $b(t)$) odvisne od parametra (glej nalogo iz leta 2017).
    $$F'(t) = \int_{a(t)}^{b(t)} \frac{\partial f(x,t)}{\partial t} dx + f(b(t), t) \cdot b'(t) - f(a(t), t) \cdot a'(t)$$
*   **Postopek:**
    1.  Odvajaj funkcijo pod integralom po parametru $a$.
    2.  Izračunaj nov integral (ki je običajno lažji od prvotnega).
    3.  Rešitev integriraj nazaj po $a$, da dobiš $F(a) + C$.
    4.  Določi konstanto $C$ s "pametno točko" (npr. če je $a=0$, je integral morda 0).

#### Sklop B: Gamma in Beta funkcije (Pogosto zraven)
Če vidiš integral z $\ln(x)$, $e^{-x}$ in koreni, ne poskušaj klasične integracije.
*   **Na pamet:** Nauči se definicijo $\Gamma(z)$ in $B(x,y)$ ter zveze (npr. $\Gamma(1/2) = \sqrt{\pi}$, $\Gamma(n)=(n-1)!$).
*   **Trik:** Nauči se substitucij, ki integral "preoblikujejo" v Gamma funkcijo (npr. $t = -\ln x$ ali $t = x^2$).

#### Sklop C: Dvojni integrali & Zamenjava vrstnega reda
Tu največ študentov izgubi točke, ker ne narišejo slike.
*   **Zamenjava vrstnega reda:** Če imaš integral $\int_0^1 dy \int_{\sqrt{y}}^1 dx$, moraš narisati območje in ugotoviti, kako se meje spremenijo, če najprej integriraš po $y$.
*   **Nove koordinate (Jacobian):**
    *   Če je območje krog $\to$ Polarne koordinate ($J=r$).
    *   Če je območje med parabolama (npr. $y=ax^2$ in $y=bx^2$) $\to$ Vpelji novi spremenljivki $u$ in $v$, da postanejo meje konstante (npr. $u = y/x^2$). **Nauči se izračunati Jacobijevo determinanto za splošne primere!**

#### Sklop D: Trojni integrali (Volumni)
*   **Vizualizacija teles:** Znati si moraš predstavljati (ali narisati) stožec ($z^2 = x^2+y^2$), paraboloid ($z = x^2+y^2$) in sfero.
*   **Izbira koordinat:**
    *   Simetrija okoli osi Z (valji, paraboloidi) $\to$ **Cilindrične koordinate**.
    *   Krogle $\to$ **Sferne koordinate**.
*   **Simetrija:** Kot namiguje naloga iz leta 2022 – če je telo simetrično in funkcija liha, je integral 0. Če je soda, lahko računaš le po polovici in množiš z 2. To prihrani ogromno časa.

### 3. korak: Strategija reševanja ("Drill")
1.  **Vzemi priložene PDF-je.** Reši vsak kolokvij posebej, kot da pišeš zares (s štoparico).
2.  **Ne glej rešitev takoj.** Če se zatakneš, poglej samo *kateri tip koordinat* se uporabi, in poskusi naprej.
3.  **Pazi na "Utemelji":** Pri nalogah s parametrom ali konvergenco (npr. 2022, 2019) ne pozabi napisati stavka o zveznosti funkcije ali o tem, zakaj integral konvergira (npr. "funkcija je na intervalu omejena" ali primerjalni kriterij). To prinaša 5-10 točk!

### 4. Kje dobiti dodatne naloge?
*   Zbirka nalog **"Rešene naloge iz Analize 3"** (avtorji s FMF, npr. Globevnik, Vidav ali novejše zbirke asistentov). Išči poglavja: *Integrali s parametrom* in *Večkratni integrali*.
*   Spletna učilnica: Reši vse domače naloge, saj so kolokviji pogosto variacije teh nalog.

**Povzetek za super oceno:**
Najprej se nauči **Leibnizovo pravilo** (to je zastonj točka). Nato vadi **risanje območij** za dvojne integrale, saj je to ključ do pravilnih mej. Pri trojnih integralih pa samo natreniraj prehod na **cilindrične in sferne koordinate**. Srečno!