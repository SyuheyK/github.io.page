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

### 共変微分
ここに概説を書く
- 平行移動
- 基底の平行移動
- ベクトル場に対する共変微分

#### 平行移動
　下図のとおり，平面上の点 $O$ で定義されたベクトル $A(O)$ の点 $P$ への平行移動を考える．
<div align="center">
{{< figure src="/image/20201112_riemann_parallel_1.png" class="center" width="500" >}}
ベクトル $A(O)$ の点 $O$ から点 $P$ への平行移動
</div>
ベクトル $A(O)$ を点 $P$ 上にコピーし，その曲線座標系への射影を $A_{||}(O\rightarrow P)$ と定めると，このベクトル $A_{||}$ は元の $A$ とは異なる．
その差を $A_{\bot}(O\rightarrow P)$ と表すと
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
では，対象としている空間を飛び出してしまうため基底 ({$\boldsymbol{e}_ m$}) だけでは微分を表現できず， 同じ空間内で処理できなくなってしまう．
そのため，平行移動した基底 $\boldsymbol{e}_ {||m}$ を用意しておき，
{{<equation>}}
  \delta\boldsymbol{e}_m(\boldsymbol{x})
  &= \boldsymbol{e}_ {||m}(\boldsymbol{x}+d\boldsymbol{x}\rightarrow\boldsymbol{x}) - \boldsymbol{e}_ m(\boldsymbol{x})
  = dx^k\Gamma_{k\ m}^{\ n}(\boldsymbol{x})\boldsymbol{e}_n(\boldsymbol{x})
{{</equation>}}
とすれば，基底 ({$\boldsymbol{e}_ m$}) だけで微分を表現することができる．

<!-- 
#### 双対基底の位置変化
-->

#### ベクトル場に対する共変微分
ベクトル場 $\boldsymbol{A}(\boldsymbol{x})$ の位置変動を調べてみよう．
$\boldsymbol{A}(\boldsymbol{x}+d\boldsymbol{x})$ は考えている空間の次元からはみ出てしまうため，一般のベクトルについても差分ベクトルを
{{<equation>}}
  d\boldsymbol{A}(\boldsymbol{x}) = \boldsymbol{A}(\boldsymbol{x}+d\boldsymbol{x}) - \boldsymbol{A}(\boldsymbol{x})
{{</equation>}}
とするのは問題がある．
そのため，基底の平行移動と同様に $\boldsymbol{A}(\boldsymbol{x}+d\boldsymbol{x})$ を平行移動した $\boldsymbol{A}_ {||}(\boldsymbol{x}+d\boldsymbol{x}\rightarrow\boldsymbol{x})$ を考える．これは次のように展開できる．
{{<equation>}}
  \boldsymbol{A}_ {||}(\boldsymbol{x}+d\boldsymbol{x}\rightarrow\boldsymbol{x})
  &= A_ {||}^m(\boldsymbol{x}+d\boldsymbol{x}\rightarrow\boldsymbol{x})\boldsymbol{e}_ {||m}(\boldsymbol{x}+d\boldsymbol{x}\rightarrow\boldsymbol{x})\\
  &= \left(A^m(\boldsymbol{x}) + dA^m(\boldsymbol{x})\right)\left(\boldsymbol{e}_ m(\boldsymbol{x}) + \delta\boldsymbol{e}_ m(\boldsymbol{x})\right)\\
  &= A^m(\boldsymbol{x})\boldsymbol{e}_ m(\boldsymbol{x}) + dA^m(\boldsymbol{x})\boldsymbol{e}_ m(\boldsymbol{x}) + A^m(\boldsymbol{x})\delta\boldsymbol{e}_ m(\boldsymbol{x})\\
  &= \boldsymbol{A}(\boldsymbol{x}) + dA^m(\boldsymbol{x})\boldsymbol{e}_ m(\boldsymbol{x}) + A^m(\boldsymbol{x})\delta\boldsymbol{e}_ m(\boldsymbol{x}).
{{</equation>}}
これから，$\delta\boldsymbol{A}(\boldsymbol{x})$ を次式で定義し，$\boldsymbol{A}(\boldsymbol{x})$ の完全微分と呼ぶ．
{{<equation>}}
  \delta\boldsymbol{A}(\boldsymbol{x})
  &= \boldsymbol{A}_ {||}(\boldsymbol{x}+d\boldsymbol{x}\rightarrow\boldsymbol{x}) - \boldsymbol{A}(\boldsymbol{x})\\
  &= dA^m(\boldsymbol{x})\boldsymbol{e}_ m(\boldsymbol{x}) + A^m(\boldsymbol{x})\delta\boldsymbol{e}_ m(\boldsymbol{x})\\
  &= dA^m(\boldsymbol{x})\boldsymbol{e}_ m(\boldsymbol{x}) + dx^k\Gamma_ {k\ m}^{\ n}A^m(\boldsymbol{x})\boldsymbol{e}_ m(\boldsymbol{x}).
{{</equation>}}

平行移動の記号は使わなくなるので，以降は引数の $(\boldsymbol{x})$ を省略して記載する．
したがって，$\delta\boldsymbol{A}$ の反変成分 $\delta A^m$ は
{{<equation>}}
  \delta A^m=\delta\boldsymbol{A}\cdot\boldsymbol{e}^m=dA^m+dx^k\Gamma_ {k\ n}^{\ m}A^n
{{</equation>}}
となる．

これを使って，特定の $k$ に対して $dx^k$ だけ増加した際の $\delta A^m/dx^k$ を $\delta A^m/dx^k|_k$ と書くと
{{<equation>}}
  \nabla_kA^m=\left.\dfrac{\delta A^m}{dx^k}\right|_ k = \left.\dfrac{dA^m}{dx^k}\right|_ k + \Gamma_ {k\ n}^{\ m}A^n = \partial_kA^m + \Gamma_ {k\ n}^{\ m}A^n
{{</equation>}}
となり，この$\nabla_k$ を共変微分，$\nabla_kA^m$ を共変微分商とよぶ．

<!--
<a id="markdown-003" name="003"></a>
-->

<a id="markdown-002" name="002"></a>

### 双対基底に関する共変微分
$\Gamma'$ を双対基底における接続係数，双対基底におけるインデックスを $h,i$ で表すと，平行移動した双対基底は
{{<equation>}}
  \boldsymbol{e}_　{||}^h(\boldsymbol{x}+d\boldsymbol{x}\rightarrow\boldsymbol{x})
  &= \boldsymbol{e}^h(\boldsymbol{x}) + dx^k\Gamma_ {k\ i}^{'h}(\boldsymbol{x})\boldsymbol{e}^i(\boldsymbol{x})
{{</equation>}}
となる．$\boldsymbol{e}_　{||}^h\cdot\boldsymbol{e}_　{||m}=\delta^h_m$，$\boldsymbol{e}^i\cdot\boldsymbol{e}_　n=\delta^i_n$に注意しながら，
この式と式 $\ref{parallel2}$ を辺々内積をとると
{{<equation>}}
  \boldsymbol{e}_　{||}^h\cdot\boldsymbol{e}_　{||m}
  &= \left(\boldsymbol{e}^h + dx^k\Gamma_ {k\ i}^{'h}\boldsymbol{e}^i\right)\cdot\left(\boldsymbol{e}_ m + dx^k\Gamma_ {k\ m}^{\ n}\boldsymbol{e}_ n\right)\\
  &= \boldsymbol{e}^h\cdot\boldsymbol{e}_ m + dx^k\Gamma_ {k\ i}^{'\ h}\boldsymbol{e}^i\cdot\boldsymbol{e}_ m + dx^k\Gamma_ {k\ m}^{\ n}\boldsymbol{e}^h\cdot \boldsymbol{e}_ n + dx^k\Gamma_ {k\ i}^{'h}\boldsymbol{e}^i\cdot dx^k\Gamma_ {k\ m}^{\ n}\boldsymbol{e}_ n\\
  &= \delta_m^h + dx^k\Gamma_ {k\ i}^{'h}\delta^i_ m + dx^k\Gamma_ {k\ m}^{\ n}\delta^h_ n 
{{</equation>}}
となる．ここで $m\rightarrow n$，$h\rightarrow m$とすると，
{{<equation>}}
  \delta_ n^m=\delta_ n^m + dx^k\Gamma_ {k\ i}^{'m}\delta^i_ n + dx^k\Gamma_ {k\ n}^{\ i}\delta^m_ i
{{</equation>}}
となるので，結局
{{<equation>}}
  0 = dx^k\Gamma_ {k\ n}^{'m} + dx^k\Gamma_ {k\ n}^{\ m}
{{</equation>}}
となり，$dx^k$ を払うと
{{<equation>}}
  \Gamma_ {k\ n}^{'m} =- \Gamma_ {k\ n}^{\ m}
{{</equation>}}
が得られる．したがって，自然基底の場合と同様に，双対基底に対する完全微分として
{{<equation>}}
  \delta\boldsymbol{e}^m(\boldsymbol{x})
    =\boldsymbol{e}_ {||}^m(\boldsymbol{x}+d\boldsymbol{x}\rightarrow\boldsymbol{x})-\boldsymbol{e}^m(\boldsymbol{x})
    =-dx^k\Gamma_ {k\ n}^{\ m}\boldsymbol{e}^n(\boldsymbol{x})
{{</equation>}}

#### ベクトル場に対する共変微分

{{<equation>}}

{{</equation>}}


### テンソルに対する共変微分


#### 計量テンソルと接続係数




<!--
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


-->