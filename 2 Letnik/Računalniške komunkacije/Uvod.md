Komponente omrežja se delijo na tri osnovne dele: **končne sisteme**, **jedro omrežja** in **komunikacijske povezave**.

**Končni sistemi**, imenovani tudi **gostitelji**, so naprave **na robu omrežja**, ki jih neposredno uporabljajo ljudje ali avtomatizirani procesi. Ti sistemi vključujejo **odjemalce**, kot so **osebni računalniki in pametni telefoni**, ter **strežnike**, ki zagotavljajo storitve. Te naprave predstavljajo vstopno in izstopno točko za vse podatke, ki potujejo skozi omrežno infrastrukturo.. V omrežje je povezanih med 15 in 20 milijard končnih sistemov. 

Podatki iz končnih sistemov potujejo v **jedro omrežja**, ki ga sestavlja preplet **usmerjevalnikov** paketov. Naloga jedra je **učinkovito usmerjanje podatkovnih paketov** od vira do cilja skozi zapleteno mrežo poti. Usmerjevalniki sprejemajo pakete na enem vmesniku in jih na podlagi naslovov posredujejo naprej proti končni destinaciji, kar omogoča komunikacijo med geografsko oddaljenimi sistemi.

Za **fizični prenos** teh podatkov skrbijo **komunikacijske povezave**, ki povezujejo končne sisteme z jedrom in usmerjevalnike med seboj. Te povezave so lahko **žične**, kjer se uporabljajo **bakreni kabli** ali **optična vlakna**, ali pa **brezžične**. Pri brezžičnih povezavah so ključne **dostopne točke** in **bazne postaje**, ki radijske signale pretvarjajo v obliko, primerno za nadaljnje pošiljanje po fizičnih vodnikih. Izbira medija določa hitrost in zanesljivost prenosa podatkov.

Vse te komponente so povezane v hierarhično strukturo, ki tvori celoten internet. Domača omrežja, mobilna omrežja in omrežja podjetij se povezujejo na lokalne ponudnike internetnih storitev. Ti lokalni ponudniki so nato povezani z večjimi regionalnimi ali globalnimi ponudniki, kar omogoča, da se podatek iz lokalnega omrežja prenese v poljubno drugo omrežje na svetu.
*Različni tipi omrežij se preko ponudnikov internetnih storitev povezujejo v enotno globalno infrastrukturo.*

Končne sisteme v omrežju ločimo glede na storitve. V modelu **odjemalec-strežnik** so **odjemalci** tisti, ki **pošiljajo zahteve**, **strežniki** pa so zmogljivejše naprave, ki na te zahteve **odgovarjajo s posredovanjem informacij**. V mešanem načinu, imenovanem **P2P** (Peer-to-Peer), pa se meje med temi vlogami brišejo, saj vsaka sodelujoča naprava deluje **hkrati kot odjemalec in strežnik**, kar omogoča neposredno izmenjavo med udeleženci brez centralne točke.

Da do omrežja lahko dostopamo - povezava med končnim sistemom in robnim usmerjevalnikom - potrebujemo neko tehnologijo. Poznamo več načinov:

1. Modemski oz. klicni dostop *Dial up*
	- Uporablja **modem za pretvorbo digitalnih podatkov v analogne signale** ki potujejo po govornem pasu telefonskega omrežja.
	- Hitrost potovanja podatkov je **$\sim$ 56 kbps**
	- Glavna težava je da je telefonska linija med uporabo interneta zasedena; ni mogoče hkrati biti povezan do interneta in telefonirati.
	  
		*Modem je v tem primeru naprava ki izhodiščno služi za pretvorbo glasu v valovanje. Za delovanje z biti mora **modulirati** bite na zvočni val - to pomeni da spremnija frekvenco, amplitudo ali fazo kjer spremembe ene od teh predstavlja neko število bitov informacij in ko ti pridejo do cilja jih tudi demodulira. Poznamo več sistemov nek osnovni sistem je predsavljanje 1 in 0 z visoko in nizko frekvenco ampak nek napredni sistem je kombiniranje amplitude in faze signala. Po žici lahko pošljemo 2 sinusna signala z isto frekvenco brez da bi se zmešala če sta fazno zamaknjena za $\frac{\pi}{2}$, prvi je in-phase - standardni sinusni val drugi je kvadratura oz. kosinusni val zamaknjen za $\frac{\pi}{2}$. Dobimo $S(t) = I \sin\,\! (2 \pi f t) + Q \cos\,\! (2 \pi f t) kjer je $I$ amplituda sinusa in $Q$ amplituda kosinusa. Vsak od njiju lahko zvazame 4 nivoje amplitude - $-3,-1,1,3$ torej $4^{2}$ možnih kombinacij kjer vsaka ustreza 4-bitni kodi. *
2. DSL *Digital subscriber line*
	   - Isto uporablja telefonsko linijo vendar na višjih frekvencah kot glas kar omogoča sočasno uporabo telefona in interneta s pomočjo razdelilnika *splitterja* ki razdeli frekvenčni pas.
	   - 0-4 kHz : rezervirano za telefon
	   - 4-50 kHz : za odhodni promet *upstream*
	   - 50 kHz - 1 Mhz : za vhodni promet *downstream*
	- Ponavadi je asimetričen - upstream in downstream nista isto hitra, dosegajo pa ponavadi **$\sim$ 100 Mbps**
3. Kabelski dostop
	- Podatki in TV signali se prenašajo po istem kablu na različnih frekvenčnih kanalih, potrebujemo **kabelski modem**.
	- **Medij je deljen** več hiš je lahko na isti povezavi do skupnega volzišča kar ob visoki obremenitvi pomeni da hitrost pade.
	- Hitrosti so asimetrične **$\sim$ 120 Mbps** za downstream, **$\sim$ 10 Mbps** upstream.
4. Optični dostop oz. FTTH *Fiber to the home*
	- Uporablja se optično vlkano so uporabnika - podatki potujejo v obliki svetlobnih impulzov.
	- Zagotavlaj visoke in stavilne hitrosti od 100 Mbps do 1 Gbps in več.
5. Ethernet
	- Najpogostejša v javnih zavodih, univarzah in podjetjih
	- Povezava preko Ethernet stikal - *switchev*
	- Ethernet je prialgodljiv in omogoča običajne hitrosti $\sim$ 100 Mbps - 1Gbps medtem ko lahko v nekaterih omrežjih dosegajo tudi do $\sim$ 800 Gbps.
6. Wifi
	   - Deljen in neusmerjen medij - naprave si delijo zračni prostor, signal se širi v vse smeri
	   - Več standardov z razločnimi hitrostmi
		   - 802.11b/g - starejši $\sim$ 11-54 Mbps
		   - 802.11n/ac/ax (Wifi 4, 5, 6) - sodobni standardi od 600 Mbps do 10 Gbps
		   - 802.11be (Wifi 7) - prihajajoča generacija s teoretičnimi hitrostmi $\sim$ 40 Gbps
7. 3G/4G/LTE/5G
    *   uporaba central mobilnih operaterjev - narpava se poveže s baznimi postajami / radijskimi stolpi in jih pošlje k centrali preko katere se odstopa do interneta.
    *   ~2 Mbps (3G), 50 Mbps – 300 Mbps (4G)
    *   5G (100 Mbps – 2 Gbps)
    *   6G (v raziskavah, pričakovano ~2030)

**Jedro omrežja** je mreža povezanih usmerjevalnikov kjer imamo komunkacijo na povezan in nepovezan način.

**Povezan način** *circuit swithcing* je namenska povezava za vsak prenos. Ko hočemo komunicirati z neko napravao se rezervira pot samo za naju. Poiščejo se prosti kabli instikala in po njih se pošiljajo podatki.

Postane neučinkovito če med komunikacijo ne potrebujemo 100% dostopa - kar pri internetu ki deluje v "sunkih" ni idealno.

**Nepovezan način** *packet switching* pa temelji na razbijanju podatkov na pakete kjer ima vsak svojega prejemnika in paketi potujejo medsebojno neodvisno torej gre nek lahko po drugi poti kot drug na cilju pa se sestavijo nazaj v pravilnem vrstnem redu.

Omrežje ni "zasedeno" samo z enim uporabnikom in se na istem kablu lahko hkrati prepletajo paketi več naprav.

Hkrati je zagotovljena boljša odpornost saj ob izpadu nekje lahko najdemo pot drugje.

**Protokol** je nabor pravil in postopkov ki določajo format oz. sintakso podatkov, časovni razpored oz. vse korake vzpostavljanja, vzdrževanja in konca komunikacije in način obdelave sporočil med enotami ki komunicirajo.

Format je sintaksa podatka oz. kje je kateri del podatka, semantika je sporočila - npr. zahteva po datoteki, časovni razpored pa določa v kakšnem vrstnem redu si moraj onaprave pošiljati sporočila - npr. najprej sinhornizacija povezave, nato prenos podatkov.

Komunikacija je razdeljena na različne ravni. Na **"višjem nivoju"** najdemo protokole, ki so blizu uporabniku in aplikacijam, kot so HTTP (za splet), SMTP/POP3 (za e-pošto) in BitTorrent (za prenos datotek). Ti določajo, kaj se prenaša. Da pa ti podatki dejansko pridejo do cilja, potrebujejo **"nižjenivojske"** protokole. Ti skrbijo za tehnično ozadje: kako se podatki spremenijo v zaporedje bitov, kako preprečiti zastoje v omrežju (kontrola zasičenja) in po kateri poti bodo paketi potovali.

Protokoli so organizirani **hierarhično**; **višji nivoji skrbijo za vsebino in storitve**, **nižji pa za zanesljiv in učinkovit prenos podatkov po fizični infrastrukturi.**

Da bi bila komunikacija med dvema napravama uspešna, morata obe natančno vedeti, v kateri fazi postopka se nahajata. 

Protokol ni le seznam pravil, temveč **stroj stanja**: začne se s potrebo po povezavi, nadaljuje z zahtevo in konča s prejemom podatkov. 

Če gre karkoli narobe (npr. napaka 401 za avtorizacijo ali preusmeritev), protokol natančno določa naslednji korak, da se sistem ne sesuje, temveč napako predvidljivo obravnava.

**Delujejo kot logična zaporedja, ki zagotavljajo, da se naprave vedno "razumejo" glede tega, kaj sledi.**

Ker v internetu sodelujejo naprave različnih proizvajalcev, in da bi zagotovili **splošno uporabnost**, morajo biti protokoli **standardizirani**. Glavno vlogo tukaj igra organizacija **IETF** (Internet Engineering Task Force). Standarde objavljajo v obliki dokumentov **RFC** (Request For Comments). Obstaja že več kot 9500 dokumentov, ki natančno opisujejo delovanje interneta. Poleg IETF za specifične strojne standarde (kot je npr. Wi-Fi ali Ethernet) skrbijo druge organizacije, kot je **IEEE** (npr. standardi serije 802).

**Omrežne plasti**

Kompleksni komunikacijski sistemi so razdeljeni na plasti, da postanejo preglednejši in lažje obvladljivi.

Vsaka plast v sistemu ima svoja specifična pravila (protokole), ki zagotavljajo, da se storitev, začeta na eni strani, pravilno zaključi na drugi.

V omrežnem skladu višja plast (npr. aplikacija) zahteva storitev od plasti neposredno pod njo. Nižja plast to storitev izvede in po potrebi zaprosi še nižjo plast. Takšna **sistematična zasnova** omogoča, da lahko del sistema (posamezno plast) zamenjamo ali posodobimo, ne da bi pri tem vplivali na ostale dele.

 Plasti so **medsebojno** **neodvisne**; sprememba implementacije v eni plasti ne zahteva sprememb v drugih, kar omogoča **fleksibilnost** in razvoj sistema.
 
**ISO/OSI model**

Opisane koncepte združuje **ISO/OSI model**, ki je mednarodni standard za komunikacijo v omrežjih. Ta model definira natanko **7 plasti**. Vsaka plast nudi storitev plasti nad njo in s pomočjo protokolov komunicira s plastjo na drugem sistemu. 

Začnemo na **fizični plasti**, kjer se podatki prenašajo kot biti po kablih ali zraku. 

**Povezavna plast** te bite zapakira v "okvirje" in poskrbi, da se sosednji napravi v omrežju razumeta brez napak. 

**Omrežna plast**, z usmerjanjem (routingom) določi pot paketom po internetu.

**Transportna plast** poskrbi, da ti podatki na cilj pridejo zanesljivo in v pravilnem vrstnem redu. 

Višje plasti (**sejna, predstavitvena in aplikacijska**) pa se ukvarjajo z logiko povezave, formatom podatkov (npr. šifriranje) in končnimi storitvami, ki jih uporablja uporabnik (npr. HTTP za splet)

Čeprav je ISO/OSI model odličen za učenje in razumevanje teorije, današnji internet v praksi temelji na modelu **TCP/IP**. 

Ta model je bolj pragmatičen in združuje nekatere plasti OSI modela, da bi bil proces hitrejši in manj kompleksen. 

Na primer, zgornje tri plasti OSI modela (aplikacijska, predstavitvena in sejna) so v TCP/IP združene v eno samo **aplikacijsko plast**. Prav tako sta spodnji dve plasti (fizična in povezavna) v TCP/IP modelu pogosto obravnavani skupaj kot **omrežni vmesnik**. Transportna in omrežna (Internet) plast pa ostaneta ločeni, saj sta ključni za delovanje IP naslovov in prenosa podatkov.

Razlika med obema modeloma ni le v številu plasti, temveč v njunem izvoru in uporabi. ISO/OSI model velja za **"de iure"** standard (po zakonu oziroma uradni standard), kar pomeni, da je bil načrtovan teoretično in sistematično kot popoln model. Vendar pa se je v praksi uveljavil TCP/IP kot **"de facto"** standard (v dejanski rabi). TCP/IP je bil bolj prilagodljiv, fleksibilen in ker so bile njegove implementacije na voljo hitreje kot pri kompleksnem OSI modelu. Danes tako uporabljamo OSI model predvsem kot referenco za učenje, medtem ko vsi naši izdelki (usmerjevalniki, računalniki, telefoni) dejansko uporabljajo TCP/IP.