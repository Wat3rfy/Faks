 ### Fizična plast

Fizična plast predstavlja najnižji nivo v komunikacijskem modelu in je odgovorna za dejanski prenos surovih podatkov med napravama. 

**Kodiranje bitov v fizične signale**
Prvi korak v je transformacija logične enote v fizikalni signal, ki ustreza mediju. Če uporabljamo bakrene kable, se biti kodirajo v električno napetost; pri optičnih vlaknih se spremenijo v svetlobne impulze; pri brezžičnih povezavah pa v radijske valove ali infrardečo svetlobo (IR).

**Prenos posameznih bitov**
Ko je bit enkrat kodiran, se mora zgoditi **prenos podatkov**. To se lahko zgodi na dva načina: digitalno, kjer signal skače med diskretnimi stanji (npr. visoka in nizka napetost), ali analogno, kjer se podatki prenašajo s spreminjanjem lastnosti zveznega valovanja (amplituda, frekvenca).

**Prenos celotnega zaporedja bitov**
Ker podatki v omrežju nikoli ne potujejo kot osamljeni biti, temveč kot dolgi nizi informacij, fizična plast skrbi za usklajen prenos celotnega zaporedja. Vhodni niz "10110..." se na poti skozi medij spremeni v neprekinjen valovni signal. 

Da bi sprejemnik vedel, kje se en bit konča in kje se začne drugi, morata biti obe napravi usklajeni v istem ritmu (takta). Če bi oddajnik pošiljal bite hitreje, kot jih sprejemnik bere, bi se zaporedje "porušilo" – sprejemnik bi morda prebral dve enici namesto ene ali obratno. Prenos celotnega zaporedja torej zahteva vzdrževanje časovne sinhornizacije med obema stranema skozi celoten proces.
Zaradi upora in motenj iz okolja postaja signal vse šibkejši in popačen. Kljub tem motnjam se mora ohraniti oblika signala, tako da se na koncu še vedno razbere pravilno zaporedje bitov.

Na koncu se ponovno pretvori v digitalno zaporedje, kar pomeni, da mora naprava na drugi strani znati "prebrati" valovanje in ga natančno prevesti nazaj v identičen niz ničel in enic, kot je bil poslan. Šele ko sprejemnik potrdi, da je prejel celoten niz brez napak, je naloga fizične plasti pri prenosu zaporedja končana.

**Pretvorba signala v obliko primerno za medij**
Vsak prenosni medij ima svoje fizikalne omejitve, kot sta slabljenje signala ali dovzetnost za elektromagnetne motnje. Zadnja ključna naloga fizične plasti je prilagoditev (modulacija) signala tako, da je čim bolj učinkovit za specifičen medij. To pomeni, da bo signal za prenos po kilometrih optičnega kabla oblikovan drugače kot signal za kratko razdaljo preko Bluetooth povezave, vse z namenom, da se na koncu (kot kaže desni del slike) signal spet pravilno dekodira nazaj v prvotne bite.


***

**Prenosni sistem**

...združuje komponente **fizične  in povezavne plasti** torej je skupek vse strojne in programske opreme ki omogoča da podatki lahko potujejo med dvema točkama.

**Prenosni medij**

...je fizična snov ali okolje, ki omogoča širjenje določene vrste valovanja. Za električne signale so to bakrene žice, za svetlobo optična vlakna, za brezžično komunikacijo pa prosti prostor (zrak oz. vakuum), po katerem potujejo radijski valovi ali infrardeča svetloba.

**Prenosni kanal**

Prenosni sistem uporablja medij tako, da na njem vzpostavi **prenosni kanal**. Kanal je specifičen del ali način uporabe medija, ki je rezerviran za prenos določenega zaporedja bitov. Naprava preko kanala pošilja okvirje bitov od točke A do točke B.

Ko je kanal vzpostavljen, moramo določiti, kako se bodo podatki po njem gibali glede na **smer**.

- **Enosmeren (Simplex):** Podatki tečejo le v eno smer (npr. televizijski oddajnik proti sprejemniku).
- **Izmenično dvosmeren (Half-Duplex):** Obe strani lahko pošiljata, vendar ne hkrati (npr. voki-toki).
- **Sočasno dvosmeren (Full-Duplex):** Obe strani lahko hkrati pošiljata in sprejemata podatke (npr. sodoben Ethernet ali telefon).

Biti lahko **vstopajo v kanal** na različne načine

- **Serijski prenos:** Biti potujejo eden za drugim po eni sami poti. To je standard za večino sodobnih omrežnih povezav na dolge razdalje.
    
- **Paralelni (vzporedni) prenos:** Več bitov potuje hkrati po več vzporednih poteh (npr. znotraj računalniškega vodila). Je hitrejši na kratke razdalje, a težaven za sinhronizacijo na dolge razdalje.

Razlikujemo tudi kanale po **številu vključenih naprav**

- **Dvotočkovni (Point-to-Point):** Kanal neposredno povezuje le dve napravi (npr. dve stikali med seboj).
    
- **Skupinski (Multipoint):** En kanal si deli več naprav hkrati. V tem primeru mora sistem paziti, da naprave ne govorijo hkrati in ne povzročajo zmešnjave (npr. Wi-Fi dostopna točka s številnimi uporabniki).


**Prenosni mediji**

Različni mediji imajo različne lastnosti. Izbira določa **hitrost prenosa**, **največjo razdaljo**, na kateri je signal še uporaben, ter **odpornost na zunanje motnje**.

1. Eden najpogosteje uporabljenih v lokalnih omrežjih je **zvita parica**, pri čemer se najpogosteje uporablja neokrepljena različica, znana kot **UTP** **(unshielded twisted pair)**. Medij sestavljata dve vzporedni bakreni žici, od katerih je vsaka obdana s svojo izolacijsko plastjo.

	Žici sta med seboj zviti v vijačnico, kar služi zmanjševanju elektromagnetnih interferenc in presluha, do katerega pride, ko signali iz sosednjih parov žic znotraj istega kabla vplivajo drug na drugega. Z zvijanjem se elektromagnetna polja, ki jih ustvarjata žici, medsebojno delno izničijo, kar ohranja čistost signala. V današnjih lokalnih omrežjih (LAN) UTP kabli omogočajo visoke hitrosti prenosa do **10 Gbps**, vendar so te hitrosti omejene na krajše razdalje, običajno do 100 metrov, ker se električni signal z oddaljenostjo od vira oslabi.
	<br>

2. Kadar so zahteve po zaščiti signala pred zunanjimi vplivi večje, se uporabi **koaksialni kabel**, ki ima bistveno drugačno zgradbo kot zvita parica. Njegova konstrukcija je koncentrična: v samem središču se nahaja osrednji bakreni vodnik, ki prenaša podatkovni signal. Tega obdaja plast dielektrične izolacije, okoli katere je nameščen drugi vodnik, običajno v obliki kovinske mrežice ali folije. Celoten sklop je na koncu zaščiten s trpežno zunanjo izolacijsko plastjo.

	Takšna večplastna sestava zagotavlja visoko stopnjo odpornosti proti zunanjim motnjam. Zunanji prevodni sloj deluje kot elektromagnetni ščit, ki preprečuje, da bi šumi iz okolice prodrli do notranjega vodnika, hkrati pa preprečuje uhajanje oziroma sevanje signala iz kabla v okolico. Zaradi te zaščite koaksialni kabli ohranjajo integriteto signala tudi v okoljih z veliko elektromagnetnega šuma. Čeprav podpirajo nekoliko nižje najvišje hitrosti v primerjavi z najnaprednejšimi sistemi zvitih paric (običajno do **2 Gbps**), njihova robustnost omogoča stabilno delovanje v večjih distribucijskih sistemih, kot so kabelska omrežja.

Zvita parica dosega višje hitrosti z uporabo večkratnih vzporednih komunikacijskih poti (štirje pari žic), medtem ko je koaksialni kabel omejen na en sam signalni vodnik.

**Optični kabel**

Optična vlakna so izdelana iz izjemno **čistega stekla ali plastike**. Zaradi svoje sestave so vlakna mehansko občutljiva na močne upogibe in pritiske. Postopek spajanja dveh vlaken je tehnološko zahteven, saj zahteva mikroskopsko natančno poravnavo jeder, da ne pride do izgube svetlobe.  To predstavlja varnostno prednost; prisluškovanje na optičnih kablih je veliko težje saj vsak poseg v strukturo vlakna povzroči merljiv padec moči signala ali njegovo prekinitev.

Svetloba v potuje z **minimalnimi izgubami energije**, kar omogoča prenos podatkov na **velike razdalje**. Signali lahko prepotujejo do 100 kilometrov brez pomoči. Poleg velikega dosega optična vlakna ponujajo izjemno široko pasovno širino, kar omogoča hitrosti prenosa podatkov, ki dosegajo več terabitov na sekundo (Tbps).

Učinkovitost se poveča z uporabo tehnologije **WDM (Wavelength Division Multiplexing)** oziroma valovnega multipleksiranja. Ta tehnika izkorišča dejstvo, da lahko po istem vlaknu hkrati potuje več svetlobnih žarkov različnih frekvenc, ne da bi drug na drugega vplivali. Z uporabo različnih valovnih dolžin (ki jih lahko razumemo kot različne barve svetlobe) je mogoče po enem samem fizičnem vlaknu vzpostaviti več neodvisnih komunikacijskih kanalov. To drastično poveča skupno prenosno kapaciteto obstoječe infrastrukture brez potrebe po polaganju dodatnih kablov.

Zaradi začetnih visokih stroškov proizvodnje in zahtevne opreme so bila optična vlakna sprva rezervirana izključno za hrbtenice omrežij, ki povezujejo večja vozlišča, mesta in kontinente. Z napredkom tehnologije in optimizacijo proizvodnih procesov pa se je optika začela širiti neposredno do končnih uporabnikov. Danes je uveljavljen standard FTTH (Fiber to the Home), kjer optični kabel sega v stanovanjske objekte in omogča večje hitrosti širši javnosti.

**Brezžični mediji**
  
Brezžični prenosni mediji omogočajo prenos podatkov z uporabo elektromagnetnega valovanja skozi zrak, kar odpravlja potrebo po fizičnih vodnikih med napravami.

Radijske povezave delujejo v širokem frekvenčnem spektru in se običajno širijo v vseh smereh, kar omogoča hkratno povezovanje več naprav. Ta tehnologija tvori osnovo za lokalna brezžična omrežja (WLAN), osebna omrežja za povezovanje naprav na kratki razdalji (Bluetooth) ter široka mobilna omrežja za telefonijo in prenos podatkov (GSM).

Mikrovalovne povezave uporabljajo višje frekvence in so za razliko od radijskih valov strogo usmerjene. Zaradi te lastnosti zahtevajo neposredno vidno linijo med oddajnikom in sprejemnikom, kar se pogosto uporablja za vzpostavljanje fiksnih točkovnih povezav na večjih razdaljah, kjer polaganje kablov ni izvedljivo.

Infrardeča (IR) svetloba predstavlja spekter s še višjo frekvenco, ki se uporablja za komunikacijo na zelo majhnih razdaljah. Ker ti valovi ne morejo prehajati skozi trdne ovire, kot so stene, je njihova uporaba omejena na zaprte prostore, kar srečamo pri daljinskih upravljalnikih in nekaterih oblikah neposrednega prenosa med napravami.

Satelitske povezave delujejo kot ojačevalniki v zemljini orbiti, ki sprejemajo signale s tal in jih posredujejo nazaj na druge lokacije na Zemlji. To omogoča komunikacijo na ekstremno velike razdalje in pokrivanje odročnih predelov, kar vključuje globalne sisteme za dostop do interneta (Starlink), satelitsko telefonijo (Iridium, Thuraya) ter sisteme za globalno pozicioniranje in navigacijo (GPS, Galileo).

***

**Frekvenčna karakteristika** določa spekter frekvenc, ki jih določen prenosni medij lahko učinkovito prenese od oddajnika do sprejemnika. Različne vrste informacij zahtevajo različne frekvenčne razpone; človeški govor za razumljivost potrebuje razpon med 300 in 7000 Hz, medtem ko standardni telefonski kanali zaradi tehničnih omejitev delujejo v ožjem pasu med 500 in 3600 Hz. Visokokakovostna Hi-fi oprema pa mora pokrivati celoten slišni spekter človeškega ušesa, običajno od 100 do 20.000 Hz, da zagotovi verno reprodukcijo zvoka.


Med prenosom signala skozi poljuben medij pride do neizogibnih sprememb njegove prvotne oblike, kar je posledica fizikalnih lastnosti medija in zunanjih vplivov. Te spremembe neposredno vplivajo na kakovost in berljivost podatkov na sprejemni strani, saj originalni signal med potovanjem postopoma izgublja svojo integriteto.


Slabljenje ali atenuacija se kaže kot zmanjšanje amplitude oziroma moči signala z naraščanjem razdalje od oddajnika. Ker se energija signala med potovanjem skozi medij izgublja zaradi upornosti ali drugih fizikalnih dejavnikov, postaja signal vse šibkejši, kar zahteva uporabo ojačevalnikov pri prenosih na dolge razdalje.


Popačenje nastane, ko se geometrijska oblika signala spremeni zaradi različnega odziva medija na različne frekvenčne komponente znotraj istega signala. To povzroči, da sprejeti signal na cilju ni več identičen originalu po obliki, kar lahko vodi do napak pri interpretaciji digitalnih simbolov ali izgube čistosti pri analognem prenosu.


Šum predstavlja nezaželene, naključne električne ali elektromagnetne signale, ki se med prenosom pomešajo z originalnim signalom. Ti vplivi prihajajo iz okolja ali same strojne opreme in vnašajo nepravilnosti v valovanje, kar ob previsoki stopnji šuma popolnoma prekrije koristno informacijo in prepreči njeno pravilno razumevanje na sprejemni strani.

***

**Modulacija**

Modulacija je tehnični postopek analognega kodiranja digitalnega signala, ki omogoča prenos binarnih podatkov preko medijev, zasnovanih za analogna valovanja. Pri tem procesu se določen parameter nosilnega sinusnega valovanja spreminja v skladu z vrednostmi digitalnega signala, kar omogoča prenos informacij na daljavo.

*Povzetek: Modulacija je proces prilagajanja nosilnega valovanja za prenos digitalnih podatkov v analogni obliki.*

**Amplitudna modulacija (AM)**

Pri amplitudni modulaciji se informacijska vsebina zapiše s spreminjanjem amplitude oziroma višine nosilnega valovanja. Logična enica je predstavljena z visoko amplitudo, kar v zvočnem spektru ustreza glasnemu pisku, medtem ko logično ničlo predstavlja nizka ali ničelna amplituda, kar ustreza tišini. Frekvenca in faza valovanja pri tem ostaneta nespremenjeni.

*Povzetek: Amplitudna modulacija kodira podatke s spreminjanjem jakosti oziroma višine valov.*

**Frekvenčna modulacija (FM)**

Frekvenčna modulacija temelji na spreminjanju števila nihajev v časovni enoti, medtem ko amplituda valovanja ostaja konstantna. Logično enico predstavlja višja frekvenca, kjer so valovi gostejši, kar bi pri zvoku zaznali kot visok pisk. Logična ničla je kodirana z nižjo frekvenco oziroma redkejšim valovanjem, kar ustreza nizkemu pisku.

*Povzetek: Frekvenčna modulacija prenaša informacije s spreminjanjem gostote nihajev nosilnega signala.*

**Fazna modulacija (PM)**

Fazna modulacija uporablja premik v fazi nosilnega valovanja za ponazoritev spremembe signala. Vsak premik faze za določen kot, na primer za 180 ali 90 stopinj, pomeni spremembo binarnega stanja. Pri 180-stopinjskem premiku se valovanje trenutno obrne v nasprotno smer, kar sprejemnik prepozna kot kodirano informacijo, pri čemer frekvenca in amplituda valovanja ostajata enaki.

*Povzetek: Fazna modulacija kodira podatke s trenutnimi spremembami v položaju valovnega cikla.*

***
Kvadratna modulacija predstavlja napredno metodo v digitalnih komunikacijah, ki za prenos informacij hkrati izkorišča dve temeljni lastnosti valovanja: amplitudo in fazo. Namesto da bi se zanašala le na en parameter, ta tehnika združuje obe vrsti modulacije, s čimer ustvari bolj kompleksen in informacijsko bogat nosilni signal.
**Povzetek: Kvadratna modulacija združuje amplitudno in fazno modulacijo za prenos podatkov.**

V procesu kvadratne modulacije se uporablja več nivojev amplitude, kar pomeni, da višina vala ni omejena le na dve stanji. Različne jakosti signala omogočajo razlikovanje med več različnimi stanji znotraj istega osnovnega valovanja, kar povečuje količino podatkov, ki jih signal lahko nosi.
**Povzetek: Uporaba več nivojev amplitude omogoča kodiranje dodatnih informacij.**

Sistem poleg amplitude vključuje štiri natančno določene fazne kote, ki so 0, 90, 180 in 270 stopinj. Ti koti določajo, v kateri točki cikla se začne valovanje, kar ob upoštevanju prej omenjenih različnih amplitud še dodatno razširi nabor možnih unikatnih kombinacij za kodiranje podatkov.
**Povzetek: Štirje fazni koti omogočajo natančno določanje začetka valovanja za večjo variabilnost.**

Združevanje teh dveh parametrov vodi do visoke učinkovitosti prenosa, saj posamezna sprememba signala ne predstavlja le enega bita, temveč celo skupino podatkov. V praktični uporabi lahko ena kombinacija določene amplitude in faze hkrati označi skupino od 3 do 6 bitov, kar bistveno poveča hitrost prenosa informacij prek razpoložljive pasovne širine.
**Povzetek: Posamezna sprememba signala lahko v praksi predstavlja skupino od 3 do 6 bitov.**

Konstelacijski diagram služi kot grafični prikaz vseh možnih stanj moduliranega signala v določenem časovnem trenutku. Na tem diagramu so posamezne točke razporejene glede na njihove fizikalne lastnosti, kar omogoča vizualizacijo načina, kako se digitalni podatki pretvorijo v valovne spremembe.
**Povzetek: Konstelacijski diagram grafično prikazuje stanja moduliranega signala.**

Položaj točke na diagramu je določen z dvema parametroma: kotom in razdaljo od središča. Fazni koti (0°, 90°, 180° in 270°) določajo smer, v katero je točka postavljena na koordinatnem sistemu, medtem ko razdalja od središča predstavlja nivo amplitude. Točke, ki so bližje središču, ustrezajo nizki amplitudi, točke na zunanjem robu pa visoki amplitudi.
**Povzetek: Kot na diagramu predstavlja fazo, razdalja od središča pa nivo amplitude.**

Z združevanjem štirih faznih kotov in dveh nivojev amplitude dobimo skupno osem unikatnih stanj signala. Vsako izmed teh stanj je v tabeli neposredno povezano s specifično kodirano vrednostjo, sestavljeno iz treh bitov. To pomeni, da določena kombinacija faznega zamika in moči signala vedno predstavlja točno določen niz ničel in enic, kot je razvidno iz vrednosti od 000 do 111.
**Povzetek: Kombinacija faz in amplitud omogoča kodiranje osmih različnih 3-bitnih vrednosti.**

Takšna ureditev omogoča, da se z eno samo spremembo lastnosti signala prenese več bitov hkrati, kar poveča podatkovno prepustnost komunikacijskega kanala. Sprejemnik na podlagi zaznanega kota in amplitude signala točno določi, katera bitna kombinacija je bila poslana, kar zagotavlja učinkovito pretvorbo fizičnega valovanja nazaj v digitalne podatke.
**Povzetek: Prenos več bitov z enim simbolom povečuje hitrost in učinkovitost digitalne komunikacije.**