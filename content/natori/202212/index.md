+++
title = "【月刊組合せ論 Natori】June Huh 氏の業績を解説【2022 年 12 月号】"
date = 2022-12-01
tags = ["グラフ理論", "マトロイド"]
+++

{{< addbib label="ahk18" title="Adiprasito, Karim; Huh, June; Katz, Eric. Hodge theory for combinatorial geometries. Ann. Math. (2) 188, No. 2, 381-452 (2018)." >}}
{{< addbib label="bhmpw20" title="Tom Braden, June Huh, Jacob P. Matherne, Nicholas Proudfoot, Botong Wang, Singular Hodge theory for combinatorial geometries" link="https://arxiv.org/abs/2010.06088" >}}
{{< addbib label="bh20" title="Brändén, Petter; Huh, June. Lorentzian polynomials. Ann. Math. 192, No. 3, 821-891 (2020)." >}}
{{< addbib label="eur24" title="Essence of independence: Hodge theory of matroids since June Huh. Bull. Am. Math. Soc., New Ser. 61, No. 1, 73-102 (2024)." >}}
{{< addbib label="huh12" title="Huh, June. Milnor numbers of projective hypersurfaces and the chromatic polynomial of graphs. J. Am. Math. Soc. 25, No. 3, 907-927 (2012)." >}}
{{< addbib label="pit14" title="Pitsoulis, Leonidas S. Topics in matroid theory. SpringerBriefs in Optimization. New York, NY: Springer. xiv, 127 p. (2014)." >}}

月刊組合せ論 Natori は面白そうな組合せ論のトピックを紹介していく企画です。今回は 2022 年のフィールズ賞受賞者である June Huh 氏（許埈珥、ホ・ジュニとも書かれる）の業績を解説します。

高校中退を経てフィールズ賞を受賞するなど、生い立ちも注目を集めていますが、組合せ論に業績が多いということで今回は業績に注目していきたいと思います。

**注意**: 最先端の現代数学は非常に難解で、専門家にとっても解説することは難しい場合があります。それを素人である筆者が解説するのは無謀なことです。正確であるよう努めますが、誤りを含む可能性があります。正確な情報を知りたい方は提示される文献を参照してください。また誤りの指摘はいつでも受け付けます。

## 業績をひとことで

フィールズ賞の受賞理由は次のようになっています。

> For bringing the ideas of Hodge theory to combinatorics, the proof of the Dowling–Wilson conjecture for geometric lattices, the proof of the Heron–Rota–Welsh conjecture for matroids, the development of the theory of Lorentzian polynomials, and the proof of the strong Mason conjecture.

すなわち

- ホッジ理論のアイデアを組合せ論に導入した
- Dowling-Wilson 予想の証明
- Heron-Rota-Welsh 予想の証明
- ローレンツ多項式の理論の開発
- 強 Mason 予想の証明

が June Huh 氏の代表的な業績ということです。

## Read の予想

上のリストにはありませんが、まずは Read の予想について紹介します。その前にまず四色定理について説明します。

**グラフ**とは頂点と辺からなる図形です。辺は 2 つの頂点を結んでいます。以下、グラフといえば有限なものとします。

**平面グラフ**とは平面上に描かれた、辺が交差しないグラフのことです。例えば下のグラフは平面グラフです。

![](./sLI5t27.png)

下のグラフは平面グラフではありません。

![](./DCfQjgm.png)

しかし、次のように頂点を移動すると平面グラフとなります。

![](./NalHgeS.png)

このように頂点と辺の書き方を変えることで平面グラフとなるようなグラフのことを**平面的グラフ**といいます。

グラフの**彩色**とは、辺で結ばれている 2 頂点が同じ色にならないように頂点に色を塗ることです。例えば以下のグラフは 3 色で塗り分けることができます。

![](./N8HCmfT.png)

$n$ 色以下で塗り分けられるとき、$n$ **彩色可能**といいます。上のグラフは 3 彩色可能ですが、2 彩色可能ではありません。

以上の準備の下で、四色定理を述べることができます。

{{< thmbox title="定理（四色定理）" >}}
すべての平面的グラフは 4 彩色可能である。
{{< /thmbox >}}

四色定理に関連して、彩色多項式という概念が生まれました。グラフ $G$ に対して、$c_G(n)$ を $n$ 彩色の方法の数とします。$c_G(n)$ は $n$ に関する多項式となることが知られており、**彩色多項式**と呼ばれます。

例として以下の直線グラフの彩色多項式を求めてみましょう。

![](./rGbAvb7.png)

まず左端は好きな色で塗れるので、$n$ 通りあります。2 番目の頂点は異なる色で塗らなければならないので、$n-1$ 通りあります。3 番目の頂点は 2 番目の頂点と異なる色なので、これも $n-1$ 通りです。残りも同様なので、彩色多項式は

$$
c_G(n)=n(n-1)^5=n^6-5n^5+10n^4-10n^3+5n^2-n
$$

となります。

四色定理を彩色多項式を用いて述べると、任意の平面的グラフ $G$ に対して $c_G(4)>0$ ということになります。

前置きが長くなってしまいましたが、Read の予想について述べます。Read の予想は彩色多項式の係数から得られる数列に関する予想です。係数の絶対値を順に並べて数列を作ります。上の例では $1,5,10,10,5,1$ となります。Read の予想は次のような予想です。

{{< thmbox title="予想" >}}
彩色多項式の係数の絶対値からなる数列は unimodal である。すなわちある場所まで単調増加で、その先では単調減少になる。
{{< /thmbox >}}

この予想は 40 年近く未解決でしたが、当時大学院生の June Huh 氏によって証明されました。実際に証明されたのは次のより強い定理です。

{{< thmbox title="定理" >}}
彩色多項式の係数の絶対値からなる数列は対数凹 (log-concave) である。すなわちすべての $i$ に対して $a_i^2\ge a_{i-1}a_{i+1}$ をみたす。
{{< /thmbox >}}

グラフが一直線の場合、この数列は二項係数 $\binom{n}{0},\binom{n}{1},\ldots,\binom{n}{n}$ となります。二項係数の数列が log-concave な数列の代表例です。

証明は {{< cite label="huh12" >}} をご覧ください。グラフ理論の問題でありながら、証明には代数幾何、特異点理論の手法が用いられています。

ちなみに、June Huh 氏は日本人のフィールズ賞受賞者である広中平祐氏と交流があり、代数幾何を教わっていました。突然代数幾何からグラフ理論に転向したように思うかもしれませんが、2 つの分野の関わりは他の数学者が示唆していたようです。

## Heron-Rota-Welsh 予想

Heron-Rota-Welsh 予想は上述の Read の予想をマトロイド上に一般化したものです。マトロイドは数学の様々な場面で現れる性質を抽出したものです。マトロイドを定義する前にその性質を見ていきましょう。より詳しくは [【月刊組合せ論 Natori】マトロイドに入門しよう【2024 年 7 月号】](../202407/) をご覧ください。

グラフが**森**であるとは、サイクルを含まないことをいいます。特に連結な森を木といいます。

$X,Y$ がグラフ $G$ の森であるような部分グラフで、辺の数は $Y$ より $X$ の方が多いとします。このとき、$X$ の辺であり $Y$ の辺でないようなある辺 $e$ について、$Y$ に $e$ を追加しても森のままとなります。

一方、ベクトル空間においても似たような命題が成り立ちます。$X,Y$ がベクトル空間 $V$ の線形独立部分集合で、$|X|>|Y|$ とします。このとき、あるベクトル $x\in X\setminus Y$ について $Y\cup\{x\}$ が線形独立となります。

両者の性質を抽出したものがマトロイドです。

有限集合 $E$ とその部分集合族 $\mathcal{I}$ が次の条件をみたすとき、$(E,\mathcal{I})$ を**マトロイド**といいます。

1. $\emptyset\in \mathcal{I}$
2. $X\in \mathcal{I}, Y\subset X$ ならば $Y\in \mathcal{I}$
3. $X,Y\in \mathcal{I}, |X|>|Y|$ ならばある $x\in X\setminus Y$ について $Y\cup\{x\}\in \mathcal{I}$

例えばある行列 $A$ に対して、$E$ を $A$ の列ベクトル全体、$\mathcal{I}$ を $E$ の線形独立部分集合全体とすればマトロイドとなります。このようなマトロイドを**表現可能** (representable) マトロイドと呼びます。

このようにマトロイドは独立性を扱う概念です。$\mathcal{I}$ の元のことを**独立集合**と呼びます。

マトロイドから**特性多項式** (characteristic polynomial) と呼ばれる多項式が定まります。特性多項式はマトロイドがグラフに由来する場合は彩色多項式と一致することが知られています。そこで、次のような予想が生まれました。

{{< thmbox title="予想 (Helon-Rota-Welsh)" >}}
マトロイドの特性多項式の係数の絶対値からなる数列は log-concave である。
{{< /thmbox >}}

Read の予想を解決した論文で、マトロイドが標数 0 の体上で表現可能という条件の下では証明されていました。しかし一般の場合にはこの手法は力不足でした。一般のマトロイドはグラフやベクトル空間に由来するとは限らず、どのような性質を持つか謎に包まれていました。その後も部分的な進展はありましたが、完全解決にはなかなか至りませんでした。

{{< cite label="ahk18" >}} において、Heron-Rota-Welsh 予想が証明されました。彼らはどのようなマトロイドにも背後には幾何学があることを明らかにしたのです。（幾何学を作り上げた、の方が適切かもしれません。）

ざっくり説明すると、マトロイドから「コホモロジー環」を作ることで証明されました。コホモロジーは次の性質をもつことが期待されます。

- Poincaré 双対性
- hard Lefschetz 定理
- Hodge-Riemann 関係

これらを**ケーラーパッケージ** (Kähler package) と呼ぶそうです。

マトロイドから作られた Chow ring と呼ばれるものがケーラーパッケージをみたすことを示し、Hodge-Riemann 関係から Heron-Rota-Welsh 予想を導くというのが論文での証明の流れのようです。

こうして、マトロイドのホッジ理論は組合せ論と幾何学をつなぐ大きな理論となり、その後も「log-concave な数列の背後にはホッジ理論的な構造が存在する」という信念のもとに発展を続けます。

## Dowling-Wilson 予想

マトロイドにはランク関数と呼ばれる重要な関数があります。マトロイド $(E,\mathcal{I})$ のランク関数 $r$ は $E$ の部分集合に対し非負整数値を対応させる関数で

$$
r(X)=\max\{|Y|:Y\subseteq X, Y\in\mathcal{I}\}
$$

により定義されるものです。これは劣モジュラ性という性質をみたすことが知られています。

$E$ の部分集合 $X$ が**フラット**であるとは、すべての $e\in E\setminus X$ に対して $r(X\cup\{e\})>r(X)$ をみたすことをいいます。ランクが $i$ のフラットの個数を $W_i$ とおきます。

次の予想は Dowling, Wilson の Top-Heavy 予想と呼ばれるものです。

{{< thmbox title="予想 (Dowling-Wilson)" >}}
$0\le i\le j\le r(E)-i$ に対して $W_i\le W_j$ をみたす。
{{< /thmbox >}}

証明は {{< cite label="bhmpw20" >}} で与えられました。証明には上述の

- Poincaré 双対性
- hard Lefschetz 定理
- Hodge-Riemann 関係

が登場します。

なお、数列 $W_0,W_1,\ldots,W_{r(E)}$ は log-concave であることが予想されていますが、こちらは未解決のままのようです。

## 強 Mason 予想

$M$ を $n$ 元集合上のマトロイドとし、$I_k(M)$ を $M$ の $k$ 元独立集合の個数とします。例えば $M$ が $n$ 次単位行列から定まるマトロイドのとき、任意に $k$ 個の列ベクトルを選ぶと線形独立となっているので、$I_k(M)=\binom{n}{k}$ です。log-concave 性が期待できますね。実際にはより強い次の予想がありました。

{{< thmbox title="予想 (Mason)" >}}
$$
\frac{I_k(M)^2}{\binom{n}{k}^2}\ge \frac{I_{k+1}(M)}{\binom{n}{k+1}}\frac{I_{k-1}(M)}{\binom{n}{k-1}}
$$
{{< /thmbox >}}

この予想はローレンツ多項式の理論を用いて証明されました。ローレンツ多項式は {{< cite label="bh20" >}} で導入されました。定義は読んでもよくわからなかったのでここには書きません。

## あとがき

unimodal な数列という素朴な対象から、これほどまでに奥深い数学が広がっているとは思いもよりませんでした。世界がつながるのはいつ見ても面白いです。

マトロイドや log-concave 数列についてはまだまだ奥が深そうなので今後の号でも取り上げたいと思っています。

この記事を公開してから時間が経ちましたが、June Huh 氏は新たに魅力的な論文を複数発表しています。そちらも解説したいです。

これから現代数学がますます発展していくことを期待しています。

## 参考文献

まずは一般向けに書かれた以下の記事をおススメします。

- [A Path Less Taken to the Peak of the Math World](https://www.quantamagazine.org/a-path-less-taken-to-the-peak-of-the-math-world-20170627/)
- [He Dropped Out to Become a Poet. Now He’s Won a Fields Medal.](https://www.quantamagazine.org/june-huh-high-school-dropout-wins-the-fields-medal-20220705/)

また、フィールズ賞受賞者を決める ICM による解説も業績がまとまっていておススメです。

- https://www.mathunion.org/imu-awards/fields-medal/fields-medals-2022

数学セミナー 2023 年 1 月号でフィールズ賞受賞者の業績が特集されました。そちらも読んでみましょう。

{{< showbib >}}
