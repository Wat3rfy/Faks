
**Konetkstno neodvisna gramatika**

Množica jezikov ki se da zapisati s KNG imenujemo kontekstno neodvisni jeziki. Vsebujejo vse regularne jezike in druge.

Gramatika je zgrajena iz **pravil nadomeščanja** oz. **produkcij**. Sestavljeno je iz simbola, puščice in niza. Simbol je **spremenljivka**, niz pa je sestalvjen iz spremenljivk in drugih simbolov imenovani **terminali**.
Ena spremenljivka je določena kot **začetna spremenljivka**.

Vsi nizi generirani s produkcijami so jezik gramatike. Vsak jezik ga lahko generira KNG se imenuje **kontekstno neodvisen jezik**.

**Kontekstno neodvisna gramtika** je $G = (V, \Sigma, R, S)$ kjer 
- $V$ je končna množica spremenljivk
- $\Sigma$ je končna množica terminalov disjuktna z $V$
- $R$ je končna množica pravil sestavljenih iz spremenljivke in niza spremenljivk in terminalov
- $S \in  V$ je začetna spremenljivka

Če so $u,v,w$ nizi spremenljivk in terminalov in je $A \rightarrow w$ pravilo gramatike pravimo da $uAv$ daje $uwv$. 

Pravimo da se $u$ izpelje v $v$ zapisano $u \stackrel{*}{\Rightarrow} v$, če velja $u = v$ ali če obstaja zaporedje $u_1, u_2, \dots, u_k$ za $k \ge 0$, tako da velja:
$$u \Rightarrow u_1 \Rightarrow u_2 \Rightarrow \dots \Rightarrow u_k \Rightarrow v.$$

**Jezik gramatike** je $\{w \in \Sigma^* \mid S \stackrel{*}{\Rightarrow} w\}$.

Če lahko gramatika generira nek niz na vsaj dva načina rečemo da je **dvoumna**. Natančneje najprej definiramo **levo izpeljavo** za katero velja da na vsakem koraku izpeljave niza $w$ v neki gramatiki $G$ nadomestimo najbolj levo spremenljivko.
Niz $w$ je izpeljan **dvoumno** če ima vsaj 2 različni levi izpeljavi.
Gramatika je **dvoumna** če je nek niz generiran **dvoumno**.

Ponavadi lahko pretvorimo dvoumno gramatiko v nedvoumno ampak nekatere so lahko le **dvoumne**. Tem pravimo **izhodiščno dvoumne**.

Poznamo Chomskyjevo normalno obliko kjer je vsako pravilo oblike
$$A \rightarrow BC$$
$$A \rightarrow a$$
Dovolimo $A \rightarrow \varepsilon$ če je $A$ začetna spremenljivka. $B,c$ ne smeta biti začetni.



**Skladovni avtomati (Pushdown Automata)**

Skladovni avtomati (PDA) so nov računski model, ki je podoben nedeterminističnemu končnemu avtomatu, vendar ima dodatno komponento: **sklad** (*stack*).

Sklad omogoča avtomatu neomejen dodaten pomnilnik, ki deluje po principu "zadnji noter, prvi ven" (LIFO - Last In, First Out). To omogoča prepoznavanje jezikov, ki niso regularni (npr. $\{0^n 1^n \mid n \ge 0\}$), saj si lahko avtomat na sklad shrani število prebranih ničel in jih kasneje "poparčka" z enkami.

Skladovni avtomat lahko na sklad **potisne** (*push*) simbol ali pa z njega **vzame** (*pop*) simbol. Dostop je mogoč le do vrhnjega simbola.


Formalno je **skladovni avtomat** definiran kot 6-terica $P = (Q, \Sigma, \Gamma, \delta, q_0, F)$, kjer so:
- $Q$: končna množica stanj,
- $\Sigma$: vhodna abeceda,
- $\Gamma$: **skladovna abeceda** (lahko vsebuje simbole, ki niso v $\Sigma$),
- $\delta : Q \times \Sigma_\varepsilon \times \Gamma_\varepsilon \rightarrow \mathcal{P}(Q \times \Gamma_\varepsilon)$: prehodna funkcija,
- $q_0 \in Q$: začetno stanje,
- $F \subseteq Q$: množica sprejemnih stanj.

Opomba: $\Sigma_\varepsilon = \Sigma \cup \{\varepsilon\}$ in $\Gamma_\varepsilon = \Gamma \cup \{\varepsilon\}$.

Prehodna funkcija $\delta(q, a, x)$ vzame trenutno stanje $q$, naslednji vhodni simbol $a$ in vrhnji simbol na skladu $x$. Vrne množico parov $(r, y)$, kjer je $r$ novo stanje in $y$ simbol, ki zamenja $x$ na skladu (če je $y=\varepsilon$, se $x$ izbriše - *pop*; če je $x=\varepsilon$, se $y$ doda - *push*).

**Nedeterminizem** je pri skladovnih avtomatih ključen. Deterministični skladovni avtomati (DPDA) so šibkejši in ne prepoznajo vseh kontekstno neodvisnih jezikov. Mi se osredotočamo na nedeterministične.



Vhod $w$ sprejme, če lahko $w$ zapišemo kot $w = w_1 w_2 \dots w_m$, kjer je vsak $w_i \in \Sigma_{\varepsilon}$, in če obstajata zaporedje stanj $r_0, r_1, \dots, r_m \in Q$ ter zaporedje nizov $s_0, s_1, \dots, s_m \in \Gamma^*$, ki zadoščajo naslednjim trem pogojem. Nizi $s_i$ predstavljajo zaporedje vsebine sklada, ki ga ima $M$ na sprejemajoči veji računanja.

1.  $r_0 = q_0$ in $s_0 = \varepsilon$. Ta pogoj pomeni, da $M$ začne pravilno, v začetnem stanju in s praznim skladom.
2.  Za $i = 0, \dots, m - 1$ velja $(r_{i+1}, b) \in \delta(r_i, w_{i+1}, a)$, kjer je $s_i = at$ in $s_{i+1} = bt$ za neka $a, b \in \Gamma_{\varepsilon}$ in $t \in \Gamma^*$. Ta pogoj pravi, da se $M$ premika pravilno glede na stanje, sklad in naslednji vhodni simbol.
3.  $r_m \in F$. Ta pogoj pravi, da se na koncu vhoda pojavi sprejemno stanje.


***

**Ekvivalenca med KNG in PDA**


>**Izrek:** Jezik je kontekstno neodvisen natanko tedaj, ko ga prepozna nek skladovni avtomat.

Dokazujemo dve smeri:

**1. Smer (KNG $\Rightarrow$ PDA):**
Če je jezik $L$ kontekstno neodvisen, zanj obstaja KNG $G$. Konstruiramo PDA $P$, ki simulira izpeljave te gramatike.

*Ideja:*
PDA na svojem skladu hrani vmesne nize izpeljave. Začne z začetno spremenljivko.
- Če je na vrhu sklada **spremenljivka** $A$, PDA nedeterministično izbere eno od pravil za $A$ (npr. $A \to w$) in na skladu zamenja $A$ z $w$.
- Če je na vrhu sklada **terminal** $a$, PDA prebere znak z vhoda. Če se ujemata, terminala "odšteje" (pop s sklada). Če se ne ujemata, se veja izvajanja prekine (zavrne).
- Če je sklad prazen in smo prebrali celoten vhod, sprejmemo.

**2. Smer (PDA $\Rightarrow$ KNG):**
Če PDA $P$ prepozna jezik, zanj obstaja KNG $G$.
Ta smer je težja. Želimo zgraditi gramatiko, ki generira vse nize, ki avtomat $P$ pripeljejo iz enega stanja v drugega s praznim skladom.

*Postopek:*
1. Najprej poenostavimo PDA, da ima le eno sprejemno stanje, da sprazni sklad pred sprejetjem in da vsak prehod bodisi doda simbol bodisi ga odvzame (ne oboje hkrati).
2. Definiramo spremenljivke gramatike oblike $A_{pq}$.
   Spremenljivka $A_{pq}$ generira vse nize, ki avtomat pripeljejo iz stanja $p$ (s praznim skladom) v stanje $q$ (s praznim skladom).
3. Pravila gramatike:
   - Za vsak $p$ dodamo $A_{pp} \to \varepsilon$ (v 0 korakih ostanemo v istem stanju).
   - Za poti, kjer se sklad vmes ne sprazni: Če avtomat iz $p$ preide v $r$ (push $u$), nato iz $r$ pride v $s$ (vmesno dogajanje) in iz $s$ v $q$ (pop $u$), dodamo pravilo:
     $$A_{pq} \to a A_{rs} b$$
     kjer sta $a$ in $b$ vhodna simbola pri prvem in zadnjem koraku.
   - Za poti, kjer se sklad vmes sprazni v nekem stanju $r$:
     $$A_{pq} \to A_{pr} A_{rq}$$

S tem dokažemo, da so jeziki, ki jih prepozna PDA, natanko tisti, ki jih generira KNG.
