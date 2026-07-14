
Varnostne pomanjkljivosti sistemov izkoriščajo **napadlci**, to je lahko prisluškovanje, ponarejanje sporočil, , kraja identiete, prevzem seje, izločitev udeleženca iz komunikacije, onemogočanje rabe storitev,...

Glavni cilji omrežne varnosti so skrb za **zaupnost, integriteto, identifikacijo, avtentikacijo, avtorizacijo, preprečevanje zanikanja komunikacije.**

**Zaupnost** naj bi skrbela za nedostopnost komunikacije neduleženim.

**Integriteta** naj bi onemogočala možnost da nepooblaščena oseba spreminja podatke, če pa jih pa da se to zazna.

**Identifikacija** naj bi skrbela za ugotavljanje identiete udeležencev v komunikaciji.

**Avtentikacija** naj bi skrbela za dokazovanje identitete udeležencev. S tem se prepričamo o identieti udeležnih preden pošiljamo občutljive podatke.

**Avtorizacija** zagotavlja dostop do podatkov ki so namenjeni dostopu in ničemur več.

**Preprečevanje zanikanaj komunikacije** zagotavlja dokaze o izvoru in prejemu podatkov, s čimer udeleženim stranem onemogoča zanikanje njihovega sodelovanja v komunikaciji. Ta varnostni cilj se v praksi najpogosteje dosega z uporabo digitalnih podpisov, kriptografskih časovnih žigov in infrastrukture javnih ključev.

Varnost je potrebna na vseh plasteh.

Na fizični kriptiramo povezavo, na omrežni filtriramo pakete in opazujemo promet, transportna kriptira povezavo med dvema procesoma, aplikacijske plast avtenticira in preverja identieto.

Poembna je tudi dostopnost strežnikov in računalnikov, ter izobrazba uporabnikov.

Za tehnološki vidik varnosti pa se predvsem uporabljajo **kriptografksi pristopi**. Sporočilo "skrijemo", vidijo pa ga lahko le uoprabniki s ključem.

**Čistopis** je originalno sporočilo, **kriptogram** pa zakrito verzijo sporočila.

Osnovna ideja je da se ob komunikaciji uporablja algoritem ki lahko za vsako komunikacijo ustvari novo šifro ki jo obe napravi lahko dešifrirata, zunanja oseba pa ne. Za to služi **enkripcijski ključ**, ki služi izdelavi kriptograma. Oba morata poznati da enkripcijski ključ oz. morata imeti način s katerim lahko dostopata do njega.

Glede na enakost ključev v komunikaciji delimo metode na **simetrične** in **nesimetrične**. Pri prvem imata obe napravi isti ključ, pri drugem pa si ponavadi delita nek drug skupen parameter ki ga uporabita skupaj s svojima razlčinima ključema da prideta do dejanskega skupnega**enkrpcijskega ključa**.

Uporabljajo se tudi **zgoščevalne funckije** ki ne uoprabljajo ključev.

***

Metode so se delile na **substitucijske** in **transpozicijske** metode. Čeprav je sedanje težko uvrstiti v eno od teh so uporabne za osnovne principe.

**Substitucijske metode**

Vsak znak zamenjamo z nekim drugim znakom s čimer dobimo kriptogram.

Primer je **cezarjev** **kriptogram** ki ga je uporabljal Julij Cezar kjer se vsaka črka pomakne za konstantno število črk v desno, $a$ gre v $c$, $b$ gre v $d$,... *Ta se lahko izbojlša tako da še permutiramo originalno abecedo da dobimo $25!$ možnosti.*

Ko uporabljamo kriptiranje z eno samo abecedo temu rečemo **enoabecedna substitucija**.

**Vigenerjev kriptogram** je subst. kriptogram ki izvaja večabecedno substitucijo. Izberemo neko besedo kot ključ. Zapišemo čistopis, pod njega zapišemo ključ ki se ponavlja do dolžine čistopisa.

Za vsako črko v čistopisu zapišemo navadno abecedo, pogledamo pripadajočo črko ključa in pod njo zapišemo še eno abecedo tako da se začne s to črko. Nato samo pogledamo kam se preslika originalna črka.

Kompleksnost je odvisna od dolžine in vsebine ključa, ta je bolj odporen na statistično analizo parov in trojic črk.

**Porterjev kriptogram**

Naredimo matriko $n \times n$ kjer je $n$ število znakov v abecedi. V vsako polje damo neko vrednost. Potem vse pare črk slikamo v pripadajoča polja.

**Kodiranje**

Kodiranje je metoda kjer s kodno tabelo cel znak, besedo,... nadomestimo z drugo preko kodne tabele, ki nima splošnega pravila za zamenjave.
Ključ je celotne kodna tabela.


> **Kriptoanaliza** metod nam da več metod za ugotavljanje ključa.
> 
> Prva metoda temelji na **poznanem besedilu**, kjer napadalec predvideva standardne dele sporočil (npr. glave kot "HTTP/1.1" ali fraze kot "please login") in z njihovo pomočjo sklepa na ključ. K temu pripomore tudi **poznavanje vsebine** oziroma konteksta sporočila, saj lahko na podlagi teme pogovora uganemo pričakovane besede ali njihove korene.
> 
> Druga metoda je **statistika jezika** (frekvenčna analiza), kjer vemo, da se določene črke in njihove kombinacije v vsakem jeziku pojavljajo z neko pogostostjo. Če je šifrirano besedilo dovolj dolgo, lahko s preštevanjem najpogostejših znakov v šifri ugotovimo, katere črke nadomeščajo.


***

**Transpozicijske metode**

Namesto prelikovanja znakov menjajo vrstni red črk.

Eden od primerov take metode je stolpični kriptogram kjer vzamemo neko besedo kjer se črke ne ponavljajo. Naj bo beseda dolžine $k$. Če vzamemo črke in jih razporedimo po abecedi ter označimo s številkami potem nam beseda da permutacijo $k$-tih elemntov. Potem lahko to permutacijo uporabimo vsakih $k$ črk v čistopisu da jih premešamo.

Kriptoanaliza bi bila dokaj preprosta saj se frekvence črk ne spremenijo torej bi bilo dokaj lahko ugotoviti da se uporablja transpozicijksi algoritem.

***

Sodobne metode uporabljajo  kombinacijo pristopov preprostih metod. Poudarek je na kriptografkih algoritmih na matematičnih osnovah te grobo delimo v **kriptografijo s simetričnimi ključi** in **kriptografijo z javnimi ključi**.

**DES oz. Data Encryption Standard** je bila v ameriki ustanovljena kot uradni standard za kriptiranje. Uporablja se metoda **bločnega kriptiranja**.

Je kombinacija transpozicijskega in substitucijskih metod. Transpozicijske metode temeljijo na permutacijah, pravimo da postopek izvaja **permutacijska škatla** kar je permutacija neke velikosti. Permutacija tvori enkripcijski ključ permtuacijske škatle.

Substitucijo izvajajo **susbstitucijske škatle** ki so sestavljene iz treh delov. **Dekoder**, ki $k$-terice bitov preslika v desetiško število - eno izhodno povezavo, **permutacijsko vezje**   ki preslika v drugo število preko permutacije velikost $2^{k}$ in nazadnje **koder** ki izhod oz. izhodno povezavo oz. število preslika v izhodno $k$-terico bitov. Nek niz je še vedno lahko iz več $k$-teric, kjer potem uoprabljamo več $S$-škatel, za vsako $k$-terico, potem eno $P$-škratlo za vse $S$-škratle in potem spet toliko $S$-škratel za dekodiranje oz. ponovno kodiranje za novo $P$ škatlo, kar lahko vežemo naprej.


![[Pasted image 20260605181211.png]]

Problem je če je $k$ premajhen ker je preprosto ugotoviti vse možnosti, če je prevelik pa težko hranimo tabelo premutacij.

Uporabimo funkcijo za kriptiranje ki simlura veliko tabelo.

Tukaj pride na vrsto **DES** kot tudi drugi algoritmi kot so **3DES** - 3-kratni DES s 3 različnimi ključi in **AES** oz. Advanced Encryption standard.

Te algoritmi uoprabljajo ključe - DES uporablja 64-bitne bloke in 56-bitni ključ, AES pa 128-bitne bloke in 128/192/256-bitne ključe.

**DES** torej razdeli čistopis na 64-bitne bloke in jih zaporedoma kriptira kjer uporablja 56-bitni ključ. Algoritem ima 19 faz
- transpozicija $T_{1}$ neodvisna od enkripcijskega ključa
- preslikave $P_{1},...,P_{16}$, ki so parametrizirane z razlčinimi ključi, izpeljanimi iz glavnega 56-bitnega ključa
- transpozicija $T_{2}$ ki zamenja levo in desno 32 bitno polovico izhoda
- transpozicija $T_{3}$ ki je inverzna transpoziciji $T_{1}$ in tudi neodvisna od enkripcjskega ključa

![[Pasted image 20260605185901.png]]

DES se ne obravnava več kot varen zaradi povečanja računske zmogljivosti naprav.
Še vedno ga potrebujemo za združljivost s starejšimi sistemi.

**Trojni DES**

Trojni DES nadomešča DES kot uradni standard za kriptiranje. Ta je samo 3-kratna aplikacija algoritma DES s tremi različnimi ključi. Prvi in tretji zagon algoritma je standarden v normalen vrstnem redu, drugi zagon pa izvedemo kot **dekripcijo** kar pomeni da algoritem zaganjamo v obratnem vrstnem redu. To je zato ker potrebujemo združljivost s sistemi ki uoprabljajo DES. Če nastavimo $K_{1}=K_{2}$ in $K_3$ kot poseben potem je to ekvivalanetno enemu izvajanju DES torej zgolj s $K_{3}$.

Za obe različici je od nekdaj obstajal sum da je vojska poznala matematičen trik za razbijanje kriptogramov. Torej je sledilo iskanje bolj varnih metod kot je AES.

**AES**

AES je izboljšava DES in 3DES. Nastal je kot posledica javnega razpisa nacionalne agencije za standarde in tehnologije oz. NIST. Izbran je predlog Joan Daemena in Vincent Rijmenta - **Rijndael** [rajndol].

Podpira dolžine ključev in velikosti blokov po odmiku 32 bitov od 128 do 256 bitov - torej 128, 160, 192, ... Čeprav je mogoče ključ in blok izbrati neodvisno standard določa vleikost bloka kot 128 bitov, ključ pa 128, 192, 256 bitov. V praksi se najpogosteje uoprablja s 128- ali 256-bitnim ključem in 128 bitnim blokom.

Algoritem ima 10-14 iteracij izvajanja in uporablja dodatne operacije ki jih ni pri DES kot so zamikanje vrstic, zamenjave stolpcev, izpeljave ključev.

Stroj z $10^9$ procesorji in preverjanja pravilnosti enega ključa v času $10^{-12}s$ bi potreboval $10^{10}$ let. Implementacija je učinkovita - okoli 700Mbps kar je dovolj za več kot 100 mpeg-2 video posnetkov v realnem času. 

***

Problem teh metod je da se ista vsebina preslika v iste vrednosti torej lahko s poznavanjem konteksta vsebine lažje ugotavljamo ključe. Drugi problem je da lahko vzamemo šifre z nekimi ponavljajočimi oblikami za katere vemo da nekaj pomenijo in jih vstavimo v sporočilo česar prejemnik morebiti ne opazi.

To se rešuje z iterativnim spreminjanjem poslanega sporočila z neko vrednostjo od prej. Najprej se izmenja neka inicialna vrednost. S to vrednostjo se kriptira prvo sporočilo nato pa se vsako sporočilo za tem kriptira z rezultatom prejšnje kriptizacije.

Naj bo $m_{i}$ $i$-ti zaporedni blok čistopisa, $c_i$ pa $I$-ti izhodni blok kriptograma in $\veebar$ naj bo XOR, $c_{0}$ pa inicialni vektor potem deiniframo

$$c_{1}= E(m_{1} \veebar c_{0})$$
$$c_{i} = E(m_{i} \veebar c_{i-1})$$

Prejemnik bo prejeto sporočilo odkriptiral z izvedbo operacij v obratnem vrstnem redu

$$m_{1} = E^{-1}(c_{1}) \veebar c_{0}$$
$$m_{i} = E^{-1}(c_{i}) \veebar c_{i-1}$$

Isto sporočilo lahko s tem kriptiramo v različne kriptograme.

Za razbijanje kriptografskih metod se uporabljajo **diferenčna kriptoanaliza** kjer gledamo na spremembe kriptogramov ob zelo majhnih spremembah, **linearna kriptoanaliza** kjer prevedemo ogromno čistopisov in poskusimo omejiti prostor ključev, pistopi so tudi opazovanje porabe elektrike kjer enica porabi elektriko nula pa ne torej lahko poznamo število enic v ključu, lahko merimo čas izvajanja alghoritma da ugotovimo kater operacije se mogoče izvajajo.

***

**Kriptografija z javnimi ključi**

Imamo problem saj ključa ne moremo pošiljati drug drugemu. Iz tega pride algoritem ki za enkripcijo uporablja drugi ključ kot za dekripcijo čemur pravimo **asimetrična kriptografija** oz. kriptografija z javnimi ključi.

Metoda temelji na tem da si oseba generira enkripcijski in dekripcijski ključ ki nista enaka *pomožnosti se enega ne da dobiti iz drugega na trivialen način* in pošlje enkripcijski algoritem sogovorcu, ta enkripta sporočilo in ga pošlje, ker je dekripcijski ključ ostal na varnem ga lahko dekriptira samo prvotna oseba. Iz tega dobimo **javni** in **tajni** ključ.

**RSA**


Algoritem temelji na izrekih

$$n = p_{0}...p_{k} \Rightarrow\varphi(n) = (p_{0}-1)\,\, \cdot\,\, ... \,\cdot\, \,(p_{k}-1)$$
$$m\perp n \Rightarrow m^{\varphi(n)} = 1  \mod n$$

Prafaktorski razcep števila je praktično nemogoče najti. 
Na začetku si izberemo $p,q \in \mathbb{P}$ in dobimo $n = pq$ in še $e$ ki bo enkripicijski ključ.

Naj bo $P$ sporočilo ki ga kodiramo. Po zgornjem izreku dobimo idejo da če je  $P \perp n$ potem je 

$$P^{\varphi(n)} = 1 \mod n$$

Malo spremenimo da dobimo

$$P^{\varphi(n) + 1} = P \mod n$$

Ker je $n = pq$ kjer sta $p,q$ naključno izbrani števili in smo si že izbrali $e$ ne moremo reči $\varphi(n)+1 = ed$ ker je majhna možnost da obstaja tak $d$ zato raje rečemo da je 

$$ed = 1 \mod \varphi(n)$$

oz. velja da osbtaja $k$ da je

$$\varphi(n) \cdot k + 1 = ed$$

Iz tega potem sledi da je


$$P^{ed} \mod n$$
$$=P^{k \cdot = \varphi(n) + 1} \mod n$$
$$=P^{k \cdot  \varphi(n)}P \mod n$$
$$=(P^{\varphi(n)})^{k} \cdot P \mod n$$
$$= 1^{k} \cdot P \mod n$$
$$=  P \mod n$$

Edini manjši problem je *ki se v praksi ne zgodi ampak vseeno* če je $P$ deljiv s $q$ ali $p$. V tem primeru se da dokazati da še vedno velja. 

![[Pasted image 20260605220427.png]]

ker je $P^{ed}$ mod $q,p$ še vedno enak $P$ potem je 
$P^{ed}  = P$ mod $n$.

Enako velja če je $P = pk$.

Torej bo vedno veljalo $P^{ed} = P \mod n$.


Algoritem deluje sledeče

- $p,q$ običajno veliki praštevili
- $n = pq$
  $\varphi(n) = (p-1)(q-1)$
- $d$ naj bo tuje $\varphi(n)$
- Naj bo $e$ število da velja $ed = 1$  mod $\varphi(n)$

Naj bo $C = P^{e}$ mod $n$.

Velja da je $P = C^{d}$ mod $n$.

Ohranimo $d$ pošljemo pa $e,n$.

**Kriptografksa analiza**

Da bi lahko dešifrirali sporočilo bi rabili poiskati $d$ iz $e$ in $n$. *Bolj natančno bi poiskali $p,q$ in nato $e,d$.* To je faktorizacija števil kar je slaven $NP$ problem.

To je relativno počasen algoritem zato se uoprablja bolj pri krajših sporočilih, in še to ponavadi tam kjer hitrost ni pomembna.

**ECDHE**

Ta temelji na eliptičnih krivuljah in grupi ki jo tvori množenje točk na njej. Zelo eleganten sistem kjer vsak od udeležencev izračuna $G \cdot k_{1} = Q_{1}$ in $G \cdot  k_{2} = Q_{2}$, kjer je $G$ začetna točka ki jo oba poznata in $k_{1,2}$ privatna parametra. Oba pošljeta $Q_{1}$ in $Q_{2}$ in nato na svojih napravah privatno izračunata $Q_{1}k_{2}$ in $Q_{2}k_{1}$ to pomeni da oba dobita isto vrednost in sicer

$$Q_{1}k_{2} = Q_{2}k_{1}$$
$$Gk_{1}k_{2}=Gk_{2}k_{1}$$

množenje v tej grupi je kom., hkrati pa velja da je iskanje logaritma praktično nemogoče, torej če imamo podano neko točko $Q$ in začetno točko $G$ je praktično nemogoče poiskati $x$ da velja $Gx = Q$.

Množica točk so vse točke ki zadoščujejo enačbi

$$y^{2}=x^{3}+ ax + b$$

parametri $a,b$ pa so ponavadi izbrani posebej ker niso vsi enakovredno varni.

***

**Zgoščevalne funkcije**

To so funkcije ki vzamejo vrednosti in jih preslikajo v zgoščeno vrednost. Za idealne take funkcije bi veljalo da so injektivne, vendar ponavadi potrebujemo vrednosti fiksne dolžine, torej je kodomena omejena in se to ne da.

Priemr preproste hash funkcije je seštevanje števk števila, če preseže 9999, pa ponovno seštejemo števke na novo dobljenega števila in tako naprej dokler vr. ni manjša od 10000.

Taka funkcija očitno nima inverza.

Dobra hash funkcija porazdeli vhode v izhode enakomerno, in prasliko naj bi bilo relativno težko poiskati.

Najpogosteje se uporablja **MD5** in **SHA-1**.

MD5 vrača 128-bitno zgoščeno vrednost, SHA-1 pa 160-bitno. Delujeta na podoben način, vhodni niz razdelita na 512 bitne bloke, zadnjega se padda do 512, temu se prišteje število ki predstavlja dolžino celotnega vhodnega niza, nato s eprocesira vsak blok posebej z bitnimi operacijami podobno kot v simetrični kriptografiji, rezultate se sešteva po modulu in reducira tak da na koncu ko zmanjka blokov dobimo izhodni niz ustrezne dolžine.

MD5 se ne šteje več za varnega ker so možni napadi ki znižajo zahtevnost brute forca za  veliko zato je priporočljiv v sistemih kjer varnost ni ključna.

SHA-1 je varen ampak se priporoča SHA-256 ki vrača 256 bitno zgoščeno vrednost, predlagani pa so tudi SHA-384, in SHA-512.

Zgoščeno vrednost pripnemo k sporočili da dokažemo avtentičnost integritetio ali pa onemogočili zanikanje.

Ker to lahko anredi tudi napadalec potrebujemo zgoščevalno funkcijo ki deluje s ključem. 


***

Za podpisovanje in preverjanje avtentičnosti uporabljamo hash funcije in enkripcijske algoritme.

Če hočemo preverjati integriteto datoteke ki jo prejmemo moramo na začetku vedeti njen hash, ko jo prenesemo pa še mi izračunamo njen hash in ju primerjamo.

Če hočemo preverjati da je neka datoteka prišla od nekoga mora tista oseba generirati privatni ključ s katerim zakodira hash od datoteke, nam pošlje datoteko in public key s katerim lahko odklenemo hash datoteke, izračunamo hash še pri nas in primerjamo, če se ujemata lahko vemo da je datoteka res od osebe s tem ključem.

Kako pa vemo kdo je dejansko poslal to datoteko oz. lahko avtenticiramo pošiljatelje. To po navadi naredimo tako da pošiljatelj svoj public key pošlje neki **Certificate Authority**-ju ki potrdi njegovo identiteto, v primeru nekih programov, potem ta CA potrdi identiteto, uoprabi svoj privatni ključ da  iz public ključa pošiljatelja generira **certifikat** za tega pošiljatelja, public key ki lahko certifikat odklene da dobimo ta public key pa se pošlje korporacijam ali pa direktno prejemniku ki lahko zaradi dela te avtoritete zaupa da če ta public key odklene nek certifikat potem je oseba ki ga je poslala dejansko ta oseba. Potem pošiljatelj ta certifikat skupaj z zakodiranim hashom datoteke  in datoteko pošlje nam, mi odklenemo certifikat, z dobljenim public keyem pošiljatelja odklenemo hash, hashamo dobljeno datoteko in ju primerjamo in če e vse ujema lahko vemo da smo dobili legitimno datoteko.

**SSL**

SSL oz. TLS kodira povezavo med serverjem in clientom, naprej se zgodi tcp handshake potem pa client pošlje informacije o TLS verziji ki jo podpira in enkripcijske algoritme ki podpira, server se odloči kaj se bo uoprabljalo in generira  public private key pair  in pošlje public key nazaj s katerim lahko client enkripta symmetričen ključ ki bo uporalbjen za sejo, client generira ta key in ga zakodira in pošlje, od takrat naprej se še zaključi postopek in uporablja symm key.

