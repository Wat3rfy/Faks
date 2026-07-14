
Poznamo korene enote

$$z^{n} = 1$$

To bodo vsa oglišča $n$ kotnika v kompleksni ravnini.

Lahko pa pogledamo samo tista oglišča tako da velja da če ga množimo sam s sabo dobimo vsa oglišča. To bi bil npr. $z = e^{i \frac{\pi}{3}}$ kot nilča $z^{6}= 1$. Ker če ga množimo samega s sabo dobimo natanko vse ničle oz. celoten šestkotnik.

Takim korenom pravimo **primitivni koreni enote**.

Če je neko kompleksno število $\omega$ primitivni $n$-ti koren enote velja da je $\omega^{n}=1$ in da za noben $\omega^{k} \neq 1$.

$$\omega^{n}=1, \omega^{k} \neq 1 \,;\; 1 \leq k \leq n$$

Torej da generira vsa oglišča $n$-tega enotskega večkotnika. Za $z^{6}$ bi to bila $e^{i \frac{\pi}{3}}, e^{i \frac{5\pi}{3}}$ .

S tem lahko definiramo $n$-ti ciklotomični polinom $\Phi_{n}(z)$, katerega ničle so vsi primitivni $n$-ti koreni enote.

$$\Phi_{n}(z) = \prod_{D(n,k)= 1}(x - e^{i \frac{2\pi k}{n}})$$

kjer je $e^{i \frac{2 \pi k}{n}}$ eden od primitivnih korenov.


> **Trditev:**
> Vsak polinom oblike $x^{n}-1$ se razcepi na prod. ciklotomičnih polinomov vseh deliteljev števila $n$
> 
> $$x^{n}-1 = \prod_{d|n}\Phi_{d}(x)$$
> 
> To omogoča rekurzivno računanje ciklotomičnih polinomov
> 
> $$\Phi_{n}= \frac{x^{n}-1}{\prod_{\substack{d|n \\ d<n}}\Phi_{d}(x)}$$


> **Trditev**
> 
> Velja
> 
>   $$\Phi_p(x) = x^{p-1} + x^{p-2} + \dots + x + 1 = \frac{x^p - 1}{x - 1}$$


> **Trditev**
> 
>   $$\Phi_{p^k}(x) = \Phi_p(x^{p^{k-1}})$$
>   
> Primer: $\Phi_9(x) = \Phi_3(x^3) = x^6 + x^3 + 1$
