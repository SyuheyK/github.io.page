---
title: "Jump過程① -Poisson過程と点過程-"
tags: ["確率論"]
date: 2020-11-21T10:00:00+09:00
draft: false
---

<a id="markdown-001" name="001"></a>

## [Poisson過程とその性質](https://en.wikipedia.org/wiki/Poisson_point_process)
$(\tau_i)_{i\ge1}$ をそれぞれがパラメータ $\lambda$ の指数分布に従う独立な確率変数のベクトルとし，$T_n=\sum_i^n\tau_i$とする．
次式で定められる確率過程 $(N_t,t\ge0)$ を，強度 $\lambda$ のPoisson過程と呼ぶ．
{{<equation>}}
N_t = \sum_{n\ge1}1_{t\ge T_n}(t).
{{</equation>}}
<!--ランダムな時刻 $(T_n)$ の発生回数を表す確率過程であることから，計数過程である．-->

### Poisson過程の性質
1. 任意の $t>0$ に対して，$N_t$ は確率 $1$ で有限である．
1. 任意のシナリオ $\omega$ に対して，サンプルパス $t\rightarrow N_t(\omega)$ は区分的に定数であり，ジャンプ幅 $1$ で逓増する．
1. サンプルパス $t\rightarrow N_t$ は右連続左極限である．
1. 任意の $t$ に対して確率 $1$ で $N_{t-}=N_t$ である[^1]．
1. $(N_t)$ は確率収束の意味で連続である:
{{<equation>}}
\forall t>0, N_s\underset{s\rightarrow t}{\overset{\mathbb{P}}{\rightarrow}}N_t
{{</equation>}}
1. 任意の $t>0$ に対して，$N_t$ はパラメータ$\lambda t$ のPoisson分布にしたがう:
{{<equation>}}
\forall n\in\mathbb{N}, P(N_t=n)=e^{-\lambda t}\dfrac{(\lambda t)^n}{n!}
{{</equation>}}
1. $N_t$ の特性関数は次式となる:
{{<equation>}}
E[e^{iuN_t}]=\exp\left\{ \lambda t(e^{iu}-1) \right\}, \forall u\in\mathbb{R}
{{</equation>}}
1. $(N_t)$ は独立増分をもつ:任意の $t_1< \cdots< t_n$ に対して，$N_{t_n}-N_{t_{n-1}},...,N_{t_2}-N_{t_1},N_{t_1}$は互いに独立である．
1. $(N_t)$ はMarkov性をもつ:
{{<equation>}}
\forall t>s, E[f(N_t)|N_u,u\le s]=E[f(N_t)|N_s ]
{{</equation>}}

### Poisson過程に関する命題

**命題1**
$(N_t^1)_ {t\ge0}$が強度 $\lambda_1$，$(N_t^2)_ {t\ge0}$が強度 $\lambda_2$の，互いに独立なPoisson過程であるとき，
$(N_t^1+N_t^2)_ {t\ge0}$は強度 $\lambda_1+\lambda_2$のPoisson過程である．

**命題2**
ジャンプの発生時刻をあらわす確率変数の列 $(T_n,n\ge1)$ が，確率 $p\in[0,1]$ で発生し，確率 $1-p$ で発生しないとし，発生した $(T_n,n\ge1)$ を並べ直した確率変数の列 $(T_n',n\ge1)$ を使って新たな確率過程 $X_t$ を
{{<equation>}}
X_t=\sum_{n\ge1}1_{t\ge T_t'}(t)
{{</equation>}}
と定めると，$X_t$ もまたPoisson過程となる．

## ランダム測度と点過程
上記のPoisson過程の定義に基づけば，ランダムな時刻$T_1,T_2,...$ は $N$ がジャンプする時刻を表し，$N_t$ は区間 $[0,t]$ におけるジャンプの回数を表すことから，$(N_t)_{t\ge0}$ 計数過程と呼ばれる．
{{<equation>}}
N_t=\sharp\left\{i\ge1,T_i\in[0,t]\right\}
{{</equation>}}
同様に $t>s$ のとき
{{<equation>}}
N_t-N_s=\sharp\left\{i\ge1,T_i\in(s,t]\right\}
{{</equation>}}

ジャンプ時刻 $T_1,T_2,...$ は区間 $[0,\infty)$ 上のランダムな発生時点を表し，$N_t$ はその発生時点を区間 $[0,t]$ でカウントしている形になる．
このジャンプをカウントする方法を基に，以下のように区間 $[0,\infty)$ 上の測度 $M$ を作ることができる:
任意の可測集合 $A\subset\mathbb{R}^+$ に対して
{{<equation>}}
M(\omega,A)=\sharp\left\{i\ge1,T_i(\omega)\in A\right\}.
{{</equation>}}
このような定義にすると，$M(\omega,\cdot)$ は正整数値の測度で有限な可測集合 $A$ に対しては確率 $1$ で $M(A)$ が有限となる．

$M(\omega,\cdot)$ を測度として捉えると，$\omega$ に依存することから，この測度 $M$ はランダム測度と呼ばれる．
また，上記の $M$ はPoisson過程 $N$ から導かれたランダム測度であるため，Poissonランダム測度と呼ばれる．
Poisson過程ではない計数過程からもランダム測度を定めることができ，それらはPoissonランダム測度とは異なるものとなる．

Poissonランダム測度を使ってPoisson過程を書き直すと以下のとおりとなる:
{{<equation>}}
N_t(\omega)=M(\omega,[0,t])=\int_{[0,t]}M(\omega,ds)
{{</equation>}}
Poisson過程の性質を測度 $M$ で言い換えると以下の様になる．
$[t_ 1,t_ 1'],...,[t_ n,t_ n']$ を重複のない区間の集まりとする．
1. $M([t_ k,t_ k'])$ は区間 $[t_ k,t_ k']$ におけるPoisson過程のジャンプ回数を表す．すなわち，パラメータ $\lambda(t_ k'-t_ k)$ のPoisson分布に従う確率変数である．
1. $2$ つの重複のない区間 $j\neq k$ について，$M([t_ j,t_ j'])$ と $M([t_ k,t_ k'])$ は独立な確率変数である．
1. 一般に $A$ 任意の可測集合 $A$ に対して，$M(A)$ はパラメータ $\lambda|A|$ のPoisson分布に従う．ただし，$|A|=\int_Adx$ は $A$ のLebesgue測度とする．

Poissonランダム測度 $M$ はPoisson過程の``微分''と見ることもできる．
Poisson過程のサンプルパス $t\mapsto N_t(\omega)$ は単調増加な階段関数であったから，その超関数の意味での微分は正値の測度となる:
{{<equation>}}
\dfrac{d}{dt}N_t(\omega)=M(\omega,[0,t])\text{ where }M=\sum_{i\ge1}\delta_{T_i(\omega)}
{{</equation>}}
ここで，$\delta_A$ はDirac測度である．


[^1]: Poisson分布の性質 2.と3.で非連続点が確率 $1$ で存在すると言っているのに，ここでは確率 $1$ で連続と言っているのは，非連続点の測度が $0$ となるためである．