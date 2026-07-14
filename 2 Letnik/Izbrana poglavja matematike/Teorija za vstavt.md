> Naj bo 
> 
> $$f(x) = a_n x^n + a_{n-1} x^{n-1} + \dots + a_1 x + a_0 \in \mathbb{Z}[x]$$
> 
> Če obstaja praštevilo $p$, tako da velja:
> 
> 1.  **$p \mid a_i$** za vse $i \in \{0, 1, \dots, n-1\}$
> 2.  **$p \nmid a_n$**
> 3.  **$p^2 \nmid a_0$**
> 
> potem je $f(x)$ **nerazcepen** v $\mathbb{Q}[x]$.
> 
> >[!|dokaz]+ Dokaz:
> >
> 
> Dokaz temelji na **protislovju**. Predpostavimo, da je polinom $f(x)$ razcepen nad $\mathbb{Z}[x]$ (po Gaussovem lemi je nerazcepnost nad $\mathbb{Q}$ enakovredna nerazcepnosti nad $\mathbb{Z}$), torej $f(x) = g(x) \cdot h(x)$, kjer sta:
> 
> $$g(x) = b_r x^r + \dots + b_0$$
> $$h(x) = c_s x^s + \dots + c_0$$
> 
> pri čemer sta $r, s \geq 1$ in $r+s = n$.
> 
> 
> Velja $a_0 = b_0 \cdot c_0$. Ker **$p \mid a_0$**, mora $p$ deliti vsaj enega od koeficientov $b_0$ ali $c_0$.
> Brez škode za splošnost recimo, da $p \mid b_0$.
> Ker **$p^2 \nmid a_0$**, $p$ ne sme deliti $c_0$. Če bi ga delil, bi $p^2$ delil $b_0 \cdot c_0 = a_0$, kar je v nasprotju s pogojem.
> 
> Velja $a_n = b_r \cdot c_s$. Ker **$p \nmid a_n$** , $p$ ne deli niti $b_r$ niti $c_s$.
> 
> Naj bo $k$ najmanjši indeks, za katerega $p \nmid b_k$. Ker $p \nmid b_r$ (vodilni koeficient) in $p \mid b_0$, tak $k$ obstaja in velja $0 < k \leq r < n$.
>     
> Poglejmo koeficient $a_k$ produkta $f(x) = g(x)h(x)$:
> $$a_k = b_k c_0 + b_{k-1} c_1 + \dots + b_0 c_k$$
> Preuredimo enačbo za $b_k c_0$:
>     $$b_k c_0 = a_k - (b_{k-1} c_1 + \dots + b_0 c_k)$$
> 
> Po predpostavki $p \mid a_k$ (ker $k < n$).
> 
> Po definiciji indeksa $k$ vemo, da $p$ deli vse $b_0, b_1, \dots, b_{k-1}$. Zato $p$ deli celoten izraz v oklepaju $(b_{k-1} c_1 + \dots + b_0 c_k)$.
> 
> Sledi, da mora $p$ deliti tudi produkt $b_k c_0$.
> 
> 
> Ker $p \mid b_k c_0$, mora $p$ deliti bodisi $b_k$ bodisi $c_0$.
> Vemo, da $p \nmid b_k$ (po izbiri $k$).
> Vemo, da $p \nmid c_0$ (iz točke 1).
> 
> Dobimo **protislovje**. Torej naša predpostavka, da je polinom razcepen, ni pravilna.


> **Razširjen evklidov algoritem**
> 
> Iz tega, da lahko katerikoli ostanek izrazimo z linearno kombinacijo $a$ in $b$, lahko intuitivno razmišljamo o nekem algoritmu, ki bi nam rešil to enačbo:
> 
> $$r_i = x_i a + y_i b$$
> 
> Vemo, da velja:
> 
> $$r_{i-1} = q_i r_i + r_{i+1}$$
> $$\implies r_{i+1} = r_{i-1} - q_i r_i$$
> 
> Če v enačbo vstavimo definicijo $r_i = x_i a + y_i b$:
> 
> $$r_{i+1} = (a x_{i-1} + b y_{i-1}) - q_i (a x_i + b y_i)$$
> $$r_{i+1} = a (x_{i-1} - q_i x_i) + b (y_{i-1} - q_i y_i)$$
> $$r_{i+1} = a x_{i+1} + b y_{i+1}$$
> 
> $$\implies x_{i+1} = x_{i-1} - q_i x_i$$
> $$\implies y_{i+1} = y_{i-1} - q_i y_i$$
> 
> Torej velja:
> 
> $$D(a, b) = ax + by$$
> $$r_n = a x_n + b y_n$$


> Če ima kolobar delitelje niča potem obstajajo polinomi ki imajo več ničel kot je njihova stopnja


> Če smo v obsegu imajo polinomi stopnje $n$ največ $n$ ničel.

>Gaussova lema
>Polinom $p(x)$ je razcepen v $\mathbb{Q}$ natanko tedaj ko je razcepen v $\mathbb{Z}$.

> Če je $I$ ideal v $K$ potem obstaja bijekcija med množico večjih idealov - $\{ J \,;\; I \subseteq J\}$ in množico idealov v $K/I$ , in sicer $\varphi : J \mapsto J/I$. *npr. $12 \mathbb{Z}$ naj bo $I$, obstajajo ideali $J \;(1,2, 3, 4, 6,12) \mathbb{Z}$ torej se $2 \mathbb{Z}$ ideal v $\mathbb{Z}$ slika v $2 \mathbb{Z} /12\mathbb{Z}$*