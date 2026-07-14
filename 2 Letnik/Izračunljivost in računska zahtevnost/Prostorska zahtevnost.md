
![[Pasted image 20260126002600.png]]
Naj bo $M$ DTS ki se ustavi ne vseh vhodih.

**Prostorska kompleksnost** $M$ je $f : \mathbb{N} \rightarrow \mathbb{N}$ kjer je $f(n)$ maksimalno število celiv na traki ki ji h $M$ pregleda za vsak vhod $w$ dolžine $n$.

Če je prostorska kompleksnost $M$ enaka $f(n)$ pravimo da $M$ teče v prostoru $f(n)$.


***
Naj bo $f: \mathbb{N} \rightarrow \mathbb{R}^+$ funkcija. Razredi **prostorske zahtevnosti**, **SPACE($f(n)$)** in **NSPACE($f(n)$)**, so definirani na naslednji način:

Če jezik $L$ odloča **deterministični** Turingov stroj s prostorsko zahtevnostjo $O(f(n))$ potem je

$$L \in \text{SPACE}(f(n))$$

Če jezik $L$ odloča **nedeterministični** Turingov stroj s prostorsko zahtevnostjo $O(f(n))$ potem je

$$L \in \text{NSPACE}(f(n))$$

Izkaže se da je prostor močnejši, saj se ga lahko reciklira.

Velja da je $SAT$ v linearnem prostoru.

$M$ na vhodu $\langle  \phi\rangle$ za vsako določanje vrednosti liateralov, ovrednotimo $\phi$, če je $\phi$ 1 sprejmemo, če nikoli, zavrnemo.

$M$ je očitno v linearnem času saj vsaka iteracija uporablja isto porcijo traka, saj rabimo shraniti le trenutno določen izraz kar se da v $O(n)$ prostoru.

**Savitchev izrek** pravi da za katerokoli funkcijo $f : \mathbb{N} \rightarrow \mathbb{R}^{+}$ kjer je $f(n) \geq n$, $\text{NSPACE}(f(n)) \subseteq \text{SPACE}(f^{2}(n))$
Ideja dokaza je da ob podanih dveh konfiguracijah nedeterminističnega Turingovega stroja (NTM), $c_1$ in $c_2$, skupaj s številom $t$, preverimo, ali lahko NTM pride iz $c_1$ do $c_2$ v največ $t$ korakih z uporabo zgolj $f(n)$ prostora. 

Ta problem imenujemo **problem dosegljivosti** (angl. *yieldability problem*). Z reševanjem problema dosegljivosti, kjer je $c_1$ začetna konfiguracija, $c_2$ sprejemna konfiguracija in $t$ največje število korakov, ki jih nedeterministični stroj lahko porabi, lahko ugotovimo, ali stroj sprejme svoj vhod.

Podamo determinističen, rekurziven algoritem, ki rešuje problem dosegljivosti. Deluje tako, da išče vmesno konfiguracijo $c_m$ in rekurzivno preverja, (1) ali lahko $c_1$ pride do $c_m$ v $t/2$ korakih in (2) ali lahko $c_m$ pride do $c_2$ v $t/2$ korakih. Ponovna uporaba prostora za vsakega od dveh rekurzivnih preizkusov omogoča znaten prihranek prostora.

Ta algoritem potrebuje prostor za shranjevanje rekurzivnega sklada. Vsaka raven rekurzije porabi $O(f(n))$ prostora za shranjevanje ene konfiguracije. Globina rekurzije je $\log t$, kjer je $t$ največji čas, ki ga nedeterministični stroj lahko porabi na katerikoli veji izračuna. Ker velja $t = 2^{O(f(n))}$, je $\log t = O(f(n))$. Od tod sledi, da deterministična simulacija porabi $O(f^2(n))$ prostora.

>[!|hide]- 
> Tukaj je podrobna in tehnična razlaga Savitchevega izreka, razčlenjena po korakih, brez metafor in povzetkov.
> 
> ### 1. Cilj: Od nedeterminizma do determinizma s prostorsko omejitvijo
> 
> Imamo problem, ki ga rešuje **nedeterministični Turingov stroj (NTM)**. Ta stroj uporablja prostor $f(n)$. NTM ima "supermoč": na vsakem koraku lahko ugiba, v katero stanje naj gre. Če obstaja *vsaj en* niz pravilnih ugibanj, ki vodi do rešitve (sprejemnega stanja), rečemo, da stroj sprejme vhod.
> 
> Naš cilj je simulirati ta NTM z **determinističnim Turingovim strojem (DTM)**. DTM ne more ugibati. Mora sistematično preveriti možnosti.
> 
> Naivni pristop bi bil preiskovanje v širino (BFS) ali globino (DFS) po drevesu vseh možnih potez NTM-ja. Težava je v tem, da preiskovanje drevesa zahteva ogromno prostora (za shranjevanje vseh vej ali zgodovine), kar bi preseglo našo omejitev $O(f^2(n))$. Savitchev izrek ponuja pametnejši način, ki prostor žrtvuje za čas, a ostane znotraj $O(f^2(n))$.
> 
> ### 2. Koncept konfiguracije in omejitev časa
> 
> Da bi razumeli algoritem, moramo najprej definirati, kaj točno iščemo.
> 
> **Konfiguracija:**
> Trenutno stanje celotnega stroja v določenem trenutku imenujemo *konfiguracija*. To vključuje:
> 1.  Vsebino traku (ki je omejena na dolžino $f(n)$).
> 2.  Položaj glave na traku.
> 3.  Trenutno notranje stanje stroja.
> 
> Ker je prostor omejen na $f(n)$, lahko zapišemo vsako konfiguracijo kot niz znakov dolžine $O(f(n))$.
> 
> **Največje število korakov ($T$):**
> Ker je prostor omejen, obstaja končno število možnih različnih konfiguracij. Če ima stroj $|Q|$ stanj in $|\Gamma|$ simbolov traku, je število možnih konfiguracij približno $|\Gamma|^{f(n)} \cdot f(n) \cdot |Q|$.
> To pomeni, da če NTM sploh kdaj sprejme vhod, ga mora sprejeti, ne da bi ponovil isto konfiguracijo (sicer bi se zaciklal). Zato vemo, da obstaja maksimalni čas $T$, ki je eksponentno odvisen od prostora:
> $$T = 2^{c \cdot f(n)}$$
> kjer je $c$ konstanta. NTM mora priti od začetne do sprejemne konfiguracije v največ $T$ korakih.
> 
> ### 3. Problem dosegljivosti (Divide and Conquer)
> 
> Namesto da bi simulirali stroj korak za korakom, problem prevedemo v vprašanje:
> **Ali obstaja pot od konfiguracije $c_1$ do konfiguracije $c_2$ v največ $t$ korakih?**
> 
> Savitchev algoritem to rešuje z metodo "deli in vladaj".
> 
> Če želimo priti od $c_1$ do $c_2$ v $t$ korakih, mora nekje na polovici poti obstajati neka vmesna konfiguracija $c_m$. Torej, pot dolžine $t$ razbijemo na dve poti dolžine $t/2$:
> 4.  Pot od $c_1$ do $c_m$ v $t/2$ korakih.
> 5.  Pot od $c_m$ do $c_2$ v $t/2$ korakih.
> 
> Ker je DTM determinističen in ne ve, katera je prava vmesna konfiguracija $c_m$, mora preizkusiti **vse možne veljavne konfiguracije**, ki jih je mogoče zapisati v prostoru $f(n)$.
> 
> ### 4. Deterministični rekurzivni algoritem
> 
> Definirajmo funkcijo `Test(c1, c2, t)`, ki vrne *TRUE*, če lahko NTM pride iz $c_1$ v $c_2$ v največ $t$ korakih.
> 
> Algoritem deluje takole:
> 
> 6.  **Osnovni primer (ustavitveni pogoj):**
>     Če je $t = 1$, preverimo neposredno: Ali sta $c_1$ in $c_2$ enaka? Ali pa stroj v enem koraku preide iz $c_1$ v $c_2$ glede na svoja pravila prehajanja? Če ja, vrni *TRUE*, sicer *FALSE*.
> 
> 7.  **Rekurzivni korak:**
>     Če je $t > 1$, moramo najti vmesno točko.
>     Algoritem zažene zanko čez **vse možne konfiguracije** $c_m$ velikosti $f(n)$:
>     *   Za vsak $c_m$ izvedi naslednje:
>         1.  Rekurzivno pokliči `Test(c1, cm, t/2)`.
>         2.  Če (in samo če) prvi klic vrne *TRUE*, rekurzivno pokliči `Test(cm, c2, t/2)`.
>         3.  Če tudi drugi klic vrne *TRUE*, potem smo našli pot. Vrni *TRUE*.
>     *   Če zanka preteče čez vse možne $c_m$ in ne najde ustreznega, vrni *FALSE*.
> 
> Da bi ugotovili, ali stroj sprejme vhod, pokličemo:
> `Test(začetna_konfiguracija, sprejemna_konfiguracija, T)`
> 
> ### 5. Analiza porabe prostora
> 
> Tu se skriva bistvo izreka. Zakaj to porabi $O(f^2(n))$ prostora?
> 
> Prostor, ki ga potrebuje algoritem, je prostor za shranjevanje **rekurzivnega sklada** (stack). Pri vsakem rekurzivnem klicu moramo shraniti trenutno stanje izvajanja funkcije.
> 
> **A. Prostor na eni ravni rekurzije:**
> Na vsaki ravni rekurzije mora funkcija shraniti:
> *   Argumente ($c_1, c_2, t$).
> *   Trenutno lokalno spremenljivko $c_m$ (vmesno konfiguracijo, ki jo trenutno testira v zanki).
> Ker je vsaka konfiguracija velika $O(f(n))$, ena raven sklada zasede $O(f(n))$ prostora.
> 
> **B. Globina rekurzije:**
> V vsakem koraku razpolovimo čas $t$. Začnemo z maksimalnim časom $T = 2^{O(f(n))}$.
> Kolikokrat moramo deliti $T$ z 2, da pridemo do 1?
> $$\log_2(T) = \log_2(2^{O(f(n))}) = O(f(n))$$
> Globina rekurzije je torej sorazmerna s $f(n)$.
> 
> **C. Skupni prostor:**
> Skupni prostor je produkt globine rekurzije in velikosti posameznega "okvirja" na skladu:
> $$Prostor = (\text{Globina rekurzije}) \times (\text{Velikost enega okvirja})$$
> $$Prostor = O(f(n)) \times O(f(n)) = O(f^2(n))$$
> 
> ### Ključni vidik varčevanja s prostorom
> 
> Zakaj je to bolje od preprostega shranjevanja celotne poti?
> Ko algoritem preverja prvi del poti (od $c_1$ do $c_m$), uporabi sklad do globine $f(n)$. Ko ugotovi, da je ta del poti veljaven, se ta del sklada **sprosti**. Isti pomnilniški prostor se nato **ponovno uporabi** za preverjanje drugega dela poti (od $c_m$ do $c_2$).
> 
> Nikoli ne shranjujemo celotne poti hkrati. Shranjujemo le "križišča" (vmesne konfiguracije $c_m$) na različnih ravneh rekurzije, kar nam omogoča, da eksponentno veliko drevo preiščemo s kvadratno prostorsko zahtevnostjo.

***

**PSPACE** je razred jezikov, ki so odločljivi v polinomskem prostoru na determinističnem Turingovem stroju. Z drugimi besedami:

$$ \text{PSPACE} = \bigcup_{k} \text{SPACE}(n^k) $$

**NPSPACE** je razred jezikov, ki so odločljivi v polinomskem prostoru na nedeterminističnem Turingovem stroju. Z drugimi besedami:

$$ \text{NPSPACE} = \bigcup_{k} \text{NSPACE}(n^k) $$

> Po Savitchevem izreku tako velja $\text{PSPACE} = \text{NPSPACE}$ oz. bolj natančno če je nek $L$ v $\text{NSPACE}(n^{k})$ je $L$ tudi v $\text{SPACE}(n^{2k})$

***

**Odnosi med razredi**

Opazimo, da velja P $\subseteq$ PSPACE, ker stroj, ki deluje hitro, ne more porabiti veliko prostora. Natančneje, za $t(n) \ge n$ lahko vsak stroj, ki deluje v času $t(n)$, porabi največ $t(n)$ prostora, saj lahko stroj v vsakem koraku svojega izračuna obišče največ eno novo celico. Podobno velja NP $\subseteq$ NPSPACE in zato NP $\subseteq$ PSPACE.

Nasprotno pa lahko časovno zahtevnost Turingovega stroja omejimo z vidika njegove prostorske zahtevnosti. 

Za $f(n) \ge n$ ima lahko Turingov stroj (TM), ki porabi $f(n)$ prostora, največ $f(n) 2^{O(f(n))}$ različnih konfiguracij.
 *( Število celic $f(n)$ ) $\cdot |\Sigma|^{f(n)} \cdot |Q|$  *

To pomeni da če nek deterministični stroj gre čez vsako konfiguracijo bo anredil $f(n)2$
Izračun Turingovega stroja, ki se ustavi, ne sme ponoviti iste konfiguracije. Zato mora TM, ki uporablja prostor $f(n)$, delovati v času $f(n) 2^{O(f(n))}$, torej velja PSPACE $\subseteq$ EXPTIME = $\bigcup_k \text{TIME}(2^{n^k})$.


$$\text{P} \subseteq \text{NP} \subseteq \text{PSPACE} = \text{NPSPACE} \subseteq \text{EXPTIME}.$$

Ne vemo, ali je katero od teh vsebovanj dejansko enakost. Morda bo kdo še odkril simulacijo, podobno tisti v Savitchevem izreku, ki bi nekatere od teh razredov združila v isti razred. 