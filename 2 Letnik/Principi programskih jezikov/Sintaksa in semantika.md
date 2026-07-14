

**Osnovni princip**

**Programski jezik** omogoča, da neposredno podamo natančna navodila, računalniku.

**Anatomija programskega jezika**

Programski jezik je zasnovan kot sistem s komponentami:

* **sintaksa:** pravila, kako se piše kodo

* **statična semantika:** preverjanje, ali je program smiseln, na primer: »spremenljivka `i` ni
  nikjer deklarirana«

* **dinamična semantika:** določa kako se program izvede

* **denotacijska semantika:** matematični pomen programa


**Implementacija jezika** je program, ki preverja sintakso in statično semantiko jezika ter omogoča izvajanje programov. To je lahko tolmač (angl. interpreter), prevajalnik (angl. compiler), oboje, ali pa kombinacija.

Pomemben del programskega jezika so tudi metode za **analizo programov**, s katerimi ugotavljamo lastnosti programa, in za **dokazovanje pravilnosti**, s katerimi dokazujemo, da ima program želene lastnosti.

## Sintaksa aritmetičnih izrazov

Začeli bomo z zelo preprostim programskim jezikom, ki je tako preprost, da ga v praksi sploh ne obravnavamo kot samostojen programski jezik. Obravnavajmo **celoštevilske aritmetične izraze**: cela števila, operaciji `*` in `+` ter spremenljivkami. To bi lahko bil majhen košček resnega programskega jezika.

Sintaksa pove, kakšne izraze in programe lahko pišemo v programskem jeziku.

### Konkretna sintaksa aritmetičnih izrazov

Programer zapiše program kot niz znakov, na primer:

```
"y + (5 + 7 * x) * 8"
```

Ta oblika je primerna za človeka, a ni primerna za obdelavo z računalnikom, saj ne odraža
strukture izraza. Zgornji izraz predstavimo z drevesom takole:

```
      +
     / \
    y   *
       / \
      +   8
     / \
    5   *
       / \
      7   x
```

Na ta način se znebimo presledkov in oklepajev in jasno ponazorimo strukturo izraza. Tudi programsko kodo lahko
predstavimo z drevesi. Ali znate razbrati program, ki ga predstavlja naslednje drevo?

```
     ;
    / \
  :=   \
 /  \   \
i    0   \
        while
       /     \
      <       \
     / \       \
    i  10       ;
               / \
              /   \
             /     \
           :=       \
          /  \     print
         i    +      |
             / \     i
            i   1
```

### Abstraktna sintaksa aritmetičnih izrazov

Izraze lahko opišemo s podatkovno strukturo drevo. To je oblika, primerna za obdelavo, ni pa primerna za človeka.

Prednosti:
1. Iz drevesa je takoj razvidna struktura programa ali izraza.
2. Drevo ne vsebuje nepomembnih komponent (na primer presledkov in oklepajev).

Kako implementiramo drevesa, je odvisno od programskega jezika, ki ga uporabimo. V Javi se to seveda naredi z razredi.
Kasneje bomo spoznali še druge načine.


### Pravila sintakse

**Gramatika oz. slovnica** je skupek pravil ki nam podaja strukturo oz. sintakso jezika.

Poznamo več načinov, kako podamo pravila, mi si bomo ogledali poenostavljeno verzijo t.i. [oblike BNF](https://en.wikipedia.org/wiki/Backus–Naur_form), ki jo pogosto srečamo v praksi:

```
⟨izraz⟩ ::= ⟨aditivni-izraz⟩ EOF
⟨aditivni-izraz⟩ ::= ⟨multiplikativni-izraz⟩ | ⟨aditivni-izraz⟩ + ⟨multiplikativni-izraz⟩
⟨multiplikativni-izraz⟩ ::= ⟨osnovni-izraz⟩ | ⟨multiplikativni-izraz⟩ * ⟨osnovni-izraz⟩
⟨osnovni-izraz⟩ ::= ⟨spremenljivka⟩ | ⟨številka⟩ | ( ⟨aditivni-izraz⟩ )
⟨spremenljivka⟩ ::= [a-zA-Z]+
⟨številka⟩ ::= -?[0-9]+
```

V trikotnih oklepajih `⟨⋯⟩` so zapisani **neterminalni simboli**. Vsak od njih ima svoje pravilo, ki pove, kako ga razčlenimo. Ostali simboli (`+`, `*`, `(`, `)`, in regularni izrazi, ki opisujejo spremenljivke in številke) so **osnovni** ali **terminalni simboli**.

Pri opisu spremenljivk in številke smo uporabili **regularne izraze**: v oglatih oklepajih navedemo, kateri znaki so dovoljeni, znak `+` pa pomeni »ena ali več ponovitev«.


### Iz konkretne v abstraktno sintakso

Konkretno sintakso predelamo v abstraktno sintakso s postopkomaa leksikalne in sintaksne analize:

* **leksikalna analiza:** niz razbijemo na zaporedje podnizov, ki jih imenujemo **leksikalne enote** (angl. **lexemes**). Posamezne podnize predstavimo z osnovnimi simboli.  
  Npr.: "$\cdot$" je $\text{KRAT}$, "$+$" je $\text{plus}$, "$30$" je $\text{ŠTEVILO}(30)$,... 
  Omogoča da je več osnovnih simbolob predstavlja isto stvar "$\cdot , *,\times$" je $\text{KRAT}$
  
  Niz počisti, in prevede v kategorizirane tokene. 

* **sintaksna analiza** (angl. parsing): niz osnovnih simbolov oz. tokenov razčlenimo v sintaksno drevo.


Leksikalna analiza odstrani nebistvene znake, kot so presledki in prehodi v novo vrsto, pogosto tudi komentarje.

Za aritmetične izraze so leksikalni elementi in pripadajoči osnovni simboli:

* niz `+` in simbol `PLUS`
* niz `*` in simbol `KRAT`
* spremenljivka, opisana z regularnim izrazom `[a-zA-Z]+` in simbol `SPREMENLJIVKA(x)`, kjer je `x` niz
* številka, opisana z regularnim izrazom `-?[0-9]+` in simbol `ŠTEVILKA(n)`, kjer je `n` število
* niz `(` in simbol `OKLEPAJ`
* niz `)` in simbol `ZAKLEPAJ`
* `EOF` poseben gradnik, ki pomeni »konec«

Primer: `foo * (5 + 42)` nam da leksikalnih elementov
```
"foo", "*", "(", "5", "+", "42", ")"
```
s pripadajočim nizom osnovnih simbolov
```
SPREMENLJIVKA("foo") KRAT OKLEPAJ ŠTEVILKA(5) PLUS ŠTEVILKA(42) ZAKLEPAJ EOF
```
Ta niz nam da ustrezno drevo.

Primer: `x * ((5 + 8` nam da niz leksikalnih elementov
```
"x", "*", "(", "(", "5", "+", "8"
```
s pripadajočim nizom osnovnih simbolov
```
SPREMENLJIVKA(x) KRAT OKLEPAJ OKLEPAJ ŠTEVILKA(5) PLUS ŠTEVILKA(8)
```
Ta niz ni veljaven in ne določa drevesa. Javimo sintaktično napako.

Med leksikalnim elementom in osnovnim simbolom ločimo zaradi dveh razlogov

1. Več znakov lahko predstavlja množenje `*`, `×` in `·`, vse pa predstavimo z istim osnovnim simbolom, ista enota v abstraktni sintaksi
2. Osnovne simbole naštejemo v kodi, da prevajalnik točno ve, kateri simboli se lahko pojavijo. Če bi uporabljali nize, nas prevajalnik ne more opozoriti na morebitne tipkarske napake v kodi. Konkretno, če preverjamo `if (simbol == KART) then ...`, bo prevajalnik javil napako, saj ne ve, kaj je `KART`. Če bi preverjali neposredno nize z `if (simbol = "**") then ...`, prevajalnik ne bi vedel, da smo se zatipkali in da bi moralo pisati `*`.

**Parser oz. razčlenjvealnik** vzame vhodno kodo in jo primerja z gramatiko da ugotovi če uporablja pravilno stukturo in kodo pretvori v abstraktno **sintaksno drevo**.

Če imamo več enakih operatorjev zapored moramo vedeti kateri se najprej izvede tako imamo **levo-, desno- in neasociativnost** - izvaja se od leve naprej, desne naprej ali pa vezanje več operatorjev ni dovoljeno in se javi napaka.

Levo *in podobno desno* asociativnost si lahko predstavljamo kot - drevo visi v levo, plus se računa od leve proti desni oz. prvi plus ki ga izračunamo je najbolj levi oz. levi plusi so nižje.

## Operacijska semantika

Ko računamo vrednost izraza, moramo poznati vrednosti spremenljivk. 

Preslikavi, ki spremenljivke slika v njihove vrednosti, pravimo **okolje** (angl. environment). 

Na primer, če ima `x` vrednost `3`, `y` vrednost `7` in `z` vrednost `10`, to predstavimo z okoljem

```
[x ↦ 3, y ↦ 7, z ↦ 10]
```

Napaka v programu je v tem primeru če v okolju ni spremenljivke definirane v programu oz. nima dodeljene vrednosti.

Ponavadi ga označimo z $\eta$.

$$ $$
$$\eta = [x ↦ 3, y ↦ 7, z ↦ 10]$$

### Semantika velikih korakov

Semantika velikih korakov se imenuje tako, ker iz izraza (abstraktnega drevesa) dobimo njegovo vrednost (število) v enem »velikem« koraku. Predstavimo jo z relacijo

```
η | e ↪ n
```

kjer je `η` okolje, `e` je izraz in `n` celo število. Zgornji izraz preberemo takole:
»V okolju `η` se izraz `e` evalvira v število `n`.«
$e$ predstavlja abstraktno sintaksno drevo oz. simboli niso nujno vezani na operacije ki jih imamo v glavi - torej $*$ je lahko poljubna operacija če je tako definirano v konkretni implementaciji.

Na primer, pričakujemo, da velja

```
[x ↦ 3, y ↦ 2, z ↦ 5] | x + 2 * y ↪ 7
```

Pravila za računanje izrazov podamo kot **pravila sklepanja**. Pravilo sklepanja zapišemo takole:

$$ \frac{\;\;P_1\; P_2 \;\dots \;P_i\;\;}{S} $$

Ob $P_{1},...,P_{i}$ sklepamo na $S$. Oz. velja $P_{1} \land ... \land P_{i} \Rightarrow S \sim 1$.

Na primer:

$$ \frac{\;\;\;x > 0 \quad y < 0\;\;\;}{x \cdot y < 0} $$

Pravilu brez predpostavk pravimo **aksiom**

$$
\frac{\;\;\;\;\;\;\;\;\;\;\;\;}{S}
$$


Za semantiko velikih korakov veljajo naslednja pravila

Naj velja
* $\eta$ je okolje
* $n$ je število
* $e,e_{1},...$ so izrazi

Pravila:

$$\frac{\;\;\eta(x) = n\;\;}{\;\;\eta | x \hookrightarrow n\;\;}$$
$$ $$
$$\frac{}{\;\;\eta | n \hookrightarrow n\;\;}$$
$$ $$
$$\frac{\;\;\eta | e_1 \hookrightarrow n_1 \quad \eta | e_2 \hookrightarrow n_2 \quad n_1 \cdot n_2 = n\;\;}{\eta | e_1 * e_2 \hookrightarrow n}$$
$$ $$
$$\frac{\;\;\eta | e_1 \hookrightarrow n_1 \quad \eta | e_2 \hookrightarrow n_2 \quad n_1 + n_2 = n\;\;}{\eta | e_1 + e_2 \hookrightarrow n}$$

Pozor, v pravilu za seštevanje znak `+` nad črto pomeni matematično operacijo seštevanje,
pod črto pa je to del sintakse aritmetičnih izrazov, se pravi `+` je samo simbol v izrazu. Pri pravilu za množenje te težave nismo imeli, ker smo matematično množenje označili z `·`, množenje kot simbol pa z `*`.

*Torej ko vidimo simbol množenja in veljajo zgornji predikati potem se evalvira v skladu s predikati.*

### Semantika malih korakov

Semantika velikih korakov deluje hierarhično: najprej izračunamo vrednosti podizrazov in nato vrednost celotnega izraza. V šoli pa otroke učimo, da se računa »po korakih«, se pravi, da opravimo eno operacijo naenkrat. Tak postopek se imenuje **semantika malih korakov**. Podamo jo z relacijo $\mapsto$

$$\eta | e \mapsto e'$$

ki pove, kako naredimo en osnovni korak v računanju. $n_{i}$ predstavlja konstantno.
Pravila se glasijo:

$$\frac{}{\eta \mid x \mapsto \eta(x)}$$
$$ $$
$$\frac{\eta \mid e_1 \mapsto e_1'}{\eta \mid e_1 + e_2 \mapsto e_1' + e_2}$$
$$ $$
$$\frac{\eta \mid e_2 \mapsto e_2'}{\eta \mid n_1 + e_2 \mapsto n_1 + e_2'}$$
$$ $$
$$\frac{n_1 + n_2 = n}{\eta \mid n_1 + n_2 \mapsto n}$$
$$ $$
$$\frac{\eta \mid e_1 \mapsto e_1'}{\eta \mid e_1 * e_2 \mapsto e_1' * e_2}$$
$$ $$
$$\frac{\eta \mid e_2 \mapsto e_2'}{\eta \mid n_1 * e_2 \mapsto n_1 * e_2'}$$
$$ $$
$$\frac{n_1 \cdot n_2 = n}{\eta \mid n_1 * n_2 \mapsto n}$$


**Primer**

$$\eta = [x \mapsto 3, y \mapsto 2, z \mapsto 5]$$

$$\begin{aligned}
\eta \,&\mid  \,x + 2 * y \\
&\mapsto 3 + 2 * y \\
&\mapsto 3 + 2 * 2 \\
&\mapsto 3 + 4 \\
&\mapsto 7
\end{aligned}$$


Pravila ne dopuščajo nobene svobode pri računanju. Na primer, če želimo izračunati


$$[] \;|\; 2 * 3 + 5 * 6$$


potem *moramo* naprej izračunati `2 * 3`, da dobimo `6 + 5 * 6` in šele nato `5 * 6`, da dobimo `6 + 30`. Ugotovite, zakaj je tako.

**Primer**

Izvajanje se lahko tudi zatakne, na primer, če spremenljivka nima vrednosti:

```
[x ↦ 3]  |  x + 2 * y  ↦  3 + 2 * y
```

Naslednjega koraka ni, ker ne moremo uporabiti nobenega od pravil, ki so na voljo.

Torej je **operacijska semantika** formalen način opisovanja delovanja programov v splošnem kot zaporedje sprememb stanj in natančno definicijo kako se operacije izračunajo.