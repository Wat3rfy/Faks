

**Neregularni jeziki**

**Neregularni jeziki** so jeziki ki jih ne moremo izraziti s končnimi avtomati. Ponavadi izhajajo iz dejstva da rabimo slediti neskončno stanjem

Velja par ključnih trditev
- Komplement ohranja neregularnost
- Unija ni nujno neregularna $A \cup A^{C}$ kjer je $A$ neregularen da regularni jezik vseh nizov.
- Presek ni zaprt ker lahko dobimo prazno množico kar je regularen jezik.
- **Če mešamo regularen in neregularen jezik preko unije potem je neregularen.**

>**Lema o napihovanju**
>$$\exists n \geq 1 : \forall w \in L , |w| \geq n $$ $$ \exists xyz = w , |xy| \leq n, |y| \geq 1 : \forall i\geq 0 : xy^{i}z \in L$$
>Predpostavimo DKA ki sprejme $L$. Potem lahko za $n$ vzamemo število stanj v avtomatu.
>
>Pokažemo da je vsaka beseda velikosti vsaj $n$ lahko razdeljena in napihnjena
>
>Če nobena beseda ni velikosti $n$ potem velja da ne obstaja taka beseda in izrek postane prazno izpolnjen, ker pogoji oz. trditve veljajo za vse te besede - ki jih ni.
>
>Če je beseda dolžine vsaj $n$ recimo $N$ potem vemo da mora iti čez $N+1$ stanj kjer je zadnje sprejemno. Ker je $N+1 \geq n$ mora veljati da se je neko stanje ponovilo *(Dirichletovo načelo)*. 
>Naj bo $q$ stanje ki se ponovi. Besedo razdelimo na $x$ del besede ki pride do $q$, $y$ del besede s katerim pridemo nazaj v $q$ (ker se $q$ ponovi je $|y| \geq 1$ $\Rightarrow$ ker imamo $n$ stanj moramo do prve ponovitve stanja priti v največ $n$ korakih (od prvega do $n$ v $n-1$ $+ 1$ prva ponovitev preko $y$) : $|xy| \leq n$), $z$ del besede s katerim pridemo v končno stanje. Ker je $y$ del ki nas iz $q$ pripelje v $q$ ga lahko spustimo ali pa ponovimo poljubnokrat. Torej velja $xy^{i}z \in L; \forall i$

Definiramo relacijo 

$$L \subset  \Sigma^{*}$$ 
$$  x,y \in \Sigma^{*}$$
$$x \sim_{L} y \Leftrightarrow \forall z \in \Sigma^{*} : xz \in L \Leftrightarrow yz \in L$$ 

ki pravi da sta $x$ in $y$ ekvivalentna saj za vsak $z$ velja da sta še vedno v jeziku. 

Iz nje lahko določimo pripadaoče ekvivalenčne razrede oz. množice vseh nizov ki so v relaciji. Iz množice lahko izberemo nek element in ga vzamemo kot predstavnika - zapišemo $[x]$.

*Ekvivalenčne razrede razlikujemo po nizih $z$ za katere dobimo različne izide sprejemanje/zavračanje.*

>**Myhill-Nerode izrek**
>Jezik je regularen natanko tedaj ko je število ekvivalenčnih razredov relacije končno.
>Število končnih stanj v minimalnem DKA je enako številu ekvivalenčnih razredov.
Tukaj je dokaz izreka Myhill-Nerode v obliki zveznega besedila.
> >[!|dokaz]+ Dokaz:
> >
> > 
> > Oznaka $[x]$ v predstavlja ekvivalenčni razred niza $x$ glede na relacijo $\sim_L$.
> > 
> > **Dokaz smeri ($\Rightarrow$): Če je $L$ regularen, je število ekvivalenčnih razredov končno**
> > 
> > Predpostavimo, da je jezik $L$ regularen. To pomeni, da obstaja deterministični končni avtomat (DKA) $A = (Q, \Sigma, \delta, q_0, F)$, ki prepozna ta jezik. Na podlagi tega avtomata lahko vpeljemo novo relacijo $\sim_A$, kjer sta dva niza $x$ in $y$ v relaciji, če nas branje obeh nizov iz začetnega stanja pripelje v isto stanje avtomata, torej $\delta(q_0, x) = \delta(q_0, y)$. Ker je množica stanj $Q$ končna, ima relacija $\sim_A$ končno mnogo ekvivalenčnih razredov, in sicer največ toliko, kolikor je stanj v avtomatu.
> > 
> > Pokazati moramo povezavo z relacijo $\sim_L$. Če sta niza $x$ in $y$ v relaciji $\sim_A$, se avtomat po branju obeh nahaja v istem stanju $q$. Če na to stanje dodamo poljuben niz $z$, bo avtomat za vhoda $xz$ in $yz$ končal v istem stanju $\delta(q, z)$. To končno stanje je bodisi sprejemno bodisi nesprejemno, kar pomeni, da niz $xz$ pripada jeziku $L$ natanko tedaj, ko jeziku $L$ pripada niz $yz$. Po definiciji to pomeni, da velja $x \sim_L y$. Ugotovimo torej, da relacija $\sim_A$ implicira relacijo $\sim_L$, kar pomeni, da so ekvivalenčni razredi relacije $\sim_A$ vsebovani v razredih relacije $\sim_L$. Posledično je število ekvivalenčnih razredov $\sim_L$ manjše ali enako številu razredov $\sim_A$. Ker je slednje končno, je tudi število ekvivalenčnih razredov $\sim_L$ končno.
> > 
> > **Velja da je število ekvivalenčnih razredov manjše ali enako številu stanj oz. je število stanj večje ali enako številu ekv. razredov.** Sedaj moramo dokazati le še minimalnost oz. da obstaja DKA s številom stanj kot je ekvivalenčnih razredov in ker je to spodnja meja za število stanj mora biti to minimalni avtomat. 
> > 
> > **Dokaz smeri ($\Leftarrow$): Če je število ekvivalenčnih razredov končno, je $L$ regularen**
> > 
> > Za dokaz v drugo smer predpostavimo, da ima relacija $\sim_L$ končno število ekvivalenčnih razredov. Konstruiramo lahko DKA, kjer so stanja ravno ti ekvivalenčni razredi. Množico stanj $Q'$ definiramo kot množico vseh razredov $\{[x] \mid x \in \Sigma^{*}\}$. Začetno stanje je razred, ki vsebuje prazen niz, $[\epsilon]$. Množica končnih stanj $F'$ pa vsebuje tiste razrede $[x]$, za katere velja $x \in L$. Ta definicija končnih stanj je smiselna, saj iz definicije relacije sledi: če je $x \in L$ in $x \sim_L y$, potem je tudi $y \in L$ (če vzamemo $z=\epsilon$).
> > 
> > Prehodno funkcijo definiramo s predpisom $\delta'([x], a) = [xa]$. Da je ta definicija veljavna, moramo preveriti neodvisnost od izbire predstavnika. Če velja $x \sim_L y$, mora veljati tudi $xa \sim_L ya$. To lastnost imenujemo desna invariantnost in sledi neposredno iz definicije relacije $\sim_L$: če sta $x$ in $y$ nerazločljiva glede na poljuben podaljšek $z$, sta nerazločljiva tudi, če je prvi znak tega podaljška $a$. Avtomat je tako dobro definiran. Z indukcijo je enostavno videti, da avtomat po branju niza $w$ konča v stanju $[w]$. Ker smo končna stanja definirali kot tista, ki vsebujejo nize iz $L$, avtomat sprejme niz $w$ natanko tedaj, ko je $w \in L$. Ker smo uspeli konstruirati končni avtomat, je jezik $L$ regularen.
> > >[!|hide]- Dodatna razlaga
> > > ### Kaj je problem?
> > > Ko definiramo funkcijo na **ekvivalenčnih razredih** (kot je $[x]$), imamo vedno isto težavo:
> > > Razred $[x]$ je "vreča", v kateri je veliko različnih nizov (npr. $x$, $y$, $u$ ...). Vsi ti nizi predstavljajo **isto stanje**.
> > > 
> > > Definicija prehodne funkcije pravi:
> > > $$ \delta'([x], a) = [xa] $$
> > > 
> > > Tukaj smo za izračun rezultata uporabili predstavnika $x$.
> > > **Vprašanje:** Kaj pa, če bi iz te iste vreče potegnili drug niz, recimo $y$ (torej velja $[x] = [y]$ oz. $x \sim_L y$)? Ali bi nas definicija pripeljala v **isto** ciljno stanje ali v neko drugo?
> > > Če bi nas pripeljala v drugo stanje ($[xa] \neq [ya]$), potem funkcija **ni** dobro definirana (saj za isto vhodno stanje dobimo dva različna rezultata).
> > > 
> > > ### Kaj dokaže slika?
> > > Da je funkcija dobro definirana, moramo dokazati:
> > > **Če sta $x$ in $y$ v istem razredu ($x \sim_L y$), potem morata biti tudi $xa$ in $ya$ v istem razredu ($xa \sim_L ya$).**
> > > 
> > > Postopek na sliki to stori takole:
> > > 
> > > 1.  **Predpostavka:** Vzamemo dva niza, ki sta "nerazločljiva" (ekvivalentna): $x \sim_L y$. To pomeni, da za *katerikoli* podaljšek $z$ velja: $xz \in L \iff yz \in L$.
> > > 2.  **Korak:** Pustimo, da avtomat prebere znak $a$. Dobimo niza $xa$ in $ya$.
> > > 3.  **Test:** Ali sta tudi $xa$ in $ya$ "nerazločljiva"? Preverimo s poljubnim podaljškom $w$.
> > >     *   Ali je $(xa)w \in L \iff (ya)w \in L$?
> > > 4.  **Trik (asociativnost):** To je isto kot vprašanje:
> > >     *   Ali je $x(aw) \in L \iff y(aw) \in L$?
> > > 5.  **Zaključek:** Ker sta bila $x$ in $y$ na začetku nerazločljiva za **vse** podaljške, sta nerazločljiva tudi za specifičen podaljšek $aw$.
> > >     *   Torej velja $xa \sim_L ya$.
> > > 
> > > ### Povzetek
> > > Ker smo dokazali, da iz $x \sim_L y$ sledi $xa \sim_L ya$, to pomeni:
> > > $$ [x] = [y] \implies [xa] = [ya] $$
> > > $$ [x] = [y] \implies \delta'([x], a) = \delta'([y], a) $$
> > > 
> > > To pomeni, da ni važno, kateri niz izberemo za predstavnika stanja – rezultat (naslednje stanje) bo vedno enak. **Funkcija je dobro definirana.**
> > 
> > **Dokaz o minimalnosti avtomata**
> > 
> > Izrek trdi tudi, da je število stanj v minimalnem DKA enako številu ekvivalenčnih razredov relacije $\sim_L$. V drugem delu dokaza smo konstruirali avtomat, ki ima natanko toliko stanj, kot je ekvivalenčnih razredov $\sim_L$, kar nam da zgornjo mejo za velikost minimalnega avtomata. V prvem delu dokaza pa smo videli, da za vsak poljuben avtomat, ki prepozna $L$, velja, da je število njegovih stanj večje ali enako številu ekvivalenčnih razredov $\sim_L$. To pomeni, da noben avtomat ne more imeti manj stanj od števila ekvivalenčnih razredov. Sledi, da je avtomat, zgrajen na ekvivalenčnih razredih, minimalen.