# Combo 16

Dado un predicado $P:D_P\subseteq\omega\times\Sigma^\ast\to\omega$, el macro

$$
[\mathrm{IF}\ P(V1,W1)\ \mathrm{GOTO}\ A1]
$$

es de tipo PALABRA y cumple las siguientes propiedades:

1. Las variables oficiales son $V1,W1$

2. $A1$ es el único label oficial

3. Si reemplazamos:

    1. las variables oficiales (i.e. $V1,W1$) por variables concretas

        $$
        \mathrm{N}\overline{k_1},\mathrm{P}\overline{j_1}
        $$

        con $k_1,j_1\in\mathbf{N}$

    2. el label oficial $A1$ por el label concreto $\mathrm{L}\overline{k}$

    3. las variables auxiliares por variables concretas (distintas de a dos) y NO pertenecientes a la lista $\mathrm{N}\overline{k_1},\mathrm{P}\overline{j_1}$

    4. los labels auxiliares por labels concretos (distintos de a dos) y ninguno igual a $\mathrm{L}\overline{k}$

    Entonces la palabra así obtenida es un programa de $S^\Sigma$, salvo por la ley de los GOTO respecto de $\mathrm{L}\overline{k}$, que denotaremos con

    $$
    [\mathrm{IF}\ P(\mathrm{N}\overline{k_1},\mathrm{P}\overline{j_1})\ \mathrm{GOTO}\ \mathrm{L}\overline{k}]
    $$

    el cual debe tener la siguiente propiedad:

    1. Si hacemos correr $[\mathrm{IF}\ P(\mathrm{N}\overline{k_1},\mathrm{P}\overline{j_1})\ \mathrm{GOTO}\ \mathrm{L}\overline{k}]$ partiendo de un estado $e$ que le asigne a las variables $\mathrm{N}\overline{k_1},\mathrm{P}\overline{j_1}$ valores $x_1,\alpha_1$, entonces independientemente de los valores que les asigne $e$ al resto de las variables se dará que

        1. si $(x_1,\alpha_1)\notin D_P$, entonces $[\mathrm{IF}\ P(\mathrm{N}\overline{k_1},\mathrm{P}\overline{j_1})\ \mathrm{GOTO}\ \mathrm{L}\overline{k}]$ no se detiene

        2. si $(x_1,\alpha_1)\in D_P$ y $P(x_1,\alpha_1)=1$, entonces luego de una cantidad finita de pasos, $[\mathrm{IF}\ P(\mathrm{N}\overline{k_1},\mathrm{P}\overline{j_1})\ \mathrm{GOTO}\ \mathrm{L}\overline{k}]$ direcciona al label $\mathrm{L}\overline{k}$ quedando en un estado $e^{\prime}$ el cual solo puede diferir de $e$ en los valores que le asigna a las variables que fueron a reemplazar a las variables auxiliares. Al resto de las variables, no las modifica

        3. si $(x_1,\alpha_1)\in D_P$ y $P(x_1,\alpha_1)=0$, entonces luego de una cantidad finita de pasos, $[\mathrm{IF}\ P(\mathrm{N}\overline{k_1},\mathrm{P}\overline{j_1})\ \mathrm{GOTO}\ \mathrm{L}\overline{k}]$ se detiene quedando en un estado $e^{\prime}$ el cual solo puede diferir de $e$ en los valores que le asigna a las variables que fueron a reemplazar a las variables auxiliares

La palabra $[\mathrm{IF}\ P(\mathrm{N}\overline{k_1},\mathrm{P}\overline{j_1})\ \mathrm{GOTO}\ \mathrm{L}\overline{k}]$ es llamada la expansión del macro con respecto a la elección de variables y labels realizada
