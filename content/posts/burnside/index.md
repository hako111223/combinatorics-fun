---
title: "バーンサイドの補題の表現論を用いた証明"
date: 2021-08-05
showTableOfContents: true
---

バーンサイドの補題が競技プログラミング界隈で話題のようです。先日開催された ABC で出題されたからです。

https://atcoder.jp/contests/abc198/tasks/abc198_f

この記事の目標は、バーンサイドの補題を表現論を用いて証明することです。最近表現論を勉強しているので、そのアウトプットを兼ねています。

## バーンサイドの補題

バーンサイドの補題 (コーシー・フロベニウスの補題とも呼ばれます) は次のような命題です。

{{< alert "lightbulb" >}}
$G$ を有限群、$\sigma\colon G\to S_X$ を作用とする。このとき軌道の個数 $m$ は

$$
m=\frac{1}{|G|}\sum_{g\in G}|\text{Fix}(g)|
$$

で求められる。
{{< /alert >}}

ここで $|G|$ は $G$ の位数で、$\text{Fix}(g)=\{x\in X\mid \sigma_g(x)=x\}$ は $g$ を作用させても変化しない $X$ の元からなる集合です。$S_X$ は $X$ から $X$ への全単射全体のなす群で、**作用**とは群準同型 $\sigma\colon G\to S_X$ のことをいいます。また、$x\in X$ に対し、$x$ を通る**軌道**とは集合 $G\cdot x=\{\sigma_g(x)\mid g\in G\}$ のことをいいます。2 つの異なる軌道は共通部分をもちません。また、$X$ のどの元もある軌道に含まれます。このことから、軌道は $X$ の分割をなします。

具体例を 1 つ考えましょう。$n$ 個のものを円形に配置する方法が何通りあるかを数えます。ただし回転して一致するものは同じとします。$X$ は $n$ 個のものを一列に配置する方法全体であるとします。$|X|=n!$ です。$G$ を位数 $n$ の巡回群とします。$G$ の $X$ への作用は巡回シフト (例えば $1,2,\ldots,n$ と並んでいたものを $2,\ldots,n,1$ にすること) とします。すると求める方法の数は軌道の個数と等しくなります。どの $X$ の元も $G$ の非自明な元の作用で動いてしまうので

$$
\text{Fix}(g)=\begin{cases}
0 & (g\ne \text{id}) \\
|X|=n! & (g=\text{id})
\end{cases}
$$

となります。よって、答えはバーンサイドの補題から、$m=\frac{n!}{n}=(n-1)!$ であるとわかります。

また、回転や裏返しで一致するものを同一視するとき、群 $G$ は二面体群と呼ばれる位数 $2n$ の群となります。この場合 $m=\frac{n!}{2n}=\frac{(n-1)!}{2}$ となります。円順列や数珠順列は、バーンサイドの補題から求められることがわかりました。

## 表現論の基礎

バーンサイドの補題を証明するために、表現論の基礎を準備します。ここで書くことはとても基本的なもので、どの表現論の本にも載っていると思います。なので証明は省略します。

群は対称性の研究 (特に方程式の解の対称性) から生まれました。対称性という具体的なものから、群の公理という抽象的なものが生まれたわけです。

逆に、与えられた (抽象的な) 群に対して、どういった空間の対称性を表すかを考えるといったこともよく行われます。この 1 つが上でも述べた作用です。作用は群の各元に対し、集合 $X$ の全単射を対応させます。

$X$ が数学的な構造をもっている場合もよくあります。例えば線形空間の構造をもつことがあります。この場合、対応する全単射にも線形空間の構造を反映させたいです。ここでは有限次元複素線形空間のみを考えます。$V$ を線形空間とし、$V$ の可逆線形変換全体のなす群を $GL(V)$ とします。このとき、作用 $G\to S_V$ の代わりに、群準同型 $G\to GL(V)$ を考えます。これを**表現**といいます。改めて書くと、$G$ を群、$V$ を (有限次元複素) 線形空間とするとき、表現とは群準同型 $G\to GL(V)$ のことです。表現について調べるのが表現論という分野です。

1 つ自明な例をあげます。任意の $g\in G$ に対し、$\varphi_g$ を $V$ 上の恒等変換とします。すると表現 $\varphi\colon G\to GL(V)$ ができます。$V$ が 1 次元のとき、これを**自明な表現**といいます。

線形変換は適当に基底を選ぶことで行列にすることができます。よって $GL(V)$ は可逆行列のなす群 $GL_n(\mathbb{C})$ と同型です ($n$ は $V$ の次元)。ゆえに表現とは群準同型 $\varphi\colon G\to GL_n(\mathbb{C})$ のことだと言ってもよいです。$g\in G$ に対し、$\varphi_g$ は正方行列です。ここで、この行列の対角成分の和 (トレース) を $\chi(g)$ とします。すなわち

$$
\chi(g)=\text{Tr}(\varphi_g)=\sum_{i=1}^n(\varphi_g)_{ii}
$$

とします。このようにして定まる写像 $\chi\colon G\to \mathbb{C}$ のことを**指標**といいます。もともと $n$ 次行列だったものが、対角成分の和をとることで複素数になってしまいました。これではかなりの情報が抜け落ちてしまうと思うかもしれません。しかし情報は全く抜け落ちていないのです。**「2 つの表現が同値であるための必要十分条件は、それらの指標が一致することである」** という定理が成り立ちます。指標は表現の本質であり、指標によって表現がわかってしまいます。これが表現論のすごいところですね。

表現が同値であることの定義をまだしていませんでした。$\varphi\colon G\to GL(V),\psi\colon G\to GL(W)$ を表現とします。$\varphi,\psi$ が**同値**であるとは、線形同型 $T\colon V\to W$ であって、任意の $g\in G$ に対し $T\circ\varphi_g=\psi_g\circ T$ が成り立つものが存在することをいいます。

2 つの表現 $\varphi\colon G\to GL(V), \psi\colon G\to GL(W)$ に対し、新たな表現 $\rho\colon G\to GL(V\oplus W)$ を $\rho_g(v,w)=(\varphi_g(v),\psi_g(w)) \ (g\in G, v\in V, w\in W)$ により定めることができます。これを表現の**直和**といい、$\rho=\varphi\oplus\psi$ と表します。先ほどの例で $\varphi_g$ を $V$ 上の恒等変換とすることにより表現 $\varphi\colon G\to GL(V)$ を定めましたが、これは $\dim V$ 個の自明な表現の直和と同値です。

$\varphi\colon G\to GL(V)$ を表現とします。$W$ を $V$ の部分空間とします。このとき、$W$ が $G$-不変部分空間であるとは、任意の $g\in G, w\in W$ に対し、$\varphi_g(w)\in W$ となることです。$V$ 自身と $\{0\}$ は常に $V$ の $G$-不変部分空間になります。これら以外の $G$-不変部分空間が存在しないとき、この表現は**既約表現**であるといいます。

整数論においては素数が重要な役割を果たします。これはすべての整数が素数の積として表すことができ、かつその表し方が一意であるからです。実は表現論においても似たことが成り立ちます。表現論においては既約表現が素数と同じような役割を果たします。

{{< alert "lightbulb" >}}
**マシュケの定理**: 有限群の表現はすべていくつかの既約表現の直和と同値である。
{{< /alert >}}

よって任意の表現 $\varphi$ は、既約表現 $\varphi_1,\varphi_2,\ldots$ に対し $\varphi_1^{\oplus m_1}\oplus\varphi_2^{\oplus m_2}\oplus\cdots$ と同値になります (無限和の形で書いていますが、有限群の既約表現の同値類は有限個であることが知られているので、これは有限和となります)。$m_i$ を**重複度**といいます。指標を考えましょう。既約表現の指標を**既約指標**といいます。$\varphi$ の指標を $\chi$、$\varphi_i$ の既約指標を $\chi_i$ とすると、$\chi=m_1\chi_1+m_2\chi_2+\cdots$ となります。重複度 $m_i$ を求めたいです。そのために、指標の内積を導入しましょう。

$$
\langle \chi,\chi^{\prime}\rangle=\frac{1}{|G|}\sum_{g\in G}\overline{\chi(g)}\chi^{\prime}(g)
$$

これが指標の内積です。すると、次の素晴らしい関係が成り立ちます。

{{< alert "lightbulb" >}}
**指標の第一直交性**: $\chi_1,\chi_2,\ldots$ を既約指標とする。このとき

$$
\langle \chi_i,\chi_j\rangle=\begin{cases}
1 & (i=j) \\
0 & (i\ne j)
\end{cases}
$$

が成り立つ。
{{< /alert >}}

つまり、既約指標は正規直交します。このことから、重複度は $m_i=\langle \chi,\chi_i\rangle$ により求められます。特に、$m_i$ は一意に定まり、既約表現への分解が一意であることがわかります。

## 置換表現

$\sigma\colon G\to S_X$ を作用とします。ここから表現を作ってみましょう。まず $\mathbb{C}X$ を $X$ の張る線形空間とします。つまり $X$ の元の形式的な線形結合を考えて、それらのなす線形空間です。$X$ は $\mathbb{C}X$ の基底です。よって各 $g\in G$ に対し、全単射 $\sigma_g$ を線形に拡張することで、線形写像 $\widetilde{\sigma} _ g$ が構成できます。具体的に書くと

$$
\widetilde{\sigma} _ g(\sum_{x\in X}c_xx)=\sum_{x\in X}c_x\sigma_g(x)
$$

となります。このようにして表現 $\widetilde{\sigma}\colon G\to GL(\mathbb{C}X)$ が定まります。これを**置換表現**といいます。

置換表現も既約表現に分解できます。このとき、自明な表現の重複度を考えることで、バーンサイドの補題を証明します。

$\chi_1$ を自明な表現の指標とします。重複度は

$$
m_1=\langle\chi_1,\chi_{\widetilde{\sigma}}\rangle=\frac{1}{|G|}\sum_{g\in G}\overline{\chi_1(g)}\chi_{\widetilde{\sigma}}(g)=\frac{1}{|G|}\sum_{g\in G}\chi_{\widetilde{\sigma}}(g)
$$

となります。

**補題 1**：$\chi_{\widetilde{\sigma}}(g)=|\text{Fix}(g)|$

証明：$X=\{x_1,\ldots,x_n\}$ とし、基底 $X$ に関する $\widetilde{\sigma} _ g$ の行列表示を $A$ とします。このとき

$$
A_{ij} = \begin{cases}
1 & x_i=\sigma_g(x_j) \\
0 & x_i\ne \sigma_g(x_j)
\end{cases}
$$

となります。特に

$$
A_{ii} = \begin{cases}
1 & x_i\in\text{Fix}(g) \\
0 & x_i\not\in\text{Fix}(g)
\end{cases}
$$

となります。よって、$\chi_{\widetilde{\sigma}}(g)=\text{Tr}(A)=|\text{Fix}(g)|$ です。(証明終)

これで

$$
m_1=\frac{1}{|G|}\sum_{g\in G}|\text{Fix}(g)|
$$

がわかりました。あとは $m_1$ が軌道の個数に等しいことをいえばよいです。

表現 $\varphi\colon G\to GL(V)$ に対し、$V^G=\{v\in V\mid \forall g\in G, \varphi_g(v)=v\}$ とします。これは $G$-不変部分空間となります。

**補題 2**：$m_1=\dim(\mathbb{C}X)^G$

証明：$\widetilde{\sigma}$ を $\varphi_1^{\oplus m_1}\oplus \varphi_2^{\oplus m_2}\oplus\cdots$ と既約分解します。ただし $\varphi_1$ は自明な表現で、これ以外は自明な表現でないとします。この分解に対応して、$\mathbb{C}X$ も $V_1^{\oplus m_1}\oplus V_2^{\oplus m_2}\oplus\cdots$ と分解します。このとき $(\mathbb{C}X)^G=(V_1^G)^{\oplus m_1}\oplus(V_2^G)^{\oplus m_2}\oplus\cdots$ となります。ここで $V_i^G$ は $V_i$ の $G$-不変部分空間ですが、$\varphi_i$ は既約なので、$V_i^G$ は $\{0\}$ または $V_i$ に等しくなります。$i\ge 2$ に対し $\varphi_i$ は自明な表現でないので、$V_i^G=\{0\}$ となります。よって、$(\mathbb{C}X)^G=V_1^{\oplus m_1}$ となります。次元を比較して、$\dim(\mathbb{C}X)^G=m_1$ が従います。(証明終)

**補題 3**：$\dim(\mathbb{C}X)^G$ は軌道の個数に等しい。

証明：軌道を $\mathcal{O} _ 1,\ldots,\mathcal{O} _ m$ とし、$v_i=\sum_{x\in\mathcal{O} _ i}x\in\mathbb{C}X$ とします。このとき $v_i\in(\mathbb{C}X)^G$ であることは簡単に確かめられます。また $X$ が $\mathbb{C}X$ の基底であることから、$v_1,\ldots,v_m$ が線形独立であることもわかります。よって $v_1,\ldots,v_m$ が $(\mathbb{C}X)^G$ を張ることを示せばよいです。$v=\sum_{x\in X}c_xx$ を $(\mathbb{C}X)^G$ の任意の元とします。$y,z\in X$ が同じ軌道に属するとすると、ある $g\in G$ を用いて $z=\sigma_g(y)$ と表せます。このとき

$$
v=\widetilde{\sigma} _ g(v)=\sum_{x\in X}c_x\sigma_g(x)
$$

となります。左辺の $z$ の係数は $c_z$、右辺の $z$ の係数は $c_y$ です。よって $c_y=c_z$ となります。このことから、ある $c_1,\ldots,c_m\in\mathbb{C}$ が存在して、$x\in\mathcal{O} _ i$ ならば $c_x=c_i$ となります。よって

$$
v=\sum_{x\in X}c_xx=\sum_{i=1}^mc_iv_i
$$

となります。よって $v_1,\ldots,v_m$ が $(\mathbb{C}X)^G$ を張ることが示されました。(証明終)

以上の結果から、バーンサイドの補題が証明できました。

## 参考文献

- 桂利行, 『代数学II 環上の加群』, 東京大学出版会, 2007
- Steinberg, Benjamin. *Representation theory of finite groups: an introductory approach*. Springer Science & Business Media, 2011.