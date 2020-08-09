---
title: "Radon-Nikodymの定理のまとめ"
tags: ["測度論", "確率論"]
date: 2020-01-23T10:00:00+09:00
draft: false
---
過去にメモしたRadon-Nikodymの定理の証明まとめ．
[Capinski and Kopp「Measure, Integral and Probability」](https://www.springer.com/gp/book/9781852337810)を元に記載しました．

可測空間$(\Omega,\mathcal{F})$上の$F\in\mathcal{F}$に対する測度$\nu(F)$が
{{<equation>}}
F\mapsto\nu(F)=\int_Ffd\mu
{{</equation>}}
となるような$f$を見つける問題．

## 用語
$\nu$と$\mu$はともに可測空間$(\Omega,\mathcal{F})$上の測度とする．
- **絶対連続(absolutely continuous)**\
任意の$F\in\mathcal{F}$に対して$\mu(F)=0$ならば$\nu(F)=0$が成り立つならば，$\nu$は$\mu$に対して**絶対連続**であるといい，$\nu<<\mu$と表す．

- **押さえる(dominate)**\
任意の$F\in\mathcal{F}$に対して$0\le\nu(F)\le\mu(F)$が成り立つとき，$\mu$は$\nu$を**押さえる**という．

- **分割(partition)**\
$\mathcal{F}$内の有限な排反部分集合の集まり$\mathcal{P}=(F_i)_{i\le n}$で$\cup_iF_i=\Omega$をみたすものを，(有限可測な)$\Omega$の**分割**と呼ぶ．

- **細分(refinement)**\
2つの分割$\mathcal{P},\mathcal{P'}$について，任意の$\mathcal{P}$の要素が$\mathcal{P'}$の排反な要素の和集合で表されるとき，$\mathcal{P'}$は$\mathcal{P}$の**細分**と呼ぶ．

- **$\sigma$-有限($\sigma$-finite)**\
$\cup_iF_i=\Omega$をみたす$\mathcal{F}$-可測な集合列$(F_i)_{i\ge0}$が存在して，各$i$について$\nu(F_i)$が有限の値をとるとき，$\nu$を**$\sigma$-有限**な測度と呼ぶ．

## 証明
Radon-Nikodymの定理の証明をするときに，以下の補助定理を使うと便利なので，事前に証明しておきます．
Radon-Nikodymの定理との違いは
- 2つの測度が$\sigma$-有限ではなく，一方がもう片方を押さえているという仮定になっている．
- 押さえている方の測度$\mu$が全測度で1となる($\mu(\Omega)=1$)．
という2点．ただし，結論の形はRadon-Nikodymの定理と同様なのでその雰囲気は掴んでもらえるはず．

**補助定理**\
任意の$F\in\mathcal{F}$に対して，$\mu(\Omega)=1,0\le\nu(F)\le\mu(F)$が成り立つ，つまり$\mu$は$\nu$を押さえる測度とする．
このとき，任意の$F\in\mathcal{F}$に対して，
{{<equation>}}
\nu(F)=\int_Fhd\mu\tag*{(#1)}\label{eq1}
{{</equation>}}
をみたす，($\Omega$上の)非負$\mathcal{F}$-可測関数$h$が存在する．

## 補助定理の証明
以下のステップで証明する．
1. 分割$\mathcal{P}$に含まれる集合上で$\ref{eq1}$をみたすような$h_\mathcal{P}$を構成する．
ついでに$\mathcal{P}_{n+1}$が$\mathcal{P}_n$を細分するような分割の列$\mathcal{P}_1,\mathcal{P}_2,...$について
{{<equation>}}
\nu(F)=\int_\Omega h^2_{\mathcal{P}_n}d\mu\tag*{(#2)}\label{eq2}
{{</equation>}}
が非減少列になることを確認する．
1. 1.の結果および$\ref{eq2}$で定められる列が上限1をもつことから，収束定理を使って，
$h_{\mathcal{P}_{n}}$の極限として$\ref{eq1}$をみたす$h$を求めることができる．
1. 2.の方法で定めた$h$が望ましい性質を持つことを確認する．

#### 1.の説明
$A_i\in\mathcal{F}$に対して，$\mathcal{P}=\{A_1,A_2,...,A_k\}$を$\Omega$の分割とした上で，
以下の様に$A_i$上ではのっぺりするような関数$h_\mathcal{P}$を定める．
{{<equation>}}
h_\mathcal{P}=\begin{cases}
    c_i=\dfrac{\nu(A_i)}{\mu(A_i)},\omega\in A_i & \mu(A_i)>0\\
    0&\text{otherwise}\\
    \end{cases}
{{</equation>}}
補助定理の仮定から任意の$F\in\mathcal{F}$に対して$\mu(\Omega)=1,0\le\nu(F)\le\mu(F)$が成り立っていることに注意すると，
この関数$h_\mathcal{P}$は以下の性質をもつことがわかる．
ただし，$\mathcal{P},\mathcal{P}_1,\mathcal{P}_2$は$\Omega$の分割で$\mathcal{P}_2$は$\mathcal{P}_1$の細分であるとする．
<ol type="a"><li>
    $A_i$上では
    {{<equation>}}
    \nu(A_i)=\int_{A_i}h_{\mathcal{P}}d\mu.
    {{</equation>}}
</li><li>任意の$\omega\in\Omega$に対して$0\le h_{\mathcal{P}}\le1$．
</li><li>インデックス集合$J\subset\{1,2,...,k\}$について$A=\cup_{j\in J}A_j$と表すとき，
    {{<equation>}}
    \nu(A)=\int_{A}h_{\mathcal{P}}d\mu
    {{</equation>}}
    が成り立つ．ゆえに
    {{<equation>}}
    \nu(\Omega)=\int_{\Omega}h_{\mathcal{P}}d\mu
    {{</equation>}}
    もいえる．
</li><li>次が成り立つ．
    <ol type="i"><li>任意の$A\in\mathcal{P}_1$に対して，
    {{<equation>}}
    \int_{A}h_{\mathcal{P}_1}d\mu=\nu(A)=\int_{A}h_{\mathcal{P}_2}d\mu.
    {{</equation>}}
    </li><li>任意の$A\in\mathcal{P}_1$に対して，
    {{<equation>}}
    \int_{A}h_{\mathcal{P}_1}h_{\mathcal{P}_2}d\mu=\int_{A}h^2_{\mathcal{P}_1}d\mu.
    {{</equation>}}
    </li></ol>
</li><li>次が成り立つ
    {{<equation>}}
    \int_{A}(h^2_{\mathcal{P}_1}-h^2_{\mathcal{P}_2})d\mu=\int_{A}(h_{\mathcal{P}_1}-h_{\mathcal{P}_2})^2d\mu.
    {{</equation>}}
    ゆえに次も成り立つ．
    {{<equation>}}
    \int_{A}h^2_{\mathcal{P}_2}d\mu=\int_Ah^2_{\mathcal{P}_1}d\mu+\int_{A}(h_{\mathcal{P}_1}-h_{\mathcal{P}_2})^2d\mu\ge\int_Ah^2_{\mathcal{P}_1}d\mu.
    {{</equation>}}
    これから細分されていく分割の列$\mathcal{P}_1,\mathcal{P}_2,...$に対して$\int_Ah^2_{\mathcal{P}_n}d\mu$は非減少列となることがわかる．
</li></ol>
これらの証明は後にすることにして，まずは補助定理の証明を進める．

#### 2.の証明
すべての分割をとったときの上限として
{{<equation>}}
c=\sup_n\int_\Omega h^2_{\mathcal{P}_n}d\mu
{{</equation>}}
を定めておく．
また，分割$\mathcal{P}_n,n\ge 1$として
{{<equation>}}
\int_\Omega h^2_{\mathcal{P}_n}d\mu>c-\frac{1}{4^n}
{{</equation>}}
をみたすものをとる($\sup$の性質からとることができる)．
さらに$n$個の分割$\mathcal{P}_1,\mathcal{P}_2,...,\mathcal{P}_n$の中に共通する最も細分された分割を$\mathcal{Q}_n$と表すと，
- $\mathcal{Q}_n$は$\mathcal{P}_n$の細分となる．
- $\mathcal{Q}_{n+1}$は$\mathcal{Q}_n$の細分となっている．

上記に注意し，1.の結果と合わせると，次が成り立つ.
{{<equation>}}
c-\frac{1}{4^n}<\int_\Omega h^2_{\mathcal{P}_n}d\mu\le\int_\Omega h^2_{\mathcal{Q}_n}d\mu\le\int_\Omega h^2_{\mathcal{Q}_{n+1}}d\mu\le c
{{</equation>}}

1.にあげた性質のうち，e.を用いれば，
{{<equation>}}
\int_{A}(h_{\mathcal{Q}_{n+1}}-h_{\mathcal{Q}_n})^2d\mu=\int_{A}(h^2_{\mathcal{Q}_{n+1}}-h^2_{\mathcal{Q}_n})d\mu<\frac{1}{4^n}
{{</equation>}}
が成り立つことがわかり，Schwarzの不等式を$f=|h_{\mathcal{Q}_{n+1}}-h_{\mathcal{Q}_n}|$および$g=1$に適用すれば
{{<equation>}}
\int_{A}|h_{\mathcal{Q}_{n+1}}-h_{\mathcal{Q}_n}|d\mu
    \le\sqrt{\int_{A}|h_{\mathcal{Q}_{n+1}}-h_{\mathcal{Q}_n}|^2d\mu}
    <\sqrt{\frac{1}{4^n}}<\sqrt{\frac{1}{2^n}}
{{</equation>}}
が成り立つことがわかる．
したがって，$\sum_{n\ge1}\int_{A}|h_{\mathcal{Q}_{n+1}}-h_{\mathcal{Q}_n}|d\mu$が有限であることから，
Beppo-Leviの定理により関数列$h_{\mathcal{Q}_n}$は$\mu$-a.e.で収束する．
したがって極限関数
{{<equation>}}
h=h_{\mathcal{P}_1}+\sum_{n\ge1}(h_{\mathcal{Q}_{n+1}}-h_{\mathcal{Q}_n})=\lim_n h_{\mathcal{Q}_n}
{{</equation>}}
も$\mu$-a.e.でwell-definedとなる．$h$の構成としては$\mu$-零集合上では$h=0$として終了である．


#### 3.の証明
ほしい性質は以下の3つ
- $0\le h(\omega) \le 1$
- $h$は$\mathcal{F}$-可測
- 任意の$F\in\mathcal{F}$に対して$\nu(F)=\int_Fhd\mu$が成り立つ．

このうち3つめの性質のみ明らかではないので証明する．
$\mathcal{F}$-可測な集合$F$を1つ固定し，
分割$\mathcal{Q}_n,n\ge1$と$\{F,F^c\}$に共通する最も細分された分割を$\mathcal{R}_n$とする．
$F$は有限排反な$\mathcal{R}_n$の集合の和集合で表されるので，1.にあげた性質のうちc.により

{{<equation>}}
\nu(F)=\int_Fh_{\mathcal{R}_n}d\mu
{{</equation>}}
が成り立つ．
2.の議論と同様にして
{{<equation>}}
c-\frac{1}{4^n}<\int_\Omega h^2_{\mathcal{Q}_n}d\mu\le\int_\Omega h^2_{\mathcal{R}_n}d\mu\le c
{{</equation>}}
が成り立つので
{{<equation>}}
\int_{A}(h_{\mathcal{R}_n}-h_{\mathcal{Q}_n})^2d\mu<\frac{1}{4^n}
{{</equation>}}
がわかる．したがって，Schwarzの不等式で$g=1_F$とすれば，
{{<equation>}}
\left|\int_{A}(h_{\mathcal{R}_n}-h_{\mathcal{Q}_n})d\mu\right|\le\int_{A}\left|h_{\mathcal{R}_n}-h_{\mathcal{Q}_n}\right|d\mu<\frac{1}{2^n}
{{</equation>}}
が得られる．こらから，$n\ge1$を固定すれば
{{<equation>}}
\nu(F)=\int_Fh_{\mathcal{R}_n}d\mu=\int_{A}(h_{\mathcal{R}_n}-h_{\mathcal{Q}_n})d\mu+\int_Fh_{\mathcal{Q}_n}d\mu
{{</equation>}}
が得られる．最右辺の最初の積分は上記の積分の評価から$n\rightarrow\infty$とすれば，$0$に収束する．
最右辺の二項目の積分は，任意の$n\ge 1$に対して$0\le h_{\mathcal{R}_n}$であり，$\mu(\Omega)$が有限であることから，
有界収束定理を使うことができ，$\int_Fhd\mu$に収束することがわかる．

#### 1.の証明

## Radon-Nikodymの定理の証明



