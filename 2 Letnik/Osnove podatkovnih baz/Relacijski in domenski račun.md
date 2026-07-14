


- **Relacijska algebra** in **relacijski račun** sta formalna poizvedovalna jezika.
- **Relacijska algebra** je visokonivojski **postopkovni jezik** (v njem implicitno določimo postopek za pridobitev rezultata).
- **Relacijski račun** je **nepostopkovni ali deklarativni jezik**. Pri njem določimo le, **kaj** nas zanima, ne pa postopka, kako do tega priti.
- Oba jezika sta **formalno ekvivalentna**.
- Jeziki, ki so po moči enakovredni relacijskemu računu, se imenujejo **relacijsko popolni jeziki**.

### 2. Osnove predikatnega računa

Relacijski račun temelji na simbolični logiki, imenovani **predikatni račun prvega reda**.

- **Stavki (trditve):** Sestavljeni so iz predikatov in konstant.
    - **Predikati:** Besede, ki označujejo trditve. So logične funkcije z argumenti (npr. $P(a)$ pomeni, da ima objekt $a$ lastnost $P$).
    - **Konstante:** Besede, o katerih trditve držijo (npr. $a$ v $P(a)$).
    - **Primeri:** $\text{Ženska}(\text{marija})$, $\text{Moški}(\text{janez})$, $\text{SestraBrat}(\text{marija, janez})$.
- **Spremenljivke in kvantifikatorji:** Predikati lahko uporabljajo spremenljivke, katerih vrednosti so kvantificirane.
    - **Univerzalni kvantifikator ($\forall$):** "za vse". Primer: $\forall x. \text{Moški}(x) \lor \text{Ženska}(x)$ (Vsakdo je bodisi moški ali ženska).
    - **Eksistencialni kvantifikator ($\exists$):** "obstaja". Pove, da obstaja vsaj en primerek, za katerega je predikat resničen.
- **Funkcije:** Domene objektov so lahko določene s funkcijami, apliciranimi na objekte. Primer: $\forall x. \text{Moški}(\text{Oče}(x))$ (Oče osebe je moški).
- **Sintaksa in logični operatorji:**
    - Množica vseh $x$, za katere je predikat $P$ resničen: ${x \mid P(x)}$.
    - **Logični operatorji:** IN ($\land$), ALI ($\lor$), NEGACIJA ($\neg$).

---

### 3. N-terični relacijski račun (Tuple Relational Calculus - TRC)

Temelji na uporabi **n-teričnih spremenljivk**, kjer je domena spremenljivke določena z relacijo (dovoljene vrednosti so n-terice ali vrstice relacije).

- **Splošna oblika zapisa:** $${t \mid \text{COND}(t)}$$ Kjer $t$ predstavlja n-terično spremenljivko, $\text{COND}(t)$ pa nabor pogojev.
- **Proste in vezane spremenljivke:**
    - **Proste spremenljivke:** Lahko so le tiste, ki so definirane na levi strani znaka $\mid$.
    - **Vezane spremenljivke:** Spremenljivke, ki so kvantificirane z $\forall$ ali $\exists$.
- **Primeri uporabe:**
    - Vsi podatki o artiklih z zalogo $< 3$: ${A \mid \text{Artikel}(A) \land A.\text{zaloga} < 3}$.
    - Samo naziv teh artiklov: ${A.\text{naziv} \mid \text{Artikel}(A) \land A.\text{zaloga} < 3}$.
$$ $$

Uporaba $\exists$: Artikli v skladišču v Ljubljani: 

$${A \mid \text{Artikel}(A) \land (\exists S)(\text{Skladišče}(S) \land (A.\text{skladišče} = S.\text{ID}) \land (S.\text{kraj} = \text{'Ljubljana'}))}$$
$$ $$

Uporaba $\forall$: Računi, kjer imajo vse postavke ceno $> 1000$ EUR: 
      
$${R \mid \text{Račun}(R) \land (\forall P)(\text{Postavka}(P) \land (R.\text{ID} = P.\text{račun}) \land (P.\text{cena} > 1000))}$$
$$ $$

Z uporabo implikacije ($\implies$): 

$${R \mid \text{Račun}(R) \land (\forall P)((\text{Postavka}(P) \land (R.\text{ID} = P.\text{račun})) \implies (P.\text{cena} > 1000))}$$
$$ $$

#### Pravila za dobre in varno definirane izraze v TRC

- **Dober izraz:** Je nedvoumen in smiseln. Splošna oblika: ${S_1.a_1, S_2.a_2, \dots, S_n.a_n \mid F(S_1, S_2, \dots, S_m)}$, kjer je $m \ge n$.
- **Atomi za gradnjo formul ($F$):**
    
    1. $R(S_i)$: $S_i$ je n-terična spremenljivka v relaciji $R$.
    2. $S_i.a_1 \theta S_j.a_2$: primerjava atributov dveh spremenljivk.
    3. $S_i.a_1 \theta c$: primerjava atributa s konstanto.
    
    - $\theta$ je primerjalni operator: $<, \le, >, \ge, =, \neq$.
- **Rekurzivna gradnja formul:** Atomi so formule; če sta $F_1, F_2$ formuli, so tudi $F_1 \land F_2, F_1 \lor F_2, \neg F_1$ formule; če je $F$ formula s prosto spremenljivko $X$, sta $(\exists X)(F)$ in $(\forall X)(F)$ tudi formuli.
- **Varni izraz:** Preprečuje neskončne množice. Vse vrednosti rezultata morajo biti iz domene izraza $\text{dom}(E)$ (vrednosti, ki se pojavijo kot konstante ali v zapisih relacij v izrazu).
    - _Primer nevarnega izraza:_ ${A \mid \neg(\text{Artikel}(A))}$.

---

### 4. Domenski relacijski račun (Domain Relational Calculus - DRC)

Spremenljivke se nanašajo na **domene atributov** (posamezne vrednosti v stolpcih).

- **Splošna oblika zapisa:** $${d_1, d_2, \dots, d_n \mid F(d_1, d_2, \dots, d_m)}$$ Kjer so $d_i$ domenske spremenljivke in $F$ formula.
- **Atomi:**
    - $R(d_1, d_2, \dots, d_n)$: $R$ je relacija, $d_i$ so domenske spremenljivke.
    - $d_i \theta d_j$ ali $d_i \theta c$.
- **Gradnja izrazov:** Enaka rekurzivna pravila kot pri TRC.
- **Primeri:**
    - Imena hotelov v Ljubljani: ${hName \mid \exists(hNo, hAddress)(\text{Hotel}(hNo, hName, hAddress) \land hAddress = \text{'Ljubljana'})}$.
    - Hoteli s prosto dvoposteljno sobo ($\text{type}=2$): $${hName \mid \exists hNo, hAddress, rNo, rPrice (\text{Hotel}(hNo, hName, hAddress) \land \text{Room}(rNo, hNo, 2, rPrice, \text{true}))}$$.

---

### 5. Primerjava in moč jezikov

- **N-terični relacijski račun (Edgar F. Codd, 1972):** Osnova za jezik **SQL**.
- **Domenski relacijski račun (M. Lacroix in A. Pirotte, 1977):** Osnova za jezik **QBE** (Query-by-Example).
- **Enakovrednost:** Ob uporabi varnih izrazov so relacijska algebra, TRC in DRC po moči **enakovredni**.
    - Vse, kar izrazimo v relacijski algebri, lahko zapišemo v TRC ali DRC in obratno (za varne izraze).
- **De Morganova zakona** za pretvorbo izrazov:
    - $\neg(A \land B) = \neg A \lor \neg B$
    - $\neg(A \lor B) = \neg A \land \neg B$

### 6. Primerjalni prikaz poizvedbe

_Poizvedba: Izpiši nazive hotelov s prosto dvoposteljno sobo (type=2)._

- **TRC:** ${H.\text{hotelName} \mid \text{Hotel}(H) \land (\exists R)(\text{Room}(R) \land H.\text{hotelNo}=R.\text{hotelNo} \land R.\text{type}=2 \land R.\text{free} = \text{true})}$.
- **DRC:** ${hName \mid \exists hNo, hName, hAddress, rNo, rPrice (\text{Hotel}(hNo, hName, hAddress) \land \text{Room}(rNo, hNo, 2, rPrice, \text{true}))}$.
- **Relacijska algebra:** $\pi_{\text{hotelName}}(\sigma_{\text{type}=2 \land \text{free}=\text{true}}(H \bowtie_{\text{hotelNo}=\text{hotelNo}} R))$.
- **SQL:** `SELECT h.hotelName FROM Hotel h, Room r WHERE h.hotelNo=r.hotelNo AND r.type=2 AND r.free=true`.

