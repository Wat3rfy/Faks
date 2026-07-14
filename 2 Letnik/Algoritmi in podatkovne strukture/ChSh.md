\documentclass[a4paper,7pt]{extarticle}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[slovene]{babel}
\usepackage[margin=0.5cm,top=0.4cm,bottom=0.4cm]{geometry}
\usepackage{amsmath,amssymb}
\usepackage{multicol}
\usepackage{enumitem}
\usepackage{titlesec}
\usepackage{array}
\usepackage{booktabs}
\usepackage{ragged2e}
\usepackage{microtype}

% Compact settings
\setlength{\parskip}{0pt}
\setlength{\parindent}{0pt}
\setlength{\columnsep}{0.5cm}
\setlength{\tabcolsep}{3pt}
\linespread{0.9}

% Section formatting - even smaller
\titleformat{\section}{\bfseries\fontsize{6}{7}\selectfont\uppercase}{\thesection}{0.3em}{}
\titleformat{\subsection}{\bfseries\fontsize{6}{7}\selectfont}{\thesubsection}{0.3em}{}
\titleformat{\subsubsection}{\bfseries\fontsize{6}{7}\selectfont}{\thesubsubsection}{0.3em}{}
\titlespacing*{\section}{0pt}{2pt}{1pt}
\titlespacing*{\subsection}{0pt}{2pt}{1pt}
\titlespacing*{\subsubsection}{0pt}{2pt}{1pt}

% Compact lists with better spacing
\setlist[itemize]{leftmargin=0.4cm,itemsep=0.5pt,parsep=0pt,topsep=1pt}
\setlist[enumerate]{leftmargin=0.4cm,itemsep=0.5pt,parsep=0pt,topsep=1pt}

% Compact tables
\renewcommand{\arraystretch}{0.9}

% Prevent overfull hboxes
\sloppy
\hyphenpenalty=50

\begin{document}
\pagestyle{empty}
\RaggedRight
\fontsize{6.5}{7.5}\selectfont

\begin{multicols}{3}

\section*{Krovni izrek}
Nek problem velikosti $n$ razbijemo na podprobleme. Ob klicu rekurzije problem velikosti $n$ razbijemo na podprobleme velikosti $\frac{n}{b}$. Faktor \textbf{$b$} = število podproblemov ki nastane (ni enako številu ki jih rešimo). Konstanta $a$ pove koliko vej se obravnava. Idealno $a \leq b$. 

Primer: dvojiško iskanje: $b=2$, $a=1$. Prištejemo $f(n)$ kot strošek operacij zunaj rekurzivnega klica (pri dvojiškem iskanju $O(1)$).

Splošna oblika: 
$$T(n) = a \cdot T\left(\frac{n}{b}\right) + f(n)$$

Na vrhu: 1 problem velikosti $n$ s stroškom $f(n)$. Na nivoju 1: $a$ podproblemov velikosti $n/b$, strošek $a \cdot f(n/b)$. Na nivoju $i$: $a^{i}$ podproblemov velikosti $n/b^{i}$, strošek $a^{i} \cdot f(n/b^{i})$.

Višina drevesa: $\log_{b}{n}$. Število listov: $a^{\log_{b}{n}} = n^{\log_{b}{a}}$ = \textbf{kritična funkcija} (skupno delo v listih).

Primerjava kritične funkcije z $f(n)$:

-- $f(n)$ raste \textbf{polinomsko počasneje} kot $n^{\log_{b}{a}}$: $f(n) = O(n^{\log_{b}{a}-C})$, $C > 0$. Potem $T(n) = \Theta(n^{\log_{b}{a}})$. Delo se eksponentno povečuje, vsota določena z listi.

-- $f(n)$ raste \textbf{asimptotično enako}: $f(n) = \Theta(n^{\log_{b}{a}})$. Potem $T(n) = \Theta(n^{\log_{b}{a}} \log{n})$. Na vsakem nivoju enako delo, pomnožimo z $\log_b n$ nivoji.

-- $f(n)$ raste \textbf{polinomsko hitreje}: $f(n) = \Omega(n^{\log_b a + C})$, $C > 0$ in regularnost: $a f(n/b) \le c f(n)$, $c < 1$. Potem $T(n) = \Theta(f(n))$. Delo se hitro zmanjšuje, vsota določena s korenom.

Označimo $\log_{b}{a} = c$.

\section*{1. Poizvedbe na območjih}

Problem: Tabela $A$, hitri odgovori o lastnostih (vsota, min, max) podintervala $[l, r)$.

\textbf{A) Range Sum Query (RSQ)} -- Kumulativne vsote: $c_r = a_0 + \dots + a_{r-1}$. Formula: $sum(l, r) = c_r - c_l$. Predobdelava $O(n)$, poizvedba $O(1)$. Omejitev: tabela se ne spreminja.

\textbf{B) Range Minimum Query (RMQ)} -- 1) \textit{Korensko razbitje:} bloki $\sqrt{n}$, minimum na blok. Poizvedba $O(\sqrt{n})$, posodobitev $O(1)$. 2) \textit{Segmentno drevo:} Statično dvojiško drevo. Predobdelava $O(n)$, poizvedba $O(\log n)$, posodobitev $O(\log n)$. Prednost: hitre posodobitve.

\section*{2. Uravnotežena drevesa}

Osnovna BST se lahko izrodijo v seznam $O(n)$. Uravnotežena drevesa: višina $O(\log n)$.

\textbf{AVL drevo} -- Pogoj: višini levega in desnega poddrevesa se razlikujeta za največ 1. Faktor ravnovesja $b$: $height(desno) - height(levo) \in \{-1, 0, 1\}$. Če $|b| > 1$: \textbf{rotacije}. Enojna (Leva/Desna): drevo nagnjeno v isto stran. Dvojna (Leva-Desna/Desna-Leva): "koleno". Zahtevnost: iskanje, vstavljanje, brisanje $O(\log n)$.

\textbf{Drugi tipi:} \textit{Rdeče-črno drevo:} Manj strogo (višina do $2 \log n$), manj rotacij. Standard v C++ (\texttt{std::map}). \textit{Treap:} Ključ + naključna prioriteta. Ravnovesje statistično. \textit{Splay drevo:} Zadnji dostopani v koren. Amortizirano $O(\log n)$. \textit{B-drevesa:} Več ključev/otrok. Optimizirana za diske.

\section*{3. Izpitni namigi}

\textbf{Range Queries:} 1) Samo vsote, ni posodobitev? $\to$ Kumulativne vsote ($O(1)$). 2) Min/Maks, ni posodobitev? $\to$ Sparse Table ($O(1)$) ali Segmentno drevo. 3) Posodobitve? $\to$ Segmentno drevo ali Fenwickovo drevo (BIT).

\textbf{AVL:} 1) Višina: $N(h) = N(h-1) + N(h-2) + 1$ (Fibonacci). 2) Rotacije: preverjaj od spodaj navzgor. Prvo vozlišče z $|b| = 2$ je mesto rotacije. 3) Brisanje: lahko več rotacij po celotni poti (vstavljanje: dovolj ena/dvojna).

\textbf{Segmentno drevo:} Če $n$ ni potenca 2, dopolnimo z nevtralnimi elementi. Število vozlišč: $\approx 2n$. Poizvedba \texttt{query(l,r)}: razbije interval na $O(\log n)$ kanoničnih vozlišč.

\textbf{Razno:} Amortizirana zahtevnost: Splay: posamezna $O(n)$, zaporedje $M$ operacij $O(M \log n)$. B-drevesa: majhna višina (velik razvejanost), minimizira dostope do diska.

\section*{Osnove grafov}

Graf $G = (V, E)$: vozlišča ($V$) in povezave ($E$). $n = |V|$, $m = |E|$.

\textbf{Predstavitve:}

\begin{tabular}{@{}lcc@{}}
\toprule
Lastnost & Seznam sosedov & Matrika \\
\midrule
Prostor & $O(V + E)$ & $O(V^2)$ \\
Preverjanje & $O(\text{stopnja})$ & $O(1)$ \\
Vsi sosedje & Hitro & Počasno ($O(V)$) \\
Uporaba & BFS, DFS, Dijkstra & Floyd-Warshall \\
\bottomrule
\end{tabular}

\vspace{2pt}

\textbf{BFS (Iskanje v širino):} Vrsta (FIFO). Najde najkrajšo pot (najmanj povezav) v neuteženih grafih. $O(V + E)$.

\textbf{DFS (Iskanje v globino):} Sklad/rekurzija. Raziskovanje strukture (komponente, cikli). $O(V + E)$.

\textbf{Detekcija ciklov:} \textit{Neusmerjeni:} Cikel če obiščemo že obiskano vozlišče ki ni neposredni starš. \textit{Usmerjeni:} Cikel če naletimo na vozlišče v rekurzivnem skladu (povratna povezava).

\textbf{Topološko urejanje:} Samo na DAG. Linearna ureditev: če $u \to v$, potem $u$ pred $v$. Kahnov algoritem: Vhodne stopnje (\texttt{indegree}). Vozlišča z \texttt{indegree == 0} v vrsto, odstranjujemo, sosedom zmanjšujemo \texttt{indegree}.

\textbf{Kritična pot (Najdaljša v DAG):} V splošnih grafih NP-težek, v DAG z dinamičnim programiranjem. Uredi topološko, $d(u) = \max(w(u,v) + d(v))$.

\textbf{Eulerjev obhod:} Vsaka povezava natanko enkrat, isto vozlišče. Pogoj: povezan graf, vsa vozlišča sodo stopnjo (usmerjeni: $indegree(v) = outdegree(v)$).

\section*{Izpitni namigi (Grafi)}

1. \textbf{Lema o rokovanju:} $\sum deg(v) = 2|E|$. Vsota stopenj je sodo število.

2. \textbf{Drevesa:} Povezan, brez ciklov. $|E| = |V| - 1$.

3. \textbf{Dvodelnost:} BFS/DFS z dvema barvama. Graf dvodelen $\iff$ nima lihih ciklov.

4. \textbf{Zahtevnost:} Matrika sosednosti: BFS/DFS $O(V^2)$. Seznam sosedov: $O(V + E)$.

5. \textbf{Povezanost:} Neusmerjeni: povezane komponente. Usmerjeni: krepko povezane komponente (pot $u \to v$ in $v \to u$).

6. \textbf{Euler vs Hamilton:} Euler: vsaka povezava enkrat (preveri stopnje). Hamilton: vsako vozlišče enkrat (NP-poln).

7. \textbf{Enostaven graf:} Brez zank in vzporednih povezav.

\section*{Kruskalov algoritem}

\textbf{MST (Minimum Spanning Tree)} v povezanem, neusmerjenem, uteženem grafu.

\textbf{Postopek:} 1) Prazna množica $A$, vsako vozlišče svoja disjunktna množica. 2) Povezave sortirane naraščajoče. 3) Za vsako $(u,v)$: če \texttt{FIND-SET(u)} $\neq$ \texttt{FIND-SET(v)}, dodaj v $A$, \texttt{UNION(u,v)}. Če ista komponenta, zavrži (cikel). 4) Končaj ko $V-1$ povezav.

\textbf{Zahtevnost:} Požrešni. Sortiranje: $O(E \log E) = O(E \log V)$. Union-Find (stiskanje poti, združevanje po rangu): $O(E \cdot \alpha(V))$. Skupaj: $O(E \log E)$. Učinkovit za redke grafe.

\textbf{Prostor:} $O(E + V)$.

\textbf{Lastnosti:} Eksplicitno preprečuje cikle. Gradi "gozd" dreves. Osredotočen na povezave (Prim na vozlišča).

\section*{Primov algoritem}

MST. Dve množici: vključena v MST, še ne vključena. Išče najcenejšo povezavo med množicama.

\textbf{Postopek:} 1) Začetno vozlišče $s$, $key[v] = \infty$, $key[s] = 0$, $parent[v] = NIL$. Vsa vozlišča v prioritetno vrsto $Q$ (prioriteta $key$). 2) Dokler $Q$ ni prazna: izloči $u$ z min $key$ (dodano v MST). Za vsakega soseda $v$ v $Q$: če $w(u,v) < key[v]$, posodobi $parent[v]=u$, $key[v]=w(u,v)$, \texttt{DECREASE-KEY}. 3) $parent$ definira robove MST.

\textbf{Zahtevnost:} Gosti graf ($E \approx V^2$): matrika sosednosti, linearno iskanje min. Iskanje min: $O(V^2)$. Posodabljanje: $O(E)$. Skupaj $O(V^2)$. Redki graf: seznam sosedov, binarna kopica. Ekstrakcija min: $V \cdot O(\log V)$. Zmanjšanje ključa: $E \cdot O(\log V)$. Skupaj $O(E \log V)$.

\textbf{Prostor:} Matrika: $O(V^2)$. Seznam: $O(V+E)$ plus $O(V)$ za algoritem.

\section*{Dijkstrov algoritem}

\textbf{SSSP} (najkrajše poti iz enega izvora). Ne-negativne uteži.

\textbf{Postopek:} 1) Začetno $s$, $dist[v]=\infty$, $dist[s]=0$, $parent[v]=NIL$. Vsa vozlišča v $Q$ (prioriteta $dist$). 2) Dokler $Q$ ni prazna: izloči $u$ z min $dist$ (fiksirano). Za vsakega soseda $v$: sproščanje -- če $dist[u]+w(u,v) < dist[v]$, posodobi $parent[v]=u$, $dist[v]=\dots$, \texttt{DECREASE-KEY}. 3) $dist$ vsebuje dolžine, $parent$ strukturo poti.

\textbf{Zahtevnost:} Požrešni. Deluje le če uteži $\geq 0$. Gosti: matrika, linearno iskanje min. $O(V^2)$. Redki: seznam sosedov, binarna kopica. $O(E \log V)$ (s Fibonaccijevo kopico $O(E + V \log V)$).

\textbf{Prostor:} Matrika: $O(V^2)$. Seznam: $O(V+E)$. Dodatno: $O(V)$.

\section*{Bellman-Fordov algoritem}

\textbf{SSSP}. Dopušča negativne uteži in zna zaznati negativne cikle.

\textbf{Postopek:} 1) Začetno $s$, $dist[v]=\infty$, $dist[s]=0$, $parent[v]=NIL$. 2) Ponovi $(|V|-1)$-krat: za vsako povezavo $(u,v)$: sproščanje -- če $dist[u]+w(u,v) < dist[v]$, posodobi $dist$ in $parent$. 3) Preverjanje negativnih ciklov: še enkrat skozi vse povezave. Če se lahko še izboljša $\to$ negativni cikel dosegljiv iz izvora.

\textbf{Zahtevnost:} Dinamično programiranje. $(V-1)$ iteracij $\times$ $E$ povezav. $O(V \cdot E)$. Polni grafi: $O(V^3)$. Počasnejši od Dijkstre, nujen za negativne uteži.

\textbf{Prostor:} $O(V+E)$ za graf, $O(V)$ za \texttt{dist} in \texttt{parent}.

\section*{Floyd-Warshallov algoritem}

\textbf{APSP} (najkrajše poti med vsemi pari).

\textbf{Postopek:} 1) Matrika $D$ dimenzije $V \times V$. $D[i][j]=0$ če $i=j$, $w(i,j)$ če povezava, $\infty$ sicer. 2) Tri gnezdeni zanke: za vsako vmesno $k$, za vsak začetek $i$, za vsak konec $j$: če $D[i][k] + D[k][j] < D[i][j]$, posodobi $D[i][j]$. 3) Če $D[i][i] < 0$ $\to$ negativni cikel.

\textbf{Zahtevnost:} Dinamično programiranje. Tri zanke do $V$. $O(V^3)$. Neodvisno od $E$, učinkovit za goste grafe.

\textbf{Prostor:} $O(V^2)$ (matrika razdalj).

\textbf{Lastnosti:} Deluje z negativnimi utežmi. Zazna negativne cikle. Najboljša izbira za vse razdalje, zmerno $V$.

\section*{BFS (podrobno)}

\textbf{SSSP} v neuteženem grafu (vse uteži enake). Obiskuje v nivojih.

\textbf{Postopek:} 1) Začetno $s$, $dist[v]=\infty$, barva BELA, $dist[s]=0$, barva SIVA, $parent[v]=NIL$. Vrsta $Q$ z $s$. 2) Dokler $Q$ ni prazna: vzemi $u$ iz vrste. Za vsakega soseda $v$: če BELA, spremeni v SIVA, $dist[v]=dist[u]+1$, $parent[v]=u$, dodaj v $Q$. $u$ postane ČRNA. 3) $dist$ = najmanjše število povezav.

\textbf{Zahtevnost:} $O(V+E)$. Matrika sosednosti: $O(V^2)$.

\textbf{Prostor:} Seznam sosedov: $O(V+E)$. Dodatno: $O(V)$.

\section*{DFS (podrobno)}

Sistematičen pregled. Prodira čim globje, nato se vrne (backtracking). Uporaba: topološko urejanje, krepko povezane komponente, cikli.

\textbf{Postopek:} 1) Vsa vozlišča BELA, $parent[v]=NIL$, \texttt{time}=0. 2) Za vsako $u$: če BELA, \texttt{DFS-VISIT(u)}. 3) \texttt{DFS-VISIT(u)}: \texttt{time++}, $d[u]=\texttt{time}$ (čas odkritja), SIVA. Za vsakega soseda $v$: če BELA, $parent[v]=u$, \texttt{DFS-VISIT(v)}. Ko vsi sosedje: ČRNA, \texttt{time++}, $f[u]=\texttt{time}$ (čas zaključka).

\textbf{Zahtevnost:} $O(V+E)$. Matrika: $O(V^2)$.

\textbf{Prostor:} Seznam sosedov: $O(V+E)$. Dodatno: $O(V)$ za polja + sklad rekurzije $O(V)$.

\textbf{Klasifikacija povezav:} \textit{Drevesne:} $v$ prvič obiskan preko $u$. \textit{Povratne:} $v$ prednik $u$ (kažejo na cikel). \textit{Prečne/Napredne:} med vejami ali proti potomcem.

\section*{Podatkovne strukture}

\textbf{1. Polje/Vector:} Strnjen pomnilnik, dostop $O(1)$. \texttt{std::vector}: amortizirano dodajanje $O(1)$ (podvoji velikost). Uporaba: kumulativne vsote, implementacija kopic.

\textbf{2. Sklad (Stack):} LIFO. Uporaba: rekurzija, Grahamov pregled (konveksna ovojnica), DFS. Implementacija: povezan seznam/vector, vse $O(1)$.

\textbf{3. Vrsta (Queue):} FIFO. Uporaba: BFS, upravljanje nalog. Implementacija: krožno polje, povezan seznam. Simulacija z dvema skladoma.

\textbf{4. Povezani seznam:} Vozlišča z kazalcem na naslednika. Hitro vstavljanje/brisanje $O(1)$ (če imamo kazalec). Počasen dostop do $i$-tega elementa $O(n)$.

\textbf{5. Vrsta s prednostjo/Priority Queue:} Vedno vrne element z najvišjo prioriteto. Implementacija: dvojiška kopica (heap). Uporaba: Dijkstra ($O(e \log n)$), Prim, Heapsort. Majhen nabor prioritet (1 do $K$): implementacija s poljem vrst, hitrejše. Zgraditev kopice: $O(n)$ (Floydov algoritem).

\textbf{6. Slovar/Map, Hash Table:} Pari ključ-vrednost. Zgoščena tabela: pričakovano $O(1)$, najslabši primer počasen (trki). Uravnotežena drevesa (\texttt{std::map}): $O(\log n)$, prostorsko učinkovitejša. Uporaba: hitro iskanje, memoizacija pri DP.

\textbf{7. Preskočni seznam (Skip List):} Povezan seznam z več nivoji bližnjic. Pričakovano iskanje/vstavljanje $O(\log n)$. Z informacijo o številu preskočenih elementov: indeksiranje $i$-tega elementa v $O(\log n)$.

\end{multicols}
\end{document}