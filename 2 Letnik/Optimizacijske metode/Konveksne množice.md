
**Dfn.:** Množica $A$ je **konveksna** če velja 

$$\forall x,y \in A, \forall \lambda \in [0,1] : (\lambda-1)x + \lambda y \in A$$

Torej je vsaka daljica s krajiščema iz $A$ spet v $A$.

Naj bodo $x_{1},...,x_{k} \in \mathbb{R}^{n}$, $\lambda_{1},...,\lambda_{k} \geq 0$ in $\lambda_{1}+...+\lambda_{k}=1$. Potem je

$$\lambda_{1}x_{1}+...+\lambda_{k}x_{k}$$

**konveksna kombinacija** vektorjev $x_{1},...,x_{k}$.

*Brez predpostavk temu rečemo lin. komb.*

Če velja samo $\lambda_{1}+...+\lambda_{k} = 1$ je to **afina kombinacija**.

Če je $k = 1$ je $1 \cdot x$ oz. vse možne konveksne komb. enega vektorja je vektor sam.

Če je $k=2$ je $(1-\lambda)x + \lambda y$, $\lambda \in  [0,1]$ je konveksna kombinacija. Če pustimo da je $\lambda \in \mathbb{R}$ je to afina kombinacija.

Torej je definicija konveksne mn. da je vsaka konveksna kombinacija vseh elementov v množici.

> **Trditev:** $A_{i}$ je konv. $\forall i \in I$ potem velja $\bigcap_{i} A_{i}$ je konveksna množica
> >[!|dokaz]+ Dokaz:
> >$x,y \in \bigcap A_{i}, \lambda \in [0,1]$
> >$\Rightarrow x,y \in A_{i} \,;\; \forall i \in I$
> >$A_{i}$ je konveksna $\Rightarrow$ $(1-\lambda)x + \lambda y \in A_{i} \,;\; \forall i \in I$
> >$\Rightarrow (1-\lambda)x + \lambda y \in \bigcap A_{i}$

**Trditev:** Množica je konveksna $\Leftrightarrow$ konveksna komb. poljubno mnogo vektorjev iz $A$ v $A$. *Ne le daljice.*
>[!|dokaz]+ Dokaz:
>$(\Leftarrow)$ je očitno
>$(\Rightarrow)$
> Dokažemo z indukcijo na $k$.
> $k=1$ je triv., $k = 2$ je po predpostavki.
> $k \geq 3$:
> $\lambda_{1}x_{1}+...+\lambda_{k}x_{k} =$
> BŠS predpostavimo da je $\lambda_{k} < 1$ to pomeni da druge lahko izrazimo kot
> $$= (1 - \lambda_k) \left( \frac{\lambda_1}{1 - \lambda_k} x_1 + \dots + \frac{\lambda_{k-1}}{1 - \lambda_k} x_{k-1} \right) + \lambda_k x_k$$
> Po induktivni predpostavki ki pravi da je konveksna komb. $k-1$ vektorjev v $A$, in po temu da je konv. komb. dveh vektorjev v $A$ v $A$ sledi da je pridobljen vektor v $A$.
> Preverimo še da je $\sum_{i}^{}\frac{\lambda_{i}}{1 - \lambda_{k}} = \frac{\sum_{}^{}\lambda_{i}}{1-\lambda_{k}} = 1$ *ker je $\sum_{}^{}\lambda_{i} = 1- \lambda_{k}$* in očitno je $\frac{\lambda_{i}}{1-\lambda_{k}} \geq 0$.


**Dfn.:** Konveksna ogrinjača množica $A$ je presek vseh konveksnih množic ki vsebujejo $A$.

$$A \subseteq \mathbb{R}^{n}$$
$$\text{Conv}(A) = \!\!\!\!\! \bigcap_{\substack{K \text{ je konv.}\\ A \subseteq K}}\!\!\!\!\! K$$

> Trditev:
> $A \subseteq  \text{Conv}(A)$
> *Dokaz: $A$ je podmnožica vsakega $K$-ja, $A$ je podmnožica preseka $K$-jev* 

> Trditev:
> $\text{Conv}(A) \text{ je konveksna}$
> *Dokaz: presek konveksnih množic je konveksen.*

> Trditev:
>$A^{\text{konv.}}\Rightarrow \text{Conv}(A)=A$
>*Dokaz: po prvi trditvi je $A \subseteq \text{Conv}(A)$, ampak ker je $A$ konveksna in velja $A^\text{konv.} \subseteq A$ mora biti presek vseh konv. mn., ki vsebujejo $A^\text{conv.}$, vsebovan v $A$. Torej je $A = \text{Conv}(A)$.*

> Trditev:
>$A \subseteq B, B^{\text{konv.}} \Rightarrow \text{Conv}(A) \subseteq B$
>*Dokaz: $B$ je konv. in vsebuje $A$, konv. ovojnica je presek vseh konv. mn. ki vsebujejo $A$. Torej je konv. ovojnica $A$ presek ki vsebuje $B$, torej mora biti ta presek podmnožica $B$. Torej velja da je $\text{Conv}(A) \subseteq B$.*

> Trditev:
>$\text{Conv}(A) = \{ \text{konveksna kombinacije vektorjev iz }A\}$
>>[!|dokaz]+ Dokaz:
>> $(\Rightarrow)$ oz. če je $x$ v preseku vseh konv. mn. ki vsebujejo $A$ potem je konv. komb. vektorjev $A$.
>> 
>> Imamo vektorje v $A$.
>> $x_{1},...,x_{k} \in A \subseteq  \text{Conv}(A)$
>> Ker pripadajo konveksni množici $\text{Conv}(A)$ pomeni da je vsaka njihova konv. kombinacija tudi v $\text{Conv}(A)$.
>> 
>> $(\Leftarrow)$ oz. če je $x$ konv. komb. vektorjev iz $A$ potem je v $\text{Conv}(A)$.
>>
>> Pomagamo si s 4. trditvijo. Dovolj je da pokažemo $A \subseteq \{ \text{konveksna kombinacije vektorjev iz }A\}$ in da je $\{ \text{konveksna kombinacije vektorjev iz }A\}$ konveksna.
>>
>>Vsak $x \in A$ je konv. komb. vek. iz $A$ saj velja $x \cdot 1 = x$.
>>
>>Naj bosta $x_{1}\lambda_{1}+...+x_{k}\lambda_{k},\,y_{1}\mu_{1}+...+y_{l}\mu_{l} \in A$ polj. konv. komb. v $A$, njuna konv. komb. mora biti v $A$.
>>$$(\lambda-1)(x_{1}\lambda_{1}+...+x_{k}\lambda_{k})+ \lambda(y_{1}\mu_{1}+...+y_{l}\mu_{l}) =$$
>>$$x_{1}\lambda_{1}(\lambda-1)+...+x_{k}\lambda_{k}(\lambda-1)+ y_{1}\mu_{1}\lambda +...+y_{l}\mu_{l}\lambda$$
>>
>>$$(1-\lambda)\lambda_{i} \geq 0$$
>>$$\lambda \mu_{j}\geq 0$$
>>$$(1-\lambda)\lambda_{1}+...+(1-\lambda)\lambda_{k} + \lambda \mu_{1}+... + \lambda \mu_{l} = $$
>>$$(1-\lambda) \cdot 1 + \lambda + 1 = 1$$


**Dfn.:** Naj bo $A$ konv. mn. Velja da je $a \in A$ ekstremna točka, če ni konveksna komb. dveh točk $x,y \in A$, kjer $x,y \neq a$.

Alternativno

$$\nexists \lambda \in (0,1) \,,\, x,y \in A , x,y \neq a : a = (1-\lambda)x + \lambda y$$


**Opomba:** Ekstremne točke so vedno robne, robne točke niso vedno ekstremne.

***

*Ariana je končala pri ekstremnih točkah, to je od kovalinke*

**Dfn.:** $A \neq \emptyset$ je afina če za $\forall x,y \in A, \forall \lambda \in \mathbb{R}$ velja $(1-\lambda)x+\lambda y \in A$.

*Če je $x,y \in A$ potem je cela premica ki jo določujeta $x,y$ v $A$.*

> **Trditev:**
> 
> Naj bo $A \subseteq \mathbb{R}^n, A \neq \emptyset$
> 
> Naslednje trditve so ekvivalentne:
> (1) $A$ je afin
> (2) vsaka afina kombinacija vektorjev iz $A$ je v $A$
> (3) $\exists \text{podprostor }V \subseteq \mathbb{R}^{n}, \exists a \in A : A = V + a = \{v + a : v \in V\}$
> >[!|dokaz]+ Dokaz:
> >
> > $(1)\Rightarrow (2)$
> > 
> > Indukcija na $k$, $k =2$ že drži ker imamo afin prostor,
> > $k \geq 3$ 
> > Naj bo polj. afina komb. $k$ vektorjev $\lambda_1 x_1 + \dots + \lambda_k x_k$ in naj bo BŠS $\lambda_k \neq 1$
> > 
> > $$= (1 - \lambda_k) \underbrace{\left( \frac{\lambda_1}{1 - \lambda_k} x_1 + \dots + \frac{\lambda_{k-1}}{1 - \lambda_k} x_{k-1} \right)}_{\text{po $\,$i.p. } \in A} + \lambda_k x_k \in A$$
> > 
> > $(2) \Rightarrow (3)$
> > Naj bo $a \in A$ polj. vektor iz $A$. Naj bo $V = A -a$. Pokazati hočemo da je $V$ podprostor. *Očitno je da je $V+a = A$.*
> > Veljati mora $\alpha v_{1}+ \beta v_{2} \in V = A-a$.
> > $v_{1} = x_{1}-a, v_{2} = x_{2}-a$, kjer sta $x_{1}, x_{2} \in A$.
> > Ker je $A$ afin prostor velja $\lambda x_{1} + \mu x_{2} \in A$, kjer sta $\lambda, \mu \in \mathbb{R}$.
> > Poglejmo kaj velja za polj. $\lambda, \mu \in \mathbb{R}$ za 
> > $$\lambda v_{1} + \mu v_{2} =$$
> > $$\lambda(x_{1}-a) + \mu(x_{2}-a) =$$
> > $$\lambda x_{1} - \lambda a + \mu x_{2} - \mu a =$$
> > $$\lambda x_{1} + \mu x_{2} - (\lambda + \mu)a = $$
> > $$\lambda x_{1} + \mu x_{2} - a $$
> > 
> > in ker je $\lambda x_{1} + \mu x_{2} \in A$ veljada je $\lambda x_{1} + \mu x_{2} - a \in V$.
> > 
> > $(3) \Rightarrow (1)$
> > 
> > Naj bo $A = V + a$, naj bosta $x+a$ in $y+a$, kjer $x,y \in V$
> > $$(1-\lambda)(x+a) + \lambda(y+a)=(1-\lambda)x + \lambda y + a$$
> > Vemo da je polj. lin. komb. v $V$ torej je $(1-\lambda)x + \lambda y \in V$, torej je polj. afina komb. spet v  $A$.



**Opomba:** Afine množice v $\mathbb{R}^{3}$ so premice, ravnine, singelton, $\mathbb{R}^{3}$.
Afinim množicam rečemo tudi afini podprostori.

**Konveksni stožci in Farkaseva lema**

**Dfn.:** $A \subseteq \mathbb{R}^{n}$. $A$ je konveksni stožec, če za $\forall x,y \in A$, $\forall \lambda,\mu \geq 0$ velja $\lambda x + \mu y \in A$.

**Opomba:**
Konveksni stožec je konveksna množica, obratno ne velja nujno.
Vsak lin. podprostor je konv. stožec.

**Dfn.:** Naj bodo $a_{1,...,k} \in \mathbb{R}^{n}$ in naj bodo $S(a_{1},...,a_{k}) = \{ \lambda_{1}a_{1}+...+\lambda_{k}a_{k} \,;\; \lambda_{1},...,\lambda_{k} \geq 0\}.$
Temu rečemo konveksni stožec **napet** na $a_{1},...,a_{k}$

> **Trditev:** $S(a_{1},...,a_{k})$ je konv. stožec.
> >[!|dokaz]+ Dokaz:
> >$\lambda_{1}a_{1}+...+\lambda_{k}a_{k}$, $\mu_{1}a_{1}+...+\mu_{k}a_{k}$ naj bosta iz $S(a_{1},...,a_{k})$.
> >
> >Naj bo konv. komb teh elementov 
> >
> >$$\lambda(\lambda_{1}a_{1}+...+\lambda_{k}a_{k}) + \mu(\mu_{1}a_{1}+...+\mu_{k}a_{k}) =$$
> >$$\lambda\lambda_{1}a_{1}+...+\lambda\lambda_{k}a_{k} + \mu\mu_{1}a_{1}+...+\mu\mu_{k}a_{k} =$$
> >$$a_{1}(\lambda\lambda_{1} + \mu\mu_{1})+...+a_{k}(\lambda\lambda_{k} + \mu\mu_{k})$$
> >$$\lambda \lambda_{i} + \mu \mu_{i} \geq 0$$
> >
> >Torej je $S(a_{1},...,a_{k})$ konv. stožec.

**Dfn.:** Naj bo $A \subseteq \mathbb{R}$ potem je $A^{*} = \{ x \in \mathbb{R}^{n}: x^{T}a \geq 0 \text{ za } \forall a \in A\}$ **dualni stožec**.

V $A^{*}$ so vektorji, ki z vsemi vektorji iz $A$ tvorijo ostri kot.

> **Trditev:** $A^{*}$ je konveksni stožec
> >[!|dokaz]+ Dokaz:
> > Naj bosta $x, y \in A^*, \lambda, \mu \geq 0, a \in A$,
> > Pogledamo če velja pogoj
> > $$(\lambda x + \mu y)^T a = \lambda \underbrace{x^T a}_{\geq 0} + \mu \underbrace{y^T a}_{\geq 0} \geq 0$$
> > $\implies \lambda x + \mu y \in A^*$

> **Trditev:**
> $A \subseteq A^{**}$
> >[!|dokaz]+ Dokaz:
> > Naj bo $a \in A, b \in A^* \implies a^T b \geq 0$
> > V splošnem: $A \neq A^{**}$ (npr. $A$ ni konveksen stožec)
> > 


> **Farkaseva lema**
> 
> $$S^{**}(a_{1},...,a_{k}) = S(a_{1},...,a_{k})$$
> 
>> [!|dokaz]+ Dokaz:
>> 
>> $(\supseteq)$ Ta smer velja za poljubno množico $A$ iz prejšnjega izreka.
>> $(\subseteq)$ Naj bo vektor $b \in S^{**}$, radi bi dokazali da je tudi v $S$.
>> 
>> $$b \in S(a_{1},...,a_{k}) \Leftrightarrow $$
>>$$\exists  \lambda_{1},...,\lambda_{k} \geq 0 : \lambda_{1}a_{1}+...+\lambda_{k}+a_{k} = b$$
>>$$ A = [a_{1}...a_{k}] \in  \mathbb{R}^{n \times k}$$
>>
>>*Naj bodo $x := \lambda$*
>>
>>Torej je $b \in S(a_{1},...,a_{k}) \Leftrightarrow \exists  x \geq 0:$
>>$$A x = b$$
>>
>>Vemo da je $b^{T}y \geq 0$ za vsak $y \in S^{*}(a_{1},...,a_{k})$
>>Trdimo da to da je $y \in S^{*}(a_{1},...,a_{k}) \Leftrightarrow A^{T}y \geq 0$ *torej da $y$ tvorijo ster kot z vsemi $a_{i}$.*
>>Torej če je $A^{T}y \geq 0$ potem je $b^{T}y \geq 0$. Radi pa bi ugotovili če obstaja $x \geq 0$ da velja $Ax = b$.
>>
>>$$Ax = b$$
>>$$x \geq 0$$
>>
>>Radi bi dokazali da je ta LP dopusten. Če je dopusten je LP optimalen, če je LP optimalen je dual optimalen, dual pa je
>>
>>$$\min b^{T}y$$
>>$$\text{p.p. } A^{T}y \geq 0$$
>>
>>Dual je dopusten ker je $y=0$ dopustna rešitev, ta je lahko neomejen ali optimalen, a ta ne more biti neomejen, ker je $b^{T}y \geq 0$ torej je omejen od spodaj, torej je optimalen, torej je LP optimalen, torej je dopusten in je ker obstaja tak $x$ da je $Ax = b$ je $b \in S^{**}$.

---

### Zakaj je to pomembno?
Ta oblika Farkaseve leme (tudi imenovana **izrek o bikonusu**) je ključna v optimizaciji. Pove nam, da če želimo preveriti, ali je nek vektor $b$ konveksna kombinacija smeri $a_i$ z nenegativnimi koeficienti ($\lambda_i \geq 0$), je to ekvivalentno preverjanju, ali $b$ tvori ostri kot z vsemi vektorji, ki tvorijo ostri kot z vsemi $a_i$.

V praksi se to pogosto zapiše kot:
Sistem $A\lambda = b, \lambda \geq 0$ ima rešitev natanko tedaj, ko velja:
$$y^T A \geq 0 \implies y^T b \geq 0$$