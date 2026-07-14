
### Organizacija podatkov

Za shranjevanje podatkovnih baz uporabljamo koncept **datotek**, **strani** in **zapisov**.
Neka PB je lahko razdeljena med več datotek. Že sama tabela je lahko razdeljena med več datotek. Vsaka datoteka vsebuje **strani** te pa vsebujejo neko vnaprej določeno količino zapisov.

Tak sistem je bil implementiran ker je branje podatkov z diska izredno počasno. Zaradi tega nočemo prebirati vsak zapis posebej ampak več hkrati. V ta namen obstajajo strani. Strani so bloki zapisov ki jih SUPB naloži v pomnilnik naenkrat. *Zaradi rega stranem kdaj rečemo tudi bloki*.

V pomnilniku potem iščemo, vstavljamo in brišemo podatke.

Strani imajo ponavadi določeno strukturo. Začnejo se z **glavo** v kateri so ponavadi zapisani neki metapodatki kot so ID strani, ID datoteke_, prosti prostor, kazalce na sosednje strani,... 
Na koncu strani se pri nekaterih implementacijah ki to potrebujejo shrani tudi tabela kazalcev ki kažejo na različne zapise. Recimo da imamo nek zapis shranjen v neki strani na fizični lokaciji 100.  Predpostaivmo da imamo ustvarjeno drevesno strukturo za lažje iskanje podatkov, torej preverja ali so podatki levo ali desno od našega (recimo na 50 ali 150). Sedaj si predstavljamo da zbrišemo nek podatek ki je na majhnem mestu (recimo 10) to pomeni da bomo vse podatke večje od njega morali prestaviti za 10 nazaj. Če bi shranili offset bi morali v temu drevesu posodobiti vsako vozlišče  z novim offsetom. Ker za vsako vozlišče potrebujemo 1 stran (več o tem pri indeksiranju) bo to preveč dostopov do diska. (Vsako stran je treba naložiti v pomnilnik).

*Vse podatke premikamo nazaj da se izognemo fragmentaciji (če imamo podatke spremenljive dolžine nastanejo različne velike lukjnje zato premikamo podatke dol da jih zapolnimo)*. 

 Če offsetu za zapis dodelimo ključ (recimo "1,2,3,...") potem v drevesu povsod ostane "1,2,3,..." in spremenimo le offset v tabeli kazalcev kjer vsak ključ kaže na $x-10$. Ker je tabela kazalcev shranjena v **samo 1 strani** je to veliko bolj efektivno.

Poznamo več **ureditev podatkov** oz. zapisov.

**Kopica** je ureditev kjer so zapisi dodani v datoteko oz. strani v istem vrstnem redu kot so dodani v tabelo. Dodajajo se na konec. Vstavljanje je hitro a iskanje postane zato počasno, saj moramo linearno preiskati vsak zapis. Če brišemo podatke je občasno potrebna reorganizacija zaradi praznih mest po brisanju.

**Urejene datoteke** so tiste kjer so zapisi urejeni po nekem polju oz. stolpcu. Vsakič ko se doda zapis se datoteka uredi. Omogoča binarno iskanje v logaritmičnem času. Vstavljanje je počasno saj moramo ohranjevati red. Ponavadi se rešuje z implementacijo overflow strani. To so strani oz. bloki, ki shranijo podatke kot so vnešeni - torej neurejeno in na neki točki, ko se upočasni dodajanje informacij ali je nek downtime, uredimo celotno datoteko. Brisanje na podoben način zahteva reorganizacijo.

**Razpršene datoteke** temeljijo na zgoščevalni (hash) funkciji ki vsak zapis preslika na pripadajočo stran. To pomeni da za iskanje lahko ugotovimo v katero stran je bil preslikan zapis in nato samo to preiščemo linearno. Če se zgodi da hash funkcija preobremeni kakšno stran ponavadi razširimo funkcijo ali pa dodamo več povezanih oz. overflow strani in potem linearno iščemo več takih strani. 
**Niso najbolj primerna za iskanje po intervalih oz. vzorcih**.




### Indeksiranje

Indeksi so pomožne strukture za hitrejše iskanje, ločene od glavnih podatkov. Indeksna datoteka vsebuje pare (iskalni ključ, kazalec na podatek).
*   **Vrste indeksov:** Ločimo primarne (na ključu, po katerem je datoteka urejena) in sekundarne. Indeksi so lahko redki (kazalec na stran) ali gosti (kazalec na vsak zapis).
*   **Indeks gruče (clustered):** Fizična urejenost podatkov ustreza indeksu.
*   **Sestavljeni indeksi:** Ključ je kombinacija več polj.

**Drevesne strukture**
Za učinkovito iskanje in vzdrževanje urejenosti se uporabljajo drevesa:
*   **ISAM (Indexed Sequential Access Method):** Statična struktura, ki kombinira indeks in urejene podatke. Ob polnitvi strani uporablja dodatne (overflow) strani, kar sčasoma zmanjša učinkovitost.
*   **B+ drevo:** Dinamična, uravnotežena struktura in industrijski standard. Vsa iskanja imajo enako dolžino poti od korena do lista. Drevo se avtomatsko prilagaja (cepi in združuje vozlišča) ob vstavljanju in brisanju, kar zagotavlja konstantno učinkovitost. Listi so povezani v verigo za hitro zaporedno branje.

**Specializirani indeksi in optimizacija**
*   **Bitni indeksi:** Uporabni za polja z malo različnimi vrednostmi (npr. spol). So kompaktni in omogočajo hitre logične operacije nad množicami zapisov.
*   **Stični indeksi (Join index):** Povezujejo tabele preko skupnih polj, uporabno v podatkovnih skladiščih.
*   **Gruče (Clusters):** Fizično združevanje zapisov iz različnih tabel, ki se pogosto uporabljajo skupaj (npr. preko tujega ključa), da se zmanjša število dostopov do diska.

***

# Osnovni koncepti shranjevanja podatkov in indeksiranja

## 1. Osnovni koncepti shranjevanja podatkov

Podatkovna baza na sekundarnem pomnilniku (običajno trdi disk) ni enovita struktura, temveč je organizirana v **eno ali več datotek (files)**. Vsaka od teh datotek je sestavljena iz določenega števila **zapisov (records)**, ki so osnovne enote podatkov. Ti zapisi so nadalje razčlenjeni na **polja (fields)**. V kontekstu načrtovanja podatkovnih baz zapisi običajno predstavljajo posamezne entitete (npr. določenega zaposlenega), polja pa njihove atribute (npr. ime, priimek, plača).

Pri delu s sistemom za upravljanje podatkovnih baz (SUPB) ločimo med dvema pogledoma na te podatke:
*   **Logični pogled:** To je pogled, ki ga vidi uporabnik ali aplikacija, kjer so podatki predstavljeni kot tabele.
*   **Fizični pogled:** To je način, kako so podatki dejansko zapisani na disku v obliki bitov in bajtov.

Ko uporabnik od SUPB zahteva specifičen zapis (npr. zapis pod šifro A10), sistem najprej izvede **preslikavo logičnega zapisa v fizičnega**. Nato SUPB poišče ustrezni fizični zapis na sekundarnem pomnilniku in ga prepiše v **primarni pomnilnik oziroma medpomnilnik (buffer)**, kjer se lahko obdela. Pomembno je razumeti, da razmerje med fizičnim in logičnim zapisom ni vedno 1:1. Fizični zapis predstavlja osnovno enoto prenosa med diskom in primarnim pomnilnikom in ustreza konceptu **strani (page)**. Ena stran lahko vključuje več logičnih zapisov, v primeru zelo velikih logičnih zapisov pa se lahko en logični zapis razteza čez več fizičnih strani.

---

## 2. Vrste datotečnih organizacij

**Datotečna organizacija** se nanaša na fizično urejenost podatkov v zapise in strani na sekundarnem pomnilniku. SUPB uporablja različne **metode dostopa (access methods)**, ki določajo korake za iskanje ali shranjevanje zapisov, te metode pa so neposredno odvisne od uporabljene datotečne organizacije.

Poznamo tri osnovne vrste organizacij:
1.  **Kopica ali neurejena datoteka (heap file):** Zapisi so shranjeni v nedefiniranem vrstnem redu.
2.  **Zaporedno urejena datoteka (sequential file):** Zapisi so urejeni po vrednosti določenega polja.
3.  **Razpršena datoteka (hash file):** Zapisi so razporejeni z uporabo hash funkcije.

### 2.1 Neurejene datoteke (Kopica)
To je najenostavnejša oblika organizacije, kjer se zapisi shranjujejo po vrstnem redu, kot so bili dodani v sistem. Vsak nov zapis se preprosto doda na **zadnjo stran datoteke**. Če na zadnji strani ni več dovolj prostora, sistem ustvari novo stran.
*   **Prednosti:** Dodajanje je izjemno učinkovito, saj sistemu ni treba računati ali preverjati, kam vstaviti podatek, zato je ta oblika primerna za **masovni vnos podatkov**.
*   **Slabosti:** Iskanje je neučinkovito, saj zahteva **linearno pregledovanje** vseh zapisov, dokler ne najdemo iskanega. Poleg tega se prostor slabo izkorišča, ker brisani zapisi puščajo praznine, zato je treba takšne datoteke občasno **reorganizirati**.

### 2.2 Urejene datoteke
V urejenih datotekah so zapisi fizično razvrščeni po enem ali več poljih. Takšna ureditev prinaša bistveno prednost pri iskanju, saj omogoča uporabo **binarnega iskanja**, kar drastično zmanjša število potrebnih operacij.
*   **Težave:** Glavni problem nastopi pri vzdrževanju vrstnega reda ob dodajanju ali brisanju zapisov. Posebej problematično je dodajanje zapisa na začetek velike datoteke, saj bi to zahtevalo zamik vseh ostalih zapisov.
*   **Rešitev s pomožno datoteko (overflow file):** Da bi se izognili nenehnemu preurejanju, lahko uporabimo dodatno neurejeno datoteko, kamor se vpisujejo novi zapisi. Te zapisi nato periodično prepišemo v glavno urejeno datoteko. Pri iskanju sistem najprej pregleda urejeno datoteko, če zapisa ne najde, pa še linearno pregleda neurejeno pomožno datoteko.

---

## 3. Razpršene ali hash datoteke

Pri tej organizaciji se naslov strani (blok na disku), kamor zapis sodi, izračuna s pomočjo **hash funkcije** na podlagi vrednosti določenega polja, ki mu pravimo **hash polje**. Funkcija deluje po principu $f_{hash}(P) \to \text{naslov strani}$, kjer je $P$ vrednost hash polja. Iskanje je tukaj izjemno hitro, saj za večino zapisov potrebujemo le **en preber strani z diska**, iskanje znotraj strani pa se izvede v hitrem primarnem pomnilniku.

Dobra hash funkcija mora zagotavljati **enakomerno porazdeljenost** zapisov po celotni datoteki. Tipičen primer je funkcija **MOD $n$** (ostanek pri deljenju z določenim številom). Kljub učinkovitosti pa imajo hash datoteke svoje slabosti:
*   **Kolizija:** Do kolizije pride, ko hash funkcija vrne naslov strani, ki je že polna.
*   **Omejitve:** Niso primerne za iskanje po vzorcu, iskanje po nizu vrednosti (intervalih) ali iskanje po poljih, ki niso hash polja.

### 3.1 Podrobnosti o razpršeni (Hash) organizaciji

Hash datoteke so idealne za iskanje po točni vrednosti, vendar njihova učinkovitost temelji na pravilnem upravljanju s pomnilniškimi enotami.

#### 3.1.1 Koncept "Bucketa" (stran)
Pri razpršenem naslavljanju vsak izračun naslova ne kaže neposredno na posamezen zapis, temveč na določeno stran, ki se imenuje **"bucket"**. Vsak bucket ima prostore za **več zapisov**. Ko hash funkcija določi naslov bucketa, SUPB prebere celotno stran v pomnilnik in znotraj nje izvede **linearno iskanje** zapisov, ki so tam shranjeni po vrstnem redu vstavljanja.

#### 3.1.2 Tehnike za reševanje kolizij
Ko pride do kolizije, SUPB uporabi eno od naslednjih tehnik:
*   **Odprto naslavljanje (open addressing):** Sistem poišče prvo naslednjo stran, ki ima še prosto mesto. Pri iskanju velja specifično pravilo: **Če sistem naleti na prazno mesto**, preden najde iskani zapis, to pomeni, da **zapisa sploh ni v datoteki**. Iskanje se v tem primeru takoj prekine, kar preprečuje nepotrebno pregledovanje celotne datoteke.
*   **Nepovezane dodatne strani (unchained overflow):** Vzdržuje se ločen seznam oziroma prostor dodatnih strani za vse zapise, ki niso šli na svojo osnovno stran.
*   **Povezane dodatne strani (chained overflow):** Vsaka osnovna stran ima dodatno polje (kazalec), ki kaže na naslov dodatne strani, kamor so razvrščeni kolizijski zapisi. Vrednost 0 v tem polju pomeni, da kolizije ni bilo.
*   **Večkratno razprševanje (multiple hashing):** Ob koliziji se uporabi druga hash funkcija, ki vrne nov naslov, običajno v dodatnem prostoru.

#### 3.1.3 Dinamične razpršene datoteke in razširljivo razprševanje

Statične hash tehnike postanejo težavne, ko datoteka postane premajhna, kar zahteva reorganizacijo celotne datoteke z novo hash funkcijo. Rešitev so **dinamične razpršene datoteke**, kjer se velikost spreminja po potrebi. Najbolj znana tehnika je **razširljivo razprševanje (extendible hashing)**.

**Pravila razširljivega razprševanja:**
*   Strani (buckets) se ustvarjajo po potrebi.
*   Ko se stran napolni, se razdeli glede na prvih $i$ bitov ključa, kjer je $i$ trenutna **globina** imenika.
*   **Naslovna tabela strani (BAT - Bucket Address Table)** hrani kazalce na strani. Globina $i$ določa število kazalcev v imeniku ($2^i$).
*   Vsaka posamezna stran ima svojo **lokalno globino**, ki pove, koliko bitov je bilo uporabljenih za določitev njenega naslova.
*   Pri dinamičnih tehnikah je ključen parameter **$b$**, ki označuje **dolžino ključa v bitih**. Trenutna globina imenika $i$ se spreminja glede na velikost datoteka, pri čemer vedno velja omejitev **$0 \leq i < b$**.

Vira navajata primer postopnega dodajanja zapisov: po vpisu SL 21 in SG 37 je globina 0, po vpisu SG 14 se imenik razširi na globino 1, po vpisu SA 9 pa na globino 2, pri čemer se kazalci in strani ustrezno porazdelijo glede na binarne vrednosti ključev.

---

## 4. Indeksi in indeksiranje

**Indeks** je pomožna podatkovna struktura, ki SUPB-ju omogoča hitrejše lociranje zapisov, ne da bi bilo treba preiskati celotno podatkovno datoteko. Deluje analogno indeksu v knjigi, kjer na podlagi ključne besede hitro najdemo številko strani.

### 4.1 Ključni koncepti o indeksih in organizaciji

#### 4.1.1 Struktura indeksnega vpisa
Dokument jasno določa, da je indeksna datoteka ločena od podatkovne in da posamezen indeksni vpis (zapis v indeksu) sestavljata dve komponenti:
1.  **Iskalni ključ (indeksno polje):** Vrednost, po kateri iščemo.
2.  **Kazalec (pointer):** Naslov oziroma lokacija, ki kaže na dejanski zapis v podatkovni datoteki.

#### 4.1.2 Omejitev števila primarnih indeksov
Zaradi fizične narave shranjevanja podatkov ima lahko vsaka datoteka le **en primarni indeks** (ali indeks gruče). To je zato, ker primarni indeks določa dejansko fizično ureditev zapisov na disku. Datoteka pa ima lahko hkrati **več sekundarnih indeksov**, ki omogočajo iskanje po drugih poljih brez spreminjanja fizičnega vrstnega reda podatkov.

**Terminologija:**
*   **Podatkovna (osnovna) datoteka:** Vsebuje dejanske podatke.
*   **Indeksna datoteka:** Vsebuje **iskalni ključ (indeksno polje)** in kazalec na ustrezen zapis v podatkovni datoteki.

#### 4.1.3 Vrste indeksov glede na organizacijo
*   **Indeks gruče (clustered index):** To je indeks po polju, po katerem je podatkovna datoteka že fizično urejena.
*   **Primarni indeks:** Indeks po poljih, ki vsebujejo primarni ključ; datoteka je po tem ključu urejena.
*   **Sekundarni indeks:** Indeks, ki temelji na katerem koli polju, ki ni primarni ključ. Datoteka ima lahko le en primarni indeks, ima pa lahko **več sekundarnih indeksov**.
*   **Redki indeks (sparse index):** Hrani kazalce le na določene zapise (običajno po enega za vsako stran podatkovne datoteke), kar varčuje s prostorom.
*   **Gosti indeks (dense index):** Hrani kazalce na prav vse zapise v podatkovni datoteki.
*   **Sestavljen indeks (composite key):** Indeks po več poljih hkrati, kar se uporablja za poizvedbe, ki pogosto kombinirajo določene atribute (npr. plača in številka enote).

### 4.2 Drevesno indeksiranje in ISAM

Drevesno indeksiranje je izjemno učinkovito pri **intervalnem iskanju** ter pri operacijah dodajanja in brisanja podatkov.

#### 4.2.1 ISAM (Indexed Sequential Access Method)
ISAM je **statična indeksna struktura**, kar pomeni, da je njena primarna struktura določena ob kreiranju.
*   **Gradnja:** Ko se indeks ustvari, so vse strani v listih urejene zaporedno po iskalnem ključu.
*   **Dodajanje:** Če je stran v listu polna, se ustvarijo **dodatne strani (overflow pages)**. Te dodatne strani običajno niso urejene, kar sčasoma poslabša učinkovitost iskanja.
*   **Stroški:** Število I/O operacij je enako $log_F N$, kjer je $N$ število primarnih strani in $F$ faktor razvejitve (fanout). V primeru z milijon zapisi je strošek iskanja v ISAM strukturi le 3 operacije, medtem ko bi binarno iskanje po sami datoteki zahtevalo 17 operacij.

---

## 5. B+ drevesa

B+ drevo je **dinamična struktura**, ki se nenehno prilagaja spremembam v podatkovni datoteki in s tem odpravlja glavno slabost ISAM-a – kopičenje neurejenih dodatnih strani.

**Ključne lastnosti B+ dreves:**
*   Gre za **uravnoteženo drevo**, kjer so vse poti od korena do listov enako dolge.
*   Vozlišča (razen korena) morajo biti vedno vsaj **50 % zasedena**.
*   Listi so med seboj povezani v **dvosmerni seznam**, kar omogoča zelo hitro zaporedno pregledovanje in intervalno iskanje.
*   **Prednosti:** Ne potrebuje dodatnih strani za kolizije, saj se ob zapolnitvi vozlišča izvede delitev.

### 5.1 Tehnični detajli o B+ drevesih

B+ drevo je zasnovano tako, da maksimira učinkovitost branja s sekundarnega pomnilnika z minimiziranjem višine drevesa in vzdrževanjem visoke zasedenosti vozlišč.

#### 5.1.1 Parameter $d$ in pravilo zasedenosti (red drevesa)
Struktura B+ drevesa je strogo določena s parametrom **$d$**, ki predstavlja **red drevesa (order)**. Ta parameter določa kapaciteto posameznega vozlišča, ki znaša **$2d$**. Da bi zagotovili uravnoteženost in učinkovito izrabo prostora, morajo biti vozlišča vedno vsaj napol polna:
*   Vsako vozlišče (razen korena) mora vsebovati **$m$** vpisov, pri čemer velja omejitev **$d \leq m \leq 2d$**.
*   **Korensko vozlišče** je edina izjema v strukturi, saj zanj velja blažje pravilo zasedenosti: **$1 \leq m \leq 2d$**. To pomeni, da koren lahko vsebuje le en ključ, če se drevo šele začenja graditi.

#### 5.1.2 Algoritem za iskanje (Pseudokoda)
Iskanje v B+ drevesu temelji na rekurzivnem spuščanju od korena proti listom. Vira podajata natančen postopek iskanja ključa $K$:
*   **Funkcija `find(K)`:** Ta funkcija sproži iskanje tako, da pokliče pomožno funkcijo `tree_search(root, K)`.
*   **Funkcija `tree_search(nodepointer, K)`:** 
    *   Če je vozlišče, na katerega kaže `nodepointer`, **list (leaf)**, sistem vrne to vozlišče.
    *   Če vozlišče ni list, algoritem preveri ključe znotraj vozlišča ($K_1, K_2, \dots, K_m$):
        *   Če je $K < K_1$, rekurzivno sledi kazalcu $P_0$.
        *   Če je $K > K_m$, sledi kazalcu $P_m$.
        *   Sicer poišče tak indeks $i$, da velja **$K_i \leq K < K_{i+1}$**, in sledi kazalcu $P_i$.

#### 5.1.3 Višina drevesa in faktor razvejanja
Učinkovitost poizvedb v B+ drevesih je neposredno povezana z njihovo **višino ($h$)**, saj višina določa število I/O operacij (preberov z diska), potrebnih za dostop do podatkov. Zaradi velikega **faktorja razvejanja ($F$)**, ki predstavlja število otrok posameznega vozlišča, je višina običajnih B+ dreves v praksi zelo majhna – običajno ne presega **3 ali 4 nivojev**.

#### 5.1.4 Stiskanje ključev s predponami (Prefix Compression)
Za povečanje faktorja razvejanja ($F$) in s tem zmanjšanje višine drevesa SUPB uporablja tehniko **stiskanja ključev**. Namesto celotnih dolgih nizov v indeksnih vozliščih shranjuje le minimalno dolžino **predpone**, ki še omogoča ločevanje med ključi. 
*   **Vizualni primer:** Namesto da bi v indeksu shranili celotno ime "Berce Katja", sistem shrani le **"Ber"**. To zasede manj prostora na indeksni strani, kar omogoči, da na isto stran shranimo več kazalcev, s čimer se poveča faktor razvejitve in izboljša hitrost iskanja.

#### 5.1.5 Dvosmerna povezava med listi B+ drevesa
Za razliko od ISAM strukture so vsi listi v B+ drevesu med seboj povezani v **dvosmerni seznam**. Ta povezava je ključna za učinkovitost, saj omogoča:
*   Hitro **zaporedno branje** celotne datoteke ali njenega dela.
*   Učinkovito **intervalno iskanje** (npr. "najdi vse zapise med vrednostmi 20 in 50"), saj se sistem le enkrat spusti do prvega lista (vrednost 20), nato pa se preprosto premika po seznamu listov, dokler ne doseže zgornje meje.

#### 5.1.6 Operacije v B+ drevesu
Pri operacijah se uporabljajo različni mehanizmi za ohranjanje ravnovesja:
1.  **Delitev (Split):** Ko je list ali indeksno vozlišče polno, se razdeli na dvoje. Ključ iz lista se kopira nivo višje, delitveni ključ iz indeksnega vozlišča pa se prenese nivo višje.
2.  **Združevanje (Merge):** Če pri brisanju zasedenost pade pod 50 %, se vozlišče združi s sosednjim.
3.  **Redistribucija:** Namesto združevanja lahko ključe le prerazporedimo med sosednja vozlišča, da ohranimo minimalno zasedenost.

**Stiskanje ključev (Key Compression):** Višina drevesa ($h$) je ključna za hitrost. Z uporabo stiskanja (npr. shranjevanje le predpon imen namesto celih priimkov) povečamo **faktor razvejitve (F)**, kar zmanjša višino drevesa in s tem število I/O operacij.

---

## 6. Specializirani indeksi in gruče

V specifičnih okoljih, kot so podatkovna skladišča, se uporabljajo naprednejše oblike indeksiranja.

#### 6.1 Bitni indeks (Bitmap index)
Namesto kazalcev uporablja **bitne vektorje** (nize ničel in enic). Vsak bit v vektorju ustreza enemu zapisu v tabeli; vrednost 1 pomeni, da zapis ustreza določenemu atributu.
*   **Prednosti:** Izjemna kompaktnost in hitrost pri poizvedbah z več pogoji (npr. najdi vse, ki so 'Supervisor' IN v enoti 'B003'), kjer se preprosto izvede **bitno množenje** vektorjev.

#### 6.2 Stični indeks (Join index)
Uporablja se za tabele, ki so povezane s tujimi ključi. Indeks za vsako vrednost ključa hrani kazalce na zapise v vseh vpletenih tabelah. To drastično pohitri operacije stikanja (JOIN) v velikih sistemih.

#### 6.3 Gruče (Clusters)
To je tehnika, kjer SUPB fizično shrani zapise različnih relacij **skupaj**, če si delijo skupne stolpce in se pogosto uporabljajo skupaj v poizvedbah. Stolpce, ki so skupni, imenujemo **ključ gruče**. Takšna shramba izboljša čas dostopa do diska, saj so povezani podatki fizično blizu drug drugemu.