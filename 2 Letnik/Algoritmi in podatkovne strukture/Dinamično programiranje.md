Tukaj je transkripcija vsebine v formatu LaTeX Markdown.

# Dinamično programiranje

Dinamično programiranje je algoritmičen pristop, ki je podoben pristopu deli in vladaj. Tudi pri uporabi dinamičnega programiranja bomo razbili problem na manjše podprobleme, poiskali optimalne rešitve podproblemov in si z njimi pomagali pri rešitvi začetnega problema. Pomembne lastnosti problema, pri katerem si lahko pomagamo z dinamičnim programiranjem so:

- **neodvisnost podproblemov**: Posamezen podproblem lahko rešujemo neodvisno od drugih podproblemov.
- **optimalna podstruktura**: Optimalna rešitev problema vsebuje optimalne rešitve podproblemov.
- **prekrivanje/ponavljanje podproblemov**: To je glavna lastnost, ki jo bomo izkoristili za izboljšave in v čemer se pristop razlikuje od tehnike deli in vladaj.

Tehniko lahko enostavno povzamemo z nasvetom "ne računaj enakih stvari večkrat", v praksi pa je kljub temu nekoliko bolj zapleteno - kako to doseči, katere stvari sploh so enake, ...

Pristop nima nobene veze z dinamično alokacijo pomnilnika. Poimenoval ga je njen avtor Richard Bellman. "Programiranje" se nanaša na reševanje optimizacijskega problema, podobno kot matematično programiranje/optimizacija. Pridevnik "dinamično" pa se nanaša na različne podprobleme.

```cpp
#include <iostream>
#include <string>
#include <vector>
#include <algorithm>
using namespace std;
```

## Fibonaccijevo zaporedje

Osnovno idejo dinamičnega programiranja si oglejmo na trivialnem primeru Fibonacijevega zaporedja, ki je definirano rekurzivno kot: $F_0 = 0, F_1 = 1, F_n = F_{n-1}+F_{n-2}$. Zanima nas $n$-to število v zaporedju. Pri večjih $n$-jih bodo vrednosti zaporedja precej velike, vendar se s tem ne bomo ukvarjali in bomo zadovoljni z rezultatom, ki je posledica preliva (*overflow*).

```cpp
int fib(int n) {
    if (n<=1) return n;
    return fib(n-1)+fib(n-2);
}

// Preverjanje rezultatov
for (int n=0; n<10; n++) {
    cout << n << ": " << fib(n) << endl;
}
```

Vrednosti izgledajo pravilne. Hitro pa ugotovimo, da na ta način ne bomo mogli računati vrednosti že za malo večje $n$-je. Težava je v eksponentni velikosti drevesa rekurzivnih klicev. Listov tega drevesa, kjer je rezultat funkcije 1, je natanko $F_n$. Poleg tega pa imamo še liste z vrednostjo 0 in vsa notranja vozlišča. Skratka, ogromno število vozlišč oz. klicev funkcije.

Opazimo lahko, da se bo funkcija izvedla večkrat z istim argumentom $n$. Če se nismo kje zmotili, bi moral imeti vsak tak klic funkcije tudi enak rezultat. Rezultat si lahko ob prvem klicu funkcije shranimo, v kasnejših klicih pa ga samo vrnemo. To je pristop **od zgoraj navzdol** (*top-down*), ki je znan tudi pod imenom **memoizacija** (*memoization*). Funkcija se bo torej za vsak možen argument izvedla natanko enkrat, ob ostalih klicih pa bo takoj vrnila vrednost. Število klicev funkcije bo torej $O(n)$, časovna in prostorska zahtevnost pa $O(n)$.

```cpp
const int N=10000;
int memo[N+1];  // memoizacijska tabela

int fib2(int n) {
    if (n<=1) return n;
    if (memo[n]!=0) return memo[n];
    memo[n]=fib2(n-1)+fib2(n-2);
    return memo[n];
}
```

Če smo malo bolj sistematični, lahko rešujemo podprobleme v takem vrstnem redu, da imamo rešitve manjših podproblemov vedno že rešene, ko jih potrebujemo. Podprobleme bomo torej reševali **od spodaj navzgor** (*bottom-up*).

```cpp
int fib3[N+1];
fib3[0]=0;
fib3[1]=1;
for (int n=2; n<=N; n++) fib3[n]=fib3[n-1]+fib3[n-2];
```

Zaradi sistematičnosti pa smo lahko malo bolj prostorsko učinkoviti. Vedno namreč potrebujemo rezultate samo zadnjih dveh izračunanih problemov. Tako lahko prostorsko zahtevnost zmanjšamo na $O(1)$.

```cpp
int fib4(int n) {
    int f2=0, f1=1;
    for (int i=2; i<=n; i++) {
        int fi=f1+f2;
        f2=f1;
        f1=fi;
    }
    return f1;
}
```

## Žabji skoki

Vzdolž potoka gleda iz vode $n$ skal na koordinatah $x_1 < x_2 < \dots < x_n$. Žabec sedi na prvi skali in bi rad z zaporedjem skokov po skalah prispel do zadnje skale. V enem skoku lahko skoči najmanj $a$ in največ $b$ enot daleč v smeri proti cilju. Kakšno je najmanjše število skokov, ki jih potrebuje za to?

Definirajmo podproblem $f(i)$ kot najmanjše število skokov, ki ga žabec potrebuje, da pride na cilj z $i$-te skale:

- $f(n) = 0$
- $f(i) = \min_{j>i:\;a \leq x_j-x_i \leq b} (1 + f(j))$

Rešiti moramo $O(n)$ podproblemov, za rešitev vsakega od njih pa moramo preveriti $O(n)$ možnosti za naslednji skok. Časovna zahtevnost je $O(n^2)$, prostorska pa $O(n)$.

```cpp
const int inf=1e9;
int a=3, b=4;
int mem_jump[1000];

int jump(int i, vector<int> &x) {
    int n=x.size();
    if (i==n-1) return 0;
    if (mem_jump[i]!=0) return mem_jump[i];
    int best=inf;
    for (int j=i+1; j<n; j++) {
        int d=x[j]-x[i];
        if (a<=d && d<=b) best=min(best, 1+jump(j,x));
    }
    mem_jump[i]=best;
    return best;
}
```

S pomočjo dvojiške kopice ali uravnoteženega drevesa za iskanje minimuma na območju lahko časovno zahtevnost izboljšamo na $O(n \log n)$.

## Rezanje palice

Pri problemu rezanja palice (*rod cutting*) imamo palico dolžine $n$, ki jo želimo razrezati na manjše kose in te kose prodati posamično za čim večjo skupno ceno. Naj bo $c_i$ cena kosa dolžine $i$.

Rekurzivni razmislek o zaslužku $f(n)$ pri optimalnem rezanju:
$$f(n) = \max_{x \leq n} (f(n-x) + c_x)$$

| $i$ | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
|---|---|---|---|---|---|---|---|---|
| $c_i$ | 2 | 5 | 6 | 9 | 15 | 16 | 17 | 20 |

```cpp
vector<int> c = {0,2,5,6,9,15,16,17,20};
int N=8;
int f[1000];
f[0]=0;
for (int n=1; n<=N; n++) {
    f[n]=0;
    for (int x=1; x<=n; x++) {
        f[n]=max(f[n], f[n-x]+c[x]);
    }
}
cout << f[N] << endl;
```

Časovna zahtevnost je $O(n^2)$, prostorska pa $O(n)$. Rekonstrukcijo rešitve izvedemo tako, da sledimo kateri $x$ je vodil do optimalne rešitve.

## Utežena izbira aktivnosti

V uteženi različici problema imamo začetke $s_i$, konce $e_i$ in uteži $w_i$. Cilj je poiskati nekonflikten izbor aktivnosti z največjo vsoto uteži.

Naj bo $p(i)$ indeks prve aktivnosti, ki se začne po koncu $i$-te: $p(i) = \min \{ j > i : s_j \geq e_i \}$.
Podproblem $f(i)$ predstavlja največjo vsoto uteži od aktivnosti $i$ do $n$:
$$f(i) = \max \begin{cases} f(i+1) & \text{ne uporabimo } i\text{-te aktivnosti} \\ f(p(i)) + w_i & \text{uporabimo } i\text{-to aktivnost} \end{cases}$$

```cpp
int aktivnostiW(vector<array<int,3>> a) {
    sort(a.begin(), a.end());
    int n = a.size();
    vector<int> p(n), f(n+1);
    for (int i=0; i<n; i++) {
        auto [s,e,w] = a[i];
        p[i] = lower_bound(a.begin(), a.end(), array<int,3>{e,-1,-1}) - a.begin();
    }
    for (int i=n-1; i>=0; i--) {
        auto [s,e,w] = a[i];
        f[i] = max(f[i+1], f[p[i]]+w);
    }
    return f[0];
}
```

Časovna zahtevnost: $O(n \log n)$.

## Pot v mreži

V labirintu velikosti $h \times w$ iščemo število poti od zgoraj-levo do spodaj-desno s premiki samo desno in navzdol.

Podproblem $f(i,j)$ je število poti iz celice $(i,j)$ do cilja:
$$f(i,j) = f(i+1,j) + f(i,j+1)$$
Ob pogoju, da polje ni blokirano ($lab[i][j] \neq \text{'#'}$). Časovna in prostorska zahtevnost sta $O(hw)$.

```cpp
vector<string> lab = {".#....", "....#.", ".#..#.", "......"};
int h=lab.size(), w=lab[0].size();
int f[10][10];
memset(f,0,sizeof(f));
for (int i=h-1; i>=0; i--) {
    for (int j=w-1; j>=0; j--) {
        if (i==h-1 && j==w-1) f[i][j]=1;
        else if (lab[i][j]=='#') f[i][j]=0;
        else f[i][j]=f[i+1][j]+f[i][j+1];
    }
}
```

## Najdaljše skupno podzaporedje (LCS)

Iščemo najdaljši niz, ki je podzaporedje obeh nizov $S$ in $T$.
Naj bo $LCS(i,j)$ dolžina najdaljšega skupnega podzaporedja pripon $S[i \dots n-1]$ in $T[j \dots m-1]$:

$$LCS(i,j) = \max \begin{cases} 1 + LCS(i+1, j+1) & \text{če } S_i = T_j \\ LCS(i+1, j) \\ LCS(i, j+1) \end{cases}$$

Časovna in prostorska zahtevnost: $O(nm)$.

```cpp
string LCS(string s, string t) {
    int n=s.size(), m=t.size();
    int lcs[n+1][m+1];
    memset(lcs,0,sizeof(lcs));
    for (int i=n-1; i>=0; i--) {
        for (int j=m-1; j>=0; j--) {
            lcs[i][j]=max(lcs[i+1][j], lcs[i][j+1]);
            if (s[i]==t[j]) lcs[i][j]=max(lcs[i][j], 1+lcs[i+1][j+1]);
        }
    }
    // Rekonstrukcija niza...
}
```

## Nahrbtnik

Pri 0-1 problemu nahrbtnika imamo predmete s težami $t_i$ in vrednostmi $v_i$. Iščemo podmnožico z maksimalno vrednostjo in skupno težo $\leq T$.

Naj bo $f(i,x)$ največja vrednost z uporabo predmetov od $i$ dalje pri preostali nosilnosti $x$:
$$f(i,x) = \max \begin{cases} f(i+1, x) & \text{ne vzamemo } i\text{-tega predmeta} \\ f(i+1, x-t_i) + v_i & \text{vzamemo } i\text{-ti predmet (če } t_i \leq x) \end{cases}$$

Časovna zahtevnost: $O(nT)$.

```cpp
int f[n+1][nosilnost+1];
memset(f,0,sizeof(f));
for (int i=n-1; i>=0; i--) {
    for (int x=0; x<=nosilnost; x++) {
        f[i][x] = f[i+1][x];
        if (teza[i]<=x) {
            f[i][x] = max(f[i][x], vrednost[i]+f[i+1][x-teza[i]]);
        }
    }
}
```