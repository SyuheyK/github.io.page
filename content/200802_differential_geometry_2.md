---
title: "微分幾何のまとめ 2"
tags: ["微分幾何"]
date: 2020-08-13T10:00:00+09:00
draft: false
---
[細野忍「微分幾何」](http://www.asakura.co.jp/books/isbn/978-4-254-11849-0/)を元に，
リーマン幾何学に関する内容をダイジェストでまとめます．

### 内容
- [**共変微分**と**接続**，捩率テンソル](#001)
- [**リーマン接続**](#002)
<!--
- [平行移動と測地線](#003)
- [双対接続](#004)
- [リーマン計量による曲線の長さの表現](#003)
-->

<a id="markdown-001" name="001"></a>

### 共変微分と接続，捩率テンソル
各点で関数の方向微分は独立に考えられるので，それに基づいて定義された接空間も同様に独立である．
そこで２点間の接空間の基底の差分を
{{< equation >}}
  \left(\dfrac{\partial}{\partial u^j}\right)_{p+\Delta p} - \left(\dfrac{\partial}{\partial u^j}\right)_p
  &= \sum_{i,k=1}^2\Delta u^i\Gamma_{i\ j}^{\ k}\left(\dfrac{\partial}{\partial u^k}\right)_p
{{< /equation >}}
と決めることにする．
多様体内の各点によって基底が変化する様子を $C^\infty$ 上の関数 $\Gamma_{i\ j}^{\ k}$ で表現していると捉えることができる．

この式の右辺各項について，$\Delta u^i\rightarrow0$ としたときの極限を $\nabla_{\partial/\partial u^i}$ と書き，
{{< equation >}}
  \nabla_{\partial/\partial u^i}\left(\dfrac{\partial}{\partial u^j}\right)_p
    &= \sum_{i,k=1}^2\Gamma_{i\ j}^{\ k}\left(\dfrac{\partial}{\partial u^k}\right)_p
{{< /equation >}}
と定め，$T_{p+\Delta p}M$ と $T_pM$ の基底の関係を表す式と読む．

また，一般のベクトル場 $\xi_p=\sum_{j=1}^2\xi^j(\partial/\partial u^j)_p$ の2点 $p$ と $p+\Delta p$ の関係を
成分 $\xi^j$ が変化する部分と基底 $(\partial/\partial u^j)_p$ が変化する部分に分けて
{{< equation >}}
  \sum_{j=1}^2\xi^j(p+\Delta p)\left(\dfrac{\partial}{\partial u^j}\right)_{p+\Delta p}
  - \sum_{j=1}^2\xi^j(p)\left(\dfrac{\partial}{\partial u^j}\right)_{p}
  &= \sum_{i,j=1}^2\Delta u^i\left(\dfrac{\partial\xi^j}{\partial u^i}+\sum_{k=1}^2\Gamma_{i\ k}^{\; j}\xi^k\right)
  \left(\dfrac{\partial}{\partial u^j}\right)_p+O((\Delta u)^2)
{{< /equation >}}
と表すことができる．
この式の右辺第一項に現れる係数を
{{< equation >}}
  \nabla_{\partial/\partial u^i}\xi^j=\dfrac{\partial\xi^j}{\partial u^i}+\sum_{k=1}^2\Gamma_{i\ k}^{\; j}\xi^k
{{< /equation >}}
と書いて，ベクトル場 $\xi_p$ の成分 $\xi^j$ の共変微分係数あるいは単に共変微分と呼ぶ．
$\partial\xi^j/\partial u^i$ が成分が変化する部分に，$\sum_{k=1}^2\Gamma_{i\ k}^{\; j}\xi^k$ が基底が変化する部分に対応している．
この記号を用いるとベクトル場 $\xi_p$ に対する共変微分は
{{< equation >}}
  \nabla_{\partial/\partial u^i}\xi
  &=\sum_j\left(\nabla_{\partial/\partial u^i}\xi^j\right)\left(\dfrac{\partial}{\partial u^j}\right)
  =\left(\dfrac{\partial}{\partial u^i}\right)\xi+\sum_{j,k}\Gamma_{i\ k}^{\; j}\xi^k\left(\dfrac{\partial}{\partial u^j}\right)
{{< /equation >}}
と計算できる．

#### 共変微分の計算規則
共変微分の計算規則を示す前に，計算対象として考えるベクトル場について定めておく．
$M$ 上の$C^\infty$ 関数 $f$ とベクトル場 
{{<equation>}}
\xi=\sum_i\xi^i\left(\dfrac{\partial}{\partial u^i}\right)
{{</equation>}}
について，新たなベクトル場 $f\xi$ を
{{<equation>}}
f\xi=\sum_if\xi^i\left(\dfrac{\partial}{\partial u^i}\right)
{{</equation>}}
と定める．この定義は $f$ にベクトル場 $\xi$ を作用させてできる $M$ 上の関数　
{{<equation>}}
\xi f=\sum_i\xi^i\left(\dfrac{\partial f}{\partial u^i}\right)
{{</equation>}}
とは異なることに注意する．

上記のベクトル場の準備のもと，
$M$ 上の$C^\infty$ 関数 $f$ とベクトル場 $\xi,\eta$ について，
以下のとおり共変微分の計算規則がなりたつ．
1. $\nabla_{\partial/\partial u^i}(\xi+\eta)=\nabla_{\partial/\partial u^i}\xi+\nabla_{\partial/\partial u^i}\eta$
1. $\nabla_{\partial/\partial u^i+\partial/\partial u^j}\xi=\nabla_{\partial/\partial u^i}\xi+\nabla_{\partial/\partial u^j}\xi$
1. $\nabla_{f\partial/\partial u^i}\xi=f\nabla_{\partial/\partial u^i}\xi$
1. $\nabla_{\partial/\partial u^i}(f\xi)=\left(\frac{\partial}{\partial u^i}f\right)\xi+f\nabla_{\partial/\partial u^i}\xi$ (問2.12)

#### 接続係数
上記の計算規則を用いれば，共変微分の定義から，次のように2とおりに計算することができる．
ただし，局所座標近傍を交換する都合から，局所座標近傍 $\alpha,\beta$ のいずれの下で計算しているかを明記することとする．
まず，共変微分の適用後に局所座標近傍を変換することで，次の様に計算することができる．
{{<equation>}}
\nabla_{\partial/\partial u_\alpha^i}\left(\dfrac{\partial}{\partial u_\alpha^j}\right)
&= \sum_{k=1}^2\Gamma_{i\ j}^{\; k}(\alpha)\left(\dfrac{\partial}{\partial u_\alpha^k}\right)\\
&= \sum_{k,l=1}^2\Gamma_{i\ j}^{\; k}(\alpha)\left(\dfrac{\partial u_\beta^l}{\partial u_\alpha^k}\right)\left(\dfrac{\partial}{\partial u_\beta^l}\right)\tag*{(#1)}\label{gamma1}
{{</equation>}}
もう一方は，共変微分の適用前に局所座標近傍を変換することで，次のように計算できる．
{{<equation>}}
\nabla_{\partial/\partial u_\alpha^i}\left(\dfrac{\partial}{\partial u_\alpha^j}\right)
&=\nabla_{\partial/\partial u_\alpha^i}\sum_{l=1}^2\left(\frac{\partial u_\beta^l}{\partial u_\alpha^j}\right)\left(\dfrac{\partial}{\partial u_\beta^l}\right)\\
&=\sum_{l=1}^2\nabla_{\partial/\partial u_\alpha^i}\left(\frac{\partial u_\beta^l}{\partial u_\alpha^j}\right)\left(\dfrac{\partial}{\partial u_\beta^l}\right)\\
&=\sum_{l=1}^2\left\{\frac{\partial^2 u_\beta^l}{\partial u_\alpha^i\partial u_\alpha^j}\left(\dfrac{\partial}{\partial u_\beta^l}\right)+\left(\frac{\partial u_\beta^l}{\partial u_\alpha^j}\right)\nabla_{\partial/\partial u_\alpha^i}\left(\dfrac{\partial}{\partial u_\beta^l}\right)\right\}.
{{</equation>}}
最右辺2項目の計算を進めると，
{{<equation>}}
\sum_{l=1}^2\left(\frac{\partial u_\beta^l}{\partial u_\alpha^j}\right)\nabla_{\partial/\partial u_\alpha^i}\left(\dfrac{\partial}{\partial u_\beta^l}\right)
&= \sum_{l=1}^2\left(\frac{\partial u_\beta^l}{\partial u_\alpha^j}\right)
\nabla_{\sum_{m=1}^2\left(\frac{\partial u_\beta^m}{\partial u_\alpha^i}\right)\left(\frac{\partial}{\partial u_\beta^m}\right)}\left(\dfrac{\partial}{\partial u_\beta^l}\right)\\
&= \sum_{l,m=1}^2\left(\frac{\partial u_\beta^l}{\partial u_\alpha^j}\right)\left(\frac{\partial u_\beta^m}{\partial u_\alpha^i}\right)
\nabla_{\partial/\partial u_\beta^m}\left(\dfrac{\partial}{\partial u_\beta^l}\right)\\
&= \sum_{l,m=1}^2\left(\frac{\partial u_\beta^l}{\partial u_\alpha^j}\right)\left(\frac{\partial u_\beta^m}{\partial u_\alpha^i}\right)\sum_{n=1}^2\Gamma_{m\ l}^{\; n}(\beta)\left(\dfrac{\partial}{\partial u_\beta^n}\right)\\
&= \sum_{l,m,n=1}^2\left(\frac{\partial u_\beta^l}{\partial u_\alpha^j}\right)\left(\frac{\partial u_\beta^m}{\partial u_\alpha^i}\right)\Gamma_{m\ l}^{\; n}(\beta)\left(\dfrac{\partial}{\partial u_\beta^n}\right)\\
&= \sum_{l,m,n=1}^2\left(\frac{\partial u_\beta^n}{\partial u_\alpha^j}\right)\left(\frac{\partial u_\beta^m}{\partial u_\alpha^i}\right)\Gamma_{m\ n}^{\; l}(\beta)\left(\dfrac{\partial}{\partial u_\beta^l}\right)
{{</equation>}}
となる．元の式に戻すと，
{{<equation>}}
\nabla_{\partial/\partial u_\alpha^i}\left(\dfrac{\partial}{\partial u_\alpha^j}\right)
&=\sum_{l=1}^2\left\{\frac{\partial^2 u_\beta^l}{\partial u_\alpha^i\partial u_\alpha^j}\left(\dfrac{\partial}{\partial u_\beta^l}\right)+\sum_{m,n=1}^2\left(\frac{\partial u_\beta^n}{\partial u_\alpha^j}\right)\left(\frac{\partial u_\beta^m}{\partial u_\alpha^i}\right)\Gamma_{m\ n}^{\; l}(\beta)\left(\dfrac{\partial}{\partial u_\beta^l}\right)
\right\}\tag*{(#2)}\label{gamma2}
{{</equation>}}
となる．$\ref{gamma1}$ と $\ref{gamma2}$ の2とおりの式展開に対して $\partial/\partial u_\beta^l$ の係数を比較すると，次の式が成り立つことがわかる．
{{<equation>}}
\sum_{k=1}^2\Gamma_{i\ j}^{\; k}(\alpha)\left(\dfrac{\partial u_\beta^l}{\partial u_\alpha^k}\right)
&=\frac{\partial^2 u_\beta^l}{\partial u_\alpha^i\partial u_\alpha^j}+\sum_{m,n=1}^2\left(\frac{\partial u_\beta^n}{\partial u_\alpha^j}\right)\left(\frac{\partial u_\beta^m}{\partial u_\alpha^i}\right)\Gamma_{m\ n}^{\; l}(\beta)
{{</equation>}}
両辺に $\partial u_\beta^l/\partial u_\alpha^k$ の逆行列 $\partial u_\alpha^k / \partial u_\beta^l$ を掛けると
{{<equation>}}
\Gamma_{i\ j}^{\; k}(\alpha)\left(\dfrac{\partial u_\beta^l}{\partial u_\alpha^k}\right)
&=\sum_{l=1}^2\frac{\partial^2 u_\beta^l}{\partial u_\alpha^i\partial u_\alpha^j}\left(\frac{\partial u_\alpha^k}{\partial u_\beta^l}\right)
+\sum_{l,m,n=1}^2\left(\frac{\partial u_\beta^n}{\partial u_\alpha^j}\right)\left(\frac{\partial u_\beta^m}{\partial u_\alpha^i}\right)\left(\frac{\partial u_\alpha^k}{\partial u_\beta^l}\right)\Gamma_{m\ n}^{\; l}(\beta)\tag*{(#3)}\label{con_coeff}
{{</equation>}}
となる．
この表式から $\Gamma_{i\ j}^{\; k}$ はテンソル場ではないことがわかるが，
{{<equation>}}
S_{ij}^{\; k}=\Gamma_{i\ j}^{\; k}-\Gamma_{j\ i}^{\; k}
{{</equation>}}
はテンソル場となることがわかる．$S_{ij}^{\; k}$ は$\textbf{捩率テンソル(torsion tensor)}$と呼ばれる．
以上の性質をもつ $\Gamma_{i\ j}^{\; k}$ を$\textbf{接続係数}$という量として定める．

----
**定義 2.8**\
各座標近傍の$C^\infty$ 関数 $\Gamma_{i\ j}^{\ k},i,j,k=1,2$ で，変換式$\ref{con_coeff}$にしたがう量を $M$ の$\textbf{接続係数}$という．
また，，各座標近傍にこのような関数を定義することを $M$ に接続を定めるという．

----

#### その他の共変微分の性質

**(問2.11)**\
二次元可微分多様体 $M$ 上に2つの反変ベクトル場 $\xi_{(1)},\xi_{(2)}$ が存在し，各点でそれらが一次独立ならば，
行列 $(\xi_{(i)}^j(p))_{1\le i,j\le2}$ に逆行列が存在する．
この逆行列を $(\zeta_{i}^{(j)}(p))_{1\le i,j\le2}$ と表し,
{{<equation>}}
\Gamma_{i\ j}^{\ k}=\sum_{m=1}^2\xi_{(m)}^k\left(\frac{\partial\zeta_j^{(m)}}{\partial u^i}\right)
{{</equation>}}
 とするとき，$\Gamma_{i\ j}^{\ k}$ は接続係数である．

**(例題2.11)**\
ベクトル場 $\xi=\sum_j\xi^j(\partial/\partial u^j)$ の共変微分 $\nabla_i\xi^j$ は$p\in U_\alpha\cap U_\beta\neq\phi$ のとき
{{<equation>}}
\nabla_i^{(\alpha)}\xi_\alpha^j
&=\sum_{k,l=1}^2\dfrac{\partial u_\beta^k}{\partial u_\alpha^i}\dfrac{\partial u_\alpha^j}{\partial u_\beta^l}\nabla_k^{(\beta)}\xi_\beta^l
{{</equation>}}
と変換するテンソルである．

**(例題2.12)**\
共変ベクトル場 $t=\sum_jt_jdu^j$ について,ベクトル場に対する共変微分と同様に
{{<equation>}}
t(p+\Delta p)-t(p)=\sum_{i,j}\Delta u^i\left(\nabla_it_j\right)du^j,\; 
\nabla_it_j=\dfrac{\partial}{\partial u^i}t_j-\sum_k\Gamma_{i\ j}^{\ k}t_k
{{</equation>}}
と表される．

**(命題2.5)**\
$(2,1)$ テンソル場 $t^{ij}\ _k$の共変微分は
{{<equation>}}
\nabla_lt^{ij}\ _k=\dfrac{\partial}{\partial u^l}t^{ij}\ _k
+\sum_{m=1}^2\Gamma_{l\ m}^{\ i}t^{mj}\ _k
+\sum_{m=1}^2\Gamma_{l\ m}^{\ j}t^{im}\ _k
-\sum_{m=1}^2\Gamma_{l\ k}^{\ m}t^{ij}\ _m
{{</equation>}}
と表される．

**(問2.13)**\
2つのテンソル場 $t^{ij},s_{mn}$ とその縮約 $\sum_{ij}t^{ij}s_{ij}$ について，
微分と共変微分の関係式
{{<equation>}}
\dfrac{\partial}{\partial u^l}\sum_{i,j}t^{ij}s_{ij}
=\nabla_l\left(\sum_{i,j}t^{ij}s_{ij}\right)
=\sum_{i,j}\nabla_l\left(t^{ij}\right)s_{ij}
=\sum_{i,j}t^{ij}\nabla_l\left(s_{ij}\right)
{{</equation>}}
が成り立つ．


<a id="markdown-002" name="002"></a>

### リーマン接続


<!--
<a id="markdown-003" name="003"></a>

### 平行移動と測地線
#### リーマン計量による曲線の長さの表現

#### 平行移動

#### 測地線

<a id="markdown-004" name="004"></a>

### 双対接続
<a id="markdown-005" name="005"></a>
-->