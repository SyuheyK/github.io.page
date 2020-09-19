---
title: "微分幾何のまとめ 2 証明"
tags: ["微分幾何"]
date: 2020-08-13T10:00:00+09:00
draft: true
---

### 内容
- [問2.10の証明](#001)

<a id="markdown-001" name="001"></a>

### 問2.10の証明
テキスト中の式 (2.42) 
{{< equation >}}
  \left(\dfrac{\partial}{\partial u^j_\alpha}\right)_{p+\Delta p} - \left(\dfrac{\partial}{\partial u^j_\alpha}\right)_p
  =\sum_{i,k=1}^2\Delta u^i_\alpha\Gamma_{i\ j}^{\ k}(\alpha) \left(\dfrac{\partial}{\partial u^k_\alpha}\right)_p
{{< /equation >}}
と，上式左辺の座標近傍を変換した式の間で， $\Delta u^i_\alpha\left(\partial/\partial u^k_\alpha\right)_p$ の係数を比較することで，与式を得る．

式
{{< equation >}}
  \left(\dfrac{\partial}{\partial u^j_\alpha}\right)_p
  =\sum_{n=1}^2\left(\dfrac{\partial u^n_\beta}{\partial u^j_\alpha}\right)_p\left(\dfrac{\partial}{\partial u^n_\beta}\right)_p
{{< /equation >}}
より，テキスト中の式(2.42)の左辺を展開すると
{{< equation >}}
  \left(\dfrac{\partial}{\partial u^j_\alpha}\right)_{p+\Delta p} - 
  \left(\dfrac{\partial}{\partial u^j_\alpha}\right)_p
  = \sum_{n=1}^2
  \left\{
    \left(\dfrac{\partial u^n_\beta}{\partial u^j_\alpha}\right)_{p+\Delta p}\left(\dfrac{\partial}{\partial u^n_\beta}\right)_{p+\Delta p}
  - \left(\dfrac{\partial u^n_\beta}{\partial u^j_\alpha}\right)_p\left(\dfrac{\partial}{\partial u^n_\beta}\right)_p
  \right\}
{{< /equation >}}
となる．ここで，右辺の中括弧内は
{{< equation >}}
\left(\dfrac{\partial u^n_\beta}{\partial u^j_\alpha}\right)_{p+\Delta p}\left(\dfrac{\partial}{\partial u^n_\beta}\right)_{p+\Delta p} - \left(\dfrac{\partial u^n_\beta}{\partial u^j_\alpha}\right)_p\left(\dfrac{\partial}{\partial u^n_\beta}\right)_{p}
&=\left\{\left(\dfrac{\partial u^n_\beta}{\partial u^j_\alpha}\right)_{p+\Delta p}-\left(\dfrac{\partial u^n_\beta}{\partial u^j_\alpha}\right)_{p}\right\}\left(\dfrac{\partial}{\partial u^n_\beta}\right)_p\\
&\quad+ \left(\dfrac{\partial u^n_\beta}{\partial u^j_\alpha}\right)_{p+\Delta p}\left\{\left(\dfrac{\partial}{\partial u^n_\beta}\right)_{p+\Delta p} - \left(\dfrac{\partial}{\partial u^n_\beta}\right)_{p}\right\}\tag*{(#1)}\label{eq1}
{{< /equation >}}
と書き換えることができる．

$\ref{eq1}$ の右辺第一項は

ここで
{{< equation >}}
  f(p)=\left(\dfrac{\partial u^n_\beta}{\partial u^j_\alpha}\right)_p
{{< /equation >}}
とおけば，