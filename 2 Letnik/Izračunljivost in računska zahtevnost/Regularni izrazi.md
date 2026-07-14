
**Regularni izrazi**

$R$ je **regularni izraz** če velja da je $R$
- $a$ za nek $a$ v $\Sigma$
- $\varepsilon$
- $\emptyset$
- $R_{1} + R_{2}$
- $R_{1}R_{2}$
- $R_{1}^{*}$
  
Potem pa lahko še definiramo $R^{+}$ kot $RR^{*}$ in $R^{k}$ kot staknjenje $k$ $R$-jev.

Veljajo naslednje identitete:
- $R + \emptyset = R$
- $R \varepsilon = R$
- $R + \varepsilon$ je nova množica ki bsebuje vse nize iz jezika $R$ in prazen niz
- $R \emptyset = \emptyset$ je uničvelen element

Za naslednji izrek potrebujemo PNKA oz. posplošen nedeterminističen končni avtomat kjer lahko za prehodne funkcije uporabljamo regularne izraze kot vhodne spremenljivke.

>Jezik je regularen natanko tedaj ko je jezik regularnega izraza. 
>>[!|dokaz]- Dokaz:
> > 
> >Smer ($\Leftarrow$): Vsak regularni izraz opisuje regularen jezik
> >
> > **Cilj:** Če imamo regularni izraz $R$, moramo dokazati, da obstaja končni avtomat, ki sprejme $L(R)$.
> > 
> > **Dokaz (z indukcijo po zgradbi izraza - Thompsonova konstrukcija):**
> > Dokazujemo, da za vsak regularni izraz lahko zgradimo $\epsilon$-NKA (nedeterministični končni avtomat z $\epsilon$-prehodi). Ker vemo, da je $\epsilon$-NKA enakovreden DKA (determinističnemu avtomatu), je jezik regularen.
> > 
> > 2.  **Osnovni primeri:**
> >     *   $\emptyset, \epsilon, a$ (kjer je $a \in \Sigma$): Za vsakega od teh je trivialno zgraditi preprost avtomat.
> > 2.  **Induktivni korak:** Predpostavimo, da za izraza $R_1$ in $R_2$ že imamo avtomata $M_1$ in $M_2$.
> >     *   **Unija ($R_1 + R_2$):** Zgradimo nov avtomat z novim začetnim stanjem, ki ima $\epsilon$-prehod na začetni stanji $M_1$ in $M_2$.
> >     *   **Stik ($R_1 R_2$):** Povežemo končna stanja $M_1$ z začetnim stanjem $M_2$ preko $\epsilon$-prehodov.
> >     *   **Kleenejeva zvezdica ($R_1^*$):** Dodamo $\epsilon$-prehode iz končnih stanj $M_1$ nazaj na začetek in omogočimo "preskok" celotnega avtomata (za prazno besedo).
> > 
> > **Zaključek:** Ker lahko za vsak operater zgradimo $\epsilon$-NKA, je jezik regularnega izraza regularen.
> > 
> > ---
> > 
> > Smer ($\Rightarrow$): Vsak regularen jezik se da opisati z regularnim izrazom
> > **Cilj:** Če je jezik $L$ regularen (torej ga sprejme nek DKA), zanj obstaja regularni izraz.
> > 
> > **Dokaz (metoda eliminacije stanj ali GNFA):**
> > Ker je $L$ regularen, obstaja DKA $A$, ki ga prepozna. Ta DKA pretvorimo v regularni izraz s postopkom posplošenega NKA (GNFA), kjer so prehodi označeni z regularnimi izrazi namesto s črkami.
> > 
> > 1.  **Priprava:** DKA pretvorimo v GNFA tako, da dodamo novo začetno stanje (z $\epsilon$-prehodom v staro) in novo končno stanje (z $\epsilon$-prehodi iz vseh starih končnih stanj).
> > 2.  **Eliminacija:** Izbiramo stanja $q_{k}$ (ki niso začetno ali končno) in jih odstranjujemo enega za drugim.
> > 3.  **Posodobitev prehodov:** Ko odstranimo stanje $q_{k}$, moramo ohraniti poti, ki so tekle skozi njega. Če imamo prehod iz stanja $q_i$ v $q_j$ skozi $q_k$, posodobimo neposredni prehod $q_i \to q_j$ po formuli:
> >     $$R_{ij}' = R_{ij} + R_{ik} (R_{kk})^* R_{kj}$$
> >     *(Pomen: Stara pot ali (pot do k, zanka na k kolikokrat želimo, pot iz k)).*
> > 4.  **Rezultat:** Na koncu ostaneta le začetno in končno stanje z enim samim prehodom med njima. Oznaka na tem prehodu je iskani regularni izraz.
> > 
> > **Zaključek:** Za vsak DKA obstaja ekvivalenten regularni izraz.
> > 
> > ---
> > 
> > **Končni sklep:** Ker veljata obe smeri, je jezik regularen natanko tedaj, ko ga opiše regularni izraz.


Definirajmo še PNKA kot 5-terico $M = (Q, \Sigma , \delta, q_{\text{start}}, q_\text{accept})$, kjer je 
- $Q$ končna množica vseh stanj
- $\Sigma$ je vhodna abeceda
- $\delta : (Q- \{ q_\text{accept}\}) \times (Q - \{ q_\text{start} \}) \rightarrow R$ : je prehodna funkcija, kjer je $R$ množica vseh regulranih izrazov nad $\Sigma$
- $q_\text{start}$ je začetno stanje
- $q_\text{end}$ je končno stanje

PNKA sprejme besedo natanko tedaj ko velja da obstaja zaporedje stanj $q_{0},...,q_{n}$ tako da za besedo $w = w_{1}...w_{n}$ velja
- $q_{0}  = q_\text{start}$
- $q_{k} = q_\text{accept}$
- za vsak $i$ je $w_{i} \in  L(R_{i})$, kjer je $R_{i}=\delta(q_{i-1}, q_{i})$ oz. z drugimi besedami $R_{i}$ je izraz puščici med $q_{i-1}$ in $q_{i}$ 

$w_{i}$ je lahko prezen niz
