Haskell lahko opredelimo kot programski jezik, ki je:

* deklarativni jezik z leno evaluacijo
* je funkcijski jezik: funkcije so vrednosti
* ima koinduktivne tipe in zapise
* ima parametrični polimorfizem in izpeljavo tipov
* čist jezik: vsi računski učinki (stanje, I/O, izjeme) so eksplicitno zavedeni v tipu izraza
* ima razrede tipov

Razredi tipov (angl. type classes), so še en način za organizacijo kode in funkcionalnosti. Haskell je deklarativni jezik, ki se odlikuje po tem, da je tudi čist (angl. pure), kar pomeni, da v osnovi nima računskih učinkov (stanje, I/O, izjeme). O računskih učinkih in o tem, kako so implementirani z monadami, bomo govorili naslednjič.

**Osnovno o Haskellu**

Mnoge koncepte, ki nastopaj v programskem jeziku Haskell, že poznamo. Danes bomo spoznali

**Zamikanje**

V Haskellu je treba kodo pravilno zamikati, podobno kot v Pythonu. V nekaterih primerih se lahko zamikanju izognemo z uporabo alternativne sintakse { ... ; ... ; ... }. Primer bomo videli kasneje.

**Imena**

* Imena spremenljivk se pišejo z malo začetnico: x, y, ...
* Imena tipov se pišejo z veliko začetnico: Int, Bool, Char, ...
* Parametri v polimorfnih tipih se pišejo z malo začetnico: a, b, c, ...
* Imena konstruktorjev algebraičnih tipov se pišejo z veliko

**Definicije**

Vrednost `t` tipa `A` zapišemo

```haskell
t :: A
t = definicija-t
```

Pozor: zapis `t :: A` pomeni `t` ima tipa `A`, zapis `x : l` pa pomeni seznam z glavo `x` in repom `l` (ravno obratno kot v OCamlu).

Definicija ima lahko tudi več vrstic, na primer:

```haskell
f :: Int -> Int
f 0 = 1
f 1 = 1
f n = n * f (n - 1)
```

Definicije so lahko rekurzivne.

Tip v definiciji ni treba podati in smemo zapisati samo

```haskell
t = definicija-t
```

V tem primeru bo Haskell izpeljal tip `t`. Vendar pa je v Haskellu navada, da se zapiše tip vrednosti, ki jo definiramo.

**Lokalne definicije**

Lokalno definicijo zapišemo

```haskell
let x = e1
in
    e2
```

ali

```haskell
e2 where x = e1
```

Določil `where` lahko sledi več definicij:

```haskell
e1 where
    x = e2
    y = e3
    z = e4
```

**Seznami**

Prazen seznam zapišemo z `[]`, stik glave `x` z repom `l` zapišemo `x : l`, elemente lahko tudi naštejemo z `[x1, x2, ..., xi]`.

Seznam števil od `1` do `n` zapišemo `[1..n]` in podobno za interval `[a..b]`.

Haskell ima izpeljane sezname (angl. list comprehension), podobno kot Python:

* matematika: `{f(x) | x ∈ A}` je množica elementov `f(x)`, kjer je `x ∈ A`
* Python `[f(x) for x in l]` je seznam elementov `f(x)`, kjer `x` preteče seznam `l`
* Haskell `[f x | x <- l]` je seznam elementov `f x`, kjer `x` preteče seznam `l`

Podrobnosti o izpeljanih seznamih si preberite na zgornji povezavi.

**Izraz `case`**

Izraz

```haskell
case e of
    p1 -> e1
    p2 -> e2
    ...
    pj -> ej
```

primerja `e` z vzorci `p1, ..., pj`. Vrednost izraza je enaka `ei`, kjer je `pi` prvi vzorec, ki se ujema. Torej je `case` podoben izrazu `match` iz OCaml.

> **Opozorilo**
> OCaml opozori na manjkajoče primere v `match`, Haskell tega ne počne. Če uporabimo opcijo `-Wall` (vsa opozorila), nas opozori na manjkajoče primere.

Primeri morajo biti pravilno zamaknjeni, lahko pa uporabimo tudi sintakso

```haskell
case e of { p1 -> e1 ; ... ; pj -> ej }
```

ki ne zahteva zamikanja. V Haskellu velja navada, da raje zamikamo kodo, kot da bi uporabljali `{ ... }`.

**Tipi**

Imena tipov pišemo z velikimi črkami

* Osnovni tipi so `Int`, `Char`, `Bool`, ...
* `a -> b` je tip funkcij iz `a` v `b`
* `(a, b)` je produktni tip, ki ga v OCamlu pišemo `a * b`
* `[a]` je tip seznamov elementov tipa `a`, v OCamlu `a list`

Haskell pozna definicije tipov

```haskell
type T = ...
```

in definicije (koinduktivnih) algebraičnih tipov

```haskell
data T = ...
```

Definicija `type` uvaja okrajšavo, `data` pa nov podatkovni tip.

(Tipe lahko definiramo tudi z `newtype`, ki ga ta trenutek ne bomo obravnavali.)

Na primer, sezname lahko definiramo takole:

```haskell
data List a =
    Nil
  | Cons (a, List a)
```

Tip `Maybe` je definiran z

```haskell
data Maybe a =
    Nothing
  | Just a
```

To je pravzaprav tip `a option` iz OCaml.

**Primer: AVL drevesa**

```haskell
-- AVL drevesa v Haskellu

module Avl where

  -- višino drevesa merimo s celim številom
  type Height = Integer

  -- koinduktivni podatkovni tip AVL dreves
  data AVLTree a =
      Empty
    | Node a Height (AVLTree a) (AVLTree a)
    deriving Show

  -- primer drevesa
  t :: AVLTree Integer
  t = Node 5 3
      (Node 3 2
       (Node 1 1 Empty Empty)
       (Node 4 1 Empty Empty))
      (Node 8 1 Empty Empty)

  height :: AVLTree a -> Height
  height Empty = 0
  height (Node _ h _ _) = h

  leaf :: a -> AVLTree a
  leaf v = Node v 1 Empty Empty

  -- pametni konstruktor, ki poskrbi za višino
  node :: a -> AVLTree a -> AVLTree a -> AVLTree a
  node v l r = Node v (1 + max (height l) (height r)) l r

  -- drevo t zapisano s pamentim konstruktorjem
  t' :: AVLTree Integer
  t' = node 5
        (node 3
         (node 1 Empty Empty)
         (node 4 Empty Empty))
        (node 8 Empty Empty)

  -- drevo t zapisano še bolje
  t'' :: AVLTree Integer
  t'' = node 5
        (node 3
         (leaf 1)
         (leaf 4))
        (leaf 8)

  -- seznam elementov v drevesu
  toList :: AVLTree a -> [a]
  toList Empty = []
  toList (Node x _ l r) = toList l ++ (x : toList r)

  search :: Ord a => a -> AVLTree a -> Bool
  search x Empty = False
  search x (Node y _ l r) =
      case compare x y of
        EQ -> True
        LT -> search x l
        GT -> search x r

  test1 = search 1 t

  test2 = search 42 t

  rotateLeft :: AVLTree a -> AVLTree a
  rotateLeft (Node x _ a (Node y _ b c)) = node y (node x a b) c
  rotateLeft t = t

  rotateRight :: AVLTree a -> AVLTree a
  rotateRight (Node y _ (Node x _ a b) c) = node x a (node y b c)
  rotateRight t = t

  imbalance :: AVLTree a -> Integer
  imbalance Empty = 0
  imbalance (Node _ _ l r) = height l - height r

  balance :: AVLTree a -> AVLTree a
  balance Empty = Empty
  balance (t@(Node x _ l r)) =
      case imbalance t of
        2 ->  case imbalance l of
                -1 -> rotateRight (node x (rotateLeft l) r)
                _ ->  rotateRight t
        -2 -> case imbalance r of
                1 -> rotateLeft (node x l (rotateRight r))
                _ -> rotateLeft t
        _ -> t

  add :: Ord a => a -> AVLTree a -> AVLTree a
  add x Empty = leaf x
  add x (t@(Node y _ l r)) =
      case compare x y of
        EQ -> t
        LT -> balance (node y (add x l) r)
        GT -> balance (node y l (add x r))

  remove :: Ord a => a -> AVLTree a -> AVLTree a
  remove x Empty = Empty
  remove x (Node y _ l r) =
      let removeSuccessor Empty = error "impossible"
          removeSuccessor (Node x _ Empty r) = (r, x)
          removeSuccessor (Node x _ l r) = (balance (node x l' r), y) where (l', y) = removeSuccessor l
      in
        case compare x y of
          LT -> balance (node y (remove x l) r)
          GT -> balance (node y l (remove x r))
          EQ -> case (l, r) of
                  (_, Empty) -> l
                  (Empty, _) -> r
                  _ -> balance (node y' l r') where (r', y') = removeSuccessor r
```

**Razredi tipov**

Razred tipov (angl. *type class*) je način, kako v Haskellu opišemo skupino tipov, ki si delijo neko skupno funkcionalnost. Razred določa imena in tipe operacij (nekakšen vmesnik), tipi pa postanejo njegovi člani tako, da podajo instanco, v kateri te operacije implementirajo. Polimorfne funkcije lahko nato zahtevajo, da je njihov tipni parameter `a` v določenem razredu, in s tem dobijo na voljo pripadajoče operacije. V tem smislu so razredi tipov sorodni vmesnikom (angl. *interface*) v objektno usmerjenih jezikih, le da pripadnost razredu ni del same definicije tipa, temveč jo lahko dodamo naknadno z ločeno deklaracijo `instance`. Razredi tipov so tudi mehanizem, s katerim Haskell rešuje ad-hoc polimorfizem: ista operacija (npr. `==` ali `show`) se za različne tipe obnaša različno, prevajalnik pa glede na tip argumenta sam izbere ustrezno instanco.

Razrede tipov bomo razložili v živo na predavanjih s primerom `size.hs`, ki ilustrira osnovno idejo:

* Z deklaracijo `class Sized a where size :: a -> Int` uvedemo razred `Sized`, ki opisuje tiste tipe `a`, katerih vrednosti imajo neko »velikost«, izraženo s celim številom. Razred sam po sebi ne podaja implementacije; določa zgolj, da mora vsak član ponuditi funkcijo `size`.
* Funkcija `f :: Sized a => a -> Int` je polimorfna, a omejena: deluje za poljuben tip `a`, ki je v razredu `Sized`. Zapis `Sized a =>` pred tipom imenujemo omejitev (angl. *constraint*) in pove, da se sme znotraj `f` na vrednosti tipa `a` uporabiti operacija `size`.
* Z deklaracijami `instance` posameznim tipom dodelimo članstvo v razredu: za `Bool`, `Char` in `Int` enostavno povemo, koliko bitov zavzamejo. Pri tem ima vsaka instanca popoln dostop do strukture svojega tipa, zato lahko npr. instanca za `Bool` ujema vzorca `True` in `False`.
* Zapis `instance Sized a => Sized [a]` pove: če je `a` v razredu `Sized`, je tudi `[a]` v razredu `Sized`, velikost seznama pa je vsota velikosti njegovih elementov. Podobno za pare. Tako lahko iz nekaj osnovnih instanc samodejno izpeljemo velikost zelo bogatih tipov.

```haskell
-- Ideja: podatki imajo neko velikost
-- Funkcionalnost: tipi, katerih vrednosti imajo "velikost"

-- Razred, ki opisuje tiste tipe a, ki so opremljeni s funkcijo "size", ki slika v Int
class Sized a where
    size :: a -> Int

-- Funkcija, ki vrne velikost svojega argumenta, povečana za 3
f :: Sized a => a -> Int
f x = size x * 3

-- Booli so veliki 1 bit
instance Sized Bool where
    size True = 1
    size False = 1

-- Chari imajo velikost 8 bitov
instance Sized Char where
    size _ = 8

-- Inti so veliki 64 bitov
instance Sized Int where
    size x = 64

-- Velikost seznamov
instance Sized a => Sized [a] where
    size [] = 0
    size (x : xs) = size x + size xs

-- Velikost parov
instance (Sized a, Sized b) => Sized (a,b) where
    size (x, y) = size x + size y

-- Primeri

-- V Haskellu so nizi seznami znakov, se pravi [Char], zato Haskell iz zgornjih
-- instanc izpelje velikost niza kot 8 * dolžina niza.
demo1 = size "This string contains forty-two characters."

-- Če napišemo samo 14, dobimo tip Num a => a, če pa napišemo 14 :: Int,
-- Haskell prislimo, da ima 14 tip Int. (Če bi napisali 14 :: Float, bi
-- ga prisilil, da bi imel tip Float).
demo2 = size [(14 :: Int), 15]

demo3 = size ("foo", (False, 42 :: Int))
```

**Razredi tipov v standardni knjižnici**

Ogledali si bomo nekatere najbolj uporabne razrede v standardni knjižnici.

`Eq`

Razred tipov, katerih vrednosti lahko primerjamo na enakost. Ponuja operatorja `==` in `/=` (neenakost). V razred sodijo vsi tipi, pri katerih ima primerjanje smisel: osnovni tipi, seznami in pari elementov iz `Eq`, uporabniško definirani podatkovni tipi (`data`), ... Funkcije in akcije z računskimi učinki vanj ne sodijo.

`Ord`

Razred tipov z **linearno urejenostjo**. Razširja `Eq` in doda primerjalne operatorje `<`, `<=`, `>`, `>=` ter funkciji `min` in `max`. Tipično je dovolj implementirati eno od metod (`compare` ali `<=`), ostale Haskell izpelje samodejno. Za sestavljene tipe (npr. pare in sezname) je standardna instanca **leksikografska**.

`Show`

Razred tipov, katerih vrednosti znamo pretvoriti v niz znakov z metodo `show :: a -> String`. Uporablja se za izpis vrednosti v REPL-u in pri razhroščevanju. Sorodni razred `Read` opisuje obratno operacijo: razčlenjevanje niza v vrednost.

**Numerični razredi**

Številski tipi v Haskellu so organizirani v hierarhijo razredov, ki vsak doda nove operacije:

* `Num` — osnovne aritmetične operacije `+`, `-`, `*`, `negate`, `abs`, `fromInteger`.
* `Integral` — celoštevilske operacije, kot sta `div` in `mod` (npr. `Int`, `Integer`).
* `Fractional` — deljenje `/` in `recip` (npr. `Float`, `Double`, `Rational`).
* `Floating` — transcendentne funkcije, kot so `sqrt`, `exp`, `log`, `sin`, `cos`.

Zaradi te hierarhije ima številska konstanta `14` polimorfni tip `Num a => a` in se specializira glede na kontekst.

---

`Functor`

Razred **enoparametričnih konstruktorjev tipov** (oblike `f a`), ki znajo preslikati funkcijo nad svojo vsebino. Edina metoda je `fmap :: (a -> b) -> f a -> f b`, ki posploši `map` s seznamov na poljuben funktor. V razred sodijo `[]`, `Maybe`, `Either e`, `IO`, drevesa, ... Instanca mora spoštovati **zakona funktorja**: ohranjanje identitete in kompozicije.

 `Applicative`

Razred, ki razširja `Functor` in omogoča delo s funkcijami več argumentov v kontekstu `f`. Doda `pure :: a -> f a` (vstavi vrednost v kontekst) in `(<*>) :: f (a -> b) -> f a -> f b` (uporabi funkcijo v kontekstu na argument v kontekstu). `Applicative` je ključen vmesni korak med funktorji in **monadami**, ki jih bomo spoznali naslednjič.