V računalništvu in podatkovni znanosti vektorje najpogosteje predstavimo kot urejen seznam števil. Vsako število v tem seznamu predstavlja koordinato vektorja v večdimenzionalnem prostoru.

#### **Pomen vektorjev v svetu podatkov**
Vektorji lahko predstavljajo kompleksne podatke, dimnezije predstavljajo neke lastnosti, pripadajoči skalar pa izrazitost te lastnosti.

Proces pretvorbe se imenuje **vektorizacija** ali ustvarjanje **vložitev (embeddings)**. Rezultat je visokodimenzionalni vektor, ki predstavlja pomen izvirnega podatka.

#### **Predstavitev vektorskih podatkovnih baz**

**Vektorska podatkovna baza (VPB)** je specializiran sistem za shranjevanje, upravljanje in iskanje podatkov v obliki večdimenzionalnih vektorjev. Njihov primarni namen ni shranjevanje surovih podatkov, temveč njihovih numeričnih predstavitev.

V nasprotju s tradicionalnimi relacijskimi ali NoSQL bazami, ki podatke iščejo na podlagi natančnih ujemanj (npr. `WHERE ime = 'Janez'`), vektorske baze omogočajo iskanje na podlagi **podobnosti**.

To pomeni, da lahko poiščemo podatke, ki so po vsebini ali pomenu blizu naši poizvedbi, tudi če se natančno ne ujemajo.

### **Ustvarjanje in lastnosti vektorskih vložitev**

#### **Proces ustvarjanja vektorjev**

Vektorji, shranjeni v VPB, niso trivialni. Nastanejo kot rezultat kompleksne strojne obdelave podatkov, kjer modeli iz podatkov izluščijo številne, pogosto skrite in abstraktne lastnosti.

Za generiranje teh vektorskih predstavitev se uporabljajo metode, kot so **modeli strojnega učenja**, specializirani algoritmi za **vložitve besed (word embeddings)** in drugi **algoritmi za ekstrakcijo značilnosti (feature extraction)**.

Osnovni cilj tega procesa je, da se semantično podobni vhodni podatki preslikajo v vektorje, ki so si v večdimenzionalnem prostoru blizu. Podatki, ki so si po pomenu različni, bodo imeli vektorje, ki so v prostoru bolj oddaljeni.

#### **Lastnosti vektorskega prostora**

Vektorski prostor, ki ga ustvarijo modeli za vlaganje, ni naključen. Ima notranjo strukturo, ki odraža odnose in analogije iz resničnega sveta.

Znan primer je zmožnost izvajanja matematičnih operacij z vektorji, ki imajo smiseln rezultat. Na primer, z odštevanjem vektorja za besedo "moški" od vektorja za "kralj" in prištevanjem vektorja za "ženska" dobimo vektor, ki je zelo blizu vektorju za besedo "kraljica".

Ti odnosi veljajo tudi za druge koncepte, kot so glagolski časi (hoja -> hodil), razmerja med državami in glavnimi mesti (Slovenija -> Ljubljana) ali druge semantične povezave.

#### **Večmodalnost vložitev**

Moč vektorskih vložitev je v njihovi zmožnosti predstavljanja različnih vrst podatkov. Obstajajo specializirani modeli, ki pretvarjajo **avdio posnetke**, **besedila**, **slike** in **video posnetke** v enoten vektorski prostor.

To omogoča iskanje in primerjavo med različnimi tipi podatkov. Uporabnik lahko na primer z besedilnim opisom "sončni zahod na plaži" poišče vizualno podobne slike ali celo glasbo, ki vzbuja podobno razpoloženje.

### **Delovanje in prednosti vektorskih podatkovnih baz**

#### **Dve fazi delovanja: polnjenje in poizvedovanje**

Delovanje vektorske podatkovne baze poteka v dveh glavnih korakih. Prvi korak je **polnjenje baze**, kjer izvirne podatke (npr. dokumente, slike) pretvorimo v vektorje z uporabo izbranega modela za vlaganje. Ti vektorji se nato skupaj z referenco na izvirni podatek shranijo v bazo.

Drugi korak je **poizvedovanje**. Ko uporabnik vnese poizvedbo (npr. iskalni niz), se ta poizvedba z **istim modelom za vlaganje** pretvori v vektor. Baza nato s pomočjo optimiziranih algoritmov poišče vektorje, ki so poizvedbenemu vektorju najbližji.

#### **Prednosti uporabe VPB**

Glavna prednost vektorskih baz je **učinkovito iskanje podobnih podatkov** z merjenjem bližine v vektorskem prostoru. To omogoča iskanje, ki temelji na **semantični relevantnosti** namesto na natančnem ujemanju ključnih besed.

VPB so visoko optimizirane za analitične poizvedbe, kot so **gručenje (clustering)**, kjer podatke samodejno združujemo v skupine podobnih, in **kategorizacija**, kjer nove podatke uvrščamo v obstoječe kategorije.

### **Metrike za merjenje podobnosti**

#### **Opredelitev metrik razdalje**

Da bi lahko določili, kako "blizu" sta si dva vektorja, potrebujemo matematične funkcije, znane kot **metrike razdalje** ali **mere podobnosti**. Te funkcije izračunajo numerično vrednost, ki predstavlja "razdaljo" med dvema vektorjema.

Izbira prave metrike je ključna, saj različne metrike zajemajo različne vidike podobnosti in so primerne za različne tipe podatkov in aplikacij.

#### **Najpogostejše metrike razdalje**

**Evklidska razdalja (L2 norma)** je najbolj intuitivna metrika, ki meri najkrajšo premico med dvema točkama v prostoru. Zelo je občutljiva na velikost (magnitudo) vektorjev.

**Manhattanska razdalja (L1 norma)** sešteje absolutne razlike med koordinatami vektorjev. Uporabna je, kadar želimo poudariti razlike v posameznih značilnostih, ne le celotne razdalje.

**Kosinusna podobnost** meri kot med dvema vektorjema. Ta metrika je izjemno pomembna pri iskanju po besedilih, saj je osredotočena na smer vektorjev (semantični pomen) in ignorira njihovo velikost (npr. dolžino dokumenta). Manjši kot pomeni večjo podobnost.

**Skalarni produkt** upošteva tako kot med vektorjema kot tudi njuni velikosti. Večja pozitivna vrednost pomeni večjo podobnost v smeri in velikosti.

**Jaccardova podobnost** se uporablja za primerjavo dveh množic in meri razmerje med velikostjo preseka in velikostjo unije teh množic. Pogosto se uporablja pri priporočilnih sistemih.

### **Optimizacija iskanja: Indeksiranje**

#### **Problem iskanja v velikih bazah**

Preprosto primerjanje poizvedbenega vektorja z vsakim vektorjem v bazi (pristop, znan kot **ravni indeks** ali **brute-force search**) je izjemno računsko potratno in postane neizvedljivo pri milijonih ali milijardah vektorjev. Časovna kompleksnost takega iskanja je linearna.

Zato vektorske podatkovne baze uporabljajo napredne **indeksirne strukture**, ki drastično pospešijo iskanje, čeprav včasih na račun majhne izgube natančnosti.

#### **Približno iskanje najbližjih sosedov (ANN)**

Ker popolna natančnost pogosto ni potrebna, večina sodobnih VPB uporablja algoritme za **približno iskanje najbližjih sosedov (Approximate Nearest Neighbor - ANN)**. Ti algoritmi omogočajo bistveno hitrejše iskanje z iskanjem "dovolj dobrih" zadetkov namesto absolutno najbližjih.

#### **Pogosti indeksirni algoritmi**

**Lokalno občutljivo zgoščevanje (Locally Sensitive Hashing - LSH)** je tehnika, ki podobne vektorje z visoko verjetnostjo umesti v iste "koše" (buckets) s pomočjo posebnih zgoščevalnih funkcij. Iskanje se nato omeji le na nekaj relevantnih košov.

**ANNOY (Approximate Nearest Neighbors Oh Yeah)** je knjižnica, ki zgradi več naključnih drevesnih struktur za razdelitev vektorskega prostora. Iskanje poteka s prečkanjem teh dreves, kar je veliko hitreje kot pregledovanje vseh vektorjev.

Drugi napredni algoritmi, kot je **HNSW (Hierarchical Navigable Small World)**, gradijo večplastne grafovske strukture, ki omogočajo izjemno hitro in natančno navigacijo do najbližjih sosedov v prostoru.

### **Primeri uporabe vektorskih podatkovnih baz**

#### **Priporočilni sistemi in e-poslovanje**

Vektorske baze so temelj sodobnih priporočilnih sistemov. Tako uporabniki kot produkti so predstavljeni z vektorji. Sistem nato uporabniku priporoča produkte, katerih vektorji so v prostoru najbližji vektorju uporabnika, kar kaže na podobnost interesov in lastnosti.

#### **Pridobivanjem obogatena generacija (RAG)**

**RAG (Retrieval-Augmented Generation)** je ključna arhitektura za izboljšanje delovanja velikih jezikovnih modelov (LLM). Podatki podjetja (dokumenti, baze znanja) se razdelijo na manjše kose, pretvorijo v vektorje in shranijo v VPB.

Ko uporabnik postavi vprašanje, sistem najprej v VPB poišče najbolj relevantne kose informacij. Te informacije nato posreduje jezikovnemu modelu kot kontekst, kar mu omogoča, da generira odgovore, ki so natančni, ažurni in temeljijo na specifičnih podatkih, hkrati pa se zmanjša tveganje za generiranje napačnih informacij (halucinacije).

#### **Popularne vektorske baze**

Na trgu obstaja širok nabor vektorskih baz, ki se delijo na **namenske vektorske baze** (npr. **Pinecone**, **Milvus**, **Weaviate**, **Chroma**) in **tradicionalne baze**, ki so pridobile podporo za vektorsko iskanje (npr. **PostgreSQL** z razširitvijo `pgvector`, **Elasticsearch**, **Redis**). Izbira je odvisna od specifičnih potreb aplikacije, obsega podatkov in želenega ekosistema.