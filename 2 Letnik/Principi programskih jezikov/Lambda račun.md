
**Funkcijski predpis** je zapis

$$x \mapsto e$$

kjer je $e$ nek izraz ki vključuje $x$

Imenujemo jih **anonimne funkcije** ker niso poimenovane.

Lahko jim damo ime npr.  $f : x \mapsto e$.

Funkcija $f$ je **določen oz. poimenovan funkcijski predpis** skupaj z **domeno** in **kodomeno**. Sam funkcijski predpis ne določa funkcije.

**$\lambda$ račun** je sestavljen samo iz funkcijskih predpisov - je račun oz. je sistem za računanje s simboli.

Funkcijski predpis lahko uporabimo na **argumentu**. 

$$(x \mapsto x^{2})(3)$$

Temu pravimo **aplikacija**.

Lambda račun **definiramo rekurzivno.**
Naj bo $V$ množica spremenljivk. Množico $\Lambda$ definiramo kot

$$x \in X \Rightarrow x \in \Lambda$$
$$A \in \Lambda, B \in \Lambda \Rightarrow A B \in \Lambda$$
$$A \in \Lambda,x \in V \Rightarrow \lambda x.A \in \Lambda$$

**Aplikacijo** $\lambda x.e(n)$ pišemo tudi kot $\lambda x.e \,n$ in je **levo asociativna** - $\lambda x.e\, n\, m = (\lambda x.e \,n)\, m$

$\text{FV}(M)$ so vse **proste** spremenljivke člena $M$. Indukitvno definirano

$$\text{FV}(x) = \{ x\}$$
$$\text{FV}(M_{1},M_{2}) = \text{FV}(M_{1}) \cup FV(M_{2})$$
$$FV(\lambda x.M) = \text{FV}(M)\backslash\{ x\}$$

Če je $x \in FV(M)$ in imamo $\lambda x.M$ potem je $x$ **vezana** v $M$, za poljuben $y \in FV(M)$ pa velja da je še vedno prost oz. $y \in \text{FV}(\lambda x.M)$

Izrazu $\lambda x.M$ pravimo tudi **lambda abstrakcija** *izraza $M$ na spremenljivko $x$*.

**$\beta$ redukcija** je uporabljena za aplikacijo člena $N$ na $\lambda x.M$ torej $\lambda x.M \,N$ in velja 

$$\lambda x.M \, N \rightarrow M[N/x]$$

in dobimo izraz $M$ kjer je vsaka pojavitev $x$ zamenjana z $N$.

Poznamo še $\alpha$ konverzijo kjer v neki lambda abstrakciji preimenujemo vezane spremenljivke. Mora veljati da novo ime spremenljivke ni v $\text{FV}(M)$ v $\lambda x.M$.

$\lambda$ račun je **konfluenten** torej vrstni red korakov računanja ni pomemben dokler so dovoljeni.

Poznamo **neučakano** in **leno** računanje lambda računov.

* **Neučakana (eager evaluation):** v izrazu $e_1 \ e_2$ najprej do konca izračunamo $e_1$, da dobimo $\lambda x \ . \ e$, nato do konca izračunamo $e_2$, da dobimo $e_2'$ in šele nato vstavimo $e_2'$ v $e$.
* **Lena (lazy evaluation):** v izrazu $e_1 \ e_2$ najprej izračunamo $e_1$, da dobimo $\lambda x \ . \ e$, nato pa takoj vstavimo $e_2$ v $e$.


**Neučakano (argument izračunamo, preden ga vstavimo):**

$$
\begin{aligned}
&(\lambda x . (\lambda y . x) z) ((\lambda t . t) u) = \\
&(\lambda x . (\lambda y . x) z) u = \\
&(\lambda y . u) z = \\
&u
\end{aligned}
$$

**Leno (argument vstavimo takoj):**

$$
\begin{aligned}
&(\lambda x . (\lambda y . x) z) ((\lambda t . t) u) = \\
&(\lambda y . ((\lambda t . t) u)) z = \\
&(\lambda t . t) u = \\
&u
\end{aligned}
$$

**Računamo tudi znotraj $\lambda$-abstrakcij neučakano:**

$$
\begin{aligned}
&(\lambda x . (\lambda y . x) z) ((\lambda t . t) u) = \\
&(\lambda x . x) u = \\
&u
\end{aligned}
$$


Obstajajo izrazi, ki nimajo normalne oblike in jih ne moremo »izračunati do konca«. Primer je $(\lambda x . x x) (\lambda x . x x)$, ki ima natanko en možen računski korak, a ta pripelje spet do istega izraza:

$$
\begin{aligned}
&(\lambda x . x x) (\lambda x . x x) = \\
&(\lambda x . x x) (\lambda x . x x) = \\
&(\lambda x . x x) (\lambda x . x x) = \\
&\dots
\end{aligned}
$$

Definiramo lahko 

1. Identiteto
   $$\text{id} := \lambda x.x$$
2. Kompozicijo
   $$\text{compose} := \lambda f g \,x. f (gx)$$
3. Konstatne
   $$\lambda cx.c$$

Pogojni stavki in logične vrednosti

$$\text{TRUE : } \lambda xy.x$$
$$\text{FALSE : } \lambda xy.y$$

$$\text{IF : } \lambda bte.bte $$

*Vidimo lahko da true in false že implementirata odločevanje torej če preprosto vzamemo pri if true ali false in direktno vstavimo dobimo izbiranje "then" če je true in "else" če je false.*


```
if true a b =
(λ b t e . b t e) true a b =
(λ t e . true t e) a b =
(λ e . true a e) b =
true a b =
(λ x y . x) a b =
(λ y . a) b =
a
```

Da lahko delamo z $n$-tericami vpeljemo par ki ga lahko posplošimo na $n$ž-terico. Da vemo da je par ga predstavimo kot preslikavo.

Hočemo strukturo $\lambda p.pab$ za par $(a,b)$.

$$\text{PAIR} : \lambda xy. \lambda p.pxy$$
$$\text{PAIR a b}=(\lambda xy. \lambda p.pxy)ab = \lambda p.pab$$

Hočemo pridobiti prvi in drugi element. *$p$ nam lepo ponuja mesto kamor lahko vrinemo neko lambda funkcijo s katero lahko dobimo prvi ali drugi element. Torej bomo hoteli dati noter naš selector true in false.* To deluje po sintaksi $\text{FIRST PAIR } a \,b$

$$\text{FIRST} : \lambda z.z(xy.x)$$
$$\color{light} \lambda z.z(xy.x)(\lambda p.pab) = (\lambda p.pab)(xy.x) = (xy.x)ab = a $$

$$\text{SECOND : }\lambda z.z (xy.y)$$

Števila lahko predstavimo kot $n$-kratno gnezdo

$$
\begin{aligned}
0 &:= \lambda f x . x \\
1 &:= \lambda f x . f x \\
2 &:= \lambda f x . f (f x) \\
3 &:= \lambda f x . f (f (f x)) \\
4 &:= \lambda f x . f (f (f (f x))) \\
5 &:= \lambda f x . f (f (f (f (f x)))) \\
6 &:= \lambda f x . f (f (f (f (f (f x))))) \\
7 &:= \lambda f x . f (f (f (f (f (f (f x)))))) \\
8 &:= \lambda f x . f (f (f (f (f (f (f (f x))))))) \\
9 &:= \lambda f x . f (f (f (f (f (f (f (f (f x))))))))
\end{aligned}
$$

*s tem smo izrazilil $n$ -kratno aplikacijo funkcije $f$ nad nekim vhodom $x$. To predstavlja števila na način da lahko s tem definiramo naslednika kot operacijo oz. $f$ in ker imamo definirano $n$-kratno aplikacijo lahko našo opearcijo naslednika izvajamo $n$-krat oz. dobimo prištevanje števila $n$, če vzamemo še $n$-kratno aplikacijo ničesar dobimo seštevanje.*

$$\text{SUCC} : \lambda n f x.f (nfx)$$

*Successor je definiran kot pretvorba številke v surovo število aplikacij - ne le lambda abstrakcija $n$ števila aplikacij ampak člen ki izvaja $n$ aplikacij, nato pa pred njega postavimo še eno aplikacijo celoten člen pa je sedaj lambda abstrakcija večjega števila kar je po prejšnji definiciji število.*

**Seštevanje**

$$+ : \lambda nmfx.(nf)(mfx)$$

*Da pridemo do seštevanja moramo dobiti $n+m$-kratno aplikacijo - torej razmišljamo v smeri da surov člen m-kratne abstrakcije vstavimo namesto $x$ v $n$-kratni aplikaciji torej če imamo $\lambda fx.(...f(x)) = n$ hočemo naš $m$ vstaviti namesto $x$ ampak seveda mora biti naš $m$ v obliki surovega člena oz. brez lambde. Torej najprej predelamo člen $m$ tako da vstavimo noter $f$ in $x$ takoj, potem pa moramo v $n$ najprej vstaviti $f$ nato pa vstavimo še naš predelan $m$ celotno stvar zapakiramo v lambda abstrakcijo ki na koncu sprejme še $f$ in $x$.*

*Po korakih*

$$n =\lambda f x. f(f...(f{\color{orange}x'}))$$


Hočemo dobiti $n+m$ kratno aplikacijo $f$ nad $x$ torej v že obstoječo $n$ kratno aplikacijo hočemo vstaviti $m$ kratno plikacijo v $x$ ampak vidimo da če bi direktno vstavili $m$ v $x$ bi dobili $\lambda$ abstakcijo namesto funkcijskega izraza. Mi hočemo za ${\color{orange}x'}$ vstaviti $m$ ampak v svoji originalni obliki še ni v redu.
 
$${\color{orange}x' = f(...(fx))} \neq \lambda fx.f(...(fx)) =m$$

Torej hočemo $m$ iz lambda abstrakcije pretvoriti v funkcijski izraz torej samo uporabimo aplikacijo s $f$ in $x$

$${\color{blue}m} f x =  {\color{blue}(\lambda fx.f(...(fx)))} f x$$
$${\color{orange}m f x = f(...(fx)) = x'}$$

To lahko sedaj vstavimo v $n$ namesto $x'$ ampak struktura $n$ zahteva da naprej podamo $f$ preden lahko vstavljamo $x$ zato moramo pred aplikacijo $(mfx)$ še uporabiti $f$.


$$(nf)(mfx)$$

Da dobimo operacijo $n+m$ kratne aplikacije $f$ na $x$ pa samo še prevtorimo v $\lambda$ abstrakcijo

$$\color{green}+ : \lambda nmfx.(nf)(mfx)$$

**Množenje**

$$\lambda nmfx. m (nf)x$$

Ideja je da vsako instanco $f$ v $m$ nadomestimo z $n$. Seveda je pomembna podrobnost da ko vsatvljamo $n$ v $m$ moramo paziti na to da se ohranja dejstvo da uoprabljamo $f$ na $x$. To ni očitno ampak predpostavimo da vstavimo direktno $n$ v $m$ - vstavili smo $\lambda$ abstrakcijo ki sprejme $f$ in $x$ kot vhod kar ni zaželeno ker $f$-ja ne poterbujemo - zato preprosto naprej apliciramo $f$. Potem pa opzaimo da še vedno ostane lambda abstrakcija z $x$-om ampak to je v redu saj če pogledamo na najglobjo aplikacijo dobimo $n$ vidimo da imamo $(\lambda x.f(...(fx)))x = f(...(fx))$ ampak na naslednjem nivoju bi imeli $(\lambda x.f(...(fx)))(f(...(fx)))$  vidimo da moramo imeti $\lambda$ abstrakcijo da lahko vstavimo $f(...(fx))$ dejansko v aplikacijo. To potem reduciramo do konca. Torej bomo morali $n$ reducirati po $f$ a ne po $x$. Torej $m(nf)$ potem dodamo še $x$ na konec da sprostimo še $m$ ki ima v svoji lambda asbtrakciji še en $x$ torej $\lambda fx. (...)$ torej moramo prvi $x$ še odstraniti da dobimo surov člen ki ga zapakiramo z $\lambda nmfx.(...)$.

**Predhodnik** ima bolj izbirno implementacijo saj zahteva delanje s števili v paru.

Ideja temelji na funkciji $f(x,y) = (x+1,x)$ in njeni $n$-kratni aplikaciji da dobimo par $(n,n-1)$ iz česar vzamemo $n-1$.

Če konstruriramo po korakih - hočemo začeti s parom  $(0,0)$ nato pa hočemo uoprabiti funkcijo $f(x,y) = (x+1,x)$ n-krat. Torej

Naša funkcija se bo klicala $n$-krat torej rabimo da vrne to kar sprejme - to bo par. Vemo da bomo vračali nekaj s $p$-jem.

$$\lambda \_\_.p$$

Vemo da nam funkciji $\text{FIRST}$  in $\text{SECOND}$ data prvi in drugi element para. Torej hočemo tvoriti nov par kjer bo en element increment prvega člena drugi pa samo prvi člen nekega para ki ga predstavimo z $z$. *p služi kot potreben del za strukturo para - vemo da bomo rabili $p$ tudi pred piko in dobimo defincijo para (x+1,x), first nad $z$ deluje tako da vzame definicijo para in ga vstavi pred selector ki potem vrne prvi element. Successor deluje tako da v aplikacijo $f x$ vstavi še en $fx$. glej prejšnje izpeljave.*

$$\lambda \_p{.p}(\text{succ} \text{ first } z)(\text{first } z)$$

Očitno nam manjka v $\lambda$ še $z$ kot določena vezana spremenljivka

$$\lambda zp{.p}(\text{succ} \text{ first } z)(\text{first } z)$$

In to je naša funkcija $f$, če se spomnimo definicije $n$ vemo da je $n$ v resnici $n$-kratna aplikacija $f$-ja na $x$. Torej že imamo sistem da $n$-krat apliciramo na par $(0,0)$ Torej funkcij $n$ podamo arguemnta $f$ in $\text{pair} 0 0$ *vemo da je struktura $n := \lambda fx.f(...(fx))$ torej da sprejme $f$ in $x$.*

$$n \;f \text{ pair 0 0}$$
$$n \;{\color{orange}f} \,(\lambda p.p00)$$
$$n \;{\color{orange}(\lambda zp{.p}(\text{succ} \text{ first } z)(\text{first } z))} \,(\lambda p.p00)$$

Sedaj le še zapakiramo v lambda abstrakcijo oz. drugače rečeno hočemo sprejeti $n$ kot argument

$$\lambda n. n \;{\color{orange}(\lambda zp{.p}(\text{succ} \text{ first } z)(\text{first } z))} \,(\lambda p.p00)$$

Torej vzamemo par in funkcijo $x,y \mapsto x+1,x$ in jo apliciramo $n$-krat preko definicije števil.

Za konec lahko še polepšamo $f$ saj vemo da je $\lambda zp.p (...)(...) = \lambda z.\lambda p.p(...)(...)$ kar je $\lambda z. \text{pair}(...)(...)$ ampak laži pri konstrukciji razmišljati o tem.


Lambda rekurzija

Splošna rekurzija bo neka funkcija ki za izračun $f(n+1)$ vzame $n$ in $f(n)$ in iz teh dveh vrednosti dobi $f(n+1)$.

To bo oblike

$$f(n+1) := s\; n\; f(n)$$

kjer je $s$ dejansko logika funkcije - $s$ vzame argumenta $n$ in $f(n)$ in izračuna $f(n+1)$.

Mi vemo da je rekurzivna definicija plusa neka funkcija ki 

$$\text{sum} (n+1, k) := s\ n \;\text{sum}(n, k)$$

$$\Downarrow$$

$$s := \lambda x y . \operatorname{suc}(y)$$

Potem pa samo funkcijo $\text{sum}$ uporabimo $n$ krat na bazi $k$, kar nam omogča church scottovo število. Kjer apliciramo $\text{sum}$ in $k$ na $n$-ju.

$$\lambda n k . n\ \text{sum}\ k$$