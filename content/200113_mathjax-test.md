---
title: "Mathjaxのテスト"
tags: ["TeX"]
date: 2020-01-10T18:27:38+09:00
draft: false
---
テスト投稿がてら，LaTeX表現ができるか確認

<div>
  $$
  \begin{bmatrix}
  a & b \\
  c & d \\
  \end{bmatrix}
  $$
  $$
  f(z)=\oint_{|\zeta-c|=R}\frac{f(\zeta)}{\zeta-z}\frac{d\zeta}{2\pi i},\text{ }(|z-c|< R)\\
  f(z)=\sum_{n=0}^\infty(z-c)^n\oint_{|\zeta-c|=R}\frac{f(\zeta)}{(\zeta-z)^{n+1}}\frac{d\zeta}{2\pi i},\text{ }(|z-c|< R)
  $$
</div>

#### 注意事項
- 一段落で表示可能な数式数に限界があるようなので，あまり本文が長くならない様工夫する必要あり．
- 数式行は改行して入れる．

参照
https://maku77.github.io/hugo/settings/math-jax.html
