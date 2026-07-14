Aplikacije za komunikacijo uporabljajo aplikacijske protokole.

Razlikovati moramo med aplikacijami na računalniku in omrežnimi aplikacijami.

Ko govorimo o omrežnih aplikacijah govorimo o porazdeljenih aplikacijah. 
To pomeni da deli aplikacije tečejo na različnih napravah, kar pomeni da je delovanje aplikacije odvisno od vseh delov.

Del omrežne aplikacije so aplikacijski protokoli s katerimi omogočimo komunikacijo med razlčinimi deli omrežne aplikacije.

> Komunikacijska plast torej skrbi za komunikacijo med različnimi deli aplikacije na različnih napravah.

Aplikacija ne potrebuje nujno komponente s GUI.

Za posamezno aplikacijo se lahko pri implementaciji komunikacije med različnimi deli posvetimo samo razvoju aplikacijskega protokola, ki ga bomo uporabljali, podrobnosti omrežja pa lahko zanemarimo.

Primeri omrežnih aplikacij so
- email
- splet
- instant messaging
- remote login
- izmenjava datotek
- multimedijske aplikacije
- igre
- družabna omrežja
- ip telefonija

Aplikacije uporabljajo arhitekture **client-server** , **P2P** ali pa v **mešano arhitekturo**.

Pri **client-server** arh. je strežnik ves čas dostopen, odjemalci pa se priključijo občasno. *http, ftip, telnet, email*

Pri **P2P** sistemih končni uporabniki neposredno komunicirajo med seboj, če imamo omrežje na več napravah lahko kater od teh postane  nedostopna brez da se poruši celotno delovanje.

Mešana arhitektura je kombinacija, ponavadi nek server ki poskrbi za vzpostavitev komunikacije, ta pa potem deluje neposredno med končnima napravama.

Aplikacijski protokoli so ponavadi berljivi uporabniku, saj je vsebina ponavadi shranjena v tekstu v nekih strukturah.
Ta vsebina je potem porazdeljena v več paketov.

Protokoli so lahko javni so npr.: BitTorrent, DNS, HTTP, IMAP, LDAP, NTP, POP3, RDP, RTP, SMTP, SSH. Ponavadi so to uveljavljeni standardi za razširjene omrežneaplikacije. 

Ti so ponavadi definirani v specifikacijah RFC *Request For Comments* objavljeni na straneh IETF.

Lahko so lastniški, pri teh intelektualne pravice ohranjajo razvijalci. Nekateri imajo javne spceifikacije, nekateri ne.

***

Pri razvoju omr. apl. lahko izbiramo med UTP in TCP, to je odvisno od tega kaj rabimo
- **hitrost**
- **zanesljivost**

UDP je hiter, ne preverja zasičenosti, uspešnost dostavljanja, manjša glava.

TCP je zanesljiv in skrbi za zasičenje, zato je počasnejši.

DNS in DHCP uporabljata UDP, ampak ker morata biti zanesljiva se ta del prenese na aplikacijsko plast.
*To se uporablja ker naj bi bil DNS hiter in manj obremeni strežnik, saj ne rabi vzdrževati seje.*


***

**HTTP**

Ko se je http prvič pojavil je omogočil dostop do vsebin na zahtevo, kar se je razlikovalo od radijev in televizij, kjer tega ni bilo. Kdorkoli je lahko obljavljal karkoli je hotel. Omogočil je iskanje, slike, zvok, videe, kar je bilo prej veliko bolj omejeno.

Je glavni protokol ki se uporablja v spletu. Zagotavlja prenos datotek, kot so besedilo (HTML), slike, videoti, itd. med strežnikom in odjemalcem.

V spletu deluje v arhitekturi client-server, kjer strežnik prejema requeste na vratih 80, odejmalec pa nanj pošilja requeste in prejema odgovore. Za zanesljivost skrbi TCP. 

Pravimo da **ne hrani stanja** kar pomeni da strežnik ne hrani nobenih informacij o prejšnjih sehaj ali interakcijah s clientom.

Vsaka zahteva je popolnoma izolirana. Ni sistema ki bi strežniku povedal da to zahtevo pošilja isti client. 

Ker strežniku ni treba hraniti stanja vsakega uporabnika lahko dela veliko hitreje in omogoča lažje skaliranje saj vsak strežnik lahko obdela vsako zahtevo. Spomin podatkov se delegira drugim delom aplikacije.

**Oblika HTTP sporočila**

HTTP sporočilo ima posebno obliko.

**HTTP request** je sestavljen iz začetne vrstice *request line* sledijo mu več vrstic glave *header lines*, potem prazna vrstica potem pa opcijsko še telo.







![[Pasted image 20260516202505.png|500]]






```
GET /index.html HTTP/1.1
Host: www.primer.si
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64)
Accept-Language: sl-SI,sl;q=0.9,en;q=0.8
Connection: keep-alive
```


Request line se začne z **metodo**, ki definira dejanje, ki ga odjemalec zahteva od strežnika. Najpomembnejše so GET, POST, PUT, DELETE,... medtem ko so manj pomembne tudi HEAD, TRACE, CONNECT, OPTIONS,...

Tukaj je tabela iz slike v formatu Markdown:

| metoda | opis |
| :--- | :--- |
| **GET** | zahtevek po objektu (npr. besedilu spletne strani, sliki ipd.) |
| **POST** | zahtevek po objektu, ki istočasno strežniku pošilja podatke (pogosto uporabno v primeru pošiljanja vsebin polj v spletnem obrazcu, ki jih je vnesel uporabnik). Omenimo, da lahko podatke strežniku posredujemo sicer tudi z uporabo metode GET, pri čemer jih ne zapišemo v telo zahtevka, temveč kot nadaljevanje zahtevanega naslova URL za znakom "?" (npr. v naslovu `http://.../stran.html?lang=slv&id=31318` sta *lang* in *id* parametra, katerih vrednosti pošiljamo strežniku) |
| **HEAD** | zahteva po samo glavi odgovora brez vsebine zahtevanega objekta (uporabno za razhroščevanje) |
| **PUT** | nalaganje vsebine na strežnik |
| **DELETE** | brisanje vsebine s strežnika |
| **TRACE** | zahtevek za razhroščevanje, ki vrne odmev (angl. *echo*) poslanega zahtevka |
| **CONNECT** | zahtevek za povezavo preko medstrežnika |
| **OPTIONS** | povpraševanje o možnih opcijah pri zahtevku. |

Vrstica zahtevka vsebuje še dve polji.

Polje **URL** določa objekt na serverju, opredeljen z njegovim naslovom.

Polje **verzija** opredeljuje verzijo uporabljanega protokola in ima običajno vrednost HTTP/1.1. 

Vsa polja vrstice zahtevka so ločena s presledkom, vse vrstice pa se končajo s kombinacijo znakov za prehod v novo vrstico CR-LF (angl. carriage return-line feed).

Vrstici zahtevka lahko sledi več vrstic glave, ki podajajo množico parov v obliki ključ–vrednost. Vsaka vrstica se začne z imenom ključa potem sledi dvopičje potem pa vrednost tega polja.

Poleg približno 40 različnih standardiziranih ključev, ki jih lahko opredelimo v vrsticah glave, obstaja tudi veliko število nestandardiziranih, ki jih lahko uporabljajo izbrani spletni strežniki ali medstrežniki, ki izvajajo spletno predpomnenje. 

Od standardnih bomo v nadaljevanju omenili tri pogosto uporabljane, ki so *Host*, *Connection* in *If-Modified-Since*. 

```http
GET /online HTTP/1.1
Host: ldhbncxkztwsrfmv.neverssl.com
Connection: close
```

Druga možna protokolarna oblika sporočila je **odgovor HTTP** (angl. *HTTP response*), ki ga strežnik vrne odjemalcu kot odgovor na prejeti zahtevek.







![[Pasted image 20260516203614.png|580]]






Struktura odgovora je zelo podobna strukturi zahtevka, z nekaj razlikami v pomenu in vsebini posameznih polj. Statustna vrstica je prva, nato pa sledijo vrstice glave, nova vrstica in opcijsko še telo.

Statusno vrstico odgovora tvorijo polja **verzija**, ki podaja verzijo uporabljanega protokola HTTP, in polji **statusna koda** ter **opis statusa**, ki podajata numerično in opisno kodo statusa strežnikovega odgovora. 

Kode in opise statusov delimo v pet skupin glede na njihovo resnost. Skupine različnih statusov so grupirane glede na prvo števko v trimestni kodi odgovora.


| KODA | OPIS STATUSA | RAZLAGA |
| :--- | :--- | :--- |
| **1xx** | **INFORMATIVNO** | |
| 100 | Continue | strežnik je prejel glavo in sporoča, da pričakuje še telo zahtevka |
| 102 | Processing | strežnik sporoča, da še vedno obdeluje zahtevek (zaradi preobremenjenosti) |
| **2xx** | **USPEH** | |
| 200 | OK | standarden odgovor za uspešen zahtevek |
| **3xx** | **PREUSMERITEV** | |
| 301 | Moved Permanently | sporočilo, da mora biti zahteva naslovljena na drugi podani naslov |
| 304 | Not Modified | sporoča, da zahtevan vir ni bil spremenjen od podanega datuma (uporabno pri medstrežnikih) |
| 305 | Use Proxy | zahtevan vir je na razpolago samo pri uporabi medstrežnika |
| **4xx** | **NAPAKA NA STRANI KLIENTA** | |
| 400 | Bad Request | strežnik ne razume zahtevka, verjetno zaradi napačne sintakse |
| 403 | Forbidden | dostop do vira je prepovedan, verjetno zaradi pomanjkanja pravic za dostop do strežnikovega datotečnega sistema |
| 404 | Not Found | vira ni mogoče najti |
| 408 | Request Timeout | potek časovne kontrole za to, da klient v celoti dokonča zahtevek |
| 429 | Too Many Requests | uporabnik je v časovni enoti poslal preveliko število zahtevkov |
| **5xx** | **NAPAKA NA STRANI STREŽNIKA** | |
| 500 | Internal Server Error | generično sporočilo za napako na strežniku, ko je strežnik ne more podrobneje opredeliti |
| 501 | Not Implemented | strežnik nima implementirane metode, opredeljene v zahtevku |
| 502 | Bad Gateway | strežnik, ki opravlja funkcijo medstrežnika, je od tretjega strežnika prejel neveljaven odgovor |
| 505 | HTTP Version Not Supported | verzija protokola HTTP, uporabljena v zahtevku, ni podprta na strežniku |

Poleg statusne vrstice odgovor HTTP vsebuje tudi vrstice glave, ki so v enaki obliki kot vrstice glave zahtevka, in opcijsko telo, ki vsebuje podatke, s katerimi odgovori strežnik. 

Tudi vrstice glave odgovora HTTP delimo v standardizirane in nestandardizirane, opredeljene pa so v istih virih kot zahtevki HTTP. Od njih omenimo najbolj pogoste: *Connection* (status povezave), *Date* (datum in čas pošiljanja odgovora), *Server* (ime strežnika), *Last-Modified* (čas zadnje spremembe prejetega vira), *Content-Length* (dolžina vira v bajtih) in *Content-Type* (tip MIME vsebine, npr. `text/html`, `image/jpeg`, `audio/mpeg` ipd.)

```http
HTTP/1.1 200 OK
Content-Type: text/html
Content-Length: 2778
Connection: close
Date: Mon, 05 Nov 2007 12:18:23 GMT
Server: Apache/1.3.0 (Unix)
Last-Modified: Fri, 16 Feb 2018 21:32:40 GMT
```

**Vrste povezav**

Iz vrstic glave v HTTP requestu smo videli, da lahko odjemalec od strežnika zahteva prekinitev povezave s ključem `Connection: Close`, čemur pravimo, da odjemalec izvede **nevztrajno** (angl. *non-persistent*) povezavo. Ko odjemalec dobi kar je rabil zapre povezavo. 

Ker vemo, da se za izvedbo zahtevka HTTP vzpostavi povezava TCP, postopek trojnega rokovanja pri njeni vzpostavitvi tudi zahteva svoj čas. Iz tega sledi, da se za vsak prenašani vir s strežnika (stran z besedilom, sliko ipd.) porabi 2 RTT časa (1 RTT za rokovanje + 1 RTT za prenos; predpostavimo, da lahko odjemalec v tretji fazi rokovanja že pošlje podatke po principu *na štuporamo*).

Alternativa nevztrajni povezavi bi lahko bila, da odjemalec ob pošiljanju zahtevka ne zahteva rušenja povezave (izpusti ključ `Connection: Close`) in s tem zahteva **vztrajno povezavo** (angl. *persistent*), oziroma da povezava ostane po prejemu odgovora še vedno odprta. V nadaljevanju lahko odjemalec in strežnik uporabita isto povezavo za pošiljanje morebitnih nadaljnjih virov, ki so lahko del iste spletne strani (npr. slike s spletne strani), s čimer se izognemo ponovni potrebi po rokovanju pri protokolu TCP. To pomeni, da prenos vseh odgovorov razen prvega lahko izvedemo že v času 1 RTT, kar predstavlja bistveno pohitritev kot pri nevztrajnih povezavah. Iz poznavanja nadzora zasičenja protokola TCP obenem vemo, da protokol povečuje hitrost pošiljanja, kar vodi v dodatno prednost dlje časa odprte povezave, ki lahko čas prenosa še dodatno pohitri.









![[Pasted image 20260516212302.png|580]]









Poleg navadnih vztrajnih povezav poznamo tudi njihovo posebno obliko: **vztrajne povezave s cevovodom** (angl. *pipelined persistent*). Omogoča pošiljanje več vzporednih zahtevkov strežniku naenkrat. Takšen način pošiljanja smo spoznali že kot *tekoče pošiljanje* na transportni plasti. Enako kot tam, morata tukaj odjemalec in strežnik na aplikacijski plasti voditi seznam poslanih in že potrjenih aplikacijskih zahtev, ki so neodvisne od potrjevanja na transportni plasti.

**Uporaba piškotkov**


HTTP protokol ne hrani stanja povezav (angl. *stateless*), kar pomeni, da strežnik ne vodi evidence o preteklih zahtevah. 

Delovanje spletnih strežnikov je na ta način preprosto, vendar pa v taki obliki ne podpira sodobnih spletnih aplikacij, ki potrebujejo tudi informacijo o stanju. Potrebe po ukrepanju glede na predhodne akcije uporabnika lahko namreč vidimo v naslednjih primerih:

*   **spletne trgovine:** uporabniku je potrebno slediti skozi nakupovalne korake in npr. v nakupovalni košarici prikazati artikle, ki si jih je izbral v prejšnjih korakih,
*   **personalizacija:** če si uporabnik nastavi posebne nastavitve prikaza spletnega mesta (npr. barva ozadja, oblika spletnega vmesnika), je potrebno, da ga strežnik identificira in mu prikaže njegovo personalizirano vsebino,
*   **priporočila:** da spletna stran prikaže uporabniku priporočila o sorodnih artiklih ali zanimivih filmih, mora spremljati zgodovino uporabnika skozi katero analizira, kaj uporabnika zanima,
*   **avtorizacija:** da uporabniku omogočimo dostop do spletnih virov, ga je predhodno potrebno avtenticirati in na podlagi njegove identitete sproti preverjati pravice dostopa do zahtevanih spletnih virov.

Problem pomanjkanja podatkov o stanju pri protokolu HTTP lahko rešimo z uporabo **piškotkov** (angl. *cookies*). Piškotki so kratki nabori podatkov, ki lahko hranijo podatke v strukturi ključ–vrednost, poleg njih pa tudi identifikator, ki ga strežnik dodeli odjemalcu. Strežnik dodeli odjemalcu piškotek z uporabo polja *Set-Cookie* v glavi strežnikovega odgovora HTTP. Po prejetju piškotka ga odjemalec običajno shrani v svojem datotečnem sistemu, do katerega dostopa tudi brskalnik. Odjemalec nadalje pri vsaki komunikaciji s strežnikom v glavo zahtevka pripne piškotek v polje *Cookie*, s čimer ga strežnik torej lahko ponovno prepozna. Ker strežnik ve, da gre za znanega uporabnika, lahko svoje odgovore prilagodi zgodovini preteklih zahtevkov. Pri tem strežnik uporablja tudi podatkovno bazo, v kateri vzdržuje potrebne podatke o uporabniku za izvedbo aplikacije, ki potrebuje sledenje stanju uporabnika. 

![[Pasted image 20260516213215.png]]

**Varnostni pomislek:** Ker piškotke lahko uporabljamo za hranjenje podatkov o uporabniku, se je veljavno vprašati, ali so vsi nameni uporabe piškotkov dobronamerni. Žal temu ni tako, saj zbiranje podatkov o uporabnikih lahko odpira tudi etična vprašanja, kot je poseganje v uporabnikovo zasebnost. Eden bolj razvpitih primerov zlorabe piškotkov spada na področje spletnega oglaševanja, kjer se z vodenjem evidence o uporabnikovi zgodovini obiskanih strani in evidence o uporabljenih iskalnih nizih lahko uporabnike profilira z namenom ciljanega oglaševanja. Z namenom preprečevanja zlorab lahko v spletnem brskalniku onemogočimo uporabo piškotkov, v zadnjih letih pa smo bili priča tudi uvedbi zakonodaje, ki zahteva informiranje uporabnika o namembnosti piškotov na spletni strani in zahteva njegovo soglasje.

***

**Medmrežniki**

**Spletni medstrežniki** (angl. *proxy server*) so strežniki, s katerimi lahko zagotovimo hitrejši dostop do vsebin na spletu. Njihov namen je, da igrajo vlogo posrednika med odjemalcem in strežnikom in pri sebi hranijo kopije spletnih virov. Če medstrežnik pri sebi kopije zahtevanega vira še nima, jo pridobi z dostopom do pravega strežnika; v primeru, če pa kopijo že ima, jo odjemalcu takoj postreže brez nadaljnjega dostopa v svetovni splet. Na ta način medstrežnik nenehno igra vlogo strežnika proti odjemalcu in vlogo odjemalca proti pravemu strežniku na spletu.

Iz opisanega izhaja, da morajo odjemalci biti ustrezno konfigurirani, saj morajo svoje zahtevke HTTP posredovati medstrežniku in ne več neposredno strežnikom na spletu. Uporabo medstrežnikov lahko bodisi ročno nastavimo v spletnem brskalniku ali pa administrator omrežja poskrbi za samodejno nastavitev brskalnikov.

Medstrežnike lahko bodisi namestimo v lokalno omrežje (če je večje) ali pa nam jih v rabo običajno ponuja ponudnik internetnih storitev. Obe opisani postavitvi medstrežnika zagotavljata, da je ta krajevno blizu, saj to omogoča hitrejši dostop (oz. manjšo zakasnitev) do spletnih vsebin kot dostop do poljubnega strežnika kjerkoli na svetu. Namestitev medstrežnika v lokalno omrežje obenem zagotavlja manj prometa na dostopni povezavi do javnega omrežja, kar lahko predstavlja tudi prihranke v primeru zakupa povezave glede na količino podatkov.

![[Pasted image 20260516213342.png]]

Medstrežniki izvajajo svoje poizvedbe tako kot prikazuje slika. V primeru, da medstrežnik zahtevanega spletnega vira še nima, naslovi na končni strežnik običajni zahtevek, s katerim pridobi lastno kopijo zahtevanega vira. V nasprotnem primeru pa, če medstrežnik že hrani lokalno kopijo oddaljenega vira, medstrežnik izvede **pogojni zahtevek GET** (angl. *conditional GET*). V tem zahtevku medstrežnik uporabi vrstico glave `If-modified-since` (primer: `If-modified-since: Wed, 12 Feb 2012 09:12:42`), ki ji sledi datum lokalne verzije vira, ki ga zahteva. S tem opredeli, da naj končni strežnik vir posreduje le v primeru, če je njegova različica novejša od lokalno shranjene različice. Končni strežnik lahko na pogojni zahtevek odgovori bodisi s pošiljanjem novejšega vira (status `200 OK`) ali pa z odgovorom s statusom `304 Not Modified`, ki ima prazno telo in torej varčuje pri ponovnem pošiljanju nepotrebnih podatkov.

***

**FTP**

FTP (angl. *File Transfer Protocol*) je protokol, ki se uporablja za dvosmeren prenos datotek. Za razliko od protokola HTTP mora strežnik FTP hraniti stanje uporabnika, saj mora uporabnika spremljati skozi postopek avtentikacije, nadzorovati avtorizacijske pravice in slediti gibanju uporabnika skozi mape v oddaljenem datotečnem sistemu.

Delovanje protokola FTP poteka na osnovi zahtevkov in odgovorov. Aplikacijska sporočila odjemalca tipično vsebujejo zahteve po prenosu datotek, ukaze za posredovanje avtentikacijskih podatkov in ukaz za zaključek seje. Na zahtevke strežnik odgovori s statusom odgovora in dodatnimi podatki, če so zahtevani.

Ukazi zahtevka

| ukaz | opis |
| :--- | :--- |
| USER ime | posredovanje uporabniškega imena |
| PASS geslo | posredovanje gesla |
| LIST | zahteva po seznamu datotek v mapi |
| CWD ime | zamenjava trenutne mape |
| RETR ime_datoteke | zahteva po prenosu datoteke s strežnika |
| STOR ime_datoteke | zahteva po shranjevanju datoteke na strežnik |
| DELE ime_datoteke | zahteva po brisanju oddaljene datoteke |
| QUIT | zaključek seje |

Ukazi odgovora

| koda statusa | opis |
| :--- | :--- |
| 125 | Data connection open, transfer starting |
| 200 | Command okay. |
| 226 | Closing data connection. |
| 227 | Entering Passive Mode &lt;h1,h2,h3,h4,p1,p2&gt; |
| 230 | User logged in, proceed. |
| 331 | Username OK, password required |
| 332 | Need account for login. |
| 425 | Can’t open data connection. |
| 426 | Connection closed; transfer aborted. |
| 452 | Error writing file |
| 425 | Can’t open data connection. |
| 500 | Syntax error, command unrecognized. |
| 530 | Not logged in. |
| 552 | Requested file action aborted. |


Posebnost protokola FTP je ta, da med odjemalcem in strežnikom tečeta dve vzporedni ločeni povezavi TCP: *kontrolna* in *podatkovna* povezava. Kontrolna povezava se vzpostavi na začetku na pobudo odjemalca, in sicer tako, da odjemalec vzpostavi povezavo TCP s strežnikom preko vrat 21, na katerih strežnik aktivno posluša. Ob vzpostavitvi kontrolne povezave odjemalec posreduje tudi (z ukazom `PORT`) svojo številko vrat, na katerih je pripravljen vzpostaviti podatkovno povezavo. Strežnik nato vzpostavi podatkovno povezavo s svojih izhodnih TCP vrat 20 na naslov, ki ga je opredelil odjemalec z ukazom `PORT`. V nadaljevanju se kontrolna povezava uporablja za prenos kontrolnih podatkov (ukazi za prenos datotek, posredovanje uporabniškega imena/gesla, menjavo map, strežnikov status odgovora itd.), podatkovna povezava pa za prenašano zahtevano vsebino (prenos podatkov, prenos seznama datotek v mapi itd.).

```bash
> ftp -d speedtest.tele2.net
Connected to speedtest.tele2.net.
220 (vsFTPd 3.0.3)
---> OPTS UTF8 ON
200 Always in UTF8 mode.
User (speedtest.tele2.net:(none)): anonymous
---> USER anonymous
331 Please specify the password.
Password:
---> PASS
230 Login successful.
ftp> dir
---> PORT 192,168,1,132,228,38
200 PORT command successful. Consider using PASV.
---> LIST
150 Here comes the directory listing.
-rw-r--r-- 1 0 0 1024 Feb 19 2016 1KB.zip
-rw-r--r-- 1 0 0 1048576 Feb 19 2016 1MB.zip
-rw-r--r-- 1 0 0 209715200 Feb 19 2016 200MB.zip
-rw-r--r-- 1 0 0 20971520 Feb 19 2016 20MB.zip
-rw-r--r-- 1 0 0 2097152 Feb 19 2016 2MB.zip
-rw-r--r-- 1 0 0 3145728 Feb 19 2016 3MB.zip
-rw-r--r-- 1 0 0 524288000 Feb 19 2016 500MB.zip
226 Directory send OK.
ftp: 1208 bytes received in 0.19Seconds 6.26Kbytes/sec.
ftp> get 1KB.zip
---> PORT 192,168,1,132,228,50
200 PORT command successful. Consider using PASV.
---> RETR 1KB.zip
150 Opening BINARY mode data connection for 1KB.zip (1024 bytes).
226 Transfer complete.
ftp: 1024 bytes received in 0.20Seconds 5.04Kbytes/sec.
ftp> quit
---> QUIT
221 Goodbye.
```

Pri opisanem načinu vzpostavljanja podatkovne povezave lahko nastopi težava, če je odjemalec skrit v omrežju za usmerjevalnikom NAT. Če odjemalec prvi ne vzpostavi podatkovne povezave, je strežnik z vrat 20 do njega ne bo mogel vzpostaviti, saj usmerjevalnik še nima zapisa za dostop do odjemalčevih vrat, ki so namenjena podatkovni povezavi. Da bi protokol FTP lahko deloval tudi v takšnih okoliščinah, obstaja tudi njegov spremenjen način delovanja, ki ga imenujemo **pasivni način**. V pasivnem načinu klient še vedno prvi vzpostavi kontrolno povezavo s strežnikovimi vrati 21. V nadaljevanju pa, namesto da pošlje strežniku ukaz `PORT`, mu pošlje ukaz `PASV`. Ob prejemu tega ukaza strežnik odpre naključna izhodna vrata (> 1024) in njihovo številko posreduje odjemalcu po kontrolni povezavi kot odgovor na ukaz `PASV`. Odjemalec je sedaj lahko tisti, ki se poveže z navedenimi vrati strežnika in prvi poskrbi tudi za vzpostavitev podatkovne povezave. Ob njeni vzpostavitvi se v usmerjevalnikovo tabelo NAT zapišejo ustrezni vnosi, tako da lahko strežnik odjemalcu pošilja tudi povratni promet.

***

**Protokoli za e-pošto**


Protokoli za elektronsko pošto ravno tako delujejo na principu odjemalec–strežnik. Arhitektura porazdeljene aplikacije vsebuje:

*   **poštne strežnike**, ki bodisi skrbijo za pošiljanje elektronskih poročil ali shranjujejo prejeto pošto v poštnih predalih uporabnikov,
*   **odjemalske programe**, ki imajo lahko bodisi besedilni (npr. Elm, Pine) ali grafični uporabniški vmesnik (npr. Microsoft Outlook, Mozilla Thunderbird, Apple Mail, Eudora, Elm),
*   **aplikacijske protokole** za pošiljanje novih (SMTP) in prebiranje dostavljenih elektronskih sporočil (POP3, IMAP4).

Tipičen življenjski cikel elektronskega sporočila je tak, da ga uporabnik sestavi z uporabo aplikacije (e-mail odjemalca) in ga nato pošlje lokalnemu poštnemu strežniku z uporabo protokola SMTP. Strežnik uvrsti sporočilo v izhodno čakalno vrsto za pošiljanje, in ko pride na vrsto, vzpostavi povezavo (neposredno ali preko verige drugih strežnikov) s ciljnim poštnim strežnikom, na katerem se nahaja elektronski predal ciljnega prejemnika elektronskega sporočila. Dokler se sporočilo hrani na strežniku uporabnika, lahko prejemnik uporabi svoj odjemalski program za prenos sporočila lokalno k sebi (npr. z uporabo protokolov POP3 in IMAP4) in njegov prikaz.

**SMTP protokol**

Tudi protokol SMTP je namenjen delovanju v načinu odjemalec–strežnik. Strežnik običajno posluša na TCP vratih 25, na katerem sprejema ukaze in podatke (elektronska sporočila), ki pa morajo biti zakodirano v kodno tabelo znakov 7-bitno ASCII. Ker so dokumenti in slike, ki jih običajno pošiljamo kot priponke, kodirane z binarnim kodiranjem (različno dolga zaporedja bitov predstavljajo kodirane objekte in ne znake), to pomeni, da moramo mora pošiljatelj binarne priponke pred pošiljanjem prekodirati v 7-bitni ASCII, prejemnik pa to storiti v obratno smer. Ker kodiramo iz bolj obsežnega predstavitvenega nabora znakov v 7-bitni nabor (128 znakov) to pomeni, da se pri tem dolžina priponk običajno poveča.


| ukaz | opis |
| :--- | :--- |
| HELO | predstavimo se strežniku z opredelitvijo imena lastne domene |
| MAIL FROM: | podamo naslov pošiljatelja |
| RCPT TO: | podamo naslov prejemnika; ukaz lahko uporabimo večkrat, če imamo več prejemnikov |
| DATA | pričetek pošiljanja podatkov (vsebine sporočila); pošiljanje zaključimo z zaporedjem &lt;prehod v novo vrstico&gt;.(pika)&lt;prehod v novo vrstico&gt; |
| QUIT | zaključek seje s strežnikom |


| koda statusa | opis |
| :--- | :--- |
| 220 | Server is ready. |
| 221 | Closing connection. |
| 250 | Requested mail action okay, completed. |
| 354 | This is a reply to the DATA command. After getting this, start sending the body of the mail message, ending with "\r\n.\r \n" |
| 500 | The last command contained a syntax error or the command line was too long. |
| 503 | The last command was sent out of sequence. For example, you might have sent DATA before sending RECV. |
| 552 | The recipient mailbox is full. Try again later. |
| 553 | The mail address that you specified was not syntactically correct. |

Elektronsko sporočilo, ki ga odjemalec vnese po ukazu `DATA`, je sestavljeno iz vrstic glave, prazne vrstice in telesa (vsebine) sporočila. Podobno kot pri protokolu HTTP, glava hrani množico parov ključ–vrednost, ki opredeljujejo dodatne podatke aplikacijskemu odjemalcu za prikaz sporočila končnemu uporabniku. Glava običajno vsebuje vsaj polji `From:` in `To:`, ki opredeljujeta tudi polni osebni imeni pošiljatelja in prejemnika, in polje `Subject:`, ki podaja zadevo sporočila. 

```bash
220 postni.streznik.si ESMTP
HELO domena.com
250 postni.streznik.si
MAIL FROM:moje.ime@domena.com
250 2.1.0 Ok
RCPT TO:ime.prejemnika@druga.domena.com
250 2.1.5 Ok
DATA
354 End data with <CR><LF>.<CR><LF>
From: Ime Priimek <moje.ime@domena.com>
To: Prejemnik <ime.prejemnika@druga.domena.com>
Subject: Kratko sporocilo
To je e-mail sporocilo brez priponke.
.
250 2.0.0 Ok: queued as C29CE4010A
QUIT
221 2.0.0 Bye

```

Za zaključek lahko naredimo še kratko kvalitativno primerjavo protokolov protokola SMTP z že znanim protokolom HTTP, s katero lahko poudarimo bistvene razlike v principih delovanja:

*   medtem ko protokol HTTP deluje s principom *pull* (prenos podatkov – spletnih virov s strežnika k odjemalcu), deluje protokol SMTP s principom *push* (prenos podatkov – elektronskega sporočila od odjemalca k strežniku),
*   za razliko od protokola SMTP, ki zahteva kodiranje podatkov v naboru 7-bitni ASCII, lahko protokol HTTP uporablja tudi binarno kodiranje,
*   medtem ko se pri protokolu HTTP vsak objekt pošilja ločeno v svojem aplikacijskem sporočilu, se pri protokolu SMTP lahko več objektov (sporočila, priponke) prenese v istem sporočilu,
*   protokol HTTP lahko uporablja bodisi vztrajne ali nevztrajne povezave, medtem ko so povezave pri protokolu SMTP vedno vztrajne.


**POP protokol**

SMTP omogoča pošiljanje elektronske pošte, za dostop do elektronskega predala na serverju in prenos sporočil na lokalno napravo se uporabljajo drugi protokoli kot so POP *Post Office Protocol* in IMAP *Internet Message Access Protocol*.

Protokol POP je preprostejši in omogoča osnovne funkcije, kot so avtentikacija uporabnika pri dostopu do elektronskega predala, pregledovanje in prenos pošte s strežnika. 

Protokol IMAP je mlajši in nekoliko naprednejši, poleg funkcionalnosti protokola POP pa omogoča tudi samo prenos glav elektronskih sporočil, organizacijo sporočil po mapah in bolj zanesljivo vzporedno delo s strežnikom s strani več hkratnih odjemalcev (slednje sicer zvišuje obremenjenost strežnika). 

Omenimo še, da v sodobnem času do elektronske pošte dostopamo pogosto tudi kar preko spletnih odjemalcev, ki jih uporabljamo v spletnem brskalniku (npr. Gmail, Yahoo!, Outlook, Mail.com, AOL ipd.). Tak dostop do odjemalčevega aplikacijskega vmesnika sicer deluje na podlagi protokola HTTP, a v ozadju lahko te spletne aplikacije uporabljajo tradicionalne protokole za dostop do spletnih strežnikov podjetja, kot je tudi protokol POP.

Strežnik protokola POP deluje običajno na TCP vratih 110. Dialog med odjemalcem in strežnikom tipično poteka v treh fazah: (1) avtentikacija, (2) prenos sporočil in (3) zaključek dialoga in posodabljanje elektronskega predala. Tako kot protokola HTTP in SMTP tudi protokol POP ne hrani informacije o stanju, deluje pa s principom *pull* (prenos podatkov s strežnika k odjemalcu). Pogosti aplikacijski zahtevki odjemalca so prikazani v tabeli 6.8, odgovori strežnika nanje pa so izredno preprosti, saj strežnik večinoma odgovori z `"+OK"` ali napako `"-ERR pojasnilo"`, ki podaja razlog za neizvedbo operacije (npr. neznano uporabniško ime, napačno geslo, neobstoječe elektronsko sporočilo).

 Iz vsebine sporočila v tem primeru lahko vidimo, kako aplikacijski odjemalci in strežniki, preko katerih je sporočilo potovalo, dodajo številne dodatne vrstice glave. Med njimi najbolj prevladujejo vrstice `Received:`, ki beležijo, kdaj je kateri strežnik na poti sporočilo prevzel.


```bash
OK Server ready.
USER gandalf
+OK
PASS ushal1n0tpass
+OK Logged in.
LIST
+OK 5 messages:
1 2279
2 2256
3 2357
4 12582
5 12375
.
RETR 5
+OK 3356 octets
Return-Path: <bilbo@lotr.com>
Delivered-To: <gandalf@lotr.com>
Received: from localhost (localhost [127.0.0.1]) by mail.fri.uni-lj.si (Postfix)
with ESMTP id 2150540120for <gandalf@lotr.com>; Wed,8 Apr 2020
13:14:28 +0200 (CEST)
Received: from mail.fri.uni-lj.si ([127.0.0.1])by localhost (mail.fri.uni-lj.si
[127.0.0.1]) (amavisd-new, port 10024)with ESMTP id 73JgSsF87D09 for
<gandalf@lotr.com>;Wed,8 Apr 2020 13:14:26 +0200 (CEST)
Received: from mail-FRI.fri1.uni-lj.si (unknown [212.235.188.21]) by
mail.fri.uni-lj.si (Postfix) with ESMTPS id CD24B4010C for
<gandalf@lotr.com>; Wed,8 Apr 2020 13:14:26 +0200 (CEST)
< ... skraj²an izpis glave elektronskega sporo£ila ... >
To: "gandalf@lotr.com" <gandalf@lotr.com>
Subject: Lep pozdrav
Thread-Topic: Lep pozdrav
Thread-Index: AdYNltz9bY69R1JLQLWw01hHP9Y4cg==
Date: Wed, 8 Apr 2020 11:14:26 +0000
Message-ID: <bdef88babdfc4a9faeaf3ef0a2a90ef9@fri.uni-lj.si>
Moj prvi e-mail!
.
DELE 5
+OK Marked to be deleted.
QUIT
+OK Logging out, messages deleted.
```


| ukaz | opis |
| :--- | :--- |
| USER u | podajanje uporabniškega imena *u* za dostop do strežnika |
| PASS p | podajanje pripadajočega gesla *p* za uporabniško ime |
| LIST | izpis seznama sporočil v obliki (# sporočila, velikost) |
| RETR \#n | prenos sporočila s številko \#n |
| DELE \#n | brisanje sporočila s številko \#n |
| STAT | statistika o številu in velikosti vseh sporočil |
| RSET | ponastavitev elektronskega predala na stanje ob začetku seje (preklic brisanja pobrisanih sporočil) |
| NOOP | operacija brez učinka, ohranja vzpostavljeno povezavo |
| QUIT | zaključek seje s strežnikom |

***

**Domain Name Service**

Čeprav smo spoznali, da na omrežni plasti naprave naslavljamo z njihovim naslovom IP, človeški uporabniki le redkokdaj uporabljamo takšno naslavljanje s številkami. Namesto pomnjenja omrežnih naslovov si veliko lažje zapomnimo besedilne ali *simbolične* naslove, ki jih za potrebe lažjega razumevanja lahko tudi smiselno hierarhično organiziramo. Na ta način si lažje zapomnimo `www.google.com` kot pa `172.217.19.100`, `ucilnica.fri.uni-lj.si` namesto `212.235.188.23`; istočasno pa lahko tudi iz naslova razberemo, da končnica `uni-lj.si` zaobjema celo hierarhijo članic univerze, kjer je FRI samo ena izmed njih. Jasno je, da je naslavljanje s simboličnimi imeni za uporabnika bolj preprosto in transparentno, saj lahko omrežne naslove po potrebi tudi spremenimo, pri tem pa z nekaj konfiguracije ohranimo isto simbolično ime.

Iz opisanega je skoraj samoumevno, da za naslavljanje omrežnih naprav z njihovimi simbolnimi imeni namesto z naslovi potrebujemo aplikacijsko storitev, ki zna za podani simbolični naslov poiskati pripadajoč omrežni naslov. Storitev, ki opravlja tovrstno nalogo, imenujemo DNS (angl. *Domain Name Service*). Poleg preslikovanja izbranega imena v pripadajoči naslov omogoča DNS tudi preslikovanje istega imena v različne omrežne naslove, s čimer se lahko zagotovi tudi porazdeljevanje bremena.

Storitev deluje z uporabo porazdeljene podatkovne zbirke, ki je organizirana hierarhično, in aplikacijskega protokola DNS za poizvedovanje po tej zbirki. Prednosti hierarhične organizacije zbirke DNS je več. Glavni razlog je, da se s tem izognemo enotni točki odpovedi in preobremenitvi oddaljene podatkovne baze, do katere bi sicer centralizirano dostopali vsi uporabniki interneta. Lahko si tudi predstavljamo, da bi sistematično vzdrževanje in zagotavljanje nenehne razpoložljivosti takšne podatkovne baze bilo zelo težko. Ob razdelitvi podatkov in poizvedb na več omrežnih naprav zagotavljamo torej višjo *skalabilnost* (sposobnost odzivnega delovanja ne glede na večanje števila uporabnikov) in zanesljivost.

V hierarhiji DNS ločimo tri nivoje strežnikov:

1.  **Korenski strežniki** (angl. *root servers*): so temeljni strežniki, ki so v DNS hierarhiji najvišje in skrbijo za usmerjanje uporabnika na strežnike v drugem nivoju hierarhije. Ker so ključni za delovanje storitve, so dostopni kar s 13 simboličnimi imeni (z imeni `a.root-servers.net`, ..., `m.root-servers.net`), od katerih vsako dejansko ne predstavlja samo enega strežnika, temveč celo gručo strežnikov, ki so v stanju medsebojne pripravljenosti v primeru izpada enega od njih. 13 omenjenih gruč strežnikov je tudi geografsko razprostrto po celotnem svetu, za njih pa skrbi 12 različnih organizacij.
2.  **Strežniki za krovne domene (TLD)** (angl. *top level domain (TLD) servers*): so strežniki, ki skrbijo za krovne domene, kamor spadajo domene držav in generične domene. V letu 2017 je obstajalo 255 krovnih imen držav, kot so `.si` (Slovenija), `.it` (Italija), `.rs` (Srbija), `.de` (Nemčija), `.tv` (Tuvalu), `.am` (Armenija), `.gl` (Grenlandija). V zadnjih letih lahko opažamo prisotnost komercializacije teh domen, saj poddomene znotraj teh držav lahko prodajajo svoja imena kot priročne skovanke, ki omogočajo lažji dostop in uspešnejše trženje (npr. domene `instagr.am`, `youtu.be`, `bi.ng`, `ti.me`, `pep.si`, `redd.it`). Poleg imen držav obstajajo tudi t.i. generične krovne domene. Prvotnim sedmim generičnim domenam, ki so predstavljale vrsto organizacije (`.com`, `.org`, `.net`, `.int`, `.edu`, `.gov` in `.mil`), se je do leta pridružilo že približno 1500 dodatnih generičnih imen, ki še bolj podrobno opisujejo vrsto organizacije ali storitve (npr. `.actor`, `.adult`, `.museum`, `.baseball`, `.blog`, `.news`, `.restaurant` ipd.).
3.  **Avtoritativni strežniki** (angl. *authoritative servers*): so strežniki, ki skrbijo za domene znotraj krovnih domen in po potrebi tudi za poddomene znotraj njih. Npr. avtoritativni strežnik Univerze v Ljubljani (za domeno `uni-lj.si`) hrani podatke o simboličnih imenih znotraj te domene (npr. za spletni strežnik `www.uni-lj.si`) in o avtoritativnih strežnikih za posamezne poddomene (npr. za `fri.uni-lj.si`, `fmf.uni-lj.si` ali `fu.uni-lj.si`).

Postopek poizvedovanja po omrežnem naslovu, ki pripada podanemu simboličnemu imenu, poteka kot zaporedje poizvedb po zgornji hierarhiji strežnikov. Denimo, da poizvedujemo po naslovu IP strežnika `www.poddomena.domena.si`. Prva poizvedba bo tedaj poslana enemu korenskih strežnikov z vprašanjem po naslovu krovnega (TLD) strežnika za domeno `.si`. Sledila bo poizvedba, poslana krovnemu (TLD) strežniku za domeno `.si`, z vprašanjem po avtoritativnem strežniku za domeno `domena.si`. Tretja v nizu bo poizvedba omenjenemu avtoritativnemu strežniku za domeno `domena.si` s poizvedbo po naslovu avtoritativnega strežnika za domeno `poddomena.domena.si`. Končno, s poizvedbo, poslano avtoritativnemu strežniku za domeno `poddomena.domena.si` z vprašanjem po naslovu računalnika `www.poddomena.domena.si`, bo ta strežnik vrnil želeni omrežni naslov.

**Predpomnjenje zapisov DNS**

V arhitekturi naprav, ki sodelujejo pri izvedbi storitev DNS poznamo tudi *lokalne strežnike DNS*. To so strežniki, ki jih običajno namestimo lokalno (v podjetju, pri ponudniku internetnih storitev) in igrajo vlogo posrednikov do hierarhije DNS. Namesto da svoje poizvedbe *iterativno* usmerjamo po hierarhiji strežnikov DNS (naprej korenskemu, nato krovnemu, nato avtoritativnim), lahko lokalnemu strežniku DNS posredujemo eno samo poizvedbo, ki jo imenujemo *rekurzivna poizvedba*, in mu prepustimo, da opravi nalogo iterativnega poizvedovanja namesto nas sam.

Uporaba rekurzivnih poizvedb nam prinaša dve pomembni prednosti. Prva je ta, da z njimi razbremenimo končne kliente pri poizvedovanju in jim omogočimo, da do rezultatov poizvedb pridejo z eno samo poslano poizvedbo. Druga pomembna prednost je ta, da lahko lokalni strežnik DNS hrani (predpomni, angl. *caching*) rezultate opravljenih poizvedb in namesto ponovnega poizvedovanja vrača shranjene odgovore. Poleg predpomnjenja odgovorov za celotna simbolična imena strežnikov, lahko strežniki DNS predpomnijo tudi delne rezultate poizvedb. Te vsebujejo naslove krovnih (TLD) strežnikov, s čimer razbremenimo korenske strežnike, in avtoritativnih strežnikov, s čimer razbremenimo krovne in druge avtoritativne strežnike. Z delnim predpomnjenjem lahko lokalni strežnik DNS skrajša verigo iterativnih poizvedb in nadaljuje od tiste točke v hierarhiji, za katero še nima predpomnjenih podatkov.

Pomembno je poudariti, da s tem dosežemo hitrejši odziv pri poizvedbah DNS in in manj prometa v omrežju. To je ključnega pomena zato, ker je DNS podporna storitev, ki jo posredno prožijo druge storitve (npr. zahtevek HTTP) in torej predstavlja del čakanja na izvedbo drugih storitev. Iz istega razloga se predpomnjenje zapisov DNS izvaja tudi na lokalnih računalnikih, s čimer se lahko v celoti izognemo izvedbi poizvedb preko omrežja.

**Zapisi virov DNS**

Omenili smo, da je poleg porazdeljenosti strežnikov porazdeljena tudi podatkovna baza vseh zapisov. Vsak strežnik v hierarhiji vsebuje podatkovno bazo, v kateri se nahaja le del zapisov, za katere je odgovoren. Te zapise imenujemo *zapisi virov* (angl. *resource records, RR*), predstavljeni pa so s četverico podatkov: `(tip, naziv, vrednost, TTL)`. V letu 2020 je pogosto uporabljanih vrst tipov zapisa okoli 45, ta seznam pa se posodablja z razvojem Interneta in potrebah ob rojevanju novih aplikacijskih protokolov.

| tip zapisa | naziv | vrednost | pomen |
| :--- | :--- | :--- | :--- |
| A | simbolično ime | naslov IPv4 | zapis naslova (address), ki hrani simbolično ime in IP številko; ti zapisi so običajno shranjeni v avtoritativnih strežnikih za izbrano domeno |
| AAAA | simbolično ime | naslov IPv6 | predstavlja naslov IPv6 (analogno tipu A) |
| NS | ime domene | ime avtoritativnega strežnika | ti zapisi običajno v TLD strežnikih za iskanje avtoritativnega strežnika neke domene |
| CNAME | psevdonim (nadomestno ime) | kanonično (pravo) ime | omogoča bolj prijazno poimenovanje javno dostopnih strežnikov (npr. `www.ibm.com` je dejansko `www.ibm.com.cs186.net`) |
| MX | psevdonim poštnega strežnika | kanonično ime poštnega strežnika | omogoča bolj prijazno poimenovanje domenskega poštnega strežnika (tako lahko npr. uporabnika s poštnim predalom na strežniku `mta5.am0.yahoodns.net` lažje naslovimo z `ime@yahoo.com`) |
| PTR | naslov IP | simbolično ime | zapis, ki omogoča vzvratne DNS poizvedbe (poizvedovanje po imenu na podlagi naslova IP) |
| CERT | enkripcijski algoritem | certifikat | hrani certifikate za kriptiranje (npr. PKIX, SPKI, PGP). |


**Protokol DNS**

Poleg hierarhije strežnikov in porazdeljene podatkovne zbirke je tretji kos sestavljanke pri storitvi DNS protokol za poizvedovanje po zbirki. Protokol DNS deluje po principu izziv-odgovor, strežnik pa sprejema zahtevke na vratih UDP 53. Strežnik ne hrani stanja povezav, v primeru izgube aplikacijskih podatkov pa na aplikacijski ravni skrbi za ponovno pošiljanje.







![[Pasted image 20260516233754.png]]






Zahtevki in odgovori aplikacijskih sporočil imajo enako strukturo. S slike lahko razberemo, da sporočilo vsebuje naslednje poglavitne komponente:

*   **identifikator** (16 bitov): polje, ki povezuje zahtevke z odgovori,
*   **zastavice in status** (16 bitov): zahteva/odgovor, vrsta poizvedbe, avtoritativnost odgovora, krajšanje sporočila, razpoložljivost rekurzije, zahtevanje rekurzije, status odgovora,
*   **število poizvedb**, ki so zaobjete v zahtevku,
*   **število zapisov**, ki so vključeni v **polju z odgovorom**,
*   **število zapisov** v polju za **avtoritativne odgovore** strežnika,
*   **število dodatnih pomožnih zapisov** v temu namenjenem polju.

Zgornja struktura kaže, da z enim samim zahtevkom lahko strežniku posredujemo več zahtevkov in prejmemo več odgovorov. Primer ročno izvedene poizvedbe z orodjem `nslookup`.

```bash
> set debug
> set d2
> set recurse
> www.abc.com
Server: UnKnown
Address: 192.168.1.254
------------
SendRequest(), len 29
HEADER:
opcode = QUERY, id = 2, rcode = NOERROR
header flags: query, want recursion
questions = 1, answers = 0, authority records = 0, additional = 0
QUESTIONS:
www.abc.com, type = A, class = IN
------------
------------
Got answer (136 bytes):
HEADER:
opcode = QUERY, id = 2, rcode = NOERROR
header flags: response, want recursion, recursion avail.
questions = 1, answers = 5, authority records = 0, additional = 0
QUESTIONS:
www.abc.com, type = A, class = IN
ANSWERS:
-> www.abc.com
type = CNAME, class = IN, dlen = 31
canonical name = d2iwv1xxkqpmiz.cloudfront.net
ttl = 300 (5 mins)
-> d2iwv1xxkqpmiz.cloudfront.net
type = A, class = IN, dlen = 4
internet address = 99.86.243.39
ttl = 60 (1 min)
<izpis skraj²an>
------------
Non-authoritative answer:
------------
SendRequest(), len 29
HEADER:
opcode = QUERY, id = 3, rcode = NOERROR
header flags: query, want recursion
questions = 1, answers = 0, authority records = 0, additional = 0
QUESTIONS:
www.abc.com, type = AAAA, class = IN
------------
------------
Got answer (296 bytes):
HEADER:
opcode = QUERY, id = 3, rcode = NOERROR
header flags: response, want recursion, recursion avail.
questions = 1, answers = 9, authority records = 0, additional = 0
QUESTIONS:
www.abc.com, type = AAAA, class = IN
ANSWERS:
-> www.abc.com
type = CNAME, class = IN, dlen = 31
canonical name = d2iwv1xxkqpmiz.cloudfront.net
ttl = 300 (5 mins)
-> d2iwv1xxkqpmiz.cloudfront.net
type = AAAA, class = IN, dlen = 16
AAAA IPv6 address = 2600:9000:206e:f600:a:896e:12c0:93a1
ttl = 60 (1 min)
-> d2iwv1xxkqpmiz.cloudfront.net
type = AAAA, class = IN, dlen = 16
AAAA IPv6 address = 2600:9000:206e:a600:a:896e:12c0:93a1
ttl = 60 (1 min)
<izpis skraj²an>
------------
Name: d2iwv1xxkqpmiz.cloudfront.net
Addresses: 2600:9000:206e:f600:a:896e:12c0:93a1
2600:9000:206e:a600:a:896e:12c0:93a1
2600:9000:206e:d000:a:896e:12c0:93a1
2600:9000:206e:8c00:a:896e:12c0:93a1
2600:9000:206e:7e00:a:896e:12c0:93a1
2600:9000:206e:fe00:a:896e:12c0:93a1
2600:9000:206e:9800:a:896e:12c0:93a1
2600:9000:206e:2a00:a:896e:12c0:93a1
99.86.243.39
99.86.243.109
99.86.243.71
99.86.243.75
Aliases: www.abc.com
```



**Varnostni pomislek:** Pozoren bralec lahko hitro pomisli na to, da lahko s spreminjanjem zapisov v strežnikih DNS preusmerjamo, kam bo poslan promet, ki je namenjen napravi z nekim simboličnim namenom. To lahko izkoristijo napadalci, ki s postopkom **zastrupljanja tabel DNS** (angl. *DNS poisoning*) poskrbijo za napačne vnose, na podlagi katerih omrežni promet steče proti njihovim strežnikom. Na teh lažnih naslovih strežnikov napadalci radi postavijo spletišča, ki so na videz skoraj identična originalnim, njihov namen pa je zavajanje uporabnikov v posredovanje nakazil, gesel ali drugih osebnih podatkov. Podobne učinke preusmerjanja prometa lahko izvedemo tudi na nižjih plasteh komunikacijskega modela, npr. z zastrupljanjem stikalnih tabel ali tabel ARP. Za odpravljanje opisane nevarnosti pri protokolu DNS lahko uporabimo razširitev DNSSEC (angl. *DNS Security Extensions*), ki omogoča digitalno podpisovanje zapisov, za katere je strežnik avtoritativen.


**BitTorrent**

Danes verjetno najbolj znan protokol P2P za deljenje datotek je protokol BitTorrent. Izmenjava datotek pri uporabi tega protokola poteka med gručo uporabnikov, med katerimi se prenašajo manjši kosi deljene datoteke, imenovani koščki (angl. *chunks*). Gruči uporabnikov, med katerimi poteka izmenjava koščkov datoteke, se lahko novi uporabniki pridružijo ob poljubnem času. Pridružitev novega uporabnika poteka tako, da se ta prijavi sledilnemu strežniku (angl. *tracker*), od katerega dobi seznam ostalih odjemalcev, ki tvorijo gručo za izmenjavo želene datoteke. Ker je seznam vseh odjemalcev v gruči lahko zelo velik in hkratno komuniciranje z njimi vpliva na performanse, odjemalec izbere le podmnožico vseh uporabnikov, imenovanih sosedi (angl. *neighbors*). Nadaljnja izmenjava koščkov datotek poteka le s temi sosedi.

Poleg podatkov, vsebujejo aplikacijska sporočila tudi dva kontrolna bita, ki opisujeta stanje povezave med odjemalcema: *zamašen* (angl. *choked*) in *zainteresiran* (angl. *interested*). Vsaka povezava je na začetku inicializirana v *zamašenem* in *nezainteresiranem* stanju, pretok podatkov pa se začne izvajati takrat, kadar je stanje prvega odjemalca *zainteresiran*, drugi odjemalec pa ni nastavil stanja *zamašen*, s čimer je razglasil, da bo odgovarjal na zahteve prvega. Nastavljanje statusa *zamašen* je pri protokolu BitTorrent koristno, ker za odjemanje datotek potrebujemo več različnih TCP povezav. V tem primeru nadzor zasičenja, ki je vgrajen v TCP, deluje ločeno in neusklajeno za vsako od posameznih povezav. Z uvedbo dodatnega nadzora zasičenja na aplikacijski plasti protokol BitTorrent to težavo odpravi.

Pri odjemanju razpoložljivih koščkov datotek lahko odjemalec pristopa k njihovemu prenosu z različnimi strategijami. Prenosa se sicer lahko loti v naključnem vrstnem redu, a bolj varna strategija je, da se loti najprej prenosa koščkov, ki so med sosedi najmanj prisotni (angl. *rarest first*). Na ta način si odjemalec lahko zagotovi bolj verjeten uspešen prenos celotne datoteke ob nevarnosti, da uporabniki z redkimi koščki predčasno zapustijo gručo. Med prejemanjem koščkov datotek je naloga odjemalca tudi, da svoje koščke deli z ostalimi uporabniki na enak način, kot je pridobil svoje koščke. Da protokol poskrbi za vzajemnost sodelovanja, odjemalec svoje koščke pošilja s hitrostjo, ki je sorazmerna hitrosti, s katero od njih koščke prejema.

Cilj vsakega odjemalca je torej, da sčasoma pridobi vse manjkajoče koščke datoteke. Ob zaključku prenosa k sebi lahko odjemalec še nekaj časa ostane v gruči in deli koščke z drugimi uporabniki, lahko pa tudi predčasno zapusti gručo in s tem morda odnese nerecipročno več podatkov, kot jih je poslal drugim. Iz tega razloga upravljavci nekaterih sledilnikov nadzorujejo razmerja med prejetim in poslanim prometom posameznih uporabnikov in od uporabnikov zahtevajo vrednosti teh razmerij, ki so še sprejemljiva.

**Skype**

Skype spada med najbolj znane aplikacije za telekonference, t.j. za prenos videa in govora. Aplikacija uporablja za komunikacijo **lastniški protokol**, katerega specifikacija pa ni javno objavljena. S skrivanjem specifikacije podjetje skriva svoje finančne interese, saj si z učinkovitim delovanjem aplikacije zagotavljajo konkurenčno prednost na trgu. Ne glede na zapisano pa so podrobnosti o delovanju protokola Skype že uspešno razvozlali uporabniki s postopkom **obratnega inženiringa**, ki jih je ob opazovanju omrežnega prometa pripeljal do smiselnih zaključkov o delovanju.

Ob zagonu aplikacije se uporabnik najprej poveže s strežnikom za prijavo, ki hrani uporabniška imena in gesla uporabnikov. Po uspešni avtentikaciji se odjemalec nato poveže do najbližjega **nadzornega vozlišča** (angl. *supernodes*), ki na nek način predstavlja vstopno točko v aplikacijsko “hrbtenico” aplikacije Skype. Nadzorna vozlišča imajo dve bistveni nalogi:

*   hranijo zapise, ki povezujejo **uporabniška imena** uporabnikov z njihovimi **omrežnimi naslovi IP**,
*   skrbijo za **vzpostavljanje povezave** med odjemalci.

Ker mora Skype zagotavljati povezljivost med poljubnimi uporabniki, se pri vzpostavitvi videokonferenčne zveze do uporabnika, ki je skrit za mehanizmom NAT, pojavijo težave. Te Skype rešuje na naslednji izviren in zanimiv način:

1.  Udeleženec A, ki želi vzpostaviti zvezo, obvesti o svojem interesu svoje nadzorno vozlišče NA. NA ta interes posreduje nadzornemu vozlišču NB ciljnega uporabnika B.
2.  Ob posredovanju interesa se v omrežju Skype izbere nadzorno vozlišče NR, ki bo igralo vlogo posrednika/premostitvenega vozlišča (angl. *relay*) pri povezavi.
3.  Uporabnika NA in NB se obvesti o naslovu posrednika NR in ju s tem povabi k vzpostavitvi povezave z njim. Ker sta oba uporabnika vzpostavila odhodno povezavo skozi svoj usmerjevalnik in s tem ta shrani njune naslove v tabeli NAT, lahko komunikacija med uporabnikoma nemoteno steče.
4.  Premostitveno vozlišče v nadaljevanju obvesti uporabnika A o javnem naslovu/vratih uporabnika B, preko katerem uspešno komunicira, in uporabnika B o naslovu/vratih uporabnika A. A in B lahko začneta od te točke naprej komunicirati neposredno, mimo premostitvenega vozlišča.