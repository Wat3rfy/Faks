

Pot od realnega sveta do delujoče baze poteka v petih ključnih fazah:
1.  **Svet/Domena** - realni poslovni sistem, ki ga želimo modelirati $\rightarrow$ **mentalni model** - ideja inženirja na podlagi uporabniških zahtev.
2.  **Konceptualni model:** Formalen prikaz mentalnega modela (običajno ER diagram), ki je neodvisen od tehnologije. Osredotoča se na semantiko oziroma pomen podatkov v obravnavani domeni. Tu določamo entitete, njihove povezave, atribute in poslovna pravila. Ključna lastnost tega nivoja je **neodvisnost od sistema za upravljanje podatkovnih baz (SUPB)**; v tej fazi nas ne zanima, ali bomo uporabili MySQL, Oracle ali objektno bazo.
3.  **Logični model:** Preslikava konceptov v strukture določenega tipa SUPB (npr. relacijske tabele). Konceptualni model preslikamo v jezik izbranega tipa SUPB. Če izberemo relacijski SUPB, ustvarimo **relacijski model**. Tukaj določimo tabele, stolpce, primarne in tuje ključe ter uporabimo mehanizme, kot so indeksi, sprožilci (triggers) in pogledi.
4.  **Fizični model:** Tehnična implementacija v SUPB z ukazi **SQL DDL** (`CREATE TABLE`, `CREATE INDEX`, `CREATE VIEW`), kjer določimo dejansko shrambo na disku. To je zadnja faza, kjer se ukvarjamo z optimizacijo fizične sheme na pomnilniškem mediju. Odločamo se o datotečni organizaciji, velikosti medpomnilnika, sočasnosti in specifičnih nastavitvah strojne opreme.

### 1.2 Omejitve neposrednega kreiranja baze
Čeprav bi teoretično lahko bazo ustvarili neposredno z ukazi SQL DDL (npr. `CREATE DATABASE`, `CREATE TABLE`), viri opozarjajo na resne omejitve takšnega pristopa pri kompleksnih sistemih. Če ima baza več sto tabel, postane ročno pisanje skript zamudno in podvrženo napakam, vzdrževanje in spreminjanje sheme pa je skoraj nemogoče. Zato se uporabljajo strukturirani pristopi načrtovanja.

### 1.3 Notacije ER diagramov
Viri navajajo, da obstaja veliko različnih vizualnih načinov za prikaz entitet in razmerij:
*   **Chenova notacija:** Klasičen prikaz z rombi za razmerja.
*   **Martinova notacija (Crow's Foot):** Pogosto uporabljena v CASE orodjih, uporablja "vranje noge" za prikaz števnosti "več".
*   **IDEF1X:** Standard, ki se uporablja predvsem v državnih in vojaških projektih.
*   **UML:** Objektno usmerjen grafični jezik, kjer so entitete prikazane kot razredi.
*   **Min-Max / ISO:** Notacija, ki ob povezavah eksplicitno zapiše intervale števnosti, npr. (0, N) ali (1, 1).

## 2. Pristopi k načrtovanju PB
Viri navajajo dva osnovna metodološka pristopa:

1.  **Od spodaj navzgor (Bottom-up):** Začnemo z identifikacijo posameznih atributov in jih nato združujemo v skupine oziroma relacije. Ta pristop je primeren za enostavne baze z majhnim številom atributov in je tesno povezan s postopkom **normalizacije**. Normalizacija temelji na identifikaciji funkcionalnih odvisnosti med podatki.
2.  **Z vrha navzdol (Top-down):** Začnemo z visokonivojskim modelom, ki vsebuje le nekaj ključnih entitet in razmerij, nato pa jih postopoma razgrajujemo na pod-entitete, specifične povezave in atribute. Ta pristop se izvaja s pomočjo tehnike **Entiteta – Razmerje (E-R)** in je primeren za velike in kompleksne baze.

Pri izjemno obsežnih projektih se uporablja pristop **"po delih"**, kjer celotno poslovno domeno razdelimo na manjša področja, zanje ustvarimo področne sheme in jih na koncu združimo v končno shemo.

## 3. Konceptualno načrtovanje in ER modeliranje
Cilj konceptualnega načrtovanja je ustvariti mentalno sliko domene v obliki formalnega modela. Najbolj razširjena tehnika za to je **diagram entiteta-razmerje (ER)**.

### 3.1 Entitetni tipi in entitete – Teoretične in matematične definicije
Gradivo uvaja strogo formalno podlago za opredelitev entitetnih tipov in njihovih identifikatorjev.
*   **Entitetni tip:** Predstavlja zbirko istovrstnih objektov iz realnega sveta (npr. Avtomobili, Profesorji). V ER diagramu ga grafično ponazorimo s pravokotnikom, ki vsebuje naziv tipa in prostor za atribute.
*   **Entiteta:** Je posamezen objekt oziroma instanca entitetnega tipa (npr. konkretno vozilo z registracijo GO-123 ali profesor Miha Repič).

#### 3.1.1 Formalni pogoji za identifikacijo entitet
Enolični identifikator je podmnožica atributov in razmerij, ki enolično loči posamezno instanco znotraj množice.

**A. Močni entitetni tipi:**
Kadar entiteto identificiramo zgolj z njenimi atributi $\{a_1, \dots, a_k\}$, morajo biti izpolnjeni trije pogoji:
1.  Vsi atributi morajo biti **totalni in enovrednostni** - ne smejo biti null ali biti večvrednosten - seznam/ponavljanje atributa.
2.  Obstajati mora funkcija preslikave $T: V_1 \times \dots \times V_k \to E_A$ (kjer so $V_i$ območja vrednosti atributov) - nek element se slika v največ eno enititeto. *V slidih piše enovrednostna totalna ali parcialna funkcija - ampak to je samo definicija funkcije tkoda ne vem.*
3.  Podmnožica mora biti **minimalna**: ne sme obstajati prava podmnožica $X'$, ki bi prav tako izpolnjevala pogoj funkcije.

**B. Šibki entitetni tipi:**
Če identifikator vključuje tudi razmerja do drugih entitetnih tipov, je matematični pogoj razširjen:
*   Identifikator je definiran kot $\{a_1, \dots, a_k\} \cup IET_1 \cup \dots \cup IET_n$, kjer so $IET_i$ identifikatorji povezanih entitetnih tipov.
*   Funkcija preslikave vključuje tudi vrednostne množice teh tujih identifikatorjev: $T: V_{a1} \times \dots \times V_{ak} \times V_{IET1} \times \dots \times V_{IETn} \to E_A$.

### 3.2 Atributi
Atributi so lastnosti, ki opisujejo entitete. Pri načrtovanju uporabljamo abstrakcijo, kar pomeni, da izberemo le tiste lastnosti, ki so za našo bazo relevantne. Vrste atributov vključujejo:
*   **Totalni atribut:** Vedno mora imeti vrednost (ni dovoljen NULL).
*   **Parcialni atribut:** Vrednost ni nujna.
*   **Eno-vrednostni atribut:** Entiteta ima lahko le eno vrednost (npr. datum rojstva).
*   **Več-vrednostni atribut:** Oseba ima lahko več imen ali telefonskih številk.

**Atomarnost:** Vsak atribut mora biti **atomaren**, kar pomeni, da lahko na enem mestu hrani le eno vrednost (pazi pri več-vrednostnih atributih!).

### 3.3 Razmerja in njihove lastnosti
Razmerja predstavljajo dejanske povezave med entitetami (npr. Profesor *je nosilec* Predmeta). Prikazujemo jih s črto, ki povezuje dva entitetna tipa. Vsako razmerje ima svojo vlogo oziroma pomen na obeh straneh (npr. študent *je vpisan na* program, program *je vpisal* študent).

**Števnost razmerja (Cardinality):** Pove, koliko entitet z ene strani se lahko poveže z eno entiteto na drugi strani. V notacijah vedno označimo minimalno in maksimalno števnost (npr. 0..* ali 1..1). Med dvema entitetama lahko obstaja tudi več različnih razmerij hkrati (npr. študent je predmet *izbral* in študent je predmet *opravil*). Sama razmerja lahko imajo tudi svoje atribute, npr. kdaj je bil izpit opravljen in s katero oceno.

**Problem dvoumnih in nepopolnih povezav:** Problem dvoumnih povezav nastane, ko krožne poti v modelu ne podajajo jasnega odgovora na specifično vprašanje, kar rešujemo z uvedbo neposrednih vezi. Tipičen primer je trikotnik med **zdravnikom, oddelkom in pacientom**: čeprav sta oba na istem oddelku, iz krožne povezave ni razvidno, kateri konkretni zdravnik dejansko zdravi pacienta. Brez neposredne povezave med njima ostaja informacija nejasna, saj struktura dopušča več napačnih interpretacij. Z restrukturiranjem modela te poti do informacij poenostavimo in zagotovimo, da so odnosi med entitetami povsem enoznačni.

## 4. Razširjena ER notacija (EER)
EER uvaja koncepte, ki omogočajo bolj natančno modeliranje kompleksnih razmerij:

*   **Specializacija in Generalizacija:** Gre za procese določanja podtipov in nadtipov. Profesor in asistent sta lahko specializaciji entitete zaposleni.

### 4.1 Pravila za Generalizacijo in Specializacijo
Pri določanju razmerij med nadtipom (A) in podtipi (B, C) moramo določiti dve ključni omejitvi: **omejitev popolnosti** (ali mora vsak A biti tudi B/C?) in **omejitev disjunktnosti** (ali je A lahko hkrati B in C?).

*   **Totalno in ekskluzivno pokritje:** Vsaka entiteta A mora biti ali B ali C, ne pa oboje hkrati ($E_B \cup E_C = E_A$ in $E_B \cap E_C = \emptyset$). **Primer:** Oseba je lahko le Moški ali Ženska.
*   **Totalno in prekrivno pokritje:** Vsaka entiteta A mora biti vsaj en podtip, lahko pa oba ($E_B \cup E_C = E_A$ in $E_B \cap E_C \neq \emptyset$). **Primer:** Na univerzi je Oseba lahko Študent ali Zaposlen. Vsaka oseba v sistemu mora biti v eni od teh vlog, dopuščamo pa možnost, da je zaposleni hkrati tudi študent (npr. mladi raziskovalec).
*   **Delno in ekskluzivno pokritje:** Entiteta A je lahko B, C ali pa nič od tega, ne sme pa biti oboje hkrati ($E_B \cup E_C \subset E_A$ in $E_B \cap E_C = \emptyset$). **Primer:** Zaposleni je lahko Manager ali Inženir. Nekateri zaposleni so lahko navadni delavci, ki niso niti managerji niti inženirji (zato delno pokritje), vendar pa ista oseba ne more biti hkrati v obeh specializiranih vlogah.
*   **Delno in prekrivno pokritje:** Entiteta A je lahko karkoli ali pa nič ($E_B \cup E_C \subset E_A$ in $E_B \cap E_C \neq \emptyset$). Primer: Oseba je lahko Študent, Športnik, oboje ali nič od tega. **Primer:** Oseba v bazi športnega društva. Lahko je Trener, lahko je Igralec, lahko je Trener in Igralec hkrati, lahko pa je le Član, ki ne opravlja nobene od teh dveh specifičnih vlog.

  
**Agregacija in kompozicija** opisujeta razmerje med celoto in njenimi sestavnimi deli, vendar se razlikujeta po odvisnosti med njimi. 

**Agregacija** predstavlja **šibko povezavo**, pri kateri deli lahko obstajajo samostojno in neodvisno od obstoja celote, kot so na primer igralci v določeni športni ekipi. 

**Kompozicija** je močna povezava, kjer deli ne morejo obstajati brez svoje celote in so z njo neločljivo povezani. To pomeni, da se v primeru izbrisa celote, vedno samodejno izbrišejo tudi vsi njeni deli. Na primer športna ekipa in njene prihajajoče igre.

## 5. Metoda konceptualnega načrtovanja 
Proces načrtovanja je strukturiran v devetih korakih:
1.  **Identifikacija entitetnih tipov (K1.1):** Pregledamo uporabniške zahteve in iz besedila izločimo samostalnike (npr. profesor, predmet). Ločimo objekte od njihovih lastnosti. Dokumentiramo nazive, opise in sinonime.
2.  **Identifikacija povezav (K1.2):** Iščemo glagole v zahtevah (npr. profesor *razpiše* rok). Pozorni smo na binarne, n-arne in rekurzivne povezave. Izogibati se moramo nepopolnim povezavam, ki povzročajo dvoumnost.
3.  **Identifikacija atributov (K1.3):** Določimo lastnosti entitet in povezav. Pazimo na sestavljene, več-vrednostne in izpeljane atribute (tiste, ki jih izračunamo iz drugih podatkov).
4.  **Določanje domen (K1.4):** Domena je množica dovoljenih vrednosti za atribut (npr. barva mora biti iz nabora {bela, rdeča...} ali starost v intervalu [0..120]).
5.  **Določanje kandidatov za ključe (K1.5):** Izberemo primarni ključ, pri čemer dajemo prednost tistim z manj atributi, ki se redko spreminjajo.
6.  **Uporaba EER elementov (K1.6):** Po potrebi dodamo specializacijo ali agregacijo za boljšo semantiko, če to ne škodi berljivosti.
7.  **Preverjanje odvečnih elementov (K1.7):** Združimo redundantne entitetne tipe in odstranimo odvečne povezave, če je informacija dosegljiva po drugi poti.
8.  **Preverjanje transakcij (K1.8):** Preverimo, ali model podpira vse zahtevane operacije (vnos, poizvedbe).
9.  **Potrditev z uporabnikom (K1.9):** Uporabnik pregleda model in ga potrdi.

### 5.1 Hevristike in nasveti za načrtovanje
Gradivo ponuja konkretne nasvete za izboljšanje kakovosti modela:
*   **Izbira ključa:** Če imamo več kandidatov za ključ, izberemo tistega z najmanj atributi, tistega, ki se najmanj spreminja, in tistega z najmanjšo dolžino znakov. **Imena oseb** so izrecno odsvetovana kot kandidati za ključ.

### 5.2 Dokumentacijske predloge
Za uspešen prenos načrta v bazo je nujna uporaba dokumentacijskih tabel.

**Tabela za opis entitetnih tipov:**

| Naziv | Opis | Sinonim | Število entitet |
| :--- | :--- | :--- | :--- |
| Profesor | Pedagoški delavec, nosilec predmeta | Pedagok | Vsaka katedra ima 1 ali več |
| Izpitni rok | Datum razpisanega izpita | Rok, pisni izpit | ~300 letno na fakulteti |

**Tabela za opis povezav:**

| Entitetni tip | Števnost | Povezava | Števnost | Entitetni tip |
| :--- | :--- | :--- | :--- | :--- |
| Član | 1..\* | Pripada | 1..1 | Katedra |
| Laboratorij | 1..\* | Sodi v | 1..1 | Katedra |

**Tabela za opis atributov:**

| Entitetni tip | Atribut | Opis | Tip | Dolžina | Izpeljan? |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Študent | VpisSt | Vpisna številka | Number | 8 | Ne |
| Projekt | SkupnaCena | (Cena*Količina)*(1+DDV) | Decimal | 10,2 | Da (računska izpeljava) |

## 6. Logično načrtovanje in relacijski model
Logično modeliranje nastopi po konceptualnem in je osnova za ciljni SUPB. Če uporabljamo relacijsko bazo, se koncepti ER preslikajo v relacijsko shemo: entitetni tip postane tabela (relacija), atribut postane stolpec, enolični identifikator pa primarni ključ. Povezave 1:n se realizirajo prek tujih ključev.

### 6.1 Formalna definicija ključa relacije
V relacijskem modelu so atributi $X$ ključ relacijske sheme, če:
1.  $X \to A_1, A_2, \dots, A_n$ (funkcionalno določajo vse ostale atribute).
2.  **Pogoj minimalnosti:** Ne obstaja nobena prava podmnožica $X' \subset X$, ki bi prav tako funkcionalno določala vse atribute sheme.

### 6.2 Funkcionalne odvisnosti in normalizacija
**Normalizacija** je ključen postopek, s katerim preprečimo **ažurne anomalije** (napake pri dodajanju, brisanju ali spreminjanju podatkov) in zmanjšamo redundanco. Temelji na funkcionalnih odvisnostih (X -> Y pomeni, da vrednost X enolično določa Y).

**Stopnje normalnih oblik:**
*   **1NO (Prva normalna oblika):** Relacija nima ponavljajočih se atributov (skupin), ima definiran primarni ključ in določene funkcionalne odvisnosti.
*   **2NO (Druga normalna oblika):** Je v 1NO in ne vsebuje parcialnih odvisnosti (noben atribut ni odvisen le od dela sestavljenega ključa).
*   **3NO (Tretja normalna oblika):** Je v 2NO in ne vsebuje tranzitivnih odvisnosti (med neključnimi atributi ni odvisnosti).
*   **4PNO (Četrta poslovna normalna oblika):** Atributi niso odvisni od konkretne vrednosti primarnega ključa; tu se pogosto ukvarjamo z ločevanjem v več relacij, če imamo študenta, ki ja lahko redni ali izredni kjer ima redni štipendijo, izredni pa delodajalca, potem naredimo študenta, rednega študenta in izrednega študenta. 

V določenih primerih se zavestno odločimo za **denormalizacijo** (npr. shranjevanje izpeljanega atributa "skupen čas"), da povečamo učinkovitost poizvedb na račun hitrosti spreminjanja podatkov.

### 6.3 Pravila preslikave v relacije (Korak K2.1)
*   **Močni entitetni tipi:** Ustvarimo samostojno relacijo.
*   **Šibki entitetni tipi:** Relacija vključuje atribute entitete in ključe povezanih močnih entitet.
*   **Povezave 1:n:** Ključ "očeta" (stran 1) se prenese kot tuji ključ k "otroku" (stran n).
*   **Povezave 1:1:** Odvisno od obveznosti; lahko združimo v eno relacijo ali prenesemo tuji ključ k tisti entiteti, ki ima obvezno povezavo.
*   **Povezave n:n:** Vedno zahtevajo novo vmesno relacijo, ki vsebuje primarna ključa obeh entitet kot tuja ključa.
*   **Rekurzivne povezave:** Ključ se kopira v isto relacijo pod drugim imenom.

## 7. Fizično načrtovanje, optimizacija in SQL implementacija
Fizično načrtovanje določa, kako bo baza dejansko shranjena na disku. Vhod v to fazo je logični model, izhod pa so SQL skripte in nastavitve sistema.

### 7.1 Tehnične SQL podrobnosti in sintaksa – SQL DDL
Za fizično kreiranje baze uporabljamo SQL DDL ukaze. Primer definicije tabele s primarnim ključem in privzetimi vrednostmi:
```sql
CREATE DATABASE urarna;
USE urarna;

CREATE TABLE artikel (
    art_id INT(4) NOT NULL,
    art_name VARCHAR(100) NOT NULL,
    art_stock INT(4) NOT NULL DEFAULT 0,
    PRIMARY KEY (art_id)
);
```
Za preverjanje kompleksnejših poslovnih pravil (npr. da oddelek ne sme imeti več kot enega aktivnega vodje hkrati) uporabljamo omejitve `CONSTRAINT`:
```sql
CONSTRAINT ManagerConflict CHECK (NOT EXISTS 
    (SELECT dept_no FROM dept_manager 
     WHERE to_date = "9999-01-01" 
     GROUP BY dept_no HAVING COUNT(*) > 1)
);
```

### 7.2 Izbira SUPB in MySQL shrambe (Storage Engines)
Različni SUPB podpirajo različne funkcionalnosti (primarni ključi, sprožilci, domene). MySQL ponuja več pogonov (engines):
*   **InnoDB:** Privzeti pogon, podpira transakcije, zaklepanje na nivoju vrstic in tuje ključe.
*   **MyISAM:** Starejši, ne podpira transakcij, ima pa hitre full-text indekse.
*   **Memory:** Podatki so shranjeni v RAM-u, uporablja HASH indekse.

### 7.3 Indeksi in učinkovitost
Indeksi so ključni za hitrost. Gradivo opozarja, da neurejen dostop do več tabel brez indeksov lahko povzroči ogromno število nepotrebnih operacij (primer izračuna: $7 \times 110 \times 122 \times 326 \times 2996 = 91.750.822.240$ operacij!). Namen je izbrati optimalen način dostopa do podatkov. Poznamo neurejene, urejene in razpršene datoteke.
**Indeksi** so ključni za hitrost:
*   **Primarni indeks:** Indeks po primarnem ključu, po katerem je datoteka urejena.
*   **Indeks gruče (Clustered):** Datoteka je fizično urejena po tem atributu, ki pa ni nujno unikaten.
*   **Sekundarni indeksi:** Dodatni indeksi za hitrejše iskanje po neključnih poljih.

**Sintaksa za kreiranje indeksov :**
```sql
CREATE INDEX index_name ON tbl_name (col_name) USING BTREE;
-- Možni tipi: BTREE (najpogostejši), HASH (za Memory baze), RTREE (za GIS podatke) 
```

**Smernice za indeksiranje:** Ne indeksiramo majhnih tabel ali polj, ki se nenehno spreminjajo. Indeksiramo tuje ključe in polja, ki nastopajo v `ORDER BY`, `GROUP BY` ali `WHERE` pogojih. Učinkovitost indeksov v MySQL preverjamo z ukazom `EXPLAIN`.

### 7.4 Particioniranje (Razbitje relacij)
Pri tabelah z milijoni vrstic uporabimo **particioniranje**, da relacijo razbijemo na manjše dele.
*   **Horizontalno particioniranje (Horizontalna delitev):** Vrstice razdelimo glede na vrednost nekega polja (npr. po letu zaposlitve ali ID trgovine).
*   **Vertikalno particioniranje:** Tabelo razdelimo po stolpcih (npr. manj uporabljene stolpce damo v ločeno datoteko).
Prednosti so boljša porazdelitev obremenitve (load balancing), večja učinkovitost in lažje obnavljanje podatkov.

**Sintaksa za particioniranje:**
```sql
CREATE TABLE employees ( ... )
PARTITION BY HASH(store_id) PARTITIONS 4;

-- Ali particioniranje po datumu zaposlitve
PARTITION BY HASH(YEAR(hired)) PARTITIONS 4;
```

## 8. Varnost in pogledi (View)
**Uporabniški pogledi (K5 / Views):** Pogled je navidezna relacija, ki se kreira ob vsaki poizvedbi in ne obstaja fizično v baze. Omogočajo poenostavitev kompleksnih stikov za uporabnika in skrivanje občutljivih podatkov. Pogled je navidezna tabela, ki poenostavi dostop do kompleksnih poizvedb:
```sql
CREATE OR REPLACE VIEW obremenitev AS
SELECT Nosilec, SUM(StUr) as Stevilo_ur_tedensko
FROM Predmet
GROUP BY Nosilec;

-- Primer za aktivne managerje
CREATE VIEW managers AS
SELECT e.emp_no, e.first_name, d.dept_name
FROM employees e
INNER JOIN dept_manager dm ON e.emp_no = dm.emp_no
INNER JOIN departments d ON dm.dept_no = d.dept_no
WHERE dm.to_date = '9999-01-01';
```

**Varnostni mehanizmi (K6):**
*   **Sistemska varnost:** Dostop do baze prek uporabniških imen in gesel. MySQL priporoča uporabo "salt" in hash algoritmov (MD5, SHA1) za hrambo gesel.
*   **Podatkovna varnost:** Dodeljevanje specifičnih pravic (GRANT) za operacije nad tabelami.

## 9. Analiza, optimizacija in pregled sheme

### 9.1 Matrika transakcija/relacija
Za ugotavljanje obremenjenosti baze gradivo uporablja matriko, kjer za vsako transakcijo (A, B, C...) označimo operacije nad tabelami :
*   **I** (Insert)
*   **R** (Read)
*   **U** (Update)
*   **D** (Delete)
To omogoča identifikacijo "vročih" tabel, ki potrebujejo dodatno indeksiranje .

### 9.2 Povezava z DFD
Diagrami podatkovnih tokov (**DFD** - data flow diagram) se uporabljajo za preverjanje celovitosti modela. DFD kaže, kateri procesi v sistemu potrebujejo katere podatke, kar nam omogoča preveriti, ali naš podatkovni model (ER) sploh vsebuje vse potrebne entitete in atribute za delovanje teh procesov.

### 9.3 Pregled sheme v MySQL
Za analizo že ustvarjene baze gradivo navaja ključne ukaze za pregled kataloga:
*   `SHOW TABLES;` – izpis vseh tabel v bazi.
*   `DESCRIBE table_name;` – podrobna struktura stolpcev in tipov.
*   `SHOW INDEX FROM table_name;` – pregled vseh definiranih indeksov.
*   `SHOW CREATE TABLE table_name;` – izpis celotnega ukaza SQL, ki je ustvaril tabelo.

**Napredni ukazi za pregled v MySQL:**
Za analizo že ustvarjenih tabel v terminalu gradivo priporoča:
*   `SHOW CREATE TABLE table_name;` – izpis celotnega DDL ukaza.
*   **Uporaba stikala `\G`:** V terminalu ukaz `SHOW CREATE TABLE employees\G;` preoblikuje tabelarični izpis v preglednejši vertikalni niz, kar olajša branje dolgih definicij stolpcev.