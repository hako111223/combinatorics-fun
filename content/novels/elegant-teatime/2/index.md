---
title: "【elegant teatime】代数学の基本定理 (2) 【第 2 話】"
date: 2025-11-30
showTableOfContents: true
---

## 静香の証明

{{< speech img="../img/Fashion-36.png" name="芽衣" >}}
このお茶、うまいなー！
{{< /speech >}}

{{< speech img="../img/Tea-5.png" name="素子" >}}
新しい茶葉をご用意いたしました。
{{< /speech >}}

{{< speech img="../img/Sakura-23.png" name="桜子" >}}
おいしいです……。
{{< /speech >}}

{{< speech img="../img/Cuisine-17.png" name="静香" >}}
リラックスして、ねむくなるね～。
{{< /speech >}}

{{< speech img="../img/Fashion-36.png" name="芽衣" >}}
次は静香の番だから、寝ちゃだめだー。
{{< /speech >}}

{{< speech img="../img/Cuisine-17.png" name="静香" >}}
わかった～。
{{< /speech >}}

---

$f(z)=z^n+a_1z^{n-1}+\cdots+a_n$ とおくね。$f(z)=0$ をみたす $z$ が存在することを証明するよ。

$f(z)$ の偏角に応じて、$z$ に色を決めるね。$-\pi<\arg z\le -\frac{\pi}{3}$ のとき赤、$-\frac{\pi}{3}<\arg z\le \frac{\pi}{3}$ のとき緑、$\frac{\pi}{3}<\arg z\le \pi$ のとき緑にするよ。0 はどれでもいいけど、とりあえず赤にするね。

それで、この補題を使うよ。

{{< alert "lightbulb" >}}
**補題**: 凸多角形が三角形分割されている。各頂点は赤・緑・青のいずれかで塗られている。反時計回りに赤・緑・青となる三角形の個数から時計回りに赤・緑・青となる三角形の個数を引いた値を content と呼ぶ。また多角形の周上において、反時計回りに赤・緑となる辺の個数から時計回りに赤・緑となる辺の個数を引いた値を index と呼ぶ。このとき、content と index は等しい。
{{< /alert >}}

いま、大きな円を考えて、この円に内接する多角形をとって、三角形分割するよ。十分大きい円なら、反時計回りに一周すると $f(z)$ は $n$ 回転することになる。ここはもう少し慎重に考えた方がよさそうだけど、省略するね～。

円周上にある頂点が十分多いなら、反時計回りに一周したときの色の変化が赤→緑→青→赤→…、という感じで $n$ 周する。だから index は $n$ になる。

補題を使うと content も $n$ になるから、特に赤・緑・青の三角形が存在するよ。

三角形分割をどんどん細かくしていくと、どんどん小さくなる三色三角形の列がとれるね。ボルツァーノ＝ワイエルシュトラスの定理を使うと収束部分列が存在することがわかって、収束先が $f(z)=0$ をみたす点だということがわかる。

はい、これで証明おしまい～。

---

{{< speech img="../img/Sakura-23.png" name="桜子" >}}
見たことない証明です……。複素解析っぽくもあり、組合せ論的でもありますね……。
{{< /speech >}}

{{< speech img="../img/Tea-5.png" name="素子" >}}
この補題が重要そうですね。これはいったい何なのでしょう？
{{< /speech >}}

{{< speech img="../img/Cuisine-17.png" name="静香" >}}
本には index lemma という名前で載ってたよ～。ポアンカレ・ホップの定理と関係ありそうだね。
{{< /speech >}}

{{< speech img="../img/Fashion-36.png" name="芽衣" >}}
知らない定理だな～。
{{< /speech >}}

{{< speech img="../img/Tea-5.png" name="素子" >}}
そういえば、Sperner の補題を使って Brouwer の不動点定理を証明する記事を最近読みました。その手法と似ている気がします。
{{< /speech >}}

{{< speech img="../img/Sakura-23.png" name="桜子" >}}
あ……、この補題から Sperner の補題が示せそうです。Sperner の補題では凸多角形は三角形で、3 頂点の色はそれぞれ赤・緑・青。3 辺は赤緑のみ、緑青のみ、赤青のみというふうになっています……。それで、index を計算します。赤緑の頂点だけがある辺だけを見ればよくて、赤から始まって緑で終わるので index は $\pm 1$ です。なので content も $\pm 1$ なので、赤緑青の三角形が存在します……。
{{< /speech >}}

{{< speech img="../img/Fashion-36.png" name="芽衣" >}}
てことは、Sperner の補題より強いってことか！
{{< /speech >}}

{{< speech img="../img/Tea-5.png" name="素子" >}}
そうですね。
{{< /speech >}}

{{< speech img="../img/Cuisine-17.png" name="静香" >}}
眠いから寝るね～。
{{< /speech >}}

{{< speech img="../img/Sakura-23.png" name="桜子" >}}
寝てしまいました……。次は私の発表なのですが、まあ聴衆が少ない方が気が楽かもしれません……。
{{< /speech >}}

## 桜子の発表

$n=2^km$ ($m$ は奇数) と表したときの、$k$ に関する帰納法で証明します。$k=0$ のとき、つまり $n$ が奇数のときは、奇数次の多項式は実数根をもつのでよいです。中間値の定理を使うものでしたね……。

$n$ 次多項式 $f(z)$ の分解体 $F$ をとります。$F$ 上で $f(z)=a(z-z_1)\cdots (z-z_n)$ となります。ここで実数 $t$ に対して

$$
g_t(z)=\prod_{1\le i<j\le n}(z-z_i-z_j-tz_iz_j)
$$

とおきます。この多項式の次数は $n(n-1)/2$ で、2 で割れる回数が $k-1$ 回なので、帰納法の仮定が使えます。つまり $g_t(z)$ に複素数根が存在します。さらに言い換えると、$z_i+z_j+tz_iz_j$ が複素数となるような $i,j$ が存在します。

ここで $t$ を動かします。$t_1\ne t_2$ としたとき、$z_i+z_j+t_1z_iz_j, z_i+z_j+t_2z_iz_j$ が同時に複素数となるような $i,j$ が存在します。$(i,j)$ の個数より実数の方が多いので当たり前ですね……。

ここから、$z_i+z_j$ と $z_iz_j$ が複素数となることがわかります。$z^2-(z_i+z_j)z+z_iz_j$ は 2 次多項式で、これが複素数の根をもつことは簡単に確かめられるので、$z_i,z_j$ は複素数です。

これで $f(z)$ が複素数の根をもつことが確かめられました……。

---

{{< speech img="../img/Tea-5.png" name="素子" >}}
面白い証明ですね。複素数体 $\mathbb{C}$ の拡大体を考えるところや、変わった帰納法の使い方が見所ですね。
{{< /speech >}}

{{< speech img="../img/Fashion-36.png" name="芽衣" >}}
$\mathbb{C}$ って代数的閉体じゃなかったか？
{{< /speech >}}

{{< speech img="../img/Tea-5.png" name="素子" >}}
それは代数学の基本定理の言い換えですね。
{{< /speech >}}

{{< speech img="../img/Fashion-36.png" name="芽衣" >}}
そうか！
{{< /speech >}}

{{< speech img="../img/Tea-5.png" name="素子" >}}
これにて全員分の証明が揃いました。どれも大変興味深く、鑑賞する価値があります。とはいえ、紹介できなかった証明がまだまだたくさんあることでしょう。
{{< /speech >}}

{{< speech img="../img/Sakura-23.png" name="桜子" >}}
トポロジーを使う証明もありました……。
{{< /speech >}}

{{< speech img="../img/Tea-5.png" name="素子" >}}
ということなので、いつかまた鑑賞会を開きましょう。次回は別の定理を扱うかもしれません。
{{< /speech >}}

{{< speech img="../img/Fashion-36.png" name="芽衣" >}}
楽しみだ！
{{< /speech >}}

## 登場人物紹介

![](../img/Sakura-23.png)

江晩桜子 (えばんさくらこ)。家族が本屋を営んでいた。古本を集めるのが趣味。

## 参考文献

- Henle, Michael. A Combinatorial Introduction to Topology.
- [【月刊組合せ論 Natori】Brouwer の不動点定理と Sperner の補題【2025 年 11 月号】](../../../natori/202511/)
- [Fundamental theorem of algebra (Wikipedia)](https://en.wikipedia.org/wiki/Fundamental_theorem_of_algebra)
