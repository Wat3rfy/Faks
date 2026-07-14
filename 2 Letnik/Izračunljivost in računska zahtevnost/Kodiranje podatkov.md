


**Kodiranje podatkov** je preslikava nekega elementa iz neke množice $X$ v niz neke abecede $\Sigma$.

$$E : X \rightarrow \Sigma^{*}$$

$E$ mora biti tudi **injektivna**. **Ne tudi surjektivna**

Najprej definirajmo ključne pojme, ki so analogni tistim iz teorije jezikov.

Ponavadi je množica $X$ neka izvorna abeceda oz. Kleenejeva zvezda, torej vsi možni nizi neke abecede.

Pri teoriji računalništva najpogosteje slikamo v nize binarne abecede $\{ 0,1\}^{*}$. 

Primer kodirne funkcije med naravnimi števili in binarnimi nizi je

$$E_{N} : \mathbb{N} \rightarrow \{ 0,1\}^{*}$$

$$E_{N} = \begin{cases}
0 \,;\;n=0 \\
1 \,;\;n=1 \\
E_{N}\lfloor \frac{n}{2}  \rfloor \cdot \text{parity}(n);\; n > 1
\end{cases} $$

kjer množenje s $\text{parity}(n)$ predstavlja konkatenacijo.

Iz tega lahko sestavimo reprezentacijo celih števil kjer velja

$$E_{Z}(x) = \begin{cases}
0 \cdot E_{N}(x) \,;\;x \geq 0 \\
1 \cdot E_{N}(x) \,;\, x< 0
\end{cases}$$

To je injektivna funkcija a ni surjektivna. Na primer ne obstaja celo število ki bi se slikalo v prazen niz, a je to v redu saj zahtevamo le injektivnost.

Za racionalna števila imamo problem ker bi potrebovali neko ločilo. Hočemo preslikati par nizov $x,y \in \{ 0,1\}^{*}$ v en niz iz abecedea $\Sigma = \{ 0,1, |\}$, kjer $|$ služi kot ločilo med števcem $(x)$ in imenovalcem $(y)$. Enak efekt lahko dosežemo z abecedo $\{ 01,00,11\}  \subset \{ 0,1\}^{2}$ in zakodiramo vsako število kot niz iz $\{ 00,11,01\}^{* }\rightarrow\{ 0,1\}^{*}$. Torej se nam ponavljajo števke a še vedno obstaja reprezentacija.

Za predstavitev števila $\frac{a}{b}$ sedaj naprej predstavimo obe celi števili z $E_{Z}(x)$ ju združimo v par nizov in jo predstavimo z abecedo $\{ 00,11,01\}$, kjer je $01$ ločilo.


Iz tega sledi da če lahko predstaivmo objekt $T$ kot niz, potem lahko predstavimo terice objektov $T$ z nizi.

Rečemo da je množica $X$ števna če velja da obstaja surjektivna preslikava iz $\mathbb{N}$ v $X$ oz. injektivna preslikava iz $X$ v $\mathbb{N}$.

Za množico $\{ 0,1\}^{*}$ vemo da je števna saj obstaja injektivna preslikava iz $\{ 0,1\}^{*}$ v $\mathbb{N}$ kot pretvorba binarnega zapisa v naravno število.

>**Cantorjev izrek** pravi da ne obstaja injektivna preslikava $\mathbb{R} \rightarrow \{ 0,1\}^{*}$
>oz. ekvivalentno ne obstaja injekcija $\mathbb{R} \rightarrow \mathbb{N}$ oz. ne obstaja injekcija $P(\mathbb{N})\rightarrow \mathbb{\mathbb{N}}$.
>>[!|dokaz]+ Dokaz:
>>Dokazujemo da ne obstaja injekcija med $\mathbb{R}$ in $\{ 0,1\}^*$.
>>Vemo da je $\{ 0,1\}^{*}$ enako velika kot $\mathbb{N}$ torej lahko dokažemo da ne obstaja injekcija med $\mathbb{R}$ in $\mathbb{N}$.

**Neštevnost booleanovih funkcij** je izrek ki trdi da množica booleanovih funkcij $f : \{ 0,1\}^{*} \rightarrow \{ 0,1\}$. Oz. ne obstaja surjektivna funkcija iz $\{ 0,1\}^{*} \rightarrow$ množico booleanovih funkcij.

To je pomemben sklep, kjer dejansko povemo da ker je problemov (funkcij) neštevno mnogo, programov (nizov) pa števno mnogo velja da **obstajajo problemi, ki jih računalnik ne more rešiti**.

Ker lahko predstavljamo še druge elemente. Definiramo reprezentacijsko shemo za predstavitev objektov neke množice $X$. Ta je sestavljena iz **kodirne funkcije** ki preslika objekt $x$ v niz in **dekodirne funkcije** ki dekodira niz nazaj v objekt $x$. 

$$E: X \rightarrow \{ 0,1\}^{*}$$
$$D: \{ 0,1\}^{*} \rightarrow_{p}\; X $$

sta taki funkciji da velja $D(E(x)) = x$ za vsak $x \in X$.

$D$ je tako surjektivna, obe pa morata biti injektivni.

$X$ je končna če lahko, vsak element predstavimo kot nek končen niz.