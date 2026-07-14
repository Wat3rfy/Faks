Nadgradimo operacijsko semantiko s pravili boolovih izrazov in ukazov.

Here is the content from the images converted into LaTeX math blocks within Markdown:

###  Aritmetični izrazi

$$\frac{}{\eta \mid n \hookrightarrow n}$$

$$\frac{\eta(x) = n}{\eta \mid x \hookrightarrow n}$$

$$\frac{\eta \mid e_1 \hookrightarrow n_1 \quad \eta \mid e_2 \hookrightarrow n_2}{\eta \mid e_1 + e_2 \hookrightarrow n_1 + n_2}$$

$$\frac{\eta \mid e_1 \hookrightarrow n_1 \quad \eta \mid e_2 \hookrightarrow n_2}{\eta \mid e_1 - e_2 \hookrightarrow n_1 - n_2}$$

$$\frac{\eta \mid e_1 \hookrightarrow n_1 \quad \eta \mid e_2 \hookrightarrow n_2}{\eta \mid e_1 * e_2 \hookrightarrow n_1 \cdot n_2}$$



### Boolovi izrazi

$$\frac{}{\eta \mid \text{true} \hookrightarrow \text{true}}$$

$$\frac{}{\eta \mid \text{false} \hookrightarrow \text{false}}$$

$$\frac{\eta \mid b \hookrightarrow \text{false}}{\eta \mid \text{not } b \hookrightarrow \text{true}}$$

$$\frac{\eta \mid b \hookrightarrow \text{true}}{\eta \mid \text{not } b \hookrightarrow \text{false}}$$

$$\frac{\eta \mid b_1 \hookrightarrow \text{false}}{\eta \mid b_1 \text{ and } b_2 \hookrightarrow \text{false}}$$

$$\frac{\eta \mid b_1 \hookrightarrow \text{true} \quad \eta \mid b_2 \hookrightarrow v_2}{\eta \mid b_1 \text{ and } b_2 \hookrightarrow v_2}$$

$$\frac{\eta \mid b_1 \hookrightarrow \text{true}}{\eta \mid b_1 \text{ or } b_2 \hookrightarrow \text{true}}$$

$$\frac{\eta \mid b_1 \hookrightarrow \text{false} \quad \eta \mid b_2 \hookrightarrow v_2}{\eta \mid b_1 \text{ or } b_2 \hookrightarrow v_2}$$

$$\frac{\eta \mid e_1 \hookrightarrow n_1 \quad \eta \mid e_2 \hookrightarrow n_2 \quad n_1 < n_2}{\eta \mid e_1 < e_2 \hookrightarrow \text{true}}$$

$$\frac{\eta \mid e_1 \hookrightarrow n_1 \quad \eta \mid e_2 \hookrightarrow n_2 \quad n_1 \ge n_2}{\eta \mid e_1 < e_2 \hookrightarrow \text{false}}$$

***

Semantika malih korakov za ukaze je podana z relacijo

$$(\eta, c) \mapsto (\eta', c')$$

ki jo preberemo: »v okolju $\eta$ ukaz $c$ v enem koraku spremeni okolje v $\eta'$ in se nadaljuje z ukazom $c'$«.

Relacija je določena z naslednjimi pravili:

$$
\frac{\eta \mid e \hookrightarrow n}{(\eta, (x := e)) \mapsto (\eta[x \mapsto n], \text{skip})}
$$

$$
\frac{(\eta, c_1) \mapsto (\eta', c_1')}{(\eta, (c_1 ; c_2)) \mapsto (\eta', (c_1' ; c_2))}
$$

$$
\frac{}{(\eta, (\text{skip} ; c_2)) \mapsto (\eta, c_2)}
$$

$$
\frac{\eta \mid b \hookrightarrow \text{true}}{(\eta, (\text{if } b \text{ then } c_1 \text{ else } c_2 \text{ end})) \mapsto (\eta, c_1)}
$$

$$
\frac{\eta \mid b \hookrightarrow \text{false}}{(\eta, (\text{if } b \text{ then } c_1 \text{ else } c_2 \text{ end})) \mapsto (\eta, c_2)}
$$

$$
\frac{\eta \mid b \hookrightarrow \text{false}}{(\eta, (\text{while } b \text{ do } c \text{ done})) \mapsto (\eta, \text{skip})}
$$

$$
\frac{\eta \mid b \hookrightarrow \text{true}}{(\eta, (\text{while } b \text{ do } c \text{ done})) \mapsto (\eta, (c ; \text{while } b \text{ do } c \text{ done}))}
$$

Pravila določajo, kako se ukaz $c_1$ v okolju $\eta_1$ izvaja kot zaporedje korakov:

$$(\eta_1, c_1) \mapsto (\eta_2, c_2) \mapsto (\eta_3, c_3) \mapsto \dots$$

Zaporedje se lahko nadaljuje v nedogled ali pa se ustavi pri ukazu $\text{skip}$, saj je to edini ukaz, ki nima naslednjega koraka.