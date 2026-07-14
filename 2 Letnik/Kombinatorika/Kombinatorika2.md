
### Tabela inverzij in mahonska števila

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
$$\sum_{k}^{}T(n,k)q^{k} = 1(1+q)(1+q+q^{2})...(1+q+q^{2}+...+q^{n-1})$$

Maksimalna stopnja tega polinoma je $\binom{\,n\,}{\,2\,}$.

Definiramo $q$-naravno število:

$$1 + q +q^{2}+q^{3}+...+q^{n-1} = (n)_{q}$$
$$q = 1: (n)_{1}=n$$

$$(n)_{q}! = (1)_{q}(2)_{q}...(n)_{q}$$

Sedaj lahko dokažemo

$$\sum_{k}^{}T(n,k)q^{k} = 1(1+q)(1+q+q^{2})...(1+q+q^{2}+...+q^{n-1})$$
$$0\leq k\leq \binom{\,n\,}{\,2\,}$$


***


$$I_n(q) = \sum_{k=0}^{\binom{n}{2}} T(n,k)q^k = (1)_q(2)_q \dots (n)_q $$ $$= \prod_{j=1}^{n} (j)_q = \prod_{j=1}^{n} (1+q+q^2+...+q^{j-1})$$

**Trditev:** Za vsak $n \ge 1$ velja 

$$I_n(q) = \prod_{j=1}^{n} (1+q+q^2+...+q^{j-1})$$

*Zapis predstavlja rodovno funckijo. 
Ko je  $n = 1$ torej permutacija z enim elementom imamo $0$ inverzij. 
Za vsako permutacijo lahko sestavimo polinom kjer koeficient $1$ pred $q^{k}$ predstavlja da imamo $k$ inverzij. In če je $0$ pred $q^{k}$ nimamo $k$ inverzij.
Ker imamo za $n=1$ 0 inverzij dobimo pred $1q^{0}$ - torej dobimo polinom $1$* 

*Če dodamo še en element v permutacijo imamo $2$ mesti kamor lahko damo. Brez izgube za splošnost rečemo da jih dodajamo v naraščajočem vrstnem redu torej smo imeli prej 1 in dodali 2. Če ga vstavimo na desno ne dobimo inverzij, če ga dodamo na levo dobimo novo inverzijo. Če vemo da smo prej imeli $q^{0}$ in smo dodali eno inverzijo bo to $q^{1}$. Torej moramo sešteti število inverzij od prej in število inverzij od sedaj. Torej ju pomnožimo in dobimo $q^{1}$.*

*Posplošeno gledano bo veljalo da če ima permutacija z $n$ elementi $k$ inverzij potem bomo ob vstavljanju novega večjega elementa $n+1$ dodali inverzije glede na mesto kamor ga postavimo. Če ga postavimo čisto na desno ne dobimo nobene nove, eno v levo dobimo eno novo, ... če ga dodamo čisto na desno dobimo $n$ novih inverzij torej bo veljalo v tem primeru $q^{k}q^{n} = q^{k+n}$ sedaj pogledamo za vsako od možnosti kjer bo veljalo da glede na to kam vstavimo $n+1$ element dobimo eno izmed možnosti $q^{k}q^{0} + q^{k}q^{1}+...+q^{k}q^{n} = q^{k}(1+q+...+q^{n})$ Torej bo veljalo da za vsako dodajanje $n+1$ elementa dobimo $n+1$ opcij za novo število inverzov. Vsaka opcija seveda predstavlja svojo permutacijo - torej koeficient pred $q^{k}$ pove koliko permutacij dolžine $n+1$ ima $k$ inverzij.* 

*Torej pri $n=1$ imamo $q^{0}$ - ena permutacija ima 0 inverzij. Pri $n=2$ dodamo en element in pomnožimo rodovno funkcijo za $n=1 := I_{1}(q)$ z vsemi opcijami povečanja števila inverzij glede na katero mesto damo element $(1+q)$ in dobimo $1+q$ - torej imamo eno permutacijo velikosti $2$ ki ima 1 inverzijo in eno ki ima 0 inverzij. Če to ponovimo še za 3 pomnožimo z $(1+q+q^{2})$ in ker se vsi koeficienti lepo seštejejo ker distributivnost zagotavlja seštevanje vseh opcij dobimo $1+q+q+q+q^{2}+q^{2}+q^{3} = 1+ 2q + 2q^{2}+q^{3}$ in tako naprej.*

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
$$\sum_{}^{}\lambda_{i} = n$$

je razčlenitev naravnega števila $n$.

Rečemo da je $l$ število pozitivnih členov $\lambda$, $\lambda_{i}$ je člen $\lambda$ in $n$ je velikost $\lambda$.

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

 $(1) \;\;p_k(n) = \overline{p}_k(n-k)$

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

$$p(n) = \sum_{k=1}^{}(-1)^{k-1}\left(p\left(n-\frac{k(3k-1)}{2}\right)+p\left(n-\frac{k(3k+1)}{2}\right)\right)$$

Z NVI lahko zapišemo $p(n)$ kot vsoto vseh razčlenitev ki vsebujejo število $i$. Torej imamo $A_{i}$ je množica razčlenitev ki vsebujejo število $i$ kot en člen. Iz tega sledi da je moč $A_{i}$ enaka $p(n-i)$ oz- številu vseh razčlenitev brez tega števila, saj če v vsako od teh dodamo $i$ dobimo razčlenitev $n$ ki ima $i$.

Moč preseka bo $p(n-i-j- ...-k)$. Če pogledamo kako se obrača predznak vidimo da odštevamo vse koeficiente $p(n-m)$ kjer je $m$ vsota lihega števila členov in prištevajo tisti kjer je $m$ vsota sodega števila členov. Torej če imamo $p(n-5)$ prištejemo $p(n-2-3)$ odštejemo pa $p(n-5)$.

Torej bo koeficient pred $p(n-m)$ odvisen od tega koliko sodih in lihih razčlenitev $m$ imamo.

Naj bo $\alpha(m)$ število lihih razčl. $m$ in $\beta(m)$ sodih. Velja da bo koeficient enak $\alpha(m)-\beta(m)$.

Ugotovili bomo da se pri večini $m$-jev razlika pokrajša razen pri specifičnih $m$-jih.

Če za vsako razčlenitev $m$ uvedemo pravili kjer velja da imamo dve vrednosti: $b$ in $s$, kjer predstavljata velikost voka in najmanjšega elementa.

Naj velja da če je $s \leq b$ potem vzamemo najmanjši člen in ga damo na bok.

Če je $s > b$ potem vzamemo eno plast boka in ga damo kot najmanjši člen.

S tema praviloma bo veljalo da lahko iz sode razčleniteve $m$-ja pridemo v liho in obratno.

To ne bo veljalo le če je $s = b = k$, kjer je $k$ število členov bo veljalo da če vzamemo spodnji element ga ne moremo razporediti na bok ker nam en zmanjka. *Vsi členi so del boka in zadnji člen je hkrati najmanjši*
To so torej vsi $m$-ji kjer velja $m = k+(k+1)+...+(2k-1) = \frac{k(3k-1)}{2}$
Za tako razčlenitev velja da ima $k$ členov torej velja da je koeficient $(-1)^{k-1}$ saj jo prištejemo če je liha in odštejemo če je soda.

Bijekcija ne bo veljala tudi če je $s = b+1 = k+1$, kjer je $k$ število členov.
To bodo $m$-ji kjer velja $m = (k+1)+(k+2)+...+(2k) = \frac{k(3k+1)}{2}$
Torej bo koeficient $(-1)^{k-1}$

Števila $m = \frac{k(3k\pm 1)}{2}$ imenujemo petkotniška števila.

Če sedaj seštejemo čez vse $p(n-m)$ dobimo spoplošen izrek.

$$\sum_{1}^{\infty} (-1)^{k-1}(p(n-m_{1})+p(n-m_{2}))$$






### Dvanajstera pot

Imamo $n$ kroglic ki jih hočemo razporediti v $k$ škatel. To lahko predstavimo s preslikavo

$$f: [n] \rightarrow [k] $$

Sedaj pa hočemo prešteti funkcije za katere lahko velja da so vse možne, injektivne, surjektivne, ločimo med kroglicami v $[n]$, ločimo med škatlami $[k]$.

Iz tega dobimo 12 možnih problemov : $3 \cdot 2 \cdot 2$.
In le te lahko damo v tabelo.


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


Pri kombinatoriki pa rečemo da so elementi neločljivi ko oznake oz. vrstni red ni pomemben, formalno dosežemo to če rečemo da sta **dve funkciji enaki če lahko eno pretvorimo v drugo s permutacijo elementov.**

Imamo množico vseh funkcij

$$F = \{f : N \to K\}$$



- Če so elementi **ločljivi** (oznaka **1**), je vsaka funkcija svoj unikaten razpored.
    
- Če so elementi **neločljivi** (oznaka **0**), uvedemo ekvivalenčno relacijo. Dve funkciji sta "isti" (ekvivalentni), če se razlikujeta le v preimenovanju elementov. Štejemo torej **število ekvivalenčnih razredov** (orbit).



1. **Neločljiva domena, Ločljiva kodomena**
*   **Kaj to pomeni:** Mečemo neločljive kroglice (npr. bele ping-pong žogice) v oštevilčene škatle.
*   **Zapis:** $f \sim_N g \iff \exists \pi \in S_n : f \circ \pi = g$
*   **Razlaga:**
    *   $\pi \in S_n$ je permutacija domene (vhodnih podatkov, npr. kroglic).
    *   Izraz $f \circ \pi = g$ pomeni: "Funkcija $g$ je enaka funkciji $f$, le da smo premešali vhodne elemente."
    *   Ker so kroglice neločljive, nam je vseeno, *katera* kroglica gre v katero škatlo. Pomembno je le, *koliko* jih konča v posamezni škatli.
    *   **Rezultat:** To ustreza **multimnožicam** oz. kombinacijam s ponavljanjem ($\binom{n+k-1}{n}$).
* Štejemo število ekvivalenčnih razredov $\sim_{N}$

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



***

### Formalne potenčne vrste in rodovne funkcije.

*Polje je multiplikativna in aditivna grupa z aditivno in multiplikativno enoto 0 in 1 in aditivnim inverzom in multiplikativnim inverzom razen za 0, skupaj s komukativnostjo.*
*Karakteristika polja je najmanjše število $n$ da velja $n \cdot  1 = 0$,če ne obstaja je karakteristika 0.*

*Če je karakteristiko enaka 0 potem je preslikava $f:n \cdot  1$ injektivna in je vsako celo število enolično predstavljeno v polju $K$ in noben $n\neq 0$ ne postane enak 0 v polju.*

*Velja da bo polje imelo inverze in množenje celih števil in inverzov zagotavlja da ima polje podstrukturo ki je izomorfna polju racionalnih števil.*

*Karakteristika 0 je potreben pogoj pri definiciji eksponentnih rodovnih funkcij $\sum_{0}^{\infty}\frac{a_{n}}{n!}x^{n}$ saj se v polju s karakteristiko > 0 lahko zgodi da je produkt $n!$ enak $0$ ker bil eden od faktorejv $p \cdot  1 = 0$*

*V polju s karakteristiko nič imamo vedno zagotovljeno da je $n! \neq 0$ za poljuben $n \in \mathbb{N}$*

*Izomorfizem s podpoljem $\mathbb{Q}$ pa nam lepo definira deljenje.*

Naj bo polje $K$ s karaktersitiko 0. Tako polje vsebuje podpolje izomorfno $\mathbb{Q}$. Zaporedje v $K$ definiramo kot funkcijo $f :\mathbb{N} \rightarrow K$.

Lahko ga zapišemo s predpisom npr. $a_n = 2^n$ ali $b_n = n!$, rekurzivno npr. Fibonaccijevo zaporedje $F_0=0, F_1=1, F_n = F_{n-1} + F_{n-2}$ za $n \geq 2$.

Lahko ga podamo tudi **asimptotsko**

$$a_n \sim b_n$$

kar pomeni $\lim_{n \to \infty} \frac{a_n}{b_n} = 1$. 

Primer je Stirlingova formula: $n! \sim \sqrt{2\pi n} \left(\frac{n}{e}\right)^n$.

Lahko ga podamo tudi z **rodovno funkcijo** 

**Običajna rodovna funkcija:** $\sum_{n=0}^\infty a_n x^n$

**Eksponentna rodovna funkcija:** $\sum_{n=0}^\infty \frac{a_n}{n!} x^n$

Pri formalnih potenčnih vrstah nas konvergenca ne zanima; $x$ obravnavamo le kot oznako (spremenljivko), ki določa mesto koeficienta.

### Formalne potenčne vrste $K[[x]]$
Množico formalnih potenčnih vrst označimo s $K[[x]] = \{ \sum_{n=0}^\infty a_n x^n \mid a_n \in K \}$. To je razširitev prostora polinomov $K[x]$, kjer so zaporedja koeficientov končna.

V $K[[x]]$ definiramo naslednje operacije:
*   **Vsota:** $\sum a_n x^n + \sum b_n x^n = \sum (a_n + b_n) x^n$
*   **Množenje s skalarjem:** $\lambda \sum a_n x^n = \sum (\lambda a_n) x^n$
*   **Konvolucijsko množenje:** $(\sum a_n x^n) \cdot (\sum b_n x^n) = \sum c_n x^n$, kjer je $c_n = \sum_{k=0}^n a_k b_{n-k}$.

$K[[x]]$ s temi operacijami postane **komutativna algebra** nad poljem $K$. *Vektorji so potenčne vrste, skalarji so elementi polja $K$* 

Zahtevamo da je 

**Seštevanje elementov v $K[[x]]$ abelova grupa** *(zaprtost,asoc,enota,inverz,kom)*.

- **Množenje vektorjev s skalarji iz $K$** kjer mora veljati 
**distributivnost nad seštevanjem skalarjev ali vektorjev**,

- **homogenost skalarjev** $a \cdot  (b \cdot  A(x)) = (a \cdot b)A(x)$

- **množenje vektorja z enoto nam da isti vektor**.

Za algebro pa dodamo še multiplikativnost med vektorji

Distributivnost leva *in desna*
$A(x) \cdot (B(x)+C(x))=A(x)B(x) + A(x)C(x)$

Homogenost preko vektorjev
$a \cdot (A(x)B(x)) = (a \cdot  A(x))\cdot B(x)$

**Asociativna algebra** je če imamo še asocitavnost množenja.

**Enotska algebra je** če imamo še enoto za množenje.

**Komutativna algebra** je če imamo še komutativnost

**Celostna algebra je** če nimamo deliteljev niča.

Mi imamo za $K[[x]]$ izpolnjeno vsako od teh.
***

> Asociativnost
> 1.  **Leva stran $[(AB)C]_n$:**
>     $$ \sum_{m+k=n} (AB)_m \cdot c_k = \sum_{m+k=n} \left( \sum_{i+j=m} a_i b_j \right) c_k = \mathbf{\sum_{i+j+k=n} (a_i b_j) c_k} $$
> 
> 2.  **Desna stran $[A(BC)]_n$:**
>     $$ \sum_{i+m=n} a_i \cdot (BC)_m = \sum_{i+m=n} a_i \left( \sum_{j+k=m} b_j c_k \right) = \mathbf{\sum_{i+j+k=n} a_i (b_j c_k)} $$

> Enota
> $$\sum_{n} a_n x^n \sum_{n} \delta_{n0} x^n = \sum_{n} \left( \sum_{k=0}^{n} a_k \delta_{n-k 0} \right) x^n = \sum_{n} a_n x^n$$

Velja zapis

$$[x^{n}]F(x) = a_{n}$$

naj bo dogovrjeno tudi

$$F(0) = [x^{0}]F(x)$$

Velja

$$(F \cdot G) (0) = F(0) \cdot  G(0)$$


> **Trditev:** $K[[x]]$ nima deliteljev niča. Če je $A(x)B(x) = 0$, potem je $A(x) = 0$ ali $B(x) = 0$.
> *Velja da mora biti vsaj en koeficient neničeln. Vzmameo dve nenčielni vrsti izberemo prva dva neničelna koeficienta pri obeh. V novi vrsti bo zmnožek teh dveh prvi koeficient pred prvim členom. Ker so koeficienti iz polja $K$ ki nimajo deliteljev niča potem tudi ta produkt ne more biti nič torej vrsta ni neničelna.*


> **Trditev:** $F(x)$ ima inverz $\Leftrightarrow$ $a_0 \neq 0$. 
> 
> Inverz $G(x) = \sum b_n x^n$ izračunamo rekurzivno: $b_0 = \frac{1}{a_0}$ in $b_n = -\frac{1}{a_0} \sum_{k=1}^n a_k b_{n-k}$.
> >[!|dokaz]+ Dokaz:
> > $\Rightarrow$ Če predpostavimo da inverz $G$ obstaja potem velja $F \cdot G = 1$ in rečemo $x=0$ velja da $F(0) \neq 0$
> > 
> > $\Leftarrow$
> > Dokazujemo, $a_0 \neq 0$, $\Rightarrow$ lahko izračunamo koeficiente $b_n$ za inverzno vrsto $G(x) = \sum b_n x^n$.
> > Zapišemo enačbo $(\sum a_n x^n) (\sum b_n x^n) = 1$ in primerjamo koeficiente pri posameznih potencah $x$:
> > 
> > *   **Pri $x^0$:** $a_0 \cdot b_0 = 1$. Ker je $a_0 \neq 0$, lahko izračunamo $b_0 = \frac{1}{a_0}$.
> > *   **Pri $x^1$:** $a_0 b_1 + a_1 b_0 = 0$. Iz tega izrazimo $b_1 = -\frac{a_1 b_0}{a_0}$.
> > *   **Pri $x^2$:** $a_0 b_2 + a_1 b_1 + a_2 b_0 = 0$. Iz tega sledi $b_2 = -\frac{a_1 b_1 + a_2 b_0}{a_0}$.
> > 
> > Zapisana je splošna rekurzivna formula za poljuben $n$:
> > $$b_n = -\frac{1}{a_0} \sum_{k=1}^n a_k b_{n-k}$$


### Odvajanje in kompozicija

Odvajanje definiramo formalno: $(\sum a_n x^n)' = \sum n a_n x^{n-1}$. Veljajo običajna pravila, kot je pravilo za produkt: $(FG)' = F'G + FG'$.

Odvajanje potenčene vrste je ekvivalentno odvajanju vsakega člena posebej - $a_{n}x^{n} \Rightarrow na_{n}x^{n-1}$, zamaknemo indeks da lahko še vedno potence $x^{n}$ torej dobimo $(n+1)a_{n+1}x^{n}$

> Na primer iščemo potenčno vrsto da velja
> 
> $$F'(x) = 0$$
> 
> $$\Leftrightarrow (n+1)a_{n+1} = 0 \quad \forall n \ge 0$$
> 
> ker smo v polju s karakteristiko $0$ mora biti $(n+1)$ ali $a_{n+1} = 0$
> 
> $$n+1 = 0 \Leftrightarrow n = -1$$
> 
> $\Rightarrow$ torej mora biti $a_{n+1} = 0 \quad \forall n > -1$
> $\Rightarrow a_n = 0 \quad \forall n > 0$
> $\Rightarrow F(x) = a_0$

> Lahko iščemo potenčno vrsto da velja $F'(x) = \lambda F(x)$
> 
> $$
> \begin{aligned}
> \lambda F(x) &= F'(x) \\
> \implies a_{n+1}(n+1) &= \lambda a_n \quad \forall n \geq 0 \\
> \implies a_{n+1} &= \frac{\lambda a_n}{n+1} \\
> \implies a_n &= \frac{\lambda a_{n-1}}{n}, \quad a_{n-1} = \frac{\lambda a_{n-2}}{n-1} \\
> &\dots \\
> \implies a_n &= \frac{\lambda^n a_0}{n!}
> \end{aligned}
> $$
> 
> če vstavimo te koef. v originalno vrsto in je $a_0 = 1$ dobimo
> $$
> \sum_{n=0}^{\infty} \frac{\lambda^n}{n!} x^n
> $$
> kar definiramo kot $e^{\lambda x}$


> $$
> e^{\lambda x} \cdot e^{\mu x} = e^{(\lambda + \mu)x}
> $$
> 
> $$
> \sum_{n=0}^{\infty} \frac{\lambda^n}{n!} x^n \cdot \sum_{n=0}^{\infty} \frac{\mu^n}{n!} x^n = \sum_{n=0}^{\infty} \frac{(\lambda + \mu)^n}{n!} x^n
> $$
> 
> $$
> = \sum_{n=0}^{\infty} \left( \sum_{i+j=n} \frac{\lambda^i}{i!} \cdot \frac{\mu^j}{j!} \right) \cdot x^n
> $$
> 
> $$
> \sum_{i+j=n} \frac{\lambda^i \mu^j}{i! j!} = \frac{(\lambda + \mu)^n}{n!}
> $$
> 
> $$
> \sum_{i+j=n} \frac{n!}{i! j!} \lambda^i \mu^j = (\lambda + \mu)^n
> $$
> 
> $$
> (x_1 + \dots + x_n)^n = \sum_{i_1 + \dots + i_n = n} \binom{n}{i_1, \dots, i_n} x_1^{i_1} \dots x_n^{i_n}
> $$

Kompozicija $F(G(x))$ je definirana kot $\sum a_n (G(x))^n$. 

Da imamo pri koeficientih končne vsote, saj drugače ne bi imelo smisla in bi pri vsakem koeficientu imeli neskončnost npr. pri $[x_{0}]$ bi imeli $a_{0}+a_{1}b_{0} + a_{2}b_{0}^{2}+a_{3}b_{0}^{3}+...$ mora veljati:


1. $F$ je polinom. *Ima končno členov, torej nimamo neskončne verige $G(x)^{k}$ ki bi za nek $x^{i}$ čahko prispevala svoj koeficient.*
2. $G(0) = 0$ (torej $b_0 = 0$). *S tem pri vsaki potenci $G^{k}$ vidimo da ne moramo dobiti noebnih členov manjših od $x^{k}$. $G(x) = (b_{1}x+...)$ Torej če damo le to na $k$ bo najmanjša satopnja $x^{k}$ torej bodo prispevki take funkcije šči k členom večjim ali enakim $k$.*

> **Izrek:** 
> Enota za kompozitum je $x$.
> $F$ ima inverz za kompozicijo ($F \circ G = G \circ F = x$) $\Leftrightarrow$ je $F(0) = 0$ in $F'(0) \neq 0$
> 
> >[!|dokaz]+ Dokaz:
> > Če imamo $F(G(x)) = x$ mora veljati $G(F(0)) = 0$. Ker je $F$ neskončen mora veljati da je $G(0) = 0$ kar pomeni da mora biti $F(0)=0$ da vemo da bo $G(F(0)) = 0$. Torej je $F(0) = 0$.
> > Za drugi pogoj da $F'(0)\neq 0$ pa lahko odvedemo kompozitum in velja
> > $$(F(G(x)))' = (x)'$$
> > $$F'(G(x)) \cdot G'(x) = 1$$
> > $$F'(G(0)) \cdot G'(0) = 1$$
> > $$F'(0) \cdot G'(0) = 1$$
> > Da bi bila ta enačba rešljiva (da produkt dveh števil v polju da 1), **$F'(0)$ ne sme biti nič**. Če bi bil $F'(0) = 0$, bi dobili $0 = 1$, kar je protislovje.
> > 
> > V drugo smer lahko predpostavimo da drži $F(0) = 0$ in $F'(0) = a_{1} \neq 0$.
> > 
> > Zapišemo $F(x) = a_1x + a_2x^2 + a_3x^3 + \dots$
> > Želimo $F(G(x)) = x$:
> > $$a_1(b_1x + b_2x^2 + \dots) + a_2(b_1x + b_2x^2 + \dots)^2 + a_3(b_1x + \dots)^3 + \dots = x$$
> > 
> > Sedaj primerjamo koeficiente pri potencah $x$:
> > 
> > 1.  **Pri $x^1$:**
> >     $$a_1 b_1 = 1 \implies b_1 = \frac{1}{a_1}$$
> >     Ker je po predpostavki $a_1 \neq 0$, inverz $b_1$ obstaja.
> > 
> > 2.  **Pri $x^2$:**
> >     $$a_1 b_2 + a_2 b_1^2 = 0 \implies a_1 b_2 = -a_2 b_1^2 \implies b_2 = -\frac{a_2 b_1^2}{a_1}$$
> >     Tudi $b_2$ lahko enolično določimo.
> > 
> > 3.  **Pri $x^n$:**
> >     Z indukcijo vidimo, da bo enačba za koeficient pri $x^n$ vedno oblike:
> >     $$a_1 b_n + (\text{polinom v } b_1, b_2, \dots, b_{n-1}) = 0$$
> >     Ker je $a_1$ vedno na voljo za deljenje, lahko rešimo enačbo za vsak $b_n$ zaporedoma.
> > 

***
### Reševanje rekurzivnih enačb

Rodovne funkcije so močno orodje za reševanje linearnih rekurzij. Postopek vključuje:
1. Zapis rekurzije za splošni člen $a_n$.
2. Množenje celotne enačbe z $x^n$ in seštevanje po vseh $n$.
3. Izražanje vsot s pomočjo rodovne funkcije $F(x) = \sum a_n x^n$.
4. Razcep dobljene racionalne funkcije na delne ulomke.
5. Razvoj delnih ulomkov nazaj v potenčne vrste za pridobitev eksplicitne formule za $a_n$.

>[!|dokaz]+ Dokaz oz. izpeljava:
> 
> Izhodišče je homogena linearna rekurzivna enačba $d$-te stopnje:
> $$c_d a_n + c_{d-1} a_{n-1} + \dots + c_0 a_{n-d} = 0, \quad n \geq d \quad (*)$$
> Pri tem so $c_i$ konstantni koeficienti, veljati pa mora $c_d \neq 0$ (da je stopnja res $d$) in $c_0 \neq 0$ (da je rekurzija polna). "Homogena" pomeni, da je desna stran enačbe enaka nič.
> 
> Za reševanje uporabimo rodovno funkcijo zaporedja $a_n$:
> $$F(x) = \sum_{n=0}^{\infty} a_n x^n$$
> Zgornjo rekurzivno enačbo $(*)$ pomnožimo z $x^n$ in seštejemo po vseh $n \geq d$. Po preureditvi členov (kjer upoštevamo začetne pogoje $a_0, a_1, \dots, a_{d-1}$) dobimo algebraično enačbo za $F(x)$. 
> - Člen $c_d a_n$ ustreza $c_d (F(x) - a_0 - a_1 x - \dots - a_{d-1} x^{d-1})$
> - Člen $c_{d-1} a_{n-1}$ ustreza $c_{d-1} x (F(x) - a_0 - a_1 x - \dots - a_{d-2} x^{d-2})$
> - In tako naprej do zadnjega člena $c_0 a_{n-d}$, ki ustreza $c_0 x^d F(x)$.
> 
> Ko te izraze seštejemo in izpostavimo $F(x)$, dobimo:
> $$F(x) = \frac{P(x)}{c_d + c_{d-1} x + c_{d-2} x^2 + \dots + c_0 x^d}$$
> Tu je $P(x)$ polinom stopnje manj kot $d$, ki je določen z začetnimi vrednostmi zaporedja.
> 
> 
> Rodovno funkcijo zapišemo kot:
> 
> $$F(x) = \frac{P(x)}{c_d + c_{d-1}x + \dots + c_0x^d}$$
> 
> Naj bo $K(\lambda) = c_d\lambda^d + c_{d-1}\lambda^{d-1} + \dots + c_0$ **karakteristični polinom** rekurzije. Imenovalec rodovne funkcije je povezan s tem polinomom preko zveze $x^d K(1/x)$.
> 
> Če so $\lambda_i$ ničle karakterističnega polinoma s kratnostmi $\alpha_i$, lahko imenovalec razcepimo:
> 
> $$c_d + c_{d-1}x + \dots + c_0x^d = c_d \prod_{i=1}^k (1 - \lambda_i x)^{\alpha_i}$$
> 
> Rodovno funkcijo $F(x)$ nato razbijemo na **parcialne ulomke**:
> $$F(x) = \sum_{i=1}^k \sum_{j=1}^{\alpha_i} \frac{A_{ij}}{(1 - \lambda_i x)^j}$$
> 
> Vsak parcialni ulomek razvijemo v potenčno vrsto z uporabo posplošenega binomskega izreka:
> $$\frac{1}{(1 - z)^j} = \sum_{n=0}^{\infty} \binom{n+j-1}{j-1} z^n$$
> Če vstavimo $z = \lambda_i x$, dobimo:
> $$F(x) = \sum_{i=1}^k \sum_{j=1}^{\alpha_i} A_{ij} \sum_{n=0}^{\infty} \binom{n+j-1}{j-1} \lambda_i^n x^n$$
> Splošni člen zaporedja $a_n$ je koeficient pri $x^n$:
> $$a_n = \sum_{i=1}^k \left( \sum_{j=1}^{\alpha_i} A_{ij} \binom{n+j-1}{j-1} \right) \lambda_i^n$$
> Izraz v oklepaju, $\sum_{j=1}^{\alpha_i} A_{ij} \binom{n+j-1}{j-1}$, je vsota polinomov spremenljivke $n$. Ker je največja stopnja binomskega koeficienta $\binom{n+j-1}{j-1}$ enaka $j-1$, je celoten izraz v oklepaju **polinom stopnje največ $\alpha_i - 1$**. Ta polinom označimo s $p_i(n)$.
> 
> Vse zgoraj navedeno vodi do izreka o reševanju z nastavkom:
> **Rešitev rekurzivne enačbe $(*)$ je oblike:**
> $$a_n = \sum_{i=1}^k p_i(n) \lambda_i^n$$
> kjer velja:
> - $\lambda_i$ so ničle karakterističnega polinoma $c_d \lambda^d + c_{d-1} \lambda^{d-1} + \dots + c_0 = 0$.
> - $\alpha_i$ je kratnost ničle $\lambda_i$.
> - $p_i(n)$ je polinom v $n$, katerega stopnja je strogo manjša od kratnosti ničle ($\deg p_i < \alpha_i$).

**Fibbionacijevo zaporedje**

Rekurzija je:

$$a_{n+2} = a_{n+1} + a_n, \quad n \geq 0$$

z začetnima pogojema $a_0 = 0$ in $a_1 = 1$.

Enačbo pomnožimo z $x^n$ in seštejemo po vseh $n$ od 0 do neskončnosti:

$$\sum_{n=0}^{\infty} a_{n+2}x^n = \sum_{n=0}^{\infty} a_{n+1}x^n + \sum_{n=0}^{\infty} a_n x^n$$

Naj bo $F(x) = \sum_{n=0}^{\infty} a_n x^n$. Posamezne vsote izrazimo s $F(x)$:
*   $\sum_{n=0}^{\infty} a_n x^n = F(x)$
*   $\sum_{n=0}^{\infty} a_{n+1} x^n = \frac{F(x) - a_0}{x} = \frac{F(x)}{x}$
*   $\sum_{n=0}^{\infty} a_{n+2} x^n = \frac{F(x) - a_0 - a_1 x}{x^2} = \frac{F(x) - x}{x^2}$

Vstavimo v enačbo:
$$\frac{F(x) - x}{x^2} = \frac{F(x)}{x} + F(x)$$
Pomnožimo s $x^2$ in izoliramo $F(x)$:
$$F(x) - x = x F(x) + x^2 F(x)$$
$$F(x)(1 - x - x^2) = x \implies F(x) = \frac{x}{1 - x - x^2}$$


Imenovalec $1 - x - x^2$ razcepimo na $(1 - \phi x)(1 - \psi x)$, kjer sta:
$\phi = \frac{1 + \sqrt{5}}{2}$ (zlato rezilo) in $\psi = \frac{1 - \sqrt{5}}{2}$.

Razcep na delne ulomke ima obliko:
$$\frac{x}{1 - x - x^2} = \frac{A}{1 - \phi x} + \frac{B}{1 - \psi x}$$
Z reševanjem sistema dobimo $A = \frac{1}{\sqrt{5}}$ in $B = -\frac{1}{\sqrt{5}}$. Torej:
$$F(x) = \frac{1}{\sqrt{5}} \left( \frac{1}{1 - \phi x} - \frac{1}{1 - \psi x} \right)$$


Uporabimo formulo za geometrijsko vrsto $\frac{1}{1-ut} = \sum_{n=0}^{\infty} u^n t^n$:
$$F(x) = \frac{1}{\sqrt{5}} \left( \sum_{n=0}^{\infty} (\phi x)^n - \sum_{n=0}^{\infty} (\psi x)^n \right)$$
$$F(x) = \sum_{n=0}^{\infty} \left( \frac{\phi^n - \psi^n}{\sqrt{5}} \right) x^n$$

Eksplicitna formula za $n$-ti člen (Binetova formula) je:
$$a_n = \frac{1}{\sqrt{5}} \left( \left( \frac{1 + \sqrt{5}}{2} \right)^n - \left( \frac{1 - \sqrt{5}}{2} \right)^n \right)$$


> Velja da je $\frac{1}{(1-x)^{k}} = \sum_{0}^{\infty}\binom{\,n+k-1\,}{\,k-1\,}x^{n}$
> To lahko algebraično dokažemo s $k$-kratnim odvajanjem geometrijske vrste $\frac{1}{1-x}$.

### Reševanje linearnih homogenih rekurzij s konstantnimi koeficienti




Če imamo rekurzijo oblike $c_d a_n + c_{d-1} a_{n-1} + \dots + c_0 a_{n-d} = 0$, najprej zapišemo **karakteristični polinom**:
$$c_d \lambda^d + c_{d-1} \lambda^{d-1} + \dots + c_0 = 0$$

Rešitev za splošni člen $a_n$ je sestavljena iz ničel tega polinoma ($\lambda_i$):
1.  Če je $\lambda_i$ **enostavna ničla**, v rešitev prispeva člen oblike $A \cdot \lambda_i^n$.
2.  Če je $\lambda_i$ **večkratna ničla** (z večkratnostjo $k$), v rešitev prispeva člen oblike $P(n) \cdot \lambda_i^n$, kjer je $P(n)$ polinom stopnje $k-1$.
    *   Npr. za dvojno ničlo $\lambda$: $(A + Bn) \lambda^n$.
    *   Za trojno ničlo $\lambda$: $(A + Bn + Cn^2) \lambda^n$.

Enostavna rekurzija 1. reda
*   Enačba: $a_n - 2a_{n-1} = 0 \Rightarrow \lambda - 2 = 0$.
*   Ničla je $\lambda = 2$.
*   Nastavek: $a_n = A \cdot 2^n$.
*   Iz $a_0 = 1$ dobimo $A=1$, torej **$a_n = 2^n$**.

Dve različni realni ničli
*   Enačba: $a_n = 3a_{n-1} - 2a_{n-2} \Rightarrow \lambda^2 - 3\lambda + 2 = 0$.
*   Ničli sta $\lambda_1 = 1$ in $\lambda_2 = 2$.
*   Nastavek: $a_n = A \cdot 1^n + B \cdot 2^n = A + B \cdot 2^n$.
*   Z vstavljanjem začetnih pogojev ($a_0=1, a_1=4$) rešimo sistem enačb in dobimo **$a_n = -2 + 3 \cdot 2^n$**.

Fibonaccijeva števila
*   Enačba: $F_n = F_{n-1} + F_{n-2} \Rightarrow \lambda^2 - \lambda - 1 = 0$.
*   Ničli sta iracionalni: $\frac{1 \pm \sqrt{5}}{2}$.
*   Nastavek: $F_n = A \left(\frac{1+\sqrt{5}}{2}\right)^n + B \left(\frac{1-\sqrt{5}}{2}\right)^n$. To vodi do znane Binetove formule.

Dvojna ničla
*   Enačba: $a_n - 6a_{n-1} + 9a_{n-2} = 0 \Rightarrow \lambda^2 - 6\lambda + 9 = 0$.
*   Polinom je $(\lambda - 3)^2 = 0$, kar pomeni, da je **$\lambda = 3$ dvojna ničla**.
*   Nastavek mora biti: **$a_n = (A + Bn) 3^n$**.


### Rešitev nehomogene rekurzivne enačbe

Splošna rešitev nehomogene enačbe je sestavljena iz dveh delov:

$$\text{splošna rešitev} = \text{homogena rešitev} (a_n^H) + \text{partikularna rešitev} (a_n^P)$$

*   **Homogena rešitev ($a_n^H$):** Rešitev enačbe, če bi bila desna stran enaka 0 (kot smo videli na prejšnjih slikah).
*   **Partikularna rešitev ($a_n^P$):** Ena konkretna rešitev, ki "zadovolji" desno stran.


Če je desna stran enačbe oblike $q(n) \cdot \lambda^n$ (kjer je $q(n)$ polinom), potem iščemo partikularno rešitev v obliki:
$$a_n^{P} =  r(n) \cdot n^{\alpha}\cdot  \lambda^n$$

Pri tem veljata dve ključni pravili:
1.  **Stopnja polinoma:** Polinom $r(n)$ mora biti iste stopnje kot polinom $q(n)$ na desni strani.
2.  **Kratnost ($\alpha$):** Število $\alpha$ je enako **kratnosti števila $\lambda$ v karakterističnem polinomu**. Če $\lambda$ ni ničla karakterističnega polinoma, je $\alpha = 0$. Če je $\lambda$ npr. dvojna ničla, je $\alpha = 2$.

> **Primer $a_n - 4a_{n-1} + 5a_{n-2} - 2a_{n-3} = n - 2$**
> 
> **Korak 1: Homogeni del**
> *   Karakteristični polinom: $\lambda^3 - 4\lambda^2 + 5\lambda - 2 = 0$.
> *   Z razcepom dobimo: $(\lambda - 1)^2 (\lambda - 2) = 0$.
> *   Ničli sta: $\lambda = 1$ (dvojna ničla!) in $\lambda = 2$ (enostavna ničla).
> *   Homogena rešitev: $a_n^H = \underbrace{A + Bn}_{\text{zaradi dvojne 1}} + \underbrace{C \cdot 2^n}_{\text{zaradi 2}}$.
> 
> **Korak 2: Partikularni del (Nastavek)**
> *   Desna stran je $n - 2$, kar lahko gledamo kot $(n - 2) \cdot 1^n$.
> *   Tukaj je $\lambda = 1$. Opazimo, da je **$\lambda = 1$ že v homogeni rešitvi kot dvojna ničla**, zato je $\alpha = 2$.
> *   Ker je $q(n) = n - 2$ polinom 1. stopnje, mora biti tudi $r(n)$ polinom 1. stopnje (npr. $D + En$).
> *   Nastavek za partikularno rešitev je torej: $a_n^P = n^2 \cdot (D + En) \cdot 1^n = Dn^2 + En^3$.
> 
> **Korak 3: Iskanje koeficientov (Spodnja slika)**
> Spodnji del zapiskov prikazuje postopek določanja konstant $D$ in $E$:
> 1.  Vzamemo nastavek $a_n^P = Dn^2 + En^3$ in ga vstavimo v originalno rekurzivno enačbo namesto $a_n$.
> 2.  Zaradi zamikov ($a_{n-1}, a_{n-2}, \dots$) dobimo precej dolg izraz z binomi (npr. $(n-1)^3$).
> 3.  Ko vse to razpišemo in uredimo po potencah $n$, izenačimo koeficiente z desno stranjo ($n - 2$).
> 4.  Izračun (ki je v zapiskih le nakazan) nam da vrednosti za $D$ in $E$ (npr. $D = -1/6$, $E = -1/2$).



### Binomska vrsta in Catalanovo število

Vemo da velja

$$
(1+x)^n = \sum_{k=0}^n \binom{n}{k} x^k
$$

Vemo da s $k$ kratnim odvajanjem $(1-x)^{-1} = \sum_{0}^{\infty}x^{n}$ lahko dobimo

$$
\frac{1}{(1-x)^k} = \sum_{n=0}^{\infty} \binom{n+k-1}{k-1} x^n
$$

$$
\frac{1}{(1+x)^k} = (1+x)^{-k} = \sum_{n=0}^{\infty} \binom{n+k-1}{k-1} (-1)^{n} x^n
$$

Definiramo **posplošeni binomski koeficient**

$$\binom{\,\lambda\,}{\,n\,}= \frac{\lambda(\lambda-1)...(\lambda-n+1)}{n!}$$

$$\lambda \in \mathbb{N} \Rightarrow \binom{\,\lambda\,}{\,n\,}$$
$$\lambda \in \mathbb{Z} \Rightarrow \binom{\,-k\,}{\,n\,} = \frac{-k(-k-1)...(-k-n+1)}{n!} = (-1)^{n}\binom{\,n+k-1\,}{\,n\,} = (-1)^{n} \binom{\,n+k-1\,}{\,k-1\,}$$

kjer je ta definicija smiselna le v polju s karakteristiko 0.

Poznamo **binomsko vrsto**

$$(1+x)^{\alpha}= \sum_{0}^{\infty} \binom{\,\alpha\,}{\,k\,}x^{k}$$

Tako lahko izpeljemo $(1+x)^\frac{1}{2}$ kot

$$\sum_{0}^{\infty} \binom{\,\frac{1}{2}\,}{\,k\,}x^{k}$$



$$
\begin{aligned}
\binom{1/2}{n} &= \frac{\frac{1}{2} \left( -\frac{1}{2} \right) \left( -\frac{3}{2} \right) \dots \left( \frac{1}{2} - n + 1 \right)}{n!}  ;\;\text{ kjer je } \frac{1}{2} - n + 1 = \frac{3 - 2n}{2} \\\\
&= \frac{(-1)^{n-1} \cdot 1 \cdot 3 \cdot 5 \dots (2n-3)}{2^n n!} \\\\
&= \frac{(-1)^{n-1} (2n-3)!!}{2^n n!} \\\\
&= \frac{(-1)^{n-1} (2n-3)!!(2n-2)!!}{2^n n!(2n-2)!!} \\\\
&= \frac{(-1)^{n-1} (2n-2)!}{2^{n }n!\cdot  2^{n-1}(n-1)!} \\\\
&= \frac{(-1)^{n-1} (2n-2)!}{2^{2n-1} n! (n-1)!} \\\\
&= \frac{(-1)^{n-1}}{2^{2n-1} n} \binom{2n-2}{n-1}
\end{aligned}
$$

Razvoj v vrsto:
$$(1+x)^{1/2} = 1 + \sum_{n=1}^{\infty} \frac{(-1)^{n-1}}{2^{2n-1} n} \binom{2n-2}{n-1} x^n = 1 + \frac{1}{2}x - \frac{1}{8}x^2 + \frac{1}{16}x^3 - \dots$$

> Velja še
> 
> $$(1+x)^\lambda \cdot (1+x)^\mu = (1+x)^{\lambda+\mu}$$
> To velja za poljubna števila (parametre) $\lambda$ in $\mu$.
> 
> 
> Da bi dokazali to enakost vrst, moramo pokazati, da so koeficienti pri poljubni potenci $x^n$ na levi in desni strani enaki.
> **Leva stran:** 
> Koeficient pri $x^n$ v produktu dveh vrst dobimo s **Cauchyjevim produktom**:
>     $[x^n]L = \sum_{k=0}^n \binom{\lambda}{k} \binom{\mu}{n-k}$
> **Desna stran:** 
> Koeficient pri $x^n$ v razvoju $(1+x)^{\lambda+\mu}$ je po definiciji:
>     $[x^n]D = \binom{\lambda+\mu}{n}$
> 
> Izrek je torej dokazan, če dokažemo t.i. **Vandermondovo identiteto**:
> $$\sum_{k=0}^n \binom{\lambda}{k} \binom{\mu}{n-k} = \binom{\lambda+\mu}{n}$$
> 
> Dokažemo ekvivalentno trditev za **padajoče faktoriale** (označene z $\lambda^{\underline{n}} = \lambda(\lambda-1)\dots(\lambda-n+1)$). Identiteta, ki se dokazuje, je:
> $$(\lambda+\mu)^{\underline{n}} = \sum_{k=0}^n \binom{n}{k} \lambda^{\underline{k}} \mu^{\underline{n-k}}$$
> *(To je binomski izrek za padajoče faktoriale. Če celotno enačbo delimo z $n!$, dobimo Vandermondovo identiteto).*
> 
> **Potek indukcije:**
> *   **Baza ($n=0$):** $1 = 1$, kar drži.
> *   **Induktivni korak ($n-1 \to n$):**
>     1.  Izraz $(\lambda+\mu)^{\underline{n}}$ zapišemo kot $(\lambda+\mu)^{\underline{n-1}} \cdot (\lambda+\mu-n+1)$.
>     2.  Uporabimo induktivno predpostavko ($i.p.$) za prvi del.
>     3.  Zadnji člen $(\lambda+\mu-n+1)$ spretno razdelimo na dva dela: $(\lambda-k) + (\mu-(n-1-k))$.
>     4.  Ko to zmnožimo z vsoto, dobimo dve novi vsoti.
>        
> **Vsota A:** $\sum \binom{n-1}{k} \lambda^{\underline{k}}(\lambda-k) \mu^{\underline{n-1-k}} = \sum \binom{n-1}{k} \lambda^{\underline{k+1}} \mu^{\underline{n-1-k}}$
> **Vsota B:** $\sum \binom{n-1}{k} \lambda^{\underline{k}} \mu^{\underline{n-1-k}}(\mu-n+1+k) = \sum \binom{n-1}{k} \lambda^{\underline{k}} \mu^{\underline{n-k}}$
> 
> V **Vsoti A** zamenjamo indeks $k \to k-1$, da dobimo enake potence kot v B:
> $$(\lambda+\mu)^{\underline{n}} = \sum_{k} \underbrace{\left[ \binom{n-1}{k-1} + \binom{n-1}{k} \right]}_{\text{Pascalovo pravilo: } \binom{n}{k}} \lambda^{\underline{k}} \mu^{\underline{n-k}}$$
> $$(\lambda+\mu)^{\underline{n}} = \sum_{k=0}^n \binom{n}{k} \lambda^{\underline{k}} \mu^{\underline{n-k}} \quad \square$$
> Če enačbo delimo z $n!$, dobimo koeficiente za produkt binomskih vrst, s čimer je izrek dokazan.
> 


***

**Catalanova števila $C_n$** lahko predstavljajo 
- štetje števila pravilnih postavitev $n$ parov oklepajev simboli, 
- na koliko načinov lahko konveksen mnogoktonik z $n+2$ stranicami razdelimo na trikotnike tako da povežemo njegova oglišča
- Imamo kvadratno mrežo velikosti $n \times n$. Koliko je poti od spodnjega levega kota $(0,0)$ do zgornjega desnega kota $(n,n)$, če se premikamo le desno ali navzgor in nikoli ne prečkamo glavne diagonale (lahko se je le dotaknemo)?

Zadoščajo kvadratni rekurziji 

Če nas zanima postavitev $n+1$ parov oklepajev lahko postavimo prvi oklepaj, notri je lahko poljubna postavitev $k$ parov oklepajev, postaivmo zaklepaj, nato pa imamo $n-k$ preostalih parov oklepajev. Ker moramo preveriti vse možnosti za vse $k$-je bomo imeli natanko sponjo rekurzivno formulo.

Če imamo $n+1$ vozlišč iz katerih hočemo zgraditi binarno drevo potem imamo enega v korenu, nato pa lahko pogledamo levo in se odločimo da bo imelo levo poddrevo $k$ vozlišč desno pa $n-k$, ker moramo preveriti vse možne kombinacije imamo spet rekurzivno formulo.


$$C_{n+1} = \sum_{k=0}^n C_k C_{n-k}$$ 

z začetnim pogojem $C_0 = 1$.

Temu praivmo tudi kvadratna rekurzija.


Če definiramo rodovno funkcijo za Catalanovo zaporedje dobimo 

$$F(x) = \sum_{n=0}^{\infty} C_n x^n$$

$$C_{n+1} = \sum_{k=0}^{n} C_k C_{n-k} \quad / \cdot x^{n+1} \quad / \sum_{n=0}^{\infty}$$

$$\sum_{n=0}^{\infty} C_{n+1} x^{n+1} = \sum_{n=0}^{\infty} \left( \sum_{k=0}^{n} C_k C_{n-k} \right) x^{n+1}$$

$$F(x) - \underbrace{C_0}_{1} = x F(x)^2$$

$$x F(x)^2 - F(x) + 1 = 0$$

Ali je potem:

$$F(x) = \frac{1 \pm \sqrt{1-4x}}{2x}$$

V $K[[x]]$ je $\frac{G(x)}{x}$ smiselno, če je $G(0)=0$.

$$\sqrt{1+x} = 1 + \sum_{n=1}^{\infty} \frac{(-1)^{n-1}}{2^{2n-1} n} \binom{2n-2}{n-1} x^n$$

$$\begin{aligned}
\sqrt{1-4x} &= 1 + \sum_{n=1}^{\infty} \frac{(-1)^{n-1}}{2^{2n-1} n} \binom{2n-2}{n-1} (-4x)^n \\
&= 1 - 2 \sum_{n=1}^{\infty} \frac{1}{n} \binom{2n-2}{n-1} x^n
\end{aligned}$$

$\frac{1+\sqrt{1-4x}}{2x}$ ni smiselno, $\frac{1-\sqrt{1-4x}}{2x}$ pa je

$$\begin{aligned}
F(x) &= \frac{1 - \sqrt{1-4x}}{2x} = \sum_{n=1}^{\infty} \frac{1}{n} \binom{2n-2}{n-1} x^{n-1} \\
&= \sum_{n=0}^{\infty} \frac{1}{n+1} \binom{2n}{n} x^n
\end{aligned}$$


### Razčlenitve števil (Particije)

$$p_{k}(n), \overline{p_{k}}(n), p(n)$$

> $$\sum_{0}^{\infty}\overline{p_{k}}(n)x^{n} = \prod_{i= 0}^{k}\frac{1}{1-x^{i}}$$
> Predstavlja produkt geometrijskih vrst do $k$-te potence saj je število načinov razčlenitev kjer so vsi elementi manjši ali enaki $k$ enako kot število razčlenitev kjer je elementov manj ali enako $k$ saj je konjugacije bijektivna z njo pa iz ene razčlenitve dobimo pripadajočo drugo.
> 


> Naj bo $p(n)$ število razčlenitev števila $n$ na poljubne seštevance. Rodovna funkcija za particije je:
> 
> $$\sum_{n=0}^\infty p(n) x^n = \prod_{i=1}^\infty \frac{1}{1 - x^i}$$


> $$\sum_{n=0}^{\infty}p_{k}(n)x^{n} = x^{k}\prod_{i=1}^{k}\frac{1}{1-x^{i}}$$
> S konjugacijo vemo da je to enako številu razčlenitev kjer je največji element biti enak $k$ saj če konjugiramo dobimo $k$ elementov, to pa bo natanko zmnožek potenčnih vrst od 1 do $k-1$, in potenčne vrste ki doda $x^{ik}$ vsakemu zmnožku torej bomo rabili potenčno vrsto $x^{k}+x^{2k}+...$ kar bo $x^{k}(1+x^{k}+...)$ kar bo $\frac{x^{k}}{1+x^{k}}$.


>[!|hide]-  **Uporaba rodovnih funkcij (Use of generating functions)**
> 
> Zakaj uporabljamo rodovne funkcije? (Why do we use generating functions?)
> 
> - Rodovna funkcija je pogosto "lepa", tudi če nimamo "lepe" formule za zaporedje (A generating function is often "nice", even if we don't have a "nice" formula for the sequence)
>   npr. (e.g.):
>   - $\sum p_k(n) x^n = \frac{1}{(1-x)(1-x^2)\dots(1-x^k)}$
>   - $\sum_n S(n,k) x^n = \frac{x^k}{(1-x)(1-2x)\dots(1-kx)}$
>   - $\sum_n S(n,k) \frac{x^n}{n!} = \frac{1}{k!} (e^x-1)^k$
> 
> - $i_n$ ... število involucij v $S_n$ ($i_n$ ... number of involutions in $S_n$)
>   $\pi^2 = \text{id} \iff \pi^{-1} = \pi$
>   $\sum_n i_n \frac{x^n}{n!} = e^{x + \frac{x^2}{2}}$
> 
> - Rodovno funkcijo (ali enačbo, ki ji ustreza rodovna funkcija) lahko pogosto dobimo z neposrednim kombinatoričnim razmislekom (A generating function (or an equation satisfied by a generating function) can often be obtained by direct combinatorial reasoning)
> 
>   - $a_n \dots$ št. kompozicij $n$ s členi $1$ in $2$ ($a_n$ ... number of compositions of $n$ with terms 1 and 2)
>     $F(x) = \sum_n a_n x^n = \frac{1}{1-(x+x^2)}$
>     (where $x$ represents ones, $x^2$ represents twos, and the denominator form represents a sequence)
> 
>   - $b_n \dots -||-$ s členi $1, 3$ in $4$
>     $F(x) = \sum_n b_n x^n = \frac{1}{1-x-x^3-x^4}$
> 
> ---
> 
> - $i_n \dots$ št. involucij v $S_n$
>   $\pi^2 = \text{id} \iff$ vsi cikli dolžine $1$ ali $2$ (all cycles of length 1 or 2)
>   $\sum_n i_n \frac{x^n}{n!} = e^{x + \frac{x^2}{2}}$
>   *(Notation: exponent is "composed of" cycles of length 1 (term $x$) and length 2 (term $\frac{x^2}{2}$))*
> 
> - $c_n \dots$ št. $\pi \in S_n : \pi^3 = \text{id}$
>   $\sum_n c_n \frac{x^n}{n!} = e^{x + \frac{x^3}{3}}$
> 
> - $d_n \dots \# \pi \in S_n : \pi^6 = \text{id}$
>   $\sum_n d_n \frac{x^n}{n!} = e^{x + \frac{x^2}{2} + \frac{x^3}{3} + \frac{x^6}{6}}$
> 
> **Dyckove poti (Dyck paths)**
> $C_n \dots$ št. Dyckovih poti dolžine $2n$
> Dyckova pot = prazna (empty) ali $\nearrow$ (Dyckova pot) $\searrow$ (Dyckova pot)
> *(The $\searrow$ step marks the "prva vrnitev na abscisno os" - first return to the x-axis)*
> $F(x) = 1 + x F^2(x)$
> 
> **Motzkinova pot (Motzkin paths)**
> $M_n \dots$ št. Motzkinovih poti dolžine $n$ (z $n$ koraki)
> prazna (empty) ali $\rightarrow$ (Motzkinova pot) ali $\nearrow$ (Motzkinova pot) $\searrow$ (Motzkinova pot)
> 
> $M(x) = \sum_n M_n x^n$
> $M(x) = 1 + x M + x^2 M^2$



***

### Permutacijske grupe

Imamo $[n]$. Velja da je $S_{n}$ množica vseh permutacij na $[n]$. **Permutacijska grupa** je podgrupa $G \leq S_{n}$ ki tvori grupo - torej vsebuje identiteto, asociativnost, inverze, zaprta.


Imamo množico $X$.
Rečemo da je $G$ permutacijska grupa $G \leq S_{X}$ in definiramo ekvivalenčno relacijo na $X$.

$$x \sim y \Leftrightarrow \exists \pi \in G : \pi(x) = y$$

**Refleksivnost** dokažemo z identiteto, **simetričnost** velja saj obstaja inverz, **tranzitivnost** tudi velja saj imamo kompozitum. 

Za primere imamo ciklično grupo, diedrsko grupo in simetrično grupo, kjer za vse velja da je njihova oribta 1.

Če pogledamo na primer $G = \{ \text{id, zrcaljenje}\}$ bo veljalo da ima za sodo število vozlišč $\frac{n}{2}$ orbit. Če je liho število imamo $\frac{n}{2}+1$ orbit.

Definiramo ekvivalenčne razrede katerim rečemo **orbite**.

Recimo da je $g \in G$ permutacija. Zapišemo

Permutacija $g$ preslika $x$ v $g(x)$.

$$g \cdot  x = g(x)$$

Vse točke v katere se lahko preslika $x$ preko katerekoli preslikave v $G$.

$$Gx = \{ g \cdot x \,;\; g \in G\}$$

Množica vseh različnih orbit.

$$X / G = \{ Gx \,;\; x \in X\}$$

Stabilizator elementa $x$ oz množica permutacij ki pustijo $x$ na miru

$$G_{x} = \{g \in G \,;\;g \cdot  x = x  \}$$

Množica negibnih točk elementa $g \in G$.

$$X^{g} = \{ x \in X; g  \cdot x = x\}$$
***
$G = C_n$ (Ciklična grupa - samo rotacije)

**$|X/G| = 1$**: Z rotacijami lahko prideš v katero koli oglišče, zato je le ena orbita.

**$G_x = \{id\}$**: Če poljubno oglišče $x$ zarotiramo za kateri koli kot (razen za $360^\circ$ oz. identiteto), se bo točka premaknila. Edini element, ki $x$ fiksira, je identiteta.

**$X^g$**: Če je $g = id$, potem vseh $n$ točk ostane na mestu. Če $g$ ni identiteta (je rotacija), se **nobena** točka ne fiksira (vse se premaknejo). Zato je množica fiksnih točk prazna ($\emptyset$).

---

$G = D_n$ (Diedrska grupa - rotacije in zrcaljenja)

**$|X/G| = 1$**: Ena orbita.

**$G_x = \{id, \text{zrcaljenje}\}$**: Za vsako oglišče pravilnega večkotnika obstaja natanko ena os zrcaljenja, ki gre skozi to oglišče. To oglišče fiksirata identiteta in to specifično zrcaljenje.

**$|X^g|$ (Število fiksnih točk za različne $g$):**
    *   Če je $g = id$, je fiksno vse ($|X|$ točk).
    *   Če je $g$ rotacija, je fiksno $0$ točk (vse se vrtijo).
    *   Če je $g$ **zrcaljenje**:
        *   Pri **lihem $n$**: Os gre vedno skozi 1 oglišče in sredino nasprotne stranice. Fiksna je **1** točka.
        *   Pri **sodem $n$, tip I**: Os gre skozi razpolovišča stranic. Nobeno oglišče ni fiksno (**0**).
        *   Pri **sodem $n$, tip II**: Os gre skozi dve nasprotni oglišči. Fiksni sta **2** točki.

---

$G = S_n$ (Simetrična grupa - vsa možna premešanja)

**$|X/G| = 1$**: Ena orbita.
**$|G_x| = (n-1)!$**: Če želimo, da točka $x$ ostane na miru, lahko preostalih $(n-1)$ elementov premešamo na poljuben način. Število vseh takšnih načinov je $(n-1)$ fakulteta.
**$X^g$**: To so enostavno tiste točke, ki jih določena permutacija $g$ ne premakne (v cikličnem zapisu so to "cikli dolžine 1").

---

$G = \{\text{id, zrcaljenje}\}$
Tukaj opazujemo samo eno specifično zrcaljenje.
*   **$G_x$**:
    *   Če točka $x$ leži **na osi** zrcaljenja, potem jo zrcaljenje ne premakne. Stabilizator sta oba elementa: $\{id, zrcaljenje\}$.
    *   Če točka $x$ **ne leži na osi**, jo zrcaljenje premakne na drugo stran. Stabilizator je samo $\{id\}$.
*   **$|X/G|$**: Število orbit je enako tistemu, kar si imel na prvi sliki (tiste formule s $\frac{n+1}{2}$ itd.).


>Stabilizator $G_{x}$ je podgrupa grupe $G$ oz. $G_{x} \leq G$.
>Identiteta je vedno v stabilizatorju, če združimo dve permutaciji iz stabilizatorja zapored sta še vedno v stabilizatorju in inverz je trivialen.
>
>Red grupe $G$ je enak produktu velikosti orbite in reda stabilizatorja $|G| = |Gx| \cdot  |G_{x}|$ poljubnega elementa $x$.
>
>*Odsek je aplikacija elemnenta grupe na vse elemente podrgupe. Torej $gH = \{ gh; g \in G, h \in H\}$, kjer je $H$ podrgupa, $g$ pa element iz grupe.*
>
>*Kovicentna množica je grupa vseh odsekov neke podrgupe.*
>
> Hočemo pokazati da je število elementov v orbiti $x$ enako številu odsekov stabilizatorja. Torej iščemo bijekcijo med $Gx \rightarrow G/G_{x}$
> 
>Naj bo preslikava definirana kot $f(gx) = gG_{x}$
>$g \cdot  x = g' \cdot  x \Leftrightarrow g^{-1}g' \cdot  x = x \Leftrightarrow g^{-1}g' \in G_{x} \Leftrightarrow gG_{x} = g'G_{x}$
>
>Smer $\Rightarrow$ dokazuje dobro definiranost, $\Leftarrow$ pa dokazuje injektivnost
>
>Surjektivnost: Za vsak odsek $gG_{x}$ v kvocientni množici $G/G_{x}$ po definiciji obstaja element $g \cdot  x$ v orbiti ki se vanj preslika $f(gx) = g G_{x}$




**Burnsidova lema**
Število orbit je enako povprečnemu številu negibnih (fiksnih) točk elementov grupe.

**Formula:**
$$|X/G| = \frac{1}{|G|} \sum_{g \in G} |X^g|$$
*   $|X/G|$: število orbit (to so "različni" objekti, ki jih štejemo).
*   $|G|$: število elementov v grupi simetrij.
*   $|X^g|$: število elementov v $X$, ki jih element $g$ ne premakne ($g \cdot x = x$).


Dokaz temelji na tehniki **dvojnega štetja** elementov v množici parov $S = \{ (g, x) \in G \times X \mid g \cdot x = x \}$. To so pari elementa grupe in elementa množice, kjer $g$ fiksira $x$.

**Vsoto preštejemo na dva načina (stolpci vs. vrstice)**

*   Če seštevamo po elementih $g$ (stolpci), dobimo $\sum_{g \in G} |X^g|$.
*   Če seštevamo po elementih $x$ (vrstice), dobimo $\sum_{x \in X} |G_x|$, kjer je $G_x$ stabilizator elementa $x$ (množica vseh $g$, ki ne premaknejo $x$).
Torej: $$\sum_{g \in G} |X^g| = \sum_{x \in X} |G_x|$$

Vemo, da za vsak element $x$ velja: $|G| = |Gx| \cdot |G_x|$, kjer je $|Gx|$ velikost orbite elementa $x$. Od tod izrazimo stabilizator:
$$|G_x| = \frac{|G|}{|Gx|}$$
Vstavimo to v našo vsoto:
$$\sum_{x \in X} |G_x| = \sum_{x \in X} \frac{|G|}{|Gx|} = |G| \sum_{x \in X} \frac{1}{|Gx|}$$


Zdaj celotno množico $X$ razbijemo na posamezne orbite (to je tisti krožec s podrobnostmi spodaj desno).
Namesto da seštevamo po vsakem $x$ posebej, seštevamo najprej znotraj vsake orbite $\mathcal{O}$, nato pa po vseh orbitah v $X/G$:
$$\sum_{x \in X} \frac{1}{|Gx|} = \sum_{\mathcal{O} \in X/G} \left( \sum_{x \in \mathcal{O}} \frac{1}{|\mathcal{O}|} \right)$$
Ker ima vsaka orbita natanko $|\mathcal{O}|$ elementov, je notranja vsota:
$$\sum_{x \in \mathcal{O}} \frac{1}{|\mathcal{O}|} = |\mathcal{O}| \cdot \frac{1}{|\mathcal{O}|} = 1$$
To pomeni, da vsaka orbita k celotni vsoti prispeva natanko **1**.

Celotna vsota je torej enaka številu orbit:
$$|G| \sum_{\mathcal{O} \in X/G} 1 = |G| \cdot |X/G|$$
Če združimo začetek in konec:
$$\sum_{g \in G} |X^g| = |G| \cdot |X/G|$$
Ko delimo z $|G|$, dobimo končno formulo Burnsidove leme. **Q.E.D.**

### Ciklični indeks in Polyjev izrek

Imamo grupo $G \leq S_{X}$.

Ciklični indeks grupe $G$ bo

$$Z_{G}(t_{1},...,t_{n}) = \frac{1}{|G|}\sum_{g \in G}^{}\prod_{c \in \text{cikli }g}t_{|c|}$$

Gre za polinom v premenljivkah $t_{1},...,t_{n}$, kjer $t_{i}$ predstavlja 1 cikle dolžine $i$.
Vsak element grupe $g$ lahko zapišemo kot produkt dijsunktnih ciklov. Torej bom za vsako permutacijo zmnožili skupaj $t_{i}$ ki predstavljajo $i$ - dolge cikle v permutaciji.

Ta produkt nam pove ciklično strukturo $g$.

Dobili bomo povprečno ciklično strukturo  v grupi.


**Dihedralna grupa $D_4$**

Primer prikazuje ciklični indeks grupe simetrij kvadrata ($D_4$), ki deluje na njegovih 4 ogliščih. Red grupe je $|G| = 8$.
Formula: $Z_{D_4}(t_1, t_2, t_3, t_4) = \frac{1}{8} (t_1^4 + 2t_4 + t_2^2 + 2t_1^2 t_2 + 2t_2^2)$

Posamezni členi ustrezajo geometrijskim transformacijam:
*   **$t_1^4$:** Identiteta. Vsako od 4 oglišč ostane na svojem mestu (štirje cikli dolžine 1).
*   **$2t_4$:** Rotaciji za $90^\circ$ in $270^\circ$. Vsa štiri oglišča se ciklično zamenjajo (en cikel dolžine 4).
*   **$t_2^2$:** Rotacija za $180^\circ$. Dva para oglišč si zamenjata mesti (dva cikla dolžine 2).
*   **$2t_1^2 t_2$:** Zrcaljenja čez simetrali stranic. Dve oglišči ostaneta fiksni (dva cikla dolžine 1), dve pa se zamenjata (en cikel dolžine 2).
*   **$2t_2^2$:** Zrcaljenja čez diagonali. Dva para oglišč si zamenjata mesti (dva cikla dolžine 2).



**Simetrije tetraedra**

Prikazan je ciklični indeks rotacijske grupe pravilnega tetraedra, ki deluje na njegovih 4 ogliščih. Red te grupe je 12.
Formula: $Z_G(t_1, t_2, t_3, t_4) = \frac{1}{12} (t_1^4 + 8t_1 t_3 + 3t_2^2)$
*   **$t_1^4$:** Identiteta (1 element).
*   **$8t_1 t_3$:** Rotacije za $120^\circ$ in $240^\circ$ okoli osi skozi oglišče in središče nasprotne ploskve. Eno oglišče je fiksno, ostala tri tvorijo cikel dolžine 3. Ker so 4 taka osišča in 2 smeri zasuka, je takih elementov 8.
*   **$3t_2^2$:** Rotacije za $180^\circ$ okoli osi skozi razpolovišči nasprotnih robov. Oglišča se zamenjajo v dveh parih (dva cikla dolžine 2). Obstajajo 3 take osi.

**Simetrije kocke**

Kocka ima rotacijsko grupo reda 24. Prikazana sta dva primera delovanja:

A) Delovanje na ogliščih ($n=8$)
Formula: $Z_G(t_1, \dots, t_8) = \frac{1}{24} (t_1^8 + 6t_4^2 + 3t_2^4 + 8t_1^2 t_3^2 + 6t_2^4)$
*   **$t_1^8$:** Identiteta.
*   **$6t_4^2$:** Rotacije za $90^\circ$ in $270^\circ$ skozi središča nasprotnih ploskev (3 osi $\times$ 2 smeri = 6 elementov). Oglišča tvorijo dva cikla dolžine 4.
*   **$3t_2^4$:** Rotacije za $180^\circ$ skozi središča nasprotnih ploskev (3 osi). Oglišča tvorijo štiri cikle dolžine 2.
*   **$8t_1^2 t_3^2$:** Rotacije za $120^\circ$ in $240^\circ$ okoli telesnih diagonal (4 osi $\times$ 2 smeri = 8 elementov). Dve oglišči na osi sta fiksni, ostalih 6 tvori dva cikla po 3.
*   **$6t_2^4$:** Rotacije za $180^\circ$ okoli osi skozi razpolovišča nasprotnih robov (6 osi). Osem oglišč tvori štiri cikle dolžine 2.

B) Delovanje na robovih ($n=12$)
Formula: $Z_G(t_1, \dots, t_{12}) = \frac{1}{24} (t_1^{12} + 6t_4^3 + 3t_2^6 + 8t_3^4 + 6t_1^2 t_2^5)$
*   **$t_1^{12}$:** Identiteta.
*   **$6t_4^3$:** Rotacije za $90^\circ$ in $270^\circ$ skozi središča ploskev. 12 robov se razporedi v tri cikle po 4.
*   **$3t_2^6$:** Rotacije za $180^\circ$ skozi središča ploskev. Robovi tvorijo šest ciklov po 2.
*   **$8t_3^4$:** Rotacije za $120^\circ$ in $240^\circ$ okoli telesnih diagonal. Robovi tvorijo štiri cikle po 3.
*   **$6t_1^2 t_2^5$:** Rotacije za $180^\circ$ okoli osi skozi razpolovišča nasprotnih robov. Dva robova, skozi katera gre os, ostaneta fiksna (dva cikla dolžine 1), ostalih 10 robov se zamenja v petih parih (pet ciklov dolžine 2).

> Velja da je
> 
> $$Z_{C_n}(t_1, \dots, t_n) = \frac{1}{n} \sum_{d|n} \phi(d) \cdot t_d^{n/d}$$
> 
> in
> 
> $$Z_{D_n}(t_1, \dots, t_n) = \frac{1}{2n} \sum_{d|n} \phi(d) t_d^{n/d} + \begin{cases} \frac{1}{2} t_1 t_2^{\frac{n-1}{2}} & ; n \text{ je lih} \\ \frac{1}{4} t_2^{n/2} + \frac{1}{4} t_1^2 t_2^{\frac{n-2}{2}} & ; n \text{ je sod} \end{cases}$$
> 
> 
> 
> **Dokaz za $C_n$:**
> Grupa $C_n$ je generirana z elementom $(1\, 2 \dots n)$. Njeni elementi so potence:
> $$C_n = \{ (1\, 2 \dots n)^i \mid 0 \le i \le n-1 \}$$
> 
> **Primeri potenc:**
> *   $(1\, 2\, 3\, 4\, 5\, 6)^2 = (1\, 3\, 5)(2\, 4\, 6)$ &nbsp; $\to$ 2 cikla dolžine 3.
> *   $(1\, 2\, 3\, 4\, 5\, 6)^3 = (1\, 4)(2\, 5)(3\, 6)$ &nbsp; $\to$ 3 cikli dolžine 2.
> *   $(1\, 2\, 3\, 4\, 5)^2 = (1\, 3\, 5\, 2\, 4)$ &nbsp; $\to$ 1 cikel dolžine 5.
> 
> **Splošno pravilo:**
> Če $d|n$, ima element $(1\, 2 \dots n)^d$ natanko $d$ ciklov dolžine $\frac{n}{d}$.
> Cikli so oblike: $(1, d+1, 2d+1, \dots), (2, d+2, 2d+2, \dots), \dots, (d, 2d, 3d, \dots)$.
> 
> **Trditev:** Če je $gcd(i, n) = 1$, potem ima $(1\, 2 \dots n)^i$ natanko 1 cikel dolžine $n$.
> *   **Dokaz 1:** Opazujemo zaporedje $(1, i+1, 2i+1, \dots)$. Cikel se zapre, ko je $ki+1 \equiv 1 \pmod n$, kar pomeni $n | ki$. Ker sta $i$ in $n$ tuja si, mora $n | k$. Najmanjši tak pozitiven $k$ je $n$, torej je dolžina cikla $n$.
> 
> **Končni izračun:**
> Naj bo $d = gcd(i, n)$. Potem je $n = n' \cdot d$ in $i = i' \cdot d$, kjer je $gcd(i', n') = 1$.
> Element $(1\, 2 \dots n)^i$ lahko zapišemo kot $((1\, 2 \dots n)^d)^{i'}$.
> To nam da $d$ ciklov dolžine $n'$.
> Vprašanje: Za koliko indeksov $i$ velja $d = gcd(n, i)$? To je ekvivalentno vprašanju, koliko je takih $i' \le n'$, da je $gcd(i', n') = 1$.
> Takih $i'$ je natanko $\phi(n')$, kjer je $n' = n/d$.
> 
> Zato je končna formula:
> $$Z_{C_n} = \frac{1}{n} \sum_{d|n} \phi\left(\frac{n}{d}\right) t_{n/d}^d$$
> (Z zamenjavo indeksov je to ekvivalentno zapisu $\frac{1}{n} \sum_{d|n} \phi(d) t_d^{n/d}$).
> 
> >[!|dokaz]- Dokaz:
> > 
> > $C_n = \{ \sigma^i ; \ 0 \leq i \leq n-1 \}$
> > 
> > $\sigma^i$ zapišemo $\sigma^i = \sigma^{d \cdot i'}$
> > 
> > $i = d \cdot i' \quad d = \gcd(n, i)$
> > $n = d \cdot n' \implies \gcd(n', i') = 1$
> > 
> > $\sigma^d ; d \mid n$
> > $\implies i, \ i+d, \ i+2d, \dots$
> > ker imamo $n$ el., bo vsak cikel imel
> > $\frac{n}{d} \text{ el.} \implies d \text{ ciklov}$
> > $\hookrightarrow n'$
> > ker sta $i'$ in $n'$ tuja
> > bo $(\sigma^d)^{i'}$; imamo $d$ ciklov, $\frac{n}{d} = n'$ el.
> > Torej se ne spremeni dolžina ciklov, ampak
> > le premeša notranji red.
> > 
> > To pomeni, da ima $\sigma^i$ enako cik. str. (ciklično strukturo) kot $\sigma^d$.
> > $d$ ciklov dolžine $\frac{n}{d} \implies t_{\frac{n}{d}}^d$
> > 
> > $\implies Z_{C_n} = \frac{1}{n} \sum_{i=0}^{n-1} (\text{struktura } \sigma^i)$
> > 
> > Namesto po $i$-jih seštevajmo po vseh možnih vrednostih
> > $\gcd(i, n) = d$, ker vemo, da ima $\sigma^d$ strukturo $t_{\frac{n}{d}}^d$.
> > 
> > Koliko $i$-jev je $\gcd(i, n) = d$?
> > $\iff$ koliko $i'$ je, da velja $i' \cdot d = i, \ \gcd(i', n') = 1$
> > $i' \in [1, n']$ oz. $(1, \frac{n}{d}]$
> > 
> > Torej $\phi(\frac{n}{d})$
> > 
> > $\implies \frac{1}{n} \sum_{d|n} \phi(\frac{n}{d}) \cdot t_{\frac{n}{d}}^d$


> **Pólyev izrek:**
> Število neekvivalentnih barvanj z $r$ barvami pod delovanjem grupe $G$ je:
> $$\frac{1}{|G|} \sum_{g \in G} r^{c(g)} = Z_G(r, r, \dots, r)$$
> *   $c(g) \dots$ število ciklov permutacije $g \in G \le S_X$
> *   $r \dots$ število barv

> **Izrek (posplošitev Pólyevega izreka):**
> Naj bodo $u_1, u_2, \dots, u_r$ uteži (spremenljivke), ki predstavljajo posamezne barve. Rodovna funkcija (polinom), ki nam pove število neekvivalentnih barvanj za vsako možno kombinacijo barv, je podana z:
> $$F(u_1, \dots, u_r) = Z_G(u_1 + \dots + u_r, u_1^2 + \dots + u_r^2, \dots, u_1^n + \dots + u_r^n)$$



### Delno urejene množice

Množica $P$ skupaj z relacijo $\le$ se imenuje **delno urejena** množica $(P, \le)$, če relacija za poljubne elemente $x, y, z \in P$ izpolnjuje tri aksiome:
*   **Refleksivnost:** Vsak element je v relaciji s samim seboj ($x \le x$).
*   **Antisimetričnost:** Če velja $x \le y$ in hkrati $y \le x$, potem sta elementa identična ($x = y$). To preprečuje krožne relacije med različnimi elementi.
*   **Tranzitivnost:** Če je $x \le y$ in $y \le z$, potem velja tudi $x \le z$. To omogoča dedovanje urejenosti skozi verigo elementov.

Klasični primeri
*   **Naravna urejenost ($\underline{n}, \le$):** Množica prvih $n$ naravnih števil z običajno relacijo "manjše ali enako". Tukaj sta poljubna dva elementa primerljiva.
*   **Boolova algebra ($B_n, \subseteq$):** Množica vseh podmnožic množice $\{1, \dots, n\}$. Relacija je vsebovanost ($\subseteq$). Elementa (podmnožici) nista nujno primerljiva (npr. $\{1\}$ in $\{2\}$ nista v relaciji vsebovanosti v nobeni smeri).
*   **Relacija deljivosti ($D_n, |$):** Množica vseh deliteljev števila $n$. Relacija je "deli" ($x | y$). Število $x$ je "manjše" od $y$, če $x$ deli $y$ brez ostanka.


Definiramo strožje oblike relacij:
*   **Stroga urejenost ($x < y$):** Velja $x \le y$ in hkrati $x \neq y$.
*   **Relacija pokrivanja ($x \lessdot y$):** Element $y$ **pokriva** element $x$, če velja $x < y$ in med njima ne obstaja noben tretji element $z$, za katerega bi veljalo $x < z < y$. To je neposredna povezava v urejenosti.

**Primeri pokrivanja:**
*   V običajni urejenosti števil $i+1$ pokriva $i$.
*   V Boolovi algebri množica $T$ pokriva množico $S$, če je $T$ enaka $S$ z dodanim natanko enim novim elementom.
*   Pri deljivosti število $s$ pokriva $r$, če je količnik $s/r$ praštevilo.

**Hassejev diagram**
Hassejev diagram je grafična ponazoritev delno urejene množice:
*   Vozlišča so elementi množice $P$.
*   Povezava (rob) se nariše samo med tistimi elementi, kjer velja relacija pokrivanja ($x \lessdot y$).
*   Element $x$ se vedno nariše nižje od elementa $y$, če velja $x \lessdot y$. Tranzitivne povezave (npr. med $x$ in $z$, če $x < y < z$) se ne rišejo, saj so razvidne iz poti v grafu.


> Obstaja izomorfizem med delitelji števil s $k$ močno razdelitvijo na prafaktorje in $k$ veliko booleanovo algebro.

Elementa sta **primerljiva** če velja $x \leq y$ ali $y \leq x$, če nobena od teh ne velja nista.

**Veriga $C$** je podmnožica v kateri so poljubni trije elementi med seboj primerljivi. Veriga predstavlja linearno urejen del v sicer delno urejeni množici.

**Antiveriga $A$** je podmnožica v kateri sta poljubna dva različna elementa neprimerljiva.

V booleanovi algebri so primeri verige podmnožice ki naraščajo z dodajanjem elementov. Antivergie pa npr. podmnožice velikosti $k$.

**Maksimalen element** je element $x$ za katerega ne obstaja noben element $y$ ki bi bil strogo večji od $x$. Na hassejevm diagramu so to vozl. iz katerih nobena povezava ne vodi navzgor.

**Največji element** je element $x$ ki je večji ali enak vsem ostalim elementom v množici. Če največji element obstaja je natanko eden in je hkrati tudi edini maksimalen element.

Enako velja za **minimalen in najmanjši element.**

Velja  $x$ je največji $\Rightarrow$ je maksimalen. Če ima delno urejena množica več največjih elementov bi veljalo $y \geq x$ in $x \geq y$ kar pomeni da je $x = y$ torej je največji element enoličen. 

> V vsaki neprazni končni delno urejeni množici vedno obstaja vsaj en maksimalen element. *Če začnemo pri polj. $x$ in ni maksimalen vzamemo večji elemnt in ponavljamo. Ker je končno število elementov bomo prišli do konca.*
> V neskončni množici ne obstaja vedno - naravna števila.

>Množica vseh maksimalnih elementov vedno tvori antiverigo - *če ne bi bi pomenilo da sta dva elementa notri primerljiva kar pomeni da sta ali enaka ali pa je en večji od drugega.*


**Višina** je dolžina najdaljše verige.

**Širina** je velikost največje antiverige v $P$. *Koliko elementov je v najsabšem primeru neprimerljivih.*

>**Mirskyjev izrek**
>
> Naj bo $P$ končna delno urejena množica z višino $M$. Naj bo $m$ najmanjše število antiverig, s katerimi lahko pokrijemo celotno množico $P$ (tako da je vsak element v vsaj eni antiverigi). Potem velja:
> $$M = m$$
> *(Z drugimi besedami: najmanjše število antiverig za pokritje je enako velikosti najdaljše verige).*


Dokaz je razdeljen na dva dela, ki skupaj dasta enakost:

**A) Smer $M \le m$ (Enostavnejša smer)**
Vzemimo poljubno verigo $C$ dolžine $|C|$ in poljubno pokritje z $m$ antiverigami. Ker antiveriga po definiciji vsebuje le neprimerljive elemente, lahko iz poljubne verige vsebuje **največ en element**. Da bi torej pokrili vseh $M$ elementov najdaljše verige, potrebujemo vsaj $M$ različnih antiverig. Od tod sledi $m \ge M$.

**B) Smer $m \le M$ (Dokaz z indukcijo)**
Dokazujemo s pomočjo indukcije na število elementov množice $|P|$.
1.  **Baza:** Če ima množica le 1 element, je $M=1$ in $m=1$, kar drži.
2.  **Indukcijski korak:** Predpostavimo, da trditev velja za vse množice, manjše od $P$.
    *   Naj bo $A$ množica vseh maksimalnih elementov v $P$. Kot smo ugotovili, je $A$ antiveriga.
    *   Poglejmo manjšo množico $P \setminus A$ (množico $P$ brez maksimalnih elementov).
    *   **Ključna ugotovitev:** Najdaljša veriga v $P \setminus A$ ima dolžino $M-1$. Če bi namreč v $P \setminus A$ obstajala veriga dolžine $M$, bi njenemu največjemu elementu $x$ lahko dodali nek element $y \in A$, ki je nad njim (tak $y$ mora obstajati, sicer bi bil $x$ že sam maksimalen v $P$). To bi nam dalo verigo dolžine $M+1$ v celotni množici $P$, kar je v nasprotju s predpostavko, da je višina $M$.
    *   Po indukcijski predpostavki lahko $P \setminus A$ pokrijemo z $M-1$ antiverigami.
    *   Če tem dodamo še antiverigo $A$, dobimo pokritje celotne množice $P$ z natanko $M$ antiverigami.
    *   Torej je $m \le M$.

Ker velja $M \le m$ in $m \le M$, sledi končni rezultat: **$M = m$**.

>[!|hide]- Dodatno
> 
> #### 2. del: $m \le M$ (Indukcijski del)
> Dokazujemo s pomočjo indukcije na število elementov $|P|$.
> 
> **Baza indukcije:** 
> Če ima množica $P$ le 1 element, je $M=1$ in $m=1$. Izrek drži.
> 
> **Indukcijski korak:** 
> Predpostavimo, da izrek velja za vse delno urejene množice, ki imajo manj kot $n$ elementov. Naj ima naša množica $P$ natanko $n$ elementov in naj bo $M$ njena širina (velikost največje antiverige).
> 
> Ločimo dva primera:
> 
> **Primer A: Obstaja največja antiveriga $A$, ki ni niti množica vseh maksimalnih niti množica vseh minimalnih elementov $P$.**
> 1.  Definiramo dve podmnožici:
>     *   $S^+ = \{x \in P \mid \exists a \in A, x \ge a\}$ (vse "nad" antiverigo $A$)
>     *   $S^- = \{x \in P \mid \exists a \in A, x \le a\}$ (vse "pod" antiverigo $A$)
> 2.  Ker $A$ ni množica vseh maksimalnih/minimalnih elementov, sta $S^+$ in $S^-$ strogo manjši od $P$ ($|S^+| < |P|$ in $|S^-| < |P|$).
> 3.  Obe množici vsebujeta antiverigo $A$, zato je njuna širina še vedno $M$.
> 4.  Po indukcijski predpostavki lahko $S^+$ pokrijemo z $M$ verigami $\{C_1^+, \dots, C_M^+\}$ in $S^-$ z $M$ verigami $\{C_1^-, \dots, C_M^-\}$.
> 5.  Vsak element $a_i \in A$ je minimalen v $S^+$ in maksimalen v $S^-$. Zato se vsaka veriga $C_i^+$ začne pri nekem $a_i$ in vsaka $C_i^-$ konča pri istem $a_i$.
> 6.  Združimo jih v nove verige $C_i = C_i^- \cup C_i^+$. Teh $M$ verig pokrije celoten $P$. Torej $m \le M$.
> 
> **Primer B: Vsaka največja antiveriga je bodisi množica vseh maksimalnih bodisi množica vseh minimalnih elementov.**
> 1.  Izberemo poljuben minimalen element $x$ in poljuben maksimalen element $y$, tako da velja $x \le y$ (tak par vedno obstaja; v najslabšem primeru je $x=y$).
> 2.  Opazujmo manjšo množico $P' = P \setminus \{x, y\}$.
> 3.  Če bi bila širina $P'$ še vedno $M$, bi v njej obstajala antiveriga $A$ velikosti $M$. Ta $A$ bi bila tudi največja antiveriga v $P$, vendar ne bi vsebovala $x$ (ki je minimalen) in $y$ (ki je maksimalen). To bi pomenilo, da $A$ ni niti množica vseh minimalnih niti maksimalnih elementov, kar je v nasprotju s predpostavko Primere B.
> 4.  Torej mora biti širina $P'$ enaka $M-1$.
> 5.  Po indukcijski predpostavki lahko $P'$ pokrijemo z $M-1$ verigami.
> 6.  Če tem verigam dodamo še verigo $\{x, y\}$, dobimo pokritje celotne množice $P$ z natanko $M$ verigami. Torej $m \le M$.
> 
> ---
> 
> ### Sklep
> V obeh primerih smo pokazali, da lahko $P$ pokrijemo z $M$ verigami. Ker smo v prvem delu že ugotovili, da potrebujemo vsaj $M$ verig, sledi končni rezultat:
> **$m = M$**
> (Najmanjše število verig v pokritju je enako velikosti največje antiverige). $\square$



***

V grafu $G$ je **prirejanje** (*matching*) množica robov $M \subseteq E(G)$ s to lastnostjo, da noben par robov v $M$ nima skupnega vozlišča. Formalno: za vsaka $e, f \in M$, kjer $e \neq f$, velja $e \cap f = \emptyset$.

*   **Popolno prirejanje:** Prirejanje $M$ je popolno, če vsako vozlišče grafa $G$ pripada natanko enemu robu iz $M$. To pomeni, da so vsa vozlišča prekrita.
*   **Dvodelni grafi:** Graf $G$ je dvodelen, če se njegova vozlišča dajo razdeliti v dve disjunktni množici $X$ in $Y$ ($V(G) = X \cup Y$), robovi pa obstajajo le med $X$ in $Y$.
*   **Prirejanje iz $X$ v $Y$:** To je prirejanje, ki prekrije vsa vozlišča v množici $X$. Obstoj takšnega prirejanja je ekvivalenten obstoju **injektivne preslikave** $f: X \to Y$, kjer sta vozlišče $x$ in njegova slika $f(x)$ sosednja v grafu.

**Hallov poročni izrek**

Izrek podaja potreben in zadosten pogoj za obstoj prirejanja, ki prekrije množico $X$.
*   **Soseska množice:** Naj bo $A \subseteq X$. Soseska $N(A)$ je množica vseh vozlišč v $Y$, ki so sosednja vsaj enemu vozlišču iz $A$.
*   **Hallov pogoj:** Za obstoj prirejanja iz $X$ v $Y$ mora za vsako podmnožico $A \subseteq X$ veljati, da je velikost njene soseske vsaj tolikšna kot velikost množice same: **$|A| \le |N(A)|$**.
*   **Hallov izrek:** V dvodelnem grafu $G = (X \cup Y, E)$ obstaja popolno prirejanje iz $X$ v $Y$ natanko tedaj, ko za vsak $A \subseteq X$ velja $|A| \le |N(A)|$.

**Dokaz Hallovega izreka preko Dilworthovega izreka**

Smer $(\Leftarrow)$ z uporabo teorije delno urejenih množic (DUM).
1.  **Konstrukcija DUM:** Vozlišča grafa $V = X \cup Y$ obravnavamo kot elemente delno urejene množice $P$. Relacijo urejenosti $\le$ definiramo tako:
    *   $x \le x$ za vse $x \in X$, $y \le y$ za vse $y \in Y$.
    *   $x \le y$ natanko tedaj, ko sta $x \in X$ in $y \in Y$ sosednja v grafu ($x \sim y$).
2.  **Največja antiveriga:** Naj bo $A \cup B$ največja antiveriga v $P$, kjer je $A \subseteq X$ in $B \subseteq Y$. Ker so elementi v antiverigi neprimerljivi, nobena povezava v grafu ne sme obstajati med $A$ in $B$. To pomeni, da je soseska množice $A$ vsebovana v preostanku $Y$: $N(A) \subseteq Y \setminus B$.
3.  Iz Hallovega pogoja sledi $|A| \le |N(A)| \le |Y| - |B|$, kar preuredimo v $|A| + |B| \le |Y|$.
4.  To pomeni, da je velikost največje antiverige v $P$ enaka natanko $|Y|$ (saj je množica $Y$ sama po sebi že antiveriga velikosti $|Y|$).
5.  **Uporaba Dilworthovega izreka:** Množico $P$ lahko pokrijemo z $|Y|$ disjunktnimi verigami. Ker so verige v tej DUM dolžine največ 2 (vsebujejo bodisi $\{y\}$ bodisi $\{x, y\}$), verige dolžine 2 predstavljajo robove prirejanja, ki prekrije vse $x \in X$.

**Biregularni grafi in posledice**

*   **Posledica:** Če v neproznem dvodelnem grafu za vsako vozlišče $x \in X$ in $y \in Y$ velja, da je stopnja $x$ večja ali enaka stopnji $y$ ($\deg(x) \ge \deg(y)$), potem obstaja popolno prirejanje iz $X$ v $Y$.
*   **Biregularni graf:** Graf je $(r, s)$-biregularen, če imajo vsa vozlišča v $X$ stopnjo $r$ in vsa vozlišča v $Y$ stopnjo $s$.
*   Število robov $|E|$ v takem grafu je $r|X| = s|Y|$.
*   Če je graf biregularen in velja $|X| \le |Y|$, potem velja $r \ge s$, iz česar po zgornji posledici sledi, da popolno prirejanje iz $X$ v $Y$ vedno obstaja.

### 5. Uporaba: Uganka s petimi kartami (Stran 7)

Zapiski opisujejo matematično ozadje trika, kjer prijatelj prejme 5 kart in vam pokaže 4 v določenem zaporedju, vi pa ugotovite peto.
*   **Modeliranje z grafom:**
    *   Množica $X$ so vse neurejene podmnožice 5 kart iz kompleta $N$ kart ($|X| = \binom{N}{5}$).
    *   Množica $Y$ so vse urejene četverice (permutacije 4 kart).
    *   Povezava $x \sim y$ obstaja, če je četverica $y$ podmnožica peterice $x$.
*   Problem je najti popolno prirejanje iz $X$ v $Y$. Graf je biregularen, izračun pokaže, da prirejanje obstaja, če velja $N \le 124$ (za $N=52$ pogoj drži).
*   **Strategija za $N=52$:**
    1.  Po Dirichletovem načelu sta med 5 kartami vsaj dve iste barve.
    2.  Eno od teh dveh "barvnih" kart skrijemo, drugo pokažemo kot prvo.
    3.  Preostale 3 karte razvrstimo v eno od $3! = 6$ možnih permutacij. Ta vrstni red zakodira razdaljo (od 1 do 6 korakov) v cikličnem zaporedju vrednosti kart iste barve (krog z 13 vrednostmi).

Na dnu strani 7 je še kratka opomba o **Conwayevem "Doomsday" algoritmu** za določanje dneva v tednu za poljuben datum, ki temelji na fiksiranju določenih datumov v letu (npr. 4.4., 6.6., 8.8.), ki vedno padejo na isti dan v tednu.


**Širina Boolove algebre $B_n$**
Vemo, da je v $B_n$ poljubna "plast" podmnožic fiksne velikosti $k$ (označena z $\binom{[n]}{k}$) **antiveriga**. Nobena podmnožica velikosti $k$ namreč ne more vsebovati druge različne podmnožice iste velikosti. 
Širina množice $B_n$ je torej vsaj tako velika, kot je največja med temi plastmi.

**Katera plast je največja?**
Lema pravi, da je binomski simbol $\binom{n}{k}$ največji pri "sredinskem" $k$. 
*   **Dokaz:** Zapiski primerjajo $\binom{n}{k}$ in $\binom{n}{k+1}$. Z razpisom faktorielov in krajšanjem dobimo pogoj $2k+1 \le n$. 
*   To pomeni, da vrednosti binomskih simbolov naraščajo do sredine in nato padajo. Takšnemu zaporedju pravimo **unimodalo zaporedje**.
*   Največja vrednost se torej doseže pri $k = \lfloor n/2 \rfloor$ (ali $\lceil n/2 \rceil$ pri lihih $n$).

### 3. Spernerjev izrek (Stran 8)
Izrek pravi, da je širina Boolove algebre $B_n$ natanko enaka velikosti njene največje plasti:
$$\text{Širina } B_n = \binom{n}{\lfloor n/2 \rfloor}$$

### 4. Dokaz Spernerjevega izreka (Stran 8 in 9)

Dokaz temelji na štetju **maksimalnih verig**. Maksimalna veriga v $B_n$ je zaporedje podmnožic od prazne množice do celotne množice, kjer vsaka naslednja vsebuje natanko en element več: $\emptyset \subset \{i_1\} \subset \{i_1, i_2\} \subset \dots \subset [n]$.

1.  **Število vseh maksimalnih verig:** Vsaka takšna veriga ustreza eni permutaciji elementov množice $[n]$, zato jih je skupaj **$n!$**.
2.  **Verige skozi fiksno podmnožico $S$:** Naj bo $S$ podmnožica velikosti $k$. 
    *   Do $S$ lahko pridemo na $k!$ načinov (vsi vrstni redi dodajanja elementov v $S$).
    *   Od $S$ do celotne množice $[n]$ lahko nadaljujemo na $(n-k)!$ načinov.
    *   Število maksimalnih verig, ki vsebujejo množico $S$, je torej **$|S|! (n - |S|)!$**.
3.  **Ključni sklep:** Naj bo $A$ poljubna antiveriga v $B_n$. Ker je $A$ antiveriga, vsaka maksimalna veriga vsebuje **največ en element** iz $A$. 
4.  **LYM neenakost (Stran 9):** Vsota vseh maksimalnih verig, ki gredo skozi kateri koli element iz $A$, ne sme preseči skupnega števila vseh maksimalnih verig:
    $$\sum_{S \in A} |S|! (n - |S|)! \le n!$$
    Če celotno neenačbo delimo z $n!$, dobimo:
    $$\sum_{S \in A} \frac{1}{\binom{n}{|S|}} \le 1$$
5.  **Zaključek:** Ker vemo iz leme, da je $\binom{n}{|S|} \le \binom{n}{\lfloor n/2 \rfloor}$, velja obratno za ulomke: $\frac{1}{\binom{n}{|S|}} \ge \frac{1}{\binom{n}{\lfloor n/2 \rfloor}}$.
    Zamenjamo vsak člen v vsoti z najmanjšim možnim členom:
    $$\frac{|A|}{\binom{n}{\lfloor n/2 \rfloor}} \le \sum_{S \in A} \frac{1}{\binom{n}{|S|}} \le 1$$
    Iz tega sledi $|A| \le \binom{n}{\lfloor n/2 \rfloor}$.

### 5. Posledica: Povezava z Dilworthom (Stran 9)
Združitev Dilworthovega in Spernerjevega izreka nam pove, da lahko celotno Boolovo algebro $B_n$ (vse podmnožice) pokrijemo z natanko $\binom{n}{\lfloor n/2 \rfloor}$ disjunktnimi verigami. 

To je močan rezultat, saj nam pove, da čeprav je podmnožic $2^n$ (eksponentna rast), jih lahko "popredalčkamo" v razmeroma majhno število verig glede na celotno število elementov.