Ko govorimo o vsebovanju nekega $(x)$ v $(y)$ je ideja to da $(x)$ generira manjšo množico kot $(y)$ in $(y)$ vsebuje celotno $(x)$. Npr. $(6)$ in $(3)$ kjer $(3)$ vsebuje $(6)$.


Če imamo nek kvocientne kolobar $R/I$ potem bo veljalo da so ideali v $R/I$ v bijekciji z ideali v $R$ ki vsebujejo $I$.

Torej za primer naj bodo $\mathbb{Z}/6\mathbb{Z}$

$$\mathbb{Z}/6\mathbb{Z}$$

$$
\phi : \{ \mathbb{Z}, 2\mathbb{Z}, 3\mathbb{Z}, 6\mathbb{Z} \} \to \{ \text{ideali } \mathbb{Z}/6\mathbb{Z}\}
$$

$$
\begin{aligned}
&  \mathbb{Z}/6\mathbb{Z} =\{0, 1, 2, 3, 4, 5\} \\\\
&\{0,1,2,3,4,5\} \\
&\{0, 2, 4\} \longleftrightarrow 2\mathbb{Z}/6\mathbb{Z} \\
&\{0, 3\} \\
&\{0\}
\end{aligned}
$$

in vidimo da si lahko $2\mathbb{Z}/6\mathbb{Z}$ razlagamo takole

Imamo večkratnike $2$, potem pa te večkratnike delimo po $(2)/(2)(3)$ torej če si lahko predstavljamo kako to predstavlja večkratnike 2, kjer jih razdelimo po tem koliko števil lahko še uporabimo za množenje z dva da pridemo do nekega množenje s trikratnikom.

Za delitev bi zgledala nekako kot da imamo $2,4,6,8,10,12$ torej mi generiramo $2$ kot $2 \cdot 1$ potem pa lahko uporabimo še $2$ da dobimo $2 \cdot  2$ za $4$, naslednje množenje oz. generacija s $3$ je $2 \cdot 3$ kar je $6$ in seveda $3$ je v $(3)$ kar pomeni da po tem delimo kar je v tem kvocientnem kolobarju spet 0. Torej

$$0 \cdot 2 =0$$
$$1 \cdot 2 = 2$$
$$2 \cdot 2 = 4$$
$$3 \cdot 2 = 6$$

torej nam ta kvoceientni kolobar deli našo generirano množico po tem koliko števil lahko generiramo dokler ne pridemo do enega ki pripada $(3)$, v našem primeru lahko $3$ in to so $0,2,4$ ki predstavljajo ostanke. To potem za neko intuicijo zapišemo kot

$$(2) ... (2)(3)$$

To je preprost primer ki napeljuje na to kako potem delamo pri polinomih.
Naj bo primer $K=\mathbb{Z}_{2}[x]/(x^{3}+1)$. Ta ni več tako trivialen.

Najprej vidimo da je $K = \{ 0,1,x,x^{2},x^{2}+1,x+1,x+x^{2},x^{2}+x+1\}$

Sedaj pogledamo kateri ideali vsebujejo $I=(x^{3}+1)$ v $K$. Razcepimo ta polinom in dobimo naslednje ideale v $K$.

$$((x^2+x+1)(x+1)),(x^{2}+x+1),(x+1),(1)$$

Ti ideali vsebujeo $I$.

Iz $(x^{2}+x+1)$ dobimo kvocientni kolobar $(x^{2}+x+1)/(x^{2}+x+1)(x+1)$.

Če vzamemo $(x^{2}+x+1)$ in rečemo da gledamo koliko elemenotv imamo da pridemo do $(x+1)(x^{2}+x+1)$ po kateri delimo!!. Tukaj vidimo da lahko pomnožimo z $1,x,x+1$ in ko množimo z $x+1$ dobimo $0$ v kvocientnem kolobarju. Torej imamo

$$0 \; \cdot\; x^{2}+x+1 = 0$$
$$1 \; \cdot\;  x^{2}+x+1 = x^{2}+x+1$$
$$x \; \cdot\;  x^{2}+x+1 = x^{3}+x^{2}+x = x ^{2}+x+1$$
$$x+1 \; \cdot\; x^{2}+x+1 = x^{3}+x^{2}+x+x^{2}+x+1=x^{3}+1=0$$

torej sta edina elementa

Če vzamemo $(x+1)$ in rečemo da gledamo koliko elemenotv imamo da pridemo do $(x^{2}+x+1)(x+1)$.

$$0 \; \cdot\; x+1 = 0$$
$$1 \; \cdot\;  x+1 =  x+1 $$
$$x \; \cdot\;  x+1 = x^{2}+x$$
$$x+1 \; \cdot\;  x+1 = x^{2}+1$$
$$x^{2} \; \cdot\;  x+1 = x^{3}+x = 1+x$$
$$x^{2} +x\; \cdot\;  x+1 = x^{3}+x^{2}+x^{2}+x = x^{3}+x = 1+x$$
$$x^{2}+1 \; \cdot  \; x+1 = x^{3}+x^{2}+x+1 = x^{2}+x$$
$$x^{2}+x+1 \; \cdot \; x+1 = 0$$

torej so elementi $x+1,x^{2}+x, x^{2}+1,0$