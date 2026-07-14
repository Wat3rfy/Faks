

**XML (eXtensible Markup Language)** oziroma razširljivi označevalni jezik je standard namenjen strukturiranemu zapisu podatkov. Čeprav je na prvi pogled podoben jeziku HTML, se od njega bistveno razlikuje po svojem **namenu**:

- **Namen prenosa in hrambe:** Za razliko od HTML, ki je bil razvit za prikaz informacij v brskalniku, je XML zasnovan za **prenos, hrambo in organizacijo podatkov**.
- **Splošna narava:** XML sam po sebi ne "naredi" ničesar; je le način, kako podatke ovijemo v značke, da postanejo strojno berljivi in hkrati razumljivi človeku.
- **Samopojasnjevalnost:** Ker si značke (tags) določimo sami, dokument sam opisuje svojo vsebino (npr. značka `<email>` jasno pove, da gre za elektronski naslov).

Razumevanje razlik med tema dvema jezikoma je ključno za razumevanje uporabnosti XML-ja v sodobnih informacijskih sistemih.

|Lastnost|HTML (HyperText Markup Language)|XML (eXtensible Markup Language)|
|:--|:--|:--|
|**Nabor značk**|Vnaprej določen (fiksni nabor, npr. `<h1>`, `<p>`, `<a>`).|Razširljiv – značke definiramo sami glede na naravo podatkov.|
|**Poudarek**|Videz dokumenta (formatiranje teksta, barve, postavitve).|Pomen in struktura dokumenta (kaj podatek predstavlja).|
|**Strožnost**|Dopušča napake (izpuščanje zaključnih značk, nepravilno gnezdenje).|Zahteva popolno skladnost (vsaka značka mora biti pravilno zaprta in gnezdena).|
|**Informacijska vrednost**|Ne daje vsebinskih informacij o avtorju, kategoriji ali času objave.|Omogoča bogat opis metapodatkov (npr. `<avtor>`, `<datum>`, `<kategorija>`).|

**Problem programske obdelave HTML:** Ker HTML nima fiksne podatkovne strukture, je ekstrakcija specifičnih podatkov iz njega (npr. telefonske številke iz spletne strani) izjemno zahtevna. XML ta problem reši tako, da podatek (npr. "301-286-aaaa") ovije v specifično značko `<PHONE>`, kar programski opremi omogoča takojšnjo identifikacijo vsebine.



XML dokument mora slediti strogim sintaktičnim pravilom, da ga lahko procesirajo univerzalna orodja (razčlenjevalniki).

### 3.1 Osnovne komponente

1. **XML deklaracija:** Vsak dokument se mora začeti z nizom, ki določa verzijo (in pogosto kodiranje), npr. `<?xml version="1.0" ?>`.
2. **Elementi:** So osnovni gradniki, ki jih sestavljata začetna značka, vsebina in zaključna značka (npr. `<vir>Heise</vir>`).
3. **Atributi:** Dodatne informacije o elementu, ki so zapisane znotraj začetne značke. Vrednost atributa mora biti vedno v narekovajih. Primer: `<novica naslov="Google ustavil...">`.
4. **Vsebina (CDATA):** Tekstovni podatki med značkami.
5. **Komentarji:** Zapisani so enako kot v HTML: `<!-- komentar -->`.



Da bi bil dokument sintaktično ustrezen po standardu W3C, mora izpolnjevati naslednje pogoje:

- **Korenski element:** Obstajati mora natanko en element (root element), ki vsebuje vse ostale elemente v dokumentu.
- **Uravnoteženost:** Vsaka začetna značka mora imeti pripadajočo zaključno značko.
- **Pravilno gnezdenje:** Značke se ne smejo prekrivati. Če odpremo značko `A` in nato `B`, moramo najprej zapreti `B` in šele nato `A`.
- **Občutljivost na velikost črk:** `<P>` in `</p>` v XML nista par; znački se morata ujemati do črke natančno.
- **Posebni znaki:** Znaki, kot je `<`, se morajo nadomestiti z ubežnimi nizi (npr. `&lt;`), da jih razčlenjevalnik ne zameša z začetkom nove značke.


XML dokumente si logično predstavljamo kot **drevesno strukturo**. Korenski element predstavlja deblo, podrejeni elementi pa veje. Na koncu vej so listi, ki vsebujejo dejanske podatke (CDATA). Ta hierarhična narava omogoča enostavno navigacijo in iskanje po dokumentu.

***

Dokumenti se delijo glede na to, kako strogo upoštevajo pravila:

1. **Pravilno strukturiran (well-formed):** Zadošča le osnovnim sintaktičnim pravilom XML.
2. **Veljaven (valid):** Je pravilno strukturiran in hkrati skladen z **XML shemo**.

### XML Shema (XSD)

Shema je ločen dokument, ki deluje kot "zakon" ali predpis za določen razred XML dokumentov. Njene funkcije so:

- Definira **slovar** dovoljenih elementov in atributov.
- Določa **strukturo** (vrstni red elementov) ter število ponovitev posameznih elementov.
- Določa **podatkovne tipe** (npr. ali mora biti vrednost niz, število ali datum).

V shemi (XSD) uporabljamo elemente, kot sta `xs:complexType` (za elemente, ki vsebujejo druge elemente) in `xs:sequence` (za določanje vrstnega reda). Ko imamo shemo, lahko poljuben XML dokument preverimo, ali je njena veljavna **instanca**.

***

Ker so podatki v bazah pogosto v relacijski obliki (tabele), XML pa je hierarhičen, poznamo različne načine preslikav glede na tip povezav med tabelami.

- **Povezava 1 : 1:** Podatke iz relacije B preprosto gnezdimo znotraj elementa relacije A.
- **Povezava 1 : n:** Za vsako vrstico v tabeli A ustvarimo element, znotraj katerega nanižemo več elementov, ki predstavljajo pripadajoče vrstice iz tabele B.
- **Povezava m : n:** Ta zahteva uporabo referenc. Uporabimo atributa **ID** in **IDREF** (ali IDREFS). Vsakemu elementu A in B dodelimo unikaten identifikator, v vezni relaciji R pa navedemo referenci na oba elementa.

***

Za delo z XML obstaja celoten ekosistem orodij:

1. **Urejevalniki:** Namenska orodja, kot so **Oxygen**, **XMLSpy** ali **EditiX**, omogočajo vizualno urejanje, samodejno dopolnjevanje značk in validacijo v realnem času. Za preprosta opravila zadoščata tudi Notepad ali Sublime Text.
2. **Orodja za transformacijo:** Omogočajo pretvorbo XML v druge formate, najpogosteje v HTML za prikaz na spletu.
3. **Programski vmesniki (API):**
    - **DOM (Document Object Model):** Celoten XML dokument prebere v spomin in zgradi drevesno strukturo, kar omogoča poljuben dostop in posodabljanje.
    - **SAX (Simple API for XML):** Dogodkovno voden vmesnik, ki dokument bere zaporedno (stream) in je primeren za zelo velike datoteke, ki ne gredo v spomin.
    - **Razčlenjevalniki (Parsers):** Knjižnice, kot je Apache Xerces, ki izvajajo nizkonivojsko branje in preverjanje skladnosti.

******

Zaradi razširjenosti XML standarda za izmenjavo podatkov so se razvili sistemi za upravljanje podatkovnih baz (SUPB), ki podpirajo ta format, da bi se izognili nepotrebnemu pretvarjanju med formati.

### 7.1 Vrste XML baz podatkov

- **Baze, ki podpirajo XML (XML-enabled):** To so klasične relacijske baze (npr. Oracle, IBM DB2, MS SQL Server, PostgreSQL), ki so dodale podporo za XML. Podatke lahko shranjujejo kot:
    - **CLOB** (Character Large Object) – XML je shranjen kot dolg niz besedila.
    - **Shredding** – XML se ob uvozu razbije na množico relacijskih tabel.
    - **Native XML Type** – poseben podatkovni tip po ISO standardu, ki omogoča učinkovito hrambo in poizvedovanje.
- **Naravne XML baze (Native XML Databases):** Njihov logični model temelji neposredno na XML. Dokumenti so osnovna enota shranjevanja. Primer takšne baze je **eXist-db**. Te baze pogosto uporabljajo:
    - **Kolekcije:** Logične skupine dokumentov (podobno kot mape v datotečnem sistemu).
    - **Poizvedovalni jeziki:** Predvsem **XPath** in **XQuery**.
    - **XSLT:** Za transformacijo podatkov neposredno ob izhodu iz baze.

### 7.2 Podpora v MySQL

MySQL ponuja specifične funkcije za delo z XML podatki, čeprav nima polne "native" podpore kot nekateri večji konkurenti:

- **Izvoz v XML:** Preko ukazne vrstice z uporabo stikala `--xml`, kar rezultate poizvedbe SELECT avtomatsko preoblikuje v XML strukturo s polji `<field>` in vrsticami `<row>`.
- **Uvoz podatkov:** Ukaz `LOAD XML LOCAL INFILE` omogoča branje XML datotek neposredno v relacijske tabele, kjer atributi ali pod-elementi postanejo vrednosti v stolpcih.
- **Poizvedovanje in spreminjanje:**
    - `ExtractValue(xml_frag, xpath_expr)`: Iz XML fragmenta izvleče vrednost na podlagi XPath izraza.
    - `UpdateXML(xml_frag, xpath_expr, new_xml)`: Zamenja del XML dokumenta z novo vrednostjo na točno določenem mestu, definiranem z XPath.

Ta integracija omogoča hibridne sisteme, kjer se ključni relacijski podatki dopolnjujejo s fleksibilnimi XML podatki v istem okolju.
***

XQuery je deklarativni povpraševalni jezik, zasnovan za pridobivanje in obdelavo podatkov iz XML dokumentov. Za navigacijo po drevesni strukturi dokumentov uporablja izraze XPath.

XPath (XML Path Language) je namenjen navigaciji po vozliščih XML dokumenta. Deluje na principu naslavljanja poti, kar omogoča izbiro specifičnih delov dokumenta, kot so elementi, atributi ali besedilne vsebine. XML obravnava kot drevesno strukturo, po kateri se premika z uporabo poti in filtrov.

XQuery je potreben za obdelavo informacij v formatu XML, ki so hierarhični. Omogoča iskanje in združevanje podatkov ter transformacijo teh podatkov v nove oblike, kot so poročila HTML ali novi XML zapisi.

SQL je zasnovan za relacijske baze podatkov. XQuery pa je prilagojen drevesni strukturi dokumentov

FLWOR je akronim za pet ključnih ukazov jezika XQuery: **For, Let, Where, Order by** in **Return**. Predstavlja ogrodje za obdelavo, filtriranje in transformacijo XML podatkov.

Funkcije komponent:

- **For**: Iteracija po zaporedju vozlišč.
- **Let**: Prirejanje vrednosti spremenljivkam.
- **Where**: Filtriranje podatkov po pogojih.
- **Order by**: Razvrščanje rezultatov.
- **Return**: Konstrukcija končnega izpisa.

  
XSLT (Extensible Stylesheet Language Transformations) je jezik za transformacijo XML dokumentov v druge formate, kot so HTML, XML, prosti tekst ali PDF.

XQuery omogoča da s sorazmerno malo kode opišemo kompleksne operacije, podpira rekurzijo - omogoča iskanje po hiearhičnih strukturah ali grafih. 

XQuery stavki so krajši od SQL in od XSLT in uoprablja bolj naravno člevku prijazno sintakso. Hkrati pa je tudi predvidljiv in logičen - temelji na XPath.

Lahko ga uporabljamo za hiearhične strukture kot tudi tabelarične strukture.

***
XQuery je občutljiv na velikost črk.
Spremenljivke odločamo z `$`.

Datoteke si lahk predstavljamo kot drevo. Vsako vozlišče je element ki lahko vbsebuje atribute in druga vozlišča. 

Do otrok lahko dostopamo z uporabo poševnic kjer `/` izbere neposredne otroke, `//` pa otroke na vseh nivojih pod staršem.  

Lahko uoprabljamo tudi `.` ki izbere trenutno vozlišče, `..` izbere očeta, `@` pa atribut.

Če ne vemo imen vozlišč lahko uporabimo `*` kar izbere vse: `parent/*` - vsi otroci. `parent/@*` vsi atributi.

`parent//node()` - izbere vse ne glede na to kaj je - elementi, atributi,...

Za filtriranje lahko uporabljamo predikate - `/book[@atribut = 'en']`,... 

Te prosojnice podrobno razlagajo **izraze FLWOR**, ki so hrbtenica jezika XQuery. Akronim **FLWOR** stoji za: **F**or, **L**et, **W**here, **O**rder by in **R**eturn.



FOR – Iteriranje (Zanka)
*  Beseda `for` se uporablja za **iteracijo** (ponavljanje) čez zaporedje vrednosti ali vozlišč.
*  Za vsak element v zaporedju se spremenljivki (npr. `$x`) dodeli vrednost in izvede se preostanek poizvedbe.
*  `for $x in (1 to 5)` bo ustvaril 5 ločenih XML elementov, za vsako številko posebej.

AT – Štetje iteracij
* Ko uporabljamo `for`, lahko z besedo `at` dodamo še eno spremenljivko, ki služi kot **števec** (indeks) trenutne iteracije.
* Koristno, če želimo rezultate oštevilčiti (npr. `1. Everyday Italian, 2. Harry Potter...`).
*   **Funkcija `data()`:** Uporablja se za pridobitev same vsebine (besedila) elementa, brez XML značk (tagov).

LET – Dodeljevanje vrednosti (Brez zanke)
*  Za razliko od `for`, beseda `let` **ne povzroči iteracije**.
*  Spremenljivki dodeli celotno zaporedje hkrati.
*   Če z `let $x := (1 to 5)` vrnemo rezultat, bomo dobili **en sam** XML element, ki vsebuje vsa števila skupaj (`<test>1 2 3 4 5</test>`), namesto petih ločenih elementov.

WHERE – Filtriranje
*   Omogoča postavljanje **pogojev**, ki jim morajo podatki zadoščati, da so vključeni v končni rezultat.
*  `where $x/price > 30` izloči vse knjige, ki so cenejše od 30.

ORDER BY – Urejanje (Sortiranje)
*   Določa vrstni red izhodnih podatkov.
*   Sortiramo lahko po poljubnem elementu ali atributu (npr. po kategoriji, nato po naslovu).

RETURN – Oblikovanje izhoda
*    Določi, kaj točno naj poizvedba vrne in v kakšni obliki.
*  Če želimo vrniti več različnih elementov (npr. naslov in leto), jih ločimo z **vejico** in postavimo v **oklepaje**, da zagotovimo pravilen vrstni red izvajanja.

Te prosojnice pojasnjujejo zelo pomembno razliko v XQuery sintaksi: razliko med **primerjavo vrednosti** in **splošno primerjavo**.

XQuery loči med dvema skupinama operatorjev:

**Primerjava vrednosti** (`eq`, `ne`, `lt`, `le`, `gt`, `ge`) - ti operatorji so namenjeni primerjanju **točno dveh posameznih (atomarnih) vrednosti**.
Na levi in desni strani mora biti natanko en element. Če jih je več ali nič, poizvedba vrne napako.


**Splošna primerjava** (`=`, `!=`, `<`, `<=`, `>`, `>=`) - ti operatorji so bolj prilagodljivi in delujejo na **zaporedjih (listah) vrednosti**.
Rezultat je resničen (`true`), če **vsaj eden** element iz prvega zaporedja ustreza **vsaj enemu** elementu iz drugega zaporedja.


V primeru:
`where $b/title eq "Harry Potter"`
XQuery pogleda naslov knjige. Ker ima vsaka knjiga v tem primeru **le en naslov**, operacija `eq` deluje pravilno. Primerjamo en naslov z enim nizom besedila.

Primer, ki vrne **napako (error)**:
`where $b/author eq "Kurt Cagle"`


Knjiga  "XQuery Kick Start" ima **več avtorjev** (James McGovern, Per Bothner, Kurt Cagle ...).
Izraz `$b/author` zato ne vrne ene vrednosti, ampak **celoten seznam (zaporedje) avtorjev**.
Operator `eq` ne ve, kako bi primerjal seznam z enim imenom, zato "obupa" in javi napako.

Uporaba operatorja `=`:
`where $b/author = "Kurt Cagle"`

Operator `=` deluje po principu "ali je v tej skupini vsaj eden, ki mu je ime Kurt Cagle?".
XQuery gre čez celoten seznam avtorjev za določeno knjigo.
Če med njimi najde Kurta Caglea, je pogoj izpolnjen (`true`), ne glede na to, koliko drugih avtorjev je še na seznamu.

