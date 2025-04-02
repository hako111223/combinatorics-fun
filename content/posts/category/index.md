---
title: "圏における和と積"
date: 2024-12-24
showTableOfContents: true
---

この記事は[圏論 Advent Calendar 2024](https://adventar.org/calendars/10265) の 24 日目の記事です。

とある本で次のような記述があったようです：環 $R_1,\ldots,R_n$ の直積集合 $R_1\times\cdots\times R_n$ 上に加法と乗法を

- $(a_1,\ldots,a_n)+(b_1,\ldots,b_n)=(a_1+b_1,\ldots,a_n+b_n)$
- $(a_1,\ldots,b_n)\cdot (b_1,\ldots,b_n)=(a_1b_1,\ldots,a_nb_n)$

により定めたとき、$(0,\ldots,0)$ を加法の単位元、$(1,\ldots,1)$ を乗法の単位元とする環となる。これを $R_1,\ldots,R_n$ の**直和**という。

これを受けて、「直和ではなく直積だろう」という指摘がありました。私は「有限個なら直和と直積は一致するのでは？」と当初思っていましたが、調べてみるとこれは加群での話でした。

そこで、環や加群の直和・直積を復習するため、そしてこれらを圏論的に捉えるためにこの記事を書くことにしました。

## 圏における和と積

$\mathcal{C}$ を圏とします。$\lambda\in\Lambda$ に対して $A _ {\lambda}$ をこの圏の対象とします。$A=(A_{\lambda}) _ {\lambda\in\Lambda}$ の**和**とは、対象 $\widetilde{A}$ と射の族 $(i _ {\lambda}\colon A _ {\lambda}\to\widetilde{A}) _ {\lambda\in\Lambda}$ の組であって、任意の対象 $X$ と任意の射の族 $(f_{\lambda}\colon A_{\lambda}\to X) _ {\lambda\in\Lambda}$ に対して、$f\circ i_{\lambda}=f_{\lambda}$ がすべての $\lambda\in\Lambda$ に対して成り立つような射 $f\colon \widetilde{A}\to X$ が一意的に存在するものです。

$\widetilde{A}$ は $\coprod_{\lambda\in\Lambda}A_{\lambda}$ とも書かれます。また余積と呼ばれることもあります。和は圏論における帰納極限の一種です。

$A=(A_{\lambda}) _ {\lambda\in\Lambda}$ の**積**も同様に定義されます。これは対象 $\widetilde{A}$ と射の族 $(p_{\lambda}\colon \widetilde{A}\to A_{\lambda}) _ {\lambda\in\Lambda}$ であって、任意の対象 $X$ と任意の射の族 $(f_{\lambda}\colon X\to A_{\lambda}) _ {\lambda\in\Lambda}$ に対して、$p_{\lambda}\circ f=f_{\lambda}$ がすべての $\lambda\in\Lambda$ に対して成り立つような射 $f\colon X\to \widetilde{A}$ が一意的に存在するものです。

積は $\prod_{\lambda\in\Lambda}A_{\lambda}$ とも書かれます。積は射影極限の一種です。

和や積は常に存在するとは限らないことに注意が必要です。

## 加群の直和と直積

$R$ を環とします。圏 $R$-$\mathbf{Mod}$ は左 $R$ 加群を対象とし、左 $R$ 加群の準同型を射とする圏です。（小さな集合かどうかといった議論は省略します）

$(M_{\lambda}) _ {\lambda\in\Lambda}$ を左 $R$ 加群の族とします。$(M_{\lambda}) _ {\lambda\in\Lambda}$ の直積を、直積集合 $\prod _ {\lambda\in\Lambda}M_{\lambda}$ に加法を $(x_{\lambda}) _ {\lambda}+(y_{\lambda}) _ {\lambda}=(x_{\lambda}+y_{\lambda}) _ {\lambda}$、$R$ の元による左乗法を $a(x_{\lambda}) _ {\lambda}=(ax_{\lambda}) _ {\lambda}$ により定めます。この左 $R$ 加群を $\prod _ {\lambda\in\Lambda}M _ {\lambda}$ で表します。写像 $p_{\mu}\colon \prod _ {\lambda\in\Lambda}M_{\lambda}\to M_{\mu}$ を $p_{\mu}((x_{\lambda}) _ {\lambda})=x_{\mu}$ により定義します。

すると、これは圏 $R$-$\mathbf{Mod}$ における積になります。

また、$(M_{\lambda})_{\lambda\in\Lambda}$ の直和を、集合

$$
\{(x_{\lambda}) _ {\lambda}\in \prod _ {\lambda\in\Lambda}M_{\lambda}\mid \text{有限個を除いた} \lambda\in\Lambda \text{に対して} x_{\lambda}=0 \}
$$

に同様の演算を定めたものとし、$\bigoplus_{\lambda\in\Lambda}M_{\lambda}$ で表します。$i_{\mu}\colon M_{\mu}\to \bigoplus_{\lambda\in\Lambda}M_{\lambda}$ も定めます。これは $R$-$\mathbf{Mod}$ における和となります。

加群の直和・直積を圏論の和・積として捉えることができました。

定義から明らかなように、$\Lambda$ が有限集合の場合は直和と直積は一致します。

## 環の直積

環のなす圏を $\mathbf{Ring}$ とします。

最初に書いた環の「直和」は、$\mathbf{Ring}$ における積となります。

では $\mathbf{Ring}$ における和は何になるでしょうか？

どうやら、自由積と呼ばれるものになるそうです。さらに、可換環の圏においてはテンソル積になるそうです。

この辺りの議論は確かめることができませんでした。すみません。

## おわりに

当初はもっと高度なことを書こうと思っていましたが、基礎的なことがわかっていなかったのでやめました。

圏論の理解ももっと深めたいと思っています。圏論と関係する、気になっているキーワードを列挙します。

- categorification
- KLR 代数
- Hall 代数
- Soergel bimodule
- Khovanov ホモロジー

いつかはこの辺りも理解したいです。

## 参考文献

- https://x.com/komugikotori/status/1865233815494627775
- [Category of rings (Wikipedia)](https://en.wikipedia.org/wiki/Category_of_rings)
- 志甫淳, 層とホモロジー代数, 共立出版, 2016.