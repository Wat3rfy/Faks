Tukaj je transkripcija vsebine v formatu LaTeX Markdown.

# Drevesa

Drevo je abstraktni podatkovni tip, ki hrani hierarhijo podatkov v svojih vozliščih. Uporabljamo jih lahko za predstavitev hierarhije, datotečne strukture, opis strukture aritmetičnih izrazov ali gramatike, opis poteka postopka, učinkovito organizacijo podatkov, ... V računalništvu rastejo drevesa od zgoraj navzdol. Zaradi raznolikosti različnih dreves ne bomo naštevali posameznih operacij na tem mestu, temveč se bomo z njimi ukvarjali na konkretnih primerih drevesnih podatkovnih struktur.

![Drevo - wikipedija](https://upload.wikimedia.org/wikipedia/commons/5/5f/Tree_%28computer_science%29.svg)

### Terminologija

Da se bomo lahko pogovarjali o drevesih, si oglejmo nekaj običajne terminologije v zvezi z njimi.

- **Vozlišče** (*node/vertex*) je osnovni gradnik drevesa, ki lahko hrani nek podatek in **povezave** (*edge/link*) do drugih vozlišč. Vrhnje vozlišče v drevesu, ki predstavlja začetek drevesa, se imenuje **koren** (*root*). Struktura drevesa je rekurzivna, saj vozlišča hranijo povezave do korenov **poddreves** (*subtree*), ki imajo enako strukturo. Vozliščem, ki nimajo nadaljnjih povezav, rečemo **listi** (*leaves*) ali **zunanja** (*external*) vozlišča, ostalim pa **notranja** (*internal*).

- Povezave v drevesu povezujejo **starša** (*parent*) z **otrokom** (*child*). Starš in otroci vozlišča so njegovi **sosedi** (*neighbours*). Koren nima starša, vsa ostala vozlišča v drevesu pa imajo natanko enega. Vsa vozlišča razen listov imajo svoje otroke. Otrokom istega vozlišča rečemo **sorojenci** (*siblings*). Vsa vozlišča v poddrevesih otrok se imenujejo **potomci** (*descendants*). Do njih pridemo po poti od vozlišča proti listom. Vzdolž poti od vozlišča proti korenu pa se nahajajo **predniki** (*ancestors*).

- Številu otrok rečemo tudi **stopnja** (*degree*) vozlišča, skupnemu številu vozlišč v drevesu pa **velikost** (*size*) drevesa. **Globina** (*depth*) vozlišča je število povezav na poti od korena do tega vozlišča. Globina korena je tako običajno 0, včasih pa se uporablja tudi 1. **Višina** (*height*) drevesa je največja globina vozlišča v njem, torej dolžina najdaljše poti do nekega lista.

- Običajno si predstavljamo, da so drevesa "košata" in ne prav globoka. Takim "lepim" drevesom z nizko višino rečemo **uravnotežena** (*balanced*) drevesa. Če temu ni tako, rečemo, da je drevo **izrojeno** (*degenerate*), npr. povezan seznam je ekstremen primer izrojenega drevesa. Ločnica med uravnoteženimi in izrojenimi primeri je odvisna od primera uporabe. Načeloma pa bomo rekli, da imajo uravnotežena drevesa višino, ki je logaritemsko odvisna od števila vozlišč v njem, torej $h = O(\log n)$, izrojena pa so vsa ostala.

Pomembna lastnost dreves je, da med vsakim parom vozlišč obstaja enolično določena pot. Drevesa so poseben primer grafov, kjer to v splošnem ne velja in predstavlja glaven vir komplikacij. Poleg tega se bomo ukvarjali z drevesi s korenom oz. ukoreninjenimi drevesi (*rooted tree*). V teoriji grafov namreč obstaja koncept drevesa, ki pomeni, da graf ne vsebuje ciklov in ima zato enolično določene poti med pari vozlišč, vendar nima posebej določenega korenskega vozlišča.

### Obhodi dreves

Obhod drevesa je sistematičen postopek, ki obišče vsa vozlišča drevesa v nekem vrstnem redu. Poznamo štiri pogoste vrste obhodov:

- **Premi** (*pre-order*) obhod obišče vozlišče, nato pa rekurzivno po vrsti vsa poddrevesa.
- **Vmesni** (*in-order*) obhod obišče najprej levo poddrevo, nato vozlišče in nato še desno poddrevo (v primeru dvojiškega drevesa). Če gre za iskalno drevo, nam vmesni obhod vrne urejeno zaporedje.
- **Obratni** (*post-order*) obhod obišče rekurzivno vsa poddrevesa in šele nato vozlišče.
- **Nivojski** (*level-order*) obhod obišče vozlišča po nivojih, najprej koren, nato njegove otroke, nato otroke teh otrok, itd.

![Obhodi drevesa - wikipedija](https://upload.wikimedia.org/wikipedia/commons/7/75/Sorted_binary_tree_ALL_RGB.svg)

Zgornja slika prikazuje vrstni red obravnave vozlišč pri različnih obhodih. Premi obhod (F, B, A, D, C, E, G, I, H) je prikazan z rdečo, vmesni (A, B, C, D, E, F, G, H, I) z zeleno, obratni (A, C, E, D, B, H, I, G, F) pa z modro.

### Vrste dreves

- **Dvojiška** (*binary*) drevesa: Vsako vozlišče ima največ dva otroka. Splošneje: **k-tiško** (*k-ary*) drevo.
- **Polno** (*full*) drevo: Vsako vozlišče ima maksimalno število otrok ali nobenega.
- **Poravnano/celovito** (*complete*) drevo: Vsi nivoji so polni, razen morda zadnjega, ki se polni z leve (npr. kopica).
- **Popolna** (*perfect*) drevesa: Vsi listi so na enaki globini.
- **Iskalna** (*search*) drevesa: Urejena drevesa, kjer velja pravilo o vrednostih v poddrevesih (npr. levo manjši, desno večji).
- **Črkovna/znakovna** drevesa (*trie*): Namenjena hrambi zaporedij znakov.

### Predstavitev dreves

Najbolj običajna predstavitev je s *seznamom otrok* (kazalci/reference). Če se premikamo proti korenu, uporabimo *povezavo do starša*. Za določene strukture (kot kopica) uporabljamo *implicitno predstavitev* s tabelo.

```cpp
#include <iostream>
#include <vector>
#include <random>
#include <algorithm>
using namespace std;

class BSTree {
public:
    int value;
    BSTree *left, *right;
    BSTree(int v, BSTree *l=NULL, BSTree *r=NULL) : value(v), left(l), right(r) {}

    void insert(int x) {
        if (x <= value) {
            if (!left) left = new BSTree(x);
            else left->insert(x);
        } else {
            if (!right) right = new BSTree(x);
            else right->insert(x);
        }
    }

    void inorder(vector<int> &seq) {
        if (left) left->inorder(seq);
        seq.push_back(value);
        if (right) right->inorder(seq);
    }
};
```

## Poizvedbe na območjih

Ukvarjali se bomo s tabelo $A = [a_0, a_1, \dots, a_{n-1}]$ in poizvedbami $q(l,r)$ na območju $[l, r)$.

### Vsota (Range Sum Query)
Z uporabo kumulativnih vsot $c_r = \sum_{i=0}^{r-1} a_i$:
- Predobdelava: $O(n)$
- Poizvedba: $O(1)$ ($c_r - c_l$)

### Minimum (Range Minimum Query - RMQ)

1. **Naivna rešitev**: Poizvedba $O(n)$, Predobdelava $O(1)$.
2. **Bloki (Korensko razbitje)**: Tabelo razdelimo na bloke velikosti $B = \sqrt{n}$.
   - Predobdelava: $O(n)$
   - Poizvedba: $O(\sqrt{n})$
3. **Statično drevo (Segmentno drevo)**:
   - Predobdelava: $O(n)$
   - Poizvedba: $O(\log n)$

```cpp
class RMQ {
private:
    int n;
    vector<int> array;
    struct Node { int min, begin, end; };
    vector<Node> tree;
    int INF=1e9;
public:
    RMQ(vector<int> &a) {
        n = pow(2, ceil(log2((double)a.size())));
        array = a;
        array.resize(n, INF);
        tree.resize(2*n);
        build();
    }

    void build(int id=1) {
        if (id >= n) { tree[id] = {array[id-n], id-n, id-n+1}; return; }
        int left=2*id, right=2*id+1;
        build(left); build(right);
        tree[id] = {min(tree[left].min, tree[right].min), tree[left].begin, tree[right].end};
    }

    int query(int l, int r, int id=1) {
        if (l <= tree[id].begin && tree[id].end <= r) return tree[id].min;
        if (r <= tree[id].begin || tree[id].end <= l) return INF;
        return min(query(l, r, 2*id), query(l, r, 2*id+1));
    }
};
```

## Uravnotežena drevesa

Da preprečimo izroditev v povezan seznam, uporabljamo tehnike uravnoteževanja, ki zagotavljajo višino $h = O(\log n)$.

### AVL drevo
Dvojiško iskalno drevo, kjer se v vsakem vozlišču višini levega in desnega poddrevesa razlikujeta kvečjemu za 1. Minimalno število vozlišč za višino $h$ sledi rekurziji $f(h) = 1 + f(h-1) + f(h-2)$ (podobno Fibonacciju).

**Rotacije**: Osnovni operaciji za popravljanje ravnovesja sta leva in desna rotacija.

```cpp
class AVLNode {
public:
    int value;
    AVLNode *left, *right;
    int height;
    AVLNode(int v) : value(v), left(NULL), right(NULL), height(1) { }
};

class AVLTree {
public:
    AVLNode *root = NULL;

    int height(AVLNode* node) { return (node!=NULL) ? node->height : 0; }
    int balance(AVLNode* node) { return height(node->right) - height(node->left); }
    void update(AVLNode* node) { node->height = 1 + max(height(node->left), height(node->right)); }

    AVLNode* rotateLeft(AVLNode* node) {
        AVLNode *R = node->right;
        node->right = R->left; R->left = node;
        update(node); update(R);
        return R;
    }

    AVLNode* rotateRight(AVLNode* node) {
        AVLNode *L = node->left;
        node->left = L->right; L->right = node;
        update(node); update(L);
        return L;
    }

    AVLNode* insert(int x, AVLNode* node) {
        if (node == NULL) return new AVLNode(x);
        if (x <= node->value) node->left = insert(x, node->left);
        else node->right = insert(x, node->right);
        
        update(node);
        int b = balance(node);
        
        if (b == 2) {
            if (balance(node->right) < 0) node->right = rotateRight(node->right);
            return rotateLeft(node);
        } else if (b == -2) {
            if (balance(node->left) > 0) node->left = rotateLeft(node->left);
            return rotateRight(node);
        }
        return node;
    }
    
    void insert(int x) { root = insert(x, root); }
};
```

### Druga uravnotežena drevesa
- **Rdeče-črno drevo**: Uporablja barvanje vozlišč; pogosto v standardnih knjižnicah (npr. `std::map`).
- **2-3 drevo**: Vozlišča imajo lahko 2 ali 3 otroke; vsi listi na isti globini.
- **B-drevo**: Posplošitev 2-3 dreves; optimizirano za sisteme z diski/bazami.
- **Lomljeno drevo (Splay tree)**: Amortizirana logaritemska zahtevnost; premika dostopane elemente h korenu.
- **Naključno uravnoteženo drevo (Treap)**: Kombinacija binarnega iskalnega drevesa in kopice z naključnimi prioritetami.




***
**Poglejmo še fenwickovo drevo**