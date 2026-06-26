# Lema: division por casos para funciones \(\Sigma\)-p.r.

**Enunciado.** Supongamos \(f_i:D_{f_i}\subseteq\omega^n\times\Sigma^{\ast m}\to\Sigma^\ast\), \(i=1,\ldots,k\), son funciones \(\Sigma\)-p.r. tales que \(D_{f_i}\cap D_{f_j}=\emptyset\) para \(i\ne j\). Entonces \(f_1\cup\cdots\cup f_k\) es \(\Sigma\)-p.r.

**Demostracion (caso \(k=2,\ n=2,\ m=1\)).** Por el Lema 19 de la Guia 5 (extension total de funciones \(\Sigma\)-p.r.) existen extensiones totales \(\Sigma\)-p.r.
\[
\overline f_i:\omega^2\times\Sigma^\ast\to\Sigma^\ast
\]
tales que \(\overline f_i|_{D_{f_i}}=f_i\). Por la Proposicion 20 de la Guia 5 (caracterizacion de conjuntos \(\Sigma\)-p.r. como dominios), \(D_{f_1}\) y \(D_{f_2}\) son \(\Sigma\)-p.r.; luego \(U=D_{f_1}\cup D_{f_2}\) tambien lo es.

Definimos
\[
H=
\lambda\alpha\beta[\alpha\beta]\circ
\left[
\lambda x\alpha[\alpha^x]\circ
\left[\chi_{D_{f_1}}^{\omega^2\times\Sigma^\ast},\overline f_1\right],
\lambda x\alpha[\alpha^x]\circ
\left[\chi_{D_{f_2}}^{\omega^2\times\Sigma^\ast},\overline f_2\right]
\right]
=\lambda xy\alpha\left[
\overline f_1(x,y,\alpha)^{\chi_{D_{f_1}}^{\omega^2\times\Sigma^\ast}(x,y,\alpha)}
\overline f_2(x,y,\alpha)^{\chi_{D_{f_2}}^{\omega^2\times\Sigma^\ast}(x,y,\alpha)}
\right].
\]
Esta funcion es total y \(\Sigma\)-p.r. por clausura por composicion.
Para \(e\in U\), usando \(\beta^0=\varepsilon\) y \(\beta^1=\beta\),
\[
H(e)=
\begin{cases}
f_1(e)&\text{si }e\in D_{f_1},\\
f_2(e)&\text{si }e\in D_{f_2}.
\end{cases}
\]
Por lo tanto \(f_1\cup f_2=H|_U\), y el Lema 18 de la Guia 5 (restriccion de una funcion \(\Sigma\)-p.r. a un dominio \(\Sigma\)-p.r.) implica que \(f_1\cup f_2\) es \(\Sigma\)-p.r.
