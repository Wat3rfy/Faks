Tukaj je transkripcija vsebine v formatu LaTeX Markdown.

# Disjunktne množice

Čeprav poglavje obljublja delo z vpetimi drevesi, se bomo najprej posvetili neki drugi podatkovni strukturi, ki nam bo kasneje prišla prav. Prav pa nam pride v številnih aplikacijah, kjer imamo opravka z združevanjem množic ali kakšnih drugih ekvivalenčnih razredov objektov.

Podatkovna struktura disjunktnih množic (*disjoint-set*) hrani množico disjunktnih množic (ali razbitje množice na podmnožice) in omogoča naslednje operacije:

-   `add(x)`: Doda novo množico $\{x\}$ z enim samim elementom.
-   `find(x)`: Najde množico, ki ji pripada element $x$.
-   `union(x,y)`: Združi množici elementov $x$ in $y$.

Poleg disjunktnih množic se za to podatkovno strukturo uporablja tudi izraz **union-find**. Pogosto se problemi začnejo s množicami $n$ posameznih elementov, ki jih nato združujemo z uporabo funkcij `union` in `find`, zato se bomo omejili na ta primer. Dopolnitev razvitih rešitev s funkcijo `add` za dodajanje novega elementa je enostavna.

![Disjoint Set Diagram](disjoint-set.svg)

Posamezne množice bomo predstavili z drevesi. Koren drevesa pa bo predstavnik posamezne množice. Funkcija `find(x)` bo torej morala poiskati in vrniti koren drevesa, funkcija `union(x,y)` pa združiti dve drevesi v eno. Koren drevesa z elementom $x$ lahko pripnemo kot otroka korenu drevesa z elementom $y$. Združevanje je torej učinkovito, vendar lahko s takimi združevanji nastanejo zelo izrojena drevesa, zato je časovna zahtevnost operacije `find` linearna.

Zanimala nas bo amortizirana časovna zahtevnost posamezne `find` operacije v spodobno dolgem zaporedju vsaj $m \geq n$ operacij.

```cpp
#include <iostream>
#include <fstream>
#include <vector>
#include <queue>
#include <algorithm>
using namespace std;

typedef pair<int,int> PII;
typedef vector<int> VI;
typedef vector<pair<int,int>> VII;
typedef vector<vector<int>> VVI;

template<typename T>
void print(const vector<T> &sez) {
    for (T x : sez) cout << x << " ";
    cout << endl;
}
```

### Združevanje po velikosti

Pri združitvi dveh dreves je smiselno manjšega pripeti k večjemu. Velikost drevesa lahko merimo po številu vozlišč (*union by size*) ali po oceni višine (*union by rank*). Vsako vozlišče lahko nastopa v največ $O(\log n)$ združevanjih, zato je dolžina poti od vsakega vozlišča do korena dolga $O(\log n)$. Časovna zahtevnost operacije `find` je v tem primeru $O(\log n)$.

### Stiskanje poti

Če smo že prehodili dolgo pot, da smo našli koren, bi lahko vsa vozlišča na poti tudi povezali direktno nanj (*path compression*). Če upoštevamo še združevanja, je amortizirana zahtevnost operacije `find` enaka $O(\log n)$.

### Skupna rešitev

Z uporabo obeh izboljšav hkrati dobimo časovno zahtevnost $O(m \alpha(n))$, kjer je $\alpha(n)$ inverzna Ackermannova funkcija. Ta funkcija raste izjemno počasi in je praktično konstantna ($< 5$) za vse razumne vrednosti $n$.

```cpp
class DisjointSet {  // Union-Find
public:
    vector<int> parent, size;
    DisjointSet(int n) {
        parent = vector<int>(n);
        size = vector<int>(n);
        for (int i=0;i<n;i++) {  // individual sets
            parent[i] = i;
            size[i] = 1;
        }
    }
    
    int root(int x) {  // find
        if (parent[x]==x) return x;  // reached the root        
        int r = root(parent[x]);
        parent[x] = r;  // path compression
        return r;
    }

    void join(int x, int y) {  // union by size
        x=root(x); y=root(y);  // replace by roots
        if (x==y) return;
        if (size[x]>size[y]) swap(x,y);  // make x smaller
        parent[x] = y;  // attach to larger root
        size[y] += size[x];
    }
};
```

# Minimalno vpeto drevo

**Vpeto drevo** (*spanning tree*) grafa $G$ je drevo $T$, ki vključuje vsa vozlišča grafa $G$ in podmnožico njegovih povezav. **Minimalno vpeto drevo** (*minimum spanning tree, MST*) je tisto vpeto drevo, ki ima najmanjšo vsoto uteži povezav.

### Prerezna lastnost

Prerezna lastnost (*cut property*) pravi, da je najmanjša prerezna povezava vedno del nekega minimalnega vpetega drevesa (ne glede na izbrani prerez).

## Prim

Primov algoritem je požrešen algoritem, ki gradi minimalno vpeto drevo s širjenjem od izhodiščnega vozlišča navzven. Na vsakem koraku poiščemo vozlišče z najmanjšo razdaljo do že zgrajenega drevesa, ga dodamo in posodobimo razdalje sosedov. Časovna zahtevnost s prioritetno vrsto je $O(m \log n)$.

```cpp
int Prim(int n, vector<VII> &adj, vector<PII> &mst) {
    vector<int> dist(n,-1);  // distance from the tree
    vector<int> done(n, 0), parent(n);
    int cost=0;
    priority_queue<PII, vector<PII>, greater<PII>> pq;
    dist[0]=0; pq.push({0,0});
    while (!pq.empty()) {
        auto [d,x]=pq.top(); pq.pop();
        if (done[x]) continue;
        cost+=d;
        done[x]=1;
        for (auto [y,w] : adj[x]) if (!done[y]) {
            if (dist[y]==-1 || w<dist[y]) {
                dist[y]=w; pq.push({w,y});
                parent[y]=x;
            }
        }
    }
    for (int x=1;x<n;x++) {
        mst.push_back({x,parent[x]});
    }
    return cost;
}
```

## Kruskal

Kruskalov algoritem povezave uredi po velikosti in jih zaporedno dodaja, če njihova vključitev ne ustvari cikla. Za učinkovito preverjanje ciklov uporabimo podatkovno strukturo disjunktnih množic. Časovna zahtevnost je $O(m \log m)$ oziroma $O(m \log n)$.

```cpp
bool cmpW(VI e1, VI e2) { return e1[2] < e2[2]; }

int Kruskal(int n, vector<VI> &edges, vector<PII> &mst) {
    sort(edges.begin(), edges.end(), cmpW);  // sort by weights
    DisjointSet ds(n);
    int cost=0;
    for (VI e : edges) {
        int a=e[0], b=e[1], w=e[2];
        if (ds.root(a)==ds.root(b)) continue;  // same component?
        ds.join(a,b);
        cost+=w;
        mst.push_back({a,b});
    }
    return cost;
}
```

## Steinerjevo drevo v grafu

V problemu Steinerjevega drevesa želimo povezati samo izbrano podmnožico vozlišč (terminale), medtem ko lahko preostala vozlišča uporabimo po potrebi.

-   $t = n$: Problem se prevede na minimalno vpeto drevo.
-   $t = 2$: Problem se prevede na iskanje najkrajše poti.
-   V splošnem je problem NP-težek.
