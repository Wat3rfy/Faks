Tretja plast v modelu je **omrežna plast**. 

Zagotavlja prenos podatkovnih enot od izvorne do ciljne naprave, ne glede na položaj v omrežju. 

Izvaja 
- **usmerjanje**, 
- **naslavljanje pošiljatelja in prejemnika na globalni ravni** 
- **signaliziranje o morebitinh napakah v omrežju**


Postopek se začne ko **omrežna plast sprejme segmente s transportne plasti** in izvede **enkapsulacijo**. Segmentom se dodajo **glava**, ki vsebuje **logične naslove**, kot so IP naslovi, s čimer nastanejo **paketi**. 

Paketi so osnovne enote podatkov, ki potujejo skozi omrežje.

Omrežna plast  določa najboljšo pot skozi omrežje. 

**Usmerjanje** se izvaja na usmerjevalnikih - naprave v jedru omrežja - in so prisotne na vsakem vozlišču poti. 

Omrežna plast je tako **implementirana v vseh omrežnih napravah**, ki sodelujejo pri prenosu.

Treba je razlikovati med vlogama omrežne in transportne plasti. 

Omrežna plast je odgovorna za **komunikacijo od računalnika do računalnika**, torej, zagotavlja dostavo paketa do pravilne naprave v omrežju.

Po drugi strani pa **transportna plast** vzpostavlja logično **povezavo od procesa do procesa**, kar zagotavlja, da podatki dosežejo točno določeno aplikacijo na ciljni napravi.

***

Omrežna plast **segment** iz transportne plasti **enkapsulira** v **paket** na drugi strani pa **sprejme paket** ki je bil **dekapsuliran** iz **okvirja** in pošlje **segment** v transportno plast.

***

**Usmerjevalnik** je omrežna naprava, ki deluje na omrežni plasti. 

Njegova glavna vloga je transportiranje paketov po jedru omrežja, pri čemer **vsebuje vse funkcionalnosti prve, druge in tretje plasti** da lahko **omogoča povezovanje med različnimi vrstami fizičnih medijev in protokolov**. 

Ima več različnih fizičnih vmesnikov *ports* za **večjo združljivost**, če tega ne bi bilo potem bi lahko router povezali samo z napravami ki uporabljajo enako vrsto kabla. 

Enako velja za **protokole**, kjer ima router implementiranih več protokolov, zato da lahko usprešno upravlja z več različnimi vrstami okvirjev - torej podatki lahko pridejo preko etherneta poslati pa jih rabi preko wifi-ja to npr. potrebuje implementacijo obeh protokolov.

Izvaja dve ključni funkciji: **usmerjanje** in **posredovanje**. 

Usmerjanje je postopek določanja poti paketa. 

Posredovanje pa se nanaša na ugotavljanje na kateri **interface** naj pošlje paket glede na odločitev poti. 

Posredovanje se izvaja znotraj posameznega usmerjevalnika. Ko paket pride na vhodni vmesnik, mora usmerjevalnik določiti, na katera izhodna vrata ga bo poslal naprej. To določi s **posredovalno tabelo** (forwarding table), v kateri je zapisno kateri izhodni vmesniki vodijo kam.

Usmerjanje se nanaša na **določanje celotne poti** paketa od izvornega pošiljatelja do končnega prejemnika. Za razliko od posredovanja **je kolektivno delo vseh omrežnih naprav na poti**, ki s pomočjo usmerjevalnih protokolov in algoritmov izmenjujejo informacije o stanju omrežja. Ti algoritmi izračunavajo najboljše poti skozi omrežje, iz tega pa se nato polnijo in posodabljajo posredovalne tabele v posameznih usmerjevalnikih.

***

Omrežna plast nudi nabor storitev
- **zagotovljanja dostave paketov**, 
- **zagotavljanje dostave v določenem času**, 
- **ohranjanje vrstnega reda paketov**, 
- **zagotavljanje določene proste pasovne širine** *bit rate*, 
- **nadzor nad varianco zakasnitve (jitter)** *zakasnitev je čas ki ga paket potrebuje od serverja do clienta, jitter pa je nihanje tega časa.*
- **varno komunikacijo**, kot so **zaupnost, integriteta in avtentikacija**.

V praksi Internet ne zagotavlja nobene izmed naštetih storitev, saj deluje po modelu "best-effort". Ta model pomeni, da omrežje ne daje nobenih garancij glede pasovne širine, izgube paketov, vrstnega reda ali časovnih zakasnitev, temveč si prizadeva le za čim boljši prenos podatkov glede na trenutne razmere.


V primerjavi z Internetom obstajajo drugi modeli, kot je **ATM** (Asynchronous Transfer Mode), ki lahko zagotavljajo specifične storitve. Model **CBR** (Constant Bit Rate) pri ATM omrežjih zagotavlja konstantno pasovno širino, dostavo brez izgub, ohranjanje vrstnega reda in časovnih okvirjev, medtem ko model **ABR** (Available Bit Rate) nudi manj stroge garancije, vendar še vedno vključuje nekatere mehanizme za obvladovanje zamašitev.

***

Omrežja se na omrežni plasti delijo na **povezavna** in **nepovezavna**. 

Povezavna omrežja, znana tudi kot omrežja z navideznimi vodi (Virtual Circuits), zahtevajo **predhodno vzpostavitev logične povezave** med pošiljateljem in prejemnikom. V tem modelu vsi paketi znotraj ene seje sledijo vnaprej določeni poti skozi omrežno infrastrukturo.

Nasprotno od tega **nepovezavna ali datagramska omrežja** delujejo **brez predhodne vzpostavitve zveze**. Vsak paket se obravnava neodvisno od ostalih.

Usmerjevalniki na podlagi ciljnega naslova v vsakem paketu posebej odločajo o nadaljnji poti, kar pomeni, da lahko paketi istega sporočila do cilja prispejo po **različnih poteh** in v **poljubnem vrstnem** redu.

Internet spada med nepovezavna omrežja.

***

Prenos podatkov preko **navideznega voda** poteka v treh ločenih fazah: najprej se izvede **vzpostavitev povezave**, nato sledi **faza prenosa podatkov**, po zaključku pa se **povezava poruši oziroma sprosti**.

Vsak router hrani **posredovalno tabelo** ki določa kam grejo podatki. Vsak paket ki vstopi v usmerjevalnik vsebuje identifikator voda s katerega je prišel na podlagi katerega iz tabele prebere ID voda kamor mora biti posredovan.

Prvotno se pošlje **setup packet** ki edini vsebuje globalni ciljni naslov. Prvi router ki dobi paket izračuna najboljšo pot, preden posreduje paket preveri svoje proste vmesnike in povezavi dodeli nek prost vemsnik ki vodi do naslednjega routerja. Router naredi začasen vnos v svoji switching tabeli ki vhodnemu ID-ju dodeli pripadajoč izhodni vmesnik in nek ID recimo 12. Vsak naslednji router ponovi postopek tako da ID-ju dodeljenemu na prejšnjemu routerju dodeli vmesnik in svoj nov neuporabljen ID za naslednji usmerjevalnik s čimer se ustvari pot in zaporedje ID-jev katere routerji prepoznajo in pravilno usmerijo naprej.

***

**Datagramska omrežja** delujejo brez predhodne faze vzpostavljanja povezave. 

Usmerjevalniki ne hranijo nobenih informacij o stanju ali zgodovini komunikacijskih tokov. Vsak paket je obravnavan kot **samostojna enota**, saj vsak paket vsebuje naslov cilja.

Usmerjevalniki se zanašajo izključno na ciljni naslov v paketu. Na podlagi tega sproti odloča, kam bo paket posredoval naprej. To pomeni da lahko paketi, ki pripadajo istemu sporočilu, potujejo po različnih poteh, odvisno od razmer v omrežju.

Lahko se zgodi da pridejo v napačnem vrstnem redu ali pa da se izgubijo.

***

Ko pride paket z naslovom v usmerjevalnik mora vedeti na kateri interface ga mora poslati. To dosežemo s posredovalno tabelo kjer se hranijo naslovi in pripadajoči interfaci kamor se morajo paketi s temi naslovi poslati.

Ker bi bilo hranjenje kot iskanje v tej tabeli ki bi hranila vsak ip naslov bilo nemogoče se uporablja iskanje po predponi kjer se glede na najdaljšo ujemajočo predpono odloči kam gre paket. 

V tabeli je torej določeno na na katerem naslovu in interfacu je naslednji skok da vsi paketi z določeno predpono pridejo do cilja. Če ne paše nikamor gre na privzeti vmesnik.
Torej tabela vsebuje prefix, interface, gateway.


Te tabele se polnijo na različne načine.

Ob prikljuičitvi nekega omrežja nastavimo ip vmesnika s čimer se v tabelo za ta vmesnik zapiše predpona tega omrežja.

Lahko statično usmerjamo promet oz. mi ročno vnašamo podatke v to tabelo.

Dinamično usmerjanje pa je proces kjer si usmerjevalniki izmenjujejo informacije o tem v katera omrežja so priključena. S temi informacijami potem vsak router s svojimi algoritmi sestavi svojo tabelo.

Te usmerjevalni algoritmi so precej počasni - nekaj sekund.

***

Internet temelji na dejstvu da so končni sistemi pametni in da znajo sami popravljati napake in izvajati manjkajoče storitve. Dodajanje novih aplikacij je precej preprosta.

***

Na omrežni plasti je edini protokol IP protokol in je univerzalen standard s katerim se dela povsod. Služi kot most med aplikacijskim delom in tehnološkim delom.

Poleg usmerjanja in posredovanja imata glavno vlogo tudi **IP protokol** in **ICMP protokol**.

***

**IP protokol**

Paket je osnovna enota podatkov ki se prenaša po omrežju z uporabo IP protokola. Je binarni niz sestavljen iz **glave** in  dejanskih **podatkov**.

- **VER** (4 biti) - verzija protokola (lahko je 4 ali 6)
- **HEADER LENGTH** (4 biti) - dolžina glave paketa. Pove kjer se glava konča in kje se začnejo dejanski podatki. Kodira dolžino 32 bitov, kjer je najmanjša vrednost 5 oz. *0101* - torej $5 \cdot 32 = 20$ bajtov, lahko pa gre do $15$ bajtov oz. *1111*. To izhaja iz polja za opcije.
- **TYPE OF SERVICE** (8 bitov) - uporablja se za določanje prioritete in kakovosti storitve. To je ponavadi uporabno le v privatnih omrežjih.
- **LENGTH** (16 bitov) - dolžina paketa **glava + podatki** v bajtih - 16 bitno polje pomeni 65.535 bajtov čeprav je v praksi ponavadi omejena na 1500, najmanjša pa 20 bajtov.
- **IDENTIFIER** (16 bitov) - ID paketa. Če se paket med prenosom razbije na manjše dele (fragmentacija), vsi deli obdržijo isti ID, da jih ciljna naprava lahko ponovno sestavi.
- **FLAGS**  (3 biti) -  Kontrolni biti za fragmentacijo. Povedo, ali je paket dovoljeno fragmentirati in ali mu sledi še več fragmentov.
- **FRAGMENT OFFSET**  (13 bitov) -  Določa offset fragmenta v prvotnem paketu. Enota je 8 bajtov. To omogoča pravilno zaporedje pri ponovnem sestavljanju.
- **TIME TO LIVE - TTL** (8 bitov) - Števec, ki preprečuje neskončno kroženje paketa v primeru napak v usmerjanju. Vsak usmerjevalnik, skozi katerega gre paket, zmanjša to vrednost za 1. Ko doseže 0, se paket zavrže.
- **UPPER LAYER / PROTOCOL** (8 bitov) - Identificira protokol višjega nivoja, ki se nahaja v polju s podatki. Najpogostejši vrednosti sta 6 za TCP in 17 za UDP.
- **INTERNET CHECKSUM** (16 bitov) -  Nadzorna vsota, ki služi preverjanju integritete glave paketa. Vsak usmerjevalnik jo mora ob spremembi TTL polja ponovno izračunati. Če se vsota ne ujema, se paket zavrže zaradi napake. Ponovno računanje checksuma je zelo potratno.
- **SOURCE IP** (32 bitov)
- **DESTINATION IP** (32 bitov)
- **OPCIJE** (spremenljiva dolžina) - redko uporabljeno polje za testiranje ali varnostne protokole. Če so opcije prisotne, glava postane daljša od 20 bajtov. Zaradi dodatnega procesiranja jih večina usmerjevalnikov ne obravnava prednostno.
- **PODATKI**  (spremenljiva dolžina) - dejanska vsebina, ki se prenaša (npr. del spletne strani ali e-pošte). Običajno gre za TCP ali UDP segment. Dolžina tega polja je razlika med celotno dolžino paketa (Length) in dolžino glave (Header Length).

***

**Fragmentacija**

Paketi se enkapsulirajo v okvirje

- okvirji imajo omejeno dolžino - MTU oz. maximal transmission unit
- paket je treba razbiti na več delov - **fragmentacija**


Za fragmentacijo se v glavi nahajajo polja ID, FLAGS in OFFSET
- ID nam pove kateremu paketu pripada fragment
- OFFSET nam pove kje v paketu se nahaja
- FLAGS so trije biti od katerih sta zadnja dva DF - don't fragment in MF - more fragments bita

FLAGS so sestavljene iz 3 bitov.
- Prvi bit nima funkcije
- Drugi bit je **don't fragment** - pove ali se paket sme fragmentirati, če se ne sme in presega MTU potem se zavrže.
- Tretji bit je **more fragments** - pove kateri fragment je zadnji

FRAGMENT OFFSET je predstavljen z 8 biti in vsebuje lokacijo fragmenta v končnem paketu
- enota za odmik je 8 bajtov
- dolžina vsebine v fragmentu mora biti deljiva z 8 razen zadnji


V omrežju več tehnologij se lahko MTU sredi poti spremnija
- nek medij ima manjši MTU kot drugi
- v tem primeru mora usmerjevalnik storiti fragmentacijo
- torej se ta lahko dogaja kjerkoli na poti - fragment se lahko fragmentira še dlje
- **ponovno sestavljanje** fragmentov se zgodi samo na končnem sistemu.

**Napadi z uporabo fragmentacije**
Obstajajo različni napadi, ki izkoriščajo proces fragmentacije za onemogočanje delovanja omrežnih sistemov (DoS oz. Denial of Service napadi):

*   **Overlapping fragment attack** (napad s prekrivajočimi se fragmenti): Napadalec fragmentira pakete z namerno napačnimi odmiki ali dolžinami, tako da se ti med seboj prekrivajo. Pri poskusu sestavljanja se ciljni sistem lahko zmede in sesuje (zaradi napake v kodi TCP/IP sklada).
*   **Tiny fragment attack** (napad z majhnimi fragmenti): Napadalec podatke razkosa na tako majhne dele, da se fragmentirajo tudi podatki v glavi enkapsuliranega protokola (npr. TCP glava je razdeljena med dva fragmenta). Na ta način je onemogočeno varnostno filtriranje (npr. s požarnim zidom), saj npr. številka vrat (port) ni vsebovana v prvem fragmentu, ki ga filter pregleduje.


***

**IPv4 naslavljanje**

- vmesniki imajo IPv4 naslove dolge 32 bitov, razdeljene na oktete
- računalnik ima ponavadi en vmesnik, usmerjevalniki več
- obstaja okoli 4 miljarde IPv4 naslovov 
- naslovi morajo biti globalno unikatni

Naslove lahko organiziramo v podomrežje - vsi naslovi v podomrežju imajo enako predpono
- računalniki v istem podomrežju so medseboj dosegljivi brez posredovanja usmerjevalnika - so povezani na povezavni plasti
- več podomrežij lahko združimo v večje omrežje kar nam omogoča učinkovito usmerjevanje
- predpona je določena z **omrežno masko** oz. **subnet mask** - pove nam koliko bitov je za predpono oz. naslov podomrežja in koliko bitov za naslov naprav v tem podomrežju - dolžino predpone označimo z $/x$
- usmerjevalniki imajo na vsakem vmesniku drugo podomrežje

Včasih se je uporabljalo naslavljanje na osnovi razredov naslov kjer je veljalo

Razred A
- $/8$
- prvi bit omrežnega naslova je vedno $0$, ostalih 7 za določanje naslova omrežja
- ostalih 24 bitov za naprave v omrežju
- torej imamo $2^{7}$ možnih omrežij - $0.x.x.x$ do $127.x.x.x$

Razred B
- $/16$
- prva dva bita omrežnega naslova sta vedno $10$, ostalih 14 pa za naslov omrežja
- ostalih 16 je za naprave v omrežju
- torej je $2^{14}$ možnih omrežij - $128.x.x.x$ do $191.x.x.x$

Razred C
- $/24$
- prvi trije biti $110$, ostalih $21$ pa za naslov omrežja
- ostalih 8 je za naprave v omrežju
- torej je $2^{21}$ možnih omrežij - $192.x.x.x$ do $223.x.x.x$

***

Razreda A in B sta bila ponavadi prevelika po drugi strani pa je bil C premajhen.
Sistem je imel veliko potratnih naslovov če je neka firma imeal npr. B razred ampak so jih rabili le 500.

Kasneje se vpelje CIDR oz. Classless Inter-Domain Routing ki omogoča dodelitev poljubnega števila bitov v maski.

Poseben IP naslov je **broadcast** ki naslovi vse naprave na podomrežju. Sestavljen je iz samih enic v delu po omrežnem naslovu.

IP naslov s samimi ničlami po omrežnem naslovu pa naslavlja omrežje samo in ne posameznega vmesnika.

***

ICANN oz. Internet Corporation for Assigned Names and Numbers nudi naslovne prostore. Posameznemu ponudniku dodeli podomrežje z določenim naslovom. Te pa se lahko odločijo za nadaljne segmentiranje. 

Sedaj lahko poenostavimo posredovalne tabele usmerjevalnikov saj morajo preverjati le predpono ki pelje do omrežja ISP-ja ta pa ima nato usmerejevalnike ki pošiljajo te pakete naprej.

***

IPv4 naslov je zmanjkovalo. Uvedel se je sistem kjer so določeni naslovni prostori ki se smatrajo za zasebne. To so

- $10.0.0.0$ do $10.255.255.255$ z omr. masko $10.0.0.0/8$ in ponuja $2^{24}$ naslovov
- $172.16.0.0$ do $172.31.255.255$ z omr. masko $172.16.0.0/12$ in ponuja $2^{20}$ naslovov
- $192.168.0.0$ do $192.168.255.255$ z omr. masko $192.168.0.0/16$ in ponuja $2^{16}$ naslovov

Te naslovi so dogovorjeno neusmerljivi in so rezervirani za lokalno uporabo, paket ki vsebuje to kot ciljni naslov je zavržen pri ISP-ju.

Vse naprave v lokalnem omrežju sodijo v enega od teh družin. Edina naprava ki ima javni naslov dejanskega omrežja je usmerjevalnik ki katerikoli promet namenjen temu omrežju preusmeri na pripadajoč vmesnik. 

Ob priklopu v neko omrežje naprava nima IP-ja.

Za dodeljevanje IP-ja se uporablja **DHCP** oz. Dynamic Host Configuration Protocol.

Deluje v 4 fazah **DORA**
- Discover - naprava pošlje broadcast za DHCP strežnik.
- Offer - DHCP strežnik iz nabora prostih naslovov izbere enega in pošlje ponudbo napravi
- Request - Naprava lahko sprejme ali zavrne ponudbo - pošlje response za rezervacijo ali zavrnitev - ponavadi broadcast da če je več DHCP strežnikov lahko vejo da je bil IP že dodeljen.
- Acknowledge - Strežnik dokončno potrdi dodelitev
  



**DHCP DISCOVER**
*   Računalnik nima IP-ja, zato broadcasta v omrežje in išče poljuben DHCP strežnik.
*   **Source:** 0.0.0.0 (ker še nima svojega naslova)
*   **Destination:** 255.255.255.255 (broadcast – vsi v omrežju)
*   **Transaction ID:** 654 (oznaka poizvedbe)

**DHCP OFFER**
*   Strežnik (223.1.2.5) odgovori in ponudi prost IP naslov.
*   **Ponujeni IP (yiaddr):** 223.1.2.4
*   **Lifetime:** 3600 sekund (veljavnost naslova je 1 ura)
*   **Transaction ID:** 654 (mora biti enak kot pri discoverju)

**DHCP REQUEST**
*   Računalnik sprejme ponudbo in strežniku uradno sporoči: "Hočem ta naslov".
*   **Source:** 0.0.0.0 (še vedno uradno nima potrjenega naslova)
*   **Destination:** 255.255.255.255 (pove vsem, da je izbral ta strežnik)
*   **Transaction ID:** 655 (nova številka za novo fazo)

**DHCP ACK**
*   Strežnik potrdi izbiro in dokončno "zaklepa" naslov za ta računalnik.
*   **Potrjen IP (yiaddr):** 223.1.2.4
*   **Transaction ID:** 655
*   **Status:** Po tem koraku računalnik dejansko nastavi svoj IP na 223.1.2.4.

***

**NAT**

Za dejansko uoprabo prej omenjenih privatnih naslovov v lokalnih omrežju se mora javni naslov omrežja nekako preslikati v pravilni naslov naprave v podomrežju.

Za to se uoprablja **NAT** oz. Network Address Protocol
- Najprej naprava znotraj omrežja pošlje zahtevek ven iz omrežja.
- V routerju se v NAT tabeli zapiše izvorni naslov ter izvorni port naprave in izbere nek svoj prost port in v tabelo doda zraven še izbrani port in ciljni ip. Preden pošlje paket še spremeni naslov izvora v javni naslov omrežja kot tudi port.
- S tema podatkoma v tabeli lahko potem ko pride odgovor router posreduje odgovor do pravilne naprave.

**NAT pripomore k varnosti in omogoča uporabo samo enega javnega naslova za dostop do interneta celege omrežja.**

**Dela pa sicer z vrati ki so del 4. plasti in so namenjena naslavljanju procesov. Hkrati krši princip end to end komunikacije saj se routter vmešava v pakete in ne komunicirata več direktno.**


***

**ICMP**

Ker IP nima mehanizma za obveščanje o napakah za to poskrbi **ICMP protokol** oz. Internet Control Message Protocol. 

Sodi v omrežno plast ker ne dela s porti oz. ne komunicira strogo le od procesa do procesa, le z napravami, čeprav so njegovi podatki vedno enakspulirani v IP paket in sicer v paylodu - torej kot segment. 

ICMP paket se vtakne v payload navadnega IP paketa. V IP glavi v polju za protokol pa napiše $1$ in s tem sporoči da so podatki znotraj ICMP.

ICMP je namenjen routerjem na poti ki ob zavrženju paketa ustvarijo ICMP sporočilo in ga pošljejo nazaj. Zato mu rečemo tudi pomožni protokol. 

Uporablja se za sporočanje napak in sporočil ko router ne ve kaj naj s paketom. ICMP uporablja različne tipe in kode kot kategorija in subkategorija da pove kaj se dogaja.

Ključni tipi in kode so
- Type $8$: Echo request - ping
- Type $0$: Echo reply - pong
- Type $3$: Destination unreachable
	  - Code $0$: network unreachable
	  - Code $1$: Host unreachable
	  - Code $3$: Port unreachable
- Type $11$: Time Exceeded
	- Code $0$: TTL expired
	- Code $1$: Fragment reassembly time exceeded


**Traceroute** je aplikacija ki izkorišča ICMP da izpiše pot oz. naslove usmerjevalnikov po katerih potuje paket.
Vsak paket ima TTL večji za 1 torej dobimo ICMP odgovor od vsakega routerja po katerem naj bi se paket prenašal.


***

**IPv6**

IPv6 izboljša veliko delov IPv4. Ima več naslovov, omogoča hitrejše usmerjanje in zagotavlja kakovost storitev.

IPv6 naslovi so sestavljeni iz 16 skupin po 8 bitov skupaj 128 bitov za $2^{128}$ možnih naslovov. Najdaljši niz ničel se zapiše z dvema dvopičjema in prefiksne ničle lahko izpustimo.

IPv4 naslovi se v IPv6 pretvorijo z dodajanjem ničel predenj.

Pri IPv6 se fragmentacija ne dogaja več ampak za to poskrbijo višji sloji. Če je paket prevelik se preposto zavrže. *Za obveščanje poskrbi nova verzija ICMP - ICMPv6*.

Glava ne vsebuje več kontrolne vsote ker je ponavadi že prisotna v enkapusliranih podatkih.

Polja za opcije ni več - te se lahko implementirajo kot posebevn enkapsuliran protokol.

IPv6 paket sestavlja:
- VER (4 biti) : enako kot pri IPv4 - določa verzijo IP
- PRI oz. TRAFFIC CLASS (8 bitov) : Podobno kot TYPE OF SERVICE pri IPv4 in oznaka prioritete - spet najbolj uoprabno v lokalnih omrežjih, routerji na poti lahko tudi spreminjajo prioriteto
- FLOW LABEL (20 bitov) : oznaka za ohranjanje iste poti pri pošiljanju več paketov - torej če gledamo video in hočemo vse pakete poslati po isti poti da znižamo jitter potem vsem paketom damo isti flow label da router ve kam ga pošiljati in sploh ne gleda na destinatino ip address
- PAYLOAD LENGTH (16 bitov)
- NEXT HDR (8 bitov) : tip enkapsuliranega protokola
- HOP LIMIT (8 bitov) : TTL
- SOURCE (128 bitov)
- DESTINATION (128 bitov)
- DATA 



***

TODO

***

Porazdeljeno usmerjanje je princip kjer se  usmerjevalne tabele prilagodijo na spremembe cen povezav

Poznamo dva principa in sicer **"good news travel fast"** in **"bad news travel slow"**.

Prvi temelji na tem da ob dodajanju povezave se podatek o znižanju cene povezav hitro razširi in posredovalne tabele se hitro ustrezno prilagodijo.

...

Drugi temelji na tem da ko se povezava prekine vse kar ve router zraven je da nima direktne povezave



Ponavadi ceno omejimo z zgornjo mejo da propagacija višanja cen ne gre v neskončnost. RIP ima npr. ceno 16 kot maksimalno.


**Hierarhično umserjanje**

Če bi imeli vse usmerjevalnike v istem omrežju bi imeli težave. Imeli bi velike usmerjevalen tabele in vse naprave bi morale biti konfigurirane enako.

Skupine usmerjevalnkov organiziramo v avonomne sisteme ki so pod neodvisnimi administracijami

Usmerjevalniki v istem AS uporablja isti usmerjevalni protokol - **INTRA-AS** usmerjevalni algoritem npr. distance-vector ali link-state, ralični AS pa lahko različne.

Za povezovanje AS med seboj se uoprablja **INTER-AS** usmerjevalni protokol ki pa mora biti v celotnem omrežju enak. Za to poskrbi **BGP** oz. **Border Gateway Protocol**.

**INTRA-AS** usmerjanje:
- RIP - Routing information protocol
	- Usmerjanje z vektorjem razdalj - algoritem optimizira število hoppov - vsaka cena povezave je 1; največja dovoljena cena je 15
- OSPF - Open Shortest Path First
	- usmerjanje glede na **stanje povezav**
	- obvestila se z razpošiljanjem posredujejo celotnemu sistemu ki preračunanajkrajpe poti
	- da se konfigurirate varnsot, usmerjanje po več poteh za razbremenjevanje psoameznih povezav,...
- IGRP - Interior Gateway Routing Protocol
	- CISCO izboljša protokol RIP - usmerjanje z vektorjem razdalj
	- cene se izračuna kot utežena vsota pasovne širine, zakasnitve, obremenitve, MTU, in zanesljivosti
