Pregledal sem priložene PDF dokumente. Gre za sklop zapiskov predavanj iz matematične analize, ki pokrivajo teorijo in prakso **večterih (dvojnih) integralov** ter uvedbo specialnih funkcij **Gama in Beta**.

Tukaj je logični vrstni red, kako si snov sledi (od definicij do aplikacij), in povzetek v obliki zapiskov.

### Logični vrstni red dokumentov

1.  **PDF 3: `Integriranje funkcij vec spremenljivk`** (Definicija, teorija, obstoj)
2.  **PDF 4: `Racunanje dvojnega integrala`** (Fubinijev izrek, računanje po območjih)
3.  **PDF 1: `Uvedba novih spremenljivk`** (Substitucija v dvojnem integralu, Jacobi)
4.  **PDF 2: `Gama in beta`** (Specialni funkciji, ki uporabljata neprave integrale in tehnike integracije)

---

### Zapiski snovi (v slovenščini)

#### 1. Del: Definicija in lastnosti dvojnega integrala (Vir: PDF 3)
Ta del postavi teoretične temelje.

*   **Definicija:**
    *   Obravnavamo funkcijo $f: [a,b] \times [c,d] \to \mathbb{R}$.
    *   Pravokotnik razdelimo na manjšo mrežo (delitev $\Delta$).
    *   Definiramo spodnjo ($s(f, \Delta)$) in zgornjo ($S(f, \Delta)$) Riemannovo vsoto.
    *   Če limita ko gre premer delitve proti 0 obstaja in je enaka za spodnjo in zgornjo vsoto, je funkcija **integrabilna**.
    *   Oznaka: $\iint_D f(x,y) \, dx \, dy$ ali $\iint_D f(x,y) \, dA$.

*   **Geometrijski pomen:**
    *   Volumen telesa pod ploskvijo, ki jo določa graf funkcije $f(x,y)$.
    *   Če je $f(x,y) = 1$, integral predstavlja **ploščino** območja $D$.

*   **Lastnosti:**
    *   **Linearnost:** $\iint (\alpha f + \beta g) = \alpha \iint f + \beta \iint g$.
    *   **Aditivnost:** Integral po uniji disjunktnih območij je vsota integralov ($D = D_1 \cup D_2 \Rightarrow \int_D = \int_{D_1} + \int_{D_2}$).
    *   **Pozitivnost:** Če je $f(x,y) \geq 0$, je integral $\geq 0$.
    *   **Izrek o povprečni vrednosti:** Za zvezno funkcijo na povezanem območju obstaja točka, kjer funkcija zavzame povprečno vrednost integrala.

#### 2. Del: Računanje dvojnega integrala (Vir: PDF 4)
Prehod iz teorije v prakso (kako dejansko izračunamo številko).

*   **Fubinijev izrek:**
    *   Dvojni integral se prevede na dva zaporedna (iterirana) enojna integrala.
    *   Za pravokotnik $[a,b] \times [c,d]$:
        $$ \iint_D f(x,y) \, dx \, dy = \int_a^b \left( \int_c^d f(x,y) \, dy \right) dx $$
*   **Integracija po splošnih območjih:**
    *   Območja niso vedno pravokotniki. Običajno so omejena s funkcijami.
    *   **Tip I (normalno na x-os):** $x \in [a,b]$ in $y \in [\varphi(x), \psi(x)]$.
        $$ \int_a^b dx \int_{\varphi(x)}^{\psi(x)} f(x,y) \, dy $$
    *   **Tip II (normalno na y-os):** $y \in [c,d]$ in $x \in [\varphi(y), \psi(y)]$.
        $$ \int_c^d dy \int_{\varphi(y)}^{\psi(y)} f(x,y) \, dx $$
*   **Primeri:** Računanje integralov po trikotniku, območju med parabolama itd.

#### 3. Del: Uvedba novih spremenljivk (Vir: PDF 1)
Analogija substitucije pri enojnem integralu, vendar za 2D.

*   **Motivacija:** Poenostavitev območja integracije ali integranda.
*   **Preslikava:** Imamo preslikavo $F: \mathcal{D}^* \to \mathcal{D}$, podano z $x=x(u,v), y=y(u,v)$. Preslikava mora biti bijektivna in zvezno odvedljiva.
*   **Jacobijeva matrika in determinanta:**
    *   Matrika parcialnih odvodov: $DF = \begin{bmatrix} \frac{\partial x}{\partial u} & \frac{\partial x}{\partial v} \\ \frac{\partial y}{\partial u} & \frac{\partial y}{\partial v} \end{bmatrix}$.
    *   Jacobijeva determinanta (Jacobian): $J = \det(DF)$.
*   **Formula za novo spremenljivko:**
    $$ \iint_D f(x,y) \, dx \, dy = \iint_{\mathcal{D}^*} f(x(u,v), y(u,v)) \cdot |J(u,v)| \, du \, dv $$
*   *Opomba:* Faktor $|J|$ (absolutna vrednost determinante) pove, kako se lokalno spremeni ploščina pri preslikavi. Dokument omenja povezavo z Greenovo formulo za dokazovanje.

#### 4. Del: Funkciji Gama in Beta (Vir: PDF 2)
To so Eulerjevi integrali, ki so pomembni v analizi in statistiki.

*   **Funkcija Gama ($\Gamma$):**
    *   Definicija: $\Gamma(x) = \int_0^\infty t^{x-1} e^{-t} \, dt$ za $x > 0$.
    *   Osnovna lastnost (rekurzija): $\Gamma(x+1) = x \Gamma(x)$.
    *   Povezava s fakulteto: Za naravna števila velja $\Gamma(n+1) = n!$.
    *   Posebna vrednost: $\Gamma(1/2) = \sqrt{\pi}$. (Dokazano s pomočjo Gaussovega integrala in kvadriranjem integrala, kar vodi v dvojni integral in polarne koordinate).

*   **Funkcija Beta ($B$):**
    *   Definicija: $B(p,q) = \int_0^1 t^{p-1} (1-t)^{q-1} \, dt$ za $p, q > 0$.
    *   Simetrija: $B(p,q) = B(q,p)$.
    *   **Povezava z Gamo:**
        $$ B(p,q) = \frac{\Gamma(p)\Gamma(q)}{\Gamma(p+q)} $$