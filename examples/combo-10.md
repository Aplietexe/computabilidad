# Combo 10

- Un estado es un par

  $$
  (\overrightarrow{s},\overrightarrow{\sigma})=((s_1,s_2,\ldots),(\sigma_1,\sigma_2,\ldots))\in\omega^{[\mathbf{N}]}\times\Sigma^{\ast[\mathbf{N}]}.
  $$

  Si $i\ge1$, entonces diremos que $s_i$ es el contenido o valor de la variable $\mathrm{N}\overline{i}$ en el estado $(\overrightarrow{s},\overrightarrow{\sigma})$ y $\sigma_i$ es el contenido o valor de la variable $\mathrm{P}\overline{i}$ en el estado $(\overrightarrow{s},\overrightarrow{\sigma})$. Es decir, intuitivamente hablando, un estado es un par de infinituplas que contiene la información de que valores tienen alojados las distintas variables.

- Una descripción instantánea es una terna $(i,\overrightarrow{s},\overrightarrow{\sigma})$ tal que $(\overrightarrow{s},\overrightarrow{\sigma})$ es un estado e $i\in\omega$. Es decir que $\omega\times\omega^{[\mathbf{N}]}\times\Sigma^{\ast[\mathbf{N}]}$ es el conjunto formado por todas las descripciones instantáneas.

- Dado un programa $\mathcal{P}$ definiremos la función

  $$
  S_\mathcal{P}:\omega\times\omega^{[\mathbf{N}]}\times\Sigma^{\ast[\mathbf{N}]}\to\omega\times\omega^{[\mathbf{N}]}\times\Sigma^{\ast[\mathbf{N}]}
  $$

  la cual le asignará a una descripción instantánea $(i,\overrightarrow{s},\overrightarrow{\sigma})$ la descripción instantánea sucesora de $(i,\overrightarrow{s},\overrightarrow{\sigma})$ con respecto a $\mathcal{P}$. Cuando $i\in\{1,\ldots,n(\mathcal{P})\}$, intuitivamente hablando, $S_\mathcal{P}(i,\overrightarrow{s},\overrightarrow{\sigma})$ será la descripción instantánea que resulta luego de realizar $I_i^\mathcal{P}$ estando en el estado $(\overrightarrow{s},\overrightarrow{\sigma})$. Definición matemática de $S_\mathcal{P}(i,\overrightarrow{s},\overrightarrow{\sigma})$, según casos:

  - Caso $i\notin\{1,\ldots,n(\mathcal{P})\}$. Entonces $S_\mathcal{P}(i,\overrightarrow{s},\overrightarrow{\sigma})=(i,\overrightarrow{s},\overrightarrow{\sigma})$

  - Caso $Bas(I_i^\mathcal{P})=\mathrm{N}\overline{k}\leftarrow \mathrm{N}\overline{k}\mathbin{\dot{-}}1$. Entonces

    $$
    S_\mathcal{P}(i,\overrightarrow{s},\overrightarrow{\sigma})=(i+1,(s_1,\ldots,s_{k-1},s_k\mathbin{\dot{-}}1,s_{k+1},\ldots),\overrightarrow{\sigma})
    $$

  - Caso $Bas(I_i^\mathcal{P})=\mathrm{N}\overline{k}\leftarrow \mathrm{N}\overline{k}+1$. Entonces

    $$
    S_\mathcal{P}(i,\overrightarrow{s},\overrightarrow{\sigma})=(i+1,(s_1,\ldots,s_{k-1},s_k+1,s_{k+1},\ldots),\overrightarrow{\sigma})
    $$

  - Caso $Bas(I_i^\mathcal{P})=\mathrm{N}\overline{k}\leftarrow \mathrm{N}\overline{n}$. Entonces

    $$
    S_\mathcal{P}(i,\overrightarrow{s},\overrightarrow{\sigma})=(i+1,(s_1,\ldots,s_{k-1},s_n,s_{k+1},\ldots),\overrightarrow{\sigma})
    $$

  - Caso $Bas(I_i^\mathcal{P})=\mathrm{N}\overline{k}\leftarrow 0$. Entonces

    $$
    S_\mathcal{P}(i,\overrightarrow{s},\overrightarrow{\sigma})=(i+1,(s_1,\ldots,s_{k-1},0,s_{k+1},\ldots),\overrightarrow{\sigma})
    $$

  - Caso $Bas(I_i^\mathcal{P})=\mathrm{IF}\ \mathrm{N}\overline{k}\ne0\ \mathrm{GOTO}\ \mathrm{L}\overline{m}$. Entonces tenemos dos subcasos.

  - Subcaso a. El valor de $\mathrm{N}\overline{k}$ en $(\overrightarrow{s},\overrightarrow{\sigma})$ es 0. Entonces

    $$
    S_\mathcal{P}(i,\overrightarrow{s},\overrightarrow{\sigma})=(i+1,\overrightarrow{s},\overrightarrow{\sigma})
    $$

  - Subcaso b. El valor de $\mathrm{N}\overline{k}$ en $(\overrightarrow{s},\overrightarrow{\sigma})$ es no nulo. Entonces

    $$
    S_\mathcal{P}(i,\overrightarrow{s},\overrightarrow{\sigma})=(\min\{l:I_l^\mathcal{P}\text{ tiene label }\mathrm{L}\overline{m}\},\overrightarrow{s},\overrightarrow{\sigma})
    $$

  - Caso $Bas(I_i^\mathcal{P})=\mathrm{P}\overline{k}\leftarrow \curvearrowright\mathrm{P}\overline{k}$. Entonces

    $$
    S_\mathcal{P}(i,\overrightarrow{s},\overrightarrow{\sigma})=(i+1,\overrightarrow{s},(\sigma_1,\ldots,\sigma_{k-1},\curvearrowright\sigma_k,\sigma_{k+1},\ldots))
    $$

  - Caso $Bas(I_i^\mathcal{P})=\mathrm{P}\overline{k}\leftarrow \mathrm{P}\overline{k}.a$. Entonces

    $$
    S_\mathcal{P}(i,\overrightarrow{s},\overrightarrow{\sigma})=(i+1,\overrightarrow{s},(\sigma_1,\ldots,\sigma_{k-1},\sigma_k a,\sigma_{k+1},\ldots))
    $$

  - Caso $Bas(I_i^\mathcal{P})=\mathrm{P}\overline{k}\leftarrow \mathrm{P}\overline{n}$. Entonces

    $$
    S_\mathcal{P}(i,\overrightarrow{s},\overrightarrow{\sigma})=(i+1,\overrightarrow{s},(\sigma_1,\ldots,\sigma_{k-1},\sigma_n,\sigma_{k+1},\ldots))
    $$

  - Caso $Bas(I_i^\mathcal{P})=\mathrm{P}\overline{k}\leftarrow \varepsilon$. Entonces

    $$
    S_\mathcal{P}(i,\overrightarrow{s},\overrightarrow{\sigma})=(i+1,\overrightarrow{s},(\sigma_1,\ldots,\sigma_{k-1},\varepsilon,\sigma_{k+1},\ldots))
    $$

  - Caso $Bas(I_i^\mathcal{P})=\mathrm{IF}\ \mathrm{P}\overline{k}\ \mathrm{BEGINS}\ a\ \mathrm{GOTO}\ \mathrm{L}\overline{m}$. Entonces tenemos dos subcasos.

  - Subcaso a. El valor de $\mathrm{P}\overline{k}$ en $(\overrightarrow{s},\overrightarrow{\sigma})$ comienza con $a$. Entonces

    $$
    S_\mathcal{P}(i,\overrightarrow{s},\overrightarrow{\sigma})=(\min\{l:I_l^\mathcal{P}\text{ tiene label }\mathrm{L}\overline{m}\},\overrightarrow{s},\overrightarrow{\sigma})
    $$

  - Subcaso b. El valor de $\mathrm{P}\overline{k}$ en $(\overrightarrow{s},\overrightarrow{\sigma})$ no comienza con $a$. Entonces

    $$
    S_\mathcal{P}(i,\overrightarrow{s},\overrightarrow{\sigma})=(i+1,\overrightarrow{s},\overrightarrow{\sigma})
    $$

  - Caso $Bas(I_i^\mathcal{P})=\mathrm{GOTO}\ \mathrm{L}\overline{m}$. Entonces

    $$
    S_\mathcal{P}(i,\overrightarrow{s},\overrightarrow{\sigma})=(\min\{l:I_l^\mathcal{P}\text{ tiene label }\mathrm{L}\overline{m}\},\overrightarrow{s},\overrightarrow{\sigma})
    $$

  - Caso $Bas(I_i^\mathcal{P})=\mathrm{SKIP}$. Entonces

    $$
    S_\mathcal{P}(i,\overrightarrow{s},\overrightarrow{\sigma})=(i+1,\overrightarrow{s},\overrightarrow{\sigma})
    $$

- Diremos que

  $$
  \underbrace{S_\mathcal{P}(\cdots S_\mathcal{P}(S_\mathcal{P}(1,\overrightarrow{s},\overrightarrow{\sigma}))\cdots)}_{t\ \text{veces}}
  $$

  es la descripción instantánea obtenida luego de $t$ pasos, partiendo del estado $(\overrightarrow{s},\overrightarrow{\sigma})$. Si

  $$
  \underbrace{S_\mathcal{P}(\cdots S_\mathcal{P}(S_\mathcal{P}(1,\overrightarrow{s},\overrightarrow{\sigma}))\cdots)}_{t\ \text{veces}}=(j,\overrightarrow{u},\overrightarrow{\eta})
  $$

  diremos que $(\overrightarrow{u},\overrightarrow{\eta})$ es el estado obtenido luego de $t$ pasos, partiendo del estado $(\overrightarrow{s},\overrightarrow{\sigma})$.

- Cuando la primera coordenada de

  $$
  \underbrace{S_\mathcal{P}(\cdots S_\mathcal{P}(S_\mathcal{P}(1,\overrightarrow{s},\overrightarrow{\sigma}))\cdots)}_{t\ \text{veces}}
  $$

  sea igual a $n(\mathcal{P})+1$, diremos que $\mathcal{P}$ se detiene (luego de $t$ pasos), partiendo desde el estado $(\overrightarrow{s},\overrightarrow{\sigma})$.
