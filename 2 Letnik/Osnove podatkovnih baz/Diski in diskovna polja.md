
Tukaj so podrobni zapiski o diskih in diskovnih poljih na podlagi predloženih virov:

### **1. Zgradba SUPB in komponente za delo s podatki**

Sistem za upravljanje podatkovnih baz (SUPB) je sestavljen iz več plasti in komponent, ki skrbijo za učinkovito delo s podatki. Te komponente vključujejo:

- **Stroj za evaluacijo poizvedb:** Vključuje sintaktični analizator, optimizator, izvajalec plana in evaluator operatorjev.
- **Upravljanje s podatki:** Datoteke in metode dostopa, upravljalec medpomnilnika ter upravljalec prostora na disku.
- **Administrativni moduli:** Upravljalec obnove podatkov, enota za nadzor sočasnosti, upravljalec transakcij, upravljalec zaklepanja.
- **Podatki v PB:** Shranjujejo se na diskih in trakovih.
- **Upravljalec prostora na disku (Disk Space Manager):** Upravlja s prostorom na disku in prejema ukaze za zaseganje ali sproščanje prostora od upravljavca z datotekami.
- **Upravljalec z datotekami (File Manager):** Posreduje zahteve za prostor v enotah, imenovanih **strani**. Odgovoren je za upravljanje strani znotraj datoteke in urejanje zapisov znotraj posamezne strani.
- **Velikost strani:** Je parameter SUPB, tipično znaša **4 - 8 KB**.
- **Upravljalec medpomnilnika (Buffer manager):** Skrbi za prenos strani iz diska v medpomnilnik (_buffer pool_). Upravljalec z datotekami poišče stran z zapisom, prenos pa izvede upravljalec medpomnilnika.

---

### **2. Hierarhija pomnilnika**

Pomnilnik je organiziran hierarhično glede na hitrost, kapaciteto in ceno:

1. **Primarni pomnilnik:** CPU, medpomnilnik (cache) in glavni pomnilnik (RAM).
2. **Sekundarni pomnilnik:** Magnetni diski.
3. **Terciarni pomnilnik:** Magnetni trakovi.

**Razlogi za uporabo sekundarnega in terciarnega pomnilnika:**

- **Obstojnost podatkov:** Podatki ostanejo shranjeni tudi po izklopu napajanja.
- **Cena na enoto:** Shranjevanje na diskih je cenejše od RAM-a.
- **Omejen naslovni prostor:** Primarni pomnilnik ima omejen naslovni prostor (npr. $2^{32} = 4\text{ GB}$ podatkov).

---

### **3. Magnetni disk in SSD**

Struktura magnetnega diska vključuje roko diska, glavo diska, sledi, sektorje, bloke in smer premikanja glave.

**Povprečni dostopni čas diska je sestavljen iz:**

1. **Iskalni čas** (seek time).
2. **Rotacijska zakasnitev** (rotational latency).
3. **Čas prenosa** (transfer time).

Organizacija podatkov na disku neposredno vpliva na ta čas. Čas prenosa je običajno večji od časa obdelave, zato je organizacija strani ključna. Razmerje dostopnega časa med RAM-om in diskom je približno **1 : 1000**.

#### **Primerjava: HDD (Hard Disk Drive) vs. SSD (Solid State Drive)**:

|Lastnost|SSD|HDD|
|:--|:--|:--|
|**Poraba energije**|2–3 W (daljša življenjska doba baterije)|6–7 W (večja poraba)|
|**Cena**|Dražje (~1,00$ na GB)|Ceneje (~0,075$ na GB)|
|**Kapaciteta**|Tipično do 512 GB (za prenosnike)|Tipično 500 GB – 2 TB|
|**Zagon sistema**|~22 sekund|~40 sekund|
|**Hrup**|Brez gibljivih delov, neslišen|Slišno klikanje in vrtenje|
|**Vibracije**|Jih ni|Vrtenje plošč lahko povzroči vibracije|
|**Toplota**|Nizka (ni gibljivih delov)|Več toplote zaradi gibljivih delov|
|**Stopnja okvar (MTTF)**|2,0 milijona ur|1,5 milijona ur|
|**Hitrost pisanja/kopiranja**|Nad 200 MB/s (do 500 MB/s)|50 – 120 MB/s|
|**Hitrost odpiranja datotek**|Do 30% hitreje kot HDD|Počasneje|
|**Vpliv magnetizma**|Varno pred magneti|Magneti lahko izbrišejo podatke|

---

### **4. Polje diskov in RAID**

Diski so pogosto ozko grlo, saj njihova učinkovitost raste le 10 % na leto, medtem ko učinkovitost procesorjev raste 50 % na leto. Odpoved diska je kritična, saj so mehanske naprave bolj nagnjene k napakam. Rešitev je uporaba več diskov v polju.

**RAID (_Redundant Arrays of Independent Disks_)** implementira dve glavni strategiji:

1. **Učinkovitost:** Porazdelitev podatkov (_data striping_).
2. **Zanesljivost:** Podvajanje podatkov – redundanca.

#### **Porazdelitev podatkov (Data Striping)**

Podatki se razdelijo na enake enote (_striping units_) in zapišejo na več diskov po **"round robin"** algoritmu: enota $i$ se zapiše na disk $(i \pmod D)$, kjer je $D$ število diskov.

- **Enota 1 bit (Primer 1):** Vsaka I/O operacija vključi vseh $D$ diskov. Prenos je $D$-krat hitrejši, dostopni čas pa ostane enak.
- **Enota 1 blok (Primer 2):** I/O operacija velikosti 1 blok vključi le 1 disk. To omogoča paralelno izvajanje več operacij in zmanjša povprečni dostopni čas.

#### **Redundanca in zanesljivost**

Več diskov pomeni manjšo zanesljivost polja. Če ima en disk **MTTF (_mean-time-to-failure_)** 50.000 ur (5,7 let), ima polje 100 diskov MTTF le 500 ur (21 dni). Z dodajanjem redundantnih diskov (npr. 10 diskov na 100) se MTTF lahko poveča na več kot 250 let. Redundanca se pogosto izvaja z **redundantnim diskom za paritetni bit**, ki se izračuna s funkcijo XOR nad bitom na vseh podatkovnih diskih.

---

### **5. Stopnje RAID**

- **RAID 0 (Porazdeljen, brez redundance):** Uporablja le striping. Nudi najvišjo učinkovitost in 100 % izrabo prostora, a MTTF pada linearno s številom diskov.
- **RAID 1 (Zrcaljen - Mirrored):** Najdražja rešitev, kjer sta dve kopiji podatkov na dveh diskih. Izraba prostora je 50 %. Branje je lahko paralelno, pisanje pa poteka na oba diska.
- **RAID 2:** Uporablja kode za popravljanje napak (_Error-Correction Codes_).
- **RAID 3:** Pariteto na ravni bajtov (_Byte-Interleaved Parity_).
- **RAID 4:** Pariteto na ravni blokov (_Block-Interleaved Parity_) na namenskem disku.
- **RAID 5:** Porazdeljena pariteta na ravni blokov (_Block-Interleaved Distributed Parity_).
- **RAID 6:** Uporablja dva paritetna bita, ki sta oba porazdeljena. Neobčutljiv na hkratno odpoved **do dveh diskov**.
- **Gnezdena polja:** Kombinacija stopenj, npr. **RAID 6 + 0**.

**Pomembni parametri za ocenjevanje RAID polja:** izkoriščenost prostora (_Space Efficiency_), toleranca na napake (_Fault Tolerance_), verjetnost odpovedi polja (_Array failure rate_) ter učinkovitost branja in pisanja.