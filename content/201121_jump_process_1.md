---
title: "Jump過程① -Poisson過程と点過程-"
tags: ["確率論"]
date: 2020-11-21T10:00:00+09:00
draft: false
---

<a id="markdown-001" name="001"></a>

## Poisson過程とその性質
$(\tau_i)_{i\ge1}$ をそれぞれがパラメータ $\lambda$ の指数分布に従う独立な確率変数のベクトルとし，$T_n=\sum_i^n\tau_i$とする．
次式で定められる確率過程 $(N_t,t\ge0)$ を，強度 $\lambda$ の[Poisson過程](https://en.wikipedia.org/wiki/Poisson_point_process)と呼ぶ．
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
\dfrac{d}{dt}N_t(\omega)=M(\omega,[0,t])=\sum_{i\ge1}\delta_{T_i(\omega)}([0,t])
{{</equation>}}
ここで，$\delta_A(x)$ は[Dirac測度](https://en.wikipedia.org/wiki/Dirac_measure)である．

### Poissonランダム測度の定義
上記のPoissonランダム測度の定義をより一般的にフォーマルな設定で述べると以下のようになる
$(\Omega,\mathcal{F},P)$ を確率空間とし，$E\subset\mathbb{R}^d$，$\mu$ を $(E,\mathcal{E})$ 上の正値Radon測度とする．
$E$ 上の強度測度 $\mu$ の Poissonランダム測度とは，整数値ランダム測度:
{{<equation>}}
M:\Omega\times\mathcal{E}&\rightarrow\mathbb{N}\\
(\omega,A)&\mapsto M(\omega,A)
{{</equation>}}
で次をみたすものである．
1. ほとんどすべての $\omega\in\Omega$ に対して，$M(\omega,\cdot)$ は$E$ 上の整数値Radon測度である．すなわち，任意の有限な $A\subset E$ に対して，$M(A)(<\infty)$ は整数値確率変数である．
1. 任意の $A\subset E$ に対して，$M(\cdot,A)=M(A)$ はパラメータ $\mu(A)$ のPoisson分布に従う確率変数である:
{{<equation>}}
\forall k\in\mathbb{N}, P(M(A)=k)=e^{-\mu(A)}\dfrac{\mu(A)^k}{k!}
{{</equation>}}
1. 互いに排反な可測集合 $A_1,...,A_n\in\mathcal{E}$ に対して，$M(A_1),...,M(A_n)$ は互いに独立である．

Poissonランダム測度の構成については以下の命題が成り立つ．

**命題3**
任意の $E\subset\mathbb{R}^d$ 上のRadon測度 $\mu$ に対して，$E$ 上の強度 $\mu$ のPoissonランダム測度 $M$ が存在する．

### 数え上げ測度としての意味付け
$E$上の任意のPoissonランダム測度は，$E$ 内のランダムな点列の[数え上げ測度](https://en.wikipedia.org/wiki/Counting_measure)として表現することができる[^2]．
すなわち $E$ 内の点列 $\{X_n(\omega),n\ge1\}$ が存在して，
{{<equation>}}
\forall A\in\mathcal{E}, M(\omega,A)=\sum_{n\ge1}1_{A}(X_n(\omega))=\sum_{n\ge1}\delta_{X_n(\omega)}(A)
{{</equation>}}
と表すことができる．またはDirac測度を用いて，単に
{{<equation>}}
M=\sum_{n\ge1}\delta_{X_n}
{{</equation>}}
と書ける．
また $M(A)$ は任意のコンパクト集合 $A\subset E$ に対して有限でなければならない.
そのため点列 $(X_n)_ {n\ge1}$ は，任意のコンパクトな $A\subset E$ に対して $A\cap${ $X_n,n\ge1$} が確率 $1$ で有限にならなければならない．
したがって，点列 $(X_n)_ {n\ge1}$ は $E$ 内において，$1$ 点に2つ以上重複してはいけないことがこの条件から導かれる．

### Poissonランダム測度から得られるジャンプ過程
上記の数え上げ測度としての意味から，Poissonランダム測度からジャンプ過程を作ることができる．
$E=[0,T]\times\mathbb{R}^d\backslash\text{{0}}$ 上のPoissonランダム測度 $M$ を考えると，直積集合のそれぞれの要素を $(T_n,Y_n)\in E$ とすることで，
{{<equation>}}
M=\sum_{n\ge1}\delta_{(T_n,Y_n)}
{{</equation>}}
と数え上げ測度として表現することができる．

各要素はそれぞれ，$T_n$ はジャンプの観測時刻を，$Y_n$ はジャンプ時点で明らかになる情報を表す．
確率空間 $(\Omega,\mathcal{F},P)$ にフィルトレーション $\mathcal{F}_t$ を付けたとき，以下の性質をみたす $M$ を $\mathcal{F}_t$-適合なPoissonランダム測度と呼ぶ．
- $(T_n)_{n\ge1}$ は $\mathcal{F}_t$-適合なランダム時刻である．
- $Y_n$ は $\mathcal{F}_{T_n}$-適合な確率変数である．

Standard machineを使って単関数を使って近似を行うことで，$\omega$ ごとに $E=[0,T]\times\mathbb{R}^d\backslash${0} 上の測度 $M(\omega,\cdot)$ に関する積分を定めることができる．この結果に対して，時点に関する積分区間を $t\in[0,T]$ までとして積分すると，
{{<equation>}}
X_t=\int_0^t\int_{\mathbb{R}^d\backslash\text{{0}}}f(s,y)M(ds\times dy)=\sum_{n,T_n\in[0,t]}f(T_n,Y_n)
{{</equation>}}
となり，$\mathcal{F}_t$-適合な確率過程が得られる．

[^1]: Poisson分布の性質 2.と3.で非連続点が確率 $1$ で存在すると言っているのに，ここでは確率 $1$ で連続と言っているのは，非連続点の測度が $0$ となるためである．
[^2]: 実は命題3の証明で詳細は示されることである．