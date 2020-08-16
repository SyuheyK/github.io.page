---
title: "測度の畳み込み"
tags: ["測度論","確率論"]
date: 2020-08-12T10:00:00+09:00
draft: true
---

## 内容
$\mathcal{M}(\mathbb{R}^d)$ を $\mathbb{R}^d$ 上のBorel測度として，次式で **畳み込み** を定める:
{{< equation >}}
  (\mu_1\ast\mu_2)(A)=\int_{\mathbb{R}^d}\mathbb{I}_A(x+y)\mu_1(dx)\mu_2(dy).
{{< /equation >}}

ただし，$\mu_i\in\mathcal{M}(\mathbb{R}^d),i=1,2,A\in\mathcal{B}(\mathbb{R}^d)$ とする．
$A-x=\{y-x,y\in A\}$ とすると，
{{< equation >}}
  (\mu_1\ast\mu_2)(A)=\int_{\mathbb{R}^d}\mu_1(A-x)\mu_2(dx)=\int_{\mathbb{R}^d}\mu_2(A-x)\mu_1(dx)
{{< /equation >}}
と表されることが，Fubiniの定理と $\mathbb{I}_A(x+y)=\mathbb{I} _{A-x}(y)$ から言うこともできる．

この様に定めた畳み込みは，再び測度となる:

#### <a id="prop1">命題 1.</a>
畳み込み $\mu_1\ast\mu_2$ は $\mathbb{R}^d$ 上の測度である．

---

さらにこのことから，畳み込みは $\mathcal{M}(\mathbb{R}^d)$ 上の二項演算であることがわかる．このことを以下の命題にまとめる．

#### <a id="prop2">命題 2.</a>
$f\in\mathbf{B}_\mathrm{b}(\mathbb{R}^d)$ ならば，任意の測度 $\mu_i\in\mathcal{M}(\mathbb{R}),i=1,2,3$ に対して次がな成り立つ．\
1. 
{{< equation>}}
  \int_{\mathbb{R}^d}f(y)(\mu_1\ast\mu_2)(dy)=\int_{\mathbb{R}^d}\int_{\mathbb{R}^d}f(x+y)\mu_1(dy)\mu_2(dx),
{{< /equation>}}
2. 
{{< equation>}}
  \mu_1\ast\mu_2=\mu_2\ast\mu_1
{{< /equation>}}
3. 
{{< equation>}}
  (\mu_1\ast\mu_2)\ast\mu_3 = \mu_1\ast(\mu_2\ast\mu_3)
{{< /equation>}}

ただし，$\mathbf{B}_\mathrm{b}(\mathbb{R}^d)$ は値域を $\mathbb{R}^d$ にもつ有界なBorel可測関数の全体からなる線形空間を表す．

---
畳み込みと確率論における期待値との関係は次のとおり表現できる．

#### <a id="col3">系 3.</a>
$X_1$ と $X_2$ を確率空間 $(\Omega,\mathcal{F},P)$ 上の独立な確率変数とし，結合密度を $p$，周辺密度をそれぞれ $\mu_1,\mu_2$ とする．
このとき，任意の $f\in\mathbf{B}_\mathrm{b}(\mathbb{R}^d)$ に対して次が成り立つ
{{< equation >}}
  \mathbb{E}[f(X_1+X_2)]=\int_{\mathbb{R}^d}f(z)(\mu_1\ast\mu_2)(dz)
{{< /equation >}}

---
<a href="#col3">系 3.</a>より，確率測度に対する畳み込みは，2つの独立な確率変数の和の確率分布となる，すなわち
{{< equation >}}
  P(X_1+X_2\in A)=\mathbb{E}[\mathbb{I}_A(X_1+X_2)]=(\mu_1\ast\mu_2)(A)
{{< /equation >}}
である．

また，n回の畳込みを $\mu^{\ast^n}=\mu\ast\cdots\ast\mu$ と定め，逆に $\mu=(\mu^{1/n})^{\ast^n}$ となる $\mu^{1/n}$ が存在するとき，$\mu$ は $n$ 乗根の畳み込みを持つと呼ぶ．

## 証明
#### 命題 1.の証明
[<a href="#prop1">命題 1.の内容</a>]

