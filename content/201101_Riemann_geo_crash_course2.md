---
title: "リーマン幾何のcrash course"
tags: ["微分幾何"]
date: 2020-11-01T10:00:00+09:00
draft: false
---
[岡部洋一「リーマン幾何学と相対性理論」](http://www.moge.org/okabe/temp/Riemann.pdf)の内容を整理しながら，リーマン幾何学に関する内容をダイジェストでまとめます．

<!--
### 内容
- [平行移動と接続係数](#001)
- [共変微分](#002)
-->

<a id="markdown-001" name="001"></a>

### 平行移動と接続係数
　下図のとおり，平面上の点 $O$ で定義されたベクトル $A(O)$ の点 $P$ への平行移動を考える．
<div align="center">
{{< figure src="/image/20201112_riemann_parallel_1.png" class="center" >}}
ベクトル $A(O)$ の点 $O$ から点 $P$ への平行移動
</div>
ベクトル $A(O)$ を点 $P$ 上にコピーし，その曲線座標系への射影を $A_{||}(O\rightarrow P)$ と定め，これをもって
このベクトル $A_{||}$ は元の $A$ とは異なり，その差を $A_{\bot}(O\rightarrow P)$ と表すと
{{<equation>}}
A(O) &= A_{||}(O\rightarrow P) + A_{\bot}(O\rightarrow P)
{{</equation>}}
という関係式が成り立つ．
$A_{||}$ が対象とする曲線座標系の中のベクトルであり，$A_\bot$ がその座標系からはみ出すベクトルである.
これに基づいて，その曲線座標系の基底を $\boldsymbol{e}_m$ または $\boldsymbol{e}^m$ としたとき，
{{<equation>}}
A_\bot(O\rightarrow P)\cdot\boldsymbol{e}_m&=0\\
A_\bot(O\rightarrow P)\cdot\boldsymbol{e}^m&=0
{{</equation>}}
がすべての $m$ について成り立っているとき，$A_{||}$ を平行移動されたベクトルと呼ぶこととする．
すなわち，平行移動とは元のベクトルをわずかに離れた位置にコピーしたベクトルの射影であると言える．


#### 基底の平行移動
　平行移動した基底と，その場所における基底の関係を式で調べてみよう．
以下では上記の座標系で表す平行移動を考え，基底 $\boldsymbol{e}_m(\boldsymbol{x}+d\boldsymbol{x})$ を　$\boldsymbol{x}+d\boldsymbol{x}$ から $\boldsymbol{x}$ へ平行移動する場合を考える．

{{<equation>}}
\boldsymbol{e}_　m(\boldsymbol{x}+d\boldsymbol{x}) &= \boldsymbol{e}_　{||m}(\boldsymbol{x}+d\boldsymbol{x}\rightarrow\boldsymbol{x}) + \boldsymbol{e}_{\bot m}(\boldsymbol{x}+d\boldsymbol{x}\rightarrow\boldsymbol{x})
\tag*{(#1)}\label{parallel1}
{{</equation>}}
ここで$\boldsymbol{e}_　{||m}$ は平行移動したベクトル， $\boldsymbol{e}_　{\bot m}$ は平行移動したベクトルと元のベクトルとの差を表す．

　$\boldsymbol{e}_　{||m}$ は基底 $\boldsymbol{e}_ m$ とは若干のずれがあるが，移動量が小さいとき，そのずれは移動量に比例して大きくなるので，$\boldsymbol{x}$ における基底で展開して，一次の微小量まで書くと次式のようになる．
{{<equation>}}
\boldsymbol{e}_　{||m}(\boldsymbol{x}+d\boldsymbol{x}\rightarrow\boldsymbol{x})
&= \boldsymbol{e}_ m(\boldsymbol{x}) + dx^k\Gamma_{k\ m}^{\ n}(\boldsymbol{x})\boldsymbol{e}_n(\boldsymbol{x})
\tag*{(#2)}\label{parallel2}
{{</equation>}}
移動量に比例する項として第二項があり，基底によって変化量が変わることを反映して，係数が $\Gamma_{k\ m}^{\ n}(\boldsymbol{x})\boldsymbol{e}_n$ となっている．比例係数 $\Gamma_{k\ m}^{\ n}(\boldsymbol{x})$ は局所的なアフィン変換をつないでいく係数という意味で，接続係数と呼ばれる．

$\ref{parallel2}$ を $\ref{parallel1}$ に代入すると，
{{<equation>}}
\boldsymbol{e}_ m(\boldsymbol{x}+d\boldsymbol{x})-\boldsymbol{e}_ m(\boldsymbol{x})
=dx^k\dfrac{\partial}{\partial x^k}\boldsymbol{e}_ m (\boldsymbol{x})
=dx^k\partial_ k\boldsymbol{e}_ m (\boldsymbol{x})
{{</equation>}}
より
{{<equation>}}
dx^k\partial_ k\boldsymbol{e}_ m (\boldsymbol{x})
=dx^k\Gamma_{k\ m}^{\ n}(\boldsymbol{x})\boldsymbol{e}_n(\boldsymbol{x})
 +\boldsymbol{e}_{\bot m}(\boldsymbol{x}+d\boldsymbol{x}\rightarrow\boldsymbol{x})
{{</equation>}}
両辺に $\boldsymbol{e}^n(\boldsymbol{x})$ をかけると
{{<equation>}}
\boldsymbol{e}^n(\boldsymbol{x})\cdot dx^k\partial_ k\boldsymbol{e}_ m (\boldsymbol{x})
&= \boldsymbol{e}^n(\boldsymbol{x})\cdot dx^k\Gamma_{k\ m}^{\ n}(\boldsymbol{x})\boldsymbol{e}_n(\boldsymbol{x})
  + \boldsymbol{e}^n(\boldsymbol{x})\cdot \boldsymbol{e}_{\bot m}(\boldsymbol{x}+d\boldsymbol{x}\rightarrow\boldsymbol{x})\\
dx^k\boldsymbol{e}^n(\boldsymbol{x})\cdot\partial_ k\boldsymbol{e}_ m (\boldsymbol{x})
&= dx^k\Gamma_{k\ m}^{\ n}(\boldsymbol{x})\boldsymbol{e}^n(\boldsymbol{x})\cdot\boldsymbol{e}_n(\boldsymbol{x})
  + 0\\
dx^k\boldsymbol{e}^n(\boldsymbol{x})\cdot\partial_ k\boldsymbol{e}_ m (\boldsymbol{x})
&= dx^k\Gamma_{k\ m}^{\ n}(\boldsymbol{x})\delta_n^n(\boldsymbol{x})
{{</equation>}}
と計算することができ，$dx^k$ の係数を比較すると
{{<equation>}}
\Gamma_{k\ m}^{\ n}(\boldsymbol{x})=\boldsymbol{e}^n(\boldsymbol{x})\cdot\partial_ k\boldsymbol{e}_ m (\boldsymbol{x})
\tag*{(#3)}\label{parallel3}
{{</equation>}}
が得られる．

この形式の微分を扱う効用としては，次式で与えられる基底の全微分
{{<equation>}}
d\boldsymbol{e}_ m(\boldsymbol{x})
&= \boldsymbol{e}_ m(\boldsymbol{x}+d\boldsymbol{x}) - \boldsymbol{e}_ m(\boldsymbol{x})
= dx^k\partial_k\boldsymbol{e}_ m(\boldsymbol{x})
{{</equation>}}
では，対象としている空間を飛び出してしまうため({$\boldsymbol{e}_ m$}) 表現できず， 同じ空間内で処理できなくなってしまう．
そのため，平行移動した基底 $\boldsymbol{e}_ {||m}$ を用意しておき，
{{<equation>}}
\delta\boldsymbol{e}_m(\boldsymbol{x})
&= \boldsymbol{e}_ {||m}(\boldsymbol{x}+d\boldsymbol{x}\rightarrow\boldsymbol{x}) - \boldsymbol{e}_ m(\boldsymbol{x})
= dx^k\Gamma_{k\ m}^{\ n}(\boldsymbol{x})\boldsymbol{e}_n(\boldsymbol{x})
{{</equation>}}
とすれば，({$\boldsymbol{e}_ m$}) で表現することができる．


#### 計量テンソルと接続係数

$\ref{parallel3}$ の両辺に $g_{nl}$ をかけて降階すると
{{<equation>}}
g_{nl}\Gamma_{k\ m}^{\ n}(\boldsymbol{x})=g_{nl}\boldsymbol{e}^n(\boldsymbol{x})\cdot\partial_ k\boldsymbol{e}_ m (\boldsymbol{x})=\boldsymbol{e}_ l(\boldsymbol{x})\cdot\partial_ k\boldsymbol{e}_ m (\boldsymbol{x})
{{</equation>}}
この式を用いて，次の3式が得られる．
{{<equation>}}
\partial_ kg_ {ml}&=\partial_ k(\boldsymbol{e}_ m\cdot\boldsymbol{e}_ l)=\partial_ k\boldsymbol{e}_ m\cdot\boldsymbol{e}_ l+\boldsymbol{e}_ m\cdot\partial_ k\boldsymbol{e}_ l=g_ {nl} \Gamma_ {k\ m}^{\ n}+g_ {nm} \Gamma_ {k\ l}^{\ n}\tag*{(#4-1)}\label{metric_eq4-1}\\
\partial_mg_{lk}&=\partial_ m(\boldsymbol{e}_ l\cdot\boldsymbol{e}_ k)=\partial_ m\boldsymbol{e}_ l\cdot\boldsymbol{e}_ k+\boldsymbol{e}_ l\cdot\partial_ m\boldsymbol{e}_ k=g_ {nk} \Gamma_ {m\ l}^{\ n}+g_ {nl} \Gamma_ {m\ k}^{\ n}\tag*{(#4-2)}\label{metric_eq4-2}\\
\partial_lg_{km}&=\partial_ l(\boldsymbol{e}_ k\cdot\boldsymbol{e}_ m)=\partial_ l\boldsymbol{e}_ k\cdot\boldsymbol{e}_ m+\boldsymbol{e}_ k\cdot\partial_ l\boldsymbol{e}_ m=g_ {nm} \Gamma_ {l\ k}^{\ n}+g_ {nk} \Gamma_ {l\ m}^{\ n}\tag*{(#4-3)}\label{metric_eq4-3}\\
{{</equation>}}
$\ref{metric_eq4-1}+\ref{metric_eq4-2}-\ref{metric_eq4-3}$ を計算し，左右を入れ替えると
{{<equation>}}
2g_{nl}\Gamma_ {k\ m}^{\ n}=\partial_ kg_ {ml} + \partial_ mg_ {lk} + \partial_ lg_ {km}
{{</equation>}}
となる．両辺2で割ると次式が得られる．
{{<equation>}}
\Gamma_ {km,n}=g_{nl}\Gamma_ {k\ m}^{\ n}=\dfrac{1}{2}\left(\partial_ kg_ {ml} + \partial_ mg_ {lk} + \partial_ lg_ {km}\right)
{{</equation>}}

<!-- 
#### 双対基底の位置変化
-->

<a id="markdown-002" name="002"></a>

### 共変微分



<!--
<a id="markdown-003" name="003"></a>

### リーマン接続
-->
