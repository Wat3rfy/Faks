Tukaj je transkripcija vaše Jupyter beležnice v Markdown format s pravilno oblikovanimi LaTeX matematičnimi izrazi in C++ kodo.

---

# Požrešni algoritmi

Pogosto lahko sestavimo rešitev nekega problema z zaporedjem korakov, pri čemer se na vsakem koraku odločimo za eno izmed več možnih izbir. Pri požrešnem (*greedy*) pristopu reševanja se na vsakem koraku odločimo za izbiro, ki v tistem trenutku izgleda najbolj obetavno. S takim načinom bomo najbrž našli kar spodobno rešitev, pa bo ta tudi optimalna? Odvisno od problema, zato moramo znati razlikovati, kje in zakaj take strategije delujejo in kdaj ne. 

Recimo, da želimo na spodnjem zemljevidu priti iz levega zgornjega vogala v desni spodnji vogal s čim manj premiki. Na zemljevidu znaki `.` predstavljajo prosta polja, znaki `#` pa zasedena. Očitno bomo gradili rešitev postopno po premikih. Na vsakem koraku se bomo odločili za eno izmed največ 3 možnih smeri (ne bomo se premikali nazaj, od koder smo prišli). Smiselna mera obetavnosti premika je razdalja sosednjega polja od cilja. Prvo dilemo imamo na polju (3,3), kjer bolje izgleda premik navzdol, kar nas premakne bližje k cilju, kot premik navzgor. Vendar nas to vodi do slabše rešitve zaradi kasnejših komplikacij na poti, ki jih v trenutku požrešne izbire ne upoštevamo. Ni si težko zamisliti tudi primera, kjer taka izbira sploh ne bi vodila do rešitve.

```text
.#..#.
.#....
...#..
##.#.#
...#.#
.###..
.#....
...##.
```

V nadaljevanju si bomo ogledali več primerov problemov ter dokazov (ne)pravilnosti požrešnih strategij za njihovo reševanje, s čimer boste razvili nekaj intuicije in zdrave skeptičnosti glede uporabe požrešnih strategij. S požrešnimi strategijami se bomo ponovno srečali tudi kasneje pri algoritmih na grafih (Dijkstra, Prim, Kruskal). Požrešne strategije se običajno dobro obnesejo na enostavnih problemih, medtem ko na kompleksnejših z njimi dobimo neko suboptimalno oz. nepravilno rešitev. Posebej zanimivi pa so primeri, kjer nas v navidez kompleksnih problemih pripeljejo požrešne rešitve do optimalnega rezultata.

```cpp
#include <cstdio>
#include <iostream>
#include <vector>
#include <algorithm>
#include <queue>
using namespace std;

typedef pair<int,int> PII;
typedef vector<pair<int,int>> VII;
typedef vector<vector<pair<int,int>>> VVP;
```

## Bencinske črpalke

Začnimo s potovalnim problemom polnjenja avta na bencinskih črpalkah (*car fueling*). Z avtom želimo potovati do $K$ kilometrov oddaljenega cilja. Pri tem vemo, da se vzdolž poti nahaja $N$ črpalk, ki so od našega izhodišča oddaljene $0 < x_1 < x_2 < \dots < x_n < K$ kilometrov. Velikost posode za gorivo oz. doseg našega avta s polnim tankom je $T$ kilometrov (z delno polnim pa sorazmerno manj). Pot bomo začeli s polnim tankom goriva. Je cilj sploh dosegljiv? Kakšno je najmanjše število postankov na črpalkah, da prisemo na cilj?

Primer: $K = 950, T = 400, x = [200, 375, 550, 750, 950]$.

Ugotovitve:
- Na črpalki je vedno smiselno povsem napolniti tank z gorivom. Če ga ne bi napolnili do vrha, bi lahko z bolj polnim tankom opravili enako pot do naslednje črpalke. Morebiten ostanek goriva pa "zlili stran" oz. tam dotočili temu primerno manj.
- Dosegljivost lahko preverimo tako, da tankamo na vsaki črpalki.
- Če je mogoče doseči naslednjo črpalko (ali cilj), lahko preskočimo tankanje na trenutni črpalki. Na naslednji črpalki lahko namreč dotočimo gorivo do nivoja, ki bi ga imeli, če bi natočili gorivo na trenutni.

```cpp
int crpalke(int K, int T, vector<int> x) {
    x.insert(x.begin(), 0);
    x.insert(x.end(), K);
    int doseg=T, postanki=0;
    for (int i=0;i+1<x.size();i++) {
        int razdalja=x[i+1]-x[i];
        if (doseg<razdalja) { postanki++; doseg=T; }  // po potrebi napolni
        if (doseg<razdalja) return -1;  // tudi s polnim tankom ne gre
        doseg-=razdalja;
    }
    return postanki;
}
```

Da si poenostavimo implementacijo bomo dodali začetek in konec poti kot dve dodatni črpalki. Nato se premikamo med sosednjimi črpalkami v skladu s prejšnjimi ugotovitvami. Preverimo rešitev na začetnem primeru in par drugih posebnih situacijah, kjer ne rabimo dolivati goriva, ga dolivamo povsod ali je nemogoče doseči cilj.

```cpp
cout << crpalke(950, 400, {200,375,550,750}) << endl;
cout << crpalke(950, 950, {200,375,550,750}) << endl;
cout << crpalke(950, 200, {200,375,550,750}) << endl;
cout << crpalke(950, 199, {200,375,550,750}) << endl;
```

Bolj formalno bi lahko dokazali, da je tak postopek pravilen z argumentom, da je požrešna rešitev ves čas v "prednosti" pred optimalno rešitvijo. Naj bodo $s_i$ postanki, ki jih naredi požrešna rešitev, $t_i$ pa postanki optimalne rešitve. Dokazali bo radi, da pride požrešna rešitev s $k$ koraki dlje (oz. enako daleč) kot optimalna, torej da velja $s_i \geq t_i$ za vse $i$. Recimo, da to ne bi bilo res in bi prišlo do razlike na indeksu $i$ ($s_j=t_j$ za $j<i$ in $s_i < t_i$). V obeh primerih je bil predzadnji postanek na mestu $s_{i-1} = t_{i-1}$. Požrešna rešitev pa se od tam premakne najdlje, kar je možno, torej je $s_i \geq t_i$. Požrešna rešitev s $k$ postanki torej pride vsaj tako daleč kot optimalna s $k$ postanki. To pa pomeni, da ima požrešna rešitev najmanjše število postankov, da pride do konca. Če bi obstajala optimalna rešitev, ki pride do konca z manj koraki, smo pokazali, da bi obstajala tudi požrešna, ki pride do konca z enakim številom korakov.

## Izbira aktivnosti

Izbira med seboj neodvisnih aktivnosti iz nabora ponujenih (*activity selection*) je klasičen problem. Podanih imamo $N$ aktivnosti, kjer se $i$-ta aktivnost $a_i$ izvaja v obdobju $(s_i, e_i)$. Izbrati moramo čim večjo podmnožico aktivnosti, za katero velja, da je presek poljubnih dveh aktivnosti prazen. Ker lahko aktivnosti predstavimo z daljicami, je problem znan tudi kot *interval scheduling*.

Primer: $[(1,3), (2,4), (2,5), (4,5), (4,7), (6,7), (6,8), (7,12), (8,12), (9,10), (9,11), (11,12), (12,13)]$

![aktivnosti](daljice.png)

Hitro pridemo na več idej, kako bi se lahko lotili problema brez preverjanja vseh podmnožic. Katere od njih pa so res pravilne?

- **najzgodnejši začetek** (*earliest start*)
  Ne izgubljajmo časa s čakanjem! Razpored aktivnosti lahko sestavljamo po korakih tako, da vsakič dodamo aktivnost, ki se začne prva po zaključku trenutnega razporeda. 
  Protiprimer: $[(1,6), (2,3), (4,5)]$
  ![start](start.png)

- **najkrajši** (*shortest*)
  Dolge aktivnosti zasedejo veliko časa, zato začnimo z majhnimi! Razpored sestavljamo tako, da vanj dodajamo aktivnosti od krajših proti večjim. 
  Protiprimer: $[(4,7), (1,5), (6,10)]$
  ![shortest](shortest.png)

- **najmanj konflikten** (*fewest conflicts*)
  Težave so s konflikti med aktivnostmi, zato začnimo z najmanj konfliktnimi! 
  Protiprimer: $[(6,9), (1,3), (4,7), (8,11), (12,14), (2,5), (2,5), (2,5), (10,13), (10,13), (10,13)]$. Prvi interval ima samo dva konflikta, vendar njegova izbira vodi v rešitev s tremi intervali, primer pa lahko rešimo s štirimi.
  ![conflicts](conflicts.png)

- **najzgodnejši konec** (*earliest finish*)
  Čim prej zaključimo s prvo aktivnostjo, da bomo imeli čim več časa za ostale! Med vsemi aktivnostmi, ki se začnejo ob ali po koncu trenutno zadnje izberemo tisto z najzgodnejšim koncem.

  Dokažimo, da je pravilno. Recimo, da obstaja boljša optimalna rešitev, ki se na začetku strinja s požrešno, pri $i$-ti aktivnosti v izbranem razporedu pa pride prvič do razlike. Optimalna izbere aktivnost $o$, požrešna pa $p$. Ker požrešna vedno izbere aktivnost z najzgodnejšim koncem, velja $e_p \leq e_o$. Zato se aktivnost $p$ ne more pojaviti kje kasneje v predpostavljeni optimalni razporeditvi. Obe aktivnosti nista konfliktni s predhodnimi. Če v optimalnem razporedu zamenjamo aktivnost $o$ z $p$, bo preostanek razporeda ostal veljaven, rešitev pa ne bo nič slabša. Tako smo podaljšali del optimalne rešitve, ki se se strinja s požrešno, ne da bi jo kako poslabšali. Če ta razmislek ponovimo večkrat, bomo predpostavljeno optimalno rešitev lahko predelali v požrešno brez poslabšanja rezultata.

```cpp
VII aktivnosti(VII a) {
    VII razpored;
    int konec=0;
    while (1) {
        int j=-1;
        for (int i=0;i<a.size();i++) {
            if (konec<=a[i].first) {  // relevanten?
                if (j==-1 || a[i].second<a[j].second) j=i;  // boljsi?
            }
        }
        if (j==-1) break;
        razpored.push_back(a[j]);
        konec=a[j].second;
        a.erase(a.begin()+j);
    }
    return razpored;
}
```

Lahko to naredimo bolj učinkovito? Aktivnosti uredimo po njihovih koncih in jih izbiramo po vrsti, če se začetek ne seka s koncem trenutno zadnje aktivnosti. Časovna zahtevnost je tako samo $O(n \log n)$.

```cpp
bool cmpSecond(pair<int,int> a, pair<int,int> b) {
    return a.second < b.second;
}

VII aktivnosti_fast(VII a) {
    sort(a.begin(), a.end(), cmpSecond);
    VII razpored;
    int konec=0;
    for (auto [s,e] : a) {
        if (konec<=s) {
            razpored.push_back({s,e});
            konec = e;
        }
    }
    return razpored;
}
```

Kaj pa utežena različica problema, kjer ima vsaka aktivnost poleg začetka in konca tudi svojo pomembnost? To se izkaže za težji problem, h kateremu se bomo vrnili pri tehniki dinamičnega programiranja.

## Rezervacije učilnic

Pri problemu rezervacije učilnic (*classroom scheduling, interval partitioning*) moramo na fakulteti izvesti $N$ predavanj $(s_i, e_i)$. Kakšno je najmanjše število predavalnic, ki jih potrebujemo?

Če v kakšnem trenutku sočasno poteka več predavanj, bomo zagotovo potrebovali vsaj toliko predavalnic. Največjemu številu sočasnih predavanj bomo rekli globina (*depth*), ki predstavlja spodnjo mejo rešitve.

S požrešnim algoritmom bomo predavanja po vrsti glede na njihov začetek razporejali v predavalnice. Na vsakem koraku preverimo, ali je kakšna od predavalnic že prosta. Če take predavalnice ni, odpremo novo predavalnico.

Dokažimo, da prej opisani postopek doseže ravno globino. Recimo, da postopek potrebuje $d$ predavalnic. Do tega pride, ko želimo nekam razporediti predavanje $i$ z začetkom ob času $t=s_i$, vendar so vse ostale predavalnice še zasedene. To pomeni, da imamo $d-1$ predavanj, ki se zaključijo po času $t$. Vsa ta predavanja so se začela prej ali takrat kot $i$-to. V trenutku $t+\epsilon$ torej poteka sočasno $d$ predavanj.

```cpp
VVP predavalnice(VII predavanja) {
    sort(predavanja.begin(), predavanja.end());
    VVP urnik;
    for (auto p : predavanja) {
        auto [s,e] = p;
        int x=-1;
        for (int i=0;i<urnik.size();i++) {
            if (urnik[i].back().second<=s) { x=i; break; }
        }
        if (x==-1) urnik.push_back({p});
        else urnik[x].push_back(p);
    }
    return urnik;
}
```

Časovna zahtevnost zgornje implementacije je $O(N^2)$. To lahko izboljšamo na $O(N \log N)$, če predavalnice hranimo v prioritetni vrsti glede na čas zaključka zadnjega predavanja.

```cpp
VVP predavalnice_fast(VII predavanja) {
    sort(predavanja.begin(), predavanja.end());
    VVP urnik;
    priority_queue<PII, VII, greater<PII>> pq;
    for (auto p : predavanja) {
        auto [s,e] = p;
        if (!pq.empty() && pq.top().first <= s) {
            int x = pq.top().second;
            pq.pop();
            urnik[x].push_back(p);
            pq.push({e, x});
        } else {
            pq.push({e, (int)urnik.size()});
            urnik.push_back({p});
        }
    }
    return urnik;
}
```

## Datoteke na traku

Podanih imamo $N$ datotek $d_i = (s_i, f_i)$, kjer je $s_i$ velikost datoteke, $f_i$ pa pogostost dostopa. Ceno zapisa ocenimo z $\sum_i x_i f_i$, kjer je $x_i$ začetno mesto zapisa. Kakšen je optimalen razpored?

Primer: $d = [(60,5), (27,3), (1,20), (32,4)]$

Obravnavajmo sosednji datoteki $i$ in $j$. Ceni dostopa sta $x f_i + (x+s_i) f_j$ (če je $i$ pred $j$) in $x f_j + (x+s_j) f_i$ (če je $j$ pred $i$). Cena ureditve $i$ pred $j$ je manjša, ko velja:
$$x f_i + x f_j + s_i f_j \leq x f_j + x f_i + s_j f_i$$
$$s_i f_j \leq s_j f_i$$
$$\frac{s_i}{f_i} \leq \frac{s_j}{f_j}$$

V optimalnem vrstnem redu morajo biti datoteke urejene naraščajoče glede na razmerje $s_i/f_i$.

```cpp
bool cmpRatio(pair<int,int> a, pair<int,int> b) {
    return (long long)a.first * b.second < (long long)b.first * a.second;
}

int trak(vector<pair<int,int>> d) {
    sort(d.begin(), d.end(), cmpRatio);
    int x=0, sc=0;
    for (auto [s,f] : d) { sc+=x*f; x+=s; }
    return sc;
}
```

## Minimizacija zamude

Vsako opravilo je opisano s parom $o_i = (t_i, d_i)$ (čas izvajanja in rok). Če se opravilo konča ob času $f_i$, je zamuda $z_i = \max(0, f_i-d_i)$. Minimiziramo $Z = \max z_i$.

Strategija: **najzgodnejši rok** (*earliest deadline*). Opravila izvajamo glede na rok $d_i$.

Dokažimo z zamenjavo: Recimo, da v optimalni rešitvi obstajata sosednji opravili $j$ in $i$, kjer $d_j > d_i$. Ob njuni zamenjavi se zamuda opravila $i$ zmanjša. Za opravilo $j$ pa velja:
$$z'_j = f'_j - d_j = f_i - d_j \leq f_i - d_i = z_i$$
Ker sta zamudi po zamenjavi manjši ali enaki prvotni zamudi $z_i$, se maksimalna zamuda ne poveča.

```cpp
int zamuda(VII o) {
    sort(o.begin(), o.end(), cmpSecond); // cmp po d_i
    int Z=0, now=0;
    for (auto [t,d] : o) {
        now+=t;
        Z = max(Z, max(0, now-d));
    }
    return Z;
}
```

## Dokazovanje pravilnosti

#### Prednost (*stay ahead*)
Dokažemo, da je po vsakem koraku rešitev požrešne strategije vsaj tako dobra kot katerakoli druga (npr. bencinske črpalke).

#### Zamenjava (*exchange argument*)
Dokažemo, da lahko poljubno optimalno rešitev brez poslabšanja rezultata preoblikujemo v požrešno rešitev (npr. izbira aktivnosti, datoteke na traku).

#### Struktura (*structural argument*)
Dokažemo strukturno lastnost optimalne rešitve (npr. globino) in pokažemo, da jo požrešna rešitev doseže (npr. rezervacija učilnic).

## Menjava kovancev

Blagajniki uporabljajo požrešno strategijo: uporabi največji kovanec, ki ne presega preostale vrednosti. Za evrski nabor kovancev je to optimalno. Za poljuben nabor pa ni nujno (npr. vrednost 6 s kovanci $[1, 3, 4]$: požrešno $4+1+1$, optimalno $3+3$).

Naj bo $S$ najmanjši protiprimer.
- Optimalna rešitev ne uporabi največjega kovanca $a_n$ (sicer bi bil $S-a_n$ manjši protiprimer).
- Optimalna rešitev uporabi kovanec $a_i$ manj kot $a_n$-krat.

Največja vrednost, kjer se optimalna lahko razlikuje od požrešne, je omejena z $U = (a_1 + \dots + a_{n-1})(a_n - 1)$. Če požrešna strategija deluje za vse vrednosti do $U$, potem je optimalna za vsa števila.