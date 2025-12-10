

# Arhitektura in organizacija računalniških sistemov

## 1. Zapis informacije in aritmetika

V računalniku se informacije shranjujejo kot **ukazi** in **operandi**. Ukazi (instructions) CPE-ju povedo, kaj naj naredi, operandi (operands) pa so podatki, na katerih se izvajajo te operacije. Operandi so lahko **numerični** ali **nenumerični**. Numerični operandi so števila, nenumerični pa so običajno znaki, besedila, slike, zvok ipd.

### 1.1 Zapis nenumeričnih operandov
Zgodnji računalniki so delali izključno z numeričnimi operandi, danes pa je nenumeričnih operandov veliko. Običajno so to **znaki** ali **nizi znakov** (strings). Vsak znak je predstavljen z določeno **abecedo**. Abeceda določa nabor znakov in njihovo preslikavo v binarno obliko (npr. številsko vrednost).

*   **Abeceda ASCII** (American Standard Code for Information Interchange, 1968):
    *   Je **7-bitna**, kar pomeni, da za vsak znak uporablja 7 bitov, in omogoča zapis 128 znakov ($2^7$ kombinacij).
    *   Od tega je 95 natisljivih znakov in 33 kontrolnih znakov. To so znaki, ki niso natisljivi, ampak imajo poseben pomen, npr. nova vrstica, tabulator, zvočni signal, začetek/konec prenosa.
    *   Primeri: 'A' je 1000001 (65), 'a' je 1100001 (97), '0' je 0110000 (48).
    *   Kontrolni znaki se uporabljajo za računalniške komunikacije in krmiljenje V/I naprav.
*   **Razširjena 'ASCII'** (8-bitna):
    *   Dodatnih 128 znakov, kar omogoča $2^8 = 256$ znakov.
    *   Primeri standardov so **ISO/IEC 8859**, vključno z ISO 8859-1 (Latin-1) za zahodnoevropske in ISO 8859-2 (Latin-2) za vzhodnoevropske črke.
*   **Koda BCD** (Binary Coded Decimal):
    *   **4-bitna binarna predstavitev desetiških cifer**. Vsaka desetiška cifra (0-9) se posebej zapiše s 4 binarnimi biti. Npr. število 12 v BCD ni 1100$_2$, temveč 0001$_2$ 0010$_2$.
    *   Spodnji 4 biti znakov za desetiške cifre v abecedah BCDIC, EBCDIC in ASCII ustrezajo njihovi dvojiški numerični vrednosti.
*   **Unicode**:
    *   Razvil ga je neprofitni konzorcij leta 1991.
    *   Uporablja abecede **UTF-8, UTF-16, UTF-32** (Unicode transformation format). To so različni načini kodiranja znakov Unicoda, ki se razlikujejo po številu bitov na znak in kompatibilnosti.
    *   **UTF-8**:
        *   Posamezen znak zavzame od 1 do 4 bajtov.
        *   Uporablja **kodiranje spremenljive dolžine** (variable length encoding), kar pomeni, da nekateri znaki zavzamejo manj bajtov (npr. angleški znaki), drugi pa več (npr. azijski znaki), kar prihrani prostor.
        *   Prvih 128 znakov je **enako kot ASCII**, kar zagotavlja združljivost.

### 1.2 Zapis numeričnih operandov v fiksni vejici
Numerični operandi se v računalniku shranjujejo na dva glavna načina: s **fiksno vejico** in s **plavajočo vejico**. Fiksna vejica pomeni, da je pozicija dvojiške vejice v številu fiksna (vedno na istem mestu), medtem ko plavajoča vejica omogoča, da se pozicija vejice spreminja glede na velikost števila.

#### 1.2.1 Pozicijska notacija
Števila se zapisujejo v **pozicijski notaciji**, kjer ima vsaka pozicija svojo težo. To se posploši na uteži oblike $r^i$, kjer je $r$ **baza** ali **radix** številskega sistema. Baza določa število različnih cifer (simbolov), ki jih lahko uporabimo v številskem sistemu (npr. 10 za desetiški, 2 za dvojiški, 16 za šestnajstiški). Vrednost števila $b_{n-1} \dots b_2 b_1 b_0 , b_{-1} b_{-2} \dots b_{-m}$ v bazi $r$ je dana z izrazom:
$$ V_b = \sum_{i=-m}^{n-1} b_i r^i $$
V računalnikih se najpogosteje uporablja **baza $r=2$ (dvojiški zapis)**.

#### 1.2.2 Dvojiški zapis števil v fiksni vejici
Pri dvojiškem zapisu je baza $r=2$, kjer so $b_i = 0$ ali $1$. Zapis v fiksni vejici ima bite razdeljene na **celi del** in **ulomek** (oznaka **Qn.m**), kjer $n$ predstavlja število bitov v celem delu in $m$ število bitov v ulomku. Q-format je standard za predstavitev fiksne vejice, kjer n pomeni število celih bitov (vključno z morebitnim predznakovnim bitom) in m število ulomkovnih bitov. Velikost celotnega števila je n+m bitov.
*   **Primer**: Pretvorba $110101,101_2$ v desetiško število:
    $110101,101_2 = 2^5 + 2^4 + 2^2 + 2^0 + 2^{-1} + 2^{-3} = 32 + 16 + 4 + 1 + 0,5 + 0,125 = 53,625_{10}$.

#### 1.2.3 Pretvorba med bazami
*   **Desetiška števila v bazo $r$**: Algoritem vključuje zaporedno deljenje celega dela z $r$ in množenje ulomka z $r$.
    *   **Primer**: $98_{10} = 142_8$.
    *   **Primer**: $27_{10} = 11011_2$.
    *   **Primer ulomkov**: $0,375_{10} = 0,011_2$.
*   **Napaka pri rezanju decimalk**: Kadar število $N$ odrežemo na $m$ mest desno od vejice, dobimo približek $N'$. Absolutna napaka $|N' - N|$ je $\le r^{-m}$. To se zgodi, kadar ima število v eni bazi neskončno število decimalnih mest, v drugi bazi pa ga je treba odrezati. Število mest $m$ za določeno maksimalno napako $E_{max}$ se izračuna kot $m \ge \log_r(1/E_{max})$.
*   **Pretvorba med poljubnima bazama**: Ponavadi se najprej pretvori v desetiško bazo, nato pa v želeno bazo.
*   **Sorodne baze**: Pretvorba je lažja, če sta bazi večkratnika istega števila (npr. 2, 4, 8, 16). Sorodne baze so baze, ki so potence druge baze (npr. 4, 8, 16 so potence baze 2). To omogoča direktno pretvorbo brez pretvarjanja v desetiško bazo.
    *   **Osmiška (oktalna) in šestnajstiška (heksadecimalna) baza** se pogosto uporabljata v računalništvu.
        *   V šestnajstiški bazi se poleg 0-9 uporabljajo tudi črke A-F (A=10, ..., F=15).
        *   Osmiška cifra predstavlja 3 bite, šestnajstiška pa 4 bite.
        *   **Primer**: $1110010101_2 = 1 \ 110 \ 010 \ 101_2 = 1625_8$.
        *   **Primer**: $1110010101_2 = 11 \ 1001 \ 0101_2 = 395_{16}$ (ali 0x395).

#### 1.2.4 Nepredznačena števila
Nepredznačena števila (unsigned numbers) so vedno pozitivna ali nič. Z $n$ biti lahko zapišemo nepredznačena števila od **0 do $2^n-1$**. Kadar rezultat operacije preseže ta obseg, se pojavi **prenos** (carry), kar pomeni, da rezultat ni pravilen na podanem številu števk. Prenos se pojavi, ko seštevanje dveh števil preseže maksimalno vrednost, ki jo lahko zapišemo z danim številom bitov, in se ustvari dodaten bit.
*   **Primer**: $101_2 + 100_2 = (1)001_2$ (prenos).

#### 1.2.5 Predznačena števila
Predznačena števila (signed numbers) omogočajo zapis pozitivnih in negativnih števil. Predznačena števila se lahko zapišejo na več načinov:
*   **1. Predznak-veličinski zapis (PV)**:
    *   Prvi bit ($b_{n-1}$) predstavlja **predznak** (0 za +, 1 za -), ostali pa **velikost** števila (absolutna vrednost števila).
    *   **Slabosti**: Predznak je treba obravnavati posebej; obstajata dve ničli (+0 in -0). Ni primeren za seštevanje/odštevanje, bolj za množenje/deljenje.
*   **2. Zapis z odmikom (PO)**:
    *   Odmik je običajno $2^{n-1}$. Odmik določa, katera binarna vrednost predstavlja ničlo. Vse vrednosti pod odmikom so negativne, nad odmikom pa pozitivne.
    *   **Slabosti**: Pri seštevanju je treba odmik odšteti, pri odštevanju pa prišteti.
*   **3. Eniški komplement (1'K)**:
    *   $b_{n-1}$ je predznak.
    *   Pozitivna števila (prvi bit 0) so enaka kot pri PV.
    *   Negativno število se dobi z **invertiranjem vseh bitov** pozitivnega števila. To pomeni, da se 0 spremeni v 1 in 1 v 0.
    *   **Prednost**: Predznaka ni treba obravnavati posebej.
    *   **Slabosti**: Dve ničli (-0, +0); pri prenosu z najvišjega mesta (End Around Carry - EAC) je treba na najnižjem mestu prišteti 1. Dodatni prenosni bit z najvišjega mesta se prišteje na najnižje mesto rezultata.
*   **4. Dvojiški komplement (2'K)**:
    *   **Najpogosteje uporabljan zapis**.
    *   Pozitivna števila se začnejo z 0, negativna z 1.
    *   Negativno število se dobi z invertiranjem vseh bitov pozitivnega števila (1'K) in prištevanjem 1. Npr. za 4-bitno število 3 (0011) je 1'K 1100, 2'K pa 1100 + 1 = 1101 (-3). To je ekvivalentno odštevanju od $2^n$. Za npr. $-3$ v 4-bitnem 2'K je $2^4 - 3 = 16 - 3 = 13_{10} = 1101_2$.
    *   **Bit prenosa pri 2'K se ignorira**. To poenostavi aritmetiko.
    *   **Prednosti**: Primeren za seštevanje/odštevanje; nima EAC; le ena predstavitev za ničlo; predznaka ni treba obravnavati posebej.
    *   Pri razširitvi števila na več bitov je potrebno **razširiti predznak** (sign extension). To pomeni, da se predznakovni bit kopira v nove, dodane bite, da se ohrani vrednost števila pri razširitvi na večjo bitno dolžino. Npr. 0011 (+3) postane 00000011, 1101 (-3) pa 11111101.
*   **Obseg števil v $n$-bitnem 2'K**: od $-2^{n-1}$ do $2^{n-1}-1$.
    *   **Preliv (overflow)**: Pojavi se, če je pravi rezultat operacije izven tega območja. Rezultat je napačen. Preliv se pojavi, kadar je pravi rezultat operacije izven območja predstavljivih števil, ki jih lahko zapišemo z danim številom bitov v 2'K. Preliv ni isto kot prenos.
    *   **Zaznavanje preliva**: Potreben pogoj je, da imata števili enak predznak, zadosten pa, da ima vsota drugačen predznak. Pogoj za preliv je $OF = x_{n-1}y_{n-1}\overline{s_{n-1}} \lor \overline{x_{n-1}}\overline{y_{n-1}}s_{n-1}$. Lahko se zapiše tudi kot $OF = c_{n-1} \oplus c_n$. Če sta prenosa na predzadnjem in zadnjem mestu različna (eden je 0, drugi je 1 ali obratno), pride do preliva.

### 1.3 Aritmetična vezja
*   **Polovični seštevalnik (Half Adder, HA)**: 
	* Sešteva 2 bita, izračuna 
	* **vsoto** ($s = a \oplus b$) $(\oplus := \text{xor})$
	* **prenos** ($c = a \land b$)
*   **Polni seštevalnik (Full Adder, FA)**: 
	* Sešteva 3 bite - 2 vhoda in prenos
	* izračuna vsoto in izhodni prenos
	* verižno seštevanje večbitnih števil
*   **Večbitni seštevalnik**:
    
	*   **Seštevalnik z razširjanjem prenosa (Ripple Carry Adder, RCA)**: Zaporedna vezava full adderjev, kjer je izhod prejšnjega vezan na vhod naslednjega. 
	* Glavna slabost je **zakasnitev**, ki narašča linearno s številom bitov. 
    
    <br>
	
	* **Seštevalnik z vnaprejšnjim prenosom (Carry-Lookahead Adder, CLA)**: 
	Hiter izračun vseh prenosov na osnovi vhodov, z dodatno logiko. Ta metoda izračuna vse prenose sočasno, kar bistveno zmanjša zakasnitev.
	CLA je **veliko hitrejši** od RCA, vendar zahteva **bistveno več logičnih vrat**, kar pomeni, da je dražji in bolj kompleksen za izdelavo.
*   **Seštevanje in odštevanje predznačenih števil v 2'K z enim vezjem**: 
	- **Odštevanje** se izvede kot prištevanje 2'K komplementa ($a - b = a + \overline{b} + 1$). 
		  
	- **Krmilni signal (M ali Add'/Sub):** Dodamo en bit, ki nadzoruje operacijo.
	    
	    - M = 0: Seštevanje
	        
	    - M = 1: Odštevanje
	        
	- **Vrata XOR kot krmiljen invertor:** Vrata XOR imajo priročno lastnost:
	    
	    - B XOR 0 = B (bit ostane nespremenjen)
	        
	    - B XOR 1 = B' (bit se invertira)
	        
	- **Zgradba:**
	    
	    1. Pred vsak vhod Bi seštevalnika postavimo vrata XOR.
	        
	    2. Na en vhod XOR vrat pripeljemo bit Bi, na drugega pa krmilni signal M.
	        
	    3. Tisti +1, ki ga potrebujemo za odštevanje, elegantno dodamo tako, da krmilni signal M priključimo na prvi vhodni prenos seštevalnika (Cin od full adderja).
	* Vezje deluje tako da pri $M = 0$ XOR vrata ne naredijo ničesr 
	  `B xor 0 = B` , vhodni prenos je 0, dobimo `A + B`, pri $M = 1$ XOR vrata invertirajo B `B xor 1 = B'`, vhodni prenos je 1, `A + B' + 1` kar je seštevanje v dvojiškem komplementu.
	* Carry bit ignoriramo, preliv pa se zgodi pri seštevanju istopredznačenih števil, kjer dobimo napako in upoštevamo če sta števili nasprotnega predznaka.
	* Preliv se lahko zgodi **samo pri seštevanju števil z enakim predznakom**.
	
	- **Pozitivno + Pozitivno:** Če je rezultat večji od največjega pozitivnega števila (+7), pride do preliva. Rezultat bo napačno izgledal kot negativno število.
	    
	- **Negativno + Negativno:** Če je rezultat manjši od najmanjšega negativnega števila (-8), pride do preliva. Rezultat bo napačno izgledal kot pozitivno število.
	    
	- **Pozitivno + Negativno:** Nikoli ne more priti do preliva, ker se rezultat po absolutni vrednosti vedno zmanjša ali ostane enak, torej bo vedno znotraj območja.
*   **Binarno množenje**: 
	Vključuje tvorbo delnih produktov in njihovo seštevanje. 
	Vsak delni produkt je pomnoženec (število A) pomnožen z enim bitom množitelja (števila B).
    *   **Metode**:
        *  **Pomikanje in seštevanje (Shift-and-add):** Poceni metoda, ki posnema ročni postopek. Uporablja en seštevalnik in registre. V vsakem koraku (ciklu ure) preveri en bit množitelja: če je 1, prišteje množenec k vmesnemu rezultatu, nato pa rezultat pomakne v desno. Počasno (za N-bitno število rabi N korakov), a varčno s prostorom na čipu.
        *  **Kombinacijski (matrični) množilnik:** Hiter, a drag način. Ustvari vse delne produkte naenkrat (z mrežo AND vrat) in jih sešteje z drevesom seštevalnikov. Rezultat je na voljo skoraj takoj (samo zakasnitev propagacije signala). Zahteva ogromno prostora na čipu
    * **Booth-ov algoritem:** Napreden algoritem, idealen za **predznačena števila v 2'K**. Namesto da gleda vsak bit posebej, gleda pare bitov in zmanjša število operacij. Če naleti na dolgo zaporedje enic (npr. 011110), namesto štirih seštevanj naredi samo eno odštevanje (na začetku niza) in eno seštevanje (na koncu niza). 
      Vsako zaporedje enic v binarnem številu, na primer 011110, lahko matematično zapišemo kot razliko dveh števil:  
     $$ 011110 = 100000 - 000010  $$
      $$(30 = 32 - 2)$$
	
	- Boothov algoritem izkorišča točno to:

*   **Binarno deljenje**: Dva osnovna načina sta zaporedje odštevanj in pomikov ter matrični delilnik.

### 1.4 Zapis števil v plavajoči vejici
Obseg števil v fiksni vejici je premajhen za določene probleme. Uporablja se **znanstvena notacija**,  

$$m \times r^e$$ 

(npr. $3,4 \times 10^{38}$), kjer je $m$ **mantisa**, $r$ **baza** (običajno 2), in $e$ **eksponent**. Vejica "plava" vzdolž mantise, od tod ime **plavajoča vejica**.
*   **Normiranje mantise**: 
  Da se izognemo večkratnim zapisom istega števila, 
  (12 × 10⁰, 1,2 × 10¹, 0,12 × 10²) sledimo pravilu da se zapis začne z eno števko različno od 0 nato pa vejica.
  V dvojiškem je to še enostavnejše ker je edina števka različna od 0, 1. 
  Mantisa se **normira**, tako da je njen prvi bit 1 (implicitni normalni bit). S tem se zagotovi edinstvena predstavitev vsakega števila in poveča natančnost. To pomeni, da se ta '1' ne shrani v mantiso, saj je vedno prisotna, kar prihrani en bit za natančnost. 
  Zelo majhna števila, ki se ne morejo predstaviti v normirani obliki, so **denormirana števila**. Uporabljajo se za predstavitev števil blizu ničle, ki so premajhna za normirano obliko, s čimer se ohrani natančnost in prepreči 'izguba' ničle (gradual underflow).
  Pri tem lahko pride do **podliva (underflow)**. Podliv se zgodi, ko je rezultat operacije premajhen, da bi ga lahko predstavili, razen kot ničlo.
*   **Eksponent** je običajno predstavljen v **predstavitvi z odmikom**. 
  Služi za enostavno primerjavo eksponentov, saj se ni treba ukvarjati z  2'K.
  Torej da dobimo pravo vrednost eksponenta moramo odšteti odmik. Če hočemo shraniti dejanski eksponent mu prištejemo odmik.
  Odmik naj bi določal razpon števil.
*   **Standard IEEE 754** (1985, 2008, 2019):
    *   Dva osnovna formata: **enojna natančnost (single precision)** s 32 biti in **dvojna natančnost (double precision)** s 64 biti.



#### 1.4.1 Enojna natančnost (32 bitov)
*   **Bit predznaka S** (0: +, 1: -).
*   **8-bitni eksponent E** z odmikom 127 ($e = E - 127$).
*   **23-bitna mantisa m** (kar pomeni približno 7-mestno desetiško natančnost).
* `| S | EEEEEEEE | MMMMMMMMMMMMMMMMMMMMMMM |`
*   Normirana vrednost je $(-1)^S \cdot 1,m \cdot 2^{E-127}$.
*   Obseg: $\pm 1,18 \times 10^{-38}$ do $\pm 3,40 \times 10^{38}$. Velikost najvišjega in najnižjega števila, ki ga lahko predstavimo.

#### 1.4.2 Dvojna natančnost (64 bitov)
*   **Bit predznaka S** (0: +, 1: -).
*   **11-bitni eksponent E** z odmikom 1023 ($e = E - 1023$).
*   **52-bitna mantisa m** (kar pomeni približno 16-mestno desetiško natančnost).
*   Normirana vrednost je $(-1)^S \cdot 1,m \cdot 2^{E-1023}$.
*   Obseg: $\pm 2,22 \times 10^{-308}$ do $\pm 1,80 \times 10^{308}$.

#### 1.4.3 Posebna števila

- **Če je eksponent = 000...0 (same ničle):**
    - **Ničla (0):** Če je tudi mantisa enaka 0. Obstajata +0 in -0, kar je včasih uporabno (npr. pri računanju limit).
    - **Denormirana števila:** Če mantisa ni enaka 0. To so **izjemno majhna števila**, ki so tako blizu ničle, da jih ni več mogoče normirati (ker bi bil eksponent premajhen). Takrat implicitni bit ni več 1, ampak 0. To omogoča "postopno zmanjševanje" proti ničli (**gradual underflow**) in prepreči, da bi rezultat, ki je zelo majhen, a ne enak nič, kar naenkrat postal nič.
*   **Neskončnosti ($\pm \infty$)**: Predstavljajo se, ko so vsi biti E enice in mantisa $m=0$. Pojavijo se pri rezultatih, ki so preveliki (npr. $1/0$).
*   **NaN (Not a Number)**: Predstavljajo se, ko so vsi biti E enice in mantisa $m \ne 0$. Pojavijo se kot rezultat nedefiniranih operacij (npr. $0 \times \infty$, $0/0$, $\infty - \infty$, kvadratni koren negativnega števila).

Kljub temu, da so biti eksponenta vsi nič, se dejanski eksponent (za izračun vrednosti) še vedno interpretira kot **najmanjši možen eksponent normaliziranih števil**.

### 1.5 Aritmetika v plavajoči vejici

*   **Zaokroževanje**: 
  Standard IEEE 754 določa zaokroževanje na najbližje predstavljivo število, pri čemer se vrednosti, ki so enako oddaljene od dveh najbližjih števil, zaokrožijo k sodemu številu. 
  Pri računanju se mantisa podaljša z **varovalnim bitom (guard bit)**, **zaokroževalnim bitom (round bit)** in **lepljivim bitom (sticky bit)** za natančnejše zaokroževanje.  Lepljivi bit postane 1 če je katerikoli bit po njem 1.
  Če je GRS večji od ene polovice, zaokroži navzgor, če je odrezani del manjši od polovice zaokroži navzdol, če je točno polovica, zaokroži na sodo oz. spremeni zadnji bit na 0.
*   **Seštevanje (in odštevanje)**:
    1.  Eksponenta se izenačita
	- Poiščemo število z **večjim eksponentom** in ga obdržimo.
	- Število z **manjšim eksponentom** prilagodimo. Njegovo mantiso pomikamo v desno, za vsak premik pa povečamo njegov eksponent za 1, dokler se eksponenta ne izenačita.
    2.  Mantisi se seštejeta/odštejeta.
    3.  Po potrebi se normira rezultat.
    4.  Mantisa se zaokroži.
*   **Množenje**:
    1.  Eksponenta se seštejeta.
    2.  Mantisi se zmnožita (v fiksni vejici, vključno z implicitnimi enicami).
    3.  Predznak produkta je XOR obeh predznakov.
    4.  Po potrebi se normira rezultat.
*   **Deljenje**: 
  1. Odštevanje eksponentov
  2. Deljenje mantis
  3. Normalizacija in zaokroževanje 
*   **Težave pri uporabi plavajoče vejice**: 
  Lahko pride do **izgube natančnosti** zaradi omejene bitne dolžine, kar lahko vodi do napačnih rezultatov pri kompleksnih izračunih (npr. izračun variance). Izguba natančnosti se pojavi, ko se številke zmanjšajo in se prištevajo k večjim, kar povzroči, da se manjše vrednosti izgubijo (npr. izračun variance, kjer se odštevajo podobna velika števila, kar lahko povzroči veliko relativno napako).

## 2. Ukazi RISC-V in njihova obravnava

**Ukazna arhitektura (Instruction Set Architecture, ISA)** natančno definira vse ukaze procesorja, ne pa tudi njihove implementacije. ISA je abstrakcija, ki definira funkcionalnost procesorja (npr. kakšne ukaze pozna, kako so podatki organizirani), ne pa tudi, kako je to implementirano na strojni ravni.

### 2.1 RISC-V arhitektura
**RISC-V** je odprta RISC arhitektura, prvotno razvita za raziskave in poučevanje, ki postaja standard za industrijske implementacije. To pomeni, da je njena specifikacija javno dostopna in jo lahko kdorkoli uporablja in razvija brez licenciranja. Je dejansko družina ISA-jev:
*   **RV32I**: Celoštevilska 32-bitna (XLEN=32).
*   **RV64I**: Celoštevilska 64-bitna.
*   **RV128I**: Celoštevilska 128-bitna.
*   **RV32E**: Za majhne mikrokrmilnike (Embedded).
*   **Razširitve (extensions)**: M (množenje/deljenje), F (plavajoča vejica, enojna natančnost), D (plavajoča vejica, dvojna natančnost), A (atomski ukazi).

#### 2.1.1 Lastnosti RISC-V
*   **Pomnilniška beseda**: 8-bitna. Najmanjša naslovljiva enota pomnilnika.
*   **Pomnilniški naslov**: 32-bitni.
*   **Registri CPE**: 32 32-bitnih **splošnonamenskih registrov** ($x0, \dots, x31$). **Vsebina x0 je vedno 0** (pisanje vanj se ne zgodi). To je koristno za operacije, ki potrebujejo konstantno ničlo, ali za 'odmetavanje' rezultatov.
*   **Število eksplicitnih operandov**: Vsi ALE (Aritmetično-logična enota) ukazi imajo 3 eksplicitne operande. Operandi, ki so neposredno navedeni v ukazu.
    *   **Tip R**: Dva izvorna registra ($rs1, rs2$) in en ciljni register ($rd$).
    *   **Tip I**: En izvorni register ($rs1$), 12-bitni takojšnji (immediate) operand ($imm$) in en ciljni register ($rd$).
*   **Lokacija operandov in načini naslavljanja**:
    *   **Registrsko-registrski** (load/store) računalnik. Zasnova, kjer se vse aritmetično-logične operacije izvajajo samo na podatkih, ki so shranjeni v registrih. Podatki med registri in pomnilnikom se prenašajo izključno z ukazoma 'load' in 'store'.
    *   Pomnilniški operandi nastopajo **samo v ukazih load in store**.
    *   ALE ukazi imajo 2 operanda v registrih (tretji je lahko v registru ali takojšen).
    *   Dostop do pomnilnika le z load in store.
    *   Pomnilniški operandi so lahko 8-, 16- ali 32-bitni (bajt, polbeseda, beseda).
    *   **Little-endian** pravilo shranjevanja. To pomeni, da se najlažji (najmanj pomemben) bajt večbajtnega števila shrani na najnižji pomnilniški naslov.
    *   **Poravnani (aligned)** operandi: 16-bitni na naslovu deljivem z 2, 32-bitni na naslovu deljivem s 4. Pravilo, ki določa, da se večbajtni podatki morajo začeti na naslovu, ki je deljiv z njihovo velikostjo v bajtih. To omogoča hitrejši dostop do pomnilnika.
    *   Vse ALE operacije so 32-bitne. Krajši operandi (8, 16-bitni) se pri load pretvorijo v 32-bitne z **razširitvijo ničle** (za nepredznačene) ali **razširitvijo predznaka** (za predznačene). Razširitev ničle pomeni, da se manj bitno število dopolni z ničlami na levem delu do želene bitne dolžine. Razširitev predznaka pa pomeni, da se manj bitno število dopolni s kopijo predznakovnega bita na levem delu do želene bitne dolžine.

#### 2.1.2 Format ukazov RV32I
Vsi ukazi so **32-bitni in poravnani**. Ima 4 osnovne formate (R, I, S, U) in 2 dodatna (B, J). Format ukaza pove, kako so biti ukaza razdeljeni na operacijsko kodo in operande (število polj, velikost, pomen).
*   Število ukazov RV32I je 40. **Nima ukazov za množenje, deljenje ali plavajočo vejico** (te so v razširitvah M, F, D).

### 2.2 Vrste ukazov
Ukaze RISC-V delimo v več skupin:
1.  **Ukazi za prenos podatkov (load, store)**:
    *   Prenos operandov med registri in pomnilnikom.
    *   Uporabljajo format I z baznim naslavljanjem (bazni register je $rs1$). Bazno naslavljanje: naslov se izračuna kot seštevek vrednosti baznega registra (rs1) in takojšnjega odmika (imm).
    *   **Load word (lw)**: $rd \leftarrow_{32} M[rs1 + se(imm)]$.
    *   **Load byte (lb)**: $rd \leftarrow_{raz} M[rs1 + se(imm)]_7, rd \leftarrow_{8} M[rs1 + se(imm)]_{7..0}$. $se(imm)$ pomeni razširitev predznaka.
    *   **Load byte unsigned (lbu)**: $rd \leftarrow_{raz} 0, rd \leftarrow_{8} M[rs1 + se(imm)]_{7..0}$.
    *   Podobno za **halfword** (lh, lhu).
    *   Pri ukazih store (sb, sh, sw) je $rd$ izvorni register.
2.  **ALE ukazi** (aritmetične in logične operacije):
    *   **Aritmetične operacije**: ADD, ADDI (Add Immediate), SUB, LUI (Load Upper Immediate), AUIPC (Add Upper Immediate to PC).
    *   **Logične bitne operacije**: AND, ANDI, OR, ORI, XOR, XORI. Logične operacije delujejo po istoležnih bitih (bitwise). Uporabljajo se za nastavljanje, brisanje in branje posameznih bitov.
        *   NOT operacije RISC-V nima direktno, lahko pa se simulira z XOR z enicami (npr. `XORI rd, rs1, -1`, kjer je -1 v 2'K predstavljen z vsemi enicami). Pomanjkanje direktnega NOT ukaza je značilno za nekatere RISC arhitekture, kjer se zmanjšuje število kompleksnih ukazov.
    *   **Pomiki (shift)**: SLL (Shift Left Logical), SLLI, SRL (Shift Right Logical), SRLI, SRA (Shift Right Arithmetic), SRAI.
        *   Levi pomik (za $n$ mest) predstavlja množenje z $2^n$.
        *   Desni pomik (za $n$ mest) je deljenje z $2^n$ (pri celih številih).
        *   Aritmetični pomik ohrani predznak (v vstavi predznakovni bit v izpraznjena mesta).
        *   Pomiki uporabljajo **pomikalnik (barrel shifter)**, ki izvede poljuben pomik v eni urini periodi. Digitalno vezje, ki lahko izvede poljuben pomik (za poljubno število mest) v eni sami urini periodi, kar je ključno za hitre pomike.
    *   **Ukazi za primerjavo oz. set operacije**: SLT (Set if Less Than), SLTI, SLTU, SLTIU. Uporabljajo se predvsem v pogojnih stavkih ali za pripravo vrednosti za nadaljnje operacije.
        *   Če je pogoj izpolnjen, se v $rd$ zapiše 1, sicer 0.
    *   **LUI (Load Upper Immediate)**: 20-bitno konstanto naloži v zgornjih 20 bitov registra, spodnjih 12 bitov pa je 0. Uporablja se za nalaganje 32-bitnih konstant v register v dveh korakih (LUI + ADDI/ORI), saj takojšnji operand običajno ni dovolj dolg za celotno konstanto.
    *   **AUIPC (Add Upper Immediate to PC)**: Naloži 20-bitno konstanto v zgornjih 20 bitov registra in ji prišteje vrednost programskega števca (PC). Omogoča PC-relativno naslavljanje za globalne podatke in bližnje skoke.
3.  **Kontrolni ukazi** (skoki): Omogočajo spremembo vrstnega reda izvajanja ukazov. Spreminjajo vrstni red izvajanja programa.
    *   **Brezpogojni skok**:
        *   **JAL (Jump and Link)**: $rd \leftarrow PC+4, PC \leftarrow target$. Shranjuje povratni naslov (naslov naslednjega ukaza po klicu).
        *   **JALR (Jump and Link Register)**: $rd \leftarrow PC+4, PC \leftarrow (rs1 + se(imm12)) \land (-2)$. Poravna naslov na besedno mejo (najnižji bit je nastavljen na 0). Omogoča skoke na zelo oddaljene procedure, skočni naslov se lahko spreminja.
    *   **Pogojni skoki (format B)**: Uporabljajo PC-relativno naslavljanje, kar pomeni, da je ciljni naslov izražen kot odmik od trenutne vrednosti programskega števca (PC).
        *   **BEQ** (Branch if Equal to), **BNE** (Branch if Not Equal to).
        *   **BLT, BLTU** (Branch if Less Than (Unsigned)).
        *   **BGE, BGEU** (Branch if Greater or Equal (Unsigned)).
4.  **Sistemski ukazi**: Spreminjajo parametre delovanja računalnika in nadzorujejo njegovo delovanje (npr. omogočanje prekinitev, način delovanja PP, prehod na privilegiran nivo).

    *   **CSR ukazi** (CSRRW, CSRRS, CSRRC, CSRRWI, CSRRSI, CSRRCI): Dostop do registrov CSR (Control and Status Register).
    *   **FENCE**: Pomnilniška pregrada, zagotavlja dokončanje prejšnjih pomnilniških dostopov.
    *   **FENCE.I**: Pregrada za ukaze, zagotavlja dokončanje prejšnjih pisanj pred branjem ukazov.
    *   **ECALL (environment call)**: Implementacija sistemskih klicev (omogočajo dostop do jedra OS in strojne opreme).
    *   **EBREAK**: Vrne kontrolo razhroščevalniku.

### 2.3 Prevajanje in zbirni jezik
Prevajalnik pretvori programe iz višjega jezika (npr. C) v zbirni ali strojni jezik.
*   **ABI (Application Binary Interface)**: Vmesnik med programom v strojni kodi, knjižnicami in OS. Definira tudi, kako se prenašajo argumenti in vračajo rezultati funkcij, kako se upravlja s skladom ter uporaba registrov, da se zagotovi pravilno delovanje programa. Določa strukturo registrov, organizacijo sklada, pomnilniške dostope, podatkovne tipe in dogovor o klicih podprogramov.
*   **Direktive zbirnika**: Ukazi za zbirnik (assembler), ki vplivajo na proces prevajanja in generiranja strojne kode, niso pa sami po sebi procesorski ukazi (npr. `.data`, `.text`, `.byte`, `.word`, `.align`).
*   **Psevdo-ukazi**: Niso dejanski ukazi procesorja, ampak jih zbirnik prevede v dejanske ukaze. Ukazi, ki so bolj priročni za programerja v zbirnem jeziku, vendar jih zbirnik samodejno razširi v enega ali več dejanskih strojnih ukazov procesorja. (npr. `nop`, `la` (load address), `li` (load immediate), `mv`, `not`, `neg`).
    *   `nop`: No Operation – ukaz, ki ne stori ničesar, uporablja se za časovne zamike ali poravnavo.
    *   `la` (load address) je koristen za nalaganje poljubnih naslovov v register, saj 12-bitni takojšnji operand ne zadostuje za vse naslove. Prevede se v `auipc` + `addi`.
    *   `li` (load immediate): naloži takojšnjo konstanto v register.
    *   `mv`: Move – premakne vsebino enega registra v drugega (pravzaprav je to ADDI z ničlo).
    *   `not`: Invertira vse bite v registru.
    *   `neg`: Spremeni predznak števila (pravzaprav je to SUB od ničle).
*   **Uporaba zbirnega jezika**: Za zagon programe (BIOS), dele jedra OS, specifične optimizacije, razhroščevanje (disassembly), vzvratno inženirstvo ali kot učni pripomoček.

## 3. Splošne lastnosti ukazov

Lastnosti ukazov lahko opišemo v petih dimenzijah:
1.  **Način shranjevanja operandov v CPE**: Nanaša se na arhitekturo procesorja glede na to, kje procesor shranjuje in dostopa do operandov med izvajanjem aritmetično-logičnih operacij.
    *   **Akumulator**: Najstarejši način, z enim registrom (akumulatorjem). Eden sam specializiran register za aritmetično-logične operacije. Slabost: veliko prometa z glavnim pomnilnikom, kar povzroča počasnost.
    *   **Sklad (stack)**: Dostopna je samo najvišja lokacija (LIFO). Podatkovna struktura LIFO (Last-In, First-Out), kjer se dostopa le do zadnje dodane vrednosti. Ukaza PUSH in POP. Preprosta realizacija in kratki ukazi, a omejen dostop do več operandov.
    *   **Množica registrov (register set)**: Danes edina rešitev. Velika množica hitrih, notranjih pomnilniških celic v CPE. Registri so hitri, omogočajo istočasen dostop do več operandov in krajše ukaze. Obstajajo splošnonamenski registri (vsi ekvivalentni) ali specializirane skupine (za operande, za naslove).
2.  **Število eksplicitnih operandov v ukazu**: Koliko operandov je neposredno določenih v strojni kodi posameznega ukaza.
    *   **3-operandni**: `OP3 ← OP2 + OP1`. Operandi so običajno v registrih.
    *   **2-operandni**: `OP2 ← OP2 + OP1`. Enostavnejši, a malo počasnejši.
    *   **1-operandni**: `AC ← AC + OP1` (akumulatorski računalniki). Operacija se izvede med akumulatorjem in drugim operandom, rezultat pa gre v akumulator.
    *   **Brez-operandni (skladovni)**: `SkladVRH ← SkladVRH + SkladVRH-1`. Vsi operandi se vzamejo s sklada, rezultat pa se zapiše nazaj na sklad. Najkrajši ukazi, a potrebujeta vsaj 2 ukaza z eksplicitnim operandom (PUSH, POP) za prenos med glavnim pomnilnikom in skladom.
3.  **Lokacija operandov in načini naslavljanja**: Določa, kje se operandi nahajajo (v registrih, pomnilniku) in kako se izračuna njihov naslov v pomnilniku.
    *   **Lokacija operandov**: Registri CPE, glavni pomnilnik (GP), registri V/I naprav.
    *   **Računalniki glede na lokacijo operandov**:
        *   **Registrsko-registrske** (load/store): Vsi operandi so v registrih CPE. Zasnova, kjer se vse ALU operacije izvajajo samo med registri. Podatki med registri in pomnilnikom se prenašajo izključno z ukazi load in store. Najbolj razširjeni.
        *   **Registrsko-pomnilniške**: En operand v registru, drugi v pomnilniku. To zmanjšuje potrebo po ločenih ukazih load/store, vendar je lahko počasneje.
        *   **Pomnilniško-pomnilniške**: Vsak operand je lahko v pomnilniku (kompleksni ukazi, CISC). Oba operanda sta lahko v pomnilniku. To omogoča zelo kompleksne ukaze, a so izjemno počasni.
    *   **Načini naslavljanja (za pomnilniške operande)**: Različni načini, kako procesor določi dejanski naslov podatka v pomnilniku na podlagi informacij v ukazu.
        *   **Takojšnje (immediate)**: Operand je podan z vrednostjo v ukazu (konstanta). Vrednost je direktno vključena v ukaz.
        *   **Neposredno (direct)**: Operand je podan z naslovom (registrsko ali pomnilniško). Naslov operanda je neposredno podan v ukazu. Problem dolgih naslovov in nezdružljivosti.
        *   **Posredno (indirect)**: V ukazu je naslov lokacije, kjer je shranjen naslov operanda. Ukaz vsebuje naslov pomnilniške lokacije, katere *vsebina* je dejanski naslov operanda.
        *   **Relativno naslavljanje** (najpogostejše): Naslov operanda določen relativno na vsebino registra.
            *   **Bazno (base addressing)**: Naslov $A = R2 + D$ (k vsebini baznega registra R2 prištejemo odmik D). Uporabno za dostop do elementov znotraj strukture ali bloka podatkov.
            *   **Indeksno (indexed addressing)**: Naslov $A = R2 + R3 + D$ (R3 je indeksni register, uporaba za polja). Uporabno za dostop do elementov v poljih ali tabelah, kjer je R3 indeks.
            *   **Pred-dekrementno in po-inkrementno** (skupaj tvorita skladovno naslavljanje). Pogosto se uporabljata pri obdelavi podatkovnih struktur, kot so seznami, in se v kombinaciji uporabljata za delovanje sklada.
            *   **Velikostno indeksno (scaled indexed)**: $A = R2 + R3 \times \Delta + D$.
        *   **Pozicijsko neodvisno naslavljanje**: Programi, ki jih lahko premestimo v drug del pomnilnika, ne smejo vsebovati absolutnih naslovov. Programi, ki jih lahko naložimo v poljuben del pomnilnika, ne da bi jih bilo treba spreminjati.
        *   **PC-relativno naslavljanje**: Programski števec (PC) služi kot bazni register. Naslov se izračuna glede na trenutno vrednost programskega števca (PC). Pogosto se uporablja za skoke in dostop do globalnih podatkov blizu kode.
4.  **Operacije**: Manj jih je kot ukazov. Imena ukazov so **mnemoniki**. Operacije so funkcije, ki jih procesor lahko izvaja.
    *   **Prenosi podatkov (data transfer)**: LOAD, STORE, MOVE, PUSH, POP, CLEAR, SET. Premikanje podatkov med registri in pomnilnikom ali med samimi registri.
    *   **Aritmetične in logične operacije**: Seštevanje, odštevanje, množenje, deljenje, negacija, absolutna vrednost, inkrement, dekrement, AND, OR, NOT, XOR, pomiki.
    *   **Kontrolne operacije**: Spreminjajo vrstni red ukazov. Ukazi, ki spreminjajo normalni (zaporedni) tok izvajanja programa. Pogojni skoki (conditional branches), brezpogojni skoki (unconditional branch/jump), klici in vrnitve iz podprogramov (CALL, JSR, RET).
    *   **Operacije v plavajoči vejici**: Izvaja jih posebna enota (FPU).
    *   **Sistemske operacije**: Vplivajo na delovanje računalnika, običajno privilegirane.
    *   **Vhodno/izhodne operacije**: Na nekaterih računalnikih obstajajo posebni ukazi, na drugih se uporabljajo običajni ukazi za prenos podatkov.
    *   **Skalarne in vektorske operacije**.
5.  **Vrsta in dolžina operandov**: Kakšne vrste podatkov procesor podpira in kakšne so njihove velikosti.
    *   **Vrste operandov**: Bit, znak (8-bitni ASCII, niz znakov), celo število (predznačeno/nepredznačeno, 8, 16, 32, 64 bitov), realno število (plavajoča vejica IEEE 754, 32/64/128 bitov), desetiško število (BCD/ASCII). Nekateri procesorji podpirajo operacije direktno na desetiških številih, kar je pomembno za finančne aplikacije.
    *   **Dolžine operandov (večkratniki 2)**: Bajt (8 bitov), Polovična beseda (16 bitov), Beseda (32 bitov), Dvojna beseda (64 bitov), Štirikratna beseda (128 bitov).
    *   **Sestavljeni pomnilniški operandi**: Sestavljeni iz več pomnilniških besed na zaporednih lokacijah.
        *   **Pravilo debelega konca (Big Endian Rule)**: Najtežji del operanda na najnižjem naslovu (npr. število 0x12345678. Najpomembnejši bajt (0x12) je na najnižjem naslovu).
        *   **Pravilo tankega konca (Little Endian Rule)**: Najlažji del operanda na najnižjem naslovu (npr. število 0x12345678. Najmanj pomemben bajt (0x78) je na najnižjem naslovu). RISC-V uporablja little endian.
    *   **Problem poravnanosti (alignment)**: Operandi so **poravnani**, če je naslov deljiv z njihovo dolžino v bajtih. Neporavnanost zahteva več dostopov ali sproži past. Neporavnanost lahko povzroči več pomnilniških dostopov in s tem upočasni delovanje, ali pa sproži izjemo (trap), ki jo mora obravnavati operacijski sistem.

### 3.1 Zgradba ukazov
Ukaz je shranjen v eni ali več pomnilniških besedah in vsebuje **operacijsko kodo** (opcode), ki določa vrsto operacije, ki jo mora CPE izvesti (npr. seštevanje, branje iz pomnilnika, skok), ter **informacijo o operandih**.
*   **Format ukaza**: Pove, kako so biti ukaza razdeljeni na operacijsko kodo in operande (število polj, velikost, pomen).
*   **Parametri, ki vplivajo na format**: Dolžina pomnilniške besede, število eksplicitnih operandov, vrsta in število registrov v CPE, dolžina pomnilniškega naslova, število operacij.
*   **Načini oblikovanja formata ukazov**:
    *   **Spremenljiva dolžina**: Število eksplicitnih operandov in načini naslavljanja so spremenljivi. Značilno za CISC.
    *   **Fiksna dolžina**: Število eksplicitnih operandov je fiksno, majhno število formatov. Značilno za RISC.
    *   **Hibridni način**.
*   **Ortogonalnost ukazov**: Informacija o operaciji je neodvisna od informacij o operandih. Pomeni, da so različni aspekti ukaza (operacija, način naslavljanja, vrsta operanda) neodvisni drug od drugega. To poenostavi oblikovanje procesorja in prevajalnika.
*   **CISC (Complex Instruction Set Computer) vs. RISC (Reduced Instruction Set Computer)**:
    *   **CISC**: Veliko število ukazov, kompleksni ukazi (IBM 370, VAX, Intel).
    *   **RISC**: Majhno število ukazov, preprosti ukazi (MIPS, ARM, DEC Alpha).
    *   **Razlogi za povečevanje št. ukazov** (zgodovinsko): Semantični prepad (razlika med visokolevelskimi jeziki in strojnim jezikom. CISC je poskušal premostiti ta prepad z dodajanjem kompleksnih ukazov, ki so bolj podobni konstruktom v višjih programskih jezikih), mikroprogramiranje (ukazi so implementirani kot zaporedje mikro-operacij, shranjenih v posebnem pomnilniku znotraj CPE), razmerje hitrosti CPE in GP (včasih je bil GP relativno hitrejši v primerjavi s CPE, kar je omogočalo pogostejše dostope do pomnilnika).
    *   **Razlogi za zmanjševanje št. ukazov** (po 80. letih): Težave prevajalnikov (prevajalniki so imeli težave z optimizacijo kode za kompleksne CISC ukaze), pojav predpomnilnikov (predpomnilniki so zmanjšali vpliv počasnega glavnega pomnilnika, zato direktni dostop do GP znotraj ukazov ni bil več tako problematičen), uvajanje paralelizma (cevovod).
    *   **Definicija arhitekture RISC**:
        *   Večina ukazov se izvrši v enem ciklu CPE.
        *   Registrsko-registrska zasnova (load/store).
        *   Ukazi realizirani s trdo ožičeno logiko (ne mikroprogramsko).
        *   Malo ukazov in načinov naslavljanja.
        *   Enaka dolžina ukazov.
        *   Dobri prevajalniki.

## 4. Centralna procesna enota (CPE)

CPE je digitalni sistem, ki vsebuje **kombinacijska** in **sekvenčna** digitalna vezja. Kombinacijska vezja (npr. seštevalniki, logična vrata) proizvajajo izhod na podlagi trenutnih vhodov, sekvenčna vezja (npr. registri, števci) pa imajo pomnilnik in se njihovo stanje spreminja glede na vhod in čas. Njeno delovanje je odvisno od trenutnega stanja in vhodov.

1. **Aritmetično-logična enota (ALU - Arithmetic Logic Unit):**
    - To je srce CPE, odgovorno za izvajanje vseh aritmetičnih operacij (seštevanje, odštevanje, množenje, deljenje) in logičnih operacij (AND, OR, NOT, XOR, primerjave, bitni premiki).
    - Predvsem **kombinacijsko vezje**. Izhodi so neposredna funkcija vhodov.
2. **Krmilna enota (CU - Control Unit):**
    - Krmilna enota je odgovorna za krmiljenje in usklajevanje vseh operacij znotraj CPE in med CPE ter drugimi komponentami sistema. Dekodira ukaze iz pomnilnika in generira krmilne signale, ki usmerjajo pretok podatkov, aktivirajo ALU in druge dele CPE.
    - Kombinacija **kombinacijskih** (npr. dekoder ukazov) in **sekvenčnih vezij** (npr. register stanj končnega avtomata, ki določa fazo izvajanja ukaza).
    - **Deluje skupaj z:**
        - **Programski števec (PC - Program Counter):** Register, ki shranjuje naslov naslednjega ukaza, ki ga je treba pridobiti iz pomnilnika. (Sekvenčno vezje - register).
        - **Register ukazov (IR - Instruction Register):** Register, ki začasno shranjuje trenutni ukaz, ki ga dekodira krmilna enota. (Sekvenčno vezje - register). 
3. **Registri (Registers):**
    
    - So majhne, izjemno hitre pomnilne lokacije znotraj CPE, ki začasno shranjujejo podatke, vmesne rezultate, naslove in krmilne informacije. So bistveno hitrejši od glavnega pomnilnika (RAM)   
    - Predvsem **sekvenčna vezja** (sestavljeni so iz flip-flopov).
    - **Vrste registrov:**
        - **Splošni registri (General-Purpose Registers):** Uporabljajo se za shranjevanje podatkov in vmesnih rezultatov, ki jih procesira ALU.
        - **Statusni register (Flags Register):** Shranjuje zastavice (bitne indikatorje) o rezultatih prejšnjih ALU operacij (npr. zastavica ničle, prelivne zastavice, negativna zastavica), ki jih CU uporablja za pogojevanje skokov in odločitev.
        - **Kazalec sklada (SP - Stack Pointer) in Osnovni kazalec (BP - Base Pointer):** Uporabljata se za upravljanje podatkov na programskem skladu.
        - **Registri naslovov in podatkov (MAR - Memory Address Register, MDR - Memory Data Register):** Uporabljajo se za shranjevanje naslovov in podatkov, ki se prenašajo v/iz glavnega pomnilnika.
4. **Predpomnilnik (Cache Memory):**
    - Majhen, zelo hiter pomnilnik, ki shranjuje pogosto uporabljene podatke in ukaze. Nahaja se med CPE in glavnim pomnilnikom (RAM), da zmanjša zakasnitev pri dostopu do podatkov. Sodobne CPE imajo več nivojev predpomnilnika (L1, L2, L3), pri čemer je L1 najhitrejši in najbližje CPE, L3 pa največji in najpočasnejši.
    - Predvsem **sekvenčno vezje** (sestavljeno iz pomnilniških celic, ki so v bistvu zapahi ali flip-flopi), vendar z visoko stopnjo kompleksnosti pri upravljanju (kombinacijska logika za preverjanje zadetkov, sekvenčna za stanje vrstic).


### 4.1 Delovanje CPE
CPE deluje v ponavljajočem se ciklu dveh korakov:
- **Instruction Fetch**: The CPU retrieves the instruction from memory, based on the address stored in the Program Counter (PC).
- **Instruction Decode and Register Read**: The CPU decodes the fetched instruction to understand what operation to perform and which operands are needed. It also reads the required operands from the specified registers.
- **Execute (ALU Operation/Address Calculation)**: The CPU performs the main operation. This could involve an Arithmetic Logic Unit (ALU) operation (like addition, subtraction, logical operations), or if it's a memory access instruction, it calculates the memory address.
- **Memory Access (Operand Transfer/Result Storage)**:
    - **Load**: If the instruction requires data from memory, the CPU fetches that data.
    - **Store**: If the instruction's result needs to be written to memory, the CPU writes the data to the calculated memory address.
- **Write Back**: The result of the operation (if any) is written back to a register.
- **Program Counter Update**: The Program Counter (PC) is updated to point to the next instruction. For sequential instructions, the PC is typically incremented by 4 bytes (for a 32-bit instruction set, as most instructions are 4 bytes long). However, for control flow instructions like **jumps** or **branches**, the PC is updated with the target address specified by the instruction.


Vsak korak traja eno ali več period ure CPE ($t_{CPE}$). Frekvenca ure ($f_{CPE} = 1/t_{CPE}$) je navzgor omejena z zakasnitvami kombinacijskih vezij.

*   **Perioda ure CPE ($t_{CPE}$):** Predstavlja čas, ki je potreben za en cikel ure centralne procesne enote (CPE). To je čas, ki ga potrebuje signal ure, da se spusti in spet dvigne.  Je osnovna časovna enota za delovanje CPE.
*   **Frekvenca ure ($f_{CPE} = 1/t_{CPE}$):** Frekvenca je obratna vrednost periode ure. Meri se v Hertzih (Hz) in pove, koliko ciklov ure se zgodi v eni sekundi. Višja frekvenca pomeni hitrejše izvajanje navodil. Na primer, CPE s frekvenco 3 GHz izvede 3 milijarde ciklov ure na sekundo.
*   **Navzgor omejena z zakasnitvami kombinacijskih vezij:** Kombinacijska vezja so tista, katerih izhod je odvisen samo od trenutnih vhodnih vrednosti (npr. AND, OR, XOR, seštevalniki). Ta vezja potrebujejo določen čas, da stabilizirajo izhod, ko se vhod spremeni. Ta čas imenujemo **zakasnitev kombinacijskega vezja**.

    Zakaj je to pomembno?  Frekvenca ure mora biti dovolj počasna, da imajo vsa kombinacijska vezja v CPE dovolj časa, da zaključijo svoje delovanje v enem ciklu ure. Če bi bila frekvenca prehitra (perioda ure prekratka), bi se lahko zgodilo, da se podatki na vhodu spremenijo, preden bi se izhod kombinacijskega vezja stabiliziral. To bi povzročilo napačno delovanje CPE. Zato je frekvenca ure navzgor omejena z najdaljšo zakasnitvijo kombinacijskega vezja.

    **Primer:** Predstavljajte si, zakasnitev 5 ns.  Da bi ALE pravilno delovala, mora signal na vseh njenih vhodih biti stabilen vsaj 5 ns.  To pomeni, da perioda ure ($t_{CPE}$) mora biti vsaj 5 ns, frekvenca ure pa ($f_{CPE}$) največ 200 MHz (1 / 5 ns = 0.2 GHz = 200 MHz).

CPE lahko razdelimo na kontrolno enoto (KE), ki generira kontrolne signale in usmerja delovanje podatkovne enote (npr. kateri register naj bere, katero operacijo naj izvede ALE), in podatkovno enoto (PE), ki vključuje ALE in registre.

*   **Kontrolna enota (KE):** So "možgani" CPE.  Njena glavna naloga je dešifrirati navodila (inštrukcije) in generirati ustrezne kontrolne signale. Ti signali "povedo" ostalim delom CPE (predvsem podatkovni enoti), kaj naj počnejo. KE določa:
    *   Kateri register naj se prebere in prenese v ALE.
    *   Katero aritmetično ali logično operacijo naj izvede ALE (seštevanje, odštevanje, AND, OR, itd.).
    *   V kateri register naj se shrani rezultat ALE.
    *   Naslednji naslov navodila, ki ga je treba izvesti.

    KE deluje kot dirigent orkestra, ki usmerja različne instrumente (komponente CPE) za izvajanje glasbe (izvajanje programa).

*   **Podatkovna enota (PE):** Je del CPE, ki izvaja dejanske operacije na podatkih.  Vključuje:
    *   **ALE (aritmetično-logična enota):**  Izvaja aritmetične (seštevanje, odštevanje, množenje, deljenje) in logične (AND, OR, XOR, NOT) operacije.
    *   **Regristri:**  Majhne, hitre pomnilniške lokacije, ki se uporabljajo za shranjevanje podatkov in naslovov, s katerimi CPE trenutno dela.  Tipični registri vključujejo akumulator, števec programa (PC), kazalnik sklada (SP) in splošne registre.
    *   **Vodila (buses):** Skupine žic, ki prenašajo podatke med različnimi komponentami znotraj CPE (npr. med registri in ALE).
    *   **Memorija (spomin):** čeprav ni del CPE, omogoča shranjevanje podatkov, s katerimi dela CPE

    PE je torej del CPE, ki dejansko "obdeluje" podatke pod nadzorom KE.

>[!|hide]- **Primer:**
>
Recimo, da CPE izvaja navodilo `ADD R1, R2, R3` (seštej vsebino registra R1 in R2 ter rezultat shrani v register R3).
>
>1.  **KE dešifrira navodilo.**
>2.  **KE generira kontrolne signale, ki:**
>  *   Povedo PE, da prebere vsebino registra R1 in R2.
>  *   Povedo ALE, da izvede seštevanje.
>  *   Povedo PE, da shrani rezultat seštevanja v register R3.
>
Z drugimi besedami, KE ukaže PE, naj izvede določeno operacijo. Rezultat te operacije pa se vrne v PE, kjer se shrani v ustrezni register.


### 4.2 Načini implementacije CPE
1.  **Enocikelni procesor (single-cycle)**: Celoten ukaz se izvrši v eni periodi ure. Glavna slabost je **dolga perioda ure**, saj mora biti dovolj dolga za najdaljši ukaz (npr. LW, ki vključuje dostop do pomnilnika). **CPI (Cycles Per Instruction) je 1** za vsak ukaz.
2.  **Večcikelni procesor (multi-cycle)**: Ukaz se izvrši v več periodah ure, ukazi pa se ne prekrivajo. Kontrolna enota vsebuje **končni avtomat (FSM)**. Logično vezje, ki s sekvenčnim zaporedjem stanj generira kontrolne signale za vsako fazo ukaza. V vsaki periodi se izvrši ena podoperacija. Perioda ure je določena z najpočasnejšim korakom ukaza, ne z najpočasnejšim ukazom. CPI je večji (običajno 3 do 6).
  
3.  **Cevovodni procesor (pipeline)**: Ukaz se izvrši v več periodah ure, a se ukazi časovno delno prekrivajo. Ukazi se prekrivajo, kot na tekočem traku v tovarni, kjer se različne faze izdelka (ukaza) obdelujejo sočasno na različnih postajah. To je **najpogostejši način** za izkoriščanje paralelizma na nivoju ukazov.

Pri enocikelnemu in pri cevovodnem imamo še vedno 1 cikel na ukaz le da imamo pri enocikelnemu dolžino omejeno z najdaljšim ukazom, pri cevovodnem pa z najdaljšim korakom, kjer po zečetnem zamiku spet dobimo 1 cikel na ukaz, zato kljub temu da imamo isti CPI dobimo več ukazov na sekundo.

### 4.3 Merjenje zmogljivosti CPE

Zmogljivost CPE je merodajna s **časom izvrševanja programa**:

$$ \text{CPE čas} = \text{Število ukazov programa} \times \text{CPI} \times t_{CPE} $$

CPE čas je pravi pokazatelj zmogljivosti, saj upošteva tako število ukazov, kot tudi hitrost njihovega izvajanja in urino frekvenco.
*   **CPI (Clocks Per Instruction)**: Povprečno število urinih period na ukaz. Idealni CPI ($\text{CPI}_{idealni}$) ne upošteva izgubljenih urinih period zaradi zgrešitev v predpomnilniku ali cevovodnih nevarnosti.
*   **$\text{CPI}_{resnični}$** upošteva vpliv predpomnilnika:
    $$ \text{CPI}_{resnični} = \text{CPI}_{idealni} + \text{CPE}_{\text{periode\_čak}} $$
    kjer je $\text{CPE}_{\text{periode\_čak}} = N \times (1-H) \times \text{K}$ (število pomnilniških dostopov $\times$ verjetnost zgrešitve $\times$ zgrešitvena kazen).
*   **MIPS (Million Instructions Per Second)**:
    $$ \text{MIPS} = \frac{f_{CPE}}{\text{CPI} \times 10^6} $$
    MIPS ni popolnoma merodajen, saj je odvisen od vrste ukazov in programa (ne zgolj število ukazov, temveč tudi kompleksnost ukazov, kar pomeni, da višji MIPS ne pomeni nujno hitrejšega izvajanja programa).
*   **MFLOPS (Million FLoating point Operations Per Second)**: Uporablja se za programe, ki uporabljajo operacije v plavajoči vejici.
*   **Sintetični "benchmarki"** (Whetstone, Linpack, Dhrystone) in **SPEC** (Standard Performance Evaluation Corporation) se uporabljajo za primerjavo zmogljivosti. Sintetični benchmarki so programi, zasnovani posebej za merjenje zmogljivosti, ki pa morda ne odražajo realne uporabe.
*   **Pohitritev (Speed-up)**:
    $$ S = \frac{\text{Zmog}_{\text{A}}}{\text{Zmog}_{\text{B}}} = \frac{\text{CPE}_{\text{čas,B}}}{\text{CPE}_{\text{čas,A}}} $$
    Primerjava CPE zgolj na osnovi frekvence ure ($f_{CPE}$) je zavajajoča.

## 5. Cevovod (Pipeline)

Z gradnjo CPE, ki zaporedno izvršuje ukaze, je težko doseči CPI < 4. **Cevovod** je najpogostejši način za povečanje **IPS (Instructions Per Second)** z zmanjšanjem CPI (povečanjem števila logičnih elementov). Cilj cevovoda je približati CPI vrednosti 1.

### 5.1 Splošno o cevovodu
*   Pri cevovodu se naenkrat izvršuje več ukazov, tako da se **posamezni koraki izvrševanja prekrivajo** (podobno tekočemu traku).
*   Vsako podoperacijo opravi določen del cevovoda, imenovana **stopnja cevovoda (pipeline stage)** ali segment cevovoda.
*   **Idealno uravnotežen cevovod** z N stopnjami lahko poveča zmogljivost N-krat. Idealno uravnotežen cevovod pomeni, da so vse stopnje cevovoda enako dolge (enako časa za delo).
*   **Čas med dvema pomikoma** je enak urini periodi $t_{CPE}$. Perioda ne more biti krajša od časa, ki ga potrebuje najpočasnejša stopnja.
*   **Supercevovodni računalniki** imajo zelo dolge cevovode (npr. Intel Pentium 4 z 20-31 stopnjami). Imajo zelo dolge cevovode, kar omogoča zelo visoke frekvence ure, vendar poveča vpliv nevarnosti.
*   **Cevovodne nevarnosti (pipeline hazards)** povzročijo, da se cevovod ustavi in počaka. To so situacije, ki prekinejo idealno pretakanje ukazov skozi cevovod in zmanjšajo njegovo učinkovitost. Zato zmogljivost z večanjem števila stopenj najprej narašča, nato pa začne padati.
*   Prednost cevovoda je, da je **za programerja neviden**, kar omogoča združljivost starih programov z novimi arhitekturami. Prevodnik skrbi za večino optimizacij, programer se ne ukvarja neposredno z delovanjem cevovoda, razen pri zelo specifičnih optimizacijah.

### 5.2 Klasična petstopenjska cevovodna podatkovna enota
RISC procesorji so enostavnejši za cevovodno realizacijo. V RISC CPE je običajno 5 stopenj:
1.  **IF (Instruction Fetch)**: Prevzem ukaza in sprememba PC.
2.  **ID (Instruction Decode)**: Dekodiranje ukaza in dostop do registrov.
3.  **EX (Execute)**: Izvrševanje operacije.
4.  **MEM (Memory Access)**: Dostop do pomnilnika.
5.  **WB (Write Back)**: Shranjevanje rezultata v register.
*   Vsaka stopnja mora opraviti svoje delo v eni urini periodi.
*   Cevovodni procesorji imajo običajno **dva predpomnilnika** (ukaznega in operandnega) za hkratni dostop. Harvardska arhitektura – ločena predpomnilnika za ukaze in podatke, kar omogoča sočasen dostop in zmanjšuje strukturne nevarnosti.

### 5.3 Cevovodne nevarnosti
Tri vrste cevovodnih nevarnosti so:
1.  **Strukturne nevarnosti (SN)**: Pojavijo se, kadar več stopenj cevovoda v isti urini periodi potrebuje **isto enoto** (register, ALE, GP, PP). Popolno odpravljanje je drago. Pojavijo se, kadar dve različni stopnji cevovoda poskušata hkrati dostopati do iste strojne komponente.
2.  **Podatkovne nevarnosti (PN)**: Pojavijo se, kadar ukaz potrebuje kot vhodni operand **rezultat prejšnjega, še ne dokončanega ukaza** (imenuje se tudi **Read-After-Write oz. RAW**). Ukaz B poskuša prebrati podatek, ki ga še ni zapisal ukaz A.
    *   **Rešitve za PN**:
        *   **Cevovodna zaklenitev (pipeline interlock)**: CPE ugotovi PN (s posebno enoto za ugotavljanje PN, HD) in ustavi stopnjo ID (in IF) za nekaj period, tako da vstavlja ukaze NOP (imenovane **mehurčki/bubbles**). Strojni mehanizem, ki zazna PN in zaustavi procesor, dokler se potrebni podatek ne pojavi. To zmanjša zmogljivost. Mehurčki so prazni ciklusi, vstavljeni v cevovod, ki ne delajo ničesar, ampak zgolj zamikajo izvrševanje naslednjih ukazov.
        *   **Premoščanje (bypassing, data forwarding)**: Rezultat operacije se prenese neposredno iz prejšnjih stopenj cevovoda (EX ali MEM) v stopnjo EX za naslednji ukaz, s čimer se izogne čakanju. Podatki se 'posredujejo' neposredno iz stopnje, kjer so izračunani (npr. EX ali MEM), v stopnjo, ki jih potrebuje (npr. EX za naslednji ukaz), namesto da bi čakali, da se zapišejo v register in nato preberejo. Reši večino PN, razen pri ukazih load (kjer je potreben 1 mehurček).
        *   **Cevovodno razvrščanje (pipeline scheduling)**: Prevajalnik spremeni vrstni red ukazov, da odpravi nevarnosti. Preureditev vrstnega reda ukazov s strani prevajalnika med kompilacijo, da se minimizirajo PN, ne da bi se spremenil končni rezultat. Danes to večina prevajalnikov uporablja.
    *   Poleg RAW obstajajo še **WAR (Write After Read)** (Ukaz B poskuša pisati v register, ki ga še bere ukaz A) in **WAW (Write After Write)** (Ukaz B poskuša pisati v register, v katerega je že pisal ukaz A, in se morata izvesti v pravilnem vrstnem redu) nevarnosti, ki se pojavijo pri kompleksnejših cevovodih in dinamičnem razvrščanju. **RAR (Read After Read)** (Ukaz B bere iz registra, ki ga bere tudi ukaz A) ne povzroča PN.
    *   **Dinamično razvrščanje**: Strojna sprememba vrstnega reda izvrševanja ukazov. To lahko pripelje do WAR in WAW nevarnosti. **Tomasulov algoritem** (1967) s **rezervacijskimi postajami** (vmesni pomnilniki, kjer se shranijo operandi in čakajo, da so funkcionalne enote proste) odpravi te nevarnosti. To je napreden strojni algoritem za dinamično razvrščanje in odpravljanje vseh vrst podatkovnih nevarnosti (vključno z WAR in WAW) z uporabo rezervacijskih postaj in preimenovanja registrov.
    *   **Imenske odvisnosti** (WAR in WAW) se lahko odpravijo z **preimenovanjem registrov**. Fizičnim registrom se dodelijo logična imena, da se izognejo WAR in WAW nevarnostim, ko več ukazov uporablja isti logični register.
3.  **Kontrolne nevarnosti (KN)**: Pojavijo se pri ukazih, ki spremenijo PC drugače kot PC $\leftarrow PC+4$ (skoki, klici, vrnitve). Ko se PC spremeni v stopnji EX, sta vsebini stopenj IF in ID neveljavni. Pojavijo se, kadar cevovod ne ve, kateri ukaz naj prevzame naslednjega, ker je spremenjen tok izvajanja programa (npr. skok).
    *   **Rešitve za KN**:
        *   **Zmanjšanje skoččne zakasnitve**: Preverjanje pogoja za skok in izračun skočnega naslova se izvajata čim bližje prvi stopnji cevovoda (že v ID).
        *   **Vstavljanje mehurčkov (flush)**: Najenostavnejša rešitev, razveljavi ukaza v IF in ID. Cevovod se 'izprazni' napačno prevzetih ukazov po skoku. Vsak skočni ukaz povzroči 2 čakalni periodi.
        *   **Napoved (predikcija)** izpolnitve skočnega pogoja in skočnega naslova: Procesor poskuša ugibati, v katero smer bo šel skok, in začne vnaprej nalagati ukaze po tej napovedi. Če je napoved napačna, je treba cevovod izprazniti in ponovno napolniti.
            *   **Statična predikcija**: Prevajalnik napove rezultat pogoja. Lahko vključuje **zakasnjene skoke (delayed branches)**, kjer se ukazi v "skočni reži" izvršijo ne glede na izpolnitev pogoja. To je preprosta statična tehnika, kjer se ukaz(i) za skokom vedno izvršijo, ne glede na rezultat skoka. Prevajalnik mora pametno postaviti ukaze v to 'skočno režo'.
            *   **Dinamična predikcija**: Strojni načini, ki se prilagajajo dogajanju v programu. Uporabljajo **prediktorsko tabelo (branch prediction table/branch history table)**. Tabela, ki shrani zgodovino preteklih skokov in njihovih rezultatov, da se izboljša natančnost napovedi.
                *   **1-bitna prediktorska tabela**: Zapomni si zadnji rezultat (vzet/ne vzet).
                *   **2-bitna prediktorska tabela**: 4 stanja, zmanjša napačne napovedi pri vgnezdenih zankah.
                *   **Korelacijski prediktor (m,n)**: Uporablja globalno zgodovino (obnašanje prejšnjih m skokov) za izbiro n-bitne tabele.
                *   **Turnirski prediktor**: Združuje lokalne in globalne prediktorje in uporablja selektor, ki izbere najboljši prediktor za določen skok.
                *   **Skočni predpomnilnik (branch target buffer)**: Shrani skočne naslove zadnjih skokov, da se izogne zamudi pri iskanju naslova. Hrani ciljne naslove skokov, tako da jih ni treba ponovno računati ob vsaki napovedi.
                *   **Vrnitveni prediktor (return address predictor)**: Majhen sklad za napovedovanje povratnih naslovov. Majhen sklad, ki napoveduje povratne naslove podprogramov, saj je JALR naslov odvisen od registra.
                *   **Enota za prevzem ukazov (integrated instruction fetch unit)**: Samostojno dostavlja ukaze stopnjam. Samostojen del procesorja, ki je odgovoren za efektivno in predvidljivo prevzemanje ukazov, vključno z obravnavo skokov.
        *   **Vejitve brez skokov (predikatne vejitve)**: Uporabljajo se set-ukazi in logične operacije, da se izognejo skokom (npr. s pomočjo multiplekserjev), kar je koristno pri cevovodih. Namesto skokov se ukazi pogojno izvajajo ali pa se rezultati operacij pogojno izbirajo z multiplekserji. To zmanjša potrebo po skokih in izboljša pretok skozi cevovod.

### 5.4 Večizstavitveni procesorji
Za doseganje CPI < 1 (pomeni, da CPE izvede več kot en ukaz na urino periodo) se mora v vsaki urini periodi prevzeti in izstaviti več kot 1 ukaz. To so **večizstavitveni procesorji (multiple issue processors)**.
*   **Superskalarni procesorji**: Dinamično določajo, kateri ukazi se izstavijo. Imajo več funkcionalnih enot in strojno določajo, kateri neodvisni ukazi se lahko izvedejo paralelno. Uporabljajo eksplicitno **preimenovanje registrov** in **razširjeno množico registrov** za odpravljanje WAR in WAW nevarnosti. To je ključno za odpravljanje WAR in WAW odvisnosti v superskalarnih procesorjih, kjer se ukazi lahko izvajajo izven vrstnega reda.
*   **VLIW (Very Long Instruction Word) procesorji**: Imajo dolge ukaze, ki vsebujejo več običajnih ukazov za paralelno izvajanje. Ukazi so zelo dolgi in vsebujejo navodila za več funkcionalnih enot, ki se izvajajo sočasno. CPE ne ugotavlja odvisnosti in nevarnosti, to je delo **prevajalnika**. Vsa kompleksnost načrtovanja paralelizma je prenesena na prevajalnik.

>[!|]+ Intuicija
> Najprej si poglejmo, kaj pomeni `CPI` (Cycles Per Instruction – Cikli na ukaz):
> *   **CPI = 1**: Procesor povprečno izvede 1 ukaz na 1 urni cikel. To je značilno za procesorje z enostavnim cevovodom (pipelining), kjer se s pomočjo cevovoda sicer vsak cikel "dokonča" en ukaz, a jih hkrati še vedno obdelujejo.
> *   **CPI > 1**: Procesor potrebuje več kot 1 cikel za izvedbo enega ukaza. To se zgodi, če so prisotne "nevarnosti" (hazards) ali zastoje v cevovodu, zaradi katerih mora procesor čakati.
> *   **CPI < 1**: To je naš cilj! Pomeni, da procesor izvede *več kot en ukaz* v enem samem urnem ciklu. Predstavljajte si, da imate namesto enega delavca več delavcev, ki lahko hkrati opravljajo različne naloge.
>
> Da bi dosegli CPI < 1, mora procesor dejansko "prevzeti" (fetch) in "izstaviti" (issue) v izvajanje več kot en ukaz v vsakem urnem ciklu. Od tu ime **večizstavitveni procesorji (multiple-issue processors)**.
>
> Obstajata dva glavna pristopa k temu:
>
> ---
>
> ### 1. Superskalarni procesorji (Superscalar Processors)
>
> To so procesorji, ki so danes najpogostejši (npr. vsi Intelovi Core i in AMD Ryzen procesorji).
>
> **Ključna značilnost:** **Dinamično določanje** paralelnosti. Procesor sam v realnem času, med izvajanjem programa, ugotavlja, katere ukaze lahko izvede paralelno.
>
> **Kako delujejo:**
> 1.  **Več funkcionalnih enot:** Procesor ima več "izvršilnih enot". Namesto samo ene ALU (aritmetično-logične enote) ima lahko več ALU, več enot za operacije s plavajočo vejico (FPU), enote za nalaganje/shranjevanje podatkov (load/store units) itd. Predstavljajte si kuhinjo z več štedilniki, več pomivalnimi stroji in več deskami za rezanje – hkrati lahko pripravljate različne jedi.
> 2.  **Strojno ugotavljanje neodvisnosti:** Procesor prebere zaporedje ukazov in analizira njihove odvisnosti.
> *   Če ukaz B potrebuje rezultat ukaza A (npr. `add R1, R2, R3` in nato `mul R4, R1, R5`), sta odvisna in ju ni mogoče izvesti hkrati. Ukaz B mora počakati, da se A konča. To je prava odvisnost (RAW - Read After Write).
> *   Če pa sta ukaza neodvisna (npr. `add R1, R2, R3` in `sub R4, R5, R6`), jih lahko procesor izstavi in izvede hkrati na različnih funkcionalnih enotah.
> 
> **Izvajanje izven vrstnega reda (Out-of-Order Execution - OOE):** Procesor ne čaka, da se prejšnji ukaz dokonča, če lahko izvede kasnejši neodvisni ukaz. Predstavljajte si, da imate recept: najprej skuhajte testenine, nato naredite omako. Če omaka ne potrebuje testenin, lahko kuhar začne pripravljati omako, medtem ko voda za testenine še vre. To je izvajanje izven vrstnega reda.
>
> **Reševanje WAR in WAW nevarnosti:**
> Te nevarnosti (Writing After Reading in Writing After Writing) so "lažne" odvisnosti, ki nastanejo zaradi omejenega števila registrov v procesorju.
> *   **WAR (Write After Read):** Ukaz B piše v register, ki ga ukaz A šele bere. Če bi se B izvedel prej, bi A prebral napačno vrednost.
> *   Primer:
> 	```
> 	Ukaz 1: ADD R3, R1, R2
> 	Ukaz 2: SUB R1, R4, R5
> 	```
> 	
> 	Če bi se Ukaz C izvedel pred Ukazom A, bi Ukaz A v R1 naložil napačno vrednost, ko bi se Ukaz C že spremenil R1.
>
>
> *   **WAW (Write After Write):** Ukaz B piše v isti register kot ukaz A. Če bi se B izvedel prej in A kasneje, bi A-jev zapis prebrisal B-jev zapis, kar bi bilo narobe.
> *   Primer:
> 	```
> 	Ukaz A: MUL R1, R2, R3   ; R1 = R2 * R3
> 	Ukaz B: ADD R1, R4, R5   ; R1 = R4 + R5
> 	```
> 	Če se Ukaz B izvede pred Ukazom A, bi končna vrednost v R1 bila od Ukaza A. Če pa bi se Ukaz A izvedel pred Ukazom B, bi končna vrednost v R1 bila od Ukaza B. Pravilen vrstni red določa, kateri ukaz *zadnji* zapiše v register.
>
> Superskalarni procesorji rešujejo te nevarnosti z:
> *   **Eksplicitnim preimenovanjem registrov (Register Renaming):** Procesor ima dejansko več fizičnih registrov kot jih lahko programer vidi (imenujemo jih **razširjena množica registrov** ali "architectural registers" vs. "physical registers"). Ko ukaz potrebuje register, procesor temu ukazu dodeli "nov" fizični register.
> *   V zgornjem primeru WAW (`MUL R1`, `ADD R1`): Procesor bi `MUL` dodelil nek interni register `P1`, `ADD` pa drug interni register `P2`. Na koncu, ko se oba ukaza končata, se pravilna vrednost iz `P2` (ker je to "zadnji" ukaz, ki piše v R1) prenese v logični register R1. To omogoča, da se `MUL` in `ADD` izvedeta hkrati, če sta sicer neodvisna, ne da bi povzročila napako.
>
> **Prednosti superskalarnih procesorjev:**
> *   **Fleksibilnost:** Sami ugotavljajo paralelnost, kar pomeni, da je koda lahko napisana bolj splošno in bo delovala dobro na različnih superskalarnih arhitekturah.
> *   **Zmogljivost:** Zaradi dinamične optimizacije in izvajanja izven vrstnega reda lahko dosežejo zelo visoko zmogljivost.
>
> **Slabosti superskalarnih procesorjev:**
> *   **Kompleksnost strojne opreme:** Zahtevajo zelo kompleksno strojno opremo za ugotavljanje odvisnosti, preimenovanje registrov, predvidevanje skokov (branch prediction) itd. To poveča porabo energije in stroške.
>
> ---
>
> ### 2. VLIW (Very Long Instruction Word) procesorji
>
> To so procesorji, ki se manj uporabljajo v splošnih računalnikih, so pa pogosti v nekaterih specializiranih aplikacijah, kot so DSP (Digital Signal Processors) ali omrežni procesorji (npr. Intel Itanium je bil VLIW, a ni uspel na trgu).
>
> **Ključna značilnost:** **Statično določanje** paralelnosti. Procesor sam ne ugotavlja, kaj lahko izvede paralelno. To delo opravi **prevajalnik (compiler)**.
>
> **Kako delujejo:**
> 1.  **Zelo dolge ukaze (Very Long Instruction Word):** Prevajalnik vzame običajno kodo (npr. C++ ali Java) in jo prevede v VLIW ukaze. VLIW ukaz ni en sam ukaz, ampak je *paket* več običajnih ukazov, ki jih je prevajalnik predhodno analiziral in zagotovil, da se lahko izvedejo paralelno.
> *   Primer: Namesto `ADD R1, R2, R3` in nato `MUL R4, R5, R6`, bi VLIW ukaz bil nekaj takega:
> 	`[ADD R1, R2, R3 | MUL R4, R5, R6 | LOAD R7, (X) | STORE R8, (Y)]`
> 	Ta "zelo dolg" ukaz pove procesorju, da lahko vse te operacije izvede v enem samem ciklu, ker so neodvisne. Vsak del ukaza je namenjen določeni funkcionalni enoti.
> 1.  **Prevajalnik določa paralelnost:** Prevajalnik je tisti, ki analizira vse odvisnosti, preimenuje registre (če je potrebno) in poskrbi, da so vsi ukazi v enem VLIW paketu resnično neodvisni. Če prevajalnik naredi napako, bo program deloval napačno ali zelo počasi.
> 2.  **Poenostavljena strojna oprema:** Ker prevajalnik že vnaprej pove procesorju, kaj lahko izvede paralelno, procesor ne potrebuje kompleksnih vezij za dinamično ugotavljanje odvisnosti. Njegova naloga je samo, da vzame VLIW ukaz in vsak njegov del pošlje ustrezni funkcionalni enoti.
>
> **Prednosti VLIW procesorjev:**
> *   **Enostavnejša strojna oprema:** Zaradi prenosa kompleksnosti na prevajalnik so VLIW procesorji lahko preprostejši za načrtovanje, manjši in porabijo manj energije.
> *   **Predvidljivost:** Ker je paralelnost določena vnaprej, je njihovo delovanje bolj predvidljivo.
>
> **Slabosti VLIW procesorjev:**
> *   **Kompleksnost prevajalnika:** Prevajalniki za VLIW so izjemno kompleksni za razvoj.
> *   **Občutljivost na spremembe arhitekture:** Če se število ali tip funkcionalnih enot v procesorju spremeni, je treba kodo na novo prevesti, kar otežuje prenosljivost (portability). Včasih je treba kodo celo ponovno napisati.
> *   **Nekatere paralelnosti ni mogoče določiti vnaprej:** Nekatere odvisnosti podatkov so znane šele med izvajanjem programa (npr. odvisne od uporabnikovega vnosa). VLIW tukaj ni tako učinkovit kot superskalarni procesorji, kar lahko vodi do "mehurčkov" (bubbles) v cevovodu, če so deli VLIW paketa prazni.
> *   **Večja velikost kode:** Ker so ukazi "zelo dolgi" (polni praznih slotov, če ni dovolj ukazov za izvedbo v paketu), je lahko končna prevedena koda večja.
>
> ---
>
> ### Primer za razumevanje razlike:
>
> Recimo, da imamo naslednje ukaze:
>
> ```
> 1. A = B + C
> 2. D = E * F
> 3. G = A + D
> 4. H = I - J
> ```
>
> **Kako bi to obdelal **Superskalarni procesor**:
> *   Procesor pogleda Ukaz 1 in Ukaz 2. Ugotovi, da sta neodvisna (A ne potrebuje D in obratno).
> *   **V istem ciklu** izstavi Ukaz 1 (na ALU) in Ukaz 2 (na MUL enoti).
> *   Procesor pogleda Ukaz 3. Ugotovi, da je odvisen od Ukaza 1 (potrebuje A) in Ukaza 2 (potrebuje D). Zato Ukaz 3 čaka.
> *   Procesor pogleda Ukaz 4. Ugotovi, da je neodvisen od vseh ostalih.
> *   **V istem ciklu kot Ukaz 1 in 2**, ali celo prej, izstavi Ukaz 4 (na drugi ALU).
> *   Ko se Ukaz 1 in 2 končata in sta A in D na voljo, se Ukaz 3 izstavi.
>
> **Kdo je določil paralelnost?** *Procesor sam, med izvajanjem.* To je kot spretni kuhar, ki hkrati meša omako in seklja zelenjavo, ker ve, da lahko oboje dela neodvisno.
>
> **Kako bi to obdelal **VLIW procesor**:
> *   **Prevajalnik** analizira te ukaze *preden se program zažene*.
> *   Ugotovi, da sta Ukaz 1 in 2 neodvisna. Ugotovi tudi, da je Ukaz 4 neodvisen.
> *   Prevede jih v VLIW ukaze, ki izgledajo nekako takole:
>     ```
>     Urni cikel 1:  [  A = B + C  |  D = E * F  |  H = I - J  |  (prazno)  ]
>     Urni cikel 2:  [  G = A + D  |  (prazno)   |  (prazno)  |  (prazno)  ]
>     ```
>     (Predpostavljamo, da ima VLIW 4 reže, dve za aritmetiko, eno za množenje, eno za odštevanje, ali so generične).
> *   Ko procesor prejme "zelo dolg" ukaz iz Urnega cikla 1, preprosto izvrši vse tri operacije hkrati, ker ve, da so že vnaprej preverjene. Ne rabi nobenih vezij za preverjanje odvisnosti.
> *   Ko se konča Urni cikel 1 in so A, D in H že izračunani, se izvede Urni cikel 2.
>
> **Kdo je določil paralelnost?** *Prevajalnik, pred izvajanjem programa.* To je kot podroben recept, ki vam natančno pove, kaj morajo trije kuharji delati hkrati: "Kuhar 1: naribaj sir; Kuhar 2: nareži salamo; Kuhar 3: pripravi omako." Kuharji samo sledijo navodilom, ne razmišljajo o odvisnostih.
>
> ---
>
> ### Zaključek
>
> Tako superskalarni kot VLIW procesorji si prizadevajo za **paralelno izvajanje ukazov za doseganje CPI < 1**. Razlikujejo pa se v tem, **kdo nosi odgovornost** za določanje in upravljanje te paralelnosti:
>
> *   **Superskalarni procesorji:** Procesor (strojna oprema) to počne **dinamično** med izvajanjem. So zelo fleksibilni, a kompleksni.
> *   **VLIW procesorji:** Prevajalnik (programska oprema) to počne **statično** vnaprej. So preprostejši v strojni opremi, a manj fleksibilni in odvisni od zelo pametnih prevajalnikov.


### 5.5 Omejitve paralelizma na nivoju ukazov
Količina paralelizma v programih je omejena. Kljub idealnim razmeram, kjer ni strukturnih ali kontrolnih nevarnosti in so vsi dostopi do pomnilnika hitri, realni IPC (Instructions Per Cycle - število ukazov, izvršenih na urino periodo. To je obratna vrednost CPI) pade na precej nižje vrednosti.

### 5.6 Paralelizem na nivoju niti (Thread-level parallelism)
Paralelizem na višjem nivoju, kjer se izvrševanje razdeli v več neodvisnih poti (niti). Niti so neodvisne sekvence izvajanja znotraj enega programa ali procesa.
*   **Večnitnost (multithreading)**: Niti si delijo funkcionalne enote enega procesorja. Ena CPE hkrati obravnava več niti, bodisi z menjavanjem med njimi ali z vzporednim izvajanjem. Vsaka nit ima svoje stanje (registre, PC).
    *   **Časovna večnitnost (temporal multithreading)**: Preklapljanje med nitmi. Procesor preklaplja med nitmi ob določenih dogodkih (npr. zgrešitev predpomnilnika, I/O čakanje) ali po določenem času. Lahko je drobno-zrnata (vsako urino periodo, da se skrijejo zakasnitve (latency) posameznih niti) ali grobo-zrnata (ob daljšem čakanju, kar zmanjša režijske stroške preklapljanja).
    *   **Istočasna večnitnost (simultaneous multithreading, SMT)**: Pri večizstavitvenih procesorjih (npr. Intel Hyper-threading). Več niti se hkrati izvršuje na skupnih funkcionalnih enotah enega procesorja, kar izkorišča prazne cikle med ukazi različnih niti.
*   **Večjedrni procesorji (multicore)**: Več CPE (jeder) na istem čipu. Vsako jedro je samostojen procesor, ki lahko neodvisno izvaja svoj program, a si jedra delijo določene vire (npr. predpomnilnik višjih nivojev). Jedra si pogosto delijo PP L1, L2 in višje. So oblika tesno povezanih MIMD sistemov, kjer si procesorji delijo pomnilnik in imajo hiter dostop do njega.
*   **Večprocesorji (multiprocessorji)**: Računalniški sistemi z več procesorji.
    *   S skupnim pomnilnikom (shared memory): Večjedrni (UMA - uniform memory access) ali porazdeljen skupni pomnilnik (DSM, NUMA - non-uniform memory access). Pri UMA imajo vsi procesorji enako hiter dostop do kateregakoli dela skupnega pomnilnika. Pri NUMA pa procesorji imajo hitrejši dostop do svojega lokalnega pomnilnika kot do pomnilnika drugih procesorjev. Problem pomnilniške koherence. Zagotavljanje, da imajo vsi procesorji in predpomnilniki najnovejšo in enotno verzijo podatkov v skupnem pomnilniku.
    *   Multiračunalniki (več večjedrnih čipov, povezanih z omrežjem). Procesorji si ne delijo skupnega pomnilnika, ampak komunicirajo preko omrežja.
    *   Gruče (clusters). Skupina medsebojno povezanih neodvisnih računalnikov, ki delujejo kot en sistem.
    *   **SPMD (Single Program – Multiple Data)**: Pogost način delovanja na MIMD, kjer isti program teče na več procesorjih, pogojni stavki pa določajo, kaj se izvaja na posameznem procesorju. Vsi procesorji izvajajo isti program, vendar na različnih podatkih, kar je pogosto pri paralelnih aplikacijah.

### 5.7 Paralelizem na nivoju podatkov (Data-level parallelism)
**Arhitekture SIMD (Single Instruction, Multiple Data)**: Izvajajo en ukaz na več zbirkah operandov. En sam ukaz deluje na več elementih podatkov hkrati, kar je zelo učinkovito za operacije z velikimi nizi podatkov (npr. multimedija, grafika).
*   **Vektorski procesorji**: Vektorski ukazi, registri in funkcionalne enote. Posebej zasnovani procesorji z vektorskimi registri in funkcionalnimi enotami, ki omogočajo hitro izvajanje operacij na celih vektorjih podatkov z enim samim ukazom.
*   **(Multimedijske) razširitve nabora ukazov** (npr. x86: MMX, SSE, AVX). Dodatni ukazi, ki omogočajo SIMD operacije na standardnih procesorjih (npr. za obdelavo slik, zvoka).
*   **Grafične procesne enote (GPE)**, GPGPU: Visoka stopnja vzporednosti z velikim številom procesnih enot. Specializirani procesorji z ogromnim številom preprostih procesnih enot, optimiziranih za masivno podatkovno paralelno obdelavo (npr. grafika, strojno učenje).

### 5.8 Domensko specifične arhitekture (DSA)
Izvajajo specifične naloge zelo učinkovito (pospeševalniki/accelerators). Specializirana strojna oprema, zasnovana za izvajanje specifičnih nalog bistveno hitreje kot splošnonamenski CPE. Primer je **Tenzorska procesna enota (TPE, TPU)** podjetja Google, optimizirana za sklepanje v globokih nevronskih mrežah. Optimizirana za specifične tipe matričnih operacij, ki so temeljne za globoke nevronske mreže. Deluje kot koprocesor z matrično množilno enoto (MMU). Jedro TPU, ki izvede hitre operacije z matrikami.

## 6. Predpomnilniki (Cache)

**Lokalnost pomnilniških dostopov** je načelo, da so programi nagnjeni k dostopanju do podatkov in ukazov, ki so bili nedavno uporabljeni (časovna lokalnost), ali do podatkov in ukazov, ki so blizu nedavno uporabljenim (prostorska lokalnost). Omogoča uporabo **pomnilniške hierarhije**. Sistem pomnilnikov različnih hitrosti in kapacitet, ki delujejo skupaj, da pospešijo dostop do podatkov.

### 6.1 Pomnilniška hierarhija
* **Večnivojska pomnilniška hierarhija** 
  Hitrejši in dražji pomnilniki na višjih nivojih (bližje CPE), počasnejši in cenejši na nižjih -  (npr. SRAM za L1/L2, DRAM za GP, magnetni disk za pomožni pomnilnik). 
  Informacije se samodejno premikajo med nivoji. SRAM (statični RAM) je hitrejši, dražji in ne potrebuje osveževanja - L1, L2, L3 cache, DRAM (dinamični RAM) pa počasnejši in cenejši, a potrebuje osveževanje - RAM.

>[!|hidec]- SRAM
> Vsaka pomnilniška celica v SRAM-u uporablja **flip-flope**, ki so sestavljeni iz več tranzistorjev (običajno 4 do 6). Flip-flop je vezje, ki lahko stabilno drži eno od dveh stanj (0 ali 1), dokler je napajanje prisotno.
> Flip-flop obdrži svoje stanje, dokler je napajanje prisotno. Ne potrebuje nenehnega ponovnega zapisovanja, da bi obdržal podatke. Zato se imenuje "statičen".

>[!|hidec]- DRAM
> Vsaka celica v DRAM-u uporablja en kondenzator in en tranzistor, kondenzator shranjuje naboj, ki predstavlja logično 0 ali 1. Tranzistor pa deluje kot stikalo za dostop do  kondenzatorja.
> Branje in zapisovanje podatkov v kondenzator je počasnejše kot preklapljanje flip-flopov. Poleg tega je potreben proces osveževanja, ki vzame čas.
> Kondenzatorji sčasoma **puščajo naboj**. To pomeni, da se shranjena vrednost (naboj) sčasoma izgubi. Da bi ohranili podatke, je treba naboj nenehno osveževati – t.j., ga ponovno prebrati in zapisati nazaj, preden se izgubi. Ta proces se dogaja na tisoče krat na sekundo, zaradi česar se imenuje "dinamičen".

* **Glavni pomnilnik (GP) - RAM**: Danes izključno polprevodniški (DRAM). Njegova hitrost se povečuje bistveno počasneje od hitrosti CPE.
*   **Predpomnilnik (cache, PP)**: Majhen in hiter pomnilnik (SRAM), ki premošča vrzel v hitrosti med CPE in GP. Majhen, hiter vmesni pomnilnik, ki shranjuje kopije podatkov iz počasnejšega, večjega pomnilnika (npr. GP), da se zmanjša povprečni čas dostopa. Hrani podatke, ki so tudi v GP, kot podmnožico.

*   **Nivoji PP**: 
	* L1 (na CPE, manjši in hitrejši), 
	* L2 (na CPE, večji in počasnejši), 
	* L3 (ni na CPE, večji in počasnejši od L1/L2).
* Pri cevovodnih CPE je **L1** razdeljen na **ukazni** in **operandni PP** (nehomogeni PP). Ukazni predpomnilnik (Instruction Cache, I-Cache) shranjuje ukaze, operandni predpomnilnik (Data Cache, D-Cache) pa podatke. To omogoča sočasno prevzemanje ukazov in dostop do podatkov, kar izboljša pretok v cevovodu.
    *   **Zadetek (hit)**: Iskani naslov je v PP. Želeni podatek je v PP.
    *   **Zgrešitev (miss)**: Iskanega naslova ni v PP. Želenega podatka ni v PP, zato ga je treba dobiti iz počasnejšega pomnilnika. V tem primeru se blok besed (vključno z iskano besedo) prenese iz GP v PP. Blok besed (ali cache line) je najmanjša enota podatkov, ki se prenaša med PP in GP.
    *   **Verjetnost zadetka (hit ratio) H**: $H = N_p / N$, kjer je $N_p$ število zadetkov, $N$ pa skupno število dostopov. Delež dostopov, ki so zadetki. Običajno je $H > 0,95$.
    *   **Čas dostopa ($t_a$)**: $t_a = t_{PP} + (1-H)t_B$, kjer je $t_{PP}$ čas dostopa do PP, $1-H$ verjetnost zgrešitve, $t_B$ pa **zgrešitvena kazen (miss penalty)** – čas za prenos bloka. Dodatni čas, ki je potreben za pridobitev podatka po zgrešitvi predpomnilnika.
    *   **Uncacheable področja**: Deli GP, katerih besede se nikoli ne prenesejo v PP (npr. V/I registri). Deli pomnilnika, ki se ne predpomnijo, npr. registri V/I naprav, kjer je vedno treba prebrati dejansko stanje naprave, ne more biti kopija.
    *   **Zgradba PP**: Sestavljen je iz **kontrolnega** (naslovi, veljavni in umazani bit) in **pomnilniškega dela** (bloki/predpomnilniške vrstice/cache lines). Kontrolni del shrani naslovne oznake in statuse blokov, pomnilniški del pa shrani dejanske podatke.
        *   **Veljavni bit (V)**: Pove, ali je vsebina PP veljavna. Pove, ali je vsebina bloka v PP veljavna ali pa je bila spremenjena v GP.
        *   **Umazani bit (U)**: Označuje, ali je bila vsebina bloka spremenjena v PP. Če je umazani bit nastavljen, je treba blok ob zamenjavi zapisati nazaj v GP.
    *   **Vrste PP glede na omejitve pri preslikavi**:
        *   **Asociativni PP (APP)**: Vsak blok PP lahko sprejme katerokoli besedo iz GP. Vsak blok iz GP se lahko shrani v katero koli predpomnilniško vrstico. Ima največji $H$, a je zelo drag. Potrebuje kompleksno logiko za iskanje in primerjavo vseh oznak hkrati.
        *   **Set-asociativni predpomnilnik (SAPP)**: Razdeljen na S setov, vsak set je majhen APP. Kompromis med direktnim in asociativnim PP. Število blokov v setu E je stopnja asociativnosti. Za vsako besedo GP je vnaprej določeno, v katerega od setov se lahko preslika (na podlagi naslovnih bitov - **predpomnilniški indeks/cache index, CI**). Predpomnilniški indeks (cache index, CI) določa, v kateri 'set' se blok lahko shrani.
        *   **Direktni PP (Direct-mapped)**: Vsak set ima samo en blok ($E=1$). Vsak blok iz GP se lahko shrani samo v eno vnaprej določeno predpomnilniško vrstico. Enostaven za implementacijo, a z manjšim $H$.
    *   **Vpliv velikosti bloka (B)**: Večji bloki izboljšajo prostorsko lokalnost, a zmanjšajo časovno lokalnost in povečajo $t_B$. Večji bloki bolje izkoriščajo prostorsko lokalnost, a lahko povzročijo večjo zgrešitveno kazen in manjše število blokov v PP.
    *   **Strategije zamenjave blokov** (ob zgrešitvi in polnem setu): Algoritmi, ki določajo, kateri blok naj se odstrani iz PP, ko je le-ta poln in je potrebnega prostora za nov blok.
        *   **Naključna**: Enostavna.
        *   **LRU (Least Recently Used)**: Zamenja blok, do katerega najdalj ni bil narejen dostop. Izkorišča časovno lokalnost. To je kompleksno za implementacijo.
    *   **Pisanje v PP**: Način, kako se obravnavajo operacije pisanja v PP.
        *   **Pisanje skozi (write through)**: Vedno se piše v PP in GP. Enostavna, vsebini sta skladni. Vsako pisanje se izvede tako v PP kot tudi v GP hkrati.
        *   **Pisanje nazaj (write back)**: Piše se samo v PP, ob zamenjavi bloka pa se spremenjeni blok prenese v GP (če je umazani bit = 1). Hitrejše, manj prometa z GP. Pisanja se najprej izvedejo samo v PP, podatki pa se zapišejo v GP šele, ko je blok odstranjen iz PP (če je 'umazan').
        *   **Pisalni izravnalnik (write buffer)**: CPE shrani podatek, ki se bo vpisal v GP, in nadaljuje z delom. Majhen, hiter pomnilnik, ki začasno shrani podatke, namenjene za pisanje v GP, medtem ko CPE nadaljuje z delom.
        *   **Pisalna zamenjava (write allocate)**: Ob pisalni zgrešitvi se blok prenese v PP (običajno pri pisanju nazaj). Ob pisalni zgrešitvi se celoten blok najprej prebere iz GP v PP, nato pa se vanj zapiše spremenjena vrednost.
        *   **Pisanje naokrog (write around, no write allocate)**: Ob pisalni zgrešitvi se blok zamenja samo v GP (ne v PP). Ob pisalni zgrešitvi se podatki zapišejo direktno v GP, ne da bi se blok najprej naložil v PP. Uporabno za pisanje v velike nize podatkov, ki ne bodo kmalu ponovno prebrani.
    *   **Vrste zgrešitev**: Različni razlogi, zakaj se zgodi zgrešitev v PP.
        *   **Obvezne (compulsory misses, OZ)**: Pri prvem dostopu do bloka. Prvi dostop do bloka, ki še ni bil v PP.
        *   **Velikostne (capacity misses, VZ)**: Zaradi omejene velikosti PP. PP je premajhen, da bi lahko shranil vse aktivne bloke, kar povzroči, da se stari bloki izrinejo, preden se ponovno potrebujejo.
        *   **Konfliktne (conflict misses, KZ)**: Zaradi zamenjave blokov, ki se preslikajo v isti set (pri SAPP in direktnih PP). Pojavijo se v direktnih in set-asociativnih PP, ko se več različnih GP blokov, ki se preslikajo na isto mesto v PP, neprestano zamenjuje.
    *   **Skladnost PP (cache coherency)**: Problem, ko se vsebina bloka v PP razlikuje od vsebine v GP ali drugih PP. Ključni problem v multiprocesorskih sistemih, kjer več CPE ali naprav dostopa do istega pomnilnika in imajo vsak svoj PP. Potrebno je zagotoviti, da so vse kopije istega podatka usklajene. Treba je zagotoviti, da ne pride do napak.
    *   **Vpliv PP na hitrost CPE**: Zgrešitve v PP lahko bistveno upočasnijo delovanje CPE.
    *   **Načini za zmanjševanje zgrešitvene kazni**:
        *   **Vnaprejšnji prevzem bloka (block prefetch)**.
        *   **Neblokirajoči PP (nonblocking cache)**: Med zamenjavo bloka PP deluje naprej in CPE lahko špekulativno izvršuje naslednje ukaze (hit under miss). CPE lahko nadaljuje z izvajanjem ukazov, tudi če pride do zgrešitve v PP, dokler se potrebni podatki ne naložijo. To izboljša izkoriščenost CPE.

## 7. Pomnilniki

### 7.1 Lastnosti pomnilnikov
1.  **Cena**: Izraža se v $/GB$, SRAM je najdražji, magnetni disk najcenejši.
2.  **Hitrost dostopa**:
    *   **Čas dostopa ($t_a$)**: Čas od pridobitve naslova do pojavitve podatkov (pri branju). Latenca – čas, ki je potreben za pridobitev podatka.
    *   **Čas cikla ($t_c$)**: $t_c = t_a + \text{čakanje}$ (pri DRAM). Minimalni čas med dvema zaporednima dostopoma do pomnilnika.
    *   **Hitrost dostopa (access rate)**: $b_a = 1/t_c$.
    *   DRAM: $t_a \approx 50$ ns, $t_c \approx 60$ ns. SRAM: $t_a \approx 0,5 - 2,5$ ns. Magnetni disk: $\approx 100.000$-krat nižja ($ms$).
3.  **Način dostopa**:
    *   **Naključni dostop (random access)**: Čas dostopa je konstanten in neodvisen od prejšnjih naslovov (RAM: DRAM, SRAM). Do katerekoli pomnilniške lokacije lahko dostopamo v enakem času. Pri DRAM obstajajo hitrejši načini za zaporedne dostope (page mode, burst mode). To so hitrejši načini dostopa do zaporednih podatkov v DRAM, ki izkoriščajo notranjo organizacijo DRAM.
    *   **Zaporedni dostop (serial access)**: Čas dostopa je odvisen od prejšnjega naslova (npr. magnetni trak). Čas dostopa je odvisen od trenutne pozicije glave in ciljne pozicije (npr. magnetni trak).
    *   **Krožni dostop (rotational access)**: Posebna vrsta zaporednega dostopa (npr. magnetni disk s fiksnimi glavami). Dostop, ki vključuje vrtenje medija (npr. HDD).
    *   **Kombinacija zaporednega in krožnega dostopa** (npr. magnetni in optični diski s premičnimi glavami).
    *   **Asociativni pomnilniki (CAM, Content Addressable Memory)**: Dostop preko (dela) vsebine. Pomnilnik, kjer se podatki dostopajo na podlagi vsebine, ne naslova. Uporablja se v predpomnilnikih (asociativni del), usmerjevalnikih, itd. Primerjava je paralelna in zelo hitra, a so dragi in majhni.
4.  **Spremenljivost**:
    *   **Bralni pomnilniki (ROM – Read Only Memory)**: Lahko se bere, vpis ni možen. Vsebina je obstojna. Vsebina se vanje zapiše enkrat in je nato trajno shranjena, ne da bi potrebovala napajanje.
    *   **Programirljivi bralni pomnilniki (Programmable ROM - PROM)**: OTP (One Time Programmable), EPROM (Erasable PROM, UV-svetloba), EEPROM (Electrically Erasable PROM), Flash. Različne tehnologije, ki omogočajo enkratno ali večkratno programiranje ROM-a. Uporabljeni za zagonske programe (BIOS).
    *   **Bralno-pisalni pomnilniki (Random Access Memory, RAM)**: Z enako lahkoto se bere in piše. Pomnilnik, ki omogoča enostavno in hitro branje ter pisanje.
5.  **Obstojnost**:
    *   **Destruktivno branje**: Pri DRAM se ob branju kondenzatorji praznijo, zato jih je treba ponovno nabiti. Ko se prebere celica DRAM, se izprazni njen naboj, zato je treba celico takoj osvežiti (ponovno napolniti).
    *   **Dinamično shranjevanje**: Pri DRAM se kondenzatorji praznijo s časom, zato jih je treba osveževati (refresh). Pri DRAM se kondenzatorji praznijo s časom, zato je potrebno redno osveževanje (refresh) vsebine. Od tod ime dinamični RAM; SRAM ne potrebuje osveževanja.
    *   **Izpad napajanja**: Obstojni pomnilniki (nonvolatile) ohranijo vsebino, neobstojni (volatile) pa je izgubijo.
6.  **Zanesljivost**: Polprevodniški pomnilniki (solid state) so zanesljivejši od magnetnih diskov. Možne so **mehke napake** (kozmični žarki, popravljive z ECC) in **trde napake** (trajna okvara celice). Mehke napake so začasne in neponovljive napake, ki jih lahko popravimo (npr. ECC – Error Correcting Code). Trde napake so trajne napake v strojni opremi.

### 7.2 Zaščita glavnega pomnilnika
Operacijski sistem (OS) potrebuje mehanizme za **zaščito programov in OS** pred medsebojnimi posegi. Zaščita programov in OS zagotavlja, da programi ne morejo dostopati do pomnilniških območij, ki ne pripadajo njim ali operacijskemu sistemu, kar preprečuje zrušitve ali varnostne luknje.
*   **Najpreprostejši mehanizem**: Par registrov za spodnjo in zgornjo mejo naslova, ki pripada programu. Slabosti: programi morajo zasedati zvezen prostor, vse besede so enako zaščitene.
*   **Boljše rešitve**: Uporabljajo **bloke ali strani (pages)** z zaščitnimi ključi. Pomnilnik je razdeljen na fiksne velikosti blokov/strani, kar omogoča bolj granularno zaščito in lažje upravljanje pomnilnika.
*   **Privilegiran način delovanja (privileged mode)**: Dostop do določenih storitev (npr. V/I) je dovoljen le v tem načinu. Način delovanja procesorja, ki omogoča dostop do vseh sistemskih virov in ukazov. Jedro OS deluje v tem načinu. Prehod na višji nivo je možen preko sistemskih klicev. Sistemski klici so standardni vmesnik, ki programom v uporabniškem načinu omogoča varen dostop do privilegiranih funkcij jedra OS (npr. dostop do datotek, V/I naprav).
*   **Pohitritve dostopa do GP**: Načini za izboljšanje hitrosti prenosa podatkov med GP in CPE.
    *   **Širše podatkovne poti**. Povečanje števila bitov, ki se prenašajo hkrati.
    *   **Pomnilniško prepletanje (memory interleaving)**: GP je razdeljen na $m$ samostojnih modulov (bank), kar omogoča $m$ istočasnih dostopov. Razdelitev pomnilnika na več neodvisnih bank, ki se lahko dostopajo hkrati. To omogoča sočasno branje/pisanje in povečuje pasovno širino pomnilnika.

### 7.3 Organizacija glavnega pomnilnika
GP je videti kot enodimenzionalno zaporedje pomnilniških besed, vsaka z enoličnim naslovom.
*   **Pomnilniška beseda**: Najmanjše število bitov s svojim naslovom (običajno 1B ali 8 bitov). Najmanjša enota pomnilnika, ki jo je mogoče nasloviti.
*   **Pomnilniški naslov**: Binarno število, dolžina naslova določa velikost pomnilniškega prostora ($2^m$ besed za $m$-bitni naslov). Edinstven identifikator vsake pomnilniške besede. Povečanje dolžine naslova je zelo težko.
*   **Sestavljene pomnilniške besede**: Polbeseda (16 bitov), beseda (32 bitov), dvojna beseda (64 bitov). Več bajtov, ki se obravnavajo kot ena logična enota (npr. 16-bitno število). Za večino računalnikov je potrebna **poravnanost**. Sestavljene besede morajo biti shranjene na naslovih, ki so večkratniki njihove velikosti, za optimalno delovanje.

### 7.4 Tehnologija polprevodniških pomnilnikov
*   **DRAM (Dinamični RAM)**:
    *   **Zgradba**: Vključuje vrstični in stolpični dekodirnik (vezja, ki pretvorijo naslov v fizično lokacijo v matriki celic), pomnilno matriko in tipalne ojačevalnike (vezja, ki zaznajo majhno napolnjenost kondenzatorjev in jo ojačajo do logične ravni).
    *   **Pomnilna celica**: Sestavljena iz kondenzatorja (shrani naboj) in stikalnega tranzistorja (MOS). Osnovna enota, ki shrani en bit.
    *   **Pomnilniški dostop**: Bitne linije se prednabijejo, podamo naslov vrstice (RAS'), vsebina vrstice gre na tipalne ojačevalnike, shranijo se v register vrstice, podamo naslov stolpca (CAS'), nato dobimo/vpišemo bit.
    *   **Naslovno multipleksiranje**: Naslov vrstice in stolpca sta na istih pinih za zmanjšanje števila priključkov. Na istem naboru pinov se najprej pošlje naslov vrstice (RAS'), nato pa naslov stolpca (CAS'). To zmanjša število pinov na čipu.
    *   **SDRAM (Sinhronski DRAM)**: Sinhronizirani s sistemsko uro, imajo 3-stopenjski cevovod. Sinhroniziran z urinim signalom procesorja, kar omogoča cevovodno delovanje. **DDR (double data rate)**. Prenese podatke ob obeh robovih ure (naraščajočem in padajočem), s čimer podvoji pasovno širino.
*   **SRAM (Statični RAM)**: Pomnilna celica je zapah, ki ne potrebuje osveževanja. Uporablja flip-flope (zapahi) za shranjevanje bitov. Ne potrebuje osveževanja, a je dražji in večji od DRAM.
*   **ROM (Read Only Memory)** celica: Prevodnost tranzistorja določa vrednost bita. Vrednost bita je fiksirana ob izdelavi (ali programiranju) s prisotnostjo ali odsotnostjo tranzistorja.
*   **Bliskovni pomnilnik (Flash memory)**: Vrsta programirljivega ROMa z obstojno vsebino. Celica ima "plavajočo plast", ki shrani naboj in vpliva na prevodnost tranzistorja. Vrsta EEPROM-a, ki omogoča brisanje in programiranje v blokih, ne posameznih bitih. Plavajoča plast je poseben izoliran tranzistor znotraj pomnilniške celice, ki lahko zadrži električni naboj in s tem shrani bit informacije.

## 8. Podprogrami v RISC-V

**Podprogram** je del programa, ki opravlja specifično nalogo na osnovi parametrov. Samostojen del kode, ki ga lahko večkrat pokličemo in izvede določeno nalogo. Pomaga pri modularnosti in ponovni uporabi kode. Imenujemo ga tudi **procedura** ali **funkcija** (v C jeziku).

### 8.1 Proces klica podprograma
Pri klicu podprograma so potrebni naslednji koraki:
1.  **Klicatelj (caller) postavi parametre** nekam, kjer podprogram (klicani/callee) lahko dostopa do njih.
2.  **Klicatelj prenese kontrolo** na podprogram.
3.  **Podprogram pridobi potrebne pomnilniške vire**.
4.  **Podprogram izvede želeno nalogo**.
5.  **Podprogram da rezultat** nekam, kjer ga lahko klicatelj dobi.
6.  **Vrnitev na naslednji ukaz klicatelja**.

### 8.2 Sklad
**Sklad** je podatkovna struktura (LIFO), ki je najbolj primerna za shranjevanje (spill) registrov v pomnilnik. Spill registrov pomeni shranjevanje vrednosti registrov iz CPE v pomnilnik (na sklad), ko je v registrih premalo prostora.
*   Za delo s skladom potrebujemo **skladovni kazalec (SP)**, ki kaže na vrh sklada. Register, ki vedno kaže na trenutni vrh sklada. Pri RISC-V ima to vlogo **register x2 (sp)**.
*   Sklad se uporablja za **shranjevanje povratnega naslova**, **prenos parametrov**, **shranjevanje lokalnih spremenljivk** in **shranjevanje registrov**.
*   **Dogovor o klicu podprogramov (calling convention)** za RISC-V določa, naj sklad narašča v smeri padajočih naslovov (to pomeni, da se sklad širi proti nižjim pomnilniškim naslovom, kar je pogosto v RISC arhitekturah) in naj skladovni kazalec kaže na zadnji podatek na skladu.
*   RISC-V nima direktnih ukazov PUSH/POP, ampak se ti izvedejo kot zaporedje dveh ukazov (npr. `addi sp, sp, -4` in `sw reg, 0(sp)`).

### 8.3 Uporaba registrov pri klicih podprogramov (ABI)
**ABI (Application Binary Interface)** je standard, ki določa, kako se programi v strojni kodi medsebojno kličejo, vključno z uporabo registrov in sklada.
*   Registri **x10-x17 (a0-a7)** se uporabljajo za **parametre (argumente)** procedur.
*   Registra **x10-x11 (a0-a1)** se uporabljata tudi za **vrnjene vrednosti**.
*   Ukaz **JAL** shranjuje povratni naslov v **register x1 (ra, return address)**.
*   Za vrnitev se uporablja indirektni skok **JALR** (Jump and Link Register, omogoča skok na naslov, ki je shranjen v registru, kar je potrebno za vrnitev iz podprograma) ali psevdo-ukaz `ret`. Psevdo-ukaz `ret` se prevede v JALR x0, x1, 0 (ali JALR ra, 0(ra)), kar vrne kontrolo na naslov v ra.
*   **Register x8 (s0/fp)** služi kot **kazalec na okvir (frame pointer)**, ki si zapomni stanje SP pred shranjevanjem argumentnih registrov. Uporablja se za lažji dostop do lokalnih spremenljivk in argumentov na skladu, tudi če se SP spreminja.
*   RISC-V določa dve skupini registrov glede na ohranjanje vrednosti med klici:
    *   **Začasni registri (caller-saved)**: **x5-x7 (t0-t2)** in **x28-x31 (t3-t6)**. Klicani podprogram jih ne ohrani, klicatelj mora shraniti, če jih potrebuje po klicu. Njihova vsebina se lahko spremeni med klicem podprograma, zato jih mora klicatelj, če jih še potrebuje, shraniti na sklad pred klicem in jih obnoviti po klicu.
    *   **Shranjeni registri (callee-saved)**: **x8 (s0/fp), x9 (s1)** in **x18-x27 (s2-s11)**. Klicani program jih mora shraniti in obnoviti, če jih uporablja. Klicani podprogram *mora* ohraniti njihovo vrednost (s shranjevanjem na sklad na začetku in obnovo na koncu), če jih uporablja.
*   **Globalni kazalec (gp, x3)**: Kaže na statično območje podatkov. Kaže na statično območje podatkov, ki je dostopno vsem delom programa, pogosto se uporablja za globalne spremenljivke.
*   **Okvir procedure (frame)**: Del sklada, ki hrani shranjene registre in lokalne spremenljivke procedure. Del sklada, ki je dodeljen določeni instanci podprograma in vsebuje njene lokalne podatke, shranjene registre in parametre.
*   **Kopica (heap)**: Segment za dinamično alokacijo podatkov (npr. povezani seznami, drevesa). Območje pomnilnika za dinamično alokacijo podatkov. Velikost kopice se lahko med izvajanjem programa spreminja. Za razliko od sklada, ki se samodejno upravlja, kopico upravlja programer (npr. z `malloc` in `free`). Raste v nasprotni smeri kot sklad. C-funkciji sta `malloc()` in `free()`.

## 9. Sistemski ukazi

Sistemski ukazi spreminjajo parametre delovanja računalnika in nadzorujejo njegovo delovanje. Sistemski ukazi so ukazi, ki so namenjeni za komunikacijo z operacijskim sistemom, upravljanje pomnilnika, obvladovanje prekinitev in nastavitev privilegiranosti.

### 9.1 Prekinitve in pasti
*   **Prekinitev (interrupt)**: Dogodek (običajno zunanji, npr. V/I naprava), ki povzroči, da CPE začasno preneha izvajati tekoči program in preide na **prekinitveni servisni program (PSP)**. Zunanji, asinhroni dogodek, ki ga sproži strojna oprema ali programska oprema, da prekine normalno izvajanje programa in zahteva pozornost CPE. PSP je posebna rutina v operacijskem sistemu, ki obravnava specifično prekinitev ali past.
*   **Past (trap)**: Posebna vrsta prekinitve, ki jo zahteva sama CPE ob nenavadnem dogodku ali na zahtevo programerja (npr. aritmetični preliv, napaka strani, sistemski klici). Pasti pridejo od znotraj. Notranji, sinhroni dogodek, ki ga sproži sam procesor zaradi napake ali posebne programske zahteve (npr. sistemski klic).
*   **Terminologija** je zmedena in se razlikuje med arhitekturami (RISC-V, x86, ARM).
*   **Faktorji obravnave prekinitev/pasti**:
    1.  **Kdaj CPE reagira**: Običajno po izvrševanju tekočega ukaza.
    2.  **Nevidnost prekinitev**: Stanje CPE (registrov) mora ostati enako kot pred prekinitvijo. Pomeni, da mora PSP shraniti in obnoviti stanje CPE, da se ob vrnitvi v prekinjen program zdi, kot da prekinitve sploh ni bilo.
    3.  **Naslov PSP**: Lahko se določi s programskim izpraševanjem (polling) ali z **vektorskimi prekinitvami** (naprava pošlje naslov PSP). Programsko izpraševanje (polling) pomeni, da CPE redno preverja stanje naprav, kar je neučinkovito. Pri vektorskih prekinitvah naprava direktno pove CPE, kateri PSP naj se izvede, kar je hitrejše.
    4.  **Prioriteta**: Če je več prekinitvenih zahtev, je potrebna prioriteta. Določa, katera prekinitev se obravnava prej, če jih je več hkrati. Omogoča **vgnezdene prekinitve (nested interrupts)**.
    5.  **Potrjevanje prekinitve**: Potrebno je, da naprava spusti prekinitveni vhod (programsko ali strojno).
*   **Prekinitve in pasti pri cevovodu**:
    *   **V/I prekinitve**: Običajno cevovod izvrši že prevzete ukaze do konca.
    *   **Programske pasti**: Poseben brezpogojni skok.
    *   **Pasti med izvrševanjem ukaza** (najtežje): Zgodijo se na sredi ukaza, CPE ga mora ustaviti, izvršiti servisni program in ga ponovno začeti. To je najkompleksnejše za obravnavo, saj je treba stanje CPE shraniti točno sredi ukaza in ga nato po obravnavi pasti obnoviti. Primeri: napaka strani (poskus dostopa do pomnilniške strani, ki ni v fizičnem pomnilniku, ali pa ni dovoljen dostop), nedefiniran ukaz, preliv, neporavnan operand, zaščita pomnilnika.
*   **Arhitektura nivojev privilegiranosti v RISC-V**: Hierarhični sistem, ki ločuje dostop do sistemskih virov na podlagi trenutnega načina delovanja procesorja.
    *   **4 nivoji privilegiranosti**: User/App. (U) - najnižji nivo, za običajne programe, Supervisor (S) - za operacijski sistem (jedro), Reserved, Machine (M) - najvišji nivo, za zagonski sistem in virtualizacijo.
    *   **M-mode**: Lahko vse.
    *   **S-mode**: Za OS.
    *   Privilegirani ukazi se lahko izvajajo le na dovolj visokem nivoju.
    *   Prehod na višji nivo je možen preko sistemskih klicev.
    *   **CSR (Control and Status Registers)**: 12-bitni naslov določa enega od 4096 registrov. To so posebni registri, ki shranjujejo in nadzorujejo stanje in konfiguracijo procesorja in njegovega okolja.
    *   **Statusni register mstatus**: Najpomembnejši CSR, obravnava pasti, omogoča prekinitve, konfiguracijo. Eden ključnih CSR registrov, ki shranjuje trenutno stanje procesorja, vključno z omogočanjem prekinitev, nivojem privilegiranosti in drugimi sistemskimi zastavicami.
    *   **Obdelava pasti (HW in SW faza)**: Vključuje shranjevanje statusa, spremembo nivoja privilegiranosti, skok na rokovalnik in nato obnovo stanja. To je dvodelna obdelava: strojna oprema shrani osnovno stanje in preusmeri, programska oprema (PSP) pa obravnava dejanski dogodek.
*   **Izvori prekinitev**: Zunanje prekinitve (EI), prekinitve časovnika (TI), SW prekinitve (SI), prekinitev preliva lokalnega števca (LCOFI).
*   **Prekinitveni krmilnik PLIC (Platform level interrupt controller)**: Sprejema prekinitve, odloča katero jedro obvestiti, jedro "prizna" in nato "upokoji" prekinitev. Strojna komponenta, ki upravlja z zunanjimi prekinitvami v RISC-V sistemih. Agregira prekinitve iz različnih virov in jih posreduje ustreznim jedrom CPE na podlagi prioritete. Priznanje (claim) signalizira, da je jedro začelo obravnavati prekinitev, upokojitev (complete) pa, da je obravnava končana.

### 9.2 Preostali sistemski ukazi (ponovitev)
*   **FENCE, FENCE.I, ECALL, EBREAK**.

## 10. Vzporedni (paralelni) računalniki

Mnogi problemi dovoljujejo istočasno oz. paralelno izvajanje več operacij. Flynn-ova klasifikacija (1966) uporablja 2 kriterija:
*   **Tok ukazov (instruction stream)**: Koliko ukazov se izvršuje naenkrat.
*   **Tok podatkov (data stream)**: Koliko ponovitev operandov en ukaz obdeluje naenkrat.

### 10.1 Flynn-ova klasifikacija računalnikov
*   **SISD (Single Instruction stream, Single Data stream)**: Izvajajo en ukaz na eni zbirki operandov (npr. klasični von Neumannovi računalniki, vključno z vektorskimi).
*   **SIMD (Single Instruction stream, Multiple Data stream)**: Izvajajo en ukaz na več zbirkah operandov. Imajo eno kontrolno enoto in N ALE ter N množic registrov. Učinkovito za operacije z velikimi matricami, grafiko, multimedijo.
*   **MISD (Multiple Instruction stream, Single Data stream)**: Ne obstajajo v praksi (najbližje so "stream" procesorji). Teoretična kategorija, kjer več ukazov obdeluje iste podatke (npr. redundantni sistemi).
*   **MIMD (Multiple Instruction stream, Multiple Data stream)**: Izvajajo več ukazov na več zbirkah operandov. Najbolj splošna in razširjena oblika paralelnih računalnikov, ki omogoča visoko stopnjo fleksibilnosti. Vključujejo **multiprocesorje** in **multiračunalnike**.
    *   **Večjedrne (multicore)** računalnike lahko štejemo med tesno povezane MIMD.
    *   **SPMD (Single Program – Multiple Data)**: Pogost način delovanja na MIMD, kjer isti program teče na več procesorjih, pogojni stavki pa določajo, kaj se izvaja na posameznem procesorju.
*   Zmogljivost se meri v **FLOPS (Floating Point Operations Per Second)**: GFLOPS ($10^9$), TFLOPS ($10^{12}$), PFLOPS ($10^{15}$). FLOPS je mera zmogljivosti računalnika pri izvajanju operacij s plavajočo vejico.

### 10.2 Amdahlov zakon
Povečanje hitrosti računalnika pri pohitritvi določenega dela operacij je omejeno z **zaporednim delom programa** ($f$). To je tisti del programa, ki se ne more paralelizirati in ga je treba vedno izvajati zaporedno.
$$ S(N) = \frac{1}{f + \frac{1-f}{N}} $$
kjer je $N$ faktor pohitritve vzporednega dela. Amdahlov zakon kaže, da tudi pri neskončni paralelnosti ni mogoče preseči določene meje hitrosti, če obstaja zaporedni del. To pomeni, da je za zares visoke pohitritve ključno minimizirati zaporedni del programa.

### 10.3 Gustafsonov zakon
Poudarja, da lahko paralelni računalniki rešujejo **večje probleme**. Namesto da bi pohitritev merili na fiksni velikosti problema, Gustafsonov zakon predpostavlja, da se velikost problema poveča z dostopnostjo več procesorjev. Če se velikost problema povečuje, se zaporedni del ($f$) zmanjšuje in pohitritev lahko postane skoraj linearna ($S(N) \approx N$). To je bolj optimističen pogled na paralelizem, saj pravi, da lahko z več procesorji rešujemo bistveno večje in kompleksnejše probleme.

---