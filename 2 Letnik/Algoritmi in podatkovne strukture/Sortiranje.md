
Random sort
premutation sort
selection sort
insertion sort
bubble sort

merimo čas izvajanja
št operacij

kje mermimo 

najboljši, nasjabši povprečni primer
velikost pod./primerov

Računska zahtevnost ( kompleksnost)
- časovna (koliko operacij izvajamo)
- prostorska (koliko pomnilnika)

asimptotična računska zahtevnost

zogrnja meja - simptotočna časovna zahtevnost - notacija $O(n), O(n^2)$ $n \rightarrow \infty$

$$f(n) = O(n^{2}) \Rightarrow \exists C \ni: \lim_{n \to \infty} f(n) < Cn^{2}$$

$$\lim_{n \to \infty}\frac{f(n)}{g(n)} < \infty$$


$$f(n) = \frac{1}{2}(n-1)(n+2)\log{n} + \sqrt[]{n}$$

v katerem $O(n)$ je

glavne:
- $O(1)$
- $O(\log n)$
- $O(n)$
- $O(n \log n)$
- $O(n^{2})$
- $O(n^c)$ - polinomska
- $O(k^{n})$
- $O(\sqrt[]{n})$


Če imamo funkcije z več spremenljivkami lahko dobimo
$n^{2}\log m$

Primeri

$100 + 2n + 3n^{2} =(n^{2})$
$3n \cos\,\! 2\pi n + \frac{n}{\log n} + 2n = O(n)$
$1+n \log n + n^{1.5} = O(n^{1.5})$
$f(n) = n+f\left(\frac{n}{2}\right)= O(n)$


**Napredno urejanje**

Merge sort
quick sort
heap sort


**Urejanje brez primerjav**

s frekvenčno tabelo - v neko tabelo če se pojavi število incrememntamo na tistem indeksu za 1.

Bucket / bin sort

Radix sort

binary search
(bisekcija)

Abstraction podatkovni tipi
- mn. možnih vrednosti
- operacije
- funkcionalnost
- implementacije

Podatkovna struktura
- implementacija

POLJE
- init(c)
- set (i,x)
- get(i)
- size()/cpactiy

SKLAD
- last in first out
- push(x)
- pop()
- peek/top() // pop push skupaj iig
- size()


pod. str. za implementacijo?
- povezan sieznam
- dinamično polje (VEKTRO)

SEZNAM
- add(x)
- remove(x)
- size()
- traverse()
- get(i)
pod. str. za implementacijo
- poevzan seznam
- dinamično polje

**Dinamično polje** // Dynamic array ali vector

Kopiranje arraya in dodajat element je počasno obv. ker rabimo za vsak dodan element $O(n^2)$ al neki

In boljša rešitev je da namest da povečuješ za ena povečuješ za več zato da ne rabimo vedno torej sacrificamo prostor za čas.


Vsakič ko dodamo nov element v vektor vektor dolžino podvojimo.

Armotizirana časovna zahtevnost: $O(1)$, čas zahtevnost za push $O(n)$

1+2+4+8+... < 4n = O(n)

Basically ce imamo $n-4$ kapacitete in hočemo dodati $n$ elementov imamo naprej dodajanje $n$ elementov kar je $O(n)$, potem ugotovimo da presegamo meje in moramo podvojiti tabelo kar bo $O(2n)$ potem pa hočemo dodati še te 4 elemente ki so ostali in imamo

$$n+2n+4$$
$$3n+4$$

kar je 

$$<4n$$

al enki tazga ne vem se



DINAMIČNO POLJE

push()
pop()
set, get

VRSTA

fifo
push/enqueue
pop/dequeue
front/peek
sizeen
Kako dosežemo funckionalnost vrste????

povezan seznam oz. liniked list
dinamično polje
sklad (več skladov) kinda stupid


##### VRSTA S PREDNOSTJO

Zlagamo elemente v vrsto ampak ima vsak element prirejeno se nek o prioriteto in vzamemo tistega ki ima največjo prioriteto.

insert/push
pull/pop
peek&/front


BUCKET QUEUE


DVOJIŠKE KOPICA

- struktura - poravnano dvojiško drevo
- vsebina - starš $\leq$ otrok (min-heap)

kaj lahko povemo o korenu

- minimalen element
- višina $\log n$

push(x) Ologn 
pop() Ologn