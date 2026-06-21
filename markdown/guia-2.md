# GUÍA 2 DE LENGUAJES: DOS CODIFICACIONES IMPORTANTES

Veremos dos formas de codificar objetos matemáticos con números. En la primera codificaremos ciertas infinituplas de elementos de $\omega$ con números naturales y en la segunda codificaremos con elementos de $\omega$ a las palabras de un alfabeto finito $\Sigma$ para el cual tenemos un orden total dado.

## Codificación de infinituplas de números

Usaremos $\omega^{\mathbf{N}}$ para denotar el conjunto de todas las infinituplas con coordenadas en $\omega$. Es decir

$$
\omega^{\mathbf{N}} = \{(s_1, s_2, \ldots) : s_i \in \omega, \text{ para cada } i \ge 1\}.
$$

Definamos el siguiente subconjunto de $\omega^{\mathbf{N}}$

$$
\omega^{[\mathbf{N}]} = \{(s_1, s_2, \ldots) \in \omega^{\mathbf{N}} : \text{ hay un } n \in \mathbf{N} \text{ tal que } s_i = 0, \text{ para } i \ge n\}.
$$

Nótese que $\omega^{\mathbf{N}} \ne \omega^{[\mathbf{N}]}$, por ejemplo las infinituplas

$$
\begin{gathered}
(10, 20, 30, 40, 50, \ldots)\\
(1, 0, 1, 0, 1, 0, 1, 0, \ldots)
\end{gathered}
$$

no pertenecen a $\omega^{[\mathbf{N}]}$. Nótese que $(s_1, s_2, \ldots) \in \omega^{[\mathbf{N}]}$ si y solo si solo una cantidad finita de coordenadas de $(s_1, s_2, \ldots)$ son no nulas (i.e. $\{i : s_i \ne 0\}$ es finito).

Definamos

$$
\begin{aligned}
pr : \mathbf{N} &\to \omega\\
n &\mapsto n\text{-ésimo número primo}
\end{aligned}
$$

Nótese que $pr(1) = 2$, $pr(2) = 3$, $pr(3) = 5$, etc.

Es bien conocido que todo número natural es expresable como producto de primos. Por ejemplo si tomamos $x = 57596$ tenemos que $x = 2.2.7.11.11.17$. También es un hecho conocido que dicha representación en producto de primos es única, si escribimos a los factores primos de menor a mayor, tal como lo hicimos recién con el número 57596. El Teorema Fundamental de la Aritmética justamente asevera esta propiedad de factorización única de todo número natural. Trataremos de escribir este teorema de una forma un poco más "cheta".

Ya que $57596 = 2.2.7.11.11.17$, podemos escribir

$$
57596 = pr(1)^2.pr(4)^1.pr(5)^2.pr(7)^1
$$

Nótese que ahora cada primo que interviene en la factorización de 57596 figura con un exponente que nos dice cuántas veces ocurre en dicha factorización. Hay muchos primos que no ocurren en esta factorización, es decir ocurren 0 veces en la misma. Pero podemos escribir

$$
57596 = pr(1)^2.pr(2)^0.pr(3)^0.pr(4)^1.pr(5)^2.pr(6)^0.pr(7)^1.pr(8)^0.pr(9)^0.pr(10)^0\ldots
$$

y la igualdad no se altera ya que agregamos factores iguales a 1 (una cantidad infinita!). De esta manera hemos logrado que cada primo intervenga en la factorización. Además si vemos la infinitupla de exponentes de esta nueva factorización, es decir

$$
(2, 0, 0, 1, 2, 0, 1, 0, 0, 0, \ldots)
$$

obtenemos un elemento de $\omega^{[\mathbf{N}]}$.

Por supuesto esto lo podemos hacer con cualquier número natural y siempre la infinitupla de exponentes será un elemento de $\omega^{[\mathbf{N}]}$. Además es fácil notar, basándose en el Teorema Fundamental de la Aritmética, que estas representaciones "chetas" también resultan únicas. Más concretamente tenemos:

**Teorema 1 (Teorema Fundamental de la Aritmética Versión Cheta).** Para cada $x \in \mathbf{N}$, hay una única infinitupla $(s_1, s_2, \ldots) \in \omega^{[\mathbf{N}]}$ tal que

$$
x = \prod_{i=1}^{\infty} pr(i)^{s_i}
$$

(Tiene sentido escribir $\prod_{i=1}^{\infty} pr(i)^{s_i}$, ya que en esta productoria solo una cantidad finita de factores son no iguales a 1. Por una prueba de este teorema ver el apunte.)

**Ejercicio 1:** Use el teorema anterior para probar que

**(a)** $17^{1045} \ne 13^{2000}$

**(b)** $5^{55}.13^{90}.17^{1045} \ne 5^{55}.3^{122}.31^{400}$

**(c)** $2^{90}.3^{20}.17^{1045} \ne 2^{100}.3^{12}.17^{1044}$

**Ejercicio 2:** Enuncie en forma precisa qué significa la "unicidad" en el teorema anterior.

A continuación un poco de notación. Dada una infinitupla $(s_1, s_2, \ldots) \in \omega^{[\mathbf{N}]}$ usaremos $\langle s_1, s_2, \ldots\rangle$ para denotar al número $\prod_{i=1}^{\infty} pr(i)^{s_i}$. Dado $x \in \mathbf{N}$, usaremos $(x)$ para denotar a la única infinitupla $(s_1, s_2, \ldots) \in \omega^{[\mathbf{N}]}$ tal que

$$
x = \langle s_1, s_2, \ldots\rangle = \prod_{i=1}^{\infty} pr(i)^{s_i}
$$

Además para $i \in \mathbf{N}$, usaremos $(x)_i$ para denotar la $i$-ésima coordenada de $(x)$. Es decir que

&#40;1&#41; $(x) = ((x)_1, (x)_2, \ldots)$

&#40;2&#41; $(x)_i$ es el exponente de $pr(i)$ en la (única posible) factorización de $x$ como producto de primos

Se le suele llamar la "bajada $i$-ésima de $x$" al número $(x)_i$. La idea de este nombre es que para obtener $(x)_i$ debemos bajar el exponente de $pr(i)$ en la factorización de $x$. Claramente entonces

&#40;3&#41; $\langle (x)_1, (x)_2, \ldots\rangle = x$, para cada $x \in \mathbf{N}$

&#40;4&#41; Para cada $(s_1, s_2, \ldots) \in \omega^{[\mathbf{N}]}$, se tiene que

$$
(\langle s_1, s_2, \ldots\rangle) = (s_1, s_2, \ldots)
$$

Es decir que $(\langle s_1, s_2, \ldots\rangle)_i = s_i$, para $i \in \mathbf{N}$.

**Ejercicio 3:** Justifique con palabras las propiedades (3) y (4)

Tenemos entonces el siguiente resultado fundamental

**Teorema 2.** Las funciones

$$
\begin{alignedat}{3}
\mathbf{N} &\to \omega^{[\mathbf{N}]} \qquad && \omega^{[\mathbf{N}]} &\to \mathbf{N}\\
x &\mapsto (x) = ((x)_1, (x)_2, \ldots) \qquad && (s_1, s_2, \ldots) &\mapsto \langle s_1, s_2, \ldots\rangle
\end{alignedat}
$$

son biyecciones una inversa de la otra.

**Proof.** Llamemos $f$ a la función de la izquierda y $g$ a la de la derecha. Nótese que el Lema 3 de la Guía 1 nos dice que basta con probar que $f \circ g = Id_{\omega^{[\mathbf{N}]}}$ y $g \circ f = Id_{\mathbf{N}}$. Pero (3) justamente nos dice que $g \circ f = Id_{\mathbf{N}}$ y (4) nos dice que $f \circ g = Id_{\omega^{[\mathbf{N}]}}$. $\blacksquare$

Tal como se hace en la escuela primaria, el siguiente lema nos permite calcular $(x)_i$.

**Ejercicio 4:** Dados $x, i \in \mathbf{N}$, se tiene que

$$
(x)_i = \max_t \left(pr(i)^t \text{ divide a } x\right)
$$

Definamos la función $Lt : \mathbf{N} \to \omega$ de la siguiente manera:

$$
Lt(x) =
\begin{cases}
\max_i (x)_i \ne 0 & \text{si } x \ne 1\\
0 & \text{si } x = 1
\end{cases}
$$

Se tienen las siguientes propiedades básicas

**Ejercicio 5:** Para cada $x \in \mathbf{N}$:

**(a)** $Lt(x) = 0$ sii $x = 1$

**(b)** $x = \prod_{i=1}^{Lt(x)} pr(i)^{(x)_i}$

**Ejercicio 6:** Encuentre el dominio de las siguientes funciones:

**(a)** $\lambda ix[(x)_i]$

**(b)** $\lambda x[Lt(x)]$

**(c)** $\lambda x[\langle (x)_1, (x)_2, (x)_3, 0, 0, \ldots\rangle]$

## Ordenes naturales sobre $\Sigma^\ast$

Daremos biyecciones naturales entre $\Sigma^\ast$ y $\omega$, para cada alfabeto no vacío $\Sigma$. Dichas biyecciones dependen de tener asociado a $\Sigma$ un orden total, el cual nos permite de manera "lexicográfica" listar con el tipo de orden de $\omega$ a todos los elementos de $\Sigma^\ast$. Recomendamos antes repasar el concepto de orden total que está desarrollado en la última sección de la Guía 1.

Primero haremos un caso particular pero que tiene un interés extra ya que está emparentado con nuestra notación decimal clásica de los números de $\omega$.

**Notación decimal sin 0.** Usaremos $Num$ para denotar el conjunto de numerales. Nótese que $Num \cap \omega = \emptyset$. Es decir, no debemos confundir los símbolos que usualmente denotan los primeros diez números enteros con los números que ellos denotan. De hecho en china o japón los primeros diez números enteros se denotan con otros símbolos. Similarmente las palabras pertenecientes a $Num^\ast$ denotan (notación decimal) a los números de $\omega$ pero debemos tener en cuenta que $Num^\ast \cap \omega = \emptyset$. Cuando tratamos con palabras de $Num^\ast$, debemos ser cuidadosos ya que muchas veces en nuestro discurso matemático (es decir las guías, el apunte, lo que escriben los profesores en el pizarrón, etc) representamos dos objetos diferentes de la misma forma. Por ejemplo 45 puede estar denotando al número entero cuarenta y cinco o también 45 puede estar denotando la palabra de longitud 2 cuyo primer símbolo es el numeral 4 y cuyo segundo símbolo es el numeral 5, es decir en este caso la palabra 45 se denota a ella misma. Por dar otro ejemplo, el símbolo 1 en nuestro discurso algunas veces se denotará a sí mismo y otras veces denotará al número uno.

Es bien conocido que, en notación decimal, las siguientes palabras del alfabeto $Num$, denotan, de menor a mayor, a los números de $\omega$

$$
0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, \ldots
$$

Por supuesto esta lista de palabras es infinita pero asumimos que el lector sabe cómo obtener la palabra siguiente a cada miembro de la lista (i.e. sumar 1 en notación decimal), lo cual determina por completo la lista conociendo que la misma comienza con la palabra 0.

Cabe destacar que debido a la presencia del numeral 0 en la lista, la $n$-ésima palabra representa (o denota) al número $n - 1$. Dicho de otra forma, el número $n \in \omega$ es representado por la $(n + 1)$-ésima palabra de la lista.

Un detalle de la representación decimal de números de $\omega$ mediante palabras de $Num^\ast$ es que la misma no nos da una biyección entre $Num^\ast$ y $\omega$ ya que por ejemplo las palabras 00016 y 16 representan el mismo número. Dicho de otra forma en la lista anterior no figuran todas las palabras de $Num^\ast$, a saber están omitidas todas las palabras que comienzan con el símbolo 0 y tienen longitud mayor que uno. A continuación daremos una representación de los números de $\omega$ mediante palabras, la cual no tendrá este problema. El alfabeto que usaremos tendrá todos los numerales menos el 0 y además tendrá un símbolo para denotar al número diez, a saber el símbolo $d$. Es decir

$$
\widetilde{Num} = \{1, 2, 3, 4, 5, 6, 7, 8, 9, d\}
$$

Representaremos a los números de $\omega$ con la siguiente lista infinita de palabras de $\widetilde{Num}$

$$
\begin{gathered}
\varepsilon, 1, 2, 3, 4, 5, 6, 7, 8, 9, d,\\
11, 12, \ldots, 1d, 21, 22, \ldots, 2d, \ldots, 91, 92, \ldots, 9d, d1, d2, \ldots, dd,\\
111, 112, \ldots, 11d, 121, 122, \ldots, 12d, \ldots
\end{gathered}
$$

El lector ya se habrá dado cuenta de que el siguiente a una palabra $\alpha$ de la lista anterior se obtiene aplicando las siguientes cláusulas

- si $\alpha = d^n$, con $n \ge 0$ entonces el siguiente de $\alpha$ es $1^{n+1}$
- si $\alpha$ no es de la forma $d^n$, con $n \ge 0$, entonces el siguiente de $\alpha$ se obtiene de la siguiente manera:

**(a)** buscar de derecha a izquierda el primer símbolo no igual a $d$

**(b)** reemplazar dicho símbolo por su siguiente en la lista $1, 2, 3, 4, 5, 6, 7, 8, 9, d$

**(c)** reemplazar por el símbolo 1 a todos los símbolos iguales a $d$ que ocurrían a la derecha del símbolo reemplazado

Para hacer las cosas más formalmente, definamos $s : \widetilde{Num}^\ast \to \widetilde{Num}^\ast$ de la siguiente manera

- $s(d^n) = d^{n+1}$, para cada $n \ge 0$
- $s(\alpha 1d^n) = \alpha 21^{n+1}$, cada vez que $\alpha \in \widetilde{Num}^\ast$ y $n \ge 0$
- $s(\alpha 2d^n) = \alpha 31^{n+1}$, cada vez que $\alpha \in \widetilde{Num}^\ast$ y $n \ge 0$
- $s(\alpha 3d^n) = \alpha 41^{n+1}$, cada vez que $\alpha \in \widetilde{Num}^\ast$ y $n \ge 0$
- $s(\alpha 4d^n) = \alpha 51^{n+1}$, cada vez que $\alpha \in \widetilde{Num}^\ast$ y $n \ge 0$
- $s(\alpha 5d^n) = \alpha 61^{n+1}$, cada vez que $\alpha \in \widetilde{Num}^\ast$ y $n \ge 0$
- $s(\alpha 6d^n) = \alpha 71^{n+1}$, cada vez que $\alpha \in \widetilde{Num}^\ast$ y $n \ge 0$
- $s(\alpha 7d^n) = \alpha 81^{n+1}$, cada vez que $\alpha \in \widetilde{Num}^\ast$ y $n \ge 0$
- $s(\alpha 8d^n) = \alpha 91^{n+1}$, cada vez que $\alpha \in \widetilde{Num}^\ast$ y $n \ge 0$
- $s(\alpha 9d^n) = \alpha d1^{n+1}$, cada vez que $\alpha \in \widetilde{Num}^\ast$ y $n \ge 0$

Nótese que la definición de $s$ es correcta ya que una palabra de $\widetilde{Num}^\ast$ ya sea es de la forma $d^n$, con $n \ge 0$, o es de la forma $\alpha\delta d^n$, con $\alpha \in \widetilde{Num}^\ast$, $\delta \in \widetilde{Num} - \{d\}$ y $n \ge 0$; y estos casos posibles son mutuamente excluyentes.

Claramente se tiene entonces que la lista anterior puede ser escrita de la siguiente manera

$$
\varepsilon, s(\varepsilon), s(s(\varepsilon)), s(s(s(\varepsilon))), s(s(s(s(\varepsilon)))), \ldots
$$

Y como ya dijimos, pensamos que las palabras de la lista van representando en forma creciente los elementos de $\omega$:

- El número 0 es representado en la lista anterior con la palabra $\varepsilon$
- El número 1 es representado en la lista anterior con la palabra 1
- $\vdots$
- El número 9 es representado en la lista anterior con la palabra 9
- El número 10 es representado en la lista anterior con la palabra $d$
- El número 11 es representado en la lista anterior con la palabra 11
- $\vdots$
- El número 19 es representado en la lista anterior con la palabra 19
- El número 20 es representado en la lista anterior con la palabra $1d$
- El número 21 es representado en la lista anterior con la palabra 21
- El número 22 es representado en la lista anterior con la palabra 22
- $\vdots$

Como puede notarse en estos primeros veinte y pico números solo dos (el 0 y el 20) se representan en forma distinta a la representación decimal clásica. Es natural que $\varepsilon$ denote al número 0 y además nótese que la palabra $1d$ (que en la lista representa el 20) puede leerse como "diecidiez" (es decir la palabra que sigue a "diecinueve") que justamente es 20. Por supuesto con esta manera de pensar la palabra $2d$ deberíamos leerla como "ventidiez" y si nos fijamos en la lista ella representa al número treinta lo cual nuevamente es muy natural. Otro ejemplo: a $6d$ deberíamos leerla como "sesentidiez" y es natural ya que en la lista representa al setenta. También, la palabra $9d$ puede leerse noventidiez ya que representa en la lista al número 100.

La lista anterior va representando los números de $\omega$ en forma muy natural pero, aunque nuestra intuición nos diga que no, en principio podría pasar que una misma palabra del alfabeto $\widetilde{Num}$ ocurra dos veces en la lista y esto nos diría que una misma palabra estaría representando a dos números distintos. También, en principio podría suceder que haya una palabra del alfabeto $\widetilde{Num}$ la cual nunca figure en la lista. En el apunte está la prueba de que estas dos posibilidades no suceden, es decir se muestra que

&#40;S&#41; Toda palabra de $\widetilde{Num}^\ast$ aparece en la lista

&#40;I&#41; Ninguna palabra de $\widetilde{Num}^\ast$ aparece más de una vez

Nótese que la propiedad (S) nos dice que la función

$$
\begin{aligned}
\ast : \omega &\to \widetilde{Num}^\ast\\
n &\mapsto (n+1)\text{-ésimo elemento de la lista}
= \overbrace{s(\ldots s(s(\varepsilon)) \ldots)}^{n\text{ veces}}
\end{aligned}
$$

es suryectiva y la propiedad (I) nos garantiza que dicha función es inyectiva, por lo cual entre las dos nos garantizan que dicha representación establece una biyección entre $\omega$ y $\widetilde{Num}^\ast$.

Por supuesto, la pregunta que inmediatamente surge es cómo calcular la inversa de $\ast$. Llamemos $\#$ a la inversa de $\ast$. Nótese que dada una palabra $\alpha \in \widetilde{Num}^\ast$, el número $\#(\alpha)$ es justamente el número representado por la palabra $\alpha$, o dicho de otra forma $\#(\alpha)$ es la posición que ocupa $\alpha$ en la lista, contando desde el 0 (es decir $\alpha$ es la $(\#(\alpha) + 1)$-ésima palabra de la lista). Por ejemplo:

$$
\begin{gathered}
\#(\varepsilon) = 0\\
\#(1) = 1\\
\vdots\\
\#(9) = 9\\
\#(d) = 10\\
\#(11) = 11\\
\#(12) = 12\\
\vdots\\
\#(19) = 19\\
\#(1d) = 20
\end{gathered}
$$

Aquí hay que tener cuidado como leemos las igualdades anteriores. Por ejemplo en la igualdad

$$
\#(1) = 1
$$

la primera ocurrencia del símbolo 1 se refiere al numeral uno, es decir denota una palabra y la segunda ocurrencia se está refiriendo al número uno, es decir denota un número.

Dejamos al lector el ejercicio de ganar intuición con ejemplos hasta que se convenza de que tal como en el caso de la notación decimal, el número $\#(\alpha)$ se expresa como una suma de potencias de 10, con los coeficientes dados en función de los símbolos de $\alpha$. Más concretamente si $\alpha = s_1s_2\ldots s_k$ con $k \ge 1$ y $s_1, s_2, \ldots, s_k \in \widetilde{Num}$, entonces

$$
\#(\alpha) = \#(s_1).10^{k-1} + \#(s_2).10^{k-2} + \ldots + \#(s_k).10^0
$$

No daremos aquí una prueba de este hecho, el cual está probado en detalle en el apunte. Algunos ejemplos

$$
\begin{aligned}
\#(1d) &= 1.10^1 + 10.10^0 = 10 + 10 = 20\\
\#(dd) &= 10.10^1 + 10.10^0 = 100 + 10 = 110\\
\#(111) &= 1.10^2 + 1.10^1 + 1.10^0 = 100 + 10 + 1 = 111\\
\#(1d3d) &= 1.10^3 + 10.10^2 + 3.10^1 + 10.10^0
\end{aligned}
$$

Ahora que sabemos que las palabras de $\widetilde{Num}$ representan los números como suma de potencias de diez, en forma análoga a la notación decimal clásica, podemos reforzar aún más la analogía poniendo nombres adecuados que, tal como en el caso clásico, nos permitan leer las palabras de $\widetilde{Num}$ describiendo su suma de potencias asociada. Por ejemplo podríamos llamar "decenta" al número 100, por analogía a "treinta", "cuarenta",..., "noventa". O sea una decenta es diez veces diez. De esta forma la palabra $d1$ se leerá "decenta y uno" y esto es natural ya que en la lista representa al 101. La palabra $dd$ se leerá "decenta y diez" y esto describe a la perfección el número que representa, i.e. el $10.10 + 10 = 110$. La palabra que sigue en la lista a $dd$ es 111 la cual representa al 111, es decir aquí como en los otros casos vistos en los cuales no hay ocurrencias del símbolo $d$ la palabra representa al mismo número que representa en la notación decimal clásica. Por dar otro ejemplo, la palabra $59d3$ se leerá "cinco mil novecientos decenta y tres" y representará al número 6003.

Para seguir debemos ponerle nombre a "diez veces cien", es decir, "decientos" (por analogía con "novecientos = nueve veces cien") denotará al número $1000 = 10.100$. De esta forma la palabra $d51$ se leerá "decientos cincuenta y uno" y esto es natural ya que pensando un rato se puede ver que ella representa al 1051. También, la palabra $ddd$ se leerá "decientos decenta y diez" y representará al número 1110. En la página granlogico.com hay un programa hecho por Guido Ivetta el cual hace lo siguiente:

- Dado un número $n$ expresado en notación clásica decimal da explícitamente la palabra $\ast(n)$ y la forma de pronunciarla o leerla a dicha palabra

**El caso general.** Sea $\Sigma$ un alfabeto no vacío y supongamos $\le$ es un orden total sobre $\Sigma$. Supongamos que $\Sigma = \{a_1, \ldots, a_n\}$, con $a_1 < a_2 < \ldots < a_n$. Inspirados en la lista dada anteriormente de las palabras de $\widetilde{Num}^\ast$, podemos dar la siguiente lista de palabras de $\Sigma^\ast$:

$$
\begin{gathered}
\varepsilon, a_1, a_2, \ldots, a_n,\\
a_1a_1, a_1a_2, \ldots, a_1a_n, a_2a_1, a_2a_2, \ldots, a_2a_n, \ldots, a_na_1, a_na_2, \ldots, a_na_n,\\
a_1a_1a_1, a_1a_1a_2, \ldots, a_1a_1a_n, a_1a_2a_1, a_1a_2a_2, \ldots, a_1a_2a_n, \ldots, a_1a_na_1, a_1a_na_2, a_1a_na_n,\\
a_2a_1a_1, a_2a_1a_2, \ldots, a_2a_1a_n, a_2a_2a_1, a_2a_2a_2, \ldots, a_2a_2a_n, \ldots, a_2a_na_1, a_2a_na_2, a_2a_na_n,\\
\vdots\\
a_na_1a_1, a_na_1a_2, \ldots, a_na_1a_n, a_na_2a_1, a_na_2a_2, \ldots, a_na_2a_n, \ldots, a_na_na_1, a_na_na_2, a_na_na_n,\\
a_1a_1a_1a_1, a_1a_1a_1a_2, \ldots
\end{gathered}
$$

Definamos más formalmente la lista. Para esto definamos $s^{\le} : \Sigma^\ast \to \Sigma^\ast$ de la siguiente manera

- $s^{\le}((a_n)^m) = (a_1)^{m+1}$, para cada $m \ge 0$
- $s^{\le}(\alpha a_i(a_n)^m) = \alpha a_{i+1}(a_1)^m$, cada vez que $\alpha \in \Sigma^\ast$, $1 \le i < n$ y $m \ge 0$

Nótese que la definición de $s^{\le}$ es correcta ya que toda palabra de $\Sigma^\ast$ es de la forma $(a_n)^m$, con $m \ge 0$, o es de la forma $\alpha a_i(a_n)^m$, con $\alpha \in \Sigma^\ast$, $1 \le i < n$ y $m \ge 0$; y estos dos casos posibles son mutuamente excluyentes (convencerse fuertemente de que esto es así).

**Ejercicio 7:** Sea $\Sigma = \{\text{\%}, \text{!}, \text{@}\}$ y sea $\le$ el orden total sobre $\Sigma$ dado por $\text{\%} < \text{!} < \text{@}$ (es decir que aquí $a_1 = \text{\%}$, $a_2 = \text{!}$ y $a_3 = \text{@}$). Escriba los primeros elementos de la lista y describa para este caso particular la función $s^{\le}$, sin hablar de los $a_i$, i.e. solo haciendo referencia a los símbolos $\text{\%}, \text{!}, \text{@}$.

**Ejercicio 8:** Pruebe para el caso general que

**(a)** $\varepsilon \ne s^{\le}(\alpha)$, para cada $\alpha \in \Sigma^\ast$

**(b)** Si $\alpha \ne \varepsilon$, entonces $\alpha = s^{\le}(\beta)$ para algún $\beta$

**Ejercicio 9:**

**(a)** Convénzase de que valen las siguientes ecuaciones

$$
\begin{aligned}
s^{\le}(\varepsilon) &= a_1\\
s^{\le}(\alpha a_i) &= \alpha a_{i+1}, \quad i < n\\
s^{\le}(\alpha a_n) &= s^{\le}(\alpha)a_1
\end{aligned}
$$

**(b)** Note que sucesivas aplicaciones de las ecuaciones anteriores determinan por completo el valor de $s^{\le}$ en una palabra $\alpha$ previamente fijada. Explique esto con palabras.

Por supuesto, la lista anterior puede ser escrita de la siguiente manera

$$
\varepsilon, s^{\le}(\varepsilon), s^{\le}(s^{\le}(\varepsilon)), s^{\le}(s^{\le}(s^{\le}(\varepsilon))), s^{\le}(s^{\le}(s^{\le}(s^{\le}(\varepsilon)))), \ldots
$$

Con esta definición formal de la lista se puede probar (ver el apunte) que:

&#40;S&#41; Toda palabra de $\Sigma^\ast$ aparece en la lista

&#40;I&#41; Ninguna palabra de $\Sigma^\ast$ aparece más de una vez en la lista

Definamos $\ast^{\le} : \omega \to \Sigma^\ast$ recursivamente de la siguiente manera:

- $\ast^{\le}(0) = \varepsilon$
- $\ast^{\le}(i + 1) = s^{\le}(\ast^{\le}(i))$

Es claro que entonces $\ast^{\le}(i)$ nos da el $(i + 1)$-ésimo elemento de la lista, o lo que es lo mismo, el $i$-ésimo elemento de la lista contando desde el 0. O sea que las propiedades (S) y (I) nos garantizan que la función $\ast^{\le}$ es biyectiva. A continuación describiremos su inversa. Primero un lema obvio pero muy importante.

**Lema 3.** Sea $\Sigma$ un alfabeto no vacío y supongamos $\le$ es un orden total sobre $\Sigma$. Supongamos que $\Sigma = \{a_1, \ldots, a_n\}$, con $a_1 < a_2 < \ldots < a_n$. Entonces para cada $\alpha \in \Sigma^\ast - \{\varepsilon\}$ hay únicos $k \in \omega$ y $i_0, i_1, \ldots, i_k \in \{1, \ldots, n\}$ tales que

$$
\alpha = a_{i_k}\ldots a_{i_0}
$$

Notar que el $k$ del lema anterior es $|\alpha| - 1$ y los números $i_k, \ldots, i_0$ van dando el número de orden de cada símbolo de $\alpha$ yendo de izquierda a derecha. Por ejemplo si $\Sigma = \{\text{\%}, \text{!}, \text{@}\}$ y $\le$ es el orden total sobre $\Sigma$ dado por $\text{\%} < \text{!} < \text{@}$ (es decir que aquí $a_1 = \text{\%}$, $a_2 = \text{!}$ y $a_3 = \text{@}$) entonces para la palabra $\text{!\%@\%@}$ tenemos $k = 4$ y $i_4 = 2$, $i_3 = 1$, $i_2 = 3$, $i_1 = 1$ y $i_0 = 3$. Sin embargo si hubiéramos tomado el orden dado por $\text{@} < \text{\%} < \text{!}$, para la misma palabra hubiéramos tenido $i_4 = 3$, $i_3 = 2$, $i_2 = 1$, $i_1 = 2$ y $i_0 = 1$.

Ahora podemos definir la función $\#^{\le}$ de la siguiente manera

$$
\begin{aligned}
\#^{\le} : \Sigma^\ast &\to \omega\\
\varepsilon &\mapsto 0\\
a_{i_k}\ldots a_{i_0} &\mapsto i_kn^k + \ldots + i_0n^0
\end{aligned}
$$

**Ejercicio 10:** Si $\le$ es el orden de $\{\text{@}, \&\}$ dado por $\text{@} < \&$, entonces $\#^{\le}(\text{@\&@\&@}) = 2^4 + 2^4 + 2^2 + 2^2 + 1$ y $\#^{\le}(\text{@\&@\&@}) = 2^5 + 2^3 + 1$

**Ejercicio 11:** Si $\le$ es el orden de $\{\text{@}, \&\}$ dado por $\text{@} < \&$, entonces $\#^{\le}(\alpha\text{@}) = \#^{\le}(\alpha).2 + 1$, para todo $\alpha \in \{\text{@}, \&\}^\ast$

**Ejercicio 12:** Sea $\Sigma$ un alfabeto finito no vacío y sea $\le$ un orden total sobre $\Sigma$. Inspírese en el ejercicio anterior para dar una "definición recursiva" de la función $\#^{\le}$.

Aceptaremos sin prueba el siguiente resultado fundamental una prueba del cual puede verse en el apunte.

**Lema 4.** La función $\#^{\le}$ es la inversa de $\ast^{\le}$

Cabe destacar que dada una palabra $\alpha$, el número $\#^{\le}(\alpha)$ nos dice en qué posición se ubica $\alpha$ en la lista, es decir $\alpha$ es la $(\#^{\le}(\alpha) + 1)$-ésima palabra de la lista. O sea que:

$$
\alpha = \overbrace{s^{\le}(\ldots s^{\le}(s^{\le}(\varepsilon)) \ldots)}^{\#^{\le}(\alpha)\text{ veces}}
$$

**Ejercicio 13:** Si $\le$ es un orden total sobre un alfabeto no vacío $\Sigma$, entonces $s^{\le} = \ast^{\le} \circ Suc \circ \#^{\le}$

Como hemos visto las biyecciones dadas producen una "identificación" entre números de $\omega$ y palabras del alfabeto $\Sigma$. Es decir, en algún sentido identificamos palabras y números ya que se corresponden biunívocamente. Supongamos que $\alpha$ es una palabra de $\Sigma^\ast - \{\varepsilon\}$ y queremos "verla como un número". Entonces en vez de ver sus símbolos vemos los órdenes de aparición en $\Sigma$ de los mismos y miramos la suma de potencias asociada.

Supongamos ahora que $x$ es un número de $\omega - \{0\}$ y además supongamos que somos súper inteligentes y que cuando vemos a $x$ vemos la secuencia única de números $i_k, i_{k-1}, \ldots, i_0$ que nos permite expresarlo como suma de potencias según el lema anterior. Entonces si queremos ver a $x$ como una palabra simplemente miramos la secuencia $i_k, i_{k-1}, \ldots, i_0$ como palabra, reemplazando cada $i_j$ por el símbolo $i_j$-ésimo de $\Sigma$.

**Ejercicio 14:** Mastique mastique e imagine hasta que entienda con claridad el último párrafo. Luego será más mariposa.

**Extensión del orden total de $\Sigma$ a $\Sigma^\ast$.** Dado un orden total $\le$ sobre $\Sigma$, podemos extender $\le$ a $\Sigma^\ast$ de la siguiente manera

- $\alpha \le \beta$ sii $\#^{\le}(\alpha) \le \#^{\le}(\beta)$

Es decir $\alpha \le \beta$ sii $\alpha = \beta$ o $\alpha$ ocurre antes que $\beta$ en la lista. Llamaremos a este orden el orden total de $\Sigma^\ast$ inducido por $\le$. Obviamente este orden es un orden total sobre $\Sigma^\ast$. Tal como en el caso de la notación decimal clásica (con 0) el orden total de $\Sigma^\ast$ inducido por $\le$ puede ser caracterizado "lexicográficamente" en forma similar al orden de los diccionarios. Ya que se vuelve más fácil de escribir daremos a continuación la caracterización lexicográfica del orden $<$ asociado al orden total de $\Sigma^\ast$ inducido por $\le$. Lo aceptaremos sin demostración, la cual puede verse en el apunte.

**Lema 5 (Orden lexicográfico de $\Sigma^\ast$).** Sea $\le$ un orden total sobre $\Sigma$. Dados $\alpha, \beta \in \Sigma^\ast$ tenemos que:

&#40;1&#41; Si $|\alpha| \ne |\beta|$, entonces $\alpha < \beta$ si y solo si $|\alpha| < |\beta|$

&#40;2&#41; Si $|\alpha| = |\beta|$, entonces $\alpha < \beta$ si y solo si existen $\rho, \gamma_1, \gamma_2 \in \Sigma^\ast$ y $i, j \in \omega$ tales que

$$
\alpha = \rho a_i\gamma_1 \text{ y } \beta = \rho a_j\gamma_2 \text{ y } i < j
$$

Cabe destacar que si bien la condición del ítem (2) del lema anterior es de tipo descriptiva, tiene un carácter algorítmico bien marcado ya que cuando tenemos dos palabras no iguales a $\varepsilon$, de la misma longitud, podemos ver el primer par de dígitos en los que difieren y la relación de orden que tienen dichos símbolos es la que tienen dichas palabras.

Debería ser intuitivamente claro que el orden recién definido sobre $\Sigma^\ast$ posee las mismas propiedades matemáticas que el orden usual de $\omega$. Por ejemplo:

**Lema 6.** Si $S \subseteq \Sigma^\ast$ es no vacío, entonces existe $\alpha \in S$ tal que $\alpha \le \beta$, para cada $\beta \in S$.

**Ejercicio 15:** Pruebe el lema anterior (Hint: notar que el conjunto $\{\mu \in S : |\mu| \le |\alpha| \text{ para cada } \alpha \in S\}$ es finito y no vacío)
