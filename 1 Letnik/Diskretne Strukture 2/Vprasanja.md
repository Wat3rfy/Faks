Seveda, tukaj so vprašanja za pripravo na izpit, ki pokrivajo celotno vsebino vaših zapiskov. Vprašanja so v slovenščini in uporabljajo LaTeX markdown za matematične izraze.

---

## Vprašanja za pripravo na izpit iz Diskretnih struktur

### 1. Osnovne definicije in predstavitve grafov

1.  Kaj je graf? Zapišite formalno definicijo grafa $G$.
2.  Kaj je množica vozlišč $V$ in kaj množica povezav $E$? Kako so elementi množice $E$ definirani za enostaven graf?
3.  Kaj pomeni, da je graf **enostaven**?
4.  Kako lahko zapišemo povezavo med vozliščema $u$ in $v$?
5.  Definirajte **stopnjo vozlišča** $\deg_G u$.
6.  Kaj sta **maksimalna stopnja** $\Delta(G)$ in **minimalna stopnja** $\delta(G)$ grafa?
7.  Kaj je **izolirano vozlišče**?
8.  Kdaj sta dve povezavi **incidenčni**?
9.  Opišite **matriko sosednosti** grafa. Kakšne so njene lastnosti (velikost, simetričnost, diagonala, vsota vrstic/stolpcev)?
10. Opišite **incidenčno matriko** grafa. Kakšne so njene lastnosti (velikost, vsota stolpcev, vsota vrstic)?
11. Kako lahko graf predstavimo z **seznamom sosedov**? Definirajte $N_G(v)$.

### 2. Izrek o rokovanju in njegove posledice

1.  Navedite in **dokažite Izrek o rokovanju**. Zapišite formulo.
2.  Kaj je posledica Izreka o rokovanju glede števila vozlišč lihe stopnje? **Dokažite** to posledico.
3.  Kaj pomeni, da je graf **$k$-regularen**?
4.  Kateri grafi so **kubični**?

### 3. Podgrafi in komplement grafa

1.  Definirajte **podgraf** $H$ grafa $G$.
2.  Kaj je **vpet podgraf**?
3.  Kaj je **induciran podgraf**?
4.  Definirajte **komplement grafa** $\overline{G}$.

### 4. Sprehodi, poti, cikli in razdalje

1.  Definirajte **sprehod** v grafu. Kaj je **dolžina sprehoda**?
2.  Kaj je **sklenjen sprehod**?
3.  Kaj je **enostaven sprehod**?
4.  Definirajte **pot** v grafu.
5.  Definirajte **cikel** v grafu.
6.  Kaj implicira obstoj sprehoda od $u$ do $v$ glede na poti?
7.  Kaj implicira obstoj dveh različnih poti med $u$ in $v$ glede na cikle?
8.  Definirajte **razdaljo med vozliščema** $d(u,v)$. Kdaj je $d(u,v) = \infty$?
9.  Kdaj je graf **povezan**?
10. Kaj je **komponenta grafa**?
11. Kaj je **število komponent** $\Omega(G)$?
12. Kako definiramo **relacijo med vozlišči** glede na poti? Zakaj je ta relacija ekvivalenčna?
13. Kaj so **ekvivalenčni razredi** te relacije?
14. Definirajte **ekscentričnost** vozlišča $\text{ecc}(u)$.
15. Definirajte **diameter** grafa $\text{diam}(G)$.
16. Definirajte **radij** grafa $\text{rad}(G)$.
17. Kaj je **metrični prostor**? Navedite štiri lastnosti metrike $d$.
18. Navedite primer **Evklidskega prostora** in **Diskretnega metričnega prostora**.
19. Pokažite, da $(G, d)$ tvorita metrični prostor, kjer je $d$ dolžina najkrajše poti.

### 5. Dvodelni grafi

1.  Definirajte **dvodelen (bipartiten) graf**.
2.  Kaj je **Izrek o segregaciji**?
3.  **Dokažite**, da če v $G$ obstaja sklenjen sprehod lihe dolžine, obstaja tudi cikel lihe dolžine.
4.  **Dokažite**, da je graf dvodelen natanko tedaj, ko ne vsebuje nobenega lihega cikla.
5.  Kaj je **ožina** grafa $g(G)$?

### 6. Homomorfizmi in izomorfizmi grafov

1.  Definirajte **homomorfizem grafov** $\varphi: G \rightarrow H$.
2.  Kaj je **epimorfizem**?
3.  Kaj je **monomorfizem** oz. **vložitev**?
4.  Kaj je **izometrična vložitev**?
5.  Definirajte **izomorfizem** grafov. Kdaj pišemo $G \cong H$?
6.  Kaj je **avtomorfizem** grafa?
7.  Kaj je $\text{Avt}(G)$? Koliko je $|\text{Avt}(K_n)|$ in $|\text{Avt}(C_n)|$?
8.  Pojasnite razlike med homomorfizmom, epimorfizmom, monomorfizmom, izometrično vložitvijo, izomorfizmom in avtomorfizmom v tabeli.
9.  **Dokažite**, da če sta $\varphi_1: G_1 \rightarrow G_2$ in $\varphi_2: G_2 \rightarrow G_3$ homomorfizma, je tudi $\varphi_2 \circ \varphi_1$ homomorfizem.
10. **Dokažite**, da velja $\text{Avt}(G) = \text{Avt}(\overline{G})$.
11. **Dokažite**, da če $G$ ni povezan, potem je $\text{diam}(\overline{G}) \leq 2$.
12. Kaj je posledica prejšnjega izreka glede povezanosti $G$ in $\overline{G}$?

### 7. Povezanost in Mengerjev izrek

1.  Definirajte **odstranjevanje povezav** $G-F$.
2.  Definirajte **odstranjevanje vozlišč** $G-U$.
3.  Kako je podgraf $H$ povezan z operacijama odstranjevanja?
4.  Opišite postopek **skrčitve povezave** $e$ ($G \backslash e$).
5.  Kaj je **minor** grafa $G$? Navedite primer.
6.  Kaj je **subdivizija** grafa $G$?
7.  Kaj je **glajenje povezav**?
8.  Kdaj sta grafa **homeomorfna**?
9.  Definirajte **prerezno vozlišče**.
10. Definirajte **prerezno povezavo**.
11. **Dokažite**, da se pri prereznem vozlišču število komponent lahko poveča za največ $\deg(v)-1$, pri prerezni povezavi pa za največ 1.
12. Kaj je **prerezna množica** $S \subset V(G)$?
13. Kaj je **povezavno prerezna množica** $F \subset E(G)$?
14. Definirajte **$k$-povezan graf**.
15. Kaj je $\mathcal{K}(G)$? Navedite $\mathcal{K}(P_n)$, $\mathcal{K}(C_n)$ in $\mathcal{K}(K_n)$.
16. Kdaj sta poti $P_1$ in $P_2$ **notranje disjunktni**?
17. Navedite **Whitnejev izrek**.
18. Navedite in **dokažite Mengerjev izrek** (globalno različico).
19. Navedite **Mengerjev izrek (lokalno različico)**.

### 8. Drevesa in gozdovi

1.  Kaj je **gozd**?
2.  Kaj je **drevo**?
3.  Kaj so **komponente gozda**?
4.  Kaj je **list** v drevesu?
5.  **Dokažite**, da ima vsako drevo z vsaj 2 vozliščema list.
6.  Zapišite formulo za število povezav v gozdu glede na število vozlišč in komponent. **Dokažite** jo.
7.  Koliko listov ima drevo z vsaj 2 vozliščema?
8.  Kaj velja za povezanost grafa $G \backslash e$, če je $e$ povezava na nekem ciklu v $G$?
9.  Kdaj je graf drevo glede na število povezav in vozlišč?
10. Navedite ekvivalentne trditve za drevo.
11. Kaj je **most** v grafu?
12. Kaj je **vpeto drevo** grafa $G$?
13. Kaj je $\tau(G)$?
14. **Dokažite**, da je graf povezan natanko tedaj, ko obstaja vpeto drevo $G$.
15. Navedite **rekurzivno zvezo za $\tau(G)$** za multigraf. **Pojasnite intuicijo** za to formulo.
16. Kaj je **Laplaceova matrika** $L(G)$? Kako so definirani njeni elementi?
17. Navedite lastnosti Laplaceove matrike.
18. Kako je determinanta $L_{ii}$ povezana s številom vpetih dreves?
19. Navedite in **dokažite Cayleyjev izrek**. Opišite **Pruferjevo kodiranje** in njegovo vlogo pri dokazu.

### 9. Eulerjevi in Hamiltonovi grafi

1.  Kaj je **Eulerjev sprehod**?
2.  Kaj je **Eulerjev obhod**?
3.  Kdaj je graf **eulerjev**?
4.  **Dokažite**, da je povezan graf eulerjev natanko tedaj, ko so vsa vozlišča soda.
5.  Kdaj ima graf Eulerjev sprehod?
6.  Kaj je **Hamiltonova pot**?
7.  Kaj je **Hamiltonov cikel**?
8.  Kdaj je graf **hamiltonov**?
9.  Navedite pogoj za hamiltonov graf glede na odstranjevanje vozlišč $S$. **Dokažite** ga.
10. Kaj implicira pogoj $\Omega(G-S) > |S|$?
11. Kaj implicira pogoj $\Omega(G-S) > |S|+1$?
12. Kdaj je polni dvodelni graf $K_{m,n}$ hamiltonov?
13. Kaj velja za velikosti particij $|X|$ in $|Y|$, če je dvodelen graf hamiltonov?
14. Navedite izrek o hamiltonovosti grafa, ki vključuje vsoto stopenj nepovezanih vozlišč.
15. Navedite **Orejev izrek**.
16. Navedite **Diracov izrek**. Kako ga lahko zapišemo z $\delta(G)$?

### 10. Znani/pomembni grafi

Za vsak od naslednjih grafov opišite:
*   Množico vozlišč $V$ in povezav $E$.
*   Število povezav $|E|$.
*   Ključne lastnosti (npr. povezanost, regularnost, premer, dvodelnost, hamiltonovost, eulerjevost).

1.  **Polni graf** $K_n$.
2.  **Pot** $P_n$.
3.  **Cikel** $C_n$.
4.  **Hiperkocka** $Q_n$.
5.  **Polni dvodelni graf** $K_{m,n}$.
6.  **Posplošeni Petersonov graf** $P_{n,k}$. Opišite tudi klasični Petersonov graf $P_{5,2}$.

### 11. Ravninski grafi

1.  Kaj je **ravninski graf**? Kako je definirana preslikava $\varphi$ in $\Psi_e$?
2.  Kaj pravi **Jordanov izrek**?
3.  Kaj so **lica** grafa?
4.  Kaj je **dolžina lica** $l(f)$?
5.  Kaj velja za vsoto dolžin vseh lic v grafu? Zapišite formulo.
6.  Kako je ožina grafa $g(G)$ povezana z dolžino lic?
7.  Navedite **Eulerjevo formulo** za ravninske grafe. **Pojasnite** njene komponente.
8.  Navedite neenakost za število povezav v ravninskem grafu, ki ni gozd, glede na ožino in število vozlišč.
9.  Kaj implicira, če je ravninski graf z vsaj 3 vozlišči brez trikotnikov?
10. Kaj implicira, če je ravninski graf z vsaj 3 vozlišči in ima trikotnike?
11. Katera dva grafa nista ravninska?
12. Navedite **Kuratowskijev izrek**.
13. Navedite **Wagnerjev izrek**.

### 12. Barvanje grafov (vozlišča)

1.  Kaj je **barvanje grafa** $b: V(G) \rightarrow K$?
2.  Kdaj je barvanje **dobro**?
3.  Kaj je **kromatično število** $\chi(G)$?
4.  Navedite kromatična števila za $K_n$, $\overline{K_n}$, $P_n$, $C_n$.
5.  Kdaj je $\chi(G) \leq 2$?
6.  **Dokažite**, da če je $H$ podgraf $G$, potem $\chi(H) \leq \chi(G)$.
7.  Kaj je **klika** grafa?
8.  Kaj je **velikost največje klike** $\omega(G)$?
9.  Navedite neenakost, ki povezuje $\omega(G)$, $\chi(G)$ in $\Delta(G)$. Pojasnite, zakaj velja.
10. Kaj velja za $\chi(G)$ in $\Delta(G)$ za povezan graf, ki ni lih cikel ali polni graf?

### 13. Kromatični polinom

1.  Kaj je **kromatični polinom** $P_G(k)$?
2.  Navedite kromatične polinome za $N_n$ (graf brez povezav z $n$ vozlišči) in $K_n$.
3.  Izračunajte kromatični polinom za $P_3$.
4.  Navedite **rekurzivno zvezo za $P_G(k)$** glede na odstranitev in skrčitev povezave. **Pojasnite** jo.
5.  Navedite lastnosti kromatičnega polinoma $P_G(k)$ (stopnja, vodilni koeficient, konstantni člen, koeficient pri $k^{n-1}$, alternacija predznakov).

### 14. Barvanje grafov (povezave)

1.  Kaj je **dobro barvanje povezav grafa**?
2.  Kaj je **kromatični indeks** $\chi'(G)$?
3.  Navedite kromatične indekse za $P_n$, $C_n$, $K_1, K_2, K_3, K_4, K_5, K_6$.
4.  Navedite neenakost, ki povezuje $\chi'(G)$ in $\Delta(G)$.
5.  Navedite **Vizingov izrek**.
6.  Kaj pomeni, da je graf **razreda 1** ali **razreda 2**?
7.  Kaj velja za kromatični indeks dvodelnega grafa?
8.  Kaj velja za kromatični indeks regularnega grafa na lihih vozliščih?

### 15. Neodvisne in dominantne množice

1.  Definirajte **neodvisno množico** $U \subseteq V(G)$.
2.  Kaj je $\alpha(G)$?
3.  Definirajte **dominantno množico** $U \subseteq V(G)$.
4.  Kaj je $\gamma(G)$?
5.  Navedite neenakost za $\alpha(G)$ glede na $|V(G)|$, $\chi(G)$, $|E(G)|$ in $\Delta(G)$.
6.  Navedite neenakost za $\gamma(G)$ glede na $|V(G)|$ in $\Delta(G)$, če graf nima izoliranih vozlišč.
7.  Kako sta povezani $\alpha(G)$ in $\omega(\overline{G})$?
8.  Navedite neenakost, ki povezuje $\gamma(G)$, $\alpha(G)$, $\omega(\overline{G})$ in $\chi(\overline{G})$.

### 16. Produkti grafov

1.  Kaj je skupna lastnost množice vozlišč vseh treh produktov grafov $G$ in $H$?
2.  Definirajte **kartezični produkt** $G \square H$. Narišite $K_2 \square K_2$.
3.  Definirajte **direktni produkt (tenzorski produkt)** $G \times H$. Narišite $K_2 \times K_2$.
4.  Definirajte **močni produkt** $G \boxtimes H$. Narišite $K_2 \boxtimes K_2$.
5.  Kaj velja za asociativnost in komutativnost teh produktov?
6.  Zapišite formulo za razdaljo v **kartezičnem produktu** $d_{G \square H}((g, h), (g', h'))$. Pojasnite intuicijo.
7.  Zapišite formulo za razdaljo v **močnem produktu** $d_{G \boxtimes H}((g, h), (g', h'))$. Pojasnite intuicijo.
8.  Zapišite formulo za razdaljo v **direktnem produktu** $d_{G \times H}((g, h), (g', h'))$. Pojasnite posledice glede paritete in dolžine poti/sprehodov.
9.  Navedite **Weichselov izrek** o povezanosti direktnega produkta. Pojasnite oba dela izreka.
10. Kaj je posledica Weichselovega izreka za povezanost kartezičnega in močnega produkta več grafov?
11. Zapišite formulo za razdaljo v **kartezičnem produktu več grafov**.
12. Zapišite formulo za razdaljo v **močnem produktu več grafov**.
13. Kaj je posledica Weichselovega izreka za povezanost **direktnega produkta več grafov**?

---

1. Koliko najmanj potez potrebujemo da narišemo graf?