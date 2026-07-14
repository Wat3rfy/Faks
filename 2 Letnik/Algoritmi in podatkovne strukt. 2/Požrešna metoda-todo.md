Požrešna metoda se nanaša na pristop k reševanu optimizacijskih problemov kjer si izberemo nek **parameter** **ponavadi lahko izračunljiv ali očiten** po katerem gradimo rešitev problema.

Izbira parametra po kateri bomo gradili rešitev je najpomembnejša in si jo je treba pravilno izbrati - ni pa vedno nujno da je problem rešljiv na požrešen način.

Da dokažemo da je rešitev ki jo dobimo s požrešno metodo pravilna moramo dokazati pravilnost. To lahko storimo s tem da pokažemo da je v vsakem koraku iteracije rešitev vsaj tako dobra kot nek drug pristop ki pripelje do optimalne rešitve.

Lahko pa tudi storimo tako da začnemo s poljubno optimalno rešitvijo in jo preoblikujemo v požrešno rešitev.

**Primer 1 - izbira intervalov**

Imamo podanih $n$ intervalov $[s_{i}, f_{i})$. Hočemo izbrati kar se da veliko intervalov ki se ne prekrivajo.

Najprej hočemo določiti po kateri lastnosti izbiramo intervale in jih damo v rešitev. Na vsakm koraku bomo seveda upoštevali le intervale ki se ne prekrivajo.

Lahko izbiramo po temu kateri se prvi začne, po dolžini, po številu konfliktov - ampak moramo paziti če obstaja protiprimer. Izkaže se da je optimalno izbiranje po končnih točkah intervalov oz. kateri se prvi konča.

Najprej sortiramo intervale po končnem času. Nato pa izbiramo intervale enega za drugim če se ne prekrivajo z že izbranimi.

Sedaj moramo dokazati optimalnost dobljene množice intervalov.

Predpostavmo da je $A = \{ I_{1},...,I_{k}\}$ naša množica ki jo dobimo s tem postopkom in $O = \{ J_{1},...,J_{m}\}$ optimalna množica.

Dokazujemo da je $|O| = |A|$.

BSŠ predpostaivmo da sta $O$ in $A$ urejena po končnih časih intervalov.

Ker vemo da je $O$ optimalna vemo da že velja $|O| \geq |A|$ moramo le še dokazati $|A| \geq |O|$.

Naj bo $f(I_{i}) := f_{i}$ oz. končni čas intervala $I_{i}$.

Če velja da je  $f(I_{r}) \leq f(J_{r})$ za vse $r \leq |O|$ potem vemo da bo $|A|$ vseboval vsaj toliko intervalov kot $|O|$ oz. $|A| \geq |O|.$

Najprej preverimo bazo indukcije

$$f(I_{1}) \leq f(J_{1})$$

To velja ker je $I_{1}$ po definciji interval z najzgodnejšim $f_{i}$

Recimo da velja $f(I_{r-1}) \leq f(J_{r-1})$.

Potem velja da ko izberemo naslednji interval lahko izberemo nek interval $I_{r}$ ki se prej konča kot $J_{r}$, ali pa preprosto izbermo $J_{r}$, ker smo predpostavili da je $O$ urejen bo veljalo da če izberemo interval ki se konča prej ali enako kot $J_{r}$ imamo še vedno na izbiro vse intervale ki so v $O$ in mogoče boljše torej smo vedno na boljšem ali istem kot $O$. Torej je $|A| \geq |O|$

Sledi da je $|A| = |O|$.

Ta algoritem porabi $O(n \log_{}{n})$ za sortiranje intervalov in $O(n)$ za izbiranje. Torej

$$O(n \log_{}{n})$$


**Primer 2 – minimizacija maksimalne zamude**

Podanih imamo $n$ opravil. Za vsako opravilo $i$ poznamo trajanje $t_{i}$ in rok $d_{i}$, do katerega bi moralo biti opravilo končano. Naš cilj je določiti začetne čase $s_{i}$ tako, da bo **maksimalna zamuda** čim manjša.

Za vsako opravilo velja:
- Končni čas: $f_{i} = s_{i} + t_{i}$
- Zamuda: $\ell_{i} = f_{i} - d_{i}$ (če je opravilo končano pred rokom, je zamuda negativna)
- Cilj: Minimizirati $L = \max(\ell_{i})$

Najprej določimo požrešno strategijo. Razmišljamo lahko o izbiri po najkrajšem trajanju $t_{i}$ ali po najmanjši rezervi ($d_{i} - t_{i}$), vendar se za optimalno izkaže **urejanje po rokih ($d_{i}$)**.

**Algoritem:**
1. Sortiramo opravila po naraščajočih rokih $d_{1} \leq d_{2} \leq \dots \leq d_{n}$.
2. Opravila izvajamo zaporedno brez presledkov: $s_{1} = 0$ in $s_{i} = f_{i-1}$ za $i > 1$.

Sedaj dokažimo optimalnost tega postopka z uporabo **argumenta zamenjave (exchange argument)**.

**Dokaz optimalnosti:**

Najprej opazimo dve lastnosti optimalnega razporeda:
1. **Brez lukenj:** Obstaja optimalen razpored, ki nima vmesnega prostega časa (če bi bil prost čas, lahko naslednja opravila premaknemo nazaj in zamudo le zmanjšamo).
2. **Brez inverzij:** Inverzija se zgodi, če je opravilo $j$ v razporedu pred opravilom $i$, čeprav je rok $d_{i} < d_{j}$.

Dokazujemo, da naš algoritem (ki nima lukenj in nima inverzij) proizvede optimalno rešitev.

Predpostavimo, da obstaja optimalen razpored $O$, ki ima vsaj eno inverzijo. Če ima razpored inverzijo, potem nekje v njem obstajata dve **zaporedni** opravili $j$ in $i$, kjer velja $d_{i} < d_{j}$, vendar je $j$ pred $i$.

Poglejmo, kaj se zgodi, če njuni mesti zamenjamo:
- Zamude vseh ostalih opravil ostanejo nespremenjene.
- Pred zamenjavo je bila maksimalna zamuda teh dveh opravil $\max(\ell_j, \ell_i)$. Ker je $i$ na vrsti za $j$, je $\ell_i = (s + t_j + t_i) - d_i$.
- Po zamenjavi (najprej $i$, nato $j$) dobimo novi zamudi $\ell'_i$ in $\ell'_j$.
  - $\ell'_i = s + t_i - d_i$
  - $\ell'_j = s + t_i + t_j - d_j$

Ker je $t_j > 0$, je očitno $\ell'_i < \ell_i$.
Ker je $d_i < d_j$, je $\ell'_j < \ell_i$ (saj od istega končnega časa odštejemo večji rok).

Torej je $\max(\ell'_i, \ell'_j) \leq \ell_i \leq \max(\ell_j, \ell_i)$. Zamenjava sosednjih opravil, ki so bila v inverziji, torej **ne poveča** maksimalne zamude.

Z zaporednimi zamenjavami sosednjih inverzij (podobno kot pri urejanju z mehurčki) lahko vsak optimalen razpored spremenimo v naš razpored, ne da bi pri tem poslabšali maksimalno zamudo. Sledi, da je naš algoritem optimalen.

**Časovna zahtevnost:**
Algoritem porabi $O(n \log n)$ časa za sortiranje opravil po rokih in $O(n)$ časa za določitev začetnih časov.

$$O(n \log n)$$


Tukaj je strukturiran zapis še za tretji primer, pripravljen v enakem slogu kot predhodna dva.

***

**Primer 3 – Huffmanovo kodiranje**

Imamo abecedo $\Sigma$ z $n$ znaki, kjer ima vsak znak $c$ podano pogostost pojavljanja $f_{c}$. Naš cilj je vsakemu znaku določiti binarno kodo $\gamma(c)$ tako, da bo celotno sporočilo čim krajše. To dosežemo z minimizacijo **povprečne bitne dolžine (ABL)**.

$$ABL(\gamma) = \sum_{c \in \Sigma} f_{c} \cdot |\gamma(c)|$$

Pri tem moramo upoštevati pogoj **predponskega kodiranja**: nobena koda ne sme biti predpona druge kode (npr. če je 'A' kodiran kot `01`, potem se nobena druga koda ne sme začeti z `01`). To nam omogoča enolično dekodiranje brez uporabe ločil.

Problem si najlažje predstavljamo z dvojiškim drevesom:
- Znaki so **listi** drevesa.
- Pot od korena do lista določa kodo (levo = `0`, desno = `1`).
- Globina lista $d(c)$ ustreza dolžini kode $|\gamma(c)|$.

**Požrešna strategija (Huffmanov algoritem):**
Namesto da bi drevo gradili od zgoraj navzdol, ga gradimo od spodaj navzgor. Na vsakem koraku izberemo dva znaka (ali poddrevesa) z **najmanjšima pogostostma** in ju združimo v novo vozlišče, katerega pogostost je vsota njunih pogostosti.

**Dokaz optimalnosti:**

> Če imata $x,y$ najmanjšo frekvenco potem obstaja optimalna koda kjer je koda za $x,y$ enako dolga in se razlikujeta le za zadnji bit (sta brata v listih)
> >[!|dokaz]+ Dokaz:
> > Naj bosta $x,y$ poljubna lista v optimalnem drevesu $T$ in $a,b$ sosednja otroka na maksimalni globini, $f_{x},f_{y}$ najmanjši frekvenci. Naj bo $f_{x} < f_{y}$ in $f_{a} < f_{b}$, zamenjamo $x$ in $a$ in $y$ in $b$, da dobimo $T'$ tako da je $\text{depth}(a) \geq \text{depth}(x)$
> > $$B(T)-B(T')$$
> > $$\sum_{c}^{}f_{c} \cdot |\gamma_{T}(c)| - \sum_{}^{}f_{c} \cdot  |\gamma_{T'}(c)|$$ 
> > $$f_{a} \cdot \text{depth}(x) + f_{x} \cdot \text{depth}(a) - f_{a} \cdot \text{depth}(a) - f_{x} \cdot \text{depth}(x)$$
> > $$(f_{a} - f_{x})(\text{depth}(x)-\text{depth}(a)) \geq 0$$
> > Torej je $$B(T) \geq B(T')$$

> Naj bo abeceda $C \cup \{ x,y\}$ in naj bosta $f_{x},f_{y}$ najmanjši frekvenci abecede. Naj bo $T'$ optimalno drevo abecede $C \cup \{ z\}$, kjer velja da je $f_{z} = f_{x}+f_{y}$.
> Velja da je $T$ ki ga dobimo tako da $T'$ namesto $z$ damo vozlišče z otrokoma $x,y$ optimalno za abecedo $C \cup \{ x,y\}$.
> >[!|dokaz]+ Dokaz:
> >
> >Naj bo $T'$ optimalno drevo za $C \cup \{ z\}$.
> >
> > Za vse $c \in C \cup \{ x,y\}$ velja da je $f_{c} \cdot \text{depth}(c)$ enaka v $T$ in v $T'$. Edina sprememba je $f_{x} \cdot  \text{depth}(x) + f_{y} \cdot  \text{depth}(y) = (f_{x} + f_{y})\cdot (\text{depth}(z)+1)$.
> > 
> >Torej je 
> >
> >$$B(T) = \sum_{c \neq x,y}^{}... + f_{x}\cdot \text{depth}(x)+f_{y}\cdot  \text{depth(y)}$$
> >$$B(T) = \sum_{c \neq x,y}^{}... + (f_{x} + f_{y})\cdot (\text{depth}(z)+1)$$
> >$$B(T) = \sum_{c \neq x,y}^{}... + f_{z}\cdot \text{depth(z)} + f_{x} + f_{y}$$
> >$$B(T) = B(T') + f_{x} + f_{y}$$
> >
> >Torej $B(T') = B(T)-f_{x}-f_{y}$
> >
> >Naj bo $T$ ki ga dobimo neoptimalna koda za $C \cup \{ x,y\}$, BŠS obstaja $T''$, kjer sta $x,y$ soseda tako da je $B(T'') < B(T)$. Naj bo $T'''$ drevo kjer $x,y$ odstranimo in njunega starša zmaenjamo z elementom $z$ kar pomeni
> >$B(T''') = B(T'')-f_{x}-f_{y} < B(T) - f_{x}-f_{y} = B(T')$
> >Kar bi pomenilo da $T'$ ni optimalno drevo ampak ker smo to predpostavili je to protislovje.



**Časovna zahtevnost:**
V vsakem koraku moramo najti dva najmanjša elementa, kar najučinkoviteje izvedemo s **prioritetno vrsto** (kopico).
- Gradnja kopice: $O(n)$
- $n$ operacij brisanja minimuma in vstavljanja: $O(n \log n)$

Skupna zahtevnost:

$$O(n \log n)$$

**Omejitve:**
Huffmanovo kodiranje je optimalno pod pogojem, da znake kodiramo posamično in da so pogostosti vnaprej znane ter konstantne. Če se statistika besedila spreminja ali če želimo še večjo kompresijo, uporabimo druge metode (npr. aritmetično kodiranje ali Lempel-Ziv).