
# Predznačena števila

Binarni zapis z $n$ nam omogoča zapis $2^{n}$ števil, kjer je množica števil $\{ 0, ..., 2^{n}-1\}$, omejena z $2^{n}-1$, ker štejemo še ničlo.
- 4 biti - $\{ 0, ..., 15\}$
- 8 bitov - $\{ 0, ..., 255\}$
- 12 bitov - $\{ 0, ..., 4095\}$
- 16 bitov - $\{ 0, ..., 65535\}$

Zapis ima kot števke potence 2 od $\{ 0,...,n-1\}$ torej $2^{0},..., 2^{n-1}$

1 bajt je 8 bitov.

Celo število so 4 bajti, kar je 32 bitov. (V heksadecimalnem lahko zapišemo z 8 števkami kar je natanko naslov v 32 bitnem pomnilniku.)

- 5 bitov - $\{ 0, ..., 31\}$
- 6 bitov - $\{ 0, ..., 63\}$
- 7 bitov - $\{ 0, ..., 127\}$
- 9 bitov - $\{ 0, ..., 511\}$
- 10 bitov - $\{ 0, ..., 1023\}$
- 11 bitov - $\{ 0, ..., 2047\}$


## Zapis z odmikom

Zapis z odmikom je zapis pri katerem številu zapisnim binarno odštejemo nek konstanten odmik.

Če imamo zapis z $n$ biti je odmik najpogostejej $2^{n-1}$.

Torej recimo zapis s 4 biti omogoča zapis $\{ 0, ..., 15\}$ ko pa vzamemo odmik za 8 oz. $2^{3}$ pa dobimo zapis od $\{ -8, ..., 7\}$ oz. od $\{ -2^{n-1},...,2^{n-1}-1\}$, drugače pa je lahko odmik poljuben - $\{ -\text{odmik},..., 2^{n}-1 - \text{odmik}\}$

## Predznačen zapis

Predznačen zapis je zapis števila  kjer most important bit določa predznak števila, 0 je pozitivno, 1 je negativno število. Tako iz $2^{n}$ pozitivnih števil $\{ 0,...,2^{n}-1\}$, dobimo števila od
$\{ -2^{n-1}+1 ,...,0,0,...,2^{n-1}-1 \}$, kjer se podvojijo ničle.

## Eniški komplement

Eniški komplement je zapis, kjer dobimo nasprotno število z inverzom originalnega. Posledica je da most important bit predstavlja predznak števila hkrati pa je podvojena tudi ničla (0000 : 1111).

To nam z $n$ biti da zapis od $\{ -2^{n-1}+1 ,...,0,0,...,2^{n-1}-1\}$.

## Dvojiški komplement

Dvojiški komplement je zapis, kjer dobimo nasprotno število z inverzom originalnega nato pa prištejemo 1. Še vedno velja pravilo da če je 1 na prvem mestu imamo negativno število, drugače pozitivno, s tem postopkom pa dobimo množico vrednosti

$$\{2^{n-1},...,0, ..., 2^{n-1}-1 \}$$

Glavne značilnosti so da je $10...0$ število ki nima inverza in je v resnici naše $2^{n-1}$ število, če poskusimo narediti inverz dobimo isto število. 

Nič je zapisana z $0 ... 0$, $-1$ je zapisana kot $1 ... 1$, najmanjše možno število pa je $10 ...$

Zapis z dvojiškim komplementom je v resnici odštevanje $2^{n-1}$ če je predznačeno.

# IEEE 754

Standard za zapis s plavajočo vejico IEEE 754 poznamo v enojni in dvojni natančnosti.

Enojna natančnost ima 32 bitov za eno število, MIB je namenjen predznaku, naslednjih 8 je namenjenih eksponentu, ostalih 23 pa številu.

Enojna natačnost (32 bitov):
```
| SG |  EXP  |  MNTS  |
| 31 | 30:23 |  22:0  |
|  1 |   8   |   23   |
```

Če je število pozitivno je SG 0, če je negativno je 1.

Eksponent je predstavljen v zapisu z odmikom 127.

Mantisa je decimalni del števila, kjer je 1 implicirana $\Rightarrow$ $1.\text{(MNTS)}$.

Če sta mantisa in eksponent 0 potem imamo pozitivno ali negativno ničlo glede na `SG`.
Če imamo mantiso 0 in eksponent 255 potem imamo pozitivno ali negativno neskončnost glede na `SG`.
Če imamo eksponent v $\{ 1,...,254\}$ in poljubno mantiso imamo implicitno normalno obliko.
Če imamo eksponent 0 in poljubno mantiso imamo ulomkovo obliko oz. nenormalna.
Če imamo eksponent 255 in poljubno mantiso imamo NaN.

Implicitna normalna oblika:

$$(-1)^{\text{S}} \times 1.M \times 2^{E-127}$$

Ulomkova oblika oz. nenormalna

$$(-1)^{\text{S}} \times 0.M \times 2^{-126}$$

Števila se zaokrožujejo k najbližjemu pe predstavljivemu številu, če pa sta 2 enako blizu, pa k sodemu.

# RISCV in RV32I

**RV** - RISCV
**32** - 32 bit
**I** - integer

**Beseda** je enota podatkov, ki jih procesor najbolj efektivno obdela.

**RV32I instruction set architecture** je računalniška arhitektura katere glavne lastnosti so 32 bitna velikost **besede** oz. velikost registrov s katerimi dela. Vsak register lahko shrani 32 bitno vrednost ali 32 bitni pomnilniški naslov.

Naslovi v pomnilniku so 32 bitni in kažejo na $2^{32}$ enoličnih mest. (4 GB) (Lahko dostopa do 4GB pomnilnika z uporabo 32 bitnih naslovov.)

Integer namiguje na to da načeloma dela s celimi števili, to vključuje seštevanje, odštevanje, množenje. logične in shift operacije ter primerjave, inštrukcije delujejo na celih številih.

V glavnem ne vključuje izvorne implementacije floatint point aritmetike.


V pomnilniku vsak naslov kaže na 1 bajt podatkov, to je osnovna velikost besede pomnilnika.

Naslove uporabljamo da naložimo podatke iz pomnilnika in jih pišemo nazaj. V pomnilniku imamo naslove, inštrukcije, operande,...

Pomnilnik je lahko besedno-naslovljiv ali bajt-naslovljiv. Mi delamo z bajt-naslovljimi kar pomeni da vsak naslov kaže na 1 bajt podatkov.

V RV32I arhitekturi imamo 32 registrov vsak velik 32 bitov. `x0` je vedno 0 in pisanje vanj ne spreminja njegove vrednosti.
Standard je da je `x1` return add in `x2` stack pointer.

Vsi ukazi v RV32I so 32 bitov dolgi in morajo biti poravnana na 4 bajtno razdelitev pomnilnika.
<span></span>
***
**R-type** - register-register, se uporablja za aritmetične in logične operacije med dvema registroma in shranjuje v ciljni register.

`| funct7 | rs2 | rs1 | funct3 | rd | opcode |`

`add, sub, sll, slt, sltu, xor, srl, sra, or, and`

ALU (aritmetično-logična enota) izvaja operacijo med vsebino registrov rs1 in rs2. Rezultat se zapiše v register rd.
<span></span>
***

**I-type** - immediate, se uporablja za operacije med registrom in 12 bitnim immediatom.

`| imm[11:0] | rs1 | funct3 | rd | opcode |`

`addi, slti, sltiu, xori, ori, andi, slli, srli, srai   (za OP-IMM)`
`lb, lh, lw, lbu, lhu  (za LOAD)`
`jalr`

**Aritmetično/logično:** ALU izvaja operacijo med vsebino rs1 in 12-bitnim immediatom (razširjenim predznakom). Rezultat gre v rd.

**Load:** Pomnilniški naslov se izračuna kot rs1 + 12-bitni immediate (razširjen predznakom). Podatki iz tega naslova se naložijo v register rd. Velikost naloženih podatkov (byte, half-word, word) je določena s funct3.
<span></span>
***

**S-type** - store, se uporablja za shranjevanje iz registra na naslov v pomnilniku ki je shranjen v registru in 12 bitnem 

`| imm[11:5] | rs2 | rs1 | funct3 | imm[4:0] | opcode |`

`sb, sh, sw`

Pomnilniški naslov se izračuna kot rs1 + sign-extended 12-bitni immediate. Vsebina registra rs2 se shrani na ta pomnilniški naslov. Velikost shranjenih podatkov je določena s funct3.
<span></span>
***

**U-type** - upper immideiate, se uporablja za nalaganje 20-bitne takojšnje vrednosti v zgornjihz 20 bitov registra. 

`| imm[31:12] | rd | opcode |`

`lui, auipc`

`lui rd, imm`: Vrednost imm (20 bitov) se postavi v bite 31 do 12 registra rd. Biti 11 do 0 registra rd se nastavijo na 0. Uporablja se za nalaganje konstant, ki imajo zgornjih 20 bitov nepravih. Za celotno 32-bitno konstanto se običajno lui kombinira z addi

`auipc rd, imm`: Vrednost imm (20 bitov) se razširi predznakom in pomakne **levo za 12 mest**. Ta vrednost se nato sešteje s trenutno vrednostjo Programskega Števca (PC). Rezultat se shrani v register rd. Uporablja se za izračun naslovov, ki so oddaljeni od trenutne lokacije izvajanja, kar je ključno za PC-relativno kodo (pozicijsko neodvisno kodo).
<span></span>
***
**B-type** - branch, se uporablja za pogojne skoke uporablja pa 13 bitn imm vrednost

`| imm[12] | imm[10:5] | rs2 | rs1 | funct3 | imm[4:1] | imm[11] | opcode |`

`imm[0]` je dodan implicitno, torej je odmik vedno vsaj 2-bajtno poravnan.

Vsebina registrov rs1 in rs2 se primerjata glede na pogoj, določen s funct3. Če je pogoj izpolnjen, se novi PC izračuna kot trenutni PC + sign-extended 13-bitni odmik (implicitno pomaknjen za 1, ker je odmik v bajtih, skok pa na naslove ukazov).

Namesto imm lahko uporabimo ime odseka programa ki se scompila v pravilni odmik.
<span></span>
***
**J-type** - jump, se uporablja za nepogojne skoke z 20-bitnim takojšnjim offsetom relativno na PC in shranjevanje return addressa v ciljni register

`| imm[20] | imm[10:1] | imm[11] | imm[19:12] | rd | opcode |`

`jal` 
*jalr je I-type*

Spet je `imm[0]` impliciran bit in je 1 kar pomeni da je odmik vsaj 2-bajtno poravnan.

 Izračuna se ciljni naslov skoka kot trenutni PC + sign-extended 21-bitni odmik (implicitno pomaknjen levo za 1). Naslov ukaza, ki bi se izvedel, če ne bi bilo skoka (PC + 4), se shrani v register rd. Nato se PC nastavi na izračunani ciljni naslov skoka.

Pri interpratciji se odmik deli z 2, in napiše v strojno kodo, zato da se ohranja pravilni odmik ter način kodiranja z implicitno ničlo, tukaj lahko naletimo na missalignment izjeme.
<span></span>
***

`jalr rd imm12(rs1)` skače na naslov podan v registru z odmikom imm12. Sešteje vrednost v rs1 in SE imm12 nato pa LIB nastavi na 0 za 2-bajtno poravnanost.
`ciljni naslov = (rs1 + SE imm) \land \neg 1`
Preden skoči še shrani `PC + 4` v `rd`.


>[!|hide]- Interpretacija pseudo-ukaza `la` - load address:
>
>Da, natančno tako deluje v standardnem procesu prevajanja in povezovanja (assembling and linking) za RISC-V (in večino drugih arhitektur z omejitvami na immediate vrednosti).
>
>Poglejmo si vloge posameznih orodij:
>
>1.  **Assembler (Pretvornik iz Asemblerske kode v Objektno kodo):**
>    *   Assembler bere vašo asemblersko kodo (`.s` datoteke).
>    *   Naleti na pseudo-ukaz `la rd, labela`.
>    *   Assembler sam *ne ve nujno* končnega absolutnega naslova `labela` ali končnega naslova, kjer bo ta `auipc` ukaz končal v končnem programu. To izve šele pozneje, ko linker združi vse dele programa.
>    *   Vendar pa assembler ve, da `la` potrebuje **PC-relativen odmik**. Ve tudi, da se bo `la` razširil v sekvenco `auipc` in `addi`. Ve, da bo `addi` sledil takoj za `auipc`, torej bo naslov `addi` ukaza `PC_auipc + 4` (če sta 32-bitna ukaza).
>    *   Assembler **zapiše v objektno datoteko informacijo** (relokacijski zapis - relocation entry), ki pove linkerju: "Tukaj (na lokaciji tega `auipc`/`addi` para) je ukaz `la` za labelo `labela`. Linker, ko boš ugotovil končne naslove, prosim izračunaj pravilne immediate vrednosti za ta `auipc` in `addi` in jih zapiši v strojno kodo." Assembler pogosto v tej fazi pusti nekakšne "prazne prostore" ali začasne vrednosti za immediate polja.
>
>2.  **Linker (Povezovalnik):**
>*   Linker vzame eno ali več objektnih datotek (iz assembliranja), knjižnice in skript povezovalnika.
>*   Njegova ključna naloga je **določiti končne absolutne naslove** za vse sekcije (koda, podatki itd.) in **simbole/labele** znotraj teh sekcij v končni izvršni datoteki.
>*   Linker prebere relokacijske zapise iz objektne datoteke. Ko naleti na relokacijski zapis za `la rd, labela`, ki se nanaša na določen par `auipc`/`addi` ukazov na končnem naslovu `PC_auipc` (v končni izvršni datoteki), in ko je določil končni naslov `TargetAddr` za `labela`, takrat **izvede izračun**:
>*   Izračuna natančen bajtni odmik: `ExactOffset = TargetAddr - PC_auipc`.
>*   Izračuna `upper_imm` in `lower_imm` iz `ExactOffset` (upoštevajoč pravilo delitve z 0x800 za pravilno zaokroževanje).
>*   Te izračunane `upper_imm` in `lower_imm` vrednosti nato **zapiše neposredno v immediate polja** `auipc` in `addi` ukazov v končni strojni kodi.
>
>1.  **CPU (Procesor) - Med izvajanjem:**
>*   Ko CPU naleti na `auipc rd, upper_imm`, prebere `upper_imm` *neposredno iz ukaza* (to je vrednost, ki jo je vanj zapisal linker). Izvede izračun `PC_trenutni_auipc + (upper_imm << 12)` in rezultat shrani v `rd`.
>*   Ko CPU naleti na `addi rd, rd, lower_imm`, prebere `lower_imm` *neposredno iz ukaza* (to je vrednost, ki jo je vanj zapisal linker). Izvede izračun `rd_trenutni + sign-extended lower_imm` in shrani rezultat nazaj v `rd`.
>*   CPU **nima pojma** o labelah, pseudo-ukazih, assemblerjih ali linkerjih. Zanj sta to samo dva ločena ukaza (`auipc` in `addi`) z določenimi registrskimi operandi in določenimi immediate vrednostmi.
>
**Povzetek:**
>
Izračun pravilnih immediate vrednosti za `auipc` in `addi` se **ne** dogaja med izvajanjem programa na CPU-ju. Ta izračun se izvede **preden se program zažene**, v fazi **povezovanja (linking)**. Linker ve, kje bo v končnem programu posamezen ukaz (`auipc`) in kje bo posamezna labela (`labela`), zato lahko izračuna natančen odmik in te podatke zakodira neposredno v ukaze.
>
To zagotavlja, da bo končni rezultat izvajanja sekvence `auipc`/`addi` (med izvajanjem na CPU) natanko absolutni naslov želene labele, tudi če se celoten program prestavi v pomnilniku (zaradi PC-relativne narave `auipc`).


>[!|hide]-  Sistemski ukazi
>
`FENCE` - pomnilniška pregrada, pred pomnolniškim dostopom naj se končajo vsi morebitni prejšnji dostopi
`FENCE.I` - pregrada za ukaze, naj se pred branjem ukaza izvedejo vsa morebitna prejšnja pisanja
`ECALL` - sistemski klici, usluge od jedra OS, dostop do hardwara (pomnilnik, disk, terminal) - *environment call*
So še drugi ampak se mi trenuno ne zdijo pomembni


# Načini naslavljanja operandov

Takojšnje naslavljanje
Vrednost operanda je prisotna v ukazu samem. Ta vrednost se obravnava kot konstantna ali literal.
`load r1, 155` na primer naloži 155 v register `r1` ta način je uopraben za neposredno nalaganje konstant v registre ali pomnilnik.


Neposredno naslavljanje
Ukaz vsebuje neposredni pomnilniški naslov operanda. Na primer `load r1 (12538)` bi naložil vsebino iz naslova 12538 v register r1. Če je naslov naslov registra potem je to registrsko naslavljanje, če pa je naslov v pomnilniku je to neposredno pomnilniško naslavljanje. 
Nepos. pomn. nasl. ima svoje slabosti saj z večanjem pomnilnika večamo zahtevano polje za naslov vukazu, kar vodi do daljših ukazov in ni primerno za operande katrih naslov se spremnija.

Posredno naslavljanje
Ukaz določa lokacijo pomn. naslova ali register, ki vsebuje **naslov operanda**, namesto vrednosti operanda ali neposrednega naslova.
**Pomnilniško neposredno naslavljanje** pomeni da ukaz vsebuje pomnilniški naslov recimo `A`. Dejanski operand pa je vrednost shranjena na `A`.
**Registrsko posredno naslavljanje** pomeni da ukaz določa register ki vsebuje pomnilniški naslov operanda, kar je pogosto najučinkovitejši način.

Za **relativno naslavljanje** je registrsko posredno naslavljanje pogosto združeno z odmikom oz. offsetom, kar je najpogostejša oblika naslavljanja.

Ločimo med baznim in indeksnim naslavljanjem, kjer je bazno naslavljanje z odmikom kar že poznamo, indeksno pa uporavlja še indeksni register, ki je konfiguriran tako da je povečan oz. pomanjšan tako da dostopamo do zaporednih vrednosti strukture podatkov. Velikost prestopa je določena z velikostjo podatkov ki jih beremo.
Imamo pre-increment in sub-increment naslavljanje kjer pri enem dostopamo do elementa in nato povečamo naslov pri enem pa naprej povečamo naslov in nato dostopamo do elementa.

**Pozicijsko neodvisno naslavljanje** temelji na temu da program ne vsebuje absolutnih naslovov in ga lahko premaknemo v drug del pomnilnika.

**PC-relativno naslavljanje** temelji na programskem števcu kot bazni register kateremu prištevamo in odštevamo odmik.

# Operacije

**Operacije prenosa podatkov:** Ti ukazi premikajo podatke med različnimi lokacijami, ne da bi pri tem spremenili same podatke (gre v bistvu za kopiranje). 
npr. LOAD (kopiranje iz pomnilnika v register), STORE (kopiranje iz registra v pomnilnik). Ukaze, kot sta CLEAR in SET, lahko štejemo za prenos podatkov, saj naložijo specifične vrednosti (0 ali 1).

**Aritmetične operacije** vključujejo osnovne štiri (ADD, SUB, MUL, DIV), pa tudi negacijo, absolutno vrednost, inkrementiranje in dekrementiranje. Arhitekture pogosto ponujajo različne ukaze za isto operacijo za obravnavo različnih dolžin operandov (npr. seštevanje 8-bitnih celih števil v primerjavi z 32-bitnimi celimi števili). (aritmetično-logična enota).
**Logične operacije** vključujejo bitne operacije, kot so AND, OR, NOT, XOR, ter različne operacije premika (SHIFT) in rotacije (ROTATE).

Te operacije primarno obravnava ALU 

**Kontrolne operacije:** Ti ukazi spreminjajo zaporedni tok izvajanja programa.

- **Pogojni skoki:** Ti povzročijo skok na drug naslov ukaza _samo če_ je izpolnjen določen pogoj. Pogoji se lahko določijo na več načinov:
    - S preverjanjem **pogojnih bitov** (znanih tudi kot zastavice) v statusnem registru, ki jih nastavijo prejšnje operacije (npr. zastavica ničle Z, zastavica negativne vrednosti N, zastavica prenosa C, zastavica preliva V). Ukaz BEQ (Branch if Equal - skok, če je enako) bi lahko skočil, če je zastavica Z nastavljena (kar pomeni, da je bil rezultat prejšnje operacije nič).
    - S preverjanjem vsebine **pogojnega registra** (npr. skok, če določen register vsebuje vrednost 0).
    - Z uporabo enega samega ukaza **Primerjaj in skoči** (Compare and Branch), ki v enem koraku izvede primerjavo in skoči glede na rezultat.
- **Nepogojni skoki:** Ti vedno prenesejo izvajanje na nov naslov ukaza (JMP, BR).
- **Klici in povratki iz procedur:** Pri klicu podprograma ali funkcije je treba shraniti povratni naslov trenutnega programa, da se lahko izvajanje po končanem podprogramu pravilno nadaljuje. Ukazi, kot sta CALL ali JSR (Jump to Subroutine - skok na podprogram), obravnavajo to shranjevanje (pogosto potisnejo PC na sklad). Ukaz RET (Return - vrni se) pridobi shranjeni naslov in prenese izvajanje nazaj.

>[!|hide]- Operacije s plavajočo vejico
 Te obravnavajo operacije na realnih številih, predstavljenih v formatu plavajoče vejice. Pogosto jih izvaja posebna enota, FPU (enota za plavajočo vejico), ločena od glavne ALU. Poleg osnovne aritmetike lahko vključujejo transcendentalne funkcije, kot so kvadratni koren, logaritmi, eksponentne in trigonometrične funkcije.


>[!|hide]- Sistemske operacije
Ti ukazi upravljajo stanje sistema, potencialno vplivajo na upravljanje pomnilnika, ravni zaščite ali preklapljanje med načini delovanja. Pogosto so to **privilegirani ukazi**, kar pomeni, da jih lahko izvaja samo jedro operacijskega sistema, da prepreči uporabniškim programom povzročanje škode ali dostop do zaščitenih virov.

>[!|hide]- V/I operacije
 Te obravnavajo komunikacijo z vhodno/izhodnimi napravami. Nekatere arhitekture imajo namenske V/I ukaze; druge uporabljajo pomnilniško preslikan V/I, kjer se registri naprav obravnavajo kot specifične pomnilniške lokacije, kar omogoča uporabo standardnih ukazov za prenos podatkov (LOAD, STORE) za V/I. Prenosi podatkov se lahko odvijajo med glavnim pomnilnikom (GP) in V/I napravo ali neposredno med CPU registrom in V/I napravo.
 
>[!|hide]- Skalarne in vektorske inštrukcije
>- **Skalarne instrukcije:** Delujejo na posameznih podatkovnih elementih (npr. seštevanje dveh števil). Večina ukazov v procesorjih splošne namembnosti je skalarnih.
>- **Vektorske instrukcije:** Delujejo na več podatkovnih elementih hkrati z enim samim ukazom (npr. seštevanje vseh elementov dveh polj). Te se običajno nahajajo v vektorskih procesorjih ali grafičnih procesnih enotah (GPU) in se uporabljajo v visokozmogljivem računalništvu, zlasti na superračunalnikih.

>[!|hide]- Tipi operandov
Pogosti tipi operandov vključujejo:
>
>- **Bit:** Posamezna binarna števka (0 ali 1). Čeprav se neposredno ne obravnava pogosto v višjenivojskih jezikih, so bitne operacije ključne za sistemske naloge in nadzor.
>- **Znak:** Običajno 8-bitna vrednost, ki predstavlja znak (npr. z uporabo kodiranja ASCII). Zaporedje znakov tvori **niz**.
>- **Celo število:** Cela števila, ki so lahko s predznakom (pozitivna ali negativna) ali brez predznaka (nenegativna). Pogoste dolžine so 8, 16, 32 in 64 bitov, kar ustreza bajtom, polbesedam, besedam in dvojnim besedam na mnogih arhitekturah.
>- **Realno število (plavajoča vejica):** Števila z decimalnimi deli, običajno predstavljena z uporabo standardov, kot je IEEE 754. Pogoste natančnosti vključujejo enojno natančnost (32 bitov) in dvojno natančnost (64 bitov), obstajajo pa tudi 128-bitni formati za večjo natančnost.
>- **Decimalno število:** Uporablja se v nekaterih arhitekturah, zlasti za poslovne aplikacije, ki zahtevajo natančno decimalno aritmetiko. Decimalne števke se lahko predstavijo na različne načine, na primer z binarno kodiranimi decimalnimi števili (BCD), kjer 4 biti predstavljajo decimalno števko (0-9). 8-bitni bajt bi lahko shranil dve BCD števki ali eno ASCII predstavitev števke.
>
>Dolžine operandov imajo pogosto posebna imena, zlasti kadar so potence števila 2 glede na standardno "besedno" velikost, čeprav ta imena niso univerzalno dosledna v vseh računalniških arhitekturah:
>- 8 bitov = Bajt
>- 16 bitov = Polbeseda
>- 32 bitov = Beseda
>- 64 bitov = Dvojna beseda
>- 128 bitov = Štirikratna beseda


Kadar operandi zajemajo več bajtov v pomnilniku (npr. 32-bitno celo število), se imenujejo **sestavljeni pomnilniški operandi**. Za preprost in učinkovit dostop morajo ti operandi idealno ležati v sosednjih pomnilniških lokacijah.

Ključno vprašanje se pojavi glede vrstnega reda shranjevanja bajtov večbajtnega operanda v pomnilniku, znano kot **endiannost**. Obstajata dve glavni konvenciji:

- **Big Endian:** Najpomembnejši bajt (bajt, ki vsebuje bite najvišjega reda) operanda je shranjen na najnižjem pomnilniškem naslovu dodeljenega prostora. Naslednji bajti z naraščajočo manjšo pomembnostjo so shranjeni na naraščajočih naslovih.
- **Little Endian:** Najmanj pomemben bajt (bajt, ki vsebuje bite najnižjega reda) operanda je shranjen na najnižjem pomnilniškem naslovu. Naslednji bajti z naraščajočo večjo pomembnostjo so shranjeni na naraščajočih naslovih.

BE: 0xABCD > AB | CD
LE: 0xABCD > CD | AB

Z večbajtni operandi in organizacijo pomnilnika je povezano vprašanje **poravnave**. Sodobni pomnilniški sistemi so pogosto organizirani v banke, do katerih se lahko dostopa vzporedno (npr. hkratni dostop do 8 bajtov). Za učinkovit, enociklični dostop do operanda velikosti 's' bajtov mora biti njegov začetni pomnilniški naslov 'A' večkratnik 's' (tj. A mod s = 0). Operand je **poravnan**, če je njegov naslov večkratnik njegove velikosti; sicer je **neporavnan**. 

Dostop do neporavnanega operanda lahko zahteva večkratne dostope do pomnilnika, da se pridobijo vsi njegovi bajti iz različnih bank, kar znatno upočasni operacijo. Nekatere arhitekture tolerirajo neporavnane dostope (z zmanjšanjem zmogljivosti), medtem ko druge signalizirajo napako ali "ujamejo" program, če poskuša izvesti neporavnan dostop, kar zahteva, da ga programska oprema obravnava. Na primer, v pomnilniškem sistemu, organiziranem okoli 8-bitnih bajtov, je 64-bitni (8-bajtni) operand poravnan le, če je njegov naslov večkratnik števila 8, kar pomeni, da morajo biti zadnji trije biti naslova 0.

# Struktura in format ukaza

Ukaz je predstavljen kot zaporedje bitov. Običajno je shranjen v eni ali več sosednjih pomnilniških besedah. Vsak ukaz mora vsebovati vsaj dva temeljna dela informacije:

- **Koda operacije (Opcode):** Ta del določa, _katero_ operacijo je treba izvesti (npr. ADD, LOAD, JMP).
- **Informacije o operandih:** Ta del določa operande, ki jih operacija zahteva, vključno z njihovimi lokacijami in načini naslavljanja.

**Format ukaza** določa, kako so biti ukaza razdeljeni na ta polja (polje kode operacije, polja naslovov/registrov operandov, polja načinov, polja odmikov itd.). Zasnova formata ukaza je kompleksno kompromisno razmerje, na katerega vpliva več dejavnikov:
- Dolžina pomnilniške **besede**.
- Želeno **število eksplicitnih operandov**.
- **Tip in število registrov** v CPU (vpliva na velikost polj registrov).
- **Dolžina pomnilniških naslovov** (vpliva na velikost polj naslovov/odmikov).
- Skupno **število operacij** v naboru ukazov (vpliva na velikost polja kode operacije).

Arhitekture primarno uporabljajo tri glavne strategije dolžine ukazov:

- **Spremenljiva dolžina:** Ukazi imajo lahko različne dolžine, ki jih običajno določajo polja kode operacije in načina naslavljanja. To omogoča veliko število operacij in prilagodljive načine naslavljanja, potencialno z uporabo krajših ukazov za pogosto uporabljene preproste operacije in daljših za kompleksne naloge ali večje naslove.
- **Fiksna dolžina:** Vsi ukazi imajo enako vnaprej določeno dolžino (npr. 32 bitov ali 64 bitov). Ta pristop poenostavlja pridobivanje in dekodiranje ukazov, kar je koristno za pretočno obdelavo (pipelining). Običajno omejuje število operacij in načinov naslavljanja ter pogosto omejuje velikost neposrednih vrednosti ali odmikov, ki jih je mogoče neposredno kodirati v ukazu. To je značilno za arhitekture **RISC**. Tipičen format fiksne dolžine ima lahko polja za kodo operacije in fiksno število polj operandov/registrov.
- *Hibridna: Nekatere arhitekture kombinirajo ukaze fiksne in spremenljive dolžine ali imajo več formatov fiksne dolžine. To ponuja kompromis.*

**Ortogonalnost ukazov**

Zaželena lastnost pri načrtovanju nabora ukazov je **ortogonalnost**. Ta izraz opisuje medsebojno neodvisnost različnih komponent znotraj ukaza. Idealno bi bilo, da:

- Koda operacije ne bi smela biti odvisna od operanda. 
- Informacije, ki določajo en operand, bi morale biti neodvisne od informacij, ki določajo druge operande. 

Ortogonalnost poenostavlja nabor ukazov tako za načrtovanje strojne opreme (dekoderji so enostavnejši)

>[!|hide]- CISC proti RISC: Evolucija velikosti nabora ukazov
>
Zgodovinsko gledano je prišlo do razhajanja v filozofijah načrtovanja naborov ukazov, ki se na splošno kategorizirajo kot CISC in RISC.
>
**CISC (Complex Instruction Set Computer - računalnik s kompleksnim naborom ukazov)** arhitekture, kot so IBM 370, VAX in zgodnji procesorji Intel x86, so bile značilne po velikih, kompleksnih naborih ukazov. Cilj je bil pogosto vključiti zmogljive ukaze, ki bi lahko izvajali kompleksne naloge (kot je manipulacija z nizi ali klici procedur) z enim samim ukazom, s čimer bi se zmanjšala "semantična vrzel" med konstrukti višjenivojskih jezikov in strojnih ukazov. Značilni so bili ukazi spremenljive dolžine in številni načini naslavljanja.
>
**RISC (Reduced Instruction Set Computer - računalnik z zmanjšanim naborom ukazov)** arhitekture, ki so se pojavile kasneje (npr. MIPS, ARM, DEC Alpha, IBM/Motorola PowerPC), so temeljile na opažanju, da prevajalniki redko uporabljajo mnoge kompleksne ukaze v naborih CISC, preprostejši ukazi pa bi se lahko izvajali veliko hitreje, zlasti v pretočnem procesorju. Arhitekture RISC imajo manjši, preprostejši nabor ukazov, običajno fiksne dolžine, z manj načini naslavljanja in pretežno uporabljajo operacije med registri, pri čemer zahtevajo eksplicitne ukaze LOAD in STORE za dostop do pomnilnika.
>
Ugotovitve v 80. letih prejšnjega stoletja so izpostavile ključne trende, ki so spodbudili prehod k RISC:
>
>- **Stalna rast naborov ukazov:** Proizvajalci procesorjev so nenehno dodajali vedno več ukazov. Medtem ko so imeli zgodnji stroji, kot je IAS (1951), zelo majhen nabor ukazov (23 ukazov, 1 način naslavljanja), so imeli poznejši procesorji v 70. letih prejšnjega stoletja na stotine ukazov.
>- **Redka uporaba kompleksnih ukazov:** Analize so pokazale, da optimizirajoči prevajalniki pogosto uporabljajo le majhen podnabor razpoložljivih ukazov, pri čemer se pogosto držijo preprostejših. Velik del kompleksnih, specializiranih ukazov se v tipičnih programih redko ali nikoli ni uporabljal.
>
Razlogi za prvotno rast števila ukazov so vključevali:
>
>- Željo po zmanjšanju **semantične vrzeli** med višjenivojskimi jeziki in strojno kodo.
>- Enostavnost dodajanja novih ukazov pri uporabi **mikroprogramiranja** kot metode implementacije kontrolne enote.
>- Veliko **hitrostno vrzel** med hitro logiko CPU in počasnejšim glavnim pomnilnikom (kompleksen ukaz, ki se v celoti izvaja znotraj CPU, je lahko veliko hitrejši od zaporedja preprostih ukazov, ki zahtevajo večkratne dostope do pomnilnika).
>
>Vendar pa je več dejavnikov prispevalo tudi k razlogom za **zmanjšanje** števila in kompleksnosti ukazov, kar je naklonilo pristopu RISC:
>
>- **Kompleksnost prevajalnikov:** Prevajalniki so težko učinkovito izkoristili obsežne in kompleksne nabore ukazov strojev CISC. Ciljanje na preprostejši nabor je bilo za optimizacijo lažje.
>- **Učinkovitost predpomnilnika:** Uvedba in izboljšanje predpomnilnikov CPU je znatno zmanjšalo dejansko kazen za dostop do glavnega pomnilnika. Če so podatki v predpomnilniku, je dostop do njih veliko hitrejši, kar zmanjšuje zmogljivostno prednost kompleksnih ukazov, ki so poskušali zmanjšati dostope do pomnilnika. Dostop do predpomnjenih podatkov je postal skoraj tako hiter kot izvajanje mikroprogramske kode znotraj CPU.
>- **Pretočna obdelava (Pipelining):** Sodobni procesorji se močno zanašajo na pretočno obdelavo za doseganje visoke zmogljivosti z hkratnim izvajanjem več ukazov v različnih fazah. Preprosti ukazi fiksne dolžine z omejenimi načini naslavljanja je veliko lažje učinkovito pretočno obdelati kot kompleksne ukaze spremenljive dolžine, ki lahko trajajo veliko ciklov in imajo nepredvidljive vzorce dostopa do pomnilnika.
>- **Paralelizem znotraj CPU:** Preproste ukaze je lažje izvajati vzporedno z uporabo tehnik, kot sta superskalarno izvajanje in paralelizem na ravni ukazov (ILP).


Če povzamemo te točke, pogoste značilnosti arhitekture RISC vključujejo:

- Izvajanje večine ukazov znotraj enega samega cikla ure CPU, kar olajša učinkovito pretočno obdelavo.
- Uporaba **arhitekture register-register** ali **naloži/shrani**, kjer aritmetične in logične operacije delujejo samo na registre operandov, dostop do pomnilnika pa je omejen na namenske ukaze LOAD in STORE.
- Implementacija logike izvajanja ukazov primarno s strojno ožičenim krmiljenjem (ne z mikroprogramiranjem), ki je hitrejše za preproste operacije.
- Relativno **majhen nabor ukazov** in **malo načinov naslavljanja**, kar poenostavlja krmilno enoto in dekodiranje ukazov.
- Uporaba **fiksne dolžine ukazov**, kar močno poenostavlja pridobivanje in dekodiranje ukazov za pretočno obdelavo.
- Zanašanje na **dobre prevajalnike**, ki lahko učinkovito prevedejo kodo višjega nivoja v zaporedja preprostih ukazov in učinkovito upravljajo z dodeljevanjem registrov za maksimiranje zmogljivosti na poenostavljeni strojni opremi.

# Podprogrami

|Register|ABI Name|Register|ABI Name|
|---|---|---|---|
|x0|zero|x18|s2|
|x1|ra|x19|s3|
|x2|sp|x20|s4|
|x3|gp|x21|s5|
|x4|tp|x22|s6|
|x5|t0|x23|s7|
|x6|t1|x24|s8|
|x7|t2|x25|s9|
|x8|s0 / fp|x26|s10|
|x9|s1|x27|s11|
|x10|a0|x28|t3|
|x11|a1|x29|t4|
|x12|a2|x30|t5|
|x13|a3|x31|t6|
|x14|a4|||
|x15|a5|||
|x16|a6|||
|x17|a7|||


Izvajanje podprograma je sestavljeno iz, priprave parametrov, prenos izvajanja, izvajanje, priprava rezultata, vrnitev izvajanja.

Stack je podtatkovna struktura kjer shranjujemo podatke zaporedno nato pa odstranjujemo od najnovejšega do najstarejšega.

V RISC-V uporabljamo stack pointer v registru `x2`. V implementaciji ga premikamo navzdol ko dodajamo vrednosti.

Stack uporabljamo pri shranjevanju povratnih naslovov, 
prenos parametrov če jih je več kot jih lahko damo v registre, 
shranjevanje lokalnih spremenljivk če ni registrov ali so prevelike, 
obnavljanje registrov ki smo jih spremenili a se pričakuje da so tiste vrednosti ohranjene.

Stack naj bi bil poravnan na 16 bajtov zato ponavadi premaknemo kazalec za večkratnik 16 nato pa od konstante ki kaže na začetek sklada odštevamo pravilni odmik za podatke.

Register ki vedno kaže na začetek sklada je `s0` oz. `fp` frame pointer.

Pri klicanju podprogramov imamo naslednji dogovor:
- registri `a0 - a7` so za argumente (`x10 - x17)
- registra `a0` in `a1` sta za vračanje vrednosti
- (če je več argumentov jih potisnemo na sklad)

Za prenos izvajanja imamo
- `JAL rd, label` - shrani `PC + 4` v `rd` in skoči na `label`
- `JALR rd, rs, offset` - shrani `PC + 4` v `rd` in skoči na `offset + rs`

Psevdoukaz ret uporablja `jalr x0 ra zero` kot skok na return add PC + 4 pa zavržemo.

Return address je po dogovoru shranjen v register `x1` - `ra`.

Podprogram si ponavadi v pomnilniku zgradi svoj okvir, kjer so vsi podatki ki jih poterbuje - argumetni, povratni naslovi, registre ki je treba obnoviti, lokalne spremenljivke ki niso shranjene v registrih

Frame pointer vsebuje vrednost ki kaže na okvir. To je register `s0` ki je `x8`. Omogoča stabilen odmik od `fp` za dostop do spremenljivk.

Razlikujemo med obnovljivimi in začasnimi registri,
registri ki jih moramo pred začetkom izvajanja funkcije shraniti v pomnilnik in potem obnoviti pred vrnitvijo so frame pointer, return address razen pri listnih funkcijah, shranjene registre, argumente pa shranimo v pomnilnik.

Delovni registri so tisti nad katerimi izvajamo operacije to so temporary registri in neuporabljeni argumenti ali pa kar argumenti če so shranjeni v spominu.

Ko končamo program v register a7 damo 10 in kličemo ecall.


# CPE

Centralna procesna enota oziroma CPE izvaja programske ukaze. Zgrajen je iz kombinacijskih in sekvenčnih vezij.

**Kombinacijska vezja**, kot so na primer ALU (aritmetično-logična enota), dekoderji, multipleksorji, izvajajo operacije, katerih izhod je v danem trenutku odvisen le od trenutnih vhodov. 

**Sekvenčna vezja** pa imajo sposobnost pomnjenja stanja; to so predvsem registri in pomnilniki.

Delovanje CPE je neločljivo povezano s konceptom **stanja**. 
Stanje CPE v kateremkoli trenutku je določeno z vrednostmi, shranjenimi v njenih sekvenčnih (pomnilnih) elementih, zlasti v registrih in morebitnih internih pomnilnikih (npr. predpomnilniki). 

Nadaljnje delovanje CPE – torej to, katere operacije se bodo izvedle in kakšne bodo nove vrednosti njenih pomnilnih elementov ter izhodni signali – je odvisno od njenega trenutnega stanja in od trenutnih vhodov (npr. ukaza, ki se izvaja, podatkov iz pomnilnika ali zunanjih signalov).

**Konceptualna predstavitev sinhronskih digitalnih vezij: Modela Moore in Mealy**

Sinhronska digitalna vezja, ki so osnova za večino sodobnih CPE, se pogosto modelirajo s **končnimi avtomati**. 

Klok (ura) sinhronizira delovanje, saj se sprememba stanja v registru zgodi le ob aktivni fronti ure (npr. naraščajoči ali padajoči rob kloka).

>[!|hide]- Modela
>*Mooreov model: Pri tem modelu so izhodi odvisni izključno od **trenutnega stanja vezja**. Kombinacijska logika se uporablja za izračun naslednjega stanja na podlagi trenutnega stanja in vhodov, ter za izračun izhodov na podlagi trenutnega stanja. Izhodi so stabilni skozi celotno obdobje ure.*
>
>*Mealyjev model: Pri Mealyjevem modelu so izhodi odvisni tako od trenutnega stanja kot tudi od trenutnih vhodov. Kombinacijska logika izračunava tako naslednje stanje kot izhode na podlagi trenutnega stanja in vhodov. To lahko vodi do hitrejšega odziva izhodov na spremembe vhodov, vendar so lahko izhodi nestabilni med obdobjem ure, če se vhodne spremembe hitro propagirajo skozi kombinacijsko logiko do izhodov.*


![[Pasted image 20250514205044.png]]



CPU deluje na ciklu 2 glavnih korakov:
1\. **Fetch** : CPE dobi naslednji ukaz iz pomnilnika, naslov je shranjen v `PC`
2\. **Execute** : Izvede se operacija ki jo določa ukaz.

V tem koraku se **ukaz dekodira** - katera operacija naj se izvede, preberejo se operandi iz registrov, izvede se operacija v ALU ali pa izračun pomnilniške lokacije, operandi se prenesejo iz pomnilnika če je to potrebno, rezultat se shrani v register ali pomnilnik, PC se posodobi.


Vsaka od komponent v CPE ima nek čas izvajanja oz. traja 1 ali več period ure CPE. 
Spremembe stanja sekvenčnih vezij se prožijo ob aktivni fronti ure. Preioda `t_CPE` je čas med dvema sosednjima aktivnima frontama. Njena frekvence pa je obratna vrednost `t_CPE`.

Perioda je navzdol omejena z zakasnitvijo kombinacijskih vezij.
To pomeni da je najkrajša možna perioda ure najdaljši čas izvajanja med elementoma v vezju.

Asinhronska oz. sekvenčna vezja ne uporabljalo globalne ure in niso omejena z najdaljšo potjo temveč z lko

## Cycles per instruciton
Če hočemo vedeti koliko ciklov imamo na ukaz uporabimo
$$\frac{c}{I}= \text{CPI}$$
kjer je $c$ število vseh ciklov, $I$ število vseh inštrukcij. To naj bi bilo celo število.
## Cycles per second
Če hočemo vedeti koliko ciklov se izvede na sekundo uporabimo
$$\frac{c}{t} = \text{CPS} = f_\text{CPE}$$
kjer je $c$ število vseh ciklov, $t$ čas izvajanja vseh ciklov.
## Instructions per second
Če hočemo vedeti koliko inštrukcij se izvede na sekundo imamo
$$\frac{I}{t} = \text{IPS}$$
$$\frac{I}{c\cdot \frac{t_{c'}}{c'}} = \text{IPS}$$
kjer je zgornja enačba logična, spodnja pa pravi število inštrukcij $I$ na število ciklov $c$ potrebnih za $I$ inštrukcij krat izvajanje $c'$ ciklov v $t_{c'}$ času.
To pa je 
$$\text{IPS} = \frac{f_\text{CPE}}{\text{CPI}}$$
ki pa pravi da pogledamo kako hitro dela procesor - $f_\text{CPE}$ kjer bi bilo prav če bi se vsaka inštrukcija zugodila v enem ciklu, zato pa delimo še s številom ciklov v ukazu da dobimo hitrost delovanja CPE s tolikimi cikli na inštrukcijo. 

**Hitrost izvajanja cikla delimo s številom ciklov ki jih moramo opraviti v inštrukciji da dobimo hitrost inštrukcije.**


# Cevovod

Cevovodno izvajanje razdeli izvajajnje vsakega ukaza na zaporedje korakov. Nato izvajajnje razdeli tako da se različni koraki različnih ukazov izvajajo hkrati.

Večina RISC procesorjev implementira 5-stopenjski cevovod:
- **IF (Instruction Fetch - Pridobivanje ukaza):** Procesor pridobi naslednji ukaz iz pomnilnika z uporabo programskega števca (PC).
- **ID (Instruction Decode / Register Fetch - Dekodiranje ukaza / Pridobivanje registrov):** Ukaz je dekodiran, da se ugotovi, katero operacijo izvaja. Preberejo se zahtevane vrednosti iz registrskega pomnilnika.
- **EX (Execute - Izvajanje):** Izvede se glavna operacija. To je lahko aritmetična/logična operacija (kot sta `add`, `and`), izračun pomnilniškega naslova za nalaganje/shranjevanje (npr. `lb`, `sb`) ali izračun ciljnega naslova za skok/razvejitev.
- **MEM (Memory Access - Pomnilniški dostop):** Če je ukaz ukaz za branje (npr. `lb`, `lw`), se podatki preberejo iz pomnilnika. Če je ukaz ukaz za pisanje (npr. `sb`, `sw`), se podatki zapišejo v pomnilnik. Drugi ukazi običajno preidejo to fazo, ne da bi dostopali do pomnilnika.
- **WB (Write Back - Zapis nazaj):** Rezultat ukaza (iz faze EX ali MEM) se zapiše nazaj v registrski pomnilnik.

Perioda je odvisna od časa njapočasnejše izmed stopenj cevovoda.

Ko ukazi niso popolnoma neodvisni dobimo **cevovodne nevarnosti**.

**Strukturne nevarnosti**: ko več stopenj cevovoda zahteva iso enoto

**Podatkovne nevarnosti**: ko ukaz potrebuje kot vhodni operand rezultat prejšnjega ki pa še ni dokončal ukaza

**Kontrolne nevarnost**: pri skokih, klicih,... kjer se spremnija `PC`, kjer ne moramo biti prepričani kam bo `PC` šel dokler se ne zaključi izvajanje potrebnih ukazov

Prevajalnik lahko že vstavlja `nop` ukaze kjer bi lahko bile nevarnosti oz. mehurčke.

Data forwarding oz. posredovanje je zasnova za ublažitev podatkovnih nevarnosti, kjer storjna oprema zazna kdaj je rezultat potreben pri naslednjem ukazu, preden se zapiše nazaj, kjer posreduje rezultat neposredno iz izhoda prejšnje faze cevovoda (EX/MEM) na vhod faze drugega ukaza (EXE).

Posebna vrsta podatkovne nevarnosti je nevarnost nalaganja-uporabe **load-use** hazard kjer LOAD bere iz pomnilnika v MEM fazi in so na voljo šele na koncu MEM. Ker pa naslednji ukaz zahteva ta podatek v EXE preden se MEM zaključi običajno zahtevamo 1-ciklični zastoj, da se EX zamakne dokler podatki niso na voljo.

Pri kontrolnih nevarnostih procesor predvideva da se izvajanje ne veji, kjer če ima prav ne izgubimo časa, če je napoved napačna ponavadi izgubimo 2 cikla ker se odločitev o vejitvi sprejme v EX.






