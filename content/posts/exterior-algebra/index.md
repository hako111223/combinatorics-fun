---
title: "外積代数と行列木定理"
date: 2025-12-13
showTableOfContents: true
---

この記事は[木 Advent Calendar 2025](https://adventar.org/calendars/12007) の 13 日目の記事です。

「木材と人材」というタイトルで何か書く予定でしたが、急遽予定を変更してお届けします。

## 外積代数

今月 10 日、[外積代数 in 競プロ](https://zenn.dev/sigma425/articles/a10c0b09f3b2ad)という記事が公開されました。見たことがないテクニックで興味深い記事でした。

これを見て、そういえば外積代数を使う組合せ論の論文があったなあ、ということを思い出したのでその論文を読みました。その内容を軽く紹介していきます。

まずは外積代数を復習します。ベクトル空間 $V$ の基底 $\{e_1,\ldots,e_n\}$ を考えます。外積代数 $\bigwedge(V)$ は $e_{i_1}\wedge e_{i_2}\wedge\cdots \wedge e_{i_k}$ ($1\le i_1<\cdots<i_k\le n$) を基底とするベクトル空間です。このウェッジ $\wedge$ は

- $v\wedge v=0$
- $v\wedge w=-w\wedge v$

などの性質をみたします。外積代数はグラスマン代数とも呼ばれるようです。

以下、ウェッジを省略して $v\wedge w=vw$ のように書きます。総積も $\prod$ を用います。さらに $e_i$ の代わりに $\psi_1,\ldots,\psi_n$ および $\bar{\psi}_1,\ldots,\bar{\psi}_n$ を用います。これらは関係式

- $\psi_i\psi_j=-\psi_j\psi_i$
- $\bar{\psi}_i\bar{\psi_j}=-\bar{\psi}_j\bar{\psi}_i$
- $\psi_i\bar{\psi}_j=\bar{\psi}_j\psi_i$

をみたすとします。特に $\psi_i^2=\bar{\psi}_i^2=0$ です。物理学のフェルミオンと関係するそうですが、物理学はわかりません。

## 外積代数と行列式

$n$ 次正方行列 $A=(A_{ij})$ に対して

$$
\prod_{i,j=1}^n(1+\bar{\psi}_i\psi_jA_{ij})=\sum_{I,J\subset [n]}\bar{\psi}_I\psi_J\det(A_{I,J})
$$

が成り立ちます。ここで $\bar{\psi}_I$ は $i\in I$ に関する $\bar{\psi}_i$ の積（昇順）、$\psi_J$ は $j\in J$ に関する $\psi_j$ の積（昇順）で、$A_{I,J}$ は行を $I$、列を $J$ とした小行列です。

$A$ の行列式だけでなく、小行列式も一挙に現れるところがポイントです。

## 外積代数と行列木定理

グラフ $G$ のラプラシアン $L=D-A$ は [2 日目の記事](../road-network/)でも解説したのでここでは解説しません。

{{< alert "lightbulb" >}}
**定理** (行列木定理)

1. グラフ $G$ の全域木の個数は、ラプラシアン $L$ の任意の余因子と等しい。
2. $\det(tI_n+L)$ は $t$ の多項式であり、一次の係数を $c_1$ とおく。このとき、全域木の個数は $\frac{1}{n}c_1$ に等しい。
3. $L$ の固有値を $\lambda_1,\ldots,\lambda_n$ とする。ただし $\lambda_1=0$ とする。このとき、全域木の個数は $\frac{1}{n}\lambda_2\lambda_3\cdots \lambda_n$ に等しい。
{{< /alert >}}

$j$ を固定したとき

$$
\begin{align*}
\prod_{i=1}^n(1+\bar{\psi}_i\psi_jA_{ij}) &= \prod_{i=1}^n(1+(\bar{\psi}_i-\bar{\psi}_j)\psi_jA_{ij}+\bar{\psi}_j\psi_jA_{ij}) \\
&= \prod_{i=1}^n(1+(\bar{\psi}_i-\bar{\psi}_j)\psi_jA_{ij})\prod_{i=1}^n(1+\bar{\psi}_j\psi_jA_{ij}) \\
&= \prod_{i\in [n]\setminus\{j\}}(1-(\bar{\psi}_j-\bar{\psi}_i)\psi_jA_{ij})\cdot \left(1+\bar{\psi}_j\psi_j\sum_{i=1}^n A_{ij}\right)
\end{align*}
$$

となります。ここで $\psi_j^2=0$ を使いました。

$B_j=\sum_i A_{ij}$ とおき

$$
w(i,j)=\begin{cases}
-A_{ij} & i\ne j \\
B_j & i=j
\end{cases}
$$

$$
\Psi(i,j)=\begin{cases}
(\bar{\psi}_j-\bar{\psi}_i)\psi_j & i\ne j \\
\bar{\psi}_j\psi_j & i=j
\end{cases}
$$

とおきます。すると

$$
\prod_{i,j=1}^n(1+\bar{\psi}_i\psi_jA_{ij})=\prod_{i,j=1}^n(1+\Psi(i,j)w(i,j))
$$

が得られます。

辺 $(i,j)$ の重みを $w(i,j)$ とした有向グラフ $G$ を考えます。$G$ にはループもあります。

辺集合 $H$ に対して、$w(H), \Psi(H)$ を $H$ に含まれる辺 $(i,j)$ について $w(i,j), \Psi(i,j)$ の積をとったものとします。なお $\Psi(i,j)\Psi(i',j')=\Psi(i',j')\Psi(i,j)$ なので積の順番は考えなくてよいです。（$\psi$ と $\bar{\psi}$ で符号が打ち消しあう）

このとき、右辺を展開することで

$$
\prod_{i,j=1}^n(1+\bar{\psi}_i\psi_jA_{ij})=\sum_{H\subset E(G)}\Psi(H)w(H)
$$

となるので

$$
\sum_{I,J\subset [n]}\bar{\psi}_I\psi_J\det(A_{I,J})=\sum_{H\subset E(G)}\Psi(H)w(H)
$$

が成り立ちます。

終点が等しい 2 辺 $(i_1,j),(i_2,j)$ について、$\Psi(i_1,j)\Psi(i_2,j)$ は $\psi_j^2=0$ を含むので 0 です。よって $H$ として入次数が 1 以下のもののみを考えればよいです。

入次数が 1 以下のグラフの連結成分は、次の 3 種類です。

- 木型：根付き木であって辺が根から遠ざかる向きなもの。2 頂点以上。
- ループ型：木タイプのグラフの根にループを加えたもの。1 頂点でもよい。
- サイクル型：サイクルを含むもの。

まずサイクル型を考えましょう。$1\to 2\to\cdots\to k\to 1$ ($k\ge 2$) というサイクルがあるとします。このとき

$$
\begin{align*}
& \Psi(1,2)\Psi(2,3)\cdots\Psi(k-1,k)\Psi(k,1) \\
&= (\bar{\psi}_2-\bar{\psi}_1)\psi_2(\bar{\psi}_3-\bar{\psi}_2)\psi_3\cdots(\bar{\psi}_k-\bar{\psi}_{k-1})\psi_k(\bar{\psi}_1-\bar{\psi}_k)\psi_1 \\
&= (\bar{\psi}_2\bar{\psi}_3\cdots \bar{\psi}_k\bar{\psi}_1+(-1)^k\bar{\psi}_1\bar{\psi}_2\cdots \bar{\psi}_k)\psi_2\psi_3\cdots \psi_k\psi_1 \\
&= ((-1)^{k-1}+(-1)^k)\bar{\psi}_1\bar{\psi}_2\cdots \bar{\psi}_k\psi_2\psi_3\cdots \psi_k\psi_1 \\
&= 0
\end{align*}
$$

となるので、サイクル型は考えなくてよいことになります。

木型は、根を $r$ とするとき $\psi_r$ が現れないので、$\det(A)$ のみを考える場合は無視してよいです。

最後にループ型ですが、$\Psi(H)=\bar{\psi}_{V(H)}\psi_{V(H)}$ となることがわかります。

さて、行列木定理に戻ります。$A=L$ とし、$(n,n)$ 余因子 $\det(A_{[n-1],[n-1]})$ を考えます。

$$
\sum_{H\subset E}\Psi(H)w(H)
$$

における $\bar{\psi}_1\cdots \bar{\psi}_{n-1}\psi_1\cdots \psi_{n-1}$ の係数を求めることになります。$B_j=0$ よりループのないグラフを考えることになるので、$H$ は木型のみを考えればよいです。$\psi_n$ がないので $H$ は頂点 $n$ が根であり辺の向きは根から遠ざかる向きです。全域木 1 つごとに係数が 1 増えることがわかります。よって行列木定理の 1 が証明できました。

2 も証明しましょう。$A=tI_n+L$ とおくと、元のグラフの各頂点に重み $t$ のループを加えたものを考えることになります。$\bar{\psi}_1\cdots \bar{\psi}_n\psi_1\cdots \psi_n$ の係数が $\det(A)$ なので、今回はループ型のグラフのみを考えればよいです。$\det(A)$ の一次の係数は連結成分がループ型の部分グラフであって連結成分が 1 つのもの、すなわち根を指定した全域木の個数となります。根の選び方が $n$ 通りなので、全域木の個数は $n$ で割った値となります。これで行列木定理の 2 が証明できました。

より一般に $t^k$ の係数は連結成分が $k$ 個の森と対応することがわかります。

## おまけ

数え上げと行列式といえば、行列木定理の他に LGV 公式を思い浮かべる人も多いでしょう。なんと LGV 公式も外積代数から導出できるようです。

外積代数、奥が深そうですね。競技プログラミングの世界に新たな知見をもたらして、いずれは典型になるかもしれません。

## 参考文献

- Curtin, Eugene; Lee, Junu; Lu, Andrew; Sun, Sophia. A modified Grassmann algebra approach to theorems on permanents and determinants. Linear Algebra Appl. 581, 20-35 (2019).
- Abdesselam, Abdelmalek. The Grassmann-Berezin calculus and theorems of the matrix-tree type. Adv. Appl. Math. 33, No. 1, 51-70 (2004).
- Carrozza, S.; Tanasa, A. Pfaffians and nonintersecting paths in graphs with cycles: Grassmann algebra methods. Adv. Appl. Math. 93, 108-120 (2018).
