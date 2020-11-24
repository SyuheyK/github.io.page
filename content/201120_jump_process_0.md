---
title: "Jump過程⓪ -Jump過程で使う分布-"
tags: ["確率論"]
date: 2020-11-20T10:00:00+09:00
draft: true
---

<a id="markdown-001" name="001"></a>

### [指数分布](https://en.wikipedia.org/wiki/Exponential_distribution)

非負確率変数 $X$ がパラメータ $\lambda$ 指数分布に従うとき，その確率密度関数は$x\ge0$ に対して，
{{<equation>}}
f_X(x;\lambda) = \lambda e^{-\lambda x}
{{</equation>}}
である．これから簡単な計算により分布関数は，$p\ge0$ に対して
{{<equation>}}
F_X(p)=P(X\le p)=\int_0^p f_X(x;\lambda)dx=\lambda\int_0^p e^{-\lambda x}dx=1-e^{-\lambda p}
{{</equation>}}
となることがわかる．
<!--
またこのことから，$F_X(x)$ は反転可能で，その逆関数は $p\in[0,1]$ に対して
{{<equation>}}
F^{-1}_X(p)=\dfrac{1}{\lambda}\ln(1-p)
{{</equation>}}
となることもわかる．
-->

#### 指数分布の無記憶性
指数分布に従う確率変数 $X$ の確率に関して以下の計算ができる．
{{<equation>}}
P(X\ge t)&=\int_t^\infty f_X(x;\lambda)dx=\int_t^\infty\lambda e^{-\lambda x}dx=e^{-\lambda t}\\
P(X\ge t+s)&=\int_{t+s}^\infty f_X(x;\lambda)dx=\int_t^\infty\lambda e^{-\lambda (x+s)}dx=e^{-\lambda s}\int_t^\infty\lambda e^{-\lambda x}dx=P(X\ge t)P(X\ge s)
{{</equation>}}
したがって，次式が成り立ち，
{{<equation>}}
P(X\ge t+s|X\ge t)=\dfrac{P(X\ge t+s)}{P(X\ge t)}=P(X\ge s)
{{</equation>}}
$X$をランダムな時刻を表す確率変数と見立てたとき，上式は$t$ までの事象で条件付けた $t+s$ 以降の情報は $s$ 以降の情報と一致するということを表すことから，指数分布の無記憶性と呼ばれる．


### [Dirichlet分布](https://en.wikipedia.org/wiki/Dirichlet_distribution)
Dirichlet分布はBeta分布を多変数に拡張したものなので，Beta分布を説明した後，Dirichlet分布の定義を述べ，指数分布との関連性を示す．

#### [Beta分布](https://en.wikipedia.org/wiki/Beta_distribution)
非負確率変数 $X$ がパラメータ $a>0,b>0$ のBeta分布に従うとき，その確率密度関数は$x\in[0,1]$ に対して，
{{<equation>}}
f_X(x;a,b) = \dfrac{\Gamma(a+b)}{\Gamma(a)\Gamma(b)}x^{a-1}(1-x)^{b-1}
{{</equation>}}
である．ここで，$\Gamma(a)$ は[Gamma関数](https://en.wikipedia.org/wiki/Gamma_function)を表し，$p>0$ に対して
{{<equation>}}
\Gamma(p) = \int_0^\infty x^{p-1}e^{-x}dx
{{</equation>}}
で定められる．

#### Dirichlet分布
Dirichlet分布は，Beta分布を二項分布の一般化と見たときの多項分布の一般化に対応する．
非負確率変数ベクトル $\boldsymbol{X}$ を

#### Dirichlet分布と指数分布の関係
$(\tau_1,...,\tau_n)$ を独立にパラメータ $\lambda$ の指数分布に従う確率変数のベクトルとし，$T_k = \tau_1+\cdots+\tau_k$ とする．
このとき確率変数ベクトル $(T_1,...,T_n)$ は $\mathbb{R}^n$ 上に同時密度
{{<equation>}}
\lambda^ne^{-\lambda t_n}1_{0< t_1< \cdots< t_n}(t_1,...,t_n)
{{</equation>}}
をもち，$T_n=\tau_1+\cdots+\tau_n$は確率密度関数
{{<equation>}}
f_{T_n}(t) = \lambda e^{-\lambda t}\dfrac{(\lambda t)^{n-1}}{(n-1)!}1_{[0,\infty) }(t)
{{</equation>}}
をもつ．


### [Poisson分布](https://en.wikipedia.org/wiki/Poisson_distribution)

#### Poisson分布と指数分布の関係
