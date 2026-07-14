## Izhodišče in definicija omrežja
Problem maksimalnega pretoka je problem v teoriji grafov in optimizaciji. Modeliramo ga s pomočjo usmerjenega grafa, ki predstavlja določeno **omrežje**.

Definiran je kot

$$G = (V,E)$$
$$s,t \in V$$
$$\forall ij  : s \neq j, t \neq i$$
$$c_{e} \geq 0, c_{e} \in \mathbb{Z} \,\text{ so cene povezav na $e$}$$
$$f(e) = e \rightarrow \mathbb{R} \,\text{ je pretok po $e$}$$

$$\text{In}(v) \text{ je množica vseh vstopnih povezav $v$}$$
$$\text{Out}(v) \text{ je množica vseh izstopnih povezav $v$}$$

$$S = (A,B)$$ $$A \cup B = G$$ $$A,B\neq \emptyset$$ $$s \in  A, t \in B$$
$$c(A,B) = \sum_{e \in \text{Out}(A)}^{}c_{e}$$

$$\text{In}(S) \text{ je množica vseh vstopnih povezav $S$}$$
$$\text{Out}(S) \text{ je množica vseh izstopnih povezav $S$}$$



Velja


$$0 \le f(e) \le c_e \quad \text{za vsak } e \in E$$

Veljajo Kirchhoffovi zakoni


$$\sum_{e \in \text{In}(v)} f(e) = \sum_{e \in \text{Out}(v)} f(e)$$

Vpeljemo oznaki za celotni vstopni in izstopni tok vozlišča

$$f^{\text{in}}(v) = \sum_{e \in \text{In}(v)} f(e)$$
$$f^{\text{out}}(v) = \sum_{e \in \text{Out}(v)} f(e)$$

Pogoj ohranitvi pretoka torej zapišemo kot: $f^{\text{in}}(v) = f^{\text{out}}(v)$.


Pretok omrežja je definiran kot

$$|f| = f^{\text{out}}(s) = f^{\text{in}}(t)$$

Hočemo **maksimizirazi $|f|$** ob podanih omejitvah.

**Graf rezerv**

**Graf rezerv** $G_f = (V, E_f)$ je pomožni graf, ki nam pove, za koliko in v katero smer še lahko spremenimo pretok.

**Preme povezave**

Tvorimo ga tako da če za $e = (u, v)$ velja, da je pretok manjši od kapacitete $f(e) < c_e$, potem v grafu rezerv $G_f$ obstaja usmerjena povezava $e_f = (u, v)$ z **rezervo**
$$r = c_e - f(e)$$
Pove nam da lahko pretok na $uv$ povečamo za $r$.

**Povratne povezave**
Če za $e = uv$ velja, da je na njej pretok $f(e) > 0$, potem v grafu rezerv $G_f$ obstaja  $e_f = vu$, z **rezervo**

$$r = f(vu)$$

**Povečujoče poti oz. nezasičene poti**

Vsaka pot od izvora $s$ do ponora $t$ v grafu rezerv $G_f$ se imenuje **nezasičena pot**.

Naj bo $P$ neka izbrana pot od $s$ do $t$ v grafu rezerv. Na tej poti imamo zaporedje povezav z rezervami $r_1, r_2, \dots, r_k$. Najmanjša izmed teh rezerv predstavlja omejitev celotne poti, kar imenujemo **ozko grlo** 

$$B(P, f) = \min\{r_1, r_2, \dots, r_k\}$$

kjer je $r_i$ enak

$$r_{i} = \begin{cases}
c_{i} - f(e_{i}) &&\!\!\!\!\!\!\!\!\!\!\!\! \,;\; e_{i} \text{ je prema} \\
f(e_{i}) && \!\!\!\!\!\!\!\!\!\!\!\! \,;\; e_{i} \text{ je obratna}
\end{cases}$$

Na tej poti lahko pretok povečamo za največ $B(P,f)$.




Ko v grafu rezerv najdemo pot $P^f = \langle e_1^f, e_2^f, \dots, e_k^f \rangle$ njeno ozko grlo $B(P, f)$, moramo na prvotno premih povezavah povečamo pretok za $B$ na prvotno obratnih pa zmanjšamo pretok za $B$. V grafu rezerv to pomeni da na prvotno premih povezavah zmanjšamo vrednost za $B$, na prvotno obratnih pa povečamo za $B$.



> **Veljavnost novega pretoka**
> Če je $f$ veljaven pretok, potem je tudi $f'$, ki ga dobimo s tem postopkom, veljaven pretok.
> *   **Nenegativnost:** Pretok se zmanjša le na povratnih povezavah. Ker je rezerva na povratni povezavi enaka $f(e)$ in ker je $B(P, f) \le f(e) \Rightarrow f(e) -B(P,f) \ge 0$, torej pretok nikoli ne pade pod 0.
> *   **Omejitev s kapaciteto:** Pretok se poveča le na premih povezavah. Ker je rezerva preme povezave $c_e - f(e)$ in ker je $B(P, f) \le c_e - f(e)$ bo $B(P, f) + f(e) \le c_e$, novi pretok nikoli ne preseže $c_e$.
> *   **Ohranitev pretoka:** Če se spremeni  vhodna povezava poveča za $B$ se bo izhodna povečala za $B$ in se pretok ohrani. 
> 

**Ford-Fulkersonova metoda** je postopek kjer vsaki povezavi določimo pretok $0$, potem konstruiramo rezidualni graf. Z DFS poiščemo povečujoče poti - torej če je vrednost na povezavi večja od $0$ jo dodamo v pot, drugače jo ignoriramo, ko dosežemo $t$, poiščemo $B$,  za vsako povezavo povečamo pretok za $B$ če je prema in zmanjšamo za $B$ če ni in ponavaljamo postopek dokler obstaja povečujoča pot.


**Psevdokoda Ford-Fulkersonove metode**

```text
function MAKSIMALNI-PRETOK(G)
    for all e ∈ E do
        f(e) ← 0        

    while obstaja pot P od s do t v rezidualnem grafu do

        <e1_f, ..., ek_f> ← povečujoča pot
        
        <r1, ..., rk> ← reziduali G
        
        B ← min{r1, ..., rk}
        
        <e1, ..., ek> ← pripadajoče povezave v G
        
        for i ← 1 to k do
            if (ei usmerjena enako kot ei_f) then
                f(ei) ← f(ei) + B
                posodobi rezidualni graf
            else
                f(ei) ← f(ei) - B
                posodobi rezidualni graf
    
    return f  
```

Pravimo ji metoda ker iskanje poti ni točno določeno.

Če iščemo poti poljubno je meja izvajanaj $O(CE)$, kjer je $C = \sum_{}^{}c_{e}$, saj lahko najdemo vse kupaj največ $C$ povečujočih poti, za iskanje poti pa porabimo $O(E)$ časa.

$O(E)$ časa porabimo za iskanje saj smo v povezanem grafu kjer velja $E \geq V-1$, torej bo $E \sim V$ torej bo $O(V + E) = O(2E) = O(E)$.

Ker so kapacitete celoštevilske se v vsaki iteraciji pretok poveča za najmanj ena, ker tako vedno lahko dosežemo $C$ smo omejeni navzgor torej imamo končno število korakov. Če bi bile kapacitete realne potem bi  lahko večali pretok za $\frac{1}{n}$ kar bi lahko ponavljali v neskončnost.




To zahtevnost imenujemo **psevdopolinomska**, ker je linearno odvisna od vrednosti kapacitet $C$. Če so kapacitete zelo velike (npr. zapisane z $b$ biti), je $C = 2^b$, kar pomeni, da je zahtevnost eksponentna glede na dolžino vhoda $O(2^{b(C)}E)$.



**Izreki za dokaz pravilnosti metode**

Koncept ki predstavlja "ozko grlo" celotnega omrežja je prerez grafa, ki smo ga že definirali.

Kapaciteta prereza, vsota kapacitet povezav, ki potekajo **iz množice $A$ v množico $B$**. 

Pri izračunu kapacitete prereza upoštevamo le povezave, ki kažejo "naprej" (iz $A$ v $B$). Povezav, ki kažejo "nazaj" (iz $B$ v $A$), v vsoto kapacitet **ne vključimo**.



**Razmerje med pretokom in prerezom**

Povezava med poljubnim pretokom in poljubnim prerezom je osnova za dokazovanje optimalnosti.

### Neto pretok skozi prerez
Za poljuben pretok  in prerez velja
$$|f| = f^{\text{out}}(A) - f^{\text{in}}(A)$$

**Dokaz:**
1.  Po definiciji vemo, da je $|f| = f^{\text{out}}(s)$.
2.  Ker je $f^{\text{in}}(s) = 0$, lahko zapišemo $|f| = f^{\text{out}}(s) - f^{\text{in}}(s)$.
3.  Za vsa ostala vozlišča $v \in A \setminus \{s\}$ velja zakon o ohranitvi pretoka: $f^{\text{out}}(v) - f^{\text{in}}(v) = 0$.
4.  Če seštejemo te razlike za vsa vozlišča v množici $A$, dobimo:
    $$|f| = \sum_{v \in A} (f^{\text{out}}(v) - f^{\text{in}}(v))$$
5.  V tej vsoti se povezave, ki imajo obe krajišči znotraj množice $A$, med seboj izničijo (nastopajo enkrat s pozitivnim in enkrat z negativnim predznakom).
6.  Ostanejo le povezave, ki prečkajo mejo prereza: tiste, ki gredo iz $A$ v $B$ (ostanejo z znakom $+$), in tiste, ki gredo iz $B$ v $A$ (ostanejo z znakom $-$).
7.  Torej: $|f| = \sum_{e \in \text{Out}(A)} f(e) - \sum_{e \in \text{In}(A)} f(e) = f^{\text{out}}(A) - f^{\text{in}}(A)$.

---

### Šibka dualnost
Za polj. pretok in prerez velja

$$|f| \le c(A, B)$$

**Dokaz:**
Iz prejšnje trditve vemo 

$$|f| = f^{\text{out}}(A) - f^{\text{in}}(A)$$

$$|f| = f^{\text{out}}(A) - f^{\text{in}}(A) \leq f^\text{out}(A)$$
$$|f| \le f^{\text{out}}(A)$$

Vemo tudi, da je pretok po vsaki povezavi omejen s kapaciteto ($f(e) \le c_e$), zato velja:

$$f^{\text{out}}(A) = \sum_{e \in \text{Out}(A)} f(e) \le \sum_{e \in \text{Out}(A)} c_e = c(A, B)$$
S tem je dokazano, da $|f| \le c(A, B)$.



> **Vrednost maksimalnega pretoka v omrežju je natanko enaka kapaciteti minimalnega prereza v tem omrežju.**



### Dokaz pravilnosti
Če je $f$ tak pretok, da v grafu rezerv $G_f$ **ne obstaja več poti** od izvora $s$ do ponora $t$, potem je vrednost $|f|$ maksimalna.

**Dokaz s konstrukcijo optimalnega prereza:**
Predpostavimo, da se je metoda ustavila, ker v $G_f$ ni več poti od $s$ do $t$. Konstruirajmo prerez $(A^*, B^*)$ na naslednji način:
*   Množica **$A^*$**: Naj bodo to vsa vozlišča $v \in V$, do katerih v končnem grafu rezerv $G_f$ **še obstaja** pot iz izvora $s$. (Opomba: $s$ je vedno v $A^*$).
*   Množica **$B^*$**: To so vsa ostala vozlišča ($V \setminus A^*$). Ker smo predpostavili, da poti do $t$ v $G_f$ ni, je vozlišče $t$ nujno v množici $B^*$.

Tako smo dobili veljaven prerez $(A^*, B^*)$. Poglejmo povezave, ki prečkajo mejo tega prereza v originalnem grafu $G$:

1.  **Povezave $e = (u, v)$ iz $A^*$ v $B^*$:**
    Za te povezave mora veljati $f(e) = c_e$ (**zasičene povezave**).
    *Zakaj?* Če bi bilo $f(e) < c_e$, bi v grafu rezerv $G_f$ obstajala napredna povezava od $u$ do $v$. Ker je $u$ dosegljiv iz $s$, bi bil potem tudi $v$ dosegljiv iz $s$, kar bi pomenilo, da bi moral biti $v \in A^*$, kar pa je v nasprotju z našo definicijo $B^*$.

2.  **Povezave $e' = (u', v')$ iz $B^*$ v $A^*$:**
    Za te povezave mora veljati $f(e') = 0$ (**popolnoma neizkoriščene povezave**).
    *Zakaj?* Če bi bilo $f(e') > 0$, bi v grafu rezerv $G_f$ obstajala povratna povezava od $v'$ do $u'$. Ker je $v'$ dosegljiv iz $s$, bi bila dosegljiva tudi $u'$, kar bi pomenilo $u' \in A^*$, kar je spet v nasprotju z definicijo $B^*$.

**Sklepni izračun:**
Uporabimo formulo iz Trditve 2 za naš specifični prerez $(A^*, B^*)$:
$$|f| = f^{\text{out}}(A^*) - f^{\text{in}}(A^*)$$
$$|f| = \left( \sum_{e \in \text{Out}(A^*)} f(e) \right) - \left( \sum_{e' \in \text{In}(A^*)} f(e') \right)$$
Upoštevamo ugotovitve o zasičenosti:
$$|f| = \left( \sum_{e \in \text{Out}(A^*)} c_e \right) - (0)$$
$$|f| = c(A^*, B^*)$$

Ugotovili smo, da je vrednost našega pretoka $|f|$ enaka kapaciteti prereza $(A^*, B^*)$. Ker vemo, da nobena vrednost pretoka ne more biti večja od kapacitete prereza (Trditev 3), smo s tem dokazali, da je naš pretok $f$ **maksimalen**, prerez $(A^*, B^*)$ pa **minimalen**.


**Izrek o celoštevilskosti**

Če začnemo pretok z $0$ in ga na vsakem koraku povečamo za celo število, dobimo nov celoštevilski pretok, ker so rezerve tudi celoštevilske bo vedno mogoče povečati za neko celoštevilsko vrednost.


**Edmonds Karpov algoritem**

Poti iščemo tako da najprej nasičimo najmanjše.

Edmonds Karpov teče v polinomskem času.

Naj bo

$$\delta_{f}(s,v)$$

najkrajša pot od izvora do vozlišča $v$ v $G^{f}$.

> Če imamo pretok $f$ in pretok $f'$ v naslednjem koraku je  $\delta_{f'}(s,v) \geq \delta_{f}(s,v)$
> 
> >[!|dokaz]+ Dokaz:
> >
> >Dokažemo s protislovjem.
> >
> > Predpostavimo
> > - $1]\quad\delta_{f}(s,j) > \delta_{f'}(s,j)$
> > - $2]\quad\delta_{f'}(s,j)$ je najmanjša izmed manjšajočih poti v $G^{f'}$
> >   
> >  Naj bo $i$ predhodnik $j$ v $G^{f'}$. Velja
>  > - $3]\quad\delta_{f'}(s,i)+1 = \delta_{f'}(s,j)$
>  > - $4]\quad\delta_{f}(s,i) \leq \delta_{f'}(s,i)$, *ker je $\delta_{f'}(s,j)$ najmanjša manjšajoča pot, torej mora nova pot do $i$ biti daljša*
>  > 
>  > $$(s \rightarrow... \rightarrow i \rightarrow j) \in G^{f'}$$
>  > 
>  > V $G^{f}$ se lahko zgodi da je $f(ji) = c_{ij}$ posledično povezava $ij$ v $G^{f}$ ne obstaja, res povezava $ij$ lahko obstaja le če $f(ji) \neq c_{ij}$ ni nasičena. Če povezava obstaja v $G^{f'}$ pomeni da smo po $ji$ poslali pretok s čimer velja $f(ji) \le c_{ij}$ in $f(ij) = c_{ij} - f(ji)$.
>  > 
>  > 1\. Če je povezava $ij$ že obstajala velja
>  > - $\delta_{f}(s,j) \leq \delta_{f}(s,i)+1$
>  > 
>  > Sedaj vidimo da velja
>  > $$\delta_{f}(s,j) \leq \delta_{f}(s,i)+1\leq \delta_{f'}(s,i)+1=\delta_{f'}(s,j)$$
>  > kjer uporabimo začetno dejstvo, potem $4]$ potem pa še $3]$.
>  > 
>  > 2\. Če povezava $ij$ še ni obstajala v $G^{f}$ a se je pojavila v $G^{f'}$ se je moral tok poslati po $ji$, torej je $ji$ del najkrajše poti, torej velja
>  > 
>  > - $\delta_{f}(s,i) = \delta_{f}(s,j) + 1$
>  >   
>  > Torej velja
>  > 
>  > $$\delta_{f}(s,j) = \delta_{f}(s,i) -1 \leq \delta_{f'}(s,i)-1 = \delta_{f'}(s,j)-2$$
>  > 
>  > Torej bo 
>  > 
>  > $$\delta_{f}(s,j) \leq \delta_{f'}(s,j)-2\leq \delta_{f'}(s,j)$$
>  > $$\delta_{f}(s,j)\leq \delta_{f'}(s,j)$$
>  > 


> Vsaka povezava postane kritična največ $\frac{|V|}{2}$ krat.

Če imamo $E$ povezav kjer vsaka lahko postane kritična $\frac{V}{2}$-krat imamo $O(VE)$ kritičnih poti.

Za vsako od teh $O(VE)$ poti rabimo $O(E)$ da jih najdemo, *dejansko $O(V+E)$ ampak je $V-1 \leq E$ v povezanih grafih torej lahko s tem ocenimo $O(E)$*, da posodobimo graf pa potrebujemo $O(V)$ časa kar bo spet $O(E)$ v povezanem grafu torej bo vse skupaj $O(E)$ za vsako od $O(VE)$ poti.

Imeli bomo $O(VE^{2})$ časovno kompleknost.

**Problem maksimalenga prirejanja**

Ta problem lahko preprosto prevedemo na problem maks. pretoka tako da povežemo $s$ z vsemi vozlišči leve množice, potem povežemo vse originalne povezave, potem pa vsa desna vozlišča s $t$, vsem povezam določimo ceno $1$, s tem dobimo maksimalno prirejanje, če je maksimalno prirejanje enako $\sum_{}^{}c_{sj}$ potem je to tudi popolno prirejanje.