sc

# Najkrajše poti

Klasičen problem na grafih je iskanje najkrajših poti. Zanima nas na primer najkrajša pot med parom vozlišč $A$ in $B$ (*single-pair shortest path*). Naj bo ta najkrajša pot sestavljena iz vozlišč $A, \dots, X, B$, kjer je $X$ predzadnje vozlišče na poti. V tem primeru mora biti tudi pot od $A$ do $X$ najkrajša, sicer bi lahko pot od $A$ do $B$ izboljšali. Pri iskanju najkrajše poti od $A$ do $B$ posledično izračunamo tudi najkrajše poti do ostalih vozlišč na tej poti.

Če bomo že morali izračunati najkrajše poti iz $A$ do več drugih vozlišč, pa jih lahko izračunamo iz začetnega vozlišča kar do vseh (*single-source shortest path*). Opazimo tudi, da bodo te najkrajše poti v grafu formirale **drevo najkrajših poti**. Vsako vozlišče bo imelo namreč enega optimalnega predhodnika/starša na najkrajši poti (npr. $X$ bo predhodnik $B$-ja). Koren drevesa pa bo seveda v vozlišču $A$.

Za problem iskanja najkrajših poti med vsemi pari točk, lahko $N$-krat poženemo algoritem za iskanje drevesa najkrajših poti iz posameznega začetnega vozlišča. Obstajajo pa tudi drugi algoritmi, ki so namenjeni prav iskanju poti med vsemi pari točk. Tak primer je *Floyd-Warshall*-ov algoritem, ki ga bomo obravnavali kasneje.

Ukvarjali se bomo predvsem z neusmerjenimi grafi. V usmerjenih grafih je situacija namreč podobna in lahko uporabimo enake razmisleke.

### Priprava okolja in branje grafa

```cpp
#include <iostream>
#include <fstream>
#include <vector>
#include <queue>
#include <algorithm>
#include <array>
#include <tuple>
#include <iomanip>
#include <map>

using namespace std;

typedef pair<int,int> PII;
typedef array<int,3> III;
typedef vector<int> VI;
typedef vector<pair<int,int>> VII;
typedef vector<array<int,3>> VIII;
typedef vector<vector<int>> VVI;

const int INF = 1'000'000'000;

// Pomožne funkcije za izpis
void print(const vector<int> &sez, int w=4) {
    for (int x : sez) {
        cout << setw(w);
        if (x==INF) cout << "INF";
        else if (x==-INF) cout << "-INF";
        else cout << x;
        cout << " ";
    }
    cout << endl;
}

auto read_graph(string fname, bool directed=true) {
    ifstream fin(fname);
    int n, m;
    fin >> n >> m;
    vector<III> edges;
    vector<VII> adj(n);
    vector<VI> mat(n, VI(n, INF));
    for (int i=0; i<m; i++) {
        int a, b, w;
        fin >> a >> b >> w;
        edges.push_back({a, b, w});
        adj[a].push_back({b, w});
        mat[a][b] = w;
        if (!directed) {
            edges.push_back({b, a, w});
            adj[b].push_back({a, w});
            mat[b][a] = w;
        }
    }
    return make_tuple(n, m, edges, adj, mat);
}
```

## Neuteženi grafi

V neuteženih grafih uporabimo metodo **iskanja v širino (BFS)**, ki obiskuje vozlišča od bližnjih proti bolj oddaljenim.

```cpp
void BFS_distance(vector<VI> &adj, int start, vector<int> &dist, vector<int> &prev) {
    int n = adj.size();
    dist = vector<int>(n, -1); 
    prev = vector<int>(n);
    vector<int> vis(n, 0);
    queue<int> q;
    q.push(start); vis[start] = 1;
    dist[start] = 0; prev[start] = -1;
    while (!q.empty()) {
        int x = q.front(); q.pop();
        for (int y : adj[x]) {
            if (!vis[y]) {
                q.push(y); vis[y] = 1;
                dist[y] = dist[x] + 1; 
                prev[y] = x;
            }
        }
    }
}
```

## Uteženi grafi (nenegativne uteži)

### Dijkstrov algoritem

Dijkstrov algoritem temelji na požrešnem pristopu: vedno izberemo vozlišče z najmanjšo trenutno znano razdaljo. Deluje samo na grafih s **pozitivnimi (nenegativnimi) utežmi**.

**Klasična implementacija ($O(n^2)$):**
Primerna za goste grafe.

```cpp
void Dijkstra(vector<VII> &adjw, int start, vector<int> &dist, vector<int> &prev) {
    int n = adjw.size();
    dist = vector<int>(n, -1); prev = vector<int>(n, -1);
    vector<int> p(n, -1);  // potencialne razdalje (-1=neobiskano, -2=končano)
    p[start] = 0;
    while (true) {
        int x = -1;
        for (int i=0; i<n; i++) if (p[i] >= 0) {
            if (x == -1 || p[i] < p[x]) x = i;
        }
        if (x == -1) break;
        dist[x] = p[x]; p[x] = -2;
        for (auto [y, w] : adjw[x]) {
            int d = dist[x] + w;
            if (p[y] == -1 || (p[y] >= 0 && d < p[y])) {
                p[y] = d; prev[y] = x;
            }
        }
    }
}
```

**Implementacija s prioritetno vrsto ($O(e \log n)$):**
Primerna za redke grafe.

```cpp
void Dijkstra_PQ(vector<VII> &adjw, int start, vector<int> &dist, vector<int> &prev) {
    int n = adjw.size();
    dist = vector<int>(n, -1); prev = vector<int>(n, -1);
    priority_queue<PII, vector<PII>, greater<PII>> pq;
    dist[start] = 0; pq.push({0, start});
    while (!pq.empty()) {
        auto [d, x] = pq.top(); pq.pop();
        if (dist[x] != -1 && dist[x] < d) continue;
        for (auto [y, w] : adjw[x]) {
            int d_new = dist[x] + w;
            if (dist[y] == -1 || d_new < dist[y]) {
                dist[y] = d_new; prev[y] = x;
                pq.push({d_new, y});
            }
        }
    }
}
```

## Bellman-Fordov algoritem

Bellman-Fordov algoritem rešuje problem najkrajših poti v usmerjenih grafih z **negativnimi utežmi** (pod pogojem, da ni negativnih ciklov). Časovna zahtevnost je $O(en)$.

Rekurzivna formula:
$$d_l(X) = \min(d_{l-1}(X), \min_Y (d_{l-1}(Y) + w(Y,X)))$$

```cpp
void BellmanFord(int n, vector<III> &edges, int start, vector<int> &dist, vector<int> &prev) {
    dist = vector<int>(n, INF); prev = vector<int>(n, -1);
    dist[start] = 0;
    for (int l=1; l<=n-1; l++) {
        for (auto [y, x, w] : edges) {
            if (dist[y] == INF) continue;
            if (dist[y] + w < dist[x]) {
                dist[x] = dist[y] + w;
                prev[x] = y;
            }
        }
    }
}
```

### Zaznavanje negativnih ciklov
Če v $n$-ti iteraciji še vedno pride do spremembe, graf vsebuje negativen cikel.

```cpp
void BellmanFord_NegCycle(int n, vector<III> &edges, int start, vector<int> &dist, vector<int> &prev) {
    // ... (enako kot zgoraj do n-1 iteracij)
    int a = -1;
    for (auto [y, x, w] : edges) {
        if (dist[y] != INF && dist[y] + w < dist[x]) {
            a = x; break;
        }
    }
    if (a != -1) cout << "Zaznan negativen cikel!" << endl;
}
```

## Floyd-Warshallov algoritem

Uporablja se za iskanje najkrajših poti med **vsemi pari vozlišč**. Deluje tudi z negativnimi utežmi. Časovna zahtevnost je $O(n^3)$.

Osnovna ideja (dinamično programiranje):
$$f_k(x,y) = \min(f_{k-1}(x,y), f_{k-1}(x,k) + f_{k-1}(k,y))$$

```cpp
void FloydWarshall(vector<VI> &mat, vector<VI> &dist, vector<VI> &prev) {
    int n = mat.size();
    dist = mat;
    prev = vector<VI>(n, vector<int>(n, -1));
    for (int i=0; i<n; i++) {
        for (int j=0; j<n; j++) if (mat[i][j] != INF) prev[i][j] = i;
        dist[i][i] = 0;
    }

    for (int k=0; k<n; k++) {
        for (int x=0; x<n; x++) {
            for (int y=0; y<n; y++) {
                if (dist[x][k] != INF && dist[k][y] != INF) {
                    if (dist[x][k] + dist[k][y] < dist[x][y]) {
                        dist[x][y] = dist[x][k] + dist[k][y];
                        prev[x][y] = prev[k][y];
                    }
                }
            }
        }
    }
}
```

## Primeri sorodnih problemov

- **Najširša pot (Widest path):** Maksimiziramo minimalno utež na poti.
- **Najdaljša pot:** NP-poln problem (razen v DAG-ih).
- **15 Puzzle:** BFS na implicitnem grafu stanj.
- **Tranzitivna ovojnica:** Uporaba Floyd-Warshalla z logičnimi operacijami.
- **Arbitraža:** Iskanje negativnih ciklov v grafu menjalnih tečajev (z uporabo logaritmov).