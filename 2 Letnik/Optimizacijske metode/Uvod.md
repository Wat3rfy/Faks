
Ukvarjamo se z optimizacijo nekih vrednosti tj. npr. maksimiziranje ali minimiziranje različnih veličin.


Zgled je na primer neka dilema, kjer ima kmet na voljo 50 ha - *hektarov* zemlje kamor lahko posadi pšenico, koruzo in krompir. Na razpolago ima 5000 človek-dni delovne sile.
Vemo da veljajo naslednje omejitve.

|  | Delovna sila (človek dni/ha) | Stroški (EUR/ha) | Dobiček (EUR/ha) |
| :--- | :---: | :---: | :---: |
| Pšenica | 60 | 400 | 240 |
| Koruza | 80 | 600 | 400 |
| Krompir | 100 | 480 | 320 |

Pove nam koliko delovne sile, denarja porabimo na hektar ter koliko zaslužimo na hektar za vsako poljščino.

S tem moramo ugotoviti katera konfiguracija nam prinese najvišji dobiček.


[!|hide]- Primer kmeta

Pogledamo primer kmeta kjer lahko problem matematično definiramo z naslednjimi parametri:

|  | Delovna sila (človek dni/ha) | Stroški (EUR/ha) | Dobiček (EUR/ha) |
| :--- | :---: | :---: | :---: |
| Pšenica | 60 | 400 | 240 |
| Koruza | 80 | 600 | 400 |
| Krompir | 100 | 480 | 320 |

Ker hočemo ugotoviti koliko katere poljščine posadimo določimo spremenljivke $x_{1},x_{2},x_{3}$ ki predstavljajo število hektarjev za pšenico, koruzo in krompir.

Vektor rešitve je torej $x = (x_{1},x_{2},x_{3})$.

Hočemo maksimizirati skupni dobiček torej definiramo našo kriterijsko funkcijo

$$f(x_{1},x_{2},x_{3}) = 240x_{1}+ 400x_{2} + 320 x_{3}$$

Upoštevati moramo še podane omejitve

1. Skupna površina ne sme presegati 50 hektarjev
$$x_{1}+x_{2}+x_{3} \leq 50$$
2. Skupno število človek-dni ne sme presegati 5000
$$60x_{1}+80x_{2}+100x_{3} \leq 5000$$
3. Površina ne more biti negativna
$$x_{1},x_{2},x_{3}\geq 0$$

$$D = \{ (x_1,x_2,x_{3}) \in \mathbb{R}^{3} \,;\;x_{1}+x_{2}+x_{3} \leq 50,\, 60x_{1}+80x_{2}+100x_{3} \leq 5000,\, x_{1},x_{2},x_{3}\geq 0\}$$

Če bi kmet uporabil koruzo ne doesežemo možnih 5000 enot delovne sile. Ker koruza prinaša največji dobiček na hektar in ne preseže omejitev je intuitivno verjetno optimalna rešitev $x^{*} = (0,50,0)$ in $v^{*} = 20'000$.

Predstavlja **linearen program**

$$x \in \mathbb{R}^{3} , A \subset  \mathbb{R}^{m \times n} , b \in \mathbb{R}^{m} , c \in \mathbb{R}^{n}$$


$$x = \begin{bmatrix} x_1 \\ x_2 \\ x_3 \end{bmatrix}, A = \begin{bmatrix} 1 & 1 & 1 \\ 60 & 80 & 100 \\ 400 & 600 & 480 \end{bmatrix}, \quad b = \begin{bmatrix} 50 \\ 5000 \\ 24000 \end{bmatrix},c = \begin{bmatrix} 240 \\ 400 \\ 320 \end{bmatrix}$$

iščemo maksimum (*$c$ je vektor koeficientov kriterijske funkcije*)

$$c^{T} x = \begin{bmatrix} 240 & 400 & 320 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \\ x_3 \end{bmatrix} = 240x_1 + 400x_2 + 320x_3$$

kjer velja

$$Ax \leq b$$
$$x \geq 0$$

*kjer vsaka vrstica v $A$ predstavlja eno od enačb omejitev, $b$ pa dejansko podano omejitev*


> **Stroga matematična formulacija**
> 
> **Področje dopustnih rešitev $D$:**
> $$
> D = \left\{ (x_1, x_2, x_3) \in \mathbb{R}^3 \,;\;\; 
> \begin{aligned}
> &x_1 + x_2 + x_3 \le 50 \\
> &60x_1 + 80x_2 + 100x_3 \le 5000 \\
> &400x_1 + 600x_2 + 480x_3 \le 24000 \\
> &x_1, x_2, x_3 \ge 0 
> \end{aligned}
> \right\}
> $$
> 
> **Ciljna funkcija $f$:**
> $$
> f: \mathbb{R}^3 \to \mathbb{R}
> $$
> $$
> f(x_1, x_2, x_3) = 240x_1 + 400x_2 + 320x_3
> $$
> 
> **Splošen linearni program (LP) v standardni obliki:**
> $(D, f, \max)$
> $$D = \{ x \in \mathbb{R}^n \mid Ax \le b, x \ge 0 \}$$
> $$f(x) = c^T x$$
> 




>[!|hide]- Podrobno
>
> **Vektor odločitvenih spremenljivk ($x$)**
> Vektor $x$ predstavlja naše neznanke (količino hektarjev za vsako poljščino):
> $$x = \begin{bmatrix} x_1 \\ x_2 \\ x_3 \end{bmatrix} \in \mathbb{R}^3$$
> Tukaj je $n = 3$ (število spremenljivk).
> 
> **Vektor koeficientov ciljne funkcije ($c$)**
> To so dobički na hektar, ki jih želimo maksimizirati. V matričnem zapisu uporabimo transponiran vektor $c^T$, da dobimo skalarni produkt:
> $$c = \begin{bmatrix} 240 \\ 400 \\ 320 \end{bmatrix} \implies c^T x = \begin{bmatrix} 240 & 400 & 320 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \\ x_3 \end{bmatrix} = 240x_1 + 400x_2 + 320x_3$$
> 
> **Matrika omejitev ($A$) in vektor desnih strani ($b$)**
> Vsaka vrstica matrike $A$ predstavlja koeficiente ene omejitve, vektor $b$ pa razpoložljive vire. V vašem primeru imamo $m = 3$ omejitve (zemlja, delovna sila, kapital).
> 
> $$A = \begin{bmatrix} 1 & 1 & 1 \\ 60 & 80 & 100 \\ 400 & 600 & 480 \end{bmatrix}, \quad b = \begin{bmatrix} 50 \\ 5000 \\ 24000 \end{bmatrix}$$
> 
> *   **1. vrstica (Zemlja):** $1x_1 + 1x_2 + 1x_3 \leq 50$
> *   **2. vrstica (Delovna sila):** $60x_1 + 80x_2 + 100x_3 \leq 5000$
> *   **3. vrstica (Kapital/Stroški):** $400x_1 + 600x_2 + 480x_3 \leq 24000$
> 
> 
> Kmetov problem v splošni obliki, kot je prikazana na vaši drugi sliki, izgleda takole:
> 
> $$\max \ c^T x$$
> $$\text{pri pogojih: } Ax \leq b$$
> $$x \geq 0$$
> 
> Če to razpišemo z našimi vrednostmi:
> 
> $$\text{Iščemo } \max \!\left( \begin{bmatrix} 240 & 400 & 320 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \\ x_3 \end{bmatrix} \right)$$
> $$\text{tako da velja: } \begin{bmatrix} 1 & 1 & 1 \\ 60 & 80 & 100 \\ 400 & 600 & 480 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \\ x_3 \end{bmatrix} \leq \begin{bmatrix} 50 \\ 5000 \\ 24000 \end{bmatrix}$$
> 
> $$\text{in } x_1, x_2, x_3 \geq 0$$



**Problem trgovskega potnika $(TP)$**

Trgovec ou Ljubljane hoče obiskati vsa mesta in se vrniti nazaj v Ljubljano. Kako to stori najceneje.

Cene letalskih vozovnic

$$
\begin{array}{|l|c|c|c|c|c|}
\hline & \text{Ljubljana} & \text{London} & \text{Madrid} & \text{Pariz} & \text{Rim} \\
\hline \text{Ljubljana} & - & 5 & 10 & 5 & 10 \\
\hline \text{London} & 5 & - & 10 & 1 & 5 \\
\hline \text{Madrid} & 10 & 10 & - & 5 & 5 \\
\hline \text{Pariz} & 5 & 1 & 5 & - & 1 \\
\hline \text{Rim} & 10 & 5 & 5 & 1 & - \\
\hline
\end{array}
$$


Imamo utežen graf in iščemo najcenejši hamiltonov cikel grafa.

To je primer **kombinatorne optimizacije**. Namesto iskanja realnih števil, iščemo **permutacijo** mest.

Če začnemo v nekem mestu nam ostane $v-1$ mest kar je $(v-1)!$ možnosti. Ker bi s tem dvakrat šteli cikle (npr .1231 in 1321) delimo z 2 in dobimo $\frac{(v-1)!}{2}$ možnosti.

Formalno formuliramo problem z grafom. $G= (V,E)$ in utežmi $c : E \rightarrow \mathbb{R}$. Hočemo da je $c(H) = \sum_{e \in H}^{}c(e)$ čim manjši. Ponavadi se zahteva da je graf poln.

Lahko formuliramo tudi drugače kjer vzamemo zaporedje obiskovanja mest kot ciklično permutacijo.
Definiramo lahko matriko stroškov $C$ $n \times n$ velikosti, kjer je $n$ število mest. Vsak $c_{ij}$ predstavlja strošek iz $i$ v $j$. Iščemo preslikavo $\varphi \in S_{n}$ tako da je $\varphi$ en cikel dolžine $n$. Veljati pa mora da je

$$S_{\varphi}= \sum_{1}^{n}c_{i,\varphi(i)}$$

Mi iščemo $\min_{\varphi \in S_{n}} S_{\varphi}$

> **Stroga formulacija**
> 
> **1. Formulacija z grafi:**
> *   **Podatki:** Graf $G=(V,E)$, uteži $c: E \to \mathbb{R}$ (običajno se zahteva $G = K_n$)
> *   **Množica $D$:** $D = \{ H \mid H \text{ je Hamiltonov cikel v } G \}$
> *   **Funkcija $f$:** $f: D \to \mathbb{R}$, $f(H) = \sum_{e \in E(H)} c(e)$
> 
> **2. Formulacija s permutacijami:**
> *   **Podatki:** Matrika stroškov $C \in \mathbb{R}^{n \times n}$
> *   **Množica $D$:** $D = \{ \varphi \in S_n \mid \varphi \text{ je ciklična permutacija} \}$
> *   **Funkcija $f$:** $f: D \to \mathbb{R}$, $f(\varphi) = \sum_{i=1}^n C_{i, \varphi(i)}$
> 



**Problem prirejanja**

Imamo $n$ delavcev in $n$ opravil kjer mora biti vsako opravilo dodeljeno enemu delavcu in vsak delavec mora imeti natanko eno opravilo.

Imamo matriko stroškov $C \in \mathbb{R}^{n \times n}$. Element $c_{ij}$ predstavlja strošek če $i$-ti delavec opravlja $j$-to delo.

Matametično lahko to formuliramo kot iskanje popolnega prirejanja ob polnem dvodelnem grafu $K_{n,n}$ s funkcijo uteži $c : E(K_{n,n}) \rightarrow \mathbb{R}$. Iščemo najcenejše prirejanje v grafu torej velja $\sum_{e \in M}^{}c(e)$ mora biti najmanjša.

>**Stroga formulacija**
>
> **1. Formulacija z grafi:**
> *   **Podatki:** Graf $G=(V,E)$, uteži $c: E \to \mathbb{R}$ (običajno se zahteva $G = K_{n,n}$)
> *   **Množica $D$:** $D = \{ M \mid M \text{ je popolno prirejanje v } G \}$
> *   **Funkcija $f$:** $f: D \to \mathbb{R}$, $f(M) = \sum_{e \in M} c(e)$
> 
> **2. Formulacija s permutacijami:**
> *   **Podatki:** Matrika stroškov $C \in \mathbb{R}^{n \times n}$
> *   **Množica $D$:** $D = S_n$ (vse permutacije $n$ elementov)
> *   **Funkcija $f$:** $f: D \to \mathbb{R}$, $f(\varphi) = \sum_{i=1}^n C_{i, \varphi(i)}$


**Problem svetilke** 

V izhodišču imamo štiri osebe z različnimi hitrostmi prehajanja brvi: Ana porabi 1 minuto, Borut 2 minuti, Cvetka 5 minut in Darko 10 minut. 

Brv lahko hkrati prečkata največ dve osebi, pri čemer se hitrost njunega prehajanja vedno določi po počasnejši osebi v paru. Ker je noč in imajo na voljo le eno svetilko, mora biti ta prisotna pri vsakem prehodu čez brv, kar pomeni, da se mora po vsakem skupinskem prehodu nekdo s svetilko vrniti na začetno stran, da lahko naslednji člani skupine nadaljujejo pot. Cilj naloge je določiti zaporedje prehodov, ki celotno skupino spravi na drugi breg v najkrajšem možnem času.


**Matematična formulacija**
Temelji na **grafu stanj** $G = (V, E)$. Vozlišča predstavljajo vse možne porazdelitve oseb med obema bregoma brvi. 

Vsako vozlišče je definirano kot par $(T, T^c)$, kjer $T$ predstavlja množico ljudi na prvem bregu, $T^c$ pa komplementarno množico na drugem bregu. Pri tem je nujno upoštevati lokacijo svetilke, saj isto stanje oseb na bregovih pomeni različno situacijo v grafu, odvisno od tega, kje se nahaja svetilka. Povezave $E$ v grafu povezujejo tista stanja, med katerimi je mogoč prehod z enim premikom čez brv (bodisi ene ali dveh oseb s svetilko). Te povezave so utežene, kjer utež $xy$ predstavlja čas, ki je potreben za prehod iz stanja $x$ v stanje $y$. Ta čas ustreza času najpočasnejše osebe, ki v tem koraku prečka brv.

Graf je v svojem bistvu usmerjen, vendar ga lahko obravnavamo kot neusmerjenega, če upoštevamo, da se s svetilko lahko gibljemo v obe smeri. Iskanje rešitve se tako prevede v iskanje **najkrajše poti** v uteženem grafu od začetnega stanja, kjer so vsi štirje na prvem bregu $(\{A, B, C, D\}, \emptyset)$, do končnega stanja, kjer so vsi na drugem bregu $(\emptyset, \{A, B, C, D\})$. Za sistematično iskanje te poti se uporabi **Dijkstrov algoritem**, ki preišče graf in določi zaporedje z minimalno skupno vsoto uteži.



***