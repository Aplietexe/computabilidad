# Notacion lambda

Fijado un alfabeto finito \(\Sigma\), \(\lambda\) solo se aplica a expresiones
lambdificables respecto de \(\Sigma\).

## Variables

Las variables numericas se valuan en \(\omega\) y se toman de
\[
x,y,z,w,n,m,k,\ldots;\quad x_1,x_2,\ldots;\quad y_1,y_2,\ldots
\]
Las variables alfabeticas se valuan en \(\Sigma^\ast\) y se toman de
\[
\alpha,\beta,\gamma,\eta,\ldots;\quad
\alpha_1,\alpha_2,\ldots;\quad \beta_1,\beta_2,\ldots
\]
Tambien se admiten expresiones sin variables.

## Lambdificabilidad

Una expresion \(E\) es lambdificable respecto de \(\Sigma\) si, para toda
valuacion admisible, todos sus valores definidos pertenecen siempre a
\(\omega\), o todos pertenecen siempre a \(\Sigma^\ast\). Puede estar
indefinida en algunas o todas las valuaciones; si nunca esta definida, es
lambdificable. No es lambdificable si alguna valuacion definida produce un
objeto fuera de \(\omega\cup\Sigma^\ast\), o si mezcla salidas numericas y
alfabeticas.

Las Booleanas valen en \(\{0,1\}\subseteq\omega\): verdadero \(=1\), falso
\(=0\). La expresion puede usar lenguaje matematico o coloquial, siempre que
bajo cada valuacion quede determinado si tiene valor y cual es. El concepto de
expresion lambdificable se usa intuitivamente, no como objeto formal.

## Definicion precisa

"Estar definida" exige precision completa. Una imprecision en cualquier parte
de \(E\) vuelve indefinida a toda la expresion para esa valuacion. No se oculta
por multiplicar por \(0\), por conectivos Booleanos, por cuantificaciones
vacias ni por simplificaciones externas. Ambiguedad sintactica, operacion fuera
de dominio o subexpresion imprecisa alcanzan para que \(E\) no tenga valor. Una
expresion sin variables que denota una funcion u otro objeto fuera de
\(\omega\cup\Sigma^\ast\) no es lambdificable; una que nunca denota valor si lo
es, y toda lambda construida con ella es \(\emptyset\).

## Definicion

Sean \(n,m\in\omega\), \(E\) lambdificable respecto de \(\Sigma\), y
\[
x_1,\ldots,x_n,\alpha_1,\ldots,\alpha_m
\]
una lista de variables distintas que contiene todas las que ocurren en \(E\)
--puede contener variables extra--. Entonces
\[
\lambda x_1...x_n\alpha_1...\alpha_m[E]
\]
denota la funcion \(f\) con dominio
\[
D_f=\{(k_1,\ldots,k_n,\beta_1,\ldots,\beta_m)\in
\omega^n\times\Sigma^{\ast m}: E\text{ esta definida al asignar }
x_i=k_i,\ \alpha_i=\beta_i\},
\]
y valor
\[
f(k_1,\ldots,k_n,\beta_1,\ldots,\beta_m)=
\text{el valor de }E\text{ bajo esa asignacion.}
\]

Por lambdificabilidad, \(f\) es \(\Sigma\)-mixta de tipo \((n,m,s)\), con
\(s\in\{\#,\ast\}\): \(s=\#\) para salida en \(\omega\) y \(s=\ast\) para
salida en \(\Sigma^\ast\).

## Casos de borde

- Si \(n=m=0\), se escribe \(\lambda[E]\); \(E\) no tiene variables.
- Si \(E\) produce valor, \(D_{\lambda[E]}=\{\diamond\}\); si no,
  \(\lambda[E]=\emptyset\).
- La notacion depende de \(\Sigma\) cuando hay variables alfabeticas; sin ellas,
  no.
- El orden posterior a \(\lambda\) fija el orden de las coordenadas; cambiarlo
  puede cambiar la funcion.
