---
title: "ランダム順列における固定点の個数の期待値"
date: 2024-12-04
showTableOfContents: true
---

この記事は [Math Advent Calendar 2024](https://adventar.org/calendars/10467) の 4 日目の記事です。

今回はランダム順列において固定点の個数の期待値を求めていきます。

## 問題

順列とは $(1,2,\ldots,n)$ の順列のこととします。順列 $p$ の固定点とは、$p_v=v$ をみたす $v$ のことです。例えば $p=(3,2,1,4,6,5)$ では $2,4$ が固定点です。

今回考える問題は次のようなものです：$n!$ 個の順列を等確率でランダムに選んだときの固定点の個数の期待値を求めよ。

小さい例で試してみましょう。$n=1$ のときは $p=(1)$ しかないので $1$ です。$n=2$ のとき $p=(1,2),(2,1)$ の 2 つがあります。固定点の個数はそれぞれ $2,0$ なので、期待値は 1 です。$n=3$ のとき

- $p=(1,2,3)$: 3 個
- $p=(1,3,2)$: 1 個
- $p=(2,1,3)$: 1 個
- $p=(2,3,1)$: 0 個
- $p=(3,1,2)$: 0 個
- $p=(3,2,1)$: 1 個

なので、期待値は $\frac{3+1+1+1}{6}=1$ です。すべての $n$ について期待値は 1 だろうと予測できますね。

では実際に証明してみましょう。いろいろな証明方法がありますが、ここでは対称群の作用を考えます。

## コーシー・フロベニウスの補題

群作用について簡単に紹介します。$G$ を有限群、$X$ を集合とします。$\sigma$ を $G$ の $X$ への作用とします。つまり、各 $g\in G$ に対して $\sigma(g)$ は $X$ 上の全単射であり、かつ $g$ を $\sigma(g)$ にうつす写像が $G$ から $X$ 上の全単射のなす群への群準同型であるものです。$x\in X$ に対して $\sigma(g)(x)$ のことを $g.x$ と書くことにします。

$x\in X$ に対して集合 $\{g.x\mid g\in G\}$ を**軌道**といい、$g\in G$ に対して $\mathrm{Fix}(g)=\{x\in X\mid g.x=x\}$ を**固定点集合**といいます。

コーシー・フロベニウスの補題はバーンサイドの補題とも呼ばれ、軌道の個数を数える公式です。

{{< alert "lightbulb" >}}
**補題**: 相異なる軌道の個数は

$$
\frac{1}{|G|}\sum_{g\in G}|\mathrm{Fix}(g)|
$$

に等しい。
{{< /alert >}}

この補題を使うことで期待値が計算できます。対称群 $S_n$ の $X=\{1,2,\ldots,n\}$ への作用を通常の作用とします (すなわち、$g\in S_n, x\in X$ に対して $g.x$ は $g_x$)。このとき期待値は補題における式

$$
\frac{1}{n!}\sum_{g\in S_n}|\mathrm{Fix}(g)|
$$

に等しいので、軌道の個数に等しいことになります。明らかに軌道は 1 本なので、期待値が 1 に等しいことがわかりました。

## 一般化

一般化して次の問題を考えます：$n!$ 個の順列を等確率でランダムに選んだときの固定点の個数の $k$ 乗の期待値を求めよ。

つまり

$$
\frac{1}{n!}\sum_{g\in S_n}|\mathrm{Fix}(g)|^k
$$

を計算します。ぱっと見ではコーシー・フロベニウスの補題は使えないように見えますが、実は再びこの補題を使うことができます。

$\sigma$ を $G$ の $X$ への群作用とするとき、$G$ の $X^k$ (直積集合) への群作用 $\sigma^{\prime}$ を

$$
g.(x_1,\ldots,x_k)=(g.x_1,\ldots,g.x_k)
$$

により定めます。すると $\mathrm{Fix} _ {\sigma^{\prime}}(g)=\mathrm{Fix}_{\sigma}(g)^k$ であることがわかります。集合として等しいので位数も等しいです。

このことから、対称群 $S_n$ の $\{1,2,\ldots,n\}^k$ への作用を考えたとき、軌道の個数が答えになります。

例えば $(1,2,2,3)$ の軌道には $(2,3,3,1)$ などが属しますが、$(1,2,3,2)$ は属しません。

軌道の個数は、$X_1\cup X_2\cup\cdots\cup X_n=\{1,2,\ldots,k\}$ (ここで $X_i$ は互いに交わらないが、空集合でもよい) をみたす集合 $\{X_1,\ldots,X_n\}$ の個数に等しいことがわかります。$n\ge k$ のときこの数はベル数と呼ばれる数と等しくなります。

## 参考文献

- https://kotatsugame.hatenablog.com/entry/2022/08/03/112733
- https://qchu.wordpress.com/2012/11/07/fixed-points-of-random-permutations/
