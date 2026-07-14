Trenutno je namenjeno za obravnavo kolobarjev

Manjkajo
- Perumtacijske grupe
- Diedrske grupe
- Koseti oz. edinke
- Lagarngevi, Fermatovi, Eulerjevi izreki in to
***


**Grupa** je monoid, kjer ima vsak element inverz.

Za Caylejevo tabelo velja da je vsaka vrstica permutacija originalne.

> Enota je enolična.
> >[!|dokaz]+ Dokaz:
> >Recimo da imamo $e'$ in $e$
> > $$e'=ee'=e$$

>Inverz je enoličen
> >[!|dokaz]+ Dokaz:
> >Imamo $a$ in $a'$ in $a''$.
> >$$g'=g'e=g'gg''=eg''=g''$$

> Velja $(ab)^{-1}=b^{-1}a^{-1}$
> >[!|dokaz]+ Dokaz:
> > Velja $abb^-1a^{-1}= e$, ker so inverzi enolični je $(ab)^{-1}$ lahko le $b^{-1}a^{-1}$. *Brez enoličnosti bi pokazali da je to le eden izmed inverzov na pa nujno edini.*

>Velja $(a^{-1})^{-1} = a$
>>[!|dokaz]+ Dokaz:
>>$(a^{-1})^{-1} = e(a^{-1})^{-1} =aa^{-1}(a^{-1})^{-1} =ae= a$


> Naj bo $G$ grupa ter $a$ in $b$ poljubna elementa v $G$. Tedaj imata enačbi $ax = b$ in $xa = b$ enolični rešitvi v $G$.
> 
> >[!|dokaz]+ Dokaz:
> >Predpostavimo $ax = b$. 
> >Če obe strani enačbe $ax = b$ pomnožimo z $a^{-1}$, dobimo $x = ex = a^{-1}ax = a^{-1}b$. *Torej tak $x$ obstaja.*
> > Da bi pokazali enoličnost, predpostavimo, da sta $x_1$ in $x_2$ obe rešitvi enačbe $ax = b$; potem velja $ax_1 = b = ax_2$. Torej je $x_1 = a^{-1}ax_1 = a^{-1}ax_2 = x_2$.

> Naj so $a,b,c \in G$, velja $ba = ca \Rightarrow b = c$
> >[!|dokaz]+ Dokaz:
> >$$b = baa^{-1}=caa^{-1}= c$$

<br>

Velja



$$g^n = \underbrace{g \cdot g \,\cdot \,\, ... \,\cdot\, g}_{n\text{-krat}}$$

$$g^{-n} = \underbrace{g^{-1} \cdot g^{-1}  \,\cdot \,\, ... \,\cdot\,  g^{-1}}_{n\text{-krat}}$$

<br>

Za vse $g, h \in G$ velja:

1. $g^m g^n = g^{m+n}$ za vse $m, n \in \mathbb{Z}$;
2. $(g^m)^n = g^{mn}$ za vse $m, n \in \mathbb{Z}$;
3. $(gh)^n = (h^{-1}g^{-1})^{-n}$ za vse $n \in \mathbb{Z}$.
   
Poleg tega, če je $G$ Abelova grupa, potem velja $(gh)^n = g^n h^n$. *V splošnem ne ker je $(gh)^{n} = (gh)(gh)...(gh)$*
***
**Podgrupe**

Podgrupe so podmnožice grupe, ki so grupe za isto operacijo.

Vsaka grupa ima vsaj dve podgrupi in sicer množico samo in **trivialno podgrupo**.

**Trivialna podgrupa** je $\{ e\}$.

Če podgrupa ni ena od teh ji pravimo **prava podgrupa**.

> Struktura $H$ je podgrupa $G$ natanko tedaj ko velja
> 
> - $e \in H$
> - $h_{1},h_{2} \in H \Rightarrow h_{1}h_{2} \in H$
> - $h \in H \Rightarrow h^{-1} \in H$
> 
> >[!|dokaz]+ Dokaz:
> > Predpostavimo da je $H$ podgrupa grupe $G$. Pokazati moramo, da veljajo trije pogoji. Ker je $H$ grupa, mora imeti identiteto $e_H$. Pokazati moramo, da je $e_H = e$, kjer je $e$ identiteta grupe $G$. Vemo, da velja $e_H e_H = e_H$ in da je $e e_H = e_H e = e_H$; zato velja $e e_H = e_H e_H$. S pravilom desnega krajšanja dobimo $e = e_H$. Drugi pogoj velja, saj je podgrupa $H$ grupa. Za dokaz tretjega pogoja naj bo $h \in H$. Ker je $H$ grupa, obstaja element $h' \in H$, tako da je $h h' = h' h = e$. Zaradi enoličnosti inverza v $G$ velja $h' = h^{-1}$.
> > 
> > Obratno, če veljajo trije pogoji, moramo pokazati, da je $H$ grupa za isto operacijo kot $G$; vendar so ti pogoji skupaj z asociativnostjo binarne operacije natanko aksiomi, navedeni v definiciji grupe.




> **Naj bo $H$ podmnožica grupe $G$. Tedaj je $H$ podgrupa grupe $G$ natanko tedaj, ko je $H \neq \emptyset$ in za poljubna $g, h \in H$ velja, da je $gh^{-1} \in H$.**
> 
> >[!|dokaz]+ Dokaz:
> >
> > Najprej predpostavimo, da je $H$ podgrupa grupe $G$. Želimo pokazati, da velja $gh^{-1} \in H$ za vsaka $g, h \in H$. Ker je $h \in H$, mora biti tudi njegov inverz $h^{-1} \in H$. Zaradi zaprtosti grupne operacije je tedaj $gh^{-1} \in H$.
> > 
> > Obratno, predpostavimo, da je $H \subset G$ takšna, da $H \neq \emptyset$ in $gh^{-1} \in H$ za vsaka $g, h \in H$. Če je $g \in H$, potem je $gg^{-1} = e$ v $H$. Če je $g \in H$, potem je tudi $eg^{-1} = g^{-1}$ v $H$. Sedaj naj bosta $h_1, h_2 \in H$. Pokazati moramo, da je tudi njun produkt v $H$. Vendar velja $h_1(h_2^{-1})^{-1} = h_1h_2 \in H$. Torej je $H$ podgrupa grupe $G$.


***

**Ciklične grupe**

> Naj bo $G$ grupa in $a$ poljuben element v $G$. Tedaj je množica
> $$\langle a \rangle = \{a^k : k \in \mathbb{Z}\}$$
> podgrupa grupe $G$. Poleg tega je $\langle a \rangle$ najmanjša podgrupa grupe $G$, ki vsebuje element $a$.
> 
> >[!|dokaz]+ Dokaz:
> >Identiteta je v $\langle a \rangle$, saj velja $a^0 = e$. Če sta $g$ in $h$ poljubna elementa v $\langle a \rangle$, lahko po definiciji $\langle a \rangle$ zapišemo $g = a^m$ in $h = a^n$ za neki celi števili $m$ in $n$. Tako je $gh = a^m a^n = a^{m+n}$ ponovno v $\langle a \rangle$. Nazadnje, če je $g = a^n$ v $\langle a \rangle$, je tudi inverz $g^{-1} = a^{-n}$ v $\langle a \rangle$. Jasno je, da mora vsaka podgrupa $H$ grupe $G$, ki vsebuje $a$, zaradi zaprtosti vsebovati vse potence elementa $a$; torej $H$ vsebuje $\langle a \rangle$. Zato je $\langle a \rangle$ najmanjša podgrupa grupe $G$, ki vsebuje $a$.


Za $a \in G$ imenujemo $\langle a \rangle$ **ciklična podgrupa**, ki jo generira $a$. 

Če $G$ vsebuje nek element $a$ tak, da je $G = \langle a \rangle$, potem je $G$ **ciklična grupa**. 

V tem primeru je $a$ **generator** grupe $G$. 

Če je $a$ element grupe $G$, definiramo **red** elementa $a$ kot najmanjše pozitivno celo število $n$, za katero velja $a^n = e$, in zapišemo $|a| = n$. 

Če takšnega števila $n$ ni, rečemo, da je red elementa $a$ neskončen, in za označitev reda elementa $a$ zapišemo $|a| = \infty$.

> Vsaka ciklična grupa je Abelova.
> 
> > [!|dokaz]+ Dokaz:
> > Naj bo $G$ ciklična grupa in $a \in G$ generator grupe $G$. Če sta $g$ in $h$ elementa v $G$, ju lahko zapišemo kot potence elementa $a$, torej $g = a^r$ in $h = a^s$. Ker velja
> > $$gh = a^r a^s = a^{r+s} = a^{s+r} = a^s a^r = hg,$$
> > je $G$ Abelova.


> **Vsaka podgrupa ciklične grupe je ciklična.**
> 
> > [!|dokaz]+ Dokaz:
> > Glavni orodji v tem dokazu sta algoritem deljenja in načelo dobre urejenosti. Naj bo $G$ ciklična grupa, generirana z $a$, in naj bo $H$ podgrupa grupe $G$. Če je $H = \{e\}$, je $H$ trivialno ciklična. Predpostavimo, da $H$ vsebuje še kakšen element $g$, različen od identitete. Tedaj lahko $g$ zapišemo kot $a^n$ za neko celo število $n$. Lahko predpostavimo, da je $n > 0$. Naj bo $m$ najmanjše naravno število, za katero velja $a^m \in H$. Tak $m$ obstaja po načelu dobre urejenosti.
> > 
> > Trdimo, da je $h = a^m$ generator za $H$. Pokazati moramo, da lahko vsak $h' \in H$ zapišemo kot potenco elementa $h$. Ker je $h' \in H$ in $H$ podgrupa $G$, velja $h' = a^k$ za neko pozitivno celo število $k$. Z uporabo algoritma deljenja lahko najdemo števili $q$ in $r$ tako, da velja $k = mq + r$, kjer je $0 \leq r < m$; od tod sledi:
> > $$a^k = a^{mq+r} = (a^m)^q a^r = h^q a^r.$$
> > Tako je $a^r = a^k h^{-q}$. Ker sta $a^k$ in $h^{-q}$ v $H$, mora biti tudi $a^r$ v $H$. Vendar je bil $m$ najmanjše pozitivno število, za katero je $a^m \in H$; posledično mora biti $r = 0$ in zato $k = mq$. Torej,
> > $$h' = a^k = a^{mq} = h^q$$
> > in $H$ je generirana s $h$.


**Opomba:** Podgrupe $\mathbb{Z}$ so natanko vse $n \mathbb{Z}$.

> Naj bo $G$ ciklična grupa reda $n$ in naj bo $a$ generator grupe $G$. Potem velja $a^k = e$ natanko tedaj, ko $n$ deli $k$.
> 
> > [!|dokaz]+ Dokaz:
> > Najprej predpostavimo, da velja $a^k = e$. Po algoritmu deljenja lahko zapišemo $k = nq + r$, kjer je $0 \le r < n$. Od tod sledi
> > $$e = a^k = a^{nq+r} = a^{nq}a^r = ea^r = a^r.$$
> > Ker je $n$ najmanjše pozitivno celo število, za katero velja $a^n = e$, mora biti $r = 0$.
> > 
> > Obratno, če $n$ deli $k$, potem velja $k = ns$ za neko celo število $s$. Posledično dobimo
> > $$a^k = a^{ns} = (a^n)^s = e^s = e.$$



> Naj bo $G$ ciklična grupa reda $n$ in naj bo $a \in G$ generator te grupe. Če je $b = a^k$, potem je red elementa $b$ enak $\frac{v(n,k)}{k}$. *Da iz $a^{k}$ pridemo do $e$ moramo priti do nekega večkratnika $n$, najmanjši tak je $v(n,k)$ ampak ker gremo do njega preko $a^k$ kij rabimo le $\frac{v(n,k)}{k}$.*
> 
> Kot bolj razširjen izrek se napiše tudi da je red $a^{k}$ enak $\frac{n}{D(n,k)}$ kar lahko dokažemo ali pa izpeljemo iz zgornje enačbe preko $\frac{v(n,k)}{k}=\frac{D(n,k)^{-1}nk}{k}=\frac{n}{D(n,k)}$.
> 
> > [!|dokaz]+ Dokaz:
> > Želimo poiskati najmanjše celo število $m$, tako da velja $e = b^m = a^{km}$. Ker je red elementa $a$ enak $n$, mora biti eksponent $km$ večkratnik števila $n$. Ker je produkt $km$ hkrati že po definiciji večkratnik števila $k$, iščemo najmanjše število, ki je hkrati večkratnik $k$ in $n$. To število je po definiciji najmanjši skupni večkratnik $v(n, k)$. Torej mora veljati $km = v(n, k)$, iz česar sledi, da je najmanjši tak $m$ enak $v(n, k) / k$.

***

**Odseki**

Naj bo $H$ podgrupa grupe $G$ in $a \in G$. 

Množici $aH = \{ah : h \in H\}$ in $Ha = \{ha : h \in H\}$ imenujemo **leva oziroma desna odseka** podgrupe $H$ v grupi $G$. 

Element $a$ imenujemo predstavnik odsekov $aH$ in $Ha$.

> Naj bo $G$ grupa in $H$ podskupina grupe $G$. Tedaj velja:
> 
> - $a \in H \Leftrightarrow aH = H$. *Zaradi zaprtosti $H$.*
> - $aH = bH \Leftrightarrow a^{-1}b \in H$.
> - $a \in bH \Leftrightarrow a^{-1} \in Hb^{-1}$.
> - $a \in bH \Leftrightarrow aH = bH$.
> >[!|dokaz]+ Dokaz:
> >
> > 
> > Naj bo $H$ podgrupa grupe $G$.
> > 
> > Če je $a \in H$, potem velja $aH = H$. Naj bo $x \in aH$. Tedaj je $x = ah$ za nek $h \in H$. Ker sta $a \in H$ in $h \in H$, sledi $ah = x \in H$, saj je $H$ podgrupa. Zato velja $aH \subseteq H$. Naj bo $x \in H$. Tedaj je $x = a(a^{-1}x) \in aH$. Zato velja $H \subseteq aH$. Torej je $H = aH$. Obratno, če velja $aH = H$, potem je $a = ae \in aH$, zato je $a \in H$.
> > 
> > Če velja $aH = bH$, potem je $a^{-1}(aH) = a^{-1}(bH)$, oziroma $H = (a^{-1}b)H$. Skladno s prejšnjo točko sledi $a^{-1}b \in H$. Obratno, če velja $a^{-1}b \in H$, potem je $a^{-1}bH = H$. Če pomnožimo z leve strani z $a$, dobimo $aa^{-1}bH = aH$, oziroma $bH = aH$.
> > 
> > Če je $a \in bH$, potem je $a = bh$ za nek $h \in H$, zato je $a^{-1} = (bh)^{-1} = h^{-1}b^{-1} \in Hb^{-1}$. Obratna smer se dokaže na podoben način.
> > 
> > Če je $a \in bH$, potem velja $aH = bH$. Naj bo $x \in aH$. Tedaj je $x = ah_1$ za nek $h_1 \in H$. Prav tako $a \in bH$ pomeni $a = bh_2$ za nek $h_2 \in H$. Zato je $x = (bh_2)h_1 = b(h_2h_1) \in bH$, kar pomeni $aH \subseteq bH$. Naj bo sedaj $x \in bH$. Tedaj je $x = bh_3$ za nek $h_3 \in H$, iz $a = bh_2$ pa sledi $b = ah_2^{-1}$. Zato je $x = ah_2^{-1}h_3 \in aH$, kar pomeni $bH \subseteq aH$. Torej je $aH = bH$. Obratno, če velja $aH = bH$, potem je $a = ae \in aH$, zato je $a \in bH$.


> Naj bo $H$ podgrupa grupe $G$. Tedaj velja:
>
> - Poljubna dva leva odseka $H$ sta bodisi identična bodisi disjunktna.
>
> - Unija vseh levih odsekov $H$ je $G$.
>
> - Število elementov v poljubnem levem odseku $aH$ je enako številu elementov v $H$
> 
> > [!|dokaz]+ Dokaz:
> > Naj bosta $aH$ in $bH$ dva leva odseka. Predpostavimo, da $aH$ in $bH$ nista disjunktna. Trdimo, da je $aH = bH$. Ker $aH$ in $bH$ nista disjunktna, je $aH \cap bH \neq \emptyset$, zato obstaja element $c \in aH \cap bH$. Očitno velja $c \in aH$ in $c \in bH$, zato je $aH = cH$ in $bH = cH$. Od tod sledi $aH = bH$.
> >
> > Naj bo $a \in G$. Potem je $a = ae \in aH$ in vsak element iz $G$ pripada nekemu levemu odseku podgrupe $H$. Torej je unija vseh levih odsekov $H$ enaka $G$.
> >
> > Preslikava $f : H \to aH$, definirana s $f(h) = ah$, je očitno bijekcija. Zato ima vsak levi odsek enako število elementov kot $H$.
***

**Homomorfizmi**

Homomorfizem med grupama $(G, \cdot)$ in $(H, \circ)$ je preslikava $\phi : G \rightarrow H$, za katero velja

$$\phi(g_1 \cdot g_2) = \phi(g_1) \circ \phi(g_2)$$

za vse $g_1, g_2 \in G$. Slika preslikave $\phi$ v $H$ se imenuje slika $\phi$.
>

> Trditev 11.4. Naj bo $\phi : G_1 \rightarrow G_2$ homomorfizem grup. Tedaj velja:
> 1. Če je $e$ identiteta grupe $G_1$, potem je $\phi(e)$ identiteta grupe $G_2$;
> 2. Za vsak element $g \in G_1$ velja $\phi(g^{-1}) = [\phi(g)]^{-1}$;
> 3. Če je $H_1$ podgrupa grupe $G_1$, potem je $\phi(H_1)$ podgrupa grupe $G_2$;
> 4. Če je $H_2$ podgrupa grupe $G_2$, potem je $\phi^{-1}(H_2) = \{g \in G_1 : \phi(g) \in H_2\}$ podgrupa grupe $G_1$. Poleg tega, če je $H_2$ normalna podgrupa grupe $G_2$, potem je $\phi^{-1}(H_2)$ normalna podgrupa grupe $G_1$.
> 
> > [!|dokaz]+ Dokaz:
> > Naj bosta $e$ in $e'$ identiteti grup $G_1$ oziroma $G_2$; tedaj velja $e'\phi(e) = \phi(e) = \phi(ee) = \phi(e)\phi(e)$. S krajšanjem dobimo $\phi(e) = e'$.
> > 
> > Druga trditev sledi iz dejstva, da je $\phi(g^{-1})\phi(g) = \phi(g^{-1}g) = \phi(e) = e'$.
> > 
> > Množica $\phi(H_1)$ ni prazna, saj identiteta grupe $G_2$ leži v $\phi(H_1)$. Naj bo $H_1$ podgrupa grupe $G_1$ in naj bosta $x$ in $y$ v $\phi(H_1)$. Obstajata elementa $a, b \in H_1$, tako da je $\phi(a) = x$ in $\phi(b) = y$. Ker je $xy^{-1} = \phi(a)[\phi(b)]^{-1} = \phi(ab^{-1}) \in \phi(H_1)$, je $\phi(H_1)$ podgrupa grupe $G_2$ po trditvi 3.31.
> > 
> > Naj bo $H_2$ podgrupa grupe $G_2$ in definirajmo $H_1$ kot $\phi^{-1}(H_2)$; torej je $H_1$ množica vseh $g \in G_1$, za katere velja $\phi(g) \in H_2$. Identiteta je v $H_1$, saj je $\phi(e) = e'$. Če sta $a$ in $b$ v $H_1$, potem je $\phi(ab^{-1}) = \phi(a)[\phi(b)]^{-1}$ v $H_2$, saj je $H_2$ podgrupa grupe $G_2$. Torej velja $ab^{-1} \in H_1$ in $H_1$ je podgrupa grupe $G_1$. Če je $H_2$ normalna podgrupa v $G_2$, moramo pokazati, da velja $g^{-1}hg \in H_1$ za $h \in H_1$ in $g \in G_1$. Toda $\phi(g^{-1}hg) = [\phi(g)]^{-1}\phi(h)\phi(g) \in H_2$, saj je $H_2$ normalna podgrupa grupe $G_2$. Zato je $g^{-1}hg \in H_1$.

**Jedro** homomorfizma so vsi elementi iz $G$ ki se preslikajo v $e_{H}$ oz. zapišemo lahko $f^{-1}(e_{H})$.

> Jedro je edinka $G$-ja, *saj je trivialna podgrupa edinka v $H$.*


> Naj bo $G = \langle a \rangle$ ciklična grupa z generatorjem $a$ in $H$ poljubna grupa. Homomorfizem $\phi: G \to H$ je povsem določen s sliko generatorja $a$, torej z vrednostjo $\phi(a)$.
> 
> > [!|dokaz]+ Dokaz:
> > Ker je $G$ ciklična grupa z generatorjem $a$, lahko vsak element $g \in G$ zapišemo kot potenco generatorja $a$, torej $g = a^n$ za neko celo število $n$. Ker je $\phi$ homomorfizem, z indukcijo sledi, da za vsak $n \in \mathbb{Z}$ velja $\phi(a^n) = (\phi(a))^n$. Torej imamo:
> > $$\phi(g) = \phi(a^n) = (\phi(a))^n$$
> > Ker je vrednost $\phi(g)$ za vsak element $g$ določena le z $\phi(a)$ in $n$, je homomorfizem $\phi$ povsem določen z vrednostjo $\phi(a)$.
> >


> Naj bo $G = \langle a \rangle$ ciklična grupa reda $n$ in $H$ poljubna grupa. Homomorfizem $\phi: G \to H$ je povsem določen s sliko generatorja $a$, torej z vrednostjo $\phi(a) = b$. Preslikava $\phi$ je dobro definiran homomorfizem natanko tedaj, ko red elementa $b$ v $H$ deli $n$.
> 
> > [!|dokaz]+ Dokaz:
> > Ker je $G$ ciklična grupa z generatorjem $a$, lahko vsak element $g \in G$ zapišemo v obliki $g = a^k$, kjer je $0 \leq k < n$. Če je $\phi$ homomorfizem, mora veljati $\phi(g) = \phi(a^k) = (\phi(a))^k = b^k$. To kaže, da je preslikava $\phi$ povsem določena z izbiro slike generatorja $b$.
> > 
> > Da bo preslikava $\phi$ dobro definirana, moramo zagotoviti, da vrednost $\phi(a^k)$ ni odvisna od reprezentacije elementa $g$. Ker je $a^n = e_G$, mora veljati $\phi(a^n) = \phi(e_G) = e_H$. Če definiramo $\phi(a) = b$, mora torej veljati $b^n = e_H$. To je res natanko tedaj, ko red elementa $b$ (označimo ga z $|b|$) deli $n$. Če ta pogoj velja, je preslikava $\phi(a^k) = b^k$ dobro definiran homomorfizem.









***

**Izomorfizmi**

Grupi sta **izomorfni** če velja da obstaja bijektivna preslikava $f: G \rightarrow H$ tako da velja

$$f(ab) = f(a)f(b)$$

Če je $f$ izomorfizem, je $f^{-1}$ izomorfizem.

Če imamo izomorfizem iz $G$ v $H$ potem velja $|G| = |H|$, in velja da če je $G$ abelova je tudi $H$ abelova.



> Če je $G$ ciklična grupa, potem je $H$ ciklična grupa.
> 
> > [!|dokaz]+ Dokaz:
> > Naj bo $G$ ciklična grupa in naj bo $g$ njen generator, torej $G = \langle g \rangle$. Želimo pokazati, da je $H$ ciklična grupa, ki jo generira element $\phi(g)$. Vzemimo poljuben element $h \in H$. Ker je $\phi$ izomorfizem (in s tem surjektivna preslikava), obstaja element $x \in G$, da velja $\phi(x) = h$. Ker je $G$ ciklična, lahko $x$ zapišemo kot $g^k$ za neko celo število $k$. Potem velja:
> > $$h = \phi(x) = \phi(g^k)$$
> > Ker je $\phi$ homomorfizem, velja $\phi(g^k) = (\phi(g))^k$. Torej je $h = (\phi(g))^k$. Ker smo poljuben element $h$ iz $H$ zapisali kot potenco elementa $\phi(g)$, je $H$ ciklična grupa z generatorjem $\phi(g)$.
> 

> Če ima $G$ podgrupo reda $n$, potem ima $H$ podgrupo reda $n$.
> 
> > [!|dokaz]+ Dokaz:
> > Naj bo $K \leq G$ podgrupa v $G$, katere red je $|K| = n$. Definirajmo sliko te podgrupe v $H$ kot množico $\phi(K) = \{ \phi(k) \mid k \in K \}$. Ker je slika podgrupe pri homomorfizmu vedno podgrupa, je $\phi(K)$ podgrupa v $H$. Ker je $\phi$ izomorfizem, je preslikava injektivna. Injektivnost nam zagotavlja, da se različni elementi iz $K$ preslikajo v različne elemente v $H$, zato je število elementov v $\phi(K)$ enako številu elementov v $K$. Torej velja:
> > $$|\phi(K)| = |K| = n$$
> > Skupina $H$ ima torej podgrupo $\phi(K)$ reda $n$



> Vse ciklične grupe neskončnega reda so izomorfne $\mathbb{Z}$.
>
> > [!|dokaz]+ Dokaz:
> > Naj bo $G$ ciklična grupa neskončnega reda in naj bo $a$ generator grupe $G$. Definirajmo preslikavo $\phi: \mathbb{Z} \rightarrow G$ s predpisom $\phi: n \mapsto a^n$. Tedaj velja
> > $$\phi(m + n) = a^{m+n} = a^m a^n = \phi(m)\phi(n)$$
> > Da pokažemo, da je $\phi$ injektivna, predpostavimo, da sta $m$ in $n$ elementa v $\mathbb{Z}$, kjer $m \neq n$. Lahko predpostavimo, da je $m > n$. Pokazati moramo, da je $a^m \neq a^n$. Predpostavimo nasprotno, torej $a^m = a^n$. V tem primeru je $a^{m-n} = e$, kjer je $m-n > 0$, kar je v protislovju z dejstvom, da ima $a$ neskončni red. Naša preslikava je surjektivna, saj lahko vsak element v $G$ zapišemo kot $a^n$ za neko celo število $n$ in velja $\phi(n) = a^n$.


> Če je $G$ ciklična grupa reda $n$, potem je $G$ izomorfna $\mathbb{Z}_n$.
> 
> > [!|dokaz]+ Dokaz:
> > Naj bo $G$ ciklična grupa reda $n$, ki jo generira $a$, in definirajmo preslikavo $\phi : \mathbb{Z}_n \rightarrow G$ s predpisom $\phi(k) = a^k$ za $0 \leq k < n$.
> >
> > Najprej pokažimo, da je preslikava dobro definirana. Če je $k \equiv j \pmod n$, potem je $k - j = qn$ za nek $q \in \mathbb{Z}$. Tedaj velja $a^k = a^{j+qn} = a^j(a^n)^q = a^j e^q = a^j$. Torej je preslikava neodvisna od izbire predstavnika razreda.
> >
> > Pokažimo, da je $\phi$ homomorfizem. Za poljubna $k, m \in \mathbb{Z}_n$ velja $\phi(k +_n m) = a^{k +_n m}$. Ker je $a^n = e$, velja $a^{k +_n m} = a^{k+m} = a^k a^m = \phi(k)\phi(m)$.
> >
> > Nazadnje pokažimo, da je $\phi$ bijekcija. Ker sta množici $\mathbb{Z}_n$ in $G$ končni in imata obe $n$ elementov, zadošča pokazati, da je $\phi$ injektivna. Če je $\phi(k) = e$, potem je $a^k = e$. Ker je red elementa $a$ enak $n$ in je $0 \leq k < n$, sledi, da mora biti $k = 0$. Jedro preslikave je tako $\{0\}$, kar pomeni, da je $\phi$ injektivna. Ker je $\phi$ injektivna preslikava med končnima množicama z enakim številom elementov, je tudi surjektivna in s tem izomorfizem.

<br>

Izomorfizmi določijo ekvivalenčno relacijo na množici vseh grup.

<br>

**Caylejev izrek**

> Izrek (Cayley). Vsaka grupa je izomorfna grupi permutacij.
> 
> > [!|dokaz]+ Dokaz:
> > Naj bo $G$ grupa. Poiskati moramo grupo permutacij $\bar{G}$, ki je izomorfna grupi $G$. Za poljuben $g \in G$ definirajmo funkcijo $\lambda_g : G \to G$ s predpisom $\lambda_g(a) = ga$. Trdimo, da je $\lambda_g$ permutacija grupe $G$. Da pokažemo, da je $\lambda_g$ injektivna (ena-proti-ena), predpostavimo, da je $\lambda_g(a) = \lambda_g(b)$. Tedaj velja
> > $$ga = \lambda_g(a) = \lambda_g(b) = gb$$
> > Od tod sledi $a = b$. Da pokažemo, da je $\lambda_g$ surjektivna (na), moramo dokazati, da za vsak $a \in G$ obstaja $b$, tako da velja $\lambda_g(b) = a$. Naj bo $b = g^{-1}a$.
> > Sedaj smo pripravljeni definirati našo grupo $\bar{G}$. Naj bo
> > $$\bar{G} = \{\lambda_g : g \in G\}$$
> > Pokazati moramo, da je $\bar{G}$ grupa za operacijo komponiranja funkcij in poiskati izomorfizem med $G$ in $\bar{G}$. Imamo zaprtost za operacijo komponiranja funkcij, saj velja
> > $$(\lambda_g \circ \lambda_h)(a) = \lambda_g(ha) = gha = \lambda_{gh}(a)$$
> > Prav tako velja
> > $$\lambda_e(a) = ea = a$$
> > in
> > $$(\lambda_{g^{-1}} \circ \lambda_g)(a) = \lambda_{g^{-1}}(ga) = g^{-1}ga = a = \lambda_e(a)$$
> > Izomorfizem iz $G$ v $\bar{G}$ lahko definiramo s $\phi : g \mapsto \lambda_g$. Grupna operacija se ohranja, saj velja
> > $$\phi(gh) = \lambda_{gh} = \lambda_g \lambda_h = \phi(g)\phi(h)$$
> > Preslikava je tudi injektivna, saj če je $\phi(g)(a) = \phi(h)(a)$, potem velja
> > $$ga = \lambda_g a = \lambda_h a = ha$$
> > Od tod sledi, da je $g = h$. Da je $\phi$ surjektivna, sledi iz dejstva, da je $\phi(g) = \lambda_g$ za vsak $\lambda_g \in \bar{G}$. Izomorfizem $g \mapsto \lambda_g$ imenujemo leva regularna reprezentacija grupe $G$.

***

**Zunanji direktni produkti**

Če sta $(G, \cdot)$ in $(H, \circ)$ grupi, lahko kartezični produkt $G$ in $H$ spremenimo v novo grupo. Kot množica je naša grupa sestavljena le iz urejenih parov $(g, h) \in G \times H$, kjer je $g \in G$ in $h \in H$. Binarno operacijo na $G \times H$ lahko definiramo kot $(g_1, h_1)(g_2, h_2) = (g_1 \cdot g_2, h_1 \circ h_2)$; to pomeni, da elemente v prvi koordinati množimo tako, kot to počnemo v $G$, elemente v drugi koordinati pa tako, kot to počnemo v $H$. Tukaj smo zaradi jasnosti posebej navedli operaciji $\cdot$ in $\circ$ v vsaki grupi; ponavadi pišemo kar $(g_1, h_1)(g_2, h_2) = (g_1 g_2, h_1 h_2)$.

> Naj bosta $G$ in $H$ grupi. Množica $G \times H$ je grupa za operacijo $(g_1, h_1)(g_2, h_2) = (g_1 g_2, h_1 h_2)$, kjer sta $g_1, g_2 \in G$ in $h_1, h_2 \in H$.
>
> > [!|dokaz]+ Dokaz:
> > Očitno je zgoraj definirana binarna operacija zaprta. Če sta $e_G$ in $e_H$ identiteti grup $G$ oziroma $H$, potem je $(e_G, e_H)$ identiteta grupe $G \times H$. Inverz elementa $(g, h) \in G \times H$ je $(g^{-1}, h^{-1})$. Dejstvo, da je operacija asociativna, neposredno sledi iz asociativnosti grup $G$ in $H$.

> Naj bo $(g,h) \in G \times H$. Če imata $g$ in $h$ končna reda $r$ oziroma $s$, potem je red $(g,h)$ v $G \times H$ enak najmanjšemu skupnemu večkratniku $r$ in $s$.
>
> > [!|dokaz]+ Dokaz:
> > Predpostavimo, da je $m$ najmanjši skupni večkratnik $r$ in $s$, in naj bo $n = |(g,h)|$. Tedaj velja
> > $$(g,h)^m = (g^m,h^m) = (e_G,e_H)$$
> > $$(g^n,h^n) = (g,h)^n = (e_G,e_H)$$
> > Od tod sledi, da mora $n$ deliti $m$, in $n \le m$. Vendar pa po drugi enačbi tako $r$ kot $s$ delita $n$; zato je $n$ skupni večkratnik $r$ in $s$. Ker je $m$ najmanjši skupni večkratnik $r$ in $s$, velja $m \le n$. Posledično mora biti $m$ enak $n$.

> **Posledica:** Naj bo $(g_1, \dots, g_n) \in \prod G_i$. Če ima $g_i$ končni red $r_i$ v $G_i$, potem je red $(g_1, \dots, g_n)$ v $\prod G_i$ enak najmanjšemu skupnemu večkratniku $r_1, \dots, r_n$.

> Grupa $\mathbb{Z}_m \times \mathbb{Z}_n$ je izomorfna $\mathbb{Z}_{mn}$ natanko tedaj, ko je $\gcd(m,n) = 1$.
>
> > [!|dokaz]+ Dokaz:
> > Najprej bomo pokazali, da če velja $\mathbb{Z}_m \times \mathbb{Z}_n \cong \mathbb{Z}_{mn}$, potem je $\gcd(m,n) = 1$. Dokazali bomo kontrapozicijo; to je, pokazali bomo, da če je $\gcd(m,n) = d > 1$, potem $\mathbb{Z}_m \times \mathbb{Z}_n$ ne more biti ciklična. Opazimo, da je $mn/d$ deljivo z $m$ in $n$; torej za poljuben element $(a,b) \in \mathbb{Z}_m \times \mathbb{Z}_n$ velja
> > $$\underbrace{(a,b) + (a,b) + \cdots + (a,b)}_{mn/d \text{ krat}} = (0,0).$$
> > Zato noben $(a,b)$ ne more generirati celotne grupe $\mathbb{Z}_m \times \mathbb{Z}_n$.
> > Obrat sledi neposredno iz izreka 9.17, saj je $\text{lcm}(m,n) = mn$ natanko tedaj, ko je $\gcd(m,n) = 1$.

> **Posledica:** Naj bodo $n_1, \dots, n_k$ pozitivna cela števila. Tedaj je
> $$\prod_{i=1}^k \mathbb{Z}_{n_i} \cong \mathbb{Z}_{n_1 \cdots n_k}$$
> natanko tedaj, ko je $\gcd(n_i, n_j) = 1$ za $i \neq j$.

> **Posledica:**. Če je
> $$m = p_1^{e_1} \cdots p_k^{e_k},$$
> kjer so $p_i$ različna praštevila, potem je
> $$\mathbb{Z}_m \cong \mathbb{Z}_{p_1^{e_1}} \times \cdots \times \mathbb{Z}_{p_k^{e_k}}.$$
>
> > [!|dokaz]+ Dokaz:
> > Ker je največji skupni delitelj $p_i^{e_i}$ in $p_j^{e_j}$ enak 1 za $i \neq j$, dokaz sledi iz  prejšnjih posledic.












> Če imamo hm. grup in imamo el. $x$ reda $n$ potem mora biti red $f(x)$ delitelj $n$.
> 
> >[!|dokaz]+ Dokaz:
> > Velja 
> > $$xn = 0$$
> > $$f(xn) = 0$$
> > $$nf(x)=0$$
> > torej mora biti red $f(x)$ nek delitelj $n$.


> Če imamo grupo ki jo generira $x$ potem bo vsak homomorfizem definiran s sliko generatorja, velja pa da se generator reda $n$ lahko slika samo v elemente reda ki delijo $n$.

