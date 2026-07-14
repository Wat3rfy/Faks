https://www.youtube.com/watch?v=KHCAhwd7y-U&list=PL-47DDuiZOMDFbeI0tsri7Z2IKiPafwqB&index=2

Rekurzija

Funkcija je rekurzivna ko kliče samo sebe.

```ocaml
f :: Integer -> Integer
f n = if n == 0 then 1 else n * f (n-1) 
```

Funkijco lahko razstavimo na dva dela
- telo rekurzije ki samo po sebi ni rekurzivno 
- in na rekurzivni sklic funkcije same nase


```ocaml
telo :: (Integer -> Integer) -> (Integer -> Integer)
telo self = \n -> if n == 0 then 1 else n * self (n-1)

f:: Integer -> Integer
f = telo f

```

Pravimo da smo razprli funkcijo rekurzivno zanko.

Rekurzivno funkcijo $f$ smo zapisali ko t negibno teočko funkcije telo

Negibna točka funkcije $h : X \rightarrow X$ je tak $x \in X$ da velja $x = h(x)$

*V tem primeru je $x$ naš cel funkcijski prostor.*

V numeričnih metodah lahko enačbo oblike $x = h(x)$ računamo z $x = h(h(h(h(...(h(x))))))$.


Z negibnimi točkami lahko računamo npr. binomski koeficient.

```haskell
binom :: (Integer, Integer) -> Integer
binom (n,k) = if k == 0 || k == n then 1 else binom (n-1,k-1)+ binom (n-1,k)
```

in lahko razpremo zanko

```haskell
telo :: (Integer,Integer)-> Integer -> (Integer, Integer) -> Integer
telo self = (n,k) -> if k == 0 || k == n then 1 ele self (n-1,k-1) + self(n-1,k)
```


Če hočemo imeti rekurzijo z dvema funkcijama imamo preprosto dva argumenta.


**Operator `fix`**

Recept za rekurzivno funckijo je edno isti
- telo `t` funkcije
- negibna točka `f = t f`

Torej lahko rečemo `fix` izračuna negibno točko dane funckije

```haskell
t : (a -> a) -> a
fix t = t (fix t)
```

kar gre v

```
t(t(t...(fix t)))
```


`a` je v tem primeru poljuben tip in mu pravimo **parameter**.

TOrej fakuletteta je

```haskell
f:: Integer -> Integer
f = fix(\ self n -> if n == 0 then 1 else n*self(n-1))
```


**Iteriranje**

Zanke kot so `while` so tudi primeru  rekurzije

```
while b do c done
```

```
if b then (c ; while b do c done) else skip
```

```haskell
W = (if b then (c; W) else skip)
```

**Rekurzivni seznami**

```
l = [1,2,1,2,1,2,1,...]
```

in to lahko rekurzivno definiramo

```
l = 1 : 2 : l
```

lahko naredimo npr.

```
fibs = 0:1:fibs zipWith (+) fibs (drop 1 fibs)
```

**Rekurzivni tipi**

Seznam je
- | prazen
- | sestavljen iz (glave - celo število) in (repa - seznam)

<br>

- prazen seznam `Nil` je seznam
- sestavljen seznam : `x` je celo število in `l` sseznam - potem je `Cons (x,l)` seznam


```ocaml
type seznam =
| Nil
| Cons of int * seznam
```

oz.

```
seznam = T (seznam)
```

```
T a = (Nil | Cons of int * a)
```

kjer se `a` zamenja za seznam.

Poznamo več vrst rekurzivnih tipov
- induktivni - morajo se končati
- koinduktivni - so lahko neskončni

Npr induktivna so
- naravna števila
- končni seznami
- končna drevesa
- abstraktna sintaksa jezika
	- programski jeziki
	- jeziki za označevanje podatkov
- hiearhija elementov v uporabniškem svetu

npr.:
- seznam je ali prazen (končen) ali pa je neka konstanta ki mu sledi ne končen seznam - spet končen.
- naravno število je spet ali nič ali pa naslednik nekega stevila

Primer je tudi JSON

```ocaml
type json = 
| String of string
| Number of int
| Object of (string * json) list
| Array of json array
| True
| False
| Null
```


**Splošni rekurzivni tipi**

**Strukturna rekurzija**

```ocaml
type searchtree = Empty | Node of int * searchtree * searchtree
```

V tpiu nismo shranili informacije o tem da je isklano drevo urejeno - torej rabi programer ustvariti urejeno iskalno drevo.

Strukturna rekurzija je torej lahko

```
let rec velikost' t =
match t with
| Empty -> 0
| Node (_, l, r) -> 1 + velikost l + velikost r
```

```
let rec velikost'' = 
fun t -> match t with
| Empty -> 0
| Node (_, l, r) -> 1 + velikost l + velikost r
```

```
let rec velikost = function
| Empty -> 0
| Node (_,l,r) - > + velikost l + velikost r
```

kaj če hočemo vzeti drevo in vrniti seznam v drevesu

```
let rec to_list = function
| Empty -> []
| Node (x,l,r) ->> to_lsit l @ [x] @ to_list r
```


**Koinduktivni tipi**

Komunikacijski tokovi...

še v haskellu...

še v ocamlu...

