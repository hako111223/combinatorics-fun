---
title: "【月刊組合せ論 Natori】グラフ除去補題【2025 年 7 月号】"
date: 2025-07-01
showTableOfContents: true
---

月刊組合せ論 Natori は面白そうな組合せ論のトピックを紹介していく企画です。今回はグラフ除去補題を紹介します。

## グラフ除去補題とは

グラフ $H$ の頂点数を $v(H)$ とします。グラフ除去補題とは次の定理です。

{{< alert "lightbulb" >}}
**定理**: 任意のグラフ $H$ および任意の $\varepsilon>0$ に対して、ある $\delta=\delta(H,\varepsilon)>0$ が存在して、$n$ 頂点グラフ $G$ であって部分グラフとして現れる $H$ の個数が高々 $\delta n^{v(H)}$ であるものは辺を高々 $\varepsilon n^2$ 個削除することで $H$ をなくすことができる。
{{< /alert >}}

特に $H$ が三角形 (3 頂点からなるサイクル) のときは、三角形除去補題と呼ばれます。

{{< alert "lightbulb" >}}
**定理**: 任意の $\varepsilon>0$ に対して、ある $\delta=\delta(\varepsilon)>0$ が存在して、$n$ 頂点グラフ $G$ であって部分グラフとして現れる三角形の個数が高々 $\delta n^3$ であるものは辺を高々 $\varepsilon n^2$ 個削除することで三角形をなくすことができる。
{{< /alert >}}

## Roth の定理

三角形除去補題の有名な応用として Roth の定理があります。

{{< alert "lightbulb" >}}
**定理**: $A\subset \{1,2,\ldots,N\}$ が長さ 3 の等差数列を含まないならば、$|A|=o(N)$ である。
{{< /alert >}}

整数論とグラフ理論が結びつくのは面白いですね。

Roth の定理は長さ 3 の等差数列に関する定理ですが、長さを 3 以上の整数に一般化することができ、セメレディの定理と呼ばれています。セメレディの定理はハイパーグラフ除去補題を用いて証明することができます。

素数からなる等差数列に関する有名なグリーン・タオの定理がありますが、セメレディの定理から導くことはできません (素数は密度が 0 なので)。しかしこの記事で述べる概念が大いに関わってきます。

## 正則化補題とグラフ数え上げ補題

グラフ除去補題を証明するカギとなるのは次の 2 つの補題です。

- セメレディの正則化補題
- グラフ数え上げ補題

正則化補題は大雑把にいえば、大きなグラフは頂点集合をいくつかのパーツに分けることで、どの 2 つのパーツの間もランダムっぽくすることができるという命題です。ランダムっぽいという概念を定式化したものが $\varepsilon$ 正則分割です。ざっくり見ていきましょう。

立川志の輔さんと秋山仁さんの有名なエピソードで、大きな鍋に入った味噌汁の味見は少し飲むだけでできるが、統計も同じだといった趣旨のものがあります。よく混ざっていれば味の濃さは一定なので、少しでよいということですね。ランダムグラフでも、濃さが一定であることを期待します。

$U,W$ を頂点からなる集合、$A\subseteq U, B\subseteq W$ を部分集合とします。$A,B$ 間の濃さ、すなわち辺密度 $d(A,B)$ を $A,B$ 間の辺の個数を要素数の積 $|A|\times |B|$ で割った余りとします。これが全体の辺密度 $d(U,W)$ とあまり変わらないことを期待します。もちろん $A,B$ を一点集合にしてしまうと密度が 0 または 1 になってしまうので、$A,B$ はある程度大きくしないといけません。

いよいよ定義に移ります。$(U,W)$ が $\varepsilon$ **正則**とは、$|A|\ge \varepsilon |U|, |B|\ge \varepsilon |W|$ をみたす任意の部分集合 $A,B$ に対して $|d(A,B)-d(U,W)|\le \varepsilon$ をみたすことです。

$|A|\ge \varepsilon |U|, |B|\ge \varepsilon |W|$ に現れる $\varepsilon$ は $A,B$ があまり小さくならないようにするために用いられ、$|d(A,B)-d(U,W)|\le \varepsilon$ に現れる $\varepsilon$ は辺密度の差が小さいことを表すために用いられます。2 つの役割は別ですが、別の記号を用いるメリットがあまりないので同じ記号を用いています。

頂点集合の分割 $V=V_1\sqcup V_2\sqcup\cdots\sqcup V_M$ において、各 $(V_i,V_j)$ が $\varepsilon$ 正則という状況を考えたいですが、この定義ではうまくいかないことが知られています。そこで一部は $\varepsilon$ 正則でないことを許容します。それを正確に定義したものが $\varepsilon$ 正則分割です。この記事では用いないので正確な定義は紹介しません。

以上の準備のもとでセメレディの正則化補題を述べることができます。

{{< alert "lightbulb" >}}
**定理** (セメレディの正則化補題): 任意の $\varepsilon>0$ に対して、ある $M$ が存在して、任意のグラフは高々 $M$ 個のパーツからなる $\varepsilon$ 正則分割をもつ。
{{< /alert >}}

もう一つのカギであるグラフ数え上げ補題を紹介します。話を簡単にするため三角形数え上げ補題を紹介します。

{{< alert "lightbulb" >}}
**定理** (三角形数え上げ補題): $X,Y,Z$ を頂点集合であって $(X,Y),(X,Z),(Y,Z)$ が $\varepsilon$ 正則であるものとする。$d(X,Y),d(X,Z),d(Y,Z)\ge 2\varepsilon$ ならば

$$
\begin{gather*}
|\{(x,y,z)\in X\times Y\times Z \mid xyz \text{ は三角形}\}| \\
\ge (1-2\varepsilon)(d(X,Y)-\varepsilon)(d(X,Z)-\varepsilon)(d(Y,Z)-\varepsilon)|X||Y||Z|
\end{gather*}
$$

が成り立つ。
{{< /alert >}}

グラフ除去補題の証明の流れは次のようになります。

- 正則化補題で頂点集合を分割する
- 性質の悪い辺を削除する（高々 $\varepsilon n^2$ 個）
- $H$ が存在したと仮定して、グラフ数え上げ補題で $H$ の個数が $\delta n^{v(H)}$ を超えることを示す

## bound

よく数学者は存在することだけ証明して満足すると言われがちですが、そうでない人もいます。

グラフ除去補題において $\delta$ が $H$ や $\varepsilon$ にどう依存するかを調べる研究も行われています。

グラフ除去補題は正則化補題とグラフ数え上げ補題を用いて証明されていますが、正則化補題において次の結果が Gowers によって示されました。

{{< alert "lightbulb" >}}
ある $c>0$ が存在して、十分小さな任意の $\varepsilon>0$ に対して、パーツの数が $\mathrm{tower}(\lceil\varepsilon^{-c}\rceil)$ 以下であるような $\varepsilon$ 正則分割をもたないようなグラフが存在する。
{{< /alert >}}

ここで $\mathrm{tower}(k)=2^{2^{\cdots^2}}$ (2 が $k$ 個) なので、$\varepsilon$ が小さくなるとパーツ数はとてつもなく大きくなることがわかります。この結果の簡単な証明は Moshkovitz と Shapira の論文にあります。

- Moshkovitz, Guy; Shapira, Asaf. A short proof of Gowers’ lower bound for the regularity lemma. Combinatorica 36, No. 2, 187-194 (2016).

さて、グラフ除去補題の証明では正則化補題を使うので、グラフ除去補題における $\delta$ も似たような大きさになります：

$$
\delta^{-1}=\mathrm{tower}(\varepsilon^{-O(1)})
$$

ところが、Fox によるグラフ除去補題の別証明では $\delta$ を次のようにとれることが示されました：

$$
\delta^{-1}=\mathrm{tower}(O(\log(\varepsilon^{-1})))
$$

これはずっと小さい値です。この事実は、セメレディの正則化補題はグラフ除去補題を証明するには強すぎる可能性を示唆しています。

## 弱い正則化補題

正則化補題よりも弱い命題はいくつか知られています。

- Frieze-Kannan の弱正則化補題
- Duke-Lefman-Rödl のシリンダー正則化補題

Fox の証明では Frieze-Kannan の弱正則化補題が用いられていますが、上で述べたグラフ除去補題の証明とは異なる流れです。

ここでは次の命題を紹介します。Alon, Fischer, Krivelevich, Szegedy の定理で、シリンダー正則化補題の亜種だそうです。

{{< alert "lightbulb" >}}
**定理 (★)**: 任意の $\varepsilon>0$ および $h$ に対して、ある $S=S(\varepsilon,h)$ が存在して、任意のグラフ $G$ は equipartition $\{V_1,\ldots,V_k\}$ および部分集合 $W_i\subseteq V_i \ (i=1,\ldots,k)$ であって次をみたすものをもつ。

- $\sum_{1\le i<j\le k}|d(V_i,V_j)-d(W_i,W_j)|\le \varepsilon k^2$
- すべての組 $(W_i,W_j)$ は $\varepsilon^h$ 正則
- $|W_i|\ge |V(G)|/S$

{{< /alert >}}

ここで equipartition とは $||V_i|-|V_j||\le 1$ となる分割のことで、要するに均等な分割です。この記事では話を簡単にするために、各 $V_i$ の要素数はちょうど $\frac{|V(G)|}{k}$ とします。

$S(\varepsilon,h)$ については次のような評価が知られています。

{{< alert "lightbulb" >}}
$G$ の辺密度が $O(\varepsilon)$ ならば、$S(\varepsilon,h)\le \mathrm{tower}(O(\log(\varepsilon^{-1})))$
{{< /alert >}}

残念ながら一般のグラフ $G$ ではこの結果は得られません。ですが、Fox の結果を得るには辺密度が小さいグラフのみを考えればよいのです。

## 証明

以上の話をまとめて、グラフ除去補題および Fox による評価を証明します。

話を簡単にするために、三角形除去補題のみ証明します。一般のグラフ除去補題の証明は原論文をあたってください。

### 正則化補題と評価

定理 (★)、およびそこに現れる $S$ の評価（すなわち、$G$ の辺密度が $O(\varepsilon)$ ならば、$S(\varepsilon,h)\le \mathrm{tower}(O(\log(\varepsilon^{-1})))$）については、Sapir, Shapira の論文を読んでください。（注意点として、論文では $\varepsilon^h$ 正則の部分が $\frac{\varepsilon^h}{4h}$ 正則になっています）

### 辺密度 $O(\varepsilon)$ のグラフに対する三角形除去補題

$G$ を $n$ 頂点のグラフであって、辺密度 $O(\varepsilon)$、三角形をなくすために少なくとも $\varepsilon n^2$ 辺の削除が必要であるとします。

定理 (★) を $\frac{\varepsilon}{2}$ として用いることで、equipartition $\{V_1,\ldots,V_k\}$ および部分集合 $W_i\subseteq V_i \ (i=1,\ldots,k)$ であって次をみたすものをとることができます。

- $\sum_{1\le i<j\le k}|d(V_i,V_j)-d(W_i,W_j)|\le \frac{\varepsilon}{2} k^2$
- すべての組 $(W_i,W_j)$ は $\frac{\varepsilon^3}{8}$ 正則
- $|W_i|\ge |V(G)|/S$

$d(W_i,W_j)\le \frac{\varepsilon}{2}$ をみたすような $V_i,V_j$ 間の辺を削除します。削除する辺の数は

$$
\begin{align*}
\sum d(V_i,V_j)|V_i||V_j| &= \frac{n^2}{k^2}\sum d(V_i,V_j) \\
&\le \frac{n^2}{k^2}\left(\sum|d(V_i,V_j)-d(W_i,W_j)|+\sum d(W_i,W_j)\right) \\
&< \frac{n^2}{k^2}\left(\frac{\varepsilon}{2}k^2+\frac{\varepsilon}{2}k^2\right) \\
&= \varepsilon n^2
\end{align*}
$$

ここで和は $d(W_i,W_j)\le \frac{\varepsilon}{2}$ をみたす $i\ne j$ 上をわたります。

削除後のグラフに三角形が存在します。その頂点が $V_i,V_j,V_k$ 上にあるとすると

$$
d(W_i,W_j), d(W_i,W_k), d(W_j,W_k)\ge \frac{\varepsilon}{2}\ge \frac{\varepsilon^3}{4}
$$

となります。三角形数え上げ補題を適用すると、三角形の個数は

$$
\ge \left(1-\frac{\varepsilon^3}{4}\right)\left(\frac{\varepsilon^3}{8}\right)^3\frac{n^3}{S^3}
$$

となります。辺密度が $O(\varepsilon)$ より $S\le \mathrm{tower}(O(\log(\varepsilon^{-1})))$ が成り立つので、三角形の個数は

$$
\ge n^3/\mathrm{tower}(O(\log(\varepsilon^{-1})))
$$

となり、Fox の評価が得られました。

### 一般のグラフに対する三角形除去補題

$G$ を三角形をなくすために辺を $\varepsilon n^2$ 回以上削除しなければならないグラフとします。辺を共有しない三角形を最大で $m$ 個選べるとします。$m$ 個の三角形の三辺をすべて削除すれば $G$ から三角形がなくなるので、$3m\ge \varepsilon n^2$ となります。$\varepsilon n^2/3$ 個の三角形からなる部分グラフを $G'$ とします。すると辺密度が $\varepsilon$ で、三角形をなくすために $\varepsilon n^2/3$ 回以上辺を削除する必要があります。よって上述の三角形除去補題が $\varepsilon/3$ に対して適用可能です。$G'$ に現れる三角形は $G$ にも現れることを用いると、一般の場合の証明ができます。

## おわりに

セメレディの正則化補題はこの分野の中心的存在なので、別の記事でも扱うかもしれません。その際はより深掘りしたいと思っています。

しばらく更新をおやすみしていた月刊組合せ論 Natori ですが、今月号から連載を再開しようと思います。応援のほどよろしくお願いします！

## 参考文献

- Sapir, Shachar; Shapira, Asaf. The induced removal lemma in sparse graphs. Comb. Probab. Comput. 29, No. 1, 153-162 (2020).
- Shapira, Asaf. Local-vs-global combinatorics. ICM 2022.
- Zhao, Yufei. Graph theory and additive combinatorics. Exploring structure and randomness. Cambridge University Press (2023).