
**Turingovi stroji** so avtomati z neskončnim in neomejenim spominom. Sestavljen je iz **traka** in **glave**. Glava se premika po traku in tam kjer stoji lahko **piše** ali pa **bere** simbole.

Mašina nam lahko vrne sprejem ali zavrnitev, lahko pa se nikoli ne ustavi.

**Turingov stroj** je sedemterica $(Q, \Sigma, \Gamma,\delta, q_{0}, q_{\text{accept}}, q_{\text{reject}} )$, kjer so $Q, \Sigma$ in $\Gamma$ končne množice in so
1. $Q$ množica stanj
2. $\Sigma$ vhodna abeceda brez **praznega simbola $B$**
3. $\Gamma$ je abeceda traka kjer je **prazen simbol $B$** $\in \Gamma$ in $\Sigma \subset \Gamma$.
4. $\delta: Q \times  \Gamma \rightarrow Q \times \Gamma \times  \{ L, R\}$ je funkcija spremembe stanj
5. $q_{0}$ je začetno stanje
6. $q_\text{accept}$ je sprejemno stanje
7. $q_\text{reject}$ je zavrnitveno stanje in $q_\text{reject} \neq q_\text{accept}$

**Prazni simbol $B$** je simbol ki je postavljen tam kjer na traku še ni ničesar.

Ko stroj pride v enega od $q_\text{accept}$ ali $q_\text{reject}$ se ustavi.

Vhodni niz dolžine $n$ je postalvjen na prvih $n$ mest na traku. Vsa ostala mesta so $B$. Če je glava na začetku ne more iti levo, tudi če je podan ukaz $L$.

Stanju traka in poziciji glave skupaj pravimo **konfiguracija** stroja. Ta je ponavadi podana kot $uqv$ kjer je $uv$ stanje traka kjer $B$ po $v$ ne pišemo, $q$ pa označuje trenutno stanje. 

Pravimo da konfiguracija $C_{1}$ daje $C_{2}$ če stroj lahko pride iz $C_{1}$ v $C_{2}$ v enem koraku. 

To pomeni da ob podani konfiguraciji $ua q_{i} bv$, kjer sta $u,v$ niza, $a,b$ simbola in $q_{i}$ stanje, velja:

$$\delta(q_{i},b) = (q_{j},c,L)\Rightarrow ua\,\,q_{i}\,\,bv\space \text{ da }\space u\,\,q_{j}\,\,acv $$

$$\delta(q_{i},b) = (q_{j},c,R)\Rightarrow ua\,\,q_{i}\,\,bv\space \text{ da }\space uac\,\,q_{j}\,\,v $$


**Začetna konfiguracija** stroja na vhodnem nizu $w$ je podana kot $q_{0}w$.

Stroj je v začetnem stanju $q_{0}$ in glava je na skrajnem levem mestu, torej na prvem znaku niza $w$.

Če je vhodni niz prazen (označen z $\epsilon$), je začetna konfiguracija $q_{0}B$, saj glava stoji na prvem **praznem simbolu $B$**.


V **sprejemni konfiguraciji** je stanje konfiguracije $q_{\text{accept}}$.
V **zavrnitveni konfiguraciji** je stanje konfiguracije $q_{\text{reject}}$.

Sprejemnim in zavrnitvenim konfiguracijam pravimo **ustavitvene konfiguracije**. Te konfiguracije ne dajo naslednjih konfiguracij (iz njih ne moremo nikamor).

> Turingov stroj $M$ **sprejme** vhod $w$, če obstaja zaporedje konfiguracij $C_{1}, C_{2}, \dots, C_{k}$, kjer velja:
> 1. $C_{1}$ je začetna konfiguracija $M$ na vhodu $w$
> 2. Vsak $C_{i}$ daje $C_{i+1}$
> 3. $C_{k}$ je sprejemna konfiguracija

Množica nizov ki jih sprejme $M$ je jezik $M$ oz. $L(M)$.


***


Če imamo jezika $A$ in $B$ velja, da je jezik $A$ prevedljiv na jezik $B$ če obstaja izračunljiva funkcija $f$, da velja

$$w \in A \Leftrightarrow f(w) \in B$$

Funkijca je **izračunljiva** če obstaja Turingov stroj $M$ ki se ustavi na vsakem vhodu $w$ in ima ob ustavitvi na traku zgolj $f(w)$.

***


Ko zaženemo Turingov stroj na nekem vhodu, so možni trije izidi. Stroj lahko **sprejme**, **zavrne** ali pa se **cikla**.

S **ciklanjem** mislimo, da se stroj preprosto ne ustavi.

Turingov stroj $M$ ne sprejme vhoda tako, da preide v stanje $q_{\text{reject}}$ in zavrne, ali pa s tem, da se cikla.

Strojem ki pridejo v končno stanje za vse vhode pravimo **odločitveni** stroji.
Jezik je **odločljiv** če obstaja **odločljiv** stroj ki ga sprejme.

Formalno pravimo da je $L$ odločljiv če obstaja $M$ da je $L = L(M)$ in $\forall w \in L : q_{0}w \vdash uq_{F}v$
$\forall w \notin L : q_{0}w \vdash uq_{F}v$

Stroju ki ne pride v končno stanje samo za nize ki **so v jeziku** pravimo da je polodločljiv, jezikom ki jih stroj sprejme pa **polodločljivi**.

Formalno pišemo da je $L$ polodločljiv če obstaja $M$ da velja $L = L(M)$ in velja
$\forall w \in L : q_{0}w \vdash uq_{F}v$.
*Če $w$ ni v jeziku ne vemo ali se stroj zanj ustavi ali ne.*

Polodločljivim strojem pravimo tudi prepoznavni stroji, saj lahko prepoznajo nize v jeziku, ne pa vedno ali ga zavrnemo.


***

>Če obstaja prevedba oz. **redukcija** $A$ na $B$ in je $B$ odločljiv. Potem je $A$ odločljiv.
>>[!|dokaz]- Dokaz:
>> To lahko dokažemo tako da vzamemo besedo $w$, izvedemo funkcijo $f(w)$, zaženemo $f(w)$ na odločljivem stroju za $B$ in dobimo odgovor. Ker velja $w$ je v $A$ natanko teda ko je $f(w)$ v $B$ potem vemo da je za $w \in A$ isti odgovor kot za $f(w) \in B$

>Če obstaja prevedba oz. **redukcija** $A$ na $B$ in je $B$ polodločljiv. Potem je $A$ polodločljiv.

>Če obstaja prevedba oz. **redukcija** $A$ na $B$ in je $A$ neodločljiv. Potem je $B$ neodločljiv.

>Če obstaja prevedba oz. **redukcija** $A$ na $B$ in je $A$ neprepoznaven. Potem je $B$ neprepoznaven.

***
**Variante Turingovih strojev**

Obstajajo variacije Turingovih strojev, ki vključujejo različice z več trakovi ali nedeterminizmom. Imenujemo jih **variante**. Originalni model in njegove variante **prepoznajo isti razred jezikov**. Tej odpornosti na spremembe v definiciji pravimo **robustnost**. 

Variante so **večtračni, nedterministični**, enostranski, stroj z več glavami, večdimenzionalni.

Ekvivelntni pa niso stroji z omejenim trakom, stroj ki ne more pisati na trak.

Velja tudi da če je trak omejen z dolžino traku $O(n)$ potem sprejme **kontekstno odvisne jezike**.

Da pokažemo, da sta dva modela ekvivalentna, moramo pokazati, da lahko eden simulira drugega.

**Večtračni Turingov stroj**

**Večtračni Turingov stroj** je kot navaden stroj z več trakovi. Vsak trak ima svojo glavo za branje in pisanje. Na začetku je vhodni niz zapisan na traku 1, vsi ostali trakovi pa so prazni (vsebujejo samo simbole $B$).

Funkcija prehoda je spremenjena tako, da omogoča branje, pisanje in premikanje glav na nekaterih ali vseh trakovih hkrati. Formalno je funkcija:

$$\delta: Q \times \Gamma^k \rightarrow Q \times \Gamma^k \times \{L, R, S\}^k$$

kjer je $k$ število trakov. Izraz $\{L, R, S\}$ pomeni levo, desno ali "stay" (ostani na mestu). Izraz $\delta(q_i, a_1, \dots, a_k) = (q_j, b_1, \dots, b_k, L, R, \dots, L)$ pomeni, da če je stroj v stanju $q_i$ in glave berejo simbole $a_1$ do $a_k$, stroj preide v stanje $q_j$, zapiše simbole $b_1$ do $b_k$ in premakne vsako glavo v določeno smer.

Vsak večtračni stroj lahko implementiramo z enotračnim strojem.

**Nedeterministični Turingov stroj**

**Nedeterministični stroji** delujejo tako, da se lahko na kateri koli točki izvajanja odloči med več možnostmi. Funkcija prehoda za nedeterministični stroj ima obliko:

$$\delta: Q \times \Gamma \rightarrow \mathcal{P}(Q \times \Gamma \times \{L, R\})$$

Izračun nedeterminističnega stroja je drevo, kjer veje ustrezajo različnim možnostim. Če katerakoli veja izračuna vodi do sprejemnega stanja, stroj sprejme vhod.

Da stroj zavrne vhod morajo vse veje biti končne in zavrniti vhod.

Vsak nedeterministični stroj ima ekvivalenten deterministični stroj. To dokažemo s simulacijo, kjer deterministični stroj preiskuje drevo nedeterminističnega stroja (običajno s pregledom v širino, da se izogne neskončnim vejam).

Da je NTS **odločilen** se mora ustaviti na vsaki veji.

***


**Algoritmi**


Povezava med intuitivnim konceptom algoritma in Turingovimi stroji se imenuje **Church-Turingova teza**. Teza trdi, da je vsak intuitivni algoritem ekvivalenten algoritmu Turingovega stroja.

Turingov stroj služi predvsem kot natančen model za definicijo algoritma.  Osredotočamo se na algoritme same.
S temi modeli znamo izraziti vse kar intuitivno razumemo kot algoritem.

***


Vhod v Turingov stroj je vedno niz. Če želimo kot vhod podati drug objekt (npr. graf, polinom, avtomat), ga moramo najprej zakodirati v niz. Zapis za kodiranje objekta $O$ v niz je $\langle O \rangle$. Če imamo več objektov, jih zapišemo kot $\langle O_1, O_2, \dots, O_k \rangle$.

Turingov stroj lahko vedno preprogramiramo tako, da prevede eno vrsto kodiranja v drugo, zato točen način kodiranja ni bistven.
***
Sedaj se lahko ukvarjamo s **problemi izračunljivosti** ki se tičejo končnih avtomatov.
Če hočemo algoritem ki nam pove ali je neka beseda v jeziku nekega DKA, ali je jezik DKA prazen, ali sta dva DKA ekvivalentna,... bomo definirali **odločitevni problem**.

Naj bo jezik $A_{DKA}$ definiran kot $\{ \langle K,w\rangle  \,;\; K\text{ je DKA ki sprejme }w\}$.

To pomeni da lahko problem "Ali lahko $K$ sprejme $w$" pretvorimo v jezik $A_{DKA}$ kjer postane vprašanje ekvivalentno temu ali $\langle K,w \rangle$ pripada $A_{DKA}$. 

Če pokažemo da je jezik odločljiv potem velja da je tudi originalni problem odločljiv in zanj obstaja odločljiv algoritem.

> $A_{DKA} = \{ \langle K,w\rangle  \,;\; K\text{ je DKA ki sprejme }w\}$ je odločljiv jezik
> >[!|dokaz]- Dokaz:
> > Sledimo stanju avtomata $A$ in trenutni poziciji v vhodu $w$ tako da ju zapišemo na trak. $A$ začne na $q_{0}$ in začnemo na prvem simbolu $w$. Stanja in pozicija v $w$ so posodobljena glede na $\delta$ in ko $M$ neha procesirat zadnji simbol pogledamo v katerem stanju smo glede na kar se odločimo ali sprejmemo ali zavrnemo vhod.

*Podobno lahko naredimo za $NKA$ kjer vemo da obstaja pretvorba iz kode NKA v DKA in nato uporabimo isti algoritem kot pri $A_{DKA}$. Nato pa lahko še podobno naredimo za regularne izraze, kjer jih pretvorimo v NKA in rešimo s prejšnjim algoritmom.*

> Velja da so $A_{DKA}, A_{NKA}$ in $A_{REG}$ odločljivi

Naslednji problem ki ga lahko pogledamo je ali jezik DKA ni prazen$$\overline{E}_{DKA} = \{ \langle A \rangle \,;\;A \text{ je DKA in } L(A) \neq \emptyset\}$$

> $\overline{E}_{DKA}$ je odločljiv
> >[!|dokaz]- Dokaz:
> >Algoritem je preprosto iskanje po grafu. Označimo začetno stanje nato pa oznčaujemo vsa stanja do katerih lahko pridemo iz že označenih stanj dokler jih ne zmanjka oz. ni novih stanj označnih, če nobeno končno stanje ni označeno, potem je prazen jezik.

Spet enako velja za NKA in REG.

> Odločljiv je tudi jezik ki prepozna vse DKA-je ki so ekvivalentni oz. 
> 
> $$EQ_{DKA} = \{ \langle A,B\rangle \,;\; A, B \text{ sta DKA-ja in } L(A) = L(B)\}$$

Najprej ustvarimo jezik $L(C)$ kjer velja $L(C) = L(A) \oplus L(B)$ *disjukntna unija* in preverimo če je $L(C)$ prazna množica. Ta konstrukcija je veljavna ker so vse operacije v disjkuntni uniji zaprte pod regularnimi izrazi.

Obstajajo sorodni problemi za gramatike kjer za pripadanje in nepraznost jezika velja da sta odločljiva

$$A_{CFG}=\{ \langle G,w\rangle \,;\;G \text{ je KNG in } w \in L(G\}$$


$$\overline{E}_{CFG}=\{ \langle G\rangle \,;\;G \text{ je KNG in } L(G) \neq \emptyset\}$$


medtem ko za ekvivalentnost devh KNG ne moremo odločati saj KNL niso zaprti pod presekom in komplementom

$$EQ_{CFG}=\{ \langle G_{1},G_{2}\rangle \,;\;G_{1},g_{2} \text{ sta KNG in } L(G_{1}) = L(G_{2})\}$$

Jeziki so kategorično razporejeni

$$\text{regularni} \subset \text{KNG} \subset  \text{odločljivi} \subset \text{prepoznavni}$$

Če je neodločljiv je lahko prepoznaven, ali ne prepoznaven.

Seveda obstajajo tudi jeziki za katere ne obstaja turingov stroj ki bi ga lahko prepoznal. Takim pravimo neprepoznavni

Velja da je $A_{TM}$ neodločljiv.

$$A_{TM} = \{  \langle M,w\rangle \,;\; M \text{ je TS in } w \in L(M)\}$$

Najprej lahko dokažemo da je prepoznaven. Če simuliramo $M$ na $w$ potem lahko ugotovimo če ga prepozna ne vemo pa če se bo $M$ zaciklal na $w$ kar pomeni da je prepoznaven.

Velja pa da ni odločljiv.

Najprej **dokažemo da obstajajo jeziki ki niso prepoznavni**.

>>[!|dokaz]- Dokaz:
>> Pokažemo lahko da je množica vseh TA števna, saj je $\Sigma^{*}$ števna za katerkoli $\Sigma$ in vemo da za vsak TA obstaja koda.
>> Če pustimo da je $L$ množica vseh jezikov nad $\Sigma$ lahko pokažemo da je $L$ neštevna saj lahko najdemo bijekcijo med $L$ in množico neskončnih dvojiških nizov.
>> Za $\Sigma^{*} = \{s_{0}, s_{1},...,s_{i},...\}$ in jezik $A_{DKA} \in L$ lahko dodelimo karakterističen dvojiški niz ki ima na $i$-tem mestu $0$ ali $1$ glede na to ali je $s_{i} \in A_{TM}$. Torej bi $A_{TM} = \{ s_{3},s_{6},...\}$ imel niz $001001...$. Velja da lahko torej $A_{TM} \in L$ preslikamo v neskončen dvojiški niz in s tem dobimo bijekcijo med obema.


> Sedaj dokažimo da je $A_{TM}$ neodločljiv.
> 
> Naj bo $H$ odločljiv stroj ki sprejme $\langle M,w\rangle$ in sprejme če $w \in L(M)$ ali zavrne če $w \notin L(M)$.
> 
> Hočemo pokazati da tak odločljiv $H$ ne obstaja.
> 
> Začnemo s tem da najdemo neko definicijo stroja $M$ kjer ob nekem vhodu $w$ ne moremo ugotoviti ali mu pripada ali ne.
> 
> Radi bi ugotovili ali obstaja odločilen stroj $D$ ki bi nam za nek vhod dal neko očtino protislovje kot npr. 
> $$D \text{ sprejme } w_{0} \Leftrightarrow D \text{ ne sprejme } w_{0}$$
> 
> To sicer ni delujoč stroj ampak lahko vpeljemo neko dejansko delovanje s tem da vstavimo spremenljivke in poskušamo referencirat naš orginalni stroj $H$. Ta pravi da $H$ ne sprejme $\langle M,w\rangle \Leftrightarrow M$ ne sprejme $w$. 
> 
> 
> $$D \text{ sprejme } \langle D\rangle \Leftrightarrow D \text{ ne sprejme } \langle D\rangle$$
> 
> Lahko že vidimo malo podobnosti.
> 
> Neko tako izjavo bi lahko spremenili v delovanje stroja. Lahko rečemo da $D$ dobi na vhodu neko kodo stroja $\langle M\rangle$ in jo sprejme le če $M$ ne sprejme svoje kode $\langle M\rangle$.
> 
> $$D \text{ sprejme } \langle M\rangle \Leftrightarrow M \text{ ne sprejme } \langle M\rangle$$
> 
>Če $M$ ne sprejme $\langle M\rangle$ velja da $\langle M\rangle \notin L(M)$ kar je natanko definicija našega $H$. 
>
>Veljalo bo da stroj $D$ sprejme $\langle M\rangle$ natanko tedaj ko stroj $H$ ne sprejme $\langle M, \langle M\rangle\rangle$  
>
>Stroj $D$ je torej odločilen, saj je $H$ odločilen po predpostavki.
>
>Naj bo to naša definicija stroja.
>
>$D$ sprejme $\langle M\rangle$ natanko tedaj ko velja da $H$ ne sprejme $\langle M, \langle M\rangle\rangle$.
>
>To pomeni da imamo stroj $D$ ki vzame vhod $\langle M\rangle$ in pogleda ali ga stroj $H$ sprejme. Kot smo videli če v to definicijo vstavimo $D$ dobimo protislovje kar pomeni da $H$ ne more biti odločilen stroj.

$A_{TM}$ pravimo tudi $L_{U}$ oz. **univerzalni jezik** in je neodločljiv, a prepoznaven.

**Komplement univerzalnega jezika** je neprepoznaven. To vemo ker drugače bi univerzalni jezik bil odločljiv. Lahko pa tudi dokažemo s prevedbo na diagonalni jezik.

**Diagonalni jezik** ${L_{D}} = \{ \langle M\rangle \,;\;  \langle M\rangle \notin \,L(M)\,\}$ je neprepoznaven. To lahko preprosto vidimo s tem da ko hočemo preveriti ali $\langle M\rangle$ ne spada v $M$ kjer lahko $M$ simuliramo neskončno dolgo brez da bi vedeli ali se bo ustavil torej ne moremo končati izvajanja in reči da.


**Komplement diagonalnega jezika** je prepoznaven.

> Če je jezik in njegov komplement prepoznaven potem je odločljiv.

***

**Neodločljivost problemov**

Jezik ki je prepoznaven je tudi

$$\text{HALT}_{\text{TM}} =\{  \langle M,w\rangle \,;\; M \text{ je TM in } M \text{ se ustavi na } w \}$$

Če predpostavimo da je odločljiv, potem lahko s prevedbo iz univerzalnega jezika na njega določimo odločljiv stroj za univerzalni jezik kar ni mogoče. 

Torej je $\text{HALT}_\text{TM}$ **prepoznaven**.
***
Znan primer jezika ki je **neprepoznaven** je 

$$E_{TM} = \{ \langle M\rangle \,;\; L(M) = \emptyset  \}$$

To lahko intuitivno preverimo tako da si zaimslimo da stroj sistematično preizkuša vse vhode ampak jih lahko preizkuša v neskončnost saj nikoli ne vemo če bo naslednji vhod v jeziku $M$ kar pomeni da ne moremo zagotoviti ustavitve stroja.

Dokažemo s prevodom $\overline{L_{U}}$ na $E_{TM}$ kje rečemo da se $\langle M,w\rangle$ slika v $M'$ ki simulira $M$ na $w$, kjer $w$ lahko prepozna. Če $w$ prepozna potem rečemo da $M'$ prepozna besedo na vhodu. Drugače ni izhoda. Veljalo bo da če $w$ ne pripada $L(M)$ potem je $L(M')$ prazen in obratno ampak ker $E_{TM}$ lahko prepoznava take stroje bi moral biti $\overline{L_{U}}$ prepoznaven, kar ni.

***

Jezik vseh opisov stroja ki prepozna le tise ki sprejmejo regularne jezike je tudi neprepoznaven.

$$\text{Reg}_{\text{TM}}= \{ \langle M\rangle \,;\; L(M) \text{ je regularen jezik}\}$$

***

$$\text{EQ}_{\text{TM}} = \{ \langle M_{1},M_{2}\rangle \,;\; L(M_{1}) = L(M_{2})  \}$$

je tudi neprepoznaven.





Naj bo $M$ Turingov stroj in $w$ vhodni niz. 

**Sprejemajoča zgodovina izračuna** za $M$ na $w$ je zaporedje konfiguracij $C_1, C_2, \dots, C_l$, kjer je $C_1$ začetna konfiguracija stroja $M$ na $w$, $C_l$ je sprejemajoča konfiguracija stroja $M$ in vsak $C_i$ pravilno sledi iz $C_{i-1}$ po pravilih stroja $M$. 

**Zavračajoča zgodovina izračuna** za $M$ na $w$ je definirana podobno, le da je $C_l$ zavračajoča konfiguracija.

***

Poglejmo si še primer PKP - Postov korespondenčni problem

Podano je zaporedje nizov $(x_{1},y_{1}),...,(x_{k},y_{k})$.
Ali obstaja rezporeditev $(x_{i},y_{i})$, kjer se domine lahko ponavljajo, tako da je konkatenacija levih enaka konkatenaciji desnih - $x_{a_{1}}...x_{a_{k}} = y_{a_{1}}...y_{a_{k}}$. Če obstaja pripadajo jeziku PKP.

Najprej bomo **pokazali da je modificiran PKP** - MPKP, kjer se mora zaporedje začeti z $x_{1}... = y_{1}...$ **neodločljiv** s prevedbo $A_{TM}$ na MPKP.

Torej da **MPKP sprejme podan set domin** mora veljati da **obstaja zaporedje da velja $x_{1}... = y_{1}...$**

Če **predpostaivmo da je MPKP odločljiv** in najdemo prevedbo iz $A_{TM}$ nanj potem bi lahko odločali $A_{TM}$, a ker vemo da to ne gre mora MPKP biti neodločljiv.

*S prevedbo na $A_{TM}$ mislimo da lahko $M,w$ prevedemo v množico domin. Te domine so specifično izračunane tako da če $M$ sprejme $w$ potem lahko iz njih uspešno sestavimo zaporedje. Domine so izbrane vnaprej ampak ker lahko zagotovimo da se ujemajo le če jih sestavimo na specifičen način - po nekih pravilih. To je posledica tega da moramo začeti z določeno domino ki nam zagotavlja neujemanje če ne sledimo pravilom sestavljanja. Ta pravila sestavljanja se bodo izkazala za simulacijo stroja, kjer velja da če sledimo pravilom sestavljana teh končno veliko domin in pridemo do domine ki označuje sprejemno stanje lahko dokončamo zaporedje. Če ne pridemo do domine ki vsebuje sprejemno stanje v naši množici ne bo domine ki lahko zaključi oz. ujame zaporedje. Naša prva domina zagotavlja neujemanje v množici pa imamo še domine ki se lahko znebijo neujemanja ampak le če je uporabljena domina s sprejemnim stanjem.*

Ko sprejmemo nek **$M,w$ ga prevedemo v nek končen nabor domin ki bo vseboval vse funkcije prehoda $M$, ter posebne domine ki delujejo kot zaključevalnik, ob uporabi domine s $q_\text{accept}$ se uporabijo te domine da zaključimo zaporedje**. 

Ob temu naborom domin se bo lahko naš "odločljiv stroj" za MPKP lahko odločil ali je $w$ v $M$ ali ne.

Imamo turingov stroj $M$ in vhodni niz $w = w_{1}...w_{n}$. Z njegovo definicijo sestavimo množico domin.

Prva domina bo predstavljala začetno konfiguracijo

$$(\#, \#q_{0}w_{1}...w_{n}\#)$$

Za vsako prehodno funkcijo $\delta({\color{green}q},a) =  ({\color{green}p},{\color{blue}b},R)$ ali 
$\delta({\color{green}q},a) =  ({\color{green}p},{\color{blue}b},L)$, 
$q \neq q_\text{reject}$,
 imamo domino

$$({\color{green}q}a, {\color{blue}b}{\color{green}p})$$
$$(\color{light}x{\color{green}q}a, {\color{green}p}\color{light}x{\color{blue}b})$$

Ker bomo ob gradnji zaporedja domin gradili dejansko konfiguarcije stroja moramo imeti način da kopiramo stanje iz prejšnje konfiguracije - za vsako črko v abecedi traka dodamo domino.

$$(a,a)$$

Da ločimo konfiguracije dodamo še 

$$(\#,\#)$$

in da simuliramo neskončno praznih simbolov dodamo še

$$(\#,\sqcup\#)$$

![[Pasted image 20260122203231.png]]

Sedaj si lahko predstavljamo da pridemo do $q_\text{accept}$. To pomeni da imamo zgoraj neko prejšnjo konfiguracijo spodaj pa sprejemno konfiguracijo.

![[Pasted image 20260122203619.png]]

Sedaj hočemo končati zaporedje. To dosežemo tako da vse simbole okoli $q_\text{accept}$ odstranimo.

To pomeni da dodamo domini

$$q_\text{accept}a,q_\text{accept}$$
$$aq_\text{accept},q_\text{accept}$$

To pomeni da lahko spodaj odstranimo en simbol zgoraj pa ujemamo s prejšnim stanjem. Na sliki vidmo da imamo $q_\text{accept}0$ spodaj. To pomeni da dodamo $(2,2), (1,1), (q_\text{accept}0,q_\text{accept})...$ s čimer zgoraj ujamemo s spodnjim, ampak v naslednjem se znebimo ničle.

![[Pasted image 20260122204151.png]]

Nazdanje dodamo še domino

$$(q_\text{accept}\#\#,\#)$$

![[Pasted image 20260122204232.png]]

S tem dokončamo zaporedje.

S tem smo dokazali MPCP. Če te domine poskusimo uporabiti s PCP vidimo da $(a,a),...$ in podobne lahko sestavijo validno zaporedje same po sebi.

Da pretvorimo MPCP množico domin v množico domin za PCP mora oblika domin določat da začnemo tako kot pri MPCP. To dosežemo tako da definiramo notacije:


$$\star u = * u_1 * u_2 * u_3 * \dots * u_n $$
$$u \star = u_1 * u_2 * u_3 * \dots * u_n * $$
$$\star u \star = * u_1 * u_2 * u_3 * \dots * u_n *$$

Naj bo prva domina iz MPCP definirana kot $(t,t')_{1}$ in vse druge ki jih dodamo $(t,t')_{2,...}$

Množico domin za PCP definiramo sedaj kot

$$(\star t\,,\star \,t' \star)_{1},$$
$$(\star t\,,t' \star)_{1},$$
$$(\star t\,,t' \star)_{2}$$
$$...$$
$$(*\diamond,\diamond)$$

Vidimo da edina domina ki lahko začne zaporedje je $(\star t\,,\star \,t' \star)_{1}$ *ker je edina ki se začne z istim simbolom.* 
$(*\diamond,\diamond)$ pa imamo zato da lahko dodamo zvezdo še na konec in dokončamo zaporedje.