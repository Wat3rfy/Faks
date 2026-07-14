**Računski učinki**

Računski učinki so dejanja programa ki presegajo zgolj prejemanje vhoda in vračanje čistega rezultata.

To je lahko spreminjanje stanja - povečevanje števca, spreminjanje spomina,...

To je lahko vhod/izhod kjer izpisujemo besedilo na zaslon - program ima interakcijo z zunanjim svetom.

Delne funkcije in izjeme, kjer lahko prekinejo tok oz. program.

Nedeterminizem kjer je možnih več rezultatov.

Timeout- prekinitev delovanja če se predolgo izvaja.

Verjetnostno računanje kjer program vrača porazdelitev verjetnosti nad možnimi rezultati. *Recimo da program uoprablja neko naključje iz sveta, možnih je več rezultatov in imamo neko porazdelitev, dejansko pa dobimo samo en rezultat ko se dejansko izvede program, program sam pa dejansko predstavlja celotno porazdelitev*


*Vrstni red izvjanja je pomemben če je v programu več računskih učinkov kjer ni nujno da se enak oizvede vsakič*

**Monade**

Posplošujejo algebro.

Osnovna struktura - želimo ločit med čistimi vrednostmi *- že izračunani podatki* in izračuni *- izračun izvajamo, lahko ima računske učinke*.

- **return:** Čiste vrednosti lahko predstavimo kot izračun katerega rezultat je ta vrednost.
- **bind `>>=`** - kombiniranje izračunov

**Haskell**

Izračune simuliramo zato so predstavljeni s podatkovnimi tipi ki izražajo računske učinke.

Recimo $m : \text{Type} \rightarrow \text{Type}$, ki tip $A$ preslika v tip $A \,m$, kjer je vrednost tipa $A$ in sproža učinke $m$. 

Preslikava $\text{return : } a \rightarrow m \, a$ vrednost tipa $a$ predstavi kot čisti izračun.

Operacije $$>>= \,:  m \, a \rightarrow (a \rightarrow m \, b) \rightarrow m \, b$$

Naj bo $c_{1} >>= (\lambda\,x.c_{2})$
$c_{1}$ je izračun $m$ ki vrne $a$ torej $m\,a$, $c_{2}$ je izračun $m$ ki vrne $b$ torej se $m \,a$ slika v $m\,b$.

**Enačbe za monado**

Monada mora zadoščati

- `return x >>= f = f x` čemu rpravimo **leva enota**
- `c >>= return = c` čemu rpravimo **leva enota**
- **asociativnost** *oklepaji so lahko kjer koli.*

```
return x >>= f
[x] >>= f
concat(map f [x])
concat([f x])
f x

c >>= return
concat(map return c)
concat(return v1,...,return vn)
[v1,...,vn]
c
```

**Funktor**

```
t => (a -> b) -> t a -> t b
```