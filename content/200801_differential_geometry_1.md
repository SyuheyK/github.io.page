---
title: "微分幾何のまとめ 1"
tags: ["微分幾何"]
date: 2020-08-01T10:00:00+09:00
draft: false
---
[細野忍「微分幾何」](http://www.asakura.co.jp/books/isbn/978-4-254-11849-0/)を元に，
リーマン幾何学に関する内容をダイジェストでまとめます．

### 内容
- [可微分多様体の定義](#001)
- [多様体上の関数と**接空間**](#002)
- [局所座標近傍間の貼り合わせと**ベクトル場**](#003)
- [**リーマン計量**](#004)
- [リーマン計量の**テンソル場**としての特徴づけ](#005)

<a id="markdown-001" name="001"></a>

### 可微分多様体の定義
全体をとおして，可微分多様体 $M$ を考える．
可微分多様体 $M$ とは，
(位相)多様体 $M$ について，
$U_\alpha\cap U_\beta\neq\phi$ をみたす任意の$2$つの局所座標近傍 $(U_\alpha,\phi_\alpha)$ と $(U_\beta,\phi_\beta)$ について，
両者の間の座標を移す連続写像:
{{< equation >}}
  \phi_{\beta\alpha}:=\phi_\beta\circ\phi^{-1}_\alpha:\phi_\alpha(U_\alpha\cap U_\beta)\rightarrow\phi_\beta(U_\alpha\cap U_\beta)
{{< /equation >}}
が定められていて，その座標変換関数が具体的に
{{< equation >}}
    u^1_\beta(p)&=u^1_\beta(u^1_\alpha(p),u^2_\alpha(p))=u^1_\beta(u^1_\alpha,u^2_\alpha)(p),
  \\u^2_\beta(p)&=u^2_\beta(u^1_\alpha(p),u^2_\alpha(p))=u^2_\beta(u^1_\alpha,u^2_\alpha)(p)
{{< /equation >}}
と書かれ，$C^\infty$ 級関数となっているものである．

<a id="markdown-002" name="002"></a>

### 多様体上の関数と接空間
Euclid空間 $\mathbb{E}^3$ 内の曲面上の点 $p$ における接平面が$2$ つのベクトルを基底に定められたことと同様に，
可微分多様体上での曲面およびその接平面を考える．そのために
- 可微分多様体 $M$ 上の $C^\infty$ 級関数(曲面の方程式に対応)
- その関数の方向微分(接平面を構成する接ベクトルに対応)
に関して考察し，可微分多様体での"接平面(=接空間)"を定める．

$M$ 上の関数 $f:M\rightarrow\mathbb{R}$ を考え，これが $C^\infty$ 級関数であることを，任意の局所座標近傍 $(U_\alpha,\phi_\alpha)$ について
{{< equation >}}
  f\circ\phi_\alpha^{-1}:\phi_\alpha(U_\alpha)\rightarrow\mathbb{R}
{{< /equation >}}
が $C^\infty$ 級関数であることと定める．
この関数 $f$ を $u^1_\alpha\times u^2_\alpha$ 平面上の二変数関数と捉えると関数 $f$ の偏微分を
{{< equation >}}
  \dfrac{\partial f}{\partial u^i_\alpha}(p):=\dfrac{\partial(f\circ\phi^{-1}_\alpha)(u^1_\alpha,u^2_\alpha)}{\partial u^i_\alpha}(p)
{{< /equation >}}
各変数$u^1_\alpha,u^2_\alpha$による偏微分の線形結合を用いれば，方向微分を
{{< equation >}}
  \xi^1\dfrac{\partial f}{\partial u^1_\alpha}(p) + \xi^2\dfrac{\partial f}{\partial u^2_\alpha}(p)
  &=\xi^1\dfrac{\partial(f\circ\phi^{-1}_\alpha)(u^1_\alpha,u^2_\alpha)}{\partial u^1_\alpha}(p)
   + \xi^2\dfrac{\partial(f\circ\phi^{-1}_\alpha)(u^1_\alpha,u^2_\alpha)}{\partial u^2_\alpha}(p)
{{< /equation >}}
と定めることができるが，さらにこれを
{{< equation>}}
  \xi^1\dfrac{\partial f}{\partial u^1_\alpha}(p) + \xi^2\dfrac{\partial f}{\partial u^2_\alpha}(p)
  &= \left\{\xi^1\left(\dfrac{\partial}{\partial u^1_\alpha}\right)_p + \xi^2\left(\dfrac{\partial}{\partial u^2_\alpha}\right)_p\right\}f
{{< /equation>}}
と変形し，関数 $f$ に作用する部分を方向微分と捉える．
ここで $(\partial/\partial u^i_\alpha)_p$ は点 $p$ における偏微分を表す．
この様に定義した方向微分を2つ考え
{{< equation>}}
  \xi_p=\sum_{i=1}^2\xi^i\left(\dfrac{\partial}{\partial u^i_\alpha}\right)_p
  ,\;\eta_p=\sum_{i=1}^2\eta^i\left(\dfrac{\partial}{\partial u^i_\alpha}\right)_p
{{< /equation>}}
と表し，線形和と定数倍を

1. $\xi_p+\eta_p=(\xi^1+\eta^1)(\partial/\partial u^1_\alpha)_p+(\xi^2+\eta^2)(\partial/\partial u^2_\alpha)_p$
1. $c\xi=c\xi^1(\partial/\partial u^1_\alpha)_p+c\xi^2(\partial/\partial u^2_\alpha)_p$

と定めれば，方向微分全体はベクトル空間となる．
この様に作った2つの方向微分$(\partial/\partial u^1_\alpha)_p,(\partial/\partial u^2_\alpha)_p$は一次独立であることを示すことができるので(例題 2.7)，
方向微分全体が作るベクトル空間の次元は2次元であることがわかる．

このベクトル空間のことを **接空間** と呼び $T_pM$ と表す．

<a id="markdown-003" name="003"></a>

### 局所座標近傍間の貼り合わせとベクトル場
上記のとおり定義された接空間は局所座標近傍によらず定義されていることを示すことができる．
まず，$(U_\alpha,\phi_\alpha)$ 上で $C^\infty$ 級である関数 $f$ は，
$U_\alpha\cap U_\beta\neq\phi$ である $\phi_\beta(U_\alpha\cap U_\beta)$ 上で
{{< equation >}}
  f\circ\phi_\beta^{-1}=(f\circ\phi^{-1}_\alpha)\circ(\phi_\alpha\circ\phi^{-1}_\beta)
  =(f\circ\phi^{-1}_\alpha)\circ\phi^{-1}_{\alpha\beta},\;\phi_{\alpha\beta}:\phi_\beta(U_\alpha\cap U_\beta)\rightarrow\phi_\alpha(U_\alpha\cap U_\beta)
{{< /equation >}}
より，また $C^\infty$ 級となっていることに留意する．
各座標変換関数が $C^\infty$ 級関数であることにより，$(U_\alpha,\phi_\alpha)$ 上での連続性が $(U_\beta,\phi_\beta)$ 上での連続性に"貼り合わさって"いる ．

この性質を用いると，点 $p\in U_\alpha\cap U_\beta=\phi$ について,偏微分(基底)の性質として
{{< equation >}}
  \left(\dfrac{\partial}{\partial u^i_\alpha}\right)_p=\sum_{j=1}^2\dfrac{\partial u^j_\beta}{\partial u^i_\alpha}\left(\dfrac{\partial}{\partial u^j_\beta}\right)_p\;i=1,2
{{< /equation >}}
が成り立つことがわかる(例題 2.8)．
座標変換関数 $u^i_\beta$ は可逆[^1]な $C^\infty$ 級関数であるから，その関数行列(Jacobean) $(\partial u^j_\beta/\partial u^i_\alpha)_{1\le i,j\le 2}$ は正則である．
したがって，上式を正則行列による基底の変換を表していると読めば，それらによって生成されるベクトル空間は等しいことがわかる．
すなわち，接空間 $T_pM$ は局所座標近傍のとり方に寄らないということがわかる．

このことから，成分 $\xi^1,\xi^2$ を用いて接空間 $T_pM$ のベクトルを，座標近傍を明らかにせず
{{< equation >}}
  \xi_p=\xi^1\left(\dfrac{\partial}{\partial u^1}\right)_p + \xi^2\left(\dfrac{\partial}{\partial u^2}\right)_p
{{< /equation >}}
と書くことができる．ただし，$\xi^1,\xi^2$ の値は局所座標近傍の取り方に依存することに注意する．
そのため，これらの成分が依存する局所座標近傍を明示するときは $\xi^1_\alpha,\xi^2_\alpha$ などとし，
{{< equation >}}
  \xi_p=\xi^1_\alpha\left(\dfrac{\partial}{\partial u^1_\alpha}\right)_p + \xi^2_\alpha\left(\dfrac{\partial}{\partial u^2_\alpha}\right)_p
{{< /equation >}}
と書く．先程の偏微分(基底)の性質に対応して，$U_\alpha\cap U_\beta\neq\phi$ 上で，接空間 $T_pM$ のベクトル $\xi_p$ の2とおりの成分表示 $(\xi^1_\alpha,\xi^2_\alpha),(\xi^1_\beta,\xi^2_\beta)$ とするとき，
{{< equation >}}
  \xi^i_\alpha =\sum_{j=1}^2\dfrac{\partial u^i_\alpha}{\partial u^j_\beta}\xi^j_\beta,\;i=1,2
{{< /equation >}}
が成り立つ(例題 2.9)．

接空間 $T_pM$ のベクトル $\xi_p$ で，点 $p$ を $M$ 全体にわたって動かして考えるとき，それを
{{< equation>}}
  \xi = \xi^1\left(\dfrac{\partial}{\partial u^1}\right) + \xi^2\left(\dfrac{\partial}{\partial u^2}\right)
{{< /equation>}}
と書く．$M$ 上の各点 $p$ に対して $\xi_p$ が決まるので，$\xi$ を**ベクトル場** と呼ぶ．

<a id="markdown-004" name="004"></a>

### リーマン計量
$M$ の各点 $p$ における接空間 $T_pM$ 上の正定値対称二次形式な内積として，任意のベクトル場 $\xi,\eta$ に対して以下の条件をみたす $g(\xi,\eta)$ を考える．

1. $g(\xi,\eta) = g(\eta,\xi)$
1. $g(a\xi+b\eta,\zeta)=ag(\xi,\zeta)+bg(\eta,\zeta)$
1. $\xi\neq0\Rightarrow g(\xi,\xi)>0$

ただし，$\xi,\eta,\zeta$ は任意のベクトル場，$a,b\in\mathbb{R}$ とする．
このような性質をもつ $g$ を **計量** と呼ぶ．

座標近傍を $(U_\alpha,\phi_\alpha)$，$T_pM$ の基底を $(\partial/\partial u_\alpha^1)_p,(\partial/\partial u_\alpha^2)_p$ とするとき，計量を
{{< equation >}} 
  g^{(\alpha)}_{ij}(p)=g^{(\alpha)}\left(\left(\dfrac{\partial}{\partial u^i_\alpha}\right)_p,\left(\dfrac{\partial}{\partial u^j_\alpha}\right)_p\right)
{{< /equation >}} 
と定めると，$T_pM$ 上の正定値内積となる．

これを $p$ の関数と見たときにすべての座標近傍に対して $C^\infty$ 級となるとき，$g$ を $M$ の $C^\infty$ 級リーマン計量，あるいは単に **リーマン計量** と呼ぶ．またリーマン計量が与えられた可微分多様体のことを **リーマン多様体** と呼ぶ．

また，$p\in U_\alpha\cap U_\beta(\neq\phi)$ に対して
{{< equation >}}
  g_{ij}^{(\alpha)}(p)=\sum_{k,l=1}^2\dfrac{\partial u^k_\beta}{\partial u^i_\alpha}\dfrac{\partial u^l_\beta}{\partial u^j_\alpha}g_{kl}^{(\beta)}
{{< /equation >}}
を示すことができる(問2.5)．
各座標近傍 $(U_\alpha,\phi_\alpha)$ で正定値対称行列 $g_{ij}^{(\alpha)}$ を定め，
$\left(g_{ij}^{(\alpha)}\right)_{\alpha\in A}$ がこの式にしたがってリーマン計量が $C^\infty$ 級であるという条件が $M$ 全体に張り合っていれば，
上記内積の公理を満たすリーマン計量 $g$ が得られる．


<a id="markdown-005" name="005"></a>

### リーマン計量のテンソル場としての特徴づけ
上記で定義したリーマン計量という値をテンソル場として特徴づける．

接空間 $T_pM$ の自然な基底として，
{{< equation >}}
  \left(\dfrac{\partial }{\partial u^1}\right)_p, \left(\dfrac{\partial }{\partial u^2}\right)_p
{{< /equation >}}
をとることができる．この基底の双対基底として各 $i,j=1,2$ に対して
{{< equation >}}
  (du^i)_p\left(\dfrac{\partial }{\partial u^j}\right)_p=\delta_j^i=
  \begin{cases}
      1, & \text{if}\ i=j \\
      0, & \text{otherwise}
  \end{cases}
{{< /equation >}}
となるように定められた $(du^i)_p$ で生成された $T_pM$ の双対空間は余接空間と呼ばれ，$T^\ast_pM$ と表される．

$T_pM$ の基底 $(\partial/\partial u^i)_p,i=1,2$ と双対基底 $(du^j)_p,j=1,2$ を用いて，
$(r,s)$ テンソル $t_p$ を

{{< equation >}}
  t_p = \sum_{i_1,...,i_r,j_1,...,j_s}t^{i_1,...,i_r}\;_{j_1,...,j_s}(p)\left(\dfrac{\partial}{\partial u^{i_1}}\right)_p\otimes\cdots\otimes\left(\dfrac{\partial}{\partial u^{i_r}}\right)_p\otimes(du^{j_1})_p\otimes\cdots\otimes(du^{j_s})_p
{{< /equation >}}
と定める．ただし，$p\in U_\alpha\cap U_\beta(\neq\phi)$ とする．

点 $p$ が $M$ 全体をわたって動くとき，$t$ を $(r,s)$ テンソル場と呼ぶ．

リーマン計量は $(0,2)$ テンソル場
{{< equation >}}
  ds^2=\sum_{i,j=1}^2g_{ij}du^i\otimes du^j
{{< /equation >}}
によって，無限小線分の長さを意味するものとして表すことができる．
これを簡略して
{{< equation >}}
  ds^2=\sum_{i,j=1}^2g_{ij}du^idu^j
{{< /equation >}}
とも書くが，意味することは $(0,2)$ テンソル場である．

[^1]: 上記では詳細になるため省略しているが，局所座標近傍における座標変換関数 $\phi$ は $D\subset\mathbb{R}$ への同相写像と定めている．