# Lema 21, guia 5: caso \(k=2,\ n=2,\ m=1\)

**Enunciado.** Sea \(O\in\{\omega,\Sigma^\ast\}\). Supongamos \(f_i:D_{f_i}\subseteq\omega^2\times\Sigma^\ast\to O\), \(i=1,2\), son funciones \(\Sigma\)-p.r. tales que \(D_{f_i}\cap D_{f_j}=\emptyset\) para \(i\ne j\). Entonces \(f_1\cup f_2\) es \(\Sigma\)-p.r.

**Demostracion.** Por el Lema 19 existen extensiones totales \(\Sigma\)-p.r.
\[
\overline f_i:\omega^2\times\Sigma^\ast\to O
\]
tales que \(\overline f_i|_{D_{f_i}}=f_i\). Por la Proposicion 20, \(D_{f_1}\) y \(D_{f_2}\) son \(\Sigma\)-p.r.; luego \(U=D_{f_1}\cup D_{f_2}\) tambien lo es.

Si \(O=\omega\), definimos la funcion total \(\Sigma\)-p.r.
\[
H(x,y,\alpha)=\chi_{D_{f_1}}(x,y,\alpha)\cdot \overline f_1(x,y,\alpha)+\chi_{D_{f_2}}(x,y,\alpha)\cdot \overline f_2(x,y,\alpha).
\]
Para \(e\in U\), como \(D_{f_1}\cap D_{f_2}=\emptyset\), se tiene
\[
H(e)=
\begin{cases}
f_1(e)&\text{si }e\in D_{f_1},\\
f_2(e)&\text{si }e\in D_{f_2}.
\end{cases}
\]
Luego \(f_1\cup f_2=H|_U\), que es \(\Sigma\)-p.r. por el Lema 18.

Si \(O=\Sigma^\ast\), definimos la funcion total \(\Sigma\)-p.r.
\[
H(x,y,\alpha)=\overline f_1(x,y,\alpha)^{\chi_{D_{f_1}}(x,y,\alpha)}\overline f_2(x,y,\alpha)^{\chi_{D_{f_2}}(x,y,\alpha)}.
\]
Para \(e\in U\), usando \(\beta^0=\varepsilon\) y \(\beta^1=\beta\), otra vez
\[
H(e)=
\begin{cases}
f_1(e)&\text{si }e\in D_{f_1},\\
f_2(e)&\text{si }e\in D_{f_2}.
\end{cases}
\]
Por lo tanto \(f_1\cup f_2=H|_U\), y el Lema 18 implica que \(f_1\cup f_2\) es \(\Sigma\)-p.r.
