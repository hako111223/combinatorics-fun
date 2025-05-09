---
title: "組合せ論的な証明ってなんだろう"
date: 2024-12-05
showTableOfContents: true
---

組合せ論とは何か、組合せ論的な証明とは何かについて考えていきます。

この記事はもともと月刊組合せ論 Natori の一部となる予定でしたが、[組合せ論 Advent Calendar 2024](https://adventar.org/calendars/10062) の 5 日目の記事として公開することにしました。

## 組合せ論ってなんだろう

組合せ論とは何でしょうか。「これは組合せ論でこれは組合せ論ではない」といった線引きは難しいです。なぜなら現代数学では様々な分野が融合しているからです。代数学・幾何学・解析学は勿論、数理論理学や物理学とも関係があるのが組合せ論です。

数学者 Igor Pak のサイトでは、様々な数学者が語った「組合せ論とは何か」が載っています。一度眺めてみてください。

https://www.math.ucla.edu/~pak/hidden/papers/Quotes/Combinatorics-quotes.htm

## 組合せ論的な考え方ってなんだろう

例えば $C_n=\frac{1}{n+1}\binom{2n}{n}$ という数列を考えます。これだけではただの数ですが、「$C_n$ は $n$ 個の `(` と $n$ 個の `)` からなる正しい括弧列の個数である」ということを踏まえると、$C_n$ を組合せ論的に考えることができます。

このように、ある数を「ある条件を満たすオブジェクトの個数」と考えることで組合せ論的な解釈ができるといえそうです。ですがこれは本当でしょうか？

$\mathfrak{S}_w$ をシューベルト多項式とします。この記事では解説できないので、そんなものもあるんだ程度に捉えてください。2 つのシューベルト多項式の積をシューベルト多項式の線形結合として表すことができます。

$$
\mathfrak{S} _ u\cdot\mathfrak{S} _ v=\sum_w c_{uv}^w \mathfrak{S}_w
$$

係数 $c_{uv}^w$ をシューベルト係数と呼びます。シューベルト係数は非負整数になることが知られています。このことから、シューベルト係数はあるオブジェクトの個数に等しいのではないかと考えられますが、この数の組合せ論的な解釈は見つかっていないというのが共通認識となっているようです。一方でシューベルト係数は 3 つのシューベルト多様体の交叉においてある種の点の個数に等しいということから、これが解釈ではないかという意見もあります。しかしこれは「組合せ論的な」解釈ではないと考えられているようです。

では何が組合せ論的な解釈で何が組合せ論的ではないのでしょうか。Igor Pak は組合せ論的な解釈を一言で表しています。それは #P です。#P とは P や NP のような計算複雑性のクラスです。

## 組合せ論的な証明ってなんだろう

過去の月刊組合せ論 Natori の記事を 2 つ紹介します。まずは交代符号行列予想という組合せ論の予想です。

[【月刊組合せ論 Natori】ルイス・キャロルと交代符号行列【2022 年 11 月号】](../../natori/202211/)

この予想は数理物理のテクニックを用いて証明されました。

もう 1 つは彩色多項式の係数がユニモーダルになるという予想です。

[【月刊組合せ論 Natori】June Huh 氏の業績を解説【2022 年 12 月号】](../../natori/202212/)

こちらは代数幾何学のテクニックを用いて証明されました。

このように組合せ論は様々な分野と融合して発展しています。しかしそんな中でも「組合せ論的な証明」にこだわる人がいます。実際交代符号行列予想も全単射を用いた証明が後に見つかりました。

なぜ組合せ論的な証明を追求するのでしょうか？

ぜひ組合せ論が専門の人から話を聞いてみたいです。(私にはわかりませんでした)

## おわりに

組合せ論入門みたいな記事を書きたかったのですが、実は入門記事の方が書くのが難しいんですよね。

[組合せ論 Advent Calendar 2024](https://adventar.org/calendars/10062) ではまだまだ参加者を募集しています。というか参加してくれないと主催者が過労死してしまう……。
