---
title: "【月刊組合せ論 Natori】Mahonian statistics【2024 年 10 月号】"
date: 2024-10-01
showTableOfContents: true
---

{{< katex >}}
月刊組合せ論 Natori は面白そうな組合せ論のトピックを紹介していく企画です。今回は順列について深掘りしていきます。

## Statistics

この記事では順列は $(1,2,\ldots,n)$ の順列のこととします。順列に対して数を対応させる関数のことを statistics といいます。例えば転倒数

$$
\mathrm{inv}(p)=\\#\\{(i,j)\mid 1\le i<j\le n, p_i>p_j\\}
$$

は statistics です。直訳すると統計量ですが、別に統計をやっているわけではないので単に「量」と呼ぶこともあります。

転倒数と並ぶくらい重要な量に、major index があります。順列 $p$ の降下点集合を $\mathrm{Des}(p)=\\{i\mid p_i>p_{i+1}\\}$ とするとき、major index は降下点の和、すなわち

$$
\mathrm{maj}(p)=\sum_{i\in \mathrm{Des}(p)}i
$$

により定まります。例えば $p=31425$ のとき $\mathrm{Des}(p)=\\{1,3\\}$ なので major index は $1+3=4$ です。

転倒数と major index の間には次のような驚くべき関係があります。

{{< alert lightbulb >}}
**定理**: inv と maj は同分布である。すなわち、任意の $k$ に対して転倒数が $k$ である順列の個数と major index が $k$ である順列の個数は等しい。
{{< /alert >}}

inv や maj と同分布である量は Mahonian statistics と呼ばれます。

## 転倒数

転倒数が $k$ に等しい長さ $n$ の順列の個数 $b(n,k)$ については 2024 年 2 月号の Natori に書きました。

[【月刊組合せ論 Natori】転倒数が k である順列の個数【2024 年 2 月号】](https://combinatorics-fun.vercel.app/natori/202402/)

ここでは簡単に復習します。$b(n,k)$ の母関数を

$$
f_n(z)=\sum_{k=0}^{n(n-1)/2} b(n,k)z^k=\sum_{p\in S_n}z^{\mathrm{inv}(p)}
$$

としたとき

$$
f_{n+1}(z)=(1+z+\cdots+z^n)f_n(z)
$$

という式が成り立つので

$$
f_n(z)=(1+z)(1+z+z^2)\cdots (1+z+\cdots+z^{n-1})
$$

となります。

## major index

inv と maj が同分布であることを示すためには、母関数が同じであることを示せばよいです。

$$
g_n(z)=\sum_{p\in S_n}z^{\mathrm{maj}(p)}
$$

とおきます。転倒数の場合と同様、長さ $n$ の順列 $p$ に $n+1$ を挿入することで長さ $n+1$ の順列 $p^{\prime}$ が作れることに着目します。$\mathrm{Des}(p)=\\{i_1,\ldots,i_k\\}$ とします。

$p^{\prime}$ における $n+1$ の位置を $j$ とします。$j=n+1$ のとき、すなわち末尾に $n+1$ を挿入するとき $\mathrm{maj}(p^{\prime})=\mathrm{maj}(p)$ です。以下では $j\ne n+1$ とします。このとき必ず $j\in \mathrm{Des}(p^{\prime})$ となります。

ある $m$ について $j=i_m+1$ のとき、$i_m$ は $p^{\prime}$ の降下点ではありません。$i_{m+1}$ 以降は $n+1$ を挿入した影響で 1 ずつ右にずれます。よって

$$
\begin{align*}
\mathrm{maj}(p^{\prime})&=i_1+\cdots+i_{m-1}+j+(i_{m+1}+1)+\cdots+(i_k+1) \\\
&=\mathrm{maj}(p)+k-m+1
\end{align*}
$$

となります。$1\le m\le k$ なので、この値は $\mathrm{maj}(p)+1$ 以上 $\mathrm{maj}(p)+k$ 以下です。

次に、$i_m+1<j<i_{m+1}$ と仮定します (ただし $i_0=-\infty$ とします)。このとき

$$
\begin{align*}
\mathrm{maj}(p^{\prime})&=i_1+\cdots+i_m+j+(i_{m+1}+1)+\cdots+(i_k+1) \\\
&=\mathrm{maj}(p)+j+k-m+1
\end{align*}
$$

となります。この値は $\mathrm{maj}(p)+k+1$ 以上 $\mathrm{maj}(p)+n-1$ 以下です。

さらに、挿入位置が異なれば major index の値も異なります (細かい部分は各自で確かめてみましょう)。以上より、$\mathrm{maj}(p^{\prime})$ の値は $\mathrm{maj}(p)$ 以上 $\mathrm{maj}(p)+n-1$ 以下の各整数値をとります。よって

$$
g_{n+1}(z)=(1+z+\cdots+z^n)g_n(z)
$$

となります。ここから $g_n(z)=f_n(z)$ が従います。したがって、inv と maj は同分布です。

別の証明方法として、Foata の全単射と呼ばれるものがあります。これは全単射 $\phi\colon S_n\to S_n$ であって $\mathrm{inv}(p)=\mathrm{maj}(\phi(p))$ をみたすものです。

## 一般の数列

順列の場合を考えましたが、1 が $a_1$ 個、…、$k$ が $a_k$ 個からなる数列の集合 $S$ 上においても inv と maj は同分布です。母関数は $q$ 多項係数になります。

$$
\sum_{p\in S}q^{\mathrm{inv}(p)}=\sum_{p\in S}q^{\mathrm{maj}(p)}=\binom{n}{a_1,a_2,\ldots,a_k}_q
$$

特に数が 2 種類の場合は母関数が $q$ 二項係数になります。

## その他の Mahonian statistics

inv と maj 以外の Mahonian statistics はどのようなものがあるでしょうか。次のような量を考えます。

- $v=n,n-1,\ldots,1$ の順に次を行う。$p_i=v$ となる $i$ をとり、$p_i$ と $p_v$ を入れ替える。コストは $|i-v|$ である。

コストの総和を $\mathrm{sor}(p)$ とおきます。例えば、$p=315462$ のとき

- 6, 2 を入れ替え、$p=315426$ にする。コストは 1
- 5, 2 を入れ替え、$p=312456$ にする。コストは 2
- 4 はそのまま。コストは 0
- 3, 2 を入れ替え、$p=213456$ にする。コストは 2
- 2, 1 を入れ替え、$p=123456$ にする。コストは 1

なので、$\mathrm{sor}(p)=1+2+2+1=6$ です。この $\mathrm{sor}$ も Mahonian statistics です。

他にもたくさんあります。

- Kitaev, Sergey. Patterns in Permutations and Words. Springer (2011).

の 3.3 を見ると、色々な Mahonian statistics が載っています。

## おわりに

Mahonian statistics を紹介しました。順列の世界はまだまだ奥が深いので、今後も紹介していきたいです。

## 参考文献

- Bóna, Miklós. Combinatorics of permutations. 3rd ed.
