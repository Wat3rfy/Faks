
Naloge transportne plasti: 
- **povezovanje procesov** - process to proccess
- **multipleksiranje/demultipleksiranje komunikacije** med procesi -  več procesov komunicira iz iste naprave - uporabljajo isti ip ampak moramo razločevati - dodelijo se jim porti
- **zagotavlja zanesljivost** prenosa podatkov
- **nadzoruje pretok in zasičenje** podatkov - lahko sporoči zahtevo za zmanjšanje hitrosti pošiljanja da se izognemu nasičenju omrežja ali pa preobremenitvi prejemnika.

**Socket** je kombinacija ip-ja in vrat.

Ko odpremo socket - **procesu dodelimo port** na katerem bo prejemal informacije.

Pošiljatelj sporočilo razbije v **segmente** in jih posreduje v **enkapsulacijo** omrežni plasti.

Prejemnik **dekapsulira** segmente iz paketov, **sestavljene segmente združi v sporočila** in jih **posreduje aplikacijski plasti.**

Za to sta najbolj pomembna protokola **TCP in UDP**.

Storitve ki jih transportna plast ponuja so:
- **omejene s storitvami nižje plasti** - ne more zagotoviti večje zanesljivosti kot jo omogoča omrežna plast. *Lahko le poskusi popraviti napake omrežne plasti. Transportna je torej odvisna od tega kako zanesljivo deluje omrežna plast.*
- vsak transportni protokol lahko zagotavlja svojo množico storitev
	- TCP ponuja npr. **zanesljivost**, **povezavno storitev** - vzpostava logične povezave oz. dogovor o komunikaciji, ima nadzor zamašitev
	- UDP je best-effort - nezanesljiv, nepovezavna storitev
- v internetu nimamo zagotavljanja časa dostave ali zagotavljanaja pasovne širine.

**Vtič** oz. socket je združitev ip naslova in porta s čimer naslavljamo procese. Je vmesnik med aplikacijsko in transportno plastjo. Preko njega se pošiljajo in prejemajo sporočila, vsak proces pa ima svojega.

Vtiči od 0 do 1023 so tako imenovani *well-known* ports npr.:
- http: 80 (spletni strežnik)
- smtp: 25 (poštni strežnik)
- dns: 53 (imenski strežnik)
- telnet: 23 (oddaljen dostop)
- irc: 194 (pogovorni strežnik)

Port je 16 bitna številka ponavadi nad 1023. 

Vsak transportni segment ima **16-bitna podatka** za demultipleksiranje
- **source port**
- **destination port**

`| Izvorna vrata / 16b | Ciljna vrata / 16 b | druga polja glave / 16 b | podatki aplikacije / |`

**Napad portscan**

Napad portscan (pregled vrat) je namenjen pregledovanju strežnika, na katera vrata se bo odzival. S tem napadalec (ali administrator) dobi vpogled v procese, ki tečejo na strežniku. S poznavanjem šibkih točk strežniške programske opreme (npr. operacijski sistem, SQL server) lahko napadalec ogrozi delovanje sistema.

***

**UDP - User Datagram Protocol**

- po principu best effort - ne zagotavlja to da paket pride do konca - toleiramo izgubo
	- datagrami se lahko izgubijo
	- vrstni red je lahko napačen
- nepovezaven - nima rokovanja
- nima nadzora zamašitev

Ima prednosti
- zelo osnoven
- hiter učinkovit lahek minimalističen
- majhna glava segmenta 


`| src port | dst port | lengthOfSegment | checksum | poadtki`

Namenjen je torej uporabi v okoljih ko lahko toleriramo izgube
- multimedijske aplikacije - stream, voicecall, igrce
- in tiste kjer je pomebna hitrost : DNS, SNMP
- usmerjevalni protokoli

Zanesljivost mora biti implementirana višje v aplikacijski plasti.

**UDP kontrolna vsota**

- Internet Checksum
	- Pošiljatelj mora sešteti 16-bitne besede podatkov izvede eniški komplement in vrednost shrani kot kontrolno vsoto. 
	- Prejemnik mora sešteti 16 bitne besede podatkov skupaj s kontrolno vsoto in mora dobiti same enice

```
 1110011001100110
 1101010101010101
---------------------   sešteje
11011101110111011
---------------------
 1011101110111011
                1
----------------------  prišteje predolgo enko
 1011101110111100       -> to je vsota   
----------------------  eniški komplement
 0100010001000011       -> kontrolno vsota                
```

- ne zanaša se na ostale plasti zato implementira svoje preverjanje podatkov
- implementirano je ker do napak lahko pride tudi pri hranjenju segmenta v spominu usmerjevalnika in ne nujno pri prenosu kar omrežna plast ne bi preverjala
- UDP kontrolna vsota je namenjena preverjanju pravilnosti med izvornim in ciljnim procesom, ne pa pri potovanju po posameznih povezavah (t. i. princip končnih sistemov, end-to-end argument/principle) - to je še najboljša opcija saj preverjanje na poti ni tako pomembno.
***

**TCP - Transfer Control Protocol**

TCP služi kot protokol ki zagotavlja zanesljivo dostavo z uporabo nezanesljivega kanala.

Sestavljen je iz
- osnovne funkcionalnosti pošiljanja in prejemanja
- reševanje napak - ACK, NAK
- obravnava izgubljenih paketov

**Enostavni protokol**

Pošiljatelj v svojem edinem stanju čaka na aplikacijsko zahtevo. 

Ko ta pride, pošiljatelj enkapsulira aplikacijske podatke v datagrame transportne plasti in jih pošlje po nezanesljivem kanalu. 

Po drugi strani je privzeto stanje prejemnika čakanje na dostavo datagrama. 

Kadar ga prejemnik sprejme, iz njega dekapsulira aplikacijske podatke in jih dostavi aplikaciji.

![[Pasted image 20260404155936.png]]












**Potrjevanje**

Potrjevanje zasnujmo tako, da prejemnika zadolžimo, naj ob prejemu vsakega paketa najprej preveri njegovo pravilnost, nato pa naj pravilno sprejete potrdi s potrditvijo ACK (angl. ACKnowledgment), o nepravilno sprejetih pa naj pošiljatelja obvesti z negativno potrditvijo NAK (angl. Negative AcKnowledgment). 

Kadar pošiljatelj prejme prejemnikov NAK, naj ta isti paket pošlje ponovno, v upanju, da bo v drugem poskusu sprejet pravilno.


![[Pasted image 20260404155947.png]]













Iz delovanja pošiljatelja lahko vidimo, da dokler ne prejme pozitivne potrditve tekočega paketa, ne more sprejeti nove aplikacijske zahteve po transportu in  pošiljati naslednjega paketa. Takšnemu načinu potrjevanja paketov pravimo  tudi **sprotno potrjevanje**, protokolu pa, da deluje po principu **ustavi in čakaj**  (angl. stop&wait). To omejitev moramo odpraviti.


**Obvladovanje izgube segemtnov**


Poleg okvare paketov se pri prenosu lahko pripeti tudi njihova **izguba**. 

Razlogi za izgube so lahko številni: 
 - napačen sprejem v napravah na poti, 
 - okvara pomnilnika, 
 - napake pri konfiguraciji usmerjanja, 
 - prekinitev povezav in drugi. 
   
Tudi v primeru izgube paketa moramo poskrbeti, da jo bo pošiljatelj lahko zaznal in ponovil pošiljanje.

Nadgradimo dosedanji protokol tako, da pošiljatelja opremimo z mehanizmom **časovne kontrole** pošiljanja paketov. 

S časovno kontrolo **merimo časovni interval določene dolžine** in če se le-ta **izteče**, pošiljatelj pa v tem času **ne prejme potrditve prejemnika**, lahko pošiljatelj sklepa, da se je poslani paket **izgubil** in da ga prejemnik **ni prejel**. 

![[Pasted image 20260404160452.png]]





















Prvi scenarij prikazuje uspešno pošiljanje paketov in prejemanje potrditev, ki jih pošiljatelj prejme pred potekom časovne kontrole. 

Drugi scenarij opisuje prej opisani primer, ko se poslani paket izgubi. S slike vidimo, da po preteku časovnega intervala pošiljatelj ponovi pošiljanje paketa, zanj pa tokrat uspešno prejme potrditev. Sekvenca pošiljanj in potrjevanj se zato lahko nadaljuje. 

Tretji scenarij prikazuje, da se potek časovnega intervala lahko zgodi tudi v primeru, ko se izgubi potrditev (tudi izguba potrditve je možen dogodek, saj je pri protokolu TCP potrditev ravno tako segment protokola TCP). Ker zaradi poteka časovne kontrole pošiljatelj ponovi pošiljanje paketa, prejemnik prejme podvojeni paket. To težavo bomo pri nadaljnji konstrukciji protokola odpravili z uvedbo številčenja paketov, na podlagi katerega bo prejemnik lahko pakete s ponovljenimi številkami zavrgel. 

Četrti scenarij prikazuje pomen nastavitve pravilne dolžine časovnega intervala. Če je ta prekratek, kot prikazuje slika, lahko pošiljatelj "neučakano" sklepa, da se je paket izgubil, in ponovi pošiljanje paketa, čeprav bo potrditev za prvo pošiljanje še prejel. Tudi v tem scenariju prejemnik posledično prejme isti paket dvakrat, dodatno pa tudi pošiljatelj prejme dvojno potrditev za isti paket (kar pa ne predstavlja težave). 

Omenimo lahko še scenarij (ki ni ilustriran), ko je nastavljen časovni interval predolg. V tem primeru komunikacija poteka enako kot v drugem scenariju, le s to razliko, da pošiljatelj dlje časa čaka na potek intervala in je s tem komunikacijski kanal slabše izkoriščen.

![[Pasted image 20260404160741.png]]






















Prikazan je končni avtomat protokola, ki zna reševati tudi težave z izgubljenimi paketi in potrditvami. Za potrebe zaznavanja podvojenih paketov uvedemo številčenje paketov z izmenjujočima zaporednima številkama 0 in 1. Dve številki paketov v našem primeru popolnoma zadoščata, saj še vedno uporabljamo sprotno potrjevanje oziroma protokol, ki deluje po principu ustavi in čakaj. Ob normalnem (brezizgubnem) pošiljanju lahko torej prejemnik pričakuje, da bo dobival pakete, oštevilčene v zaporedju 0, 1, 0, 1 itd. V primeru, da se zgodi tretji (izguba potrditve) ali četrti scenarij (prekratek časovni interval), bo prejemnik podvojen paket zaznal z dvakratnim prejemom iste številke (prejel bo npr. zaporedje 0, 1, 1, ...) ter bo lahko duplikat zavrgel.

Vidimo lahko, da je končni avtomat pošiljatelja simetričen po diagonali, razlikuje se le v številki paketa. Pošiljatelj v začetnem stanju čaka na aplikacijsko zahtevo. Kadar ta pride, oštevilči prvi paket s številko 0, izračuna kontrolo vsoto in pošlje enkapsulirane podatke. V fazi čakanja na potrditev ponovno pošlje isti paket, če od prejemnika prejme NAK, okvarjeno potrditev ali če poteče časovni interval. V primeru, da uspešno prejme ACK, preide v fazo čakanja na naslednje podatke za pošiljanje, ki jih bo oštevilčil s številko 1 ter simetrično nadaljeval po diagramu.

Prejemnikov diagram je ravno tako simetričen. V prvem od obeh stanj prejemnik čaka na paket, ki ima številko 0, v drugem pa na paket, ki ima številko 1. Vsakič, kadar prejemnik prejme neokvarjen paket z ustrezno številko, dekapsulira podatke, jih dostavi aplikaciji in vrne pošiljatelju ustrezno potrditev. V primeru, da v vsakem čakajočem stanju prejemnik prejme okvarjen paket, odgovori z NAK. V primeru, da v čakajočem stanju prejemnik prejme paket, ki ima drugačno številko od pričakovane, lahko sklepa, da je to ponovljen prejšnji paket – tega sicer potrdi, a vsebino zavrže. Na to, da gre resnično za prejšnji paket, lahko prejemnik sklepa zato, ker uporabljamo **sprotno potrjevanje**. Le v tem primeru se nam namreč ne more zgoditi, da z zakasnitvijo prejmemo paket, ki je starejši od prejšnjega. Uporabi ACK in NAK pravimo tudi **neposredno potrejvanje**.


S številčenjem paketov tudi dodatno poenostavimo protokol, saj lahko ta vsebuje eno obliko protokolarnega sporočila manj (negativne potrditve niso več potrebne). Prejemnik izvaja **posredno potrjevanje** tako, da za vsak (pravilno ali nepravilno) prejeti paket odgovori z ACK, ki vključuje številko paketa, ki je bil nazadnje uspešno sprejet. V primeru uspešnega sprejema bo torej prejemnik odgovoril z ACK+<številka trenutnega paketa>, v primeru neuspešnega sprejema pa z ACK+<številka prejšnjega paketa>. Če bo prejemnik torej dvakrat prejel potrditev za isti (prejšnji) paket, bo lahko sklepal, da tekoči paket ni bil sprejet pravilno, kar je enakovredno negativni potrditvi.

***
**Tekoče pošiljanje**




Protokol, ki smo ga razvili do sedaj, še vedno uporablja sprotno potrjevanje, kar pomeni, da mora čakati na potrditev trenutnega paketa, preden lahko pošlje naslednjega. 

Tak način pošiljanja bi lahko izboljšali, če bi naredili tak protokol, ki lahko pošlje več paketov hkrati in vodi evidenco, za katere od poslanih paketov je že prejel potrditve. 

V primeru manjkajočih potrditev bi ta protokol lahko nato poslal ponovno tiste pakete, ki še niso bili potrjeni. Takšen način potrjevanja imenujemo **tekoče pošiljanje** ali **pošiljanje z drsečim oknom**.

Omogoča nam boljšo izkoriščenost komunikacijskega medija, saj lahko pošiljatelj pošlje naslednji paket hitreje od povratnega časa prenosa med pošiljateljem in prejemnikom.

Poznamo dva različna protokola za tekoče pošiljanje, a ima **tekoče pošiljanje nekaj skupnih lastnosti**, kot posledica hkratnega pošiljanja več paketov in se odražajo na pošiljatelju in prejemniku:

**Pošiljatelj** mora voditi evidenco paketov, v kateri mora razlikovati med
- **paketi, ki so šele prišli na vrsto za pošiljanje** (**čakajoči paketi**)
- **paketi, ki so bili poslani in čakajo na potrditve** (**nepotrjeni paketi**) 
- **paketi, ki so bili poslani ter potrjeni (potrjeni paketi)**. 


Poleg paketov pošiljatelj vodi tudi evidenco o velikosti preostalega (prostega) **pomnilnika**, ki ga je namenil hranjenju paketov in ki je običajno v obliki čakalne vrste. Vrsta je za ta namen primerna struktura, saj deluje po principu FIFO (angl. *first-in-first-out*), kar sovpada s tem, da želimo prej poslati tiste pakete, ki so posledica bolj zgodnjih aplikacijskih zahtev. Kadar je najstarejši paket potrjen, se lahko ta iz vrste odstrani, s tem pa se ustvari prostor za novi čakajoči paket.


Zaradi omejitev pomnilnika in znižanja kompleksnosti protokola je smiselno, da pošiljatelj omeji največje število paketov, ki so v danem trenutku nepotrjeni. Vsakič, kadar prejemnik potrdi nek paket, lahko torej pošiljatelj pošlje enega novega. Ta način delovanja opisujemo s pojmom **drsečega okna**, ki si ga lahko predstavljamo kot čakalno vrsto, iz katere izstopajo potrjeni paketi, vanjo pa vstopajo poslani, a nepotrjeni paketi. Največje število nepotrjenih paketov, ki so v obtoku, je torej enako parametru, ki ga imenujemo **velikost okna**.

Ker imamo lahko v obtoku večje število paketov, je potrebno, da povečamo **razpon števil**, ki smo jih uporabljali za številčenje paketov (številki 0 in 1 ne bosta več zadoščali). Le na ta način lahko zagotovimo, da se lahko pošiljatelj in prejemnik nedvoumno sporazumeta, katere številke paketov potrjuje prejemnik.

Ker je v obtoku lahko večje število paketov, lahko pošiljatelj uporablja tudi več **časovnih kontrol**, za vsak paket največ eno.

Za lažje potrjevanje bosta pošiljatelj in prejemnik uporabljala posebno obliko posrednega potrjevanja, ki ga imenujemo **kumulativno potrjevanje**. Pri tej obliki potrjevanja bo veljalo, da potrditev oblike ACK+<številka paketa n> uspešno potrjuje prejem vseh preteklih paketov do vključno n-tega. Na primer, če je pošiljatelj poslal pakete s številkami P35, P36, P37, P38 in P39, prejemnik pa odgovori samo z ACK38, šteje, da je potrdil prve štiri pakete, zadnjega pa (še) ne.

Ker vemo, da lahko paketi potujejo po različnih poteh, jih bo prejemnik lahko sprejel v **nepravilnem vrstnem redu**. Zato je tudi za prejemnika pomembno, da ima na sprejemni strani namenski pomnilnik, v katerem bo hranil pakete toliko časa, dokler ne pridejo morebitni manjkajoči paketi. Ti paketi so potrebni za to, da prejemnik lahko vse pakete uredi v pravilni vrstni red in uspešno dekapsulira celotno sporočilo.

V nadaljevanju bomo opisali dve obliki protokolov za tekoče pošiljanje, ki uporabljata različne implementacije zgoraj naštetih lastnosti.

**Ponavljanje zadnjih**

Pri **ponavljanju zadnjih** (angl. go-back-N) hrani pošiljatelj okno z največjim številom nepotrjenih paketov, prejemnik pa ne izvaja urejanja paketov, saj protokol zagotavlja sprejem v pravilnem vrstnem redu. Pošiljatelj hrani samo eno časovno kontrolo, ki jo proži za najstarejši paket v oknu. Kadar ta časovna kontrola poteče, pošlje pošiljatelj vse pakete iz okna prejemniku ponovno. Če prejemnik prejme paket, ki ni v pravilnem vrstnem redu, je to znak, da se je vsaj en vmesni paket izgubil. Vsak sprejeti paket, ki ni v pravilnem vrstnem redu, lahko prejemnik zavrže, saj iz zgornjega opisa protokola vemo, da ga bo pošiljatelj ponovno poslal kasneje – v oknu vseh nepotrjenih paketov, v katerem so tudi manjkajoči nepotrjeni paketi.

![[Pasted image 20260404172814.png]]










Slika prikazuje pošiljatelja, ki uporablja velikost okna 4. Pošiljatelj na začetku pošlje štiri pakete (P1, P2, P3 in P4), od katerih prejemnik odgovori s potrditvami ACK1, ACK2, ACK2 (in ne ACK3!), saj se paket P3 izgubi, P2 pa je bil zadnji še pravilno sprejeti paket. Ker je prejemnik prejel paket P4 v nepričakovanem vrstnem redu (P3 manjka), ga zavrže. V nadaljevanju opazimo, da ko pošiljatelj prejme potrditev ACK1, premakne okno naprej in pošlje naslednji paket v vrsti – P5. Enako se zgodi tudi ob prejeti potrditvi ACK2, ki omogoči pošiljanje paketa P6. V pošiljateljevem oknu so sedaj paketi P3, P4, P5 in P6, časovna kontrola pa meri čas pošiljanja za P3, ki je najstarejši paket v oknu. Prejemnik zavrže tudi P5 in P6, saj tudi ta dva nista v pravilnem vrstnem redu (še vedno manjka P3). Ko poteče časovna kontrola, pošlje pošiljatelj celotno okno paketov ponovno (torej pakete P3, P4, P5 in P6). Prejemnik jih tokrat sprejme v pravilnem vrstnem redu in uspešno potrdi.

Vprašamo se lahko še, kaj bi se zgodilo v primeru izgubljene potrditve. Ker protokol uporablja kumulativno potrjevanje, predstavlja vsaka potrditev paketa z višjo številko hkrati tudi potrditev paketov, za katere se je potrditev izgubila. Protokol je zato odporen proti takšnim scenarijem.

**Ponavljanje izbranih**

Tukaj je prepisano besedilo:

**Ponavljanje izbranih**

Pri ponavljanju izbranih (angl. *selective repeat*) uporablja pošiljatelj okno poslanih paketov, prejemnik pa okno sprejetih paketov. Slednjega mora prejemnik uporabljati zato, ker protokol dopušča sprejem paketov v nepravilnem vrstnem redu. Zato mora prejemnik hraniti pakete do prihoda manjkajočih, da jih lahko uredi in dostavi aplikaciji. Za prejemnikovo okno velja enako kot za pošiljateljevo: šele kadar je uspešno urejen in sprejet najstarejši paket, lahko prejemnik okno premakne naprej in sprejema nove pakete v čakanje za urejanje. Tak sistem mu omogoča smiselno porabo pomnilnika, ki je omejen.

Največja razlika od prejšnjega protokola za tekoče pošiljanje je pri ponavljanju izbranih ta, da hrani pošiljatelj časovno kontrolo za vsak posamezni poslani paket posebej (hrani torej toliko časovnih kontrol, kot je velikost okna). Pošiljatelj in prejemnik izvajata potrjevanje posameznih paketov (in ne torej kumulativnega potrjevanja), na podlagi česar lahko pošiljatelj ob poteku časovnih kontrol ponovi pošiljanje samo tistih paketov, za katere še ni prejel potrditve (in ne pošilja vseh paketov v oknu). V primeru, če pride do izgube potrditve, bo pošiljatelj isti paket poslal ponovno, ko poteče časovna kontrola zanj. Prejemnik bo moral zato na podlagi številk paket ugotavljati, ali je prejeti paket že prejel v preteklosti in če gre za duplikat, bo le-tega zavrgel.

![[Pasted image 20260404173636.png]]





Slika prikazuje pošiljatelja in prejemnika, ki uporabljata okno velikosti 4. Do prve zapolnitve okna pošlje pošiljatelj pakete P1, P2, P3, P4, od katerih se P3 izgubi. Ob pravilnem sprejemu prejemnik potrjuje vsak paket posebej in odgovori s potrditvami ACK1, ACK2 in ACK4. Ker je ob prejemu P4 prejemnik zaznal, da je manjkal paket P3, paketa P4 še ne preda višji plasti, ampak ga začasno shrani. Po prejemu ACK1 in ACK2 premakne pošiljatelj okno naprej in pošlje P5 in P6. Prejemnik tudi tadva potrdi z ACK5 in ACK6 in ju začasno shrani, saj še vedno ni sprejel P3. Ko poteče pošiljateljeva časovna kontrola za najstarejši paket v oknu (P3), pošlje pošiljatelj P3 ponovno. Prejemnik ga tokrat uspešno sprejme, uredi pakete P3, P4, P5 in P6 v pravilni vrstni red in jih dostavi višji plasti. Ob tem se prejemnikovo okno prestavi naprej: pripravljen je na sprejem paketov od P7 naprej.

Simulacija
https://www.tkn.tu-berlin.de/teaching/rn/animations/gbn_sr/

***

**Protokol TCP**

Te principe implementira **TCP protokol**. 

Protokol *Transmission Control Protocol* (TCP) te principe tudi implementira. 

Poleg odkrivanja napak, ponovnega pošiljanja, urejanja vrstnega reda in zaznavanja duplikatov skrbi TCP tudi za **nadzor pretoka** in **kontrolo zasičenja**. 

Je **povezavni protokol**, kar pomeni, da pred prenosom podatkov potrebuje **vzpostavitev povezave**, pri kateri se določijo potrebni parametri za izvedbo komunikacije. 

Na povezavi, ki poveže natanko enega pošiljatelja in sprejemnika, lahko teče dvosmerni promet v obliki oštevilčenega toka podatkov.

Segment TCP protokola vsebuje naslednja polja.

| POLJE | DOLŽINA | POMEN |
| :--- | :--- | :--- |
| ŠT. IZVORNIH VRAT | 16 bitov | Številka izvornih vrat, ki je običajno naključno določena z vrednostjo $\ge 1024$ in potrebna za odgovor pošiljateljevemu procesu. |
| ŠT. CILJNIH VRAT | 16 bitov | Številka, potrebna za naslavljanje procesa na prejemnikovi strani. Za določene (strežniške) aplikacije obstajajo ustaljene (standardizirane) številke vrat. |
| ZAPOREDNA ŠT. | 32 bitov | Številka, ki določa zaporedje segmentov, izraženo v številu prenesenih bajtov podatkov. |
| ŠT. POTRDITVE | 32 bitov | Številka potrditve, izražena v številki naslednjega pričakovanega bajta s strani prejemnika potrditve. |
| DOLŽINA GLAVE | 4 biti | Določa dolžino glave v 32-bitnih besedah. |
| REZERVIRANO POLJE | 3 biti | Hrani vrednost 0, namenjeno morebitnim razširitvam v prihodnosti. |
| KONTROLNI BITI | 9 bitov | <ul><li>NS, CWR, ECE: 3 kontrolni biti, ki se v eksperimentalni različici uporabljajo za kontrolo zasičenja z uporabo omrežnih storitev,</li><li>URG: zastavica, ki indicira veljavno vsebino v polju s kazalcem na nujno vsebino,</li><li>ACK: zastavica, ki indicira veljavno vsebino v polju s številko potrditve,</li><li>PSH: zahteva takojšnjo dostavo aplikaciji brez hranjenja v sprejemnem medpomnilniku,</li><li>RST: zahteva za resetiranje povezave,</li><li>SYN: zahteva po vzpostavitvi povezave in usklajevanju začetnih zaporednih številk,</li><li>FIN: zahteva po prekinitvi povezave.</li></ul> |
| SPREJEMNO OKNO | 16 bitov | Uporabno za nadzor pretoka: pošiljateljevo sporočilo o prostem sprejemnem medpomnilniku. |
| KONTROLNA VSOTA | 16 bitov | Kontrolna vsota, izračunana z algoritmom *Internet Checksum*, ki je izračunana nad podatki iz glave paketa IP (naslov pošiljatelja, naslov prejemnika, protokol, dolžina) in vsemi podatki iz UDP datagrama. |
| KAZALEC NA NUJNO VSEBINO | 16 bitov | Odmik glede na zaporedno številko, ki kaže na začetek podatkov, ki naj jih prejemnik preko vrste dostavi aplikaciji. V sodobnem TCP zelo slabo uporabno in implementirano. |
| OPCIJE | do 320 bitov | Možne razširitve glave segmenta, dolžina mora biti večkratnik 32 bitov. |
| APL. PODATKI | spremenljiva dolžina | Enkapsulirani podatki aplikacijske plasti. |

![[Pasted image 20260413095220.png]]


Ker je TCP povezaven protokol, pošiljatelj in prejemnik pred izmenjavo podatkov najprej vzpostavita povezavo. Povezava je po vzpostavitvi dvosmerna, kar pomeni, da se podatki lahko prenašajo v obe smeri. 

Da razlikujemo med vzpostaviteljem komunikacije od prejemnika, prvega imenujemo *pošiljatelj*, drugega pa *prejemnik*, kljub temu da gre za komunikacijsko enakovredna udeleženca.

Vzpostavitev povezave poteka s postopkom, imenovanim **trojno rokovanje** (angl. *three-way handshake*), v katerem udeleženca:
- naključno določita in izmenjata zaporedni številki, s katerima bosta pričela številčiti segmente (začetni številki na obeh straneh sta neodvisni in naključno določeni zaradi večje varnosti – onemogočanja preproste ponovitve komunikacije in vrivanja paketov),
- izmenjata začetne velikosti medpomnilnikov, kar je potrebno za izvajanje nadzora pretoka.

Trojno rokovanje se izvede v naslednjih treh korakih :
1. Pošiljatelj pošlje prejemniku segment z zastavico SYN. Ta segment še ne vsebuje podatkov, v polju *zaporedna številka* (na skici označeno s *seq*) pa vsebuje začetno številko zaporedja segmentov, ki je določena naključno.
2. Prejemnik odgovori s segmentom, ki ima veljavni zastavici SYN in ACK. S tem segmentom obvesti pošiljatelja o svoji začetni številki segmenta (v polju *zaporedna številka* oziroma *seq*) in z zastavico ACK in poljem *številka potrditve* (na skici zapisano kot *ack*) potrdi sprejem prejšnjega segmenta. Prejemnik ravno tako obvesti pošiljatelja o svoji velikosti razpoložljivega sprejemnega medpomnilnika (na skici označeno z *rwnd*).
3. Pošiljatelj izvede še tretji korak – prejemniku pošlje segment z zastavico ACK, s katerim potrdi sprejem podatkov iz koraka 2. Pošiljatelj istočasno prejemnika obvesti tudi o trenutni velikosti svojega razpoložljivega medpomnilnika za sprejete segmente. V tem koraku lahko pošiljatelj v segmentu skupaj s potrditvijo ACK že pošilja tudi podatke (skupno pošiljanje potrditve in hkrati novih podatkov imenujemo **pošiljanje na štuporamo** (angl. **piggy-backing**)).

![[Pasted image 20260413100031.png]]


Pošiljatelj in prejemnik pri številčenju segmentov ne uporabljata številčenja z zaporednimi števili. Uporabljata drugačno definicijo vrednosti v poljih *zaporedna številka* in *številka potrditve*:
- V polje **zaporedna številka** pošiljatelj vedno shrani prvo zaporedno številko bajta, ki tvori sporočilo. Na primer, če pošiljatelj v nekem segmentu, ki ima zaporedno številko 81, pošlje 8 bajtov podatkov (torej pošlje bajte s številkami 81-88), bo njegov naslednji segment imel zaporedno številko 89.
- V polje **številka potrditve** udeleženec v komunikaciji vedno zapiše naslednji zaporedno številko bajta, ki ga pričakuje od nasprotnega udeleženca.


Na primer, če je pošiljatelj v nekem segmentu z zaporedno številko 81 poslal 8 bajtov podatkov (torej bajte s številkami 81-88), bo odjemalec odgovoril s številko potrditve 89, kar je številka naslednjega pričakovanega segmenta s strani pošiljatelja.

Kadar eden od udeležencev v komunikaciji zaključi s prenosom podatkov, lahko sproži rušenje povezave. Rušenje se izvede v naslednjih štirih korakih:
1. Pošiljatelj pošlje strežniku segment z zastavico FIN.
2. Prejemnik odgovori na prejeti segment s potrditvijo (ACK).
3. Kadar tudi prejemnik zaključi s prenosom podatkov proti pošiljatelju, pošlje tudi prejemnik pošiljatelju segment z zastavico FIN.
4. Pošiljatelj prejemniku odgovori s potrditvijo (ACK) na prejeti zaključni segment. Po pošiljanju pošiljatelj uporabi čakanje s časovnim intervalom, v primeru, če se njegova poslana potrditev izgubi in prejemnik ponovi pošiljanje segmenta FIN. Po preteku časovnega intervala je povezava dokončno zaprta.


**Stanja protokola TCP**

Vidimo, da se lahko pošiljatelj in odjemalec pri protokolu TCP nahajata v enem izmed več možnih stanj protokola. Sodobni operacijski sistemi nam omogočajo vpogled v seznam trenutnih povezav TCP in v njihovo stanje, ki je lahko eno izmed naslednjih:

* **LISTEN:** stanje prejemnika, v katerem čaka na dohodne zahteve po vzpostavitvi povezav,
* **SYN_SENT:** stanje pošiljatelja, v katerega preide po prvem koraku trojnega rokovanja (SYN),
* **SYN_RCVD:** stanje prejemnika, v katerega preide po izvedenem drugem koraku trojnega rokovanja (SYN ACK),
* **ESTABLISHED:** stanje pošiljatelja, v katerega preide po izvedenem tretjem koraku trojnega rokovanja (ACK) in stanje prejemnika, v katerega le-ta preide ob prejemu istega ACK; v tem stanju je povezava uspešno vzpostavljena in udeleženca lahko izmenjujeta segmente,
* **FIN_WAIT_1:** stanje, v katerega preide pošiljatelj ob izvedenem prvem koraku rušenja povezave (FIN),
* **CLOSE_WAIT:** stanje, v katerega preide prejemnik po sprejemu segmenta FIN in odgovoru z ACK,
* **FIN_WAIT_2:** stanje, v katerega preide pošiljatelj ob sprejemu ACK prejemnika in čakanju na njegov FIN,
* **LAST_ACK:** stanje, v katerega preide prejemnik ob izvedbi tretjega koraka rušenja povezave (pošiljanje FIN),
* **TIME_WAIT:** stanje, v katerega preide pošiljatelj ob prejemu prejemnikovega FIN in odgovorom z ACK; v tem stanju pošiljatelj izvaja čakanje za morebitno prestrezanje zamujenih zaključnih segmentov³,
* **CLOSED:** stanje, v katerega preideta pošiljatelj in prejemnik po uspešnem rušenju povezave.


**SYN flood** je napad, v katerem napadalec pošlje strežniku veliko število paketov za vzpostavitev povezave (SYN), pri čemer strežnik na zahtevo odgovori s segmentom SYN ACK in za vsako zahtevo rezervira del svojega medpomnilnika. Ker napadalec načrto ne zaključi tretjega koraka trojnega rokovanja (ACK), se zasedenost strežnikovega pomnilnika zaradi delno odprtih povezav povečuje. V skrajni sili lahko pride do prenehanja delovanja strežnika oz. onemogočanja njegovega delovanja (angl. *denial of service, DoS*). Napad, ki ga lahko izvede tudi več napadalcev hkrati (porazdeljeni napad DoS), je potrebno preprečevati z zagotavljanjem dovolj velikega možnega števila povezav, časovno kontrolo hranjenja napol odprtih povezav ali pa s sistemom za opazovanje paketov v omrežju.

Za zagotavljanje zanesljive dostave segmenta se uporablja časovna kontrola, znotraj katere pošiljatelj pričakuje potrditev s strani prejemnika. 

Pri nastavljanju dolžine časovne kontrole se pošiljatelj opira na meritve povratnega časa komunikacije (angl. *round-trip time, RTT*) do prejemnika. To je čas, ki je potreben za to, da pošiljatelj pošlje prejemniku okvir, prejemnik pa da nanj odgovori. Intuitivno se lahko zavedamo, da dolžina časovne kontrole ne sme biti manjša od tega najkrajšega časa komunikacije, saj bo pošiljatelj v tem primeru “neučakano” oz. prezgodaj prožil ponovno pošiljanje segmentov. Ravno tako pa nastavitev časovne kontrole ne sme biti veliko daljša od časa RTT, saj v primeru izgubljenih paketov to predstavlja predolgo čakanje, ki vodi v slabo izkoriščenost komunikacijskega kanala.

Ker se dolžina RTT lahko zaradi različnih poti, obremenjenosti usmerjevalnikov in zasičenosti omrežja skozi čas spreminja, mora tudi pošiljatelj biti sposoben dolžino časovnega kontrole dinamično prilagajati razmeram. 

Za izračun primerne časovne kontrole zato pošiljatelj avtomatsko opravlja meritve RTT skozi čas. Na podlagi izmerjenih RTT (količina $\text{IzmerjeniRTT}$) gladi skoke v meritvah z izračunom gibajočega povprečja skozi čas (količina $\text{OcenjeniRTT}$), pri katerem s faktorjem $\alpha$ uteži novo vrednost izmerjenega RTT, s faktorjem $1 - \alpha$ pa uteži vrednost gibajočega povprečja v prejšnji časovni enoti. Vrednost gibajočega povprečja v novi časovni enoti izračuna kot linearno kombinacijo obeh količin, pri čemer običajno uporabi $\alpha = 0,125$:

$$\text{OcenjeniRTT}[i] \leftarrow (1 - \alpha) \cdot \text{OcenjeniRTT}[i - 1] + \alpha \cdot \text{IzmerjeniRTT}[i]$$

Nadalje pošiljatelj izračuna tudi gibajočo deviacijo, ki je količina, ki opisuje zglajena odstopanja od gibajočega povprečja. Tudi njo izrazi kot linearno kombinacijo vrednosti deviacije v prejšnji časovni enoti, utežene z $\beta$, in vrednosti absolutne razlike med izmerjenim RTT in gibajočim povprečjem, utežene z $1 - \beta$ (privzeta vrednost za $\beta$ znaša $0,25$):

$$\text{DevRTT}[i] \leftarrow (1 - \beta) \cdot \text{DevRTT}[i - 1] + \beta \cdot |\text{IzmerjeniRTT}[i] - \text{OcenjeniRTT}[i]|$$

Izračunano gibajočo deviacijo, ki opisuje velikost odstopanj od povprečja, lahko pošiljatelj uporabi kot “rezervo”, ki jo mora prišteti gibajočemu povprečju, da skupna vsota zagotovo ne predstavlja prekratkih časovnih kontrol. Implementacije protokola TCP običajno uporabljajo štirikratnik gibajoče deviacije kot privzeto “rezervo” in dolžino časovne kontrole izrazijo kot:

$$\text{CasovnaKontrola}[i] = \text{OcenjeniRTT}[i] + 4 * \text{DevRTT}[i]$$


Primer računanja časovne kontrole na podlagi izmerjenih RTT-jev.

![[Pasted image 20260413104701.png]]

**Potrjevanje TCP**

Protokol TCP za potrjevanje uporablja kombinacijo pristopov: bolj je podoben pošiljanju zadnjih (angl. *go-back-N*) s to razliko, da ob poteku časovne kontrole ponovi le pošiljanje najstarejšega segmenta v oknu in ne celotnega okna segmentov.

Spomnimo se lahko, da je prejemnik pri protokolu za pošiljanje zadnjih segmentov na račun ponovnega pošiljanja celotnega okna lahko zavračal segmente, ki so prispeli v nepravilnem vrstnem redu. Ker pa pri protokolu TCP pošiljatelj ne pošilja več celotnega okna, mora TCP prejemnik hraniti nepravilno sprejete segmente v medpomnilniku in jih urediti v pravilni vrstni red ob prispetju manjkajočih. Vidimo lahko, da je ta del protokola bolj podoben protokolu za ponavljanje izbranih segmentov. V primeru, da se poslani segment izgubi in da prejemnik prejme segment s previsoko številko, prejemnik **zazna vrzel** v številkah. V tem primeru prejemnik odgovori s številko potrditve tistega segmenta, ki je še zadnji prišel v pravilnem vrstnem redu. Kadar pošiljatelj ponovi pošiljanje manjkajočih segmentov, začne s tem prejemniku **polniti vrzel** v manjkajočih številkah. V tem primeru prejemnik sproti potrjuje pakete, ki so mu do tega trenutka manjkali.

Poleg opisanih splošnih principov potrjevanja ima TCP še nekaj specifik:
- Če je prejemnik vse prejšnje segmente že potrdil, potem ob sprejemu naslednjega segmenta v pravilnem vrstnem redu prejemnik izvede **zakasnjeno potrjevanje** (angl. *delayed acknowledgment*). Pri zakasnjenem potrjevanju prejemnik ne odgovori s potrditvijo takoj, temveč počaka 500 ms. V kolikor v tem času pride še drugi novi segment, prejemnik izvede kumulativno potrditev obeh tako, da potrdi le zadnji prejeti segment, s čimer implicitno potrjuje uspešen prejem tudi prvega. Poudarimo, da po prejemu drugega segmenta prejemnik ne izvaja ponovnega čakanja intervala 500 ms, temveč mora nujno poslati potrditev. V kolikor v intervalu 500 ms prejemnik ne sprejme še drugega segmenta, potrdi samo prvega po preteku intervala. Opisani postopek omogoča, da lahko prejemnik pošilja potrditve samo za vsaki drugi segment, s čimer se zmanjša potrebna količina režije pri pošiljanju. Poudarimo še, da prejemnik ob polnjenju vrzeli ne uporablja zakasnjenega potrjevanja, ampak brez zakasnitve potrdi vsak prej manjkajoči paket.
- V primeru, da pošiljatelj pošlje pet paketov (P1, P2, P3, P4 in P5) in od prejemnika prejme potrditev za prvi paket (ACK1), ki ji sledijo še tri kopije iste potrditve (ACK1, ACK1, ACK1; skupno torej štiri enake potrditve) je to znamenje, da je prejemnik uspešno prejel P1, P3, P4 in P5, paket P2 pa da se je izgubil (tri kasnejše enake potrditve so posledica zaznane vrzeli pri prejemu segmentov). Ob takšnem scenariju pošiljatelj izvede postopek **hitrega ponovnega pošiljanja** (angl. *fast retransmit*). Pri tem postopku pošiljatelj ne čaka na potek časovne kontrole za potrditev paketa P2, temveč takoj ob prejemu četrte iste potrditve ponovi pošiljanje P2. S tem postopkom pošiljatelj skrajša nepotreben čas za ponovno pošiljanje in prepreči preveliko kopičenje paketov v prejemnikovem sprejemnem medpomnilniku.

**Nadzor pretoka**

**Nadzor pretoka (flow control)** usklajuje hitrost pošiljanja med komunikacijo, da prejemnik ne bi bil preobremenjen. Če pošiljatelj pošlje preveč podatkov, se prejemnikov medpomnilnik prelije, kar zahteva ponovno pošiljanje in zmanjša učinkovitost.

TCP uporablja številčenje bajtov. Prejemnik spremlja zasedenost medpomnilnika kot:
- zasedeno = zadnji sprejeti bajt – zadnji bajt, predan aplikaciji.
- **Prostor (rwnd)** = velikost medpomnilnika – zasedeno.

Vsak TCP segment vsebuje 16-bitno polje **sprejemno okno (rwnd)**. Vanj pošiljatelj in prejemnik vpišeta trenutno razpoložljivo velikost svojega medpomnilnika in tako sogovornika sproti obveščata o svojih zmožnostih.

Zato ob vzpostavitvi povezave (trojno rokovanje) poleg začetnih številk izmenjata tudi začetni velikosti medpomnilnikov.

**Nadzor zasičenja**

Zasičenje omrežja je stanje omrežja ko ne more procesirati količne informacij v njem. 

*Ker ima vsak usmerjevalnik omejen pomnilnik za čakajoče pakete se novi paketi za katere ni prostora zavržejo in pride do packet lossa. Če paketi niso zavrženi lahko čakajo predolgo in imamo queueing delay. Po povezavah se začnejo prenašati ponovitve paketov in pride do zmanjšanja prenosa novih podatkov, ko se vse to nabira pride do preobremenitve in na koncu se ne prenaša skoraj nič uporabnega. Pride do * **congestion collapsa**.

Razlogi za zasičenost so lahko 
- hitrost procesiranja pošiljateljev in prejemnikov,
- hitrost proceisranja usmerjevalnikov
- velikosti medpomnilnikov

Za preprečevanje zasičenja uoprabljamo pristopa z **odprto zanko** in **zarpto zanko**

**Odprta zanka** je sistem, ki nima podatkov iz omrežja in mitigacijo zasičenosti izvaja po svojih vnaprej določenih pravilih.

To vključuje 
- odločanje o ponovnem pošiljanju paketov, *manjkajoč ACK lahko pomeni dolgo čakalno vrsto, rešujemo z algoritmi za nastavljanje časovne kontrole*
- velikost pošiljateljevega okna, *koliko bajtov lahko pošljemo brez prejete potrditve, omejuje fizično hitrost pošiljatelja* 
- odločanje o zavračanju paketov, *pri nekaterih aplikacijah je zavračanje bolj smiselno - videoklici*
- način potrjevanja, *lahko se odločimo za komulativno namesto posamezno*
- možnostih za vzpostavljanje dodatnih novih povezav, *če je omrežje preobremenjeno omejimo ali onemogočimo priklop novih naparav nanj*


**Zaprta zanka** je sistem kjer naprave v omrežju komunicirajo med sabo in se obveščajo o zasičenju omrežja.

Uporablja se lahko
- ECN oz. Explicit Congestion Notification, kjer usmerjevalnik opazi, da se njegovi medpomnilniki polnijo in da lahko pride do zasičenja. V tem primeru v IP headerju označi zastavico CE *Congestion Experienced*. Oznaka potuje do prejemnika, ki jo posreduje pošiljatelju, ki zmanjša hitrost. *Dodan v IP in TCP protokol kot test a je manj v uporabi.*
- Choke Packets ki se uporabljajo ko je usmerjevalnik zasičen, v katerem primeru se pošlje pošiljatelju nadzorno sporočilo za zmanjšanje hitrosti.
- Backpressure je sistem kjer zasičen usmerejevalnik ukaže prejšnjemu da se naj upočasni, ta naslednjemu in tako vse do pošiljatelja.
- Sprejemna naprava lahko zavrača dohodni promet če ga prihaja preveč in to sporoči pošiljatelju


TCP uoprablja odprto zanko, kjer pošiljatelj ob opazovanju prejetih potrditev prilagaja hitrost pošiljanja. 

Če uspešno dobi ACK znotraj predvidene časovne kontrole postopoma zvišuje hitrost pošiljanja, v nasprotnem primeru sklepa da prehajamo v zasičenje in zmanjša hitrost.

Hitrost pošiljanja je odvisno od **okna za nadzor zasičenja** *angl. congestion window* označeno s **cwnd**. Pošiljamo z maksimalno hitrostjo $\min(\text{rwnd}, \text{cwnd})$.

Velikost $\text{cwnd}$ merimo v enotah $\text{MSS}$ *angl. maximum segment size* ki določa velikost največjega dovoljenega segmenta TCP (brez glave).

$\text{MSS}$ je neposredno povezana z $\text{MTU}$ oz. *maximum transmission unit, na povezavni plasti*, velja torej da je $\text{MSS}$ manjši od $\text{MTU}$ in sicer za vsaj $40$ bajtov, saj je velikost glave IP in TCP protokolov 20. Torej velja $\text{MSS} \leq  \text{MTU}-40$.

Obstaja več različic TCP protokola. Ukvarjamo se s **TCP Reno**, kjer nadzorovanje zasičenja poteka po naslednjih korakih

Prva faza je **počasni začetek (Slow Start)**, v kateri se velikost okna zasičenja povečuje eksponentno. Pošiljatelj začne z začetno vrednostjo `cwnd` = 1 MSS (Maximum Segment Size). Za vsako prejeto potrditev (ACK) se okno poveča za 1 (`cwnd` = `cwnd` + 1), kar pomeni, da se po vsakem krogu (RTT) število poslanih paketov podvoji. Ko pride do izgube paketa ob doeseženem timeoutu se polovična vrednost `cwnd` nastavi kot `sstresh`. `cwnd` gre na 1 in izvajamo prvo fazo dokler ne dosežemo ali presežemo `sstresh`.

Če je dosežen ali presežen gremo na drugo fazo.

Druga faza je **izogibanje zasičenju (Congestion Avoidance)**. V tej fazi se rast okna spremeni iz eksponentne v linearno. Velikost okna se poveča za 1 šele takrat, ko so potrjeni vsi paketi iz trenutnega okna (približno 1 MSS na RTT). Če je trenutni cwnd npr. 16, mora pošiljatelj prejeti 16 potrditev, da se okno poveča na 17. S tem mehanizmom se protokol nadzorovano približuje polni prepustnosti omrežja.

Če se v teh korakih zgodi da je izguba paketa karakterizirana s tem da ppošiljatelj prejme 3 ACK. To zaznamuje da omrežje deluje a se je nek paket nekje izgubil, namesto da se je omrežje zamašilo.

Tretja faza je **hitra obnova (Fast Recovery)**. Namesto čakanja na časovni pretek (timeout), pošiljatelj takoj ponovno pošlje manjkajoči paket (hitro ponovno pošiljanje). Pri tem se prag (ssthresh) nastavi na polovico trenutnega `cwnd`, vrednost `cwnd` pa se postavi na `ssthresh + 3`. S tem se TCP Reno izogne ponovnemu začetku iz faze 1 MSS in ohranja višjo prepustnost. Ko je izgubljeni paket potrjen, se protokol vrne v fazo izogibanja zasičenju.

![[Pasted image 20260504223531.png]]

TCP Tahoe je različica ki uporablja samo prvo in drugo fazo.
TCP Reno doda tretjo fazo.
TCP Vegas doda zaznavanje situacij ki vodijo v zasičenje in linearno zmanjševanje hitrosti pošiljanja ob zasičenju.


***

**Pravičnost TCP**

Protokol TCP prek mehanizma za nadzor zasičenja samodejno zagotavlja, da se razpoložljiva pasovna širina med uporabniki sčasoma porazdeli pravično. Če si dva uporabnika delita povezavo s kapaciteto $C$, njuni hitrosti na grafu omejuje padajoča premica med točkama $(C, 0)$ in $(0, C)$, ki predstavlja polno izkoriščenost kanala. Idealna pravična delitev se nahaja na diagonali kvadranta, kjer sta hitrosti obeh uporabnikov enaki, optimalno stanje pa predstavlja sredinska točka $(\frac{C}{2}, \frac{C}{2})$.

Prilagajanje hitrosti poteka iterativno po načelu linearnega povečevanja in multiplikativnega zmanjševanja. Ob uspešno prejetih potrditvah oba pošiljatelja svojo hitrost linearno povečujeta, kar na grafu vidimo kot premik desno navzgor pod kotom 45 stopinj. Ko skupna hitrost preseže kapaciteto kanala, pride do izgube segmentov, zaradi česar oba uporabnika svojo hitrost prepolovita. Ta umik proti izhodišču $(0,0)$ v kombinaciji s ponovnim linearnim naraščanjem povzroči, da se delovna točka z vsakim ciklom zasičenja bolj približa diagonali pravičnosti. Rezultat tega procesa je konvergenca proti sredinski točki grafa, kar dokazuje, da je pravična delitev vgrajena v samo zasnovo protokola TCP in deluje tudi pri večjem številu uporabnikov.

**Pravičnost UDP**

UDP ne skrbi za nadzor zasičenja ali zanesljive dostave torej se vsi borijo za kapaciteto in ni nobenega sistema ki bi karkoli porazdelili posredno ali neposredno.

Če se uporabljata v istem omrežju TCP in UDP bo TCP vedno na slabšem.