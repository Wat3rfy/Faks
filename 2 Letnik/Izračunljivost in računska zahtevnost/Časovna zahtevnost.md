
>[!|hide]- $O$ in $o$ notacija
> Naj bosta $f$ in $g$ funkciji $f, g:  \mathbb{N} \rightarrow \mathbb{R}^{+}$. Pravimo, da je $f(n) = O(g(n))$, če obstajata pozitivni celi števili $c$ in $n_0$ tako, da za vsako celo število $n \geq n_0$ velja:
> 
> $$f(n) \leq c g(n).$$
> 
> Kadar je $f(n) = O(g(n))$, pravimo, da je $g(n)$ **zgornja meja** za $f(n)$, ali natančneje, da je $g(n)$ **asimptotična zgornja meja** za $f(n)$, s čimer poudarimo, da zanemarjamo konstantne faktorje.
> 
> 
> Naj bosta $f$ in $g$ funkciji $f, g: \mathcal{N} \longrightarrow \mathcal{R}^+$. Pravimo, da je $f(n) = o(g(n))$, če velja:
> 
> $$\lim_{n \to \infty} \frac{f(n)}{g(n)} = 0.$$
> 
> Z drugimi besedami, $f(n) = o(g(n))$ pomeni, da za poljubno majhno realno število $c > 0$ obstaja število $n_0$ tako, da velja $f(n) < c g(n)$ za vse $n \geq n_0$.
> 
> Pri $O$ obstaja vsaj 1 $c$ tako da je $f$ manjša od $c \cdot g$. Kar pomeni da $f$ ne raste hitreje kot $g$.
> 
> Pri $o$ pa za vsak $c$ velja da je $f$ manjša od $c \cdot g$, kar pomeni da je $f$ zanemarljiva v primerjavi z $g$ ko gre v neskončost.

***

Če obstaja **odločljiv deterministični turingov stroj** ki za vsako besedo dolžine $n$ v $O(f(n))$ korakih ugotovi ali beseda pripada jeziku $L$ natanko tedaj velja

$$L \in \text{TIME}(f(n))$$

> Če obstaja večtračni TS ki prepozna $L$ v času $O(f(n))$ potem obstaja enotračni TS ki $L$ prepozna v $O(f^{2}(n))$.
> >[!|dokaz]- Dokaz:
> >
> > 
> > To sledi iz dejstva da v najslabšem primeru simuliranje vseh trakov na enem dolžin traku poveča v razmerju s $f(n)$, torej če se pri vsakem koraku glava premakne v desno bo dolžina vhoda sorazmerna s $f(n)$ in ker se moramo vedno enkrat ali ponavadi večkrat sprehoditi čez celo dolžino za vsak korak se moramo $f(n)$ krat sprehoditi čez $f(n)$ mest, kar je $f^{2}(n)$



> Ker DKA porabi za vhod dolžine $n$ natanko $n$ korakov da sprejme ali zavrne so TS ki implementirajo regularne jezike v $O(f(n))$.

***
Če imamo **odločljiv nedeterminstični turingov stroj** (*vsaka pot se konča*) velja da je njegova časovna kompleksnost $f(n)$ enaka najdaljši poti ki jo nedeterminističen stroj izvede.

Če obstaja **odločljiv nedeterministični turingov stroj** ki za vsako besede dolžine $n$ v $O(f(n))$ korakih ugotovi ali beseda pripada jeziku $L$ natanko tedaj velja

$$L \in  \text{NTIME}(f(n))$$

***



> Naj bo $t(n)$ funkcija, kjer je $t(n) \geq n$. Potem ima vsak nedeterministični enotračni Turingov stroj s časovno zahtevnostjo $t(n)$ ekvivalenten deterministični enotračni Turingov stroj s časovno zahtevnostjo $2^{O(t(n))}$. Ni nujno da je to najboljši.
> >[!|dokaz]- Dokaz:
> > 
> > To sledi iz tega da je drevo višine $t(n)$. Če se vsakič razvejamo v $b$ otrok potem bo celotno drevo potrebovalo $t(n)b^{t(n)}$ korakov, saj do vozlišča pridemo v $t(n)$, teh pa je $b^{t(n)}$. Z algebro lahko spremenimo to $t(n)b^{t(n)} = 2^{\log_{2}t(n)b^{t(n)}}$ $= 2^{t(n)\log_{2}b + \log_{2}{t(n)}} = 2^{O(t(n))}$.

***

Za naše potrebe so polinomski časi in razlike vzete za majhne, medtem ko eksponentne vzamemo za velike. To je v glavnem zaradi ogromne razlike v hitrosti naraščanja funkcij. Polinomski algoritmi so dovolj hitri v veliko primerih medtem ko so eksponentni redko uporabni.

Eksponentni čas je ponavadi posledica brute-force reševanja problema. Poskušamo vse možnosti preko osnovnih definicij problema. Temu se pogosto lahko izognemo z iskanjem polinomskega algoritma in globjemu razumevanju problema.

V teoriji časovne kompleksnosti so polinomske razlike zanemarjene.
***
$P$ je razred jezikov, ki so odločljivi v polinomskem času na determinističnem enotračnem Turingovem stroju.

$$P = \bigcup_{k} \text{TIME}(n^k).$$

Pravimo da problemi spadajo v $\bigcup_{k}\text{TIME}(n^{k})$  razred $P$ oz. polinomski čas, če jih determinističen stroj lahko reši v polinomskem času.

$P$ (*torej množica jezikov v $P$*) je invarianten za vse računske modele ki so polinomsko ekvivalentni determinstičnem enotračnem turingovem stroju.*Če nek jezik sprejme DETS v polinomskem času potem bo na nekem drugem polinomsko ekvivalenetnem modelu bil isti jezik sprejet z max polinomsko razliko.*

*Časovna kompleksnost razreda ni vezana na stroj ki ga rešuje. Vsi jeziki v razredu P ostanejo v njem pri prehodu med različnimi ekvivalentnimi modeli izračunljivosti, ker vsi standardni deterministični stroji, kot so RAM-stroji in lambda račun, simulirajo drug drugega z največ polinomsko časovno upočasnitvijo.*

*Simulacija je mogoča, ker lahko vsako kompleksno operacijo naprednejšega modela, denimo neposredni dostop do pomnilnika, preprostejši enotračni Turingov stroj izvede z zaporednim skeniranjem traku v času, ki je omejen s polinomsko funkcijo dolžine prvotnega izračuna.*

$P$ se grobo preslika v razred problemov ki so realistično rešljivi na računalniku. 

Primeri problema v $P$ so **problem najkrajše poti** (*Ali v grafu med dvema podanima vozliščema obstaja pot, ki je krajša ali enaka $k$*), **povezanost grafa** (*Ali sta poljubni dve vozlišči v grafu povezani s potjo*), **preverjanje praštevilskosti** (*Ali je dano naravno število $n$ praštevilo oziroma ali nima drugih deliteljev razen 1 in samega sebe*).


***


Jezik $L$ je v $NP$ natanko tedaj, če ga odloča nek polinomski **nedeterministični turingov stroj**. To pomeni:

$$\text{NP} = \bigcup_{k} \text{NTIME}(n^k)$$

Torej lahko problem reši nedeterminstičen stroj v polinomskem času.

Če pogledamo nek polinomski NTS lahko vidimo da bi ob informaciji, katero vejo vzamemo, lahko dobili determinističen polinomski stroj ki bi lahko preveril ali bo ta beseda bila sprejeta ali ne na koncu.

*To da nam pove katero vejo vzamemo pomeni da nam na vsakme nivoju drevesa poda nek simbol ali nekaj kar nam pove katero vejo moramo v tistem trenutku vzeti. To pomeni da je informacija **polinomske dolžine**.*

*Certifikat ni nujno neka beseda ki nam točno pove da naj uberemo neko pot v nedeterminističnem razredu na primer pri iskanju klike grafa je lahko le množica vozlišč v kateri vemo da je klika, nato pa determinističen preverjevalnik lahko le preveri da so notri vse potrebne povezave.*

Takemu stroju pravimo **preverjevalnik** in velja da je $NP$ razred jezikov ki imajo **polinomski preverjevalnik**.

**Preverjevalnik**  $V$ definiramo kot determ. TS za katerega velja

 $$w \in L \iff \exists c\, \text{ da } V \text{ sprejme } \langle w, c \rangle$$


> Če obstaja deterministični turingov stroj $V$, ki za vhod $w$ in dodatno informacijo $c$ (certifikat)  v polinomskem času preveri pripadnost jeziku, potem za jezik $L$ velja:
> 
> $$w \in L \iff \exists c\, \text{ da } V \text{ sprejme } \langle w, c \rangle$$
> 
> kjer mora biti $c$ **polinomske dolžine**.

*To pomeni da $V$ deluje v $O(n^{k})$ in da obstaja polinom $p$ da za vsak $w \in L$ obstaja $c$ tak da je $|c| \leq p(n)$*

Če $w \notin L$ potem, noben $c$ ne sme prepričati preverjevalnika.
***

To da sta definiciji ekvivalentni lahko potrdimo s tem da iz NTS lahko naredimo preverjevalnik kjer za certifikat vzemamo vejo oz. kodo veje ki jo mora NTS ubrati - na vsakem koraku preberemo število veje po kateri moramo iti, ker vemo da je NTS polinomske dolžine bo tudi $c$ polinmske dolžine.

Obratno pa velja da če imamo nek preverjevalnik $V$ potem lahko NTS polinmske kompleknosti konsturiramo tako da ugibamo certifikat in potem deterministično pregleda ali ga $V$ sprejme skupaj z $w$, kar bo polinomskega časa saj je $V$ polinomski DTS, $c$ pa polinomske dolžine.

Primeri problemov v $NP$ so **Hamiltonova pot** (*Ali v grafu obstaja pot, ki obišče vsako vozlišče natanko enkrat*), **problem izpolnjivosti (SAT)** (*Ali za dano logično formulo obstaja nabor resničnostnih vrednosti spremenljivk, pri katerih je celotna formula resnična*), **vsota podmnožice** (*Ali v dani množici celih števil obstaja neprazna podmnožica, katere vsota elementov je natanko enaka podanemu številu $T$*) in **barvanje grafov** (*Ali je mogoče vozlišča grafa pobarvati z največ $k$ barvami tako, da nobena sosednja vozlišča niso iste barve*).

Da so problemi v $NP$ dokazujemo tako da damo neko dodatno informacijo oz. mogočo rešitev problema in potem preverjamo če ob tej dodatni informaicji lahko rešimo problem za podano rešitev.

**Preverjevalnik**
Za vsoto podmnožice $A$ npr. podamo neko poljubno množico števil *ne nujno $A$*, preverimo ali je vsota teh enaka $k$, preverimo ali je množica podmnožica $A$. 

**NTS**
Nedeterministično izberemo podmnožico $A$, preverimo ali se seštejejo do $k$.

**Preverjevalnik**
Za kliko lahko podamo nek podgraf $G$. Testiramo ali ima $k$ vozlišč, testiramo ali $G$ vsebuje vse robove ki povezujejo vozlišča v $G$.

**NTS** Nedeterministično izbiramo podmnožice $k$ vozlišč. Testiramo ali se vse povezujejo.

**Če pogledamo negacijo vprašanj vidimo da niso očitno v NP - tem pravimo coNP**. *ComplementNP in ne vemo ali je drugačen od NP.*

***

$P$ povzamemo kot množico jezikov kjer lahko besedo odločamo v polinmskem času, $NP$ pa množico jezikov kjer lahko besedo preverimo v polinmskem času.

Velja $P \subseteq NP$, saj lahko vsak problem, ki ga rešimo v polinomskem času, v polinomskem času tudi preverimo (certifikata ne potrebujemo ali pa je prazen).
Odprto vprašanje **P proti NP** sprašuje, ali je preverjanje rešitve enako zahtevno kot generiranje rešitve. Če bi veljalo $P = NP$, bi bili vsi problemi v NP rešljivi v determinističnem polinomskem času.

Vemo da je $P \subset NP$ saj lahko vsako rešitev ki jo lahko odločimo v polinomskem času očitno preverimo v polinomskem času - ne podamo certifikata ali pa je prazen.

Podani primeri za $NP$ so bili te za katere ne vemo da so $P$. Do sedaj še ni bilo dokazano da obstaja jezik ki je v $NP$ in ni v $P$

Do sedaj je najboljša determinstična metoda ki odloča jezik v $NP$ v eksponentnem času oz. velja

$$\text{NP} \subseteq \text{EXPTIME} = \bigcup_{k}\text{TIME}(2^{n^{k}})$$

ne vemo pa če je $NP$ vsebovan v manjši deterministični množici časovne kompleksnosti.

***

Poznamo koncept **$NP$-polnosti**. To pomeni da obstajajo problemi v $NP$ za katere velja da odražajo kompleksnost  celotnega razreda - z drugimi besedami če obstaja polinomski algoritem da se reši katerikoli $NP$-poln problem potem so vsi problemi v $NP$ rešljivi v polinomskem času. 

Po drugi strani če kateri koli problem v $NP$ rabi več kot polinomski čas potem ga rabi tudi $NP$-poln.

Funkcija $f:\Sigma^{*} \rightarrow \Sigma^{*}$ je  **polinomsko izračunljiva funkcija** če obstaja polinomski TS ki na se vhodu $w$ ustavi na traku pa ostane samo $f(w)$. 

Jezik $A$ se da **polinomsko prevesti** na $B$ če velja $w \in A \Leftrightarrow w \in B$ in je $f(w)$ polinomsko izračunljica. $A \leq_{p} B$.

*Torej v polinomskem času lahko izvedemo prevedbo ki jo bo potem lahko neki polinomski algoritem rešil.*

>$A \leq_{p} B$ in $B \in P$ $\Rightarrow$ $A \in P$ .



> Velja da je jezik $B$ $NP$ poln ko velja da je $B \in NP$ in lahko vsak $A \in NP$ polinomsko prevedemo na $B$ oz.
> $B \text{ je NP poln } \Leftrightarrow B \in NP \land \forall A \in NP : A \leq_{p} B$

Da je jezik $NP$ poln pomeni da lahko vsak jezik v $NP$ prevedemo na tega - če bi lahko tega rešili v polinomskem času, in je prevod le nek polinomski dodatek bi bil celoten problem s prevedbo vred rešljiv v polinomskem času.

Hkrati nam to pove da lahko nek jezik prevedemo v $B$ in celoten proces - prevedba in preverjanje $B$-ja ne bo večja od polinomske zahtevnosti.


Eden izmed $NP$-polnih problemov je **satisfability problem** oz. $SAT$ problem. Če imamo podano nek logični izraz $\Phi$ potem je $SAT$ problem **ali obstaja določitev spremenljivk da se izraz evaluira v 1.**

Naj bo **člen oz. klavzula** definiran kot več spremenljivk povezanih z disjunkcijo.

KNO izraz je konjunktivna normalna oblika.

3KNO izraz je konjuktivna normalna oblika z natanko tremi spremenljivkami v vsakemoklepaju.

$$(x_1 \lor \overline{x_2} \lor \overline{x_3}) \land (x_3 \lor \overline{x_5} \lor x_6) \land (x_3 \lor \overline{x_6} \lor x_4) \land (x_4 \lor x_5 \lor x_6)$$

$3SAT$ pa je problem pri katerem sprejmemo izraz če obstaja določoitev spremenljivk da se izraz ovrednoti z 1.
***
Če hočemo dokazati da je problem iskanja klike $k$ velikosti $NP$ poln potem mora biti v $NP$ in veljati da obstaja prevedba iz $3SAT$ na $CLIQUE$ ker lahko vse probleme v $NP$ prevedemo na $3SAT$ in očitno potem tudi na $CLIQUE$.

Prevedba iz $3SAT$ v $CLIQUE$ je taka da za vsako skupino treh spremenljivk definiramo 3 vozlišča. Za vozlišča v isti skupini bo veljalo da med seboj niso povezana. Vse ostalo je povezano razen pari vozlišč ki so presdtavljeni z isto spremenlijvko ampak, kjer je ena od vrednosti negirana.

Tak izraz bo ovrednoten z 1 natanko tedaj ko bo obstajala v grafu klika $k$ velikosti.

Recimo da se izraz ovrednoti z ena. To pomeni da je v vsakem členi vsaj 1 spremenljivka enaka 1. Iz vsakega člena si izberemo poljubno vozlišče ki je ovrednoteno z 1. Ta vozlišča tvorijo kliko. Vsa vozlišča ki bodo izbrana bodo povezana saj niso povezana le vozlišča kjer bi bilo v eni skupini 1 in v drugi 0.

Predpostavimo da ima $G$ kliko. Vozlišča ki tvorijo kliko ne morejo biti v isti skupini. Torej mora vsaka skupina vsebovati natanko eno of $k$ vozlišč ki tvorijo kliko. Dodelimo vrednosti logičnemu izrazu tako da vsa vozlišča ki tvorijo kliko dobijo 1, kar je mogoče saj povezava med vozlišči ki bi lahko imeli nasprotni vrednosti ne obstaja. Ta določitev spremenljivk zadošča izrazu saj imamo 1 v vsakem členu.

***

> Za ta dokaz smo uporabili izrek ki pravi
> $B$ je $NP$-poln in velja da je $B \leq_{p} C$ za nek $C \in NP$ potem je $C$ $NP$-poln.

> Če velja da je $B$ $NP$-poln in je $B \in P$ potem velja $P = NP$.

***


> **Cook-Levinov izrek**
> 
> **SAT je NP-poln.**

SAT je v NP ker lahko nedetemrinistično uganemo določitev vrednosti nato pa v polinomskem času preverimo ali se ovrednoti z 1.

Sedaj vzamemo jezik $A$ ki naj bo v $NP$ in pokažemo da je $A$ polinomsko prevedljiv na $SAT$.

Naj bo $N$ NTS ki odloča $A$ v $n^{k}$.
Naj bo tabla za $N$ na $w$, $n^{k}\times n^{k}$ tabela katere vrstice so konfiguracije veje $N$ ki procesira $w$.







![[Pasted image 20260125140138.png]]







Tabla je sprejemna če katerakoli vrstica vsebuje sprejemno konfiguracijo. To prevede problem odločanja če $N$ sprejme $w$ v odločanje ali obstaja sprejemljiva tabla za $N$ na $w$.

Sedaj pridemo do polinomske prevedba iz $A$ na $SAT$. Ob vhodu $w$ pridobimo izraz $\phi$.

Da opišemo spremenljivke $\phi$ rečemo da sta $Q$ in $\Gamma$, množici stanj in abecede traku. Naj bo $C = Q \cup \Gamma \cup \{ \#\}$. Za vsak $i$ in $j$ $\in  \{ 1,...,n^{k}\}$ in za vsak $s \in C$ imamo spremenljivko $x_{i,j,s}$.

Vsak od $n^{2k}$ celic ima vrsitco $i$ in stolpec $j$ ter vsebuje simbol $s$. Vsako celico lahko predstavimo z eno spremenljivko. Če celica $[i,j]$ vsebuje $s$ rečemo da je $x_{i,j,s} \sim 1$.

Sedaj ustvarimo izraz kjer izraz ovrednoten z 1 odraža sprejemno tablo $N$ na $w$.

Le ta bo konjunkcija 4 delov

$$\phi_\text{cell} \land \phi_{_\text{start}} \land \phi_\text{move} \land \phi_\text{accept}$$

Najprej moramo zagotoviti da vsaka celica vsebuje natanko 1 simbol.

$$\phi_{\text{cell}} = \bigwedge_{1 \le i, j \le n^k} \left[ \left( \bigvee_{s \in C} x_{i,j,s} \right) \wedge \left( \bigwedge_{\substack{s, t \in C \\ s \neq t}} (\overline{x_{i,j,s}} \vee \overline{x_{i,j,t}}) \right) \right]$$

oz.

$$\phi_{\text{cell}} = \bigwedge_{1 \le i, j \le n^k} \left[ \left( \bigvee_{s \in C} x_{i,j,s} \right) \wedge \left( \bigwedge_{\substack{s, t \in C \\ s \neq t}} (x_{i,j,s} \Rightarrow \overline{x_{i,j,t}}) \right) \right]$$

Za vsako celico velja da je vsaj en $s$ zapisan noter in če je nek $s$ napisan noter potem $t \neq s$ ne sme bit noter hkrati.

Za $\phi_\text{start}$ velja da določa da je v prvi vrstici začetna konfiguracija

$$\begin{aligned}
\phi_{\text{start}} = \, & x_{1,1,\#} \wedge x_{1,2,q_0} \wedge \\
& x_{1,3,w_1} \wedge x_{1,4,w_2} \wedge \dots \wedge x_{1,n+2,w_n} \wedge \\
& x_{1,n+3,\sqcup} \wedge \dots \wedge x_{1,n^k-1,\sqcup} \wedge x_{1,n^k,\#}.
\end{aligned}$$

Za $\phi_\text{accept}$ pa velja da zahteva pojavitev sprejemne konfiguracije v tabli, s tem da zahteva $q_\text{accept}$ v eni od celic

$$\phi_{\text{accept}} = \bigvee_{1 \le i, j \le n^k} x_{i,j,q_{\text{accept}}}$$

Na koncu $\phi_\text{move}$ zagotavlja da je vsaka vrstica v tabli veljavna konfiguracija ki sledi iz prejšnje. To stori tako da zagotovi da so vsa $2 \times 3$ okna legalna, kar pomeni da ne krši prehodne funkcije.

Tako okno je dovolj saj se lahko konfiguracije iz prehoda ene v drugo meaningfully spremeni samo v okolici glave. Ta lahko spremeni simbol in se premakne desno ali levo. 
To pomeni da lahko vpliva (če je na sredini) na 3 simbole in to le v primeru če spremeni simbol v glavi in se premakne levo. V vseh drugih primerih se spremeni največ 2 ali 1 simbol. To pomeni da če potrdimo da so vsa $2 \times  3$ okna legalna je prehod med konfiguracijami validen.

Če je prva vrstica začetna konfiguracija in je v tabli vsako okno legalno potem je vsaka vrstica validna konfiguracija ki sledi prejšnji po prehodni funkciji.

$\phi_\text{move}$ zagotavlja da so vsa okna v tabli legalna. Vsako okno vsebuje 6 celic ki so lahko razporejeni v nekem končnem številu razporeditev. Vse te razporeditve so vključene v prevedbo in izraz pravi

$$\phi_{\text{move}} = \bigwedge_{1 \le i < n^k, 1 < j < n^k} (\text{the } (i, j)\text{-window is legal}).$$

kjer je oklepaj za legalnost $i,j$ okna

$$\bigvee_{\substack{a_1, \dots, a_6 \\ \text{is a legal window}}} 
(x_{i, j-1, a_1} \wedge x_{i, j, a_2} \wedge x_{i, j+1, a_3} \wedge 
x_{i+1, j-1, a_4} \wedge x_{i+1, j, a_5} \wedge x_{i+1, j+1, a_6})$$

kjer je $\bigvee_{\substack{a_1, \dots, a_6 \\ \text{is a legal window}}}$ range vseh legalnih oken ki jih generiramo ob prevodu preko prehodnih funkcij.

Prevod je polinomski, res velja da je $Q$ in $\Gamma$ posledično tudi velikost $C = \Gamma \cup(Q \times \Gamma)$, konstantna in neodvisna od $n$ . To pomeni da je števio vseh razporeditev v oknu $|C|^{6}$ kar je konstantno.
V tabeli je $n^{k}\times n^{k}$ oken (*kar je prostorska in časovna omejtiev*) enaka $n^{2k}$ kar je res polinomske kompleksnosti.

Za glavno porabo časa imamo torej $\phi_\text{move}$ kar bo število oken $\times$ število legalnih konfiguracij $\times$  Število celic v oknu $\sim n^{2k} \cdot |C|^{6} \cdot 6$

***

Da dokažemo da je tudi 3SAT NP poln poiščemo polinomsko redukcijo SAT na 3SAT.

Za $\phi_\text{cell, accept, start}$ so že praktično v KNO. Pretovoriti moramo samo $\phi_\text{move}$. Uporabimo distributivnost da pridemo iz DNO v KNO. To ponavadi eksplodira velikost ampak v tem primeru je število simbolov v oknu konstantno kar pomeni da se poveča le za konstanten faktor, ki ni odvisen od $n$.
Sedaj imamo celotno formulo v KNO. Da pretvorimo v 3SAT torej 3 člene v vsakega preprosto delamo naslednje transformacije

$$a \rightarrow a\lor a \lor a$$
$$a \lor b\rightarrow a\lor a \lor b$$
$$a_1 \vee a_2 \vee a_3 \vee a_{4}\rightarrow(a_1 \vee a_2 \vee z_1) \wedge (\neg z_1 \vee a_3 \vee a_4)$$

2SAT ne bi bil primeren saj je **rešljiv** v linearnem času $O(N+M)$ kar pomeni da če uspemo najti prevedbo iz SAT na 2SAT potem bi dokazali da je $P=NP$.

Pri 2SAT-u ni ugibanja saj v dvočlenskih disjunkcijah določanje ene spremenljivke določi drugo to določi naslednjo in tako naprej - **rešljivo** je v polinomskem času.

Pri 3SAT je problem ker potrebujemo določiti 2 spremenljivki da dobimo tretjo kar pomeni da moramo ugibati, če imamo $n$ takih odločitev bomo imeli drevo z $2^{n}$ listi, ampak problem pa je še vedno preverljiv v polinomskem času saj imamo nek certifikat ki poda vrednosti za vsak člen, mi le preverimo če je ena izmed njih 1 teh bo največ $3 \cdot m \cdot n$, seveda mora biti tudi certifikat polinomkse dolžine. Za formulo ki je vhod 3SAT velja da je dolžine $n$ saj podamo $n$ vrednosti za logične vrednosti spremenljivk.

***

Velja da je tudi pokritje vozlišč NP poln. To dokažemo s prevodom 3SAT na VC - vertex cover. VC je problem kjer nas zanima ali v podanem grafu obstaja množica vozlišč velikosti $k$ da je vsaka povezava del vozlišča iz množice.

Za prevedbo mora veljat da lahko poljuben logični izraz prevedemo v graf $G$ in število $k$ kjer obstaja obstaja $k$ vozliščno pokritje natanko tedaj ko je izraz ovrednoten z 1.

Veljalo bo da je $k = 2m$, kjer je $m$ število členov. Torej hočemo najti pokritje velikosti $2m$.

Za vsak člen s tremi literali ustvarimo 3 vozlišča in jih povežemo s ciklom. Če imamo $m$ členov imamo $3m$ vozlišč.
Povezave narišemo še med nasprotnimi literali torej če imamo v enem členu $x$ in v drugem $\overline{x}$ te dve vozlišči povežemo.

To deluje saj moramo v vsakem od $m$ trikotnikov izbrati 2 oglišči, da pokrijemo notranje povezave trikotnika. To pride $2m$ oglišč. V vsakem trikotniku ostane eno vozlišče - ta predstavlja resničen literal.

Ker moramo preprečiti izbiro kjer v enem trikotniku ostane $x$ v drugem pa $\overline{x}$ povežemo še vse nasprotne literale s čimer ob izpustitvi enega mora veljati da drugega vključimo, saj drugače ni pokritja ker povezava med njima ni vključena.

Torej mi lahko nek izraz prevedemo v opisan graf, in če najdemo veljavno pokritje $2m$ lahko trdimo da so v orignalnem izrazu te spremenljivke $0$ ostale pa 1 in bomo dobil veljaven izraz ki se ovrednoti z 1.

Velja da sta tudi **vsota podmnožice** in **hamiltonova pot** NP polna. Dokaz še pride.

313