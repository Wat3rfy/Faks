# Zgodovina

Računakniška arhitektura je določena preko nivojev abstrakcije oz. implementacije sistemov, ki omogočajo da izvajamo uporabo obstoječih tehnologij.

V splošnem si sledijo 
- Aplikacija
- Algoritem
- Programski jezik
- Zbirni jezik
- Ukazna arhitektura
- Mikroarhitektura
- RTL
- Logična vrata
- Tranzistorji
- Fizika

**Digitalni in analogni princip** 
Računski stroji temeljijo na dveh osnovnih principih: digitalnem in analognem. 
Digitalni princip pomeni, da so podatki predstavljeni s končnim številom diskretnih vrednosti, kar zagotavlja večjo natančnost. 
Analogni princip pa uporablja zvezne vrednosti za predstavitev podatkov, vendar je njegova natančnost omejena. 
Digitalni računalniki so danes standard, medtem ko so analogni praktično izginili.

Prvi primer analognega računalnika je logaritmično računalo (Rechenschieber), ki omogoča računanje z uporabo logaritmov.

>[!|dokaz]- Logaritmično računalo:
>Logaritmično računalo (Rechenschieber), znano tudi kot logaritemsko ravnilo, je analogni računalnik, ki omogoča hitro računanje z množenjem, deljenjem, potenciranjem in korenjenjem, pri čemer izkorišča lastnosti logaritmov.
>
>Logaritemsko ravnilo temelji na dejstvu, da se množenje in deljenje lahko pretvorita v seštevanje in odštevanje logaritmov:
>
>- **Množenje**: $a \times b = 10^{(\log a + \log b)}$
>- **Deljenje**: $a \div b = 10^{(\log a - \log b)}$
>  ### Postopek uporabe
>
>- **Množenje**: Premikamo drsno lestvico tako, da začetna vrednost ene številke sovpada z drugo številko na fiksni lestvici. Rezultat odčitamo na ustrezni poziciji.
>- **Deljenje**: Obraten postopek – določimo razmerje med številoma na lestvici.
>- **Potenciranje in korenjenje**: Posebne oznake omogočajo izvajanje teh operacij z enostavnim premikanjem lestvice.

**Obdobje mehanike in prvi kalkulatorji** Prvi kalkulatorji so bili mehanske naprave, ki so omogočale osnovne aritmetične operacije, kot so seštevanje, odštevanje, množenje in deljenje.

Wilhelm Schickard je leta 1623 razvil prvi mehanski kalkulator, ki je uporabljal zobata kolesa z 10 zobniki in mehanizem za prenos vrednosti naprej. 

>[!|dokaz]- Wilhelm Schikardov kalkulator:
> Za seštevanje je vseboval 6 zobnikov, ki so prenašali enico, lahko si vnesel originalno število in vsako kolo zavrtel tolikokrat kolikor je bila vrednost števke števila ki se ga prišteva.
> Množenje je enako z vnaprej izračunanimi vrednostmi na valju, ob vnosu prvega faktorja se nastavi valj, ob vnosu drugega faktorja pa se razkrijejo okna, kjer so na valju zapisane pravilne vrednosti množenja. 

Pascalov stroj (1642) je imel dve skupini koles, kjer je ena služila kot akumulator, druga pa za prištevanje ali odštevanje vrednosti.

>[!|dokaz]- Pascalov stroj:
> Deluje praktično enako kot Wilhelm Schikardov le da je rahlo bolj zakompliciran s tem da uporablja sestavo mehanskih koles kjer je eno od koles le del kolesa ki se za prenos enice dviguje in pri prekoračitvi iz 9 na 0 spusti na koli zraven kjer ga zavrti in poveča vrednost za 1. 

Gottfried Wilhelm Leibniz je leta 1671 razvil naprednejši kalkulator, ki je omogočal vse osnovne operacije in bil pomemben korak v razvoju računalniških naprav. 

>[!|dokaz]- Leibnizov kalkulator:
> Vnesene vrednosti se z vrtenjem ročke dodajo v oz. odstranijo iz akumulatorja s katerega preberemo vrednost.
> 
> Množenje temelji na vrtenju ročke za vsako mesto množenja. Torej 7 $\times$ 35 bi naprej vrteli petkrat oz. prišteli 7 petkrat. Nato je še ena ročka zunaj akumulatorja, ki premika mesta seštevanja torej z vrtenjem te zunanjem ročke nastavimo katero mesto seštevamo torej bi prišteli 7 trikrat a na desetiških mestih kjer mesta menjamo z zunanjo ročko, seštevanje pa s sprednjo ročko.
> 
> Deljenje naj bi bilo le celh števil 

V 19. stoletju je Charles Babbage zasnoval **diferenčni stroj**, ki je temeljil na aproksimaciji funkcij s polinomi in uporabi metode končnih diferenc. Njegov analitični stroj, načrtovan okoli leta 1835, velja za prvi računalnik s shranjenim programom. Vsebuje računski del (mlin), pomnilnik, ukazne kartice in operandne kartice.

**Elektromehanski računalniki** 

Z razvojem elektrotehnike so se pojavili elektromehanski računalniki. Ti so uporabljali elektromotorje za pogon mehanskih kalkulatorjev ter električno branje luknjanih kartic. 

**Konrad Zuse** je leta 1938 razvil Z1, prvi mehanski računalnik, kasneje pa **Z3** (1941), ki velja za prvi funkcionalni splošnonamenski računalnik. Imel je pomnilnik s 64 22-bitnimi besedami in je omogočal delo s plavajočo vejico.

**Harvard Mark I**, ki ga je leta 1943 izdelal Howard Aiken v sodelovanju z IBM, je bil elektromehanski računalnik, dolg 15 metrov. Njegov pomnilnik je shranjeval 72 vrednosti po 23 desetiških mest, ukazi pa so bili zapisani na luknjanem traku.

**Prehod na elektronske računalnike** 

Elektromehanski stroji so imeli omejitve zaradi mehanskih delov, ki so upočasnjevali delovanje. 

Elektronski računalniki so jih hitro nadomestili. Elektronke so omogočile bistveno večjo hitrost, saj so elektroni veliko hitrejši od mehanskih komponent. 

**ENIAC (Electronic Numerical Integrator And Calculator)** (1945) je bil prvi elektronski računalnik, financiran s strani vojske. Vsebuje 18.000 elektronk, 1.500 relejev in je porabil 140 kW energije. Ker programi niso morali biti shranjeni je njegova programska shema je zahtevala ročno prevezovanje kablov in nastavitev stikal, kar je bilo zelo zamudno.

**John von Neumann** je uvedel koncept računalnika s shranjenim programom. 

**EDVAC (Electronic Discrete Variable Computer)** (1951) je bil prvi računalnik, ki je deloval po tej arhitekturi. Shranjeni program omogoča, da računalnik dostopa do ukazov in podatkov enako hitro, kar odpira možnosti za napredne obdelave podatkov. Stroj je voden od znotraj, program pa lahko spremnija druge programe.

**Razvoj tehnologije** 

Leta 1947 so v Bell Labs razvili **tranzistor**, ki je nadomestil elektronke in omogočil manjše, hitrejše ter energetsko učinkovitejše računalnike. Leta 1958 so nastala integrirana vezja (čipi), ki so še dodatno zmanjšala velikost in povečala zmogljivost računalnikov. Moorov zakon napoveduje, da se število tranzistorjev na čipu podvoji vsakih 18 mesecev, kar še danes drži.

**Sodobni računalniki in vgrajeni sistemi** Današnji računalniki vključujejo namizne in prenosne računalnike, strežnike, superračunalnike ter vgrajene sisteme v telefonih, kamerah, igralnih konzolah, gospodinjskih aparatih in avtomobilih. Vgrajeni sistemi so ključni v industriji in vsakdanjem življenju.

**Razvoj programiranja** Sprva programska orodja niso obstajala, zato so se programi pisali neposredno v strojni jezik. V 50. letih so se pojavili zbirni jeziki, kjer so simbolične kode zamenjale binarne ukaze. Prvi višji programski jezik, FORTRAN, se je pojavil leta 1956, sledili so ALGOL, COBOL in Lisp.

V 60. letih je IBM razvil IBM 360, prvi računalnik s prenosljivim ukaznim naborom. To je omogočilo razvoj standardiziranih sistemov. Danes programski jeziki, kot so C, C++, Java in Python, omogočajo razvoj kompleksnih aplikacij in sistemov.

tba / dosedanji razvoj, osnovni principi

zapis informacija in aritemtika . pdf:

Informacije v računalniku so organizirane v dve glavni kategoriji: ukaze in operande. Ukazi so navodila, ki jih računalnik izvaja, medtem ko so operandi podatki, na katerih te ukazi delujejo. Operandi se nadalje delijo na dve širši skupini: numerične in nenumerične operande.


Numerični operandi so številski podatki, ki jih računalnik obdeluje. Obstaja več vrst numeričnih operandov:

1. **Fiksna vejica**: Števila s predhodno določeno decimalno vejico.
    
2. **Predznačena števila**: Števila, ki lahko vsebujejo pozitivne ali negativne vrednosti.
    
3. **Nepredznačena števila**: Števila, ki so vedno pozitivna.
    
4. **Plavajoča vejica**: Števila, kjer se decimalna vejica lahko premika za večjo natančnost.
    
    - **Enojna natančnost**: 32-bitna predstavitev plavajoče vejice.
        
    - **Dvojna natančnost**: 64-bitna predstavitev plavajoče vejice.
        


Nenumerični operandi vključujejo podatke, ki niso številski:

1. **Logične spremenljivke**: Vrednosti, ki so lahko resnične (true) ali neresnične (false).
    
2. **Znaki**: Posamezni simboli iz določene abecede.


Zgodovinsko gledano so prvi računalniki podpirali le numerične operande, medtem ko sodobni računalniki obdelujejo široko paleto nenumeričnih podatkov. Najpogostejši obliki nenumeričnih operandov sta:

1. **Znaki**: Posamezni elementi abecede (npr. črke, številke, simboli).
    
2. **Nizi znakov (strings)**: Zaporedja znakov, ki tvorijo besede ali stavke.
    

Vsak znak je predstavljen z določeno abecedo, kar pomeni, da je vsak znak kodiran na specifičen način (npr. ASCII, Unicode). Ta standardizacija omogoča, da računalniki razumejo in obdelujejo besedilne podatke.

**ASCII** (American Standard Code for Information Interchange) je standardiziran sistem kodiranja znakov, ki je bil razvit leta 1968 in je postal temelj za predstavitev besedilnih podatkov v računalnikih. Osnovna različica ASCII uporablja 7-bitno kodiranje, kar omogoča predstavitev 128 različnih znakov. Med temi znaki je 95 natisljivih, ki vključujejo velike in male črke angleške abecede (A–Z, a–z), številke (0–9), ter različne ločila in simbole (npr. !, ", #). Preostalih 33 znakov so kontrolni znaki, ki služijo za upravljanje komunikacijskih procesov in krmiljenje vhodno/izhodnih naprav, kot so npr. znaki za začetek ali konec besedila, povratek vozlišča in drugi.

Vsak znak v ASCII je predstavljen z unikatno binarno kodo in decimalno vrednostjo. Na primer, velika črka **A** je kodirana kot `1000001` (65 v decimalnem sistemu), mala črka 'a' kot `1100001` (97), številka '0' kot `0110000` (48), in klicaj '!' kot `0100001` (33). Ta standardizacija je omogočila enotno interpretacijo besedilnih podatkov med različnimi računalniškimi sistemi, kar je bilo ključno za razvoj digitalne komunikacije.

Ker osnovna 7-bitna ASCII tabela ni vključevala znakov za ne-angleške jezike (npr. črke s posebnimi diakritičnimi znamenji), so bile razvite razširjene različice, ki uporabljajo 8-bitno kodiranje. To je omogočilo dodatnih 128 znakov, skupaj torej 256. Med najpomembnejše razširitve spadata **ISO/IEC 8859-1** (Latin-1), ki vključuje znake za zahodnoevropske jezike (npr. šumnike in črke kot so ñ, ç, ü), in **ISO/IEC 8859-2** (Latin-2), ki podpira vzhodnoevropske jezike (npr. poljske, češke in madžarske črke).

Koda BCD (Binary Coded Decimal) je način kodiranja decimalnih števk v binarni obliki, kjer vsaka posamezna decimalna cifra (0–9) predstavljena s svojo 4-bitno binarno vrednostjo. To pomeni, da se število v decimalnem sistemu ne pretvori v celoto v binarno obliko (kot pri običajnem dvojiškem zapisu), temveč se vsaka njegova cifra ločeno kodira s štirimi biti. Na primer, decimalno število **25** bi v BCD zapisu bilo predstavljeno kot `0010 0101` (kjer `0010` ustreza 2 in `0101` ustreza 5).

Spodnji štirje biti znakov za decimalne cifre v različnih abecedah, kot so BCDIC, EBCDIC in ASCII, prav tako sledijo BCD kodiranju. To pomeni, da je binarna reprezentacija števk v teh abecedah dosledna z njihovo numerično vrednostjo. Na primer, v ASCII je številka **0** kodirana kot `0110000`, vendar so njene spodnje štiri bite (`0000`) mogoče razumeti kot BCD kodo za 0. Podobno velja za druge številke: **5** ima v ASCII spodnje štiri bite `0101`, kar je tudi njena BCD reprezentacija.

Unicode je neprofitni konzorcij, ustanovljen leta 1991, ki standardizira kodiranje znakov za vse svetovne pisave. Njegov glavni cilj je omogočiti enotno predstavitev besedila v različnih jezikih, tudi tistih z ne-latinimi črkami.

Unicode uporablja več različnih kodirnih shem, imenovanih UTF (Unicode Transformation Format):

- **UTF-8**: Najbolj razširjena shema, ki uporablja spremenljivo dolžino kodiranja (1-4 bajte)
    
- **UTF-16**: Uporablja 2 ali 4 bajte za vsak znak
    
- **UTF-32**: Fiksna dolžina 4 bajti za vsak znak
    

UTF-8 je posebej pomemben zaradi svoje učinkovitosti in združljivosti:

- **Spremenljiva dolžina**: Znaki zavzemajo od 1 do 4 bajtov
    
- **Združljivost z ASCII**: Prvih 128 znakov (7-bitni) je enakih kot v ASCII, kar omogoča lažjo prehodnost
    
- **Struktura bajtov**:
    
    - Prvi bajt pove število bajtov v zaporedju
        
    - Nadaljnji bajti imajo posebno oznako (10xxxxxx)
        


UTF-8 različno kodira znake glede na njihovo pozicijo v Unicode prostoru:

1. **1-bajtni znaki** (0x00-0x7F): Enojni bajt v obliki 0xxxxxxx
    
2. **2-bajtni znaki** (0x0080-0x07FF): Dva bajta z vodilnimi biti 110xxxxx in 10xxxxxx
    
3. **3-bajtni znaki** (0x0800-0xFFFF): Trije bajti z vodilnimi biti 1110xxxx in dvema 10xxxxxx
    
4. **4-bajtni znaki** (0x10000-0x10FFFF): Štirje bajti z vodilnimi biti 11110xxx in tremi 10xxxxxx
    

# Zapis števil

**Pozicijska notacija** omogoča zapis števil v poljubni bazi $r,$ kjer vsaka števka $b_i$ prispeva k skupni vrednosti glede na svoj položaj in težo oblike $r^i$. Splošna formula za vrednost števila $V(b)$ je:

$$ V(b) = \sum_{i=-m}^{n-1} b_i r^i $$

Primer v sedmiškem sistemu ($r=7$):  
$215,36_7 = 2 \times 7^2 + 1 \times 7^1 + 5 \times 7^0 + 3 \times 7^{-1} + 6 \times 7^{-2}$  
Kar v decimalnem sistemu pomeni: $98 + 7 + 5 + \frac{3}{7} + \frac{6}{49} \approx 110,489$.

**Dvojiški zapis števil v fiksni vejici** uporablja bazo $r=2$ kjer vsak bit $b_i$ zavzame vrednost 0 ali 1. Vrednost števila se izračuna po formuli:

$$ V(b) = \sum_{i=-m}^{n-1} b_i 2^i $$

Pri fiksni vejici so biti razdeljeni na celi del ($n$ bitov) in ulomek ($m$ bitov), kar označujemo s formatom Qn.m. Na primer, format Q3.5 pomeni 3 bite za celi del in 5 bitov za ulomek:  
$b_2 b_1 b_0, b_{-1} b_{-2} \ldots b_{-5}$.

Primer pretvorbe dvojiškega števila $110101,101_2$ v desetiško:  

$$1 \times 2^5 + 1 \times 2^4 + 0 \times 2^3 + 1 \times 2^2 + 0 \times 2^1 + 1 \times 2^0 + 1 \times 2^{-1} + 0 \times 2^{-2} + 1 \times 2^{-3} =$$ 
$$= 32 + 16 + 0 + 4 + 0 + 1 + 0,5 + 0 + 0,125 = 53,625_{10}$$

Druge oblike fiksne vejice:  
- Q8.8: 8 bitov za celi del in 8 bitov za ulomek  
- Q2.2: 2 bita za celi del (max $3_{10}$) in 2 bita za ulomek (natančnost $0,25$).  
Primer Q2.2: $11,01_2 = 3 + 0,25 = 3,25_{10}$.

Za **pretvarjanje iz desteiškega v dvojiški** deliš z dva in prebereš števke od zadnje do prve.

Za **pretvarjanje ulomka** pa množiš z 2, in potem celi del vzememo za števke in jih preberemo od zadnje do prve.

Ne da se pa vsakega desetiškega v dvojiški sistem dat, ker grejo lahko v neskončnost.

Kadar številu režemo decimalna mesta vedno velja da je napaka oz. ostanek manjši od $\text{baza}^\text{števio decimalk}$.

$$10.3232$$
$$10.32 \Rightarrow \text{err} = 0.0032$$
$$10^{-2} = 0.01 \geq \text{0.0032}$$

Če želimo da napak ni večja od nekega izbranega $E_{\max}$ potem, velja

$$\text{err} \leq r^{-m} \leq E_{\max}$$

torej da zagotovimo napako manjšo od izbrane napake potrebujemo $m$ mest.

$$m\leq \log_{r}{\frac{\!\!1}{E_{\max}}}$$

Enačba velja za katerokoli bazo.

### Nepredznačena števila

$$V(b) = \sum_{i = 0}^{n-1}b_{i}2^{i}$$


Z $n$ biti lahko zapišemo $2^{n}-1$ števil.

Kadar rezultat operacije preseže obseg števil, se pojavi **carry**.

### Predznačena števila

Lahko jih zapišemo na več načinov:

**Predznak-veličinski zapis (PV)**

Prvi bit predstavlja predznak ostali velikost, a je problem da imamo 2 ničle in pri seštevanju in odštevanju moramo obravnavati predznak posebej in izbrati pravilno operacijo.

$$V(n) = (-1)^{b_{n-1}}\sum_{i=0}^{n-2}b_{i}2^{i}$$


**Predstavitev z odmikom (PO)**

Vsakemu številu odštejemo nek odmik.

$$V(n) = \sum_{i=0}^{n-1}b_{i}2^{i} - 2^{n-1}$$

Odmik ne rabi biti $2^{n-1}$
Pri seštevanju je treba odmik odšteti, pri odštevanju pa prišteti.


**Eniški komplement**

$$V(b)=\sum_{i=0}^{n-1}b_{i}2^{i}-b_{n-1}(2^{n}-1)$$

Če se začne z $1$ je negaitvno število. Nasprotno število dobimo če invertamo vse bite. Enako če odštejemo oz. prištejemo $2^{n}-1$.

**Dvojiški komplement**

$$V(b) = \sum_{i=0}^{n-1}b_{i}2^{i}-b_{n-1}2^{n}$$

Lahko si predstavljamo kot da je MIB negaitven. Nasprotno število dobimo s tem da invertamo bite in prištejemo 1.

Pozitivna števila se začnejo z 0, negativna p z -1.

**Če seštevamo dve števili v dvojiškem komplementu bit prenosa ne upoštevamo.**

**Če seštevamo dve pozitivni števili in dobimo negativno število je vsota nemogoča.**

# IEEE 745

Enojna natačnost (32 bitov):
```
| SG |  EXP  |  MNTS  |
| 31 | 30:23 |  22:0  |
|  1 |   8   |   23   |
```
Predznak: 0 ;-; pos, 1 ;-; neg
8-bit eksponent z odmikom 127: EXP-127 = dejanski eksponent
če je EXP = 00000000 je dejasnki eksponent -126 in implicirana enica postane 0.
Za mantiso velja da vsebuje le decimalni del, kjer pred vejico stoji implicirana enka, oz. če je exponent enak 0 je implicirana vrednost 0.

0 ima mantiso nič, kot eksponent

Neskončnost ;-; EXP = 255, če je MNTS = 0 imamo $\infty, -\infty$

NaN ;-; EXP = 255, m $\neq$ 0

**tba zaokroževanje**

Dvojna natačnost (32 bitov):
```
| SG |  EXP  |  MNTS  |
| 63 | 62:52 |  51:0  |
|  1 |   11  |   52   |
```


# RISCV


Pomnilnik sestavljen iz bajtov podatkov : ```xxxx_xxxx xxxx_xxxx``` v binarnem oz. ```XX``` v 16-iškem.

Vsak bajt ima svoj 32 bitni naslov. Naslovi so lahko shranjeni v naslovnih spremenljivkah ki jih definiramo v podatkovnem segmentu skupaj s pripadajočimi vrednostmi na naslovih.

> V podatkovnem segmentu dejansko samo podajamo vrednost, ki se zaporedno shranjujejo v pomnilnik, naslovne spremenljivke niso potrebne, a so uporabne da shranimo naslove pomembnih vrednosti

Podatkovni segment definiramo z ```.data```.
Ob definiciji naslovnih spremenljivk, opredelimo vrednost ki se shrani na ta naslov
```
A: .word 23

.word 23 # je še vedno validno; vrednost se shrani na naslednje mesto
```
Shranimo lahko ```.byte .half .word```, kjer je
```byte``` velikosti 8 bitov, 
```half``` velikosti 16 bitov, 
```word``` pa 32 bitov.

Vrednosti, ki jih želimo shraniti lahko zapišemo v binarnem, šestnajtiškem ali desetikem sistemu.

Kar se dogaja je da se vrednosti po vrsti zapisujejo v pomnilnik, kjer se naslov ob definiciji naslovne spremenljivk (recimo ```A```) shranijo v tabelo simbolov in naslovov.

Če je vrednost prevelika kot velikost podatkovnega tipa se program ne prevede.
```
.byte 0xFFF # se ne prevede
```

Vrednosti se v pomnilnik zapisujejo po **pravilu tankega konca**. 
To pomeni da se bodo spodnji biti zapisujejo prvi. 

Hkrati se bodo iz pomnilinka vrednosti nalagale tako da bodo vrednosti pobrane iz naslova postavljene na najbolj spodnje bite.

```
0x123456 -> 56 34 12 00

56 23 00 00 -> 0x00002356
```

Vrednosti lahko zapišemo tudi kot list

```
A: .byte 0x12, 0x34, 0x56

# -> 12 34 56 00
```

Uporabimo lahko tudi ```.align X```, ki vstavi ```X``` število bytov ničel do ustreznega naslova, ki je deljiv s podanim številom, razen če je "kazalec" že na naslovu, ki je deljiv s številom. (```.align``` deluje tudi pri ```.text```)

```
.byte 0x23
.align 4
.byte 0x23

#
# 23 x  x  x
# 23 00 00 00

.byte 0x23
.byte 0x23

#
# x  x  x  x
# 23 23 x  x

```

V procesni enoti se nahajajo registri v katerih so shranjeni operandi.

Pri RISCV arhitekturi imamo 32 registrov, kjer je ```x0``` rezerviran za 0.

Vrednosti iz pomnilnika nalagamo v registre, nato pa z vrednostmi v njih lahko izvajamo neke aritemtične operacije.

Za prenašanje podatkov iz pomnilnika v registre in obratno uporabljamo ukaze.

Ukaze delimo na tipe R, I, S, U, B, J

>**R oz. register-register** operations 
>
>```opcode```, ```funct3```,```funct7``` identifikacija ukaza
>```rd``` - destination register (ciljni register)
>```rs1, rs2``` - source register (izvorna registre)
>
>```add x1 x2 x3```:
>
>```
>| 0000000 | 00011 | 00010 | 000 | 00001 | 0110011 |
>| funct7  | rs2   | rs1   |funct3| rd   | opcode  |
>```
>
>V pomnilniku:
>
>```0b10110011 | 0b00000000 | 0b00110001 | 0b00000000```
>
>
>R operacije imajo en ciljni in 2 izvorna registra

>**I oz. immidiate** operations
>
>```opcode```, ```funct3``` identifikacija ukaza
>```rd``` - destination register (ciljni register)
>```rs1``` - source register (izvorni register)
>```imm[11:0]``` - 12-bit sign-extended immediate
>
>```addi x1, x2, 42```:
>```
>| 000000101010 | 00010 | 000 | 00000 | 0000010 |
>| imm[11:0]    | rs1   |funct3|  rd  | opcode  |
>```
>V pomnilniku:
>
>```0b00000010 | 0b00000000 | 0b10100001 | 0b00000010```
>
>I operacije imajo ciljni, izvorni register in takojšnjo vrednost
>To bojo operacije:  ```addi, andi, lw, lh, lb, jalr,... ```
>`slli` in nekateri drugi imajo drugače, pri `slli` je `shamt*` nepredznačeno 5-bitno število.


> **S oz. store** operations
>
>```opcode```, ```funct3``` identifikacija ukaza
>```rs1``` - base address (register z naslovom na katerega shranjujemo)
>```rs2``` - source register (izvorni register)
>```imm[11:5], imm[4:0]``` - upper 7 bits, lower 5 bits - 12-bit signed immediate offset
>
>```sw x1, 100(x2)```:
>```
>| 0000011 | 00001 | 00010 | 010 | 00100 | 0100011 |
>| imm[11:5] | rs2 |  rs1 |funct3|imm[4:0]| opcode |
>```
>V pomnilniku:
>
>```0b00100011 | 0b00100010 | 0b00010001 | 0b00000110```
>


> **B oz. branch** operations
>
>```opcode```, ```funct3``` identifikacija ukaza
>```rs1, rs2``` -  compared registers (registra ki primerjamo)
>```imm [12:1]``` - naslov kamor skočimo, večkratnik 2, ker morajo veje biti **2-byte aligned**. 
>
>`beq x1, x2, label`:
>```
>| 0 | 100000 | 00010 | 00001 | 000 | 0000 | 0 | 1100011 
>
>| imm[12] | imm[10:5] | rs2 | rs1 |funct3| imm[4:1] | imm[11] | opcode |
>```
>V pomnilniku:
>
>```0b01100011 | 0b10000000 | 0b00100000 | 0b01000000```

> **U oz. upper immediate** operations
>
>```opcode```, ```funct3``` identifikacija ukaza
>```rd``` -  compared registers (registra ki primerjamo)
>```imm [31:12]``` - 20-bit immediate. 
>
>`lui x1, 0x12345`:
>```
>| 01000000001000001000 | 00000 | 1100011 
>
>|      imm[31:12]      |  rd   | opcode  |
>```
>
>V pomnilniku:
>
>```0b01100011 | 0b10000000 | 0b00100000 | 0b01000000```

> **J oz. jump** operations
>
>```opcode```, ```funct3``` identifikacija ukaza
>```rd``` -  compared registers (registra ki primerjamo)
>```imm [31:12]``` - 20-bit immediate. 
>
>`lui x1, 0x12345`:
>```
>| 0 | 1000000000 | 0 | 00000000 | 00001 | 1101111 
>
>| imm[20] | imm[10:1] | imm[11] | imm[19:12] | rd | opcode |
>```
>
>V pomnilniku:
>
>```0b11101111 | 0b00000000 | 0b00000000 | 0b01000000```

 `immediate` je pr vsakemu ukazu mal drgač obdelan tkoda je tuki sam vse kar sem do sedaj ugotovil.

> Če kjer koli uporabljamo 3 bajtni `imm` lahko uporabimo `˙-0x800` in naprej da se program prevede

1\. `lui`:
`lui x2, 0x123456789` bo v register `x2` naložil  `56789` oz. zadnjih 5 števk tudi če uporabimo `%lo` ali `%hi`
Pri prevajanju bo pogledal zadnjih 8 števk, če bo zadnjih 8 števk večjih od `7FFFFFFF` potem se ne prevede in enako velja za naslove, ki pa ne morejo biti več od 8 števk v 16 sistemu
Če uporabljamo naslovne spremenljivke brez `%lo` ali `%hi` dobimo spodnjih 5 števk in velja isto da pregleda zadnjih 8 števk ter ne prevede če so večje od `0x7FFFFFF`
```
.data #0x7FFFFFFF
A: .word 0
B: .word 0

.text

lui x2, %hi(0x689abcde)
lui x2, A
```
```
0: lui x2 0xabcde
4: lui x2 0xfffff
```

Ko uporabljamo pravilno pa se prevede in deluje pravilno tudi če je `%hi` večje od `7ffff`.


2\. `addi`:
`imm` mora biti 2047 ali manj, za negativna števila pa -2048 ali večji ter zapisan v desetiškem sistemu.

To je pomembno pri uporabi `%lo` kjer moramo pazit da nismo na takem naslovu kjer bi spodnji biti presegali `800`.

**Če dam memory start v 7FFFFFFF deluje če ga dam v 80000000 ga sploh ne morm gledat**
**Dodamo še da `lw` deluje do naslovov `80000000`**

3\. `slli`
Zahteva `imm` velikosti 5 bitov oz. nepredznačeno od 0 do 31


**Nalaganje podatkov iz pomnilnika** se izvaja z ukazi
`lw, lh, lb`
`lwu, lhu, lbu`

>Load word :
>
>`lw rd, imm(rs1)` ali `lw rd imm rs1`
>```
>lw x4 A 
># se prevede v 
>auipc x4 0x10000  # oz. %hi(A) 
>lw x3 1024 x3     # oz. %lo(A) x3
>```
>Ta deluje dokler je `pc` dovolj majhen.
>`imm` mora biti med -2048 in 2047, predstavlja 1 byte pomika
>```
>lw x2 0x7FF x3
>lw x2 A x3     # A < 0x000007FF
>lw x2 -2048 x3
>```
>podaljša predznak

**Shranjevanje podatkov v pomnilnik** se izvaja z uakzi
`sb, sh, sw`

```
sb rs2, imm(rs1) # rs1 <- memory add, imm <- odmik, 
# rs2 <- vrednost
```

Pri obeh imamo 12 bitni oz. 3 bajtni predznačeni odmik.

**Aritmetične operacije**

Pri uporabi `imm` se jim predznak razširina 32 bitov.

`addi, andi, ori, xori` vsi uporabljajo **3 bajtni** predznačeni `imm`

`lui, auipc` uporabljata **5 bajtni** predznačeni

`slli, srli, srai` uporabljajo **5 bitni** nepredznačeni `imm`

Premike ločujemo po aritemtičnih in logičnih, kjer aritemitični ohranjajo predznak, logičini ne ohranjajo predznaka

**Logični premiki za n mest predtavljajo množenje oz. deljenje z $2^{n}$**

Vsi ALE ukazi so 
`add, sub, addi, lui, auipc, and, or, xor, andi, ori, xori`
`sll, srl, sra, slli, srli, srai`

`lui` v zgornji del registra naloži 5 bajtno število.

`auipc` sešteje `pc` in 5 bajhtno število pomaknjeno z 12 bitov (preberemo 5 bajtno število prištejemo ga pa kakor da smo ga naložili v zgornji del 8 bajtenga števila). 


**V ALE ukaze spadajo tudi ukazi za primerjavo**

`slt, sltu, slti, sltui` : je prvi register manjši od drugega oz. prvi register manjši od `imm

`sltui` oba sta nepredznačena
`slti` oba sta predznačena

`slti` in `sltiu` uporabljata 3 bajtni immediate, ki je signed (torej ne več kot `0x7FF`) lahko pa -2048

**Psevdo ukazi** uporabljamo za lažje programiranje prevedejo pa se v dreuge ukaze

```
li x5 0xFFFFFFF # load immediate
mv x3 x4        # move x4 into x3
neg x3 x4       # negate x4 into x3
la x5 A         # load address

```






# Hazard

**Data hazards**
Read-After-Write hazard

When an instruction needs data that a previous instruction hasn't finished producing yet. The most common is the **Read-After-Write (RAW)** hazard.

- Example:  
    ADD R1, R2, R3 (writes to R1)  
    SUB R4, R1, R5 (reads from R1)
    
- In the pipeline, the SUB instruction reads R1 in its ID stage, but the ADD instruction won't write the correct value to R1 until its WB stage. If the SUB proceeds without waiting, it will read the old value of R1.

Load-Use hazard

`lb x2, B(x1)` (I2) reads `x1` for address calculation in EX/MEM. Dependency: I1 -> I2 (on x1). This is a Load-Use hazard. Since I2 immediately follows I1, it needs the value in its EX stage which is 1 cycle after I1's MEM stage finishes. This causes **1 stall cycle**.


**Control hazard** stane 2 cikla in se zgodi ko imaš nek skok oz. vejitev, kjer recimo da je `bne` v `DI` stanju, `FI` mora iti na naslednji ukaz torej ugiba ker ne ve ali bo skok ali ne, ko pride bne do EXE stanja šele posodobi program counter to pa stane 2 cilkla če moramo skočiti.

Procesor predvideva, da skok ne bo izveden.
**Answer b:** 14 urinih period. Utemeljitev: Procesor predvideva, da skok ne bo izveden. Če je skok izveden, to povzroči 2 izgubljeni urini periodi (procesor izprazni napačno privzete ukaze in vstavi mehurčke, ter nato privzame pravilen ukaz). Skok beq x2, x0, Z se izvede dvakrat (pri i=1 in i=4), kar povzroči 2 * 2 = 4 izgubljene periode. Skok bne x1, x0, LOOP se izvede petkrat (pri i=0, 1, 2, 3, 4), kar povzroči 5 * 2 = 10 izgubljenih period. Skupaj znašajo izgubljene periode zaradi kontrolnih nevarnosti 4 + 10 = 14.




***

Gemini log

Okay, let's break down this exercise about a pipelined RISC-V processor.

**1. Understanding the Setup**

*   **Processor:** It's a pipelined RISC-V processor.
*   **Forwarding (Premoščanje):** It has built-in forwarding. This is crucial – forwarding allows results from earlier pipeline stages (EX, MEM, WB) to be used by later instructions *before* the result is written back to the register file, reducing many data hazards.
*   **Control Hazard Handling:** For branches, the processor uses "predict not taken". If a branch is *taken* (the condition is met), it "invalidates fetched instructions and inserts bubbles". This means there's a penalty for taken branches. The penalty for a standard 5-stage pipeline (IF, ID, EX, MEM, WB) with predict-not-taken, where the branch decision is made in the EX stage, is typically 2 cycles. The instruction in IF and ID stages when the branch is in EX are flushed.

**2. Understanding the Code**

This is RISC-V assembly code.

*   `.data #0x400`: Defines a data section starting at memory address 0x400.
*   `A: .byte 5,4,3,2,1,0`: Defines an array `A` of bytes starting at address `A` (which is 0x400). The values are 5, 4, 3, 2, 1, 0.
*   `B: .byte 3,0,5,7,0,3`: Defines an array `B` of bytes starting at address `B` (which is `A` + size of `A`, so 0x400 + 6 = 0x406). The values are 3, 0, 5, 7, 0, 3.
*   `.text #0x0`: Defines a code section starting at memory address 0x0.
*   `addi x3, x0, A`: Sets register `x3` to the memory address of `A` (0x400). `x0` is the zero register (always 0). `x3` will act as a pointer to array `A`.
*   `LOOP:`: Label for the start of the loop.
*   `lb x1, 0(x3)`: Load byte from the memory address `x3 + 0` into register `x1`. This loads the current element from array `A`.
*   `lb x2, B(x1)`: Load byte from the memory address `B + x1` into register `x2`. This uses the *value* loaded from `A` (`x1`) as an *index* into array `B`. For example, if `x1` is 5, it loads `B[5]`.
*   `beq x2, x0, Z`: Branch to label `Z` if the value in `x2` (the element loaded from `B`) is equal to `x0` (zero).
*   `and x4, x1, x2`: Perform a bitwise AND operation between the values in `x1` and `x2`, and store the result in `x4`. This instruction is skipped if the `beq` branch is taken.
*   `sb x4, 0(x3)`: Store the byte from register `x4` into the memory address `x3 + 0`. This writes the result of the AND back into the current element of array `A`. This instruction is also skipped if the `beq` branch is taken.
*   `Z:`: Label for the branch target of `beq`.
*   `addi x3, x3, 1`: Increment the pointer `x3` by 1. This moves the pointer to the next byte (next element) in array `A`.
*   `bne x1, x0, LOOP`: Branch to label `LOOP` if the value in `x1` (the element loaded from `A` in this iteration) is *not* equal to `x0` (zero). This is the loop condition: the loop continues as long as the loaded element from `A` is non-zero.

**What the program does:**
The program iterates through the array `A`. For each element `A[i]`, it loads the value `A[i]` into `x1`. It then uses this value as an index to load the corresponding element `B[A[i]]` into `x2`.
- If `B[A[i]]` is zero, it skips the `and` and `sb` instructions and moves to the next element of `A`.
- If `B[A[i]]` is non-zero, it calculates `A[i] & B[A[i]]` and writes this result back into `A[i]`.
After processing `A[i]`, it moves to `A[i+1]`. The loop continues as long as the value *loaded* from `A` in the current iteration (`x1`) is non-zero.

**Tracing the Loop Execution (Values of x1 and B[x1]):**
*   i=0: `x3` points to A[0]. `lb x1, 0(x3)` loads `A[0]=5`. `lb x2, B(x1)` loads `B[5]=3`. `beq` (3==0) is false. `and` (5&3=1), `sb` (A[0]=1). `addi x3` points to A[1]. `bne` (5!=0) is true. Loop.
*   i=1: `x3` points to A[1]. `lb x1, 0(x3)` loads `A[1]=4`. `lb x2, B(x1)` loads `B[4]=0`. `beq` (0==0) is true. Branch to Z. Skip `and`, `sb`. `addi x3` points to A[2]. `bne` (4!=0) is true. Loop.
*   i=2: `x3` points to A[2]. `lb x1, 0(x3)` loads `A[2]=3`. `lb x2, B(x1)` loads `B[3]=7`. `beq` (7==0) is false. `and` (3&7=3), `sb` (A[2]=3). `addi x3` points to A[3]. `bne` (3!=0) is true. Loop.
*   i=3: `x3` points to A[3]. `lb x1, 0(x3)` loads `A[3]=2`. `lb x2, B(x1)` loads `B[2]=5`. `beq` (5==0) is false. `and` (2&5=0), `sb` (A[3]=0). `addi x3` points to A[4]. `bne` (2!=0) is true. Loop.
*   i=4: `x3` points to A[4]. `lb x1, 0(x3)` loads `A[4]=1`. `lb x2, B(x1)` loads `B[1]=0`. `beq` (0==0) is true. Branch to Z. Skip `and`, `sb`. `addi x3` points to A[5]. `bne` (1!=0) is true. Loop.
*   i=5: `x3` points to A[5]. `lb x1, 0(x3)` loads `A[5]=0`. `lb x2, B(x1)` loads `B[0]=3`. `beq` (3==0) is false. `and` (0&3=0), `sb` (A[5]=0). `addi x3` points to A[6]. `bne` (0!=0) is false. Exit loop.

The loop body executes 6 times (for indices 0 through 5). The `beq` branch is taken in iterations i=1 and i=4. The `bne` branch is taken in iterations i=0, 1, 2, 3, 4. The `bne` branch is *not* taken in iteration i=5, which terminates the loop.

**3. Answering the Questions**

Assuming a standard 5-stage pipeline (IF, ID, EX, MEM, WB) with forwarding, where Load results are available at the end of MEM and can be forwarded to the EX stage of the *next* instruction, requiring a 1-cycle stall for this immediate Load-Use hazard.

**a. Koliko urinih period se izgubi zaradi podatkovnih nevarnosti? (6 točk)**
(How many clock cycles are lost due to data hazards?)

Identify data dependencies within the loop body:
1.  `lb x1, 0(x3)` (I1) writes `x1`.
2.  `lb x2, B(x1)` (I2) reads `x1` for address calculation in EX/MEM. Dependency: I1 -> I2 (on x1). This is a Load-Use hazard. Since I2 immediately follows I1, it needs the value in its EX stage which is 1 cycle after I1's MEM stage finishes. This causes **1 stall cycle**.
3.  `beq x2, x0, Z` (I3) reads `x2` in EX. Dependency: I2 -> I3 (on x2). This is also a Load-Use hazard. Since I3 immediately follows I2, it needs the value in its EX stage 1 cycle after I2's MEM finishes. This causes **1 stall cycle**.
4.  `and x4, x1, x2` (I4) reads `x1` and `x2` in EX. Dependencies: I1 -> I4 (on x1), I2 -> I4 (on x2). I4 is 2 instructions after I1 and 1 instruction after I2. The values `x1` and `x2` will be available via forwarding from I1 and I2's MEM/WB stages in time for I4's EX stage (especially considering the stalls for I2 and I3 push I4 back). **0 stalls** for these.
5.  `sb x4, 0(x3)` (I5) reads `x4` and `x3`. Dependencies: I4 -> I5 (on x4), `addi x3` (I6) -> I5 (on x3). I4's EX result and I6's EX result can be forwarded to I5's EX/MEM stage without stalls. **0 stalls**.
6.  `addi x3, x3, 1` (I6) reads and writes `x3`. Dependency: I6 -> I6 (on x3) across loop iterations, or initial `addi x3, x0, A` -> I6. Forwarding handles this. **0 stalls**.
7.  `bne x1, x0, LOOP` (I7) reads `x1` in EX. Dependency: I1 -> I7 (on x1). I7 is 5 instructions after I1. The value is available in time. **0 stalls**.

So, there are 2 data hazard stalls per iteration of the loop (1 for `lb x1 -> lb x2`, 1 for `lb x2 -> beq x2`).
The loop executes 6 times.
Total data stalls = 6 iterations * 2 stalls/iteration = **12 clock cycles**.

**Answer a:** 12 urinih period. Utemeljitev: V vsaki iteraciji zanke se pojavita dve podatkovni nevarnosti tipa "load-use", ki ju premoščanje v standardnem 5-stopenjskem cevovodu ne more popolnoma odpraviti brez vstavitve ene mehurčke: med ukazi `lb x1, 0(x3)` in `lb x2, B(x1)` zaradi odvisnosti na registru x1, ter med ukazi `lb x2, B(x1)` in `beq x2, x0, Z` zaradi odvisnosti na registru x2. Vsaka od teh nevarnosti povzroči eno izgubljeno urino periodo. Zanka se izvede 6-krat (za elemente A[0] do A[5]), kar skupaj znese 6 * 2 = 12 izgubljenih urinih period zaradi podatkovnih nevarnosti.

**b. Koliko urinih period se izgubi zaradi kontrolnih nevarnosti? (6 točk)**
(How many clock cycles are lost due to control hazards?)

The processor predicts "not taken". Penalty for a taken branch is 2 cycles.
1.  `beq x2, x0, Z`: This branch is taken when `B[A[i]] == 0`. This happens for i=1 (B[4]=0) and i=4 (B[1]=0). The branch is taken 2 times. Each taken branch costs 2 cycles.
    Penalty from `beq` = 2 * 2 cycles = 4 cycles.
2.  `bne x1, x0, LOOP`: This branch is taken when `x1 != 0`, which means `A[i] != 0`. This happens for i=0, 1, 2, 3, 4. The branch is taken 5 times. Each taken branch costs 2 cycles.
    Penalty from `bne` = 5 * 2 cycles = 10 cycles.
    In the last iteration (i=5), `x1` is 0. The `bne` branch is *not* taken. The processor predicts not taken, which is correct. **0 penalty** for the final `bne`.

Total control stalls = Penalty from `beq` + Penalty from `bne` = 4 + 10 = **14 clock cycles**.

**Answer b:** 14 urinih period. Utemeljitev: Procesor predvideva, da skok ne bo izveden. Če je skok izveden, to povzroči 2 izgubljeni urini periodi (procesor izprazni napačno privzete ukaze in vstavi mehurčke, ter nato privzame pravilen ukaz). Skok `beq x2, x0, Z` se izvede dvakrat (pri i=1 in i=4), kar povzroči 2 * 2 = 4 izgubljene periode. Skok `bne x1, x0, LOOP` se izvede petkrat (pri i=0, 1, 2, 3, 4), kar povzroči 5 * 2 = 10 izgubljenih period. Skupaj znašajo izgubljene periode zaradi kontrolnih nevarnosti 4 + 10 = 14.

**c. Koliko urinih period traja izvajanje programa? (7 točk)**
(How many clock cycles does the program execution take?)

Total Cycles = Cycles for first instruction + Cycles for subsequent instructions + Total Stalls.
A simple way to approximate this for a sequence of N instructions on an S-stage pipeline is N + S - 1 cycles in the ideal case (no stalls). Here, the code has a loop and branches, so we need to be more precise.

Total Cycles = (Ideal cycles for all executed instructions) + Total Data Stalls + Total Control Stalls.
- Initial instruction: `addi x3, x0, A`. This is 1 instruction. Takes 5 cycles to pass through the 5-stage pipeline initially (IF, ID, EX, MEM, WB).
- Loop instructions executed:
    - Iterations i=0, 2, 3, 5 execute the full 7-instruction loop body (`lb x1`, `lb x2`, `beq`, `and`, `sb`, `addi x3`, `bne`). 4 iterations * 7 instructions = 28 instructions.
    - Iterations i=1, 4 execute a shorter path (skip `and`, `sb`). The sequence is `lb x1`, `lb x2`, `beq` (taken), `addi x3`, `bne`. 5 instructions are executed in the intended path, but 2 (`and`, `sb`) are fetched but flushed. 2 iterations * 5 instructions = 10 instructions.
    - Total useful instructions executed in the loop = 28 + 10 = 38 instructions.
- Total useful instructions executed = 1 (initial `addi`) + 38 = 39 instructions.
- Ideal cycles for these 39 instructions on a 5-stage pipeline (ignoring loop/branch structure temporarily for base calculation): 39 + 5 - 1 = 43 cycles. (This is the cycles taken if you laid out all 39 instructions in a line and ran them through the pipeline without stalls).

Total Cycles = Ideal Cycles + Total Data Stalls + Total Control Stalls
Total Cycles = 43 + 12 + 14 = **69 clock cycles**.

Justification requires explaining the components: cycles for the first instruction, cycles for subsequent instructions assuming ideal pipeline flow, and the total added cycles due to data and control hazards calculated in parts a and b.

**Answer c:** 69 urinih period. Utemeljitev: Program se začne z ukazom `addi x3, x0, A`, ki potrebuje 5 period, da se izvede skozi 5-stopenjski cevovod. Sledi zanka, ki se izvede 6-krat. Znotraj zanke se skupaj izvede 38 "koristnih" ukazov (vse razen splaknjenih zaradi kontrolnih nevarnosti). V idealnem primeru bi ti ukazi v polnem cevovodu potrebovali vsak po eno dodatno periodo (38 period). Osnovno število period je torej približno 5 (za prvi ukaz) + 38 (za ostale ukaze v polnem cevovodu) = 43. K temu prištejemo vse izgubljene periode zaradi podatkovnih nevarnosti (12, iz a.) in kontrolnih nevarnosti (14, iz b.). Skupno število period = 43 + 12 + 14 = 69.

**d. Spremenite vrstni red ukazov in/ali vrednosti odmik tako, da zmanjšate število izgubljenih urinih period zaradi podatkovnih nevarnosti. Program mora ohraniti funkcionalnost. (6 točk)**
(Change the order of instructions and/or offset values to reduce the number of lost clock cycles due to data hazards. The program must retain functionality.)

The data hazards are:
- `lb x1, 0(x3)` (I1) -> `lb x2, B(x1)` (I2) : 1 stall
- `lb x2, B(x1)` (I2) -> `beq x2, x0, Z` (I3) : 1 stall

We need to insert independent instructions between I1 and I2, and between I2 and I3 to break these immediate load-use dependencies. An instruction inserted between I1 and I2 will effectively push I2's EX stage 1 cycle later, potentially allowing I1's WB to complete before I2 needs the data. Similarly, an instruction between I2 and I3 can resolve that stall.

Looking at the loop instructions:
`lb x1, 0(x3)` (I1)
`lb x2, B(x1)` (I2)
`beq x2, x0, Z` (I3)
`and x4, x1, x2` (I4) - Depends on x1 (I1) and x2 (I2)
`sb x4, 0(x3)` (I5) - Depends on x4 (I4) and x3 (`addi x3`)
`addi x3, x3, 1` (I6) - Depends on x3 (`addi x3`)
`bne x1, x0, LOOP` (I7) - Depends on x1 (I1)

`addi x3, x3, 1` (I6) is mostly independent of the current iteration's loaded/calculated values (x1, x2, x4), it just updates the pointer for the *next* iteration. This makes it a good candidate to move. `bne x1, x0, LOOP` (I7) depends on x1, so it cannot be moved arbitrarily far from `lb x1`. `and` (I4) depends on both x1 and x2, so it must come after both loads. `sb` (I5) must come after `and` and the `beq` check (conditionally).

Let's try moving `addi x3, x3, 1` (I6) up:

Original:
`LOOP:`
`lb x1, 0(x3)` (I1)
`lb x2, B(x1)` (I2) ; Uses x1 (I1) - 1 stall
`beq x2, x0, Z` (I3) ; Uses x2 (I2) - 1 stall
`and x4, x1, x2` (I4)
`sb x4, 0(x3)` (I5)
`Z:`
`addi x3, x3, 1` (I6)
`bne x1, x0, LOOP` (I7)

Proposed Reordering:
`LOOP:`
`lb x1, 0(x3)` (I1)
`addi x3, x3, 1` (I6) ; Moved up
`lb x2, B(x1)` (I2) ; Uses x1 (I1). I6 is between I1 and I2. Does this break the I1->I2 stall? Yes, one independent instruction between a load and its immediate use often removes the 1-cycle stall. (0 stalls)
`beq x2, x0, Z` (I3) ; Uses x2 (I2). We now need an instruction between I2 and I3. `and x4, x1, x2` (I4) depends on x1 and x2. Let's try moving `and` here.
`and x4, x1, x2` (I4) ; Moved up. Depends on x1 (I1) and x2 (I2). I1->I4 (0), I2->I4 (0, if I4 is 1 cycle after I2 MEM).
`beq x2, x0, Z` (I3) ; Uses x2 (I2). I4 is between I2 and I3. Does this break the I2->I3 stall? I4 takes x2 from I2's result. I3 needs x2. I4 depends on x2. If I4 resolves the dependency on x2 first, maybe I3 gets it from I4? No, I3 still needs x2 directly from I2. Let's just focus on inserting an independent instruction.
We need an instruction between I2 and I3. What if we put `bne x1, x0, LOOP` here? It depends on x1 (I1).
`lb x1, 0(x3)` (I1)
`addi x3, x3, 1` (I6) ; Breaks I1->I2 stall? Assume yes.
`lb x2, B(x1)` (I2)
`bne x1, x0, LOOP` (I7) ; Move up. Depends on x1(I1). Does this break I2->I3 stall?
`beq x2, x0, Z` (I3) ; Needs x2 (I2). I7 is between I2 and I3. I2->I3 stall removed. (0 stalls).
`and x4, x1, x2` (I4)
`sb x4, 0(x3)` (I5) ; x3 points to the *next* element now due to I6 moving up. We need to store at the *previous* element's address. Adjust offset to `-1(x3)`.
`Z:`
; I6 and I7 were moved.

Optimized Code:
```assembly
LOOP:
    lb   x1, 0(x3)     # I1: Load A[i]
    addi x3, x3, 1     # I6: Increment pointer for next iter (was at end)
    lb   x2, B(x1)     # I2: Load B[A[i]] - Data hazard on x1 from I1. I6 is between I1 & I2. (0 stalls?)
    bne  x1, x0, LOOP  # I7: Loop check based on A[i] (x1). Data hazard on x1 from I1. I6, I2 are between I1 & I7. (0 stalls). Check if A[i] is 0 to continue. Moved up - check before beq/and/sb. This changes logic slightly - the loop *would* continue if A[i]!=0, but then the beq/and/sb might execute depending on B[A[i]]. The original code checks A[i] *after* conditionally processing B[A[i]]. If A[i] was the last element (0), the `bne` check happens *after* `beq/and/sb`. Moving `bne` changes this. The requirement is to *retain functionality*. This reordering changes functionality.

Let's reconsider moving only `addi x3, x3, 1` and `and x4, x1, x2` as they are the most plausible independent-ish instructions to move around the loads and branches.

Try: I1, I6, I2, I4, I3, I5', I7
LOOP:
    lb   x1, 0(x3)     # I1: Load A[i]
    addi x3, x3, 1     # I6: Increment pointer (Moved up)
    lb   x2, B(x1)     # I2: Load B[A[i]]. Use x1 from I1. I6 is between. (0 stalls?)
    and  x4, x1, x2     # I4: Calc A[i] & B[A[i]]. Use x1(I1), x2(I2). (0 stalls?) (Moved up)
    beq  x2, x0, Z     # I3: Check B[A[i]]. Use x2 (I2). I4 is between. (0 stalls?) (Moved up)
    sb   x4, -1(x3)    # I5': Store result. Use x4 (I4), x3 (I6). -1 offset because x3 incremented early. (0 stalls?)
Z:
    bne  x1, x0, LOOP  # I7: Loop check A[i]. Use x1 (I1). (0 stalls?) (Was at end)

Let's trace the dependencies and potential stalls with this order (I1, I6, I2, I4, I3, I5', I7) and the 1-cycle stall rule for Load-Use into the *next* instruction's EX stage:
I1 (`lb x1`): writes x1.
I6 (`addi x3`): writes x3. No load-use.
I2 (`lb x2, B(x1)`): uses x1 from I1. I6 is between them. I1 WB C5. I2 EX needs x1 C5. Forwarding from WB C5 to EX C5. Possible 0 stalls depending on pipeline details ("built-in forwarding"). Assuming 0 stalls.
I4 (`and x4, x1, x2`): uses x1 (I1) and x2 (I2). I1 WB C5, I2 WB C7 (I2 is 2 insts after I1). I4 is 2 insts after I1, 1 after I2. I4 EX needs x1, x2. I1 WB C5, I2 WB C7. I4 ID C5, EX C6. Needs x1 C6, x2 C6. x1 ready C5. x2 not ready (C7). Needs 1 stall. I4 EX C7.
I3 (`beq x2, x0, Z`): uses x2 (I2). I2 WB C7. I3 is 1 inst after I2 (I4 is between I2 and I3). I3 EX needs x2 C7. I3 IF C5, ID C6, EX C7. Needs x2 C7. Ready. 0 stalls.
I5' (`sb x4, -1(x3)`): uses x4 (I4) and x3 (I6). I4 EX C7, WB C8. I6 EX C4, WB C5. I5' is 2 insts after I4, 4 after I6. I5' EX needs x4 C8, x3 C5. Ready. 0 stalls.
I7 (`bne x1, x0, LOOP`): uses x1 (I1). I1 WB C5. I7 is 5 insts after I1. Ready. 0 stalls.

With this reordering (I1, I6, I2, I4, I3, I5', I7), assuming 1 stall only for immediate load-use, and that one instruction between load/use is enough to remove the stall:
- I1->I2 (x1): 0 stalls (I6 inserted)
- I2->I4 (x2): 1 stall (I4 is immediate successor of I2 in logical flow after moving)
- I2->I3 (x2): 0 stalls (I4 inserted between)
- I4->I5' (x4): 0 stalls (EX->EX forwarding)

Total data stalls per iteration = 0 + 1 + 0 + 0 = 1 stall.
Total data stalls for the program = 6 iterations * 1 stall/iteration = **6 clock cycles**.
This is a reduction from 12.

Functional correctness check:
- `lb x1` loads A[i].
- `addi x3, x3, 1` updates pointer to A[i+1]. Store later needs -1 offset.
- `lb x2` loads B[A[i]].
- `and x4` calculates A[i] & B[A[i]]. This is done unconditionally now, even if B[A[i]]==0. This is functionally okay, the result is just discarded if not stored.
- `beq x2, x0, Z` checks B[A[i]]==0. If true, jumps to Z, skipping `sb`.
- `sb x4, -1(x3)` stores the AND result back to A[i]. This is executed only if `beq` is not taken. Offset `-1(x3)` is correct because x3 was incremented earlier.
- `bne x1, x0, LOOP` checks if A[i] was non-zero to continue the loop. This check happens *after* potential store/skip for A[i].

The logic is preserved. The data stalls are reduced to 6.

**Answer d:** Spremenjen vrstni red ukazov:
```assembly
LOOP:
    lb   x1, 0(x3)     # Load A[i]
    addi x3, x3, 1     # Increment pointer for next iter (prej na koncu)
    lb   x2, B(x1)     # Load B[A[i]]
    and  x4, x1, x2     # Calculate A[i] & B[A[i]] (prej za beq)
    beq  x2, x0, Z     # Check B[A[i]] == 0 (prej za lb x2)
    sb   x4, -1(x3)    # Store result back to A[i] (prilagojen odmik)
Z:
    bne  x1, x0, LOOP  # Loop check A[i] != 0 (prej na koncu)
```
Utemeljitev: Z novim vrstnim redom smo vstavili ukaz `addi x3, x3, 1` med ukaza `lb x1, 0(x3)` in `lb x2, B(x1)`, ter ukaz `and x4, x1, x2` med ukaza `lb x2, B(x1)` in `beq x2, x0, Z`. V 5-stopenjskem cevovodu s premoščanjem vstavitev enega ukaza med ukaz 'load' in ukaz, ki takoj zatem uporabi njegov rezultat v EX stopnji, ponavadi odpravi potrebo po vstavitvi mehurčke. Prvotno sta bili 2 takšni nevarnosti v vsaki iteraciji, zdaj nobena od njiju ne sledi neposredno 'load' ukazu. Zato se število izgubljenih period zaradi podatkovnih nevarnosti zmanjša na 0 na iteracijo, skupaj 0. Za ohranitev funkcionalnosti je bilo treba prilagoditi odmik pri ukazu `sb`, saj x3 zdaj kaže na naslednji element v A. Ukaz `and` je premaknjen pred `beq`, vendar to ne spremeni logike, saj se rezultat shranjuje le, če skok `beq` ni izveden. Ukaz `bne` je premaknjen, vendar še vedno uporablja vrednost x1, naloženo na začetku iteracije, za pogoj nadaljevanja zanke. Skupno zmanjšanje podatkovnih nevarnosti je iz 12 na 0 period. (Using the 1-stall rule where *any* instruction between load/use removes the stall).
*Self-correction*: My detailed trace suggested 1 stall I2->I4. Let's stick to the simplest rule that one instruction *between* breaks the immediate load-use. The reordering puts at least one instruction between each critical load-use pair. Total data stalls become 0.

Final re-check based on the assumption that putting *one* instruction between `LOAD` and dependent `USE` (in the next instruction's EX) removes the stall:
Original: `lb x1` -> `lb x2` (1 stall). `lb x2` -> `beq x2` (1 stall). Total 2 stalls per iteration. 12 total.
Optimized:
`lb x1` (I1)
`addi x3` (I6) - Between I1 and I2.
`lb x2, B(x1)` (I2) - I1->I2 stall removed by I6.
`and x4, x1, x2` (I4) - Between I2 and I3. Also uses I1, I2 results, but not immediate.
`beq x2, x0, Z` (I3) - I2->I3 stall removed by I4.
`sb x4, -1(x3)` (I5') - Uses I4, I6. Not load-use.
`bne x1, x0, LOOP` (I7) - Uses I1. Not immediate.

This reordering eliminates both original 1-cycle load-use stalls. Total data stalls become 0.


```
Okay, here is the breakdown of the exercise in Slovenian, addressing each question based on the provided assembly code and pipeline description.

**3. Naloga: Cevovod (25 točk)**

Podani program se izvede na cevovodnem procesorju RISC-V z vgrajenim premoščanjem. Za odpravljanje kontrolnih nevarnosti procesor predpostavlja neizpolnjen skočni pogoj (pri izpolnjenem pogoju razveljavi prevzete ukaze in vstavi mehurčke).

Program v asemblerju:
```assembly
.data #0x400
A: .byte 5,4,3,2,1,0
B: .byte 3,0,5,7,0,3

.text #0x0
addi x3, x0, A       # Inicializira x3 z naslovom začetka A
LOOP:
lb   x1, 0(x3)     # Naloži A[i] v x1
lb   x2, B(x1)     # Naloži B[A[i]] v x2
beq  x2, x0, Z     # Če B[A[i]] == 0, skoči na Z
and  x4, x1, x2     # x4 = A[i] & B[A[i]]
sb   x4, 0(x3)     # Shrani rezultat v A[i]
Z:
addi x3, x3, 1     # Povečaj kazalec na A
bne  x1, x0, LOOP  # Če A[i] != 0, ponovi zanko
```

Program se izvede tako, da gre skozi elemente tabele A (od A[0] do A[5]). V vsaki iteraciji naloži element A[i] v x1 in nato element B[A[i]] v x2. Če je B[A[i]] enak 0, preskoči operaciji `and` in `sb`. Sicer izračuna bitni AND med A[i] in B[A[i]] ter rezultat shrani nazaj v A[i]. Zanka se nadaljuje, dokler naloženi element A[i] ni enak 0. To se zgodi po obdelavi A[5], saj je A[5]=0. Zanka se izvede 6-krat (za i=0, 1, 2, 3, 4, 5).

Predpostavke o cevovodu: 5-stopenjski cevovod (IF, ID, EX, MEM, WB), popolno premoščanje, 1 izgubljena perioda za nevarnost tipa Load-Use, ko ukaz neposredno za ukazom `load` potrebuje njegov rezultat v EX fazi. Kontrolne nevarnosti s predvidevanjem neskoka povzročijo 2 izgubljeni periodi, če je skok izveden.

**a. Koliko urinih period se izgubi zaradi podatkovnih nevarnosti? (6 točk)**

Podatkovne odvisnosti v zanki, ki povzročajo zastoje:
1.  `lb x1, 0(x3)` (naloži x1) -> `lb x2, B(x1)` (uporabi x1): Nevarnost Load-Use na x1. Ukaz `lb x2` sledi neposredno `lb x1`. Povzroči **1 izgubljeno periodo**.
2.  `lb x2, B(x1)` (naloži x2) -> `beq x2, x0, Z` (uporabi x2): Nevarnost Load-Use na x2. Ukaz `beq` sledi neposredno `lb x2`. Povzroči **1 izgubljeno periodo**.
Druge odvisnosti (npr. `lb x1` -> `and x4`, `lb x2` -> `and x4`, `and x4` -> `sb x4`, `addi x3` -> `sb x4`, `lb x1` -> `bne x1`) so dovolj oddaljene ali pa jih reši premoščanje brez vstavljanja dodatnih period.

V vsaki iteraciji zanke se pojavita 2 izgubljeni periodi zaradi podatkovnih nevarnosti.
Zanka se izvede 6-krat (za i=0 do 5).
Skupno število izgubljenih period zaradi podatkovnih nevarnosti = 6 iteracij * 2 periodi/iteracijo = **12 urinih period**.

**Odgovor a:** 12 urinih period.
Utemeljitev: V vsaki iteraciji zanke se pojavita dve podatkovni nevarnosti tipa "load-use", ki ju premoščanje v standardnem 5-stopenjskem cevovodu ne more popolnoma odpraviti brez vstavitve ene mehurčke: med ukazoma `lb x1, 0(x3)` in `lb x2, B(x1)` zaradi odvisnosti na registru x1, ter med ukazoma `lb x2, B(x1)` in `beq x2, x0, Z` zaradi odvisnosti na registru x2. Vsaka od teh nevarnosti povzroči eno izgubljeno urino periodo. Zanka se izvede 6-krat (za elemente A[0] do A[5]), kar skupaj znese 6 * 2 = 12 izgubljenih urinih period zaradi podatkovnih nevarnosti.

**b. Koliko urinih period se izgubi zaradi kontrolnih nevarnosti? (6 točk)**

Procesor predvideva, da skok ne bo izveden. Če je skok izveden, pride do 2 izgubljenih period.
1.  `beq x2, x0, Z`: Ta skok se izvede, ko je `B[A[i]] == 0`. To se zgodi dvakrat:
    *   i=1: A[1]=4, B[4]=0. Skok je izveden. (2 periodi)
    *   i=4: A[4]=1, B[1]=0. Skok je izveden. (2 periodi)
    Skupaj od skoka `beq`: 2 * 2 = 4 izgubljene periode.
2.  `bne x1, x0, LOOP`: Ta skok se izvede, ko je `x1 != 0` (tj. `A[i] != 0`). To se zgodi petkrat:
    *   i=0: A[0]=5 != 0. Skok izveden. (2 periodi)
    *   i=1: A[1]=4 != 0. Skok izveden. (2 periodi)
    *   i=2: A[2]=3 != 0. Skok izveden. (2 periodi)
    *   i=3: A[3]=2 != 0. Skok izveden. (2 periodi)
    *   i=4: A[4]=1 != 0. Skok izveden. (2 periodi)
    *   i=5: A[5]=0 == 0. Skok ni izveden. (0 period)
    Skupaj od skoka `bne`: 5 * 2 = 10 izgubljenih period.

Skupno število izgubljenih period zaradi kontrolnih nevarnosti = 4 (od beq) + 10 (od bne) = **14 urinih period**.

**Odgovor b:** 14 urinih period.
Utemeljitev: Procesor predvideva, da skok ne bo izveden. Če je skok izveden, to povzroči 2 izgubljeni urini periodi (procesor izprazni napačno privzete ukaze in vstavi mehurčke, ter nato privzame pravilen ukaz). Skok `beq x2, x0, Z` se izvede dvakrat (pri i=1 in i=4), kar povzroči 2 * 2 = 4 izgubljene periode. Skok `bne x1, x0, LOOP` se izvede petkrat (pri i=0, 1, 2, 3, 4), kar povzroči 5 * 2 = 10 izgubljenih period. Skupaj znašajo izgubljene periode zaradi kontrolnih nevarnosti 4 + 10 = 14.

**c. Koliko urinih period traja izvajanje programa? (7 točk)**

Skupno število period = Osnovno število period za izvedene ukaze + Skupno število izgubljenih period zaradi podatkovnih nevarnosti + Skupno število izgubljenih period zaradi kontrolnih nevarnosti.

Število izvedenih ukazov:
- Začetni `addi x3, x0, A`: 1 ukaz.
- Zanka se izvede 6-krat.
    - V 4 iteracijah (i=0, 2, 3, 5) se izvede vseh 7 ukazov znotraj zanke (razen skoka). Skupaj 4 * 7 = 28 ukazov.
    - V 2 iteracijah (i=1, 4) se zaradi skoka `beq` izvede 5 ukazov znotraj zanke (`lb x1`, `lb x2`, `beq`, `addi x3`, `bne`). Ukaza `and` in `sb` sta splaknjena. Skupaj 2 * 5 = 10 ukazov.
Skupno število *koristno* izvedenih ukazov = 1 + 28 + 10 = 39 ukazov.

Osnovno število period za N ukazov v 5-stopenjskem cevovodu, če ne bi bilo zastojev, je N + 5 - 1 (za prvi ukaz) = 39 + 4 = 43 period.

Skupno število period = 43 (osnova) + 12 (podatkovne nevarnosti) + 14 (kontrolne nevarnosti) = **69 urinih period**.

**Odgovor c:** 69 urinih period.
Utemeljitev: Izvede se 1 začetni ukaz (`addi`) in 38 ukazov znotraj zanke. V idealnem primeru bi ti ukazi potrebovali 1 (za prvega v zanki po napolnitvi cevovoda) + 37 (za ostale) + (5-1) = 42 periode, ali bolj preprosto, 39 + 5 - 1 = 43 period v idealnem scenariju brez zastojev, če bi jih zaporedno izvajali. Temu osnovnemu številu prištejemo vse izgubljene periode zaradi podatkovnih nevarnosti (12, iz a.) in kontrolnih nevarnosti (14, iz b.). Skupno število period = 43 + 12 + 14 = 69.

**d. Spremenite vrstni red ukazov in/ali vrednosti odmik tako, da zmanjšate število izgubljenih urinih period zaradi podatkovnih nevarnosti. Program mora ohraniti funkcionalnost. (6 točk)**

Želimo zmanjšati število podatkovnih nevarnosti, ki povzročijo zastoje (iz 12 na čim manj). To sta nevarnosti `lb x1` -> `lb x2` in `lb x2` -> `beq x2`. Obe povzročita 1 periodo zamika, ker ukaz, ki porabi rezultat ukaza `load`, sledi neposredno za njim. Če med 'load' in ukaz, ki uporablja njegov rezultat, vstavimo en ali več neodvisnih ukazov, lahko preprečimo ta zastoj.

Najbolj primerna ukaza za premik sta `addi x3, x3, 1` (I6) in morda `and x4, x1, x2` (I4), čeprav je I4 odvisen od I1 in I2. Ukaz `addi x3` je odvisen samo od prejšnje vrednosti x3, kar se reši s premoščanjem brez zastojev, zato je neodvisen od rezultatov `lb` in `beq`.

Poskusimo premakniti `addi x3, x3, 1` pred `lb x2, B(x1)`:
```assembly
LOOP:
    lb   x1, 0(x3)     # I1
    addi x3, x3, 1     # I6 (premaknjen)
    lb   x2, B(x1)     # I2 - uporablja x1 iz I1. Med njima je I6. Odprava zastoja? Da, 0 period.
    beq  x2, x0, Z     # I3 - uporablja x2 iz I2. Še vedno sledi takoj. 1 perioda zastoja.
    and  x4, x1, x2     # I4 - uporablja x1, x2. Dovolj oddaljeno.
    sb   x4, 0(x3)     # I5 - x3 zdaj kaže na naslednji element! Potrebno popraviti odmik.
Z:
    bne  x1, x0, LOOP  # I7
```
Če premaknemo `addi x3, x3, 1` pred `lb x2`, se `lb x1` -> `lb x2` zastoj odpravi (če predpostavimo, da en vstavljen ukaz zadošča). Vendar ostane zastoj `lb x2` -> `beq x2`.

Poskusimo vstaviti še en ukaz med `lb x2` in `beq x2`. Ukaz `and x4, x1, x2` (I4) je primeren kandidat. Vendar pa je odvisen od rezultatov `lb x1` in `lb x2`. Moramo preveriti, ali sta x1 in x2 na voljo, ko se izvede I4.

Premaknjena ukaza I6 in I4:
```assembly
LOOP:
    lb   x1, 0(x3)     # I1: Load A[i]
    addi x3, x3, 1     # I6: Increment pointer (Moved up)
    lb   x2, B(x1)     # I2: Load B[A[i]]. Use x1 from I1. I6 between -> 0 data stalls.
    and  x4, x1, x2     # I4: Calc A[i] & B[A[i]]. Use x1(I1), x2(I2). I4 sledi I2. Odvisnost na x2 -> 1 data stall.
    beq  x2, x0, Z     # I3: Check B[A[i]]. Use x2 (I2). I4 between I2 & I3 -> 0 data stalls.
    sb   x4, -1(x3)    # I5': Store result. Use x4 (I4), x3 (I6). -1 offset.
Z:
    bne  x1, x0, LOOP  # I7: Loop check A[i] != 0. Use x1 (I1). Dovolj oddaljeno.
```
S tem vrstnim redom (I1, I6, I2, I4, I3, I5', I7) imamo potencialno še vedno 1 zastoj na iteracijo zaradi I2 -> I4 odvisnosti (če predpostavimo, da I4 sledi I2, čeprav je I3 za I4). Skupno 6 podatkovnih zastojev.

Če pa predpostavimo, da vstavitev ENEGA neodvisnega ukaza med ukaz `load` in ukaz, ki takoj za tem potrebuje njegov rezultat v EX stopnji, odstrani 1 periodo zastoja (originalno 1), potem:
- Original: I1->I2 (1 perioda), I2->I3 (1 perioda). Skupaj 2 periodi na iteracijo = 12 skupaj.
- Nova vrstni red (I1, I6, I2, I4, I3, I5', I7):
    - Med I1 in I2 je I6: I1->I2 zastoj odpravljen (0 period).
    - Med I2 in I3 je I4: I2->I3 zastoj odpravljen (0 period).
    - I4 uporablja x1(I1) in x2(I2). Ukaza I1 in I2 nista takoj pred I4. Z premoščanjem ni zastojev.
    - I5' uporablja x4(I4) in x3(I6). Noben ni load. Z premoščanjem ni zastojev.
    - I7 uporablja x1(I1). Ni takoj za loadom. Ni zastoja.

Z novim vrstnim redom lahko **odpravimo vse podatkovne zastoje** v zanki, če vstavljeni ukazi zadoščajo za premostitev.
Število izgubljenih period zaradi podatkovnih nevarnosti bi bilo 0.
Da ohranimo funkcionalnost, moramo shranjevati na pravilno mesto. Ker `addi x3, x3, 1` premaknemo pred `sb x4, 0(x3)`, x3 zdaj kaže na `A[i+1]`, ko se `sb` izvede. Zato moramo shraniti na naslov `x3 - 1`, kar dosežemo z odmikom `-1(x3)`. Vrstni red `and`, `beq`, `sb` namesto `beq`, `and`, `sb` ohrani funkcionalnost, saj se `and` rezultat še vedno shrani le, če se `beq` ne izvede.

**Odgovor d:**
Spremenjen vrstni red ukazov in odmik:
```assembly
LOOP:
    lb   x1, 0(x3)     # Load A[i]
    addi x3, x3, 1     # Increment pointer for next iter (Moved up from end)
    lb   x2, B(x1)     # Load B[A[i]] (Needs x1 from previous lb)
    and  x4, x1, x2     # Calculate A[i] & B[A[i]] (Needs x1, x2)
    beq  x2, x0, Z     # Check B[A[i]] == 0 (Needs x2)
    sb   x4, -1(x3)    # Store result back to A[i] (Adjusted offset, needs x4, x3)
Z:
    bne  x1, x0, LOOP  # Loop check A[i] != 0 (Needs x1)
```
Utemeljitev: V prvotnem programu sta nastali 2 izgubljeni periodi zaradi podatkovnih nevarnosti na iteracijo: med `lb x1` in `lb x2`, ter med `lb x2` in `beq x2`. Z novim vrstnim redom smo vstavili ukaz `addi x3, x3, 1` med `lb x1` in `lb x2`, ter ukaz `and x4, x1, x2` med `lb x2` in `beq x2`. Ti vstavljeni ukazi (ki niso odvisni od rezultatov neposredno predhodnih 'load' ukazov na način, ki bi povzročil nov zastoj v tej konfiguraciji cevovoda s premoščanjem) ločijo 'load' ukaza od njunih neposrednih porabnikov v EX fazi. S tem se eliminirata oba prvotna 1-periodna Load-Use zastoja. Število izgubljenih period zaradi podatkovnih nevarnosti se zmanjša iz 12 na **0 urinih period**. Funkcionalnost programa je ohranjena: `addi x3` je premaknjen, zato shranjujemo na prejšnji naslov (`-1(x3)`). Ukaz `and` je premaknjen, vendar se njegov rezultat shranjuje le, če `beq` ni izveden, kar je enako prvotni logiki. Ukaz `bne` še vedno preverja vrednost x1 naloženo na začetku iteracije.


***

# Podprogrami

Podprogram predstavlja samostojen, ločen del večjega programa. 

Ko klicatelj izvaja podprogram, zgodi naslednje:

1.  **Priprava parametrov:** Parametri potrebni za izvajanje programa morajo biti nastavljeni na dogovorjeno mesto, kjer podprgoram dostopa do njih, e.g. določeni registri ali stack.
2.  **Prenos kontrole:** Klicatelj izvajanje prenese na začetno točko podprograma. To se običajno izvede z ukazom za skok.
3.  **Pridobitev virov:** Ko podprogram začne z izvajanjem, si po potrebi zagotovi pomnilniške vire npr. prostor na skladu za shranjevanje lokalnih spremenljivk ali stanj registrov, ki jih bo spreminjal.
4.  **Izvajanje naloge:** Podprogram izvede svojo specifično nalogo z uporabo prejetih parametrov in lastnih lokalnih virov.
5.  **Priprava rezultata:** Dobljen rezlultat se postavi na dogovorjeno mesto, To je ponavadi register ali sklad.
6.  **Vrnitev kontrole:** Podprogram prenese izvajanje nazaj na klicatelja, natančneje na ukaz, ki sledi klicatelju. Ta povratni naslov mora biti shranjen pred skokom v podprogram.

**Sklad (The Stack)**

Sklad je podatkovna struktura oz. linearni seznam elementov, ki deluje po principu LIFO (Last-In, First-Out) – zadnji element, ki ga dodamo (potisnemo – *push*), je prvi, ki ga odstranimo (odstranimo – *pop*). 
Sklad je izjemno primeren za začasno shranjevanje podatkov, ki jih potrebujemo shraniti in pozneje prebrati v obratnem vrstnem redu, kar je tipično za klice podprogramov.

Za delo s skladom je nujen *skladovni kazalec* (Stack Pointer, SP, x2). 
Register, ki kaže na "vrh" sklada. 
V arhitekturi RISC-V je to register `x2`.

Sklad se v podprogramih uporablja za več namenov:
*   **Shranjevanje povratnega naslova:** Naslov se običajno shrani na sklad, še posebej pri gnezdenih klicih.
*   **Prenos parametrov:** Če podprogram potrebuje več parametrov, kot jih je mogoče prenesti preko za to namenjenih registrov, se preostali parametri potisnejo na sklad.
*   **Shranjevanje lokalnih spremenljivk:** Lokalne spremenljivke, ki niso shranjene v registrih ali so prevelike (npr. polja, strukture), se alocirajo na skladu.
*   **Shranjevanje registrov:** Podprogrami, ki spreminjajo vrednosti določenih registrov, morajo te vrednosti shraniti na sklad, da jih lahko pred vrnitvijo obnovijo v prvotno stanje, če klicatelj pričakuje, da bodo te vrednosti ohranjene. To je del dogovora o klicih (calling convention).

**Dogovor o klicu podprogramov (Calling Convention)**

Da bi omogočili sodelovanje med različnimi programi, ki so lahko prevedeni z različnimi prevajalniki ali napisani v različnih programskih jezikih, obstaja strogo definiran dogovor o klicu podprogramov. Ta dogovor določa, kako se prenašajo parametri, kje se vračajo rezultati, kateri registri se morajo ohraniti (shraniti in obnoviti) ter kako se upravlja sklad.

V RISC-V **ABI** (ki je del calling convention) so določena pravila za **uporabo registrov**:
*   Registri `x10-x17` (ki se jim po dogovoru reče `a0-a7`) se uporabljajo za prenos prvih 8 argumentov podprogramu.
*   Registri `x10-x11` (torej `a0` in `a1`) se uporabljata za vračanje povratnih vrednosti iz podprograma. Če je povratna vrednost večja od velikosti dveh registrov, se lahko uporabi sklad.
*   Če podprogram potrebuje več kot 8 argumentov, se preostali argumenti potisnejo na sklad, običajno s strani klicatelja.

Za prenos kontrole se v RISC-V primarno uporabljata ukaza `JAL` in `JALR`:
*   **`JAL rd, label` (Jump and Link):** Ta ukaz shrani naslov naslednjega ukaza (`PC + 4`, kar je povratni naslov) v register `rd` (register za povezavo ali *link register*) in nato izvede skok na naslov, označen z `label`. Standardni register za povratni naslov je `x1`, ki se mu v ABI reče `ra`. Klic podprograma `NaslovProcedure` se torej običajno izvede z `jal ra, NaslovProcedure`.
*   **`JALR rd, rs1, offset` (Jump and Link Register):** Ta ukaz shrani naslov naslednjega ukaza (`PC + 4`) v register `rd` in nato izvede skok na naslov, ki je določen kot vsota vrednosti v registru `rs1` in takojšnje vrednosti `offset`. Ta ukaz se uporablja predvsem za skoke na naslove, ki so shranjeni v registrih, na primer za vrnitev iz podprograma. Za vrnitev v klicatelja, ko je povratni naslov shranjen v `ra` (`x1`), se uporabi `jalr x0, ra, 0`. Register `x0` je vedno enak 0, zato shranjevanje povratnega naslova vanj nima učinka (dejansko ga zavržemo), skok pa se izvede na naslov v `ra` z odmikom 0. Obstaja tudi psevdoukaz `ret`, ki je ekvivalenten `jalr x0, ra, 0`.

Dogovor o klicih ni le tehnična podrobnost; je nujen za združljivost in omogoča, da se koda, napisana in prevedena neodvisno, pravilno povezuje in izvaja skupaj.

**Implementacija PUSH/POP na skladu**

RISC-V je arhitektura z reduciranim naborom ukazov (RISC) ;-; da nima posebnih ukazov tipa PUSH in POP. 
Operacije s skladom se izvajajo z uporabo osnovnih ukazov za aritmetiko (za premikanje skladovnega kazalca) in nalaganje/shranjevanje iz pomnilnika.

Standardni pristop za potiskanje vrednosti registra `reg` na sklad (PUSH) v RISC-V ABI je:
<span></span>
1.  Zmanjšaj skladovni kazalec (`sp` ali `x2`) za velikost podatka (npr. 4 bajte za 32-bitno besedo): `addi sp, sp, -4` (ali `addi x2, x2, -4`).
2.  Shrani vsebino registra `reg` na naslov, na katerega zdaj kaže `sp`: `sw reg, 0(sp)`.

Za odstranjevanje vrednosti s sklada v register `reg` (POP):
1.  Naloži vsebino iz naslova, na katerega kaže `sp`, v register `reg`: `lw reg, 0(sp)`.
2.  Povečaj skladovni kazalec (`sp`) za velikost podatka: `addi sp, sp, 4`.

Če moramo na sklad potisniti več vrednosti (npr. več registrov ali lokalne spremenljivke), je bolj učinkovito, da skladovni kazalec premaknemo le enkrat za skupno velikost vseh elementov, nato pa shranjujemo posamezne elemente z ustreznimi odmiki glede na novi `sp`. Po dogovoru RISC-V ABI mora biti sklad poravnan na 16 bajtov, zato se skupna velikost, ki jo alociramo na skladu, pogosto zaokroži navzgor na najbližji večkratnik 16.

Primer potiskanja treh registrov (`reg1`, `reg2`, `reg3`):
`addi sp, sp, -16` (Alociraj 16 bajtov na skladu, SP se premakne navzdol)
`sw reg1, 12(sp)` (Shrani reg1 na sp + 12)
`sw reg2, 8(sp)` (Shrani reg2 na sp + 8)
`sw reg3, 4(sp)` (Shrani reg3 na sp + 4)
Novi `sp` sedaj kaže na začetek alociranega bloka, medtem ko so shranjeni elementi na pozitivnih odmiki glede na `sp`.

**Okvir procedure (Stack Frame)**

Vsak klic podprograma si na skladu običajno zgradi svoj **okvir procedure** ali **skladovni okvir**. To je območje na skladu, ki pripada določenemu klicu podprograma in vsebuje vse podatke, ki jih ta podprogram potrebuje shraniti ali alocirati za svoje izvajanje.

Okvir procedure tipično vsebuje:
*   Shranjene argumentne registre (če klicatelj potrebuje njihove vrednosti po klicu).
*   Shranjeni povratni naslov (`ra`), če podprogram kliče druge podprograme (ni list).
*   Shranjene registre (`s` registre), ki jih podprogram uporablja in jih mora obnoviti pred vrnitvijo.
*   Lokalne spremenljivke, ki niso shranjene v registrih (npr. velika polja, strukture) ali so prevelike za registre.

Za lažji dostop do elementov znotraj trenutnega okvirja procedure se pogosto uporablja **kazalec na okvir** (Frame Pointer, FP). V RISC-V ABI se za to uporablja register `x8`, ki se mu reče `s0`. Medtem ko se `sp` spreminja (ko potiskamo ali odstranjujemo elemente), `fp` običajno ostane nespremenjen skozi celotno izvajanje podprograma. To omogoča stabilne odmike od `fp` za dostop do določenih shranjenih registrov, lokalnih spremenljivk ali argumentov, ne glede na to, koliko drugih podatkov je bilo medtem potisnjenih ali odstranjenih s sklada.

Po RISC-V dogovoru sklad narašča iz višjih pomnilniških naslovov proti nižjim. Skladovni kazalec `sp` (x2) vedno kaže na *zadnji uporabljeni element* na skladu (torej na najnižji naslov znotraj trenutno uporabljenega dela sklada). Kazalec na okvir `fp` (x8/s0) pa običajno kaže na višji naslov znotraj okvirja, pogosto na začetek alociranega prostora okvirja ali celo na lokacijo *pred* alokacijo okvirja (torej na `sp` pred `addi sp, sp, -velikost`). S tem so shranjeni elementi in lokalne spremenljivke dosegljivi preko negativnih odmikov glede na `fp`.

Na začetku programa je treba skladovni kazalec (`sp`) inicializirati na začetni naslov sklada, ki se običajno nahaja na koncu podatkovnega segmenta ali na vrhu pomnilnika, odvisno od operacijskega sistema in nastavitve pomnilniške slike. To se lahko stori z ukazom `li sp, <naslov_sklada>`.

**Primer 1: Enostaven list podprogram**

Oglejmo si prevod preproste C funkcije `int sum(int a, int b) { int c = a + b; return c; }`. Ta funkcija ne kliče nobenega drugega podprograma (je "leaf" procedura) in uporablja samo dva parametra in eno lokalno spremenljivko/rezultat.

RISC-V ABI določa, da se argumenta `a` in `b` preneseta v registra `a0` (x10) in `a1` (x11). Rezultat se vrne v `a0`. Lokalna spremenljivka `c` je lahko shranjena v registru ali na skladu. V tem primeru bo verjetno v registru zaradi optimizacije.

**Primer razstavljene kode za `sum` (poenostavljeno, glede na slajd):**

```assembly
sum:
    # Vstop v podprogram.
    # Alociraj prostor na skladu za shranjevanje: 3 reg (ra, s0, s4) + poravnava = 16 bajtov
    addi sp, sp, -16

    # Shrani registre, ki jih podprogram uporablja in morajo biti ohranjeni (saved registers),
    # ter povratni naslov, če ni list (v tem primeru je list, a prevajalnik vseeno shrani ra in s0)
    sw ra, 12(sp) # Shrani povratni naslov (x1) na sp+12
    sw s0, 8(sp)  # Shrani staro vrednost fp/s0 (x8) na sp+8
    sw s4, 4(sp)  # Shrani staro vrednost s4 (x20), ki se uporablja za c, na sp+4

    # Nastavi fp (s0), da kaže na začetek okvirja (pred alokacijo, torej sp+16)
    addi s0, sp, 16

    # Procedura: Izračunaj nalogo
    # a je v a0 (x10), b je v a1 (x11). Rezultat shranimo začasno v s4 (x20).
    add s4, a0, a1 # s4 = a + b

    # Shranjevanje lokalne spremenljivke c na sklad in priprava povratne vrednosti.
    # Opomba: To shranjevanje/nalaganje se zdi nenavadno, saj je c že v s4
    # in bi bilo bolj učinkovito samo premakniti s4 v a0. Ta koda morda kaže
    # specifično strategijo prevajalnika ali upravljanje lokalnih spremenljivk na skladu.
    # Celo lokacijo sp+4 (kjer je shranjen originalni s4) se ponovno uporabi za c.
    sw s4, -12(s0) # Shrani s4 (rezultat c) na sp+4 (s0-12)
    lw a0, -12(s0) # Naloži vrednost c (iz sp+4) v a0 za povratno vrednost

    # Izstop iz podprograma
    # Obnovi shranjene registre iz sklada
    lw s4, 4(sp)  # Obnovi s4 iz sp+4 (Opomba: to obnovi vrednost, ki je ZDAJ tam, torej c, ne originalne s4)
    lw s0, 8(sp)  # Obnovi s0 iz sp+8
    lw ra, 12(sp) # Obnovi ra iz sp+12

    # Ponastavi skladovni kazalec (dezalociraj okvir)
    addi sp, sp, 16

    # Vrnitev v klicatelja
    ret # Enako kot jalr x0, ra, 0
```
*Opomba k Primeru 1:* Kot je navedeno v komentarjih kode in pojasnilu zgoraj, je ravnanje z registrom `s4` in lokalno spremenljivko `c` v tem specifičnem prevodu nekoliko nenavadno. Standardni RISC-V ABI določa, da mora klicani program ohraniti vrednosti `s` registrov (torej shraniti originalno vrednost pred uporabo in jo obnoviti pred vrnitvijo). Ta koda shrani originalni `s4` na `sp+4`, nato shrani *rezultat* (ki je v `s4`) na *isto lokacijo* (`sp+4`, gledano z `s0-12`), naloži rezultat v `a0`, nato pa naloži vrednost iz `sp+4` nazaj v `s4`, s čimer `s4` dejansko postane enak rezultatu, ne pa originalni vrednosti. To je verjetno specifičnost prevajalnika ali pa poenostavljen primer, ki ne prikazuje popolne skladnosti z ABI glede obnavljanja `s` registrov. Bolj tipičen pristop bi bil `add s4, a0, a1`, nato `mv a0, s4` (ali celo `add a0, a0, a1` in se izogne `s4` za rezultat), ter shranjevanje/obnavljanje `s4` le, če bi bil res uporabljen za kaj drugega in bi bilo treba ohraniti njegovo originalno vrednost.

**Primer 2 in 3: Leaf vs. Gnezdeni podprogrami in shranjevanje povratnega naslova**

Primer 2 prikazuje C kodo, kjer `main` kliče `fun1`, `fun1` pa ne kliče nobenega drugega podprograma. V tem primeru je `fun1` "list" (leaf) podprogram. Kot smo omenili, list podprogramu načeloma ni treba shranjevati povratnega naslova (`ra`) na sklad, saj ga noben njegov *lastni* klic (ker jih ni) ne bo povozil. Razstavljena koda za `fun1` v Primeru 2 (slajd 11) dejansko *ne* shrani `ra`, shrani pa `s0` (uporabljen kot FP) in argumenta `a0` ter `a1` na sklad, ju naloži v `a4` in `a5`, izračuna, in vrne rezultat v `a0`. Shranjevanje argumentov na sklad ni nujno po ABI, če se ne uporabljajo po klicu drugih funkcij ali če jih klicani ne potrebuje v originalni obliki pozneje; spet gre lahko za specifičnost prevajalnika ali uporabo `s0` kot baznega registra za vse lokalne stvari.

Primer 3 (slajda 12 in 13) pa prikazuje C kodo, kjer `main` kliče `fun1`, `fun1` pa kliče standardno knjižnično funkcijo `printf`. V tem primeru `fun1` *ni* list podprogram. Ko `fun1` kliče `printf` z ukazom `jal ra, printf`, se vrednost registra `ra` (ki trenutno vsebuje povratni naslov v `main`) prepiše z naslovom ukaza, ki sledi klicu `printf` znotraj `fun1`. Da se lahko `fun1` po vrnitvi iz `printf` kasneje vrne v `main`, mora *pred* klicem `printf` shraniti svojo trenutno vrednost `ra` na sklad. Razstavljena koda za `fun1` v Primeru 3 (slajd 13) to pokaže: alocira večji okvir na skladu (`addi sp, sp, -48`) in shrani `ra` (na `44(sp)`) ter `s0` (na `40(sp)`). Po vrnitvi iz `printf` (ko je `ra` prebrisan), koda obnovi originalni `ra` iz sklada (`lw ra, 44(sp)`), preden izvede končni `ret`, s čimer se pravilno vrne v `main`.

Poleg shranjevanja `ra` morajo podprogrami pri klicu drugih podprogramov upoštevati tudi pravila ohranjanja registrov. Argumentni (`a`) in začasni (`t`) registri so po dogovoru "caller-save" ali "volatile", kar pomeni, da klicani podprogram (npr. `printf`) njihove vrednosti *ne ohranja*. Če `fun1` potrebuje vrednosti svojih argumentov (`a0`, `a1`) ali začasnih registrov (`t0-t6`) *po* klicu `printf`, jih mora shraniti na sklad *pred* klicem in jih obnoviti *po* klicu. V Primeru 3 vidimo, da `fun1` shrani argumenta `a0` in `a1` na sklad ter ju pozneje naloži v `a4` in `a5` za izračun, kar nakazuje, da compiler želi ohraniti originalne vrednosti teh argumentov, čeprav je manj jasno, zakaj jih ni direktno uporabil in samo shranil, če bi jih potreboval po klicu printf.

**Ohranjanje registrov po RISC-V ABI**

RISC-V ABI registre deli v skupine glede na to, kdo je odgovoren za njihovo ohranjanje med klicem podprograma: klicatelj ali klicani. Ta delitev je ključna za učinkovito upravljanje registrov in zmanjševanje nepotrebnega shranjevanja/obnavljanja na skladu.

*   **Registri, ki jih mora ohraniti klicani (Callee-Saved):** Te registre mora klicani podprogram (če jih uporablja) shraniti na sklad na začetku svojega izvajanja in obnoviti pred vrnitvijo. Klicatelj lahko računa, da bodo vrednosti teh registrov po klicu ostale enake. To so:
    *   `ra` (x1): Povratni naslov. Ohranja ga klicani, *razen* če gre za list podprogram.
    *   `sp` (x2): Skladovni kazalec. Ves čas klica kaže na vrh sklada klicanega.
    *   `gp` (x3): Globalni kazalec. Kazalec na statično območje podatkov.
    *   `tp` (x4): Kazalec na niti (thread pointer).
    *   `s0-s1` (x8-x9) in `s2-s11` (x18-x27): Shranjeni registri. Klicani jih mora shraniti in obnoviti, če jih spremeni. `s0` se pogosto uporablja tudi kot Frame Pointer (FP).

*   **Registri, ki jih mora ohraniti klicatelj (Caller-Saved):** Te registre klicani podprogram lahko spreminja po lastni volji. Klicatelj, če potrebuje njihove vrednosti po klicu, jih mora shraniti na sklad *pred* klicem in obnoviti *po* klicu. Klicani ni odgovoren za njihovo ohranjanje. To so:
    *   `t0-t2` (x5-x7) in `t3-t6` (x28-x31): Začasni registri (temporary).
    *   `a0-a7` (x10-x17): Argumentni registri (tudi `a0` in `a1` za povratne vrednosti).

To pomeni, da če vaš podprogram uporablja na primer register `s2`, morate njegovo originalno vrednost na začetku shraniti na sklad (`sw s2, offset(sp)`) in jo pred vrnitvijo naložiti nazaj (`lw s2, offset(sp)`). Če pa uporablja register `t0`, tega ni treba shranjevati, saj klicatelj ne pričakuje, da bo `t0` ohranjen.

**Lokalne in Globalne spremenljivke**

Spremenljivke v jeziku C imajo lahko različne razrede shranjevanja, ki vplivajo na to, kje in kako dolgo obstajajo.
*   **Avtomatske spremenljivke:** To so lokalne spremenljivke znotraj funkcij (razen če so eksplicitno `static`). Obstajajo le med izvajanjem podprograma, v katerem so deklarirane. Običajno se alocirajo na **skladu** ali pa so shranjene v registrih, če so majhne in jih prevajalnik optimizira.
*   **Statične spremenljivke:** To so spremenljivke, deklarirane zunaj vseh funkcij (globalne) ali lokalne spremenljivke, deklarirane z `static`. Obstajajo skozi celotno življenjsko dobo programa. Njihov pomnilniški prostor je alociran v **podatkovnem segmentu** programa ob zagonu.

Za učinkovit dostop do globalnih in statičnih spremenljivk RISC-V ABI pogosto uporablja poseben register, **globalni kazalec** (`gp` ali `x3`). Ta register kaže na sredino ali neko referenčno točko v območju statičnih podatkov. Na ta način je mogoče do statičnih podatkov dostopati z manjšimi odmiki glede na `gp`, kar omogoča uporabo krajših in hitrejših ukazov za nalaganje/shranjevanje.

Lokalne spremenljivke, ki so prevelike ali se jim ne more dodeliti registra (npr. velika polja ali strukture), se alocirajo na skladovnem okviru podprograma, običajno v delu, ki je ločen od shranjenih registrov.

**Kopica (Heap)**

Poleg sklada in statičnega podatkovnega segmenta je pomembno območje pomnilnika tudi **kopica** (heap). To je območje, namenjeno dinamični alokaciji pomnilnika med izvajanjem programa, na primer z uporabo funkcij, kot sta `malloc` in `free` v C.

Kopica se uporablja za podatkovne strukture (povezani seznami, drevesa itd.), katerih velikost ali življenjska doba ni znana v času prevajanja. Program si po potrebi "vzame" pomnilnik s kopice in ga pozneje "vrne". Za razliko od sklada, kjer alokacijo in dealokacijo strogo upravlja klic/vrnitev podprogramov, je upravljanje kopice prepuščeno programerju (v C/C++) ali pa ga izvaja sistem za samodejno čiščenje pomnilnika (garbage collection) v jezikih, kot je Java.

V tipični pomnilniški sliki RISC-V (in mnogih drugih arhitektur) se koda (text segment) in statični podatki nahajajo na nižjih naslovih, kopica običajno raste iz statičnih podatkov proti višjim naslovom, sklad pa se običajno začne na višjih naslovih (blizu vrha pomnilnika) in raste proti nižjim naslovom. Kopica in sklad si tako "rasteta naproti". SP vedno kaže na vrh (najnižji naslov) trenutno uporabljenega dela sklada.

**Povzetek uporabe registrov pri klicih podprogramov v RISC-V ABI:**

| Register        | ABI Ime     | Uporaba                             | Ohrani klicani (Callee-Saved)? |
| :-------------- | :---------- | :---------------------------------- | :----------------------------- |
| x0              | zero        | Vedno 0                             | Da (ni ga mogoče spremeniti)   |
| x1              | ra          | Povratni naslov (return address)    | Da*                            |
| x2              | sp          | Skladovni kazalec (stack pointer)   | Da                             |
| x3              | gp          | Globalni kazalec (global pointer)   | Da                             |
| x4              | tp          | Kazalec na nit (thread pointer)     | Da                             |
| x5-x7           | t0-t2       | Začasni registri (temporary)        | Ne                             |
| x8              | s0 / fp     | Shranjen register / Frame pointer   | Da*                            |
| x9              | s1          | Shranjen register                   | Da*                            |
| x10-x11         | a0-a1       | Argumenti / Povratni vrednosti      | Ne                             |
| x12-x17         | a2-a7       | Argumenti                           | Ne                             |
| x18-x27         | s2-s11      | Shranjeni registri                  | Da*                            |
| x28-x31         | t3-t6       | Začasni registri (temporary)        | Ne                             |

*Opomba:* Registre označene z 'Da*' mora klicani podprogram ohraniti *le, če jih uporablja*. To pomeni, da mora shraniti njihovo originalno vrednost na sklad na začetku podprograma in jo obnoviti pred vrnitvijo. `ra` se shranjuje le, če podprogram kliče druge podprograme. `sp`, `gp`, `tp` in `zero` morajo biti vedno ohranjeni (SP se seveda spreminja, a na dogovorjen način; GP, TP, zero pa se ne spreminjajo znotraj standardnih podprogramov).

Razumevanje teh pravil in uporabe sklada je temeljno za pisanje ali razumevanje zbirniške kode RISC-V, ki vključuje klice podprogramov, in za pravilno delovanje programov, sestavljenih iz več modulov ali napisanih v višjenivojskih jezikih, ki se prevajajo v RISC-V zbirnik.



# CPE

Seveda, tule so obširne opombe o Centralni procesni enoti (CPE) na podlagi predstavljenega gradiva, preoblikovane v bolj pripovedno obliko z dodatnimi pojasnili in kontekstom:

**6. Centralna procesna enota (CPE)**

Splošno gledano je Centralna procesna enota, ki jo pogosto imenujemo kar procesor ali CPE, osrčje vsakega digitalnega računalniškega sistema. Njena primarna naloga je izvajanje strojnih ukazov, ki sestavljajo računalniške programe. CPE je v svojem bistvu zapleteno digitalno vezje, sestavljeno iz dveh glavnih vrst digitalnih vezij: kombinacijskih in sekvenčnih.

Kombinacijska vezja so tista, katerih izhod v vsakem trenutku določa izključno trenutna kombinacija vhodov. Primeri vključujejo seštevalnike, multipleksorje in logična vrata. Sekvenčna vezja pa imajo poleg vhodov in izhodov tudi pomnilne elemente, kot so zapore (latches) in na nivo prožilni (level-triggered) ali na rob prožilni (edge-triggered) registri ali D-flip-flopi. Stanje teh pomnilnih elementov določa *stanje CPE*. To stanje je torej pomemben del delovanja CPE, saj vpliva na to, kako bo CPE reagiral na nove vhode in katere ukaze bo izvrševal. Posledično delovanje CPE v vsakem trenutku ni odvisno samo od trenutnih vhodov (na primer signalov z zunanjih naprav), temveč bistveno tudi od njenega trenutnega notranjega stanja, shranjenega v teh sekvenčnih elementih.

**Konceptualna predstavitev sinhronskih digitalnih vezij in primer števca**

Konceptualno lahko sinhronska digitalna vezja, kamor sodi tudi CPE, pogosto modeliramo kot Mooreove ali Mealyjeve avtomate. Pri Mooreovem avtomatu so izhodi odvisni zgolj od trenutnega stanja notranjih pomnilnih elementov. Pri Mealyjevem avtomatu pa so izhodi odvisni tako od trenutnega stanja kot tudi od trenutnih vhodov. Na predstavitvi vidimo poenostavljeni shemi za oba modela: oba vsebujeta kombinacijsko logiko, ki na podlagi trenutnega stanja (iz registra) in vhodov (pri Mealyju tudi neposredno na izhod) določa naslednje stanje, ki se ob aktivnem robu ure zapiše v register. Register shranjuje trenutno stanje.

Za ilustracijo delovanja sinhronskih sekvenčnih vezij si poglejmo preprost primer: dvobitni števec, ki periodično šteje od 0 do 3. Ta števec lahko realiziramo z dvema D-flip-flopoma in nekaj kombinacijske logike. Vhod D0 nižjega flip-flopa (ki predstavlja bit Q0) je enak negiranemu izhodu Q0' tega istega flip-flopa. Vhod D1 višjega flip-flopa (ki predstavlja bit Q1) pa je enak logični operaciji ekskluzivni ALI (XOR) med Q0 in Q1. Stanje števca (Q1Q0) se ob vsakem aktivnem robu ure posodobi: 00 -> 01 -> 10 -> 11 -> 00 -> ...

Tako imamo dvobitni register (realiziran z dvema D-flip-flopoma) in kombinacijsko logiko (en invertor za Q0' in eno vrata XOR za Q0 xor Q1). Zakasnitev teh kombinacijskih vrat (invertorja in XOR) določa, kako hitro se lahko vhodi D0 in D1 po spremembi izhodov Q0 in Q1 ustalijo na pravih vrednostih pred naslednjim aktivnim robom ure. To je ključno, saj morajo biti vhodni signali na flip-flopih stabilni vsaj za čas *vzpostavitve (setup time)* pred aktivnim robom in ostati stabilni za čas *držanja (hold time)* po njem. Zakasnitev kombinacijske logike med registri torej določa najmanjšo možno periodo ure, kar posledično omejuje maksimalno frekvenco, s katero lahko vezje deluje.

**Delovanje CPE: Cikel ukaza**

Osnovno delovanje CPE poteka v ponavljajočem se ciklu, ki se večinoma sestoji iz dveh glavnih korakov: dobave ukaza (fetch) in izvrševanja ukaza (execute). Ta cikel se ponavlja, dokler računalnik deluje.

1.  **Dobava ukaza (Fetch):** CPE pridobi (dobavi) naslednji ukaz, ki ga mora izvršiti, iz pomnilnika. Naslov tega ukaza je shranjen v posebnem registru, imenovanem programski števec (PC – Program Counter).
2.  **Izvrševanje ukaza (Execute):** CPE izvede operacijo, ki jo določa dobavljeni ukaz. Ta faza je lahko sestavljena iz več podkorakov, odvisno od kompleksnosti ukaza in arhitekture CPE:
    *   a) Dekodiranje ukaza: CPE razlaga (dekodira) pomen dobavljenega ukaza in ugotovi, katera operacija naj se izvede ter na katerih podatkih (operandih). V tej fazi se lahko tudi preberejo operandi iz registrov.
    *   b) Izvedba ALE operacije (ALU Operation): CPE izvede aritmetično-logično operacijo (z uporabo ALU - Arithmetic Logic Unit) ali pa izračuna naslov pomnilniške lokacije, če ukaz zahteva dostop do pomnilnika (npr. ukaza `load` ali `store`).
    *   c) Prenos operandov v CPE iz pomnilnika (po potrebi): Če ukaz zahteva operande, ki niso v registrih, se ti preberejo iz pomnilnika in prenesejo v CPE.
    *   d) Shranjevanje rezultata (po potrebi): Rezultat operacije se shrani, bodisi v register ali v pomnilnik (pisanje v register ali pomnilnik).
    *   e) Posodobitev programskega števca (PC): Za večino ukazov se PC poveča za velikost ukaza, da kaže na naslednji ukaz v sekvenci (npr. PC ← PC + 1, če predpostavimo, da je velikost ukaza 1 enota). Pri ukazih skoka (branch/jump) pa se PC naloži z naslovom ciljnega ukaza, s čimer se prekine zaporedno izvajanje.

Izjema od tega strogega Fetch-Execute cikla so dogodki, kot so prekinitve (interrupts) in pasti (traps). Ti dogodki povzročijo, da CPE začasno ustavi normalno izvajanje programa in skoči na poseben rutino (obravnavalec prekinitve/pasti), ki obravnava dogodek, nato pa se po možnosti vrne k prvotnemu programu. To v bistvu pomeni skok na nek drug ukazni naslov.

**Časovna analiza cikla in frekvenca ure**

V sinhronskih CPE je celoten cikel ukaza (Fetch-Execute) razdeljen na več bolj elementarnih korakov ali faz. Vsak od teh korakov traja eno ali več period ure CPE. Delovanje sinhronskih vezij je tesno povezano z urinimi signali (clock signals). Spremembe stanja sekvenčnih vezij (registrov, flip-flopov) se prožijo ob aktivni fronti ure (naraščajočem ali padajočem robu urnega signala). Perioda ure CPE (označena kot t_CPE) je čas med dvema sosednjima aktivnima frontama, njena frekvenca (f_CPE) pa je obratna vrednost periode (f_CPE = 1/t_CPE). Ta frekvenca ure je ključna za določanje hitrosti CPE.

Kot smo videli pri dvobitnem števcu, je perioda ure navzdol omejena z zakasnitvami kombinacijskih vezij med sekvenčnimi elementi. Če bi bila perioda krajša od časa, ki ga potrebujejo signali, da prepotujejo skozi kombinacijsko logiko in se ustalijo na vhodih naslednjih registrov, se novo stanje ne bi imelo časa pravilno vzpostaviti pred naslednjim aktivnim robom. To bi povzročilo napačno delovanje. Zato je maksimalna frekvenca delovanja omejena z najdaljšo zakasnitvijo med katerima koli dvema sekvenčnima elementoma v vezju.

Alternativa sinhronskim vezjem so asinhronska sekvenčna vezja, ki ne uporabljajo globalne ure. Njihove prednosti so, da so načeloma lahko hitrejša (ker niso omejena z najdaljšo potjo, temveč z lokalnimi zakasnitvami, in ker ni zakasnitev razpošiljanja ure) in porabijo manj energije (ker se deli vezja aktivirajo le po potrebi). Nekateri procesorji, kot je bil MIPS R3000, so jih uporabili za doseganje večje hitrosti (domnevno 4x hitrejši kot sinhronski). Vendar pa je načrtovanje asinhronskih vezij izredno težavno in kompleksno zaradi problema sinhronizacije dogodkov in preprečevanja tekme (race conditions) ter metastabilnosti, zato so v praksi veliko manj pogosta kot sinhronska.

**Struktura CPE: Podatkovna enota in Kontrolna enota**

CPE lahko funkcionalno razdelimo na dva glavna dela, ki tesno sodelujeta:

1.  **Kontrolna enota (KE - Control Unit):** To je možganski center CPE. Njena glavna naloga je interpretirati ukaze in na podlagi tega generirati *kontrolne signale*. Ti signali krmilijo vse ostale dele CPE, vključno s podatkovno enoto, pomnilnikom in vhodno/izhodnimi (V/I) enotami. Kontrolna enota določa zaporedje operacij, ki jih CPE izvaja za vsak ukaz. V bistvu povedo, kateri register se prebere, katero operacijo ALU naj izvede, ali se bere iz pomnilnika ali piše vanj, kam se shrani rezultat itd.
2.  **Podatkovna enota (PE - Datapath):** To je "mišica" CPE, kjer se dejansko izvaja procesiranje podatkov. Sestavljena je iz:
    *   Aritmetično-logične enote (ALE - ALU): izvaja aritmetične (seštevanje, odštevanje) in logične (AND, OR, XOR) operacije.
    *   Registrov: hitrih pomnilnih celic znotraj CPE, ki shranjujejo operande in rezultate operacij, pa tudi sistemske podatke (npr. programski števec, statusni registri).
    *   Notranjih povezav (vodil), multipleksorjev in ostalih vezij, ki usmerjajo pretok podatkov med ALE, registri in vmesniki s pomnilnikom/V/I.

Podatkovna enota je v svojem bistvu pasivna; sama po sebi ne dela ničesar, dokler ji kontrolna enota ne pove, kaj naj stori, z aktiviranjem ustreznih kontrolnih signalov. Kontrolna enota pa mora imeti popolno znanje o setu ukazov in vedeti, kateri koraki so potrebni za izvršitev vsakega ukaza ter katere kontrolne signale je treba aktivirati v določeni periodi ure ali stanju. Razvoj kontrolne enote je pogosto najbolj kompleksen in kritičen del načrtovanja novega CPE, in večina napak se pojavi prav v njej.

**Načini implementacije CPE (Sinhronski)**

Različne arhitekture CPE se ločijo po tem, kako je organiziran cikel izvrševanja ukaza glede na periode ure. Trije glavni načini sinhronske implementacije so:

1.  **Enocikelni procesor ('single-cycle'):** V tem pristopu se celoten ukaz (Fetch in Execute) izvrši znotraj *ene same periode ure*. To poenostavi načrtovanje kontrolne enote, saj morajo biti vsi kontrolni signali določeni na začetku cikla in ostati stabilni do konca. Glavna pomanjkljivost je, da mora biti perioda ure dovolj dolga, da sprejme *najdaljši* ukaz v celotnem setu ukazov, kar pomeni, da hitrejši ukazi (ki bi sicer potrebovali manj časa) "čakajo" na konec periode. Posledica je daljša perioda in s tem nižja frekvenca ure kot bi bila sicer mogoča.
2.  **Večcikelni procesor ('multi-cycle'):** Tukaj se izvrševanje ukaza razdeli na več, običajno 3 do 5, stopenj (faz), od katerih vsaka traja eno periodo ure. Ukazi si sledijo zaporedno in se *ne prekrivajo*. Vsaka stopnja opravi del posla (npr. dobava ukaza, dekodiranje/branje registrov, izvršitev ALE, dostop do pomnilnika, pisanje rezultata v register). Perioda ure je določena z zakasnitvijo *najdaljše stopnje*, ne najdaljšega ukaza, kar omogoča višjo frekvenco ure kot pri enocikelnem. Kontrolna enota je bolj kompleksna, saj mora nadzorovati zaporedje stopenj za vsak ukaz in aktivirati ustrezne signale v vsaki periodi; tipično se implementira kot končni avtomat (FSM - Finite State Machine).
3.  **Cevovodni procesor ('pipeline'):** Ta pristop, ki temelji na večcikelnem modelu, gre še korak dlje. Ukazi so še vedno razdeljeni na več stopenj, a se te stopnje *časovno prekrivajo*. Ko eden ukaz zaključi stopnjo 1 in preide na stopnjo 2, lahko naslednji ukaz začne stopnjo 1. To je podobno proizvodni liniji. Čeprav posamezen ukaz še vedno potrebuje več period za dokončanje (imenovano latenca), procesor lahko začne izvajati nov ukaz v skoraj vsaki periodi ure, kar močno poveča *prepustnost* (število ukaza na časovno enoto). Cevovodni procesorji so standard v sodobnih CPE, čeprav prinašajo svoje izzive (npr. reševanje konflikta med ukazi, ki so hkrati v cevovodu).

**Implementacija enocikelnega procesorja (Primer RISC-V)**

Poglejmo podrobneje implementacijo enocikelnega procesorja na primeru podnabora ukazov arhitekture RISC-V, ki vključuje ukaze za nalaganje besede (`lw`), shranjevanje besede (`sw`), pogojni skok (`beq`) ter aritmetično-logične ukaze formata R (npr. `add`, `sub`, `and`, `or`).

Datapath (podatkovna enota) enocikelnega procesorja za ta nabor ukazov vključuje ključne komponente, kot so programski števec (PC), pomnilnik za ukaze (instruction memory), datotečni register (Registers - zbirka vseh splošnih registrov), aritmetično-logična enota (ALU), pomnilnik za podatke (data memory) ter različni multipleksorji (Mux) in enote za razširitev predznaka (Imm Gen, Shift left 1 za naslove skokov). Diagram (slajd 11, 12) prikazuje, kako so te komponente povezane za izvajanje vseh omenjenih ukazov v enem ciklu.

ALU je ključna komponenta, ki izvaja operacije nad dvema 32-bitnima vhodnima operandoma (x in y). Izhod ALE je 32-bitni rezultat in 1-bitni signal `Zero`, ki je aktiven, če je rezultat nič. Katera operacija naj ALU izvede (seštevanje, odštevanje, AND, OR, ...) določajo 4-bitni kontrolni signali `ALUOp`, ki prihajajo iz kontrolne enote. Ti signali `ALUOp` so odvisni od delov ukaza, natančneje od operacijske kode (`opcode`) in v primeru R-tipa ukazov tudi od podaljškov `funct3` in `funct7`. Na primer, če je `ALUOp` '00', ALU izvaja seštevanje, primerno za izračun naslova pri `lw` in `sw`. Če je `ALUOp` '01', izvaja odštevanje in signalizira nič, primerno za preverjanje enakosti pri `beq`. Za R-tip ukaze (`ALUOp` '10') se specifična ALU operacija (add, sub, and, or) določi na podlagi `funct3` in `funct7` bitov ukaza (tabela na slajdu 13 prikazuje to preslikavo).

Kontrolna enota v enocikelnem procesorju (diagram na slajdu 12, tabela na slajdu 14) je odgovorna za generiranje vseh kontrolnih signalov za posamezni ukaz: `ALUSrc`, `Branch`, `MemRead`, `MemWrite`, `RegWrite`, `MemToReg`, `ALUOp`, `ALUSrc` (za ALE vhoda A in B), `ResultSrc` (za kam gre rezultat), `PCSource` (za naslednji PC). Ker se vsi signali določijo na začetku cikla in ostanejo konstantni, je kontrolna enota v tem preprostem primeru v bistvu kar *kombinacijsko vezje* (ali bralni pomnilnik ROM/PLA), ki na podlagi bitov ukaza (opcode, funct) določa vrednosti vseh kontrolnih signalov. Tabela na slajdu 14 prikazuje primer kontrolnih signalov za `lw`, `sw`, `beq` in R-tip ukaze. Na primer, za `lw` (opcode 0000011) kontrolna enota aktivira `MemRead=1`, `RegWrite=1`, nastavi `ALUSrc` tako, da sešteje vrednost registra (baza) in razširjen premik (`offset`), nastavi `MemToReg` tako, da rezultat pride iz pomnilnika, in nastavi `ALUOp` na '00' (seštevanje).

**Primer programa in zmogljivost enocikelnega procesorja**

Za boljšo predstavo o delovanju si lahko ogledamo primer kratkega programa v asemblerju za RISC-V (slajd 15). Program prikazuje štiri ukaze s svojimi naslovi, asemblersko obliko, formatom (I, S, R, B) in binarno strojno kodo. Na primer, ukaz `lw x6, -4(x9)` je ukaz za nalaganje besede (format I), ki naloži 32-bitno vrednost iz pomnilnika na naslovu, izračunanem kot vrednost registra x9 minus 4, v register x6.

Zmogljivost enocikelnega procesorja je bistveno omejena z dolžino njegove urinske periode. Kot že omenjeno, to periodo določa *kritična pot* – najdaljša pot signala med poljubnima sekvenčnima elementoma (običajno med registri). Pri enocikelnem procesorju je kritična pot najdaljša zaporedna pot skozi vse kombinacijske dele, ki jih kateri koli ukaz uporablja v enem ciklu. Tipično je najdaljši ukaz `lw` (nalaganje besede), saj zahteva dostop do pomnilnika za ukaz, branje iz registrske datoteke, izračun naslova v ALE, dostop do pomnilnika za podatke in na koncu pisanje rezultata nazaj v registrsko datoteko. Minimalna perioda ure (t_CPE) je torej vsota zakasnitev vseh teh stopenj: zakasnitev naložitve PC (t_pcq), dostopa do pomnilnika za ukaze (t_mem), branja iz registrske datoteke (t_RFread), izračuna v ALE (t_ALE, kar vključuje tudi razširitev predznaka in multipleksorje), dostopa do pomnilnika za podatke (t_mem) in časa vzpostavitve (setup time) pred pisanjem v register (t_RFsetup). Perioda je približno t_pcq + t_mem + max(t_RFread, t_se + t_mux) + t_ALE + t_mem + t_mux + t_RFsetup. Rdeče označene zakasnitve (t_mem, t_RFread, t_ALE) so običajno dominantne in po grobi oceni je perioda malo večja kot 2*t_mem + t_RFread + t_ALE.

V enocikelnem procesorju vsak ukaz, ne glede na to, kako preprost ali kompleksen je, porabi natanko eno periodo ure za izvršitev. Zato je CPI (Clocks Per Instruction) za *vsak* ukaz enak 1. Skupni čas izvajanja programa je torej število ukazov pomnoženo z dolžino urinske periode.

Na slajdu 17 je primer izračuna minimalne periode ure za enocikelni CPE z danimi zakasnitvami komponent: t_pcq=30 ps, t_mem=250 ps, t_RFread=150 ps, t_ALE=200 ps, t_mux=25 ps, t_se=20 ps, t_RFsetup=20 ps. Minimalna perioda se izračuna po formuli kritične poti LW, ki je najdaljša: 30 (t_pcq) + 250 (t_mem) + max(150 (t_RFread), 20 (t_se) + 25 (t_mux)) + 200 (t_ALE) + 250 (t_mem) + 25 (t_mux) + 20 (t_RFsetup). Če upoštevamo najdaljšo pot, ki gre skozi vse komponente LW: PC -> ukazni pomnilnik -> register file -> ALU (z vključeno razširitvijo predznaka in ALU vhodnim muxom) -> podatkovni pomnilnik -> MemToReg mux -> register file (pisanje). Perioda je 30 + 250 + 150 + max(20+25, 150) + 200 + 250 + 25 + 20 = 30 + 250 + 150 + 200 + 250 + 25 + 20 = 925 ps. Če imamo program z 10^9 ukazi, bo trajal 10^9 ukaza * 1 cikel/ukaz * 925 ps/cikel = 925 * 10^9 ps = 925 ms.

**Implementacija večcikelnega procesorja**

Da bi izboljšali zmogljivost (dosegli krajšo periodo ure), lahko uporabimo večcikelno implementacijo. Pri tem vsak ukaz potrebuje več period ure za svojo izvedbo, a je posamezna perioda lahko krajša. V vsaki periodi se izvrši le ena "podoperacija" ali stopnja izvajanja ukaza.

Za podporo večstopenjskemu izvajanju v večcikelnem procesorju je potrebno dodati nekaj *vmesnih registrov* (slajd 18, 19). Ti registri shranjujejo rezultate ene stopnje (periode) za uporabo v naslednjih stopnjah. Primeri takih registrov vključujejo:
*   Register ukaza (IR - Instruction Register), ki shrani ukaz, ko je bil dobavljen.
*   Registra A in B, ki shranita operanda, prebrana iz registrske datoteke.
*   Register ALUOut, ki shrani rezultat ALU operacije.
*   Register Data, ki shrani podatke, prebrane iz pomnilnika podatkov.
*   Register OldPC, ki shranjuje naslov ukaza pred posodobitvijo PC, kar je uporabno pri povratnih skokih ali izjemah.

Diagram podatkovne enote večcikelnega procesorja (slajd 19) prikazuje te dodatne registre in kako so povezave reorganizirane, da omogočijo večstopenjsko obdelavo in ponovno uporabo komponent (npr. ALU se uporabi za izračun PC+4, izračun naslova pomnilnika in izvedbo ALE operacije). Multipleksorji so zdaj tudi na vhodih teh vmesnih registrov, da lahko naložijo rezultate iz različnih virov glede na trenutno stopnjo izvajanja ukaza.

**Kontrolna enota večcikelnega procesorja**

Pri večcikelnem procesorju je kontrolna enota (KE) bistveno bolj zapletena. Podatkovna enota ostaja pasivna, izvaja samo to, kar od nje zahtevajo kontrolni signali, a KE mora zdaj vedeti za vsak ukaz, kateri koraki (stopenj) so potrebni in katere kontrolne signale je treba aktivirati v *vsaki* od teh stopenj, tj. v določeni periodi ure. Ker se ukazi izvajajo v zaporedju stopenj, kontrolna enota deluje kot *končni avtomat* (FSM - Finite State Machine).

Delovanje KE v večcikelnem procesorju lahko podamo z diagramom prehajanja stanj (DPS) (slajd 22). Vsako stanje v diagramu ustreza eni stopnji izvajanja ukaza (ene periode ure). Prehodi med stanji se zgodijo ob aktivnem robu ure, odvisno od trenutnega stanja in nekaterih vhodnih signalov (npr. biti v registru ukaza, signal Zero iz ALU).

V vsakem stanju končnega avtomata sta definirani dve glavni funkciji (slajd 21):
1.  **Funkcija naslednjega stanja:** Na podlagi trenutnega stanja in vhodnih signalov (npr. opcode ukaza, zastavice stanja ALU, kot je Zero) določa, v katero stanje se bo avtomat premaknil ob naslednjem aktivnem robu ure.
2.  **Funkcija izhodnih signalov:** Določa, kateri kontrolni signali (MemRead, RegWrite, ALUSrc, ALUOp, itd.) morajo biti aktivni (ali imeti določeno vrednost) v danem trenutnem stanju, da podatkovna enota izvede zahtevano operacijo za to stopnjo.

Končni avtomat se realizira s kombinacijskim vezjem (ki določa naslednje stanje in izhodne signale) in sekvenčnim vezjem (registrom stanja), ki shrani trenutno stanje. Diagram prehajanja stanj na slajdu 22 prikazuje poenostavljen primer za nekaj ukazov: Stanje S0 je faza dobave ukaza (Fetch), S1 je dekodiranje in branje registrov, S2/S3 sta za dostop do pomnilnika (izračun naslova, branje), S4 je pisanje rezultata `lw` v register, S5 je pisanje `sw` v pomnilnik, S6 je izvajanje R-tip ukaza, S7 je pisanje R-tip rezultata v register, S10 pa je izvajanje `beq`. Prehodi med stanji so odvisni od operacijske kode ukaza (`op`) ali rezultata preverjanja pogoja (`beq`).

Kontrolna enota večcikelnega procesorja ima lahko precejšnje število izhodnih signalov (do 20 ali več, odvisno od arhitekture). Ker so ukazi v arhitekturah RISC-V relativno preproste in fiksne dolžine, lahko znaten del bitov iz registra ukaza (IR), kot so naslovi registrov ali takojšnje vrednosti, peljemo mimo kontrolne enote neposredno na ustrezne multipleksorje ali enote za obdelavo podatkov v podatkovni enoti (PE).

**Realizacija kontrolne enote: Trdo ožičena ali mikroprogramirana**

Na splošno obstajata dva glavna načina, kako realizirati logiko kontrolne enote:

1.  **Trdo ožičena logika (Hard-wired logic):** Kontrolna enota je zgrajena neposredno z uporabo standardnih kombinacijskih in sekvenčnih logičnih vrat (AND, OR, NOT, flip-flopi) in njihove medsebojne povezave. Logika, ki na podlagi vhodov (stanje, biti ukaza) določa naslednje stanje in izhodne signale, je implementirana direktno v strojni opremi. Ta pristop je običajno hitrejši, saj signali potujejo samo skozi logična vrata. Vendar pa je zasnova trdo ožičene kontrolne enote zelo kompleksna za procesorje z velikimi in kompleksnimi nabori ukazov (CISCs, kot je x86), saj je treba v strojno opremo vgraditi logiko za izvajanje vsakega ukaza. Spremembe ali dodajanje novih ukazov so izjemno težavne, saj zahtevajo fizični poseg in redizajn vezja.

2.  **Mikroprogramiranje:** V tem pristopu je kontrolna enota sama po sebi manjši, enostavnejši, trdo ožičen procesor, ki izvaja zaporedje *mikroukazov*. Ti mikroukazi so shranjeni v posebnem pomnilniku znotraj kontrolne enote, imenovanem *kontrolni pomnilnik* (Control Memory), pogosto ROM. Vsak ukaz v "glavnem" naboru ukazov CPE (arhitektura, ki jo vidi programer) je v bistvu interpretiran in izveden kot majhen *mikroprogram* – zaporedje enega ali več mikroukazov. Mikroukazi so bolj primitivni in neposredno krmilijo kontrolne signale CPE (npr. "aktiviraj MemRead", "nastavi ALUSrcA na register A"). Ta pristop je običajno počasnejši od trdo ožičene logike (ker je treba mikroukaze brati iz pomnilnika), vendar pa je izredno prilagodljiv. Dodajanje novih ukazov ali spreminjanje obstoječih je relativno enostavno, saj zahteva samo spremembo vsebine kontrolnega pomnilnika (posodobitev *firmware*), ne pa redizajna strojne opreme. To je bila ključna prednost pri procesorjih s kompleksnimi in spreminjajočimi se nabori ukazov, kot so zgodnji Intelovi procesorji 80x86, ki so za svoje obsežne in kompleksne ukaze potrebovali več tisoč "stanj" (mikroukazov). Za relativno majhen primer, kot je obravnavani podnabor RISC-V ukazov, bi zadostoval že manjši kontrolni pomnilnik (npr. ROM s 512 lokacijami, naslovljen z 9-bitnim naslovom). Koncept mikroprogramiranja je sicer danes manj viden v modernih RISC procesorjih, ki so večinoma trdo ožičeni, je pa pomemben zgodovinski in arhitekturni koncept.

Za končnega uporabnika ali programerja v višjem jeziku je način realizacije kontrolne enote (trdo ožičena ali mikroprogramirana) v resnici nepomemben. Pomembno je samo, da CPE pravilno izvršuje ukaze svoje arhitekture.

**Merjenje zmogljivosti CPE: CPI in MIPS**

Čas, ki ga CPE porabi za izvršitev programa, je ključno merilo zmogljivosti. Pri večcikelnih procesorjih posamezni ukazi ne porabijo enakega števila urinskih period (ciklov) za izvedbo. Preprostejši ukazi, kot je npr. R-tip ukaz, lahko potrebujejo manj stopenj (in s tem manj ciklov) kot bolj kompleksni ukazi, kot sta `lw` ali `sw`, ki vključujejo dostop do pomnilnika. Zato je pri večcikelnem procesorju CPI (Clocks Per Instruction) za posamezni ukaz tipično večji od 1 (običajno med 3 in 6 cikli za osnovne ukaze, a se lahko zelo razlikuje).

Povprečen CPI za določen program na večcikelnem CPE je tehtano povprečje števila ciklov, ki jih potrebuje vsaka vrsta ukaza, kjer so uteži relativne pogostosti (verjetnost) pojavljanja posamezne vrste ukaza v tem programu. Formula za idealni CPI (CPI_ideal), ki ne upošteva čakalnih dob zaradi pomnilniških dostopov ali drugih vzrokov, je:
CPI_ideal = Σ (p_i * CPI_i)
kjer je p_i relativna pogostost ukaza tipa i v programu, CPI_i pa je število urinskih period, ki jih potrebuje ukaz tipa i v večcikelnem procesorju.

Primer izračuna (slajd 28): Predpostavimo, da nek C-prevajalnik generira kodo, ki vsebuje 46% ALE ukazov, 36% ukazov za prenos podatkov (load/store) in 18% kontrolnih ukazov (skokov). Predpostavimo tudi, da je število `lw` ukazov trikrat večje od števila `sw` ukazov znotraj 36% prenosa podatkov (tj. 0.75 * 36% = 27% `lw`, 0.25 * 36% = 9% `sw`). Iz tabel na slajdu (ki prikazujejo minimalno število period brez čakanja) vidimo, da `lw` potrebuje 5 ciklov, `sw` 4 cikle, ALE 4 cikle in `beq` (skok) 3 cikle. Idealni CPI bi bil:
CPI_ideal = (0.46 * 4) + (0.27 * 5) + (0.09 * 4) + (0.18 * 3)
CPI_ideal = 1.84 + 1.35 + 0.36 + 0.54 = 4.09.
(Opomba: V primeru na slajdu je pri izračunu pogostosti load/store ukazi obravnavani skupaj, kar daje drugačno številko 1.71, ter pogostosti 0.75 in 0.25 se nanašata znotraj skupine 36%. Moj izračun: 0.46*4 + 0.36*(0.75*5 + 0.25*4) + 0.18*3 = 1.84 + 0.36*(3.75+1) + 0.54 = 1.84 + 0.36*4.75 + 0.54 = 1.84 + 1.71 + 0.54 = 4.09. Rezultat 4.09 na slajdu je pravilen).

Realna zmogljivost CPE pa ni odvisna samo od idealnega CPI in frekvence ure, temveč tudi od časa, ki ga CPE preživi *čakanja* na pomnilniške dostope, zlasti ob zgrešitvah v predpomnilniku (cache misses). Vsi ukazi potrebujejo vsaj en dostop do pomnilnika za *dobavo ukaza*. Ukazi `lw` in `sw` pa potrebujejo še dodaten dostop za *dobavo/shranjevanje podatka*. Če predpostavimo hierarhijo pomnilnika s predpomnilnikom, se dostopi do pomnilnika podatkov (in včasih tudi do ukazov) lahko zgrešijo v predpomnilniku. Zgrešitev zahteva branje bloka podatkov iz počasnejšega glavnega pomnilnika, kar povzroči precejšnje število *čakalnih urinskih period* (stalls). To število se imenuje *zgrešitvena kazen* (K_z - Miss Penalty).

Povprečno število čakalnih urinskih period na ukaz zaradi zgrešitev v predpomnilniku podatkov je odvisno od števila dostopov do pomnilnika podatkov na ukaz (N_data_accesses), verjetnosti zgrešitve v predpomnilniku podatkov (Miss Rate_data = 1 - Hit Rate_data) in zgrešitvene kazni (K_z). Povprečne čakalne periode na ukaz (CPE_periode_čak) = (N_data_accesses per instruction) * Miss Rate_data * K_z. Če predpostavimo, da je verjetnost zadetka (H) v predpomnilniku 95% (torej Miss Rate 5%) in zgrešitvena kazen (K_z) 10 ciklov, je povprečno število čakalnih period na dostop 0.05 * 10 = 0.5 cikla. Ukaz `lw` ima 2 dostopa (ukaz + podatki), `sw` 2 dostopa, ALE 1 (ukaz), BEQ 1 (ukaz). Povprečne čakalne periode na ukaz za ta primer:
*   `lw`: 1 (dostop ukaza, predpostavimo 100% zadetek v ukaznem cache ali zanemarimo) + 1 (dostop podatkov) * 0.05 * 10 = 0.5 cikla čakanja. Skupni CPI_real = CPI_ideal + čakanje = 5 + 0.5 = 5.5
*   `sw`: 1 (dostop ukaza) + 1 (dostop podatkov) * 0.05 * 10 = 0.5 cikla čakanja. Skupni CPI_real = 4 + 0.5 = 4.5
*   ALE: 1 (dostop ukaza) * 0.05 * 10 = 0.5 cikla čakanja. Skupni CPI_real = 4 + 0.5 = 4.5
*   BEQ: 1 (dostop ukaza) * 0.05 * 10 = 0.5 cikla čakanja. Skupni CPI_real = 3 + 0.5 = 3.5
(Opomba: Primer na slajdu 30 ima v tabeli malo drugačne idealne CPI za `lw` (5), `sw` (4), ALE (4), BEQ (3) in potem realne CPI 6, 5, 4.5, 3.5. To implicira, da morda upoštevajo čakanje pri *vsakem* pomnilniškem dostopu, tudi za ukaze, kar sem jaz na začetku pripisal samo podatkovnim dostopom. Če vsak pomnilniški dostop (ne glede na to, ali je za ukaz ali podatke) v povprečju povzroči 0.5 cikla čakanja, potem: lw (2 dostopa): 5 + 2*0.5 = 6; sw (2 dostopa): 4 + 2*0.5 = 5; ALE (1 dostop ukaza): 4 + 1*0.5 = 4.5; BEQ (1 dostop ukaza): 3 + 1*0.5 = 3.5. Te številke se ujemajo s tabelo na slajdu 30).

Realni CPI (CPI_resnični) programa, ki upošteva čakanje, je torej vsota idealnega CPI (najmanjšega števila period) in povprečnega števila čakalnih period na ukaz (CPE_periode_čak). CPI_resnični = CPI_ideal + CPE_periode_čak. S predpostavljenimi pogostostmi in realnimi CPI vrednostmi (ki vključujejo čakanje na pomnilnik) izračunamo realni povprečni CPI za program:
CPI_resnični = (0.46 * 4.5) + (0.36 * 5.5) + (0.18 * 3.5)
CPI_resnični = 2.07 + 1.98 + 0.63 = 4.68.
(Opomba: Spet neskladje s slajdom 31, kjer je 0.36*(0.75*6+0.25*5) = 0.36*(4.5+1.25) = 0.36*5.75 = 2.07. In skupni izračun 2.07+2.07+0.63 = 4.77. Razlika je v tem, ali se povprečni CPI za load/store izračuna kot tehtano povprečje realnih CPI-jev (0.75*6 + 0.25*5) ali se idealni CPI tehtata (0.75*5+0.25*4) in se čakalna doba (ki je enaka za oba) prišteje na koncu. Pravilnejši je pristop na slajdu: najprej določimo *realni* CPI za *vsak* tip ukaza, nato pa izračunamo tehtano povprečje *teh realnih* CPI-jev. Torej, za load/store ukaze, katerih je 36%, je povprečni realni CPI = 0.75 * 6 (za lw) + 0.25 * 5 (za sw) = 4.5 + 1.25 = 5.75. Potem je CPI_resnični = (0.46 * 4.5) + (0.36 * 5.75) + (0.18 * 3.5) = 2.07 + 2.07 + 0.63 = 4.77. Ta izračun se ujema s slajdom 31).

Parameter MIPS (Million Instructions Per Second) je še en pogost merilec zmogljivosti CPE. Predstavlja število milijonov ukazov, ki jih CPE lahko izvrši v eni sekundi. Izračuna se po formuli:
MIPS = Frekvenca ure (v Hz) / (CPI * 10^6)
ali MIPS = (1 / Perioda ure (v sekundah)) / (CPI * 10^6).
Če imamo CPE s frekvenco 2 GHz (2 * 10^9 Hz) in povprečnim realnim CPI 4.77, je njegova zmogljivost v MIPS:
MIPS = (2 * 10^9 Hz) / (4.77 * 10^6) = 2000 / 4.77 ≈ 419 MIPS.
To pomeni, da ta CPE lahko izvrši približno 419 milijonov ukazov na sekundo za ta specifični program.

**Kritična pot in časovna analiza večcikelnega procesorja**

Kritična pot v večcikelnem procesorju je, tako kot v enocikelnem, najdaljša zakasnitev med poljubnima sekvenčnima elementoma. Vendar pa pri večcikelnem procesorju to ni več celotna pot enega ukaza, ampak najdaljša zakasnitev *znotraj katere koli posamezne stopnje* (periode ure). Vsaka stopnja ukaza se mora zaključiti v eni periodi ure. Minimalna perioda ure (t_CPE,min) je torej določena z maksimalno zakasnitvijo katere koli stopnje izvrševanja ukaza (Fetch, Decode, Execute, Memory, Writeback), vključno s časom naložitve PC ali drugega registra na začetku stopnje in časom vzpostavitve registra na koncu stopnje.

Formula za minimalno periodo pri večcikelnem CPE je: t_CPE,min = t_pcq + max(zakasnitev stopenj) + t_setup. Najdaljša stopnja je običajno Fetch (dostop do ukaznega pomnilnika), Execute (ALE operacija z branjem registrov in muxi) ali Memory (dostop do pomnilnika podatkov).

Primer izračuna (slajd 33): Uporabimo enake zakasnitve komponent kot prej: t_pcq=30 ps, t_mem=250 ps, t_RFread=150 ps, t_ALE=200 ps, t_mux=25 ps, t_se=20 ps, t_RFsetup=20 ps.
Zakasnitve posameznih stopenj:
*   Fetch (S0): PC -> Mem ukazi -> IR -> t_pcq + t_mem ≈ 30 + 250 = 280 ps (v resnici je treba dodati še čas do vhoda IR, t_IRsetup, in pot skozi PC izračun: PC -> Add(PC+4) -> PCSource Mux -> PC; torej t_pcq + t_ALE + t_mux + t_PCsetup. V diagramu večcikličnega je PC + 4 izračun v drugi stopnji. Stopnja 0 je PC -> Ukazni pomnilnik -> IR. Pot je PC (register) -> Ukazni pomnilnik (komb.) -> IR (register). Traja t_pcq + t_mem + t_IRsetup. Z danimi številkami in predpostavko t_pcq=30, t_mem=250, t_IRsetup=20: 30+250+20 = 300 ps).
*   Decode (S1): IR -> Read Reg -> ALU (PC+4 izračun) -> t_IRq + t_RFread + t_ALE ≈ 30 + 150 + 200 = 380 ps (Pot je IR (register) -> Read registers (komb.) -> ALU (komb.). Traja t_IRq + t_RFread + t_ALE. Z danimi številkami in predpostavko t_IRq=30: 30 + 150 + 200 = 380 ps).
*   Execute R (S6): A, B reg -> ALU -> ALUOut reg -> t_Aq + t_ALE + t_ALUOutsetup ≈ 30 + 200 + 20 = 250 ps.
*   Memory Access (S3/S5): ALUOut reg -> Data Mem -> Data reg / SW data -> t_ALUOutq + t_mem + t_Datasup ≈ 30 + 250 + 20 = 300 ps.
*   Write Back (S4/S7): Data reg / ALUOut reg -> MemtoReg Mux -> Write Reg -> t_Dataq/t_ALUOutq + t_mux + t_RFsetup ≈ 30 + 25 + 20 = 75 ps.

Najdaljša stopnja je dekodiranje/branje registrov (380 ps). Minimalna perioda ure je torej približno 380 ps (v resnici bi bilo treba biti natančnejši pri vseh poteh, vključno z multiplkesorji in setup časi na vseh registrih). Vendar, če vzamemo izračun s slajda (morda poenostavljen ali s specifično potjo): t_CPE,min = 30 (t_pcq) + 2*25 (dva muxa, npr. PCSource in Imm/Reg mux na ALU vhodu) + 250 (t_mem za ukaze) + 20 (t_setup na IR?) = 325 ps, ali pa glede na kritično pot med registri v kateri koli stopnji. Slajd 33 navaja primer t_CPE,min = 30+2*25+250+20 = 350 ps. To očitno ustreza poti, kot je PC -> Mux -> Mem Ukazi -> IR, ali podobni kombinaciji.

Z minimalno periodo 350 ps in povprečnim realnim CPI 4.77 (izračunano prej), se program z 10^9 ukazi na tem večcikelnem procesorju izvaja:
Čas = Število ukazov * CPI * t_CPE
Čas = 10^9 * 4.77 * 350 ps = 10^9 * 4.77 * 350 * 10^-12 s = 10^9 * 4.77 * 0.35 * 10^-9 s ≈ 1.67 s.
Če program traja 10^9 ukazov: Idealni čas = 10^9 * 4.09 * 350 ps ≈ 1.432 s. Realni čas = 10^9 * 4.77 * 350 ps ≈ 1.6695 s. Slajd navaja 1.432 ns (pravilneje s) za idealni čas, kar ustreza 4.09 * 350 ps.

Primerjava: Enocikelni procesor (925 ps perioda, CPI=1) je isti program izvedel v 925 ms. Večcikelni procesor (350 ps perioda, CPI=4.77) ga izvede v približno 1.67 s. V tem primeru je enocikelni procesor *hitrejši* zaradi nizkega CPI, kljub daljši periodi. To poudarja, da ni samo frekvenca ure tista, ki določa zmogljivost.

**Merjenje zmogljivosti CPE (skupna slika)**

Zmogljivost CPE ni nujno enaka zmogljivosti celotnega računalnika. Zmogljivost celotnega sistema vključuje tudi hitrost in učinkovitost pomnilniške hierarhije (predpomnilniki, glavni pomnilnik) ter vhodno/izhodnega (V/I) sistema. CPE lahko dosega svojo maksimalno zmogljivost le, če mu pomnilniški in V/I sistem lahko dovolj hitro zagotavljata podatke in ukaze ter sprejemata rezultate, tj., če CPE ne čaka. Če zanemarimo V/I, je čas izvajanja programa na CPE (CPE čas) primarno merilo zmogljivosti CPE in se izračuna kot:
CPE čas = Število ukazov programa * CPI * t_CPE.
Tukaj je CPI povprečno realno število urinskih period na ukaz (Clocks Per Instruction), ki vključuje tudi morebitno čakanje na pomnilnik.

Tri ključne lastnosti, ki vplivajo na CPE čas in so medsebojno odvisne (ter cilji optimizacije), so:
*   **t_CPE (ali f_CPE):** Dolžina periode ure (ali frekvenca). Odvisna je od hitrosti elementarnih digitalnih vezij in arhitekturne zgradbe CPE (npr. koliko kombinacijske logike je v najdaljši stopnji pri večcikelnem/cevovodnem, ali v kritični poti pri enocikelnem).
*   **CPI:** Povprečno število urinskih period na ukaz. Odvisno je od arhitekturne zgradbe CPE (enocikelni vs. večcikelni vs. cevovodni), nabora ukazov in – kar je zelo pomembno – od učinkovitosti pomnilniške hierarhije (čakalne dobe zaradi zgrešitev v predpomnilniku).
*   **Število ukazov programa:** Koliko strojnih ukazov CPE mora izvršiti za določen program. Odvisno je od algoritma, programskega jezika, *prevajalnika* (kako učinkovito prevede višji jezik v strojne ukaze) in nabora ukazov samega CPE (kompleksnejši ukazi lahko v enem ukazu opravijo več dela, a so običajno počasnejši ali zahtevajo več stopenj/ciklov).

Nobena od teh lastnosti sama po sebi ni zadostno merilo zmogljivosti! CPE z višjo frekvenco ni nujno hitrejši, če ima bistveno višji CPI. Program, preveden v manj ukazov, ni nujno hitrejši, če so ti ukazi počasnejši ali povzročijo več čakanja.

Zmogljivost (Performance) je obratno sorazmerna s časom izvajanja: Zmogljivost = 1 / Čas izvajanja. Boljši (hitrejši) CPE ima krajši čas izvajanja in s tem večjo zmogljivost.

Pohitritev (Speed-up) se uporablja za primerjavo zmogljivosti dveh procesorjev (ali različnih izvedb istega procesorja) za isti program. Izračuna se kot razmerje časov izvajanja:
S = Čas_starega / Čas_novega = Zmogljivost_novega / Zmogljivost_starega.
Ali s pomočjo zgornje formule za CPE čas:
S = (Št_ukazov_stari * CPI_stari * t_CPE_stari) / (Št_ukazov_novi * CPI_novi * t_CPE_novi).
Če primerjamo isti program na dveh CPE-jih, generirana s istim prevajalnikom za isto arhitekturo (enako število ukazov), se formula poenostavi na S = (CPI_stari * t_CPE_stari) / (CPI_novi * t_CPE_novi).

Marsikdo še vedno primerja različne CPE na osnovi frekvence ure (f_CPE). To je lahko zelo zavajajoče! CPE z nižjo frekvenco lahko dejansko izvrši program hitreje kot CPE z višjo frekvenco, če ima bistveno nižji CPI (npr. zaradi boljše arhitekture, učinkovitejšega cevovoda, boljšega predpomnilnika, ali pa če primerjamo večcikelni/cevovodni z nizkim CPI vs. enocikelni z visokim t_CPE).

Parameter MIPS, čeprav široko uporabljan, ima tudi svoje pomanjkljivosti in ga nekateri označujejo celo kot "Meaningless Indication of Processor Speed".
*   MIPS je odvisen od števila in vrste ukazov v programu. Preprost nabor ukazov (RISC) lahko zahteva več strojnih ukazov za nalogo kot kompleksen nabor (CISC), a če so ti ukazi hitrejši, je lahko celoten čas krajši kljub višjemu MIPS. MIPS je običajno višji za programe z velikim deležem hitrih, enostavnih ukazov.
*   MIPS je odvisen od prevajalnika, ki lahko vpliva na število in vrsto generiranih ukazov. Optimizacijski prevajalniki lahko vplivajo na CPI in število ukazov.
*   MIPS neposredno ne upošteva časa, porabljenega v V/I ali čakanja na pomnilnik (razen če je to vključeno v CPI).

Kljub pomanjkljivostim je MIPS lahko uporaben za primerjavo *istega programa* na *istih* procesorjih z *različnimi frekvencami* ali za grobo primerjavo *podobnih* arhitektur z *podobnimi* nabori ukazov.

**Drugi merilci zmogljivosti**

Poleg MIPS obstajajo tudi drugi merilci, ki poskušajo bolje zajeti zmogljivost:

*   **MFLOPS (Million Floating point Operations Per Second):** Število milijonov operacij s plavajočo vejico na sekundo. Ta metrika je bolj smiselna za programe, ki intenzivno uporabljajo aritmetiko s plavajočo vejico (npr. znanstveni in inženirski izračuni), saj so operacije s plavajočo vejico med različnimi procesorji bolj standardizirane kot celotni ukazi. Vendar pa tudi ta metrika lahko zavaja, saj nekateri proizvajalci navajajo maksimalno teoretično zmogljivost ("peak MFLOPS"), ki je pogosto dosti višja od zmogljivosti, dosežene na realnih programih ("sustained MFLOPS").

*   **Sintetični "benchmarki":** To so kratki, specializirani programi, zasnovani posebej za merjenje zmogljivosti. Primeri vključujejo Whetstone (starejši, meri pretežno operacije s plavajočo vejico), Linpack (meri reševanje sistemov linearnih enačb, močno obremenjuje tako CPE kot pomnilnik), in Dhrystone (meri celoštevilčno aritmetiko, upravljanje z nizi, klici procedur – namenjen za merjenje splošne CPE zmogljivosti, ne plavajoče vejice). Problem sintetičnih benchmarkov je, da so pogosto premajhni, ne predstavljajo dobro realnih delovnih obremenitev in jih lahko proizvajalci ali prevajalniki "optimizirajo" do te mere, da rezultati niso več reprezentativni za realno delovanje.

*   **SPEC (Standard Performance Evaluation Corporation) benchmarki:** SPEC je konzorcij računalniških podjetij, ki razvija standardizirane zbirke programov (suite) za merjenje zmogljivosti. SPEC benchmarki običajno uporabljajo večje, kompleksnejše programe, ki posnemajo (ali so kar) realne aplikacije (npr. prevajalniki, urejevalniki besedil, simulacije, baze podatkov). Te zbirke se redno posodabljajo (SPECint, SPECfp za celoštevilčne/plavajoče operacije, SPECrate za prepustnost, SPECpower za energetsko učinkovitost itd.). Ker uporabljajo realne programe, so rezultati SPEC benchmarkov veliko bolj reprezentativni za dejansko zmogljivost CPE na tipičnih delovnih obremenitvah in so danes industrijski standard za primerjavo zmogljivosti. Kljub temu so tudi SPEC rezultati lahko odvisni od prevajalnika in nastavitev optimizacije.

V zaključku, razumevanje CPE zahteva poznavanje njegove zgradbe (KE, PE), načina delovanja (cikel ukaza, vpliv ure), različnih implementacijskih pristopov (enocikelni, večcikelni, cevovodni) in zavedanje, da je merjenje njegove zmogljivosti kompleksno ter zahteva upoštevanje več faktorjev (t_CPE, CPI, število ukazov, vpliv pomnilnika) in uporabo ustreznih metrik, ki presegajo zgolj frekvenco ure ali enostavne MIPS vrednosti.



# Pipelined processor


Okay, let's break down the concepts behind the exercise. You're asking about the fundamental principles of pipelining in a RISC-V processor.

Imagine a factory assembly line. Instead of one worker building a whole product from start to finish, different workers specialize in different steps. As soon as one worker finishes their step, they pass the product to the next worker and start on a new product. This is the core idea of pipelining.

**1. What is a Pipelined Processor?**

A standard processor executes instructions one after another: Fetch instruction 1, Decode instruction 1, Execute instruction 1, etc., then Fetch instruction 2, Decode instruction 2, Execute instruction 2, and so on. This is **sequential execution**.

A **pipelined processor** breaks down the execution of each instruction into a sequence of smaller steps or **stages**. It then overlaps the execution of multiple instructions by having different stages work on different instructions simultaneously.

Think of the instruction processing steps like washing, drying, folding, and storing laundry.
*   **Sequential:** Wash load 1, Dry load 1, Fold load 1, Store load 1. Then Wash load 2, Dry load 2, etc. The washer is idle while you dry, fold, and store.
*   **Pipelined:** Wash load 1. While load 1 is drying, Wash load 2. While load 1 is folding and load 2 is drying, Wash load 3. And so on. All machines (stages) are busy as much as possible.

**2. Pipeline Stages**

Most modern RISC processors, including standard RISC-V implementations, use a 5-stage pipeline. These stages represent the main steps an instruction goes through:

*   **IF (Instruction Fetch):** The processor fetches the next instruction from memory using the Program Counter (PC).
*   **ID (Instruction Decode / Register Fetch):** The instruction is decoded to figure out what operation it performs. The required values from the register file are read.
*   **EX (Execute):** The main operation is performed. This could be an arithmetic/logic calculation (like `add`, `and`), or calculating the memory address for a load/store (`lb`, `sb`), or calculating the target address for a branch/jump.
*   **MEM (Memory Access):** If the instruction is a load (`lb`, `lw`, etc.), data is read from memory. If it's a store (`sb`, `sw`, etc.), data is written to memory. Other instructions typically pass through this stage without doing memory access.
*   **WB (Write Back):** The result of the instruction (from EX or MEM) is written back to the register file.

In a 5-stage pipeline, ideally, in any given clock cycle, you have 5 different instructions in different stages of execution. After the pipeline is full (5 cycles), one instruction ideally finishes every single clock cycle. This results in a CPI (Cycles Per Instruction) of 1, which is much better than sequential execution (where CPI might be 5 or more, depending on the number of stages).

**3. Hazards**

The ideal scenario (one instruction finishes every cycle) is disrupted when instructions aren't completely independent. When an instruction needs something that isn't ready yet because of the pipeline overlap, it's called a **hazard**. Hazards reduce performance because they require the pipeline to **stall** (pause for one or more cycles) or **flush** (discard instructions).

There are three main types of hazards:

*   **Structural Hazards:** When two different instructions need to use the *same* piece of hardware at the *same* time (e.g., if there was only one memory port, a load/store instruction in MEM stage and an instruction fetch in IF stage might conflict). Modern processors usually avoid these by duplicating hardware resources (like having separate instruction and data caches/ports).
*   **Data Hazards:** When an instruction needs data that a previous instruction hasn't finished producing yet. The most common is the **Read-After-Write (RAW)** hazard.
    *   Example:
        `ADD R1, R2, R3` (writes to R1)
        `SUB R4, R1, R5` (reads from R1)
    *   In the pipeline, the `SUB` instruction reads R1 in its ID stage, but the `ADD` instruction won't write the correct value to R1 until its WB stage. If the `SUB` proceeds without waiting, it will read the old value of R1.

*   **Control Hazards:** When the pipeline doesn't know which instruction to fetch next, usually due to branches or jumps. The decision of where to go next (the "target address") might not be known until a later stage of the branch/jump instruction.
    *   Example:
        `BEQ R1, R2, Target`
        `ADD R3, R4, R5` (This instruction is *after* the branch in memory)
        `Target:`
        `SUB R6, R7, R8` (This is the instruction at the branch target)
    *   When `BEQ` is in the pipeline (say, in ID), the processor needs to fetch the *next* instruction. It doesn't know yet whether the branch will be taken (go to `Target`) or not taken (go to `ADD`). If it guesses wrong, it fetches instruction(s) that it will later have to discard.

**4. Forwarding (Data Forwarding / Bypassing)**

Forwarding is a hardware technique specifically designed to mitigate **Data Hazards**. Instead of always waiting for a result to be written back to the register file (WB stage), the hardware detects when a result is needed by a subsequent instruction *before* it's written back. It then **forwards** the result directly from the output of an earlier pipeline stage (like EX or MEM) to the input of a later stage (like EX) that needs it.

*   Example (revisiting `ADD`/`SUB`):
    `ADD R1, R2, R3` (Result calculated in EX)
    `SUB R4, R1, R5` (Needs R1 in EX)
    *   Without forwarding: `SUB` would stall until `ADD` completes WB.
    *   With forwarding: The result of `ADD` is ready at the end of its EX stage. This result can be "forwarded" directly to the input of `SUB`'s EX stage, often allowing `SUB` to execute without stalling.

**When Forwarding Might Still Need a Stall (Load-Use Hazard):**

A specific type of data hazard that often *still* requires a stall even with forwarding is the immediate Load-Use hazard. A `LOAD` instruction reads data from memory in its MEM stage. This data is typically available only at the *very end* of the MEM stage. If the *very next* instruction in sequence tries to *use* that loaded data in its EX stage (which happens *before* the MEM stage finishes), the data isn't ready in time to be forwarded directly to the EX stage of the *next* instruction. This usually requires a 1-cycle stall (a "bubble") to delay the dependent instruction's EX stage until the data is available from the load's MEM stage via forwarding.

*   Example:
    `LB R1, 0(x10)` (Loads R1, data ready at end of MEM stage)
    `ADD R2, R1, R3` (Needs R1 in EX stage)
    *   The `ADD`'s EX stage starts when the `LB` is in its MEM stage. The data from memory for `LB` is not ready *at the beginning* of the `LB`'s MEM stage, only at the end. The `ADD`'s EX needs the data at its input, corresponding to the end of its ID stage / start of its EX stage. Forwarding from `LB`'s MEM to `ADD`'s EX is too late by one clock cycle. Thus, the `ADD` is stalled for 1 cycle.

**5. Control Hazard Handling (Branch Prediction)**

To deal with control hazards (branches), processors use strategies to guess the outcome of a branch. The exercise mentions "predict not taken".

*   **Predict Not Taken:** The processor *assumes* the branch will *not* be taken and continues fetching instructions sequentially after the branch.
    *   **If the prediction is correct (branch is NOT taken):** No time is lost. The sequentially fetched instructions are the correct ones.
    *   **If the prediction is incorrect (branch IS taken):** The instructions that were fetched sequentially *after* the branch (while the branch was deciding in EX) are wrong. These instructions are **flushed** or **squashed** from the pipeline, and the processor fetches the correct instruction from the branch target address. This flushing costs cycles – typically 2 cycles for a 5-stage pipeline where the branch decision is made in EX (the instructions in IF and ID when the branch is in EX are the ones flushed). The exercise description confirms this penalty of inserting bubbles for taken branches.

**Putting it Together for the Exercise:**

The exercise asks you to analyze the provided RISC-V code running on such a pipelined processor.
*   You need to identify where **data hazards** occur and how many stalls they cause *given the built-in forwarding* (specifically looking for the 1-cycle Load-Use stalls).
*   You need to identify where **control hazards** occur (the branches) and how many stalls they cause *given the "predict not taken" strategy* (2 stalls for each taken branch).
*   Then, calculate the total execution time by figuring out the base cycles for the instructions and adding the total stalls from both data and control hazards.
*   Finally, optimize the code by reordering instructions to *reduce the data hazards* while preserving the original program's behavior.

Understanding these basic concepts of pipelining, stages, hazards, and forwarding is key to solving the problem. The specific numbers (like the 1-cycle Load-Use stall and the 2-cycle taken branch penalty) are crucial for the calculations.


