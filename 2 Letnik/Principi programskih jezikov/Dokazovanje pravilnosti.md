**Specifikacija in implementacija**

Ločimo med **specifikacijo** in **implementacijo** programa:

- **Specifikacija** je opis, kaj naj želeni program počne.
- **Implementacija** je program, ki počne to, kar zahteva specifikacija.

Specifikacija je lahko podana natančno, v človeškem jeziku ali zapisana v formalnem matematičnem jeziku. Specifikacije imajo več namenov:

- opis programa, ki naj bi ga sestavili
- preverjanje pravilnosti implementacije
- zagotovimo kompatibilnost med različnimi deli programske opreme - vemo kaj pričakovati od nekega dela programa definiranega vsak s svojo specifikacijo

**Hoarova logika**

V Hoarovi logiki delovanje programa opišemo s **Hoarovimi trojicami**

$$\{ P\} \;c\;  \{ Q\}$$

Tu sta $P$ in $Q$ logični formuli in $\subset$ ukaz. Formuli $P$ pravimo **predpogoj** (angl. _precondition_), formuli $Q$ pravimo **končni pogoj** (ang. _postcondition_). Skupaj tvorita specifikacijo, program $c$ pa je implementacija.

Pravilnost programa lažje obravnavamo v dveh korakih

1. Ali program deluje pravilno, če se ustavi?
2. Ali se program ustavi?

V ta namen poznamo dve vrsti Hoarovih trojic:


1. **Delna pravilnost**
$$\text{Če velja $P$ in se ukaz $c$ konča, potem velja $Q$.}$$

$$\Leftrightarrow$$

$$\{ P \} \, c \, \{ Q \}$$

2. **Popolna pravilnost**

$$\text{Če velja $P$ potem se ukaz $c$ konča in velja $Q$.}$$

$$\Leftrightarrow$$

$$[ P ] \, c \, [ Q ]$$



Delna pravilnost ne zagotavlja, da se bo $c$ končal, popolna pravilnost to zagotavlja.

Ko v programu nočemo da se pojavi neka spremenljivka $n$ pravimo da je **duh** oz. *ghost variable*.



Hoarove trojice običajno pišemo navpično, takole:

$\begin{aligned}
&\{ x = m \land y = n \} \\
&\;c \\
&\{ x = \min(m, n) \land y = \max(m, n) \}
\end{aligned}$

Če imamo opravka z večimi vrsticami kode, vrivamo predpogoje med vrstice:

$\begin{aligned}
&\{ P_1 \} \\
&\;c_1 \\
&\{ P_2 \} \\
&\;c_2 \\
&\{ P_3 \} \\
&\;c_3 \\
&\dots
\end{aligned}$

in jih beremo kot zaporedje Hoarovih trojic: velja $\{ P_1 \} \, c_1 \, \{ P_2 \}$ in velja $\{ P_2 \} \, c_2 \, \{ P_3 \}$ in velja $\{ P_3 \} \, c_3 \, \{ P_4 \}$ in tako naprej.



**Splošna pravila sklepanja**

$$
\frac{P' \Rightarrow P \quad \{ P \} \, c \, \{ Q \} \quad Q \Rightarrow Q'}{\{ P' \} \, c \, \{ Q' \}}
$$

$$ $$

$$
\frac{\{ P_1 \} \, c \, \{ Q_1 \} \quad \{ P_2 \} \, c \, \{ Q_2 \}}{\{ P_1 \land P_2 \} \, c \, \{ Q_1 \land Q_2 \}}
$$

$$ $$

$$
\frac{}{\{ P \} \, \text{skip} \, \{ P \}}
$$



Naj bodo **$\text{FV(P)}$** vse spremenljivke, ki se pojavljajo v formuli $P$ (**free variables**) in **$\text{FA(c)}$** vse spremenljivke, ki jih $c$ nastavlja (**assigned variables**). Na primer:

$$
FV(x \le y \lor x > 0) = \{ x, y \}
$$

$$
FA(\text{if } x < y \text{ then } x := y + 3 \text{ else skip end}) = \{ x \}
$$

Velja

$$
\frac{FV(P) \cap FA(c) = \emptyset}{\{ P \} \, c \, \{ P \}}
$$

$$ $$

If else stavek

$$
\frac{\{ P \land b \} \, c_1 \, \{ Q \} \quad \{ P \land \neg b \} \, c_2 \, \{ Q \}}{\{ P \} \, \text{if } b \text{ then } c_1 \text{ else } c_2 \text{ end} \, \{ Q \}}
$$

Kompozicija

$$
\frac{\{ P \} \, c_1 \, \{ Q \} \quad \{ Q \} \, c_2 \, \{ R \}}{\{ P \} \, c_1 \, ; \, c_2 \, \{ R \}}
$$

Zanka

$$
\frac{\{ P \land b \} \, c \, \{ P \}}{\{ P \} \, \text{while } b \text{ do } c \text{ done } \{ \neg b \land P \}}
$$

*To si lahko interpretiramo kot indukcijo, če velja $PcP$ potem induktivno velja po zanki da če velja $P$ po zanki velja $P$. *
*To je orodje za dokazovanje ne nek gradnik strukture.*
*Mi to orodje uporabljamo da ob izvedbi zanke lahko dejansko dokažemo kaj sledi zanki, ne glede na to kolikorat se izvede - če lahko dokažemo da se neka invarianta ohrani lahko z indukcijo pokažemo da se ohrani čez celo zanko.*

Prirejanje

$$
\frac{}{\{ P[x \mapsto e] \} \, x := e \, \{ P \}}
$$


Primer 1

```
{ n ≥ 0 }
{ n ≥ 0 , 0 = 0}
{ n ≥ 0 , s = 0[s ↦ 0]}
s := 0 ;
{ n ≥ 0 , s = 0}
{ n ≥ 0 , s = 0, 1 = 1}
{ n ≥ 0 , s = 0, i = 1[i ↦ 1]}
i := 1 ;
{ n ≥ 0 , s = 0, i = 1}

{s = 0+1+...+(i-1), n ≥ 0}
while (i ≤ n) do
    {s = 1+...+(i-1), n ≥ 0, i ≤ n}
    {s+i = 1+...+(i-1)+i, n ≥ 0, i ≤ n}
    {s = 1+...+(i-1)+i, n ≥ 0, i ≤ n[s ↦ s+i]}
    
    s = s + i ;

    {s = 1+...+(i-1)+i, n ≥ 0, i ≤ n}
    {s = 1+...+i+1-1, n ≥ 0, i+1 ≤ n+1}
    {s = 1+...+(i-1), n ≥ 0, i ≤ n+1[i ↦ i+1]}

    i = i + 1

    {s = 1+...+(i-1), n ≥ 0, i ≤ n+1}
done
{s = 1+...+(i-1), n ≥ 0, i > n, i ≤ n+1}
{s = 1+...+(i-1), n ≥ 0, i = n+1}
{s = 1+...+n, n ≥ 0, i = n+1}
{s = 1+...+n, n ≥ 0, i = n+1}
{s = 1 + 2 + ... + n }
```

Primer 2

```  
r := x;
q := 0;
{x = qy + r, r = x, q = 0, x ≥ 0, y > 0}
while y <= r do
    {x = qy + r, y ≤ r}
    {x - y = qy + r - y, 0 ≤ r - y}
    {x - y = qy + r, 0 ≤ r [r ↦ r-y]}
    r := r - y;
    {x - y = qy + r, 0 ≤ r}
    {x - y = (q-1+1)y + r, 0 ≤ r}
    {x - y = (q-1)y + r, 0 ≤ r[q ↦ q+1]}
    q := q + 1;
    {x - y = (q-1)y + r, 0 ≤ r}
    {x = qy + r, 0 ≤ r}
    {x = qy + r, 0 ≤ r}
done
{x = qy + r, 0 ≤ r, y > r}
{x = qy + r}
```





**Popolna pravilnost**

Pogojni stavek
$$
\frac{\;\;[ P \land b ] \, c_1 \, [ Q ] \quad [ P \land \neg b ] \, c_2 \, [ Q ]\;\;}{[ P ] \, \text{if } b \text{ then } c_1 \text{ else } c_2 \text{ end} \, [ Q ]}
$$

Neodvisne spremenljivke
$$
\;\;\frac{FV(P) \cap FA(c) = \emptyset\;\;}{\{ P \} \, c \, \{ P \}}
$$

Neodvisne spremenljivke in ustavljivost
$$
\frac{\;\;FV(P) \cap FA(c) = \emptyset \quad [ R ] \, c \, [ Q ]\;\;}{[ R \land P ] \, c \, [ Q \land P ]}
$$

Zanka

*Naj bo $e$ količina, ki se ne more v nedogled zmanjševati (na primer naravno število):*

$$
\frac{[ P \land b \land e = z ] \, c \, [ P \land e < z ] \quad z \notin FA(c)}{[ P ] \, \text{while } b \text{ do } c \text{ done } [ \neg b \land P ]}
$$

Primer od prej le da vpeljemo neko vrednost ki se manjša
```

r := x;
q := 0;
[x = qy + r, r = x, q = 0, x ≥ 0, y > 0]
while y <= r do
    {x = qy + r, y ≤ r, r = z}
    {x - y = qy + r - y, 0 ≤ r - y, r-y = z-y}
    {x - y = qy + r, 0 ≤ r, r = z-y [r ↦ r-y]}
    r := r - y;
    {x - y = qy + r, r ≥ 0, r = z-y}
    {x - y = (q-1+1)y + r, r ≥ 0, r = z-y}
    {x - y = (q-1)y + r, r ≥ 0, r = z-y[q ↦ q+1]}
    q := q + 1;
    {x - y = (q-1)y + r, r ≥ 0, r = z-y}
    {x = qy + r, r ≥ 0, r = z-y}
    [x = qy + r, r ≥ 0, r = z-y, z-y < z]
    [x = qy + r, r ≥ 0, r < z]
done
[x = qy + r, r ≥ 0, y > r]
[x = qy + r]
```


Za določanje invariante lahko poskusimo ugotoviti do kdaj zanka teče, pogledamo če je v končnem pogoju ta vrednost in v končni pogoj namesto končne vrednosti vstavimo spremenljivko loopa.

Če je končni pogoj sestavljen iz $P$ in $\neg b$ potem lahko uporabimo $P$ kot invarianto.

Lahko delamo s tabelo.

Skoraj vedno pa invarianta vključuje tudi meje spremenljivke zanke torej vemo da bomo dobili neko zgornjo mejo za $i$, ki bo verjetno del invariante.