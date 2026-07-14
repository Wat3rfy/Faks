
### Kompleksna števila

Kompleksno število $z = a+b i$ je kompleksno število, kjer je $i$ imaginarna enota in velja

$$i^{2} = -1$$

Predstalvjena so v kompleksni ravnini in jih lahko zapišemo kot par $(a,b)$.

Definirano je seštevanje po komponentah.

Množenje je definirano kot

$$a+bi \cdot c + di = ac -bd + i(ad + bc)$$

če to poskusimo zapisati kot funkcijo iz $\mathbb{R}^{2}$ v $\mathbb{R}^{2}$, $w = c+di$ dobimo

$$f_{w}(a,b) = \begin{pmatrix}
ac-bd\\
ad+bc
\end{pmatrix}$$

Kot linearno preslikavo zapišemo kot

$$
\begin{pmatrix}
c & -d \\
d & c
\end{pmatrix}
\begin{pmatrix}
a \\
b
\end{pmatrix}
=
\begin{pmatrix}
ac-bd\\
ad+bc
\end{pmatrix}
$$

Kompleksno število lahko konjugiramo

$$\overline{z} = a - ib$$
$$\text{Re} = \frac{z + \overline{z}}{2}$$
$$\text{Im} = \frac{z - \overline{z}}{2i}$$

<br>

$$
\overline{\overline{z}} = z
$$
$$
\overline{z + w} = \overline{z} + \overline{w}
$$
$$
\overline{z \cdot w} = \overline{z} \cdot \overline{w}
$$
$$
\overline{\left(\frac{z}{w}\right)} = \frac{\overline{z}}{\overline{w}}, \quad w \neq 0
$$
$$
\overline{z^n} = (\overline{z})^n
$$
$$
z = \overline{z} \iff z \in \mathbb{R}
$$

Velja tudi identiteta

$$\left|z \right| = \sqrt[]{z \overline{z}}$$
$$= \sqrt[]{a^{2}+b^{2}}$$

Za abs. vrednost velja

$$
|z \cdot w| = |z| |w|
$$
$$
\left|\frac{z}{w}\right| = \frac{|z|}{|w|}
$$
$$
|z^n| = |z|^n
$$

$$
|z| - |w|\leq |z + w| \leq |z| + |w|

$$
$$
  ||z| - |w||\leq|z - w|
$$
$$
|\overline{z}| = |z|
$$

Kompleksno število lahko zapišemo v polarnem zapisu

$$z = |z|(\cos\,\! \varphi + i \sin\,\! \varphi)$$

kjer je $a = |z| \cos\,\! \varphi$ in $b = |z| \sin\,\! \varphi$.

$\varphi$ pravimo tudi argument $z$ oziroma $\varphi = \arg z$.

Oblika je uporabna pri množenju. Velja da argumenta seštejemo in dolžini pomnožimo.
***
### Riemannova sfera

Kompleksna ravnina je množica vseh kompleksnih števil. Ta **ni kompaktna**. Obstaja na primer zaporedje $a_{n} = n$ ki nima konvergentnega podazporedja.
Narašča v $\infty$ kar v $\mathbb{C}$ ne obstaja kar pomeni da "pobegne" iz prostora.
To nam onemogoča da bi definirali $f(z)= \frac{1}{z}$ kjer je $f(0) = \infty$ ker $\infty \notin \mathbb{C}$.
Za kompaktnost manjka točka v neskončnosti h kateri konvergirajo taka zaporedja.

Definiramo $\mathbb{C} \cup \{ \infty\}$. Ta prostor lahko preslikamo v sfero in dokažemo da je res kompakten z bijekcijo.

Definiramo **Riemannovo sfero** kot enotsko kroglo $K$. Naj bo $S$ severna točka sfere $(0,0,1)$. 
Vsaka točka na kompleksni ravnini se lahko preslika na sfero tako da potegnemo črto od $S$ do točke na ravnini in vzamemo točko preseka s sfero.

Hitra izpeljava bijekcije iz $\mathbb{C}$ v Riemannovo sfero je sledeča.

Vzamemo točko na sferi ki bo slika označena kot $T' = (x,y,z)$ in točko na kompleksni ravnini $T=(a,b,0)$. Za vektorja od $S$ do $T'$ velja da je skalar vektorja od $S$ do $T$.

$$x = (a,b,0)-(0,0,1) = (a,b,-1)$$
$$y = (a',b',z)-(0,0,1) = (a',b',z-1)$$
$$tx = y$$
$$t(a,b,-1) = (a',b',z-1)$$

S tem dobimo 3 enačbe.

$$ta = a'$$
$$tb = b'$$
$$1-t = z$$

Ker vemo da za sfero velja

$$x^{2}+y^{2}+z^{2} = 1$$

in je $(a',b',z)$ na sferi dobimo

$$(ta)^{2}+(tb)^{2}+(1-t)^{2} = 1$$
$$(ta)^{2}+(tb)^{2}+1+t^{2}-2t = 1$$
$$ t^{2}(a^{2}+b^{2}+1)-2t=0$$
$$t(a^{2}+b^{2}+1)-2=0$$
$$t=\frac{2}{a^{2}+b^{2}+1}$$

V 3 enačbe vstavimo $t$.

$$\frac{2}{a^{2}+b^{2}+1}a = a'$$
$$\frac{2}{a^{2}+b^{2}+1}b = b'$$
$$1-\frac{2}{a^{2}+b^{2}+1} = z$$

Velja

$$\varphi(a,b) = \left(\frac{2a}{a^{2}+b^{2}+1},\frac{2b}{a^{2}+b^{2}+1},\frac{a^{2}+b^{2}-1}{a^{2}+b^{2}+1}\right)$$

S tem smo **definirali riemannovo sfero**. Opazimo da se vsako kompleksno število preslika v neko točko na sferi **razen v $S$ oz. $(0,0,1)$.** Dobili smo bijekcijo med $\mathbb{C}$ in $K\backslash\{ S\}$.

**Definiramo $\varphi(S) = \infty$.**

S  tem dobimo preslikavo $\varphi: K \rightarrow \mathbb{C}_{\infty}$ ki je bijektivna in zvezna.

Ker je sfera omejena in kompaktna množica je $\mathbb{C}_\infty$ **kompaktna**.

To nam omogoča rigorozno obravnavanje konceptov ki so bili prej problematični.

$z_{n} = n$ nima limite v $\mathbb{C}$, ampak v $\mathbb{C}_{\infty}$ velja $z_{n} \rightarrow \infty \Leftrightarrow |z_{n}| \rightarrow \infty$.
Gre v konkretno točko. *Po sferi gre v $S$.*

$f(z) =\frac{1}{z}$ lahko prevedemo na funkcijo $g(w) = f(\frac{1}{w})=w$ v točki $w = 0$. Ker je prostor kompakten in homogen je okolica $\infty$ enaka okolici $0$. 

*V realnih številih lahko storimo podobno da določimo eno točko za neskočnost. Tega ne ponavadi ne delamo saj uniči urejenost realnih števil. Ker kompleksna števila nimajo ureditve s tem **ne izgubimo nobene lastnosti** in omogočimo deljenje z vsemi števili.*

*S tem poenostaivmo inverzije - $\frac{1}{z}$, dobimo izreke o racionalnih funkcijah - vsak racionalna funkcija stopnje $n$ se dotakne vsake vrednosti $n$-krat.*

*Če ne definiramo $1/0$:*
*Opazujmo $f(z) = \frac{1}{z}$. To je funkcija stopnje 1.*
*Ali doseže vrednost 5? Da, pri $z=1/5$.*
*Ali doseže vrednost 0? Ne. (Ne obstaja končen $z$, kjer bi veljalo $1/z=0$).*
*Ali doseže vrednost $\infty$? Ne. (Ker $1/0$ ni definirano).*
*Izrek ne deluje. Funkcija "zgreši" določene vrednosti.*

*Če definiramo $1/0=\infty$ in $1/\infty=0$:*
*Ali doseže 0? Da, pri $z=\infty$.*
*Ali doseže $\infty$? Da, pri $z=0$.*
*Izrek deluje*


***

### Zaporedja v kompleksnih številih

Člen zapišemo kot

$$z_{n} = a_{n}+ib_{n}$$

Velja da konvergira k $z$ natanko tedaj ko za vsak $\varepsilon>0$ velja da obstaja $N$ tako da $\forall  n \geq N$

$$|z-z_{n}| < \varepsilon$$

Zaporedje $z_{n}$ je omejeno če obstaja število $M$ da velja

$$|z_{n}| \leq M$$

Za cauchyjev izrek velja enako tukaj.




