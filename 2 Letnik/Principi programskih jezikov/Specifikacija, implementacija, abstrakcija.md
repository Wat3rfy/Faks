**Specifikacija & implementacija**

**Specifikacija (angl. specification)** $S$ je opis zahtev, ki definira, kakšen mora biti izdelek da ustreza potrebam naročnika.

**Implementacija (angl. implementation)** $I$ je izdelek. Implementacija $I$ *zadošča* specifikaciji $S$, če ustreza zahtevam iz $S$.

V praksi je specifikacija **vodilo za programerja**.

Začnemo z **dokumentacijo za naročnika** (kaj naj bi program delal), nato to prevedemo v **tehnične zahteve v kodi** (npr. vmesnike, ki definirajo tipe podatkov), na koncu pa uporabimo **avtomatizirane teste**, ki so najstrožja oblika specifikacije.

Če test vrne napako, pomeni, da naša **implementacija** ne ustreza **specifikaciji**, torej moramo  kodo popraviti, dokler testi ne potrdijo, da vse deluje točno tako, kot je bilo zahtevano.

Brez specifikacije ne vemo, kaj je treba naprogramirati. 

Za primer lahko pogledamo definicijo alg. struktur, ki poteka v dveh korakih:

* **signatura** pove, kakšne množice, konstante in operacije imamo
* **aksiomi** povedo, kakšnim zakonom morajo zadoščati operacije

> **Primer:**
> 
> Matematično strukturo **grupa** opišemo takole:
> 
> * signatura:
>     * množica $G$
>     * operacija $\cdot : G \times G \to G$
>     * operacija $^{-1} : G \to G$
>     * konstanta $e : G$
> * aksiomi:
>     ```
>     x · (y · z) = (x · y) · z
>     x · e = x
>     e · x = x
>     x · x⁻¹ = e
>     x⁻¹ · x = e
>     ```

> **Primer**
> 
> Matematično strukturo **usmerjen graf** opišemo takole:
> 
> * signatura:
>     * množica $V$ (vozlišča)
>     * množica $E$ (povezave)
>     * operacija $\text{src} : E \to V$ (začetno vozlišče povezave)
>     * operacija $\text{trg} : E \to V$ (končno vozlišče povezave)
> * aksiomi: ni aksiomov

Kako v programskih jezikih poskrbimo za zapis specifikacij in kako programski jezik preveri, ali dana koda (implementacija) zadošča dani specifikaciji.

V programskih jezikih to ponavadi storimo z omejitvo prostora možnih vrednosti.

- s **tipi** postavimo specifikacijo na neko spermenljivko `int x`, `string ime`,...
- z **interface** in **function signature** lahko definiramo kaj sprejme in vrne funkcija oz. nek objekt.
- s **komentarji**

Preverjanje specifikacije je lahko **statično** in **dinamično**. Statično pomeni analiziranje kode pred zagonom za skladnost tipov,... Dinamično pa pomeni preverjanje skladnosti tipov med izvajajnem programa.

Zapišemo lahko tudi **unit teste** s katerimi simuliramo uporabo kode.

***

**Vmesniki**

Specifikaciji včasih rečemo tudi **vmesnik (angl. interface)**, ker jo lahko razumemo kot opis, ki pove, kako se uporablja neko programsko kodo. Na primer, avtor programske knjižnice običajno objavi **API (Application Programming Interface)**, ki ni nič drugega kot specifikacija, ki pove, kako deluje knjižnica.

Torej imamo (vsaj) dve uporabi specifikacij:

* ko pišemo program na zunanjo zahtevo (specifikacija)
* protokol za uporabo programske kode (vmesnik)


**Vmesniki v Javi**

V Javi je specifikacija $S$ podana z vmesnikom

```java
public interface S {
    ...
}
```

v katerem lahko naštejemo metode. Tipe, ki nastopajo v specifikaciji, podamo kot generične razrede. Na primer, vmesnik za grupo bi zapisali takole:

```java
public interface Group<G> {
    public G getUnit();
    public G multiply(G x, G y);
    public G inverse(G x);
}
```

Vmesnik za usmerjeni graf:

```java
public interface Graph<V, E> {
    public V src(E e);
    public V trg(E e);
}
```

**Vmesniki v Ocamlu**

V OCamlu lahko podamo poljubno signaturo (tipe in vrednost), ne moremo pa zapisati aksiomov, ki jim zadoščajo. Takole zapišemo signaturo za grupo:

```ocaml
module type GROUP =
sig
  type g
  val mul : g * g -> g
  val inv : g -> g
  val e : g
end
```

In takole za usmerjeni graf:

```ocaml
module type DIRECTED_GRAPH =
sig
  type v
  type e
  val src : e -> v
  val trg : e -> v
end
```


***

**Implementacije**

Programski jeziki seveda omogočajo implementacijo, kar ni nič drugega kot pisanje kode, ki ustreza dani specifikaciji.

**Implementacija v Javi**

V Javi implementiramo vmesnik $I$ tako, da definiramo razred $C$, ki mu zadošča:

```java
public class C implements I {
    ...
}
```

Razred lahko hkrati zadošča več vmesnikom.

**Implementacija v Ocamlu**

Implementacija v OCamlu se imenuje **modul (angl. module)**. Modul je skupek definicij tipov in vrednosti, lahko pa vsebuje tudi še nadaljnje podmodule.

Nekaj primerov (nepraktičnih) implementacij grup podajmo tu, kasneje pa bomo videli bolj uporabne primere:

```Ocaml
(* Najprej definiramo signature. *)

module type GROUP =
sig
    type g
    val mul : g * g -> g
    val inv : g -> g
    val e : g
end

module type DIRECTED_GRAPH =
sig
    type v
    type e
    val src : e -> v
    val trg : e -> v
end

(* Signaturo implementiramo z modulom ali strukturo.
   Dana signatura ima lahko več implementacij. *)

module Z3 : GROUP =
struct

  type g = Zero | One | Two

  let e = Zero

  let plus = function
    | (Zero, y) -> y
    | (x, Zero) -> x
    | (One, One) -> Two
    | (One, Two) -> Zero
    | (Two, One) -> Zero
    | (Two, Two) -> One

  let mul = plus

  let inv = function
    | Zero -> Zero
    | One -> Two
    | Two -> One
end

module Z3' : GROUP =
struct

    type g = int

    let mul (x, y) = (x + y) mod 3
    let inv x = (3 - x) mod 3
    let e = 0
end

module K4 : DIRECTED_GRAPH =
struct

    type v = V0 | V1 | V2 | V3
    type e = E0 | E1 | E2 | E3 | E4 | E5

    let src = function
      | E0 -> V0
      | E1 -> V1
      | E2 -> V2
      | E3 -> V3
      | E4 -> V0
      | E5 -> V1

    let trg = function
      | E0 -> V1
      | E1 -> V2
      | E2 -> V3
      | E3 -> V0
      | E4 -> V2
      | E5 -> V3
end

module Cycle3 : DIRECTED_GRAPH =
struct
  type v = int (* uporabimo 0, 1, 2 *)
  type e = int (* uporabimo 0, 1, 2 *)
  let src e = e
  let trg e = (e + 1) mod 3

  (* Graf z vozlišči 0, 1, 2 in povezavami 0, 1, 2:
        src    trg
     0 : 0 --> 1
     1 : 1 --> 2
     2 : 2 --> 0
  *)
end

(* Takole pa naredimo modul, ki je parametriziran s
   strukturo. Kasneje bomo videli bolj uporabne primere. *)
module Cycle (S : sig val n : int end) : DIRECTED_GRAPH =
struct
  type v = int
  type e = int
  let src k = k
  let trg k = (k + 1) mod S.n
end

module C5 = Cycle(struct let n = 5 end)
module C15 = Cycle(struct let n = 15 end)
```

***

**Abstrakcija**


Ko gradimo večje programske sisteme, so ti sestavljeni iz enot, ki jih povezujemo med seboj. Za vsako enoto je lahko zadolžena ločena ekipa programerjev. Programerji opišejo programske enote z *vmesniki*, da vedo, kaj kdo počne in kako uporabljati kodo ostalih ekip.

A to je le del zgodbe. Denimo, da prva ekipa razvija programsko enoto `E`, ki zadošča vmesniku `S` in da druga ekipa uporablja enoto `E` pri izdelavi svoje programske enote. Dobra programska praksa pravi, da se druga ekipa ne sme zanašati na podrobnosti implementacije `E`, ampak samo na to, kar je zapisano v specifikaciji `S`. Na primer, če `E` vsebuje pomožno funkcijo `f`, ki je `S` ne omenja, potem je druga ekipa ne sme uporabljati, saj je `f` namenjena *notranji* uporabi `E`. Prva ekipa lahko `f` spremeni ali zbriše, saj `f` ni del specifikacije `S`.

Če sledimo načelu, da mora programski jezik neposredno podpirati aktivnosti programerjev, potem bi želeli *skriti* podrobnosti implementacije `E` tako, da bi lahko programerji druge ekipe imeli dostop *samo* do tistih delov `E`, ki so našteti v `S`.

Kadar *skrijemo* podrobnosti implementacije, pravimo, da je implementacija **abstraktna**.

Programski jeziki omogočajo abstrakcijo v večji ali manjši meri:

* Java nadzoruje dostopnost do komponent z določili `private`, `public` in `protected`
* Python omogoča skrivanje s poimenovanjem `__xyz` (glej name mangling).
* OCaml omogoča abstrakcijo z določilom `M : S`, kjer je `M` module in `S` signatura. S tem skrijemo vsebino modula `M`, razen tistih komponent, ki so naštete v `S`.

<br>

**Generično programiranje**

Z izrazom _generično programiranje_ razumemo kodo, ki jo lahko uporabimo večkrat na različne načine. Na primer, če napišemo knjižnico za 3D grafiko, bi jo želeli uporabljati na več različnih grafičnih karticah. Ali bomo za vsako grafično kartico napisali novo različico knjižnice? Ne! Želimo **generično** implementacijo, ki bo preko ustreznega _vmesnika_ dostopala do grafične kartice. Proizvajalci grafičnih kartic bodo implementirali _gonilnike_, ki bodo zadoščali temu vmesniku.

**Java**

Java podpira generično programiranje. Ko definiramo razred, je ta lahko odvisen od kakega drugega razreda:

```java
public class Knjiznica3D<Driver extends GraphicsDriver> {
  ...
}
```

**Ocaml**

V OCamlu je generično programiranje omogočeno s **funktorji (angl. functor)**.

Funktor je preslikava iz struktur v strukture in je bolj splošen kot generični razredi v Javi (ker lahko struktura vsebuje podstrukture in definicije več tipov, razred pa ne more vsebovati definicij podrazredov).

Funktor `F`, ki sprejme strukturo `A`, ki zadošča signaturi `S`, in vrne strukturo `B` zapišemo takole:

```ocaml
module F(A : S) =
struct
  (* definicija strukture B *)
end
```
Zgoraj smo videli primer preprostega funktorja `Cycle`, ki sprejme strukturo s številom `n` in vrne usmerjeni cikel na `n` vozliščih. Bolj uporaben primer sledi.

***

**Primer:**

**Prioritetna vrsta** je podatkovna struktura, v katero dodajamo elemente, ven pa jih jemljemo glede na njihovo prioriteto. Zapišimo specifikacijo:

**Signatura:**
* podatkovni tip `element`
* operacija `priority : element -> int`
* podatkovni tip `queue`
* konstanta `empty : queue`
* operacija `put : element -> queue -> queue`
* operacija `get : queue -> element option * queue`

Aksiomov ne bomo pisali, ker bi morali v tem primeru spoznati bolj zahtevne jezike za specifikacijo, ki presegajo okvir te lekcije. Neformalno pa lahko opišemo zahteve za prioritetno vrsto:

* `element` je tip elementov, ki jih hranimo v vrsti
* `priority x` vrne prioriteto elementa `x`, ki je celo število. Manjše število pomeni »prej na vrsti«
* `queue` je tip prioritetnih vrst
* `empty` je prazna prioritetna vrsta, ki ne vsebuje elementov
* `put x q` vstavi element `x` v vrsto `q` glede na njegovo prioriteto in vrne tako dobljeno vrsto
* `get q` vrne `(Some x, q')` kjer je `x` element iz `q` z najnižjo prioriteto in `q'` vrsta `q` brez `x`. Operacija `get` vrne `(None, q)`, če je `q` prazna vrsta.

```Ocaml
module type PRIORITY_QUEUE =
  sig
    type element
    val priority : element -> int
    type queue
    val empty : queue
    val put : element -> queue -> queue
    val get : queue -> element option * queue
  end

module MyFirstQueue : PRIORITY_QUEUE with type element = int * int =
  struct
    type element = int * int

    let priority (a, b) = a

    type queue = element list

    let empty = []

    let rec put x = function
      | [] -> [x]
      | y :: ys ->
         if priority x <= priority y then
           x :: y :: ys
         else
           y :: put x ys

    let get = function
      | [] -> (None, [])
      | x :: xs -> (Some x, xs)
  end

module type PRIORITY =
sig
  type t
  val priority : t -> int
end


(* Implementacija prioritetne vrste s seznami. To je funktor, ki
   sprejme tip elemetov in prioritetno funkcijo. *)
module ListQueue (M : PRIORITY) : PRIORITY_QUEUE with type element = M.t
  =
  struct
    type element = M.t

    let priority = M.priority

    type queue = element list

    let fortytwo = 42

    let empty = []

    let rec put x = function
      | [] -> [x]
      | y :: ys ->
         if priority x <= priority y then
           x :: y :: ys
         else
           y :: put x ys

    let get = function
      | [] -> (None, [])
      | x :: xs -> (Some x, xs)
  end

(* Naredimo prioritetno vrsto nizov, prioriteta je dolžina niza. *)
module A =
  ListQueue(
      struct
        type t = string
        let priority = String.length
      end)

(* Preizkus. *)
let example1 =
  A.get (A.put "kiwi" (A.put "jabolko" (A.put "banana" A.empty)))

(* Naredimo prioritetno vrsto nizov, prioriteta je dolžina niza. *)
module A' =
  ListQueue(
      struct
        type t = string
        let priority s = - String.length s
      end)

(* Preizkus. *)
let example1' =
  A'.get (A'.put "kiwi" (A'.put "jabolko" (A'.put "banana" A'.empty)))

(* Naredimo prioritetno vrsto parov števil. *)
module B =
  ListQueue(
      struct
        type t = int * int
        let priority (a,b) = a
      end
    )

module IntQueue =
  ListQueue(
    struct
      type t = int
      let priority k = k
    end
  )


(* Učinkovita implementacija z levičarskimi kopicami,
   glej https://en.wikipedia.org/wiki/Leftist_tree.
   Implementacija je abstraktna, ker uporabimo :,
   vendar dodamo določilo, da je tip element enak tipu t.
 *)
module LeftistHeapQueue (M : PRIORITY)
       : PRIORITY_QUEUE with type element = M.t =
  struct
    type element = M.t

    let priority = M.priority

    type queue = Leaf | Node of int * element * queue * queue

    let rank = function
      | Leaf -> 0
      | Node (r, _, _, _) -> r

    let node (x, a, b) =
      if rank a < rank b then
        Node (1 + rank a, x, b, a)
      else
        Node (1 + rank b, x, a, b)

    let rec meld a b =
      match (a, b) with
      | (_, Leaf) -> a
      | (Leaf, _) -> b
      | (Node (_, ka, la, ra), Node (_, kb, lb, rb)) ->
         if priority ka < priority kb then
           node (ka, la, meld ra b)
         else
           node (kb, lb, meld a rb)

    let singleton x = Node (1, x, Leaf, Leaf)

    let empty = Leaf

    let put x q = meld q (singleton x)

    let get = function
      | Leaf -> (None, Leaf)
      | Node (_, y, l, r) -> (Some y, meld l r)
  end


module D = LeftistHeapQueue(
               struct
                 type t = int * int
                 let priority (x, y) = x + y
               end)

let example2 =
  let rec loop q = function
    | 0 -> D.put (0, 0) q
    | k -> loop (D.put ((47 * k * k + 13) mod 1000, k) q) (k - 1)
  in
  loop D.empty 300000

let rec to_list q =
  match D.get q with
  | (None, _) -> []
  | (Some x, q) -> x :: to_list q
```

**Implementacija v Javi**

Signatura:
* podatkovni tip `Element`
* metoda `priority : element -> int`
* podatkovni tip `queue`
* operacija `empty : unit -> queue`
* operacija `is_empty : queue -> bool`
* operacija `put : element -> queue -> unit`
* operacija `get : queue -> element option`

Zahteve so podobne kot prej, le da operacije `empty`, `put` in `get` delujejo nekoliko drugače:
* `empty ()` vrne nov objekt prazne vrste
* `put x q` vstavi `x` v vrsto `q` in s tem *spremeni* `q`
* `get q` vrne prvi `x` v vrsti `q` in s tem *spremeni* `q`

Zgornjo specifikacijo predelamo v dva vmesnika. Prvi je vmesnik za razrede, ki imajo metodo `priority`:

```java
public interface Priority {
    public int priority();
}
```

Vmesnik `PriorityQueue` pa podaja specifikacijo za prioritetno vrsto:

```java
public interface PriorityQueue<Element extends Priority> {
    public PriorityQueue<Element> emptyQueue();
    public boolean isEmpty();
    public void put(Element x);
    public Element get();
}
```

Še primer implementacije prioritetnih vrst s seznami:

```java
import java.util.LinkedList;

public class ListQueue<Element extends Priority> implements PriorityQueue<Element> {
    private LinkedList<Element> elements;

    public ListQueue() {
        elements = new LinkedList<Element>();
    }

    @Override
    public boolean isEmpty() {
        return elements.isEmpty();
    }

    @Override
    public void put(Element x) {
        int i = 0;
        for (Element y : elements) {
            if (x.priority() < y.priority()) {
                break;
            } else {
                i += 1;
            }
        }
        elements.add(i, x);
    }

    @Override
    public Element get() {
        return elements.removeFirst();
    }

    @Override
    public PriorityQueue<Element> emptyQueue() {
        return new ListQueue<Element>();
    }
}
```