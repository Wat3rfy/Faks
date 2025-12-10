

### Relacijska algebra

**Relacijska algebra je postopkovni jezik** kjer navajamo potek pridobivanja zahtevanih informacij.

**Relacijsko popoln jezik** je tak s katerim je mogoče izvesti vsako operacijo ki jo je mogoče izvesti z relacijsko algebro ki presdtavlja izhodišče. *Temelji na selekciji, projekciji, kartezičnem produktu, uniji, razliki.*

**Vhod in izhod** so **relacije**. Vhodne relacije se ne spreminjajo.


**Selekcija** deluje na enojni relaciji $R$ in vrne relacijo ki vsebuje samo tiste $n$-terice ki zadoščajo predikatu $\theta$ - določenem pogoju.
$$\sigma_\theta (R)$$

**Projekcija** deluje na enojni relaciji $R$ in vrne relaicjo ki vsebuje samo tiste atribute ki so določeni s seznamom $s_1,...,s_n$

$$\pi_{s_{1},...,s_{n}} (R) $$

>[!|hide]- Primer
>Vzemimo relacijo (tabelo) **ZAPOSLENI**:
> 
> | Id | Ime | Oddelek | Plača |
> | :---: | :---: | :---: | :---: |
> | 101 | Ana | IT | 3500 |
> | 102 | Marko | Prodaja | 3200 |
> | 103 | Petra | IT | 4100 |
> | 104 | Luka | Prodaja | 3200 |
> 
> $$\sigma_{\text{Oddelek = ' IT '}} (\text{ZAPOSLENI})$$
> 
> | Id | Ime | Oddelek | Plača |
> | :---: | :---: | :---: | :---: |
> | 101 | Ana | IT | 3500 |
> | 103 | Petra | IT | 4100 |
> 
> $$\pi_{\text{Plača}} (\text{ZAPOSLENI})$$
> 
> | Plača |
> | :---: |
> | 3500 |
> | 3200 |
> | 4100 |


**Unija** deluje na dveh relacijah in vrne relacijo ki vsebuje vse $n$-terice relaije $R$ in $S$.
Eliminira duplikate.

Mora veljati **unijska združljivost** - ujemanje po **številu atributov** in **podatkovnem tipu domen**. 

>[!|hide]- Primer 
> $R$
> | Ime | Mesto |
> | :---: | :---: |
> | Peter | Ljubljana |
> | Ana | Maribor |
> | Maja | Celje |
> 
> $S$
> | Ime | Mesto |
> | :---: | :---: |
> | Maja | Celje |
> | Jure | Koper |
> 
> $$R \cup S$$
> 
> | Ime | Mesto |
> | :---: | :---: |
> | Peter | Ljubljana |
> | Ana | Maribor |
> | Maja | Celje |
> | Jure | Koper |



**Razlika** med relacijama $R$ in $S$ vrne relacijo, ki vsebuje samo tiste $n$-terice (vrstice), ki so v $R$ in jih ni v $S$.

Za izvedbo operacije je potrebna **unijska združljivost**.

>[!|hide]- Primer
>
> $R$
> | Ime | Mesto |
> | :---: | :---: |
> | Peter | Ljubljana |
> | Ana | Maribor |
> | Maja | Celje |
>
> $S$
> | Ime | Mesto |
> | :---: | :---: |
> | Maja | Celje |
> | Jure | Koper |
>
> $$R - S$$
>
> **Rezultat:**
>
> | Ime | Mesto |
> | :---: | :---: |
> | Peter | Ljubljana |
> | Ana | Maribor |
> *(Vrstica 'Maja, Celje' je izključena, ker je prisotna v $S$.)*

**Presek** deluje na dveh relacijah in je v resnici kompozitska operacija.

$$R \cap S = R \backslash (R \backslash S)$$

Ker je sestavljena iz razlike potrebujemo **unijsko združljivost.**

**Kartezični produkt** je operacija na dveh relacijah in vrne relacijo z vsemi možnimi kombinacijami med vrsticami obeh relacij.


>[!|hide]- Primer
>
> $R$ = `ARTIKEL`
> 
> | Šifra | Naziv | Zaloga |
> | :---: | :---: | :---: |
> | A10 | Telovadni copati Nike | 10 |
> | A12 | Trenerka Bali | 4 |
> | BC80 | Moška jakna QuickSilver | 1 |
> | X12 | Ženska jakna QuickSilver | 0 |
>
> $S$ = `RAČUN`
> 
> | Račun | Šifra artikla | Količina |
> | :---: | :---: | :---: |
> | 15/05 | A10 | 1 |
> | 15/05 | X12 | 1 |
>
> $R \times S$
>
> | Šifra | Naziv | Šifra artikla | Količina |
> | :---: | :---: | :---: | :---: |
> | A10 | Telovadni copati Nike | A10 | 1 |
> | A10 | Telovadni copati Nike | X12 | 1 |
> | A12 | Trenerka Bali | A10 | 1 |
> | A12 | Trenerka Bali | X12 | 1 |
> | BC80 | Moška jakna QuickSilver | A10 | 1 |
> | BC80 | Moška jakna QuickSilver | X12 | 1 |
> | X12 | Ženska jakna QuickSilver | A10 | 1 |
> | X12 | Ženska jakna QuickSilver | X12 | 1 |

**Stik** je operacija ki združi kartezični produkt in selekcijo. Ena izmed bolj časovno kompleksnih operacij.

Obstaja več vrst stika:
- **Theta stik**
- **Ekvistik**
- **Naravni stik**
- **Odprti stik**
- **Delni stik**

**Theta stik** med $R$ in $S$ vrne vrstice ki zadoščajo predikatu $F$ kartezičnega produkta $R \times S$.

$$R \bowtie_F S$$


Predikat $F$ je oblike 

$$R.\text{atrR} \;\theta\; S.\text{atrS}$$

**Ekvistik** je theta stik omejen na enakost. *Če je atribut skupen se v tabeli pojavi dvakrat (Za obe relaciji)*

**Naravni stik** $R$ in $S$ je vrsta ekvistika prek skupnih atributov relacij $R$ in $S$.

$$R \bowtie S$$

*V stiku ostane le en primerek skupnega atributa.*

**Odprti stik** je stik kjer lahko prikažemo vrstice ki nimajo vrednosti v stičnem atributu.
Poznamo **levo odprti** in **desno odprti** stik.

$$ R \rtimes S $$
$$ R \ltimes S $$

**Levi odprti stik** je stik kjer so $n$-terice $R$ ki nimajo para v $S$ s stičnim atributom, vključene v rezultat.
**Desni stik** je enako le da so vključene $n$-terice iz $S$ ki nimajo para v $R$.

**Delni stik** je relacija ki vsebuje tiste $n$-terice $R$ ki nastopajo v stiku s $S$ po stolpcu $F$.

$$ R \triangleright_F S $$

>[!|hide]- Primer
> 
> **R=ARTIKEL**
> 
> | Šifra | Naziv | Skladišče | Dobavitelj | Zaloga |
> | :---: | :---: | :-------: | :--------: | :----: |
> | A10 | Telovadni copati Nike | LJ | Nike | 10 |
> | BC80 | Moška jakna QuickSilver | LJ | Karma | 1 |
> | X12 | Ženska jakna QuickSilver | GO | Karma | 0 |
> 
> **S=SKLADIŠČE**
> 
> | Šifra | Kraj |
> | :---: | :---: |
> | LJ | Ljubljana, Tržaška 33 |
> | MB | Maribor, Prešernov trg 2 |
> | GO | Nova Gorica, Cankarjeva 2 |
> 
> $$ $$
> $$ R \triangleright_{R.\text{Skladišče} = S.\text{Šifra}} (\sigma_{\text{Šifra} = \text{'LJ'}} (S)) $$
> $$ $$
> 
> | Šifra | Naziv | Skladišče | Dobavitelj | Zaloga |
> | :---: | :---: | :-------: | :--------: | :----: |
> | A10 | Telovadni copati Nike | LJ | Nike | 10 |
> | BC80 | Moška jakna QuickSilver | LJ | Karma | 1 |



**Količnik** med $R$ in $S$ vrne relacijo z atributi $C$ ki jo sestavljajo $n$-terice iz $R$, ki so v parih z vsemi vrednostmi iz $S$.

*Količnik se izvaja pod predpostavko da sta $R$ in $S$ razdeljena na dva dela. Če imamo atribute $A$ in $B$ potem so atributi $R$ enaki $A \cup B$, in atributi $S$ = $B$.*

$$R/S$$
$$\color{light} =\pi_{A}(R)-\pi_{A}((\pi_{A}(R) \times S)-R)$$

>[!|hide]- Postopek
> Najprej določimo množico vseh potencialnih subjektov (npr. Kupec ID, če je to naš $A$), ki se nahajajo v relaciji $R$. To so vsi subjekti, ki so sploh kadarkoli izvedli nakup.
>
> Nato izračunamo kratezični produkt med množico vseh potencialnih subjektov in celotno množico delitelja $S$ (npr. vsi obvezni artikli 'Karma'). To ustvari **idealno relacijo**, ki vsebuje *vse* kombinacije, ki bi morale obstajati, če bi vsak subjekt kupil vsak obvezni artikel.
> 
> Od idealne relacije (vseh teoretičnih kombinacij) odštejemo dejansko relacijo $R$ (dejanske nakupe). Rezultat te razlike so **manjkajoče povezave**.
> 
> Manjkajoče povezave iz projektiramo nazaj samo na atribute $A$ (Kupec ID). S tem dobimo seznam vseh subjektov, ki jim **manjka vsaj ena povezava** z obveznimi entitetami iz $S$ (torej, kupec ni kupil vsaj enega artikla 'Karma').
> 
> Nazadnje, od celotne množice potencialnih subjektov (Korak 1) odštejemo tiste subjekte, ki jim nekaj manjka. Ostanemo samo z naborom subjektov, ki so povezani **z VSEMI** entitetami v delitelju $S$.

>[!|hide]- Primer
> $\pi_{\text{Šifra, Kupec}}$
> 
> | Šifra | Kupec |
> | :---: | :---: |
> | A10 | K1 |
> | A12 | K1 |
> | BC80 | K2 |
> | X12 | K3 |
> | A10 | K3 |
> | BC80 | K3 |
> | BC80 | K4 |
> | X12 | K4 |
> | A12 | K5 |
> 
> $\pi_{\text{Šifra artikla}} (\sigma_{\text{dobavitelj} = \text{'Karma'}} (S))$
> 
> | Šifra |
> | :---: |
> | BC80 |
> | X12 |
> 
> 
> $\pi_{\text{Šifra, Kupec}} (R) / \pi_{\text{Šifra artikla}} (\sigma_{\text{dobavitelj} = \text{'Karma'}} (S))$
> 
> | Kupec |
> | :---: |
> | K3 |
> | K4 |


***

**Agregatne operacije**

$$\Gamma_{AL}(R)$$

Agregat $\Gamma_{AL}$ aplicira seznam agregatnih funkcij $AL$ na relaciji $R$ in vrne agregirano relacijo.

$AL$ vsebuje enega ali več parov
$(\text{<agregatna funkcija>}, \text{<atribut>})$

Poznamo $\text{COUNT, SUM, AVG, MIN, MAX}$

>[!|hide]- Primer
> $$ \rho_R(\text{AvgCena}) \Gamma_{\text{AVG Cena}} (\sigma_{\text{Zaloga} > 0} (R)) $$
> 
> **R**
> 
> | Šifra | Naziv | Skladišče | Cena | Zaloga |
> | :---: | :---: | :-------: | :----: | :----: |
> | A10 | Telovadni copati Nike | LJ | 17.990 | 10 |
> | A12 | Trenerka Bali | MB | 6.750 | 4 |
> | BC80 | Moška jakna QuickSilver | LJ | 14.290 | 1 |
> | X12 | Ženska jakna QuickSilver | GO | 14.290 | 0 |
> 
> **Rezultat**
> 
> | AvgCena |
> | :-----: |
> | 13.010 |

***

**Zruževalne operacije**

$$\text{GA }\Gamma_{AL}(R) = $$

Relacijo ko jo dobimo vsebuje atribute $GA$ ter vrednosti ki jih dobim z agregati $AL$ kjer se združijo po istih vrednostih atributov iz $GA$.
***

**Preimenovanje** je operacije ki poeimenuje atributi ki ga dobimo z operacijami $\text{Op}$ nad relacijo $R$ z imenom $\text{Ime}$.

$$\rho_{R}(\text{AvgCena})\Gamma_{\text{AVG}Cena} (\sigma_{\text{Zaloga}>0}(R))$$

***