**Masovni podatki**, velika količina zapletenih in raznolikih vrst podatkov.

Te ponavadi zaznamuje **ogromna količina** v peta ali eksabajtih, **raznolikost** podatkov oz. različne oblike zmešane skupaj - tekst, slike, senzorski podatki,... nazadnje pa še **hitrost dostopa** do podatkov, kjer ponavadi zahtevamo takojšnjo dostopnost podatkov. 

Količina bo zahtevala vzporedno procesiranje, raznolikost bo zahtevala odpornost na različne formate, hitrost pa hitro procesiranje.

Poleg tega lahko zahtevamo še zelo **natančno shranjevanje** oz. ne smemo izgubljati informacij in preverjanje **koristnosti** informacij.


**Razširljivost (Scalability)** oz. sposobnost sistema da ga lahko prilagodimo večjemu številu podatkov. To ponavadi pomeni da mu **dodamo vire** kot so procesorji, pomnilnik, več strežnikov,... **in hkrati vzdržujemo zmogljivost sorazmerno s količino virov.** 

Če je zahteva na strežniku težja se mu dodeli več virov - uporabnik ne bi smel občutiti razlike.

**Linearna razširljivost** je ideal, kjer podvojitev števila strežnikov pomeni natanko podvojitev procesne moči in ohranjanje časovne zahtevnosti. Drugače povedano če podvojimo vire ob isti količini informacij se mora čas procesiranja razpoliviti.

Ločimo **vertikalno razširljivost** z dodajanjem virov na nek stroj in **horizontalno** z dodajanjem novih vozlišč / strojev v mrežo.



**Relacijske podatkovne baze** so zanesljive. Delujejo po sistemu ACID:
- Atomicity - stransakcija se izvede ali pa ne, če se zgodi napaka se celoten postopek razveljavi in baza se ne spremeni
- Consistency - baza mora ostati v veljavnem stanju po vsaki transakciji
- Isolation - Če se izvaja več transakcij hkrati ena ne sme motiti druge. Vsaka se obnaša kot da je edina v sistemu
- Durability - Ko je transakcija potrjena so podatki trajno shranjeni - tudi če zmanjka elektrike ali se strežnik sesuje bodo podatki še vedno tam.

Za upravljanje z relacijskimi bazami se uporablja SQL ki je precej enostaven, omogoča povezovanje podatkov različnih tabel, deluje deklarativno, kjer povemo le kaj hočemo in ne rabimo pimplementirati logike pridobitve.

Relacijske baze pa so bile zgrajene za delovanje na enem samem močnem strežniku (vertikalno skaliranje).

Zaradi zagtoavljanja ACID

Uporabljajo strukturiran jezik SQL in so primarno optimizirane za shranjevanje podatkov na enem močnem strežniku.

Določen je s strogimi strukturami in potreben je dober plan. Preden vstalvjamo podatke moramo definirati shemo, kar omogča red ampak otežuje hitre spremembe.

**Ker so relacijske baze osnovane na ACID je težko horizontalno skaliranje, ker bi rabili biti vsi strežniki usklajeni kar bi upočasnjevalo sistem.**
***
**NoSQL podatkovne baze** so nastale kot odgovor.

Deluejo tako da povežejo na tisoče običajnih računalnikov skupaj.
S tem tudi zmanjšamo možnost odpovedi saj ob izpadu vozlišč lahko delo preusmerimo na druga vozlišča.

Ponavadi deluje brez podatkovne sheme - *schema on read* - v bazo hranimo poljubno strukturo *npr. json* ta pa se interpretira šeče takrat ko podatke beremo - *schema on read* - kar omogoča fleksibilnost.

Optimizirane so za spletne storitve kjer je veliko zapisov in branj naenkrat.

Večina jih uporablja svoj jezik.

Temelji na **fragmentaciji in replikaciji**. Podakte razbijemo na manjše dele in jih razpršimo po različnih strežnikih - *npr. uporabniki od A do N na enem in od N do Ž na drugem* - vsakega pa shranimo na različnih strežnikih hkrati - če se en sesuje so podatki še vedno varni.

V takih sistemih težko zagotavljamo ACID ker komunikacija med strežniki traja.

ACID je žrtvovan za hitrost in razpoložljivost - govorimo o CAP izreku - hkrati lahko zagotovimo dve od treh lastnosti
- Consistency - Vsa vozlišča vidijo iste podatke ob istem času
- Availability - Vsaka zahteva prejme odgovor - uspeh / napaka
- Partition tolerance - Sistem deluje tudi če se mreža med strežniki prekine

*V praksi vedno izbermeo P in nato izbiramo med C in A.*

Večina NoSQL baz uporablja postopno konsistentnost - namesto da bi vsi strežniki takoj imeli istipodatek, zagotavljamo da se bo podatek razžiril na vse strežnike čez čas - običajno nekaj milisekund.

**Relacijski uporabljamo za strukturirane podatke in 100% natančnost, NoSQL in porazdeljene pa za sisteme ki obdeluejjo ogormne količine podatkov, ki morajo biti vedno na voljo in omogočajo fleksibilnost..**

Ker morajo baze imeti možnost da se razširjajo po količini bralnih operacij - vedno več uporabnikov ki zahteva branje podatkov, številu pisalnih operacij - vedno več novih podatkov, velikosti podatkovne baze - presežena kapaciteta strežnika.

Kot rešitev uporabljamo **replikacijo** - ker imamo več kopij istih podatkov lahko bralne zahteve razporedimo med več strežnikov, *load balancer* poskrbi da noben strežnik ni preobremenjen, če en strežnik odpove, sistem deluje naprej, delo prevzamejo druga vozlišča z istimi podatki.

Glavni problem je sinhronizacija - pisanje postane počasnejše in kompleksnejše - lahko uporabljamo sinhrono pisanje in uporabnik dobi potreditev šele ko so potaki varno zapisni na vseh vozliščih kar zagotavlja doslednost podatkov, lahko pa uporabljamo asinhrono pisanje kar je hitreje a lahko pride do nedoslednosti kjer nekdo vidi druge podatke kot nekdo drug, ker se še niso posodobili.

**Fragmentacija** je razbijanje baze na več delov, kjer nek del hrani le del baze. To omogča skoraj **neomejeno povečevanje kapacitete** - dodamo novo vozlišče in nanj prestavimo del podatkov.

Največja težava so povetave oz. JOIN operacije saj pridobivanje podatkov iz drugih strežnikov med tem ko se vse izvaja in spreminja je težko izvesti - recimo če rabimo podatke o kupcu na nekem vozlišču in o naročilu na nekem drugem vozlišču. Ponavadi zato NoSQL baze JOIn ne podpirajo neposredno.

***

ACID je za Durability v ozadju zagotovljen z WAL - Write Ahead Log, kjer je vsaka sprememba njaprej zapisana v poseben dnevnik na disku, šele nato pa se dejansko posodobi baza. Če pride do izpada se pogleda v dnevnik. 
Za ACI pa skrbi s centralnim zaklepanjem, kjer sprejme podatek in ga zaklene da ga nihče drug ne more brazi ali pisati, to v porazdeljenih sistemih predstavlja ozko grlo zato implementirajo drugačen pristope.

Po **izreku CAP** v porazdeljenem sistemu ne moremo imeti vsega hkrati, ampak lahko zagotovimo le dve od treh lastnosti: **razpoložljivost (A)**, **konsistentnost (C)** in **odpornost na odpovedi (P)**. Relacijske baze (RDBS) stavijo na točnost in dosegljivost (C in A), medtem ko NoSQL sistemi običajno žrtvujejo popolno točnost, da lahko delujejo na tisočih strežnikih hkrati in ostanejo odporni na izpade omrežja (A in P).

Pri **strogi konsistentnosti** vsi uporabniki v istem trenutku vidijo popolnoma isto vrednost, kar je nujno v bančništvu – če dvignete denar, mora sistem to takoj vedeti na vseh vozliščih. 

Pri **postopni konsistentnosti** pa nastane t.i. "okno nekonsistentnosti", kjer nekateri uporabniki še kratek čas vidijo star podatek, dokler se sprememba ne razširi.

Poznamo tudi **"beri-svoje-podatke"** konsistentnost, kjer sistem zagotavlja, da vedno vidiš svoje zadnje spremembe takoj po zapisu, čeprav jih drugi še ne vidijo. **Konsistentnost seje** pa to zagotavlja le, dokler si prijavljen v isti seji; če se odjaviš in takoj nazaj, se lahko zgodi, da te sistem poveže na drug strežnik, ki še nima posodobljenih podatkov, in spet vidiš staro stanje.