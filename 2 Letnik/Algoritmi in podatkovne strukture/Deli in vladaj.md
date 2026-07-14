

## Krovni izrek

- Nek problem velikosti $n$ lahko razbijemo na več podproblemov.
<br>
- Ob klicu rekurzije razbijemo problem velikosti $n$ na več podproblemov velikosti $\frac{n}{b}$.
- Vpeljali smo faktor **$b$** - število podproblemov ki nastane. *To ni enako številu podproblemov ki jih moramo rešiti.*
<br>
- Ker ni nujno da algoritem preverja vse veje/podprobleme nam konstanta $a$ pove koliko vej se obravnava.
- Idealno je $a \leq b$. *Lahko se  zgodi da katero vejo obravnavamo večkrat v katerem primeru je $a \ge b$*
  
> Primer je dvojiško iskanje kjer vzamemo vhod $n$, ga damo na dva dela velikost $\frac{n}{2} \Rightarrow b=2$. Vzamemo pa le enega torej $a = 1$.

- prištejemo še $f(n)$ kot strošek kakšrnih koli drugih operacij zunaj rekurzivnega klica

> Pri dvojiškem iskanju je na primer potrebna primerjava sredinskega elementa z iskanim elementom kar je $O(1)$.



- Splošna oblika rekurzije bo torej
  $$T(n) = a \cdot T\left(\frac{n}{b}\right) + f(n)$$

- Na vrhu imamo en problem velikosti $n$ s stroškom $f(n)$.
  Na nivoju 1 imamo $a$ podproblemov velikosti $n/b$, skupni strošek je $a \cdot f(n/b)$.
- Na nivoju $i$ imamo $a^{i}$ podproblemov velikosti $n/b^{i}$ skupni strošek je $a^{i} \cdot f(n/b^{i})$
<br>
- Višina drevesa je $\log_{b}{n}$ torej bo število listov v drevesu $a^{\log_{b}{n}}$ ta izraz lahko preoblikujemo v $n^{\log_{b}{a}}$ kar predstavlja skupno delo v listih - osnovnih delih rekurzije. Temu pravimo tudi **kritična funkcija**.
<br>
- Bistvo izreka je da primerjamo kritično funkcijo z delom v vozliščih - $f(n)$.
<br>
- Če funkcija $f(n)$ raste **polinomsko počasneje** kot $n^{\log_{b}{a}}$ potem večino dela opravijo listi.
- Velja $f(n) = O(n^{\log_{b}{a}-C})$ za nek $C > 0$ in **$T(n) = \Theta(n^{\log_{b}{a}})$**.
  *Ker se delo z vsakim nivojem rekurzije eksponentno povečuje, je celotna vsota asimptotično določena z zadnjim nivojem (listi).*
  <br>
- Če funkcija $f(n)$ raste **asimptotično** enako kot $n^{\log_{b}{a}}$ potem je opravljeno delo približno enako.
- Velja $f(n) = \Theta(n^{\log_{b}{a}})$ in **$T(n) = \Theta(n^{\log_{b}{a}} \log_{}{n})$**.
  *Na vsakem nivoju drevesa opravimo približno enako količino dela. Ker je nivojev $\log_b n$, skupno delo pomnožimo s tem faktorjem.*
<br>
- Če funkcija $f(n)$ raste **polinomsko hitreje** kot $n^{\log_b a}$, potem se večina dela opravi na vrhu drevesa (v trenutnem vozlišču).
- Velja $f(n) = \Omega(n^{\log_b a + C})$ za nek $C > 0$ **in** izpolnjen mora biti pogoj regularnosti: $a f(n/b) \le c f(n)$ za nek $c < 1$ in dovolj velik $n$. Tako pride **$T(n) = \Theta(f(n))$**.
  *Delo se z globino rekurzije tako hitro zmanjšuje, da je vsota vseh nivojev asimptotično določena s stroškom prvega koraka (koren drevesa).*

<BR>
- V splošnem označimo $\log_{b}{a} = c$.

***

Namesto oblike drevesa se sedaj osredotočimo na različne funkcije $f(n)$ pri običajnih konstantah $b=2, a=2$.

- Predpostavimo da je $f(n) = \log n$ 
V korenu imamo $\log n$ dela, v obeh otrocih $\log n/2$, ... 
Naj bo $L=\log n$. 
Skupno delo je 
$$\sum_{i=0}^{\log_{b}{n}}a^{i}f\left(\frac{n}{b^{i}}\right)$$
$$\sum_{i=0}^L 2^i \log(n/2^i) = \sum_{i=0}^L 2^i (L - i)$$
$$\sum_{i=0}^L 2^i \log(n/2^i) = \sum_{i=0}^L 2^i (L - i)$$  

Z nekaj matematične spretnosti (odvod delnih vsot geometrijske vrste) to poenostavimo v $2^{L+1} -L -2 = 2n - \log n - 2 = O(n)$. Tu prevladuje velikost rekurzivnega drevesa.
- $f(n) = n: \quad$ Tega že poznamo. Imamo $\log n$ nivojev in na vsakem nivoju $n$ dela, skupaj torej $O(n \log n)$.
- $f(n) = n^2: \quad$ V korenu imamo $n^2$ dela, v otrocih $2(n/2)^2 = 1/2 n^2$, v vnukih $4(n/4)^2 = 1/4 n^2$. Vsota je $O(n^2)$, ker prevladuje delo v korenu.


---

Oglejmo si nekaj primerov uporabe krovnega izreka pri razpolavljanju z $b=2$:

- $a=2, f(n)=1$ (rekurzivno seštevanje): $\quad c=1$, velja 1. primer, zato je $T(n) = O(n)$
- $a=2, f(n)=\log n$: $\quad c=1$, velja 1. primer, zato je $T(n) = O(n)$
- $a=3, f(n)=n$ (Karatsuba): $\quad c \approx 1.6$, velja 1. primer, zato je $T(n) = O(n^{1.6})$.
- $a=1, f(n)=1$ (dvojiško iskanje): $\quad c=0$, velja 2. primer, zato je $T(n) = O(\log n)$.
- $a=2, f(n)=n$ (quick/merge sort): $\quad c=1$, velja 2. primer, zato je $T(n) = O(n \log n)$.
- $a=2, f(n)=2^n$: $\quad c=1$, velja 3. primer, zato je $T(n) = 2^n$.

Primeri, kjer si ne moremo pomagati s krovnim izrekom:

- $T(n) = 1/2\,T(n/4) + n:\quad$ $a < 1$ nima smisla, rešujemo pol problema velikosti $n/4$?
- $T(n) = 2\,T(n/1) + n:\quad$ $b = 1$, zato se problem sploh ne zmanjšuje.
- $T(n) = 3\,T(n/2) − n^2:\quad$ Delo $f(n)$ ne more biti negativno.
- $T(n) = n/2\,T(n/2) + n:\quad$ $a=n/2$ ni konstanta.
- $T(n) = 2\,T(n/2) + n/\log\log{n}:\quad$ Tega ne pokriva noben izmed treh primerov ($n/\log\log{n} \neq O(n^{0.999\ldots})$, da bi veljal prvi primer).

Posplošitev krovnega izreka na primere, kjer imamo opravka s podproblemi različnih velikosti (niso vsi enako veliki $n/b$), je znana kot Akra-Bazzi metoda.

## Primeri nalog

Sedaj smo opremljeni s teorijo pristopa deli in vladaj, ki jo v nadaljevanju poskusimo uporabiti na nekaj primerih.

```cpp
#include <iostream>
#include <vector>
using namespace std;
```

```cpp
template<typename T>
void print(const vector<T> &s) {
    for (T x : s) cout << x << " ";
    cout << endl;
}
```

### Potenciranje

Izračunati želimo potenco $x^n$. Pri tem predpostavimo, da lahko množimo poljubno velika števila v konstantnem času (kar seveda ni res). Ali pa izračunajmo rešitev po nekem modulu $M$ (v kolobarju ostankov), kjer lahko pri seštevanju in množenju sproti računamo z ostanki.

Če je $n$ sod, bi nam prišla prav potenca $p = x^{n/2}$. Iskani rezultat je ravno $p^2$. Če pa je $n$ lih, mu odštejemo 1 (in množimo rezultat z $n$) ter tako pridemo do sodega primera. Obakrat smo s konstantnim številom operacij razpolovili velikost problema, zato je časovna zahtevnost $O(\log n)$, za kar nam niti ni treba komplicirati s krovnim izrekom. Postopek se imenuje **potenciranje s kvadriranjem** (*exponentiation by squaring*).

```cpp
int potenca(int x, int n) {
    if (n==0) return 1;
    if (n%2==0) {
        //return potenca(x, n/2) * potenca(x, n/2);  // narobe! ... O(n)
        int p = potenca(x, n/2);
        return p*p;
    } else {
        return x*potenca(x, n-1);
    }
}
```

```cpp
cout << potenca(2,10) << endl;
```

Pozorni moramo biti, da ne računamo vrednosti `potenca(x, n/2)` dvakrat. V tem primeru bi bila časovna zahtevnost $O(n)$, kar ni nič boljše od zaporednega množenja. Vrednost izračunamo enkrat in jo nato kvadriramo.

### Enakomerno razbitje seznama

Podan imamo seznam $n$ števil $a_1, a_2, \ldots, a_n$ z vsoto $V=\sum_1^n a_i$, ki ga želimo razbiti na $k$ strnjenih podseznamov (ki so lahko tudi prazni). Želimo si, da je razbitje tako, da so si vsote podseznamov čim bolj podobne. Idealno bi bilo, če bi imel vsak podseznam vsoto $V/k$, vendar to ni vedno mogoče. Odločili smo se, da bomo to dosegli tako, da bomo zahtevali, da je največja vsota $v$ posameznega podseznama čim manjša (minimiziramo maksimalno vsoto). Kakšno je optimalno razbitje?

Za primer vzemimo seznam `12, 8, 3, 5, 4, 13, 5, 3, 7` in $k=3$. Vsota je 60, zato bi bilo idealno, če bi naredili skupine po 20. Prva dva elementa se ravno seštejeta v 20, zato bi ju bilo smiselno dati v svojo skupino. Potem nam ostane še dilema glede meje med drugo in tretjo skupino, kjer lahko preizkusimo obe meji okoli vsote 20. Smo s tem požrešnim razmislekom prišli do optimalne rešitve? Nismo. Prvo skupino se splača podaljšati, da pride do lepše delitve med drugo in tretjo. Optimalno razbitje je `(12, 8, 3), (5, 4, 13), (5, 3, 7)`, kjer so vsote 23, 22 in 15.

Pogosto so odločitveni problemi lažji od optimizacijskih. Je neka konkretna meja $v$ sprejemljiva? Ali obstaja razbitje na $k$ kosov, katerih vsota ne presega $v$? Večja kot je meja za vsoto, lažji je problem. Če obstaja razbitje z mejno vsoto $v$, obstaja tudi pri meji $v+1$ (veljavno je isto razbitje). In obratno, če pri meji $v$ ne obstaja, potem ne obstaja tudi pri $v-1$. Iščemo mejo med situacijama, kjer razbijte še obstaja in kjer ne. To lahko poiščemo z dvojiškim iskanjem. Pravzaprav delamo dvojiško iskanje po možnih rešitvah $v$ in preverjamo, ali so sprejemljive.

Kako ugotovimo, ali obstaja veljavno razbitje pri neki mejni vsoti $v$? Poiskali bomo razbitje s čim manj kosi, ki ne presegajo vsote $v$ (vedno lahko dodamo kakšnega praznega, da jih bo točno $k$). Tega se lahko lotimo na požrešen način. Prvi kos naj bo največja predpona seznama, ki še ne preseže vsote $v$. To bo vedno vodilo do neke optimalne rešitve. Recimo, da ne bi, in bi moral biti prvi kos krajši (daljši očitno ne more biti). Potem bi lahko v tej predpostavljeni optimalni rešitvi premaknili nekaj elementov iz drugega kosa v prvega. Vemo, da je v prvem kosu še prostor, z zmanjševanjem drugega kosa pa tudi ne pokvarimo rešitve. Požrešno strategijo lahko torej uporabimo za določanje vsakega kosa znova. Če s tem nismo presegli $k$ kosov, je mejna vsota $v$ sprejemljiva, sicer pa ne.

Razmislimo še o časovni zahtevnosti opisanega postopka. Za dvojiško iskanje meje $v$ bomo potrebovali $O(\log V)$ korakov. Za določanje sprejemljivosti posamezne meje pa $O(n)$. To je skupaj $O(n \log V)$. Če imamo podano omejitev velikosti posameznih števil v seznamu, npr. $a_i \leq m$, je $V \leq nm$ in lahko časovno zahtevnost zapišemo kot $O(n \log(nm)) = O(n(\log n + \log m))$.

```cpp
int partition(vector<int> a, int k) {
    int total=0, largest=0;
    for (int x : a) {
        total+=x;
        largest = max(largest, x);
    }
    int lo=largest-1, hi=total;  // lo=infeasible, hi=feasible
    while (lo+1<hi) {
        int lim=(lo+hi)/2;
        int sum=0, chunks=1;
        for (int x : a) {
            if (sum+x<=lim) sum+=x;  // extend last chunk
            else { chunks++; sum=x; }  // start new chunk
        }
        if (chunks<=k) hi=lim;
        else lo=lim;
    }
    return hi;
}
```

```cpp
vector<int> a={12,8,3,5,4,13,5,3,7};
cout << partition(a, 3) << endl;
for (int k=1;k<=a.size();k++) {
    cout << k << ": " << partition(a, k) << endl;
}
```

### K-ti element

V problemu izbire k-tega elementa (*selection problem*) imamo podan (neurejen) seznam $n$ števil $a_1, a_2, \ldots, a_n$. Zanima nas, katero število je $k$-to po velikosti oz. bi bilo na $k$-tem mestu, če bi seznam uredili.

Seznam lahko uredimo in preverimo, kateri element konča na $k$-tem mestu. Časovna zahtevnost je odvisna od časa urejanja in je v splošnem $O(n \log n)$. Smo lahko kaj bolj učinkoviti? Vsakakor moramo preveriti vseh $n$ elementov, morda pa lahko izboljšamo faktor $\log n$.

Lahko bi vzdrževali samo seznam najmanjših $k$ elementov. Če je $k$ bistveno manjši od $n$-ja, bi bila taka rešitev bolj učinkovita. Trenutno najmanjše elemente bi namesto v seznamu hranili urejene v max-kopici. Vsakič bi v kopico dodali nov element in izločili največjega iz kopice, ter tako vzdrževali najmanjših $k$ elementov. Ker velikost kopice ne bi presegla $k$, bi bila časovna zahtevnost $O(n \log k)$.

Še hitrejša rešitev uporablja podoben prostopa kot pri hitrem urejanju (*quick sort*). Zato se algoritmu, ki ga bomo opisali, reče **hitro izbiranje** (*quick select*). Izbrali bomo delilni element (*pivot*) in razdelili števila na manjša (ali enaka) in večja. Naj bo manjših števil $m$. Če je $k<=m$, moramo $k$-tega iskati med manjšimi. Sicer pa moramo med večjimi poiskati $(k-m)$-tega.

Ob predpostavki, da nam seznami razpadajo na prbiližno enako velike skupine, bo pričakovana časovna zahtevnost $O(n + n/2 + n/4 + \ldots) = O(n)$. S tem se strinja tudi krovni izrek pri $b=2, a=1, f(n)=n$ (3. primer).

V C++ je ta funkcionalnost že na voljo kot funkcija `nth_element` iz knjižnice `algorithm`, ki delno uredi seznam tako, da je n-ti element na pravem mestu, pred njim so samo manjši ali enaki elementi, za njim pa večji ali enaki.

```cpp
vector<int> v = {3,5,2,8,1,10,2,3,8,5,1};
nth_element(v.begin(), v.begin()+4, v.end());
print(v);
sort(v.begin(),v.end());
print(v);
```

### Štetje inverzij

V seznamu $n$ števil $a_1, a_2, \ldots, a_n$ je inverzija par indeksov $i$ in $j$ ($i<j$), za kateri velja, da sta pripadajoči števili v seznamu narobe urejeni ($a_i > a_j$). Zanima nas, koliko inverzij vsebuje podani seznam? Seveda lahko preverimo vse pare indeksov, vendar ima to kvadratno časovno zahtevnost. 

Prilagodili bomo algoritem urejanja z zlivanjem (merge sort). Poleg urejanja podseznamov naj funkcija izračuna še število inverzij v njem (pred urejanjem). Recimo, da smo seznam razbili na levo in desno polovico, ter rekurzivno rešili manjša problema. S tem smo dobili število inverzij v levi polovici in urejeno levo polovico, ter enako za desno polovico. Urejeni polovici znamo zliti v urejeno celoto. Kaj pa inverzije?

Inverzije v levi in desni polovici seštejemo, vendar nam manjkajo še tiste inverzije, kjer je eno število v levi, drugo pa v desni polovici. Za vsako število $x$ iz leve polovice bomo izračunali število inverzij, v katerih nastopa - koliko je v desni polovici manjših števil od $x$? To lahko učinkovito izračunamo med zlivanjem obeh polovic. Recimo, da smo že zlili $l$ števil iz leve polovice in $d$ iz desne ter je naslednje na vrsti število $x$ iz leve polovice. Pred njim je v zlitem urejenem seznamu že $d$ manjših števil iz desne polovice, s katerimi je formiral inverzije in jih prištejemo k rezultatu.

### Podseznam z največjo vsoto

Podan imamo seznam oz. tabelo $A$ z $n$ pozitivnimi in negativnimi števili. Zanima nas, kakšna je največja vsota strnjenega podseznama v njem $A_i + A_{i+1} + ... + A_j$ (*maximum subarray problem*). Za ta problem poznamo tudi druge (enostavnejše) rešitve, vendar si oglejmo pristop s tehniko deli in vladaj.

Seznam razbijemo na levo in desno polovico. Za vsak del izračunamo odgovor - največjo vsoto podseznama v njem. Če bi kot rezultat vzeli večjega od njiju, bi zgrešili rešitve, ki se raztezajo čez sredinsko mejo med polovicama. Poleg izračunanih rezultatov za podseznama moramo torej upoštevati tudi rezultate, ki vključujejo dele obeh polovic. Preverimo lahko vsote vseh možnih parov pripon leve polovice in predpon desne polovice. Časovna zahtevnost bo $O(n^2)$, v kar se lahko prepričate s krovnim izrekom ($a=2, b=2, c=\log_b a=1, f(n)=n^2$) ali z malo analize. To je enako slabo kot rešitev s preiskovanjem vseh možnih strnjenih podseznamov.

Z malo razmisleka lahko enostavno zmanjšamo število preverjenih parov pripon in predpon. Edina relevantna pripona leve polovice bo namreč tista z največjo vsoto. Enako velja za predpono desne polovice. To lahko poiščemo v linearnem času ($f(n)=n$), s čimer dobimo rešitev s časovno zahtevnostjo $O(n\log n)$.

Tudi to lahko še izboljšamo. Namesto, da vsakič znova računamo najboljšo pripono in predpono, lahko to vrednost vrne rešitev podproblema. Problem torej nekoliko **razširimo** in zahtevamo, da algoritem za dani podproblem vrne največjo strnjeno vsoto ($\text{sol}$), največjo predpono ($\text{pre}$) in največo pripono ($\text{suf}$). Za učinkovito računanje največjih predpon in pripon nam bo prav prišla tudi vsota celotnega seznama ($\text{sum}$).

- $\text{sol} = \max(\text{sol}_L, \text{sol}_R, \text{suf}_L+\text{pre}_R)$
- $\text{pre} = \max(\text{pre}_L, \text{sum}_L+\text{pre}_R)$
- $\text{suf} = \max(\text{suf}_R, \text{suf}_L+\text{sum}_R)$
- $\text{sum} = \text{sum}_L + \text{sum}_R$

Tako lahko rešitve podproblemov združimo v konstantnem času $f(n)=1$. Časovna zahtevnost je zato samo še $O(n)$.

```cpp
struct Result {
	int max, prefix, suffix, sum;
};
```

```cpp
Result max_array(vector<int> a) {
    int n=a.size();
    if (n==1) return (Result){max(a[0],0),max(a[0],0),max(a[0],0),a[0]};
    vector<int> left(a.begin(),a.begin()+n/2);
    vector<int> right(a.begin()+n/2,a.end());
    Result resL = max_array(left);
    Result resR = max_array(right);
    Result res;
    res.max = max({resL.max, resR.max, resL.suffix+resR.prefix});
    res.prefix = max(resL.prefix, resL.sum+resR.prefix);
    res.suffix = max(resR.suffix, resL.suffix+resR.sum);
    res.sum = resL.sum + resR.sum;
    return res;
}
```

```cpp
vector<int> a = {2,-1,-2,3,7,-2,1,5,-6,4};
Result res = max_array(a);
cout << res.max << endl;
```

Za konec še dve razširitvi problema v razmislek:

- Kako bi dopolnili rešitev, da bi vrnila tudi indeksa $i$ in $j$, ki definirata podseznam z največjo vsoto?
- Kako bi omogočili učinkovito spreminjanje posameznih vrednosti v tabeli in ob vsaki spremembi vrnili iskano največjo vsoto?