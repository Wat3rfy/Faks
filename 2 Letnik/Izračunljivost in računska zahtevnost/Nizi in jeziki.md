

Definiramo **abecedo** kot katero koli neprazno končno množico.
Elementom abecede pravimo **simboli** abecede.
Za označevanje abeced običajno uporabljamo velike grške črke $\Sigma$ in $\Gamma$ ter pisavo tipkovnice (typewriter font) za simbole iz abecede.

Nekaj primerov abeced.

$$\Sigma_1 = \{0, 1\}$$
$$\Sigma_2 = \{a, b, c, d, e, f, g, h, i, j, k, l, m, n, o, p, q, r, s, t, u, v, w, x, y, z\}$$
$$\Gamma = \{0, 1, x, y, z\}$$

**Niz nad abecedo** je končno zaporedje simbolov iz te abecede, običajno zapisanih drug poleg drugega in brez vejic.

Če je $\Sigma_1 = \{0, 1\}$, je $01001$ niz nad $\Sigma_1$.
Če je $\Sigma_2 = \{a, b, c, \ldots, z\}$, je $abracadabra$ niz nad $\Sigma_2$.

Če je $w$ niz nad $\Sigma$, je **dolžina** niza $w$, zapisana $|w|$, število simbolov, ki jih vsebuje.

Niz z dolžino nič se imenuje **prazni niz** in se zapiše $\epsilon$. 

Če ima $w$ dolžino $n$, lahko zapišemo $w = w_1 w_2 \ldots w_n$, kjer je vsak $w_i \in \Sigma$.

**Obrat** niza $w$, zapisan $w^R$, je niz, dobljen z zapisom $w$ v obratnem vrstnem redu (tj. $w_n w_{n-1} \ldots w_1$).

Niz $z$ je **podniz** niza $w$, če se $z$ pojavi zaporedoma znotraj $w$. Na primer, $cad$ je podniz niza $abracadabra$. 

Pomembno je ločiti podniz od *podzaporedja*, kjer simbolom ni treba biti zaporednim, ampak le ohraniti vrstni red. Torej $aaa$ bi bilo podzaporedje $abracadabra$.

Če imamo niz $x$ dolžine $m$ in niz $y$ dolžine $n$, je **konkatenacija** $x$ in $y$, zapisana $xy$, niz, dobljen z dodajanjem $y$ na konec $x$, kot v $x_1 \ldots x_m y_1 \ldots y_n$. Konkatenacija je asociativna ($(xy)z = x(yz)$), vendar ni komutativna ($xy \neq yx$).
Za konkatenacijo niza samega s seboj večkrat uporabljamo nadpisno notacijo $x^k$, ki pomeni

$$ \underbrace{xx \cdots x}_{k} $$

Prazni niz je **identitetni element** za operacijo konkatenacije: za vsak niz $w$ velja $w\epsilon = \epsilon w = w$. 
Poleg tega velja $w^0 = \epsilon$.

Leksikografski vrstni red nizov je enak znanemu vrstnemu redu slovarja.
Občasno bomo uporabili spremenjen leksikografski vrstni red, imenovan **shortlex vrstni red** ali preprosto **vrstni red nizov**, ki je enak leksikografskemu, razen da krajši nizi vedno predhodijo daljšim. Tako je vrstni red vseh nizov nad abecedo $\{0, 1\}$:

$$(\epsilon, 0, 1, 00, 01, 10, 11, 000, \ldots).$$

Rečemo, da je niz $x$ **predpona** niza $y$, če obstaja niz $z$, za katerega velja $xz = y$, in da je $x$ **prava predpona** niza $y$, če poleg tega velja $x \neq y$. Podobno je niz $x$ **sufiks** niza $y$, če obstaja niz $z$, za katerega velja $zx = y$.

Prazni niz je predpona, in originalni niz je vedno svoja predpona.

Preden definiramo jezik, si poglejmo nekaj pomembnih množic nizov. 

Množica vseh nizov nad $\Sigma$ z dolžino natanko $k$ je označena s $\boldsymbol{\Sigma^k}$. 

Množica vseh možnih nizov (katerekoli končne dolžine) nad abecedo $\Sigma$ se imenuje **Kleenejevo zaprtje** ali **Kleenejeva zvezda** in se zapiše $\Sigma^* = \Sigma^0 \cup \Sigma^1 \cup \Sigma^2 \cup \dots$.

Množica vseh nepraznih nizov pa se imenuje **Kleenejev plus**, $\boldsymbol{\Sigma^+} = \Sigma^1 \cup \Sigma^2 \cup \dots$.

**Jezik** je množica nizov. Ker je jezik množica, vrstni red nizov v njem ni pomemben in ne vsebuje duplikatov. Vsak jezik $L$ nad abecedo $\Sigma$ je podmnožica $\Sigma^*$, torej $L \subseteq \Sigma^*$. Jezik je lahko končen ali neskončen. Jezik je **brez predpon** (*prefix-free*), če noben član ni prava predpona drugega člana.

Prazni niz ($\epsilon$) $\neq$ Prazni jezik ($\emptyset$ ali $\{\}$) $\neq$ Jezik, ki vsebuje samo prazni niz ($\{\epsilon\}$)

$\epsilon$: To je **niz** dolžine $0$. Je konkreten objekt.

$\emptyset$: To je **jezik** (množica), ki ne vsebuje **nobenega** niza. Njegova moč (kardinalnost) je $0$.

$\{\epsilon\}$: To je **jezik** (množica), ki vsebuje natanko **en niz**: prazni niz. Njegova moč je $1$.

Za jezike poznamo tudi operacije:

Če sta $L_1$ in $L_2$ jezika nad abecedo $\Sigma$:

1.  **Unija (Union):**
    $L_1 \cup L_2 = \{ w \mid w \in L_1 \text{ ali } w \in L_2 \}$
    To je standardna unija množic.

2.  **Konkatenacija (Concatenation):**
    $L_1 L_2 = \{ xy \mid x \in L_1 \text{ in } y \in L_2 \}$
    To je jezik, ki vsebuje vse nize, nastale s stikanjem niza iz $L_1$ z nizom iz $L_2$
    *Primer:* Če je $L_1 = \{a, b\}$ in $L_2 = \{0, 1\}$, potem je $L_1 L_2 = \{a0, a1, b0, b1\}$.

3.  **Potenca jezika (Power):**
    $L^k = \underbrace{L L \cdots L}_{k}$ (k-kratna konkatenacija jezika samega s seboj).
    Definiramo tudi dva posebna primera:
    *   $L^0 = \{\epsilon\}$ (To velja za **vsak** jezik $L$, tudi za praznega!)
    *   $L^1 = L$

4.  **Kleenejeva zvezda (Kleene Star):**
    $L^* = L^0 \cup L^1 \cup L^2 \cup \dots = \bigcup_{k \ge 0} L^k$
    To je jezik, ki vsebuje vse možne nize, nastale s konkatenacijo nič ali več nizov iz jezika $L$.

5.  **Kleenejev plus (Kleene Plus):**
    $L^+ = L^1 \cup L^2 \cup L^3 \cup \dots = \bigcup_{k \ge 1} L^k$
    Enako kot zvezda, le da izključuje prazni niz (razen če ga $L$ že vsebuje na drug način). Velja tudi $L^+ = L L^*$.

6.  **Obrat jezika (Reversal):**
    $L^R = \{ w^R \mid w \in L \}$
    Jezik, ki vsebuje obrate vseh nizov iz $L$.

<br>

1.  **Vloga $\emptyset$ in $\{\epsilon\}$ v operacijah (NAJPOMEMBNEJE!):**
    To je daleč najpogostejši vir napak.
    *   **Identiteta za konkatenacijo:** Jezik $\{\epsilon\}$ je identitetni element za konkatenacijo jezikov, ne pa $\emptyset$.
        *   $L \cdot \{\epsilon\} = \{\epsilon\} \cdot L = L$
    *   **Ničelni element za konkatenacijo:** Prazni jezik $\emptyset$ deluje kot "uničevalec" pri konkatenaciji. Če stakneš karkoli s "ničemer", dobiš "nič".
        *   $L \cdot \emptyset = \emptyset \cdot L = \emptyset$
        *   **Finta:** Vprašanje "Ali velja $L_1 L_2 = L_2 L_1$?" Odgovor je ne, ker konkatenacija ni komutativna. Ampak kaj, če je $L_1 = \emptyset$? Potem velja, ker je $\emptyset L_2 = L_2 \emptyset = \emptyset$.

2.  **Kleenejeva zvezda nad praznim jezikom:**
    To je klasično trik vprašanje.
    *   Kaj je $\emptyset^*$?
    *   Po definiciji je $\emptyset^* = \emptyset^0 \cup \emptyset^1 \cup \emptyset^2 \cup \dots$.
    *   $\emptyset^0$ je po definiciji **vedno** $\{\epsilon\}$.
    *   $\emptyset^1 = \emptyset$, $\emptyset^2 = \emptyset \cdot \emptyset = \emptyset$, itd.
    *   Torej: $\emptyset^* = \{\epsilon\} \cup \emptyset \cup \emptyset \cup \dots = \{\epsilon\}$.
    *   **Zapomnite si: $\emptyset^* = \{\epsilon\}$**. Intuitivno: edini način, da iz prazne množice nizov izberemo "nič ali več" nizov in jih staknemo, je, da jih izberemo natanko nič, kar nam da prazni niz $\epsilon$.

3.  **Kleenejeva zvezda nad jezikom $\{\epsilon\}$:**
    *   Kaj je $\{\epsilon\}^*$?
    *   $\{\epsilon\}^0 = \{\epsilon\}$
    *   $\{\epsilon\}^1 = \{\epsilon\}$
    *   $\{\epsilon\}^2 = \{\epsilon\}\{\epsilon\} = \{\epsilon\epsilon\} = \{\epsilon\}$
    *   Torej: $\{\epsilon\}^* = \{\epsilon\} \cup \{\epsilon\} \cup \dots = \{\epsilon\}$.

4.  **Predpona vs. Prava predpona:**
    *   Vaša definicija je točna. Pazite pri vprašanjih tipa: "Ali je niz $w$ predpona niza $w$?" **Da.** "Ali je niz $w$ *prava* predpona niza $w$?" **Ne.**
    *   To je pomembno pri definiciji **jezika brez predpon (prefix-free language)**, ki ste jo pravilno navedli: noben niz v jeziku ni *prava* predpona drugega niza. To pomeni, da če je $w$ v jeziku, noben $wz$ (kjer $z \neq \epsilon$) ne sme biti v jeziku.

5.  **Moč (kardinalnost) jezika vs. Dolžina niza:**
    *   Oba se včasih označujeta z $|...|$. Bodite pozorni na kontekst.
    *   $|w|$ je **dolžina niza** (število simbolov). Primer: $|\text{abac}| = 4$.
    *   $|L|$ je **moč jezika** (število nizov v jeziku). Primer: $|\{a, b, ab\}| = 3$.
    *   Jezik je lahko neskončen ($|\Sigma^*| = \infty$), čeprav so vsi nizi v njem končne dolžine.

6.  **Razlika med $\Sigma$ in $\Sigma^1$:**
    *   $\Sigma$ je **abeceda** (množica simbolov). Primer: $\{0, 1\}$.
    *   $\Sigma^1$ je **jezik** (množica nizov dolžine 1). Primer: $\{0, 1\}$.
    *   Tehnično gledano sta to različna objekta (množica simbolov vs. množica nizov), čeprav sta v praksi izomorfna in se pogosto uporabljata izmenično. Dobro se je zavedati te subtilne razlike.

