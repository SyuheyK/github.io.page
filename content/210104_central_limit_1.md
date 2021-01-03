---
title: "中心極限定理の証明① "
tags: ["確率論"]
date: 2021-01-03T10:00:00+09:00
draft: false
---
中心極限定理の証明をまとめます．
こちらでは[Levyの定理](https://en.wikipedia.org/wiki/L%C3%A9vy%27s_continuity_theorem)を所与として，[Lindeberg-Fellerの定理](https://en.wikipedia.org/wiki/Lindeberg%27s_condition#Feller's_theorem)を元に[中心極限定理](https://en.wikipedia.org/wiki/Central_limit_theorem#Classical_CLT)を示す．
本稿は[Capinski, Marek, Kopp, Peter E., Measure, Integral and Probability, Springer, 2004](https://www.springer.com/jp/book/9781852337810)を参考に記載する．

確率変数列 $X_n$ に関する記号を以下のようにする．
- $m_n=\mathrm{E}(X_n)$
- $\sigma^2_n=\mathrm{Var}(X_n)$
- $S_n=\sum_{k=1}^nX_k$
- $\sigma_n^2=\mathrm{Var}(S_n)$
- $T_n=(S_n)-\mathrm{E}(S_n)) / c_n$ 

### Lindeberg-Fellerの定理
確率変数列 $X_n$ が各 $n$ に対して $\mathrm{E}(X_n)<\infty, \mathrm{Var}(X_n)<\infty$ をみたし，
ある$\varepsilon>0$ に対して
{{<equation>}}
  \dfrac{1}{c_n}\sum_{k=1}^n\int_{\{x\left||x-m_k|\ge\varepsilon c_n\right.\}}(x-m_k)^2\mathrm{d}P_X(x)\rightarrow 0\text{ as }n\rightarrow\infty\tag*{(C1)}\label{lf_clt_condition1}
{{</equation>}}
が成り立つとき，$P_{T_n}$ は正規分布に弱収束する．

---


### 証明
次の定理が成り立つ前提のもと証明する．

**Levyの定理**  
$\varphi_ n$ を測度 $P_n$ の特性関数とする．
$\varphi_n\rightarrow\varphi$が成り立ち，$\varphi$ は $0$ 点で連続な関数とすると，
$\varphi$ は測度 $P$ の特性関数であり，$P_n$ は $P$ に弱収束する．

---

Levyの定理を使えば，
{{<equation>}}
  \varphi_{T_n}(u)\rightarrow\mathrm{e}^{-\frac{1}{2}u^2}\tag*{($\ast$1)}
{{</equation>}}
を示せば十分である．これを計算すると
{{<equation>}}
  \varphi_{T_n}(u)
    &= \mathrm{E}(\mathrm{e}^{-\mathrm{i}uT_n})\\
    &= \mathrm{E}(\mathrm{e}^{-\mathrm{i}\frac{u}{c_n}\sum_ {k=1}^nX_k})\\
    &= \mathrm{E}\left(\prod_ {k=1}^n\mathrm{e}^{-\mathrm{i}\frac{u}{c_ n}X_k}\right)\\
    &= \prod_ {k=1}^n\mathrm{E}\left(\mathrm{e}^{-\mathrm{i}\frac{u}{c_ n}X_k}\right)\\
    &= \prod_ {k=1}^n\varphi_{X_ k}\left(\dfrac{u}{c_ n}\right)
{{</equation>}}
となる．したがって，示すべき式は
{{<equation>}}
  \log\prod_{k=1}^n\varphi_{X_k}\left(\dfrac{u}{c_n}\right)\rightarrow -\frac{1}{2}u^2\tag*{($\ast$2)}
{{</equation>}}
となるが，これを書き換えると
{{<equation>}}
  \left|\log\prod_{k=1}^n\varphi_{X_k}\left(\dfrac{u}{c_n}\right)+\dfrac{1}{2}u^2\right|\rightarrow0\text{ as }n\rightarrow\infty\tag*{($\ast$3)}\label{lfclt_stateq1}
{{</equation>}}
となる．

以下，以下の流れで証明する．
- 特性関数 $\varphi_ {X_k}(u)$ を書き換える．
- 式 $\ref{lfclt_stateq1}$ を書き換える．
- 収束性を示す．

#### 特性関数の書き換え
表記の簡単化のために以下の変数を定義する．
{{<equation>}}
  \alpha_{nk}
    &=\int_ {|x|\ge\varepsilon c_ n}x^2\mathrm{d}P_ {X_ k}(x)\\
  \beta_{nk}
    &=\int_ {|x|<\varepsilon c_ n}x^2\mathrm{d}P_ {X_ k}(x)
{{</equation>}}
$\beta_{nk}$ について，積分区間の条件式を二乗することで
{{<equation>}}
  \beta_{nk}
    &=\int_ {|x|<\varepsilon c_ n}x^2\mathrm{d}P_ {X_k}(x)
    =\int_ {x^2<\varepsilon^2c_ n^2}x^2\mathrm{d}P_ {X_k}(x)
    \le\int_ {x^2<\varepsilon^2c_ n^2}\varepsilon^2c_ n^2\mathrm{d}P_ {X_k}(x)
    =\varepsilon^2c_ n^2
{{</equation>}}
と計算でき，$\beta_{nk}\le\varepsilon^2c_ n^2$ がわかる．
なお，不等式に等号もついているのは $\{x^2<\varepsilon^2c_ n^2\}$ が零集合の場合を考慮したためである．
定理の条件式 $\ref{lf_clt_condition1}$ はこの変数を使うと，
{{<equation>}}
  \sum_ {k=1}^n\dfrac{1}{c_ n^2}\alpha_ {nk}\rightarrow0\text{ as }n\rightarrow\infty\tag*{(#1)}\label{lf_clt_limit1}
{{</equation>}}
と書き換えることができるが，
{{<equation>}}
  \sum_{k=1}^n\left(\alpha_{nk}+\beta_{nk}\right)
    =\sum_{k=1}^n\int x^2\mathrm{d}P_{X_n}(x)
    =\sum_{k=1}^n\mathrm{Var}(X_k)
    =c_n^2
{{</equation>}}
となることから，上式を両辺 $c_n$ で除して
{{<equation>}}
  \sum_ {k=1}^n\dfrac{1}{c_ n^2}\beta_ {nk}\rightarrow1\text{ as }n\rightarrow\infty\tag*{(#2)}\label{lf_clt_limit2}
{{</equation>}}
をみたすことがわかる．
被積分関数の形から，$\alpha_{nk},\beta_{nk}$ はともに正値なので，最後の級数の収束は単調増加である．
また，これらの式は任意の $\varepsilon>0$ に対してなりたつ．

これらを使って $\varphi_ {X_k}(u)$ を書き換える．任意の $\varepsilon>0$ に対して
{{<equation>}}
  \varphi_ {X_k}(u)
    &=\int_ {|x|\ge\varepsilon c_n}\mathrm{e}^{\mathrm{i}ux}\mathrm{d}P_ {X_ k}(x)
    +\int_ {|x|<\varepsilon c_ n}\mathrm{e}^{\mathrm{i}ux}\mathrm{d}P_ {X_ k}(x)
{{</equation>}}
と $\varphi_ {X_k}(u)$ を分解し，右辺第一項と第二項をそれぞれ，複素関数に対するTaylor展開:
{{<equation>}}
  \mathrm{e}^{\mathrm{i}y}&=1+\mathrm{i}y+\dfrac{1}{2}\theta_2y^2\text{ for some }\theta_2\text{ with }|\theta_2|<\infty,\\
  \mathrm{e}^{\mathrm{i}y}&=1+\mathrm{i}y-\dfrac{1}{2}y^2+\dfrac{1}{6}\theta_3|y|^3\text{ for some }\theta_3\text{ with }|\theta_3|<\infty
{{</equation>}}
を用いて書き換えると
{{<equation>}}
  \varphi_ {X_k}(u)
    &=\int_ {|x|\ge\varepsilon c_n}\left(1+\mathrm{i}ux+\dfrac{1}{2}\theta_2u^2x^2\right)\mathrm{d}P_ {X_ k}(x)\\
    &\quad +\int_ {|x|<\varepsilon c_ n}\left(1+\mathrm{i}ux-\dfrac{1}{2}u^2x^2+\dfrac{1}{6}\theta_3|u|^3|x^3|\right)\mathrm{d}P_ {X_ k}(x)\\
    &=1+\dfrac{1}{2}u^2\int_ {|x|\ge\varepsilon c_n}\theta_2x^2\mathrm{d}P_ {X_ k}(x)-\dfrac{1}{2}u^2\int_ {|x|<\varepsilon c_ n}x^2\mathrm{d}P_ {X_ k}(x)\\
    &\quad +\dfrac{1}{6}|u|^3\int_ {|x|<\varepsilon c_ n}\theta_3|x|^3\mathrm{d}P_ {X_ k}(x)\tag*{(#3)}\label{lfclt_cf}
{{</equation>}}
となる．

#### 式(*3) を押さえる評価式
式 $\ref{lfclt_cf}$ の最右辺の各項について検討を進めると，まず第二項については$|\theta_ 2|<1$ より
{{<equation>}}
  \left|\int_ {|x|\ge\varepsilon c_n}\theta_ 2x^2\mathrm{d}P_ {X_ k}(x)\right|
    &\le\int_ {|x|\ge\varepsilon c_n}\left|\theta_ 2x^2\right|\mathrm{d}P_ {X_ k}(x)
    \le\int_ {|x|\ge\varepsilon c_ n}x^2\mathrm{d}P_ {X_ k}(x)
{{</equation>}}
となることから，$|\theta'_ 2|<1$ をみたす $\theta'_ 2$ が存在して，
{{<equation>}}
  \int_ {|x|\ge\varepsilon c_ n}\theta_ 2x^2\mathrm{d}P_ {X_ k}(x)
  =\theta'_ 2\int_ {|x|\ge\varepsilon c_n}x^2\mathrm{d}P_ {X_ k}(x)
  =\theta'_ 2\alpha_ {nk}
{{</equation>}}
が得られる．

同様に式 $\ref{lfclt_cf}$ の最右辺の第三項については$|\theta_3|<1$ より
{{<equation>}}
  \left|\int_ {|x|<\varepsilon c_ n}\theta_3|x|^3\mathrm{d}P_ {X_ k}(x)\right|
    &\le\int_ {|x|<\varepsilon c_ n}\left|\theta_3|x|^3\right|\mathrm{d}P_ {X_ k}(x)
    \le\int_ {|x|<\varepsilon c_ n}\varepsilon c_ nx^2\mathrm{d}P_ {X_ k}(x)
{{</equation>}}
となることから，$|\theta'_ 3|<1$ をみたす $\theta'_ 3$ が存在して，
{{<equation>}}
  \int_ {|x|<\varepsilon c_ n}\theta_3|x|^3\mathrm{d}P_ {X_ k}(x)
  =\theta'_ 3\int_ {|x|<\varepsilon c_ n}\varepsilon c_ nx^2\mathrm{d}P_ {X_ k}(x)
  =\theta'_ 3\varepsilon c_ n\beta_{nk}
{{</equation>}}

これらを式 $\ref{lfclt_cf}$ に代入すると
{{<equation>}}
  \varphi_ {X_k}(u)=1 + \dfrac{1}{2}u^2\theta'_ 2\alpha_ {nk} - \dfrac{1}{2}u^2\beta_{nk} + \dfrac{1}{6}|u|^3\theta'_ 3\varepsilon c_ n\beta_{nk}
{{</equation>}}
となる．
ここで，$u$ に $u/c_ n$ を代入すると
{{<equation>}}
  \varphi_ {X_k}\left(\dfrac{u}{c_ n}\right)=1 + \dfrac{1}{2}\left(\dfrac{u}{c_ n}\right)^2\theta'_ 2\alpha_ {nk} - \dfrac{1}{2}\left(\dfrac{u}{c_ n}\right)^2\beta_{nk} + \dfrac{1}{6}|u|^3\theta'_ 3\varepsilon \dfrac{1}{c_ n^2}\beta_{nk}
{{</equation>}}
となるが，表記の簡単のため，
{{<equation>}}
  \gamma_{nk} = \dfrac{1}{2}\left(\dfrac{u}{c_ n}\right)^2\theta'_ 2\alpha_ {nk} - \dfrac{1}{2}\left(\dfrac{u}{c_ n}\right)^2\beta_{nk} + \dfrac{1}{6}|u|^3\theta'_ 3\varepsilon \dfrac{1}{c_ n^2}\beta_{nk}
{{</equation>}}
とおけば，
{{<equation>}}
  \varphi_ {X_k}\left(\dfrac{u}{c_ n}\right)=1+\gamma_{nk}
{{</equation>}}
となる．$\gamma_{nk}$ の収束性については $\ref{lf_clt_limit1}$ と $\ref{lf_clt_limit2}$ から
{{<equation>}}
  \sum_{k=1}^n\gamma_{nk}\rightarrow- \dfrac{1}{2}\left(\dfrac{u}{c_ n}\right)^2 + \dfrac{1}{6}|u|^3\theta'_ 3\varepsilon \dfrac{1}{c_ n^2}
{{</equation>}}
がなりたつ．

$\ref{lfclt_stateq1}$ の評価式に話を戻すと，複素関数に対するTaylor展開:
{{<equation>}}
  \log(1+z)=z+\theta_1|z|^2\text{ for some }\theta_1\text{ with }|\theta_1|<1
{{</equation>}}
より，
{{<equation>}}
  \log\prod_{k=1}^n\varphi_{X_n}\left(\dfrac{u}{c_ n}\right)=\sum_{k=1}^n\log\varphi_{X_n}\left(\dfrac{u}{c_ n}\right)=\sum_{k=1}^n\left(\gamma_{nk}+\theta_1|\gamma_{nk}|^2\right)
{{</equation>}}
となるので，示すべき式は
{{<equation>}}
  \left|\log\prod_{k=1}^n\varphi_{X_n}\left(\dfrac{u}{c_ n}\right)+\dfrac{1}{2}u^2\right|
  =\left|\sum_{k=1}^n\left(\gamma_{nk}+\theta_1|\gamma_{nk}|^2\right)+\dfrac{1}{2}u^2\right|
  \rightarrow0\text{ as }n\rightarrow\infty\tag*{($\ast$4)}\label{lfclt_stateq2}
{{</equation>}}
となる．

#### 収束性の証明
任意の$\delta>0$ に対して $u$ を固定すると，$\ref{lfclt_stateq2}$ は
{{<equation>}}
  \left|\sum_{k=1}^n\left(\gamma_{nk}+\theta_1|\gamma_{nk}|^2\right)+\dfrac{1}{2}u^2\right|
  &\le\left|\sum_{k=1}^n\gamma_{nk}+\dfrac{1}{2}u^2-\dfrac{1}{6}|u|^3\theta'_3\varepsilon+\dfrac{1}{6}|u|^3\theta'_3\varepsilon\right|+|\theta_1|\sum_{k=1}^n|\gamma_{nk}|^2\\
  &\le\left|\sum_{k=1}^n\gamma_{nk}+\dfrac{1}{2}u^2-\dfrac{1}{6}|u|^3\theta'_3\varepsilon\right|+|\theta_1|\sum_{k=1}^n|\gamma_{nk}|^2+\left|u\right|^3\varepsilon\left|\theta'_3\right|
{{</equation>}}
となる．

### 中心極限定理
