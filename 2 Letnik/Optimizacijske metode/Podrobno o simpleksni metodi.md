*Na hitro še o neenačbah. Če imamo premico $Ax+By = C$ lahko vzamemo gradient - to nam pove v katero smer narašča funkcija, če potem vzamemo neenakost torej $Ax + By \leq C$ recimo potem pogledamo kam gleda vektor $A,B$ - naš gradient in vemo da bo rep tega vektorja tisti del ravnine ki bo pobarvan - nato ugotovimo kje je naša premica - v našem primeru s pomočjo gradienta ugovotimo da je za $C$ stran od izhodišča v smeri gradienta pravokotna na gradient - in pobarvamo del proti repu gradienta - to je ker imamo $\leq$ in to pomeni da gledamo ta nižji del funkcije. Torej zakaj bi hotli da je pri simpleksni metodi $C \geq 0$ zato ker če pogledamo kako bi zgledale vse ravnine ki jih pobarvamo za vsako funkcijo - vedno bi v pobarvanem delu bila vključena (0,0) - to lahko ugotovimo s tem da si predstavljamo da gradeint kaže v vsakega izmed kvadrantov in ker je $C$ večji od $0$ mora biti črta ki označuje premico vedno potisnejna v kvadrant kamor kaže gradient - pobaravmo vedno vse kar je za črto glede na gradient - to vedno vkljulčuje (0,0)*



Imamo LP v standardni obliki za sedaj z nenegativnimi koeficienti $b$


$$\begin{array}
\\
\max &c^{T}x \\
\text{p.p.} &Ax \leq b \\ 
&x \geq 0\\
&b \geq 0
\end{array}$$



Množica dopustnih rešitev je konveksni polieder in bo veljalo da se rešitev nahaja v enem izmed oglišč. 

Torej moramo najti pravo oglišče poliedra to pa delamo tako da se iz enega oglišča premikamo v drugega.

To je najlažje izvedeno s tako imenovanim **slovarjem** kjer vzamemo vse naše omejitve in izrazimo dopolnilne spremenljivke.

Iz neenakosti $Ax \leq b$ tvorimo enakosti z dodajanjem **dopolnilnih spremenljivk** $s_{i}$. Te služijo kot razlika med $b$ in $a^{T}x$.

$$a_{i,1}x_{1}+...+a_{i,n}x_{n} \leq b_{i}$$
$$a_{i,1}x_{1}+...+a_{i,n}x_{n} + s_{i} = b_{i}$$


Velja $\forall  s_{i}\geq 0$.

S tem si bomo pomagali da hodimo iz oglišča v oglišče. Najprej hočemo nekje začeti.

*Opazimo da če $\forall s_{i}$ nastavimo na 0 dobimo enačbe premic ki omejujejo naše območje. Zraven pa imamo še $x_{1}$ in $x_{2}$ ki tudi delujeta kot premici ki omejujeta območje ko velja $x_{1} = 0$ ali $x_{2} = 0$. Z nastavljanjem dveh od $\{s_{1},...,s_{n},x_{1},x_{2}\}$ na nič efektivno iščemo presek teh dveh premic - naše oglišče.*

Ob predpostavki da je $b\geq 0$ lahko nastavimo vse $x_{1},...,x_{n}$ na $0$ in dobimo da velja $s = b \Rightarrow \forall s_{i} \geq 0$ Dobimo validno oglišče v katerm lahko začnemo.

*$x_{1}$ in $x_{2}$ smo nastavili na 0 - presek teh dveh premic je v $(0,0)$. Iščemo naslednje oglišče kamor bi šli. To delamo s pomočjo $z$ kjer si izberemo spremenljivko z največjim koeficientom - recimo $x_{1}$. To pomeni da $x_{1}$ ne bo več 0. Da pridemo v najbližje oglišče pogledamo katera premica ga bo prva omejila pri njegovem gibanju - to je premica s katero bo tvorjeno novo oglišče oz. presečišče smeri premikanja - v našem primeru $x_{1}$ in premice do katere najprej pridemo v tej smeri.*

*Ko govorimo o premikanju po robovih je stvar naslednja. Ko nastavimo vse desne spremenljivke na 0 pogledamo v originalni slovar kaj nastane. Dobimo nekaj kar predstavlja presečišče premic oz. v višjih dimenzijah hiperravnin.*

*In to je v bistvu to kar delamo. Najdemo spremenljivko ki bi jo večali - nočemo da je 0. Ker vse na desni nastavljamo na nič jo damo na levo - katero damo na desno? tisto ki jo najbolj omejuje - predstavlja premico s katero se seka - oglišče - jo damo na desno da lahko s to premico dejansko delamo ker bo veljalo $0 = a_{1}x_{1}+a_{2}x_{2}$ iz česar iščemo presečišče. V naslednjih korakih ponavljamo - iščemo kaj bi večali - mora iti na levo da ne bo 0, najdemo kaj gre na desno - spremenljivka ki predstavlja najbližjo premico ki bo sekala trenutno smer potovanja - nastavimo na 0, ker je na desni - če pogledamo v prvi slovar s tem dobimo presečišče oz. novo oglišče.*

![[Pasted image 20260307120407.png]]

*Torej vstopanje in izstopanje iz baze je samo določanje katere omejitve bomo upoštevali oz. po katerih se lahko premikamo. Vse kar ni bazno gre na nič - te spremenljivke postanejo pritrjene - če pogledamo v prvi slovar to pomeni da te omejitve upoštevamo, iz česar dobimo oglišče preseka omejitev - torej če damo nebazne spremenljivke na nič in so vse te dopolnilne bo to predstavljalo omejitev $x_{1},...,x_{n}$ z enačbami hiperravnin ki jih dopolnilne spremenljivke določajo.*


***


Recimo da imamo

$$x_1 \begin{pmatrix} 1 \\ 2 \end{pmatrix} + x_2 \begin{pmatrix} 1 \\ 1 \end{pmatrix} + s_1 \begin{pmatrix} 1 \\ 0 \end{pmatrix} + s_2 \begin{pmatrix} 0 \\ 1 \end{pmatrix} = \begin{pmatrix} 10 \\ 15 \end{pmatrix}$$

Hočemo pridit do $\begin{pmatrix} 10 \\ 15 \end{pmatrix}$.

Rešitev gradimo z vektorji na desni. Ker smo v tem primeru v dvodimenzionalnem prostoru rabimo dva vektorja da dosežemo cilijnega.

Tem vektorjem ki jih izberemo pravimo baza.

Tukaj je prevod besedila v slovenščino, ki ohranja razlagalni in tehnični ton:

---

**Torej, ko izberemo bazne spremenljivke, dobesedno izbiramo, katera dva gradnika bomo uporabili, da dosežemo cilj $\begin{pmatrix} 10 \\ 15 \end{pmatrix}$.**



Ko za našo bazo izberemo $s_1$ in $s_2$:
*   "Vektor $\begin{pmatrix} 10 \\ 15 \end{pmatrix}$ bom sestavil samo z uporabo stolpcev $s_1$ in $s_2$."
*  $s_1 \begin{pmatrix} 1 \\ 0 \end{pmatrix} + s_2 \begin{pmatrix} 0 \\ 1 \end{pmatrix} = \begin{pmatrix} 10 \\ 15 \end{pmatrix}$
*   Rešitev: $s_1 = 10, s_2 = 15$.
*   Ta "baza" nas je zaklenila v točko, kjer sta $x_1=0$ in $x_2=0$.

**Kaj se zgodi, ko izvedete pivotiranje (Pivot)?**
Odločite se, da je stolpec $x_1$ $\begin{pmatrix} 1 \\ 2 \end{pmatrix}$ "boljši" gradnik kot stolpec $s_2$.
*   Zamenjate ju. Vaša nova baza je $\{s_1, x_1\}$.
*   Zdaj morate rešiti: $s_1 \begin{pmatrix} 1 \\ 0 \end{pmatrix} + x_1 \begin{pmatrix} 1 \\ 2 \end{pmatrix} = \begin{pmatrix} 10 \\ 15 \end{pmatrix}$.
*   Rešite sistem: $x_1$ postane $7.5$, $s_1$ postane $2.5$.
*   **Točka:** Ta nova baza vas je "povlekla" v novo oglišče $(7.5, 0)$.

### 3. Baza določa "perspektivo"
Razlog, zakaj se imenuje baza, je v tem, da je **vsaka spremenljivka v slovarju (dictionary) zapisana s pomočjo te baze.**

V srednješolski algebri imate standardne bazične vektorje $i = (1,0)$ in $j = (0,1)$.
V Simpleksu ob pivotiranju **spreminjate koordinatni sistem**.
*   "Nebazične" spremenljivke so vaše **nove osi**.
*   "Bazične" spremenljivke so **fiksne točke**, ki ste jih dosegli z uporabo teh osi.

### 4. Zakaj torej ime "Baza"?
To ni le modno ime. V sistemu $Ax=b$:
1.  Matrika $A$ ima $n$ stolpcev.
2.  $b$ živi v $m$-dimenzionalnem prostoru.
3.  Vsak nabor $m$ stolpcev iz matrike $A$, ki lahko "doseže" $b$, je **baza za ta $m$-dimenzionalni prostor.**

Dantzig jih je poimenoval "bazične spremenljivke", ker tvorijo **bazično matriko ($B$)**, ki se uporablja za reševanje enačbe $Bx = b$.

### Povzetek spoznanja ("Aha!" trenutek)
Rekli ste: *"Ne vidim, kako to uporabljamo, da pridemo do točke."*

Dejansko **baza JE točka.**
Če mi podate seznam, katere spremenljivke so "bazične", lahko izvedem inverzijo matrike ($B^{-1}b$) in vam natančno povem, v katerem oglišču lika stojite.
*   Če spremenite bazo, spremenite oglišče.
*   Simpleksna metoda je le način spraševanja: **"Kateri nabor $m$ stolpcev naj uporabim kot svojo bazo, da dosežem ciljni vektor $b$, medtem ko bo dobiček $Z$ čim večji?"**

To se povezuje s "pravo algebro", ker je vsak korak simpleksne metode le **ponovno zapisovanje ciljnega vektorja $b$ kot kombinacije različnih bazičnih vektorjev.**