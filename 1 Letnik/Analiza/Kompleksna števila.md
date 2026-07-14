
## Kompleksna števila

Kompleksna števila so števila oblike

$$a+bi \,;\; a,b \in \mathbb{R}$$

kjer je $i$ imaginarna enota za katero velja

$$i^{2}= -1$$

Služi kot število $\sqrt[]{-1}$.

To pomeni da lahko sedaj razčlenimo 

$$a^{2}+b^{2} = (a+bi)(a-bi)$$

$a,b$ predstavljata koordinati v kompleksni ravnini.

Velja

$$\text{Re} \,z = a$$
$$\text{Im} \,z = b$$


Re $z = \frac{z+\bar{z}}{2}$ in Im $z = \frac{z-\bar{z}}{2i}$.


Kompleksno število pa lahko zapišemo tudi z njenim kotom in velikostjo.

$$|z| = \sqrt[]{a^{2}+b^{2}}$$
$$|z|^{2} = a^{2} + b^{2}$$

S tem lahko zapišemo $a$ in $b$

$$a = |z| \cdot \cos \varphi$$
$$b = |z| \cdot \sin \varphi$$

$z$ pa kot 

$$z = {\color{green}a}  +{\color{blue}bi} = {\color{green}|z| \cdot \cos\,\! \varphi} + {\color{blue}|z| \cdot \sin\,\! \varphi \cdot  i}$$
$$z = |z| ( \cos\,\! \varphi + \sin\,\! \varphi \cdot i)$$

*Preko znanja o funkcijskih vrstah lahko zapišemo $\cos$ in $\sin$ kot funkcijski vrsti, kjer množenje členov $\sin$ z $i$*

Kompleksno število lahko konjugiramo:

$$\overline{z} = a-bi$$
$$\overline{z} = |z|e^{-\varphi i}$$

Velja tudi

$$z \overline{z} = |z|^{2}=a^{2}+b^{2}$$
$$\overline{z+w} = \overline{z}+ \overline{w}$$
$$\overline{z-w} = \overline{z}- \overline{w}$$
$$\overline{zw} = \overline{z}\cdot  \overline{w}$$
$$\overline{\left(\frac{z}{w}\right)\,\,} = \frac{\overline{z}}{\overline{w}}$$
$${\overline{z^{n}}} = \overline{z}^n$$

Velja

$$|\overline{z}| = |z|$$
$$|zw| = |z||w|$$
$$|a|\leq |z| \text{ in } |b| \leq |z|$$
$$|z|+|w| \leq |z+w|$$
$$|z^{n}| = |z|^{n}$$

**de Moiverova formula**

$$(\cos \alpha + i \sin\,\! \alpha )^{n} = \cos\,\! n \alpha + i \sin\,\! n \alpha$$

*Množenje je množenje dolžin in seštevanje argumentov.*

Množenje z $i$ je vrtenje za $90\degree$
Množenje z $e^{i\alpha}$ je vrtenje za $\alpha\degree$

**Karakterizacija imaginarnega, realnega števila**

$$x \in \mathbb{R} \iff x = \overline{x}$$
$$x \in \mathbb{I} \iff -x = \overline{x}$$