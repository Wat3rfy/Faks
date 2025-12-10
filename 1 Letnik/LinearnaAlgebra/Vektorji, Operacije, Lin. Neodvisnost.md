
>[!|]- Vsebuje
>Geometrijski vektor, krajevni vektor, seštevanje vektorjev, množenje vektorja s skalarjem, lastnosti vsote vektorjev, lastnosti množenje s skalarjem, središče točk, linearna kombinacija vektorjev, linearna neodvisnost vektorjev
>
>**Trditev:** Vektorji $v_1, \dots, v_m$ so linearno neodvisni natanko tedaj, ko ima sistem linearnih enačb $\alpha_1 v_1 + \dots + \alpha_m v_m = 0$ samo eno rešitev, to je trivialno rešitev $\alpha_1 = \dots = \alpha_m = 0$.
>**Posledica (Unikatnost linearne kombinacije):** Vektorji $v_1, \dots, v_m \in \mathbb{R}^n$ so linearno neodvisni natanko tedaj, ko se da vsak vektor iz $\mathbb{R}^n$ na kvečjemu en način izraziti kot linearna kombinacija vektorjev $v_1, \dots, v_m$.


## Vektorji v $\mathbb{R}^n$

Za lažjo predstavo se pogosto omejimo na ravnino, čeprav vsi pojmi veljajo tudi za prostor in višje dimenzije.

**Geometrijski vektor** je usmerjena daljica med dvema točkama. Začetni točki pravimo **rep**, končni točki pa **glava** vektorja. Dva geometrijska vektorja sta enaka, če sta vzporedna, enako dolga in kažeta v isto smer.
*   **Primer:** $\vec{AB} = \vec{CD}$ pomeni, da daljica od $A$ do $B$ in daljica od $C$ do $D$ predstavljata isti vektor.

Ko izberemo neko točko v ravnini, ki ji pravimo **izhodišče**, lahko definiramo **krajevni vektor**.

**Krajevni vektor** je geometrijski vektor, ki ima rep v izhodišču. 
Vsak geometrijski vektor je enak natanko enemu krajevnemu vektorju, saj ga lahko vzporedno premaknemo tako, da njegov rep pade v izhodišče.

**Vsak krajevni vektor je natanko določen s svojo glavo**. Če skozi izhodišče potegnemo koordinatni sistem, je glava natanko določena s svojimi koordinatami.

**Primer:** Koordinate krajevnega vektorja, ki je enak geometrijskemu vektorju iz točke $(x_1, \dots, x_n)$ v točko $(y_1, \dots, y_n)$, so $(y_1 - x_1, \dots, y_n - x_n)$.

### Operacije z vektorji

Krajevnim vektorjem bomo v nadaljevanju preprosto rekli **vektorji**. Glavna prednost vektorjev je, da z njimi lahko računamo.

**Vsota dveh vektorjev** je algebraično definirana z:
$$ (x_1, \dots, x_n) + (y_1, \dots, y_n) := (x_1 + y_1, \dots, x_n + y_n) $$
Geometrijsko se vsota pojasni s **paralelogramskim pravilom**.

Realnim številom bomo v nadaljevanju pogosto rekli **skalarji**.

**Produkt vektorja s skalarjem** je algebraično definiran z:
$$ \alpha(x_1, \dots, x_n) := (\alpha x_1, \dots, \alpha x_n) $$
Geometrijski pomen produkta vektorja s skalarjem $\alpha$ je, da vektor raztegnemo za faktor $|\alpha|$. Če je $\alpha < 0$, potem vektor raztegnemo in ga prezrcalimo čez izhodišče.

Ker sta obe operaciji definirani po komponentah, lahko njune lastnosti izpeljemo iz lastnosti realnih števil.
Označimo **ničelni vektor** $0 := (0, \dots, 0)$ in **nasprotni vektor** $-(x_1, \dots, x_n) := (-x_1, \dots, -x_n) = (-1)(x_1, \dots, x_n)$

**Lastnosti vsote (za vektorje $x, y, z$):**
*   $x + y = y + x$ (**komutativnost**)
*   $(x + y) + z = x + (y + z)$ (**asociativnost**)
*   $x + 0 = x$ (**ničelni element**)
*   $x + (-x) = 0$ (**inverzni element**)

**Lastnosti množenja s skalarjem (za skalarje $\alpha, \beta$ in vektor $x$):**
*   $\alpha(x + y) = \alpha x + \alpha y$ (distributivnost skalarja nad vsoto vektorjev)
*   $(\alpha + \beta)x = \alpha x + \beta x$ (distributivnost vsote skalarjev nad množenjem z vektorjem)
*   $(\alpha \beta)x = \alpha(\beta x)$ (asociativnost)
*   $1x = x$ (nevtralni element za množenje)
*   $0x = 0$ (množenje z ničelnim skalarjem da ničelni vektor)

Te lastnosti bomo kasneje vzeli za aksiome abstraktnega vektorskega prostora.

>[!|hide]- Primer: Delitev daljice v danem razmerju
Dana je daljica $AB$. Iščemo tako točko $C$ na tej daljici, ki jo deli v razmerju $3:2$. To pomeni, da velja $|\vec{AC}| = \frac{3}{5}|\vec{AB}|$. Označimo z $\vec{r}_A, \vec{r}_B, \vec{r}_C$ krajevne vektorje, ki ustrezajo točkam $A, B, C$. Želimo izraziti $\vec{r}_C$ z $\vec{r}_A$ in $\vec{r}_B$.
Ker je $\vec{AC} = \frac{3}{5}\vec{AB}$ in $\vec{AB} = \vec{r}_B - \vec{r}_A$, dobimo:
$$ \vec{r}_C - \vec{r}_A = \frac{3}{5}(\vec{r}_B - \vec{r}_A) $$
$$ \vec{r}_C = \vec{r}_A + \frac{3}{5}\vec{r}_B - \frac{3}{5}\vec{r}_A = \left(1 - \frac{3}{5}\right)\vec{r}_A + \frac{3}{5}\vec{r}_B = \frac{2}{5}\vec{r}_A + \frac{3}{5}\vec{r}_B $$


**Središče točk** $\vec{r}_1, \dots, \vec{r}_m$ je točka:

$$ \frac{1}{m}(\vec{r}_1 + \dots + \vec{r}_m) $$


**Dokaz (z indukcijo):** Naj bo $\vec{p}_1 = \vec{r}_1$. Za vsak $i = 2, \dots, m$ naj bo $\vec{p}_i$ taka točka na daljici med $\vec{p}_{i-1}$ in $\vec{r}_i$, ki to daljico deli v razmerju $1 : (i-1)$. Trdimo, da je potem $\vec{p}_m$ iskana točka.
*   **Osnovni korak ($i=1$):** $\vec{p}_1 = \vec{r}_1 = \frac{1}{1}\vec{r}_1$. Trditev drži.
*   **Indukcijski korak:** Predpostavimo, da trditev drži za $i-1$, torej $\vec{p}_{i-1} = \frac{1}{i-1}(\vec{r}_1 + \dots + \vec{r}_{i-1})$.
    Po prejšnjem primeru delitve daljice v razmerju $1 : (i-1)$ velja:
    $$ \vec{p}_i = \frac{i-1}{i}\vec{p}_{i-1} + \frac{1}{i}\vec{r}_i $$
    Vstavimo indukcijsko predpostavko za $\vec{p}_{i-1}$:
    $$ \vec{p}_i = \frac{i-1}{i} \left(\frac{1}{i-1}(\vec{r}_1 + \dots + \vec{r}_{i-1})\right) + \frac{1}{i}\vec{r}_i $$
    $$ \vec{p}_i = \frac{1}{i}(\vec{r}_1 + \dots + \vec{r}_{i-1}) + \frac{1}{i}\vec{r}_i = \frac{1}{i}(\vec{r}_1 + \dots + \vec{r}_i) $$
    S tem je trditev dokazana za vse $i$, in torej za $i=m$ dobimo $\vec{p}_m = \frac{1}{m}(\vec{r}_1 + \dots + \vec{r}_m)$.

### Linearne kombinacije vektorjev

**Linearna kombinacija:** Vektor $v \in \mathbb{R}^n$ je **linearna kombinacija** vektorjev $v_1, \dots, v_m \in \mathbb{R}^n$, če obstajajo taki skalarji $\alpha_1, \dots, \alpha_m \in \mathbb{R}$, da velja:
$$ v = \alpha_1 v_1 + \dots + \alpha_m v_m $$

Če želimo preveriti, ali je vektor $v$ linearna kombinacija vektorjev $v_1, \dots, v_m$, moramo rešiti sistem z $m$ neznankami (za vsak vektor ena neznanka oz en skalar) in $n$ linearnih enačb (za vsako komponento vektorja svoja enačba).

### Linearna neodvisnost vektorjev

**Linearno odvisni/neodvisni vektorji:** Vektorji $v_1, \dots, v_m$ so **linearno odvisni**, če je eden od njih enak linearni kombinaciji preostalih. Sicer so **linearno neodvisni**.

**Geometrijski pomen linearne neodvisnosti:**
En je linearno neodvisen če ni ničelni, dva vektorja sta, če ne ležita na isti premici, trije če ne ležijo na isti ravnini,...

**Trditev:** Vektorji $v_1, \dots, v_m$ so linearno neodvisni natanko tedaj, ko ima sistem linearnih enačb $\alpha_1 v_1 + \dots + \alpha_m v_m = 0$ samo eno rešitev, to je trivialno rešitev $\alpha_1 = \dots = \alpha_m = 0$.

**Dokaz:**
*   **($\Rightarrow$) Predpostavimo, da so $v_1, \dots, v_m$ linearno neodvisni.**
    Očitno je $\alpha_1 = \dots = \alpha_m = 0$ vedno rešitev sistema $\alpha_1 v_1 + \dots + \alpha_m v_m = 0$.
    Denimo, da bi imel ta sistem še kakšno drugo rešitev, kjer bi bil vsaj en koeficient $\alpha_i \neq 0$.
    Potem bi lahko izrazili $v_i$ kot linearno kombinacijo preostalih vektorjev:
    $$ v_i = -\frac{\alpha_1}{\alpha_i}v_1 - \dots - \frac{\alpha_{i-1}}{\alpha_i}v_{i-1} - \frac{\alpha_{i+1}}{\alpha_i}v_{i+1} - \dots - \frac{\alpha_m}{\alpha_i}v_m $$
    To pa pomeni, da je $v_i$ linearna kombinacija preostalih vektorjev, kar je v protislovju z definicijo linearne neodvisnosti. Zato mora biti edina rešitev trivialna rešitev.

*   **($\Leftarrow$) Predpostavimo, da ima sistem $\alpha_1 v_1 + \dots + \alpha_m v_m = 0$ samo trivialno rešitev.**
    Denimo, da bi bili $v_1, \dots, v_m$ linearno odvisni. Po definiciji linearne odvisnosti bi to pomenilo, da je eden od njih linearna kombinacija preostalih. Recimo, da je $v_i = \beta_1 v_1 + \dots + \beta_{i-1}v_{i-1} + \beta_{i+1}v_{i+1} + \dots + \beta_m v_m$ za neke skalarje $\beta_j$.
    Če to preuredimo, dobimo:
    $$ \beta_1 v_1 + \dots + \beta_{i-1}v_{i-1} - 1 \cdot v_i + \beta_{i+1}v_{i+1} + \dots + \beta_m v_m = 0 $$
    S tem smo našli netrivialno rešitev za sistem $\alpha_1 v_1 + \dots + \alpha_m v_m = 0$ (saj je koeficient pri $v_i$ enak $-1$, kar ni nič). To je v protislovju z našo predpostavko. Torej so vektorji $v_1, \dots, v_m$ linearno neodvisni.

**Posledica (Unikatnost linearne kombinacije):** Vektorji $v_1, \dots, v_m \in \mathbb{R}^n$ so linearno neodvisni natanko tedaj, ko se da vsak vektor iz $\mathbb{R}^n$ na kvečjemu en način izraziti kot linearna kombinacija vektorjev $v_1, \dots, v_m$.

**Dokaz:**
*   **($\Rightarrow$) Predpostavimo, da so $v_1, \dots, v_m$ linearno neodvisni.**
    Denimo, da se da nek vektor $v \in \mathbb{R}^n$ izraziti na dva načina:
    $$ v = \alpha_1 v_1 + \dots + \alpha_m v_m $$
    $$ v = \beta_1 v_1 + \dots + \beta_m v_m $$
    Če enačbi odštejemo, dobimo:
    $$ 0 = (\alpha_1 - \beta_1)v_1 + \dots + (\alpha_m - \beta_m)v_m $$
    Ker so vektorji $v_1, \dots, v_m$ linearno neodvisni, po zgornji trditvi sledi, da morajo biti vsi koeficienti enaki nič:
    $$ \alpha_1 - \beta_1 = 0, \dots, \alpha_m - \beta_m = 0 $$
    To pomeni, da je $\alpha_i = \beta_i$ za vse $i = 1, \dots, m$. Torej je izražava unikatna.

*   **($\Leftarrow$) Predpostavimo, da se da vsak vektor iz $\mathbb{R}^n$ na kvečjemu en način izraziti kot linearna kombinacija vektorjev $v_1, \dots, v_m$.**
    Vzemimo ničelni vektor $0 \in \mathbb{R}^n$. Vemo, da je $0 = 0v_1 + \dots + 0v_m$ trivialna linearna kombinacija.
    Po predpostavki, da je izražava kvečjemu ena, to pomeni, da če je $\alpha_1 v_1 + \dots + \alpha_m v_m = 0$, potem mora biti $\alpha_1 = \dots = \alpha_m = 0$.
    Po zgornji trditvi to natanko pomeni, da so vektorji $v_1, \dots, v_m$ linearno neodvisni.

### Ogrodje in Baza

**Ogrodje:** Vektorji $v_1, \dots, v_m \in \mathbb{R}^n$ so **ogrodje** (ali razpenjalna množica), natanko tedaj, ko se da *vsak* vektor iz $\mathbb{R}^n$ na *vsaj en* način izraziti kot linearna kombinacija vektorjev $v_1, \dots, v_m$.

**Baza:** Vektorji $v_1, \dots, v_m \in \mathbb{R}^n$ so **baza**, natanko tedaj, ko so ogrodje *in* ko so linearno neodvisni. Se pravi, natanko takrat, ko se da vsak vektor iz $\mathbb{R}^n$ na *natanko en* način izraziti kot linearna kombinacija vektorjev $v_1, \dots, v_m$.

**Opomba:** Izkaže se, da ima vsaka baza v $\mathbb{R}^n$ natanko $n$ elementov.

