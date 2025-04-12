---
title: "【数学探究雑誌 Math 人】#001"
date: 2025-04-12
showTableOfContents: true
---

## 創刊の辞

数学は最も人間的な営みの一つである。なぜなら、未知のものを探究し生活を豊かにしていくことは古来より人間の行ってきた行為だからである。

探究は学問に限らない。献立を考えたり、暮らしのアイデアを生み出したり、そういった小さな探究も探究である。

しかし、現代社会では探究は制限されている。誰かが決めたルールに盲目的に従うことを強制され、「なぜ？」の問いすら許されない。学校では校則を守ってやりたくもない勉強をさせられ、社会ではつまらない労働をさせられる。盲目的に他者を従わせる方が便利なため、相手の思考力を奪う行為が蔓延している。そこに探究はない。このような現代社会のあり方は明らかに人間らしさを失っている。

だからこそ、探究を通じて人間らしさを取り戻していかなければならない。新たに創刊する雑誌「Math 人」は、数学を通じて探究というものを考えていくことを目的とする。強制的な勉強はつまらないものだが、探究という見方をすれば面白いものになるだろう。

春の近づく金沢にて　箱星

## 探究 001

### 探究のはじまり

数学の世界では日々、探究が行われている。その様子を垣間見ることができる場所がある。それはプレプリントサーバー arXiv である。arXiv では平日のほぼ毎日、数学のプレプリントが投稿されている。その中から「探究したい！」と思わせてくれるプレプリントを見つけ出し、探究の起点としたい。

3 月 12 日、次のようなプレプリントを目にした。

- Takuya Inoue, On refined enumerations of plane partitions of a given shape with bounded entries. ([arXiv:2503.07957](https://arxiv.org/abs/2503.07957))

筆者は組合せ論が好きであるが、その中でも特に好きなテーマがこのプレプリントに詰まっていると一目で感じた。なので、ここを起点に探究を始める。

まずは AI (Gemini) を使って重要なキーワードをピックアップしてもらった。以下がそのリストである。一部修正してある。

- 平面分割 (Plane Partition)
- 符号付き集合 (Signed Set)
- Sijection
- 統計量 (Statistic)
- 適合性 (Compatibility)
- LGV 補題 (LGV Lemma)
- シューア関数 (Schur Function)
- 半標準ヤングタブロー (Semi-Standard Young Tableaux)
- ヤング図形 (Young Diagram)
- 分割 (Partition)
- 非交差パス (Non-Intersecting Paths)

好きなテーマなだけあってこの中の多くは既に知っていた。しかし、signed set と sijection はあまりなじみがない。そこで、これらを調べていく。

### signed set と sijection

プレプリントを見ると、signed set は disjoint な有限集合の組であると書かれている。$S=(S^+,S^-)$ のように書かれるようだ。

sijection は符号付き全単射 (signed bijection) のことで、$S=(S^+,S^-)$ から $T=(T^+,T^-)$ への sijection とは、$S^+\sqcup T^-$ と $S^-\sqcup T^+$ の間の全単射のことである。要素数を比較すると $|S^+|-|S^-|=|T^+|-|T^-|$ となり、符号付きの意味が少し見えてくる。

sijection は交代符号行列と Descending Plane Partition の間の全単射を構築する問題を研究する中で導入された概念のようだ。これについては [【月刊組合せ論 Natori】ルイス・キャロルと交代符号行列【2022 年 11 月号】](../../natori/202211/) に書いてある。このプレプリントの著者も別のプレプリントでこの問題を扱っている。著者は sijection の適合性という概念を導入した。$S,T$ が符号付き集合で、$\eta_S, \eta_T$ が $S,T$ 上の量であるとする。このとき $S,T$ 間の sijection $\phi$ が $\eta=\eta_S\sqcup \eta_T$ と適合するとは

$$
\forall s\in S^+\sqcup S^- \sqcup T^+\sqcup T^-, \eta(\phi(s))=\eta(s)
$$

が成り立つことをいう。今回のプレプリントでは、この適合性を用いて平面分割の数え上げを考えている。

### Garsia-Milne involution principle

平面分割をさらに探究していってもよいが、もう 1 つ気になるワードがある。それは冒頭に書いてある「Garsia-Milne involution principle」だ。数え上げについて調べていてこの言葉を見かけることがあるが、詳しく調べたことはない。なので次はこちらを探究する。

まず involution (対合) とは逆写像が自身と一致するような全単射である。$S=S^+\sqcup S^-$ 上の対合 $\alpha$ について、次の条件を満たすものを符号反転対合と呼ぶ：任意の $x\in S\setminus\mathrm{Fix}(\alpha)$ に対して $\alpha(x)$ と $x$ の符号が異なる。さらに $\mathrm{Fix}(\alpha)\subseteq S^+$ と仮定する。このとき $S^+\setminus \mathrm{Fix}(\alpha)$ と $S^-$ の間に全単射が存在するので、要素数も等しい。

$T$ も符号付き集合とし、$\beta$ を $T$ 上の対合で、$\alpha$ と同様の条件を満たすものとする。いま、$f\colon S\to T$ を符号を保つ全単射とする。すなわち $f(S^+)=T^+, f(S^-)=T^-$ をみたすものとする。このとき

- $|S^+|-|\mathrm{Fix}(\alpha)|=|S^-|$
- $|T^+|-|\mathrm{Fix}(\beta)|=|T^-|$
- $|S^+|=|T^+|$
- $|S^-|=|T^-|$

をみたすので、$|\mathrm{Fix}(\alpha)|=|\mathrm{Fix}(\beta)|$ が成り立つ。Garsia-Milne involution principle は、全単射 $\mathrm{Fix}(\alpha)\to \mathrm{Fix}(\beta)$ を構成する方法である。

最近公開された論文

- Shalosh B. Ekhad and Doron Zeilberger, Experimenting with the Garsia-Milne Involution Principle. SIGMA 21 (2025), 015. https://doi.org/10.3842/SIGMA.2025.015

によれば、対合を使わなくてもよいらしい。

また

- Ilse Fischer and Matjaž Konvalinka, The mysterious story of square ice, piles of cubes, and bijections.

によれば

> the Garsia–Milne involution principle is equivalent to the special case of the composition of two sijections when only the “intermediate” set has a nonempty negative part.

とのことで、sijection が重要であると感じる。

Garsia-Milne involution principle はロジャーズ・ラマヌジャン恒等式の全単射証明のために導入された。フック長公式にも応用されているようである。

## 編集後記

3 月 12 日に本文中に述べたプレプリントを見つけた頃からこの企画を立ち上げようと思っていた。プレプリントを保存するだけで読まない生活が続いていたため、何とかして読みたいという思いもあった。まさに探究への思いが溢れていた時期であった。

しかし 17 日頃から新型コロナに罹患してしまい、それに伴って数学をする気力を喪失してしまった。今では少しずつ取り戻そうとしているものの、結果として「Math 人」の創刊号は想定よりもクオリティの低いものになってしまったことは否めない。

それでも公開することに決めたのは、探究というもののあり方を見せるためである。数学は完成された学問であると思っている人もいるが、初めから完成していたわけではない。多くの人の挑戦があり、その中には失敗もあった。探究も同じであると考える。なので、上手くいった探究のみを紹介することは探究に対する誤解を招くことになる。

「Math 人」はこのようなコンセプトの雑誌である。そのため、Natori 等と比べて荒削りな部分も多くなると思う。そういった部分も楽しんでいただければ幸いである。
