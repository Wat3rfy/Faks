### 6. Jordanska kanonična forma

**Definicija jordanske kletke in jordanske matrike**

Jordanska kletka je matrika oblike
$[\lambda]$, $\begin{bmatrix} \lambda & 1 \\ 0 & \lambda \end{bmatrix}$, $\begin{bmatrix} \lambda & 1 & 0 \\ 0 & \lambda & 1 \\ 0 & 0 & \lambda \end{bmatrix}$, ..., $\begin{bmatrix} \lambda & 1 & 0 & 0 \\ 0 & \lambda & 1 & 0 \\ 0 & 0 & \lambda & 1 \\ 0 & 0 & 0 & \lambda \end{bmatrix}$,
kjer je $\lambda$ kompleksno število.

Jordanska matrika je matrika oblike
$\begin{bmatrix} J_1 & & 0 \\ & \ddots & \\ 0 & & J_m \end{bmatrix}$,
kjer so $J_1, \dots, J_m$ jordanske kletke (lahko različnih velikosti in različnih $\lambda$).

**Izrek o jordanski kanonični formi**

Vsaka kompleksna kvadratna matrika $A$ je podobna kaki jordanski matriki $J$. Pravimo, da je $J$ jordanska kanonična forma za $A$.

**Opomba:** Jordanska kanonična forma matrike $A$ ni enolična. Če namreč permutiramo njene jordanske kletke, potem spet dobimo jordansko kanonično formo matrike $A$. S primerno permutacijo jordanskih kletk lahko dosežemo, da jordanske kletke z istim $\lambda$ sedijo skupaj in so urejene po velikosti od največje do najmanjše.

**Opomba:** Jordanska kanonična forma matrike $A$ je uporabna za računanje funkcij matrike $A$. To bomo spoznali v naslednjem razdelku.

**Definicija jordanske verige**

Naj bo $\lambda$ lastna vrednost matrike $A$. Jordanska veriga dolžine $k$ je tako zaporedje neničelnih vektorjev $v_1, \dots, v_k$ iz $\mathbb{C}^n$, da velja
$(A - \lambda I)v_1 = 0$, $(A - \lambda I)v_2 = v_1, \dots, (A - \lambda I)v_k = v_{k-1}$.

**Opomba:** Iz definicije sledi, da je $Av_1 = \lambda v_1, Av_2 = v_1 + \lambda v_2, \dots, Av_k = v_{k-1} + \lambda v_k$. V matrični obliki to zapišemo kot
$A [v_1 \ v_2 \ \dots \ v_k] = [v_1 \ v_2 \ \dots \ v_k] \begin{pmatrix} \lambda & 1 & & 0 \\ 0 & \lambda & \ddots & \\ \vdots & \vdots & \ddots & 1 \\ 0 & 0 & \dots & \lambda \end{pmatrix}$ (*).
Matrika $[v_1 \ v_2 \ \dots \ v_k]$ ni kvadratna. Stolpci so linearno neodvisni.

**Definicija jordanske baze**

Bazi, ki je unija jordanskih verig pravimo jordanska baza.
Če uspemo najti jordansko bazo za $\mathbb{C}^n$, je dokaz izreka o jordanski kanonični formi končan. Elemente te baze namreč zložimo v matriko $P = [P_1 \ \dots \ P_m]$, kjer so stolpci podmatrike $P_i$ ravno elementi $i$-te Jordanske verige v tej bazi. Po formuli (*) obstajajo take Jordanske kletke $J_1, \dots, J_m$, da velja $AP_i = P_iJ_i$ za vsak $i$. Odtod sledi, da velja
$AP = P \begin{bmatrix} J_1 & & 0 \\ & \ddots & \\ 0 & & J_m \end{bmatrix}$.
Torej je matrika $A$ res podobna Jordanski matriki.

**Konstrukcija jordanske baze**

Da bi našli jordansko bazo za $\mathbb{C}^n$, je dovolj poiskati jordansko bazo za vsak korenski podprostor posebej. Po izreku o korenskem razcepu je namreč $\mathbb{C}^n$ direktna vsota vseh korenskih podprostorov matrike $A$, torej je unija baz vseh korenskih podprostorov baza za cel prostor $\mathbb{C}^n$.

Korenski podprostor $\mathrm{Ker}(A - \lambda I)^r$, ki ustreza lastni vrednosti $\lambda$ si predstavljamo kot veliko škatlo, v kateri gnezdijo majhne škatle. Najmanjša od teh škatel je lastni podprostor $\mathrm{Ker}(A - \lambda I)$ za $\lambda$.
$\mathrm{Ker}N^r \supset \mathrm{Ker}N^{r-1} \supset \dots \supset \mathrm{Ker}N^2 \supset \mathrm{Ker}N$, kjer $N = A - \lambda I$.

**1. korak Računanje pomožnih baz.**
Za vsak $i = 1, \dots, r$ izberemo poljubno bazo $\mathcal{B}_i$ za $\mathrm{Ker}N^i$.

**2. korak Popravljanje pomožne baze $\mathcal{B}_r$.**
Izberimo take elemente $u_1, \dots, u_{k_1} \in \mathcal{B}_r$, ki dopolnijo $\mathcal{B}_{r-1}$ do baze za $\mathrm{Ker}N^r$. Potem je $\mathcal{B}_{r-1} \cup \{u_1, \dots, u_{k_1}\}$ popravek pomožne baze $\mathcal{B}_r$.

**3. korak Popravljanje pomožne baze $\mathcal{B}_{r-1}$.**
Vektorje $u_1, \dots, u_{k_1} \in \mathrm{Ker}N^r$ pomnožimo z matriko $N$.
* Dobljeni vektorji $Nu_1, \dots, Nu_{k_1}$ ležijo v $\mathrm{Ker}N^{r-1}$.
* Množica $\mathcal{B}_{r-2} \cup \{Nu_1, \dots, Nu_{k_1}\}$ je linearno neodvisna.
Izberimo take elemente $v_1, \dots, v_{k_2} \in \mathcal{B}_{r-1}$, ki dopolnijo linearno neodvisno množico $\mathcal{B}_{r-2} \cup \{Nu_1, \dots, Nu_{k_1}\}$ do baze za $\mathrm{Ker}N^{r-1}$. Potem je $\mathcal{B}_{r-2} \cup \{Nu_1, \dots, Nu_{k_1}\} \cup \{v_1, \dots, v_{k_2}\}$ popravek pomožne baze $\mathcal{B}_{r-1}$

**4. korak Popravljanje pomožne baze $\mathcal{B}_{r-2}$.**
Vektorje $Nu_1, \dots, Nu_{k_1}, v_1, \dots, v_{k_2} \in \mathrm{Ker}N^{r-1}$ pomnožimo z $N$
* Dobljeni vektorji $N^2u_1, \dots, N^2u_{k_1}, Nv_1, \dots, Nv_{k_2}$ ležijo v $\mathrm{Ker}N^{r-2}$.
* Množica $\mathcal{B}_{r-3} \cup \{N^2u_1, \dots, N^2u_{k_1}, Nv_1, \dots, Nv_{k_2}\}$ je LN.
Izberimo take elemente $w_1, \dots, w_{k_3} \in \mathcal{B}_{r-2}$, ki dopolnijo LN množico $\mathcal{B}_{r-3} \cup \{N^2u_1, \dots, N^2u_{k_1}, Nv_1, \dots, Nv_{k_2}\}$ do baze za $\mathrm{Ker}N^{r-2}$.

Postopek nadaljujemo, dokler ne popravimo vseh pomožnih baz. Na koncu dobimo naslednjo skico (verige so stolpci):
- $u_i \in \mathrm{Ker}N^r \setminus \mathrm{Ker}N^{r-1}$ ($i=1, \dots, k_1$)
- $Nu_i \quad v_j \in \mathrm{Ker}N^{r-1} \setminus \mathrm{Ker}N^{r-2}$ ($j=1, \dots, k_2$)
- $N^2u_i \quad Nv_j \quad w_k \in \mathrm{Ker}N^{r-2} \setminus \mathrm{Ker}N^{r-3}$ ($k=1, \dots, k_3$)
- $\vdots \quad \vdots \quad \vdots$
- $N^{r-2}u_i \quad N^{r-3}v_j \quad N^{r-4}w_k \dots t_l \in \mathrm{Ker}N^2 \setminus \mathrm{Ker}N$ ($l=1, \dots, k_{r-1}$)
- $N^{r-1}u_i \quad N^{r-2}v_j \quad N^{r-3}w_k \dots N t_l \quad z_m \in \mathrm{Ker}N$ ($m=1, \dots, k_r$)

Vsak stolpec v zgornji skici nam da eno jordansko verigo. Imamo torej $k_1$ jordanskih verig dolžine $r$, $k_2$ jordanskih verig dolžine $r-1$, $k_3$ jordanskih verig dolžine $r-2, \dots, k_r$ jordanskih verig dolžine $1$. Skupaj je to $k_1 + \dots + k_r = \mathrm{dim} \mathrm{Ker}N$ jordanskih verig. Jordanskih verig za lastno vrednost $\lambda$ je torej toliko kot je njena geometrijska večkratnost.

**Trditev**
Naj bo $k$ naravno število in $N$ matrika. Naj bo $\mathcal{B}_{k-1}$ baza za $\mathrm{Ker}N^{k-1}$, $\mathcal{B}_k$ baza za $\mathrm{Ker}N^k$ in naj bo $\mathcal{C}_{k+1}$ dopolnitev $\mathcal{B}_k$ do baze za $\mathrm{Ker}N^{k+1}$. Potem je množica $\mathcal{B}_{k-1} \cup N(\mathcal{C}_{k+1})$ linearno neodvisna, torej jo lahko dopolnimo do baze za $\mathrm{Ker}N^k$ s podmnožico od $\mathcal{B}_k$.

**Dokaz:**
Naj bo $\mathcal{B}_{k-1} = \{e_1, \dots, e_r\}$, $\mathcal{B}_k = \{f_1, \dots, f_s\}$ in $\mathcal{C}_{k+1} = \{g_1, \dots, g_t\}$. Ker je $\mathcal{C}_{k+1}$ podmnožica $\mathrm{Ker}N^{k+1}$, je $N(\mathcal{C}_{k+1}) := \{Ng_1, \dots, Ng_t\}$ podmnožica $\mathrm{Ker}N^k$. Preverimo, da je množica $\mathcal{B}_{k-1} \cup N(\mathcal{C}_{k+1})$ linearno neodvisna. Recimo, da je
$\alpha_1 e_1 + \dots + \alpha_r e_r + \beta_1 Ng_1 + \dots + \beta_t Ng_t = 0 \quad (1)$.
Pomnožimo z $N^{k-1}$ in upoštevajmo, da $e_1, \dots, e_r \in \mathrm{Ker}N^{k-1}$. Dobimo $\beta_1 N^k g_1 + \dots + \beta_t N^k g_t = 0$, torej $\beta_1 g_1 + \dots + \beta_t g_t \in \mathrm{Ker}N^k$. Ker je $f_1, \dots, f_s$ baza za $\mathrm{Ker}N^k$, lahko razvijemo
$\beta_1 g_1 + \dots + \beta_t g_t = \gamma_1 f_1 + \dots + \gamma_s f_s$.
Ker je $f_1, \dots, f_s, g_1, \dots, g_t$ baza za $\mathrm{Ker}N^{k+1}$, velja $\beta_1 = \dots = \beta_t = 0$ (in $\gamma_1 = \dots = \gamma_s = 0$), torej iz (1) dobimo $\alpha_1 e_1 + \dots + \alpha_r e_r = 0$. Ker je $e_1, \dots, e_r$ baza za $\mathrm{Ker}N^{k-1}$, odtod sledi $\alpha_1 = \dots = \alpha_r = 0$.
Torej je množica $\mathcal{B} := \{e_1, \dots, e_r, Ng_1, \dots, Ng_t\}$ res linearno neodvisna. Če je $\mathrm{Span}\mathcal{B} = \mathrm{Ker}N^k$, potem končamo. Če $\mathrm{Span}\mathcal{B} \neq \mathrm{Ker}N^k$ potem $\mathrm{Span}\mathcal{B}$ ne more vsebovati vseh $f_j$, saj so ti baza za $\mathrm{Ker}N^k$. Torej obstaja tak indeks $i_1$, da $f_{i_1} \notin \mathrm{Span}\mathcal{B}$. Podobno konstruiramo tak $i_2$, da $f_{i_2} \notin \mathrm{Span}(\mathcal{B} \cup \{f_{i_1}\})$. S postopkom nadaljujemo dokler $\mathcal{B} \cup \{f_{i_1}, \dots, f_{i_p}\}$ ni baza za $\mathrm{Ker}N^k$.


### 7. Funkcije matrik

Če poznamo razcep $A = PJP^{-1}$ matrike $A$, potem se računanje potenc matrike $A$ prevede na računanje potenc matrike $J$, saj velja
$A^n = (PJP^{-1})^n = PJ^nP^{-1}$.
Ker je $J$ bločno diagonalna matrika sestavljena iz Jordanskih kletk, se potenciranje matrike $J$ prevede na potenciranje Jordanskih kletk.
Potenciranje matrik je uporabno pri reševanju linearnih rekurzivnih enačb.

**Primer sistema linearnih rekurzivnih enačb**
$x_{n+1} = -4x_n + 4y_n$, $x_0 = 0$
$y_{n+1} = -x_n$, $y_0 = 1$.

Najprej sistem zapišemo v matrični obliki:
$\begin{bmatrix} x_{n+1} \\ y_{n+1} \end{bmatrix} = A \begin{bmatrix} x_n \\ y_n \end{bmatrix}$, kjer $A = \begin{bmatrix} -4 & 4 \\ -1 & 0 \end{bmatrix}$.
Odtod sledi $\begin{bmatrix} x_n \\ y_n \end{bmatrix} = A^n \begin{bmatrix} x_0 \\ y_0 \end{bmatrix} = A^n \begin{bmatrix} 0 \\ 1 \end{bmatrix}$.

Jordanska kanonična forma za $A$: $A = PJP^{-1}$, kjer $P = \begin{bmatrix} 2 & 3 \\ 1 & 2 \end{bmatrix}$, $J = \begin{bmatrix} -2 & 1 \\ 0 & -2 \end{bmatrix}$, $P^{-1} = \begin{bmatrix} -2 & 3 \\ 1 & -2 \end{bmatrix}$.
S popolno indukcijo pokažemo, da je
$J^n = \begin{bmatrix} (-2)^n & n(-2)^{n-1} \\ 0 & (-2)^n \end{bmatrix}$.

Odtod sledi, da je
$A^n = PJ^nP^{-1} = \begin{bmatrix} 2 & 3 \\ 1 & 2 \end{bmatrix} \begin{bmatrix} (-2)^n & n(-2)^{n-1} \\ 0 & (-2)^n \end{bmatrix} \begin{bmatrix} -2 & 3 \\ 1 & -2 \end{bmatrix}$
$= \begin{bmatrix} (-2)^n - 2n(-2)^{n-1} & 4n(-2)^{n-1} \\ -n(-2)^{n-1} & (-2)^n + 2n(-2)^{n-1} \end{bmatrix}$.
Če $A^n$ pomnožimo z $\begin{bmatrix} x_0 \\ y_0 \end{bmatrix} = \begin{bmatrix} 0 \\ 1 \end{bmatrix}$, dobimo
$\begin{bmatrix} x_n \\ y_n \end{bmatrix} = (-2)^n \begin{bmatrix} -2n \\ 1-n \end{bmatrix}$.

**Formula za potenco $k \times k$ jordanske kletke**

Jordansko kletko $J_k(\lambda)$ lahko zapišemo v obliki $\lambda I + N$, kjer je $N$ matrika, ki ima na prvi naddiagonali same enke, drugod pa same ničle. $N^k = 0$. Po binomski formuli je
$(\lambda I + N)^n = \sum_{i=0}^n \binom{n}{i} (\lambda I)^{n-i} N^i = \sum_{i=0}^{k-1} \binom{n}{i} \lambda^{n-i} N^i$.
Torej je $J_k(\lambda)^n = \begin{bmatrix} \lambda^n & n\lambda^{n-1} & \binom{n}{2}\lambda^{n-2} & \dots & \binom{n}{k-1}\lambda^{n-k+1} \\ 0 & \lambda^n & n\lambda^{n-1} & \dots & \binom{n}{k-2}\lambda^{n-k+2} \\ \vdots & \vdots & \ddots & \ddots & \vdots \\ 0 & 0 & \dots & \lambda^n & n\lambda^{n-1} \\ 0 & 0 & \dots & 0 & \lambda^n \end{bmatrix}$.

**Funkcije matrik s potenčnimi vrstami**

Številne funkcije se dajo izraziti s potenčno vrsto, recimo $e^x = \sum_{n=0}^\infty \frac{x^n}{n!}$.
Če imamo funkcijo $f(x) = \sum_{n=0}^\infty c_n x^n$ in vstavimo $A = PJP^{-1}$ namesto $x$, dobimo
$f(A) = \sum_{n=0}^\infty c_n A^n = \sum_{n=0}^\infty c_n (PJP^{-1})^n = P \left( \sum_{n=0}^\infty c_n J^n \right) P^{-1} = P f(J) P^{-1}$.
Računanje $f(J)$, kjer je $J$ bločno diagonalna jordanska matrika, lahko prevedemo na računanje $f(J_i)$ za posamezne jordanske kletke:
$f\left(\begin{bmatrix} J_1 & & 0 \\ & \ddots & \\ 0 & & J_m \end{bmatrix}\right) = \begin{bmatrix} f(J_1) & & 0 \\ & \ddots & \\ 0 & & f(J_m) \end{bmatrix}$.

**Formula za funkcijo $k \times k$ jordanske kletke**
$f(J_k(\lambda)) = \begin{bmatrix} f(\lambda) & f'(\lambda) & \frac{f''(\lambda)}{2!} & \dots & \frac{f^{(k-1)}(\lambda)}{(k-1)!} \\ 0 & f(\lambda) & f'(\lambda) & \dots & \frac{f^{(k-2)}(\lambda)}{(k-2)!} \\ \vdots & \vdots & \ddots & \ddots & \vdots \\ 0 & 0 & \dots & f(\lambda) & f'(\lambda) \\ 0 & 0 & \dots & 0 & f(\lambda) \end{bmatrix}$.
Za $f(x) = x^n$ je to ravno formula za potenco jordanske kletke. Ker je formula linearna v funkciji $f$, odtod sledi, da velja za vse potenčne vrste.

**Uporaba funkcij matrik za sisteme diferencialnih enačb**

Iz Analize vemo, da je funkcija $y(t) = ce^{at}$ rešitev diferencialne enačbe $y'(t) = ay(t)$. To nam da idejo za reševanje naslednjega sistema diferencialnih enačb:
$y_1'(t) = a_{1,1}y_1(t) + \dots + a_{1,d}y_d(t)$
$\vdots$
$y_d'(t) = a_{d,1}y_1(t) + \dots + a_{d,d}y_d(t)$.
Ta sistem najprej zapišemo v matrični obliki kot $y'(t) = Ay(t)$.
Izkaže se, da je njegova rešitev vektorska funkcija $y(t) = e^{At}c$, kjer je $c$ konstanten vektor.

**Izračun matrične eksponentne funkcije $e^{At}$**

Matrično funkcijo $e^{At}$ izračunamo tako, da v funkcijo $f(x) = e^{tx}$ vstavimo $A$ namesto $x$. Kot zgoraj to prevedemo na primer $e^{Jt}$, kjer je $J$ jordanska kletka. V tem primeru iz formule za funkcijo jordanske kletke dobimo:
$e^{J_k(\lambda)t} = \begin{bmatrix} e^{\lambda t} & te^{\lambda t} & \frac{t^2}{2}e^{\lambda t} & \dots & \frac{t^{k-1}}{(k-1)!}e^{\lambda t} \\ 0 & e^{\lambda t} & te^{\lambda t} & \dots & \frac{t^{k-2}}{(k-2)!}e^{\lambda t} \\ \vdots & \vdots & \ddots & \ddots & \vdots \\ 0 & 0 & \dots & e^{\lambda t} & te^{\lambda t} \\ 0 & 0 & \dots & 0 & e^{\lambda t} \end{bmatrix}$.