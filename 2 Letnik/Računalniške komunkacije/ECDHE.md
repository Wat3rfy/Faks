Za podrobno razumevanje delovanja **ECDHE** moramo proces razdeliti na matematični temelj in korake izmenjave.

### 1. Matematični temelj: Eliptične krivulje
Namesto klasičnega računanja z ostanki pri deljenju (kot pri RSA), ECDHE temelji na enačbi eliptične krivulje, ki ima obliko:
$$y^2 = x^3 + ax + b$$

Glavna operacija tukaj ni navadno množenje, temveč **skalarno množenje točk na krivulji**.
*   Izberemo **bazno točko ($G$)** na krivulji, ki je javno znana.
*   Če točko $G$ "pomnožimo" s številom $k$ (torej jo $k-krat$ seštejemo s samo seboj po posebnih geometrijskih pravilih), dobimo novo točko $P$.
*   **Enosmerna funkcija:** Če poznaš $k$ in $G$, je zelo enostavno izračunati $P$. Če pa poznaš samo $P$ in $G$, je **praktično nemogoče** ugotoviti, kolikšen je bil $k$. To se imenuje *problem diskretnega logaritma na eliptičnih krivuljah*.

---

### 2. Postopek izmenjave (korak za korakom)

Predstavljajmo si odjemalca (tvoj brskalnik) in strežnik.

#### Korak 1: Dogovor o parametrih
Odjemalec in strežnik se najprej dogovorita, katero eliptično krivuljo bosta uporabila in katera je bazna točka ($G$). To se zgodi v uvodnem delu TLS komunikacije (Handshake).

#### Korak 2: Generiranje efemernih (začasnih) ključev
Obe strani si v ozadju zgenerirata svoja para ključev:

*   **Odjemalec:**
    *   Izbere naključno število **$d_A$** (to je njegov **privatni ključ**, ki ga ne pove nikomur).
    *   Izračuna **$Q_A = d_A \times G$** (to je njegov **javni ključ**, ki je točka na krivulji).
*   **Strežnik:**
    *   Izbere naključno število **$d_B$** (njegov **privatni ključ**).
    *   Izračuna **$Q_B = d_B \times G$** (njegov **javni ključ**).

#### Korak 3: Izmenjava javnih ključev
Odjemalec pošlje svoj $Q_A$ strežniku, strežnik pa pošlje svoj $Q_B$ odjemalcu.
*Prisluškovalec na kablu vidi samo $G, Q_A$ in $Q_B$, kar mu ne pomaga.*

#### Korak 4: Izračun skupne skrivnosti (Shared Secret)
Zdaj se zgodi "magija" Diffie-Hellmana. Obe strani opravita množenje:

*   **Odjemalec** vzame strežnikov javni ključ $Q_B$ in ga pomnoži s svojim privatnim ključem $d_A$:
    $$S = d_A \times Q_B$$
*   **Strežnik** vzame odjemalčev javni ključ $Q_A$ in ga pomnoži s svojim privatnim ključem $d_B$:
    $$S = d_B \times Q_A$$

Zaradi matematičnih lastnosti eliptičnih krivulj velja:
$$d_A \times (d_B \times G) = d_B \times (d_A \times G)$$
**Oba sta dobila popolnoma isto točko $S$ na krivulji!**

#### Korak 5: Izpeljava ključa za šifriranje
Točka $S$ (natančneje njena koordinata $x$) se nato uporabi kot osnova za ustvarjanje **simetričnega ključa** (npr. za algoritem AES). S tem ključem se nato šifrirajo vsi podatki, ki si jih izmenjata.

---

### 3. Zakaj je to "Ephemeral" (E) in zakaj je to pomembno?

V starejših sistemih (navaden RSA) je strežnik uporabil svoj stalni privatni ključ (tistega iz certifikata) za dešifriranje ključa seje. Če bi heker shranjeval ves promet in čez 5 let ukradel ta privatni ključ s strežnika, bi lahko dešifriral ves promet za 5 let nazaj.

Pri **ECDHE** pa sta $d_A$ in $d_B$ **začasna**:
1.  Ustvarita se samo za točno to sejo.
2.  Takoj ko je skupna skrivnost $S$ izračunana, se $d_A$ in $d_B$ **izbrišeta iz pomnilnika**.
3.  Tudi če heker kasneje vdre v strežnik in dobi vse certifikate, tam **ne bo našel ključa**, s katerim bi lahko dešifriral preteklo komunikacijo, saj so bili ključi uničeni.

To lastnost imenujemo **Perfect Forward Secrecy (PFS)**.

### Povzetek
ECDHE omogoča, da si dve osebi, ki se nikoli nista srečali, pred očmi vseh mimoidočih izmenjata informacije, na podlagi katerih si oba izračunata isto geslo, ne da bi to geslo kdaj dejansko izgovorili ali poslali. Eliptične krivulje pa poskrbijo, da je vse to matematično izjemno težko zlomiti, hkrati pa proces teče zelo hitro.