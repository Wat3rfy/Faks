TO je gotov pravilno

![[Pasted image 20260615124043.png]]


To ne vem če je prav in se mi ne da preverjat

![[Pasted image 20260614234137.png]]



Če hočem v zadnji nivo spraviti $x$ elementov, potem bomo rabili $\lceil \log_{2}{x}\rceil$ višino - recimo imamo $13$ elementov, hočemo potem vsaj 16 elementov v zadnji vrstici da vse spravimo not, torej rabimo 4 podvojitve oz. višino 4 kar bo navzgor zaokrožen logaritem.





*Ko govorimo o višini **popolnoega drevesa z $n$ listi** ponavadi govorimo o številu povezav do najglobjega vozlišča v tem primeru za dvojiško drevo velja da če imamo na koncu $n$ listov  potem je višina natanko $\lceil \log_{2}{n} \rceil$. To si lahko razlagamo z naslednjim razmislekom. Začnemo z $1$ - če pomnožimo z $2$ dobimo novo povezavo in vsakič ko množimo z $2$ novo. To pomeni da vsaka povezava predstavlja množenje z $2$. To pomeni da če imamo na koncu število $2^{k}$ bo pomenilo da imamo $k$ povezav saj $k$ predstavlja $\,2 \cdot \,\ldots\, \cdot 2$. Če $n$ ni potenca $2$ potem bo veljalo da nam bo $\log_{2}{n}$ dal neko decimalko kjer bo celi del zaznamoval $2^{k}$ decimalni del pa nek ostanek tega $n$-ja iz česar lahko sklepamo da imamo drevo katerega povezav je $k$ in še ena povezava za ostale elemente - torej $k+1$ oz. $\lceil\log_{2}{n}\rceil$.*

*Logaritem nam da dejansko število množenj $1$ s $k$ da dobimo $n$.*

*Po temu velja isto za vse $\log_{k}{n}$ - torej če gledamo po številu povezav bo vedno $\lceil \log_{k}{n}\rceil$ globina.*

*Če gledamo po nivojih pa vedno samo prištejemo še $1$.*

*Pogledamo si lahko še če je v **popolnem drevesu** $n$ vozlišč - torej ni $n$ listov ampak so vsa vozlišča všteta. Naj bo $h$ višina drevesa (po povezavah).*

*Za dvojiška bo veljalo da je $n = \sum_{0}^{h}2^{k}$ kar je $n = 2^{h+1} - 1$ sledi $\log_{2}{(n+1)}-1 =h$. Če drevo ni zapolnjeno do konca potem bo veljalo da je $2^{h}\leq n \leq 2^{h+1} - 1$ kar pomeni da pri logaritmiranju dobimo nekaj med $h$ in $h+1$ mi vemo da hočemo $h$ torej izberemo $\lfloor \log_{2}{n} \rfloor$.*

*Za $k$-tero drevo uporabljamo poenostavitev $h = \lfloor \log_{k}{N} \rfloor$*