
>Ogrodje, baza, norma, lastnosti norme, skalarni produkt, lastnosti skalranega produkta
>Če je $\phi$ kot med vektorjema $\vec{x}, \vec{y} \in \mathbb{R}^n$, potem velja:
$$ \langle\vec{x}, \vec{y}\rangle = \left\Vert \vec{x}\right\Vert \!\! \cdot \!\! \left\Vert \vec{y}\right\Vert \cos \phi $$
>**Trditev:** kriterij za pravokotnost
> **Cauchy-Schwarzova neenakost:** Za vsaka $\vec{x}, \vec{y} \in \mathbb{R}^n$ velja:
> $$ |\langle\vec{x}, \vec{y}\rangle| \le \left\Vert \vec{x}\right\Vert \!\! \cdot \!\! \left\Vert \vec{y}\right\Vert $$
>**Trditev** Kvadrat norme dvočlenika
>**Trditev** Trikotniška neenakost
>vektorski produkt, lastnosti vektorskega produkta, 
>**Enačba za dolžino**
>**Pravokotnost vektorja vektorskega produkt**
>**Orientacija vektorja vektorskega produkta**

## Norma

**Norma vektorja** $\vec{x}=(x_1, \dots, x_n) \in \mathbb{R}^n$ je skalar, ki predstavlja njegovo "dolžino" in je definirana kot:
$$ \left\Vert \vec{x}\right\Vert = \sqrt{\sum_{i=1}^n x_i^2} $$
Geometrijsko, po Pitagorovem izreku, norma $\left\Vert \vec{x}\right\Vert$ predstavlja oddaljenost točke $\vec{x}$ od izhodišča. Razdaljo med dvema točkama $\vec{x}$ in $\vec{y}$ pa lahko izrazimo kot $\left\Vert \vec{y}-\vec{x}\right\Vert.$

**Osnovne lastnosti norme so:**
*   **Nenegativnost:** $\left\Vert \vec{x}\right\Vert \ge 0$ za vsak $\vec{x} \in \mathbb{R}^n$. Enakost velja natanko tedaj, ko je $\vec{x} = \vec{0}$.
*   **Homogenost:** $\left\Vert \alpha\vec{x}\right\Vert = |\alpha| \cdot \left\Vert \vec{x}\right\Vert$ za vsak skalar $\alpha \in \mathbb{R}$ in vsak $\vec{x} \in \mathbb{R}^n$.
*   **Trikotniška neenakost:** $\left\Vert \vec{x} + \vec{y}\right\Vert \le \left\Vert \vec{x}\right\Vert + \left\Vert \vec{y}\right\Vert$ za vse $\vec{x}, \vec{y} \in \mathbb{R}^n$.

## Skalarni produkt

**Skalarni produkt** dveh vektorjev $\vec{x}=(x_1, \dots, x_n)$ in $\vec{y}=(y_1, \dots, y_n)$ iz $\mathbb{R}^n$ je skalar, definiran kot:
$$ \langle\vec{x}, \vec{y}\rangle = \sum_{i=1}^n x_i y_i $$

**Osnovne lastnosti skalarnega produkta (za skalarje $\alpha, \beta$ in vektorje $\vec{x}, \vec{y}, \vec{z}$):**
*   **Pozitivna definitnost:** $\langle\vec{x}, \vec{x}\rangle = \left\Vert \vec{x}\right\Vert^2$. To pomeni, da je skalarni produkt vektorja s samim seboj vedno nenegativen, in je enak nič, če in samo če je vektor ničelni.
*   **Simetričnost:** $\langle\vec{x}, \vec{y}\rangle = \langle\vec{y}, \vec{x}\rangle$. Vrstni red faktorjev ne vpliva na rezultat.
*   **Linearnost v prvem faktorju:** $\langle\alpha\vec{x} + \beta\vec{y}, \vec{z}\rangle = \alpha\langle\vec{x}, \vec{z}\rangle + \beta\langle\vec{y}, \vec{z}\rangle$.
*   **Linearnost v drugem faktorju:** $\langle\vec{x}, \alpha\vec{y} + \beta\vec{z}\rangle = \alpha\langle\vec{x}, \vec{y}\rangle + \beta\langle\vec{x}, \vec{z}\rangle$.
Te lastnosti lahko preverimo z neposrednim računom.


**Geometrijski pomen skalarnega produkta:**
Če je $\phi$ kot med vektorjema $\vec{x}, \vec{y} \in \mathbb{R}^n$, potem velja:
$$ \langle\vec{x}, \vec{y}\rangle = \left\Vert \vec{x}\right\Vert \!\! \cdot \!\! \left\Vert \vec{y}\right\Vert \cos \phi $$

**Dokaz:** Uporabimo kosinusni izrek za trikotnik, ki ga tvorijo vektorji $\vec{x}$, $\vec{y}$ in $\vec{x}-\vec{y}$. Dolžine stranic so $a = \left\Vert \vec{x}\right\Vert$, $b = \left\Vert \vec{y}\right\Vert$, $c = \left\Vert \vec{x} - \vec{y}\right\Vert$, in kot med $\vec{x}$ in $\vec{y}$ je $\phi$.

Kosinusni izrek pravi: $c^2 = a^2 + b^2 - 2ab \cos \phi$.

Vstavimo dolžine: $\left\Vert \vec{x} - \vec{y}\right\Vert^2 = \left\Vert \vec{x}\right\Vert^2 + \left\Vert \vec{y}\right\Vert^2 - 2\left\Vert \vec{x}\right\Vert \!\! \cdot \!\! \left\Vert \vec{y}\right\Vert \cos \phi$

Po drugi strani, iz osnovnih lastnosti skalarnega produkta vemo:
$\left\Vert \vec{x} - \vec{y}\right\Vert^2 = \langle\vec{x} - \vec{y}, \vec{x} - \vec{y}\rangle = \langle\vec{x}, \vec{x}\rangle + \langle\vec{y}, \vec{y}\rangle - \langle\vec{x}, \vec{y}\rangle - \langle\vec{y}, \vec{x}\rangle$

Zaradi simetričnosti $\langle\vec{y}, \vec{x}\rangle = \langle\vec{x}, \vec{y}\rangle$, dobimo:
$\left\Vert \vec{x} - \vec{y}\right\Vert^2 = \left\Vert \vec{x}\right\Vert^2 + \left\Vert \vec{y}\right\Vert^2 - 2\langle\vec{x}, \vec{y}\rangle$.

Če izenačimo obe formuli za $\left\Vert \vec{x} - \vec{y}\right\Vert^2$, dobimo:
$\left\Vert \vec{x}\right\Vert^2 + \left\Vert \vec{y}\right\Vert^2 - 2\langle\vec{x}, \vec{y}\rangle = \left\Vert \vec{x}\right\Vert^2 + \left\Vert \vec{y}\right\Vert^2 - 2\left\Vert \vec{x}\right\Vert \!\! \cdot \!\! \left\Vert \vec{y}\right\Vert \cos \phi$

Ko odštejemo $\left\Vert \vec{x}\right\Vert^2 + \left\Vert \vec{y}\right\Vert^2$ in delimo z $-2$, dobimo želeno trditev:
$\langle\vec{x}, \vec{y}\rangle = \left\Vert \vec{x}\right\Vert \!\! \cdot \!\! \left\Vert \vec{y}\right\Vert \cos \phi$

$$\blacksquare$$

**Kriterij za pravokotnost:** Vektorja $\vec{x}, \vec{y} \in \mathbb{R}^n$ sta **pravokotna** natanko tedaj, ko je $\langle\vec{x}, \vec{y}\rangle = 0$

**Dokaz:** Če sta oba vektorja neničelna, potem je $\langle\vec{x}, \vec{y}\rangle = 0$ natanko tedaj, ko je $\cos \phi = 0$. Slednje velja natanko tedaj, ko je $\phi = \frac{\pi}{2} + k\pi$ za celoštevilski $k$, kar pomeni, da je $\phi$ pravi kot. Če je vsaj eden od vektorjev ničelen, je skalarni produkt avtomatsko nič, in privzamemo, da sta pravokotna.

**Cauchy-Schwarzova neenakost:** Za vsaka $\vec{x}, \vec{y} \in \mathbb{R}^n$ velja:
$$ |\langle\vec{x}, \vec{y}\rangle| \le \left\Vert \vec{x}\right\Vert \!\! \cdot \!\! \left\Vert \vec{y}\right\Vert $$

**Dokaz:** Iz lastnosti skalarnega produkta vemo, da je 
$$\langle\vec{x}, \vec{y}\rangle = \left\Vert \vec{x}\right\Vert \!\! \cdot \!\! \left\Vert \vec{y}\right\Vert \cos \phi$$

Ker za kot $\phi$ velja $-1 \le \cos \phi \le 1$, lahko pomnožimo to neenakost z $\left\Vert \vec{x}\right\Vert \!\! \cdot \!\! \left\Vert \vec{y}\right\Vert$
$$-\left\Vert \vec{x}\right\Vert \!\! \cdot \!\! \left\Vert \vec{y}\right\Vert \le \left\Vert \vec{x}\right\Vert \!\! \cdot \!\! \left\Vert \vec{y}\right\Vert \cos \phi \le \left\Vert \vec{x}\right\Vert \!\! \cdot \!\! \left\Vert \vec{y}\right\Vert$$
$$|\langle\vec{x}, \vec{y}\rangle| \le \left\Vert \vec{x}\right\Vert \!\! \cdot \!\! \left\Vert \vec{y}\right\Vert$$

**Kvadrat norme dvočlenika**

$$\left\Vert \vec{x} + \vec{y} \right\Vert^{2} = \left\Vert \vec{x} \right\Vert^2 + \left\Vert \vec{y} \right\Vert^2 + 2 \langle \vec{x}, \vec{y} \rangle $$
$$\langle \vec{x}+\vec{y}, \vec{x}+\vec{y} \rangle = \langle \vec{x},\vec{x} \rangle + \langle \vec{x},\vec{y} \rangle + \langle \vec{y},\vec{x} \rangle + \langle \vec{y},\vec{y} \rangle     $$

**Razširjen pitagorov izrek**

$$\left\Vert \vec{x} + \vec{y} \right\Vert^{2} = \left\Vert \vec{x} \right\Vert^2 + \left\Vert \vec{y} \right\Vert^2  $$

$$\vec{x} \perp \vec{y}$$

**Trikotniška neenakost (ponovno):** Za vsaka $\vec{x}, \vec{y} \in \mathbb{R}^n$ velja:

$$ \left\Vert \vec{x} + \vec{y}\right\Vert \le \left\Vert \vec{x}\right\Vert + \left\Vert \vec{y}\right\Vert $$

**Dokaz:** 

$$ \left\Vert \vec{x} + \vec{y}\right\Vert^2 \le (\left\Vert \vec{x}\right\Vert + \left\Vert \vec{y}\right\Vert)^2 $$
$$ \left\Vert \vec{x} + \vec{y}\right\Vert^2 \le \left\Vert\vec{x}\right\Vert^2 + 2\left\Vert \vec{x}\right\Vert \!\! \cdot \!\! \left\Vert \vec{y}\right\Vert + \left\Vert \vec{y}\right\Vert^2 $$
$$\left\Vert\vec{x}\right\Vert^2 + 2\langle\vec{x}, \vec{y}\rangle + \left\Vert\vec{y}\right\Vert^{2}\leq\left\Vert\vec{x}\right\Vert^2 + \,2\left\Vert \vec{x}\right\Vert \!\! \cdot \!\! \left\Vert \vec{y}\right\Vert + \left\Vert \vec{y}\right\Vert^2$$
$$ 2\langle\vec{x}, \vec{y}\rangle \leq \,2\left\Vert \vec{x}\right\Vert \!\! \cdot \!\! \left\Vert \vec{y}\right\Vert$$
$$ \langle\vec{x}, \vec{y}\rangle \leq \,\left\Vert \vec{x}\right\Vert \!\! \cdot \!\! \left\Vert \vec{y}\right\Vert$$
$$\blacksquare$$

## Vektorski produkt (v $\mathbb{R}^3$)

Za dva vektorja iz $\mathbb{R}^3$ lahko definiramo njun **vektorski produkt**. Če sta $\vec{x}=(x_1, x_2, x_3)$ in $\vec{y}=(y_1, y_2, y_3)$, potem je njun vektorski produkt definiran kot:
$$ \vec{x} \times \vec{y} = (x_2 y_3 - x_3 y_2, x_3 y_1 - x_1 y_3, x_1 y_2 - x_2 y_1) $$

**Osnovne algebrske lastnosti vektorskega produkta:**
*   **Antikomutativnost:** $\vec{y} \times \vec{x} = -(\vec{x} \times \vec{y})$.
*   **Nilpotentnost (lastnost s samim seboj):** $\vec{x} \times \vec{x} = \vec{0}$ za vsak $\vec{x} \in \mathbb{R}^3$. To pomeni, da je vektorski produkt vzporednih vektorjev enak ničelnemu vektorju.
*   **Linearnost v obeh členih (bilinearnost):** $(\alpha\vec{x} + \beta\vec{y}) \times \vec{z} = \alpha(\vec{x} \times \vec{z}) + \beta(\vec{y} \times \vec{z})$ za vsake $\vec{x}, \vec{y}, \vec{z} \in \mathbb{R}^3$ in skalarje $\alpha, \beta \in \mathbb{R}$.

Vektorski produkt je posledica produktov enotskih vektorjev, velja:

*   $\mathbf{i} \times \mathbf{j} = \mathbf{k}$
*   $\mathbf{j} \times \mathbf{k} = \mathbf{i}$
*   $\mathbf{k} \times \mathbf{i} = \mathbf{j}$
*   $\mathbf{j} \times \mathbf{i} = -\mathbf{k}$, etc.
*   $\mathbf{i} \times \mathbf{i} = \mathbf{0}$, $\mathbf{j} \times \mathbf{j} = \mathbf{0}$, $\mathbf{k} \times \mathbf{k} = \mathbf{0}$ 
 ker je kot 0, $\sin(0) = 0$


Naj bo $\vec{a} = a_x \mathbf{i} + a_y \mathbf{j} + a_z \mathbf{k}$ in $\vec{b} = b_x \mathbf{i} + b_y \mathbf{j} + b_z \mathbf{k}$.

Potem se lahko $\vec{a} \times \vec{b}$ razširi v:
$\vec{a} \times \vec{b} = (a_x \mathbf{i} + a_y \mathbf{j} + a_z \mathbf{k}) \times (b_x \mathbf{i} + b_y \mathbf{j} + b_z \mathbf{k})$
$= a_x b_x (\mathbf{i} \times \mathbf{i}) + a_x b_y (\mathbf{i} \times \mathbf{j}) + a_x b_z (\mathbf{i} \times \mathbf{k})$
$+ a_y b_x (\mathbf{j} \times \mathbf{i}) + a_y b_y (\mathbf{j} \times \mathbf{j}) + a_y b_z (\mathbf{j} \times \mathbf{k})$
$+ a_z b_x (\mathbf{k} \times \mathbf{i}) + a_z b_y (\mathbf{k} \times \mathbf{j}) + a_z b_z (\mathbf{k} \times \mathbf{k})$

Nato poračunamo
$= a_x b_x (\mathbf{0}) + a_x b_y (\mathbf{k}) + a_x b_z (-\mathbf{j})$
$+ a_y b_x (-\mathbf{k}) + a_y b_y (\mathbf{0}) + a_y b_z (\mathbf{i})$
$+ a_z b_x (\mathbf{j}) + a_z b_y (-\mathbf{i}) + a_z b_z (\mathbf{0})$

Združimo člene:
$= (a_y b_z - a_z b_y)\mathbf{i}$
$+ (a_z b_x - a_x b_z)\mathbf{j}$
$+ (a_x b_y - a_y b_x)\mathbf{k}$

In dobimo točno
$\vec{a} \times \vec{b} = (a_y b_z - a_z b_y, a_z b_x - a_x b_z, a_x b_y - a_y b_x)$

Opazimo da je zelo podobno kot računanje 2x2 determinant matrik in zato lahko vektorski produkt poračunamo tako da izračunamo determinanto  $3 \times 3$ matrike s prvo vrsto enotskih vekotrjev in drugi dve vrstici vektorja $\vec{a}$ in $\vec{b}$.

$\begin{vmatrix} \mathbf{i} & \mathbf{j} & \mathbf{k} \\ a_x & a_y & a_z \\ b_x & b_y & b_z \end{vmatrix}$


$(a_y b_z - a_z b_y)\mathbf{i} + (a_z b_x - a_x b_z)\mathbf{j} + (a_x b_y - a_y b_x)\mathbf{k}$


**Geometrijski pomen vektorskega produkta:**
*   **Dolžina:** Dolžina vektorja $\vec{x} \times \vec{y}$ je enaka ploščini paralelograma, ki ga oklepata vektorja $\vec{x}$ in $\vec{y}$. Torej $\left\Vert \vec{x} \times \vec{y}\right\Vert = \left\Vert \vec{x}\right\Vert \!\! \cdot \!\! \left\Vert \vec{y}\right\Vert \sin \phi$, kjer je $\phi$ kot med vektorjema $\vec{x}$ in $\vec{y}$.
    To lastnost lahko izpeljemo iz identitete $\left\Vert \vec{x} \times \vec{y}\right\Vert^2 + \langle\vec{x}, \vec{y}\rangle^2 = \left\Vert \vec{x}\right\Vert^2\left\Vert \vec{y}\right\Vert^2$, ki jo lahko dokažemo z izračunom. 
    Z vstavitvijo $\langle\vec{x}, \vec{y}\rangle = \left\Vert \vec{x}\right\Vert \!\! \cdot \!\! \left\Vert \vec{y}\right\Vert \cos \phi$ dobimo $\left\Vert \vec{x} \times \vec{y}\right\Vert^2 + (\left\Vert \vec{x}\right\Vert \!\! \cdot \!\! \left\Vert \vec{y}\right\Vert \cos \phi)^2 = \left\Vert \vec{x}\right\Vert^2\left\Vert \vec{y}\right\Vert^2$, kar se poenostavi v $\left\Vert \vec{x} \times \vec{y}\right\Vert^2 = \left\Vert \vec{x}\right\Vert^2\left\Vert \vec{y}\right\Vert^2 (1 - \cos^2 \phi) = \left\Vert \vec{x}\right\Vert^2\left\Vert \vec{y}\right\Vert^2 \sin^2 \phi$ Korenjenje da želeni rezultat.
*   **Smer:** Vektor $\vec{x} \times \vec{y}$ leži na premici skozi izhodišče, ki je pravokotna tako na vektor $\vec{x}$ kot na vektor $\vec{y}$. Natančneje, skalarni produkt $\langle\vec{x} \times \vec{y}, \vec{x}\rangle = 0$ in $\langle\vec{x} \times \vec{y}, \vec{y}\rangle = 0$.
*   **Orientacija:** Smer vektorja $\vec{x} \times \vec{y}$ določimo s pravilom vijaka. 

## Mešani produkt (v $\mathbb{R}^3$)

**Mešani produkt** za tri vektorje iz $\mathbb{R}^3$, recimo $\vec{x}, \vec{y}, \vec{z}$, definiramo kot skalarni produkt vektorskega produkta prvih dveh vektorjev s tretjim:
$$ [\vec{x}, \vec{y}, \vec{z}] = \langle\vec{x} \times \vec{y}, \vec{z}\rangle $$

**Geometrijski pomen mešanega produkta:** Njegova absolutna vrednost $|[\vec{x}, \vec{y}, \vec{z}]|$ je enaka prostornini paralelepipeda, ki ga razpenjajo vektorji $\vec{x}, \vec{y}$ in $\vec{z}$.
Velja namreč $[\vec{x}, \vec{y}, \vec{z}] = \left\Vert \vec{x} \times \vec{y}\right\Vert \!\! \cdot \!\! \left\Vert \vec{z}\right\Vert \cos \theta$, kjer je $\theta$ kot med $\vec{x} \times \vec{y}$ in $\vec{z}$. Osnovna ploskev paralelepipeda je paralelogram s stranicama $\vec{x}$ in $\vec{y}$, njegova ploščina je $\left\Vert \vec{x} \times \vec{y}\right\Vert$. Višina paralelepipeda je $\left\Vert \vec{z}\right\Vert |\cos \theta|$. Če $\vec{z}$ leži na isti strani osnovne ploskve kot $\vec{x} \times \vec{y}$, potem se predznaka ujemata, sicer pa ne.

**Algebraični pomen:** Mešani produkt je enak determinanti $3 \times 3$ matrike z vrsticami $\vec{x}, \vec{y}, \vec{z}$. To bomo podrobneje obravnavali pri geometrijskem pomenu determinante.

**Osnovni lastnosti mešanega produkta:**
*   **Linearnost:** Je linearen v vsakem faktorju (enako kot skalarni produkt).
*   **Poševna simetričnost:** Če zamenjaš dva faktorja, se spremeni predznak (npr. $[\vec{y}, \vec{x}, \vec{z}] = -[\vec{x}, \vec{y}, \vec{z}]$).
* Če ciklično preuredimo vektorje se vrednost ne spremeni: $[\vec{y}, \vec{x}, \vec{z}] = [ \vec{z},\vec{y} ,\vec{x}]$
* Če se vektor ponovi v mešanem produktu je enak 0.
