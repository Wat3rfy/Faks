Tukaj je povzetek informacijske vsebine iz diapozitivov, pretvorjen v LaTeX markdown za matematične izraze:

# Singularni razcep - 3. del

## 9. Kovariančna in korelacijska matrika

Najprej osvežimo osnovne pojme iz opisne statistike. Ponavljamo poskus in beležimo podatke na merilnih napravah. Dobimo **tabelo podatkov**.
Če imamo eno merilno napravo, ima tabela podatkov en stolpec podatkov:
```
ponovitev | podatek
----------|--------
1.        | x_1
2.        | x_2
...       | ...
n-ta      | x_n
```
Za ta stolpec izračunamo povprečje $\overline{x} = \frac{x_1 + \dots + x_n}{n}$.

Če nas zanima razpršenost podatkov okrog povprečja, potem najprej izračunamo **odmike podatkov od povprečja**, se pravi števila $x_i' = x_i - \overline{x}$. Dobimo **centralizirano tabelo podatkov**:
```
ponovitev | centralizirani podatek
----------|----------------------
1.        | x_1' = x_1 - \overline{x}
2.        | x_2' = x_2 - \overline{x}
...       | ...
n-ta      | x_n' = x_n - \overline{x}
```
Povprečen odmik od povprečja ni dobra mera za razpršenost, saj velja $\frac{x_1' + \dots + x_n'}{n} = \frac{(x_1 - \overline{x}) + \dots + (x_n - \overline{x})}{n} = \frac{(x_1 + \dots + x_n) - n\overline{x}}{n} = \overline{x} - \overline{x} = 0$.

Boljša mera za razpršenost podatkov je kvadratična sredina odmikov:
$s = \sqrt{\frac{1}{n} \sum_{i=1}^n (x_i')^2} = \sqrt{\frac{1}{n} \sum_{i=1}^n (x_i - \overline{x})^2}$.
Temu številu pravimo **standardna deviacija** stolpca podatkov.
Če vse elemente v centralizirani tabeli podatkov delimo z $s$ dobimo **standardizirano tabelo podatkov**:
```
ponovitev | standardizirani podatek
----------|----------------------
1.        | x_1'' = x_1'/s = (x_1 - \overline{x})/s
2.        | x_2'' = x_2'/s = (x_2 - \overline{x})/s
...       | ...
n-ta      | x_n'' = x_n'/s = (x_n - \overline{x})/s
```
Povprečje standardizirane tabele podatkov je 0, njena standardna deviacija pa je 1, saj je $\sqrt{\frac{1}{n} \sum_{i=1}^n (x_i'')^2} = \sqrt{\frac{1}{n} \sum_{i=1}^n (x_i'/s)^2} = \sqrt{\frac{1}{ns^2} \sum_{i=1}^n (x_i')^2} = \sqrt{\frac{s^2}{s^2}} = 1$.

Če imamo dve merilni napravi, ima tabela podatkov dva stolpca podatkov:
```
ponovitev | podatek prve merilne naprave | podatek druge merilne naprave
----------|------------------------------|-------------------------------
1.        | x_1                          | y_1
2.        | x_2                          | y_2
...       | ...                          | ...
n-ta      | x_n                          | y_n
```
Če stolpca centraliziramo, dobimo **centralizirano tabelo podatkov**. Če ju standardiziramo, dobimo **standardizirano tabelo podatkov**.
Še bolj nas zanima koliko so podatki v enem stolpcu odvisni od podatkov v drugem stolpcu. Stopnjo odvisnosti merimo s **kovarianco**:
$K = \frac{1}{n} \sum_{i=1}^n (x_i - \overline{x})(y_i - \overline{y}) = \frac{1}{n} \sum_{i=1}^n x_i'y_i'$.
Če so podatki prve merilne naprave neodvisni od podatkov druge merilne naprave, je kovarianca enaka nič. Obratno ne velja.

**Opomba:** Pojem kovariance je tesno povezan s pojmom regresijske premice. Njen smerni koeficient je $k = \frac{\overline{xy} - \overline{x}\overline{y}}{\overline{x^2} - \overline{x}^2}$. Pokažimo, da je števec tega izraza ravno kovarianca. Velja namreč:
$\frac{1}{n} \sum_{i=1}^n (x_i - \overline{x})(y_i - \overline{y}) = \frac{1}{n} \sum_{i=1}^n (x_iy_i - x_i\overline{y} - \overline{x}y_i + \overline{x}\overline{y}) = \overline{xy} - \overline{x}\overline{y} - \overline{x}\overline{y} + \overline{x}\overline{y} = \overline{xy} - \overline{x}\overline{y}$.
Skoraj enak račun nam pokaže, da je imenovalec enak $s_1^2$, kjer je $s_1$ standardna deviacija prvega stolpca. Velja torej $k = \frac{K}{s_1^2}$.

S pomočjo kovariance in standardnih deviacij obeh stolpcev lahko definiramo **kovariančno matriko**:
$C = \begin{bmatrix} s_1^2 & K \\ K & s_2^2 \end{bmatrix}$.
Če vstavimo definicije $s_1, s_2$ in $K$, dobimo:
$C = \begin{bmatrix} \frac{1}{n}\sum_{i=1}^n (x_i')^2 & \frac{1}{n}\sum_{i=1}^n x_i'y_i' \\ \frac{1}{n}\sum_{i=1}^n x_i'y_i' & \frac{1}{n}\sum_{i=1}^n (y_i')^2 \end{bmatrix} = \frac{1}{n} \begin{bmatrix} x_1' & y_1' \\ \vdots & \vdots \\ x_n' & y_n' \end{bmatrix}^T \begin{bmatrix} x_1' & y_1' \\ \vdots & \vdots \\ x_n' & y_n' \end{bmatrix} = \frac{1}{n} (X')^T X'$,
kjer je $X'$ matrika centraliziranih podatkov.
**Opomba:** Matriko $X'$ dobimo tako, da v matriki rezultatov $X$, od vsakega elementa odštejemo povprečje stolpca v katerem se nahaja.

Opazimo, da se kovarianca vedno nahaja med $-s_1s_2$ in $s_1s_2$. To sledi iz Cauchy-Schwartzove neenakosti: $|\sum x_i'y_i'| \le \sqrt{\sum (x_i')^2} \sqrt{\sum (y_i')^2}$.
Če obe strani delimo z $n = (\sqrt{n})^2$. Zato pridemo na idejo, da bi definirali:
$r = \frac{K}{s_1s_2}$.
Temu izrazu pravimo **korelacija** (ali korelacijski koeficient) obeh stolpcev v matriki podatkov. S standardiziranimi podatki se izraža takole:
$r = \frac{1}{n s_1s_2} \sum_{i=1}^n x_i'y_i' = \frac{1}{n} \sum_{i=1}^n x_i''y_i''$.
Torej je korelacija enaka nič natanko tedaj, ko sta stolpca v standardizirani tabeli podatkov ortogonalna.

Definirajmo še **korelacijsko matriko**:
$R = \begin{bmatrix} 1 & r \\ r & 1 \end{bmatrix}$.
Opazimo, da velja:
$R = \begin{bmatrix} \frac{1}{n}\sum_{i=1}^n (x_i'')^2 & \frac{1}{n}\sum_{i=1}^n x_i''y_i'' \\ \frac{1}{n}\sum_{i=1}^n x_i''y_i'' & \frac{1}{n}\sum_{i=1}^n (y_i'')^2 \end{bmatrix} = \frac{1}{n} (X'')^T X''$,
kjer je $X''$ matrika standardiziranih podatkov.
**Opomba:** Matriko $X''$ dobimo tako, da v matriki centraliziranih podatkov $X'$ vsak stolpec delimo z njegovo standardno deviacijo.

Posplošimo sedaj definicije iz dveh na $p$ merilnih naprav. Naj bo $x_{i,j}$ podatek $j$-te merilne naprave pri $i$-ti ponovitvi poskusa.
```
ponovitev | 1. merilnik | 2. merilnik | ... | p-ti merilnik
----------|--------------|--------------|-----|---------------
1.        | x_1,1        | x_1,2        | ... | x_1,p
2.        | x_2,1        | x_2,2        | ... | x_2,p
...       | ...          | ...          | ... | ...
n-ta      | x_n,1        | x_n,2        | ... | x_n,p
```
Za vsak stolpec v tabeli smo izračunali povprečje $\overline{x_j} = \frac{1}{n}\sum_{i=1}^n x_{i,j}$ in standardno deviacijo $s_j = \sqrt{\frac{1}{n}\sum_{i=1}^n (x_{i,j} - \overline{x_j})^2}$.

Matriki $X = [x_{i,j}]$ pravimo **matrika podatkov**. Njena velikost je $n \times p$, kjer je $n$ število ponovitev poskusa, $p$ pa število merilnih naprav.
Matriki $X' = [x_{i,j}']$, kjer je $x_{i,j}' = x_{i,j} - \overline{x_j}$, bomo rekli **centralizirana matrika podatkov**.
Matriki $X'' = [x_{i,j}'']$, kjer je $x_{i,j}'' = x_{i,j}'/s_j = (x_{i,j} - \overline{x_j})/s_j$, bomo rekli **standardizirana matrika podatkov**.

Kovarianca $j$-tega in $k$-tega stolpca matrike $X$ je enaka $C_{j,k} = \frac{1}{n} \sum_{i=1}^n (x_{i,j} - \overline{x_j})(x_{i,k} - \overline{x_k}) = \frac{1}{n} \sum_{i=1}^n x_{i,j}'x_{i,k}'$.
Opazimo, da je $C_{j,j} = s_j^2$, kjer je $s_j$ standardna deviacija $j$-tega stolpca matrike $X$. **Kovariančna matrika** $C = [C_{j,k}]$ zadošča $C = \frac{1}{n} (X')^T X'$.

Korelacija med $j$-tim in $k$-tim stolpcem matrike $X$ je enaka $r_{j,k} = C_{j,k}/(s_js_k)$.
Velja $-1 \le r_{j,k} \le 1$ in $r_{j,j} = 1$. **Korelacijska matrika** $R = [r_{j,k}]$ zadošča $R = \frac{1}{n} (X'')^T X''$.

## 10. Metoda glavnih komponent (PCA)

Naj bo $X'$ centralizirana matrika podatkov za nek poskus. (Pozor, nekateri raje delajo s standardizirano matriko podatkov $X''$.)
Radi bi zmanjšali število stolpcev matrike $X'$ (iz $p$ na $k$), ne da bi pri tem izgubili veliko informacij. Ideja je, da si zapomnimo samo take linearne kombinacije stolpcev matrike $X'$, ki imajo največjo standardno deviacijo.
Spomnimo se, da vsako linearno kombinacijo stolpcev $X'$ lahko zapišemo kot $X'w$ za nek vektor $w$. Ponavljamo naslednji postopek:
*   Poišči tak normiran vektor $w_1$, da ima vektor $y_1 := X'w_1$ največjo možno standardno deviacijo.
*   Med vsemi normiranimi vektorji, ki so ortogonalni na $w_1$, poišči tak vektor $w_2$, da ima $y_2 := X'w_2$ največjo možno standardno deviacijo.
*   Med vsemi normiranimi vektorji, ki so ortogonalni na $w_1$ in $w_2$, poišči tak vektor $w_3$, da ima $y_3 := X'w_3$ največjo možno standardno deviacijo.
...
Končamo, ko se $X'$ ujema z $y_1w_1^T + \dots + y_kw_k^T$ do predpisane natančnosti.

**Opomba:** Vektorjem $y_1, \dots, y_k$ bomo rekli **glavne komponente** matrike $X'$, vektorjem $w_1, \dots, w_k$ pa **glavne osi** matrike $X'$. Pozor, terminologija se zelo razlikuje od avtorja do avtorja.

### Trditev 1

Za vektorje $w_1, w_2, w_3, \dots$ lahko vzamemo kar lastne vektorje kovariančne matrike $C = \frac{1}{n}(X')^T X'$, ki ustrezajo prvi, drugi, tretji, $\dots$ največji lastni vrednosti.

**Opomba:** Lastni vektorji kovariančne matrike $C = \frac{1}{n}(X')^T X'$ se ujemajo z lastnimi vektorji matrike $(X')^T X'$, ti pa se ujemajo s stolpci matrike $Q_2$ v singularnem razcepu $X' = Q_1DQ_2^T$.

**Dokaz:**
Naj bodo $\lambda_1 \ge \dots \ge \lambda_p$ lastne vrednosti matrike $C$ in naj bodo $v_1, \dots, v_p$ pripadajoči ortonormirani lastni vektorji.
Vsak normiran vektor $w \in \mathbb{R}^p$ lahko zapišemo kot $w = \beta_1 v_1 + \dots + \beta_p v_p$, kjer je $\beta_1^2 + \dots + \beta_p^2 = 1$. Standardna deviacija vektorja $X'w$ je enaka:
$\sigma_{X'w} = \sqrt{\frac{1}{n}(X'w)^T(X'w)} = \sqrt{w^T \left(\frac{1}{n}(X')^T X'\right) w} = \sqrt{w^T C w}$.
$\sqrt{(\beta_1 v_1 + \dots + \beta_p v_p)^T C (\beta_1 v_1 + \dots + \beta_p v_p)} = \sqrt{\sum_{i=1}^p \beta_i^2 \lambda_i}$.
$\sqrt{\beta_1^2 \lambda_1 + \dots + \beta_p^2 \lambda_p}$.
Ker je $\beta_i^2 \ge 0$ in $\sum \beta_i^2 = 1$, je ta izraz maksimalen, ko je $\beta_1 = 1$ in $\beta_i = 0$ za $i \ne 1$. V tem primeru je vrednost $\sqrt{\lambda_1}$. Enačaj je očitno dosežen pri $w = v_1$. Torej lahko vzamemo $w_1 = v_1$.
Vsak normiran vektor $w \in \mathbb{R}^p$, ki je ortogonalen na $v_1$ lahko zapišemo kot $w = \gamma_2 v_2 + \dots + \gamma_p v_p$, kjer je $\gamma_2^2 + \dots + \gamma_p^2 = 1$. Standardna deviacija vektorja $X'w$ je enaka $\sqrt{\gamma_2^2 \lambda_2 + \dots + \gamma_p^2 \lambda_p}$.
Enačaj je dosežen pri $w = v_2$, zato lahko vzamemo $w_2 = v_2$. To lahko nadaljujemo.

### Trditev 3

Če je $i \ne j$, potem je kovarianca med stolpcema $y_i$ in $y_j$ enaka nič.

**Dokaz:**
Ker sta stolpca $y_i$ in $y_j$ linearni kombinaciji stolpcev matrike $X'$, sta njuni povprečji enaki nič. Torej je njuna kovarianca enaka:
$K = \frac{1}{n} \sum_{l=1}^n y_i^{(l)} y_j^{(l)} = \frac{1}{n} y_i^T y_j$.
$y_i = X'w_i$. $y_j = X'w_j$.
$K = \frac{1}{n} (X'w_i)^T (X'w_j) = \frac{1}{n} w_i^T (X')^T X' w_j = w_i^T C w_j$.
Ker sta $w_i$ in $w_j$ lastna vektorja matrike $C$, ki pripadata različnima lastnima vrednostma, sta ortogonalna. Torej $w_i^T C w_j = \lambda_j w_i^T w_j = 0$.
**Opomba:** Različne glavne komponente $X'$ so torej nekorelirane.

V nadaljevanje nas bo zanimalo, kolikšno napako naredimo, če matriko $X'$ zamenjamo z matriko $Y_k W_k^T$. Napako bomo merili s Frobeniusovo matrično normo.
Uvedimo nekaj oznak. Za vsak $k = 1, \dots, p$ naj bo $W_k = \begin{bmatrix} w_1 & \dots & w_k \end{bmatrix}$ in $Y_k = \begin{bmatrix} y_1 & \dots & y_k \end{bmatrix} = X'W_k$.
Očitno je $Y_k W_k^T = y_1 w_1^T + \dots + y_k w_k^T$.
Iskana napaka je torej $||X' - Y_k W_k^T||_F$.

### Trditev 4 (Geometrijski pomen $Y_k W_k^T$ in $||X' - Y_k W_k^T||_F$)

Če $i$-to vrstico matrike $X'$ ortogonalno projeciramo na podprostor $\mathrm{Lin}\{w_1^T, \dots, w_k^T\}$ v $\mathbb{R}^p$, potem dobimo ravno $i$-to vrstico matrike $Y_k W_k^T$. Vsota kvadratov oddaljenosti vrstic matrike $X'$ od njihovih ortogonalnih projekcij na podprostor $\mathrm{Lin}\{w_1^T, \dots, w_k^T\}$ je torej enaka $||X' - Y_k W_k^T||_F^2$.

**Dokaz:**
Vrstice matrik $X'$ in $Y_k W_k^T$ ter vektorji $w_1^T, \dots, w_k^T$ so vrstični vektorji dolžine $p$. Ker so $w_1, \dots, w_k$ ortonormirani, so tudi $w_1^T, \dots, w_k^T$ ortonormirani. Naj bo $x^{(i)}$ $i$-ta vrstica matrike $X'$. Njena ortogonalna projekcija na podprostor $\mathrm{Lin}\{w_1^T, \dots, w_k^T\}$ je enaka $\sum_{j=1}^k \langle x^{(i)}, w_j^T \rangle w_j^T$.
Najprej opazimo, da je skalarni produkt $\langle x^{(i)}, w_j^T \rangle$ enak matričnemu produktu $x^{(i)} w_j$. Poleg tega je
$\sum_{j=1}^k (x^{(i)} w_j) w_j^T = x^{(i)} \begin{bmatrix} w_1 & \dots & w_k \end{bmatrix} \begin{bmatrix} w_1^T \\ \vdots \\ w_k^T \end{bmatrix} = x^{(i)} W_k W_k^T$.
Tudi $i$-ta vrstica produkta $X'(W_kW_k^T)$ je enaka $x^{(i)} W_k W_k^T$.
Drugi del trditve sledi iz prvega dela in naslednjega računa. Za poljubni matriki $A$ in $B$ iste velikosti $n \times p$ velja:
$||A - B||_F^2 = \sum_{i=1}^n \sum_{j=1}^p (a_{i,j} - b_{i,j})^2 = \sum_{i=1}^n ||a^{(i)} - b^{(i)}||^2$.

### Trditev 5

Če so $\lambda_1 \ge \dots \ge \lambda_p$ lastne vrednosti kovariančne matrike $C = \frac{1}{n}(X')^T X'$, potem je $||X' - Y_k W_k^T||_F^2 = n(\lambda_{k+1} + \dots + \lambda_p)$.

**Dokaz:**
Izračunajmo razdaljo med $X'$ in $Y_k W_k^T$ v Frobeniusovi normi.
Naj bo $X' = UDV^T$ singularni razcep matrike $X'$. Potem so stolpci $U$ ortonormirani vektorji v $\mathbb{R}^n$, stolpci $V$ so ortonormirani vektorji v $\mathbb{R}^p$, diagonalna matrika $D$ vsebuje singularne vrednosti $\sigma_1 \ge \dots \ge \sigma_p \ge 0$.
Lastne vrednosti $C$ so povezane s singularnimi vrednostmi $X'$ z $\lambda_i = \sigma_i^2/n$. Torej so $w_i = v_i$.
$||X' - Y_k W_k^T||_F^2 = ||X' - U \begin{bmatrix} I_k & 0 \\ 0 & 0 \end{bmatrix} D W_k^T||_F^2$.
$Y_k W_k^T = X'V_k V_k^T = U D V^T V_k V_k^T = U D \begin{bmatrix} I_k & 0 \\ 0 & 0 \end{bmatrix} V^T$.
$||X' - Y_k W_k^T||_F^2 = ||U(D - D_k)V^T||_F^2 = ||D - D_k||_F^2$.
$||D - D_k||_F^2 = \sum_{i=k+1}^p \sigma_i^2 = n \sum_{i=k+1}^p \lambda_i = n(\lambda_{k+1} + \dots + \lambda_p)$.

Naslednja posledica Trditve 5 nam pove kako izbrati $k$, da dosežemo predpisano natančnost.

### Posledica

*   Če za nek $k$ velja $\lambda_{k+1} + \dots + \lambda_p \le \frac{\varepsilon^2}{n}$, potem je $||X' - Y_k W_k^T||_F \le \varepsilon$.
*   Če pa za nek $k$ velja $\frac{\lambda_{k+1} + \dots + \lambda_p}{\lambda_1 + \dots + \lambda_p} \le \varepsilon^2$, potem je $\frac{||X' - Y_k W_k^T||_F^2}{||X'||_F^2} \le \varepsilon^2$.

### Povzetek algoritma za računanje glavnih komponent

1.  Preberi matriko podatkov $X$ in predpisano relativno natančnost $\varepsilon$.
2.  Zapomni si povprečja stolpcev matrike $X$; $\overline{x} := \begin{bmatrix} \overline{x_1} & \dots & \overline{x_p} \end{bmatrix}$.
3.  Centraliziraj matriko podatkov; $X' := X - e\overline{x}^T$, kjer $e = \begin{bmatrix} 1 & \dots & 1 \end{bmatrix}^T$.
4.  Poišči singularni razcep $X' = UDV^T$, kjer za diagonalne elemente matrike $D$ (=singularne vrednosti matrike $X'$) velja $\sigma_1 \ge \dots \ge \sigma_p$.
5.  Poišči tak $k$, da velja $\frac{\sigma_{k+1}^2 + \dots + \sigma_p^2}{\sigma_1^2 + \dots + \sigma_p^2} \le \varepsilon^2$.
6.  Zapomni si prvih $k$ stolpcev matrike $V$ (= $W_k =$ glavne osi $X'$) in prvih $k$ stolpcev matrike $UD$ (= $Y_k =$ glavne komponente $X'$).
7.  Velja $\frac{||X' - Y_k W_k^T||_F^2}{||X'||_F^2} \le \varepsilon^2$. Torej je $Y_k W_k^T$ dober približek za $X'$.
Odtod sledi, da je $Y_k W_k^T + e\overline{x}^T$ dober približek za matriko $X$.