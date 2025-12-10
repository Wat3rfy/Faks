
V teoriji računljivosti uporabljamo idealiziran računalnik, imenovan **računski model** (*computational model*). 

Obstaja jih več odvisno od potrebovanih lastnosti.

Začnemo z najpreprostejšim modelom - **končni avtomat** (*finite state machine* ali *finite automaton*).

**Končni avtomat** je model račnunalnika z močno omejenim pomnilnikom.

Končni avtomat lahko predstavimo z diagramom stanj. Sestavljen je iz začetnih stanj, vmesnih stanj in končnih oz sprejemnih stanj. Med njimi so puščice - prehodi.

Če dobimo nek vhod kot je 1101 dobimo izhod kot je sprejetost ali zavrnitev. Pravimo da je izhod tipe ja/ne. Ko pridemo do konca pogledamo če smo v končnem stanju - če smo vrnemo ja drugače ne.


Končni avtomat definiramo kot 5-terico $M = (Q,\Sigma, \delta, q_{0}, F)$, kjer so
- $Q \text{ : končna množica vseh stanj}$
- $\Sigma : \text{ končna množica simbolov oz. vhodna abeceda}$
- $\delta : Q \times \Sigma \rightarrow Q : \text{prehodna funkcija}$
- $q_{0} \in Q : \text{ začetno stanje}$
- $F \subset  Q : \text{ množica končnih stanj}$

Lahko uprabljamo tudi notacijo $\langle \text{objekt}\rangle$, kjer to predstavlja nek simbol iz abecede.

Iz vskaega stanja pelje natanko ena puščica za vsak simbol iz abecede. Torej mora biti v DKA Točno $|Q| \cdot |\Sigma|$.

Če je $A$ jezik ki jih avtomat $M$ sprejme pravimo da je $A$ jezik $M$ oz. $L(M) = A$.
Avtomat vedno sprejeme natanko en jezik.

> Imamo $M  = (Q, \Sigma, \delta, q_{0}, F)$ in $w = w_{1}...w_{n}$ je  niz sestavljen iz abecede $\Sigma$. $M$ sprejme $w$ če velja da obstaja zaporedje stanj $r_{0},...,r_{n}$ v $Q$ da velja
> 
> $$r_{0} = q_{0}$$
> $$\delta(r_{i},w_{i+1}) = r_{i+1} \,;\; \forall i \in \{ 0,...n-1\}$$
> $$r_{n} \in F$$
> 
> Pravimo da $M$ sprejme jezik $A$ če je $A = \{ w \,;\; M \text{ sprejme } w\}$


> Definirajmo funkcije $\delta' : Q \times \Sigma^* \to Q$
> 
> 1. ${\delta'}(q, \varepsilon) = q$
> 2. ${\delta'}(q, xa) = \delta({\delta'}(q, x), a) ; a \in \Sigma, x \in \Sigma^*$
> 
> Jezik končnega avtomata pa bo tako
> 
> $$L(M) = \{ w \in \Sigma^{*} \,;\; \delta' (q_{0},w) \in  F\}$$

Jezik je **regularen** če obstaja končni avtomat ki ga sprejme.

Konstrukcija končnega avtomata temelji na prepoznavanju nekih končno mnogih stanj med katerimi moramo razločevati npr. sodost lihost simbola, ostanek pri deljenju simbola, kateri so trenutni končni znaki, pojavitev števila zaporednih črk,...

Nad ragularnimi jeziki definiramo regularne operacije **unija, konkatenacija in zvezda**:
- $A \cup B = \{ x \;;\; x \in A \lor x \in B\}$
- $A \circ B = \{ xy \;;\; x \in A \land y \in  B \}$
- $A^{*} = \{ x_{1}x_{2}...x_{k} \,;\;k \geq 0 \land x_{i}\in A\}$

Poleg teh operacij ohranjajo regularnost tudi
- Presek $L_{1} \cap L_{2}$
- Komplement $L^{C}$
- Razlika $L_{1}\backslash L_{2}$
- Obrat $L^{R}$
- Homomorfizem $f(L)$

$A^{*}$ vedno vsebuje $\varepsilon$.

>Unija, konkatenacija in zvezda so zaprte operacije za regularne jezike.
>>[!|dokaz]+ Dokaz:
>> Za dokaz uporabimo nedeterministične končne avtomate, kjer rečemo da za $L_{1}$ in $L_{2}$ obstajata avtomata $M_{1}$ in $M_{2}$.
>> Za unijo lahko definiramo novo začetno stanje in povežemo preko $\varepsilon$ z začetnimi stanji $M_1$ in $M_{2}$. 
>> Za konkatenacijo vzamemo $M_1$ in iz vsakega končnega stanja dodamo $\varepsilon$ prehod v začetno stanje $M_{2}$. Sedaj so sprejemna stanja le še $M_2$.
>> Za zvezdo ustvarimo novo začetno stanje ki je hkrati sprejemno, dodamo epsilon prehod iz novega začetnega tanja v staro začetno stanje $M_{1}$ in iz vbseh starih sprejemnih stanj dodamo $\varepsilon$ prehod v staro začetno stanje $M_{1}$.


**Nedeterministični končni avtomati** so avtomati kjer velja da lahko iz vsakega stanja gremo v več stanj za nek vhod. Za sprejemanje besede mora veljati da obstaja vsaj 1 pot do končnega stanja, teh je lahko več, dopuščamo pa tudi $\varepsilon$-prehode kar so prehodi brez vhoda.

Velja da je NKA 5-terica $M = (Q, \Sigma, \delta, q_{0}, F)$
kjer velja vse enako kot pri DKA le da je 
$\delta : Q \times \Sigma   \rightarrow P\{ Q\}$

$\delta$ lahko vrne prazno množico kot izhod kar ne pomeni da smo sprejeli stanje temveč da je pot umrla.

NKA $N = (Q, \Sigma, \delta, q_{0}, F)$ sprejme $w = y_{1}...y_{n}, y_{i} \in \Sigma_\varepsilon$ natanko tedaj ko velja da je 
- $r_{0} = q_0$
- $r_{i+1}\in  \delta(r_{i} , y_{i+1}) \,;\; i \in \{ 0,...,n-1\}$ 
- $r_{n} \in  F$

Pravimo da je prehodna funkcija oblika

1. $$\delta' (q,\varepsilon) = \{ q\}$$
2. $$\delta' (q,xa) = \bigcup_{p \in  \delta'(q,x)} \delta(p,a)$$


Jezik NKA potem definiramo
$$L(M) = \{ w \in \Sigma^{*} \,;\; \delta'(q_{0},w) \cap F \neq \emptyset\}$$



Če definiramo še $\varepsilon$-NKA kot NKA kjer v abecedo vključimo še prazen niz.

Definirajmo še $\varepsilon$ zaprtje nekega stanja kot množica vseh stanj ki jih lahko dosežemo iz nekega stanja preko $\varepsilon$ prehodov oz. preko praznih nizov.

Za vsako stanje velja da preko praznega niza pridemo nazaj vanj oz. je implicitno.

> Velja, da za vsak NKA obstaja ekvivalenten DKA. To dosežemo s **podmnožično konstrukcijo**, kjer množico trenutnih stanj NKA obravnavamo kot eno stanje DKA. Če ima NKA $n$ stanj, jih ima DKA v najslabšem primeru $2^n$.
>>[!|dokaz]- Dokaz:
> > **Smer DKA $\Rightarrow$ NKA:** Trivialno, saj je vsak DKA le poseben primer NKA (brez nedeterminizma in $\epsilon$-prehodov).
> >
> > **Smer NKA $\Rightarrow$ DKA:**
> > Konstruiramo DKA $M$ iz NKA $N$:
> > 1. **Stanja:** Množica stanj $M$ je **potenčna množica** stanj $N$ (oznaka $2^{Q_N}$). Vsako stanje v DKA torej predstavlja *množico* stanj iz NKA.
> > 2. **Začetno stanje:** Vsebuje začetno stanje $N$ in vsa stanja, dosegljiva z $\epsilon$-prehodi ($\epsilon$-zaprtje).
> > 3. **Prehodi:** Za stanje $R = \{q_i, \dots\}$ (ki je množica stanj NKA) in simbol $a$ je prehod unija vseh možnih prehodov v NKA:
> >    $$\delta_{M}(R, a) = \bigcup_{q \in R} \delta_{N}(q, a)$$
> > 4. **Končna stanja:** So tiste podmnožice v $M$, ki vsebujejo **vsaj eno** končno stanje iz $N$.
> >
> > Tak DKA simulira izvajanje NKA tako, da sledi vsem možnim potem hkrati. Beseda je sprejeta, če se simulacija konča v množici, ki vsebuje končno stanje.

Jezik je regularen natanko tedaj, ko ga prepozna nek nedeterministični končni avtomat.


