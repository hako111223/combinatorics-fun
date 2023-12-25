---
title: "奇数次元のシンプレクティック群とは何か"
date: 2023-12-25
showTableOfContents: true
---

{{< katex >}}

この記事は[表現論 Advent Calendar 2023](https://adventar.org/calendars/8636) の 25 日目の記事です。

まずは通常のシンプレクティック群の紹介から始めて、奇数次元のシンプレクティック群を紹介します。

## シンプレクティック群

$$
J_n=\begin{pmatrix} 0 & 1 & & & & & \\\ -1 & 0 & & & & & \\\ & & 0 & 1 & & & \\\ & & -1 & 0 & & & \\\ & & & & \ddots & & \\\ & & & & & 0 & 1 \\\ & & & & & -1 & 0 \end{pmatrix}
$$

とおきます。これは $2n$ 次の正方行列です。空白の部分はすべて 0 です。

$$
Sp_{2n}(\mathbb{C})=\\{g\in SL_{2n}(\mathbb{C})\mid {}^tgJ_ng=J_n\\}
$$

を複素シンプレクティック群といいます。これは複素リー群となります。対応するリー環は

$$
\mathfrak{sp} _ {2n}(\mathbb{C})=\\{X\in\mathfrak{sl}_{2n}(\mathbb{C})\mid {}^tXJ_n+J_nX=O\\}
$$

です。

なお、$J_n$ の定義が微妙に異なる文献もあります。

## 奇数次元シンプレクティック群

シンプレクティック群といえば通常は偶数次元ですが、奇数次元のシンプレクティック群を Proctor が導入しました。それは次のようなものです。

$$
Sp_{2n+1}(\mathbb{C})=\begin{pmatrix} & & & 0 \\\ & Sp_{2n}(\mathbb{C}) & & \vdots \\\ & & & 0 \\\ * & \cdots & * & z \end{pmatrix}
$$

ここで $z$ は 0 でない複素数です。より一般に

$$
Sp_{2n,m}(\mathbb{C})=\begin{pmatrix} Sp_{2n}(\mathbb{C}) & O \\\ * & GL_m(\mathbb{C}) \end{pmatrix}
$$

を intermediate シンプレクティック群といいます。

奇数次元のシンプレクティック群は単純群でない（簡約群でもない）ため、偶数次元のシンプレクティック群ほどはいい性質をもたない群です。

## 指標

$GL_n(\mathbb{C})$ の場合を振り返ってみましょう。$T$ を正則な対角行列全体からなる $GL_n(\mathbb{C})$ の部分群とします。$GL_n(\mathbb{C})$ の有限次元表現 $(W,\rho)$ に対して、$(\operatorname{ch}W)(z_1,\ldots,z_n)=\operatorname{tr} _ W\rho(\mathrm{diag}(z_1,\ldots,z_n))$ によって定まる $\operatorname{ch}W$ を指標といいます。シューア多項式 $s_{\lambda}$ はある $GL_n(\mathbb{C})$ の既約表現の指標と一致することが知られています。

$Sp_{2n}(\mathbb{C})$ の場合、正則な対角行列は $\mathrm{diag}(z_1,z_1^{-1},\ldots,z_n,z_n^{-1})$ の形です。$Sp_{2n,m}(\mathbb{C})$ の場合は $\mathrm{diag}(z_1,z_1^{-1},\ldots,z_n,z_n^{-1},z_{n+1},\ldots,z_{n+m})$ となります。

## シンプレクティックシューア関数

シューア関数は

- 行列式の比
- 半標準ヤングタブローに関する和

として定義することもできます。シンプレクティックシューア関数や intermediate シンプレクティックシューア関数も同様です。タブローの方を解説します。

タブローに書き込む文字とその大小関係を $1<\bar{1}<\cdots<n<\bar{n}<n+1<n+2<\cdots<n+m$ とします。$\lambda$ のヤング図形にこれらの文字を書き込む方法であって

- 各行について広義単調増加
- 各列について狭義単調増加
- $i$ 行目の成分は $i$ 以上

をみたすものの集合を $\mathrm{SpTab}^{(n,m)}(\lambda)$ とします。タブロー $T$ に書き込まれた $i$ の個数を $m_T(i)$ とするとき

$$
sp_{\lambda}^{(n,m)}(z_1,z_1^{-1},\ldots,z_n,z_n^{-1},z_{n+1},\ldots,z_{n+m})=\sum_{T\in \mathrm{SpTab}^{(n,m)}(\lambda)}\prod_{i=1}^{n+m} z_i^{m_T(i)-m_T(\bar{i})}
$$

によって intermediate シンプレクティックシューア関数を定義します。ただし $n+1\le i\le n+m$ のときは $m_T(\bar{i})=0$ です。

$n=0$ のときシューア関数、$m=0$ のときシンプレクティックシューア関数となります。

## 応用

これが何の役に立つのかと思うかもしれませんが、数え上げ問題に役立つようです。

## おわりに

駆け足になってしまいましたが、奇数次元のシンプレクティック群について紹介しました。

数え上げと関係があるのは面白いと思いました。表現論と組合せ論の関係をもっと知りたいです。

## 参考文献

- 小林俊行・大島利雄, リー群と表現論, 岩波書店, 2005.
- Maliakas, Mihalis. On odd symplectic Schur functions. J. Algebra 211, No. 2, 640-646 (1999).
- Okada, Soichi. Intermediate symplectic characters and shifted plane partitions of shifted double staircase shape. Combinatorial Theory 1, Paper No. 10, 42 p. (2021).
- Proctor, Robert A. Odd symplectic groups. Invent. Math. 92, No. 2, 307-332 (1988).