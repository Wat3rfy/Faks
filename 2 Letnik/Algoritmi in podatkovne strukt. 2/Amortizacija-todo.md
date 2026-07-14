Če imamo časovno kompleknost nekega zaporedja operacij kjer vsaka individualno trajajo različno dolgo lahko ugotovimo koliko je njihova povprečna cena z amortizacijo, kjer vzmameo celoten čas izvajanja in ga razporedimo čez vse operacije v zaporedju da dobimo amortizirano časovno kompleksnost ene operacije.

Torej če ena operacija traja veliko dlje kot druge potem po porazdelitvi lahko pokažemo da je v resnici povprečen čas izvajanja vsake operacije majhen.

Amortizirana analiza garantira povprečno hitrost vsake operacije v algoritmu v najslabšem primeru.

Pogledali si bomo
- **agregatno analizo**
- **accounting method**
- **potential method**

**Agregatna analiza**

To je metoda kjer ugotovimo $O(n)$ algoritma in ga nato delimo s številom operacij ki se izvedejo da dobimo povprečno ceno ene operacije. Temu pravimo **amortizitana cena operacije**

$$\frac{T(n)}{n}$$

Lahko si pogledamo primer dodajanja in odvzemanja s sklada kjer imamo operacije `dodaj`, `odvzemi`, `odvzemi(k)`, kjer lahko izvedemo $n-1$ dodajanj in nato odvzem $n$-tih da dobimo totalno časovno zahtevnost algoritma $n \cdot  O(1) + O(n) = O(n)$. Da dobimo amortizirano ceno ene operacije delimo $\frac{O(n)}{n} = O(1)$ torej je amortizirana cene ene operacije $O(1)$.

Večanje binarnega števca je problem kjer imamo $k$ bitno število ki ga hočemo povečati $n$-krat. Predpostavimo da imamo funkcijo `inc(A,k)` ki poveča binarano število za ena. $A$ je array s $k$ mesti, kjer vsako mesto predstavlja bit. Implementacija ni pomembna. Šteli bomo sjkupno število flipov bitov če povečamo neko število za $n$. Predpostavimo da je $n \leq 2^{k}-1$

Recimo da začnemo z 0. To pomeni da za povečanje števila za $n$ potrebujemo $n$ flipov bita $A[0]$, potem potrebujemo $\lfloor \frac{n}{2} \rfloor$ flipov bita $A[1]$... oz. v splošnem velja

$$A[i] \text{ se obrne} \left\lfloor \frac{n}{2^{i}} \right\rfloor \text{- krat}$$

To pomeni da bo število vseh obratov enako

$$\sum_{i =0}^{\lceil \log_{2}{n} \rceil} \left\lfloor \frac{n}{2^{i}} \right\rfloor $$

ampak očitno velja

$$\sum_{i =0}^{\lceil \log_{2}{n} \rceil} \left\lfloor \frac{n}{2^{i}} \right\rfloor  \leq$$
$$\sum_{i =0}^{k-1} \left\lfloor \frac{n}{2^{i}} \right\rfloor \leq$$
$$\sum_{0}^{\infty} \frac{n}{2^{i}}= n \sum_{0}^{\infty} \frac{1}{2^{i}} = n \cdot 2 = O(n)$$

Torej bo amortizirana vrednost večanja števila za ena enaka

$$\frac{O(n)}{n} = O(1)$$


**Računovodska metoda**

Pri tej metodi posameznim operacijam lahko dodelimo večjo ceno kot dejansko stanejo, drugim pa posledično manjšo, razliko med dejansko ceno in **računovodsko ceno** pripišemo posameznim objektom v podatkovni strukturi kot **kredit** ki ga lahko uporabijo za plačevanje drugih operacij ki imajo nižjo računovodsko ceno kot dejansko.

Naj bo $c_i$ dejanska cena operacije in $\hat{c}_{i}$ računovodska cena. Da nam vsota računovodksih cen operacij lahko dejansko da zgornjo mejo si moramo le-te izbrati tako da velja

$$\sum_{}^{}\hat{c_{i}} \geq \sum_{}^{}c_{i}$$

za vsako zaporedje $n$ operacij. Torej mora razlika med obema vsotama biti nenegativna na katerikoli točki v programu. Če bi na katerikoli točki razlika postala negativna pomeni da smo podcenili neko operacijo kjer potem torej na točki kjer imamo negativno razliko, računovodska cena ni zgornja meja na dejanski ceni algoritma.

Če pogledamo večanje binarnega števca lahkododelimo spreminjanju $i$-tega bita iz $0$ na $1$ ceno $2$, spreminjanju $i$-tega bit iz $1$ na $0$ pa $0$.

Pri vsakem povečanju števila se samo en bit spremeni iz $0$ na $1$, ker za vsako tako spremembno plačamo $2$ potem smo za vsako spremembo bitov iz $1$ na $0$ že plačali in za njih ne rabimo skrbeti. Dobimo računovodsko ceno $2n$ operacij kar je $O(n)$ torej bo amortizirana čas. zahtevnost $O(1)$. 


**Metode potencialov**

je metode kjer namesto da je presežek dodeljen vsakemu elementu je shranjen v **potencialu** strukture. Vsaka operacija ima še vedno računovodsko ceno, le da se razlika med dejansko ceno in amortizirano ceno doda v potencial iz kjer dobimo funkcijo $\Phi(D_{i})$ ki nam pove vrednost potenciala v $i$-tem koraku algoritma.

Glede na to da se v potencialu hrani razlika med dejansko in amortizirano ceno je očitno da bo veljalo

$$\Phi(D_{i}) = \Phi(D_{i-1}) + \hat{c}_{i} - c_{i}$$

Iz tega tudi sledi da je

$$\hat{c_{i}} = \Phi(D_{i})-\Phi(D_{i-1}) + c_{i}$$

Torej velja

$$\sum_{i=1}^{n}\hat{c}_{i} = \sum_{1}^{n}c_{i} + \Phi(D_{i}) - \Phi(D_{i-1})$$

457