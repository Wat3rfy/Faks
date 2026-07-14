Tukaj je transkripcija vsebine vaše beležnice v Markdown format s pravilno oblikovanimi LaTeX matematičnimi izrazi in C++ kodo.

---

# Grafi

Graf $G$ je abstraktni podatkovni tip, ki ga sestavljata množica **vozlišč** (*nodes, vertices, points*) $V$ in množica **povezav** (*edges, links*) $E$, ki predstavljajo relacije med pari vozlišč. Vozliščema, ki sestavljata povezavo, rečemo **krajišči** (*endpoints*). Vozlišča in povezave lahko hranijo tudi kakšne dodatne lastnosti.

Običajne operacije, ki jih želimo izvajati na grafu so:

- dodajanje/odstranjevanje vozlišča/povezave
- nastavljanje/ugotavljanje lastnosti vozlišča/povezave
- ugotavljanje sosednosti dveh vozlišč
- iskanje vseh sosednjih vozlišč
- ...

Kadar z grafom modeliramo nek resničen pojav ali proces, namesto grafa pogosto uporabimo izraz *omrežje (network)*. Grafe lahko uporabimo za modeliranje številnih procesov, kot so razna družbena ali komunikacijska omrežja, omrežja soavtorstev ali celo biološka omrežja, ki modelirajo razne kemijske procese. Mi pa se bomo ukvarjali samo s strukturami brez njihovega ozadja, torej z grafi.

## Terminologija

Glavni lastnosti grafa sta število vozlišč $n = |V|$ in število povezav $e = |E|$ (za število povezav bomo včasih uporabljali tudi $m$).

Poznamo več vrst grafov glede na njihove lastnosti:

- **Neusmerjeni** (*undirected*) grafi vsebujejo same neusmerjene povezave, ki predstavljajo simetrične relacije, kjer vrstni red krajišč ni pomemben, npr. med dvema bratoma. **Usmerjeni** (*directed*) grafi (*digraphs*) pa so sestavljeni iz usmerjenih povezav, ki predstavljajo asimetrično relacijo, npr. od otroka k staršu. Te običajno ponazorimo z puščicami.
- Glede na lastnost povezav ločimo med **neuteženimi** (*unweighted*) in **uteženimi** (*weighted*) grafi. V neuteženih grafih so vse povezave enakovredne, v uteženih pa vsaki povezavi priredimo neko numerično vrednost, ki ji rečemo utež, in lahko predstavlja npr. dolžino, ceno, ...
- **Enostavni** (*simple*) grafi ne vsebujejo **zank** (*loop*), ki povezujejo vozlišče s samim seboj, in **vzporednih povezav** (*multiple/parallel edges*) med istimi pari vozlišč.
- Glede na prisotnost ciklov v grafih poznamo **aciklične** (*acyclic*) in **ciklične** (*cyclic*) grafe.
- Grafe precej grobo ločujemo tudi po razmerju med številom povezav in številom vozlišč. V **gostih** (*dense*) grafih je število povezav velikostnega reda, ki je blizu maksimalnemu številu možnih povezav, $e = O(n^2)$. V **redkih** (*sparse*) grafih pa je število povezav linearno odvisno od števila vozlišč $e = O(n)$.

Oglejmo si še nekaj drugih terminov povezanih z grafi:

- Tako kot pri drevesih, tudi v grafih poznamo **stopnjo** (*degree*) vozlišča, ki je enaka številu povezav, ki vključujejo to vozlišče. Če govorimo o stopnji grafa (kar bomo označevali z $d$), pa mislimo največjo stopnjo njegovega vozlišča. V usmerjenih grafih ločujemo **vhodno** in **izhodno** stopnjo (*indegree/outdegree*), ki sta število povezav, ki kažejo v vozlišče oz. izven njega.
- Dve vozlišči sta **sosednji** (*adjacent*) oz. **soseda**, če ju povezuje katera izmed povezav v grafu. Množici sosednjih vozlišč izbranega vozlišča rečemo tudi soseščina (*neighbourhood*).

Poleg že omenjenih splošnih vrst grafov, poznamo tudi več razredov grafov, ki imajo podobne strukturne lastnosti. Poznamo:

- **drevesa** (*trees*), ki so v kontekstu novih terminov pravzaprav aciklični povezani neusmerjeni graf
- **polne grafe** (*complete graph*), ki vsebujejo vse možne povezave ($K_n$)
- **regularne grafe** (*regular graph*), v katerih imajo vsa vozlišča enako stopnjo
- **dvodelne grafe** (*bipartite graph*), ki so sestavljeni iz dveh skupin vozlišč, povezave pa potekajo samo med obema skupinama
- **poti** ($P_n$), **cikle** ($C_n$), **zvezde** ($S_n$), ...

Na grafih nas pogosto zanimajo premiki med sosednjimi vozlišči:

- **Sprehod** (*walk*) je poljubno zaporedje vozlišč, med katerimi se premikamo po povezavah v grafu. Če obstaja sprehod med dvema vozliščema, bomo rekli, da sta **povezani**. Spomnimo se, da če sta povezani neposredno z eno samo povezavo, jima rečemo tudi sosednji.
- **Obhod** (*closed walk*) je sprehod, ki se začne in konča v istem vozlišču.
- **Steza** (*trail*) je sprehod brez ponovljenih povezav.
- **Pot** (*path*) je sprehod brez ponovljenih vozlišč.
- **Cikel** (*cycle*) je obhod brez ponovljenih vmesnih vozlišč (z izjemo začetnega in končnega, ki sta enaka).

## Predstavitve

Strukturo grafa, ki jo definirajo vozlišča in povezave, moramo nekako predstaviti oz. shraniti. Poznamo tri pogoste načine predstavitve grafov.

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

- **Seznam povezav** (*edge list*) je najbolj enostavna predstavitev. Vse povezave v grafu preprosto shranimo v seznam.

```cpp
VII read_graph(string fname, int &n, int &m) {
    ifstream fin(fname);
    fin >> n >> m;
    vector<PII> povezave;
    for (int i=0;i<m;i++) {
        int a,b;
        fin >> a >> b;
        povezave.push_back({a,b});
    }
    fin.close();
    return povezave;
}
```

- **Seznam sosedov** (*adjacency list*) hrani za vsako vozlišče seznam njegovih sosedov.

```cpp
VVI adjacency_list(VII &edge_list, int n, bool dir=false) {
    vector<VI> adj(n);
    for (auto [a,b] : edge_list) {
        adj[a].push_back(b);
        if (!dir) adj[b].push_back(a);
    }
    return adj;
}
```

- **Matrika sosednosti** (*adjacency matrix*) je namenjena učinkovitemu preverjanju sosednosti dveh vozlišč prek matrike $M$, kjer $M_{x,y}$ hrani informacijo o povezavi.

```cpp
VVI adjacency_matrix(VII &edge_list, int n) {
    vector<VI> mat(n, vector<int>(n));
    for (auto [a,b] : edge_list) {
        mat[a][b] = 1;
        mat[b][a] = 1;
    }
    return mat;
}
```

### Primerjava predstavitev

| Lastnost | Seznam povezav | Seznam sosedov | Matrika sosednosti |
| :--- | :--- | :--- | :--- |
| **Prostorska zahtevnost** | $O(e)$ | $O(n+e)$ | $O(n^2)$ |
| **Dodajanje povezave** | $O(1)$ | $O(1)$ | $O(1)$ |
| **Brisanje povezave** | $O(e)$ | $O(n)$ | $O(1)$ |
| **Dodajanje vozlišča** | $O(1)$ | $O(1)$ | $O(n^2)$ |
| **Brisanje vozlišča** | $O(e)$ | $O(e)$ | $O(n^2)$ |
| **Sosednost vozlišč** | $O(e)$ | $O(n)$ | $O(1)$ |

## Preiskovanje grafov

### Preiskovanje v širino (BFS)

Preiskovanje v širino obišče začetno vozlišče, nato njegove sosede, nato njihove sosede itd. Uporablja se za iskanje najkrajših poti v neuteženih grafih.

```cpp
void BFS(int x, vector<VI> &adj, vector<int> &vis, vector<int> &seq) {
    queue<int> q;
    q.push(x); vis[x]=1;
    while (!q.empty()) {
        x=q.front(); q.pop();
        seq.push_back(x);
        for (int y : adj[x]) if (vis[y]==0) {
            q.push(y); vis[y]=1;
        }
    }
}
```

### Preiskovanje v globino (DFS)

Preiskovanje v globino preiskuje graf tako, da se spušča čim globje vzdolž veje, preden se vrne nazaj (backtracking).

```cpp
void DFS(int x, vector<VI> &adj, vector<int> &vis, vector<int> &seq) {
    seq.push_back(x);
    vis[x]=1;
    for (int y : adj[x]) if (vis[y]==0) {
        DFS(y, adj, vis, seq);
    }
}
```

Časovna zahtevnost obeh preiskovanj je $O(n + e)$, prostorska pa $O(n)$.

## Detekcija ciklov

V neusmerjenem grafu cikel zaznamo, ko naletimo na že obiskano vozlišče, ki ni neposredni starš trenutnega vozlišča v DFS drevesu.

```cpp
int cycle(int x, vector<VI> &adj, vector<int> &par, vector<int> &cyc) {
    if (par[x]==-1) par[x]=x;
    for (int y : adj[x]) if (y!=par[x]) {
        if (par[y]!=-1) {  // cikel najden
            for (int z=x; z!=y; z=par[z]) cyc.push_back(z);
            cyc.push_back(y);
            return 1;
        }
        par[y]=x;
        if (cycle(y,adj,par,cyc)) return 1;
    }
    return 0;
}
```

V usmerjenem grafu (cycle v usmerjenih grafih) moramo preveriti, ali povezava kaže na vozlišče, ki je trenutno še v "skladu" (ancestor) trenutnega DFS klica.

```cpp
int cycleDir(int x, vector<VI> &adj, vector<int> &par, vector<int> &path, vector<int> &cyc) {
    if (par[x]==-1) par[x]=x;
    path[x]=1;
    for (int y : adj[x]) {
        if (path[y]) {  // najden povratni rob (cikel)
            for (int z=x; z!=y; z=par[z]) cyc.push_back(z);
            cyc.push_back(y);
            reverse(cyc.begin(), cyc.end());
            return 1;
        }
        if (par[y]==-1) {
            par[y]=x;
            if (cycleDir(y,adj,par,path,cyc)) return 1;
        }
    }
    path[x]=0;
    return 0;
}
```

## Topološko urejanje

Topološko urejanje usmerjenega acikličnega grafa (DAG) je linearna ureditev vozlišč, tako da za vsako usmerjeno povezavo $u \to v$ velja, da se $u$ pojavi pred $v$.

```cpp
VI toposort(vector<VI> &sosedi, int n) {
    vector<int> indeg(n);
    for (int x=0;x<n;x++) {
        for (int y : sosedi[x]) indeg[y]++;
    }
    queue<int> q;
    for (int x=0;x<n;x++) {
        if (indeg[x]==0) q.push(x);
    }
    vector<int> seq;
    while (!q.empty()) {
        int x=q.front(); q.pop();
        seq.push_back(x);
        for (int y : sosedi[x]) {
            indeg[y]--;
            if (indeg[y]==0) q.push(y);
        }
    }
    return seq;
}
```

## Kritična pot

Kritična pot je najdaljša pot v usmerjenem acikličnem grafu (DAG). Izračunamo jo lahko z uporabo dinamičnega programiranja v topološkem vrstnem redu. Formula za najdaljšo pot $d(x)$ iz vozlišča $x$ je:
$$d(x) = \max_{y: (x,y) \in E} (w(x,y) + d(y))$$

```cpp
// Izračun razdalj d[x] v obratnem topološkem vrstnem redu
vector<int> d(n);
for (int x : ord_rev) {
    for (auto [y, w] : adjw[x]) {
        d[x] = max(d[x], w + d[y]);
    }
}
```

## Eulerjev obhod

Eulerjev obhod je obhod, ki obišče vsako povezavo grafa natanko enkrat.
- **Neusmerjen graf**: Eulerjev obhod obstaja, če in samo če je graf povezan in so vsa vozlišča sode stopnje.
- **Eulerjev sprehod**: Obstaja, če sta natanko dve vozlišči lihe stopnje (začetek in konec).

Hierholzerjev algoritem omogoča iskanje Eulerjevega obhoda v času $O(e)$.