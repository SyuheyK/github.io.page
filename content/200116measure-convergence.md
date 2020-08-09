---
title: "測度論の収束定理"
tags: ["測度論"]
date: 2020-01-16T10:00:00+09:00
draft: false
---
測度論の収束定理で有名な以下の三定理について，一つが成り立てば他二つも成り立つことを示します．
その後，Lebesgueの収束定理を使った計算例を紹介します．

## 三定理のステートメント
以下いずれも測度空間$(X,\mathcal{B},\mu)$を所与とする．
### 単調収束定理
$0\le f_n\le f_{n+1}\text{ a.e. }(n=1,2,...), f_n\rightarrow f\text{ a.e. }(n\rightarrow\infty)$である可測関数列$f_n(n=1,2,...)$と可測関数$f$について
{{<equation>}}\lim_{n\rightarrow\infty}\int_Xf_nd\mu=\int_Xfd\mu{{</equation>}}
が成り立つ．

### Fatouの補題
$f_n\ge0\text{ a.e. }$である可測関数列に対して，
{{<equation>}}\liminf_{n\rightarrow\infty}\int_Xf_nd\mu \ge \int_X\liminf_{n\rightarrow\infty}f_nd\mu{{</equation>}}
が成り立つ．

### Lebesgueの収束定理
可測関数列$f_n(n=1,2,...)$と可測関数$f$が以下をみたすものとする．
1. $f_n\rightarrow f\text{ a.e. }$,
2. 可測関数$h$が各$n$に対し$|f_n|\le h$
このとき，極限関数$f$も可積分であり，
{{<equation>}}\lim_{n\rightarrow\infty}\int_Xf_nd\mu=\int_Xfd\mu{{</equation>}}
が成り立つ．

## 三定理の証明
証明は以下の感じ．
- 単調収束定理が成り立つ $\Rightarrow$ Fatouの補題が成り立つ
- Fatouの補題が成り立つ $\Rightarrow$ 単調収束定理が成り立つ
- Fatouの補題が成り立つ $\Rightarrow$ Lebesgueの収束定理が成り立つ

### 単調収束定理が成り立つ ⇒ Fatouの補題が成り立つ
$f_n\ge0\text{ a.e. }(n=1,2,...)$である可測関数列が与えられたとする．
$\liminf_{n\rightarrow\infty}f_n=\sup_{n\ge1}\inf_{k\ge n}f_k$に注意すると，$g_n:=\inf_{k\ge n}f_k$は
{{<equation>}}f_n\ge g_n\text{ a.e., }{{</equation>}}
をみたすので，
{{<equation>}}g_n\uparrow \liminf_{n\rightarrow\infty}f_n\text{ a.e. }{{</equation>}}
が成り立つ．よって単調収束定理から，

{{<equation>}}
\liminf_{n\rightarrow\infty}\int_Xf_nd\mu 
\ge \liminf_{n\rightarrow\infty}\int_Xg_nd\mu 
= \lim_{n\rightarrow\infty}\int_Xg_nd\mu \\
= \int_X\lim_{n\rightarrow\infty}g_nd\mu 
= \int_X\liminf_{n\rightarrow\infty}f_nd\mu.
{{</equation>}}

### Fatouの補題が成り立つ ⇒ 単調収束定理が成り立つ
仮定の$0\le f_n\le f_{n+1}\text{ a.e. }(n=1,2,...)$から，各$n$に対して，$f_n\le f,\int_Xf_nd\mu\le\int_Xfd\mu$が成り立つ．これから,
{{<equation>}}\limsup_{n\rightarrow\infty}\int_Xf_nd\mu\le\int_Xfd\mu.{{</equation>}}
Fatouの補題から
{{<equation>}}\int_Xfd\mu\le\liminf_{n\rightarrow\infty}\int_Xf_nd\mu{{</equation>}}
が成り立つので，上2式を合わせて
{{<equation>}}\limsup_{n\rightarrow\infty}\int_Xf_nd\mu\le\liminf_{n\rightarrow\infty}\int_Xf_nd\mu{{</equation>}}
が成り立つ．上下限に関する基本的な関係式から
{{<equation>}}\liminf_{n\rightarrow\infty}\int_Xf_nd\mu\le\limsup_{n\rightarrow\infty}\int_Xf_nd\mu{{</equation>}}
が得られるから，
{{<equation>}}\int_Xfd\mu=\limsup_{n\rightarrow\infty}\int_Xf_nd\mu=\liminf_{n\rightarrow\infty}\int_Xf_nd\mu{{</equation>}}
より，$\inf_Xf_nd\mu$は$\int_Xfd\mu$に収束することがいえる．

### Fatouの補題が成り立つ ⇒ Lebesgueの収束定理が成り立つ

## Lebesgueの収束定理の計算例
### 標準正規分布の全確率
標準正規分布の全確率が$1$になること
{{<equation>}}
\int_{-\infty}^\infty\frac{1}{\sqrt{2\pi}}e^{-\frac{x^2}{2}}dx=1
{{</equation>}}
を重積分を使わずに証明します．その際にLebesgueの収束定理を使います．

関数$f:[0,\infty)\rightarrow\mathbb{R}$を
{{<equation>}}
f(x)=\left(\int_0^xe^{-\frac{t^2}{2}}dt\right)^2+2\int_0^1\frac{\exp\left\{-\frac{x(1+t^2)}{2}\right\}}{1+t^2}dt
{{</equation>}}
と定義する．$f$を微分すると
{{<equation>}}
f'(x)
    &=2\left(\int_0^xe^{-\frac{t^2}{2}}dt\right)\cdot e^{-\frac{x^2}{2}}\\
    &\quad 2\int_0^1\frac{\exp\left\{-\frac{x(1+t^2)}{2}\right\}}{1+t^2}\cdot\left\{-x(1+t^2)\right\}dt\\
    &=\cdots\\
    &=0
{{</equation>}}
つまり$f$は定数関数．さらに
{{<equation>}}
f(0)
    &=0+2\int_0^1\frac{1}{1+t^2}dt\\
    &=2\left[\arctan t\right]_0^1\\
    &=\frac{\pi}{2}
{{</equation>}}
なので，$f$の値は恒等的に$\pi/2$である．ゆえに
{{<equation>}}
\frac{\pi}{2}
    &=\lim_{x\rightarrow\infty}f(x)\\
    &=\left(\int_0^\infty e^{-\frac{t^2}{2}}dt\right)^2+2\lim_{x\rightarrow\infty}\int_0^1\frac{\exp\left\{-\frac{x(1+t^2)}{2}\right\}}{1+t^2}dt\\
    &=\left(\int_0^\infty e^{-\frac{t^2}{2}}dt\right)^2+2\int_0^1\lim_{x\rightarrow\infty}\frac{\exp\left\{-\frac{x(1+t^2)}{2}\right\}}{1+t^2}dt\\
    &=\left(\int_0^\infty e^{-\frac{t^2}{2}}dt\right)^2+0.
{{</equation>}}
この式を整理して全確率$1$の公式を得る．

### $\sin x/ x$の積分
講義積分
{{<equation>}}
\lim_{M\rightarrow\infty}\int_0^M\frac{\sin x}{x}dx=\frac{\pi}{2}
{{</equation>}}
の証明．
{{<equation>}}
\lim_{M\rightarrow\infty}\int_0^M\frac{\sin x}{x}dx
    &=\lim_{M\rightarrow\infty}\int_0^M\left(\int_0^\infty e^{-tx}dt\right)\sin xdx\\
    &=\lim_{M\rightarrow\infty}\int_0^\infty\left(\int_0^Me^{-tx}\sin xdx\right)dt\\
    &=\lim_{M\rightarrow\infty}\int_0^\infty\frac{1+e^{-tM}(\cos M+t\sin M)}{1+t^2}dt\\
    &=\int_0^\infty\lim_{M\rightarrow\infty}\frac{1+e^{-tM}(\cos M+t\sin M)}{1+t^2}dt\\
    &=\int_0^\infty\frac{1}{1+t^2}dt\\
    &=\left[\arctan t\right]_0^\infty\\
    &=\frac{\pi}{2}.
{{</equation>}}