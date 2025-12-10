>[!|hide]- Snov gimnazije
> 
> Če imamo $n$ predmetov in jih poskušamo razporediti na $n$ mest potem to lahko storimo na $n!$ načinov.
> Na prvo mesto lahko damo enega izmed $n$ predmetov, na drugo enega izmed $n-1$ in tako naprej. Temu pravimo permutacije.
> 
> $$P_{n} = n!$$
> 
> Če imamo $n$ predmetov in jih probamo postaviti na $k$ mest potem lahko število načinov izračunamo z
> 
> $$p_{k,n} = \frac{n!}{(n-k)!}$$
> 
> To lahko razložimo kot na vsako od k mest lahko damo $n, n-1, n-2,...,n-k+1$ elementov kar je natanko $\frac{n!}{(n-k)!}$, ker se preostalih znebimo tako da jih pokrajšamo.
> 
> Oziroma če si predstavljamo vseh $n!$ razporeditev. Recimo da imamo razporeditev 5 elemtnov na 3 mesta. Imamo lahko 12345 in 12354, kjer imamo razporeditev na prvih 3 mestih ponovljeno, in ker nas zanimajo le te moramo vse možne ponovitve zbrisati. Ker sta ostali le 2 mesti se lahko elementi na teh mestih razporedijo na $2!$ načinov, to jih da v grupe velikosti $2!$, da dobimo število grup verlikosti $2!$ pa moramo deliti z $2!$. 
> 
> Če imamo elemente ki se lahk ponovijo na $k$ mestih imamo
> 
> $$n^{k}$$
> 
> Če hočemo razporediti elemente kjer se nek elemente ki se ponovijo kjer se ponovijo $k_{1},...,k_m$ imamo
> 
> $$p^{n}_{k_{1},...,k_{n}} = \frac{n!}{k_{1}!k_{2}!...k_{n}!}$$
> 
> Spet delujemo po principu da dobimo $k_{1}!,...,k_{n}!$, kjer moramo deliti da dobimo pravilno število možnosti. Če imamo črke naprimer: $\text{BAN}_1\text{AN}_2$ in $\text{BAN}_2\text{AN}_1$ imamo spet $2!$ intako za vse možne črke.
> 
> Nato pa imamo če kombinacije, kjer iščemo samo vse množice velikosti  $k$ v množici z $n$ elementi.
> 
> $$_{n}C_{k} = \frac{n!}{k!(n-k)!}$$
> 
> Kar se dogaja je da gledamo vse razporeditve $n$ elementov na $k$ mestih nato pa še delimo z $k!$ se hočemo znebiti vseh permutacij teh elementov na $k$ mestih oz. vse permutacije istih elementov združimo v eno skupino.
> 
> Za kombinacije uporabljamo tudi binomski simbol.
> 
> $$\binom{\,n\,}{\,k\,}$$
> 
> Binomski simbol se pojavi tudi pri $n$-ti potenci dvočlenika kjer velja
> 
> $$(x+y)^{n} = \sum_{k = 0}^{n}\binom{\,n\,}{\,k\,}x^{n-k}y^{k}$$
> 
> Če pogledamo primer
> 
> $$(x+y)^{3} = (x+y)(x+y)(x+y)$$
> $$x^{3}+3x^{2}y + 3xy^{2}+y^{3}$$
> 
> je prva stvar ki jo opazimo da so vsi členi neka kombinacija $x$ in $y$. Nato pa je edina naslednja stvar še da opazimo da lahko do nekaterih kombinacij pridemo na več načinov kot do drugih saj vrstni red ni pomemben. Efektivno delamo računamo kombinacije obeh členov, kjer lahko do nekaterih členov pridemo na več načinov kot do drugih. Iz tega dobimo tudi Pascalov trikotnik.
> 
> **Kombinacije lahko gledamo tudi kot najprej permutacije, potem se omejimo na mesta na začetku in jih damo v skupine kjer je prvih $k$ elementov v enakem vrstnem redu, to se elementi te skupine, da ugotovimo koliko teh skupin je oz. koliko je permuatcij elementov na $k$ mestih moramo deliti s številom elementov v tej skupini - $\frac{n!}{(n-k)!}$, kar so permutacije ostalih elementov.**
> **Nato moramo še pogledati kje se elementi ponavljajo in dati vsa zaporedja ki vsebujejo iste elemente oz. so permutacije samih sebe v svojo skupino - in spet delimo s številom elementov v tej skupini da dobimo končno število kombinacij.**



## Osnovni problemi kombinatorike

###  Funkcija
Funkcija je definirana kot podmnožica kartezičnega produkta $A \times B$, kjer velja da za vsak $a \in A$ obstaja natanko en $b \in B$ tako da je $(a,b) \in  f$.

$$f: A \to B$$

$A$: **domena**
$B$: **kodomena**
$f(A)$: **slika**

> Funkcijo lahko zapišemo na različne načine:
> 
> **Eksplicitno za vsak element**
> $\{1,2,3\} \to \{a,b,c,d\}$; $f(1)=a, f(2)=a, f(3)=b$
> 
> **Predpis**
> $F: \mathbb{N} \to \mathbb{N}$; $F(n) = 2n$
> 
> **Rekurzivna**
> $F: \mathbb{Z} \to \mathbb{Z}$; $f(n) = f(n-1) + f(n-2)$ 

Funkcija ima lahko naslednje lastnosti
**Injektivnost**:
$$x \neq y \implies f(x) \neq f(y)$$
*Interpretacija:* v vsaki škatli je $\le 1$ kroglica.

**Surjektivnost**:
Slika funkcije je enaka $B$.
*Interpretacija:* vsaj ena kroglica v vsaki škatli.

**Bijektivnost**:
Je injektivna in surjektivna hkrati.

***

Za kombinatoriko pa so pomembne oznake

*   $[n] = \{1, \dots, n\}$; $|[n]| = n$. 
  Za $n=0 \implies \emptyset$. 
* $\mathbb{N} = \{0,1,2, \dots\}$.
*   $2^A$: **Potenčna množica** $\{X ; X \subseteq A\}$.
*   $\binom{A}{k} = \{B \in 2^A ; |B|=k\}$ (podmnožice s $k$ elementi).
*   $B^A :=$ množica vseh preslikav iz $A \vee B$.

***

 **Dirichletovo načelo**


$$f: A \to B \text{ je injektivna } \Rightarrow |A| \le |B|$$
$$\iff$$
$$|A| > |B| \implies \nexists \text{ inj. } F: A \to B$$

Za dokazovanje z **dirichletovim načelom** poskušamo najti neko karakterizacijo problema da lahko določimo množico z manj elementi kot imamo kroglic.

*Primer take uporabe je pri dokazovanju spodnjega problema kjer imamo podmnožico velikosti $n+1$ iz česar poskuismo ugotoviti ali v množici $[2n]$ lahko povlečemo množico z $n$ ali manj elementi tako da je aplikabilno za naš primer. ker imamo $2n$ elementov vemo da je notri natanko $n$ lihih števil nato pa lahko opazimo da je za deljivost uporaben zapis $2^{k} \cdot l$ kjer je $l$ liho število in lahko tako dokažemo da ni dovolj lihih števil kar pomeni da mora eno deliti drugo*

*Če damo $n$ kroglic v $k$ škatel in je $n > k$, potem je v vsaj eni škatli več kot 1 kroglica.*

>[!|]- Primeri:
> 13 ljudi $\implies$ potem imata vsaj 2 rojstni dan v istem mesecu.
> *   Kroglice: ljudje
> *   Škatle: meseci
> *   Preslikava: mesec rojstva. $|A|=13, |B|=12$.
> ***
> $n+1$ števil. Med njimi sta 2, ki imata razliko deljivo z $n$.
> *   Kroglice: izbrana števila ($n+1$)
> *   Škatle: ostanki pri deljenju z $n$ ($\{0, \dots, n-1\}$, teh je $n$)
> *   Preslikava: je ostanek pri deljenju z $n$. 
> Če imata dve števili isti ostanek $r$ $\Rightarrow x = k_{1}n+r \;,\; y=k_{2}n+r$ $\Rightarrow x-y = (k_{1}-k_{2})n$
>  $\Rightarrow n|x-y$
> ***
> $n$ ljudi, vsaka 2 se lahko poznata ali ne. Obstajata 2, ki poznata enako število ljudi.
> *   Kroglice: ljudje ($n$)
> *   Škatle: možna števila znancev $\{0, \dots, n-1\}$.
> *   *Opazka:* Škatli 0 (pozna nikogar) in $n-1$ (pozna vse ostale) ne moreta biti 'zasedeni' hkrati.
> *   $\implies$ imamo $n-1$ škatel na voljo za $n$ ljudi.
> ***
> $X \subseteq [100], |X|=10$. Dve disjunktni neprazni podmnožici $X$ morata imeti isto vsoto.
> *   Kroglice: neprazne podmnožice $X$; teh je $2^{10}-1 = 1023$.
> *   Škatle: možne vsote. Maksimalna vsota je $100+99+\dots+91 \approx 955$.
> *   Zaloga vrednosti (škatle) $\subseteq [955]$.
> *   $1023 > 955 \implies$ imamo dve različni podmnožici z isto vsoto $A, B \subseteq X$.
> *   Če nista disjunktni: vzemi $A \setminus (A \cap B)$ in $B \setminus (A \cap B)$. Še vedno imata isto vsoto in sta disjunktni.
> ***
> $X \subseteq [2n], |X|=n+1$. $\implies \exists x, x' \in X$, **tako da** $x | x'$ ali $x' | x$.
> *   Vsako število zapišemo kot $x = 2^a \cdot L$, kjer je $L$ lih del (lih faktor).
> *   Kroglice: $x \in X$ (teh je $n+1$).
> *   Škatle: liha števila v $[2n]$. To so $\{1, 3, 5, \dots, 2n-1\}$. Teh je $n$.
> *   Preslikava: $x \mapsto L$ (element preslikamo v njegov lihi del).
> *   Po Dirichletovem principu $\exists x, x' \in X$ z istim lihim delom $L$.
>     $x = 2^a \cdot L, \quad x' = 2^b \cdot L$.
>     Ker sta $x$ in $x'$ različna, sta tudi eksponenta $a$ in $b$ različna.
>     Če $a < b \implies x | x'$. (Sicer, če $b < a \implies x' | x$).

---

Pri kombinatoričnih problemih poznamo načelo vsote in produkta ki opisujeta koliko načinov imamo da izberemo nek element iz množic oz. koliko načinov imamo da tvorimo zaporedje izbir iz nekih množic.

**Načelo vsote**:

$$|A \cup B| = |A| + |B|,  \text{če sta } A \text{ in } B \text{ disjunktni.}$$

Splošno

$$|A \cup B| = |A| + |B| - |A \cap B|$$

*Uporabljamo ko imamo disjuntkne izbire -  ne moreta se zgoditi hkrati  - izbire se izključujejo - izberem lahko element iz množice $A$ ali element iz množice $B$*

**Načelo produkta**:

$$|A \times B| = |A| \cdot |B|$$

*Ko imamo izbire ki si sledijo ena drugi (recimo naprej izberemo element iz $A$ potem pa izberemo še element iz $B$) potem obstaja toliko zaporedij teh izbir kot je produkt moči $A$ in $B$.*

>[!|hide]- Primer
>  3 majice, 3 srajce (zgoraj 6 opcij); 4 hlače, 4 trenirke (spodaj 8 opcij).
Kombinacije: $(3+3) \cdot (4+4) = 6 \cdot 8 = 48$.
> 
> Izbiramo najprej med zgornjimi oblačili - $M + S$ potem pa kot naslednja izbira (v zaporedju) še med spodnjimi oblačil $H + T$.
> 
> $$M+S \cdot H+T$$

***

> Preslikav iz množice $N$ v $K$ je natanko $k^{n}$.
> Če  imamo $K^{N}$ imamo $k$ izbir za vsak element $n$.
> 
> Torej je $\underbrace{k \cdot k \cdot \dots \cdot k}_{n} = k^n$.
> 
> >[!|hide]- Dokaz bijekcije med podmnožicami in binarnimi zaporedji:
> > $|2^{[n]}| = |\{0,1\}^n| = 2^n$.
> > Iščemo bijekcijo iz $2^{[n]} v \{0,1\}^n = \{(\epsilon_1, \dots, \epsilon_n); \epsilon_i \in \{0,1\}\}$.
> > Preslikava s karakterističnim vektorjem:
> > $\Phi(A) = (\epsilon_1 \dots \epsilon_n)$, kjer $\epsilon_i = \begin{cases} 1; & i \in A \\ 0; & i \notin A \end{cases}$.
> > Inverz: $\Psi(\epsilon_1 \dots \epsilon_n) = \{ i \in [n] ; \epsilon_i = 1\}$.

> Če je $N$ končna in imamo $F \in  N^{N}$ potem velja naslednje
> 
> $F$ je inj. $\iff F$ je surjektivna $\iff F$ je bijektivna.

**Število injektivnih preslikav iz  $N \to K$**
Prvi element ima $k$ izbir, drugi $k-1$, ...

$$k(k-1)\dots(k-n+1) = k^{\underline{n}} = \frac{k!}{(k-n)!}$$

To označujemo kot **padajoča potenca** 

$$\large k^{\underline{\;\!\!n}} = k(k-1)\dots(k-n+1)$$

Obstaja tudi **naraščajoča potenca** 

$$\large k^{\overline{\;\!\!n}} = k(k+1)\dots(k+n-1)$$

Število bijekcij $N \to N$ oz. **permutacij**:

$$|N^N| = n! = n \cdot (n-1) \dots 2 \cdot 1$$


**Stirlingova aproksimacija**: $n! \sim \sqrt{2\pi n}(\frac{n}{e})^n$

>[!|hide]- 
>
> $$
> \ln(n!) = \ln(n) + \dots + \ln(1)
> $$
> $$
> \sum_{1}^{n} \ln(x) \approx \int_{1}^{n} \ln(x) dx
> $$
> $$
> \Big[ x\ln(x) - x \Big]_1^n \approx n\ln(n) - n
> $$
> $$
> \implies \ln(n!) \approx n \ln(n) - n
> $$
> $$
> n! \approx e^{n \ln(n) - n} = e^{\ln(n^n) - n}
> $$
> $$
> \approx n^n \cdot e^{-n} = \left(\frac{n}{e}\right)^n
> $$
***
> **Asimptotična enakost**: $a_{n}\sim b_{n}  := \lim \frac{a_n}{b_n} = 1$.
***
Posebni primeri (iz definicije preslikav med praznimi množicami):
*   $0! = 1$ (ena bijekcija $\emptyset \to \emptyset$).
*   $0^0 = 1$ (ena funkcija $\emptyset \to \emptyset$).
  
>[!|dokaz]- Dokaz:
> Funkcija $f: X \to Y$ je relacija $f \subseteq X \times Y$, ki mora izpolnjevati pogoj, da za vsak element $x \in X$ obstaja natanko en element $y \in Y$, na katerega ga funkcija preslika ($\forall x \in X, \exists ! y \in Y: (x, y) \in f$). $X = \emptyset$ in $Y = \emptyset$. V tem primeru je njun kartezični produkt $X \times Y$ prav tako prazen, $\emptyset \times \emptyset = \emptyset$.
> 
> Vsaka funkcija $f: \emptyset \to \emptyset$ mora biti podmnožica praznega produkta, torej $f \subseteq \emptyset$. Ker je edina podmnožica prazne množice sama prazna množica, obstaja samo ena takšna relacija: $f = \emptyset$. Sedaj moramo preveriti, ali ta prazna relacija ustreza strogim pogojem za funkcijo. Pogoj obstoja slike (totalnost), ki zahteva, da za vsak $x \in X$ obstaja slika, je trivialno resničen, saj ker je $X = \emptyset$, ne obstaja noben $x$. Ta univerzalna trditev o elementih prazne množice je avtomatično izpolnjena, saj ni nobenega nasprotnega primera, ki bi jo lahko ovrgel. Podobno je z enoličnostjo slike za vsak $x$: tudi ta pogoj je trivialno izpolnjen, ker ni nobenega elementa v domeni. Torej, funkcija $f: \emptyset \to \emptyset$ izpolnjuje vse zahteve in obstaja natanko ena – prazna funkcija $f = \emptyset$.
> 
> Ta rezultat je ključen pri razumevanju potenciranja v teoriji množic in kombinatoriki, kjer $a^b$ definiramo kot število vseh funkcij $f: B \to A$. Ko to definicijo uporabimo za moči praznih množic, kjer sta število elementov množic $A$ in $B$ enaka nič, dobimo izraz $0^0$. Ker smo dokazali, da obstaja natanko ena funkcija med dvema praznima množicama, matematična definicija določa, da je $0^0 = |\{f: \emptyset \to \emptyset\}|$, kar je enako 1.

---

## Permutacije

Bijekcija $A \to A$ je **permutacija** $A$. 

Množica vseh permutacij $A$ v $A$ je $S_A$.
Velikost: $|S_A| = |A|!$.

Za $[n]$ označimo $S_{[n]} = S_n$.

Notacije:
*   Dvovrstična: $\begin{pmatrix} 1 & 2 & \dots & n \\ \pi_1 & \pi_2 & \dots & \pi_n \end{pmatrix}$
*   Enovrstična: $\pi_1 \pi_2 \dots \pi_n$


**Ciklična notacija**:
Sledimo elementu: $1 \to \pi(1) \to \pi^2(1) \dots$ dokler se ne vrnemo.
Cikel zapišemo: $(i, \pi(i), \pi^2(i), \dots, \pi^{k-1}(i))$, kjer $\pi^k(i) = i$.

>Vsako permutacijo lahko zapišemo kot produkt disjunktnih ciklov.

>Cikle dolžine ena imenujemo **negibne točke**.

>Disjunktni cikli komutirajo.

## Načelo dvojnega štetja

Recimo da imamo $A$ in $B$ in relacijo $S \subseteq A \times B$.
Predstavljamo si lahko tabelo kjer imamo vrstico po $b$-jih in stolpec po $a$-jih.

$$\begin{bmatrix}(a_{1},b_{1}) & (a_{1},b_{2}) & ... &(a_{1},b_{n}) \\ (a_{2},b_{1}) & (a_{2},b_{2}) & ... &(a_{2},b_{n}) \\ ... & ...&...&...\\(a_{n},b_{1}) & (a_{n},b_{2}) & ...& (a_{n},b_{n})  \end{bmatrix}$$

Sedaj lahko za vrstico, nekega elementa $A$ zapišemo njeno vsoto:

$v_{i} = \text{št. } \checkmark \text{ v vrstici } a_{i} = |\{ (a_{i},b_{j}) \in S \,;\; j \in \{ 1,...,n\} \}|$

Oz. drugače povedano število relacij oz. parov $(a,b)$ ki pripadajo relaciji v vrstici.

$s_{j} = \text{št. } \checkmark \text{ v stolpcu } b_{j} = |\{ (a_{i},b_{j}) \in S \,;\; i \in \{ 1,...,n\} \}|$

Načelo dvojnega štetja pravi, da je skupno število kljukic enako, ne glede na način seštevanja:

$$\sum_{i=1}^{n} v_{i} = \sum_{j=1}^{n} s_{j} = |S| $$

>[!|hide]- Glaven primer
> 
> $$
> \sum_{1}^{n} k \binom{n}{k}
> $$
> 
> Iščemo kako bi lahko sešteli število podmožic velikosti $k$
> pomnoženih s številom elementov
> 
> $k \binom{n}{k}$ je lahko predsatvljen na naslednji način 
> $\qquad \qquad\quad \{1,2\}, \{2,3\}, \{1,3\}$
> $\qquad \qquad 1 \quad \checkmark \quad\quad\quad\qquad \quad \checkmark$
> $\qquad \qquad 2 \quad \checkmark \quad\quad\quad \checkmark \quad \qquad$
> $\qquad \qquad 3 \quad \quad\quad\quad \quad \checkmark \quad\quad \checkmark$
> kjer vidimo da če tvorimo tabelo kjer so  
> 
> podmnožce $\to$
> št. $[n] \downarrow$
> 
> potem naj bo relacija $(A, x)$ tako da velja $A R x$ če je $x \in A$.
> $\implies \sum_{1}^{n} \binom{n}{k} k$ sešteva po stolpcih
> 
> za $n 2^{n-1}$ pa seštevamo vrstice torej za vsako vrstico velja da je relacija tam kjer je element v podmnožici. $\implies$ recimo vrstica $2$ $-$ to pomeni da gledamo koliko je vseh podmnožic ki vsebujejo $2$. $\implies$ imamo $n-1$ el. ki so še lahko podmnožici
> $\implies 2^{n-1}$, ker je $n$ vrstic $\implies n 2^{n-1}$
> $$
> \implies \sum_{1}^{n} \binom{n}{k} k = n 2^{n-1}
> $$

>[!|hide]- Primeri:
> 
> (1) 32 deklet, vsako dekle pozna 4 fante. Vsak fant pozna 8 deklet. Koliko je fantov?
> *   $A = \text{dekleta}, B = \text{fantje}$. Relacija "se poznata".
> *   Vsota po dekletih: $32 \cdot 4$.
> *   Vsota po fantih: $|B| \cdot 8$.
> *   $32 \cdot 4 = |B| \cdot 8 \implies 128 = 8|B| \implies |B| = 16$.
> 
> (2) Triangulacija grafa (dodajamo povezave dokler niso vsa lica trikotniki).
> *   Relacija med množico povezav $E$ in množico lic $F$. ($e_j$ je na robu lica $F_i$).
> *   Št. $\checkmark$ v vrstici $e_j$ (povezava): vsaka povezava meji na 2 lici.
> *   Št. $\checkmark$ v stolpcu $F_i$ (lice): vsako lice je trikotnik, ima 3 povezave.
> *   Dvojno štetje:
>     $$2 \cdot |E| = 3 \cdot |F|$$
> 
> (3) Koliko deliteljev imajo naravna št. "v povprečju"?
> *   Pogledamo na $[n]$ in vzamemo $n \to \infty$.
> *   Tabela velikosti $n \times n$. Vrstice: števila $i \in \{1 \dots n\}$, Stolpci: možni delitelji $d \in \{1 \dots n\}$.
> *   Relacija: $d$ deli $i$ ($d|i$).
> *   $v_r(i) = s_i$: število deliteljev števila $i$.
> *   $v_s(d)$: število števil v $[n]$, ki so večkratniki $d$. To je $\lfloor \frac{n}{d} \rfloor$.
> *   Vsota: $\sum_{i=1}^n s_i = \sum_{d=1}^n \lfloor \frac{n}{d} \rfloor$.
> *   Povprečje:
>     $$\frac{1}{n} \sum_{i=1}^n s_i = \frac{1}{n} \sum_{d=1}^n \lfloor \frac{n}{d} \rfloor \approx \frac{1}{n} \sum_{d=1}^n \frac{n}{d} = \sum_{d=1}^n \frac{1}{d} = H_n$$
>     $H_n$ (harmonično število) asimptotično raste kot $\ln n$.
> 
> (4) Dokaz
> $$
> \sum_{k=0}^{n} \binom{n}{k} = 2^n
> $$
> 
> $\text{el. } [n] \downarrow$ 
> podmnožice $\rightarrow$
> 
> 
> 
> $i \ R \ A \Leftrightarrow |A| = i$
> 
> Po stolpcih velja $2^n$ saj imamo v vsakem stolpcu eno relacijo - podmnožica ima eno velikost.
> 
> Po vrsticah velja da imamo toliko kljukic  v vrstici kolikor je podmnožic velikosti $i$.
> $$
> 1 + \binom{n}{1} + \binom{n}{2} + \dots + \binom{n}{n-1} + 1
> $$
> $$
> \Rightarrow \sum_{k=0}^{n} \binom{n}{k} = 2^n
> $$



### Podmnožice in načrti

**Binomski koeficient**


$$2^A = \{B \subset A\}$$

$$\binom{\,A\,}{\,k\,} = \{ B \subset A : |B| = k\}$$

>[!|hide]- Neka perspektiva
> *Recimo da imamo nekoga ki meče žogo v koš, in gledamo na koliko načinov lahko doseže 1 od 3 košev. Efektivno izbiramo iz množice 3 zadetkov a izberemo samo 2, kar definira tudi koliko zgrešitev bo.*
> *Taka stvar je isto pri binomskem izreku, $(x+y)^{n}$, kjer izbiramo med množico $x_{n}$ in izbiramo koliko $x_{i}$ za $k$-to potenco.*

Def:

$$\binom{\,n\,}{\,k\,} = \left| \binom{\,[n]\,}{\,k\,}\right|$$

oz. število k-elementnih podmnožic množice z $n$ elementi; število načinov da izberemo $k$ elementov iz množice z $n$ elementi.

$$\binom{\,[n]\,}{\,0\,} = \{ \emptyset\}$$
$$\binom{\,[n]\,}{\,1\,} = \{ \{ 1\},\{ 2\},...,\{ n\}\}$$
$$\binom{\,[n]\,}{\,n\,} = \{ [n]\}$$

$$\binom{\,n\,}{\,k\,}=0 \,;\; k < 0 \lor k > n$$

Binomski koeficient je simetričen

$$\binom{\,n\,}{\,k\,} = \binom{\,n\,}{\,n-k\,}$$
$$ $$
$$\phi: \binom{\,[n]\,}{\,k\,} \rightarrow \binom{\,[n]\,}{\,n-k\,}$$
$$\phi (A) = A^{C}$$
$$ $$

Rekurzivna zveza

$$ \binom{\,n\,}{\,k\,} = \binom{\,n-1\,}{\,k-1\,} + \binom{\,n-1\,}{\,k\,}$$

>[!|dokaz]- Dokaz:
> 
> Predpostavimo da damo nek element ven iz množice. Imamo $n-1$ elementov. Nato poiščemo vse podmnožice velikosti $k-1$ to so te ki bodo po dodajanju tega elementa vsebovale tudi le tega in bo velikost $k$.
> Nato pa lahko poiščemo še vse množice velikosti $k$ ki ne vsebujejo odstranjenega elementa in dobimo torej množice ki tako ali tako nimajo odstranjenega elementa torej so velikosti $k$. Ko dodamo odstranjen element nazaj v množico pa ga lahok dodamo še vsem množicam velikosti $k-1$, in dobimo podmnožice velikosti $k$ kar so potem vse podmnožice velikosti $k$.

> **Formula za binomski koeficient**
> 
> $$\binom{\,n\,}{\,k\,} = \frac{n^{\underline{k}}}{k!}$$
> 
> >[!|dokaz]- Dokaz:
> >Izberemo zaporedja $k$ elementov iz množice $n$ ampak ker smo šteli vse permutacije $k$ elementov moramo za vsako množico zaporedij z istimi elementi izločiti vse permutacije teh elementov - torej jih lahko damo po skupinah velikosti $k!$ - to pomeni da delimo s $k!$.



> $$1+2+...+n = \binom{\,n+1\,}{\,2\,}$$
> 
> >[!|dokaz]- Dokaz:
> > Z indukcijo in rekurzivno zvezo


**Pascalov trikotnik**


$$
\begin{array}{ccccccccccccc}
&&&&&& 1 &&&&&& \\
&&&&& 1 && 1 &&&&& \\
&&&& 1 && 2 && 1 &&&& \\
&&& 1 && 3 && 3 && 1 &&& \\
&& 1 && 4 && 6 && 4 && 1 && \\
& 1 && 5 && 10 && 10 && 5 && 1 & \\
1 && 6 && 15 && 20 && 15 && 6 && 1
\end{array}
$$

Kjer vsaka $i$-ta vrstica zaznamuje množico z $i$ elementi.
Vsak $j$-ti stolpec pa število $j$-elementnih podmnožic.

**Binomski izrek**

$$(x+y)^{n} = \sum_{0}^{n}\binom{\,n\,}{\,i\,}a^{i}b^{n-i}$$

Za to potrebujemo komutativni kolobar oz. da $a$ in $b$ komutirata in enoto če definiramo še $(a+b)^{0}$

>[!|dokaz]- Dokaz:
>1\. Način - indukcija po $n$-ju
>2\. Način - krajša ampak z idejo indukcije
>$$(a+b)^{n}=\sum_{k}^{}\binom{\,n\,}{\,k\,}a^{n-k}b^{k}$$
>$$(a+b)^{n} = (a+b)^{n-1}(a+b)$$
>$$= (\sum_{k}^{}\binom{\,n-1\,}{\,k\,}a^{n-1-k}b^{k})(a+b)$$
>$$\sum_{k}^{}\binom{\,n-1\,}{\,k\,}a^{n-k}b^{k} + \sum_{k}^{} \binom{\,n-1\,}{\,k\,}a^{n-1-k}b^{k+1}$$
>$$\sum_{k}^{}\binom{\,n-1\,}{\,k\,}a^{n-k}b_{k}+\sum_{k}^{}\binom{\,n-1\,}{\,k-1\,}a^{n-k}b^{k}$$
>$$\sum_{k}^{}(\binom{\,n-1\,}{\,k\,} + \binom{\,n-1\,}{\,k-1\,})a^{n-k}b^{k}$$
>3\. Način kombinatorični dokaz
>
>Kombinatorični dokaz Binomskega izreka, ki trdi, da je $(x+y)^n = \sum_{k=0}^{n} \binom{n}{k} x^{n-k} y^k$, se osredotoča na razumevanje, kako nastanejo posamezni členi v razširitvi produkta. Izraz $(x+y)^n$ predstavlja produkt $n$ enakih faktorjev $(x+y)$, torej $\underbrace{(x+y)(x+y)\cdots(x+y)}_{n \text{ faktorjev}}$. Ko ta produkt razširimo, vsak posamezni člen nastane z izbiro bodisi $x$ ali $y$ iz vsakega od $n$ oklepajev in nato pomnožitvijo teh izbranih elementov.
> 
> Oglejmo si splošni člen $x^{n-k}y^k$ v tej razširitvi, kjer $k$ predstavlja število faktorjev $y$ in $n-k$ število faktorjev $x$. Da bi dobili ta člen, moramo izbrati $y$ iz natanko $k$ oklepajev, medtem ko moramo iz preostalih $n-k$ oklepajev izbrati $x$. Ker je vrstni red izbire nepomemben, je ključno vprašanje, na koliko različnih načinov lahko izberemo teh $k$ oklepajev izmed vseh $n$ razpoložljivih oklepajev, iz katerih bomo vzeli $y$.
> 
> Število načinov za izbiro $k$ oklepajev iz množice $n$ oklepajev je natanko binomski koeficient $\binom{n}{k}$, kar je po definiciji število kombinacij brez ponavljanja. Vsak od teh $\binom{n}{k}$ načinov ustvari natanko en primerek člena $x^{n-k}y^k$. Ko se vsi ti primerki v končni vsoti seštejejo, je skupni koeficient pri členu $x^{n-k}y^k$ enak $\binom{n}{k}$. Ker ta logični argument velja za vsako vrednost $k$ od $0$ do $n$, s tem dokažemo, da je Binomski izrek resničen in da je celotna razširitev enaka vsoti teh členov: $(x+y)^n = \sum_{k=0}^{n} \binom{n}{k} x^{n-k} y^k$.


Pogosto pišemo tudi 

$$(1+x)^{n} = \sum_{0}^{n}\binom{\,n\,}{\,k\,}x^{k}$$

***
### Izbori

Imamo $n$ oštevilčenih kroglic in izberemo $k$ kroglic oz. $n$ elementov na $k$ mestih.

Razlikujemo med tem ali je **vrstni red pomemben** ali ne in ali lahko izbiro vračamo nazaj oz. so **dovoljene ponovitve**.


| | **Ponovitve so Dovoljene (DA)** | **Ponovitve niso Dovoljene (NE)** |
| :---: | :---: | :---: |
| **Vrstni red je Pomemben (DA)** | **Variacije s ponavljanjem** | **Variacije (Permutacije) brez ponavljanja** |
| | $$n^k$$ | $$\frac{n!}{(n-k)!}$$ |
| **Vrstni red ni Pomemben (NE)** | **Kombinacije s ponavljanjem** | **Kombinacije brez ponavljanja** |
| | $$\binom{k+n-1}{n-1}$$ | $$\binom{n}{k} = \frac{n!}{k!(n-k)!}$$ |

**Kombinacije s ponavljanjem**

Če imamo $n$ elementov ki se lahko ponavljajo in jih hočemo razporediti na $k$ mest.

Ker vrstni red ni pomemben lahko pri vseh izbirah kjer ponavljamo elemente  le-te damo skupaj enega za drugega.

Sedaj imamo za recimo $n=2, k=3$ namesto $*_{1}*_{2}*_{1}$ vedno $*_{1}*_{1}*_{2}$.

Torej lahko vse kombinacije s ponavljanjem predstavimo z zaporedjem kjer so vsi ponovljeni elementi drug za drugim.

Sedaj lahko vpeljemo pregrade ki stojijo med skupinami. Torej če imamo neke $1,...,n$ elemente mestih jih lahko grupiramo in vidimo da jih lahko ločimo z $n-1$ pregradami. Sedaj moramo le ugotoviti rapzporeditev tako da jih bo $k$. 

Če vzamemo le pregrade in $k$ mest potem bo veljalo da tam kjer so mesta med pregradami damo pripadajoče elemente.

Te pregrade lahko imajo ali nimajo vmes prostora kjer stoji dejanski element npr. $11|2|||$ s tem lahko definiramo vsko kombinacijo s ponavljanjem.

Če dodamo našim $k$ prostim mestom še mesta za pregrade dobimo $k + n-1$ mest. Opazimo da je s postavitvijo pregrad že definirana kombinacija saj ostane $k$ mest kjer so po skupinah ločeni elementi.

Vidimo da je v resnici izbira $n-1$ mest za pregrade iz $k+n-1$ vseh mest - za pregrade in elemente $n-1 + k$.

Torej je enačba

$$\binom{\,k+n-1\,}{\,n-1\,}$$

Kar je enako

$$\binom{\,k+n-1\,}{\,k\,}$$

***

### Kompozicije

Kompozicija števila $n$ je $k$-terica $\lambda_{i}$, kjer velja $\lambda_{i} \in [n] \Rightarrow$ torej $\lambda_{i} \geq 1$.

$$\sum_{i}^{}\lambda _{i} = n$$

$\lambda_{i}$ so členi kompozicije
$l$ je dolžina kompozicije
$n$ je velikost kompozicije

To si lahko predstavljamo s tem da imamo $n$ elementov in med vsako lahko damo pregrado lahko pa ne. 

Tako imamo skupno število kompozicij enako

$$2^{n-1}$$

saj imamo $n-1$ pregrad ki jih lahko postavimo ali ne.

Za 0 velja da ima eno kompozicijo - prazno kompozicijo.

Št kompozicij števila $n$ dolžine $k$ da imamo $n-1$ aktivnih mest a lahko aktiviramo le $k-1$ pregrad.

$$\binom{\,n-1\,}{\,k-1\,}$$
***
**Šibka kompozicija** števila $n$ je $\lambda = (\lambda_{1},...,\lambda_{n}) \,;\; \lambda_{i}\geq 0$.

Koliko je šibkih kompozicij nekega števila $n$ dolžine $k$.

>[!|dokaz]- Dokaz:
> 1\. Način
> Imamo neko šibko kompozicijo $0+0+3+1+0+2+0+0+1$ kar je 7.
> 
> $$||***|*||**|||*$$
> 
> Imamo $n+k-1$ objektov in jih dajemo na $k-1$ mest kamor damo pregrade.
> 
> $$\binom{\,n+k-1\,}{\,k-1\,}$$
> 
> 2\. Način
> 
> $$\lambda_{1}+...+\lambda_{k} = n \,;\; \lambda_{i} \geq 0$$
> 
> $$\mu_{i}= \lambda_{i}+1$$
> $$\mu_{1}+...+\mu_{k}=n+k$$
> $$\binom{\,n+k-1\,}{\,k-1\,}$$

Šibke kompozicije lahko predstavimo z $n$ elementi ki jih ločimo s pregradami. Ker je $k$ mest imamo $k-1$ pregrad.

To je podobno kombinacijam s ponavljanjem in sicer $k$ mest v šibki kompoziciji predstavlja $k$ elementov ki se lahko ponavljajo : vsako mesto predstavlja neko množico ponovitev, število $n$ šibke kompozicije pa predstavlja število mest na katere lahko damo teh $k$ elementov ki se lahko ponavljajo. Velja da je šibka kompozicija $n$ na $k$ mest enako kot kombinacija s ponavljanjem $k$ elementov na $n$ mest torej

$$\binom{\,n+k-1\,}{\,k-1\,}$$

Ker je šibkih kompozicij števila $n$ neskončno o vseh šibkih kompozicijah ne govorimo zares. Lahko rečemo da mora biti dolžina maksimalno $n$ kar pa je le šibka kompozicija $n$ z dolžino $n$. Torej $\binom{\,2n-1\,}{\,n-1\,}$

***

### Multinomski koeficienti

**Multimnožica** je množica kjer se elementi lahko ponavljajo.

$$A = \{ 1,1,1,2,2,3,3\} = \{ 1^{3}, 2^{2}, 3^{2}\}$$

Multimnžica $M$ je definirana kot par množice elementov $S$ in preslikave ki slika vsak element množice $S$ v število ponovitev v multimnožici.

$$M = (S, \varphi)$$

$S$ je množica, $\varphi: S \rightarrow \mathbb{N}$

$$A = (S, \varphi)$$
$$S = [4], \varphi(1)=3, \varphi(2)=1,...$$

Naj bo permutacija multimnožice mešanje elementov, kjer ne ločimo med istimi elementi.
To pomeni da ko imamo $a_{1}a_{2}b_{1}$ je enako kot $a_{2}a_{1}b_{1}$.

**Primer**

$$11223,12123,11322,...$$ 

Dobimo jih lahko z izbiranjem mest za iste elemente torej 2 mesti izberemo od 5 za enke, 2 za dvojke in 1 za trojke:

Za enke imamo $\binom{\,5\,}{\,2\,}$ za dvojek $\binom{\,3\,}{\,2\,}$ za trojek $\binom{\,1\,}{\,1\,}$.

$$\binom{\,5\,}{\,2\,} \binom{\,3\,}{\,2\,} \binom{\,1\,}{\,1\,} = 30$$

Lahko pa ugotovimo da so to vse permutacije ki jih lahko grupiramo po temu da ugotovimo koliko elementov je v skupini kjer so elementi med katerimi ne razlikujemo pomešani, kar so njegove permutacije. V taki skupini jih je natanko $k!$, kjer je element ponovljen $k$-krat. Torej delimo s številom členov v tej skupini da dobimo število dejanskih različnih skupin.

Imamo $5!$ načinov ampak se znebimo permutacij enk in dvojk, torej 

$$\frac{5!}{2!2!}$$
***
Imamo $M = \{ 1^{a}, 2^{a_{2}},...,k^{a_{k}}\}$

Elemente lahko premešamo na več načinov

**1\. Način:** 
Naprej izberemo mesta za enke $\binom{\,n\,}{\,a_{1}\,}$ potem izberemo mesta za dvojke $\binom{\,n-a_{1}\,}{\,a_{2}\,}$, potem trojke $\binom{\,n-a_{1}-a_{2}\,}{\,a_{3}\,}$ in tako naprej do$\binom{\,a_{k}\,}{\,a_{k}\,}$

$$\binom{\,n\,}{\,a_{1}\,}\binom{\,n-a_{1}\,}{\,a_{2}\,}...\binom{\,a_{k}\,}{\,a_{k}\,}$$
$$\frac{n!}{a_{1}(n-a_{1})!}\frac{(n-a_{1})!}{a_{2}!(n-a_{1}-a_{2})!}...$$

Vse se pokrajša in dobimo $$\frac{n!}{a_{1}!...a_{k}!}$$

**2\. Način** 
$1_{1},...,1_{a_{1}},2_{1},...,2_{a_{2}},...,k_{1},...,k_{a_{k}}$

$n!$ permutacij, izbrišemo vsako permutacijo multimnožice dobimo

$a_{1}!a_{2}!...a_{k!}$-krat

$$\binom{\,n\,}{\,a_1,...,a_{k}\,}:=\frac{n!}{a_{1}!...a_{k}!}$$

kjer je 

$$a_{1}+...+a_{k} = n$$

Temu pravimo **multinomski koeficient**.

$$\binom{\,a_{1}+a_{2}\,}{\,a_{1},a_{2}\,} = \binom{\,a_{1}+a_{2}\,}{\,a_{1}\,} = \binom{\,a_{1}+a_{2}\,}{\,a_{2}\,}$$
$$\binom{\,n\,}{\,k\,} = \binom{\,n\,}{\,k,n-k\,}$$

**Multinomski izrek**

$$(x_{1}+...+x_{k})^{n} = \sum_{a_{1}+...+a_{k} = n} \binom{\,n\,}{\,a_{1},...,a_{k}\,} x_{1}^{k_{1}}...x_{k}^{k_{k}}$$


***




**Načelo vključitev izključitev** *Principle of inclusion and exclusion*

$$
\left| \bigcup_{i=1}^{n} A_i \right| = $$ 
$$ \sum_{i} |A_i| - \sum_{i < j} |A_i \cap A_j| + \sum_{i < j < k} |A_i \cap A_j \cap A_k| - \cdots + (-1)^{n-1} \left| \bigcap_{i=1}^{n} A_i \right|$$

Kot vidimo seštevamo in odštevamo vedno večje preseke množic. Indeksi zaznamujejo vse kombinacije množic $A_{i}$ ki jih imamo. Torej če imamo $n$ množic - $A_{1,...,n}$ bomo seštevali moči množic katerih indeksi bojo neka podmnožica indeksov. Torej pri odštevanju preseka 2 množic bomo imeli $A_{i}\cap A_{j} \,;\; \{ i,j\}\subset [n]$ torej $\sum_{I \subset [n], |I| = 2}^{}|A_{i}\cap A_{j}|$. 

To bomo počeli za za vsako podmnožico indeksov vseh velikosti, vse kar se spremnija je le predznak zato lahko zapišemo




$$ \left| \bigcup_{i=1}^{n} A_i \right| = \sum_{\emptyset \ne I \subseteq \{1, \dots, n\}} (-1)^{|I|-1} \left| \bigcap_{i \in I} A_i \right| $$

Če definiramo presek 

$$A_{I}:=\{ a \in A:a \in A_{i} , \forall i \in I\}$$

Dobimo formulo

$$ \left| \bigcup_{i=1}^{n} A_i \right| = \sum_{\emptyset \ne I \subseteq \{1, \dots, n\}} (-1)^{|I|-1} \left| A_{I} \right| $$

**Dokaz: to-do**



**Ekvivalentno lahko uporabimo deMorganove zakone**

Vedno predpostavljamo da je $A_{1},...,A_{n} \subset A$, da lahko definiramo komplement $A_{i}^{C}$ kot $A - A_{i}$.

$$A_{I}=\{ a \in A:a \in A_{i} \forall i \in I\}$$

$$A_{\emptyset}= \{ a \in A:a \in A, \forall i \in \emptyset\} = A$$
$$|A_{\emptyset}| = A$$
$$|\emptyset| = 0$$

Velja

$$
\left|\bigcup A_{i}\right| = \left|\left(\bigcap A_{i}^{c}\right)^{c}\right|
$$
$$
\left|\bigcup A_{i}\right| = |A| - \left|\bigcap A_{i}^{c}\right|
$$
$$
\left|\bigcap A_{i}^{c}\right| = |A| - \left|\bigcup A_{i}\right|
$$
$$
= |A| - \sum_{\emptyset \neq I \subseteq [n]} (-1)^{|I|-1} |A_{I}|
$$

Ker je $|A|$ definiran kot $|A_\emptyset|$ ga lahko vključimo v vsoto in razširimo mejo $I \subset [n]$. Prej pa še minus izpred vsote damo v vsoto in dobimo $(-1)^{|I|}$.


$$
= |A| + \sum_{\emptyset \neq I \subseteq [n]} (-1)^{|I|} |A_{I}|
$$
$$
= \sum_{I \subseteq [n]} (-1)^{|I|} |A_{I}|
$$

$$\Rightarrow$$
$$\left|\bigcap_{i=1}^{n} A^{C}_{i}\right| = \sum_{I \subset [n]}^{}(-1)^{|I|}\left|\bigcap_{i \in I} A_{i} \right| $$

Velja da je torej komplement unije enak preseku komplementov $A_{i}$ kar je enako vsoti kombinacij presekov.

$$ \left|\left(\bigcup A_{i}\right)^{C} \right| = \left|\bigcap_{i=1}^{n} A^{C}_{i}\right| = \sum_{I \subset [n]}^{}(-1)^{|I|}\left|\bigcap_{i \in I} A_{i} \right|$$

*Še kle rabm dokaz* to-do

**Kronickerjeva delta**

$$\delta_{ij} = \begin{cases}
1: i = j \\
0: i \neq j \\
\end{cases}$$

Primer uporabe

$$0^{n} = \delta_{0n}$$

*Vedno je enaka 0 razen pri $0^{0} = 1$.*

$$\delta_{0m} = \sum_{k=0}^{m}\binom{\,m\,}{\,k\,}(-1)^{k}$$

>[!|dokaz]- Dokaz:
> 
> $$ \left| \bigcup_{i=1}^{n} A_i \right| = \sum_{i} |A_i| - \sum_{i < j} |A_i \cap A_j| + \sum_{i < j < k} |A_i \cap A_j \cap A_k| - \cdots + (-1)^{n-1} \left| \bigcap_{i=1}^{n} A_i \right| $$
> 
> ---
> 
> ## Dokaz Principa Vključevanja in Izključevanja (PVII) za $n$ Množic
> 
> Dokaz temelji na preštevanju, kolikokrat je poljuben element $x$, ki pripada uniji, prispeval k vsoti na desni strani enačbe (DSE).
> 
> **Cilj dokaza:** Pokazati, da vsak element $x$, ki pripada vsaj eni množici $A_i$ (tj. $x \in \bigcup_{i=1}^{n} A_i$), prispeva k DSE natanko **enkrat**.
> 
> ### 1. Definicija elementa in število njegovih pojavitev
> 
> Vzemimo poljuben element $x$ iz unije $\bigcup_{i=1}^{n} A_i$.
> 
> Naj bo $m$ **število množic $A_i$, ki vsebujejo element $x$**. Ker je $x$ v uniji, vemo, da je $m \ge 1$.
> $$1 \le m \le n$$
> 
> ### 2. Prispevek elementa $x$ k desni strani enačbe (DSE)
> 
> Preštejmo, kolikokrat $x$ prispeva k posameznim vsotam v PVII:
> 
> #### Korak 1: Vsota enojnih množic (Sum $\sum |A_i|$)
> Element $x$ je vključen v $m$ množic. Zato prispeva k prvi vsoti $m$-krat.
> $$\text{Prispevek: } \binom{m}{1}$$
> 
> #### Korak 2: Vsota dvojnih presekov (Sum $\sum |A_i \cap A_j|$)
> Element $x$ se pojavi v preseku dveh množic $A_i \cap A_j$ samo, če sta $A_i$ in $A_j$ med tistimi $m$ množicami, ki vsebujejo $x$.
> Število parov množic, izbranih iz $m$ množic, je $\binom{m}{2}$.
> $$\text{Prispevek: } \binom{m}{2}$$
> 
> #### Korak $k$: Vsota $k$-terih presekov (Sum $\sum |A_{i_1} \cap \dots \cap A_{i_k}|$)
> Element $x$ prispeva k vsoti $k$-terih presekov, če je izbran $k$-terice množic, ki vsebujejo $x$. To je mogoče le, če izberemo $k$ množic izmed tistih $m$ množic, ki element $x$ vsebujejo.
> $$\text{Prispevek: } \binom{m}{k}$$
> 
> #### Korak $n$: $n$-kratni presek
> Ker je $x$ prisoten v le $m$ množicah, in $m \le n$, prispeva k $n$-kratnemu preseku le, če je $m=n$, torej $\binom{n}{n}$. Na splošno je prispevek $\binom{m}{n}$ (kar je 0, če je $m < n$).
> 
> ### 3. Skupni prispevek elementa $x$
> 
> Skupni prispevek elementa $x$ k desni strani enačbe (DSE) je alternirajoča vsota teh prispevkov (upoštevajoč predznake v PVII):
> 
> $$\text{DSE prispevek}(x) = \binom{m}{1} - \binom{m}{2} + \binom{m}{3} - \cdots + (-1)^{m-1} \binom{m}{m} + \cdots + (-1)^{n-1} \binom{m}{n}$$
> 
> Ker je $\binom{m}{k} = 0$, če je $k > m$, se vsota ustavi pri $k=m$:
> 
> $$\text{DSE prispevek}(x) = \binom{m}{1} - \binom{m}{2} + \binom{m}{3} - \cdots + (-1)^{m-1} \binom{m}{m}$$
> 
> ### 4. Uporaba Binomske formule
> 
> Zdaj uporabimo splošno znano identiteto, ki izhaja iz razvoja $(1-1)^m = 0$. Iz binomskega izreka vemo:
> 
> $$(1 + y)^m = \sum_{k=0}^{m} \binom{m}{k} y^k$$
> 
> Vstavimo $y = -1$:
> 
> $$(1 + (-1))^m = \sum_{k=0}^{m} \binom{m}{k} (-1)^k$$
> 
> $$0 = \binom{m}{0} (-1)^0 + \binom{m}{1} (-1)^1 + \binom{m}{2} (-1)^2 + \cdots + \binom{m}{m} (-1)^m$$
> 
> $$0 = \binom{m}{0} - \binom{m}{1} + \binom{m}{2} - \binom{m}{3} + \cdots + (-1)^m \binom{m}{m}$$
> 
> Ker vemo, da je $\binom{m}{0} = 1$, lahko preuredimo enačbo:
> 
> $$1 = \binom{m}{1} - \binom{m}{2} + \binom{m}{3} - \cdots + (-1)^{m-1} \binom{m}{m}$$
> 
> ### 5. Zaključek
> 
> Ugotovili smo, da je skupni prispevek poljubnega elementa $x$ k desni strani enačbe (DSE) natanko:
> 
> $$\text{DSE prispevek}(x) = 1$$
> 
> Ker vsak element $x$ v uniji prispeva k DSE natanko 1-krat, je vsota na DSE natanko enaka številu elementov v uniji.
> 
> $$\left| \bigcup_{i=1}^{n} A_i \right| = \text{Število elementov } x \text{ v uniji} \times 1$$
> 
> To dokazuje Princip vključevanja in izključevanja za $n$ množic.


*Računanje vseh surjekcij iz $A$ v $B$*


Število surjekcij $N_{\text{sur}}$ je:

$$ N_{\text{sur}} = \sum_{k=0}^{m} (-1)^k \binom{m}{k} (m-k)^n $$

**Razlaga formule:**
1. **$k=0$ (Vsi):** $\binom{m}{0} m^n$. To je skupno število vseh funkcij.
2. **$k=1$ (Odštejemo, kjer manjka 1 element):** $\binom{m}{1} (m-1)^n$. Izberemo $k=1$ element, ki ga funkcija ne doseže, in preštejemo vse funkcije, ki preslikajo $A$ v preostalih $m-1$ elementov.
3. **$k=2$ (Prištejemo nazaj, kjer manjkata 2 elementa):** $\binom{m}{2} (m-2)^n$. To so funkcije, ki ne dosežejo dveh izbranih elementov. Te so bile dvakrat odštete prej, zato jih moramo prišteti nazaj.
4. **... do $k=m$:** $\binom{m}{m} (m-m)^n = 1 \cdot 0^n$ (če je $n \ge 1$; če je $n=0$, je 1).

### Končna formula za število surjekcij

$$ \text{Število surjekcij } (n \to m) = m! \cdot S(n, m) = \sum_{k=0}^{m} (-1)^k \binom{m}{k} (m-k)^n $$


***
**Preštevanje premestitev**: premutacije brez negibne točke : torej $\pi(i) \neq i$.
>[!|hide]-  
> Predstavljeni izpisek natančno opisuje prve korake uporabe **Principa vključitve in izključitve (PIE)** za izračun števila **deranžmajev** ($D_n$).
> 
> Deranžma je posebna vrsta permutacije, pri kateri noben element ni preslikan sam vase (tj. nima fiksne točke).
> 
> Spodaj je podrobna razlaga posameznih korakov in izpeljave formule.
> 
> ---
> 
> ## B) Preštevanje deranžmajev (Permutacije brez fiksne točke)
> 
> **Cilj:** Izračunati število permutacij $D_n$ množice $\{1, 2, \dots, n\}$, za katere velja, da je $\pi(i) \neq i$ za vsak $i \in \{1, \dots, n\}$.
> 
> Za izračun uporabimo Princip vključitve in izključitve.
> 
> ### 1. Določitev Univerzalne Množice ($U$)
> 
> **Naj bo $U$ množica vseh permutacij.**
> *   Velikost univerzalne množice je:
>     $$|U| = n!$$
> *   To je celotno število možnih razporeditev $n$ elementov.
> 
> ### 2. Določitev "Slabih" Lastnosti (Množice $A_i$)
> 
> **Naj bo $A_i$ množica vseh permutacij, ki imajo fiksno točko $i$.**
> *   To pomeni, da je za $\pi \in A_i$ izpolnjeno: $\pi(i) = i$.
> *   $A_i$ predstavlja "slabe" permutacije, saj kršijo pogoj, da noben element ni fiksna točka.
> *   Cilj je izračunati: $$D_n = |U| - |\bigcup_{i=1}^n A_i|$$
>     (Število deranžmajev je število vseh permutacij minus število tistih, ki imajo vsaj eno fiksno točko).
> 
> ### 3. Izračun Velikosti Posameznega Preseka
> 
> Po Principu vključitve in izključitve moramo izračunati vsote velikosti presekov $k$ množic, imenovanih $S_k$. Najprej določimo velikost posameznega preseka $k$ množic.
> 
> **Obravnavamo presek $A_{i_1} \cap A_{i_2} \cap \dots \cap A_{i_k}$:**
> *   Ta presek predstavlja množico permutacij, ki imajo fiksne točke na *natančno določenih* $k$ mestih: $i_1, i_2, \dots, i_k$.
> *   Ker so ta mesta fiksirana ($\pi(i_j) = i_j$), preostalih $n - k$ elementov lahko poljubno preuredimo med preostalimi $n - k$ mesti.
> *   Število načinov preureditve $n-k$ elementov je **$(n-k)!$**.
> *   Torej, velikost katerega koli določenega preseka $k$ množic je:
>     $$|A_{i_1} \cap \dots \cap A_{i_k}| = (n-k)!$$
> 
> ### 4. Izračun Vsote Presekov ($S_k$)
> 
> $S_k$ je vsota velikosti vseh možnih presekov, ki vključujejo *točno $k$* množic $A_i$.
> 
> *   **Število možnih presekov $k$ množic:** Ker nas ne zanimajo, kateri elementi so fiksne točke, temveč le koliko jih je ($k$), moramo izbrati $k$ indeksov izmed $n$ možnosti. To storimo na $\binom{n}{k}$ načinov.
>     $$\text{Število presekov} = \binom{n}{k}$$
> *   **Izračun $S_k$:** Ker je velikost vsakega takšnega preseka $(n-k)!$, je vsota vseh $k$-presekov produkt števila možnosti in velikosti posameznega preseka:
>     $$S_k = \sum_{1 \le i_1 < \dots < i_k \le n} |A_{i_1} \cap \dots \cap A_{i_k}| = \binom{n}{k} (n-k)!$$
> 
> **Poenostavitev $S_k$:**
> Uporabimo definicijo binomskega koeficienta $\binom{n}{k} = \frac{n!}{k!(n-k)!}$:
> $$S_k = \frac{n!}{k!(n-k)!} \cdot (n-k)!$$
> $$S_k = \frac{n!}{k!}$$
> 
> ---
> 
> ### Končna Formula za Deranžmaje ($D_n$)
> 
> S pomočjo $S_k$ in Principa vključitve in izključitve lahko sedaj izračunamo število deranžmajev ($D_n$).
> 
> Število permutacij, ki imajo vsaj eno fiksno točko, je:
> $$|\bigcup_{i=1}^n A_i| = S_1 - S_2 + S_3 - \dots + (-1)^{n-1} S_n = \sum_{k=1}^n (-1)^{k-1} S_k$$
> 
> Število deranžmajev $D_n$ je torej:
> $$D_n = |U| - |\bigcup_{i=1}^n A_i| = n! - \sum_{k=1}^n (-1)^{k-1} S_k$$
> 
> Če vstavimo izračun za $S_k = \frac{n!}{k!}$:
> $$D_n = n! - \sum_{k=1}^n (-1)^{k-1} \frac{n!}{k!}$$
> 
> Lahko preoblikujemo tako, da vključimo $k=0$ člen (ki je $S_0 = |U| = n!$):
> $$D_n = n! + \sum_{k=1}^n (-1)^{k} \frac{n!}{k!} = \sum_{k=0}^n (-1)^{k} \frac{n!}{k!}$$
> 
> **To je končna formula za število deranžmajev $D_n$.**


***

**Eulerjeva funkcija**

$$\varphi(n) = |\{ i \in [n] \,;\;i \perp n\}|$$

Razstavimo število na prafaktorje

$$n = p_{1}^{e_{1}}...p_{k}^{e_{k}}$$

Hočemo prešteti števila ki niso deljiva z nobenim od teh prafaktorjev, in njihovo število odštejemo od $n$.

Imamo $[n] \Rightarrow |[n]| = n$

Naj bo $A_{i}$ množica števil ki so deljiva z s prafaktorjem $p_{i}$.

Če odštejemo presek vseh $A_{i}$ smo lahko na primer število $p_{1}p_{2} \leq n$ odšteli dvakrat zato uporabimo princip o vključitvi in izključitvi.

Iščemo torej komplement unije $A_{i}$.

$$A_{i}=\{ m \in [n]; p_{i}|m\}$$

Velja da je $|A_{i}| = \frac{n}{p_{i}}$

$$A_{i} \cap A_{j} = \{ m \in [n]; p_{i}p_{j}|m\}$$

Kot tudi da je $|A_{i} \cap A_{j}| = \frac{n}{p_{i}p_{j}}$

$$A_{I} = \{ m \in [k];  \prod_{i \in I} p_{i} |m\}$$

Torej velja

$$|A_{I}| = \frac{n}{\prod_{i \in I}\,p_{i}}$$

Če vzamemo unijo vseh množic kjer so števila deljiva z nekim prafaktorskim razcepom $n$ in vzamem njen komplement potem dobim vse števila ki so si tuja.

$$\left(\bigcup_{I \subset [n]} A_{I} \right)^{C}= \bigcap_{I \subset [n]} A_{I}^{C}$$

$$\sum_{I \subset [k]}^{}(-1)^{|I|} \cdot  n \cdot  \frac{1}{\prod_{i \in I}p_{i}}$$


$$= n \cdot \prod_{p|n}(1-\frac{1}{p})$$

***

### Načrti in t-načrti


**Incidenca** je relacija pripadnosti.

Velja da je **struktura incidence** urejena trojica $S = (P,B,I)$ kjer velja

$P$ je množica **točk**. $B$ je množica **blokov**.
$I$ pa je **relacija incidence** oz. podmnožica $P \times B$.

Relacija $I$ določa ali točka $p$ stoji v relaciji z blokom $b$.
Če sta v relaciji rečemo da je točka $p$ incidienčna bloku $b$, oz. $p$ pripada $b$.

Primer je evklidska geometrija kjer pravimo da je točka incidenčna neki premici če točka leži na premici.

Primer je tudi graf kjer je točka incidenčna povezavi če je točka ena od končnih vozlišč povezave.

Iz tega izhaja tudi incidenčna matrika kjer vrstice predstavljajo točke, stolpci pa bloke in imamo 1 če imamo incidenčno relacijo drugače 0.

***

**Načrt** je struktura definirana kot množica podmnožic množice $[v]$ - **blokov**, velikosti $k$, kjer velja da se vsaka točka pojavi v natanko $\lambda$ blokih.

$$\mathcal{B} = \{ B_{1},...,B_{b}\}$$
$$|\mathcal{B}| = b$$
$$B_{i} \subset [v]$$
$$|B_{i}| = k$$
$$v' \in [v] \text{ je element natanko } \lambda \text{ množic } B_{i}$$

Rečemo da sta $v' \text{ in } B_{i}$ v relaciji incidence če velja $v' \in B_{i}$.

Lahko narišemo tabelo kjer so po stolpcih bloki po vrsticah pa elementi $[v]$ in damo kljukico tam kjer imamo incidenco.

Iz tega dobimo da velja formula

$$k \cdot b = \lambda \cdot v$$

torej število blokov krat velikost blokov je enako številu elementov krat ponovitvi elementov v blokih.

Iz enačbe lahko izpeljemo da je 

$$b = \frac{\lambda \cdot v}{k}$$

Torej mora **$k$ deliti $\lambda \cdot v$.**

Velja tudi da je

$$b \leq \binom{\,v\,}{\,k\,}$$

To pomeni da je število blokov manjše ali enako številu $k$ velikih podmnožic.

Iz česar lahko izpeljemo

$$b = \frac{\lambda v}{k} \leq \binom{\,v\,}{\,k\,}$$
$$\frac{\lambda v}{k} \leq \frac{(v-1)!}{k!(v-k)!}$$
$$\lambda \leq \binom{\,v-1\,}{\,k-1\,}$$

Izberemo točko $x$ in pogledamo strukturo blokov ki lahko vsebujejo $x$: $\{ x,...\}$, torej imamo $k-1$ veliko množico, izbiramo pa med $v-1$ elementi, to so vse možnosti blokov z elementom $x$, torej mora število blokov ki vsebuje $x$ : $\lambda$ biti manjše od $\binom{\,v-1\,}{\,k-1\,}$.

Pogoja da je $k|v \cdot \lambda$ in da je $\lambda \leq \binom{\,v-1\,}{\,k-1\,}$ sta zadostna da načrt $(v,k,\lambda)$ obstaja.


>[!|hide]- **Postopek konstrukcije načrta**:
> 
> #### 1. Definicija Problema
> 
> Dani so parametri $v, k, \lambda \in \mathbb{N}$. Cilj je konstruirati množico blokov $\mathcal{B}$, kjer je vsak blok $B \in \mathcal{B}$ $k$-elementna podmnožica množice točk $V = \{1, 2, \dots, v\}$, tako da vsaka točka $x \in V$ pripada natanko $\lambda$ blokom. Taka struktura $(V, \mathcal{B})$ se imenuje **1-$(v, k, \lambda)$-načrt**.
> 
> #### 2. Vhodni in Izhodni Podatki
> 
> *   **Vhod:**
>     *   $v \in \mathbb{N}$: število točk.
>     *   $k \in \mathbb{N}$: velikost blokov, $k \le v$.
>     *   $\lambda \in \mathbb{N}$: ciljna ponovitvena stopnja.
> *   **Izhod:**
>     *   Množica blokov $\mathcal{B}$, ki tvori 1-$(v, k, \lambda)$-načrt.
> 
> #### 3. Predpogoji
> 
> Za obstoj 1-načrta mora veljati nujen pogoj deljivosti:
> $$ k \mid v\lambda $$
> Število blokov $b$ je določeno z $b = \frac{v\lambda}{k}$ in mora biti celo število.
> 
> #### 4. Algoritem
> 
> **Korak 1: Inicializacija**
> 1.1. Izračunaj potrebno število blokov: $b := \frac{v\lambda}{k}$.
> 1.2. Generiraj začetno množico $\mathcal{B}_0$, ki vsebuje $b$ poljubnih, med seboj različnih, $k$-elementnih podmnožic množice $V$.
> 1.3. Postavi števec iteracij $t := 0$.
> 
> **Korak 2: Analiza Stanja in Pogoj za Ustavitev**
> 2.1. Za trenutno množico blokov $\mathcal{B}_t$ izračunaj ponovitveno stopnjo $d_x^{(t)}$ za vsako točko $x \in V$:
>    $$ d_x^{(t)} := |\{ B \in \mathcal{B}_t : x \in B \}| $$
> 2.2. Preveri pogoj za ustavitev:
>    **ČE** $d_x^{(t)} = \lambda$ za vse $x \in V$, **POTEM**
>    Vrni $\mathcal{B}_t$ in končaj algoritem.
>    **SICER**
>    Nadaljuj na Korak 3.
> 
> **Korak 3: Izbira Kandidatov za Zamenjavo**
> 3.1. Definiraj množici točk, ki ne ustrezata pogoju:
>    *   Množica "prepogostih" točk: $V_{over} := \{ x \in V \mid d_x^{(t)} > \lambda \}$
>    *   Množica "preredkih" točk: $V_{under} := \{ x \in V \mid d_x^{(t)} < \lambda \}$
> 3.2. Izberi poljuben element $i \in V_{over}$ in poljuben element $j \in V_{under}$.
> 
> **Korak 4: Izvedba Zamenjave (Trade-off)**
> 4.1. Poišči blok $B \in \mathcal{B}_t$, ki zadošča pogojema:
>    $$ i \in B \quad \land \quad j \notin B $$
> 4.2. Konstruiraj nov kandidatni blok $B'$:
>    $$ B' := (B \setminus \{i\}) \cup \{j\} $$
> 4.3. Preveri veljavnost zamenjave:
>    **ČE** $B' \notin \mathcal{B}_t$, **POTEM**
>      *   Zamenjava je veljavna. Posodobi množico blokov:
>        $$ \mathcal{B}_{t+1} := (\mathcal{B}_t \setminus \{B\}) \cup \{B'\} $$
>      *   Povečaj števec iteracij: $t := t+1$.
>      *   Vrni se na **Korak 2**.
>    **SICER**
>      *   Vrni se na **Korak 4.1** in poskusi z drugim ustreznim blokom $B \in \mathcal{B}_t$.
> 
> ---
> **DODATEK: 5. Zagotovilo Napredka (Obstoj Veljavne Zamenjave)**
> 
> Ključno vprašanje je, ali se algoritem lahko "zatakne" – to je, ali lahko pride do situacije, ko za izbrani par $(i, j)$ z $d_i > \lambda > d_j$ **vsaka** možna zamenjava ustvari blok, ki že obstaja. Dokaz s protislovjem pokaže, da to ni mogoče.
> 
> 1.  **Predpostavka (protislovje):** Recimo, da se je algoritem zataknil. To pomeni, da za vsak blok $B$, ki vsebuje $i$, a ne $j$, novonastali blok $B' = (B \setminus \{i\}) \cup \{j\}$ že obstaja v zbirki $\mathcal{B}$.
> 
> 2.  **Argument s štetjem:**
>     *   Naj bo $\mathcal{B}_{i,\neg j}$ množica blokov, ki vsebujejo $i$, a ne $j$.
>     *   Naj bo $\mathcal{B}_{j,\neg i}$ množica blokov, ki vsebujejo $j$, a ne $i$.
>     *   Naša predpostavka pomeni, da vsaka zamenjava bloka iz $\mathcal{B}_{i,\neg j}$ ustvari unikaten blok v $\mathcal{B}_{j,\neg i}$. To bi pomenilo, da je število blokov prve vrste kvečjemu enako številu blokov druge vrste: $|\mathcal{B}_{i,\neg j}| \le |\mathcal{B}_{j,\neg i}|$.
> 
> 3.  **Protislovje:**
>     *   Vendar pa naša začetna izbira temelji na pogoju $d_i > d_j$. Število pojavitev $d_i$ je vsota blokov, ki vsebujejo samo $i$ ($\mathcal{B}_{i,\neg j}$), in tistih, ki vsebujejo oba ($i$ in $j$). Podobno velja za $d_j$.
>     *   Iz $d_i > d_j$ neposredno sledi, da mora biti $|\mathcal{B}_{i,\neg j}| > |\mathcal{B}_{j,\neg i}|$.
>     *   To je v neposrednem protislovju s sklepom iz točke 2.
> 
> **Zaključek:** Začetna predpostavka, da se je algoritem zataknil, je napačna. Vedno mora obstajati vsaj en blok, ki omogoča veljavno zamenjavo in napredek algoritma.
> 
> ---
> #### 6. Dokaz Konvergence
> 
> Algoritem se vedno konča v končnem številu korakov. To dokažemo z uporabo potenčne funkcije (mere napake).
> 
> 4.  **Definicija mere napake:** V koraku $t$ definirajmo mero napake $S_t$:
>     $$ S_t = \sum_{x \in V} |d_x^{(t)} - \lambda| $$
> 
> 5.  **Lastnosti mere napake:** $S_t \ge 0$, $S_t$ je sodo celo število, in algoritem se konča natanko takrat, ko je $S_t = 0$.
> 
> 6.  **Vpliv zamenjave na mero napake:** Vsaka veljavna zamenjava, ki popravi elementa $i \in V_{over}$ in $j \in V_{under}$, spremeni ponovitvene stopnje $d_i$ in $d_j$ za 1 proti ciljni vrednosti $\lambda$. To zmanjša vsoto $S_t$ za natanko 2:
>     $$ S_{t+1} = S_t - 2 $$
> 
> 7.  **Zaključek:** Ker se mera napake $S_t$ v vsaki iteraciji strogo zmanjša (kot je zagotovljeno v točki 5) in je od spodaj omejena z 0, mora algoritem po končnem številu korakov doseči stanje, kjer je $S_t = 0$. V tem stanju je $\mathcal{B}_t$ veljaven 1-načrt.


Če vzamemo načrt, ga lahko posplošimo s tem da rečemo da je $\lambda_{t}$ število ki nam pove v koliko blokih se pojavi $t$-elementna podmnožica v našem načrtu namesto v koliko blokih se pojavi nek element. 
Tej posplošitvi rečemo **$t$-načrt**.

Velja da je $\mathcal{B}$ $t$-načrt kjer velja

$$\mathcal{B} = \{ B_1,...,B_{b}\}$$
$$B_{i} \subset [v], |B_{i}| = k$$
$$\forall T \subset [v]:|T| = t , T \subset B_{i} \text{ za natanko } \lambda_{t}\text{ indeksov }i \text{ (torej v } \lambda_{t} \text{ blokih)}$$

>[!|hide]- **Fainova ravnina**  
>je $2$-načrt s parametri $(7,3,1)$ in je najmanjša možna projektna ravnina.
> 1. **Sestava:** Vsebuje natanko **7 točk** in **7 premic**.
>     
> 2. **Pravila (aksiomi):**
>     
>     - Na vsaki premici ležijo natanko **3 točke**.
>         
>     - Skozi vsako točko potekajo natanko **3 premice**.
>         
>     - Poljubni dve različni točki določata natanko eno premico.
>         
>     - Poljubni dve različni premici se sekata v natanko eni točki. **Posledica: V Fanovi ravnini ni vzporednic!**




V splošnem **ni znan potreben ali zadosten pogoj** za obstoj $t$-načrta s poljubnimi parametri za $t>1$.


>Izrek
>Vsak $t$-načrt je $t-1$-načrt in velja
>$$\lambda_{t-1} = \lambda_{t}\frac{v-t+1}{k-t+1}$$
>>[!|dokaz]+ Dokaz:
> > 
> > Dokazati moramo, da če je neka struktura $t$-načrt, potem obstaja konstanta $\lambda_{t-1}$, tako da je **vsaka poljubna** $(t-1)$-elementna podmnožica točk vsebovana v natanko $\lambda_{t-1}$ blokih. Ključno je, da to število ni odvisno od izbire podmnožice.
> > 
> > 
> > 1.  **Postavitev:**
> >     Naj bo $(V, \mathcal{B})$ dan $t$-$(v, k, \lambda_t)$-načrt.
> >     Izberimo poljubno, $(t-1)$-elementno podmnožico točk in jo poimenujmo $S$. Torej $|S| = t-1$.
> >     Naj bo $\lambda_{S}$ število blokov v $\mathcal{B}$, ki vsebujejo množico $S$.
> > 2.  **Argument z dvojnim štetjem:**
> >     Konstruriramo pare $(x, B)$, kjer velja:
> >     *   $x \in V \setminus S$ (vse točke ki niso v $S$).
> >     *   $B \in \mathcal{B}$ je blok, ki vsebuje $S$ in $x$
> > 
> > 3.  **1. način štetja (preko blokov):**
> >     *   Najprej izberemo blok $B$, ki ustreza pogojem. Koliko takih blokov obstaja? Po naši definiciji je to natanko $\lambda_{S}$ blokov, ki vsebujejo množico $S$.
> >     *   Za vsak tak blok $B$ se vprašajmo, koliko točk $x$ lahko izberemo, da ustrezajo pogojem. Točka $x$ mora biti v bloku $B$, a ne v množici $S$. Ker ima blok $B$ $k$ elementov in množica $S$ $t-1$ elementov, je število takih točk $x$ enako $|B \setminus S| = k - (t-1) = k - t + 1$.
> >     *   Skupno število parov $(x, B)$ je torej:
> >         $$ \lambda_{S} \cdot (k - t + 1) $$
> > 
> > 4.  **2. način štetja (preko točk):**
> >     *   Najprej izberemo točko $x$, ki ustreza pogojem, torej $x \in V \setminus S$. Koliko takih točk obstaja? Ker ima $V$ $v$ elementov in $S$ $t-1$ elementov, je število možnih izbir za $x$ enako $|V \setminus S| = v - (t-1) = v - t + 1$.
> >     *   Za vsako tako izbrano točko $x$ tvorimo novo množico $T = S \cup \{x\}$. Ker je $|S|=t-1$ in $x \notin S$, je $|T|=t$.
> >     *   Ker je naša struktura $t$-načrt, vemo, da je vsaka $t$-elementna podmnožica (torej tudi naša množica $T$) vsebovana v natanko $\lambda_t$ blokih.
> >     *   Skupno število parov $(x, B)$ je torej:
> >         $$ (v - t + 1) \cdot \lambda_t $$
> > 
> > 5.  **Zaključek:**
> >     Ker smo na dva različna načina prešteli isto stvar, morata biti rezultata enaka:
> >     $$ \lambda_{S} \cdot (k - t + 1) = (v - t + 1) \cdot \lambda_t $$
> >     Iz te enačbe lahko izrazimo $\lambda_{S}$:
> >     $$ \lambda_{S} = \frac{(v - t + 1)}{(k - t + 1)} \cdot \lambda_t $$
> >     Opazimo, da je izraz na desni strani **konstanta**, ki je odvisna le od parametrov načrta ($v, k, t, \lambda_t$) in **ni odvisna od specifične izbire množice $S$**.
> >     To pomeni, da je vsaka $(t-1)$-elementna podmnožica vsebovana v natanko enakem številu blokov. To število lahko poimenujemo $\lambda_{t-1}$.
> > 
> >     Torej, struktura je tudi $(t-1)$-načrt s parametrom:
> >     $$ \lambda_{t-1} = \frac{v - t + 1}{k - t + 1} \cdot \lambda_t $$
> >     **Q.E.D.** (Kar je bilo treba dokazati)
> > 

**Steinerjev sistem trojk** reda $v$ je $2$-načrt $(v,3,1)$.
Zanj velja da obstaja natanko takrat ko je $v \text{ mod } 6 = 1$ ali $v \text{ mod } 6 = 3$.
Reši enega izmed najbolj znanih problemov:
**Kirkmanov problem petnajstih šolark**:  
Kako razporediti 15 šolark v skupine po 3 za sprehod vsak dan v tednu (7 dni), tako da nobena šolarka ne hodi v paru z isto sošolko več kot enkrat?

***

**Permutacije, razdelitve in razčlenitve**

**Stirlingova števila 1. vrste** $c(n,k)$ so št. permutacij v $S_{n}$ s $k$ cikli.
*To je ekvivalenetno posedanju $n$ oseb za $k$ orkoglih miz.*


$c(4,2)$
$(\_\,\_\,\_)$ $(\_)$
$(\_\,\_)(\_\,\_)$

$c(n,k) = 0\,;\;k>n; k<0$

$c(n,n) = 1$
$c(n,0) = \delta_{n0}$
$c(n,1) = (n-1)!$
$c(n,n-1) = \binom{\,n\,}{\,2\,}$

Obstaja rekurzivna zveza

$$c(n,k) = c(n-1,k-1) + (n-1)c(n-1,k)$$

Če izberemo nek element $x$ potem lahko naprej preštejemo vse permutacije kjer je $x$ osamljen v ciklu oz. je singleton. Teh je natanko $c(n-1,k-1)$. Nato pa pogledamo še vse druge permutacije kjer izločimo $x$ iz množice, pogledamo koliko je permutacij in nato vstavimo $x$ na neko mesto v permutacijo *ker je $n-1$ števil v permutaciji je $n-1$ mest za $x$*, kar je $(n-1)c(n-1,k)$

| n\k | 0 | 1 | 2 | 3 | 4 | 5 |
|:---:|:-:|:-:|:--:|:--:|:--:|:-:|
| **0** | 1 | | | | | |
| **1** | 0 | 1 | | | | |
| **2** | 0 | 1 | 1 | | | |
| **3** | 0 | 2 | 3 | 1 | | |
| **4** | 0 | 6 | 11 | 6 | 1 | |
| **5** | 0 | 24| 50 | 35 | 10 | 1 |

Če seštejemo $c(n,k)$ po vseh $k$-jih potem velja

$$\sum_{k}^{}c(n,k) = n!$$

saj s tem štejemo vse možne permutacije, katerih je $n!$.

Poznamo $\sum_{k}^{}\binom{\,n\,}{\,k\,}x^{k} = (1+x)^{n}$. Velja tudi

$$\large \sum_{k}^{}c(n,k)x^{k} = x^{\overline{\;\!\!n}}$$

To dokažemo z indukcijo, distribuciijo, redefiniranjem $k$, ter rekurzivno zvezo.

$$x=1$$
$$\sum_{k}^{}c(n,k)1^{k} = 1^{\overline{\;\!\!n}} = n!$$

$$ $$
$$x=-x$$
$$\sum_{k}^{}c(n,k)(-x)^{k} = \sum_{k}^{}c(n,k)(-1)^{k}x^{k} = (-1)^{n}x^{\underline{\;\!\!n}} $$
$$\sum_{k}^{}{\color{green}(-1)^{n-k}c(n,k)}x^{k}  = x^{\underline{\;\!\!n}}$$

$(-1)^{n-k}c(n,k)$ pravimo **preznačeno Strilingovo število prve vrste.**
***

**Razdelitev** množice $A$ na $k$ blokov je $\{ B_{1},...,B_{k}\}$ da velja

$$\bigcup B_{i} = A \,;\;B_{i}\cap B_{j} = \emptyset \,;\;B_{i} \neq \emptyset$$

*Razdelitev množice na $k$ disjunktnih podmnožic.*

**Stirlingova števila 2. vrste** $S(n,k)$ so razdelitve množice $[n]$ na $k$ blokov.



**Bellova števila** $B(n)$ so število razdelitev na poljubno blokov.

Za $B(n)$ velja

$$B(n) = \sum_{k}^{}S(n,k)$$

$S(n,n) = 1$
$S(n,0) = \delta_{n0}$
$S(n,1) = 1$
$S(n,n-1) = \binom{\,n\,}{\,2\,}$
$S(n,2) = \frac{2^{n}-2}{2}$
$S(n,k) = 0; k<0, k>n$
$c(n,k)\geq S(n,k)$

Tudi tu velja rekurzivna zveza

$$S(n,k) = S(n-1,k-1) + k \cdot S(n-1,k)$$


Spet osamimo nek element in pogledamo možne razdelitve brez njega: $S(n-1,k-1)$. Nato pa pogledamo še razdelitve velikosti $k$ brez da vključimo element nakar še pogledamo kam ga lahko vstavimo - to pa bo natanko $k$ blokov.

Kot tudi za

$$B(n+1) = \sum_{k}^{n}\binom{\,n\,}{\,k\,}B(k)$$

Kjer si predstavljamo da izoliramo element $x$ in se odločamo koliko elementov ne bo v bloku skupaj z $x$. To naj bo $k$ elementov. Ostane nam $n-k$ elementov ki bodo skupaj z $x$. Sedaj lahko pogledamo na koliko načinov lahko izberemo $k$ elementov ki ne bodo z $x$ to je $\binom{\,n\,}{\,k\,}$, za vsako to množico pa velja da ima  $B(k)$ razcepov.

Stirlingova števila 2. vrste lahko interpretiramo tudi drugače. Vemo da **ekvivalenčna relacija** definira **ekvivalenčne razrede** za katere velja da so **neprazni in disjunktni** kar so točno tudi bloki v poljubni delitvi. 
Iz tega lahko **Stirlingova števila 2. vrste** definiramo tudi kot št. ekvivalenčnih relacij na množici $[n]$ s $k$ ekvivalenčnimi razredi, medtem ko so **bellova števila** enaka številu vseh ekvivalenčnih relacij na $[n]$.

Razdelitve so tudi povezane s surjekcijami. Če si predstavljamo surjekcijo iz množice z $n$ elementi v množico s $k$ elementi kjer velja da je $n>k$ potem lahko opazimo da neka surjektivna preslikava razdeli $[n]$ v bloke kjer vsaka slika tvori množico praslik edina razlika je da le to razdelitev lahko premešamo med $k$ elementov torej če nek blok pripada $k_{1}$ elementu ga lahko zamenjamo z nekim drugim. Tako lahko vidimo da je očitno **število surjekcij iz $[n]$ v $[k]$ natanko enako Stirlingovim številom II. vrste pomnoženim s $k!$ zaradi premešavanja pripadajočih elementov iz $[k]$**. 

$$k!S(n,k) = \text{Število surjekcij}$$


>[!|dokaz]- Dokaz:TODO

Sledi formula

$$S(n,k) = \frac{1}{k!}\sum_{j=0}^{k}(-1)^{k-j} \binom{\,k\,}{\,j\,} j^{n}$$
$$= \sum_{j= 0}^{k}\frac{(-1)^{k-j} j^{n}}{j! ( n-j)!}$$

Kot pri prejšnjih številih poznamo tudi tukaj povezavo s polinomi

$$\sum_{k}^{}S(n,k)x^{\underline{k}} = x^{n}$$

>[!|dokaz]- Dokaz:
> 
> Ključna ideja je da če dokažemo, da sta dva polinoma stopnje največ $n$ enaka v vsaj $n+1$ točkah, potem sta ta dva polinoma enaka. 
> 
> Ker se bosta v našem primeru polinoma ujemala za vsa naravna števila, se ujemata v neskončno točkah, kar je zadosten pogoj, da sta enaka.
> 
> Najprej enakost dokažimo za $x \in \mathbb{N}$, z uporabo kombinatoričnega argumenta.
> 
> Leva stran enačbe, $x^n$, predstavlja število vseh preslikav iz množice z $n$ elementi, ki jo označimo z $[n] = \{1, 2, \dots, n\}$, v množico z $x$ elementi, $[x] = \{1, 2, \dots, x\}$.
> 
> Desno stran enačbe dobimo s preštevanjem istih preslikav na drugačen način – z razdelitvijo po moči slike preslikave. Vsaka preslikava $f: [n] \to [x]$ je surjektivna na svojo sliko, $Im(f) \subseteq [x]$. Naj bo moč slike $|Im(f)| = k$. Število vseh preslikav lahko dobimo tako, da seštejemo število preslikav za vsako možno moč slike $k$.
> 
> Za fiksno velikost slike $k$, lahko najprej izberemo $k$-elementno sliko iz kodomene $[x]$ na $\binom{x}{k}$ načinov. Nato moramo prešteti vse surjektivne preslikave iz domene $[n]$ na to izbrano $k$-elementno množico. Število takih surjekcij je enako $k! S(n,k)$, kjer je $S(n,k)$ Stirlingovo število druge vrste (število razdelitev množice z $n$ elementi na $k$ nepraznih podmnožic).
> 
> S seštevanjem po vseh možnih velikostih slike $k$ (od $k=0$ do $k=n$) dobimo skupno število vseh preslikav:
> 
> $$ x^n = \sum_{k=0}^{n} \binom{x}{k} k! S(n,k) $$
> 
> Ta enakost, dokazana s kombinatoričnim argumentom, zagotovo velja za vsa naravna števila $x$.
> 
> Zdaj pa obe strani enačbe obravnavajmo kot polinoma v spremenljivki $x$. Leva stran, $x^n$, je očitno polinom stopnje $n$. Tudi desna stran je polinom, saj je binomski koeficient, pomnožen s $k!$, padajoča fakulteta:
> 
> $$ \binom{x}{k} k! = \frac{x(x-1)\cdots(x-k+1)}{k!} k! = x(x-1)\cdots(x-k+1) $$
> 
> To je polinom v spremenljivki $x$ stopnje $k$. Celotna vsota je torej vsota polinomov in je zato tudi sama polinom, katerega stopnja je največ $n$. Ker smo pokazali, da se vrednosti teh dveh polinomov ujemajo za vsa naravna števila $x$, se torej ujemajo na neskončno mnogo točkah. Iz tega sledi, da morata biti polinoma identično enaka. Zato zgornja enakost velja ne le za naravna števila, ampak za poljubna realna ali kompleksna števila $x$.


***

### Lahova števila

Antimarksistična števila

$L(n,k)$ je število razdelitev $[n]$ na $k$ urejenih blokov.

$S(n,k)$ šteje razdelitve na bloke, $c(n,k)$ razdelitve na ciklične bloke, $L(n,k)$ pa urejene bloke.

$L(n,n) = 1$
$L(n,1) = n!$
$L(n,n-1) = n(n-1)$

**Trditev:**

$$L(n, k) = \frac{n!}{k!} \binom{n-1}{k-1}$$

To lahko razložimo kot enakost med številom urejenih razdelitev na $k$ blokov: 

$$k! L(n, k)$$ 

in kompozicije $n,k$

$$\dots |\dots| \dots$$
$$ \binom{n-1}{k-1}$$
$$n-1 \text{ možnih mest za pregrade}$$
$$\text{izbira } k-1 \text{ mest za pregrade}$$

Nato pa lahko teh $n$ elementov v blokih poljubno uredimo, torej:

$$\binom{n-1}{k-1} n!$$
$$ $$
$$\Rightarrow k! L(n, k) = n! \binom{n-1}{k-1}$$
$$L(n, k) = \frac{n!}{k!} \binom{n-1}{k-1}$$


Drugače pa lahko trdimo da z $\binom{\,n-1\,}{\,k-1\,}$ izberemo pregrade za $k$ množic. Potem pomnožimo s permutacijami elementov $n$ kar nam da urejene množice, a s tem smo premešali tudi množice ki jih moramo z $\frac{1}{k!}$ odmešati.


Poznamo tudi rekurzivno zvezo

$$L(n, k) = L(n-1, k-1) + (n+k-1) L(n-1, k)$$


>[!|dokaz]- Dokaz:
> Razdelitev $[n]$ na $k$ blokov:
> 
> 1.  **$\{n\}$ je blok:**
>     $$L(n-1, k-1)$$
>     (Preostalih $n-1$ elementov razdelimo na $k-1$ blokov.)
> 
> 2.  **$\{n\}$ ni blok:**
>     $$L(n-1, k) \cdot (n-1+k)$$
>     (Razdelimo $n-1$ elementov na $k$ blokov, element $n$ pa vstavimo na eno izmed $n+k-1$ možnih mest.)
>     *   $n-1$ : za el (za elemente, tj. za vsakim obstoječim elementom)
>     *   $k$ : na zač. bloka (na začetek enega izmed $k$ blokov)



Obstaja tudi polinomska zveza

$$\sum_{k=0}^{n}L(n,k)x^{\underline{k}} = x^{\overline{n}}$$

Iz vseh polinomskih zvez, ki smo jih naredili do sedaj, lahko vidimo povezavo.
Naj bo $\{ 1,x,x^{2},...\}$ baza za vektorski prostor $\mathbb{R}[x]$.

Za baze lahko vzamemo tudi $\{ 1,x^{\underline{1}},x^{\underline{2}},...\}$ kot tudi $\{ 1,x^{\overline{1}},x^{\overline{2}},...\}$ in kot vemo, med bazami obstajajo prehodne matrike. Izkaže se, da so za

$$\mathcal{B}_1 = \{1, x, x^2, x^3, \dots, x^n, \dots\}$$
$$\mathcal{B}_{2} = \{1, x^{\underline{1}}, x^{\underline{2}}, \dots, x^{\underline{n}}, \dots\}$$
$$\mathcal{B}_{3} = \{1, x^{\overline{1}}, x^{\overline{2}}, \dots, x^{\overline{n}}, \dots\}$$

te matrike sestavljene iz naslednjih kombinatoričnih števil.

Spodnje enačbe predstavljajo prehode **iz** baz 

$\mathcal{B}_{1}\rightarrow \mathcal{B_{2}}$, $\mathcal{B}_{2}\rightarrow \mathcal{B_{1}}$

$$\sum_{k=0}^{n} S(n, k) x^{\underline{k}} = x^n$$

$$\sum_{k=0}^{n} (-1)^{n-k} c(n, k) x^k = x^{\underline{n}}$$

$\mathcal{B}_{1}\rightarrow \mathcal{B_{3}}$, $\mathcal{B}_{3}\rightarrow \mathcal{B_{1}}$

$$\sum_{k=0}^{n} c(n, k) x^k = x^{\overline{n}}$$



$$\sum_{k=0}^{n} (-1)^{n-k} S(n, k) x^{\overline{k}} = x^n$$

$\mathcal{B}_{2}\rightarrow \mathcal{B_{3}}$, $\mathcal{B}_{3}\rightarrow \mathcal{B_{2}}$

$$\sum_{k=0}^{n} L(n, k) x^{\underline{k}} = x^{\overline{n}}$$
$$\sum_{k=0}^{n} (-1)^{n-k} L(n, k) x^{\overline{k}} = x^{\underline{n}}$$

Natanko prehodne matrike med temi bazami. (Prehodne matrike so $c,S,L$ kjer $i$-ti stolpec vsebuje $c/S/L(i,k)$)

$$x^{3}:$$
$$ P_{\mathcal{B}_2 \leftarrow \mathcal{B}_1} = \begin{pmatrix}
S(0,0) & S(1,0) & S(2,0) & S(3,0) \\
S(0,1) & S(1,1) & S(2,1) & S(3,1) \\
S(0,2) & S(1,2) & S(2,2) & S(3,2) \\
S(0,3) & S(1,3) & S(2,3) & S(3,3)
\end{pmatrix} = \begin{pmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 1 & 1 \\
0 & 0 & 1 & 3 \\
0 & 0 & 0 & 1
\end{pmatrix} $$

$$ \begin{pmatrix} 1 & 0 & 0 & 0 \\ 0 & 1 & 1 & 1 \\ 0 & 0 & 1 & 3 \\ 0 & 0 & 0 & 1 \end{pmatrix} \begin{pmatrix} 0 \\ 0 \\ 0 \\ 1 \end{pmatrix} = \begin{pmatrix} 0 \\ 1 \\ 3 \\ 1 \end{pmatrix} $$

$$x^{3}=0 \cdot x^{\underline{0}} + 1 \cdot x^{\underline{1}} + 3 \cdot x^{\underline{2}} + 1 \cdot x^{\underline{3}}$$

### Tabela inverzij in mahovska števila

Naj bo $\pi \in S_{n}, \pi=(\pi(1),...,\pi(i),...\pi(j),...,\pi(n))$, kjer to ni cikel temveč enovrstična notacija.

Število inverzij $\text{inv}(\pi)$ je število parov členov $(i,j)$ kjer velja da je $i<j$ in $\pi(i)>\pi(j)$. Je število parov vseh števil $a,b$ kjer je $a$ večje od $b$ in $b$ stoji pred njim v zapisu permutacije. 

Predznak permutacije lahko izrazimo s številom inverzij:

$$\text{sgn}(\pi) = (-1)^{\text{inv}(\pi)}$$

$$\det A = \sum_{\pi \in S_{n}}^{}\text{sgn}(\pi)a_{1,\pi(1)}\cdot a_{2,\pi(2)}\,\cdot \;... $$

Grupo $S_n$ generirajo enostavne transpozicije $S_{n} = \langle ...,(i,i+1),...\rangle; i \in  \{ 1,...,n-1\}$

Število inverzij $\pi$ je enako najmanjšemu številu enostavnih transpozicij katerih produkt je $\pi$.

Za $\text{inv}(\pi)$ velja

$$0 \leq \text{inv}(\pi) \leq \binom{\,n\,}{\,2\,}$$

Ker lahko za vsako inverzijo izberemo 2 elementa oz. imamo permutacijo ki je $(n,n-1,...,1)$.

**Tabela inverzij** je zapis

$$I(\pi) = (i_{1}...i_{n})$$
$$0 \leq i_{k}\leq n-k$$

kjer je $i_{k}$ število inverzij za $k$-ti element. Oz, $k$ ima $i_{k}$ elementov večjih od njega levo od sebe.


$$I(4\, 2\,5\,3\,1) = (4,1,2,0,0)$$

Velja

$$\sum_{a_{k} \in I(\pi)}^{}a_{k} = \text{inv}(\pi)$$

Izrek:

$$\pi \mapsto I(\pi) \text{ je bijekcija iz } S_{n} \text{ v } \{ (a_{1},...,a_{n}): 0 \leq a_{k}\leq n-k \}$$

Za preslikavo v desno je trivialno $\pi \rightarrow I(\pi)$.

Za preslikavo iz $I(\pi) \rightarrow \pi$ pa lahko vzamemo najbolj desno število oz. največje število $(n)$ in ga vstavimo prvega. Vzamemo naslednje število $(n-1)$ in ga postavimo na primerno mesto, to deluje ker $a_{k}\leq n-k$ kar pomeni da vedno vemo kam ga lahko damo.

To je v resnici še en dokaz da je $|S_{n}| = n!$.

>[!|dokaz]- Dokaz:
> 
> Dokaz za $|S_n| = n!$ temelji na tem, da izračunamo število vseh možnih inverzijskih tabel $I(\pi)$, ki jih lahko tvorimo pri danih omejitvah.
> 
> Ker je $\pi \mapsto I(\pi)$ bijekcija (eno-eno in na), mora biti število elementov v domeni enako številu elementov v kodomeni:
> 
> $$|S_n| = |\{ (a_{1},...,a_{n}): 0 \leq a_{k}\leq n-k \}|$$
> 
> Izračunajmo število elementov v kodomeni (množici inverzijskih tabel):
> 
> Elementi inverzijske tabele so $a_1, a_2, \dots, a_n$, in za vsakega veljajo neodvisne omejitve:
> 
> 1. **Za $a_1$:** $0 \leq a_1 \leq n-1$.
>    Število možnih vrednosti za $a_1$ je $(n-1) - 0 + 1 = n$.
> 2. **Za $a_2$:** $0 \leq a_2 \leq n-2$.
>    Število možnih vrednosti za $a_2$ je $(n-2) - 0 + 1 = n-1$.
> 3. **Za $a_3$:** $0 \leq a_3 \leq n-3$.
>    Število možnih vrednosti za $a_3$ je $n-2$.
>    ...
> 4. **Za $a_{n-1}$:** $0 \leq a_{n-1} \leq n-(n-1) = 1$.
>    Število možnih vrednosti za $a_{n-1}$ je $1 - 0 + 1 = 2$.
> 5. **Za $a_n$:** $0 \leq a_n \leq n-n = 0$.
>    Število možnih vrednosti za $a_n$ je $0 - 0 + 1 = 1$.
> 
> Ker je izbira vsakega $a_k$ neodvisna od ostalih, pomnožimo število možnosti za vsak element, da dobimo skupno število vseh možnih inverzijskih tabel:
> 
> $$\text{Število tabel} = n \times (n-1) \times (n-2) \times \cdots \times 2 \times 1$$
> 
> To je definicija fakultete.
> 
> $$\text{Število tabel} = n!$$


### Mahonska števila

$T(n,k)$ je število permutacij v $S_n$ s $k$ inverzijami

$T(n,0) = T(n,\binom{\,n\,}{\,2\,}) = 1$

$$0\leq k\leq \binom{\,n\,}{\,2\,}$$
$$\sum_{k}^{}T(n,k)q^{k} = q(1+q)(1+q+q^{2})...(1+q+q^{2}+...+q^{n-1})$$

Maksimalna stopnja tega polinoma je $\binom{\,n\,}{\,2\,}$.

Definiramo $q$-naravno število:

$$1 + q +q^{2}+q^{3}+...+q^{n-1} = (n)_{q}$$
$$q = 1: (n)_{1}=n$$

$$(n)_{q} = (1)_{q}(2)_{q}...(n)_{q}$$

Sedaj lahko dokažemo

$$\sum_{k}^{}T(n,k)q^{k} = q(1+q)(1+q+q^{2})...(1+q+q^{2}+...+q^{n-1})$$
$$0\leq k\leq \binom{\,n\,}{\,2\,}$$


***


$$I_n(q) = \sum_{k=0}^{\binom{n}{2}} T(n,k)q^k = (1)_q(2)_q \dots (n)_q $$ $$= \prod_{j=1}^{n} (j)_q = \prod_{j=1}^{n} (1+q+q^2+...+q^{j-1})$$

**Trditev:** Za vsak $n \ge 1$ velja 

$$I_n(q) = \prod_{j=1}^{n} (1+q+q^2+...+q^{j-1})$$

>[!|dokaz]- Dokaz:
> 
> Uporabili bomo matematično indukcijo po $n$.
> 
> **Baza indukcije:** Za $n=1$ imamo v $S_1$ le eno permutacijo, identiteto $(1)$, ki ima $0$ inverzij. Torej je $T(1,0)=1$ in $T(1,k)=0$ za $k>0$.
> Leva stran enačbe je $I_1(q) = T(1,0)q^0 = 1$.
> Desna stran enačbe je $\prod_{j=1}^{1} (j)_q = (1)_q = 1$.
> Ker sta obe strani enaki, baza indukcije velja.
> 
> **Indukcijski korak:** Predpostavimo, da formula velja za $n-1$. Torej velja:
> $$I_{n-1}(q) = \sum_{k=0}^{\binom{n-1}{2}} T(n-1, k) q^k = \prod_{j=1}^{n-1} (j)_q$$
> Pokažimo, da formula velja tudi za $n$.
> 
> Vsako permutacijo $\pi \in S_n$ lahko enolično tvorimo iz permutacije $\pi' \in S_{n-1}$ tako, da v $\pi'$ (ki je permutacija števil $\{1, 2, \dots, n-1\}$) vstavimo element $n$ na eno od $n$ možnih mest.
> 
> Naj bo $\pi' \in S_{n-1}$ poljubna permutacija z $\text{inv}(\pi')$ inverzijami. Ko vanjo vstavimo element $n$, ta tvori novo inverzijo z vsakim elementom, ki se v zapisu nahaja desno od njega. Ker je $n$ največji element, bo prispeval k številu inverzij natanko toliko, kolikor je elementov na njegovi desni.
> 
> Če $n$ vstavimo na:
> -   zadnje mesto, ustvarimo 0 novih inverzij. Skupno število inverzij: $\text{inv}(\pi') + 0$.
> -   predzadnje mesto, ustvarimo 1 novo inverzijo. Skupno število inverzij: $\text{inv}(\pi') + 1$.
> -   ...
> -   prvo mesto, ustvarimo $n-1$ novih inverzij. Skupno število inverzij: $\text{inv}(\pi') + n-1$.
> 
> Vsaka permutacija $\pi' \in S_{n-1}$ torej generira $n$ unikatnih permutacij v $S_n$, katerih število inverzij je $\text{inv}(\pi'), \text{inv}(\pi')+1, \dots, \text{inv}(\pi')+(n-1)$.
> 
> Zapišimo to z rodovnimi funkcijami. Rodovna funkcija $I_n(q)$ je vsota vseh $q^{\text{inv}(\pi)}$ za $\pi \in S_n$. Združimo člene glede na to, iz katere $\pi' \in S_{n-1}$ izhajajo:
> $$I_n(q) = \sum_{\pi \in S_n} q^{\text{inv}(\pi)} = \sum_{\pi' \in S_{n-1}} \left( q^{\text{inv}(\pi')} + q^{\text{inv}(\pi')+1} + \dots + q^{\text{inv}(\pi')+(n-1)} \right)$$
> Izpostavimo skupni faktor $q^{\text{inv}(\pi')}$:
> $$I_n(q) = \sum_{\pi' \in S_{n-1}} q^{\text{inv}(\pi')} \left( 1 + q + q^2 + \dots + q^{n-1} \right)$$
> Vsota v oklepaju je $(n)_q$. Ker ta faktor ni odvisen od $\pi'$, ga lahko izpostavimo pred sumacijski znak:
> $$I_n(q) = \left( \sum_{\pi' \in S_{n-1}} q^{inv(\pi')} \right) \cdot (1 + q + \dots + q^{n-1})$$
> Prvi faktor je po definiciji rodovna funkcija $I_{n-1}(q)$. Tako dobimo rekurzivno zvezo:
> $$I_n(q) = I_{n-1}(q) \cdot (n)_q$$
> Po indukcijski predpostavki je $I_{n-1}(q) = \prod_{j=1}^{n-1} (j)_q$. Če to vstavimo v zgornjo enačbo, dobimo:
> $$I_n(q) = \left( \prod_{j=1}^{n-1} (j)_q \right) \cdot (n)_q = \prod_{j=1}^{n} (j)_q$$
> S tem je indukcijski korak dokazan. Trditev velja za vsak $n \ge 1$.





### Razčlenitve

Naj bo 

$$\lambda = (\lambda _{1},...,\lambda _{l})$$
$$\lambda _{1} \geq \lambda _{2} \geq ... \geq \lambda _{l} \geq 0$$

je razčlenitev naravnega števila $n$.

Rečemo da je $l$ dolžina $\lambda$, $\lambda_{i}$ je člen $\lambda$ in $n$ je velikost $\lambda$.

Označimo

$p(n)$ je število razčlenitev $n$.
$p_{k}(n)$ je število razčlenitev z dolžino $k$
$\overline{p}_{k}(n)$ je število razčlenitev $n$ dolžine manjše ali enake $k$.

$p(0) = 1$; prazna razčlenitev
$p(1) = 1$
$p(2) = 2$
$p(3) = 3$
$p(4) = 5$
$p(5) = 7$

Razčlenitev $\lambda$ lahko grafično predstavimo z dvema diagramoma

Ferrersov diagram
$\cdot \cdot \cdot \cdot \cdot$
$\cdot \cdot \cdot$
$\cdot \cdot \cdot$
$\cdot \cdot\,$

Youngsov diagram $\lambda = (5,3,3,2)$
$\square\;\;\square\;\;\square\;\;\square\;\;\square \;\;\lambda_1$
$\square\;\;\square\;\;\square\;\;\lambda_2$
$\square\;\;\square\;\;\square\;\;\lambda_3$
$\square\;\;\square\;\;\lambda_4$

Predstavljajo število členov v razčlenitvi.

Transpozicija razčlenitve je transponiranje diagrama oz.

$$\lambda_{i}' = | \{ j: \lambda_{j} \geq i\}|$$

$i = 1$ 
${\color{green}\square}\;\;\square\;\;\square\;\;\square\;\;\square \;\;\lambda_1$
${\color{green}\square}\;\;\square\;\;\square\;\;\lambda_2$
${\color{green}\square}\;\;\square\;\;\square\;\;\lambda_3$
${\color{green}\square}\;\;\square\;\;\lambda_4$

$\lambda_{1,2,3,4} \geq 1 \Rightarrow \lambda_{1}' = 4$

$i = 2$ 
$\square\;\;{\color{green}\square}\;\;\square\;\;\square\;\;\square \;\;\lambda_1$
$\square\;\;{\color{green}\square}\;\;\square\;\;\lambda_2$
$\square\;\;{\color{green}\square}\;\;\square\;\;\lambda_3$
$\square\;\;{\color{green}\square}\;\;\lambda_4$

$\lambda_{1,2,3,4} \geq 1 \Rightarrow \lambda_{2}' = 4$

$i = 3$
$\square\;\;\square\;\;{\color{green}\square}\;\;\square\;\;\square \;\;\lambda_1$
$\square\;\;\square\;\;{\color{green}\square}\;\;\lambda_2$
$\square\;\;\square\;\;{\color{green}\square}\;\;\lambda_3$
$\square\;\;\square\;\;\lambda_4$

$\lambda_{1,2,3} \geq 3 \Rightarrow \lambda_{3}' = 3$

$i = 4$
$\square\;\;\square\;\;\square\;\;{\color{green}\square}\;\;\square \;\;\lambda_1$
$\square\;\;\square\;\;\square\;\;\lambda_2$
$\square\;\;\square\;\;\square\;\;\lambda_3$
$\square\;\;\square\;\;\lambda_4$

$\lambda_{1} \geq 4 \Rightarrow \lambda_{4}' = 1$

$i = 5$
$\square\;\;\square\;\;\square\;\;\square\;\;{\color{green}\square} \;\;\lambda_1$
$\square\;\;\square\;\;\square\;\;\lambda_2$
$\square\;\;\square\;\;\square\;\;\lambda_3$
$\square\;\;\square\;\;\lambda_4$

$\lambda_{1} \geq 5 \Rightarrow \lambda_{5}' = 1$


$\lambda_{i}'$ je število členov $\lambda_{j}$ večje ali enake velikosti $i$ 

Velja tudi da je konjugacija konjugirane razčlenitve enaka originalni razčlenitvi $\lambda'' = \lambda$.

Poznamo rekurzivno zvezo za $p(n), p_{k}(n), \overline{p}_{k}(n)$ :

 $(1) \;\;p_k(n) =-= \overline{p}_k(n-k)$

$(2) \;\;p_k(n) = p_{k-1}(n-1) + p_k(n-k)$

$(3) \;\;\overline{p}_k(n) = \overline{p}_{k-1}(n) + \overline{p}_k(n-k)$

>[!|dokaz]- Dokaz:
> 
> $(1)$
> 
> Vzemimo poljubno razčlenitev števila $n$ na natanko $k$ delov. Ker ima vsak del vrednost vsaj 1, lahko od vsakega od $k$ delov odštejemo 1. S tem dobimo razčlenitev števila $n-k$ na $k$ delov, od katerih so nekateri lahko enaki 0. Če te ničelne dele opustimo, dobimo razčlenitev števila $n-k$ na največ $k$ delov. Ta postopek je obratno enoličen in vzpostavi bijekcijo med obema množicama razčlenitev. To ustreza tudi odstranitvi prvega stolpca v Ferrerjevem diagramu.
> 
> $(2)$
> 
> Množico vseh razčlenitev števila $n$ na $k$ delov razdelimo v dve disjunktni skupini:
> 1.  **Razčlenitve, kjer je najmanjši del enak 1.** Če ta del odstranimo, dobimo razčlenitev števila $n-1$ na $k-1$ delov. Takšnih razčlenitev je $p_{k-1}(n-1)$.
> 2.  **Razčlenitve, kjer so vsi deli večji od 1.** Če vsakemu od $k$ delov odštejemo 1, dobimo razčlenitev števila $n-k$ na natanko $k$ delov. Takšnih je $p_k(n-k)$.
> 
> Ker skupini pokrijeta vse možnosti in sta disjunktni, velja formula $p_k(n) = p_{k-1}(n-1) + p_k(n-k)$.
> 
> $(3)$
> 
> Število razčlenitev števila $n$ na največ $k$ delov, $\overline{p}_k(n)$, lahko razdelimo na dva primera: razčlenitve, ki imajo natanko $k$ delov, in razčlenitve, ki imajo manj kot $k$ delov (torej največ $k-1$). Iz tega sledi identiteta:
> $\overline{p}_k(n) = p_k(n) + \overline{p}_{k-1}(n)$
> 
> Z uporabo zveze iz prvega dokaza, $p_k(n) = \overline{p}_k(n-k)$, vstavimo desni del v zgornjo enačbo in dobimo iskano rekurzivno formulo:
> $\overline{p}_k(n) = \overline{p}_{k-1}(n) + \overline{p}_k(n-k)$


Poznamo tudi **rekurzivno zvezo za** $p(n)$ znan tudi kot **Eulerjev petkotniški izrek**.

$$p(n) = \sum_{k=0}^{}(-1)^{k-1}\left(p\left(n-\frac{k(3k-1)}{2}\right)+p\left(n-\frac{k(3k+1)}{2}\right)\right)$$

>[!|dokaz]- Dokaz: TODO


### Dvanajstera pot

Imamo $n$ kroglic ki jih hočemo razporediti v $k$ škatel. To lahko predstavimo s preslikavo

$$f: [n] \rightarrow [k] $$

Sedaj pa hočemo prešteti funkcije za katere lahko velja da so vse možne, injektivne, surjektivne, ločimo med kroglicami v $[n]$, ločimo med škatlami $[k]$.

Iz tega dobimo 12 možnih problemov : $3 \cdot 2 \cdot 2$.
In le te lahko damo v tabelo.
Seveda, tukaj je lepo oblikovana tabela v formatu Markdown z uporabo LaTeX-a za matematične izraze, ki povzema vsebino vaše slike. Ta pristop je znan kot "Dvanajsterna pot" (Twelvefold Way) v kombinatoriki, ki sistematično obravnava načine razporejanja $n$ elementov v $k$ predalov (ali preslikav iz množice z $n$ elementi v množico s $k$ elementi), odvisno od tega, ali so elementi in predali ločljivi ali neločljivi.

---

### Kombinatorični pregled razporeditev (Dvanajsterna pot)

Spodnja tabela prikazuje število načinov za razporeditev $n$ elementov v $k$ predalov, glede na lastnosti elementov in predalov.

| $[n]$ / $[k]$ | Vse preslikave                                 | Injektivne preslikave                                   | Surjektivne preslikave                                 |
| :------------------------------------- | :--------------------------------------------- | :------------------------------------------------------ | :----------------------------------------------------- |
| **Ločimo / Ločimo**                | $$k^n$$                                          | $$k^{\underline{n}} = \frac{k!}{(k-n)!}$$                  |  $$k! \, S(n,k) $$$$ \textbf{(1)}$$                      |
| **Ne ločimo / Ločimo**              | $$\binom{n+k-1}{n}$$                              | $$\binom{k}{n}$$                                          | $$\binom{n-1}{k-1} $$$$ \textbf{(2)}$$                  |
| **Ločimo / Ne ločimo**              | $$\sum_{i=1}^{k} S(n,i)$$                        | $$\begin{cases} 1 & \text{če } n \le k \\ 0 & \text{če } n > k \end{cases}$$ | $$S(n,k) $$$$ \textbf{(3)}$$                            |
| **Ne ločimo / Ne ločimo**            | $$\overline{p_k}(n) = \sum_{i=1}^{k} p_i(n)$$      | $$\begin{cases} 1 & \text{če } n \le k \\ 0 & \text{če } n > k \end{cases}$$ | $$p_k(n) $$$$ \textbf{(4)}$$                            |

---

### Pojasnila in opombe iz slike:

1.  **$k! \, S(n,k)$**: Število surjektivnih preslikav iz $n$-članske v $k$-člansko množico. Kombinatorični argument je "najprej razdeli, nato dodeli":
    *   $S(n,k)$ je število načinov za razdelitev $n$ ločljivih elementov v $k$ nepraznih, **neločljivih** skupin (Stirlingova števila 2. vrste).
    *   $k!$ je število načinov, na katere lahko teh $k$ skupin priredimo $k$ **ločljivim** predalom.


2.  **$\binom{n-1}{k-1}$**: Število načinov za razporeditev $n$ neločljivih elementov v $k$ ločljivih predalov, tako da noben predal ni prazen. To je enako številu **kompozicij** števila $n$ na $k$ delov.


3.  **$S(n,k)$**: **Stirlingova števila 2. vrste**. Po definiciji je to število načinov za razdelitev množice z $n$ ločljivimi elementi v $k$ nepraznih podmnožic (ki so neločljive).


4.  **$p_k(n)$**: **Število particij (razdelitev)** števila $n$ na natanko $k$ delov. To ustreza razporeditvi $n$ neločljivih elementov v $k$ nepraznih, neločljivih predalov.

    *   Simbol $\overline{p_k}(n)$ v zgornji vrstici predstavlja število particij števila $n$ na *največ* $k$ delov.

Pri vrstici kjer ločimo med $n$ in $k$ elementi štejemo funkcije, pri vrsticah ne ločimo med enim.

Pri kombinatoriki pa rečemo da so elementi neločljivi ko oznake oz. vrstni red ni pomemben, formalno dosežemo to če rečemo da sta **dve funkciji enaki če lahko eno pretvorimo v drugo s permutacijo elementov.**

Imamo množico vseh funkcij

$$F = \{f : N \to K\}$$



- Če so elementi **ločljivi** (oznaka **1**), je vsaka funkcija svoj unikaten razpored.
    
- Če so elementi **neločljivi** (oznaka **0**), uvedemo ekvivalenčno relacijo. Dve funkciji sta "isti" (ekvivalentni), če se razlikujeta le v preimenovanju elementov. Štejemo torej **število ekvivalenčnih razredov** (orbit).



1. **Primer 01: Neločljiva domena, Ločljiva kodomena**
*   **Kaj to pomeni:** Mečemo neločljive kroglice (npr. bele ping-pong žogice) v oštevilčene škatle.
*   **Zapis:** $f \sim_N g \iff \exists \pi \in S_n : f \circ \pi = g$
*   **Razlaga:**
    *   $\pi \in S_n$ je permutacija domene (vhodnih podatkov, npr. kroglic).
    *   Izraz $f \circ \pi = g$ pomeni: "Funkcija $g$ je enaka funkciji $f$, le da smo premešali vhodne elemente."
    *   Ker so kroglice neločljive, nam je vseeno, *katera* kroglica gre v katero škatlo. Pomembno je le, *koliko* jih konča v posamezni škatli.
    *   **Rezultat:** To ustreza **multimnožicam** oz. kombinacijam s ponavljanjem ($\binom{n+k-1}{n}$).

2. **Primer 10: Ločljiva domena, Neločljiva kodomena**
*   **Kaj to pomeni:** Mečemo oštevilčene kroglice v enake (neoznačene) vreče.
*   **Zapis:** $f \sim_K g \iff \exists \sigma \in S_k : \sigma \circ f = g$
*   **Razlaga:**
    *   $\sigma \in S_k$ je permutacija kodomene (izhodnih podatkov, npr. škatel).
    *   To pomeni, da če prelepimo nalepke na škatlah, dobimo "isto" razporeditev.
    *   Ni važno, ali so kroglice {A, B} v škatli 1 in {C} v škatli 2, ali obratno. Važno je le, katere kroglice so skupaj.
    *   **Rezultat:** To ustreza **razbitjem množice (Set partitions)** in Stirlingovim številom 2. vrste ($S(n,k)$).

3. **Primer 00: Neločljiva domena, Neločljiva kodomena**
*   **Kaj to pomeni:** Mečemo neločljive kroglice v neločljive škatle.
*   **Zapis:** $f \sim_{n,k} g \iff \exists \sigma, \pi \in S_k, S_n : \sigma \circ f \circ \pi = g$
*   **Razlaga:**
    *   Tu smemo mešati tako kroglice ($\pi$) kot škatle ($\sigma$).
    *   Ker so kroglice enake, štejejo le količine. Ker so škatle enake, vrstni red količin ni važen.
    *   Razporeditev 3 žogice v prvo, 2 v drugo je ista kot 2 v prvo, 3 v drugo.
    *   **Rezultat:** To ustreza **razbitjem števila (Integer partitions)** ($p_k(n)$).




