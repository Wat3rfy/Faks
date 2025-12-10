
**Polkolobarji in kolobarji**
Množici z dvema operacijama pravimo tudi **bigrupoid**. 
Operaciji običajno označimo s $+$ in $\cdot$, čeprav ni nujno, da imata enake lastnosti kot običajno seštevanje in množenje. Kadar med operacijama ni nobene zveze, je vseeno, če študiramo vsako zase. To pomeni, da je študij bigrupoida $(M, +, \cdot)$ enak ločenemu študiju grupoidov $(M, +)$ in $(M, \cdot)$.


Primer zanimive zveze med obema operacijama je distributivnost:
$(x + y) \cdot z = (x \cdot z) + (y \cdot z)$ in $z \cdot (x + y) = (z \cdot x) + (z \cdot y)$.

**Definicija polkolobarja in kolobarja**

Bigrupoid $(M, +, \cdot)$ je **polkolobar**, če je $(M, +)$ **komutativna polgrupa**, $(M, \cdot )$ pa **grupoid** in velja distributivnost.

Polkolobar $(M, +, \cdot)$ je **kolobar**, če je $(M, +)$ **Abelova grupa**.

Opomba: Naj bo $(M, +, \cdot)$ kolobar. Enoto Abelove grupe $(M, +)$ označimo z $0$. Iz distributivnosti sledi, da je $x \cdot 0 = 0$ in $0 \cdot x = 0$ za vsak $x \in M$.

**Primeri polkolobarjev, ki niso kolobarji**

- $(\mathbb{N}_{0},+,\cdot)$
- $(\mathbb{R}, \max(a,b), +)$

**Definicija lastnosti kolobarjev**

- Kolobar $(M, +, \cdot)$ je komutativen, če je grupoid $(M, \cdot)$ komutativen.
- Kolobar $(M, +, \cdot)$ je asociativen, če je grupoid $(M, \cdot)$ asociativen.
- Kolobar $(M, +, \cdot)$ je z enoto, če je grupoid $(M, \cdot)$ z enoto.


**Primeri kolobarjev** (komutativnost, asociativnost, enota)
* $(\mathbb{R}^3, +, \times)$ - 0 0 0
- ne obstaja - 0 0 1
* $\left(\begin{bmatrix}a&b\\0&0\end{bmatrix}, +,\cdot \right)\,;\; a,b \in \mathbb{R}$
* $(M_{2}(\mathbb{R}), +, \cdot )$
* $(\mathbb{R}, +, \frac{a+b}{2})$
* $(\mathbb{R}[x], +, p \cdot q + p'\cdot q')$
* $(2\mathbb{Z}, +, \cdot )$
* $(\mathbb{Z}, +, \cdot)$
 

**Primer: Boolov kolobar**
Naj bo $M_S$ množica vseh podmnožic dane množice $S$. Potem je $M_S$ kolobar za operaciji
$A + B := (A \setminus B) \cup (B \setminus A)$
$A \cdot B := A \cap B$
***
**Definicija podkolobarja**
Podkolobar kolobarja $(M, +, \cdot)$ je taka podmnožica $N \subseteq M$, da je $N$ podgrupa Abelove grupe $(M, +)$ in podgrupoid grupoida $(M, \cdot)$.

 Preprosteje definicijo podkolobarja povemo takole. 
 
 Podmnožica $N$ v $M$ je podkolobar, če za vsaka $x, y \in N$ velja $x - y \in N$ in $x \cdot y \in N$.

**Primeri podkolobarjev in podpolkolobarjev**
* $\mathbb{N}$ je podpolkolobar v $(\mathbb{Z}, +, \cdot)$.
* Števila deljiva s $3$ so podkolobar v $(\mathbb{Z}, +, \cdot)$.


**Primeri podkolobarjev v $M_n(\mathbb{R})$**
* Zgornje trikotne $n \times n$ matrike so podkolobar v $(M_n(\mathbb{R}), +, \cdot)$.
* Matrike z ničelno zadnjo vrstico so podkolobar v $(M_n(\mathbb{R}), +, \cdot)$.
* Matrike z elementi iz $\mathbb{Z}$ so podkolobar v $(M_n(\mathbb{R}), +, \cdot)$.
* Matrike oblike $\begin{bmatrix} a & b \\ b & a \end{bmatrix}$, kjer $a, b \in \mathbb{R}$, so podkolobar v $(M_2(\mathbb{R}), +, \cdot)$.

**Primeri podkolobarjev v $\mathbb{R}^S$**
Množico vseh funkcij iz intervala $[a, b]$ v množico $\mathbb{R}$ označimo z $\mathbb{R}^{[a,b]}$.
* Podmnožica vseh zveznih funkcij je podkolobar v $(\mathbb{R}^{[a,b]}, +, \cdot)$.
* Podmnožica vseh odvedljivih funkcij je podkolobar v $(\mathbb{R}^{[a,b]}, +, \cdot)$.

***

**Obsegi in polja**

**Definicija obsega**
Obseg je tak kolobar, v katerem je množica neničelnih elementov grupa za množenje. 

Lahko tudi rečemo: je tak asociativen kolobar z enoto, v katerem je vsak neničeln element obrnljiv.

**0 1 1**

**Definicija polja**
Komutativnemu obsegu pravimo **polje**.

**1 1 1**


**Primeri polj**
Kolobarji $(\mathbb{Q}, +, \cdot)$, $(\mathbb{R}, +, \cdot)$ in $(\mathbb{C}, +, \cdot)$ so polja.

Za vsako polje $F$ naj bo $F(x)$ množica vseh racionalnih funkcij v spremenljivki $x$ s koeficienti iz $F$. Ta množica je polje za običajno seštevanje in množenje racionalnih funkcij. Torej so $(\mathbb{Q}(x), +, \cdot)$, $(\mathbb{R}(x), +, \cdot)$ in $(\mathbb{C}(x), +, \cdot)$ polja.

**Primer obsega, ki ni polje**
Obseg kvaternionov $(\mathbb{H},+,*)$

Ta izraz lahko na kratko zapišemo kot $a\mathbf{1} + b\mathbf{i} + c\mathbf{j} + d\mathbf{k}$. Matrika $\mathbf{1}$ je identična matrika, za matrike $\mathbf{i}, \mathbf{j}, \mathbf{k}$ pa velja
$\mathbf{i}^2 = \mathbf{j}^2 = \mathbf{k}^2 = -1$, $\mathbf{ij} = -\mathbf{ji} = \mathbf{k}$, $\mathbf{jk} = -\mathbf{kj} = \mathbf{i}$, $\mathbf{ki} = -\mathbf{ik} = \mathbf{j}$.
Odtod med drugim sledi, da obseg kvaternionov ni komutativen.

**Podobsegi in podpolja**

**Definicija podobsega in podpolja**
Naj bo $(L, +, \cdot)$ obseg. Podmnožica $K \subseteq L$ je njegov **podobseg**, če je $K$ podgrupa v $(L, +)$ in če je $K \setminus \{0\}$ podgrupa v $(L \setminus \{0\}, \cdot)$. 

Komutativen podobseg je **podpolje**.

Na kratko povedano je $K \subseteq L$ podobseg v $L$, če je zaprta za odštevanje in deljenje.

**Primeri podpolj**
Očitno je $\mathbb{Q}$ podpolje polja $\mathbb{R}$ in $\mathbb{R}$ je podpolje polja $\mathbb{C}$.
***
