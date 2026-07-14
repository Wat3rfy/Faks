**Namen in potreba po podatkovnih skladiščih**

Večina sistemov je zasnovanih za tekoče poslovanje - hranijo le trenutne vrednosti podatkov. Za strateđke odločitve pa potrebujemo **daljše časovno obdobje**, **infomracije z več aplikacij** vse skupaj.

To lahko dosežemo z **integracijskim vmesnikom oz. virutalna integracija** - sistem se pretvarja da so vsi podatki na enem mestu v resnici pa jih sproti išče po virih - vsak vir ima svojo ovojnico ki neko zahtevo prevede v jezik ki ga vir razume da dobi podatke. Ker sistem poizveduje direktno v produkcijske baze lahko velika zahtevna poizvedba - upočasni delovanje dejanske baze, saj se uporabljata isti procesor in disk. 

Če je eden od virov nedosegljiv celotna analiza ne more biti končana.

**Fizična integracija oz. podatkovno skladišče** - podatki so preneseni v ločeno namensko enoto. Ključen je ETL proces oz. extract, transform, load kjer podatke iz virov izvlečemo, preoblikujemo (poenotimo, foramtiramo) in naložimo v skladišče.

Ker so podatki fizični shranjeni v skladišču, analize ne obremenjujejo primarnih sistemov. Konflikti pa so razrešeni že v procesu shranjevanja podatkov.

Pri integr. modelu so podatki vedno zadnji možni - sveži, pri podatkovnem skladišču pa je pomembnejša hitrost analize, stabilnost in zgodovina.

***

Podatkovno skladišče je potrebno saj informacije v vakuumu ne nareišejo celotne slike in lahko dobimo napačno idejo - integriranje vseh področij nekega sistema je ključno za natančno analizo.

Pomembna je **vsebinska organizacija**, klasični transakcijski sistemi so zgrajeni okoli **procesov** - proces vpisa, proces izdaje računa... Podatkovno skladišče pa procese "razbije" in podatke reorganizira okoli **poslovnih entitet** - študent, kupec,....
Npr. namesto da bi imeli ločene tabele za "aplikacijo za knjižnico" in "aplikacijo za študentsko prehrano", skladišče vse te podatke združi pod entiteto **Študent**.
Analitika ne sprašuje "kako poteka vpis", ampak "kakšen je profil študenta, ki uspešno opravi izpite". Skladišče je torej strukturirano tako, da odgovarja na vprašanja o vsebini (kdo, kaj, kje), ne o postopkih.

**Integriranost** je najtežji del gradnje skladišča. Podatki prihajajo iz različnih virov (knjižnica, kadrovska, računovodstvo), ki med seboj ne komunicirajo in pogosto uporabljajo različne standarde.
Lahko se pojavi nekonsistentnost - višina študenta je nekje lahko zapisana v cm nekje v metrih. Nekje je zapisan s celotnim imenom nekje le po priimku,...

Skladišče te podatke med prenosom (ETL proces) "očisti" in poenoti. Ko podatek vstopi v skladišče, mora imeti **enoten format**.

Podatkovno skladišče deluje kot **arhiv** - vsak zapis v skladišču ima zapisan čas. Če se študent preseli, skladišče ne prepiše starega naslova z novim, ampak doda nov zapis z novim časovnim intervalom veljavnosti.
To omogoča analizo trendov.

**Nespremenljivost** najlažje razumemo skozi razliko v operacijah nad bazo. V transakcijski bazi nenehno izvajamo UPDATE (posodabljanje) in DELETE (brisanje). V podatkovnem skladišču teh dveh operacij v klasičnem smislu ni.

Podatki se v skladišče le nalagajo (INSERT). Ko je podatek enkrat v skladišču, ga analitične aplikacije ne smejo spreminjati.
Če analitik danes izvede poročilo o prodaji za lanski december, mora dobiti popolnoma enak rezultat kot analitik, ki bo isto poizvedbo zagnal čez en teden. 
    
Izvajanje operacij delimo v naslednji skupini.
OLTP oz. **On Line Transaction Processing** je procesiranje tekočih operacij kjer izhaja iz trenutnega stanja podatkov direktno iz virov medtem ko OLAP oz. **On Line Analytical Processing** deluje v podatkovnem skladišču in izvaja svoje procesiranje tam.

TP vidi le trenutno verzijo - nič zgodovine - AP vidi vse.
TP se ukvarja z dinamičnimi podatki - AP s statičnimi.
TP ima veliko število transakcij - AP malo.
TP je predvidljivo - kupi, plačaj, tiskaj,... AP ni predvidljivo - vprašanja so številna.

Poznamo vče načinov zbiranja / obdelovanja podatkov za AP. Vsem je skupen proces ETL - extract, transform, load.

Najprej imamo **generično dvonivojsko arhitekturo** -  vsi podatki iz vseh virov se stekajo v eno centralno podatkovno skladišče. Prednost je da obstaja en vir resnice - konsistentnost, a je gradnja in vzdrževanje kompleksno saj mora zajeti celotno podjetje hkrati.

**Neodvisna področna skladišča** imajo za vsak oddelek lastno neodvisno področno skladišče kar je hitreje za vzpostavit ampak vodi do nekonsistentnosti podatkov - marketing ima drugačne številke o prodaji kot finance (podvojeni podatkim različne definicije) - ni enotnega pogleda.

**Odvisna področna skladišča** - ustvari se centralno podjetniško podatkovno skladišče nato se iz tega vira podatki pretakajo v manjša **področna skladišča** - zagotavlja konsistentnost in hitrejši dostop do podatkov.

Orodja za dostop do podatkovnega skladišča so številna. Mora podpirati **rutinsko analizo** in nepredvidena vprašanja.

Uporabljajo se orodja kot so **orodja za poročila in poizvedbe** oz. **generatorji** - ustavarjajo standardizirane dokumente in poročila, za poizvedbe pa SQL, grafični vmesniki,..., **direktorski informacijski sistem** - grafični prikazi za vodstva (omogoča hiter pogled v ključne kazalnike uspešnosti), **OLAP orodja** - večdimenzionalni pregled podatkov - npr. po času regiji in izdelku hkrati in orodja za data mining oz. iskanje vzorcev.

**ER** model je namanjen transakcijskim sistemom *TP*. Zagotavlja celovitost podatkov in čim manjše podvajanje - normalizacija.

**Zvezdna shema** je osnova za AP - poizvedbe in poročanje je čim hitrejše in ne obremenjuje dejanskih delovnih baz.

Ko modeliramo neko podjetje je preveč podatkov za eno zvezdno shemo zato jih **dekomponiramo** v več zvezdnih shem. Standardni pristop pravi da vsaka tabela dejstev / center zvezde predstavlja en poslovni proces - ker imamo več teh je noramlno da dobimo več zvezdnih sistemov.


